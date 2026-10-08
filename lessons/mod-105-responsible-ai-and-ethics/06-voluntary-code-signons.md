# Chapter 6 — Voluntary Codes at CAO Scope

## Why this chapter exists

The CAO's external Responsible AI narrative — the one
the firm presents to regulators, customers, press,
investors, and the public — frequently includes
reference to a voluntary code the firm has signed or
affiliated with. "We are signatories to the G7 Hiroshima
Code of Conduct." "We participate in the EU AI Office's
GPAI Code of Practice." "We are a Partnership on AI
member." These statements are *commitments*, not
decorations. Each carries scope, obligations,
reporting cadence, and reputational consequences for
non-compliance.

Many CAOs inherit sign-ons that pre-date their
appointment, or are asked by the CEO or Board to sign
on to a code without a developed sense of what the
sign-on entails. This chapter is the orientation. The
goal is not to recommend particular codes — that is
context-specific — but to equip the CAO to answer four
questions for each one: *what did we commit to*, *what
do we actually have to do*, *what do we actually get*,
and *under what conditions should we walk back*.

## 6.1 Why voluntary codes exist

Three distinct things are happening in the voluntary-
code landscape, and the CAO's response to each is
different.

- **Pre-regulatory anchoring.** Codes developed in
  advance of statutory regulation (or in jurisdictions
  without equivalent statute) serve as a floor the
  industry can be held to while governments catch up.
  The G7 Hiroshima Code of Conduct is the clearest
  example — issued October 2023, during the policy
  window between early LLM deployments and the EU AI
  Act's final adoption.
- **Statutory-compliance scaffolding.** Codes developed
  under a specific statute as the operational
  implementation of statutory obligations. The EU AI
  Office GPAI Code of Practice (under EU AI Act Art.
  56) is the clearest current example — a signatory
  gets presumption of compliance with specific
  statutory obligations.
- **Industry-coordination scaffolding.** Codes and
  consortia that coordinate industry on shared
  technical patterns and shared benchmarks. MLCommons
  AI Safety and Partnership on AI are the clearest
  examples — multi-stakeholder bodies that produce
  benchmarks, white papers, and shared practice
  references.

A CAO reading a voluntary-code request should first
place it in one of these three categories, because
each category implies different stakes and different
reporting rhythms.

## 6.2 The specific codes a CAO must know

Not an exhaustive list — this is the set most CAOs
encounter in 2026-era external narrative.

### 6.2.1 OECD AI Principles (2019, updated 2024)

- **Status.** International instrument, adopted by
  OECD member countries plus adherent non-members.
  Country-level signatory list, not organisation-
  level — a company does not formally "sign" the OECD
  AI Principles.
- **Content.** Five values-based principles
  (inclusive growth, human-centered values, transparency
  & explainability, robustness & safety,
  accountability) plus five recommendations for
  national policies. The 2024 update extended the
  principles' coverage of general-purpose AI and
  safety.
- **CAO-scope relevance.** A company whose
  jurisdictions have adopted the Principles should
  reference them as the shared *international* vocabulary
  for Responsible AI, not as an operational standard
  the company is subject to.
- **What signing on means.** For a company, nothing
  directly. For a country, a commitment to work the
  principles into national AI policy. The common
  misstatement — "we are OECD-aligned" meaning the
  company's practices embody the principles — is
  defensible but should not be presented as a formal
  commitment.

### 6.2.2 G7 Hiroshima AI Process Code of Conduct (October 2023)

- **Status.** Multi-stakeholder voluntary code. The
  Code of Conduct for Organisations Developing Advanced
  AI Systems is one of three deliverables of the G7
  Hiroshima AI Process (the Guiding Principles for
  Organisations Developing Advanced AI Systems and
  the Hiroshima Process Reporting Framework are the
  others).
- **Content.** Eleven actions for organisations
  developing *advanced* AI systems (interpreted as
  state-of-the-art foundation models and generative
  AI). Themes: pre-deployment risk assessment,
  pre- and post-deployment testing, vulnerability
  reporting, incident sharing, invest in robust
  security controls, prioritise research on societal
  risks, develop and deploy mechanisms for content
  authentication and provenance, publicly report
  capabilities and limitations, invest in evaluation,
  support international technical standards, implement
  appropriate data input measures.
- **Reporting.** OECD hosts a reporting framework
  companies use to disclose how they implement each of
  the eleven actions. Participation is voluntary;
  reports are public.
