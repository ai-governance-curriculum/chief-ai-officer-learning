# Chapter 1 — The AI Threat Landscape: Real vs Hype

## Why this chapter exists

The AI security literature in 2024–2026 has produced more
*theoretical* threat categories than any of them have
produced documented incidents. A working CAO distinguishes
the threats that have produced reproducible production harm
from the threats that remain academic curiosities, and
weights the program's attention accordingly.

This is not a claim that theoretical threats are
unimportant. Many will become operational. The claim is
that a program organising its defences around every
theoretical threat will produce defences that are *broad
and shallow*, while real incidents keep happening in the
same handful of categories.

The CAO does not own AI security — the CISO does
([Chapter 5](./05-cao-ciso-boundary.md)) — but the CAO sets
the program-level threat-model expectations the CISO
operates within, and the CAO's reporting to the Board and
regulators is informed by the threat landscape. The
discipline of this chapter is informed prioritisation.

## 1.1 Where to look for the evidence base

A threat is *real* when the public incident base contains
reproducible examples of harm. The sources that carry the
evidence base in 2026:

- **AI Incident Database (incidentdatabase.ai).**
  Volunteer-curated public catalog of AI-related incidents.
  Imperfect, but the broadest single source.
- **MITRE ATLAS case studies.** Curated vignettes attached
  to specific ATLAS techniques. Smaller set than the AVID
  or Incident Database but with high-signal technique
  mapping.
- **AVID (AI Vulnerability Database).** Technique and
  taxonomy mapping with reproducibility notes.
- **CISA / NCSC / sector-ISAC advisories.** Government and
  sector incident response bodies have begun publishing
  AI-related advisories; the signal is high when it
  appears.
- **Vendor post-mortems.** OpenAI, Anthropic, Google, and
  Microsoft publish incident write-ups for issues
  affecting their own services. Narrow but detailed.
- **Peer-sector incident sharing.** Financial services
  firms share through FS-ISAC; health through H-ISAC;
  these are not public but are available to member
  institutions.

A CAO organising the program's threat model from the
*academic literature alone* produces an uncalibrated model.
The incident base is the calibration.

## 1.2 The categories with documented production incidents

The threat categories where production incidents recur
publicly, as of early 2026:

1. **Prompt injection (direct and indirect).** Users or
   upstream content sources cause an LLM-based system to
   produce outputs outside its intended behaviour. Public
   incident base is large and growing. Treated by OWASP
   LLM Top 10 as LLM01 and by MITRE ATLAS under multiple
   techniques (`AML.T0051`, `AML.T0054`, and the
   LLM-prompt-injection family).
2. **Data exfiltration through model output.** Models
   trained on or with access to sensitive data produce
   that data in outputs. OWASP's LLM02 (sensitive
   information disclosure) and LLM07 (system prompt
   leakage) sit here.
3. **Adversarial inputs to classification models.** Image
   classifiers, fraud detectors, content moderators can
   be evaded by inputs crafted to exploit specific
   decision boundaries. NIST AI 100-2 E2023's "evasion"
   category.
4. **Training-data poisoning of curated datasets.** Open
   dataset contributors have repeatedly introduced data
   designed to produce specific model behaviours. The
   `nightshade`-style and the deliberately-mislabelled
   contribution patterns are the two dominant forms.
5. **Supply-chain compromise.** Compromised model weights,
   compromised inference container images, compromised
   vendor-hosted services. The classical software supply-
   chain problem applied to model artifacts. `AML.T0010`
   in ATLAS; LLM03 in OWASP.
6. **Tool-call exploitation in agentic systems.** Agents
   that call tools can be manipulated to invoke tools the
   principal did not authorise — especially when prompt
   injection meets agentic tool calls. OWASP's LLM06
   (excessive agency).
7. **Denial of service through expensive inputs.** Long
   inputs, recursive prompts, or computationally-expensive
   operations cause resource exhaustion. OWASP's LLM10
   (unbounded consumption).

These seven account for the majority of incidents the
CISO community has documented in open sources through
2025. Defences against them are the right priority. A
program whose threat model does not include all seven has
a gap you can name specifically.

## 1.3 The categories that remain mostly theoretical

The threat categories that appear in literature with
limited or no documented production exploitation at
program-material scale:

- **Membership inference attacks** (determining whether a
  specific record was in training data). Possible in some
  settings; weaponisation at production scale is rare and
  the economics usually do not favour the attacker.
- **Model stealing via API queries** (extracting a model
  by querying it). Possible against unprotected APIs; a
  defended API with rate limiting and output-pattern
  monitoring makes it uneconomic for anything but the
  smallest models.
- **Reward hacking in production.** Discussed in alignment
  literature; most production AI systems do not have the
  reward-hacking topology (a learned objective being
  optimised online against externally-visible metrics)
  that makes this exploit interesting.
