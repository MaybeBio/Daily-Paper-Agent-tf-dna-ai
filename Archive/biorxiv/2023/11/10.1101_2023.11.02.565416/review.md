## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability, and supplementary figure/table references)
- **Assessment boundary** Scientific claims, methodology, experimental design, and evidence quality as presented in the provided text
- **Shared manuscript claim summary** The authors present TRAFICA, a transformer-encoder based language model pre-trained on ATAC-seq derived open chromatin sequences and fine-tuned on in vitro TF-DNA binding affinity data (PBM and HT-SELEX), which they claim outperforms existing machine learning and deep learning tools in predicting both in vitro and in vivo TF-DNA binding affinity.
- **Visible evidence base** Results sections 2.2 through 2.5 with associated figures (Figures 3, 4, 5), methods sections 4.1 through 4.5, and references to supplementary materials (Tables S1-S8, Figures S1-S13, Notes 1-6)
- **Missing materials affecting confidence** Figures 1-6 are referenced but not provided in the text; supplementary tables and figures are referenced but not available; detailed hyperparameter settings for the model are only partially described; the exact composition and preprocessing of the ATAC-seq dataset beyond the number of sequences is not fully specified; details of the comparison tool training protocols are deferred to Supplementary Note 6

## Reviewer

- **Overall assessment** The manuscript addresses a relevant problem in computational genomics, namely the integration of chromatin accessibility information into TF-DNA binding affinity prediction. The core idea of pre-training a language model on open chromatin sequences is conceptually reasonable and the reported performance improvements are notable. However, the manuscript as presented has several significant gaps in methodological detail and evidence transparency that prevent full evaluation of the claims. The reliance on supplementary materials for critical information, the absence of key statistical details, and the lack of clarity on certain experimental choices weaken the current presentation. The work has potential but requires substantial revision and additional analysis to fully support its claims.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on transcription factor binding prediction, regulatory genomics, and deep learning applications in genomics would be the primary audience. Researchers developing or using sequence-based models for gene regulation prediction would find the approach of integrating open chromatin information relevant. The work may also interest experimental biologists who use computational predictions to prioritize TF binding sites for validation.

