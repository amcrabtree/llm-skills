# Field Framing Examples

Reference sentences and patterns for the "Field Position" section.
Adapt these to the user's specific subfield and results.

---

## Positioning Patterns

### "Ahead of the field"
> "While most published approaches still rely on single-marker IHC, our pipeline operates across 7-plex panels — a level of multiplexing only beginning to appear in preprints from the top computational pathology groups."

> "Chen et al. (2024, *Nature Cancer*) recently demonstrated cell-type co-localization as a survival predictor in NSCLC; our model extends this to spatial interaction graphs, which they called a 'critical next step' in their discussion."

### "In line with / validating"
> "Our findings converge with Schürch et al.'s CODEX work in colorectal cancer — the tumor-immune interface features we're extracting map closely to their 'community' architecture, which strengthens the biological plausibility of our approach."

> "The field has been moving toward foundation models for pathology (e.g., UNI, CONCH, Prov-GigaPath); our work sits squarely in this direction, adapting these backbones specifically for mIF spatial context."

### "First in our indication / dataset type"
> "To our knowledge, this is the first application of graph neural networks to spatial mIF in [cancer type] — the closest published work is in H&E-based graphs (Chen et al., 2021, *Cell Systems*), which lacks the immune phenotyping resolution we have."

> "Published benchmarks for cell segmentation in dense tumor microenvironments don't yet account for multiplex channel bleedthrough correction — our validation dataset is one of the first to do so."

### "Responding to a known gap"
> "A recent review (Bressan et al., 2023, *Science*) identified 'robust spatial neighborhood quantification' as the largest unresolved bottleneck in translational spatial biology — that's precisely what this pipeline addresses."

---

## Subfield-Specific Reference Hooks

### Spatial mIF / MIBI / CODEX
- Schürch et al. 2020 (*Cell*) — CODEX CRC communities
- Keren et al. 2018 (*Cell*) — MIBI-TOF breast cancer TME
- Hickey et al. 2023 (*Nature Methods*) — spatial omics benchmarking

### Computational Pathology / CV on H&E
- Chen et al. 2022 (*Nature Biomedical Engineering*) — HIPT hierarchical ViT
- Campanella et al. 2019 (*Nature Medicine*) — weakly supervised WSI classification
- UNI (Chen et al. 2024, *Nature Medicine*) — foundation model for pathology

### Spatial Transcriptomics (if relevant)
- Rodriques et al. 2019 (*Science*) — Slide-seq
- Moses & Pachter 2022 (*Nature Methods*) — Museum of Spatial Transcriptomics review

### Tumor Microenvironment / Immuno-oncology
- Tumeh et al. 2014 (*Nature*) — PD-1 blockade and CD8 proximity
- Galon & Bruni 2019 (*Nature Reviews Cancer*) — Immunoscore framework

---

## Framing Sentence Templates

Fill in brackets:

- "Our work [extends / validates / challenges / is the first to apply] [method/finding] from [Author et al., Year] to [your context]."
- "While [Author et al.] demonstrated [X] in [indication], we show [Y] — a [more clinically relevant / higher resolution / scalable] approach."
- "The [grant aim / clinical question] we're addressing maps directly to what [Author et al.] identified as the key open problem in [subfield]."
- "[Top venue paper] recently established [X] as a benchmark; our preliminary results [meet / exceed / reframe] that benchmark in [your dataset]."