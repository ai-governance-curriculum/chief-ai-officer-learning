# Chapter 8 — Enterprise-Face Communication During a Serious Incident

## Why this chapter exists

Serious AI incidents produce a specific kind of
communication problem the earlier chapters did
not fully address. The response team is operating
on the technical and regulatory layer. The firm
as a whole — its CEO, its Board, its investors,
its customers, its regulators, the press — is
operating on the trust and narrative layer. The
two layers are coupled: what the response team
decides on hour 6 constrains what the CEO can
credibly say on day 2, and what the CEO says on
day 2 constrains what the firm has to deliver on
week 3.

Most AI programs under-prepare the enterprise-
face communication layer. The CAO function is
responsible for the technical narrative, so the
firm defaults to assuming the CAO function will
handle the external messaging too. In practice,
enterprise communications requires its own
specialists — Head of Communications, Chief
Marketing Officer, Investor Relations, legal
counsel — and the CAO function's role is to
*supply* those specialists with content and
*constrain* them to say things the technical
response can defend. The chapter teaches that
boundary.

Four audiences receive distinct communication
during a serious incident: the **CEO**, the
**Board**, the **press / public**, and
**customers**. Each has a different information
need, a different cadence, a different format,
and a different approval chain. The chapter
walks each and names the CAO function's
specific contribution.

## 8.1 Why enterprise communication is a CAO concern

Three reasons the CAO function cannot delegate
enterprise communication wholly to Communications
or Investor Relations.

- **Technical accuracy.** Public communication
  that contains inaccurate statements about the
  AI system creates liability on top of the
  incident itself. The CAO function is the
  only function with the depth to verify the
  technical accuracy of the public narrative.
- **Regulatory consistency.** The regulatory
  notifications (Chapter 4) and the public
  communications must be consistent in
  content. A customer notification that
  minimises what the regulator was told
  creates a specific regulatory finding —
  that the firm's external communications
  misrepresented what it had told the
  supervisor.
- **Longitudinal consistency.** What is said in
  the first public statement must be
  consistent with what is said at week 3 and
  with what the post-incident review (Chapter
  6) ultimately concludes. The CAO function's
  understanding of the incident's technical
  shape is what keeps the narrative from
  drifting into statements the firm will
  later have to retract.

The pattern that works: Communications and the
CAO function co-author the external narrative.
Communications owns tone, channel, and the
corporate-communication craft; the CAO function
owns technical accuracy, regulatory alignment,
and longitudinal consistency. Each has a veto
within their lane. Disagreements escalate to the
CEO (or GC where the dispute is a legal-
communications boundary).

## 8.2 The CEO briefing

The CEO is briefed first and most frequently.
For a material incident, the CEO briefing
cadence is:

- **First briefing within hours of the
  incident's classification as material.**
  Not after the first notification is sent;
  not after containment is in place; within
  hours of the materiality determination.
- **Daily during the acute phase** (first
  48–72 hours) at a specific time, in a
  specific format.
- **Twice-weekly during the response phase**
  (days 3 through resolution).
- **Weekly** until the post-incident review
  is complete.
- **On-demand** when a significant development
  occurs (new regulator engagement, new
  media attention, new scope revision).

The content of each briefing has a specific
structure:

1. **What happened.** One paragraph. Current
   understanding.
2. **What we are doing.** Current containment
   posture, current notifications made,
   current investigation state.
3. **What is likely to happen next.**
   Expected regulator engagement, expected
   media attention, expected customer
   response.
4. **What we need from you.** Decisions the
   response team needs the CEO to make or
   approvals the CEO needs to give.
5. **What we are watching for.** Specific
   indicators the response team is
   monitoring for escalation or
   de-escalation.

The briefing is 10–15 minutes maximum,
delivered in writing with a short verbal
follow-up. CEOs under incident pressure cannot
absorb 60-minute walk-throughs; they need the
briefing short enough to read and the response
team's time efficient enough to continue the
response.

The CAO function typically delivers the
briefing. For joint incidents, the CAO function
and the CISO co-brief. GC is present. The CEO
is the single named decision-maker at the
enterprise scale; the briefing's purpose is to
let them exercise that role.

