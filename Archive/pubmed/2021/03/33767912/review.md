## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, experimental design, and conclusions as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose CRPTS, a hybrid convolutional recurrent neural network architecture that combines DNA sequence and DNA shape features to predict transcription factor binding sites. They claim superior performance over state-of-the-art methods on 66 in vitro uPBM datasets, and demonstrate the ability to discover experimentally verified binding motifs.
- **Visible evidence base** Abstract, Introduction, Results (including Figures 1-4 and Table 1), Discussion, Materials and Methods, Supplemental Information description
- **Missing materials affecting confidence** Supplemental Tables S1-S3 referenced but not provided; full experimental results per dataset not visible; comparison methodology details incomplete; hyperparameter tuning procedure not described; statistical significance testing details absent

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in transcriptional regulation by proposing a hybrid deep learning architecture that integrates DNA sequence and shape features for TFBS prediction. The idea of using a shared hybrid CNN/RNN model is reasonable and builds upon prior work (DLBSS). However, the manuscript has several significant weaknesses that prevent the claims from being fully established. The performance improvements reported are modest, the experimental comparison lacks critical details, and the statistical rigor is insufficient. The novelty claim is partially overstated given the existence of DLBSS. The writing is generally clear but some technical details are ambiguous. The work may be of interest to the computational biology community, but substantial revisions and additional analyses are required before the conclusions can be considered robust.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on transcription factor binding prediction, regulatory genomics, and deep learning applications in genomics. Researchers developing sequence-based predictive models who are interested in incorporating structural features would find the shared architecture approach relevant. The motif visualization component may also interest experimental biologists studying TF-DNA recognition mechanisms.

- **Major strengths** 
  1. The problem is important and timely, with clear practical applications in regulatory genomics.
  2. The shared hybrid architecture is a sensible extension of prior work, combining CNN for local pattern detection and RNN for long-range dependencies.
  3. The authors evaluate on a substantial benchmark of 66 uPBM datasets, which provides reasonable breadth.
  4. The motif visualization component adds interpretability value beyond simple prediction accuracy.
  5. Code availability is a positive feature for reproducibility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "CRPTS significantly outperforms the state-of-the-art methods" and "CRPTS achieves a statistically significant improvement in average R2 and PCC"
