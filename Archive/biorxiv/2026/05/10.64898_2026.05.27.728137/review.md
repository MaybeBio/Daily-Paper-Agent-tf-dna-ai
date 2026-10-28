## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, figure legends) as provided.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to the presented evidence, and alignment with Nature-style criteria. No assessment of code availability, server functionality, or supplementary data files beyond what is described in the text.
- **Shared manuscript claim summary** The authors present ModCRE-NN, a machine-learning framework integrating structure-derived and evolutionary Position Weight Matrices (PWMs) into a 20-channel tensor representation. Three architectures (regression, CNN, Transformer) are trained to reconstruct TF binding motifs. Claims include: (1) integration of structural and evolutionary information improves PWM prediction; (2) CNN/Transformer outperform regression under low homology and high structural uncertainty; (3) models denoise heterogeneous motif assemblies and produce stable consensus representations; (4) a reliability framework estimates prediction quality as a function of evolutionary similarity, cluster consistency, and TF family.
- **Visible evidence base** Abstract, Introduction, Methods (sections 1-9), Results and Discussion (sections 1-3), Conclusions, Figure legends for Figures 1-5 and Supplementary Figures S1-S10. No actual data, figures, or tables are visible in the provided material.
- **Missing materials affecting confidence** All primary data (figures, tables, supplementary results) are absent. Quantitative performance metrics, baseline comparisons, statistical significance tests, and detailed hyperparameter settings are referenced but not shown. The manuscript text alone is insufficient to verify the central claims.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely the prediction of TF binding specificity by integrating structural and evolutionary information. The conceptual framework, combining structure-derived PWMs with evolutionary PWMs across identity intervals into a multi-channel tensor, is interesting and potentially useful. However, the provided text is largely a methodological description without the supporting evidence needed to evaluate its performance. The claims of improved prediction, denoising, and reliability estimation are plausible but unverifiable from the current material. The writing is clear but the lack of data prevents a rigorous assessment of technical soundness and scientific impact.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on TF binding site prediction, motif discovery, and regulatory genomics. Researchers interested in interpretable deep learning for biological sequence analysis and those developing integrative methods that combine structural and evolutionary information would also find this work relevant. The potential for a web server may attract experimental biologists seeking to predict binding motifs for uncharacterized TFs.
- **Major Strengths**
    - The conceptual integration of structural and evolutionary information into a unified tensor representation is a novel and sensible approach.
    - The use of multiple architectures, including an interpretable baseline, allows for a comparative analysis of model behavior.
    - The explicit focus on uncertainty estimation and reliability is a valuable contribution to the field.
    - The consideration of homology leakage and the construction of a stratified independent test set demonstrate methodological awareness.
- **Major Concerns**
    - **R1-M1** (Blocking: Yes)
    - **R1-M2** (Blocking: Yes)
    - **R1-M3** (Blocking: Yes)
    - **R1-M4** (Blocking: No)
- **Minor Comments**
    - **R1-m1**
    - **R1-m2**
    - **R1-m3**
- **Technical failings that need to be addressed before the case is established** The absence of all empirical results, including performance metrics, baseline comparisons, and statistical analyses, is a fundamental failing. The claims of superiority for CNN/Transformer models and the denoising capability are not supported by any visible data. The reliability framework is described but its accuracy and calibration are not demonstrated.
- **Assessment against Nature-style criteria**
    - **Originality:** The specific combination of structure-derived and evolutionarily diverse PWMs into a multi-channel tensor for deep learning appears novel. However, the originality of the overall concept of integrating these data types is incremental.
    - **Scientific importance:** The problem of predicting TF specificity is important. If the method significantly improves prediction, especially in low-homology regimes, it would be of interest. However, the importance cannot be assessed without performance data.
    - **Interdisciplinary readership:** The topic is of interest to computational biologists and molecular biologists. The methods are described in a way that is accessible to a computational audience, but the lack of clear biological validation or a compelling demonstration of utility limits its broader appeal.
    - **Technical soundness:** The methodological design is reasonable, but the technical soundness of the implementation and the validity of the results cannot be evaluated from the text alone. The absence of data is a critical flaw.
    - **Readability for nonspecialists:** The abstract and introduction are clear. The methods section is technical but understandable. The results section, however, is difficult to follow without the figures and data it references.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a plausible and potentially interesting framework, but the complete absence of empirical data prevents any assessment of its validity, performance, or significance. A full review is contingent on the availability of the actual results, figures, and supplementary materials.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence
- **Claim pointer** The manuscript claims that CNN and Transformer architectures show superior robustness under low evolutionary similarity and increased structural uncertainty, and that all models improve upon baseline input motifs.
- **Evidence pointer** Results and Discussion, Section 3; Figures 3, S9
- **Concern** The central performance claims are made without presenting any of the underlying data. The text describes trends in figures that are not provided. There are no quantitative metrics, no statistical tests, and no direct comparison of the proposed models against the baseline input PWMs or against existing state-of-the-art methods.
- **Why it matters** The core scientific contribution of this work is the claimed improvement in PWM prediction. Without the actual performance data, the validity of the entire approach cannot be assessed. The claims of "superior robustness" and "denoising" are unsupported assertions.
- **Resolution test** Provide the actual performance data for all models and baselines across all conditions. Include quantitative metrics (e.g., TOMCAT scores, correlation coefficients), statistical significance tests, and a comparison with existing methods. The figures must be made available for review.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes a detailed methodology for data construction, model training, and evaluation.
- **Evidence pointer** Methods, Sections 1-9
- **Concern** The methods are described at a high level, but critical details necessary for reproduction are missing. For example, the exact architecture of the CNN and Transformer (number of layers, heads, etc.) is not specified in the main text. The hyperparameter optimization is mentioned, but the final chosen hyperparameters are not listed. The process for generating structure-derived PWMs with ModCRElib is referenced but not detailed.
- **Why it matters** Reproducibility is a cornerstone of scientific research. Without complete methodological details, other researchers cannot replicate the experiments or build upon the work. This is a significant barrier to the manuscript's utility and impact.
- **Resolution test** Provide full architectural details for all models, final hyperparameter values, and a complete description of the ModCRElib structure-derived PWM generation process. This information could be included in the main text or a detailed supplementary methods section.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of Evaluation
- **Claim pointer** The manuscript claims that the independent test set was constructed to minimize homology leakage and that the evaluation is unbiased.
- **Evidence pointer** Methods, Section 1; Methods, Section 4
- **Concern** The description of the redundancy reduction and test set construction is not sufficient to assess its effectiveness. The text states that CD-HIT at 40% sequence identity was used, but it is unclear if this was applied to the full TF sequences or only the DNA-binding domains. The manuscript also does not describe how the "independent" test set relates to the training set in terms of TF families, which could lead to inflated performance if certain families are overrepresented.
- **Why it matters** A biased evaluation can lead to overly optimistic performance estimates and false conclusions about the method's generalizability. The validity of the entire evaluation hinges on the rigor of the data partitioning strategy.
- **Resolution test** Provide a detailed description of the redundancy reduction process, including the exact sequences used for clustering. Show the distribution of TF families in the training, validation, and test sets. Demonstrate that the test set is truly independent and representative.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Significance of Contribution
- **Claim pointer** The manuscript claims that the proposed framework provides a "general strategy for integrating heterogeneous biological evidence" and that the reliability framework is a key contribution.
- **Evidence pointer** Conclusions; Results and Discussion, Section 3
- **Concern** While the reliability framework is an interesting addition, its novelty and utility are not clearly demonstrated. The text describes the methods used (Random Forest, exponential interpolation) but does not show how this framework outperforms simpler baselines or how it would be used in practice. The claim of a "general strategy" is also broad and not fully supported by the single application presented.
- **Why it matters** The manuscript's significance is partly based on the novelty and utility of its contributions. If the reliability framework is not shown to be accurate or useful, its value is diminished. The claim of a general strategy needs to be substantiated with evidence of its applicability beyond the specific case of PWM prediction.
- **Resolution test** Provide a validation of the reliability framework, showing that its confidence estimates are well-calibrated. Compare its performance to simpler baselines. Discuss the potential for generalization to other types of biological data integration problems.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion, Section 1
- **Evidence pointer** Figure S7
- **Issue** The text states that the Transformer model achieved the "best overall predictive accuracy," but the difference from the CNN model appears marginal based on the described MSE values (0.1812 vs 0.1837). The text also notes that "many trials with the same parameters were not as good as this," which raises questions about the stability of the Transformer's performance.
- **Required correction** Clarify whether the performance difference between the CNN and Transformer is statistically significant. Discuss the stability of the Transformer's performance across different random seeds or initializations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results and Discussion, Section 3
- **Evidence pointer** Figure 5
- **Issue** The description of the CTCF case study is qualitative. The text states that the predicted motif is "highly similar" to the canonical profile, but no quantitative similarity score is provided for this specific example.
- **Required correction** Provide the quantitative TOMCAT similarity score for the CTCF predictions shown in Figure 5, along with the expected score from the reliability model.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, Section 5
- **Evidence pointer** Location not provided
- **Issue** The manuscript mentions that details of the architectures can be found in the supplementary material. For a self-contained review, it is important to have at least a summary of the key architectural choices in the main text.
- **Required correction** Include a brief description of the CNN and Transformer architectures in the main text, such as the number of layers, filter sizes, and attention heads.

## Risk / unsupported claims
- The claim that CNN and Transformer models "denoise heterogeneous motif assemblies and reconstruct stable consensus DNA-binding representations" is unsupported by the provided evidence.
- The claim that the models "effectively denoise" and "reduce prediction variance" is not verifiable without the actual data distributions.
- The claim that the reliability framework provides "biologically informed confidence estimates" is not validated by any presented results.
- The claim that the method provides a "general strategy for integrating heterogeneous biological evidence" is an overstatement based on the single application shown.
- The overall performance of the models relative to existing state-of-the-art methods is not assessable.