- **CAO-scope relevance.** For organisations developing
  foundation models, this is a widely-cited baseline
  commitment. The reports become reference material
  cited by regulators, academics, and press.
- **What signing on means.** The CAO (or equivalent
  role) is on the record for the content of the report.
  Material divergence between the report and the
  firm's actual practice is a reputational and
  governance risk — treat the report with the same
  care as a regulatory filing.
<!-- needs-research: current count of G7 Hiroshima reporting-framework participants and link to the OECD-hosted repository. -->

### 6.2.3 EU AI Office GPAI Code of Practice (2025)

- **Status.** Statutory-compliance scaffolding under
  EU AI Act Art. 56. The AI Office (established 2024
  within DG CNECT) convened working groups to draft
  the Code; the final text was adopted in 2025 after
  multi-stakeholder consultation.
- **Content.** Operational implementation of the EU AI
  Act obligations on providers of general-purpose AI
  models under Art. 53 and (for systemic-risk models)
  Art. 55. Covers model documentation, copyright
  compliance obligations, systemic-risk assessment and
  mitigation, cybersecurity measures, incident
  reporting.
- **Reporting.** Signatories commit to specific
  operational practices under the Code; the AI Office
  monitors adherence. Divergence from signed
  commitments triggers AI Act enforcement pathways
  (not merely reputational consequences).
- **CAO-scope relevance.** For organisations placing
  general-purpose AI models on the EU market, this is
  not optional in practice — the alternative is
  demonstrating compliance with Art. 53/55 directly
  without the Code's presumption. For organisations
  not placing GPAI models on the EU market, this is
  not applicable but is often cited as a reference
  for internal practices.
- **What signing on means.** This is the sign-on
  closest in character to a regulatory commitment.
  Treat it with full compliance-grade rigor.
<!-- needs-research: final adoption date of the GPAI Code of Practice and the exact AI Office signatory list as of 2026. -->

### 6.2.4 MLCommons AI Safety and the AILuminate benchmark

- **Status.** Industry-coordination consortium (not
  government body). MLCommons is the organisation
  behind the MLPerf benchmarks; the AI Safety Working
  Group developed AILuminate as a reproducible safety
  benchmark for text-to-text LLMs.
- **Content.** AILuminate v1.0 (December 2024) measures
  LLM responses across hazard categories (violent
  crimes, sex-related crimes, child sexual
  exploitation, suicide & self-harm, hate, indiscriminate
  weapons, intellectual property, defamation, privacy,
  specialized advice, non-violent crimes, sexual
  content). Scores are published publicly for models
  tested.
- **Reporting.** Participation ranges from working-
  group membership to running the benchmark and
  publishing results to co-authoring the benchmark
  spec.
- **CAO-scope relevance.** For organisations
  developing or deploying LLMs, participation (or
  reference to AILuminate results) provides a
  shared vocabulary for the "did you test for
  safety" question. The benchmark is not
  comprehensive — it covers specific hazard
  categories and is one benchmark among many.
- **What signing on means.** Membership obligates
  the firm to the consortium's working-group
  governance. Publishing an AILuminate score commits
  the firm to the published number as an operational
  claim.
<!-- needs-research: current MLCommons AI Safety Working Group member list and AILuminate benchmark release cadence through 2026. -->

### 6.2.5 Partnership on AI (PAI)

- **Status.** Multi-stakeholder non-profit, founded
  2016. Members include industry, civil society, and
  academic institutions. Membership tiers vary; each
  carries different participation obligations.
- **Content.** PAI publishes frameworks, case studies,
  and best-practice documents across its research
  focus areas (AI, labor, and the economy; safety-
  critical AI; fairness, transparency, accountability;
  media integrity; among others). Notable publications:
  Responsible Practices for Synthetic Media (2023),
  the ABOUT ML initiative on model documentation,
  Fairness, Transparency and Accountability
  guidelines.
- **Reporting.** Members contribute to working groups,
  co-author frameworks, and are referenced in PAI
  publications. Participation is public.
- **CAO-scope relevance.** PAI membership is a signal
  of participation in the multi-stakeholder
  Responsible-AI discourse. The published frameworks
  are useful operational references, not binding
  standards.
- **What signing on means.** The commitment is to
  participation and good-faith engagement with
  working-group output. There is no compliance
  dimension; divergence from a PAI framework is not
  a violation.
<!-- needs-research: current PAI membership tier structure and the 2024-2026 publication list. -->

### 6.2.6 Others a CAO may encounter

