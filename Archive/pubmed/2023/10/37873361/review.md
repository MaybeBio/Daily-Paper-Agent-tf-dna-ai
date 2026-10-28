## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the provided text; no external data or code were accessed
- **Shared manuscript claim summary** The authors present a neural network framework that jointly models DNA sequence and pre-existing chromatin features to predict the binding of five Forkhead transcription factors (FoxA1, FoxC1, FoxG1, FoxL2, FoxP3) ectopically expressed in mouse embryonic stem cells. They report that these Fox TFs bind distinct genomic sites despite similar in vitro motifs, that sequence alone does not explain differential binding, and that chromatin features differentially contribute to binding predictions across factors. They further report that FoxA1, FoxL2, and FoxC1 can engage relatively inaccessible chromatin, while FoxG1 and FoxP3 preferentially bind pre-existing accessible regulatory regions.
- **Visible evidence base** Main text figures (Figs 1–8), supplementary figures (S1–S14), tables (Tables 1–2, S1–S3), methods section, data availability statement
- **Missing materials affecting confidence** Supplementary figures and tables were referenced but not provided in the submitted text; code and data repositories were not accessed; no raw sequencing quality metrics or reproducibility benchmarks were included

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in transcription factor biology: how sequence preference and chromatin context jointly determine TF binding, and whether pioneer activity can be systematically compared across paralogs. The experimental design, using a common mES cell environment with inducible Fox TFs, is well conceived. The development of a joint sequence and chromatin CNN with attribution analysis is a methodological advance. However, the manuscript has several technical and interpretive gaps that currently limit the strength of the central claims. The evidence for differential chromatin engagement is largely correlative, the CNN improvement metrics are not statistically benchmarked, and the attribution analyses are not validated against independent perturbations. The manuscript would be substantially strengthened by additional controls, quantitative benchmarking, and clearer operational definitions of "pioneer ability."
- **Who would be interested in the results, and why** Researchers studying transcription factor binding mechanisms, chromatin biology, pioneer factors, and gene regulation. The methodological framework for integrating sequence and chromatin features via interpretable neural networks will also be of interest to computational biologists developing predictive models of TF occupancy. The comparative analysis across Fox paralogs has implications for understanding how TF families diversify regulatory functions during development.
- **Major strengths** 1) The experimental system is well designed: ectopic expression of five Fox TFs in a common mES chromatin environment allows direct comparison of binding behavior without confounding cell-type differences. 2) The integration of sequence and chromatin features in a single CNN architecture with attribution analysis is a principled and novel approach. 3) The study provides a rich resource of ChIP-exo, ATAC-seq, and RNA-seq data for five Fox TFs. 4) The finding that Fox TFs differ in their ability to engage inaccessible chromatin, despite similar DNA-binding domains, is biologically significant and challenges assumptions about uniform pioneer activity across the Forkhead family.
- **Major Concerns** 
  - **R1-M1** (Major, Blocking: Yes)
  - **R1-M2** (Major, Blocking: Yes)
  - **R1-M3** (Major, Blocking: No)
  - **R1-M4** (Major, Blocking: No)
  - **R1-M5** (Major, Blocking: No)
- **Minor Comments** 
  - **R1-m1** (Minor)
  - **R1-m2** (Minor)
  - **R1-m3** (Minor)
  - **R1-m4** (Minor)
  - **R1-m5** (Minor)
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2
- **Assessment against Nature-style criteria** 
  - **Originality** High. The joint sequence-chromatin CNN with attribution is a novel methodological contribution, and the comparative analysis of Fox paralog pioneer activity is a fresh angle on a well-studied family.
  - **Scientific importance** High. Understanding how TFs integrate sequence and chromatin information is fundamental to gene regulation. The finding that pioneer activity varies across Fox paralogs has implications for developmental biology and disease.
  - **Interdisciplinary readership** Moderate. The topic will appeal to molecular biologists, chromatin biologists, and computational biologists. The heavy reliance on neural network methodology may limit accessibility for some experimental readers.
  - **Technical soundness** Currently insufficient. The CNN performance improvements are not statistically benchmarked, the attribution analyses lack validation, and the chromatin engagement claims are not supported by direct chromatin accessibility measurements at binding sites.
  - **Readability for nonspecialists** Moderate. The manuscript is generally well written, but the CNN methodology and attribution analysis are described at a level that assumes computational expertise. The biological conclusions are clearly stated.
