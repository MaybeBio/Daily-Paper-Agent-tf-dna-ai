## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure/table legends.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of conclusions, and clarity of the presented work. This review does not assess editorial fit or language polishing beyond scientific readability.
- **Shared manuscript claim summary** The authors profile temporal changes in chromatin accessibility (ATAC-seq) and transcriptome (RNA-seq) in *Medicago truncatula* roots treated with lipo-chitooligosaccharides (LCOs). They apply a novel integrative algorithm, dynamic regulatory module networks (DRMN), to predict cis-regulatory elements and transcription factors driving nodulation-related gene expression. They validate two predicted regulators, EIN3 and ERF1, via RNAi knockdown, showing reduced nodule numbers.
- **Visible evidence base** Main text figures (Figs. 1–8), methods section, and referenced supplementary figures and tables (Additional files 1 and 2). No raw data or code were provided for review.
- **Missing materials affecting confidence** Raw sequencing data, processed data matrices, code for DRMN and MTG-LASSO, and detailed parameter settings for all analyses were not provided. Supplementary figures and tables were referenced but not fully accessible for this review.

## Reviewer
- **Overall assessment** This manuscript presents a valuable and timely dataset of temporal chromatin accessibility and transcriptome changes during early nodulation in *M. truncatula*. The integration of these data using DRMN is a novel and promising approach. The identification and experimental validation of EIN3 and ERF1 as regulators of nodulation is a significant finding. However, several technical aspects of the analysis, particularly regarding the DRMN application, statistical rigor, and the interpretation of the validation experiments, require clarification and strengthening. The manuscript is well-written and will be of interest to the plant-microbe interaction and gene regulation communities.
- **Who would be interested in the results, and why** Researchers studying legume-rhizobia symbiosis, root nodule development, plant hormone signaling (ethylene, auxin, ABA), chromatin dynamics and gene regulation in plants, and those interested in integrative computational methods for multi-omics time-series data.
- **Major strengths**
    1.  The generation of a comprehensive, time-resolved dataset of both chromatin accessibility and transcriptome changes in response to LCOs is a significant resource for the community.
    2.  The application of DRMN, a sophisticated algorithm, to integrate these data types and predict regulatory relationships is a novel and powerful approach that goes beyond standard correlation analyses.
    3.  The experimental validation of two computationally predicted regulators (EIN3 and ERF1) using RNAi provides functional evidence supporting the predictive power of the approach.
    4.  The identification of both known and novel regulators, including those involved in hormone signaling, provides a solid foundation for future mechanistic studies.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim summary** The authors claim that DRMN analysis predicts transcription factors that "most significantly contribute to transcriptomic changes associated with symbiosis."
    - **Evidence pointer** Results section "DRMN integration of ATAC-seq and RNA-seq data identifies key regulators...", Figure 6.
    - **Concern** The manuscript does not provide sufficient detail on the DRMN model's parameters, validation, and statistical significance. The selection of hyperparameters (ρ1, ρ2, ρ3) is described, but the final model's performance (e.g., cross-validated R²) is not reported. More critically, the method for prioritizing regulators (Figure 6) is based on a t-test of regression coefficient changes, but the multiple testing problem across hundreds of motifs and modules is not addressed. The FDR-corrected q-values are mentioned for motif enrichment, but not for the significance of the coefficient changes. This makes it difficult to assess the robustness of the predicted regulator list.
    - **Why it matters** Without a clear demonstration of the model's predictive accuracy and statistical rigor, the central claim that these are the "most significant" regulators is not fully supported. The list of prioritized regulators could be influenced by noise or overfitting.
    - **Resolution test** The authors should provide: (1) cross-validated performance metrics (e.g., correlation between predicted and actual expression) for the final DRMN model; (2) a clear description of how the significance of the change in regression coefficients was assessed, including correction for multiple comparisons; (3) a sensitivity analysis showing how the prioritized regulator list changes with different hyperparameter settings.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim summary** The authors state that "RNAi-based knockdown of EIN3 and ERF1 reduced nodule number in M. truncatula validating the role of these predicted regulators in symbiosis."
    - **Evidence pointer** Results section "EIN3 and ERF1 are important regulators of root nodule symbiosis...", Figure 8.
    - **Concern** The validation experiment is presented with minimal detail. The number of biological replicates for the RNAi experiment is not stated in the main text (only n=20, 16, and 13 are shown in the figure legend). The efficiency of the knockdown is not quantified (e.g., qRT-PCR data is mentioned in methods but not shown). The statistical test used is mentioned (ANOVA with Tukey's HSD), but the effect size is not discussed. Furthermore, the specificity of the RNAi construct is not addressed. While the reduction in nodule number is clear, the lack of molecular characterization of the knockdown lines weakens the claim of validation.
    - **Why it matters** A functional validation experiment is only convincing if the knockdown is efficient and specific. Without this data, the observed phenotype could be due to off-target effects or incomplete knockdown.
    - **Resolution test** The authors should provide: (1) qRT-PCR data demonstrating the efficiency of transcript knockdown for EIN3 and ERF1 in the RNAi roots; (2) a statement on the number of independent biological replicates and the statistical power of the experiment; (3) a discussion of potential off-target effects, or a demonstration of specificity (e.g., complementation or use of multiple independent RNAi lines).

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Reproducibility
    - **Claim summary** The study's findings are based on a complex computational pipeline and novel datasets.
    - **Evidence pointer** Methods section, all figure legends.
    - **Concern** The manuscript does not state where the raw sequencing data (FASTQ files) and processed data matrices (e.g., normalized ATAC-seq counts, expression matrices) will be deposited. The custom code for DRMN and MTG-LASSO is not provided or referenced to a public repository. This is a major impediment to reproducibility and to the community's ability to fully utilize the valuable dataset.
    - **Why it matters** For a resource paper of this nature, data and code availability are essential. Without them, the claims cannot be independently verified, and the dataset's utility is significantly diminished.
    - **Resolution test** The authors should provide a clear "Data Availability" statement with accession numbers for all raw and processed data, and a link to a public repository (e.g., GitHub) for all custom analysis code.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific Importance
    - **Claim summary** The authors state that "analyses of early temporal events driving this symbiosis have only captured correlative relationships between regulators and targets at mRNA level."
    - **Evidence pointer** Background section.
    - **Concern** While the integration of chromatin accessibility is a step forward, the DRMN and MTG-LASSO methods are still fundamentally correlative. They predict regulatory relationships based on statistical associations between accessibility and expression. The manuscript does not fully acknowledge this limitation. The validation of EIN3 and ERF1 is a good start, but it does not validate the entire network of predicted interactions.
    - **Why it matters** The novelty of the work is partly framed as moving beyond correlation. It is important to clearly state that the computational predictions are still hypotheses that require further validation, and that the current study only validates a small fraction of the predicted network.
    - **Resolution test** The authors should temper the language in the discussion to more clearly distinguish between predictive modeling and causal validation. They should also discuss the limitations of their approach for inferring causality and suggest future experimental approaches (e.g., DAP-seq, ChIP-seq, or perturbation experiments) to validate the broader network.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Figure 1C
    - **Evidence pointer** Figure 1C and corresponding text.
    - **Issue** The F-score comparison to the Larrainzar et al. dataset is difficult to interpret from the figure alone. It is unclear what the color scale represents and how the comparisons were structured.
    - **Required correction** Please provide a clearer explanation of the F-score matrix in the figure legend, including what each cell represents and the direction of the comparison.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Methods section "Expression clustering analysis with ESCAROLE"
    - **Evidence pointer** Methods section.
    - **Issue** The description of the ESCAROLE analysis is somewhat brief. The specific parameters used for the hierarchical clustering (e.g., linkage method, distance metric) are not fully described.
    - **Required correction** Please provide the specific parameters used for the hierarchical clustering step to ensure reproducibility.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Discussion section
    - **Evidence pointer** Discussion section.
    - **Issue** The discussion of the "engineering of nodulation in species unable to establish that symbiosis naturally" is somewhat speculative and not directly supported by the data presented.
    - **Required correction** Consider softening this statement or framing it as a long-term, speculative goal.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** Methods section "Exploratory analysis of ATAC-seq data"
    - **Evidence pointer** Methods section.
    - **Issue** The manuscript states that "fragment distributions in ±1 kbp of the transcription start site (TSS) were examined" but does not provide a clear metric for the quality of the ATAC-seq data, such as the fraction of reads in peaks (FRiP) or the transcription start site enrichment score.
    - **Required correction** Please include standard ATAC-seq quality metrics (e.g., FRiP score, TSS enrichment) to demonstrate the quality of the data.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of statistical rigor in the DRMN regulator prioritization.
    - R1-M2: Insufficient detail and characterization of the RNAi validation experiments.
    - R1-M3: Lack of data and code availability statement.

## Risk / unsupported claims
- The claim that the identified regulators "most significantly contribute" to transcriptomic changes is not fully supported due to the lack of statistical correction for multiple testing in the prioritization step.
- The claim that the RNAi experiments "validate" the role of EIN3 and ERF1 is weakened by the lack of molecular characterization of the knockdown lines.
- The statement in the conclusion about engineering nodulation in non-legumes is speculative and not directly supported by the data.
- The generalizability of the DRMN predictions to other legume species or rhizobial strains is not discussed and cannot be assessed from the provided data.