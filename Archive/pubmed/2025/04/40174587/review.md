## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, interpretability of deep learning models, experimental validation, and claims supported by the provided evidence
- **Shared manuscript claim summary** The authors propose that cell-type-specific regulatory responses to the Hippo signaling pathway are encoded in cis-regulatory sequences. Using a deep learning model (BPNet) trained on high-resolution ChIP-nexus data for TEAD4, YAP1, TFAP2C, CDX2, and GATA3 in mouse trophoblast stem cells, they identify sequence rules governing YAP1/TEAD4 binding. They report that TFAP2C motifs enhance YAP1 binding in a distance-dependent manner (soft syntax), and that a strictly spaced Tead double motif is a widespread, canonical, highly active element bound cooperatively by TEAD4 through labile protein-protein interactions, as supported by molecular dynamics simulations and validated by CRISPR-Cas9 editing and reporter assays.
- **Visible evidence base** Figures 1–6 and S1–S6, Tables S1–S5, methods descriptions for ChIP-nexus, ChIP-seq, ATAC-seq, TT-seq, RNA-seq, CRISPR-Cas9 editing, BPNet training, and MD simulations
- **Missing materials affecting confidence** Raw data files, full figure panels with all subpanels, exact statistical test outputs, model performance metrics on validation sets, MD simulation convergence analyses, and complete CRISPR editing validation data were not fully accessible in the provided text

## Reviewer

- **Overall assessment** This manuscript presents a compelling and technically sophisticated integration of deep learning, genomics, and biophysical simulation to address a fundamental question in gene regulation: how signaling effectors achieve cell-type-specific transcriptional responses. The central claim that cis-regulatory sequence rules encode the response to Hippo signaling is well supported by the combination of predictive modeling, interpretation, and experimental validation. The discovery of the Tead double motif as a widespread canonical element, and the proposal of labile protein-protein interactions as a mechanism for cooperative binding, are novel and significant contributions. The work is likely to be of broad interest to the gene regulation, developmental biology, and computational biology communities. However, several technical concerns regarding model validation, statistical rigor, and the interpretation of MD simulations need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, enhancer biology, signaling pathways (particularly Hippo/YAP/TAZ), and cell-type specification will find this work directly relevant. The demonstration that interpretable deep learning can uncover mechanistic insights from genomics data will also appeal to computational biologists and method developers. The findings on TEAD4 cooperative binding and the role of TFAP2C in trophoblast development have implications for developmental biology and potentially for cancer biology, given the importance of Hippo signaling in both contexts.

