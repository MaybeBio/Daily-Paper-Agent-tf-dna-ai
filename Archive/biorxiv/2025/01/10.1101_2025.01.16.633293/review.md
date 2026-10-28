## Review setup
- **Input scope** Full manuscript text, including abstract, main text, results, discussion, methods, data and code availability statements.
- **Assessment boundary** Scientific and technical soundness of the proposed method, validity of benchmarking claims, biological interpretability claims, and reproducibility based on the provided manuscript text. No supplementary figures, tables, or code were inspected beyond what is described in the text.
- **Shared manuscript claim summary** The authors present scTFBridge, a deep generative model for single-cell multi-omics integration and gene regulatory network (GRN) inference. The model disentangles latent spaces into modality-shared and modality-private components using mutual information minimization and contrastive learning, incorporates TF-motif binding priors to constrain the shared latent space, and uses SHAP-based explainability to derive cis- and trans-regulatory scores. The authors claim consistent outperformance over baseline methods in both cis- and trans-regulation inference tasks across multiple datasets.
- **Visible evidence base** Main text figures referenced (Figs. 1-6), methods section, data availability statements, and benchmark descriptions. Supplementary figures and tables are referenced but not provided for inspection.
- **Missing materials affecting confidence** Supplementary figures (S1-S6), supplementary tables (1-3), benchmark implementation details, baseline method configurations, hyperparameter settings per dataset, and the actual code repository were not available for review. These are essential for verifying the benchmarking claims and reproducibility.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important problem: inferring gene regulatory networks from paired single-cell multi-omics data. The proposed architecture, combining disentangled VAEs with TF-motif priors and SHAP-based interpretability, is conceptually appealing and well-motivated. However, the current manuscript provides insufficient technical detail to assess the validity of the core claims. Several methodological choices are under-specified, the benchmarking protocol lacks critical controls, and the biological validation is largely descriptive. The central claim of "consistent outperformance" over baselines cannot be fully evaluated from the provided material. The work has potential, but the evidence as presented does not yet establish the case.
- **Who would be interested in the results, and why** Computational biologists developing single-cell multi-omics integration methods; researchers studying gene regulatory networks, particularly those interested in cis-regulatory mechanisms; and experimentalists seeking interpretable tools for identifying cell-type-specific regulatory elements and disease susceptibility genes. The disentanglement approach and the use of TF-motif priors may also interest the deep learning for genomics community.
- **Major strengths** 1. The problem is well-motivated and addresses a real gap in single-cell multi-omics GRN inference. 2. The architecture is thoughtfully designed, with a clear rationale for each component (disentanglement, contrastive alignment, TF-motif regularization, SHAP-based scoring). 3. The use of external gold-standard datasets (eQTL, ChIP-seq, pcHi-C) for benchmarking is appropriate and strengthens the evaluation. 4. The application to lung cancer susceptibility data demonstrates potential translational relevance.
- **Major Concerns** 
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that scTFBridge "consistently outperformed baseline methods in both cis- and trans-regulation inference tasks."
- **Evidence pointer** Results sections on benchmarking (Figs. 4 and 5), Methods section on benchmarking.
- **Concern** The benchmarking protocol is critically under-specified. The authors do not describe how baseline methods (PCC, Distance, Random, SCENIC+, GENIE3, PIDC) were configured, whether hyperparameters were tuned per dataset, how many random seeds were used, or whether statistical significance of performance differences was assessed. The AUPR ratio and AUC metrics are described, but the authors do not report confidence intervals or variance across cross-validation folds. Without this information, the claim of "consistent outperformance" cannot be verified. Furthermore, the choice of baselines is incomplete: recent state-of-the-art methods for single-cell GRN inference (e.g., SCENIC+, LINGER, CellOracle) should be included or justified for exclusion.
- **Why it matters** The central contribution of the paper is the claimed superiority of scTFBridge over existing methods. If the benchmarking is not rigorous, the core claim is unsupported, and the method's utility is not established.
- **Resolution test** Provide a detailed benchmarking protocol including: exact baseline configurations, hyperparameter tuning procedure, number of random seeds, statistical tests for performance differences (e.g., paired bootstrap or Wilcoxon signed-rank test across folds), and inclusion of additional state-of-the-art baselines. Report mean and variance of metrics across folds.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the CMI module "minimizes mutual information" between latent variables and that the CLUB estimator provides an upper bound.
- **Evidence pointer** Methods section, Framework of scTFBridge.
- **Concern** The description of the mutual information minimization is mathematically incomplete. The authors state that the CLUB estimator is used but do not provide the exact form of the estimator used, how the conditional distribution p(y|x) is parameterized, or how the minimization is integrated into the overall loss function. The equations referenced (Eqs. 10-17) are not fully derived in the text. Additionally, the claim that minimizing MI between shared and private representations is sufficient for disentanglement is not theoretically justified; recent work has shown that MI minimization alone may not guarantee disentanglement without additional structural constraints.
- **Why it matters** The disentanglement mechanism is a core contribution of the paper. If the MI minimization is not rigorously described and theoretically justified, the validity of the disentanglement claim is questionable.
- **Resolution test** Provide a complete mathematical derivation of the MI estimator, its integration into the loss function, and a theoretical or empirical justification for why MI minimization leads to meaningful disentanglement in this context. Include ablation studies showing the effect of the CMI module on downstream performance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological interpretability
- **Claim pointer** The authors claim that the TF-motif prior "enhances biological interpretability" and that the shared latent variables "correspond to specific TFs."
- **Evidence pointer** Results sections on disentangled embedding learning and lung cancer susceptibility; Methods section on TF-motif regularization.
- **Concern** The biological validation of the TF-motif prior is weak. The authors show that shared embeddings are enriched for promoter peaks and that certain TFs are identified in specific cell types, but they do not demonstrate that the latent variables actually correspond to the intended TFs in a quantitative manner. For example, do the learned TF latent variables correlate with measured TF expression or chromatin binding? The claim that ESR, TCF7, and SOX4 are cell-type-specific regulators is based on visual inspection of rankings, but no statistical test is provided. The lung cancer analysis is also descriptive; the authors do not validate the predicted regulatory relationships experimentally or against independent datasets.
- **Why it matters** The interpretability claim is a key differentiator of scTFBridge. Without rigorous validation that the latent variables capture genuine TF regulatory activity, the biological utility of the method is not established.
- **Resolution test** Provide quantitative validation of TF latent variables, e.g., correlation with TF expression or ChIP-seq binding in matched cell types. Include statistical tests for cell-type specificity of identified TFs. Validate predicted regulatory relationships in the lung cancer dataset against independent experimental data or at least against known literature-curated interactions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that "All source code utilized in this study is publicly available on GitHub."
- **Evidence pointer** Code availability section.
- **Concern** The code repository was not accessible for review. Additionally, the manuscript does not provide sufficient implementation details to reproduce the method independently. Key hyperparameters (e.g., learning rate schedule, batch size, latent dimensionality, number of layers) are only partially described. The preprocessing pipeline is described at a high level but lacks specific parameters (e.g., normalization method, filtering thresholds). The exact TF-motif scoring procedure using HOMER is not described in sufficient detail.
- **Why it matters** Reproducibility is a fundamental requirement for computational methods. Without access to code and detailed implementation parameters, the method cannot be independently verified or applied by other researchers.
- **Resolution test** Ensure the code repository is publicly accessible and well-documented. Provide a complete list of hyperparameters for each dataset, a detailed preprocessing pipeline, and a step-by-step description of the TF-motif scoring procedure.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that scTFBridge "provides an efficient computational framework for exploring phenotype-specific gene regulatory mechanisms."
- **Evidence pointer** Discussion section.
- **Concern** While the method is applied to three datasets, the novelty of the biological findings is limited. The identification of cell-type-specific TFs in BMMCs and RA is largely confirmatory of known biology. The lung cancer analysis identifies NRG1 as a susceptibility gene, but this is already known from previous GWAS studies. The authors do not demonstrate that scTFBridge uncovers genuinely novel regulatory mechanisms that could not be identified by existing methods.
- **Why it matters** For a methods paper, the biological applications serve as validation. If the applications do not yield new biological insights, the added value of the method over existing approaches is less clear.
- **Resolution test** Either demonstrate a novel biological finding enabled by scTFBridge that is validated experimentally or through independent data, or temper the claims of biological discovery and focus the paper more narrowly on the methodological contribution.

