# Chapter 2 — Detection and the First Hour

## Why this chapter exists

Most of what goes wrong in an AI incident response
is set in the first hour. The classification is
wrong, so the wrong team leads; the containment
posture is wrong, so the response either harms
customers unnecessarily or lets harm continue; the
first-hour evidence is not captured, so the
post-incident review two months later cannot
reconstruct what actually happened. The errors
compound: a bad first-hour classification routes
the incident to a team that will not pursue the
notification obligations correctly, which produces
a regulator finding months later even if the
substantive response was otherwise competent.

The chapter teaches first-hour discipline. Not the
philosophy of readiness — specific decisions the
single named lead has to make inside the hour,
with specific evidence produced, inside a specific
decision structure that survives post-hoc review.

## 2.1 Detection: what fires the response

AI incidents reach the program through more
channels than classical security incidents. Each
channel has a different urgency posture, a different
credibility weight, and a different first-move
pattern.

| Source | Typical signal | Urgency posture |
|---|---|---|
| AI program monitoring | Threshold-crossing alert on bias, drift, calibration, performance | Variable — depends on the monitor's prior false-positive rate |
| SOC / security monitoring | Classical intrusion indicators, AI-specific signatures (prompt-injection, model-exfil) | High when confirmed |
| Customer complaint | Customer reports unexpected AI behaviour, incorrect output, perceived discrimination | Variable — but underweighted by most programs |
| Whistleblower / staff report | Internal observer notices pattern | High — because the observer has already classified something as abnormal |
| Vendor notification | Upstream provider (LLM vendor, data provider, infra provider) discloses an issue affecting the system | High — vendors do not notify casually |
| Regulator inquiry | Supervisor asks a question that reveals an issue | High — the regulator is already engaged |
| Media / public reporting | Journalist, researcher, or social-media surfacing of an issue | High — because external awareness has started |
| External researcher | Bug bounty, security researcher, academic auditor | Variable — depends on severity of what was found |

Three biases to resist. First, monitoring alerts
tend to be *underweighted* because of their
cry-wolf history; this leads to delayed response
on real incidents that happen to come through
monitoring. Second, customer complaints tend to be
*underweighted* because they arrive one at a time
without the structure the complaints collectively
reveal; a program with no pattern-detection on the
complaint stream will miss things. Third, vendor
and regulator channels tend to be *correctly
weighted* precisely because the sender has already
done triage.

The practical discipline: at program quiet times,
specify which channels route directly to the AI IR
on-call rotation and which route via triage first.
A monitoring alert on a top-tier system should
route directly; a monitoring alert on a secondary
system can route via triage. Customer complaints
should route via pattern-detection on the stream,
not individually.

## 2.2 Verification: is this real?

Not every detection event is an incident. False
positives are expensive — a full response to a
false alarm consumes credibility the program needs
for real incidents. The first decision in the first
hour is whether to proceed.

Three verification patterns worth naming:

- **Confirmed.** The detection signal is
  unambiguous: the model is producing demonstrably
  wrong outputs on a reproducible set of inputs,
  the vendor has issued a specific advisory, the
  SOC has already triaged a classical intrusion.
  Proceed with full response.
- **Suspected.** The signal is ambiguous. The
  monitoring threshold crossed but the sample size
  is small; the customer complaint is credible but
  isolated; the vendor hint is vague. The right
  posture is to proceed with provisional
  classification while the response team's first
  working session attempts to confirm or
  disconfirm.
- **Likely false positive.** The signal matches a
  known false-positive pattern (the Monday-morning
  drift spike that appears every week with the
  weekend data refresh, the customer-complaint
  pattern that matches a documented UX issue).
  Investigate quickly but do not escalate; open an
  incident ticket and close it with a false-
  positive disposition — do not simply mute.

The discipline the chapter needs most to insist
upon: **never let "we'll wait until we know" delay
the response past the first hour**. Provisional
classification with explicit provisional status is
the right posture when verification is incomplete.
Programs that wait for certainty before classifying
discover certainty arrived after the regulatory
clock ran out.

## 2.3 The mute-the-alert temptation

