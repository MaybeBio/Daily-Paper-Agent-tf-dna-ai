## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific and technical soundness of the proposed method, validation approach, and claims; no assessment of code functionality or server availability beyond what is described
- **Shared manuscript claim summary** The authors present TransPilot, a web server that identifies key transcription factors (TFs) regulating differentially expressed genes (DEGs) by correlating ranked and direction-annotated TF-target sets with ranked DEG lists using weighted Kendall's tau rank correlation. TF-target sets are constructed from TF binding sites (TFBSs) predicted by an artificial neural network (ANN) trained on log-likelihood ratio (LLR) array features. Direction of regulation is inferred from expression correlation in a reference transcriptome dataset. The method is benchmarked on a macrophage polarization dataset and tissue-specific datasets from GTEx.
- **Visible evidence base** Full text including methods, results, figures referenced (Figs 1-5), supplementary files referenced (Files 1-6), and data availability statements
- **Missing materials affecting confidence** Supplementary files (Files 1-6) not provided; figure content not visible; no detailed hyperparameter or architecture description for the ANN; no details on the reference transcriptome dataset preprocessing; no comparison with FLAVER on identical benchmarks; no information on server implementation, runtime, or scalability

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful extension of the FLAVER approach by incorporating directionality of TF-target regulation and an ANN-based TFBS prediction method. The core statistical framework is built on established rank correlation methods, and the authors provide a reasonable motivation for the imputation strategy. However, the validation is limited in scope, lacks rigorous comparison with existing tools on identical benchmarks, and the reported performance metrics are not sufficient to establish superiority or even equivalence to current state-of-the-art methods. The manuscript would benefit from more systematic benchmarking, clearer description of the ANN architecture and training, and a more critical discussion of limitations.
- **Who would be interested in the results, and why** Researchers in regulatory genomics and transcriptomics who need to infer key TFs from differential expression data. The web server format makes the tool accessible to experimental biologists without programming expertise. The direction-annotated TF-target sets may be of interest to those studying both activation and repression in gene regulatory networks.
- **Major strengths** The motivation for incorporating directionality of TF-target regulation is clear and addresses a real gap in existing tools. The use of weighted Kendall's tau with a custom weighting function is statistically sound and appropriate for emphasizing end-ranked genes. The imputation strategy for genes lacking TFBSs is a thoughtful solution to a practical problem. The authors provide a web server implementation, which enhances usability.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (validation scope), R1-M2 (ANN description), R1-M3 (comparison with FLAVER), R1-M4 (statistical assumptions)
- **Assessment against Nature-style criteria** **Originality**: Moderate. The combination of ANN-based TFBS prediction with direction-annotated rank correlation is novel, but the underlying components are established. **Scientific importance**: Moderate. The tool addresses a practical need, but the demonstrated improvements over existing methods are not compelling. **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to bioinformaticians and computational biologists; the presentation is technical and assumes familiarity with rank correlation statistics and TFBS prediction. **Technical soundness**: Partially established. The statistical framework is sound, but the ANN training details and validation methodology have gaps. **Readability for nonspecialists**: Below average. The methods section is dense and would be challenging for experimental biologists to follow without significant background in computational methods.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding validation rigor and methodological transparency.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors claim the server was benchmarked on a macrophage polarization dataset and outperformed competitors (Section 3.2).
- **Evidence pointer** Section 3.2, Fig. 3, File 5
- **Concern** The benchmarking is limited to a single real-world dataset. The comparison with competitors (SCENIC, VIPER, ChEA3) is based on pairwise counts of how often the target TF ranked better, but no statistical significance testing is reported for these comparisons beyond a paired Z-test mentioned in Methods. The choice of 27 target TFs from literature is subjective, and no sensitivity analysis is provided for this selection. The synthetic dataset experiments (Section 3.2, Fig. 4) only test TransPilot itself and do not include any competitor comparison.
- **Why it matters** A single benchmark dataset is insufficient to establish generalizable performance. The lack of statistical rigor in the comparison undermines the claim of superiority. Without competitor comparison on synthetic data, it is unclear whether the observed performance differences are due to the method itself or to dataset-specific effects.
- **Resolution test** Provide benchmarking on multiple independent datasets (e.g., different cell types, disease states, species). Report effect sizes and confidence intervals for the comparisons with competitors. Include competitor methods in the synthetic data experiments where feasible, or justify their exclusion more rigorously.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors state that an ANN was trained using features derived from an LLR array model to identify TFBSs (Abstract, Section 2.2).
- **Evidence pointer** Section 2.2, Fig. 1C
- **Concern** The description of the ANN is insufficient for reproducibility. The architecture (number of layers, hidden units, activation functions), training procedure (loss function, optimizer, regularization), and the exact construction of the LLR feature matrix are not fully specified. The relationship between the LLR feature matrix and the one-hot encoding is mentioned but not formalized. The threshold for classifying a site as a TFBS (YANN > 0.5) is stated, but no information is given on how this threshold was chosen or validated.
- **Why it matters** Without a complete description of the ANN and feature construction, the method cannot be reproduced or independently validated. The choice of threshold directly affects the composition of TF-target sets and therefore all downstream results.
- **Resolution test** Provide a complete specification of the ANN architecture, training details, and feature construction. Include a sensitivity analysis for the classification threshold. Make the trained models and training data available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors state that TransPilot incorporates theoretical enhancements and software upgrades over FLAVER (Section 1, last paragraph).
- **Evidence pointer** Section 1, Section 2.3
- **Concern** The manuscript does not provide a direct comparison between TransPilot and FLAVER on the same datasets. The claimed enhancements (direction annotation, imputation) are described, but their individual contributions to performance are not quantified. It is unclear whether the improvements are due to the direction annotation, the imputation, the ANN-based TFBS prediction, or a combination of these factors.
- **Why it matters** The manuscript positions TransPilot as an improvement over FLAVER, but without an ablation study or direct comparison, this claim is not supported. Understanding which components contribute to performance is essential for users to make informed choices between tools.
- **Resolution test** Run both TransPilot and FLAVER on the same benchmark datasets and report comparative results. Perform an ablation study by running TransPilot with and without direction annotation, with and without imputation, and with one-hot versus LLR encoding.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** The authors state that the weighted Kendall's tau statistic is used to test the significance of correlation between TF-target set ranks and DEG list ranks (Section 2.3).
- **Evidence pointer** Section 2.3, Equations (4)-(7)
- **Concern** The statistical properties of the weighted Kendall's tau under the null hypothesis are not discussed. The limiting distribution is stated to approach N(0,1) as n approaches infinity, but the rate of convergence and the adequacy of this approximation for realistic gene set sizes (thousands of genes) are not addressed. The imputation of random LLR values for genes lacking TFBSs introduces stochasticity into the analysis, but it is unclear how this affects the null distribution and whether multiple imputations are needed to account for this variability.
- **Why it matters** If the null distribution is not well-calibrated, the reported p-values and FDR values may be systematically biased, leading to incorrect conclusions about which TFs are significant. The stochastic imputation could also produce different results on repeated runs, which is problematic for reproducibility.
- **Resolution test** Provide simulation studies to assess the type I error rate and power of the test under realistic conditions. Address the impact of imputation stochasticity, either by demonstrating that results are stable across multiple runs or by recommending a multiple imputation approach.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, Results section
- **Issue** The abstract states the method identifies key TFs but does not specify the input requirements (e.g., species, genome build, promoter definition) or the output format.
- **Required correction** Add a brief statement on input requirements and output format to the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The reference transcriptome dataset from the Human Protein Atlas is mentioned, but the specific version, preprocessing steps, and how expression correlation was computed are not described.
- **Required correction** Provide details on the reference dataset version, normalization, and correlation computation method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1, Fig. 2B
- **Issue** The transcriptional regulatory network in Fig. 2B is described as constructed from seven TFs, but the criteria for selecting these seven TFs from the larger set of significant TFs are not stated.
- **Required correction** Clarify the selection criteria for the TFs shown in the network figure.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.3
- **Evidence pointer** Section 3.3
- **Issue** The tissue-specific analysis uses an FDR threshold of 1e-20, which is extremely stringent. The rationale for this threshold is not provided.
- **Required correction** Justify the choice of FDR threshold or discuss its implications for the number of TFs identified.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2, Equation (2)
- **Issue** The definition of the LLR feature matrix is not fully clear. The equation is referenced but not shown in the text provided.
- **Required correction** Ensure the equation is fully defined and the construction of the feature matrix is explained step by step.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Usability
- **Affected element** Section 4
- **Evidence pointer** Section 4, last paragraph
- **Issue** The authors recommend users submit DEG lists of 2000-3000 genes, but no guidance is given on how to handle smaller or larger lists.
- **Required correction** Provide guidance on the expected behavior for different list sizes and any minimum requirements.

## Risk / unsupported claims
- The claim that TransPilot outperforms SCENIC, VIPER, and ChEA3 is not statistically substantiated; the reported pairwise counts do not include confidence intervals or effect sizes.
- The claim of "theoretical enhancements" over FLAVER is not supported by a direct comparison or ablation study.
- The performance metrics for the ANN (accuracy, sensitivity, specificity, precision, F1) are reported without a clear definition of the ground truth or the evaluation protocol.
- The claim that the imputation method avoids artificial bias is not fully supported; the discussion provides arguments but no empirical evidence.
- The biological relevance of the TFs identified in the tissue-specific analysis is based on literature annotation, but the completeness and objectivity of this annotation are not assessed.
- The statistical properties of the weighted Kendall's tau with the proposed weighting function and imputation are not established under realistic null conditions.