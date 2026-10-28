## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, methodological rigor, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present EPInformer, a transformer-based deep learning framework that integrates promoter and enhancer sequences with multimodal epigenomic signals (DNase, H3K27ac, Hi-C) to predict gene expression. They claim superior performance over existing models (Enformer, Borzoi, CREaTor, Seq-GraphReg, Xpresso) in cross-chromosome validation, accurate enhancer-gene interaction prioritization validated by CRISPR perturbation data, and identification of transcription factor motifs at enhancers.
- **Visible evidence base** Main text figures 1-4, supplementary figures 1-9, methods section, and references to supplementary tables and datasets
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; detailed hyperparameter settings; full ablation study results; statistical significance testing details; code availability statement; data availability statement

## Reviewer
- **Overall assessment** The manuscript presents a technically sound and potentially useful framework for gene expression prediction that integrates multiple data modalities. The architectural choices are well motivated, and the cross-chromosome validation strategy is rigorous. However, several concerns regarding the completeness of benchmarking, the interpretation of attention-based enhancer prioritization, and the generalizability of the approach need to be addressed. The work is of interest to the computational genomics community, though the incremental advance over existing methods should be more clearly delineated.

- **Who would be interested in the results, and why** Computational biologists and genomics researchers working on gene regulation prediction, enhancer-promoter interaction modeling, and deep learning applications in genomics. The framework's efficiency and flexibility may appeal to laboratories with limited computational resources. Researchers studying cis-regulatory elements and their role in gene expression would also find the interpretability aspects valuable.

- **Major strengths**
  1. The framework explicitly models promoter-enhancer interactions through a dedicated attention mechanism, addressing a key limitation of sequence-only models.
  2. The model is computationally efficient (0.4M parameters, ~1 hour training) compared to existing large models, making it accessible to a broader research community.
  3. The integration of multiple data modalities (sequence, epigenomics, chromatin contacts) in a flexible architecture is a thoughtful design choice.
  4. The cross-chromosome validation strategy is rigorous and addresses generalization concerns.
  5. The enhancer-gene interaction prioritization validated against CRISPR perturbation data provides functional relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "EPInformer outperforms existing gene expression prediction models in rigorous cross-chromosome validation"
