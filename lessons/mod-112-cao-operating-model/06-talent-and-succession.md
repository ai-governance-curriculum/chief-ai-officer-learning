# Chapter 6 — Talent and Succession

## Why this chapter exists

The CAO function is one of the more difficult
to staff. The roles are new; the required
combination of skills is unusual; the market
for AI governance practitioners is less
developed than the market for the roles the
function has to partner with (CRO staff, CISO
staff, MRM analysts). The specific pattern
that keeps CAO programs from maturing is not
missing a *strategy* for talent; it is
treating the strategy as a hiring plan and
not as a *succession and development
discipline*.

This chapter maps the talent profile the
function needs, the hiring sequence that
tends to work across year 1 and year 2, the
succession discipline that makes the function
survive the departure of any individual
(including the CAO), and the CAO's own
development.

Chapter 7 handles budget and CFO / CxO peer
coordination.

## 6.1 The talent profile

Roles in the CAO function require four
capability axes, each of which is scarce on
its own and particularly scarce in
combination:

- **Technical depth.** Enough to engage
  substantively with engineering, MRM, and
  the CISO's organisation. The function does
  not need the deepest ML researcher in the
  room; it needs people who can read a
  model card, understand a validation
  report, and ask the right follow-up
  questions. See
  [`mod-104`](../mod-104-model-risk-management/README.md)
  on what "substantively engage with MRM"
  requires.
- **Risk discipline.** Familiarity with
  risk-management frameworks and practice.
  COSO ERM, NIST AI RMF, three-lines-of-defense
  (IIA Three Lines Model), SR 11-7, EU AI
  Act and similar sectoral frameworks. The
  function cannot bootstrap this from
  scratch each hire.
- **Governance literacy.** Comfort with
  board, committee, and regulator dynamics.
  The ability to brief a board committee,
  draft a charter, draft an appetite
  statement, engage a regulator in a
  non-defensive posture. See
  [`mod-111`](../mod-111-board-reporting/README.md)
  for the full discipline.
- **Communication clarity.** The ability to
  write a 3-page report that a board can act
  on; the ability to run an AI Risk Council
  session; the ability to resolve a boundary
  dispute without turning it into a
  turf war.

This combination is rare. CAO functions
typically build it through hiring *across*
backgrounds — a risk background hire plus a
compliance background hire plus an engineering
background hire — rather than finding it in
every candidate. Programs that insist on all
four axes in every hire either do not hire or
hire slowly enough that the function cannot
cover the year-1 scope.

## 6.2 The hiring sequence

A typical year-1 / year-2 hiring sequence,
offered as a pattern rather than a
prescription:

| Hire | Year | Role | Representative background | Why this timing |
|---|---|---|---|---|
| CAO | Y0 | Chief AI Officer | Senior risk, program-lead, or MRM background with AI exposure | Starting condition |
| 1 | Y1 Q1 | AI Risk Lead | Risk professional; typically CRO-adjacent, MRM, or operational-risk background | Carries day-to-day so the CAO can set direction |
| 2 | Y1 Q1-Q2 | Policy Lead | Compliance, GC-adjacent, or policy-authorship background | Standards authorship is critical-path for year 1 |
| 3 | Y1 Q2 | Evidence Lead | Engineering, audit, or MRM-infrastructure background | Audit ledger + continuous evidence substrate |
| 4 | Y1 Q2-Q3 | Regulatory Engagement Lead | Legal, former regulator, or senior compliance background | Regulator interface and material notification matrix |
| 5 | Y2 | Deputy AI Risk Lead | Succession track for the AI Risk Lead | Function needs a continuity role before the CAO can shift (Chapter 4) |
| 6 | Y2 | Algorithm Validation Lead | MRM-adjacent or statistics / ML validation background | Partners with MRM at the CAO×MRM boundary |
| 7 | Y2 | Trust Architecture Lead | Engineering; cross-CISO partnership | Operational owner of the trust-gate infrastructure |
| 8 | Y2-Y3 | Communications / Board Lead | Board-reporting specialty | Enables the year-3 shift in CAO time toward board and strategic work |

Each specific shape varies by organisation; a
heavily-regulated US bank adds roles earlier
on the regulatory-engagement axis; an
AI-native product company adds roles earlier
on the engineering axis. The *sequence*
tends to hold: AI Risk Lead first, Policy
Lead second, Evidence and Regulatory
Engagement next, Deputy and specialists in
year 2.

