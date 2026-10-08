# Chapter 6 — The CAO × Chief Compliance Officer Boundary

## Why this chapter exists

The CAO function has three recurring second-line peer-
boundary problems in its first two years:

- The **CAO × MRM** boundary (see [`mod-104`](../mod-104-model-risk-management/README.md)
  Chapter 6) — overlapping scope on model risk.
- The **CAO × CISO** boundary (see [`mod-107`](../mod-107-ai-security/README.md)
  Chapter 5) — overlapping scope on AI security.
- The **CAO × Chief Compliance Officer** boundary —
  the subject of this chapter.

The Compliance Officer boundary has specific
characteristics the other two do not. The Compliance
function predates every CAO function by decades at
most firms. It has established obligations
infrastructure, established regulator relationships,
and established executive confidence. The CAO function
arrives into territory the Compliance Officer has
owned without challenge. Getting this boundary wrong
in the first six months — in either direction —
locks in a dysfunctional pattern that costs years to
unwind.

This chapter operationalises the peer boundary the
same way the MRM and CISO boundaries were
operationalised. The structural pattern is the same;
the specifics differ.

## 6.1 What Compliance owns

The Chief Compliance Officer (titles vary: Chief
Compliance & Ethics Officer, Head of Regulatory
Affairs, General Counsel in some structures) owns:

- **The enterprise compliance program** — all
  regulatory obligations the organisation faces, not
  just AI-specific ones. The compliance-risk register
  at enterprise scope. The compliance committee or
  equivalent governing body.
- **Compliance intake and workflow infrastructure** —
  how obligations enter the register, how changes are
  tracked, how attestation and sign-off flow.
- **Regulator engagement strategy** — some firms
  centralise this fully in Compliance; others
  distribute. The default position is centralised
  intake with distributed subject-matter.
- **Investigation and discipline** for compliance
  failures. Code-of-conduct, whistle-blower, and
  internal investigation processes.
- **Compliance training and culture** at enterprise
  scope. The organisation-wide compliance curriculum,
  mandatory training, acknowledgement workflow.
- **The regulator-of-record relationship** for most
  regulators the firm encounters. Historically-
  established exam cadences with FINRA, OCC, FDIC,
  state regulators, SEC, FTC, CFPB, etc.

Each item has been operated by Compliance for years or
decades. The CAO function cannot and should not try to
replace or duplicate any of them.

## 6.2 What the CAO function owns

The CAO function owns:

- **AI-specific obligations** within the enterprise
  compliance program. The EU AI Act, state AI laws,
  NYDFS Part 500 AI amendments, NAIC Model Bulletin
  on AI, FDA SaMD and PCCP guidance, OMB M-25-21 (for
  federal programs). The AI-specific slice of the
  obligations register.
- **The AI control catalog** — the operational form
  of AI obligations (Chapter 2). The AI-specific
  controls, their mappings, their maturity.
- **The AI continuous-evidence cadence** (Chapter 3).
- **AI-specific regulator engagement**. EU AI Act
  authorities, AI-specific state regulators,
  AI-focused components of broader exams (e.g., the
  AI section of an FDIC exam at a bank with ML in
  underwriting).
- **The AI program's standards** — [`mod-105`](../mod-105-responsible-ai-and-ethics/README.md)
  responsible-AI, [`mod-106`](../mod-106-trust-architecture/README.md)
  trust architecture, [`mod-107`](../mod-107-ai-security/README.md)
  AI security. These are standards the CAO function
  authored (with peer input) and operates.
- **AI incident response** at the AI-specific layer
  (see [`mod-110`](../mod-110-incident-response/README.md)).
  Compliance leads enterprise incident response; the
  CAO contributes AI-specific expertise and leads
  the AI-specific regulatory notifications where the
  regulatory interface is AI-specific.

Note what the CAO does *not* own under this boundary:

- The enterprise obligations register. Compliance
  does; the CAO contributes the AI slice.
- Enterprise regulator engagement. Compliance does
  for most regulators.
- Investigation and discipline. Compliance leads.
- Enterprise compliance training. Compliance owns the
  curriculum; the CAO contributes AI-specific
  content.

## 6.3 The intersection — where both have legitimate claims

Six intersection topics predictably create tension.
Each has a legitimate claim from both sides.

| Topic | Compliance's claim | CAO function's claim |
|---|---|---|
| **Obligations register** | Enterprise register at enterprise scope | AI-specific obligations with sector-overlay nuance |
| **Control catalog** | Enterprise controls (SOX, SOC 2, info-sec, privacy, financial crime) | AI-specific controls, often extending enterprise controls |
| **Evidence collection** | Organisation-wide infrastructure already exists | AI-specific overlay (telemetry patterns from mod-108) |
| **Training** | Enterprise compliance training is Compliance's responsibility | AI-specific content needs the CAO's authoring |
| **Investigation** | Compliance leads investigations | AI expertise is needed for AI-related investigations |
| **Regulator engagement** | Most regulators are Compliance's historical relationships | AI-specific regulators (EU AI Act authorities) are CAO's |

