# Chapter 5 — Retention, Sealing, and Chain of Custody

## Why this chapter exists

A working evidence layer is not just the ledger
infrastructure (Chapter 2) and the vocabulary that
populates it (Chapter 3). It is also the
organisational practice around the ledger over time.
Three disciplines carry that practice: **retention**
(how long records are kept), **sealing** (how
periods are committed to externally), and **chain of
custody** (how evidence is handled from emission to
delivery).

Each discipline is where programs collapse under
adversarial review. The cryptographic layer is often
the strongest layer; the organisational layer is
where opposing counsel, auditors, and regulators find
their footholds. The CAO's attention to this chapter
is time well-spent — the engineering function will
not provide these answers unprompted.

## 5.1 Retention

Retention is *how long* evidence must be kept.
Sources of retention obligation include:

- **Regulatory.** EU AI Act Art. 12 requires high-
  risk-system logs for at least 6 months, longer if
  other EU law specifies. US banking regulators'
  SR 11-7-aligned expectations are typically 5–7
  years for materials supporting model-risk
  decisions. State insurance regulators vary. FDA
  SaMD guidance expects records across the system's
  useful life plus a tail. CFPB adverse-action
  documentation sits on top of the ECOA framework's
  retention expectations.
- **Litigation hold.** Active or reasonably-
  anticipated litigation may require retention
  beyond the regulatory minimum. The duty to
  preserve attaches when litigation is reasonably
  foreseeable, not only when it is filed; working
  programs have a process for recognising the
  trigger.
- **Internal policy.** Programs may choose longer
  retention to support lessons-learned, trend
  analysis, model-risk re-validation, or incident
  retrospection. This is a legitimate choice but
  should be made explicitly, not drifted into.

A working retention policy combines all three with
explicit reasoning per evidence category. The
output is a table that answers, for each category of
evidence, *how long* it is kept, *why*, and *what
happens at the end of the period*.

### 5.1.1 Why "keep forever" is wrong

Retention is *not* "keep forever." Keeping more than
needed is itself a risk:

- **Privacy exposure.** Records involving customers,
  employees, or third parties create ongoing
  obligations under GDPR, CCPA, and sector privacy
  rules. The right-to-erasure framework has a
  compliance carve-out for records retained for
  legitimate purposes; indefinite retention
  undermines the legitimacy claim.
- **Breach exposure.** Evidence stored indefinitely
  is evidence available to a future breach. The
  breach's blast radius is the volume of retained
  records.
- **Litigation exposure.** Records kept beyond the
  retention policy become discoverable in ways the
  program may not want. "Why do you still have this?"
  is a question with no good answer.
- **Operational cost.** Retention has infrastructure
  cost — storage, backup, index maintenance, sealing
  continuity. At enterprise scale this is non-
  trivial.

A retention policy sets explicit end-of-period
treatment: deletion, archival to cold storage with
reduced sealing cadence, aggregation to retention-
preserving summaries. The policy is itself an
evidence category — the records of what was kept and
what was disposed of, and why.

### 5.1.2 Common retention durations as of 2026

Illustrative, not prescriptive — programs should
validate each duration against their specific
sources:

| Source | Typical retention |
|---|---|
| EU AI Act Art. 12 | 6 months minimum; longer if other EU law applies |
| GDPR (where evidence contains personal data) | "No longer than necessary" — typically 5–7 years for financial-services AI evidence under the legitimate-purpose carve-out |
| US banking SR 11-7-related | 5–7 years typical |
| FDA SaMD | Across the system's useful life + 2 years |
| State insurance | Varies by state; typically 5–10 years |
| SEC (Advisers Act, where applicable) | 5 years; some records longer |
| FINRA (where applicable) | 3–6 years depending on record type |

The CAO's job is not to memorise these but to ensure
every evidence category in the program has an
explicit, source-cited retention duration in the
policy and an operational pathway that honours it.

## 5.2 Sealing

Sealing is the practice of *finalising* an evidence
epoch — committing publicly to the ledger's contents
at a specific moment, in a way that subsequent
modifications become detectable to anyone who has
observed the seal.

The working pattern: at the end of each defined
epoch (typically daily, sometimes sub-daily for
high-stakes systems), the program produces a **sealed
commitment** — a signed statement of the Merkle root
at that moment, countersigned by independent
witnesses, with an external **RFC 3161 Time-Stamp
Authority** countersignature establishing the time of
the seal independently of any party under program
control. The seal is itself appended to the ledger as
an event.

### 5.2.1 Why external timestamping matters

A seal signed only by the program carries the
program's own guarantee that it happened at time T.
Opposing counsel can argue that the program
backdated the signature. An external TSA signature,
produced by an independent authority that neither
party controls, closes this attack. The TSA's
signature means: "This hash existed by time T, where
T is a timestamp I generated with my own clock and
signing key."

RFC 3161 is the governing standard. Multiple
independent TSAs exist; programs should use at least
one, and for the most sensitive seals (annual
closes, regulatory evidence submissions) more than
one. The redundancy is cheap and the independence of
the TSAs becomes material if any one is later
compromised or discredited.

### 5.2.2 Operational benefits of sealing

