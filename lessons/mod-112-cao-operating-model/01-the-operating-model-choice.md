# Chapter 1 — The Operating-Model Choice, Revisited

## Why this chapter exists

[`mod-101`](../mod-101-foundations/README.md)
Chapter 6 introduced the three structural
patterns a governance function can take —
**centralised**, **federated**, and
**hub-and-spoke** — and the usual arguments for
and against each. That chapter asked you to pick
one for a specific hypothetical. This chapter
asks a harder question: now that you have seen
what each pattern *produces downstream* — across
model risk management
([`mod-104`](../mod-104-model-risk-management/README.md)),
trust architecture
([`mod-106`](../mod-106-trust-architecture/README.md)),
security partnership
([`mod-107`](../mod-107-ai-security/README.md)),
the evidence substrate
([`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)),
continuous compliance
([`mod-109`](../mod-109-compliance-operations/README.md)),
incident response
([`mod-110`](../mod-110-incident-response/README.md)),
and board reporting
([`mod-111`](../mod-111-board-reporting/README.md))
— how do you make or defend the choice?

The structural choice is the single decision that
most shapes how the function spends the next
three years. It is also the decision CAOs most
often *inherit* rather than *make*. The chapter
teaches both: what the choice determines, how
context shapes it, and how to operate inside a
model you did not pick.

## 1.1 What the choice determines

The operating model is not a diagram on the HR
chart. It is the enforcement mechanism for a
set of downstream properties the program will
have to live with:

- **Who decides what controls apply where.** In
  centralised, the hub decides and the business
  unit executes. In federated, the business unit
  decides within standards the hub sets. In
  hub-and-spoke, decisions are negotiated — the
  hub owns the standards and the serious cases,
  the spokes own routine application.
- **Where the evidence lives.** Centralised
  produces consolidated evidence under a single
  schema; federated produces per-business-unit
  evidence with reconciliation overhead;
  hub-and-spoke centralises evidence for the
  controls the hub owns and distributes evidence
  for the controls the spokes own. The evidence
  topology drives how
  [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)
  and
  [`mod-109`](../mod-109-compliance-operations/README.md)
  can be implemented.
- **How the CAO function scales.** Centralised
  scales linearly with hub headcount — more AI
  systems means more hub reviewers. Federated
  scales by replicating the pattern per
  business-unit, which is cheaper per unit at
  the margin but more expensive to coordinate.
  Hub-and-spoke scales selectively: the hub
  grows slowly, the spokes grow with the
  business.
- **Where the program is brittle.** Centralised
  has **hub key-person risk**: when the AI Risk
  Lead or Policy Lead leaves, continuity is
  materially impaired. Federated has
  **consistency risk**: the same scenario is
  decided differently across business units.
  Hub-and-spoke has **coordination overhead**:
  decisions that cross the boundary take longer
  and sometimes do not resolve.
- **How regulators see the program.** A
  centralised program presents a single
  interface, which simplifies examinations but
  places all exam pressure on a small team. A
  federated program presents per-business-unit
  interfaces, which spreads the pressure but can
  surface inconsistency findings. A hub-and-spoke
  program presents both layers; the regulator
  sees the hub's framework and the spokes'
  execution and will probe the connection
  between them.
- **How boundary partners engage.** The CRO,
  CCO, CISO, GC, and MRM Lead engage the CAO
  function differently depending on model. Peer
  functions whose own architecture matches the
  CAO function's architecture integrate more
  cleanly; mismatched models create recurring
  friction. The engagement contract patterns
  from
  [`mod-101`](../mod-101-foundations/README.md)
  Chapter 7 presume a specific operating model
  on both sides.

## 1.2 The choice is contextual

There is no universally correct model. The
choice depends on at least five factors:

- **Organisation size and complexity.** Small,
  single-business organisations settle naturally
  into centralised. Large, multi-line-of-business
  organisations with distinct regulatory
  perimeters settle naturally into federated or
  hub-and-spoke. The transition point is not
  defined by headcount alone; it is defined by
  the point at which a central team can no
  longer stay substantively close to each
  business unit's work.
- **Regulatory landscape.** Single-regulator
  contexts (a US-only insurer; a national-only
  bank) favour centralised because the
  interface is singular. Multi-regulator
  contexts (a global bank subject to US, UK,
  EU regulation simultaneously) favour
  distributed approaches, because no central
  team can hold the regulatory knowledge in
  one place.
- **Existing risk-function architecture.** If
  enterprise risk management (ERM) is
  centralised under a group CRO, the CAO
  function usually follows the pattern;
  misaligned architectures create friction at
  every boundary. If ERM is federated, the CAO
  function usually follows federated. The
  [`mod-104`](../mod-104-model-risk-management/README.md)
  CAO×MRM boundary is one specific case of this
  principle — the two functions operate most
  cleanly when their structures match.
- **Maturity of AI deployment.** Programs in
  the early stages benefit from centralised
  decision-making: the number of material
  cases is small, consistency matters most,
  and a federated structure spreads scarce
  expertise too thinly. Mature programs can
  sustain federated or hub-and-spoke, because
  the shared vocabulary and standards are in
  place and the business units can execute
  them.
- **Executive sponsorship pattern.** A CEO who
  wants a single accountable AI leader
  accountable to them for everything AI
  pushes toward centralised. A CEO who treats
  AI as a cross-functional capability pushes
  toward federated or hub-and-spoke. The CAO
  is rarely in a position to overrule this
  preference in year 1.

The choice emerges from the combination, not
from any single factor. Programs that choose
their model from a single factor (usually
"what my peer institution does" or "what the
consulting deck recommends") are often
course-correcting within two years.

## 1.3 The choice carries forward

The downstream consequences across the track
form a coherent pattern once you have worked
through the modules:

- The **CAO × MRM** split
  ([`mod-104`](../mod-104-model-risk-management/README.md)
  Chapter 6) operates most cleanly in
  **hub-and-spoke**. The hub (CAO) sets the AI
  risk framework and specific AI-era controls;
  MRM retains its SR 11-7 discipline for
  individual-model validation; the two
  functions have natural counterparts because
  both are second-line.
- The **CAO × CISO** boundary
  ([`mod-107`](../mod-107-ai-security/README.md))
  operates most cleanly in **centralised**,
  where the boundary discussion happens once
  at the enterprise level rather than
  per-business-unit. Where the boundary is
  negotiated in each business unit, it tends
  to drift inconsistently.
- The **CAO × Compliance** boundary
  ([`mod-109`](../mod-109-compliance-operations/README.md))
  operates most cleanly when the operating
  models of the two functions **match** —
  both centralised, or both federated. A
  centralised compliance function matched
  with a federated CAO function or vice versa
  produces recurring friction on who evidences
  what.
- The **evidence infrastructure**
  ([`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md))
  is more efficient when **centralised**
  regardless of the broader CAO operating
  model. Many hub-and-spoke programs centralise
  the audit ledger specifically — the hub
  owns the ledger even where the spokes own
  the decisions it records.
