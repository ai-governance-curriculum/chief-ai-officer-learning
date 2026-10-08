# Chapter 2 — The AI Risk Appetite Statement

## Why this chapter exists

The AI risk appetite statement is the single
most important document the CAO authors for the
board. Everything else operates against it. The
quarterly report (Chapter 3) uses its
categories; the materiality framework (Chapter
4) sets thresholds relative to its boundaries;
the incident classification taxonomy ([`mod-107`](../mod-107-ai-security/README.md)
§6) escalates when a case approaches its limits;
the GOVERN loop ([`mod-103`](../mod-103-ai-risk-frameworks/README.md)
§6) uses it to decide which treatment actions
are inside policy and which require board-level
re-ratification.

A program without a working appetite statement
operates on *implicit* appetite — whatever the
CAO function individually decides is acceptable
risk in the moment. Implicit appetite is not
appetite; it is drift. Different leaders, under
different pressures, produce different
dispositions on identical cases. The board
cannot ratify what it cannot see, and the
regulator cannot evaluate what was never
written down.

The chapter teaches the structure that works,
the language patterns that make appetite
expressible in board-readable form, and the
drafting process that gets a working statement
adopted without three years of committee.

## 2.1 What a risk appetite statement is

A working AI risk appetite statement:

- **Names** the categories of AI risk the
  organisation faces, drawn from the AI risk
  taxonomy the program has already adopted
  ([`mod-103`](../mod-103-ai-risk-frameworks/README.md)
  §2).
- **Expresses**, for each category, how much
  risk the organisation chooses to take.
- **Establishes** the boundary between
  acceptable and unacceptable.
- **Names** the process by which cases that
  approach or exceed the boundary are
  escalated.
- **Sets** the review cadence under which the
  board revisits the statement.

The statement is **adopted by the board**, not
authored by the board. The CAO authors; the
CRO, CFO, CCO, GC co-sharpen; the AI Risk
Council endorses; the Board Risk Committee
reads it out and recommends to the full board;
the board adopts. The program then **operates
against the ratified statement**, not against
the CAO's internal view of appetite.

A statement that is adopted but then operated
in parallel with a different internal view is
worse than no statement. The regulator or
auditor who finds the two inconsistent is
being handed a specific finding.

## 2.2 What a risk appetite statement is not

Four distinctions worth drawing explicitly,
because each is a common failure mode:

- **Not a risk tolerance.** Tolerance is what
  the organisation can *withstand*; appetite is
  what the organisation *chooses to take*. The
  two often differ — an organisation can
  withstand more risk than it chooses to take,
  and an organisation that chooses more risk
  than it can withstand is mispriced. Appetite
  is a *choice*; tolerance is a *constraint*.
  (The COSO ERM appetite guidance is the
  standard reference for this distinction.)
- **Not a control catalogue.** Controls
  operationalise appetite — they are the
  mechanisms by which the program keeps itself
  inside appetite. The appetite is the source
  statement; controls derive from it. Appetite
  statements that drift into enumerating
  controls have forgotten what they are for.
- **Not a list of metrics.** Metrics measure
  whether the program is within appetite; they
  are downstream of the appetite statement, not
  within it. A statement padded with metric
  tables is diluting the signal; the metrics
  belong in the quarterly report or in the AI
  Risk Council pack.
- **Not a policy.** Policies derive from the
  appetite — the fairness policy, the model
  validation policy, the vendor AI policy, the
  acceptable-use policy. The appetite is the
  source of their authority; the appetite is
  what the board adopts and the policies are
  what management writes.

A test: if the document could be read without
loss by substituting "policy" or "standard" for
"appetite statement," it is not an appetite
statement — it has become a policy.

## 2.3 The structure that works

A working AI risk appetite statement has five
elements, in this order:

### 2.3.1 Preamble

Short — a paragraph. What AI risk means at this
organisation; what this statement does; the
relationship to the organisation's enterprise
risk appetite (the one that already exists for
non-AI risks). The preamble establishes
authority: this statement is adopted by the
board under the enterprise risk appetite
framework, inheriting its ratification
discipline.

### 2.3.2 Risk categories

Drawn from the program's AI risk taxonomy. For
most organisations, six to ten categories
covers the ground:

1. **Model performance.** Accuracy, drift,
   degradation, failure modes.
2. **Bias and fairness.** Disparate performance
   across protected classes, substantive
   fairness in decisions.
3. **Transparency and explainability.**
   Capacity to explain decisions to affected
   parties, regulators, internal review.
4. **Privacy and data.** Data minimisation,
   purpose limitation, personal-data
   protections in AI systems.
5. **Security.** Classical and AI-specific
   attack surface (prompt injection, data
   poisoning, model extraction).
6. **Vendor and third-party AI.** Dependency,
   concentration, contract and governance
   coverage.
7. **Market and conduct.** Market-abuse,
   consumer-conduct, suitability in
   AI-mediated interactions.
8. **Strategic and reputational.** Programmatic
   and public-exposure risks that do not fit
   the operational categories.

