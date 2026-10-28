## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and data availability statements.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and significance of the claims presented in the manuscript. No assessment of editorial fit or publication policy.
- **Shared manuscript claim summary** The authors present GraphReg, a graph attention network-based deep learning framework that integrates 1D epigenomic data or DNA sequence with 3D chromatin interaction data to predict gene expression. They claim improved accuracy over CNN baselines, enhanced identification of functional enhancers via feature attribution, and accurate prediction of direct TF targets via in silico motif ablation.
- **Visible evidence base** Main text figures (Fig. 1, 2), supplementary figures (S1–S38), supplementary tables (S1–S3), methods section, and data availability statements.
- **Missing materials affecting confidence** Supplementary figures and tables referenced in the text were not provided in the submitted material. Trained model weights and code are referenced via GitHub but were not independently verified. Full hyperparameter details, training curves, and computational resource specifications are not fully described in the visible text.

## Reviewer
- **Overall assessment** The manuscript presents a technically sophisticated and biologically motivated approach to a longstanding problem in regulatory genomics. The integration of 3D chromatin interaction data via graph attention networks is a novel and sensible architectural choice. The authors provide a comprehensive set of experiments across multiple cell types and assays, with validation against CRISPR-based enhancer screens and TF perturbation data. However, several methodological details and statistical rigor issues need to be addressed before the central claims can be fully accepted. The comparison against CNN baselines is reasonable but could be strengthened with additional baselines and ablations. The feature attribution and motif analysis sections are promising but require more rigorous statistical controls and clearer presentation of effect sizes.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and machine learning applied to genomics. The work is directly relevant to those studying enhancer-promoter interactions, gene expression prediction, and interpretation of noncoding variation. The methodological framework may also interest the broader deep learning community working on graph-structured biological data.
- **Major strengths** 1) Novel and biologically motivated use of graph attention networks to incorporate 3D chromatin interactions for gene expression prediction. 2) Comprehensive evaluation across multiple cell types, assays, and validation datasets. 3) Demonstration of improved performance over CNN baselines, particularly for complex genes with many interactions. 4) Feature attribution analysis provides interpretable insights into distal regulatory elements. 5) In silico motif ablation experiments connect model predictions to TF perturbation data.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical comparison methodology), R1-M2 (baseline comparison fairness), R1-M3 (feature attribution validation), R1-M4 (motif analysis statistical rigor).
- **Assessment against Nature-style criteria** **Originality** High. The use of graph attention networks for integrating 3D chromatin data into gene expression prediction is a novel contribution that extends prior work in a meaningful direction. **Scientific importance** High. The problem of linking distal enhancers to genes is fundamental and unresolved; improved modeling has direct implications for interpreting noncoding variation. **Interdisciplinary readership** Moderate to high. The work bridges genomics, machine learning, and regulatory biology, and should appeal to readers across these fields. **Technical soundness** Moderate. The core methodology is sound, but several statistical and validation issues need to be resolved. **Readability for nonspecialists** Good. The manuscript is generally well-written and accessible, though some methodological sections assume familiarity with deep learning and genomics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the experiments are extensive, but the statistical rigor and validation details need strengthening before the claims are fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that GraphReg significantly outperforms CNN baselines based on Wilcoxon signed-rank tests on NLL values from 50 random samples of 2000 genes.
- **Evidence pointer** Results section, Figure 2, location not provided
- **Concern** The statistical comparison methodology is unclear. The authors state they randomly sampled 2000 genes 50 times and computed mean NLL for both models, then performed a Wilcoxon signed-rank test. However, it is not clear whether the 50 samples are independent, whether the same gene sets are used for both models in each sample, and how the mean NLL is computed across genes. Additionally, the Wilcoxon signed-rank test on 50 paired samples may have low power to detect differences, and the choice of 2000 genes per sample is not justified.
- **Why it matters** The central claim of improved performance over baselines rests on this statistical comparison. If the methodology is flawed or underpowered, the conclusion may not be robust.
- **Resolution test** Provide a clear description of the sampling procedure, including whether the same gene sets are used for both models, how the mean NLL is computed, and whether the 50 samples are independent. Consider using a more appropriate statistical test, such as a paired test across all genes or a bootstrap procedure with confidence intervals. Report effect sizes and confidence intervals in addition to p-values.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline comparison fairness
- **Claim pointer** The authors claim GraphReg outperforms CNN baselines, but the CNN baselines may not be optimally configured.
- **Evidence pointer** Methods section, Supplemental Figure S1, location not provided
- **Concern** The CNN baselines (Epi-CNN and Seq-CNN) use dilated convolutions to achieve a large receptive field, but the number of layers, dilation rates, and other hyperparameters may not be optimally tuned. The authors do not report whether hyperparameter search was performed for the baselines or whether the same training procedure was used. If the baselines are underpowered, the comparison is unfair.
- **Why it matters** The claim of superiority over CNNs is a key contribution. If the baselines are not well-tuned, the improvement may be due to suboptimal baselines rather than the graph attention mechanism.
- **Resolution test** Report the hyperparameter search procedure for both GraphReg and CNN baselines. Ensure that the baselines are given comparable computational resources and training effort. Consider including additional baselines, such as a transformer-based model or a simpler graph convolutional network, to contextualize the improvement.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Feature attribution validation
- **Claim pointer** The authors claim that feature attribution with GraphReg accurately identifies functional enhancers, validated by CRISPRi-FlowFISH and TAP-seq.
- **Evidence pointer** Results section, Figure 3, location not provided
- **Concern** The validation of enhancer identification relies on auPR curves, but the details of how the auPR is computed are not fully described. Specifically, it is unclear how the set of candidate enhancers is defined, how the positive set (functional enhancers) is determined from the CRISPR screens, and whether the auPR is computed per gene or across all genes. Additionally, the comparison to ABC and CNN baselines may be confounded by differences in the underlying models.
- **Why it matters** The claim that GraphReg identifies functional enhancers more accurately than existing methods is a major contribution. If the evaluation is not rigorous, the claim is not well-supported.
- **Resolution test** Provide a detailed description of the auPR computation, including the definition of candidate enhancers, the positive set, and the aggregation across genes. Consider reporting precision-recall curves and auPR values for individual genes. Discuss potential sources of bias in the evaluation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Motif analysis statistical rigor
- **Claim pointer** The authors claim that Seq-GraphReg accurately predicts direct TF targets via in silico motif ablation, validated by CRISPRi TF knockout experiments.
- **Evidence pointer** Results section, Figure 4, location not provided
- **Concern** The motif ablation analysis uses FIMO to identify TF motifs in high and low saliency regions, and Fisher's exact test to assess enrichment. However, the multiple testing correction is only applied within each gene, not across all genes and motifs tested. This could lead to inflated false discovery rates. Additionally, the choice of the saliency threshold for defining high and low saliency regions is not described, and the analysis may be sensitive to this choice.
- **Why it matters** The claim that Seq-GraphReg captures meaningful TF regulatory information is important for the broader utility of the model. If the statistical analysis is not rigorous, the conclusions may not be reliable.
- **Resolution test** Describe the saliency threshold selection procedure. Apply multiple testing correction across all gene-motif pairs tested. Consider using a more robust statistical test, such as a permutation-based approach, to assess enrichment.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1C
- **Evidence pointer** Figure 1C, location not provided
- **Issue** The example region shown in Figure 1C is described as a 6-Mb region of Chromosome 19 in K562 cells, but the figure is difficult to interpret without more detailed annotation. The predicted and true CAGE signals are shown, but it is unclear how the reader should assess the quality of the prediction from this example.
- **Required correction** Add annotations to Figure 1C to highlight key features, such as known enhancer-promoter pairs, and provide a brief description in the figure legend of what the reader should observe.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, model training
- **Evidence pointer** Methods section, location not provided
- **Issue** The authors state that hyperparameters were chosen based on validation performance but do not provide the specific values or the search range. This limits reproducibility.
- **Required correction** Provide a table of hyperparameters used for each model and dataset, including learning rate, batch size, number of epochs, number of layers, number of attention heads, and any regularization parameters.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results section, Figure 2
- **Evidence pointer** Figure 2, location not provided
- **Issue** The box plots in Figure 2 show NLL distributions, but the y-axis scale is not clearly labeled, and the units are not intuitive. It would be helpful to also show the distribution of R values or a more interpretable metric.
- **Required correction** Consider showing both NLL and R values in the box plots, or provide a clear explanation of the NLL scale and its interpretation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, location not provided
- **Issue** The discussion mentions potential extensions to single-cell data and other transcriptomic assays but does not discuss potential limitations of the approach, such as the reliance on the quality of 3D interaction data or the computational cost of training on large genomes.
- **Required correction** Add a paragraph discussing limitations and potential failure modes of the approach.

## Risk / unsupported claims
- The claim that GraphReg is "the most comprehensive and versatile model" for gene expression prediction is not directly supported by the experiments presented, as only a limited set of baselines was compared.
- The claim that GraphReg "accurately predicts direct TF targets" is based on a single analysis pipeline and may be sensitive to the choice of motif database and saliency threshold.
- The generalizability of the model to cell types not represented in the training data is only partially addressed, and the cross-cell-type experiments are limited to a few pairs of cell lines.
- The claim that 3D interaction data are essential for improved performance is not fully tested, as the authors do not show results for a model that uses only 1D data with a larger receptive field.