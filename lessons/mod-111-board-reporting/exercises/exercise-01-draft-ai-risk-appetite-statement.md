# Exercise 01 — Draft an AI Risk Appetite Statement

**Estimated time**: 3 hours
**Deliverable**: AI risk appetite statement (≤ 3 pages)

---

## The scenario

You are the CAO at **Halverston Capital**, a
$40B wealth-management and asset-management
firm with US SEC and FINRA oversight, EU
operations under MiFID II and the EU AI Act,
and a growing book of AI-mediated client-
facing capabilities (wealth-advisory chat,
onboarding fraud screening, portfolio
construction co-pilots, operational
automation).

The Board Risk Committee has asked you to
draft an AI risk appetite statement for
adoption at the next quarterly meeting. The
statement will be the foundation document
for Halverston's AI program — every other
governance artifact derives from it. The
Audit Committee chair has indicated she
expects the full board to adopt the statement
within two cycles.

## Your assignment

Produce a draft AI risk appetite statement
with the structure from
[Chapter 2 §2.3](../02-ai-risk-appetite-statement.md#23-the-structure-that-works):

### Section 1 — Preamble (≤ ¼ page)

- What AI risk means at Halverston.
- What this statement does (and does not do),
  per Chapter 2 §2.2.
- The relationship to Halverston's enterprise
  risk appetite statement (which already
  exists for non-AI risks).

### Section 2 — Risk categories (≤ ¼ page)

Drawn from Halverston's AI risk taxonomy
(building on
[`mod-103`](../../mod-103-ai-risk-frameworks/README.md)
Exercise 01). Brief listing of the eight
top-level categories.

### Section 3 — Per-category appetite (≤ 1¾ pages)

For each of Halverston's eight top-level
categories (model performance, bias and
fairness, transparency and explainability,
privacy and data, security, vendor and
third-party AI, market and conduct, strategic
and reputational), express the appetite using
the Chapter 2 §2.4 patterns — risk-class
framing, boundary language, and threshold
language.

Each category gets one paragraph plus one
boundary or threshold expression.

### Section 4 — Escalation process (≤ ¼ page)

What happens when a case approaches or
exceeds the boundaries. Integrates with the
[`mod-107`](../../mod-107-ai-security/README.md)
§6 classification taxonomy and the
[`mod-110`](../../mod-110-incident-response/README.md)
response flow.

### Section 5 — Review cadence (≤ ¼ page)

When the board reconsiders the statement
(annual plus material-trigger, per Chapter 2
§2.3.5).

## Constraints

- The statement must be **board-readable**.
  A board member without specialised AI
  knowledge should be able to read and act on
  it.
- Each category's appetite expression must
  combine **at least two** of the Chapter 2
  §2.4 patterns (risk-class + boundary, or
  risk-class + threshold, or boundary +
  threshold).
- At least three categories must include
  **specific quantitative thresholds**
  (percentage points, dollar amounts, count
  thresholds, time-window thresholds).
- The bias-and-fairness category must
  acknowledge the
  [`mod-105`](../../mod-105-responsible-ai-and-ethics/README.md)
  §3.2 impossibility result per Chapter 2
  §2.5.1 — naming which fairness conception
  takes priority at Halverston and which
  others are explicitly not enforced.
- The vendor-and-third-party category must
  include a concentration threshold (what
  percentage of AI capability dependent on a
  single vendor is outside appetite).
- The escalation process in Section 4 must
  explicitly tie to the mod-110 incident
  classification — cases approaching
  boundaries enter the incident flow.
- The statement must survive the Chapter 2
  §2.7 adoption dynamics — anticipate the
  "why so much on bias," "quantify
  everything," and "aren't we just making
  this up" questions.

## Rubric

| Criterion | Weight |
|---|---|
| Structure — five sections per Chapter 2 §2.3 | 10% |
| Board-readable language | 20% |
| Per-category appetite with two patterns combined | 25% |
| Quantitative thresholds where appropriate | 15% |
| Bias category acknowledges impossibility result | 10% |
| Vendor concentration threshold specified | 5% |
| Escalation integrates with mod-110 flow | 10% |
| Length discipline — ≤ 3 pages | 5% |

## Where to submit

`chief-ai-officer-solutions/modules/mod-111-board-reporting/exercise-01-draft-ai-risk-appetite-statement/SOLUTION.md`

Reference solution adopts equalised odds as
Halverston's primary fairness conception with
explicit acknowledgment that other
conceptions (predictive parity, demographic
parity) are not simultaneously enforced, and
sets vendor LLM concentration appetite at
50% of client-facing AI capability (crossing
triggers Board Risk Committee notification).

## Reading before you start

- Chapter 1 (what boards actually need).
- Chapter 2 (the AI risk appetite statement)
  — all sections.
- [`mod-103`](../../mod-103-ai-risk-frameworks/README.md)
  Exercise 01 (taxonomy).
- [`mod-105`](../../mod-105-responsible-ai-and-ethics/README.md)
  §3.2 (impossibility result).
- [COSO ERM — Applying ERM to AI](https://www.coso.org/)
  — at minimum the appetite section.
- [NIST AI RMF 1.0, GOVERN function](https://www.nist.gov/itl/ai-risk-management-framework)
  — GV-1 through GV-3 subcategories.
