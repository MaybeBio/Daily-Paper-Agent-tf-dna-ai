## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, declarations, figure legends)
- **Assessment boundary** Scientific claims, methodological soundness, statistical approach, evidence quality, and reproducibility as presented in the provided text
- **Shared manuscript claim summary** The authors present craTEs, a statistical model that infers TE subfamily cis-regulatory activity from protein-coding gene expression data alone. They validate it against CRISPRi perturbation datasets, estimate a ~200kb range of TE cis-regulatory influence, and identify TF-TE regulatory relationships in hESCs.
- **Visible evidence base** Abstract, full introduction, results narrative (without figures), discussion, methods, data availability statements
- **Missing materials affecting confidence** All figures and supplementary figures, figure legends, additional files 1 and 2, exact numerical results, validation statistics, code implementation details

## Reviewer

### Overall assessment
The manuscript presents a conceptually interesting statistical framework for inferring TE subfamily cis-regulatory activity from RNA-seq data. The core idea, that coordinated cis-regulatory effects of TE subfamilies can be estimated from gene expression changes without requiring TE-derived transcript quantification, is novel and potentially useful. However, the evidence as presented is incomplete. The results section is written as a narrative without the supporting figures, making it impossible to evaluate the actual performance of the model, the validity of the validation approach, or the robustness of the conclusions. The methods section contains several ambiguities and potential statistical issues that need clarification. The claim of a ~200kb cis-regulatory range is based on cross-validation across four datasets, but the details of this analysis are not fully described. The biological conclusions, while interesting, rest on the validity of the model, which cannot be fully assessed from the provided material.

### Who would be interested in the results, and why
Researchers studying transposable element biology, cis-regulatory evolution, and gene regulatory networks would find this work relevant. The claim that TE cis-regulatory activity can be inferred from standard RNA-seq data without specialized TE-aware pipelines could be practically useful for the broader genomics community. Those interested in the role of TEs in pluripotency and early development would also find the biological results of interest. The methodological contribution, if validated, could enable reanalysis of existing large-scale perturbation datasets.

