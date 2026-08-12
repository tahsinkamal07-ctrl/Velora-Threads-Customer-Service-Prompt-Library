# Velora Threads — AI Complaint Handling Prompt Library

This repository is an assessment portfolio for a consultancy-style AI workflow automation proposal.

## 1. Business context

**Business:** Velora Threads  
**Business field:** E-commerce clothing retail  
**Organisation type:** Mid-sized online clothing store  
**Workflow problem:** Customer complaint handling is time-consuming and can be inconsistent across intake, triage, policy checking, response writing, escalation and follow-up.  
**Primary outcome:** Improve customer satisfaction by making complaint handling faster, more consistent, empathetic, auditable and policy-safe.

## 2. Proposed solution

The proposal is a **10-prompt complaint-handling library** that supports an end-to-end service workflow:

1. Complaint intake and structured extraction
2. Category, priority and routing
3. Missing-information clarification
4. Policy-constrained eligibility check
5. Resolution option recommendation
6. Empathetic customer response draft
7. Escalation and human handoff
8. Pre-send quality and risk check
9. Post-resolution follow-up and CSAT capture
10. Complaint trend and root-cause management summary

The prompts are designed as workflow components rather than isolated chat prompts. They use explicit role/context/task instructions, input placeholders, constraints, output formats, factual-grounding rules, privacy controls, escalation triggers and human-in-the-loop decision points.

## 3. Repository files

```text
velora_threads_prompt_library/
├── README.md
├── PROMPT_LIBRARY.md
└── ITERATION_LOG.md
```

- **PROMPT_LIBRARY.md** — the final 10-prompt library. Every entry contains the five required fields: exact prompt text, intended workflow/task, problem solved, automation potential, and risks/limitations.
- **ITERATION_LOG.md** — v1.0 → v1.1 → v1.2 development evidence, design observations, lessons learned and spaces for real La Trobe Prompt Lab scores.
- **README.md** — business case, workflow, prompt design approach, testing plan, GitHub process and submission checklist.

## 4. Prompt design strategy

The final prompts are intentionally structured to target high prompt-quality criteria:

- clear role and business context
- one specific workflow objective
- named input variables
- explicit rules and constraints
- defined output format
- “unknown / cannot determine” handling instead of guessing
- policy grounding using supplied text
- privacy and data-minimisation controls
- prompt-injection resistance for customer text
- human approval for refunds, compensation, exceptions and high-risk cases
- confidence/escalation signals
- concise customer-facing word limits
- self-checks before final output

This aligns with the assessment emphasis on structured prompting, constraints, business relevance, critical risk evaluation and evidence of iteration.

## 5. Human-in-the-loop model

AI is used to **support** complaint handling, not to replace accountable staff.

**AI can handle:** extraction, classification, drafting, policy comparison, option ranking, handoff summarisation, QA checks, follow-up drafting and management summarisation.

**Human approval remains required for:** financial compensation, refund exceptions, legal/privacy/safety complaints, discrimination allegations, ambiguous policy decisions, high-risk escalation and final response sending during the pilot.

## 6. Expected business value

Suggested management KPIs:

- First Response Time (FRT)
- Average Handling Time (AHT)
- First Contact Resolution (FCR)
- complaint transfer/rerouting rate
- repeat-contact and reopen rate
- policy-compliance/QA pass rate
- escalation accuracy
- agent editing time
- post-resolution Customer Satisfaction (CSAT)
- repeat complaint rate by category

The objective is not simply “faster AI replies”; it is a measurable improvement in customer effort, response consistency and safe resolution quality.

## 7. Main risks and governance

| Risk | Business impact | Control |
|---|---|---|
| Hallucinated facts/policies | Wrong resolution, trust loss | Use supplied data only; UNKNOWN/CANNOT DETERMINE states; QA prompt |
| Privacy exposure | Customer harm/compliance risk | Data minimisation; no credentials; de-identification for analytics |
| Incorrect escalation | Delayed high-risk case or supervisor overload | Rule-based triggers; confidence; human override |
| Unauthorised compensation | Financial loss/inconsistent precedent | AI recommends only; authorised human approves |
| Bias or emotion-based prioritisation | Unfair treatment | No protected-trait inference; emotion alone cannot raise priority |
| Over-reliance on AI | Staff may skip judgement | Human sign-off, audit logs, pilot monitoring |
| Prompt injection in complaints | Model follows malicious customer text | Treat customer content as data, not instructions |

