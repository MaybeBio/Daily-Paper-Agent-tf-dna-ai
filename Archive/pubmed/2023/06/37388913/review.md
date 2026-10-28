## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplemental figure/table legends.
- **Assessment boundary** Scientific soundness, technical rigor, interpretation of results, and alignment with stated claims. Editorial and stylistic suggestions are limited to those affecting clarity for a broad readership.
- **Shared manuscript claim summary** The authors integrate CRISPRi, dCas9 tiling, base editing, and a fine-tuned deep learning model (Enformer) to dissect a ~170 bp regulatory interval within a ~1.5 kb enhancer upstream of CD69. They identify a single C-to-T base edit (C-948) that disrupts a GATA3 binding site, displaces a GATA3-TAL1 activating complex, increases BHLHE40 repressor association, and suppresses CD69 induction. They further propose a general role for GATA3-BHLHE40 interplay in rapid T cell transcriptional responses.
- **Visible evidence base** Main text figures (Figures 1–4), supplemental figures (S1–S5), methods section, and data availability statements. No raw data files or processed data tables were provided for independent verification.
- **Missing materials affecting confidence** Raw sequencing data, processed count matrices, and peak calls are not included in the provided material. The manuscript references GEO accession GSE206377, but the data were not accessible for review. Additionally, the fine-tuned Enformer model weights and training scripts are referenced via a repository, but the code was not provided for inspection.

## Reviewer
- **Overall assessment** This manuscript presents a well-executed, multi-pronged approach to dissect a functional regulatory element at base resolution. The integration of orthogonal methods (epigenetic perturbation, base editing, deep learning) is a strength, and the convergence on a single critical nucleotide is compelling. However, several technical concerns, particularly regarding the specificity of the base editing effects, the interpretation of the BHLHE40 ChIP data, and the generalizability of the proposed GATA3-BHLHE40 interplay, require clarification or additional analysis before the conclusions are fully supported.
- **Who would be interested in the results, and why** Researchers in gene regulation, chromatin biology, immunology (particularly T cell biology), and computational genomics. The work demonstrates a practical framework for functional dissection of noncoding elements, which is of broad interest given the vast number of uncharacterized regulatory regions. The specific findings on GATA3-BHLHE40 antagonism in T cell activation will interest immunologists.
- **Major strengths**
    1.  The study design is logical and integrates complementary techniques to move from a broad regulatory region to a single functional base.
    2.  The convergence of deep learning predictions and experimental base editing screens on the same interval and nucleotide is a powerful validation of the approach.
    3.  The mechanistic dissection using ChIP-seq to show loss of activator binding and gain of repressor binding provides a plausible molecular explanation for the observed phenotypic effect.
    4.  The manuscript is generally clearly written and the figures are informative.
- **Major Concerns**
    - **R1-M1** (Blocking: Yes)
    - **R1-M2** (Blocking: Yes)
    - **R1-M3** (Blocking: No)
    - **R1-M4** (Blocking: No)
- **Minor Comments**
    - **R1-m1**
    - **R1-m2**
    - **R1-m3**
    - **R1-m4**
- **Technical failings that need to be addressed before the case is established** The specificity of the base editing phenotype (R1-M1) and the interpretation of BHLHE40 redistribution (R1-M2) are the primary technical issues. The lack of a genome-wide assessment for off-target effects of the top guide and the absence of a clear mechanistic link for the diffuse BHLHE40 binding pattern are the main weaknesses.
- **Assessment against Nature-style criteria**
    - **Originality:** High. The combination of base editing screens with fine-tuned deep learning models to dissect a native regulatory element is a novel and valuable contribution.
    - **Scientific importance:** High. The work provides a blueprint for moving from GWAS/ATAC-seq peaks to functional bases and transcription factor interactions, a major goal in the field. The specific finding of GATA3-BHLHE40 antagonism is important for understanding T cell biology.
    - **Interdisciplinary readership:** Moderate to high. The methods and findings will appeal to genomicists, computational biologists, and immunologists. The conceptual framework is accessible, though some technical details may be dense for a general biology audience.
    - **Technical soundness:** Generally sound, but with significant caveats. The core experiments are well-controlled, but the specificity of the base editing effect and the interpretation of the BHLHE40 ChIP data require further validation. The deep learning component is used appropriately but is not the primary source of biological discovery.
    - **Readability for nonspecialists:** Good. The abstract and introduction are clear. The results are presented logically, and the figures help guide the reader. Some methods details are complex but are appropriately relegated to the methods section.
