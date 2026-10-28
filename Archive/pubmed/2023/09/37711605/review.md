## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided.
- **Assessment boundary** Scientific and technical evaluation of the methods, validation strategy, and claims as presented in the provided text. No assessment of code functionality or reproducibility beyond what is described.
- **Shared manuscript claim summary** The authors present TGPred, a suite of six penalized regression methods (four TF–target gene identification methods combining MSE or Huber loss with Lasso or Elastic Net penalties, and two network-based methods combining MSE or Huber loss with a network penalty) solved via an accelerated proximal gradient descent (APGD) algorithm. They claim improved efficiency over a standard convex solver (CVX), superior performance of ENET-based methods over Lasso-based methods in simulation, and utility for genome-wide TF target prediction and pathway GRN inference, validated on simulated data and real transcriptomic datasets (SND1, gl3, maize B73).
- **Visible evidence base** Simulated data under three settings (general, hierarchical network, Barabasi-Albert network); real data from Populus SND1 overexpression (GSE49911), maize gl3 overexpression (dTALes system), and maize B73 compendium (736 samples); comparisons against CLR, MRNET, and TIGRESS; ROC-style analyses; runtime comparisons between APGD and CVX.
- **Missing materials affecting confidence** Full equations (formulas 1-5 referenced but not fully displayed in the provided text); Supplemental Text S1-S8 and Figures S1-S8 not available for review; detailed parameter settings, grid specifications, and statistical significance testing procedures not fully described; no explicit description of how the "top-ranked" gene lists were thresholded for real data comparisons; no confidence intervals or variance estimates for performance metrics.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant gap in TF target gene prediction by integrating established statistical and machine learning components into a unified framework with an efficient optimization algorithm. The simulation studies are reasonably designed, and the application to real datasets demonstrates practical utility. However, the novelty is incremental, the validation against existing methods is limited in scope, and several technical details are insufficiently described to fully assess robustness and generalizability. The claims of superiority for ENET-based methods and the practical advantages over comparison methods are only partially supported by the evidence presented.

- **Who would be interested in the results, and why** Researchers in plant genomics and systems biology, particularly those studying transcriptional regulation and constructing gene regulatory networks. Computational biologists developing or applying penalized regression methods for regulatory inference would also find the APGD implementation and comparative analyses of interest. The potential application to validating ChIP/DAP-seq results broadens the appeal to molecular biologists working on TF-target relationships.

- **Major strengths**
  1. The integration of multiple loss functions and penalties into a single framework with a unified optimization algorithm is practical and potentially useful.
  2. The APGD algorithm addresses a real computational bottleneck, and the reported speed improvements over CVX are valuable for genome-scale applications.
  3. Validation on multiple real datasets (SND1, gl3, maize B73) demonstrates applicability beyond synthetic benchmarks.
  4. The stability selection approach avoids the difficult problem of choosing optimal tuning parameters, which is a practical advantage.
  5. The manuscript is generally clearly written and the workflow is logically presented.

- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
    - **Axis** Technical soundness of validation
    - **Claim pointer** The authors claim that "ENET-based methods performed better than Lasso-based methods" in simulation and that Huber-ENET and MSE-ENET "outperformed all other methods" on real data.
    - **Evidence pointer** Figures 1, 3A-D; Results section "Validation of the four TF–TG identification methods with SND1 overexpression transcriptomic data" and "Validation of the four TF–TG identification methods with glossy (gl3) overexpression transcriptomic data"
    - **Concern** The performance comparisons rely on TPR calculations and ROC-style analyses, but the manuscript does not describe how the "top-ranked" gene lists were defined or how the number of selected genes was determined for each method. Without a clear, consistent thresholding or ranking criterion, the reported TPRs and comparisons may not be directly comparable across methods. Additionally, no statistical tests (e.g., bootstrap confidence intervals, permutation tests) are provided to assess whether observed differences are significant.
    - **Why it matters** The central claim of the paper is that the proposed methods outperform existing approaches. If the comparison framework is not rigorously defined and statistically grounded, the conclusions are not reliable.
    - **Resolution test** Provide a detailed description of the ranking and thresholding procedure, including how the number of top genes was chosen. Add statistical significance testing (e.g., bootstrap or permutation-based confidence intervals) for TPR differences across methods.

  - **R1-M2** (Blocking: Yes)
    - **Axis** Reproducibility and methodological completeness
    - **Claim pointer** The authors state that "an accelerated proximal gradient descent (APGD) algorithm was developed for the parameter optimization in all six methods" and that it is "equally effective but much faster" than CVX.
    - **Evidence pointer** Methods section "Algorithm to solve the penalized regression models"; Figures S2-S4
    - **Concern** The APGD algorithm is described only at a high level. Key details are missing: convergence criteria, step-size selection, handling of the non-differentiable terms for each penalty type, initialization, and stopping rules. The comparison with CVX is presented only in supplementary figures, and the manuscript does not report the actual runtime values or the experimental setup (e.g., data dimensions, hardware) in the main text. Without these details, the algorithm cannot be independently implemented or the efficiency claim fully evaluated.
    - **Why it matters** Reproducibility is a core requirement for methodological contributions. The efficiency advantage is a key selling point, and it must be documented with sufficient detail and context.
    - **Resolution test** Provide a complete algorithmic description (pseudocode or detailed equations) in the main text or supplement. Report runtime comparisons with explicit data sizes, hardware specifications, and the exact CVX configuration used.

  - **R1-M3** (Blocking: No)
    - **Axis** Generalizability and scope of validation
    - **Claim pointer** The authors state that the TF–TG identification methods "fill the gap of lacking a method for genome-wide TG prediction of a TF" and that the net-based methods are "instrumental for predicting pathway GRNs."
    - **Evidence pointer** Abstract; Discussion section "Development and elucidation of six novel methods for identifying TGs of a TF"
    - **Concern** The real-data validation is limited to two plant TF overexpression datasets (SND1, gl3) and one maize compendium for pathway GRNs. The claim of filling a general gap is strong, but the evidence is restricted to a narrow set of organisms and conditions. No comparison is made to more recent or widely used methods beyond CLR, MRNET, and TIGRESS, and the manuscript does not discuss potential limitations when applied to other organisms, data types (e.g., single-cell), or TF perturbation strategies.
    - **Why it matters** The stated significance of the work depends on its broad applicability. A narrow validation limits the strength of the general claims.
    - **Resolution test** Add additional validation on diverse datasets (e.g., animal or human data, different perturbation types) or temper the claims to reflect the scope of the current validation. Discuss known limitations and potential failure modes.

  - **R1-M4** (Blocking: No)
    - **Axis** Biological interpretation and practical utility
    - **Claim pointer** The authors suggest the methods have "potential for validating ChIP/DAP-seq results" and that the net-based methods can identify "unique regulatory relationships."
    - **Evidence pointer** Discussion section; Results section "Validation of the two net-based methods for identifying lignin pathway genes and GRN"
    - **Concern** The biological validation is indirect. For the lignin pathway analysis, the authors note that "we do not know which method is better than another" because true targets are mostly unknown. The claim of identifying "unique regulatory relationships" is based on overlap analysis, but no experimental validation or literature-based confirmation of these unique predictions is provided. The practical utility for ChIP/DAP-seq validation is asserted but not demonstrated with a concrete example.
    - **Why it matters** For a methods paper in a biological journal, demonstrating biological relevance strengthens the case for adoption. Without experimental or strong literature-based support, the practical claims remain speculative.
    - **Resolution test** Provide at least one experimentally validated or literature-confirmed example of a unique prediction. Alternatively, present a case study where the method successfully narrows down ChIP/DAP-seq candidates.

