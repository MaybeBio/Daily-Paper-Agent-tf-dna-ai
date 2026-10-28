## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency of the presented evidence
- **Shared manuscript claim summary** The authors propose that T7 DNA polymerase actively and sequentially displaces monomeric T7 SSB (gp2.5) from ssDNA during lagging-strand synthesis, via direct physical interaction mediated by the SSB C-terminal tail, rather than relying on passive dissociation or collective pushing of SSBs.
- **Visible evidence base** Single-molecule optical tweezers measurements, dual-color fluorescence imaging, FRET experiments, AWSER coarse-grained molecular dynamics simulations, and bulk primer extension assays
- **Missing materials affecting confidence** Raw trajectory data, full statistical reporting for all comparisons, supplementary figures referenced but not provided in the submitted text, simulation parameter details, and control experiments for FRET specificity

## Reviewer
- **Overall assessment** The manuscript addresses a fundamental question in DNA replication, namely how a replicative polymerase overcomes the barrier posed by high-affinity SSB proteins. The combination of single-molecule force spectroscopy, fluorescence imaging, and molecular dynamics is ambitious and potentially powerful. However, the current presentation has several issues that prevent full confidence in the conclusions. The central claim of "active" displacement is supported by indirect evidence, and the distinction between active displacement and facilitated dissociation is not clearly established. The FRET experiments, which are critical for the direct interaction claim, are described with insufficient detail and appear to have limited statistical power. The simulation results are suggestive but the connection to the experimental timescales and conditions is not rigorously established. The manuscript would benefit from clearer presentation of the quantitative analysis and additional control experiments.

- **Who would be interested in the results, and why** Researchers studying DNA replication mechanisms, single-molecule biophysics, protein-nucleic acid interactions, and genome stability. The work is also relevant to those interested in how motor proteins overcome protein obstacles on DNA templates, a question that extends beyond SSB to other DNA-binding proteins. The methodological combination of force spectroscopy with fluorescence and simulation may interest method developers in the single-molecule community.

- **Major Strengths**
  - The combination of complementary techniques (force spectroscopy, fluorescence imaging, FRET, and simulation) is a notable strength and provides multiple lines of evidence.
  - The force-dependent modulation of SSB effects on replication is an interesting and potentially important observation.
  - The use of a C-terminal deletion mutant provides a clear experimental perturbation to test the proposed mechanism.
  - The manuscript is generally well-written and the figures appear to be of high quality based on the legends.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that "DNA polymerase actively and sequentially displaces single-stranded DNA-binding proteins" and that this occurs through "direct physical interaction" between the polymerase and the SSB C-terminal tail.
