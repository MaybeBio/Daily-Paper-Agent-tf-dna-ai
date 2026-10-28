## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) and supporting information file list. No figures, tables, or supplementary data files were provided for direct inspection.
- **Assessment boundary** Assessment is limited to the claims, methods, and results as described in the text. Statistical details, figure contents, and supplementary results (S1-S15 Figs, S1-S3 Tables, S1 Text) could not be independently verified.
- **Shared manuscript claim summary** The authors present FCNsignal, a fully convolutional neural network framework that predicts transcription factor (TF) DNA binding signals at base-resolution from DNA sequence. The framework is claimed to simultaneously perform four tasks: (i) modeling base-resolution binding signals, (ii) discriminating binding from non-binding regions, (iii) locating TF binding regions, and (iv) predicting binding motifs. The authors further claim superior performance over existing methods on 53 ChIP-seq and 6 ATAC-seq datasets, the ability to predict on sequences of arbitrary length, genome-wide localization of binding regions on chromosome 17, and identification of causal disease-associated SNPs from LD groups.
- **Visible evidence base** Text descriptions of results referencing Figures 1-7 and Supplementary Figures S1-S15, Supplementary Tables S1-S3, and Supplementary Text S1. No actual data, figures, or tables were available for direct examination.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials. Statistical test details (e.g., Wilson's test parameters), exact performance values, dataset accession numbers, hyperparameter settings, and code availability. The absence of these materials substantially limits the ability to verify the reported results.

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in regulatory genomics: predicting TF binding at base resolution from DNA sequence alone. The proposed framework integrates multiple related tasks into a single architecture, which is a useful contribution. However, the manuscript as presented has several significant issues. The evaluation methodology is incompletely described, particularly regarding negative sequence generation, cross-cell-line validation, and the SNP identification experiments. The claim of superiority over existing methods is not fully supported by the visible evidence, and the authors note that FCNA* outperforms FCNsignal on motif prediction. The arbitrary-length input claim requires clarification given the architecture's downsampling and upsampling operations. The SNP analysis appears to be a proof-of-concept with limited validation. The manuscript would benefit from clearer descriptions of the experimental setup, additional baseline comparisons, and more rigorous statistical analysis.
- **Who would be interested in the results, and why** Researchers in computational genomics, regulatory genomics, and machine learning applied to biology would be interested. The framework's ability to perform multiple tasks in a unified architecture is relevant to those developing deep learning methods for genomics. The application to SNP prioritization may interest researchers studying disease-associated genetic variation. The chromatin accessibility prediction results may interest those studying gene regulation across cell types.
- **Major Strengths** The manuscript addresses a relevant problem and proposes a unified framework for multiple related tasks. The use of base-resolution signals as supervision is appropriate and potentially more informative than binary labels. The exploration of arbitrary-length sequence inputs and whole-chromosome prediction is ambitious and practically useful. The application to SNP prioritization is a valuable direction.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (evaluation completeness), R1-M2 (arbitrary length claim), R1-M3 (SNP analysis validation), R1-M4 (baseline comparisons).
- **Assessment against Nature-style criteria** **Originality**: Moderate. The application of FCN architectures to base-resolution TF binding prediction is not entirely new, given prior work such as BPNet. The integration of multiple tasks is a useful but incremental contribution. **Scientific importance**: Moderate to high. Accurate base-resolution prediction of TF binding is important for understanding gene regulation. The potential for genome-wide prediction and SNP prioritization increases the importance. **Interdisciplinary readership**: Moderate. The work is primarily of interest to computational biologists and machine learning researchers. The biological insights are limited. **Technical soundness**: The core approach is reasonable, but the evaluation is incomplete and some claims are not fully supported by the visible evidence. **Readability for nonspecialists**: The manuscript is generally readable, but some sections, particularly the architecture description, could be clearer for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the evaluation and presentation need substantial improvement before the claims can be fully accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evaluation completeness
- **Claim pointer** The authors claim that FCNsignal outperforms existing state-of-the-art methods on signal regression, sequence classification, and motif prediction across 53 ChIP-seq and 6 ATAC-seq datasets.
- **Evidence pointer** Results sections "The overall performance of FCNsignal on ChIP-seq datasets" and "The overall performance of FCNsignal on ATAC-seq datasets"; Figures 2 and 5; Supplementary Figures S3, S5.
- **Concern** The evaluation methodology is incompletely described. The negative sequence generation is only briefly mentioned ("sequences of the same length at 3000bp upstream of the peaks"), and it is unclear whether these are matched for GC content, repeat content, or other confounding factors. The classification task uses the maximum predicted signal with a sigmoid transform, but the threshold for classification is not described. The statistical comparison (Wilson's test, paired) is mentioned, but the number of comparisons, correction for multiple testing, and the exact test procedure are not detailed. The claim of superiority is based on average metrics, but the variance across datasets and the significance of the differences are not reported. The authors note that FCNsignal performs worse than LSGKM on three TFs, which is acknowledged but not fully analyzed.
- **Why it matters** Without a complete and rigorous evaluation, the claim of superiority over existing methods is not established. The choice of negative sequences can dramatically affect classification performance. The lack of statistical detail prevents the reader from assessing the reliability of the reported differences.
- **Resolution test** Provide a complete description of the negative sequence generation, including any matching criteria. Report the classification threshold and how it was determined. Provide full statistical details, including the number of comparisons, correction for multiple testing, and effect sizes with confidence intervals. Show the distribution of performance metrics across all datasets, not just averages. Discuss the cases where FCNsignal underperforms and provide a more detailed analysis of the reasons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** The authors claim that FCNsignal can accept sequences of arbitrary length as input.
- **Evidence pointer** Results section "FCNsignal can locate potential TF-DNA binding sites on the whole chromosome"; Figure 4D; Supplementary Figure S12.
- **Concern** The architecture includes downsampling (max-pooling) and upsampling (bilinear interpolation) operations. While FCNs can technically process inputs of varying size, the behavior of the model on very short or very long sequences is not characterized. The claim of "arbitrary length" is strong and requires demonstration. The experiments on chromosome 17 use a sliding window approach (segments of 1000bp), which does not demonstrate true arbitrary-length processing. The authors state that FCNsignal can "predict DNA sequences of arbitrary length" but the experiments only show prediction on fixed-length windows.
- **Why it matters** The claim of arbitrary-length input is a stated advantage of the framework. If the model's performance degrades with sequence length, or if there are practical limits, the claim is misleading. The distinction between processing a single long sequence and processing many fixed-length windows is important.
- **Resolution test** Provide experiments demonstrating the model's performance on sequences of varying lengths (e.g., 500bp, 2000bp, 5000bp, 10000bp). Show that the model can process a single long sequence (e.g., a full chromosome) in one forward pass, or clearly state the limitations. Discuss any architectural constraints on input length.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of SNP analysis
- **Claim pointer** The authors claim that FCNsignal can identify causal SNPs from LD groups.
- **Evidence pointer** Results section "FCNsignal can identify causal SNPs from LD groups"; Figure 7; Supplementary Figure S14.
- **Concern** The SNP analysis is presented as a proof-of-concept with only four examples. The method for computing SNP scores is described, but the validation is limited. For the breast cancer example, the authors report a ratio of SNP scores (54 vs. 1.5) but do not provide a statistical test or a comparison with a null distribution. The choice of DeltaSVM as the only competing method is limited. The authors do not discuss the limitations of using a model trained on one cell type to predict effects in another. The relationship between the predicted signal change and the actual regulatory effect is not established.
- **Why it matters** The identification of causal SNPs is a potentially important application. However, the current evidence is insufficient to support the claim. A more rigorous validation, including additional datasets, statistical testing, and comparison with experimental data, is needed.
- **Resolution test** Provide a more comprehensive evaluation of the SNP prioritization method, including additional datasets and a statistical framework for assessing the significance of the predictions. Compare with additional methods beyond DeltaSVM. Validate the predictions against experimental data (e.g., allelic imbalance, reporter assays) where possible. Discuss the limitations of the approach.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Baseline comparisons
- **Claim pointer** The authors claim that FCNsignal outperforms existing state-of-the-art methods on multiple tasks.
- **Evidence pointer** Results sections on ChIP-seq and ATAC-seq performance; Figures 2, 3, 5.
- **Concern** The choice of baseline methods is not fully justified. For motif prediction, FCNA* outperforms FCNsignal, which is acknowledged but the implications are not fully discussed. The authors state that FCNA* is "extremely dependent on the PCMs" and cannot distinguish positive from negative sequences, but this does not negate its superior motif prediction performance. The comparison with BPNet is relevant, but the authors do not discuss potential differences in training data, hyperparameters, or evaluation protocols. The comparison with LSGKM is limited to classification, and the authors do not discuss whether LSGKM could be adapted for the other tasks.
- **Why it matters** A fair and comprehensive comparison with existing methods is essential to establish the superiority of the proposed approach. The current comparison is incomplete and does not fully address the strengths and weaknesses of each method.
- **Resolution test** Justify the choice of baseline methods. Discuss the implications of FCNA*'s superior motif prediction performance. Ensure that all methods are evaluated under the same conditions (e.g., same training/validation/test splits, same hyperparameter tuning). Consider additional baselines, such as DeepSEA or Basenji, for comparison.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The first sentence is a general statement about the importance of TF binding site identification, but it does not clearly state the specific problem addressed by the manuscript.
- **Required correction** Revise the first sentence to more specifically state the problem of predicting TF binding signals from DNA sequence at base resolution.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and methods, Model training
- **Evidence pointer** "Model training" section
- **Issue** The hyperparameter tuning procedure is described as "randomly sampled 15 times," but the specific ranges for each hyperparameter are not provided. The selection criterion is described as "the best performance," but the metric used for selection is not specified.
- **Required correction** Provide the ranges for each hyperparameter and specify the metric used for model selection on the validation set.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "FCNsignal can accurately predict TF-DNA binding motifs"
- **Evidence pointer** Figure 3A
- **Issue** The description of the motif prediction results is brief. The authors state that FCNsignal outperforms several methods but do not provide specific numbers or a detailed discussion of the differences.
- **Required correction** Provide specific performance values (e.g., median -log2(p-value)) and discuss the significance of the differences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "FCNsignal can identify causal SNPs from LD groups"
- **Evidence pointer** Figure 7
- **Issue** The description of the SNP analysis is brief. The authors do not provide details on the number of SNPs in each LD group, the distribution of scores, or the statistical significance of the results.
- **Required correction** Provide more details on the SNP analysis, including the number of SNPs tested, the distribution of scores, and statistical tests.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Materials and methods, "The proposed framework"
- **Evidence pointer** Equations 1-4
- **Issue** The notation in the equations is not fully defined. For example, the dimensions of the weight matrices and bias vectors are not specified, and the meaning of the superscript (c) is not explicitly stated.
- **Required correction** Define all notation used in the equations, including the dimensions of all variables.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and methods, "Data preparation"
- **Evidence pointer** "Data preparation" section
- **Issue** The description of the data processing is brief. The authors state that peaks were "expanded to 1000bp length," but it is unclear how this was done (e.g., centered on the peak summit, extended from the peak boundaries).
- **Required correction** Provide a detailed description of the data processing steps, including how peaks were expanded and how signals were extracted.

## Risk / unsupported claims
- The claim that FCNsignal "outperforms some existing state-of-the-art methods" is not fully supported by the visible evidence, as the statistical significance of the differences is not reported and the authors note that FCNA* performs better on motif prediction.
- The claim that FCNsignal can "predict DNA sequences of arbitrary length" is not fully supported, as the experiments use fixed-length windows.
- The claim that FCNsignal can "identify causal SNPs from LD groups" is based on a limited proof-of-concept with four examples and no statistical validation.
- The claim that the maximum values of predicted signals can be used to discriminate binding from non-binding regions is based on a correlation analysis (S15 Fig) that was not available for review.
- The claim that FCNsignal can "find most of the known binding regions" on chromosome 17 is based on a comparison with ReMap2020 peaks, but the details of this comparison (e.g., overlap criteria, background model) are not fully described.