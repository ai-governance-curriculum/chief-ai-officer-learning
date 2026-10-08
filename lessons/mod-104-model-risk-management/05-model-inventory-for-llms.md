# Chapter 5 — Authoring Model Inventory Entries, Including for LLMs

## Why this chapter exists

SR 11-7 §V requires a *comprehensive set of model
documentation*, including an inventory of all models in
use, under development, or recently retired. The
inventory is the single most consulted artifact in an
MRM program:

- Examiners open with "show me the inventory."
- Internal audit samples from the inventory to pick
  what to audit.
- The MRM function uses it to plan validation and
  monitoring workload.
- The CAO function uses it to find AI systems that may
  carry obligations the model team has not thought of
  (EU AI Act high-risk flagging, affected-party
  transparency).
- The CRO uses it for board-level risk reporting.

Classical model inventories were designed for
econometric and statistical models. The fields they
require map cleanly to a logistic-regression credit
model and poorly to an LLM-based system. Programs
that force LLM entries into classical templates either
produce misleading records or leave fields blank
("n/a") in ways that hide important information.

This chapter develops the discipline of authoring an
inventory entry that satisfies both SR 11-7 and the
CAO program, with special attention to LLM-class
systems. Exercise 03 forces the discipline onto a
specific LLM customer-service agent.

## What SR 11-7 requires in the inventory

Read §V carefully. The guidance identifies specific
inventory requirements: unique identifier, model name,
type, developer, use, limitations, performance, and so
on. The intent is that the inventory be
*comprehensive enough to support the four pillars*. The
test: can MRM plan validation and monitoring from the
inventory alone? If no, the inventory is incomplete.

Note what the source does *not* prescribe:

- A specific field schema. Firms design their own
  templates within the comprehensive-support bar.
- A single-document form. Many firms use a tabular
  inventory plus linked detail documents.
- A specific retention period. Firm policy, aligned with
  record-retention regulation.

The design room is where LLM-class extensions can go
without breaking SR 11-7 compatibility.

## The classical inventory template

A representative classical template, derived from large-
bank MRM practice:

| Field | What it holds (classical form) |
|---|---|
| Model ID | Sequential or structured identifier |
| Model name | Descriptive — recognizable to the business |
| Model type | Statistical / econometric / mixed |
| Model owner (role) | Named role (not a person) in the first line |
| Model purpose | Business use — one or two sentences |
| Inputs (named) | Named data sources, refresh cadence |
| Outputs (named) | Specific quantitative outputs |
| Methodology summary | High-level description of the technique |
| Implementation environment | Where it runs (platform, hosting) |
| Development date | When built |
| Last validation | Date + outcome |
| Tier | Tier per MRM policy |
| Material limitations | Known model limitations |
| Performance metrics | Currently-tracked metrics |
| Material changes since last validation | Log |
| Vendor (if any) | Vendor + product |

For a classical credit model this template works. Each
field has a clean populated form; the fields together
cover what §V asks for.

## Where the classical template breaks for LLMs

Apply the template to a vendor-hosted customer-service
LLM agent and the mismatches surface quickly:

- **Model type.** "LLM (vendor-hosted)" is accurate but
  does not convey the composition — foundation model +
  prompt template + retrieval + guardrails. The field
  under-specifies what is being governed.
- **Methodology summary.** For a vendor-hosted LLM the
  firm does not know the methodology (training data,
  architecture, RLHF details). The field forces a vendor
  description that the firm cannot vouch for.
- **Inputs (named).** The user conversation is an input;
  so is the retrieval corpus; so is the prompt template.
  The field was designed for enumerable feature inputs
  and does not naturally handle the user text as input.
- **Outputs (named).** LLM output is generative text,
  not an enumerable quantitative output. "Natural
  language response" is accurate and uninformative.
- **Material limitations.** For an LLM, limitations are
  often behavioural (what the model will refuse, what
  topics are out-of-scope, what hallucination rate was
  observed) rather than statistical. The field was
  designed for the latter.
