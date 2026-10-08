# Chapter 6 — Build, Buy, or Partner

## Why this chapter exists

Chapters 1–5 built the trust-architecture discipline.
This chapter addresses the enterprise question: how
does an organisation acquire that architecture? The
CAO does not typically make the engineering choice —
that belongs to the CISO, CTO, and CIO — but the CAO
has distinct contributions to the decision that often
go undelivered because the CAO treats the choice as
"not my job".

This chapter does three things. It names the three
options honestly, including the weaknesses of each. It
offers a structured decision framework. And it
specifies what the CAO contributes that the engineering
executives do not. Exercise 05 forces the CAO
contribution against a specific scenario (Halverston
Capital, continued from mod-103 and mod-105).

## 6.1 The three options, honestly

### 6.1.1 Build

The organisation engineers its own trust architecture
using standards (NIST SP 800-207, W3C VC, OAuth 2.1,
JWT/JOSE) and in-house implementation.

- **Strengths:** maximum control; no vendor
  dependency; architecture matches the
  organisation's specific needs; intellectual
  property is the firm's. The firm's engineers
  understand every design decision.
- **Weaknesses:** substantial engineering
  investment; multi-year roadmap to parity with
  commercial offerings; ongoing maintenance burden;
  the organisation must maintain cryptographic and
  security expertise it would otherwise outsource.
  Attrition in key engineers can hollow out the
  capability.
- **Best for:** organisations with strong engineering
  capacity, novel requirements that don't fit
  commercial offerings, or regulatory contexts where
  vendor dependency is itself a risk (hyperscalers,
  defence contractors, certain financial-services
  programs).

### 6.1.2 Buy

The organisation licences a commercial trust
architecture product (VeriSwarm, Cloudflare AI
Gateway, IBM watsonx.governance, and others).

- **Strengths:** fast deployment (months, not
  years); vendor support; architecture is battle-
  tested with other customers; vendor handles
  standards evolution and spec changes; recruiting
  is easier because the skill set is portable.
- **Weaknesses:** vendor lock-in; product roadmap
  may diverge from organisation needs; cost scales
  with usage; concentration risk if the vendor is
  acquired, pivots, or fails.
- **Best for:** organisations without specialised
  cryptographic engineering capacity, common
  requirements where commercial offerings are
  well-developed, or contexts where speed matters
  more than maximal control.

### 6.1.3 Partner

The organisation engages a commercial partner for
some components and builds others — typically buy the
identity / attestation infrastructure and build the
policy / orchestration layer; or buy the audit ledger
and build the gates.

- **Strengths:** uses vendor expertise where it is
  strongest; preserves control where the
  organisation's specific needs matter; distributes
  vendor concentration across multiple vendors.
- **Weaknesses:** integration burden; coordination
  across vendor + internal teams; partial-vendor-
  lock-in; the interfaces between built and bought
  components become their own maintenance surface.
- **Best for:** most large enterprises; the modal
  pattern by 2026.

### 6.1.4 The decision is not binary

A single build-buy-partner choice at portfolio level
is often the wrong framing. The matrix is per-
component: identity, capability manifest, trust gate,
scoring, audit ledger, posture monitoring, policy
authoring. Different components may warrant different
choices.

A worked example: a firm might buy the identity /
attestation infrastructure (because standards are
mature and off-the-shelf is credible), buy the audit
ledger (because tamper-evidence is a specialised
capability), build the policy authoring and
orchestration (because firm-specific vocabulary is
critical), and build the posture monitoring (because
the signals that matter are firm-specific). Four
components, four choices.

## 6.2 The decision framework

A useful framework for the choice, by dimension:

| Dimension | Build | Buy | Partner |
|---|---|---|---|
| Time-to-deploy | Slow (12–24 months) | Fast (3–9 months) | Medium (6–12 months) |
| Engineering investment | High (upfront + ongoing) | Low (integration + ongoing) | Medium |
| Maintenance burden | High | Low (vendor-managed) | Medium (interface surface) |
| Vendor dependency | None | High (single vendor) | Mixed (multiple vendors) |
| Customisation | Maximum | Limited to product | Selective |
| Standards evolution | Self-managed | Vendor-managed | Mixed |
| Regulatory defensibility | Self-attested | Vendor-attested + firm audit | Mixed |
| Cost over 5 years | Variable; often higher | Predictable; usage-scaled | Mixed |
| Talent recruiting | Hard (specialised skills) | Easy (portable skills) | Mixed |
| Risk of vendor failure | None | High | Distributed |

