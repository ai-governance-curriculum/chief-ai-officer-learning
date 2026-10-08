# Chapter 7 — Tabletop Exercises

## Why this chapter exists

A program's response capability is the composite
of its playbooks, its people, its tooling, its
boundary conventions, and its evidence
infrastructure. The playbooks look fine on paper.
The people have been trained. The tooling is in
place. The question nothing on paper answers is:
**will the composite work under pressure?**

Tabletop exercises are the practice that answers
that question without the cost of a real incident.
A well-run tabletop surfaces gaps the paper
review would never find — the containment decision
the lead cannot defend under time pressure, the
notification obligation the matrix was missing,
the coordination handoff that silently fails
between the CISO's call bridge and the CAO
function's. A badly-run tabletop produces a
good-looking report, a clean readout to the Audit
Committee, and no actual readiness improvement.

The chapter teaches the discipline that
distinguishes the two. The specific tabletops
this module's Ex-03 asks the learner to design
sit within that discipline.

## 7.1 What a tabletop actually tests

A tabletop is not a training exercise. Training
exists to transfer skills to new team members;
tabletops exist to test whether the composite
capability works. Three specific capabilities a
tabletop tests:

- **Decision-making under compressed time.**
  Can the single named lead make the four
  first-hour decisions (Chapter 2 §2.4) in
  the compressed window the exercise
  simulates? Not can they describe the
  decisions in the abstract — can they make
  them in the moment, under injected
  information, with incomplete facts?
- **Cross-functional coordination.** When the
  response team spans the CAO function, the
  CISO, GC, the model owner, communications,
  and compliance operations, do the
  handoffs work? Does the single-named-lead
  convention actually hold under pressure, or
  does ownership drift to the loudest voice?
- **Reaching the regulatory interface.** When
  the notification matrix (Chapter 4) comes
  into play, can the team consult it,
  classify correctly, and reach the external
  interface in the window the matrix
  specifies? Does the approval chain hold
  when the GC has to be reached at 02:00?

Programs that run tabletops without targeting
these specifically — tabletops that are more
briefing than exercise — produce a tabletop
report but do not test the capability. The
Audit Committee reads the report; the next real
incident reveals that the composite still has
the gaps the tabletop was supposed to find.

## 7.2 The six properties of a working tabletop

- **Based on a realistic scenario.** Modeled on
  a real incident pattern — a near-miss the
  firm had, a peer-institution public
  incident, a documented vendor incident, a
  pattern surfaced in regulatory sanction
  summaries. Invented scenarios without
  precedent in the industry produce
  responses that are not grounded.
- **Cross-functional in the roles it exercises.**
  Includes every role on the notification
  matrix's response path for the scenario.
  Tabletops that exercise only the CAO
  function's internal response miss the
  cross-functional seams that are the main
  source of failure.
- **Time-pressured.** Real incident timelines
  are compressed. Tabletop injects should be
  compressed too — not more than real
  (which would be artificial pressure) but
  not less than real (which would let the
  team work in a slower cadence than they
  would face).
- **Decision-forcing.** Each inject requires
  the response team to make a specific
  decision in real time. "Here is more
  information" without an attached decision
  is a briefing, not a tabletop.
- **Documented in real time.** Decisions,
  reasoning, and the exercise record are
  captured as the exercise proceeds. The
  tabletop's post-exercise review (§7.5)
  depends on contemporaneous record exactly
  as a real incident's review depends on
  the audit ledger.
- **Reviewed.** The tabletop produces its own
  post-exercise review with findings and
  recommendations that route into the
  program improvement backlog.

A tabletop missing any of these six is not doing
the work. External facilitators are useful but
not sufficient; a facilitator-led tabletop with
a soft scenario and no decision-forcing injects
is still ceremony.

## 7.3 The scenario-design discipline

Scenarios are the hardest part of a tabletop to
design well. Three failure modes to avoid:

- **The too-easy scenario.** The incident is
  one the team has rehearsed, one that falls
  cleanly into a single classification, one
  with a clear containment call. The team
  responds competently; the report shows a
  successful exercise; no gaps are found.
  The next real incident is nothing like the
  scenario.
- **The too-exotic scenario.** The incident is
  novel in ways that overwhelm the team's
  capability. The team flounders; the report
  shows apparent problems; the apparent
  problems were artifacts of the scenario
  design, not the capability under test.
- **The ambiguity-free scenario.** The scenario
  has one correct classification, one correct
  containment posture, one correct
  notification obligation. The team executes
  the right answers. Real incidents are
  rarely like this. A scenario without
  genuine ambiguity does not test the
  team's actual judgement.

A working scenario has three attributes:

- **Grounded in a real pattern.** The
  underlying mechanism is one that has
  actually occurred. Where possible, cite the
  precedent (a public post-mortem, a
  regulator action, a near-miss internal
  record).
