# Chapter 2 — Tiering ML Models Without Forcing ML into Financial-Model Assumptions

## Why this chapter exists

SR 11-7 does not mandate a specific tiering system. It
requires that the firm's MRM framework incorporate tiering
*commensurate with model risk* and leaves the details to
the firm. Tiering is the spine of an MRM program because
it is the single lever that determines how much
validation, governance, and monitoring effort each model
gets.

For classical financial models — econometric time series,
credit scorecards, actuarial reserving — the tiering
inputs are well-known: materiality of the decision,
regulatory exposure, pricing impact. For ML models,
particularly LLMs and large foundation models in product
roles, those inputs still apply but are not sufficient.
This chapter builds a tiering discipline that works
without forcing ML into the shape of a financial model.

Exercise 01 forces tiering against an explicit scheme on
five concrete ML models. Everything in this chapter is
written so that Exercise 01 is executable from it.

## What a tier means

A model's tier is shorthand for *the level of MRM
investment the model warrants*. A higher-tier model gets:

- **More rigorous independent validation before
  deployment.** For Tier 1 that is a full validation
  against each of SR 11-7 §IV's four elements; for lower
  tiers, a proportionate subset.
- **More frequent ongoing monitoring.** Daily or weekly
  performance tracking with alerting, versus monthly or
  quarterly reporting.
- **More senior governance oversight.** A model risk
  committee reviewing material decisions, versus
  model-owner self-approval within an envelope.
- **More detailed documentation.** Full technical file
  with reproducibility artifacts, versus a shorter
  structured record.
- **More onerous change-control.** Material changes
  require re-validation and senior approval; lower-tier
  changes may be approved by the model owner within a
  pre-authorised envelope.

A lower-tier model gets correspondingly less. The point
of tiering is *not* to be lenient on low-risk models; it
is to allocate MRM capacity in proportion to risk, so that
the high-risk models get the attention they warrant.

A tiering scheme is **defensible** if it:

1. **Reflects real differences in model risk.** A Tier 1
   model should carry materially higher risk than a Tier 3
   model on the dimensions the scheme measures.
2. **Applies consistently across the portfolio.** Like
   models get like tiers. If Model A is Tier 1 because its
   output drives an externally-binding decision, Model B
   with the same property must also be Tier 1 absent a
   named substantive difference.
3. **Produces reproducible classifications.** A different
   analyst applying the same criteria to the same model
   should reach the same tier. Tiering that depends on
   who is doing it is not defensible under examination.

## A working three-tier scheme

The following three-tier scheme is a working starting
point that adapts to ML. A four-tier scheme — splitting
Critical into *Catastrophic* and *Critical* — is more
common in large banks and is a straightforward extension.

| Tier | Criteria (any one is sufficient) | MRM treatment |
|---|---|---|
| **Tier 1 — Critical** | (i) model output directly drives an externally-binding decision (credit extension, insurance claim adjudication, clinical treatment pathway); (ii) failure has material customer, regulatory, or reputational consequence; (iii) system falls under a high-risk designation (EU AI Act Annex III high-risk; FDA Class II/III SaMD; state-level consumer-protection designation) | Full independent validation pre-deployment covering all four §IV elements; quarterly MRM monitoring review; annual full re-validation; senior MRM committee approval for material changes; detailed technical file with reproducibility artifacts |
| **Tier 2 — Important** | (i) model output substantively informs a decision but a human in the loop has authority and demonstrably exercises it; (ii) failure has identifiable but bounded operational impact; (iii) EU AI Act limited-risk category for systems with affected parties | Independent validation pre-deployment with proportionate scope; semi-annual MRM monitoring; biennial full re-validation; MRM lead approval for material changes |
| **Tier 3 — Standard** | All other in-scope models | Targeted validation (proportionate to risk); annual MRM monitoring; trigger-based re-validation; documented model-owner approval for changes within a pre-authorised envelope |

Two features of this scheme worth naming explicitly:

- **Multiple criteria, any one sufficient.** A single
  trigger — binding decision, material consequence, or
  regulatory designation — moves the model up. A model
  does not have to meet all of them. This is deliberate:
  tiering is a floor, not an average.
- **Explicit room for regulatory-designation triggers.**
  Criterion (iii) at each tier is where sector-specific
  regimes plug in. A system that an outside regime
  (EU AI Act, FDA, state insurance) has already labelled
  high-risk should carry that label into the MRM tiering,
  not re-litigate it.

## ML-specific tiering considerations

Three considerations that classical-model tiering misses
for ML, each of which may push a model up a tier when
present:

### Data freshness as a tiering input

A model trained on monthly batch data and retrained
quarterly has different risk dynamics than a model
retrained weekly on streaming data. Higher retraining
cadence often warrants higher tier, even if intended use
is similar, for two reasons:

- **Drift exposure.** A weekly-retrained model can shift
  behaviour meaningfully between validation cycles. The
  validation window must shrink accordingly or the
  monitoring must detect the drift in time.
- **Change discipline.** A retrain is a material model
  change under SR 11-7 §IV. A model that retrains weekly
  is executing material changes weekly. The tier must
  support that cadence operationally.

The practical rule: if the retrain cadence is faster than
your re-validation cadence allows, either the retrain
needs to slow down or the tier (and validation cadence)
needs to go up.

### Model size and inscrutability

A 100-billion-parameter foundation model embedded in a
product is *materially less explainable* than a 100-feature
gradient-boosted model with similar use. Some firms add
inscrutability as a tiering input directly. The reasoning:

- **Validation surface.** A model you cannot inspect
  internally is harder to validate on conceptual soundness
  (§IV element 1 in the next chapter). You compensate with
  more behavioural testing, more adversarial testing, and
  more human evaluation — all of which cost more MRM
  capacity.
- **Explainability obligations.** Where regulation
  (ECOA/Reg B adverse action, EU AI Act Article 13) or
  internal policy requires explanations, an inscrutable
  model forces investment in post-hoc explanation methods
  with their own validation requirements.

Inscrutability does not automatically mean Tier 1 — a
tiny inscrutable model with no decision influence is
still low tier. It is an *input*, pushing in the direction
of higher tier when combined with real decision influence.

### Vendor and foundation-model provenance

A model whose internal details the firm does not have
access to — a closed-weights hosted LLM, a vendor
proprietary scorecard — carries higher validation and
monitoring challenge than an on-prem model with full
access to weights, training data, and training code.
Some firms tier vendor models one step higher than
equivalent in-house models to account for the validation
gap.

The nuance:

- The firm cannot inspect the model's training data for
  bias or contamination.
- The firm cannot reproduce the model from documentation.
- The vendor may change the model behind a stable API
  (the foundation-model-swap problem addressed in
  Chapter 4).
- The vendor's validation evidence is *input* to the
  firm's validation, not a substitute for it (per
  Chapter 3).

The practical rule: if the system's answer to "could
another competent professional reproduce this from the
documentation we hold?" is *no, because the vendor won't
give it to us*, that counts as an inscrutability input
and often warrants an upward tier adjustment.

## A worked example

Consider two models that at first glance both look like
"Tier 2 — Important":

- **Model P.** An in-house gradient-boosted model that
  estimates a propensity-to-respond score used to
  prioritise marketing contact. Humans decide which
  prospects to call. Retrained monthly. Internally
  built, full documentation.
- **Model Q.** A vendor-hosted LLM agent that assists
  customer-service representatives by drafting responses
  to common inquiries. The representative edits and sends.
  Vendor swaps foundation model with 30-day notice.

Apply the tiering scheme:

- **Model P.** Criterion (i) at Tier 2 fits (humans
  authority, demonstrably exercised). Monthly retrain is
  within envelope. In-house provenance, full
  documentation. Tier 2 is defensible.
