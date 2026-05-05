# UHY AI Clarity Program

## Student Demo Handout



### **How to use this handout**

This handout contains every prompt that will be demoed during the session. Copy any prompt below and paste it into Copilot to follow along. Each demo lists:

* The file (if any) you'll need to attach when running the prompt
* A short description of what the demo shows
* The prompt itself, in a gray box, you can copy directly

Files referenced in this handout will be distributed separately. The 📎 callout box at the top of each demo tells you which file to attach. The 📄 note below it summarises what's inside that file so you know what you're working with. Demos without a callout don't need a file.

# **Module 1 — Shared Core**

## **Part 1 — Prompting Mechanics**

### **Demo 1 — A vague prompt and what comes back**

The most basic possible version of the request. Run this and notice that the output isn't terrible — but it's also not specific to anything. The notes are pasted directly into the prompt, so no file is needed.

```
Write a memo from these engagement notes.

Met with client CFO and Controller on 3/10. Discussion focused on Q1 revenue recognition. Client mentioned they changed their revenue recognition accounting policy mid-year. Two contracts flagged: Contract A ($2.3M) and Contract B ($1.1M). Controller said they have documentation but couldn't locate it during the call. Also discussed depreciation. They added equipment in Q3, useful life estimate seems aggressive. CFO was not sure who made that determination. Accounts receivable aging shows some old balances, client says they're collectible but no written support. Follow up needed on all of the above.
```

### **Demo 2 — Adding role, task, output structure, and constraints**

The same engagement notes, now wrapped in a properly structured prompt. Compare this output to Demo 1 and notice how the four levers (role framing, task description, output structure, and constraints) change the result.

```
You are a senior auditor at a public accounting firm. I'm going to give you rough engagement notes from a client call during fieldwork. Your task is to convert these notes into a formal client inquiry memo that will be included in the audit workpaper file.

The memo should:
- Be addressed to the client (use "Client Management" as the recipient)
- Be written in professional accounting language, third-person formal tone
- Open with a brief summary paragraph describing the purpose of the call and the date
- Include a clearly labeled section for each topic discussed (Revenue Recognition, Depreciation, Accounts Receivable)
- For each topic, clearly state: (1) what was observed or discussed, (2) what documentation or clarification is requested from the client, and (3) a specific deadline (use "within 10 business days" as the standard)
- Close with a professional sign-off paragraph

Here are the engagement notes:

Met with client CFO and Controller on 3/10. Discussion focused on Q1 revenue recognition. Client mentioned they changed their revenue recognition accounting policy mid-year. Two contracts flagged: Contract A ($2.3M) and Contract B ($1.1M). Controller said they have documentation but couldn't locate it during the call. Also discussed depreciation. They added equipment in Q3, useful life estimate seems aggressive. CFO was not sure who made that determination. Accounts receivable aging shows some old balances, client says they're collectible but no written support. Follow up needed on all items above.
```

### **Demo 3 — Run it together: see non-determinism in action**

Everyone runs this exact prompt at the same time. The outputs will differ across the room — that's the point. Copilot is a probabilistic system, so even a well-structured prompt produces variations on each run. Human verification is always required.

```
You are a senior auditor at a public accounting firm. I'm going to give you rough engagement notes from a follow-up client call during fieldwork. Your task is to convert these notes into a formal client inquiry memo that will be included in the audit workpaper file.

The memo should:
- Be addressed to the client (use "Client Management" as the recipient)
- Be written in professional accounting language, third-person formal tone
- Open with a brief summary paragraph describing the purpose of the call and the date
- Include a clearly labeled section for each topic discussed (Inventory Valuation, Accrued Liabilities)
- For each topic, clearly state: (1) what was observed or discussed, (2) what documentation or clarification is requested from the client, and (3) a specific deadline (use "within 10 business days" as the standard)
- Close with a professional sign-off paragraph

Here are the engagement notes:

Follow-up call with client Accounting Manager on 3/17. Discussion focused on the inventory valuation process. Client mentioned they switched to a new costing method at the start of the fiscal year but couldn't confirm whether the change was documented in the board minutes. Two SKUs flagged as potentially obsolete: Item X (carrying value $480K) and Item Y (carrying value $215K). No formal obsolescence analysis on file. Also discussed accrued liabilities: client has several open vendor invoices from Q4 that haven't been matched. AP clerk was not available during the call. Follow up needed on all items above.
```