Sealing has three operational benefits beyond the
cryptographic property:

- **Independent verification.** The seal can be
  published to a public channel (an external
  transparency log, a notarised archive, a public
  bucket with versioning). External parties can
  confirm the program's commitments without
  trusting the program.
- **Tampering detection at the seal boundary.** Even
  sophisticated ledger compromise becomes
  detectable when the seal is checked. An attacker
  who gets inside the program's ledger
  infrastructure cannot alter sealed epochs without
  the alteration being externally visible.
- **Audit reference.** When the auditor asks "what
  was the ledger state at date D?", the seal at D
  is the authoritative answer. Without seals, the
  question has to be answered from the current
  state of the ledger, which is weaker.

### 5.2.3 Seal failure response

What happens if sealing fails on a given day? The
policy must answer this. Working patterns:

- The failure is itself recorded as an event in the
  next successful seal.
- The window during which seals were missed is
  explicitly identified in subsequent audits.
- The program's response — root-cause analysis,
  remediation — is itself evidence.
- Repeated seal failures escalate to the CAO and
  through to the Board Risk Committee.

A program that silently misses seals and does not
notice has an evidence layer that is theatre.

## 5.3 Chain of custody

Chain of custody is the documented history of who
handled a piece of evidence between its emission and
its delivery to an audience. The discipline is
particularly important in litigation contexts, where
chain-of-custody breaks can cause evidence to be
challenged or excluded. In regulatory contexts, it
provides positive assurance that the program
produced the evidence rather than fabricating it.

A working chain-of-custody record for a given piece
of evidence captures:

- The system that emitted the evidence (and its
  attestation).
- The signing key used (and its lifecycle state at
  the time of signing).
- Any intermediate handling — export from the
  ledger, transfer to a staging area, inclusion in
  a package, review by named individuals.
- The recipients and the timestamps of each
  transfer.
- The final delivery, with recipient acknowledgment.

Each transfer should be signed by both the
transferor and the recipient. The chain of custody
itself becomes an auditable record, often included
as a section of the evidence package it accompanies
(Chapter 4 §4.2).

### 5.3.1 Common chain-of-custody failures

Four failure modes recur across industries:

- **Email transmission of evidence.** Email is not a
  controlled channel. Headers can be forged; messages
  can be edited after delivery by anyone with inbox
  access; delivery is not reliably acknowledged. A
  chain of custody that terminates in "sent via
  email" is weaker than one that terminates in "made
  available through a documented portal with
  recipient acknowledgment." Transmit through
  controlled channels; use email only to notify the
  recipient the artifact is available.
- **Email forwarding by the recipient.** Even when
  the program delivers evidence as a signed
  attachment, recipients routinely forward the body
  content with the file omitted. The signature covers
  the file; forwarded body text is just text.
  Programs should instruct recipients explicitly to
  forward the file, not the message content.
- **Casual handling of leftover copies.** Recipients
  of evidence make copies — for internal review, for
  external counsel, for archive. Chain of custody
  ends at the official recipient. What happens
  afterward is the recipient's chain of custody, not
  the program's. The program should name this
  boundary explicitly in the package's custody
  section.
- **Key-rotation gaps.** If the signing key used to
  sign evidence is rotated and the old key is
  destroyed without the chain of custody recording
  the signing key's lifecycle, subsequent verifiers
  cannot confirm the signature's validity at the
  time of signing. The program should preserve
  historical signing-key metadata (certificate,
  issuer, lifecycle) with the chain of custody.

### 5.3.2 Chain of custody as a cultural practice

The failure modes above have a common root: chain of
custody is often treated as a document to produce
rather than a practice to perform. Programs with
strong chain of custody treat each handoff as a
small ceremony — the transferor confirms what they
are transferring and to whom; the recipient
acknowledges what they received; both actions are
recorded. The ceremony is modest and takes seconds
when the tooling supports it, but it is the thing
that holds up under adversarial scrutiny.

## Summary

- Retention is set per evidence category by three
  overlapping sources — regulatory, litigation
  hold, internal policy — with explicit reasoning
  and explicit end-of-period treatment. "Keep
  forever" is wrong on privacy, breach, litigation,
  and cost grounds.
- Sealing commits publicly to ledger epochs. The
  working pattern is daily sealing with multiple
  independent witness signatures and RFC 3161 TSA
  timestamping; failed seals are themselves
  recorded and the response is evidence.
- External timestamping via RFC 3161 provides time
  provenance independent of the program; it closes
  the "the program backdated the seal" attack and
  is cheap enough that multiple independent TSAs
  are the right posture for the most sensitive
  seals.
- Chain of custody records who handled evidence at
  every stage from emission to delivery; each
  handoff is signed by both parties; the record is
  usually included in the evidence package that
  accompanies it.
- Four recurrent chain-of-custody failures: email
  transmission; email forwarding of body rather
  than file; casual handling of leftover copies;
  signing-key lifecycle gaps. Each has a specific
  policy and tooling response.
- The deeper point: retention, sealing, and chain
  of custody are the organisational practices
  around the cryptographic ledger. The
  cryptography does not substitute for them; it
  only enables them. Programs that over-invest in
  the ledger and under-invest here fail under
  adversarial review.
