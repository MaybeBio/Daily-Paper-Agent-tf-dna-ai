## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and presentation quality based solely on the provided text
- **Shared manuscript claim summary** The authors propose a multiscale probabilistic framework that integrates machine-learning predictions of binding affinity (from protein sequence or structure) into Bayesian parameter inference of dynamic cell signaling ODE models, and quantify the information gained from this augmentation using KL divergence
- **Visible evidence base** Text descriptions of results in Sections 2.1–2.7, including references to Figures 1–7 and Supplementary Figures S1–S9; no actual data, figures, or numerical results are visible
- **Missing materials affecting confidence** All figures, tables, numerical results, statistical outputs, and supplementary information are absent; code repository referenced but not reviewed

## Reviewer

- **Overall assessment** The manuscript addresses a timely and important problem in systems biology: leveraging abundant molecular data (sequence, structure) to improve parameter estimation in mechanistic models. The proposed framework is conceptually appealing and the authors are appropriately cautious in their claims. However, the absence of all figures, numerical results, and supplementary materials in the provided scope prevents verification of the central claims. The manuscript is well-written and the logical structure is clear, but several methodological details and potential limitations require clarification before the case is fully established.

- **Who would be interested in the results, and why** Researchers in systems biology, computational biology, and mechanistic modeling of cell signaling would be the primary audience. The work is also relevant to those developing machine-learning approaches for biophysical property prediction and those interested in Bayesian inference and uncertainty quantification in biological models. The framework's generalizability to other signaling pathways and its potential to improve model identifiability could attract a broader computational biology readership.

- **Major strengths** The manuscript addresses a clear and important gap: underdetermined parameters in mechanistic models of cell signaling. The proposed framework is novel in its integration of ML-based binding affinity predictions into Bayesian inference for dynamic models. The authors are appropriately cautious, acknowledging limitations and testing robustness to prior specifications. The use of two well-established test cases (EGFR and GPCR) with different model sizes provides a reasonable test of generalizability. The writing is clear and accessible, with a helpful author summary.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence
- **Claim pointer** The central claim that the augmented approach improves parameter estimation, particularly for unbinding rates, cannot be verified
- **Evidence pointer** Section 2.3, Figures 4a–c; location not provided
- **Concern** The manuscript states that "the information in y AUG improves the parameter estimates, especially in the case of the unbinding rates, where the improvement is statistically significant." However, no numerical values, effect sizes, confidence intervals, or statistical test results are visible in the provided text. The magnitude of improvement and its practical significance cannot be assessed.
- **Why it matters** The central contribution of the paper is the demonstration that sequence/structure data improves parameter estimation. Without visible quantitative evidence, this claim is unverifiable and the paper's main conclusion cannot be evaluated.
- **Resolution test** Provide the actual numerical results, including parameter estimates, error metrics, and statistical test outputs, either in the main text or as visible figures/tables.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The ML pipeline's predictions are stated to outperform an uninformed prior, but the evaluation methodology is incomplete
- **Evidence pointer** Section 2.2, Figure 3a; location not provided
- **Concern** The comparison between ML pipeline predictions and uninformed prior samples is described only qualitatively. The number of binding reactions tested is small (n=10), and for one reaction an experimental structure was used. The manuscript does not describe how the uninformed prior was sampled (beyond noting it is log-uniform), how many samples were drawn, or what statistical test was used to establish that the ML pipeline's error is "significantly lower."
- **Why it matters** A rigorous statistical comparison is essential to justify the use of the ML pipeline over simpler approaches. The small sample size and the single experimental structure make the robustness of this conclusion uncertain.
- **Resolution test** Provide the full statistical analysis, including sample sizes, test statistics, and p-values. Discuss the limitations of the small sample size and the potential impact of the single experimental structure on the conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The KL divergence results are used to conclude that the most information is gained on unbinding rates, but the interpretation is unclear
- **Evidence pointer** Section 2.3, Figure 4b; location not provided
- **Concern** The manuscript reports KL divergences from the baseline posterior to the augmented posterior for each parameter. However, KL divergence is asymmetric and sensitive to the support of the distributions. The authors do not explain why this particular direction of KL divergence was chosen, how the kernel density estimates were validated, or whether the results are robust to the choice of divergence metric. Additionally, the claim that "the most information is gained on the rate of protein unbinding" requires a baseline for comparison: is this relative to other parameters, or relative to some absolute threshold?
- **Why it matters** The interpretation of "information gained" is central to the paper's conclusions about when the approach is useful. If the KL divergence results are not robust or are difficult to interpret, the practical recommendations may be misleading.
- **Resolution test** Justify the choice of KL divergence direction and metric. Provide sensitivity analyses using alternative divergence measures or distance metrics. Clarify what constitutes a meaningful amount of information gain.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The sensitivity analysis is used to explain prediction differences, but the methodology has limitations
- **Evidence pointer** Section 2.5, Figure 6b–c; location not provided
- **Concern** The local sensitivity analysis is performed at the maximum likelihood parameter values of the baseline case. This is a reasonable first step, but local sensitivity at a single point may not capture the behavior of the posterior distribution, especially if the posterior is multimodal or has strong correlations between parameters. The authors acknowledge this limitation in the discussion, but the interpretation of the correlation results in Figure 6b would benefit from a more thorough treatment.
- **Why it matters** The sensitivity analysis is used to explain why some predictions change and others do not. If the local analysis is not representative, the explanation may be incomplete or misleading.
- **Resolution test** Consider complementing the local sensitivity analysis with a global sensitivity analysis or with sensitivity calculations at multiple points in the posterior distribution. Discuss the potential impact of parameter correlations on the results.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The ML pipeline is described as user-friendly and generalizable, but reproducibility details are incomplete
- **Evidence pointer** Section 2.1, Section 4.5; location not provided
- **Concern** The manuscript describes chaining together PPI-Affinity and AlphaFold 3, but does not provide sufficient detail on how these tools were used. For example, what specific version of AlphaFold 3 was used? What were the input parameters? How were the outputs of AlphaFold 3 (predicted structures) formatted and fed into PPI-Affinity? The code repository is referenced, but the manuscript should provide enough detail for independent replication.
- **Why it matters** Reproducibility is a core requirement for computational work. Without detailed methodology, other researchers cannot apply the framework to their own systems or verify the results.
- **Resolution test** Provide a detailed description of the ML pipeline, including software versions, parameters, and any preprocessing steps. Consider including a step-by-step protocol in the supplementary material.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Figure 3a
- **Evidence pointer** location not provided
- **Issue** The statement that "one of these K D predictions was made with an experimental structure" is interesting but the implications are not discussed. It would be helpful to know whether the experimental structure led to a more accurate prediction, and whether this suggests a general advantage of using experimental structures when available.
- **Required correction** Add a brief discussion of the performance of the experimental structure prediction relative to the AlphaFold 3 predictions, and comment on the implications for the pipeline's applicability.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.4, Figure 5
- **Evidence pointer** location not provided
- **Issue** The description of prediction differences between baseline and augmented approaches is qualitative. It would be helpful to have a quantitative summary, such as the number of predictions that differ significantly or the average magnitude of differences.
- **Required correction** Provide a brief quantitative summary of the prediction differences, such as the proportion of test points where the difference exceeds a threshold or the root mean square difference.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 4.8, Likelihood
- **Evidence pointer** location not provided
- **Issue** The likelihood formulation for the augmented data is described but the equation is not shown in the provided text. The description of the power prior is clear, but the actual mathematical formulation would aid understanding.
- **Required correction** Include the explicit likelihood equation for the augmented data, showing how the power prior weights the K D term.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.10, KL divergence
- **Evidence pointer** location not provided
- **Issue** The description of the KL divergence calculation mentions kernel density estimation and Monte Carlo integration, but does not specify the bandwidth selection method for the KDE or the number of Monte Carlo samples used.
- **Required correction** Provide these implementation details to ensure the KL divergence calculations are reproducible.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.6, Investigation of ML Prediction Confidence
- **Evidence pointer** location not provided
- **Issue** The finding that weighting by confidence did not significantly change results is presented briefly. It would be helpful to know whether this is because the confidence scores were not informative, or because the weighting scheme was too conservative.
- **Required correction** Add a brief interpretation of this null result and discuss potential alternative weighting schemes.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 2.7, Robustness to Prior
- **Evidence pointer** location not provided
- **Issue** The robustness analysis is described as "qualitatively consistent" but the specific differences are not detailed. It would be helpful to know which results changed and in what direction.
- **Required correction** Provide a brief summary of the specific differences observed under the alternative priors.

