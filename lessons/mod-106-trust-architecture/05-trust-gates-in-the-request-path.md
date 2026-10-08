# Chapter 5 — Trust Gates in the Request Path

## Why this chapter exists

The three composable questions from Chapter 1 —
identity, capability, context — are answered by a
runtime component. That component is the **trust
gate**. A trust gate is the enforcement point that
makes authorisation decisions at the moment an agent
attempts an operation; everything in Chapters 1–4 is
preparation for the few milliseconds the gate spends on
each operation.

This chapter builds the gate: where it sits, what it
does, what it costs, and what it breaks. The honest
accounting matters because trust gates impose real
costs — latency, availability dependency, developer
friction — and a program that denies the costs will
have the costs discovered by the production system in
unflattering ways. Exercise 04 asks for a gate design
with explicit cost acknowledgment.

## 5.1 Where trust gates sit — the placement taxonomy

Four common placement patterns. Each has strengths and
weaknesses, and in practice production architectures
use several in combination.

| Placement | What it sees | Strengths | Weaknesses |
|---|---|---|---|
| **Agent-side** (inside the agent's process, as a middleware or SDK) | Every operation the agent attempts | Lowest latency; full agent context (reasoning, prompt state) | Trusts the agent process; agent can bypass if compromised; policy updates require agent redeploy |
| **Reverse-proxy** (between agent and downstream services) | Every operation the agent makes outbound | Cannot be bypassed by the agent; policy updates don't require agent change | Cannot see agent reasoning before the call; terminates at the proxy, so TLS and auth live there |
| **Resource-side** (inside the resource being accessed, before business logic) | Every operation against the resource | Sees authentic resource state and parameters; last line of defence | Each resource implements its own gate (duplication); inconsistency across resources |
| **Gateway-mediated** (separate gateway service that agents call for authorisation) | Every operation routed through the gateway | Single point of policy enforcement; comprehensive audit; central policy management | Latency (extra network hop); availability (gateway outage = all agents stop); scale (gateway must handle whole fleet) |

### 5.1.1 Why defence-in-depth

In practice, programs deploy **multiple** gates with
overlapping responsibilities. The agent-side gate
rejects obvious errors quickly; the reverse-proxy or
gateway gate is the authoritative decision; the
resource-side gate is the last-line defence against a
compromised path.

An agent-side gate on its own is not an authorisation
boundary — if the agent is compromised, so is the
gate. A reverse-proxy or gateway on its own means the
agent's internal state is invisible to the decision.
A resource-side gate on its own means every resource
re-implements the policy. Defence-in-depth applies to
trust architecture as much as to security
architecture.

### 5.1.2 A worked example — three-gate pipeline

A realistic pipeline for the Tessera customer-service
agent:

```
Customer prompt arrives
  │
  ▼
Agent process
  ├── Agent-side gate (SDK)
  │     - Fast rejection of obvious violations
  │     - Latency budget: ≤5ms p99
  │     - Fail-open to the next gate (don't block if the SDK itself errors)
  │
  ▼
Agent emits a tool call
  │
  ▼
Reverse-proxy gate (sidecar / egress proxy)
  ├── Signature + capability + context evaluation
  ├── Deterministic 4-axis trust score computed here
  ├── Latency budget: ≤30ms p99
  ├── Fail-closed (if the gate errors, deny)
  │
  ▼
Call reaches downstream API
  │
  ▼
Resource-side gate (inside the API before business logic)
  ├── Final capability check against resource state
  ├── Latency budget: ≤15ms p99
  ├── Fail-closed for high-stakes resources (transfers, disputes)
  │
  ▼
Business logic executes
  │
  ▼
Return path — signed event emitted summarising the decision
```

The cumulative latency budget: ≤50ms p99 end-to-end for
interactive operations. Each gate has its own fail
behaviour; two gates fail closed (reverse-proxy,
high-stakes resource-side) and one fails open
(agent-side SDK — because a buggy SDK should not
freeze the agent, as the authoritative gate is
downstream).

The pattern is reusable; the specifics are a design
choice. Exercise 04 asks for a defensible version with
latency broken out per gate.

## 5.2 What a trust gate does

A trust gate's responsibilities, in order:

1. **Authenticate.** Verify the agent's identity
   attestation — signature, freshness, revocation
   status, delegation chain.
2. **Verify capability.** Confirm the requested
   operation is within the agent's signed capability
   scope. Capability constraints are evaluated
   against the operation parameters.
3. **Evaluate context.** Apply runtime policy: risk
   thresholds, recent posture signals, anomaly flags,
   time-based rules. The trust-score axes from
   Chapter 4 are computed here.
4. **Decide.** Allow, deny, or require additional
   evidence (step-up authentication, human approval).
5. **Log.** Emit a signed event recording the
   decision, the inputs, and the reasoning. Feeds the
   posture-feedback loop from Chapter 2 and the audit
   ledger (mod-108).

Each step is independently failable. A gate that does
step 2 without step 1 authorises operations from
unauthenticated agents (because it never checked who
the agent was). A gate that does steps 1–4 without
step 5 cannot be audited (there is no record of what
it decided or why). A gate that does step 5 without
step 4 is not a gate; it is a logger.

The test: for each step, can the implementer point to
the code that performs it, and the signed artifact it
produces? If any step is implemented by "we trust
the agent", that step is not implemented.

## 5.3 The latency trade-off

Trust gates add latency. For interactive agents
(customer-facing chat, real-time decision-support),
the gate's latency is on the user-experience critical
path. For asynchronous agents (overnight processing,
batch operations), latency is less constrained but
still real.

Latency budgets vary by use case; useful starting
targets:

| Operation class | Trust gate budget | Notes |
|---|---|---|
| **Interactive, user-facing** | <50ms p99 | Human user is waiting; above 100ms begins to feel slow |
| **Streaming / per-token** | <5ms p99 | Thousands of calls per minute; latency compounds |
| **Batch / asynchronous** | <200ms p99 | Users not waiting; still worth bounding to avoid blocking the batch |
| **Catastrophic / high-stakes** | Latency is irrelevant if correct | A 2-second gate that correctly blocks a fraudulent $50,000 transfer is cheaper than a 2-millisecond gate that lets it through |

Programs sometimes try to optimise the gate by caching
authorisation decisions. Caching is dangerous when
capability assertions are short-lived or revocation
matters; the cache must be invalidated on revocation
events, and the cache window must be shorter than the
token lifetime. A cache that keys on `(agent_jti,
operation_hash)` and expires on `exp` of the token
is defensible. A cache that keys on `(agent_id,
resource)` without a revocation path is not.

### 5.3.1 Latency-budget reasoning as a worked example

How does an architect choose 50ms vs 100ms vs 200ms?
A worked chain:

- Customer-service chat UI commits to perceived
  latency <500ms for the first-token response.
- LLM inference accounts for ~300ms.
- Database retrieval for context ~50ms.
- Downstream API call (round trip, including
  resource processing) ~100ms.
- Available budget for trust gates ~50ms.

A 50ms budget split across three gates: 5ms (agent-
side) + 30ms (reverse-proxy) + 15ms (resource-side).
Each gate's budget is enforced in load tests; a gate
that regularly exceeds its budget is in violation and
either gets re-architected, cached more aggressively,
or moved earlier in the pipeline so its latency is
not on the critical path.

The point is to make the budget *visible* in the
architecture, not to defend any specific number.
Different firms, use cases, and hardware will produce
different budgets; the discipline is choosing one
deliberately rather than discovering the budget was
exceeded at incident post-mortem.

## 5.4 What trust gates break — honest accounting

Trust gates impose costs. A program that cannot name
them cannot manage them. Five categories; the
Exercise 04 constraint requires addressing all five.

### 5.4.1 Latency

Addressed above. Each gate adds milliseconds on the
critical path. The cost is paid by every operation,
even the ones that would have been allowed anyway.

### 5.4.2 Availability dependency

The gate becomes a dependency for any operation that
goes through it. Gate outage = system outage. Programs
must choose: fail-open (operations continue, security
degrades) or fail-closed (operations halt,
authorisation preserved). Fail-closed is correct for
catastrophic operations; fail-open may be defensible
for very-low-stakes operations if the posterior
detection is strong.

The architectural implication: trust gates must have
*higher* availability than the services they protect.
A trust gate at 99.9% that gates a 99.95% API has
reduced the API's effective availability. Operational
investment follows.

### 5.4.3 Operational complexity

The gate must be deployed, monitored, scaled, updated.
Policy changes become infrastructure changes. The team
operating the gate must understand both the policy
model (the CAO's domain) and the enforcement
infrastructure (the SRE's domain). This is a staffing
and process cost, not just an engineering one.

### 5.4.4 Developer friction

Agent developers must understand the gate's policy
model; misunderstanding produces operations the gate
rejects, which manifests as system errors in the
agent's logs. If the gate's error messages are
cryptic, every rejected operation becomes a support
ticket.

Mitigations: good error messages (name the specific
capability missing or constraint violated); a
development-mode gate that explains rather than
rejects; clear documentation of the capability
vocabulary; a sandbox that developers can test
against before deployment.

### 5.4.5 False positives

A gate that rejects too aggressively breaks legitimate
operations; one that rejects too leniently fails its
purpose. The tuning problem has no clean solution; it
requires continuous attention.

Mitigations: a shadow mode (gate evaluates but does
not enforce) during initial deployment, with
production reads of what *would have been* rejected;
A regular review of rejected operations to find
false-positive patterns; a mechanism for principals
to appeal rejections (contestability, per mod-105
Chapter 5).

A gate design that acknowledges all five costs and
proposes mitigations for each is a credible design. A
design that silently assumes the costs are zero will
have the costs discovered by the production system,
usually at the worst possible time.

## 5.5 Step-up authentication patterns

For high-stakes operations where the gate is uncertain,
the right output is often neither allow nor deny but
*require additional evidence*. Step-up is the pattern
for this. Four common step-up triggers:

| Pattern | What it requires | When it fits |
|---|---|---|
| **Human-in-the-loop approval** | Operation pauses for a human approver (customer, employee, or operations) | High-blast-radius operations with low frequency — large funds transfers, external messaging to new recipients |
| **Re-attestation** | Agent must present a fresh attestation, often with extra strength (e.g., a higher-assurance issuer) | When the current attestation is near expiry or when the operation is above routine blast radius |
| **Posture re-check** | The agent's deployed configuration is re-verified before the operation proceeds | When posture signals have degraded; when the configuration hash is unexpected |
| **Multi-party authorisation** | Multiple principals must approve the operation | For catastrophic operations — regulatory filings, policy changes, large transfers across business units |

Step-up triggers must be **specific**. "For unusual
operations" is not a trigger; "when the funds-transfer
amount exceeds the 75th percentile of the customer's
90-day transfer history" is. The discipline is naming
the condition in machine-evaluable terms.

Step-up is the right pattern when the operation's
blast radius is high but legitimate use is also
expected. It avoids the binary trap of allow-or-deny
and gives principals a path through for operations
that are legitimate but out-of-pattern. Without a
step-up option, the gate's choice is between failing
legitimate customers (deny) or allowing fraudulent
operations (allow). Step-up gives a third door.

## 5.6 What a CAO reads for in a trust-gate design

Five tests, as a CAO reading a gate design:

1. **Is the placement defence-in-depth?** A
   single-placement design is not robust. Expect at
   least two placements with explicit roles.
2. **Does the design name the latency budget per
   gate?** A cumulative-only budget hides the
   trade-offs. Per-gate budgets make the design
   inspectable.
3. **Does at least one gate fail closed for
   catastrophic operations?** A fail-open gate on a
   payment path is a design that will produce
   incidents.
4. **Are the step-up triggers specific and
   mechanical?** Vague step-up ("for unusual
   operations") is not operational.
5. **Does the design acknowledge all five costs
   (latency, availability, operational complexity,
   developer friction, false positives) with
   mitigations?** A design that denies the costs is
   not credible.

## Summary

- Trust gates are the runtime components that make
  authorisation decisions. Chapters 1–4 are
  preparation; the gate is where the discipline
  becomes operational.
- Four placement patterns (agent-side, reverse-proxy,
  resource-side, gateway-mediated), each with
  trade-offs; defence-in-depth is the practical
  discipline.
- Gate responsibilities are five, in order:
  authenticate, verify capability, evaluate context,
  decide, log. Each step is independently failable
  and must be inspectable.
- Latency budgets vary by use case; the discipline is
  choosing the budget deliberately, broken out per
  gate, and enforcing it in load tests.
- Gates impose five costs — latency, availability,
  operational complexity, developer friction, false
  positives. Honest designs name all five.
- Step-up authentication gives the gate a third door
  beyond allow/deny; triggers must be specific and
  machine-evaluable.
