## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, declarations)
- **Assessment boundary** Scientific validity of the proposed synthetic benchmarking framework, the claims regarding model attribution performance, and the conclusions drawn from the presented experiments
- **Shared manuscript claim summary** The authors propose a synthetic data generation framework to benchmark the ability of ML-based virtual screening models to identify functional groups responsible for binding. They claim that a deep learning model (PointVS) identifies important functional groups with 39% more efficiency than a fingerprint-based random forest, and that ligand-specific biases substantially impair attribution performance across all tested models.
- **Visible evidence base** Abstract, full methods section, results and discussion section, conclusion, code and data availability statements
- **Missing materials affecting confidence** Figures 1-5 and Tables S1-S2 are referenced but not provided; exact numerical results for many reported metrics are not given in the text; hyperparameter details for the random forest models are not specified; details on the ZINC dataset preprocessing and ligand selection are incomplete

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question in computational drug discovery: whether ML-based virtual screening models learn meaningful intermolecular interactions or exploit dataset biases. The proposed synthetic benchmarking framework is conceptually sound and represents a useful contribution to the field. However, the manuscript as presented has several significant limitations. The absence of the referenced figures and tables makes it impossible to fully evaluate the experimental results. The reported quantitative claims, particularly the 39% efficiency improvement of PointVS over the random forest, are not sufficiently supported by the data presented in the text. The experimental design, while clever, relies on simplified binding rules that may not adequately capture the complexity of real protein-ligand interactions, and the authors acknowledge this limitation but do not fully address its implications for the generalizability of their conclusions. The comparison between PointVS and the fingerprint-based models is somewhat unfair given that the random forest models are not optimized for attribution performance. The manuscript would benefit from a more thorough analysis of the relationship between predictive accuracy and attribution performance, and from a clearer discussion of what the synthetic benchmarks can and cannot tell us about real-world model behavior.

- **Who would be interested in the results, and why** Researchers developing and evaluating ML-based virtual screening methods would be the primary audience. The synthetic benchmarking framework provides a controlled environment for assessing model interpretability, which is of growing interest in the computational chemistry and drug discovery communities. The findings regarding the impact of dataset bias on attribution performance are relevant to anyone working with real-world virtual screening datasets such as DUD-E or LIT-PCBA. The work also speaks to the broader question of whether deep learning models genuinely learn physical interactions or rely on statistical shortcuts, which is of interest to the machine learning for science community more broadly.

