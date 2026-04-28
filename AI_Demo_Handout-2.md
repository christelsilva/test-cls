

# Generative AI Essentials for Non-Technologists

## Student Demo Handout



### **How to use this handout**

This handout contains every prompt that will be demoed during the session. Copy any prompt below and paste it into your AI tool to follow along. Each demo lists:

* The file (if any) you'll need to attach when running the prompt  
* A short description of what the demo shows  
* The prompt itself, in a gray box, you can copy directly

Files referenced in this handout will be distributed separately. The 📎 callout box at the top of each demo tells you which file to attach. Demos without a callout don't need a file.

## **Part 1 — Understanding LLMs**

### **Demo 1 — Non-deterministic behavior**

Run this prompt twice and compare the responses. The same prompt will return different answers each time — this is by design. LLMs are probabilistic, not deterministic.

```
What are 3 catchy names for a new internal initiative focused on sustainable investing?
```

## **Part 2 — Prompt Engineering Techniques**

### **Demo 2 — Structuring prompts (three levels)**

Three versions of the same task, each with more structure than the last. Run all three and notice how dramatically the response improves as you move from vague to a fully structured prompt using the GCSE framework (Goal, Context, Source, Expectations).

***Level 1 — Vague***

```
Write a client email.
```

***Level 2 — Natural language with some detail***

```
I need to write an email to a client named Sarah who hasn't responded to our last two meeting requests. She's a high-value client, and I don't want to seem pushy, but I need to meet before quarter end.
```

***Level 3 — Structured with GCSE***

```
## Goal
Draft a follow-up email to a high-value client who hasn't responded to two previous meeting requests.
 
## Context
Client: Sarah (12-year relationship, $5M+ AUM). Two prior emails were sent (March 3 and March 17). No response. Quarter-end approaching.
 
## Expectations
- Professional but warm tone
- Acknowledge that she's busy without being passive-aggressive
- Provide 2-3 specific time options
- Mention one value-add for the meeting (market update or portfolio insight)
- Under 200 words, include subject line
```

### **Demo 3 — Language effects**

Three prompts on the same topic, each phrased for a different audience. Run all three and compare how dramatically the response changes based on how you frame the question.

***Prompt A — Generic phrasing***

```
Explain what a bond yield curve inversion means.
```

***Prompt B — Audience-specific (analyst, with analogy)***

```
Explain what a bond yield curve inversion means as if I'm a first-year analyst who just joined the fixed income desk. Use an analogy.
```

***Prompt C — Audience-specific (client newsletter)***

```
Explain what a bond yield curve inversion means for a client newsletter. The audience is high-net-worth individuals who are financially literate but not traders. Focus on what it signals historically and what they should consider for their portfolio.
```

### **Demo 4 — Bias in AI responses**

A broad question that surfaces patterns from the training data. Look at the response and notice whether the list skews by gender, region, or era.

```
Who are the top 10 financial advisors of all time?
```

### **Demo 5 — Interpretation bias**

A vague prompt the model has to interpret. What kind of forecast did it give you — weather, financial, or sales? The model's interpretation reflects patterns in its training data.

```
Give me today's forecast.
```

### **Demo 6 — Meta-prompting (let the AI help you write the prompt)**

| 📎 File required: Raw Client Meeting.docx (used in Step 3 below) |
| :---- |

This is a three-step demo. First, ask the AI to interview you. Second, ask it to turn that conversation into a reusable prompt. Third, run that prompt with the attached file.

***Step 1 — Start the interview***

```
I'm designing a prompt that helps me create a weekly client interaction summary from raw data. I need you to help me clarify the goal by asking one question at a time.
```

***Step 2 — Once the AI has finished asking questions***

```
Now use this clarity to create a detailed prompt in a code block that I can save and reuse. Do not use emojis.
```

***Step 3 — Run the generated prompt***

```
[Paste the prompt the AI just generated in Step 2, and attach Raw Client Meeting.docx]
```

### **Demo 7 — Templatizing prompts for reuse**

Take a prompt that works and convert it into a reusable template using placeholders. Compare the two versions below.

***Original — One-off prompt***

```
Create a client re-engagement email for our high-value client, ACME CORP. Let them know it's been 6 months since their last review, and Bob, their account manager, would like to schedule a meeting.
```

***Templatized — Reusable across clients***

```
Create a client re-engagement email for our high-value client [CLIENT_NAME], let them know it's been [TIME_SINCE_REVIEW] since their last review, and [ACCOUNT_MANAGER], their account manager, would like to schedule a meeting.
```

Ask the user to fill in these placeholders before generating the email.

## **Part 3 — Drafting Content**

### **Demo 8 — Drafting without context (hallucination risk)**