No row determines the choice. The CAO's input focuses
on dimensions where the governance perspective is
distinct from the engineering perspective:

- **Regulatory defensibility** — can the program
  explain the architecture to a regulator and defend
  it? A bought architecture is defensible if the
  vendor can produce attestations; a built
  architecture is defensible if the firm can
  demonstrate the discipline internally.
- **Maintenance burden over the program's lifetime**
  — does the organisation have the sustained capacity
  to maintain what is built? A build project that
  loses its key engineer in year three is a build
  project that becomes a partner project under
  duress.
- **Vendor dependency and concentration** — what
  happens if the chosen vendor changes terms, gets
  acquired, pivots, or fails? Trust architecture is
  load-bearing infrastructure; vendor failure is a
  continuity event.
- **Customisation needs** — does the program have
  requirements that commercial offerings don't meet?
  "Our LOBs have different latency profiles" or "we
  need a specific capability vocabulary" are
  substantive requirements, not preferences.

## 6.3 The 2026 landscape — practitioner patterns

The current commercial and open-source landscape (no
specific endorsement; observe the range):

### 6.3.1 Commercial AI-trust-architecture products

- **VeriSwarm** — deterministic 4-axis trust scoring
  + Passport (identity + capability manifest) + Vault
  (tamper-evident ledger). A full-stack take; one
  implementation.
- **Cloudflare AI Gateway** — gateway-mediated trust
  with observability and content-safety features;
  cloud-native deployment pattern.
- **IBM watsonx.governance** — governance platform
  with trust components integrated with the broader
  AI lifecycle management stack.
- **Robust Intelligence, Credo AI, Holistic AI** —
  governance platforms with partial trust-
  architecture components.

### 6.3.2 Open-source patterns

- **SPIFFE / SPIRE** — workload identity originally
  designed for services; adaptable to agents.
- **OpenID Connect + W3C VC combinations** — identity
  + delegation.
- **Sigstore** — attestation chains originally for
  build artifacts; pattern reference for runtime
  attestation.
- **OpenTelemetry GenAI semantic conventions** —
  evolving event vocabulary.

### 6.3.3 Hyperscaler offerings

- **AWS Bedrock Guardrails**; **Azure AI Content
  Safety**; **Google Cloud Vertex AI safety
  features**. These are partial trust architecture —
  they handle some axes (content safety, basic
  identity) and not others (capability scoping across
  agent ecosystems, deterministic trust scoring,
  cross-vendor delegation).

Each of these is a *practitioner pattern*, not the
answer. The build-vs-buy-vs-partner decision is
itself a build-vs-buy-vs-partner across the matrix of
trust-architecture components. No single vendor
offers a complete solution for most enterprise
contexts; the question is which components to buy
from whom, and which to build.

## 6.4 Vendor capture risk

The most insidious risk in the buy or partner
patterns is **vendor capture**: the program's
architecture becomes structurally dependent on a
specific vendor's product in ways that are not
visible at decision time but become irreversible
later. mod-101 §6 named this as a failure mode of
ethics programs; it applies equally to trust
architecture.

Capture happens through several mechanisms:

- **Proprietary data formats.** The vendor's
  manifest format or event vocabulary is specific
  to the vendor; migrating away requires rewriting
  every emitter and consumer.
- **Integration surface.** The firm's agent systems,
  identity provider, and audit infrastructure are
  wired to the vendor's APIs. Each integration is
  reversible in principle but costly in practice.
- **Operational muscle memory.** The firm's
  operations team learns the vendor's console, the
  vendor's incident patterns, the vendor's support
  channels. Switching vendors means retraining.
- **Compliance posture.** The firm's regulator-
  facing attestations cite the vendor's audits. A
  vendor change triggers a re-attestation cycle.

Mitigations the CAO should insist on:

- **Standards-based interfaces.** Components used
  must speak standard protocols (W3C VC, OAuth,
  OIDC, OpenTelemetry) so substitution is
  technically possible. Insist on this at
  procurement.
- **Documented assumptions.** The architecture
  documentation states what the vendor handles and
  what would need to be replaced if the vendor
  were unavailable. The replacement plan does not
  need to be executable immediately, but it must
  be thinkable.
- **Periodic vendor risk review.** The CAO function
  reviews vendor dependency annually as part of the
  obligations register (mod-102 §6.1).
- **Acceptable concentration.** Some vendor
  dependency is acceptable; concentration of
  multiple critical functions in one vendor is
  not. Spread risk across vendors where feasible.
- **Exit clauses in contracts.** Data portability,
  export of configuration, cooperation during
  transition. Negotiate these before signing, not
  during the exit.

A program that cannot name its vendor concentration
and the mitigations around it has probably been
captured — it has just not realised it yet.

## 6.5 What the CAO contributes to the decision

The CAO function's contribution to a trust-
architecture build / buy / partner decision is **not**
the architecture choice itself. The CAO contributes:

### 6.5.1 Requirements

What *must* the architecture support that the
engineering teams would not naturally prioritise?

- Regulatory defensibility — the architecture must
  produce evidence the firm can present to
  regulators (EU AI Act, NYDFS, FDA, state
  consumer-protection regulators depending on
  sector).
- Audit obligations — the architecture must emit
  the signed events the audit ledger (mod-108) and
  compliance program (mod-109) require.
- AI-program constraints — the architecture must
  respect ethical constraints (contestability from
  mod-105, explainability by audience).
- Lifecycle integration — the architecture must
  integrate with the model inventory (mod-104), the
  risk register (mod-103), and the board reporting
  rhythm (mod-111).

### 6.5.2 Risk assessment

- Vendor capture risk, named explicitly.
- Architectural fragility — what happens if a
  component fails? What is the recovery posture?
- Dependency on novel standards — the W3C VC
  ecosystem is maturing; betting on a specific
  profile may be premature.
- Transition risk — if the choice is wrong, how
  expensive is correcting it?

### 6.5.3 Program-level position

How is the chosen architecture described in the
program charter, in board reports, and to
regulators? The CAO owns the narrative; the
engineering team owns the implementation. The
narrative must be defendable, honest about
limitations, and consistent with the AI-program
rhythm.

### 6.5.4 Long-term maintenance posture

The architecture has lifecycle implications for the
program. A built architecture that depends on a
specific team's expertise has a succession risk the
CAO must name. A bought architecture has a vendor-
relationship cost the CAO must track. These are not
engineering decisions; they are program decisions,
and the CAO is the one responsible for naming them.

### 6.5.5 What the CAO does not contribute

The actual architecture choice belongs to the
engineering and security executives — CISO, CTO,
CIO. The CAO informs that choice; the CAO does not
own it. A CAO who tries to make the choice on
engineering grounds is overreaching; a CAO who abdicates
the governance input is underperforming. The
distinction is between *recommending requirements and
constraints* (CAO's role) and *selecting technologies*
(engineering's role).

Exercise 05 asks you to author the CAO's
contribution to a build-vs-buy-vs-partner decision
for Halverston Capital. The exercise is deliberately
structured so that the CAO's input is distinct from
what the CTO or CISO would independently produce.

## Summary

- Three options — build, buy, partner — each with
  honest strengths and weaknesses. The decision is
  rarely binary; most enterprise programs are
  per-component mixtures.
- A structured decision framework compares the
  options across ten dimensions. No row determines
  the choice; the CAO focuses on regulatory
  defensibility, maintenance burden, vendor
  dependency, and customisation needs.
- The 2026 landscape has commercial products,
  open-source patterns, and hyperscaler offerings.
  No single vendor offers a complete solution for
  most enterprises; the question is per-component.
- Vendor capture is the insidious risk of buy and
  partner patterns. Mitigations include standards-
  based interfaces, documented replacement
  assumptions, periodic vendor risk review,
  acceptable-concentration policies, and exit
  clauses negotiated upfront.
- The CAO contributes requirements, risk
  assessment, program-level position, and long-term
  maintenance posture — not the architecture choice
  itself.
