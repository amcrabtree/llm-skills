# Lab Brief — Design Guide

## Core Philosophy

The Lab Brief exists to answer three questions a busy PI or PM has when they see it:
1. **"Is this person making progress?"** → Yes/No, fast.
2. **"Is this work competitive / fundable / publishable?"** → Field Position section.
3. **"What do I need to do?"** → The Ask.

Everything else is secondary. If a sentence doesn't serve one of those three questions, cut it.

---

## Audience-Specific Guidance

### For the PI (Brian archetype: clinical genomics background, grant-focused, time-poor)
- Lead with the *significance*, not the method
- Name-drop competitor groups or top-tier venues: "This puts us ahead of what [group] published in *Nature Methods* last month"
- Tie to grant aims explicitly if known: "This directly supports Aim 2 of [grant name]"
- Never assume they remember what you told them last time — one-sentence project context always
- Use the word "novel" carefully — only if you can back it up with the Field Position

### For the PM (Alex archetype: immunobiology PhD, task-management focused, ML-cautious)
- Progress should be legible without technical depth
- Milestone badges and status indicators help her see "on track / off track"
- The "Ask" section is especially for her — give her something actionable
- Avoid jargon acronyms without a brief gloss the first time (e.g., "mIF (multiplex immunofluorescence)")

---

## Tone

- **Confident but not boastful** — describe results plainly; the field context does the bragging for you
- **Concise** — every word earns its place; no throat-clearing ("In this update I will...")
- **Human** — one casual aside is fine ("This one surprised me.")
- **Forward-looking** — always end on momentum, not on a list of problems

---

## Visual Element Rules

Always include at least one visual. In priority order:

1. **User-provided figure** — embed directly, write a clear caption
2. **Mermaid diagram** — use for pipelines, model architectures, workflows, decision trees
3. **Table** — use for comparison (methods vs. methods, results vs. benchmarks)
4. **Quarto callout with structured data** — use when a figure isn't available but data can be displayed inline

### Mermaid diagram guidance
- Pipeline diagrams: `graph LR`
- Decision flows: `flowchart TD`
- Keep node labels short (≤4 words)
- Add a `%%| fig-cap:` annotation

---

## Field Position Section

This is the most important section for Brian. Rules:

- Cite 1–2 papers. Real if possible; if the user doesn't provide them, use plausible recent citations in the relevant subfield (spatial transcriptomics, computational pathology, mIF analysis, etc.) and note they should verify
- Frame the user's work as: *ahead of / in line with / extending / the first to...*
- One sentence max per paper
- The callout box (`::: {.callout-note}`) visually sets this apart — keep it

---

## The Ask

This is the most important section for both audiences. Rules:

- Must be *specific*: not "feedback welcome" — instead: "Do you want me to prioritize X before Y?" or "I need access to Z to proceed" or "Should we share this with [collaborator] now?"
- One ask only. If there are multiple, pick the most important
- If no ask exists, use: "No action needed — flagging for awareness. Next update in [timeframe]."

---

## Length and Format

- **Total body word count**: Under 600 words
- **Sections**: Exactly these four — What I Did / Why It Matters / What's Next / Ask
- **Subsections**: Avoid — keep it scannable
- **Emoji section headers**: Yes — they help busy readers scan at a glance (🔬 📍 ⏭️ ✋)
- **Bold**: Use sparingly for key terms or results only

---

## Quarto-Specific Notes

- Always set `embed-resources: true` so the HTML is a single portable file
- `execute: echo: false` hides code blocks from the rendered output
- `toc: false` — the document is short enough to not need a TOC
- The `{=html}` raw blocks for header/footer badges require Quarto ≥ 1.3
- Mermaid diagrams render natively in Quarto HTML — no extra plugin needed
- If the user has a custom CSS file, note that `styles.css` can be replaced or omitted