## 8. How to test in La Trobe Prompt Lab

**Important:** These prompts have been engineered to target a strong score, but a 90+ score cannot be honestly guaranteed without running the university's Prompt Lab.

For each prompt:

1. Test v1.0 using the same realistic complaint case.
2. Record the score and save the output.
3. Test v1.1 with the same case.
4. Record the score and note what improved or remained weak.
5. Test v1.2 from `PROMPT_LIBRARY.md`.
6. Record the actual score in `ITERATION_LOG.md`.
7. If v1.2 is below your target, improve only the weak criterion identified by Prompt Lab, retest, and create v1.3.
8. Keep the final version that combines the strongest score with the most usable business output.

Do not optimise for score alone. A high-scoring prompt that invents policy or creates an unsafe customer response is not suitable for the business case.

## 9. Recommended GitHub workflow for genuine iteration evidence

Create a repository such as:

`velora-threads-ai-complaint-library`

Suggested real workflow:

```bash
git init
git add README.md ITERATION_LOG.md PROMPT_LIBRARY.md
git commit -m "Set up complaint handling prompt library"

# After each genuine test/refinement session:
git add .
git commit -m "Test prompt 1 v1.0 and record findings"

git add .
git commit -m "Refine prompt 1 to v1.1 with role and context"

git add .
git commit -m "Refine prompt 1 to v1.2 with constraints and QA"
```

Repeat as you genuinely test and refine the other prompts. The purpose is to create a traceable development record, not artificial commit history.

## 10. Suggested consultancy pitch structure

A 5–7 minute management presentation can follow this sequence:

1. **Set the scene** — consultant role, e-commerce clothing context.
2. **Purpose and positioning** — complaint inconsistency and customer-satisfaction problem.
3. **AI opportunity and solution** — introduce the 10-prompt workflow.
4. **Prompt design strategy** — structured prompting, chaining, constraints and governance.
5. **Illustrative examples** — demonstrate 2–3 representative prompts.
6. **Impact and business value** — FRT, AHT, FCR, CSAT, reopens, QA.
7. **Risks and responsible use** — hallucination, privacy, bias, escalation, human oversight.
8. **Recommendation** — pilot the library in a supervised complaint queue, measure outcomes, then expand only if quality targets are met.

## 11. Suggested prompts to demonstrate in the video

Use these three because they show different parts of the value chain:

- **Prompt 2: Category, Priority & Routing** — shows speed and workflow automation.
- **Prompt 6: Empathetic First-Resolution Response** — shows direct customer-satisfaction value.
- **Prompt 8: Pre-Send Quality & Risk Check** — shows governance and responsible AI.

Together they demonstrate operational value, customer experience and risk control.

## 12. Management recommendation

Run a **4-week supervised pilot** in one complaint queue. Keep human approval before send, compare the AI-assisted group with the existing process, and measure first-response time, average handling time, first-contact resolution, QA error rate, repeat contacts and post-resolution CSAT. Expand only if service quality and risk controls remain acceptable.

## 13. Submission checklist

- [ ] All 10 prompts included
- [ ] Exact prompt text shown, not just descriptions
- [ ] Intended workflow/task documented for every prompt
- [ ] Problem being solved documented in business language
- [ ] Automation potential and human-in-the-loop role stated
- [ ] Specific risks, limitations and mitigations included
- [ ] At least two genuine iterations tested per prompt
- [ ] Actual Prompt Lab scores/results added
- [ ] GitHub commit history shows real iteration
- [ ] Portfolio link is accessible
- [ ] 5–7 minute consultancy pitch recorded
- [ ] Pitch speaks to business value, measurement and governance
- [ ] Clear recommendation and next step included

## 14. Academic-use note

The business name and scenario are fictional. Replace or expand assumptions if your lecturer requires a real company context. Any Prompt Lab scores, model outputs, testing times or performance results submitted as evidence should be your actual results from your own testing.