- **Major strengths** The synthetic data generation framework is a novel and well-motivated contribution that addresses a genuine gap in the field. The use of deterministic binding rules allows for precise ground truth attribution, which is not possible with real-world data. The authors consider both polar and contribution-based binding mechanisms, providing some robustness to their conclusions. The investigation of dataset bias effects on attribution performance is a valuable addition to the literature. The code and data are made publicly available, which facilitates reproducibility and further research.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that PointVS identified the most important functional groups with 39% more efficiency than a fingerprint-based random forest is a central quantitative result of the paper.
- **Evidence pointer** Abstract, Results section, location not provided
- **Concern** The 39% efficiency improvement is stated in the abstract but the supporting data is not presented in the text. The referenced figures and tables that would contain this information are not provided in the manuscript. Without access to the actual attribution scores, rankings, and statistical comparisons, it is impossible to verify this claim or assess its significance. Furthermore, the definition of "efficiency" in this context is not clearly specified. Is this the relative improvement in Attribution AUC, the MATR score, or some other metric? The lack of clarity and supporting evidence for this headline quantitative claim is a significant issue.
- **Why it matters** This quantitative claim is the primary evidence for the paper's conclusion that deep learning models are better at identifying important functional groups than fingerprint-based methods. If this claim cannot be verified from the presented data, the central argument of the paper is weakened.
- **Resolution test** The authors should provide the full experimental results, including the actual Attribution AUC values, MATR scores, and RER values for all models and datasets, either in the main text or in clearly referenced supplementary tables. The definition of "efficiency" should be explicitly stated and the statistical significance of the 39% improvement should be assessed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The claim that the synthetic datasets allow for an objective assessment of whether ML models can identify functional groups responsible for binding.
- **Evidence pointer** Methods section, Results section, location not provided
- **Concern** The synthetic binding rules are acknowledged by the authors to be considerably simpler than real-world protein-ligand binding. While this is a reasonable starting point, the paper does not adequately address how the simplicity of these rules affects the generalizability of the findings. The polar rule, which requires only a single interaction within a distance threshold, is particularly simplistic. Real binding involves a complex interplay of multiple interactions, desolvation effects, entropic contributions, and conformational changes. The contribution rule is somewhat more realistic but still far from the complexity of actual binding. The authors do not discuss what aspects of real binding are captured by their rules and what aspects are missed, nor do they provide any validation that performance on their synthetic tasks correlates with performance on real-world tasks.
- **Why it matters** The entire premise of the paper is that the synthetic framework can serve as a benchmark for model generalizability to real-world scenarios. If the synthetic tasks are too far removed from reality, the conclusions drawn from them may not transfer. The paper needs to make a more convincing case for why performance on these simplified tasks is informative about real-world model behavior.
- **Resolution test** The authors should provide a more detailed discussion of the relationship between their synthetic binding rules and real protein-ligand interactions. They could also include experiments that vary the complexity of the binding rules to show how model performance changes, or provide evidence from real-world datasets that supports the conclusions drawn from the synthetic experiments.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor
- **Claim pointer** The claim that the attribution performance of the models was assessed using the proposed metrics (Attribution AUC, MATR, RER).
- **Evidence pointer** Methods section, Evaluation Metrics subsection, location not provided
- **Concern** The attribution metrics are described but their properties and limitations are not thoroughly discussed. The Attribution AUC, which is based on the number of adjacent transpositions required to achieve a correct ranking, is a somewhat unusual metric. Its behavior under different conditions, such as when there are many tied attribution scores or when the number of binding atoms varies, is not analyzed. The MATR and RER metrics are more standard but their sensitivity to the choice of threshold and the distribution of true contributions is not explored. Additionally, the use of atom masking for attribution is a reasonable approach, but the manuscript does not discuss potential issues with this method, such as the effect of deleting an atom on the model's perception of the overall molecule structure.
- **Why it matters** The validity of the paper's conclusions depends on the reliability of the attribution metrics. If these metrics have undesirable properties or are not well-calibrated, the reported results may be misleading. A more thorough analysis of the metrics would strengthen confidence in the findings.
- **Resolution test** The authors should provide a more detailed analysis of their attribution metrics, including their behavior on synthetic examples with known ground truth, their sensitivity to parameter choices, and a comparison with alternative attribution methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison fairness
- **Claim pointer** The comparison between PointVS and the fingerprint-based random forest models, suggesting that PointVS is better at identifying important functional groups.
- **Evidence pointer** Results section, Performance of PointVS subsection, location not provided
- **Concern** The comparison between PointVS and the random forest models may not be entirely fair. The random forest models are trained using fingerprint representations that are designed for classification, not for attribution. The attribution scores for the random forest models are derived from the effect of deleting an atom on the model's prediction, which may not be a meaningful measure of importance for a model that operates on a fixed-length fingerprint vector. PointVS, on the other hand, operates directly on the 3D structure and may be more naturally suited to producing atom-level attributions. The paper does not address this potential confound.
- **Why it matters** If the comparison is biased, the conclusion that deep learning methods are superior for attribution may not be justified. The paper should either use a more comparable baseline or acknowledge and discuss this limitation.
- **Resolution test** The authors should consider using a fingerprint-based model that is specifically designed for interpretability, or should discuss why the random forest attribution scores are a fair basis for comparison. They could also include additional baseline methods, such as a simple distance-based model that would be expected to perform well on the synthetic tasks.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that PointVS identified important functional groups with "39% more efficiency" but does not specify the metric used or the comparison baseline. This makes the claim difficult to interpret without reading the full manuscript.
- **Required correction** Specify the metric (e.g., Attribution AUC, MATR) and the comparison baseline in the abstract, or rephrase to be more descriptive of the finding.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, Machine Learning Algorithms subsection
- **Evidence pointer** Methods section, location not provided
- **Issue** The hyperparameters for the random forest models are not specified. The number of trees, maximum depth, and other parameters can significantly affect model performance and attribution results.
- **Required correction** Provide the full hyperparameter settings for the random forest models, or state that default scikit-learn parameters were used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section, Performance of RF_PLEC models on Contribution dataset subsection
- **Evidence pointer** Results section, location not provided
- **Issue** The Spearman's rank correlation coefficients are reported for the RF_PLEC models on the Contribution dataset, but no confidence intervals or significance tests are provided. Given the small number of models tested, it is unclear whether the differences between models are meaningful.
- **Required correction** Provide confidence intervals or significance tests for the reported correlation coefficients, or acknowledge the lack of statistical power.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, Ligand-only model performance subsection
- **Evidence pointer** Results section, location not provided
- **Issue** The text states that RF_Morgan models trained on DUD-E datasets attained "substantially better-than-random predictive accuracy" but does not provide the actual accuracy values in the main text. This information is only in Table S1, which is not provided.
- **Required correction** Include the key accuracy values in the main text or ensure that the supplementary tables are available for review.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section, Performance of PointVS subsection
- **Evidence pointer** Results section, location not provided
- **Issue** The authors note that PointVS performed slightly worse than the best RF_PLEC models on the Polar dataset but do not discuss whether this difference is practically significant. Given that the RF_PLEC models have access to the exact distance cutoff used in the binding rule, this result is not surprising and may not be a meaningful comparison.
- **Required correction** Discuss the practical significance of the performance differences and consider whether the comparison is informative given the different information available to each model.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Conclusion
- **Evidence pointer** Conclusion, location not provided
- **Issue** The conclusion states that deep learning methods "should have a greater ability to generalize to novel targets" based on the synthetic experiments. However, the synthetic tasks are far simpler than real-world binding, and the paper does not provide any evidence that the observed differences in attribution performance would translate to real-world settings.
- **Required correction** Soften the claim or provide additional evidence, such as experiments on real-world datasets, to support the generalizability conclusion.

