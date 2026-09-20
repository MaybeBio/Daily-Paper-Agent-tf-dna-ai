## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusion. Figures and tables referenced but not provided. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific soundness, methodological clarity, validity of performance claims, reproducibility, and alignment with the stated scope of predicting single-stranded and double-stranded DNA-binding proteins.
- **Shared manuscript claim summary** The authors propose BAN-SDBPred, a deep learning framework combining ESM2 and ProtT5 protein language model embeddings with RECM-HOG local structural features, fused via a bilinear attention network, and trained with an adaptive neighborhood-based sampling (ANBS) strategy to address class imbalance. They report improved performance over existing predictors on independent test data.
- **Visible evidence base** Text descriptions of methods and results, including numerical performance values for several configurations. No figures, tables, or supplementary material were available for inspection.
- **Missing materials affecting confidence** All figures and tables, including the main performance comparison table, ablation tables, UMAP visualizations, calibration curves, and all supplementary tables and notes. Without these, quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in bioinformatics, namely the classification of DNA-binding proteins into single-stranded and double-stranded binding types. The proposed architecture is a reasonable combination of established components, and the authors provide a thorough set of experiments across multiple feature extractors and model architectures. However, the absence of all figures, tables, and supplementary material prevents verification of the central quantitative claims. Several methodological details are also unclear or potentially inconsistent, particularly regarding the RECM-HOG feature dimensionality and the description of the ANBS algorithm. The reported improvements, while plausible, are modest and based on a single benchmark split, which limits the strength of the conclusions.
- **Who would be interested in the results, and why** Researchers working on protein function prediction from sequence, particularly those interested in DNA-binding protein classification, protein language model embeddings, and class imbalance handling in bioinformatics. The work may also be of interest to developers of deep learning architectures for biological sequence analysis.
- **Major strengths** The problem is well-motivated and practically relevant. The authors evaluate a wide range of feature extractors and model architectures, providing a systematic comparison. The use of protein language model embeddings is timely. The inclusion of calibration analysis and bootstrap confidence intervals is a positive methodological step. The authors also compare ANBS against SMOTE and perform hyperparameter sensitivity analysis, which strengthens the claims about the sampling strategy.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The combination of ESM2, RECM-HOG, bilinear attention, and ANBS is novel in this specific configuration, but each component is established. The conceptual advance is incremental rather than transformative.  
  - **Scientific importance** Moderate. Accurate prediction of SSB versus DSB is useful, but the problem is narrow and the performance gains over existing methods are modest. The work does not open a new direction or resolve a long-standing bottleneck.  
  - **Interdisciplinary readership** Limited. The manuscript is written for a specialist bioinformatics audience. Biologists without deep learning expertise would struggle with the methods section.  
  - **Technical soundness** Not fully assessable from the provided material. Several methodological details are unclear or potentially inconsistent, and the absence of figures and tables prevents verification of results.  
  - **Readability for nonspecialists** Below the standard expected for a general journal. The introduction is accessible, but the methods and results sections assume substantial prior knowledge of protein language models, bilinear attention, and sampling techniques.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript may become publishable after the authors provide the missing materials, clarify the methodological inconsistencies, and strengthen the evaluation with additional benchmarks and statistical rigor.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence integrity
