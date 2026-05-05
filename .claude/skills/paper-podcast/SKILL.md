---
name: paper-podcast
description: Converts a scientific paper into an engaging, narrated audio-script tailored to a reader with wet lab microbiology and ML backgrounds who is building expertise in cancer immune biology and spatial immunofluorescence. Trigger if the user says something like "make an audio version of this paper" or "make a podcast-style summary" or "make a fun version" — the skill produces a flowing, podcast-style narrative script calibrated to this specific reader's background and work.
---

# Paper Podcast

Converts a scientific paper into a flowing, podcast-style narrative script tailored to a specific reader profile. The final output is pure prose — TTS-ready, engaging, and calibrated to the reader's background.

## Reader Profile

**Strong background in:**
- Wet lab microbiology: tissue culture, bacterial/yeast culture, molecular techniques (PCR, cloning, etc.)
- Basic ML model training concepts and evaluation
- Spatial immunofluorescence (IF) data analysis for cancer research (non-transcriptomic)

**Building expertise in:**
- Cancer immune biology and tumor microenvironment (TME)
- Applying spatial IF data to ML models
- Bridging wet lab, clinical pathology, and computational methods
- Identifying gaps in the literature and opportunities for novel analysis

**Communication style:** Technical but not jargon-dense. Use analogies to familiar wet lab or ML concepts. Avoid over-explaining molecular biology basics. Do explain clinical pathology terminology, immune cell subtype roles, and computational architecture choices.


## Step 1: Get and read the paper

Get the paper from the user. Read the **entire** paper carefully — methods, results, discussion, limitations. The quality of the digest depends entirely on genuine comprehension first.


## Step 2: Internal analysis (do not output this — use it to inform the script)

Before writing, think through these dimensions and use them to shape the narrative. This is a scratchpad, not an output section.

**Paper identity**
- Full title, first/last authors and their institutions, journal, year of publication

**Biological framing**
- What cancer type, tissue, or biological system?
- What immune cell types or pathways are central? Do they need explanation for this reader?
- Key clinical or pathological concepts the reader needs to follow the paper's logic

**Spatial / imaging angle** (if present)
- Platform and staining panel (e.g., mIF, CODEX, Vectra, H&E)
- Spatial features or metrics extracted (cell density, proximity scores, neighborhoods, contact)
- How tissue regions or compartments were defined
- Anything novel or noteworthy in the spatial analysis

**ML / computational angle** (if present)
- Model type and what that architecture is actually good at
- Input format, prediction target, training strategy, validation approach
- Performance metrics and whether they are appropriate

**Key findings** (4-6, ranked by novelty and impact)

**Techniques and tools** worth flagging for the reader's own work

**Limitations and gaps** — what the authors flagged, what is still missing, what a follow-up could address

**Relevance** — direct connections to spatial IF + ML work, cancer immune biology gaps, novel analysis opportunities


## Step 3: Write the audio script

Write a **3,000 to 5,000 word** flowing prose narrative. Save to `/mnt/user-data/outputs/<slug>_transcript.txt` where `<slug>` is a short version of the paper title.

### Required opening

The script must open by naming the paper: its title, the key authors (first author, last/senior author), their institutions, and the year of publication. Work this in naturally as part of the hook — not as a dry citation read-aloud. For example: "A team at [institution], led by [first author] and [senior author], set out to ask..." or "Published in [year] by researchers at [institution], this paper..."

### Narrative structure (do not announce these as sections — just flow through them)

1. **Hook** — Open with the core question or a striking finding. Why should a listener care?
2. **Context** — What is the broader problem? What did we not know before?
3. **Approach** — How did the researchers tackle it? Make methods feel like plot, not procedure.
4. **Findings** — Walk through key results with enough specificity to be credible, always connecting back to what it means.
5. **Implications** — So what? What changes, what opens up?
6. **Caveats and limitations** — Be honest about what the paper does not claim.
7. **Relevance to the listener's work** — Explicitly connect to spatial IF, ML on pathology images, cancer immune biology, or gaps in the field.
8. **Takeaway** — Land on something memorable.

### Prose rules for TTS quality

- **No headers, bullet points, or markdown** — pure prose paragraphs only
- **Spell out abbreviations** on first use: "multiplex immunofluorescence, or mIF" (TTS cannot explain acronyms)
- **Spell out numbers and symbols**: "approximately 3.7 percent" not "~3.7%"; "p equals 0.03" not "p=0.03"
- **No inline citations**: say "the researchers found" not "Smith et al. (2023) demonstrated"
- **Avoid em-dashes and parentheticals** — they cause awkward TTS pauses; use commas or rewrite
- **Vary sentence length**: mix short punchy sentences with longer flowing ones to create rhythm
- **Explain immune biology terms** on first use: "CD8-positive T cells, the immune system's primary tumor-killing cells"
- **Use wet lab analogies** when helpful: "Think of spatial neighborhoods like co-culture conditions — who a cell is surrounded by shapes how it behaves"
- **Be specific**: do not say "they found a correlation"; say what correlated with what and roughly how strongly
- **Read aloud mentally as you write**: if it sounds stiff, rewrite it


## Troubleshooting

**Very long papers (>8,000 words)**: Focus on the most important contributions. Depth on key findings beats breadth across all sections.

**Review articles / meta-analyses**: Structure the narrative around the major themes synthesized rather than a single study's methods. Mention the most important primary papers by name.

**Purely computational papers with no biology**: Spend less time on biological context and more on what the computational approach enables and why that matters for the field.