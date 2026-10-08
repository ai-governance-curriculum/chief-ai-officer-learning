# Chapter 2 — Year 1: The Foundation Arc

## Why this chapter exists

Year 1 is unglamorous. Most of the work is
invisible from outside the function. The
deliverables are documents, charters, meetings
established — not the AI capabilities the board
hired the CAO to govern. The pressure to
produce *visible* work mounts somewhere between
month 4 and month 8, and the CAOs who pivot
toward visibility at that moment produce year-2
programs that look impressive briefly and
collapse under the first material challenge.

The discipline of year 1 is to lay the
foundation that lets year 2 operate rather than
build, and to communicate the foundation-laying
as the deliverable while it is happening. This
chapter maps the six things year 1 should
accomplish, the five things year 1 should
*not* try to accomplish, the mid-year-1
inflection point and how to navigate it, and
the year-1 self-assessment pattern that
honestly closes the arc.

## 2.1 What year 1 should accomplish

Six workstreams, roughly in this order. The
order is approximate — several run in
parallel — but the sequence is the natural
dependency chain.

### 2.1.1 Build the governance machinery

The AI Risk Council and AI Review Board exist
and operate. The charter is adopted. The
reporting lines are declared. The operating
model (Chapter 1) is explicit, whether
inherited or chosen. By end of Q1 these
should be in place and meeting on their
declared cadence. See
[`mod-101`](../mod-101-foundations/README.md)
Chapters 6 and 7.

### 2.1.2 Establish the program's authority

The AI risk appetite statement is drafted,
sharpened by the CRO / CFO / CCO / GC, endorsed
by the AI Risk Council, and adopted by the
Board Risk Committee or full board. The
policy hierarchy is declared — which
documents sit at policy altitude, which at
standard, which at procedure. See
[`mod-111`](../mod-111-board-reporting/README.md)
Chapter 2 for the appetite pattern.

Authority without the appetite statement is
discretionary; year-2 operating decisions
cannot ladder up cleanly to a board-ratified
posture. Year 1 produces the statement.

### 2.1.3 Stand up the operational discipline

Six specific substrates are needed before the
program can operate:

- **Model / system inventory** per
  [`mod-104`](../mod-104-model-risk-management/README.md)
  Chapter 5 — the inventory of what you have
  and the tier assigned to each system.
- **Impact assessments** per the NIST AI RMF
  MAP function and ISO/IEC 42001 Annex A
  controls — initial pass on tier-1 systems
  within year 1.
- **Monitoring infrastructure** per
  [`mod-106`](../mod-106-trust-architecture/README.md)
  — the trust architecture components (bias,
  drift, hallucination, abuse monitoring) in
  place on tier-1 systems.
- **Audit ledger / evidence layer** per
  [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)
  — the records substrate that supports
  everything downstream.
- **Incident response machinery** per
  [`mod-110`](../mod-110-incident-response/README.md)
  — the response playbook, the single-named-lead
  pattern, the notification matrix.
- **Compliance evidence cadence** per
  [`mod-109`](../mod-109-compliance-operations/README.md)
  — the continuous evidence pattern operating
  on at least a subset of controls.

Year 1 does not need every substrate operating
at full coverage. It needs each in place at
tier-1 coverage with the gaps documented.

### 2.1.4 Engage the boundaries

The CAO × MRM boundary
([`mod-104`](../mod-104-model-risk-management/README.md)
Chapter 6), CAO × CISO boundary
([`mod-107`](../mod-107-ai-security/README.md)),
and CAO × Compliance boundary
([`mod-109`](../mod-109-compliance-operations/README.md))
each need to have been engaged formally
during year 1. Not necessarily resolved — some
boundaries will not be fully resolved for
years — but engaged, with written positions
documented and a cadence for re-engagement
established.

Year-1 boundary discussions that are deferred
without engagement become year-2 crises when
the first incident forces the question in
real time.

### 2.1.5 Hire the team

The first 4-5 roles that will carry year 2
(see Chapter 6 §6.2 for the typical sequence):

