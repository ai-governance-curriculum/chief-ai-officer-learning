# Chapter 2 — The Tamper-Evident Ledger Pattern

## Why this chapter exists

Chapter 1 named tamper resistance as one of the three
distinguishing properties of evidence. This chapter is
the cryptographic machinery that provides it at scale.
Two structures do the work: **Merkle trees** and **hash
chains**. One standard assembles them into a production-
grade pattern: **RFC 9162 — Certificate Transparency
Version 2.0**.

The chapter is deliberately disciplined about what the
pattern does and does not do. The CAO who reads
cryptographic-ledger marketing material will encounter
claims that collapse under examination; the discipline
here is distinguishing the integrity guarantees the
mathematics actually provides from the organisational
guarantees programs are tempted to assume on top of them.

## 2.1 The Merkle tree

A Merkle tree is a tree of hashes. Each leaf is the hash
of a data record. Each internal node is the hash of its
children's hashes. The root hash commits to every leaf —
change any leaf, and the root changes.

```
                   root_hash
                  /          \
              h(h1+h2)    h(h3+h4)
              /    \      /    \
            h1    h2    h3    h4
            |     |     |     |
          rec1  rec2  rec3  rec4
```

The structure has two operational properties that matter
for evidence.

**Inclusion proofs are small.** To prove that a specific
record is in the tree, you provide `log₂(n)` hashes —
the *audit path* from the leaf to the root. For a tree
of 1 billion records, an inclusion proof is 30 hashes.
The external verifier computes the root from the leaf
and the path, and compares against the published root.

**Consistency proofs are small.** To prove that a later
tree is a strict *extension* of an earlier tree — that
no history has been rewritten — the proof size is also
`log₂(n)` hashes. The external verifier can confirm
that the sequence of commitments the program has
published form a monotonic, append-only history.

Both properties are what makes Merkle trees the right
structure for evidence at scale: external verifiers can
check inclusion or consistency without needing the full
ledger, and the proofs can be transmitted alongside
individual evidence records.

## 2.2 The hash chain

A hash chain is a simpler structure. Each record
includes the hash of the previous record. Change any
record and every subsequent record's chain link breaks.

```
rec1: { data: ..., prev_hash: 0 }   → h1
rec2: { data: ..., prev_hash: h1 }  → h2
rec3: { data: ..., prev_hash: h2 }  → h3
...
```

Compared to Merkle trees:

- **Sequential structure.** Operations append at the
  end; ordering is preserved intrinsically. This is
  useful when the order of records matters to the
  interpretation of the evidence (which it does for
  most CAO-relevant events — a sequence of
  authorisation decisions and tool invocations is
  interpreted in order).
- **Larger consistency proofs.** Verifying that record
  `N` is unchanged requires walking back `N` records,
  or `N/k` for an indexed hash chain with periodic
  checkpoints. Not as efficient as a Merkle tree at
  large scale.
- **Simpler implementation.** No tree balancing, no
  path arithmetic. For small-to-medium volumes, a hash
  chain alone is often sufficient.

Most working audit ledgers use *both*: hash chains
within batches (preserving per-operation order) and
Merkle trees across batches (efficient external
verification at scale). The structural requirements for
Exercise 03 assume this hybrid.

## 2.3 RFC 9162 and Certificate Transparency

The technical reference for production tamper-evident
ledgers in 2026 is **RFC 9162 — Certificate
Transparency Version 2.0**. Certificate Transparency
has operated at internet scale since 2013, logging
every TLS certificate issued by participating CAs. Its
structural patterns transfer cleanly to AI audit, and
the standard is mature, interoperable, and vendor-
neutral.

The RFC 9162 architecture rests on four concepts:

- **Append-only log.** Records can only be added.
  Modification of existing records is treated as
  evidence of compromise, not a routine operation.
- **Public commitments.** The log periodically
  publishes its root hash — a *signed tree head*
  (STH) — to a public channel. The STH is small
  (a hash plus a signature plus a timestamp) and
  can be observed by anyone.
- **Witness signatures.** Multiple independent
  witnesses observe the log's STHs and countersign
  them. Tampering requires compromising the log
  operator *and* multiple witnesses — a materially
  higher bar than compromising the log alone.
- **Monitors.** External parties continuously watch
  for inconsistencies — a published STH that is not
  a consistent extension of previous STHs — and
  disclose them. The ledger's trustworthiness
  depends on monitors existing and operating; the
  cryptography makes their job efficient but does
  not substitute for them.

AI audit ledgers using RFC 9162 patterns inherit
considerable assurance from the architecture itself,
and interoperate with tooling the broader security
community has already built.

