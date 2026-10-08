# Chapter 6 — Build, Buy, or Partner for Audit Ledgers

## Why this chapter exists

Chapters 1–5 built the discipline. This chapter is
the enterprise question: how does the organisation
acquire the discipline's infrastructure? The CAO does
not typically own the engineering choice — that
belongs to the CTO, CISO, and CIO — but the CAO has
distinct contributions to the decision that often go
undelivered because the CAO treats the choice as "not
my job."

The framework here mirrors `mod-106` §6 for trust
architecture. The structural parallel is deliberate:
both chapters sit at the end of their module and ask
how the technical substrate is procured. The specific
contours — vendor landscape, migration risk, standards
— differ, and this chapter is the audit-ledger
version.

Exercise 05 forces the CAO contribution against a
specific scenario (Halverston Capital, continued from
earlier modules and from Exercise 04 in this module).
This chapter is the framework the exercise applies.

## 6.1 The three options, honestly

### 6.1.1 Build

The organisation engineers its own audit-ledger
infrastructure using cryptographic standards (RFC 9162,
RFC 3161, JOSE/JWS for signing) and in-house
implementation.

- **Strengths.** Maximum control. No vendor
  dependency on the layer that holds the
  organisation's evidence. The architecture matches
  the organisation's specific event vocabulary,
  retention needs, and sealing cadence. Intellectual
  property remains in-house. The firm's engineers
  understand every design decision.
- **Weaknesses.** Substantial engineering investment
  — typically 12–18 months to a production-grade
  implementation. Cryptographic expertise is
  required and expensive to recruit and retain. The
  integrity guarantees are only as good as the
  implementation's correctness; a subtle bug in a
  Merkle-tree library can invalidate years of
  evidence silently. Ongoing maintenance burden
  including cryptographic agility (algorithm
  deprecations, new primitives).
- **Best for.** Organisations with strong
  cryptographic engineering capacity; organisations
  for which vendor dependency on evidence
  infrastructure is itself a material risk (certain
  government, defence, and hyperscaler-adjacent
  contexts); organisations whose event volume
  justifies the operating leverage of in-house
  tuning.

### 6.1.2 Buy

The organisation licences a commercial audit-ledger
product. Candidates in 2026 include commercial AI-
governance platforms with audit components, Sigstore
Rekor as a managed service, hyperscaler-managed
audit trails (AWS CloudTrail with integrity
validation and equivalents at other hyperscalers),
and sector-specific vendors.

- **Strengths.** Fast deployment — typically months,
  not years. Vendor support. Architecture is
  battle-tested with other customers. Vendor
  handles cryptographic correctness, library
  updates, and algorithm agility. Recruiting is
  easier because the skill set is portable.
- **Weaknesses.** Vendor lock-in. For evidence
  infrastructure this is materially sharper than
  for most infrastructure (§6.4 below). Product
  roadmap may diverge from the organisation's
  needs. The organisation's evidence sits in a
  system whose design is governed by someone else.
  Commercial terms (pricing, SLAs, data residency)
  can change at renewal.
- **Best for.** Organisations without specialised
  cryptographic engineering capacity;
  organisations where time-to-production matters;
  organisations whose evidence requirements fit
  standardised compliance patterns.

### 6.1.3 Partner

The partner option is a conscious split. The
organisation buys some components and builds others.
Common partner patterns:

- **Buy the ledger; build the vocabulary and
  analysis.** The cryptographic guarantees come
  from the vendor. The program retains control over
  what goes into the ledger (per Chapter 3) and how
  it is interpreted. The migration risk shrinks
  because what is vendor-specific is the ledger
  primitives, not the organisation's event model.
- **Buy the ledger and the analysis layer; build
  the evidence-package assembly.** The vendor
  provides ledger and query primitives. The
  program authors the audience-specific packages
  (per Chapter 4). The organisation retains the
  discipline of curating evidence for its specific
  audiences.