- **Major strengths** The manuscript addresses a genuine gap in existing TF-DNA binding affinity prediction tools by incorporating open chromatin context, which is biologically well motivated. The use of a large-scale ATAC-seq dataset (over 13 million sequences) for pre-training is a substantial resource. The evaluation across multiple datasets (PBM, HT-SELEX, ChIP-seq) and comparison with several existing tools provides a reasonably broad assessment. The ablation study on the pre-training stage helps isolate the contribution of the proposed approach. The cross-technology generalization experiment (HT-SELEX fine-tuning to PBM testing) is a valuable addition.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that TRAFICA significantly outperforms existing tools in predicting in vitro TF-DNA binding affinity on DREAM5 PBM datasets (average PCC=0.649 vs. 0.433 for DNAffinity, p-value<1e-12).
- **Evidence pointer** Section 2.2, Figure 3A
- **Concern** The evaluation protocol for the DREAM5 PBM datasets is described as a cross-microrray design where the model is fine-tuned on one microarray and tested on the other. However, the manuscript does not specify how hyperparameter selection was performed during fine-tuning, whether the test set was used for early stopping or model selection, or how the comparison tools were optimized. If hyperparameters were selected based on test set performance, the reported PCC values could be optimistically biased. Additionally, the statistical test used to compute the p-value is not described, and it is unclear whether the comparison accounts for the paired nature of the data across TFs.
- **Why it matters** The central claim of superior performance rests on this comparison. Without a clearly described and unbiased evaluation protocol, the reported improvements cannot be reliably interpreted. The lack of statistical detail prevents assessment of whether the observed differences are robust.
- **Resolution test** Provide a detailed description of the hyperparameter selection procedure, explicitly state that the test set was not used for any model selection decisions, describe the statistical test used for significance testing, and report confidence intervals for the PCC values.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that TRAFICA substantially outperforms existing tools on HT-SELEX datasets with average R2 values of 0.973 (Jolma et al.), 0.987 (Yang et al.), and 0.957 (Yin et al.).
- **Evidence pointer** Section 2.3, Figure 4A
- **Concern** The R2 values reported are extremely high, approaching the theoretical maximum. This raises the question of whether the evaluation protocol is sufficiently challenging. The manuscript states that sequences were split into 80% fine-tuning and 20% test sets from the same dataset. If the test sequences are highly similar to training sequences (e.g., near-duplicates or sequences sharing long common substrings), the evaluation may reflect memorization rather than generalization. The manuscript does not report sequence identity thresholds between training and test sets, nor does it describe any redundancy reduction step. Additionally, the comparison with other tools under the same protocol is described, but the details of how those tools were trained and tuned are deferred to supplementary material.
- **Why it matters** If the test set is not sufficiently disjoint from the training set, the reported performance does not reflect true predictive ability on new sequences. The near-perfect R2 values warrant scrutiny of the evaluation design.
- **Resolution test** Report sequence similarity statistics between training and test sets, describe any redundancy filtering applied, and provide the comparison tool training details in the main text or clearly state where they can be found. Consider evaluating on a more challenging split, such as by sequence family or motif occurrence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that TRAFICA was pre-trained on 13,013,152 genomic sequences from open chromatin regions defined by peaks in 422 ATAC-seq experiments from the ENCODE project.
- **Evidence pointer** Section 2.1, Section 4.1, Figure 1A
- **Concern** The description of the ATAC-seq dataset construction is incomplete. The manuscript does not specify the criteria for selecting the 422 experiments, the peak calling parameters used, the length of sequences extracted (beyond "100bps upstream and downstream flanking regions"), whether overlapping peaks were merged, or how the final set of 13,013,152 sequences was deduplicated. The threshold of -log10(p-value) >= 100 for "high confidence" peaks is unusually stringent and its justification is not provided. These details are essential for reproducing the pre-training dataset.
- **Why it matters** The pre-training data is a core component of the proposed method. Without a complete description of how it was constructed, other researchers cannot reproduce the work or assess potential biases in the data.
- **Resolution test** Provide a complete description of the ATAC-seq data processing pipeline, including experiment selection criteria, peak calling parameters, sequence extraction and filtering steps, and the rationale for the significance threshold.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that considering open chromatin characteristics significantly improves TF-DNA binding affinity prediction, particularly when limited TF-DNA binding profiles are available.
- **Evidence pointer** Section 2.5, Figure 5B
- **Concern** The in vivo evaluation on ChIP-seq datasets is presented as evidence for the utility of the open chromatin pre-training. However, the manuscript does not describe how the ChIP-seq datasets were processed, how positive and negative sets were defined, or how the comparison tools were adapted for binary classification. The improvement in AUROC is reported as 0.13 from the ablation study, but the baseline AUROC values are not reported in the text. Without this context, the practical significance of the improvement is unclear.
- **Why it matters** The claim that open chromatin information improves in vivo prediction is a key contribution of the work. The current presentation does not allow the reader to assess the magnitude of the effect in context.
- **Resolution test** Report the baseline and ablated AUROC values, describe the ChIP-seq data processing and labeling scheme, and provide the full evaluation protocol for the in vivo experiments.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that the pre-training stage significantly improved performance, with average PCC rising from 0.526 to 0.649 (p-value<1e-5) on DREAM5 PBM datasets.
- **Evidence pointer** Section 2.2, Figure 3C
- **Concern** The ablation study compares the full model with a version without pre-training. However, the manuscript does not specify whether the non-pre-trained model had the same architecture, training budget, and hyperparameter tuning as the pre-trained model. If the non-pre-trained model was not given sufficient training iterations or optimal hyperparameters, the comparison may be unfair. Additionally, the p-value is reported without describing the statistical test used.
- **Why it matters** The ablation study is intended to isolate the contribution of pre-training. An unfair comparison would overstate the benefit of the pre-training stage.
- **Resolution test** Describe the training protocol for the ablated model, including number of iterations, learning rate schedule, and hyperparameter selection. Specify the statistical test used for the p-value.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that TRAFICA was evaluated on in vitro and in vivo datasets, but the specific performance metrics and the magnitude of improvements are not mentioned. The abstract would benefit from including key quantitative results.
- **Required correction** Include the main performance numbers (e.g., average PCC, R2, AUROC) and the names of the best-performing comparison tools in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.3
- **Evidence pointer** Section 4.3
- **Issue** The loss function for pre-training is described with an equation, but the equation itself is not rendered in the provided text. The description of the masking strategy is clear, but the exact formulation of the cross-entropy loss cannot be verified.
- **Required correction** Ensure the loss function equation is properly displayed and defined in the final version.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3, Figure 4B
- **Issue** The sampling procedure for generating subsets of 10,000 to 50,000 sequences is described, but the number of replicates for each sampling is not stated. It is unclear whether the reported R2 values are from a single run or averaged over multiple runs.
- **Required correction** State the number of replicate samplings and report the variance or standard deviation of the performance metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.6
- **Evidence pointer** Section 2.6, Figure 6
- **Issue** The motif analysis reports that 249 TFs from 362 TF-motif pairs matched validated motifs in JASPAR2022. The criteria for a "match" are not described, and the MoSBAT-e score threshold for considering a match is not stated.
- **Required correction** Describe the matching criteria and the score threshold used to determine a valid match.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.1
- **Evidence pointer** Section 4.1
- **Issue** The description of the ChIP-seq dataset incorporation states it was "from DeepBind" but does not specify the number of ChIP-seq datasets, the cell types, or the processing steps applied.
- **Required correction** Provide details on the ChIP-seq datasets used, including the number of datasets, cell types, and any preprocessing applied.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2, Figure 3B
- **Issue** The manuscript notes that predictive performance varies substantially across TFs, even within the same families. This observation is mentioned but not analyzed further. A discussion of which TFs or families show the largest improvements or failures would strengthen the manuscript.
- **Required correction** Add a brief analysis of performance variation across TF families, highlighting cases where the model performs particularly well or poorly.

