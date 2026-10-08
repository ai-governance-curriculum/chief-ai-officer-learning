# Chapter 3 — Identity and Capability Scoping

## Why this chapter exists

Identity and capability are the two questions a trust
architecture must answer *before* it allows an agent to
act. Chapter 1 named them as two of the three composable
questions; Chapter 2 named composite identity as one of
the three places NIST SP 800-207 needs adaptation. This
chapter does the construction: how to specify identity
for an AI agent, how to express what the agent is
permitted to do, and how to make both verifiable at the
trust gate in a few milliseconds.

The chapter leans on existing standards — W3C Verifiable
Credentials, JWT/JOSE, OAuth 2.1 — rather than invent
new ones. The standards are mature and interoperable;
the discipline is in *using* them well, not in authoring
replacements. Exercise 03 forces authoring a manifest
against this discipline for the Tessera agent.

## 3.1 Agent identity — the composite model

For an AI agent, identity is **composite**: it consists
of several attributes that together specify what the
runtime trust gate is being asked to authorise. A
working composite identity includes:

| Attribute | What it specifies | Standard / pattern |
|---|---|---|
| **Model identity** | Which underlying model is being invoked | Vendor identifier + model version string |
| **Configuration identity** | What system prompt, tool set, and memory the agent is running with | Configuration hash; prompt-template version |
| **Principal** | On whose behalf the agent is acting | OAuth identity / OIDC identity / service principal |
| **Delegation chain** | If the principal authorised an agent, which delegations are in effect | Verifiable credential chain |
| **Session** | Which interaction this operation is part of | Session identifier; cryptographically bound to principal |
| **Origin** | Where the operation request came from | Network origin; client attestation |

A working trust architecture binds these together
cryptographically. The agent presents a token (often a
JWT) that names all relevant attributes and is signed
by an authority the gate trusts.

Why composite rather than monolithic? Three reasons.

1. **Each attribute has a different authority.** The
   model identity is attested by the model vendor; the
   configuration identity by the deploying team; the
   principal by the identity provider. Collapsing them
   loses the ability to say which authority is making
   which claim.
2. **Each attribute has a different lifetime.** The
   model version is stable across many sessions; the
   configuration may update on each deployment; the
   principal is per-user; the session is per-
   interaction. Collapsing them forces a single
   lifetime that fits none of the underlying facts.
3. **Each attribute is independently revocable.** If
   the model vendor rotates signing keys, model
   attestations must re-issue — without touching the
   principal's authority. If the principal revokes the
   agent, delegation credentials expire — without
   touching the model attestation. Composite identity
   makes these revocations independent.

Different practitioner patterns compose the attributes
differently:

- **OAuth 2.1 + JWT** for the principal layer; the
  agent acts as a confidential client with delegated
  authority via a token bound to the principal.
  Mature, interoperable; the baseline.
- **W3C Verifiable Credentials** for the delegation
  chain; the principal issues a VC that names the
  agent's permitted capabilities, the agent presents
  the VC at each operation. The right choice when
  delegations are multi-party or multi-hop.
- **Agent passports** (term used by several
  practitioners — VeriSwarm Passport, IBM watsonx
  trust IDs, others) — a single signed document that
  packages all identity attributes into one verifiable
  artifact. Convenient; carries vendor-capture risk
  if the passport format is proprietary.
- **Roll-your-own** with mTLS for transport, signed
  JWTs for identity, and a service-side capability
  registry. Works, requires more maintenance, is
  often the right choice for firms with existing
  OIDC infrastructure.

There is no single right pattern. Choosing among them
is the subject of Exercise 03 and Chapter 6 of this
module.

## 3.2 Capability scoping

Capability is the question *what is this agent
permitted to do*. Capability scoping is the discipline
of expressing capabilities precisely enough that the
trust gate can evaluate them, and not so broadly that
the scope is meaningless.

A working capability scope includes:

- **Action type.** What kind of operation is being
  authorised (read, write, invoke, send, submit).
- **Resource.** Which specific resource the action is
  on. Not "the API" — the specific endpoint and
  method.
- **Constraints.** Any conditions on the action
  (amount limits, recipient restrictions, time
  windows, counterparty restrictions).
- **Delegation depth.** Can the agent delegate this
  capability further to sub-agents, and if so, how
  deep?
- **Audit obligation.** What must be logged when this
  capability is exercised, beyond the standard trust
  decision log.

Capability scopes should be:

- **Bounded.** "Can read customer data" is too broad;
  "can read customer records for the authenticated
  principal in the customer-service context" is
  scope-appropriate for a customer-service agent.
- **Verifiable.** The trust gate must be able to
  decide *yes* or *no* deterministically given the
  capability scope and the operation request. If the
  gate needs to call out to a human, the scope was
  under-specified.
