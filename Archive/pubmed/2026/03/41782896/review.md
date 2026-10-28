## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary figure/table references
- **Assessment boundary** Technical soundness of the deep learning architecture, validity of the evaluation methodology for known and unknown transcription factors, robustness of the dataset construction, and support for the central claim that the model can predict gene regulation for unknown TFs
- **Shared manuscript claim summary** The authors present GReNIMJA, a deep learning model that mixes features from TF amino acid sequences and target gene nucleotide sequences using a 2D LSTM architecture, to predict the presence or absence of gene regulatory relationships. The model reportedly achieves 84.4% accuracy for known TFs and 68.5% accuracy for unknown TFs, a task the authors state is unsolved by conventional deep learning models.
- **Visible evidence base** Abstract, full methods section, results section with references to Tables 1-5 and Figures 1-5, discussion section, supplementary figure and table references
- **Missing materials affecting confidence** Actual tables and figures are not provided in the submitted material; supplementary figures and tables referenced (Supplementary Figs S1-S10, Tables S1-S2) are not available; exact dataset construction details for negative sampling are partially described but require the supplementary material for full assessment; hyperparameter values from tuning are referenced but not shown

## Reviewer
- **Overall assessment** The manuscript addresses a genuinely important problem in gene regulatory network inference: predicting regulatory relationships for transcription factors that are not present in the training data. The proposed architecture, which mixes TF amino acid sequence features with target gene nucleotide sequence features via a 2D LSTM, is a reasonable and potentially novel approach. However, the manuscript as provided has several critical gaps that prevent full evaluation of the claims. The most significant concerns relate to the evaluation methodology for unknown TFs, the construction of negative samples, the lack of clarity on how the 2D LSTM mixing is implemented, and the absence of the actual results tables and figures. The claim of 68.5% accuracy for unknown TFs is the central contribution, but the provided text does not adequately describe the experimental setup for this evaluation, nor does it provide sufficient comparison with appropriate baselines. The work is potentially publishable if these technical concerns are addressed, but the case is not fully established from the provided evidence.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, transcription factor binding prediction, and deep learning applications in genomics would be the primary audience. Researchers developing methods for predicting TF binding sites or regulatory relationships in less-studied organisms or for uncharacterized TFs would find the approach relevant. The work may also interest experimental biologists seeking computational prioritization of candidate TF-gene regulatory relationships, particularly for TFs without known binding motifs.

- **Major strengths**
  1. The problem addressed is important and timely: predicting regulatory relationships for unknown TFs is a genuinely unsolved problem, and the authors correctly identify this gap in existing deep learning approaches.
  2. The architectural choice to mix TF amino acid sequence features with target gene nucleotide sequence features is conceptually sound and biologically motivated, as TF DNA-binding specificity is determined by amino acid sequence.
  3. The authors include multiple evaluation metrics (accuracy, AUROC, AUPR, F-measure, MCC) and compare against several baseline methods, which is methodologically thorough.
  4. The feature interpretation analysis (activation of known DNA-binding domains, AT content focus) provides biological validation that the model learns meaningful features.
  5. The authors acknowledge limitations of their dataset, including potential false positives and negatives from the source databases, and discuss the trade-off between interpretability and performance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design for unknown TF evaluation
