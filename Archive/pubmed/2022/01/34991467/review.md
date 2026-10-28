## Review setup
- **Input scope** Full manuscript text, including abstract, background, methods, results, discussion, and conclusions. No supplementary materials or figures were provided beyond those referenced in the text.
- **Assessment boundary** Evaluation is limited to the scientific content, methodological soundness, and claims as presented in the supplied manuscript. No external data, code, or additional documentation were available for verification.
- **Shared manuscript claim summary** The authors present cTAP, a machine learning framework that integrates ChIP-seq data with multiple GEO expression datasets to predict target genes of IRF8 and NFATc1 during osteoclast differentiation. They claim that cTAP identifies consistent up/down-regulated targets across heterogeneous datasets, outperforms log2 fold change alone, and that predicted targets have known roles in bone remodeling.
- **Visible evidence base** Results tables (Tables 1, 2, 6, 7, 8, 9), figures (Figs. 1, 2, 3, 4, 5, 6, 7, 8), and methodological descriptions in the Methods section. Literature citations are provided for validation of predicted targets.
- **Missing materials affecting confidence** No code, hyperparameter settings, or detailed dataset preprocessing scripts were provided. The full list of 134 functional group genes and their curation criteria are not fully detailed. No statistical significance testing for target predictions is described. The manuscript lacks a clear description of how the error tolerance parameter T was optimized across models.

## Reviewer
- **Overall assessment** The manuscript presents a novel computational framework, cTAP, for predicting transcription factor targets by integrating ChIP-seq data with multiple gene expression datasets. The core idea of using functional groups and machine learning to identify consistent regulatory patterns is interesting and potentially useful. However, the manuscript has significant methodological gaps, including unclear validation procedures, lack of statistical rigor, and insufficient detail on data processing and model training. The claims of predictive validity are supported only by literature correlation, not by independent experimental or computational validation. The writing is sometimes unclear, and the results are presented without adequate context or comparison to existing methods. While the approach has merit, the current evidence does not fully establish its reliability or generalizability.
- **Who would be interested in the results, and why** Researchers in bone biology, particularly those studying osteoclast differentiation and transcriptional regulation, would be interested in the predicted target genes. Computational biologists developing methods for transcription factor target prediction or integrating heterogeneous omics data would also find the cTAP framework relevant. The approach could be of interest to those working on pathway analysis and gene regulatory network inference.
- **Major strengths** 1. The integration of ChIP-seq data with multiple expression datasets is a reasonable strategy to identify consistent targets. 2. The use of functional groups rather than individual genes is a thoughtful way to capture coordinated regulation. 3. The comparison of multiple machine learning models provides some insight into method robustness. 4. The literature validation of predicted targets, while limited, does provide some confidence in the approach.
- **Major Concerns** 
  - R1-M1: Lack of independent validation of predicted targets.
  - R1-M2: Insufficient detail on functional group curation and composition.
  - R1-M3: Unclear statistical framework for evaluating prediction accuracy.
  - R1-M4: Potential overfitting and lack of external dataset testing.
  - R1-M5: Inconsistent and incomplete reporting of results across models.
- **Minor Comments** 
  - R1-m1: Typographical and grammatical errors throughout the text.
  - R1-m2: Figure and table numbering inconsistencies.
  - R1-m3: The t-SNE plot (Fig. 6) is not adequately explained or interpreted.
  - R1-m4: The description of the TQN method is unclear and lacks mathematical detail.
  - R1-m5: The manuscript would benefit from a clearer statement of the novelty relative to BioTarget.
- **Technical failings that need to be addressed before the case is established** The lack of independent validation, unclear statistical testing, and insufficient methodological detail are critical. The authors must demonstrate that cTAP predictions are not artifacts of the training data and that the method generalizes to unseen datasets. The functional group curation process must be transparent and reproducible.
- **Assessment against Nature-style criteria** 
  - Originality: The concept of using functional groups and machine learning for TF target prediction is somewhat novel, but similar integrative approaches exist. The originality is moderate.
  - Scientific importance: The potential to identify novel targets of key osteoclast transcription factors is important for bone biology, but the current evidence does not yet demonstrate significant biological insights.
  - Interdisciplinary readership: The work bridges computational biology and bone biology, which could appeal to a broad audience, but the technical presentation may limit accessibility.
  - Technical soundness: The methodology has several weaknesses, including lack of validation, unclear statistical framework, and potential overfitting. Technical soundness is currently insufficient.
  - Readability for nonspecialists: The manuscript is difficult to follow for nonspecialists due to unclear writing, undefined terms, and a dense presentation of results.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revisions, including independent validation, clearer methodology, and more rigorous statistical analysis, before the claims can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors claim that cTAP identifies "consistent up/down-regulated targets" and that literature review "revealed that all predicted target genes have known roles in bone remodeling."