A specific failure mode worth naming in isolation.
When a monitoring alert fires and the on-call
suspects a false positive, the temptation is to
mute the alert, investigate privately, and close
the matter without opening an incident. This is
almost always wrong, and for three specific
reasons:

- Muting the alert removes the historical record of
  when and how often it fired. The next time it
  fires, no one knows this is the second instance;
  the context that would have classified it as a
  real pattern is gone.
- Private investigation means the rest of the
  response team does not know an investigation is
  underway. If the alert turns out to be real,
  escalation starts late because other team members
  did not have the opportunity to notice.
- The response discipline degrades. The team learns
  that monitoring alerts can be handled silently,
  which produces the pattern where real incidents
  arrive in silence.

The right pattern: open the incident with
provisional classification, investigate openly,
close as false positive if that is what the facts
warrant. Closing as false positive is honest work;
muting silently is credibility arbitrage against the
future.

## 2.4 The four decisions in the first hour

Four specific decisions the single named lead must
make inside the first hour. The chapter's
exercises will drill these specifically.

### 2.4.1 Verify or defer

Per §2.2 and §2.3: confirmed, suspected, or likely
false positive. The result is recorded in the audit
ledger with the person making the determination
and the time.

### 2.4.2 Provisionally classify

Per [`mod-107`](../mod-107-ai-security/README.md)
§6: security, AI-program, or joint. The
classification routes the response — classical IR
machinery for security, CAO-led for AI-program,
co-lead for joint — and triggers the applicable
notification matrix (Chapter 4) and governance
convene (per the firm's escalation thresholds).

The classification is explicitly *provisional*.
First-hour classifications are made with incomplete
information; the response team can and should
reclassify as information clarifies, and should
record each reclassification with reasoning. The
provisional label is not a failure of discipline;
it is the discipline.

### 2.4.3 Assign the single named lead

Per the boundary patterns in
[mod-104 Ch. 6](../mod-104-model-risk-management/README.md),
[mod-107 Ch. 5](../mod-107-ai-security/README.md),
and [mod-109 Ch. 6](../mod-109-compliance-operations/README.md):
one function leads any given incident; others
contribute. The lead is assigned in the first hour.
For an AI-program classification, the lead is the
AI Risk Lead (or the role filling that function);
for security, the CISO's incident commander; for
joint, both are named with explicit decision
authorities per activity.

The single-named-lead convention is the structural
remedy for the diffuse-responsibility failure mode
AI incidents are prone to (§1.2.5). Without it,
the response produces decisions by consensus-
drift; with it, decisions have a name attached and
can be defended.

### 2.4.4 Choose the containment posture

Per Chapter 3: contain, partially contain, operate
with elevated monitoring, or roll back. The
first-hour choice is explicitly *provisional* and
revisited at every subsequent working session of
the response team.

Over-containment and under-containment are both
first-hour failure modes with specific political
logics (Chapter 3 operationalises each). The lead
is the one who defends the posture — not the
response team collectively, not the governance
body, not the CRO. The posture is the lead's call,
with the response team's input and the governance
body's visibility.

## 2.5 Who is on the first-hour call

The response team convenes within the first hour.
Membership depends on classification but typically
includes:

- The single named lead (per §2.4.3).
- The AI Risk Lead and / or CISO on-call (both for
  joint classification; whichever is lead for
  single-function).
- The relevant **model owner** or system owner — the
  business-unit role accountable for the system's
  operation. If the owner cannot be reached in the
  first hour, the response team records the
  attempt and proceeds; it does not wait.
- **General Counsel** or the delegated attorney.
  Many first-hour decisions have privilege and
  liability implications; GC presence is not
  ceremonial.
- A **communications lead** (per Chapter 8). Even
  if no communication is sent in the first hour,
  the communication posture is being set; the
  comms lead is in the room from the start.
- The **AI Risk Council chair** or delegate, for
  classification routing visibility. (The Council
  itself does not convene in the first hour; the
  chair's visibility is enough.)
- The **compliance operations lead** (per
  [`mod-109`](../mod-109-compliance-operations/README.md))
  for notification matrix consultation.

Three roles that should be visible but are not
usually on the first call: the CRO (visibility
without participation unless the incident is
material at the enterprise scale), the Audit
Committee chair (visibility only, via GC), the CEO
(visibility only, via CRO or GC, for material
incidents).

The first-hour call is a *working* meeting, not a
briefing. The decisions in §2.4 are made in the
call, not reported to the call. The lead drives.

## 2.6 What the first hour produces

Evidence captured in the audit ledger regardless of
outcome:

- The **detection event** itself (source, time,
  signal, who received it).
- The **verification decision** (confirmed /
  suspected / false positive) with the deciding
  role, time, and reasoning.
- The **provisional classification** with the
  deciding role, time, and reasoning. If
  reclassification occurs later, both the original
  and the reclassification are retained.
- The **single-named-lead assignment** with time
  and the authority basis (per the taxonomy's
  routing rules).
- The **response team convene event**, with
  attendance list and absentees recorded.
- The **containment posture decision** with
  reasoning, including the counterfactual the lead
  considered (what the posture is in case this
  turns out to be real vs. not).
- The **notification matrix consultation record** —
  which matrix row the team consulted, which
  notification clocks are now running, which
  notifications have been triggered and which are
  pending further information.

Programs without first-hour evidence capture end up
with narrative reconstructions weeks later that do
not reconcile with the ledger. The reconstruction
undermines the review's credibility and increases
the regulator's suspicion. Programs with disciplined
first-hour capture produce reviews that stand on
contemporaneous record.

The audit-ledger discipline from
[`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)
is the chapter's silent prerequisite: the ledger
has to exist, be reliable, and support the event
vocabulary before first-hour capture can be the
default rather than an aspiration.

## 2.7 The hour-24 revisit

A pattern worth adopting explicitly: at hour 24 of
every incident response, the response team revisits
each of the four §2.4 decisions and asks whether
the current fact pattern still supports the
original decision.

- Was the verification correct, or has the signal
  shifted? (Sometimes a "suspected" matures to
  "confirmed"; occasionally a "confirmed" turns out
  to be a complex false positive.)
- Is the classification still right? Did joint
  elements emerge that reroute from AI-program to
  joint classification? Did the AI-program
  classification turn out to be a classical
  security misdiagnosis?
- Is the lead still the right lead? (Sometimes the
  original lead has to hand off because the
  incident's shape has shifted.)
- Is the containment posture still right? Should it
  tighten or relax given what hour 24 has revealed?

The hour-24 revisit is not an admission of
first-hour error; it is the structured recognition
that first-hour decisions are made with incomplete
information. Programs that do not revisit at hour
24 tend to carry first-hour errors to hour 72 or
beyond, where they become costlier to correct.

Hour 24 is also the natural decision point for
most of the notification matrix's "do we notify
provisionally or wait" calls (see Chapter 4 §4.5).
The revisit and the notification call are the same
meeting.

## Summary

- Detection reaches AI programs through more
  channels than classical IR: monitoring, SOC,
  customer complaint, whistleblower, vendor,
  regulator, media, external researcher. Each
  carries a different urgency posture; monitoring
  and complaints tend to be systematically
  underweighted.
- Verification distinguishes confirmed / suspected
  / likely false positive. The discipline is to
  proceed with provisional classification when
  verification is incomplete rather than wait
  for certainty.
- Muting a monitoring alert quietly is almost
  always wrong — it removes historical record,
  hides investigation, and degrades response
  discipline. Open the incident, investigate
  openly, close as false positive if warranted.
- Four first-hour decisions: verify or defer,
  classify provisionally (per mod-107 §6), assign
  the single named lead (per boundary patterns),
  choose the containment posture (per Chapter 3).
- The response team on the first-hour call: single
  named lead, AI Risk Lead / CISO on-call, model /
  system owner, GC, communications lead, AI Risk
  Council chair for visibility, compliance
  operations lead for notification matrix.
- The first hour produces evidence captured in the
  audit ledger (mod-108): detection event,
  verification, classification, lead assignment,
  convene, containment posture, notification
  matrix consultation. Programs without first-hour
  capture produce reviews that do not survive
  scrutiny.
- At hour 24 the team revisits the four decisions
  explicitly. This is the structured recognition
  that first-hour decisions are made with
  incomplete information and must mature as
  information clarifies.
