# Velora Threads — Prompt Iteration & Testing Log

This file documents iterative improvement from broad v1.0 prompts to structured v1.1 prompts and the final v1.2 prompts in `PROMPT_LIBRARY.md`.

> **Academic integrity / evidence note:** The observations below are design dry-run observations, not La Trobe Prompt Lab scores. Run each version in Prompt Lab, record the actual score and key output evidence, and commit the update to GitHub. Do not claim a 90+ score unless the tool actually gives that score.

## Testing method

For each prompt, test the same realistic complaint case across versions. Compare: relevance, specificity, factual grounding, output consistency, workflow fit, customer-safety controls, human-review clarity, and editing effort. Save screenshots or copied outputs where your assessment rules allow.

## Score record template

| Prompt | v1.0 Prompt Lab score | v1.1 Prompt Lab score | v1.2 Prompt Lab score | Final selected? |
|---|---:|---:|---:|---|

| 1 | [enter] | [enter] | [enter] | v1.2 if target met |
| 2 | [enter] | [enter] | [enter] | v1.2 if target met |
| 3 | [enter] | [enter] | [enter] | v1.2 if target met |
| 4 | [enter] | [enter] | [enter] | v1.2 if target met |
| 5 | [enter] | [enter] | [enter] | v1.2 if target met |
| 6 | [enter] | [enter] | [enter] | v1.2 if target met |
| 7 | [enter] | [enter] | [enter] | v1.2 if target met |
| 8 | [enter] | [enter] | [enter] | v1.2 if target met |
| 9 | [enter] | [enter] | [enter] | v1.2 if target met |
| 10 | [enter] | [enter] | [enter] | v1.2 if target met |



---

## Prompt 1: Complaint Intake & Structured Extraction

### v1.0 — Initial broad prompt
```text
Summarise this customer complaint and list the important details.
```

**Change status:** Initial version.  
**Dry-run observation:** Output is likely to be readable but inconsistent; it may omit key fields or infer missing facts.  
**Prompt Lab score:** 38/100

### v1.1 — Structured role + context
```text
You are a customer-service analyst at an online clothing store. Extract the order reference, product, complaint type, requested outcome, key dates and missing information from the complaint. Use only information provided and return a bullet list.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** More consistent extraction, but still lacks an explicit unknown-value rule and confidence signal.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** 66.5/100

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to produce a CRM-ready record with fewer unsupported inferences because unknowns, privacy and prompt-injection handling are explicit.  
**Lesson learned:** Structured fields, unknown handling and input boundaries reduce hallucination and make automation easier.  
**Prompt Lab score:** 86.5/100  
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 2: Complaint Category, Priority & Routing

### v1.0 — Initial broad prompt
```text
Classify this customer complaint and decide how urgent it is.
```

**Change status:** Initial version.  
**Dry-run observation:** Priority labels are underspecified, so similar complaints may be routed differently.  
**Prompt Lab score:** 38/100

### v1.1 — Structured role + context
```text
You are a customer-service triage agent for an e-commerce clothing store. Categorise the complaint, assign High/Medium/Low priority and recommend a queue. Explain the reason in one sentence. Do not use demographic characteristics.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Role and categories improve consistency, but High/Medium/Low is still too subjective for risky cases.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** 67/100

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to improve routing consistency through defined categories, P1-P4 rules, JSON output, confidence and mandatory human review.  
**Lesson learned:** Priority must be rule-based, not emotion-based; confidence and fail-safe escalation improve governance.  
**Prompt Lab score:** 90.25/100 
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 3: Missing Information & Clarification Request

### v1.0 — Initial broad prompt
```text
Write a message asking the customer for any missing information.
```

**Change status:** Initial version.  
**Dry-run observation:** Questions may be broad, repetitive or request unnecessary data.  
**Prompt Lab score:** 38/100

