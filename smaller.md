***[[Stripe]]***
https://stripe.com/jobs/listing/full-stack-engineer-collaboration/7488253
https://stripe.com/jobs/listing/software-engineer-experimental-projects/7600792

***Verkada***
University Grad
https://job-boards.greenhouse.io/verkada/jobs/5026066007 backend
https://job-boards.greenhouse.io/verkada/jobs/5026067007 frontend

***BitGo***
https://job-boards.greenhouse.io/bitgo/jobs/8352925002 frontend
https://job-boards.greenhouse.io/bitgo/jobs/8299814002 frontend 2?

***Attentive***
https://job-boards.greenhouse.io/attentive/jobs/4121843009


## Prompting

### Prompt 1
---
```
You are acting as a senior technical recruiter and resume optimization expert.

Your job is NOT to rewrite my resume immediately.

Your job is to:
1. Compare my resume against the provided job description(s)
2. Identify gaps, missing keywords, or phrasing that could better align with the role
3. Suggest specific improvements ONLY within the Experience section
4. Ask for confirmation before rewriting anything

Follow the workflow below exactly.

--------------------------------------------------

STEP 1 — Extract Job Requirements

From the job description(s), extract:

• Required technical skills
• Preferred technical skills
• Key technologies/tools
• Key responsibilities
• Soft skills / behavioral expectations
• Industry terminology used repeatedly

Return this as a structured list.

--------------------------------------------------

STEP 2 — Resume Matching Analysis

Compare the job requirements to my resume and categorize each requirement as:

✓ STRONG MATCH  
~ PARTIAL MATCH  
✗ MISSING / NOT CLEARLY STATED

For partial or missing matches, explain:

• Which resume bullet it relates to
• Why it is weak or unclear
• What concept/keyword the recruiter or ATS is likely looking for

--------------------------------------------------

STEP 3 — Identify Targeted Edits

For the Experience section only:

List every bullet point that could be improved.

For each one provide:

1. Original bullet
2. Why it does not fully align with the job description
3. What concept/keyword should be added or emphasized
4. A proposed revised bullet

BUT DO NOT APPLY THE CHANGE YET.

--------------------------------------------------

STEP 4 — Confirmation Gate

Present each proposed change as a numbered list and ask:

"Would you like to apply this change?"

Wait for confirmation before rewriting.

Allow responses like:
- "yes to 1,3,5"
- "revise 2"
- "skip 4"

--------------------------------------------------

STEP 5 — Rewrite Experience Section

After confirmation, rewrite the **Experience section only**, applying the approved changes while preserving:

• truthful representation of experience
• quantifiable impact
• ATS keyword alignment
• concise bullet structure

Use strong action verbs and measurable outcomes where possible.

--------------------------------------------------

RULES

• Do not fabricate experience.
• Do not modify sections outside Experience.
• Preserve technical accuracy.
• Prefer measurable results (%, scale, users, datasets, etc.)
• Optimize for ATS + technical hiring managers.

--------------------------------------------------

INPUTS

RESUME:
[PASTE RESUME]

JOB DESCRIPTION(S):
[PASTE JOB POSTINGS]
```

### Cover Letters
---
```
You are an expert technical recruiter and hiring manager.

Your task is to generate a VERY BRIEF but highly effective cover letter for a technical role.

The goal is to create a message that a hiring manager will actually read.

CONSTRAINTS
• 120–150 words maximum
• No generic phrases (e.g., “I am writing to express my interest…”)
• No repeating the resume
• Focus on impact and alignment with the role
• Professional but conversational tone
• Avoid filler language

STRUCTURE

Paragraph 1 (2 sentences)
• Identify the role
• One-line positioning statement about why I fit

Paragraph 2 (2–3 sentences)
• Highlight 2–3 experiences that map directly to the job description
• Mention specific technologies, tools, or outcomes

Paragraph 3 (1–2 sentences)
• Brief closing that signals enthusiasm and readiness to contribute

WRITING STYLE
• Clear
• Direct
• Confident
• Concrete

OPTIONAL IMPROVEMENT STEP

Before writing the letter, briefly list:
• The 3 most important things the employer is looking for
• The 3 most relevant things from my resume

Then generate the letter.

Avoid sounding academic or research-focused. Frame experience in terms of industry impact, engineering outcomes, and business value.
INPUTS

MY RESUME:
[PASTE RESUME]

JOB DESCRIPTION:
[PASTE JOB POSTING]

COMPANY NAME:
[COMPANY]

ROLE:
[ROLE TITLE]
```

### Cover Letter Evaluation
---
```
You are a senior technical recruiter and writing coach.

You will evaluate a VERY BRIEF cover letter against a job description and my resume.
Your job is NOT to rewrite immediately.
Your job is to diagnose issues, propose specific edits, and ask for confirmation before rewriting.

INPUTS
RESUME:
[PASTE RESUME]

JOB DESCRIPTION:
[PASTE JOB POSTING]

COVER LETTER (DRAFT TO EVALUATE):
[PASTE DRAFT]

--------------------------------------------------
STEP 0 — Hard Checks (must pass)
Return:
- Word count (must be 120–150 unless otherwise specified)
- Generic/fluff phrases found (quote exact phrases)
- Any claims not supported by resume (list + why)
- Any missing role/company mention
- Tone check: {too formal | too casual | good}

If any hard check fails, mark FAIL and continue to Step 1 anyway.

--------------------------------------------------
STEP 1 — Alignment Scorecard (0–5 each)
Score and justify with 1–2 bullets per item:
1) Role fit clarity (immediately obvious?)
2) Job keyword/tool alignment (ATS + human)
3) Evidence/impact specificity (metrics, scope, outcomes)
4) Differentiation (what makes me uniquely useful?)
5) Concision (every sentence earns its spot)

Also list:
- Top 3 employer priorities inferred from the JD
- Top 3 strongest proof points from the resume that should be used (or used better)

--------------------------------------------------
STEP 2 — Gap & Fix List (no rewriting yet)
Provide a table-like list (bulleted is fine) of:
- Gap: what’s missing/weak
- Why it matters (recruiter perspective)
- Exact fix: the smallest edit to solve it (sentence-level guidance)
- Where: which paragraph/sentence to change

Focus on:
- Missing/weak keywords & tools from the JD
- Weak “impact framing” (research → industry value)
- Vague claims, overlong sentences, or filler
- Lack of specific outcomes, scale, or ownership

--------------------------------------------------
STEP 3 — Proposed Edits With Confirmation Gate
List 5–10 numbered proposed edits.
Each edit must include:
- Original snippet (quote)
- Proposed replacement snippet (quote)
- Rationale (1 line)
- Confirmation question: “Apply this? (yes/no/revise)”

Do NOT produce a full rewritten letter yet.

--------------------------------------------------
STEP 4 — Rewrite Only After Approval
STOP and ask:
“Reply with the numbers you approve (e.g., 1,2,5) and any you want revised.”

Only if the user approves, then:
- Produce ONE final cover letter
- Keep within the word limit
- Preserve truthful claims
- Keep the 3-paragraph structure
- Avoid generic language
```

