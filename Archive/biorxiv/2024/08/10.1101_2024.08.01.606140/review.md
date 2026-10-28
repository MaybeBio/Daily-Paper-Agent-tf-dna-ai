## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present a framework for predicting regulatory variants in cattle using machine learning, including novel cattle-specific conservation metrics, and demonstrate its utility in enriching for trait-associated variants
- **Visible evidence base** Abstract, full results narrative, discussion, methods, figure/table references (Figures 1-10, Supplementary Figures 1-14, Tables 1-2), code and data availability statements
- **Missing materials affecting confidence** Actual figures and tables not provided; supplementary materials referenced but not included; no raw performance metrics or statistical test details; unpublished cattle MPRA dataset referenced but not described

## Reviewer

- **Overall assessment** This manuscript addresses an important gap in livestock genomics by developing a machine learning framework for regulatory variant prediction in cattle. The work is timely and potentially impactful, given the growing interest in applying AI to animal breeding. The authors demonstrate reasonable performance in both human and cattle models, and the enrichment analyses for trait-associated variants are compelling. However, several technical concerns regarding data quality, model evaluation, and the interpretation of performance gaps between species require clarification. The claim that improved gold-standard training sets are the primary limitation is plausible but not fully established from the provided evidence.

- **Who would be interested in the results, and why** Livestock geneticists and animal breeders would be the primary audience, as the framework offers a practical tool for prioritizing functional variants in cattle breeding programs. Additionally, computational biologists working on regulatory genomics and cross-species model transfer would find the comparative analysis between human and cattle models of interest. The conservation metrics generated for cattle are a valuable community resource.

