## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and data/code availability statements.
- **Assessment boundary** Scientific validity, technical soundness, reproducibility, and support of claims by the presented evidence. No assessment of editorial fit or publication policy.
- **Shared manuscript claim summary** The authors present BendNet, a deep neural network trained on yeast loop-seq data, to predict intrinsic DNA bendability at base resolution. They claim high accuracy and generalizability across species and assays, and use the model to generate genome-wide bendability maps for human and 307 other species. They report associations between predicted bendability and chromatin features, replication timing, TF binding, disease-associated variants, and eccDNA, and provide a webserver for querying predictions.
- **Visible evidence base** Main text figures (Figures 1–6), supplementary figures (Supplementary Figures 1–7), supplementary tables (Supplementary Table 1), methods descriptions, and data availability statements. Raw data and code are referenced via external repositories.
- **Missing materials affecting confidence** The manuscript text does not include the actual figures or supplementary material content, only figure callouts and brief descriptions. Statistical details (exact p-values, confidence intervals, multiple testing corrections) are not fully reported in the text. The independent validation dataset section header is present but its content is not provided. The full list of 307 species and the details of the webserver implementation are not described in the provided text.

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful deep learning tool for predicting DNA bendability at base resolution, trained on a substantial experimental dataset. The reported correlations with independent experimental measurements are encouraging. However, the manuscript as provided has several technical gaps that prevent full evaluation of the core claims. The most significant concerns are the lack of a clear baseline comparison for the model's predictive performance, the absence of a rigorous demonstration that base-resolution predictions are meaningfully better than lower-resolution alternatives, and the incomplete description of the independent validation datasets. The biological findings are largely correlative and would benefit from more direct experimental or mechanistic support. The resource aspect (307 species, webserver) is valuable but its accessibility and quality are not fully assessable from the provided text.
- **Who would be interested in the results, and why** Researchers in chromatin biology, DNA mechanics, and gene regulation would be interested in the genome-wide bendability maps and the potential link between DNA sequence-encoded mechanics and regulatory function. Computational biologists developing sequence-to-function prediction models would be interested in the architecture and training approach. The resource for 307 species could be useful for comparative genomics and evolutionary studies of regulatory DNA.
- **Major strengths**
  - The use of a large, high-throughput experimental dataset (loop-seq) for training is a significant strength.
  - The demonstration of generalizability to independent datasets from different species and assays (E. coli, human, mouse) is compelling.
  - The application to the human genome and the observation of associations with known regulatory features (TSSs, enhancers, TF binding) provides a useful resource and generates testable hypotheses.
  - The provision of a webserver and precomputed predictions for 307 species is a valuable community resource.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that BendNet outperforms other models in prediction accuracy (Figure 1D) and is the fastest deep learning model.
