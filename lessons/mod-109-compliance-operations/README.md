# Module 109 — Compliance Operations

> Module 109 of the Chief AI Officer track. Compliance
> operations — the discipline of turning regulatory
> obligations into a continuous operating practice
> rather than a quarter-end scramble. This is where the
> obligations register from `mod-102` meets the evidence
> layer from `mod-108` and the program standards from
> `mod-105` through `mod-107` become operational.

## What you will leave with

After working through this module you should be able to:

1. Distinguish compliance operations from compliance,
   audit, policy, and governance — and explain why a
   program with strong compliance opinion but weak
   operations still fails regulator reviews.
2. Apply the control-mapping discipline to turn an
   abstract regulatory obligation into a specific
   testable control with named owner, cadence, and
   evidence.
3. Specify a continuous-evidence cadence for an
   obligation — what is collected, how often, where it
   lives, who reviews, and how review failure is
   detected.
4. Identify which compliance work warrants
   automation and which warrants explicit non-
   automation, including the vendor-landscape
   trade-offs.
5. Use ISO/IEC 42001:2023 Annex A as a working control
   catalog for an AI program — including its
   limitations and the sector overlays it needs.
6. Operate the CAO × Chief Compliance Officer peer
   boundary cleanly — distinct from the CAO × MRM and
   CAO × CISO boundaries.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md) through
[`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md).

Particularly relevant:

- `mod-102` §6 (jurisdictional mapping discipline) —
  this module operationalises that discipline.
- `mod-103` Chapter 6 (GOVERN continuously) —
  compliance operations is the GOVERN function at the
  obligation level.
- `mod-108` (audit ledgers + evidence) — the evidence
  infrastructure compliance operations rests on.
- `mod-104` Chapter 6 and `mod-107` Chapter 5 — the
  CAO × MRM and CAO × CISO peer-boundary chapters that
  Chapter 6 of this module parallels.

## Module layout

```
mod-109-compliance-operations/
├── README.md                                           you are here — chapter index
├── 01-what-compliance-operations-is.md                 operations vs its four neighbours
├── 02-control-mapping.md                               obligations → testable controls
├── 03-continuous-evidence-collection.md                cadence, patterns, failure modes
├── 04-compliance-automation.md                         what to automate, what not to
├── 05-iso-42001-annex-a-as-control-catalog.md          Annex A as working catalog, with limits
├── 06-cao-compliance-officer-boundary.md               the third peer-boundary chapter
├── exercises/                                          five exercises (~15 hours total)
├── quiz.md                                             20 questions covering the chapters
└── resources.md                                        annotated reading list, standards-first
```

## Chapters at a glance

| # | Title | Objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [What compliance operations is (and isn't)](./01-what-compliance-operations-is.md) | Objective 1 | NIST AI RMF GOVERN; ISO/IEC 42001 §9 performance evaluation |
| 2 | [Control mapping](./02-control-mapping.md) | Objective 2 | ISO/IEC 42001 Annex A; NIST AI RMF Playbook crosswalks |
| 3 | [Continuous evidence collection](./03-continuous-evidence-collection.md) | Objective 3 | `mod-108` evidence infrastructure; practitioner cadence patterns |
| 4 | [Compliance automation](./04-compliance-automation.md) | Objective 4 | Vendor-landscape survey (2026); automation-trap failure patterns |
| 5 | [ISO/IEC 42001 Annex A as control catalog](./05-iso-42001-annex-a-as-control-catalog.md) | Objective 5 | ISO/IEC 42001:2023 Annex A + ISO/IEC 42005:2025 impact assessment |
| 6 | [The CAO × Chief Compliance Officer boundary](./06-cao-compliance-officer-boundary.md) | Objective 6 | `mod-101` §4 peer-role structure; `mod-104` Ch. 6 + `mod-107` Ch. 5 parallels |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Map a regulation to controls and evidence](./exercises/exercise-01-map-regulation-to-controls.md) | 3 | Applied | Control mapping table |
| 02 | [Design a continuous-evidence cadence](./exercises/exercise-02-continuous-evidence-cadence.md) | 3 | Applied | Cadence specification |
| 03 | [Build a control-coverage gap analysis](./exercises/exercise-03-control-coverage-gap-analysis.md) | 3 | Analytical | Gap analysis + remediation roadmap |
| 04 | [Decide what to automate](./exercises/exercise-04-compliance-automation-framework.md) | 3 | Synthesis | Automation framework + decisions |
| 05 | [Resolve a CAO × Compliance Officer boundary](./exercises/exercise-05-cao-vs-compliance-officer-boundary.md) | 3 | Analytical | Resolution memo + boundary diagram |

## A note on tone

Compliance operations has a deceptive surface — it
looks like administrative work next to the higher-
profile responsible-AI, security, or trust-
architecture modules. In practice this layer is where
most CAO programs collapse under regulator scrutiny.
The discipline is taking the operational machinery
seriously even when the rest of the executive table
assumes "we have a Compliance function" is answer
enough.

## How this module fits

`mod-102` built the obligations register. `mod-105`,
`mod-106`, and `mod-107` built the program standards.
`mod-108` built the evidence infrastructure. `mod-109`
is where the three strands become a continuously
operated practice: obligations map to controls,
controls emit evidence into the ledger, review
cadences keep the controls operating, and the
Annex-A-shaped catalog gives auditors and regulators a
coherent surface to examine. Downstream modules build
on this foundation:

- **`mod-110` (Incident Response)** — the operational
  treatment of obligations triggered by incidents.
- **`mod-111` (Board Reporting)** — where compliance
  operations roll up to executive accountability.
- **`mod-112` (CAO Operating Model)** — the overall
  function design that keeps compliance operations
  sustained.

## Paired solutions repo

[`chief-ai-officer-solutions / modules/mod-109-compliance-operations`](https://github.com/ai-governance-curriculum/chief-ai-officer-solutions/tree/main/modules/mod-109-compliance-operations)

Same conventions as `mod-101` through `mod-108` —
worked answers, not the answer.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
