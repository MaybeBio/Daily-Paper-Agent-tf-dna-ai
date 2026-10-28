## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, supporting information descriptions)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided text. No supplementary files, figures, tables, or code were available for inspection.
- **Shared manuscript claim summary** The authors propose a two-step computational pipeline: (1) a fine-tuned ProtBERT model to classify transcription factors (TFs) versus non-TFs, and (2) a Reduced Amino Acid Category (RAAC) plus K-mer feature encoding with an SVM classifier to distinguish TFs that preferentially bind methylated DNA (TFPMs) from those that do not. They report superior performance over existing methods on benchmark datasets, cross-species generalizability on mouse data, and biologically plausible predictions on a large human TF dataset.
- **Visible evidence base** Text descriptions of datasets, methods, and results. Tables 1-6 and Figures 1-4 are referenced but not provided. No numerical data, code, or supplementary material was accessible.
- **Missing materials affecting confidence** All tables, figures, supplementary files, code repository contents, and the actual dataset compositions. The manuscript text contains placeholders where equations and dataset criteria should appear, and these are not evaluable.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in gene regulation: computational identification of TFs that preferentially bind methylated DNA. The two-step design is reasonable, and the choice to use a lightweight feature-based classifier for the second step is defensible given small dataset sizes. However, the evidence presented in the text is insufficient to evaluate the core claims. Key methodological details are missing or incomplete, the comparison to prior work is not quantitatively substantiated in the visible text, and the biological interpretation of the top predictions is speculative. The manuscript has potential but requires substantial revision and full access to data and code before the claims can be assessed.
- **Who would be interested in the results, and why** Researchers in computational biology, epigenetics, and gene regulation would be interested. The problem of predicting TF methylation preference is of practical value for prioritizing candidates for wet-lab validation. The use of ProtBERT for TF classification and the RAAC-K-mer-SVM combination for TFPM classification may be of methodological interest to those working on protein sequence classification with limited training data.
- **Major Strengths**
  - The problem is well-motivated and practically relevant.
  - The two-step design is logical: a large-scale pretrained model for the first task, and a simpler, interpretable model for the second task where data are scarce.
  - The authors explicitly address the risk of overfitting in small datasets and justify their choice of a classical ML model over deep learning for the second step.
  - Cross-species validation is a valuable addition and strengthens the generalizability claim if the results are as reported.
  - The authors provide code and data repositories, which supports reproducibility if the contents are complete.
- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: Yes)
  - **R1-M4** (Blocking: No)
  - **R1-M5** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
  - **R1-m6**
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The combination of ProtBERT and RAAC-K-mer-SVM is novel, but each component is established. The conceptual advance is incremental.
  - **Scientific importance** Moderate. The problem is important, but the manuscript does not yet demonstrate a significant advance in understanding or methodology beyond existing tools.
  - **Interdisciplinary readership** Limited. The work is primarily of interest to computational biologists and epigenetics specialists. The biological interpretation is thin and would not attract a broad readership.
  - **Technical soundness** Not assessable from the provided text. Critical details are missing, and no data or code was available for verification.
  - **Readability for nonspecialists** The manuscript is generally readable, but the methods section contains incomplete sentences and placeholders that disrupt flow. The biological rationale for the Krueppel C2H2-type Zinc-finger family is presented without sufficient context for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revision, full provision of data and code, and clarification of methods before a fair assessment can be made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors claim their method outperforms all existing approaches on TF and TFPM classification.