- **Major strengths**
  1. The study addresses a long-standing and important problem: how signaling pathways achieve cell-type-specific transcriptional outcomes. The hypothesis that cis-regulatory sequences encode this specificity is well formulated and tested.
  2. The integration of a high-resolution genomics approach (ChIP-nexus) with a state-of-the-art deep learning model (BPNet) is methodologically strong. The use of multiple interpretation techniques (contribution scores, in silico motif injection) provides complementary evidence.
  3. The experimental validation is thorough, including luciferase reporter assays, CRISPR-Cas9 editing of endogenous enhancers, and in vivo embryo aggregation experiments. This moves beyond purely computational claims.
  4. The discovery of the Tead double motif as a widespread, functional element is a significant finding that challenges the field to reconsider what constitutes a canonical Hippo response element.
  5. The use of MD simulations to propose a mechanistic basis for cooperative binding is innovative and provides a testable hypothesis for future structural studies.
  6. The manuscript is generally clearly written and the figures appear well-organized, with appropriate use of supplementary materials.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of model validation
  - **Claim pointer** The authors claim that BPNet accurately predicts TF binding at base resolution and that the learned rules are general and genome-wide.
  - **Evidence pointer** Figure 1D, S1C–S1F; Methods "BPNet model training"
  - **Concern** The manuscript reports high prediction accuracy but does not provide sufficient detail on the quantitative metrics used to assess model performance. The Jensen-Shannon distance values are mentioned for one example (Figure 1D), but global performance metrics across all test chromosomes and all TFs are not systematically reported. The cross-validation approach is mentioned but the variance across folds is not shown. Furthermore, the comparison to replicate reproducibility (Figure S1C) is mentioned but the actual values and thresholds for "high accuracy" are not specified.
  - **Why it matters** The entire interpretability pipeline depends on the model being sufficiently accurate. If the model is not demonstrably accurate on held-out data, the subsequent interpretation of motif contributions and syntax rules is not reliable. The field has established standards for reporting deep learning model performance in genomics, and this manuscript falls short of those standards.
  - **Resolution test** Provide a comprehensive table of performance metrics (e.g., Pearson/Spearman correlations for counts, AUPRC for profile predictions at multiple resolutions) for each TF across all test chromosomes, with mean and standard deviation across cross-validation folds. Include a comparison to replicate reproducibility for each TF. Show that the model outperforms simpler baselines (e.g., PWM-based predictions).

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor of distance-dependent analyses
  - **Claim pointer** The authors claim that TFAP2C motifs enhance YAP1 binding in a distance-dependent manner, with closer distances showing stronger effects (Figure 3B, 3C).
  - **Evidence pointer** Figure 3B, 3C, S3A–S3D; Table S5
  - **Concern** The statistical analysis supporting the distance-dependent effect is not fully described. The Wilcoxon test p-value is reported for Figure 3B, but the effect sizes, confidence intervals, and the number of observations in each distance bin are not provided. The linear regression in Figure 3C reports a slope and p-value, but the R² value, the confidence interval of the slope, and the potential confounding factors (e.g., motif strength, chromatin context) are not discussed. The analysis appears to pool all genomic instances, which may violate independence assumptions.
  - **Why it matters** The distance-dependent effect is a central claim of the paper. If the statistical evidence is weak or confounded, the conclusion that soft syntax governs TFAP2C-TEAD4 cooperativity is not robust. The field requires rigorous statistical treatment of such genome-wide analyses.
  - **Resolution test** Provide a detailed description of the statistical model, including the number of observations per distance bin, effect sizes with confidence intervals, and a discussion of potential confounders. Consider using mixed-effects models that account for genomic locus identity. Show that the distance-dependent effect is robust to different binning strategies and to the inclusion of control variables (e.g., motif strength, GC content).

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Interpretation of MD simulations
  - **Claim pointer** The authors claim that MD simulations suggest TEAD4 binds the double motif cooperatively through labile protein-protein interactions that depend on the DNA template.
  - **Evidence pointer** Figure 5A–5E, S5A–S5N; Methods "Molecular dynamics simulations"
  - **Concern** The MD simulation results are used to support a mechanistic claim about cooperative binding. However, the manuscript does not provide sufficient detail on the convergence of the simulations, the sampling of the protein-protein interaction space, or the statistical significance of the differences in buried surface area between the wild-type and mutant/deletion systems. The claim that interactions are "labile" is based on the observation of dynamic contacts, but no quantitative measure of lability (e.g., residence times, free energy profiles) is provided. The comparison to other TF complexes (Figure 5H) is qualitative and may not be appropriate given different simulation/experimental conditions.
  - **Why it matters** The MD simulations are a key piece of evidence for the proposed mechanism. If the simulations are not well-converged or the analysis is not statistically robust, the mechanistic claim is weakened. Over-interpretation of MD data is a common pitfall in the literature.
  - **Resolution test** Provide convergence analysis (e.g., RMSD vs. time, block averaging of buried surface area), replicate simulations with different initial velocities, and a statistical comparison of buried surface area distributions (e.g., bootstrap or Bayesian estimation). Discuss the limitations of the simulation timescale and the potential for sampling artifacts. Consider free energy calculations (e.g., umbrella sampling) to quantify the strength of the protein-protein interaction.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of the Tead double motif finding
  - **Claim pointer** The authors claim that the Tead double motif is a widespread, canonical element of the Hippo pathway, and that this generalizes to other TEAD family members and cell types.
  - **Evidence pointer** Figure 4E, S4E; Results "The Tead double motif is a canonical element of the Hippo pathway"
  - **Concern** The generalization to other cell types is based on analysis of ENCODE ChIP-seq data for TEAD1-4. However, the analysis appears to be limited to motif discovery in peak regions, and it is not clear whether the functional activity of the Tead double motif (e.g., enhancer activation) was tested in these other cell types. The claim of "canonical" status would be strengthened by demonstrating that the double motif is enriched in active enhancers and that its disruption affects gene expression in multiple contexts.
  - **Why it matters** The broad significance of the finding depends on its generalizability. If the Tead double motif is only functionally important in trophoblast cells, its impact is more limited.
  - **Resolution test** Provide additional analysis of ENCODE data showing that Tead double motifs are enriched in active enhancer marks (e.g., H3K27ac) across multiple cell types. If possible, include a reporter assay or CRISPR experiment in a second cell type to demonstrate functional conservation.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of methods
  - **Affected element** ChIP-nexus data processing
  - **Evidence pointer** Methods "ChIP-nexus data processing"
  - **Issue** The description of ChIP-nexus data processing is brief and lacks some technical details that would allow replication, such as the specific parameters used for adapter trimming, the criteria for read deduplication, and the exact normalization procedure.
  - **Required correction** Expand the methods section to include all relevant parameters and software versions. Consider providing a step-by-step pipeline description or a link to a public workflow.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Figure accessibility
  - **Affected element** Figure 1B
  - **Evidence pointer** Figure 1B
  - **Issue** The Spearman correlation matrix in Figure 1B is mentioned in the text but the actual values are not reported in the figure legend or in the text. It is unclear how many regions were used for this analysis.
  - **Required correction** Add the correlation values to the figure or provide them in the legend. State the number of regions used.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation of luciferase assays
  - **Affected element** Figure 3A, 3F, S3E
  - **Evidence pointer** Figure 3A, 3F, S3E
  - **Issue** The luciferase assays are normalized to an empty vector control, but it is not clear whether the normalization accounts for transfection efficiency differences across constructs. The use of a co-transfected control (e.g., Renilla) is standard practice.
  - **Required correction** Clarify the normalization procedure. If a co-transfected control was not used, discuss the potential impact on the results and consider repeating the experiments with a dual-luciferase assay.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clarity of terminology
  - **Affected element** "Soft syntax"
  - **Evidence pointer** Throughout the manuscript
  - **Issue** The term "soft syntax" is used to describe distance-dependent cooperativity without strict spacing. While the concept is clear, the term may be unfamiliar to some readers and is not formally defined.
  - **Required correction** Provide a clear definition of "soft syntax" when it is first introduced, and contrast it with "strict syntax" as exemplified by the Tead double motif.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness of data availability
  - **Affected element** Data and code availability section
  - **Evidence pointer** Data and code availability
  - **Issue** The statement "The trained BP model is available at Zenodo" is good, but the link to the GitHub repository is provided. It would be helpful to also provide a link to the processed data files (e.g., bigWig files for ChIP-nexus and ChIP-seq) in GEO.
  - **Required correction** Ensure that all processed data files are deposited and that the accession numbers are provided in the manuscript.

