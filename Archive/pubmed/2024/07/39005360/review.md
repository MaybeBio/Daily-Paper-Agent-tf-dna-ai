## Review setup
- **Input scope** Full manuscript text (abstract, main text, figure legends not provided, methods summarized)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and generalizability as presented in the provided text
- **Shared manuscript claim summary** The authors present GET, a foundation model for transcriptional regulation that uses chromatin accessibility and sequence information to predict gene expression across 213 human cell types, with claims of experimental-level accuracy in unseen cell types, transferability across platforms, and utility in identifying regulatory elements, transcription factor interactions, and disease-relevant mechanisms
- **Visible evidence base** Main text descriptions, figure references (Figures 1-6), supplementary figure references, performance metrics (Pearson correlations, R² values, precision values, enrichment statistics), and methodological summaries
- **Missing materials affecting confidence** Figure panels and legends, detailed methods sections, model architecture specifics, hyperparameter choices, training data processing details, full benchmark comparisons, code availability, and complete statistical analyses

## Reviewer
- **Overall assessment** The manuscript presents a potentially significant advance in computational modeling of transcriptional regulation, with a novel architecture that extends effective sequence context beyond existing models and demonstrates strong performance in held-out cell types. The claims of experimental-level accuracy and cross-platform transferability are notable and, if fully validated, would represent an important contribution. However, the provided text lacks sufficient methodological detail and complete evidence to fully assess the robustness of the claims. Several key comparisons, statistical validations, and technical specifications are referenced but not fully described. The biological applications, particularly the PAX5 case study, are compelling but require more rigorous validation to establish causality. The work is likely to interest a broad audience in genomics, computational biology, and disease genetics, but the current evidence base is insufficient to fully establish all claims.

- **Who would be interested in the results, and why** Computational biologists developing foundation models for genomics, researchers studying transcriptional regulation and gene expression control, geneticists investigating non-coding variants and disease mechanisms, and experimental biologists seeking predictive tools for regulatory element discovery. The model's claimed generalizability and interpretability would appeal to those working across diverse cell types and conditions, and the PAX5 case study would interest leukemia researchers specifically.

