# Automation BA Toolkit — Assessment, Scoping & Business Case Suite

A suite of four linked browser-based tools that replicate the complete Business Analysis workflow for both classic RPA and probabilistic AI agents. Built as a portfolio piece demonstrating practical Business Analysis methodology — from initial automation suitability assessment through to structured design documentation and financial justification.

No installation. No account. Runs entirely in the browser.

**Live tool:** [joshdeadbody.github.io/PDD-planer](https://joshdeadbody.github.io/PDD-planer/)

---

## The Workflow

The tools are designed to be used in sequence, branching based on the project phase and solution type:

1. Open the **Process Assessment Tool** (`index.html`) — the default page at the link above
2. Complete the suitability assessment for your process
3. Choose your pipeline: Click **"Send to RPA PDD Planner"**, **"Send to Agentic Planner"**, or **"Build Business Case"** — parameters pass automatically via URL
4. The selected Planner or Builder opens with all relevant context pre-filled
5. Complete the remaining discovery phases and export your Markdown document

---

## Tool 1 — Process Assessment Tool

Based on UiPath's automation suitability scoring model. Determines whether a process is worth automating before any discovery work begins, and helps decide if the solution requires rigid RPA or an autonomous agent.

**Eliminatory gates** — hard stops that end the assessment immediately if triggered:
- Non-digital or heavily physical input types
- Process relies entirely on subjective human judgment

**Postponement gates** — flags that don't eliminate but mark the process as not yet ready:
- Process or supporting applications are actively changing or unstable

**Weighted scoring** — once past the gates, the tool scores across:
- Process complexity and number of steps
- Data structure (structured vs. unstructured)
- Volume, frequency, and average handling time
- FTE bandwidth calculation running in parallel
- Multipliers applied automatically for thin client environments (1.6×) and OCR dependency (1.2×)

**AI reviewer** — reads both the hard scores and the free-text notes, providing a structured assessment of viability, flagged risks, and recommended next steps before you choose a planner.

---

## Tool 2 — Classic RPA PDD Planner

Structures the Process Discovery Document for deterministic, hard-coded robots. Focuses on mapping the exact "happy path" and strict exception handling.

**Phases:**
1. AS-IS Process Mapping
2. Business Value & ROI
3. Technical & Business Exceptions
4. Dependency Mapping
5. TO-BE State Definition
6. Edge Case Audit
7. PDD Readiness Gate

**AI Reviewer Persona:** Acts as a Feasibility Challenger, checking for missing exceptions, unstructured data risks, and generating a Mermaid.js Top-Down flowchart of the mapped process.

---

## Tool 3 — Agentic Automation Planner (AAP)

Structures the design document for probabilistic AI agents. Shifts the BA focus away from step-by-step instructions toward mapping objectives, tool boundaries, and risk mitigation.

**Phases:**
1. Mission & Context (Objective States, Context Payloads, KPIs)
2. The Toolkit (Data Sensitivity, Tool Scopes, Blacklists)
3. Guardrails & Boundaries (Behavioral Rules, Limitations)
4. Autonomy & Handoffs (Confidence Thresholds, Escalation Triggers)
5. Identity, Access & Governance (Execution Scopes, Blast Radius, Compliance)
6. Verification Artifacts & Audit Gates (Deterministic Proof of Work)
7. Readiness Gate

**AI Reviewer Persona:** Acts as a Risk Assessor. Aggressively challenges weak guardrails, broad permissions, and lack of deterministic verification. Generates Mermaid.js State Machine diagrams or Capability Maps to visualize boundaries.

---

## Tool 4 — Business Case Builder

Structures the financial justification and executive sign-off for automation initiatives. Translates technical scoping into business value to secure budget approval.

**Core Features & Phases:**
- **Live ROI Dashboard:** Auto-calculates Total Cost, Annual Benefit, 12-Month ROI, and Payback Period.
- **The Financial Model:** Input dev costs and infra expenses against FTE savings, visualized via a Chart.js cumulative cash flow graph.
- **Strategic Benefits:** Maps qualitative outcomes (Productivity, Quality, Employee Experience).
- **Risks & Mitigation:** Pre-filled with exceptions and boundaries from the assessment phase.
- **Recommendation & Sign-Off:** Final executive verdict and narrative.

**AI Reviewer Persona:** Acts as a strict CFO / Financial Approver. Challenges underestimated costs, overly optimistic savings, and scores the likelihood of budget approval.

---

## AI & API Setup

All four tools use a **proxy by default** — no API key required. This ensures the AI reviewer works out of the box for anyone accessing the tool, including recruiters or practitioners who may not have their own key.

**Using your own key and model:**

The tools support any OpenAI-compatible endpoint. In the API settings panel:
- Paste your **Base URL** (e.g. `https://api.openai.com/v1`, `https://openrouter.ai/api/v1`, or any compatible endpoint)
- Paste your **API Key**
- Specify the **model name** (e.g. `gpt-4o`, `o1`, `gemini-2.5-pro`, `mistral-large`)

This means the tools are compatible with OpenAI, OpenRouter, Anthropic (via compatible wrappers), locally hosted models via Ollama, or any provider following the OpenAI API standard.

**Note on model choice:** The default proxy uses Gemini 2.5 Flash — fast and cost-efficient. For production use with complex agentic guardrails or deeply interdependent RPA processes, a reasoning model (e.g. `o1`, `gemini-2.5-pro`) will produce more rigorous architectural challenges.

---

## Methodology Notes

**Assessment Tool** — the scoring model and gate logic are based on industry-standard suitability frameworks, adapted for browser-based use with additional weighting for thin client and OCR scenarios that are commonly underestimated during scoping.

**Deterministic vs. Probabilistic Scoping** — The split between the two planners reflects the reality of modern automation. If a process relies on stable UIs and structured data, the RPA PDD Planner ensures tight, step-by-step governance. If a process relies on unstructured data and dynamic routing, the Agentic Planner ensures the blast radius is contained and the agent's output is highly auditable.

**The Business Case Handoff** — The addition of the Business Case Builder bridges the gap between technical Business Analysis and executive sponsorship. It ensures that before a line of code is written, the initiative makes financial sense and has a clear payback period.

**URL-based handoff** — the tools pass parameters to each other via URL rather than localStorage. This keeps them stateless, independently usable, and easy to share or bookmark at any point in the workflow.

---

## License

MIT — free to use, modify, and deploy, including within an organisation. See `LICENSE` for details.

---

*Built by Joshua Tutuianu | RPA & Agentic BA Portfolio | [GitHub](https://github.com/joshdeadbody)*
