# Chapter 4 — Trust Scoring: Deterministic vs Heuristic

## Why this chapter exists

Chapters 1–3 built identity and capability — the
*who* and *what*. This chapter builds the *how
confident* layer: trust scoring. A trust score is a
quantification of trust that a gate uses as input to
its authorisation decision. The question that divides
practitioners is whether that score should be computed
from verifiable facts by a function the operator can
inspect, or inferred from behavioural signals by a
model that adapts over time.

The posture this chapter defends: for scores used in
**authorisation decisions**, deterministic is the right
default; heuristic scoring has a place *adjacent to*
authorisation, not *as* authorisation. The chapter
makes the argument explicitly so a CAO can defend the
posture to a regulator, an auditor, or a vendor pushing
a learned-score product. Exercise 02 forces authoring a
four-axis deterministic score with explicit math.

## 4.1 The deterministic approach

A deterministic trust score is computed from inputs the
system can specifically verify, by a function the
operator can inspect. Inputs are signed events,
attestation artifacts, capability assertions, and
posture indicators. The function is rule-based or
weighted-sum based; given the same inputs, it produces
the same score.

**Properties of deterministic scoring:**

- **Reproducible.** The same inputs produce the same
  score. A post-mortem four months after the fact
  reproduces the gate's decision exactly.
- **Auditable.** The operator can inspect why a score
  is what it is. The reasoning chain is open to
  examination.
- **Defendable.** Explainable to regulators, to
  customers in contestability processes (mod-105
  Chapter 5), to internal review.
- **Limited.** Can only score what is verifiable;
  cannot capture subtleties no signed event reflects.
  A deterministic score cannot say "this operation
  feels off" if no verifiable signal reflects that
  feeling.

**Where it fits:** high-stakes authorisation decisions
(payments, customer-facing actions, regulated-domain
operations), regulator-facing trust attestations,
decisions a post-mortem must reconstruct.

## 4.2 The heuristic approach

A heuristic trust score is computed from observable
signals, many of which are proxies for trustworthiness.
Inputs may include historical agent performance,
response-pattern similarity, anomaly detection signals,
peer agent comparisons. The function is often a
learned model.

**Properties of heuristic scoring:**

- **Captures patterns deterministic scoring cannot.**
  Behavioural drift, subtle anomalies, cross-agent
  correlations.
- **Adapts to new threats or behaviours.** Learns
  from history.
- **Performant.** Usually fast at inference.
- **Opaque.** The operator may not be able to inspect
  why a score is what it is. A learned model is
  explainable only to the extent its
  explanation layer is adequate.
- **Brittle.** Subject to its own bias, drift, and
  adversarial manipulation. A learned score is itself
  a model and inherits all the risks mod-104 names.

**Where it fits:** detection-style use cases (anomaly
flagging, prioritisation, secondary signal alongside
deterministic gating), posture monitoring (how is this
agent behaving over time?), where speed matters more
than defendability.

## 4.3 The deterministic-is-better posture, defended

For trust scoring used in **authorisation decisions**,
deterministic is generally the right posture. Four
reasons, each worth being able to state cleanly.

### 4.3.1 Defendability

A regulator, an auditor, or a customer challenging an
authorisation decision needs to know why. A
deterministic score can be explained in a sentence:
"the identity attestation was 5 minutes old (score 95),
the operation matched a signed capability (score 100),
the amount was within envelope (score 100), the
customer's session was active (score 100). Total 98,
threshold 70, allowed."

A heuristic score requires explaining a model, which
is harder and more vulnerable to inspection challenges.
"Our model learned that operations of this shape by
agents of this class are typical" is not an answer the
regulator will accept when the agent authorised a
fraudulent transfer.

### 4.3.2 Reproducibility

When an incident occurs and the post-mortem asks why
the trust gate authorised the operation, a
deterministic score reproduces exactly from the
inputs. The signed events, the attestation at the
time, the policy version — all re-combinable.

A heuristic score may have shifted by the time the
post-mortem runs. The model may have been retrained
twice; the signals that drove the score at decision
time may be different signals today. The question
"what score did the gate assign at 14:03:17?" may be
unanswerable.

### 4.3.3 Adversarial robustness

A heuristic score is itself a model, subject to
adversarial manipulation. A sophisticated attacker may
craft operations that game the score — present
features the model has learned to associate with
trustworthiness. mod-107 Chapter 3 covers the attack
patterns in detail.

