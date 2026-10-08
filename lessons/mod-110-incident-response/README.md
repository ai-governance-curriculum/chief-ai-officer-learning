# Module 110 — Incident Response

> Module 110 of the Chief AI Officer track. The
> operational treatment of AI incidents across all
> classes from [`mod-107`](../mod-107-ai-security/README.md)
> §6 — the first hour, containment, the EU AI Act
> Art. 73 notification matrix and its neighbours,
> investigation discipline that produces program
> improvement rather than blame, post-incident
> review that survives external scrutiny, tabletop
> readiness, and the enterprise-face communication
> a serious incident demands.

## What you will leave with

After working through this module you should be
able to:

1. Distinguish AI incident response from classical
   IR — and operate the differences without
   losing the discipline classical IR provides.
2. Run the first hour of an AI incident credibly:
   detection posture across channels, verification
   discipline, provisional classification, single-
   named-lead assignment, defensible containment
   posture.
3. Apply the notification matrix — EU AI Act
   Art. 73, NYDFS Part 500 §500.17, GDPR Arts.
   33–34, sector-specific regimes — to specific
   incidents.
4. Lead investigation and root-cause analysis
   that reaches organisational causes and
   produces program improvement rather than
   blame, in the NTSB-adjacent discipline.
5. Author post-incident reviews that survive
   external scrutiny and feed the GOVERN loop
   from `mod-103` §6.
6. Specify tabletop exercises that test the
   program's incident-response capability without
   over-investing in performance art.
7. Own the enterprise-face communication to CEO,
   Board, press, and customers during a serious
   incident — on the CAO function's lane, not
   substituting for Communications.

## Prerequisites

[`mod-101`](../mod-101-foundations/README.md)
through [`mod-109`](../mod-109-compliance-operations/README.md).

Particularly relevant:

- [`mod-107`](../mod-107-ai-security/README.md) §6
  (incident classification taxonomy) — the routing
  mechanism the first-hour classification uses.
- [`mod-102`](../mod-102-regulatory-landscape/README.md)
  §2.7 (EU AI Act Art. 73 timelines) and §4
  (sector regulations).
- [`mod-103`](../mod-103-ai-risk-frameworks/README.md)
  §6 (GOVERN continuously) — the loop
  post-incident reviews feed.
- [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)
  (audit ledger + evidence) — incident response
  produces evidence into and consumes evidence
  from the ledger.
- [`mod-109`](../mod-109-compliance-operations/README.md)
  (compliance operations) — the control catalog
  and continuous-evidence cadence incident
  response operates against.

## Module layout

```
mod-110-incident-response/
├── README.md                                        you are here — chapter index
├── 01-what-ai-incident-response-is.md               AI IR vs. classical IR; CAO function's role
├── 02-detection-and-the-first-hour.md               detection channels, verification, four first-hour decisions
├── 03-containment.md                                options, choosing, over- and under-containment
├── 04-the-notification-matrix.md                    seven dimensions × six regime families; multi-jurisdiction
├── 05-investigation-and-root-cause.md               five properties, five-whys, NTSB discipline
├── 06-post-incident-review.md                       properties, "what worked", recommendations, template
├── 07-tabletop-exercises.md                         scenario design, injects, scoring, cadence, anti-patterns
├── 08-enterprise-face-communication.md              CEO / Board / press / customer communication during serious incidents
├── exercises/                                       five exercises (~15 hours total)
├── quiz.md                                          20 questions covering the chapters
└── resources.md                                     annotated reading list, standards-first
```

## Chapters at a glance

| # | Title | Objective it anchors | Anchor sources |
|---|---|---|---|
| 1 | [What AI incident response is (and isn't)](./01-what-ai-incident-response-is.md) | Objective 1 | NIST SP 800-61 Rev. 2; `mod-107` §6 |
| 2 | [Detection and the first hour](./02-detection-and-the-first-hour.md) | Objective 2 (part) | NIST SP 800-61 Rev. 2; `mod-107` §6; `mod-108` evidence |
| 3 | [Containment without over- or under-containment](./03-containment.md) | Objective 2 (part) | NIST SP 800-61 Rev. 2; `mod-109` controls |
| 4 | [The notification matrix](./04-the-notification-matrix.md) | Objective 3 | EU AI Act Art. 73; NYDFS Part 500 §500.17; GDPR Arts. 33–34; sector regimes |
| 5 | [Investigation and root-cause analysis](./05-investigation-and-root-cause.md) | Objective 4 | NTSB investigation procedures; classical five-whys |
| 6 | [Post-incident review](./06-post-incident-review.md) | Objective 5 | NTSB-style review; `mod-103` §6 GOVERN loop |
| 7 | [Tabletop exercises](./07-tabletop-exercises.md) | Objective 6 | ISO 22301 BCM; cross-sector tabletop practice |
| 8 | [Enterprise-face communication during a serious incident](./08-enterprise-face-communication.md) | Objective 7 | SEC cybersecurity disclosure rule; practitioner crisis-communication sources |

## Exercises at a glance

| # | Title | Hours | Type | Deliverable |
|---|---|---|---|---|
| 01 | [Walk an incident through response](./exercises/exercise-01-walk-incident-through-response.md) | 3 | Applied | Phase-by-phase response narrative |
| 02 | [Design a notification matrix](./exercises/exercise-02-design-notification-matrix.md) | 3 | Applied | Notification matrix |
| 03 | [Lead a tabletop exercise design](./exercises/exercise-03-tabletop-exercise-design.md) | 3 | Synthesis | Tabletop design + scoring |
| 04 | [Author a post-incident review template](./exercises/exercise-04-post-incident-review-template.md) | 3 | Applied | Template + worked example |
| 05 | [Organizational incident-readiness assessment](./exercises/exercise-05-readiness-assessment.md) | 3 | Analytical | Readiness assessment |

## A note on tone

Incident response is the module where the CAO
function most visibly either earns the executive
room's confidence or loses it. The chapters hold
to that stakes level. The specific disciplines —
first-hour decisions, the notification matrix, the
NTSB-style separation of investigation from blame
— are not procedural niceties. They are the
machinery that decides whether an incident becomes
a documented learning event or a regulatory
finding that reshapes the program under duress.

## How this module fits

[`mod-107`](../mod-107-ai-security/README.md) §6
built the classification taxonomy. [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)
built the evidence infrastructure. [`mod-102`](../mod-102-regulatory-landscape/README.md)
supplied the obligations register. [`mod-103`](../mod-103-ai-risk-frameworks/README.md)
§6 named the GOVERN loop. [`mod-109`](../mod-109-compliance-operations/README.md)
operationalised the controls. This module is where
all of them come under incident pressure
simultaneously, and the discipline shows.

Downstream modules build on this one:

- **[`mod-111`](../mod-111-board-reporting/README.md) — Board Reporting & Risk Appetite.**
  Material incidents surface here; the Chapter 8
  Board briefing is the input.
- **[`mod-112`](../mod-112-cao-operating-model/README.md) — CAO Operating Model.**
  The incident-readiness assessment (Ex-05) is a
  specific input to the operating-model
  dimensioning.

## Paired solutions repo

[`chief-ai-officer-solutions / modules/mod-110-incident-response`](https://github.com/ai-governance-curriculum/chief-ai-officer-solutions/tree/main/modules/mod-110-incident-response)

Same conventions as earlier modules — worked
answers, not the answer.

---

<!-- aicg:maintained-by -->
Maintained by [VeriSwarm.ai](https://veriswarm.ai)