## **Part 2 — Catching Hallucinations**

### **Demo 4 — Hallucination mitigation techniques**

A toolkit of four techniques you can apply to any Copilot output. The first three are follow-up prompts you run after the initial response. The fourth is a set of guardrail snippets you add into your prompts upfront.

***Technique 1 — Prompt Interrogation (ask Copilot to show its work)***

```
Walk me through how you arrived at the conclusions in your previous response. What assumptions did you make? What information did you rely on? Are there any parts of your response where you were uncertain or where the answer could vary depending on interpretations I haven't specified?
```

***Technique 2 — Structured Cross-Referencing (challenge a specific claim)***

```
In your previous response, you referenced [specific claim or figure]. Please verify this against only the source material I provided. If this information was not explicitly stated in the source material, tell me so and identify where you may have inferred or assumed it.
```

***Technique 3 — The Adversarial Reviewer (ask it to argue against itself)***

```
Now I want you to act as a skeptical reviewer who is looking for flaws in the analysis you just provided. What are the weakest parts of this analysis? What assumptions might be wrong? What would a professional skeptic challenge? What information would change your conclusion?
```

***Technique 4 — Preventive guardrails to add into your prompts upfront***

Add any of these snippets into a prompt before you run it. They reduce the rate at which Copilot fabricates content.

*Source-only grounding*

```
Base your response exclusively on the information I have provided in this prompt. Do not supplement with external knowledge. If the information I've provided is insufficient to answer part of the question, tell me what's missing rather than filling in the gap.
```

*Confidence flagging*

```
Where you are uncertain or where your response relies on an assumption rather than information I provided, flag that sentence with [UNCERTAIN] so I can review it specifically.
```

*Standards citation caution*

```
Do not reference specific paragraph numbers or sub-sections of accounting standards unless you are certain of the exact reference. If you are not certain, describe the general principle and note that I should verify the specific citation.
```

### **Demo 5 — Verification sequence in practice**

Run these two follow-up prompts on the memo from Demo 2, in the same conversation, one after the other. Watch how Copilot surfaces its own assumptions and pushes back on its own work.

***Step 1 — Interrogate the memo***

```
Walk me through how you arrived at the conclusions in your previous response about the revenue recognition, depreciation, and accounts receivable issues. What assumptions did you make? Were there any parts of the engagement notes where the information was ambiguous or incomplete?
```

***Step 2 — Adversarial review of the memo***

```
Now review the memo you produced as a skeptical senior auditor. What are the three weakest parts of this memo? What would a quality reviewer push back on? What language might be too assertive given the state of the evidence?
```

## **Part 3 — Task Decomposition**

### **Demo 6 — Classifying a workflow into AI-ready steps**

Paste this prompt to ask Copilot to evaluate a seven-step audit workflow and identify which steps are AI-ready, partially AI-ready, or human-only. The workflow is embedded in the prompt — no file needed.

```
I am going to describe a seven-step audit workflow. For each step, tell me: (1) what the input is, (2) what the output is, and (3) whether the step is AI-ready, partially AI-ready, or human-only. Explain your reasoning for each classification.

Here is the workflow:
1. Pull the accounts receivable aging report from the client's system
2. Select a sample of balances to confirm based on risk and materiality
3. Prepare confirmation letters for each selected balance
4. Send letters to the client's customers and log the send date
5. Track responses as they come in and flag non-responses after 10 business days
6. Follow up on non-responses or exceptions identified in responses
7. Document conclusions in the workpaper memo

For human-only steps, explain what specific professional judgment is involved that AI cannot replace.
```

## **Part 4 — Data Cleanup**

### **Demo 7 — Reconciling a chart of accounts from three sources**

| 📎 Files required: ERP_ChartOfAccounts_Export.csv, CFO_Spreadsheet.xlsx, Intercompany_Schedule.xlsx |
| :---- |

