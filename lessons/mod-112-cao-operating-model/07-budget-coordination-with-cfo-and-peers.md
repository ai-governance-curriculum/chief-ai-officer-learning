# Chapter 7 — Budget Coordination with the CFO and CxO Peers

## Why this chapter exists

The CAO budget sits at an awkward altitude.
It is large enough that the CFO cares about
its shape, small enough that the CFO does not
staff a specialist to manage it, and new
enough that neither the CFO's existing
templates nor the firm's existing capital
discipline fully fits. On top of that, AI
investment increasingly dominates the
*enterprise* technology envelope — training
compute, foundation-model subscriptions,
GPU-dense infrastructure, AI-enablement
tooling — and that envelope is contested
across the CTO, CIO, Chief Data Officer,
CISO, CMO, CRO, and lines of business. The
CAO is one voice among many in a conversation
the CFO is trying to adjudicate.

The CAO who treats budget as a *request*
process — "here is what the function needs
next year" — gets the function's budget cut
every year the CFO is under pressure. The
CAO who treats budget as a *strategic
coordination* process — one leg of a
cross-CxO conversation about the enterprise
AI envelope — defends the function and
contributes to the enterprise's AI financial
discipline.

This chapter is specifically about the
*coordination* work — how the CAO engages
the CFO and the CxO peers on the AI budget
envelope at the CEO / board altitude.
[`mod-111`](../mod-111-board-reporting/README.md)
Chapter 7 covered the portfolio P&L and ROI
*reporting* substrate; this chapter covers
the *budget conversation* that reporting
substrate feeds.

## 7.1 The three budgets, named

The CAO is engaged with three distinct
budgets that in many firms get conflated:

### 7.1.1 The CAO function budget

The CAO function's own cost — the team's
compensation, the tools the function
operates (audit ledger infrastructure, trust
architecture monitoring tools, GRC tooling),
specific external engagements (counsel,
specialist consultants, external
benchmarking). Typically single-digit
millions in large firms; smaller elsewhere.
This budget the CAO owns and defends
directly.

### 7.1.2 The enterprise AI investment envelope

The firm's total AI investment: model
development, foundation-model vendor spend,
training infrastructure, AI-enablement
tooling across the organisation. This budget
is distributed across the CTO / CIO (platform
and infrastructure), the LOB leaders
(business-specific AI capability spend), the
CDO (data and model infrastructure), and the
CMO (AI in marketing / growth). The CAO
does not own the envelope but has a
specific stake: the governance load scales
with the envelope. Doubling the envelope
without expanding the governance budget is a
structural error the CFO rarely spots
unaided.

### 7.1.3 The AI risk reserve

In firms that treat AI as material risk, a
risk reserve — explicit or implicit — against
potential AI losses: fines, remediation
costs, incident response. The reserve
intersects with ERM's broader operational
risk reserves and with the firm's capital
planning. Insurance and banking firms are
further along on this than other sectors.
The CAO contributes to the sizing
conversation; the CFO and CRO own it
jointly. See the Basel III operational risk
framework (BCBS Standardised Approach) and
the COSO ERM Compliance Supplement for the
governing patterns.

The CAO's budget conversation covers all
three. Programs that defend only the first
and ignore the other two end up with a
function that cannot keep up with the
envelope and a firm that is under-reserved.

## 7.2 The CFO as partner

The CFO is a specific partner for the CAO
across all three budgets. The relationship
is one of the two or three most consequential
CxO relationships the CAO has (alongside the
CRO and GC) and is often the one CAOs
under-invest in during year 1.

The CFO cares about:

- **Return on invested capital.** Across the
  AI envelope and in each specific
  investment.
- **Capital allocation discipline.** Clear
  criteria for approving investment,
  measuring return, pulling or sustaining
  investment on review.
- **Expense predictability.** Steady-state
  costs that can be budgeted; growth that
  can be planned.
- **Downside sizing.** What is the AI
  programme's exposure if specific risks
  materialise? Fines, remediation, operational
  loss, reputational.
- **Audit and controls.** The CFO owns the
  firm's financial controls and will want to
  know how AI-related expenditure, revenue
  attribution, and the risk reserve interact
  with the audit opinion.

The CAO cares about:

- **Function budget sized to the governance
  load.** Which is driven by the envelope
  more than by the CAO's own ambition.
- **Appetite-constrained envelope growth.**
  The appetite statement
  ([`mod-111`](../mod-111-board-reporting/README.md)
  Chapter 2) implicitly constrains how
  quickly AI investment can be absorbed
  without taking on risk outside appetite.
  The CAO's seat in the envelope conversation
  is the mechanism for making that
  constraint explicit.
