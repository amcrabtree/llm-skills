# mIF Standards Reference

Load this file when: the manuscript is a methods/computational paper, when the user asks for platform-specific guidance, or when deep technical critique of the image analysis pipeline is needed.

---

## Table of Contents
1. Platform-Specific Reporting Standards
2. Cell Segmentation — Methods and Pitfalls
3. Phenotyping and Gating Strategies
4. Spatial Analysis Methods Glossary
5. Statistical Standards for mIF Data
6. Public Datasets for Validation
7. Key Journals and Their Expectations

---

## 1. Platform-Specific Reporting Standards

### Akoya CODEX / PhenoCycler-Fusion
- Report: number of cycles, stripping efficiency controls, cycle-to-cycle registration accuracy
- Key pitfall: antibody stripping incomplete → bleed-through into subsequent cycles; should be verified with single-stain controls each cycle
- Resolution: typically 0.5 µm/pixel at 20x; report pixel size
- Panel size: up to 40+ markers; justify marker selection and order (early cycles: high-abundance markers for registration)

### Akoya Vectra Polaris / Opal
- Report: Opal dye assignments, spectral library construction, unmixing algorithm used
- Key pitfall: spectral overlap between Opal 520/570/620 if not properly unmixed; autofluorescence (AF) channel inclusion is critical for FFPE
- Inform whether inForm, HALO, or QuPath was used for unmixing and phenotyping
- Maximum practical simultaneous markers: ~7–8 (plus DAPI); larger panels require sequential staining with re-staining validation

### MIBI-TOF (IONpath)
- Report: metal isotope assignments, acquisition time per FOV, ion dose
- Key pitfall: mass spillover between adjacent isotopes; compensation matrix should be reported
- Spatial resolution: ~500 nm; single-cell sensitivity varies by marker abundance

### MACSima
- Report: number of imaging cycles, antibody elution validation
- Key advantage: no spectral unmixing required (single-color per cycle)

---

## 2. Cell Segmentation — Methods and Pitfalls

### Nuclear Segmentation (DAPI-based)
- Tools: CellProfiler, ImageJ/FIJI, StarDist, Cellpose (nucleus model)
- Pitfall: touching nuclei in dense regions cause under-segmentation; watershed parameters must be tuned
- Mitigation: report minimum/maximum nuclear diameter thresholds used

### Whole-Cell Segmentation
- Tools: Cellpose (cyto2/3 model), DeepCell/Mesmer, HALO's AI segmentation
- Mesmer (DeepCell): requires nuclear + membrane channel input; well-validated on CODEX/mIF data
- Pitfall: membrane marker choice critically affects accuracy — pan-cytokeratin for epithelial, CD45 for immune; cells with weak membrane marker expression may be missed
- Report: which membrane marker(s) were used as segmentation input

### Validation of Segmentation
- Gold standard: manual annotation of a held-out FOV subset; report F1, precision, recall vs. manual
- Minimum: visual inspection with overlaid masks shown in supplemental figures
- Cell count QC: report mean ± SD cells per FOV; flag FOVs with extreme outliers

---

## 3. Phenotyping and Gating Strategies

### Manual Gating / Thresholding
- Report: who set thresholds, whether done blinded to outcome, reproducibility (inter-rater agreement if multiple annotators)
- Pitfall: threshold drift across batches; should be set on training data and locked before applying to test data

### Clustering-Based Phenotyping
- Tools: PhenoGraph, FlowSOM, Leiden (via scanpy/squidpy), UMAP for visualization
- Report: which features were used for clustering (mean marker intensity? binary positivity?), number of clusters, resolution parameter
- Pitfall: batch effects dominate clustering if not corrected; consider Harmony, ComBat, or sample-level normalization
- Cluster annotation: should be done by domain expert; report marker expression heatmap used for annotation

### ML Classifier-Based Phenotyping
- Tools: inForm random forest, HALO AI, custom CNNs
- Report: training set size and composition, cross-validation strategy, performance metrics on held-out data
- Pitfall: classifiers trained on one tissue type or staining batch may not generalize

### Phenotype Validation Approaches
- Orthogonal IHC: re-stain serial sections with single markers; compare density
- Flow cytometry correlation: if matched fresh tissue available
- scRNA-seq deconvolution: use CIBERSORTx, RCTD, or cell2location with matched or published reference
- Published signature comparison: compare identified phenotype marker combinations to canonical definitions in literature

---

## 4. Spatial Analysis Methods Glossary

