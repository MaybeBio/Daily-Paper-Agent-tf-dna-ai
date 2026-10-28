## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, limitations, conclusion, methods, and supplementary figure/table references.
- **Assessment boundary** Scientific validity, methodological rigor, logical coherence, and support of claims by presented evidence. Editorial or stylistic issues are noted only where they affect comprehension or reproducibility.
- **Shared manuscript claim summary** The authors map G-quadruplex (G4) structures in the prostate cancer cell line C4-2 via BG4 ChIP-seq, identify 1,289 prostate cancer-specific G4-associated genes, integrate immune pathway enrichment with five machine learning algorithms to nominate IKBKB as a key hub gene, and propose that a promoter G4 in IKBKB enhances transcription via AR/ERG recruitment, driving NF-κB activation and malignant phenotypes. They further propose CRISPR-dCas9-mediated G4 disruption and AI-designed peptide inhibitors as therapeutic strategies.
- **Visible evidence base** Results sections with figures referenced (Figures 1-10), supplementary tables and figures, methods descriptions, and data availability statement (GEO accession GSE334282).
- **Missing materials affecting confidence** Raw sequencing data, peak calling statistics, machine learning feature selection details, single-cell RNA-seq analysis parameters, docking scores, peptide design validation metrics, and experimental replicates for functional assays are not fully described. No in-house validation beyond C4-2 cell line is presented.

## Reviewer

- **Overall assessment** The manuscript addresses an important and timely question: the role of G4 structures in prostate cancer immune regulation and their potential as therapeutic targets. The integration of G4 ChIP-seq with machine learning is conceptually appealing and the identification of IKBKB as a hub gene is plausible. However, the evidence supporting the central mechanistic claim (G4-mediated regulation of IKBKB via AR/ERG) is largely correlative and pharmacological, and the authors themselves acknowledge the absence of G4-mutant reporter assays. The therapeutic proposals, while innovative, are purely computational and lack experimental validation. The manuscript would benefit from substantial additional evidence to establish causality and translational relevance.
- **Who would be interested in the results, and why** Researchers in cancer epigenetics, particularly those studying G4 biology and its intersection with tumor immunology. Clinicians and translational scientists interested in prostate cancer biomarkers and drug repurposing may also find the druggability and drug screening components relevant. The AI-based peptide design section may appeal to computational biologists working on protein design.
- **Major strengths**
  1. Novel integration of G4 ChIP-seq with machine learning for target discovery in prostate cancer.
  2. Comprehensive pathway enrichment analysis across multiple databases, reducing bias.
  3. Multi-faceted characterization of IKBKB, including expression, survival, immune correlation, and functional assays.
  4. Translational focus with druggability assessment and proposal of two distinct therapeutic strategies.
  5. Transparent acknowledgment of limitations, particularly regarding the lack of G4-mutant assays.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal mechanism
