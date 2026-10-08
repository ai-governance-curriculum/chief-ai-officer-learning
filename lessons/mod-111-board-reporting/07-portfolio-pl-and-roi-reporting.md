# Chapter 7 — Portfolio P&L Attribution and ROI Reporting

## Why this chapter exists

Risk reporting without value reporting
produces a board that — correctly — asks what
the program is for. A board that sees six
chapters' worth of appetite, materiality,
exceptions, incidents, and self-assessment,
without seeing a parallel view of what the AI
portfolio is producing in business value, is
seeing half the picture. The CFO is reading
the same quarterly pack and asking the same
question from a different angle: *what is this
costing us, and what is it returning?*

The CAO function does not own the business
case for individual AI investments — product
and line-of-business ownership stays with the
product and LOB leaders. But the CAO does own
the **portfolio view** that consolidates AI
investment, attributes P&L impact across the
AI portfolio, and reports ROI in a form the
Audit Committee, the Board Risk Committee,
and the CFO can act on in parallel to the
risk view.

This chapter builds the consolidation
discipline, the attribution framework, and
the ROI reporting pattern that completes the
board's view of the AI program as a *going
concern* — not just a risk surface, but a
value engine with risk that must be managed.

## 7.1 Why the CAO owns the portfolio view

Four reasons the portfolio consolidation sits
with the CAO function rather than with the
CFO or with individual LOB leaders:

- **AI-specific accounting treatments.** AI
  investment has specific accounting
  characteristics — model development may be
  capitalisable or expensed depending on
  jurisdiction and intended use; training-
  compute costs have specific attribution
  patterns; vendor LLM spend is operationally
  recurring rather than depreciable in most
  structures. The CFO function can carry
  these; the CAO function is the one with the
  substantive view of which costs attach to
  which capabilities.
- **Cross-LOB consolidation.** AI
  investments made by individual LOBs may be
  double-counted or missed if consolidated
  by LOB leaders individually. The CAO
  function is positioned to see the full
  portfolio and reconcile the LOB-level views.
- **Risk-adjustment context.** The portfolio
  view the board needs is risk-adjusted —
  returns are reported against the risk posture
  the rest of the module reports. The CAO
  function is the one with the risk view;
  the CFO function is the one with the
  financial view; the integration lives
  natively in the CAO's reporting lane.
- **Vendor and infrastructure
  concentration.** Portfolio-level
  concentration risk — percentage of AI
  value derived from a single vendor LLM, a
  single training-infrastructure provider, a
  single internal model — is a view only the
  CAO sees in full. The CFO sees spend
  concentration; the CAO sees value and
  dependency concentration.

The division of labour: the CFO function owns
the authoritative financial record (the
general ledger, the capital allocation, the
budget cycle). The CAO function owns the
*portfolio consolidation and attribution* on
top of that record — the view that
reconciles to the CFO's books but presents AI
investment and return in the shape the board
and the AIRC need.

## 7.2 The portfolio inventory

The foundation of the portfolio view is a
living inventory of AI investments. The
inventory draws from the model inventory
([`mod-104`](../mod-104-model-risk-management/README.md)
§5) and the vendor register
([`mod-109`](../mod-109-compliance-operations/README.md))
but expands them to carry the value and cost
dimensions those inventories do not.

For each AI investment in the portfolio, the
inventory records:

- **Identifier.** The AI capability, model, or
  system identifier that matches the model
  inventory and the audit ledger.
- **Owning LOB or function.** The business
  unit accountable for value delivery.
- **Investment classification.** Build vs.
  buy vs. hybrid; capitalised vs. expensed
  under the firm's accounting policy.
- **Lifecycle stage.** Pre-production,
  production, retired. (This matters for ROI
  attribution — pre-production spend is cost
  without current return, not an operational
  loss.)
- **Risk tier.** From the mod-104 tiering
  (Tier 1 / 2 / 3). The risk tier shapes the
  risk-adjustment applied to the ROI (§7.5).
- **Vendor concentration.** If vendor-
  dependent: the primary vendor and the
  substitutability posture.
- **Dependency map.** Downstream systems that
  depend on this capability.

The inventory is updated continuously; the
quarterly pack and the annual self-assessment
draw from the current state. The inventory
itself is an appendix; the board does not read
it line-by-line but may consult it.

## 7.3 The cost attribution

AI costs attach to specific capabilities
through four categories:

### 7.3.1 Direct build costs

Development spend — internal engineering,
data-science, ML-ops time at loaded cost; the
training-compute and training-data costs; the
tooling and infrastructure specifically
provisioned for the capability. These are
usually capitalisable under the firm's
accounting policy if the capability is for
internal use and reaches the firm's defined
threshold; expensed otherwise.

### 7.3.2 Direct run costs

Operating spend — inference compute, inference
data access, vendor API costs (per-token,
per-request, or subscription), vendor
licensing, model refresh and retraining
costs, model monitoring and observability
costs. These are generally expensed.

