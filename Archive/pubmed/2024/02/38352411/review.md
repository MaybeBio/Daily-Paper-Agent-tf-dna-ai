## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2024)
- **Assessment boundary** Scientific content, methodology, validation, and claims as presented in the provided text; no supplementary figures or data were available for inspection
- **Shared manuscript claim summary** The authors present a family-level machine learning framework (FamilyCode) that predicts DNA binding specificity changes (ΔΔΔG/RT) for transcription factor mutants, using a reference-free tetrahedral representation of base preferences. The method is validated on bHLH and homeodomain families, with experimental confirmation for selected bHLH mutants.
- **Visible evidence base** Main text, methods, figure legends (referenced but not shown), and references to supplementary materials (not provided)
- **Missing materials affecting confidence** All figures, supplementary data files, code repository contents, raw sequencing data, and detailed model configurations were not accessible; these are essential for verifying the quantitative claims

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting and potentially useful approach for predicting the effects of transcription factor mutations on DNA binding specificity. The tetrahedral representation is a novel and elegant solution to a known problem in comparing position-specific affinity matrices across proteins. The authors demonstrate reasonable predictive performance on held-out wild-type factors and provide experimental validation for a small set of mutants. However, the current evidence base is insufficient to fully assess the robustness, generalizability, and practical utility of the method. Key concerns include the limited scope of experimental validation, the lack of accessible code and data for independent verification, and the absence of a clear comparison with alternative approaches beyond two baselines. The manuscript would benefit from a more thorough benchmarking, a clearer articulation of the method's limitations, and a more cautious interpretation of the results, particularly regarding the clinical relevance of the predictions.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational biology, and protein-DNA interactions would find this work relevant. The method offers a potential tool for prioritizing disease-associated TF variants for experimental follow-up, which could be of interest to the human genetics community. The tetrahedral representation itself may be of broader methodological interest for comparing quantitative binding models across related proteins.
- **Major strengths** The tetrahedral representation is a novel and mathematically sound solution to the problem of comparing base preferences across TFs with different preferred bases. The use of a biophysically interpretable framework (ProBound) provides a solid foundation. The authors demonstrate the generalizability of their approach by applying it to two distinct TF families (bHLH and homeodomain). The inclusion of experimental validation, albeit limited, strengthens the claims.
- **Major Concerns** The experimental validation is limited to a small number of mutants in two proteins (HES2, ASCL2), and the predictive accuracy for homeodomain mutants is not experimentally verified. The comparison with alternative methods (closest-paralog, similarity regression) is limited and does not include more recent or structure-based approaches. The manuscript does not provide a clear assessment of the method's sensitivity to training set composition, alignment quality, or the choice of the tetrahedral transformation. The claim that the method can predict "disease-associated" mutation effects is not directly supported by the data presented, as no disease-associated variants are tested. The confidence score, while correlated with accuracy in cross-validation, is not validated on an independent dataset.
- **Minor Comments** The manuscript would benefit from a more detailed description of the tetrahedral transformation and its properties. The choice of the F-test p-value threshold for feature selection is not justified. The description of the "reference-free" nature of the representation could be clarified. The discussion of the method's limitations is somewhat brief and could be expanded. The writing is generally clear but could be more concise in places.
- **Technical failings that need to be addressed before the case is established** The lack of access to the code and data prevents independent verification of the results. The experimental validation is too limited to establish the method's predictive power for arbitrary mutants. The comparison with rCLAMPS and DeepPBS is not fully described, and the metrics used may not be directly comparable. The manuscript does not address the potential for overfitting in the feature selection process.
- **Assessment against Nature-style criteria** 
  - **Originality**: The tetrahedral representation is a novel contribution. The overall concept of family-level prediction is not entirely new, but the specific implementation is original.
  - **Scientific importance**: The problem of predicting the functional impact of TF mutations is important. However, the demonstrated impact is limited by the scope of the validation.
  - **Interdisciplinary readership**: The work is primarily of interest to computational biologists and molecular biologists studying gene regulation. The potential clinical relevance is mentioned but not developed.
  - **Technical soundness**: The methodology appears sound in principle, but the lack of access to code and data prevents a full assessment. The statistical analysis is appropriate but could be more rigorous.
  - **Readability for nonspecialists**: The manuscript is written for a specialist audience. The methods section is dense and may be challenging for readers without a strong background in machine learning and biophysics.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the current evidence is insufficient to fully establish the method's utility. The authors should provide access to code and data, expand the experimental validation, and provide a more comprehensive benchmarking against existing methods.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and data availability
