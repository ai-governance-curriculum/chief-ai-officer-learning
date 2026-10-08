# Chapter 5 — Contestability and Recourse

## Why this chapter exists

Transparency (Chapter 4) tells an affected party what
the system did. Contestability lets them do something
about it. The two are different disciplines and
programs commonly conflate them — producing explanations
without recourse mechanisms, or recourse mechanisms
without the explanations required to use them.

This chapter builds contestability as a *design
property*, not a complaints process bolted on at the
end. The affected-party's perspective is primary
throughout: a system that is "contestable" in the view
of its designers but opaque, slow, and expertise-
demanding from the view of the affected party is not
contestable. The chapter also distinguishes
contestability from the adjacent concept of *recourse*
— what the affected party can do *outside* the
contestation channel — and makes the interaction
between the two explicit, because designing one
without the other produces predictable failures.

## 5.1 What contestability requires

Contestability requires six things that AI systems
often lack. A system missing any of these has not
implemented contestability; it has implemented a
complaints inbox.

1. **A named decision** the affected party can
   identify. "The bank denied my application" is a
   named decision. "The system surfaced concerns about
   your transaction" is not — it is unclear what is
   being contested.
2. **A named decider** the affected party can address.
   "Speak to your loan officer" is a named decider.
   "The AI recommended denial; the underwriter agreed"
   leaves the affected party unclear whom to contest.
   A named human role is required; "the algorithm" is
   not a decider.
3. **A path** for raising the contestation. What form?
   What channel? What required information? Explicit
   enough that the affected party can act without
   expert help.
4. **A timeline** for resolution. Within what window
   does the contestation get acknowledged, reviewed,
   and resolved? The timeline must be bounded by
   policy, not left to case-by-case discretion.
5. **A resource** for the affected party. Free?
   Mediated? Does the affected party need their own
   counsel? Is in-house advocacy available? A
   contestation process that requires expertise the
   affected party does not have, with no help
   provided, is contestation on paper only.
6. **An outcome** that can actually change the
   decision. Override? Re-evaluation? Compensation?
   Documentation of the complaint? A contestation
   process whose only outcome is "the decision stands"
   is procedurally a confirmation channel, not a
   contestation channel.

The six elements are *all* required. A system that has
five of the six is a system where one element silently
unravels the others.

### 5.1.1 Example — the six elements made specific

A claims-triage contestability example (continuing the
mod-104 and mod-105 Exercise 04 context):

| Element | Specification |
|---|---|
| Named decision | "The AI classification flagged your claim for fraud review, resulting in delayed settlement." Not "your claim was reviewed." |
| Named decider | Claims Review Specialist (role in Claims Operations, independent of the AI team). Named at the point the fraud-review flag is raised. |
| Path | Written form (web + mailed) OR phone call to the Claims Review Specialist line. Required info: policy number, claim ID, nature of objection. |
| Timeline | 2 business days for acknowledgment; 5 business days for resolution. Documented in the policy. |
| Resource | Free. Claims Operations provides a plain-language explainer. Policyholder may bring an attorney but need not. |
| Outcome | Possible outcomes: fraud flag removed and claim re-routed to standard review; fraud flag confirmed with specific stated reasons; claim escalated to supervisor review if the Specialist is uncertain. |

Any of the cells left as "to be determined" collapses
contestability for the entire process. Exercise 04
asks you to produce this table for a specific context.

## 5.2 Recourse

Recourse is what the affected party can do *outside*
contestation. The two interact: a system with strong
contestation but weak recourse forces every concern
into the contestation channel; a system with strong
recourse but weak contestation lets the affected party
route around the formal process.

Common recourse mechanisms:

- **Modifying the inputs the system uses.** "I can
  pay off this card to improve my credit profile and
  reapply in three months." Requires the explanation
  to identify the modifiable inputs.
- **Waiting for the system to re-evaluate.** "My
  credit score will update after the next reporting
  cycle; I can reapply then." Requires the system's
  re-evaluation cadence to be known to the affected
  party.
- **Choosing a different channel.** "I can apply at a
  competitor." Requires the market to actually offer
  alternatives (less reliable in concentrated
  markets).
- **Using a different relationship.** "I can ask my
  banker directly rather than through the online
  underwriter."
- **Switching providers.** For deployed systems, the
  option of leaving the service entirely. Requires
  low switching cost; often unavailable in healthcare,
  employment, housing contexts.

