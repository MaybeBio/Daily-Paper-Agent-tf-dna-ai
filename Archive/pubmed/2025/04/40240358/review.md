## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information references.
- **Assessment boundary** Scientific validity, methodological soundness, benchmark rigor, biological interpretability, and generalizability of the TRAPT framework as presented.
- **Shared manuscript claim summary** The authors propose TRAPT, a multi-stage deep learning framework that integrates cis-regulatory element activity and genome-wide transcription regulator binding site information to predict transcriptional regulators from input gene sets. They claim state-of-the-art performance on 570 knockdown/knockout datasets, superior prediction of transcription co-factors and chromatin regulators, and successful identification of disease-relevant, cell-fate, and tissue-specific regulators.
- **Visible evidence base** Benchmark comparisons against Lisa, BART, iCisTarget, and ChEA3; ablation studies; case studies in ESR1 knockdown, Alzheimer's disease post-GWAS analysis, hematopoiesis, and tissue-specific analysis; supplementary figures and data referenced.
- **Missing materials affecting confidence** Supplementary figures and data files (Supplementary Figs. 1-9, Supplementary Data 1-11) were not provided. Detailed hyperparameter settings, training/validation splits, and statistical significance thresholds for benchmark comparisons are not fully described in the visible text. Code and web tool functionality could not be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a technically ambitious and potentially useful framework for transcriptional regulator prediction. The multi-stage fusion approach, combining knowledge distillation with graph neural networks, is conceptually interesting and addresses a real gap in existing tools. However, the visible evidence is insufficient to fully evaluate the claimed performance gains. Several methodological details are underspecified, and the benchmark comparisons, while favorable, lack rigorous statistical treatment. The biological case studies are compelling but would benefit from more quantitative validation. The work is likely of interest to computational biologists and epigenomics researchers, but the current presentation does not fully establish the superiority of TRAPT over existing methods.

- **Who would be interested in the results, and why** Computational biologists developing gene regulatory network inference tools; epigenomics researchers studying enhancer-promoter interactions and chromatin state; researchers using gene set enrichment approaches to identify upstream regulators in disease contexts; and bioinformaticians interested in knowledge distillation and graph neural network applications in genomics.