- **Major strengths** The development of cattle-specific conservation metrics addresses a critical gap in livestock genomics. The species-agnostic pipeline design is commendable and promotes reproducibility. The systematic comparison of model performance across species and the investigation of factors contributing to performance gaps is thorough. The enrichment analyses for trait-associated variants demonstrate practical utility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and representativeness
- **Claim pointer** The cattle eQTL training data from FarmGTLE is used as the gold standard for regulatory variants, and the authors claim that limitations in this dataset explain the performance gap between species.
- **Evidence pointer** Methods section, "Genotype datasets" subsection; Results section, "Comparison of human and cattle baseline models"
- **Concern** The cattle eQTL dataset is derived from heterogeneous public RNA-seq data with variant calling performed solely on RNA-seq, as acknowledged in the introduction. The authors do not provide details on the number of individuals, breeds, tissues, or the quality control measures applied to this dataset. The claim that this dataset's quality is the primary limitation for cattle model performance is not directly tested.
- **Why it matters** If the training data quality is indeed the bottleneck, the conclusions about model transferability and the recommendations for future data generation are valid. However, without a clear characterization of the training data and a direct comparison of data quality metrics between species, alternative explanations (e.g., differences in genetic architecture, annotation quality) cannot be ruled out.
- **Resolution test** Provide detailed statistics on the cattle eQTL dataset (number of samples, breeds, tissues, variant counts, quality metrics). Conduct a direct comparison of data quality between human and cattle training sets, such as the proportion of variants with high imputation confidence or the consistency of eQTL effect sizes across studies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model evaluation and generalizability
- **Claim pointer** The models achieve high AUROC scores (0.86 in human, 0.81 in cattle) and substantially enrich for trait-associated variants.
- **Evidence pointer** Results section, "The ability to predict regulatory variants in humans" and "Our models substantially enrich for trait-associated variants in both species"; Figures 3, 8, 9
- **Concern** The evaluation relies primarily on AUROC, which can be misleading when class distributions are imbalanced. The enrichment analyses use different thresholds and background sets across species and traits, making direct comparisons difficult. The robustness of the enrichment results to different background selection strategies is not fully explored.
- **Why it matters** The practical utility of the models depends on their precision and recall at operationally relevant thresholds, not just ranking ability. If the enrichment is driven by a small number of high-confidence variants or is sensitive to background selection, the conclusions about practical utility may be overstated.
- **Resolution test** Report precision-recall curves and precision at fixed recall levels. Provide enrichment results at multiple thresholds and with different background sets (e.g., matched for genic vs. intergenic, recombination rate). Conduct sensitivity analyses to assess the stability of enrichment estimates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Cross-species transfer and feature importance
- **Claim pointer** The authors claim that human and cattle models trained on common features show similar feature importance, and that human data cannot improve cattle model performance.
- **Evidence pointer** Results section, "Human omics data does not improve cattle models"; Figure 4B
- **Concern** The cross-species transfer experiments are limited to three approaches (direct application, incremental learning, lift-over). The authors do not explore more sophisticated transfer learning methods, such as domain adaptation or multi-task learning, which might be more effective. The interpretation of feature importance is based on SHAP values, but the stability of these rankings across different training runs is not assessed.
- **Why it matters** The conclusion that species-specific models are superior has implications for resource allocation in livestock genomics. If more advanced transfer learning methods could improve cattle model performance, the recommendation to focus solely on cattle-specific data would be premature.
- **Resolution test** Test additional transfer learning approaches, such as fine-tuning with domain adaptation layers or using human model predictions as features in the cattle model. Assess the stability of SHAP feature rankings through bootstrap resampling.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Enformer feature utility
- **Claim pointer** The authors conclude that Enformer features provide little benefit in predicting regulatory variants in either species.
- **Evidence pointer** Results section, "Enformer provides little benefit in predicting regulatory variants in either species"; Figure 5
- **Concern** The Enformer features are derived from the difference between reference and alternative allele predictions, which may not capture the full information available from the model. The authors do not explore alternative ways of using Enformer outputs, such as using the raw predicted profiles as features or using attention-based aggregation. The comparison is also limited to a single model architecture (CatBoost).
- **Why it matters** If the conclusion that deep learning sequence models are of limited utility is incorrect, it could discourage valuable research directions. The finding that Enformer features are not helpful is surprising given their success in human genomics and warrants more thorough investigation.
- **Resolution test** Explore alternative feature extraction methods from Enformer, such as using the full predicted profile or embeddings from intermediate layers. Test the utility of Enformer features with different downstream models, including neural networks that might better capture the structure of the features.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and resource availability
- **Claim pointer** The framework is described as species-agnostic and reusable, with code and data availability statements.
- **Evidence pointer** Methods section, "Code availability" and "Data availability" subsections
- **Concern** While the code is available on GitHub, the manuscript does not provide a detailed description of the computational environment, dependencies, or expected runtime. The cattle conservation metrics are deposited on Zenodo, but the full set of trained models and intermediate data (e.g., feature matrices) are not mentioned. The unpublished cattle MPRA dataset is referenced but not described in sufficient detail.
- **Why it matters** Reproducibility is a core requirement for computational biology. Without clear documentation and access to all necessary data and models, other researchers may not be able to validate or build upon this work.
- **Resolution test** Provide a detailed README with installation instructions, dependency versions, and example commands. Deposit trained models and feature matrices in a public repository. Describe the cattle MPRA dataset in the methods or provide a preprint citation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figures
- **Affected element** Figures 3, 4, 8, 9
- **Evidence pointer** Results section, multiple subsections
- **Issue** The text references ROC curves, SHAP plots, and enrichment plots, but the actual figures are not provided in the manuscript. The descriptions in the text are not sufficient to fully evaluate the results.
- **Required correction** Ensure all figures are included in the final submission with clear axis labels, legends, and annotations. Consider adding supplementary figures for additional model performance metrics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Enrichment analyses
- **Evidence pointer** Results section, "Our models substantially enrich for trait-associated variants in both species"
- **Issue** The enrichment ratios are reported without confidence intervals or statistical significance tests. The number of background sampling iterations is mentioned but not the variability across iterations.
- **Required correction** Report confidence intervals for enrichment ratios and provide the distribution of background enrichment values. Consider using a permutation test to assess statistical significance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** "regulatory variants" vs. "functional variants"
- **Evidence pointer** Throughout the manuscript
- **Issue** The terms "regulatory variants" and "functional variants" are used interchangeably, which could cause confusion.
- **Required correction** Define both terms early in the manuscript and use them consistently, or clarify the distinction if one is intended.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, final paragraph
- **Issue** The discussion of limitations focuses primarily on data quality but does not address potential biases in the model evaluation, such as the choice of background variants or the chromosome-level holdout strategy.
- **Required correction** Add a paragraph discussing the limitations of the evaluation strategy and potential sources of bias.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Citation completeness
- **Affected element** References to unpublished data
- **Evidence pointer** Results section, "Model performance in predicting human and cattle MPRA regulatory variants"
- **Issue** The cattle MPRA dataset is described as "unpublished" without a preprint or author citation, making it difficult for readers to assess the data quality.
- **Required correction** Provide a preprint citation or describe the dataset in sufficient detail in the methods.

## Risk / unsupported claims
- The claim that "the best approach would be generating improved gold-standard sets of known cattle regulatory variants" is presented as a conclusion but is not directly tested; it is inferred from the performance gap analysis.
- The claim that "human omics data does not improve cattle models" is based on three specific transfer approaches and may not generalize to other methods.
- The claim that Enformer features provide "little benefit" is based on a specific feature extraction method and may not hold for alternative approaches.
- The enrichment results for cattle traits are based on a limited number of traits and may not generalize to other phenotypes.
- The statement that the framework has "potential for wider use across animal species" is speculative and not supported by direct evidence in this manuscript.