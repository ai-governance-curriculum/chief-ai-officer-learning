# Chapter 3 — Event Vocabulary for AI Systems

## Why this chapter exists

Chapter 2's cryptographic machinery is necessary but
not sufficient. A ledger with impeccable integrity
properties and the wrong events in it fails the audit.
The CAO's attention has to extend from the structure
of the ledger to the vocabulary of what the program
puts into it.

Vocabulary is where many programs underinvest. The
engineering function tends to emit what is
operationally convenient; the compliance function
tends to ask for what regulators have historically
wanted; neither asks the shared question — *what
events, at what granularity, with what fields, would
let the program reconstruct any in-scope operation
three years later and defend it to an auditor?* This
chapter is that question's working answer.

## 3.1 The granularity problem

Two failure modes bracket the right answer.

**Under-granular.** Events are aggregated. One event
records "agent operated successfully" for an hour of
operations, or "100 customer sessions completed."
Operational dashboards are satisfied; the auditor
cannot trace individual decisions, and the program
cannot answer "what happened to customer X at 14:03"
in a defensible way.

**Over-granular.** Events are emitted for every
function call, every cache hit, every internal message
pass between agent subcomponents. The ledger overflows.
Query performance degrades. Retention costs balloon.
The auditor cannot find what matters because
everything is in the way. The program's own analysts
stop using the ledger because it is unusable.

The right granularity for CAO evidence is **the level
of operations that have program-relevant
consequences** — one evidence event per agent action
that affects principals, resources, or external state.
A single customer-facing operation that invokes three
tools and makes two authorisation decisions produces
on the order of five to six evidence events, not
hundreds, and not one.

A working test: *would the program want to reconstruct
this operation at year+3 if the program were
challenged?* If yes, emit as evidence. If no,
operational logging is sufficient. The test is
subjective enough that reasonable people disagree at
the margins; it is objective enough that gross
mistakes in either direction become obvious.

## 3.2 The completeness problem

A working event vocabulary covers at least seven
categories. A vocabulary that is missing any one of
them has gaps that will surface at the first serious
audit.

- **Authorisation events.** Per-operation decisions by
  trust gates (per `mod-106` §5.2 — the gate's
  decision, inputs, and reasoning). Every allowed and
  every denied operation. Missing this category and
  the program cannot defend "the agent operated
  within its capability scope" to a regulator.
- **Capability assertions.** Manifest issuance,
  revocation, and verification events. Every time a
  capability manifest changes, and every time an
  agent asserts a capability it holds. Missing this
  and the program cannot defend "the agent held the
  right scope at the time of the operation."
- **Tool invocations.** Per-tool calls by agents, with
  input and output *references* (the content lives in
  object storage; the event records what was called,
  with what hash of input, producing what hash of
  output). Missing this and the program cannot
  reconstruct what the agent actually did.
- **Model interactions.** Calls to underlying models
  — which model identity, which version,
  configuration hash, references to the input and
  output artifacts. Missing this and the program
  cannot defend "which model made this decision" when
  the model fleet rotates.
- **State changes.** Material changes to data the
  agent reads from or writes to. Missing this and the
  program cannot distinguish an agent that read
  something stale from one that was given stale
  input.
- **Configuration changes.** Changes to agent system
  prompts, tool lists, capability scopes, policy
  parameters. Missing this and the program cannot
  defend "what the agent was configured to do during
  the period in question."
- **Incident-relevant signals.** Detections by
  monitoring — drift signals, anomaly flags,
  threshold crossings — *even when no immediate
  action is required*. Missing this and the program
  cannot defend "what the monitoring saw." The
  monitoring that fired but was not acted on is
  often the most consequential record at audit time.

A program whose vocabulary is missing any of these has
incomplete evidence; the gap will be exactly where the
first regulator inquiry lands, because that is where
regulators have learned to ask.

## 3.3 What goes in an event

Each evidence event should include, at minimum, the
following envelope:

| Field | Why it is required |
|---|---|
| Event ID | Unique identifier within the ledger |
| Event type | Vocabulary classification; maps to the registry (§3.4) |
| Timestamp | When the event occurred (system clock); ideally also a TSA timestamp (RFC 3161, see Chapter 5 §5.2) |
| Actor | The agent / service / user that produced the event |
| Subject | The entity the event concerns (customer, resource, account) |
| Operation | The specific action |
| Result | Success / failure / deferral — never only success |
| Reason / context | Sufficient context to interpret the event later without re-reading surrounding events |
| References | Pointers to related larger artifacts (model identity hash, configuration hash, policy version, input/output content hashes) |
| Signing key reference | The key used to sign the event |
| Prior event hash | For the hash chain (per Chapter 2 §2.2) |

