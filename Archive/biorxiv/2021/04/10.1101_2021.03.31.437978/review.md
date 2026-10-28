## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods sections provided; figures and supplemental materials referenced but not provided)
- **Assessment boundary** Scientific claims, methodological soundness, validation adequacy, and presentation quality as assessable from the provided text
- **Shared manuscript claim summary** The authors present GraphReg, a deep learning framework combining convolutional neural networks and graph attention networks to integrate 1D epigenomic data or DNA sequence with 3D chromatin interaction data for predicting gene expression. They claim improved accuracy over CNN baselines, superior identification of functional enhancers validated by CRISPR screens, and accurate prediction of direct TF targets via in silico motif ablation.
- **Visible evidence base** Results text describing performance metrics (NLL, Pearson R, auPR), comparisons to CNN baselines and ABC model, CRISPRi-FlowFISH and TAP-seq validation datasets, TF KO prediction analyses; methods text describing model architecture, training, and data sources
- **Missing materials affecting confidence** All figures and supplemental figures/tables referenced in the text; exact hyperparameter values; full architecture specifications; statistical test details beyond test names; baseline model implementation details; data preprocessing pipelines

## Reviewer
- **Overall assessment** The manuscript presents a technically sophisticated and biologically motivated approach to a longstanding problem in regulatory genomics. The integration of 3D chromatin interaction data via graph attention networks is a reasonable and potentially impactful design choice. The validation strategy using CRISPR perturbation datasets is appropriate and the reported improvements over baselines are encouraging. However, the provided text lacks sufficient detail to fully evaluate the robustness of the claims, particularly regarding statistical significance, baseline fairness, and generalizability. Several claims appear stronger than the evidence presented in the text alone can support.
- **Who would be interested in the results, and why** Computational biologists developing gene regulatory models; experimentalists studying enhancer-promoter interactions and gene regulation; researchers interpreting non-coding genetic variation; machine learning practitioners interested in graph neural networks for genomic applications. The work addresses a central problem in regulatory genomics and offers a practical tool with demonstrated validation.
- **Major strengths** The problem is important and timely. The architectural choice of GATs over GCNs is well motivated biologically. The multi-task learning approach for sequence-based models is sensible. Validation against CRISPRi-FlowFISH and TAP-seq datasets is appropriate and rigorous. The TF knockout prediction analysis via motif ablation is a creative and informative validation strategy. The code and trained models are made available.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical significance), R1-M2 (baseline fairness), R1-M3 (generalizability evidence), R1-M4 (feature attribution validation)
- **Assessment against Nature-style criteria** Originality: High. The combination of GATs with 3D interaction data for gene expression prediction is novel and distinct from prior CNN-based and GCN-based approaches. Scientific importance: High. The problem of linking enhancers to genes and modeling regulatory impact is fundamental and clinically relevant. Interdisciplinary readership: Moderate to high. The work bridges genomics, machine learning, and molecular biology, though the methods section may be challenging for non-specialists. Technical soundness: Moderate based on provided text. The approach is reasonable, but insufficient detail and statistical rigor are provided to fully assess robustness. Readability for nonspecialists: Moderate. The introduction and results are generally clear, but the methods section assumes significant background in both deep learning and genomics.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the validation strategy is appropriate, but the current text does not provide sufficient evidence to fully establish the claims of superiority over existing methods.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims GraphReg models "significantly" outperform CNN baselines and ABC model across multiple metrics (NLL, R, auPR).
- **Evidence pointer** Results section, Figures 2A-B, 3A-D, Supplemental Figures S2-S13
- **Concern** The text reports Wilcoxon signed-rank test results for NLL comparisons but does not provide effect sizes, confidence intervals, or multiple testing corrections. For auPR comparisons, no statistical tests are reported at all. The number of genes used in each analysis is not consistently stated. The claim of "significantly" better performance requires more rigorous statistical reporting.
- **Why it matters** Without proper statistical characterization, the reader cannot assess whether the reported improvements are robust or could arise from chance, particularly given the large number of comparisons performed across cell types, gene sets, and model variants.
- **Resolution test** Provide effect sizes with confidence intervals for all key comparisons. Report exact p-values with multiple testing corrections where applicable. State the number of genes/observations in each analysis. For auPR comparisons, perform and report appropriate statistical tests (e.g., bootstrap or permutation tests).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline fairness
- **Claim pointer** The manuscript claims GraphReg outperforms "state-of-the-art deep learning methods" and CNN baselines.
- **Evidence pointer** Results section, Figures 2A-B, 3A-D, Supplemental Figures S2-S13, Supplemental Tables S1-S2
- **Concern** The CNN baselines (Epi-CNN and Seq-CNN) are described as using dilated CNN layers instead of GAT layers, but the text does not specify whether these baselines were optimized to the same extent as GraphReg models. Hyperparameter tuning, model capacity, and training procedures for baselines are not described. The comparison to Basenji is mentioned but not detailed. The comparison to ABC is presented but the ABC implementation details are not provided.
- **Why it matters** If baselines are not comparably optimized, the reported improvements may reflect differences in tuning effort rather than architectural advantages. This is a common pitfall in deep learning papers and undermines the validity of the comparative claims.
- **Resolution test** Describe the hyperparameter search procedure for all models. Ensure baselines receive comparable tuning effort. Report the number of parameters and training compute for each model. Provide details on the ABC implementation used for comparison.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** The manuscript claims Epi-GraphReg is "cell-type agnostic" and can generalize to new cell types.
- **Evidence pointer** Results section, Figure 2D, Supplemental Figures S11-S13
- **Concern** The cross-cell-type generalization experiments are only performed between K562 and GM3738, two cancer cell lines. The claim of cell-type agnosticism requires testing on more diverse cell types, including non-cancerous or primary cells. Additionally, the text notes that generalization performance depends on the choice of 3D assay and FDR threshold, which complicates the claim.
- **Why it matters** The practical utility of the model depends on its ability to generalize across cell types. Limited testing on two related cell lines does not establish generalizability.
- **Resolution test** Test cross-cell-type generalization on additional cell types with diverse regulatory landscapes. Report performance across different 3D assay and FDR combinations systematically. Discuss limitations of the cell-type agnostic claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Feature attribution validity
- **Claim pointer** The manuscript claims feature attribution on GraphReg models "accurately identifies functional enhancers" and that motif ablation "accurately predicts direct TF targets."
- **Evidence pointer** Results section, Figures 3A-E, 4A-D, Supplemental Figures S22-S23
- **Concern** The text does not describe how feature attribution scores are aggregated across the model to produce enhancer-level scores. The choice of attribution method (saliency vs. DeepSHAP) is not justified. For the TF knockout analysis, the text does not specify how the 100 predicted target genes are selected beyond ranking by predicted logFC, nor how the significance threshold for calling predicted differentially expressed genes is set. The comparison to random baseline is described but the baseline distribution is not fully characterized.
- **Why it matters** The biological interpretability claims are a major contribution of the work. If the attribution methodology is not clearly described and validated, the biological conclusions are not reliable.
- **Resolution test** Describe the feature attribution aggregation procedure in detail. Justify the choice of attribution method. Provide sensitivity analyses for attribution thresholds. Describe the full pipeline for TF target prediction including significance thresholds. Characterize the random baseline distribution more completely.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Model description
- **Evidence pointer** Methods section, "Graph attention networks" subsection
- **Issue** The equations describing the GAT layer are presented without clear definitions of all variables. The notation for the attention mechanism is dense and may be difficult for readers unfamiliar with GATs.
- **Required correction** Provide a clear textual explanation of each equation component. Consider including a schematic diagram of the GAT layer in the main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Training details
- **Evidence pointer** Methods section, "Model architecture and training" subsection
- **Issue** The text does not specify the learning rate, optimizer, batch size, number of epochs, or early stopping criteria. The hardware used for training is not mentioned.
- **Required correction** Provide complete training hyperparameters and hardware specifications.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data processing
- **Affected element** Input data preprocessing
- **Evidence pointer** Methods section, "Data" subsection
- **Issue** The text does not describe how the 1D epigenomic data were normalized or how the DNA sequence was encoded beyond "one-hot." The processing of CAGE data to generate target values is not described.
- **Required correction** Describe all data preprocessing steps, including normalization, filtering, and encoding.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Comparison completeness
- **Affected element** Baseline comparisons
- **Evidence pointer** Results section, Supplemental Figure S9
- **Concern** The comparison to Basenji is mentioned but not described in detail. It is unclear whether Basenji was retrained or used as a pre-trained model, and what input data were provided.
- **Required correction** Provide details on the Basenji comparison, including training procedure and input data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure references
- **Evidence pointer** Results section
- **Issue** The text frequently references supplemental figures without describing their content in the main text. This makes it difficult to follow the results without constantly switching to the supplement.
- **Required correction** Briefly describe the key findings shown in each referenced supplemental figure within the main text.

## Risk / unsupported claims
- The claim that GraphReg "more faithfully models gene regulation" is a strong interpretive statement not directly supported by the predictive performance metrics reported.
- The claim that GraphReg "represents an important advance" is subjective and not directly testable from the provided evidence.
- The claim that the model "accurately predicts direct TF targets" is based on a single validation approach (CRISPRi TF KO) and may not generalize to all TFs or cell types.
- The claim of "cell-type agnostic" Epi-GraphReg is not fully supported given the limited cross-cell-type testing.
- The statement that "the majority of genes have positive DeltaNLL" is presented without quantifying the proportion or assessing whether this proportion is significantly different from chance.
- The claim that GraphReg "is the most comprehensive and versatile model" among prior work is not systematically supported by comparisons to all relevant methods.