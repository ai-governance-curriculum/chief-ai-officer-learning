# Module 107 — Resources

Annotated reading list for AI Security and Adversarial
Defense. Standards and primary documentation first;
practitioner references treated as *range*, not template.

## Tier 1 — Authoritative attack taxonomies

| Source | Why it matters |
|---|---|
| [MITRE ATLAS](https://atlas.mitre.org/) | The structured vocabulary [Chapter 2](./02-attack-taxonomies.md) builds on; curated case-study base |
| [OWASP Top 10 for LLM Applications (2025)](https://genai.owasp.org/llm-top-10/) | The LLM-specific priority list; executive-communication framing |
| [NIST AI 100-2 E2023 — Adversarial Machine Learning](https://csrc.nist.gov/pubs/ai/100/2/e2023/final) | Classical-ML + LLM bridging taxonomy with mitigation guidance |
| [NIST AI 600-1 — Generative AI Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) | GenAI-specific risk vocabulary; complements NIST AI 100-2 |
| [AVID — AI Vulnerability Database](https://avidml.org/) | Fine-grained vulnerability catalog with reproducibility notes |
| [AI Incident Database](https://incidentdatabase.ai/) | Volunteer-curated public catalog — the calibration source for Chapter 1 |

## Tier 2 — Authoritative process and governance

| Source | Use |
|---|---|
| [NIST SP 800-39 — Risk Management](https://csrc.nist.gov/pubs/sp/800/39/final) | Defense-in-depth grounding for [Chapter 3](./03-defense-in-depth-for-ai.md) |
| [NIST SP 800-53 Rev. 5 — Security and Privacy Controls](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final) | Control catalogue; AI-specific controls increasingly cross-referenced |
| [NIST SP 800-61 Rev. 3 — Computer Security Incident Handling Guide](https://csrc.nist.gov/pubs/sp/800/61/r3/final) | Incident response grounding for [Chapter 6](./06-ai-incident-classification.md) |
| [EU AI Act — Regulation (EU) 2024/1689](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | Article 15 (cybersecurity), Articles 51–55 (GPAI with systemic risk), Article 73 (serious incident reporting) |
| [NYDFS 23 NYCRR Part 500](https://www.dfs.ny.gov/industry_guidance/cybersecurity) | §500.17 cybersecurity-event notification; recent AI-related guidance from the Superintendent |
| [GDPR — Regulation (EU) 2016/679](https://gdpr-info.eu/) | Articles 33 and 34 personal-data-breach notification |
| [SEC Reg SCI](https://www.sec.gov/rules/final/2014/34-73639.pdf) | System intrusion / disruption reporting for regulated entities |

## Tier 3 — Red-teaming references

| Source | Pattern illustrated |
|---|---|
| [EU AI Act Article 55 + GPAI Code of Practice](https://digital-strategy.ec.europa.eu/en/policies/ai-code-practice) | Red-teaming obligations for GPAI with systemic risk |
| [NIST AI 600-1 §4 (MEASURE actions)](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) | NIST red-team guidance within the GenAI Profile |
| [Microsoft AI Red Team playbook](https://learn.microsoft.com/en-us/security/ai-red-team/) | Enterprise red-team operating model |
| [Google AI Red Team / SAIF framework](https://safety.google/cybersecurity-advancements/saif/) | Hyperscaler red-team patterns |
| [Anthropic Responsible Scaling Policy](https://www.anthropic.com/news/anthropic-responsible-scaling-policy) | Capability-tier red-teaming cadence (frontier-lab pattern) |
| [HackerOne — AI safety / vulnerability bounty guidance](https://www.hackerone.com/ai) | External-researcher bounty patterns adapted for AI |

## Tier 4 — Foundational cross-references

| Source | What it gives this module |
|---|---|
| `mod-101` §4 (CAO peer-role boundaries) | Structural pattern for [Chapter 5](./05-cao-ciso-boundary.md) |
| `mod-103` §2 (risk taxonomy) | Security as a risk category |
| `mod-104` Chapter 6 (CAO × MRM boundary) | Direct structural parallel for the CAO × CISO boundary |
| `mod-106` (Trust Architecture) | The positive control surface this module operates against |
| [IIA Three Lines Model](https://www.theiia.org/en/content/position-papers/2020/the-iia-three-lines-model/) | Three-line application for CISO ownership |

## Tier 5 — Supplementary and watch-list

| Source | Use |
|---|---|
| [ENISA AI Threat Landscape (periodic reports)](https://www.enisa.europa.eu/topics/artificial-intelligence) | EU regulator-adjacent threat-landscape framing |
| [CISA AI alerts and advisories](https://www.cisa.gov/topics/artificial-intelligence) | US government AI-related security advisories |
| ISO/IEC 27090 (AI security guidance, in draft) | Watch for publication; will matter more by 2027 |
| [FS-ISAC (financial sector) AI working groups](https://www.fsisac.com/) | Member-only sector incident sharing |
| [H-ISAC (health sector) AI working groups](https://h-isac.org/) | Member-only sector incident sharing for healthcare |

## Tier 6 — Practitioner references (range, not template)

Treated per the module's source policy: these are
*practitioner patterns* that illustrate how specific
organisations have implemented the standards above. None
is the canonical answer.

| Source | Pattern illustrated |
|---|---|
| [OpenAI System Cards and preparedness publications](https://openai.com/safety) | Vendor-published pre-deployment risk evaluations |
| [Cloudflare AI Gateway](https://www.cloudflare.com/products/ai-gateway/) | Gateway-mediated input / output filtering pattern |
| [Lakera Guard](https://www.lakera.ai/) | Prompt-injection detection as a product |
| VeriSwarm Guard | Scanning / filtering reference pattern |
| [NVIDIA NeMo Guardrails](https://developer.nvidia.com/nemo/guardrails) | Programmable guardrail pattern around LLMs |

## Where to go next

- **`mod-108` — Audit Ledgers and Evidence.** Tamper-
  evident logging complements incident classification;
  the signed events feed the audit trail.
- **`mod-109` — Compliance Operations.** Cross-walks
  between security incidents and regulatory obligations.
- **`mod-110` — Incident Response.** Operational treatment
  of incident response across both security and
  AI-program dimensions.
- **`ai-infra-security-learning`** (paired curriculum) —
  engineering-depth treatment of the same surface.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
