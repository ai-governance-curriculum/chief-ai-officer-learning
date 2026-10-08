# Chapter 4 — Red-Teaming as Governance Practice

## Why this chapter exists

Red-teaming — adversarial evaluation of an AI system by
people specifically tasked with breaking it — has emerged
as one of the most-cited AI governance practices in
2024–2026. The EU AI Act's obligations on providers of
general-purpose AI models with systemic risk (Articles
51–55) require adversarial testing. NIST's AI 600-1
GenAI Profile names it in the MEASURE function. Vendor
Responsible Scaling Policies and voluntary commitments
cite it. Board members have begun asking "do we red-team
our AI?" at the same frequency they ask about pen-testing.

The CAO's job is not to execute red-teaming. The CAO's
job is to make sure the red-teaming the program does is
*governance-grade* — scoped, independent, repeatable,
evidenced — rather than security-engineering-grade one-off
exercises that produce no durable program value.

Exercise 02 asks you to design a specific red-team
exercise. This chapter is the governance discipline that
exercise fits within.

## 4.1 What red-teaming is for

Red-teaming for AI systems serves three program-level
functions. Each is independently necessary; a red-team
exercise that serves none of them is performance art.

1. **Discover unknown failure modes.** Adversarial minds
   find behaviours that the development team did not
   anticipate. The point is to surface what nobody
   thought to test for.
2. **Stress-test the controls.** Test whether the
   defense-in-depth design (Chapter 3) actually defends.
   A red-team exercise against a system with zero
   findings is more likely a weak exercise than a strong
   system.
3. **Produce evidence.** For regulators (EU AI Act Art.
   15 + the GPAI model documentation obligations), for
   the Board (as part of the AI risk pack), for internal
   audit — evidence that the program has done
   adversarial testing.

The three functions correspond roughly to the three
audiences for the exercise's output: the engineering
team (what to fix), the AI Risk Council / Board (how we
compare over time), and regulators (what proof we have).

## 4.2 What red-teaming is not

Honest distinctions. Three common conflations:

- **Red-teaming is not penetration testing.** Pen
  testing focuses on infrastructure — network,
  endpoint, identity, cloud configuration. Red-teaming
  for AI focuses on the AI system's behaviour and the
  system's defense-in-depth surface as a whole. Pen
  tests probe where attackers find footholds; AI
  red-teams probe where behaviour deviates from
  specification.
- **Red-teaming is not validation.** Validation
  (`mod-104` Chapter 3) evaluates whether the model is
  fit for purpose on its intended distribution.
  Red-teaming evaluates whether the system fails under
  adversarial pressure. Validation uses representative
  inputs; red-teaming uses deliberately unrepresentative
  inputs.
- **Red-teaming is not a substitute for monitoring.**
  Red-teaming surfaces failure modes; monitoring
  detects production occurrences. Both are needed. A
  firm that red-teams quarterly and does not monitor
  continuously will miss the attack that lands between
  exercises.

A program that uses red-teaming to replace any of these
other disciplines produces a gap elsewhere.

## 4.3 Red-teaming program elements

A working red-teaming program at the CAO level
specifies the following elements. A program missing any
is not red-teaming; it is ad hoc adversarial testing.

| Element | What it requires |
|---|---|
| Scope | Which systems get red-teamed, at what cadence, with what boundary |
| Methodology | The structured approach the red team uses (ATLAS-aligned scenarios, OWASP-aligned coverage, NIST 100-2-aligned classification) |
| Independence | Red team independence from the system development team — see §4.5 |
| Rules of engagement | What the red team can and cannot do, with explicit customer-protection rules |
| Reporting | What findings get reported, to whom, in what format, on what timeline |
| Disposition | How findings get triaged, prioritised, and remediated |
| Re-test | When and how findings are re-tested after remediation |
| Evidence | What artifacts get retained for audit and regulator |

Each row is non-optional. A program whose red-team
"charter" is a short bullet list missing half of these
rows will reach its first regulator request with no
answers.