> **📄 What's in these files:**
>
> - **`ERP_ChartOfAccounts_Export.csv`** (the master) — A clean chart of accounts export with two columns: `Account Code` and `Account Description`. Should contain ~15–25 standardised accounts with codes (e.g., `6000 — Office Supplies`, `6100 — Travel & Entertainment`, `6200 — Marketing & Advertising`, `7000 — Professional Fees`, `8000 — Intercompany Receivable`).
> - **`CFO_Spreadsheet.xlsx`** — An informal recap built by the CFO. Has an `Account` column with labels written in everyday language (e.g., "Office stuff", "Travel/meals", "Marketing", "Lawyers & consultants"). Some labels match the master cleanly, others are ambiguous, and one or two should look like new accounts not present in the master. Other columns (amounts, periods) can be present but the prompt only references the `Account` column.
> - **`Intercompany_Schedule.xlsx`** — A Q4 intercompany transactions schedule with an `Account Description` column. Should contain a mix of: rows that map cleanly to intercompany accounts in the master, rows whose descriptions are ambiguous, and at least 2–3 rows where the `Account Description` cell is blank. Each row should also have a `Reference` column (e.g., `IC-2024-1112-007`) so unlabelled rows can be located by reviewers.

This demo shows Copilot reconciling messy real-world data against a master record. The guardrail "Do not invent mappings" is what keeps the output safe — without it, Copilot will confidently map ambiguous accounts and you may not notice.

```
You are an accounting analyst helping to standardize a chart of accounts from three different data sources for consolidation.

I have attached three files representing the three sources:
- Source 1 (Master): ERP_ChartOfAccounts_Export.csv — the ERP chart of accounts export. Use this as the master.
- Source 2: CFO_Spreadsheet.xlsx — the CFO's internal recap spreadsheet. The relevant account labels are in the "Account" column.
- Source 3: Intercompany_Schedule.xlsx — the Q4 intercompany transactions schedule. The relevant account labels are in the "Account Description" column. Note that some rows have no account label populated.

Your tasks are:
1. Map each account from Sources 2 and 3 to its corresponding account in Source 1. Where a match is clear, state it. Where a match is ambiguous, flag it as [NEEDS REVIEW] and explain why.
2. Identify any accounts in Sources 2 or 3 that have no clear counterpart in Source 1. Flag these a [NEW ACCOUNT - VERIFY].
3. For rows in Source 3 that have no account label, flag each as [UNLABELED ROW - MANUAL REVIEW REQUIRED]. Include the row's Reference value (e.g., IC-2024-1112-007) so reviewers can locate it.
4. Ignore non-account content such as titles, headers, totals, notes, and footnotes. Only process actual account/transaction rows.
5. Produce your output as a clean table with columns: Source, Original Label, Mapped to Source 1 Code, Mapped to Source 1 Description, Status.

Do not invent mappings. If you are not confident in a mapping, use the [NEEDS REVIEW] flag.
```

## **Part 5 — Reusable Templates**

### **Demo 8 — Building a reusable template (and then using it)**

This is a three-step demo. Step 1 builds the template. Step 2 exports it to Word so you can attach it. Step 3 populates the template with specific engagement notes — this is the workflow you'd use repeatedly across different engagements.

***Step 1 — Build the template***

```
You are helping me build a professional, reusable communication template for an accounting firm's audit teams. The template will be filled in by both humans and AI assistants, so placeholders must be self-describing and unambiguous.

The template is for: Client Inquiry Memos sent during audit fieldwork.

The template should:

1. Use the placeholder format [[TOKEN_NAME: description and format hint]] consistently throughout. Tokens are UPPER_SNAKE_CASE, unique, and decomposed (e.g., [[TEAM_MEMBER_EMAIL]] not [[CONTACT_DETAILS]]). Reuse the same token wherever the same value appears.

2. Include a header table with placeholders for client name, engagement period, memo date, preparer (name and title), and reviewing manager/senior (name and title).

3. Include an opening paragraph of mostly fixed text with one placeholder for the engagement phase or testing area.

4. Include a repeating numbered inquiry section with (a) observation, (b) documentation requested, and (c) response deadline. Wrap one example block in delimiters like <!-- BEGIN_INQUIRY_BLOCK: duplicate per item, renumber --> ... <!-- END_INQUIRY_BLOCK --> so it's clear how to repeat it.

5. Include a closing paragraph with fixed language and discrete placeholders for the responsible team member's name, title, email, and phone.

6. Use a formal, professional tone appropriate for external client communication.

After the template, include two short instruction sections:
- "How to Use This Template" for human team members.
- "AI Fill-In Guide" stating: replace each [[TOKEN]] with content (removing brackets and description); duplicate the inquiry block per item; preserve fixed text exactly; flag any token it cannot confidently fill rather than guessing.
```