## 8.3 The Board briefing

The Board — specifically the Audit Committee
and / or Risk Committee — is briefed on
materiality determination and on the response's
progress against commitments made to the Board.

Cadence:

- **Initial briefing** within 24 hours of
  materiality determination. The Audit
  Committee chair is briefed, who decides
  whether to convene the Committee.
- **Written update** at the next regular
  Audit Committee meeting (or sooner if the
  Committee convenes).
- **Final briefing** at the post-incident
  review's publication, including the
  review's recommendations and the
  implementation plan.

Content for the Board briefing is structured
differently than the CEO briefing. The Board
wants:

- **Materiality context.** Why this is being
  brought to the Board. The materiality
  thresholds the firm defined are applied
  explicitly.
- **Governance assessment.** Did the
  governance frameworks the Board approved
  (the AI Risk Council, the escalation
  thresholds, the response-team design)
  operate as designed? The honest answer
  may be "mostly yes, except for X."
- **Enterprise exposure.** Legal, regulatory,
  reputational, financial. Ranges where
  precise estimates are not available.
- **Management posture.** How the executive
  team is handling the incident, including
  cross-functional coordination.
- **The ask.** What the Board is being asked
  to do — acknowledge, approve, convene,
  disclose. Boards act; they do not simply
  receive.

The Board briefing has a privilege dimension
GC must attend to. Board communications are
discoverable in some circumstances; the briefing
format and the record kept are structured with
privilege considerations in mind. GC is in the
room; GC approves the written content.

The CAO function typically does not deliver
the Board briefing directly. The CEO delivers
(for the executive summary) with the CAO
function present for technical questions. GC
is present throughout. For incidents where the
AI dimension is the dominant exposure, the CAO
function may deliver sections of the briefing
directly at the CEO's request.

## 8.4 The press / public communication

Press and public communication is where
enterprise communication becomes most high-
stakes and most CAO-constrained.

Three decisions the firm must make early.

### 8.4.1 Whether to disclose

Not every incident requires public disclosure.
Regulatory disclosure (per Chapter 4) is
mandatory where triggers are met; public
disclosure beyond the regulatory minimum is
discretionary and depends on:

- **Whether the incident is likely to become
  public anyway.** Patterns surfaced by
  external researchers, regulators, or
  customers tend to reach public awareness
  with or without firm disclosure. Pre-
  emptive disclosure under the firm's
  control is strongly preferable to the firm
  reacting to someone else's framing.
- **Whether customers / public need to act.**
  If the public needs to take action to
  protect themselves (change a password,
  verify a transaction, seek alternative
  medical treatment), the public must be
  told. Non-disclosure in such cases is both
  harmful and legally exposed.
- **Whether disclosure is required under
  securities law.** For public companies,
  the SEC cybersecurity disclosure rule
  (2023) requires Form 8-K for material
  cybersecurity incidents; some AI
  incidents meet this threshold.

### 8.4.2 When to disclose

If disclosure is going to happen, timing
decisions are shaped by:

- **Regulatory sequencing requirements.**
  In some regimes, regulators must be
  informed before the public; in others
  (securities), public disclosure comes
  first after regulators have been briefed.
- **Response readiness.** Public disclosure
  of an incident the firm has not yet
  contained produces panic without
  resolution. Public disclosure after
  containment allows the firm to answer
  the question "what are you doing about
  it" with "we have contained it and are
  investigating."
- **Narrative control.** Pre-emptive
  disclosure before external parties
  surface the issue gives the firm
  narrative control; reactive disclosure
  after external surfacing gives narrative
  control to the first external voice.

### 8.4.3 What to say

A working public statement has four properties:

- **Honest about what happened.** No
  corporate euphemism that minimises harm;
  honest naming of what went wrong.
  Minimising language is read by regulators
  as inadequate disclosure, by customers
  as evasion, by the press as material for
  the next story.
- **Specific where specific is possible.**
  Specific numbers (customers affected,
  period covered, actions being taken)
  where known; honest ranges where only
  ranges are known; honest "we do not yet
  know" where that is the truth.
- **Clear on what customers / public should
  do.** The specific actions, with the
  specific support channels, with the
  specific timelines.