- **Technical failings that need to be addressed before the case is established** The absence of visible numerical results and figures is the primary technical failing in the provided scope. The central claims regarding improved parameter estimation and information gain cannot be verified. Additionally, the statistical comparison between ML pipeline predictions and uninformed priors requires more rigorous reporting. The KL divergence methodology needs justification and sensitivity analysis. Reproducibility of the ML pipeline requires more detailed methodology.

- **Assessment against Nature-style criteria** 
  - **Originality** The framework is novel in its specific combination of ML-based binding affinity prediction with Bayesian inference for dynamic signaling models. While individual components exist, their integration into a unified probabilistic framework appears original.
  - **Scientific importance** The problem addressed is important: parameter identifiability in mechanistic models is a major bottleneck in systems biology. The potential to leverage abundant molecular data to constrain parameters could have broad impact.
  - **Interdisciplinary readership** The work bridges machine learning, Bayesian statistics, and cell signaling modeling. It could appeal to researchers in all three communities, though the technical depth may limit accessibility for some.
  - **Technical soundness** The methodological approach is reasonable, but the provided text does not allow verification of the results. The small number of test cases (n=10 binding reactions) and the single experimental structure limit the strength of the conclusions.
  - **Readability for nonspecialists** The manuscript is well-written and the author summary is helpful. The introduction provides appropriate context. However, the methods section assumes familiarity with Bayesian inference and ML concepts.

- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework is promising and the manuscript is well-written, but the central claims cannot be verified from the provided material. The authors should provide the full numerical results, figures, and supplementary materials for a complete assessment. The methodological details regarding the ML pipeline and KL divergence calculations need to be expanded. If these concerns are addressed, the work could make a valuable contribution to the field.