***Step 2 — Export the template to Word***

```
Export this into a word document.
```

***Step 3 — Populate the template with engagement notes***

Attach the Word template you just generated, then run this prompt.

```
I have a communication template and I have specific engagement notes. Please populate the template with the relevant information from the notes, inserting the appropriate content into each placeholder and content zone.

Do not change any of the fixed text in the template. Fill in only the bracketed placeholders and the inquiry topic sections.

If any information needed to fill a placeholder is not present in the engagement notes, leave the placeholder visible.

The template has been given as a word document.

Here are the engagement notes:

Northgate Industrial Supply, FY ending 12/31/25, fieldwork phase doing substantive testing on inventory and accruals. Memo going out 3/19/26. I'm preparing (Jordan Alvarez, senior associate), Priya Raman reviewing as engagement manager.

Follow-up call with client Accounting Manager (Diane Whitfield) on 3/17. Discussion focused on the inventory valuation process. Client mentioned they switched to a new costing method (FIFO to weighted-average) at the start of the fiscal year but couldn't confirm whether the change was documented in the board minutes. Two SKUs flagged as potentially obsolete: Item X (carrying value $480K, slow-moving warehouse stock, last shipment August 2024) and Item Y (carrying value $215K, discontinued product line). No formal obsolescence analysis on file. Also discussed accrued liabilities: client has several open vendor invoices from Q4 that haven't been matched to POs or receiving reports. AP clerk (Marcus Reilly) was not available during the call. Follow up needed on all items above.

Want to formally request the following from client, response due in 5 business days (target 3/26). For the costing method change: board minutes authorizing the FIFO to weighted-average switch, the written accounting policy memo with rationale and effective date, and a quantitative impact analysis showing the effect on prior-period comparability and current-year COGS. For the obsolescence on Items X and Y: formal obsolescence analysis as of year-end with last sale dates, sales velocity over the prior 24 months, and NRV calcs supporting the $480K and $215K carrying values. For the Q4 vendor invoices: aged listing of unmatched POs and receiving reports, copies of vendor invoices and proof of receipt, and a reconciliation to the year-end accrued liabilities balance. Will also try to set up a separate call with Marcus Reilly directly.

Contact for client correspondence is me, Jordan Alvarez, senior associate at Hartwell & Boone LLP, jalvarez@hartwellboone.com, (415) 555-0182.
```

# **Module 2 — Manager Track**

## **Part 6 — Multi-Step Review Chains**

### **Demo 9 — Three-step review chain: AR workpaper**

| 📎 File required: AR_Workpaper_C200.docx |
| :---- |

> **📄 What's in this file:**
>
> A staff-prepared workpaper section documenting accounts receivable testing for a fictitious client. The document should be 1–2 pages and include:
>
> - A **testing objective** statement (e.g., "verify the existence and accuracy of the year-end accounts receivable balance").
> - A **procedures performed** section listing 3–5 procedures (sample selection, vouching to subsequent receipts, agreeing to subledger, etc.). Intentionally **omit at least one procedure you'd normally expect** for AR testing — for example, no positive confirmation procedure, or no sales cut-off testing.
> - An **evidence referenced** section pointing to specific support (e.g., "AR aging at 12/31, subledger detail, sample of cash receipts post year-end"). At least one procedure should reference evidence that's vague or thin.
> - A **conclusion stated** that is somewhat **stronger than the evidence supports** (e.g., asserts existence and valuation are fully supported when the cut-off and confirmation work is incomplete).
>
> The intentional gaps are what make the demo valuable — Step 2 of the chain will surface them.

