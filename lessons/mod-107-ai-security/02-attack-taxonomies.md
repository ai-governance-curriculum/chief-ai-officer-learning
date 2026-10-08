# Chapter 2 — Attack Taxonomies: ATLAS, OWASP, NIST

## Why this chapter exists

Three taxonomies dominate AI security work in 2026. They
are complementary, not competitive. Working programs use
elements of all three. A CAO who treats them as
interchangeable — or picks one and flattens the others
into it — produces a threat model that cannot speak to the
regulator the program will actually face, or to the
engineers who will actually build the defences.

The chapter's payoff is twofold. First, you can read each
taxonomy for what it is good at. Second, you can compose
them without producing a mega-checklist that is used
once and then set aside. Exercise 01 uses MITRE ATLAS as
the primary vocabulary and asks you to supplement it with
OWASP and NIST 100-2 where each adds precision ATLAS
misses — this chapter is the prerequisite for that
exercise.

## 2.1 MITRE ATLAS

**MITRE ATLAS** — *Adversarial Threat Landscape for
Artificial Intelligence Systems* — is MITRE's ATT&CK-style
taxonomy adapted for AI systems. Tactics plus techniques,
mapped to AI-specific kill chains, with a curated case-
study base.

### 2.1.1 Structure

ATLAS tactics in the 2024–2025 revision include:

- Reconnaissance (`AML.TA0001`)
- Resource development (`AML.TA0002`)
- Initial access (`AML.TA0003`)
- ML model access (`AML.TA0004`)
- Execution (`AML.TA0005`)
- Persistence (`AML.TA0006`)
- Privilege escalation (`AML.TA0012`)
- Defense evasion (`AML.TA0007`)
- Credential access
- Discovery (`AML.TA0008`)
- Collection (`AML.TA0009`)
- ML attack staging (`AML.TA0010`)
- Exfiltration (`AML.TA0011`)
- Impact (`AML.TA0013`)

Each tactic has specific techniques (e.g. under *ML model
access*: `AML.T0010` ML supply-chain compromise;
`AML.T0024` query-based model extraction; `AML.T0044`
physical environment access).

### 2.1.2 Strengths

- Structured vocabulary that maps onto existing MITRE
  ATT&CK that security teams already know.
- Concrete techniques rather than high-level principles,
  so the vocabulary is operationally usable rather than
  aspirational.
- Connected to a curated case-study base — each technique
  has worked examples drawn from public incidents.
- Updates on a reasonable cadence, so it stays close to
  the live threat landscape.

### 2.1.3 Limitations

- The taxonomy is large; used as a checklist it produces
  too many items for program-level action.
- Some techniques are technically interesting but rarely
  material to enterprise deployments — the catalog is
  built for comprehensiveness, not prioritisation.
- The tactic structure assumes a kill-chain mental model
  that is a stronger fit for targeted attacks than for
  opportunistic prompt-injection noise.

### 2.1.4 How the CAO uses it

ATLAS is the right choice as a structured *vocabulary*
for threat-modelling and incident-classification. Not as a
checklist to tick off, but as a shared language that
makes conversations with the CISO's engineers legible on
both sides.

## 2.2 OWASP LLM Top 10

**OWASP Top 10 for Large Language Model Applications** —
the 2025 revision — is a deliberately short list of the
most prevalent and impactful LLM-specific risks.

### 2.2.1 Structure

The 2025 OWASP LLM Top 10 categories:

| ID | Category |
|---|---|
| LLM01 | Prompt injection |
| LLM02 | Sensitive information disclosure |
| LLM03 | Supply chain |
| LLM04 | Data and model poisoning |
| LLM05 | Improper output handling |
| LLM06 | Excessive agency |
| LLM07 | System prompt leakage |
| LLM08 | Vector and embedding weaknesses |
| LLM09 | Misinformation |
| LLM10 | Unbounded consumption |

### 2.2.2 Strengths

- Short enough to remember and to communicate to
  non-security executives without a glossary.
- Maps closely to [Chapter 1 §1.2](./01-ai-threat-landscape-real-vs-hype.md)
  — the categories with documented production incidents.
- OWASP's broader credibility in web-security transfers;
  Board and audit audiences accept OWASP as a reference
  authority.
- Each category comes with example attack scenarios and
  defensive guidance, so it is immediately usable in
  policy drafting.

### 2.2.3 Limitations

- LLM-specific; does not directly cover classical-ML
  attack categories (adversarial inputs to classifiers,
  model stealing against regression models, etc.).
- The ten-item ceiling forces aggregation that can hide
  structure — "excessive agency" bundles several distinct
  failure modes.
- OWASP's refresh cadence (roughly every 12–18 months) is
  slower than the threat landscape in some sub-categories.

### 2.2.4 How the CAO uses it

OWASP is the right choice as the *priority list* for
LLM-specific defence, and as the framing for executive
communication. "We defend against the OWASP LLM Top 10"
is a sentence that lands in a Board setting. "We defend
against ATLAS techniques AML.T0051 through AML.T0054" is
a sentence that lands only with the engineers.

## 2.3 NIST AI 100-2 E2023

**NIST AI 100-2 E2023** — *Adversarial Machine Learning: A
Taxonomy and Terminology of Attacks and Mitigations* —
provides a taxonomy for both classical-ML and LLM attacks
with mitigation recommendations.

### 2.3.1 Structure

NIST 100-2 is structured by three orthogonal dimensions:

- **Attack stage** — training-time, deployment-time, or
  post-deployment.
- **Attack goal** — availability, integrity,
  confidentiality, or abuse.
- **Adversary knowledge** — white-box, grey-box, or
  black-box.

