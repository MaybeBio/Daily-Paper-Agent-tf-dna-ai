## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided
- **Assessment boundary** Scientific and technical evaluation of the manuscript as submitted; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors present GRNFormer, a graph transformer framework for gene regulatory network inference from single-cell or bulk transcriptomic data. The method combines a transformer-based gene expression encoder (Gene-Transcoder) with a variational graph autoencoder (GraViTAE) using pairwise attention, and a transcription factor-anchored subgraph sampling strategy (TF-Walker). The authors claim state-of-the-art performance on BEELINE benchmarks, cross-species generalization to DREAM5 bulk datasets, and robust recovery of known and novel regulatory modules in human embryonic stem cells and peripheral blood mononuclear cells.
- **Visible evidence base** Main text including Methods sections 2.1-2.9, Results sections 3.1-3.6, Tables 1-2 referenced, Figures 1-4 referenced, supplementary sections referenced (Methods S1-S11, Results S1-S7, Figures S1-S16, Tables S1-S6)
- **Missing materials affecting confidence** Supplementary figures and tables not provided; detailed algorithm pseudocode not provided; hyperparameter settings not fully specified; statistical significance testing not reported; comparison method implementation details not fully described

## Reviewer
- **Overall assessment** The manuscript presents a technically sophisticated architecture that combines several established ideas in a novel configuration for GRN inference. The core claims of high accuracy and cross-species generalization are supported by the reported metrics, but several methodological details and evaluation choices require clarification before the case is fully established. The most significant concerns relate to the fairness of the benchmark comparison, the potential for information leakage in the evaluation protocol, and the lack of statistical significance testing.
- **Who would be interested in the results, and why** Computational biologists developing or applying GRN inference methods; researchers working with single-cell transcriptomics who need network inference tools; machine learning researchers interested in graph transformers and variational autoencoders applied to biological data. The cross-species and cross-modality generalization claims would be of interest to a broad audience in regulatory genomics.
- **Major strengths** The architecture is well-motivated and integrates biologically informed design choices (TF-centered sampling, edge-aware attention, variational regularization). The evaluation spans multiple benchmarks, species, and data modalities, which is commendable. The zero-shot evaluation on PBMC data without cell type labels is a strong test of practical utility. The computational efficiency analysis is useful for practitioners.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evaluation fairness
- **Claim pointer** The manuscript claims GRNFormer "outperforms existing traditional and deep learning state-of-the-art methods in blind evaluations" and that it "surpasses all SOTA methods-including GNE-on the majority of datasets."
- **Evidence pointer** Section 3.2, Figure 3, Results S1
- **Concern** The comparison protocol is asymmetric. GRNFormer is trained on five cell types and tested on two held-out cell types, while competing deep learning methods are trained and evaluated on within-dataset splits of each test cell type. This means competing methods see test cell type data during training, which could either advantage them (more relevant training data) or disadvantage them (less diverse training data). The manuscript does not justify why this asymmetric protocol is fair, nor does it report results for GRNFormer under the same within-dataset training protocol as the competitors. Without this control, the claimed superiority is not cleanly attributable to the model architecture.
- **Why it matters** The central claim of the paper is that GRNFormer achieves state-of-the-art performance. If the comparison protocol is not matched across methods, the performance differences could reflect training data composition rather than model quality. This directly affects the validity of the main conclusion.
- **Resolution test** Report GRNFormer results under the same within-dataset training protocol used for competing methods, and report competing method results under the cross-dataset protocol. If GRNFormer still achieves superior or comparable performance under matched protocols, the claim is strengthened. Alternatively, provide a clear justification for why the asymmetric protocol is the appropriate comparison.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Information leakage
- **Claim pointer** The manuscript states that "localized z-score normalization across genes for each cell in every subgraph" prevents information leakage by "preventing memorization of gene identities/patterns across subgraphs."
- **Evidence pointer** Section 2.3, Section 2.9
- **Concern** The normalization strategy is described as preventing leakage, but the mechanism is not fully convincing. If the same genes appear across training and test subgraphs (which the manuscript acknowledges: "individual genes may appear in both phases"), the model could learn gene-specific biases during training that transfer to test subgraphs containing those same genes. The z-score normalization is applied within each subgraph, but the model still sees the same gene identities across train and test. The manuscript does not demonstrate that the normalization fully eliminates this potential leakage pathway.
- **Why it matters** If gene identity information leaks from training to test, the reported performance on held-out cell types may be optimistically biased. This would undermine the generalization claims.
- **Resolution test** Perform an ablation where gene identities are masked or permuted between training and test subgraphs, and show that performance degrades to chance levels. Alternatively, demonstrate that the model cannot distinguish gene identities from the normalized expression patterns alone.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports performance metrics (Sampled_AUROC, Sampled_AUPRC, Full test-set AUROC/AUPRC, F1, precision, recall) across multiple datasets and methods.
- **Evidence pointer** Section 3.1, Section 3.2, Tables 2, S1, S2, Figures 3, S7-S11
- **Concern** No statistical significance testing is reported. The manuscript states GRNFormer "consistently achieves the highest or near-highest performance" and "significantly outperforms" competitors, but no confidence intervals, standard deviations across runs, or hypothesis tests are provided. Given that bootstrapped negative sampling is used, it would be straightforward to compute variance estimates across bootstrap iterations.
- **Why it matters** Without measures of variability, the reader cannot assess whether observed performance differences are meaningful or within the range of random variation. This is particularly important given the asymmetric evaluation protocol described in R1-M1.
- **Resolution test** Report mean and standard deviation (or confidence intervals) across bootstrap iterations for all metrics, and perform paired statistical tests (e.g., Wilcoxon signed-rank) comparing GRNFormer to each competitor across datasets.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological detail
- **Claim pointer** The manuscript describes the TF-Walker strategy as "a transcription factor-anchored subgraph sampling approach" and states that during inference it "deterministically extends to all available neighbors of a given TF."
- **Evidence pointer** Section 2.2, Section 2.9, Methods S2, S7
- **Concern** The description of TF-Walker is incomplete. The manuscript does not specify how TFs are identified in the input data (e.g., from a predefined list, from annotation, or learned), how the hop expansion is bounded during training, what happens when a TF has fewer than 99 neighbors, or how overlapping subgraphs are reconciled during aggregation. The distinction between training (random sampling of 99 neighbors) and inference (deterministic full expansion) is described, but the implications for train-test distribution shift are not discussed.
- **Why it matters** The TF-Walker strategy is a core contribution of the paper. Without a complete specification, the method cannot be reproduced or properly evaluated by others. The train-inference distribution shift could also affect performance in ways that are not currently addressed.
- **Resolution test** Provide a complete algorithmic specification of TF-Walker, including TF identification, hop expansion bounds, handling of low-degree TFs, and subgraph aggregation. Discuss the potential impact of the train-inference distribution shift and provide empirical evidence that it does not degrade performance.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** The manuscript claims GRNFormer "robustly recovers both known and novel regulatory networks, including pluripotency circuits in human embryonic stem cells (hESCs) and immune cell modules in peripheral blood mononuclear cells (PBMCs)."
- **Evidence pointer** Section 3.6, Figures 4A-B, S14-S16
- **Concern** The case studies are presented as evidence of biological validity, but the evaluation is largely qualitative. The manuscript shows that known regulators (POU5F1, SOX2, NANOG, MYC) appear as central nodes and that a novel module is enriched for developmental pathways, but no quantitative comparison to established regulatory networks is provided. For the PBMC analysis, no comparison to known immune cell type markers or regulatory circuits is shown beyond listing a few genes.
- **Why it matters** The claim of recovering "biologically meaningful" networks is a key part of the paper's significance. Without quantitative benchmarks against known regulatory interactions (e.g., using databases like TRRUST, RegNetwork, or ENCODE), the biological validity claim is not fully supported.
- **Resolution test** Provide quantitative overlap statistics between predicted networks and known regulatory interactions (e.g., precision at top-k predictions against curated databases). For the PBMC analysis, compare predicted cell-type-specific modules to known marker gene regulatory circuits.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Baseline completeness
- **Claim pointer** The manuscript compares GRNFormer against "existing traditional and deep learning state-of-the-art methods" including CNNC, GNE, GNNLink, STGRNS, scGREAT, LEAP, PIDC, PPCOR, and SINCERITIES.
- **Evidence pointer** Section 3.2, Table S2, Methods S9
- **Concern** The list of baselines is reasonable but incomplete. Recent methods such as GRNBoost2, SCENIC, CellOracle, and DeepSEM are not included. More importantly, the manuscript does not report results for a simple correlation-based baseline (e.g., Pearson correlation on the same data), which would establish a lower bound for what the deep learning methods add. The choice of hyperparameters for each baseline method is not described.
- **Why it matters** Without a comprehensive baseline set, the claim of state-of-the-art performance is not fully established. A simple baseline would help contextualize the absolute performance levels.
- **Resolution test** Add a correlation-based baseline and at least one additional recent GRN inference method. Report hyperparameter choices for all baselines and justify the selection of baselines.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, equation for pairwise attention
- **Evidence pointer** Section 2.5, equation (1)
- **Issue** The pairwise attention coefficient equation is presented without defining all symbols clearly. The relationship between the attention mechanism and the edge features is not fully explained.
- **Required correction** Define all symbols in the equation and provide a brief explanation of how edge features modulate the attention computation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.8, training details
- **Evidence pointer** Section 2.8, Table 1
- **Issue** The manuscript states training was performed on "two GPUs of NVIDIA A10" but does not report training time, number of parameters, or convergence criteria. The beta value for KL regularization is described as "e.g., 0.01 or 1/#genes in subgraph" without specifying which was used.
- **Required correction** Report the exact beta value used, training time, model size, and convergence criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.5, scalability results
- **Evidence pointer** Section 3.5, Figure 4C
- **Issue** The scalability analysis reports inference time and memory usage but does not report training time or memory usage, which is also relevant for practical utility.
- **Required correction** Report training time and memory usage for the largest datasets.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.4, DREAM5 results
- **Evidence pointer** Section 3.4, Results S3, Figure S12
- **Issue** The manuscript reports Sampled_AUROC and Sampled_AUPRC for DREAM5 but does not report Full test-set metrics for these datasets. The relationship between sampled and full metrics is not explained.
- **Required correction** Report both sampled and full test-set metrics for DREAM5, or explain why only sampled metrics are reported.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.7.2, PBMC dataset
- **Evidence pointer** Section 2.7.2
- **Issue** The PBMC dataset description is minimal. The manuscript does not specify the number of cells, number of genes, or how the data were preprocessed beyond stating it was "obtained in preprocessed form via the Scanpy toolkit."
- **Required correction** Provide details on the PBMC dataset size, preprocessing steps, and quality control measures.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Abstract, "Availability and implementation" section
- **Evidence pointer** Abstract, Availability section
- **Issue** The abstract states "National Sscience Foundation" in the funding section, which appears to be a typo for "National Science Foundation."
- **Required correction** Correct the typo.

## Risk / unsupported claims
- The claim that GRNFormer "establishes GRNFormer as a robust and transferable tool for network biology" is not fully supported given the concerns about evaluation fairness (R1-M1) and potential information leakage (R1-M2).
- The claim of recovering "novel regulatory networks" in hESCs is not quantitatively validated against known regulatory databases.
- The claim that the model "can be applied across diverse species, cell types, and contexts without retraining" is supported only by the DREAM5 zero-shot results, which are limited to two microbial species and do not include full test-set metrics.
- The statement that "the model was trained without any explicit knowledge of species, cell type, or regulatory context" is not verifiable from the provided text, as the training data composition and any implicit biases are not fully described.
- The claim that "TF-Walker effectively localizes transcriptional context" is based on ablation results that are only summarized in supplementary material not provided for review.