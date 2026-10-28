## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) as provided
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and evidence presented in the supplied text only
- **Shared manuscript claim summary** The authors propose ScPGE, a scalable deep learning framework that predicts gene expression from discrete candidate cis-regulatory elements (cCREs) by integrating DNA sequences, TF binding scores, and epigenomic signals into 3D tensors, using CNN and transformer modules. They report superior performance over state-of-the-art models, identify a distance-dependent regulatory pattern in true positives, and develop two methods incorporating chromatin loops to improve distal cCRE-gene interaction capture. They also report accurate TF motif discovery and cross-cell/cross-species prediction.
- **Visible evidence base** Main text figures referenced (Figures 1-6), Supplemental Figures S1-S12, Supplemental Tables S1-S7, equations 1-4, and methodological descriptions
- **Missing materials affecting confidence** Actual figure panels and data values are not provided in the supplied text. Supplemental figures and tables are referenced but their contents are not visible. Numerical performance metrics (e.g., PCC, MAE values, PRAUC scores) are described qualitatively but not reported as specific numbers in the text. Details on dataset splits, hyperparameter tuning, and statistical significance testing are not fully described.

## Reviewer

- **Overall assessment** The manuscript presents a computationally efficient and conceptually interesting framework for gene expression prediction from cCREs. The core idea of assembling discrete regulatory elements into tensor representations and applying CNN-transformer architectures is reasonable and potentially useful. The observation of a distance-dependent regulatory pattern in true positives is intriguing and could inform model design. However, the evidence as presented is largely qualitative, with key quantitative results referenced only in figures or supplements that are not visible in the supplied material. The comparative claims against state-of-the-art models, the generalizability claims, and the biological insights derived from attention mechanisms require stronger statistical support and clearer reporting to be fully evaluated. The manuscript is potentially of interest to computational biologists and researchers in gene regulation, but the current evidence base is insufficient to fully establish the stated claims.

- **Who would be interested in the results, and why** Computational biologists developing deep learning methods for regulatory genomics would be interested in the architectural innovations and the incorporation of chromatin loops. Researchers studying cis-regulatory logic and enhancer-promoter interactions would be interested in the distance-dependent regulatory pattern and the TF motif discovery. The lightweight design and scalability claims may appeal to laboratories with limited computational resources. The cross-cell and cross-species prediction results could be relevant to those working on comparative genomics and model organism research.