- **Evidence pointer** Results section "Overview of BendNet", Figure 1D, Supplementary Figure 1D–F.
- **Concern** The comparison with other models (Random Forest, SVR, AlexNet, VGG16, GoogleNet22, ResNet34, DNAcycP, DeepBend) is mentioned, but the text does not provide the actual performance metrics (e.g., correlation coefficients, MSE) for each model. Without these numbers, the claim of "outperforms" cannot be quantitatively assessed. Furthermore, the hyperparameter optimization for BendNet is described in detail, but it is unclear if the comparison models were also hyperparameter-tuned to a similar extent. An unfair comparison (e.g., default parameters for others vs. optimized for BendNet) would weaken the claim of superiority.
- **Why it matters** The central technical claim of the paper is that BendNet is a state-of-the-art predictor. If the comparison is not rigorous or the metrics are not reported, the reader cannot verify this claim, which is fundamental to the paper's contribution.
- **Resolution test** Provide a table with the performance metrics (e.g., Pearson R, MSE) for all compared models on the same test set. Describe the hyperparameter tuning process for each comparison model. If default parameters were used, justify this choice and discuss its potential impact on the comparison.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that BendNet provides "base-resolution" predictions and can provide a "finer map" compared to the original 7-bp resolution loop-seq data.
- **Evidence pointer** Abstract, Introduction, Results section "BendNet predicts base-resolution DNA bendability in human", Figure 2A.
- **Concern** The model is trained on data with 7-bp resolution (tiling at 7-bp steps). The claim of "base-resolution" prediction implies the model can assign a bendability value to each base pair. However, the manuscript does not explain how the model achieves this, given the training data resolution. Is the model output a single value per 50-bp window, or does it produce a per-base profile? If it produces a per-base profile, how is this evaluated against experimental data that is only available at lower resolution? The comparison with the original loop-seq data (Figure 2A) shows agreement at a coarse level, but this does not validate per-base predictions.
- **Why it matters** The "base-resolution" aspect is a key selling point of the tool and is used to justify its application to large genomes. If the resolution claim is not technically substantiated, the novelty and utility of the tool are significantly diminished.
- **Resolution test** Clarify the output format of the model. If it is per-base, provide a validation strategy, such as comparing predicted per-base profiles to high-resolution experimental data (e.g., from other assays) or demonstrating that the model can recapitulate known sequence-dependent mechanical features at single-base resolution. If the output is per-window, revise the "base-resolution" claim accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The claim of generalizability based on "independent validation datasets" (E. coli, human, mouse).
- **Evidence pointer** Methods section "Independent validation datasets", Results section "Overview of BendNet", Figure 2B–D, Supplementary Figure 1I.
- **Concern** The "Independent validation datasets" section in Methods is empty in the provided text. The results section mentions correlations with E. coli, human, and mouse datasets, but the details of these datasets (e.g., how they were generated, their size, the specific experimental assay) are not described. Without this information, the reader cannot assess the validity of the validation or the potential for data leakage (e.g., if the human or mouse data was used in any way during model development).
- **Why it matters** Independent validation is crucial for establishing that the model generalizes beyond its training distribution. If the validation datasets are not properly described, the strength of the generalizability claim is unknown.
- **Resolution test** Provide a full description of the independent validation datasets, including the species, the experimental method, the number of data points, and how they were obtained. Confirm that these datasets were not used in any part of the training or model selection process.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that DNA bendability is "associated with" various biological features, including chromatin states, replication timing, TF binding, and disease-associated variants.
- **Evidence pointer** Results sections "Effect of DNA bendability in TSS and TES regions", "Effect of DNA bendability in G4 structure", "Effect of DNA bendability on replication timing", "DNA bendability in disease associated regulatory regions", "Effect of DNA bendability in enhancer regions", "Effect of DNA bendability on TF binding", Figures 3–5.
- **Concern** The reported associations are largely correlative. For example, the correlation between bendability and replication timing (Figure 3G) or GWAS SNP frequency (Figure 3H) does not establish a causal or mechanistic link. The manuscript would be significantly strengthened by a more direct test of the functional relevance of predicted bendability, such as a perturbation experiment (e.g., mutating a specific base to alter predicted bendability and measuring the effect on a biological process) or a more sophisticated analysis that controls for confounding factors (e.g., GC content, which is shown to be correlated with bendability).
- **Why it matters** The biological insights are a major part of the paper's claimed significance. If these are only weak correlations, the impact of the work is reduced.
- **Resolution test** Add a more direct experimental or analytical test of the functional role of bendability. For example, use the in silico mutagenesis predictions to identify specific mutations that are predicted to strongly alter bendability and test their effect on TF binding or nucleosome positioning in a reporter assay. Alternatively, perform a statistical analysis that controls for known confounders like GC content to show that the association with bendability is independent.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that the model can be applied to 307 species and the resulting resource is comprehensive.
- **Evidence pointer** Results section "Resource of DNA bendability in 307 species", Figure 6B, C, Supplementary Table 1.
- **Concern** The manuscript states that predictions were made for 307 species, but the details of this analysis are sparse. It is unclear how the model, trained on yeast data, performs on genomes with very different sequence compositions and organizational features. The comparison of average bendability across species (Figure 6B) is interesting, but the biological interpretation is not discussed in depth. The quality of the predictions for non-yeast species is not assessed, as no experimental validation is presented for these species.
- **Why it matters** The cross-species resource is a major deliverable of the paper. If the predictions for these species are not reliable, the resource could be misleading.
- **Resolution test** Provide a more detailed analysis of the cross-species predictions, including an assessment of prediction confidence or uncertainty. If possible, validate predictions for at least one or two non-yeast species against experimental data. Discuss the potential limitations of applying a model trained on yeast to distantly related species.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Model architecture"
- **Evidence pointer** Methods section "Model architecture"
- **Issue** The description of the model architecture is high-level. The text mentions "convolutional blocks" and "capsule blocks" but does not provide specific details such as the number of layers, kernel sizes, activation functions, or the total number of parameters for the final model.
- **Required correction** Provide a more detailed description of the architecture, possibly in a table or supplementary figure, to allow for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "BendNet predicts base-resolution DNA bendability in human"
- **Evidence pointer** Results section "BendNet predicts base-resolution DNA bendability in human", Figure 3A, B.
- **Issue** The text states that PCGs exhibit the strongest bendability drop at TSSs and TESs, but the statistical significance of the differences between gene types (PCG, lncRNA, ncRNA, pseudogene) is not reported.
- **Required correction** Add statistical tests (e.g., Wilcoxon rank-sum test) comparing the bendability profiles of different gene types and report the resulting p-values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data and code availability
- **Evidence pointer** Data Availability and Code Availability sections
- **Issue** The code availability statement is not present in the provided text, although the Data Availability section mentions a GitHub repository. The availability of the code is crucial for reproducibility.
- **Required correction** Add a clear Code Availability statement with the repository URL and a version or DOI if applicable.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "DNA bendability of human eccDNA"
- **Evidence pointer** Results section "DNA bendability of human eccDNA", Figure 6A.
- **Issue** The analysis of eccDNA is brief. It is stated that eccDNA sequences are "significantly bendable" compared to genomic background, but the control group is not well-defined. It is unclear if the control is matched for GC content, length, or genomic location.
- **Required correction** Clarify the composition of the control group and describe the statistical test used to establish significance.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion is relatively short and does not fully contextualize the findings within the broader field of DNA mechanics and gene regulation. It also does not discuss potential limitations of the approach in detail.
- **Required correction** Expand the discussion to include a more thorough comparison with existing methods and a more critical assessment of the limitations and potential biases of the model and the biological interpretations.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative performance comparison with baseline models.
  - R1-M2: Unclear definition and validation of "base-resolution" predictions.
  - R1-M3: Incomplete description of independent validation datasets.
  - R1-M4: Correlative biological findings without direct functional validation or control for confounders.

