# Chapter 2 — Zero-Trust Adapted for AI Agents

## Why this chapter exists

Zero-trust architecture (NIST SP 800-207) is the most
useful structural inheritance for thinking about AI
trust. It is *not* a perfect fit — 800-207 was written
for human and service identities, not for agents that
generate novel intents at runtime — but the structural
discipline transfers cleanly when adapted.

This chapter does the adaptation. The payoff is twofold.
First, a CAO who can read 800-207 and translate it to
the agent case can hold technical conversations with the
CISO and CTO without conceding the vocabulary. Second,
the adaptation names three places the source framework
needs extension — dynamic identity, intent-aware
authorisation, per-operation enforcement — that later
chapters build on.

Exercise 01 maps trust boundaries using these tenets.
This chapter is written so that the mapping is
executable from it.

## 2.1 The 800-207 core tenets

NIST SP 800-207 names seven tenets of zero-trust
architecture. Each was written with human and service
identity primarily in mind. Each translates to the AI
agent case cleanly if you do the translation
deliberately. The two-column mapping:

| 800-207 tenet | Translation for AI agents |
|---|---|
| All data sources and computing services are considered resources | Every model endpoint, every tool, every data store the agent touches is a resource. The agent itself is also a resource to systems upstream of it |
| All communication is secured regardless of network location | Agent-to-tool and agent-to-data communication is authenticated regardless of "internal" / "external". Private VPC does not confer trust |
| Access is granted on a per-session basis | Each agent operation is independently authorised; prior operations do not extend authority. "The agent was trusted five minutes ago" is not a basis for authorising the current operation |
| Access is determined by dynamic policy | Authorisation considers the requesting agent's identity, capability scope, the resource's classification, and runtime context (anomaly signals, posture, time of day) |
| Asset integrity and security posture is monitored | Both the agent's deployed configuration (prompt template, tool set, model version) and the resources it touches have continuous posture monitoring |
| Authentication and authorisation are dynamic and strictly enforced | No standing privilege; capability assertions are short-lived; authorisation is evaluated per request against the current policy |
| Information about asset state, network infrastructure, and communications is collected for posture improvement | Agent operation logs feed back into trust scoring, policy refinement, and gate-design improvement (the posture-feedback loop) |

The discipline these tenets encode — *do not extend
trust beyond the scope you can verify, do not assume
that prior verification carries forward without
re-evaluation* — is the right discipline for AI agents.
The tenets are more conservative than most agent
systems operate today, and that is precisely why they
are useful: they describe a stance the architecture
should aspire to, not the stance a convenient
deployment defaults to.

## 2.2 Where 800-207 needs adaptation

Three places the source framework was not designed for
agentic AI. Each is a load-bearing gap that later
chapters address.

### 2.2.1 Agent identity is not static

A human or service has a stable identity: a username,
a service account, a workload identity bound to a
certificate. An AI agent may be one of many instances
of an underlying model, each instantiated for a
specific session, possibly with different system
prompts or memory state, possibly delegated by a
different principal.

Identity in this case is a **composite**: `(model
version, configuration hash, principal-on-whose-behalf,
session id)`. NIST 800-207's identity model does not
directly address this. Chapter 3 builds out the
composite identity pattern in detail.

The practical consequence: an architecture that treats
"the agent" as a single identity will quickly discover
it cannot distinguish between an authorised agent
running the current prompt template and an unauthorised
agent running a tampered prompt template. The
distinction matters because the second case is a prompt
injection, and prompt injection is the dominant class
of agent compromise.

### 2.2.2 Agent intent is generated at runtime

A traditional service knows in advance what API calls
it will make: those API calls are coded into it. An AI
agent decides at runtime, often based on a user prompt
plus the model's reasoning, which tools to invoke and
with what arguments. Authorisation cannot pre-approve
all possible intents the agent might generate.

Two implications. First, capability scoping must be
coarse enough to cover the space of legitimate intents
and fine enough to exclude the illegitimate ones —
Chapter 3 §3.2 names the discipline for this. Second,
posterior detection (logging, anomaly flagging) is
*not* a substitute for prior authorisation: a gate
that logs an unauthorised payment and alerts an
analyst three hours later has still allowed the
payment. The agent's non-standard intent must be
caught *before* it is executed.

### 2.2.3 Policy enforcement must scale to per-operation granularity

Service-level access control is typically per-API-call
or per-resource. Agent-level trust architecture is
per-operation, which can mean per-tool-invocation
within a single conversation. A single customer-service
agent conversation may generate 10–50 tool invocations;
each is a trust-architecture decision.

Throughput requirements differ accordingly. A trust
gate that is adequate at a per-session granularity is
not necessarily adequate at a per-operation
granularity. Chapter 5 §5.3 addresses the latency
budget directly.

The adaptations: **dynamic identity composition**
(Chapter 3), **intent-aware authorisation** (Chapters
3 and 5), **per-operation policy evaluation** (Chapter
5). Where the next chapters disagree with 800-207's
exact wording, they do so to preserve the discipline
800-207 encodes.

