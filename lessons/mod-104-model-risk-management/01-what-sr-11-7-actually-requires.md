# Chapter 1 — What SR 11-7 Actually Requires

## Why this chapter exists

SR 11-7 — the Federal Reserve and OCC's 2011 *Supervisory
Guidance on Model Risk Management* — is one of the
shortest, most influential, and most misunderstood
documents in the AI governance space. It is twenty-one
pages. Most of what people *say* it requires is downstream
interpretation that has calcified into folklore. The first
discipline of this module is reading what the document
actually says, in its own words, and separating the text
from the practitioner commentary on top of it.

The payoff is practical. An AI governance program that
quotes "SR 11-7 says ..." has to be able to defend the
quote. An examiner who has read the source will catch a
quote that attributes to SR 11-7 something the source
leaves to the firm. This chapter is the inoculation.

Read the source alongside this chapter if you have not
already — it is 21 pages. Citations below use the
section markers inside SR 11-7 itself (§III, §IV, §V).

## What SR 11-7 is actually for

SR 11-7's central premise appears in its opening section:

> *"The use of models invariably presents model risk,
> which is the potential for adverse consequences from
> decisions based on incorrect or misused model outputs
> and reports."*

Two things are doing work in that sentence. The guidance
identifies **two sources** of model risk:

1. **Fundamental error** — the model has a flaw that
   produces inaccurate outputs. This is what most people
   think of when they hear "model risk" and what most
   validation practice focuses on.
2. **Misuse** — the model is used outside its design
   intent, or its outputs are misinterpreted by
   decision-makers. The model may be fine; the use of
   the model is wrong.

The whole document is structured around managing *both*.
This is the single most under-recognised feature of SR
11-7 by AI governance programs. Programs that focus only
on fundamental error — better validation, better testing,
better evaluation harnesses — without addressing misuse —
better governance of *how* outputs are used, who may
override, what prompts are considered on-label — have
built half the discipline SR 11-7 is asking for.

The misuse framing is also what makes SR 11-7 translate
cleanly to LLMs. A chatbot that is accurate on-label but
is used off-label by a frontline employee to make a
decision the chatbot was never evaluated for is not a
fundamental-error problem; it is a misuse problem. SR 11-7
has had the vocabulary for this since 2011.

## The four pillars of an MRM framework

SR 11-7 §III specifies that a *firm-wide* MRM framework
must include:

1. **Robust model development, implementation, and use**
   (§III).
2. **Sound model validation processes** (§IV).
3. **Strong governance, policies, and controls** (§V).
4. **A firm-wide MRM framework integrating the above**
   (§VI).

The four pillars are not a checklist. They are *load-
bearing structures*. A framework missing any of them
collapses under regulator scrutiny. In particular, the
fourth pillar — firm-wide integration — is the one most
often skipped. A firm with validation and governance
functions that operate as independent silos *does not have
an MRM framework*; it has validation and governance
functions that overlap by accident.

The relationships between the pillars matter:

- Pillar 1 generates artifacts (development documentation,
  implementation evidence, use records). Pillar 2
  evaluates those artifacts. The two are both load-
  bearing; neither substitutes for the other.
- Pillar 3 sets the policies that constrain Pillars 1 and
  2 (what documentation is required, who may approve what
  changes, who sits on the model-risk committee).
- Pillar 4 wires the three together — a single inventory,
  a single policy stack, consistent tiering, a reporting
  rhythm that reaches senior management.

An AI program adopting SR 11-7 structure must stand up all
four. Standing up two or three is a common failure mode
and reads immediately as such to anyone familiar with the
guidance.

## What counts as a "model" under SR 11-7

The most over-debated topic in MRM. SR 11-7 defines a
model as:

> *"a quantitative method, system, or approach that
> applies statistical, economic, financial, or
> mathematical theories, techniques, and assumptions to
> process input data into quantitative estimates."*

Read carefully: *quantitative estimates*. The definition
is broad on inputs (any data) and specific on outputs
(estimates of some quantity). The implication for AI/ML:

- A neural network producing a credit score is **a model**.
  The score is a quantitative estimate.
- A gradient-boosted ranker inside a fraud-detection
  pipeline is **a model**. The ranking is a quantitative
  estimate of fraud probability.
- An LLM producing customer-facing text where the text
  influences a decision is **a model** under the broader
  reading now common among examiners. The text is not
  itself a quantitative estimate, but the influence on the
  downstream decision is.
- An LLM used purely as a calculator-style assistant with
  no decision influence (format my email, summarise this
  internal document) is **arguably not a model** under
  SR 11-7's literal text — but the trend is for examiners
  to read "quantitative estimate" broadly whenever the
  output materially shapes a judgment or action.

mod-102 §4 referenced the *black-box
defense* — the attempt to argue a system was not a "model"
because its internals could not be inspected or because it
produced qualitative outputs. CFPB and prudential examiners
have both rejected that framing in enforcement contexts.
The same logic applies to MRM scoping: trying to define a
system *out of* "model" scope to avoid MRM investment is a
losing strategy. The scoping decision will later be read
in a bad light if the system fails.

The operational rule: **when in doubt, scope in**. A
system scoped in and tiered low is defensible. A system
scoped out and later found to be a model is a finding.

## The three lines of defense, applied to MRM

SR 11-7 explicitly assigns roles across the three lines of
defense (the term 3LOD was contemporary with the guidance
and has stuck):

