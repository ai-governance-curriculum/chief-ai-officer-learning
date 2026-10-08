# Chapter 3 — Bias and Fairness Beyond Demographic Parity

## Why this chapter exists

Bias and fairness is the most technically rich area of
AI ethics. It is also the area where ethics theater is
most common — programs claim bias mitigation by
computing one metric, ignoring the metric's known
limitations, and declaring victory. A model that is
"fair" by demographic parity is often simultaneously
*unfair* by predictive parity, by equalized odds, or by
individual fairness. These are not reconciliable through
better engineering. They are mathematically
irreconcilable in any context with unequal base rates,
which is almost every real decisioning context.

The CAO's job here is to make the trade-off visible,
make the metric choice specific, and defend the choice
on both clinical/business grounds *and* ethical grounds.
A program that computes a metric without being able to
state what that metric would miss has not done the work.
This chapter builds the vocabulary and the discipline.

## 3.1 The basic metrics

Several bias metrics are in regular use. None is correct
in isolation; all carry assumptions about what fairness
*means*.

| Metric | What it measures | Also known as |
|---|---|---|
| Demographic parity | Equal positive-prediction rate across groups: P(ŷ=1 \| A=a) equal for all a | Statistical parity, independence |
| Equal opportunity | Equal true-positive rate across groups within the qualified population: P(ŷ=1 \| y=1, A=a) equal for all a | Equality of opportunity |
| Equalized odds | Equal true-positive AND false-positive rates across groups | Separation |
| Predictive parity | Equal positive predictive value across groups: P(y=1 \| ŷ=1, A=a) equal for all a | Precision parity, sufficiency, calibration-by-group |
| Treatment equality | Equal ratio of false-negative to false-positive across groups | Treatment equality |
| Counterfactual fairness | Prediction unchanged in a counterfactual world where only the protected attribute differs | Causal fairness |
| Individual fairness | Similar individuals (per a defined similarity metric) get similar predictions | Lipschitz fairness |

Each metric is grounded in a different intuition about
what fairness *means*:

- **Demographic parity** says fairness is equal
  outcomes across groups, independent of underlying
  rates.
- **Equal opportunity** says fairness is equal access
  to the positive outcome *among those who deserve
  it*.
- **Equalized odds** says fairness is parity of error
  *in both directions*.
- **Predictive parity** says fairness is that a
  positive prediction means the same thing across
  groups.
- **Treatment equality** says fairness is that the
  *balance* of errors is proportionate across groups.
- **Counterfactual fairness** says fairness is that
  the protected attribute does not causally drive the
  prediction.
- **Individual fairness** says fairness is about
  individuals, not groups — the group framing may itself
  be the problem.

Each has been argued for in the academic literature.
Each is defensible in some context. None can be the
answer alone.

### 3.1.1 A concrete example

Take a loan-approval model operating in a market with
unequal base rates of default across groups (base rate
of default = 10% in Group A, 15% in Group B — the model
cannot change the base rates; the model only predicts
them).

- A model enforcing **demographic parity** would
  approve the same percentage of applicants in Group B
  as in Group A, which — given the higher base rate —
  means approving some applicants with worse risk
  profiles than Group A. The model's precision on
  Group B drops.
- A model enforcing **predictive parity** (equal
  precision) accepts that Group B's approval rate will
  be lower than Group A's — the model is "fair" in the
  sense that an approved applicant has the same
  default probability regardless of group, but the
  group-level approval rates differ.
- A model enforcing **equalized odds** matches both the
  true-positive and false-positive rates across groups,
  but the resulting precisions differ.

All three models are "fair" by their own metric. All
three disagree on who gets approved. Pick one and the
other two will tell you the model is biased.

## 3.2 The impossibility result

The most important result in algorithmic fairness is
*Chouldechova (2017)* and the independent but
compatible *Kleinberg, Mullainathan, Raghavan (2016)*:

> In any context where group base-rates of the target
> outcome differ, you cannot simultaneously satisfy:
>
> 1. Predictive parity (equal precision across groups);
> 2. Equal false-positive rates across groups;
> 3. Equal false-negative rates across groups.
>
> You can have any two; you cannot have all three.

This is not a flaw in current algorithms. It is
mathematically unavoidable — a consequence of the
arithmetic of confusion matrices when base rates differ.
Chouldechova's paper is short, accessible, and reads
cleanly for a reader with undergraduate statistics; it
is required reading at the CAO level.

The practical implication: **every fairness choice is a
trade-off**. There is no metric set that satisfies all
ethically-resonant fairness definitions simultaneously
in any context with unequal base rates — and unequal
base rates are the norm in most real decisioning
contexts.

A program that claims to have eliminated bias on all
metrics is either (a) operating in a base-rate-equal
context (rare), (b) using a metric set that hides the
trade-off, or (c) wrong.

### 3.2.1 The ProPublica / COMPAS debate as a worked case

