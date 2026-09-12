## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract
- **Shared manuscript claim summary** The authors present a machine learning framework that uses local geometric features derived from RNA tertiary structures to predict capsid protein binding sites in single-stranded RNA viruses, using the Qbeta bacteriophage as a proof-of-concept system. The neural network achieves an AUC of 0.88 in 5-fold cross-validation using experimental structures and an AUC of 0.75 using AlphaFold-predicted structures.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or results sections provided
- **Missing materials affecting confidence** Full manuscript, including methods description, dataset details, feature definitions, model architecture, cross-validation procedure, and all figures/tables

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting computational approach to a challenging problem in virology. The concept of using local geometric features from RNA structures for capsid binding site prediction is novel, and the reported performance metrics are promising. However, the abstract alone provides insufficient detail to evaluate the technical soundness, reproducibility, or generalizability of the work. Critical information about dataset construction, feature engineering, model validation, and statistical rigor is absent.
- **Who would be interested in the results, and why** Researchers in structural virology, RNA biology, and computational biology would be interested. The work addresses a bottleneck in understanding viral genome packaging, which is relevant to antiviral drug development and synthetic virology. The machine learning approach could also interest the broader bioinformatics community working on RNA-protein interaction prediction.
- **Major strengths** 1) Addresses an important and experimentally challenging problem (identification of capsid protein binding sites in RNA genomes). 2) Novel integration of RNA tertiary structural modeling with geometric feature extraction for this specific prediction task. 3) Demonstrates predictive performance using both experimental and predicted RNA structures, suggesting practical applicability.
- **Major Concerns** 
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset and ground truth
- **Claim pointer** "We constructed a benchmark dataset of experimentally identified binding and non-binding RNA fragments."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not describe the size, composition, or source of the benchmark dataset. It is unclear how many binding and non-binding fragments were used, how non-binding sites were defined (e.g., random genomic regions, experimentally validated negatives, or assumed negatives), and whether the dataset is balanced or imbalanced. The definition of "non-binding" is critical for classifier training and evaluation.
- **Why it matters** Without this information, the reported AUC of 0.88 cannot be properly interpreted. A small or imbalanced dataset, or one with poorly defined negative examples, could inflate performance metrics. The generalizability of the model depends entirely on the quality and representativeness of the training data.
- **Resolution test** Provide the full dataset description in the manuscript, including: number of positive and negative examples, criteria for defining non-binding sites, experimental methods used to establish binding status, and any data splitting or stratification procedures.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation and overfitting
- **Claim pointer** "the neural network showed a strong ability to distinguish capsid protein binding sites from non-binding RNA fragments, achieving an area under the receiver operating characteristic curve (AUC) of 0.88 in a 5-fold cross-validation"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract reports only a single performance metric (AUC) from 5-fold cross-validation. There is no mention of held-out test sets, independent validation, or assessment of variance across folds. The phrase "repeatedly trained and tested with these geometric descriptors on different subsets" is ambiguous and does not clarify whether the same data were used for feature selection, hyperparameter tuning, and evaluation.
- **Why it matters** Without proper separation of training, validation, and test data, the reported AUC may reflect overfitting rather than true predictive performance. The lack of confidence intervals or standard deviations across cross-validation folds prevents assessment of model stability. The field of machine learning for biological sequence analysis has well-documented pitfalls with data leakage and over-optimistic performance estimates.
- **Resolution test** Provide: (1) clear description of data partitioning (training/validation/test sets), (2) performance metrics with variance estimates across cross-validation folds, (3) results on an independent held-out test set not used in any model development step, and (4) assessment of potential data leakage (e.g., sequence similarity between training and test fragments).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability and biological scope
- **Claim pointer** "our findings provide new mechanistic insights into RNA-capsid interactions and establish a foundation for extending this approach to diverse ssRNA viruses"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The entire study is based on a single virus system (Qbeta bacteriophage). The abstract provides no evidence that the approach generalizes to other ssRNA viruses, which may have different capsid proteins, RNA structures, and packaging mechanisms. The claim of establishing a "foundation for extending this approach to diverse ssRNA viruses" is aspirational rather than supported by data.
- **Why it matters** The title and conclusions imply broad applicability, but the experimental evidence is limited to one model system. Without validation on at least one additional virus, the generalizability of the method remains unsubstantiated. The mechanistic insights claimed may be specific to Qbeta or to bacteriophages in general.
- **Resolution test** Either: (1) provide validation data from at least one additional ssRNA virus (e.g., MS2, TMV, or a mammalian virus), or (2) substantially revise the claims to accurately reflect the single-virus scope of the study, and discuss specific challenges for generalization.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Feature engineering and interpretability
- **Claim pointer** "We designed a set of geometric descriptors to characterize the local structural features of the RNA backbone."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not describe what geometric descriptors were used, how many features were extracted, or how they were selected. There is no information about feature importance, redundancy, or whether the descriptors capture biologically meaningful structural properties. The phrase "local geometric features" is vague.
- **Why it matters** The novelty of the approach hinges on the geometric feature design. Without understanding what features drive predictions, the method remains a black box. For the claimed "mechanistic insights" to be credible, the authors must demonstrate which structural features are most predictive and how they relate to known RNA-capsid interaction mechanisms.
- **Resolution test** Provide: (1) complete list and mathematical definition of all geometric descriptors, (2) feature importance analysis (e.g., SHAP values, permutation importance), (3) discussion of which features are most predictive and their biological interpretation, and (4) assessment of feature redundancy and dimensionality.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparison to existing methods
- **Claim pointer** "identification of capsid protein binding sites in the RNA genome remains challenging... motivating the development of computational approaches"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not compare the proposed method to any existing computational approaches for RNA-protein binding site prediction. There is no baseline comparison, no discussion of how the method performs relative to sequence-based or structure-based alternatives, and no justification for why a new method is needed.
- **Why it matters** Without comparative evaluation, it is impossible to assess whether the proposed method offers any advantage over existing tools. The field already has several methods for predicting RNA-protein interactions (e.g., RNABindR, PRIdictor, RPI-Pred). The authors must demonstrate that their geometric feature approach outperforms or complements these methods.
- **Resolution test** Provide: (1) benchmarking against at least 2-3 existing methods on the same dataset, (2) discussion of cases where the geometric approach succeeds or fails compared to sequence-based methods, and (3) clear articulation of the unique advantages of the proposed approach.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and reproducibility
- **Claim pointer** "the classifier retained considerable predictive performance (AUC = 0.75)"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract reports that AlphaFold-predicted structures yield an AUC of 0.75, but provides no statistical comparison to the 0.88 AUC from experimental structures. There is no confidence interval, p-value, or effect size to assess whether this drop is significant. The phrase "considerable predictive performance" is subjective and not quantitatively justified.
- **Why it matters** The claim that predicted structures retain "biologically meaningful information" depends on demonstrating that the performance is significantly better than random (AUC = 0.5) and that the degradation from experimental structures is acceptable. Without statistical testing, the reader cannot evaluate whether the 0.75 AUC is meaningful or merely reflects chance given the dataset characteristics.
- **Resolution test** Provide: (1) confidence intervals or standard deviations for all AUC values, (2) statistical test comparing the 0.88 and 0.75 AUCs (e.g., DeLong test for ROC curves), (3) comparison to a random classifier baseline, and (4) analysis of which predictions fail and why.

