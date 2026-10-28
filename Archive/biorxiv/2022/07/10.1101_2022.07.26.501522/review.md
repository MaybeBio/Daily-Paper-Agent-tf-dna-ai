## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and suitability for a high-impact generalist journal
- **Shared manuscript claim summary** The authors present DNAffinity, a physics-based machine learning approach that predicts in vitro transcription factor binding affinities using DNA structural and mechanical properties derived from atomistic molecular dynamics simulations. The method reportedly outperforms existing algorithms across uPBM, gcPBM, and HT-SELEX datasets, and when combined with nucleosome positioning maps, provides accurate in vivo binding site predictions in yeast for the transcription factor CBF1.
- **Visible evidence base** Abstract, full introduction, methods section (datasets, feature classes, training procedure, quality assessment, genomic testing), results and discussion (performance metrics, comparisons with existing methods, feature importance analysis, in vivo validation), conclusions
- **Missing materials affecting confidence** Figures 1-7 and Supplementary Figures S1-S12 referenced but not provided; Supplementary Tables S1-S4 referenced but not provided; Supplementary Methods referenced but not provided; GitHub repository code not independently verified; detailed hyperparameter settings for the random forest regressor not specified; exact train/test split details per dataset not fully specified

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach that combines physics-based DNA descriptors from molecular dynamics simulations with a random forest regressor to predict transcription factor binding affinities. The core idea of using theoretically derived mechanical and structural properties of DNA as features is novel and potentially valuable, particularly the claim that these descriptors can be extended to non-canonical DNA such as epigenetic variants. However, the manuscript as provided has several critical gaps that prevent full evaluation. The most significant concerns are the absence of all figures and supplementary materials, which are essential for assessing the actual performance claims, the limited scope of the in vivo validation (single transcription factor in yeast), and the lack of clarity on several methodological details. The comparison with existing methods appears favorable but cannot be fully verified without the referenced figures. The in vivo results, while promising, are based on a single TF and rely on assumptions about nucleosome occupancy that need more rigorous treatment. The manuscript would benefit from clearer articulation of the novelty relative to existing shape-based approaches and a more critical discussion of the limitations of the in vitro to in vivo extrapolation.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on transcription factor binding site prediction would be the primary audience. Researchers studying DNA mechanics and its role in protein-DNA recognition would also find the approach interesting. Additionally, experimental biologists studying gene regulation, particularly those working with yeast as a model system, may be interested in the in vivo application. The potential extension to epigenetic variants could attract researchers in epigenetics and DNA damage repair fields.