## 2.3 The blast-radius framing

NIST 800-207 implies but does not name what is, for AI
agents, the operationally most important framing: the
*blast radius* of an unauthorised operation.

Blast radius for AI agents is unusually large because:

- **Tool chaining amplifies.** A single agent
  operation may touch multiple downstream services —
  an email agent that reads a document, summarises
  it, drafts a reply, and sends the reply has
  touched four services in a single logical
  operation. If one of those services is
  mis-authorised, the mis-authorisation cascades.
- **Natural-language reasoning is manipulable.** An
  agent's "decision" to take an action is often a
  natural-language reasoning step. If that step is
  compromised (prompt injection, hallucination,
  jailbreak), the agent's intent is adversarial while
  its identity remains legitimate. Downstream services
  that trust identity will execute the compromised
  intent.
- **Recovery may be impossible.** An agent that sends
  a customer email, posts to a public channel, or
  initiates a payment has produced an action that
  cannot be retracted by removing the agent's access.
  Posterior cleanup is often more expensive than
  prior prevention.

The trust-architecture implication: where blast radius
is large, the *prior authorisation* gates matter more
than the *posterior detection* gates. Architecture
should fail closed; bypassing the trust gate should
not be the default fast path; the gate should be in
the critical path for any operation that has
externally-visible effects.

A useful operational heuristic: for each operation an
agent can perform, write one sentence describing
"what breaks if this operation is unauthorised and
executes anyway?" If the answer involves money leaving
the firm, a customer receiving a message, a record
being written to a system of truth, or a public post
appearing, that operation is high blast radius and
deserves a correspondingly rigorous gate. If the
answer is "the agent sees data it should not have
seen, but no state changes externally", the operation
is lower blast radius and may be gated more cheaply.

## 2.4 Worked example — mapping 800-207 to a customer-service agent

To make the mapping concrete, consider a stylised
customer-service agent with four capabilities: read
account state, compose customer messages, initiate
disputes, transfer funds between the customer's own
accounts. Mapping each tenet to the design:

| Tenet | How this agent's architecture satisfies it |
|---|---|
| Resources | Account-read API, disputes API, transfers API, message service, LLM endpoint — each is a resource with its own authorisation policy |
| Secured communication | mTLS between agent and every downstream service; no reliance on network location |
| Per-session basis | Each tool invocation presents a fresh capability assertion; prior invocations do not extend authority |
| Dynamic policy | Transfers evaluated against (customer identity, amount vs 90-day pattern, time of day, agent posture); disputes evaluated against (customer identity, open-dispute count) |
| Posture monitoring | Agent configuration hash is attested at start of session; LLM endpoint vendor and version are logged; downstream resource health is tracked |
| Dynamic authn/authz | Capability assertions expire in 15 minutes; revocation list checked at each gate; no standing privilege |
| Posture feedback | Each decision emits a signed event; events feed trust-score refinement and policy tuning |

An architecture that answers all seven columns is not
necessarily good — it may be slow, brittle, or hard to
operate — but it is at least structurally complete. An
architecture that cannot answer one of them has a
load-bearing gap that will produce an incident, and
usually a public one.

## 2.5 What a CAO reads for in a zero-trust-for-AI proposal

A proposal lands on your desk from the CISO or CTO
claiming to apply zero-trust principles to the firm's
agent portfolio. Four things to check, as a CAO:

1. **Does the proposal name the three agent-specific
   adaptations?** If it reads like 800-207 applied
   unchanged — static workload identity, static policy,
   per-service authorisation — the authors have not
   done the agent adaptation. Expect prompt-injection
   failures.
2. **Does the proposal include a blast-radius ranking
   of agent operations?** If every operation is treated
   the same, high-stakes operations are under-gated
   and routine operations are over-gated. Both are
   failures.
3. **Does the proposal address revocation?** 800-207's
   "no standing privilege" tenet is operationally
   enforced through short-lived credentials and active
   revocation. A proposal silent on revocation has not
   finished the zero-trust work.
4. **Is the posture-feedback loop named?** The seventh
   tenet is the one most often skipped. A gate that
   logs decisions but never improves from the log is
   not realising the posture-feedback discipline.

A CAO who asks these four questions and names where
the proposal is weak has done the CAO job on this
chapter.

## Summary

- NIST SP 800-207 is the structural inheritance for
  AI trust architecture. Its seven tenets translate
  cleanly to AI agents when adapted deliberately.
- Three places the framework needs adaptation: agent
  identity is composite (not static), intent is
  generated at runtime (not pre-coded), enforcement
  must be per-operation (not per-service). Chapters
  3–5 build out each.
- Blast radius is the operationally most important
  framing 800-207 implies but does not name.
  High-blast-radius operations get prior-authorisation
  gates; posterior detection is not a substitute.
- A CAO reading an AI zero-trust proposal reads for
  the three adaptations, a blast-radius ranking, a
  revocation story, and a posture-feedback loop.
  Proposals missing any of these have load-bearing
  gaps.
