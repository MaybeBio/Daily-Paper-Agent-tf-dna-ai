## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, data and code availability statements.
- **Assessment boundary** Scientific and technical evaluation of the SIGNET method as presented, including methodology, validation approach, and reported results. No assessment of code functionality or reproducibility beyond what is described in the text.
- **Shared manuscript claim summary** The authors present SIGNET, a deep learning framework using multiple-layer perceptron bagging to predict gene regulatory networks from single-cell RNA-seq data. The method identifies TF-target gene relationships by assessing prediction accuracy changes when individual TFs are removed from the input, followed by motif enrichment filtering and AUCell scoring. The authors claim improved sensitivity over SCENIC in identifying ChIP-seq-validated regulatory interactions, better clustering performance, and utility in identifying rare cell types and clinically relevant regulons.
- **Visible evidence base** Three scRNA-seq datasets (GSE60361, GSE115978, GSE103322), one large multi-organ dataset (GSE109774), ChIP-seq cross-validation, TCGA survival analysis, and multiple clustering metrics (F score, CSI, PSI, ARI, NMI, RMSSTD, MHG).
- **Missing materials affecting confidence** No supplementary figures or tables were provided for review. No detailed hyperparameter settings, training curves, or convergence analysis. No statistical significance testing for the reported sensitivity differences. No comparison with other deep learning-based GRN inference methods. No runtime or computational cost analysis. No detailed description of the bagging ensemble size or aggregation strategy.

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful approach to GRN inference from scRNA-seq data, with a reasonable methodological pipeline combining MLP-based feature importance with established downstream tools. The core idea of using case-deletion in a neural network context is not entirely novel but is applied in a systematic way. However, the evidence provided is insufficient to fully establish the claimed advantages over existing methods. The sensitivity improvements over SCENIC are reported without statistical testing, the clustering comparisons lack rigorous quantitative support, and several methodological details are underspecified. The clinical relevance analysis is suggestive but limited in scope. The manuscript would benefit from more comprehensive benchmarking, clearer statistical reporting, and additional technical details.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, single-cell transcriptomics analysis, and method development for regulatory genomics. The method addresses a recognized challenge in capturing nonlinear regulatory relationships and handling rare cell populations, which are of interest to researchers studying cell type diversity, development, and tumor heterogeneity. The integration with existing tools (RcisTarget, AUCell) makes it potentially accessible to the SCENIC user community.

- **Major strengths**
  1. The methodological pipeline is clearly structured and integrates well-established components (MLP, RcisTarget, AUCell) in a coherent workflow.
  2. The focus on rare cell types is a relevant and under-addressed problem in GRN inference.
  3. The use of multiple real datasets and cross-validation with ChIP-seq data provides some external validation.
  4. The survival analysis linking regulon activity to patient outcomes adds translational relevance.
  5. The code is made publicly available, supporting reproducibility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that SIGNET exhibits increased sensitivity in identifying ChIP-seq-validated regulatory interactions compared with SCENIC.