- **Major strengths**
  1. The conceptual advance of integrating both cis-regulatory element activity and genome-wide binding site information in a single framework is novel and addresses a clear limitation of existing methods.
  2. The multi-stage knowledge distillation design, with separate models for downstream and upstream regulatory potential, is well-motivated and technically sound.
  3. The extensive benchmark evaluation across 570 datasets, including separate analyses for TFs, TcoFs, and CRs, is commendable in scope.
  4. The biological case studies (ESR1, Alzheimer's disease, hematopoiesis, tissues) provide practical demonstrations of utility.
  5. The availability of both web and local implementations increases accessibility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim TRAPT outperforms state-of-the-art methods, but the statistical significance of these improvements is not established.
- **Evidence pointer** Results section "TRAPT demonstrates state-of-the-art performance on benchmark datasets"; Fig. 2
- **Concern** The performance comparisons report raw improvements (e.g., 13% better than Lisa in top-10 recovery) but do not provide confidence intervals, p-values, or effect sizes for these differences. Given the likely overlap in predictions between methods, it is unclear whether the observed improvements are statistically meaningful or within the range of random variation.
- **Why it matters** Without statistical rigor, the central claim of superiority over existing methods cannot be substantiated. This is critical for a methods paper where the primary contribution is improved performance.
- **Resolution test** Provide bootstrap confidence intervals or paired statistical tests (e.g., Wilcoxon signed-rank) across the 570 datasets for each comparison. Report effect sizes and discuss practical significance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The U-RP model selects 10 epigenomic samples based on "reasonable choice" determined by auROC, but the selection procedure is not fully described.
- **Evidence pointer** Methods section "Predicting the regulatory potential via downstream gene sets"; Supplementary Fig. 2e
- **Concern** The manuscript states that "We determined that 10 epigenomic samples provided a reasonable choice" but does not describe the full range of sample sizes tested, the criteria for "reasonable," or whether this choice was optimized on the benchmark datasets (which could lead to overfitting). The selection of 10 samples appears somewhat arbitrary.
- **Why it matters** The number of selected epigenomic samples is a key hyperparameter that directly affects model performance and interpretability. If this was tuned on the test data, the reported performance may be optimistically biased.
- **Resolution test** Describe the full hyperparameter search, use nested cross-validation or a separate validation set for selection, and show sensitivity analysis around the chosen value.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The D-RP model's link prediction performance is reported (auROC 0.81, auPRC 0.84), but the evaluation protocol is unclear.
- **Evidence pointer** Results section "Multi-stage fusion strategy boosts prediction of transcriptional regulators"; Supplementary Fig. 3c
- **Concern** The link prediction evaluation splits observed links into training, validation, and test sets, but the manuscript does not specify how negative links were sampled, whether the split was random or time-based, or whether the model was evaluated on its ability to recover held-out links of specific types (e.g., cell-type-specific links). The masking experiments (up to 15% masked) are described but the relationship to the reported auROC/auPRC is unclear.
- **Why it matters** Link prediction results are used to justify the D-RP model's ability to reconstruct regulatory relationships. If the negative sampling or evaluation protocol is biased, the reported performance may not reflect real-world utility.
- **Resolution test** Clearly describe the negative sampling strategy, the train/validation/test split, and report performance stratified by link type or cell-type specificity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The Alzheimer's disease case study claims identification of key TRs impacted by causal variants, but the validation is largely qualitative.
- **Evidence pointer** Results section "TRAPT predicts functional transcriptional regulators in post-GWAS analysis of Alzheimer's disease"; Fig. 5
- **Concern** The analysis identifies TRs whose binding sites overlap with causal variants, but the statistical framework for assessing enrichment is not fully described. The p-values reported (e.g., hypergeometric test p=2.5e-12) are for binding enrichment, but it is unclear whether these are corrected for multiple testing across the many TRs examined. The co-localization analysis is mentioned but not described in detail.
- **Why it matters** For the method to be useful in post-GWAS interpretation, the statistical framework must be rigorous and properly controlled. Overstated significance could lead to false biological conclusions.
- **Resolution test** Describe the multiple testing correction procedure, provide a null model for the enrichment analysis, and report the full distribution of p-values (e.g., via a Q-Q plot).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The ablation studies demonstrate the contribution of each module, but the results are only presented as bar charts without numerical values or statistical tests.
- **Evidence pointer** Results section "Multi-stage fusion strategy boosts prediction of transcriptional regulators"; Fig. 3
- **Concern** The ablation results (removing U-RP, D-RP, TR-RP, knowledge distillation) are described qualitatively ("significant decline") but the actual MRR values and the magnitude of decline are not reported in the text. Without numerical values, it is difficult to assess the relative importance of each component.
- **Why it matters** Ablation studies are essential for understanding which components drive performance. The current presentation does not allow readers to evaluate the contribution of each module quantitatively.
- **Resolution test** Report the numerical MRR values for each ablation condition, include confidence intervals, and perform statistical tests comparing each ablation to the full model.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and uses technical jargon ("multi-stage fused deep learning framework," "cis-regulatory elements," "genome-wide binding sites") without sufficient context for a general readership.
- **Required correction** Briefly explain what "transcriptional regulator activity" means in practical terms and why predicting it from gene sets is important, before introducing the technical approach.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Hyperparameters and training of the model"
- **Evidence pointer** Methods section
- **Issue** The hyperparameters for the U-RP model's teacher and student networks are not specified (only the D-RP model's batch size, learning rate, and epochs are given).
- **Required correction** Provide the full hyperparameter settings for all models, including network architectures, activation functions, optimization algorithms, and regularization parameters.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Preprocessing of datasets of epigenomes and transcriptional regulators"
- **Evidence pointer** Methods section
- **Issue** The description of data preprocessing is brief. It is unclear how the 20,000+ datasets were quality-controlled, how peaks were called, and how the "percentage of intergenic distance" was calculated and used as a weight.
- **Required correction** Provide a more detailed description of the data processing pipeline, including specific tools, parameters, and quality control thresholds.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Results section "TRAPT predicts key transcriptional regulators in the ESR1 knockdown study"
- **Evidence pointer** Fig. 4
- **Concern** The figure caption mentions "gastric cancer" in the title, but the text describes breast cancer (MCF7). This is confusing.
- **Required correction** Clarify whether the analysis was performed on both gastric and breast cancer datasets, or correct the figure title.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion is largely a summary of results and does not critically evaluate limitations or compare with alternative deep learning approaches in detail.
- **Required correction** Add a paragraph discussing limitations (e.g., dependence on existing ChIP-seq data quality, potential biases in the training data, generalizability to non-human species) and how TRAPT compares with other deep learning-based regulatory prediction methods.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Calculation of enrichment scores and significance in post-GWAS analysis"
- **Evidence pointer** Methods section
- **Issue** The description of the enrichment score calculation is unclear. The formula appears to be a running sum statistic, but the "scale" function is not defined.
- **Required correction** Define all terms in the formula and provide a step-by-step description of the enrichment score calculation.

## Risk / unsupported claims
- The claim that TRAPT "outperformed state-of-the-art methods" is not statistically substantiated without confidence intervals or hypothesis tests.
- The claim that TRAPT "successfully identify key TRs associated with diseases" is based on qualitative case studies without quantitative validation against known disease mechanisms.
- The claim that the D-RP model "effectively captured the epigenetic information of ESR1 in cancer" is based on p-values from a single comparison and may not be robust.
- The generalizability of TRAPT to non-human species or to gene sets derived from non-differential-expression sources is not demonstrated.
- The performance of the web tool and local installation could not be verified from the provided materials.
- The claim that the multi-stage fusion strategy is superior to simpler alternatives is only supported by ablation studies without statistical testing.