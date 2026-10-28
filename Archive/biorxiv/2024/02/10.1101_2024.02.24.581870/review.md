## Review setup
- **Input scope** Full manuscript text (abstract, introduction, model, results, discussion, methods, supplementary information description)
- **Assessment boundary** Scientific claims, modeling framework validity, consistency with cited experimental data, and technical soundness of the simulation methodology as presented
- **Shared manuscript claim summary** The authors present a coarse-grained Brownian dynamics model of protein-DNA co-condensation on end-tethered DNA, explicitly incorporating DNA sequence-dependent protein binding affinities. They claim that (1) homogeneous DNA yields a single condensate at equilibrium, (2) sequence heterogeneity can produce multiple coexisting condensates (pearl-necklace structures), (3) capillary forces are dictated by the protein binding affinity of interfacial DNA, and (4) the framework can interpret published experimental data for Dps, Sox2, and HP1, revealing sequence-independent (Dps) versus sequence-dependent (Sox2, HP1) co-condensation behavior.
- **Visible evidence base** Simulation results described in text and referenced figures (Figures 2-6, S1-S6); methodological descriptions in Section 5; model parameter tables (Tables 1-3); re-analysis of published experimental images (Figure 7)
- **Missing materials affecting confidence** Actual figure images and data files not provided; exact numerical values for force measurements, condensate counts, and correlation coefficients not fully specified in text; details of the experimental image analysis protocol (e.g., thresholding, background subtraction) are incomplete; no error bars or statistical significance tests reported for simulation results beyond bootstrapped standard deviations

## Reviewer

### Overall assessment
The manuscript addresses a timely and important question: how DNA sequence heterogeneity influences protein-DNA co-condensation and the resulting capillary forces. The modeling framework is conceptually appealing and the qualitative predictions, particularly the role of interfacial DNA affinity in governing capillary forces and the possibility of multiple coexisting condensates on heterogeneous DNA, are potentially significant for interpreting in vitro experiments. However, the manuscript as presented has several technical weaknesses that undermine confidence in the quantitative claims. The simulation methodology is described with insufficient detail to assess convergence, equilibration, and finite-size effects. The comparison with experimental data is largely qualitative and relies on visual inspection of published images rather than rigorous quantitative analysis. The claim that HP1 exhibits sequence-dependent binding, which challenges existing literature, requires stronger evidence than the current analysis provides. The manuscript would benefit from clearer presentation of the force calculation methodology, explicit reporting of simulation parameters and convergence tests, and a more rigorous statistical framework for comparing model predictions with experimental observations.

