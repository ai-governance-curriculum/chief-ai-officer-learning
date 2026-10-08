# Exercise 05 — Author a Defense-in-Depth Program Standard

**Estimated time**: 3 hours
**Deliverable**: A defense-in-depth program standard
(≤ 3 pages)

---

## The scenario

You are the CAO at **Halverston Capital** (the
context from `mod-103` / `mod-105` / `mod-106`). The
CISO and you have agreed (per the Exercise 03
boundary resolution pattern of this module) that
the CAO function authors the **program-level
requirements** for AI defense-in-depth and the CISO
authors the security-engineering implementation
guidance. The CAO has been asked for the program
standard.

## Your assignment

Author the **AI Defense-in-Depth Program Standard**
covering Halverston's three lines of business
(public markets, private credit, wealth advisory).

The standard must:

### Section 1 — Scope (≤ ¼ page)

What systems are in scope, what is out of scope,
which tiers (per `mod-104` Chapter 2) attract which
levels of required defence depth.

### Section 2 — The nine-layer model (≤ 1¾ pages)

For each of the nine layers from
[Chapter 3 §3.1](../03-defense-in-depth-for-ai.md)
(principal, input, model, output, tool, data,
infrastructure, observability, response), specify:

- **What must be defended** at the layer
  (program-level requirement).
- **Required controls** at the layer (high-level —
  *what* not *how*).
- **Acceptance criteria** — what evidence shows
  the layer is operating.
- **Tiered application** — what is required at
  Tier 1 vs Tier 2 vs Tier 3.

The standard does NOT name specific products,
specific vendors, or specific technical implementation
choices. Those belong to the CISO's engineering
standard (per Exercise 03 boundary resolution).

### Section 3 — Layer dependency analysis (≤ ½ page)

Acknowledge:

- Where layer redundancy is correlated (per
  Chapter 3 §3.4.2) — i.e., layers that fail
  together.
- Where layer redundancy is independent — i.e.,
  layers that fail independently.
- Where the **bypass test** (Chapter 3 §3.4.3)
  applies — layers that could be skipped.

Programs without this analysis claim defense-in-depth
where they have one control replicated.

### Section 4 — The three Halverston-specific concerns (≤ ¼ page)

Acknowledge three specific challenges Halverston's
multi-LOB structure creates:

1. **Public-markets latency** — defense-in-depth
   adds latency the public-markets agents may
   not tolerate. How does the standard handle?
2. **Vendor LLM model swaps** — the standard's
   acceptance of a particular model identity
   becomes invalid on swap. How does the standard
   handle?
3. **Cross-LOB shared infrastructure** — some
   defence layers (audit ledger, identity service)
   are shared across LOBs; layer failure has
   cross-LOB impact. How does the standard handle?

### Section 5 — Review and update cadence (≤ ¼ page)

How the standard evolves:

- Review cadence (annual minimum).
- Trigger-based updates (new threat category, new
  regulation, incident lessons-learned).
- Who approves changes.
- How the standard interfaces with the AI risk
  register and the program's other standards.

## Constraints

- **Three pages, hard limit.**
- The standard must specify *what*, not *how*. Any
  passage that names specific products is **not**
  program-level standards work; rewrite at the
  capability level.
- Tiered application is **mandatory** — the
  standard must specify which controls are
  required at which tier, not a single
  one-size-fits-all set.
- The layer dependency analysis must address at
  least three specific dependencies.
- The Halverston-specific section must address all
  three named concerns substantively.

## Rubric

| Criterion | Weight |
|---|---|
| Scope — explicit and bounded | 10% |
| Nine layers — each with what / controls / acceptance / tier | 35% |
| Layer dependency analysis — substantive, three+ dependencies | 15% |
| Halverston-specific concerns — all three addressed | 20% |
| Review and update cadence | 10% |
| Stays at program-level (no product names) | 10% |

## Where to submit

`ai-infra-chief-ai-officer-solutions/modules/mod-107-ai-security/exercise-05-defense-in-depth-standard/SOLUTION.md`

Reference solution treats the nine layers tier-
differentiated: Tier 1 requires all nine; Tier 2
requires seven (omits tool-layer where the system is
not agentic, and may relax response-layer
requirements); Tier 3 requires five (principal,
input, output, observability, response — the
minimum that supports CAO program defensibility).

## Reading before you start

- [Chapter 3 — Defense-in-depth for AI systems](../03-defense-in-depth-for-ai.md)
  — all of it.
- `mod-106` (trust architecture) — the trust gates
  are part of multiple layers in the model.
- `mod-105` §3 (bias metrics) — output-layer
  filtering for fairness is in scope of the
  output layer.
