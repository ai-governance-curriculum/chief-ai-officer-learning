# Module 106 — Trust Architecture

> Module 106 of the Chief AI Officer track. Trust
> architecture — the technical and operational
> machinery by which an organisation decides what an
> AI agent is permitted to do, on whose behalf, and
> with what evidence. The discipline lives at the
> intersection of identity, capability scoping, and
> runtime enforcement.

## What you will leave with

After working through this module you should be able to:

1. Define "trust" for AI systems in operational terms,
   not metaphorical ones.
2. Apply NIST SP 800-207 (Zero Trust Architecture) to
   agentic AI without forcing the source framework to
   carry assumptions it was not designed for.
3. Distinguish deterministic from heuristic trust
   scoring and choose the approach that fits the
   stakes.
4. Author an agent identity and capability manifest
   (signed, verifiable, scoped) using current
   standards (W3C Verifiable Credentials, JWT/JOSE,
   OAuth 2.1).
5. Design a trust-gate request pipeline that sits
   between AI agents and the resources they touch.
6. Make enterprise build-vs-buy-vs-partner decisions
   for trust architecture at portfolio scope with a
   structured framework.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md) through
[`mod-105`](../mod-105-responsible-ai-and-ethics/README.md).

Particularly relevant:

- mod-103 §2 (taxonomy) — security risk + transparency
  risk as categories.
- mod-104 §3 (validation patterns) — how trust scoring
  validates.
- mod-105 §4 (transparency by audience) — what trust
  decisions owe to whom.
- mod-107 (AI Security) follows directly; trust
  architecture is the *positive* control surface that
  security operates within.

## Module layout

```
mod-106-trust-architecture/
├── README.md                                                you are here — chapter index
├── 01-what-trust-means-for-ai-systems.md                    the operational definition
├── 02-zero-trust-adapted-for-ai-agents.md                   NIST SP 800-207, adapted
├── 03-identity-and-capability-scoping.md                    composite identity, signed manifests
├── 04-trust-scoring-deterministic-vs-heuristic.md           the scoring posture + four axes
├── 05-trust-gates-in-the-request-path.md                    placement, pipeline, latency, step-up
├── 06-build-buy-or-partner.md                               enterprise decision framework
├── exercises/                                               five exercises (~16 hours total)
├── quiz.md                                                  20 questions covering the chapters
└── resources.md                                             annotated reading list, standards-first
```

## Chapters at a glance

| # | Title | Objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [What "trust" means for AI systems](./01-what-trust-means-for-ai-systems.md) | Objective 1 | NIST AI RMF; mod-101 §1 (neighbors of governance); operational-definition discipline |
| 2 | [Zero-trust adapted for AI agents](./02-zero-trust-adapted-for-ai-agents.md) | Objective 2 | NIST SP 800-207; CISA Zero Trust Maturity Model |
| 3 | [Identity and capability scoping](./03-identity-and-capability-scoping.md) | Objective 4 | W3C Verifiable Credentials 2.0; RFC 7519 (JWT); RFC 9068 (JWT Profile for OAuth); OAuth 2.1 |
| 4 | [Trust scoring — deterministic vs heuristic](./04-trust-scoring-deterministic-vs-heuristic.md) | Objective 3 | NIST AI RMF MEASURE-2.7; OpenTelemetry GenAI semconv; practitioner four-axis patterns |
| 5 | [Trust gates in the request path](./05-trust-gates-in-the-request-path.md) | Objective 5 | NIST SP 800-207 policy-decision/policy-enforcement model; practitioner placement patterns |
| 6 | [Build, buy, or partner](./06-build-buy-or-partner.md) | Objective 6 | mod-101 §5 (operating models); vendor-landscape survey (2026) |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Map trust boundaries using NIST 800-207](./exercises/exercise-01-map-trust-boundaries.md) | 3 | Applied | Annotated boundary diagram + memo |
| 02 | [Design a 4-axis trust score with explicit math](./exercises/exercise-02-design-four-axis-trust-score.md) | 4 | Synthesis | Scoring spec with weights, thresholds, math |
| 03 | [Author an agent identity + capability manifest](./exercises/exercise-03-author-agent-identity-manifest.md) | 3 | Applied | Signed manifest + verifier code-sketch |
| 04 | [Design a trust-gate request pipeline](./exercises/exercise-04-design-trust-gate-pipeline.md) | 3 | Applied | Pipeline design + tradeoff analysis |
| 05 | [Build-vs-buy-vs-partner decision](./exercises/exercise-05-build-vs-buy-trust-architecture.md) | 3 | Synthesis | Decision matrix + recommendation memo |

## A note on practitioner references

This module is the one most often discussing specific
vendor or open-source implementations. **Source
policy applies in full**: VeriSwarm Gate / Passport /
Vault, Cloudflare AI Gateway, IBM watsonx.governance,
Anthropic agent attestation patterns, and roll-your-own
with NIST + W3C standards are all *practitioner
patterns*. None is the canonical answer. The chapters
draw on several and the exercises require you to
compare them without picking one as the default.

If a passage of this module reads like it is
recommending a vendor, file an issue.

## How this module fits

mod-101 through mod-105 built the governance,
regulatory, risk, model-risk, and ethics disciplines.
mod-106 is where the discipline becomes operational
at the runtime level — the point where an agent
tries to do something and the architecture decides.
Downstream modules build on this:

- **mod-107 (AI Security & Adversarial Defense)** —
  the adversarial perspective. Trust architecture
  is the positive control surface; security defends
  it.
- **mod-108 (Audit Ledgers & Evidence)** — tamper-
  evident logging is the audit complement to trust
  architecture; the signed events this module emits
  are what the ledger stores.
- **mod-109 (Compliance Operations)** — trust
  architecture is one of the most-asked-for evidence
  surfaces in regulator engagement.
- **mod-111 (Board Reporting)** — the trust-gate
  posture rolls up into the board risk pack as a
  specific tracked indicator.

## Paired solutions repo

[`chief-ai-officer-solutions / modules/mod-106-trust-architecture`](https://github.com/ai-governance-curriculum/chief-ai-officer-solutions/tree/main/modules/mod-106-trust-architecture)

Same conventions as mod-101 through mod-105 — worked
answers, not the answer.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
