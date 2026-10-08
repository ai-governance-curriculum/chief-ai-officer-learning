# Chapter 3 — Defense-in-Depth for AI Systems

## Why this chapter exists

Defense-in-depth is the security principle that no single
control should be sufficient to prevent compromise; multiple
layered controls handle the case where any individual
control fails. The principle is classical — NIST SP 800-39
and SP 800-53 encode it for information systems in general
— and it transfers to AI systems *in principle* without
difficulty.

What does not transfer without work is the layer model.
The classical-perimeter model (network → host → application
→ data) misses layers that are first-order for AI systems
— the model layer, the tool layer, the output layer — and
over-weights layers that AI systems share with everything
else. A CAO who imports the classical model unchanged
produces an "AI security program" whose weak links are
exactly the AI-specific ones.

Exercise 05 asks you to author a program-level
defense-in-depth standard. This chapter is the layer
model that standard is written against.

## 3.1 The nine layers of an AI system

A working defense-in-depth for AI systems considers
defences at:

1. **The principal layer** — authentication and
   authorisation of the principal (user, service, agent's
   invoking principal). See `mod-106` Chapter 3 for the
   composite-identity treatment.
2. **The input layer** — what the system accepts as
   input; content-based filtering; input validation;
   adversarial-input detection; prompt injection
   detection for LLM systems.
3. **The model layer** — the model itself: its
   training-data provenance, its alignment, its
   robustness properties, its version pinning.
4. **The output layer** — what the system emits; output
   filtering; format constraints; PII detection; harmful
   content filtering; secret-leakage prevention.
5. **The tool layer** — for agentic systems: which tools
   are reachable from the agent, with what authority,
   with what audit. The trust-gate pipeline from `mod-106`
   Chapter 5 is this layer's primary mechanism.
6. **The data layer** — what data the system can read or
   write; access control; encryption at rest and in
   transit; data classification; retention and deletion.
7. **The infrastructure layer** — the runtime
   environment: container security, network isolation,
   secrets management, image signing.
8. **The observability layer** — what is logged; what is
   monitored; what triggers alerts; what feeds the audit
   ledger (`mod-108`).
9. **The response layer** — what happens when an alert
   fires: kill switches, rollback, notification,
   containment, post-mortem.

A program with defences at all nine layers is
*structurally complete*; programs missing layers have
characteristic blind spots.

## 3.2 The common blind spots

Programs that miss defences at specific layers do so in
predictable ways. The three most common:

**The tool layer.** Agentic systems add the tool layer
to the threat surface. Many programs apply classical API
security (the service-to-service calls are
authenticated, rate-limited, logged) but do not
separately control which tools the AI agent can invoke.
The failure mode: a prompt injection succeeds in
causing the agent to invoke a tool it has API-level
permission to invoke but should not have been reasoning
about. The classical-API security did not stop it
because the API call itself was authorised.

**The output layer.** Input filtering is well-understood;
output filtering is often an afterthought. The failure
mode: the agent is prompted for data it has access to,
produces that data in the output, and the output is
delivered to a party that should not have had it. The
output layer is the last chance to stop exfiltration
from being delivered.

**The response layer.** Detection without response is
governance theatre. A program where an alert fires and
produces no documented response — because nobody
rehearsed the playbook, because the kill switch was
never wired up, because the on-call rotation does not
include someone who understands the AI system — is a
program in name only.

`mod-105` §6 (operationalising ethics) named the
governance-theatre risk; the AI security version is
*security-theatre*: alerts that nobody acts on, playbooks
nobody runs, kill switches that have never been tested.

## 3.3 The non-classical layers

Two layers that AI defense-in-depth needs but classical
defense-in-depth does not emphasise.

### 3.3.1 The model layer

The model is not an "application" in the classical sense;
it is an artifact whose behaviour you did not fully
specify and may not fully understand. Model-layer
defences:

- **Training-data integrity controls.** Datasheets, data
  provenance tracking, signed data manifests. The
  training-data layer is a supply-chain surface in its
  own right.
- **Alignment training.** RLHF, constitutional methods,
  safety fine-tuning. The CAO is not deciding
  implementation; the CAO is deciding whether alignment
  is a layer the program expects a model to pass through
  before deployment.
- **Model-version pinning.** Where the firm controls it
  (self-hosted or inference-API with pin-support),
  version is specified; where the vendor controls it,
  the firm's exposure to silent swaps is logged and
  monitored (continuity with `mod-104` Exercise 04).
- **Model behavioural evaluation.** Pre-deployment and
  on-change evaluation against the firm's threat model
  — not merely benchmark accuracy, but adversarial
  behaviour under the §1.2 real-threat categories.

### 3.3.2 The tool layer

For agentic systems, which tools the agent can invoke is
a first-order security property. Tool-layer defences:

- **Capability scoping.** Per `mod-106` §3.2 — the agent
  carries a signed capability manifest; tools outside
  the manifest are not callable.
- **Tool allowlist enforcement.** The orchestrator (not
  the agent, which is manipulable) decides which tool
  calls are permitted.
