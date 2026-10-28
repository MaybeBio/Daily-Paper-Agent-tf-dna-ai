## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided text. No code execution or independent data verification performed.
- **Shared manuscript claim summary** The authors present TRAFICA, a Transformer-based language model pretrained on open chromatin sequences from ATAC-seq data and fine-tuned on in vitro TF–DNA binding affinity data (PBM, HT-SELEX) using LoRA. They claim state-of-the-art performance in predicting both in vitro and in vivo TF–DNA binding affinity, outperforming existing tools and DNA language models, and demonstrate that incorporating open chromatin sequence characteristics improves prediction.
- **Visible evidence base** Main text figures referenced (Fig. 1A–C, Fig. 2A–D, Fig. 3A–J, Fig. 4A–B), supplementary tables (Tables 1–9), supplementary notes (Notes 1–7), and data availability URLs. No actual figures, tables, or supplementary files were provided for inspection.
- **Missing materials affecting confidence** All figures, tables, and supplementary notes are referenced but not included. Exact hyperparameters for fine-tuning, evaluation metrics definitions, statistical test details, and the full results of ablation studies are not fully specified in the text. The GitHub repository and HuggingFace model collections were not accessed.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely problem in computational genomics: improving TF–DNA binding affinity prediction by incorporating in vivo chromatin accessibility context. The core idea of pretraining a language model on ATAC-seq-derived open chromatin sequences is conceptually sound and potentially impactful. However, the current manuscript, as provided, lacks sufficient detail in several critical areas to fully assess the validity and generalizability of the claims. The evaluation methodology, particularly for the in vivo ChIP-seq prediction task, requires more rigorous description and justification. The comparison with existing tools and DNA language models is presented, but the fairness and completeness of these comparisons are not fully verifiable without the supplementary materials. The manuscript is well-written and the logic is clear, but the evidence base is incomplete for a definitive assessment.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing and applying deep learning models for gene regulation. Researchers studying transcription factor binding mechanisms, particularly those interested in integrating in vitro and in vivo data. The broader genomics community interested in the application of large language models to non-coding DNA sequences.
- **Major strengths**
    1.  **Novel and relevant concept**: The idea of pretraining a model on open chromatin regions to capture in vivo TF binding context is a logical and potentially powerful extension of existing approaches that rely solely on in vitro data.
    2.  **Comprehensive evaluation framework**: The authors evaluate their model across multiple paradigms (PBM, HT-SELEX, ChIP-seq) and against a wide range of baselines, including classic machine learning, deep learning, and large DNA language models.
    3.  **Practical considerations**: The use of LoRA for efficient fine-tuning and the exploration of different tokenization strategies (k-mer, BPE) are practical and valuable contributions.
    4.  **Interpretability analysis**: The attention-based motif analysis provides a mechanism to interpret the model's predictions and link them to known biological motifs, strengthening the biological relevance of the approach.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** "TRAFICA consistently outperformed all competing tools across the evaluations, demonstrating its robustness as a computational tool for investigating TF–DNA binding."
    - **Evidence pointer** Section 3.2, 3.3; Figures 2, 3; Tables 6, 7, 8 (location not provided)
    - **Concern** The claim of consistent state-of-the-art performance is made, but the statistical significance of the performance differences is not reported. For example, in the DREAM5 PBM benchmark, the difference between TRAFICA (PCC=0.647) and DNABERT (PCC=0.549) is stated with a P-value, but for other comparisons, particularly in the HT-SELEX cross-experiment and cross-platform tests, no statistical tests are mentioned. It is unclear if the observed improvements are statistically significant across all datasets and conditions.
    - **Why it matters** Without statistical significance testing, it is impossible to determine if the reported performance gains are robust or due to chance, especially when comparing models with different architectures and training procedures. This is a fundamental requirement for establishing a new state-of-the-art method.
    - **Resolution test** The authors should provide statistical significance tests (e.g., paired t-test, Wilcoxon signed-rank test) for all primary performance comparisons across all datasets and evaluation paradigms. The specific test used, the number of replicates, and the resulting P-values should be clearly reported in the main text or supplementary materials.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** "We further fine-tuned TRAFICA using low-rank adaptation (LoRA) on PBM and HT-SELEX TF-DNA binding profiles to learn intrinsic binding preferences for specific TFs."
    - **Evidence pointer** Section 2.4, Section 3.3 (location not provided)
    - **Concern** The methodology for the in vivo ChIP-seq prediction task is not described in sufficient detail. The text states that models fine-tuned on HT-SELEX data are tested on ChIP-seq data, but the exact procedure for generating predictions and calculating AUROC is unclear. How are the binary labels for the ChIP-seq peaks defined? Are the models predicting a score for all peaks, or are they classifying peaks versus non-peaks? The construction of the negative set is critical for AUROC calculation and is not described.
    - **Why it matters** The in vivo prediction task is a key differentiator and a major claim of the paper. If the evaluation protocol is not clearly defined and rigorously constructed, the reported AUROC values are not interpretable, and the claim of superior in vivo performance is not verifiable.
    - **Resolution test** The authors must provide a detailed description of the ChIP-seq evaluation protocol, including: (1) how the positive and negative sets of genomic regions are defined, (2) how the model is applied to these regions to generate a score, (3) how the AUROC is calculated, and (4) any filtering or preprocessing steps applied to the ChIP-seq peaks.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Reproducibility
    - **Claim pointer** "The source code of TRAFICA and detailed tutorials are available at https://github.com/ericcombiolab/TRAFICA."
    - **Evidence pointer** Data availability section (location not provided)
    - **Concern** While the code and data are stated to be available, the manuscript does not provide a detailed description of the model architecture hyperparameters (e.g., number of layers, hidden size, attention heads) beyond the number of parameters and layers. The exact training procedure, including learning rate schedules, warmup steps, and batch size, is mentioned but not fully specified. The specific LoRA configuration (rank, alpha) is given, but the details of the prediction head are not.
    - **Why it matters** For a computational methods paper, reproducibility is paramount. Without complete architectural and training details, other researchers cannot fully replicate the experiments or apply the method to new data, limiting the impact and utility of the work.
    - **Resolution test** The authors should provide a complete specification of the model architecture and training hyperparameters in the main text or a supplementary table. This should include all relevant details for both the pretraining and fine-tuning stages.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific Importance
    - **Claim pointer** "These findings indicate that considering the sequence characteristics from open chromatin regions could significantly improve TF–DNA binding affinity prediction."
    - **Evidence pointer** Section 3.2, Figure 2D (location not provided)
    - **Concern** The ablation study (Fig. 2D) shows that pretraining improves performance. However, the comparison is between a model pretrained on open chromatin sequences and a model trained from scratch. It is not clear if the improvement is due to the specific nature of the pretraining data (open chromatin) or simply due to the benefits of any pretraining (e.g., transfer learning from a large corpus). A more informative ablation would compare pretraining on open chromatin sequences versus pretraining on random genomic sequences or other non-functional sequences.
    - **Why it matters** The central hypothesis of the paper is that open chromatin context is specifically beneficial. If the performance gain is merely a general pretraining effect, the novelty and importance of the approach are diminished.
    - **Resolution test** The authors should include an additional ablation where the model is pretrained on a control dataset, such as random genomic sequences or sequences from closed chromatin regions, to demonstrate that the specific content of the open chromatin pretraining data is responsible for the observed improvement.

