# Chapter 3 — The Quarterly Board Report

## Why this chapter exists

The quarterly board report is the operational
artifact that connects the AI program to the
board on an ongoing basis. It is the document
where the over-reporting failure mode from
Chapter 1 either lives or dies, and the
document against which the board forms its
view of whether the CAO function is being run
competently in the quarters when nothing
material happens.

That last point matters. In the quarters when
nothing material happens, the quality of the
report is the *only* thing the board sees from
the CAO function. A report that is thin,
boilerplate, or defensive signals a function
that has nothing to say — which, over several
quarters, becomes a function that is treated
as having nothing to say. A report that is
long, dense, and uneditable signals a function
that cannot discipline its own output. The
sweet spot — three to five pages, honest,
specific, actionable — signals a function that
understands its audience.

This chapter builds that sweet spot: the
structure, the asks discipline, the honesty
discipline, and the off-cycle update patterns
that complete it.

## 3.1 The structure that works

A working quarterly board report is **three to
five pages** (plus appendices on request) and
has six sections:

### 3.1.1 Risk posture summary (≤ ½ page)

An aggregate view of the program by risk
appetite category (Chapter 2), with a
change-from-last-quarter indicator for each.
Not metrics in detail — the posture.

The visual pattern most boards find readable:

| Category | Current | Direction | Note |
|---|---|---|---|
| Model performance | Within appetite | → | Routine |
| Bias & fairness | Approaching boundary | ↑ | Site H-12 under remediation |
| Transparency & XAI | Within appetite | → | Reg B review clean |
| Privacy & data | Within appetite | → | Routine |
| Security | Within appetite | → | Routine |
| Vendor & third-party | Approaching boundary | ↑ | LLM vendor change pending |
| Market & conduct | Within appetite | → | Routine |
| Strategic & reputational | Within appetite | → | Routine |

Three states — within, approaching, outside —
and three directions — improving, stable,
worsening. Boards that get used to this
pattern can read it in under a minute.

### 3.1.2 Material changes (≤ ½ page)

What has changed in the trailing quarter that
the board should know. Material incidents
closed; material program decisions made under
delegated authority; material organisational
changes that affected the program; material
regulatory movement that reshaped the risk
landscape.

Each item: one line of what happened, one line
of how the program responded, one line of
disposition. Not the full story — the
disposition.

### 3.1.3 Material exceptions (≤ 1 page)

Cases outside risk appetite right now, with
response and timeline. For each exception, in
3-5 lines:

- **The fact.** What is outside appetite, in
  which category, by how much.
- **The context.** How it got there (new
  deployment, drift, external event).
- **The response.** What the program is doing
  about it, and under whose lead.
- **The timeline.** When the program expects
  to be back within appetite.
- **The residual.** The risk the board is
  implicitly accepting while the response
  runs.

The exceptions section is the section where
boards most often ask follow-up questions.
Pre-brief the Board Risk Committee chair on
exceptions that are likely to attract
questions.

### 3.1.4 Material decisions pending (≤ ½ page)

What the board needs to decide, ratify, or be
positioned to decide in the next cycle. For
each: what the decision is, what the
recommendation is, what the implications are
of either direction, and when the decision is
due.