- **UK AI Safety Institute (now AI Security Institute)
  commitments.** Firms deploying frontier models in
  the UK may be party to voluntary pre-deployment
  evaluation commitments with the Institute. Scope
  and content are evolving.
- **Seoul AI Safety Summit commitments (May 2024).**
  16 companies committed to Frontier AI Safety
  Commitments at the Seoul Summit — thresholds for
  risk, publication of safety frameworks, and
  reporting. Follow-on commitments were made at
  subsequent summits.
- **White House Voluntary AI Commitments (July 2023,
  updated).** US-centric; set of pre-deployment and
  deployment commitments by major foundation-model
  developers.
- **National AI standards bodies** (ANSI, BSI, DIN,
  JIS). More standards-body than voluntary-code; same
  reporting-rigor expectation applies.
- **Industry-sector codes** (e.g., AICPA assurance
  standards for AI, NAIC AI Model Bulletin for state
  insurance departments). Often sector-specific and
  may blur with regulatory expectations.
<!-- needs-research: current status of UK AISI commitments and the Seoul-Summit follow-on commitments through 2026. -->

## 6.3 The four questions before signing on

Before the firm signs on to any voluntary code — new
sign-on or renewal — the CAO function should produce
written answers to four questions. These answers
become the record the Board or CEO relies on when
authorising the signature.

### 6.3.1 What did we commit to?

- The specific text of the code (as of the version
  being signed) in the record.
- The specific commitments the firm is signing to
  (some codes have optional modules; which modules
  apply).
- The reporting obligations: what, when, to whom, on
  what cadence.
- The *scope* within the firm: which business units,
  which products, which jurisdictions.

A sign-on without a documented scope statement is a
sign-on that commits the entire firm by default —
which may or may not be the intent.

### 6.3.2 What do we actually have to do?

- The internal operational changes required to meet
  the commitments. If zero changes are required, that
  is a signal — either the firm's practices already
  met the standard (good; verify by audit) or the
  commitments are weak (verify the code is worth
  signing).
- The named owner for each commitment. Commitments
  without owners drift.
- The evidence trail for each commitment. The sign-on
  is a representation that the firm *does* the thing;
  the evidence must be producible.
- The incident posture: what triggers an obligation to
  update the signatory authority, and what is the
  firm's response time.

### 6.3.3 What do we actually get?

- The reputational value of the sign-on in the firm's
  relevant stakeholder communities. If the sign-on is
  not recognised by the stakeholders who matter, the
  reputational return is low.
- The operational value: does the sign-on improve the
  firm's practices, or does it merely document them?
- The regulatory value: does the sign-on carry
  presumption of compliance (as the EU GPAI Code of
  Practice does) or does it carry no regulatory weight?
- The industry-coordination value: does the sign-on
  put the firm in rooms where industry norms are
  being set, or is it a passive affiliation?

A sign-on that provides none of the four categories of
value is a sign-on the firm should decline.

### 6.3.4 Under what conditions do we walk back?

Often overlooked. Each sign-on should include, in the
internal record, the conditions under which the firm
would publicly withdraw. Examples:

- The code's governance body changes the commitments
  in a way the firm cannot meet.
- The firm's own practices change (through acquisition,
  divestiture, or strategy shift) in a way that makes
  continued participation misleading.
- The code is being used by a bad-actor signatory to
  launder reputation, and the firm's association
  dilutes.
- Reporting obligations have become operationally
  unsustainable.

Pre-written walk-back conditions are not a plan to
quit; they are a plan to communicate the quit
decision honestly if the moment comes. Firms that
quietly stop meeting commitments while remaining
publicly affiliated expose themselves to the sharpest
form of reputational damage.

## 6.4 The CAO's operating practices

A short list of operating practices that keep the
voluntary-code portfolio honest.

- **Signatory inventory.** A single inventory of every
  voluntary code the firm has signed, with scope,
  owner, reporting cadence, next reporting date, and
  current adherence status. The inventory lives in the
  CAO's artifact store (mod-108) alongside the model
  inventory.
- **Pre-signature review.** No signature is added
  without CAO function sign-off and documentation of
  the four §6.3 answers.
- **Reporting integrity.** Reports under any voluntary
  code use the same evidence-grade discipline as
  regulatory filings. Where the firm cannot report
  honestly on a specific commitment, the report says
  so.
- **Annual portfolio review.** The CAO function
  reviews the portfolio annually: are these the right
  codes to be signed to; are any obsolete; have the
  commitments drifted; are there codes we should
  consider joining or leaving.
