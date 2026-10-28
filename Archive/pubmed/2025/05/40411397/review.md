## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, experimental section) as provided
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and presentation quality as inferable from the supplied text. No supplementary figures, tables, or code were available for inspection.
- **Shared manuscript claim summary** The authors present deepTFBS, a deep learning framework combining multi-task learning (deepTFBS-MT) and transfer learning (deepTFBS-TL) to predict transcription factor binding sites (TFBSs) within and across plant species. They report superior performance over PWM, DeepSEA, DanQ, and adapted BPNet on Arabidopsis data, cross-species transfer to wheat, interpretability via Integrated Gradients, and experimental validation of WUS target predictions using yeast one-hybrid assays.
- **Visible evidence base** Main text figures referenced (Figures 1–6), tables referenced (Tables S1–S10 in supplementary), and methodological descriptions in the Experimental Section. No actual figure images, numerical results tables, or code outputs were provided in the supplied material.
- **Missing materials affecting confidence** Supplementary tables (S1–S10), all figure panels, detailed hyperparameter settings, dataset accession details, code repository contents, and the full results of yeast one-hybrid experiments. Without these, quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in plant genomics: improving TFBS prediction accuracy within and across species using deep learning. The proposed framework is reasonable in design, combining multi-task pretraining with transfer learning, and the authors include useful comparisons against established methods. However, the provided text alone does not allow verification of the central quantitative claims, and several methodological details are either missing or ambiguous. The cross-species results, while promising, are presented with limited statistical rigor, and the experimental validation section is underdescribed. The work has potential, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those focused on plant species with limited TF binding data. Researchers developing deep learning methods for genomics would also find the multi-task and transfer learning comparisons relevant. Plant molecular biologists studying transcriptional regulation in crops such as wheat may benefit from the practical prediction tool and web server.
- **Major strengths**  
  1. The problem is well-motivated: cross-species TFBS prediction is practically important and underexplored in plants.  
  2. The framework design is sensible, combining multi-task learning with transfer learning in a way that directly addresses small-sample and cross-species scenarios.  
  3. The authors include comparisons against multiple baselines (PWM, DeepSEA, DanQ, BPNet) and report both within-species and cross-species performance.  
  4. The interpretability analysis using Integrated Gradients adds value by connecting model predictions to known motif information.  
  5. The inclusion of experimental validation (yeast one-hybrid) for a subset of predictions strengthens the practical relevance.  
  6. The provision of open-source code, a Docker image, and a web server enhances usability and reproducibility.
- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "deepTFBS outperformed previously described prediction strategies, including position weight matrix, deepSEA and DanQ, with a 244.49%, 49.15%, and 23.32% improvement of the area under the precision-recall curve (PRAUC), respectively."  
- **Evidence pointer** Abstract; Figures 2C–J; Tables S2, S4, S5 (location not provided)  
- **Concern** The headline performance improvements are stated as percentages, but the absolute PRAUC values, the number of TFs considered, the statistical significance of the differences, and the variance across TFs are not reported in the provided text. The comparison methodology for DeepSEA and DanQ is described only briefly, and it is unclear whether the same train/test splits and hyperparameter tuning procedures were used for all methods.  
- **Why it matters** Without absolute metrics, error bars, and significance testing, the claimed improvements cannot be evaluated. Percentage improvements can be misleading when baseline values are low. A fair comparison requires identical data splits, evaluation protocols, and reporting of per-TF distributions.  
- **Resolution test** Provide a table with median and interquartile ranges of PRAUC and AUROC for each method, the number of TFs with statistically significant improvement (e.g., paired Wilcoxon test), and a clear description of the evaluation protocol ensuring identical train/test splits across methods.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity  
- **Claim pointer** "deepTFBS-TL improved performance in 347 out of 359 TFs, achieving an average PRAUC improvement of 50.5% compared to deepTFBS-MT."  
- **Evidence pointer** Results section "deepTFBS-TL Shows Enhanced TFBS Prediction Through Transfer Learning Both within and Across Plant Species"; Figure 5A; Table S4 (location not provided)  
- **Concern** The transfer learning procedure is described at a high level, but critical details are missing: how many fine-tuning epochs, what learning rate, whether early stopping was used, how the balanced datasets were constructed (e.g., negative sampling strategy, seed), and how the ensemble of 10 models was aggregated for final predictions. The comparison between deepTFBS-TL and deepTFBS-MT is also confounded by the fact that deepTFBS-TL uses balanced training data while deepTFBS-MT uses imbalanced data, making it unclear whether improvements are due to transfer learning or to the balanced sampling.  
- **Why it matters** Reproducibility is a core requirement for computational methods. The confounding between transfer learning and data balancing undermines the specific claim that transfer learning is the cause of improvement.  
- **Resolution test** Provide full hyperparameter settings, a description of the negative sampling procedure, and an additional control experiment where deepTFBS-MT is retrained on balanced data without transfer learning, to isolate the effect of transfer learning.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "Further cross-species prediction of TFBS in wheat showed that deepTFBS yielded a significant PRAUC improvement of 30.6% over these three baseline models."  
- **Evidence pointer** Abstract; Results section "deepTFBS-TL Shows Enhanced TFBS Prediction Through Transfer Learning Both within and Across Plant Species"; Figure 5C; Table S5 (location not provided)  
- **Concern** The cross-species evaluation is described only in aggregate. It is unclear how many wheat TFs were tested, how the wheat test set was constructed, whether the same 110 wheat TFs were used for all methods, and what the baseline PRAUC values were. The claim of "significant" improvement is not supported by any statistical test reported in the text.  
- **Why it matters** Cross-species prediction is a central contribution of the paper. Without detailed evaluation metrics and statistical support, the claim of cross-species utility is not established.  
- **Resolution test** Report per-TF PRAUC and AUROC for all methods on the wheat test set, the number of TFs with significant improvement, and the statistical test used. Clarify the construction of the wheat test set and whether orthology information was used in evaluation.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "we experimentally confirmed several predicted binding events in wheat, using yeast one-hybrid assays"  
- **Evidence pointer** Results section "Application of deeptfbs to Study the WUS Regulatory Network in Arabidopsis, Maize, and Wheat"; Figure 6C; Table S7 (location not provided)  
- **Concern** The experimental validation is mentioned but not described in sufficient detail. The number of tested candidates, the selection criteria for choosing these candidates, the definition of a "positive" result, and the overall success rate are not reported in the provided text. The comparison to "predicted solely based on PWM" (mentioned in the text) is not quantified.  
- **Why it matters** Experimental validation is a strong point of the paper, but without clear reporting of the experimental design and results, the reliability of the validation cannot be assessed.  
- **Resolution test** Provide a detailed description of the yeast one-hybrid assay, including the number of candidates tested, the criteria for positive binding, the success rate, and a comparison table of predictions from deepTFBS-TL versus PWM-based methods.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Technical soundness  
- **Claim pointer** "deepTFBS-MT has Interpretation Ability by Identifying TF Binding Preferences"  
- **Evidence pointer** Results section "deepTFBS-MT has Interpretation Ability by Identifying TF Binding Preferences"; Figure 4A (location not provided)  
- **Concern** The interpretability analysis using Integrated Gradients is presented for only ten TFs, and the comparison to known motifs from the Plant Cistrome Database is qualitative. The text states that seven of ten motifs matched, but the criteria for "matching" are not defined. No quantitative motif similarity scores are provided.  
- **Why it matters** Interpretability is a secondary but valuable contribution. Without quantitative criteria, the claim that the model learns known binding preferences is weak.  
- **Resolution test** Provide a quantitative motif comparison metric (e.g., Tomtom similarity score) for all 359 TFs, and report the distribution of similarity scores. Define the threshold for a "match."

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract  
- **Issue** The abstract states "a 244.49%, 49.15%, and 23.32% improvement" without specifying the baseline PRAUC values. This makes the improvements difficult to interpret.  
- **Required correction** Include baseline PRAUC values in parentheses, e.g., "from 0.18 to 0.63 (244.49% improvement)."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Experimental Section, "The deepTFBS Architecture and Training"  
- **Evidence pointer** Experimental Section  
- **Issue** The number of convolutional filters, kernel sizes, LSTM hidden units, and attention head dimensions are not specified.  
- **Required correction** Provide a complete architecture table with layer types, output dimensions, and parameter counts.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical rigor  
- **Affected element** Results, "deepTFBS-MT Shows Superior Performance"  
- **Evidence pointer** Figure 2 (location not provided)  
- **Issue** The text reports median values but does not report confidence intervals or the results of statistical tests comparing methods.  
- **Required correction** Add confidence intervals (e.g., bootstrap) and paired statistical tests (e.g., Wilcoxon signed-rank) for all comparisons.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Results, "Application of deeptfbs to Study the WUS Regulatory Network"  
- **Evidence pointer** Figure 6D (location not provided)  
- **Issue** The text states "760 targets in the Arabidopsis genome conserved across all three species" but does not clarify how conservation was defined (e.g., orthology, sequence similarity, binding site overlap).  
- **Required correction** Define the criteria for "conserved targets" and describe the comparative analysis method.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Data Availability Statement  
- **Evidence pointer** Data Availability Statement  
- **Issue** The statement says data are available in supplementary material, but no accession numbers for raw sequencing data (beyond the custom WUS DAP-Seq) or processed data are provided.  
- **Required correction** Provide accession numbers for all public datasets used and a persistent link to the processed data.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (missing absolute metrics and statistical tests), R1-M2 (confounded transfer learning comparison), R1-M3 (insufficient cross-species evaluation detail), R1-M4 (underdescribed experimental validation). These four concerns are blocking because the central claims of the paper depend on them.

- **Assessment against Nature-style criteria**  
  **Originality:** Moderate. The combination of multi-task learning and transfer learning for plant TFBS prediction is not entirely novel, as similar ideas exist in human genomics, but the application to cross-species plant prediction is a useful extension.  
  **Scientific importance:** Moderate to high. Improved cross-species TFBS prediction would be valuable for crop genomics, but the demonstrated impact is limited by the incomplete evaluation.  
  **Interdisciplinary readership:** Moderate. The work bridges computational biology and plant molecular biology, but the presentation is heavily method-oriented and may not fully engage experimental plant biologists.  
  **Technical soundness:** Currently not fully assessable. The architecture is reasonable, but missing details on training, evaluation, and statistical rigor prevent verification.  
  **Readability for nonspecialists:** Adequate but improvable. The introduction and discussion are accessible, but the results section assumes familiarity with deep learning terminology and evaluation metrics.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the practical resources (code, web server) are valuable, but the quantitative claims must be substantiated with complete reporting and statistical analysis before the case is established.