Decisions range from narrow (ratification of a
revised bias-monitoring threshold under the
appetite statement's annual review clause) to
broad (approval of a material new AI
operating-model investment).

### 3.1.5 Material changes ahead (≤ ½ page)

Foreseeable change the board should be aware
of — regulatory, market, organisational.
Short. Not a horizon scan — a *selection* of
the material items from the horizon scan the
AI Risk Council maintains.

Pattern: three bullets, one line each,
labelled by category (regulatory / market /
organisational).

### 3.1.6 Asks (≤ ½ page)

What the program needs from the board. §3.2
treats this as its own discipline because the
asks section is the one most commonly
under-populated.

### 3.1.7 Appendices (any length, reference only)

Reference material the board does not need to
read but may consult. Typical appendices:

- Detailed metrics by category.
- Full incident register (summarised in §3.1.2
  if material).
- Vendor register (summarised in §3.1.1 if
  concentration is noteworthy).
- Gap analyses (from [`mod-109`](../mod-109-compliance-operations/README.md)
  and [`mod-110`](../mod-110-incident-response/README.md)).
- Portfolio P&L / ROI appendix (Chapter 7
  builds this).

Appendices exist for reference, not for
reading. They should be internally searchable
(table of contents at the front) so a director
who wants to look something up can.

## 3.2 The asks discipline

The most under-used section of most CAO board
reports is **Asks**. A working CAO leaves the
board meeting having received a specific
answer to a specific question.

A board report without asks signals one of two
things:

- The CAO believes the program needs nothing
  from the board (rarely true).
- The CAO has not asked clearly (commonly
  true).

The discipline: **every quarterly report has
at least one ask**. The ask might be small
(ratification of an updated bias-monitoring
threshold under the appetite statement's
annual review clause) or large (approval of a
new operating-model investment). Boards need
to practice being asked things; if the CAO
never asks, the board's reflex when an ask
*does* come is "why now?"

Three categories of ask that routinely belong
in a quarterly report:

- **Ratifications.** Decisions already made
  under delegated authority that the board
  should ratify for the audit trail. Example:
  a new threshold adopted by the AI Risk
  Council under the appetite statement's
  §2.3.4 escalation process.
- **Judgments.** Decisions the board is being
  asked to make with the CAO's recommendation.
  Example: approval of a material new vendor
  concentration that crosses the vendor-and-
  third-party appetite threshold.
- **Resourcing.** Investments the program
  needs the board's view on. Example:
  endorsement of a year-2 operating-model
  expansion ([`mod-112`](../mod-112-cao-operating-model/README.md))
  that materially increases headcount in the
  CAO function.

The ask should be **specific**. A board can
act on *"Ratify the revised bias-monitoring
threshold for Tier-1 systems from 5 pp to 4
pp, effective Q3, as recommended by the AI
Risk Council in its 2026-02-14 session"*. A
board cannot act on *"Please consider our
monitoring posture."*

## 3.3 The honesty discipline

The single biggest failure of board reports
is softening the bad news. A report that
systematically presents the program as healthy
when it is struggling produces a board that
discovers reality from external sources — a
regulator, a peer institution, a media
incident. That discovery is much more
damaging than the originally bad news would
have been.

Three patterns to avoid:

### 3.3.1 Euphemism

*"The program experienced an elevated
engagement with the state insurance
regulator"* is a sentence that tries to not
say that the regulator opened an inquiry.
Boards read euphemism; they discount the rest
of the report. The sentence is *"The state
insurance regulator opened an inquiry on
2026-03-14; our response is X and we expect
disposition by Y."*

### 3.3.2 Burying

A material exception at the top of §3.1.3
reads differently from the same exception at
the bottom of Appendix F. The regulator or
auditor who later finds that the material
item was present-but-buried has a specific
finding to make. Burying material items is
anti-insurance — it fails at exactly the moment
it was supposed to help.

### 3.3.3 Softening the ask

The ask that reads *"The program would
welcome board input on monitoring posture"*
is an ask the board can decline without
engaging. Soft asks produce soft responses.
The ask that reads *"We request the board
ratify the revised threshold"* is an ask the
board must respond to.

The discipline positive: when the program is
struggling, say so specifically. Boards are
professional audiences; they expect bad news
to surface and they respect the executive who
delivers it honestly. The CAO who delivers bad
news honestly builds the credibility that
makes the harder asks landable later.

## 3.4 Change-from-last-quarter: the quiet discipline

The *change* column in the risk posture
summary (§3.1.1) is the section boards look at
most carefully. It is also the section easiest
to over-smooth — reporting "stable" when the
underlying posture is quietly worsening is a
pattern that catches up with the program
across two or three cycles.

A test for whether the change column is being
reported honestly: does the direction indicator
*ever* read "worsening"? Programs where every
category is always stable or improving are
either in an unusually benign environment or
are not reporting honestly. Over a full year,
some categories *will* worsen; the quarterly
report should reflect that when it happens.

Related: the "approaching boundary" state in
the current column. A program whose categories
only ever read "within appetite" or "outside
appetite" has probably skipped the
intermediate state. "Approaching" is the state
in which the board can usefully exercise
oversight *before* the item becomes a material
exception. Reports that elide it miss the
window where oversight is most useful.

## 3.5 The cadence and the off-cycle update

Quarterly is the standard cadence for board
reporting. But material incidents (per
[`mod-110`](../mod-110-incident-response/README.md))
and material decisions in flight may require
**off-cycle updates**. Four patterns:

### 3.5.1 Board Risk Committee chair briefings

Brief the chair when something material is
happening between meetings; let the chair
decide whether to convene the committee early.
The chair is the right first stop for most
off-cycle matter — the chair has standing to
decide whether to escalate to the full board,
whether to convene an off-cycle meeting, or
whether to hold for the next regular cycle.

### 3.5.2 Executive-session updates

Updates to a smaller body (Audit Committee or
Board Risk Committee) without going to the
full board. Appropriate when the matter is
material enough to require board-level
awareness but not so material that it needs
full-board intervention.

### 3.5.3 Pre-meeting briefings

Brief the chair before the regular meeting on
items that will be discussed, especially items
likely to attract questions. Surprises at the
meeting are unwelcome; the chair who was
pre-briefed can shape the discussion
constructively, and the CAO who skipped the
pre-brief is signalling that the material was
not worth the chair's time.

### 3.5.4 Written off-cycle notes

A short written note to the committee (one
page) when something material has happened
but does not warrant convening. The note goes
on the record alongside the regular quarterly
reports and feeds the audit trail. For some
regulatory regimes (EU AI Act Art. 73,
material model events under SR 11-7, SEC
cybersecurity disclosure) the off-cycle written
note is the artifact that evidences board
awareness.

A CAO who **never** briefs off-cycle is
either not encountering material events or is
hiding them. Both are failure modes. Over a
year of operations, two or three off-cycle
briefings is a healthy pattern; zero is a
signal that something is being suppressed.

## 3.6 Integration with the incident flow

The quarterly report inherits material
incidents from the mod-110 flow:

- **Closed incidents** become entries in
  §3.1.2 (material changes) — one line summary
  with pointer to the post-incident review.
- **Open incidents** become entries in
  §3.1.3 (material exceptions) with the
  current response posture.
- **Incidents producing regulatory
  notifications** become entries in §3.1.5
  (material changes ahead) where the
  regulatory disposition is pending.
- **Incidents producing programmatic
  improvements** become entries in §3.1.4
  (material decisions pending) when the
  improvement requires board ratification.

The flow is one-way for most incidents — the
mod-110 post-incident review (PIR) is the
substantive artifact; the quarterly report
summarises for the board. For material
incidents (per Chapter 4's materiality
framework), the flow is two-way: the board
may ask for the full PIR, and the CAO
provides it as an appendix.

## 3.7 Integration with the compliance / audit cycle

The quarterly report inherits from the
compliance operations cycle ([`mod-109`](../mod-109-compliance-operations/README.md)):

- **Continuous-evidence findings** become
  inputs to the risk posture summary — if
  evidence is not available on a specific
  control for the quarter, the relevant
  category's posture reflects the gap.
- **Compliance gaps** become entries in
  §3.1.3 (material exceptions) if above
  materiality threshold.
- **Audit findings** become entries in
  §3.1.2 or §3.1.3 depending on remediation
  posture; the board sees internal audit
  findings separately through its direct
  access to the internal audit function
  (third line), but the CAO's view on
  AI-specific findings belongs in the
  quarterly report.

The CAO's quarterly report is not the same as
the internal audit's view, and the board
should see both. The CAO's view is first-line
/ second-line judgment ([`mod-101`](../mod-101-foundations/README.md)
§3); internal audit is third-line. The two
can diverge; when they do, the board benefits
from seeing both and the divergence.

## Summary

- The quarterly report has six sections —
  risk posture, material changes, material
  exceptions, material decisions pending,
  material changes ahead, asks — in three to
  five pages plus appendices.
- Every quarterly report has at least one
  ask. Asks are specific — they admit of a
  board response.
- Honesty discipline: no euphemism, no
  burying, no softening of asks. The change
  column should sometimes read "worsening";
  the current column should sometimes read
  "approaching boundary."
- Off-cycle updates are a standard discipline
  for material in-flight matter. Chair
  briefings, executive-session updates,
  pre-meeting briefings, written off-cycle
  notes. A CAO who never briefs off-cycle is
  either not encountering material events or
  is hiding them.
- The report integrates with the mod-110
  incident flow and the mod-109 compliance
  cycle. Material items flow into the
  quarterly structure; the full
  substantive artifact (PIR, audit finding)
  lives elsewhere and is referenced.
