## Review setup

- **Input scope** Abstract and author summary only. Full text, figures, tables, and supplementary materials were not provided.
- **Assessment boundary** Assessment is limited to the claims and evidence as presented in the abstract and author summary. No independent verification of model architecture, data processing, or statistical results was possible.
- **Shared manuscript claim summary** The authors claim that DeepHBV, an attention-based deep learning model, predicts HBV integration sites with improved performance when augmented with repeat peaks and TCGA Pan Cancer peaks, and that attention analysis reveals transcription factor binding site enrichment near integration sites, supporting mechanistic interpretation.
- **Visible evidence base** Abstract and author summary only. No methods, results sections, figures, tables, or code were supplied.
- **Missing materials affecting confidence** Full manuscript, model architecture details, hyperparameters, training and validation data splits, baseline comparisons, statistical significance tests, attention mechanism implementation, and reproducibility details are absent. These omissions prevent rigorous evaluation of the core claims.

## Reviewer

- **Overall assessment** The abstract presents a potentially useful application of deep learning to HBV integration site prediction, with a plausible performance improvement from feature augmentation. However, the provided material is insufficient to assess technical soundness, reproducibility, or the validity of the mechanistic claims. The attention-based interpretation is intriguing but lacks supporting evidence in the visible text. The work may interest computational biologists and HBV researchers, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Computational biologists developing predictive models for genomic integration events, virologists studying HBV pathogenesis, and cancer genomics researchers interested in integration-mediated oncogenesis. The model could offer a tool for prioritizing candidate integration sites, and the attention analysis might inform mechanistic hypotheses.
- **Major strengths** The problem is clinically and biologically relevant. The use of an attention-based deep learning approach is modern and potentially interpretable. The reported performance improvement from adding genomic features is a clear, testable claim. The focus on transcription factor binding site enrichment provides a plausible link to mechanism.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4  
  - R1-M5
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5. The absence of methodological detail and statistical validation means the core predictive and mechanistic claims are not verifiable.
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. Deep learning for integration site prediction is not entirely novel, but the attention-based interpretability angle adds some originality.  
  - Scientific importance: Potentially high for HBV and liver cancer research, but the significance depends on validation and generalizability, which are not shown.  
  - Interdisciplinary readership: The topic bridges virology, cancer genomics, and machine learning, but the abstract is too brief to engage nonspecialists effectively.  
  - Technical soundness: Not assessable from the abstract. Key details on data, model, and evaluation are missing.  
  - Readability for nonspecialists: The abstract is concise but uses technical terms without sufficient context, limiting accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The claims are plausible but unsupported by the visible material. A full manuscript with methods, results, and statistical analysis is required for a meaningful evaluation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The model achieves AUROC of 0.9430 and AUPR of 0.9310 with HBV integration sequences plus TCGA Pan Cancer peaks.  