- **Claim pointer** The manuscript claims that all code and data are available, but the provided links and references are not sufficient for independent verification.
- **Evidence pointer** Data and Software Availability section; Methods section
- **Concern** The manuscript states that code is available at a GitHub repository and raw sequencing data at an NCBI BioProject, but these were not accessible during review. Furthermore, the supplementary data files (S1-S5) referenced throughout the text are not provided. Without access to these materials, it is impossible to verify the accuracy of the model fitting, the quality of the binding models, or the validity of the cross-validation results.
- **Why it matters** Reproducibility is a cornerstone of scientific progress. The inability to access the code and data undermines the credibility of the claims and prevents other researchers from building upon this work.
- **Resolution test** The authors must provide a complete, functional code repository with clear documentation, all processed data files, and the raw sequencing data (or a clear explanation for why raw data cannot be shared). The supplementary files must be made available for review.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation scope and strength
- **Claim pointer** The manuscript claims that the method can accurately predict the effects of TF mutations on DNA binding specificity, but the experimental validation is limited to a small number of mutants in two bHLH proteins.
- **Evidence pointer** Results section, "A tetrahedron-based strategy..." and "Cross-validation..." subsections; Figure 4 (not shown)
- **Concern** The experimental validation of the method's predictive power for mutants is limited to four single and two double mutants of HES2 and ASCL2. While the results for ASCL2 are encouraging (R2 = 0.94), the results for HES2 are notably weaker (R2 = 0.61). The manuscript does not provide experimental validation for any homeodomain mutants, despite the method being applied to this family. This limited validation does not establish the generalizability of the method across different TF families or mutation types.
- **Why it matters** The central claim of the manuscript is that the method can predict the effect of mutations. A limited validation on a small, potentially non-representative set of mutants is insufficient to support this claim. The weaker performance on HES2 also raises questions about the robustness of the method.
- **Resolution test** The authors should expand the experimental validation to include a larger and more diverse set of mutants, including homeodomain mutants. They should also provide a more detailed analysis of the cases where the method performs poorly, to understand the limitations of the approach.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Benchmarking and comparison with existing methods
- **Claim pointer** The manuscript claims that FamilyCode outperforms closest-paralog and similarity regression, but the comparison is limited and may not be fair.
- **Evidence pointer** Results section, "Cross-validation..." subsection; Figure 3D and S3 (not shown)
- **Concern** The comparison with alternative methods is limited to two relatively simple baselines (closest-paralog and similarity regression). The comparison with rCLAMPS and DeepPBS is only performed on the homeodomain mutant prediction task, and the details of this comparison are not fully described. It is unclear whether the same training data, alignment, and evaluation metrics were used for all methods. A more comprehensive benchmark, including more recent and potentially more powerful methods, would be necessary to establish the superiority of FamilyCode.
- **Why it matters** The claim of improved performance is a key selling point of the method. Without a fair and comprehensive comparison, it is difficult to assess the true value of the approach relative to the state of the art.
- **Resolution test** The authors should provide a more detailed description of the comparison with rCLAMPS and DeepPBS, including the exact data splits, hyperparameters, and evaluation metrics. They should also consider benchmarking against other relevant methods, such as those based on structural modeling or deep learning.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological robustness and sensitivity analysis
- **Claim pointer** The manuscript claims that the method is robust and can be applied to different TF families, but the sensitivity of the method to key parameters and data quality is not assessed.
- **Evidence pointer** Methods section, "Construction of SVD-regression model" and "Assessment of prediction confidence" subsections
- **Concern** The method relies on several key choices, including the alignment of protein sequences, the selection of features (amino acid positions), and the threshold for feature inclusion. The manuscript does not provide a sensitivity analysis to show how the results change with these choices. For example, the choice of the F-test p-value threshold (0.05) is arbitrary and its impact on the results is not explored. The robustness of the method to the quality of the input binding models (e.g., models with different levels of noise) is also not assessed.
- **Why it matters** A method that is highly sensitive to arbitrary parameter choices or to the quality of the input data is of limited practical use. A sensitivity analysis would help to establish the robustness of the method and provide guidance for its application to new datasets.
- **Resolution test** The authors should perform a sensitivity analysis, varying the key parameters (e.g., p-value threshold, alignment method, training set size) and reporting the impact on prediction accuracy. They should also assess the method's performance on binding models with varying levels of noise.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Clinical relevance and interpretation
- **Claim pointer** The manuscript suggests that the method could be used to predict the impact of disease-associated mutations, but this claim is not directly supported by the data.
- **Evidence pointer** Abstract; Discussion section
- **Concern** The manuscript mentions "disease-associated mutations" in the abstract and introduction, but none of the tested mutants are disease-associated. The link between the predicted ΔΔΔG/RT values and phenotypic or clinical outcomes is not established. The discussion of the potential clinical relevance is speculative and not grounded in the presented results.
- **Why it matters** The potential to predict the impact of disease-associated mutations is a major motivation for this work. Without a direct demonstration on such variants, the clinical relevance of the method remains an unsubstantiated claim.
- **Resolution test** The authors should either test their method on a set of known disease-associated TF variants or temper their claims about clinical relevance. They could also discuss the potential challenges and limitations of applying their method to disease-associated variants.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Tetrahedral representation
- **Evidence pointer** Methods section, "Tetrahedron representation of DNA binding energies"
- **Issue** The description of the tetrahedral transformation is concise and may be difficult for readers to follow. The rationale for choosing this specific transformation and its properties (e.g., invariance, interpretability) could be explained more clearly.
- **Required correction** Provide a more detailed and intuitive explanation of the tetrahedral representation, including a worked example or a schematic figure. Discuss the advantages and limitations of this representation compared to other possible approaches.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Cross-validation and significance testing
- **Evidence pointer** Results section, "Cross-validation..." subsection; Methods section, "Assessment of prediction confidence"
- **Issue** The manuscript reports R2 and RMSD values for the cross-validation, but does not provide confidence intervals or statistical tests to assess the significance of the differences between methods. The bootstrap t-test is mentioned but not described in detail.
- **Required correction** Provide confidence intervals for the reported metrics and a more detailed description of the statistical tests used. Consider using a more robust approach, such as repeated cross-validation with different random seeds.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation of results
- **Affected element** Figures and tables
- **Evidence pointer** Results section; Figure legends (not shown)
- **Issue** The manuscript relies heavily on supplementary figures and tables, which are not provided. The main figures are not available for review, making it difficult to assess the quality of the data and the validity of the conclusions.
- **Required correction** Ensure that all key results are presented in the main figures and tables. Provide the supplementary materials for review.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the method's limitations is brief. The authors acknowledge that the method may be less suitable for de novo engineering, but they do not discuss other potential limitations, such as the dependence on the quality of the input binding models, the assumption of additivity, or the potential for context-dependent effects.
- **Required correction** Expand the discussion of limitations and potential avenues for future improvement.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Entire manuscript
- **Evidence pointer** Throughout
- **Issue** The writing is generally clear but could be more concise. Some sentences are long and complex, and the manuscript could benefit from careful editing.
- **Required correction** Revise the manuscript for clarity and conciseness.

## Risk / unsupported claims
- The claim that the method can predict the effect of "disease-associated mutations" is not supported by the data, as no disease-associated variants were tested.
- The claim that FamilyCode outperforms rCLAMPS and DeepPBS is not fully supported, as the comparison is not described in sufficient detail and may not be fair.
- The claim that the method is "general" and can be applied to other TF families is not fully supported, as it is only demonstrated on two families.
- The claim that the tetrahedral representation is "reference-free" and "robust" is not fully validated, as the properties of the representation are not thoroughly analyzed.
- The performance of the method on the homeodomain mutant prediction task is not experimentally validated, making it difficult to assess the practical utility of the method for this family.