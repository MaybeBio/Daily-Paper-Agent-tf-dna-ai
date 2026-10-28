## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose DNABERT-Enhancer, a genomic language model based on the pre-trained DNABERT architecture, for predicting enhancers and allele-specific enhancer activity in the human genome. Two models were trained on ENCODE candidate cis-Regulatory Element collections, with the best model achieving 88.05% accuracy and a Matthews correlation coefficient of 76% on independent held-out data. The authors also report genome-wide enhancer predictions across all human chromosomes, comparisons with public enhancer databases, and application of the model to predict candidate SNPs with allele-specific enhancer and transcription factor binding activity.
- **Visible evidence base** Abstract text only; no quantitative performance metrics beyond accuracy and MCC, no dataset descriptions, no model architecture details, no validation methodology, no comparison benchmarks, no SNP prediction results
- **Missing materials affecting confidence** Full manuscript, methods section, model training and fine-tuning details, dataset composition and preprocessing, evaluation protocols, baseline comparisons, statistical significance testing, genome-wide prediction methodology, SNP prediction validation, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a potentially useful application of a pre-trained genomic language model to enhancer prediction, a problem of ongoing interest in regulatory genomics. The reported performance metrics are plausible but cannot be independently assessed without methodological details. The claim of genome-wide enhancer annotation and allele-specific activity prediction is ambitious, but the abstract provides no evidence of validation for these downstream applications. The work may be of interest to computational biologists and functional genomics researchers, but the current evidence base is insufficient to establish the core claims.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory element prediction, genomic language model applications, and variant effect prediction would be the primary audience. Researchers studying enhancer biology and non-coding variant interpretation in human genetics may also find the predicted resources useful, provided the methods and validation are robust.
- **Major strengths** The use of a pre-trained genomic language model to capture sequence context for enhancer prediction is a reasonable and timely approach. The reported accuracy and MCC values suggest competitive performance, if reproducible. The extension to allele-specific enhancer and transcription factor binding prediction addresses a practically important problem in variant interpretation.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. Applying DNABERT to enhancer prediction is incremental, as DNABERT has been used for various regulatory element prediction tasks. The allele-specific extension adds some novelty but is not clearly differentiated from existing approaches.  
  - Scientific importance: Potentially relevant to enhancer annotation and variant interpretation, but the significance depends on demonstrated improvements over existing methods and validated downstream utility.  
  - Interdisciplinary readership: The topic bridges machine learning and genomics, which could attract a broad readership, but the abstract does not clearly articulate the broader biological or clinical implications.  
  - Technical soundness: Cannot be assessed from the abstract alone. No methodological details, evaluation protocols, or statistical analyses are provided.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses jargon without sufficient context, and the claims of genome-wide annotation and allele-specific prediction are not explained in accessible terms.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient methodological or validation detail to support the core claims. A full manuscript with detailed methods, benchmarks, and validation would be required for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The best fine-tuned model achieved 88.05% accuracy with Matthews correlation coefficient of 76% on independent set aside data.  
