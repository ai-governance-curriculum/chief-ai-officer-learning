# Chapter 3 — Continuous Evidence Collection

## Why this chapter exists

Chapter 2 built the control map. Chapter 3 answers the
operational question that follows: once a control
exists, how does the program *know* it is operating?
The default answer — "we check at audit" — is the
quarter-end scramble from Chapter 1 §1.2. The
disciplined answer is **continuous evidence
collection**: the control produces evidence as a side
effect of its normal operation, the evidence is
captured in the audit ledger ([`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)),
and someone reviews it on a cadence shorter than the
audit cadence.

This chapter is the operational discipline that
converts a control catalog from paper to practice. It
is also the chapter where the distinction between
**operational logging** and **audit-grade evidence**
(mod-108 Chapter 1) becomes decisive: if what the
control emits is not evidence, the continuous
collection is still continuous and still useless.

## 3.1 What *continuous* means

Continuous evidence collection means three things
simultaneously:

- **Evidence is produced** as a side effect of the
  control's normal operation, not by a separate
  evidence-production task. The quarterly bias review
  does not produce evidence by writing a quarterly
  report; it produces evidence by *being a review that
  someone did*, captured as it happens.
- **Evidence is captured** in the audit ledger per
  mod-108 immediately — with provenance,
  completeness, and tamper-resistance properties
  intact. "Immediately" means within minutes, not
  within days.
- **Evidence is reviewable** by the control owner on a
  defined cadence shorter than the audit cadence. If
  the audit cadence is annual, the review cadence is
  not annual.

A control whose evidence is only checked at audit time
is being *audited*, not *operated*. The regulator sees
the difference immediately: a control that nobody
reviewed between audits is a control the organisation
did not actually operate — it was just one that nobody
looked at until forced to.

## 3.2 The three review cadences

A working compliance operation runs **three review
cadences per control**. Each cadence has a different
reviewer, a different question, and a different
artifact. All three are necessary; dropping any one
produces a specific failure mode.

| Cadence | Reviewer | Question answered | Typical artifact |
|---|---|---|---|
| **Operating cadence** | Control owner (first-line or second-line, per control) | Is the control operating today? Does the evidence show expected shape? | Signed review record |
| **Steward cadence** | CAO function / compliance-operations lead | Have all owners attested for the period? Are any controls silent? | Portfolio status report |
| **Audit cadence** | Internal audit (third line) | Are controls operating as documented across the full period? | Audit report with findings and management response |

The three cadences compound. The operating cadence
catches today's drift; the steward cadence catches the
owner who has stopped reviewing; the audit cadence
catches both the owner and the steward if they have
let something slip. Dropping the operating cadence
means failures persist until the steward notices.
Dropping the steward cadence means an owner can go
quiet and no one knows until audit. Dropping the audit
cadence means no outside eye ever confirms the first
two cadences are honest.

The operating cadence is the most frequent (daily,
weekly, or monthly depending on the control). The
steward cadence is intermediate (monthly across the
portfolio). The audit cadence is annual or at the
auditor's choice.

Programs with only an audit cadence — the control
owner does not check their own control until the
auditor asks — discover failures too late to do
anything about them. The problem is not that audit
failed; the problem is that audit was the first
review.

## 3.3 Three evidence-collection patterns

Three patterns recur across working compliance
operations. Most programs use all three; the
discipline is choosing the right pattern per control.

### Pattern 1 — Telemetry-derived evidence

Evidence is **computed** from production telemetry.
Example: the proportion of agent operations subject to
the trust gate ([mod-106](../mod-106-trust-architecture/README.md))
is computed from the trust gate's emission of
`trust-gate.decision` events (see mod-108 Chapter 3's
event-vocabulary pattern). The control owner reviews
the aggregate weekly; the auditor samples specific
weeks.

Telemetry-derived evidence is the strongest of the
three patterns because it is the hardest to fake. The
events are emitted by production systems; the
aggregation is a computation over the events; the
audit path leads back to signed records in the ledger.

The requirement for telemetry-derived evidence to
work: the aggregation pipeline must exist. Raw
telemetry is not evidence; aggregated telemetry with
provenance is. See §3.4 for the specific failure mode
where the pipeline is skipped.

### Pattern 2 — Attested evidence

A **named role attests** that an activity occurred.
Example: a business-unit head attests quarterly that
the AI inventory for their unit is current. A model
owner attests after each release that the release-
review checklist was completed. The attestation
itself is an event in the audit ledger (signed by the
attester).

Attested evidence is cheap to produce but **weak as
standalone evidence**. An attestation is a human
claim; auditors can and will test the claim against
telemetry. Attestation is appropriate for activities
that have no telemetry equivalent (committee
deliberations, policy acknowledgements, judgment
decisions) and inappropriate for activities that do
have telemetry (bias-metric reviews, system-inventory
counts). Programs that over-use attestation to cover
for missing telemetry fail at the first sampling that
compares attestations to the underlying data.

### Pattern 3 — Document-as-evidence

A **document** (policy, minutes, plan, decision memo)
is itself the evidence. Example: AI Risk Council
meeting minutes are evidence that the Council met and
addressed agenda items. A signed risk-acceptance memo
is evidence that a specific risk was accepted by a
specific role on a specific date.

Document-as-evidence is appropriate for governance and
judgment artifacts that are *about* the deliberation,
not about an operational activity. The document must
be signed, dated, retained per mod-108 retention
policy, and findable. Documents that live in a shared
drive without versioning or signatures are not
evidence.

### Choosing between patterns

A rough heuristic:

- **Does the activity leave production telemetry?**
  Prefer Pattern 1 (telemetry-derived). Fall back to
  Pattern 2 only for the parts that telemetry cannot
  cover.
- **Is the activity a deliberation or decision?** Use
  Pattern 3 (document-as-evidence). Supplement with
  Pattern 2 for attendance and attestation.
- **Is the activity a periodic human check against
  telemetry (e.g., quarterly review of a dashboard)?**
  Use Pattern 2 (attested) with the telemetry
  explicitly referenced; the attester attests *to the
  review of the specific telemetry*.

A single control can combine patterns. The inventory-
currency control from Chapter 2 §2.4 uses all three:
telemetry-derived (monthly reconciliation), attested
(quarterly business-unit attestation), document-as-
evidence (the signed catalog version itself).

## 3.4 What goes wrong

Four evidence-collection failure modes to watch for.

- **Telemetry that doesn't aggregate to control
  evidence.** The raw events exist in production
  logging, but no one has built the pipeline that
  turns them into something the control owner can
  review and the auditor can read. The fix is **the
  aggregation pipeline**, not more telemetry. Programs
  that respond to this failure by emitting more raw
  events double down on the mistake.
- **Attestation fatigue.** Owners are asked to attest
  to too many things; attestations become rubber-
  stamp. A business-unit head who signs 40
  attestations each quarter is not reviewing anything;
  they are signing a stack. The fix is
  **consolidation** — fewer, larger attestations with
  substantive review each. Twelve meaningful
  attestations beat forty rubber-stamp ones.
- **Documents not reviewed.** Meeting minutes are
  produced but never reviewed by anyone other than
  the secretary. The next meeting opens with "any
  objections to the minutes?" and no one objects
  because no one read them. The fix is **making
  review part of the next meeting's agenda** — the
  first substantive item, before any new business.
- **Review that produces no artifact.** The reviewer
  reads the evidence but leaves no record that they
  did. The audit cannot distinguish "reviewed and
  approved" from "not reviewed at all". The fix is
  **every review produces an artifact** — a signed
  record, even if the record is one line.

Each failure mode has a specific signature. Diagnose
before you fix.

## 3.5 The cadence calibration question

How often should a control owner review their
control's operating evidence? The right answer varies
by control. A rough calibration:

| Control type | Operating cadence |
|---|---|
| High-stakes, high-frequency (trust-gate decisions, fairness monitoring for a customer-facing system) | Weekly |
| Standing controls (inventory accuracy, policy currency) | Monthly |
| Periodic controls (annual risk-register refresh, biennial training) | Quarterly review of the once-a-year execution |
| One-time controls (initial deployment review, major-release approval) | Per event |

The wrong calibration in either direction is a
problem. **Too-frequent review** produces review-
fatigue and reduces signal — the reviewer stops
noticing anomalies because they are now the texture
of the review. **Too-infrequent review** allows
control failures to persist long enough that the
owner cannot remember what the expected state looked
like.

A rule of thumb: calibrate the operating cadence to be
*shorter than the time between material failures of
the control*. If a control fails once every six
months on average, review it monthly, not quarterly.
If a control has never failed in two years, you can
probably stretch to quarterly review — but the audit
cadence is still watching.

## 3.6 Where evidence lives

Compliance operations rests on the evidence
infrastructure from [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md).
A short recap of the specific hooks this chapter
depends on:

- **The audit ledger.** Every control's evidence lands
  in the same tamper-evident ledger. Programs with
  per-control storage silos cannot assemble evidence
  packages efficiently.
- **The event vocabulary.** The event types the
  control emits are part of the program's event
  vocabulary (mod-108 Chapter 3). New controls
  typically add new event types; the vocabulary
  evolves with the catalog.
- **Retention and sealing.** Each evidence record has
  a retention policy and a sealing timestamp
  (RFC 3161) per mod-108 Chapter 5. The retention
  periods are driven by the obligations the control
  satisfies.
- **Chain of custody.** When evidence is produced for
  an auditor or regulator, chain of custody applies
  per mod-108 Chapter 5. The control owner is one
  link in that chain.

Compliance operations and the evidence layer are not
separate projects. They are two faces of the same
infrastructure.

## 3.7 Operating cadence as a control itself

A subtle but important point: the operating cadence
is itself a control. If the control owner is supposed
to review bias metrics weekly and reviews them twice
in a quarter, the review itself has failed — the
underlying control may or may not have failed, but
the review certainly did.

The practical implication: the **steward cadence**
(§3.2) exists in part to detect operating-cadence
failures. The CAO function's monthly question is not
only "are the controls operating?" but "did every
owner complete their operating review?" An owner who
missed a review is itself a signal.

Programs that treat the review as personal
responsibility rather than an operated control find
that reviews drift. Treating the review as a control
closes the loop.

## Summary

- Continuous evidence collection produces evidence as
  a side effect of control operation, captures it in
  the audit ledger immediately, and makes it
  reviewable on a cadence shorter than the audit.
- Three review cadences compound to detect failure at
  three levels: operating (control owner, today),
  steward (CAO function, across the portfolio), audit
  (internal audit, across the year). Dropping any
  cadence produces a specific failure mode.
- Three evidence-collection patterns — telemetry-
  derived, attested, document-as-evidence. Prefer
  telemetry where it exists; use attestation
  sparingly; use documents for deliberation and
  decisions. Most controls combine patterns.
- Four failure modes: telemetry without aggregation,
  attestation fatigue, documents not reviewed, review
  without artifact. Each has a specific fix.
- Calibrate the operating cadence to be shorter than
  the time between material failures. Too-frequent
  review produces fatigue; too-infrequent review
  allows persistence.
- Compliance operations rests on mod-108 evidence
  infrastructure (ledger, event vocabulary,
  retention, chain of custody) and extends it with the
  cadence discipline.
- The operating cadence is itself a control; the
  steward cadence watches for review drift.