- **Recommendation posture** Supportive if the technical concerns regarding base editing specificity and BHLHE40 interpretation are adequately addressed with additional experiments or analyses. The core finding of a single base controlling an enhancer's function is potentially significant, but the current evidence does not fully exclude alternative explanations.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Experimental design
- **Claim pointer** The manuscript claims that "the single C-948-to-T edit strongly impacts transcriptional induction of CD69 in response to stimulation" and that this edit is responsible for the observed reduction in enhancer activity.
- **Evidence pointer** Figure 3A–C, Figure S3A–F, and related text.
- **Concern** The primary evidence linking the C-948 edit to the phenotype relies on a single guide RNA (sg#70) in the base editing screen. The manuscript does not demonstrate that the observed phenotypic effect is specifically due to the C-948 edit and not due to off-target editing events or other effects of the base editor. The authors report editing frequencies at the target locus but do not provide a genome-wide assessment of off-target edits for this guide. Furthermore, the manuscript does not show a clear correlation between the allelic frequency of the C-948 edit and the degree of CD69 suppression at the single-cell or population level. The lack of a rescue experiment (e.g., introducing the same C-to-T mutation in a cell line with a different genetic background or using a different base editor with a different guide targeting the same base) weakens the causal claim.
- **Why it matters** The central conclusion of the paper is that a single base pair is critical for enhancer function. If the phenotype is due to off-target effects or a bystander edit, the conclusion is invalid. The authors need to rigorously exclude off-target effects to support their claim.
- **Resolution test** Provide genome-wide off-target analysis (e.g., GUIDE-seq or CAST-seq) for sg#70. Alternatively, demonstrate that a second, independent guide RNA targeting the same C-948 base produces a similar phenotype. A more definitive test would be to introduce the C-948T mutation in isolation (e.g., using prime editing) and show that it recapitulates the enhancer loss-of-function phenotype.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of results / Data analysis
- **Claim pointer** The manuscript claims that the C-948 edit "promotes the association of a key T cell repressor across the locus" and that BHLHE40 binding becomes "diffuse" across an ~8 kb region in edited cells.
- **Evidence pointer** Figure 3F, Figure 4C–D, and related text.
- **Concern** The ChIP-seq data for BHLHE40 in the edited cells show a diffuse signal across a broad region, which is interpreted as increased repressor association. However, this pattern could also be explained by technical artifacts, such as changes in chromatin solubility or non-specific antibody binding due to the altered chromatin state. The manuscript does not provide a quantitative comparison of BHLHE40 binding between control and edited cells at specific loci, nor does it show that the diffuse signal is enriched for BHLHE40 motifs. The claim that BHLHE40 is "recruited" to the locus is not directly supported by the data, as the ChIP signal could reflect a redistribution of existing BHLHE40 rather than new recruitment. The functional relevance of this diffuse binding is also unclear, as the manuscript does not demonstrate that BHLHE40 binding is required for the observed repression.
- **Why it matters** The proposed mechanism relies on a switch from activator (GATA3-TAL1) to repressor (BHLHE40) binding. If the BHLHE40 ChIP data are not robust, the mechanistic model is weakened. The authors need to provide stronger evidence that BHLHE40 is functionally involved in the repression.
- **Resolution test** Perform a quantitative ChIP-seq analysis (e.g., using spike-in normalization) to compare BHLHE40 occupancy between control and edited cells. Show that the diffuse BHLHE40 signal is specifically enriched at the CD69 locus and not a global artifact. Perform BHLHE40 knockdown in the edited cells and show that this partially rescues CD69 expression. Additionally, demonstrate that the BHLHE40 binding sites within the diffuse region contain functional BHLHE40 motifs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability / Scope of claims
- **Claim pointer** The manuscript claims that "the interplay between GATA3 and BHLHE40 plays a general role in rapid T cell transcriptional responses."
- **Evidence pointer** Figure 4E–F, Figure S5, and related text.
- **Concern** The genome-wide analysis shows a significant overlap between GATA3 and BHLHE40 binding sites and co-regulated genes. However, the analysis is largely correlative. The manuscript does not demonstrate that the antagonistic relationship observed at the CD69 locus is a general phenomenon. For example, it is not shown that BHLHE40 binding at co-bound sites is associated with repression of nearby genes, nor that GATA3 binding is associated with activation. The direction of the effect (activation vs. repression) at co-bound sites is not systematically analyzed. The claim of a "general role" is therefore an extrapolation from a single detailed example.
- **Why it matters** The broader significance of the work depends on the generality of the proposed mechanism. If the GATA3-BHLHE40 antagonism is specific to CD69, the impact of the study is reduced.
- **Resolution test** Perform a more detailed analysis of the co-bound sites. Classify genes based on the relative binding strength of GATA3 and BHLHE40 and show that the ratio of GATA3 to BHLHE40 binding correlates with the direction and magnitude of transcriptional response. Use perturbation experiments (e.g., knockdown of each factor) at a subset of co-bound loci to demonstrate a general antagonistic relationship.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Data analysis
- **Claim pointer** The manuscript uses a fine-tuned Enformer model to predict functional bases and states that "the individual bases nominated by Enformer frequently coincided with sgRNAs that scored in the CBE screen."
- **Evidence pointer** Figure S2H–I, Methods section "Enformer predictions and fine-tuning".
- **Concern** The fine-tuning of the Enformer model is a key component of the analysis, but the details of the fine-tuning procedure are not fully described. Specifically, the manuscript does not state how the model was trained to predict differential accessibility, what the training and validation sets were, or how overfitting was avoided. The correlation between model predictions and experimental results is presented, but the statistical significance of this overlap is not rigorously assessed. The model's performance is compared to the experimental screen, but it is unclear if the model provides added value beyond simpler sequence-based methods (e.g., motif scanning).
- **Why it matters** The deep learning component is presented as a key innovation. If the model's predictions are not robust or are not significantly better than simpler methods, the contribution of this aspect is diminished.
- **Resolution test** Provide a more detailed description of the fine-tuning procedure, including hyperparameters, training/validation splits, and a baseline comparison (e.g., a motif-based predictor). Perform a permutation test to assess the statistical significance of the overlap between model predictions and experimental hits.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Methods, "Guide library design and cloning"
- **Evidence pointer** Methods section, "Guide library design and cloning".
- **Issue** The description of the guide RNA library design is brief. The criteria for guide selection (e.g., on-target score thresholds, off-target filtering) are not fully specified.
- **Required correction** Provide a more detailed description of the guide design algorithm, including the specific scoring metrics used and the thresholds applied.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2C
- **Evidence pointer** Figure 2C and related text.
- **Issue** The figure shows common SNPs, eQTLs, and conservation scores, but the y-axis scale for the conservation score is not clearly labeled. The density of eQTLs and SNPs is also difficult to discern at the shown resolution.
- **Required correction** Add clear axis labels and consider using a separate panel or an inset to show the conservation and variation data at a higher resolution.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section.
- **Issue** The discussion speculates on the role of GATA3-BHLHE40 interplay in T cell polarization but does not fully contextualize this with existing literature on Th1/Th2 differentiation.
- **Required correction** Add a brief discussion of how the proposed model fits with or challenges existing models of Th1/Th2 polarization.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data and code availability
- **Evidence pointer** Data and code availability section.
- **Issue** The code repository is referenced, but the specific version or commit is not provided. The GEO accession is listed, but the reviewer could not access the data.
- **Required correction** Provide a specific version or DOI for the code repository and ensure the GEO data are publicly available and properly formatted.

## Risk / unsupported claims
- The claim that the C-948 edit is the sole cause of the observed phenotype is not fully supported without off-target analysis or an independent validation.
- The claim that BHLHE40 is "recruited" to the locus is not directly supported by the ChIP-seq data, which show a diffuse signal that could be due to technical artifacts.
- The claim of a "general role" for GATA3-BHLHE40 interplay in T cell responses is an extrapolation from a single detailed example and is not fully supported by the genome-wide correlative analysis.
- The predictive power of the fine-tuned Enformer model is not rigorously benchmarked against simpler methods, making its specific contribution unclear.