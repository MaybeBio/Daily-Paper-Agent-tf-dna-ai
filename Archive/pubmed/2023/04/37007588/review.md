## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, claims, and evidence presented in the manuscript
- **Shared manuscript claim summary** The authors present ChromTransfer, a transfer learning method that fine-tunes a pre-trained, cell-type agnostic model of chromatin accessibility on cell-type specific regulatory elements. They report improved prediction accuracy over baseline models trained from scratch, robustness to small training data, and identification of cell-type relevant transcription factor binding motifs through feature attribution analysis.
- **Visible evidence base** Main text, figures referenced (Figures 1–3), tables referenced (Table 1), supplementary figures and tables referenced
- **Missing materials affecting confidence** Supplementary figures and tables not provided; code repository and trained models not inspected; detailed hyperparameter search results not shown

## Reviewer
- **Overall assessment** The manuscript presents a well-motivated and clearly described transfer learning approach for modeling cell-type specific chromatin accessibility from DNA sequence. The core idea of pre-training on a large compendium of open chromatin regions and fine-tuning on cell-type specific data is sensible and timely. The reported performance improvements over baseline models are consistent and the robustness to small training data is a notable practical advantage. The feature attribution analyses are appropriate and the biological interpretations are plausible. However, several technical details and validations are missing or under-specified, and the generalizability of the approach beyond the six cell lines tested remains unclear. The manuscript would benefit from additional analyses to strengthen the claims of broad utility and to rule out alternative explanations for the observed performance gains.

- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and machine learning applied to genomics would be interested. The work addresses a practical bottleneck in applying deep learning to regulatory element modeling, namely the need for large training datasets. The demonstration that transfer learning can mitigate this limitation is relevant to anyone building predictive models for cell-type specific regulatory activity, and the feature attribution results provide insights into the sequence determinants of cell-type specificity.

- **Major strengths** 
  1. The problem is well-motivated and the transfer learning framework is clearly described and logically sound.
  2. The evaluation is thorough, including comparisons to two baseline approaches (binary and multi-class) and a bootstrap analysis of training data size.
  3. The feature attribution analysis is appropriate and the biological interpretations are supported by known cell-type specific transcription factor biology.
  4. The manuscript is clearly written and the figures are informative.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "ChromTransfer achieved high predictive performances for all cell lines (overall test set F1 scores ranging between 0.73 and 0.86, AUROC ranging between 0.79 and 0.89, and AUPRC ranging between 0.4 and 0.74; Figure 1F; Supplementary Figure S1B; Supplementary Tables S1-2)."
  - **Evidence pointer** Figure 1F, Supplementary Figure S1B, Supplementary Tables S1-2
  - **Concern** The reported AUPRC values (0.4–0.74) are notably lower than the AUROC values (0.79–0.89), and the range is wide. The manuscript does not discuss this discrepancy or its implications for model utility. Additionally, the positive class F1 scores for some cell lines (e.g., HCT116 and MCF7 in the baseline models) are very low, suggesting that the positive class (open chromatin) is particularly challenging to predict. The manuscript does not provide a detailed analysis of the types of errors made by the models or the characteristics of misclassified regions.
  - **Why it matters** The practical utility of a predictive model depends on its precision and recall, not just its ranking ability. The low AUPRC values suggest that the models may have limited precision in identifying cell-type specific open chromatin regions, which could limit their use in downstream applications such as variant prioritization. A more detailed error analysis would help readers understand the limitations of the approach.
  - **Resolution test** Provide a detailed analysis of precision-recall trade-offs, including confusion matrices or error profiles for representative cell lines. Discuss the characteristics of false positives and false negatives, and consider whether the low AUPRC values are due to inherent sequence similarity between cell-type specific and shared regulatory elements.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "We find that transfer learning minimizes overfitting, allowing fine-tuning of models with high predictive performances using only a small fraction of input data."
  - **Evidence pointer** Figure 2, Table 1
  - **Concern** The bootstrap analysis is performed only for HepG2. The manuscript claims that transfer learning "allows for accurate sequence-based modeling of chromatin accessibility using small input data sets" as a general property, but this is demonstrated for only one cell type. It is unclear whether the same robustness to small training data would hold for cell types with different regulatory complexity or with fewer available training examples.
  - **Why it matters** The claim of robustness to small training data is a key selling point of the method. If this property is cell-type dependent, the general utility of the approach would be reduced. A broader evaluation across multiple cell types would strengthen the claim.
  - **Resolution test** Repeat the bootstrap analysis for at least one additional cell type with different regulatory characteristics (e.g., a cell type with a more complex regulatory landscape). Report the results and discuss any cell-type-specific differences in the relationship between training data size and performance.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** "Through feature importance analysis, we identify how ChromTransfer uses sequence elements to predict chromatin accessibility differently across cell types and match these elements to key TF binding site sequences."
  - **Evidence pointer** Figure 3, Supplementary Figures S3-S5
  - **Concern** The feature attribution analysis identifies known cell-type specific transcription factors as important, which is a useful validation. However, the manuscript does not explore whether the models capture any novel or unexpected sequence determinants. The analysis is limited to known TF motifs from JASPAR, and the authors do not perform a de novo motif discovery analysis to identify potentially novel sequence features.
  - **Why it matters** The stated goal is to "decipher the regulatory code." If the models only recapitulate known TF motifs, the added value for understanding the regulatory code is limited. A de novo motif analysis could reveal novel sequence features that are predictive of cell-type specific accessibility, which would be a more significant contribution.
  - **Resolution test** Perform a de novo motif discovery analysis on the sequences most important for each cell-type specific model. Compare any discovered motifs to known TF motifs and discuss whether the models have identified any novel sequence determinants.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** "We demonstrate superior performances with ChromTransfer for learning cell-type specific chromatin accessibility from sequence compared to models not informed by a pre-trained model."
  - **Evidence pointer** Figure 1G-H, Supplementary Figure S1B-C, Supplementary Tables S1, S3
  - **Concern** The comparison to baseline models is limited to models trained from scratch with the same architecture. It is unclear how ChromTransfer compares to other established methods for predicting chromatin accessibility from sequence, such as Basenji, DeepSEA, or Enformer. The manuscript does not position the method within the broader landscape of existing tools.
  - **Why it matters** For the method to be adopted by the community, it needs to demonstrate advantages over existing state-of-the-art approaches. Without such a comparison, it is difficult to assess the practical value of ChromTransfer.
  - **Resolution test** Compare ChromTransfer to at least one or two established methods for predicting chromatin accessibility from sequence, using the same evaluation metrics and data splits. Discuss the relative performance and computational cost.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction
  - **Evidence pointer** Introduction, first paragraph
  - **Issue** The introduction assumes familiarity with the concept of DNase I hypersensitive sites and the ENCODE project. A brief explanation of these concepts would make the manuscript more accessible to readers outside the immediate field.
  - **Required correction** Add a sentence or two explaining what DNase I hypersensitive sites are and why they are used as a proxy for regulatory element activity.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, Neural network architecture
  - **Evidence pointer** Materials and Methods, "Neural network architecture, training and hyperparameter tuning of the pre-trained model"
  - **Issue** The description of the neural network architecture is detailed but the rationale for specific design choices (e.g., kernel sizes, number of layers) is not provided. It is unclear whether these choices were optimized or based on prior work.
  - **Required correction** Briefly state the rationale for the architecture choices, or cite prior work that used a similar architecture.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, Data used for modeling
  - **Evidence pointer** Materials and Methods, "Data used for modeling of regulatory sequences"
  - **Issue** The negative set is described as "tiling the genome in 600 bp non-overlapping windows" with removal of regions overlapping gaps, blacklist regions, or within 300 bp of rDHSs. It is not clear whether the negative set was matched for GC content or other sequence properties, which could introduce bias.
  - **Required correction** State whether the negative set was matched for any sequence properties, and if not, discuss the potential implications for model performance.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion
  - **Evidence pointer** Discussion, first paragraph
  - **Issue** The discussion of the regulatory code is somewhat generic and does not fully engage with the specific findings of the study. The authors could more explicitly discuss what their results add to the understanding of the regulatory code.
  - **Required correction** Expand the discussion to more specifically address how the findings from ChromTransfer contribute to the understanding of the regulatory code, and what the next steps should be.

