# Chapter 5 — Investigation and Root-Cause Analysis

## Why this chapter exists

After the incident is contained and the first
notifications are out, the response moves into
investigation. This is the part of the response
that most often fails on its own terms. Not
because investigators are incompetent — they
rarely are — but because the shape of a good
investigation is counter-intuitive in two
specific ways.

First, the investigation that satisfies the
response team's natural curiosity (*what
happened?*) is not the same investigation that
feeds program improvement (*why did the program
let this happen?*). The former ends at the
proximate cause and feels complete; the latter
pushes past the proximate cause to the systemic
conditions, and feels unfinished at the point
where the former would have stopped.

Second, the investigation that identifies who did
what is the one most prone to produce defensive
witnesses and shallow findings. Blame-adjacent
investigation produces post-incident reviews that
read well internally and crumble under external
scrutiny — because external reviewers can see
when the investigation stopped before it reached
the uncomfortable systemic observation.

This chapter teaches the discipline that produces
the second kind of investigation: deep enough to
drive program improvement, structured enough to
survive external review, deliberate enough about
blame to keep witnesses contributing instead of
defending.

## 5.1 Properties of a working investigation

A working investigation has five properties.
Investigations missing any of them typically
produce reviews that do not survive examination.

- **Named lead.** The same single-named-lead
  pattern as the rest of the response. One
  person is accountable for the investigation's
  completeness; others contribute. For
  AI-program incidents the lead is typically
  the AI Risk Lead or a delegate; for complex
  cases the lead can be an internal auditor
  not in the chain of operational
  responsibility.
- **Defined scope.** The initial scope is
  named — the specific system, the specific
  period, the specific behaviours or outputs
  under review. Scope can and should expand as
  evidence warrants, but each expansion is a
  recorded decision. Investigations that drift
  without recorded scope changes produce
  reports that cannot be defended against the
  question "why did you look at this but not
  that?"
- **Evidence-producing as it proceeds.**
  Investigation findings land in the audit
  ledger (per [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md))
  as they are established, not at the end.
  Weekly working-paper entries record the
  current fact pattern, the current open
  questions, the current working hypotheses.
  Programs that batch investigation evidence
  for the final report lose the time-stamped
  chain of custody that the report rests on.
- **Separates facts from inferences.** What is
  established by evidence vs. what is
  hypothesised. The report structure (Chapter
  6) carries this separation forward.
  Investigations that blur the distinction
  produce reports in which contested inferences
  look like settled facts, and the first
  external reviewer who notices undermines the
  whole report.
- **Names what is not yet known.** Honest about
  remaining uncertainty. The report concludes
  with an explicit "not yet established" section
  rather than overclaiming completeness. The
  external reviewer who finds an unaddressed
  question not acknowledged in the report
  concludes the investigation did not notice;
  the one who finds the same question in the
  "not yet established" section concludes the
  investigation was aware and had reasons.

The five properties combine. A named lead with
defined scope producing evidence as the
investigation proceeds and separating fact from
inference and naming the unknown — this is a
working investigation. Any one missing is a
specific failure the chapter can anticipate.

## 5.2 The five-whys discipline

The classical root-cause technique: ask "why?"
five times, each time digging deeper. The
discipline sounds mechanical but has a specific
purpose — it forces the investigation past the
proximate cause into the systemic conditions.

A worked example on an AI incident:

- *Why did the model misclassify this
  customer?* The confidence score was 0.47
  — below the 0.5 threshold — but the
  decision workflow treated it as an approval.
- *Why did the workflow treat 0.47 as
  approval?* The threshold was 0.4 in the
  deployed configuration, not 0.5 as the
  model documentation specified.
- *Why was the deployed threshold different
  from the documentation?* A production
  tuning adjustment two months ago lowered
  the threshold to increase approvals,
  without updating the documentation.
- *Why was the adjustment made without
  documentation update?* The threshold-tuning
  procedure in production does not include a
  documentation step. The documentation is
  updated only on model-retraining releases,
  not on operational tuning.
- *Why doesn't the procedure require
  documentation updates on operational
  tuning?* The procedure was authored before
  threshold-tuning was a routine production
  activity. The procedure's assumptions no
  longer match operational practice.

The chain ends at a procedural / organisational
cause: a procedure authored under one set of
operational assumptions is now being used under a
different set. That is the right level for
program improvement — a specific procedure can be
revised, with named owners and a specific change,
and the post-incident recommendations can be
tracked to closure (Chapter 6 §6.3).

Three practical cautions on the five-whys:

