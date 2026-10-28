## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary references
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present TransBind, a deep learning architecture that integrates DNA sequence embeddings with protein embeddings from a DNA-binding protein language model (ESM-DBP) via cross-attention, to improve genome-wide transcription factor binding site prediction. They report state-of-the-art performance on 690 ChIP-seq experiments across 161 TFs and 91 cell types, demonstrate motif recovery, and show label-zero-shot prediction for unseen TFs.
- **Visible evidence base** Abstract, full methods description, results tables referenced (Tables 1-9), figures referenced (Figures 1-5), supplementary notes and figures referenced
- **Missing materials affecting confidence** Actual tables and figures not provided; supplementary materials not available; baseline model prediction details not fully specified; statistical test details for pairwise comparisons not fully described

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely problem in regulatory genomics: incorporating TF protein information into DNA-based binding site prediction. The proposed architecture is reasonable and the reported improvements are potentially meaningful. However, several methodological details and evaluation choices require clarification before the claims can be fully assessed. The label-zero-shot evaluation is a strength, but the moderate performance and limited scope of held-out TFs temper the generalizability claims.
- **Who would be interested in the results, and why** Computational biologists developing deep learning methods for regulatory genomics; experimental biologists studying TF binding mechanisms; researchers interested in multimodal learning approaches for genomics; those working on protein language model applications beyond structure prediction.
- **Major strengths** 1) Addresses a clear gap in existing methods by incorporating TF protein information; 2) Large-scale evaluation across 690 experiments; 3) Includes label-zero-shot prediction, an important practical capability; 4) Provides biological interpretability analysis via motif recovery; 5) Ablation studies systematically dissect component contributions.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evaluation methodology
  - **Claim pointer** The claim that TransBind outperforms state-of-the-art methods including TBiNet, EPBDXDNABERT-2, DanQ, and DeepSEA with a relative AUPR improvement of at least 11.8%
  - **Evidence pointer** Table 2, Results section "Comparison with state-of-the-art TF–DNA binding prediction methods"
  - **Concern** The baseline comparison methodology is not fully described. The authors state that all baseline models were retrained using the same Optuna-based hyperparameter optimization protocol, but the details of this retraining are not provided. For EPBDXDNABERT-2, the authors report performance "as described in the original publication" without retraining, which raises concerns about comparability. Different training data, preprocessing pipelines, and evaluation protocols between the original publication and this work could confound the comparison. Additionally, the authors note that "in all cases, the optimized configurations achieved performance lower than the originally reported results, and the original setting was used for evaluation" - this is confusing and needs clarification. If the original settings were used, what was the purpose of the hyperparameter optimization?
  - **Why it matters** The central claim of the paper is superiority over existing methods. If the baseline comparisons are not conducted under identical conditions, the reported improvements may reflect differences in training protocols rather than architectural advantages.
  - **Resolution test** Provide complete details of baseline retraining procedures, including hyperparameter search spaces, number of trials, and final configurations. Clarify the decision to use original settings when optimized configurations performed worse. For EPBDXDNABERT-2, either retrain under identical conditions or justify why this is not feasible and discuss potential biases.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical significance
  - **Claim pointer** The claim that TransBind outperformed existing methods in at least 98% of TF-cell type combinations
  - **Evidence pointer** Results section "Comparison with state-of-the-art TF–DNA binding prediction methods", Figure 4
  - **Concern** The statistical significance of the performance differences is not established. The authors report paired t-tests comparing TransBind against TBiNet across all 690 TF-cell type combinations, yielding highly significant p-values. However, the manuscript does not report whether multiple testing corrections were applied across the 690 comparisons. Additionally, the use of a paired t-test assumes normality of the differences, which may not hold for AUROC and AUPR values, particularly given the severe class imbalance described. The authors should consider non-parametric tests or bootstrap-based confidence intervals.
  - **Why it matters** Without proper statistical validation, the reported improvements could be within the range of random variation, particularly for experiments with very few positive examples.
  - **Resolution test** Report whether multiple testing corrections were applied. Consider using non-parametric tests (e.g., Wilcoxon signed-rank test) or bootstrap resampling to establish confidence intervals for the performance differences. Report the distribution of per-experiment performance differences.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Label-zero-shot evaluation
  - **Claim pointer** The claim that TransBind_zeroshot enables label-zero-shot prediction for unseen TFs with robust performance
  - **Evidence pointer** Results section "Label-zero-shot binding prediction for TF paralogs", Table 4, Table 5
  - **Concern** The label-zero-shot evaluation has several limitations. First, the held-out TFs are described as having moderate to high sequence similarity to training TFs (mean 45.86% identity to closest paralog), which means this primarily tests within-family generalization rather than true generalization to novel TF families. Second, the comparison against the TF-ID conditioned TBiNet baseline is only performed on three TFs, which is a very small sample. Third, the authors acknowledge that held-out TF sequences may have been in the ESM-DBP pretraining corpus, making this a label-zero-shot rather than sequence-zero-shot setting, but the potential impact of this on performance is not discussed. Fourth, the performance for held-out TFs (AUROC 0.575-0.628) is substantially lower than the full model, and the practical utility of this level of performance is not discussed.
  - **Why it matters** The label-zero-shot capability is presented as a key advantage of the method. If the evaluation is limited to closely related paralogs and the performance is moderate, the practical value for truly novel TFs is unclear.
  - **Resolution test** Expand the label-zero-shot evaluation to include more held-out TFs with a wider range of sequence similarity. Discuss the practical implications of the achieved performance levels. Consider evaluating on TFs from entirely different families with no close paralogs in the training set.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological interpretability
  - **Claim pointer** The claim that TransBind recovered 160 known TF binding motifs in the JASPAR database, providing biological interpretability
  - **Evidence pointer** Results section "Convolutional kernels capture general DNA patterns", Figure 5
  - **Concern** The motif recovery analysis is presented as evidence of biological interpretability, but the analysis has limitations. The authors state that 160 kernels matched known motifs with P < 0.05, but do not report how many of the 320 total kernels were matched, what fraction of the 161 TFs are represented, or whether the recovered motifs correspond to the TFs in the training set. The comparison between the discovered motifs and JASPAR references is qualitative (visual inspection of sequence logos). The authors should provide a quantitative assessment of motif similarity and discuss whether the recovered motifs are specific to the TFs being predicted or represent general DNA-binding preferences.
  - **Why it matters** The interpretability claim is important for establishing that the model learns biologically meaningful features rather than dataset-specific patterns.
  - **Resolution test** Report the number of unique TFs with recovered motifs, the distribution of motif match significance, and a quantitative comparison (e.g., using TomTom's q-values or correlation coefficients). Discuss whether the recovered motifs are specific to the TFs in the training set.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods section "Deep learning model for label-zero-shot TF–DNA binding site prediction"
  - **Evidence pointer** Methods section
  - **Issue** The description of the label-zero-shot model training is unclear. The authors state that "each DNA sequence is paired with multiple TF embeddings and vice versa" but do not specify how negative pairs are constructed. This is critical for understanding the training procedure.
  - **Required correction** Provide details on how positive and negative TF-DNA pairs are sampled during training, including the ratio of positive to negative pairs and any hard negative mining strategies.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods section "Training and evaluation"
  - **Evidence pointer** Methods section
  - **Issue** The hyperparameter optimization details are referenced to Supplementary Note S1, which is not available for review. Key hyperparameters (e.g., learning rate schedule, early stopping criteria, number of trials) should be summarized in the main text.
  - **Required correction** Include a summary of the hyperparameter search space and final selected values in the main text or a table.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data availability section
  - **Evidence pointer** Data availability section
  - **Issue** The data availability statement only mentions the software code. The processed dataset (1,903,668 bins with 690 labels) and the specific train/validation/test splits are not made available, which limits reproducibility.
  - **Required correction** Provide the processed dataset and splits, or clearly state where they can be obtained.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Writing quality
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section
  - **Issue** The discussion contains a typo: "chrommatin" should be "chromatin". Additionally, "we image it can be trained" should be "we imagine it can be trained".
  - **Required correction** Correct the typos.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Evaluation
  - **Affected element** Results section "Comparison with state-of-the-art TF–DNA binding prediction methods"
  - **Evidence pointer** Results section
  - **Issue** The authors report that TransBind outperforms baselines in 98% of cases but do not report the magnitude of improvement for the cases where it does not outperform. Understanding the failure cases could provide insight into the method's limitations.
  - **Required correction** Discuss the characteristics of the 2% of cases where TransBind does not outperform baselines.

  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Related work
  - **Affected element** Introduction
  - **Evidence pointer** Introduction section
  - **Issue** The introduction mentions BTFBS as the first to incorporate TF protein sequences but does not discuss other recent works that may have also explored protein-aware approaches. A more comprehensive review of related work would strengthen the novelty claim.
  - **Required correction** Expand the related work discussion to include recent protein-aware TF binding prediction methods and clearly articulate the differences.

- **Technical failings that need to be addressed before the case is established** R1-M1 (baseline comparison methodology), R1-M2 (statistical significance), R1-M3 (label-zero-shot evaluation scope)

## Risk / unsupported claims
- The claim of "at least 11.8% relative AUPR improvement" over state-of-the-art methods cannot be fully verified without access to the actual tables and detailed baseline comparison methodology
- The claim of recovering 160 known motifs is presented without quantitative assessment of motif similarity or specificity
- The label-zero-shot performance is described as "robust" but the AUROC values (0.575-0.628) are moderate and the evaluation is limited to closely related paralogs
- The claim that the model "recovers" motifs "providing biological interpretability" is partially supported but requires more rigorous quantitative analysis
- The statement that TransBind "enables label-zero-shot prediction for unseen TFs" is supported but the practical utility at the achieved performance levels is not discussed
- The claim that the cross-attention mechanism "reflects the biological intuition that protein structure plays an important role in determining DNA-binding specificity" is speculative and not directly tested

## Assessment against Nature-style criteria
- **Originality** Moderate. The integration of protein embeddings with DNA sequences via cross-attention is a reasonable extension of existing work, but the core idea of incorporating TF information is not entirely novel (BTFBS is acknowledged). The label-zero-shot formulation adds some originality.
- **Scientific importance** Moderate to high. Improving TF binding prediction has practical value for regulatory genomics. The label-zero-shot capability, if robust, would be important for poorly characterized TFs. However, the moderate performance in the zero-shot setting limits the immediate impact.
- **Interdisciplinary readership** Moderate. The work will appeal to computational biologists and machine learning researchers in genomics. The biological interpretability analysis broadens the appeal to experimental biologists, but the technical nature of the methods may limit accessibility.
- **Technical soundness** The architecture is reasonable and the ablation studies are thorough. However, the baseline comparison methodology and statistical validation need strengthening. The label-zero-shot evaluation is limited in scope.
- **Readability for nonspecialists** The manuscript is generally well-written and the biological motivation is clearly articulated. However, some methodological details (e.g., cross-attention mechanism, ESM-DBP embeddings) may be challenging for readers without deep learning expertise. The authors should consider adding a brief primer on these concepts.

## Recommendation posture
Supportive if technical concerns are resolved. The core idea is relevant and the architecture is sensible, but the baseline comparison methodology, statistical validation, and label-zero-shot evaluation need to be strengthened before the claims can be fully accepted.