- **Technical failings that need to be addressed before the case is established** The primary technical failing is the lack of access to the figures and tables that contain the core experimental results. Without these, the quantitative claims cannot be verified. Additionally, the definition of the "efficiency" metric used for the 39% improvement claim is unclear. The manuscript also lacks a thorough analysis of the attribution metrics' properties and a discussion of the fairness of the comparison between PointVS and the fingerprint-based models.

- **Assessment against Nature-style criteria** 
  - Originality: The synthetic benchmarking framework is a novel contribution. While prior work has used synthetic data for evaluating ML models, the specific focus on attribution performance and the design of binding rules to test spatial understanding is original.
  - Scientific importance: The question of whether ML models learn meaningful interactions or exploit biases is of significant importance to the field of computational drug discovery. The paper addresses this question in a controlled setting, which is valuable.
  - Interdisciplinary readership: The work is primarily of interest to computational chemists and machine learning researchers working on drug discovery. The methods and findings are unlikely to attract a broader interdisciplinary audience.
  - Technical soundness: The experimental design is generally sound, but the lack of access to the full results and the unclear definition of key metrics prevent a full assessment of technical soundness.
  - Readability for nonspecialists: The manuscript is written in a technical style that assumes familiarity with virtual screening, fingerprint representations, and graph neural networks. It would be challenging for a nonspecialist to follow.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising framework and addresses an important question, but the core quantitative claims cannot be verified without the missing figures and tables. The methodological concerns regarding metric definitions and comparison fairness also need to be addressed. The authors should be encouraged to resubmit a revised version with the full experimental results and a more thorough analysis.