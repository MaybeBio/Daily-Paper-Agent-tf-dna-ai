## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusions) and metadata (title, authors, journal, DOI, URL)
- **Assessment boundary** Scientific and technical evaluation of the manuscript as submitted to PeerJ Computer Science; no comparison to other journals or editorial decisions
- **Shared manuscript claim summary** The authors present a machine learning framework (Hi-ChIP-ML) that predicts chromatin folding patterns in Drosophila melanogaster using epigenetic features. They compare linear regression with regularization, gradient boosting, and bidirectional LSTM RNNs across three cell lines, and report that the biLSTM model achieves the best performance. They identify Chriz and H3K4me2 as the most informative features for predicting TAD-related chromatin states.
- **Visible evidence base** Full text including Methods, Results, Discussion, Conclusions; references to Tables 1-3, Figures 1-6, Figure S1, Table S1, Figure S2; code repository URL
- **Missing materials affecting confidence** Actual data values (tables not shown in provided text), figure contents, supplemental files, hyperparameter search details, exact dataset sizes, computational resources, statistical significance tests, code implementation details

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in chromatin biology by applying machine learning to predict TAD-related features from epigenetic marks in Drosophila. The work is methodologically sound in its general approach, and the comparison of multiple model classes is useful. However, the manuscript has several significant weaknesses that limit its impact: the novelty is incremental relative to prior work, the evaluation metrics are limited, the feature importance analysis is somewhat superficial, and the biological interpretation of the results is not sufficiently rigorous. The claims about the superiority of biLSTM and the biological relevance of specific features are only partially supported by the evidence presented. The manuscript would benefit from more thorough validation, additional metrics, and a more critical discussion of limitations.

- **Who would be interested in the results, and why** Researchers in computational biology and genomics, particularly those working on 3D genome organization, chromatin state prediction, and machine learning applications to epigenomics. The open-source code and the comparison of different model architectures may be of practical interest to practitioners in the field. The finding that Chriz and H3K4me2 are informative for TAD prediction in Drosophila may also interest experimental biologists studying chromatin architecture.

