# Exercise 03 — Design a Materiality Threshold Framework

**Estimated time**: 3 hours
**Deliverable**: Materiality framework + decision examples (≤ 3 pages)

---

## The scenario

You are the CAO at **Tessera Bank**, a $25B
US regional bank with primary supervision by
the OCC, consumer-protection supervision by
the CFPB, state-level cybersecurity oversight
under NYDFS Part 500 for its NY-chartered
subsidiary, and model-risk oversight under
SR 11-7.

The Audit Committee has asked for an explicit
materiality framework so the boundary between
board-level matters and CAO-function-level
matters is consistent across the program. The
CCO has agreed (building on the
[`mod-109`](../../mod-109-compliance-operations/README.md)
Exercise 05 split-authorship resolution) that
AI-specific materiality is authored by the
CAO function.

## Your assignment

Produce a materiality framework following
[Chapter 4](../04-materiality-framework.md):

### Section 1 — Definition and approach (≤ ¼ page)

- What materiality means for Tessera AI
  matters (Chapter 4 §4.1).
- The relationship to Tessera's enterprise
  materiality framework for non-AI matters.
- The principle that the framework
  structures judgment, not replaces it.

### Section 2 — The dimensions (≤ ¼ page)

The five Chapter 4 §4.2 dimensions
(financial, regulatory, reputational,
operational, strategic), with Tessera-
specific adaptations.

### Section 3 — Calibrated thresholds (≤ 1¼ pages)

For each dimension, the thresholds calibrated
to Tessera's $25B scale per Chapter 4 §4.3.

| Dimension | Threshold | Examples |
|---|---|---|
| Financial | ≥ $5M or ≥ 0.5% of revenue | $5M+ remediation; $10M fine |
| Regulatory | Any regulator-initiated action; EU AI Act Art. 73; SR 11-7 material model event; CFPB inquiry; SEC 8-K-triggering AI cyber event | OCC MRA; CFPB CID; NCA inquiry |
| Reputational | Public exposure or substantiated potential; ≥ 1,000 customers visible | Media coverage; customer-visible adverse-action failure |
| Operational | > 4-hour AI system outage; cross-LOB impact; RTO breach | Trust gate outage; LLM vendor outage |
| Strategic | Material change in AI direction; vendor concentration crossing diversification floor | Entering new use case; major vendor swap |

### Section 4 — Decision examples (≤ ¾ page)

Apply the framework to specific scenarios:

- **Scenario A — Site H-12 bias incident
  pattern at Tessera.** A sensitivity gap
  above the appetite threshold sustained over
  two monitoring cycles. Material? Along
  which dimensions? Reasoning.
- **Scenario B — Trust-gate outage of 2
  hours affecting one LOB (commercial
  lending).** Material?
- **Scenario C — Vendor LLM swap discovered
  rather than pre-notified.** Vendor
  changed the model version with contractual
  notice but the notice reached Tessera via
  the Model Risk team rather than the
  procurement channel. Material?
- **Scenario D — One customer complaint
  about an AI-driven adverse-action notice
  that did not contain the specific reasons
  required by Reg B §1002.9.** Material?
- **Scenario E — A 6pp sensitivity gap in
  monitoring for one weekly cycle (single
  data point, no established trend).**
  Material?

For each, name the materiality decision and
the reasoning. At least one must be a
**boundary case** requiring §4.5 escalation.

### Section 5 — Boundary-case escalation (≤ ¼ page)

Tessera-specific version of the Chapter 4
§4.5 escalation — CRO within 5 business days,
Board Risk Committee chair within 10
business days if unresolved, disposition
recorded in the
[`mod-108`](../../mod-108-audit-ledgers-and-evidence/README.md)
audit ledger.

### Section 6 — Calibration cadence (≤ ¼ page)

When and how the thresholds are
recalibrated per Chapter 4 §4.6.

## Constraints

- Thresholds must be **calibrated to
  Tessera's $25B scale** — not generic.
- At least three thresholds must be
  **quantitative**.
- The decision examples must address all
  five scenarios with explicit reasoning.
- At least one scenario must be a **boundary
  case** requiring §4.5 escalation rather
  than a clear material/non-material call.
- The framework must address at least two of
  the Chapter 4 §4.8 anti-patterns
  explicitly (threshold creep, boundary-
  case-as-default, materiality-by-
  consensus) — how Tessera's framework
  avoids them.
- The regulatory dimension must specify
  which regimes Tessera is in-scope for and
  how the AI-specific framework coexists
  with the statutory floors in Chapter 4
  §4.7 (SEC 8-K, EU AI Act Art. 73, SR 11-7,
  NYDFS Part 500 §500.17, GDPR Arts. 33-34
  as applicable).

## Rubric

| Criterion | Weight |
|---|---|
| Definition and approach | 10% |
| Dimensions adapted for Tessera | 10% |
| Thresholds calibrated to $25B scale | 20% |
| Decision examples — five with reasoning | 25% |
| At least one boundary case escalation | 10% |
| Anti-patterns addressed | 10% |
| Regulatory statutory floors addressed | 10% |
| Length discipline — ≤ 3 pages | 5% |

## Where to submit

`chief-ai-officer-solutions/modules/mod-111-board-reporting/exercise-03-design-materiality-framework/SOLUTION.md`

Reference solution treats Scenario D (one
customer complaint on Reg B §1002.9
specificity) as the boundary case —
depending on whether the complaint pattern
is isolated or structural, it may or may not
be material; the §4.5 escalation discipline
is applied.

## Reading before you start

- Chapter 4 (materiality framework), all
  sections.
- Chapter 1 (what boards need) for the
  distinction between oversight-altitude and
  management-altitude matter.
- [`mod-107`](../../mod-107-ai-security/README.md)
  Exercise 04 (classification taxonomy —
  related context).
- [SEC 2023 cybersecurity disclosure final rule](https://www.sec.gov/)
  for the Form 8-K materiality baseline.
- [EU AI Act Art. 73](https://artificialintelligenceact.eu/)
  for the serious-incident notification
  posture.