- **Signed by a specific executive.** For
  the most serious incidents, the CEO; for
  less-material, a named executive. "The
  company regrets" without a named signatory
  reads as evasive.

The CAO function reviews the statement for
technical accuracy before release. The GC
reviews for legal exposure. Communications
reviews for channel and tone. The CEO approves.

For material incidents, the statement is
accompanied by:

- A **customer-facing FAQ** addressing the
  specific questions customers will have.
- A **support channel** staffed to handle
  the volume. Serious-incident support
  volume can be 10–100× normal; the
  response plan anticipates this.
- A **press-briefing plan** for the inquiries
  the statement will generate. Spokesperson
  (not the response-team lead; a designated
  spokesperson), on-the-record vs.
  background, cadence.

## 8.5 Customer communication (the detailed form)

Chapter 4 §4.7 covered customer notification at
the regulatory level. The enterprise-face
customer communication is a broader envelope.

Four audiences within the customer base:

- **Affected customers.** Customers whose
  specific accounts, cases, or interactions
  were affected by the incident. Direct
  individual notification, often with a
  specific individualised remedy.
- **At-risk customers.** Customers in the
  cohort that could have been affected but
  the firm has not yet confirmed individual
  impact. Notification is more general;
  action may be optional or precautionary.
- **Unaffected customers.** Customers who
  may hear about the incident through the
  public communication but who do not need
  to act. Communication is at the public-
  statement level; direct individual
  outreach is not warranted.
- **Prospective customers.** Not current
  customers but considering becoming
  customers. Will hear about the incident
  through press and public communication;
  the firm's broader narrative response
  shapes their perception.

Each audience gets a different communication,
with content, channel, and support path
calibrated. The CAO function contributes
technical accuracy to all four; Communications
owns the drafting and channel execution; the
business units own the individual customer
relationships for the affected and at-risk
categories.

Contestability — the recourse paths from
[`mod-105`](../mod-105-responsible-ai-and-ethics/README.md)
— becomes directly relevant for affected
customers. The communication to affected
customers must include the recourse path, not
just the apology. Programs that treat the
communication as a stand-alone message rather
than an entry to the recourse process produce
customer frustration that becomes the next
regulatory finding.

## 8.6 Internal employee communication

A separate audience that is easy to under-
prepare: **the firm's own employees**.

Employees are hearing about the incident from
customers, from the press, from the public
statement. If they are not briefed internally,
they will:

- Make statements to customers that are
  inconsistent with the firm's position
  (because they do not know the firm's
  position).
- Make statements to the press (even
  casually, even on social media) that
  create liability.
- Lose confidence in the firm, including the
  specific confidence that would let them
  support the response.

Internal communication is routed through
Communications and Human Resources, with the
CAO function contributing content. The
communication:

- States what happened at the level the
  public statement states.
- States what the firm is doing.
- States what employees should and should
  not say — and specifically where to
  route questions they receive.
- Acknowledges that employees may have
  concerns about their own exposure and
  identifies the channel for raising those
  concerns.

The timing matters: internal communication is
ideally released simultaneously with the
public statement, not after. Employees learning
about their firm's incident from a news story
is a specific trust failure.

## 8.7 Regulator communication beyond the formal notification

Beyond the formal notifications from Chapter 4,
regulators often engage with the firm during a
serious incident in less-formal ways:

- Phone calls from the regulator asking for
  updates between formal notifications.
- Requests for additional information under
  the regulator's ordinary powers.
- Requests to meet.
- In the extreme, on-site presence during
  the incident response.

The firm's posture:

- **Candid.** Regulators distinguish between
  firms that are candid and firms that are
  managing them. Candour builds the
  regulatory relationship that will matter
  for the next incident.
- **Prepared.** Requests get specific
  responses, delivered on schedule, in the
  format the regulator expects.
- **Consistent with the formal
  notifications.** What is said in a phone
  call must align with what was formally
  filed.
- **Documented.** Regulator interactions
  during an incident are themselves
  evidence. The response team's record
  includes every regulator interaction with
  time, participants, substance, and
  commitments made.

