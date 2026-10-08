# Module 109 — Resources

Annotated reading list for Compliance Operations.
Standards and primary sources first; practitioner
tools last.

## Tier 1 — Authoritative (standards and regulations)

| Source | Why it matters |
|---|---|
| [ISO/IEC 42001:2023 — AI management systems](https://www.iso.org/standard/81230.html) | The AIMS standard. Clauses 4–10 and Annex A anchor the control catalog Chapter 5 builds on. |
| [ISO/IEC 42005:2025 — AI system impact assessment](https://www.iso.org/standard/44545.html) | Companion standard specifying impact-assessment process; cross-referenced by Annex A.5. |
| [NIST AI Risk Management Framework 1.0 + Playbook](https://www.nist.gov/itl/ai-risk-management-framework) | Crosswalk source for Chapter 2 §2.3 and the operating-loop reference for continuous practice. |
| [EU AI Act (Regulation 2024/1689) — Art. 17 Quality Management System](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | Operational obligation underlying continuous practice; Art. 72 (post-market monitoring) and Art. 73 (serious incidents) are directly operated against. |
| [ISO/IEC 23894:2023 — AI risk management guidance](https://www.iso.org/standard/77304.html) | Risk-management guidance that complements Annex A and ISO 31000. |
| [ISO/IEC 38507:2022 — Governance implications of the use of AI by organizations](https://www.iso.org/standard/56641.html) | Governance-side reference that frames the Chapter 6 peer-boundary pattern. |

## Tier 2 — Authoritative, sector-specific

| Source | Sector | Use |
|---|---|---|
| [OCC/FRB SR 11-7 — Guidance on Model Risk Management](https://www.federalreserve.gov/supervisionreg/srletters/sr1107.htm) | Financial services | Model-risk control overlay; see also `mod-104` |
| [FRB SR 22-6 — Supervisory Guidance on Model Risk Management (updates)](https://www.federalreserve.gov/supervisionreg/srletters/sr2206.htm) | Financial services | Updates to SR 11-7 interpretation |
| [NYDFS Part 500 — Cybersecurity Regulation (as amended)](https://www.dfs.ny.gov/industry_guidance/cybersecurity) | NY financial services | Cybersecurity + AI overlay; §500.09 (risk assessment), §500.13 (asset inventory), §500.17 (notifications) |
| [FDA — Software as a Medical Device (SaMD) and PCCP guidance](https://www.fda.gov/medical-devices/software-medical-device-samd) | Healthcare | Device-specific controls; Predetermined Change Control Plans for continuous-learning systems |
| [NAIC Model Bulletin on Use of AI Systems by Insurers (2023)](https://content.naic.org/sites/default/files/inline-files/2023-12-4%20Model%20Bulletin_Adopted_0.pdf) | Insurance | State-adopted insurance AI governance expectations |
| [OMB M-25-21 — Advancing the Responsible Acquisition of AI in Government](https://www.whitehouse.gov/omb/management/office-federal-financial-management/) | US federal | CAIO structure and federal AI control expectations |
| [Canadian Directive on Automated Decision-Making](https://www.tbs-sct.canada.ca/pol/doc-eng.aspx?id=32592) | Canadian federal | Impact-level framework and sector-neutral controls |
| [SOC 2 Trust Services Criteria](https://www.aicpa-cima.com/topic/audit-assurance/audit-and-assurance-greater-than-soc-2) | Cross-sector | Common framework for evidence-based audit; frequently paired with Annex A |

## Tier 3 — Crosswalks and secondary mappings

| Source | Pattern |
|---|---|
| NIST AI RMF Playbook — crosswalk sections | NIST ↔ ISO/IEC 42001 ↔ EU AI Act mappings; secondary artifact — trust the primary source where they disagree |
| European AI Office implementation guidance (as published) | EU AI Act article-level implementation specifics; evolving |
| Published sector-regulator crosswalks (NYDFS, NAIC) | Where available, use the regulator's own crosswalk preference |

## Tier 4 — Practitioner platforms (vendor landscape; descriptive, not endorsements)

Named in Chapter 4 §4.4. Capabilities evolve rapidly;
confirm current state before adopting.

| Category | Representative tools |
|---|---|
| General compliance platforms | OneTrust, Vanta, Drata, AuditBoard, Hyperproof |
| AI governance platforms with compliance features | IBM watsonx.governance, Credo AI, Holistic AI, Fairly, Fiddler |
| Hyperscaler-embedded compliance | AWS Audit Manager, Azure Compliance Manager, Google Cloud Compliance Reports |
| Roll-your-own | Audit ledger from `mod-108` + custom aggregation and workflow |

## Where to go next

- **`mod-110` — Incident Response.** The operational
  treatment of obligations triggered by incidents.
- **`mod-111` — Board Reporting & Risk Appetite.**
  Where compliance operations roll up to executive
  accountability.
- **`mod-112` — CAO Operating Model.** The function
  design that keeps compliance operations sustained.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
