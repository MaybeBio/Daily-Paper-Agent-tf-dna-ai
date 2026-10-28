## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure/table references
- **Assessment boundary** Scientific content, methodological rigor, reproducibility, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors compiled ZGA gene sets from five mammalian species, identified 111 conserved homologous genes, developed an interpretable machine learning model based on k-mer features that predicts ZGA genes with AUC > 0.81, and built the ZGAExplorer web platform for ZGA gene screening
- **Visible evidence base** Main text figures (Figures 1-7), supplementary figures (S1-S4), supplementary tables (S1-S2), methods section, and data availability statement
- **Missing materials affecting confidence** Raw RNA-seq and ChIP-seq data files, detailed model hyperparameters, feature selection results, complete motif analysis outputs, and validation metrics for individual species models were not fully provided

## Reviewer

### Overall assessment
The manuscript addresses an important question in developmental biology, namely the sequence determinants of zygotic genome activation genes across mammals. The authors have assembled a substantial dataset and applied machine learning approaches to identify conserved sequence features. The development of the ZGAExplorer platform is a useful community resource. However, several technical aspects require clarification and strengthening before the conclusions can be fully supported. The claim of conserved sequence determinants across five species rests on a relatively small set of 111 homologous genes, and the machine learning model interpretation, while promising, needs more rigorous validation and comparison with existing tools.

### Who would be interested in the results, and why
Developmental biologists studying early embryogenesis and zygotic genome activation would be the primary audience. Researchers working on transcriptional regulation, particularly those interested in transcription factor binding motifs and cis-regulatory elements, would also find the results relevant. Additionally, computational biologists developing machine learning approaches for genomic sequence analysis may be interested in the methodological framework. The ZGAExplorer platform could serve as a useful resource for the broader mammalian embryology community.

### Major strengths
1. The compilation of ZGA gene sets from five mammalian species using consistent criteria is a valuable contribution.
2. The application of interpretable machine learning (SHAP analysis) to identify sequence features is methodologically sound and provides biological insight.
3. The identification of conserved 6-mer features across species, including CTGCAG, is an interesting finding with potential functional relevance.
4. The ZGAExplorer web platform is a practical resource that will facilitate future research.
5. The integration of both sequence and epigenetic features in the predictive model is a thoughtful approach.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the RF-6mer model shows "excellent performance in predicting ZGA genes (AUC > 0.81)" across all five species.
- **Evidence pointer** Figure 5b, Section "Interpretable Machine Learning Models Based on Sequence-Dependent Determinants"
- **Concern** The manuscript reports AUC values for each species model but does not provide detailed performance metrics such as sensitivity, specificity, precision, and F1 score for each species individually. The evaluation appears to rely primarily on AUC, which can be misleading, especially with imbalanced datasets. The authors state that non-ZGA genes were randomly sampled to balance the dataset, but the total number of positive and negative samples, the number of features after selection, and the variance across cross-validation folds are not reported. Without these details, it is difficult to assess the robustness and generalizability of the models.
- **Why it matters** AUC alone does not fully characterize model performance, particularly for practical screening applications where precision and recall are critical. The lack of detailed metrics and dataset characteristics undermines the reproducibility and reliability of the claimed predictive performance.
- **Resolution test** Provide per-species performance metrics (sensitivity, specificity, precision, F1, and AUC with confidence intervals), report the number of positive and negative samples, the number of features retained after selection, and the cross-validation strategy in detail. Additionally, include a confusion matrix or precision-recall curve for at least one representative species.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that "111 homologous genes" were identified as conserved ZGA genes across all five species, and that these genes exhibit "a conserved genetic coding region" suggesting "potential sequence preferences for ZGA genes."
- **Evidence pointer** Section "Sequence Conservation of Cross-Species Homologous ZGA Genes", Figures 2 and 3
- **Concern** The identification of only 111 conserved genes out of thousands of ZGA genes per species is a small fraction. The authors do not provide a statistical framework to determine whether this overlap is greater than expected by chance. Furthermore, the claim of a "conserved genetic coding region" is based on alignment of 18 genes, which is a very small subset. The functional significance of the conserved region between Positions 360-400 is inferred from a single example (YTHDF2) and is not systematically validated across the other conserved genes.
- **Why it matters** The central claim of the manuscript is that there are conserved sequence determinants of ZGA genes across mammals. If the 111-gene overlap is not statistically significant, or if the conserved region is not functionally relevant, the main conclusion is weakened. The small sample size for the detailed sequence analysis limits the generalizability of the findings.
- **Resolution test** Perform a permutation test or hypergeometric test to assess whether the observed overlap of 111 genes is significantly greater than expected by chance. Expand the conserved region analysis to all 111 genes and provide functional evidence (e.g., enrichment of known TF binding motifs, conservation scores) that the identified region is biologically meaningful.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "gene sequence features and epigenetic modification features play equally important roles in regulating ZGA genes."
- **Evidence pointer** Section "Explainable Model Insights Into Epigenetic Modification Patterns", Figure 6
- **Concern** The comparison between sequence-based and epigenetic-based models is not clearly described. The authors state that the epigenetic model uses ChIP-seq data from mouse two-cell embryos, but it is unclear whether the same set of ZGA genes was used for both models, how the features were integrated, and whether the models were compared on the same test sets. The claim of "equally important" requires a formal statistical comparison of model performance, which is not provided. Additionally, the epigenetic data are only available for mice, so the cross-species comparison is limited.
- **Why it matters** The conclusion that both sequence and epigenetic features are equally important is a key finding of the manuscript. Without a rigorous comparison, this claim is not substantiated. The lack of cross-species epigenetic data also limits the generalizability of this conclusion.
- **Resolution test** Provide a clear description of the model comparison methodology, including the same training and test sets, and perform a statistical test (e.g., DeLong test for AUC comparison) to support the claim of equal importance. If cross-species epigenetic data are unavailable, temper the claim accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The authors state that "ZGAExplorer is the most comprehensive ZGA gene information platform to date, integrating approximately 170,000 genes spanning 40 gene types from 17 datasets, encompassing five mammalian species."
- **Evidence pointer** Section "ZGAExplorer Webserver", Figure 7
- **Concern** The description of the ZGAExplorer platform is brief and lacks technical details. It is unclear how the platform handles data updates, whether it supports programmatic access (e.g., API), and what specific query and visualization capabilities are offered. The claim of being "the most comprehensive" is not benchmarked against existing resources such as the Mouse Genome Informatics (MGI) database or other ZGA-specific databases.
- **Why it matters** The ZGAExplorer platform is presented as a major deliverable of the manuscript. For it to be a useful resource, the community needs to understand its functionality, limitations, and how it compares to existing tools. Overstating its comprehensiveness without benchmarking undermines its credibility.
- **Resolution test** Provide a more detailed description of the platform's architecture, features, and usage. Include a comparison table with existing ZGA-related databases and resources. If possible, provide a link to a live demo or tutorial.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract uses technical terms such as "k-mer core features" and "interpretable machine learning model" without sufficient context for a general biological audience. The significance of the AUC value is not explained.
- **Required correction** Briefly explain what k-mer features are and why an AUC > 0.81 is considered good performance. Consider adding a sentence on the potential practical applications of the findings.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Machine Learning Model Building"
- **Evidence pointer** Methods section
- **Issue** The methods state that "grid search and tenfold cross-validation methods were used to search for the best hyperparameters," but the specific hyperparameter ranges and the final selected parameters for each model are not reported.
- **Required correction** Provide the hyperparameter search space and the final optimal parameters for each species model to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Motif Analysis"
- **Evidence pointer** Methods section
- **Issue** The description of the motif analysis is incomplete. It is unclear how the k-mer features were converted into motifs, what background model was used, and how statistical significance was assessed.
- **Required correction** Provide a more detailed description of the motif discovery pipeline, including the software parameters and the statistical significance thresholds used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions "artificial ZGA regulatory elements" as a potential application, but this is not elaborated upon. The link between the identified sequence features and the design of such elements is not clearly articulated.
- **Required correction** Expand on how the identified conserved features could be used to design artificial regulatory elements, and discuss potential challenges and limitations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Data Availability Statement
- **Evidence pointer** Data Availability Statement
- **Issue** The data availability statement only states that data are available upon request, which is not in line with modern open science practices. The code used for the analysis is not mentioned.
- **Required correction** Provide a clear statement on data and code availability, including accession numbers for all datasets used and a link to a public code repository (e.g., GitHub).