Run this prompt with no attached file. The model has never heard of "InsightEdge," so it will fill in the gaps — convincingly. Look closely at the features it invents.

```
Write a blog post announcing the launch of our new portfolio analytics tool, InsightEdge. We want to excite potential clients about modernizing their portfolio monitoring, especially those who have been relying on traditional manual reporting. Highlight its main features like automated performance attribution and real-time risk monitoring. Include a call to action to schedule a demo.
```

### **Demo 9 — Adding a simple guardrail**

Same prompt as Demo 8, but with one sentence added at the end. See how the response changes.

```
Write a blog post announcing the launch of our new portfolio analytics tool, InsightEdge. We want to excite potential clients about modernizing their portfolio monitoring, especially those who have been relying on traditional manual reporting. Highlight its main features like automated performance attribution and real-time risk monitoring. Include a call to action to schedule a demo. If you don't know who that product is or you don't have accurate information about that product, then respond with "I don't have reliable information about this product."
```

### **Demo 10 — Drafting with context and guardrails**

| 📎 File required: InsightEdge Product.docx |
| :---- |

Now we give the model real product information AND keep the guardrail. Compare this output to Demo 8\.

```
Write a blog post announcing the launch of our new portfolio analytics tool, InsightEdge. Include a call to action to schedule a demo.
 
## Context
Review the following product specification attached thoroughly before writing.
 
## Expectations
- Use ONLY information contained in the product specification. Do not invent features, statistics, or capabilities not explicitly stated.
- Maintain factual, benefit-focused language without unverifiable superiority claims.
- If you're uncertain about a detail, either omit it or clearly indicate it as a general industry benefit rather than a specific product feature.
- If you don't know who that product is or you don't have accurate information about that product, then respond with "I don't have reliable information about this product."
```

### **Demo 11 — Drafting a client email with internal/external context separation**

| 📎 File required: Internal Memo.docx |
| :---- |

A more advanced drafting prompt. The internal memo informs tone but must not be referenced in the email itself — guardrails enforce that boundary.

```
## Goal
Draft a professional email to a long-standing client informing them of a change to our quarterly reporting format.
 
## Client Context
- The client has been with us for 12 years
- We are transitioning from static PDF reports to an interactive digital dashboard
- Some long-standing clients may be resistant to change
- The email is client-facing and relationship-focused
 
## Internal Context (For Background Only)
You have access to an **internal memo** explaining the rationale for moving from PDF reports to interactive digital dashboards.
 
This internal context is provided **only to inform tone and positioning**. It must **not** be referenced directly or disclosed to the client.
 
## Expectations
- Warm, relationship-focused tone that reflects a 12-year partnership
- Emphasize client-relevant benefits
- Acknowledge that the client may prefer the existing PDF format
- Offer a clear transition period and support
- Keep the email under 400 words
- Include a call to action to schedule a walkthrough of the new dashboard
 
## Guardrails
- Use **only** client-appropriate information in the email
- Do **not** reference internal documents, memos, operational motives, or efficiency gains
- Do **not** disclose internal strategy, scalability goals, or process changes
- Do **not** invent client-specific history beyond what is provided
- If you cannot confidently separate internal context from client-safe messaging, respond with:
  **"I don't have enough information to draft this email without risking internal data exposure."**
```

### **Demo 12 — Drafting client meeting talking points**

Generates talking points using only the context provided in the prompt. Notice how guardrails prevent the model from inventing performance drivers or forecasts.

```
## Goal
Create talking points for a 30-minute client review meeting.
 
## Context
- Quarterly portfolio review for a high-net-worth client
- Portfolio is up 3.2% this quarter vs. benchmark of 2.8%
- One underperforming position in commercial real estate
- Client previously expressed interest in ESG investing
 
## Expectations
- Opening: positive framing of overall performance
- Middle: honest, balanced discussion of the real estate position with a recommended next step
- Close: introduce ESG opportunities as a conversation starter
- Bullet point format
- Conversational, client-friendly tone
 
## Guardrails
- Use **only** the information provided in the Context
- Do **not** invent causes of performance, forecasts, or market outlooks
- Do **not** imply guarantees or certainty of future results
- Frame recommendations as **discussion options**, not directives
- Treat ESG as exploratory; do **not** assume it is a priority or mandate
- Do **not** reference other clients, internal strategy, or internal analysis
- If you cannot create talking points without adding assumptions, respond with:
  **"I don't have enough information to create client-ready talking points safely."**
```

## **Part 4 — Summarization**

### **Demo 13 — Summarization tailored to three audiences**

| 📎 File required: Morgan Stanley First Quarter 2026 Earnings Results.pdf |
| :---- |

Run all three prompts against the same earnings document. Notice how dramatically the output changes based on the audience and summary type (abstractive, extractive, hybrid).

