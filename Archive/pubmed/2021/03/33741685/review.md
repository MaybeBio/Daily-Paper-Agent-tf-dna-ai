## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Technical and scientific evaluation of the presented method, its validation, and claims; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors present Leopard, a deep learning method based on a one-dimensional U-Net architecture, that predicts cell type–specific transcription factor binding at single-nucleotide resolution using DNA sequence and DNase-seq signals. They report high predictive accuracy (average AUROC 0.982, AUPRC 0.208), substantial improvement over state-of-the-art methods (Anchor, FactorNet) at 200-bp resolution, and a hundredfold to thousandfold speedup over many-to-one neural network approaches.
- **Visible evidence base** Main text figures (Figs 1–4), supplemental tables S1–S9, supplemental figures S1–S10, methods section, software availability statement
- **Missing materials affecting confidence** Actual figure images and supplemental files not provided; exact numerical results per TF–cell type pair not fully detailed in text; hyperparameter choices and training details partially described; no ablation studies shown in text; comparison methodology at 1-bp resolution described but not fully detailed

## Reviewer
- **Overall assessment** The manuscript presents a technically sound and potentially valuable contribution to computational genomics. The core idea of adapting a many-to-many U-Net architecture to predict TF binding at single-nucleotide resolution is well motivated and the reported performance improvements are notable. However, several aspects require clarification and additional validation before the claims can be fully accepted. The speed advantage is compelling, but the biological interpretability and generalizability claims need stronger support. The manuscript is clearly written and accessible to a broad audience, though some technical details are underspecified.
- **Who would be interested in the results, and why** Computational biologists developing deep learning methods for regulatory genomics; experimental biologists studying TF binding mechanisms; researchers interested in cell type–specific gene regulation; method developers in the ENCODE-DREAM challenge community; bioinformaticians working on genome-wide prediction tasks where computational efficiency is critical.
- **Major strengths** 1) Novel application of many-to-many architecture to TF binding prediction, addressing a key limitation of many-to-one approaches. 2) Comprehensive benchmarking against state-of-the-art methods on standardized data. 3) Impressive computational speedup, making genome-wide predictions practical. 4) Use of multiple validation strategies (cross-cell-type, cross-chromosome, ChIP-exo). 5) Clear motivation and well-structured presentation.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** **Originality**: The adaptation of U-Net to single-nucleotide TF binding prediction is a novel contribution, though the underlying concept of using convolutional networks for regulatory genomics is established. The many-to-many architecture for this specific problem is a meaningful advance. **Scientific importance**: The problem of cell type–specific TF binding prediction is of high importance for understanding gene regulation and disease mechanisms. The computational efficiency gains could enable broader applications. However, the biological insights derived from the method are not deeply explored. **Interdisciplinary readership**: The work bridges deep learning and genomics, with potential interest for both communities. The presentation is accessible, though some genomics-specific details may challenge non-specialists. **Technical soundness**: The methodology is generally sound, but several validation gaps and underspecified details (see Major Concerns) need addressing. The performance claims are supported by the reported metrics, but the comparison methodology requires clarification. **Readability for nonspecialists**: The manuscript is well written with clear figures (as described) and logical flow. Technical terms are explained adequately, though the deep learning architecture details may be dense for some readers.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Leopard substantially outperformed the state-of-the-art methods Anchor and FactorNet, improving the predictive AUPRC by 19% and 27%, respectively, when evaluated at 200-bp resolution."
- **Evidence pointer** Figure 4A, Supplemental Figure S3, Methods "Method comparison at 200-bp resolution"
- **Concern** The comparison at 200-bp resolution uses a modified version of Leopard (Leopard-200-bp) with an additional frequency feature. The manuscript does not clearly specify whether the same hyperparameter tuning, training procedure, and validation strategy were used for all compared methods. Differences in training protocols, early stopping criteria, or model selection could bias the comparison. Additionally, the statistical significance testing is described as paired Wilcoxon signed-rank tests, but the number of samples, the exact pairing strategy, and whether multiple testing correction was applied are not reported.
- **Why it matters** Fair benchmarking is essential to support the claim of outperforming state-of-the-art methods. Underspecified comparison protocols undermine confidence in the reported improvements and prevent independent replication.
- **Resolution test** Provide a detailed comparison protocol including hyperparameter search space, model selection criteria, number of random seeds, and full statistical reporting (effect sizes, confidence intervals, p-values with correction). Ideally, release code and configuration files for all compared methods to enable exact replication.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Leopard accurately identified TF binding profiles for the 10 TFs in this study, with a median prediction AUROC of 0.982. In 19 out of 23 (83%) testing TF–cell type pairs, Leopard achieved high AUROCs above 0.970."
- **Evidence pointer** Figure 2A–D, Supplemental Tables S3–S5
- **Concern** The positive class definition requires both a ChIP-seq peak and a FIMO motif hit. This composite label may inflate performance metrics because the model receives motif-relevant sequence information and open chromatin information as inputs. The manuscript does not report performance when using ChIP-seq peaks alone as the gold standard, nor does it analyze cases where binding occurs without a motif match (indirect binding). The AUPRC values (mean 0.208) are low in absolute terms, and the manuscript does not discuss whether this level of precision is practically useful for genome-wide predictions.
- **Why it matters** The label construction directly affects the interpretability and generalizability of the results. If the method only predicts motif-containing open chromatin regions, its novelty over simpler baselines (motif scanning + DNase-seq thresholding) is less clear. The practical utility of the predictions depends on precision at genome-wide scale.
- **Resolution test** Report performance with alternative gold standard definitions (e.g., ChIP-seq peaks only, with and without motif filtering). Provide precision-recall curves at genome-wide scale with estimated number of true binding sites. Discuss the fraction of true binding events that lack motifs and how the method handles these cases.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Leopard features a hundredfold to thousandfold speedup compared with current many-to-one machine learning methods."
- **Evidence pointer** Figure 4B, Supplemental Figure S7
- **Concern** The speed comparison is presented as a major advantage, but the benchmarking methodology is not fully described. It is unclear whether the comparison uses the same hardware, batch sizes, and optimization for all methods. The manuscript does not report the total wall-clock time for training versus inference separately, nor does it account for the time required for hyperparameter tuning. The speedup claim appears to be for inference only, but this is not explicitly stated.
- **Why it matters** Computational efficiency is a key selling point, but the claim must be precisely scoped and fairly benchmarked. If the speedup is only for inference and training times are comparable or longer, the practical advantage may be less significant for users who need to retrain models frequently.
- **Resolution test** Provide detailed benchmarking setup including hardware specifications, software versions, batch sizes, and whether times include data loading and preprocessing. Report training and inference times separately for all methods. Discuss the implications of the speedup for typical use cases (e.g., genome-wide prediction for multiple cell types).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "The neural network architecture of Leopard"
- **Evidence pointer** Supplemental Table S1
- **Issue** The manuscript states that the architecture is adapted from U-Net but does not provide a complete description of all hyperparameters (e.g., number of filters per layer, dropout rates, learning rate schedule, weight initialization). The supplemental table is referenced but not visible in the provided material.
- **Required correction** Include a complete architecture specification in the main text or ensure the supplemental table provides all necessary details for independent implementation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Benchmarking Leopard prediction against the ChIP-exo data"
- **Evidence pointer** Figure 3A–E
- **Concern** The ChIP-exo analysis uses a within-cell-type model, which differs from the cross-cell-type approach used for ChIP-seq. The manuscript does not explain why this difference is justified or how it affects the interpretation of the results.
- **Required correction** Clarify the rationale for using within-cell-type models for ChIP-exo and discuss any implications for the generalizability of the findings.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Location not provided
- **Issue** The discussion mentions alternative methods (CUT&RUN-seq, ChIP-nexus, SLIM-ChIP) but does not discuss how Leopard could be adapted to these data types or whether the model would benefit from higher-resolution experimental data.
- **Required correction** Add a brief discussion of potential adaptations to newer experimental technologies and how the model might leverage higher-resolution data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, "Leopard accurately identifies cell type–specific TF binding profiles at single-nucleotide resolution"
- **Evidence pointer** Figure 2A–D
- **Concern** The manuscript reports median AUROC and mean AUPRC but does not provide confidence intervals or variability measures across the 23 testing pairs. The spread of performance across TFs and cell types is not discussed.
- **Required correction** Report performance distributions (e.g., box plots or confidence intervals) and discuss any outliers or patterns across TFs and cell types.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Data collection and preprocessing"
- **Evidence pointer** Location not provided
- **Issue** The manuscript states that DNase-seq signals were quantile normalized following the Anchor pipeline, but the specific implementation details (e.g., reference panel, bin size) are not provided.
- **Required correction** Provide sufficient detail on the normalization procedure to enable replication.

## Risk / unsupported claims
- The claim of "single-nucleotide resolution" is supported by the architecture and ChIP-exo validation, but the practical resolution may be limited by the input features (DNase-seq has limited resolution) and the label definition requiring motif hits.
- The statement that "Leopard distinguishes the putative binding events from nonbinding ones" based on a single example (Fig 2E) is anecdotal and not quantitatively supported.
- The claim that "longer inputs lead to significantly better performance" is based on a comparison of five input lengths but the statistical significance of these differences is not reported.
- The generalizability of the method to TFs not included in the training set is not tested or discussed.
- The performance on cell types not represented in the training data is not explicitly evaluated, despite the cross-cell-type design.
- The biological interpretability of the learned features (e.g., via saliency maps) is demonstrated only qualitatively and not systematically evaluated.