# Chapter 5 — ISO/IEC 42001 Annex A as a Working Control Catalog

## Why this chapter exists

Chapter 2 taught the discipline of control mapping.
Chapter 3 taught the cadence that keeps controls
operating. Chapter 5 answers the catalog-building
question: *where should a CAO start when assembling
the AI-program control catalog from scratch?* The
honest answer in 2026 is **ISO/IEC 42001:2023 Annex
A**.

Annex A is one of the few authoritative, operationally-
shaped control catalogs for AI available to programs.
It is published by a recognised standards body, is
written in auditable form (not principles), is
accompanied by implementation guidance in ISO/IEC
42005 and the forthcoming ISO/IEC 42006, and has
published or community-maintained crosswalks to NIST
AI RMF and the EU AI Act. For a CAO who needs a
starting point that is defensible to regulators and
auditors, Annex A is the shortest path.

The chapter also treats Annex A's limitations
honestly. The catalog is comprehensive at cross-sector
breadth and necessarily thin on sector depth; it pre-
dates the agentic-AI patterns of 2024–2026 and does
not directly address trust-architecture or trust-
gating; it carries less emphasis on post-market
monitoring as a separable artifact than EU AI Act
Art. 72 asks for. A program that adopts Annex A
verbatim and stops there has a defensible baseline and
material gaps.

## 5.1 What ISO/IEC 42001 is

ISO/IEC 42001:2023 is the first ISO AI management
system (AIMS) standard, published December 2023. It
follows the same clause structure as ISO/IEC 27001
(information security) and ISO/IEC 9001 (quality):

- Clauses 4–10 contain the **management-system
  requirements** — organisational context, leadership,
  planning, support, operation, performance evaluation,
  improvement. These are the requirements an
  organisation must meet to claim conformance.
- **Annex A** contains the **control catalog** — a
  normative list of controls organised under control
  objectives, that organisations should consider for
  their AIMS.
- **Annex B** contains **implementation guidance** —
  non-normative explanations of what each Annex A
  control looks like in practice.

ISO/IEC 42005:2025 (AI system impact assessment)
and ISO/IEC 42006 (AIMS auditor requirements) extend
the standard with impact-assessment process guidance
and auditor expectations. The three together are the
reference set.

For CAO purposes, the Annex A catalog is the piece
this chapter uses. The management-system clauses are
important for certification but are themselves not a
catalog of day-to-day controls — they describe how
the catalog is governed.

## 5.2 The Annex A structure

Annex A is organised into control **objectives**,
each with multiple **controls**. The objectives, in
Annex A's own numbering (A.2 through A.10, with A.1
being general):

- **A.2 Policies related to AI** — organisational
  policies, their approval, and their review.
- **A.3 Internal organisation** — roles and
  responsibilities, reporting on AI concerns.
- **A.4 Resources for AI systems** — the resources
  (people, data, computing, system) available to AI
  activities.
- **A.5 Assessing impacts of AI systems** — the AI
  system impact assessment process (expanded in
  ISO/IEC 42005).
- **A.6 AI system life cycle** — objectives covering
  the AI system from design through retirement.
- **A.7 Data for AI systems** — data quality,
  provenance, management, and treatment of personal
  data.
- **A.8 Information for interested parties of AI
  systems** — transparency to users, affected
  parties, and other interested parties.
- **A.9 Use of AI systems** — controls on how the
  organisation uses its own AI systems.
- **A.10 Third-party and customer relationships** —
  controls at the boundary with suppliers and
  customers who provide or consume AI capabilities.

Across the objectives, Annex A specifies roughly 38
controls at a published granularity broadly
comparable to ISO/IEC 27001 Annex A. The exact
control count may evolve across revisions; the
objective structure is more stable.

## 5.3 Using Annex A as the catalog spine

The practical use pattern — five steps.

### Step 1 — Adopt the objectives as the catalog spine

The 10 objectives become the top-level organisation of
the control catalog. Every program control sits under
one of the objectives. This gives the catalog a
stable structure that aligns with the standard and
that auditors already know.