- **Minor Comments**

    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Section 3.3, Figure 3E
    - **Evidence pointer** "TRAFICA (5-mer) achieved the best performance compared to other methods across D1–D4 (Fig. 3E), with marginal performance differences relative to DNABERT (6-mer) on D5 (P = 0.884)."
    - **Issue** The statement "marginal performance differences" is vague. It is unclear if this means the difference is not statistically significant or if the magnitude of the difference is small.
    - **Required correction** Please clarify the statistical interpretation of the comparison on D5. If the difference is not significant, state that explicitly. If it is significant but small, provide the effect size.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Readability
    - **Affected element** Section 3.3, Figure 3I
    - **Evidence pointer** "identifying TFs MAFK (from cell lines: A549, H1, HeLa-S3, HepG2, IMR-90, K562, MCF-7, and GM12878) and ZSCAN4 (HEK293) as the top performers on D1 (mean AUROC>0.9)"
    - **Issue** The list of cell lines for MAFK is long and interrupts the flow of the sentence.
    - **Required correction** Consider moving the detailed list of cell lines to a supplementary table or figure legend, and summarizing the finding in the main text (e.g., "MAFK across multiple cell lines and ZSCAN4 in HEK293 cells").

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** Section 2.3, Model pretraining
    - **Evidence pointer** "We employed a warm-up strategy to select the learning rates during the pretraining stage (from 0.0001 to 0.0001 over the first 50 000 steps, cosine decay to 0 in the remaining steps)."
    - **Issue** The learning rate range is stated as "from 0.0001 to 0.0001", which implies no change during the warmup phase. This is likely a typo.
    - **Required correction** Please correct the learning rate schedule description. It should likely be "from 0 to 0.0001" or similar.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Section 3.3
    - **Evidence pointer** "We noticed that the average PCC of TRAFICA (5-mer) was higher on D3 compared to D4 and D5, a trend not shown on other models."
    - **Issue** The explanation for this observation is speculative ("could be attributed to the model's reduced capacity"). While this is a reasonable hypothesis, it is presented without supporting evidence.
    - **Required correction** Please either provide evidence to support this claim (e.g., analysis of training loss or model behavior) or clearly label it as a hypothesis for future investigation.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of statistical significance testing for key performance comparisons.
    - R1-M2: Insufficient detail on the in vivo ChIP-seq evaluation protocol, making the results non-reproducible and unverifiable.
    - R1-M3: Incomplete specification of model architecture and training hyperparameters, hindering reproducibility.

