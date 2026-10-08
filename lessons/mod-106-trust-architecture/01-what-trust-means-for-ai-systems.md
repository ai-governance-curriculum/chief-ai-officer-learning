# Chapter 1 — What "Trust" Means for AI Systems

## Why this chapter exists

"Trust" is a metaphor we borrow from human relationships
and apply, often loosely, to AI systems. For operational
purposes the metaphor is unhelpful: humans extend trust
based on context, history, and intuition; AI systems do
not have any of those, and reasoning *as if they did*
produces designs that do not survive contact with
production.

The discipline of trust architecture begins by replacing
the metaphor with operational definitions. A CAO who can
hold the operational definitions in mind — and keep the
program's conversations with CISO, CTO, and the board
anchored there — avoids most of the common governance
pathologies in this space. Everything in later chapters
assumes the vocabulary this chapter establishes.

Exercise 01 forces the vocabulary against a concrete
agent (Tessera Bank's customer-service agent). This
chapter is written so that Exercise 01 is executable
from it, together with Chapter 2.

## 1.1 Two senses of "trust" in AI systems

When practitioners talk about trust in AI systems, they
usually mean one of two things. The two senses are
related, but they are not the same, and conflating them
produces governance documents that talk about agent
identity in the same breath as fairness — which is not
coherent.

**Sense A — Trust as a property of the system.**
*"Can we trust this AI?"* In this sense, the question is
whether the system reliably produces outputs the
organisation can defend. It is the question NIST AI RMF,
ISO/IEC 42001, and the EU AI Act all address. **This
sense of trust is the subject of mod-101 through
mod-105**; it is *not* the subject of this module.

**Sense B — Trust as a runtime authorisation question.**
*"Should this agent be allowed to do this thing on
behalf of this principal right now?"* In this sense, the
question is about identity (who is this agent),
capability (what is it permitted to do), and context
(under what conditions). **This sense of trust is the
subject of mod-106.**

An organisation that cannot do (B) operationally will
have a harder time demonstrating (A) at the program
level. The CAO cares about both. Trust architecture is
how (B) gets built.

## 1.2 Operational trust as three composable questions

For any AI agent operation, trust architecture asks
three composable questions:

1. **Identity.** Is this agent who it claims to be?
2. **Capability.** Is this agent permitted to perform
   this operation? On behalf of which principal? Within
   what scope?
3. **Context.** Do current conditions support performing
   this operation? Has anything in the agent's
   environment changed in ways that should alter the
   decision?

These three are *separable* — a system can be strong on
identity and weak on capability, or strong on both but
unable to evaluate context. A working trust architecture
addresses all three.

A worked walkthrough. A customer-service agent attempts
to initiate a $4,900 funds transfer from a customer's
checking account to their savings account. The runtime
trust decision decomposes:

| Question | What is being evaluated |
|---|---|
| Identity | Is this the agent instance the authorising principal issued credentials to? Signed JWT presented at the operation; signature verified; freshness within token lifetime; revocation list consulted |
| Capability | Does this agent's capability manifest include `transfer:intra-customer:$5000:3-per-day`? Is this transfer within that envelope? Scope evaluated against the operation parameters |
| Context | Is the originating session cryptographically bound to the customer principal? Is the amount within normal pattern for this customer? Has the agent's deployed configuration changed since the capability was issued? Any posture signals in the last window? |

A gate that answers all three questions *yes* authorises
the operation. A gate that answers *no* to any one of
them does not — and the reason the gate said *no* must
be inspectable, because it will be examined after the
fact.

## 1.3 What this is not

Honest distinctions. Trust architecture overlaps with
several adjacent disciplines, and programs that
collapse the overlap end up with incoherent artifacts.

- **Trust architecture is not safety.** Safety asks
  whether the system's catastrophic failure modes are
  bounded. Trust architecture asks whether routine
  operations are authorised. The two interact — a
  safety-critical system should fail its authorisation
  gates closed — but the disciplines are distinct.
- **Trust architecture is not security.** Security (in
  the CISO sense) defends against adversaries. Trust
  architecture authorises non-adversarial agents. The
  two interact heavily — mod-107 treats this — but
  they are distinct disciplines. Security without a
  trust architecture is defending a boundary that no
  one has specified; trust architecture without
  security is specifying permissions no one is
  enforcing.
- **Trust architecture is not the model.** The model
  is what the agent runs on. The agent is what the
  trust architecture authorises. A program that
  conflates them ends up trying to authorise model
  weights, which is incoherent — weights do not
  originate operations, agents do.
- **Trust architecture is not the ledger.** A
  tamper-evident audit ledger (mod-108) records what
  happened. Trust architecture decides what is
  *allowed to happen*. They are complementary
  artifacts; a program that has one without the other
  has either an un-auditable gate or an audit trail of
  decisions no one controlled.

The test: for any trust-architecture claim, name the
runtime operation it governs. If the claim does not
map to an operation, the claim is probably in Sense A,
not Sense B — important work, but someone else's
module.

## 1.4 Why this matters for the CAO

The CAO does not typically *build* trust architecture
— that is a CISO + CTO + CIO partnership. The CAO's
job is to:

- **Know what good looks like.** A proposal that
  cannot answer the three composable questions for its
  high-stakes operations is not a trust architecture.
- **Set the program-level requirements.** What
  regulatory defensibility must the architecture
  support? What audit evidence does the program need?
  What AI-program constraints must the architecture
  respect?
- **Recognise when an architecture is operationally
  inadequate.** A design that authorises based on
  shared secrets, treats "the agent" as a single
  static identity, or has no revocation path is
  inadequate — regardless of whose logo is on it.
- **Hold the vocabulary.** A board conversation about
  AI trust that mixes "customers trust us" (Sense A)
  with "the agent authenticates per request" (Sense B)
  is a conversation that goes nowhere. The CAO is the
  one who separates them.

A CAO who can read an architecture proposal and
identify whether identity, capability, and context are
separable in the design is doing the job. A CAO who
can also name the operations the architecture does
*not* govern — and defend the scoping decision — is
doing it well.

## 1.5 The vocabulary this module uses

For readers coming from governance or policy backgrounds
rather than engineering, a short glossary of the terms
used throughout this module:

| Term | Meaning in this module |
|---|---|
| **Agent** | A software system that takes actions on behalf of a principal, often (but not necessarily) driven by an LLM. Agents originate operations |
| **Principal** | The identity on whose behalf an agent acts — a human customer, an employee, the firm as a legal person, a service account |
| **Operation** | A single action an agent attempts (read, write, invoke a tool, send a message). Trust architecture authorises operations |
| **Resource** | Anything the agent operates against — a database, an internal API, an email service, a model endpoint, a payment rail |
| **Capability** | A specific thing the agent is permitted to do, scoped tightly enough that a gate can evaluate it deterministically |
| **Attestation** | A signed statement about an identity or capability, verifiable without contacting the issuer at runtime |
| **Trust gate** | The runtime component that evaluates the three composable questions and allows / denies / escalates the operation |
| **Trust score** | A quantification of trust along one or more axes, used as input to a gate's decision logic |
| **Blast radius** | The scope of consequences if an operation turns out to be unauthorised. The headline metric for prioritising gate design |

If a passage uses one of these words in a sense that
does not fit the glossary, that is a drafting bug —
file an issue.

## Summary

- There are two senses of trust in AI. Sense A (system
  properties) is governed by mod-101 through mod-105;
  Sense B (runtime authorisation) is this module.
- Operational trust decomposes into three composable
  questions — identity, capability, context. A working
  architecture addresses all three separately.
- Trust architecture is not safety, security, the
  model, or the ledger. It overlaps with each; it is
  identical with none.
- The CAO does not build trust architecture; the CAO
  specifies what it must do, recognises inadequate
  designs, and holds the vocabulary.
- The module's working glossary — agent, principal,
  operation, resource, capability, attestation, trust
  gate, trust score, blast radius — is the vocabulary
  for the rest of the chapters. Later chapters assume
  it.