### 7.3.3 Governance and risk-management
       overhead

The CAO function cost — risk management,
compliance, independent validation, audit
support, incident response proportion
attributable to AI. This is the *second-line
cost* ([`mod-101`](../mod-101-foundations/README.md)
§3) of operating the program; it is a real
cost of the AI portfolio and must be
attributed to the portfolio to produce an
honest ROI view.

Attribution patterns:

- Fully-attributed: the CAO function cost is
  entirely absorbed by the AI portfolio.
  Most straightforward; most honest.
- Per-capability: the function cost is
  attributed to capabilities proportionally
  to risk tier or governance intensity.
  More accurate per-capability but requires
  defensible allocation keys.
- Hybrid: direct AI-specific CAO function
  spend is attributed per-capability;
  general governance overhead is portfolio-
  level.

The pattern used must be disclosed in the
reporting; otherwise cross-period comparisons
become unreliable.

### 7.3.4 Risk and incident costs

Realised cost of AI incidents in the period —
customer remediation, legal fees, regulatory
fines, settlement reserves, lost revenue
during capability pauses. Also: insurance
premiums specifically allocated to AI risk.

This category is where risk-adjusted ROI
differs most materially from gross ROI. A
capability with high gross returns but a
history of realised incident costs has a
different risk-adjusted picture than a
capability with the same gross returns and
no incidents.

## 7.4 The value attribution

The harder half. AI value attaches to
capabilities through four patterns:

### 7.4.1 Direct revenue

New revenue traceable to the AI capability.
Clean examples: an AI-driven product tier
that customers pay for separately; a volume
of transactions that would not have occurred
without the capability. Harder examples: an
AI-assisted sales process that increases
conversion rates — the attribution requires a
counterfactual (what conversion would have
been without the AI), which is estimated
rather than observed.

### 7.4.2 Cost avoidance

Costs that would have been incurred without
the capability but were avoided. Classical
examples: AI-driven fraud detection
preventing losses; AI-driven process
automation reducing operational headcount
spend; AI-driven document processing reducing
third-party service spend.

Cost avoidance is where attribution gets
contested. The baseline — what cost would have
been without the capability — is a
counterfactual that different stakeholders
measure differently. The CAO function's
disclosure discipline matters here: name the
baseline, name the measurement method, do not
over-claim.

### 7.4.3 Capability enablement

Value created by capabilities that are
*preconditions* for other value — a trust
architecture ([`mod-106`](../mod-106-trust-architecture/README.md))
does not produce direct revenue but enables
customer-facing AI capabilities that do. A
governance platform does not produce
revenue but reduces the time-to-production
for new AI capabilities.

Enablement value is reported *qualitatively* in
the portfolio view rather than monetised,
unless the firm has a defensible method for
monetising enablement (uncommon; usually not
worth the methodological debate).

### 7.4.4 Avoided tail risk

The expected value of risks the capability
*mitigates*. This is particularly relevant for
AI-driven risk-management capabilities (fraud,
AML, cybersecurity, model-risk monitoring).
The reporting discipline is to disclose the
loss-expectation framework used; different
frameworks produce different numbers and
cross-period comparison requires framework
stability.

## 7.5 Risk-adjusted ROI

ROI reported without risk adjustment produces
a misleading view. A capability with high
gross ROI but high residual risk is not the
same investment as a capability with the same
gross ROI and low residual risk. Three
patterns for risk adjustment:

### 7.5.1 Realised-incident attribution

The simplest. Realised incident costs
(§7.3.4) are subtracted from gross returns.
Captures risk that has already crystallised;
does not capture unrealised risk.

### 7.5.2 Expected-loss adjustment

A probability-weighted expected loss is
subtracted. The probability is derived from
the risk-posture rating (within appetite /
approaching boundary / outside appetite) and
the risk tier. More comprehensive than
realised-only; introduces estimation error
that the reporting must disclose.

### 7.5.3 Appetite-conditional

Returns are reported only when the
capability is operating within appetite.
Capabilities operating outside appetite are
reported separately with the risk disposition
pending — the implicit view is that returns
earned outside appetite are not creditable
to the portfolio in a way the board should
recognise. This is the most conservative
pattern and the one that most strongly aligns
the value view with the risk view.

The chosen pattern is a reporting-policy
decision, made jointly between the CAO and
the CFO, ratified by the Audit Committee. It
is disclosed in the reporting itself.

## 7.6 The reporting structure

The portfolio P&L and ROI reporting sits in
one of two places depending on the firm's
pattern:

### 7.6.1 Dedicated section in the quarterly report

For firms where AI is a strategic priority,
the portfolio view is a section of the
Chapter 3 quarterly report (not one of the
six core sections; typically a separate
section after Asks or in the lead appendix).
~ 1 page, with:

- Portfolio-level summary — total AI spend,
  total gross returns, total risk-adjusted
  returns, direction vs. prior quarter.
- Top three capabilities by investment.
- Top three capabilities by return.
- Material concentration risks (vendor,
  infrastructure, internal single-points).