- **Assessment against Nature-style criteria**
    - **Originality**: The concept of pretraining a language model specifically on open chromatin regions is a novel contribution. While DNA language models exist, the targeted pretraining strategy to capture in vivo context is a distinct and interesting idea.
    - **Scientific importance**: The problem of accurately predicting TF–DNA binding affinity, especially in vivo, is of high importance to the fields of gene regulation and genomics. If the claims are robust, this work could provide a valuable tool and a new paradigm for integrating chromatin context into binding predictions.
    - **Interdisciplinary readership**: The work is primarily of interest to computational biologists and bioinformaticians. The biological implications are clear, but the methodological focus may limit its immediate appeal to a broader biological audience. The potential impact on understanding gene regulation could broaden its reach.
    - **Technical soundness**: The technical approach is sound in principle, but the current manuscript has significant gaps in the evaluation methodology and reporting of statistical rigor. The lack of detail on the in vivo evaluation and statistical tests prevents a full assessment of technical soundness.
    - **Readability for nonspecialists**: The manuscript is clearly written and the logic is easy to follow. The introduction and discussion provide sufficient context for a reader with a general genomics background. However, the methods section assumes a high level of familiarity with deep learning and high-throughput sequencing technologies.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the preliminary results are encouraging. However, the manuscript in its current form does not fully establish its claims due to the lack of statistical rigor and incomplete methodological details. The authors must address the major concerns, particularly the in vivo evaluation protocol and statistical testing, before the case for state-of-the-art performance is convincing.

## Risk / unsupported claims
- The claim of "state-of-the-art performance" is not fully supported without statistical significance testing across all benchmarks.
- The claim that TRAFICA has "better generalizability" based on cross-platform and cross-experiment tests is weakened by the lack of statistical analysis.
- The specific claim that the performance drop on larger datasets (D4, D5) is due to "model's reduced capacity" is unsupported and speculative.
- The biological interpretation of the attention-based motif analysis is presented as a strength, but the novelty of this analysis compared to existing methods is not discussed.
- The performance of TRAFICA on cell lines absent from pretraining is only briefly mentioned and not compared against other models, making the claim of generalizability to new cell lines unsubstantiated.