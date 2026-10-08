# Chapter 3 — Containment Without Over- or Under-containment

## Why this chapter exists

Containment is the activity that *stops the
incident from continuing*. For classical security
incidents, containment is often a matter of
isolating a compromised asset: pull the network
cable, revoke the credential, firewall the host.
The affected unit continues to work; the asset is
quarantined; the business continues around it.

For AI incidents, containment is harder in a
specific way: the thing being contained is often
the thing providing value. Pausing the triage
recommender means patients wait longer. Pausing
the fraud scorer means fraud is scored manually or
not at all. Pausing the LLM assistant means the
support queue backs up. Each of these costs,
sometimes visibly and sometimes invisibly, and the
cost accrues *during* the response — on the
response team's watch, counted against their
decisions.

The result: containment postures in AI incidents
are decided under genuine two-sided risk. Over-
containment produces visible cost (customers can't
transact, dependent systems degrade, operations
suffer). Under-containment produces hidden cost
(continued harm to customers during the response
window). Programs that reflexively over-contain
drift towards the pattern where business leaders
stop trusting the response team's judgement;
programs that under-contain accumulate incidents
in which the response could have shortened the
harm window and did not. The chapter teaches the
discipline that defends either direction.

## 3.1 The containment option set

Five options the response team can select or
combine. Each has a different cost structure and a
different detection posture under continued
operation.

- **Full system pause.** The AI system is
  disabled; the fallback path (manual, legacy
  system, human review) carries the load. Highest
  cost of containment; strongest reduction of
  continuing harm. Used when the system is
  producing harm the fallback does not.
- **Capability restriction.** Some operations of
  the AI system are blocked; others continue. The
  recommender keeps running for balance-inquiry
  but is disabled for fund-transfer; the triage
  tool keeps triaging low-acuity patients but
  escalates all high-acuity to human review; the
  LLM keeps answering informational queries but
  not account-change requests. Narrower cost, less
  reduction, requires the capability boundary to
  be enforceable at the system interface.
- **Scope restriction.** The AI system continues
  for some users / cohorts / sites but not others.
  Pause at the affected site; continue at
  unaffected sites. Pause for the affected
  customer cohort; continue for the rest. Narrower
  cost than a full pause, but the response team
  must be able to defend the scope boundary — if
  the pattern is at other sites that have not
  yet surfaced it, the scope-restricted posture
  under-contains.
- **Elevated monitoring with continued operation.**
  The AI system keeps running but every output is
  flagged for human review at a higher rate (or
  outputs over a confidence threshold are
  reviewed, or a sample is sent to review). Cost
  is operational (reviewer capacity) rather than
  customer-facing. The response team can observe
  whether the incident is continuing.
- **Rollback to a prior version.** Revert to a
  known-good model, prompt, configuration, or data
  snapshot. Preserves the AI capability while
  removing the suspected cause. Available only if
  the known-good version exists and is deployable.

The options compose. A credit-decision incident
might be contained by rolling back the model
version *and* restricting scope to the two sites
with elevated monitoring *and* capability-
restricting high-value loans to manual review for
48 hours. Chapter 2 Ex-01's exercise walks a
compound containment posture through this kind of
decision structure.

## 3.2 Choosing among the options

Five variables the response team evaluates:

1. **Confidence in the incident.** High confidence
   warrants more restrictive containment;
   uncertainty warrants less. The verification
   state from Chapter 2 §2.2 feeds this directly.
2. **Cost of continued operation if the incident
   is real.** Customer harm (how many customers,
   how severe), regulatory liability (what
   notifications would be triggered, what
   penalties available), trust loss (what the
   public reporting looks like if this surfaces
   externally). This is the under-containment
   cost.
3. **Cost of containment itself.** Customer-
   experience impact (wait times, failed
   transactions), dependent system impact (what
   breaks downstream), operational cost (reviewer
   staffing, call-centre volume), business cost
   (lost revenue, breached SLAs). This is the
   over-containment cost.
4. **Containment reversibility.** Can the
   containment be relaxed quickly if it turns out
   to be unnecessary? A capability-restriction via
   configuration flag relaxes in minutes; a model
   rollback that invalidates downstream caches may
   take hours to reverse. The faster the reversal,
   the more aggressive the lead can be in the
   first-hour posture.