| Hire | Timing | Role |
|---|---|---|
| 1 | Q1 | AI Risk Lead |
| 2 | Q1-Q2 | Policy Lead |
| 3 | Q2 | Evidence Lead |
| 4 | Q2-Q3 | Regulatory Engagement Lead |
| 5 | Q3-Q4 | Deputy / specialist (deferrable) |

Year-1 hiring sequencing is specific. The AI
Risk Lead is hire #1 because the lead will
carry the day-to-day operations the CAO
should not personally own by month 6. The
Policy Lead is hire #2 because the standards
authorship is a critical path for the whole
year. Hiring sequences that reverse these
leave the CAO personally doing operational
and policy work the function needs to be
able to delegate by year 2.

### 2.1.6 Brief and engage the board

Quarterly board reports are operating by Q2
at latest, per
[`mod-111`](../mod-111-board-reporting/README.md)
Chapter 3. The appetite statement is formally
adopted by the board in Q3 or Q4. The first
annual self-assessment is produced at end of
Q4 (§2.4 below).

The board engagement cadence in year 1 is
particularly important because it establishes
the posture the board uses for the next
several years: a board that in year 1
experienced a CAO who over-reported or
under-reported takes years to recalibrate.

## 2.2 What year 1 should not try to do

Equally important. Year 1 will be *tempted* to
attempt all of the following and should defer
them:

- **Solve every gap.** Year 1 inventories and
  impact assessments will surface numerous
  gaps. Picking which ones to address in year
  1 and which to document for year 2 is the
  year-1 discipline. Attempting to close
  everything produces a year 1 that never
  finishes foundation.
- **Build comprehensive automation.**
  [`mod-109`](../mod-109-compliance-operations/README.md)
  §4.3 names automation-before-practice-maturity
  as a specific failure mode. Year 1 builds
  the practice; year 2 considers automation
  of the practice. Automation of a practice
  that is not yet stable produces automated
  wrongness.
- **Run many tabletops.**
  [`mod-110`](../mod-110-incident-response/README.md)
  §6.5 names tabletop overuse as a specific
  anti-pattern. One substantive tabletop in
  year 1 — on the single most plausible
  material scenario — is enough. More is
  performance of discipline rather than
  practice of it.
- **Author every standard at once.** The
  program standards take time to draft well.
  Year 1 produces the load-bearing ones (the
  policy hierarchy itself, a transparency
  standard, a defense-in-depth standard, an
  AI incident classification taxonomy) and
  defers the rest. A function that produces
  twenty draft standards in year 1 is almost
  certainly producing twenty weak standards.
- **Win every boundary discussion.** Some
  boundary discussions are not yet ripe in
  year 1 — the CAO function doesn't yet have
  the operating history to argue the case
  from. Documenting positions and
  re-engaging in year 2 is acceptable.
  Pressing to resolution prematurely tends
  to produce resolutions that have to be
  re-opened later.

The discipline is naming what you are *not*
doing in year 1 and defending it — to
yourself, to the AI Risk Council, and to the
board.

## 2.3 The mid-year-1 inflection point

Somewhere between month 6 and month 8 of year
1, almost every CAO hits the same inflection
point:

- The foundation work is substantial.
- The visible deliverables are limited.
- Pressure for visible results mounts — from
  the CEO, from business-unit heads, from
  the Board Risk Committee chair in casual
  side conversations.
- The CAO function is small enough that
  everyone can see each other is working;
  outside the function, it is less obvious.

The temptation at this inflection is to pivot
to visible deliverables: a bias dashboard
that is impressive to demo but not yet
calibrated; an AI policy that is published
to the intranet before it is substantively
load-bearing; a vendor risk framework that
has a template but no filled instances.

The discipline is to continue the foundation
work and to **communicate the
foundation-laying as the deliverable**. The
Q2 and Q3 board reports can show foundation
progress specifically:

> *"AI Risk Council operating monthly;
> impact assessments completed on five
> Tier-1 systems with specific findings
> documented in Appendix A; trust
> architecture monitoring deployed on three
> Tier-1 systems; policy hierarchy drafted
> and in AI Risk Council review; first
> annual AI incident response tabletop
> scheduled for Q4."*