- **Evidence pointer** Figure 2, Figure 3, Results section "DNA polymerase sequentially displaces stationary SSBs" and "Active displacement of SSB by DNA polymerase"
- **Concern** The central claim of "active" displacement is not convincingly established. The experimental evidence shows that SSBs remain stationary while the polymerase advances, and that FRET signals are observed during pauses and backtracking. However, this does not distinguish between active displacement (where the polymerase exerts force to remove SSB) and facilitated dissociation (where the polymerase alters the local environment, e.g., by competing for binding or changing ssDNA conformation, thereby increasing the SSB off-rate). The comparison of the polymerase traversal rate (~200 nt/s, traversing an SSB footprint in 0.05 s) with the intrinsic SSB off-rate (~2.4 s⁻¹, corresponding to a residence time of ~0.4 s) shows that the polymerase arrives at an SSB much faster than spontaneous dissociation would occur. This is consistent with active displacement, but it is also consistent with a mechanism where the polymerase transiently pauses, and during that pause, the SSB dissociates with its intrinsic rate. The observation of pauses (Figure 2E, 3I) is actually consistent with this alternative interpretation. The authors need to provide more direct evidence that the polymerase actively destabilizes the SSB-DNA complex, for example by measuring the force-dependence of the displacement rate or by directly observing the SSB removal event with higher temporal resolution.
- **Why it matters** The distinction between active and passive displacement is the central conceptual claim of the paper. If the polymerase simply waits for spontaneous dissociation, the proposed "active" mechanism and the role of the C-terminal tail in "pulling" the polymerase forward would not be supported. This distinction has implications for understanding how polymerases and other motors deal with protein obstacles in general.
- **Resolution test** The authors should either (a) provide direct evidence of force exertion on the SSB during displacement, for example by measuring the displacement rate as a function of applied force and showing it is inconsistent with a purely passive mechanism, or (b) revise the claims to be consistent with a facilitated dissociation model, or (c) provide additional experimental evidence, such as single-molecule FRET with higher temporal resolution that can resolve the actual removal event and show it is coupled to polymerase advancement.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that FRET signals indicate "close protein proximity during encounters" and support "direct physical interaction" between DNA polymerase and SSB.
- **Evidence pointer** Figure 3G-I, Results section "Active displacement of SSB by DNA polymerase"
- **Concern** The FRET experiments are described with insufficient detail to assess their validity. The authors state that "FRET signals were detected during pausing events (6/8 cases) and backtracking events (2/8 cases), not observed during active replication." However, the following critical details are missing: (1) the number of total FRET events observed and the total number of pause/backtracking events analyzed, (2) the criteria for identifying a FRET signal, (3) the labeling positions on both proteins and the expected FRET efficiency for a direct interaction, (4) control experiments to rule out non-specific FRET due to random proximity or dye-dye interactions, and (5) the temporal resolution of the FRET measurements. The observation that FRET is only seen during pauses and backtracking, and not during active replication, is interesting but could also be explained by the polymerase and SSB being in close proximity only when the polymerase is stalled, without this proximity being functionally relevant for displacement. The authors also note that "not every pause or backtrack event produced a FRET signal," which raises questions about the specificity and sensitivity of the assay.
- **Why it matters** The FRET data is presented as key evidence for the direct interaction model. If the FRET measurements are not rigorously controlled and quantified, the claim of direct physical interaction is not supported. This is a central pillar of the proposed mechanism.
- **Resolution test** The authors should provide a complete description of the FRET methodology, including labeling positions, expected FRET efficiencies, control experiments (e.g., with a non-interacting protein or with the C-terminal deletion mutant), and a statistical analysis of the frequency of FRET events during different phases of polymerase activity. They should also discuss the temporal resolution limitations and how these affect the interpretation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that "optimal replication requires SSB saturation of ssDNA, establishing a delicate balance between protection and efficiency."
- **Evidence pointer** Figure 4D-F, Results section "The C-terminal tail and saturated SSB states: essential for DNA replication dynamics"
- **Concern** The claim that SSB saturation is required for optimal replication is based on bulk primer extension assays showing that wild-type SSB increases replication rate at concentrations above 150 nM, while the C-terminal deletion mutant decreases the rate. However, the interpretation of these bulk assays is complicated by several factors. First, the assay measures ensemble behavior, and the observed rate changes could be due to effects on polymerase processivity, initiation, or other factors not directly related to SSB displacement. Second, the claim of "saturation" is inferred from the concentration dependence, but no direct measurement of SSB occupancy on the ssDNA template is provided. Third, the authors do not discuss how the 17-nt ssDNA overhang in the primer extension assay relates to the longer ssDNA templates used in the single-molecule experiments. The single-molecule experiments were performed at 150 nM SSB, which is stated to be saturating, but the bulk assays show effects at concentrations up to 3000 nM. The relationship between these different concentration regimes is not clearly explained.
- **Why it matters** The claim about SSB saturation and the balance between protection and efficiency is presented as a key conclusion. If the evidence is not robust, this conclusion is weakened. The interpretation of the bulk assays needs to be more carefully connected to the single-molecule observations.
- **Resolution test** The authors should provide a more direct measurement of SSB occupancy on the ssDNA template under the conditions of the bulk assay, or at least discuss how the concentration dependence relates to the known binding affinity of gp2.5 for ssDNA. They should also clarify how the results from the bulk and single-molecule assays are related.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors use AWSER coarse-grained molecular dynamics simulations to support the active displacement model and claim that the C-terminal tail of SSB plays a key role in facilitating displacement.
- **Evidence pointer** Figure 3A-F, Results section "Active displacement of SSB by DNA polymerase", Methods section "Coarse-grained force field for protein-ssDNA system"
- **Concern** The simulation results are presented as supporting the experimental findings, but the connection between the simulations and the experiments is not rigorously established. The simulations use a coarse-grained model (AWSER) that has been previously benchmarked, but the specific system simulated (full-length gp2.5 with ssDNA, and the complex with DNA polymerase) is new. The authors do not provide sufficient details on the simulation setup, such as the length of the simulations, the number of replicas, the convergence of the free energy profiles, or the validation of the force field for this specific system. The free energy profiles show differences between the wild-type and C-terminal deletion mutant, but the statistical significance of these differences is not assessed. The claim that the C-terminal tail "anchors" to the DNA polymerase basic patch is based on a single representative structure, and it is not clear how robust this interaction is across the ensemble of simulations.
- **Why it matters** The simulations are used to provide a mechanistic explanation for the experimental observations. If the simulations are not rigorously validated and the results are not statistically robust, the mechanistic model is not well-supported.
- **Resolution test** The authors should provide more details on the simulation methodology, including convergence tests, error estimates on the free energy profiles, and an analysis of the ensemble of structures to demonstrate the robustness of the proposed C-terminal-basic patch interaction. They should also discuss the limitations of the coarse-grained model for capturing the details of the interaction.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Methods section "Analysis of single-molecule basepair-time traces"
- **Evidence pointer** Methods, location not provided
- **Issue** The description of the pause detection algorithm is vague. The authors state that a pause is defined as an event where the actual process duration is ten times greater than the expected time, but the details of how the "expected time" is calculated and how the threshold is applied are not fully specified.
- **Required correction** Provide a more detailed description of the pause detection algorithm, including the specific parameters used and how the threshold was determined.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 1D, 4F, and associated text
- **Evidence pointer** Figure legends, location not provided
- **Issue** The statistical reporting is inconsistent. Some comparisons report p-values, but the number of replicates, the type of statistical test used, and whether the data meet the assumptions of the test are not always stated. For example, in Figure 1D, the p-value is given, but the sample size and the test used are not specified in the legend.
- **Required correction** Ensure that all statistical comparisons report the sample size, the statistical test used, and the exact p-value. Consider reporting effect sizes and confidence intervals.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section, paragraph on force-dependent effects
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion of the force-dependent effects of SSB on replication is somewhat speculative. The authors suggest that the force-dependent modulation may be relevant in vivo, but they do not provide a concrete model for how this would occur.
- **Required correction** Either provide a more concrete model for the in vivo relevance of the force-dependent effects or temper the speculation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2F
- **Evidence pointer** Figure 2F legend, location not provided
- **Issue** The histogram in Figure 2F shows the distribution of distance changes, but the categories are not clearly defined. The text mentions "backtracking," "SSB displacement," and "stationary," but it is not clear how these categories were assigned.
- **Required correction** Provide a clear definition of the categories used in the histogram and describe the criteria for assigning events to each category.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "Coarse-grained force field for protein-ssDNA system"
- **Evidence pointer** Methods, location not provided
- **Issue** The description of the AWSER model and its parameters is brief and refers to previous work. For a non-specialist reader, it is difficult to assess the validity of the simulations without more detail.
- **Required correction** Provide a more complete description of the simulation parameters, including the specific AWSER version used, the temperature, the integration time step, and the total simulation time.

## Risk / unsupported claims
- The claim of "active" displacement is not fully supported by the evidence, as the distinction between active displacement and facilitated dissociation is not clearly established.
- The claim of "direct physical interaction" between DNA polymerase and SSB is based on FRET data that is not fully described and may not be statistically robust.
- The claim that "optimal replication requires SSB saturation" is based on bulk assays that may not directly reflect the single-molecule conditions.
- The simulation results are presented as supporting the mechanism, but the statistical robustness and convergence of the simulations are not demonstrated.
- The statement that "this spatiotemporal coordination between DNAp and SSB is critical for resolving molecular collisions and may represent a general mechanism" is speculative and not directly tested in this work.