- **Technical failings that need to be addressed before the case is established**
  1. Insufficient reporting of model performance metrics (R1-M1).
  2. Incomplete statistical description of distance-dependent analyses (R1-M2).
  3. Lack of convergence and statistical analysis for MD simulations (R1-M3).

- **Assessment against Nature-style criteria**
  - **Originality** High. The application of interpretable deep learning to uncover regulatory syntax for a signaling pathway is novel. The discovery of the Tead double motif as a widespread canonical element, and the proposal of labile protein-protein interactions, are original contributions.
  - **Scientific importance** High. The work addresses a fundamental question in gene regulation and provides a general framework for studying how signaling pathways achieve cell-type-specific responses. The findings have implications for developmental biology and potentially for diseases where Hippo signaling is dysregulated.
  - **Interdisciplinary readership** High. The work bridges computational biology, genomics, developmental biology, and biophysics. It should appeal to a broad audience.
  - **Technical soundness** Moderate to High. The experimental design is generally sound, but the technical concerns outlined above (model validation, statistics, MD simulations) need to be addressed to fully establish the claims.
  - **Readability for nonspecialists** Good. The manuscript is well-written and the concepts are explained clearly. The use of figures helps convey the main findings. However, some sections (e.g., MD simulations) may be challenging for non-experts.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a significant and novel contribution with a strong experimental validation strategy. The main issues are related to the completeness of the technical reporting and the statistical rigor of some analyses. If the authors can address these concerns, the paper would be suitable for publication in a high-impact journal.