### v1.1 — Structured role + context
```text
You are a customer-service agent. Using the complaint record and the information required by our process, ask the customer only for missing information. Ask no more than three concise questions and do not request passwords or payment credentials.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Question count and privacy improve, but the model still needs a rule for when no clarification is required.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** 70.25/100

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to reduce unnecessary back-and-forth by asking only essential questions and returning 'no clarification needed' when appropriate.  
**Lesson learned:** Customer effort falls when clarification is minimal, necessary and privacy-conscious.  
**Prompt Lab score:** 84.25 
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 4: Policy-Constrained Eligibility Check

### v1.0 — Initial broad prompt
```text
Check whether this customer can get a refund or return based on our policy.
```

**Change status:** Initial version.  
**Dry-run observation:** Without strict grounding, the model may use general return-policy knowledge instead of the supplied policy.  
**Prompt Lab score:** 38/100

### v1.1 — Structured role + context
```text
You are a policy assistant. Compare the complaint facts against the policy text provided. State which remedies appear eligible, ineligible or uncertain, and cite the supplied policy wording. Do not invent policy rules.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Policy grounding improves, but remedy status and ambiguity handling need a fixed format and approval boundary.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** 70.25/100

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to reduce policy hallucination by requiring supplied policy evidence, separating supported/not supported/uncertain remedies and blocking final financial approval.  
**Lesson learned:** Policy prompts need source grounding and an explicit 'cannot determine' state.  
**Prompt Lab score:** 86.75/100  
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 5: Resolution Option Recommender

### v1.0 — Initial broad prompt
```text
Suggest the best solution for this customer complaint.
```

**Change status:** Initial version.  
**Dry-run observation:** Recommendations may optimise for goodwill without policy, cost or approval boundaries.  
**Prompt Lab score:** 29/100

### v1.1 — Structured role + context
```text
You are a complaint-resolution assistant. Based on the complaint facts, approved remedies and policy result, recommend up to three resolution options. Rank them and note which require human approval.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Ranking improves usefulness, but trade-offs and repeated failed remedies are not explicitly considered.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** 56.5/100

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to improve first-contact resolution quality by ranking only allowed options and showing customer-effort, cost and approval trade-offs.  
**Lesson learned:** Resolution automation should support, not replace, authorised human decisions on money and exceptions.  
**Prompt Lab score:** 84.25/100  
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 6: Empathetic First-Resolution Response Draft

### v1.0 — Initial broad prompt
```text
Write a polite reply to the customer resolving their complaint.
```

**Change status:** Initial version.  
**Dry-run observation:** Tone may be acceptable but the response can include unsupported promises or inconsistent length.  
**Prompt Lab score:** 41/100

### v1.1 — Structured role + context
```text
You are a Velora Threads customer-service writer. Draft a warm, concise complaint response using only verified facts and the approved resolution. Do not invent timelines or offer extra compensation. Keep it under 170 words.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Response is more usable, but channel length, blame avoidance and final factual self-check are not explicit.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** 79.25/100

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to reduce agent editing and unsupported commitments through verified inputs, length limits, channel rules and a final self-check.  
**Lesson learned:** Customer-facing automation needs both tone controls and factual/commitment controls.  
**Prompt Lab score:** 88.5/100 
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 7: Escalation Decision & Human Handoff Brief

### v1.0 — Initial broad prompt
```text
Decide if this complaint should be escalated and summarise it for a manager.
```

**Change status:** Initial version.  
**Dry-run observation:** Escalation can become subjective because mandatory triggers and uncertainty handling are not defined.  
**Prompt Lab score:** 43.5/100

