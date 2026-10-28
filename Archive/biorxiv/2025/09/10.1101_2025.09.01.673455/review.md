## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, figure legends not fully provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness based solely on the provided text
- **Shared manuscript claim summary** The authors propose that centromere positioning at the surface of mitotic chromosomes is driven by electrostatic repulsion between negatively charged centromere-associated proteins (kinetochore components, CENP-B) and condensed chromatin, operating independently of condensin-mediated loop extrusion and microtubule engagement. This mechanism is supported by cellular perturbations, biochemical reconstitution, and multiscale molecular dynamics simulations, and is recapitulated by synthetic negatively charged protein constructs.
- **Visible evidence base** Abstract, main text sections (Results and Conclusions), Materials and Methods (partial), figure references (Fig. 1-5, Fig. S1-S7, Table S1)
- **Missing materials affecting confidence** Full figure panels and data values, statistical details, control experiments, simulation parameters, raw data, supplementary figures, and complete methods for several key experiments

## Reviewer
- **Overall assessment** This manuscript presents a conceptually novel and potentially important mechanism for centromere organisation during mitosis. The combination of cellular, biochemical, and computational approaches is ambitious and the central hypothesis is clearly articulated. However, several critical technical concerns must be addressed before the conclusions are fully supported. The quantitative evidence for the electrostatic repulsion model, particularly in the cellular context, is incomplete, and the generalisability of the in vitro findings to the complex in vivo environment requires further validation.
- **Who would be interested in the results, and why** Researchers in chromosome biology, mitosis, centromere/kinetochore function, chromatin organisation, and biophysics of phase separation. The proposed electrostatic mechanism could have broad implications for understanding how chromatin domains are spatially organised within the nucleus and during cell division, and may interest those studying synthetic biology approaches to genome organisation.
- **Major strengths** 1) The study addresses a fundamental and long-standing question in chromosome biology with a fresh conceptual framework. 2) The multi-disciplinary approach integrating cell biology, biochemistry, and multiscale simulations is powerful and appropriate. 3) The use of a synthetic system to test the generality of the electrostatic principle is elegant and strengthens the mechanistic claim. 4) The demonstration of condensin- and microtubule-independence is a clear and important negative result.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** 
  - **Originality** High. The electrostatic repulsion model is a novel conceptual framework for centromere positioning, distinct from prevailing loop-extrusion or chromatin-folding models.
  - **Scientific importance** Potentially high. If fully validated, this mechanism could explain a fundamental aspect of chromosome architecture and may be generalisable to other chromatin domains. The finding that a simple physical property (charge) can program spatial organisation is conceptually significant.
  - **Interdisciplinary readership** Broad. The work bridges cell biology, biochemistry, biophysics, and computational biology, and the conclusions are likely to be of interest to a wide audience.
  - **Technical soundness** Currently not fully established. While the experimental design is generally sound, several key quantitative analyses and controls are missing or under-described, and the link between in vitro and in vivo observations requires stronger evidence.
  - **Readability for nonspecialists** Good. The manuscript is clearly written and the central hypothesis is well explained. The figures are referenced appropriately, though the full figure content was not available for review.
- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is compelling and the preliminary data are promising, but the current evidence base is insufficient to fully establish the model.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative data and statistical analysis
- **Claim pointer** The authors claim that CENP-A-rich domains are "essentially at the chromatin surface" with "only 5.7 ± 5.0% of foci located deeper than 200 nm" in control cells, and that this localisation is maintained after condensin depletion and microtubule depolymerisation.
- **Evidence pointer** Fig. 1a-d, Fig. 1e, Fig. S1; location not provided for specific data points
- **Concern** The quantitative analysis of CENP-A focus distribution relative to the chromatin surface is central to the paper's premise, yet the methods for this analysis are not fully described. The authors report a mean depth of 46 ± 107 nm, but the large standard deviation suggests a heterogeneous distribution. It is unclear how the chromatin surface was defined in 3D, how foci were segmented, and whether the analysis was blinded. Furthermore, the statistical comparison between conditions (control vs. condensin-depleted vs. microtubule-depolymerised) is not described. The claim of "no significant difference" requires appropriate statistical testing and reporting of effect sizes and confidence intervals.
- **Why it matters** The entire paper rests on the observation that centromeres are specifically surface-localised and that this localisation is independent of condensin and microtubules. If the quantitative analysis is flawed or underpowered, the central conclusion is not supported.
- **Resolution test** Provide a detailed description of the image analysis pipeline, including surface definition, focus detection, and statistical methods. Report the number of cells/foci analysed per condition, the statistical test used, and the effect sizes with confidence intervals. Ideally, provide a validation of the analysis method using simulated or ground-truth data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic evidence
- **Claim pointer** The authors claim that "chromatin surface localisation emerges from repulsion between condensed chromatin and both the kinetochore and the highly negatively charged centromere protein, CENP-B."
- **Evidence pointer** Fig. 2, Fig. 3, Fig. S3-S5; location not provided
- **Concern** The causal link between CENP-B's negative charge and surface localisation is not fully established. In cells, CENP-B knockout alone had no effect, and only in combination with kinetochore depletion was a reduction in surface localisation observed. This suggests redundancy, but the relative contributions of kinetochore charge versus CENP-B charge are not quantified. In vitro, the experiments show that CENP-B can drive surface localisation, but the physiological relevance of the charge density used in these experiments is unclear. The simulation results are consistent with the model but are not a direct test of the in vivo mechanism.
- **Why it matters** The paper proposes a specific biophysical mechanism. Without a clear demonstration that the charge of CENP-B (and kinetochore components) is the causative factor in cells, alternative explanations (e.g., specific protein-protein interactions, steric effects) cannot be excluded.
- **Resolution test** Provide a more quantitative analysis of the cellular data, e.g., by measuring the charge density of kinetochores and CENP-B and correlating this with surface localisation. Use charge-neutralising mutations of CENP-B (e.g., replacing acidic residues with neutral ones) in the knockout background to directly test the role of charge. In the in vitro system, titrate the charge density to demonstrate a dose-dependent effect.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation-experiment consistency
- **Claim pointer** The authors claim that their multiscale MD simulations "accurately recapitulate the CENP-B-induced surface targeting of associated chromatin."
- **Evidence pointer** Fig. 3c,d, Fig. 3g,h; location not provided
- **Concern** The simulations are a key pillar of the paper, but the level of agreement between simulations and experiments is not quantified. The authors show representative density profiles and PMF curves, but it is unclear how well the simulated surface enrichment values match the experimental values. The simulation model for CENP-B is highly simplified (a single bead for the globular domain and a flexible chain for the acidic domain), and the parametrisation of the interactions is based on an empirical mapping. The sensitivity of the results to these parameters is not explored.
- **Why it matters** The simulations are used to support the mechanistic interpretation. If the model is not quantitatively validated or is highly sensitive to parameters, the conclusions drawn from it are weakened.
- **Resolution test** Provide a quantitative comparison of simulated and experimental surface enrichment values, including error bars. Perform a sensitivity analysis of the key interaction parameters (e.g., charge density, interaction strength) to show that the predicted surface localisation is robust. Ideally, make predictions from the simulations that can be tested experimentally.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalisability of the in vitro system
- **Claim pointer** The authors claim that "tethering synthetic negatively charged proteins to chromatin was sufficient to recapitulate this surface localisation in cells and in vitro."
- **Evidence pointer** Fig. 4, Fig. 5, Fig. S6-S7; location not provided
- **Concern** The in vitro system uses purified nucleosome arrays and phase separation conditions that may not fully recapitulate the complex environment of the mitotic chromosome. The cellular experiments with TetR-GFP(neg25) show a modest effect, and the authors note it is "less pronounced" than in vitro. The density of TetR-GFP(neg25) binding to the TetO arrays in cells is not quantified, and it is unclear whether the achieved charge density is comparable to that of CENP-B at endogenous centromeres.
- **Why it matters** The claim that electrostatic repulsion is a "general and programmable mechanism" relies on the demonstration that a synthetic charge can mimic the effect. If the effect is weak or requires non-physiological charge densities, the generalisability is questionable.
- **Resolution test** Quantify the number of TetR-GFP(neg25) molecules bound per TetO array in cells and compare this to the number of CENP-B molecules at endogenous centromeres. Test a range of charge densities to establish the threshold required for surface localisation. Show that the effect is specific to negative charge (e.g., by using a neutral or positively charged control protein).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Alternative explanations
- **Claim pointer** The authors conclude that "centromere layering is not hardwired by chromatin folding patterns but instead emerges from phase separation in chromatin."
- **Evidence pointer** Fig. 1, Fig. 2, Fig. 3; location not provided
- **Concern** The paper does not fully exclude alternative mechanisms for surface localisation. For example, the kinetochore is a large protein complex that could physically exclude chromatin from the interior, or it could interact with specific factors at the chromosome periphery. The experiments with CENP-C depletion and CENP-B knockout are consistent with the electrostatic model, but they do not directly test it. The observation that DNA fragments alone can drive surface localisation in vitro is suggestive, but the in vivo relevance of this finding is unclear.
- **Why it matters** The paper makes a strong claim about the mechanism. To be convincing, it must rule out other plausible explanations.
- **Resolution test** Perform experiments that directly manipulate the charge of the kinetochore or CENP-B without affecting their other functions. For example, replace CENP-B's acidic domain with a neutral or positively charged domain of similar size and test for surface localisation. Use optical tweezers or other biophysical methods to measure the forces between chromatin and kinetochore components.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure legends
- **Affected element** Fig. 1-5, Fig. S1-S7
- **Evidence pointer** Figure legends not provided in the manuscript text
- **Issue** The figure legends are not included in the provided text, making it difficult to fully interpret the data presented.
- **Required correction** Ensure that all figure legends are complete and self-explanatory, including details on sample sizes, statistical tests, and error bar definitions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Cell line generation, CENP-C depletion
- **Evidence pointer** Materials and Methods, "Cell Line Generation" and "Kinetochore depletion"
- **Issue** The efficiency and specificity of CENP-C depletion are not quantified. The authors state that depletion was confirmed by immunofluorescence, but the level of depletion and the number of cells analysed are not reported.
- **Required correction** Provide quantitative data on CENP-C depletion efficiency (e.g., percentage of cells with undetectable CENP-C, mean fluorescence intensity before/after depletion).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Simulation details
- **Affected element** MD simulation methods
- **Evidence pointer** Materials and Methods, "Single fibre MD simulation details" and "Direct Coexistence MD simulations"
- **Issue** The simulation parameters are not fully described. For example, the number of independent simulations, the equilibration time, and the criteria for determining equilibrium are not stated.
- **Required correction** Provide a complete description of the simulation protocol, including the number of replicates, simulation length, and convergence criteria.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** All quantitative results
- **Evidence pointer** Fig. 1-5; location not provided
- **Issue** The statistical tests used for comparisons are not consistently reported. For example, in Fig. 1, the comparison between control and condensin-depleted conditions is not described.
- **Required correction** Clearly state the statistical test used for each comparison, the number of independent experiments, and the p-values or confidence intervals.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Electrostatic polarity"
- **Evidence pointer** Abstract, Introduction, Discussion
- **Issue** The term "electrostatic polarity" is used to describe a directional asymmetry in charge distribution. This is a useful concept, but it should be clearly defined and distinguished from other uses of "polarity" in cell biology.
- **Required correction** Provide a clear definition of "electrostatic polarity" in the introduction and use the term consistently throughout the manuscript.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** All datasets
- **Evidence pointer** Not specified
- **Issue** The manuscript does not include a data availability statement.
- **Required correction** Add a data availability statement describing where the raw data, analysis scripts, and simulation input files can be accessed.

## Risk / unsupported claims
- The claim that the mechanism is "independent of condensin-mediated loop extrusion" is supported by the depletion experiments, but the possibility of residual condensin activity or redundant pathways is not fully excluded.
- The claim that "electrostatic repulsion is a key determinant of surface localisation" is supported by correlative evidence, but a direct causal demonstration in cells is lacking.
- The claim that the mechanism is "programmable" is based on the synthetic TetR-GFP(neg25) experiments, but the efficiency of this system in cells is modest and the charge density is not quantified.
- The in silico charge estimate of -303.9e per kinetochore complex (Table S1) is presented without details on the calculation method or the structural model used, making it difficult to assess its accuracy.
- The generalisation of the findings to "centromere layering" in all organisms is not supported by the data, which are limited to human cells and in vitro systems.