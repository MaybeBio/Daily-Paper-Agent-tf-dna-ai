## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion) as provided
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the supplied text
- **Shared manuscript claim summary** The authors present LINGER, a lifelong learning neural network method that integrates atlas-scale external bulk data and TF motif knowledge to infer gene regulatory networks from single-cell multiome data, claiming 2-3 fold higher accuracy over existing methods and enabling TF activity estimation from expression data alone
- **Visible evidence base** Results sections describing benchmark comparisons (Fig 2, 3, 4), GWAS integration analyses (Fig 5), and TF activity applications (Fig 6); methods descriptions; supplementary references
- **Missing materials affecting confidence** Figures and supplementary tables referenced but not provided; detailed hyperparameter settings; ablation study details; statistical test descriptions partially incomplete; code availability statement absent

## Reviewer
- **Overall assessment** The manuscript addresses a significant problem in computational biology, namely context-specific GRN inference from single-cell multiome data, and proposes a technically interesting solution combining lifelong learning with motif-based regularization. The core idea of leveraging atlas-scale external data through continuous learning is timely and potentially impactful. However, the evidence presented in the text is insufficient to fully evaluate the claimed performance improvements, particularly regarding the statistical rigor of benchmark comparisons, the contribution of individual method components, and the generalizability of findings beyond the demonstrated cell types. The GWAS and TF activity analyses are promising but require more detailed methodological clarity and validation.

- **Who would be interested in the results, and why** Computational biologists developing GRN inference methods, researchers studying gene regulation in single cells, and investigators using GWAS data to identify disease-relevant cell types and regulatory mechanisms. The method's ability to estimate TF activity from expression data alone could be broadly useful for interpreting case-control transcriptomic studies.

