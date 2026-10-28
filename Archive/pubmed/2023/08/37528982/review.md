## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, author contributions, conflict of interest, publisher's note, supplementary material description, acknowledgments)
- **Assessment boundary** Scientific and technical evaluation of the manuscript's claims, methods, results, and interpretation as presented. No external data or code were consulted.
- **Shared manuscript claim summary** The authors train random forest classifiers to predict whether rice genes are upregulated or nonresponsive under heat or drought stress, using genomic features including known TF binding sites, putative cis-regulatory elements (pCREs), and (di)nucleotide content of promoter and gene body regions. They evaluate the impact of gene selection, promoter length, and k-mer finding strategy on model performance, and use SHAP values to identify the most important regulatory motifs, revealing time point-specific and common features.
- **Visible evidence base** Full text of the manuscript including all main figures (Figures 1–6) and supplementary figures (Figures S1–S5) and tables (Table S1) as referenced in the text. No raw data, code, or supplementary files were provided for direct inspection.
- **Missing materials affecting confidence** The actual figures and supplementary materials are not available for direct examination. The manuscript text describes results but the visual data (plots, heatmaps, performance curves) cannot be independently verified. Code and data availability are not described in detail beyond a public RNA-seq dataset accession.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and timely question in plant stress biology: whether machine learning models trained on genomic sequence features can predict transcriptional responses to heat and drought in rice, and whether interpretability of these models can reveal biologically meaningful regulatory motifs. The authors conduct a systematic evaluation of several methodological choices (gene selection, promoter length, k-mer finding approach) and provide a detailed framework for building and interpreting such models. The work is technically sound in its overall design, but several concerns arise regarding the robustness of the conclusions, the generalizability of the findings, and the biological interpretation of the identified motifs. The manuscript is well-written and accessible, but the scientific impact is somewhat limited by the lack of experimental validation and the narrow scope of the analysis (single species, single stress conditions, no integration with other data types).
- **Who would be interested in the results, and why** Researchers in plant molecular biology, particularly those studying abiotic stress responses and gene regulation, would find this work useful as a methodological framework. Computational biologists working on regulatory genomics and machine learning applications in biology would also be interested in the comparative analysis of feature types and k-mer finding strategies. The findings on the importance of coding sequence (di)nucleotide content and the limited value of known TFBSs for drought prediction could inform future model design. However, the lack of experimental validation limits the direct utility for breeders or biotechnologists seeking to engineer stress-tolerant crops.
- **Major strengths**
  - Systematic evaluation of methodological choices (gene selection, promoter length, k-mer finding approach) that are often taken for granted in similar studies.
  - Use of a gene-family-guided train-test split to avoid overfitting due to gene relatedness, which is a rigorous approach.
  - Comparison of multiple feature types (TFBSs, pCREs, (di)nucleotide content) and their combinations, providing a comprehensive view of predictive power.
  - Use of SHAP values for model interpretability, which is more informative than simple feature importance rankings.
  - Identification of both time point-specific and common regulatory motifs, with some biological plausibility (e.g., HSF at early heat, REVEILLE at 24h drought).
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the use of enriched promoter oligomers, complementing known TF binding sites, allowed us to gain novel insights in DNA motifs contributing to the stress regulatory code" (Abstract) and that "pCREs outperform TFBSs in predicting gene expression" (Results, Figures 6 and S5).
- **Evidence pointer** Results section, Figures 6 and S5; location not provided
- **Concern** The comparison between pCREs and TFBSs as feature sets is confounded by the number of features in each set. The manuscript does not report the number of TFBS features versus pCRE features used in the models. If the TFBS set is much smaller (e.g., a few hundred) than the pCRE set (e.g., several thousand), the performance difference could be attributed to feature count rather than the biological information content. Additionally, the pCREs are derived from the same training data used for model training (albeit with test set exclusion), which could lead to overfitting and inflated performance estimates. The manuscript does not describe any cross-validation of the pCRE discovery step itself.
- **Why it matters** The central claim of the paper is that pCREs are more informative than known TFBSs for predicting stress-responsive genes. If this conclusion is an artifact of feature set size or data leakage, the biological interpretation of the results would be substantially weakened.
- **Resolution test** The authors should report the number of features in each set, perform a controlled comparison where the number of features is matched (e.g., by selecting the top N TFBSs and top N pCREs), and describe how pCRE discovery was validated to avoid overfitting. Alternatively, they could use a nested cross-validation scheme where pCRE discovery is performed within each training fold.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that "this study provides a solid foundation to build and interpret ML models accurately predicting transcriptional responses and enables novel insights in biological sequence features that are important for abiotic stress responses" (Abstract).
- **Evidence pointer** Discussion section; location not provided
- **Concern** The manuscript does not provide any experimental validation of the predicted regulatory motifs. The identified pCREs and TFBSs are presented as biologically meaningful, but no evidence is provided that these motifs actually function in stress-responsive gene regulation (e.g., via reporter assays, electrophoretic mobility shift assays, or mutant analysis). The authors also do not compare their findings with existing experimental data on stress-responsive cis-elements in rice, which would strengthen the biological relevance of their predictions.
- **Why it matters** The stated goal of the work is to "unravel the regulatory grammar" of stress responses. Without experimental validation or comparison to known functional elements, the biological insights remain speculative. The manuscript would have greater impact if the authors could demonstrate that at least some of the identified motifs are functional or are enriched in experimentally validated stress-responsive promoters.
- **Resolution test** The authors should either (a) provide experimental validation of a subset of the most important motifs, (b) compare their identified motifs with known stress-responsive cis-elements from the literature or databases, or (c) clearly state the limitations of their approach in generating testable hypotheses rather than confirmed regulatory elements.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the use of non-random undersampling to increase the contrast between upregulated and nonresponsive genes" (Methods) improves model performance.
- **Evidence pointer** Methods section, "Binning and undersampling" subsection; location not provided
- **Concern** The non-random undersampling strategy selects the most responsive and least responsive genes based on log2FC. This approach could introduce selection bias, as the model is trained on extreme examples and may not generalize to genes with intermediate responses. The manuscript does not report how the model performs on a test set that includes genes with moderate expression changes, nor does it compare the non-random undersampling approach to random undersampling or other class balancing techniques.
- **Why it matters** The choice of training data directly affects the model's applicability. If the model is only trained on extreme cases, its utility for predicting the response of the broader gene population is unclear. The authors' decision to use this approach is justified for interpretability, but the trade-off with generalizability should be explicitly addressed.
- **Resolution test** The authors should evaluate their model on a test set that includes genes with a range of expression changes (e.g., all genes, not just the most and least responsive) and report performance metrics for this broader set. They should also compare non-random undersampling to random undersampling to demonstrate the benefit of their approach.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the use of proximal or distal promoter regulatory elements for model training revealed, for both heat and drought, a comparable performance" (Results, Figure 3).
- **Evidence pointer** Results section, Figure 3; location not provided
- **Concern** The manuscript does not report the overlap or correlation between the features derived from the proximal and distal promoter regions. If the proximal and distal promoter sequences are highly similar (e.g., due to the distal promoter containing the proximal region), the comparison may be trivial. The authors should clarify whether the distal promoter includes the proximal region or is an independent upstream region.
- **Why it matters** The conclusion that the proximal promoter suffices for prediction is only meaningful if the two promoter definitions are truly distinct. If the distal promoter includes the proximal sequence, the comparison is confounded.
- **Resolution test** The authors should clearly define the genomic coordinates of the proximal and distal promoter regions and report the sequence overlap. They could also perform a feature importance analysis to show which regions contribute most to prediction.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The authors claim that "the use of SHAP values... enabled us to identify the most important regulatory motifs" (Methods, Feature importance estimation).
- **Evidence pointer** Methods section, "Feature importance estimation" subsection; location not provided
- **Concern** The manuscript does not provide a clear explanation of how SHAP values are calculated for the random forest model and how the "knee" of the absolute SHAP value distribution is determined. The KneeLocator method is mentioned but not described in sufficient detail for reproducibility. Additionally, the interpretation of SHAP values for binary features (presence/absence of a pCRE) versus continuous features ((di)nucleotide content) is not discussed.
- **Why it matters** The interpretability of the models is a key contribution of the paper. If the SHAP value calculation and thresholding are not clearly described, readers cannot fully understand or reproduce the analysis.
- **Resolution test** The authors should provide a more detailed description of the SHAP value calculation, including the exact parameters used for KneeLocator, and discuss how SHAP values should be interpreted for different feature types.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract uses technical terms such as "pCREs," "TFBSs," and "SHAP values" without defining them. While these are standard in the field, the abstract could be more accessible to a broader readership.
- **Required correction** Define abbreviations at first use in the abstract, or use more descriptive terms such as "putative regulatory elements" and "known transcription factor binding sites."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Transcriptome data collection and differential expression analysis"
- **Evidence pointer** Methods section; location not provided
- **Issue** The description of the differential expression analysis is brief. The authors state that "upregulated genes were defined based on a log2FC >= 1 at any time point" but do not specify how the FDR was controlled across multiple time points or whether the analysis was performed separately for each time point or in a combined model.
- **Required correction** Provide more detail on the statistical model used for differential expression analysis, including how multiple time points were handled and whether a time-series analysis was performed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Gene-family-guided train-test split"
- **Evidence pointer** Methods section; location not provided
- **Issue** The manuscript does not report the number of gene families in the training and test sets, nor does it describe how the gene family assignments were obtained (e.g., from OrthoFinder). This information is important for assessing the effectiveness of the split.
- **Required correction** Report the number of gene families and the number of genes in each set, and describe the OrthoFinder parameters used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section; location not provided
- **Issue** The discussion of the biological implications of the identified motifs is somewhat generic. The authors mention HSF, MYB, and other TF families but do not discuss how their findings could be used to generate testable hypotheses for future experiments.
- **Required correction** Add a paragraph explicitly stating how the identified motifs could be prioritized for experimental validation and how the model could be used to predict stress-responsive genes in other rice varieties or related species.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, Figures 5 and S4
- **Evidence pointer** Results section, Figures 5 and S4; location not provided
- **Issue** The description of the hierarchical clustering of motifs is brief. The authors do not explain how the similarity between motifs was computed or how the clustering was performed.
- **Required correction** Provide details on the similarity metric and clustering algorithm used, and consider adding a supplementary figure showing the full clustering dendrogram.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Confounded comparison between pCREs and TFBSs due to feature count and potential data leakage in pCRE discovery.
  - R1-M2: Lack of experimental validation or comparison with known functional elements to support biological claims.
  - R1-M3: Potential selection bias from non-random undersampling, with no evaluation on a broader test set.
  - R1-M4: Unclear definition of proximal versus distal promoter regions and their overlap.

