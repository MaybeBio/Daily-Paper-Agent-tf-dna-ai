## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological soundness, interpretability of the machine learning approach, biological claims, and reproducibility based on the provided manuscript text
- **Shared manuscript claim summary** The authors built neural network models to predict V(D)J recombination efficiency from DNA sequence at the H4-S2 region of the 12-RSS, used SHAP-based explainability to identify first- and second-order nucleotide interactions, and trained a nonamer-informed model to detect heptamer-nonamer crosstalk
- **Visible evidence base** Main text figures referenced (Figs 1-9), supplementary figures S1-S12, supplementary datasets S1-S2, and methods descriptions
- **Missing materials affecting confidence** Actual figure images, supplementary dataset contents, code repository contents, and detailed hyperparameter values were not provided in the submitted material

## Reviewer
- **Overall assessment** This manuscript presents a useful application of neural network modeling and SHAP-based interpretability to a well-defined biological problem: sequence determinants of V(D)J recombination efficiency. The work builds on a substantial experimental dataset (SARP-seq) and offers a novel analytical approach (CRV analysis) for extracting pairwise interaction information from SHAP values. The biological findings, particularly the identification of position-specific nucleotide preferences and the evidence for heptamer-nonamer crosstalk, are potentially valuable to the immunology and genome rearrangement communities. However, several technical aspects require clarification and strengthening before the conclusions can be fully accepted. The manuscript would benefit from clearer justification of methodological choices, more rigorous validation of the interpretability claims, and additional discussion of limitations.

- **Who would be interested in the results, and why** Immunologists studying V(D)J recombination and antigen receptor diversity would be the primary audience. Computational biologists working on sequence-function models and interpretable machine learning would also find the CRV methodology of interest. Researchers studying RAG-mediated off-target recombination and genomic instability may find the nonamer crosstalk findings relevant. The work could also interest those developing predictive models for variant effect prediction in regulatory genomic elements.