- **Recommendation posture** Supportive if technical concerns are resolved. The core question is important, the experimental design is strong, and the methodological framework is promising. However, the current evidence does not fully establish the central claims about differential chromatin engagement, and the CNN analyses require additional validation and benchmarking.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "adding pre-existing chromatin features to the CNN training process results in a substantial improvement in the ability to predict ChIP-exo read counts at held-out sites" (Results, section "Representation of Fox TF binding activities is improved by accounting for the pre-existing chromatin environment").
- **Evidence pointer** Figure 4B, Figure 4C, Figure S9, Figure S10; location not provided for specific metrics
- **Concern** The improvement in prediction performance when adding chromatin features is reported qualitatively ("substantial improvement") without quantitative metrics, confidence intervals, or statistical tests. The figure descriptions suggest correlation coefficients or similar metrics are shown, but no numerical values, error bars, or significance tests are presented in the text. It is unclear whether the improvement is consistent across all five Fox TFs, whether it is driven by a subset of factors, or whether it is statistically significant given the number of held-out sites.
- **Why it matters** The central methodological claim of the paper is that joint sequence and chromatin modeling improves prediction of TF binding. Without quantitative benchmarking, the reader cannot assess the magnitude or reliability of this improvement. This is critical because the subsequent attribution analyses and biological conclusions depend on the validity of the CNN models.
- **Resolution test** Provide quantitative performance metrics (e.g., Pearson or Spearman correlation, AUROC, or mean squared error) for both sequence-only and sequence+chromatin models, with confidence intervals and statistical significance tests (e.g., paired tests across held-out sites or bootstrap resampling). Report these metrics for each Fox TF individually and for the combined set. If the improvement is modest or inconsistent, discuss the implications for the interpretation of the attribution results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "using sequence and chromatin feature attribution techniques to interpret the neural network predictions, we show that differential sequence preferences combined with differential abilities to engage relatively inaccessible chromatin together explain Fox TF binding patterns at individual sites and genome-wide" (Abstract).
- **Evidence pointer** Figure 5, Figure 6, Figure S11, Figure S12; location not provided for attribution score distributions
- **Concern** The attribution analysis is used to make strong claims about the relative contributions of sequence and chromatin features to binding predictions. However, the attribution scores are not validated against independent experimental perturbations or known biological ground truth. For example, the claim that FoxG1 and FoxP3 CNNs use chromatin features to suppress binding predictions at FoxL2-preferred sites is based solely on attribution scores, with no experimental manipulation of chromatin state to confirm causality. Additionally, the attribution scores are presented as aggregate distributions or example loci, but no statistical comparison of attribution score distributions across clusters or TFs is provided.
- **Why it matters** Attribution methods are known to be sensitive to model architecture, training data, and the choice of baseline. Without validation, the attribution-based conclusions about differential chromatin engagement are not robustly supported. The biological claims about pioneer activity differences across Fox paralogs depend on these attribution results.
- **Resolution test** Validate attribution scores by (a) comparing attribution-based predictions to experimental perturbations (e.g., chromatin remodeling, nucleosome depletion) if available, or (b) performing in silico perturbation experiments where chromatin features are set to zero or shuffled and assessing the impact on predicted binding. Provide statistical comparisons of attribution score distributions across clusters and TFs, with appropriate multiple testing corrections. If validation is not possible, temper the claims and explicitly state the limitations of attribution-based inference.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence strength
- **Claim pointer** The authors claim that "FoxA1 causes a substantial increase in ATAC-seq signal at its binding sites, regardless of whether they were 'active' or 'inactive' in the pre-existing mES chromatin environment," while "FoxP3 and FoxG1 display little if any ability to cause an increase in accessibility at their binding sites" (Results, section "Differential Fox binding produces distinct impacts on chromatin and gene expression").
- **Evidence pointer** Figure 7A, Figure 7B; location not provided for statistical comparisons
- **Concern** The ATAC-seq analysis is used to support claims about differential pioneer activity. However, the comparison between Fox TF-induced accessibility changes and the null control is described qualitatively. It is unclear whether the differences between Fox TFs are statistically significant, whether the "inactive" site classification is robust, and whether the ATAC-seq signal changes are confounded by differences in binding site numbers or genomic context. The figure descriptions suggest aggregate plots, but no effect sizes, confidence intervals, or significance tests are reported.
- **Why it matters** The claim that FoxA1, FoxL2, and FoxC1 can open chromatin while FoxG1 and FoxP3 cannot is a key biological conclusion. Without statistical support, the reader cannot determine whether these differences are meaningful or within the range of experimental noise.
- **Resolution test** Provide quantitative ATAC-seq signal changes (e.g., mean fold change with confidence intervals) for each Fox TF at "active" and "inactive" binding sites, compared to the null control. Perform statistical tests (e.g., permutation tests or mixed-effects models) to assess whether the differences between Fox TFs are significant. If sample sizes are limited, discuss the power limitations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "the CNN uses early integration of input features to predict the quantitative ChIP enrichment signal at binding sites" and describe the architecture in the Methods.
- **Evidence pointer** Methods section "Convolutional neural network architecture and training"; Table 1; Table 2
- **Concern** The CNN architecture is described, but key training details are missing. The hyperparameter search is mentioned, but the search space, number of trials, and selection criteria are not fully specified. The number of training epochs, batch size, learning rate schedule, and early stopping criteria are not reported. The data splitting strategy (chromosome-level holdout) is described, but the number of positive and negative examples per TF is not stated. The code is available, but the manuscript does not provide a reproducibility statement or a containerized environment.
- **Why it matters** For a methodological contribution, reproducibility is essential. Without complete training details, other researchers cannot replicate the models or assess the robustness of the results. This is particularly important given the reliance on CNN predictions for biological conclusions.
- **Resolution test** Provide complete training details in the Methods or Supplementary Information, including hyperparameter search space, final hyperparameters, training epochs, batch size, learning rate, and data set sizes. Include a reproducibility statement with the software environment and dependencies. If possible, provide a Docker or Singularity container for the analysis pipeline.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive clarity
- **Claim pointer** The authors state that "the selected Fox TFs display a wide range of affinities for pre-existing chromatin states" and that "differential abilities to engage relatively inaccessible chromatin together explain Fox TF binding patterns" (Abstract, Results).
- **Evidence pointer** Figure 3, Figure 5, Figure 6; location not provided for operational definitions
- **Concern** The term "pioneer ability" or "ability to engage relatively inaccessible chromatin" is used throughout the manuscript, but no operational definition is provided. It is unclear whether this refers to binding at nucleosome-occupied sites, binding at sites lacking active histone marks, or binding at sites that become accessible upon TF expression. The chromatin state analysis (Fig 3) and the ATAC-seq analysis (Fig 7) are related but not integrated into a single quantitative measure of pioneer activity.
- **Why it matters** The central biological claim is that Fox TFs differ in pioneer activity. Without a clear, quantitative definition, the claim is difficult to evaluate or compare with other studies. The lack of a unified metric also makes it hard to assess whether the CNN attribution results and the ATAC-seq results are measuring the same phenomenon.
- **Resolution test** Provide an explicit operational definition of pioneer activity, such as the fraction of binding sites that are in "inactive" chromatin states, the change in ATAC-seq signal at binding sites, or a composite score. Apply this definition consistently across all analyses and discuss how it relates to established definitions in the field.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "intrinsic sequence preferences and extrinsic interactions with cell-specific chromatin landscapes" is somewhat vague. The term "extrinsic" could be misinterpreted as extracellular signals.
- **Required correction** Consider rephrasing to "intrinsic DNA sequence preferences and extrinsic factors such as cell-specific chromatin environments and interacting proteins."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, section "Fox paralogs bind to different sites when expressed in mES cells"
- **Evidence pointer** Figure 2A, Figure 2B
- **Issue** The clustering analysis that yields eight binding site clusters is described, but the criteria for choosing K=10 (later merged to 8) are subjective. The text states "K=10 was chosen by subjectively trying to minimize the number of small clusters while preserving interesting differences between clusters."
- **Required correction** Provide a more objective justification for the choice of K, such as a silhouette score or gap statistic, or acknowledge the subjectivity more explicitly and discuss the robustness of the conclusions to different K values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, section "Fox paralogs differentially associate with pre-existing chromatin features"
- **Evidence pointer** Figure 3A, Figure 3B
- **Issue** The ChromHMM analysis uses 15 states, but the state labels in Figure 3B are not fully defined in the text. The reader is left to infer what "Enh", "EnhPois", "Tss", etc. mean.
- **Required correction** Provide a table or supplementary figure that defines each ChromHMM state and the associated chromatin marks.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, section "ChIP-exo"
- **Evidence pointer** Methods, "ChIP-exo" paragraph
- **Issue** The ChIP-exo protocol is referenced, but the number of biological replicates for each Fox TF is not stated in the main text. The figure legends may contain this information, but it is not accessible in the provided text.
- **Required correction** State the number of biological replicates for each experiment in the Methods or Results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 2
- **Issue** The discussion of "assisted loading" and "pioneer activity" is interesting but somewhat speculative. The authors suggest that FoxG1 and FoxP3 may rely on pre-existing accessibility, but do not discuss alternative explanations, such as differences in nuclear mobility or protein stability.
- **Required correction** Briefly acknowledge alternative interpretations and discuss how the current data distinguish between them, or state that these alternatives cannot be excluded.

## Risk / unsupported claims
- The claim that "differential abilities to engage relatively inaccessible chromatin together explain Fox TF binding patterns" is not fully supported because the attribution analysis is not validated and the chromatin engagement is not directly measured.
- The claim that "FoxA1 causes a substantial increase in ATAC-seq signal at its binding sites" is not supported by statistical tests or effect sizes.
- The claim that "the selected Fox TFs display a wide range of affinities for pre-existing chromatin states" is based on correlative overlap analyses and is not quantified with confidence intervals.
- The claim that "sequence-only models do not fully capture the dynamic range of the data" is not quantified, and the improvement from adding chromatin features is not statistically benchmarked.
- The generalizability of the CNN framework to other TFs or cell types is asserted but not demonstrated.