## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and data/code availability statements.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and adequacy of evidence as presented in the provided text. No assessment of code functionality, supplementary figures, or unreferenced external data.
- **Shared manuscript claim summary** The authors present DeepSCENIC, a deep learning framework that infers causal gene regulatory networks (GRNs) by transferring knowledge from pretrained sequence-to-function (S2F) models to single-cell multiome data. The framework jointly learns TF–region (TF–RE) and region–gene (RE–TG) interactions, enabling prediction of perturbation effects and cross-species GRN conservation.
- **Visible evidence base** Abstract, Introduction, Results (narrative only, no figures or tables visible), Discussion, Methods, and data/code availability statements.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are absent from the provided text. Specific quantitative results (e.g., AUC values, correlation coefficients, p-values) are mentioned but not shown in tabular or graphical form. Details of model architecture, hyperparameters, and training procedures are incomplete.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing and timely integration of S2F models with single-cell GRN inference. The core idea, using transfer learning from pretrained models like Enformer and Borzoi to parameterize TF–RE interactions, is a logical and potentially impactful advance. However, the current text, without access to figures and detailed methods, does not allow verification of the central claims. The narrative is strong on motivation and positioning but thin on verifiable quantitative evidence. The lack of a clear baseline comparison against state-of-the-art GRN methods (beyond correlation-based approaches) and the absence of statistical rigor in several validation sections are notable weaknesses. The manuscript is well-written and accessible, but the scientific case is not fully established from the provided material.
- **Who would be interested in the results, and why** Computational biologists developing or applying GRN inference methods; researchers studying gene regulation, enhancer biology, and cell fate decisions; and those interested in the application of foundation models to single-cell genomics. The potential to simulate both cis- and trans- perturbations in a mechanistic framework would be of broad interest to the gene regulation community.
- **Major strengths**
    1.  The conceptual advance of unifying S2F models with GRN inference is significant and timely.
    2.  The model's design for interpretability, with explicit TF–RE and RE–TG parameters, is a strong point.
    3.  The validation strategy, using multiple independent datasets (ENCODE, CRISPRi, melanoma, cross-species), is comprehensive in scope.
    4.  The writing is clear and effectively positions the work within the broader landscape of both S2F models and GRN inference methods.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Evidence sufficiency
        - **Claim pointer** The claim that DeepSCENIC "accurately predicts single-cell gene expression and chromatin accessibility" and "recovers TF-region (TF-RE) interactions with high fidelity" is central to the paper's premise.
        - **Evidence pointer** Results section "DeepSCENIC: Extracting gene regulatory networks from sequence-to-function models" and "DeepSCENIC simulates cell state changes upon TF and sequence perturbation"; location not provided.
        - **Concern** The text states performance metrics (e.g., "mean correlation of 0.41 for expression and 0.46 for accessibility", "AUC of 0.83", "correlation coefficients of 0.85 and 0.82") but provides no figures, tables, or statistical distributions to support these numbers. The reader cannot assess the variance, the significance of the improvement over baselines, or the context of these values (e.g., what is a good AUC for this task?).
        - **Why it matters** The core scientific claim rests on these quantitative results. Without the ability to see the data, the performance, and the comparison, the claims are unverifiable and the scientific case is not established.
        - **Resolution test** Provide the figures and tables that display these results, including error bars, statistical tests, and clear baseline comparisons. The text should reference these figures so the reader can directly evaluate the evidence.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Methodological clarity
        - **Claim pointer** The claim that DeepSCENIC enables "causal gene regulatory network inference" and can act as a "mechanistic simulator" for perturbations.
        - **Evidence pointer** Methods section "Model parameterization and outputs" and "In-silico perturbations"; location not provided.
        - **Concern** The methods section is incomplete. The exact architecture of the variational encoder, the definition of the "shared non-linear variational encoder f(⋅)", the precise form of the loss function (the equation is missing), and the details of the "iterated" perturbation procedure are not fully specified. The claim of causality is strong and requires a clear explanation of how the model structure and training procedure justify it, beyond just propagating perturbations through learned weights.
        - **Why it matters** For a methods paper, the reproducibility of the approach is paramount. The current description is too high-level to be replicated. The causal claim needs a more rigorous justification, as the model appears to learn associations from observational data, and the term "causal" is used loosely.
        - **Resolution test** Provide a complete mathematical specification of the model, including all equations, loss functions, and training algorithms. Include a dedicated section or discussion that explicitly addresses the assumptions and limitations of the model's causal interpretation.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Benchmarking and comparison
        - **Claim pointer** The claim that DeepSCENIC outperforms "correlation-based baselines" and is a superior approach to existing GRN methods.
        - **Evidence pointer** Results section "DeepSCENIC: Extracting gene regulatory networks from sequence-to-function models"; location not provided.
        - **Concern** The only baselines mentioned are correlation-based methods. The GRN inference field has many established methods (e.g., SCENIC+, Pando, CellOracle, GENIE3, GRNBoost2) that are not purely correlation-based. The comparison to SCENIC+ is mentioned but not detailed. A more robust comparison against a wider range of state-of-the-art methods is necessary to support the claim of superiority.
        - **Why it matters** The novelty and utility of a new method are judged by its performance relative to the current state of the art. The current comparison is too narrow to be convincing.
        - **Resolution test** Include a benchmark against a diverse set of GRN inference methods on the same datasets, using standard evaluation metrics (e.g., AUROC, AUPRC for edge prediction). The results should be presented in a clear figure.
    - **R1-M4**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Validation of cross-species claims
        - **Claim pointer** The claim that DeepSCENIC identifies "mouse-human cortex conserved GRNs" and that this provides cross-species support for the inferred networks.
        - **Evidence pointer** Results section "DeepSCENIC identifies conserved GRNs in the human and mouse cerebral cortex"; location not provided.
        - **Concern** The methodology for this analysis is vague. The text mentions "matched cortical subclasses" and "liftOver" but does not specify how the GRNs are compared, what constitutes "conservation," or how statistical significance is assessed. The validation against "experimental reporter assays" is mentioned but not detailed.
        - **Why it matters** Cross-species conservation is a powerful validation, but only if the analysis is rigorous and well-defined. The current description is too superficial to be evaluated.
        - **Resolution test** Provide a detailed description of the conservation analysis, including the exact definition of conserved TF–TG links, the null model used, and the statistical tests. Show the results of the reporter assay validation in a figure.

- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Clarity
        - **Affected element** Abstract and Introduction
        - **Evidence pointer** Abstract; location not provided.
        - **Issue** The abstract states the model "enables causal GRN inference" but the term "causal" is not defined or qualified. This is a strong claim that is not fully supported by the methods described.
        - **Required correction** Consider using a more cautious term like "mechanistic" or "predictive" in the abstract, or explicitly define the scope of causality in the introduction.
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Completeness
        - **Affected element** Methods section "GRN benchmark evaluation protocol"
        - **Evidence pointer** Methods; location not provided.
        - **Issue** The section header is present, but the content is missing from the provided text.
        - **Required correction** Ensure the full protocol is included in the final manuscript.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Reproducibility
        - **Affected element** Methods section "Datasets"
        - **Evidence pointer** Methods; location not provided.
        - **Issue** The description of the simulated ENCODE data is clear, but the details of the melanoma and cortex datasets are sparse. The text mentions "processed scRNA-seq count matrix" and "topic-modeled imputed accessibility" but does not specify the exact processing steps or the source of these processed files.
        - **Required correction** Provide more detail on the data processing pipelines or cite the exact source of the processed data files.
    - **R1-m4**
        - **Severity** Minor
        - **Axis** Presentation
        - **Affected element** Results section "DeepSCENIC simulates cell state changes upon TF and sequence perturbation"
        - **Evidence pointer** Results; location not provided.
        - **Issue** The text mentions "predicted log2FC trajectories" and "standardized MEL/MES program activity scores" but the figure that would show these trajectories is not referenced.
        - **Required correction** Add explicit references to the relevant figures (e.g., "Fig. 3f, g") in the text.
    - **R1-m5**
        - **Severity** Minor
        - **Axis** Statistical rigor
        - **Affected element** Results section "DeepSCENIC identifies conserved GRNs in the human and mouse cerebral cortex"
        - **Evidence pointer** Results; location not provided.
        - **Issue** The text states that conserved TF–TG links show "overlap beyond random expectation" but does not provide the p-values or confidence intervals for this enrichment.
        - **Required correction** Report the statistical significance of the observed overlaps.

## Risk / unsupported claims
- The claim of "causal GRN inference" is not supported by the methodological description, which appears to be based on associative learning from observational data.
- All quantitative performance claims (e.g., correlation coefficients, AUCs) are unverifiable without the corresponding figures and tables.
- The claim that DeepSCENIC "captures de novo TF binding motifs without prior PWM knowledge" is not supported by the provided text, as the motif recovery experiment is only described narratively.
- The claim of "high cross-species concordance" in TF activity programs is not supported by any statistical evidence in the text.
- The claim that DeepSCENIC is a "new paradigm" is an overstatement not supported by the evidence presented.