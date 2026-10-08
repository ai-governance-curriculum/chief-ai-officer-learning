# Exercise 01 — Walk an Incident Through Response

**Estimated time**: 3 hours
**Deliverable**: Phase-by-phase response narrative (≤ 4 pages)

---

## The scenario

You are the CAO at **Northfield Mutual**, a US
life + health insurer with EU-resident policyholder
exposure via a cross-border group-benefits
arrangement. On Tuesday at 09:30 local time, the
demographic-stratified bias monitoring on the
claims-triage v2 system emits a threshold-crossing
alert: a 6.5 percentage-point sensitivity gap on
the age-80+ subgroup at one specific site (Site
H-12), representing the second consecutive month
showing the gap.

Per the escalation thresholds the firm defined
(building on [`mod-107`](../../mod-107-ai-security/README.md)
Ex-04 classification taxonomy), this triggers an
automatic AI Risk Council convene.

## Your assignment

Walk the incident through the four NIST SP 800-61
phases — preparation (what was already in place),
detection and analysis, containment / eradication /
recovery, post-incident activity — plus the
coordination-and-communication thread. For each
phase, describe:

- The decisions made and the deciding role (per
  the single-named-lead convention in Chapter 2
  §2.4.3).
- The actions taken.
- The artifacts produced into the audit ledger
  per [`mod-108`](../../mod-108-audit-ledgers-and-evidence/README.md).
- The notifications considered against the
  matrix (per Chapter 4).
- The time elapsed.

Carry the incident from detection at 09:30 through
notification, containment, investigation, resolution,
and post-incident review.

### Hour 0 (09:30) — Detection (≤ ½ page)

- What detection event fired, through which
  channel (per Chapter 2 §2.1).
- Who received it, and the on-call routing.
- The first response — including whether a false-
  positive investigation was considered (per
  Chapter 2 §2.3).

### Hour 0–1 — First Hour (≤ 1 page)

The four first-hour decisions from Chapter 2 §2.4
in detail. For each:

- **Verification** — confirmed, suspected, or
  likely false positive, with reasoning.
- **Provisional classification** — per
  [`mod-107`](../../mod-107-ai-security/README.md)
  §6 taxonomy; name the sub-category and whether
  the classification is likely to be revised.
- **Single named lead** assignment, with the
  authority basis.
- **Containment posture** chosen (per Chapter 3
  §3.1), including which of the five options and
  the reasoning (per Chapter 3 §3.2).

### Hours 1–24 — Containment, Initial Investigation, and the Hour-24 Revisit (≤ 1 page)

- The containment posture as held and (if
  changed) revised, with the Chapter 3 §3.5
  decision record.
- The investigation team formation (per Chapter
  5 §5.5), initial scope, and initial findings.
- The notification matrix consultation (per
  Chapter 4), with the specific rows considered.
  Which clocks are now running? Which
  notifications have been sent provisionally?
  Which are pending further information?
- The hour-24 revisit (Chapter 2 §2.7 /
  Chapter 4 §4.5.3) in detail.

### Hours 24–168 (one week) — Deep Investigation (≤ ¾ page)

- The deepening investigation.
- Root-cause emergence via the five-whys
  discipline (Chapter 5 §5.2).
- Proximate causes vs. systemic causes (Chapter
  5 §5.3) — name both explicitly.
- Resolution of the incident.

### Days 8–30 — Post-Incident Review (≤ ¾ page)

- The review process per Chapter 6, including
  review lead selection (Chapter 6 §6.1) and the
  participants invited.
- Findings — what worked (Chapter 6 §6.2) and
  what did not.
- Recommendations with the Chapter 6 §6.3
  discipline. Include at least one residual
  acceptance (Chapter 6 §6.4) if warranted.
- Loop closure into the GOVERN backlog
  ([`mod-103`](../../mod-103-ai-risk-frameworks/README.md)
  §6).

## Constraints

- The narrative must be specific — not "the team
  decided" but "AI Risk Lead X decided, at
  10:18, to restrict Site H-12 to elevated
  human-reviewer sampling of age-80+ claims."
- The provisional classification must be made
  within the first hour, in writing, with the
  deciding role recorded.
- At least one notification obligation must be
  triggered (EU AI Act Art. 73 if any
  EU-resident policyholders are in the affected
  cohort; state insurance regulator at
  minimum).
- The investigation must surface a *systemic*
  cause (Chapter 5 §5.3), not just a proximate
  one.
- The post-incident review must produce at
  least three specific recommendations
  structured per Chapter 6 §6.3 — each with
  owner, timeline, and tracking.
- At least one recommendation should route into
  the GOVERN backlog (Chapter 6 §6.5), with a
  specific improvement-item identifier.

## Rubric

| Criterion | Weight |
|---|---|
| Phase coverage — all four NIST phases + coordination | 20% |
| First-hour decisions per Chapter 2 §2.4 | 20% |
| Containment posture defensible per Chapter 3 §3.5 | 15% |
| Notification matrix consulted with specific rows | 15% |
| Systemic cause surfaced per Chapter 5 §5.3 | 15% |
| Post-incident review produces specific, tracked recommendations | 15% |

## Where to submit

`chief-ai-officer-solutions/modules/mod-110-incident-response/exercise-01-walk-incident-through-response/SOLUTION.md`

## Reading before you start

- Chapter 1 (what AI IR is) through Chapter 6
  (post-incident review) of this module.
- [`mod-107`](../../mod-107-ai-security/README.md)
  §6 + Ex-04 (classification taxonomy).
- [`mod-105`](../../mod-105-responsible-ai-and-ethics/README.md)
  Ex-02 (bias metric specification) — grounds
  what the monitoring alert actually represents.
- [`mod-103`](../../mod-103-ai-risk-frameworks/README.md)
  Ex-04 (treatment plan with residual
  discipline) — for the shape of the systemic-
  cause recommendations.
