## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors use long-timescale molecular dynamics simulations and free energy calculations to define the energetic basis for ligand-independent activation of estrogen receptor alpha (ERα) mutants Y537S and D538G, which are frequently found in endocrine-resistant metastatic breast cancers. They propose a "spring-loading" model in which the H11-12 loop acts as an energetic barrier controlling the conformational switch of helix 12, and identify a Glu419-Lys531 salt bridge that "locks" the active conformation. The model is supported by cell-based transcriptional assays and ligand binding/unbinding kinetics experiments.
- **Visible evidence base** Full manuscript text including Introduction, Materials and Methods, Results, Discussion, Authors' Disclosures, Authors' Contributions, and Acknowledgments. Figures and tables are referenced but not provided in the supplied material.
- **Missing materials affecting confidence** Figures 1-6, Table 1, and Supplementary Figure S1 are referenced but not included. Experimental details for the luciferase assays and binding kinetics are described but raw data, statistical analyses, and replicate information are not fully provided. No supplementary methods or data files are available.

## Reviewer

- **Overall assessment** This manuscript presents a comprehensive computational and experimental study aimed at elucidating the molecular mechanisms underlying ligand-independent activation of ERα mutants in breast cancer. The combination of long-timescale MD simulations, free energy calculations, and experimental validation is ambitious and potentially valuable. The proposed "spring-loading" model is conceptually appealing and could have broader implications for understanding conformational regulation in nuclear receptors. However, several technical concerns regarding the computational methodology, the interpretation of free energy results, and the strength of experimental validation need to be addressed before the conclusions can be fully accepted.

- **Who would be interested in the results, and why** Researchers in the fields of structural biology, computational biophysics, and cancer biology, particularly those studying nuclear receptor signaling, endocrine resistance in breast cancer, and the molecular mechanisms of activating mutations. The methodological approach combining long-timescale simulations with free energy calculations may also interest computational biologists working on conformational transitions in proteins.