***Prompt A — For senior leadership (abstractive)***

```
## Goal
Provide senior leadership with a concise, strategic overview of Morgan Stanley's Q1 2026 performance to support discussion and decision-making.
 
## Context
Use the attached Morgan Stanley Q1 2026 Earnings Release as the sole source. Your audience is the senior leadership team.
 
## Expectations
- Write an abstractive summary: paraphrase and synthesize the main points in your own words
- Cover firm-wide performance and how each of the three segments (Institutional Securities, Wealth Management, Investment Management) performed versus the prior-year quarter
- Highlight strategic themes: operating leverage, client momentum, capital position, and shareholder returns
- Flag any one-off items or accounting changes that warrant leadership attention (e.g. severance charges, DCP hedging transition)
- Avoid non-GAAP acronym overload; keep it concise and actionable
- Maximum one page
```

***Prompt B — For equity research analysts (extractive)***

```
## Goal
Equip an equity research analyst with the precise figures and quoted management commentary needed to update their Morgan Stanley financial model.
 
## Context
Refer exclusively to the attached Morgan Stanley Q1 2026 Earnings Release. Audience: sell-side or buy-side equity research analyst covering US banks.
 
## Expectations
- Create an extractive summary: quote the most relevant financial figures, ratios, and CEO/management commentary directly from the document
- For each extracted item, include the page or section reference (e.g., "Highlights, p.1", "Institutional Securities, p.2", "Consolidated Income Statement, p.8")
- Organize extractions by: Firm-level results, Institutional Securities, Wealth Management, Investment Management, Capital & Shareholder Returns
- Include both reported figures and YoY comparatives where given; do not round or paraphrase numbers
- Call out footnoted accounting or presentation changes that affect comparability (e.g. DCP treatment, long-term net flows definition change)
- Use technical language appropriate for financial professionals
```

***Prompt C — For new Financial Advisor training (hybrid)***

```
## Goal
Help new Financial Advisors understand the firm's quarterly performance so they can speak to clients with confidence about Morgan Stanley's results.
 
## Context
The summary will be used in a training session for Financial Advisors in their first year at Morgan Stanley. Source: the attached Q1 2026 Earnings Release.
 
## Expectations
- Start with a brief abstractive overview in plain language explaining how the firm performed and why it matters
- List 3-5 key points using extractive snippets from the document (e.g., headline revenue, EPS, ROTCE, Wealth Management net new assets, CET1 ratio)
- For each point, add a reference to the relevant page or section
- Explain each point's practical relevance — for example, what $118B of Wealth Management net new assets means for an advisor's client conversations
- Use clear, simple language; define acronyms on first use (ROTCE, CET1, AUM, NNA)
- End with 2-3 sample talking points an advisor could use with a client
```

### **Demo 14 — Summarizing a long email chain**

This demo pulls emails directly from Outlook — no separate file needed. The AI tool will need access to your inbox and will summarize an existing thread containing "Project Aurora" in the subject line.

| ℹ Note: No file attachment — your AI tool will read from Outlook directly. |
| :---- |

```
## Goal
Summarize a long email thread related to **Project Aurora** for a busy stakeholder.
 
## Context
- The input is a multi-email Outlook conversation
- Emails all contain "Project Aurora" in the subject
- The thread includes updates, questions, and discussion
- Some messages may contain internal opinions, side conversations, or unresolved topics
 
## Expectations
- Concise, executive-ready summary
- Written in neutral, professional language
- Clearly structured using bullet points
- Focus on signal over noise
 
The summary should include:
- Key themes or topics discussed
- Any clearly stated decisions (only if explicitly stated)
- Open questions or unresolved issues
- Notable next steps (only if explicitly mentioned)
 
## Guardrails
- Base the summary **only on the provided email content**
- Do **not** invent decisions, agreements, or conclusions
- Do **not** assume intent, tone, or priority beyond what is written
- Do **not** infer timelines, owners, or deadlines unless explicitly stated
- Exclude internal opinions, speculation, or casual commentary unless central to the discussion
- Do **not** add recommendations or personal interpretation
- Preserve confidentiality: do **not** expose sensitive details beyond what is required for a high-level summary
 
If the email thread does not contain clear outcomes or decisions, state that explicitly rather than inferring them.
 
If you cannot summarize the thread without making assumptions, respond with:
**"The email chain does not contain enough explicit information to produce a reliable summary."**
```

### **Demo 15 — Transforming messy handwritten meeting notes**

| 📎 File required: handwritten-meeting-notes.jpg |
| :---- |

Attach the handwritten notes image and let the AI extract structure from it — without inventing details that aren't actually there.

