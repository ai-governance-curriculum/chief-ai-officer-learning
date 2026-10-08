# Chapter 2 — The Principles Landscape

## Why this chapter exists

You will encounter many AI ethics principles documents.
Several are well-respected and load-bearing in specific
contexts. Several others are produced primarily for the
producing organisation's reputational benefit. Treating
them as *interchangeable* — picking one at random, or
collating them into a single internal document that
inherits none of the specific operational commitments
— is the most common failure mode in CAO principles work.

This chapter builds the discipline of navigating the
landscape honestly: which documents actually matter,
where they converge (and why that convergence is
meaningful), where they diverge (and why that divergence
is operationally consequential), and how a CAO picks a
*framing principle set* that anchors the program's
reasoning without pretending to resolve what the
documents leave open.

## 2.1 The documents that actually matter in 2026

The field has produced hundreds of principles documents.
A small number carry operational weight. The following
are the ones a CAO must know by substance, not just by
name:

| Document | Year | Why it matters |
|---|---|---|
| OECD AI Principles | 2019 (updated May 2024) | Upstream of NIST AI RMF and EU AI Act; the closest thing to international consensus; 40+ country signatories |
| UNESCO Recommendation on the Ethics of AI | 2021 | The broadest international ethics statement; adopted by 193 member states; useful as a global-floor reference |
| IEEE 7000 series | 2021–2024 | Standards-grade ethics; especially IEEE 7000 (ethical system design process), 7001 (transparency), 7002 (data privacy), 7003 (algorithmic bias) |
| EU HLEG Ethics Guidelines for Trustworthy AI | 2019 | Upstream of EU AI Act; operationally superseded by the Act for high-risk systems but still cited for the seven key requirements |
| NIST AI RMF (preamble + core) | 2023 | Names the values the framework operationalizes (valid & reliable, safe, secure & resilient, accountable & transparent, explainable & interpretable, privacy-enhanced, fair with harmful bias managed) |
| Asilomar AI Principles | 2017 | Frontier-AI focused; useful anchor in capability-tier governance discussions |
| Microsoft Responsible AI Standard v2 | 2022 | Not authoritative but one of the most-developed public operationalisations; useful as a *pattern reference* |

A CAO who treats these interchangeably has not read them.
Each has a different intended audience, a different
authority basis, and a different set of operational
expectations.

## 2.2 The convergence problem

Most ethics principles documents say roughly the same
things at the principle level:

- Be fair / non-discriminatory
- Be transparent / explainable
- Respect privacy
- Be accountable
- Be safe / robust
- Respect human autonomy
- Be beneficial / promote well-being

The convergence at this level is genuine — there is real
international consensus on these as the *categories* of
concern. The convergence is also misleading: when the
principles are operationalized, the documents diverge
sharply on the specifics.

A useful framing: convergence at the principle level is
*evidence the principles are meaningful*. Divergence at
the operationalization level is *evidence the principles
are operationally non-trivial*. The discipline is not to
pick one set of principles and call the question
settled, but to navigate the operational divergence
honestly.

A corollary: if a CAO's principles document reads as
substantively identical to five others, the document has
done the easy part of the work — restating the
convergent principles. The hard part — committing to
specific operationalizations — has not been done. See
Chapter 7 §1 for the ethics-in-standards discipline that
closes this gap.

## 2.3 Where principles diverge in practice

Three examples make the operational divergence concrete.

### 2.3.1 On bias

- **OECD AI Principles**: AI should be "non-
  discriminatory and equitable" but provides no
  operational definition of what counts as either.
- **EU HLEG**: emphasizes "diversity, non-discrimination
  and fairness"; operationally closest to a disparate-
  impact analysis plus procedural-fairness framing.
- **IEEE 7003**: bias is treated as a measurable
  property with multiple competing metrics; the
  standard explicitly requires documenting *which*
  metric is used and *why*, and documenting trade-offs
  against metrics not used.
- **NIST AI RMF**: lists "fair with harmful biases
  managed" as a trustworthiness characteristic; the
  AI RMF Playbook recommends measuring across multiple
  metrics but does not prescribe which.
- **Microsoft RAI**: treats fairness as a property of
  the *system in context*; requires per-use-case bias-
  harm identification and documented mitigations.

Each of these would lead to a different bias-validation
*design* for the same model. Chapter 3 treats this in
operational depth.