- **Major strengths** The study addresses a clinically relevant problem with a sophisticated computational approach. The use of microsecond-scale simulations on Anton is a significant technical achievement. The identification of distinct mechanisms for Y537S versus D538G mutations is an important insight. The experimental validation using transcriptional assays and binding kinetics strengthens the computational predictions. The "spring-loading" model provides a clear conceptual framework that could guide future studies.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of free energy calculations
- **Claim pointer** The authors claim that BEUS free energy calculations provide quantitative energetic differences between the buried and solvent-exposed states of Leu536 across the four systems, with differences of 2.00-2.75 kcal/mol.
- **Evidence pointer** Methods section "BEUS-free energy calculation"; Results section "Computation of energy profiles for the buried versus solvent-exposed transition for Leu536"
- **Concern** The description of the BEUS calculations lacks critical details needed to assess convergence and accuracy. The reaction coordinate is defined as a coordination number between Leu536 side-chain heavy atoms and all other protein heavy atoms, which is a complex collective variable that may not capture the relevant conformational transition adequately. The manuscript does not report the number of umbrella sampling windows used for each system beyond stating 23 windows, the total simulation time per window (stated as 100 ns), or the convergence criteria beyond "the resulting free energy profile no longer changed with additional sampling." More critically, the choice of a coordination number as the reaction coordinate may not adequately describe the Leu536 conformational transition, as it does not distinguish between different orientations or packing arrangements of the side chain. The authors should provide convergence tests, error estimates from block analysis, and validation that the chosen reaction coordinate captures the relevant transition pathway.
- **Why it matters** The quantitative free energy differences are central to the "spring-loading" model. If the calculations are not converged or the reaction coordinate is inadequate, the energetic conclusions may be unreliable, undermining the core mechanistic claims.
- **Resolution test** Provide convergence plots showing free energy profiles as a function of simulation time, block error analysis, and a comparison of the free energy profiles obtained with different reaction coordinates or collective variable definitions. Additionally, the authors should demonstrate that the free energy differences are robust to the choice of force field parameters and system preparation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation strength
- **Claim pointer** The authors claim that the Glu419-Lys531 salt bridge is critical for the constitutive activity of Y537S and D538S mutants, based on luciferase assays showing reduced activity when the salt bridge is disrupted by E419A or K531A mutations.
- **Evidence pointer** Results section "The transcriptional activity of constitutively active mutant ERs relies on formation of the glu419–lys531 salt bridge"; Methods section "Activity of ER single and double mutants in breast cancer cells by luciferase assay"
- **Concern** The experimental validation is described with insufficient detail. The luciferase assay section does not report the number of independent experiments, statistical methods used, or effect sizes with confidence intervals. The text states that E419A "diminishing their activity to nearly that of WT ER" and K531A "also having a marked effect," but no quantitative data or statistical analysis is presented. Furthermore, the authors do not address whether the E419A or K531A mutations might affect protein expression levels, protein stability, or folding, which could confound the interpretation of reduced transcriptional activity. The binding kinetics experiments are described even more briefly, with no data shown.
- **Why it matters** The experimental data are presented as supporting evidence for the computational model. Without proper statistical reporting and controls for protein expression/stability, the strength of this validation is unclear. The claim that the salt bridge is critical for constitutive activity requires robust experimental support.
- **Resolution test** Provide quantitative data with error bars and statistical tests for the luciferase assays, including at least three independent experiments. Include Western blot or other expression level controls to ensure that the mutations do not affect protein stability. Present the binding kinetics data with fitted rate constants and confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of structural data
- **Claim pointer** The authors state that "the Y537S mutation changes the hydrogen-bonding partner from Asn348 to Asp351" and that this "optimized hydrogen bond acts as a 'latch'" based on MD simulations.
- **Evidence pointer** Results section "Specific point mutations change the dynamics of known hydrogen-bonding contacts for residue 537 in the H11–12 loop of ERα"; Figure 1 (not provided)
- **Concern** The claim that the Y537S mutation changes the hydrogen-bonding partner is based on the analysis of MD trajectories, but the manuscript does not provide quantitative measures of hydrogen bond occupancy or stability. The histogram in Figure 1 (not visible) is described qualitatively. The authors should report the fraction of simulation time during which specific hydrogen bonds are formed, the distances and angles distributions, and whether these observations are consistent across all replicates. Additionally, the statement that the Asp351 interaction is "optimized" in the mutant is not supported by quantitative energetic analysis.
- **Why it matters** The shift in hydrogen-bonding partner is a key mechanistic element of the proposed model. Without quantitative characterization, the claim remains qualitative and could be an artifact of the specific simulation conditions.
- **Resolution test** Provide hydrogen bond occupancy analysis with time series and distributions for each system, including error estimates across replicates. Show that the observed hydrogen-bonding patterns are stable and reproducible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the model
- **Claim pointer** The authors propose that the "spring-loading" model and the identified salt bridge mechanism "could also prove useful in studying the functional nature of aberrant receptor signaling due to mutations in other ligand-regulated proteins."
- **Evidence pointer** Discussion section "The H11–12 spring force keeping WT-ER LBD off in the absence of ligand gives it the 'fly-casting' characteristics of intrinsically disordered domains and results in a pronounced ligand-dependent on–off character"
- **Concern** The generalizability claim is speculative and not supported by data from other systems. While the model is plausible for ERα, the authors do not provide evidence that similar mechanisms operate in other nuclear receptors or ligand-regulated proteins. The discussion of "fly-casting" and intrinsically disordered domains is interesting but not directly tested in this study.
- **Why it matters** Overstating the generalizability of the model could mislead readers into assuming broader applicability than is warranted by the evidence.
- **Resolution test** Either temper the generalizability claims or provide additional analysis (e.g., sequence conservation analysis, structural comparisons with other nuclear receptors) to support the broader applicability.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Methods section "Equilibrium MD simulations"
- **Evidence pointer** Methods section "Equilibrium MD simulations"
- **Issue** The manuscript states that simulations were performed at 310 K and 1.0 atm but does not specify the exact number of atoms in each system, the water box dimensions, or the ionic concentration. The choice of the CHARMM36 force field is justified, but the protocol for parameterizing the E2 ligand is not described in detail.
- **Required correction** Provide system size details, ion concentration, and a description of how ligand parameters were assigned and validated.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "The transcriptional activity of constitutively active mutant ERs relies on formation of the glu419–lys531 salt bridge"
- **Evidence pointer** Results section "The transcriptional activity of constitutively active mutant ERs relies on formation of the glu419–lys531 salt bridge"
- **Issue** The luciferase assay results are described qualitatively without reporting the number of replicates, error bars, or statistical significance.
- **Required correction** Include a figure with quantitative data, error bars, and statistical analysis (e.g., t-tests or ANOVA) for all comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figures 1-6 and Table 1
- **Evidence pointer** Results sections referencing Figures 1-6 and Table 1
- **Issue** The figures and table are not provided in the manuscript text, making it impossible to assess the quality of the data presentation and the validity of the visual interpretations.
- **Required correction** Ensure that all figures and tables are included in the submission and are of sufficient resolution to evaluate the data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Discussion section "The Y537S- and D538G-activating mutations use distinct mechanisms to overcome the spring-like nature of H11–12 and access the active conformation without bound ligand"
- **Evidence pointer** Discussion section "The Y537S- and D538G-activating mutations use distinct mechanisms to overcome the spring-like nature of H11–12 and access the active conformation without bound ligand"
- **Issue** The terms "spring-loading," "latch," and "lock" are used somewhat interchangeably throughout the manuscript, which could lead to confusion about the specific roles of different structural elements.
- **Required correction** Define each term clearly at first use and use them consistently throughout the manuscript.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction and Discussion
- **Issue** The manuscript does not discuss alternative models or competing hypotheses for ligand-independent activation of ERα mutants, such as changes in protein dynamics or allosteric effects beyond the H11-12 loop.
- **Required correction** Add a brief discussion of alternative models and how the proposed mechanism differs from or complements them.

## Risk / unsupported claims
- The claim that the free energy differences of 2.00-2.75 kcal/mol quantitatively distinguish the four systems is not fully supported without convergence analysis and error estimates.
- The claim that the Glu419-Lys531 salt bridge is critical for constitutive activity is not quantitatively supported by the experimental data as presented.
- The generalizability of the "spring-loading" model to other ligand-regulated proteins is speculative and not supported by data from other systems.
- The claim that the Y537S mutation forms an "optimized" hydrogen bond with Asp351 is not quantitatively supported by hydrogen bond occupancy analysis.
- The statement that the D538G mutation "relaxes" loop strain is inferred from free energy profiles but not directly validated experimentally.
- The relevance of the computational model to the clinical behavior of these mutants in patients is not directly addressed, and the clinical implications are stated without supporting evidence.