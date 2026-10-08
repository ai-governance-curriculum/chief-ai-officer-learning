# Chapter 3 — Independent Validation When Challenger Models Break

## Why this chapter exists

SR 11-7 §IV requires that material model outputs be
*independently validated*. In classical financial-services
MRM, the archetypal validation technique is the
**challenger model** — a separately-built alternative run
against the same data, with disagreements between the
challenger and the production model investigated as
evidence the production model may be wrong.

The challenger pattern works well for well-bounded
econometric and statistical models. It works less well
for ML models and works poorly for LLMs. Programs that
try to force LLM validation into a challenger-model
shape either (a) fail to produce useful signal or
(b) satisfy themselves with a toy challenger that
provides theatre, not validation.

The chapter does three things:

1. Reads §IV in its own words to show that the challenger
   model is one *example* among validation techniques,
   not a requirement.
2. Builds a taxonomy of validation patterns that work for
   ML, with explicit applicability notes.
3. Defines what *independence* means for ML validation
   and what the practical test is.

Exercise 02 forces this discipline onto a Tier 1 credit
model and asks the student to combine patterns.

## What SR 11-7 §IV actually requires

Read §IV directly. The four elements of validation it
identifies are:

1. **Evaluation of conceptual soundness.** Is the model
   well-founded for its intended use? Does the chosen
   method fit the problem? Are the assumptions defensible?
2. **Ongoing monitoring.** Is the model continuing to
   perform as expected in production?
3. **Outcomes analysis.** Are the model's outputs
   consistent with what actually happens?
4. **Benchmarking and comparison.** Does the model
   produce outputs comparable to other defensible
   approaches?

What is **not** in the source:

- A challenger model is not required. SR 11-7 lists it as
  an example *within* element 4 (benchmarking). Treating
  it as a universal requirement is practitioner folklore.
- A specific frequency of re-validation is not prescribed.
  Risk tier and triggering events drive it; the periodic
  cadence is "typically annual for material models" but
  the source is deliberately not more specific.
- Validation is not the same as testing. Validation
  evaluates the model's *fitness for purpose*. A model
  that passes every unit test can still be unfit for
  purpose if the problem framing is wrong.
- A specific set of statistical tests is not prescribed.
  Firms choose techniques "appropriate to" the model.

The validation elements are the *required outputs*; the
techniques are a firm choice. This is the room to design
that LLM validation needs.

## A taxonomy of validation patterns

Nine validation patterns, with what each pattern tells you
and where it fits (or does not fit) in ML. Most ML
validations use several in combination.

| Pattern | What it evaluates | ML applicability |
|---|---|---|
| **Challenger model** | Build an alternative model independently; compare disagreement rates and investigate | Good for tabular ML; moderate for image / speech models; poor for LLMs on free-form tasks |
| **Benchmarking against published baselines** | Compare performance against academic or industry benchmarks (SuperGLUE, HELM, MMLU, task-specific holdouts) | Good when the benchmark genuinely reflects use; risky when benchmark fits poorly or has been part of training data |
| **Counterfactual evaluation** | Probe the model with synthetic inputs that vary one factor at a time; observe output response | Good for explainability and sensitivity validation; partial for general robustness |
| **Stress / adversarial testing** | Subject the model to deliberately hostile or edge-case inputs | Essential for LLMs (prompt injection, jailbreaks); good for any production model (distribution-shift stress) |
| **Subgroup validation** | Evaluate performance on stratified populations (protected classes, geographic regions, product segments) | Required for fairness; often missing from initial ML validation and inserted late |
| **Out-of-distribution (OOD) testing** | Test on inputs deliberately outside the training distribution; verify refusal or degraded-but-safe behaviour | Important for production drift detection; essential for safety-critical systems |
| **Red-team evaluation** | Adversarial probing by humans trying to make the model fail | Increasingly required for LLM-driven systems; the only approach that catches social-engineering-style failures |
| **Human evaluation by domain experts** | Domain experts grade outputs against a rubric with defined inter-rater reliability | Often the only valid approach for LLM outputs with no automatic ground truth |
| **Process validation** | Validate the *development process* rather than just the outputs (data lineage, review gates, evaluation harness design) | Important when artifact-based validation is impossible or incomplete |

