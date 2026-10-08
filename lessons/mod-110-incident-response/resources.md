# Module 110 — Resources

Annotated reading list for Incident Response.
Standards and primary regulations first;
practitioner references last.

## Tier 1 — Authoritative (incident-response standards)

| Source | Why it matters |
|---|---|
| [NIST SP 800-61 Rev. 2 — Computer Security Incident Handling Guide](https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final) | The classical IR backbone Chapters 1–3 inherit. Four-phase lifecycle plus coordination-and-communication thread. Consult the NIST CSRC site for the current revision if a later edition supersedes Rev. 2. |
| [NIST SP 800-184 — Guide for Cybersecurity Event Recovery](https://csrc.nist.gov/publications/detail/sp/800-184/final) | Recovery-phase companion to SP 800-61; grounds Chapter 3 containment-to-recovery transition. |
| [ISO/IEC 27035 (series) — Information security incident management](https://www.iso.org/standard/78973.html) | International counterpart to NIST SP 800-61; useful cross-reference for firms operating under ISO/IEC 27001. |
| [ISO 22301:2019 — Business continuity management systems](https://www.iso.org/standard/75106.html) | Business-continuity discipline that overlaps IR; grounds the Chapter 3 §3.8 sustained-containment handoff. |

## Tier 2 — Authoritative (AI-specific and notification regimes)

| Source | Why it matters |
|---|---|
| [EU AI Act (Regulation (EU) 2024/1689) — Art. 73 serious incidents](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | The AI-specific notification regime. Consult alongside any implementing acts and guidance from the European AI Office for the current operational template and timeline tiers. |
| [EU AI Act — Art. 72 post-market monitoring](https://eur-lex.europa.eu/eli/reg/2024/1689/oj) | The surveillance regime that feeds Art. 73 triggers; grounds the Chapter 2 detection posture. |
| [NYDFS Part 500 — Cybersecurity Regulation (as amended)](https://www.dfs.ny.gov/industry_guidance/cybersecurity) | §500.17 cybersecurity-event notification (72-hour); §500.09 risk assessment; §500.13 asset inventory. The 2023 and 2024 amendments materially shifted triggers; use the current text. |
| [GDPR Art. 33 — breach notification to supervisory authority](https://gdpr-info.eu/art-33-gdpr/) | 72-hour notification regime; AI incidents with personal-data impact can trigger. |
| [GDPR Art. 34 — breach communication to data subject](https://gdpr-info.eu/art-34-gdpr/) | High-risk notification to individuals; interacts with the Chapter 4 §4.7 customer-notification discipline. |
| [EDPB Guidelines 9/2022 on personal data breach notification](https://edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-92022-personal-data-breach-notification-under_en) | EDPB elaboration of Arts. 33–34 operational mechanics. |
| [EU NIS2 Directive (Directive (EU) 2022/2555)](https://eur-lex.europa.eu/eli/dir/2022/2555/oj) | EU cybersecurity incident regime for essential and important entities; AI programs at covered firms carry parallel obligations. |

## Tier 3 — Sector-specific

| Source | Sector | Use |
|---|---|---|
| [OCC/FRB SR 11-7 — Guidance on Model Risk Management](https://www.federalreserve.gov/supervisionreg/srletters/sr1107.htm) | Financial services | Model-event supervisor escalation expectations; see also `mod-104`. |
| [FRB SR 22-6 — updates to SR 11-7](https://www.federalreserve.gov/supervisionreg/srletters/sr2206.htm) | Financial services | Updates to supervisory expectations on model risk and events. |
| [SEC Final Rule — Cybersecurity Risk Management, Strategy, Governance, and Incident Disclosure (2023)](https://www.sec.gov/rules/final/2023/33-11216.pdf) | Public companies | Form 8-K disclosure for material cybersecurity incidents within four business days of materiality determination. |
| [FINRA Rule 4530 — Reporting Requirements](https://www.finra.org/rules-guidance/rulebooks/finra-rules/4530) | Broker-dealers | Reportable events including specified customer complaints and incidents. |
| [FDA — Software as a Medical Device (SaMD) and PCCP guidance](https://www.fda.gov/medical-devices/software-medical-device-samd) | Healthcare devices | Device-specific controls and adverse-event framework. |
| [21 CFR 803 — Medical Device Reporting](https://www.ecfr.gov/current/title-21/chapter-I/subchapter-H/part-803) | Healthcare devices | Adverse-event reporting mechanics and timelines; applies to SaMD manufacturers. |
| [HHS OCR — HIPAA Breach Notification Rule](https://www.hhs.gov/hipaa/for-professionals/breach-notification/index.html) | Healthcare | Breach-notification regime for protected health information. |
| [NAIC Model Bulletin on Use of AI Systems by Insurers (2023)](https://content.naic.org/sites/default/files/inline-files/2023-12-4%20Model%20Bulletin_Adopted_0.pdf) | Insurance | State-adopted governance and documentation expectations for AI in insurance. |
| [UK ICO — Personal data breaches guidance](https://ico.org.uk/for-organisations/report-a-breach/personal-data-breach/) | UK | UK GDPR breach-notification operational guidance. |
| [MHRA — Software and AI as a Medical Device](https://www.gov.uk/government/publications/software-and-ai-as-a-medical-device-change-programme) | UK healthcare | UK regulator approach to AI-enabled medical devices. |

## Tier 4 — Foundational (investigation and learning culture)

| Source | What it gives this module |
|---|---|
| [NTSB Investigation Procedures](https://www.ntsb.gov/investigations/process/Pages/default.aspx) | The blame-free root-cause model Chapter 5 §5.4 adapts for AI IR. The separation of safety investigation from disciplinary process is the structural remedy for the Chapter 5 blame problem. |
| [FAA — Aviation Safety Action Program (ASAP)](https://www.faa.gov/about/initiatives/asap) | Safety-reporting-culture model: witnesses who report receive protection; the aggregate safety signal improves. Grounds the Chapter 5 §5.4 posture. |
| [NASA Aviation Safety Reporting System (ASRS)](https://asrs.arc.nasa.gov/) | Anonymous reporting culture; another model for the Chapter 5 §5.4 structural separation. |

## Tier 5 — AI-incident knowledge base and crosswalks

| Source | Pattern |
|---|---|
| [AI Incident Database (Partnership on AI)](https://incidentdatabase.ai/) | Catalogued public AI incidents; useful for grounding tabletop scenarios (Chapter 7 §7.3) in real patterns. |
| [OECD AI Incidents Monitor](https://oecd.ai/en/incidents-methodology) | OECD methodology for cataloguing AI incidents; cross-jurisdictional view. |
| [MITRE ATLAS — Adversarial Threat Landscape for AI Systems](https://atlas.mitre.org/) | AI-specific adversarial threat vocabulary; grounds AI-specific signatures the Chapter 2 §2.1 detection posture monitors for. |
| [MITRE ATT&CK](https://attack.mitre.org/) | Classical adversarial vocabulary for the security sub-categories of the Chapter 4 matrix. |
| [NIST AI RMF Playbook — crosswalk sections](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook) | NIST AI RMF ↔ ISO 42001 ↔ EU AI Act crosswalks that inform the Chapter 4 notification-matrix alignment work. Secondary artifact — trust the primary source where they disagree. |

## Tier 6 — Practitioner references (descriptive, not endorsements)

Named for completeness. Capabilities evolve;
confirm current state before adopting.

| Category | Representative sources |
|---|---|
| Live incident telemetry | [SANS Internet Storm Center](https://isc.sans.edu/) for current security-incident patterns |
| AI-safety research and post-mortems | Published academic post-mortems; vendor-published incident disclosures; peer-institution public retrospectives |
| Crisis communications | [SEC guidance on cybersecurity disclosure](https://www.sec.gov/corpfin/announcement/corpfin-announcement-cybersecurity-disclosure) is a primary source; broader crisis-communications practice draws on practitioner literature — consult current sources |

## Where to go next

- **[`mod-111`](../mod-111-board-reporting/README.md) — Board Reporting & Risk Appetite.**
  Where material incidents surface to executive
  accountability; the Chapter 8 Board briefing
  is the direct input.
- **[`mod-112`](../mod-112-cao-operating-model/README.md) — The CAO Operating Model.**
  Where incident-readiness fits in the overall
  program structure; the Ex-05 readiness
  assessment is a specific input to operating-
  model dimensioning.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