- **Major strengths** 1) The use of physics-based descriptors derived from MD simulations is conceptually novel and provides a mechanistic basis for the predictions, distinguishing this approach from purely sequence-based methods. 2) The method demonstrates applicability across three different experimental platforms (uPBM, gcPBM, HT-SELEX), suggesting generalizability. 3) The inclusion of mechanical properties (stiffness constants) alongside equilibrium geometry is physically well-motivated. 4) The attempt to bridge in vitro predictions to in vivo binding through integration with chromatin structure data is an important step toward practical utility. 5) The authors provide the code and database publicly, supporting reproducibility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims excellent predictive performance (R² = 0.93 for gcPBM, 0.69 for uPBM, 0.66-0.71 for HT-SELEX) and superiority over existing methods.
- **Evidence pointer** Figures 1-5, Supplementary Figures S4-S9, Supplementary Tables S2-S4; location not provided
- **Concern** All figures and supplementary materials referenced in the results section are missing from the provided manuscript. Without these, the actual performance data, comparison plots, and detailed results cannot be evaluated. The claims of outperforming existing methods rest entirely on these unprovided materials.
- **Why it matters** The central claims of the manuscript are quantitative performance claims. Without the actual data visualizations and tables, it is impossible to assess whether the reported R² values are accurate, whether the comparisons with other methods are fair and properly controlled, and whether the conclusions drawn from the data are justified.
- **Resolution test** Provide all figures and supplementary materials. The performance claims must be verifiable from the presented data, including proper statistical analysis of the comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The methods section describes training a random forest regressor on features derived from MD simulations, with an 80/20 train/test split and bootstrap resampling.
- **Evidence pointer** Materials and Methods, Machine Learning Training; location not provided
- **Concern** Several critical methodological details are missing. The exact hyperparameters of the random forest (number of trees, tree depth, feature sampling strategy) are not specified. The procedure for handling the different dataset types (uPBM, gcPBM, HT-SELEX) in a unified training framework is unclear, particularly how features are computed for sequences of different lengths. The weighting scheme for uPBM data is described but the exact implementation is not detailed. The cross-validation procedure is mentioned but the relationship between the bootstrap approach and the 10-fold cross-validation is not clarified.
- **Why it matters** Reproducibility is a fundamental requirement for any computational method. Without complete methodological details, other researchers cannot implement or validate the approach. The lack of clarity on how different dataset types are handled also raises questions about whether the model is truly universal or dataset-specific.
- **Resolution test** Provide complete details on hyperparameters, feature computation for variable-length sequences, the exact weighting and undersampling procedures, and clarify the relationship between bootstrap and cross-validation approaches.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Validation scope
- **Claim pointer** The in vivo validation claims over 94% true positive rate for CBF1 binding site prediction in yeast when combined with nucleosome maps.
- **Evidence pointer** Results and Discussion, Genomic testing; Figure 7; location not provided
- **Concern** The in vivo validation is limited to a single transcription factor (CBF1) in a single organism (yeast). While the results are encouraging, the generalizability of the approach to other TFs and organisms is not demonstrated. Additionally, the definition of true and false positives relies on overlap with experimental peaks, but the criteria for "overlap" are not precisely defined. The treatment of nucleosome-occupied sites as "explained false positives" is reasonable but requires more rigorous justification.
- **Why it matters** The claim that the method can bridge in vitro to in vivo predictions is a significant one. A single example, however compelling, is insufficient to establish this as a general property of the method. The lack of precise definitions for peak overlap and the handling of nucleosome data also affect the reproducibility of the analysis.
- **Resolution test** Expand the in vivo validation to additional transcription factors and ideally additional organisms. Provide precise definitions for peak overlap criteria and clearly document the processing of nucleosome positioning data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison fairness
- **Claim pointer** The manuscript claims DNAffinity outperforms all existing methods in cross-dataset transfer (average Pearson correlation 0.47 vs 0.20-0.41 for other methods).
- **Evidence pointer** Results and Discussion, DNAffinity's performance compared to existing ML predictors; Figure 5C; location not provided
- **Concern** The comparison with existing methods is described as using "the same number of cases (TFs) and the same dataset as used by the original developers of the methods." However, it is unclear whether the hyperparameters of the competing methods were optimized for these datasets or used as default. The comparison of cross-dataset transfer (training on HT-SELEX, testing on uPBM) may not be apples-to-apples if the competing methods were not designed for such transfer. The choice of Pearson correlation as the metric for this comparison, while R² is used elsewhere, needs justification.
- **Why it matters** Unfair or poorly controlled comparisons can lead to inflated claims of superiority. The choice of evaluation metrics and the conditions under which competing methods are run significantly affect the conclusions about relative performance.
- **Resolution test** Provide details on how competing methods were configured, whether hyperparameter tuning was performed for each method, and justify the choice of evaluation metrics for each comparison.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Feature importance interpretation
- **Claim pointer** The manuscript claims that the importance of different feature classes depends dramatically on the experimental data type, with physical properties being most important for gcPBM and all three classes contributing for HT-SELEX.
- **Evidence pointer** Results and Discussion, Importance of the features; Figure 6; Supplementary Figures S10-S11; location not provided
- **Concern** The interpretation of feature importance is based on the random forest's built-in importance measures, which are known to be biased toward features with many categories or high cardinality. The manuscript does not specify which importance measure was used (e.g., Gini importance vs permutation importance). The claim that "the electrostatic descriptor gained importance when using HT-SELEX data compared to uPBM" is presented without statistical testing.
- **Why it matters** Feature importance analysis is used to draw conclusions about the biological mechanisms of DNA recognition. If the importance measures are biased or the differences are not statistically significant, the biological interpretations may be misleading.
- **Resolution test** Specify the importance measure used, consider using permutation importance as a more robust alternative, and provide statistical tests for the differences in feature importance across datasets.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states the method "can be extended to epigenetic variants, mismatches, mutations, or any non-coding nucleobases" but no results demonstrating this extension are presented in the manuscript.
- **Required correction** Either provide proof-of-concept results for at least one of these extensions or soften the claim to indicate this is a potential future direction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 1; location not provided
- **Issue** The term "physics-based" is used to describe the approach, but the machine learning model is a random forest trained on physics-derived features. This distinction should be clarified to avoid overstating the physics-based nature of the prediction itself.
- **Required correction** Clarify that the features are physics-derived but the prediction model is empirical, or use a more precise term such as "physics-informed."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results and Discussion
- **Evidence pointer** Results and Discussion, DNAffinity's performance; location not provided
- **Issue** The reported R² values are presented as means with standard deviations (e.g., 0.93±0.02), but the number of replicates or the source of variability is not specified.
- **Required correction** Specify the number of independent training runs or the source of the reported variability.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Materials and Methods
- **Evidence pointer** Materials and Methods, Datasets for training and testing; location not provided
- **Issue** The manuscript states that all dataset references are in Supplementary Table S1, but this table is not provided.
- **Required correction** Include the supplementary table or provide the dataset accessions directly in the main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Typographical
- **Affected element** Results and Discussion
- **Evidence pointer** Results and Discussion, Genomic testing; location not provided
- **Issue** The text contains a typographical error: "in vitro} binding" has a stray closing brace.
- **Required correction** Correct the typographical error.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusions
- **Evidence pointer** Conclusions; location not provided
- **Issue** The statement "Prediction of transcription factor binding sites is the next grand challenges in genomic research" contains a grammatical error ("challenges" should be "challenge").
- **Required correction** Correct the grammatical error.

## Risk / unsupported claims
- The claim that DNAffinity "can be extended to epigenetic variants, mismatches, mutations, or any non-coding nucleobases" is unsupported by any results in the provided manuscript.
- The claim of "state-of-the-art predictive power" for in vivo binding site identification is based on a single transcription factor (CBF1) in yeast and cannot be generalized without additional validation.
- The assertion that "the real FP rate can be as low as 7%" relies on assumptions about polymerase activity evidence that are not fully described.
- The claim that "in vivo binding may be understood as in vitro binding corrected by high-resolution chromatin structure" is presented as a general conclusion but is derived from a single case study.
- The performance comparison claims cannot be evaluated without the referenced figures and supplementary tables.
- The feature importance analysis and its biological interpretation are not statistically validated.