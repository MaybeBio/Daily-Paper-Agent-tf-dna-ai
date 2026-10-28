## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and general interest assessment based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors present Bag-of-Motifs (BOM), a computational framework representing distal cis-regulatory elements as unordered counts of transcription factor motifs, combined with gradient-boosted trees, to predict cell-type-specific enhancers across mouse, human, zebrafish, and Arabidopsis datasets. They claim BOM outperforms deep-learning models, that synthetic enhancers built from top predictive motifs drive cell-type-specific expression, and that motif-based models detect functional conservation beyond sequence alignment.
- **Visible evidence base** Main text figures 1-6 (as referenced), supplementary figures 1-16, supplementary tables 1-25, supplementary datasets 1-3, methods section, and source data statement
- **Missing materials affecting confidence** Actual figure images, supplementary tables and datasets, source data files, and code availability statements were not provided. Experimental details for the luciferase assay are present but raw data are not shown. Statistical details for some comparisons are incomplete.

## Reviewer

- **Overall assessment** This manuscript presents a conceptually simple yet potentially powerful framework for predicting cell-type-specific regulatory elements from motif counts alone. The cross-species validation and the experimental confirmation using synthetic enhancers are notable strengths. However, several technical concerns regarding benchmarking fairness, statistical rigor, and the interpretation of the cross-species results need to be addressed before the central claims can be fully accepted. The work is likely of interest to the gene regulation and computational biology communities, but the current evidence does not fully establish all claims made.

- **Who would be interested in the results, and why** Researchers studying cis-regulatory element function, transcription factor biology, and cell-type-specific gene regulation would find this work relevant. Computational biologists developing interpretable models for regulatory genomics would also be interested, as BOM offers a transparent alternative to deep-learning approaches. The cross-species applicability and the experimental validation of predicted motifs would appeal to those working on enhancer design and synthetic biology.

- **Major strengths**
  1. The bag-of-motifs representation is elegantly simple and provides direct interpretability, addressing a key limitation of deep-learning models.
  2. The validation across multiple species (mouse, human, zebrafish, Arabidopsis) and diverse datasets strengthens the generalizability claim.
  3. The experimental validation using synthetic enhancers is a significant step beyond purely computational benchmarking.
  4. The cross-species prediction results, particularly the finding that motif-based models work even when sequences cannot be aligned, are conceptually interesting.
  5. The use of SHAP values for local interpretability provides a practical tool for hypothesis generation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of benchmarking