```
## Goal
Transform these rough handwritten meeting notes into a structured summary.
 
## Context
- The input consists of handwritten meeting notes
- Some handwriting may be unclear or ambiguous
- Not all decisions, owners, or dates may be explicitly documented
 
## Expectations
- Attendees:
  - List only those explicitly written in the notes
  - Do **not** guess additional attendees
- Key discussion points:
  - 3–5 bullets based strictly on written content
- Decisions made:
  - Include only decisions that are clearly stated
  - If none are explicit, state "No explicit decisions documented"
- Action items:
  - List only if clearly written
  - Include owners and due dates **only if explicitly noted**
- Next meeting:
  - Include only if a date or topic is clearly mentioned
```

## **Part 5 — Building a Knowledge Base Assistant**

### **Demo 16 — Grounded Q\&A from a single document**

| 📎 File required: Morgan Stanley First Quarter 2026 Earnings Results.pdf |
| :---- |

Set up the assistant with the system prompt below, then try the follow-up questions to test its boundaries. Notice how it handles questions inside the document vs. completely outside it.

***Step 1 — Set up the grounded assistant***

```
## Goal
Act as a grounded Q&A system that answers user questions about Morgan Stanley's Q1 2026 performance using only the attached earnings release, with no external knowledge or speculation.
 
## Context
Use the attached Morgan Stanley Q1 2026 Earnings Release as the sole source of truth. Only content explicitly present in the attached document—including tables, footnotes, and defined terms is in scope.
 
Audience: any user asking a question about the quarter's results, this could be an analyst, an advisor, a leadership team member, or a journalist.
 
## Expectations
- Answer only from the provided document; do not use prior training data, external knowledge, or inference beyond what the text supports
- For each answer:
  1. Identify the most relevant section(s) of the document
  2. Synthesize a concise, coherent response grounded in that content
  3. Cite the page or section reference
- Preserve exact figures, percentages, and defined terms as they appear in the document; do not round, rephrase, or approximate numbers
- If figures differ between the narrative text and tables, use the table values and cite the source without reconciliation
- If the question involves a non-GAAP measure or defined term (e.g., ROTCE, CET1, net new assets, DCP), reference the relevant footnote or definition
- Do not infer causality, drivers, or outlook unless explicitly stated in the document
- Do not answer forward-looking or "why" questions unless the document explicitly addresses them
- If a question contains multiple parts, answer each part explicitly; if any part cannot be answered, respond only with:
   "Information unavailable in the current document."
- If the answer cannot be derived from the document, respond only with:
   "Information unavailable in the current document."
- Do not elaborate, speculate, or offer related information
- If a question is ambiguous or could be interpreted multiple ways, ask a clarifying question before answering, rather than guessing
- Maintain a neutral, factual tone regardless of audience
- Keep answers concise: lead with the direct answer, then provide supporting figures or context only if needed
```

***Step 2 — Questions that should work (in scope)***

```
What is the current compensation expense?
```

```
Are the Investment Banking net revenues up?
```

```
What did the Board of Directors declare?
```

***Step 3 — Question that should be refused (out of scope)***

```
What type of car should I buy if I have a family of 4?
```

## **Part 6 — Editing and Tone Adjustment**

### **Demo 17 — Rewriting a blunt client email**

| 📎 File required: Email.txt |
| :---- |

The source email is a transactional decline that needs softening — without changing the underlying decision. The prompt enforces that boundary and asks for multiple tonal variants.

```
## Goal
Refine an advisor-drafted client email declining an application for a premium advisory tier so that it is professional, empathetic, and aligned with a premium wealth-management brand voice, without changing the underlying decision.
 
## Context
A relationship manager has drafted a direct, transactional email informing an existing Morgan Stanley client that their application for a premium advisory tier has been declined. The decision itself is final and will not change.
 
Your role is to improve tone, framing, and clarity while preserving the advisor's intent and all factual details. The email is client-facing and will be sent directly to the declined applicant.
 
Before proceeding, ask the user to paste the draft email they would like rewritten. Do not generate any rewritten content until the source email has been provided.
 
## Success Criteria
The rewritten email:
- Communicates the decision clearly and respectfully
- Feels consistent with a premium wealth management relationship
- Preserves trust and professionalism despite a negative outcome
- Offers a constructive, forward-looking path where appropriate
- Can be sent to a high-net-worth client without further editing
 
## Expectations
- Preserve the core decision exactly as stated in the source email, including:
  - The decline itself
  - Any reapplication window
  - Any stated conditions for reconsideration
- Acknowledge the existing client relationship and thank the client for their interest
- Explain the outcome clearly without listing blunt or personal failure reasons; frame eligibility criteria neutrally
- Offer a constructive path forward where applicable, such as:
  - Who the client can contact with questions
  - What to focus on next
  - When reconsideration could occur, if stated
- Maintain a warm, professional, and human tone consistent with a premium financial services brand
- Avoid corporate jargon, legalistic language, hollow apologies, or excessive sentiment
- Keep each version concise (150–180 words)
- Provide 2–3 rewritten variants with different tonal emphasis (e.g., relationship-focused, crisp and professional, advisory and forward-looking)
- Create the versions of the email in an Outlook draft
 
## Guardrails
- Do not soften, reverse, or obscure the decision
- Do not introduce new reasons, promises, timelines, or eligibility criteria
- Do not invent missing details or imply flexibility that does not exist
- Do not shift accountability for the decision
- If the source email is missing essential details (e.g., unclear sign-off, missing reapplication guidance, ambiguous wording), ask a brief clarifying question before rewriting rather than making assumptions
```