- **Cross-cutting on at least one dimension.**
  Multi-system, multi-jurisdiction,
  cross-functional at the classification
  boundary. A single-dimension scenario
  tests the single dimension; the cross-
  functional seams need cross-cutting
  scenarios.
- **Containing at least one genuinely
  ambiguous decision.** A classification call
  that could reasonably go two ways; a
  containment posture that is defensible at
  either of two neighbouring levels; a
  notification obligation whose trigger is
  arguably met and arguably not. The
  ambiguity is where real tabletop learning
  happens.

The scenario's narrative is one page, written as
the facilitator will present it to the team. The
backstory the facilitator knows but does not
disclose (what actually caused the incident,
what the correct containment turns out to have
been, what the regulator ultimately expected) is
a separate document.

## 7.4 Injects and timing

Injects are the events the facilitator introduces
into the exercise over its run. A half-day
tabletop typically has 6–8 injects spread across
the simulated time window.

A worked example of inject pacing for a half-day
tabletop simulating 72 hours:

| Simulated time | Inject | Decision forced |
|---|---|---|
| T+0 | Initial detection via SOC alert | First-hour decisions (verify, classify, lead, containment) |
| T+1h | Customer complaints begin arriving via support | Classification revisit; customer-communication posture |
| T+2h | Vendor advisory arrives suggesting upstream issue | Vendor-dependency assessment |
| T+5h | Media inquiry via corporate comms | Public-communication decision (Chapter 8) |
| T+12h | Preliminary scope estimate: broader than first thought | Containment revisit; notification matrix revisit |
| T+24h | Hour-24 revisit meeting | Containment relax/tighten; notification go/no-go |
| T+48h | Regulator asks preliminary questions | External coordination; messaging consistency |
| T+72h | Independent researcher publishes partial finding | Public-communication revisit; disclosure timing |

Injects are *decision-forcing*, not informational.
Each one puts a specific decision in front of a
specific role on a specific clock.

The facilitator's job during injects is to
present, not to coach. The team is tested, not
trained. If the team misses a decision, the
facilitator notes it in the exercise record;
the review (§7.5) is where the miss gets
addressed.

## 7.5 Roles: who plays, who observes, who facilitates

A working tabletop has three role categories.

### 7.5.1 Players

The response team members who would be on the
real incident call. For a scenario spanning
cross-functional response, that typically
includes:

- The single named lead for the scenario's
  classification.
- The AI Risk Lead and / or CISO on-call.
- The relevant model or system owner.
- General Counsel.
- The communications lead.
- The compliance operations lead.
- A member of the AI Risk Council (chair or
  delegate).

For cross-LOB scenarios, representatives of the
affected business units join.

### 7.5.2 Observers

Observers are present to watch and learn but do
not drive the response. Typical observers:

- An Audit Committee member or delegate (for
  governance visibility — the exercise is a
  governance input).
- Internal audit (observing the response
  mechanics for subsequent assurance work).
- Representatives from functions downstream
  of the response (business continuity,
  investor relations, HR for severe cases).

Observers do not participate in the response.
They may ask clarifying questions in the hot-
wash (§7.6) but do not substantively direct
the exercise.

### 7.5.3 Facilitator

The facilitator drives the exercise. For a
first-time tabletop or a materially new
scenario, external facilitation is worth the
cost — an outside facilitator brings experience
across firms and does not have internal
political relationships that shape their
behaviour.

The facilitator's responsibilities:

- **Deliver injects on the schedule.** Not
  earlier (to give the team breathing room),
  not later (to let them finish a decision
  they are stuck on).
- **Maintain the time compression.** The
  tabletop's half-day represents 72 hours;
  the facilitator's clock enforces the
  compression.
- **Document decisions contemporaneously.**
  Decisions, deciders, timing, reasoning.
  The record feeds the review.
- **Hold the back-story.** The facilitator
  knows what actually caused the incident
  and what the "right" answers are; the
  team does not. The facilitator does not
  reveal this during the exercise.
- **Not participate substantively.** The
  facilitator does not suggest answers, does
  not warn the team of inject timing, does
  not coach.

Internal facilitation can work for routine
tabletops once the program has internalised the
discipline; external facilitation remains the
default for high-visibility or first-time
exercises.

## 7.6 Scoring and the post-exercise review

The exercise produces findings along four
dimensions. Each dimension gets a 1–5 score
with specific anchor points.

- **Decision quality.** Were the right
  decisions made for the information available?
  (Not whether the decisions matched the
  facilitator's back-story — whether they
  were defensible on the facts the team had.)
- **Decision timing.** Were the decisions made
  in the window the matrix / scenario
  required? First-hour decisions in the
  first hour; notification decisions by hour
  24 for 72-hour regimes; etc.