That is a substantive update. It is not an
exciting demo. The board that is used to
exciting demos has to be re-trained on what
substantive governance progress looks like,
and the CAO who re-trains them well is
building the credibility that will matter
in year 2.

CAOs who pivot prematurely at month 6-8
produce year-2 programs that have visible
apparatus but weak foundation. The apparatus
collapses the first time a material incident
tests it, and the year-2 program spends six
months rebuilding what year 1 should have
built in the first place.

## 2.4 The end-of-year-1 self-assessment

The annual self-assessment from
[`mod-111`](../mod-111-board-reporting/README.md)
Chapter 6 is particularly important at the
end of year 1. The honest read is rarely
"the program is mature"; it is usually "the
foundation is laid and the program is ready
to consolidate". This is the right read for
a year-1 self-assessment.

Specific markers of a healthy year-1
self-assessment:

- Program maturity, assessed per
  [`mod-111`](../mod-111-board-reporting/README.md)
  Chapter 6 §6.1.1 against the practitioner
  CMMI-style maturity levels commonly applied
  to NIST AI RMF functions (Initial, Developing,
  Defined, Managed, Optimising), reads as
  **Developing** across most functions, with a
  small number at **Initial**. A year-1
  self-assessment that claims **Defined** or
  higher across the board is almost certainly
  over-rating.
- The findings section names **specific gaps**
  with specific year-2 owners and timelines. A
  self-assessment with no findings is not
  credible; a self-assessment with twenty
  findings is likely cataloguing rather than
  prioritising.
- The year-2 priorities ladder cleanly from
  the findings — if the findings say gap X,
  year-2 priorities should name closing X
  explicitly. Priorities that do not trace
  back to findings tell the board the
  self-assessment and the plan are
  disconnected.

The self-assessment is also the artifact that
most clearly surfaces whether the CAO survived
the mid-year inflection point (§2.3). A
foundation-laid self-assessment at end of year
1 is a healthier read than a mature-program
self-assessment, because the first is honest
and the second is almost always wrong.

## 2.5 The specific year-1 postures that matter

Three personal-posture patterns that
differentiate year-1 CAOs who build well
from year-1 CAOs who do not:

- **Listen more than opine, for the first
  quarter.** The CAO's first quarter is
  largely about understanding the
  organisation's existing risk and
  compliance architecture, the business
  units' AI deployment reality, and the
  board's priorities. CAOs who come in with
  a declared program on day 1 miss context
  that would have changed the program.
- **Be visibly resource-constrained, not
  frantic.** The CAO function's budget is
  being justified for the first time
  (Chapter 7). Showing constraint and
  prioritisation reads as discipline; showing
  frantic activity reads as under-staffing
  and attracts the wrong kind of help.
- **Make the first material disagreement
  honestly.** At some point in year 1 the
  CAO will disagree with a business-unit
  head, the CTO, or the CRO about a
  specific case. The first time this
  happens is formative: a CAO who
  capitulates establishes that the function
  is advisory; a CAO who registers the
  disagreement cleanly, per
  [`mod-105`](../mod-105-responsible-ai-and-ethics/README.md)
  §6.5 and
  [`mod-111`](../mod-111-board-reporting/README.md)
  Chapter 5, establishes that the function
  is substantive.

## Summary

- Year 1 is foundation. Six workstreams —
  governance machinery, program authority,
  operational discipline, boundary
  engagement, team hiring, board engagement.
- Five explicit non-goals — don't solve
  every gap, don't automate before practice
  maturity, don't tabletop-overload, don't
  author every standard, don't win every
  boundary discussion.
- The mid-year-1 inflection (month 6-8) is
  where the temptation to pivot to visible
  deliverables peaks. The discipline is to
  continue foundation-laying and communicate
  it as the deliverable.
- The year-1 self-assessment should read as
  "foundation laid, ready to consolidate" —
  not as "program mature". Honesty here
  sets the posture for year 2.
- Personal postures: listen before opining
  for the first quarter; be constrained
  rather than frantic; register the first
  material disagreement cleanly.