- **Performance metrics.** For an LLM there is often no
  ground-truth-based metric. The field forces a number
  that is misleading.

Programs that populate these fields with the obvious
transliteration end up with inventories that read
*legalistically* — technically filled in, operationally
uninformative. The MRM function cannot plan validation
from the inventory because the inventory does not
describe the thing being validated.

## The missing fields for LLMs

A working LLM inventory entry needs fields the classical
template does not have:

- **Foundation model version pinning.** Which vendor
  model is in use; what version string pins it;
  what is the firm's policy when the vendor announces a
  swap (immediate accept, N-day evaluation window,
  negotiated hold).
- **Prompt template version.** The prompt is part of the
  system. A prompt-template version is a referenceable
  artifact (ideally a git commit hash on a prompt
  repository) with an owner and a change log.
- **Retrieval index / RAG corpus description.** If the
  system has retrieval, the corpus — scope, refresh
  cadence, chunking strategy, embedding model and
  version, access controls — is as load-bearing as the
  model.
- **Guardrail / output-filter configuration.** What
  content filters, PII scrubbing, refusal rules, and
  post-processors are applied. Which are vendor-provided;
  which are firm-configured.
- **Evaluation set provenance.** How the evaluation set
  was constructed; how often it is refreshed; what
  separates it from training data (critical for vendor
  foundation models that may have been trained on
  public evaluation sets).
- **Deployment-time guardrails.** Rate limiting, user
  authentication, session boundaries, input length
  limits.
- **Behavioural envelope.** A statement of what the
  system is expected to do and expected *not* to do;
  this is the misuse-detection yardstick.
- **Human-in-loop configuration.** Where and how a human
  reviews, overrides, or escalates. For misuse
  (SR 11-7's second source of model risk, per Chapter 1)
  this is the first-line control.

Each of these is an SR 11-7-compatible extension — none
of them contradict the guidance, and all of them are
within the firm's design room under §V's "comprehensive
set of documentation" language.

## The LLM Supplement pattern

A clean way to extend the inventory without breaking
compatibility with classical models: an **LLM Supplement**
section that classical models leave blank, and that LLM-
class models populate.

The classical fields remain. For each LLM entry the
Supplement adds structured fields for:

| LLM Supplement field | Populated form |
|---|---|
| Foundation model + version pinning | Vendor + model string + pinning policy |
| Prompt template version | Reference (git hash or repo + tag) + owner |
| Retrieval corpus | Scope + refresh cadence + embedding model + access controls |
| Guardrails / output filters | Firm config + vendor config, with ownership |
| Behavioural envelope | Short statement: expected uses and expected refusals |
| Evaluation set | How constructed, how refreshed, contamination posture |
| Human-in-loop | Where in the workflow, with what authority, with what logging |
| Prompt-template change policy | Who approves prompt changes; which changes trigger re-validation (per Chapter 3) |

A single inventory template with "if LLM, also populate
the Supplement" is simpler than two parallel templates
and preserves the single-source-of-truth property that
makes the inventory valuable.

## Fields that remain, with adapted content

Many classical fields still apply to LLMs; the content is
adapted:

- **Model type:** "LLM (vendor-hosted, foundation
  model + prompt template + RAG)" with the composition
  made explicit.
- **Model owner:** named role in the first line; usually
  the engineering lead for the product that embeds the
  LLM.