### Who would be interested in the results, and why
Biophysicists and molecular biologists studying phase separation, chromatin organization, and genome architecture would find this work relevant. Researchers using optical tweezers or coverslip-based assays to study protein-DNA condensates would be particularly interested in the prediction that capillary forces depend sensitively on the sequence composition at the condensate interface. The framework could also interest computational biologists developing coarse-grained models of chromatin. The potential challenge to the prevailing view of HP1 as a sequence-independent DNA binder would attract attention from the heterochromatin research community.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of simulation methodology
- **Claim pointer** The authors claim that their simulations reach equilibrium and that the observed condensate configurations represent equilibrium states (Sections 3.1, 3.2, 3.3)
- **Evidence pointer** Section 5.1, location not provided
- **Concern** The simulation methodology description lacks critical details needed to assess whether equilibrium was achieved. The authors state production times of at least 3×10^6 τ but do not report how they verified equilibration, whether different initial conditions were tested, or whether the final condensate configurations are independent of starting state. For a system with multiple metastable states (as implied by the pearl-necklace structures), demonstrating true equilibrium is essential. Additionally, the system size (500 monomers, box dimensions 80×80×600 σ) and the use of periodic boundary conditions are not discussed in terms of finite-size effects. The authors also do not report the number of independent simulation runs or how statistical errors were estimated for the reported condensate counts and forces.
- **Why it matters** If the simulations are not at equilibrium, the central claim that homogeneous DNA yields one condensate while heterogeneous DNA yields multiple coexisting condensates could be an artifact of kinetic trapping rather than a thermodynamic property. The quantitative force predictions would also be unreliable.
- **Resolution test** The authors should provide: (1) a clear demonstration of equilibration (e.g., time evolution of condensate number and size, autocorrelation functions), (2) tests with multiple initial conditions (e.g., random protein distributions, pre-formed condensates at different locations), (3) system-size dependence studies, and (4) reporting of the number of independent runs and standard errors for all reported quantities.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of force calculation methodology
- **Claim pointer** The authors claim to calculate capillary forces exerted by protein-DNA condensates on bare DNA (Sections 3.1, 3.3, Figure 3, 6)
- **Evidence pointer** Section 5.4, location not provided
- **Concern** The force calculation method is problematic. The authors state that they calculate force using F_i = K(l_i - l_0), where l_0 is the mean bond length calculated for the polymer with free ends. However, this approach conflates the force due to condensate-induced DNA compaction with the intrinsic entropic elasticity of the polymer. The force on the tethered ends in a constant-distance ensemble should be calculated from the tension in the terminal bonds, not from deviations of all bonds from a free-polymer reference length. The authors also do not clarify how the presence of proteins inside the condensate affects the bond length distribution, nor how they distinguish condensate-induced forces from thermal fluctuations. The statement "To express the force in pN, we multiply" appears incomplete, with the conversion factor missing.
- **Why it matters** The quantitative force values reported (up to 7 pN in the context of Sox2) are a central result of the paper. If the force calculation is incorrect, the comparison with experimental measurements and the claim that interfacial DNA affinity dictates capillary forces would be unsupported.
- **Resolution test** The authors should provide a detailed derivation of the force calculation, validate the method against known results (e.g., force-extension curve of a worm-like chain without proteins), and clearly state the conversion factor from simulation units to pN. They should also report the force calculated from the terminal bonds directly and compare with their current method.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Strength of experimental comparison
- **Claim pointer** The authors claim that their model can interpret experimental data for Dps, Sox2, and HP1, and that HP1 exhibits sequence-dependent co-condensation (Sections 3.4, 4)
- **Evidence pointer** Section 5.9, Figure 7, location not provided
- **Concern** The comparison with experimental data is qualitative and potentially overinterpreted. For Dps, the authors state agreement with a single condensate at one end, but the experimental image analysis (intensity profiles from published figures) is not described with sufficient detail to assess objectivity. For Sox2, the claim of multiple condensates is consistent with the model, but no quantitative comparison (e.g., number of condensates, positions, sizes) is provided. Most critically, the claim that HP1 exhibits sequence-dependent binding is based on the observation of two condensates in a published experiment. The authors argue that a homogeneous model would predict only one condensate, but this argument assumes the homogeneous model is correct for HP1, which is precisely what is being questioned. Alternative explanations for two condensates (e.g., kinetic trapping, surface effects, protein concentration gradients) are not discussed. The original paper's interpretation of the two condensates as arising from conformational fluctuations is dismissed without direct evidence.
- **Why it matters** The HP1 claim challenges existing literature and is presented as a key finding. If the evidence is not robust, the paper's impact is significantly diminished. The qualitative nature of the comparison also weakens the claim that the model provides "mechanistic insights" into experimental observations.
- **Resolution test** The authors should: (1) provide a detailed, quantitative analysis of the experimental images (e.g., number of condensates across multiple experiments, statistical significance), (2) perform a systematic parameter scan to show that the homogeneous model cannot produce two stable condensates under any reasonable conditions, and (3) discuss alternative explanations for the experimental observations and how their model distinguishes between them.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model parameter justification
- **Claim pointer** The authors claim that their model parameters are informed by experimental studies and that the results are robust (Sections 2, 3, 5.2)
- **Evidence pointer** Section 5.2, Tables 1-3, location not provided
- **Concern** The choice of interaction parameters (e.g., ɛ_AP = 2 k_B T for homogeneous DNA, ɛ_PP = 2 k_B T) is not justified in detail. The authors state that these values are "consistent with previous studies" but do not provide specific references or a sensitivity analysis. For the partial λ-DNA model, the assignment of interaction energies based on AT content (ranging from 0 to 4 k_B T) is arbitrary, and the mapping from AT percentage to interaction strength is not explained. The authors also do not report how sensitive their conclusions are to the specific parameter values chosen.
- **Why it matters** The model's predictions, particularly the quantitative force values and the conditions for multiple condensate formation, depend critically on the interaction parameters. Without a sensitivity analysis, it is unclear whether the qualitative conclusions are robust or specific to the chosen parameter set.
- **Resolution test** The authors should provide a systematic sensitivity analysis showing how the number of condensates and capillary forces vary with interaction strengths, and justify their parameter choices with specific experimental or theoretical references.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Section 3.2, Figure 4
- **Evidence pointer** Location not provided
- **Issue** The text in Section 3.2 contains a typographical error: "the number of condensates varies non-monotonically as a function of R′e andS4C). and ρp (see Figure. S4B" appears to have misplaced text and parentheses.
- **Required correction** Correct the sentence structure and properly reference the supplementary figures.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Section 5.4
- **Evidence pointer** Location not provided
- **Issue** The sentence "To express the force in pN, we multiply" is incomplete, with the conversion factor missing.
- **Required correction** Complete the sentence with the appropriate conversion factor and explain how it was derived.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Sections 3.1-3.3
- **Evidence pointer** Location not provided
- **Issue** The authors report qualitative observations (e.g., "marginal increase," "sharp jump") without providing numerical values or error bars for the force measurements and condensate counts.
- **Required correction** Provide numerical values with standard errors for all reported quantities, and specify the number of independent simulations used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 4 (Discussion)
- **Evidence pointer** Location not provided
- **Issue** The discussion of capillary forces in biological contexts could be enriched by referencing recent experimental work on wetting and capillary forces at condensate interfaces, which would strengthen the biological relevance of the findings.
- **Required correction** Add relevant references and a brief discussion connecting the simulation results to broader biophysical principles of condensate-surface interactions.