- **Major strengths** The manuscript addresses a longstanding question in V(D)J recombination with a novel computational approach. The use of a large, experimentally generated dataset (4096 sequences) provides a solid foundation. The development of CRV analysis as a method to extract pairwise interactions from SHAP values is creative and potentially widely applicable. The validation using an independent fluorescence-based assay strengthens the claims. The identification of position-specific nucleotide preferences and the modular behavior between heptamer and nonamer regions provides new biological insight.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of interpretability method
- **Claim pointer** The authors claim that their CRV analysis of pairwise SHAP value comparisons "quantifies the typical direction (angle) and the maximum strength (length) of how changes in one feature's SHAP value affects another feature's SHAP value" and that this captures second-order interactions between nucleotide positions.
- **Evidence pointer** Materials and methods, "Novel pairwise SHAP value comparative analysis" section; Results, "H4S2 model SHAP reveal nucleotide:position first-order interactions" section; Figure 6
- **Concern** The CRV method is presented as a novel approach for identifying second-order interactions, but the manuscript does not provide sufficient validation that the vector angle and length derived from PCA of SHAP value distributions actually correspond to true interaction effects in the underlying model. SHAP values for categorical one-hot encoded features are inherently constrained by the sum-to-zero property across the four nucleotide categories at each position, and the pairwise distributions may reflect marginal effects rather than genuine interactions. The authors do not compare their CRV results against established interaction detection methods (e.g., SHAP interaction values, Friedman's H-statistic, or permutation-based interaction measures) to demonstrate that CRV provides unique or superior information. Without such validation, the biological interpretations drawn from CRV groupings (e.g., the claim that H6-H7 makes a dominant contribution) may be artifacts of the method rather than true properties of the system.
- **Why it matters** The central novelty of this manuscript lies in the CRV approach for extracting interaction information. If the method is not rigorously validated, the biological conclusions about pairwise nucleotide interactions and heptamer-nonamer crosstalk are not reliable. This affects the core contribution of the paper.
- **Resolution test** The authors should validate CRV against established interaction detection methods on the same model, demonstrate with simulated or synthetic data that CRV correctly recovers known interaction structures, and provide theoretical justification for why PCA on SHAP value distributions captures interaction effects rather than marginal effects. Alternatively, they could use SHAP interaction values (which are directly supported by the SHAP framework) to confirm the CRV findings.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation and generalizability
- **Claim pointer** The authors claim the H4S2 model "effectively predicts the V(D)J recombination efficiency level for different 12-RSS sequences" and that the nonamer-informed model "outperformed the H4S2 model's predictions."
- **Evidence pointer** Results, "Overview of generating the H4S2 model" section; Results, "The absence of sequence coverage from the nonamer stifles H4S2 model prediction" section; Figures 2 and 7
- **Concern** The manuscript reports performance metrics (FVAP, Spearman correlation, RMSE) but does not provide confidence intervals, statistical comparisons between models, or analysis of prediction errors across the sequence space. The claim that the nonamer-informed model outperforms the H4S2 model is made without formal statistical testing. Additionally, the validation on experimental replicates is presented but the manuscript does not discuss whether the model's performance is consistent across different regions of the sequence space (e.g., GC content, presence of cryptic motifs). The single outlier sequence (AGTG|CT) is mentioned but not analyzed in depth. The manuscript would benefit from a more systematic error analysis and discussion of where the model fails.
- **Why it matters** Without rigorous model validation, the biological interpretations derived from the model may not be generalizable. The claim of outperformance between models needs statistical support. Understanding model limitations is essential for assessing the reliability of the biological conclusions.
- **Resolution test** Provide confidence intervals for all performance metrics, perform formal statistical comparison between models (e.g., paired tests across test sets), analyze prediction errors stratified by sequence features, and discuss the implications of the outlier sequence for model reliability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation and mechanistic claims
- **Claim pointer** The authors state that "H4-S2 sequences with lower melting temperature (Tm) trend toward higher levels of recombination efficiency" and propose that this reflects the energetic barrier for conformational changes required for RAG cleavage.
- **Evidence pointer** Results, "Melting propensity of the H4-S2 region" section; Figure 4; Discussion
- **Concern** The correlation between melting temperature and recombination efficiency is weak (Spearman rho = -0.28) and the manuscript does not adequately address alternative explanations. The melting temperature calculation uses a nearest-neighbor model that may not accurately reflect the thermodynamic context within the RAG-DNA complex. The claim that decreased Tm facilitates the conformational changes required for cleavage is speculative and not directly tested. The manuscript would benefit from a more nuanced discussion of what the weak correlation might mean and what alternative mechanisms could explain the observed relationship.
- **Why it matters** The melting temperature analysis is presented as a biological insight, but the weak correlation and lack of direct mechanistic testing weaken this claim. Overinterpretation of correlational findings could mislead the field.
- **Resolution test** The authors should either strengthen the mechanistic interpretation with additional experimental or computational evidence, or temper the claims to reflect the correlational nature of the finding. They should also discuss alternative explanations for the observed relationship.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and data availability
- **Claim pointer** The authors state that "the code to generate and analyze the models are available through a Zenodo Repository and a GitHub Repository" and that "the complete iSAR1 dataset is listed in Supplementary Dataset S1."
- **Evidence pointer** Data availability section; Materials and methods
- **Concern** While the authors state that code and data are available, the manuscript does not provide sufficient detail on the computational environment, dependency versions, or expected runtime for the model training and analysis. The use of AI-assisted code development (ChatGPT, Gemini) raises questions about code quality assurance and reproducibility. The manuscript would benefit from a more detailed description of the computational workflow, including specific library versions, random seeds, and any preprocessing steps that could affect results.
- **Why it matters** Reproducibility is a core requirement for computational biology papers. Without sufficient detail, other researchers may not be able to replicate the results or apply the methods to their own data.
- **Resolution test** Provide a detailed computational environment specification, include all random seeds, and ensure that the code repositories contain complete, well-documented workflows that can be executed without additional information.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction, first paragraph
- **Issue** The abstract and introduction use dense, technical language that may be challenging for non-specialist readers. The significance of the work could be stated more clearly.
- **Required correction** Consider revising the abstract to include a clearer statement of the biological question and the practical implications of the findings. The introduction could benefit from a brief explanation of why understanding RSS sequence specificity matters for human health.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 5, 6, and 7
- **Evidence pointer** Results sections referencing these figures
- **Issue** The manuscript references complex figures (e.g., CRV plots, cumulative length/angle plots) but the text does not always provide sufficient guidance for interpretation. The figures are not included in the submitted material, making it difficult to assess their clarity.
- **Required correction** Ensure that figure captions are self-explanatory and that the text provides clear guidance on how to interpret each panel. Consider adding schematic diagrams to explain the CRV methodology.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections reporting correlations and performance metrics
- **Evidence pointer** Results, "H4S2 model performance compared to the historic RIC score metric" section; Results, "Melting propensity of the H4-S2 region" section
- **Issue** Correlation coefficients are reported without confidence intervals or p-values in some instances. The manuscript would benefit from more complete statistical reporting.
- **Required correction** Add confidence intervals and p-values for all reported correlation coefficients and performance metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion, final paragraphs
- **Issue** The discussion of limitations is brief and does not fully address the constraints of the experimental system (e.g., plasmid-based assay, constant 23-RSS, limited sequence coverage in certain regions).
- **Required correction** Expand the limitations section to include a more thorough discussion of the experimental constraints and how they might affect the generalizability of the findings.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Multiple sections
- **Issue** The terms "recombination efficiency" and "recombination activity" are used interchangeably. The manuscript should define these terms and use them consistently.
- **Required correction** Define the terms at first use and use them consistently throughout the manuscript.

## Risk / unsupported claims
- The claim that CRV analysis captures true second-order interactions between nucleotide positions is not validated against established methods and may reflect artifacts of the SHAP value distribution for categorical features.
- The claim that decreased melting temperature facilitates RAG-mediated cleavage through reduced energetic barriers is speculative and not directly tested.
- The claim that the nonamer-informed model outperforms the H4S2 model lacks formal statistical testing.
- The biological interpretation of CRV groupings (e.g., "H6-H7 makes a dominant contribution") is presented as definitive when it is derived from a single modeling approach without cross-validation against other interpretability methods.
- The statement that "the models have demonstrated robust prediction" is somewhat overstated given the limited error analysis and the acknowledged outlier sequence.
- The claim that the approach "could be leveraged to differentiate if newly identified SNPs would significantly affect RSS usage" is speculative and not demonstrated in this work.