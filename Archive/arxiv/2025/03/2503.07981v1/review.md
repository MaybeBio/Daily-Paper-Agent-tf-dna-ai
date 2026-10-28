## Review setup
- **Input scope** Full manuscript text including main text and appendices
- **Assessment boundary** Scientific claims, methodology, experimental validation, and presentation quality as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose TACO, a reinforcement learning-based fine-tuning approach for autoregressive DNA models, to design cis-regulatory elements (CREs) with high fitness. The method integrates TFBS-derived rewards into the RL process and is evaluated on yeast promoter and human enhancer design tasks.
- **Visible evidence base** Main text tables (Tables 1-5), figures (Figures 1-4), and appendices (A-K) with supplementary tables and figures
- **Missing materials affecting confidence** Code repository referenced but not reviewed; full experimental details for some baselines not fully specified; no wet-lab validation data

## Reviewer
- **Overall assessment** The manuscript presents a novel integration of reinforcement learning with autoregressive DNA language models for CRE design, incorporating TFBS-derived biological priors into the reward structure. The approach is technically sound and addresses a relevant problem in regulatory genomics. However, several methodological details require clarification, and the experimental validation would benefit from additional comparisons and robustness analyses. The claim of being "among the first" to integrate TFBS motif information into ML-based CRE design needs more careful positioning against existing literature.
- **Who would be interested in the results, and why** Researchers in synthetic biology, regulatory genomics, and computational biology would find this work relevant. The approach of combining RL with biological priors for sequence design could interest those working on promoter engineering, gene therapy vector design, and cell-type-specific expression systems. The methodological framework may also appeal to the broader ML community working on discrete sequence optimization.
- **Major strengths** 1) Novel integration of TFBS-derived rewards into RL fine-tuning of autoregressive models, addressing a gap in existing CRE design methods. 2) Comprehensive evaluation across multiple datasets (yeast and human) and settings (oracle-guided and offline MBO). 3) The incorporation of biological prior knowledge through TFBS rewards is a thoughtful approach that bridges domain expertise with ML optimization. 4) The authors provide ablation studies that help isolate the contributions of key components.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (baseline completeness), R1-M2 (statistical rigor), R1-M3 (reproducibility details)
- **Assessment against Nature-style criteria** Originality: The work presents a novel combination of RL with TFBS-derived rewards for CRE design, which is a meaningful contribution to the field. Scientific importance: The problem of designing functional CREs is of high importance for therapeutic and biotechnological applications, and the approach offers a new perspective. Interdisciplinary readership: The work bridges ML and genomics, making it potentially interesting to both communities, though the presentation may be somewhat technical for a general audience. Technical soundness: The methodology is generally sound, but several concerns about baseline comparisons, statistical rigor, and reproducibility need to be addressed. Readability for nonspecialists: The manuscript is reasonably well-written but assumes familiarity with both RL and genomics concepts; some sections could be more accessible.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim TACO demonstrates "superior performance compared to the baselines" across multiple datasets and settings.
- **Evidence pointer** Tables 2-4, Section 4.2, Section 4.3
- **Concern** The baseline comparisons are incomplete. The authors compare against evolutionary algorithms, Bayesian optimization, and a modified version of LatProtRL, but do not include several relevant recent methods for CRE design, such as diffusion-based approaches (DDSM is only mentioned in the offline MBO section) or other RL-based sequence design methods. Additionally, the adaptation of LatProtRL to DNARL removes the ESM-based encoding, which may not be a fair comparison if the original method's strength relies on that component. The authors should include a more comprehensive set of baselines, particularly those specifically designed for CRE or regulatory sequence optimization.
- **Why it matters** Without comprehensive baseline comparisons, the claimed superiority of TACO cannot be fully established. The choice of baselines significantly affects the interpretation of results and the generalizability of the findings.
- **Resolution test** Include additional baselines such as full LatProtRL with ESM encoding, diffusion-based methods (DDSM with proper conditioning), and other recent RL-based sequence design approaches. Provide a clear justification for baseline selection and any modifications made.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report mean and standard deviation across five runs, but the significance of differences between methods is not assessed.
- **Evidence pointer** Tables 2-4, Section 4.1
- **Concern** The manuscript reports performance metrics with standard deviations but does not provide statistical significance testing (e.g., t-tests, Mann-Whitney U tests) to determine whether observed differences between TACO and baselines are meaningful. Given the variability in stochastic optimization methods, it is unclear whether the reported improvements are statistically significant. Additionally, the use of only five runs may be insufficient for reliable estimates, particularly for methods with high variance.
- **Why it matters** Without statistical testing, readers cannot assess the reliability of the reported improvements. This is particularly important for a field where small performance differences can be within noise.
- **Resolution test** Add statistical significance tests (e.g., paired tests across runs) for key comparisons. Report effect sizes and confidence intervals. Consider increasing the number of runs if computationally feasible.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state "The code is available at https://github.com/yangzhao1230/TACO" and provide implementation details in appendices.
- **Evidence pointer** Section 4.1, Appendix G
- **Concern** While the code is referenced, the manuscript lacks sufficient detail for full reproducibility. Specifically: (1) The exact hyperparameter search procedure for TACO and baselines is not described; (2) The computational cost (training time, GPU hours) for each method is not reported; (3) The specific version of HyenaDNA and the exact fine-tuning procedure (e.g., number of epochs, batch size) are not fully specified; (4) The details of the TFBS reward computation, including the exact threshold for statistical significance in the SHAP analysis, are not provided in the main text.
- **Why it matters** Reproducibility is a core requirement for scientific publications. Without complete implementation details, other researchers cannot replicate or build upon the work.
- **Resolution test** Provide a detailed hyperparameter table for all methods, report computational costs, and include complete algorithmic details in the appendix. Verify that the code repository is functional and well-documented.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** The authors claim TACO generates "high-fitness CREs" based on computational predictions.
- **Evidence pointer** Tables 2-4, Section 4
- **Concern** All evaluations rely on computational fitness predictions from the reward models. There is no wet-lab validation of the designed sequences. While the authors acknowledge this limitation in the discussion, the claim of generating "high-fitness CREs" is only as strong as the predictive accuracy of the reward models. Given known limitations of computational fitness predictors for regulatory sequences, some form of experimental validation (even limited) would substantially strengthen the claims.
- **Why it matters** The ultimate utility of CRE design methods depends on their ability to produce functional sequences in biological systems. Computational-only evaluation may not capture important biological constraints.
- **Resolution test** Include at least a small-scale experimental validation (e.g., testing a handful of designed sequences in relevant cell types) or clearly frame the results as computational predictions that require experimental verification.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2, Equation 1
- **Evidence pointer** Section 3.2
- **Issue** The pre-training loss function is not explicitly defined. The text mentions "minimizing" an equation but the equation itself is not shown in the main text.
- **Required correction** Include the explicit pre-training loss function or refer clearly to the equation number in the appendix.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2
- **Issue** The figure caption does not fully explain the RL fine-tuning process, particularly the role of the TFBS reward in the policy update.
- **Required correction** Expand the figure caption to clearly describe the RL loop, including how TFBS rewards are computed and integrated.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.1, Dataset description
- **Evidence pointer** Section 4.1, Appendix A
- **Issue** The description of the dataset splits for the offline MBO setting is somewhat unclear. The text mentions "randomly splitting the dataset in half" but does not specify whether this is done per cell type or across all data.
- **Required correction** Clarify the exact splitting procedure and whether the same split is used across all methods for fair comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Section 3.3, Equation 5
- **Evidence pointer** Section 3.3
- **Issue** The hyperparameter alpha is described as "tunable" but no guidance is provided on how to select it or its sensitivity.
- **Required correction** Provide a brief discussion of alpha selection or include a sensitivity analysis in the appendix.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature positioning
- **Affected element** Section 2, Related Work
- **Evidence pointer** Section 2
- **Issue** The related work section could benefit from a more explicit comparison with recent diffusion-based CRE design methods, particularly regarding their limitations that TACO addresses.
- **Required correction** Add a brief paragraph explicitly contrasting TACO with diffusion-based approaches and highlighting the specific advantages of the RL-based generative approach.

## Risk / unsupported claims
- The claim of being "among the first to explicitly integrate TFBS motif information into machine learning-based CRE design" is not fully supported by the literature review presented; a more thorough search and positioning is needed.
- The statement that TACO "enables the generated sequences to maintain high diversity while also exploring those with superior functional performance" is supported only by computational metrics, not experimental validation.
- The claim that "TFBS frequency alone can still capture much of the predictive power" is based on a single comparison (Table 1) and may not generalize across all cell types and conditions.
- The assertion that the offline MBO setting "makes the task more challenging" is not quantitatively demonstrated; the authors do not compare performance degradation across settings systematically.
- The observation that "GAs directly led to surprisingly good results" is presented as a finding but not thoroughly investigated or explained, leaving this as an unsupported claim about the nature of the fitness landscape.