# Chapter 6 — Post-Incident Review

## Why this chapter exists

The post-incident review is the single artifact
that turns an incident into program improvement.
Without the review, each incident is a one-off
disruption that fades from institutional memory
within months. With it, each incident becomes a
specific input to the GOVERN loop from
[`mod-103`](../mod-103-ai-risk-frameworks/README.md)
§6 — monitoring thresholds adjusted, policies
revised, procedures amended, controls added,
training updated.

The review has two audiences and must serve both.
The **internal** audience is the response team,
the governance bodies, and the executives who
need to understand what happened and what the
program is doing about it. The **external**
audience — regulators, auditors, in some cases
the public — reads the review as evidence that
the firm has a working incident-learning
discipline. A review that satisfies the internal
audience but not the external one is a review
that will be contested the first time a
regulator opens it; a review that satisfies the
external audience but not the internal one does
not actually improve the program.

The chapter teaches the structure that serves
both.

## 6.1 Properties of a working review

A review worth the name has six properties.

- **Conducted on a defined timeline.** Within
  30 days of incident closure for ordinary
  cases; faster — within 10 business days —
  for material incidents and for incidents
  with external visibility. Reviews conducted
  60+ days after closure drift into
  reconstruction; witnesses forget, context
  decays, and the review relies on narrative
  rather than contemporaneous record.
- **Includes everyone materially involved.** The
  response team, the model or system owner,
  the single named lead, GC, the compliance
  operations lead, the AI Risk Council chair
  (or delegate), representatives of affected
  business units, and anyone whose actions
  are material to the causal chain. People
  with substantive input who are not invited
  perceive the review as closed; the review
  loses the information they would have
  contributed.
- **Led by someone not in the chain of
  responsibility.** The AI Risk Lead can
  lead the review of an incident their
  function did not operationally lead;
  internal audit can lead reviews of
  AI-program incidents; for the most complex
  cases an external reviewer leads with
  internal support. The review lead's
  independence from the response is what
  lets them produce findings that criticise
  the response if criticism is warranted.
- **Produces a written report.** Signed,
  version-controlled, added to the audit
  ledger per
  [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md).
  A review that produced only a verbal
  readout did not actually feed the program;
  the artifact is what carries forward.
- **Follows a standard template.** Programs
  with ad-hoc report structures discover that
  external reviewers notice the structural
  inconsistency across reports and infer the
  program is not treating review as a
  discipline. A standard template signals
  discipline and makes the review faster to
  produce under pressure. §6.6 specifies the
  template this module adopts.
- **Routes recommendations into the program's
  improvement backlog.** The review does not
  end at the report; the recommendations enter
  the improvement backlog with named owners
  and timelines, and the review tracks them to
  closure (§6.3 and §6.5).

Reviews missing any of the six have specific
failure modes the chapter can anticipate and that
external reviewers will spot.

## 6.2 The "what worked" discipline

A common failure mode: the review focuses only on
what went wrong. Reviews that produce only
criticism develop two problems.

- **Defensive response teams.** The response
  team learns that review produces only
  negative findings about their decisions.
  Next time an incident arises, they slow
  down — defending their decisions in the
  moment, documenting more exhaustively,
  reaching for consensus rather than making
  calls. The response slows measurably.
- **Lost signal on what to reinforce.** The
  response team made some decisions well.
  Which decisions? The first responder's
  quick classification; the on-call's good
  judgement on containment; GC's fast
  notification authorisation; the model
  owner's willingness to accept the pause.
  These are specific skills the program
  wants to reinforce. A review that does not
  name them does not reinforce them.

A working review has an explicit **what worked**
section. The section identifies specific
decisions, actions, and behaviours that
contributed positively to the response. Each
item is attributed to a role (not necessarily
named individuals, though sometimes
appropriate) and tied to a specific moment in
the timeline.

A review with no "what worked" findings is
suspicious. Either the response was uniformly
bad (unlikely for a well-staffed team) or the
review is pretending to be more negative than
warranted (to look rigorous). Both are failure
modes.

## 6.3 Recommendation discipline

Recommendations are where review becomes
improvement. The failure mode: reviews that
produce vague recommendations that do not become
specific changes.

A working recommendation has five properties.

- **Specific.** "Add a monitoring alert when
  the demographic-parity gap exceeds 2
  percentage points at any single site, with
  a page to the on-call AI Risk Lead" is
  specific. "Improve monitoring" is not.
