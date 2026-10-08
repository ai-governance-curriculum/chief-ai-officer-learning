# Chapter 2 — Control Mapping

## Why this chapter exists

Every obligation in the obligations register from
[`mod-102`](../mod-102-regulatory-landscape/README.md)
has one of two fates: it becomes a **control** that the
program operates against, or it becomes a liability the
program carries without knowing it. The discipline that
determines which is **control mapping** — turning an
abstract regulatory requirement into a specific,
testable, continuously-operating activity with a named
owner, a cadence, and evidence.

Done well, the map is the program's source of truth for
what it actually does. Done badly, the map is
wallpaper: a document that satisfies no one in the room
and does not help the operator who has to answer the
regulator's question. This chapter teaches the
discipline that produces the first kind of map and
avoids the second.

## 2.1 The six-element control specification

A control map is not an obligations list. It is a
structured specification. A complete entry has six
elements:

- **Obligation** — the specific regulatory text or
  framework requirement being satisfied. Cite the
  article, section, or control-objective reference.
  *"EU AI Act Art. 9(2)(a)"* is a reference;
  *"compliance with the AI Act"* is not.
- **Control** — the operating activity that satisfies
  the obligation. Written as a *verb-phrase describing
  work that is done* ("maintain the AI system
  inventory", "review bias metrics against thresholds
  weekly"), not a noun-phrase describing a document or
  a committee.
- **Evidence** — the artifacts produced *when* the
  control operates. Named artifacts the auditor can
  request. If asking "what would an auditor sample?"
  does not produce a concrete answer, the evidence row
  is incomplete.
- **Owner** — the role accountable for the control
  operating. A named role, not a function or a
  committee. "The CAO function" is a function; "AI
  Risk Lead" is a role; the second is the owner.
- **Cadence** — how often the control operates.
  Weekly / monthly / per-event / on-change. "As
  needed" is not a cadence.
- **Test** — how the program verifies the control
  operates. Who samples what, how often. Without a
  test, the control might be operating or not; no one
  can tell.

A control missing any of the six elements is
incomplete. Programs with partial controls routinely
produce evidence packages that auditors cannot connect
back to obligations: the obligation references point to
controls that do not quite describe what the evidence
shows, or vice versa. Partial controls fail at the
seams.

## 2.2 The granularity problem

Control maps have the same granularity failure mode as
event vocabularies (see [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)
Chapter 3 §3.1):

- **Under-granular.** One control covers many
  obligations. When a specific challenge to compliance
  arrives — "show us the activity that satisfies
  Art. 9(2)(b) in particular" — the map cannot answer.
  The control is so broad that it does not actually
  describe anything the program does on a given day.
- **Over-granular.** Hundreds of controls, each
  covering a sliver. No one can hold the map in their
  head. Auditors get lost. Owners don't know how many
  controls they own. The map becomes a document to be
  maintained rather than operated against.

The right granularity: **one control per
operationally-distinguishable activity**. If two
obligations are satisfied by the same operating
activity — same evidence, same owner, same cadence,
same test — they are one control covering two
obligations. If two obligations require materially
different activities, they are separate controls, even
if the controls are related.

A working rule-of-thumb for the catalog size: a mature
CAO program typically operates **30–80 AI-specific
controls**, mapped against several hundred
obligations. Maps smaller than ~20 controls usually
under-cover; maps larger than ~150 controls usually
over-granularise. These are indicative ranges, not
limits.

## 2.3 The crosswalk pattern

Many regulations have overlapping requirements. EU AI
Act Art. 9 risk management overlaps with NIST AI RMF
MANAGE function which overlaps with ISO/IEC 42001 §8
(operational planning and control). SR 11-7 §V model
inventory overlaps with ISO/IEC 42001 §A.6.1 AI system
inventory overlaps with NIST AI RMF GOVERN-1.6.

The discipline: **build one control that satisfies all
overlapping obligations**, and cross-reference the
obligations in the control's documentation.

The crosswalk pattern keeps the control catalog small
and the operation coherent. Programs that build one
control per regulation end up with three controls doing
the same thing — producing three sets of similar
evidence, owned by three roles, on three cadences. The
first time all three regulators show up in the same
quarter, the program discovers its triplication the
hard way.

Published crosswalks you can lean on in 2026:

- The **NIST AI RMF Playbook** includes crosswalks to
  ISO/IEC 42001 and to parts of the EU AI Act.
- **ISO/IEC 42001 Annex A** controls map onto NIST AI
  RMF sub-functions via community-maintained
  crosswalks.
- Sector regulators increasingly publish their own
  mappings (e.g., NYDFS Part 500 §500.09 risk
  assessment maps cleanly to ISO 42001 Annex A impact
  assessment).

Use these as starting points. Where the published
crosswalk disagrees with your reading of the source
text, trust the source. Cross-walks are secondary
artifacts.

## 2.4 A worked control specification

A working control specification, in the form the
module's exercises will ask you to produce:

```
Control ID:  HVN-CTL-007
Name:        AI-system inventory currency
Owner:       CAO function — AI Risk Lead

Obligations satisfied:
  - EU AI Act Art. 6 (high-risk classification scope) —
    requires identification of systems in scope
  - ISO/IEC 42001 §6.1 + Annex A.6.1 — AI system
    inventory
  - NIST AI RMF GOVERN-1.6 — AI system inventory
  - SR 11-7 §V — model inventory
  - NYDFS Part 500 §500.13 — asset inventory (overlay)

Activity:
  - Maintain master AI inventory in <inventory system>
  - Quarterly business-unit attestation that the
    inventory is current
  - Monthly automated reconciliation against
    deployed-system telemetry
  - On-change update on material system event

Evidence produced:
  - Quarterly signed attestation per business unit
  - Monthly reconciliation report
  - On-change inventory event in the audit ledger

Cadence:
  - Monthly automated reconciliation
  - Quarterly business-unit attestation
  - On-change inventory event

Test:
  - Internal audit quarterly samples inventory entries
    against deployed systems
  - Annual external sampling during ISO 42001 audit
```

The example shows the discipline: one control covers
five separate obligations with one coherent operating
activity. The evidence section names concrete artifacts.
The owner is a role, not a function. The cadence
specifies three distinct rhythms (monthly, quarterly,
on-change) because the activity has three distinct
rhythms. The test specifies two testers at two
cadences.

Programs with controls at this specification level
produce small, defensible catalogs. Programs with
controls at *"AI inventory is maintained"* level
produce catalogs that cannot survive examination.

## 2.5 What is *not* a control

Three honest distinctions. Each is a conflation that
has cost a working CAO program at some point.

- **A policy is not a control.** *"AI policy requires
  that bias is monitored"* is the **source of
  authority** for a control — not the control itself.
  The control is the operating activity that satisfies
  the policy. Programs that list their policies as
  controls produce catalogs that fail at audit sampling
  — the auditor asks for evidence of the control
  operating, and there is only a policy document.
- **An aspiration is not a control.** *"We will improve
  our bias monitoring"* is not a control; the actual
  bias-monitoring activity is. Programs with
  aspirations-as-controls fail at the first evidence
  request where the aspiration has not become a
  concrete activity.
- **An organisational structure is not a control.** *"We
  have an AI Risk Council"* is not a control; the
  Council's decisions and review activities are. The
  Council itself is the organisational container in
  which controls operate. Programs that treat the
  existence of a committee as a control fail at the
  first regulator question about what the committee
  *does*.

A control is **work that someone does on a schedule,
that produces evidence, that someone else can test.**
Policies, aspirations, and committees enable controls;
they are not controls.

## 2.6 Mapping an obligation step by step

A repeatable procedure for turning an obligation into
a control:

1. **Read the source text literally.** Not a summary.
   The source paragraph says what it says. If you are
   working from a vendor summary of EU AI Act Art. 9,
   go to the Regulation text itself and read the
   article in context (and its recitals).
2. **Identify the active verbs.** What does the
   regulation require the organisation to *do*?
   "Identify", "estimate", "evaluate", "adopt
   measures". These verbs are the shape of the control.
3. **Decide the operationally-distinguishable scope.**
   Does this obligation require activity that is
   distinct from what you already do for other
   obligations? If yes, it is a separate control. If
   no, it joins an existing control via the crosswalk
   pattern.
4. **Specify the six elements.** Fill in obligation,
   control, evidence, owner, cadence, test — all six.
   If any element is "to be determined", the control
   is not yet usable.
5. **Walk the control through its first cycle.** Does
   the specified owner have the authority and
   information to operate the control? Does the
   evidence land in a place where the test can sample
   it? If either answer is no, the control is specified
   but not viable.
6. **Register the control.** Add it to the catalog
   with a stable ID. Register the obligation-to-
   control mapping. Both the catalog and the mapping
   are themselves evidence.

Exercise 01 walks EU AI Act Art. 9 through this
procedure for a specific firm. The exercise is where
the discipline becomes muscle memory.

## 2.7 Maintaining the catalog

A control map is a living document. Three triggers
that should produce a catalog update:

- **A regulation changes.** EU AI Act delegated acts,
  NIST AI RMF Playbook revisions, state-level AI law
  enactments. The obligations register (mod-102)
  signals the change; the catalog is where it lands.
- **A control fails.** A control fires but produces
  the wrong evidence, or an audit finds a gap. The
  catalog's test row and sometimes its activity row
  need to update.
- **The organisation changes.** A reorg moves roles;
  a new business unit comes under the AI program; an
  acquisition brings new systems. Owners and scope
  update.

Programs that treat the catalog as a once-a-year
document discover drift at the next audit. The
catalog needs the same operational cadence it
specifies for the controls it describes. See Chapter 3
for the cadence pattern.

## Summary

- A control map is a six-element specification:
  obligation, control, evidence, owner, cadence, test.
  Any missing element is a seam at which the map
  fails.
- Granularity is the subtle failure mode. One control
  per operationally-distinguishable activity; a mature
  catalog is typically 30–80 controls, not 15 and not
  300.
- Overlapping obligations map to **one control** with
  cross-referenced obligations. The crosswalk pattern
  keeps the catalog small and the operation coherent.
- Policies, aspirations, and organisational structures
  are **not controls** — they enable controls. Programs
  that confuse the layers produce catalogs that fail at
  evidence sampling.
- Mapping is a repeatable six-step procedure. Exercise
  01 walks EU AI Act Art. 9 through the procedure.
- The catalog itself needs an operational cadence;
  regulations, control failures, and organisational
  changes trigger updates.