A three-prompt chain that takes a staff-prepared workpaper, inventories what's there, identifies gaps, and drafts review notes. Run all three prompts in the same conversation, in order. Each prompt builds directly on the previous output.

***Step 1 — Extract and structure what's there***

```
You are helping me review a workpaper section submitted by a staff 
accountant. Before I evaluate its quality, I need a clear picture of 
what it contains.

Please read the attached workpaper section (AR_Workpaper_C200.docx) 
and produce a structured inventory with these four elements:
1. Testing objective: what was this test designed to accomplish?
2. Procedures performed: list each audit procedure described, in the 
   order performed
3. Evidence referenced: list every piece of documentation or 
   client-provided support mentioned
4. Conclusion stated: what conclusion did the staff member reach, and 
   how did they express it?

Do not evaluate quality yet. Do not add information that is not in the 
document. Only extract and organize what is there.

Label your output as "Workpaper Inventory" so we can refer to it in 
the next step.
```

***Step 2 — Identify gaps and issues***

```
Using the Workpaper Inventory you produced above, please identify:
1. Completeness gaps: are there procedures you would expect for this 
   type of testing that are not reflected in the inventory? List each 
   one and explain briefly why it would typically be expected.
2. Evidence gaps: for each procedure listed, is the evidence 
   referenced sufficient to support the procedure having been 
   performed? Flag any procedure where the evidence seems insufficient 
   or absent.
3. Conclusion alignment: does the conclusion stated align with the 
   procedures performed and the evidence referenced? If the conclusion 
   is stronger than the evidence supports, or weaker than it could be, 
   describe the mismatch specifically.
4. Escalation flags: are there any issues that go beyond a staff-level 
   revision, items that affect the scope, risk assessment, or require 
   a decision at the Senior or Manager level?

Organize your output as a numbered list under each of the four 
headings. Be specific. Reference the actual procedures and evidence 
from the Workpaper Inventory, not generic review observations.

Label your output as "Gap Analysis" so we can refer to it in the 
next step.
```

***Step 3 — Draft the review notes***

```
Based on the Gap Analysis you produced above, please draft written 
review notes to return to the staff member.

The review notes should:
- Open with a brief, specific acknowledgment of what was done well. 
  Reference something concrete from the workpaper, not a generic 
  compliment.
- Address each gap and issue from the Gap Analysis, organized from 
  most significant to least significant
- For each issue, explain what the problem is and what a complete, 
  correct version would look like. Give the staff member enough to 
  act on without doing the work for them.
- Flag any escalation items separately at the end with a note that 
  these will be discussed with the Manager
- Close with a clear statement of what the staff member needs to do 
  before resubmitting and a reasonable timeframe

Tone: constructive and developmental. Direct about the issues without 
being discouraging. This person should leave the review notes knowing 
exactly what to do next.
```

### **Demo 10 — Three-step chain adapted: analytical procedures memo**

| 📎 File required: Revenue_AP_Memo_B300.docx |
| :---- |

> **📄 What's in this file:**
>
> A staff-prepared analytical procedures memo for revenue, 1–2 pages, structured to surface specific weaknesses in Step 2:
>
> - A **testing objective** statement (e.g., "perform a substantive analytical procedure over current-year revenue").
> - An **expectation development** section that is **not sufficiently precise** — for example, prior-year revenue scaled by growth without reflecting known drivers like a new product line, a price increase, or a divested segment.
> - An **actual result vs. expectation** comparison with a stated variance in both dollars and percentage. The variance should be material enough to warrant investigation.
> - A **threshold for further investigation** that is **either absent or stated only generically** (e.g., no pre-established materiality threshold).
> - An **explanation offered** that is taken from client management with **no corroborating evidence cited**.
> - A **conclusion** that is stronger than the evidence supports — e.g., "no further procedures considered necessary" despite the gaps above.

The same three-step pattern as Demo 9, applied to a different workpaper type. Notice the structure stays identical even though the content of each prompt is different. Run all three in the same conversation.