- **Risk reserve sized to the envelope and
  posture.** Under-reserved programs
  surprise the CFO when losses materialise.
- **Vendor and infrastructure concentration
  visibility.** The CFO sees spend
  concentration; the CAO sees value and
  dependency concentration. The two views
  reconcile in the portfolio view
  ([`mod-111`](../mod-111-board-reporting/README.md)
  Chapter 7).

The alignment: both roles care about AI
being a sustainable investment with sized
risk. The CFO is the natural ally for
appetite-constrained envelope growth; the
CAO is the natural ally for governance-sized
risk reserve. Programs where the CFO and
CAO work the AI budget together have both
functions better supported than programs
where either tries to operate alone.

## 7.3 The CxO peer conversation

The AI envelope is contested across more
than two seats. A working CAO engages at
least five CxO peers deliberately on the
envelope conversation.

### 7.3.1 CTO / CIO

The CTO (or CIO) owns most of the
infrastructure and platform spend inside the
envelope. The specific CAO contribution:

- Governance load scales with the number
  and tier of AI systems the platform
  supports; the trust architecture
  ([`mod-106`](../mod-106-trust-architecture/README.md))
  has a direct cost that lives in the CTO
  budget line but is driven by governance
  requirements the CAO sets.
- Vendor concentration decisions (which
  foundation model vendors to standardise
  on; which to maintain as alternates) have
  governance implications the CAO owns and
  cost implications the CTO owns.
- Build-vs-buy decisions on specific AI
  capabilities have risk-posture
  implications the CAO owns and cost
  implications the CTO owns.

### 7.3.2 Chief Data Officer

The CDO owns data infrastructure and
AI-adjacent data governance. The specific
CAO contribution:

- Training data governance (consent,
  provenance, licensing) is CDO-owned but
  governance-constrained; the appetite
  statement's data-use category sets what
  the CDO can and cannot do with specific
  data classes.
- Data retention and model-reversion
  policies interact with both functions.
- Model inventory
  ([`mod-104`](../mod-104-model-risk-management/README.md)
  Chapter 5) and data lineage are joint
  concerns; the budget to maintain them
  tends to sit in the CDO's lane.

### 7.3.3 CISO

The CISO owns security and increasingly
owns some of the AI-security budget (prompt-
injection controls, model-exfiltration
controls, etc.). See
[`mod-107`](../mod-107-ai-security/README.md)
on the boundary. The CAO contribution:

- The trust architecture and the security
  architecture overlap; coordinated budget
  defends against duplicated spend and
  against gaps between the two.
- Incident response capacity
  ([`mod-110`](../mod-110-incident-response/README.md))
  often straddles the CISO's existing
  security operations function and the
  AI-specific response machinery; joint
  budgeting is the pattern that works.

### 7.3.4 CRO

The CRO owns ERM and typically owns MRM
(and in financial services often owns the
AI risk function entirely before a CAO is
appointed). The CAO contribution:

- MRM capacity
  ([`mod-104`](../mod-104-model-risk-management/README.md))
  is driven partly by AI model volume; the
  envelope and MRM budget correlate.
- Operational risk reserve for AI falls
  under the CRO's broader operational risk
  framework; the CAO sizes the AI-specific
  piece.

### 7.3.5 Line-of-business leaders

Each business-unit head owns a slice of the
envelope — the AI capabilities their LOB is
building or buying. The CAO contribution:

- Governance load per LOB is proportionate
  to the LOB's AI investment and risk tier
  distribution; LOBs that over-invest without
  commensurate governance support generate
  friction later.
- The LOB's budget should include its share
  of the trust architecture, evidence, and
  response infrastructure the enterprise
  provides. Shared-cost allocation is a
  conversation the CFO leads; the CAO
  informs on the shape of the governance
  consumption.

The CAO's seat in the enterprise AI
investment conversation is not primarily
*adversarial* — it is coordinating. The
CAO's specific contribution is the view
that spans the envelope and the risk
posture, which no other CxO sees in full.

## 7.4 Budget framing: the three postures

Three framings for the CAO's budget
conversation that work; one that doesn't:

### 7.4.1 Tie investment to risk reduction (works)

Not "the function needs X headcount to
operate" — "the governance load on tier-1
systems has grown by Y% over the past
twelve months; without the proposed
investment, impact assessments on new tier-1
systems slip beyond the appetite statement's
MAP coverage requirement by Q3". The CFO can
evaluate the second; the first reads as a
line item.

### 7.4.2 Phase the budget (works)

Year 1 is foundation-heavy; year 2 is
consolidation with continued growth; year 3
is operational with selective investment.
The specific phasing matches the arcs from
Chapters 2 through 4. A multi-year budget
with the shape made explicit — foundation,
consolidation, operation — reads differently
from an annual repeated request.