- The **incident response** flow
  ([`mod-110`](../mod-110-incident-response/README.md))
  needs a **single named lead** per incident
  regardless of operating model. Federated
  programs that distribute incident response
  across business-unit leads discover that
  cross-cutting incidents are nobody's job to
  own. The hub-and-spoke pattern — hub owns
  incident coordination even where the
  substantive work happens in the spokes —
  tends to be the most durable.
- The **board interface**
  ([`mod-111`](../mod-111-board-reporting/README.md))
  is almost always **centralised at the top**,
  regardless of the operating model below it.
  The board does not want a separate report
  per business-unit AI programme; it wants one
  consolidated report. The CAO consolidates
  for the board interface even when the work
  below is federated.

The structural insight: **the operating model
should be chosen to optimise for the boundaries
the CAO function will spend the most time
operating against**. The boundary that absorbs
the most CAO attention is usually CAO × CRO
or CAO × MRM in regulated industries;
CAO × product or CAO × engineering in
AI-native businesses; CAO × CISO where the
AI deployment is heavily enterprise-facing.
Design the model so that boundary is cleanest.

## 1.4 Hybrid is the common case

Real operating models are rarely pure. Most
mature programs end up with a hybrid: a core
hub-and-spoke pattern, with specific functions
operated centralised (evidence ledger, board
reporting, external regulator interface) and
specific decisions federated (routine impact
assessments, business-unit-specific control
tailoring, local tabletop exercises).

