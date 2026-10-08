# Chapter 5 — The CAO × CISO Boundary

## Why this chapter exists

The CAO × CISO boundary is the second of the three
recurring CAO boundary problems. `mod-104` Chapter 6
covered CAO × MRM; `mod-111` will cover CAO × CFO for
board reporting. The discipline is parallel: respect the
peer function's domain expertise; do not encroach; do
contribute the AI-program perspective the peer function
does not own.

The CISO is older than the CAO function in most firms,
better networked, deeper in the operational tooling, and
unambiguously accountable for the firm's security
posture. A new CAO who comes in acting as if AI security
is "the CAO function's job" discovers quickly that the
CISO organisation can quietly block the program. A new
CAO who defers entirely to the CISO on AI matters
surrenders the AI-specific obligations the role was
created to carry — and discovers, usually during a
regulator interaction, that the CISO's generic security
posture does not answer AI-specific questions.

Exercise 03 forces a specific boundary dispute to a
defensible resolution. This chapter is the structural
model that exercise applies.

## 5.1 The structural parallel with CAO × MRM

Before the content: the structural model is the same as
`mod-104` Chapter 6. Two second-line functions. Overlap
is genuine. Neither sits above the other. Hierarchical
framings in either direction fail predictably.

| Property | CAO × MRM (`mod-104`) | CAO × CISO (this chapter) |
|---|---|---|
| Peer function | MRM under CRO | CISO (variable reporting) |
| Established function age | ~15 years at mature banks | ~25 years across most sectors |
| Overlap source | Models are an AI subset | AI systems are a security subset |
| Primary failure mode | New CAO treats as subordinate or superior | New CAO treats as subordinate or superior |
| Resolution pattern | Peer-boundary with named lead per topic | Peer-boundary with named lead per topic |

The parallel is not a coincidence. It is the general
shape of CAO peer-function boundaries: the AI function is
new; the peer function has operational depth the AI
function needs; the resolution is partition of scope by
primary framing of the issue, not partition by
hierarchy.

## 5.2 What the CISO owns

Within AI-related security, the CISO owns:

- **AI-system security in the classical sense.** Network
  security, infrastructure security, identity, endpoint,
  secrets management, image signing, deployment
  pipelines. The infrastructure layer and most of the
  data layer from Chapter 3.
- **AI-related incident response operations.** The IR
  team, the IR tooling, the IR playbooks, the on-call
  rotation. Running an incident is a CISO operational
  discipline.
- **The security monitoring stack as it applies to AI
  systems.** SIEM, EDR, UEBA, cloud security posture
  management, data loss prevention. The CAO contributes
  what to monitor for; the CISO operates the stack.
- **The penetration-testing program.** Pen-test
  methodology, vendor relationships, remediation
  tracking.
- **The vulnerability-management program.** CVE
  tracking, patching cadence, SBOM. Model artifacts
  increasingly fit this program's scope.
- **Vendor security risk assessment for AI vendors.** In
  coordination with the CAO function for AI-specific
  criteria.

The historical centre of gravity on each is CISO. A new
CAO function cannot and should not claim them.

## 5.3 What the CAO function owns

Within AI-related security, the CAO function owns:

- **The AI risk taxonomy's security category.** Per
  `mod-103` §2. Security is a risk category within the AI
  risk framework; the CAO owns the AI framework and the
  category inside it.
- **The AI-program-level threat-model expectations the
  CISO operates within.** The CAO specifies which
  categories (from Chapter 1) must be defended against;
  the CISO decides how.
- **The AI-program-level red-teaming policy.** Per
  Chapter 4. The CAO sets cadence, independence
  expectations, and evidence requirements; the CISO (or
  external) executes.
- **AI-specific incident classification.** When is an
  incident a security incident vs an AI-program
  incident vs both. Chapter 6 develops the taxonomy.
- **AI-program reporting on security posture to the
  Board and regulators.** The AI section of the Board
  risk pack; the EU AI Act Article 15 "cybersecurity"
  position; sector-regulator AI-security
  correspondence.
- **The EU AI Act, NYDFS Part 500 AI amendments, and
  similar AI-specific regulator interfaces.** In
  coordination with the CISO for any cybersecurity-
  overlap elements.
- **AI vendor assessment criteria.** The CAO defines
  what AI-specific criteria the CISO's vendor-
  assessment process must evaluate.

Note what the CAO does *not* own under this boundary:
the operational security tooling, the incident response
machinery, the pen-test program, or the general vendor-
security process. The CAO contributes criteria and
oversight; the CISO operates.

## 5.4 The intersection — where both have legitimate claims

