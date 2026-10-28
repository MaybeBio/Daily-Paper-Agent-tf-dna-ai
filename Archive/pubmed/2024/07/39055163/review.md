## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods summary, results, conclusions) without supplementary information or figures
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided text; no assessment of supplementary figures or tables beyond what is referenced
- **Shared manuscript claim summary** The authors propose that shape deformation at DNA-binding sites creates an entropic funnel that biases the 1D diffusion of DNA-binding proteins toward their target motifs, enhancing both efficiency and specificity of recognition. This mechanism is claimed to be generic, operating whether deformation arises from intrinsic sequence flexibility or from protein binding at adjacent sites.
- **Visible evidence base** Coarse-grained molecular dynamics simulations of PU.1 and Fis-Xis systems on 200 bp DNA constructs; analysis of minor groove width fluctuations, search mode propensities, transfer entropy, and umbrella sampling free energy profiles; comparison with all-atom simulations for validation
- **Missing materials affecting confidence** Supplementary figures (S1–S17), tables (S1–S8), video S1, detailed methods for PCA and umbrella sampling, and the all-atom simulation protocols are referenced but not provided; these are essential for verifying key quantitative claims

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely question in protein-DNA recognition, proposing a novel mechanistic framework that links DNA shape deformation to entropy-driven biased diffusion. The central hypothesis is conceptually appealing and the combination of kinetic, thermodynamic, and information-theoretic analyses is ambitious. However, the evidence presented in the main text is insufficient to fully establish the claims. Several key results are only described qualitatively, the connection between the entropic funnel and specificity remains correlative rather than causal, and the generality of the mechanism is asserted rather than demonstrated. The manuscript would benefit from clearer quantitative presentation of the simulation results and a more rigorous treatment of alternative explanations.
- **Who would be interested in the results, and why** Researchers in biophysics, computational biology, and molecular recognition, particularly those studying protein-DNA interactions, transcription factor target search mechanisms, and allosteric communication through DNA. The proposed entropic funnel concept could also interest experimentalists using single-molecule techniques to study facilitated diffusion, as it provides testable predictions about minor groove width fluctuations and search dynamics.
- **Major strengths** The manuscript tackles a fundamental question with a physically motivated framework. The use of two distinct systems (PU.1 and Fis-Xis) representing different sources of DNA deformation is a thoughtful design. The transfer entropy analysis is a sophisticated approach to quantifying information flow along DNA. The authors also make a commendable effort to connect their findings to broader genomic observations about AT-rich flanking sequences.
- **Major Concerns** The core claims rest on simulation analyses that are not fully described or quantified in the main text. The distinction between correlation and causation in the entropy-funnel mechanism is not clearly established. The generality of the proposed mechanism is inferred from only two systems, both simulated with the same coarse-grained model. The treatment of specificity, a central concept in the title, is indirect and relies on a proxy measure (pS/pR) whose relationship to actual binding specificity is not validated.
- **Minor Comments** Several methodological details are deferred to the supplementary information without sufficient summary in the main text. The presentation of numerical results is inconsistent, with some values given and others described only qualitatively. The discussion of the speed-stability paradox and its connection to the proposed mechanism could be more precise.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The entropic funnel concept is a novel contribution that extends prior work on DNA shape readout. Scientific importance: The question of how proteins achieve efficient and specific target recognition is of broad significance, and the proposed mechanism, if validated, could influence thinking about transcription factor search dynamics. Interdisciplinary readership: The topic bridges biophysics, molecular biology, and computational chemistry, and the writing is largely accessible to nonspecialists, though some jargon could be better explained. Technical soundness: The simulation methodology is appropriate in principle, but the evidence presented is insufficient to fully evaluate the claims. Readability for nonspecialists: The abstract and introduction are clear, but the results section becomes dense and would benefit from more explicit framing of the key findings.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework is promising and the work addresses a significant question, but the current manuscript does not provide sufficient evidence to fully establish the proposed mechanism. Substantial revision with clearer quantitative presentation and additional validation would be needed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that deformation at the binding motif creates an entropic funnel that biases protein diffusion toward the target site, enhancing recognition efficiency.
- **Evidence pointer** Figures 1C, 2C, 3E, 3F, 7A, 7B; Tables 1 and 2; location not provided for specific numerical values
- **Concern** The central claim of an entropic funnel biasing protein diffusion is supported primarily by qualitative descriptions of simulation results. The main text reports that PU.1 reaches the binding site approximately two times faster and Xis approximately 2.2 times faster in the presence of deformation, but the statistical significance, error bars, and distribution of these values across the 20 independent simulations are not reported. Similarly, the ptarget analysis in Figure 3E,F is described as showing bias, but the magnitude of the effect, its dependence on distance from the target, and the statistical comparison between conditions are not quantified in the text. Without these details, the reader cannot assess the robustness of the claimed effect.
- **Why it matters** The efficiency enhancement is a foundational claim of the manuscript. If the effect size is small or variable across simulations, the proposed mechanism would not be compelling. The current presentation does not allow the reader to evaluate the strength of the evidence.
- **Resolution test** Provide quantitative values for search times with standard deviations or confidence intervals, report effect sizes for ptarget with statistical tests comparing deformed versus non-deformed conditions, and show the distribution of results across independent simulations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that the entropy gain, rather than electrostatic interactions, is the primary driver of the biased diffusion toward the binding site.
- **Evidence pointer** Tables 1 and 2; Figure 4A,B; Figure S8; location not provided
- **Concern** The thermodynamic analysis reports enthalpy changes of approximately -2.7 to -2.8 kcal/mol and entropy contributions of approximately 37-41 kcal/mol, leading the authors to conclude that entropy dominates. However, the manuscript does not adequately address the coupling between enthalpy and entropy in the simulation. The electrostatic interactions are described as "nonspecific" and are modeled with a Debye-Hückel potential, but the relative contributions of different interaction terms to the free energy are not decomposed. Furthermore, the umbrella sampling results in Figure 4A,B are described as showing an entropy-driven process, but the free energy profiles are not shown with error estimates, and the comparison between flexible and fixed DNA conditions is not quantified. The claim that entropy is the predominant driver requires a more rigorous demonstration that the enthalpy-entropy decomposition is reliable and that the observed bias is not an artifact of the specific simulation setup.
- **Why it matters** The manuscript proposes a specific physical mechanism (entropy-dominated recognition). If the enthalpy-entropy balance is not robustly established, the mechanistic claim is not supported. This is particularly important because the authors themselves note that the enthalpy change is small and within error of zero.
- **Resolution test** Provide a detailed decomposition of the free energy into enthalpic and entropic contributions with error propagation, show convergence of the entropy estimates, and demonstrate that the umbrella sampling results are robust to the choice of reaction coordinate and simulation parameters.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity claim
- **Claim pointer** The authors claim that the alignment between the molecular frustration of the protein and the ruggedness of the entropic funnel determines specificity in recognition.
- **Evidence pointer** Figure 8A-D; Figures S16 and S17; location not provided
- **Concern** The connection between the entropic funnel and specificity is the least developed part of the manuscript. The authors introduce the frustration parameter χ and show that PU.1 has a higher χ (0.19) than Xis (0.08), and that the pS/pR ratio decreases as proteins approach the binding site in the presence of deformation. However, the manuscript does not establish a quantitative relationship between χ, funnel ruggedness, and actual binding specificity. The claim that "a complementary relationship might exist" is presented as a hypothesis, not a demonstrated result. The control experiment with Xis in the absence of Fis (Figures S16 and S17) is described as showing lower specificity, but the quantitative comparison is not provided in the main text. The manuscript would need to show that the proposed mechanism can distinguish between different protein-DNA pairs with known specificity differences.
- **Why it matters** Specificity is a central concept in the title and the proposed mechanism. Without a clear demonstration that the entropic funnel mechanism can account for specificity differences, the manuscript does not fully deliver on its stated aims.
- **Resolution test** Provide a quantitative comparison of pS/pR and funnel ruggedness between conditions with and without deformation, and demonstrate that the proposed mechanism can predict or explain known specificity differences between the two systems studied.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The authors claim that their coarse-grained model adequately captures the structural and dynamical features of DNA relevant to shape readout.
- **Evidence pointer** Figures S3-S6; location not provided
- **Concern** The validation of the coarse-grained model against all-atom simulations is only mentioned in passing, with the results relegated to the supplementary information. The main text states that the findings show an "excellent match" but does not provide any quantitative metrics of agreement, such as root-mean-square deviations in minor groove widths or correlation coefficients. Given that the entire mechanistic framework depends on the fidelity of the coarse-grained model in reproducing DNA shape and fluctuations, this validation is critical. The reader cannot assess whether the model is sufficiently accurate to support the conclusions.
- **Why it matters** If the coarse-grained model does not faithfully reproduce DNA conformational dynamics, the entropic funnel and its effects on protein diffusion could be artifacts of the model rather than real physical phenomena.
- **Resolution test** Provide quantitative validation metrics in the main text or a clear summary of the supplementary validation, including comparisons of minor groove width distributions, fluctuation amplitudes, and bending angles between coarse-grained and all-atom simulations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, simulation details
- **Evidence pointer** Materials and Methods, Simulation Protocol
- **Issue** The simulation protocol states that 20 independent simulations were conducted for each system, but the equilibration time, production run length, and criteria for determining when the protein has "reached" the binding site are not specified in the main text.
- **Required correction** Provide these details in the main text or clearly reference the supplementary information with a brief summary of the key parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of the speed-stability paradox
- **Evidence pointer** Results and Discussion, Thermodynamics section
- **Issue** The manuscript invokes the speed-stability paradox but does not clearly explain how the proposed entropy-driven mechanism resolves it. The connection between the entropic funnel and the paradox is implied but not explicitly articulated.
- **Required correction** Add a brief paragraph explicitly connecting the proposed mechanism to the speed-stability paradox, explaining how entropy-driven biased diffusion can reconcile fast search with stable specific binding.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Conclusions, final paragraph
- **Evidence pointer** Conclusions
- **Issue** The authors speculate about the existence of a wider entropic funnel in genomic contexts based on AT-rich sequences around binding sites, but this is presented without supporting analysis or simulation data.
- **Required correction** Either provide preliminary evidence for this claim or clearly label it as a speculative hypothesis for future work.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and main text
- **Evidence pointer** Abstract, Results and Discussion
- **Issue** The term "entropy funnel" is used throughout, but its precise definition in the context of this work is not explicitly stated. It is unclear whether this refers to a free energy funnel in configuration space, an information-theoretic construct, or a combination of both.
- **Required correction** Provide an explicit definition of the "entropy funnel" as used in this work, distinguishing it from related concepts such as folding funnels or free energy landscapes.

## Risk / unsupported claims
- The claim that the proposed mechanism is "generic" for DNA shape readout is not supported by the evidence, as only two systems were studied, both with the same coarse-grained model.
- The claim that entropy is the predominant driving force (approximately 15 times larger than enthalpy) is not fully supported without a rigorous error analysis and demonstration of convergence.
- The claim that the entropic funnel extends over a "significantly broad" region encompassing flanking nucleotides is not quantified in the main text.
- The hypothesis about a wider entropic funnel in genomic contexts based on AT-rich flanking sequences is speculative and not supported by data presented in this manuscript.
- The relationship between the frustration parameter χ and actual binding specificity is asserted but not demonstrated quantitatively.