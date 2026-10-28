## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to presented evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors apply transfer learning to predict quantitative chromatin accessibility responses to TWIST1 and SOX9 dosage in cranial neural crest cells, identify sequence features that distinguish buffered versus sensitive responses, validate predictions with reporter assays, and propose a biophysical model based on transcription factor-nucleosome competition to explain the sensitizing effect of low-affinity binding sites.
- **Visible evidence base** Main text figures 1-5 with legends, supplemental figure legends S1-S11, methods descriptions, and data availability statements
- **Missing materials affecting confidence** Raw data files, full supplemental tables, model architecture details, hyperparameter settings, and complete computational pipelines were not available for direct inspection

## Reviewer
- **Overall assessment** This manuscript presents a compelling and technically sophisticated application of transfer learning to a biologically important problem: understanding how cis-regulatory elements respond quantitatively to transcription factor dosage. The work is timely, methodologically innovative, and addresses a gap in the field by moving beyond steady-state predictions to perturbed contexts. The combination of precise dosage titration, deep learning, and experimental validation is a strength. However, several technical concerns regarding model interpretation, statistical rigor, and the generalizability of the biophysical model need to be addressed before the central claims are fully established.

- **Who would be interested in the results, and why** Researchers in gene regulation, computational biology, and developmental genetics would find this work of high interest. The transfer learning framework for predicting quantitative responses to TF dosage has broad applicability beyond the specific TWIST1/SOX9 system studied here. The finding that low-affinity binding sites confer sensitivity to TF dosage has implications for understanding how regulatory variants contribute to phenotypic variation and disease. The evolutionary conservation analyses linking buffering and sensitizing sequences to purifying selection will interest those studying the functional significance of non-coding variation.

- **Major strengths**
  1. The experimental system is well-designed, using the dTAG system to achieve precise, graded modulation of TF dosage with single-cell resolution.
  2. The transfer learning approach is methodologically sound and clearly outperforms baseline methods, demonstrating the value of pretraining on unperturbed data.
  3. The combination of model interpretation, motif discovery, and experimental validation provides a coherent and convincing narrative.
  4. The biophysical model offers a mechanistic explanation for the observed sensitizing effects of low-affinity sites.
  5. The evolutionary conservation analyses add an important dimension, suggesting functional relevance beyond the in vitro system.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of model interpretation
