## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and availability statements. Figures and supplementary materials referenced but not provided.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and interpretation of results as presented in the supplied text. No assessment of code functionality or web application performance beyond stated claims.
- **Shared manuscript claim summary** The authors present DNABERT-Enhancer, a fine-tuned DNABERT model for predicting enhancer regions from DNA sequence. They report high classification accuracy on curated ENCODE cCRE datasets, genome-wide enhancer prediction covering 26.65% of the human genome, and identification of candidate loss-of-function and gain-of-function variants affecting enhancer activity and transcription factor binding.
- **Visible evidence base** Main text tables and figures referenced: Table 1 (cell-type-specific model performance), Table 2 (baseline comparisons), Table 3 (NT comparison), Fig. 1 (model architecture), Fig. 2 (dataset characteristics and performance), Fig. 3 (comparison plots), Fig. 4 (genome-wide validation), Fig. 5 (variant examples). Supplementary tables and figures referenced but not visible.
- **Missing materials affecting confidence** All supplementary figures and tables, detailed methods for variant effect prediction thresholds, permutation testing procedures, hyperparameter search details, and the full benchmark dataset composition. Without these, several quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a technically competent application of a pre-trained genomic language model to enhancer prediction, with reasonable performance metrics and a useful resource for the community. The core methodological contribution is incremental, building directly on the authors' prior DNABERT work, and the novelty relative to existing enhancer prediction tools is modest. The variant effect prediction section is potentially the most valuable contribution, but the validation is thin and relies heavily on overlap with biased databases. The writing is clear and the resource availability is commendable. However, several claims regarding biological interpretation and clinical relevance are overstated relative to the evidence presented. The manuscript would benefit from stronger validation of the variant effect predictions and a more careful discussion of limitations.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those developing or applying deep learning methods for noncoding variant interpretation. Researchers studying enhancer biology and seeking sequence-based prediction tools may also find the resource useful. The variant prioritization catalog could be of interest to those working on noncoding disease variants, though the clinical utility remains to be demonstrated.

- **Major strengths**
  1. The use of a pre-trained language model with attention mechanisms is a sensible and current approach for capturing sequence context in regulatory genomics.
  2. The benchmark dataset curation from ENCODE cCREs is well described and the two-length design (201 and 350 bp) is thoughtful.
  3. The comparison against multiple baseline classifiers and two recent enhancer prediction methods provides useful context for performance claims.
  4. The genome-wide application and public availability of predictions through a web application and archived models is a valuable community resource.
  5. The cell-type-specific modeling experiments address an important question about the generality versus specificity of enhancer sequence features.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of variant effect predictions
