# Chapter 4 — The Notification Matrix

## Why this chapter exists

More AI programs fail regulatory review on
notification timing than on substantive response.
The reason is specific: notification timelines are
measured in hours or days from a trigger event
that is itself a judgment call ("awareness"
under GDPR Art. 33; "determination" under NYDFS
§500.17; "becoming aware" under EU AI Act Art. 73).
When a response team under incident pressure also
has to interpret ambiguous triggers against
regimes they have not internalised, they miss
clocks that could have been met.

A **notification matrix** is the pre-computed
decision aid that lets the response team consult
rather than interpret in the moment. Built at
program quiet times by the CAO function with the
Chief Compliance Officer (per
[`mod-109`](../mod-109-compliance-operations/README.md)
Ch. 6) and the DPO (where privacy regimes apply),
the matrix answers "for *this* classification of
incident, who gets notified, in what window, by
whom, in what format, with what approvals". When
the first-hour team pulls the matrix, they consult
rather than re-derive — the derivation already
happened.

This chapter builds the matrix, section by
section. The specific 2026 obligations landscape
grounds it, but the discipline is more durable
than the specific regime list: a program with a
working matrix can absorb new obligations as they
land without rebuilding the response machinery.

## 4.1 The seven matrix dimensions

For each incident classification (per
[`mod-107`](../mod-107-ai-security/README.md)
§6), the matrix specifies seven dimensions per
notification obligation that may apply:

| Dimension | The question it answers |
|---|---|
| **Recipient** | Which specific regulator, cohort, business partner, or internal body is notified |
| **Trigger** | Which facts about the incident activate this notification (not just "an incident", but *this classification* with *these attributes*) |
| **Timeline** | The specific window, measured from a specific starting event (e.g., 72 hours from awareness; 2 days from determination; immediate for defined classes) |
| **Lead** | Which function at the firm authors and transmits — AI Risk Lead, CISO, DPO, Chief Compliance Officer, General Counsel, Investor Relations |
| **Format** | Prescribed template or structured format if regulated (EU AI Act Annex IX; state DFI forms; NYDFS reporting portal) |
| **Supporting evidence** | What accompanies the notification — incident summary, scope estimate, containment status, remediation plan |
| **Approvals required** | Who must sign before transmission — CAO + GC + CRO is a common minimum for AI-specific notifications |

A matrix row with any of the seven unfilled is
incomplete. Programs that leave "format" blank
discover during an incident that the regulator
expects a specific template; programs that leave
"approvals" blank discover a general counsel who
is not available at hour 70 of a 72-hour clock.