A single-pattern validation is rarely adequate for an ML
system of any consequence. The right question is not
"which pattern?" but "which combination?". The
combination should cover the four §IV elements and the
risks the system carries.

### A worked combination

A Tier 1 ML credit-decisioning model (the kind Exercise 02
targets):

- **Challenger model** satisfies element 4 (benchmarking)
  for the quantitative-estimate task. A credit decisioning
  context has a defensible alternative model class
  (logistic regression, scorecard) that produces a
  comparable output. Investigate disagreement rates on
  held-out data.
- **Subgroup validation** addresses the fair-lending
  obligation (ECOA / Reg B). Required regardless of other
  patterns; failure here is enforcement risk.
- **Counterfactual evaluation** validates the model's
  response to the specific features the decision depends
  on. If raising reported income by $10k changes the
  decision in a way that violates the policy intent, that
  is a model problem.
- **OOD / stress testing** validates behaviour on
  distribution-shift scenarios (an economic downturn
  class not represented in training data). Combined with
  the challenger disagreement rate, this is the
  robustness check.

Four patterns together cover elements 1 (conceptual
soundness, via the challenger's existence as a sanity
check and counterfactual probing of causal structure),
3 (outcomes analysis, implicit in the holdout
disagreement), 4 (benchmarking). Element 2 (ongoing
monitoring) is a separate ongoing discipline covered in
Chapter 4.

### What this looks like for an LLM

A Tier 1 LLM customer-facing assistant has no clean
challenger. The combination shifts:

- **Human evaluation by domain experts** replaces
  challenger for the free-form output axis. A graded
  rubric scored by trained raters, with inter-rater
  reliability tracked (Cohen's kappa or Krippendorff's
  alpha, pre-registered acceptance threshold).
- **Red-team evaluation** is where prompt-injection,
  jailbreak, and social-engineering failures surface.
  Treat as a scheduled discipline, not a one-off.
- **Subgroup validation on human-graded outputs** — do
  minority-dialect speakers get the same quality of
  response as majority-dialect speakers?
- **Counterfactual evaluation on structured probes** —
  change the user's apparent demographic in otherwise
  identical queries; look for differential refusal rates
  or differential helpfulness.
- **Benchmark against vendor-provided evaluations as
  evidence** (not substitute). The vendor's evals go into
  the file as supporting evidence; the firm's own
  evaluation is still required.

Five patterns together give defensible coverage. A
validation plan that proposed only vendor evaluation
would not meet the §IV bar.

## What independence actually means for ML

SR 11-7 requires validation performed by personnel
*independent of the model owner*. For classical banking
models, independence has a well-rehearsed structural
answer: a separate function, under a separate reporting
line, with no shared performance accountability. For ML
the question is sharper because teams are smaller and
the "model owner" boundary is less clean.

Three principles:

### The model owner cannot validate their own model

This rules out the common pattern of "the model team
validates the model and MRM reviews the validation."
Review of someone else's validation is not independent
validation. MRM must *do*, or *commission*, the
validation itself. Reviewing is not doing.

The practical consequence: in a small ML team, the
"independent validator" may be a different person in the
same reporting line. That is acceptable only if the
following three conditions all hold:

- The validator is not accountable for the model's
  success in production.
- The validator has no shared OKR / performance review
  dimension with the model owner.
- The validator has structural authority to withhold
  deployment approval.

If any of the three fails, the independence is
insufficient on examination.

### Independence does not require a different organisation

A separate team within the same engineering function can
be sufficient *if* real independence exists on the three
conditions above. For small firms where a separate MRM
function is not viable, this is the operational pattern.
For larger firms, the structural answer is simpler: MRM
reports up a different line (typically to the CRO), and
the independence is both structural and operational.

### Vendor validation does not substitute for firm validation

A foundation-model vendor's evaluation results are
useful *evidence* — they go in the validation file. They
are not *validation*. The firm's validation evaluates
the model's fitness for *the firm's intended use*, which
the vendor cannot know. The vendor's evaluation is
necessarily generic; the firm's is specific.

The clearest tell: a validation document that cites
vendor evaluations as its primary technique and performs
no firm-specific evaluation is not a validation.

## The independence test

The practical test, in a single question:

