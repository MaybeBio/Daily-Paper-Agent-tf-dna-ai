## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and supplementary material descriptions.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as presented in the manuscript. No external data or code verification was performed.
- **Shared manuscript claim summary** The authors propose StackCBEmbed, a stacking ensemble machine learning model that combines traditional sequence-based features with ProtT5-XL-U50 protein language model embeddings to predict protein-carbohydrate binding sites at the residue level. They claim superior performance over existing state-of-the-art methods on independent test sets TS49 and TS88, and introduce a new test set TS46.
- **Visible evidence base** Tables 1-13, Figures 1-5, Supplementary Tables S1-S3, and algorithmic descriptions in the Methods section.
- **Missing materials affecting confidence** The actual code repository was not inspected. Full hyperparameter grid search results are only in supplementary files. The exact composition of the TS46 dataset and the full list of 604 PROCARB proteins are not provided. The training/validation split details are not fully specified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely sequence-based prediction of protein-carbohydrate binding sites. The methodological combination of protein language model embeddings with a stacking ensemble is timely and of interest to the community. However, several technical concerns regarding dataset construction, evaluation methodology, and reproducibility need to be addressed before the claims of superiority over state-of-the-art methods can be fully accepted.
- **Who would be interested in the results, and why** Researchers in computational biology, bioinformatics, and glycobiology, particularly those working on protein function annotation, binding site prediction, and application of protein language models. The work may also interest developers of machine learning methods for biological sequence analysis.
- **Major strengths** The use of a pre-trained transformer-based protein language model (ProtT5-XL-U50) for feature extraction is a modern and promising approach. The stacking ensemble framework with a systematic base learner selection via mutual information is methodologically sound. The authors provide a new independent test set (TS46) and compare against multiple state-of-the-art methods. The analysis of redundancy in test sets for CAPSIF models is a valuable contribution to the field.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4.
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The application of protein language model embeddings to carbohydrate binding site prediction is novel, but the overall approach of stacking ensembles for binding site prediction is not entirely new.  
  *Scientific importance*: Moderate to high. Protein-carbohydrate interactions are biologically important, and improved prediction methods would be valuable.  
  *Interdisciplinary readership*: Moderate. The work bridges machine learning and glycobiology, but the audience may be somewhat specialized.  
  *Technical soundness*: Needs improvement. Several methodological details and evaluation practices require clarification and strengthening.  
  *Readability for nonspecialists*: Acceptable. The manuscript is generally well-written, but some sections, particularly the feature extraction and ensemble methods, may be challenging for readers without a machine learning background.