- **Minor Comments**
  - **R1-m1**
    - **Severity** Minor
    - **Axis** Clarity of writing
    - **Affected element** Introduction, paragraph 1
    - **Evidence pointer** "Although biological experiments can be carried out to obtain gene regulatory relationships, they are labor-intensive and time-consuming, and can therefore only be used to obtain a small number of true regulatory relationships."
    - **Issue** The phrase "true regulatory relationships" is ambiguous. It could mean experimentally validated relationships or all actual relationships in the system.
    - **Required correction** Rephrase to clarify, e.g., "can only be used to validate a small number of candidate regulatory relationships."

  - **R1-m2**
    - **Severity** Minor
    - **Axis** Technical accuracy
    - **Affected element** Methods, "Penalty functions" section
    - **Evidence pointer** "ENET penalty combines the penalties of ridge regression and Lasso to gain 'super-penalty'."
    - **Issue** The term "super-penalty" is not standard terminology and is not defined. It may confuse readers.
    - **Required correction** Replace with a standard description, e.g., "the ENET penalty combines L1 and L2 penalties to encourage grouping of correlated predictors while maintaining sparsity."

  - **R1-m3**
    - **Severity** Minor
    - **Axis** Statistical rigor
    - **Affected element** Methods, "Selection probability" section
    - **Evidence pointer** "the half-sample approach, which does not need to choose the optimal tuning parameters in selection methods"
    - **Issue** The claim that the half-sample approach avoids tuning parameter selection is not entirely accurate. The grid of lambda and alpha values still needs to be specified, and the choice of grid range can affect results.
    - **Required correction** Clarify that the approach avoids cross-validation-based selection of a single optimal tuning parameter, but that the grid range still requires specification.

  - **R1-m4**
    - **Severity** Minor
    - **Axis** Presentation of results
    - **Affected element** Results, "Validation of the four TF–TG identification methods with SND1 overexpression transcriptomic data"
    - **Evidence pointer** "The results, as shown in Figures 3A and B, demonstrated the following: (i) When applied to 178 DEGs, Huber-ENET and MSE-ENET in overall identified less positive TGs than CLR and MRNET methods but more than Huber-Lasso, MSE-Lasso and TIGRESS"
    - **Issue** The description is confusing. "Identified less positive TGs" could mean fewer true positives or fewer total predictions. The sentence structure makes it hard to follow the comparison.
    - **Required correction** Rewrite for clarity, e.g., "Huber-ENET and MSE-ENET identified fewer total TGs than CLR and MRNET but more than Huber-Lasso, MSE-Lasso, and TIGRESS, while achieving higher TPRs."

  - **R1-m5**
    - **Severity** Minor
    - **Axis** Data availability
    - **Affected element** Data Availability section
    - **Evidence pointer** "The R package TGPred and Python module TGPred 52 are freely and publicly available at: https://zenodo.org/record/8297854 (R version) and https://zenodo.org/record/8299724 (Python version)."
    - **Issue** The text "TGPred 52" appears to contain a stray reference number. Also, the GitHub link in the Methods section (https://github.com/xueweic/TGPred) is not mentioned in the Data Availability section.
    - **Required correction** Remove the stray "52" and include both the GitHub and Zenodo links in the Data Availability section.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of a clearly defined and statistically rigorous comparison framework for performance claims.
  - R1-M2: Insufficient algorithmic detail for the APGD method to be independently implemented and the efficiency claim fully evaluated.

- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The combination of existing loss functions and penalties with a network-based penalty and an efficient solver is a useful integration, but each component is well-established. The novelty lies primarily in the specific combination and the APGD implementation, which is incremental rather than transformative.
  - **Scientific importance** Moderate. The problem of TF target prediction is important, and the methods address a practical need. However, the demonstrated advantages over existing methods are modest and the scope of validation is narrow, limiting the immediate impact.
  - **Interdisciplinary readership** Limited. The manuscript is primarily of interest to computational biologists and plant genomics researchers. The methods are not presented in a way that would attract a broad readership from other disciplines.
  - **Technical soundness** The core statistical framework is sound, but the validation methodology has weaknesses (see R1-M1) and the algorithmic description is incomplete (see R1-M2). The simulation studies are reasonable but would benefit from more comprehensive benchmarking.
  - **Readability for nonspecialists** The manuscript is generally well-written, but the methods section assumes familiarity with penalized regression and optimization. The biological motivation is clear, but the technical details may be challenging for nonspecialist readers. The figures and results are described in a way that is accessible, but the lack of clear definitions for some terms (e.g., "super-penalty") detracts from readability.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially useful tool, but the validation framework and algorithmic documentation must be strengthened to support the claims. The authors should address the blocking concerns regarding comparison methodology and algorithmic detail before the case for the method's utility is fully established.