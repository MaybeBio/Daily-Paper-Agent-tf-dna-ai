## Review setup
- **Input scope** Full manuscript text (abstract, background, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific claims, methodology, data analysis approach, and interpretation as presented in the manuscript text. Figure images and supplementary materials were not available for review.
- **Shared manuscript claim summary** The authors propose that promoter-bound transcription factor binding sites (TFBSs) can predict downstream alternative splicing patterns. They develop CNN models using TF binding changes between tissue pairs to predict splicing phase changes, achieving an AUROC of 0.889. They further identify candidate splicing regulators through in silico perturbation analysis and validate one candidate (CTCFL) using external knockdown data.
- **Visible evidence base** Abstract, Background, Results, Discussion, Materials and Methods sections. Figure references are present but figure images were not provided. No supplementary materials were available.
- **Missing materials affecting confidence** Figure images (Figs 1-5), supplementary tables, source code repository contents, exact hyperparameter settings, dataset accession numbers, and detailed preprocessing scripts. The absence of figures significantly limits the ability to assess data quality, effect sizes, and the validity of the statistical analyses presented.

## Reviewer
- **Overall assessment** This manuscript addresses an interesting and relatively underexplored question: whether promoter-bound TFBSs can predict downstream alternative splicing patterns. The authors present a systematic computational pipeline integrating DNase-seq, TF motif scanning, and RNA-seq data across 15 human tissues. The work is timely given the growing interest in transcriptional-splicing coupling. However, the manuscript has several significant weaknesses. The most critical issue is the authors' own admission that gene-wise cross-validation (the most rigorous generalization test) yields performance barely above random chance (AUROC ~0.50). This fundamentally undermines the central claim that promoter TFBSs can predict splicing patterns. The subsequent analysis using delta Z-scores and paired tissue comparisons partially addresses this, but the improvement in performance appears to come from a different task formulation (predicting splicing phase change rather than absolute splicing state). The external validation with CTCFL knockdown data is a positive feature, but the analysis is limited to a single TF. The manuscript would benefit from clearer presentation of the relationship between the two prediction tasks, more rigorous baseline comparisons, and additional validation experiments.

- **Who would be interested in the results, and why** Researchers studying alternative splicing regulation, transcriptional-splicing coupling, and computational genomics. The work may also interest those developing deep learning approaches for regulatory genomics. The identification of specific TFs potentially involved in splicing regulation could be of interest to experimental biologists studying splicing mechanisms. The methodological discussion about cross-validation strategies in genomics is relevant to the broader computational biology community.

- **Major strengths** 
  1. The manuscript addresses a novel and important question about the relationship between promoter architecture and alternative splicing, moving beyond the traditional focus on splice site sequences.
  2. The authors implement multiple cross-validation schemes (event-wise, tissue-wise, gene-wise) and honestly report the poor performance of gene-wise validation, demonstrating scientific integrity.
  3. The use of paired tissue comparisons with delta Z-scores is a thoughtful approach to control for gene-specific baseline splicing levels.
  4. The external validation using CTCFL knockdown data provides independent evidence for at least one predicted regulator.
  5. The in silico perturbation analysis for feature importance is a reasonable approach to extract interpretable information from the CNN models.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Core claim validity
- **Claim pointer** The central claim that promoter TFBSs can predict splicing patterns is not supported by the gene-wise cross-validation results, which yield AUROC near 0.50 (random chance).
- **Evidence pointer** Results section, Fig. 1F (yellow bars)
- **Concern** The authors report that gene-wise cross-validation, where genes in the test set are completely unseen during training, yields performance "slightly better than random guess at 0.50." This is the most appropriate test of generalization to new genes, which is the stated goal of the predictive model. The high performance in event-wise and tissue-wise schemes (AUROC ~0.84) is likely inflated by the presence of the same genes in both training and test sets, as the authors themselves acknowledge in the Discussion.
- **Why it matters** The core scientific claim of the manuscript is that promoter TFBS composition can predict splicing patterns. If the model cannot generalize to unseen genes, this claim is not established. The high performance in the other schemes may reflect memorization of gene-specific features rather than learning a general regulatory code.
- **Resolution test** The authors should either (a) demonstrate that gene-wise performance can be improved through better feature engineering, model architecture, or training strategies, or (b) reframe the claims to focus on the more modest finding that TF binding changes are associated with splicing changes in a paired-tissue context, without claiming general predictive power.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors claim that CNN models "learned from the TF binding changes in the promoter to predict the splicing pattern changes" with AUROC of 0.889, but the comparison to simpler baselines is insufficient.
- **Evidence pointer** Results section, Fig. 4B
- **Concern** The manuscript does not report comparisons against simpler baseline models that might achieve similar performance without capturing meaningful biological signal. For example, a model using only the number of TFBSs, or only the most informative single TF, or a model using random permutations of the input features, would help establish that the CNN is learning genuine regulatory relationships. Additionally, the authors do not report confidence intervals for the AUROC values, making it impossible to assess whether the differences between models are statistically significant.
- **Why it matters** Without appropriate baselines, the claimed superiority of the CNN approach cannot be evaluated. The high AUROC might be achievable by much simpler models, which would weaken the claim that the complex spatial arrangement of TFBSs is important for splicing regulation.
- **Resolution test** The authors should include: (a) a baseline model using only TFBS counts (no positional information), (b) a model trained on randomly shuffled input features to establish chance-level performance, (c) confidence intervals or statistical tests comparing model performances, and (d) ideally, a comparison to a model using only the most predictive individual TFBSs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Validation depth
- **Claim pointer** The authors state that "through an in silico perturbation-based analysis of the CNN models, we identified several TFs that considerably reduced the model performance of splicing prediction" and validate CTCFL using external knockdown data.
- **Evidence pointer** Results section, Fig. 5
- **Concern** Only one TF (CTCFL) is validated experimentally using external data. The other 18 candidate TFs identified by the perturbation analysis are not validated. Furthermore, the CTCFL validation is limited to a single cell line (K562) and the analysis only shows a statistical difference in delta Z-scores between target and non-target genes, without demonstrating that the direction of splicing changes is consistent with the model's predictions.
- **Why it matters** The identification of specific TFs as potential splicing regulators is a key contribution of the work. Validation of only one TF, with limited analysis, is insufficient to establish the biological relevance of the predictions. The manuscript would be strengthened by validating additional TFs or by providing more detailed analysis of the CTCFL results, such as directionality of splicing changes and consistency with model predictions.
- **Resolution test** The authors should either validate additional TFs using available public datasets, or provide a more comprehensive analysis of the CTCFL validation, including directionality of splicing changes, comparison with model predictions for individual genes, and ideally validation in additional cell lines or conditions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data and feature representation
- **Claim pointer** The authors use TF binding motif scanning within DNase-seq defined open chromatin regions to define TFBS occupancy, but the validity of this approach is not thoroughly discussed.
- **Evidence pointer** Methods section, "Identification of putative in vivo TF binding sites"
- **Concern** The approach of scanning for TF motifs within open chromatin regions is an indirect measure of TF binding. The authors do not discuss the limitations of this approach, such as the high false positive rate of motif scanning, the lack of consideration of TF concentration or cooperativity, and the potential for motifs to be bound by multiple TFs. Additionally, the use of a less stringent FDR threshold (<10^-3) for motif scanning may increase false positives. The authors also do not compare their approach to using actual ChIP-seq data for a subset of TFs, which would be a useful validation.
- **Why it matters** The quality of the input features directly affects the validity of the conclusions. If the TFBS representation is noisy or inaccurate, the model may be learning spurious patterns. The authors should acknowledge these limitations and ideally provide some validation of their TFBS calling approach.
- **Resolution test** The authors should discuss the limitations of their TFBS representation and ideally provide a comparison using ChIP-seq data for a subset of TFs to validate their approach. At minimum, they should acknowledge the potential for false positives and discuss how this might affect their conclusions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and biological insight
- **Claim pointer** The authors claim that the importance analysis "identified several TFs that considerably reduced the model performance of splicing prediction" and that these TFs are potential splicing regulators.
- **Evidence pointer** Results section, Fig. 5A
- **Concern** The importance analysis identifies TFs that are important for the model's predictions, but this does not necessarily mean these TFs are biologically relevant for splicing regulation. The analysis is purely computational and the link to biological mechanism is speculative. The authors do not provide any functional enrichment analysis of the target genes of the identified TFs, nor do they discuss whether the identified TFs are known to be involved in splicing regulation.
- **Why it matters** The biological interpretation of the model is a key contribution of the work. Without additional analysis linking the identified TFs to known biological pathways or processes, the significance of the findings is limited.
- **Resolution test** The authors should perform additional analyses to strengthen the biological interpretation, such as: (a) functional enrichment analysis of target genes of identified TFs, (b) comparison with known splicing regulators, (c) analysis of whether the identified TFs are differentially expressed across the 15 tissues in a manner consistent with their predicted role in splicing regulation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract, Results section
- **Issue** The abstract states that CNN models "learned from the TF binding changes in the promoter to predict the splicing pattern changes" with AUROC of 0.889, but this performance is only achieved in the paired-tissue delta Z-score framework, not in the absolute splicing prediction task. The abstract should clarify this distinction.
- **Required correction** Revise the abstract to clearly distinguish between the two prediction tasks and report the performance of each, including the poor gene-wise performance for absolute splicing prediction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Results section, Fig. 3 and 4
- **Issue** The manuscript reports AUROC and AUPRC values but does not provide confidence intervals or statistical tests comparing model performances across cross-validation folds.
- **Required correction** Report mean and standard deviation (or confidence intervals) for all performance metrics across cross-validation folds, and perform statistical tests (e.g., paired t-test or Wilcoxon test) to compare model performances.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods section
- **Evidence pointer** Methods section, "Machine learning and deep learning models"
- **Issue** The hyperparameter settings for the DNN and CNN models are not fully described. The number of layers, filter sizes, learning rates, batch sizes, and number of training epochs are not specified.
- **Required correction** Provide complete hyperparameter specifications for all models, including the number of convolutional filters, kernel sizes, pooling strategies, learning rates, and optimization algorithms.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods section
- **Evidence pointer** Methods section, "Data processing and sample selection"
- **Issue** The specific ENCODE dataset accession numbers for the DNase-seq and RNA-seq data are not provided. This limits reproducibility.
- **Required correction** Provide a table listing all ENCODE dataset accession numbers used in the study, including the specific experiment and file accessions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Background section
- **Evidence pointer** Background section
- **Issue** The Background section contains some awkward phrasing and grammatical errors (e.g., "Date to 20 years ago" should be "Dating back to 20 years ago").
- **Required correction** Carefully proofread the manuscript for grammatical errors and awkward phrasing.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures
- **Evidence pointer** Fig. 1-5 (not visible to reviewer)
- **Issue** The figure legends are not provided in the manuscript text, making it impossible to fully interpret the figures.
- **Required correction** Ensure that all figure legends are complete and self-contained, describing all panels, axes, and statistical annotations.

## Risk / unsupported claims
- The claim that promoter TFBSs can predict splicing patterns is not supported by the gene-wise cross-validation results, which show near-random performance.
- The claim that the identified TFs are potential splicing regulators is based solely on computational analysis and is not sufficiently validated experimentally.
- The claim that the CNN model "learned" the regulatory code from TF binding changes is not supported by comparison to simpler baseline models.
- The biological significance of the findings is not established, as no functional validation or enrichment analysis is provided.
- The generalizability of the findings beyond the 15 tissues studied is not addressed.
- The relationship between the two prediction tasks (absolute splicing state vs. splicing phase change) is not clearly explained, and the relationship between performance in these tasks is not discussed.