- **Technical failings that need to be addressed before the case is established** 
  - R1-M1 (AUPRC discrepancy and error analysis)
  - R1-M2 (generalizability of small-data robustness)

- **Assessment against Nature-style criteria** 
  - **Originality** The application of transfer learning to cell-type specific chromatin accessibility prediction is not entirely novel, as transfer learning has been used in other genomic contexts. However, the specific framing of pre-training on a large compendium of open chromatin regions and fine-tuning on cell-type specific data is a reasonable and potentially useful contribution. The originality is moderate.
  - **Scientific importance** The problem of predicting cell-type specific regulatory activity from sequence is important for understanding gene regulation and disease. The demonstration that transfer learning can improve performance with limited data is practically relevant. However, the importance is somewhat limited by the lack of comparison to state-of-the-art methods and the restricted evaluation to six cell lines.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and regulatory genomics researchers. The methods and results are unlikely to attract a broad interdisciplinary readership beyond these fields.
  - **Technical soundness** The technical approach is generally sound, but there are gaps in the evaluation (e.g., limited error analysis, single-cell-type bootstrap analysis) that need to be addressed. The lack of comparison to existing methods is a notable weakness.
  - **Readability for nonspecialists** The manuscript is clearly written and the figures are helpful, but the introduction and methods assume a level of familiarity with genomics and deep learning that may be challenging for nonspecialists.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the results are encouraging, but the manuscript needs to address the concerns regarding the AUPRC discrepancy, the generalizability of the small-data robustness claim, and the lack of comparison to existing methods before the case is fully established.

## Risk / unsupported claims
- The claim that ChromTransfer "minimizes overfitting" is supported only for HepG2; the generalizability to other cell types is not demonstrated.
- The claim that ChromTransfer "reveals the underlying sequence elements of relevance for the regulatory elements" is supported by the feature attribution analysis, but the analysis is limited to known TF motifs and does not explore novel sequence determinants.
- The claim that ChromTransfer is a "promising tool for deciphering how DNA codes for regulatory activities" is not fully supported without a comparison to existing state-of-the-art methods.