- **Claim pointer** "The IKBKB promoter harbors a clear G4 peak in C4-2 cells... G4 stabilization increased IKBKB expression and activated the NF-κB pathway, enhancing cancer cell viability, proliferation, and migration."
- **Evidence pointer** Results section "G4-mediated IKBKB upregulation activates NF-κB signaling and promotes malignant phenotypes", Figures 8A-E, Supplementary Figure 7
- **Concern** The causal relationship between G4 structure and IKBKB expression is not directly established. The evidence relies on (a) correlative comparison between C4-2 (G4-positive) and HepG2 (G4-negative) cells, and (b) pharmacological stabilization with TMPY4 and PYRIDOSTATIN. However, G4 ligands are known to have off-target effects, and the authors do not demonstrate that the observed effects are specifically due to G4 stabilization at the IKBKB promoter. The absence of G4-disrupting mutations in the promoter, or CRISPR-based G4 disruption experiments, leaves the central mechanism unproven.
- **Why it matters** The entire premise of the proposed therapeutic strategy (CRISPR-dCas9-mediated G4 disruption) depends on the causal role of the promoter G4 in driving IKBKB overexpression. Without direct evidence, the translational relevance is speculative.
- **Resolution test** Provide G4-disrupting mutations in the IKBKB promoter and show loss of IKBKB upregulation. Alternatively, use CRISPR-dCas9 with G4-binding effectors to disrupt the G4 and demonstrate reduced IKBKB expression and downstream phenotypes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Machine learning methodology
- **Claim pointer** "The intersection of these methods identified 26 hub genes... All five machine learning methods achieved accuracy values above 0.93."
- **Evidence pointer** Results section "Unbiased pathway enrichment and identification of immune-related hub genes using machine learning", Figures 2D-F
- **Concern** The machine learning pipeline is insufficiently described. Key details are missing: (1) the training and test datasets used for each algorithm, (2) the feature selection criteria, (3) the cross-validation scheme, (4) the definition of "accuracy" and how it was computed, and (5) how the intersection of 26 genes was derived from the outputs of five different algorithms. Without these details, the robustness and reproducibility of the hub gene identification cannot be assessed.
- **Why it matters** The identification of IKBKB as the sole prognostic hub gene is a central finding. If the machine learning methodology is flawed or not reproducible, the entire target discovery pipeline is compromised.
- **Resolution test** Provide a detailed description of the machine learning pipeline, including dataset splits, hyperparameters, and feature selection. Include performance metrics (e.g., AUC, sensitivity, specificity) and a clear explanation of how the 26-gene intersection was obtained.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional validation
- **Claim pointer** "IKBKB promoted genome instability, tumor stemness, and immune microenvironment remodeling."
- **Evidence pointer** Results section "IKBKB is associated with core cancer hallmarks in prostate cancer", Figures 5-6
- **Concern** The functional claims are based primarily on correlation analyses with gene expression data and computational inference. The only direct functional experiments are the G4 stabilization assays in C4-2 cells (Figure 8). There are no experiments directly manipulating IKBKB expression (e.g., knockdown or overexpression) to demonstrate its role in genome instability, stemness, or immune modulation. The knockdown experiments referenced in Supplementary Figure 8 are not described in sufficient detail.
- **Why it matters** The manuscript claims IKBKB is a "driver" of prostate cancer progression, but the evidence is largely associative. Direct loss-of-function and gain-of-function experiments are needed to establish causality.
- **Resolution test** Perform IKBKB knockdown and overexpression experiments in prostate cancer cell lines, assessing effects on proliferation, migration, genome instability markers, and immune-related gene expression.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Therapeutic strategy validation
- **Claim pointer** "We propose two novel therapeutic strategies: G4 disruption at the IKBKB promoter and AI-designed peptide inhibitors."
- **Evidence pointer** Results section "AI-assisted design of G4 disruptors and peptide inhibitors targeting IKBKB", Figures 9-10
- **Concern** Both therapeutic strategies are purely computational. The CRISPR-dCas9 approach is described conceptually but not experimentally tested. The AI-designed peptides are generated in silico but not synthesized or tested for binding affinity, specificity, or biological activity. The docking scores and binding energies are not reported.
- **Why it matters** The translational value of the manuscript depends on the feasibility of these therapeutic strategies. Without experimental validation, they remain speculative.
- **Resolution test** Synthesize the designed peptides and test their binding to IKBKB in vitro, and assess their effects on IKBKB activity in cell-based assays. For the CRISPR-dCas9 approach, provide proof-of-concept data in cell lines.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data availability and reproducibility
- **Claim pointer** "The original contributions presented in the study are publicly available. This data can be found here: GEO database, and the corresponding GEO accession number is GSE334282."
- **Evidence pointer** Data availability statement
- **Concern** The GEO accession number is provided, but the manuscript does not describe the processing pipeline for the BG4 ChIP-seq data in sufficient detail. Key parameters such as peak calling thresholds, input normalization, and quality control metrics are not reported. Additionally, the single-cell RNA-seq analysis (EGAS00001005787) is mentioned but not described in the methods.
- **Why it matters** Reproducibility is a core requirement for scientific manuscripts. Without detailed methods, other researchers cannot replicate the analysis or verify the findings.
- **Resolution test** Provide a detailed bioinformatics pipeline in the methods, including software versions, parameters, and quality control steps. Describe the single-cell RNA-seq analysis in full.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Correlation analyses
- **Evidence pointer** Results section "IKBKB is associated with core cancer hallmarks", Figure 5A
- **Issue** The correlation coefficients and p-values are reported for IKBKB with immune function and genome instability, but the statistical methods used (e.g., Spearman vs. Pearson) are not consistently stated. The methods section mentions Spearman's rho, but Figure 5A appears to use Pearson correlation coefficients.
- **Required correction** Clarify which correlation method was used for each analysis and ensure consistency between the methods and figure legends.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1
- **Evidence pointer** Results section "Identification of prostate cancer-specific G4 structure-associated genes", Figure 1
- **Issue** The schematic in Figure 1A is not described in the text. The correlation values in Figure 1C are reported as a range (0.5-0.9), but individual replicate correlations are not shown.
- **Required correction** Add a description of Figure 1A in the text and provide individual replicate correlation values or a heatmap of pairwise correlations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "G4 screen"
- **Evidence pointer** Title and methods
- **Issue** The term "G4 screen" is used in the title but is not defined in the methods. It is unclear whether this refers to the BG4 ChIP-seq experiment or a separate screening approach.
- **Required correction** Define "G4 screen" in the methods and clarify its relationship to the BG4 ChIP-seq data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Introduction and discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** Several statements in the introduction and discussion lack specific citations. For example, the claim that "G4s are frequently associated with the promoters of oncogenes" is not directly cited, and the discussion of G4 ligands' off-target effects is not referenced.
- **Required correction** Add appropriate citations for all factual claims and ensure that references are accurately cited.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and clarity
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** Some sentences in the discussion are overly long and convoluted, making it difficult to follow the logical flow. For example, the paragraph describing the dual role of IKBKB could be simplified.
- **Required correction** Revise the discussion for clarity and conciseness, breaking up long sentences and improving paragraph structure.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Supplementary material
- **Affected element** Supplementary Tables and Figures
- **Evidence pointer** Results sections referencing Supplementary Tables 1-4 and Supplementary Figures 1-8
- **Issue** The supplementary material is referenced but not provided in the manuscript. It is unclear whether the supplementary files are accessible or complete.
- **Required correction** Ensure that all supplementary material is submitted and accessible, and that the legends for supplementary figures and tables are included.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Ethical compliance
- **Affected element** Cell line usage
- **Evidence pointer** Methods section "Cell culture and treatments"
- **Issue** The manuscript does not state whether the C4-2 cell line was authenticated or tested for mycoplasma contamination. This is a standard requirement for cell-based studies.
- **Required correction** Add a statement regarding cell line authentication and mycoplasma testing.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Figure 8
- **Evidence pointer** Results section "G4-mediated IKBKB upregulation activates NF-κB signaling and promotes malignant phenotypes"
- **Issue** The qPCR data in Figures 8A and 8B show changes in gene expression, but the statistical analysis is not described. It is unclear how many biological replicates were performed and what statistical test was used.
- **Required correction** Describe the statistical analysis for qPCR data, including the number of replicates and the test used.