The *reference-rather-than-include* pattern deserves
emphasis. Events should be small — on the order of
kilobytes, not megabytes. Large artifacts — model
weights, full prompts and responses, full input
documents, full tool-call payloads — belong in object
storage, addressed by content hash, with the event
carrying the hash reference. This keeps the ledger
compact (which matters at long retention), keeps the
cryptographic operations fast (which matters at
emission latency), and allows selective disclosure
(the event can be shared without necessarily sharing
the referenced content).

## 3.4 The vocabulary registry

A working program maintains a **vocabulary registry**:
the catalog of event types the program recognises,
with definitions, expected fields, and emission rules.
The registry is itself versioned, and changes to the
registry are themselves events in the ledger.

Without a registry, three failure modes appear
predictably:

- **Novel field names.** New systems emit events using
  field names that the analysis layer does not
  recognise. Reporting pipelines silently drop them.
  The event was captured; the analysis was not.
- **Type proliferation.** Event types accumulate over
  time. `tool_invoke`, `tool_invocation`,
  `tool_call`, `agent_tool_use` all appear in the
  ledger with slightly different field sets. Auditors
  cannot tell which types are equivalent. Analysis
  queries miss events because they filter on the
  wrong type name.
- **Semantic drift.** The same event type's meaning
  changes over time without the change being
  recorded. "Authorisation event" means something
  different in Q1 than Q3; evidence from Q1 is now
  misinterpreted when analysed in Q3.

A registry prevents each of these by making the
vocabulary explicit, enforceable, and versioned. The
registry is part of the CAO function's standards work
(`mod-105` §6.1 referenced ethics in standards; the
same discipline applies to this technical standard
even though the content is different).

## 3.5 A worked example

A customer-service agent processing a funds-transfer
request produces the following evidence events, in
order, for a single operation:

```
1. authorisation.evaluated          (gate decision: allow;
                                     capability scope cited;
                                     policy version referenced)
2. capability.asserted              (agent asserted holding
                                     "transfer_funds" within
                                     $500 scope)
3. tool.invoked                     (tool: funds_transfer_api;
                                     input hash; output hash;
                                     result: success)
4. state.changed                    (account balance updated;
                                     before/after reference by
                                     hash)
5. authorisation.recorded.outcome   (operation's outcome
                                     bound back to the gate
                                     decision for closure)
```

Five events for one customer operation. Each is a leaf
in the Merkle tree (Chapter 2 §2.1). Each is linked by
`prior_event_hash` to the previous event in the hash
chain within this batch. Each references supporting
artifacts (the policy version, the capability manifest,
the input/output content) by hash rather than including
them. Three years later, an auditor can reconstruct
exactly what happened, with inclusion proofs for each
event and content integrity for each referenced
artifact.

A program that emits one event — `operation.completed`
— for the same work can tell the auditor that the
operation completed, and nothing else of substance.
A program that emits fifty events for the same work
has drowned the evidence in noise.

## 3.6 Practitioner patterns

The current event-vocabulary landscape as of 2026:

- **OpenTelemetry GenAI semantic conventions.** The
  closest to community consensus for LLM and agent
  event types. The specification is still evolving;
  programs adopting it should expect to track changes
  for the next several years. The right starting
  baseline for new programs.
- **CloudEvents 1.0.** Generic event envelope; used
  as a base by several AI-specific vocabularies.
  Does not define AI-specific types but provides a
  stable transport-neutral envelope.
- **Commercial AI-governance platform vocabularies.**
  Several vendors ship a vocabulary with their
  product. Variable quality; programs should treat
  the vocabulary as something to evaluate alongside
  the ledger (an auditable product should document
  its vocabulary explicitly).
- **Roll-your-own** with project-specific event
  types. Workable; programs that go this route
  should still document the vocabulary in a
  registry (§3.4) and should expect to maintain it
  as the system evolves.

No standard has fully settled in 2026. The CAO's
position: pick a *baseline* (OpenTelemetry GenAI or a
practitioner reference) and extend it with program-
specific events as needed. Document the extensions in
the vocabulary registry. Expect to re-align with the
baseline as it stabilises.

## Summary

- Granularity for CAO evidence is one event per
  program-relevant operation — not per function call,
  not per hourly aggregate. The working test is
  whether the program would want to reconstruct this
  operation at year+3.
- A complete vocabulary covers seven categories:
  authorisation, capability assertions, tool
  invocations, model interactions, state changes,
  configuration changes, and incident-relevant
  signals. Missing categories are gaps that will
  surface in the first serious audit.
- Each event carries a standard envelope (ID, type,
  timestamp, actor, subject, operation, result,
  reason/context, references, signing key, prior
  event hash). Large artifacts are referenced by
  content hash rather than embedded.
- The vocabulary registry is the versioned catalog of
  event types. Without a registry, programs
  experience novel-field, type-proliferation, and
  semantic-drift failure modes that only surface at
  audit time.
- OpenTelemetry GenAI semantic conventions are the
  best starting baseline in 2026; expect extensions
  and ongoing re-alignment as the specification
  matures.