- **Claim pointer** The authors claim that contribution scores from fine-tuned models reveal sequence features that are "predictive" of buffered or sensitive responses, and that these features are biologically meaningful.
- **Evidence pointer** Figure 3, Methods section "Model interpretation and motif matching"
- **Concern** The interpretation pipeline relies on TF-MoDISCO and contribution scores, but the manuscript does not provide sufficient detail on how the significance of contribution scores was assessed. Specifically, it is unclear whether the authors performed any null hypothesis testing or permutation-based controls to determine whether the identified motifs contribute significantly more than expected by chance. The threshold for mapping motifs (Jaccard similarity percentile ≥10%, contribution percentile ≥0.5%) appears arbitrary and may lead to false positives. Additionally, the authors do not report how many motifs were identified in total, how many were tested, or how multiple testing was handled.
- **Why it matters** The central claim that specific sequence features predict dosage response depends entirely on the reliability of the motif discovery and attribution pipeline. If the contribution scores are noisy or the thresholds are too permissive, the identified motifs may not be truly predictive, undermining the subsequent experimental validation and the biophysical model.
- **Resolution test** The authors should provide a rigorous statistical framework for assessing the significance of contribution scores, including permutation tests or comparison against a null model. They should also report the total number of motifs identified, the false discovery rate, and demonstrate that the identified motifs are enriched for known TF binding sites or show consistent patterns across independent model initializations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of model evaluation
- **Claim pointer** The authors claim that fine-tuned models achieve "near-experimental accuracy" in predicting dosage response, and that transfer learning substantially outperforms baseline approaches.
- **Evidence pointer** Figure 2, Figure S3
- **Concern** The evaluation of model performance relies on correlations between predicted and observed values, but the manuscript does not clearly describe how the "lower bound of experimental reproducibility" was calculated. It is unclear whether this benchmark is appropriate, and whether the comparison between model performance and experimental reproducibility is statistically valid. Furthermore, the authors do not report confidence intervals for the performance metrics, nor do they show whether the improvement over baselines is statistically significant across multiple model initializations or data splits.
- **Why it matters** The claim of "near-experimental accuracy" is a strong one that, if true, would be a significant advance. However, without proper statistical evaluation, it is impossible to assess whether the observed performance is robust or whether it reflects overfitting to the specific test set. The comparison to experimental reproducibility is also critical, as it sets the ceiling for what is achievable.
- **Resolution test** The authors should provide a more detailed description of how the experimental reproducibility benchmark was computed, including the number of replicate comparisons and the statistical method used. They should also report performance metrics with confidence intervals, and perform statistical tests comparing the fine-tuned model to baselines across multiple independent train-test splits.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance and generalizability
- **Claim pointer** The authors claim that the sequence determinants identified for TWIST1 and SOX9 dosage response represent "additional layers of the cis-regulatory code" that are generalizable beyond the specific cell type and TFs studied.
- **Evidence pointer** Discussion section, Figure 4
- **Concern** The study is limited to two TFs in a single cell type. While the authors acknowledge this limitation, the broader claim of uncovering general principles of the cis-regulatory code requires evidence that the identified features (e.g., low-affinity sites conferring sensitivity) apply to other TFs and cellular contexts. The biophysical model is only tested on TWIST1 data, and its applicability to SOX9 is not demonstrated. The evolutionary conservation analyses are suggestive but do not directly test whether the identified features are functionally important in vivo.
- **Why it matters** The significance of the work for a broad audience depends on the generalizability of the findings. If the identified sequence determinants are specific to TWIST1 and SOX9 in CNCCs, the impact would be considerably narrower. The authors should temper their claims or provide additional evidence, such as analysis of publicly available datasets for other TFs, to support generalizability.
- **Resolution test** The authors should either (1) apply their transfer learning approach to additional TFs and cell types using publicly available data to demonstrate generalizability, or (2) substantially moderate the claims of generalizability in the discussion. They should also test whether the biophysical model can recapitulate SOX9 dosage response data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness of biophysical model
- **Claim pointer** The authors claim that transcription factor-nucleosome competition can explain the sensitizing effect of low-affinity binding sites, and that fitted model parameters support this mechanism.
- **Evidence pointer** Figure 6, Methods section "Modeling of chromatin accessibility"
- **Concern** The biophysical model is highly simplified and makes several assumptions that are not fully justified. The model assumes a fixed number of binding sites and does not account for cooperative interactions between TFs or the possibility of nucleosome repositioning. The fitting procedure is described only briefly, and it is unclear how robust the fitted parameters are, whether the model is identifiable, or whether alternative models could fit the data equally well. The authors do not report goodness-of-fit statistics or model comparison against simpler alternatives.
- **Why it matters** The biophysical model is presented as providing mechanistic insight into the observed phenomena. If the model is not well-constrained by the data or if alternative explanations are equally plausible, the mechanistic interpretation is weakened. This is particularly important because the model is used to make claims about the underlying biology.
- **Resolution test** The authors should provide a more thorough analysis of the model, including identifiability analysis, parameter uncertainty quantification, and comparison against alternative models (e.g., a model without nucleosome competition). They should also test the model's predictions against additional experimental data, such as nucleosome occupancy measurements at different TF dosages.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Methods section "Deep learning model pretraining and fine-tuning"
- **Evidence pointer** Methods section
- **Issue** The description of the fine-tuning procedure is incomplete. The authors state that the learning rate was set to 1e-3 and training was performed for 10 epochs, but do not specify the batch size, optimizer, loss function weights, or how the final model was selected. This level of detail is insufficient for reproducibility.
- **Required correction** Provide a complete description of the training procedure, including all hyperparameters, the optimizer, the loss function, and the model selection criteria. Consider making the code publicly available.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 2, Figure S3
- **Evidence pointer** Figure legends
- **Issue** The performance metrics in Figure 2 are presented as correlation coefficients, but the authors do not report confidence intervals or p-values for these correlations. Additionally, it is unclear whether the correlations are computed on the test set only, and how many test samples were used.
- **Required correction** Report confidence intervals and p-values for all correlation coefficients, and clearly state the number of test samples used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of evolutionary analyses
- **Affected element** Figure 4F, Figure S6
- **Evidence pointer** Figure 4F legend
- **Issue** The evolutionary conservation analysis compares buffering and sensitizing motif occurrences to shuffled controls. However, the shuffling procedure is not described in sufficient detail, and it is unclear whether the shuffled controls preserve the local sequence context (e.g., GC content, CpG density) that could affect conservation scores.
- **Required correction** Describe the shuffling procedure in detail, and ensure that the shuffled controls are matched for relevant sequence features.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity of experimental validation
- **Affected element** Figure 5, Methods section "Luciferase assays"
- **Evidence pointer** Figure 5C
- **Issue** The number of biological replicates for the reporter assays is stated as "at least 4" but the exact number for each construct is not provided. Additionally, the criteria for selecting the 19 enhancers for validation are not fully described.
- **Required correction** Provide the exact number of replicates for each construct, and describe the selection criteria for the enhancers used in the validation experiments.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1C
- **Evidence pointer** Figure 1C legend
- **Issue** The PCA plot in Figure 1C shows the effect of TWIST1 dosage on chromatin accessibility, but the axis labels are not clearly defined. It is unclear what "PC1" and "PC2" represent in terms of biological variance.
- **Required correction** Clarify the axis labels and describe the percentage of variance explained by each principal component.

## Risk / unsupported claims
- The claim that the identified sequence features represent "additional layers of the cis-regulatory code" that are generalizable beyond the studied system is not fully supported by the data, as only two TFs in one cell type were examined.
- The claim that transcription factor-nucleosome competition "can explain" the sensitizing effect of low-affinity sites is presented as a definitive mechanism, but the model is simplified and alternative explanations are not ruled out.
- The assertion that model predictions approach "experimental accuracy" is difficult to evaluate without more detailed statistical analysis and a clearer description of the experimental reproducibility benchmark.
- The evolutionary significance of the identified buffering and sensitizing sequences is inferred from conservation scores, but direct functional evidence linking these sequences to organismal fitness is not provided.