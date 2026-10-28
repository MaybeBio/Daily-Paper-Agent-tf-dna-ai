## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, proposed model, performance metrics, results, discussion, conclusion)
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, reproducibility, and alignment with stated objectives
- **Shared manuscript claim summary** The authors propose GMean, a hybrid semi-supervised model combining a gated recurrent unit (GRU) and K-means clustering, to predict transcription factor binding sites in unlabelled DNA sequences. The model is evaluated on ENCODE-derived datasets (GM12878, K562, HepG2) using accuracy, precision, recall, and F1-score, with reported accuracies ranging from 88.80% to 91.85%.
- **Visible evidence base** Abstract, introduction, materials and methods, proposed model description, performance metrics definitions, results tables (Tables 3–6), and figures (Figures 1–5) referenced in text
- **Missing materials affecting confidence** No code, hyperparameter settings, training curves beyond accuracy/loss, statistical significance tests, baseline comparisons with existing TF binding site predictors, or detailed dataset characteristics (e.g., sequence length, class balance verification) are provided

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in bioinformatics, namely reducing reliance on labelled data for TF binding site prediction. The idea of combining a GRU with K-means in a semi-supervised framework is conceptually interesting. However, the current presentation has substantial methodological gaps, unclear experimental design, and insufficient evidence to support the claimed effectiveness. The results are reported without statistical validation or comparison to established methods, and several technical details are ambiguous or potentially erroneous. The case for novelty and practical utility is not convincingly established from the provided material.
- **Who would be interested in the results, and why** Researchers working on computational prediction of transcription factor binding sites, particularly those interested in semi-supervised or hybrid deep learning approaches. The potential to reduce labelled data requirements could appeal to those in regulatory genomics and genome annotation. However, interest would be conditional on stronger validation and clearer methodological presentation.
- **Major strengths**
  - Addresses a practical problem: reducing labelled data dependency in TF binding site prediction.
  - The hybrid architecture (GRU + K-means) is a reasonable and potentially useful combination.
  - The use of k-mer tokenization is appropriate for DNA sequence representation.
  - The paper is generally readable and the structure is logical.
- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: Yes)
  - **R1-M4** (Blocking: Yes)
  - **R1-M5** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
  - **R1-m6**
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**
  - **Originality** The combination of GRU and K-means in a semi-supervised pipeline is not entirely novel, as similar hybrid approaches exist in other domains. The specific application to TF binding sites is a modest extension. The originality claim is weak without a clear demonstration of how this differs from prior semi-supervised or hybrid models in genomics.
  - **Scientific importance** The problem is important, but the manuscript does not demonstrate that GMean offers a meaningful advance over existing methods. No comparison to state-of-the-art TF binding site predictors is provided, so the scientific impact is not established.
  - **Interdisciplinary readership** The topic sits at the intersection of machine learning and genomics, which has broad appeal. However, the presentation assumes familiarity with both fields without sufficient context for either audience. The lack of biological validation or interpretation of predicted binding sites limits cross-disciplinary interest.
  - **Technical soundness** There are significant technical concerns, including potential errors in the GRU equations, unclear handling of unlabelled data, missing hyperparameter details, and no statistical analysis of results. The technical foundation is not sufficiently rigorous.
  - **Readability for nonspecialists** The manuscript is readable in structure but contains jargon and inconsistencies that would confuse nonspecialists. Key concepts such as the semi-supervised mechanism and the role of K-means are not explained clearly enough for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revisions to address methodological clarity, experimental rigor, and comparative validation before the claims can be supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that GMean is a semi-supervised model that uses labelled data for training and unlabelled data for testing and prediction, with K-means used to predict unlabelled sequences.