Deterministic scoring computed from cryptographic
attestations is harder to game. The signature either
verifies or does not; the expiration either holds or
does not; the capability either matches or does not.
The attacker's path is forging the attestation, which
is a cryptographic attack, not a feature-engineering
attack.

### 4.3.4 Maintenance cost

Heuristic models drift and need retraining. Retraining
requires fresh labels, which for authorisation
decisions means confirmed-bad examples — rare and
expensive. The model needs validation (per mod-104)
every retrain; the validation feeds back into the
trust gate's auditability story.

Deterministic scoring functions change only when the
operator changes them. Change-control is a policy
operation, not a modelling operation. The maintenance
burden is lower, and more importantly, the burden is
*in the right place* — on the policy, where the CAO
can see it.

### 4.3.5 Where heuristic scoring still fits

The posture is not "no heuristics ever". Heuristic
scoring has a place:

- As an **adjacent signal** that triggers step-up
  authentication (Chapter 5 §5.5) — the gate still
  authorises deterministically, but the heuristic flags
  the operation for additional evidence.
- For **posture monitoring** — tracking how an agent's
  behaviour is evolving over time, feeding back into
  deterministic policy refinement.
- For **triage prioritisation** — of the operations the
  gate allowed, which ones most warrant human review?

A program that uses heuristic scoring to flag-for-
review combined with deterministic scoring to authorise
has both advantages: the deterministic gate is
defendable, the heuristic signal catches patterns the
gate alone would miss.

## 4.4 The trust-score axes

A useful pattern: trust scoring on **multiple
orthogonal axes** rather than a single combined score.
Single combined scores collapse information; a 70/100
could mean "very strong on three axes, weak on one" or
"moderate on all four", and the gate needs to make
different decisions in those two cases.

A common four-axis structure:

| Axis | What it measures | Example inputs |
|---|---|---|
| **Identity** | Strength of identity verification | Signature freshness; revocation status; delegation-chain completeness; attestation issuer trust level |
| **Risk** | Risk profile of this operation in context | Operation blast radius; amount relative to pattern; recipient reputation; time of day; posture signals |
| **Reliability** | Track record of this agent (or its class) over recent history | Successful-operation rate; recent policy violations; drift signals; validation-cycle recency |
| **Autonomy** | Level of independent decision-making the operation requires | Human-in-the-loop presence; recency of principal interaction; agent reasoning-chain depth |

For each axis, a deterministic computation produces a
score in a bounded range (typically 0–100 or 0.0–1.0).
The trust gate's authorisation logic considers all
axes jointly.

This is the *4-axis pattern* used by several
practitioners — VeriSwarm Gate is one; Cloudflare AI
Gateway uses a similar shape with different specific
axes; IBM watsonx.governance varies the structure.
None is the canonical answer. The pattern (multiple
orthogonal axes, deterministic per-axis scoring,
policy-level decision logic on top) is reusable across
implementations.

### 4.4.1 A worked example — identity-axis scoring

Making the math concrete. The Identity axis for the
Tessera customer-service agent:

```
IDENTITY_SCORE =
    40 * signature_valid        # 1 if JWT signature verifies, 0 otherwise
  + 20 * freshness_factor       # linear decay: 1.0 at iat, 0.0 at exp
  + 20 * revocation_clean       # 1 if jti not in revocation list, 0 otherwise
  + 10 * amr_strength           # 0 if no auth; 0.5 if password; 1 if pwd + 2fa
  + 10 * delegation_verified    # 1 if full delegation chain verifies, 0 if partial, −∞ if broken

bound to [0, 100]
```

Reading the function:

- `signature_valid` is binary. An unsigned or
  tampered manifest scores zero on this component.
  Because the component is worth 40 of 100 points,
  any realistic threshold will reject.
- `freshness_factor` decays linearly. A manifest
  fresh out of issuance scores 20; one with 10
  seconds left before expiry scores close to zero.
  Encodes "trust decays with age".
- `revocation_clean` cliff-drops to zero if the
  manifest has been revoked. A revoked manifest
  loses 20 points instantly.
- `amr_strength` reflects the authentication method
  used by the principal. Password-only principals
  carry less identity confidence than 2FA'd ones.
- `delegation_verified` enforces the chain. A broken
  chain scores negative infinity — in practice, a
  deny decision — because the delegation is being
  claimed but cannot be verified.

A developer could implement this function from the
specification in an afternoon. An auditor reading the
specification can reproduce any score given the
inputs. That is the discipline deterministic scoring
is for.

Exercise 02 asks for similar specificity on all four
axes.