- **Evidence pointer** Abstract, performance metrics section. Location not provided.  
- **Concern** The reported performance metrics are presented without any description of the model architecture, training procedure, hyperparameter tuning, or cross-validation strategy. There is no indication of how the training and test sets were partitioned, whether the same samples were used across feature sets, or how overfitting was controlled.  
- **Why it matters** Without these details, the reported AUROC and AUPR values cannot be interpreted as reliable estimates of model performance. The improvement from feature augmentation could be an artifact of data leakage, class imbalance, or inappropriate evaluation.  
- **Resolution test** Provide a full methods section describing the model, data splits, hyperparameter selection, and evaluation protocol. Report confidence intervals or standard deviations for performance metrics, and include a baseline comparison to non-deep learning methods.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** DeepHBV was trained and tested using HBV integration sites data from dsVIS database and validated on VISDB.  
- **Evidence pointer** Abstract, data sources. Location not provided.  
- **Concern** The abstract does not specify the number of integration sites, the genomic context (e.g., gene regions, intergenic regions), the criteria for defining positive and negative samples, or the preprocessing steps. The use of two databases is mentioned, but the overlap or independence of these datasets is unclear.  
- **Why it matters** Reproducibility is a core requirement for computational models. Without clear data descriptions and access to the code or data, other researchers cannot replicate or build upon the work.  
- **Resolution test** Provide detailed data processing steps, sample counts, positive and negative definitions, and a link to the code and processed data. Clarify whether the validation dataset is truly independent from the training data.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical validity  
- **Claim pointer** Adding repeat peaks and TCGA Pan Cancer peaks significantly improves model performance.  
- **Evidence pointer** Abstract, performance comparison. Location not provided.  
- **Concern** The term "significantly" is used without any statistical test. The differences in AUROC and AUPR between feature sets are reported as point estimates, but no confidence intervals, p-values, or permutation tests are provided.  
- **Why it matters** The claim of significant improvement is central to the paper's contribution. Without statistical evidence, the observed differences could be due to chance, especially if the test set is small or the model is unstable.  
- **Resolution test** Perform and report statistical significance testing, such as DeLong's test for AUROC differences or bootstrap confidence intervals for AUPR. Report the number of test samples and the variability of the metrics.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Interpretability and mechanistic claim  
- **Claim pointer** Transcription factor binding sites were significantly enriched near genomic positions attended to by the convolutional neural network, and specific TFs were highlighted in both datasets.  
- **Evidence pointer** Abstract, attention analysis section. Location not provided.  
- **Concern** The abstract claims enrichment of TF binding sites near attention-highlighted positions, but no details are given on how attention weights were extracted, how "near" was defined, what background model was used for enrichment, or how significance was assessed. The list of TFs is presented without any quantitative support.  
- **Why it matters** The mechanistic interpretation is a key selling point of the model. If the enrichment analysis is not rigorously defined, the claim of revealing HBV integration preference is unsupported.  
- **Resolution test** Describe the attention extraction method, the genomic window size, the background model (e.g., random genomic regions or matched controls), and the statistical test used. Provide enrichment scores and p-values for each TF, and show that the findings are robust across datasets.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Generalizability  
- **Claim pointer** DeepHBV is a robust model for prediction of HBV integration sites.  
- **Evidence pointer** Abstract, summary statement. Location not provided.  
- **Concern** The abstract reports performance on one training database and one validation database, but there is no evidence of external validation on independent cohorts, different HBV genotypes, or different tissue types. The term "robust" is not supported by the visible evidence.  
- **Why it matters** Generalizability is essential for clinical or biological utility. A model that works only on a specific dataset is of limited value.  
- **Resolution test** Validate the model on multiple independent datasets, including different HBV genotypes and host tissues. Report performance stratified by these factors and discuss any limitations.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, model description  
- **Evidence pointer** Abstract, first paragraph. Location not provided.  
- **Issue** The term "attention-based deep learning model" is used, but the specific type of attention mechanism (e.g., self-attention, additive attention) is not specified.  
- **Required correction** Specify the attention mechanism type and its role in the model architecture.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract, feature sets  
- **Evidence pointer** Abstract, performance section. Location not provided.  
- **Issue** The abstract mentions "repeat peaks" and "TCGA Pan Cancer peaks" but does not define what these features represent or how they were derived.  
- **Required correction** Provide brief definitions of these feature sets and their biological rationale.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reporting  
- **Affected element** Abstract, performance metrics  
- **Evidence pointer** Abstract, performance section. Location not provided.  
- **Issue** Only AUROC and AUPR are reported. Other relevant metrics such as sensitivity, specificity, or F1 score are not mentioned.  
- **Required correction** Report additional metrics, especially if the dataset is imbalanced, to give a fuller picture of model performance.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Accessibility  
- **Affected element** Author summary  
- **Evidence pointer** Author summary, last sentence. Location not provided.  
- **Issue** The author summary states the model is "robust and explainable" but does not explain what "explainable" means in this context or how a user would interpret the model's predictions.  
- **Required correction** Clarify the interpretability mechanism and provide an example of how attention weights can be used to understand predictions.

## Risk / unsupported claims

- The claim of "significant" performance improvement is unsupported without statistical tests.
- The claim of TF binding site enrichment near attention-highlighted positions is unsupported without details on the enrichment analysis.
- The claim that DeepHBV is "robust" is unsupported without external validation.
- The claim that the model is "explainable" is not substantiated with a clear description of the interpretability method.
- The generalizability of the model to other HBV datasets or clinical settings is not assessable from the provided material.