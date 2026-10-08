# Chapter 4 — The Materiality Framework

## Why this chapter exists

The hardest practical question in board
reporting is *does this matter to the board?*
Programs without a materiality framework
either flood the board with non-material items
(the Chapter 1 over-reporting failure mode) or
quietly keep material items at the operational
level and are later asked why. Both failures
end badly; the second ends worse.

A working materiality framework is the
decision aid that structures the judgment.
It does not replace the judgment — materiality
is inherently a judgment call — but it makes
the judgment defensible, consistent across
cases, and reviewable by the board itself.

This chapter builds a framework in the shape
of the dimensions-plus-thresholds pattern that
is standard across risk disciplines (COSO ERM,
sector supervisory expectations, classical
financial-accounting materiality) adapted to
AI matters, plus the boundary-case escalation
discipline that handles the matters where the
framework alone does not resolve the call.

## 4.1 What materiality means

Materiality is the threshold at which
something is *important enough* to require
board attention. The classical materiality
test, from financial accounting: something is
material if a reasonable user of the
information would make a different decision if
they knew it. Applied to AI board reporting:

> *An AI matter is material if the board would
> form a different view of the program's risk
> posture, or take different oversight action,
> if it knew.*

The definition is operational, not formal. A
matter can be material along one or more
dimensions (§4.2) and non-material along
others; the aggregate call is a judgment the
framework structures but does not make.

Two properties of a working materiality
framework:

- **Defensible.** When a specific matter is
  judged non-material and later proves to have
  been material, the framework and the
  evidence against which it was applied are
  the defense. "Our materiality framework
  specified X; the matter did not reach X;
  here is the written assessment" is a
  position that survives external review.
  "We just didn't think it was material" is
  not.
- **Consistent.** The framework produces
  comparable calls across cases over time.
  Different CAOs under different pressures
  reach the same calls on the same facts.
  Consistency protects against drift, which
  is where materiality calls go wrong most
  often — not in the obvious cases but in the
  slow erosion of thresholds under cumulative
  small pressures.

## 4.2 The materiality dimensions

For AI matters, materiality has five
dimensions. A matter that crosses any of these
dimensions at sufficient magnitude is
material; a matter below threshold on all
five is non-material.

### 4.2.1 Financial

Would this affect the organisation's financial
results materially? Includes:

- Direct remediation cost (customer
  compensation, legal fees, settlement
  reserves).
- Regulatory fines and sanctions.
- Lost revenue from capability pauses or
  rollbacks.
- Opportunity cost of leadership attention
  (not usually quantified but material in
  concentration).

For public companies, SEC materiality standards
apply alongside the AI-specific framework; the
AI framework should be at least as strict as
the SEC baseline.

### 4.2.2 Regulatory

Would this trigger regulatory action, fines,
or enforcement? Includes:

- Regulator-initiated inquiries, examinations,
  or enforcement actions.
- Notifications required by regime (EU AI Act
  Art. 73, GDPR Arts. 33–34, NYDFS Part 500
  §500.17, SR 11-7 model events, sector
  regimes).
- Supervisory expectations expressed informally
  but with enforcement implications (OCC MRA
  / MRIA pathways, FRB SR letters).

The regulatory dimension often *drives*
materiality on its own — any regulator-
initiated action is typically material
regardless of other dimensions.

### 4.2.3 Reputational

Would this affect the organisation's public
reputation if it surfaced? Includes:

- Public exposure (media coverage, social
  surfacing, regulator public announcement).
- Potential public exposure (facts that would
  attract coverage if surfaced).
- Customer-visible failure (an AI system
  producing visibly wrong outcomes to a
  non-trivial customer base).

Reputational materiality is the hardest to
threshold because the external response is
inherently unpredictable. The framework names
*kinds* of reputational exposure (per
Chapter 2 §2.5.2) rather than numeric
thresholds.

### 4.2.4 Operational

Would this affect core operations? Includes:

- Multi-system outage affecting cross-LOB
  delivery.
- Customer-affecting incident of duration
  exceeding the business continuity threshold
  for the system class.
- Degradation of fallback capacity — the
  organisation's ability to operate without
  the AI tier is reduced below the
  continuity-planning floor.

Operational materiality often requires the
Business Continuity function's input to
calibrate the thresholds that already exist
for non-AI operations.

### 4.2.5 Strategic

Would this affect the organisation's
strategic direction or long-term posture?
Includes:

- Decision to enter or exit a major AI
  capability class.
- Material vendor change (concentration,
  dependency, upstream model change).
- Material organisational change (acquisition,
  divestiture, restructuring) that
  materially affects the AI program's
  footprint.
- Material capability-tier change — the
  program is now operating or planning to
  operate at a capability level that crosses
  a frontier-safety boundary (Chapter 2
  §2.5.4).

## 4.3 The threshold framework