5. **Detection capability under continued
   operation.** If the AI keeps running (full
   operate, elevated monitoring, scope-restricted
   operate), can the team observe whether the
   incident is still occurring? If detection
   capability is high, the lead can defend a
   less-restrictive posture because the team will
   know if containment proves inadequate.

The right posture rarely "feels" right at the
time. Both failure modes have specific political
logics that bias decisions in opposite directions.

## 3.3 Over-containment: the failure mode and its logic

**Over-containment** is pausing or restricting
more than the incident actually warrants.
Symptoms:

- The entire AI portfolio is paused for an
  incident affecting one system.
- Containment continues longer than necessary
  because no one wants to be the one who relaxes
  it.
- The cost of containment is materially higher
  than the cost the incident, treated at the
  posture one notch down, would have produced.
- The business learns to work around the AI
  system because it is routinely paused during
  incidents; the AI function's credibility erodes.

The political logic: over-containment is **safe for
the response team**. No one gets blamed for being
too cautious. The lead who paused the system can
defend the pause to any auditor; the lead who kept
the system running has to defend why. In most
institutional cultures, the asymmetry of blame
pushes the posture toward over-containment by
default.

The discipline the chapter teaches: over-containment
has real costs, and the response team must be able
to defend the posture against the counterfactual in
*both* directions. The decision record (§3.5) must
show that the containment cost was considered, not
just the incident cost.

Repeat over-containment patterns degrade the
program's credibility with the business. When the
third incident this year pauses an AI tier for
48 hours and later turns out to have warranted a
scope-restriction, business leaders stop trusting
the AI function to make proportionate calls. The
next incident's posture — including the one where
full pause is actually warranted — becomes harder
to defend.

## 3.4 Under-containment: the failure mode and its logic

**Under-containment** is operating the AI system
through the incident, producing continuing harm
during the response window. Symptoms:

- Continued operation while the response team
  investigates.
- Customer harm during the investigation period
  that was predictable at the time of the
  first-hour decision.
- The post-incident review later finds the
  containment posture was inadequate on
  information the team had at the first hour.

The political logic is the mirror image: no one
wants to take down a revenue-generating system,
no one wants to be the lead who caused the
business a four-hour service outage, no one wants
the news story that reports "firm took down its AI
system over a false alarm." The under-containment
pressure comes from business leaders worried about
the cost of the pause and from a response team
reluctant to impose that cost without being
certain.

The discipline the chapter teaches: under-
containment is defensible only when the response
team can show, under counterfactual analysis, that
the posture chosen was proportionate to the
information available at the first hour. The test
is not what later turned out to be true; the test
is what the team knew when they chose.

The post-incident review (Chapter 6) applies this
test explicitly. If the review finds that the
first-hour information warranted more containment
than the team chose, the finding is a program-
improvement input — not necessarily a blame
finding on the lead, because the pressure to
under-contain is systemic and the review must
address the systemic contributor as well.

## 3.5 Defending the posture: the decision record

Both failure modes have the same remedy: a
contemporaneous decision record that captures the
information the lead had, the options considered,
the costs on both sides, and the reasoning for the
posture chosen.

