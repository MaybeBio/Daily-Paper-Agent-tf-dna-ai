## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality based solely on the provided text
- **Shared manuscript claim summary** The authors report the identification of novel cis-regulatory elements (CREs) and promoter structures involved in iron (Fe) excess response in rice using bioinformatics approaches, including network analysis (WGCNA) and a machine-learning tool (MAMA), applied to previously published microarray data. They claim to have found four expression clusters, 560 CRE candidates, and 42 important conserved sequences, with a Boruta-XGBoost model achieving approximately 83% accuracy in explaining expression patterns.
- **Visible evidence base** Microarray data from Aung et al. (2018b) for Fe excess; microarray data from Ogo et al. (2006) for Fe deficiency; microarray data from Suzuki et al. (2012) for Zn deficiency; bioinformatics analyses using WGCNA, PlantPAN3, MAMA, Boruta, XGBoost, and party packages; supplementary tables and figures referenced but not provided
- **Missing materials affecting confidence** Supplementary figures and tables (Supplementary Figures 1–6, Supplementary Tables 1–11, Supplementary Data 1–4) are referenced but not available for review; detailed parameter settings for MAMA, WGCNA, and XGBoost are not fully described; raw microarray data and preprocessing steps are not described in sufficient detail; no experimental validation data are provided

## Reviewer
- **Overall assessment** This manuscript presents a bioinformatics-driven exploration of cis-regulatory elements associated with Fe excess response in rice. The work builds on previously published transcriptomic data and applies a combination of established and custom computational tools. The identification of four expression clusters and the use of MAMA to extract candidate CREs is a reasonable approach, and the reported model accuracy of 83% is notable. However, the manuscript has several significant weaknesses. The lack of experimental validation for any of the predicted CREs limits the biological significance of the findings. The description of the computational methods is incomplete, particularly regarding parameter choices, data preprocessing, and validation procedures. The claim of "novel" CREs is not adequately supported, as no comparison to existing databases or known motifs is systematically presented. The manuscript would benefit from clearer presentation of the statistical significance of motif enrichment and a more critical discussion of the limitations of the approach. Overall, the work is of interest to the plant iron homeostasis community, but the current evidence does not fully establish the functional relevance of the identified elements.
- **Who would be interested in the results, and why** Researchers studying iron homeostasis in plants, particularly those focused on rice and other graminaceous crops, would be interested in this work. The identified CRE candidates and promoter structure models could inform future studies on transcriptional regulation under Fe excess. Additionally, researchers developing bioinformatics tools for cis-regulatory element discovery may find the application of MAMA to a new stress condition of interest. The potential for using these promoter elements in crop improvement for Fe tolerance would also attract plant biotechnologists.
- **Major strengths** The study addresses an important and understudied topic: the transcriptional regulation of Fe excess response in rice. The use of multiple complementary bioinformatics approaches (network analysis, motif discovery, machine learning) is a methodological strength. The integration of data from Fe excess, Fe deficiency, and Zn deficiency conditions provides a broader context for understanding Fe homeostasis regulation. The reported high accuracy of the combined MAMA-PLACE model is encouraging and suggests the identified elements have predictive value.
- **Major Concerns** The major concerns are detailed below.
- **Minor Comments** The minor comments are detailed below.
- **Technical failings that need to be addressed before the case is established** The lack of experimental validation is the most critical technical failing. The manuscript is purely computational, and no evidence is provided that any of the predicted CREs actually function in vivo. Additionally, the incomplete description of the computational methods, particularly the MAMA algorithm parameters and the WGCNA soft-thresholding power selection, prevents reproducibility. The statistical framework for determining which motifs are "important" is not fully described, and the claim of novelty is not rigorously established.
- **Assessment against Nature-style criteria** 
  - **Originality**: Moderate. The application of MAMA to Fe excess response is novel, but the overall approach of combining network analysis and motif discovery is not new. The identification of specific novel motifs, if validated, would increase originality.
  - **Scientific importance**: Moderate. Understanding Fe excess regulation is important for rice production in acidic soils. However, the purely computational nature of the study limits its immediate impact. The findings are hypothesis-generating rather than definitive.
  - **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to plant molecular biologists and bioinformaticians working on iron homeostasis. The lack of experimental validation and the specialized nature of the topic would limit broader appeal.
  - **Technical soundness**: The computational approach is generally sound, but the incomplete description of methods and the lack of validation reduce confidence. The reported accuracies are promising but need more rigorous statistical backing.
  - **Readability for nonspecialists**: The manuscript is reasonably well-written but assumes familiarity with bioinformatics concepts and plant iron biology. The abstract is clear, but the methods and results sections would be challenging for nonspecialists.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a potentially useful computational framework and candidate elements, but the lack of experimental validation and incomplete methodological details prevent the claims from being fully supported. The work could become publishable with significant revisions, including experimental validation or at least a more rigorous computational validation strategy, and a more complete description of methods.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have identified "novel cis-regulatory elements" and "42 important conserved sequences of CREs directly related to the Fe excess response."
