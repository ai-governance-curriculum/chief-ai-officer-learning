# Chapter 4 — Explainability by Audience

## Why this chapter exists

Transparency is one of the most over-claimed and
under-specified properties in AI governance. "The model
is explainable" without specifying *what is explained*,
*to whom*, and *in what form* is the most common form of
ethics theater. It is the sentence that reads well in a
brochure and collapses on contact with any specific
audience's actual needs.

The discipline this chapter builds: transparency is
*audience-specific*. What is owed to a regulator is not
what is owed to a customer is not what is owed to an
internal validator. Programs that conflate these
produce documents that satisfy none of the audiences —
too technical for the customer, too thin for the
regulator, too opaque for the validator. A CAO who can
specify the per-audience obligation is a CAO who can
author a defensible explainability standard; Exercise
03 produces exactly that.

## 4.1 The audience taxonomy

Explainability has, at minimum, eight audiences. Each
requires *different content* at *different depth* in a
*different format*.

| Audience | What they need | Why |
|---|---|---|
| Regulator | Complete technical + process documentation; access on demand | To verify compliance and investigate after incidents |
| Internal validator (MRM, audit) | Reproducibility-by-another-competent-professional (SR 11-7 §V) | To independently verify the model's fitness |
| Senior management / board | Risk-shaped summary with material findings | To exercise oversight at scale |
| External deployer (e.g., EU AI Act Art. 13) | Operating instructions and limitations | To use the system correctly |
| Affected parties (customers, patients, employees) | Decision-specific explanation + recourse | To understand and contest decisions |
| Affected communities | Aggregate-level system behaviour transparency | To exercise democratic accountability |
| Internal developers / users | Model-behaviour analysis + known limitations | To improve or operate the system |
| Curious external public | High-level descriptions, published model/data documentation | To exercise informed citizenship |

A single "explainability report" that tries to serve all
audiences serves none. The right question is not "is the
model explainable?" but "what explanation is owed to
*which* audience, and does the program produce it on
cadence?"

## 4.2 Regulator-grade transparency

The EU AI Act establishes the most demanding regulator-
grade transparency requirements in current law. Three
articles together define the obligation for providers
of high-risk systems:

- **Art. 11 + Annex IV** — a technical file covering
  roughly a dozen enumerated items: system
  description, design methodology, data governance,
  development process, testing, risk management
  outcomes, performance characteristics, intended
  purpose, known limitations, instructions for use,
  changes, and more.
- **Art. 13** — transparency to deployers (next
  audience; see §4.5).
- **Art. 86** — explanation of individual decisions to
  affected persons for certain high-risk uses.

Member-state authorities and the EU AI Office can
request access to the technical file at any time.

The operational implication: a program that can produce
the Annex IV technical file *on demand* passes
regulator-grade transparency. A program that produces
it under deadline pressure does not — the production
inevitably leaves gaps, inconsistencies, and documents
dated to the week of the request. The discipline is
*continuous* maintenance, not on-demand construction.
mod-108 (audit ledgers and evidence) builds the
continuous-maintenance machinery.

Non-EU jurisdictions have thinner but still real
regulator-grade obligations:

- **US sector regulators** (CFPB, OCC, FDA, NAIC-
  member states) will ask for model documentation,
  validation records, and inventory entries.
  SR 11-7 §V governs the inventory expectation for
  prudentially-regulated banks.
- **Colorado SB 24-205** (effective 2026) requires
  developers and deployers of high-risk AI to make
  specified documentation available to the Colorado
  attorney general on request.
- **NYC Local Law 144** requires published bias-audit
  summaries for automated employment decision tools.

A regulator-grade transparency posture is a *library of
up-to-date documentation*, not an *ability to produce
documentation under pressure*.

## 4.3 Internal-validator transparency

The internal validator audience — MRM, internal audit,
model risk committee — requires something subtly
different from the regulator audience: *reproducibility*.

SR 11-7 §V establishes the standard: another competent
professional should be able to reproduce the model's
development, validation, and monitoring from the
documentation alone, without talking to the original
developer. This is sometimes called the "hit-by-a-bus"
standard — if the development team disappears tomorrow,
can the validation team still do its work?

Reproducibility-grade documentation includes:

- Full data-provenance records (what data, from where,
  under what consent).
- Training-process records (what procedure, what
  hyperparameters, what random seeds, what
  environment).
- Evaluation harness and benchmark results, with the
  harness itself versioned alongside the model.
- Dependency and environment snapshots.
- The reasoning behind design choices (not just the
  choices themselves).

mod-104 §3 covers how this plugs into the independent
validation process. The transparency obligation to the
internal validator is often *higher-content* than the
obligation to the regulator — the regulator asks "did
you do the work?" and the validator asks "can I redo
the work?"

## 4.4 Affected-party transparency

The most contested category. What is owed to a customer
denied credit by an AI system? To a patient flagged for
intervention? To an employee whose performance review
included AI-generated assessment?

### 4.4.1 Three principles that survive operational pressure