- **Claim pointer** The central claim that the model can predict gene regulation for unknown TFs with 68.5% accuracy
- **Evidence pointer** Section "Evaluation of model performance for unknown TFs", Table 5
- **Concern** The description of how unknown TFs were evaluated is critically underspecified. The text states that TFs in the test dataset were "completely unseen" and that TFs were divided into training (597), validation (30), and test (70) sets, but the exact procedure for ensuring the model has no information about test TFs is not fully described. Specifically, it is unclear whether the word2vec embedding model was trained on amino acid sequences from all TFs including those in the test set. If the embedding model was pre-trained on sequences from test TFs, then the model has indirect access to information about these TFs through the embedding vectors, which would compromise the claim of predicting for "unknown" TFs. Additionally, the text does not describe how the negative pairs for unknown TFs were constructed, which is critical for interpreting the 68.5% accuracy figure.
- **Why it matters** The entire novelty of the work rests on the claim that the model can generalize to TFs not seen during training. If the embedding layer was trained on all TF sequences, the evaluation does not truly test generalization to unknown TFs, and the 68.5% accuracy may be inflated. Without a clear description of the negative sampling strategy for unknown TFs, the accuracy metric is difficult to interpret, as the baseline accuracy would depend heavily on the ratio of positive to negative pairs.
- **Resolution test** The authors must clarify whether the word2vec embedding model was trained on sequences from test TFs, and if so, they must retrain the embeddings excluding test TFs and re-evaluate. They must also describe the exact procedure for constructing negative pairs for unknown TFs, including the ratio of positive to negative pairs and whether the negative pairs were matched for any confounding variables such as gene expression level or chromatin state.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset construction and negative sampling
- **Claim pointer** The claim that the model achieves high accuracy in predicting gene regulatory relationships, supported by the dataset of 3,383,776 pairs
- **Evidence pointer** Section "Dataset", Section "Evaluation of model performance for known TFs"
- **Concern** The dataset construction is described in limited detail. The authors state that they collected 2,674,639 pairs from DoRothEA and Harmonizome, removed duplicates and low-confidence entries, and obtained 1,806,075 positive pairs. They then "shuffled the TFs and genes and assigned negative labels to the shuffled pairs for which the gene regulatory relationship was not detected." This negative sampling strategy is problematic for several reasons. First, the number of negative pairs (1,577,701) is close to the number of positive pairs, but the text does not explain how this specific number was chosen. Second, random shuffling of TFs and genes may create negative pairs that are biologically implausible or that contain TFs and genes that are not expressed in the same cell type, which could make the classification task artificially easy. Third, the text does not describe whether the negative pairs were filtered to remove any that might actually be true regulatory relationships not captured in the databases.
- **Why it matters** The validity of the performance metrics depends entirely on the quality of the negative samples. If negative pairs are trivially distinguishable from positive pairs due to sequence composition biases or other artifacts, the reported accuracy, AUROC, and AUPR values will be inflated and not reflective of real-world performance. The authors themselves acknowledge that the databases may have false positives and false negatives, but they do not describe any mitigation strategies for the negative sampling.
- **Resolution test** The authors must provide a more detailed description of the negative sampling procedure, including how the number of negative pairs was determined, whether any filtering was applied to remove potentially true positive pairs from the negative set, and whether the negative pairs were matched for confounding factors. They should also perform a sensitivity analysis using alternative negative sampling strategies, such as sampling TFs and genes that are known to be expressed in different cell types or tissues.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline comparisons and evaluation fairness
- **Claim pointer** The claim that GReNIMJA outperforms conventional models, including PWMScan, SVM, LR, XGBoost, DeepRAM, TBiNet, and CacPred
- **Evidence pointer** Section "Evaluation of model performance for known TFs", Tables 1 and 2
- **Concern** The comparison with baseline methods raises several concerns. First, for DeepRAM, the authors state that they "randomly selected 44 TFs from the 697 TFs in the dataset" due to computational constraints. This subsampling makes the comparison with GReNIMJA, which was evaluated on all 70 test TFs, potentially unfair, as the performance on 44 TFs may not be representative. Second, for PWMScan, the authors state that TFs not included in the JASPAR database were excluded from the test dataset, which means the comparison was performed on a different test set than for the other methods. Third, the text does not describe how hyperparameters were selected for the baseline methods, other than for GReNIMJA. If baseline methods were not properly tuned, the comparison may be biased in favor of GReNIMJA.
- **Why it matters** The claim of superiority over existing methods is a key part of the paper's contribution. If the baseline methods were evaluated under suboptimal conditions, the comparison is not fair, and the reported improvements may not hold in practice. The use of different test sets for different baselines makes the results difficult to interpret and compare.
- **Resolution test** The authors must evaluate DeepRAM on the same set of 70 test TFs as GReNIMJA, or at minimum report performance on the full test set. For PWMScan, they should either evaluate on the full test set using a different approach for TFs without JASPAR motifs, or clearly report the results separately for the subset of TFs with known motifs. They should also describe the hyperparameter tuning procedure for all baseline methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical significance and variance of results
- **Claim pointer** The claim that GReNIMJA outperforms conventional models in "almost all evaluation metrics"
- **Evidence pointer** Section "Evaluation of model performance for known TFs", Tables 1 and 2
- **Concern** The manuscript does not report any measures of variance or statistical significance for the performance metrics. It is unclear whether the reported improvements are consistent across multiple runs with different random seeds, or whether they could be due to chance. The text mentions five-fold cross-validation for model selection, but the final evaluation on the test set appears to be a single run. No confidence intervals, standard deviations, or statistical tests are reported.
- **Why it matters** Deep learning models can exhibit significant variance across training runs due to random initialization and stochastic optimization. Without reporting variance or statistical significance, the reader cannot assess whether the observed improvements are reliable or within the range of expected variability.
- **Resolution test** The authors should report the mean and standard deviation of all metrics across multiple runs (e.g., 5-10 runs with different random seeds) and perform appropriate statistical tests (e.g., paired bootstrap or Wilcoxon signed-rank test) to assess whether the differences between GReNIMJA and baseline methods are statistically significant.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of unknown TF prediction
- **Claim pointer** The claim that the model can predict gene regulation for unknown TFs by leveraging feature similarity to learned TFs
- **Evidence pointer** Section "Evaluation of model performance for unknown TFs", Section "Feature analysis of the trained model", Figure 4
- **Concern** The analysis of unknown TF prediction relies on the assumption that the model learns features that generalize across TF families. The homology analysis (Figure 4) shows that neighboring TFs in the learned feature space have high sequence similarity at a rate of 10-20% for unknown TFs, which the authors interpret as evidence that the model uses similarity-based generalization. However, this rate seems relatively low, and the text does not provide a clear threshold for what would constitute sufficient similarity for reliable prediction. Additionally, the manuscript does not analyze whether prediction accuracy for unknown TFs varies systematically with the degree of similarity to known TFs, which would be a more direct test of the proposed mechanism.
- **Why it matters** The practical utility of the model depends on its ability to make reliable predictions for TFs that are truly novel, not just those that are similar to known TFs. If the model only works well for TFs with close homologs in the training set, its applicability to truly uncharacterized TFs would be limited.
- **Resolution test** The authors should stratify the unknown TF test results by sequence similarity to the training set (e.g., bins of percent identity) and show how accuracy varies with similarity. They should also consider a more challenging evaluation where unknown TFs are selected to be maximally dissimilar to all training TFs.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction contain some awkward phrasing and grammatical errors. For example, "GReNIMJA was designed, not to predict the specific TFs from genes, but to predict whether the regulatory relationships exist or not from both of the amino acid sequences of TFs and nucleotide sequences of regulatory region of target genes" is convoluted. The phrase "the highest accuracy (0.844) indicated that the model was the most accurate at predicting gene regulatory relationships" is redundant.
- **Required correction** The authors should revise the abstract and introduction for clarity and conciseness. The sentence describing the model design should be restructured to more clearly state that the model takes both TF amino acid sequences and target gene sequences as input and outputs a binary classification of whether a regulatory relationship exists.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, hyperparameter tuning
- **Evidence pointer** Section "Training procedure"
- **Issue** The hyperparameter tuning procedure is described as using Optuna with Bayesian optimization, and the tuned hyperparameters are said to be in Supplementary Table S1. However, the specific hyperparameter search space is not described in the main text, and the final hyperparameter values are not reported in the main text.
- **Required correction** The authors should provide a brief summary of the hyperparameter search space and the final selected values in the main text, even if the full details are in the supplementary material.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of evaluation metrics
- **Affected element** Section "Evaluation of model performance for known TFs"
- **Evidence pointer** Section "Evaluation of model performance for known TFs", Tables 1 and 2
- **Issue** The text states that "the average of the evaluation metrics for all test data" was calculated, and also that "the average of the evaluation metrics for each TF in the test data" was calculated. It is unclear what the difference is between these two calculations and which one is reported in Tables 1 and 2.
- **Required correction** The authors should clarify the distinction between these two averaging procedures and clearly state which one is reported in each table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion of limitations focuses primarily on the trade-off between interpretability and performance, and the potential biases in the source databases. However, the authors do not discuss the limitation that the model only uses sequence information and does not incorporate other relevant data types such as chromatin accessibility, DNA methylation, or 3D genome structure, which are known to influence gene regulation.
- **Required correction** The authors should add a brief discussion of this limitation and how it might be addressed in future work.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 5
- **Evidence pointer** Section "Visualization of GRNs using adjacency matrices", Figure 5
- **Issue** The description of Figure 5 is brief and does not explain what the reader should observe in the adjacency matrices. It is unclear whether the clustering patterns are expected to differ between the models and what the biological interpretation of the clustering should be.
- **Required correction** The authors should expand the description of Figure 5 in the results section to explain what patterns are visible and how they support the claim that the model learns TF-gene interactions rather than relying solely on CpG content.

## Risk / unsupported claims
- The claim of 68.5% accuracy for unknown TFs is not fully supported by the provided evidence, as the evaluation methodology is underspecified and the actual results table (Table 5) is not provided.
- The claim that the model "learned the decision boundary of a gene regulatory relationship by using the biological domain context as a basis for the prediction" is only weakly supported by the feature activation analysis, which identified 11 activated TF domains but also found biologically implausible activations (e.g., plant-specific domains in what appears to be a human dataset).
- The claim that the model "might have learned latent representations that reflect the homology among TFs" is speculative and not directly tested.
- The statement that the dataset has "low sequence similarity and the risk of data leakage is minimal" is based on a comparison of mean alignment scores, but the interpretation of these scores is not well explained, and the threshold for "low" similarity is not defined.
- The claim that GReNIMJA "can also predict the presence or absence of gene regulatory relationships on the basis of biological domain knowledge" is not directly demonstrated; the analysis shows correlation with known domains but does not establish causal use of this information.