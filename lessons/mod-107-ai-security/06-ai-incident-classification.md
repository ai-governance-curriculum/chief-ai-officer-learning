# Chapter 6 — AI Incident Classification

## Why this chapter exists

AI incidents need classification. The classification
determines who responds, what notification obligations
apply, what regulatory reporting is required, and how
the incident gets reported up. A firm that tries to work
out the classification *during* the response has already
lost time — and the kind of time losses that matter here
are the ones the EU AI Act Article 73 timeline (as short
as *immediate* for critical infrastructure) will not
forgive.

The discipline is pre-computed taxonomy, pre-wired
routing, pre-named leads, pre-identified notification
obligations. Exercise 04 asks you to author exactly this
set of artifacts for Northfield. This chapter is the
structural model that exercise applies.

## 6.1 The three primary classifications

A working classification distinguishes:

1. **Security incident.** The AI system was compromised
   in a classical security sense — unauthorised access,
   data breach, malicious code execution, credential
   compromise, infrastructure takeover. Routes through
   the CISO's incident response.
2. **AI-program incident.** The AI system behaved in a
   way the program's controls were intended to prevent
   — bias incident, transparency failure,
   contestability failure, capability-boundary
   violation by the agent itself, model-behaviour
   change on vendor swap. Routes through the CAO
   function.
3. **Joint incident.** The incident has both security
   and AI-program dimensions. Routes through both, with
   a single named lead.

The third category is common for AI systems. Prompt
injection that exfiltrates customer data is a joint
incident: security (data exfiltration) and AI-program
(agent-behaviour failure). A vendor silently swapping
the foundation model that then produces different
decisions is also joint: security (supply-chain) and
AI-program (unauthorised behaviour change). Treating
joint incidents as single-category is a common first-
year error.

## 6.2 Sub-categories

Each top-level category needs sub-categorisation to
drive routing. A taxonomy with only three top-level
categories is operationally too coarse. A proposed
sub-structure:

**Security incident sub-categories:**

- `SEC-ACC` unauthorised access to AI system
- `SEC-EXF` data exfiltration via AI system
- `SEC-SUP` supply-chain compromise of model / tooling
- `SEC-INF` infrastructure compromise affecting AI
- `SEC-DOS` denial of service against AI

**AI-program incident sub-categories:**

- `AI-BIA` bias / disparate impact
- `AI-TRA` transparency / explainability failure
- `AI-CON` contestability failure
- `AI-CAP` capability-boundary violation (agent acted
  out of scope)
- `AI-DRI` drift / degradation beyond specification
- `AI-MOD` model-behaviour change on vendor swap

**Joint incident sub-categories:**

- `JNT-INJ` prompt-injection-driven exfiltration or
  misuse
- `JNT-TOL` tool-exploitation driven by compromised
  input
- `JNT-POI` training-data poisoning producing
  AI-program harm
- `JNT-VND` vendor compromise affecting both security
  and AI-program behaviour

The sub-category structure must be *small enough to
remember* (`mod-103` §2.1 discipline). More than ~15
total sub-categories across the three primary categories
produces a taxonomy that is consulted but not used.

A specific firm's taxonomy may vary; the discipline is
the three-primary structure plus bounded sub-structure.

## 6.3 Routing rules

A working classification produces *routing rules* that
determine the response path. The default routing:

```
Incident detected
    │
    ▼
Classify: security / AI-program / joint?
    │
    ├── security: route to CISO IR; notify CAO function
    │
    ├── AI-program: route to CAO function; notify CISO
    │
    └── joint: AI Risk Council assigns single named
                  lead; both functions respond with
                  defined streams; CAO + CISO joint
                  status
```

The single-named-lead pattern is the same as `mod-104`
Chapter 6 (CAO × MRM vendor swap response). Distributed
leads on joint incidents is the failure mode that
produces conflicting responses to the same incident.

For each sub-category, the routing specification needs:

- **Detector.** Who or what detects the incident
  (monitoring, user report, external report).
- **Classifier.** Who makes the initial classification
  decision, and who can re-classify as more facts
  emerge.
- **Lead.** The named lead function.
- **Stream leads.** Named individuals (or roles) within
  each function who run their stream.
- **Internal notification list.** Who inside the firm
  learns about the incident at hour 0, at hour 24, at
  resolution.