- **Assessment against Nature-style criteria**
  - Originality: The manuscript applies existing machine learning methods to a new problem (rice stress response) and systematically evaluates methodological choices. While not conceptually novel, the comparative analysis of feature types and k-mer finding strategies provides some originality.
  - Scientific importance: The work is relevant to understanding stress-responsive gene regulation in a major crop, but the lack of experimental validation limits its immediate impact. The findings are incremental rather than transformative.
  - Interdisciplinary readership: The manuscript is primarily of interest to plant molecular biologists and computational biologists. The methods are not sufficiently novel to attract a broader machine learning audience, and the biological findings are not sufficiently validated to attract a broad plant science audience.
  - Technical soundness: The overall design is sound, but the concerns raised above (feature count confounding, potential data leakage, selection bias) need to be addressed to fully establish the technical validity of the conclusions.
  - Readability for nonspecialists: The manuscript is generally well-written and accessible, but some technical details (e.g., SHAP values, KneeLocator) could be explained more clearly for a broader audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a useful methodological framework and some interesting biological observations, but the current evidence does not fully support the central claims regarding the superiority of pCREs over TFBSs and the biological significance of the identified motifs. Addressing the major concerns, particularly the feature count confounding and the lack of experimental validation, would substantially strengthen the manuscript.

## Risk / unsupported claims
- The claim that pCREs outperform TFBSs for predicting stress-responsive genes is not fully supported due to potential confounding by feature count and data leakage in pCRE discovery.
- The claim that the identified motifs provide "novel insights" into the stress regulatory code is not supported by experimental validation or comparison with known functional elements.
- The claim that the non-random undersampling approach improves model performance is not supported by a comparison with random undersampling or evaluation on a broader test set.
- The claim that the proximal promoter suffices for prediction is not fully supported without a clear definition of the promoter regions and their overlap.
- The generalizability of the models to other rice varieties, stress conditions, or species is not assessed and should not be inferred from the current results.