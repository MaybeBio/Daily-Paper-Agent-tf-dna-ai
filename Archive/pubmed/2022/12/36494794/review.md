## Review setup
- **Input scope** Full manuscript text (including abstract, background, methods, results, discussion, and supplementary information description)
- **Assessment boundary** Methodological soundness, statistical validity, biological relevance, and clarity of the proposed clustering framework for transcription factor binding data
- **Shared manuscript claim summary** The authors propose novel clustering methods (NLK and NLH) based on nonhomogeneous Poisson process likelihoods to detect clusters of transcription factors from ChIP-seq binding site data, demonstrating improved performance over existing approaches in simulations and identifying known and novel regulatory clusters in mouse embryonic stem cells
- **Visible evidence base** Simulation studies across four scenarios, comparison with four alternative clustering methods, application to mouse ESC ChIP-seq data for 14 transcription factors, figures and tables presenting clustering results and intensity estimates
- **Missing materials affecting confidence** Code availability, detailed parameter settings for real data analysis, statistical significance measures for cluster assignments, quantitative comparison metrics beyond misclassification rates, and full supplementary figures referenced but not provided in the submitted text

## Reviewer
- **Overall assessment** The manuscript presents a statistically principled approach to clustering transcription factors based on their binding site distributions, modeled as nonhomogeneous Poisson processes. The methodological framework is innovative and the simulation results are encouraging. However, several technical aspects require clarification and strengthening, particularly regarding the estimation procedure, the choice of basis functions, the handling of real data complexities, and the biological interpretation of the clusters. The real data application, while demonstrating feasibility, lacks rigorous validation of the biological significance of the identified clusters.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing methods for ChIP-seq data analysis, statisticians working on point process models and clustering, and researchers studying transcriptional regulation and transcription factor cooperativity in stem cell biology. The methods could also interest those analyzing other types of genomic event data.
- **Major strengths** The use of nonhomogeneous Poisson processes provides a flexible and statistically sound framework for modeling transcription factor binding events. The likelihood-based clustering approach naturally extends classical methods to non-vector data. The simulation studies are well-designed and demonstrate clear advantages over existing methods. The application to real mouse ESC data yields biologically plausible results consistent with known regulatory mechanisms.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The approach is novel in applying NHPP likelihoods to transcription factor clustering, though the underlying statistical concepts are established. Scientific importance: The problem of identifying cooperative transcription factor clusters is relevant, but the demonstrated impact is limited to a single cell type and lacks extensive validation. Interdisciplinary readership: The work bridges statistics and genomics, but the presentation may be too technical for a broad biological audience. Technical soundness: The core methodology is sound, but several implementation details and validation steps are incomplete. Readability for nonspecialists: The manuscript is clearly written but assumes familiarity with point process theory and clustering algorithms.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding estimation procedures, model validation, and biological interpretation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the proposed NLK and NLH methods accurately detect transcription factor clusters and uncover the hierarchy of transcription factor interactions.
- **Evidence pointer** Methods section, Simulation results, Figures 1-4
- **Concern** The estimation of the NHPP intensity function via basis expansion is described, but the manuscript does not specify how the number of basis functions is selected, how the sparsity of coefficients is enforced, or how the optimization is performed. The choice of DCT is mentioned but not justified. The sensitivity of the clustering results to these choices is not explored.
- **Why it matters** The performance of the proposed methods critically depends on the accuracy of intensity estimation. Without clear guidance on parameter selection and evidence of robustness, the methods may not be reproducible or generalizable to other datasets.
- **Resolution test** The authors should provide a detailed description of the estimation algorithm, including the selection of basis functions, the optimization procedure, and any regularization. They should also conduct sensitivity analyses to show that the clustering results are stable across reasonable choices of these parameters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that NLK outperforms four alternative methods in all simulation scenarios.
- **Evidence pointer** Table 2, Simulation results
- **Concern** The comparison with alternative methods is limited to a single set of simulation scenarios. The manuscript does not report the variability of the performance metrics across the 1,000 simulation repetitions, nor does it provide statistical tests to confirm that the observed differences are significant. Additionally, the alternative methods are not described in sufficient detail to assess whether they are implemented optimally.
- **Why it matters** Without measures of variability and significance, the claim of superiority cannot be rigorously evaluated. A fair comparison requires that all methods are implemented and tuned appropriately.
- **Resolution test** The authors should report the standard deviations or confidence intervals for the performance metrics, and perform statistical tests (e.g., paired tests) to compare the methods. They should also provide details on the implementation of the alternative methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that the application to mouse ESC data identifies the cluster of core ESC regulators and provides new insights on functional implications of transcriptional regulatory modules.
- **Evidence pointer** Real data application, Figures 6-7
- **Concern** The real data analysis is descriptive and lacks quantitative validation. The manuscript does not provide statistical measures to assess the significance or stability of the identified clusters. The choice of the number of clusters (k) is not justified, and the results are not compared with alternative clustering methods on the real data. The biological interpretation of the clusters is speculative and not supported by additional analyses (e.g., enrichment analysis, comparison with known regulatory networks).
- **Why it matters** The biological relevance of the proposed methods is a key selling point. Without rigorous validation, the claims of identifying known and novel regulatory clusters are not substantiated.
- **Resolution test** The authors should provide a systematic approach for selecting k, assess the stability of the clusters (e.g., via bootstrap), compare with alternative methods on the real data, and perform enrichment analyses to support the biological interpretation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the NHPP model is appropriate for modeling transcription factor binding events.
- **Evidence pointer** Methods section, Background
- **Concern** The manuscript does not provide evidence that the NHPP assumption is valid for the real ChIP-seq data. The independence assumption of binding events in non-overlapping intervals may be violated due to chromatin structure, cooperative binding, or other biological factors. The manuscript does not discuss or test the goodness-of-fit of the NHPP model.
- **Why it matters** If the model assumptions are not met, the clustering results may be biased or misleading. The validity of the NHPP assumption is fundamental to the proposed approach.
- **Resolution test** The authors should perform goodness-of-fit tests for the NHPP model on the real data, or at least discuss the potential limitations and their impact on the results.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript claims that the methods are novel and effective for detecting transcription factor clusters.
- **Evidence pointer** Methods section, Results
- **Concern** The manuscript does not provide code or a detailed pseudocode for the proposed algorithms. The description of the algorithms is at a high level, and the implementation details (e.g., initialization, convergence criteria, handling of edge cases) are not specified. This limits the reproducibility of the results.
- **Why it matters** Reproducibility is a fundamental requirement for scientific research. Without access to the code or detailed implementation, other researchers cannot apply or build upon the proposed methods.
- **Resolution test** The authors should make the code publicly available and provide a detailed description of the algorithms, including all implementation details.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract mentions "transcrisptional regulatory modules" which appears to be a typographical error for "transcriptional regulatory modules".
- **Required correction** Correct the typo in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Background section
- **Evidence pointer** Background
- **Issue** The phrase "the the Poisson process assumption" contains a duplicated article.
- **Required correction** Remove the duplicate "the".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Methods, Maximum likelihood estimation
- **Issue** The manuscript mentions that the optimization is performed by "numerically searching over the coefficient space" but does not specify the optimization algorithm used.
- **Required correction** Specify the optimization algorithm (e.g., gradient descent, Newton-Raphson) and any constraints on the coefficients.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** Real data application
- **Issue** The manuscript states that the two strategies (pooling and concatenating) provide "similar" results for k=4 and k=5, but does not quantify the similarity.
- **Required correction** Provide a quantitative measure of similarity (e.g., adjusted Rand index) to support this claim.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion mentions future directions but does not discuss the computational complexity of the proposed methods.
- **Required correction** Add a brief discussion of the computational cost and scalability of the methods.

## Risk / unsupported claims
- The claim that NLK "clearly outperforms" alternative methods is not fully supported without measures of variability and statistical significance.
- The claim that the real data application provides "new insights on functional implications" is not substantiated by quantitative analyses.
- The appropriateness of the NHPP model for the real data is not validated.
- The stability and significance of the identified clusters in the real data are not assessed.
- The reproducibility of the methods is limited by the lack of code and detailed implementation information.