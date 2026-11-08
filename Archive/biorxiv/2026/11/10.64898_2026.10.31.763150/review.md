## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusion, methods, and supporting information list)
- **Assessment boundary** Scientific validity, methodological rigor, and interpretation of the reported molecular dynamics simulation study; no assessment of experimental wet-lab data beyond what is cited
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations to propose that serotonin (5-HT), without directly binding the Y4 receptor (Y4R), remodels the brain plasma membrane lipid environment in a concentration-dependent manner, which in turn rewires intramolecular communication pathways between residues implicated in PP binding and receptor activation/G-protein coupling.
- **Visible evidence base** Simulation trajectories (825.9 ns total across three conditions, five replicas each), density distributions, radial distribution functions, depletion-enrichment indices, contact frequencies, order parameters, area per lipid, bilayer thickness, WISP pathway analysis, mutual information analysis, RMSF, and tilt angle calculations
- **Missing materials affecting confidence** The full Results and Discussion section is not provided in the submitted text; only section headings are visible. Figures referenced (Figures 1-8, S1-S8) are not available for inspection. Simulation input files, force field parameter files, and convergence criteria are not provided. The specific numerical values for key analyses (e.g., D-E indices, contact frequencies, WISP node degeneracies) are not visible.

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive investigation into a plausible and interesting hypothesis: that serotonin can modulate Y4R function indirectly through membrane-mediated allosteric mechanisms rather than through direct receptor binding. The methodological framework is sophisticated, combining state-of-the-art all-atom MD simulations with network-based communication analysis. However, the manuscript as presented has substantial limitations that prevent full evaluation. The Results and Discussion section is essentially absent from the provided text, making it impossible to assess the actual findings, their statistical robustness, or the strength of the evidence supporting the central claims. The total simulation time (825.9 ns) is modest for the complexity of the system, and the production run length per replica (20 ns) is short for drawing conclusions about slow membrane reorganization processes. The connection between the observed lipid redistribution and functional consequences for Y4R signaling remains largely speculative, as acknowledged by the authors in places. The work is potentially interesting to the GPCR and membrane biophysics communities, but the current evidence base is insufficient to establish the mechanistic claims made.

- **Who would be interested in the results, and why** Researchers studying GPCR pharmacology, particularly those interested in allosteric modulation and membrane-mediated signaling mechanisms. The membrane biophysics community would find interest in the concentration-dependent effects of an amphiphilic neurotransmitter on a heterogeneous, asymmetric model membrane. Computational biophysicists developing and applying network-based communication analysis to membrane protein systems would also find methodological interest. Finally, those working on the neurobiology of serotonin and its relationship to metabolic and psychiatric disorders may find the conceptual framework relevant, though the direct physiological implications remain distant from the simulation evidence.

