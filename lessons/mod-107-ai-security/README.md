# Module 107 — AI Security and Adversarial Defense

> Module 107 of the Chief AI Officer track. AI security
> *from the CAO perspective* — not engineering depth, but
> program-level fluency. The technical defence work belongs
> to the CISO and the engineering organisation. The CAO's
> job is knowing what good looks like, where the boundary
> with the CISO function sits, and how AI-specific attacks
> get classified, escalated, and reported.

## What you will leave with

After working through this module you should be able to:

1. Distinguish AI-specific attack categories that are live
   threats in 2026 from those that remain theoretical, and
   explain why.
2. Use MITRE ATLAS, OWASP LLM Top 10, and NIST AI 100-2
   E2023 to threat-model an AI system without flattening
   them into a single checklist.
3. Apply defense-in-depth to AI systems beyond the
   classical-perimeter framing.
4. Specify red-teaming and adversarial evaluation as a
   governance practice — what gets done, how often, by
   whom, with what evidence.
5. Operate the CAO × CISO boundary cleanly — distinct from
   the CAO × MRM boundary (`mod-104` Chapter 6) but with
   parallel discipline.
6. Author an AI-incident classification taxonomy that
   distinguishes security incidents, AI-program incidents,
   and the joint cases.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md) through
[`mod-106`](../mod-106-trust-architecture/README.md).

Particularly relevant:

- `mod-103` §2 (risk taxonomy — security as a category).
- `mod-104` Chapter 6 (CAO × MRM boundary — the structural
  parallel for Chapter 5 of this module).
- `mod-106` (trust architecture) — defines the positive
  control surface; this module operates on the
  adversarial perspective.

This module **pairs with** `ai-infra-security-learning`,
which carries the engineering-depth treatment of the same
surface. The CAO who can engage substantively with the
engineering organisation on AI security needs both — but
the two modules approach the topic from different angles
and need not be read in either order.

## Module layout

```
mod-107-ai-security/
├── README.md                                        you are here — chapter index
├── 01-ai-threat-landscape-real-vs-hype.md           real vs theoretical threats
├── 02-attack-taxonomies.md                          ATLAS, OWASP, NIST 100-2 composed
├── 03-defense-in-depth-for-ai.md                    the nine-layer model
├── 04-red-teaming-as-governance.md                  governance-grade adversarial evaluation
├── 05-cao-ciso-boundary.md                          the second peer-function boundary
├── 06-ai-incident-classification.md                 three-category taxonomy + routing
├── exercises/                                       five exercises (~16 hours total)
├── quiz.md                                          20 questions covering the chapters
└── resources.md                                     annotated reading list, standards-first
```

## Chapters at a glance

| # | Title | Objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [The AI threat landscape — real vs hype](./01-ai-threat-landscape-real-vs-hype.md) | Objective 1 | AI Incident Database; ATLAS case studies; AVID; sector-ISAC advisories |
| 2 | [Attack taxonomies](./02-attack-taxonomies.md) | Objective 2 | MITRE ATLAS; OWASP LLM Top 10 (2025); NIST AI 100-2 E2023; NIST AI 600-1 |
| 3 | [Defense-in-depth for AI systems](./03-defense-in-depth-for-ai.md) | Objective 3 | NIST SP 800-39; NIST SP 800-53; AI-specific layer additions |
| 4 | [Red-teaming as governance practice](./04-red-teaming-as-governance.md) | Objective 4 | EU AI Act Articles 51–55 (GPAI); NIST AI 600-1 MEASURE; practitioner cadence patterns |
| 5 | [The CAO × CISO boundary](./05-cao-ciso-boundary.md) | Objective 5 | `mod-104` Chapter 6 structural pattern; CAO × CISO specifics |
| 6 | [AI incident classification](./06-ai-incident-classification.md) | Objective 6 | EU AI Act Art. 73; NYDFS Part 500 §500.17; GDPR Art. 33/34; sector incident regimes |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Threat-model an AI system using MITRE ATLAS](./exercises/exercise-01-threat-model-mitre-atlas.md) | 3 | Applied | ATLAS-aligned threat model |
| 02 | [Design a red-team exercise](./exercises/exercise-02-design-red-team-exercise.md) | 4 | Synthesis | Exercise design + scoring rubric |
| 03 | [Resolve a CAO-vs-CISO boundary dispute](./exercises/exercise-03-cao-vs-ciso-boundary-dispute.md) | 3 | Analytical | Boundary memo + diagram |
| 04 | [Build an AI incident classification taxonomy](./exercises/exercise-04-ai-incident-classification.md) | 3 | Applied | Taxonomy + routing rules |
| 05 | [Author a defense-in-depth program standard](./exercises/exercise-05-defense-in-depth-standard.md) | 3 | Applied | Standard document |

## A note on tone

AI security is one of the topics where the CAO most often
gets pulled into engineering detail beyond program-level
relevance. The module's voice is deliberately disciplined
about staying at the program level. Engineering-depth
questions go to the security engineering organisation and
to `ai-infra-security-learning`. The CAO's job is the
program structure that the engineering work delivers
against.

## How this module fits

`mod-106` built the positive control surface — trust
architecture. `mod-107` is the adversarial complement:
what breaks the control surface, how to classify what
has broken, who leads the response. Downstream modules
build on this:

- **mod-108 (Audit Ledgers & Evidence).** Tamper-evident
  logging is the audit complement to incident
  classification; the signed events that incident
  response produces live in the ledger.
- **mod-109 (Compliance Operations).** The cross-walks
  between security incidents and regulatory obligations
  are an operational discipline there.
- **mod-110 (Incident Response).** Operational treatment
  of incident response across both security and
  AI-program dimensions, picking up where Chapter 6
  leaves off.
- **mod-111 (Board Reporting).** The security posture
  rolls up into the Board risk pack with specific tracked
  indicators.

## Paired solutions repo

[`chief-ai-officer-solutions / modules/mod-107-ai-security`](https://github.com/ai-governance-curriculum/chief-ai-officer-solutions/tree/main/modules/mod-107-ai-security)

Same conventions as `mod-101` through `mod-106` — worked
answers, not the answer.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