For each dimension, the framework specifies a
threshold above which matters are considered
material. The thresholds are *calibrated to
the organisation's size and context* — what
is material at a $1B firm differs from what
is material at a $100B firm, and the
framework must reflect that calibration.

A pattern thresholding table — not an answer:

| Dimension | Threshold pattern | Example triggers |
|---|---|---|
| Financial | Greater of (fixed $ threshold) or (% of annual revenue) | $5M customer remediation; $10M regulatory fine; 0.5% of revenue impact |
| Regulatory | *Any* regulator-initiated action; EU AI Act Art. 73 notification; SR 11-7 material model event; SEC cybersecurity 8-K | OCC examination finding; CFPB inquiry; EU AI Act competent authority inquiry |
| Reputational | Public exposure or substantiated potential; media coverage; customer-visible AI failure affecting > N customers | Media coverage of an AI incident; customer-visible decisioning failure |
| Operational | Multi-system outage; customer-affecting incident exceeding RTO for system class; cross-LOB impact | Trust gate outage; LLM vendor outage; multi-system fallback invocation |
| Strategic | Material change in AI program direction; concentration crossing diversification floor; capability-tier change | Entering a new AI use-case class; major vendor change; capability frontier crossing |

The thresholds are calibrated to the specific
organisation at the time the framework is
adopted. The calibration is not permanent
— §4.6 treats the review cadence.

## 4.4 The materiality decision

For each potential matter, the CAO function
applies the framework and reaches one of three
outcomes:

### 4.4.1 Clearly material

The matter crosses threshold on at least one
dimension unambiguously. Routing: the matter
reaches the board pack for the next regular
meeting; if the matter is in-flight or has
regulatory timing implications, off-cycle
briefing (Chapter 3 §3.5) applies.

Examples of clearly material matters:

- A regulator-initiated AI inquiry of any
  kind (regulatory dimension).
- An AI incident producing customer-visible
  harm with media exposure (reputational +
  operational).
- A vendor LLM concentration that crosses the
  vendor appetite threshold on acquisition
  of the primary vendor (strategic + vendor
  appetite).
- A material model event under SR 11-7 at a
  bank subject to SR 11-7 (regulatory).

### 4.4.2 Clearly non-material

The matter is below threshold on all five
dimensions. Routing: operates internally to
the CAO function; appears in appendices or
AIRC-level reporting if relevant; does not
reach the board pack.

Examples of clearly non-material matters:

- A single-cycle monitoring threshold crossing
  that reverts in the next cycle with no
  customer impact.
- A vendor change below concentration
  threshold with equivalent governance
  posture.
- A routine model retraining producing a
  within-expected performance adjustment.
- An operational AI-system incident contained
  within hours with no customer-visible
  impact.

### 4.4.3 Boundary case

The matter is close to threshold on one or more
dimensions and the materiality call is
genuinely uncertain. Routing: §4.5 escalation.

The boundary case is the discipline that
protects against both failure modes. Pretending
material items are not is the failure mode
that produces post-hoc board embarrassment;
flooding the board with every uncertain item
is the failure mode that erodes the board's
attention. The boundary-case consultation
prevents both without requiring the CAO to
guess alone.

## 4.5 The boundary-case escalation

A working boundary-case escalation operates
on a defined timeline:

### 4.5.1 Recognise