### v1.1 — Structured role + context
```text
You are an escalation assistant. Use the complaint record, contact history and routing rules to decide Standard or Escalate. Flag safety, fraud, privacy, legal, discrimination and repeated unresolved cases. Provide a short handoff summary.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Risk coverage improves, but the handoff needs a fixed factual structure and conservative uncertainty rule.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** 57.25/100

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to improve safe escalation and reduce customer repetition by using mandatory triggers plus a structured handoff brief.  
**Lesson learned:** Escalation prompts need conservative rules for high-risk uncertainty and a clean handoff format.  
**Prompt Lab score:** 87.25/100 
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 8: Pre-Send Quality & Risk Check

### v1.0 — Initial broad prompt
```text
Check this complaint response for quality before it is sent.
```

**Change status:** Initial version.  
**Dry-run observation:** A simple quality check may say a response is 'good' without finding specific policy/privacy defects.  
**Prompt Lab score:** [enter actual score]

### v1.1 — Structured role + context
```text
You are a quality reviewer. Check the draft complaint response for accuracy, policy consistency, empathy, privacy, clear next steps and unsupported promises. Return Pass or Revise with required edits.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Review is better, but without a scoring threshold the PASS decision may be inconsistent.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** [enter actual score]

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to create a more reliable quality gate through ten explicit criteria, fail-closed rules and a 20-point scoring structure.  
**Lesson learned:** Quality assurance becomes auditable when criteria and pass/block thresholds are explicit.  
**Prompt Lab score:** [enter actual score]  
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 9: Post-Resolution Follow-up & Satisfaction Capture

### v1.0 — Initial broad prompt
```text
Write a follow-up message asking whether the customer is satisfied.
```

**Change status:** Initial version.  
**Dry-run observation:** Message can be sent at the wrong time or to customers who should not receive automated follow-up.  
**Prompt Lab score:** [enter actual score]

### v1.1 — Structured role + context
```text
You are a customer-service follow-up writer. If the resolution is confirmed complete and contact is allowed, send a brief message asking for a 1-5 satisfaction score and inviting the customer to reply if unresolved.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Follow-up is better, but needs opt-out/sensitivity trigger rules and a defined reopen threshold.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** [enter actual score]

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to capture cleaner satisfaction data without premature or inappropriate outreach because completion, permission and sensitivity conditions are explicit.  
**Lesson learned:** Follow-up automation needs trigger conditions, consent controls and a recovery path for low satisfaction.  
**Prompt Lab score:** [enter actual score]  
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


---

## Prompt 10: Complaint Trend & Root-Cause Management Summary

### v1.0 — Initial broad prompt
```text
Analyse these complaints and tell management the main problems.
```

**Change status:** Initial version.  
**Dry-run observation:** Summary may overstate patterns or invent percentages if the dataset is incomplete.  
**Prompt Lab score:** [enter actual score]

### v1.1 — Structured role + context
```text
You are a management analyst. Using only the complaint dataset provided, identify the top complaint categories, repeat-contact drivers, customer-satisfaction risks and three improvement actions. State data limitations and do not invent figures.
```

**Change made:** Added business role, workflow context and a clearer task.  
**Dry-run observation:** Management relevance improves, but observed pattern vs root-cause hypothesis still needs explicit separation.  
**Lesson from v1.1:** More structure improves relevance, but reliable automation needs explicit constraints, output formats and exception handling.  
**Prompt Lab score:** [enter actual score]

### v1.2 — Final high-quality version

The full v1.2 prompt is in `PROMPT_LIBRARY.md`.

**Change made:** Added explicit inputs, decision rules, output structure, constraints, anti-hallucination/privacy controls and human-review triggers.  
**Dry-run observation:** Expected to produce management-ready insights with stronger data integrity because counts, denominators, limitations and hypothesis labels are required.  
**Lesson learned:** Management analysis must distinguish evidence from hypotheses and disclose data quality limits.  
**Prompt Lab score:** [enter actual score]  
**Decision:** Select v1.2 only after its real Prompt Lab result and output quality meet your target.


## Recommended evidence to add before submission

- Screenshot or export of each version's Prompt Lab score where permitted.
- One representative input/output test for each final prompt.
- A short note when a version failed or required manual editing.
- Real GitHub commits made as you test and refine the prompts; do not fabricate dates or results.
- Final decision note explaining why the selected version is strongest for business use.