- **Major strengths** The framework addresses a real and important problem: linking cCREs to target gene expression in a scalable manner. The use of discrete cCREs rather than long contiguous genomic windows is a sensible design choice that reduces computational burden. The identification of a distance-dependent regulatory pattern from prediction analysis is a valuable empirical observation that could guide future model development. The two methods for incorporating chromatin loops (direct attention modification and KL divergence loss) are technically distinct and thoughtfully motivated. The scalability analysis across multiple dimensions (epigenomic tracks, cCRE number, model structure) is commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Compared with current state-of-the-art models, ScPGE exhibits superior performance in predicting gene expression" and "ScPGE shows improvements of 10% in PCC and 9.6% in MAE compared to Enformer and improvements of 4.2% in PCC and 2.7% in MAE compared to EPInformer"
- **Evidence pointer** Figure 2A,B; location not provided for specific data values
- **Concern** The performance comparison claims are stated with specific percentage improvements, but the actual data values, error bars, statistical significance tests, and the number of independent replicates are not reported in the text. The figure panels are referenced but not visible in the supplied material. Without these details, it is impossible to assess whether the reported improvements are statistically robust or within the range of biological and technical variability.
- **Why it matters** The central claim of the manuscript is that ScPGE outperforms existing methods. If this claim is not supported by rigorous statistical evidence, the primary contribution of the work is undermined. The specific numbers cited (e.g., 10% PCC improvement) need to be contextualized with confidence intervals and significance testing.
- **Resolution test** Provide the full performance comparison table with mean and standard deviation across multiple random seeds or cross-validation folds, along with appropriate statistical tests (e.g., paired t-test or Wilcoxon signed-rank test) for each comparison. Report the exact number of genes and cell types used in each evaluation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** "ScPGE demonstrates its flexible scalability from three aspects: (i) scalability of epigenomic tracks, (ii) scalability of cCREs, and (iii) scalability of model structure"
- **Evidence pointer** Figure 2C-F; location not provided
- **Concern** The scalability experiments are described only qualitatively. For example, "ScPGE using 13 epigenomic tracks performs better than ScPGE using four default tracks" and "we observe a decrease in ScPGE's performance as the number of cCREs increases." The actual performance values, the range of cCRE numbers tested, and the specific model configurations are not reported. The claim that the framework is "scalable" requires quantitative evidence showing how performance and computational cost scale with each of these factors.
- **Why it matters** Scalability is a stated key advantage of the framework. Without quantitative data on how performance and resource usage change with input size, the practical utility of the method for larger-scale applications cannot be evaluated.
- **Resolution test** Provide plots or tables showing performance (PCC, MAE) and computational cost (training time, memory usage) as a function of the number of epigenomic tracks, the number of cCREs (e.g., 20, 50, 100, 200), and model depth/width. Include error bars and describe the experimental setup.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** "By comprehensively analyzing ScPGE's predictions, we find a pattern in true positives (TPs) that the regulatory effect of cCREs on genes decreases with distance."
- **Evidence pointer** Figure 4A; Supplemental Figures S5-S7; location not provided
- **Concern** The distance-dependent regulatory pattern is a key empirical finding that motivates the chromatin loop incorporation methods. However, the analysis is described only in general terms. It is unclear how the pattern was quantified, what statistical test was used to establish its significance, whether the pattern was consistent across cell types, and how it compares to the distance decay expected by chance. The categorization of predictions into TP/FP/TN/FN is described in the methods, but the thresholds and their justification are not fully explained.
- **Why it matters** This pattern is used as the biological rationale for the exponential decay function in the KL divergence method. If the pattern is not robustly established, the motivation for the method is weakened.
- **Resolution test** Provide a quantitative description of the pattern, including the fitted decay function, the goodness of fit, and a statistical comparison against a null model (e.g., random expectation). Show the pattern for each cell type separately and report the variability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** "ScPGE accurately discovers some crucial TF motifs within prioritized cCREs and reveals the different regulatory types of these cCREs."
- **Evidence pointer** Figure 6A-G; location not provided
- **Concern** The TF motif discovery and regulatory type classification are presented as biological insights, but the validation is not described in sufficient detail. It is unclear how the discovered motifs were compared to known motifs beyond the TOMTOM match, whether the regulatory type classification was experimentally validated, and how the attention-based prioritization was benchmarked against other methods for enhancer classification.
- **Why it matters** The biological interpretability of the model is a claimed advantage. Without clear validation of the discovered motifs and regulatory types, the biological relevance of the model's outputs remains uncertain.
- **Resolution test** Provide a detailed description of the motif discovery validation, including the number of motifs discovered, the significance thresholds used, and a comparison to known cell type-specific motifs. For the regulatory type classification, provide experimental validation or a clear benchmark against existing enhancer classification methods.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reporting completeness
- **Affected element** Model training details
- **Evidence pointer** Methods, Model training section
- **Issue** The training procedure is described at a high level, but several important details are missing: the number of training epochs, early stopping criteria, learning rate schedule, weight decay, and the specific data augmentation strategies (if any). The "warm-up" strategy is described, but the number of random initializations and the selection criteria are not specified.
- **Required correction** Provide a complete description of the training hyperparameters, including the range of values explored and the final values used. Specify the number of random initializations in the warm-up phase and the validation metric used for model selection.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Cross-species prediction
- **Evidence pointer** Figure 4C; Supplemental Figure S8B; location not provided
- **Issue** The cross-species prediction results are described as having "comparable PCC" but "significantly higher MAE" compared to intraspecies prediction. The term "significantly" is used without reporting the statistical test or the p-value. It is also unclear whether the higher MAE is due to systematic bias (e.g., different dynamic ranges) or genuine prediction error.
- **Required correction** Report the statistical test used to compare MAE values and provide the p-value. Additionally, show a scatter plot of predicted vs. observed expression for the cross-species setting to assess whether the higher MAE is due to bias or variance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Chromatin loop incorporation
- **Evidence pointer** Methods, Incorporation of chromatin loops; Equations 3 and 4
- **Issue** The direct method (Equation 3) multiplies the attention logits by exp(M), where M is the interaction matrix. It is unclear how the scale of M (normalized counts) interacts with the scale of the attention logits. The indirect method (Equation 4) adds a KL divergence loss, but the relative weighting between the MSE and KL terms is only described as a hyperparameter alpha, with no information on how it was tuned.
- **Required correction** Clarify whether M is normalized before being used in Equation 3, and describe the range of alpha values explored and the final value used. Provide a sensitivity analysis of performance with respect to alpha.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity of definitions
- **Affected element** Prediction categorization
- **Evidence pointer** Methods, Categorization of predictions
- **Issue** The thresholds for defining TP, FP, TN, and FN are described as "prediction (P) is above 0.7 and the true (T) is below 0.2" for FP, etc. However, the normalization step (x - xmin)/(xmax - xmin) is applied to both predicted and true values, but it is unclear whether the min and max are computed per cell type, per gene, or globally. This affects the interpretation of the thresholds.
- **Required correction** Specify the exact procedure for computing xmin and xmax, and justify the choice of thresholds (0.7 and 0.2). Consider reporting the sensitivity of the results to these thresholds.

- **Technical failings that need to be addressed before the case is established** R1-M1 (performance claims lack statistical evidence), R1-M2 (scalability claims lack quantitative data), R1-M3 (distance-dependent pattern lacks rigorous quantification), R1-M4 (biological validation is insufficiently described)

- **Assessment against Nature-style criteria**
  - **Originality** The combination of tensor-based representation of discrete cCREs with CNN-transformer architecture is a reasonable incremental advance over existing methods like Enformer and CREaTor. The distance-dependent regulatory pattern observation is potentially novel, but its originality depends on whether similar patterns have been reported elsewhere, which cannot be assessed from the supplied material.
  - **Scientific importance** Gene expression prediction from regulatory elements is an important problem. The lightweight design and scalability could be practically valuable. However, the importance of the specific contributions (e.g., the chromatin loop incorporation methods) is not fully established without stronger validation.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and bioinformaticians. The biological insights (TF motifs, regulatory types) could attract experimental biologists, but the presentation is heavily method-oriented. The potential for broader readership is limited.
  - **Technical soundness** The architectural choices are reasonable, but the evaluation methodology has gaps. The lack of reported statistical significance, the incomplete description of hyperparameter tuning, and the qualitative nature of several key results prevent a full assessment of technical soundness.
  - **Readability for nonspecialists** The abstract and introduction are accessible, but the methods and results sections assume significant familiarity with deep learning architectures and genomics terminology. The manuscript would benefit from clearer explanations of the tensor construction and the attention mechanism for a broader audience.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant problem and presents a plausible framework, but the key claims of superior performance, scalability, and biological insight are not supported by sufficient quantitative evidence in the supplied text. The authors should provide the actual data values, statistical tests, and detailed experimental setups for the performance comparisons, scalability analyses, and pattern discovery. If these are provided and the claims hold, the manuscript could become a valuable contribution to the field.