### 6.2.1 Specific sequencing errors to avoid

Three patterns that recur:

- **Policy Lead before AI Risk Lead.** The
  function ends up policy-rich and
  operations-poor. The CAO is doing
  operational work the function should have
  someone operating.
- **Trust Architecture Lead before the
  CAO × CISO boundary is engaged.** The
  Trust Architecture Lead gets dropped into
  a boundary negotiation the CAO should have
  held first.
- **Specialists before generalists.** A
  specialist hired to a function that doesn't
  yet have shape ends up re-shaped into a
  generalist by the function's unmet needs,
  wasting the specialisation.

The pattern: the function hires generalists
first to establish shape and then specialists
to deepen specific capability.

## 6.3 Capability gaps and non-hiring mitigation

Not every capability gap can be hired. Three
specific gaps that are hard to hire in the
current market and the non-hiring
mitigations that work:

### 6.3.1 Vendor AI risk specialisation

Deep expertise in vendor-model risk —
specifically for foundation-model vendors —
is scarce. The function's year-1 capability
usually comes from one of three places:

- **A specialist consultant** engaged under
  retainer for the first 12-18 months,
  partnering with an internal lead who
  grows into the capability.
- **Partnership with the CISO's third-party
  risk management (TPRM) function**, which
  typically has vendor-risk discipline from
  non-AI vendors that transfers partially.
- **An industry peer network** — specifically
  through GARP or AICPA practitioner
  communities — that shares patterns on
  specific vendors.

The function builds the capability
internally over 12-24 months while running
with external support.

### 6.3.2 Deep statistical / ML validation

Expertise in validating specific ML
techniques — gradient boosting, deep neural
networks, LLMs — at the depth MRM has
traditionally brought to GLMs. In regulated
industries, MRM typically holds this
expertise and the CAO function partners
rather than duplicates. In non-regulated
industries, the function may need to hire
or contract specifically for it.

### 6.3.3 Regulatory engagement with multiple regimes

Depth in a specific regulator — the Fed's
SR 11-7 team, the OCC, EU AI Act competent
authorities, state insurance regulators —
is scarce and typically has to be hired for
one regime at a time. Multi-regime depth is
built by hiring regime-specific leads over
year 2 and year 3 rather than by trying to
hire one person who covers all regimes.

The pattern across the three gaps: the
mitigation is a *combination* of partnership,
retained external expertise, and multi-year
internal development. Function leads that
expect to close every gap by hiring will
either hire slowly or hire poorly.

## 6.4 Succession

Most boards and CEOs treat the CAO role as
person-specific in year 1 — *this* CAO. In
year 2 they begin asking "what happens
if?". In year 3 the question becomes formal
succession planning. The function should be
ahead of the question by year 2.

Three succession horizons:

### 6.4.1 Immediate succession (0-6 months)

If the CAO leaves unexpectedly — including
unexpected absence — who runs the function
until a replacement arrives?

- **Named interim CAO.** Usually the AI Risk
  Lead, in year 2 and beyond. In year 1, the
  CRO or a senior risk peer typically holds
  the interim designation because the
  function hasn't matured enough.
- **Top three priorities for the interim.**
  Specifically named, not generic — maintain
  the AI Risk Council and AI Review Board
  cadence; preserve the board reporting
  rhythm; cover any in-flight material
  incident. Three is roughly the right
  number; more creates a programme the
  interim cannot sustain.
- **Top three risks the interim monitors.**
  Boundary disputes freezing; the appetite
  statement being quietly stretched under
  business pressure; regulator engagement
  stalling.

The specific disciplines live in a documented
*succession playbook* the function
maintains. Not a confidential document — a
documented operating artifact. Boards
specifically ask to see this in year 2
and year 3.

### 6.4.2 Short-term succession (1-2 years)

Formal successor track. Internal candidates
specifically identified, with a development
plan.

- **Identified internal candidates.** The
  Deputy AI Risk Lead (if hired in year 2);
  the AI Risk Lead; occasionally a
  cross-functional candidate from the CRO
  or CCO organisation.
- **External pipeline.** Relationships with
  potential successors at peer institutions
  — not solicited directly, but known. The
  CAO's peer network from Chapter 5 §5.2.3
  is where the external pipeline lives.
