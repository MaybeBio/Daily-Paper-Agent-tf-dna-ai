## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary figure/table legends.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with Nature-style criteria. Editorial and formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors present a pipeline that integrates time-series nitrogen (N) response transcriptomics in maize, inference of gene regulatory networks (GRNs) using dynamic factor graphs (DFG), validation of transcription factor (TF) targets via a cell-based TARGET assay, and machine learning (XGBoost) to identify conserved NUE regulons between maize and Arabidopsis. They claim that conserved NxTime genes enhance NUE prediction and that a specific conserved regulon (ZmMYB34/R3 and AtDIV1) significantly improves predictive performance.
- **Visible evidence base** Abstract, full results section, materials and methods, and supplementary figure/table legends. No raw data, code, or supplementary files were provided for direct inspection.
- **Missing materials affecting confidence** Supplementary figures S1–S20, tables S1–S28, data sets 1–5, raw sequencing data, code repository, and the Arabidopsis NxTime dataset (Varala et al. 2018) were not accessible. These are critical for verifying statistical analyses, network inference parameters, and machine learning performance.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive and ambitious systems biology approach to identify conserved regulatory modules controlling nitrogen use efficiency (NUE) in maize and Arabidopsis. The integration of time-series data, network inference, experimental TF validation, and machine learning is conceptually strong and addresses a significant agricultural challenge. However, the current evidence base is insufficient to fully support the central claims. Key concerns include the lack of accessible supplementary data, potential circularity in the NUE Regulon scoring, limited validation of the machine learning predictions, and unclear generalizability of the TARGET assay results to in planta conditions. The work is potentially important but requires substantial additional evidence and clarification before the case is established.
- **Who would be interested in the results, and why** Plant systems biologists, computational biologists working on gene regulatory networks, and crop scientists focused on nitrogen use efficiency and sustainable agriculture. The methodological pipeline (GRN inference + machine learning + cross-species conservation) will interest researchers developing trait-prediction frameworks. The identification of specific TF regulons (e.g., ZmMYB34/R3, AtDIV1) may guide breeding or genetic engineering efforts.
- **Major strengths**
  1. Novel integration of time-series N-response data with network inference and machine learning to identify trait-relevant regulons.
  2. Experimental validation of 23 maize TFs using a cell-based TARGET assay, providing a substantial resource for the community.
  3. Cross-species conservation analysis across a C3–C4 divide (160 million years) adds evolutionary significance.
  4. The NUE Regulon scoring approach is a creative way to prioritize network modules for trait prediction.
  5. The manuscript is generally well-written and logically structured, with clear objectives and a coherent narrative.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that the conserved NxTime genes (331 in maize) significantly outperform random gene sets in predicting NUE traits (Figure 6).
  - **Evidence pointer** Results section "Model-to-crop conserved N-response genes enhance machine learning of genes-of-importance to NUE"; Figure 6; Supplementary Tables S20 and S21.
  - **Concern** The statistical comparison against random gene sets is described, but the exact methodology for generating random sets, the number of random iterations, and the distribution of performance metrics are not fully detailed in the main text. Without access to the supplementary methods or code, it is impossible to assess whether the random baseline is appropriate (e.g., matched for gene number, expression variance, or network connectivity). Additionally, the performance metric (Pearson's r) is reported from 100 iterations, but the variance across iterations and the significance threshold are not stated.
  - **Why it matters** The central claim that conserved NxTime genes enhance NUE prediction hinges on this comparison. If the random baseline is not properly controlled, the observed improvement could be due to confounding factors (e.g., gene expression dynamic range) rather than biological conservation.
  - **Resolution test** Provide detailed methods for random gene set generation, including matching criteria (e.g., expression level, variance, GC content). Report the full distribution of performance metrics (e.g., boxplots) and the statistical test used to compare the conserved set against random sets. Make the code and random seed available for reproducibility.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Circularity / validation
  - **Claim pointer** The NUE Regulon score integrates XGBoost NUEscores with GRN edges to rank TFs, and the top-ranked regulon (ZmMYB34/R3) is then used to predict NUE in independent datasets.
  - **Evidence pointer** Results section "NUE Regulon: integration of gene networks with machine learning scores for NUE trait predictions"; Figure 7; Supplementary Table S22.
  - **Concern** The NUE Regulon score is calculated using the same XGBoost NUEscores that were derived from the conserved NxTime genes. If the conserved NxTime genes were already selected for their predictive power, then using their NUEscores to rank TFs and subsequently testing the resulting regulon on the same or related datasets may introduce circularity. The manuscript does not clearly state whether the independent datasets (Li et al. 2023) were used only for final validation or also for feature selection. Additionally, the improvement in prediction using the regulon genes over random conserved NxTime genes (Figure 8B, C) needs to be compared against a baseline that accounts for the feature selection process.
  - **Why it matters** If the regulon is derived from the same data used for evaluation, the reported predictive performance may be optimistically biased. This would undermine the claim that the identified regulon is genuinely informative for NUE.
  - **Resolution test** Clarify the data splitting strategy: which datasets were used for feature selection, model training, and final evaluation. Perform a nested cross-validation or a fully independent validation where the regulon is fixed before testing. Compare the regulon's performance against random gene sets of the same size that are also selected from the conserved NxTime genes (to control for selection effects).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of TARGET assay
  - **Claim pointer** The TARGET assay in maize protoplasts identifies direct TF targets that are used to validate and prune the GRN, and the authors suggest these reflect in planta regulatory relationships.
  - **Evidence pointer** Results section "Validation of maize TFs that regulate genes in the temporal N-response cascade"; Figure 2; Supplementary Figure S10.
  - **Concern** The TARGET assay is performed in isolated protoplasts with overexpression of TF-GR fusion proteins. While this is a valuable high-throughput approach, it may not fully recapitulate in planta conditions, including chromatin context, tissue-specific cofactors, and post-translational modifications. The manuscript does not discuss potential limitations of this system or provide orthogonal validation (e.g., ChIP-seq in planta, mutant analysis) for the key TFs beyond ZmKN1.
  - **Why it matters** The GRN pruning and subsequent regulon identification rely heavily on the TARGET-derived TF-target edges. If these edges are not representative of in planta regulation, the network may be biased, and the resulting regulon may not be biologically meaningful.
  - **Resolution test** Provide additional validation for at least a subset of the 23 TFs, such as ChIP-seq in plant tissues or comparison with published in planta binding data. Discuss the limitations of the protoplast system and how they might affect the network inference. If possible, include a sensitivity analysis showing that the main conclusions are robust to the inclusion or exclusion of TARGET-derived edges.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor of network inference
  - **Claim pointer** The DFG-inferred networks outperform GENIE3, dynGENIE3, and Pearson correlation in predicting TF-target edges (Supplementary Figure S11).
  - **Evidence pointer** Results section "Time-based network inference and validation of TFs controlling the temporal nitrogen response cascade in maize"; Supplementary Figure S11; Supplementary Table S13.
  - **Concern** The AUPR comparison is described, but the details of the evaluation are incomplete. Specifically, it is unclear how the gold standard for TF-target edges was defined (e.g., only TARGET-validated edges for 23 TFs, or a broader set). The number of positive and negative edges, the handling of TFs not in the TARGET set, and the statistical significance of the AUPR differences are not fully reported. Additionally, the permutation test for the DFN network is mentioned, but the null distribution and the exact p-value calculation are not described.
  - **Why it matters** The claim that DFG is superior to other methods is a key methodological contribution. Without rigorous evaluation, readers cannot assess whether the improvement is meaningful or an artifact of the evaluation setup.
  - **Resolution test** Provide a detailed description of the gold standard construction, including the number of positive and negative edges. Report AUPR values with confidence intervals and the results of statistical tests comparing methods. Describe the permutation test procedure in full, including how random networks were generated and how p-values were computed.
  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility and data availability
  - **Claim pointer** The authors state that raw sequencing data are deposited in GEO (GSE280353) and code is available on GitHub.
  - **Evidence pointer** Data availability section.
  - **Concern** While the data availability statement is present, the specific accession for the TARGET and ChIP-seq data is not broken down by experiment type. The GitHub link is provided, but it is not clear whether the code includes all analysis steps (e.g., network inference, machine learning, statistical tests) and whether it is versioned and documented. Without access to the code and data, the reproducibility of the results cannot be verified.
  - **Why it matters** Reproducibility is a core requirement for Nature-style publications. The inability to access the code and data prevents independent verification of the claims and limits the utility of the resource for the community.
  - **Resolution test** Provide a detailed data availability statement with separate accessions for RNA-seq, TARGET, and ChIP-seq data. Ensure the GitHub repository includes all scripts, configuration files, and a README with instructions for reproducing the analysis. Consider depositing the code in a permanent archive (e.g., Zenodo) with a DOI.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1C
  - **Evidence pointer** Results section "Identification of a temporal cascade of early-to-late nitrogen-responsive genes in maize"; Figure 1C.
  - **Issue** The description of the spline model and the JIT binning is brief. It is unclear how the degrees of freedom (df = 5) were chosen and whether sensitivity analyses were performed.
  - **Required correction** Add a brief justification for the spline model parameters and mention any sensitivity analyses in the methods or supplementary materials.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Figure 5 and ZmKN1 analysis
  - **Evidence pointer** Results section "Network Walking uncovers a new role for ZmKN1 in the maize nitrogen response"; Figure 5.
  - **Issue** The claim that ZmKN1 has a "new role" in N response is based on overlap with NxTime genes and GO enrichment. However, the functional significance of this overlap is not experimentally tested (e.g., via mutant phenotyping under different N conditions).
  - **Required correction** Soften the claim or add a statement that functional validation is ongoing. Alternatively, include a brief discussion of how the predicted role could be tested.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Figure 8A
  - **Evidence pointer** Results section "NUE Regulon: integration of gene networks with machine learning scores for NUE trait predictions"; Figure 8A.
  - **Issue** The orthology mapping plot is described but not fully explained. It is unclear how the 23 Arabidopsis and 24 maize genes were selected for display and whether all are direct targets of the TFs.
  - **Required correction** Add a legend or text explaining the selection criteria for the displayed genes and the meaning of the visual elements (e.g., node size, color).
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section (not provided in full, but implied).
  - **Issue** The discussion does not address potential limitations of the machine learning approach, such as the risk of overfitting despite cross-validation, or the interpretability of the XGBoost model.
  - **Required correction** Add a paragraph discussing limitations and potential biases in the machine learning pipeline, and how they might affect the conclusions.
- **Technical failings that need to be addressed before the case is established**
  1. R1-M1: Insufficient detail on random gene set generation and statistical comparison for the NUE prediction enhancement claim.
  2. R1-M2: Potential circularity in the NUE Regulon scoring and validation process.
  3. R1-M3: Lack of orthogonal validation for TARGET-derived TF-target edges in planta.
  4. R1-M4: Incomplete description of the AUPR evaluation and permutation testing for network inference.
  5. R1-M5: Inadequate documentation of code and data for reproducibility.
- **Assessment against Nature-style criteria**
  - **Originality** High. The integration of time-series data, network inference, experimental TF validation, and machine learning into a single pipeline for NUE is novel. The cross-species conservation of regulons is a fresh angle.
  - **Scientific importance** High. NUE is a critical trait for sustainable agriculture. The identification of conserved regulatory modules could inform breeding and genetic engineering strategies. The methodological framework may be applicable to other traits and species.
  - **Interdisciplinary readership** Moderate to high. The work bridges plant biology, computational biology, and agronomy. The machine learning and network inference aspects may appeal to a broader computational audience, but the focus on NUE and plant systems may limit appeal to non-specialists.
  - **Technical soundness** Currently insufficient. The main claims are plausible but not fully supported by the accessible evidence. The lack of supplementary data and code prevents thorough evaluation. The potential circularity in the NUE Regulon scoring is a significant concern.
  - **Readability for nonspecialists** Good. The manuscript is well-structured and the narrative is clear. However, some sections (e.g., DFG, XGBoost) may be challenging for readers without a computational background. The authors could improve accessibility by adding a brief primer on these methods.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework and potential impact are strong, but the current evidence base is insufficient to fully establish the claims. The authors must address the concerns regarding statistical rigor, potential circularity, and reproducibility before the case is made.