The specific list is organisation-specific.
What matters is that the categories are the
*same categories* the quarterly report (Chapter
3) will use for the risk posture summary. A
category in the appetite statement that has no
corresponding row in the quarterly report is
unoperationalised; a category in the quarterly
report that has no corresponding appetite row
has no benchmark against which to be
evaluated.

### 2.3.3 Per-category appetite

For each category, the appetite is expressed
in board-readable language. §2.4 teaches the
three patterns that work. Each category gets
roughly one paragraph plus one boundary or
threshold.

### 2.3.4 Escalation process

What happens when a case approaches or exceeds
a boundary. The escalation integrates with the
incident classification taxonomy (mod-107 §6)
and the materiality framework (Chapter 4). A
working escalation names:

- The decision point at which escalation
  triggers (approaching the boundary; crossing
  the boundary; sustained crossing).
- Who is informed at each level (AI Risk
  Council; AI Risk Lead; CRO; Board Risk
  Committee chair; full board).
- The decision authority at each level
  (CAO-function remediation; AI Risk Council
  disposition; CRO-escalated review;
  Board Risk Committee ratification).

### 2.3.5 Review cadence

When the board reconsiders the statement. For
most organisations: **annually**, as part of
the enterprise risk appetite review cycle;
**off-cycle on material trigger** — a
regulatory shift, a material incident, a
material business change, a material change in
AI capability or deployment that makes a
previous boundary obsolete.

A statement that is never reviewed is a
statement that is quietly diverging from
reality. A statement that is reviewed every
quarter is a statement without the authority a
board-adopted document needs. Annual plus
material-trigger is the discipline.

## 2.4 Expressing appetite in board-readable language

The hardest practical problem in drafting an
appetite statement is that appetite is
inherently fuzzy and the board needs to be
able to act on it. Three language patterns
work, and a working statement uses all three.

### 2.4.1 Pattern 1 — Risk-class language

The high-level framing of what kinds of risk in
this category the organisation accepts and does
not accept:

> *We accept material model-performance risk
> where the business case justifies it and
> independent validation ([`mod-104`](../mod-104-model-risk-management/README.md))
> demonstrates fitness for purpose. We do not
> accept performance risk that materially
> affects customers without explicit
> customer-impact review by the AI Risk
> Council.*

Risk-class framing establishes the posture.
It does not, on its own, tell the operator
when they have crossed the line.

### 2.4.2 Pattern 2 — Boundary language

Named categorical limits — things the
organisation will not do:

> *The organisation will not deploy AI systems
> that produce binding adverse decisions for
> which we cannot provide affected-party
> explanations meeting Reg B
> (12 CFR 1002.9) or GDPR Art. 22 standards,
> as applicable to the jurisdiction of the
> affected party.*

Boundary language draws clear lines. It is
how the appetite statement operationalises the
"will not" cases — the ones where no amount of
business justification should override the
line.

### 2.4.3 Pattern 3 — Threshold language

Quantitative triggers that connect appetite to
measurable program state:

> *Bias risk appetite: an equalised-odds gap
> greater than 5 percentage points across any
> protected class, sustained over two
> consecutive monitoring cycles, is outside
> appetite for any Tier 1 system.*

Threshold language is the connection point to
the metrics and monitors the program actually
runs. Without threshold language, the appetite
cannot be operationalised against the
monitoring stack; without risk-class and
boundary language above it, the threshold is a
number without context.

### 2.4.4 Combining the three

A working appetite statement, for each
category, combines all three:

- Risk-class framing to set the posture;
- Boundary language to name the categorical
  limits;
- Threshold language to connect the appetite
  to the monitoring stack.

The combination is what lets the board read a
paragraph and understand both the shape of
the appetite and the specific triggers that
indicate it is being challenged.

## 2.5 The hardest categories

Some categories are harder than others to
express appetite for. The hard categories are
worth drafting carefully — if the appetite
statement collapses on them, the hard cases
are also the ones most likely to produce board
embarrassment later.

### 2.5.1 Bias and fairness

The fairness impossibility result ([`mod-105`](../mod-105-responsible-ai-and-ethics/README.md)
§3.2) is operational, not academic: an AI
system cannot simultaneously satisfy equalised
odds, predictive parity, and demographic parity
except in degenerate cases. The appetite
statement cannot be silent on which conception
takes priority — if it tries, the program will
later be measured against all three and found
wanting on at least one.

The statement must **name a primary
conception** and acknowledge that others are
not enforced:

> *For Tier 1 systems in retail credit,
> equalised odds is our primary fairness
> conception. We do not enforce predictive
> parity simultaneously and acknowledge the
> trade-off this choice represents.*

Boards do not need to understand the formal
impossibility result; they need to see that
the CAO has made the choice knowingly rather
than by inheritance.

### 2.5.2 Reputational risk

Reputational risk is inherently subjective and
the thresholds in other categories do not
transfer. The statement names the *kinds* of
reputational risk the organisation will not
accept rather than attempting thresholds:

> *We will not deploy AI capabilities whose
> plausible failure modes would produce
> front-page coverage without a defensible
> position on how the capability met our
> stated governance standards at the time of
> deployment.*

The pattern — a conditional that defines
"what good looks like" when the capability
fails — is more operational than a threshold
would be.

