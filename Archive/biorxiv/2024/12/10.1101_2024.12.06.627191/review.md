## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Technical soundness, methodological clarity, evidence quality, and claims as stated in the provided text; no external data or code verification performed
- **Shared manuscript claim summary** The authors present JAX-EPBD, a GPU-accelerated Langevin molecular dynamics framework for simulating DNA breathing dynamics, claiming up to 30x speedup over a C-based EPBD implementation, validated on the AAV P5 promoter and applied to transcription factor binding affinity prediction using SELEX data
- **Visible evidence base** Text descriptions of methods, datasets, and results; references to Figures 1-8 and Table 1; no actual figures, tables, or numerical data visible in the provided material
- **Missing materials affecting confidence** All figures, tables, numerical results, code availability, and supplementary materials; specific parameter values for the EPBD model; details of the SELEX data preprocessing; statistical significance testing

## Reviewer

### Overall assessment
The manuscript presents a potentially valuable computational tool for studying DNA breathing dynamics at scale. The motivation is clear and the application to transcription factor binding is timely. However, the provided text lacks the quantitative evidence needed to evaluate the central claims. Speedup figures are mentioned but not systematically presented. The biological validation on the AAV P5 promoter is described qualitatively. The TF binding prediction results are summarized without statistical detail. The manuscript would benefit from clearer presentation of the model equations, which appear incomplete in the text, and from explicit comparison with existing methods beyond runtime.

### Who would be interested in the results, and why
Computational biologists studying DNA dynamics, gene regulation, and transcription factor binding; researchers developing GPU-accelerated molecular simulation tools; biophysicists interested in sequence-dependent DNA behavior. The tool's scalability could enable genome-wide analyses that were previously impractical, which would interest a broad community.

### Major strengths
1. Clear identification of a computational bottleneck (Langevin simulations of long DNA sequences) and a plausible solution using JAX GPU acceleration.
2. The application to TF binding prediction provides a concrete use case that extends beyond pure simulation methodology.
3. Validation on a well-studied promoter system (AAV P5) with known transcriptional activity differences offers a biologically relevant test case.
4. The framework's ability to compute time-dependent properties (bubble lifetimes, flipping kinetics) addresses limitations of equilibrium methods like MCMC.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims the EPBD model is described by equations (1)-(4), but the equations are not fully presented in the provided text. The Morse potential, stacking potential, and Langevin equation are referenced but the actual mathematical forms are incomplete or missing.
- **Evidence pointer** Section "The Langevin-EPBD Model", equations (1)-(4); location not provided
- **Concern** The model equations are central to the work but are not fully visible in the provided material. Without the complete mathematical formulation, the reader cannot assess whether the implementation is correct, what parameter values were used, or how the model compares to established EPBD formulations. The text mentions parameters D_n, a_n, coupling constants, rho, beta, and gamma, but their values are not given.
- **Why it matters** Reproducibility is a core requirement for computational work. The missing equations and parameters prevent independent verification and limit the manuscript's utility as a methodological reference.
- **Resolution test** Provide the complete set of model equations with all parameter definitions and values used in the simulations. Include the integration scheme details for the RK2 method as applied to the stochastic differential equation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The abstract and conclusion claim "up to 30x speedup" and "consistent improvements in R2 values" for TF binding prediction, but the provided text does not contain the supporting numerical data.
- **Evidence pointer** Abstract; Section "Results and Discussion"; Figures 6-8; Table 1; location not provided
- **Concern** The central performance claims are presented without the underlying data. Table 1 is referenced for a single benchmark point (100 bp, 100 simulations) but the speedup values for other configurations are not given. The R2 improvement claims in Figure 8 are described qualitatively ("consistent improvements", "significant gains") without reporting actual R2 values, confidence intervals, or statistical tests.
- **Why it matters** The manuscript's primary contribution is computational efficiency and predictive utility. Without quantitative results, the claims cannot be evaluated or compared with alternative approaches.
- **Resolution test** Present complete benchmark results including runtime measurements, speedup factors with standard deviations, and scaling behavior across all tested configurations. Report R2 values for all TF families with and without breathing features, including standard errors and statistical significance tests.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that JAX enables "unparalleled ability to process multiple sequences concurrently" and that other frameworks "typically support only a single instance of simulation on GPUs at a time."
- **Evidence pointer** Section "High-Throughput Langevin EPBD"; location not provided
- **Concern** This is a strong comparative claim about other frameworks (PyTorch, TensorFlow) that is not substantiated with benchmarks or references. The assertion that these frameworks cannot support concurrent simulations is technically questionable, as batched operations are standard in deep learning frameworks.
- **Why it matters** The claim overstates the uniqueness of the approach and may mislead readers about the landscape of available tools. It also distracts from the more defensible claim that JAX's functional programming model and vmap/pmap are well-suited for this specific use case.
- **Resolution test** Either provide comparative benchmarks demonstrating the limitations of other frameworks for this specific simulation task, or soften the claim to accurately reflect that JAX was chosen for its specific advantages without implying other frameworks are incapable.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that incorporating breathing features with sequence data improves TF binding prediction, but the biological interpretation of this improvement is not discussed.
- **Evidence pointer** Section "Results and Discussion", Figure 8; location not provided
- **Concern** The connection between DNA breathing dynamics and TF binding is asserted but not mechanistically explained. Why would breathing features improve binding affinity prediction? Is there a known relationship between local DNA flexibility and TF recognition? The manuscript does not address these questions.
- **Why it matters** Without a mechanistic interpretation, the improved prediction is a purely empirical result. Understanding why breathing features help would strengthen the biological significance and guide future applications.
- **Resolution test** Add a discussion section that interprets the improved predictions in the context of known TF binding mechanisms, such as conformational selection or induced fit, and relate breathing features to structural determinants of binding specificity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Introduction, paragraph 1
- **Evidence pointer** Section "Introduction"; location not provided
- **Issue** The citation "( Watson et al. 2013 )" appears in the first sentence but the reference list is not provided. Additionally, the citation "( ? )" in the Introduction is incomplete.
- **Required correction** Complete all citations and ensure the reference list is included.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section "Langevin-EPBD Simulation"
- **Evidence pointer** Section "Langevin-EPBD Simulation"; location not provided
- **Issue** The text states "The integration time step is set to 0.00002" without specifying units. Earlier, the simulation time is given in picoseconds and nanoseconds, so the time step should be expressed in consistent units.
- **Required correction** Specify the units for the integration time step and ensure consistency with the stated simulation durations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "Langevin-EPBD Simulation"
- **Evidence pointer** Section "Langevin-EPBD Simulation"; location not provided
- **Issue** The text mentions "Figure 5f (right panel)" and "Figure 5g" but the figure is not visible. The description of the figure panels is confusing without the actual figure.
- **Required correction** Clarify the figure panel descriptions and ensure the figure is included in the final submission.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section "DataSets"
- **Evidence pointer** Section "DataSets"; location not provided
- **Issue** The text states "The dataset, preprocessed by Yang et al. ( Yang et al. 2015 )" but the citation year appears inconsistent with the reference style used elsewhere.
- **Required correction** Verify the citation and ensure consistency with the reference list.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "The Langevin-EPBD Model"
- **Evidence pointer** Section "The Langevin-EPBD Model"; location not provided
- **Issue** The text contains typographical errors such as "u n™ 1" and "v n™ 1" which appear to be encoding artifacts.
- **Required correction** Correct typographical errors and ensure proper mathematical notation throughout.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section "Langevin-EPBD Simulation"
- **Evidence pointer** Section "Langevin-EPBD Simulation"; location not provided
- **Issue** The text states "we perform at least 1,000 independent simulations" but earlier in the same section it says "we run at least 500 independent simulations." The numbers are inconsistent.
- **Required correction** Reconcile the number of independent simulations and ensure consistency throughout the manuscript.