- **Heterogeneous.** Buy from one vendor for
  in-scope-of-vendor systems; build for systems
  outside that scope (legacy systems, specialised
  deployments, segregated regulated environments).
  Operationally more complex but sometimes the only
  feasible posture for a diverse estate.

Partner is often the right answer for sophisticated
organisations with a diverse system estate. It is
rarely the first option proposed because it requires
the organisation to be more thoughtful about *what*
it is buying and *what* it is building than
build-or-buy framings require.

## 6.2 The structured decision

The decision matrix for audit-ledger procurement
should address at least nine dimensions:

| Dimension | Why it matters |
|---|---|
| Time-to-deploy | Regulatory deadlines and board commitments are real |
| 5-year total cost | Short-horizon pricing comparisons mislead |
| Annual operating cost | Determines steady-state resource allocation |
| Vendor dependency | Evidence infrastructure is particularly sticky |
| Migration risk | The §6.4 concern; often the deciding dimension |
| Standards conformance | RFC 9162 and RFC 3161 are the baseline |
| Customisation for the program's event vocabulary | A vendor whose vocabulary does not fit forces compromise |
| Regulator defensibility | What the program can say to a regulator about this choice |
| Engineering / talent posture | Who maintains the capability over the long term |

Dimensions should be filled in with specific values
or characterisations — not "medium" or "high" alone
but concrete numbers and qualitative descriptions
that let the decision reviewer evaluate them. Exercise
05 is where this discipline becomes concrete.

## 6.3 Where the decision usually lands

Across sectors, the dominant pattern in 2026 is
**partner**, with specific commentary:

- **Financial services** typically partners by
  buying the cryptographic ledger primitives
  (where vendor expertise materially adds value)
  and building the event vocabulary and evidence-
  package assembly (where the firm's specific
  regulatory posture matters). Migration risk is
  managed with standards-conformant export
  requirements.
- **Healthcare** typically partners differently —
  buying the ledger from an existing clinical-
  systems vendor whose compliance posture is
  already established, with less emphasis on
  cryptographic sovereignty.
- **Technology / platform** firms often build —
  the engineering capacity is in-house and the
  evidence patterns are novel enough that
  commercial offerings don't fit cleanly.
- **Smaller firms across sectors** typically buy —
  they do not have the engineering capacity to
  build or to run a thoughtful partner split.

The partner-dominant pattern is not a prescription.
It is the empirical centre of gravity. Specific
organisations in each sector will land elsewhere for
specific reasons; those reasons should be explicit in
the decision document.

## 6.4 The migration risk

The most insidious risk in *buying* audit-ledger
infrastructure is **migration risk** — the cost of
moving from one vendor to another is materially
higher than for most infrastructure categories.
Three reasons:

- **Retention duration.** Evidence has long
  retention requirements. Chapter 5 §5.1 named 5–10
  year durations as typical. Moving years of
  sealed evidence with preserved integrity
  properties is a multi-quarter engineering
  project at minimum. The organisation cannot
  simply walk away from a vendor and leave the
  evidence behind.
- **Cryptographic lineage.** Seals, inclusion
  proofs, and signatures depend on the vendor's
  key material and ledger structure. Migrating
  preserves integrity only if the migration itself
  is cryptographically careful — producing a
  "migration witness" that attests to the
  equivalence of the pre- and post-migration
  ledger states.
- **Format proprietary layers.** Even where the
  core structures are RFC-conformant, vendors
  typically have proprietary extensions. Importing
  into another system requires either coercing
  into a standards-only subset (losing
  information) or custom conversion.

### 6.4.1 Mitigations

Three mitigations substantially reduce migration
risk:

- **Standards-based export formats.** The vendor
  must produce evidence in standards-conformant
  formats — CloudEvents envelopes, RFC 9162-style
  inclusion and consistency proofs, RFC 3161
  timestamps, JOSE/JWS signatures. If the vendor's
  only export format is proprietary, migration is
  effectively impossible.