***Step 1 — Inventory the memo***

```
You are helping me review an analytical procedures memo submitted by 
a staff accountant. Before I evaluate its quality, I need a clear 
picture of what it contains.

Please read the attached memo (Revenue_AP_Memo_B300.docx) and produce 
a structured inventory with these four elements:
1. Testing objective: what was this analytical procedure designed to 
   accomplish?
2. Expectation development: how was the expectation developed, and 
   what assumptions does it rely on?
3. Variance identified: what is the variance between the expectation 
   and the actual result, stated in both dollars and percentage?
4. Explanation offered: what explanation did the staff member document 
   for the variance, and what corroboration is cited?

Do not evaluate quality yet. Only extract and organize what is there.

Label your output as "Memo Inventory" so we can refer to it in the 
next step.
```

***Step 2 — Evaluate the memo***

```
Using the Memo Inventory you produced above, please evaluate the 
analytical procedures memo:
1. Expectation quality: is the expectation sufficiently precise to be 
   meaningful? Does it reflect all relevant drivers of the account 
   balance, or are there factors that should have been incorporated 
   but were not?
2. Variance threshold: does the memo indicate whether the variance 
   exceeds any pre-established threshold for further investigation? 
   Flag if this is absent.
3. Explanation corroboration: is the client's explanation for the 
   variance supported by sufficient corroborating evidence? Flag any 
   explanation that is accepted without corroboration.
4. Conclusion alignment: does the conclusion follow logically from 
   the expectation, the variance, and the explanation? If the 
   conclusion is stronger than the evidence supports, describe the 
   gap specifically.
5. Escalation flags: are there any items that should be brought to 
   the manager's attention before the memo is finalized?

Organize your output under each heading. Be specific. Reference the 
actual content from the Memo Inventory, not generic review observations.

Label your output as "Gap Analysis" so we can refer to it in the 
next step.
```

***Step 3 — Draft review notes for the staff member***

```
Based on the Gap Analysis you produced above, please draft written 
review notes to return to the staff member.

The review notes should:
- Open with a brief, specific acknowledgment of what was done well
- Address each issue from the Gap Analysis, organized from most 
  significant to least significant
- For each issue, explain what the problem is and what a complete, 
  correct version would look like
- Flag any escalation items separately at the end
- Close with a clear statement of what the staff member needs to do 
  before resubmitting

Tone: constructive and direct. The staff member should know exactly 
what to do next.
```

## **Part 7 — Cross-Reference Validation**

### **Demo 11 — Cross-reference: revenue recognition conclusion against the five-step model**

| 📎 File required: REV-2025-104_TechFlow_RevRec_Workpaper.docx |
| :---- |

> **📄 What's in this file:**
>
> A staff-prepared revenue recognition working paper for a fictitious client (TechFlow Solutions Master Software Agreement). 2–3 pages. The structure must be:
>
> - **Section 1 — Header & Objective.** Working paper reference (REV-2025-104), client name, period, preparer/reviewer, brief objective.
> - **Section 2 — Contract Facts.** A description of the TechFlow arrangement that includes elements touching multiple steps of the five-step model: a software licence + an implementation service + ongoing support, a tiered fee structure with a usage-based component (variable consideration), a termination-for-convenience clause, and a side acceptance criterion. Include facts that are intentionally **incomplete** — for example, no information on whether the implementation service is distinct, or no quantitative estimate of variable consideration.
> - **Section 3 — Documented Conclusion.** The staff member's conclusion on revenue recognition. The conclusion should address some of the five steps cleanly (e.g., contract identification), partially address others (e.g., performance obligations described but not clearly evaluated for distinct status), and **not address at least one step** (e.g., transaction price allocation skipped or treated superficially).
>
> The mix of aligned, partially aligned, and not-addressed elements is what makes the cross-reference output instructive.

A single prompt that walks Copilot through a structured five-step cross-reference and flags alignment status at each step. The output is a scaffold for your professional judgment — not a final answer. The instruction "do not invent requirements" is critical and must stay in the prompt.