- **Material-change notification.** When a firm change
  (acquisition, divestiture, major deployment,
  incident) affects a sign-on's accuracy, the
  signatory authority is notified within a documented
  window.
- **Board visibility.** The signatory inventory and
  the annual portfolio review are standing items in
  the mod-111 board reporting pack. A board that is
  surprised to learn the firm is a signatory to
  something is a board with a governance gap.

## 6.5 The anti-pattern: ethics-washing

Voluntary-code sign-ons are a well-known vector for
*ethics-washing* — asserting ethical commitment by
association without the underlying practice. The
practice patterns that avoid ethics-washing accusations:

- **Publication consistency.** The firm's internal
  practices documented in sign-on reports match the
  firm's internal operations and standards.
- **Public reporting without PR optimisation.**
  Reports that mention weak points, in-progress
  implementations, and known gaps carry more
  credibility than reports that read as pure
  endorsement.
- **Specific-not-general language.** Reports that
  say "we test for X using Y with Z result" carry
  more weight than "we are committed to safety".
- **Owned by the CAO, not communications.**
  Communications teams are stakeholders in the
  reports' publication but not authors of the
  commitments. A report written by a comms team is
  a brochure.
- **Linked to the firm's actual operational standards.**
  Each commitment in a sign-on report should
  reference the internal standard that implements it.
  Commitments that reference no internal standard
  are commitments that are not implemented.

A credible CAO is one who can withstand the question
"what specifically does your sign-on to [code] mean
you do?" with a specific answer that is defensible by
inspection.

## 6.6 Interaction with the regulatory landscape

Voluntary codes do not replace statutory obligations.
They *interact* with them in three ways:

- **Statutory floor + voluntary ceiling.** The
  statute sets the minimum; the voluntary code may
  set a higher bar. The firm's practice must meet the
  statute; the sign-on commits the firm to the
  voluntary ceiling.
- **Statutory alignment via code (Art. 56-style
  pattern).** The code *is* the operational
  implementation of the statute. Signatory status
  carries presumption of compliance. Non-signatory
  firms must still comply with the statute by other
  means.
- **Statutory succession.** A voluntary code written
  in advance of statutory regulation is sometimes
  codified later. Firms with early sign-on history
  often have operational advantages when the statute
  arrives; late sign-on firms sometimes face the
  statute cold.

The CAO function's regulatory landscape view (mod-102)
should include voluntary codes alongside statutes
as part of the firm's governance surface — not as a
separate "soft" tier.

## 6.7 Where voluntary codes do not help

Honest about the limits:

- Voluntary codes do not substitute for internal
  operational discipline. A firm that signs five codes
  and has no operating standards is a firm with a
  reputational portfolio and no ethics practice.
- Voluntary codes do not resolve ethics disagreements.
  A code that is silent on the specific trade-off the
  firm is making provides no cover for the choice.
- Voluntary codes do not transfer liability. Signing a
  code does not shift legal responsibility; it may
  shift reputational expectations.
- Voluntary codes do not protect against incidents.
  The code is a commitment; the implementation is
  what matters.

A CAO who understands these limits can make the
voluntary-code portfolio a real asset. A CAO who treats
sign-ons as substitutes for the internal work has
built a liability.

## Summary

- Voluntary codes fall into three categories: pre-
  regulatory anchoring, statutory-compliance
  scaffolding, and industry-coordination scaffolding.
  Each implies different stakes and different
  reporting rhythms.
- The specific codes a CAO must know (as of 2026):
  OECD AI Principles, G7 Hiroshima Code of Conduct,
  EU AI Office GPAI Code of Practice, MLCommons AI
  Safety / AILuminate, Partnership on AI.
- Before any sign-on, the CAO function produces
  written answers to four questions: what did we
  commit to; what do we actually have to do; what do
  we actually get; under what conditions do we walk
  back.
- Operating practice: a signatory inventory, pre-
  signature review, reporting-integrity discipline,
  annual portfolio review, material-change
  notification, and standing board visibility.
- Ethics-washing is the predictable anti-pattern.
  Avoid it with publication-consistency, specific
  language, CAO ownership, and traceable linkage to
  internal standards.
- Voluntary codes interact with statutes as floor-
  ceiling, statutory-alignment, or statutory-
  succession patterns. Treat voluntary codes as part
  of the governance surface, not a soft tier beneath
  it.
- Voluntary codes do not substitute for internal
  discipline, resolve disagreements, transfer
  liability, or prevent incidents. They are
  commitments; the implementation is what matters.
