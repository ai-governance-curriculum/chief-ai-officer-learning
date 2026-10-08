# Chapter 1 — What AI Incident Response Is (and Isn't)

## Why this chapter exists

Most organisations entering AI governance already have
an incident response function. The CISO's team has
operated under NIST SP 800-61 for years. The privacy
office knows GDPR Art. 33. Business continuity has
tabletop practice. The temptation — a reasonable one —
is to treat AI incidents as one more input to the
established pipeline: classify, notify, contain, close.

That treatment works for the easy half of the AI
incident landscape (classical security events against
AI infrastructure) and silently fails on the harder
half (bias, drift, hallucination, misuse,
substantive-decision failure). AI incidents violate
several assumptions the classical IR backbone depends
on: a discrete start and stop, a bounded set of
affected records, a single compromised component to
isolate, a single regulatory regime. A program that
runs AI incidents on pure classical IR *looks* orderly
until a regulator asks why the bias incident of
November was treated as closed in a week when it had
been operating for six months. A program that
abandons classical IR to "AI-native" improvisation
produces responses that cannot survive scrutiny for
different reasons: no evidence trail, no notification
discipline, no reproducible closure.

The discipline this module teaches is holding both:
inheriting classical IR where it applies and
substituting AI-specific practice where it doesn't.
This chapter draws the line between the two.

## 1.1 The classical IR backbone

NIST SP 800-61 Rev. 2 — the US federal reference
document for computer-security incident handling —
specifies a four-phase incident response lifecycle:

1. **Preparation.** Readiness before any incident:
   staffed response team, documented playbooks,
   tested tooling, exercised relationships with
   partners and regulators.
2. **Detection and analysis.** Identifying that an
   incident has occurred, scoping it, and
   classifying it. Includes the "is this real?"
   verification step.
3. **Containment, eradication, and recovery.**
   Stopping the incident from continuing, removing
   the cause, and returning the affected systems
   to normal operation.
4. **Post-incident activity.** The structured
   lessons-learned pass: what happened, what to
   improve, how the recommendations get
   implemented.

Plus a continuous fifth activity threaded through
all four — **coordination and communication** —
with internal stakeholders, external partners,
regulators, and (where applicable) the public.

The backbone is sound. Thousands of security
incidents a year run on it. AI programs that
*discard* it in favour of improvisation produce
ad-hoc responses that fail at evidence, timing, and
regulatory closure. The four phases, the
single-named-lead convention, the audit-trail
discipline, the structured lessons-learned pattern
— all of this transfers to AI IR and should be
inherited directly.

Sector regimes supplement the NIST backbone with
their own expectations. The FFIEC IT Examination
Handbook, FDA's incident reporting infrastructure
for medical devices, FINRA Rule 4530 for broker-
dealers, and NIS2 for EU-regulated essential and
important entities all layer on top of (not instead
of) the four-phase model. Classical IR is the
substrate; sector regimes are the overlays.

## 1.2 Five ways AI incidents differ

Five characteristics of AI incidents warrant
treatment the classical backbone does not
automatically produce. Each is a specific
operational implication, not a philosophical
observation.

### 1.2.1 The incident may lack a clean "stop" point

A classical breach has discrete events: adversary
in, adversary out, malware detected, system
restored. The response team can draw a timeline
with a start timestamp and an end timestamp. An AI
bias incident may have no discrete start: the
system was "working" the whole time, producing
outputs that were — on review — systematically
unfair for months. The containment question
"when did this stop" has no satisfying answer
because the thing never had a start event.

The operational implication: AI IR must distinguish
*discovery* from *onset*. The timeline of discovery
runs forward from detection; the timeline of impact
runs backward from onset. Post-incident reviews
that collapse the two mislead their readers.

### 1.2.2 Containment can degrade the system of care

Classical containment usually isolates a specific
compromised asset. The rest of the environment
continues to operate. AI containment may require
pausing or degrading the AI system itself —
turning off the triage recommender, disabling the
fraud scorer, falling back to manual review. Each
of these has costs: longer customer wait times,
untreated patients, missed fraud, dependent
downstream systems that assumed the AI tier was
present.

The operational implication: containment decisions
are *trade-offs*, not just risk-reduction moves.
The CAO function must defend containment postures
against counterfactual analysis in both directions
— the harm the AI system might have continued to
produce and the harm the containment itself
produced. Chapter 3 operationalises this.

