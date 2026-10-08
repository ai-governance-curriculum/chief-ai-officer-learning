# Module 108 — Audit Ledgers and Evidence

> Module 108 of the Chief AI Officer track. Tamper-
> evident logging, evidence packages, and signed
> exports — the infrastructure that lets the AI
> program *prove what happened*. Most CAO programs
> can describe their controls; programs that survive
> external scrutiny can also produce the evidence
> that the controls operated.

## What you will leave with

After working through this module you should be able to:

1. Distinguish operational logging from audit-grade
   evidence and explain why most production logging
   does not meet the latter standard.
2. Apply the Merkle-tree / hash-chain pattern
   (RFC 9162) to AI audit ledgers without forcing the
   cryptographic structure to carry organisational
   expectations it was not designed for.
3. Specify an event vocabulary at the right
   granularity for an AI system — comprehensive
   enough to support audit, narrow enough to remain
   maintainable.
4. Author an evidence package for a specific
   regulator or auditor request, including
   completeness, signing, and chain of custody.
5. Design retention, sealing, and chain-of-custody
   policies (with RFC 3161 timestamping) that
   survive an adversarial review.
6. Make build / buy / partner decisions for audit-
   ledger infrastructure at enterprise portfolio
   scope.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md) through
[`mod-107`](../mod-107-ai-security/README.md).

Particularly relevant:

- `mod-106` (Trust Architecture) — defines the
  positive control surface; the audit ledger is
  the *evidence layer* of that surface.
- `mod-107` (Security) — defines the threat surface
  the evidence layer must survive.
- `mod-103` §6 (GOVERN continuously) — evidence is
  the GOVERN output that lower functions feed into.
- `mod-102` §2 (EU AI Act) — Art. 12 (record-keeping)
  is one of the article-level obligations evidence
  must satisfy.

## Module layout

```
mod-108-audit-ledgers-and-evidence/
├── README.md                                              you are here — chapter index
├── 01-operational-logging-vs-audit-grade-evidence.md      the distinction and three audiences
├── 02-the-tamper-evident-ledger-pattern.md                Merkle, hash chains, RFC 9162
├── 03-event-vocabulary-for-ai-systems.md                  granularity, completeness, registry
├── 04-evidence-packages.md                                curating signed artifacts for audiences
├── 05-retention-sealing-and-chain-of-custody.md           retention, RFC 3161 sealing, custody discipline
├── 06-build-buy-or-partner-for-audit-ledgers.md           enterprise decision framework
├── exercises/                                             five exercises (~16 hours total)
├── quiz.md                                                20 questions covering the chapters
└── resources.md                                           annotated reading list, standards-first
```

## Chapters at a glance

| # | Title | Objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [Operational logging vs audit-grade evidence](./01-operational-logging-vs-audit-grade-evidence.md) | Objective 1 | EU AI Act Art. 12; NYDFS Part 500 §500.06; SOC 2 / ISO 42001 evidence expectations |
| 2 | [The tamper-evident ledger pattern](./02-the-tamper-evident-ledger-pattern.md) | Objective 2 | RFC 9162 (Certificate Transparency v2.0); RFC 6962 (CT v1); Merkle-tree and hash-chain primitives |
| 3 | [Event vocabulary for AI systems](./03-event-vocabulary-for-ai-systems.md) | Objective 3 | OpenTelemetry GenAI semantic conventions; CloudEvents 1.0; practitioner vocabularies |
| 4 | [Evidence packages](./04-evidence-packages.md) | Objective 4 | Auditor expectations; regulator inquiry patterns; litigation discovery discipline |
| 5 | [Retention, sealing, and chain of custody](./05-retention-sealing-and-chain-of-custody.md) | Objective 5 | EU AI Act Art. 12 retention; RFC 3161 Time-Stamp Protocol; records-management practice |
| 6 | [Build, buy, or partner for audit ledgers](./06-build-buy-or-partner-for-audit-ledgers.md) | Objective 6 | `mod-106` §6 framework; vendor-landscape survey (2026) |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Design event vocabulary for a system](./exercises/exercise-01-design-event-vocabulary.md) | 3 | Applied | Vocabulary + emission specification |
| 02 | [Author an evidence package for a regulator request](./exercises/exercise-02-evidence-package-for-regulator.md) | 4 | Synthesis | Complete evidence package |
| 03 | [Design a Merkle-chained ledger structure](./exercises/exercise-03-design-merkle-ledger-structure.md) | 3 | Synthesis | Ledger design + verification protocol |
| 04 | [Author retention and chain-of-custody policy](./exercises/exercise-04-retention-and-chain-of-custody-policy.md) | 3 | Applied | Policy document |
| 05 | [Build / buy decision for the audit ledger](./exercises/exercise-05-build-vs-buy-audit-ledger.md) | 3 | Synthesis | Decision matrix + recommendation |

## A note on tone

Evidence work has a deceptive surface — it looks like
administrative work compared to the higher-profile
governance, security, or model topics. In practice the
evidence layer is where most CAO programs collapse
under regulator scrutiny. The discipline is taking the
infrastructure seriously even though it is the
quietest part of the program.

## How this module fits

`mod-106` built the positive control surface — trust
architecture. `mod-107` named the adversarial surface
that control must survive. `mod-108` is where the
operations of both become durable: the signed events
that the trust gates emit, that incident response
produces, that board reporting rounds up, all land in
the ledger this module designs. Downstream modules
build on this foundation:

- **mod-109 (Compliance Operations)** — the
  regulator-facing operations that use the evidence
  this module produces.
- **mod-110 (Incident Response)** — the operational
  use of evidence in post-incident review and
  regulator notification.
- **mod-111 (Board Reporting)** — the roll-up from
  evidence to board-level reporting with
  traceability back to signed records.

## Paired solutions repo

[`chief-ai-officer-solutions / modules/mod-108-audit-ledgers-and-evidence`](https://github.com/ai-governance-curriculum/chief-ai-officer-solutions/tree/main/modules/mod-108-audit-ledgers-and-evidence)

Same conventions as `mod-101` through `mod-107` —
worked answers, not the answer.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