- **External notification matrix.** Which regulators,
  on what timelines (§6.4).
- **Auto-escalation threshold.** Which incidents
  escalate to AI Risk Council / Board automatically
  rather than by judgement.

A routing specification missing any of these is not a
specification; it is a hint.

## 6.4 Notification obligations

AI incident regulatory notification obligations are
complex and overlapping in 2026. The CAO and CISO share
responsibility for triggering and fulfilling them.
Notable obligations:

| Regime | Trigger | Timeline | Lead |
|---|---|---|---|
| EU AI Act Art. 73 | High-risk AI serious incident | Immediate for critical infrastructure disruption; 2 days for fundamental-rights infringement; 15 days for other serious incidents | CAO |
| NYDFS Part 500 §500.17 | Cybersecurity event affecting NY-supervised entity | 72 hours | CISO with CAO content |
| GDPR Art. 33 | Personal data breach | 72 hours to Data Protection Authority | CISO + privacy + CAO joint |
| GDPR Art. 34 | Personal data breach with high risk to rights | Without undue delay to data subjects | Privacy + CAO joint |
| SR 11-7 model events | Material model incident at supervised bank | Per bank's regulator supervisory letter — commonly in next supervisory cycle | MRM + CAO |
| FDA MDR (medical devices) | Device-related adverse event | 30 days (10 days for malfunction causing death / serious injury) | Regulatory affairs + CAO |
| State insurance (varies) | Model-related consumer harm | Varies by state | Compliance + CAO |
| SEC Reg SCI (regulated entities) | System intrusion / disruption | Immediately upon awareness; written report in 24 hours | CISO + CAO + legal |

The table captures regime-specific triggers and
timelines as published; EU AI Act Article 73
implementing acts will refine triggers and timelines
through 2026–2027, so the program's internal matrix
should be refreshed on a quarterly cadence against the
current regulatory text.

Programs that try to compute notification obligations
*during* an incident response have already lost time.
The discipline is pre-computed notification matrices:
for each incident sub-category, which notifications are
required, on what timeline, who is responsible, with
template content pre-approved by legal.

## 6.5 Classification examples

| Incident | Classification | Sub-category | Lead | Why |
|---|---|---|---|---|
| Prompt injection causes the customer-service agent to disclose another customer's account information | Joint | `JNT-INJ` | CAO lead | Security (unauthorised disclosure) and AI-program (agent-behaviour failure); CAO leads because EU AI Act Art. 73 may apply |
| Vendor LLM provider silently swaps the foundation model, agent behaviour changes | AI-program | `AI-MOD` | CAO | Not a classical security incident; an AI-program behaviour change. Notify CISO of the vendor governance failure |
| Container image hosting the agent service is found to have a known CVE, but not yet exploited | Security | `SEC-INF` | CISO | Classical security; CAO informed because the agent is in scope of the AI program |
| Bias monitoring detects new disparate impact in production | AI-program | `AI-BIA` | CAO | Not a security incident in the classical sense; AI-program response |
| Customer reports that the agent's responses include text from another customer's session | Joint | `JNT-INJ` or `SEC-EXF` depending on facts | Initially CISO (immediate containment); re-assigned to CAO as facts emerge | Both possible privacy breach and agent behaviour failure; CISO leads immediate containment; classification revisited |
| Adversarial input to the fraud-detection model produces a false-negative pattern detectable in production | Joint | `JNT-INJ` (variant) | Joint lead | Adversarial defence is engineering (CISO); pattern detection feeds AI-program risk register |
| Credential leak gives an attacker access to the inference API | Security | `SEC-ACC` | CISO | Classical credential compromise; AI-program informed because of possible downstream behavioural anomaly |
| Red-team exercise finds a reproducible jailbreak that bypasses the output filter | AI-program (not an incident) | n/a — finding, not incident | CAO + CISO joint disposition | Red-team findings are not incidents by this taxonomy; they go to the risk register |

The pattern: most non-trivial incidents are joint. The
classification's value is naming the single lead and the
response path; not pretending the incident is one-sided.

A classification that was right at hour 0 may need
revision at hour 24. The taxonomy explicitly permits
re-classification; the IR ticket carries both the
initial and the current classification with a
revision log.

## 6.6 Post-incident discipline