## 2.4 What the pattern does not do

The Merkle / RFC 9162 pattern provides **integrity**
and **inclusion** assurance at scale. It does not
provide — and no reading of the specification should
suggest it does — the following:

- **Confidentiality.** Anyone with access to the
  ledger sees what is in it. If the ledger contains
  sensitive data in plaintext, the Merkle structure
  does nothing to protect it. Programs with sensitive
  content in evidence records should encrypt the
  content and store ciphertext, or store hashes with
  content held separately.
- **Authenticity of records relative to reality.**
  The pattern guarantees that a record was committed
  to the log at a point in time. It does not
  guarantee that the record reflects reality. A
  compromised emitter can write false records that
  the ledger faithfully preserves forever. Integrity
  of the ledger is not integrity of the input.
- **Right interpretation of records.** The records
  enable analysis. They do not perform the analysis.
  A ledger of perfectly authentic records that the
  program misinterprets is still a program failure.
- **Compliance.** A program with an RFC 9162-conformant
  ledger that captures the wrong events, retains them
  for the wrong duration, or produces evidence
  packages that fail the audience's verification
  protocol has not met the regulatory obligation. The
  cryptography is a layer of the control; it is not
  the control.

Programs that treat "we have a Merkle ledger" as
sufficient evidence assurance are confusing the
infrastructure with the discipline. Chapter 1 §1.4
flagged this conflation; the specific cost here is
that the mathematics creates a false confidence that
substitutes for the organisational work.

## 2.5 The specific guarantees, in words a non-cryptographer can use

Three statements the CAO should be able to make
accurately about a ledger that implements the pattern:

1. "Any record in the ledger comes with a short
   mathematical proof that an external party can
   check in milliseconds, without seeing the rest
   of the ledger."
2. "If anyone — including the operator of the ledger
   — modifies or removes a record after it was
   committed, that modification is detectable to any
   party who has observed the earlier commitments."
3. "If the ledger operator publishes new commitments
   that contradict earlier ones, the contradiction
   is externally visible to any monitor who has
   recorded the earlier commitments."

These three statements are honest. Statements that go
beyond them — "we can prove the records are true", "we
can prove no one has tampered with the system", "we are
compliant because we have a Merkle ledger" — are not,
and the discipline is noticing when the overclaim
appears.

## 2.6 Practitioner patterns

A range of implementations exists in 2026. The CAO
does not need to choose; the CAO needs to know what
the engineering function is choosing from:

- **Sigstore Rekor.** Open-source, Merkle-based
  transparency log designed for software supply chain.
  Adaptable to AI events; growing ecosystem.
- **AWS CloudTrail with log-file integrity validation.**
  Hyperscaler-managed audit trail with digest-chain
  integrity. Operationally familiar; less flexible on
  event vocabulary.
- **Google Cloud Logging with log bucket retention +
  immutability.** Similar posture at a different
  hyperscaler.
- **Commercial AI-governance platforms** (VeriSwarm
  Vault; IBM watsonx.governance audit features;
  sector-specific vendors). Range of implementations;
  programs should verify the specific cryptographic
  claims rather than relying on marketing.
- **Blockchain-backed ledgers.** Public verifiability
  at the cost of higher latency and operational
  complexity; relevant for contexts where public
  verifiability is itself the requirement, rare for
  typical enterprise AI.
- **Roll-your-own** using RFC 9162 directly plus
  standard cryptographic libraries. Full control,
  highest ongoing maintenance cost.

Exercise 03 asks you to specify a vendor-agnostic
structural design that any of these implementations
could meet. The exercise is deliberately about the
*design* — the structural requirements the engineering
function will hold the vendor to — not about picking a
vendor.

## Summary

- Merkle trees commit to a set of records via a root
  hash; inclusion and consistency proofs are
  `log₂(n)` size, which makes external verification
  efficient at any scale.
- Hash chains preserve record order within a sequence;
  modifications break the chain and are detectable on
  a linear walk-back.
- Production audit ledgers typically use both: hash
  chains within batches, Merkle trees across batches.
- RFC 9162 (Certificate Transparency v2.0) is the
  mature standard that assembles the structures with
  append-only semantics, signed public commitments,
  witness countersignatures, and monitor roles. It is
  the reference for AI audit ledgers in 2026.
- The pattern provides integrity and inclusion
  guarantees. It does not provide confidentiality,
  record-reflects-reality authenticity, correct
  interpretation, or compliance. Programs that
  confuse the infrastructure for the discipline
  under-invest in the discipline.
- Three honest statements the CAO can make about a
  conformant ledger — see §2.5. Statements that go
  beyond them are overclaims to notice and correct.
