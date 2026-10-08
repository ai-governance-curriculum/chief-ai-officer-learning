# Chapter 4 — The Model Lifecycle with ML-Specific Stops

## Why this chapter exists

SR 11-7 implies a model lifecycle. §III moves from
development through implementation to use; §IV moves
through pre-deployment validation into ongoing
monitoring; §V imposes governance over the whole arc.
Working MRM programs make the lifecycle *explicit* — a
named set of stops with named owners, named artifacts,
and named gates between stops.

For classical models the stops map cleanly. For ML
systems — especially LLM-based ones — several stops in
the lifecycle deserve more emphasis than they get in
classical programs. Two in particular are regularly
skipped and produce the governance gaps that later
become findings.

This chapter names the stops, calls out the ML-specific
considerations at each, and surfaces the two stops that
programs most often skip. It is the operational scaffold
on which Chapter 5 (inventory) and the ongoing-monitoring
half of Chapter 3 both rest.

## The nine lifecycle stops

| # | Stop | What happens | ML-specific consideration |
|---|---|---|---|
| 1 | **Concept / sponsor approval** | Business case; intended use; expected risk tier; stakeholders identified | LLM use-cases benefit from rigorous intended-use definition; the prompt determines the system as much as the model does |
| 2 | **Data acquisition** | Source identification; provenance documentation; rights review; consent review | Training-data IP and consent issues; EU AI Act technical-file requirements per mod-102 begin here |
| 3 | **Development** | Model building; internal testing; iteration | Computationally expensive; iterations less reviewable than for classical models; experiment tracking is the only way to make this inspectable |
| 4 | **Independent validation** | Per Chapter 3 — multiple patterns combined; §IV elements covered | Cannot rely on a single technique; cannot rely on vendor evaluation alone |
| 5 | **Implementation** | Deployment into the operating environment; the system around the model is wired up | **Often skipped.** LLM systems: prompt template versioning, model-version pinning, output filtering, retrieval index wiring, guardrail configuration |
| 6 | **Use** | Operating with first-line controls | Workflow design matters as much as model quality: asymmetric escalation, human-in-loop structure, override discipline, logging for later outcomes analysis |
| 7 | **Ongoing monitoring** | Performance, drift, fairness, security, misuse | Leading + lagging indicators per mod-103 §4; alert thresholds pre-registered |
| 8 | **Re-validation** | Periodic + trigger-based (per Chapter 3) | More frequent than for classical models due to retrain cadence and vendor-swap exposure |
| 9 | **Retirement** | Decommissioning | **Often skipped.** Models silently outlive their utility; the inventory still shows them active |

Each stop has an entry condition (what must be true to
begin it), an exit condition (what must be true to leave
it for the next stop), and a named artifact (what the
stop produces). A lifecycle without named exit conditions
is a wishlist.

## Stop 1 — Concept / sponsor approval

The entry condition is a business case that identifies the
decision the model will influence. The exit condition is
a signed one-pager that commits the sponsor to the
intended-use scope, the expected tier, and the acceptance
criteria. The named artifact is the intended-use statement
that will later be the yardstick for misuse detection.

