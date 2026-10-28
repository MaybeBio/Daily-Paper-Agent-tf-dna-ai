## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, acknowledgements)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present ProBASS, a model combining sequence (ESM2) and structural (ESM-IF1) embeddings, fine-tuned on a large experimental dataset of ΔΔG bind values, to predict the effect of mutations on protein-protein binding affinity. They report high correlations for single mutations (0.83 ± 0.05 within a PDB; 0.81 ± 0.02 on a mixed dataset) and moderate correlations for double mutations (0.69 ± 0.04 within a PDB), and claim superiority over existing methods.
- **Visible evidence base** Abstract, Introduction, Methods (partial), Results (narrative), Discussion, Data availability statement
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; detailed hyperparameter settings; exact data splitting procedures; full dataset composition; code implementation details; comparison methodology details

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in protein engineering and design, and the proposed approach of combining two complementary protein language models is conceptually sound. However, the current manuscript has several critical gaps in methodological reporting and validation that prevent full assessment of the claims. The results as described are promising but not fully substantiated without access to the referenced figures and detailed experimental protocols.
- **Who would be interested in the results, and why** Researchers in computational protein design, protein engineering, and biophysics would be interested. The work is also relevant to those developing machine learning methods for predicting mutational effects, and to experimentalists seeking to prioritize mutations for characterization in therapeutic antibody or enzyme engineering contexts.
- **Major strengths** 1) The combination of sequence-based and structure-based PLM embeddings is a reasonable and potentially powerful approach. 2) The use of a large experimental dataset (nearly 26K mutations) is a significant resource advantage. 3) The comparison with existing methods (ESM-IF1, ProteinMPNN, ThermoMPNN) is useful for benchmarking. 4) The analysis of outlier mutations provides insight into model limitations and potential avenues for improvement.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing figures and validation details), R1-M2 (data leakage risk), R1-M3 (incomplete comparison methodology), R1-M4 (double mutation generalization claim unsupported)
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The combination of ESM2 and ESM-IF1 for binding affinity prediction is novel, but the overall approach of fine-tuning PLMs for downstream prediction tasks is not new.  
  *Scientific importance*: High. Accurate prediction of mutation effects on binding affinity has broad applications in disease understanding and protein engineering.  
  *Interdisciplinary readership*: Moderate. The work bridges machine learning and structural biology, but the presentation is likely to be most accessible to computational biologists.  
  *Technical soundness*: Currently not fully assessable due to missing methodological details and figures. The described approach is plausible but requires verification.  
  *Readability for nonspecialists*: The abstract and introduction are accessible, but the methods and results sections assume familiarity with PLM architectures and ΔΔG bind prediction conventions.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the dataset is valuable, but the manuscript in its current form does not provide sufficient evidence to fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript reports specific correlation values (0.83 ± 0.05 for single mutations, 0.69 ± 0.04 for double mutations, 0.81 ± 0.02 for the mixed dataset) and comparisons with other methods.
