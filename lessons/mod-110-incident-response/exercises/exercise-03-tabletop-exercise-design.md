# Exercise 03 — Lead a Tabletop Exercise Design

**Estimated time**: 3 hours
**Deliverable**: Tabletop design + scoring rubric (≤ 4 pages)

---

## The scenario

You are the CAO at **Halverston Capital**, a
diversified financial-services firm with three
lines of business (asset management, broker-
dealer, retail banking). The Audit Committee has
asked that the AI program run its first
cross-functional tabletop exercise. Participants
will include the CAO function, CISO, MRM, GC,
CCO, CTO, business-unit heads from all three
LOBs, and an external facilitator.

You have been asked to author the tabletop
design. The exercise will run as a single
half-day session simulating 72 hours of real
incident timeline.

## Your assignment

Produce the design in six sections.

### Section 1 — Goals (≤ ¼ page)

Three specific outcomes the exercise is intended
to produce. Each goal is a measurable indicator
tied back to Chapter 7 §7.1 (what tabletops
test):

- A specific **readiness indicator** — e.g., can
  the team make the four first-hour decisions
  (Chapter 2 §2.4) within the compressed first
  hour of the exercise.
- A specific **coordination indicator** — e.g.,
  do the CAO function and the CISO coordinate
  effectively on a joint-classification
  incident, with the single-named-lead
  convention holding under pressure.
- A specific **learning indicator** — the
  exercise surfaces at least two substantive
  issues per Chapter 7 §7.8.

### Section 2 — The scenario (≤ 1 page)

A realistic AI-incident scenario tailored to
Halverston's multi-LOB structure, meeting the
Chapter 7 §7.3 scenario discipline:

- **Grounded in a real pattern** — cite the
  precedent (a near-miss Halverston had, a
  peer-institution public incident, or a
  documented vendor incident) in the design
  document (though not in the facilitator's
  reveal to the players).
- **Cross-cutting on at least one dimension** —
  multi-LOB, multi-jurisdiction, or
  cross-functional at the classification
  boundary.
- **Contains at least one genuinely ambiguous
  decision** — a classification call, a
  containment posture, or a notification
  trigger that could reasonably go two ways.

Write the scenario as a one-page narrative in two
layers: the player-facing version the
facilitator will present, and the back-story the
facilitator holds (what actually caused the
incident, the correct containment posture in
hindsight, the ultimate regulatory expectation).

### Section 3 — Injects (≤ 1 page)

6–8 injects over the half-day, each
decision-forcing per Chapter 7 §7.4. For each
inject:

| Simulated time | Inject content | Decision forced | Target role |
|---|---|---|---|
| T+0 | Initial detection via <specific channel> | First-hour decisions (verify, classify, lead, containment) | AI Risk Lead / CISO on-call |
| T+1h | <information that reshapes classification> | Reclassification decision | Single named lead |
| ... | ... | ... | ... |

At least one inject must introduce the
notification matrix (Chapter 4) under pressure.
At least one inject must require revisiting the
containment posture (Chapter 3 §3.6). At least
one inject must introduce an external-
communication decision (Chapter 8) — press
inquiry, customer complaint pattern, or
regulator phone call.

### Section 4 — Roles and observers (≤ ½ page)

Per Chapter 7 §7.5, specify:

- Which roles play actively in the exercise
  (the response team members who would be on
  the real incident call for this scenario).
- Which roles observe (Audit Committee member,
  internal audit, downstream-function
  representatives).
- The facilitator's responsibilities — drive
  injects on schedule, maintain time
  compression, document decisions
  contemporaneously, hold the back-story,
  not participate substantively.

### Section 5 — Scoring rubric (≤ ¾ page)

Scoring on the four dimensions from Chapter 7
§7.6, each with 1–5 anchor points:

- **Decision quality.** 1 = decisions
  demonstrably indefensible on the facts
  available; 3 = defensible decisions with
  gaps the review will surface; 5 = decisions
  that would survive external review on
  content and reasoning.
- **Decision timing.** 1 = first-hour decisions
  not made in the first hour; 3 = made but
  with specific delays; 5 = made within the
  windows the matrix / scenario required.
- **Coordination.** 1 = single-named-lead
  convention fails; 3 = holds with friction;
  5 = holds cleanly with handoffs documented.
- **Documentation.** 1 = decisions not
  documented contemporaneously; 3 =
  documented with gaps; 5 = complete
  contemporaneous record aligned with the
  audit-ledger expectation.

Scores are reported per dimension, not
aggregated.

### Section 6 — Post-exercise review (≤ ¼ page)

Per Chapter 7 §7.6:

- The 30-minute hot-wash immediately after,
  with facilitator sharing the back-story.
- The written review within 10 business days
  with the Chapter 6 structure.
- Recommendations routed into the program
  improvement backlog (Chapter 6 §6.5) with
  owners and timelines.

## Constraints

- The scenario must be **realistic** —
  recognisable as a plausible Halverston
  incident, grounded in a cited pattern.
- The injects must include **at least one
  ambiguous** classification or containment
  call.
- At least one inject must exercise the
  notification matrix.
- At least one inject must require an external-
  communication decision (Chapter 8).
- The scoring rubric must include the
  documentation dimension. Programs that ignore
  documentation in tabletops produce real
  responses that do not survive audit.
- The post-exercise review must produce
  routed recommendations, not just findings.
- The exercise must fit in a half-day
  simulating approximately 72 hours.
- The design must not devolve into a training
  exercise (Chapter 7 §7.8 anti-patterns);
  participants are being tested, not trained.

## Rubric

| Criterion | Weight |
|---|---|
| Goals — three specific, measurable indicators | 15% |
| Scenario — grounded, cross-cutting, ambiguous | 25% |
| Injects — 6–8 decision-forcing with notification + external-comms coverage | 20% |
| Roles and observers — specific per Chapter 7 §7.5 | 10% |
| Scoring rubric — four dimensions with anchor points | 15% |
| Post-exercise review specified with routing | 10% |
| Length discipline — ≤ 4 pages | 5% |

## Where to submit

`chief-ai-officer-solutions/modules/mod-110-incident-response/exercise-03-tabletop-exercise-design/SOLUTION.md`

## Reading before you start

- Chapter 7 (tabletop exercises) of this module.
- Chapter 2 (first hour) and Chapter 3
  (containment) — the decisions the exercise
  tests.
- Chapter 4 (notification matrix) — one of the
  injects exercises this.
- Chapter 8 (enterprise-face communication) —
  at least one inject exercises this.
- [`mod-107`](../../mod-107-ai-security/README.md)
  Ex-04 (classification taxonomy) for scenario
  grounding.