- **Assessment against Nature-style criteria**
  - **Originality** The use of a deep learning model trained on high-throughput loop-seq data to predict genome-wide bendability is a novel application. The idea of using such a model to generate a resource for multiple species is also original. However, the underlying concept of sequence-dependent DNA mechanics is well-established, and the novelty lies primarily in the scale and resolution of the predictions.
  - **Scientific importance** The potential to provide base-resolution bendability maps for entire genomes is significant and could be a valuable resource for the community. The observed associations with regulatory features are interesting but require further validation to establish their biological importance. The cross-species resource could enable comparative studies, but its reliability needs to be demonstrated.
  - **Interdisciplinary readership** The work bridges computational biology, genomics, and biophysics. It would be of interest to researchers in these fields, as well as those studying gene regulation and chromatin structure. The resource and webserver could attract a broad user base.
  - **Technical soundness** The training data is substantial and the reported correlations with independent datasets are promising. However, the lack of a rigorous model comparison and the unclear definition of "base-resolution" are significant technical weaknesses that need to be addressed. The biological analyses are mostly correlative and would benefit from more robust statistical controls.
  - **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear. However, some sections, particularly the model architecture description, may be challenging for readers without a deep learning background. The biological findings are presented in an accessible way.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea and the potential resource are valuable. However, the manuscript in its current form does not fully establish the technical superiority of the model or the validity of the "base-resolution" claim. The biological insights, while interesting, are not yet compelling enough to be the primary basis for the paper's significance. Addressing the major concerns, particularly R1-M1 and R1-M2, is essential.

## Risk / unsupported claims
- The claim that BendNet "outperforms" other models is unsupported without quantitative performance metrics for all models.
- The claim of "base-resolution" prediction is not technically substantiated given the 7-bp resolution of the training data.
- The generalizability claim is weakened by the incomplete description of the independent validation datasets.
- The biological associations (e.g., with replication timing, GWAS SNPs) are presented as meaningful without adequate statistical controls or functional validation.
- The statement that "BendNet predictions are as sensitive as loop-seq measurements in detecting DNA bendability in individual regions" is a strong claim that is not quantitatively supported in the provided text.
- The cross-species resource for 307 species is presented as a comprehensive resource, but the accuracy and limitations of these predictions are not assessed.