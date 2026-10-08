# Chapter 7 — MRM Outside Banking

## Why this chapter exists

SR 11-7 is banking guidance, issued by prudential
supervisors to prudentially-supervised firms. Its
*applicability* outside banking is not automatic — a
hospital system is not under OCC/FRB jurisdiction, and
pointing to SR 11-7 at a healthcare regulator produces
politely raised eyebrows.

Its *discipline*, however, is one of the most useful
imports a non-bank can make. The four pillars, the
tiering concept, the independence of validation, and the
documentation standard are all framework-agnostic. The
question for a non-bank CAO is not *do we adopt SR
11-7?* — it is *how do we import the discipline SR 11-7
encodes without claiming an obligation that does not
apply to us?*

This chapter develops the translation into four non-
banking contexts: healthcare, insurance, public sector,
and industrial. Exercise 05 forces the construction of
an MRM-equivalent program in a healthcare setting.

## What translates well

Several SR 11-7 features travel across sectors with
little adaptation:

- **The four pillars** (development, validation,
  governance, firm-wide integration). These are
  framework-agnostic. Any serious model-governance
  program converges on something structurally similar,
  often without naming SR 11-7 explicitly.
- **The model definition** — "quantitative method whose
  outputs drive decisions." Useful in any context. The
  vocabulary (what counts as a "model") may change but
  the underlying scoping question does not.
- **The independence requirement for validation.** This
  is the discipline that separates serious programs from
  ceremonial ones. It applies in healthcare,
  government, insurance, and industrial contexts with
  equal force.
- **Documentation discipline.** "Reproducible by another
  competent professional" is the right standard
  everywhere. It is sometimes articulated differently —
  FDA's PCCP requires "device description sufficient
  for review"; ISO/IEC 42001 requires management-system
  records — but the content is the same.
- **Tiering.** The principle applies universally. The
  criteria adapt to sector materiality.
- **The two-source model risk framing** (fundamental
  error plus misuse). Industrial AI is where the misuse
  framing is most under-recognised — operators using
  AI recommendations outside the validated envelope is
  the textbook example.

## What does not directly translate

Several SR 11-7 features are banking-specific or classical-
model-specific and require explicit adaptation:

- **The MRM "committee" architecture.** Large banks have
  Model Risk Committees with named senior membership
  (CRO, CFO, Chief Model Officer, senior line
  executives). Non-banks may not have a committee at
  that level and forcing one into existence is often
  wrong. The pattern that works is to use existing
  risk-committee architecture with an MRM agenda item
  — a Quality & Safety Committee in healthcare; an
  Enterprise Risk Committee in insurance; an existing
  governance body in public sector.
- **The challenger-model paradigm.** As Chapter 3
  noted, this is less applicable for ML. Outside
  banking it is also often inapplicable because
  classical alternative models do not exist for the
  use case — there is no challenger model for a
  radiology AI, no challenger for a child-welfare risk
  screener. The validation pattern set from Chapter 3
  travels; the challenger-first default does not.
- **The "model" vocabulary.** Healthcare prefers "device
  algorithm" or "clinical decision-support tool."
  Insurance varies by regulator but often uses
  "predictive model" or "actuarial technique." Public
  sector tends toward "automated decision system."
  Industrial uses "advisory system" or "control
  recommendation." Use the local vocabulary; a
  governance document that forces banking language on a
  hospital reads foreign and gets resisted.
- **The regulator-interface model.** Banks have a single
  prudential supervisor who speaks for all of model
  risk. Healthcare has FDA (for devices), CMS (for
  reimbursement and conditions of participation), and
  state regulators (for professional licensure and
  insurance). The regulator interface is pluralised
  and the governance program must address each.

## Healthcare adaptation

Healthcare has its own regulatory analogs — the FDA's
Software as a Medical Device (SaMD) framework and the EU
Medical Device Regulation (MDR). These cover
*device-classified* AI narrowly. Many AI systems in a
hospital are not device-classified — operational AI
(capacity management, staffing, scheduling), workflow AI
(prior authorisation drafting), administrative AI
(coding, revenue cycle). These sit outside FDA scope
and need an MRM-like discipline the device frameworks do
not provide.

### What works in healthcare

- **The MRM-equivalent home is the Chief Quality
  Officer's office or the Chief Medical Officer's
  office**, depending on the health system's
  structure. The AI governance function sits alongside,
  providing AI-specific overlays. The clinical safety
  committee is the natural governance body.