The overlap is genuine. Seven topics predictably sit on
the boundary:

| Topic | CAO contribution | CISO contribution |
|---|---|---|
| Prompt-injection defence | Program expectations: what systems need it, what classes of injection must be defended against | Engineering: specific input / output filters, prompt-injection detection techniques, operational deployment |
| LLM output filtering | What must be filtered (PII, harmful content, secrets, system-prompt leakage) | Operates the filters; selects products; tunes thresholds |
| Adversarial-input defence | Program-level validation expectation (`mod-104` Ex-02 pattern) | Engineers detection; tunes decision-boundary monitoring |
| AI vendor security | Sets AI-specific assessment criteria (foundation-model-swap handling, training-data provenance, red-team evidence) | Executes the vendor-security assessment within existing third-party-risk machinery |
| Red-teaming program | Program-level requirements per Chapter 4 | Often executes, or commissions external execution; both review findings |
| AI incident response | Classifies (Chapter 6); reports externally where AI-regime obligations apply | Operates IR; executes containment; coordinates internal response |
| Regulator-facing security posture | Authors AI-program parts (EU AI Act, AI-specific sector rules) | Authors security-engineering parts (NYDFS Part 500, GLBA Safeguards, HIPAA security rule) |

The pattern on each topic is the same: both have a
legitimate claim; neither can unilaterally own the topic
without losing something important.

## 5.5 Operating the boundary — patterns that work

Four patterns, in order of importance:

### 5.5.1 Single named lead per topic

When an issue surfaces, one function leads and the other
is informed. The lead is determined by the primary
framing of the issue:

- Classical security pattern (infrastructure vuln,
  credential leak, malware) → CISO leads.
- AI-specific pattern (bias finding under adversarial
  pressure, model behaviour change on vendor swap,
  prompt-injection surface in a new agent) → CAO leads.
- Combined (prompt injection that exfiltrates PII;
  foundation-model swap that regresses alignment) →
  joint, with a *single* named lead and the other
  function explicitly in support.

The named-lead convention is what allows the regulator
to hear one organisation. Dual leads produce dual
positions, which produce one examiner question: "which
of these is your official position?"

### 5.5.2 Joint red-teaming expectations

The CAO defines the program-level expectations; the
CISO executes (or commissions external execution). Both
functions review findings. The co-signed artifact is a
single red-team program document that both heads will
defend to the Board.

Specifically:

- Scope, independence, cadence, evidence requirements —
  CAO specifies, CISO implements.
- Specific threat scenarios for each exercise — jointly
  authored, with the CAO contributing AI-program-level
  threats and the CISO contributing security-
  engineering threats.
- Findings disposition — jointly reviewed; CAO prevails
  on AI-program-material findings, CISO prevails on
  security-engineering-material findings, joint
  disposition on genuinely-joint findings.

### 5.5.3 Cross-referenced incident classification

AI incidents that are also security incidents get *one*
classification reflecting both, not two. Chapter 6
develops the taxonomy. Operationally: the IR ticket
carries both an AI-program classification code and a
security classification code; the same incident does not
exist twice in the two systems.

### 5.5.4 Single regulator response on joint topics

EU AI Act Art. 73 incident reporting may have both AI-
program and security elements. CAO leads on Art. 73
specifically with CISO's content contribution. The
regulator receives one response, not two.

Conversely, NYDFS Part 500 §500.17 cybersecurity-event
reporting is CISO-led with CAO content contribution for
AI-specific aspects. The regulator receives one
response.

The principle: whichever regime is primary, that
function leads; the other contributes substantively but
does not communicate separately with the regulator.

## 5.6 The collision patterns — what fails

Four patterns that look reasonable and consistently
produce bad outcomes:

### 5.6.1 CAO writing the security-engineering standards

Encroachment. The CAO function writes standards the
engineering team cannot operationalise, or writes
standards that duplicate the CISO's existing standards
with slight variation. Produces standards engineers
will not follow. Resolution: CAO authors program
expectations, CISO authors engineering standards.
Exercise 03 is this collision pattern in detail.

### 5.6.2 CISO ignoring AI-program-level threat-model expectations

Decoupling. The CISO's security controls are optimised
for classical threats; AI-specific threats go
undefended because they do not fit the CISO's
historical threat model. Resolution: CAO-authored
threat-model expectations become binding on CISO's
security-engineering standards; disputes escalate to
the shared executive.

### 5.6.3 Separate AI security incident channels

