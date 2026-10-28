## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, conclusions, appendices referenced but not provided in full)
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text. Numerical results in tables and figures are referenced but not fully visible.
- **Shared manuscript claim summary** The authors propose GMI-Score, a machine learning-based scoring function that models multi-level, multi-body atomic interactions (pairwise and triplet-wise) via graph-based representations, and claim consistent state-of-the-art performance across multiple benchmarks including PDBbind v2013, v2016, v2020, CSAR-NRC-HiQ, and PDBbind-Redocked.
- **Visible evidence base** Abstract, introduction, results narrative (Sections 2.1, 2.2, 2.4, 2.5, 2.6, 2.7), methods description (Section 3.1, 3.2), conclusions, author contributions, funding, data availability. Tables and figures are referenced but their contents are not provided in the supplied text.
- **Missing materials affecting confidence** Full tables (Table 1, 2, 3, 5, A1, A2, A3, B4), all figures (Figure 1, 2, 3, B1), appendix contents (C, D), and detailed hyperparameter optimization results. Without these, quantitative comparisons and statistical claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational drug discovery, namely binding affinity prediction, and proposes a graph-based approach that extends pairwise interaction models to include triplet-wise interactions. The conceptual motivation is reasonable and the authors acknowledge the computational trade-offs of more expressive geometric models. However, the provided text does not include the actual numerical results, tables, or figures that would substantiate the central performance claims. The methods section contains several incomplete or unclear mathematical definitions, and the fusion strategy is described at a high level without sufficient detail to assess its novelty or validity. The external validation on CSAR-NRC-HiQ is based on only 49 complexes, which raises concerns about statistical power. The manuscript also contains numerous typographical errors and inconsistencies that impede readability. The core claims of consistent outperformance and robustness cannot be fully evaluated from the supplied material.
- **Who would be interested in the results, and why** Computational chemists, cheminformaticians, and researchers in structure-based drug design would be the primary audience. The work is relevant to those developing or applying machine learning scoring functions for virtual screening and lead optimization. The emphasis on higher-order interactions and practical scalability may also interest researchers working on geometric deep learning for molecular applications.
- **Major strengths** The conceptual framing of multi-body interactions in a unified graph framework is a sensible extension of existing pairwise approaches. The authors explicitly address the computational scalability concern that limits the application of equivariant geometric GNNs to large-scale screening. The use of multiple benchmark datasets, including a redocked set, is appropriate for assessing generalization. The feature fusion strategy aimed at reducing model complexity while improving accuracy is a practical and potentially valuable contribution.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing numerical evidence), R1-M2 (incomplete methods), R1-M3 (external validation sample size), R1-M4 (statistical comparison details).
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The idea of incorporating triplet-wise interactions into a graph-based scoring function is a reasonable incremental extension of prior pairwise models. The conceptual shift claimed by the authors is not fully demonstrated in the provided text.  
  - **Scientific importance** Moderate to high. Binding affinity prediction is an important problem, and improvements in accuracy and robustness are of practical value. However, the magnitude of the claimed improvement over existing methods cannot be assessed without the numerical results.  
  - **Interdisciplinary readership** Moderate. The work bridges machine learning and structural biology, but the presentation is likely to be most accessible to specialists in computational drug design. The methods section assumes familiarity with graph-based representations and gradient boosting.  
  - **Technical soundness** Not fully assessable. The mathematical definitions in Section 3.1 are incomplete, and the fusion strategy is described without sufficient algorithmic detail. The statistical analysis is referenced but not shown.  
  - **Readability for nonspecialists** Below the standard expected for a general journal. The text contains numerous typographical errors, incomplete sentences, and inconsistent notation. The abstract includes unclear phrases such as "redocked and withheld atascenarios" and "open heminformaticsworkflows."  