- **Documented migration playbook.** Even if no
  migration is planned, the playbook ensures the
  organisation knows what migration would require,
  what the risks are, and what sign-offs the
  organisation would need. The playbook is itself
  a hedge against vendor leverage at renewal
  negotiations.
- **Periodic export verification.** Produce a full
  export of the ledger (or a statistically
  meaningful sample) periodically — once a quarter
  is reasonable — and verify it independently of
  the vendor. This exercises the export pathway,
  surfaces problems before they are urgent, and
  provides evidence of the migration playbook
  being executable.

Programs that have never tested their export have no
honest understanding of their migration risk.

## 6.5 The CAO contribution

As in `mod-106` §6.5, the choice itself is
engineering-and-security-led. The CAO's distinct
contributions:

- **The requirements.** What evidence the
  infrastructure must produce, what audiences it
  must serve, what regulatory obligations it must
  satisfy. Chapters 1–5 are, in effect, the
  requirements document the CAO brings to the
  decision.
- **The risk assessment.** Vendor dependency
  analysis, migration-risk assessment, integrity-
  assumption analysis (what has the organisation
  implicitly delegated to the vendor's integrity).
  The CAO function is the one that cares about
  these specifically — the engineering function
  tends to focus on functional capability and the
  security function tends to focus on breach
  posture.
- **The program-level position.** How the chosen
  architecture is described in the program
  charter, in board reports, and to regulators.
  The CAO is the person who will have to defend
  the choice at a regulator meeting; the CAO's
  input to the decision should reflect that
  future conversation.
- **The audit-defensibility assessment.** Will the
  chosen architecture let the program pass its
  anticipated audits — SOC 2, ISO 42001, sector-
  specific exam, regulatory inquiry? This is a
  CAO-specific question the engineering function
  may not evaluate rigorously.

Contributions the CAO should *not* make:

- Vendor selection on technical grounds alone.
  That is engineering's call.
- Architectural design beyond requirements. That is
  engineering's design authority.
- Cost arbitration beyond flagging CAO-material
  concerns. The CFO adjudicates cost.

The CAO who stays in the right lane here is more
useful than the CAO who tries to adjudicate
engineering tradeoffs.

## 6.6 A note on how this choice ages

Audit-ledger infrastructure is one of the choices
that will age the longest. A trust-gate vendor
choice ages at the speed of the trust-architecture
market (fast). A model-provider choice ages at the
speed of the model market (also fast). An audit-
ledger choice ages at the speed of the organisation's
oldest retained evidence — 5–10 years, often longer.

This means: the choice is sticky in both directions.
The organisation lives with the choice longer than
it lives with most procurement decisions, and the
cost of changing it rises monotonically as evidence
accumulates. The decision deserves commensurate
rigour at the time it is made.

## Summary

- Three options: build, buy, partner. The honest
  weaknesses of each are different — build on
  engineering burden and cryptographic risk, buy on
  vendor dependency and migration risk, partner on
  the complexity of running a conscious split.
- The decision matrix should address at least nine
  dimensions, filled in with specific values. The
  CAO's job is ensuring the matrix is populated,
  not populating it alone.
- The dominant pattern in financial services is
  partner (buy the ledger primitives, build the
  vocabulary and package assembly); other sectors
  land differently. The pattern is empirical, not
  prescriptive.
- Migration risk is the sharpest risk in buying.
  Three mitigations: standards-based export
  formats, documented migration playbook, periodic
  export verification.
- The CAO's distinct contributions: requirements,
  risk assessment, program-level position, audit-
  defensibility. The CAO stays out of vendor
  selection on technical grounds, architectural
  design beyond requirements, and cost arbitration.
- Audit-ledger choices age at the speed of the
  organisation's oldest retained evidence, which
  can be a decade or more. The decision warrants
  rigour commensurate with its stickiness.
