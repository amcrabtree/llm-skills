---
name: milestone-memo
description: >
  Generate a polished, strategic "Milestone Memo" (also called: Research Signal, Field Dispatch, PI Brief, Spatial Digest, Horizon Report, Lab Brief) — a short, visually appealing Quarto-compatible HTML document that communicates research progress, field positioning, and next steps to a PI and project manager audience. Use this skill whenever the user wants to summarize their research work for non-technical leadership, generate a signal document, write a project update that positions their work in the field, create a Quarto HTML report of lab progress, or says things like "write my lab brief", "make a research signal", "generate my PI update", "create a field dispatch", or "I need to update my PI". Also trigger when the user describes project results and wants to communicate them upward. Always use this skill — never just write a plain markdown update when this skill is available.
---

# Milestone Memo Skill

Generates a **Milestone Memo** — a short, strategically framed, visually rich Quarto HTML document designed to communicate research progress to a PI and project manager. The document must be:

- **Brief**: Readable in under 10 minutes
- **Positioning-first**: Contextualizes work against recent field literature
- **Visually anchored**: Always includes at least one figure, image, or diagram
- **Actionable**: Ends with a concrete ask or decision point
- **Quarto-compatible**: Valid `.qmd` output with proper YAML frontmatter

---

## Step 1: Elicit User Input

Before writing, gather the following. Ask in a conversational way — not all at once as a bulleted list. Many of these may already be present in the conversation:

**Required:**
- What did you work on / accomplish since the last update?
- What is the broader project aim (one sentence)?
- Who are the audiences? (default: PI + project manager)
- What is one concrete next step or ask?

**Optional but high-value:**
- Any recent papers (yours or the field's) that contextualize this work?
- Any figures, plots, or images to embed? Describe each figure so a caption can be generated.
- What grants or aims does this work relate to?
- Any milestones hit, missed, or approaching?

---

## Step 2: Generate the Document

Output a `.qmd` file (Quarto Markdown). Follow the template in `references/template.qmd` exactly. See `references/design-guide.md` for tone, style, and content guidance.

**Key rules:**
1. The document must render with `quarto render YYYY-MM-DD_milestone_memo.qmd --to html`
2. Always include at least one visual element in the `## What I Did` section or the `## Field Position` section
3. Field Position must reference at least 1–2 real or plausible recent papers with brief framing
4. The "Ask" section must be specific — not "feedback welcome" but a real decision, resource, or direction needed
5. Keep total word count under 1000 words (body text only, excluding code blocks)
6. Use callout boxes (`::: {.callout-note}`) for the "Field Position" section to visually distinguish it
7. Use a progress or status badge if a milestone is relevant

---

## Step 3: Offer Variants

After generating the document, offer:
- A **shorter TL;DR version** (email-paste format, 5 sentences)
- A **talking points version** (for a 5-minute verbal update at a lab meeting)
- An alternate document name if they didn't choose one

---

## Reference Files

- `references/template.qmd` — Quarto template to follow
- `references/design-guide.md` — Tone, style, content guidance
- `references/field-framing-examples.md` — Example field-positioning sentences