- **Claim pointer** "BOM outperforms more complex deep-learning models while using fewer parameters" (Abstract) and "BOM achieved a mean auPR of 0.99 and an MCC of 0.93, outperforming LS-GKM, DNABERT, and Enformer by 17.2%, 55.1%, and 10.3% in auPR, and by 77.5%, 211.9%, and 33.4% in MCC, respectively" (Results)
- **Evidence pointer** Figure 2, Supplementary Table 3, Methods section on benchmarking
- **Concern** The benchmarking comparison against deep-learning models raises several questions. First, the input representation differs fundamentally: BOM uses motif counts while deep models use one-hot encoded sequences. This is appropriate, but the comparison may not be entirely fair if the deep models were not given sufficient training data or epochs. The manuscript states DNABERT and Enformer were fine-tuned with hyperparameter optimization, but details on the computational resources, training time, and whether the deep models were trained from scratch or fine-tuned from pretrained weights are incomplete. For Enformer, which is designed for long-range context, restricting input to 500 bp may disadvantage it. The authors note they "made modifications to Enformer to enhance its ability for our cell-type classification" but the nature and extent of these modifications are not fully described. Without a clear description of the baseline models' configurations and training procedures, the claim of outperformance is difficult to evaluate rigorously.
- **Why it matters** The central claim of the manuscript is that a simple motif-count model outperforms complex deep-learning approaches. If the comparison is not conducted under fair and well-documented conditions, this claim is not established, which would substantially weaken the paper's contribution.
- **Resolution test** Provide complete details of the deep-learning model architectures, training procedures, hyperparameter search spaces, and computational budgets. Ideally, include a comparison where deep models are given the same amount of training data and computational resources. Also clarify what modifications were made to Enformer and justify why these modifications are appropriate. If possible, include a learning curve analysis showing performance as a function of training set size for all models.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of experimental validation
- **Claim pointer** "SREs containing HepG2 motifs consistently exhibited higher reporter expression in HepG2 cells than in GM12878 cells, whereas SREs with GM12878 motifs showed the opposite pattern" (Results, Figure 6)
- **Evidence pointer** Figure 6, Methods section on activity testing
- **Concern** The experimental validation using synthetic enhancers is a key strength, but the statistical analysis appears incomplete. The manuscript reports p-values from two-tailed t-tests, but it is unclear how many biological replicates were performed. The text states "Two replicates of the assays were performed," which is insufficient for a robust statistical comparison. Additionally, the figure legend mentions normalization to transfection efficiency and template activity, but the exact normalization procedure is not fully described. The variability among the five SREs within each cell type is shown in the boxplot, but it is not clear whether the comparison is between individual SREs or pooled across SREs. A mixed-effects model accounting for SRE identity as a random effect would be more appropriate than simple t-tests.
- **Why it matters** The experimental validation is the most direct evidence that BOM-identified motifs confer cell-type specificity. If the statistical analysis is underpowered or inappropriate, the conclusion that these motifs drive cell-type-specific expression is not robustly supported.
- **Resolution test** Clearly state the number of biological and technical replicates. Use appropriate statistical tests that account for the hierarchical structure of the data (e.g., mixed-effects models with SRE as a random effect). Report effect sizes and confidence intervals. If only two replicates were performed, additional replicates are needed to support the claim.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for cross-species conservation claim
- **Claim pointer** "motif-based models detect functional conservation beyond conventional sequence alignment" (Discussion) and "The mouse models correctly identified 64.5% of human cardiomyocyte and 62.9% of human erythroblast CREs" (Results, Figure 4)
- **Evidence pointer** Figure 4, Supplementary Tables 18-22, Methods section on cross-species analyses
- **Concern** The cross-species prediction results are interesting, but the interpretation requires careful scrutiny. The claim that motif-based models detect conservation "beyond sequence alignment" is based on the observation that many correctly predicted CREs lack detectable alignment. However, this could also be explained by the fact that the motif vocabulary is shared across species even when individual motif instances are not orthologous. The analysis does not appear to control for the possibility that the models are simply detecting general enhancer-like properties rather than cell-type-specific conservation. Additionally, the threshold for "correctly predicted" is not clearly defined, and the baseline performance (e.g., what would be expected by chance given the class balance) is not reported. The manuscript also does not compare against a sequence-alignment-based approach directly, which would strengthen the claim.
- **Why it matters** The claim that motif-based models capture functional conservation beyond sequence alignment is a significant conceptual contribution. If this claim is not rigorously supported, the broader significance of the work is diminished.
- **Resolution test** Provide a direct comparison between BOM predictions and a sequence-alignment-based conservation approach (e.g., phastCons or PhyloP scores) on the same datasets. Report the expected performance of a null model that uses the same motif vocabulary but random assignment of cell-type labels. Clarify the definition of "correctly predicted" and report sensitivity and specificity at multiple thresholds.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and dataset representativeness
- **Claim pointer** "BOM maintained high accuracy across species, cell types and disease states, demonstrating that a simple motif-count representation can capture context-specific cis-regulatory grammar across a broad phylogenetic range" (Results)
- **Evidence pointer** Figure 3, Supplementary Tables 14-17
- **Concern** While the cross-species results are impressive, the datasets used vary substantially in size and quality. For example, the Arabidopsis dataset has fewer than 300 CREs per class, which is quite small for training a robust classifier. The Drosophila analysis used only 15.6% of the data used to train DeepSTARR, and the performance was notably lower for developmental enhancers (Pearson r = 0.42 vs. 0.68 for DeepSTARR). The manuscript acknowledges this but does not fully explore why BOM underperforms in this context. The claim of "broad phylogenetic range" is supported by the species diversity, but the depth of validation in each species is uneven.
- **Why it matters** The generalizability claim is central to the paper's impact. If the model performs well in some species but poorly in others, the conditions under which the motif-count representation is sufficient need to be more clearly delineated.
- **Resolution test** Provide a more detailed analysis of the conditions under which BOM performs well versus poorly. For the Drosophila developmental enhancers, investigate whether the underperformance is due to insufficient training data, the complexity of developmental enhancer grammar, or limitations of the motif representation. Consider including additional species or datasets to strengthen the generalizability claim.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Motif annotation and threshold selection
- **Evidence pointer** Methods section on motif database and scoring
- **Issue** The choice of q-value threshold (≤0.5) for motif annotation is quite lenient, and the manuscript notes that "about 83% of the nucleotides in each CRE were annotated as motifs" at this threshold. This raises the question of whether the model is essentially using a near-complete sequence representation rather than a sparse motif vocabulary. The sensitivity of the results to this threshold is not explored.
- **Required correction** Provide a sensitivity analysis showing model performance as a function of the q-value threshold. Justify the choice of 0.5 and discuss whether the results are robust to this parameter.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretability of SHAP values
- **Affected element** Figure 5, Methods section on calculating motif importance
- **Evidence pointer** Figure 5d-h
- **Issue** The SHAP analysis identifies important motifs, but the link between motif importance and transcription factor expression is only shown for a few examples. The manuscript states that "motifs with high importance typically corresponded to lineage-specific transcription factors," but the quantitative relationship between SHAP values and expression is not systematically evaluated.
- **Required correction** Provide a systematic analysis correlating SHAP importance with transcription factor expression across all cell types, with appropriate statistical tests. This would strengthen the claim that BOM identifies biologically meaningful regulators.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reporting of negative results
- **Affected element** Pleiotropic element classification
- **Evidence pointer** Figure 1f
- **Issue** The manuscript reports that performance on pleiotropic elements dropped markedly (mean auPR = 0.44), but this result is not discussed in depth. Understanding why the model fails on these elements could provide insights into the limitations of the motif-count representation.
- **Required correction** Expand the discussion of pleiotropic element performance, including potential reasons for the drop and whether alternative representations could address this limitation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Code and data availability
- **Affected element** Methods section
- **Evidence pointer** Not specified
- **Issue** The manuscript does not state whether the BOM software and analysis code are publicly available, nor does it provide a data availability statement beyond the source data file.
- **Required correction** Add a clear code and data availability statement, including a repository link for the BOM implementation and any analysis scripts.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 1-6
- **Evidence pointer** Figure legends
- **Issue** The figure legends are detailed, but the actual figures were not available for review. Some figure panels (e.g., Figure 3f) appear to show individual data points, but the axis labels and units are not fully described in the legend.
- **Required correction** Ensure all figure panels have clear axis labels, units, and legends. Consider adding a schematic overview of the BOM framework in Figure 1 for readers unfamiliar with the approach.

## Risk / unsupported claims
1. The claim that BOM "outperforms more complex deep-learning models" is not fully established due to incomplete details on benchmarking fairness and model configurations.
2. The claim that "motif-based models detect functional conservation beyond conventional sequence alignment" is not rigorously supported without a direct comparison to alignment-based conservation methods.
3. The experimental validation with synthetic enhancers is based on only two replicates, which is insufficient to robustly support the claim that BOM-identified motifs drive cell-type-specific expression.
4. The statement that "BOM maintained high accuracy across species" is unevenly supported, with notably weaker performance on Drosophila developmental enhancers and small sample sizes in Arabidopsis.
5. The claim that "a highly predictive sequence code at distal regulatory regions" exists is supported by the results, but the manuscript does not fully explore the conditions under which this code is sufficient versus when additional information (e.g., chromatin context) is needed.
6. The performance on pleiotropic elements (mean auPR = 0.44) is reported but not adequately explained, leaving the scope of BOM's applicability unclear.