- **Evidence pointer** Figures 2, 3, 4, 5, 6 and Supplementary Figures 1, 2, 3, 5, 6 are referenced but not provided in the submitted material.
- **Concern** The central quantitative claims of the manuscript cannot be verified without access to the referenced figures. Correlation values, error bars, and comparative performance are presented only as text descriptions. Additionally, the methods section is incomplete, lacking details on model architecture, training hyperparameters, and evaluation protocols.
- **Why it matters** The validity of the core claims depends entirely on the data shown in the figures. Without them, the reported performance cannot be assessed for statistical significance, potential overfitting, or methodological artifacts.
- **Resolution test** Provide all referenced figures and supplementary figures with clear axis labels, error bars, and statistical significance indicators. Complete the methods section with full details on model training, hyperparameters, and evaluation procedures.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data leakage and generalization
- **Claim pointer** The manuscript claims that training on multiple PDBs improves prediction accuracy on unseen PDBs, with an average correlation of 0.68 for six tests.
- **Evidence pointer** Methods section "Training and testing" and Results section, Figure 3B and Supplementary Figure 3.
- **Concern** The manuscript does not clearly describe how the training and test sets were partitioned to avoid data leakage. Specifically, when training on 131 PDBs and testing on one PDB, it is unclear whether mutations from homologous complexes or similar sequences were excluded. Additionally, the claim that the model generalizes to unseen PDBs is based on only six test cases, which may not be statistically robust.
- **Why it matters** Data leakage can inflate performance estimates. If homologous complexes share similar mutation patterns, the model may be memorizing rather than generalizing. The limited number of test PDBs also raises questions about the reliability of the reported average correlation.
- **Resolution test** Clearly describe the data partitioning strategy, including any sequence or structural similarity thresholds used to prevent leakage. Report performance on a larger and more diverse set of held-out PDBs, ideally with confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Comparative evaluation
- **Claim pointer** The manuscript claims that ProBASS surpasses state-of-the-art methods (ESM-IF1, ProteinMPNN, ThermoMPNN) in correlation with experimental data.
- **Evidence pointer** Results section, Figure 6.
- **Concern** The comparison methodology is not fully described. It is unclear whether the same training data, evaluation metrics, and data splits were used for all methods. For ESM-IF1 and ProteinMPNN, the manuscript states that negative log probability scores were correlated with experimental values, but the details of how these scores were computed and normalized are not provided. For ThermoMPNN, the exact protocol for computing ΔΔG values is not described.
- **Why it matters** Fair comparison is essential to support the claim of superiority. Differences in data preprocessing, evaluation protocols, or metric definitions could bias the comparison in favor of ProBASS.
- **Resolution test** Provide a detailed description of the evaluation protocol for each method, including data splits, scoring functions, and any normalization steps. Consider reporting additional metrics such as RMSE, Spearman correlation, and classification accuracy.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalization to double mutations
- **Claim pointer** The manuscript states that the model achieves a correlation of 0.69 ± 0.04 for double mutations when training and testing on the same PDB, but notes that generalization to other PDBs was not achieved due to limited data.
- **Evidence pointer** Results section, Figure 5A and 5B, Supplementary Figure 5B.
- **Concern** The claim that the model can predict double mutation effects is based on only two PDBs (3OTJ and 1CBW), both of which are serine protease/inhibitor complexes. The manuscript acknowledges that generalization was not possible, but the abstract states that the model is "broadly applicable" for ΔΔG bind prediction. This overstates the current evidence.
- **Why it matters** Double mutations are more challenging and less well-represented in training data. Without evidence of generalization across diverse PDBs, the claim of broad applicability is not supported.
- **Resolution test** Either temper the claim in the abstract and discussion, or provide additional validation on double mutations from structurally diverse PDBs.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, "Feature Engineering and machine learning"
- **Evidence pointer** Methods section, paragraph 2
- **Issue** The text contains a duplicated sentence: "We extracted the structural features from the ESM-IF1 model, Since the structural embeddings describe the positions of the Cα atoms only and hence are very similar for the wild-type and the mutant sequence, we have only used the wild-type embeddings to describe the structural features of the complex." This sentence appears twice verbatim.
- **Required correction** Remove the duplicated sentence and ensure the description of structural feature extraction is clear and concise.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, "Training and testing"
- **Evidence pointer** Methods section, paragraph 3
- **Issue** The RMSE equation is described in text but not presented as a proper equation. The variables Yi and Yl are defined but the equation itself is not shown.
- **Required correction** Present the RMSE equation in a standard mathematical format with clear definitions of all variables.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, all subsections
- **Evidence pointer** Results section, Figures 2, 3, 4, 5, 6
- **Issue** The manuscript reports correlation coefficients and RMSE values but does not provide confidence intervals or statistical significance tests for the differences between methods.
- **Required correction** Add confidence intervals for correlation coefficients and perform statistical tests (e.g., bootstrap or permutation tests) to assess whether differences between ProBASS and other methods are significant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data description
- **Affected element** Methods section, "Data Preparation"
- **Evidence pointer** Methods section, paragraph 1
- **Issue** The manuscript states that 44% of the data belongs to serine-protease/inhibitor complexes but does not provide a breakdown of the remaining 56% in terms of complex types or structural diversity.
- **Required correction** Provide a more detailed description of the dataset composition, including the number of PDBs per complex type and the range of binding affinities represented.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction, paragraph 1
- **Issue** The term "biding affinity" appears in the Introduction (paragraph 1) and should be "binding affinity". Additionally, the abstract uses "ΔΔG bind" without defining the subscript convention.
- **Required correction** Correct the typo and define the notation for ΔΔG bind at first use.

## Risk / unsupported claims
- The claim that ProBASS "surpasses the state-of-the-art methods" is not fully supported without detailed comparison methodology and access to Figure 6.
- The claim that the model is "broadly applicable" for ΔΔG bind prediction is overstated given the limited diversity of double mutation data and the acknowledged lack of generalization for double mutations.
- The claim that the model achieves "nearly perfect correlation" for single mutations within a PDB is based on text descriptions only and cannot be verified without the figures.
- The statement that "additional experiments may not be necessary" once sufficient training data is available is speculative and not directly supported by the results presented.
- The claim that fine-tuning on one task (stability) decreases accuracy for another task (binding) is based on a single comparison with ThermoMPNN and requires more evidence.