- **Technical failings that need to be addressed before the case is established**
  1. Lack of direct causal evidence for G4-mediated regulation of IKBKB (R1-M1).
  2. Insufficient detail in the machine learning methodology (R1-M2).
  3. Absence of direct functional experiments manipulating IKBKB expression (R1-M3).
  4. Purely computational therapeutic proposals without experimental validation (R1-M4).
  5. Incomplete bioinformatics methods for ChIP-seq and single-cell RNA-seq analyses (R1-M5).

- **Assessment against Nature-style criteria**
  - **Originality** The integration of G4 ChIP-seq with machine learning for target discovery in prostate cancer is novel. The focus on immune-related G4-regulated genes is a fresh angle. However, the concept of G4s as therapeutic targets is not new, and the specific findings, while interesting, do not represent a paradigm shift.
  - **Scientific importance** The identification of IKBKB as a potential therapeutic target in prostate cancer is clinically relevant, given the need for new treatments in castration-resistant disease. However, the importance is diminished by the lack of causal evidence and the purely computational nature of the therapeutic proposals.
  - **Interdisciplinary readership** The manuscript bridges epigenetics, immunology, and computational biology, which could appeal to a broad audience. However, the depth of each individual component is limited, and the lack of experimental validation may reduce interest from experimental biologists.
  - **Technical soundness** The computational analyses are generally sound, but the machine learning pipeline is under-described, and the functional experiments are limited. The absence of G4-mutant assays is a significant technical gap.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible, but some sections, particularly the machine learning and AI-based design, may be challenging for readers without computational expertise. The discussion could be clearer.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an interesting hypothesis and a plausible pipeline, but the central causal claim (G4-mediated regulation of IKBKB) is not supported by direct evidence. The therapeutic proposals are speculative. Substantial additional experimental work is required to establish the case. I would be supportive if the authors provide direct evidence for G4-mediated regulation of IKBKB (e.g., G4-disrupting mutations), validate the machine learning pipeline with full methodological detail, and provide at least preliminary experimental validation of the proposed therapeutic strategies.

## Risk / unsupported claims
- The claim that "G4 stabilization increased IKBKB expression and activated the NF-κB pathway" is supported only by pharmacological experiments with potential off-target effects; causality is not established.
- The claim that "IKBKB promoted genome instability, tumor stemness, and immune microenvironment remodeling" is based on correlation analyses, not direct functional experiments.
- The claim that "the presence of a promoter G4 structure is associated with higher basal transcriptional activity of IKBKB" is based on a single cell line comparison (C4-2 vs. HepG2) and is not generalizable.
- The proposed CRISPR-dCas9 strategy for G4 disruption is described conceptually but not experimentally tested; its feasibility is unproven.
- The AI-designed peptide inhibitors are generated in silico but not synthesized or tested; their binding affinity and biological activity are unknown.
- The machine learning hub gene identification is not reproducible without detailed methodology.
- The single-cell RNA-seq analysis is mentioned but not described, making the results unverifiable.