The CAO function typically leads AI-specific
regulator engagement during an incident; the
Chief Compliance Officer or GC leads cross-
regime engagement. For enterprise-scale
engagement (e.g., state attorneys general,
cross-agency inquiries), the GC leads with the
CAO function contributing.

## 8.8 The communication cadence as a program

A working program does not design communication
on the fly during an incident. It has:

- **A standing communication plan** for
  serious incidents, developed at program
  quiet times with Communications, GC,
  Investor Relations, HR, and the CAO
  function. The plan specifies the
  audiences, the cadences, the approval
  chains, the format templates.
- **Named spokespeople** for each audience
  with specific messaging training.
- **A pre-approved first statement template**
  that can be customised to the specific
  incident in hours, not days. The template
  is not generic — it is specific to a
  classification and a scenario — and
  there may be several templates per
  classification.
- **A customer-notification process** that
  can be executed at scale (10,000 to
  10,000,000 notifications depending on the
  firm's size). Not improvised; practised
  via the Chapter 7 tabletop exercises.

Programs that author the communication plan
during an incident produce communication that
is slow, inconsistent, and defensive.
Pre-planning is the only way to get this right
under the time pressure a serious incident
imposes.

## 8.9 What the CAO function specifically must not do

A boundary worth drawing explicitly:

- The CAO function **does not** become the
  firm's spokesperson. The CAO is a
  technical executive, not a communications
  executive. The firm's spokesperson is the
  CEO (for the most serious), a designated
  spokesperson (otherwise), or the Chief
  Communications Officer. The CAO
  contributes content and reviews for
  technical accuracy.
- The CAO function **does not** make
  disclosure decisions unilaterally. The
  decision whether and when to disclose is
  the CEO's (for public), the Audit
  Committee's (for Board-level), or the GC's
  (for securities-law triggers). The CAO
  function contributes the technical
  assessment that informs the decision.
- The CAO function **does not** engage with
  individual journalists directly on
  attribution. Press engagement goes through
  Communications, who may bring the CAO
  function into interviews under
  Communications' direction.
- The CAO function **does not** communicate
  outside the approved plan. The temptation
  to clarify technical details on social
  media or in public forums during an
  incident is specifically dangerous; off-
  plan communication by any executive
  produces inconsistencies the response
  cannot defend.

The CAO function's role is to make the
communication plan technically correct and
to supply content under the plan — not to
substitute for the communication function.

## Summary

- Enterprise-face communication during a
  serious incident has four audiences — CEO,
  Board, press / public, customers — each
  with distinct information needs, cadences,
  formats, and approval chains.
- The CAO function cannot delegate enterprise
  communication wholly to Communications or
  Investor Relations. Technical accuracy,
  regulatory consistency, and longitudinal
  consistency require CAO function
  contribution.
- CEO briefings: first within hours of
  materiality determination; daily during
  acute phase; weekly through resolution.
  Short, structured, written with verbal
  follow-up.
- Board briefings: initial within 24 hours
  of materiality; written update at next
  Audit Committee; final at post-incident
  review. Content is governance-oriented
  (materiality, framework operation,
  enterprise exposure, management posture,
  ask).
- Press and public communication requires
  three early decisions: whether to disclose,
  when to disclose, what to say. A working
  statement is honest, specific, clear on
  what the public should do, signed by a
  specific executive.
- Customer communication has four audiences:
  affected, at-risk, unaffected,
  prospective. Different communications for
  each. Contestability from mod-105 is the
  entry point for affected customers.
- Internal employee communication is often
  under-prepared. Routed through
  Communications and HR with CAO function
  content; released simultaneously with
  public statement.
- Beyond formal notifications, regulators
  engage during serious incidents. The
  firm's posture is candid, prepared,
  consistent with formal notifications,
  documented.
- A working program has a standing
  communication plan, named spokespeople,
  pre-approved first-statement templates,
  and a customer-notification process that
  scales. Pre-planning is practised via
  Chapter 7 tabletop exercises.
- The CAO function does not become the
  firm's spokesperson, does not make
  disclosure decisions unilaterally, does
  not engage journalists directly, does
  not communicate outside the approved
  plan. The CAO function contributes
  content and reviews for technical
  accuracy.