- **Evidence pointer** Figure 3, Tables S1 and S2 (location not provided)
- **Concern** The authors claim statistical significance for performance improvements but provide no statistical testing methodology. No p-values, confidence intervals, or effect sizes are reported. The statement "statistically significant improvement" appears in the Results section without any supporting statistical analysis. The boxplots in Figure 3 show distributions but no significance indicators.
- **Why it matters** Claims of superiority over existing methods require proper statistical validation. Without significance testing, the observed improvements (approximately 6% in R2 and 4% in PCC over DLBSS) could be within normal variation across cross-validation folds. The scientific community requires rigorous statistical evidence before accepting performance claims.
- **Resolution test** Provide appropriate statistical tests (e.g., paired t-test, Wilcoxon signed-rank test) across the 66 datasets comparing CRPTS with each baseline. Report exact p-values, confidence intervals, and effect sizes. If multiple comparisons are performed, apply appropriate corrections.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental comparison completeness
- **Claim pointer** "CRPTS obviously outperforms the state-of-the-art methods"
- **Evidence pointer** Tables S1 and S2 (location not provided), Figure 2
- **Concern** The comparison with state-of-the-art methods is incomplete. Only DeepBind, two kernel-based methods, and DLBSS are compared. Several recent deep learning methods for TFBS prediction (e.g., DeepSEA, Basset, DanQ) are mentioned in the introduction but not included in the comparison. The choice of baselines appears selective, and the rationale for excluding other established methods is not provided. Additionally, the hyperparameter settings for baseline methods are not described, raising concerns about whether they were optimally configured.
- **Why it matters** A fair and comprehensive comparison is essential to support claims of state-of-the-art performance. Selective baseline selection can bias results. Without details on baseline configuration, readers cannot assess whether the comparison was fair. The claim of outperforming "state-of-the-art methods" requires comparison against the current best-performing approaches.
- **Resolution test** Include additional recent deep learning baselines (e.g., DeepSEA, Basset, DanQ) with appropriate hyperparameter tuning. Describe baseline configurations in detail. Justify the selection of comparison methods. If computational constraints limit the number of baselines, provide clear reasoning for the chosen set.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and contribution
- **Claim pointer** "The novelty of our proposed method relies on three critical aspects: (1) the shared hybrid CNN and RNN... (2) common patterns found from DNA sequences and their corresponding DNA shape features; (3) capture local structural information without completely relying on DNA shape data"
- **Evidence pointer** Introduction, Discussion
- **Concern** The novelty claim is not sufficiently differentiated from prior work. DLBSS already uses a shared CNN to find common patterns from DNA sequences and shape features. The primary difference appears to be the addition of an RNN/LSTM layer. The authors acknowledge this in the introduction but do not clearly articulate what specific advantages the RNN component provides beyond what DLBSS achieves. The claim of "first use" of a shared hybrid model for this task is not clearly established, and the incremental contribution needs to be more precisely defined.
- **Why it matters** For a methods paper, the novelty and contribution must be clearly articulated. If the improvement is primarily the addition of an LSTM layer, the authors need to demonstrate why this architectural choice is significant and what specific limitations of prior work it addresses. Reviewers and readers need to understand the distinct contribution to justify publication.
- **Resolution test** Provide a more precise statement of novelty that clearly differentiates from DLBSS. Include an ablation study showing the contribution of each component (shared architecture, RNN, shape features) to the final performance. Discuss specific limitations of DLBSS that the proposed architecture addresses.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical reproducibility
- **Claim pointer** "The source code is freely provided in the GitHub repository"
- **Evidence pointer** Materials and Methods, GitHub link
- **Concern** While code availability is commendable, the manuscript lacks sufficient detail for reproduction. The exact architecture dimensions (number of LSTM units, number of fully connected layer units) are partially specified, but the training procedure is incomplete. The learning rate, batch size is given (300), but the optimizer parameters, initialization scheme, and data augmentation (if any) are not described. The early stopping criterion is not specified. The random seed for reproducibility is not mentioned.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without complete training details, other researchers cannot reliably reproduce the results. The GitHub repository may contain the code, but the manuscript should be self-contained enough for understanding and reproduction.
- **Resolution test** Provide complete training details including learning rate schedule, initialization, early stopping criteria, and random seeds. Ensure the GitHub repository contains all necessary code and instructions for reproducing the reported results.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evaluation methodology
- **Claim pointer** "The performance of the CRPTS was measured using 5-fold cross-validation for each of 66 in vitro datasets"
- **Evidence pointer** Results, Materials and Methods
- **Concern** The evaluation methodology has several ambiguities. The train/validation/test split strategy is not clearly described. The authors mention "the optimal parameter set was retained during the training process and applied to the entire training dataset," which suggests a potential data leakage issue if the validation set is used for early stopping and then the model is retrained on the full training set. The metric computation details (whether R2 and PCC are computed per dataset and then averaged, or pooled across datasets) are not specified.
- **Why it matters** Proper evaluation methodology is critical for reliable performance assessment. Data leakage or inappropriate metric aggregation can lead to inflated performance estimates. The described procedure of retraining on the entire training dataset after parameter selection could compromise the validity of the cross-validation results.
- **Resolution test** Clearly describe the data splitting strategy (e.g., 80/10/10 for train/validation/test). Clarify whether the final model is trained on the full training set after hyperparameter selection and how this affects the reported metrics. Specify how R2 and PCC are aggregated across datasets.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1 description
- **Evidence pointer** Figure 1
- **Issue** The figure caption describes the architecture but the flow of data through the network is not entirely clear. The relationship between the "channels matching module" and the "feature extraction module" could be better illustrated.
- **Required correction** Enhance Figure 1 to clearly show the data flow, including tensor shapes at each stage and how the sequence and shape inputs are combined.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table shows examples of learned motifs but does not provide quantitative similarity scores or the number of motifs successfully recovered across all 66 datasets.
- **Required correction** Add a column with motif similarity scores (e.g., Pearson correlation with known motifs) and report the fraction of datasets where motifs were successfully recovered.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Equation 13
- **Evidence pointer** Materials and Methods
- **Issue** The loss function includes an L2 regularization term, but the regularization parameter λ is not specified. The notation "yi‾" is used for ground truth, which is unconventional and could be confused with the mean.
- **Required correction** Specify the value or range of λ used. Use standard notation for ground truth (e.g., yi) and predicted values (e.g., ŷi).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion of future work and limitations is brief. The authors mention combining 13 DNA structure features but do not discuss potential limitations of the current approach, such as generalizability to in vivo data or computational efficiency.
- **Required correction** Expand the discussion to include limitations of the proposed method and a more detailed plan for future extensions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** GitHub repository
- **Evidence pointer** Materials and Methods
- **Issue** The manuscript states the code is available but does not describe the repository structure or provide usage instructions.
- **Required correction** Add a brief description of the repository contents and basic usage instructions in the manuscript or as supplementary material.

## Risk / unsupported claims
- The claim of "statistically significant improvement" is unsupported as no statistical tests are described or reported.
- The claim of "obviously outperforms the state-of-the-art methods" is not fully supported given the incomplete baseline comparison.
- The novelty claim regarding the "shared hybrid CNN and RNN" being first used for this task is not clearly established with a comprehensive literature review.
- The claim that CRPTS "can capture local structural information of DNA sequences without completely relying on DNA shape data" is not directly tested; the comparison between CRPT and CRPTS shows only modest differences.
- The generalizability claim in the Discussion ("accommodating any type of high-throughput data") is speculative and not demonstrated.
- The performance improvement over DLBSS (approximately 6% R2 and 4% PCC) is presented without confidence intervals or effect sizes, making the practical significance unclear.