- **Claim pointer** "By applying a 5% empirical false discovery rate (FDR) threshold, we identified 2681 LOF SNPs (LOR > 2.65) and 1917 GOF SNPs (LOR < −1.77) that, respectively, altered the activity of 1623 ENCODE SCREEN enhancers (affecting 301 TFs) and 1247 enhancers between reference and alternative alleles, effectively converting enhancers to non-enhancers or vice versa."
- **Evidence pointer** Section 3.8; Supplementary Methods referenced but not provided
- **Concern** The threshold values for LOR (log odds ratio) and the FDR procedure are stated but the derivation is not visible. The claim that variants "effectively convert enhancers to non-enhancers or vice versa" is strong and implies a binary functional switch, but the underlying probability changes are not reported. Without the supplementary methods detailing how LOR was computed, how the FDR was calibrated, and what the distribution of effect sizes looks like, this central claim cannot be evaluated. Additionally, the validation via overlap with ClinVar, GWAS, and eQTL databases is acknowledged by the authors as biased, but the small number of validated variants (8 LOF, 6 GOF) raises questions about precision of the predictions.
- **Why it matters** The variant effect prediction is presented as a key application and potential clinical resource. If the thresholds or FDR procedure are not robust, the catalog of 4,598 prioritized variants could be substantially enriched for false positives, misleading downstream users.
- **Resolution test** Provide the supplementary methods detailing LOR computation, FDR calibration, and show the distribution of effect sizes. Include a sensitivity analysis demonstrating that the prioritized variant lists are stable to reasonable changes in thresholds. Report precision estimates based on the overlap with external databases rather than raw counts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Validation of genome-wide predictions
- **Claim pointer** "Genome-wide application identified 1,684,595 enhancer regions covering 26.65% of the human genome."
- **Evidence pointer** Section 3.7; Fig. 4 and supplementary tables referenced but not provided
- **Concern** The genome-wide prediction covers over a quarter of the human genome, which is a strikingly high fraction. The authors report overlap with ENCODE SCREEN (82.05% of SCREEN recovered) and other databases, but the biological plausibility of 26.65% of the genome functioning as enhancers is not discussed. The merging procedure tolerates "brief dips" in probability, which could substantially inflate region sizes. The comparison with EnhancerAtlas, which contains regions longer than 5 kb, is problematic because the model was trained on 350 bp windows and the merging procedure may create very long regions that are not directly comparable.
- **Why it matters** If the genome-wide predictions are substantially over-inclusive, the resource could mislead users into investigating large numbers of false positive regions. The 26.65% figure is a headline result that invites scrutiny.
- **Resolution test** Report the distribution of predicted enhancer region lengths and the fraction of the genome covered by regions of different sizes. Provide a comparison using a stricter merging criterion or higher probability threshold to show how the genome coverage changes. Discuss the biological plausibility of the coverage figure in the context of known estimates of enhancer content in the human genome.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of cell-type-specific model results
- **Claim pointer** "The comparable performance observed across distinct cellular contexts indicates that enhancer-associated sequence determinants are robust and learnable within individual lineages."
- **Evidence pointer** Section 3.3; Table 1
- **Concern** The authors interpret similar performance across cell types as evidence that enhancer sequence features are largely shared. However, an alternative explanation is that the model is not sensitive enough to detect cell-type-specific features, or that the training data for each cell type is too small or too similar. The four cell types chosen (two brain, two breast) may not be sufficiently distinct to reveal context-dependent grammar. The authors do not report cross-cell-type transfer experiments, which would be the appropriate test: train on one cell type and evaluate on another, comparing to within-cell-type performance.
- **Why it matters** The interpretation that enhancer sequences are mostly conserved across cell types has implications for the generalizability of the model and for understanding enhancer biology. If the conclusion is an artifact of insufficient sensitivity, it could mislead the field.
- **Resolution test** Perform cross-cell-type training and evaluation. If performance drops substantially when transferring between lineages, this would indicate cell-type-specific features that the current analysis misses. Report the overlap of predicted enhancers between cell types at the sequence level, not just aggregate accuracy.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with existing methods
- **Claim pointer** "DNABERT-Enhancer outperforms recent enhancer prediction methods" and "DNABERT-Enhancer achieved superior performance compared to all benchmarks"
- **Evidence pointer** Sections 3.4 and 3.5; Tables 2 and 3
- **Concern** The comparison with iEnhancer-ELM, iEnhancer-DCLA, and iEnhancer-ECNN uses their default parameters, which may not be optimal for this dataset. More importantly, the comparison with the Nucleotide Transformer (NT) is limited to a single model size (500M) and a single pre-training approach. The claim that overlapping k-mer tokenization is responsible for the performance advantage is not directly tested; it is an inference from comparing two models that differ in many ways beyond tokenization. The authors do not report whether the performance differences are statistically significant.
- **Why it matters** The performance claims are central to the paper's contribution. If the comparisons are not fair or the differences are not significant, the claimed advantage over existing methods is not established.
- **Resolution test** Report confidence intervals or statistical tests for the performance differences. Include a comparison with NT models of different sizes to test whether the advantage is robust. Consider an ablation study that varies tokenization strategy within the same model architecture to directly test the tokenization hypothesis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of reporting
- **Affected element** Dataset composition
- **Evidence pointer** Section 2.1
- **Issue** The description of negative set construction is vague. The text states that negatives were sampled from non-enhancer regions while excluding annotated enhancers, but does not specify whether other regulatory elements (promoters, insulators, etc.) were excluded, or how the genomic background was matched for GC content, repeat content, or other confounders.
- **Required correction** Provide a detailed description of negative set construction, including any filtering criteria and matching procedures. Report the genomic distribution of negatives relative to positives.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Hyperparameter details
- **Evidence pointer** Section 2.2.2
- **Issue** The hyperparameter search ranges are not reported. The text mentions learning rates, warm-up steps, and weight decay values, but not batch size, number of epochs, or the selection criteria for the final model.
- **Required correction** Report all hyperparameters and the model selection procedure in the main text or supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Permutation testing
- **Evidence pointer** Section 3.7; Supplementary Methods referenced
- **Issue** The permutation-based significance testing for overlaps with external databases is described only by reference to supplementary materials. The number of permutations, the null model, and the resulting p-values are not visible.
- **Required correction** Summarize the permutation testing procedure and report the resulting significance values in the main text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of attention
- **Affected element** Attention analysis
- **Evidence pointer** Section 3.8; Fig. 5
- **Issue** The claim that "DNABERT consistently shows highest attention at/around the variants of interest" is based on two examples. This is anecdotal and does not establish a general pattern. No systematic analysis of attention across the full set of prioritized variants is presented.
- **Required correction** Either provide a systematic analysis of attention patterns across all prioritized variants or temper the claim to reflect the anecdotal nature of the evidence.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "De novo enhancers"
- **Evidence pointer** Abstract and Section 3.8
- **Issue** The term "de novo enhancers" is used to describe regions that become enhancer-like upon variant substitution. This is potentially confusing, as "de novo" in genomics typically refers to sequences that arise anew in a genome, not sequences that acquire a new function through mutation. The authors may mean "cryptic enhancers" or "neo-enhancers."
- **Required correction** Clarify the terminology or use a more standard term such as "cryptic enhancers" or "acquired enhancer activity."

