# RPA BA Toolkit — Process Assessment & PDD Planner

Two linked browser-based tools that replicate the BA workflow for RPA scoping. Built as a portfolio piece demonstrating practical RPA Business Analysis methodology — from initial automation suitability assessment through to a structured Process Discovery Document.

No installation. No account. Runs entirely in the browser.

**Live tool:** [joshdeadbody.github.io/PDD-planer](https://joshdeadbody.github.io/PDD-planer/)

---

## The Workflow

The two tools are designed to be used in sequence:

1. Open the **Process Assessment Tool** (`index.html`) — the default page at the link above
2. Complete the suitability assessment for your process
3. Click **"Send to PDD Planner"** — 13 parameters pass automatically via URL
4. The **PDD Planner** opens with all relevant fields pre-filled
5. Complete the remaining discovery phases and export your PDD

---

## Tool 1 — Process Assessment Tool

Based on UiPath's automation suitability scoring model. Determines whether a process is worth automating before any discovery work begins.

**Eliminatory gates** — hard stops that end the assessment immediately if triggered:
- Non-digital or heavily physical input types
- Process relies on human judgment rather than defined rules

**Postponement gates** — flags that don't eliminate but flag the process as not yet ready:
- Process or supporting applications are actively changing or unstable

**Weighted scoring** — once past the gates, the tool scores across:
- Process complexity and number of steps
- Data structure (structured vs. unstructured)
- Volume, frequency, and average handling time
- FTE bandwidth calculation running in parallel
- Multipliers applied automatically for thin client environments (1.6×) and OCR dependency (1.2×)

**Notes field** — every question has a free-text notes field. These are read by the AI reviewer, which flags risks that scores alone don't capture.

**AI reviewer** — reads both the hard scores and the notes, then provides a structured assessment of automation viability, flagged risks, and recommended next steps.

---

## Tool 2 — PDD Planner

Structures the full Process Discovery Document across seven phases. Receives context from the Assessment Tool automatically and pre-fills all relevant fields on load.

**Phases:**
1. AS-IS Process Mapping
2. Business Value & ROI
3. Technical & Business Exceptions
4. Dependency Mapping
5. TO-BE State Definition
6. Edge Case Audit
7. PDD Readiness Gate

**Additional features:**
- AI reviewer with conversational follow-up per phase
- Auto-generated Mermaid.js process flowchart rendered directly in the tool
- Markdown export of the completed PDD

---

## AI & API Setup

Both tools use a **proxy by default** — no API key required. This is intentional: the proxy ensures the AI reviewer works out of the box for anyone accessing the tool, including recruiters or practitioners who may not have their own key or whose organisation policy prevents them entering one.

**Using your own key and model:**

Both tools support any OpenAI-compatible endpoint. In the API settings panel:
- Paste your **Base URL** (e.g. `https://api.openai.com/v1`, `https://openrouter.ai/api/v1`, or any compatible endpoint)
- Paste your **API Key**
- Specify the **model name** (e.g. `gpt-4o`, `o1`, `gemini-2.5-pro`, `mistral-large`)

This means the tools are compatible with OpenAI, OpenRouter, Anthropic (via compatible wrappers), locally hosted models via Ollama, or any provider following the OpenAI API standard.

**Note on model choice:** The default proxy uses Gemini 2.5 Flash — fast and cost-efficient for a portfolio demo. For production use with complex, interdependent processes, a reasoning model (e.g. `o1`, `gemini-2.5-pro`) will produce more reliable outputs where multiple dependencies need to be weighed simultaneously.

---

## Methodology Notes

**Assessment Tool** — the scoring model and gate logic are based on UiPath's published automation suitability framework, adapted for browser-based use with additional weighting for thin client and OCR scenarios that are commonly underestimated during scoping.

**PDD vs SDD** — this toolkit covers the PDD layer only: what the user does now, what the business problem is, and what the automated process should achieve. Solution design (how the bot will technically implement the solution) is intentionally out of scope and belongs in a separate SDD produced by the developer or solutions architect.

**URL-based handoff** — the Assessment Tool passes parameters to the PDD Planner via URL rather than localStorage. This is deliberate: it keeps the tools stateless, independently usable, and easy to share or bookmark at any point in the workflow.

---

## License

MIT — free to use, modify, and deploy, including within an organisation. See `LICENSE` for details.

---

*Built by Josh | RPA BA Portfolio | [GitHub](https://github.com/joshdeadbody)*