The pattern on each topic is the same: both have a
legitimate claim; neither can unilaterally own the
topic without losing something important. The
boundary pattern that works resolves each topic as a
**joint ownership with a named lead per activity**.

## 6.4 The operating pattern that works

Four operating patterns, in order of importance.

### Extend, don't duplicate

The CAO's controls **extend** the Compliance
Officer's enterprise control catalog rather than
duplicating it. AI-specific controls are *additional*
to enterprise controls; where they overlap, one
control covers both via the crosswalk pattern from
Chapter 2 §2.3.

The practical test: for each AI-specific control,
does an enterprise equivalent already exist? If yes,
the AI control extends the enterprise one (or the
enterprise one is amended to cover AI-specific
needs). If no, the AI control is net new. A new CAO
function should rarely create AI-specific
infrastructure where enterprise infrastructure covers
the need; the CAO function should rarely accept the
enterprise infrastructure as sufficient without
AI-specific overlay where the AI stakes require more.

### Shared evidence infrastructure

The CAO's evidence flows into the **same evidence
infrastructure** as Compliance's enterprise evidence.
The audit ledger ([`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md))
is shared. Programs that build parallel evidence
infrastructures discover they have two sources of
truth that drift; the first time an audit opens both
and finds divergence, the program loses credibility
on both.

Shared infrastructure does not mean undifferentiated
scope. The CAO's AI-specific events, retention
policies, and chain-of-custody expectations may differ
from the enterprise defaults. The infrastructure is
shared; the configuration is AI-specific where
needed.

### Joint quarterly review

The CAO and Compliance Officer **review the
obligations register jointly** at least quarterly.
Changes to AI-specific obligations enter the shared
register; changes to enterprise obligations surface
AI implications the Compliance Officer may not catch
unilaterally.

The joint review is a working meeting, not a
ceremony. The output is a signed memo recording
changes, decisions, and open questions. The memo is
itself evidence.

### Joint regulator briefings

When an obligation touches both AI-specific and
enterprise domains (SR 11-7 and EU AI Act both apply
to a credit model; NYDFS Part 500 covers both
cybersecurity and AI; CFPB inquiries can involve both
fair lending and model governance), the CAO and
Compliance lead **present together**. One voice
speaks for the organisation on the overlap. The post-
meeting internal reconciliation happens offline.

The named-lead-per-topic convention is what allows
the regulator to hear one organisation. Dual leads
produce dual positions, which produce one examiner
question: "which of these is your official
position?" The regulator will not accept "both".

## 6.5 Patterns that fail

Four patterns that look reasonable and consistently
produce bad outcomes.

- **Separate AI compliance function running in
  parallel to enterprise Compliance.** The CAO
  function builds its own obligations register, its
  own evidence intake, its own regulator-engagement
  machinery. Within a year, the two functions produce
  divergent positions on topics they both cover; the
  regulator discovers the divergence; the firm pays
  for it. The remedy is extending, not duplicating.
- **CAO building separate enterprise-wide compliance
  machinery.** A new CAO who views the existing
  Compliance function as inadequate and tries to
  replace it ends up with two Compliance functions.
  The remedy is addressing specific gaps (if they
  exist) within the enterprise function via joint
  work, not around it.
- **Compliance building AI-specific controls
  unilaterally.** The Compliance Officer, confronted
  with AI-specific obligations and without CAO input,
  builds AI controls that look like classical
  compliance controls — attestations, policy
  references, periodic reviews — and miss the
  operational-telemetry patterns that AI obligations
  often require. The remedy is Compliance briefing the
  CAO on new obligations before authoring controls.
- **Named-lead-per-topic missing or ambiguous.** On a
  given issue, no one knows who leads. Both sides are
  deferential; nothing moves. Or both sides claim
  lead; the regulator sees inconsistency. The remedy
  is the explicit per-topic named-lead convention
  from §6.4, written down.

Each failing pattern is traceable to one of two
anti-patterns: duplication (parallel infrastructure)
or hierarchical framing (one function trying to be
superior to the other). The peer-boundary design is
the structural remedy.

## 6.6 How this boundary differs from CAO × MRM and CAO × CISO

The three peer boundaries have common structural
features and specific differences.

| Dimension | CAO × MRM (mod-104 Ch. 6) | CAO × CISO (mod-107 Ch. 5) | CAO × Compliance (this chapter) |
|---|---|---|---|
| Established function | Yes — SR 11-7 since 2011 | Yes — longer | Yes — longest |
| Primary overlap | Model validation and inventory | Threat landscape, incident response, infra security | Obligations register, controls, regulator engagement |
| CAO scope framing | AI-system-level across model-plus-non-model components | AI-specific threat classes and detections | AI-specific obligations within enterprise compliance |
| Typical first-year failure | Re-validation of MRM-validated models | Parallel AI-security tooling | Parallel AI compliance function |
| Reporting line | Both typically to CRO | CISO to CTO/CIO/CRO; CAO to CRO | Compliance usually to GC or CEO; CAO to CRO |

The reporting-line difference is the most structurally
distinctive. The Compliance Officer frequently
reports *outside* the CRO's organisation — most
commonly through the General Counsel, sometimes
directly to the CEO. The CAO function (per mod-101
§4) typically reports to the CRO. This creates a
cross-executive boundary that the other two peer
boundaries do not have.

The cooperation pattern works when both heads share a
governance forum — the AI Risk Council, the
enterprise risk committee, the Board Risk Committee.
When they do not — when Compliance operates through
General Counsel and CAO through CRO and never share
a forum — the cooperation degrades into ceremony.
The forcing function is a joint committee at the
right level, with written minutes and decisions that
stick.

## 6.7 The reporting-line question (specifically)

A specific debate at firms designing the CAO
function: should the CAO function report to the Chief
Compliance Officer instead of the CRO?

The pattern that generally fails: CAO reporting to
CCO. Reasons:

- The CAO function's work spans beyond compliance
  into risk management, model operations, trust
  architecture, security, and incident response. A
  compliance-only reporting line narrows the scope
  the CAO can operate against.
- Compliance culture is often retrospective (did we
  comply?); CAO work is often prospective (will the
  AI system behave as intended under conditions that
  haven't yet been tested?). The two cultures can
  productively interact but should not be nested.
- Regulators increasingly expect AI oversight to be
  risk-based rather than compliance-based. A
  compliance-nested CAO function reports a weaker
  posture.

The pattern that generally works: CAO function to
CRO (or to a peer executive at that tier), with a
strong peer relationship to the Chief Compliance
Officer via the mechanics §6.4 describes.

## 6.8 Working the boundary at steady state

A CAO function that has made peace with the
Compliance Officer typically has:

- A short, co-signed **scope memo** describing the
  boundary. Both heads sign; refreshed annually; the
  memo lives in both functions' operating documents.
- A **joint quarterly review** of the obligations
  register and the control catalog. Signed minutes.
- **Mutual read-access** to each function's
  obligations register, control catalog, and
  evidence pipelines. Opacity between the two
  functions is where boundary conflicts breed.
- A **named escalation path** to a shared executive
  (CEO or Board Risk Committee chair) for the rare
  disputes that cannot resolve at working level.
- A **joint annual report** to the Board or Audit
  Committee that covers both enterprise compliance
  and AI-specific compliance, with explicit cross-
  references.

The absence of any of these items is a diagnostic. A
CAO who cannot describe the cadence by which they
coordinate with the Compliance Officer has not yet
solved the boundary. Exercise 05 puts a specific
version of this boundary under pressure — a
Compliance Officer's proposal to absorb AI-regulatory
engagement into existing enterprise processes — and
asks for a defensible resolution.

## Summary

- The CAO × Chief Compliance Officer boundary is the
  third of the second-line peer boundaries (alongside
  MRM and CISO) and typically the most
  organisationally sensitive, because the Compliance
  function is the longest-established.
- Compliance owns the enterprise compliance program,
  obligations register, intake and workflow,
  investigations, enterprise regulator engagement, and
  enterprise training. The CAO function owns AI-
  specific obligations, control catalog, continuous
  evidence, AI-specific regulator engagement, and
  the AI program's standards (mod-105, mod-106,
  mod-107, mod-110).
- Six intersection topics (obligations register,
  controls, evidence collection, training,
  investigation, regulator engagement) have
  legitimate claims from both sides; the pattern is
  joint ownership with a named lead per activity.
- Four operating patterns work: extend don't
  duplicate, shared evidence infrastructure, joint
  quarterly review, joint regulator briefings. Four
  patterns fail: parallel compliance function,
  CAO building separate enterprise machinery,
  Compliance building AI controls unilaterally,
  ambiguous named-lead.
- The boundary differs structurally from CAO × MRM
  and CAO × CISO primarily in the reporting-line
  pattern — Compliance often reports outside the CRO
  organisation. The cooperation forcing-function is
  a shared governance forum.
- CAO reporting to the CCO typically fails because
  the CAO scope exceeds compliance. CAO to CRO with
  peer relationship to Compliance via explicit
  mechanics is the pattern that works.
- Steady state: scope memo, joint quarterly review,
  mutual read-access, named escalation, joint annual
  report. Absence of any is a diagnostic.