- **Minor Comments** 
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1a-g
- **Issue** The figure is described in the text but not provided. The description is dense and difficult to follow without the visual.
- **Required correction** Ensure the figure is self-explanatory with clear labels for each panel. Consider adding a schematic of the overall architecture in a single panel.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, TF-motif scoring
- **Evidence pointer** Methods section, Framework of scTFBridge
- **Issue** The description of how HOMER is used to scan REs for TF motifs is incomplete. The specific parameters (e.g., motif score threshold, background model) are not provided.
- **Required correction** Provide the exact HOMER command and parameters used for motif scanning.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 3e
- **Evidence pointer** Results section on RA analysis
- **Issue** The chi-squared test is mentioned but the contingency table and effect size are not reported.
- **Required correction** Report the contingency table, chi-squared statistic, degrees of freedom, and p-value.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations is brief and does not address potential failure modes of the method, such as sensitivity to the choice of TF list or the impact of motif database completeness.
- **Required correction** Expand the limitations section to discuss these potential issues and their implications.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The GEO accession for the lung dataset (GSE2414468) appears to have a typo (likely GSE241446 or similar). This needs to be verified.
- **Required correction** Verify and correct the GEO accession number.

- **Technical failings that need to be addressed before the case is established** R1-M1 (benchmarking rigor), R1-M2 (MI formulation), R1-M3 (biological validation), R1-M4 (reproducibility). These are blocking concerns that must be resolved before the core claims of the paper can be accepted.
- **Assessment against Nature-style criteria** 
  - Originality: The combination of disentangled VAEs with TF-motif priors and SHAP-based interpretability for GRN inference is a novel contribution. However, the individual components are well-established, and the novelty lies primarily in their integration.
  - Scientific importance: The problem of GRN inference from single-cell multi-omics is of high importance. If the method is rigorously validated, it could be a valuable tool. However, the current evidence does not yet demonstrate a clear advantage over existing methods.
  - Interdisciplinary readership: The work is likely to appeal to computational biologists, bioinformaticians, and potentially experimentalists in genomics. The writing is generally accessible, but the methods section assumes significant familiarity with deep generative models and information theory.
  - Technical soundness: The technical soundness cannot be fully assessed due to under-specification of the method and benchmarking. The mathematical formulation of the MI minimization is incomplete, and the benchmarking protocol lacks critical controls.
  - Readability for nonspecialists: The abstract and introduction are clear and accessible. The results and methods sections are more technical and may be challenging for readers without a computational background. The figures, if provided, would likely aid comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising approach, but the core claims of consistent outperformance and biological interpretability are not sufficiently supported by the evidence provided. The blocking concerns must be addressed before the case is established.

## Risk / unsupported claims
- The claim of "consistent outperformance" over baseline methods is unsupported due to the under-specified benchmarking protocol.
- The claim that latent variables "correspond to specific TFs" is not quantitatively validated.
- The claim that scTFBridge "uncover[s] cell-type-specific susceptibility genes" in lung cancer is not validated against independent experimental data.
- The claim that the CMI module effectively disentangles latent spaces is not supported by ablation studies or theoretical justification.
- The biological findings in BMMC and RA datasets are largely descriptive and not statistically validated.