- **Evidence pointer** Section "The proposed model (GMean)", Section "K-means clustering", location not provided
- **Concern** The semi-supervised mechanism is not clearly described. It is unclear how K-means is applied to the unlabelled data. Specifically, does K-means operate on the latent representations from the GRU? If so, how are cluster assignments mapped to class labels (0 or 1)? The paper states that the number of clusters is set to two, but it does not explain how the clusters correspond to the two classes. Without this clarification, the semi-supervised claim is not substantiated.
- **Why it matters** The core contribution of the paper is the semi-supervised approach. If the mechanism is not clearly defined and justified, the novelty and utility of the method cannot be evaluated.
- **Resolution test** The authors should provide a detailed algorithmic description of how K-means is integrated with the GRU, including how cluster labels are assigned to classes, how the number of clusters is determined, and how the unlabelled data are used in the prediction phase. A step-by-step pseudocode or flowchart would be helpful.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors present GRU equations in Section "Gated recurrent unit" and claim they are used to learn and extract motifs from labelled DNA sequences.
- **Evidence pointer** Section "Gated recurrent unit", equations (1), location not provided
- **Concern** The GRU equations appear to contain errors. Specifically, the candidate hidden state equation is written as \hat{C}_t = tanh(W_C x_t + V_C(r_t . h_{t-1}, x_t)), which is not a standard GRU formulation. The notation is ambiguous and likely incorrect. The hidden state is denoted as t_t, which is unconventional and confusing. These errors undermine the technical credibility of the model description.
- **Why it matters** Accurate mathematical formulation is essential for reproducibility and for readers to understand the model. Errors in the core equations suggest a lack of rigor in the manuscript.
- **Resolution test** The authors should correct the GRU equations to match standard formulations (e.g., those in the original GRU paper by Cho et al.) and ensure all variables are clearly defined. The hidden state should be denoted consistently, and the candidate hidden state equation should be corrected.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental rigor
- **Claim pointer** The authors claim that GMean achieves high accuracy (up to 91.85%) in predicting TF binding sites across different datasets.
- **Evidence pointer** Section "Result and discussion", Tables 3–6, location not provided
- **Concern** The experimental evaluation is insufficient. No statistical significance tests (e.g., confidence intervals, p-values) are reported. The results are presented as single values without variance or repeated runs. Additionally, there is no comparison to existing TF binding site prediction methods, which is essential to demonstrate the advantage of GMean. The authors also do not report the number of training epochs, batch size, learning rate, or other hyperparameters, making the results difficult to reproduce.
- **Why it matters** Without statistical validation and comparison to baselines, the reported accuracies could be due to chance or dataset-specific artifacts. The lack of reproducibility details undermines the reliability of the findings.
- **Resolution test** The authors should include multiple runs with standard deviations, perform statistical tests (e.g., paired t-tests or Wilcoxon signed-rank tests) against baseline methods, and provide full hyperparameter settings. They should also compare GMean to at least one or two established TF binding site predictors.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Data and preprocessing
- **Claim pointer** The authors state that the dataset includes 16,000 labelled and 4,000 unlabelled DNA sequences, with labels 0 and 1 representing GM12878 and K562, respectively.
- **Evidence pointer** Section "Materials and methods", location not provided
- **Concern** The dataset description is incomplete. The authors do not specify the length of the DNA sequences, the number of positive and negative samples in the labelled set, or how the unlabelled data were selected. The claim that the dataset is balanced is stated but not verified. Additionally, the source of the data is cited as reference 12, but the authors do not describe any preprocessing steps beyond k-mer tokenization, such as filtering, normalization, or handling of class imbalance.
- **Why it matters** Incomplete dataset details prevent readers from assessing the generalizability of the results and reproducing the experiments. The class balance claim is important for interpreting accuracy as a meaningful metric.
- **Resolution test** The authors should provide a detailed description of the dataset, including sequence length, class distribution, and any preprocessing steps. They should also verify the class balance with actual counts.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Clarity of claims
- **Claim pointer** The authors claim that GMean is "feasible and effective" based on the reported accuracies.
- **Evidence pointer** Section "Result and discussion", Section "Conclusion and future work", location not provided
- **Concern** The claim of effectiveness is overstated given the lack of comparison to baselines and the acknowledged overfitting issue. The authors note that overfitting occurs despite dropout, which suggests the model may not generalize well. The conclusion that GMean is "feasible and effective" is not fully supported by the evidence presented.
- **Why it matters** Overstated claims can mislead readers and detract from the credibility of the work. A more nuanced interpretation of the results is needed.
- **Resolution test** The authors should temper their claims and discuss the overfitting issue in more depth, including potential remedies. They should also clearly state the limitations of their evaluation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states "The experimental results show that GMean is feasible and effective in predicting deoxyribonucleic acid sequences, as the highest accuracy is 91.85% in predicting K562 and HepG2." This sentence is grammatically awkward and could be clearer.
- **Required correction** Rephrase for clarity, e.g., "The experimental results demonstrate that GMean is feasible and effective, achieving the highest accuracy of 91.85% when predicting K562 and HepG2 sequences."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section "Performance metrics"
- **Evidence pointer** Section "Performance metrics", Table 2, location not provided
- **Issue** The confusion matrix in Table 2 is incorrectly described. The text states "False positive (TP) is predicted correctly and is actually negative," which is a typo. It should read "False positive (FP) is predicted positive but is actually negative."
- **Required correction** Correct the typo in the description of the confusion matrix elements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section "The proposed model (GMean)"
- **Evidence pointer** Section "The proposed model (GMean)", location not provided
- **Issue** The authors mention that the model is implemented using the Keras library but do not provide details on the optimizer, loss function, or training configuration.
- **Required correction** Add a brief description of the optimizer, loss function, batch size, and number of epochs used in the experiments.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section "Result and discussion"
- **Evidence pointer** Section "Result and discussion", location not provided
- **Issue** The text in Section "Performance comparison with different type of datasets" contains a stray quotation mark: "Overfitting occurred as the highest accuracy during the training and validation phases were 93.46% and 92.12%, respectively”." This appears to be a formatting error.
- **Required correction** Remove the stray quotation mark and ensure proper punctuation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section "Conclusion and future work"
- **Evidence pointer** Section "Conclusion and future work", location not provided
- **Issue** The conclusion is brief and does not summarize the key findings or discuss broader implications. It also ends with a stray quotation mark.
- **Required correction** Expand the conclusion to summarize the main results, acknowledge limitations, and suggest concrete future directions. Remove the stray quotation mark.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** References
- **Affected element** Reference 12
- **Evidence pointer** Section "Materials and methods", location not provided
- **Issue** The dataset is cited as reference 12, but the reference list is not provided in the manuscript text. It is unclear whether the dataset is publicly available and how it was processed.
- **Required correction** Ensure the reference is complete and accessible, and briefly describe the dataset source and any relevant accession numbers.

## Risk / unsupported claims
- The claim that GMean is "feasible and effective" is not fully supported due to the lack of baseline comparisons and statistical validation.
- The semi-supervised nature of the model is not clearly demonstrated; the role of K-means in the prediction phase is ambiguous.
- The reported accuracies are presented without variance or confidence intervals, making it impossible to assess their reliability.
- The claim that the dataset is balanced is not verified with actual counts.
- The GRU equations contain apparent errors, which undermines the technical validity of the model description.
- The overfitting issue is acknowledged but not analyzed in depth, and the proposed dropout does not appear to resolve it, which raises questions about the model's generalizability.