- **"Five" is a convention, not a limit.** The
  real signal is reaching a level where the
  cause is organisational — a policy, a
  procedure, a structural choice. For some
  incidents that is three whys; for others
  it is seven. The discipline is "ask until
  you reach the organisational layer," not
  "stop at five."
- **The chain can fork.** Many incidents have
  multiple contributing causes. The
  investigation produces a *tree* of why-chains,
  not a line. The tree is the right artifact
  for the post-incident review.
- **The chain can be contested.** Different
  investigators tracing the same incident can
  produce different chains. The investigation
  convenes the response team to walk the chain
  together, record disagreements, and resolve
  them with evidence where possible. Chains
  that one investigator produced in isolation
  are brittle under external review.

## 5.3 Proximate cause vs. systemic cause

A specific failure mode worth isolating:
**stopping the investigation at the proximate
cause**. "The model misclassified because the
input distribution shifted" is proximate; "the
program did not detect the distribution shift
because its monitoring was configured for one
distributional metric and the shift was along
another dimension" is systemic.

The proximate cause explains the specific
incident. The systemic cause explains the class
of incidents the program is exposed to. Program
improvement is about the latter, not the former.

Three patterns of systemic cause that recur in
AI incidents:

- **Monitoring blind spot.** The incident
  occurred along a dimension the monitoring
  was not configured to detect. The systemic
  improvement extends the monitoring; the
  proximate improvement does nothing because
  the next incident will arrive along another
  blind spot.
- **Policy gap.** The policy did not address
  the specific decision the operator made; the
  operator chose per their best judgement; the
  judgement was reasonable in isolation and
  wrong in context. The systemic improvement
  closes the policy gap; the proximate
  improvement blames the operator and leaves
  the gap.
- **Vendor assumption.** The firm relied on a
  vendor-provided property (model behaviour,
  guardrail, SLA) that the vendor did not in
  fact guarantee at the level the firm
  depended on. The systemic improvement
  revisits vendor assumptions and either
  secures them contractually or adds internal
  compensating controls; the proximate
  improvement switches vendors and often
  encounters the same pattern at the new
  vendor.

Investigations that produce only proximate causes
produce post-incident reviews that recommend
narrow fixes and miss the structural issue. Six
months later, a different incident arrives in
the same class, and the review concludes "we
didn't catch the structural issue last time
either." Programs that build the pattern of
missing systemic causes develop a specific
regulatory finding — the same class of incident
recurring without program improvement.

## 5.4 The NTSB discipline: investigate causes, not blame

Investigations have a political dimension that
has to be addressed in advance or it will shape
the investigation in ways no one intends.
Identifying "the person responsible" is the
political temptation; it is almost always
counterproductive to the investigation's actual
purpose.

Three specific failure modes blame-adjacent
investigation produces:

- **Defensive witnesses.** When investigation
  participants perceive that someone will be
  held responsible, their contributions become
  self-protective. They answer the questions
  asked without volunteering the context that
  reveals the systemic story. The
  investigation hears less than it would
  under a less adversarial posture.
- **Shallow findings.** Blame-focused
  investigation stops at the proximate cause
  because the proximate cause supplies a
  nameable person. The systemic layer is left
  unexamined because examining it would move
  responsibility from the named person to the
  program.
- **Punitive post-incident actions that do not
  improve the program.** The person named is
  removed or disciplined; the system that
  produced them making the decision they made
  is not touched; the next similar incident
  arrives on schedule.

The National Transportation Safety Board (NTSB)
has worked out the counter-pattern over decades
of aviation safety investigation. The pattern:

- **The investigation produces facts and
  causal analysis.** The report says what
  happened, including who did what, with the
  purpose of understanding — not with the
  purpose of allocating consequences.
- **Consequences for individuals are a separate
  process.** Owned by HR, management, or (in
  the aviation case) separate regulatory
  action. The safety investigation does not
  recommend consequences.
- **Reporting is encouraged.** Witnesses who
  volunteer information gain regulatory
  protection; the investigation gets fuller
  information; the aggregate safety signal
  improves.

The AI IR adaptation: the investigation names
what happened and why, including the actions of
specific people where those actions are
material to the chain. Consequences for those
individuals are a separate process owned by HR
and management, not by the response team. The
investigation lead does not make
recommendations about individual consequences.
If HR or management need the investigation's
findings to inform a separate process, they can
request them — but the investigation's purpose
is understanding, not allocation.

This posture is harder to maintain than it
sounds. Senior stakeholders will ask who is
responsible; business leaders will press for a
named person; the media (if the incident is
public) will frame the story in blame terms.
The CAO function's discipline is to deliver the
investigation on its own terms and let the
separate processes operate separately.