- **Recommendation posture** Currently not established from the provided evidence. The central performance claims cannot be verified without the tables and figures. The methods section requires substantial clarification. The authors should be invited to resubmit a revised version with complete results and a more rigorous methods presentation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The manuscript claims that GMI-Score "consistently outperforms state-of-the-art scoring functions" and achieves Pearson correlation coefficients up to 0.877 across multiple benchmarks.  
- **Evidence pointer** Tables 1, 2, 3, 5, A1, A2, A3; Figures 1, 2, 3, B1 (contents not provided)  
- **Concern** The central quantitative claims of the paper are presented without the actual numerical data. The text references tables and figures that are not included in the supplied material, making it impossible to verify the reported correlation coefficients, compare against baseline methods, or assess the statistical significance of the differences.  
- **Why it matters** The entire case for the proposed method rests on its empirical performance relative to existing approaches. Without the underlying data, the claims of consistent outperformance and robustness are unsupported.  
- **Resolution test** Provide all tables and figures with full numerical values, including baseline comparisons, standard deviations, and sample sizes. Ensure that the reported correlation coefficients are reproducible from the provided data.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological completeness  
- **Claim pointer** The methods section (Section 3.1) defines multi-body interaction graphs and scoring functions, and Section 3.2 describes a fusion strategy.  
- **Evidence pointer** Section 3.1, Section 3.2  
- **Concern** The mathematical definitions in Section 3.1 are incomplete. The vertex set, edge set, and weight function are described with missing symbols and incomplete expressions. The definition of the cyclic score is cut off, and the clique score is not fully specified. The fusion strategy in Section 3.2 is described at a conceptual level without algorithmic details, such as how feature importance is computed, how the threshold for feature selection is chosen, or how the rank-based aggregation is implemented.  
- **Why it matters** A methods section that cannot be followed or reproduced undermines the scientific contribution. The reader cannot assess whether the proposed approach is novel, correct, or implementable.  
- **Resolution test** Rewrite Section 3.1 and 3.2 with complete mathematical notation, clear definitions of all variables, and a step-by-step description of the fusion algorithm. Provide pseudocode or a reference to an implementation.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Statistical robustness  
- **Claim pointer** The external validation on CSAR-NRC-HiQ reports a Pearson correlation of 0.796 ± 0.016 based on 49 complexes.  
- **Evidence pointer** Section 2.6, Table 5 (contents not provided)  
- **Concern** The CSAR-NRC-HiQ validation set contains only 49 complexes. With such a small sample, the reported correlation coefficient is subject to wide confidence intervals, and the comparison against other methods may not be statistically meaningful. The manuscript does not report confidence intervals or effect sizes for this comparison.  
- **Why it matters** A claim of superior performance on a small external set may not generalize. The authors should acknowledge the limitation and provide appropriate statistical measures.  
- **Resolution test** Report confidence intervals for the correlation coefficients on the CSAR-NRC-HiQ set, and discuss the statistical power of the comparison given the sample size.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Statistical rigor  
- **Claim pointer** The manuscript states that paired t-tests were applied to assess whether the difference in R p between GMI-Score and the individual models is meaningful.  
- **Evidence pointer** Section 2.4, Table A2 (contents not provided)  
- **Concern** The text reports a difference of "nearly 0.02" in R p and claims statistical significance, but the details of the t-test are not provided. It is unclear whether the test was applied to the correlation coefficients across folds, whether the assumptions of the t-test were checked, and whether multiple comparisons were accounted for.  
- **Why it matters** Statistical claims require transparent reporting of the test procedure, including the number of comparisons, the distribution of the data, and the correction for multiple testing.  
- **Resolution test** Provide the full output of the t-test, including the test statistic, degrees of freedom, p-value, and a description of how the data were prepared for the test. State whether any correction for multiple comparisons was applied.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, "Scientific Contribution" paragraph  
- **Issue** The phrase "redocked and withheld atascenarios" appears to be a typographical error, and "open heminformaticsworkflows" is unclear.  
- **Required correction** Revise to "redocked and withheld scenarios" and "open cheminformatics workflows."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Consistency  
- **Affected element** Section 2.4  
- **Evidence pointer** Section 2.4, paragraph 1  
- **Issue** The text states "PDBBind v2016" in one instance and "PDB-bind v2016" in another. The dataset name should be used consistently throughout.  
- **Required correction** Standardize the dataset name to "PDBbind" in all instances.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Section 2.2  
- **Evidence pointer** Section 2.2, Table 2 and Table A1  
- **Issue** The text mentions "various Gradient Boosting models" but does not specify which hyperparameters were varied, the range of values tested, or the criteria for selecting the best configuration.  
- **Required correction** Provide a brief description of the hyperparameter grid and the selection criterion.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 3.1  
- **Evidence pointer** Section 3.1, paragraph on weight function  
- **Issue** The sentence "where Φ is a kernel function parameterized by a characteristic distance , we place the following conditions on the weight function Φ as previous work [ 44 ]" is incomplete and grammatically incorrect.  
- **Required correction** Rewrite the sentence to clearly state the conditions on the weight function and cite the relevant prior work.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Section 3.2  
- **Evidence pointer** Section 3.2, paragraph on feature fusion  
- **Issue** The description of the feature fusion process is vague. The text mentions "n minimum node impurity of features from m datasets" but does not define n or m, nor does it explain how the "new variables" are constructed.  
- **Required correction** Provide a precise definition of the feature selection and fusion procedure, including the role of the gradient boosting model and the exact formula for the new feature set.

- **Concern ID** R1-m6  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Section 2.1  
- **Evidence pointer** Section 2.1, paragraph on CSAR-NRC-HiQ  
- **Issue** The text states that the CSAR-NRC-HiQ dataset was filtered to remove overlaps with PDBbind, but it does not specify the overlap removal criteria or the resulting number of complexes before filtering.  
- **Required correction** Clarify the filtering procedure and report the number of complexes before and after overlap removal.

## Risk / unsupported claims
- The claim that GMI-Score "consistently outperforms state-of-the-art scoring functions" is unsupported because the numerical results in Tables 1, 2, 3, 5 and Figures 1, 2, 3 are not provided.
- The claim of "strong predictive power under strict data leakage controls" is not verifiable because the leakage control procedure is not described in the supplied text.
- The claim that the model "retains strong predictive power under realistic docking conditions" is based on the PDBbind-Redocked dataset, but the results are not shown.
- The statement that the fusion model is "statistically significantly better" than individual models is not verifiable without the t-test details in Table A2.
- The claim that GMI-Score "makes a conceptual shift in cheminformatics scoring functions" is overstated relative to the incremental nature of the proposed extension.