- **Evidence pointer** Results section, Table 3, Supplementary Tables 4–11
- **Concern** The claim of novelty is not adequately supported. The authors do not systematically compare their identified motifs against existing databases of known plant cis-regulatory elements (e.g., PLACE, PlantPAN, JASPAR, or literature-curated motifs). Without such a comparison, it is impossible to determine which of the 560 candidates are truly novel and which are known elements previously associated with other stress responses. Furthermore, the criteria for designating a motif as "important" are not clearly defined. The authors state that 42 motifs were selected through Boruta-XGBoost, but the specific selection threshold and the statistical significance of these selections are not reported.
- **Why it matters** The central claim of the manuscript is the discovery of novel regulatory elements. If this claim is not rigorously established, the scientific contribution is substantially diminished. The lack of a clear definition of "importance" also undermines the reproducibility and interpretability of the results.
- **Resolution test** The authors should provide a comprehensive comparison of their identified motifs against known plant cis-regulatory element databases, clearly indicating which motifs are novel and which are known. They should also provide a detailed description of the Boruta feature selection process, including the number of runs, the threshold for importance, and the statistical significance of the selected features. Ideally, they would also provide a list of the 42 important motifs with their sequences, genomic locations, and associated genes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the MAMA-based model "accurately classified genes as Fe excess-regulated genes with CRE candidates or as non-responsive genes" with accuracy above 86% (Table 2) and that the combined MAMA-PLACE model achieved 83% accuracy (Table 1).
- **Evidence pointer** Results section, Tables 1 and 2, Methods section
- **Concern** The description of the model construction and validation is insufficient. The authors do not specify the exact training and test data split, the cross-validation procedure (beyond mentioning "5 times cross validation"), or the hyperparameters used for the XGBoost model. The use of "under sampled test data" is mentioned but not explained. It is unclear whether the reported accuracy is on a held-out test set or on training data. The potential for overfitting, particularly given the large number of features (560 motifs) relative to the number of samples, is not addressed. The authors also do not report confidence intervals or variability across cross-validation folds.
- **Why it matters** The reported high accuracy is a key piece of evidence supporting the utility of the identified CREs. If the model is overfitted or the validation procedure is flawed, the accuracy estimates are meaningless, and the entire computational framework is called into question.
- **Resolution test** The authors should provide a detailed description of the model training and validation procedure, including the exact data split, the cross-validation scheme, and the hyperparameter tuning process. They should report the mean and standard deviation of accuracy across cross-validation folds. They should also address the potential for overfitting, perhaps by comparing the performance of the full model to a model trained on a reduced set of features or by using a permutation test to establish a baseline accuracy.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that their findings "will provide a comprehensive resource for discovery of genes and transcription factors involved in Fe excess-responsive pathways" and suggest that the identified elements could be used to "produce new rice varieties that are tolerant of Fe excess."
- **Evidence pointer** Abstract, Discussion, Conclusion
- **Concern** The manuscript is entirely computational, and no experimental validation is provided for any of the predicted CREs or the promoter structure models. The authors do not test whether any of the identified motifs are actually bound by transcription factors, whether they are necessary or sufficient for Fe excess-responsive gene expression, or whether they function in a heterologous system. The claim that these elements could be used for crop improvement is speculative without such validation.
- **Why it matters** The biological significance of the findings is entirely dependent on the functional relevance of the identified elements. Without experimental validation, the manuscript remains a bioinformatics exercise with unverified biological implications. The claims of practical application are premature.
- **Resolution test** The authors should either provide experimental validation of at least a subset of the identified CREs (e.g., using electrophoretic mobility shift assays, yeast one-hybrid assays, or reporter gene constructs in transgenic plants) or substantially temper their claims about the biological and practical significance of their findings. At minimum, they should clearly state that the identified elements are computational predictions that require experimental validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the maximum accuracy was obtained using both PLACE and MAMA, at 83.0% which is the highest" (Table 1).
- **Evidence pointer** Results section, Table 1
- **Concern** The comparison between models using different feature sets (reported Fe-related CREs, PLACE CREs, MAMA motifs, and MAMA+PLACE) is not statistically rigorous. The authors do not report whether the differences in accuracy between models are statistically significant. The improvement from 80.9% (MAMA only) to 83.0% (MAMA+PLACE) is modest, and it is unclear if this difference is meaningful or within the noise of the model.
- **Why it matters** The claim that the combined model is the "best" is a key conclusion of the manuscript. If the improvement is not statistically significant, the conclusion is not supported.
- **Resolution test** The authors should perform a statistical test (e.g., McNemar's test or a paired bootstrap) to compare the performance of the different models and report the p-values. They should also report the variability of the accuracy estimates across cross-validation folds.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section, "Analyses of cis-Regulatory Element Candidates"
- **Evidence pointer** Methods section
- **Issue** The description of the MAMA method is too brief for readers unfamiliar with the tool. The authors state that MAMA was "previously established" (Kakei et al., 2013) but do not provide a summary of how it works, what its inputs and outputs are, or what parameters were used in this study.
- **Required correction** Provide a brief description of the MAMA algorithm, including its key steps (e.g., how it defines motifs, how it scores motif enrichment), and specify the parameters used in this analysis (e.g., motif length range, number of motifs to extract, background model).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, "Network Analyses of Gene Expression Patterns"
- **Evidence pointer** Methods section
- **Issue** The description of the WGCNA analysis is incomplete. The authors do not specify the soft-thresholding power used, the minimum module size, or the criteria for merging modules. They also do not describe how the "four major expression clusters" were identified from the network analysis.
- **Required correction** Provide the specific WGCNA parameters used and describe the criteria for defining the four expression clusters. If the clusters were defined based on module eigengenes, specify the correlation threshold used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section, "Important CRE Candidates Located Upstream of Fe Excess-Responsive Genes"
- **Evidence pointer** Results section, Figures 4 and 5
- **Issue** The description of the motif distribution figures is unclear. The authors state that motifs are "distributed in the proximal region of the TSS" but do not clearly explain what the x-axis and y-axis of the figures represent, or how the "coverage ratio" is calculated.
- **Required correction** Provide a clear figure legend and a more detailed description in the text of how the distribution and coverage ratio are calculated and what they indicate.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the relationship between Fe excess, Fe deficiency, and Zn deficiency is somewhat repetitive and could be more focused. The authors mention that "Fe excess condition causes Zn deficiency" but do not fully explore the implications of this for the interpretation of their motif analysis.
- **Required correction** Streamline the discussion and more explicitly address how the overlap between Fe excess, Fe deficiency, and Zn deficiency responses affects the interpretation of the identified CREs.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section, "Hypothetical Modeling of the Fe Excess-Responsive Transcriptional Regulation"
- **Evidence pointer** Results section, Figure 7
- **Issue** The tree model shown in Figure 7A is described as having "an average accuracy of 68.4% in cross-validation," but the details of this cross-validation are not provided. It is also unclear how this model relates to the more accurate XGBoost model.
- **Required correction** Provide details of the cross-validation procedure for the party tree model and clarify the relationship between the two models (XGBoost and party) in the text.

## Risk / unsupported claims
- The claim that the identified CREs are "novel" is unsupported without a systematic comparison to existing databases.
- The claim that the identified elements could be used to "produce new rice varieties that are tolerant of Fe excess" is speculative and unsupported by any experimental evidence.
- The claim that the MAMA-based model "accurately classified" gene expression patterns is not fully supported due to incomplete description of the validation procedure and potential for overfitting.
- The biological significance of the identified CREs is unverified, as no experimental validation is provided.
- The statement that "the maximum accuracy was obtained using both PLACE and MAMA, at 83.0% which is the highest" is not supported by statistical testing.