Any specific attack maps to a *coordinate* in this cube:
e.g. training-time + integrity + white-box = classical
backdoor poisoning; deployment-time + confidentiality +
black-box = query-based model extraction.

### 2.3.2 Strengths

- Covers both classical ML and LLMs in one framework,
  which neither ATLAS nor OWASP does cleanly.
- Includes mitigation recommendations as part of the
  text, not as a separate catalog.
- Government-authored — useful for regulator-facing
  context, particularly US agency work and EU AI Act
  compliance narratives.
- The orthogonal-axis structure forces attention to
  attributes a flat list does not.

### 2.3.3 Limitations

- Comparatively academic in tone — the exercises in this
  module should not expect executives to read it in the
  original.
- Less practitioner traction than ATLAS or OWASP, so the
  engineering team may not already know the taxonomy and
  will need onboarding.
- Updates are infrequent; expect the 2023 edition to
  remain current longer than ATLAS or OWASP.

### 2.3.4 How the CAO uses it

NIST 100-2 is the *bridging framework* when the program
has both classical-ML and LLM systems — which is the
common case in financial services (fraud + credit
classical ML plus LLM customer agents) and in healthcare
(image-classification classical ML plus LLM clinical
scribes).

It is also the framework to reach for when
regulator-facing documentation needs a government source
for taxonomy framing.

## 2.4 Composing the three

A working program does not pick one. The composition
pattern that works:

| Taxonomy | Program role |
|---|---|
| OWASP LLM Top 10 | Priority list for LLM-specific defence; executive and Board communication framing |
| MITRE ATLAS | Threat-modelling vocabulary and incident-classification structure; engineering-team language |
| NIST AI 100-2 E2023 | Bridging framework for programs with both classical ML and LLMs; regulator-facing documentation |

The program's threat-model artifacts cite *all three*
where relevant. Exercise 01 uses ATLAS as the primary
framing; the reference solution shows where OWASP and
NIST 100-2 supplement. The exercise rubric penalises
collapsing to a single taxonomy — not because taxonomy
pluralism is virtuous for its own sake, but because each
taxonomy is weaker alone than in combination.

## 2.5 Where none of the three is enough

Three gaps across all three taxonomies that a working
program names:

- **Agentic composition.** All three taxonomies treat
  AI-system attacks largely at the model layer. Agentic
  systems add attacks on *tool composition* — malicious
  tool chains, prompt-leaked tool metadata, trust-gate
  bypass (`mod-106` Chapter 5). ATLAS has begun
  addressing this with LLM-prompt-injection techniques,
  but the agent-specific composition surface is
  under-covered.
- **Supply-chain depth.** Each taxonomy names supply-
  chain compromise as a category. None of them specifies
  the depth: foundation model → fine-tune → adapter →
  prompt library → agent framework → tool catalog. A
  real supply-chain threat model walks the whole chain.
- **Human-process attacks.** None of the taxonomies
  treats the *human processes* around the AI system — the
  validation process, the red-team process, the incident
  response process — as attack surfaces. In practice,
  attackers compromise processes as readily as code.

Programs that name these gaps explicitly in their threat
model do a better job than programs that let the taxonomy
structure define the threat universe.

## 2.6 Supplementary taxonomies worth tracking

Not the primary three, but worth tracking:

- **NIST AI 600-1 (Generative AI Profile).** The NIST AI
  RMF Generative-AI companion. Risk-category framing
  rather than attack-taxonomy framing. Overlaps with
  OWASP on sensitive-information disclosure and
  misinformation.
- **ENISA AI Threat Landscape reports.** The European
  Union Agency for Cybersecurity publishes periodic AI
  threat landscape reports. More regulator-adjacent than
  practitioner-focused.
- **AVID (AI Vulnerability Database).** Fine-grained
  vulnerability catalog with reproducibility notes. Good
  for red-team scenario construction (Chapter 4).
- **ISO/IEC 27090 (AI security guidance, in draft).**
  Will matter more by 2027. Watch for the final
  publication.

## 2.7 What the CAO reads for in a program's taxonomy choice

Four questions:

1. **Does the threat model cite more than one taxonomy?**
   A single-taxonomy threat model is almost always
   under-specified for the firm's actual AI mix.
2. **Does it name the OWASP categories as a priority
   list, not just as an enumeration?** OWASP without
   prioritisation collapses to a checklist.
3. **Does it use ATLAS technique IDs for engineering-
   facing artifacts?** A threat model that refers to
   techniques by English-language description forces the
   engineering team to re-translate every time.
4. **Does it reach for NIST 100-2 when both classical ML
   and LLMs are in scope?** A classical-ML-plus-LLM
   program using only OWASP has a gap in its taxonomy
   coverage.

A CAO who can ask these four questions and name where the
program's threat model is weak has done the CAO job on
this chapter.

## Summary

- Three dominant taxonomies in 2026: MITRE ATLAS, OWASP
  LLM Top 10, NIST AI 100-2 E2023. They are
  complementary, not competitive.
- ATLAS gives vocabulary and technique IDs. OWASP gives a
  short, memorable priority list. NIST 100-2 bridges
  classical-ML and LLM attack categories.
- The composition pattern: OWASP for executive priority
  and Board framing; ATLAS for engineering vocabulary;
  NIST 100-2 for cross-ML programs and regulator-facing
  documentation.
- Three gaps across all three: agentic composition,
  supply-chain depth, human-process attacks. Programs
  should name these gaps rather than let taxonomy
  structure define their threat universe.
- The CAO's test on a program's threat model: multiple
  taxonomies cited, OWASP used as a priority list, ATLAS
  used by technique ID, NIST 100-2 reached for when the
  system mix calls for it.