> *If the model fails materially in production, can the
> validation team be reasonably accused of bias toward
> the model owner — shared incentives, shared career
> stake, shared supervisor — in a way that would survive
> an after-action review?*

If yes, the independence is insufficient *now*, before
the failure, and should be remedied. If no, the
independence is defensible.

This test is what an examiner is applying implicitly
when they ask "who validated this model?". The question
is not organizational; it is incentive-structural.

## Re-validation cadence

SR 11-7 requires re-validation on:

- Material model change.
- Material change in intended use.
- Material change in the operating environment.
- Periodic basis (typically annual for material models,
  with specific cadences driven by tier).

For ML models, several *material change* triggers warrant
particular care because they are easy to miss:

- **Training-data refresh.** Material if the refresh
  shifts the distribution materially. Most training
  refreshes meet this bar; the heuristic is "if the
  training data from before and after would produce
  materially different model behaviour, the refresh is
  material." Which it almost always is.
- **Foundation-model swap** (vendor-hosted). Material
  always. The vendor's claim that the new foundation
  model is "equivalent" is a vendor claim, not a
  validation. Chapter 4 and Exercise 04 both develop
  this.
- **Fine-tuning.** Material if it changes the generation
  surface. A fine-tune for domain adaptation is material.
  A fine-tune purely for formatting may not be — but the
  decision needs to be documented, not assumed.
- **Prompt template change** for LLM systems. Material
  if it changes the system's behavioural envelope. An
  LLM system where the prompt template can be changed
  without re-validation has effectively defeated the
  MRM framework. This is the most under-recognised
  trigger in LLM programs.
- **Guardrail or output-filter change.** The guardrail
  is part of the system, not external to it. Changing
  the guardrail changes the system behaviour and
  warrants validation of the delta.

The practical rule for LLM systems: anything that changes
the *behavioural envelope* of the system is a material
change. The behavioural envelope includes the model
weights, the prompt template, the guardrails, the output
filters, the retrieval index, and the context-assembly
logic.

## The re-validation plan artifact

A validation plan should name explicitly:

- The patterns in use (which of the nine above, or
  reasoned alternatives).
- The acceptance criteria per pattern (what passing looks
  like, in advance of running the evaluation).
- The independence arrangement (who performs each
  pattern; how the independence test above is met).
- The re-validation triggers (which material changes
  reset the clock) and the periodic cadence.
- The documentation deliverable (what artifacts the
  validation produces for the file).

Exercise 02 produces exactly this artifact for a Tier 1
credit model.

## Common validation failures

Four patterns of validation that look right and are not:

- **The vendor-evaluation-only validation.** The
  validation document cites the vendor's benchmark
  numbers, declares them acceptable, and performs no
  firm-specific evaluation. Fails the "fitness for
  firm's intended use" standard.
- **The one-shot pre-deployment validation with no
  re-validation plan.** Element 2 (ongoing monitoring)
  of §IV is a continuous obligation. A validation that
  ends at deployment is half the discipline.
- **The challenger-model-only validation on an LLM.**
  The challenger — often a smaller or earlier LLM — gives
  disagreement rates that look like validation signal but
  do not test the right thing. The disagreement rate
  measures *difference*, not *correctness*.
- **The validation performed by the model team "with MRM
  review."** Addressed above. If MRM reviews rather than
  does, the firm has review, not validation.

## Summary

- SR 11-7 §IV identifies four elements of validation —
  conceptual soundness, ongoing monitoring, outcomes
  analysis, benchmarking. The challenger model is one
  example within benchmarking, not a universal
  requirement.
- Nine validation patterns cover ML; most ML validations
  use several in combination. For LLMs, human evaluation,
  red-team evaluation, and counterfactual probing often
  replace challenger as the core.
- Independence has a practical test: can the validation
  team be reasonably accused of bias toward the model
  owner after a failure? If yes, insufficient.
- Vendor evaluations are evidence, not validation. The
  firm's validation evaluates fitness for the firm's
  intended use.
- Material-change triggers for ML include training-data
  refresh, foundation-model swap, fine-tuning, prompt
  template change, and guardrail change. The behavioural
  envelope is the thing being tracked.
- A validation that ends at deployment is half the
  discipline; ongoing monitoring per element 2 is
  continuous.