## 4.5 Decision logic on top of the axes

Having scored each axis, the gate still has to decide.
Three common decision logics:

**Threshold on each axis.** All axes must exceed a
per-axis threshold; any axis below triggers deny or
step-up. Simple; preserves the orthogonal information;
easy to defend.

```
if IDENTITY >= 80 and RISK <= 30 and RELIABILITY >= 60 and AUTONOMY <= 50:
    return ALLOW
elif IDENTITY >= 70 and RISK <= 50:
    return STEP_UP
else:
    return DENY
```

**Weighted sum with floor.** Each axis contributes to
a composite score; a floor on each axis prevents a
very-high score on one axis from compensating for a
critical weakness on another. More flexible; harder to
explain in a single sentence.

**Policy matrix.** A decision table across the four
axes. Explicit about every combination; readable; can
grow unwieldy if the matrix is large.

The threshold-on-each-axis pattern is the most
defendable and the easiest for a regulator to
understand. The reference solution for Exercise 02 uses
this pattern.

Across all three logics, the **step-up option** is
important: the right output of a trust decision is
sometimes neither allow nor deny but "I need more
evidence". Chapter 5 §5.5 covers step-up patterns in
detail.

## 4.6 The event vocabulary problem

A working deterministic trust system depends on a
*vocabulary of signed events* — a standardised set of
event types the agent ecosystem emits and the trust
gate consumes. The vocabulary needs to be:

- **Comprehensive** enough that meaningful operations
  are captured.
- **Specific** enough that events are unambiguous.
- **Stable** enough that ecosystem participants can
  emit compatible events.

Without a shared vocabulary, every integration becomes
custom. The gate ends up with heuristic parsing of
free-form agent logs, which defeats the determinism
the architecture is for.

Practitioner patterns in 2026:

- **VeriSwarm's event vocabulary** — a working set of
  event types for agent operations, openly defined;
  emit events from any agent ecosystem into a shared
  trust score. Specific to a vendor's architecture.
- **OpenTelemetry's evolving GenAI semantic
  conventions** — community-maintained event
  vocabulary with broadening adoption; less
  trust-architecture-specific, more
  observability-oriented. Converging but not yet
  settled.
- **Roll-your-own** with project-specific event types
  — works for closed ecosystems, doesn't compose with
  others.

There is no settled standard as of 2026. CAO programs
operating across multiple agent ecosystems should
expect to invest in event-vocabulary discipline:
agreeing an internal vocabulary, mapping vendor events
to it, and insisting that new agent systems emit events
in the agreed shape. The investment pays back when the
posture-feedback loop (Chapter 2 §2.1) can draw signal
from all agents on the same terms.

## 4.7 What a CAO reads for in a trust-scoring proposal

Four tests, as a CAO:

1. **Is the scoring deterministic where it drives
   authorisation?** A proposal that uses a learned
   model to allow or deny high-stakes operations
   should be challenged. Heuristic scoring is a
   secondary signal; it is not the gate.
2. **Are the axes orthogonal and separately
   defensible?** A single combined score is a smell.
   Multiple orthogonal axes let the gate make
   different decisions in different weakness patterns.
3. **Can every decision be reproduced from signed
   inputs?** If the post-mortem for an incident cannot
   reconstruct the score, the architecture is not
   defendable.
4. **Is the event vocabulary named?** A trust-scoring
   proposal silent on how events are emitted and
   consumed is incomplete. Insist on specificity.

A proposal that passes these four tests may still be
wrong on specifics — the axes may be badly chosen, the
math may be badly weighted — but it is at least
addressable. A proposal that fails any of them has a
load-bearing gap.

## Summary

- Two broad approaches: deterministic (computed from
  verifiable inputs by an inspectable function) and
  heuristic (inferred from observable signals, often
  by a learned model).
- For authorisation decisions, deterministic is the
  right default: defendable, reproducible,
  adversarially robust, lower maintenance.
- Heuristic scoring still has a place — adjacent to
  authorisation, triggering step-up, feeding posture
  monitoring — not as the authorisation itself.
- The four-axis pattern (Identity, Risk, Reliability,
  Autonomy) is a working structure; the discipline is
  specifying inputs, math, and ranges per axis so
  developers can implement and auditors can reproduce.
- Decision logic on top of the axes should be rule-
  based; threshold-on-each-axis is the most defendable
  shape.
- The event vocabulary is the under-specified
  foundation. Programs should expect to invest in
  vocabulary discipline, especially across multiple
  agent ecosystems.