- **Per-tool authorisation evaluation.** Each tool call
  carries its own authorisation decision; permission to
  invoke tool A does not extend to tool B.
- **Tool-output sanitisation.** Output from a tool is
  treated as untrusted content before it is returned to
  the agent, because an agent reasoning over
  attacker-controlled tool output is a prompt-injection
  surface.

A program that addresses input and output but not model
and tool layers has *partial* defense-in-depth, not full.

## 3.4 The cost-benefit reality

Defense-in-depth is not free. Each layer adds latency,
complexity, and operational cost. The right depth depends
on the system's blast radius (per `mod-106` §2.3). Three
principles:

### 3.4.1 Depth should track blast radius

High-blast-radius operations get all nine layers.
Routine, low-blast-radius operations may operate with
fewer. A customer-service agent initiating a $10,000
funds transfer should go through every layer; the same
agent summarising public documentation can skip layers
that would otherwise impose latency without
proportionate protection.

Tiered application (per `mod-104` Chapter 2) is the
discipline for making the "which layers at which depth"
decision defensible. Exercise 05 requires it.

### 3.4.2 Correlated-failure layers are one control

Two input-filter layers using the same regex library
are not two controls — they are one control with two
instances. Two input-filter layers, one regex-based and
one model-based, are two controls, because their
failure modes are uncorrelated.

Programs that claim defense-in-depth by stacking
instances of the same technique are producing an audit
artifact, not a defence.

### 3.4.3 The bypass test

A layer that an attacker can skip without consequence is
a layer providing no protection. Defense-in-depth is
about layers the attacker must bypass *each one, in
series* — not layers that happen to exist somewhere in
the architecture.

The bypass test as a question: for each layer, can the
attacker reach the next layer without defeating this
one? If yes, the layer is not load-bearing. Programs
that pass the bypass test are rare in the field; most
"defense-in-depth" diagrams have at least one bypassable
layer.

### 3.4.4 Latency and operability budgets

Each layer imposes some latency and some operational
burden. The CAO's job is not to optimise latency — that
is the engineering team's — but to be aware that
defense-in-depth that renders the system unusable gets
turned off. A standard that is routinely disabled is a
standard that does not exist.

The operational test: can the engineering team maintain
all nine layers for all Tier-1 systems with the staff
they have? If not, either staffing changes or the layer
model does.

## 3.5 Composing layers across the request path

The layers are not just independent controls — they
compose along the request path:

```
User → Principal gate → Input layer → Model → Tool layer
     → Downstream resource → Output layer → User
                                 ↑                ↑
                        Data layer gates    Output filters
                        apply at each       apply on the
                        resource boundary   way out
                                 ↑                ↑
                        Infrastructure (containers, mTLS, secrets)
                                 ↑
                        Observability (every arrow is logged)
                                 ↑
                        Response (observability feeds response)
```

The composition is not visible in a flat enumeration of
layers; a program-level standard that lists the layers
without naming how they compose produces an operations
guide that cannot be executed. Exercise 05's dependency-
analysis section forces this out.

## 3.6 What the CAO reads for in a defense-in-depth proposal

Six questions:

1. **Are all nine layers present?** Missing layers are
   not accidental; they signal where the program's
   historical centre of gravity has been.
2. **Is the model layer substantive?** A program that
   lists "model layer" with one bullet about alignment
   is treating the model as a black box. The model-
   layer defences in §3.3.1 should each have a position.
3. **Is the tool layer substantive, where agentic?** A
   program with agentic systems and no tool-layer
   section has an uncovered surface.
4. **Is tiered application specified?** All nine layers
   for all systems is both impossible and
   unprioritised. The standard should say which layers
   at which tier.
5. **Is the bypass test addressed anywhere?** A standard
   that claims nine layers without naming which ones
   are bypassable has not finished the work.
6. **Is the response layer wired to actual response?**
   The playbooks are named; the on-call rotation is
   named; the kill switches have been tested. If not,
   it is security-theatre.

A CAO who can hold these six questions open through the
engineering team's defense-in-depth briefing is doing
the CAO's job on this chapter.

## Summary

- Defense-in-depth for AI systems requires nine layers:
  principal, input, model, output, tool, data,
  infrastructure, observability, response. The layer
  model differs from classical perimeter defence in
  three load-bearing additions (model, tool, response-
  wiring).
- The three most common blind spots are the tool layer,
  the output layer, and the response layer. Programs
  missing any of these produce predictable incident
  patterns.
- The model and tool layers are the AI-specific
  additions. Programs that address only input and output
  have *partial* defense-in-depth, not full.
- Three cost-benefit principles: depth tracks blast
  radius, correlated-failure layers count as one, the
  bypass test is binary. Programs that violate any
  produce defence that looks real on paper and is thin
  in practice.
- Layers compose along the request path; a flat
  enumeration without composition is an operations
  guide that cannot be executed.
- The CAO reads a defense-in-depth proposal for all
  nine layers, substantive model and tool treatments,
  tiered application, the bypass test, and the response-
  wiring reality.