### 7.4.3 Show the cost of not investing (works)

Per
[`mod-111`](../mod-111-board-reporting/README.md)
Chapter 7 — what is the exposure if the
investment doesn't happen? "If MAP coverage
on tier-1 systems slips below the appetite
statement's 95% requirement, the following
regulators will have notification material
on examination: ..." is a specific exposure
the CFO and board can price. "The function
would be understaffed" is not.

### 7.4.4 Request-mode budgeting (doesn't work)

Line-item requests comparing against prior
year, without reference to the envelope or
to specific risk reductions, read as
institutional overhead. Overhead gets cut
first under pressure. The pattern breaks
when the CAO reframes from request to
coordination: "here is how the governance
budget scales with the envelope and what
specific risk postures each level supports".

## 7.5 The annual budget cycle

A working CAO budget cycle has a specific
rhythm. The dates vary by firm; the
sequence is stable.

| When | Who | What |
|---|---|---|
| Pre-cycle (Q2-Q3 of fiscal year) | CAO + direct reports | Next-year scope hypothesis: specific capability additions, specific risk postures |
| Pre-cycle | CAO + CTO + CDO + CISO | Peer coordination on envelope shape — what the function expects the envelope to grow into, what governance load that implies |
| Pre-cycle | CAO + CRO + CFO | Risk reserve sizing update; appetite statement signals for budget purposes |
| Cycle open (Q3) | CAO | Function budget submission framed per §7.4 |
| Cycle open | CAO + CFO | Review of function budget in context of envelope; iterations |
| Cycle open | CAO | Submission to Board Risk Committee (where applicable) ahead of board budget review |
| Cycle close (Q4) | CAO + CFO + Board | Board budget approval; specific CAO function allocation; envelope-wide allocations finalised |
| In-year | CAO | Quarterly re-forecast against actuals; variance surfaced to the Board Risk Committee in the quarterly report |

The CAO who shows up at the cycle open with
peer coordination already done, risk reserve
sized, and the function budget framed in
§7.4 postures walks in with the budget
roughly already defended. The CAO who shows
up at the cycle open with a request walks
into negotiation from a weaker starting
position.

## 7.6 Specific traps

Three recurring traps in the CAO budget
conversation:

### 7.6.1 Under-sizing the function to the envelope

The envelope grows; the function budget stays
flat under CFO pressure. The function
compresses silently rather than visibly
pushing back. Two years in, the function is
materially under-resourced relative to the
envelope and the board is surprised by the
state. The CAO's responsibility is to make
the envelope-vs-function sizing *visible* at
budget time, not to absorb the compression
silently and surface it later.

### 7.6.2 Pricing risk reserves off historical AI losses

Historical AI losses in most firms are
small — the technology is young. Pricing the
reserve off historical losses understates
the exposure materially. The CFO and CRO
share this trap; the CAO's role is to
contribute a forward-looking view (what are
peers seeing; what is the regulatory
notification regime signalling; what is the
appetite statement implying) that
counterweights the historical anchor.

### 7.6.3 Treating the envelope as the CTO's problem

The CTO and CIO own most of the envelope on
paper, which creates a temptation to treat
the envelope conversation as not a CAO
conversation. The envelope *is* the
governance load; a CAO who abdicates the
envelope conversation is implicitly
accepting whatever governance load the
envelope generates without a say in it. The
posture is coordinating, not deferring.

## Summary

- The CAO is engaged with three budgets: the
  function's own, the enterprise AI
  investment envelope, and the AI risk
  reserve. All three are the CAO's
  conversation.
- The CFO is a primary partner. The two
  functions align on sustainable investment
  with sized risk; the CAO's seat in the
  envelope conversation is the mechanism for
  making appetite-constrained envelope
  growth and governance-sized risk reserve
  explicit.
- Five CxO peers hold slices of the envelope:
  CTO/CIO, CDO, CISO, CRO, and the LOB
  leaders. The CAO's contribution is the
  view that spans the envelope and the risk
  posture — a view no other peer sees in
  full.
- Working budget framings tie investment to
  risk reduction, phase the budget to the
  foundation/consolidation/operation arcs,
  and show the cost of not investing. The
  framing that doesn't work is request-mode
  line-item budgeting against prior year.
- The budget cycle begins before the cycle
  opens — peer coordination, reserve sizing,
  and framing all happen in Q2-Q3 of the
  prior fiscal.
- Traps to avoid: silently under-sizing the
  function to a growing envelope; pricing
  reserves off thin historical AI loss data;
  treating the envelope as the CTO's
  conversation rather than a shared one.
