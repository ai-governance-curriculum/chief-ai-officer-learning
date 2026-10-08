# Chapter 6 — The CAO × MRM Boundary

## Why this chapter exists

The most predictable conflict in a CAO's first year — in
any organisation with an established MRM function — is
with the MRM head. Both functions are second line. Both
oversee model-related risk. Their scope overlaps, and
both have historically-defensible claims to parts of the
overlap. mod-101 Chapter 4 named this boundary; this
chapter operationalises it.

The conflict matters because the regulator and the board
read the organisation as a single entity. If the CAO and
MRM present inconsistent positions, the external parties
read the firm as internally confused. Resolving the
boundary is not optional; it is a first-year priority.

Exercise 04 forces a specific boundary dispute — a
vendor foundation-model swap — to a defensible
resolution.

## Where the boundary sits

Under SR 11-7, MRM is second-line, structurally
independent of the first-line model owners. The CAO
function, per mod-101 Chapter 4, is also second-line.
Both report (in a mature structure) to the CRO or to a
peer executive at that tier.

The boundary is not a hierarchy. It is a scope line
between two second-line functions. Neither sits above
the other. Mishandling this is the single most common
first-year error: a new CAO who positions as *above* MRM
on AI matters finds the MRM function (older, better
networked, with more operational history) quietly
blocks everything. A new CAO who positions as
*subordinate* to MRM on AI matters surrenders the AI-
specific obligations the role was created to carry.

The boundary that works is a *peer* boundary with
negotiated scope.

## What MRM owns

MRM, under SR 11-7, owns:

- **The MRM framework, policies, and standards** for
  *all* models — financial, actuarial, operational, ML.
  This is the pillar 3 governance stack.
- **Independent validation of models** within MRM scope.
  The actual act of validating.
- **Ongoing monitoring oversight** — verifying that
  first-line monitoring is working, escalating when it is
  not.
- **Model inventory completeness** within MRM scope.
  Every in-scope model has a current inventory entry.
- **The model risk committee** (or equivalent) operation.
- **Reporting to senior management and regulators on
  *model risk*** — SR 11-7 §V requires a periodic
  management report; MRM is the author.

The historical centre of gravity on each of these is
MRM. A new CAO function cannot and should not try to
claim them.

## What the CAO function owns

The CAO function owns:

- **AI-specific risks that are not exclusively model
  risk.** Bias and fairness at the *program* level
  (across many models), transparency to affected
  parties, AI-specific regulatory compliance (EU AI
  Act), AI vendor and ecosystem risk, AI incident
  patterns across the portfolio.
- **AI-specific governance bodies** — AI Review Board,
  AI Risk Council, AI Ethics Committee. These are
  typically newer than the model risk committee.
- **The AI risk taxonomy** (per mod-103 Chapter 2) — the
  category structure under which AI-specific risks are
  catalogued.
- **The AI risk register** — the operational artifact
  tracking AI-specific risks. mod-103 Chapter 6
  develops this.
- **AI program reporting to the board** — the AI section
  of the board risk pack, which may or may not be
  consolidated into the MRM report.
- **AI regulator engagement strategy** — EU AI Act
  authorities, FDA for health AI, state regulators,
  civil-society interlocutors.

Note what the CAO does *not* own, under this boundary:

- Validation of individual models. MRM does.
- Model-by-model monitoring. MRM does, with CAO input
  on AI-specific metrics.
- The model risk committee itself.

## The intersection — where both have legitimate claims

The overlap is genuine. Six topics predictably sit on
the boundary:

| Topic | How both can legitimately claim |
|---|---|
| ML model validation | MRM does the validation; the CAO sets AI-specific validation expectations (subgroup fairness, red-team cadence, LLM-specific patterns from Chapter 3) |
| Model inventory | MRM owns the inventory of *models*; the CAO owns the inventory of *AI systems* (per Chapter 5); the two overlap on every ML model but are not identical |
| AI-specific risks inside a model | Bias in a credit model is both a CAO concern (fair-lending program-level) and an MRM concern (model performance for a protected subgroup) |
| Incident response | MRM may have a model-incident process; the CAO may have an AI-incident process; a single incident often touches both |
| Vendor AI | MRM has third-party model governance; the CAO has AI vendor governance including foundation-model-swap exposure |
| Regulator interface | MRM is the historical SR 11-7 interface; the CAO is the EU AI Act interface; many issues touch both regimes |

The pattern on each topic is the same: both have a
legitimate claim; neither can unilaterally own the
topic without losing something important.

## Operating the boundary — patterns that work

Four patterns, in order of importance:

### Single named lead per topic

When an issue surfaces, one function leads the
investigation and the other is informed. The lead is
determined by the *primary framing* of the issue:

- Model error (accuracy failure, drift, prediction
  anomaly) → MRM leads.
- AI-specific pattern (bias across the portfolio,
  transparency failure, EU AI Act compliance question)
  → CAO leads.
- Combined (vendor foundation-model swap that affects
  both model quality and AI-specific risks) → joint,
  with a *single* named lead and the other function
  explicitly in support.

The named-lead convention is what allows the regulator
to hear one organisation. Dual leads produce dual
positions, which produce one examiner question: "which
of these is your official position?"

### Joint validation expectations

The CAO contributes to what the validation plan must
include; MRM executes. Specifically:

- For AI-specific risk categories (bias, transparency,
  AI-specific security), the CAO defines required
  validation patterns per Chapter 3's taxonomy —
  subgroup validation, red-team evaluation,
  counterfactual probing.
- MRM incorporates those patterns into the validation
  plan for in-scope models and executes.
- The validation report back to the AI governance body
  is co-signed by MRM (as the executing function) and
  acknowledged by the CAO (as the function that defined
  the AI-specific expectations).