The matrix lives in the audit ledger per
[`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md),
is version-controlled, and is signed by the
authoring heads of function. See §4.4 for why
versioning matters.

## 4.2 The 2026 obligations landscape

Six regime families most likely to apply to AI
incidents at a cross-jurisdictional firm. The
chapter cites primary sources; practitioners
should read the source text, not practitioner
summaries, when authoring the matrix.

### 4.2.1 EU AI Act Art. 73 — serious incidents

The EU AI Act (Regulation (EU) 2024/1689) requires
providers of high-risk AI systems to report
"serious incidents" to the national competent
authority (NCA) of the Member State where the
incident occurred.

- **Timelines.** The Regulation specifies
  tiered timelines: immediate for incidents
  involving infringement of fundamental rights
  that have a widespread or irreversible
  effect, with the Regulation setting the
  outer bounds and implementing acts
  elaborating the mechanics. Readers should
  consult the Regulation text and any
  implementing acts current at the time of
  the matrix build; the specific days-count
  used in operational matrices should be
  cross-checked against the then-current
  official source rather than paraphrased.
  <!-- needs-research: cite the specific Art. 73 timeline tiers and any 2025/2026 implementing acts clarifying the trigger definitions once they are available. The AI Office may publish operational templates. -->
- **Trigger.** "Serious incident" is defined
  with respect to the AI system's impact —
  injury or death, significant damage to
  property or environment, serious and
  irreversible disruption of critical
  infrastructure, infringement of fundamental
  rights.
- **Lead.** The CAO function authors the
  notification; the General Counsel approves;
  the DPO contributes where personal data is
  involved.
- **Format.** Member States and the AI Office
  are expected to standardise reporting;
  authors should use the current template.
- **Supporting evidence.** Scope estimate,
  containment status, provisional root cause,
  remediation posture.

### 4.2.2 NYDFS Part 500 §500.17 — cybersecurity events

The NY Department of Financial Services'
cybersecurity regulation (Part 500) applies to
covered financial-services firms operating in
New York. §500.17 requires notification of a
"cybersecurity event" to the Superintendent.

- **Timeline.** 72 hours from determination that
  a cybersecurity event has occurred that
  requires notification. The 2023 amendments
  tightened and expanded the regime; the 2024
  amendments added class notifications for
  specific event types. Authors should refer
  to the then-current Part 500 text.
- **Trigger.** Covered events include those
  with a reasonable likelihood of materially
  harming any material part of normal
  operations, those requiring notice to any
  government body, self-regulatory agency, or
  other supervisory body, and ransomware-
  specific triggers. AI incidents can trigger
  via several of these.
- **Lead.** The CISO leads for the
  cybersecurity notification mechanics; the
  CAO function contributes AI-specific
  content where the AI system was the vector
  or the harm.
- **Format.** NYDFS portal with structured
  fields.
- **Supporting evidence.** Prescribed per
  portal; typically includes the event summary,
  the systems affected, the data categories,
  the response posture.

### 4.2.3 GDPR Art. 33 and Art. 34 — personal data breach

- **Art. 33 — to the supervisory authority.**
  Notification without undue delay and, where
  feasible, not later than 72 hours after
  having become aware of the breach, where the
  breach is likely to result in a risk to the
  rights and freedoms of natural persons.
- **Art. 34 — to the data subject.** Without
  undue delay when the breach is likely to
  result in a high risk to the rights and
  freedoms of natural persons.
- **Trigger.** Personal data breach as defined
  in Art. 4(12). An AI incident that exposed,
  altered, or lost personal data processed by
  the AI system can trigger. A bias incident
  may or may not trigger depending on whether
  it involved personal data processing in a
  way that affected the data subjects'
  rights.
- **Lead.** The DPO leads for the Art. 33
  notification; the CISO contributes the
  cybersecurity dimension; the CAO function
  contributes the AI content; the General
  Counsel approves. For Art. 34 to the data
  subject, the customer-service and
  communications functions join the lead
  group.
- **Format.** Supervisory authority template.
- **Supporting evidence.** Nature of the
  breach, categories and approximate number
  of data subjects, likely consequences,
  measures taken.

### 4.2.4 Sector-specific — financial services

- **SR 11-7 model events.** Not a hard
  notification regime in the EU AI Act or
  GDPR sense, but a supervisory expectation
  that material model events are escalated to
  the firm's supervisor (OCC, FRB, FDIC). The
  MRM function (per
  [`mod-104`](../mod-104-model-risk-management/README.md))
  typically leads; the CAO function
  contributes AI-specific content for AI
  systems that qualify as models.
- **SEC cybersecurity disclosure (2023 rule).**
  For public companies, material cybersecurity
  incidents require Form 8-K disclosure within
  four business days of materiality
  determination. The Chief Financial Officer
  and General Counsel lead; the CAO function
  contributes AI content where applicable;
  Investor Relations manages the public
  disclosure.
- **FINRA Rule 4530** for broker-dealers on
  specified reportable events, including
  certain customer complaints and
  cybersecurity events.

### 4.2.5 Sector-specific — healthcare

- **FDA SaMD adverse event reporting (21 CFR
  803 for medical devices).** For AI systems
  classified as Software as a Medical Device,
  manufacturers report adverse events per
  the medical-device adverse-event framework.
  Timelines vary (5-day, 30-day, periodic);
  authors should consult 21 CFR 803 and the
  SaMD-specific guidance current at matrix
  build time.
- **FDA PCCP-specific triggers** where a
  Predetermined Change Control Plan governs
  continuous-learning behavior and a change
  falls outside the PCCP envelope.
- **HHS OCR breach notification (HIPAA)**
  where protected health information is
  affected.

### 4.2.6 Sector-specific — insurance

- **NAIC Model Bulletin on Use of AI Systems
  by Insurers (2023, as adopted by states).**
  Governance and documentation expectations;
  state-by-state adoption drives specific
  notification mechanics.
- **State insurance regulator notifications**
  for market-conduct events, discriminatory
  pricing or claims-handling outcomes, or
  rate-filing-material deviations.

### 4.2.7 Internal and contractual

- **Board of Directors** — the Audit
  Committee or Risk Committee, typically with
  a materiality threshold. For material
  incidents the Chair is briefed in the first
  24 hours.
- **AI Risk Council** — convened per the
  escalation thresholds the firm defines.
- **Customer contracts** — large-customer
  contracts frequently require notification
  within specified windows (24 hours, 72
  hours, 5 business days) of incidents
  affecting the services the customer buys.
- **Vendor contracts** — some vendor
  contracts require notification *to* the
  vendor of incidents affecting their
  products; others require vendors to notify
  the firm, which creates a different
  obligation.

The internal and contractual rows are the ones
most frequently missed. External regulatory
regimes have practitioner attention; customer-
contract notification obligations frequently sit
in commercial-contract clauses that neither the
response team nor the compliance operations team
is routinely tracking.

## 4.3 Pre-computation: the matrix is authored at quiet times

The core discipline: the matrix is authored when
the program is **not** under incident pressure.
At quiet times, the authoring team can:

- Read the primary regulatory text carefully.
- Resolve ambiguities with internal counsel and
  (where appropriate) outside counsel.
- Consult precedent — how similar incidents
  have been treated by the firm's own regulators
  in the past.
- Model edge cases without being under the
  clock.
- Produce a matrix that the response team can
  *use*, not interpret.

A matrix authored during an incident is a matrix
authored under deadline pressure. Pre-computation
is the only way to get it right. A good exercise
is this chapter's Ex-02: build the matrix for a
specific firm at a specific regulatory posture at
a quiet time and compare against the first
real-incident consultation.

The matrix is updated on triggers, not on
calendar. Three triggers that should produce a
matrix update:

- **A new regulation.** An EU AI Act
  implementing act drops; a state passes an AI
  law; NYDFS amends Part 500.
- **A new jurisdiction.** The firm starts
  operating in a new country, state, or sector
  with its own regime.
- **A matrix defect.** An incident surfaces a
  row that was wrong or missing; the
  post-incident review (Chapter 6) feeds the
  update back.

A joint quarterly review (CAO function + Chief
Compliance Officer + CISO + DPO + GC) is the
calendar backstop. Even without a specific
trigger the review walks the matrix for drift.
See [`mod-109`](../mod-109-compliance-operations/README.md)
Ch. 6 for the joint-review cadence.

## 4.4 The matrix is itself evidence

Like everything else in the program, the matrix
is an evidence artifact (per
[`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)):
signed by the authoring heads of function,
version-controlled with timestamp, retained with
chain-of-custody.