- **Major strengths** 
  1. The use of transitional gamma as a continuous target variable is a thoughtful choice that avoids the arbitrariness of binary TAD boundary classification.
  2. The comparison of multiple model classes (linear, gradient boosting, RNN) on the same data is a reasonable approach.
  3. The code is publicly available, which supports reproducibility.
  4. The analysis across three cell lines provides some evidence for generalizability.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the biLSTM model "performed two times better than the constant prediction and outscored all trained LR and GB models" (Results section).
  - **Evidence pointer** Tables 1 and 2; location not provided
  - **Concern** The actual performance values are not shown in the provided text. The claim of "two times better" is vague and not substantiated with specific numbers, confidence intervals, or statistical significance tests. It is unclear whether the improvement is consistent across cell lines and train/test splits.
  - **Why it matters** Without quantitative results and statistical validation, the central claim of the paper (that biLSTM outperforms other models) cannot be properly evaluated. The reader cannot assess the magnitude of the improvement or its practical significance.
  - **Resolution test** Provide the actual performance values (e.g., wMSE, R², Pearson correlation) for all models and cell lines, with standard deviations across cross-validation folds. Include statistical significance tests (e.g., paired t-test or Wilcoxon test) comparing the best model to the alternatives.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "the selected set of 18 chromatin marks can be used for chromatin folding patterns prediction in Drosophila" (Results section).
  - **Evidence pointer** Tables 1 and 2; location not provided
  - **Concern** The evaluation is based solely on wMSE, a custom loss function. No other metrics (e.g., Pearson or Spearman correlation, R², mean absolute error) are reported. The wMSE is weighted to downweight errors on high-target-value bins, which may mask poor performance on those bins. It is unclear how well the models perform in absolute terms.
  - **Why it matters** A single custom metric is insufficient to establish that the models are reliable predictors. The weighting scheme may obscure systematic errors. Without additional metrics, the practical utility of the predictions cannot be assessed.
  - **Resolution test** Report multiple complementary metrics (e.g., Pearson correlation, R², MAE) and, if possible, compare predictions against a null model or a simpler baseline (e.g., genomic distance-based prediction).

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Originality
  - **Claim pointer** The authors state that "as opposed to previous approaches, we incorporate information about the region context on two levels" (Introduction).
  - **Evidence pointer** Introduction; location not provided
  - **Concern** The novelty of the approach is not clearly established. Prior work on TAD boundary prediction using machine learning (including the cited Ulianov et al. 2016 and Ramírez et al. 2018) already used epigenetic features. The use of RNNs for sequential genomic data is not new in the broader field of genomics. The specific contribution of this work relative to existing methods is not clearly articulated.
  - **Why it matters** If the methodological novelty is limited, the scientific contribution of the paper is reduced. The authors need to clearly state what is new and why it matters.
  - **Resolution test** Provide a more explicit comparison with prior methods, including a discussion of what specific limitations of previous approaches are addressed here. If possible, benchmark against a previously published model on the same data.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "the results of omitting each feature one by one while using the second dataset of features are almost identical as we expected. It could be explained by the fact that most of the features are strongly correlated" (Results section).
  - **Evidence pointer** Figure 6; location not provided
  - **Concern** The feature importance analysis is not rigorous. The drop-one-feature approach shows little effect for most features, which the authors attribute to correlation, but no correlation analysis is presented. The use-one-feature approach is also limited because it does not account for interactions between features. The conclusion that Chriz and H3K4me2 are the most important features is based on a somewhat informal analysis.
  - **Why it matters** The biological interpretation of the results depends on the feature importance analysis. If the analysis is not robust, the biological conclusions are not well supported.
  - **Resolution test** Provide a correlation matrix of the features, use a more systematic feature importance method (e.g., SHAP values or permutation importance), and test whether the identified top features are statistically significant.

  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors state that "the use of adjacent DNA bins created a meaningful biological context and enabled the training of a comprehensive ML model, strongly improving the evaluation scores of the best RNN model" (Discussion).
  - **Evidence pointer** Figure 3, Tables 1 and 2; location not provided
  - **Concern** The biological interpretation of the window size (6 bins = 120 kb) as corresponding to the typical TAD size in Drosophila is speculative. The optimal window size may be an artifact of the data or the model architecture, and the authors do not test whether the optimal window size varies across cell lines or genomic regions. The claim that the model captures "meaningful biological context" is not directly tested.
  - **Why it matters** The biological significance of the results is a key part of the paper's contribution. If the interpretation is speculative, the impact of the work is reduced.
  - **Resolution test** Test the model with different window sizes and show that the optimal size is consistent across cell lines. Provide additional evidence that the window size corresponds to a biological feature (e.g., compare with TAD size distributions from Hi-C data).

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Abstract
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract does not mention the specific performance metrics or the magnitude of the improvement. It also does not mention the limitations of the study.
  - **Required correction** Include a brief quantitative summary of the results and a sentence on limitations.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, hyperparameter selection
  - **Evidence pointer** Methods section, "Machine learning models"; location not provided
  - **Issue** The hyperparameter search for the biLSTM is described only briefly. It is unclear how many hyperparameter combinations were tested, what the search range was, and how overfitting was avoided.
  - **Required correction** Provide a more detailed description of the hyperparameter search, including the range of values tested and the selection criterion.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Data preprocessing
  - **Evidence pointer** Methods section, "Data"; location not provided
  - **Issue** The description of the ChIP-chip data processing is incomplete. It is unclear how the raw signals were converted to the features used in the models, and whether any batch effects or technical variability were addressed.
  - **Required correction** Provide more details on data preprocessing, including normalization steps, handling of missing values, and any quality control measures.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Discussion
  - **Evidence pointer** Discussion; location not provided
  - **Issue** The discussion of the biological implications is somewhat speculative and not well connected to the specific results. For example, the claim that H3K4me2 is important because it defines transcription factor binding regions is not directly supported by the data presented.
  - **Required correction** Strengthen the connection between the computational results and the biological interpretation, and clearly distinguish between findings and speculation.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Code availability
  - **Evidence pointer** Abstract, Conclusions; location not provided
  - **Issue** The code is stated to be publicly available, but there is no mention of the software environment, dependencies, or instructions for reproducing the results.
  - **Required correction** Provide a brief description of the software environment and dependencies, and include instructions for running the pipeline.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative results and statistical validation), R1-M2 (insufficient evaluation metrics)

## Risk / unsupported claims
- The claim that biLSTM "performed two times better than the constant prediction" is not supported by the data shown in the provided text.
- The claim that the optimal window size of 6 bins corresponds to the typical TAD size in Drosophila is speculative and not directly tested.
- The claim that the feature importance analysis reveals "factors relevant for chromatin folding into TADs" is based on an informal analysis and is not statistically validated.
- The claim that the models are "transferable between cell lines" is based on limited evidence and no statistical comparison across cell lines.
- The claim that the framework "may be adapted to any similar biological dataset" is not supported by any demonstration of generalizability beyond the specific datasets used.