- **Validation independence maps to "clinical safety
  review of AI separate from AI development"**,
  typically through the medical staff committee
  structure. Perfect independence is hard in a hospital
  system where everyone's reporting lines ultimately
  converge in the C-suite; structural workflow
  constraints (which clinician gets the recommendation,
  what the override discipline is) do much of the work
  that organisational separation does in a bank.
- **The FDA PCCP guidance** is the closest analog for
  continuous-learning systems. It is the most useful
  non-SR-11-7 document for an AI healthcare governance
  program.
- **The behavioural-envelope concept** (from Chapter 1,
  misuse) is particularly load-bearing. Clinical AI used
  outside its validated envelope is the pattern that
  produces the headline-grabbing failures.

### Specifically for Exercise 05

Exercise 05 builds an MRM-equivalent for a non-bank
healthcare system. The reference approach:

- Translation uses *clinical decision support tool* and
  *operational AI system* as the local vocabulary.
- The four pillars map to existing functions where
  possible — development to the IT/informatics
  function; validation to clinical safety + AI
  governance jointly; governance to the Quality
  Committee; firm-wide integration to a cross-committee
  AI oversight body.
- Independence is addressed structurally rather than
  through claimed organisational independence —
  honestly acknowledging that in an 800-bed hospital
  system, perfect independence is implausible.

## Insurance adaptation

Insurance is closest to banking in regulatory DNA. State
insurance regulators oversee carriers; actuarial models
have their own validation tradition (actuarial opinion,
ASOP standards) that structurally resembles MRM. The
NAIC Model Bulletin on the Use of Artificial Intelligence
Systems by Insurers (2023) explicitly imports MRM-like
discipline for AI, with specific requirements for
governance, risk management, documentation, and
third-party oversight. Several states have adopted it
(the list grows; check state-by-state).

### What works in insurance

- **The actuarial-validation function is the natural
  MRM home.** It has decades of validation discipline
  on actuarial models. Extending its scope to AI
  underwriting, AI claims-triage, and AI pricing models
  is a smaller step than building a new function.
- **The state insurance regulator is the analogous
  prudential supervisor.** The regulator interface is
  state-by-state, which is more fragmented than banking
  but structurally similar — a dedicated supervisory
  relationship with reporting obligations.
- **The NAIC Model Bulletin** reads as a direct import
  of MRM principles into AI, with carrier-specific
  terminology. Programs built against it have strong
  structural overlap with programs built against SR
  11-7.

### The common gap

The most common gap in insurance AI governance is that
AI *underwriting* models do not get the same validation
rigor as classical actuarial models. The CAO function's
job is to close that gap, often by partnering with the
existing actuarial-validation function and extending
its scope rather than building parallel machinery.

## Public sector adaptation

Public-sector deployments — benefits eligibility
decisions, recidivism risk scoring, child-welfare
screening, immigration processing — have the strongest
direct-affected-person impact but often the weakest MRM
machinery. The regulatory frameworks are newer:

- **Canadian Directive on Automated Decision-Making**
  (Treasury Board of Canada Secretariat) — the clearest
  public-sector analog to SR 11-7, with explicit tiering
  (Impact Levels I–IV) and corresponding governance
  requirements.
- **OMB M-24-10 / M-25-21** (United States federal) —
  AI use in federal agencies with specific requirements
  for *rights-impacting* and *safety-impacting* AI.
- **State and city-level requirements** — New York City
  Local Law 144 (automated employment decision tools);
  various state algorithmic-accountability measures.

### What works in public sector

- **Build MRM discipline more or less from scratch**,
  anchored to the applicable regulatory framework.
  There is rarely an existing MRM-equivalent function
  to inherit.
- **Pay particular attention to transparency to
  affected persons** — FOIA, due-process, and record-
  availability obligations in public-sector contexts
  are substantially stronger than in private sector.
- **Algorithmic-discrimination testing** is often
  state-mandated or federally-expected. Build it in
  from the start.
- **Inventory of automated decision systems** is a
  near-universal requirement. The Canadian Directive,
  NYC LL35-2018 (algorithmic tool inventory), and
  various state parallels all require it. Treat the
  inventory as a public-facing document, not an
  internal one — many jurisdictions require public
  posting.

### What is different

- The regulator is often the *agency's own general
  counsel or Inspector General*, rather than an external
  supervisor. This changes the examination dynamics
  substantially — the examining function is the firm's
  own.
