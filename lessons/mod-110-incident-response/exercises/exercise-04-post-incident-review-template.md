# Exercise 04 — Author a Post-Incident Review Template

**Estimated time**: 3 hours
**Deliverable**: Review template + worked example (≤ 4 pages combined)

---

## The scenario

You are the CAO at **Northfield Mutual**
(continuation from Ex-01). The Audit Committee,
after reviewing Northfield's recent incident
responses, has asked you to author a **standard
post-incident review template** that ensures all
material AI incidents receive consistent treatment
and that the reviews survive external scrutiny
(Chapter 6 §6.7).

## Your assignment

Produce two artifacts.

### Artifact 1 — The template (≤ 2 pages)

A template structured per Chapter 6 §6.6, with
all eight sections and the field-level content
each requires. For each section, provide:

- The **fields** to populate.
- An **authoring prompt** (one-to-two sentences
  guiding the author on what belongs in the
  section — what is in scope, what is out).
- An **example** of what a good filled-in
  version looks like.

The eight sections are:

1. **Incident summary** — one-paragraph
   description; classification per
   [`mod-107`](../../mod-107-ai-security/README.md)
   §6; materiality determination; affected
   scope.
2. **Response summary** — timeline from
   Chapter 5 §5.6; key decisions and roles;
   containment posture history (Chapter 3);
   notifications made (Chapter 4).
3. **What worked** — at least two specific
   positive findings (Chapter 6 §6.2) with
   attribution.
4. **What didn't** — substantive findings
   with evidence.
5. **Root causes** — proximate and systemic
   (Chapter 5 §5.3), the causal tree
   (Chapter 5 §5.2), and the known unknowns
   (Chapter 5 §5.7).
6. **Recommendations** — each meeting the
   five properties from Chapter 6 §6.3, with
   at least one residual acceptance per
   Chapter 6 §6.4 where applicable.
7. **Recommendation status** — open / in
   progress / closed / accepted-as-residual,
   with the update cadence.
8. **Sign-off** — review lead, AI Risk
   Lead, AI Risk Council, and (for material
   incidents) Board / Audit Committee
   acknowledgment, with date and version.

### Artifact 2 — Worked example (≤ 2 pages)

Apply the template to a hypothetical Northfield
incident. Use the bias-incident scenario from
Ex-01 (or a similar pattern) and populate every
section as a fully-realised review.

The worked example must demonstrate:

- The **what-worked discipline** (Chapter 6
  §6.2) with at least two specific positive
  findings.
- The **proximate-vs-systemic distinction**
  (Chapter 5 §5.3) as separate fields, each
  with specific content.
- The **recommendation discipline** (Chapter
  6 §6.3) with at least three recommendations
  that are specific, assigned (named role),
  scheduled, tracked, and (as-of publication)
  with status.
- At least one **residual acceptance** (Chapter
  6 §6.4) — a finding where remediation is
  not the chosen path, with the residual
  risk, compensating controls, accepting
  authority, and review cadence named.

## Constraints

- The template must include the "what worked"
  section explicitly. Programs that omit it
  develop the defensive culture Chapter 6 §6.2
  warns against.
- The template must distinguish proximate cause
  from systemic cause as separate fields.
- The recommendation section must include
  status tracking with the Chapter 6 §6.3
  five properties.
- The worked example must include at least
  one residual-acceptance recommendation.
  Programs that recommend remediation for
  every finding are not credible with
  experienced regulators (Chapter 6 §6.4).
- The template must specify the review's
  signatories and acknowledgments explicitly;
  "signed by appropriate parties" is not
  sufficient.
- The combined length is ≤ 4 pages.

## Rubric

| Criterion | Weight |
|---|---|
| Template — eight sections with fields + prompts + examples | 25% |
| What-worked discipline applied in the worked example | 15% |
| Proximate vs systemic causation distinguished | 15% |
| Recommendation discipline applied with the five properties | 15% |
| Worked example — fully populated | 15% |
| At least one residual-acceptance recommendation | 10% |
| Length discipline — ≤ 4 pages | 5% |

## Where to submit

`chief-ai-officer-solutions/modules/mod-110-incident-response/exercise-04-post-incident-review-template/SOLUTION.md`

## Reading before you start

- Chapter 5 (investigation and root cause),
  especially §5.3 (proximate vs. systemic) and
  §5.7 (what investigation produces).
- Chapter 6 (post-incident review), especially
  §6.3 (recommendation discipline), §6.4
  (residual acceptance), and §6.6 (template).
- The reference solution for Ex-01 (for the
  incident scenario context) once available.
- [`mod-103`](../../mod-103-ai-risk-frameworks/README.md)
  Ex-04 (treatment plan with residual
  discipline) — the residual-acceptance
  pattern this exercise applies at incident
  scale.
