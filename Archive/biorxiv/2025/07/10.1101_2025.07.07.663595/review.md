## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and data/code availability statements. Figures and supplementary materials are referenced but not provided.
- **Assessment boundary** Scientific validity, technical soundness, methodological clarity, and support of claims based solely on the provided text. No assessment of figures, tables, or supplementary data is possible as they were not supplied.
- **Shared manuscript claim summary** The authors introduce PPLM, a protein–protein language model pretrained on paired sequences with a hybrid intra-/inter-protein attention mechanism. They claim state-of-the-art performance across three downstream tasks: binary PPI prediction (PPLM-PPI), binding affinity prediction (PPLM-Affinity), and inter-protein contact prediction (PPLM-Contact and PPLM-Contact2), with particular gains on challenging immunological complexes and in comparison to structure-based methods including AlphaFold variants.
- **Visible evidence base** Textual descriptions of benchmark results, performance metrics (AUPRC, F1, PCC, SRCC, RMSE, MAE), statistical tests (Wilcoxon signed-rank, Cohen's d), and ablation summaries. All numerical results are reported in the text but the underlying figures, tables, and supplementary analyses are not visible.
- **Missing materials affecting confidence** All figures, all supplementary tables and texts, benchmark datasets, model architecture diagrams, and detailed per-fold results. Without these, the quantitative claims cannot be independently verified.

## Reviewer

- **Overall assessment** The manuscript presents a timely and potentially impactful contribution to computational PPI modeling. The core idea of pretraining a language model on paired sequences with an explicit inter-protein attention mechanism is conceptually sound and addresses a genuine limitation of single-sequence protein language models. The reported performance gains, particularly on binding affinity and contact prediction relative to structure-based methods, are notable. However, the assessment is severely constrained by the absence of all figures, tables, and supplementary materials. Several methodological details, especially regarding data leakage prevention, baseline fairness, and the precise architecture of the inter-protein transformer, require clarification. The claim that PPLM-Contact2 outperforms AlphaFold3 on contact prediction is strong and demands rigorous scrutiny of the evaluation protocol. The manuscript is well-written and the logical flow is clear, but the evidence base as presented is insufficient to fully establish all claims.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein interaction prediction, protein language models, and structure prediction would be the primary audience. Researchers in immunology and antibody engineering may also find the affinity prediction results on antibody–antigen and TCR–pMHC complexes relevant. The work is of interest because it proposes a unified sequence-based framework for three interrelated PPI tasks, potentially reducing dependence on costly structure determination or prediction.

- **Major strengths**  
  1. The conceptual advance of a paired-sequence language model with a dedicated inter-protein attention mechanism is clear and well-motivated.  
  2. The scope is broad, addressing three major PPI tasks within a single framework, which is ambitious and potentially unifying.  
  3. The authors report extensive benchmarking against multiple state-of-the-art methods, including structure-based approaches, which is commendable.  
  4. The attention to data leakage, including structure-level clustering and similarity-stratified evaluation, indicates methodological awareness.  
  5. The manuscript is clearly written and the logical structure is easy to follow.

- **Major Concerns**

  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** "PPLM-Contact further surpasses existing contact predictors on inter-protein contact prediction and interface residue recognition, including those deduced from cutting-edge complex structure predictions."  
  - **Evidence pointer** Results section "PPLM-Contact outperforms existing methods in inter-protein contact prediction"; Figures 4 and 5; Supplementary Tables S10–S15  
  - **Concern** The claim that PPLM-Contact2 outperforms AlphaFold2.3, AlphaFold3, and DMFold on inter-protein contact prediction is a strong and important result. However, the evaluation protocol is not fully described in the text. Specifically, it is unclear whether the AlphaFold models were run under identical conditions, whether the same test set was used for all methods, and how contact precision was computed for structure-based methods (e.g., from predicted models or from sampled structures). The text states that "all baseline methods were installed and executed locally," but the precise input formats, multiple sequence alignment generation, and any template usage for the AlphaFold baselines are not specified.  
  - **Why it matters** If the comparison is not perfectly controlled, the reported improvements over AlphaFold3 could be an artifact of evaluation conditions rather than genuine methodological superiority. This is the most consequential claim in the manuscript and requires the highest standard of evidence.  
  - **Resolution test** Provide a detailed description of the evaluation protocol for all baselines, including exact commands, input features, and any post-processing. Show that the test set is identical across methods and that contact precision is computed in a consistent manner. Ideally, provide per-target results in the supplementary material to allow independent verification.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Data leakage and generalization  
  - **Claim pointer** "PPLM-PPI maintains strong performance across all homology ranges and delivers the largest gains over existing methods, demonstrating that its predictive accuracy is not driven by shortcut learning."  
  - **Evidence pointer** Results section "PPLM-PPI outperforms existing methods in binary protein interaction prediction"; Supplementary Text S3  
  - **Concern** The similarity-stratified evaluation is described only briefly. The text states that test interactions were grouped by maximum sequence identity to any human protein in the training set, but the thresholds for the identity intervals are not given, and it is unclear how the training set for PPLM-PPI relates to the PPLM pretraining data. Since PPLM was pretrained on a large corpus that includes PDB and STRING data, there is a risk that the pretraining data overlaps with the test sets used for downstream evaluation. The authors state that validation pairs were removed if redundant to training clusters, but this is described for PPLM pretraining, not for the PPI benchmark test sets.  
  - **Why it matters** If the pretraining data overlaps with downstream test sets, the reported performance could be inflated by memorization rather than genuine generalization. This concern applies to all three downstream tasks but is most acute for PPI prediction where the benchmark datasets are derived from public databases.  
  - **Resolution test** Clarify the relationship between the PPLM pretraining corpus and all downstream benchmark test sets. Provide explicit sequence identity thresholds used for stratification and demonstrate that no test pair shares significant sequence identity with any pretraining pair. If such filtering was not performed, re-run the evaluations on strictly non-overlapping test sets.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Methodological clarity  
  - **Claim pointer** "we introduce a novel Protein–Protein Language Model (PPLM) that jointly encodes paired sequences, enabling direct learning of interaction-aware representations"  
  - **Evidence pointer** Methods section "Protein–protein language model"; Figure 1A  
  - **Concern** The description of the hybrid intra-/inter-protein attention mechanism is incomplete. The text mentions rotary position embeddings for intra-chain attention and no positional encoding for inter-protein attention, along with learnable weights and a binary mask. However, the exact formulation of how the two attention matrices are combined is not fully specified. The equation for the full attention matrix is referenced but not shown in the text. Additionally, the rationale for using no positional encoding for inter-protein pairs is stated as avoiding spurious spatial priors, but the potential consequences for sequence-order-dependent interactions are not discussed.  
  - **Why it matters** The attention mechanism is the central methodological contribution. Without a complete specification, the work cannot be reproduced or fully evaluated. The choice of positional encoding strategy has implications for the model's ability to capture distance-dependent interaction patterns.  
  - **Resolution test** Provide the complete mathematical formulation of the attention mechanism, including the combination rule for the two attention matrices and the role of the learnable weights. Discuss the trade-offs of omitting positional encoding for inter-protein pairs and, if possible, include an ablation showing the impact of this design choice.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Baseline fairness  
  - **Claim pointer** "PPLM-Affinity outperforms both ESM2 and structure-based methods on binding affinity modeling, particularly on challenging cases including antibody–antigen and TCR–pMHC complexes."  
  - **Evidence pointer** Results section "PPLM-Affinity achieves superior performance in protein binding affinity prediction"; Figure 3D; Supplementary Tables S7–S9  
  - **Concern** The comparison with structure-based methods for affinity prediction is described only in aggregate. It is unclear which specific structure-based methods were compared, whether they were retrained on the same data, and whether the same cross-validation splits were used. The text states that the PPB-Affinity model was retrained using its released source code, but the details of this retraining, including hyperparameters and training time, are not provided. Additionally, the evaluation metric is reported as PCC and SRCC, but the units of the predicted affinity values and the range of the experimental data are not stated.  
  - **Why it matters** Affinity prediction is notoriously sensitive to data splitting and evaluation protocols. If the structure-based baselines were not given the same advantage of pretraining or fine-tuning, the comparison may be unfair. The practical significance of a PCC improvement from, say, 0.60 to 0.64 depends on the context and the difficulty of the dataset.  
  - **Resolution test** List all baseline methods with their respective input features and training procedures. Report the distribution of experimental ΔG values in the test sets. Provide per-subgroup results (e.g., antibody–antigen, TCR–pMHC, enzyme–inhibitor) to show where the gains are concentrated. Consider reporting additional metrics such as RMSE in kcal/mol to aid interpretation.

  - **Concern ID** R1-M5  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Statistical rigor  
  - **Claim pointer** "All improvements are statistically significant" (stated for contact prediction and interface recognition)  
  - **Evidence pointer** Results sections on contact prediction and interface recognition; Supplementary Tables S10–S18  
  - **Concern** The text reports statistical significance using Wilcoxon signed-rank tests and Cohen's d effect sizes, but the multiple testing problem is not addressed. With many comparisons across multiple datasets, cutoffs, and baselines, the probability of false positives increases. The authors mention Benjamini-Hochberg FDR correction in one sentence for the contact prediction analysis, but it is unclear whether this correction was applied to all reported comparisons or only a subset.  
  - **Why it matters** Without proper multiple testing correction, some of the reported "significant" improvements may be spurious. This is particularly relevant for the head-to-head comparisons where many individual targets are tested.  
  - **Resolution test** Clearly state which comparisons were corrected for multiple testing and which were not. Apply FDR correction consistently across all primary claims. Report the number of tests performed and the adjusted p-values for the main results.

- **Minor Comments**

  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Abstract  
  - **Evidence pointer** Abstract, first sentence  
  - **Issue** The title contains "Corporative" which appears to be a typographical error. The intended word is likely "Cooperative" or "Corporative" may be a nonstandard usage.  
  - **Required correction** Verify the intended word and correct the title accordingly.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Methods, binding affinity prediction  
  - **Evidence pointer** Methods section "Binding affinity prediction using PPLM"  
  - **Issue** The text states that the last transformer block of PPLM is fine-tuned, but the number of trainable parameters, the learning rate schedule, and the early stopping criteria are not specified.  
  - **Required correction** Provide full training details, including optimizer settings, batch size, number of epochs, and any regularization techniques.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Results, interface recognition  
  - **Evidence pointer** Results section "PPLM-Contact enhances interface residue recognition"  
  - **Issue** The definition of interface residues is given (heavy atoms within 8 Å), but the evaluation metric is only described as "precision." It is unclear whether recall or F1 are also reported and whether the metric is computed per-residue or per-target.  
  - **Required correction** Clarify the exact evaluation metrics and how they are aggregated across targets.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Presentation  
  - **Affected element** Results, PPLM language modeling  
  - **Evidence pointer** Results section "PPLM improves language modeling of protein pairs"  
  - **Issue** The perplexity comparison with ESM2 is described, but the text does not state whether the comparison was performed on identical sequences and masking patterns.  
  - **Required correction** Specify the exact evaluation protocol for perplexity, including the number of masked positions and whether the same random seeds were used.

  - **Concern ID** R1-m5  
  - **Severity** Minor  
  - **Axis** Accessibility  
  - **Affected element** Data availability  
  - **Evidence pointer** Data availability section  
  - **Issue** The URL for the Uniref30 database contains a typo: "https://wwwuser.gwdguser.de/~compbiol/uniclust/" appears to have duplicated "user".  
  - **Required correction** Correct the URL to the proper Uniclust/UniRef30 download page.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (baseline evaluation protocol for contact prediction), R1-M2 (potential pretraining-test overlap), and R1-M3 (incomplete attention mechanism specification) are the primary technical issues. Without resolving these, the central claims of the manuscript cannot be fully accepted.

- **Assessment against Nature-style criteria**  
  - **Originality** The idea of a paired-sequence language model with explicit inter-protein attention is a genuine conceptual advance over single-sequence models. The unified treatment of three PPI tasks is also novel. However, the individual components (attention mechanisms, transformer architectures, fine-tuning strategies) are not new in themselves. The originality lies in their combination and application.  
  - **Scientific importance** If the claims hold, the work could have broad impact on PPI prediction, affinity estimation, and contact-based structure modeling. The potential to replace structure-based affinity prediction with a sequence-based method is significant. However, the importance is contingent on the robustness of the evaluation.  
  - **Interdisciplinary readership** The work bridges machine learning, structural biology, and immunology. The results on antibody–antigen and TCR–pMHC complexes could attract interest from the therapeutic antibody community. The writing is accessible to a broad computational biology audience, though some methodological details require specialized knowledge.  
  - **Technical soundness** The overall approach is technically sound in concept, but the incomplete specification of the attention mechanism and the insufficient detail on baseline evaluations prevent a full assessment. The statistical analyses appear appropriate but need consistent multiple testing correction.  
  - **Readability for nonspecialists** The manuscript is well-structured and the narrative is clear. The abstract effectively summarizes the contributions. However, the methods section assumes familiarity with transformer architectures and protein language models, which may limit accessibility for readers outside the immediate field.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the reported results are potentially important. However, the manuscript in its current form does not provide sufficient evidence to fully establish the claims, particularly regarding the comparison with AlphaFold3 and the generalization to unseen proteins. The authors should be encouraged to revise the manuscript to address the concerns raised, with particular attention to the evaluation protocol and data leakage prevention.

## Risk / unsupported claims
- The claim that PPLM-Contact2 outperforms AlphaFold3 on inter-protein contact prediction is not fully supported by the visible evidence, as the evaluation protocol for the AlphaFold baselines is not described in sufficient detail.
- The claim that PPLM-PPI's performance is not driven by shortcut learning is not fully supported, as the relationship between the PPLM pretraining corpus and the PPI benchmark test sets is not clarified.
- The reported improvements on antibody–antigen and TCR–pMHC affinity prediction are promising but cannot be evaluated without the per-subgroup results and the distribution of experimental values.
- The perplexity improvements over ESM2 are reported with statistical significance, but the practical implications of these improvements for downstream tasks are not directly demonstrated.
- The claim that PPLM captures "biologically meaningful dependencies" based on the single example of 1Y9B is suggestive but not generalizable without additional case studies or systematic analysis.