- **Assigned.** A named role is accountable
  for the recommendation's implementation.
  Named roles, not functions or committees.
  "AI Risk Lead" is a role; "the CAO
  function" is a function.
- **Scheduled.** A specific timeline. "Within
  60 days of review publication" is a
  timeline. "As soon as practicable" is not.
- **Tracked.** The recommendation enters the
  program improvement backlog with status
  updates at each governance cycle (quarterly
  at minimum; monthly for high-urgency
  cases).
- **Closed with evidence.** When the
  recommendation is implemented, the closure
  record includes evidence — the code
  change, the policy revision, the training
  completion — not just a status change.

Reviews that produce five vague recommendations
without this discipline produce five
unimplemented recommendations by the time the
next review happens. Programs that accumulate
unimplemented recommendations fail regulator
inquiry on the question "what did you do with
your post-incident recommendations?"

## 6.4 Residual acceptance is a legitimate recommendation

A specific and often missed category:
**acceptance of a documented residual** is
sometimes the correct recommendation.

Not every finding can or should be remediated.
Some systemic conditions are inherent to the
program (statistical power for small subgroups
cannot be arbitrarily improved; a particular
vendor dependency may be irreducible without
redoing the architecture). The honest finding
may be that the condition is accepted at the
governance level, with explicit treatment of
the residual.

A residual acceptance is a specific kind of
recommendation. It specifies:

- The **finding** being accepted.
- The **remediation options considered** and
  the reasoning for not adopting them.
- The **residual risk** being accepted,
  quantified where possible.
- The **compensating controls** that bound
  the residual.
- The **accepting authority** — typically the
  governance body with the authority to
  accept risk at this level (AI Risk Council
  for program-scale residuals, Board Risk
  Committee for enterprise-scale).
- The **review cadence** for the acceptance
  — residual acceptances are not permanent;
  they are reviewed annually and may be
  revised as conditions change.

Programs that only recommend remediation —
treating every finding as something to be
fixed — produce review culture that is not
credible with experienced regulators. Mature
regulators expect to see residual acceptances;
their absence suggests the program is not
honestly engaging with its risk picture.
[`mod-103`](../mod-103-ai-risk-frameworks/README.md)
Ex-04 (treatment plans) connects directly: the
residual-acceptance discipline is the same at
the incident-review scale and the enterprise-
risk-treatment scale.

## 6.5 Routing into the GOVERN loop

The post-incident review's recommendations are
not a standalone list. They enter the program's
improvement backlog alongside recommendations
from audits, regulator findings, independent
validations, and periodic reviews. The
improvement backlog is operated per
[`mod-103`](../mod-103-ai-risk-frameworks/README.md)
§6 as the GOVERN loop's continuous practice.

Three operational mechanics the routing
requires:

- **The backlog has a canonical form.** Each
  item has an owner, a timeline, a status,
  evidence of completion. The post-incident
  review's recommendations enter in that
  form.
- **The backlog has a review cadence.** The
  AI Risk Council reviews the backlog at
  each regular meeting (monthly or
  quarterly). Items that have slipped are
  escalated.
- **The backlog closures feed the next
  review.** When the next incident of
  similar class arrives, the response team
  checks whether earlier recommendations
  from similar incidents were implemented;
  recurring incidents from unimplemented
  recommendations are a specific finding in
  the current review.

A program with a working loop produces reviews
that build on each other. A program without
produces reviews that read as if each were the
first; the pattern of unimplemented
recommendations is itself the finding external
reviewers will surface.

## 6.6 The template

A standard template this module recommends.
Each section has a specific purpose; sections
can be expanded but not omitted.

### Section 1 — Incident summary

- One-paragraph description of what happened.
- Classification per
  [`mod-107`](../mod-107-ai-security/README.md)
  §6.
- Materiality determination (per the firm's
  materiality thresholds).
- Affected scope — customers, data, systems,
  period.

### Section 2 — Response summary

- Timeline (from investigation per Chapter 5
  §5.6).
- Key decisions and the deciding roles.
- Containment posture history (per Chapter 3).
- Notifications made (per Chapter 4), with
  recipient, timeline, format, and content
  reference.

### Section 3 — What worked

- At least two specific decisions / actions /
  behaviours that contributed positively (per
  §6.2).
- Attribution to roles.
- Timeline reference.

### Section 4 — What didn't work

- Substantive findings with evidence.
- Attribution to systemic causes, not just
  proximate.
- Honest about the uncomfortable findings.

### Section 5 — Root causes