The hybrid is not a compromise; it is a
*deliberate structural choice* that places
each sub-function at the altitude where it
operates best. The discipline is naming the
hybrid explicitly in the function's charter
rather than drifting into it. A program whose
charter says "centralised" but which has
federated most of its routine work has a
documentation problem the first regulator who
reads the charter will notice.

The ISO/IEC 42001:2023 AI Management System
standard treats this explicitly: the standard
requires the organisation to define the
*scope* of the AIMS and the *roles,
responsibilities and authorities* within it
(§4.3, §5.3). An AIMS that documents its
operating model as pure centralised while
operating hybrid is not conforming — the
scope and the role definitions are
inconsistent with the as-operated reality.
See resources.md for the primary standard.

## 1.5 What if you inherited the model

Most CAOs inherit an operating model rather
than choosing one. Three postures:

### 1.5.1 Inherited model fits

If the inherited model is a reasonable fit for
the organisation, the posture is **operate
within it**. Spend year 1 (Chapter 2) making
it work rather than agitating for change.
Boards and CEOs are rightly skeptical of new
executives whose first move is to restructure.

### 1.5.2 Inherited model doesn't fit

If the inherited model doesn't fit — the
business is federated and the governance is
centralised, or vice versa — the posture is
**operate within it for now, propose change
deliberately once the program is mature
enough to absorb the transition**. The
transition itself is costly; attempting it in
year 1 or year 2 is rarely the right move
regardless of how obvious the case seems.

A specific signal that an operating-model
change is ripe: when the inherited model is
producing *recurring* friction at the same
boundary quarter after quarter, surfacing in
multiple AI Risk Council sessions, and when
the CAO function has enough operating history
to credibly diagnose the cause and defend
the restructure proposal to the board. That
is a year-3 move at the earliest for most
programs.

### 1.5.3 No model declared

If no operating model has been declared — the
CAO walks in and finds a function with
ambiguous reporting lines, undefined authority,
and no governance charter — the posture is to
**declare one deliberately in year 1**, as
part of the governance machinery §2.1 names
as a year-1 deliverable. Operating without a
declared model is drift; drift becomes the
model by default. See
[`mod-101`](../mod-101-foundations/README.md)
Chapter 6 for the declaration pattern.

## 1.6 Changing the model is expensive

Changing the operating model is among the most
expensive things a CAO can do. The cost is
not primarily in the restructure paperwork; it
is in the *reset* every boundary partner has
to perform.

- The CRO re-learns who to call on what cases.
- The CCO re-learns which standards apply where.
- The CISO re-learns the trust-architecture
  partnership interface.
- The business units re-learn how to engage.
- The AI Risk Council and AI Review Board
  reset their membership, chairmanship, and
  decision domains.

Each of these resets takes weeks to months of
practitioner time across the organisation. A
model change proposed and executed in a
single year will consume most of that year's
discretionary capacity across the governance
network. If the model change does not
materially improve the program's effectiveness,
the capacity was wasted. If it does, the
year of lost capacity was the price. CAOs
proposing model changes should be able to
make the case explicitly in those terms.

## Summary

- The operating model determines downstream
  properties the program lives with for years:
  who decides, where the evidence lives, how
  the function scales, where it is brittle,
  how regulators see it, how boundary
  partners engage.
- The choice is contextual — organisation
  size, regulatory landscape, existing risk
  architecture, AI maturity, executive
  sponsorship pattern. No single factor
  decides it.
- Downstream across the track: hub-and-spoke
  tends to serve the CAO × MRM split;
  centralised tends to serve the CAO × CISO
  boundary and the evidence substrate;
  matched models serve the CAO × Compliance
  boundary; the board interface is
  consolidated at the top regardless.
- Real models are usually hybrid. The ISO/IEC
  42001 AIMS discipline requires the hybrid
  to be documented explicitly rather than
  drifted into.
- Most CAOs inherit the model. If it fits,
  operate within it. If not, operate within
  it until the program can absorb a
  transition — year 3 at the earliest.
- Model changes are expensive — not in
  paperwork, but in the reset every boundary
  partner performs. Propose changes with that
  cost named explicitly.