## 4.4 Cadence

The right cadence depends on the system's tier (per
`mod-104` Chapter 2):

| Tier | Red-teaming cadence |
|---|---|
| Tier 1 Critical | Before deployment + quarterly + on material change |
| Tier 2 Important | Before deployment + annually + on material change |
| Tier 3 Standard | Trigger-based (incident, environment change, novel-threat emergence) |

Frontier-AI capability-tier systems (per Anthropic's
Responsible Scaling Policy and adjacent frameworks) have
*additional* cadences specific to capability thresholds —
pre-training-run evaluation, post-training evaluation,
pre-deployment capability-tier re-evaluation. Enterprise
CAOs who are not frontier-labs borrow discipline from
the RSP framings but do not need the full cadence.

What counts as a "material change" needs a program-level
definition. The default: a change to the model, the
prompt scaffolding, the tool catalogue, the identity /
capability manifest, or the downstream resource surface.
Vendor foundation-model swaps (`mod-104` Exercise 04) are
material changes.

## 4.5 Independence

The `mod-104` §3.3 independence test applies: if the
system fails in production, can the red team be
reasonably accused of bias toward the development team?
If yes, independence is insufficient.

The red-team independence patterns, from strongest to
most convenient:

- **External red team.** Contracted specialists outside
  the organisation. Highest assurance; highest cost;
  slower to spin up for repeat exercises; information-
  handling boundaries matter (how much of the system
  can be exposed to external parties).
- **Internal red team in a separate organisational
  branch.** Reports to CISO or to an independent
  function, not to the AI program. Good assurance;
  moderate cost; faster than external for repeat
  exercises; the independence is structural rather than
  contractual.
- **Internal red team within the AI program with
  structural safeguards.** Separate from the development
  team but in the same organisation. Operationally
  available; weaker independence test; viable for
  Tier 2 and Tier 3 but not Tier 1 without additional
  controls.

CAO-level positions: Tier 1 systems use external or the
second pattern at minimum; the third pattern is
acceptable for Tier 2 with explicit governance
arrangements (named independence protections, dedicated
reporting line, veto-free reporting path to the AI Risk
Council).

A fourth pattern — public bug-bounty or AI safety
bounty programs (HackerOne-mediated, Anthropic-style
model safety bounties) — complements but does not
substitute for scheduled red-teaming. Bounty programs
are opportunistic; the scheduled exercise is the
governance artifact.

## 4.6 Exercise design elements

A red-team exercise is *designed*, not improvised.
Exercise 02 asks you to design one. The design elements:

- **Threat model.** What the red team is testing
  against. Drawn from ATLAS / OWASP / NIST 100-2 per
  Chapter 2. The threat model names which attack
  categories are in scope and which are explicitly out
  of scope.
- **Rules of engagement.** What the red team can and
  cannot do (e.g., they can attempt prompt injection
  but cannot extract real PII even if the system would
  allow it). Customer-protection rules are mandatory.
- **Time-box.** How long the exercise runs. The length
  trades depth against program cadence — longer
  exercises find more; shorter exercises repeat more
  often.
- **Goals.** What specific outcomes the red team is
  trying to demonstrate. Example: "the trust-gate
  pipeline from `mod-106` Chapter 5 fails closed under
  prompt-injection pressure."
- **Scoring rubric.** How findings are graded —
  severity, exploitability, reproducibility, detection.
  The *detection* dimension is often the one program
  cares most about: did Tessera's own monitoring see
  the attack?
- **Out of scope.** What is explicitly excluded. Classical
  perimeter penetration, social engineering of
  employees, DDoS, and compromise of the vendor's
  internal weights are commonly out of scope.
- **Reporting structure.** How findings flow into
  remediation — the ticket queue, the disposition
  authority, the re-test commitment.

A design document that specifies all seven elements
makes the exercise executable without further
negotiation. A design missing elements produces
real-time scope disputes during the exercise, which is
when scope disputes are most expensive.