### Major strengths
1. The conceptual advance of inferring TE cis-regulatory activity from gene expression alone, without requiring TE-derived reads, is genuinely novel and addresses a real limitation in the field.
2. The model is grounded in a clear biological hypothesis (TE subfamilies as coordinated cis-regulatory modules) and builds on established statistical frameworks (MARA).
3. The validation strategy using CRISPRi perturbation datasets with known targets provides a sensible ground truth approach.
4. The application to a large-scale perturbation dataset (441 transgenes) is ambitious and could yield useful resources for the community.
5. The authors are transparent about data availability and provide code through a reproducible platform.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that craTEs "accurately identifies cis-regulatory TE subfamilies from RNA-seq data alone" and "outperforms enrichment approaches based on differential expression analyses."
- **Evidence pointer** Results section, figures 1-4 (not provided)
- **Concern** The results section is presented entirely as narrative text without the accompanying figures. No numerical results, effect sizes, confidence intervals, or performance metrics are provided in the text. The reader cannot evaluate the actual performance of craTEs, the magnitude of the effects detected, or the statistical evidence supporting the claims.
- **Why it matters** The central claims of the manuscript rest on the empirical performance of the model. Without access to the figures and their associated statistics, the validity of the model cannot be assessed. This is a fundamental barrier to evaluation.
- **Resolution test** Provide all figures with complete legends, including numerical results in the text or figure legends. Report effect sizes, confidence intervals, and adjusted p-values for the key validation experiments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The model estimates differences in TE cis-regulatory activity between two conditions using a linear regression framework, with significance tested against the null hypothesis that the activity difference is zero.
- **Evidence pointer** Methods section, "cis-regulatory activity estimation for TE subfamilies (craTEs)"
- **Concern** The statistical properties of the estimator are not fully described. The model uses ordinary least squares on a design matrix N that is likely to be highly collinear (many TE subfamilies, many genes with overlapping cis-regulatory windows). The authors mention that MARA uses ridge regression to address collinearity, but it is unclear whether craTEs uses ridge regression or OLS. If OLS is used, the estimates may be unstable and the standard errors unreliable. If ridge regression is used, the significance testing framework needs to be described in detail.
- **Why it matters** The validity of all downstream biological conclusions depends on the statistical reliability of the activity estimates. Collinearity in the design matrix is a known issue in this type of analysis and can lead to spurious findings.
- **Resolution test** Clearly state whether ridge regression or OLS is used. If ridge regression, describe how the regularization parameter is chosen, how significance is computed (e.g., via a test on the ridge coefficients), and how the bias-variance tradeoff is handled. Provide simulation or analytical results demonstrating the false positive rate control of the testing procedure.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation adequacy
- **Claim pointer** The authors validate craTEs using CRISPRi datasets targeting LTR5-Hs/SVA in naïve hESCs and LTR2B in K562 cells, and claim that craTEs correctly identifies these subfamilies as significantly less active upon repression.
- **Evidence pointer** Results section, figure 1C
- **Concern** The validation approach relies on the assumption that CRISPRi-mediated repression of a TE subfamily abolishes its cis-regulatory effect. However, the extent of repression, the fraction of subfamily members effectively silenced, and the potential off-target effects are not discussed. Moreover, the validation only demonstrates that craTEs can detect large, engineered perturbations. It does not establish that the model can reliably detect endogenous cis-regulatory activity differences in unperturbed conditions or in response to TF overexpression, which is the primary application in the perturbome analysis.
- **Why it matters** The validation establishes the model's ability to detect strong, targeted perturbations. The subsequent application to TF overexpression experiments involves much subtler effects, and the validation does not demonstrate that the model has sufficient sensitivity and specificity in this regime.
- **Resolution test** Provide quantitative details on the CRISPRi validation, including the number of genes affected, the magnitude of expression changes, and the statistical power. Consider additional validation using datasets with known endogenous TE cis-regulatory effects, or simulations that mimic the expected effect sizes in the perturbome analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Confounding factors
- **Claim pointer** The authors claim that "differences in expression at protein-coding genes alone are sufficient to estimate the magnitude and significance of TE-contributed cis-regulatory activities."
- **Evidence pointer** Abstract, Results section
- **Concern** The model assumes that the presence of TE subfamily members within a cis-regulatory window is a sufficient predictor of cis-regulatory influence. However, many TE subfamily members are likely to be inactive due to mutations, epigenetic silencing, or lack of appropriate TF binding sites. The model does not account for the fraction of potentially active elements within a subfamily. Additionally, the model does not control for other sources of cis-regulatory variation, such as non-TE enhancers, promoter architecture, or chromatin state, which could confound the association between TE presence and gene expression.
- **Why it matters** If the model attributes expression variation to TE subfamilies that is actually driven by other correlated genomic features, the estimated activities will be biased and the biological conclusions potentially misleading.
- **Resolution test** Discuss how the model handles inactive TE copies. Consider incorporating additional covariates (e.g., chromatin state, non-TE enhancer density) into the model as controls. Perform sensitivity analyses to assess the robustness of the results to these potential confounders.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The authors conclude that "TE subfamilies can be split into truly regulatorily active versus inactive fractions based on additional information such as matched epigenomic data" and that "TF binding may better predict TE cis-regulatory activity than differences in histone marks."
- **Evidence pointer** Results section, figure 4
- **Concern** The comparison between TF binding and histone marks as predictors of cis-regulatory activity is based on a limited set of experiments (KLF4 and ZNF611 overexpression) and a specific set of TE subfamilies. The conclusion that TF binding is a better predictor may not generalize. Moreover, the analysis splits subfamilies into functional and non-functional fractions based on overlap with epigenomic features, but the criteria for defining "functional" are not fully described, and the circularity of using the same data to define and validate the fractions is a concern.
- **Why it matters** The claim about TF binding versus histone marks has implications for how researchers should prioritize epigenomic data in future studies. If the conclusion is based on a narrow or circular analysis, it may be misleading.
- **Resolution test** Provide a more detailed description of the functional/non-functional split criteria. Acknowledge the limited scope of the comparison. Consider additional datasets or a more systematic analysis across multiple TFs and TE subfamilies.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that the code is available on the Renku platform and that data are deposited in GEO and Zenodo.
- **Evidence pointer** Data availability section
- **Concern** While the data and code availability statements are commendable, the manuscript does not provide a detailed description of the computational pipeline, including software versions, parameters, and intermediate processing steps. The methods section for RNA-seq analysis is brief, and the exact commands or workflow are not provided. This limits the reproducibility of the results.
- **Why it matters** Reproducibility is a core requirement for computational biology manuscripts. Without a detailed pipeline description, independent verification of the results is difficult.
- **Resolution test** Provide a more detailed methods section, including software versions, parameters, and a step-by-step description of the analysis pipeline. Consider providing a containerized workflow or a detailed README on the code repository.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Results
- **Evidence pointer** Abstract, "Results" section
- **Issue** The abstract states that the model works "even in contexts where TE-derived transcription fails to do so," but this point is not clearly explained in the results. The distinction between TE-derived transcription and TE cis-regulatory activity on nearby genes is conceptually important and should be clarified.
- **Required correction** Add a brief explanation in the results or introduction clarifying the difference between TE transcription and TE cis-regulatory effects on neighboring genes, and why the model does not require the former.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Methods, "cis-regulatory activity estimation"
- **Evidence pointer** Methods section
- **Issue** The term "cis-regulatory activity" is used to describe a regression coefficient, but the units and interpretation are not immediately clear. The authors state that a positive value indicates an "enhancer-like" effect, but the magnitude of the coefficient is not interpreted in biological terms.
- **Required correction** Provide a brief interpretation of the units of the activity coefficient, perhaps with an example (e.g., "a coefficient of 1 implies a 2-fold increase in expression for each additional TE copy").

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, figure 1C
- **Evidence pointer** Results section
- **Issue** The text mentions "six TE subfamilies with significant differences" but does not report the number of subfamilies tested, the multiple testing correction method, or the threshold used.
- **Required correction** Report the total number of subfamilies tested, the multiple testing correction method, and the significance threshold in the results or methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods, "Computing the regulatory susceptibilities"
- **Evidence pointer** Methods section
- **Issue** The merging of fragmented TE annotations is mentioned but not described in detail. The criteria for merging (distance threshold, overlap requirement) are not specified.
- **Required correction** Provide a detailed description of the TE merging procedure, including the specific parameters used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, figure 3
- **Evidence pointer** Results section
- **Issue** The hierarchical clustering analysis is described briefly, but the distance metric, linkage method, and how clusters were defined are not stated.
- **Required correction** Specify the clustering parameters in the methods or results.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "Cell culture"
- **Evidence pointer** Methods section
- **Issue** The cell culture section mentions transduction and selection but does not specify the multiplicity of infection, the time of selection, or the number of biological replicates for each experiment.
- **Required correction** Provide these experimental details for reproducibility.