### 2.3.2 On transparency

- **OECD**: transparency to those "adversely affected"
  — audience-specific framing but no content standard.
- **EU AI Act**: detailed technical documentation (Art.
  11 + Annex IV) for providers of high-risk systems;
  transparency to deployers (Art. 13); human oversight
  (Art. 14) — all explicitly separated as different
  obligations with different content requirements.
- **IEEE 7001**: transparency as a *property* requiring
  audience-specific explanations with explicit levels
  (end-user, expert, incident-investigator, etc.).
- **NIST AI RMF**: lists both "accountable &
  transparent" and "explainable & interpretable" —
  separated because they are not the same property.

The operational implications are different. A program
that reads OECD and declares transparency work done has
not reckoned with the EU AI Act's content requirements.

### 2.3.3 On autonomy and human oversight

- **OECD**: human-centered values and fairness; human
  oversight is a general norm.
- **EU AI Act Art. 14**: specific human-oversight
  requirements for high-risk systems — identification
  of when the system's output should be overridden,
  the ability to override, training for overseers.
- **IEEE 7000** (process standard): requires explicit
  identification of decisions delegated to AI vs.
  those reserved to humans, as part of the
  value-elicitation phase.
- **Asilomar Principle 16**: humans should retain
  control over how AI systems affect them — framed as
  a societal commitment rather than an operational
  obligation.

A program picking one of these as its "human oversight"
anchor must then back-fill the operational specifics the
chosen anchor does not provide.

## 2.4 Reading each document for what it is good for

A quick CAO-level characterisation. These are not
rankings; they are *fit-for-purpose* notes.

- **OECD AI Principles** — the right anchor for *inter-
  jurisdictional* framing. If the program operates
  across OECD-member countries, this is the lingua
  franca. Not operational on its own.
- **UNESCO Recommendation** — the right anchor for
  *global reach* and for sectors where UNESCO member-
  state alignment matters (education, cultural
  heritage, media). Longer and broader than OECD.
- **IEEE 7000 series** — the right anchor when the
  program wants a *standards-grade* operationalisation
  it can hold vendors and internal teams to. The IEEE
  7003 bias standard is particularly operational.
- **EU HLEG** — the right historical anchor for
  understanding where the EU AI Act's structure came
  from. For current EU compliance work, the AI Act
  itself has superseded the Guidelines; cite HLEG for
  framing, cite the Act for obligations.
- **NIST AI RMF** — the right anchor for programs
  anchored to a US federal / sector-regulator posture.
  AI RMF is a *framework*, not a principles document;
  the preamble carries the principle content.
- **Asilomar** — the right anchor for *frontier-
  capability* framing. Overkill for application-tier
  AI; well-suited for board-level discussions about
  general-purpose model acquisition and deployment.
- **Microsoft RAI Standard** — the right *pattern
  reference* when authoring internal operationalisation.
  Not authoritative; useful because it shows one firm's
  worked choices.

A CAO who can characterise the documents this way can
answer the "what principles do we follow?" question with
a *reasoned pick*, not a collage.

## 2.5 Choosing a framing principle set

A working CAO ethics function picks a *framing principle
set* — a small set of principles the program treats as
authoritative for its own decisions. This is *not* the
same as picking one document and disregarding others.
It is the discipline of being *explicit* about which
principles the program will treat as operationally
load-bearing.

A defensible framing principle set has these properties:

- **Locatable** in at least one authoritative document
  (so the framing is not idiosyncratic and so stakeholders
  can look it up).
- **Small** (5–7 principles maximum). Longer lists get
  ignored; shorter lists stop covering the categories.
- **Operationalizable** — for each principle, the
  program names what specific operational test it
  satisfies. "Fairness" with no operational test is a
  wish, not a principle.
- **Reviewable** — periodically revisited (annually is
  common) as the program matures and the external
  landscape shifts.
- **Attributed** — each principle names which document
  it is anchored to. A principle anchored to multiple
  documents states that explicitly; a principle anchored
  to none is a red flag.

### 2.5.1 Example — a defensible framing set

A composite example, not a template:

