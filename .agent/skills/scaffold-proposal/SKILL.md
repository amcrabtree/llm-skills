---
name: scaffold-proposal
description: >
  Creates a structured scaffold (template with guidance) for a grant proposal. Use this skill
  whenever the user mentions grant writing, grant proposals, grant applications, funding proposals,
  or asks for help applying for a grant — even if they only say "I need to write a grant" or
  "help me apply for funding." The skill walks the user through describing their grant, optionally
  analyzing example successful grants, and then produces a clear, well-organized scaffold saved
  to grant_proposal_scaffold.md that a first-time grant writer can follow.
---

# Grant Proposal Scaffold Skill

Help users create a well-structured grant proposal scaffold by learning about their grant, optionally studying examples of successful grants, and producing a clear, annotated template they can fill in.

---

## Step 1: Understand the Grant

Ask the user to describe their grant. Prompt with these questions (ask them together in one message, not one by one):

- What organization or program are you applying to? (e.g., NIH, a local community foundation, a corporate grant)
- What is your project about — what problem does it solve, and for whom?
- Roughly how much funding are you requesting, and over what time period?
- Do you have any page limits, word limits, or required sections specified by the funder?
- Is this your first time writing a grant, or have you done this before?

Wait for the user's answers before proceeding.

---

## Step 2: Gather Examples (Optional but Recommended)

After learning about the grant, ask the user:

> "Do you have any examples of successful grants to analyze? You can upload files (PDF, Word, or text) or paste text directly. If you don't have examples, I can search the web for publicly available successful grants in your area."

**If the user uploads or pastes examples:**
- Read each example carefully.
- Note the structure, section order, length of each section, and tone.
- Look for patterns: what elements appear in all or most examples?
- Note any language that seems particularly compelling (mission clarity, quantified impact, etc.).

**If the user has no examples:**
- Use web search to find 2–3 publicly available successful grant proposals relevant to their funder or topic area.
- Search query examples: `"successful grant proposal" [funder name] example`, `"NIH funded grant" sample`, `"community foundation grant" example PDF`.
- Read and analyze whatever you find.

**If the user declines both:**
- Proceed using general grant-writing best practices (see Step 3).

---

## Step 3: Build the Scaffold

Based on what you've learned about the grant and any examples, create a scaffold: a template with clearly labeled sections and detailed guidance notes for each section.

### Core Sections to Include

Every grant scaffold should include the following sections (adjust based on funder requirements):

1. **Cover Page / Title**
2. **Executive Summary / Abstract**
3. **Statement of Need / Problem Statement**
4. **Project Description / Narrative**
   - Goals and Objectives
   - Methods / Approach
   - Timeline
5. **Evaluation Plan**
6. **Organizational Capacity**
7. **Budget Summary**
8. **Budget Justification**
9. **Conclusion**
10. **Appendices** (if allowed)

Add, remove, or rename sections based on the funder's stated requirements or patterns observed in examples.

### Scaffold Format

For each section, include:

```
## [Section Name]

**What this section is for:**
[Plain-language explanation of the purpose of this section — 1–3 sentences. Assume the reader has never written a grant before.]

**What to include:**
- [Bullet list of content that belongs here]

**Tips for this section:**
[2–3 practical tips based on what makes this section strong. Reference patterns from examples if available.]

**Length guidance:** [e.g., "Typically 1–2 paragraphs" or "Usually 200–400 words"]

---
[PLACEHOLDER TEXT IN BRACKETS — e.g., [Describe the problem your project addresses and who is affected by it.]]
```

### Elements to Emphasize

Regardless of the grant type, make sure to highlight the following as strengths throughout the scaffold:

- **Clearly defined objectives**: Each goal should be specific and measurable. Prompt the user to use SMART criteria (Specific, Measurable, Achievable, Relevant, Time-bound).
- **Impact statements**: Prompt the user to quantify expected outcomes wherever possible (e.g., "We expect to serve X people over Y months").
- **Evaluation methods**: Explain why funders care about this — they want to know their money is well spent and that progress can be tracked.
- **Clarity for non-experts**: Remind the user that reviewers may not be specialists in their field. Encourage plain language.

---

## Step 4: Save the Scaffold

Save the completed scaffold to a file named `grant_proposal_scaffold.md` in the current working directory using the bash tool or file creation tool.

Then present the file to the user and offer to:
- Adjust any sections based on their funder's specific requirements
- Expand the guidance notes in any section
- Help them start filling in any section

---

## Tips for Adapting the Scaffold

- **Government grants** (NIH, NSF, NEA, etc.) often have very strict formatting requirements. Always check the funder's published guidelines and add a note at the top of the scaffold reminding the user to verify requirements.
- **Foundation grants** tend to be shorter and more narrative-driven. Emphasize storytelling and mission alignment.
- **Corporate grants** may prioritize ROI and community visibility. Adjust the impact framing accordingly.
- **First-time writers**: Add extra encouragement and plain-language explanations. Avoid jargon.

---

## Tone and Communication

- Use plain, encouraging language throughout the scaffold — grant writing can feel intimidating.
- Label every placeholder clearly with [BRACKETS] so the user knows exactly where to write.
- Be explicit about *why* each section matters — this helps writers prioritize their effort.
- If the user seems unfamiliar with grant writing, briefly explain any terms you use (e.g., "evaluation plan," "budget justification").