## 4.7 Governance-grade vs engineering-grade

The distinction that matters: a red-team exercise
produces *engineering value* (fixes to the system) and
*governance value* (evidence the program is doing the
discipline). Engineering-grade exercises optimise for
the first; governance-grade exercises hold the second
non-negotiable alongside the first.

The CAO's test: can the exercise's output be shown to a
regulator six months later with the regulator reaching
useful conclusions? Governance-grade yes; engineering-
grade sometimes, often not.

Specific governance-grade requirements that
engineering-grade exercises sometimes skip:

- **Reproducibility of each finding.** A finding that
  cannot be reproduced is not a finding; it is a
  story. Each finding ships with reproducible steps.
- **Severity scoring with explicit rubric.** Not
  informal priorities. The rubric is published; the
  findings are scored against it; disagreements go to
  a disposition committee rather than a hallway
  conversation.
- **Detection annotation.** For each finding, did
  Tessera's production monitoring observe the attack
  while it was happening? If not, that is a monitoring
  gap distinct from the finding itself.
- **Evidence retention.** Reproducible artifacts
  retained in the audit ledger (`mod-108`) with the
  disposition decision. Shelf life: through the next
  regulatory examination cycle at minimum.

Exercise 02's rubric penalises designs that skip any of
these.

## 4.8 Red-teaming the red team

An under-appreciated discipline: periodically evaluate
whether the red-team program itself is working. The
questions:

- Are findings tracked to closure, or do they sit open
  past their re-test SLA?
- Does the next exercise find variations of what the
  previous exercise found, or does it find new
  categories? (A plateau on finding types often means
  the methodology needs refresh.)
- Are findings from one system informing threat models
  on other systems? (The red-team's institutional
  learning should propagate.)
- Does the engineering team view red-team findings as
  signal or as noise? (A high-noise reputation collapses
  the program's influence.)

A program that red-teams its systems but never
evaluates the red-team program itself is missing one
level of the discipline.

## 4.9 What the CAO reads for in a red-team program

Five questions:

1. **Is cadence tiered?** All systems quarterly is both
   unaffordable and unprioritised. Trigger-based for
   everything is deferred cadence.
2. **Is independence structurally enforced for Tier 1?**
   An internal team "within the AI program" red-teaming
   Tier 1 is weak independence that will not survive
   regulator scrutiny.
3. **Does each finding have reproducible steps?** If
   not, the artifacts cannot be used after the
   exercise.
4. **Is the detection dimension in the rubric?** Without
   it, the program learns about failures but not about
   its own monitoring gaps.
5. **Does the exercise cadence feed the risk register?**
   Findings should land in `mod-103`'s AI risk register
   with explicit disposition. A red-team report that
   stops at the exercise is undercapitalised.

A CAO who can hold these five questions through a
red-team program review is doing the CAO's job on this
chapter.

## Summary

- Red-teaming for AI serves three program functions:
  discovery of unknown failure modes, stress-test of
  controls, production of evidence. All three are
  non-optional.
- Red-teaming is not penetration testing, not
  validation, and not a substitute for monitoring.
  Each distinction fails programs that collapse it.
- A working red-team program specifies scope,
  methodology, independence, rules of engagement,
  reporting, disposition, re-test, and evidence. Missing
  elements make the exercise ad hoc.
- Cadence is tiered: Tier 1 quarterly + on change;
  Tier 2 annually + on change; Tier 3 trigger-based.
  Material change triggers always apply.
- Independence patterns descend from external → separate
  internal branch → within-program with safeguards.
  Tier 1 systems do not use the third pattern alone.
- Governance-grade red-teaming adds reproducibility,
  explicit scoring, detection annotation, and evidence
  retention to engineering-grade. The CAO holds the
  additions non-negotiable.
- The red-team program itself needs evaluation on a
  cadence. A plateau on finding types means the
  methodology needs refresh.