| Line | Function | Role under SR 11-7 |
|---|---|---|
| First | Model owners (developers, business users) | Build, document, implement, and use the model correctly |
| Second | MRM function | Independent validation, ongoing monitoring oversight, MRM policy stewardship |
| Third | Internal audit | Periodic assurance that the first two lines are working as designed |

Two consequences follow immediately:

- **MRM is not the model team.** A firm whose "MRM
  function" sits inside the modelling team has
  misunderstood SR 11-7. MRM must be structurally
  independent of model ownership. This is the single most
  common structural error.
- **The CAO function sits in the second line alongside
  MRM — not on top of it.** This is developed in detail in
  Chapter 6 of this module. For now: both are second
  line, both oversee model-related risk, and the boundary
  between them is operational, not hierarchical.

## Why SR 11-7 has aged well for AI/ML

SR 11-7 was written for logistic regressions, Monte Carlo
simulations, and macroeconomic forecasting models. It has
aged well for 2020s AI/ML for three reasons:

1. **It is framework-agnostic.** The principles do not
   assume a specific model class. A 1990s logistic-
   regression credit model and a 2025 fine-tuned LLM both
   fit the "quantitative method producing quantitative
   estimates" definition. Specific validation techniques
   change; the four pillars do not.
2. **It separates *what* must be done from *how*.** The
   four pillars are required; the implementation is left
   to the firm. This survives technology change in a way
   that a more prescriptive standard — specifying, say,
   particular statistical tests — would not. A firm that
   wants to add adversarial red-teaming as a validation
   pattern can do so under SR 11-7; the guidance does not
   enumerate the techniques.
3. **It centers documentation and replication.** SR 11-7
   demands that another competent professional could
   reproduce the model's development, validation, and
   monitoring from the documentation alone. For classical
   models this discipline was already standard. For ML
   models it is often absent at the start of a program.
   SR 11-7 forces it, and the resulting discipline
   generalises well — the "reproducible by another
   competent professional" standard is the same standard
   that academic ML, FDA PCCP, and ISO/IEC 42001 record
   discipline eventually converge on.

The aging-well property is why the AI governance community
has consistently reached for SR 11-7 rather than
reinventing MRM. The reach is correct. The misreading
risk — treating practitioner elaborations as if they were
the source — is the thing to guard against.

## What SR 11-7 does not address well

Honesty about the gaps keeps a program credible when an
examiner asks the hard question:

- **Continuous-learning systems.** SR 11-7 was written
  for stationary models — build once, validate once,
  monitor, retire. Modern ML systems retrain on schedules
  short enough that the validation posture must adapt.
  FDA's Predetermined Change Control Plan (PCCP) guidance
  is closer for adaptive systems; SR 11-7 supervisors are
  working out their posture in real time as of 2026.
- **LLMs and generative outputs.** SR 11-7's validation
  framework assumes the model's output is *evaluable*
  against ground truth. Many LLM outputs are not —
  free-form text, generated code, drafted summaries have
  no single right answer. The MRM community is actively
  developing techniques; Chapter 3 of this module covers
  the current state.
- **Vendor / third-party AI.** SR 11-7 §V covers
  third-party models but predates the foundation-
  model-as-service pattern (an LLM provider swapping the
  underlying weights behind a stable API). SR 22-6 is a
  partial update; the operational gap remains, and
  Exercise 04 forces a specific resolution.
- **System composition.** SR 11-7 implicitly treats "the
  model" as a single artifact. A modern ML system is
  often a chain — retrieval + reranker + LLM + output
  filter + policy wrapper. The pillars still apply, but
  *to what*? Programs that validate only the central
  model and ignore the chain leave half the system
  outside the framework.

These gaps are real. They are not reasons to ignore SR
11-7; they are reasons to extend it carefully, which is
what the remainder of this module teaches.

## Reading the source directly

Three concrete suggestions if you have not read the
guidance yet:

- **Read §III, §IV, §V end-to-end** before reading any
  practitioner commentary. The sections are short.
  Reading them cold forces you to form your own reading
  rather than inheriting someone else's.
- **Mark every sentence that uses "should" vs "may".** The
  modal verbs matter; "should" marks the load-bearing
  expectations.
- **Mark every passage where the guidance punts to the
  firm.** Passages that say "appropriate to the model's
  risk" or "commensurate with" are permission to firm-
  specific implementation. These are where the room to
  design lives.

The source is linked in [`resources.md`](./resources.md)
Tier 1.

## Summary

- SR 11-7 is a 21-page document that is both load-bearing
  and widely misquoted. Read the source; distinguish text
  from folklore.
- It defines model risk as having two sources —
  fundamental error and misuse — and addresses both.
  Programs that focus only on fundamental error are doing
  half the discipline.
- The four pillars (development, validation, governance,
  firm-wide integration) are required; firms that skip any
  one of them do not have an MRM framework.
- The model definition is broad on inputs, specific on
  "quantitative estimates" outputs. The operational rule
  is *when in doubt, scope in*.
- MRM sits in the second line, structurally independent
  of the model owner. The CAO function sits alongside
  MRM in the second line, not above it.
- SR 11-7 has aged well because it is framework-agnostic,
  separates what from how, and centers reproducibility.
- Its gaps — continuous learning, LLM outputs, vendor
  foundation-model swaps, system composition — are real
  and are extended, not ignored, by the rest of this
  module.
