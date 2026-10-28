## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplement descriptions)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and reproducibility as presented in the provided text
- **Shared manuscript claim summary** The authors present Mahi, a graph neural network framework that integrates multi-modal molecular features (chromatin accessibility, TF binding, histone modifications, protein structure) with tissue-specific functional networks to learn context-aware gene embeddings across 290 tissues and cell types. They claim superior performance over sequence-based models in predicting gene essentiality across 1,183 cancer cell lines, demonstrate that learned embeddings capture tissue-specific functional organization, and show that in silico gene knockout perturbations recover disease-relevant pathways.
- **Visible evidence base** Abstract, full introduction, full results section, full discussion, full methods, data/code availability statements, supplement table descriptions
- **Missing materials affecting confidence** Figures and supplementary figures (Figure 1-4, S1-S3) are referenced but not provided; Table S1-S3 contents not shown; no quantitative comparison data for baseline models in the visible text; no ablation studies; no hyperparameter sensitivity analyses; no validation of the in silico perturbation approach against experimental perturbation data

## Reviewer
- **Overall assessment** The manuscript presents a technically ambitious framework that addresses a genuine gap in context-aware gene function modeling. The core idea of integrating multi-modal molecular features with tissue-specific network topology through a GNN is sound and timely. However, the evidence provided in the text is insufficient to fully evaluate several key claims. The essentiality prediction results are reported as aggregate metrics without showing per-cell-line variability, baseline comparison details, or statistical significance beyond standard deviations. The in silico perturbation analysis, while conceptually interesting, lacks validation against experimental perturbation datasets, which is critical for establishing biological credibility. The tissue-specific functional organization claim relies on a single PCA-based dispersion metric without alternative validation. The manuscript would benefit from clearer reporting of model ablations, sensitivity analyses, and direct comparisons with more recent foundation models.

- **Who would be interested in the results, and why** Computational biologists developing gene function prediction methods, researchers in precision medicine and drug target discovery, and experimental biologists studying tissue-specific gene regulation. The framework's interpretability and public availability of embeddings could make it a useful resource for the broader functional genomics community.