### 1.2.3 Affected populations may be diffuse and
       identifiable only after analysis

A classical breach affects an enumerable set of
records: *2,348 customer records exfiltrated,
exhibit A is the list*. An AI bias incident may
have affected an unknown number of customers over
an unknown period in an unknown geographic pattern.
"Who was affected?" is itself a research question
that may consume much of the investigation.

The operational implication: notification timelines
anchored on *awareness of the incident* collide with
the fact that scope is itself a derived quantity.
Chapter 4 walks the regulatory treatment of this
collision; the short answer is provisional
notification with scope updates, not silence until
scope is fixed.

### 1.2.4 Multiple regulators apply simultaneously

Classical breaches often trigger one or two
notification regimes — cybersecurity authorities and
privacy supervisors. An AI incident at a
cross-jurisdictional firm may simultaneously
trigger EU AI Act Art. 73, GDPR Arts. 33–34, NYDFS
Part 500 §500.17, state insurance regulators under
NAIC Model Bulletin provisions, FDA under SaMD
adverse-event rules, SR 11-7 model-event
expectations with the OCC or FRB, SEC cybersecurity
disclosure under the 2023 rule, and customer-
contract notification obligations.

The operational implication: a notification matrix
must be pre-computed per incident class, not
re-derived per incident. Chapter 4 is the chapter
this implication produces.

### 1.2.5 The blame surface is broader

A classical security incident usually implicates a
specific component — a vulnerable server, a
mishandled credential, a misconfigured firewall.
Responsibility maps cleanly. An AI incident
implicates the model, the training data, the
deployment configuration, the operating policy,
the monitoring thresholds, the escalation
decisions, the vendor's upstream choices. Multiple
layers, multiple owners, multiple decisions each of
which contributed.

The operational implication: investigation
discipline (Chapter 5) must separate causation from
blame deliberately. Investigations that stop at
"the data scientist chose this threshold" miss the
systemic failures that let an unsafe threshold ship.
The classical five-whys discipline survives; the
NTSB-style separation of safety investigation from
disciplinary process must be made explicit.

## 1.3 What the CAO function does and does not run

The CAO function is **not** the enterprise's
incident response function. The CISO's team
operates incident response as a day-to-day
discipline, with staffed shifts, escalation
rotations, and tooling the CAO function will not
duplicate. The boundary (see also [`mod-107`](../mod-107-ai-security/README.md)
Chapter 5) is specific:

The CAO function **owns**:

- The **classification expectations** that drive
  routing — the taxonomy of security vs.
  AI-program vs. joint incidents developed in
  [`mod-107`](../mod-107-ai-security/README.md) §6.
- **AI-program-substantive response** for incidents
  classified as AI-program (bias, drift,
  hallucination, substantive-decision failures,
  misuse of the AI system).
- **Joint response co-lead** with the CISO for
  incidents classified as joint, per the boundary
  patterns in mod-107 Ch. 5.
- **AI-specific external notifications** — EU AI
  Act Art. 73 to the national competent authority,
  AI-specific regulator briefings, AI content
  within joint notifications.
- **Post-incident review** for the AI-program
  dimensions of every material incident, feeding
  the GOVERN loop ([`mod-103`](../mod-103-ai-risk-frameworks/README.md)
  §6).

The CAO function **does not**:

- Replace the CISO's operational IR function.
- Run parallel containment activities competing
  with the CISO's.
- Author security-engineering containment
  decisions on classical security dimensions.
- Lead enterprise regulatory notifications outside
  AI-specific territory (NYDFS Part 500 §500.17
  stays with the CISO; GDPR Art. 33 to the
  supervising DPA stays with the DPO; the CAO
  contributes AI content, not lead signature,
  on each).

This is the single most common structural mistake
in a new CAO function's first year: operating a
parallel incident response team that competes with
the CISO's. The failure mode is specific. In a real
incident the two teams end up on separate call
bridges, make inconsistent containment moves,
produce diverging timelines, and the regulator
later discovers two internal narratives that do not
reconcile. The boundary pattern is co-lead with
single named lead per activity, same as the other
peer boundaries ([mod-104 Ch. 6](../mod-104-model-risk-management/README.md),
[mod-107 Ch. 5](../mod-107-ai-security/README.md),
[mod-109 Ch. 6](../mod-109-compliance-operations/README.md)).