### Step 2 — Map each Annex A control to a program control

Walk through each Annex A control. For each:

- **1:1 mapping** — an existing program control
  satisfies this Annex A control directly. Record the
  mapping.
- **1:many mapping** — one program control satisfies
  multiple Annex A controls (the Chapter 2 §2.3
  crosswalk pattern). Record all the Annex A controls
  the program control satisfies.
- **No mapping** — the program has no control for
  this Annex A control. Flag as a gap.

The output is a two-way table: Annex A control ↔
program control. Both directions matter; the Annex A
→ program direction surfaces gaps, the program →
Annex A direction surfaces controls that are not
anchored to the standard.

### Step 3 — Rate maturity

For each Annex A control, rate the program's maturity:

| Rating | Meaning |
|---|---|
| **Not present** | No program control exists |
| **Partial** | Program control exists but has gaps against the Annex A control's expectation |
| **In place** | Program control satisfies the Annex A control |
| **Mature** | Program control exceeds the expectation and has history of continuous operation |

The maturity table is the gap-analysis artifact.
Exercise 03 produces this artifact at scale against a
fictional firm.

### Step 4 — Cross-reference other obligations

For each program control, cross-reference the *other*
obligations it satisfies — NIST AI RMF sub-functions,
EU AI Act articles, sector overlays (SR 11-7, NYDFS
Part 500, NAIC Model Bulletin, FDA guidance). The
crosswalks let a single control cover an obligation
stack.

Published crosswalks that help:

- NIST AI RMF Playbook includes cross-references to
  ISO/IEC 42001 for most sub-functions.
- The ISO/IEC 42001 ↔ EU AI Act crosswalk is
  maintained by multiple consultancies and the
  European AI Office; use the primary sources where
  possible.
- Sector regulators sometimes publish their own
  crosswalks; NAIC and NYDFS have both referenced ISO
  42001 in guidance.

### Step 5 — Test the catalog annually

Pre-audit preparation: run the gap analysis annually.
Address material gaps before the external audit sees
them. Document the acceptance posture for gaps the
program decides not to close.

## 5.4 What Annex A does well

Four strengths worth naming.

- **Comprehensive**. Annex A covers the AI lifecycle
  from policy through retirement and spans data,
  system design, third-party relationships, and user-
  facing transparency. The breadth is well-chosen for
  a cross-sector catalog.
- **Auditable form**. Controls are written as
  activities, not principles. "Verify that AI systems
  operate as intended" is operationally testable;
  "respect human autonomy" is not. Annex A errs on
  the operational side of the line.
- **Standards-grade**. The catalog is published by
  ISO/IEC and is defensible to regulators and
  auditors who recognise the standard — which, in
  2026, is most of them.
- **Crosswalkable**. Published and community mappings
  exist to NIST AI RMF, EU AI Act, and sector
  overlays. A control satisfying an Annex A
  requirement can be documented as also satisfying
  the mapped obligations.

## 5.5 What Annex A doesn't do well

Four limitations worth naming. A program that adopts
Annex A verbatim and stops has these gaps.

- **Limited sector depth.** Annex A is cross-sector by
  design. Specific financial-services requirements
  (SR 11-7 §V model inventory, SR 22-6 Validation of
  Non-regression Testing, NYDFS Part 500 §500.09),
  healthcare requirements (FDA SaMD guidance,
  PCCP-specific obligations), insurance requirements
  (NAIC Model Bulletin bias testing), and public-
  sector requirements (OMB M-25-21 CAIO structure,
  Canadian Directive on Automated Decision-Making) all
  need **sector overlays**. The overlays extend Annex
  A; they do not replace it.
- **Post-market monitoring under-emphasised as a
  separable artifact.** EU AI Act Art. 72 specifies
  post-market monitoring with specific scope and
  retention; Annex A covers monitoring under A.6
  lifecycle controls but does not elevate post-market
  monitoring to the same operational prominence. A
  program with EU AI Act exposure needs an explicit
  post-market monitoring artifact beyond Annex A's
  lifecycle treatment.