The versioning matters. When a regulator later
asks why incident X on date D was treated as
non-notifiable, the matrix in effect on date D
has to be retrievable. If the matrix has since
been updated to add that notification, the version
history shows that the response at the time
followed the then-current matrix. If the matrix
was already correct and the response did not
follow it, that is a different (and worse) finding.

Three evidentiary scenarios the matrix must
survive:

- **A missed notification.** Regulator asks "why
  did we not hear from you within 72 hours of
  the breach you disclosed last quarter?" The
  matrix in effect at the time showed the
  classification; the response's matrix
  consultation record (per Chapter 2 §2.6)
  shows what the response team concluded. If
  the matrix was wrong, the firm has a
  documented oversight; if the matrix was
  right and the response did not consult, the
  firm has a worse problem.
- **A false-positive notification.** Regulator
  received a notification that turned out not
  to be warranted. "We notified under matrix
  row R because at the time the facts matched
  R; subsequent investigation revealed that
  the triggering facts did not actually hold."
  Over-notification is a smaller problem than
  under-notification but still consumes
  regulator credibility; the matrix with the
  then-current trigger specification defends
  the choice.
- **A multi-regime incident.** Regulator in
  one jurisdiction asks why a notification
  made to a peer regulator in another
  jurisdiction was not also made to them. The
  matrix shows the regime-specific triggers
  and the response's consultation record
  shows which rows were applied.