- Procurement is a central governance venue. A model
  procured on a contract may be governed by the
  contract more than by any MRM policy. Model risk
  management in public sector often lives in
  procurement discipline as much as in a traditional
  MRM function.

## Industrial adaptation

Industrial AI — predictive maintenance, quality
control, process optimization, control-loop
augmentation — has the most cleanly-defined ground
truth in many cases. The prediction can be checked
against the outcome in a reasonable timeframe.
Validation is often *easier* than in financial services
because the feedback loop is short and quantitative.

The discipline that typically gets skipped in industrial
AI is **misuse tracking**: operators relying on AI
recommendations beyond the validated operational
envelope. SR 11-7's misuse framing (Chapter 1) is
directly applicable and under-used.

### What works in industrial

- **The quality / reliability function is the natural
  MRM-equivalent home.** It has validation discipline
  for physical systems that extends naturally to AI
  advisors.
- **The operational envelope is the central
  governance artifact** — what operating conditions
  the system was validated for, what alarms when
  conditions move outside envelope. Industrial AI
  programs that specify the envelope and monitor
  excursions have most of SR 11-7's substance
  structurally.
- **Human-factors engineering** is the industrial
  parallel to the human-in-loop control design from
  Chapter 4. Industrial engineering has deep practice
  here that is often transferable.

### What is different

- There is no single regulator for industrial AI (OSHA,
  EPA, DOT, FDA for industrial systems that touch food
  or pharma — all possible, none dedicated to the
  "model risk" concept). The governance anchor is
  typically the firm's enterprise-risk function and the
  industry-specific safety regime (ANSI, IEC, ISO
  standards for the sector).
- The business-value framing is often *reliability* and
  *efficiency* rather than consumer-protection. MRM-
  style discipline needs to argue its ROI through
  prevented downtime and prevented safety events
  rather than through prevented regulatory enforcement.

## Translating MRM — a short recipe

For a non-bank CAO building an MRM-equivalent program:

1. **Name the sector-equivalent regulatory anchor.**
   FDA PCCP for healthcare device AI; NAIC Model
   Bulletin for insurance; Canadian Directive or
   OMB M-25-21 for public sector; industry-specific
   safety standards for industrial. The anchor replaces
   SR 11-7 as the external-authority point.
2. **Translate the vocabulary.** Use the local terms —
   device algorithm, decision-support tool, automated
   decision system, advisory system. Do not force
   banking language.
3. **Keep the four pillars.** Development, validation,
   governance, firm-wide integration — these are
   universal. The implementation adapts.
4. **Reuse existing functions where possible.** The
   quality office, the actuarial function, the
   compliance program, the procurement function. New
   parallel machinery is more expensive than extended
   existing machinery.
5. **Be honest about independence.** In most non-bank
   contexts, perfect validation independence is
   implausible. Structural workflow constraints,
   explicit documentation of residual conflict, and
   compensating controls carry the load.
6. **Build the inventory.** The inventory discipline
   from Chapter 5 works everywhere. The template may
   change; the obligation does not.
7. **Address the regulator interface explicitly.** In
   banking the regulator asks about MRM; outside
   banking the regulator may not have the vocabulary.
   The CAO function provides the translation.

## Summary

- SR 11-7 is banking guidance; its discipline is not
  banking-specific. The four pillars, tiering, the
  independence requirement, and the documentation
  standard all travel.
- The MRM committee architecture, the challenger-model
  paradigm, and the "model" vocabulary are
  banking-specific and need adaptation.
- Healthcare adaptation lives in the Quality / Clinical
  Safety function with CAO AI-specific overlays. FDA
  PCCP is the closest regulatory analog.
- Insurance is the closest to banking; the actuarial-
  validation function is the natural MRM home; the NAIC
  Model Bulletin reads as a direct MRM import.
- Public-sector programs usually build from scratch,
  with heavier attention to transparency, affected-party
  obligations, and inventory as a public document.
  The Canadian Directive is the clearest public-sector
  SR 11-7 analog.
- Industrial AI validation is often easier (short
  feedback loop); the misuse framing is the under-used
  piece.
- A short recipe — name the anchor, translate the
  vocabulary, keep the four pillars, reuse existing
  functions, be honest about independence, build the
  inventory, address the regulator — produces an MRM-
  equivalent program in any sector.