- **Major strengths** The two-stage pretraining-finetuning architecture is conceptually well-motivated and addresses a real limitation in existing models. The use of chromatin accessibility data without paired expression for pretraining is a practical and scalable approach. The demonstrated performance in unseen cell types, if robust, would be a meaningful advance. The integration of causal discovery with structural prediction represents an innovative pipeline for generating testable hypotheses about transcription factor interactions. The PAX5 case study provides a concrete example of the model's potential utility in interpreting disease-associated variants.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "GET achieves experimental-level accuracy in predicting gene expression even in previously unseen cell types"
- **Evidence pointer** Figure 1c-d, Supplementary Figure 2a-c
- **Concern** The claim of "experimental-level accuracy" is supported by a single example (astrocytes, r=0.94) and aggregate statistics that are not fully described. The comparison to experimental replicates (r=0.92-0.99) is based on a limited set of culture systems and may not represent the full range of experimental variability across all cell types. The negative R² values for baseline methods (TSS accessibility R²=-0.23, gene activity score R²=-0.67) suggest these baselines are poorly calibrated, which may inflate the relative performance of GET. The manuscript does not report confidence intervals, error bars, or variability across the 213 cell types, making it impossible to assess whether the performance is consistently high or driven by a subset of cell types.
- **Why it matters** The central claim of the manuscript rests on the model's ability to predict expression in unseen cell types at experimental accuracy. If this claim is not robustly supported across the full range of cell types, the generalizability argument is weakened. The comparison to experimental replicates is critical for establishing the "experimental-level" claim, and the current evidence is insufficient.
- **Resolution test** Provide per-cell-type performance distributions (e.g., box plots or histograms of Pearson r and R² across all 213 cell types), confidence intervals for the reported metrics, and a more comprehensive comparison to experimental replicates across multiple cell types and conditions. Report the number of genes and regions used for evaluation, and clarify how the R² values are computed (e.g., across genes, across regions, or across both).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "GET outperforms current models in predicting lentivirus-based massive parallel reporter assay readout with reduced input data"
- **Evidence pointer** Figure 2e-g, Supplementary Figure 3a-c
- **Concern** The comparison to Enformer on lentiMPRA data is described qualitatively, but the specific metrics, the number of elements evaluated, the statistical significance of the performance difference, and the details of the "reduced input data" condition are not provided. The claim that GET outperforms Enformer "with reduced input data" is ambiguous, as it is unclear what data reduction was applied and whether this is a fair comparison. Additionally, the manuscript does not describe how the in silico lentiMPRA procedure was implemented, including how the minipromoter activity was modeled and how the averaging over insertions was performed.
- **Why it matters** The lentiMPRA benchmark is a key demonstration of the model's practical utility for regulatory element prediction. Without detailed metrics and a clear description of the comparison, the claim of superiority over Enformer cannot be evaluated. The "reduced input data" aspect is particularly important, as it suggests a practical advantage that is not clearly defined.
- **Resolution test** Provide the full lentiMPRA benchmark results, including the number of elements, the performance metrics (e.g., Pearson r, Spearman rho, AUROC), the statistical test used to compare GET and Enformer, and a clear description of the "reduced input data" condition. Describe the in silico lentiMPRA procedure in sufficient detail to allow replication.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "GET-based causal discovery identifies potential transcription factor-transcription factor interactions" and "we achieved precisions of 25.2% and 15.9%, respectively" for causal and correlation approaches
- **Evidence pointer** Figure 4f-h, Supplementary Figure 6-7
- **Concern** The causal discovery approach using LiNGAM on a gene-by-motif matrix is described at a high level, but the validity of applying causal inference to this type of data is not discussed. The assumptions of LiNGAM (linearity, non-Gaussianity, acyclic causal structure) may not hold for gene regulatory data, and the manuscript does not address potential violations. The precision values are reported without confidence intervals or a clear description of how the "known" interactions in STRING were defined and matched to motif-level predictions. The comparison to the mass spectrometry-based study and the colocalization score is described, but the details of these comparisons are not provided.
- **Why it matters** The causal discovery component is a distinctive feature of the manuscript and is used to generate the structural catalog and the PAX5 case study. If the causal inference is not methodologically sound, the downstream analyses are compromised. The precision values are the primary quantitative evidence for the utility of this approach, and they need to be rigorously established.
- **Resolution test** Provide a detailed description of the LiNGAM implementation, including how the gene-by-motif matrix was constructed, how the model was fit, and how the assumptions were validated. Report confidence intervals for the precision values and describe the matching procedure between predicted motif pairs and STRING interactions. Provide a more detailed comparison to the alternative approaches, including the specific metrics and statistical tests used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "In fetal erythroblasts, we identify distal (>1Mbp) regulatory regions that were missed by previous models"
- **Evidence pointer** Figure 3a-d, Supplementary Figure 4a-c
- **Concern** The identification of distal regulatory regions is presented as a key biological finding, but the evidence is limited to a comparison with "previous models" without specifying which models, what the comparison criteria were, and whether the identified regions were experimentally validated. The manuscript does not describe how the regulatory regions were defined from the model's predictions, how the distance threshold was chosen, or whether the identified regions are supported by independent evidence such as chromatin conformation data or genetic association studies.
- **Why it matters** The claim of identifying novel distal regulatory regions is a strong biological claim that would be of interest to a wide audience. If the identified regions are not validated or the comparison to previous models is not rigorous, the claim is not established.
- **Resolution test** Provide a detailed description of the regulatory region identification procedure, including the model interpretation method, the criteria for defining a regulatory region, and the distance threshold. Specify which previous models were compared and how the comparison was performed. Provide independent validation of the identified regions, such as Hi-C data, eQTL analysis, or experimental perturbation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We show GET outperforms current models in predicting lentivirus-based massive parallel reporter assay readout with reduced input data" and "GET achieved a Pearson correlation of 0.90 compared to Enformer's performance of 0.74" for K562 CAGE
- **Evidence pointer** Supplementary Figure 2g
- **Concern** The comparison to Enformer on K562 CAGE prediction is reported as a single Pearson correlation for each model, but the details of the evaluation are not provided. It is unclear how many genes or regions were evaluated, whether the comparison was performed on the same set of regions, and whether the difference is statistically significant. The manuscript does not describe how the CAGE data were processed, how the model was finetuned for this task, or whether the comparison is fair given that Enformer was trained on a different set of data.
- **Why it matters** The claim of superiority over Enformer is a key differentiator for the model. If the comparison is not rigorously performed, the claim is not established.
- **Resolution test** Provide the full details of the CAGE comparison, including the number of regions, the evaluation metric, the statistical test for the difference, and a description of the data processing and model finetuning. Ensure that the comparison is performed on the same set of regions and that the evaluation protocol is fair to both models.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Model description
- **Evidence pointer** Methods-Model architecture
- **Issue** The description of the model architecture is too brief. The manuscript states that an "embedding and attention architecture" is used, but does not specify the number of layers, attention heads, embedding dimensions, or other architectural details. This makes it difficult to assess the novelty of the architecture or to replicate the model.
- **Required correction** Provide a more detailed description of the model architecture, including the number of parameters, the number of layers, the attention mechanism, and the input representation. Consider including a diagram or pseudocode.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Training data
- **Evidence pointer** Methods-ATAC-seq data processing and RNA-seq data processing
- **Issue** The manuscript states that pseudobulk chromatin accessibility data from 213 cell types were used, but does not provide details on the data sources, the number of cells per cell type, the quality control criteria, or the processing pipeline. This information is essential for reproducibility.
- **Required correction** Provide a detailed description of the data sources, the number of cells per cell type, the quality control criteria, and the processing pipeline. Consider including a supplementary table with this information.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Performance metrics
- **Evidence pointer** Figure 1c-d, Figure 2g, Figure 3c-d
- **Issue** The manuscript reports Pearson correlations and R² values without confidence intervals or measures of variability. It is unclear whether the reported values are stable across different random seeds, data splits, or evaluation sets.
- **Required correction** Report confidence intervals for the key performance metrics and describe the variability across different evaluation sets or model initializations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 4h
- **Evidence pointer** Figure 4h
- **Issue** The precision comparison in Figure 4h is described in the text, but the figure itself is not visible in the provided text. It is unclear what the x-axis and y-axis represent and how the different approaches are compared.
- **Required correction** Provide a clear description of the figure, including the axes, the data points, and the comparison being made.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Code availability
- **Evidence pointer** Data availability
- **Issue** The manuscript states that precomputed results are available, but does not mention whether the model code, training scripts, or evaluation pipelines are publicly available. This is important for reproducibility and for the community to build on the work.
- **Required correction** Provide a statement on code availability, including a link to a public repository if applicable.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Causal discovery
- **Evidence pointer** Methods-Causal discovery of regulator interaction
- **Issue** The manuscript uses LiNGAM for causal discovery but does not discuss the limitations of this approach, such as the assumption of no latent confounders and the difficulty of distinguishing causation from correlation in observational data.
- **Required correction** Add a discussion of the limitations of the causal discovery approach and how the results should be interpreted in light of these limitations.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Model evaluation
- **Evidence pointer** Figure 1e
- **Issue** The manuscript reports performance on adult cell types when trained on fetal data, but the number of adult cell types and the specific cell types are not described. It is unclear whether the performance is consistent across all adult cell types or driven by a subset.
- **Required correction** Provide a breakdown of the performance across individual adult cell types and describe the characteristics of the cell types where performance is lower.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Biological validation
- **Affected element** PAX5 case study
- **Evidence pointer** Figure 6d-e
- **Issue** The PAX5-NR2C2 interaction is validated by proximity labeling, but the manuscript does not describe the statistical significance of the interaction or whether the increased interaction with the G183S mutant is reproducible across replicates.
- **Required correction** Provide statistical analysis of the proximity labeling results, including the number of replicates and the significance of the observed differences.

## Risk / unsupported claims
- The claim of "experimental-level accuracy" is not fully supported by the evidence provided, as the comparison to experimental replicates is limited and the variability across cell types is not reported.
- The claim that GET "outperforms current models" on lentiMPRA and CAGE benchmarks is not fully supported, as the details of the comparisons are not provided.
- The claim of identifying "distal (>1Mbp) regulatory regions that were missed by previous models" is not supported by sufficient evidence, as the comparison criteria and validation are not described.
- The causal discovery results are presented as identifying transcription factor interactions, but the validity of the causal inference approach is not established.
- The generalizability of the model to new sequencing platforms and non-physiological cell types is claimed, but the evidence is limited to a few examples and the details of the evaluations are not provided.
- The biological significance of the PAX5 G183S mutation is suggested, but the causal link between the mutation, the altered interaction, and the transcriptional program is not fully established.