The 2016 ProPublica investigation of Northpointe's
COMPAS recidivism model is the canonical example. The
investigators found that COMPAS had *higher false-
positive rates for Black defendants* and *lower false-
positive rates for White defendants*. Northpointe
responded that COMPAS had *equal predictive parity* —
the probability of recidivism given a high score was
roughly the same across groups.

Both claims were correct. The disagreement was not
empirical; it was about which fairness definition
applied. Base rates of re-arrest differed across the
groups in the data, which made the two fairness
definitions mathematically irreconcilable. Chouldechova's
2017 paper formalised this exact example into the
impossibility result.

The CAO lesson: when stakeholders disagree about whether
a model is biased, the disagreement may be a
mathematical consequence of the group's data, not a
dispute about facts. Named metric choice makes the
disagreement visible instead of latent.

## 3.3 Choosing a metric set

The honest approach: pick a metric set that reflects the
*specific* fairness commitment you are making, and own
the trade-off.

A useful pattern: choose **2–3 metrics** that together
characterize the bias surface, with explicit awareness
that no choice satisfies all definitions.

### 3.3.1 Defensible examples by context

- **Credit decisioning** — predictive parity (so the
  precision of "approve" predictions is similar across
  groups — this addresses CFPB's adverse-action and
  disparate-impact concerns) + equal opportunity for
  the qualified population (so qualified applicants
  from minority groups get approved at the same rate
  as qualified majority applicants). The known
  trade-off: group-level approval rates may still
  differ.
- **Clinical triage / early-warning systems** —
  equalized odds (so both over-triage and under-
  triage rates are matched across groups — clinical
  safety requires parity in *both* error directions).
  The known trade-off: precision will differ by group,
  which is accepted because the primary clinical
  concern is parity of missed cases.
- **Content moderation** — equal-opportunity-style
  metric for protected-speech contexts (so protected
  speech from each group is removed at the same low
  rate when it is protected) + treatment-equality for
  harmful-content categories. The known trade-off:
  intra-category precision drifts.
- **Hiring and promotion** — equal opportunity +
  calibration-by-group. The known trade-off: group-
  level selection rates may differ, which may trigger
  disparate-impact scrutiny under US employment law
  (requires the four-fifths rule analysis as a
  separate compliance check).
- **Resource allocation / public services** —
  depending on the resource, often individual
  fairness as the primary frame, with group-fairness
  metrics as secondary audit tools.

### 3.3.2 The metric-set anatomy

A defensible bias-metric specification states, at
minimum:

1. **The protected populations** — named, with how
   each is identified (self-report, proxy, derived).
2. **The metrics** — 2–3, defined precisely for the
   system's positive class and relevant outcome.
3. **The thresholds** — numeric, with the reasoning.
   "Should not exceed 0.1 absolute difference" with
   the reasoning anchored.
4. **The response** — what the program does when a
   threshold is crossed. Investigate? Suspend
   deployment? Retrain? Document and continue? The
   response matters as much as the threshold.
5. **The trade-off acknowledgment** — which
   impossibility-result properties the metric set does
   *not* satisfy, with the ethical reasoning for the
   choice.

A specification missing any of the five is not a
specification. It is a wish.

### 3.3.3 Thresholds — a note on numbers

A common question: what threshold is "right"?

Honest answer: there is no universally correct
threshold. Several reference points inform the choice:

- The **four-fifths rule** (US EEOC guidance in
  employment contexts) — a selection rate for one
  group that is less than four-fifths of the rate for
  another group is considered evidence of adverse
  impact. This is a *legal threshold*, not an ethical
  one, and only applies to employment contexts.
- The **CO Reg 10-1-1 insurance testing standard** —
  specifies tests for unfairly discriminatory
  outcomes, including quantitative tests the insurer
  must document.
- **NIST AI RMF Playbook** — recommends tracking
  disparity *trends* in addition to absolute levels, so
  the program notices when disparity is growing.

The CAO's role: pick a threshold defensible to a
regulator and an affected stakeholder, and *name* the
trade-off the threshold implies. A low threshold catches
more cases but creates more operational burden. A high
threshold is operationally easier but misses more harm.

## 3.4 Beyond metrics: process fairness

Fairness is not entirely captured by output metrics.
Process-fairness concerns:

- **Procedural fairness.** Was the affected party
  treated according to a consistent, principled
  process? Two applicants with identical files should
  get the same treatment; a system that routes
  applications through different models based on
  arbitrary factors is procedurally unfair even if
  metric-fair in aggregate.
- **Representational fairness.** Are the model's
  outputs perpetuating stereotypes in their
  representation of groups (e.g., generative outputs
  that consistently represent doctors as male, nurses
  as female)? Metric-based bias testing may not catch
  this because the "positive class" is not well-
  defined for generative outputs.
- **Distributive fairness.** Are the benefits of the
  system distributed in a way the organisation can
  defend as fair? A model may be metric-fair while
  producing an aggregate benefit allocation that
  disproportionately favors one group.