Duplication. The CAO function stands up its own
incident-response capability for AI systems because the
CISO's IR doesn't handle AI incidents well. Produces
two IR capabilities with worse performance than one
unified capability. Resolution: embed AI-specific
capability inside the CISO's IR with a CAO-contributed
AI incident playbook (Chapter 6).

### 5.6.4 CAO rubber-stamping CISO's AI security posture

The opposite of §5.6.2. The CAO defers to the CISO
entirely; the AI-program-level threat model is whatever
the CISO's slide deck says. Resolution: the CAO maintains
an independent view of the AI threat model and
challenges the CISO's posture on it on a cadence.

Each failure pattern is traceable to one of the two
functions attempting hierarchy. The peer-boundary design
is the structural remedy.

## 5.7 The reporting-line question

A recurring debate: where should AI-specific security
*engineering* work report?

| Pattern | Trade-off |
|---|---|
| In the CISO's organisation | Alignment with CISO operational standards; CAO contributes criteria but does not operate engineering. The dominant mature pattern |
| In a parallel AI security function under the CAO | AI-specific depth; expensive duplication of CISO infrastructure; typically fails at scale |
| Matrixed between CISO and CAO | Flexible; coordination overhead is high; works only with strong joint-committee machinery |

The pattern that works: AI-specific security *engineering*
sits in the CISO's organisation; the CAO function's
contribution is **program design and oversight**. This
mirrors the MRM pattern — MRM engineering sits with the
CRO, and the CAO's contribution is program-level.

The principle: where established functions exist, embed
the AI-specific work within them; do not create parallel
functions. Parallel functions produce the collision
patterns in §5.6.

## 5.8 Working the boundary at steady state

A CAO function that has made peace with the CISO
typically has:

- A short, co-signed scope memo describing the
  boundary. Both heads sign; refreshed annually.
- A joint-committee cadence that is the primary venue
  for cross-boundary decisions. Weekly or biweekly.
- Joint red-team program documentation. Single
  artifact; two heads defend it.
- Shared incident classification taxonomy (Chapter 6).
  Operationalised in the IR ticketing system.
- Mutual read-access to each function's standards,
  working documents, and incident logs.
- A named escalation path to a shared executive — CRO,
  COO, or CEO depending on firm structure — for the
  rare disputes that cannot resolve at working level.
- A joint annual report to the Board that covers both
  security posture and AI-program posture, with
  explicit cross-references.

The absence of any item is a diagnostic. A CAO who
cannot describe the cadence by which they coordinate
with the CISO has not yet solved the boundary.

## 5.9 What the CAO reads for in the boundary

Six questions to hold through the first year with the
CISO:

1. **Is there a co-signed scope memo?** If not, draft
   one. The absence is a tell that the boundary has
   not been resolved.
2. **Who authors the AI-security engineering
   standards?** If CAO, encroachment (§5.6.1). If CISO
   alone, likely a decoupling risk (§5.6.2).
3. **Is there a single IR capability or two?** If two,
   remediate.
4. **Is there a joint red-team artifact?** If not, the
   §5.5.2 pattern has not landed.
5. **Which function speaks to each regulator?** If both
   speak to the same regulator independently, the
   §5.5.4 pattern has not landed.
6. **Where does the AI-specific security engineering
   report?** If parallel to CISO under CAO, re-visit.

A CAO who holds these six questions open is doing the
CAO's job on this boundary.

## Summary

- The CAO × CISO boundary is a peer-boundary between a
  new (CAO) and an established (CISO) function. The
  structural model mirrors the CAO × MRM boundary from
  `mod-104` Chapter 6.
- CISO owns operational security — infrastructure, IR,
  monitoring, pen-testing, vulnerability management,
  vendor security. CAO owns AI-program expectations —
  threat model, red-team policy, incident
  classification, AI-regime regulator interfaces.
- Seven intersection topics have legitimate claims from
  both sides: prompt-injection, output filtering,
  adversarial inputs, AI vendor security, red-teaming,
  AI incident response, regulator-facing posture.
- Four operating patterns work: single named lead per
  topic, joint red-teaming expectations, cross-
  referenced incident classification, single-regulator-
  voice on joint topics.
- Four collision patterns fail: CAO writing security-
  engineering standards, CISO ignoring AI-program
  threat-model expectations, separate IR channels, CAO
  rubber-stamping CISO posture.
- AI-specific security engineering sits in the CISO's
  organisation. CAO contributes program design and
  oversight. Parallel functions produce the collision
  patterns and should be avoided.
- A working CAO × CISO boundary has: co-signed scope
  memo, joint committee cadence, single red-team
  artifact, shared incident classification, mutual read
  access, named escalation path, joint Board report.
