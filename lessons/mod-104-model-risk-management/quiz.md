# Module 104 — Quiz

Twenty questions. Answer key in the paired solutions repo.

---

## Section A — What SR 11-7 actually requires (Chapter 1)

**Q1.** SR 11-7 identifies **two** sources of model risk.
Which?

  a. Fundamental error and misuse
  b. Fundamental error and adversarial attack
  c. Misuse and regulatory non-compliance
  d. Adversarial attack and data quality

**Q2.** Which of the following is **not** one of SR 11-7's
four pillars of an MRM framework?

  a. Robust model development, implementation, and use
  b. Sound model validation processes
  c. Strong governance, policies, and controls
  d. Independent third-party audit firm engagement

**Q3.** Short answer: in one sentence, explain why
attempting to define a system out of "model" scope to
avoid MRM is described as a losing strategy.

**Q4.** Which line of defense does SR 11-7 place the MRM
function in?

  a. First
  b. Second
  c. Third
  d. Fourth

---

## Section B — Tiering ML models (Chapter 2)

**Q5.** Which of the following is **not** a property of a
defensible tiering scheme?

  a. Reflects real differences in model risk
  b. Applies consistently across the portfolio
  c. Always uses three tiers
  d. Produces reproducible classifications

**Q6.** Which ML-specific consideration is mentioned in
Chapter 2 as a possible additional tiering input?

  a. Number of model parameters
  b. Model size / inscrutability
  c. Programming language used
  d. Vendor pricing

**Q7.** True or false: "Tiering everything as Tier 1 to be
safe" is described as a defensible conservative posture.

---

## Section C — Independent validation (Chapter 3)

**Q8.** Which of the following is **explicitly identified
as one of the four elements of validation** in SR 11-7 §IV?

  a. Challenger model construction
  b. Evaluation of conceptual soundness
  c. Vendor third-party attestation
  d. Production traffic logging

**Q9.** Which validation pattern is described in Chapter 3
as "often the only valid approach for LLM outputs with no
automatic ground truth"?

  a. Counterfactual evaluation
  b. Subgroup validation
  c. Human evaluation by domain experts
  d. Out-of-distribution testing

**Q10.** Short answer: in one sentence, state the
*independence test* from Chapter 3 for validation
personnel.

**Q11.** Which of these is described as a **material
change** that triggers re-validation for LLM systems,
beyond the classical triggers?

  a. New customer onboarding
  b. Prompt template change
  c. Server hardware upgrade
  d. Marketing campaign launch

---

## Section D — The model lifecycle (Chapter 4)

**Q12.** Which two lifecycle stops does Chapter 4
identify as "most often skipped"?

  a. Concept approval and data acquisition
  b. Implementation review and retirement
  c. Development and use
  d. Validation and ongoing monitoring

**Q13.** Short answer: in one sentence, describe why
*implementation review* matters more for ML systems than
classical models.

---

## Section E — Inventory for LLMs (Chapter 5)

**Q14.** Which of the following is **not** a field the
chapter identifies as missing from the classical
inventory template for LLM-class systems?

  a. Foundation-model version pinning
  b. Prompt template version
  c. Retrieval corpus / RAG index description
  d. Model developer's academic affiliation

**Q15.** True or false: a vendor's evaluation of its
foundation model is sufficient as the firm's validation
record for the LLM-based system.

---

## Section F — CAO × MRM boundary (Chapter 6)

**Q16.** Which of these is described as a **collision
pattern** that fails?

  a. Joint validation expectations between CAO and MRM
  b. Cross-referenced inventories that point to each other
  c. Re-validation of MRM-validated models by the CAO
     function
  d. Joint regulator briefings

**Q17.** Which of the following is owned by **MRM**, not
the CAO function?

  a. The AI risk taxonomy
  b. Independent validation of models within MRM scope
  c. The AI risk register
  d. AI vendor and ecosystem risk

**Q18.** Short answer: in two sentences, describe one
example of the *intersection* between CAO and MRM scope
and how it can be operated cleanly.

---

## Section G — MRM outside banking + comprehensive (Chapter 7 + cross)

**Q19.** Which adaptation is described as closest from
banking MRM to insurance?

  a. The MRM committee architecture is unchanged
  b. The actuarial-validation function is the natural
     MRM home
  c. The challenger-model paradigm maps directly
  d. The 21-page document length

**Q20.** True or false: SR 11-7's *misuse* framing
applies directly to industrial AI deployments where
operators use AI beyond the validated operational
envelope.