- **Major strengths** The multi-modal integration strategy is well-conceived and addresses a real limitation of existing sequence-only approaches. The scale of the resource (290 tissues, 1,183 cell lines) is substantial. The in silico perturbation framework with tissue-resolved pathway analysis is a novel contribution. The authors are transparent about data sources and code availability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Mahi outperforms sequence-, expression-, and graph-based embeddings" in predicting gene essentiality
- **Evidence pointer** Results section "Mahi outperforms sequence-, expression-, and graph-based embeddings"; Figure 2C, 2D
- **Concern** The comparison against baseline models is described only qualitatively ("significantly outperformed") without reporting actual performance numbers for the baselines. The text states Mahi achieves ROCAUC = 0.921 ± 0.012, but no corresponding metrics for DeepSEA, ESM-C, Borzoi, scGPT, or node2vec are provided in the visible text. Without these numbers, the claimed superiority cannot be assessed. Additionally, the choice of gradient-boosted trees as the downstream predictor for all embeddings may favor certain embedding types, and this potential bias is not discussed.
- **Why it matters** The central claim of the paper is that multi-modal tissue-aware integration provides advantages over existing approaches. Without quantitative baseline comparisons, this claim is unverifiable from the provided material.
- **Resolution test** Provide a table with mean and standard deviation of ROCAUC and PRAUC for all baseline models across the 1,183 cell lines, along with paired statistical test results. Discuss potential biases in the downstream model choice.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "Mahi supports in silico gene perturbation experiments, which produce interpretable tissue- and cell-type-resolved exploration of context-dependent network rewiring and disease-relevant pathways"
- **Evidence pointer** Results section "Mahi provides an interpretable framework for modeling context-specific perturbation responses"; Figure 4
- **Concern** The in silico knockout approach is described as removing a gene and its edges, then re-running the pretrained model. However, no validation is presented against experimental perturbation data (e.g., CRISPR screens, expression perturbation datasets). The pathway enrichments for ALPK3, DMD, and CFTR are biologically plausible, but plausibility is not evidence of predictive validity. The method could be systematically biased toward recovering well-known pathways regardless of actual perturbation effects.
- **Why it matters** The perturbation modeling capability is a major claimed contribution with potential therapeutic applications. Without validation against ground truth perturbation outcomes, the biological utility of this approach remains speculative.
- **Resolution test** Validate in silico perturbation predictions against experimental perturbation datasets (e.g., LINCS L1000, CRISPR perturbation screens with transcriptomic readouts). Report correlation between predicted embedding shifts and observed expression changes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "Mahi embeddings capture tissue-specific functional organization, with genes forming distinct clusters reflecting their context-dependent roles"
- **Evidence pointer** Results section "Mahi embeddings capture tissue-specific gene functionality"; Figure 3
- **Concern** The evidence for tissue-specific functional organization relies on PCA visualization and convex hull area comparisons between tissue-elevated and housekeeping genes. This is a weak form of validation. PCA on high-dimensional embeddings can produce apparent clustering that reflects technical artifacts rather than biology. The convex hull metric is sensitive to outlier genes and sample size. No alternative validation (e.g., correlation with known tissue-specific pathway activity, comparison with expression-based tissue specificity) is provided.
- **Why it matters** The claim that embeddings encode meaningful tissue-specific biology is foundational to the framework's utility. Weak validation undermines confidence in downstream applications.
- **Resolution test** Provide additional validation: correlation of embedding distances with tissue-specific expression specificity indices, enrichment of known tissue-specific transcription factor targets in cluster neighborhoods, or comparison with alternative embedding methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "Mahi is a scalable and interpretable graph neural network framework"
- **Evidence pointer** Methods section "Mahi Framework"
- **Concern** The methods section contains incomplete equations (the TransformerConv layer equation and the MLP equation are referenced but not fully written out in the provided text). Hyperparameter optimization is described but the final hyperparameter values are not reported. The number of parameters, training time, and computational resources required are not stated. The GitHub repository is mentioned but its contents cannot be verified from the manuscript.
- **Why it matters** Reproducibility is a core requirement for computational methods papers. Incomplete methodological details prevent independent implementation and evaluation.
- **Resolution test** Complete the equations, report final hyperparameters, training details, and computational requirements. Ensure the GitHub repository contains all code, pretrained models, and documentation needed for reproduction.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "290 tissues and cell-types" but the methods describe pretraining on 35 core tissues. The relationship between these numbers and how the remaining 255 tissues are handled is unclear.
- **Required correction** Clarify whether the 35 tissues are a subset used for pretraining and the full 290 are used for downstream tasks, or if all 290 are used throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Essentiality prediction evaluation
- **Evidence pointer** Results section "Mahi accurately predicts cell-line-specific gene essentiality"
- **Issue** The text reports mean ROCAUC and PRAUC across cell lines but does not describe the distribution of these metrics. Given the heterogeneity of cancer cell lines, some cell lines may perform much worse than others.
- **Required correction** Report the range, interquartile range, or show a distribution plot of performance across the 1,183 cell lines.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Baseline descriptions
- **Evidence pointer** Results section "Mahi outperforms sequence-, expression-, and graph-based embeddings"
- **Issue** The text mentions comparisons with scGPT and node2vec but does not describe how these embeddings were generated for the genes in the study (e.g., which scGPT model version, what training data, what node features for node2vec).
- **Required correction** Provide details on how each baseline embedding was generated, including model versions and preprocessing steps.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** CFTR perturbation analysis
- **Evidence pointer** Results section "Mahi reveals how genetic perturbations drive distinct, tissue-specific pathways across context"
- **Issue** The text describes pathway enrichments in reproductive tissues following CFTR perturbation but does not provide quantitative measures of enrichment significance or effect sizes.
- **Required correction** Report enrichment p-values, fold enrichments, and gene counts for the key pathways mentioned.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** APPNP propagation
- **Evidence pointer** Methods section "Mahi Framework"
- **Issue** The grid search over k and alpha is described, but the selection criterion for "optimal balance" is not specified. It is unclear whether this was based on downstream task performance or a separate validation metric.
- **Required correction** Specify the selection criterion used for choosing k = 8 and alpha = 0.6.

## Risk / unsupported claims
- The claim that Mahi "significantly outperformed" all baseline models is unsupported without quantitative comparison data in the visible text
- The biological validity of in silico perturbation predictions is unverified without comparison to experimental perturbation data
- The claim that embeddings "recapitulate known tissue-specific organization" is weakly supported by a single PCA-based metric
- The scalability claim is not supported by any runtime or resource measurements
- The interpretability claim is asserted but not demonstrated with specific examples of interpretable features
- The generalizability of the framework to new tissues or cell types not in the 290 is not addressed
- The statement that "Mahi could be expanded for perturbation modeling across a broader range of biological contexts" is speculative and not evidence-based
- The relationship between the 35 pretraining tissues and the full 290 tissues is not clearly explained, creating ambiguity about the framework's actual coverage