## Minor Comments
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and terminology
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract uses "Qbeta;" with a semicolon, which appears to be a typographical error for "Qbeta" (the bacteriophage).
- **Required correction** Correct the typo to "Qbeta" or "Qβ" as appropriate.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract mentions a GitHub repository (https://github.com/melody144/CPBSpred) but does not state whether the code, data, and trained models are publicly available. The repository URL alone does not guarantee accessibility or completeness.
- **Required correction** State explicitly in the abstract or main text: (1) whether the code and data are publicly available, (2) under what license, and (3) whether the trained model weights are provided for reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states "the failed predictions suggest that viral genome packaging is not only governed by intrinsic RNA structural features, but also by additional dynamic factors." This interpretation is speculative and not directly supported by the data presented.
- **Required correction** Either provide evidence for the role of dynamic factors (e.g., by comparing static and dynamic structural models) or temper the claim to reflect that failed predictions may also result from limitations in the model, features, or training data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scope
- **Affected element** Title
- **Evidence pointer** Title; location not provided
- **Issue** The title claims prediction for "Single-Stranded RNA Viruses" in general, but the study only demonstrates results for one bacteriophage (Qbeta).
- **Required correction** Consider revising the title to reflect the single-virus scope, e.g., "Predicting Capsid Protein Binding Sites in the Qbeta Bacteriophage Using Machine Learning from Local Geometric Features" or add a qualifier such as "A Proof-of-Concept Study."

## Risk / unsupported claims
- "our findings provide new mechanistic insights into RNA-capsid interactions" – Unsupported; the abstract does not describe any mechanistic insights beyond the observation that static structures may be insufficient.
- "establish a foundation for extending this approach to diverse ssRNA viruses" – Unsupported; no evidence of generalization beyond Qbeta is provided.
- "the classifier retained considerable predictive performance (AUC = 0.75)" – The term "considerable" is subjective and not statistically justified without confidence intervals or comparison to baselines.
- "the failed predictions suggest that viral genome packaging is not only governed by intrinsic RNA structural features, but also by additional dynamic factors" – Speculative; alternative explanations (model limitations, feature inadequacy, data quality) are not ruled out.