### **Demo 18 — Aligning content to a brand style guide**

| 📎 File required: Communications Style Guide.docx AND Internal Announcement.docx |
| :---- |

Attach both files. The model uses the style guide as the standard and rewrites the announcement to match—without changing what the message actually says.

```
## Goal
Act as a senior corporate communications editor at Morgan Stanley with extensive experience shaping firm-wide internal messaging. Revise the attached internal announcement so that it aligns with the Morgan Stanley Communications Style Guide while preserving the original intent, meaning, and factual content.
 
## Context
You are provided with:
1. An informal draft of an internal announcement intended for employees
2. The Morgan Stanley Communications Style Guide, which defines expected tone, structure, and writing standards
 
The announcement communicates internal process updates. The substance of the message must remain unchanged; only how it is expressed should be refined.
 
Audience: internal Morgan Stanley employees.
 
## Success Criteria
The revised announcement:
- Reflects the tone, voice, and structure outlined in the Communications Style Guide
- Reads as professional, clear, and appropriate for firm-wide internal communication
- Maintains confidence and credibility without sounding casual or overly verbose
- Can be distributed internally without further editing
 
## Expectations
- Preserve the original meaning, intent, and scope of the announcement
- Improve clarity, structure, and flow in line with the style guide
- Replace informal or conversational language with professional phrasing
- Use a composed, human tone consistent with a premium global financial institution
- Organize content logically (context → key information → next steps)
- Keep the revision concise; avoid adding unnecessary detail or emphasis
- Use professional salutations and sign-offs appropriate for internal communications
 
## Guardrails
- Do not introduce new information, commitments, timelines, or policy implications
- Do not change the substance or implications of the message
- Do not add operational rationale beyond what is already stated
- Do not reference the style guide explicitly in the output
- If the source announcement is ambiguous, preserve the ambiguity rather than clarifying or expanding it
```

## **Part 7 — Working with Spreadsheets**

### **Demo 19 — Excel formulas and data operations**

| 📎 File required: client\_data.xlsx |
| :---- |

Run each of the prompts below against the attached spreadsheet. Each one demonstrates a different kind of data operation — from aggregation to categorization to splitting fields.

***Prompt 1 — Aggregation***

```
What's the total account value by advisor? Put the answer in a new sheet.
```

***Prompt 2 — Chart creation***

```
Create a chart showing account value distribution by advisor
```

***Prompt 3 — Categorization***

```
Add a column that categorizes clients as 'High Value' (>$500K), 'Medium' ($100K-$500K), or 'Standard' (<$100K)
```

***Prompt 4 — Date calculation***

```
Calculate how many days since each client's last review
```

***Prompt 5 — Conditional formatting***

```
Highlight all clients with account values over $1 million
```

***Prompt 6 — Splitting fields***

```
Split the client names into first name and last name columns
```

## **Part 8 — Classification with Few-Shot Prompting**

### **Demo 20 — Sentiment analysis across an email chain**

| 📎 File required: Client Email Correspondence.docx |
| :---- |

This prompt uses few-shot examples to teach the model how to interpret subtle tone shifts in client emails. Notice how the examples in the prompt shape the analysis you get back.

