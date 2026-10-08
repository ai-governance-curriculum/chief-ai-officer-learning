# Module 104 — Model Risk Management

> Module 104 of the Chief AI Officer track. Model Risk
> Management — the discipline financial services has been
> running for over a decade — applied to AI / ML. SR 11-7 is
> not just an obligation; it is one of the few sources of
> *concrete operational standards* for how to validate,
> monitor, and govern a model. This module makes that
> discipline usable in any context.

## What you will leave with

After working through this module you should be able to:

1. Explain what SR 11-7 actually requires (vs. what people
   say it requires) and why it works.
2. Tier ML models within an SR 11-7-style MRM framework
   without forcing ML into financial-model assumptions.
3. Design an independent validation for an ML model where
   classical challenger-model approaches do not directly
   apply.
4. Author a model inventory entry — including for an LLM —
   that satisfies both SR 11-7 and the CAO program.
5. Resolve the recurring boundary disputes between the
   CAO function and an established MRM function under the
   CRO.
6. Apply the MRM discipline outside banking — healthcare,
   insurance, public sector, industrial.

## Prerequisites

[`mod-101-foundations`](../mod-101-foundations/README.md),
[`mod-102-regulatory-landscape`](../mod-102-regulatory-landscape/README.md),
and [`mod-103-ai-risk-frameworks`](../mod-103-ai-risk-frameworks/README.md).

Particularly relevant:

- mod-102 §4 (sector-specific: SR 11-7 + SR 22-6 + NYDFS).
- mod-103 Chapter 6 (MANAGE in practice; treatment plans).
- mod-101 Chapter 4 (CAO peer-role boundaries, esp. MRM
  under CRO).

## Module layout

```
mod-104-model-risk-management/
├── README.md                                 you are here — chapter index
├── 01-what-sr-11-7-actually-requires.md      the source, read in its own words
├── 02-tiering-ml-models.md                   tiering discipline for ML
├── 03-independent-validation-for-ml.md       validation when challengers break
├── 04-model-lifecycle-with-ml-stops.md       the lifecycle + the two skipped stops
├── 05-model-inventory-for-llms.md            inventory discipline, LLM Supplement
├── 06-cao-mrm-boundary.md                    the second-line peer boundary
├── 07-mrm-outside-banking.md                 healthcare, insurance, public, industrial
├── exercises/                                five exercises (~15 hours total)
├── quiz.md                                   20 questions covering the chapters
└── resources.md                              annotated reading list, source-first
```

## Chapters at a glance

| # | Title | Objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [What SR 11-7 actually requires](./01-what-sr-11-7-actually-requires.md) | Objective 1 | OCC/FRB SR 11-7 — all of it, not the summary |
| 2 | [Tiering ML models](./02-tiering-ml-models.md) | Objective 2 | SR 11-7 §III; sector adaptations |
| 3 | [Independent validation for ML](./03-independent-validation-for-ml.md) | Objective 3 | SR 11-7 §IV; SR 22-6; EBA MRM Guidelines |
| 4 | [The model lifecycle with ML stops](./04-model-lifecycle-with-ml-stops.md) | Supports Objective 3 + 4 | SR 11-7 §III–§VI; FDA PCCP for continuous-learning analog |
| 5 | [Model inventory for LLMs](./05-model-inventory-for-llms.md) | Objective 4 | SR 11-7 §V; CAO inventory practice |
| 6 | [The CAO × MRM boundary](./06-cao-mrm-boundary.md) | Objective 5 | mod-101 §4 + program-level integration |
| 7 | [MRM outside banking](./07-mrm-outside-banking.md) | Objective 6 | NAIC Model Bulletin; FDA PCCP; Canadian Directive; OMB M-25-21 |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Tier 5 ML models per SR 11-7](./exercises/exercise-01-tier-five-ml-models.md) | 3 | Applied | Tier table + reasoning |
| 02 | [Design an independent validation for an ML model](./exercises/exercise-02-design-independent-validation.md) | 4 | Synthesis | Validation plan (≤ 3 pp) |
| 03 | [SR 11-7-compliant inventory entry for an LLM](./exercises/exercise-03-sr-11-7-inventory-entry-for-llm.md) | 2 | Applied | Inventory row + completeness audit |
| 04 | [Resolve a CAO-vs-MRM-lead boundary dispute](./exercises/exercise-04-cao-vs-mrm-boundary-dispute.md) | 3 | Analytical | Memo + boundary diagram |
| 05 | [Apply MRM outside banking](./exercises/exercise-05-mrm-outside-banking.md) | 3 | Synthesis | MRM-equivalent program for a non-bank context |

## A note on the source material

SR 11-7 is short (about 21 pages). It is also dense; every
sentence is doing work. The chapters summarise it but
**you should read the actual document**. The Playbook-style
guidance most people cite is downstream of the source. When
the citation and the source disagree, the source wins.

## How this module fits

mod-103 gave you the daily operating loop
(MAP → MEASURE → MANAGE → GOVERN). mod-104 deepens the
MANAGE and MEASURE discipline for model-class risk under
the most-developed external standard. Downstream modules
build on what this one establishes:

- **mod-105 (Responsible AI & Ethics)** layers the ethics
  dimension over the MRM discipline.
- **mod-107 (AI Security)** deepens the adversarial /
  stress / red-team patterns from Chapter 3.
- **mod-108 (Audit Ledgers & Evidence)** hardens the
  evidence trail behind the validation and inventory
  artifacts.
- **mod-109 (Compliance Operations)** operationalises
  model inventory and tiering against specific regimes.
- **mod-111 (Board Reporting)** rolls the MRM report into
  the board risk pack.

## Paired solutions repo

[`chief-ai-officer-solutions / modules/mod-104-model-risk-management`](https://github.com/ai-governance-curriculum/chief-ai-officer-solutions/tree/main/modules/mod-104-model-risk-management)

Same conventions as mod-101, mod-102, and mod-103 — worked
answers, not the answer.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