### 7.6.2 Separate annual report to Audit
       Committee and CFO

For firms where AI is one priority among
several, the portfolio view may be reported
annually (parallel to the Chapter 6 self-
assessment) rather than quarterly, with
quarterly updates only on material changes.
The annual report is longer and more detailed
— ~ 5-8 pages — and routes to the Audit
Committee and the CFO directly, with the
Board Risk Committee receiving the summary.

### 7.6.3 In both patterns

- The reporting reconciles to the CFO's
  authoritative financial record. Material
  reconciliation differences are disclosed.
- The attribution methodology is disclosed;
  cross-period comparison requires
  methodology stability.
- The risk adjustment pattern is disclosed;
  risk-adjusted and gross returns are both
  reported where feasible.
- Concentration risks are called out
  specifically — the single-vendor-LLM
  concentration, the single-model
  concentration, the single-team key-person
  concentration.

## 7.7 The common failure modes

### 7.7.1 Gross-only ROI

The portfolio reports gross returns without
risk adjustment. Board reads the ROI
favourably; incident surfaces later; the
implied prior overstatement erodes
credibility. The remedy is to report
risk-adjusted alongside gross and to disclose
the adjustment method.

### 7.7.2 Counterfactual stretch

Value attribution relies on counterfactuals
that over-reach (the AI drove the entire
customer-conversion increase; the AI
prevented all the fraud losses the baseline
would have incurred). Any individual
counterfactual may be defensible; the
portfolio pattern of consistently
over-attributing produces a cumulative
over-statement that becomes visible across
cycles.

The remedy is methodological conservatism —
measurement methods documented, baselines
named, estimation uncertainty disclosed. A
smaller honest number is more valuable to
the board than a larger stretched one.

### 7.7.3 Governance costs omitted

The CAO function cost is not attributed to
the portfolio; the gross-value number
ignores the second-line overhead that
supports the capabilities. Boards and CFOs
reading the view notice. The pattern tends
to emerge when the CAO function budget is
treated as "overhead" rather than as "cost
of operating the AI portfolio responsibly."
The remedy is explicit §7.3.3 attribution.

### 7.7.4 Enablement capitalised as value

Enablement capabilities (trust architecture,
governance platform, audit ledger
infrastructure) are reported as "value
delivered" when they are actually
preconditions for value delivery elsewhere.
The pattern inflates the apparent portfolio
return and double-counts: the enablement
value is also claimed in the downstream
capabilities it enables. The remedy is
qualitative reporting of enablement value
(§7.4.3) rather than monetised reporting.

## 7.8 The CFO relationship

The portfolio P&L and ROI reporting is a
substantive collaboration with the CFO
function. The relationship works when:

- **The accounting policies are shared.**
  Capitalisation thresholds, depreciation
  schedules, attribution rules — the CAO
  does not independently decide these; the
  CFO's policies apply.
- **The reconciliation is routine.** The
  CAO's portfolio view reconciles to the
  general ledger at known check-points; the
  reconciliation differences are small and
  explained.
- **The reporting cadences align.** The
  CAO's portfolio report is produced in the
  same cadence as the CFO's financial
  reporting, with the same close discipline.
- **Methodology changes are joint
  decisions.** A change in attribution
  methodology or risk-adjustment pattern is
  jointly ratified before taking effect, so
  the two reports do not later disagree.

The relationship fails when the CAO's
portfolio view is produced in isolation from
the CFO's record. The two views then diverge
over cycles and the Audit Committee asks why.

## Summary

- Portfolio P&L and ROI reporting completes
  the board's view — a program reported only
  on risk gives the board half the picture
  and invites the "what is this for?"
  question.
- The CAO owns the portfolio consolidation;
  the CFO owns the authoritative financial
  record. The portfolio view reconciles to
  the CFO's books.
- The portfolio inventory extends the model
  inventory and the vendor register with
  cost, value, risk tier, and concentration
  dimensions.
- Cost attribution has four categories:
  direct build, direct run, governance
  overhead, risk and incident costs.
- Value attribution has four patterns: direct
  revenue, cost avoidance, capability
  enablement, avoided tail risk. The last
  two are hardest to monetise; disclosure
  discipline matters.
- Risk-adjusted ROI is reported alongside
  gross — realised-incident, expected-loss,
  or appetite-conditional. The pattern used
  is a joint CAO/CFO reporting-policy
  decision, disclosed in the reporting
  itself.
- Reporting lives in a dedicated quarterly
  section (strategic-priority firms) or an
  annual Audit-Committee report (other
  firms). In both patterns, reconciliation
  to the general ledger and methodology
  disclosure matter.
- Common failure modes: gross-only ROI,
  counterfactual stretch, omitted governance
  costs, enablement capitalised as value.
- The relationship with the CFO is a
  substantive collaboration; divergent views
  between the CAO's portfolio report and
  the CFO's financial record are a specific
  Audit Committee finding to avoid.
