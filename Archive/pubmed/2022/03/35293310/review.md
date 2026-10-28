## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure/table legends
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors propose DeepCAGE, a deep learning framework integrating DNA sequence, TF binding scores, and TF expression data to predict chromatin accessibility across 55 cell types, with applications to variant prioritization in WGS data
- **Visible evidence base** Main text figures (Figures 1-6), supplementary figure legends (S1-S5), supplementary table legends (S1-S7), and methodological descriptions
- **Missing materials affecting confidence** Actual figure images, numerical results tables, hyperparameter values, code implementation details, and full supplementary data are not available for direct verification

## Reviewer
- **Overall assessment** The manuscript presents a reasonable computational approach for integrating multiple data modalities in chromatin accessibility prediction. The methodological framework is coherent and the authors address an important problem in functional genomics. However, several technical aspects require clarification and additional validation before the claims can be fully assessed. The performance improvements over baselines, while reported, cannot be independently verified from the provided materials. The interpretability analyses are interesting but their biological significance requires stronger evidence.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those developing deep learning methods for functional element annotation. Researchers studying transcription factor biology and chromatin dynamics would also find the interpretability analyses relevant. The variant prioritization application may interest statistical geneticists working on complex trait mapping.

- **Major strengths** The integration of TF binding scores and expression data with sequence information is biologically motivated and represents a thoughtful departure from purely sequence-based approaches. The cell-type-level cross-validation design is appropriate for assessing generalization. The gradient-based interpretability strategy provides a mechanism for biological validation of learned features. The application to WGS variant prioritization demonstrates practical utility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim DeepCAGE achieves state-of-the-art performance in both classification and regression of chromatin accessibility signals, with mean cell-type-wise auPR of 0.418 for known accessible loci compared to 0.166-0.319 for baselines.
- **Evidence pointer** Figure 2A, Figure 3B-C, Results section "DeepCAGE accurately predicts binary chromatin accessibility statuses" and "DeepCAGE recovers a continuous degree of chromatin accessibility"
- **Concern** The reported performance metrics cannot be verified from the provided materials. No confidence intervals, statistical significance tests, or per-cell-type variability measures are reported for the classification results. For regression, only a single P value is provided for one comparison. The baseline comparisons may be confounded by differences in training data, hyperparameter tuning, or evaluation protocols. Additionally, the auPR values reported (0.418 for known loci) seem modest in absolute terms, and the practical significance of these improvements requires clarification.
- **Why it matters** The central claim of the manuscript is that DeepCAGE outperforms existing methods. Without rigorous statistical assessment and transparent reporting of experimental conditions, this claim cannot be evaluated. Reproducibility of the reported performance is essential for the method to be adopted by the community.
- **Resolution test** Provide per-cell-type performance distributions, confidence intervals, and appropriate statistical tests for all comparisons. Report exact experimental conditions including training/validation splits, hyperparameter optimization procedures, and any data preprocessing steps that differ between methods. Make evaluation code and trained models available to allow independent verification.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that DeepCAGE incorporates binding statuses of TFs by scanning input sequences with HOCOMOCO motifs using HOMER and selecting the maximum score for each of 402 TFs.
- **Evidence pointer** Methods section "Overview of DeepCAGE", Figure 1
- **Concern** The description of how binding scores are computed and integrated is insufficiently detailed. The authors do not specify the HOMER parameters used, how motif scanning is performed relative to the 1000 bp input window, whether scores are normalized across TFs, or how the element-wise product with expression data is justified. The choice of 402 TFs and the HOCOMOCO database version are not justified. The potential redundancy between motif scores and sequence features learned by the convolutional layers is not addressed.
- **Why it matters** The binding score integration is a key novelty of the method. If the procedure is not precisely specified, the method cannot be reproduced or compared fairly with alternatives. The biological rationale for the element-wise product operation requires explicit justification.
- **Resolution test** Provide complete details of the motif scanning procedure including software version, parameters, score thresholds, and post-processing steps. Justify the choice of 402 TFs and the multiplicative integration scheme. Discuss potential redundancy between motif features and learned sequence features, and provide ablation results that isolate the contribution of binding scores.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that GIS successfully prioritizes cell type-related TFs, using K562 and TP53 as an example, and that top-ranked TFs are related to leukemia functions.
- **Evidence pointer** Figure 4A-C, Results section "GIS helps prioritize cell type-related TFs"
- **Concern** The GIS analysis is demonstrated for a single gene (TP53) in a single cell type (K562). The authors do not provide a systematic evaluation of whether GIS-prioritized TFs are enriched for known cell type-specific regulators across multiple loci and cell types. The GO enrichment analysis is mentioned but no statistical details or multiple testing corrections are reported. The relationship between GIS values and actual TF binding or regulatory function is not validated experimentally or against independent datasets.
- **Why it matters** The interpretability of the model is presented as a major advantage. A single anecdotal example is insufficient to establish that GIS provides reliable biological insights. Without systematic validation, the claimed utility for understanding regulatory mechanisms remains speculative.
- **Resolution test** Perform GIS analysis across multiple genes and cell types with known regulatory programs. Compare GIS-prioritized TFs against experimentally validated regulators using enrichment analyses with appropriate statistical controls. Validate a subset of predictions against independent ChIP-seq or perturbation data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that DeepCAGE successfully prioritizes putative deleterious variants underlying human complex traits, with top-ranked variants explaining 2.11% of height variance compared to 2.49% for all variants.
- **Evidence pointer** Figure 6A-D, Results section "DeepCAGE prioritizes putative deleterious variants in personal genomes"
- **Concern** The variant prioritization analysis has several potential issues. The use of 3290 genome-wide significant height-associated SNPs as "risk SNPs" may introduce selection bias. The definition of risk regions as 200 kb windows centered on these SNPs is arbitrary. The linear regression model with l1 penalty for height prediction uses only variant scores as predictors, which may not account for linkage disequilibrium structure or effect directions. The comparison between top-ranked and bottom-ranked variants is not accompanied by appropriate statistical tests. The claim that top 10% variants "contained most information" is not formally demonstrated.
- **Why it matters** The application to WGS data is presented as a practical demonstration of the method's utility. If the analysis has methodological flaws, the conclusions about variant prioritization may not be reliable.
- **Resolution test** Provide details on how LD is accounted for, justify the choice of risk regions, report statistical significance of differences between top and bottom ranked variants, and compare against appropriate null models or alternative prioritization methods.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the DenseNet architecture contributes to improved performance, with DenseNet leading to 6.4% improvement over ResNet in median cell-type-wise PCC.
- **Evidence pointer** Supplementary Figure S4, Results section "Model ablation analysis of DeepCAGE"
- **Concern** The comparison between DenseNet and ResNet is described in a supplementary figure legend but the experimental details are incomplete. The authors state the ResNet has "the same number of layers as the number of dense blocks" which suggests a potentially unfair comparison, as DenseNet layers within dense blocks are not equivalent to ResNet layers. The hyperparameter optimization for the ResNet variant is not described. The statistical significance of the 6.4% improvement is not reported.
- **Why it matters** The choice of architecture is presented as a methodological contribution. An unfair or incomplete comparison does not establish the advantage of DenseNet over ResNet for this task.
- **Resolution test** Provide a fair comparison with matched model capacity, training procedures, and hyperparameter optimization for both architectures. Report statistical significance and effect sizes across multiple random seeds.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Methods section "Data processing", Code availability section
- **Issue** The authors state that DNase-seq and RNA-seq data were downloaded from ENCODE and GTEx, but specific accession numbers, data versions, and processing pipelines are not provided. The code repository link is given but the manuscript does not specify which scripts correspond to which analyses.
- **Required correction** Provide a data availability statement with specific accession identifiers and versions. Clearly map code files to manuscript figures and analyses.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Method description
- **Evidence pointer** Methods section "Model evaluation"
- **Issue** The definition of "putative known accessible loci" and "putative novel accessible loci" is described in the supplementary figure legend but the main text does not clearly explain the distinction. The relationship between these definitions and the training/testing split is unclear.
- **Required correction** Move the definition of known and novel loci to the main text methods section and clarify how these definitions affect the evaluation protocol.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Performance comparison
- **Evidence pointer** Figure 2A, Figure 3B-C
- **Issue** The manuscript reports mean auPR and PCC values but does not report variability across cross-validation folds or cell types. The statistical test for regression comparison is mentioned but the test for classification comparisons is not described.
- **Required correction** Report standard deviations or interquartile ranges for all performance metrics. Describe the statistical tests used for all comparisons, including classification results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** Motif analysis
- **Evidence pointer** Methods section "Motif analysis", Figure 5
- **Issue** The description of how PWM motifs are derived from convolutional kernel weights is incomplete. The threshold for considering a subsequence "activated" is described but the relationship between the learned motifs and the input HOCOMOCO motifs is not discussed.
- **Required correction** Clarify the motif extraction procedure and discuss whether the learned motifs are distinct from or redundant with the input motif database.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations focuses on potential extensions but does not address potential biases in the training data, the choice of 1000 bp window size, or the generalizability to non-ENCODE cell types.
- **Required correction** Add a paragraph discussing potential limitations of the current approach, including data biases and parameter choices.

- **Technical failings that need to be addressed before the case is established** R1-M1 (performance verification), R1-M2 (binding score methodology), R1-M3 (GIS validation), R1-M4 (variant prioritization methodology)

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The integration of TF binding scores with sequence and expression data is a reasonable extension of existing approaches, but the individual components (sequence-based deep learning, expression integration, motif analysis) have been explored previously.
  - Scientific importance: Moderate. Chromatin accessibility prediction is an active area, and improved methods with interpretability features would be of interest to the community. However, the incremental improvement over existing methods needs to be clearly established.
  - Interdisciplinary readership: Limited. The manuscript is primarily of interest to computational biologists and bioinformaticians. The biological insights from GIS analysis could broaden appeal but require stronger validation.
  - Technical soundness: The overall framework is reasonable, but several methodological details are insufficiently specified and the performance claims lack rigorous statistical assessment.
  - Readability for nonspecialists: The manuscript is generally well-written and the figures are clearly described. However, some methodological details assume familiarity with deep learning architectures and genomics terminology.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important problem and presents a coherent framework, but the central performance claims require rigorous verification, the binding score methodology needs complete specification, and the interpretability analyses require systematic validation. These issues are addressable but currently prevent full assessment of the method's contributions.