- **Model Q.** Criterion (i) at Tier 2 fits on the face
  of it — representative has authority. But: the vendor
  can swap the underlying model, which is a material
  change outside the firm's control (the inscrutability
  and provenance inputs both apply). The practical risk
  dynamics look more like Tier 1 behaviour (frequent
  material-change events) at a Tier 2 use. Firms
  typically resolve this by either (a) tiering Model Q up
  to Tier 1 to match the change-control cadence or
  (b) negotiating contractual notice + validation windows
  with the vendor so Model Q's effective change rate is
  bounded.

The example is a reminder that the tier is the output of
*applying the scheme* to the specific model, not a
guess at category. Exercise 01 forces this level of
discipline across five models.

## Tiering anti-patterns

Patterns that look reasonable from the outside and fail
on examination:

- **Tiering by business sponsor seniority.** A model
  sponsored by an SVP is not therefore Tier 1. Tier
  reflects *the model's risk*, not political weight.
  Programs where the SVP's models all end up Tier 1 and
  the junior PM's models all end up Tier 3 have inverted
  the discipline.
- **Tiering everything as Tier 1 "to be safe".** Looks
  conservative, is not. Forces MRM into impossible
  workload; the program degrades silently as resourcing
  fails to keep pace; validations get rubber-stamped;
  monitoring reviews happen on paper only. The result is
  a program with a Tier 1 label and a Tier 3 reality,
  which is worse than an honest Tier 3.
- **Tiering everything Tier 3 "during pilot".** "Pilot"
  becomes a permanent tier-avoidance category. SR 11-7
  does not exempt pilots from scope when they affect
  customers; the examiner will notice. A pilot that could
  affect customers is in scope; what varies is the
  validation depth, not the tier.
- **Re-tiering downward without documented rationale.**
  Common during model updates (the model has been in
  production for a year without incident; let's drop it
  to Tier 3). The examiner will read this as motivated
  reasoning unless the rationale is specific. Document
  what changed in the model's risk profile, not what has
  not happened.
- **Tiering the model but not the system around it.**
  A Tier 1 model embedded in a Tier 3 pipeline is a Tier 3
  system. Treat the system end-to-end. If the output of
  a validated model gets passed through an unvalidated
  post-processor, the tier of the composite is driven by
  the weakest link.

## Where tiering sits in the program

Tiering is the first operational decision for every model
in the inventory. It drives:

- The validation plan (Chapter 3).
- The lifecycle stops the model goes through (Chapter 4).
- The inventory record (Chapter 5) — tier is a required
  field.
- The CAO × MRM boundary (Chapter 6) — tier anchors
  "whose approval is needed for what".
- The reporting rhythm (mod-103 Chapter 7 + mod-111) —
  Tier 1 models typically appear in board-level reports
  individually; lower tiers roll up in aggregate.

A program that tiers once at onboarding and never
re-tiers has misunderstood the discipline. Tiers should
be reviewed on any material change in intended use, any
change in regulatory designation of the use case, or on
a periodic cadence (annual is common). An unchanged
tier that has been reviewed and reaffirmed on cadence is
different from an unchanged tier that has been forgotten.

## Summary

- Tiering is the spine of an MRM program; it allocates
  MRM capacity in proportion to model risk.
- SR 11-7 requires tiering but does not prescribe the
  scheme. A defensible scheme reflects real differences
  in risk, applies consistently, and produces reproducible
  classifications.
- The working three-tier scheme — Critical / Important /
  Standard — uses three criteria (decision influence,
  consequence of failure, regulatory designation) with
  any one sufficient to escalate.
- ML-specific tiering inputs — data freshness,
  inscrutability, vendor provenance — push a model up a
  tier when present with real decision influence.
- The common anti-patterns — tiering by sponsor
  seniority, over-tiering "to be safe", pilot
  tier-avoidance, undocumented downward re-tiering,
  tiering the model but not the system around it — all
  read as failures on examination.
- Tiering is reviewed, not set once. An unchanged tier
  that has been reaffirmed is different from one that has
  been forgotten.