- **Claim pointer** The manuscript claims that BAN-SDBPred outperforms existing predictors on independent test data, with specific improvements in Acc, Pre, F1, MCC, and AUC.
- **Evidence pointer** Results sections; Table 4; Figure 6 (both referenced but not provided)
- **Concern** All figures and tables, including the primary performance comparison table and all ablation tables, are missing from the provided material. Without these, the central quantitative claims cannot be verified. The text provides some numbers, but these are insufficient to assess statistical significance, variance across folds, or the validity of the comparisons.
- **Why it matters** The core contribution of the manuscript is a performance improvement. If the supporting data are not available for inspection, the claims are unverifiable and the scientific contribution cannot be assessed.
- **Resolution test** Provide all figures and tables, including the full performance comparison, ablation results, and calibration curves. Ensure that all values reported in the text match the tables and figures.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The RECM-HOG feature is described as producing a fixed 81-dimensional vector, but the RECM matrix is defined as R ∈ R^(L×20), and the HOG transformation is applied to a 20×20 image.
- **Evidence pointer** Methods section, "RECM-HOG Transformation" subsection
- **Concern** The description of the RECM-HOG feature extraction is internally inconsistent. The RECM is defined as an L×20 matrix, but the HOG transformation is described as operating on a 20×20 image. The equations for gradient computation and the cell partitioning appear to assume a 20×20 input, which contradicts the L×20 definition. It is unclear how a variable-length sequence is converted into a fixed 20×20 matrix, and how the 81-dimensional output is derived from this.
- **Why it matters** The RECM-HOG feature is a central component of the proposed method. If the feature extraction is not clearly and correctly described, the method cannot be reproduced or evaluated.
- **Resolution test** Clarify the exact dimensions of the RECM matrix, the preprocessing steps that convert a variable-length sequence into a fixed-size input, and the precise steps of the HOG transformation. Provide a step-by-step example or pseudocode.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The ANBS algorithm is described as "adaptive neighborhood-based sampling" that "iteratively increases the minority class until a balanced configuration is achieved" and "removes majority samples close on both sides of the decision boundary."
- **Evidence pointer** Methods section, "Adaptive Neighborhood-Based Sampling (ANBS) Algorithm" subsection; Algorithm 1
- **Concern** The description of ANBS is vague and partially contradictory. The text states that the algorithm "increases the minority class" but also "removes majority samples." It is unclear whether ANBS performs oversampling, undersampling, or both. The relationship to ADASYN is mentioned, but the specific modifications are not described. The pseudocode is referenced but not provided. The parameters max_ratio and iter_max are given, but their roles are not fully explained.
- **Why it matters** The ANBS strategy is claimed to be a key contribution of the work. Without a clear description of the algorithm, the method cannot be reproduced, and the claimed benefits of ANBS over standard methods cannot be evaluated.
- **Resolution test** Provide a complete and precise description of the ANBS algorithm, including the pseudocode, the exact steps for selecting and synthesizing samples, the criteria for removing majority samples, and the roles of all parameters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports performance improvements of BAN-SDBPred over existing predictors, including a 21% improvement in F1 and 20% in AUC over CNN-Pred on the independent test set.
- **Evidence pointer** Results section, "Performance Analysis of BAN-SDBPred with Existing State-of-the-Art Predictors" subsection; Table 4
- **Concern** The reported improvements are based on a single train-test split. No statistical significance testing is reported, and no confidence intervals are provided for the comparison with existing methods. The bootstrap analysis is mentioned for the final model, but it is not clear whether this was applied to the comparisons with other predictors. Given the small size of the independent test set (165 sequences), the reported differences may not be statistically robust.
- **Why it matters** The claim of superiority over existing methods is a central conclusion. Without statistical evidence, the observed improvements could be due to chance or to the specific choice of test set.
- **Resolution test** Report confidence intervals for all performance metrics on the independent test set, and perform statistical significance tests (e.g., McNemar's test) for the comparison with existing predictors. Consider reporting results across multiple random seeds or cross-validation schemes.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that "All data and models are available at 10.5281/zenodo.18718092."
- **Evidence pointer** Abstract; Data Availability statement (implied)
- **Concern** The Zenodo link is provided, but the actual contents of the repository are not described. It is unclear whether the repository contains the training data, the test data, the trained model weights, the source code, or all of the above. Without a clear description of the repository contents and the exact versions of the software dependencies, the work cannot be reproduced.
- **Why it matters** Reproducibility is a fundamental requirement for computational research. The authors should provide a clear and complete description of the code and data availability.
- **Resolution test** Provide a detailed description of the Zenodo repository contents, including the directory structure, file formats, and software dependencies. Ensure that the code is well-documented and that the data are in a standard format.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, last sentence
- **Issue** The abstract states that BAN-SDBPred achieves improvements of "2%, 4.5%, 21%, 9%, and 20%" in Acc, Pre, F1, MCC, and AUC, respectively. These numbers are presented without context, and it is unclear whether these are absolute or relative improvements.
- **Required correction** Clarify whether these are absolute or relative improvements, and specify the baseline model for each comparison.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction and Methods
- **Evidence pointer** Introduction, paragraph 1; Methods, "Benchmark Data Sets" subsection
- **Issue** The terms "SSB" and "DSB" are used throughout, but the full forms "single-stranded DNA-binding protein" and "double-stranded DNA-binding protein" are not consistently used. The abstract uses "SSBs" and "DSBs" without defining them.
- **Required correction** Define all abbreviations at first use in the abstract and in the main text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "Benchmark Data Sets" subsection
- **Evidence pointer** Methods, "Benchmark Data Sets" subsection
- **Issue** The description of the dataset construction mentions that CD-HIT was used to remove redundancy at a 0.7 threshold, but the final class distribution is only given as a ratio (DSB:SSB ≈ 4.77:1). The exact number of sequences in each class for both training and test sets is not stated in the text.
- **Required correction** Provide the exact number of sequences in each class for the training and test sets.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Bilinear Attention Network for Feature Fusion" subsection
- **Evidence pointer** Methods, "Bilinear Attention Network for Feature Fusion" subsection
- **Issue** The description of the bilinear attention mechanism is brief. The equations for the interaction score and the pooling operation are provided, but the overall architecture, including the number of attention heads, the dimensions of the projection matrices, and the fusion with the fully connected layers, is not fully described.
- **Required correction** Provide a more detailed description of the bilinear attention network architecture, including the number of heads, the dimensions of the projection matrices, and the structure of the classification head.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results, "Performance Analysis of Single Features on 5-Fold-CV and Independent Testing (without ANBS)" subsection
- **Evidence pointer** Results, first subsection
- **Issue** The text states that "persistent models were unstable with handcrafted features" and gives the example of LSTM with CPSF obtaining 62.3 in Acc. The term "persistent models" is unclear.
- **Required correction** Replace "persistent models" with a clearer term, such as "recurrent models" or "LSTM-based models."

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "Performance Analysis of BAN-SDBPred with Existing State-of-the-Art Predictors" subsection
- **Evidence pointer** Results, final subsection
- **Issue** The comparison with existing predictors is limited to four methods. The authors do not discuss why these specific methods were chosen or whether there are more recent methods that should be included.
- **Required correction** Justify the choice of baseline methods and discuss whether any more recent predictors should be included in the comparison.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Multiple locations
- **Issue** The manuscript contains several grammatical errors and awkward phrasings, e.g., "The BAN-SDBPs use the deep representation" in the Conclusion, and "as experimental techniques" at the end of a sentence in the Introduction.
- **Required correction** The manuscript should be carefully proofread and edited for grammar and clarity.

## Risk / unsupported claims
- The claim that BAN-SDBPred outperforms existing predictors cannot be verified without the missing tables and figures.
- The claim that ANBS improves performance over SMOTE is based on a single comparison and lacks statistical testing.
- The claim that the bilinear attention network provides "biologically interpretable" insights is supported only by a qualitative statement and a reference to SHAP analysis, but no SHAP results are shown in the provided material.
- The claim that the model captures "long-range sequence dependencies and local residue interactions simultaneously" is plausible but not directly demonstrated.
- The claim that the method is "generalizable" is based on a single independent test set and lacks external validation on more recent or diverse datasets.
- The statement that "the benchmark data sets used are relatively old" is acknowledged in the Conclusion, but the authors do not discuss the potential impact of this limitation on the validity of their results.