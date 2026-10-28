## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and figure legends (figures themselves not provided)
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors use molecular dynamics simulations to compare the SARS-CoV-2 wild-type spike protein with the B.1.1.7 variant, reporting that the D614G mutation reduces inter-chain salt bridge stability and increases flexibility near the fusion peptide, while the N501Y mutation reduces electrostatic binding affinity to ACE2 by displacing glutamine 498 from the interface
- **Visible evidence base** Text descriptions of RMSF, RMSD, salt bridge distance analyses, contact analyses, and linear interaction energy calculations; supplementary figure and table references cited but not provided
- **Missing materials affecting confidence** Figures, supplementary figures, tables, simulation parameter details, force field validation, convergence criteria, and raw trajectory data

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question regarding the molecular basis of increased transmissibility of the B.1.1.7 SARS-CoV-2 variant. The authors employ molecular dynamics simulations to investigate two key aspects: the effect of the D614G mutation on spike trimer dynamics and the effect of the N501Y mutation on RBD-ACE2 binding. The study design is reasonable and the findings are potentially interesting. However, the manuscript has several significant limitations that prevent the conclusions from being fully established. The simulation time of 200 ns for the trimeric spike protein is short for capturing large-scale conformational changes, and the lack of replicate simulations with detailed convergence analysis weakens the statistical basis of the claims. The reported reduction in electrostatic binding energy for the N501Y variant is counterintuitive given experimental evidence suggesting increased ACE2 binding affinity for this variant, and the authors do not adequately reconcile this discrepancy. The manuscript would benefit from additional validation, more detailed methodological reporting, and a more nuanced discussion of how the simulation results relate to experimental observations.
- **Who would be interested in the results, and why** Researchers studying SARS-CoV-2 evolution, spike protein structure and dynamics, viral entry mechanisms, and computational virology. The findings on salt bridge rearrangements and fusion peptide flexibility could inform understanding of how mutations affect spike protein function and potentially guide experimental studies on viral entry and fusion.
- **Major strengths** The study addresses a clinically relevant question using atomistic simulations. The authors examine both the trimeric spike protein and the RBD-ACE2 complex, providing a more comprehensive view than studying isolated domains. The analysis of salt bridge dynamics and the distinction between pre- and post-cleavage states is thoughtful. The inclusion of a D614G-only mutant helps isolate the contribution of this specific mutation.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The study addresses a timely question but the approach is largely derivative of existing MD simulation studies on SARS-CoV-2 spike protein. Scientific importance: The question of how B.1.1.7 mutations affect spike function is important, but the conclusions are not sufficiently supported by the evidence presented. Interdisciplinary readership: The topic would interest structural biologists, virologists, and computational biologists, but the presentation is too specialized for a broad readership. Technical soundness: Several methodological concerns undermine confidence in the results, including short simulation times, limited replicates, and lack of convergence analysis. Readability for nonspecialists: The manuscript is written in a technical style that assumes familiarity with MD simulation terminology and would be challenging for nonspecialists to follow.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an important question and the authors' approach is reasonable, but the technical limitations and the counterintuitive finding regarding reduced ACE2 binding affinity require substantial additional work before the conclusions can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the N501Y mutation reduces binding affinity between RBD and ACE2, as evidenced by reduced electrostatic interaction energy from −200 kcal/mol in wild-type to −165 kcal/mol in B.1.1.7
- **Evidence pointer** Results section "The N501Y mutation lowers electrostatic binding in B.1.1.7", Figure 3, Table 4
- **Concern** The finding of reduced electrostatic binding energy for the N501Y variant contradicts multiple experimental studies that report increased ACE2 binding affinity for the N501Y mutation. The authors do not address this discrepancy or provide experimental validation. Furthermore, the linear interaction energy method used here is an approximate approach, and the reported difference of 35 kcal/mol may not be meaningful without free energy perturbation calculations or experimental binding assays. The authors also report MM/GBSA calculations that "imply" reduced binding but do not show the data.
- **Why it matters** The claim of reduced ACE2 binding affinity is a central conclusion of the manuscript and directly contradicts the prevailing understanding that N501Y enhances receptor binding. If this claim is incorrect, the interpretation of the results and the proposed mechanism for increased transmissibility would be substantially weakened.
- **Resolution test** The authors should either provide experimental binding data (e.g., surface plasmon resonance, biolayer interferometry) comparing wild-type and N501Y RBD binding to ACE2, or perform more rigorous free energy calculations (e.g., FEP or TI) to validate the linear interaction energy results. They should also discuss how their finding relates to published experimental data showing increased binding affinity for N501Y.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the D614G mutation induces increased flexibility near the fusion peptide through salt bridge rearrangements, based on 200 ns MD simulations of the trimeric spike protein
- **Evidence pointer** Results section "D614G induces flexibility around the fusion peptide via salt bridge rearrangement", Figures 1-2, Tables 1-2
- **Concern** The simulation time of 200 ns is short for a large trimeric protein complex, and the authors do not provide evidence of convergence. The manuscript does not report the number of replicate simulations, the equilibration protocol in sufficient detail, or the system size. The analysis of salt bridge occupancy is based on distance criteria, but the authors do not report the statistical significance of the differences between wild-type and B.1.1.7. The claim that the D614G mutation causes the observed flexibility changes is based on comparison between wild-type and B.1.1.7, which contains multiple mutations, and the D614G-only simulation is only used to partially address this.
- **Why it matters** The central mechanistic claim of the manuscript depends on the reliability of the MD simulations. Without evidence of convergence, adequate sampling, and statistical analysis, the observed differences in flexibility and salt bridge occupancy could be due to insufficient sampling rather than genuine biological differences.
- **Resolution test** The authors should provide convergence analysis (e.g., RMSD vs time plots, block averaging), report the number of replicates, and perform statistical tests to demonstrate that the observed differences are significant. They should also consider longer simulations or enhanced sampling methods to ensure that the conformational space is adequately explored.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that they used the Amber MD software package with the ff14SB force field and followed a "previously applied protocol" (reference 33)
- **Evidence pointer** Methods section "Molecular dynamics simulations"
- **Concern** The methods section lacks critical details needed for reproducibility. The authors do not report the specific version of the ff14SB force field parameters, the water model parameters, the salt concentration, the number of atoms in each system, the temperature and pressure coupling parameters beyond the Berzelius thermostat, or the specific commands used for the simulations. The reference to a "previously applied protocol" is insufficient without specifying which parameters were used. The use of hydrogen mass repartitioning with a 4 fs time step is mentioned, but the authors do not discuss potential artifacts associated with this approach.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publications. Without sufficient methodological detail, other researchers cannot replicate the simulations or assess the validity of the results.
- **Resolution test** The authors should provide a complete description of the simulation setup, including all force field parameters, system composition, equilibration protocol, and production run parameters. They should also make the input files and trajectories available or provide sufficient detail for others to reproduce the simulations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that the B.1.1.7 variant shows increased flexibility in the fusion peptide region and that this might explain higher transmissibility
- **Evidence pointer** Results sections "Flexibility of the spike trimer" and "D614G induces flexibility around the fusion peptide via salt bridge rearrangement", Figures 1-2
- **Concern** The manuscript does not provide the actual figures or supplementary figures for review, making it impossible to assess the quality of the data presentation. The text descriptions of RMSF differences and salt bridge analyses are insufficient to evaluate whether the observed effects are biologically meaningful. The authors do not provide quantitative comparisons with error bars or statistical tests for the RMSF differences. The claim that increased flexibility "might explain higher transmissibility" is speculative and not directly supported by the simulation data.
- **Why it matters** The central conclusions of the manuscript depend on the quality and interpretation of the simulation data. Without access to the figures and without proper statistical analysis, the evidence for the claimed effects cannot be evaluated.
- **Resolution test** The authors should provide the figures and supplementary data for review, include error bars and statistical tests for all quantitative comparisons, and temper the claims about transmissibility to reflect the speculative nature of the connection between simulation results and viral infectivity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the B.1.1.7 variant shows "enhanced infectiousness" and that the results "might explain the higher infectivity of B.1.1.7," but the simulations do not directly measure infectivity. The causal link between the simulation results and viral transmissibility is speculative.
- **Required correction** The authors should clarify in the abstract that the simulations provide hypotheses about molecular mechanisms that require experimental validation, rather than directly explaining higher infectivity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section
- **Evidence pointer** Results section "Flexibility of the spike trimer", location not provided
- **Issue** The authors state that "highest RMSF values were calculated for the RBD with flexibility of up to 10 Å" but do not provide a comparison with experimental B-factor data or other validation of the simulation results.
- **Required correction** The authors should compare their simulation results with available experimental structural data to validate the simulations, or acknowledge the lack of such validation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section, location not provided
- **Issue** The authors suggest that reduced electrostatic affinity could allow "faster dissociation of the S protein RBD-ACE2 complex," but this interpretation is not directly supported by the simulation data, which only show reduced interaction energy, not dissociation kinetics.
- **Required correction** The authors should either provide additional simulations or experimental data to support the kinetic interpretation, or revise the discussion to acknowledge that the relationship between interaction energy and dissociation kinetics is not direct.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Methods section
- **Evidence pointer** Methods section "Molecular dynamics simulations", location not provided
- **Issue** The authors state that simulations were performed "two times for all forms of the trimeric spike protein and four times for both forms of the RBD in complex with ACE2," but do not report whether these replicates were started from different initial velocities or different initial structures.
- **Required correction** The authors should clarify the setup of the replicate simulations to allow assessment of sampling independence.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction and Discussion sections, location not provided
- **Issue** The authors do not discuss experimental studies on the B.1.1.7 spike protein that have been published since the emergence of this variant, including studies on ACE2 binding affinity and cell entry efficiency.
- **Required correction** The authors should place their findings in the context of the broader literature on B.1.1.7, including experimental studies that may support or contradict their simulation results.

## Risk / unsupported claims
- The claim that the N501Y mutation reduces RBD-ACE2 binding affinity is not supported by experimental evidence and contradicts published studies showing increased binding affinity for this variant
- The claim that increased flexibility near the fusion peptide "might explain the higher infectivity of B.1.1.7" is speculative and not directly supported by the simulation data
- The claim that salt bridge rearrangements induced by D614G "could allow faster insertion of the fusion peptide into the host cell membrane" is speculative
- The claim that reduced electrostatic affinity could lead to "faster dissociation of the S protein RBD-ACE2 complex" is not directly supported by the simulation data
- The statistical significance of the reported differences in RMSF values and salt bridge occupancies between wild-type and B.1.1.7 is not established
- The convergence of the MD simulations is not demonstrated, and the short simulation time (200 ns for the trimer) may be insufficient for reliable conclusions