| Principle | Anchor | Operational test |
|---|---|---|
| Non-discrimination | OECD §1.2(a); IEEE 7003 | Pre-deployment bias validation across named protected classes with chosen metric set; threshold documented in Standard |
| Transparency to affected parties | OECD §1.3; EU AI Act Art. 86 | Decision-specific explanation with the four properties of Chapter 4 §3 |
| Transparency to regulators | EU AI Act Art. 11 + Annex IV | Continuously-maintained technical file |
| Contestability | GDPR Art. 22; EU AI Act Art. 14 | Named contestation process per Chapter 5 |
| Accountability | OECD §1.5; NIST AI RMF Core (GOVERN-6) | Named role accountable for each production AI system; recorded in inventory |
| Human oversight | EU AI Act Art. 14; IEEE 7000 §6 | Decisions delegated to AI vs. reserved to humans documented per-system; override capability recorded |
| Privacy | OECD §1.2(c); IEEE 7002 | DPIA/PIA for every production AI system handling personal data |

Seven principles. Each with an anchor. Each with a named
operational test. This is the posture that survives the
"what does your program stand for?" question.

### 2.5.2 What the framing-principle set is not

- It is **not** a mission statement. It is a decision
  framework.
- It is **not** the firm's full ethics position. The
  firm's position may be richer than its framing set
  by design.
- It is **not** immutable. Framing sets are revisited
  (quarterly, annually) with explicit sign-off and
  record of what changed.
- It is **not** sufficient on its own. The framing set
  anchors the reasoning; the operational standards
  (Chapter 7 §1) implement it.

A program with a documented framing set and no
corresponding standards has done half the work. A
program with standards but no framing set has standards
that will drift because nothing anchors them.

## 2.6 A note on bespoke principles documents

Many firms author their own principles document. This is
not inherently a bad idea. It is a bad idea when:

- The bespoke document inherits none of the operational
  specificity of the external documents it quietly
  draws from.
- The bespoke document is used as a *replacement* for
  attribution to the external anchors — hiding what the
  program is actually committing to.
- The bespoke document is produced for external
  communications only, with no counterpart standard
  governing internal decisions.

It is a reasonable idea when:

- The bespoke document explicitly cites the external
  anchors it operationalises.
- The bespoke document is paired with the operational
  standards (Chapter 7 §1).
- The bespoke document is one document in a documented
  hierarchy (principles → standards → procedures),
  not a standalone artifact.

A CAO ethics function with a bespoke document and no
hierarchy has produced a brochure. A CAO ethics function
with a bespoke document anchored to external principles
and operationalised through standards has produced the
first layer of a program.

## 2.7 The ethics-committee / standards-body question

Some organisations also contend with an *external*
ethics advisory body (academic ethicists, community
members, external experts) or a standards-body
affiliation (IEEE member, participation in NIST working
groups, etc.). Chapter 7 §4 treats the committee
question operationally. For the principles-landscape
discussion:

- Standards-body affiliation (IEEE, ISO) *does* obligate
  the program to the body's standards within the
  affiliation's scope. This is a real commitment.
- Advisory-body affiliation (an in-house ethics
  committee) does *not* obligate the program to anything
  external, but *does* commit the program to considering
  the body's advice on the record.
- Voluntary-code sign-ons (OECD Hiroshima Code, G7
  Hiroshima AI Process Code of Conduct, EU GPAI Code of
  Practice, Partnership on AI, MLCommons AI Safety
  working groups) are a separate class of commitment —
  Chapter 6 treats these in detail.

The common mistake: treating a voluntary-code sign-on as
if it were a principles document, or treating an
advisory-committee recommendation as if it were a
standards-body obligation. The distinctions matter when
a regulator later asks "what did you commit to?"

## Summary

- The principles landscape has a small number of
  documents that carry operational weight (OECD,
  UNESCO, IEEE 7000 series, EU HLEG, NIST AI RMF,
  Asilomar, Microsoft RAI). They are not interchangeable.
- Convergence at the principle level is genuine;
  divergence at the operationalisation level is where
  CAO work happens.
- A CAO picks a *framing principle set* — small,
  locatable, operationalizable, reviewable, attributed.
  5–7 principles, each with a named operational test.
- A bespoke principles document is defensible when it
  is paired with external anchors and operational
  standards; indefensible when it is a stand-alone
  brochure.
- Standards-body affiliation, advisory-committee
  recommendations, and voluntary-code sign-ons are
  distinct classes of commitment. Chapter 6 treats
  voluntary-code sign-ons as their own discipline.
