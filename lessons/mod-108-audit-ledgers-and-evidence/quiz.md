# Module 108 — Quiz

Twenty questions. Answer key in the paired solutions repo.

---

## Section A — Operational logging vs audit-grade evidence (Chapter 1)

**Q1.** Which of these is **not** one of the three
properties Chapter 1 names as distinguishing evidence
from operational logging?

  a. Provenance
  b. Completeness
  c. Tamper resistance
  d. Customer-experience integration

**Q2.** True or false: A working test for evidence is
whether a hostile system that replaced the original
emitter could lie about history undetectably.

**Q3.** Short answer: in one sentence, distinguish
evidence from justification (Chapter 1 §1.4).

---

## Section B — The tamper-evident ledger pattern (Chapter 2)

**Q4.** What is the size of a Merkle inclusion proof
for a record in a tree of 1 billion records?

  a. 1 hash
  b. About 30 hashes
  c. About 1,000 hashes
  d. 1 billion hashes

**Q5.** Which structural property does Chapter 2 §2.3
say makes Certificate Transparency relevant as a
reference for AI audit?

  a. Patent protection
  b. Append-only with public commitments + witness
     signatures + external monitors
  c. The cryptographic algorithm choice (ECDSA P-256)
  d. The blockchain backend

**Q6.** True or false: A Merkle ledger provides
authenticity of records — guaranteeing that the
record reflects reality.

**Q7.** Short answer: in one sentence, describe one
thing the Merkle / RFC 9162 pattern does **not** do.

---

## Section C — Event vocabulary (Chapter 3)

**Q8.** What does Chapter 3 §3.1 name as the right
granularity for CAO evidence?

  a. Every function call
  b. Every operation that has program-relevant
     consequences
  c. Daily aggregates
  d. Per-week summaries

**Q9.** Which of these is **not** named in Chapter 3
§3.2 as something the event vocabulary should cover?

  a. Authorisation events
  b. Tool invocations
  c. Configuration changes
  d. Employee email contents

**Q10.** True or false: Large artifacts (model
weights, full input data, full output data) should
be included directly in the event records.

**Q11.** Short answer: in one sentence, describe
one consequence of operating without a vocabulary
registry (Chapter 3 §3.4).

---

## Section D — Evidence packages (Chapter 4)

**Q12.** Which of these is **not** named in Chapter 4
§4.2 as part of a complete evidence package?

  a. Cover document
  b. Inclusion proofs
  c. Chain of custody
  d. The model's training weights

**Q13.** Which evidence-package type is the Chapter 4
§4.4 pre-design pattern most appropriate for?

  a. One-off litigation discovery requests
  b. Regulator quarterly attestations
  c. Investigative subpoenas
  d. Internal post-incident reviews

**Q14.** Short answer: in one sentence, describe one
of the steps in the Chapter 4 §4.5 verification
protocol.

---

## Section E — Retention, sealing, chain of custody (Chapter 5)

**Q15.** What is the minimum EU AI Act Art. 12
retention period for high-risk-system logs?

  a. 30 days
  b. 6 months
  c. 7 years
  d. Indefinite

**Q16.** True or false: "Keep everything forever" is
described as the right retention posture.

**Q17.** Which of these is **not** a working chain
of custody record element per Chapter 5 §5.3?

  a. The system that emitted the evidence
  b. The signing key used
  c. The recipients and timestamps
  d. The retail price of the evidence

**Q18.** Short answer: in one sentence, describe
why email transmission of evidence is identified as
a chain-of-custody failure (Chapter 5 §5.3.1).

---

## Section F — Build, buy, or partner (Chapter 6)

**Q19.** Which risk is identified in Chapter 6 §6.4
as **most insidious** for audit-ledger buying?

  a. Latency overhead
  b. Migration risk
  c. Throughput limitations
  d. UI ugliness

**Q20.** Short answer: in two sentences, describe
one CAO contribution from Chapter 6 §6.5 to the
audit-ledger build / buy / partner decision.