- **Technical failings that need to be addressed before the case is established**
  1. The variant effect prediction methodology (LOR computation, FDR calibration) is not fully described in the visible text and must be provided for evaluation (R1-M1).
  2. The genome-wide prediction coverage of 26.65% requires a more detailed analysis of region length distribution and a discussion of biological plausibility (R1-M2).
  3. The cell-type-specific analysis lacks cross-cell-type transfer experiments to support the claim of conserved enhancer features (R1-M3).
  4. The comparison with NT and other methods lacks statistical significance testing and a direct test of the tokenization hypothesis (R1-M4).

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The application of DNABERT to enhancer prediction is a natural extension of prior work by the same group and others. The variant effect prediction component adds some novelty, but the overall approach is not conceptually new.
  - **Scientific importance**: Moderate. Enhancer prediction and noncoding variant interpretation are important problems, and the resource may be useful. However, the incremental nature of the methodological contribution limits the potential impact.
  - **Interdisciplinary readership**: Limited. The work is primarily of interest to computational biologists and bioinformaticians. The biological insights are not deep enough to attract a broad genomics audience, and the clinical relevance claims are not sufficiently validated for clinical genetics readers.
  - **Technical soundness**: The core classification results appear sound based on the reported metrics, but the variant effect prediction and genome-wide application have validation gaps that need to be addressed.
  - **Readability for nonspecialists**: The manuscript is clearly written and accessible to readers with a computational biology background. The introduction and discussion provide appropriate context. However, some methodological details are relegated to supplementary materials, which may hinder nonspecialist comprehension.

- **Recommendation posture** Supportive if technical concerns are resolved. The core classification approach is reasonable and the resource is potentially valuable. However, the variant effect prediction claims, the genome-wide coverage figure, and the interpretation of cell-type-specific results require additional analysis and clarification before the case is fully established. The manuscript would be strengthened by addressing the major concerns outlined above, particularly the methodological transparency of the variant effect predictions and a more careful discussion of the limitations of the validation approach.