For LLM systems, the intended-use statement must specify
*what prompts are on-label*. The common failure is to
define intended use at the business level ("customer
service agent") and leave the behavioural envelope
unspecified. An intended-use statement that cannot
support a yes/no answer to "is this specific prompt
on-label?" is incomplete.

## Stop 2 — Data acquisition

The entry condition is the signed intended-use statement.
The exit condition is a documented data lineage from
origin to training set, with rights/consent review
complete. The named artifact is the data provenance
record.

For ML models this is where EU AI Act Article 10 (data
governance) obligations start accruing (per mod-102
Chapter 3). For vendor-hosted LLMs the firm cannot
produce this artifact for the foundation-model training
data — but it can and should produce it for any
fine-tuning data, RAG corpus, and evaluation set the
firm controls.

## Stop 3 — Development

The entry condition is approved data. The exit condition
is a model artifact plus a development record — training
code, training configuration, held-out evaluation
results, experiment log.

For ML, the development record is where reproducibility
either exists or does not. SR 11-7's "another competent
professional could reproduce" standard applies here. The
practical form:

- Training code under version control, with the commit
  hash recorded against the model artifact.
- Training data lineage documented (Stop 2 output
  referenced).
- Random seeds captured (and acknowledged where
  non-determinism is intrinsic, as with distributed GPU
  training).
- Evaluation harness code and evaluation data captured
  alongside the model.

Programs without this discipline cannot pass Chapter 3's
"reproducibility by another competent professional"
test and lose the entire structural argument SR 11-7 is
making.

## Stop 4 — Independent validation

Covered in Chapter 3. The entry condition is a complete
development record. The exit condition is a validation
report that covers the §IV elements and names any
material limitations. The named artifact is the
validation file.

## Stop 5 — Implementation review

**The first of the two most-often-skipped stops.**

Classical models go from validation to use in roughly one
step — the deployment is the implementation. ML systems,
particularly LLM-based ones, have a deployment
infrastructure that is **as load-bearing as the model
itself**:

- The serving stack (which model version is actually
  deployed, what inference parameters are set).
- The prompt template (for LLM systems — a change here
  changes the system behaviour).
- The retrieval index (for RAG systems — the corpus and
  the chunking / embedding strategy both affect outputs).
- The output filter / guardrail (what post-processing
  constrains the output).
- The surrounding application logic (what gets passed to
  the model, what gets done with the output).

Implementation review verifies that *the system in
production* is the system that was validated. Without
this stop, the validation evaluates one artifact and
production runs a different artifact. The gap is often
discovered only during an incident, when the system that
is actually running turns out to differ from the system
on paper.

A working implementation review produces:

- A deployment manifest listing exact model version,
  prompt template version, retrieval index version,
  guardrail configuration, and application-logic version.
- A diff against the validated configuration if any
  difference exists, with the delta either justified or
  escalated.
- A sign-off from both the model owner and the MRM
  validator that the deployed system matches the
  validated system.

The exit condition is a signed deployment manifest. The
named artifact is the manifest itself, retained in the
inventory record (Chapter 5).

## Stop 6 — Use

The entry condition is a signed deployment manifest. The
exit condition is... there is no exit condition in a
cycle-ending sense; Stop 6 runs continuously until
retirement. What matters here is the *first-line control
design*:

- **Workflow asymmetry.** Human-in-loop controls work
  only if the human actually reads and sometimes
  overrides. A workflow where overriding the model
  requires five clicks and accepting it requires one has
  effectively eliminated the human-in-loop.
- **Override logging.** Overrides are a signal; a system
  with no override logging cannot measure its own misuse.
- **Prompt / usage logging** for LLM systems. The
  production prompts are the production data; losing
  them is losing the model's actual use record.

The design of Stop 6 directly determines whether Stop 7
(ongoing monitoring) has data to work with. A production
system that logs nothing is a monitoring void.

## Stop 7 — Ongoing monitoring

Per mod-103 §4 and SR 11-7 §IV element 2. The entry
condition is a monitoring plan (what metrics, what
thresholds, what alerting). The ongoing exit is per
monitoring cycle — a monitoring review that confirms
performance is within envelope or escalates.

For ML the leading indicators matter: data drift,
distribution shift, override rate, user-reported errors,
subgroup performance gaps. Lagging indicators (overall
accuracy against ground truth) remain the final signal
but arrive too late for timely intervention. mod-103 §4
develops the leading-vs-lagging discipline.

## Stop 8 — Re-validation

Per Chapter 3's cadence and triggers. The entry condition
is either a material change trigger firing or a periodic
cadence tick. The exit condition is an updated
validation file with the delta documented.

Re-validation is not a repeat of initial validation; it
is validation of *the change* against the baseline.
Programs that treat re-validation as a repeat burn
capacity on things the first validation already
established; programs that treat it as too light miss
drift and change effects.

## Stop 9 — Retirement

**The second of the two most-often-skipped stops.**

Most ML programs accumulate models. Models are
"deprecated" in name but continue to serve traffic, or
live in a staging environment that is referenced by
production code, or persist in a vendor contract that
has not been renegotiated, or sit on a shared endpoint
that nobody has removed. The inventory still shows them.
The regulator reads the inventory.

A working retirement stop includes:

- **A named retirement gate.** A sponsor decision to
  retire, with the reason recorded.
- **Deployment-removal verification.** Not "we marked it
  deprecated"; a check that no production traffic
  reaches it.
- **Inventory delete.** The record moves to a retired
  state, retained for the audit window, but no longer
  listed among active models.
- **Vendor-contract review.** For vendor-hosted models,
  the retirement includes contract disposition — are we
  still paying for it; are we still receiving model
  updates; is there a replacement model inherited by
  default?

Programs that routinely skip Stop 9 end up with
inventories full of ghost models — things listed as
active that have not been meaningfully used, validated,
or monitored in years. The inventory stops being usable
as the firm's actual map.

## The lifecycle's role in audit

A well-defined lifecycle makes internal audit (the third
line) cheaper and more informative. Internal audit can
verify the lifecycle was followed for any specific
model — were the entry / exit conditions met at each
stop; were the artifacts produced; are the sign-offs
present — rather than re-validating from scratch.

A program where lifecycle stops are not documented gets
a re-perform-from-scratch audit, which is expensive and
informative in unwanted ways. Audits that have to
reconstruct what happened tend to find more than audits
that merely verify what is documented.

Internal audit's own expectations (per IIA guidance and
each firm's audit charter) typically require evidence
that:

- Every active model has been through all nine stops.
- The gates between stops were real (not retro-signed).
- The retirement path works (sample a few retired
  models; confirm they are no longer serving traffic).

## Composing the lifecycle with the tier scheme

The nine stops are universal; the *depth* at each stop
scales with tier (per Chapter 2):

- Tier 1: full stop with full artifact set at every stop;
  senior MRM committee gate at Stops 1, 4, 5, 9.
- Tier 2: full stop at Stops 1, 4, 5, 7, 9; proportionate
  depth at 2, 3, 6, 8; MRM lead gate at 4, 5.
- Tier 3: lifecycle present but proportionate; model
  owner may self-approve within envelope at Stops 3, 6,
  8; MRM gate at Stops 1, 4, 9.

The tier does not change which stops exist; it changes
how much work each stop warrants.

## Summary

- SR 11-7 implies a lifecycle; working programs make it
  explicit — nine stops with entry / exit conditions and
  named artifacts.
- The two stops most often skipped are implementation
  review (Stop 5) and retirement (Stop 9). Implementation
  review ensures the deployed system matches the
  validated system; retirement ensures the inventory
  stays truthful.
- For LLM systems, Stop 5 covers the full behavioural
  envelope — model version, prompt template, retrieval
  index, guardrail, application logic — because any of
  them can change the system behaviour independent of the
  model weights.
- Stop 6 (use) is where first-line controls are designed;
  Stop 7 (monitoring) can only measure what Stop 6
  logged.
- A well-defined lifecycle makes audit cheaper and more
  informative. An undocumented lifecycle gets a
  reconstruct-from-scratch audit.
- The nine stops are universal; depth at each stop scales
  with tier.