Recourse design is often invisible to the system
designer because recourse is *what the affected party
does to work around the system*. Honest CAO ethics work
surfaces recourse explicitly and assesses whether the
recourse options are reasonable. A system where
"recourse" means "apply to a competitor" is a system
with no effective recourse if there is no competitor —
and the CAO function should name this.

### 5.2.1 Recourse-contestation interaction

Three patterns the CAO function should watch for:

- **Recourse-only, contestation-weak.** The system
  tells the affected party what to do but not how to
  challenge the decision. Common in high-volume
  consumer services where contestation is operationally
  expensive. Risk: affected parties with legitimate
  grievances cannot surface them.
- **Contestation-only, recourse-opaque.** The system
  has a formal contestation process but the affected
  party cannot modify their position otherwise.
  Common in regulated settings where the firm optimises
  for formal compliance. Risk: contestation channel
  overloads; many contestations are really recourse-
  seeking.
- **Neither strong.** The system treats the affected
  party as a passive recipient. Common when the
  product team optimises for throughput. The CAO
  function has not functioned.

A working CAO ethics function assesses the recourse-
contestation interaction *as a system*, not each
element separately.

## 5.3 Contestability in regulated contexts

Several regulations explicitly require contestability
or elements of it:

- **EU AI Act Art. 14** — human oversight obligations
  for high-risk systems. Includes the ability of
  overseers to intervene, override, and interrupt the
  system.
- **EU AI Act Art. 86** — right to explanation of
  individual decisions for affected persons in
  specified high-risk uses.
- **GDPR Art. 22** — right not to be subject to
  decisions based solely on automated processing in
  specified cases, with conditions. Where Art. 22
  applies, the data subject has the right to obtain
  human intervention, express their point of view,
  and contest the decision.
- **CFPB / Reg B / ECOA** — adverse-action notices
  include the right to obtain the model's reasons.
  Not an explicit contestation requirement, but the
  reasons-notice is upstream of consumer dispute.
- **FCRA** — consumers have the right to dispute
  inaccuracies in consumer-reporting data; AI systems
  consuming CRA data must support the dispute
  resolution process.
- **ADA / Section 508** — accessibility requirements
  that affect the *path* and *resource* elements for
  affected parties with disabilities.
- **Colorado SB 24-205** (2026) — includes
  requirements for consumer appeal of consequential
  decisions made with high-risk AI systems.

Where contestability is regulated, the design must meet
the regulation's specific requirements. Where it is
not, the program is making an ethical choice that the
regulator has not yet codified. The ethical choice is
not optional merely because the regulatory floor is
silent.

## 5.4 Contestability anti-patterns

A short field guide to patterns that look like
contestability but are not:

- **Contestation channels that route to the same
  model.** An automated appeals process that uses the
  same model re-evaluating the same inputs is
  procedurally a reconfirmation channel, not
  contestation. The decider changes nothing.
- **Contestation timelines that exceed the harm
  window.** An employment-decision contestation that
  takes 90 days to resolve while the affected party is
  unemployed is not effective. The timeline must be
  bounded materially shorter than the harm the
  decision creates.
- **Contestation that requires expertise the affected
  party does not have.** A contestation form that asks
  the affected party to identify which of the model's
  features were incorrectly weighted is asking the
  wrong party to do the work. Even a technically-
  perfect form is a barrier if it requires technical
  literacy.
- **Contestation without resourcing.** A contestation
  process that exists on paper but has no staffing is
  worse than acknowledging that contestation is not
  available — because the paper process creates a
  false sense of accountability.
- **Contestation outcomes that cannot change the
  decision.** If the only possible outcomes are
  "decision confirmed" or "decision confirmed with
  apology," the process is a complaint channel, not a
  contestation channel.
- **Contestation that requires waiving rights.** If
  the affected party must sign away their right to
  future legal action to use the internal contestation
  process, the mechanism is adversarial and the
  "contestation" framing is misleading.
- **Contestation only accessible to the technically
  savvy.** A contestation path that lives only on a
  web form, with no verbal channel, excludes affected
  parties who prefer or require non-digital contact.
  Multi-channel access is often a required feature,
  not a nice-to-have.

A contestability process should be explicitly tested
against this list. A documented statement of which
anti-patterns the process avoids and how it avoids
them is defensible evidence that the design was
intentional.

## 5.5 Building contestability in

The discipline: contestability is **a design property**,
not a feature added at the end. A system designed with
contestability in mind looks different from a system
that is otherwise complete and then has a contestation
page added.

### 5.5.1 Design properties that support contestability