- **Short-lived.** Capability assertions should
  expire. "This agent has capability X" without an
  expiration is a standing-privilege pattern that
  800-207 explicitly disfavours. Minutes-to-hours is
  the right default; days-and-weeks is a smell.

### 3.2.1 Capability-scope anti-patterns

Four scopes that look specific but are not:

| Anti-pattern | Why it fails |
|---|---|
| `banking:*` | Wildcards defeat the point of scoping. If the gate must authorise every banking operation under this scope, the scope has not constrained anything |
| `read:all-customers` | Breadth without purpose. A legitimate customer-service agent needs to read the current customer's data, not all customers |
| `transfer:any-amount` | No constraints. Legitimate operations have envelopes; a scope without limits is a scope that cannot be enforced proportionate to risk |
| `admin` | A category, not a capability. "Admin" means "all admin-labelled operations"; the gate cannot decide anything useful from it |

The test: can a developer, reading the capability
scope, enumerate the specific set of (action, resource,
constraint) tuples it authorises? If not, the scope is
not operationally sufficient.

## 3.3 Signed capability manifests

The practitioner pattern that works: a **signed
manifest** that declares the agent's identity,
permitted capabilities, and the authorising principal.
The manifest is:

- Issued by a trusted authority (the principal, or a
  delegated administrator acting on the principal's
  behalf).
- Signed cryptographically (ES256, RS256, or Ed25519
  are the common choices; Ed25519 is the current
  default for new designs).
- Short-lived (minutes to hours, depending on stakes).
- Presented at each operation; verified at the trust
  gate.
- Revocable via a revocation list, JWKS rotation, or
  token-binding scheme.

### 3.3.1 A worked example — JWT-shaped capability manifest

A JWT-shaped manifest for the Tessera customer-service
agent, operating on behalf of a specific customer. The
JWT payload after decoding (signatures and headers
elided for brevity):

```json
{
  "iss": "https://identity.tessera.example/v1",
  "sub": {
    "agent_instance_id": "agent-cs-7f3a9c",
    "model_id": "vendor-x/claude-sonnet-4-6",
    "config_hash": "sha256:7a2b...",
    "deployment_id": "cs-prod-2026-10"
  },
  "aud": "https://gates.tessera.example",
  "iat": 1759900000,
  "exp": 1759900900,
  "jti": "mft-01HE9...",
  "principal": {
    "sub": "cust-882131",
    "idp": "https://idp.tessera.example",
    "session_id": "sess-01HE9...",
    "auth_time": 1759899800,
    "amr": ["pwd", "otp"]
  },
  "capabilities": [
    {
      "action": "read",
      "resource": "accounts:self",
      "constraints": {
        "principal_match": "sub"
      }
    },
    {
      "action": "transfer",
      "resource": "accounts:self",
      "constraints": {
        "from_owner": "sub",
        "to_owner": "sub",
        "amount_max_usd": 5000,
        "count_max_per_day": 3
      }
    },
    {
      "action": "dispute:create",
      "resource": "transactions:self",
      "constraints": {
        "principal_match": "sub"
      }
    }
  ],
  "delegation_depth": 0,
  "audit": {
    "log_level": "detailed",
    "required_events": ["authn", "authz", "action"]
  }
}
```

Several points worth naming:

- The `sub` claim is a **structured object**, not a
  string. The composite identity (§3.1) is expressed
  by giving each attribute a field.
- The `principal` block separates the user's identity
  (`sub`, `idp`, `auth_time`, `amr`) from the agent's
  identity. A gate can tell *who authorised the
  agent* independently from *who the agent is*.
- Each capability names its `action`, `resource`, and
  `constraints`. The constraints are machine-
  evaluable: `amount_max_usd: 5000` is a specific
  check the gate performs against the operation
  parameters.
- `delegation_depth: 0` disallows sub-agent
  delegation for this manifest. Explicit zero is
  safer than omission.
- `exp` is 15 minutes after `iat`. Fresh manifests
  are issued per session; revocation is largely
  implicit.
- `jti` is a unique identifier that enables precise
  revocation (adding `jti` to a deny-list) if a
  specific manifest must be invalidated before `exp`.

The pattern maps cleanly to W3C Verifiable Credentials
if a VC envelope is required (for cross-firm
delegation, or for regulator-presentable audit trails).
A VC version would move the `principal` claims into a
VC chain and sign the whole with the issuer's DID.

### 3.3.2 Verification at the trust gate

The verification function the gate performs for each
manifest. Pseudocode:

```
function verify_manifest(manifest, current_time, operation, gate_context):
    # Step 1: Signature
    if not verify_signature(manifest, issuer_jwks(manifest.iss)):
        return DENY, "bad_signature"

    # Step 2: Audience
    if gate_context.audience not in manifest.aud:
        return DENY, "wrong_audience"

    # Step 3: Expiration (and not-before, if present)
    if current_time >= manifest.exp:
        return DENY, "expired"
    if current_time < manifest.iat:
        return DENY, "not_yet_valid"

    # Step 4: Revocation
    if revocation_list.contains(manifest.jti):
        return DENY, "revoked"

    # Step 5: Delegation chain (if present)
    if manifest.delegation_chain:
        for hop in manifest.delegation_chain:
            if not verify_signature(hop, issuer_jwks(hop.iss)):
                return DENY, "delegation_chain_broken"
            if current_time >= hop.exp:
                return DENY, "delegation_hop_expired"

    # Step 6: Capability match
    for cap in manifest.capabilities:
        if matches(cap, operation):
            if constraints_satisfied(cap.constraints, operation, manifest):
                return ALLOW, "ok"
            else:
                return STEP_UP, "constraint_mismatch"

    return DENY, "no_capability"
```

Six verification steps. A gate that implements fewer is
not verifying the manifest; it is accepting it. Note
that the function returns a *reason* with every
decision — the reason is what makes the gate's decision
inspectable after the fact.

## 3.4 The revocation problem

The hardest practical problem in agent identity:
revocation. When something goes wrong (compromise,
policy change, principal revokes authority), the trust
architecture must stop honouring the agent's existing
capability assertions. Several patterns in use, each
with trade-offs:

| Pattern | How revocation works | Latency to effect | Cost |
|---|---|---|---|
| **Short-lived tokens** | Capabilities expire quickly; revocation is implicit (stop renewing) | Up to the token lifetime | Low |
| **Active revocation list** | Gate consults a deny-list of `jti` values before authorising | Immediate once list updated | Moderate (list availability + freshness) |
| **Per-operation re-attestation** | Each operation fetches a fresh attestation; revocation propagates at next operation | Immediate | High (latency, availability dependency) |
| **Token binding + session kill** | Token bound to a session; killing the session invalidates the token | Immediate once session kill propagates | Moderate (session infrastructure) |

A working architecture **combines** these. Short-lived
tokens for routine operations (balance inquiries,
message composition); active revocation-list checks for
high-stakes operations (transfers, disputes);
per-operation re-attestation for catastrophic-action
operations (payments to external parties, bulk
customer messaging).

The revocation path is often the single most under-
specified part of agent trust architectures. A design
that explains how authorisation works but is silent on
how to *remove* authorisation is not operationally
complete. Where the next incident forces a revocation,
the architecture must be ready; a program that
discovers at incident time that revocation takes 48
hours to propagate has already failed.

## 3.5 Multi-agent delegation

A more advanced case: an agent that delegates part of
its work to a sub-agent. A planning agent, for example,
may invoke a specialised retrieval agent, which in turn
invokes a specialised summarisation agent.

Three design choices to make:

1. **Delegation depth.** How many hops deep can
   capability flow? Zero (no delegation), one (one
   sub-agent allowed), or N. Deeper chains are harder
   to reason about and audit.
2. **Capability attenuation.** When a parent agent
   delegates to a sub-agent, must the sub-agent's
   capabilities be a *strict subset* of the parent's?
   The 800-207 discipline says yes — delegation should
   not expand authority. Enforce in the gate.
3. **Audit obligation inheritance.** When a sub-agent
   acts, is the audit obligation that of the parent, or
   does it attach to the sub-agent's manifest? For
   regulator-presentable systems, the audit chain must
   be reconstructible; this usually means both.

The pattern that works: each hop in the delegation
chain is a signed credential citing the parent's
`jti`, with the sub-agent's capabilities being an
attenuation of the parent's. The gate verifies the
chain end-to-end before authorising the leaf
operation. W3C Verifiable Credentials with chained
holder-presenter semantics is a clean fit; multi-hop
JWT delegation also works but typically requires more
custom code at the gate.

Exercise 03 asks you to author the manifest format
for a one-hop case (customer → agent). For deeper
chains, the pattern extends but the discipline — bind
cryptographically, attenuate capabilities, verify end-
to-end — is the same.

## Summary

- Agent identity is composite: model, configuration,
  principal, delegation chain, session, origin. A
  working architecture binds the attributes
  cryptographically into one presentable artifact.
- Capability scoping must be bounded, verifiable, and
  short-lived. Wildcards and category labels are
  anti-patterns; a scope that cannot be enumerated by
  a developer is not operationally sufficient.
- Signed manifests (JWT-shaped or VC-shaped) are the
  practitioner pattern that works. The verification
  function has six steps — signature, audience,
  expiration, revocation, delegation chain, capability
  match — and must return a reason with every decision.
- Revocation is the under-specified part of most agent
  architectures. Combine short-lived tokens, active
  revocation lists, and per-operation re-attestation
  according to the operation's blast radius.
- Multi-agent delegation extends the pattern: enforce
  depth limits, require capability attenuation, carry
  the audit chain end-to-end.