- **Major strengths** The study addresses a genuinely interesting and underexplored question: whether neurotransmitters can modulate GPCR function through membrane-mediated mechanisms without direct receptor contact. The use of a realistic, asymmetric, multi-component brain plasma membrane model is a significant improvement over simpler single-component systems. The combination of multiple analytical approaches (density, RDF, D-E index, contact frequency, order parameter, WISP, mutual information) provides a multi-faceted view of the system. The authors appropriately acknowledge limitations, including the absence of direct evidence for altered receptor activation and the correlational nature of the communication pathway analysis. The inclusion of two 5-HT concentrations (6 mM and 50 mM) allows for concentration-dependence assessment, and the comparison with a single-component POPC system provides a useful control.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims to demonstrate concentration-dependent rewiring of communication pathways between PP-binding and activation-associated residues of Y4R, and a connection between serotonin-dependent lipid reorganization and altered intra-receptor communication.
- **Evidence pointer** Results and Discussion section (not provided in full); Figures 4, 5, 7, 8; Tables in SI
- **Concern** The Results and Discussion section is not included in the submitted manuscript text. Only section headings are visible. This is the core evidence section of the paper, and without it, none of the central claims can be evaluated. The figures that would contain the quantitative results are also not available. It is impossible to assess whether the data support the conclusions, whether the statistical analyses are appropriate, or whether alternative interpretations have been considered.
- **Why it matters** The central claims of the paper, including the concentration-dependent rewiring of communication pathways and the connection between lipid reorganization and receptor communication, rest entirely on results that are not visible in the submitted material. A review cannot establish scientific validity without access to the primary evidence.
- **Resolution test** The full Results and Discussion section, including all figures with numerical values, error bars, and statistical comparisons, must be provided for evaluation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological sufficiency
- **Claim pointer** The authors claim that 5-HT induces selective lipid reorganization, enhanced lipid-chain ordering, and modest bilayer compaction in the heterogeneous BPM, and that these changes are linked to altered intra-receptor communication.
- **Evidence pointer** Methods section (Simulation Details); Table 1; Figure 6
- **Concern** The total simulation time is 825.9 ns across all systems, with production runs of only 20 ns per replica. Membrane lipid reorganization, particularly the redistribution of minor lipid species like PIP2, occurs on timescales that typically exceed hundreds of nanoseconds to microseconds. A 20 ns production run is very short for observing meaningful lipid redistribution around a large membrane protein. The equilibration protocol is described as proceeding until area per lipid converges, but the convergence criteria are not specified. Additionally, the use of only five replicas per condition, each with 20 ns of production, may not provide sufficient sampling for the WISP and mutual information analyses to be statistically robust.
- **Why it matters** The central mechanistic claim is that 5-HT causes lipid reorganization that in turn affects receptor communication. If the simulation timescales are insufficient to capture equilibrium lipid distributions, the observed effects may be artifacts of incomplete relaxation or initial conditions rather than genuine 5-HT-induced reorganization.
- **Resolution test** Provide evidence of convergence for all measured properties (e.g., block averaging, time evolution of D-E indices, contact frequencies, and WISP pathways). Justify the choice of 20 ns production runs, or extend simulations to demonstrate that the observed effects are stable over longer timescales.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive overreach
- **Claim pointer** The authors state that their findings "connect serotonin dependent selective lipid redistribution to altered intramolecular communication between Y4R residues associated with PP binding and G-protein coupling" and suggest implications for "lipid-targeted pharmacology as a complementary strategy to modulate GPCR allostery."
- **Evidence pointer** Abstract; Conclusion
- **Concern** The WISP analysis identifies communication pathways based on correlated motions in simulations. However, the functional significance of these pathways is inferred, not demonstrated. The authors acknowledge that their results do not directly demonstrate altered receptor activation or downstream signaling, yet the framing of the conclusions, particularly in the abstract and conclusion, implies a mechanistic connection that goes beyond what the simulation data can establish. The leap from "altered communication pathways in silico" to "a framework for lipid-targeted pharmacology" is substantial and not supported by the evidence presented.
- **Why it matters** The broader significance of the work, and its potential impact on the field, depends on whether the observed in silico changes in communication pathways have functional relevance. Without experimental validation or at least a more careful framing of the speculative nature of these connections, the conclusions risk overstating what has been demonstrated.
- **Resolution test** Either provide additional analysis that strengthens the link between communication pathway changes and functional outcomes (e.g., comparison with known activating/inactivating mutations, or free energy calculations), or substantially temper the conclusions to clearly distinguish demonstrated findings from speculative implications.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with experimental context
- **Claim pointer** The authors reference experimental evidence that 5-HT modulates PP-Y4R binding kinetics through membrane allostery (reference 10), and state that their simulations are consistent with this observation.
- **Evidence pointer** Introduction; Abstract
- **Concern** The experimental study referenced (ref 10) reportedly used a specific lipid composition that differs from the BPM model used here. The authors do not discuss how differences in lipid composition between the experimental system and their simulation model might affect the comparability of results. Furthermore, the experimental concentration of 5-HT used in ref 10 is not discussed in relation to the 6 mM and 50 mM concentrations chosen here. The relevance of 50 mM 5-HT, which is far above physiological concentrations, is not justified.
- **Why it matters** The claim of consistency with experimental observations is central to the paper's significance. If the simulation conditions differ substantially from the experimental conditions, the comparison may not be valid, and the physiological relevance of the findings becomes questionable.
- **Resolution test** Provide a detailed comparison of the experimental system (lipid composition, 5-HT concentration) with the simulation conditions, and justify the choice of 5-HT concentrations used, particularly the physiological relevance of 50 mM.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, last sentence
- **Evidence pointer** Abstract
- **Issue** The final sentence of the abstract states that the findings "provide a basis for exploring lipid-targeted therapeutics as an alternative to protein" but this is a significant overstatement given the purely computational nature of the study and the absence of any experimental validation of the proposed mechanism.
- **Required correction** Rephrase to indicate that the findings suggest a potential avenue for future investigation, rather than providing a basis for therapeutic development.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Methods, Simulation Details
- **Evidence pointer** Methods section
- **Issue** The equilibration protocol is described in detail, but the criteria for determining when the area per lipid "converges and attains equilibrium" are not specified. The reader cannot assess whether the equilibration was sufficient.
- **Required correction** Provide quantitative convergence criteria (e.g., drift thresholds, block averaging analysis) for the area per lipid and other key structural properties.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** WASP analysis, Mutual Information analysis
- **Evidence pointer** Methods section
- **Issue** The WASP analysis uses 300 paths, but the justification for this number is not provided. The mutual information analysis uses 500 permutations, which gives a minimum p-value of 0.002; this is reported as the p-value for all three concentrations, which is suspicious and suggests the test may be underpowered.
- **Required correction** Justify the choice of 300 paths for WASP. For the mutual information analysis, either increase the number of permutations to obtain more precise p-values or report the results differently (e.g., as p < 0.002).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 6
- **Evidence pointer** Figure 6 (referenced in text)
- **Issue** The text states that Figure 6 shows area per lipid, bilayer thickness, and order parameters, but the figure is not available for inspection. The description in the text is insufficient to determine what is actually shown.
- **Required correction** Ensure that all figures are included in the manuscript submission and that the figure captions are self-explanatory.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and clarity
- **Affected element** Throughout
- **Evidence pointer** Various sections
- **Issue** The manuscript contains several instances of awkward or unclear phrasing (e.g., "concnetrations" in the Results section, "stressed-lipid associated network" without clear definition). These detract from readability.
- **Required correction** Careful proofreading and editing for language clarity and consistency of terminology.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Quantum Chemical Calculation
- **Evidence pointer** Methods section
- **Issue** The authors state that the MP2/cc-pVDZ optimized geometry from ref 37 is used "without further re-optimization" and a single-point calculation is performed at B3LYP/6-311++G(d,p). The choice of this mixed approach is not justified, and it is unclear whether the B3LYP single-point calculation on an MP2 geometry is appropriate for deriving CHELPG charges.
- **Required correction** Provide justification for the mixed basis set/level of theory approach, or perform the optimization and charge derivation at a consistent level of theory.

## Risk / unsupported claims
- The claim that 5-HT "rewires" communication pathways in Y4R is based solely on computational analysis of correlated motions and is not validated by any functional assay or experimental measurement. This is acknowledged by the authors but the framing in the abstract and conclusion overstates the strength of the evidence.
- The connection between PIP2 enrichment at the receptor interface and altered communication pathways is correlational; no causal mechanism is established.
- The physiological relevance of the findings is unclear, particularly given the use of 50 mM 5-HT, which is far above physiological concentrations (typically in the micromolar range or lower in the brain).
- The claim that the results are "consistent with" experimental observations of 5-HT-mediated modulation of PP-Y4R binding kinetics cannot be fully evaluated without the full Results section and without a detailed comparison of the experimental and simulation conditions.
- The statement that the findings "provide a basis for exploring lipid-targeted therapeutics" is unsupported by the evidence, as no therapeutic implications are demonstrated or tested.
- The assertion that the BPM model "captures the essential biophysical properties and lipid asymmetry conserved in human neuronal membranes" is taken from the model's original publication (ref 20) and is not independently validated in this work.
- The claim that 5-HT does not directly interact with Y4R is based on RDF analysis, but the absence of close contacts in simulations does not rule out weak or transient interactions that may occur on timescales not sampled.