### Technical failings that need to be addressed before the case is established
1. The statistical framework for significance testing in the presence of collinearity needs to be clarified and validated (R1-M2).
2. The validation against CRISPRi datasets needs quantitative detail and a demonstration of sensitivity in the expected effect size regime (R1-M3).
3. The potential confounding from inactive TE copies and other cis-regulatory elements needs to be addressed (R1-M4).
4. The criteria for defining functional versus non-functional TE fractions need to be described and the circularity concern addressed (R1-M5).

### Assessment against Nature-style criteria
- **Originality** The concept of inferring TE cis-regulatory activity from gene expression alone is a novel contribution. The application of a MARA-like framework to TE subfamilies is a creative adaptation. This criterion is met.
- **Scientific importance** The question of how TEs contribute to gene regulation is of broad interest. A reliable computational method to infer TE cis-regulatory activity from standard RNA-seq data would be a useful tool. However, the importance is contingent on the validity of the method, which is not fully established from the provided evidence. This criterion is partially met.
- **Interdisciplinary readership** The work bridges computational biology, genomics, and evolutionary biology. The findings on TF-TE regulatory relationships in hESCs could appeal to developmental biologists. However, the presentation is quite technical and may not be accessible to a broad readership without additional context. This criterion is partially met.
- **Technical soundness** The technical soundness cannot be fully assessed due to missing figures and incomplete methods. The statistical concerns raised above need to be addressed. This criterion is not currently met.
- **Readability for nonspecialists** The introduction and discussion are well-written and accessible. The results section, however, is dense and assumes familiarity with regression-based approaches to gene regulation. The abstract is clear. This criterion is partially met.

### Recommendation posture
Currently not established from the provided evidence. The manuscript presents a promising idea, but the evidence as provided is incomplete. The figures and their associated statistics are essential for evaluation and are not available. The statistical methodology has potential issues that need to be resolved. The authors should be encouraged to resubmit a revised version with complete figures, detailed statistical methods, and additional validation.