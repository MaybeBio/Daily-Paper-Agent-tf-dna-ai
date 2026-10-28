## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present EPEPDI, a deep learning framework using pre-trained protein language model embeddings (ESM2, ESM1v, ProtTrans) with a multi-channel transformer architecture to predict binding free energy changes (ΔΔG) from missense mutations in DNA-binding proteins, with separate models for double-stranded (DSB) and single-stranded (SSB) DNA-binding proteins, and an information entropy-based method to select an optimal input sequence length of 181 residues
- **Visible evidence base** Tables 1–6, Figures 2–8, descriptions of cross-validation and independent test results, ablation study, case study comparisons with mCSM-NA
- **Missing materials affecting confidence** Actual figure images, supplementary tables (S1–S3), Text S1, model architecture diagram (Figure 1), training code, hyperparameter details, statistical significance tests, and full benchmark dataset descriptions

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely the prediction of binding free energy changes upon missense mutations in protein-DNA interactions, with a novel emphasis on distinguishing double-stranded versus single-stranded DNA-binding proteins. The use of pre-trained protein language model embeddings is timely and the multi-channel architecture is reasonable. However, the manuscript has several critical weaknesses that prevent the case from being fully established: the dataset is very small, the comparison with existing methods appears incomplete or inconsistent, some reported numbers are internally inconsistent, and the claimed advantages are not rigorously demonstrated with statistical testing. The entropy-based sequence length selection is interesting but its justification is not fully convincing. The writing is sometimes unclear and contains apparent errors in cross-referencing tables and figures.
- **Who would be interested in the results, and why** Computational biologists working on protein-DNA interaction prediction, researchers developing deep learning methods for variant effect prediction, and potentially clinicians or geneticists interested in interpreting missense variants in DNA-binding proteins. The distinction between DSB and SSB proteins could be of interest to those studying DNA repair and replication mechanisms.
- **Major strengths** The explicit separation of DSB and SSB proteins is a thoughtful and biologically motivated design choice. The use of multiple pre-trained protein language model embeddings in a multi-channel architecture is a modern and reasonable approach. The entropy-based sequence length selection is a creative idea. The case study with structural visualization adds practical value.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset size and construction), R1-M2 (comparison methodology), R1-M3 (internal inconsistencies), R1-M4 (entropy method justification), R1-M5 (evaluation rigor)
- **Assessment against Nature-style criteria** Originality: moderate. The application of PLM embeddings to ΔΔG prediction is not entirely new, though the DSB/SSB distinction adds a novel angle. Scientific importance: moderate. Improving ΔΔG prediction is valuable, but the small dataset and limited validation reduce the potential impact. Interdisciplinary readership: limited. The work is primarily of interest to computational biologists; the biological insights are not deeply developed. Technical soundness: currently not fully established due to small dataset, incomplete comparisons, and internal inconsistencies. Readability for nonspecialists: the manuscript is generally readable but contains jargon and some unclear passages; the methods section is thin in places.
- **Recommendation posture** Currently not established from the provided evidence. The core idea is promising, but the dataset is too small, the comparisons are incomplete or inconsistent, and several technical issues need to be resolved before the claims can be accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset size and construction
- **Claim pointer** The authors claim that EPEPDI outperforms existing approaches on benchmark and independent datasets, and that the DSB/SSB distinction improves predictive accuracy.
- **Evidence pointer** Section 2.1, Table 1, Section 4.3, Section 4.5
- **Concern** The entire study is based on only 324 mutations from 73 complexes, with a training set of 276 mutations and an independent test set of 48 mutations. After splitting into DSB and SSB subsets, the SSB training set contains only 54 mutations from 6 complexes, and the independent SSB test set contains only 13 mutations from 5 complexes. This is an extremely small dataset for training a deep learning model with multiple transformer encoders. The risk of overfitting is very high, and the reported performance metrics are unlikely to be stable. The authors acknowledge the small dataset in Section 4.5 but do not adequately address how this affects the reliability of their conclusions.
- **Why it matters** Deep learning models require substantial data to generalize. With only 54 SSB training samples, the reported PCC of 0.863 for SSB108 is likely to be highly dependent on the specific data split and may not reflect true generalization performance. The claim that EPEPDI outperforms existing methods cannot be reliably established with such a small dataset.
- **Resolution test** The authors should provide confidence intervals for all reported metrics, perform multiple random splits with variance reporting, and ideally validate on additional external datasets. They should also discuss the minimum dataset size required for reliable deep learning in this context.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparison methodology
- **Claim pointer** The authors claim that EPEPDI outperforms existing state-of-the-art methods, including PEMPNI, SAMPDI, PremPDI, and mCSM-NA.
- **Evidence pointer** Section 4.5, Table 4, Figure 5, Figure 6
- **Concern** The comparison with existing methods is not described with sufficient detail. It is unclear whether the same data splits were used for all methods, whether hyperparameters were optimized for each method, and whether the comparison is fair. For example, in Section 4.5, the authors state that EPEPDI achieves a PCC of 0.755 on MPD552 cross-validation, but Figure 6A reports a PCC of 0.753 for the same setup. This discrepancy is not explained. Additionally, the comparison with mCSM-NA in Figure 5 appears to use different independent test sets (IDSB70 and ISSB26) than those described in Table 1 (IDSB35 and ISSB13). The relationship between these datasets is unclear.
- **Why it matters** A fair and transparent comparison is essential to support the claim of superiority. If the comparison is not conducted under identical conditions, the results are not interpretable. The internal inconsistencies in reported numbers further undermine confidence.
- **Resolution test** The authors should clearly describe the evaluation protocol for all methods, including data splits, hyperparameter tuning, and any preprocessing steps. They should reconcile the discrepancies between Table 4 and Figure 6, and clarify the relationship between the independent test sets mentioned in different sections.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency
- **Claim pointer** The manuscript reports performance metrics that are internally inconsistent across tables and figures.
- **Evidence pointer** Section 4.5, Table 4, Figure 6, Table 3
- **Concern** There are several apparent inconsistencies in the reported numbers. For example, in Section 4.5, the authors state that EPEPDI achieves a PCC of 0.755 and RMSE of 0.964 on MPD552 cross-validation, but Figure 6A reports a PCC of 0.753 and RMSE of 0.883 for the same setup. The authors provide a brief explanation that scatter plot metrics are calculated by combining results from each fold, but this does not fully explain why the RMSE differs so substantially. Additionally, in Section 4.5, the authors refer to "Table 3" when discussing independent test results, but Table 3 appears to be the ablation study table. The cross-referencing of tables and figures is confusing and suggests a lack of careful proofreading.
- **Why it matters** Internal inconsistencies in reported results make it difficult for readers to trust the findings. If the numbers cannot be reconciled, the validity of the conclusions is called into question.
- **Resolution test** The authors should carefully audit all reported metrics and ensure that tables, figures, and text are consistent. They should clarify the exact calculation method for each reported value and explain any discrepancies.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Entropy-based sequence length selection
- **Claim pointer** The authors claim that an information entropy-based algorithm determined 181 residues as the optimal sequence length where amino acid contributions and entropy dynamics balance.
- **Evidence pointer** Section 4.2, Figure 3
- **Concern** The entropy-based method for selecting sequence length is described only briefly. The algorithm is not fully specified, and the criteria for "optimal" are not clearly defined. The authors state that model performance generally improves with decreasing entropy, but this is a correlation, not a causal justification. It is unclear why 181 residues specifically is the optimal length, and whether this choice is robust across different datasets or protein families. The relationship between entropy and predictive performance is not rigorously established.
- **Why it matters** The choice of sequence length is a key design decision in the model. If the justification is not rigorous, the generalizability of the approach is questionable.
- **Resolution test** The authors should provide a more detailed description of the entropy-based algorithm, including the exact formula and the criteria for optimality. They should also show that the choice of 181 residues is stable across different random seeds or data subsets.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evaluation rigor
- **Claim pointer** The authors claim that EPEPDI demonstrates superior performance compared to existing methods, and that the DSB/SSB distinction improves accuracy.
- **Evidence pointer** Section 4.3, Section 4.5, Table 4, Figure 5
- **Concern** The evaluation lacks statistical significance testing. No confidence intervals, p-values, or error bars are reported for any of the performance metrics. Given the small dataset, it is possible that the observed differences between EPEPDI and other methods are not statistically significant. Additionally, the authors do not report results for multiple random seeds or data splits, which is standard practice for deep learning evaluations.
- **Why it matters** Without statistical rigor, the claimed improvements could be due to chance. The small dataset makes this concern particularly acute.
- **Resolution test** The authors should report confidence intervals for all metrics, perform multiple runs with different random seeds, and conduct appropriate statistical tests (e.g., paired t-tests or Wilcoxon signed-rank tests) to compare EPEPDI with baseline methods.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Section 2.2, last sentence
- **Evidence pointer** "For the MPD552 dataset, we assembled feature tensors—such as 512×181×1280 for ESM-2—omitting batch dimensions for simplicity/."
- **Issue** The sentence ends with a stray slash and is unclear. The meaning of "omitting batch dimensions for simplicity" is ambiguous.
- **Required correction** Rewrite the sentence for clarity, e.g., "For the MPD552 dataset, we assembled feature tensors of shape 512×181×1280 for ESM-2, omitting the batch dimension for simplicity."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Cross-referencing
- **Affected element** Section 4.5
- **Evidence pointer** "Figure 6 delivers unprecedented diagnostic insights" and "Table 3" references
- **Issue** The phrase "unprecedented diagnostic insights" is overly promotional and not supported by the evidence. Additionally, the reference to "Table 3" in the context of independent test results is confusing, as Table 3 appears to be the ablation study table.
- **Required correction** Replace promotional language with neutral phrasing. Correct the table cross-references to point to the appropriate tables.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Dataset description
- **Affected element** Section 2.1
- **Evidence pointer** "detailed information is provided in Table S1 and Table S2"
- **Issue** The supplementary tables are not available for review. The authors should provide at least a summary of the dataset composition in the main text.
- **Required correction** Add a brief summary of the dataset composition (e.g., number of proteins per type, distribution of ΔΔG values) in the main text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.3
- **Evidence pointer** "The model was trained over 150 epochs" and "early stopping halted training if validation loss stalled for 40 epochs"
- **Issue** The description of the training procedure is incomplete. Key hyperparameters such as learning rate, batch size, optimizer, and regularization are not reported.
- **Required correction** Provide a complete list of hyperparameters and training details, or refer to a publicly available code repository.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 4.5
- **Evidence pointer** "MPD976" in the sentence "EPEPDI excels over existing methods in PCC on MPD552 and MPD976"
- **Issue** The dataset "MPD976" is not defined anywhere in the manuscript. It is unclear whether this is a typo or a different dataset.
- **Required correction** Clarify the dataset name or correct the typo.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure availability
- **Affected element** Figures 1–8
- **Evidence pointer** All figures
- **Issue** The figures are not provided in the manuscript text. The descriptions in the text are insufficient to fully evaluate the results.
- **Required correction** Ensure that all figures are included and clearly labeled, with appropriate captions.

## Risk / unsupported claims
- The claim that EPEPDI "outperforms existing approaches" is not fully supported due to incomplete comparison methodology and lack of statistical testing.
- The claim that 181 residues is the optimal sequence length based on entropy analysis is not rigorously justified.
- The claim that distinguishing DSB and SSB proteins improves accuracy is plausible but not rigorously demonstrated with statistical significance.
- The reported performance metrics contain internal inconsistencies that are not fully explained.
- The case study comparison with mCSM-NA is limited to six mutations and may not be representative.
- The generalizability of the model to unseen protein families or larger datasets is not demonstrated.