```
## Goal
You are an assistant helping a Relationship Manager understand a client's sentiment and overall relationship health based on written communication, so they can respond proactively and appropriately.
 
## Context
You are reviewing a series of client email exchanges that are attached between a client and their relationship team over time. These are routine business emails, not formal complaints, and no issue has been escalated.
 
Your task is to analyze how the client's sentiment evolves over time, identify early
warning signals, and support human judgment (not replace it).
 
## Steps
1. Review the full email correspondence in chronological order.
2. Identify changes in tone, emotion, confidence, or expectations over time.
3. Focus on *how* things are said, not just *what* is said.
4. Distinguish polite or professional language from underlying frustration,
   anxiety, or erosion of trust.
5. Summarise the client's current sentiment state and relationship risk at a
   high level.
 
## Examples (Sentiment Interpretation)
Example 1 – Neutral / Healthy
Text: "Happy to discuss when convenient."
Interpretation: Neutral, cooperative tone; no indication of concern or urgency.
 
Example 2 – Early Signal
Text: "I had expected more advance notice."
Interpretation: Mild dissatisfaction expressed professionally; early expectation
misalignment, but not a complaint.
 
Example 3 – Escalating Concern
Text: "This is the second time I've needed to chase."
Interpretation: Frustration emerging due to repeated follow-ups; confidence beginning
to erode.
 
Example 4 – Reputational Signal
Text: "Part of the reason I chose this firm was the expectation of proactive service."
Interpretation: Client is reassessing value and service expectations; heightened
relationship risk despite calm tone.
 
Use these examples to guide how you interpret sentiment throughout the emails.
 
## Guardrails
- Do not assign blame to individuals or teams.
- Do not speculate about churn, complaints, or future client actions.
- Do not label the client as 'angry', 'difficult', or 'problematic'.
- Do not treat professional language as proof of satisfaction.
- Base insights only on observable language patterns in the emails.
 
 
## Expectations
Provide your response in four short sections:
 
1. Sentiment Progression
   - How the client's tone and confidence change over time
 
2. Key Sentiment Signals
   - Specific phrases or behaviors indicating emerging concern
 
3. Current Relationship Health (High-Level)
   - A neutral, business-appropriate summary
 
4. Focus Areas for the Relationship Manager
   - Practical, non-prescriptive areas of attention
 
Keep the response concise, professional, and suitable for briefing a senior relationship or client-coverage leader.
```

## **Part 9 — Extracting Structured Data**

### **Demo 21 — Extracting director nominees into a clean table**

| 📎 File required: 2026\_Proxy\_Statement.pdf — extract pages 16–27 first, then attach those pages only |
| :---- |

The full proxy statement is large. Trim to just the relevant pages (16–27) before attaching, then run the prompt below. This shows the value of cleaning up your context before sending it to the model.

```
## Goal
Extract structured information from a long, semi-structured corporate governance document and output it as a clean, validated table suitable for review and downstream analysis.
 
## Persona
You are a meticulous financial data analyst at Morgan Stanley with deep experience in corporate governance disclosures and SEC filings. You work on the team that ingests proxy statement data into internal systems for board benchmarking and governance analysis. You are known for your precision with names, dates, and committee structures, your discipline around footnote handling, and your refusal to infer values that aren't explicitly stated. When a field isn't disclosed, you mark it "Not disclosed" rather than guess.
 
## Context
Use the attached Morgan Stanley 2026 Proxy Statement as the sole source of truth. The user wants a structured table of the director nominees put forward for election at the 2026 annual meeting, suitable for review by the governance team.
 
## Expectations
- Extract the following fields for each 2026 director nominee:
  * Full name
  * Age
  * Director since (year only)
  * Independent (Yes / No)
  * Primary occupation (current role and employer as disclosed)
  * Committee memberships
  * Committee chair roles (or "None")
  * Other public company boards (or "None")
  * Notes (any footnoted qualifiers, e.g., "Lead Independent Director",
    "Chair effective [date]")
 
- Output as a table, one row per nominee, with the fields above as columns in the order listed
- For list-type fields (committees, other boards), separate multiple values with semicolons within the cell
- Preserve exact names, titles, and company names as they appear in the document; do not abbreviate, paraphrase, or standardize
- Use "Not disclosed" for any field not explicitly stated for a given nominee; do not infer or fill from external knowledge
- Only include directors being put forward for the 2026 vote; exclude any directors who are stepping down, retiring, or not standing for re-election (these may be mentioned alongside nominees — read carefully)
 
- After the table, provide a short validation summary:
  * Total number of nominees extracted
  * Any fields that were missing or inconsistent across nominees
  * Any ambiguities encountered and how you resolved them
 
- If the user requests a different output format afterward (CSV, JSON, etc.), re-emit the same data in that format without re-extracting
```

## **Part 10 — Process Mapping (5-prompt chain)**

This is a connected sequence: each prompt builds on the output of the previous one. Run them in order, in the same conversation, so the model has access to all the prior outputs as context. None of these demos requires an attached file — the source content lives inside the prompts themselves.

### **Demo 22 — Step 1: Capture the as-is process**

Turn a messy verbal description into a structured numbered process map. Notice the \[unclear\] flag — the prompt instructs the model to surface gaps rather than guess.

