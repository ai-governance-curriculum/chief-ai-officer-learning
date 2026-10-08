# Chapter 3 — Year 2: The Consolidation Arc

## Why this chapter exists

Year 2 is the year the CAO function stops
*building* and starts *operating*. The shift
sounds unremarkable in the abstract and is
in practice the hardest year of the three.
Everything year 1 produced is now under
operating pressure. The appetite statement
has to actually constrain decisions. The
inventory has to actually be maintained. The
incident response machinery has to actually
respond to incidents. The boundaries with MRM,
CISO, and Compliance have to actually hold
when a specific case tests them.

Year 2 is also when the first material
incident almost always arrives — and when it
does, the program's year-1 foundation gets
tested in public.

The chapter maps the six things year 2 should
accomplish, the specific year-2 trap of trying
to fix every year-1 error at once, the first-
material-incident discipline, and the year-2
self-assessment pattern that honestly closes
the arc.

## 3.1 What year 2 should accomplish

Six workstreams, in roughly this order.

### 3.1.1 Operate the controls at cadence

The continuous-evidence cadence from
[`mod-109`](../mod-109-compliance-operations/README.md)
Chapter 3 becomes real in year 2. Monthly
AI Risk Council reviews consume live
evidence. The audit ledger
([`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md))
accumulates records in production rather
than as a backfill exercise. The trust
architecture monitoring
([`mod-106`](../mod-106-trust-architecture/README.md))
produces operational signals the function
acts on, not dashboards no one reads.

Year 1 built the controls. Year 2 runs them.

### 3.1.2 Close the year-1 gaps

Most of the gaps the year-1 self-assessment
surfaced are closed in year 2. Not all —
some will defer to year 3 for defensible
reasons — but the material ones. The
year-2 program review (Exercise 02) is
substantively a tracking document for which
year-1 gaps closed, which deferred, and why.

### 3.1.3 Mature the program

Program maturity — assessed per
[`mod-111`](../mod-111-board-reporting/README.md)
Chapter 6 §6.1.1 against the practitioner
CMMI-style levels commonly applied to NIST AI
RMF functions — progresses from mostly
**Developing** across functions to mostly
**Defined**. The progression is specific, not
uniform: some functions mature faster than
others. GOVERN and MANAGE often mature first;
MEASURE sometimes lags because the measurement
infrastructure takes longer to produce useful
signal.

A year 2 that ends with every function at the
same maturity level is almost certainly
over-rated on the laggards. Honest maturity
progression is uneven.

### 3.1.4 Integrate cross-LOB or cross-function

The patterns that worked in one business unit
or function in year 1 extend to others in
year 2. The hub-and-spoke or federated
operating model from Chapter 1 produces its
first substantial cross-unit output in year
2: the shared taxonomy, the shared impact
assessment template, the shared incident
response machinery, now being used across
multiple spokes.

The specific risk in year 2 is **shared-form
drift** — business units that were given the
year-1 templates have adapted them locally,
and the adaptations are now diverging. Part
of year 2 is reconciling the adaptations
back to a shared baseline or formally
accepting them as business-unit-specific
variants.

### 3.1.5 Build the second tier of the team

Roles that support the year-1 hires. From
Chapter 6 §6.2, the second-tier roles are
typically:

- Deputy AI Risk Lead (succession track).
- Algorithm Validation Lead (MRM-adjacent
  partnership role).
- Trust Architecture Lead (engineering, cross-
  CISO partnership).
- Communications / Board Lead (board
  engagement specialty, if the function has
  grown enough to warrant it).

The second-tier hires are what let the
year-1 hires start doing work the CAO was
doing in year 1, and what let the CAO start
doing work the function needs them to do in
year 3 (see Chapter 4).

### 3.1.6 Handle the first material incident credibly

Most programs face their first material AI
incident in year 2. The incident might be a
model-behaviour event (bias finding at a
regulator-noticeable scale, a hallucination
in a customer-facing system that reaches
media), a vendor event (a vendor LLM swap
without notification per
[`mod-104`](../mod-104-model-risk-management/README.md)
Ex-04), a security event (a prompt-injection
success per
[`mod-107`](../mod-107-ai-security/README.md)),
or a compliance event (a NYDFS §500.17-grade
cybersecurity event with AI involvement). The
specific trigger varies; the fact of a first
material incident in year 2 is nearly
universal.

The year-1 foundation is what gets tested.
The response machinery operates. The single
named lead per
[`mod-110`](../mod-110-incident-response/README.md)
is named within the first hour. The
notification matrix fires on time. The
post-incident review per
[`mod-110`](../mod-110-incident-response/README.md)
§6 produces substantive findings.

Credible handling of the first material
incident establishes the program's reputation
for several years. Mishandling it costs
roughly the same several years to recover
from. Chapter §3.4 covers the specific
discipline.

## 3.2 The consolidation discipline

Year 2 is where the CAO function moves from
"building" to "operating". The posture shift
is specific:

- **Resist the temptation to start new
  initiatives.** Year 1's foundation needs to
  consolidate before year 2 can sustain new
  workstreams. The CAO who in month 14
  announces three new programs is distracting
  from the consolidation that year 2 is
  supposed to produce. New initiatives mostly
  wait for year 3.
- **Honor the standards you authored.** Year
  1's standards become real in year 2 because
  cases arrive that test them. The pressure
  to relax a standard under business pressure
  — a specific product launch slipping the
  tier-1 bar; a vendor exception on
  defense-in-depth; a transparency carveout
  for a regulated communication — surfaces
  in year 2. Resisting that pressure, or
  granting the exception on documented
  grounds with a time-bound re-review, is
  the year-2 work. Granting silently is drift.
- **Use the evidence.** The evidence layer
  from
  [`mod-108`](../mod-108-audit-ledgers-and-evidence/README.md)
  starts producing patterns in year 2.
  Reviewing it monthly in the AI Risk
  Council — not to audit the function, but to
  surface signals — is where year-1 investment
  starts paying back.
- **Refine, don't rebuild.** Year 1's
  structures will be imperfect. The impact
  assessment template leaves gaps; the tiering
  rubric produces edge cases; the appetite
  statement has categories that didn't
  anticipate specific scenarios. Year 2
  refines them with amendments and
  clarifications; rebuilding is year-3 work
  at the earliest. The discipline is naming
  which refinements the function is making
  deliberately rather than drifting into them.

## 3.3 The year-2 trap

A specific failure mode: the program in year
2 discovers that some year-1 choices were
wrong and tries to fix them comprehensively.
The year-2 self-assessment then looks
suspiciously similar to the year-1
self-assessment — the program is "building"
again rather than "operating".

The trap is intelligible. Year-1 choices made
without operating evidence will turn out wrong
in a predictable fraction of cases. The
appetite statement had a category that didn't
anticipate what actually arrived. The tiering
rubric placed too many systems at Tier 1 and
the review bandwidth collapsed. The hiring
sequence under-weighted vendor-risk
specialisation. The reaction to realising
year-1 choices were wrong is to re-plan
year 1 all over again.

The discipline:

- **Name year-1 errors specifically.** Not "the
  program needs restructuring" — "the appetite
  statement category X doesn't cover scenarios
  of type Y and should be amended in Q3". The
  specificity constrains the fix to a bounded
  change.
- **Fix the most material ones.** Not all
  year-1 errors are equal. The two or three
  that materially impair year-2 operation
  get fixed in year 2; the others get
  documented as year-3 work.
- **Explicitly defer the rest.** The deferred
  items go into a "known-weak" register that
  the AI Risk Council and board can see. The
  function knows what it hasn't fixed, which
  is a different posture from either denying
  the error or trying to fix everything.

Programs that try to fix every year-1 error
in year 2 end year 2 with a renovated
foundation and no operating history. Programs
that fix the material errors and document the
rest end year 2 with a slightly imperfect
foundation and substantial operating history.
The second is what the board needs.

## 3.4 The first material incident

The first material incident in year 2 is a
test the year-1 foundation was built for.
Three specific aspects of handling it:

### 3.4.1 Treat the incident as the test

The response team shouldn't try to prove the
program works by over-performing. Operating
the response per the playbook from
[`mod-110`](../mod-110-incident-response/README.md)
— single named lead within an hour, the
notification matrix firing on its SLA, the
containment decisions documented, the
post-incident review conducted on timeline —
is what the test looks like. A response team
that improvises because "the playbook doesn't
quite fit" is the symptom of a playbook that
year-1 built badly, not an argument for
improvisation.

### 3.4.2 Honour the notification matrix in both directions

The notification matrix from
[`mod-110`](../mod-110-incident-response/README.md)
Chapter 4 names what external notifications
fire on what thresholds — SEC 8-K Item 1.05,
NYDFS §500.17, GDPR Articles 33 and 34, EU AI
Act Article 73, state insurance regulator
notifications, and so on. The pressure in a
first material incident is to under-notify
(deciding the incident is not quite over the
threshold yet). The year-1 foundation is what
makes the matrix defensible: the regulator who
later reviews the response finds the matrix
was in place and the thresholds were set
honestly in advance.

A corollary: the matrix should not be *invented
during the incident*. If year 1 did not
produce the matrix, year 2 produces the first
notification matrix in the middle of a
compressed decision window — which almost
guarantees it will be re-written again in the
calmer period after the incident. Year 1
produces it under working conditions; year 2
operates it under incident conditions.

### 3.4.3 Produce a substantive post-incident review

The post-incident review per
[`mod-110`](../mod-110-incident-response/README.md)
§6 is the year-2 program's most important
artifact. It is read by the board, by the
regulator, by internal audit, and (if the
review discipline becomes known as substantive)
by peer institutions. A superficial review
that papers over findings is the single most
common reason first-material-incident
responses hurt the program's long-term
credibility more than they help. See
[`mod-110`](../mod-110-incident-response/README.md)
§6.2 on the *what worked* discipline — a
review of only failures is less useful and
less credible than one that specifies both.

## 3.5 The end-of-year-2 self-assessment

The year-2 self-assessment is the most
important of the three. It is the first
self-assessment the program has operating
history behind. The expectations:

- **Maturity progression specified function
  by function.** Not "the program improved
  across the board" but "GOVERN moved from
  Developing to Defined; MANAGE moved from
  Developing to Defined; MEASURE remained
  mostly Developing with specific gaps X,
  Y, Z". The function-by-function detail is
  what makes the self-assessment honest.
- **Year-1 gaps closed enumerated.** Not just
  "most year-1 gaps closed" — the specific
  gaps, closed or deferred, with the
  decision for each.
- **First material incident response named.**
  The incident, the response, the
  post-incident review findings, the
  improvements routed into the program's
  improvement backlog.
- **Cross-LOB integration state.** Specific
  state of the shared-form drift from §3.1.4
  — reconciled or formally variant.
- **One or two honest findings about the CAO
  function itself.** A year-2 self-assessment
  that names only external factors (business
  pressure, resource constraints) and no
  internal findings is almost certainly not
  self-assessing honestly. See
  [`mod-111`](../mod-111-board-reporting/README.md)
  §6 on the peer-CAO honesty test.

If the year-2 self-assessment cannot show
these, the program is stalling at year-2
levels, which is the next chapter's subject.

## Summary

- Year 2 shifts from building to operating.
  Six workstreams — operate the controls,
  close year-1 gaps, mature the program,
  cross-unit integration, build second-tier
  team, handle the first material incident.
- The consolidation discipline: resist new
  initiatives, honour the standards, use
  the evidence, refine rather than rebuild.
- The year-2 trap: trying to fix every
  year-1 error at once. Fix the material
  ones, document the rest, maintain
  operating history.
- The first material incident is the test
  the year-1 foundation was built for.
  Operate the response per the playbook;
  honour the notification matrix; produce a
  substantive post-incident review.
- The year-2 self-assessment shows function-
  by-function maturity progression, year-1
  gaps closed or deferred, the incident
  response, cross-unit integration state,
  and at least one honest finding about
  the CAO function itself.