### Technical failings that need to be addressed before the case is established
R1-M1 (incomplete model equations), R1-M2 (missing quantitative results), R1-M3 (unsubstantiated comparative claims)

### Assessment against Nature-style criteria
- **Originality** Moderate. GPU acceleration of existing models is a useful engineering contribution but not conceptually novel. The application to TF binding prediction adds some originality.
- **Scientific importance** Potentially significant if the speedup claims hold and the TF binding improvements are robust. The ability to perform genome-scale DNA breathing simulations would be valuable. However, the current evidence does not establish this importance.
- **Interdisciplinary readership** The topic bridges biophysics, computational biology, and genomics, which could attract broad interest. The writing is accessible but the missing equations and results limit interdisciplinary comprehension.
- **Technical soundness** Cannot be fully assessed due to missing equations, parameters, and quantitative results. The described methodology is plausible but unverifiable from the provided text.
- **Readability for nonspecialists** The abstract is clear and accessible. The main text is reasonably well-organized but contains some jargon and incomplete descriptions that would challenge nonspecialists.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a worthwhile problem and the approach is promising, but the missing equations, parameters, and quantitative results prevent evaluation of the central claims. The authors should provide complete methodological details, full benchmark data, and statistical analysis of the TF binding prediction improvements before the case can be assessed.

## Risk / unsupported claims
- The "up to 30x speedup" claim is unsupported by visible data.
- The claim that JAX uniquely enables concurrent simulation instances compared to PyTorch or TensorFlow is unsubstantiated.
- The "consistent improvements in R2 values" for TF binding prediction are not backed by reported numbers or statistical tests.
- The statement that the P5 promoter "displays a longer lifespan of bubbles at the mutation region" is presented without quantitative comparison or statistical support.
- The claim that breathing features capture "subtle sequence-dependent interactions" important for TF binding is asserted without mechanistic evidence.
- The validation on the AAV P5 promoter is described as "visually consistent" with prior work, which is not a rigorous standard of agreement.