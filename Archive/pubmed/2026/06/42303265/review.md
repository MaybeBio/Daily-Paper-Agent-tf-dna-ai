## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract, without access to full methods, derivations, or simulation details
- **Shared manuscript claim summary** The authors use mean-field theory and stochastic simulations to show that phase separation of transcription factors (TFs) can tune the dynamics of two canonical gene regulatory networks (the toggle switch and the repressilator), altering fixed-point stability, basin geometry, and oscillatory cycles. They report that when multiple TFs phase separate, the one with the lowest saturation concentration dominates system dynamics, and that the effect of phase separation on noise depends on circuit topology, contrasting with noise reduction seen in isolated gene expression.
- **Visible evidence base** Abstract text only; no figures, tables, equations, or simulation parameters provided
- **Missing materials affecting confidence** Full manuscript, methods, simulation details, parameter values, derivations, and all figures/tables

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting theoretical contribution linking biomolecular phase separation to gene regulatory network dynamics. The central claims are plausible and the contrast with isolated-gene noise behavior is intriguing. However, the abstract alone provides insufficient detail to evaluate the rigor of the mean-field analysis, the stochastic simulation methodology, or the robustness of the reported findings. The claim about dominance of the lowest saturation concentration is stated without supporting evidence or mechanistic explanation, and the topology-dependent noise effect is asserted without quantitative context. The work may be of interest to biophysicists and systems biologists, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Biophysicists studying phase separation and its functional consequences, systems biologists working on gene regulatory network dynamics, and researchers interested in cellular decision-making mechanisms. The work bridges two active fields and could inform experimental design for studying TF phase separation in regulatory contexts.
- **Major strengths** The topic is timely and relevant, addressing a gap between phase separation biology and GRN dynamics. The choice of two canonical network motifs (toggle switch and repressilator) provides a clear framework for analysis. The reported topology-dependent noise effect is a non-obvious finding that could stimulate further work.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide enough methodological detail to assess the validity of the mean-field approximations, the stochastic simulation algorithm, or the parameter regimes explored. The dominance claim and the noise-topology relationship require quantitative support that is not visible in the abstract.
- **Assessment against Nature-style criteria**  
  - Originality: The combination of phase separation with GRN dynamics is relatively novel, though the individual components are well studied. The specific claims about dominance and topology-dependent noise appear original.  
  - Scientific importance: Potentially high if the findings are robust, as they could unify two research areas and offer predictive principles for cellular decision-making.  
  - Interdisciplinary readership: The topic bridges biophysics, systems biology, and cell biology, which could attract a broad audience.  
  - Technical soundness: Cannot be assessed from the abstract alone; the mean-field and stochastic methods are standard but their application here requires scrutiny.  
  - Readability for nonspecialists: The abstract is clear and accessible, with appropriate context and minimal jargon.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but insufficient to support the strong claims made. A full manuscript with methods and results would be needed to assess whether the case is convincing.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "Our mean-field analysis reveals that phase separation alters the stability of fixed points and reshapes the basin geometry of the toggle switch and modifies the oscillatory cycles of the repressilator."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract states that mean-field analysis reveals specific dynamical changes, but no details are given about the model formulation, the nature of the phase separation coupling, or the mathematical methods used to analyze stability and basin geometry. Without this information, it is impossible to verify whether the mean-field treatment is appropriate for the systems considered or whether the reported effects are robust to parameter choices.  
- **Why it matters** The core contribution of the work rests on these mean-field results. If the approximations are not justified or the analysis is flawed, the entire framework collapses.  
- **Resolution test** Provide the model equations, the mean-field derivation, and a stability analysis with explicit parameter values. Show that the reported changes in fixed-point stability and basin geometry are reproducible across a reasonable parameter range.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Support for claims  
- **Claim pointer** "A key finding for both networks is that when multiple TFs undergo phase separation, the one with the lowest saturation concentration for phase separation dominates system dynamics."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** This is presented as a key finding, but the abstract provides no mechanistic explanation or quantitative evidence for why the lowest saturation concentration should dominate. It is unclear whether this is an exact result, an approximation, or an empirical observation from simulations. The scope of the claim (both networks, all conditions) is broad and may not hold universally.  
- **Why it matters** This claim is likely to be a headline result that could guide experimental work. If it is not rigorously established, it could mislead researchers designing experiments or interpreting data.  
- **Resolution test** Provide a derivation or systematic simulation study showing that the dominance of the lowest saturation concentration holds across a wide range of parameters and network topologies, with a clear explanation of the underlying mechanism.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Support for claims  
- **Claim pointer** "Stochastic simulations show that the impact of phase separation on fluctuations (or noise) in the abundance of TFs for GRNs depends strongly on the topology of the circuits. This behaviour stands in sharp contrast with the noise reduction effect observed in the expression of isolated genes."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract reports a topology-dependent noise effect without providing quantitative measures of noise (e.g., Fano factor, coefficient of variation) or the specific differences between the toggle switch and repressilator. The contrast with isolated-gene behavior is stated but not quantified, and it is unclear whether this contrast is based on the authors' own simulations or on published results.  
- **Why it matters** This is a potentially important and non-obvious finding, but without quantitative support it remains an assertion. The claim of contrast with isolated genes needs a clear baseline for comparison.  
- **Resolution test** Present noise measurements for both networks under phase-separating and non-phase-separating conditions, with statistical error bars, and compare them directly to the isolated-gene case using the same model framework.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "saturation concentration" is used without definition. In the phase separation context, this likely refers to the critical concentration for phase separation, but the abstract does not clarify this.  
- **Required correction** Define the term explicitly, e.g., "the critical concentration above which phase separation occurs," in the abstract or introduction.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Model description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not specify whether the phase separation is modeled as a continuous process or as a discrete switch, nor does it mention the spatial dimension (e.g., well-mixed vs. spatially resolved).  
- **Required correction** Add a brief statement in the abstract or methods about the modeling approach for phase separation and the spatial assumptions.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Literature comparison  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract claims a contrast with noise reduction in isolated genes but does not cite or describe the relevant prior work, making it hard to assess the novelty of the contrast.  
- **Required correction** Include a reference to the isolated-gene noise reduction studies and briefly state how the current results differ.

## Risk / unsupported claims
- The claim that the lowest saturation concentration dominates system dynamics is unsupported in the abstract, as no evidence or mechanism is provided.
- The claim that noise effects depend strongly on circuit topology is unsupported without quantitative noise measurements.
- The contrast with noise reduction in isolated genes is asserted but not substantiated with data or references.
- The mean-field results on stability, basin geometry, and oscillatory cycles are unverifiable from the abstract alone.