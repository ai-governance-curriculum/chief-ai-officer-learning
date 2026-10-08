# Chapter 4 — Evidence Packages

## Why this chapter exists

Chapters 1–3 built the capability to generate
trustworthy records at the right granularity, stored
in a ledger with cryptographic integrity properties.
A regulator or auditor who asks for evidence does not
want ledger access. They want an **evidence package**:
a curated, signed, self-contained artifact that
answers their specific question.

This chapter is the operational discipline of
producing those packages. It is the most consequential
chapter in the module in day-to-day terms — most CAO
programs will spend more time producing evidence
packages than designing ledgers.

## 4.1 Why packages, not raw ledger access

Three reasons to produce curated packages rather than
grant raw access to the ledger.

**Scope.** Auditors and regulators ask specific
questions. "Please provide evidence that System X
operated within scope Y during period Z." Raw access
produces noise and leaves scope definition to the
audience; curated packages produce signal and
constrain the question to the one that was asked. A
package that answers the specific question is more
useful to the audience than access to everything.

**Confidentiality.** The ledger may contain
information the audience is not entitled to —
information about operations outside the audience's
scope, information involving third parties, trade-
secret system configuration. Granting raw access
inverts the default: everything is disclosed unless
the audience chooses not to look. Packages invert the
default back: nothing is disclosed except what is
in scope.

**Verifiability.** Packages are signed and timestamped
at production. The audience receives an artifact with
provenance — the program committed to this bundle of
evidence at this moment, with these signatures.
Granting raw access gives the audience a query result
that may change if they query again later; packages
freeze the response.

The package is also an artifact of the chain of
custody discipline (Chapter 5 §5.3). Raw access has
no chain of custody at all.

## 4.2 What goes in a package

A complete evidence package includes:

- **Cover document.** What question this package
  answers, who requested it, when it was produced,
  the identifier of the request, the point of
  contact.
- **Scope statement.** What is in scope and what is
  not. The audience should be able to read this
  section and know precisely what claims the
  package makes and does not make.
- **Evidence records.** The relevant events from the
  ledger — the facts the package is actually
  presenting.
- **Inclusion proofs.** Cryptographic proofs that each
  evidence record is in the ledger (Chapter 2 §2.1).
  Without these the records are claims; with them
  they are verifiable claims.
- **Consistency proof.** A proof that the ledger
  state at package production is consistent with
  prior signed ledger states — specifically, with
  the sealed commitments the program has previously
  published. Without this, the package is proof the
  records are in *a* ledger; with it, the package is
  proof the records are in *the* ledger the program
  has been operating.
- **Supporting artifacts.** Model identity
  attestations, manifest snapshots, policy versions,
  configuration references that the evidence
  records point to by hash. The audience should not
  need to request additional artifacts to verify or
  interpret the package.
- **Chain of custody.** The production and handling
  history of the package itself. Who produced it,
  from which systems, with which keys, through which
  internal review.
- **Verification protocol.** The steps the audience
  can take to verify the package. This is
  deliberately a *section of the package*, not a
  separate document.
- **Package signature.** A cryptographic signature by
  the program over the entire package. One signature
  that commits to the whole bundle.

A package missing any of these has a corresponding
weakness the audience can name specifically.

## 4.3 Common evidence-package use cases

Six common package types the CAO program should
expect to produce:

| Use case | Audience | Typical scope |
|---|---|---|
| Regulator inquiry response | EU AI Act authority, OCC, FDA, state insurance regulators | Specific operations or time period named by the regulator |
| Customer adverse-action explanation | Customer (or customer's counsel) | The specific decision affecting that customer |
| Internal audit sampling | Internal audit | Statistical sample of operations in the audit scope |
| Insurance claim | Cyber or professional-liability carrier | Operations relevant to the claim |
| Litigation discovery | Counsel and opposing party | Court-defined scope, often broad |
| Board quarterly | Board Risk Committee | Aggregate program metrics with exceptions |

Each has different completeness, confidentiality, and
format requirements. A regulator inquiry package is
typically narrower and more defensively-written than
an internal audit package; a litigation discovery
package is typically broader and more thoroughly
reviewed by counsel before release. The discipline is
treating each use case as its own design problem
rather than one-size-fits-all.

## 4.4 Pre-built templates vs ad hoc assembly

The most common evidence packages should be **pre-
designed templates**, not assembled from scratch each
time. Programs that assemble each package ad hoc
spend regulatory-deadline time on package
construction. Programs with templates spend the same
time on review and sign-off.

Standard template categories:

- **Regulator quarterly attestations.** Pre-built;
  the content refreshes automatically on a cadence;
  signed monthly or quarterly and held ready.
- **Adverse-action explanation packages.** Pre-built;
  produced automatically per adverse decision from
  the lineage of the decision in the ledger. The
  volume makes ad hoc assembly infeasible.
- **Annual SOC 2 / ISO 42001 evidence sets.** Pre-
  built per the audit framework's control catalog;
  updated as controls evolve.
- **EU AI Act Art. 12 logging-compliance evidence.**
  Pre-built; produced on demand against the Article's
  specific requirements.
- **Litigation-hold evidence sets** per matter type.
  Pre-built templates for the categories of matter
  the firm has historically faced.

Ad hoc construction is reserved for genuinely unusual
inquiries that do not fit a template. A program whose
templates cover 80%+ of inquiries can treat the
remaining 20% carefully; a program with no templates
treats every inquiry as a fire drill.

## 4.5 The verification protocol

A working evidence package includes the specific steps
the audience must take to verify it. The protocol is
not a courtesy — it is the operational artifact that
closes the loop between the cryptographic structure
Chapter 2 described and the audience's ability to act
on it.

The standard protocol:

1. **Verify the package's outer signature.** Confirm
   that the package as received was signed by the
   program, by the expected signing key, and that the
   signature covers the entire package.
2. **Verify each evidence record's inclusion proof.**
   Confirm, for each record in the package, that its
   hash is included in the Merkle tree whose root is
   named in the package. This is the Chapter 2 §2.1
   check applied to each record.
3. **Verify the ledger consistency proof.** Confirm
   the ledger state at package production is a
   strict extension of prior signed ledger states
   (sealed commitments) the audience may already
   have.
4. **Verify timestamps on supporting attestations.**
   Confirm RFC 3161 TSA timestamps on sealed
   commitments and on individual records where
   applicable. See Chapter 5 §5.2.
5. **Verify the chain of custody.** Confirm the
   package was handled appropriately between
   production and receipt — the handoffs match the
   custody record.

The protocol is documented *in the package itself*,
in plain language, with the specific cryptographic
operations stated. Audiences who do not perform the
verification have the option; audiences who want to
perform it should not need to assemble the protocol
from the standards. Programs that fail to document
the protocol are signalling, intentionally or not,
that the verification is not expected.

## 4.6 Honest treatment of adverse findings

A specific temptation at package production time:
the records show something unflattering — a monitor
that fired but was not actioned promptly, an
authorisation decision that in retrospect looks
questionable, a configuration change made outside
normal process. The temptation is to narrow the
scope of the package so these records fall just
outside.

The discipline is the opposite. A package that
honestly surfaces an unflattering fact *and
references the program's response to it* is
materially stronger with regulators than a package
that excludes the fact. The response is often the
evidence that the program is functioning: the
monitor fired, the Review Board convened, the
corrective action was taken.

A package that excludes something the regulator
later discovers independently converts a routine
inquiry into an investigation. The honest package
is both the ethical choice and — on any realistic
risk calculation — the lower-risk one.

Exercise 02's reference solution deliberately
includes a threshold crossing during the period of
inquiry; the exercise is where this discipline
becomes concrete.

## Summary

- Evidence packages are the operational artifact
  programs produce in response to specific
  requests. They are preferred to raw ledger access
  on three grounds: scope, confidentiality, and
  verifiability.
- A complete package contains cover, scope,
  evidence records, inclusion proofs, a consistency
  proof, supporting artifacts, chain of custody,
  verification protocol, and an outer package
  signature.
- Common use cases include regulator inquiry
  response, adverse-action explanation, internal
  audit sampling, insurance claims, litigation
  discovery, and board quarterly reporting. Each
  has distinct expectations.
- The highest-volume package types should be pre-
  built templates; ad hoc assembly is reserved for
  genuinely novel inquiries.
- Verification protocols belong inside the package,
  in plain language, with the cryptographic steps
  stated. Audiences who verify get the full
  assurance of the Chapter 2 pattern; audiences who
  do not retain the option.
- Honest surfacing of adverse findings — with the
  program's response — is both the ethical and the
  lower-risk choice. Packages that narrow scope to
  hide awkward records convert routine inquiries
  into investigations.