```
## Goal
Capture an "as-is" process map from the description below. Surface every step, decision point, handoff, and waiting period exactly as it happens today — not how it should happen, and not a cleaned-up version.
 
## Context
The description is from a senior team member who has done this job for 10 years. It's conversational, informal, and almost certainly incomplete. I need the capture to reflect the actual messiness of the source so I can have a useful follow-up conversation with them about the gaps.
 
## Source
"Okay, so when a new client comes in, usually the advisor emails me their details, sometimes it's in a PDF, and sometimes just in the body of the email. I check everything's there; if it's not, I email them back and wait — that can take a few days. Once I've got everything, I open a case in the CRM and then I have to upload the KYC docs to the compliance portal, which is a different system. Compliance reviews it, usually takes 2-3 days, sometimes longer if they have questions which come back to me, and I have to ask the advisor. When compliance approves, I manually create the account in the trading platform, and then I email the advisor to say it's ready. Oh, and I also have to set up the billing record separately in the finance system."
 
## Expectations
Produce a numbered list of steps in the order they happen. For each step, include:
- Step number and short title
- Actor (who does it)
- System (which tool or platform)
- Estimated time
- Type: [Action] / [Wait] / [Decision] / [Handoff]
 
## Example of the format I want (use this shape exactly)
1. Advisor submits client details
   - Actor: Advisor
   - System: Email (inbound)
   - Time: n/a (trigger event)
   - Type: [Handoff] — Advisor → Operations
 
2. Operations checks submission completeness
   - Actor: Operations analyst
   - System: Email / [unclear — no checklist tool mentioned]
   - Time: ~5 minutes
   - Type: [Decision] — complete vs. incomplete
 
## Guardrails
- Do NOT invent details that are not in the source. If something is unclear (system name, exact timing, who performs a step), write [unclear] and keep going. Do not guess.
- Do NOT tidy the process up. If the source implies the step happens in a clunky or redundant way, preserve that.
- Preserve every waiting period and every handoff, even if they seem obvious.
- At the very end, add a section titled "Gaps to clarify with the SME" that lists every [unclear] item plus any ambiguity you noticed that a new hire would trip over.
```

### **Demo 23 — Step 2: Visualize the process as a flowchart**

Generates Python code (graphviz) that you can run to produce a PNG flowchart from the as-is map you just created.

```
## Goal
Write a short Python script using the `graphviz` library that turns the as-is process map above into a flowchart PNG.
 
## Context
The PNG will go into a slide for a stakeholder review. Audience: operations leaders who will skim, not read. The visual needs to make the handoffs and waiting periods jump off the page.
 
## Source
The numbered as-is process map from the previous step. Every box in the diagram must come from a step in that map.
 
## Expectations
- Return a single Python code block and nothing else.
- Layout: top to bottom.
- Style the boxes like this:
  - Start and End: grey ovals
  - Action steps: blue rounded boxes
  - Waiting periods: orange boxes with a dashed border
  - Decision points: white diamonds
- Label arrows with the handoff when one occurs (e.g., "Advisor → Ops").
- Keep the text inside each box to 4 short lines max.
- Save the output as `onboarding_process.png`.
 
## Guardrails
- Every box must match a step in the process map. Do not invent steps.
- If a step was marked [unclear], keep that note inside the box label.
- Keep waiting periods as their own orange dashed box — do not merge them into the step before.
- Use short, simple IDs for boxes (like S, A1, D1, W1). Only put words and spaces in the LABELS, never in the IDs.
```

### **Demo 24 — Step 3: Identify friction in the as-is process**

Now ask the model to find specific issues in the process map. The output is a structured table that feeds directly into the next prompt.

```
## Goal
Analyze the as-is process map above and identify opportunities for simplification. The output feeds directly into the next prompt, which will design a to-be process, so the issues need to be specific and actionable.
 
## Context
We're looking for the kinds of issues that operations leaders can act on: handoffs that could be collapsed, waiting periods caused by manual coordination, steps done in two systems that could be one, and so on. We are NOT looking for generic advice ("consider automation"). Every finding must point to a specific step or pair of steps from the map.
 
## Source
The as-is process map from above. Do not reference external best practices or generic process-improvement knowledge — everything you flag must be traceable to a step that actually appears in the map.
 
## Expectations
Produce a Markdown table with these columns, in this order:
| # | Issue | Where it occurs (step #) | Why it's a problem | Category | Impact |
 
Categories (use these exact labels):
- Duplication
- Unnecessary handoff
- Manual step (automatable)
- Waiting period
- Missing standardization
- Rework risk
 
Impact: High / Medium / Low, based on a combination of time cost and error risk. State the reason for the rating in the "Why it's a problem" cell; do not just assert it.
 
## Example row (use this level of specificity)
| 1 | KYC docs uploaded manually to a second system after case is already opened in CRM | Steps 4–5 | Same document set is handled twice across two systems with no integration, creating ~10 min of duplicate keying per client and a re-key error risk that compliance has to catch downstream | Duplication | High |
 
## Guardrails
- Only flag issues that are visible in the as-is map. If you are inferring based on "this usually happens" rather than what the map shows, prefix the issue with [inference] so the user knows to validate it.
- Do NOT suggest solutions in this table — that is the next prompt's job. Describe the problem only.
- Do NOT say things like "slow" or "inefficient" without saying what specifically causes the slowness or inefficiency. Every "Why it's a problem" cell must name the mechanism.
- Aim for 5–10 issues. If there are fewer real ones, return fewer. Do not pad.
```