A working program's post-incident discipline:

- **Classification is revisited** during the incident as
  more facts emerge. The IR ticket carries both initial
  and current classification. Re-classification
  decisions are logged.
- **Findings feed both the security threat model and the
  AI risk register** (`mod-103` §6.2). Incidents are not
  one-off events; they are inputs to the program.
- **Lessons learned are shared** across the CAO and CISO
  functions in a joint post-incident review. Separate
  reviews that do not converge produce two sets of
  lessons neither function fully adopts.
- **The classification taxonomy itself is reviewed
  annually** based on incidents that surfaced. Categories
  may need to evolve; new sub-categories may be needed;
  stale sub-categories may need retirement.
- **Notification completeness is audited.** Did the
  firm notify every regime it was obligated to notify?
  Internal audit (third-line, `mod-101` §3) runs this
  check periodically.

A program that classifies incidents but does not feed
lessons back into the taxonomy and the risk register is
missing the loop-closure the discipline requires.

## 6.7 Interface with existing IR

The AI incident classification does not stand alone. It
interfaces with the firm's existing incident response
machinery:

- **IR ticketing system.** Each AI-related incident
  ticket carries both an AI-program classification code
  (if applicable) and a security classification code
  (if applicable). The two codes may both appear on the
  same ticket for joint incidents.
- **IR playbooks.** Each sub-category has an IR
  playbook, co-authored by CAO and CISO, that specifies
  the first-24-hour actions. Playbooks are rehearsed on
  a cadence.
- **On-call rotation.** The CAO function's on-call —
  typically a dedicated role or a rotating duty — is
  reachable within the IR tooling at the same latency
  as the CISO's on-call.
- **Communication templates.** Templates for internal
  stakeholder communications and for external regulator
  communications are pre-approved by legal and
  pre-staged in the IR tooling.
- **Audit ledger.** Every classification decision, every
  re-classification, every notification sent lands in
  the audit ledger (`mod-108`).

The programs that struggle in year one are the ones
that treat AI incident classification as a separate
system from the CISO's existing IR. The programs that
work embed the classification *inside* existing IR
tooling with AI-specific extensions.

## 6.8 What the CAO reads for in a classification taxonomy

Six questions:

1. **Does the taxonomy name a joint category?** A
   two-category (security + AI-program) taxonomy misses
   the common case.
2. **Does it have sub-categories, bounded in count?** No
   sub-categories produces unactionable classifications;
   too many produces an unused taxonomy.
3. **Does each sub-category have a named lead and
   stream leads?** If not, run-time negotiation.
4. **Is the notification matrix pre-computed?** If not,
   the firm will miss timelines.
5. **Is re-classification explicitly permitted and
   logged?** If not, the taxonomy is brittle to the
   facts changing.
6. **Is the taxonomy reviewed on a cadence against
   actual incidents?** If not, drift between taxonomy
   and reality.

A CAO who holds these six questions through a
classification review has done the CAO's job on this
chapter.

## Summary

- AI incidents come in three primary classifications:
  security, AI-program, joint. The joint category is
  common; collapsing it into one of the others produces
  distributed leads and conflicting response.
- Each primary category needs bounded sub-categorisation
  — the proposed ~15-sub-category structure stays within
  the memorability discipline from `mod-103` §2.1.
- Routing rules specify detector, classifier, lead,
  stream leads, internal notification list, external
  notification matrix, auto-escalation threshold. A
  specification missing any element is a hint, not a
  specification.
- Notification obligations across EU AI Act Art. 73,
  NYDFS Part 500 §500.17, GDPR Art. 33/34, SR 11-7, FDA
  MDR, state insurance, SEC Reg SCI, and sector-specific
  rules are pre-computed into a matrix. Computing during
  the incident loses time.
- Classification is revised as facts emerge; the IR
  ticket carries initial and current classification with
  a log. Programs that treat classification as
  one-shot are brittle to the facts moving.
- Post-incident discipline includes: lessons feed both
  security threat model and AI risk register, joint
  post-incident reviews, annual taxonomy review,
  internal audit on notification completeness.
- The classification is embedded in existing CISO IR
  tooling, not run as a parallel system. Playbooks are
  co-authored, on-call is reachable at parity latency,
  decisions land in the audit ledger.
