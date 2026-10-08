# Module 105 — Responsible AI and Ethics

> Module 105 of the Chief AI Officer track. The ethics layer
> on top of the risk, regulatory, and MRM discipline built
> in mod-101 through mod-104. *Ethics* is the part of AI
> governance most prone to soft language and box-checking.
> This module insists on operational specificity.

## What you will leave with

After working through this module you should be able to:

1. Explain why AI ethics is a distinct discipline from
   compliance and risk management — and where the
   boundaries are honest.
2. Navigate the principles landscape (OECD, IEEE 7000,
   UNESCO, Asilomar, NIST, EU HLEG) without treating them
   as interchangeable.
3. Choose bias and fairness metrics with explicit
   awareness of the mathematical impossibility results
   that constrain the choice.
4. Design explainability that is *owed to specific
   audiences*, not just produced for completeness.
5. Build contestability into a deployed system from the
   affected-party's perspective.
6. Carry the external Responsible AI narrative into
   voluntary-code sign-ons (OECD, G7 Hiroshima, EU AI
   Office GPAI Code of Practice, MLCommons AI Safety,
   Partnership on AI) at CAO scope.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md),
[`mod-102`](../mod-102-regulatory-landscape/README.md),
[`mod-103`](../mod-103-ai-risk-frameworks/README.md),
[`mod-104`](../mod-104-model-risk-management/README.md).

Particularly relevant:

- mod-103 §2 (taxonomy) — bias and fairness, transparency,
  privacy as categories.
- mod-104 §3 (validation patterns) — subgroup validation,
  counterfactual evaluation.
- mod-101 §6 (failure modes) — *governance theatre* is the
  ever-present risk in ethics work.

## Module layout

```
mod-105-responsible-ai-and-ethics/
├── README.md                                 you are here — chapter index
├── 01-ethics-vs-compliance-and-risk.md       the honest distinctions
├── 02-the-principles-landscape.md            OECD/UNESCO/IEEE/HLEG/NIST/Asilomar
├── 03-bias-and-fairness.md                   metrics, impossibility, subgroups
├── 04-explainability-by-audience.md          regulator, validator, affected party
├── 05-contestability-and-recourse.md         six elements + anti-patterns
├── 06-voluntary-code-signons.md              OECD/G7/GPAI-CoP/MLCommons/PAI
├── 07-operationalizing-ethics.md             standards, Board, pressure, survival
├── exercises/                                five exercises (~15 hours total)
├── quiz.md                                   20 questions covering the chapters
└── resources.md                              annotated reading list, source-first
```

## Chapters at a glance

| # | Title | Objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [Ethics vs compliance and risk](./01-ethics-vs-compliance-and-risk.md) | Objective 1 | mod-101 §1 (neighbors of governance); OECD AI Principles; NIST AI RMF preamble |
| 2 | [The principles landscape](./02-the-principles-landscape.md) | Objective 2 | OECD; UNESCO; IEEE 7000 series; EU HLEG; NIST AI RMF; Asilomar; Microsoft RAI |
| 3 | [Bias and fairness](./03-bias-and-fairness.md) | Objective 3 | Chouldechova (2017); Kleinberg et al. (2016); Selbst et al. (2019); CFPB Circular 2022-03; CO Reg 10-1-1 |
| 4 | [Explainability by audience](./04-explainability-by-audience.md) | Objective 4 | EU AI Act Arts 11/13/14/86; CFPB Circular 2022-03; Mitchell et al. (2019) Model Cards; Gebru et al. (2018) Datasheets |
| 5 | [Contestability and recourse](./05-contestability-and-recourse.md) | Objective 5 | EU AI Act Art. 14; GDPR Art. 22; CFPB / Reg B / ECOA; FCRA; CO SB 24-205 |
| 6 | [Voluntary codes at CAO scope](./06-voluntary-code-signons.md) | Objective 6 | OECD AI Principles 2024; G7 Hiroshima Code of Conduct; EU AI Office GPAI CoP (Art. 56); MLCommons AILuminate; Partnership on AI |
| 7 | [Operationalizing ethics](./07-operationalizing-ethics.md) | Supports Objectives 1–6 | mod-101 §5 (Review Board); mod-108 (evidence); mod-111 (board reporting) |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Compare three ethics frameworks and find the operational disagreement](./exercises/exercise-01-compare-three-ethics-frameworks.md) | 3 | Analytical | Comparison table + operational-disagreement memo |
| 02 | [Define bias metrics for a specific context](./exercises/exercise-02-define-bias-metrics.md) | 3 | Applied | Metric set + trade-off reasoning + impossibility analysis |
| 03 | [Design an explainability standard](./exercises/exercise-03-design-explainability-standard.md) | 3 | Applied | Standard document covering 3+ audiences |
| 04 | [Build a contestability process](./exercises/exercise-04-build-contestability-process.md) | 3 | Applied | Process design + worked example |
| 05 | [Resolve a hard ethics case](./exercises/exercise-05-resolve-ethics-case-study.md) | 3 | Synthesis | Decision memo with reasoning |

## A note on tone

This module's voice is deliberately direct about a topic
that often invites vagueness. *Ethics theater* (mod-101 §6
governance theatre dressed in ethics vocabulary) is the
single biggest failure mode of CAO ethics work. The chapters
name it and the exercises are structured to resist it.

The discipline this module teaches is being able to give
*specific* answers to *hard* questions. Not always
*correct* answers — reasonable people disagree on hard
ethics questions — but specific ones. A CAO who can give
specific answers and defend them survives external
scrutiny; a CAO who only gives principled answers does
not.

## How this module fits

mod-104 gave you the MRM discipline for model-class risk.
mod-105 layers the ethics dimension over it — the choices
about *which* fairness conception to enforce, *what* is
owed to affected parties, *who* can contest, and *how*
the external Responsible AI narrative is carried into
voluntary-code commitments. Downstream modules build on
what this one establishes:

- **mod-106 (Trust Architecture)** operationalises trust
  gates and identity for AI systems — including the
  contestability design properties from Chapter 5.
- **mod-107 (AI Security)** is where fairness and
  security overlap (adversarial attacks on fairness
  metrics; bias-as-attack-surface).
- **mod-108 (Audit Ledgers & Evidence)** builds the
  evidence machinery behind the standards and sign-on
  reports.
- **mod-109 (Compliance Operations)** operationalises
  the explainability-standard and contestability-process
  artifacts against specific regimes.
- **mod-111 (Board Reporting)** rolls the ethics-function
  performance into the board risk pack.

## Paired solutions repo

[`chief-ai-officer-solutions / modules/mod-105-responsible-ai-and-ethics`](https://github.com/ai-governance-curriculum/chief-ai-officer-solutions/tree/main/modules/mod-105-responsible-ai-and-ethics)

Same conventions as mod-101 through mod-104 — worked
answers, not the answer.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