This structure resolves the "MRM rejects AI-specific
validation patterns" failure mode by making the pattern
set a joint artifact.

### Cross-referenced inventories

Per Chapter 5. MRM's model inventory and the CAO's AI
system inventory point to each other. A row in one
references the corresponding row in the other. They are
not merged into a single artifact — they serve
different users with different scopes — but a reader
can traverse between them.

The operational test: can you take any entry in one
inventory and, in a single click or query, reach the
corresponding entry in the other? If not, drift will
appear.

### Joint regulator briefings

When SR 11-7 and EU AI Act both touch an issue, the CAO
and MRM lead present *together*. One speaker speaks for
both functions on the overlap, with the other
contributing on their domain. The regulator hears one
organisation. The post-meeting internal reconciliation
happens offline.

## The collision patterns — what fails

Four patterns that look reasonable and consistently
produce bad outcomes:

- **Re-validation of MRM-validated models by the CAO
  function.** Creates duplicative work; signals lack of
  trust in MRM; produces conflicting findings when the
  two validations differ on anything. The remedy is the
  joint-validation-expectations pattern above —
  influence the validation design, do not re-perform it.
- **Separate model inventories that diverge.** The two
  inventories drift; an audit opens both and finds the
  divergence; the program loses credibility on both
  sides. The remedy is cross-reference, not merge, with
  the discipline of mutual update.
- **MRM rejecting AI-specific validation patterns
  because "that's not in SR 11-7".** SR 11-7 explicitly
  leaves validation technique to the firm (Chapter 3).
  Refusing subgroup validation or red-team evaluation
  because classical MRM did not do them is a
  misreading of the source. The remedy is a short
  position paper from the CAO showing that the AI-
  specific patterns satisfy §IV's elements by other
  means.
- **CAO setting model-validation standards
  unilaterally.** Without MRM concurrence, the
  standards do not get applied — MRM owns the
  validation stack. The remedy is joint-standard-
  setting with a defined escalation path to the CRO
  (or shared executive) on disagreement.

Each of these patterns is traceable to one of the two
functions trying to be the hierarchical superior. The
peer-boundary design is the structural remedy.

## The reporting-line question

A recurring debate: should the CAO function and MRM
report to the same executive (CRO), or to different
executives?

| Pattern | Trade-off |
|---|---|
| Both report to CRO | Easier coordination (common executive); risk of organizational gravity pulling AI work into "another MRM team" over time |
| CAO to CRO; MRM to a peer (e.g., CFO or COO in some structures) | More independence between the functions; harder coordination; higher reliance on joint-committee machinery |
| Joint AI committee chaired by CRO with CAO and MRM Head as co-chairs | Coordination forcing function; works in mid-sized firms; weaker in very large firms where committee machinery is already saturated |

There is no universally correct answer. The most common
mature pattern in large banks is *both report to CRO +
joint operating committee*, where the committee is the
weekly forcing function for cross-boundary issues and
the CRO is the escalation point for disputes. In
smaller or non-bank firms the committee alone may
suffice.

What matters more than the reporting line is the
committee discipline: a weekly or biweekly working
committee at the right level, with written minutes, with
decisions that stick. A boundary that is only resolved
by executive adjudication is a boundary that is not
working.

## When the boundary should move

The scope line is not permanent. It should move when:

- **A category of risk becomes material enough to
  warrant dedicated governance.** When AI vendor risk
  grows from a few vendor models to a significant
  portion of the portfolio, the vendor-AI topic may
  justify its own working group under the CAO. The
  boundary with MRM third-party-model governance
  stays, but the operational depth on the CAO side
  grows.
- **A regulator issues sector-specific AI guidance.**
  EU AI Act enforcement guidance from a specific
  authority; FDA PCCP updates; state-level
  requirements. The CAO function typically absorbs the
  new obligation; MRM participates on model-quality
  dimensions.
- **An incident reveals a boundary gap.** A specific
  incident type that neither function recognised as
  theirs. The lesson learned is a boundary adjustment,
  documented in both functions' operating documents.

The discipline of a boundary that moves consciously is
different from the chaos of a boundary that moves
without record. Document each adjustment.

## Working the boundary at steady state

A CAO function that has made peace with MRM typically
has:

- A short, co-signed scope memo describing the
  boundary. Both heads sign; refreshed annually.
- A joint-committee cadence that is the primary venue
  for cross-boundary decisions.
- Mutual read-access to each function's inventories,
  working documents, and incident logs. Opacity between
  the two functions is where boundary conflicts breed.
- A named escalation path to a shared executive for
  the rare disputes that cannot resolve at working
  level.
- A joint annual report to the board that covers both
  model risk and AI-specific risk, with explicit
  cross-references.

The absence of any of these items is a diagnostic. A
CAO who cannot describe the cadence by which they
coordinate with MRM has not yet solved the boundary.

## Summary

- The CAO × MRM boundary is a peer-boundary between two
  second-line functions. Hierarchical framings
  (either direction) fail predictably.
- MRM owns the MRM framework, individual-model
  validation, and model inventory; the CAO owns the AI
  taxonomy, AI-specific risks, and AI regulatory
  interface.
- Six predictable intersection topics — model
  validation, inventory, risks-inside-a-model, incident
  response, vendor AI, regulator interface — have
  legitimate claims from both sides.
- Four operating patterns work: single named lead per
  topic, joint validation expectations, cross-referenced
  inventories, joint regulator briefings.
- Four collision patterns fail: re-validation, parallel
  divergent inventories, MRM rejection of AI patterns,
  unilateral CAO standard-setting.
- Reporting-line choice matters less than committee
  discipline. The mature pattern is both-to-CRO with a
  working committee.
- Boundaries move consciously, not accidentally. Document
  each adjustment.