### Technical failings that need to be addressed before the case is established
R1-M1 (equilibration and finite-size effects), R1-M2 (force calculation methodology), and R1-M3 (strength of experimental comparison) are blocking concerns. Without addressing these, the central claims of the manuscript cannot be considered established.

### Assessment against Nature-style criteria
- **Originality**: The manuscript addresses a relatively underexplored question, the role of DNA sequence in protein-DNA co-condensation, and introduces a modeling framework that explicitly incorporates sequence heterogeneity. This is a novel contribution, though the underlying physics (phase separation, capillary forces) is well-established.
- **Scientific importance**: The question is important for understanding genome organization and the biophysical principles of protein-DNA condensates. The potential challenge to the view of HP1 as sequence-independent is significant, but the evidence is currently insufficient.
- **Interdisciplinary readership**: The work bridges biophysics, molecular biology, and computational biology, and would appeal to a broad readership if the claims are properly supported.
- **Technical soundness**: The simulation methodology and force calculation have significant gaps that need to be addressed. The experimental comparison is qualitative and lacks rigor.
- **Readability for nonspecialists**: The manuscript is generally well-written and accessible, but the methods section is dense and would benefit from clearer explanations of the simulation and analysis procedures.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an important question and presents a promising framework, but the technical concerns regarding equilibration, force calculation, and experimental comparison must be resolved before the claims can be considered supported. I would be supportive if these concerns are adequately addressed with additional simulations, validation, and quantitative analysis.

## Risk / unsupported claims
- The claim that HP1 exhibits sequence-dependent DNA binding is not sufficiently supported by the current analysis, which relies on a single published experiment and a qualitative comparison.
- The quantitative force values reported (e.g., up to 7 pN for Sox2) are not reliable given the incomplete force calculation methodology.
- The claim that the model can "interpret" experimental data for Dps, Sox2, and HP1 is overstated, as the comparison is qualitative and lacks statistical rigor.
- The assertion that "small changes in affinity of interfacial DNA leads to a significant rise in global capillary forces" is based on a correlation coefficient of 0.91, but the statistical significance and robustness of this correlation are not reported.
- The statement that "sequence heterogeneity can result in the coexistence of multiple condensates" is presented as a general finding, but it is demonstrated only for specific parameter choices and sequence arrangements without a systematic exploration of parameter space.