- **Evidence pointer** Figure 2, Methods section "Baseline methods"
- **Concern** The benchmarking against Enformer and Borzoi uses their officially released pre-trained models with the original hold-out test sets, while EPInformer is trained and tested on these same splits. However, the comparison may be confounded by differences in training data composition, preprocessing pipelines, and the fact that Enformer and Borzoi were not retrained on the same data. The authors state that retraining these models requires substantial computational resources, but this creates an unfair comparison where EPInformer benefits from training on the test distribution.
- **Why it matters** The central claim of superior performance is the primary contribution of the manuscript. If the comparison is not apples-to-apples, the conclusion may not hold under more controlled conditions.
- **Resolution test** Provide additional benchmarking where Enformer and Borzoi are fine-tuned or retrained on the same training data as EPInformer, even if on a subset of chromosomes, to establish a fairer comparison. Alternatively, provide analysis showing that the performance gap persists when controlling for training data composition.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "EPInformer accurately prioritizes cell-type-specific enhancer-gene interactions validated by CRISPR perturbation experiments"
- **Evidence pointer** Figure 3, Methods section "Enhancer prioritization"
- **Concern** The attention-based scores are derived from the interaction encoder's attention weights, but the manuscript does not provide sufficient evidence that these attention weights are causally meaningful rather than reflecting spurious correlations. The comparison to ABC scores, while favorable, does not establish that the attention mechanism is learning genuine regulatory relationships. Additionally, the evaluation uses only 1,575 candidate enhancer-gene pairs from a single cell line (K562), which limits the generalizability of the claim.
- **Why it matters** The interpretability claim is a key differentiator of this work. If the attention weights do not reflect true regulatory interactions, the method's utility for hypothesis generation is diminished.
- **Resolution test** Provide additional validation in multiple cell lines, include negative controls (e.g., shuffled enhancer-gene assignments), and demonstrate that attention weights correlate with independent measures of enhancer activity or chromatin conformation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "EPInformer identifies crucial transcription factor motifs within regulatory sequences"
- **Evidence pointer** Figure 4, Methods section "Nucleotide contribution and motif discovery"
- **Concern** The motif discovery analysis identifies known and cell-type-specific transcription factor motifs, but the novelty of this finding is unclear. Many previous studies have identified similar motifs at enhancers using deep learning interpretability methods. The manuscript does not demonstrate that EPInformer's motif discovery provides new biological insights beyond what could be obtained with existing tools.
- **Why it matters** The biological interpretability claim is important for the broader impact of the work. Without demonstrating novel biological findings, this aspect of the manuscript is confirmatory rather than transformative.
- **Resolution test** Provide evidence that the motif discovery approach identifies novel regulatory motifs or provides new insights into cell-type-specific regulation that were not previously known. Alternatively, temper the claims to reflect the confirmatory nature of these findings.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "EPInformer can be trained on DNase-seq data alone or by integrating DNase-seq, H3K27ac ChIP-seq, and Hi-C contacts"
- **Evidence pointer** Results section, Supplementary Figures 4-5
- **Concern** The manuscript demonstrates the flexibility of the framework across different input modalities, but the ablation analysis appears incomplete. The specific contribution of each modality (sequence, epigenomics, Hi-C) to performance improvement is not systematically quantified. The authors mention that Hi-C provides marginal improvement, but the statistical significance of these differences is not reported.
- **Why it matters** Understanding the relative contribution of each data modality is important for users deciding which data to collect and integrate. Without this information, the practical guidance for applying EPInformer is incomplete.
- **Resolution test** Provide a systematic ablation study with statistical significance testing for each modality combination, and report the incremental contribution of each data type.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Model training and evaluation"
- **Evidence pointer** Methods section
- **Issue** The manuscript does not provide specific hyperparameter values for the interaction encoder (number of layers, hidden dimensions, dropout rates, etc.) beyond the general architecture description. The training details mention AdamW optimizer and learning rate, but other critical hyperparameters are missing.
- **Required correction** Provide a complete table of hyperparameters for all model variants, including the sequence encoder, interaction encoder, and predictor modules.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Baseline methods"
- **Evidence pointer** Methods section
- **Issue** The description of how Enformer and Borzoi predictions were obtained is insufficient. The authors state they used officially released pre-trained models, but do not specify the exact version, preprocessing steps, or how the input sequences were formatted for these models.
- **Required correction** Provide detailed instructions for reproducing the baseline predictions, including software versions, input formatting, and any post-processing steps.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 2, Results section
- **Evidence pointer** Figure 2
- **Issue** The performance comparisons report Pearson correlation coefficients but do not include confidence intervals or statistical significance tests. Given the cross-chromosome validation design, it should be possible to compute variance across folds.
- **Required correction** Report confidence intervals or standard deviations across validation folds, and perform statistical significance testing for the key performance comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3, Results section
- **Evidence pointer** Figure 3
- **Issue** The precision-recall curves in Figure 3b are described but the number of positive and negative examples in the CRISPR perturbation dataset is not stated. This information is critical for interpreting the AUPRC values.
- **Required correction** Report the number of positive and negative enhancer-gene pairs in the evaluation dataset, and discuss the class imbalance in the interpretation of AUPRC values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions future work on isoform-level expression prediction and integration of repressive histone modifications, but does not address potential limitations of the current approach, such as the reliance on candidate enhancer definitions from ABC or the handling of cell-type-specific Hi-C data availability.
- **Required correction** Add a paragraph discussing the limitations of the current framework, including the dependence on candidate enhancer identification and the impact of Hi-C data availability on model applicability.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (benchmarking fairness), R1-M2 (attention weight validation), R1-M3 (novelty of motif findings)

- **Assessment against Nature-style criteria**
  - Originality: Moderate. The integration of multimodal data in a transformer architecture for gene expression prediction is a reasonable extension of existing work, but the core ideas (attention mechanisms, multimodal integration) are not fundamentally novel.
  - Scientific importance: Moderate. Improved gene expression prediction and enhancer-gene interaction modeling are valuable contributions, but the incremental improvement over existing methods needs to be more clearly established.
  - Interdisciplinary readership: Moderate. The work will appeal to computational biologists and genomics researchers, but may have limited appeal beyond these fields.
  - Technical soundness: The cross-chromosome validation is rigorous, but concerns about benchmarking fairness and attention weight interpretation need to be addressed.
  - Readability for nonspecialists: The manuscript is generally well written and accessible, though some sections (e.g., model architecture) may be challenging for readers without deep learning expertise.

- **Recommendation posture** Supportive if technical concerns are resolved. The framework is potentially useful and the validation strategy is thoughtful, but the benchmarking fairness and interpretability claims need to be strengthened before the case is fully established.

## Risk / unsupported claims
- The claim that EPInformer "outperforms existing gene expression prediction models" is not fully supported due to potential benchmarking confounds (R1-M1).
- The claim that attention scores "accurately prioritize cell-type-specific enhancer-gene interactions" is not fully established without additional validation in multiple cell lines and negative controls (R1-M2).
- The claim that EPInformer "identifies crucial transcription factor motifs" is confirmatory rather than novel, and the biological significance of these findings is not demonstrated (R1-M3).
- The claim of "scalable" performance is not fully quantified; the manuscript mentions training time but does not provide scaling analysis with respect to genome size or number of genes.
- The generalizability of the approach to non-human genomes or disease-relevant cell types is not assessed.