- **Coordination.** Did the cross-functional
  team coordinate effectively? Did handoffs
  work? Did the single-named-lead convention
  hold? Were decisions made by the lead with
  team input, not by consensus-drift?
- **Documentation.** Were decisions documented
  contemporaneously in the way a real
  incident would require? Programs that
  ignore the documentation dimension in
  tabletops produce real incidents whose
  responses do not survive audit.

Scoring is specific to the dimensions, not
aggregated into a composite "pass / fail." A
tabletop with decision-quality 4 and
documentation 2 reveals a specific gap; a
composite score of 3 obscures it.

### 7.6.1 The hot-wash

Thirty minutes immediately after the exercise.
The team walks through the exercise, the
facilitator shares the back-story, participants
name what went well and what did not. The
hot-wash captures first impressions while they
are fresh.

### 7.6.2 The written review

Within 10 business days of the exercise. Same
structure as the post-incident review
(Chapter 6): what happened, what worked, what
did not, root causes, recommendations, status.
Signed by the facilitator, the response team's
single named lead, the AI Risk Lead or CISO as
appropriate, the AI Risk Council chair.

The review routes recommendations into the same
improvement backlog as real incident reviews
(per Chapter 6 §6.5). A tabletop recommendation
without routing is wallpaper exactly as a
real-incident recommendation without routing is
wallpaper.

## 7.7 Cadence

A working program runs tabletops on three
cadences.

- **Quarterly** — the response team runs a
  tabletop in rotation across scenario
  types. Rotation across types matters:
  running the same bias-incident scenario
  every quarter teaches the team that
  specific scenario, not the general response
  pattern.
- **Annually** — broader participation. Audit
  Committee observer. External facilitator.
  Novel scenario design. The annual tabletop
  is a visible-governance event.
- **On-demand** — when a new incident type
  emerges. A peer-institution incident, a
  novel attack pattern, a regulatory change
  that creates new notification obligations.
  The on-demand tabletop is the forcing
  function that keeps the program's
  capability current with the environment.

Programs that run only annual tabletops
discover gaps during the real incident
between annuals. Programs that run only
quarterly tabletops in the same pattern
produce a team that is good at the quarterly
scenario and no better than paper-trained
on anything else.

## 7.8 Anti-patterns

Four common failure modes.

- **Performance art.** The tabletop produces
  a good-looking report with no real
  learning. Signs: no written review beyond
  a brief, no routing of findings into the
  improvement backlog, no changes in
  program practice between exercises.
- **Tabletop as training.** The exercise is
  used to train new team members rather
  than test the composite capability. The
  trainees do fine (because they are being
  trained); the real capability remains
  untested.
- **Same scenario repeatedly.** The team
  learns the scenario. The next scenario is
  something else. The team's capability on
  the scenario-they-learned looks
  reassuring; capability on anything else
  is unchanged.
- **No findings.** A tabletop that produces
  no substantive findings is either too
  easy or being conducted as performance.
  A working tabletop surfaces 2–4
  substantive findings; zero is suspicious,
  ten suggests the scenario was
  unrealistic.

A tabletop whose written review finds 2–4
substantive issues and routes them into the
improvement backlog is doing its job. The
program improves between exercises. The next
real incident finds a shorter list of gaps
than the last.

## Summary

- Tabletops test the composite incident-
  response capability without the cost of a
  real incident. They are tests, not
  training.
- Three capabilities tested: decision-making
  under compressed time, cross-functional
  coordination, reaching the regulatory
  interface.
- Six properties of a working tabletop:
  realistic scenario, cross-functional,
  time-pressured, decision-forcing,
  documented in real time, reviewed.
- Scenarios are grounded in real patterns,
  cross-cutting on at least one dimension,
  and contain at least one genuinely
  ambiguous decision. Avoid too-easy,
  too-exotic, and ambiguity-free scenarios.
- Injects are decision-forcing, not
  informational. A half-day exercise
  typically runs 6–8 injects simulating
  48–72 hours.
- Three role categories: players (the
  response team), observers (Audit
  Committee, internal audit, downstream
  functions), facilitator (drives, does
  not participate). External facilitation
  is the default for high-visibility
  exercises.
- Scoring on four dimensions with specific
  anchors: decision quality, decision
  timing, coordination, documentation.
  Hot-wash within 30 minutes; written
  review within 10 business days.
  Recommendations route into the same
  improvement backlog as real-incident
  reviews.
- Three cadences: quarterly rotation across
  scenario types, annual with broader
  participation, on-demand when new
  incident types emerge.
- Four anti-patterns: performance art,
  tabletop-as-training, same scenario
  repeatedly, no findings. A working
  tabletop finds 2–4 substantive issues
  and routes them.