- **Trust architecture and trust-gating not directly
  addressed.** Annex A was finalised before the
  agentic-AI patterns ([`mod-106`](../mod-106-trust-architecture/README.md))
  solidified. Trust-boundary definition, trust-score
  computation, trust-gate enforcement, and agent-
  identity management are not Annex A controls today.
  A CAO program with agentic AI needs controls above
  and beyond Annex A to cover these.
- **AI incident reporting under-structured.** Annex A
  touches incident response but does not give the
  topic the operational prominence EU AI Act Art. 73
  does for serious incidents, or that NYDFS Part 500
  §500.17 does for cybersecurity events. Programs
  with regulatory incident-reporting obligations need
  dedicated incident controls beyond Annex A's
  treatment. See [`mod-110`](../mod-110-incident-response/README.md).

A working program uses Annex A as the spine and
overlays sector-specific and AI-evolution-specific
controls on top. Exercise 03 produces this overlay
pattern against a specific firm.

## 5.6 Interaction with certification

If the program is pursuing ISO/IEC 42001
certification, three practical considerations.

### Certification scope

The certification scope is the organisation's
decision, not the auditor's. A program may certify a
specific business unit, a specific AI system
portfolio, or the whole organisation. The scope
decision affects which Annex A controls apply and
how the gap analysis is bounded.

Scope decisions that work:

- Certify where the operational muscle already exists;
  grow scope outward. First-time certifications that
  attempt whole-organisation scope frequently fail at
  the first audit on readiness grounds.
- Scope matches a reporting boundary. If the AI
  program reports as a single unit to the board, the
  certification scope commonly aligns.

### Auditor selection

Annex A audits are performed by accredited
certification bodies. ISO/IEC 42006 (when fully
published) sets expectations for auditor
qualifications. In the interim, select auditors with
specific AI experience; a classical ISO/IEC 27001
auditor without AI depth will produce a less
illuminating audit.

### Certification is not the goal

A certification artifact is useful. It is **not** a
substitute for the operational discipline. Programs
that treat certification as the goal under-invest in
the continuous-cadence practice from Chapter 3 and
over-invest in the audit preparation. The regulator
exam that follows will test the operation, not the
certificate.

## 5.7 The relationship to NIST AI RMF

A recurring CAO question: should the program adopt
Annex A or the NIST AI RMF as its spine?

The honest answer: they are different artifacts and
you probably want both.

- **NIST AI RMF** is a **framework** — organised
  around functions (GOVERN, MAP, MEASURE, MANAGE),
  intended to be adopted and tailored. It is not a
  control catalog; the Playbook contributes concrete
  actions but at a different grain than Annex A.
- **ISO/IEC 42001 Annex A** is a **control catalog** —
  a normative list of controls with implementation
  guidance.

Use NIST AI RMF for the **operating-loop structure**
(see [`mod-103`](../mod-103-ai-risk-frameworks/README.md)
Chapter 6); use Annex A for the **control catalog
spine**. Cross-reference the two. Pointing to only
one is a weaker posture than pointing to both.

## Summary

- ISO/IEC 42001:2023 Annex A is the strongest working
  AI control catalog available to CAO programs in
  2026 — authoritative, operationally-shaped,
  crosswalkable.
- Annex A is structured as 10 control objectives
  (A.2–A.10 plus general) with roughly 38 controls.
  The objectives become the catalog spine; the
  controls are mapped to program controls.
- Five-step use pattern: adopt the objectives,
  map each Annex A control to a program control, rate
  maturity, cross-reference other obligations, test
  annually.
- Four strengths: comprehensive, auditable form,
  standards-grade, crosswalkable. Four limitations:
  limited sector depth, under-emphasised post-market
  monitoring, trust architecture not directly
  addressed, AI incident reporting under-structured.
- A working program overlays sector-specific and AI-
  evolution-specific controls on top of Annex A, not
  instead of it.
- Certification is useful; certification is not the
  goal. The regulator exam tests the operation.
- NIST AI RMF and Annex A are complementary — use the
  framework for the operating loop, use Annex A for
  the control catalog.