- Proximate causes.
- Systemic causes (per Chapter 5 §5.3).
- The causal tree from Chapter 5 §5.2.
- Known unknowns from Chapter 5 §5.7.

### Section 6 — Recommendations

- Each with the five properties from §6.3.
- Including at least one residual acceptance
  per §6.4 where applicable (and reasoning if
  no residual accepted).

### Section 7 — Recommendation status

- At publication: all recommendations are open.
- Updated at each governance review cycle.
- Final status when all recommendations are
  closed or formally accepted as residual.

### Section 8 — Sign-off

- Review lead signature.
- AI Risk Lead acknowledgment.
- AI Risk Council acknowledgment.
- For material incidents: Board Risk Committee
  or Audit Committee acknowledgment.
- Date and version.

The template is itself a controlled document
(per [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)):
versioned, signed by the authoring heads of
function, reviewed quarterly for drift.

Exercise 04 of this module asks the learner to
author a working template and apply it to a
specific incident.

## 6.7 How reviews survive external scrutiny

A specific test the chapter can set: when a
regulator or external auditor opens the review,
what are they looking for?

Five things, in roughly this order:

1. **A time-stamped record of what happened.**
   Not a reconstruction. The regulator wants
   the audit-ledger entries that back the
   timeline.
2. **Honest engagement with what went wrong.**
   The regulator reads a review that is
   defensive and concludes the program is
   defensive. The regulator reads a review
   that names specific failings — with
   remediation underway — and concludes the
   program is operating.
3. **A causal analysis that reaches
   organisational causes.** Reviews that stop
   at proximate causes read as superficial.
4. **Recommendations that are specific,
   assigned, and tracked.** With status.
   Status matters as much as the
   recommendations themselves.
5. **A pattern across reviews.** The current
   review in context of earlier reviews.
   Reviews that would stand alone cannot
   survive a regulator who has read the last
   three; patterns of unimplemented
   recommendations become findings in their
   own right.

A review built per §6.1–§6.6 passes all five.
Programs with a running history of such reviews
have the strongest possible defence under
regulatory scrutiny — not that incidents did
not happen, but that each produced documented
improvement and the program is systematically
learning.

## 6.8 The review is not an audit

A boundary worth drawing: the review is a
response-team-plus-governance exercise. It is
*not* an audit. The firm's internal audit
function (and external audit where engaged) does
its own work on AI incidents, with its own
scope, standards, and reporting lines.

The review and the audit interact but do not
substitute:

- The review is **faster** than the audit.
  Days-to-weeks, not weeks-to-months.
- The review is **owned by the operating line**
  (second-line in the three-lines-of-defence
  model per
  [`mod-101`](../mod-101-foundations/README.md)
  §3). The audit is owned by the third line.
- The review's purpose is **program improvement**.
  The audit's purpose is **assurance** about the
  program's design and operation.
- The review's audience is primarily **internal**
  (with external review as a secondary
  audience). The audit's audience is primarily
  **external** (with internal use as a secondary
  audience).

Programs that treat the review as a lightweight
audit tend to over-structure it (slowing down),
over-formalise it (defensive culture), and
under-use it (the operating line disengages).
Programs that treat the audit as a review tend
to under-structure it (poor assurance quality).
The distinction keeps each in its lane.

## Summary

- The post-incident review turns incidents into
  program improvement via the GOVERN loop. It
  has internal and external audiences and must
  serve both.
- Six properties of a working review: defined
  timeline (30 days ordinary, 10 business days
  material), inclusive participation,
  independent lead, written report, standard
  template, routes recommendations into the
  improvement backlog.
- The "what worked" discipline is explicit —
  reviews that only criticise produce
  defensive responders and lose signal on what
  to reinforce. A review with no positive
  findings is suspicious.
- Recommendations are specific, assigned,
  scheduled, tracked, closed with evidence.
  Vague recommendations become wallpaper.
- Residual acceptance is a legitimate
  recommendation. Programs that only
  recommend remediation are not credible with
  experienced regulators.
- Recommendations route into the GOVERN loop
  improvement backlog. The backlog has a
  review cadence; closures feed the next
  review.
- Template: incident summary, response
  summary, what worked, what didn't, root
  causes, recommendations, recommendation
  status, sign-off.
- External scrutiny checks five things:
  time-stamped record, honest engagement
  with failings, causal analysis reaching
  organisational causes, tracked
  recommendations, pattern across reviews.
- The review is not an audit. It is faster,
  owned by the second line, and oriented
  toward improvement; the audit is the
  third-line assurance exercise.