### 2.5.3 Strategic risk

Strategic appetite is directional, not
bounded. The statement frames it as "we will
/ will not pursue X" rather than as thresholds:

> *We will pursue AI capabilities that extend
> existing customer value propositions. We
> will not pursue AI capabilities whose
> primary value is to intermediate the
> customer relationship in ways that
> structurally reduce human contact.*

Strategic appetite is the one place where the
statement crosses most explicitly into product
and commercial territory. The CAO drafts in
close partnership with the CEO and the
business line heads, not alone.

### 2.5.4 Model-safety / frontier-model risk

For organisations deploying frontier LLMs or
operating at or near research-grade AI
capability, a separate category for
model-safety risk is worth standing up — the
operational analog to published Responsible
Scaling Policies (Anthropic RSP, OpenAI
Preparedness Framework, Google DeepMind
Frontier Safety Framework) adapted to the
organisation's own posture. The appetite names
the capability thresholds above which internal
review discipline tightens.

## 2.6 Drafting the appetite

The drafting process matters as much as the
content. A statement rushed through adoption
produces a statement that has not been
sharpened, and the sharpening then happens
in-flight as the program operates against it —
which is the worst possible place for it to
happen.

A working drafting process has five stages:

1. **CAO + AI Risk Council draft.** The CAO
   produces the first draft; the AI Risk
   Council reviews it line by line. This
   stage produces a *working draft* —
   internally coherent, grounded in the
   taxonomy, structurally complete.
2. **Pre-circulation to CRO, CFO, CCO, GC.**
   The four C-suite peers who will each have
   to operate against this appetite in their
   own domains review substantively. The
   output of this stage is a draft that
   survives peer review — one that the CRO
   can defend to the Board Risk Committee
   without surprises, one that the CFO can
   reconcile with the enterprise risk
   appetite, one that the GC can defend as
   consistent with the obligations register.
3. **Pre-circulation to Audit Committee chair
   and Board Risk Committee chair.** The two
   board chairs who will shepherd the
   statement through adoption read it out
   before it hits the full board. This is
   where directors with substantive AI
   interest sharpen the language and name the
   things they personally would want to be
   able to point to. The output: a draft the
   chairs are prepared to defend.
4. **Board review and adoption.** Typically
   over one to two board cycles — the first
   cycle is a read-out and discussion with
   feedback; the second is the adoption vote.
   First-cycle adoption is possible but
   signals the pre-circulation was
   insufficient.
5. **Annual review.** The statement is
   revisited annually alongside the
   enterprise appetite review; material
   triggers can bring it back off-cycle.

The pre-circulation steps are not optional.
Boards do not want to be the first audience
for a substantive new document; a statement
that arrives at the board without
pre-circulation is almost always sent back
for revision, which costs a cycle and signals
to the board that the function is not yet
operating with the discipline the function
needs.

## 2.7 The adoption dynamics worth anticipating

Three dynamics come up in nearly every
adoption cycle. Anticipating them saves time
and face:

- **The "why so much on bias" dynamic.**
  Directors new to AI governance often ask why
  the bias category receives more detail than
  other categories. The honest answer is that
  bias is the category where the operational
  gap between appetite and current state is
  largest; where regulatory attention is
  highest; and where the measurement
  discipline is most mature. The response is
  not to level down the bias section; it is to
  explain the asymmetry and offer to deepen
  other categories as the discipline in each
  matures.
- **The "quantify everything" dynamic.** A
  director with a finance or risk background
  asks why not every boundary is quantified.
  The honest answer is that some risks are
  not usefully quantified — reputational risk
  does not admit of a threshold, strategic
  risk is directional, bias quantification
  depends on which conception is primary. The
  response is to name which categories admit
  of thresholds and which do not, and to
  explain the pattern used in each.
- **The "aren't we just making this up"
  dynamic.** A sceptical director observes
  that the thresholds are judgments, not
  derivations from first principles. The
  honest answer is yes — appetite statements
  are judgments, calibrated to the
  organisation's context, informed by
  benchmarks where benchmarks exist, and
  adjusted over time as the organisation
  learns. The response is to show the
  calibration anchors (sector benchmarks,
  peer institution disclosures where
  available, the organisation's own historical
  incident experience) and to commit to the
  annual review discipline.

## Summary

- The AI risk appetite statement is the
  source document everything else operates
  against. Without it, program decisions
  derive from the CAO's implicit view, which
  drifts and which the board cannot ratify.
- The statement is **adopted by the board**,
  authored by the CAO, and operated by the
  program. It is not a tolerance, not a
  control catalogue, not a metrics list, and
  not a policy.
- Structure: preamble, categories, per-category
  appetite, escalation, review cadence.
- Three language patterns combine for each
  category — risk-class framing, boundary
  language, threshold language.
- The hard categories (bias, reputational,
  strategic, frontier-model safety) require
  explicit treatment. Silence on them is
  worse than inelegant treatment.
- Drafting is a staged process — CAO + AIRC,
  C-suite peers, board chairs, full board,
  annual review. Pre-circulation is not
  optional.
- Boards will ask three predictable
  questions during adoption. Prepare for
  them.