## 1.4 Where this module sits in the program

This module operationalises incident response for the
AI program. It depends on earlier modules and feeds
later ones.

Upstream dependencies the module assumes:

- The **classification taxonomy** from [`mod-107`](../mod-107-ai-security/README.md)
  §6, which routes incidents to the CISO, the CAO
  function, or joint response. Without a working
  taxonomy, the first-hour classification call in
  Chapter 2 has no scaffolding.
- The **evidence infrastructure** from [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md),
  which incident response produces evidence into and
  consumes evidence from. The audit ledger carries
  the detection event, the classification decision,
  the containment-posture decision, the notification
  log — every artifact Chapter 2 and Chapter 4
  produce.
- The **obligations register** from [`mod-102`](../mod-102-regulatory-landscape/README.md),
  which supplies the regulatory inputs to the
  Chapter 4 notification matrix.
- The **GOVERN loop** from [`mod-103`](../mod-103-ai-risk-frameworks/README.md)
  §6, which the Chapter 6 post-incident review feeds
  back into.
- The **compliance operations** discipline from
  [`mod-109`](../mod-109-compliance-operations/README.md),
  which supplies the control catalog incident
  response operates against.

Downstream flow this module produces:

- **Material incidents** become inputs to
  [`mod-111`](../mod-111-board-reporting/README.md)
  board-level reporting — the subject of the next
  module.
- **Post-incident findings** feed the responsible-AI
  ([`mod-105`](../mod-105-responsible-ai-and-ethics/README.md)),
  trust-architecture ([`mod-106`](../mod-106-trust-architecture/README.md)),
  and AI-security ([`mod-107`](../mod-107-ai-security/README.md))
  standards for revision.
- **Readiness assessments** from the Chapter 7
  tabletop discipline feed the operating-model
  decisions in [`mod-112`](../mod-112-cao-operating-model/README.md).

## 1.5 What this module owns, and doesn't

This module owns:

- The operational discipline of running AI
  incidents through all four NIST phases
  (Chapters 2, 3, 5, 6).
- The notification matrix pattern that compresses
  the obligations landscape into a decision aid for
  the response team (Chapter 4).
- The investigation discipline that produces
  program improvement rather than blame (Chapter 5).
- The post-incident review template pattern that
  survives external scrutiny (Chapter 6).
- The tabletop exercise pattern that tests
  readiness without over-investing in performance
  art (Chapter 7).
- The CAO-face communication discipline for the
  CEO, Board, press, and customers during a
  serious incident (Chapter 8).

This module does *not* own:

- The classification taxonomy itself (mod-107 §6).
- Firm-specific IR playbooks for a specific CISO's
  environment — those are a CAO × CISO joint
  deliverable, informed by this module.
- The evidence infrastructure the response consumes
  and produces into (mod-108).
- The enterprise-wide IR program the CISO operates
  (reference: FFIEC IT Examination Handbook,
  practitioner CISO sources). The AI slice
  integrates into that program.
- Classical cybersecurity-specific IR playbook
  content. This module teaches AI IR; classical IR
  is referenced to NIST SP 800-61 Rev. 2 and sector
  norms.

## Summary

- AI incident response inherits the four-phase
  NIST SP 800-61 backbone — preparation, detection
  and analysis, containment-eradication-recovery,
  post-incident activity — plus the cross-cutting
  coordination and communication activity.
- Five differences from classical IR drive the rest
  of the module: no clean stop point, containment
  degrades the system of care, affected populations
  are discovered rather than enumerated, multiple
  regulators apply simultaneously, the blame
  surface is broader.
- The CAO function does not replace the CISO's
  incident response. It owns classification
  expectations, AI-program-substantive response,
  joint co-lead on joint incidents, AI-specific
  external notifications, and post-incident review
  of AI-program dimensions. Parallel IR functions
  are the dominant first-year failure.
- The module depends on classification (mod-107
  §6), evidence (mod-108), obligations (mod-102),
  the GOVERN loop (mod-103), and compliance
  operations (mod-109). It feeds board reporting
  (mod-111) and the operating model (mod-112).
- Chapters 2 and 3 build the first-hour and
  containment discipline. Chapter 4 is the
  notification matrix. Chapters 5 and 6 build
  investigation and review discipline. Chapter 7
  is tabletop exercises. Chapter 8 is enterprise-
  face communication during serious incidents.