### Technical failings that need to be addressed before the case is established
1. Lack of detailed per-species model performance metrics and dataset characteristics (R1-M1).
2. Insufficient statistical validation of the conserved gene set overlap (R1-M2).
3. Incomplete description of the comparison between sequence and epigenetic models (R1-M3).
4. Inadequate technical details on the ZGAExplorer platform and its benchmarking (R1-M4).

### Assessment against Nature-style criteria
- **Originality** The manuscript presents a novel integration of multi-species ZGA gene sets with interpretable machine learning. The use of SHAP analysis to identify conserved sequence features is a creative approach. However, the core idea of using k-mer features for regulatory element prediction is not entirely new, and the originality lies mainly in the application to ZGA genes across species.
- **Scientific importance** The question of what determines ZGA genes is of fundamental importance in developmental biology. The identification of conserved sequence features and potential TF binding motifs could have implications for understanding early embryonic development and developmental arrest. However, the small number of conserved genes and the lack of functional validation limit the immediate impact.
- **Interdisciplinary readership** The manuscript bridges developmental biology and computational biology, which could appeal to a broad readership. However, the technical details of the machine learning approach may be challenging for nonspecialists, and the biological significance of the findings needs to be more clearly articulated.
- **Technical soundness** The machine learning methodology is generally sound, but the lack of detailed performance metrics and the incomplete description of the model comparison undermine the technical rigor. The statistical validation of the conserved gene set is also insufficient.
- **Readability for nonspecialists** The manuscript is generally well-written, but the abstract and some sections of the results are dense with technical jargon. The figures are informative, but the main message could be more clearly highlighted.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses an important question and presents a potentially useful resource. However, the current evidence does not fully support the main claims regarding conserved sequence determinants and the equal importance of sequence and epigenetic features. The authors need to provide more rigorous statistical validation, detailed performance metrics, and a clearer description of the methods to strengthen the case.