A program whose matrix cannot survive these three
scenarios is not using the matrix as evidence; it
is using it as reference material.

## 4.5 Awareness is a judgment call

The hardest practical question in notification:
**when do we know enough to notify?** Every
regime measures the clock from some version of
"awareness" or "determination," and both are
judgment calls:

- GDPR Art. 33: "after having become aware" —
  guidance distinguishes awareness of the breach
  from awareness that a breach has occurred.
- NYDFS §500.17: "determination that a
  cybersecurity event has occurred" — explicit
  determination step.
- EU AI Act Art. 73: "serious incident" —
  requires both the incident and its
  classification as serious.

Three operational patterns the chapter adopts:

### 4.5.1 Notify provisionally

Many regulations explicitly contemplate
provisional notification with follow-up updates.
A first notification with provisional information
meets the timeline; subsequent updates fill in
details as the investigation produces them.
Programs that wait for the full picture before
notifying frequently miss the first clock.

Provisional notification requires the matrix row
to specify what the first notification contains
(at minimum: the fact of the incident, the
classification, the containment posture, the
expected update cadence) and what subsequent
notifications contain.

### 4.5.2 Notify with caveats

State what is known, what is suspected, what is
unknown. Regulators generally prefer "we are
notifying you now with limited information
because [reason]; we will provide a complete
picture within [window]" to silence until the
picture is complete.

### 4.5.3 The hour-24 decision pattern

Treat the hour-24 revisit (per Chapter 2 §2.7)
as the "are we notifying or not" decision point
for most obligations. By hour 24 the response
team has enough information to make the
notification call for 72-hour regimes with some
margin; further delay is just delay. For 2-day
and 15-day regimes the hour-24 decision is a
provisional call that is confirmed or revised at
hour 48 and hour 72.

For regimes with "immediate" or sub-24-hour
clocks, the first-hour team must notify from the
first hour or defend why awareness had not yet
accrued.

## 4.6 Multi-jurisdiction incidents

A specific operational problem: an incident at a
firm with operations in multiple jurisdictions
can simultaneously trigger notifications under
different regimes with different timelines and
different content expectations.

The matrix row structure handles this
mechanically: each regime is a row; the response
consults every applicable row. The operational
problem is not identification but **coordination**:

- The content must be *consistent* across
  notifications even where the formats differ.
  A regulator in jurisdiction A will see the
  notification sent to the regulator in
  jurisdiction B at some point; divergent
  narratives undermine the firm's credibility
  in both.
- The sequencing may matter. In some regimes
  (e.g., disclosure under the SEC
  cybersecurity rule), the public disclosure
  is the first thing the markets learn;
  pre-disclosure private notifications to
  other regulators must be timed to not
  create selective-disclosure risk.
- The approvals must align. If the EU
  notification requires CAO + GC + CRO sign-
  off but the US notification requires CISO
  + GC + CFO, parallel notifications under
  deadline pressure can produce either
  bottlenecks (one GC) or inconsistencies
  (different GCs approving different content).

The pre-computed matrix includes a
multi-jurisdictional index: for each
classification, which regimes apply, in what
sequence, with what consistency expectations, and
which approvers overlap. Ex-02 in this module's
exercises builds this explicitly.

## 4.7 Customer notification

Customer notification deserves its own treatment
because it operates on a different logic than
regulator notification. Four considerations:

- **Timing.** Too early may produce panic
  without resolution — customers are told
  something happened but there is no path yet
  for them to act on it. Too late may produce
  trust loss when customers discover the
  issue independently (via media, a
  regulator's disclosure, or another
  customer's social-media post). The right
  window is usually constrained by regulatory
  timelines (GDPR Art. 34, state breach-
  notification laws) but has to balance the
  two.
- **Tone.** Honest about what happened, what
  is being done, what customers should do.
  Corporate-euphemism language that minimises
  the harm is read by customers as evasion and
  by regulators as inadequate disclosure.
  [`mod-105`](../mod-105-responsible-ai-and-ethics/README.md)
  Ex-04 (contestability) connects directly:
  customers affected by the incident need
  recourse paths that are clear and
  operational, not just acknowledgments.
- **Channel.** Match the affected population's
  channels — email where email is the
  primary; postal for regulatory-mandated
  mail; in-app messaging for digital-first
  services; direct call for high-touch
  relationships.
- **Coordination with the broader matrix.**
  Customer notification cannot precede
  regulatory notification in some regimes
  (where the regulator must be informed
  first), cannot lag it in others, and must
  be aligned in content with it in all. The
  matrix row for customer notification
  references the regulatory rows it
  depends on.

Chapter 8 covers the enterprise-face
communication dimension of serious incidents,
including the press and public-communication
layers. The customer notification is the baseline;
public communication is the broader envelope.

## 4.8 Edge cases the matrix must address

Three edge cases the matrix explicitly addresses,
because they predictably arise and because getting
them wrong under incident pressure is costly.

- **Vendor-side incident.** The LLM vendor
  announces a vulnerability or a model-swap
  that caused unexpected behaviour; the firm
  consumed the vendor's product and
  experienced the downstream effect. The
  firm's notification obligations do not
  defer to the vendor's; the firm notifies
  under its own regimes based on the effect
  the firm's customers experienced. The
  matrix row names this explicitly.
- **Discovery during examination.** A
  regulator discovers an incident during their
  own examination before the firm has
  independently detected and classified it.
  The firm's notification posture under this
  scenario differs from the detect-first
  scenario — the regulator is already aware,
  so the timeline is effectively zero for
  that regulator; other regulators' clocks
  are still running from the firm's point of
  awareness. The matrix names this.
- **Determination that an event is not an
  incident.** The matrix row includes
  explicit *no-notification-required*
  determinations where appropriate, with the
  reasoning captured. Programs that treat
  silence as the default produce ambiguity
  about whether the matrix was consulted or
  the obligation was missed.

## Summary

- The notification matrix is the pre-computed
  decision aid that lets the response team
  consult rather than interpret regulatory
  obligations under incident pressure.
- Seven dimensions per obligation: recipient,
  trigger, timeline, lead, format, supporting
  evidence, approvals required.
- Six regime families most commonly apply in
  2026: EU AI Act Art. 73, NYDFS Part 500
  §500.17, GDPR Arts. 33 and 34, sector-
  specific (SR 11-7, SEC cybersecurity rule,
  FDA SaMD, NAIC Model Bulletin), internal
  (Board, Risk Council), and contractual
  (customer, vendor).
- Pre-computation is the discipline: author at
  quiet times, update on triggers (new
  regulation, new jurisdiction, matrix defect),
  review quarterly as a joint CAO +
  Compliance + CISO + DPO + GC working
  meeting.
- The matrix is itself evidence (per
  mod-108): versioned, signed, retained,
  retrievable. It must survive missed-
  notification, false-positive, and multi-
  regime inquiries.
- Awareness is a judgment call across every
  regime. Three operational patterns: notify
  provisionally with follow-up updates, notify
  with caveats, make the notification decision
  at the hour-24 revisit for 72-hour regimes.
- Multi-jurisdictional coordination demands
  content consistency, sequencing control, and
  aligned approvals across regimes.
- Customer notification follows a different
  logic — timing, tone, channel, coordination
  with the broader matrix. It cannot precede
  regulatory in some regimes.
- Three edge cases the matrix names
  explicitly: vendor-side incidents,
  discovery during examination, and
  no-notification-required determinations
  with reasoning.