- **Specific development plan.** Internal
  candidates get year-2 and year-3
  stretch assignments that develop the
  capabilities the CAO role requires but
  which the current role doesn't yet give
  them: board presentations, chairing the
  AI Risk Council for a quarter, leading
  a regulator engagement.

### 6.4.3 Longer-term succession (3-5 years)

Bench strength. Multiple potential
successors, the function's documented
operating model that supports succession,
and the work done now to make the function
*continuously succession-ready*.

The specific marker: the function can
operate for a quarter without the current
CAO without visible degradation. This is
not a thought experiment — mature CAO
functions test it in practice by having
the CAO take a formal 2-week absence in
year 2 and in year 3 and reviewing what
broke.

### 6.4.4 The CAO's own posture

The hardest part of succession is the CAO's
own posture. The temptation is to be
irreplaceable. The discipline is to be
*replaceable*. CAOs whose function depends
entirely on them produce programs that do
not survive their departure, which means
the risk-reduction work of the function was
load-bearing on one career.

The specific posture:

- Writing enough down that a successor can
  operate without multi-week handover.
- Delegating by charter (Chapter 5 §5.3)
  rather than by preference.
- Developing deputies so they can
  substantively run the function during
  2-week absences.
- Being candid with the board about
  succession readiness state — year 1:
  not succession-ready; year 2: interim
  succession plan in place; year 3:
  continuously succession-ready.

Boards strongly prefer CAOs who name
succession state candidly over CAOs who
reassure them the function is fine. The
candour is also what makes the function
actually succession-ready, because the
function knows what gaps to close.

## 6.5 The CAO's own development

The CAO is themselves a person needing
development. The role is isolating; the peer
group is small; the work is high-stakes.

Four practices that work:

### 6.5.1 Peer-CAO network

Monthly conversation with peers at
non-competing institutions. The non-competing
constraint matters — competitive dynamics
truncate what can be shared. Peer networks
can be organised through industry bodies
(GARP, AICPA), through alumni networks, or
through informal arrangements. The frequency
matters: a quarterly cadence is often not
frequent enough to maintain the shared
context; monthly is more sustainable.

### 6.5.2 Executive coaching

Specifically for the CAO role — not generic
executive coaching. The role has specific
dynamics (second-line in a cross-functional
field; new domain with evolving regulation;
board-visible without the executive
authority of first-line roles) that generic
coaching does not address.

### 6.5.3 Board chair relationship

The Audit Committee or Board Risk Committee
chair is often an undervalued mentor. The
chair sees the function from the oversight
side and can give feedback the CAO cannot
get elsewhere. A standing conversation
between the CAO and the Chair outside the
quarterly committee meeting — monthly or
every other month — is one of the
higher-leverage uses of CAO time.

### 6.5.4 Reading

AI safety, governance, regulatory
developments — continuously. The specific
sources rotate. The discipline is protecting
reading time (Chapter 5 §5.2.1) and
treating staleness as a career-impairing
risk rather than a minor one.

The CAO who treats their own development as
optional becomes the brittle keystone of an
otherwise mature program. The investment is
not optional at the CAO altitude.

## Summary

- The CAO function needs four capability
  axes: technical depth, risk discipline,
  governance literacy, communication clarity.
  The combination is rare; it is built
  across hires, not sought in every hire.
- The hiring sequence puts the AI Risk Lead
  first, Policy Lead second, Evidence and
  Regulatory Engagement next, and
  specialists (Deputy, Algorithm Validation,
  Trust Architecture, Communications) in
  year 2.
- Some capability gaps are hard to hire —
  vendor AI risk specialisation, deep ML
  validation, multi-regime regulatory
  engagement. The mitigation is partnership,
  retained external expertise, and
  multi-year internal development, not
  attempted single hires.
- Succession has three horizons: immediate
  (named interim; three priorities, three
  risks), short-term (internal candidates,
  external pipeline, development plan),
  longer-term (continuous succession-
  readiness tested by actual CAO absences).
- The CAO's own posture: be replaceable, not
  irreplaceable. The function should be able
  to run a quarter without the current CAO
  by year 3.
- CAO development: peer-CAO network
  (monthly), coaching specific to the role,
  the Audit / Risk Committee chair as
  mentor, continuous reading. Not optional
  at this altitude.