```
I am a Senior Auditor validating a revenue recognition conclusion against the applicable revenue recognition standard. The staff member's documented conclusion and the relevant contract facts are contained in the attached working paper (REV-2025-104, Revenue Recognition – TechFlow Solutions Master Software Agreement). Section 2 of that working paper sets out the contract facts; Section 3 sets out the staff member's documented conclusion.

Your task is to run a structured cross-reference against the five-step revenue recognition model:
Step 1: Identify the contract with the customer
Step 2: Identify the performance obligations
Step 3: Determine the transaction price
Step 4: Allocate the transaction price to performance obligations
Step 5: Recognize revenue when (or as) performance obligations are satisfied

For each step:
1. State what the standard requires at this step. Describe the principle in plain language.
2. State what the staff member's conclusion addresses (or does not address) at this step
3. Flag the alignment status: ALIGNED / PARTIALLY ALIGNED / NOT ADDRESSED / CONFLICT
4. Where the status is anything other than ALIGNED, describe specifically what is missing or inconsistent

After the five-step analysis, produce a brief validation summary: does the overall conclusion appear to be supportable based on the cross-reference? What, if anything, needs to be resolved before the conclusion can be finalized?

Important: base your description of each step's requirements on established accounting principles. Do not invent requirements. Where a specific requirement would depend on facts not provided in the attached working paper, flag it as [FACT-DEPENDENT: VERIFY].

Use only the facts contained in the attached working paper — do not assume facts that are not stated there.
```

### **Demo 12 — Cross-reference adapted: going concern assessment**

| 📎 File required: GC-2026-001_NorthBay_GoingConcern_Workpaper.docx |
| :---- |

> **📄 What's in this file:**
>
> A going concern assessment working paper for a fictitious client (NorthBay Components Pty Ltd). 2–3 pages, same Section 1 / 2 / 3 structure as Demo 11:
>
> - **Section 1 — Header & Objective.** Working paper reference (GC-2026-001), client name, period, preparer/reviewer, brief objective.
> - **Section 2 — Entity Facts.** Conditions and events that may indicate substantial doubt — for example, recurring operating losses, declining cash position, an upcoming debt maturity, a covenant approaching breach. Include management's plans to mitigate (refinancing in progress, cost-reduction programme, equity raise being explored). Some plans should be supported by evidence, others described but **not corroborated**.
> - **Section 3 — Documented Assessment.** The audit team's working assessment of going concern, addressing identification of conditions, evaluation of mitigating plans, conclusion on whether substantial doubt is alleviated, and disclosure considerations. Include intentional gaps — e.g., disclosure requirements not addressed, or conclusion stated more strongly than the supporting evidence justifies.

The same scaffold as Demo 11 — extract requirement, state what was addressed, flag status, summarise — adapted to going concern. Notice the added instruction "Do not state conclusions about substantial doubt on behalf of the auditor" because the conclusion itself is a professional judgment, not a factual determination.

```
I am validating a going concern assessment against the requirements of the applicable going concern auditing standard. The audit team's documented assessment and the relevant entity facts are contained in the attached working paper (GC-2026-001, Going Concern Assessment – NorthBay Components Pty Ltd). Section 2 of that working paper sets out the entity facts; Section 3 sets out the audit team's documented assessment.

Please run a structured cross-reference across the following elements:
1. Identification of conditions and events that may indicate substantial doubt
2. Evaluation of management's plans to mitigate those conditions and events
3. Assessment of whether substantial doubt is alleviated after considering management's plans
4. Disclosure requirements: are the required disclosures consistent with the conclusion reached?

For each element, follow the same structure: state what the standard requires, state what the assessment addresses, flag the alignment status (ALIGNED / PARTIALLY ALIGNED / NOT ADDRESSED / CONFLICT), and describe any gap specifically.

After the element-by-element analysis, produce a brief validation summary: does the overall assessment appear to be consistent with the applicable standard? What needs to be resolved?

Do not state conclusions about substantial doubt on behalf of the auditor. That determination is a professional judgment. Flag where the analysis supports or does not support the conclusion, and leave the final determination to me.

Use only the facts contained in the attached working paper — do not assume facts that are not stated there.
```

## **Part 8 — Sequencing AI-Assisted Tasks**

