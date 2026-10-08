# Module 105 — Resources

Annotated reading list for Responsible AI and Ethics.
Source-first — primary documents before practitioner
commentary.

## Tier 1 — Authoritative principle documents (read these)

| Source | Why it matters |
|---|---|
| [OECD AI Principles (2024 update)](https://oecd.ai/en/ai-principles) | The closest thing to international consensus; upstream of NIST + EU; Chapter 2 anchor |
| [UNESCO Recommendation on the Ethics of AI (2021)](https://www.unesco.org/en/artificial-intelligence/recommendation-ethics) | Broad international ethics statement; 193-country adoption |
| [IEEE 7000 series](https://sagroups.ieee.org/global-initiative/) | Standards-grade; IEEE 7000 (process), 7001 (transparency), 7002 (data privacy), 7003 (algorithmic bias) most operational |
| [EU HLEG Ethics Guidelines for Trustworthy AI (2019)](https://digital-strategy.ec.europa.eu/en/library/ethics-guidelines-trustworthy-ai) | Upstream of EU AI Act; the seven key requirements |
| [NIST AI RMF 1.0 (2023)](https://www.nist.gov/itl/ai-risk-management-framework) | Preamble names the values the framework operationalizes |

## Tier 1 — Authoritative technical literature

| Source | Why it matters |
|---|---|
| Chouldechova (2017), *Fair Prediction with Disparate Impact* — [arXiv:1703.00056](https://arxiv.org/abs/1703.00056) | The impossibility result — required reading for Chapter 3 §2 |
| Kleinberg, Mullainathan, Raghavan (2016), *Inherent Trade-offs in the Fair Determination of Risk Scores* — [arXiv:1609.05807](https://arxiv.org/abs/1609.05807) | The other impossibility result; same conclusion via different framing |
| Selbst, Boyd, Friedler, Venkatasubramanian, Vertesi (2019), *Fairness and Abstraction in Sociotechnical Systems* — [ACM FAT* 2019](https://dl.acm.org/doi/10.1145/3287560.3287598) | Why algorithmic fairness alone is insufficient — Chapter 3 §4 |
| Mitchell et al. (2019), *Model Cards for Model Reporting* — [arXiv:1810.03993](https://arxiv.org/abs/1810.03993) | Foundational artifact for transparency to multiple audiences — Chapter 4 §7 |
| Gebru et al. (2018), *Datasheets for Datasets* — [arXiv:1803.09010](https://arxiv.org/abs/1803.09010) | Data-side transparency complement to Model Cards |

## Tier 2 — Sector-specific regulation

| Source | Sector | Use |
|---|---|---|
| [CFPB Circular 2022-03](https://www.consumerfinance.gov/compliance/circulars/circular-2022-03-adverse-action-notification-requirements-in-connection-with-credit-decisions-based-on-complex-algorithms/) | Financial services | Explainability / adverse-action; the "black-box defense" rejection — Chapter 4 §5 |
| [EU AI Act (Regulation 2024/1689)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | Horizontal | Arts 11, 13, 14, 53, 55, 56, 86 cited throughout Chapters 4-6 |
| [GDPR Art. 22](https://gdpr-info.eu/art-22-gdpr/) | Horizontal (EU) | Automated-decision rights; Chapter 5 §3 |
| [CO Reg 10-1-1](https://www.sos.state.co.us/CCR/GenerateRulePdf.do?ruleVersionId=11060) | Insurance | Algorithmic discrimination testing — Chapter 3 §3 |
| [Colorado AI Act (SB 24-205)](https://leg.colorado.gov/bills/sb24-205) | Horizontal (CO, 2026) | Consumer appeal + developer disclosure — Chapter 5 §3 |
| [FDA Software as a Medical Device (SaMD) guidance](https://www.fda.gov/medical-devices/software-medical-device-samd/) | Healthcare | Patient-affected transparency under medical-device frameworks |
| [NYC Local Law 144 (DCWP rules)](https://www.nyc.gov/site/dca/about/automated-employment-decision-tools.page) | HR | Bias audit + candidate notice — Chapter 3 §3 |
| [EEOC "Four-Fifths Rule" guidance (Uniform Guidelines on Employee Selection Procedures, 29 CFR 1607.4(D))](https://www.ecfr.gov/current/title-29/subtitle-B/chapter-XIV/part-1607) | HR | Disparate-impact threshold reference — Chapter 3 §3 |

## Tier 2 — Voluntary codes (Chapter 6 anchors)

| Source | Category | Why it matters |
|---|---|---|
| [G7 Hiroshima Process International Code of Conduct for Organisations Developing Advanced AI Systems (October 2023)](https://www.mofa.go.jp/files/100573473.pdf) | Pre-regulatory anchoring | Eleven voluntary actions; OECD-hosted reporting framework |
| [G7 Hiroshima Process International Guiding Principles for Organisations Developing Advanced AI Systems](https://www.mofa.go.jp/files/100573471.pdf) | Pre-regulatory anchoring | Companion principles document to the Code of Conduct |
| [OECD Reporting Framework for the Hiroshima AI Process Code of Conduct](https://oecd.ai/en/hcoc) | Reporting | Where signatory reports are hosted |
| [EU AI Office — General-Purpose AI Code of Practice](https://digital-strategy.ec.europa.eu/en/policies/ai-code-practice) | Statutory-compliance scaffolding | Operational implementation of EU AI Act Art. 53/55/56 obligations for GPAI providers |
| [MLCommons AI Safety Working Group / AILuminate benchmark](https://mlcommons.org/working-groups/ai-safety/ai-safety/) | Industry-coordination scaffolding | v1.0 safety benchmark for text-to-text LLMs across 12 hazard categories |
| [Partnership on AI](https://partnershiponai.org/) | Industry-coordination scaffolding | Multi-stakeholder non-profit; frameworks on synthetic media, model documentation, safety-critical AI |
| [White House Voluntary AI Commitments (July 2023)](https://www.whitehouse.gov/briefing-room/statements-releases/2023/07/21/fact-sheet-biden-harris-administration-secures-voluntary-commitments-from-leading-artificial-intelligence-companies-to-manage-the-risks-posed-by-ai/) | Pre-regulatory anchoring (US) | Early commitments by major foundation-model developers |
| [Seoul Frontier AI Safety Commitments (May 2024)](https://www.gov.uk/government/publications/frontier-ai-safety-commitments-ai-seoul-summit-2024) | Frontier-safety commitments | 16 companies committed to safety-framework publication and risk thresholds |

<!-- needs-research: confirm the most current public URLs and version anchors for the EU AI Office GPAI Code of Practice and the OECD-hosted Hiroshima reporting portal as of 2026. -->

## Tier 3 — Foundational

| Source | What it gives this module |
|---|---|
| [Asilomar AI Principles (2017)](https://futureoflife.org/open-letter/ai-principles/) | Frontier-AI focused; useful for Chapter 1 discussion of safety vs. ethics |
| Friedman & Hendry (2019), *Value Sensitive Design: Shaping Technology with Moral Imagination* (MIT Press) | Methodological grounding for Chapter 7 §2 (ethics in standards) |
| Barocas, Hardt, Narayanan (2023), *Fairness and Machine Learning: Limitations and Opportunities* — [fairmlbook.org](https://fairmlbook.org/) | Textbook treatment of Chapter 3 topics |
| mod-103 §2 (AI risk taxonomy) | Bias, transparency, privacy as risk categories |
| mod-104 §3 (validation patterns) | Subgroup validation as operational form of fairness |

## Tier 4 — Practitioner references (pattern, not template)

| Source | Pattern |
|---|---|
| [Microsoft Responsible AI Standard v2 (2022)](https://www.microsoft.com/en-us/ai/responsible-ai) | One well-developed operationalization; hub-and-spoke pattern |
| [Google AI Principles](https://ai.google/responsibility/principles/) | Hyperscaler principles document; pattern reference only |
| [Anthropic Responsible Scaling Policy](https://www.anthropic.com/news/anthropic-responsible-scaling-policy) | Frontier-AI capability tiers (adjacent to ethics, not it) |
| [IBM Trustworthy AI documentation](https://www.ibm.com/topics/trustworthy-ai) | Enterprise-vendor pattern reference |
| Published Model Cards (Hugging Face library) | Format reference for audience-tailored transparency |
| [NIST AI RMF Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook) | Suggested implementations for AI RMF functions |

## Tier 4 — Case material

| Source | Why it matters |
|---|---|
| Angwin, Larson, Mattu, Kirchner (2016), *Machine Bias* — ProPublica investigation of COMPAS | The canonical case behind Chapter 3 §2.1 (fairness-definition disagreement) |
| Dieterich, Mendoza, Brennan (2016), Northpointe response to ProPublica | The other side of the COMPAS case; shows the predictive-parity framing |
| [Obermeyer et al. (2019), *Dissecting racial bias in an algorithm used to manage the health of populations*](https://www.science.org/doi/10.1126/science.aax2342) | Healthcare bias case study; proxy-attribute-driven disparity |

## Where to go next

- **mod-106 — Trust Architecture.** Operationalises trust
  gates and identity for AI systems; builds on Chapter 5
  contestability design properties.
- **mod-107 — AI Security & Adversarial Defense.** Where
  fairness and security overlap.
- **mod-108 — Audit Ledgers & Evidence.** The evidence
  machinery behind ethics-function reporting.
- **mod-111 — Board Reporting & Risk Appetite.** Where
  ethics-function performance surfaces to executive
  accountability.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