- **Model purpose:** the business decision influenced,
  with specificity (not "customer service" but "handles
  customer inquiries about X category of question;
  routes Y category to humans").
- **Inputs:** adapted to list the categories of input
  (user conversation; retrieved documents; system
  prompt; conversation history) rather than named
  features.
- **Outputs:** adapted to describe the output surface
  (free-form text responses; structured tool-call
  outputs if any) rather than a single quantitative
  output.
- **Material limitations:** behavioural — observed
  hallucination rate on the evaluation set; refusal
  behaviour; known failure modes from red-team findings.
- **Performance metrics:** per Chapter 3 — human-rater
  scores with inter-rater reliability, red-team
  pass-rate, subgroup-fairness measures, override rate
  as a proxy.
- **Material changes since last validation:** every
  prompt-template change, every vendor foundation-model
  swap, every retrieval-corpus refresh above threshold.

## What the inventory is for, revisited

Three uses of the inventory that drive what it must
contain:

- **Planning validation.** Can MRM determine from the
  inventory what validation patterns to apply? For an
  LLM entry that means knowing the behavioural envelope,
  the evaluation-set posture, and the guardrail
  configuration. Without those fields, validation
  planning is guesswork.
- **Supporting examination.** An examiner asks "how do
  you know this LLM is not making prohibited
  statements?" The inventory should answer: here is the
  guardrail configuration, here is the evaluation
  evidence, here is the last red-team run, here is the
  monitoring. If the inventory cannot answer, the firm
  is reconstructing live.
- **Supporting incident response.** When an incident
  occurs on an LLM system, the inventory should let
  responders answer: what version of what model with
  what prompt template was running when the incident
  occurred, and which guardrail was supposed to catch
  this? Inventories that cannot answer this question
  within minutes extend incident response substantially.

An inventory that supports all three uses is doing its
job. One that supports only "we have an inventory" is
ceremonial.

## Cross-reference to the CAO's AI system inventory

The CAO function typically maintains a parallel inventory
of **AI systems** (not models). The two inventories are
not the same artifact:

- MRM's model inventory lists *models* — one row per
  model, including non-AI quantitative models that are
  outside the CAO's AI scope.
- The CAO's AI system inventory lists *AI systems* —
  one row per system, which may contain multiple models
  or a model composed with non-model components. The
  system-level view is what EU AI Act Article 11
  (technical documentation) is scoped to.

The two inventories must point at each other. A row in
MRM's inventory for a vendor-hosted LLM should link to
the CAO's row for the AI system that embeds it; the
CAO's row should link back. A single-click traversal in
both directions is the operational test. Chapter 6
develops the CAO × MRM boundary in which these two
inventories live.

## Common inventory failures

Patterns that look like a filled-in inventory and are
not usable:

- **The "n/a — not applicable" field.** A field marked
  n/a without a reason hides whether the field was
  genuinely inapplicable or whether no one knew the
  answer. The convention "n/a — <reason>" makes the
  distinction visible.
- **The ghost-model inventory.** Models listed as active
  that have not been meaningfully validated or monitored
  in two years. Usually a symptom of a missing Stop 9
  (retirement) discipline from Chapter 4.
- **The frozen prompt-template field.** A single
  "prompt template version" entry that never changes
  while the engineering team routinely updates the
  prompt. The field exists; the discipline does not.
- **The vendor-opaque fields.** Methodology, training
  data, limitations all listed as "vendor-proprietary"
  for a vendor LLM. The response under examination is
  "then what do we know about this system?" — the
  firm must have *something* beyond vendor marketing.
- **Parallel inventories that diverge.** MRM's inventory
  and the CAO's AI system inventory contain different
  entries, with different fields, that both claim to
  cover the same portfolio. An audit that opens one and
  then the other finds the inconsistency fast.

## Summary

- The model inventory is the single most consulted MRM
  artifact. Examiners, auditors, incident responders,
  and the board all enter the program through it.
- Classical inventory templates mismap to LLMs on
  methodology, inputs, outputs, limitations, and
  performance metrics. Filling them in legalistically
  produces inventories that read right and are
  operationally useless.
- The missing LLM fields — foundation-model version
  pinning, prompt-template version, retrieval corpus,
  guardrails, behavioural envelope, evaluation-set
  provenance, human-in-loop — can be added as an LLM
  Supplement without breaking classical-model
  compatibility.
- Inventories are tested by three uses: planning
  validation, supporting examination, supporting
  incident response. An inventory that cannot support
  these is ceremonial.
- MRM's model inventory and the CAO's AI system
  inventory are different artifacts that must
  cross-reference. Divergence between them is a visible
  audit finding.