- **Evidence pointer** Abstract, performance metrics section; location not provided  
- **Concern** The abstract reports accuracy and MCC but provides no information on the dataset size, class balance, train-validation-test split, hyperparameter selection, or whether the independent test set is truly disjoint from the training data. Without these details, the reported metrics cannot be interpreted or reproduced.  
- **Why it matters** Performance claims are only meaningful in the context of the evaluation protocol. Class imbalance, data leakage, or inappropriate threshold selection could inflate accuracy and MCC. The absence of these details prevents assessment of whether the model genuinely generalizes.  
- **Resolution test** Provide a detailed description of the dataset, including the number of enhancer and non-enhancer sequences, the source of negative examples, the split strategy, and the exact evaluation protocol. Report precision, recall, F1, and ROC-AUC in addition to accuracy and MCC. If possible, include confidence intervals or cross-validation results.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** We trained two different models, using large collection of enhancers curated from the ENCODE registry of candidate cis-Regulatory Elements.  
- **Evidence pointer** Abstract, model training description; location not provided  
- **Concern** The abstract does not specify which ENCODE cCRE categories were used, how enhancers were defined, how negative regions were selected, or how the two models differ. The choice of training data and negative set construction critically affects model performance and generalizability.  
- **Why it matters** Enhancer prediction models are highly sensitive to the definition of positive and negative examples. If the negative set is not representative of the genomic background, the model may learn trivial discriminative features. Without this information, the biological validity of the predictions is unclear.  
- **Resolution test** Clearly describe the ENCODE cCRE categories used, the filtering criteria, the construction of the negative set, and the differences between the two trained models. Justify these choices with reference to prior work or biological rationale.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** We present the analysis of the predicted enhancers for all chromosomes of the human genome by comparing with the enhancer regions reported in publicly available databases.  
- **Evidence pointer** Abstract, genome-wide analysis description; location not provided  
- **Concern** The abstract claims genome-wide enhancer prediction and comparison with public databases but provides no quantitative results, such as overlap statistics, enrichment analyses, or concordance metrics. It is unclear how the predictions were generated genome-wide, how thresholds were set, and whether the comparisons are meaningful.  
- **Why it matters** Genome-wide predictions are only useful if they are validated against independent resources. Without quantitative comparison results, the claim of genome-wide annotation cannot be evaluated, and the utility of the predicted enhancer set as a resource is unsubstantiated.  
- **Resolution test** Provide overlap statistics with public enhancer databases, such as FANTOM5, VISTA, or ENCODE cCREs, including sensitivity and specificity estimates. Describe the genome-wide prediction pipeline, including windowing strategy, threshold selection, and post-processing filters.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** We applied DNABERT-Enhancer along with other DNABERT based regulatory genomic region prediction models to predict candidate SNPs with allele-specific enhancer and transcription factor binding activity.  
- **Evidence pointer** Abstract, SNP prediction application; location not provided  
- **Concern** The abstract states that the model was applied to predict allele-specific enhancer and transcription factor binding activity for candidate SNPs, but no results, validation, or even a description of the approach are provided. It is unclear how allele-specific predictions were made, whether experimental validation was performed, and how the predictions were benchmarked against existing variant effect prediction tools.  
- **Why it matters** Allele-specific prediction is a strong claim with potential clinical relevance. Without any evidence of accuracy, calibration, or comparison to existing methods, the claim is unsupported. The utility of the predicted candidate SNPs as a resource cannot be assessed.  
- **Resolution test** Describe the computational approach for allele-specific prediction, including how reference and alternative alleles were scored. Provide validation results, such as comparison with experimentally validated allele-specific enhancer activity or existing tools like DeepSEA or Enformer. Report the number of candidate SNPs predicted and any prioritization criteria.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability for nonspecialists  
- **Affected element** Abstract, overall framing  
- **Evidence pointer** Abstract, first sentence; location not provided  
- **Issue** The abstract opens with a general statement about the difficulty of enhancer prediction but does not clearly state what the specific gap or limitation of existing methods is, beyond a vague reference to failing to learn sequence context.  
- **Required correction** Briefly specify what existing methods lack, such as inability to capture long-range dependencies or contextual features, and how the language model approach addresses this.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Scientific importance  
- **Affected element** Abstract, resource claim  
- **Evidence pointer** Abstract, final sentence; location not provided  
- **Issue** The claim that the genome-wide enhancer annotations and candidate loss-of-function genetic variants provide valuable resources is not supported by any description of how these resources will be made available or how they were evaluated for utility.  
- **Required correction** State whether the predictions are publicly available, in what format, and provide at least one example of a validation or application that demonstrates their utility.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Abstract, model naming  
- **Evidence pointer** Abstract, model description; location not provided  
- **Issue** The model is named DNABERT-Enhancer, but the abstract does not clarify whether this is a fine-tuned version of the original DNABERT model or a modified architecture. This could cause confusion for readers familiar with the DNABERT framework.  
- **Required correction** Clarify the relationship between DNABERT-Enhancer and the original DNABERT model, including any architectural modifications or fine-tuning strategies.

## Risk / unsupported claims
- The reported accuracy of 88.05% and MCC of 76% are unsupported without details on dataset composition, evaluation protocol, and statistical significance.
- The claim of genome-wide enhancer prediction across all human chromosomes is unsupported without a description of the prediction pipeline and quantitative comparison results.
- The claim of predicting candidate SNPs with allele-specific enhancer and transcription factor binding activity is unsupported without any methodological description or validation results.
- The assertion that the predicted resources are valuable for genome interpretation in functional and clinical genomics is not substantiated by any evidence of utility or accessibility.