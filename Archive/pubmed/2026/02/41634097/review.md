## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific soundness, methodological clarity, validity of claims, and reproducibility based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors propose TFBS-Finder, a deep learning framework combining a pre-trained DNABERT encoder with CNN, modified convolutional block attention module (MCBAM), multi-scale convolutions with attention (MSCA), and an output module, for predicting transcription factor binding sites. The model is trained and tested on 165 ENCODE ChIP-seq datasets, with reported improvements over existing methods in accuracy, PR-AUC, and ROC-AUC. Ablation studies, cross-cell line validation, and interpretability analyses are presented.
- **Visible evidence base** Abstract, Introduction, Results and Discussion (including Tables 1-7, Figures 1-6), Materials and Methods (including model architecture descriptions and equations), Conclusion, and references to supplementary materials
- **Missing materials affecting confidence** Supplementary tables (S1-S11) and figures referenced but not provided; detailed hyperparameter values; dataset split specifications; baseline model implementation details; code repository not inspected

## Reviewer
- **Overall assessment** The manuscript presents a technically plausible architecture for TFBS prediction, combining a pre-trained transformer encoder with attention-augmented convolutional modules. The experimental design includes appropriate comparisons and ablations. However, several methodological details are missing or unclear, particularly regarding data partitioning, baseline fairness, and statistical rigor. The reported performance gains, while positive, are modest and require closer scrutiny of experimental conditions. The work is of interest to the computational genomics community but does not yet establish a clear advance over existing methods from the evidence provided.
- **Who would be interested in the results, and why** Researchers in computational biology and genomics, particularly those working on regulatory genomics, transcription factor binding prediction, and application of large language models to DNA sequences. The work may also interest method developers in deep learning for biological sequence analysis.
- **Major strengths** 1. The architecture is well-motivated, combining global context from DNABERT with local feature extraction through attention-augmented convolutions. 2. The evaluation on 165 ENCODE datasets is comprehensive in scale. 3. Ablation studies systematically isolate the contribution of each module. 4. Cross-cell line validation addresses generalizability. 5. Interpretability analysis via saliency maps and motif discovery adds practical value. 6. Code availability supports reproducibility.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (data leakage risk), R1-M2 (baseline fairness), R1-M3 (statistical reporting), R1-M4 (negative set construction)
- **Assessment against Nature-style criteria** Originality: Moderate. The combination of DNABERT with attention-augmented convolutions is incremental over existing work, particularly BERT-TFBS, which the authors acknowledge. Scientific importance: Moderate. TFBS prediction is an active area, but the performance gains over strong baselines are small and may not translate to biological insight. Interdisciplinary readership: Limited. The work is primarily of interest to computational genomics specialists. Technical soundness: Partially established. The architecture is reasonable, but missing experimental details prevent full assessment. Readability for nonspecialists: Adequate. The manuscript is generally clear, though some sections assume familiarity with deep learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea has merit, but the current evidence does not fully establish superiority over existing methods due to potential data leakage, baseline fairness issues, and incomplete statistical reporting.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validity
- **Claim pointer** The claim that TFBS-Finder outperforms existing methods on 165 ENCODE ChIP-seq datasets.
- **Evidence pointer** Table 5, Section "Comparison with existing models"
- **Concern** The manuscript does not specify how the dataset was partitioned into training, validation, and test sets. If the same ENCODE datasets were used for both training and testing across compared methods, there is a risk of data leakage, particularly if overlapping genomic regions appear in both sets. The authors state the dataset is "the same as considered in [6]" but do not clarify whether the train/test splits are identical to those used for baselines.
- **Why it matters** Data leakage can inflate performance estimates and make comparisons unfair. Without clear partitioning details, the reported improvements may not reflect genuine generalization.
- **Resolution test** Provide explicit description of train/validation/test splits, including whether they are genomic-region-based or sequence-based, and confirm that baseline methods were evaluated under identical conditions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evaluation
- **Claim pointer** The claim that TFBS-Finder outperforms nine benchmark models including BERT-TFBS, DeepBind, DanQ, and others.
- **Evidence pointer** Table 5, Section "Comparison with existing models"
- **Concern** The manuscript does not describe how baseline models were trained and tuned. Were hyperparameters optimized for each baseline? Were the same training epochs, early stopping criteria, and data augmentation used? Without this information, it is unclear whether the comparison is fair or whether baselines were disadvantaged.
- **Why it matters** Unfair comparisons undermine the central claim of superiority. If baselines were not properly tuned, the reported gains may be artifacts of suboptimal baseline performance.
- **Resolution test** Provide details of baseline training procedures, including hyperparameter search, epochs, and any modifications made for fair comparison. Ideally, report results from published baseline implementations without modification.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The claim that TFBS-Finder shows statistically significant improvements over baselines.
- **Evidence pointer** Table 6, Section "Comparison with existing models"
- **Concern** While p-values and effect sizes are reported, the manuscript does not specify which statistical test was used, how many comparisons were performed, or whether multiple testing correction was applied. Additionally, the number of datasets (165) is large, and reporting only average values may obscure variability across datasets.
- **Why it matters** Without proper statistical methodology, the significance claims cannot be evaluated. Multiple testing across 165 datasets increases the risk of false positives.
- **Resolution test** Specify the statistical test used, whether it was paired or unpaired, and whether multiple testing correction was applied. Consider reporting confidence intervals or per-dataset distributions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Data construction
- **Claim pointer** The claim that TFBS-Finder generalizes well across cell lines based on cross-cell line validation.
- **Evidence pointer** Table 4, Section "Cross-cell line validation"
- **Concern** The negative sequences are constructed by shuffling positive sequences while conserving dinucleotide frequencies. The authors acknowledge this limitation in the Conclusion but do not address its impact on the reported results. Shuffled sequences may be easier to distinguish from real genomic sequences, potentially inflating performance. Additionally, the cross-cell line validation uses only CTCF, which limits the generalizability of the conclusion.
- **Why it matters** If the negative set is artificially easy, the model may not perform as well on realistic genomic backgrounds. The cross-cell line claim is based on a single TF, which is insufficient to establish generalizability.
- **Resolution test** Include experiments with alternative negative sets (e.g., genomic regions without known binding) and validate cross-cell line performance on additional TFs beyond CTCF.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Table 1
- **Evidence pointer** Section "Performance based on k-mer value"
- **Issue** The table reports average values but does not specify the number of datasets used for the k-mer selection experiments or the standard deviation.
- **Required correction** Add the number of datasets and standard deviations to Table 1, or state that these are preliminary results on a subset.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model training section
- **Evidence pointer** Section "Model training"
- **Issue** The manuscript states "All the hyperparameters are selected based on experiments" but does not provide the final hyperparameter values in the main text.
- **Required correction** Include the final hyperparameter values in the main text or clearly reference the supplementary table where they are listed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Section "Ablation study"
- **Issue** The violin plots are described but the figure itself is not visible in the provided text. The description of outliers and quartiles is clear, but the reader cannot verify the claims without the figure.
- **Required correction** Ensure the figure is included in the final submission and that all panels are referenced in the text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Cross-cell line validation
- **Evidence pointer** Section "Cross-cell line validation"
- **Issue** The manuscript mentions misclassification of YY1, CoREST, MYC, and HDAC as CTCF but does not provide quantitative evidence or a systematic analysis of these errors.
- **Required correction** Provide a brief quantitative summary of the most frequently confused TFs, or reference a supplementary figure/table with this information.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Introduction
- **Evidence pointer** Section "Introduction"
- **Issue** The sentence "To summarise, the main contributions of the work are as follows:We propose a novel DNABERT-based deep learning model..." is missing a space after the colon.
- **Required correction** Fix the typographical error.

## Risk / unsupported claims
- The claim of "superiority" over existing methods is not fully supported without evidence of fair baseline tuning and identical data splits.
- The claim of "generalisability and robustness" based on cross-cell line validation is only demonstrated for CTCF and may not extend to other TFs.
- The claim that the model "successfully recovers the canonical binding patterns" is based on only two TFs (CEBPB and GATA3) and may not be representative.
- The efficiency comparison in Table 7 is limited to BERT-TFBS and does not include other baselines, making the claim of efficiency gains incomplete.
- The manuscript states that "all the existing methodologies with which we have compared TFBS-Finder have considered the same ChIP-seq experiments," but this is an assumption that cannot be verified from the provided text.