1. **The decision must be explainable in terms the
   affected party can act on.** "The model gave you a
   low score" is not actionable. "Your score was
   lowered primarily by the recent drop in your
   average account balance and the high number of
   recent credit inquiries" is — the affected party
   can address those. The CFPB has articulated this
   repeatedly in adverse-action-notice guidance
   (Circular 2022-03 is the pointed version); the
   "principal reasons for the adverse action"
   requirement under ECOA/Reg B requires specificity,
   not generalities.

2. **The explanation must be true.** Post-hoc
   rationalisations that bear no relation to the
   actual model's reasoning are ethically worse than
   no explanation. Some explainability techniques
   (LIME, SHAP) produce explanations that are
   *consistent* with the model's outputs but may not
   reflect the model's actual reasoning — §4.5 of
   this chapter addresses the trap directly.

3. **The explanation must come with a path forward.**
   The affected party needs to know what they can do
   — contest, appeal, modify the inputs, wait for
   re-evaluation. Explanation without recourse is
   information without empowerment. Chapter 5 treats
   contestability and recourse in operational depth.

### 4.4.2 A fourth principle in regulated contexts

In the regulated contexts where affected-party
transparency is a statutory obligation, there is a
fourth principle:

4. **The explanation must be delivered in the medium
   and language required by the regulation.** US
   adverse-action notices must be written notices;
   EU AI Act Art. 86 requires a "clear and meaningful
   explanation"; some jurisdictions require specific
   languages beyond English based on the affected
   population.

A standard that specifies content but not medium
leaves a compliance gap.

### 4.4.3 Example — affected-party explanations side by side

A loan-denial example, in three forms.

- **Transparency theater**: "Your application was
  declined. Our model considered multiple factors."
- **Mechanical explainability**: "Your application
  was declined. SHAP attributions: income (-0.24),
  recent inquiries (+0.18), payment history (-0.07),
  age of accounts (-0.04)."
- **Decision-grade**: "Your application was declined.
  The two factors that most lowered your score were:
  (1) a recent decrease in your reported income
  compared with the past 12 months; (2) three new
  credit inquiries in the past 90 days. You may:
  provide updated income documentation if the recent
  figure is not representative, wait 90 days for the
  inquiry history to age, or appeal this decision
  within 30 days by [specific process]."

Only the third satisfies the three principles.

## 4.5 The mechanical-explainability trap

A common pattern: the program adopts SHAP, LIME, or a
similar attribution technique; outputs feature-
attribution charts to affected parties; declares
transparency achieved. The pattern fails in three
subtle ways:

1. The feature attribution is *consistent with* the
   model but may not be its actual reasoning. Both
   LIME and SHAP are local approximations; multiple
   different approximations are consistent with the
   same model behaviour. The attribution is one
   plausible explanation, not *the* explanation.
2. The attribution is technically correct but
   cognitively opaque to affected parties. A SHAP
   waterfall chart does not tell a loan applicant
   what to *do*.
3. The attribution does not specify what the affected
   party should *do*. Attribution does not imply
   recourse.

This is not an argument against SHAP and LIME. They are
useful tools for *internal* audiences (developers,
validators, incident investigators). The argument is
against treating the *tool output* as transparency in
the §4.4 sense. Transparency is a property of the
relationship between the system and the audience, not
a property of an attribution chart.

A defensible standard treats mechanical-explainability
techniques as *inputs* to the affected-party explanation
(an analyst reviews the attribution to help identify
the principal reasons) rather than as *outputs* delivered
to the affected party verbatim.

### 4.5.1 A note on CFPB Circular 2022-03

The 2022 CFPB Circular made the operational position
explicit for US consumer-finance contexts: *the use of a
complex model does not relieve the creditor of its
obligation to provide specific principal reasons for
adverse action*. The informal "black-box defense" — the
argument that the model's internals are too complex to
explain — is rejected on the record.

The practical implication: if the model's internals do
not support producing specific principal reasons, the
creditor's obligation is to pick a different model, not
to lower the explanation standard.

## 4.6 Process transparency vs. model transparency

Often missed in AI governance: *how a decision was
reached procedurally* is sometimes more important than
*what the model computed*. A patient who knows the
clinical workflow that produced an AI-assisted
recommendation may need that more than a heatmap of
the model's attention.

Process-transparency content:

- Which decisions in a workflow are AI-generated,
  AI-assisted, or human-made.
- Where in the workflow a human reviews the AI output.
- What that human sees (the AI output alone? The AI
  output plus input data? The AI output with
  supporting explanation?).
- What authority the human has to override.
- Where the record of the decision is kept.
- Who has access to that record and under what
  conditions.

A working transparency standard includes process
transparency as a first-class category — not as an
afterthought. For many affected parties, the process
information is the information they most need to
understand and challenge a decision.

### 4.6.1 Deployer transparency as a process-transparency case

The EU AI Act Art. 13 obligation to deployers (the
organisation using a high-risk system, not necessarily
its provider) is a *process-transparency* obligation.
The deployer needs to know:

- The system's intended purpose and known limitations.
- The level of accuracy, robustness, and cybersecurity
  the system has been tested for.
- Any known or foreseeable circumstances under which
  the system may pose a risk.
- Human-oversight measures that are available or
  required.
- Expected lifetime and maintenance/update expectations.

A provider that supplies the technical file (§4.2) but
not the deployer instructions has not met the Art. 13
obligation. The two documents overlap substantially but
have different reading audiences.

## 4.7 Transparency to affected communities

Where affected-party transparency addresses the
individual, affected-*community* transparency addresses
the collective. Mechanisms:

- **Model cards and system cards** — Mitchell et al.
  (2019) *Model Cards for Model Reporting* is the
  canonical reference. Published model cards describe
  intended use, limitations, performance by subgroup,
  and known risks at a level consumable by non-
  experts.
- **Datasheets for datasets** (Gebru et al. 2018) —
  the data-side complement; often more operationally
  important than model cards for understanding
  behaviour.
- **Impact reports** — periodic published reports on
  the aggregate behaviour of deployed AI systems:
  volumes, outcomes, subgroup performance, incident
  rates. Several large US agencies and private firms
  publish these; the discipline is to publish *before*
  external pressure forces it.
- **NYC Local Law 144 bias-audit publications** — the
  statutory version in the employment context.
- **Independent evaluations** — commissioned or
  invited third-party reviews with published findings.

Community-level transparency differs from individual-
level transparency in that the audience is unbounded
and the content is aggregate. Programs that treat
community transparency as "communications" rather than
as part of the ethics discipline risk producing
marketing documents rather than accountability
instruments.

## 4.8 The explainability standard

The operational form of this chapter's content is a
*program-wide explainability standard* that specifies,
per audience type, the content + depth + delivery
format + cadence + owner the program will provide.
Exercise 03 asks you to author one.

A defensible standard is:

- **Short.** 2–3 pages, hard limit. Standards longer
  than this get ignored.
- **Specific.** Standards that include "as required"
  or "as appropriate" are not standards; they are
  wishes.
- **Owner-tagged.** Every requirement names the role
  responsible. Requirements without named owners get
  ignored.
- **Named for failure.** The standard includes what
  happens when a requirement is not met (which role
  escalates to whom, what the system cannot do until
  the requirement is met).

### 4.8.1 Example standard structure

```
TESSERA BANK — EXPLAINABILITY STANDARD v3

1. Scope
   In-scope: Tier 1 and Tier 2 production AI systems
     per TB-TIER-01.
   Out-of-scope: internal productivity assistants with no
     decision influence (see TB-SCOPE-02).

2. Audience-specific obligations
   (a) Affected parties
       Content: principal reasons + path forward (per 4.4)
       Depth: ≤ 150 words, consumer-grade language
       Format: adverse-action notice (ECOA/Reg B compliant)
       Cadence: per-decision
       Owner: Consumer Operations Director
   (b) Internal validators
       Content: reproducibility documentation per TB-MRM-04
       Depth: full technical + evaluation records
       Format: validation package in evidence vault
       Cadence: pre-deployment; on material change
       Owner: Modeling Team Lead
   (c) Regulators (OCC, CFPB, NYDFS)
       Content: SR 11-7-grade inventory + validation
         records + model-change log
       Depth: full
       Format: on-request package via Compliance Liaison
       Cadence: continuously maintained; 72-hour
         production SLA
       Owner: Chief Compliance Officer

3. Explainability-technique posture
   SHAP / LIME: permitted as analyst input only.
     Affected-party explanations derived through
     TB-XAI-01 review process.

4. Process-transparency obligations
   Every production AI system maintains a published
   process diagram (public domain for affected-
   community use) within 30 days of deployment.

5. Failures
   A system that cannot produce the required
   affected-party explanation is deferred by the AI
   Review Board. No deployment without compliant
   explanation capability.
```

The example is deliberately short. A standard this
short that is actually enforced is more valuable than
a 30-page standard that is universally ignored.

## Summary

- Transparency is audience-specific. A single
  explanation serving all audiences serves none.
- Regulator-grade transparency (EU AI Act Art. 11 +
  Annex IV; sector equivalents) is continuous, not
  on-demand.
- Internal-validator transparency is reproducibility-
  grade — the hit-by-a-bus standard. Often higher-
  content than the regulator obligation.
- Affected-party transparency has three (or four)
  principles: actionable, true, with recourse (plus
  regulatory delivery requirements where applicable).
- The mechanical-explainability trap: SHAP / LIME
  attributions are useful tools, not affected-party
  explanations. CFPB Circular 2022-03 rejects the
  black-box defense.
- Process transparency (how a decision was reached) is
  often more important than model transparency (what
  the model computed).
- Community-level transparency uses model cards,
  datasheets, impact reports — mechanisms distinct
  from individual-level transparency.
- The operational form is a short, specific, owner-
  tagged explainability standard that specifies the
  per-audience obligation and failure response.
