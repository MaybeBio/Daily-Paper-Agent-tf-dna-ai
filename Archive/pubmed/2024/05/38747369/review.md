## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present ProkDBP, a machine learning model for predicting prokaryotic DNA binding proteins (DBPs). They report that a light gradient boosting machine (LGBM) with random forest variable importance measure (RF-VIM) feature selection achieved the highest five-fold cross-validation accuracy among 14 models, with auROC 0.9534 and auPRC 0.9575. Independent testing yielded auROC 0.9332 and auPRC 0.9371. The model is claimed to outperform several existing tools and is available as a web server.
- **Visible evidence base** Abstract text only; no methodological details, dataset descriptions, feature definitions, or performance comparison tables are provided
- **Missing materials affecting confidence** Full manuscript, dataset composition and size, feature encoding details, hyperparameter settings, cross-validation protocol, independent dataset source and characteristics, baseline model specifications, statistical significance tests, and web server implementation details

## Reviewer
- **Overall assessment** The abstract presents a potentially useful computational tool for prokaryotic DBP prediction, but the evidence provided is insufficient to evaluate the technical soundness or the validity of the performance claims. The reported metrics are promising, yet the lack of methodological transparency and comparative rigor prevents a definitive assessment. The work addresses a relevant gap in prokaryotic-specific prediction, but the case for superiority over existing models is not established from the supplied material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those focused on DNA binding proteins. Microbiologists studying gene regulation in prokaryotes may also find the tool useful for prioritizing candidate proteins. The web server availability increases practical utility for experimental researchers without programming expertise.
- **Major strengths** The focus on prokaryotic-specific prediction addresses a recognized limitation of generic models. The comparison of 14 models, including both shallow and deep learning approaches, suggests a systematic evaluation. The reported independent test performance and web server availability enhance potential usability.
- **Major Concerns** The abstract lacks critical methodological details needed to assess reproducibility and validity. The claim of superiority over existing models is not supported by specific comparative data. The absence of dataset descriptions and statistical testing undermines confidence in the reported performance differences.
- **Minor Comments** The abstract would benefit from clearer specification of the feature types used. The choice of evaluation metrics is appropriate but should be complemented by additional measures such as sensitivity and specificity. The web server URL is provided, but no information on implementation or user interface is given.
- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset and protocol transparency), R1-M2 (comparative evidence), R1-M3 (statistical significance)
- **Assessment against Nature-style criteria** Originality: Moderate, as the application of existing machine learning methods to a prokaryotic-specific problem is incremental. Scientific importance: Potentially relevant for prokaryotic biology, but the abstract does not demonstrate broader biological insights. Interdisciplinary readership: Limited, as the content is primarily methodological and will appeal mainly to computational specialists. Technical soundness: Not assessable from the abstract due to missing methodological details. Readability for nonspecialists: The abstract is generally clear but uses technical terms without sufficient explanation for a broad audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially useful tool, but the lack of methodological transparency and comparative rigor means the core claims cannot be verified. A revised version with full methodological details and robust comparative analysis would be needed for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model achieved the highest five-fold cross-validation accuracy with auROC 0.9534 and auPRC 0.9575 among 14 models.
- **Evidence pointer** Abstract, performance metrics section; location not provided
- **Concern** The abstract does not describe the dataset used for training and evaluation, including the number of positive and negative samples, sequence identity thresholds for redundancy reduction, or the source of the data. Without this information, the reported performance metrics cannot be interpreted or reproduced.
- **Why it matters** Dataset composition directly affects model performance and generalizability. If the dataset is small, biased, or has high sequence similarity, the reported auROC and auPRC may be inflated. Reproducibility is a fundamental requirement for computational tools.
- **Resolution test** Provide a detailed description of the training and independent datasets, including sample sizes, sequence sources, redundancy reduction procedures, and any class imbalance handling. This information should be in the main text or supplementary materials.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** When benchmarked against several cutting-edge existing models, ProkDBP showcased superior predictive accuracy.
- **Evidence pointer** Abstract, comparison statement; location not provided
- **Concern** The abstract claims superiority over existing models but provides no specific names of the compared tools, no performance values for those tools, and no description of the comparison protocol. The claim is therefore unverifiable.
- **Why it matters** A central contribution of the work is the claimed improvement over existing methods. Without concrete comparative data, the scientific importance of the tool cannot be assessed, and readers cannot judge whether ProkDBP offers a meaningful advance.
- **Resolution test** List the specific existing models compared, report their performance metrics on the same independent dataset, and describe the evaluation protocol. Include a table or figure showing the comparison.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The light gradient boosting machine (LGBM), coupled with evolutionarily significant features selected via random forest variable importance measure (RF-VIM) yielded the highest five-fold cross-validation accuracy.
- **Evidence pointer** Abstract, model selection statement; location not provided
- **Concern** The abstract does not report any statistical significance testing for the difference in performance between LGBM and the other 13 models. The performance gap could be within random variation, especially if the dataset is small.
- **Why it matters** Without significance testing, the claim that LGBM is the best model is not statistically supported. This is critical because the entire tool is built on this model choice.
- **Resolution test** Provide confidence intervals or p-values for the performance differences between LGBM and the other models, or use appropriate statistical tests such as McNemar's test or a paired bootstrap.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract, feature description
- **Evidence pointer** Abstract, "evolutionarily significant features"; location not provided
- **Issue** The term "evolutionarily significant features" is vague and not defined. It is unclear what these features represent or how they were derived.
- **Required correction** Specify the feature types used, such as evolutionary conservation scores, sequence composition, or structural properties, and provide a brief explanation of their biological relevance.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Abstract, model evaluation
- **Evidence pointer** Abstract, performance metrics; location not provided
- **Issue** The abstract reports only auROC and auPRC. These metrics are useful but do not provide a complete picture of model performance, particularly for imbalanced datasets.
- **Required correction** Report additional metrics such as sensitivity, specificity, precision, and F1-score, or state that these are available in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Abstract, web server description
- **Evidence pointer** Abstract, web server URL; location not provided
- **Issue** The abstract mentions the web server but provides no information on its usability, such as input format, output interpretation, or computational requirements.
- **Required correction** Add a brief description of the web server interface and user instructions, or refer to a detailed methods section.

## Risk / unsupported claims
- The claim of superior predictive accuracy over existing models is unsupported because no comparative data are provided.
- The claim that LGBM with RF-VIM is the best model is unsupported without statistical significance testing.
- The reported performance metrics (auROC 0.9534, auPRC 0.9575) are not assessable without dataset details.
- The generalizability of the model to diverse prokaryotic species is not assessable from the abstract.
- The practical utility of the web server cannot be evaluated without implementation details.