The CAO function recognises a matter as a
boundary case — not clearly material, not
clearly non-material. The recognition itself
is captured in writing in the audit ledger
([`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)):
the matter, the facts known at the time, the
dimensions where it is close to threshold,
the time of recognition.

### 4.5.2 Brief CRO (within 5 business days)

The CRO is briefed on the boundary case. The
CRO's role: a second-opinion check on the
materiality call from someone with enterprise
risk authority who is not inside the CAO
function. The CRO may:

- Agree it is non-material; the matter stays
  below the board line.
- Agree it is material; the matter proceeds
  to §4.5.4.
- Call the case still-boundary; the matter
  proceeds to §4.5.3.

### 4.5.3 Brief Board Risk Committee chair (within 10 business days)

If the CRO cannot resolve the call, the Board
Risk Committee chair is briefed. The chair
decides disposition:

- Include in the next regular board pack as
  non-material-but-noted (board awareness
  without materiality classification).
- Include in the next regular board pack as
  material.
- Escalate off-cycle to the full committee
  or board.
- Stand down with written chair concurrence.

### 4.5.4 Record the disposition

The disposition is captured in the audit
ledger. The record is dated, named, and
specific. If the matter later proves to have
been material, the boundary-case audit trail
is the defense: a reasonable escalation
discipline was applied; a specific
disposition was reached in writing; the
disposition was concurred in by the CRO
and/or the Board Risk Committee chair at
the time.

## 4.6 Calibration cadence

Thresholds drift. What was material at a $5B
firm is not material at a $25B firm; what was
material before the EU AI Act is operationally
different now; what was material before the
program had operational monitoring at scale
is different once it does. The framework
needs a defined review cadence:

- **Annual review.** As part of the appetite
  statement review (Chapter 2 §2.3.5). The
  CRO and CAO co-recommend; the Board Risk
  Committee ratifies.
- **Material-trigger review.** A material
  change in the organisation's scale, in the
  regulatory environment, or in the AI
  program's own scope triggers an off-cycle
  recalibration.

A test for whether the framework is being
calibrated honestly: is the frequency of
boundary cases roughly stable over time? A
framework whose boundary-case volume is
climbing suggests the thresholds are no longer
calibrated to current reality; a framework
whose boundary-case volume is near zero
suggests the thresholds have been loosened
enough that nothing is close to the line, which
usually means material items are being
classified below the line.

## 4.7 Materiality and the regulators

Several regulatory regimes have their own
materiality definitions that layer on top of
the AI-specific framework:

- **SEC 2023 cybersecurity disclosure rule.**
  Material cybersecurity incidents require
  Form 8-K disclosure within 4 business days
  of the materiality determination. The
  AI-specific framework must be at least as
  strict as the SEC baseline for AI matters
  with cybersecurity implications.
- **EU AI Act Art. 73.** Serious incidents
  must be notified to the national competent
  authority within 15 days (10 for widespread
  infringement; 2 for death/serious bodily
  harm). The AI-specific materiality
  framework identifies which matters warrant
  the Art. 73 clock being started.
- **SR 11-7 (OCC/FRB).** Material model
  events require escalation to senior
  management and documentation in the model
  inventory. The AI-specific framework
  aligns with the SR 11-7 materiality
  posture for in-scope models.
- **NYDFS Part 500 §500.17.** Material
  cybersecurity events require notification
  to the superintendent within 72 hours. AI
  matters with cybersecurity implications
  flow into this clock.
- **GDPR Arts. 33–34.** Personal-data
  breaches require notification to the
  supervisory authority within 72 hours of
  awareness. AI matters involving personal
  data flow into this clock.

The AI-specific framework does **not**
override the regulatory thresholds; it adds
AI dimensions on top. A matter can be
regulatorily non-material and AI-material;
it can be regulatorily material and
AI-non-material (unusual, but it happens
when a classical cyber incident touches an
AI system without AI being the operative
dimension); it can be both.

## 4.8 The anti-patterns

Three patterns to recognise and avoid:

### 4.8.1 Threshold creep

The thresholds are quietly raised as the
organisation grows or as uncomfortable items
approach them. The pattern is detectable from
the audit ledger: thresholds in the current
framework are measurably higher than
thresholds a year ago, without a documented
calibration decision backing the change.
Threshold creep is how programs end up with
materiality floors so high that nothing ever
reaches the board.

### 4.8.2 Boundary case as default

Every ambiguous matter is classified as a
boundary case to defer the materiality
decision. The pattern is detectable from the
audit ledger: boundary cases are routinely
disposed of as non-material after the CRO or
chair review, suggesting the initial
classification was defensive rather than
substantive. Boundary-case-as-default is how
programs end up with the CRO and chair
functioning as the materiality decision-maker
rather than the CAO.

### 4.8.3 Materiality by consensus

The materiality decision is reached by
collective agreement among the CAO function,
the AIRC, and peer executives rather than by
the CAO's judgment against the framework. The
pattern looks collaborative but produces a
decision no one owns; when the decision is
later tested, the deciding authority is
diffused. Materiality decisions are owned by
the CAO; peer executives are consulted on
boundary cases per §4.5 but do not
collectively replace the CAO's judgment on
non-boundary cases.

## Summary

- Materiality is a judgment, structured by a
  framework but not replaced by it. A matter
  is material if the board would form a
  different view or take different action if
  it knew.
- Five dimensions: financial, regulatory,
  reputational, operational, strategic. A
  matter crossing any dimension at magnitude
  is material.
- Thresholds are calibrated to the specific
  organisation. Quantitative where possible;
  categorical for reputational and strategic
  dimensions.
- Three outcomes: clearly material (goes to
  board), clearly non-material (stays below
  the board line), boundary case (§4.5
  escalation).
- Boundary-case escalation: CAO recognises in
  writing; CRO briefed within 5 business
  days; Board Risk Committee chair briefed
  within 10 business days if unresolved;
  disposition recorded in the audit ledger.
- Calibration is annual plus material-
  trigger. Threshold creep, boundary-case-
  as-default, and materiality-by-consensus
  are the anti-patterns to watch for.
- Regulatory materiality regimes (SEC 8-K,
  EU AI Act Art. 73, SR 11-7, NYDFS Part 500
  §500.17, GDPR Arts. 33–34) layer on top of
  the AI-specific framework and set
  statutory floors.