- **Participation fairness.** Were affected
  communities involved in defining what fairness
  *meant* for this context? A metric choice made
  without consultation of the affected community may
  be metric-fair while being participatorily unfair.

The mod-103 §2 taxonomy treats bias as one risk category
because the operational machinery is similar. The
operational machinery is *not* sufficient — the value
choices about which fairness conception to enforce sit
above the machinery. See *Selbst et al. (2019),
Fairness and Abstraction in Sociotechnical Systems* for
the standard argument that algorithmic fairness alone is
insufficient (Tier 1 reading).

## 3.5 Subgroup discovery

The hardest practical fairness problem: *you do not
know in advance which subgroups will exhibit disparate
impact*.

The classical pattern is *pre-specified protected
classes* (race, sex, age, religion, national origin,
disability status, veteran status, etc. — the exact
list depends on jurisdiction and sector). The classical
pattern is necessary but not sufficient for AI systems
because:

- Models can produce disparate impact along axes nobody
  thought to test — intersections of attributes, or
  attributes not usually tracked.
- Combinations of attributes can produce disparate
  impact even when each attribute alone does not. A
  model may show no disparity on race, no disparity on
  sex, but material disparity on race × sex × age
  intersections.
- Behavioral and linguistic patterns can create
  effectively-protected groups — users of a specific
  dialect, users of assistive technology, users with
  mobile-first access patterns.
- Models trained on one population may produce
  disparate impact on populations under-represented in
  training data (dataset shift as a bias driver).

### 3.5.1 Subgroup-discovery patterns

Several techniques in use. None is sufficient alone; a
mature program runs several and takes the union.

- **Slice-finding tools** (e.g., tools that search for
  subgroups where model performance deviates
  significantly from overall). Examples in the open-
  source literature: SliceFinder, Multiaccuracy,
  Divisi, as well as the slicing primitives in
  Fairlearn and AIF360. The techniques differ in
  objective function; running two and comparing is
  routine.
- **Clinical / population stratification** — for
  healthcare systems, stratifying by clinical sub-
  population (diagnosis, severity, comorbidity) rather
  than purely demographic attributes.
- **Behavioral stratification** — stratifying by usage
  pattern (first-time user, mobile vs. desktop,
  session length) to find performance disparities
  invisible to pure demographics.
- **Community-informed evaluation** — asking affected
  communities what performance disparities would
  matter to them, and testing for those specifically.
- **Red-team subgroup probing** — adversarial testing
  that constructs plausible subgroups and tests the
  model's performance on each.

Subgroup discovery is an *under-specified* discipline.
No single tool reliably finds all relevant subgroups.
The discipline is to run *several* methods, treat their
union as the analysis space, document the methods used
*and* the methods not used, and own the gap honestly.

### 3.5.2 The "unknown-subgroups" obligation

A deployed system continues to encounter subgroups the
development process did not anticipate. The operational
pattern:

- **Monitoring** that watches for performance
  disparities across axes the deployment configuration
  did not pre-specify.
- **Incident channels** that treat subgroup-disparity
  reports from affected parties, deployers, and
  internal observers as first-class findings (not
  "feature requests").
- **Periodic subgroup review** — some firms adopt an
  annual or semi-annual pass where the subgroup
  discovery techniques of §3.5.1 are re-run against
  current production data to find subgroups that
  emerged with usage.

A program with a pre-deployment bias validation and no
post-deployment subgroup-discovery discipline has done
half the work.

## 3.6 Operationalisation checklist

A CAO ethics function with working bias discipline can
produce, for any production AI system:

1. The named protected populations (per-system).
2. The chosen metric set (2–3 metrics, defined
   precisely for the system).
3. The named thresholds (numeric, with reasoning).
4. The named response when thresholds are crossed.
5. The explicit impossibility-result trade-off (which
   properties the metric set does not satisfy).
6. The subgroup-discovery methodology (which tools /
   techniques were run; what the union-set analysis
   showed).
7. The post-deployment monitoring plan.
8. The incident channel for subgroup-disparity
   reports.

Exercise 02 asks you to produce the first six for a
specific clinical system. mod-104 §3 covers the
validation-process discipline into which this plugs.

## Summary

- Multiple fairness metrics exist, each grounded in a
  different intuition. None is correct in isolation.
- Chouldechova (2017) and Kleinberg et al. (2016)
  prove that predictive parity, equal false-positive
  rates, and equal false-negative rates cannot all
  hold simultaneously when group base rates differ.
  You pick two; you lose the third.
- A defensible metric set is 2–3 metrics with specific
  thresholds, a named response, and an explicit
  acknowledgment of the impossibility-result trade-off.
- Process fairness (procedural, representational,
  distributive, participatory) matters alongside
  metric fairness. Metrics alone are not sufficient.
- Subgroup discovery is under-specified. Run several
  techniques, take the union, document the gap.
  Continue the discipline post-deployment.
- A production AI system should have a traceable
  bias-metric specification and a documented subgroup-
  discovery record — not just a passing bias score.