- **Catastrophic misalignment at deployment scale.** An
  active research area with real safety-relevance for
  frontier labs; not a present operational threat for
  typical non-frontier enterprise deployments.
- **Steganographic covert channels between agents.** A
  2024–2025 research topic. No documented production
  exploitation at material scale.

Programs should be *aware* of these — research moves;
what is theoretical in 2026 may be live in 2028. They
should not be the priority for the defences that get
built in 2026.

## 1.4 Why "mostly theoretical" is not "ignore"

The temptation after reading §1.3 is to drop theoretical
categories from the program's threat model entirely. That
is the wrong lesson. The right lesson:

- **Watch the research.** Assign someone — in the CISO's
  org or shared with the CAO function — to track the
  literature on each theoretical category. When the
  category produces its first reproducible production
  incident, the program's weighting has to shift.
- **Design out, where cheap.** Some theoretical threats
  have cheap preventive controls that make sense to adopt
  even before the first incident. API rate limiting is a
  model-stealing control that is also just good API
  hygiene. Training-data provenance is a poisoning
  control that is also just good MRM (`mod-104` §5).
- **Do not advertise the gap.** A program that publishes
  "we are not defending against model stealing" invites
  the first incident. Internal awareness is not the same
  as external disclosure of weakness.

## 1.5 The misallocation pattern

The most common AI security program misallocation:
program effort spent on theoretical threats while the
seven documented categories continue producing
incidents. Symptoms:

- The program's threat model is dominated by
  academic-literature categories.
- Detection coverage is broad but shallow — many
  signals, low fidelity on any single threat.
- Recent incidents at peer organisations are not
  reflected in the program's threat model.
- Red-team exercises target exotic scenarios while
  known-exploitable paths go untested.
- Board reporting features new-and-interesting threats
  rather than the recurring ones.

A working CAO ensures the program's attention is
weighted toward what is happening, not toward what could
happen. The test is simple: for every category in the
program's threat model, can someone name a documented
incident at a peer organisation that it defends against?
If not, that category needs a defensible rationale.

## 1.6 Sector adjustment

The seven real categories are the base rate. Specific
sectors have additional priorities:

| Sector | Additional priority category | Why |
|---|---|---|
| Financial services | Adversarial inputs to fraud / AML models | Direct financial incentive for attackers |
| Healthcare | Training-data provenance of medical datasets | Patient-safety consequences of poisoned data |
| Public sector | Prompt-injection against citizen-facing LLMs | Combination of adversarial users + public-trust blast radius |
| E-commerce / retail | Tool-call exploitation in checkout agents | Agentic systems with direct financial actuation |
| Media / platforms | Content-moderator evasion | Scale of adversarial content at platform volume |

Sector adjustment is not a sixth or seventh category — it
is a reweighting of the seven. A financial-services CAO's
threat model should have adversarial inputs weighted higher
than a media-platform CAO's threat model does. Nothing
about the seven categories is sector-neutral; the program
has to do the sector-specific weighting.

## 1.7 Why this discipline matters for the CAO

A CAO who treats every theoretical threat as a priority
will under-resource the actual defences. A CAO who dismisses
theoretical threats will be caught off-guard when one
operationalises. The discipline is informed
prioritisation, held explicit, reviewed on a cadence.

What the CAO reads for in the program's threat model:

1. **Does it name the seven real categories?** Any missing
   category is a gap that will show up in the first
   serious incident of that type.
2. **Does it name sector-specific weighting?** A
   generic threat model that could apply to any sector is
   under-specified for the firm.
3. **Does it name the theoretical categories as watched,
   not ignored?** Awareness without priority. The
   program should name the review cadence (quarterly,
   annually) at which it re-weights.
4. **Does it cite the evidence base?** A threat model
   whose categories are not traceable to real incidents
   (or named gaps) is not calibrated.

Exercise 01 builds the threat model directly. This chapter
is the prioritisation discipline that exercise applies.

## Summary

- Live threats in 2026 differ from theoretical threats.
  The program should weight to what has produced
  reproducible incidents, not to what could.
- The seven real categories: prompt injection, data
  exfiltration through output, adversarial inputs to
  classifiers, training-data poisoning, supply-chain
  compromise, tool-call exploitation, denial of service
  through expensive inputs.
- The mostly-theoretical categories (membership
  inference, model stealing, reward hacking, catastrophic
  misalignment, covert channels) are watched, not
  ignored; cheap preventive controls go in regardless.
- The misallocation pattern — effort on theory while
  recurring real incidents go undefended — is the
  dominant program failure mode. The CAO's job is
  informed re-prioritisation on a cadence.
- Sector-specific weighting of the seven is required.
  Generic threat models under-serve the firm.
