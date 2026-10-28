## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Technical and conceptual evaluation of the described method, benchmarking claims, and biological validation, based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present scRegulate, a variational autoencoder framework that embeds prior gene regulatory network knowledge to infer transcription factor activities and cell-type-specific gene regulatory networks from single-cell RNA sequencing data. They claim superior performance over existing methods in clustering accuracy, GRN inference on synthetic gold-standard data, and prediction of experimentally validated TF knockdown effects, alongside biological relevance demonstrated on PBMC data.
- **Visible evidence base** Main text including Methods, Results, Discussion; references to Figures 1–5 and Supplementary Figures/Tables; no actual figures, tables, or supplementary material were provided
- **Missing materials affecting confidence** All figures, supplementary figures, supplementary tables, and supplementary notes; actual numerical results beyond those quoted in text; code repository contents; detailed hyperparameter settings; dataset preprocessing specifics

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach that combines prior knowledge with variational inference for TF activity and GRN inference. The methodological framework is clearly described and the motivation is well-argued. However, the evidence provided in the text alone is insufficient to fully evaluate the claims. Key quantitative results are reported without accompanying figures or statistical details, and several methodological choices require further justification. The biological validation on PBMC data is qualitative and would benefit from more rigorous comparison. The work has potential but the current evidence base does not fully establish the superiority claims over existing methods.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on single-cell transcriptomics, gene regulatory network inference, and transcription factor activity prediction. Researchers developing deep learning methods for biological data would also find the integration of prior knowledge into VAEs of interest. The method could be useful for those studying cell-type-specific regulatory mechanisms in development and disease.
- **Major strengths** 1) The conceptual integration of prior GRN knowledge into a VAE framework is novel and addresses a clear gap in existing methods. 2) The three-phase training approach (prior initialization, dynamic inference, cell-type-specific fine-tuning) is well-designed and logically motivated. 3) The use of multiple benchmark types (synthetic, Perturb-seq, real data) is comprehensive. 4) The method provides interpretable outputs (TF embeddings, cell-type-specific GRNs) that are directly useful for downstream analysis.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The lack of provided figures and supplementary data prevents verification of the reported quantitative results. The statistical comparison methodology against baseline methods is not fully described. The biological validation lacks quantitative rigor.
- **Assessment against Nature-style criteria** **Originality**: The approach of embedding prior GRN knowledge into a VAE for TF activity inference is original and distinct from existing methods. **Scientific importance**: TF activity inference from scRNA-seq is a fundamental problem, and improved methods with cell-type-specific resolution would be valuable. **Interdisciplinary readership**: The work bridges machine learning and molecular biology, potentially appealing to both computational and experimental researchers. **Technical soundness**: The methodological framework is sound in principle, but the provided evidence is insufficient to fully assess implementation and performance. **Readability for nonspecialists**: The manuscript is generally well-written and accessible, though some methodological details assume familiarity with VAE terminology.
- **Recommendation posture** Supportive if technical concerns are resolved and full evidence is provided; currently not fully established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims superior performance over existing methods in GRN inference (AUROC 0.71–0.86, AUPRC 0.80–0.95) and TF activity prediction from Perturb-seq data.
- **Evidence pointer** Figures 3A, 3B, S4, S5; location not provided
- **Concern** The reported quantitative results are presented without the accompanying figures or supplementary data. The text states specific AUROC/AUPRC values and p-values, but without the actual figures, tables, or statistical details, these claims cannot be independently verified. The comparison methodology against baseline methods (SCENIC, CellOracle, BITFAM, decoupleR) is not fully described, including how significance was determined and whether multiple testing corrections were applied.
- **Why it matters** The core claims of the manuscript rest on these quantitative comparisons. Without the actual data and figures, the reader cannot assess whether the reported improvements are meaningful, robust, or statistically significant. This is essential for establishing the method's validity.
- **Resolution test** Provide all figures and supplementary data with full statistical details, including confidence intervals, effect sizes, and the exact comparison methodology. Include the actual AUROC/AUPRC curves and the distribution of results across the five synthetic dataset subsets.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The manuscript states that scRegulate "dynamically tailors regulatory networks and TF activities to reflect the unique transcriptional landscapes of different cell populations" and that the prior GRN is "gradually relaxed" during training.
- **Evidence pointer** Methods section "Integration of Prior GRNs into TF Activity Estimation" and "GRN Prior Enforcement and Dynamic Updating"; location not provided
- **Concern** The mechanism by which the prior GRN is relaxed and how cell-type-specific GRNs are derived is not fully specified. The text describes a mask factor m(t) that transitions from 1 to 0, but the exact schedule, the criteria for determining when the prior is sufficiently relaxed, and how the final cell-type-specific GRNs are extracted from the model are unclear. Additionally, the relationship between the prior GRN (from TFLink) and the learned GRN weights is not fully explained.
- **Why it matters** The central innovation of the method is the integration and subsequent relaxation of prior knowledge. Without a clear description of this mechanism, the method cannot be reproduced or fully understood. The claim of cell-type-specific GRN inference depends on this mechanism being well-defined.
- **Resolution test** Provide a detailed algorithmic description of the training procedure, including the exact schedule for α and m(t), how cell-type-specific GRNs are computed from the model, and how the prior GRN influences the final learned weights. Include pseudocode or a formal algorithm box.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation rigor
- **Claim pointer** The manuscript claims that scRegulate "accurately recapitulates experimentally validated TF knockdown effects" and "identifies differentially active TFs that align with known immune regulatory pathways" in PBMC data.
- **Evidence pointer** Results sections "scRegulate Outperforms Alternatives in Predicting TF Activity from Experimental Knockdowns" and "scRegulate Uncovers Cell-Type-Specific Regulatory Programs in Real PBMC Data"; Figures 4, 5, S6–S8; location not provided
- **Concern** The biological validation on PBMC data is largely qualitative. The text lists known TFs (PAX5, BCL6, IRF4, GATA3, etc.) that were recovered, but does not provide a systematic quantitative comparison against a gold standard or against alternative methods. The GO enrichment analysis is described but the results are not shown. The hierarchical clustering of GRNs is mentioned but the figure is not provided. The claim of "accurate recapitulation" of Perturb-seq effects is based on a limited set of TFs (ELK1, EGR1, CREB1) and the reported p-values are not corrected for multiple testing.
- **Why it matters** Biological relevance is a key selling point of the method. Without rigorous quantitative validation, the biological claims remain anecdotal. The reader cannot assess whether the recovered TFs are truly specific to the method or would be found by any reasonable approach.
- **Resolution test** Provide quantitative enrichment statistics (e.g., hypergeometric test p-values) for the overlap between recovered TFs and known cell-type markers. Include a systematic comparison against alternative methods on the PBMC data. Show the GO enrichment results with full statistical details. Provide multiple testing correction for the Perturb-seq analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Baseline comparison fairness
- **Claim pointer** The manuscript claims that scRegulate "outperforms existing TF inference methods" across multiple benchmarks.
- **Evidence pointer** Results sections on clustering, GRN inference, and Perturb-seq; location not provided
- **Concern** The choice of baseline methods and the fairness of comparison are not fully justified. The text mentions SCENIC, decoupleR, BITFAM, and CellOracle, but does not describe how these methods were configured, whether hyperparameters were optimized for each, or whether the same preprocessing was applied. The comparison on clustering uses TF embeddings from each method, but the dimensionality and nature of these embeddings may differ substantially, potentially biasing the comparison.
- **Why it matters** Unfair or poorly described baseline comparisons can lead to misleading conclusions about method superiority. The reader needs to know that the comparison was conducted in a way that gives each method its best chance.
- **Resolution test** Describe the exact configuration and hyperparameter choices for each baseline method. State whether hyperparameter optimization was performed and how. Provide details on the preprocessing pipeline applied to each method. Consider including a sensitivity analysis to show that results are robust to reasonable variations in baseline configurations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, Results section; location not provided
- **Issue** The abstract states "achieving a mean log2 fold change of −0.61 to −18.92" for the Perturb-seq validation. This range is extremely wide and the lower bound (−18.92) seems implausibly large for a log2 fold change in a gene expression context. This may be a typographical error or may refer to a different metric.
- **Required correction** Clarify the exact metric and range reported. If this is indeed the range of log2 fold changes, provide context for why such extreme values are observed. If it is a typo, correct it.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, hyperparameter selection
- **Evidence pointer** Methods section "Loss Functions, Optimization, and Training Details"; location not provided
- **Issue** The text states that hyperparameter selection is described in "Section 2.3.4" but this section is not clearly identified in the provided text. The specific values for learning rate, batch size, number of epochs, latent dimension, and the α scheduling parameters (α_start, α_max, Δα) are not stated.
- **Required correction** Provide the specific hyperparameter values and the full training configuration in the main text or a clearly referenced supplementary section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, clustering performance
- **Evidence pointer** Results section "scRegulate TF Embeddings Capture Cellular Heterogeneity"; location not provided
- **Issue** The text reports mean ± standard deviation for clustering metrics (e.g., ARI 0.814 ± 0.042) but does not state the number of replicates or how the standard deviation was computed. It is unclear whether these are across the five synthetic subsets or across different random seeds.
- **Required correction** Specify the number of replicates and the source of variability (e.g., random seeds, data subsets). Report the exact number of runs used to compute the mean and standard deviation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Availability section
- **Evidence pointer** Data Availability section; location not provided
- **Issue** The text states that code is available on GitHub but does not provide a version number, commit hash, or license information. The statement "Supplementary data are available at Bioinformatics online" is inconsistent with the manuscript being a bioRxiv preprint.
- **Required correction** Provide a specific version or commit hash for the code repository. Correct the supplementary data availability statement to reflect the preprint status.

## Risk / unsupported claims
- The claim of "unprecedented resolution in studying cell-type-specific regulatory mechanisms" is not supported by the provided evidence and is overly strong.
- The statement that scRegulate "outperforms existing TF inference methods" is not fully supported without the actual comparison figures and statistical details.
- The biological relevance claims on PBMC data are based on qualitative observations and require quantitative validation.
- The claim that scRegulate "overcomes the limitation of approaches that rely on highly variable genes" is not empirically demonstrated in the provided text.
- The reported Perturb-seq results (mean log2 fold change range) appear potentially erroneous and require clarification.