- **Decisions are logged with sufficient context** that
  a human reviewer can re-evaluate without rebuilding
  the context. This includes the inputs the model saw,
  the model's output, and the operational step the
  output triggered.
- **Affected parties know they are being affected** by
  an AI system at the time of the decision. Silent AI
  use breaks contestability by removing the predicate
  — the affected party does not know there is
  something to contest.
- **The reviewing role is named and reachable**
  through at least two channels (one written, one
  verbal). The role is independent enough of the
  decision pipeline that it can disagree.
- **The timeline is bounded by policy**, with the
  bound tied to the harm window of the decision.
- **The outcome is reported** to the affected party,
  including the reasons for the outcome.
- **Contestation outcomes feed back into the system**.
  A pattern of successful contestations on a specific
  axis is a signal of model drift or latent bias; the
  pattern should surface to the model-owner and the
  AI Review Board as a monitoring signal.

### 5.5.2 Design properties that undermine contestability

Equally important to name:

- **Opaque pipelines** where the decision cannot be
  reconstructed after the fact.
- **Unlogged intermediate steps** (e.g., a reranker
  that silently filters candidates before a visible
  decision).
- **Over-general output framing** where the system's
  recommendation is a composite that cannot be
  challenged on any specific component.
- **Chain-of-model pipelines without per-step
  contestability** — the user contests the final
  output, but the error was in an earlier step with no
  surface for contestation.

A system with any of these properties will produce
contestations that cannot be meaningfully resolved,
which trains the organisation and the affected
population to stop using the contestation channel.

## 5.6 Contestability in the deployment lifecycle

Contestability intersects with the lifecycle at several
points:

- **Pre-deployment design review** — the AI Review
  Board asks: who is the affected party, how do they
  know they are affected, and what is their
  contestation path? If any of the three are not
  specified, the system is not approved.
- **Launch** — the contestation process is live and
  staffed on day one, not promised for a later
  release.
- **Monitoring** — contestation volume, outcome
  distribution, and resolution time are tracked as
  operational metrics alongside model performance.
- **Incident response** (mod-110) — a contestation
  that reveals a systematic flaw is routed as an
  incident, not just handled as a one-off.
- **Model retirement / change** — contestability for
  affected parties on retiring versions does not
  terminate when the version is retired; outstanding
  contestations are honored.

A program whose contestability discipline exists only
at pre-deployment review has a contestation page, not
a contestability function.

## 5.7 Measuring contestability

The uncomfortable truth: contestability is harder to
measure than fairness or explainability. Several
imperfect metrics are useful; none is sufficient alone:

- **Volume of contestations** — low volume can mean
  the system is working, or that affected parties
  cannot find the contestation channel. Monitor
  both interpretations.
- **Outcome distribution** — percentage of
  contestations that result in a change. Very low
  (near-zero) suggests the process is confirmatory;
  very high suggests the original decisions are
  systematically problematic.
- **Resolution time** — distribution of time from
  contestation submission to outcome delivery, with
  the harm-window as the comparison baseline.
- **Access distribution** — contestation rates
  stratified by affected-party demographics,
  geographic access, device access. A pattern where
  contestation is used by only one subset of
  affected parties is a signal of access failures.
- **Qualitative review of contestations** — periodic
  review of a sample of contestation records (with
  appropriate confidentiality) to assess whether
  the written outcomes are actually responsive to the
  objections raised.

Contestability metrics belong in the mod-111 board
reporting pack as part of the ethics-performance
layer, not just the operational-performance layer.

## Summary

- Contestability requires six elements — named
  decision, named decider, path, timeline, resource,
  outcome — all specified, none left to case-by-case
  discretion.
- Recourse (what the affected party can do outside
  the contestation channel) is distinct from
  contestability. The two interact; both matter.
- Regulated contexts (EU AI Act, GDPR Art. 22, CFPB,
  FCRA, ADA, Colorado SB 24-205) codify specific
  requirements; the ethical obligation is not limited
  to the codified floor.
- Common anti-patterns — routing back to the same
  model, timelines exceeding the harm window,
  demanding expertise from the affected party, paper-
  only processes, confirmation-only outcomes — are
  predictable failures to design against.
- Contestability is a design property. A system
  designed for it looks different from a system that
  bolts a contestation page on at the end.
- Contestability intersects the deployment lifecycle
  at design review, launch, monitoring, incident
  response, and retirement — not only at review.
- Contestability metrics (volume, outcome
  distribution, time-to-resolution, access
  distribution, qualitative review) belong in the
  board reporting pack. See Exercise 04 to produce
  a contestability-process design for a specific
  context.
