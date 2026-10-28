## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, results, discussion, and conclusion. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific and technical evaluation of the machine learning model, its validation, and the biological claims made. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors present Plant-DTI, a machine learning-based predictor for transcription factor (TF) DNA-binding domain (DBD) and transcription factor binding site (TFBS) interactions in plants. They claim it is the first model covering 30 plant TF families from 22 species, introduces a novel TFBS feature representation called "TFBS base-preference," achieves high predictive accuracy, outperforms existing methods, and successfully predicts regulators of the cassava MeSUS1 gene, including a TF experimentally verified by yeast one-hybrid.
- **Visible evidence base** Main text figures (Figures 1-7), tables (Table 1), and in-text performance metrics. Supplementary tables and figures are referenced but not available for review.
- **Missing materials affecting confidence** Supplementary Tables S1-S6, Supplementary Figures S1-S7, Supplementary Data 1.1 and 1.2, and the web application implementation. These are essential for verifying data processing, model configuration, and validation details.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant gap in plant transcriptional regulation by developing a machine learning predictor with broader TF family coverage than prior tools. The core idea of using a position-specific nucleotide preference representation for TFBS is reasonable and shows improved performance over binary encoding in their benchmarks. However, several technical aspects require clarification and additional evidence before the claims can be fully accepted. The validation with independent ChIP-seq data is limited in scope, the comparison with state-of-the-art methods lacks detail on data handling, and the biological application to MeSUS1 is presented as a demonstration but the novelty of the finding is not clearly established. The manuscript is potentially valuable but currently does not fully support all stated conclusions.
- **Who would be interested in the results, and why** Researchers studying plant transcriptional regulation, particularly those working on TF binding site prediction, gene regulatory network inference, and crop improvement. The tool could be useful for prioritizing candidate TFs for experimental validation in less-studied plant species. The methodological contribution on TFBS feature representation may also interest computational biologists working on protein-DNA interaction prediction.
- **Major strengths**  
  1. Broad coverage of plant TF families and DBD types compared to existing tools, addressing a clear gap in plant-specific resources.  
  2. The proposed TFBS base-preference feature is a simple but sensible idea that improves over binary encoding, with systematic evaluation across multiple classifiers.  
  3. Validation with independent ChIP-seq data and comparison with two existing methods adds credibility.  
  4. The application to cassava MeSUS1 demonstrates practical utility and includes experimental verification of one predicted TF.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness of validation  
  - **Claim pointer** The manuscript claims Plant-DTI was "validated with 22 independent ChIP-seq datasets" and accurately predicted DBD-TFBS pairs.  
  - **Evidence pointer** Section "Validation of Plant-DTI by ChIP-seq data", Figure 5, Supplementary Figure S5  
  - **Concern** The validation uses only 14 DBD-TFBS interactions from 11 TFs, all from Arabidopsis thaliana. This is a small and taxonomically narrow test set. The claim of validation across 22 datasets is misleading because the number of unique TFs and interactions is limited. Additionally, the criteria for selecting these 14 interactions and the handling of multiple ChIP-seq datasets for the same TF are not described.  
  - **Why it matters** A model intended for plant-wide predictions must demonstrate generalization across diverse TF families and species. The current validation does not adequately support the claim of broad applicability.  
  - **Resolution test** Provide a detailed breakdown of the 22 ChIP-seq datasets, including the number of unique TFs, TF families, and species. Include performance metrics per TF family and per species. If possible, validate on additional species beyond Arabidopsis.  
  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness of comparison with existing methods  
  - **Claim pointer** The manuscript states Plant-DTI showed "a figure of merit in sensitivity and specificity" compared to PWM and TSPTFBS methods.  
  - **Evidence pointer** Section "Comparison of Plant-DTI performances with state-of-art methods", Table 1  
  - **Concern** The comparison is based on 10 ChIP-seq and 57 DAP-seq datasets, but the details of how these datasets were processed for each method are not provided. It is unclear whether the same negative sets, the same TFBS definitions, and the same evaluation thresholds were used for all methods. Without this information, the comparison may be biased.  
  - **Why it matters** Fair benchmarking is essential to support the claim of superiority. Differences in data preprocessing or evaluation protocols could explain the observed performance gaps.  
  - **Resolution test** Describe the exact input data, negative set construction, and scoring thresholds used for PWM and TSPTFBS. Provide per-dataset results and statistical significance tests for the performance differences.  
  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Reproducibility and data availability  
  - **Claim pointer** The model was constructed from DBD-TFBS interactions in the CIS-BP database, and the final dataset included 3,931,070 and 2,482,629 interactions for RP and RW models, respectively.  
  - **Evidence pointer** Section "Plant DBD-TFBS interactions datasets", Section "Training and test datasets", Supplementary Tables S1, S2  
  - **Concern** The process of generating positive and negative datasets is described, but the exact filtering criteria, the number of TFs and TFBSs removed at each step, and the final composition of the training and test sets are not fully detailed in the main text. The supplementary tables are referenced but not available for review. Without these details, the reproducibility of the dataset construction is questionable.  
  - **Why it matters** Reproducibility is a core requirement for computational tools. Other researchers must be able to reconstruct the training data and model to verify and build upon the work.  
  - **Resolution test** Provide a complete data processing pipeline, including all filtering steps, in the main text or a clearly accessible supplement. Make the final training and test datasets publicly available in a standard format.  
  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Biological claim support  
  - **Claim pointer** The application to MeSUS1 predicted 150 TFs, including MeER72, which was experimentally verified by yeast one-hybrid.  
  - **Evidence pointer** Section "Utilization of Plant-DTI to search for putative TFs controlling sucrose synthase 1 gene in cassava", Figure 7  
  - **Concern** The biological demonstration is presented as a key outcome, but the analysis is limited to a single gene. The claim that Plant-DTI "helped to fill the knowledge gap" is based on one example. The novelty of the MeERF72-MeSUS1 interaction is not discussed in the context of prior knowledge, and the functional relevance of this interaction is not experimentally tested beyond binding.  
  - **Why it matters** A single example, even with binding validation, is insufficient to demonstrate broad biological utility. The claim of filling a knowledge gap requires stronger evidence or a more cautious interpretation.  
  - **Resolution test** Either expand the biological validation to multiple genes and TFs, or temper the claim to reflect that this is a single case study. Discuss the novelty of the MeERF72-MeSUS1 interaction relative to existing literature.  
- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity of methods  
  - **Affected element** TFBS base-preference definition  
  - **Evidence pointer** Section "TFBS base-preference", Supplementary Figure S1  
  - **Issue** The equation for Pj(X) is mentioned but not displayed in the text. The description of how probabilities are calculated from the 343 interactions is incomplete.  
  - **Required correction** Display the equation explicitly and provide a worked example of how a TFBS sequence is converted into the base-preference feature vector.  
  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Model selection rationale  
  - **Affected element** Classifier choice  
  - **Evidence pointer** Section "Plant-DTI model construction", Supplementary Tables S4, S5  
  - **Issue** The authors state that Random Forest was selected based on F1-score, but the performance differences between classifiers are not shown in the main text.  
  - **Required correction** Include a supplementary figure or table showing the performance of all tested classifiers and feature combinations to justify the final model choice.  
  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Threshold selection  
  - **Affected element** Probability threshold of 0.7  
  - **Evidence pointer** Section "Validation of Plant-DTI by ChIP-seq data", Figure 5  
  - **Issue** The choice of 0.7 as the default threshold is based on a trade-off between sensitivity and specificity, but the analysis appears to be based on a small number of interactions.  
  - **Required correction** Provide a more detailed analysis of threshold selection, including precision-recall curves and the impact of threshold choice on downstream predictions.  
  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Web tool accessibility  
  - **Affected element** Plant-DTI web application  
  - **Evidence pointer** Section "Abstract", Section "Conclusion"  
  - **Issue** The web application is mentioned but no URL is provided in the manuscript text.  
  - **Required correction** Include the URL for the Plant-DTI web application in the Data Availability Statement or a dedicated section.  
- **Technical failings that need to be addressed before the case is established**  
  R1-M1, R1-M2, R1-M3 must be addressed. The validation set is too small and narrow, the comparison with existing methods lacks methodological detail, and the dataset construction is not fully reproducible from the provided information.
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The TFBS base-preference feature is a novel contribution, but the overall approach of machine learning for TFBS prediction is not new.  
  - Scientific importance: Moderate. The tool addresses a real gap in plant research, but the demonstrated impact is limited to a single case study.  
  - Interdisciplinary readership: Limited. The work is primarily of interest to plant molecular biologists and computational biologists. The methods are not broadly accessible to other disciplines.  
  - Technical soundness: Currently insufficient. The validation and comparison concerns need to be resolved.  
  - Readability for nonspecialists: Acceptable. The manuscript is generally clear, but some methods sections assume familiarity with machine learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea has merit, and the tool could be valuable to the plant research community. However, the current evidence does not fully support the claims of broad validation and superiority over existing methods.

## Risk / unsupported claims
- The claim of being "the first machine-learning model that covered the largest experimental datasets of 30 plant TF families" is not verifiable without a systematic comparison of existing resources.  
- The claim that Plant-DTI "accurately predicted the measured DBD-TFBS pairs" is based on a small validation set of 14 interactions from one species.  
- The claim that the TFBS base-preference "enhanced the specificity of TFBS to DBD types" is supported by their data but the mechanism is not fully explained.  
- The biological significance of the MeERF72-MeSUS1 interaction is presented as a finding but its novelty relative to prior knowledge is not established.  
- The statement that Plant-DTI can predict TF-TFBS interactions for "any plant species" is an extrapolation not directly supported by the validation data.