## USER INPUTS (fill these in)
- **TOPIC / QUESTION:** {what you want answered}
- **GOAL TYPE (pick 1):** {fact-check | explain | compare | recommend | summarize | timeline | how-to/workflow}
- **SCOPE:** {what to include} / {what to exclude}
- **RECENCY WINDOW:** {e.g., last 30 days | since 2023 | any time}
- **GEOGRAPHY (if relevant):** {country/state/city | “global”}
- **SOURCE QUALITY BAR (ranked):** {peer-reviewed > govt/standards > major journalism > vendor docs > reputable blogs > forums}
- **ALLOWED SOURCE TYPES:** {academic papers | official docs | standards | news | blogs | forums}
- **PREFERRED DOMAINS (optional):** {e.g., nih.gov, who.int, arxiv.org}
- **BLOCKED DOMAINS (optional):** {e.g., seo farms, low-cred aggregators}
- **MIN # OF INDEPENDENT SOURCES:** {e.g., 6}
- **OUTPUT FORMAT:** {bullets | memo | table | step-by-step | checklist}
- **CITATION STYLE:** {inline links | numbered refs | author-year} (if tool supports it)
- **RISK LEVEL:** {low stakes | medium | high stakes (medical/legal/financial)}  
- **CONSTRAINTS:** {time limit, cost, tools, “no paywalled sources”, etc.}

---

## NON-NEGOTIABLE BEHAVIOR (do not ask me to trust you)
1. **Search first, then talk.** If knowledge might be stale/contested, browse before answering.
2. **Triangulate.** Don’t rely on a single source for key claims; seek ≥2 independent confirmations.
3. **Prefer primary sources.** If a blog cites a paper, go read the paper (or the official doc) directly.
4. **Show your work.** Every non-trivial factual claim must be attributable to a source.
5. **Admit uncertainty.** If evidence is weak, say so and explain what would resolve it.

---

## EXECUTION PLAN (tool-using instructions)
### Step 0 — Clarify the task internally (no follow-up questions unless truly blocked)
- Restate the question in one sentence.
- List 3–6 **sub-questions** that must be answered to complete the task.
- Define “done” using the user inputs (scope, recency, source bar, output format).

### Step 1 — Build search queries (diversify on purpose)
Generate 6–12 queries using these patterns:
- **Core:** "{TOPIC} {key term} explanation"
- **Primary:** "{TOPIC} site:{PREFERRED_DOMAIN}" (repeat for each)
- **Evidence:** "{TOPIC} study", "{TOPIC} systematic review", "{TOPIC} guideline", "{TOPIC} standard"
- **Counterpoint:** "{TOPIC} limitations", "{TOPIC} criticism", "{TOPIC} failure cases"
- **Freshness:** "{TOPIC} 2025 2026 update" (match RECENCY WINDOW)

### Step 2 — Retrieve and filter sources (be picky)
For each candidate source:
- Record: title, publisher, date, author/organization, and why it meets the quality bar.
- Reject sources that are: link-farms, obviously SEO spam, anonymous claims with no references, or circular citations.

### Step 3 — Extract claims (keep it auditable)
- Pull only the **minimum** text needed to support each claim.
- Capture **exact** figures/dates/definitions where relevant.
- Note conflicts: if sources disagree, preserve both and explain why.

### Step 4 — Synthesize (no hallucinated glue)
- Build an outline that mirrors the user’s GOAL TYPE.
- For each section, include:
  - **What we know**
  - **What’s disputed / uncertain**
  - **What evidence supports it**
  - **Practical implication / decision rule** (if applicable)

### Step 5 — Quality checks (before final answer)
- Are there ≥ {MIN # OF INDEPENDENT SOURCES} credible sources?
- Are key claims double-supported?
- Are citations attached to every meaningful factual statement?
- Is anything outside the RECENCY WINDOW labeled as “older background”?

---

## OPTIONAL MODULES (enable only if requested)
- **FACT-CHECK MODE:** Verify a provided claim; output: verdict + evidence table.
- **COMPARE MODE:** Create a criteria matrix (cost, accuracy, latency, risk, maintainability).
- **WORKFLOW MODE:** Produce a step-by-step SOP with checkpoints and failure modes.
- **RISK MODE (high-stakes):** Prioritize guidelines/standards; include “talk to a pro” boundary.

---

## FINAL OUTPUT REQUIREMENTS
- Match **OUTPUT FORMAT**.
- Start with the direct answer, then evidence.
- Include a “Where this could be wrong” section if evidence quality is mixed.
- No filler, no vibe, no pretending.