## 5.5 The investigation team

Who conducts the investigation depends on the
classification and the complexity.

For straightforward incidents, the response
team's investigation sub-team can conduct the
investigation directly: the AI Risk Lead or
delegate as investigation lead, model owner as
contributor, SOC analyst as contributor for
security dimensions, GC as advisor for
privilege and liability.

For complex incidents, three additional roles
are warranted:

- **Internal audit** as investigation lead
  rather than contributor. Internal audit is
  outside the chain of operational
  responsibility; they can investigate
  without defending prior decisions. Audit
  committee may require internal audit
  leadership for incidents of certain
  severity.
- **External investigators** for incidents with
  substantial legal exposure, regulatory
  attention, or public visibility. External
  investigators can bring forensic
  specialisation (digital forensics,
  model-forensics, data-provenance analysis)
  the firm does not have in-house. External
  investigators also create privilege clarity
  for the resulting report.
- **Independent AI validators** for incidents
  where the AI system's behaviour is itself
  under investigation. The model-validation
  function from [`mod-104`](../mod-104-model-risk-management/README.md)
  may lead or contribute. External AI
  auditors from the
  [`mod-106`](../mod-106-trust-architecture/README.md)
  trust-architecture ecosystem may be engaged.

The investigation team is formed in the first
48 hours and does not change substantially after
that. Mid-investigation team changes produce
discontinuities in the record and raise questions
in external review.

## 5.6 Timeline reconstruction

A specific deliverable from investigation: a
timeline of the incident. The timeline is the
backbone of the post-incident review report
(Chapter 6).

A working timeline has three attributes:

- **Time-stamped.** Each event has a specific
  time. "Around mid-morning" is not a
  time-stamp; "09:34 local, per the SOC
  ticket" is.
- **Sourced.** Each event has a provenance —
  the audit-ledger entry, the system log, the
  email, the call-recording. The source is
  the primary record, not someone's
  recollection.
- **Classified.** Each event is classified as
  *detection*, *decision*, *action*, or
  *external*. The classification lets the
  reader see where the decisions were, which
  actions followed, and where external events
  intersected the response.

Timeline reconstruction from memory is unreliable
within days of an incident and useless within
weeks. Programs that depend on contemporaneous
audit-ledger capture (per Chapter 2 §2.6) can
produce timelines; programs that depend on
reconstruction cannot. This is one of the places
where the mod-108 evidence discipline earns its
cost.

## 5.7 What investigation produces

The investigation hands five artifacts to the
post-incident review:

- A **timeline** reconstructed from the ledger
  and from investigation evidence.
- A **causal tree** (per §5.2) with the
  branches reaching the organisational layer.
- A **fact set** — what has been established
  by evidence, with sources.
- An **inference set** — what has been
  concluded from the facts, with the
  reasoning.
- An **unknown set** — what has not been
  established, with the reasoning for why not
  (and whether additional investigation is
  warranted or whether the question is
  intrinsically unanswerable).

These five artifacts feed Chapter 6's post-
incident review structure directly. An
investigation that produces all five hands the
review a tractable task; one that produces fewer
forces the review to do investigative work on top
of its own task.

## Summary

- Investigation produces understanding deep enough
  to drive program improvement, structured enough
  to survive external review, deliberate enough
  about blame to keep witnesses contributing.
- Five properties of a working investigation:
  named lead, defined scope, evidence-producing
  as it proceeds, separates facts from
  inferences, names what is not yet known.
- The five-whys discipline pushes past the
  proximate cause to the organisational layer.
  "Five" is a convention, not a limit; the chain
  can fork and can be contested; the signal is
  reaching the organisational cause.
- Three recurring systemic causes in AI
  incidents: monitoring blind spot, policy gap,
  vendor assumption. Investigations that stop at
  the proximate cause miss these and produce
  reviews that recommend narrow fixes.
- The NTSB discipline separates investigation
  from blame allocation. The investigation
  produces facts and causal analysis;
  consequences for individuals are a separate
  process owned by HR and management.
  Blame-adjacent investigation produces
  defensive witnesses, shallow findings, and
  punitive actions that do not improve the
  program.
- The investigation team is formed in the first
  48 hours and does not change substantially
  after. Internal audit lead for complex cases;
  external investigators for high-exposure
  cases; independent validators for
  AI-behavioural investigations.
- Timeline reconstruction depends on
  contemporaneous audit-ledger capture.
  Each event is time-stamped, sourced, and
  classified (detection / decision / action /
  external).
- The investigation hands the post-incident
  review five artifacts: timeline, causal tree,
  fact set, inference set, unknown set.