- **Technical failings that need to be addressed before the case is established** R1-M1 (evaluation protocol transparency), R1-M2 (potential data leakage in HT-SELEX evaluation), R1-M3 (incomplete dataset description for reproducibility)

- **Assessment against Nature-style criteria** 
  - Originality: The concept of pre-training a language model on open chromatin sequences for TF binding affinity prediction is a novel combination of existing ideas. The use of ATAC-seq data as a pre-training corpus is not commonly explored in this context. However, the underlying architecture (transformer-encoder) and the fine-tuning approach are well-established, so the originality lies primarily in the application rather than the methodology.
  - Scientific importance: Accurate TF binding prediction is important for understanding gene regulation. The potential improvement in low-data regimes, as suggested by the in vivo results, could be practically valuable. However, the importance of the specific contribution needs to be better contextualized against existing benchmarks and the magnitude of improvement needs to be more clearly demonstrated.
  - Interdisciplinary readership: The work sits at the intersection of machine learning and genomics. The writing is generally accessible to computational biologists, but the manuscript assumes familiarity with both transformer architectures and TF binding assays. The broader biological significance could be communicated more effectively to a general readership.
  - Technical soundness: The core methodology is reasonable, but the evaluation protocols have transparency issues that need to be resolved. The extremely high R2 values on HT-SELEX datasets raise questions about the difficulty of the evaluation task. The statistical reporting is incomplete in several places.
  - Readability for nonspecialists: The manuscript is structured clearly, but the introduction and discussion assume significant background knowledge. The abstract is accessible, but the results sections would be challenging for readers without prior exposure to TF binding prediction methods.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the reported results are potentially interesting, but the current manuscript does not provide sufficient methodological detail and evaluation transparency to fully assess the claims. The authors should address the major concerns regarding evaluation protocol, data leakage potential, and dataset description before the case for the method's superiority can be considered established.

## Risk / unsupported claims
- The claim that TRAFICA "significantly outperformed" existing tools is not fully supported without a description of the statistical tests used and the variance in the performance metrics.
- The claim that open chromatin pre-training improves in vivo prediction is based on an ablation study where the baseline AUROC values are not reported.
- The claim of robustness with small fine-tuning datasets is presented in Figure 4B, but the specific thresholds for "small" and the practical implications are not discussed in the text.
- The statement that DNA shape features "may not consistently improve" prediction is based on a null comparison between CRPT and CRPTS, but the statistical power of this comparison is not discussed.
- The generalizability claim across assay technologies (Section 2.4) is based on a single cross-technology experiment with 86 datasets, and the limitations of this comparison are not addressed.