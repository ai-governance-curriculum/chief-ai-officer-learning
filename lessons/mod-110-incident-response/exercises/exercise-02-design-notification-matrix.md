# Exercise 02 — Design a Notification Matrix

**Estimated time**: 3 hours
**Deliverable**: Notification matrix (≤ 4 pages)

---

## The scenario

You are the CAO at **Tessera Bank**, a mid-sized
US bank with EU-resident customers via its
corporate-banking arm (and therefore EU AI Act
reach for AI systems used in that line), New York
state operations (NYDFS Part 500 reach), personal-
data processing under GDPR, and SR 11-7 model-
risk obligations with its primary federal
supervisor.

The Chief Compliance Officer and you have agreed
(per the mod-109 Ch. 6 peer-boundary pattern)
that the CAO function will author the AI-specific
notification matrix. The matrix operationalises
who gets notified, when, by whom, in what format,
for each incident classification from
[`mod-107`](../../mod-107-ai-security/README.md)
§6.

## Your assignment

Produce the matrix in four sections.

### Section 1 — Scope and use (≤ ¼ page)

- Which incidents the matrix covers (AI-program
  + joint per [`mod-107`](../../mod-107-ai-security/README.md)
  §6; security-only incidents follow the CISO's
  existing matrix).
- Who maintains the matrix and the joint review
  cadence (Chapter 4 §4.3).
- How the response team consults the matrix
  during an incident, and where the consultation
  record is written (Chapter 2 §2.6).
- Version-control and audit-ledger placement
  (Chapter 4 §4.4).

### Section 2 — The matrix proper (≤ 2 pages)

For each of the nine incident sub-categories from
[`mod-107`](../../mod-107-ai-security/README.md)
Ex-04 (security 1.a–d, AI-program 2.a–d, joint
3.a–d — notification triggers differ within
top-level categories, so the matrix must operate
at the sub-category layer), produce rows per
applicable notification obligation using the
seven dimensions from Chapter 4 §4.1:

| Sub-category | Recipient | Trigger | Timeline | Lead | Format | Supporting evidence | Approvals |
|---|---|---|---|---|---|---|---|
| 2.a Bias incident | EU AI Act NCA | Fundamental-rights impact on EU-resident customer | Per EU AI Act Art. 73 timelines (consult current text) | CAO function | Per EU AI Act Annex IX | Scope estimate, containment, provisional root cause | CAO + GC + CRO |
| 2.a Bias incident | State insurance / banking regulator | US state-supervised customer affected | Per state (typically 72h from determination) | CCO + CAO | Per state portal | Customer scope, remediation plan | CCO + CAO |
| ... | ... | ... | ... | ... | ... | ... | ... |

Cover at minimum (Chapter 4 §4.2):

- EU AI Act Art. 73 (every sub-category where
  applicable).
- NYDFS Part 500 §500.17 (security sub-
  categories + joint; refer to the current text
  for 2024-amended triggers).
- GDPR Art. 33 (to supervisory authority) where
  personal data is affected.
- GDPR Art. 34 (to data subject) where high
  risk to rights and freedoms.
- SR 11-7 model-event supervisor escalation.
- SEC cybersecurity disclosure (2023 rule) for
  materiality-triggered events, with Investor
  Relations coordination.
- Contractual customer notification (per
  Tessera's largest customer-contract
  notification clauses — specify the window and
  the content expectation).
- Internal: Board (Audit Committee), AI Risk
  Council (per the firm's escalation
  thresholds).

### Section 3 — Edge cases (≤ ¾ page)

Address four edge cases explicitly (Chapter 4
§4.8):

- **Multi-jurisdiction.** A customer is both
  EU-resident and US-domiciled — which
  notifications apply, with what sequencing and
  what consistency requirement.
- **Vendor-side incident.** The LLM vendor
  announces an upstream issue that affected
  Tessera's output. How Tessera's notifications
  apply (not deferring to the vendor's).
- **Discovery during examination.** A regulator
  discovers the incident during their own
  exam before Tessera independently detected
  and classified. The posture under this
  scenario.
- **No-notification-required determination.**
  Where the matrix row concludes no external
  notification is required — the reasoning and
  the recording expectation.

### Section 4 — Maintenance (≤ ¼ page)

- Trigger events for matrix update (Chapter 4
  §4.3): new regulation, new jurisdiction,
  matrix defect from a real incident.
- Review cadence (joint quarterly working
  meeting with CAO + CCO + CISO + DPO + GC).
- Approval authority for matrix changes.
- Version-control and audit-ledger insertion.

## Constraints

- All nine sub-categories must be covered.
- All cells must be **specific** — no "as
  appropriate" or "per applicable regulation".
- Timelines must cite the specific authority
  (Art. 73; Part 500 §500.17; GDPR Art. 33;
  etc.) and be aligned with the current source
  text at matrix build time. Where a specific
  timeline tier depends on an implementing act
  or an evolving regulation, flag the
  dependency.
- Approval chains must name roles, not
  functions. "GC" is a role; "the legal
  function" is a function.
- At least one row must be a *no-notification-
  required* determination with reasoning (per
  §4.8).
- The matrix must address at least one
  multi-jurisdiction coordination case in
  Section 3 with specific sequencing.

## Rubric

| Criterion | Weight |
|---|---|
| Coverage — all 9 sub-categories | 20% |
| Cell specificity — no "as appropriate" | 20% |
| Authority citations aligned with current source text | 15% |
| Edge cases addressed substantively | 20% |
| Maintenance cadence and version-control | 10% |
| Multi-jurisdiction coordination handled | 10% |
| Length discipline — ≤ 4 pages | 5% |

## Where to submit

`chief-ai-officer-solutions/modules/mod-110-incident-response/exercise-02-design-notification-matrix/SOLUTION.md`

## Reading before you start

- Chapter 4 (notification matrix) of this
  module.
- Chapter 2 §2.6 (what the first hour produces,
  including the matrix consultation record).
- [`mod-107`](../../mod-107-ai-security/README.md)
  §6 and Ex-04 (classification taxonomy the
  matrix operates against).
- [`mod-102`](../../mod-102-regulatory-landscape/README.md)
  §2.7 (EU AI Act Art. 73) and §4 (sector
  regulations). Verify the current text —
  implementing acts and amendments can shift
  timeline tiers between the module authoring
  date and the reader's build date.
- [`mod-109`](../../mod-109-compliance-operations/README.md)
  Ch. 6 (CAO × Chief Compliance Officer
  boundary; the matrix is a joint artifact).
