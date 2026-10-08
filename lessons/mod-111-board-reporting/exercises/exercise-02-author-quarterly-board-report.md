# Exercise 02 — Author a Quarterly Board Report

**Estimated time**: 3 hours
**Deliverable**: Quarterly board report (3–5 pages main cover + portfolio ROI appendix)

---

## The scenario

You are the CAO at **Northfield Mutual**, a
US life + health insurer with EU-resident
policyholder exposure via a cross-border
group-benefits arrangement. The Q2 Board
Risk Committee meeting is in two weeks. You
need to author the quarterly AI report.

The quarter included:

- The **Site H-12 bias incident** (the age-
  80+ sensitivity gap on claims-triage v2
  from
  [`mod-110`](../../mod-110-incident-response/README.md)
  Exercise 01).
- A state insurance regulator inquiry
  resulting from the incident.
- The EU AI Act National Competent Authority
  notification under Art. 73.
- Three program-improvement milestones (new
  training-data refresh review gate; improved
  monitoring sensitivity; formalised patient-
  notification authority).
- The acceptance of one specific residual
  risk (the age-80+ cohort below the pre-
  incident performance baseline for one
  additional quarter while the training-data
  refresh completes).
- An ask for board ratification on an updated
  bias-monitoring threshold (5 pp → 4 pp
  for Tier-1 systems).
- A vendor LLM swap in the fraud-screening
  capability — upstream model version
  change, discovered rather than
  pre-notified.
- Portfolio-level: AI operating spend up
  12% YoY driven by inference compute;
  realised value from fraud screening and
  claims-triage AI capability now exceeds
  governance-plus-operating cost for the
  first time.

## Your assignment

Produce a quarterly board report following
the structure from
[Chapter 3 §3.1](../03-quarterly-board-reporting.md#31-the-structure-that-works).
Use the H-12 incident context throughout to
ground the report, and include a Chapter 7
portfolio ROI appendix.

### Section 1 — Risk posture summary (≤ ½ page)

Aggregate view of the program by risk
appetite category (from the Exercise 01
appetite statement framing), with
change-from-last-quarter indicators per
Chapter 3 §3.1.1 (within / approaching /
outside appetite × improving / stable /
worsening).

### Section 2 — Material changes (≤ ½ page)

What has changed in the trailing quarter the
board should know. Material program
decisions, closed incidents, organisational
movement.

### Section 3 — Material exceptions (≤ 1 page)

Cases outside risk appetite, with response
and timeline, per Chapter 3 §3.1.3. The
H-12 incident's bias-monitoring threshold
crossing is one. The regulator inquiry is
material-change rather than exception;
confirm your classification.

### Section 4 — Material decisions pending (≤ ½ page)

What the board needs to decide.

### Section 5 — Material changes ahead (≤ ½ page)

What's foreseeable (regulatory, market,
organisational).

### Section 6 — Asks (≤ ½ page)

Specific asks per Chapter 3 §3.2. At least
one is required. The bias-monitoring
threshold update is the natural ask;
identify at least one other.

### Appendix A — Portfolio ROI (≤ 1 page)

Per Chapter 7, a portfolio-level view with:

- Portfolio summary (spend, gross returns,
  risk-adjusted returns, direction).
- Top three capabilities by investment.
- Top three capabilities by return.
- Material concentration risks called out
  specifically (vendor LLM concentration
  after the swap; the single-model
  concentration in claims-triage).
- Explicit methodology note — attribution
  pattern used; risk-adjustment pattern used.

### Appendix B — Incident register (any length)

Reference material; summarise in §2 or §3 if
material.

## Constraints

- The main report cover is **3–5 pages**.
  Appendices do not count toward this limit
  but are explicitly labelled as reference.
- Per Chapter 3 §3.3, the report must be
  **honest** about the H-12 incident. No
  euphemism, no burying, no softening of the
  ask.
- Per Chapter 3 §3.2, at least two specific
  asks (one being the bias-monitoring
  threshold update).
- The report must avoid the Chapter 1 §1.3
  anti-patterns — no operational metrics in
  detail, no technology details, no
  educational content.
- The risk posture summary (§1) must use the
  appetite categories from the Exercise 01
  appetite statement.
- The portfolio appendix must disclose the
  risk-adjustment pattern used (per Chapter
  7 §7.5) and reconcile to the CFO's
  financial record (methodology note).
- The vendor LLM swap must be addressed —
  which section it belongs in is a
  classification call you make and defend.

## Rubric

| Criterion | Weight |
|---|---|
| All six main sections present | 10% |
| Risk posture uses appetite categories | 10% |
| H-12 incident honestly addressed | 25% |
| At least two material asks, specific | 15% |
| Chapter 1 §1.3 anti-patterns avoided | 10% |
| Portfolio ROI appendix per Chapter 7 | 15% |
| Vendor LLM swap classified and addressed | 10% |
| Length discipline — 3-5 pages main cover | 5% |

## Where to submit

`chief-ai-officer-solutions/modules/mod-111-board-reporting/exercise-02-author-quarterly-board-report/SOLUTION.md`

Reference solution presents the H-12
incident as the central exception, the
regulator inquiry as material change, the
bias-monitoring threshold update as the
primary ask, and the vendor LLM swap as a
material exception against the vendor
appetite (discovered rather than
pre-notified crosses the appetite boundary
on process even where the swap itself may be
functionally acceptable). Portfolio appendix
reports risk-adjusted ROI using the
realised-incident attribution pattern.

## Reading before you start

- Chapter 1 (what boards need) and Chapter 3
  (quarterly reporting).
- Chapter 7 (portfolio P&L and ROI) for the
  appendix.
- [`mod-110`](../../mod-110-incident-response/README.md)
  Exercise 01 reference (the H-12 incident
  context).
- [`mod-105`](../../mod-105-responsible-ai-and-ethics/README.md)
  Exercise 04 (contestability process —
  informs program improvements).
- [`mod-107`](../../mod-107-ai-security/README.md)
  Exercise 04 (incident classification
  taxonomy).