- **Evidence pointer** Tables 4 and 5, location not provided
- **Concern** The manuscript text states that the proposed method outperforms existing models, but the actual numerical results are not visible in the provided material. Tables 4 and 5 are referenced but not included. Without these data, the central claim of superiority cannot be verified.
- **Why it matters** The primary contribution of the manuscript is the claimed performance improvement. If the numerical results are not available for inspection, the core claim is unsupported.
- **Resolution test** Provide the full tables with all compared methods and metrics. Include confidence intervals or statistical tests where appropriate. Ensure the comparison is fair, using identical train/test splits and evaluation protocols.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The authors describe a two-step pipeline using ProtBERT for TF classification and RAAC-K-mer-SVM for TFPM classification.
- **Evidence pointer** Materials and methods, "Identifying TFs" and "Identifying TFPMs" sections, location not provided
- **Concern** The methods section contains placeholders where equations should be, and the dataset processing criteria are described as "the following criteria" but the criteria themselves are not provided in the text. The description of the SVM hyperparameter search is incomplete, and the rationale for choosing K=1 is only qualitatively discussed. The exact feature dimensions, the number of features after RAAC reduction, and the handling of class imbalance are not described.
- **Why it matters** Reproducibility is a fundamental requirement. Without complete methodological details, other researchers cannot replicate the work or assess its validity.
- **Resolution test** Provide all equations, dataset filtering criteria, exact feature dimensions, hyperparameter ranges, and any preprocessing steps. Describe how class imbalance was handled, if at all. Include the full grid search results or at least the performance landscape around the chosen parameters.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability and validation
- **Claim pointer** The authors claim cross-species generalizability based on a mouse dataset and biological plausibility based on predictions on 1,639 human TFs.
- **Evidence pointer** Results and discussion, "Generalization of TFPM model to new data" section, Tables 5 and 6, location not provided
- **Concern** The mouse dataset is described as lacking definitive negative samples, which is acknowledged, but the implications for the reported performance are not discussed. The top 20 predictions are listed in Table 6, which is not provided. The biological interpretation relies on literature for a few examples, but no systematic analysis is presented. The claim that "most of the top 20 proteins belong to the Krueppel C2H2-type Zinc-finger family" is interesting but not quantitatively evaluated against a background distribution.
- **Why it matters** Generalizability and biological relevance are key claims. Without the actual predictions and a proper statistical evaluation, these claims remain anecdotal.
- **Resolution test** Provide the full list of predictions with scores. Perform a statistical enrichment analysis for the Krueppel C2H2-type Zinc-finger family against a suitable background. Discuss the limitations of the mouse validation given the absence of negative samples.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison fairness
- **Claim pointer** The authors state their method outperforms existing approaches, including XGBoost, Random Forest, and deep learning models.
- **Evidence pointer** Results and discussion, "TFPMs classification" section, Figure 4, location not provided
- **Concern** The comparison to existing methods is described qualitatively. It is unclear whether the same data splits, feature representations, and hyperparameter tuning were used for the baselines. The statement that "only SVM performed reliably" is vague and not supported by visible data.
- **Why it matters** Unfair or incomplete comparisons undermine the claim of superiority.
- **Resolution test** Describe the exact experimental setup for all baselines, including feature encoding, hyperparameter tuning, and cross-validation strategy. Provide the full results for all methods, not just the proposed one.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The authors suggest that the top predictions being enriched for Krueppel C2H2-type Zinc-finger proteins supports the robustness of their approach.
- **Evidence pointer** Results and discussion, "Generalization of TFPM model to new data" section, location not provided
- **Concern** The link between the Krueppel C2H2-type Zinc-finger family and DNA methylation preference is presented as known, but the cited evidence is not provided in the text. The reasoning is circular: the model predicts these proteins, and because some are known to bind methylated DNA, the model is deemed correct. A more rigorous approach would be to test the model on a held-out set of experimentally validated TFPMs.
- **Why it matters** The biological plausibility argument is used as supporting evidence for the model's validity. If the argument is weak, the model's credibility is reduced.
- **Resolution test** Provide a more rigorous validation, such as a prospective test on newly curated data or a blinded evaluation against experimental results. Discuss potential biases in the training data that could lead to overrepresentation of certain families.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states "Cross-species validation on an independent mouse dataset further demonstrates the generalizability of our proposed framework" but the sentence is incomplete, ending without a period. This is a typographical issue but affects readability.
- **Required correction** Complete the sentence and ensure proper punctuation throughout the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction
- **Evidence pointer** Introduction, location not provided
- **Issue** The term "TFPM" is used to refer to TFs that preferentially bind methylated DNA, but the abbreviation is not expanded at first use in the abstract or introduction. The definition is implied but should be explicit.
- **Required correction** Define TFPM and TFPNM at first use in both the abstract and the main text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Identifying TFs" section
- **Evidence pointer** Materials and methods, location not provided
- **Issue** The manuscript states "The experimental results suggest that a maximum sequence length (max_len) of 1000 gives the optimal AUC (Table 1)" but does not describe how this was determined or whether other lengths were tested.
- **Required correction** Describe the range of max_len values tested and the criteria for selecting 1000.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, "TFPMs classification" section
- **Evidence pointer** Results and discussion, location not provided
- **Issue** The manuscript reports sensitivity and specificity but does not report confidence intervals or statistical significance tests for the differences between methods.
- **Required correction** Add confidence intervals or statistical tests to support the claim of superiority.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "Datasets" section
- **Evidence pointer** Materials and methods, location not provided
- **Issue** The dataset processing criteria are described as "the following criteria" but the criteria are not listed in the text. This appears to be a formatting error.
- **Required correction** Insert the full list of criteria used for dataset filtering.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Multiple sections, location not provided
- **Issue** There are several typographical errors and awkward phrasings, such as "insuï¬€icient" and "simiplify" and "eï¬€icient". These do not affect scientific content but reduce professionalism.
- **Required correction** Perform a thorough language edit to correct typographical and grammatical errors.

## Risk / unsupported claims
- The claim that the proposed method outperforms all existing approaches is unsupported in the provided text because the numerical results in Tables 4 and 5 are not visible.
- The claim of cross-species generalizability is weakened by the acknowledged absence of definitive negative samples in the mouse dataset, and the implications are not discussed.
- The biological interpretation of the top 20 predictions is speculative and not supported by a statistical enrichment analysis.
- The statement that "only SVM performed reliably" is vague and not substantiated with data.
- The rationale for choosing K=1 is qualitative and not supported by a systematic comparison of K values in the visible text.
- The manuscript references a GitHub repository and supplementary files, but their contents were not available for verification, so all claims relying on them are not assessable.