### **Demo 25 — Step 4: Propose a simplified to-be process**

The model now designs a realistic, improved version that addresses the issues from Demo 23\. Anything requiring new tooling or policy goes in Phase 2 instead.

```
## Goal
Propose a simplified "to-be" version of this process that addresses the High and Medium issues from the previous step.
 
## Context
This will be used as a discussion document with operations leadership. They want realism, not a greenfield redesign — we need something we could start implementing next quarter with the people and systems we already have. Anything that requires new software, new integrations, or policy change goes into a separate "Phase 2" list at the end, so we can discuss it but not block on it.
 
## Source
Use the as-is process map and the friction table from above. Every change you propose must address at least one issue from the table. Do not introduce changes that don't map to a flagged issue.
 
## Expectations
Return three sections:
 
### Section A: To-be process map
Numbered list of steps in the same format as the as-is map (Step number, Actor, System, Time, Type). Same shape, so it can be dropped straight into the Mermaid prompt to regenerate the diagram.
 
### Section B: Change log
A table mapping each change back to the issues it resolves: | Change | Issues addressed (# from friction table) | Rationale |
 
### Section C: Phase 2 (requires investment)
Bullet list of changes that WOULD meaningfully improve the process but require new tooling, integrations, or policy approval. One line each.
 
## Guardrails
- Do NOT assume new tools appear. If a change requires a system that doesn't exist in the as-is map, it belongs in Phase 2, not Section A.
- Do NOT drop steps that exist for regulatory or compliance reasons (KYC review, compliance approval) even if they feel like friction. You can change HOW they happen, not WHETHER they happen.
- Every step removed from the as-is map must be justified in Section B. Silent deletions are not allowed.
- If an as-is step was marked [unclear], carry that uncertainty forward rather than resolving it by guessing.
```

### **Demo 26 — Step 5: Draft a formal SOP from the to-be process**

The final step in the chain. The model produces a downloadable Word document that a new hire could follow on day one, using the to-be process as its factual spine.

```
## Goal
Draft a formal Standard Operating Procedure for the to-be client onboarding process. The output should be a Word document that a new operations hire could follow on day one.
 
## Context
The SOP will live on our operations intranet. Audience: new operations hires with basic financial services knowledge but no prior experience with our specific systems. They will read this document while doing the task for the first time, so ambiguity is expensive — every step must leave them knowing what to click or who to contact next.
 
## Source
The to-be process map (Section A) from Demo 4. Use this as the factual spine of the Procedure section. Do not introduce steps, systems, or approvals that are not in that map.
 
## Expectations
- Output the SOP as a downloadable .docx file named Client_Onboarding_SOP.docx.
- Structure the SOP with these sections, in this order:
 
1. **Purpose** — one paragraph on what this procedure achieves and for whom.
2. **Scope** — bullet list of "this SOP applies when..." and "this SOP does NOT apply when..." so edge cases route elsewhere.
3. **Roles and responsibilities** — table of Role | Responsibility in this procedure.
4. **Prerequisites** — what must be in place before Step 1 can start (access, approvals, information, training).
5. **Procedure** — numbered steps, each with:
   - What to do
   - Which system / where
   - Expected output/completion signal
   - Who to contact if blocked
6. **Exceptions and escalations** — table of Scenario | What to do | Escalation contact.
7. **Related documents** — placeholder list with bracketed TODOs, e.g., [Link: KYC policy], [Link: Advisor onboarding form template].
8. **Review cadence** — suggested review interval and owner role (not a named person).
 
## Guardrails
- Do NOT invent company-specific policies, system names, team names, or escalation contacts. Use [bracketed placeholders] for anything the author needs to fill in before publishing.
- Do NOT add regulatory or compliance language beyond what is in the source process. If a step needs a compliance reference, use [Reference: applicable policy] as a placeholder.
- Use plain language. If you must use jargon, define it on first use.
- Do NOT pad the Purpose or Scope sections with filler. One tight paragraph is better than three vague ones.
- If an as-is step was carried forward as [unclear] in the to-be map, carry it forward here as [unclear — confirm with SME] rather than guessing the resolution.
```