- **Evidence pointer** Results section, Tables 1 and 2, literature validation paragraphs.
- **Concern** The predicted targets are validated only by literature correlation, which is a weak form of validation. There is no independent experimental validation (e.g., qPCR, ChIP-qPCR, knockdown/overexpression) or computational validation on held-out datasets. The literature review is also selective and does not systematically assess whether the predicted targets are enriched for known osteoclast genes compared to a random set.
- **Why it matters** Without independent validation, the predictions could be false positives or artifacts of the training data. The claim of predictive validity is not supported by the evidence presented.
- **Resolution test** The authors should validate a subset of predicted targets experimentally or use an independent dataset (e.g., a GEO dataset not used in training) to test whether the predictions hold. They should also perform a statistical enrichment analysis (e.g., hypergeometric test) to show that predicted targets are significantly enriched for known osteoclast-related genes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors state that "we have included about ∼134 such curated genes in 14 functional groups" and that these are used for target discovery.
- **Evidence pointer** Methods section, "Modeling functional group" subsection, Table 5.
- **Concern** The process of curating the 134 genes into 14 functional groups is not described. The criteria for inclusion, the sources used, and how the groups were defined are not provided. This makes the approach non-reproducible and raises concerns about bias in gene selection.
- **Why it matters** The functional groups are central to the cTAP framework. If the curation is not transparent and reproducible, the entire method cannot be independently evaluated or applied by other researchers.
- **Resolution test** The authors should provide a detailed description of the curation process, including the sources (e.g., KEGG, GO, literature), inclusion/exclusion criteria, and how genes were assigned to groups. Ideally, the full list of genes per group should be provided as a supplementary table.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report AUC values above 0.85 for all models and compare model performance using accuracy, MCC, sensitivity, and specificity.
- **Evidence pointer** Results section, Fig. 7, Table 6.
- **Concern** The statistical framework for evaluating prediction accuracy is unclear. The authors do not describe how the training and test sets were split, whether cross-validation was used, or how confidence intervals for AUC were calculated. The comparison between models lacks statistical testing (e.g., DeLong test for AUC differences).
- **Why it matters** Without proper statistical evaluation, the reported performance metrics could be overoptimistic or not significantly different between models. The claim that machine learning models outperform log2 fold change alone is not statistically supported.
- **Resolution test** The authors should describe the exact train/test split procedure, use repeated cross-validation, and report confidence intervals and p-values for model comparisons. They should also test whether the AUC of the ML models is significantly higher than that of the log2 fold change baseline.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** The authors claim that cTAP can be applied to "11 publicly available GEO data sets related to osteoclastogenesis" and that it identifies consistent targets across datasets.
- **Evidence pointer** Methods section, "Generating comparison pairs" subsection, Table 4.
- **Concern** The manuscript does not demonstrate that the method generalizes beyond the specific datasets used. There is no external validation on datasets not included in the training cohort. The potential for overfitting to the specific datasets is not addressed.
- **Why it matters** If the method only works on the specific datasets used, its utility for other biological contexts is limited. The claim of generalizability is not supported.
- **Resolution test** The authors should test cTAP on an independent set of osteoclast differentiation datasets or on a different biological context to demonstrate generalizability. They should also discuss potential limitations and biases in the dataset selection.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reporting
- **Claim pointer** The authors state that "the machine learning models using GP and GA produced NFATc1 and IRF8 target genes different than simply using a log2 fold change alone."
- **Evidence pointer** Results section, Tables 1, 2, 7, 8, 9.
- **Concern** The results are presented in a fragmented manner, with multiple tables and figures that are not fully integrated. The differences between models are described qualitatively, but the actual lists of predicted targets are not compared systematically. The error tolerance parameter T is mentioned but its effect on results is not explored.
- **Why it matters** The reader cannot fully assess the consistency and reliability of the predictions across models. The lack of a clear comparison undermines the claim that the ML approach adds value over simpler methods.
- **Resolution test** The authors should provide a unified comparison of predicted targets across all models and the log2 fold change baseline, including overlap statistics (e.g., Jaccard index). They should also perform a sensitivity analysis of the T parameter.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Entire manuscript
- **Evidence pointer** Throughout
- **Issue** The manuscript contains numerous typographical and grammatical errors, such as "forrth" instead of "fourth" and "ostecoclast" instead of "osteoclast." These errors detract from readability.
- **Required correction** The manuscript should be carefully proofread and edited for language and typographical errors.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures and tables
- **Evidence pointer** Figs. 1, 6, 7, 8; Tables 1, 2, 4, 5, 6, 7, 8, 9
- **Issue** Figure and table numbering is inconsistent. For example, Table 3 is referenced in the text but appears to be a different table than the one described. Figure 6 is mentioned but not fully explained.
- **Required correction** The authors should ensure all figures and tables are correctly numbered and referenced in the text, and each should have a clear caption and description.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Fig. 6
- **Evidence pointer** Results section, "Generating functional groups" subsection
- **Issue** The t-SNE plot is presented but not adequately interpreted. The authors do not explain what the plot shows or how it supports the method.
- **Required correction** The authors should provide a clear interpretation of the t-SNE plot and explain its relevance to the method.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodology
- **Affected element** TQN method
- **Evidence pointer** Methods section, "Training and prediction" subsection
- **Issue** The trimmed quantile normalization (TQN) method is described in text but lacks mathematical detail. The equation provided (Eq. 3) is not fully explained, and the choice of the trimming parameter P is not justified.
- **Required correction** The authors should provide a more detailed description of TQN, including the exact algorithm, the choice of P, and its effect on the results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Background section, Discussion
- **Issue** The novelty of cTAP relative to the authors' previous work, BioTarget, is not clearly stated. The differences in methodology and scope are not explicitly discussed.
- **Required correction** The authors should clearly articulate what is new in cTAP compared to BioTarget and why this represents a significant advance.

## Risk / unsupported claims
- The claim that "all predicted target genes have known roles in bone remodeling" is not supported by a systematic literature review or statistical enrichment analysis.
- The claim that machine learning models outperform log2 fold change alone is not statistically tested.
- The claim that cTAP can be applied to "11 publicly available GEO data sets" without addressing potential batch effects or platform differences is not fully supported.
- The claim that predicted targets "could be direct targets" of IRF8 and NFATc1 is speculative and not supported by experimental evidence.
- The generalizability of the method to other biological contexts is not demonstrated.