- **Evidence pointer** Results section, Figure 3C and 4C
- **Concern** The sensitivity comparison with SCENIC is presented without any statistical testing or confidence intervals. The figure descriptions indicate differences in overlap counts, but it is unclear whether these differences are significant given the variability in ChIP-seq data quality and the different numbers of predicted targets per method. The authors also note that specificity is slightly lower or comparable, but the trade-off between sensitivity and specificity is not systematically analyzed.
- **Why it matters** The central claim of the paper rests on this sensitivity advantage. Without statistical support, the reader cannot assess whether the observed differences are robust or within the range of random variation. A sensitivity-specificity trade-off analysis is essential for a fair method comparison.
- **Resolution test** Provide statistical tests (e.g., bootstrap or permutation tests) comparing sensitivity and specificity distributions across multiple datasets or cross-validation folds. Report confidence intervals for the overlap proportions. Present ROC-style or precision-recall style analyses to characterize the trade-off.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that SIGNET achieves better cell clustering performance than other methods based on five metrics (F score, CSI, PSI, ARI, NMI) and two internal validation indices (RMSSTD, MHG).
- **Evidence pointer** Results section, Figure 2B, 2D, 2F
- **Concern** The clustering comparison is described qualitatively in the text ("consistently demonstrated that SIGNET achieved the best performance") without reporting the actual metric values or any measure of variability. The choice of hierarchical clustering with average linkage for both SCENIC and SIGNET is reasonable, but the comparison with Seurat uses a different clustering approach (integrated pipeline), which may confound the comparison. The number of clusters is not specified, and it is unclear whether the same number of clusters was used across methods.
- **Why it matters** Clustering performance is a key claimed advantage, but the evidence as presented is not quantitatively assessable. Without metric values and variability estimates, the reader cannot evaluate the magnitude of the improvement or its practical significance.
- **Resolution test** Report the actual metric values for all methods and datasets in a table. Include standard deviations or confidence intervals from multiple runs. Specify the number of clusters used and justify the choice. Consider using the same clustering algorithm for all methods to isolate the effect of the input representation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The description of the bagging procedure and its role in the method.
- **Evidence pointer** Methods section, "Prediction of the relationship between genes"
- **Concern** The term "bagging" appears in the title and abstract, but the methods section does not clearly describe how bagging is implemented. The text mentions bootstrapping to balance positive and negative cases, but this appears to be a resampling of the training data rather than ensemble bagging in the traditional sense. It is unclear whether multiple MLP models are trained on different bootstrap samples and aggregated, or whether a single model is trained on a resampled dataset. The number of models in the ensemble, if any, is not specified.
- **Why it matters** The title and abstract emphasize bagging as a key feature of the method. If the implementation differs from standard bagging, this should be clarified. The ensemble strategy affects the method's variance reduction properties and its robustness claims.
- **Resolution test** Clearly describe the bagging procedure, including the number of models, the resampling strategy, and the aggregation method. If the bootstrap is only used for class balancing, rename the approach to avoid confusion with ensemble bagging.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The claim that SIGNET is a useful tool for identifying important regulatory modules driving various biological processes.
- **Evidence pointer** Results section, Figure 3A, 3D, 4A, 4D
- **Concern** The biological validation is largely based on literature concordance for a small number of selected regulons (GATA1, GATA2, AP-1, c-MYC, MYB, etc.). While these are reasonable examples, the analysis does not include a systematic evaluation of the biological relevance of the full set of predicted regulons. The survival analysis is limited to a single cancer type and uses a single normalization approach.
- **Why it matters** The claim of biological utility extends beyond the specific examples shown. A more systematic evaluation, such as enrichment analysis across all predicted regulons or validation in additional datasets, would strengthen the case.
- **Resolution test** Perform gene set enrichment analysis on the full set of predicted regulons to assess enrichment for known biological processes and pathways. Extend the survival analysis to additional cancer types or independent cohorts.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The description of the data preprocessing and feature selection steps.
- **Evidence pointer** Methods section, "Data preprocessing"
- **Concern** The preprocessing steps are described at a high level, but several details are missing. The criteria for selecting 5000-7000 highly variable genes are not specified. The Hodges-Lehmann estimator is used for binarization, but the rationale for this choice over other binarization methods is not discussed. The handling of dropout events and technical noise is not addressed.
- **Why it matters** Preprocessing choices can significantly affect downstream results. Without clear specifications, the method cannot be accurately reproduced or compared with alternatives.
- **Resolution test** Provide detailed preprocessing parameters, including the exact criteria for gene filtering, the software versions and parameters used, and the treatment of dropout events. Justify the choice of the Hodges-Lehmann estimator for binarization.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that SIGNET is "more effective for various downstream analyses" but does not specify which analyses or provide quantitative support.
- **Required correction** Specify the downstream analyses and provide a brief quantitative summary of the improvements.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 1
- **Issue** The introduction lists three challenges in GRN inference but does not clearly map these challenges to the specific design choices in SIGNET.
- **Required correction** Explicitly connect each challenge to the corresponding component of the SIGNET pipeline.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Screening of potential coexpression gene pairs"
- **Evidence pointer** Methods section, equation 8
- **Issue** The accuracy metric ACC_mn is defined as 1 minus the L0 norm of the difference between predicted and true labels, normalized by K. This is equivalent to accuracy, but the notation is unnecessarily complex.
- **Required correction** Simplify the notation and define ACC_mn as the proportion of correctly predicted labels.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "SIGNET identifies cell-specific transcription factors"
- **Evidence pointer** Results section, Figure 3E
- **Issue** The statement that GATA1 and GATA2 regulatory networks exhibited a high degree of overlap is not quantified.
- **Required correction** Report the overlap statistic (e.g., Jaccard index or percentage of shared targets).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Survival analysis of clinical data"
- **Evidence pointer** Methods section, "Survival analysis of clinical data"
- **Issue** The survival analysis uses GEPIA2, but the specific parameters (e.g., cutoff for high/low expression groups, covariates adjusted) are not described.
- **Required correction** Provide the GEPIA2 parameters and any statistical adjustments used.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 2
- **Issue** The discussion attributes the method's performance to three aspects but does not provide supporting evidence for each attribution.
- **Required correction** Reference specific results or analyses that support each attribution.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The ChIP-seq datasets are referenced via a general link to ChIP-Atlas, but the specific datasets used are not listed.
- **Required correction** List the specific ChIP-seq dataset identifiers used for validation.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The statement about adjusting the motif enrichment score threshold is vague regarding how users should choose the threshold.
- **Required correction** Provide guidance or a default threshold and describe the sensitivity of results to this parameter.

## Risk / unsupported claims
- The claim of "increased sensitivity" over SCENIC is not statistically supported.
- The claim of "more effective for various downstream analyses" in the abstract is not quantified.
- The claim that SIGNET is "more robust to background noise" is based on a single downsampling experiment without statistical analysis.
- The biological significance claims are based on selected examples and literature concordance, not systematic evaluation.
- The performance on the large multi-organ dataset (GSE109774) is mentioned only briefly in the discussion without detailed results.
- The computational efficiency of the method is not assessed or compared with alternatives.
- The choice of the Hodges-Lehmann estimator for binarization is not justified or compared with alternatives.