A working decision record (in the audit ledger per
[`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md))
captures:

- **Time of decision** and **deciding role**
  (single named lead).
- **Verification state** at the time (confirmed /
  suspected / likely false positive).
- **Options considered** — explicitly, including
  the options not chosen.
- **Costs considered on both sides**:
  - *Continued-operation cost if the incident is
    real:* customer harm estimate, regulatory
    exposure, trust implications.
  - *Containment cost:* customer-experience
    impact, dependent system impact, operational
    cost, business cost.
- **Posture chosen** with the specific
  configuration (which capabilities, which cohorts,
  what elevated-monitoring thresholds).
- **Reversibility assumption** — how long to
  relax, how long to re-tighten.
- **Detection posture under the chosen
  containment** — what the team will know and
  when, enabling the hour-24 revisit (per Chapter
  2 §2.7).
- **Next revisit time** — explicit, not "when we
  know more".

The decision record is the single artifact that
defends the posture in post-incident review and
regulator inquiry. "The team made the best call
with the information available" is a defensible
claim only if the record shows what information
was available and how it was weighed. Programs
that treat containment as a judgement call without
record cannot defend either direction.

## 3.6 Containment is reversible

A framing worth adopting explicitly: the
containment posture is **provisional at every
step**. The response team can and should relax
containment as the situation clarifies, and should
re-tighten if new facts emerge. First-hour
over-containment can be relaxed at hour 24 without
loss of face; first-hour under-containment can be
tightened at hour 24 without admitting the first-
hour was wrong.

Programs that treat the initial containment
decision as permanent constrain themselves
unnecessarily. The hour-24 revisit (Chapter 2
§2.7) is explicitly a containment-revisit meeting.
"Should we tighten or relax containment given what
we know now?" is one of the standing questions.

The ratchet failure mode worth naming:
containment that only tightens, never relaxes.
Once a capability is restricted "for safety," no
one wants to be the one to re-enable it; months
pass; the restricted capability becomes permanent
by neglect. The ratchet is the long-form version
of over-containment. The discipline is naming,
at the time of each containment move, the
specific conditions under which it will be
relaxed. "This restriction stays in place until
investigation closes the hypothesis that
training-data drift caused the pattern" is a
condition; "this restriction stays in place until
we're sure" is not.

## 3.7 Containment interacts with notification

A specific coupling between containment and
Chapter 4's notification matrix: the containment
posture is **evidence of the incident's severity**,
and regulators read it that way.

A full-system pause reads as the firm treating the
incident as severe; an operate-with-elevated-
monitoring posture reads as the firm treating it
as moderate. If the firm's notification claims the
incident is moderate but the containment posture
was a full pause, a regulator will ask about the
inconsistency. If the notification claims the
incident is serious but the containment posture
was elevated monitoring, the regulator will ask a
different question.

The practical implication: the lead must be able
to defend the alignment between the two. Not
because they must match in some mechanical way —
sometimes a full pause is operationally the only
reversible option, and the incident is still only
moderate — but because the record must *explain*
the pattern. The decision record (§3.5) that
captures the posture is also what explains the
alignment to the notification matrix's severity
determination.

## 3.8 Operational handoff of a sustained containment

A specific operational detail: containment
postures that persist beyond the first 24 hours
need to be transferred into normal operation
rather than held on the response team's call.
Full pauses in particular need a defined
transition into business continuity (which
fallback path is operating, who is monitoring it,
what the capacity is, how long it can sustain).

The transition is itself an event in the ledger:
the containment posture becomes a scoped
restriction with a named owner, a review cadence,
and a stated condition for relaxation. The
response team can disband or scale down; the
containment persists on the normal operational
layer. Without this transition, containment
either stays indefinitely on an overheated
response-team call bridge or quietly dissolves
without the ratchet-relax discipline from §3.6.

## Summary

- Containment is the discipline of stopping an
  incident from continuing. For AI systems,
  containment often degrades the thing providing
  value — the AI system itself — so it is decided
  under genuine two-sided risk.
- Five composable options: full system pause,
  capability restriction, scope restriction,
  elevated monitoring with continued operation,
  rollback to prior version. The response team
  can combine.
- Five variables drive the choice: confidence in
  the incident, cost of continued operation if
  real, cost of containment, containment
  reversibility, detection capability under
  continued operation.
- Over-containment is the failure mode of pausing
  more than warranted. Its political logic:
  no one gets blamed for being too cautious.
  Repeat over-containment degrades the program's
  credibility with the business.
- Under-containment is the mirror failure mode:
  continued operation produces continuing harm.
  Its political logic: no one wants to take down
  a revenue-generating system. The counterfactual
  test is what the lead knew when they chose, not
  what later turned out to be true.
- The decision record is the artifact that defends
  either direction: time, lead, verification
  state, options considered, costs on both sides,
  posture chosen, reversibility, detection
  posture, next revisit.
- Containment is reversible at every step.
  First-hour postures are provisional; the hour-24
  revisit is explicitly a containment-revisit
  meeting. The ratchet failure mode — containment
  that only tightens — is defeated by naming the
  relax condition at the time of each move.
- Containment couples to notification. The
  posture is read by regulators as evidence of
  severity; the record must explain the alignment.
- Sustained containment transitions into normal
  operation at a defined event, with named owner
  and review cadence. Without the transition,
  containment either persists indefinitely on an
  overheated response bridge or dissolves without
  the relax discipline.