### **Demo 13 — Two-prompt chain: contract review for revenue recognition**

| 📎 File required: Master_Subscription_Agreement.docx |
| :---- |

> **📄 What's in this file:**
>
> A signed B2B customer contract written in normal contract style (parties, recitals, numbered clauses, signature block). It should be detailed enough that the extraction in Prompt 1 has substance to work with — roughly 6–10 pages. To make Prompt 2 productive, the contract should contain elements that touch each ASC 606 step:
>
> - **Performance obligations** — at least two distinguishable deliverables (e.g., a SaaS subscription + an implementation/onboarding service + ongoing support).
> - **Pricing** — a base fee plus at least one component that creates **variable consideration** (usage tiers, volume discounts, performance bonuses, or service credits).
> - **Payment terms** — a defined invoicing cadence (e.g., annual in advance) and any net-payment terms.
> - **Termination / refund clauses** — a termination-for-convenience right and a refund or service-credit mechanism.
> - **Modification language** — a clause covering how scope changes are handled.
> - **Acceptance criteria** — language defining when the customer has accepted the implementation.
> - **A side-letter or addendum reference** — even just a clause noting that addenda exist but are not attached, so Prompt 2 has something to flag as an open question.
>
> Use clear clause and section numbering throughout (e.g., "Section 4.2 — Variable Consideration") so the extraction can reference specific locations.

Two prompts designed to chain. Prompt 1 extracts terms into a structured table with no interpretation. Prompt 2 takes that table as its input and produces an issues memo. The handoff between them is engineered — the structured output of Prompt 1 is exactly what Prompt 2 needs.

***Prompt 1 — Extract key contract terms (attach the contract)***

```
You are helping me complete the contract review step of a revenue
recognition audit. I have attached a customer contract. Extract the
key terms that affect revenue recognition into a structured output.

This output will be the direct input to a subsequent issues
identification prompt, so format and consistency are critical.
Do not interpret, evaluate, or flag issues at this stage — just
extract. Evaluation comes in the next step.

Produce the output in two parts:

Part 1 — Contract Summary
One short paragraph covering: parties, contract type, effective date,
total estimated contract value, and contract term.

Part 2 — Key Terms Table
A table with these columns:
- Term Category (use one of: Performance Obligation, Pricing,
  Variable Consideration, Payment Terms, Termination/Refund,
  Modification, Side Agreement, Acceptance Criteria, Other)
- Specific Term (short description, 5-10 words)
- Contract Reference (clause or section number)
- Verbatim Excerpt (key contract language, kept brief)
- Relevant ASC 606 Step (1-Identify Contract, 2-Identify Performance
  Obligations, 3-Determine Transaction Price, 4-Allocate Transaction
  Price, 5-Recognise Revenue)

Capture every term that touches revenue recognition. Be exhaustive.
```

***Prompt 2 — Produce the flagged issues memo***

Copy the full output from Prompt 1 and paste it where indicated below.

```
I am completing the revenue recognition risk review of a customer
contract. I am going to give you the structured extraction of key
terms produced in the prior step. Use it to produce a flagged issues
memo for the audit workpaper.

For each term in the extraction, assess whether it warrants follow-up
during fieldwork. Produce a memo with the following structure:

Section 1 — Issues Requiring Follow-up
A table with columns:
- Issue ID (sequential, e.g., I-01, I-02)
- Term Category (from the extraction)
- Contract Reference
- Issue Description (what about this term creates revenue recognition
  risk or requires further procedures)
- ASC 606 Step Affected
- Risk Rating (High / Medium / Low)
- Recommended Procedure (specific testing or inquiry — not generic
  language like "review for compliance")

Section 2 — Terms Reviewed and Cleared
Brief list of terms reviewed but not flagged, each with a one-line
rationale for clearing.

Section 3 — Open Questions for the Client
A short list of specific questions to put to the client to resolve
gaps surfaced by the contract review (e.g., requests for side letter
copies, additional documentation, clarifications of commercial intent).

Anchor every recommended procedure and every question to a specific
contract reference from the extraction.

Here is the contract extraction:

[paste output from Prompt 1]
```