- **Recommendation posture** Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Data leakage and evaluation integrity  
- **Claim pointer** The authors claim that StackCBEmbed outperforms state-of-the-art methods on independent test sets TS49 and TS88.  
- **Evidence pointer** Section 2.1, Section 3.8, Tables 8 and 9  
- **Concern** The benchmark dataset used for training was derived from Zhao et al. and Taherzadeh et al., and the TS49 and TS88 test sets were also derived from these sources. The authors state that they removed redundant proteins with 30% sequence identity cutoff, but it is unclear whether this redundancy removal was performed jointly across the training and test sets or independently. If the training and test sets were not jointly deduplicated, there is a risk of sequence similarity between training and test proteins, which could inflate performance estimates.  
- **Why it matters** Data leakage due to sequence similarity between training and test sets is a well-known issue in protein function prediction. If not properly controlled, the reported performance metrics may not reflect true generalization to unseen proteins.  
- **Resolution test** The authors should clarify the exact procedure for redundancy removal and demonstrate that no protein in the test sets shares more than 30% sequence identity with any protein in the training set. A joint clustering step should be described.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity and reproducibility  
- **Claim pointer** The authors state that the optimal feature set was determined via incremental feature selection (IFS) using F1-score.  
- **Evidence pointer** Section 2.4, Algorithm 1, Supplementary Table S1  
- **Concern** The IFS procedure is described at a high level, but several details are missing. Specifically, it is unclear how the performance of each feature combination was evaluated during IFS. Was a separate validation set used, or was cross-validation on the training set employed? The manuscript mentions a validation set for the meta learner, but the role of this validation set in feature selection is not clear. Additionally, the criterion for stopping the IFS is not explicitly stated.  
- **Why it matters** Without a clear description of the model selection procedure, it is difficult to assess whether the reported performance is unbiased or whether overfitting to the validation set occurred during feature selection.  
- **Resolution test** The authors should provide a detailed description of the IFS procedure, including how performance was estimated, how the validation set was used, and the stopping criterion. Ideally, a nested cross-validation scheme should be used to avoid selection bias.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical significance and comparison fairness  
- **Claim pointer** The authors claim that StackCBEmbed outperforms state-of-the-art methods in terms of sensitivity and balanced accuracy.  
- **Evidence pointer** Section 3.8, Tables 8 and 9  
- **Concern** The performance comparison with state-of-the-art methods is presented without any statistical significance testing. It is unclear whether the observed differences in performance metrics are statistically significant or could be due to random variation. Additionally, for methods where the authors reproduced results (e.g., StackCBPred), it is unclear whether the same training and test protocols were used. For methods where published values were used, differences in evaluation protocols could confound the comparison.  
- **Why it matters** Claims of superiority require statistical support. Without significance testing or confidence intervals, the reader cannot assess the reliability of the reported improvements.  
- **Resolution test** The authors should perform statistical significance tests (e.g., McNemar's test for paired comparisons) or provide confidence intervals for the performance metrics. They should also clearly state the evaluation protocol for each compared method.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Dataset description and class imbalance handling  
- **Claim pointer** The authors state that the training dataset is heavily imbalanced and that they applied an ensemble random undersampling approach.  
- **Evidence pointer** Section 2.1, Section 2.6, Table 1  
- **Concern** The description of the undersampling approach is incomplete. The authors state that 10 subsampled datasets were created with varying proportions of negative samples (0.2%, 2%, 20%), but it is not clear how these proportions were chosen or how the final model combines predictions from models trained on these subsampled datasets. Additionally, the class imbalance ratio in the original training set is not explicitly stated, making it difficult to assess the severity of the imbalance.  
- **Why it matters** The handling of class imbalance is critical for binding site prediction, where positive sites are rare. An incomplete description of the balancing strategy hinders reproducibility and makes it difficult to assess the validity of the approach.  
- **Resolution test** The authors should provide a detailed description of the undersampling procedure, including the rationale for the chosen proportions, how predictions from the 10 models are combined, and the exact class imbalance ratio in the training set.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of writing  
- **Affected element** Section 2.2, Feature Extraction  
- **Evidence pointer** Section 2.2  
- **Issue** The description of the Yeo-Johnson transformation and standardization is brief. It is unclear whether these transformations were applied to all features or only to specific ones.  
- **Required correction** Clarify which features were transformed and whether the transformation parameters were estimated on the training set only.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness of results  
- **Affected element** Section 3.1, Table 2  
- **Evidence pointer** Section 3.1, Table 2  
- **Issue** The comparison of different protein language model embeddings is presented only as averaged results across 10 predictors. It would be informative to see the variance or standard deviation of these results.  
- **Required correction** Report standard deviations or confidence intervals for the performance metrics in Table 2.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Section 2.7, Hyperparameter tuning  
- **Evidence pointer** Section 2.7, Table 6  
- **Issue** The hyperparameter tuning procedure is described, but the exact search ranges for the grid search are not provided in the main text.  
- **Required correction** Provide the full grid search ranges in the main text or refer clearly to the supplementary material where they are available.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation of results  
- **Affected element** Section 3.8, Tables 8 and 9  
- **Evidence pointer** Section 3.8, Tables 8 and 9  
- **Issue** The authors note that the performance of CAPSIF models may be overestimated due to redundancy, but they do not provide a similar analysis for PS-G and PS-S, whose training sets were not available.  
- **Required correction** Discuss the potential impact of unknown training sets for PS-G and PS-S on the comparison and interpret their results with appropriate caution.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Availability of resources  
- **Affected element** Availability of data and materials  
- **Evidence pointer** Section "Availability of data and materials"  
- **Issue** The authors state that the model and scripts are available on GitHub, but no version number or DOI is provided.  
- **Required correction** Provide a versioned release or a DOI for the code repository to ensure long-term accessibility and reproducibility.

## Risk / unsupported claims
- The claim that this is the first application of a protein language model to protein-carbohydrate binding site prediction is not fully supported, as the authors do not provide a comprehensive literature search to rule out prior work.
- The claim that StackCBEmbed outperforms state-of-the-art methods is not statistically substantiated.
- The performance of PS-G and PS-S is reported without knowledge of their training sets, making the comparison potentially unfair.
- The TS46 dataset is described as novel, but its full composition and the criteria for inclusion are not provided, limiting its utility for future benchmarking.
- The statement that deep learning models did not yield promising results is based on supplementary tables that are not fully described in the main text, making this claim difficult to evaluate.