### Cell Density and Infiltration
- **Cells/mm²**: standard unit; report per tissue compartment (tumor, stroma, TLS, invasive margin)
- **Excluded vs. infiltrating pattern**: distance from tumor-stroma interface; e.g., CD8+ T cells >30µm from tumor nests = excluded phenotype
- Tools: HALO spatial analysis, QuPath measurements, custom Python/R

### Nearest Neighbor and Proximity
- **G-function**: distribution of nearest-neighbor distances; tests for clustering vs. random
- **K/L-function (Ripley's K)**: degree of spatial clustering at multiple radii
- **Cross-K function**: spatial association between two cell types
- Tools: spatstat (R), Squidpy, SPIAT

### Cellular Neighborhoods
- **Cellular neighborhood (CN) analysis**: K-nearest-neighbor graph → clustering of local composition → discrete TME states
- Reference: Schürch et al. Cell 2020 (CN analysis in CRC); Moldoveanu et al. — key mIF papers
- Tools: HistoCAT (MATLAB), Squidpy (Python), neighborhood analysis in SPIAT

### Spatial Statistics Pitfalls
- Do not report proximity without testing against spatial null model (CSR — complete spatial randomness)
- Account for tissue area when comparing across samples (normalize by tissue area, not raw counts)
- Avoid reporting correlation between two cell types derived from the same sample set without correcting for sample-level confounding

### Tumor-Infiltrating Lymphocyte (TIL) Scoring
- Report whether TIL scoring follows international TIL Working Group guidelines (Salgado et al., Ann Oncol 2015)
- Automated TIL scores should be compared to manual pathologist scores

---

## 5. Statistical Standards for mIF Data

### Unit of Analysis
- **Cell level**: valid for intra-sample analyses; pseudoreplication if treating cells as independent across patients
- **FOV/core level**: appropriate intermediate; account for within-patient correlation if multiple FOVs per patient
- **Patient level**: gold standard for clinical associations; requires summarizing cell-level data (mean, median, % positive) per patient

### Recommended Tests
- Comparing two groups (patient-level continuous variable): Mann-Whitney U (non-normal distributions common in mIF)
- Multiple groups: Kruskal-Wallis + Dunn's post-hoc with Bonferroni or BH correction
- Correlation: Spearman (rank-based, robust to outliers)
- Survival: Cox proportional hazards; verify PH assumption; Kaplan-Meier for visualization only
- High-dimensional: report dimensionality reduction method (UMAP/PCA) parameters; clustering resolution

### Multiple Testing
- Any analysis involving >1 marker or >1 spatial metric requires correction
- Report which correction method was used (Bonferroni, BH/FDR)
- Distinguish discovery (exploratory) from confirmatory analyses; be explicit about which is which

### Sample Size and Power
- mIF studies are frequently underpowered; if n < 30 per group, this should be flagged
- If no power calculation was performed, note this as a limitation

---

## 6. Public Datasets for External Validation

| Dataset | Platform | Cancer Type | Access |
|---------|----------|-------------|--------|
| Keren et al. 2018 (MIBI) | MIBI-TOF | TNBC | Published data tables |
| Schürch et al. 2020 | CODEX | CRC | Mendeley/GEO |
| Moldoveanu et al. | Vectra | HGSOC | GEO |
| HTAN (Human Tumor Atlas Network) | Multi-platform | Pan-cancer | htan.cancer.gov |
| IMAXT (Cancer Research UK) | Various | Breast | CRUK portal |
| caMicroscope / TCIA | Various | Pan-cancer | cancerimagingarchive.net |
| Jackson et al. 2020 (IMC) | IMC | Breast | Zenodo |

Suggest relevant datasets based on tumor type and question in the manuscript under review.

---

## 7. Key Journals and Their Expectations

### High-Impact (require strong novelty + clinical validation)
- **Nature Cancer**, **Cancer Cell**, **Cell**: expect orthogonal validation, large cohorts (n > 100), mechanistic insights, external dataset validation
- **JCI**, **Science Translational Medicine**: translational framing critical; clinical relevance must be explicit

### Mid-Tier (strong methods + solid biology)
- **Cancer Research**, **Clinical Cancer Research**: large patient cohorts, clinical outcomes
- **Journal of Pathology**, **Modern Pathology**: histopathology framing, TMA-friendly
- **npj Precision Oncology**: translational, biomarker focus

### Methods Journals
- **Nature Methods**, **Nature Protocols**: reproducibility paramount; must share code and data; MIAME/MIQE-equivalent checklists expected
- **Bioinformatics**, **PLOS Computational Biology**: code availability required; benchmark against existing tools

### Spatial Biology-Specific
- **Cell Systems**: systems-level spatial analysis
- **Genome Biology**: computational methods with biological insight