- **Major strengths** The problem is well-motivated and important. The lifelong learning framework is a novel and appropriate application to GRN inference, addressing the fundamental issue of limited independent data points. The integration of motif knowledge via manifold regularization is principled. The downstream applications to GWAS interpretation and TF activity estimation demonstrate practical utility. The writing is generally clear and accessible.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "LINGER achieves 2–3 fold higher accuracy over existing methods" (Abstract) and "LINGER improves the cellular population GRN inference by lifelong machine learning" (Results)
- **Evidence pointer** Fig 2B, 2C, 2D, 2E; Fig 3; Fig 4; Methods "Benchmark the trans-regulatory potential"
- **Concern** The benchmark comparisons are described only in aggregate terms. The text reports p-values from paired t-tests but does not provide effect sizes, confidence intervals, or the number of test cases for each comparison. The claim of "2-3 fold higher accuracy" is not substantiated with specific AUPR ratio values across all ground truth datasets. The comparison with SCENIC+ uses F1 score with a threshold-based selection of top predictions, which may not be directly comparable to the continuous scoring used for other methods. The choice of ground truth datasets (10 for blood, 33 for H1) is mentioned but the criteria for inclusion and potential biases are not discussed.
- **Why it matters** The central claim of the manuscript is that LINGER substantially outperforms existing methods. Without detailed quantitative results, statistical rigor, and transparent comparison protocols, this claim cannot be verified. The scientific community requires reproducible and statistically sound benchmarks to assess whether a new method genuinely advances the field.
- **Resolution test** Provide a comprehensive benchmark table with AUPR ratios, AUC values, and their standard deviations or confidence intervals for all methods across all ground truth datasets. Include the number of positive and negative examples for each ground truth. Describe the exact protocol for generating ROC and PR curves, including how thresholds are applied. For SCENIC+ comparisons, clarify whether the same number of predictions is used for all methods and justify the F1 score approach.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "LINGER improves the cell type specific GRN inference" (Results section title) and the described improvements in TF-RE binding, cis-regulatory, and trans-regulatory predictions
- **Evidence pointer** Fig 3A-E, 3F-K; Fig 4; Fig S2; Methods "Construct cell type-specific gene regulatory network"
- **Concern** The cell type-specific GRN construction combines multiple factors (TF-RE binding potential, cis-regulatory potential, trans-regulatory potential) into composite scores. The text does not explain how these factors are weighted or normalized relative to each other. The validation of cell type-specific predictions relies on ChIP-seq, HiC, and eQTL data, but the text does not describe how cell type matching is performed between the multiome data and these external validation datasets. For example, ChIP-seq data for "blood" may not correspond exactly to the specific PBMC cell types identified in the single-cell data. The eQTL validation uses whole blood data, which is a mixture of cell types, potentially confounding cell type-specific claims.
- **Why it matters** The manuscript claims improved cell type-specific GRN inference, which is a key contribution. If the validation datasets are not properly matched to the cell types being predicted, the results may reflect general regulatory features rather than cell type-specific improvements. The composite scoring approach needs transparency to be reproducible and interpretable.
- **Resolution test** Describe the exact formula for combining factors into cell type-specific potentials, including all normalization steps. Detail how cell type labels are assigned to ChIP-seq, HiC, and eQTL datasets, and whether any deconvolution or cell type enrichment analysis was performed. Provide a sensitivity analysis showing how results change with different weighting schemes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "LINGER allows for the estimation of TF activity solely from bulk or single-cell gene expression data" (Abstract) and the two examples in Fig 6
- **Evidence pointer** Fig 6A-E; Methods "Identify driver regulators based on transcription profiles"
- **Concern** The TF activity estimation relies on AUCell with target gene sets derived from the GRN. The text does not specify how the target gene set size (top 1000) was chosen, whether results are robust to this choice, or how AUCell scores are normalized across samples. In the AML example, the p-value for FOXN1 activity difference is reported as 0.035, which is marginally significant, and the text does not report multiple testing correction across all TFs tested. The survival analysis is described as showing higher survival probability for high FOXN1 activity, but no hazard ratios, confidence intervals, or p-values are provided. The TCR stimulation example reports consistency with proteomics data but does not provide quantitative comparison metrics.
- **Why it matters** TF activity estimation is presented as a key practical application. The statistical evidence for the two examples is weak and incomplete. Without proper multiple testing correction and effect size reporting, the findings may not be reproducible or may represent false positives. The survival analysis claim requires proper statistical reporting.
- **Resolution test** Report the number of TFs tested in each analysis and apply appropriate multiple testing corrections. Provide hazard ratios, confidence intervals, and p-values for the survival analysis. For the TCR example, provide quantitative measures of agreement between TF activity and proteomics data. Perform a sensitivity analysis on the target gene set size.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "the LINGER software is publicly available to the scientific community" (Introduction)
- **Evidence pointer** Not specified in the provided text
- **Concern** The manuscript states that LINGER software is publicly available, but no URL, repository name, or accession code is provided in the text. The methods section describes the algorithm but lacks implementation details such as the deep learning framework used, hyperparameter values, training time, and computational resource requirements. The preprocessing steps for the external bulk data and single-cell data are not fully specified.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without access to the code and detailed implementation parameters, other researchers cannot apply LINGER to their own data or verify the reported results. The lack of computational resource information also prevents assessment of practical usability.
- **Resolution test** Provide a public repository URL with documented code, a detailed description of all hyperparameters and their selection criteria, and a statement of computational requirements. Include a step-by-step tutorial or example dataset to demonstrate usage.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "LINGER reveals the complex regulatory landscape of GWAS traits" (Results section title) and the IBD analysis
- **Evidence pointer** Fig 5A-G; Methods "LINGER reveals the complex regulatory landscape of GWAS traits"
- **Concern** The GWAS analysis identifies cell types and TFs relevant to IBD, but the text does not provide a comparison with existing methods for cell type enrichment analysis of GWAS data, such as sc-linker, scDRS, or LDSC applied to single-cell data. The claim of "complex regulatory landscape" is supported by a single disease example. The statistical framework for defining "trait-relevant cell types" relies on comparing top 100 expressed TFs versus random TFs, but the text does not explain why this specific comparison is appropriate or how the random selection is performed.
- **Why it matters** The GWAS application is presented as a major contribution, but without benchmarking against existing approaches, it is unclear whether LINGER provides unique insights or simply recapitulates known biology. The single disease example limits generalizability claims.
- **Resolution test** Compare LINGER's cell type and TF prioritization with at least one established method for the same IBD dataset. Apply the analysis to at least one additional GWAS trait to demonstrate generalizability. Provide a detailed description of the random TF selection procedure and justify the choice of top 100 expressed TFs.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract claims "2–3 fold higher accuracy" but the Introduction states "about 2-fold more accuracy than a random predictor" for the AUPR ratio. These numbers are inconsistent and the basis for the "2-3 fold" claim is unclear.
- **Required correction** Reconcile the accuracy claims between abstract and introduction, and specify the exact metric and comparison baseline for each claim.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Methods "TF importance score"
- **Issue** The subsection "TF importance score" is listed but the description is incomplete, ending with "There are steps to generate the TF importance score:" without detailing the steps.
- **Required correction** Complete the description of the TF importance score calculation, including all formulas and algorithmic steps.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Fig 2A
- **Evidence pointer** Fig 2A
- **Issue** The text reports a p-value of 569.11 on the -log10 scale for the comparison between scNN and Elastic Net, but does not report the actual PCC values or the number of genes tested.
- **Required correction** Report the mean PCC values for both models and the number of genes included in the comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "LINGER improves the cellular population GRN inference"
- **Evidence pointer** Fig 2F
- **Issue** The text states "4.37% of genes are cis-regulation dominant, while 2.00% are trans-regulation dominant" but does not explain the criteria for dominance or the statistical test used.
- **Required correction** Define the criteria for cis- or trans-regulation dominance and describe the statistical test used to determine significance.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods "PBMC 10x data"
- **Evidence pointer** Methods "PBMC 10x data"
- **Issue** The description of pseudobulk generation is unclear. The text states "randomly selecting square root of the number of cells in each cell type and averaged the expression levels and chromatin accessibility of 100 nearest cell" but does not explain what "100 nearest cell" refers to or how the averaging is performed.
- **Required correction** Clarify the pseudobulk generation procedure, including the definition of "nearest cells" and the averaging method.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion is largely a restatement of the results without critical evaluation of limitations or comparison with alternative approaches.
- **Required correction** Add a critical discussion of method limitations, potential biases in validation data, and how LINGER compares with other recent GRN inference methods.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Completeness
- **Affected element** References
- **Evidence pointer** Not specified
- **Issue** The reference list is not provided in the supplied text, making it impossible to verify the appropriateness of citations.
- **Required correction** Ensure all claims are properly cited and the reference list is complete.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "LINGER reveals the complex regulatory landscape of GWAS traits"
- **Evidence pointer** Fig 5D
- **Issue** The text reports p-values for overlap significance but does not describe the statistical test used or how the background distribution was generated.
- **Required correction** Describe the statistical test for overlap significance and the procedure for generating the background distribution.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods "GRN inference by Shapley value"
- **Evidence pointer** Methods "GRN inference by Shapley value"
- **Issue** The description of Shapley value computation is brief and does not specify the approximation method used, which is important for computational feasibility.
- **Required correction** Describe the Shapley value approximation algorithm and its computational complexity.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "LINGER improves the cell type specific GRN inference"
- **Evidence pointer** Fig 3D, 3H, 3K
- **Issue** The text reports p-values for comparisons with SCENIC+ but does not specify the number of test cases or the exact metric used for F1 score calculation.
- **Required correction** Report the number of TF-RE or RE-TG pairs used in each comparison and describe the F1 score calculation protocol.

## Risk / unsupported claims
- The claim of "2–3 fold higher accuracy over existing methods" is not quantitatively substantiated in the provided text.
- The claim that LINGER "reveals the complex regulatory landscape of GWAS traits" is based on a single disease example without benchmarking against existing methods.
- The claim that TF activity estimation identifies "driver regulators" is supported by two examples with weak statistical evidence.
- The generalizability of LINGER to tissues beyond PBMCs and cell lines is not demonstrated.
- The statement that "LINGER provides a comprehensive tool" is not supported by evidence of usability, scalability, or robustness across diverse datasets.
- The claim that lifelong learning "mitigates the challenge of limited data" is not directly tested through ablation studies comparing with and without external data pretraining.
- The manuscript does not provide evidence that the manifold regularization based on motif matching significantly contributes to performance beyond the neural network architecture alone.