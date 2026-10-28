## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure references
- **Assessment boundary** Scientific content, methodological rigor, claims versus evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors use multimicrosecond all-atom molecular dynamics simulations to show that gain-of-function mutations in λ Cro (Act3 and Act8) remodel interaction surfaces, reduce DNA engagement, alter C-terminal tail dynamics, and redistribute intramolecular communication, providing a mechanistic framework for how compact transcription factors evolve new regulatory functions
- **Visible evidence base** Simulation results including RMSF, hydrogen bonding, SASA/rSASA, contact analysis, dCNA, community detection, MM/GBSA binding energies, APBS electrostatics, and HADDOCK docking
- **Missing materials affecting confidence** Supplementary figures S1-S19 and Table 1 are referenced but not provided; force field validation data not shown; convergence assessments beyond RMSD not described in detail; docking results presented without statistical rigor

## Reviewer
- **Overall assessment** This manuscript presents a technically competent molecular dynamics study of an important model transcription factor, λ Cro, and its engineered gain-of-function variants. The simulations are extensive (5 μs per replicate, five replicates per system) and the analysis is multifaceted. However, the central claim that these mutations provide a "mechanistic framework" for understanding how transcription factors evolve new functions is only partially supported by the evidence presented. The study is largely descriptive, and the link between observed conformational/dynamic changes and the experimentally established gain-of-function phenotype remains speculative. The authors acknowledge several limitations, but key concerns about simulation convergence, force field accuracy, and the interpretation of MM/GBSA results need to be addressed before the mechanistic conclusions can be considered robust.

- **Who would be interested in the results, and why** Researchers in molecular biophysics, computational biology, and protein engineering would find this study relevant. Those studying transcription factor structure-function relationships, particularly small repressors like λ Cro and λ cI, would benefit from the detailed dynamic characterization. The work also speaks to the broader question of how minimal sequence changes can rewire protein interaction networks, which is of interest to synthetic biologists and those working on protein design. The methodological approach combining long-timescale MD with network analysis could serve as a template for similar studies.

- **Major strengths** 
  1. The simulation protocol is rigorous: 5 μs per replicate with five replicates per system across 18 systems represents a substantial computational investment, and the use of multiple analysis methods (contacts, hydrogen bonds, SASA, dCNA, MM/GBSA) provides a comprehensive view.
  2. The study directly addresses an experimentally characterized system, with clear links to prior work by Bushman et al. and Brödel et al., grounding the simulations in biological relevance.
  3. The authors are appropriately cautious in several interpretations, acknowledging limitations of MM/GBSA and the potential for protocol artifacts (e.g., the Watson-Crick pairing difference in Act3).
  4. The finding that the C-terminal tail plays a context-dependent role, with truncation specifically destabilizing Act3 but not Act8, is a concrete and testable prediction.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for mechanistic claims
- **Claim pointer** The abstract and discussion state that simulations "reveal that minimal sequence changes can reorganize interaction surfaces, shift DNA-binding modes, modulate binding affinities, and redistribute intramolecular communication pathways," and that these provide "a mechanistic framework for understanding how transcription factor sequence, structure, and dynamics reshape gene regulatory function."
- **Evidence pointer** Results sections "Cro Mutations Form a New Interaction Patch," "Cro's Disordered C-Terminal Tail Redistributes Interactions Based on Assembly State," "C-terminal Truncation Reduces DNA Binding in Act3 Cro," and "Cro Mutations Redistribute Contacts and Allosteric Coupling"; Figures 2-5 (referenced); Table 1 (referenced)
- **Concern** The manuscript claims a "mechanistic framework" but the evidence is largely correlative and descriptive. The simulations show changes in contacts, hydrogen bonding, and dynamics, but do not establish a causal link between these changes and the experimentally observed gain-of-function phenotype (dual repression/activation). The authors do not demonstrate that the proposed "interaction patch" actually binds RNA polymerase or other partners with altered affinity or specificity. The HADDOCK docking results are mentioned only briefly in the discussion and are not presented with sufficient detail or statistical analysis to support claims of differential binding.
- **Why it matters** The central scientific contribution claimed is mechanistic understanding. Without direct evidence linking the observed conformational changes to functional outcomes, the study remains a descriptive characterization of mutant dynamics. This distinction is critical for the paper's significance and for guiding future experimental validation.
- **Resolution test** The authors should either (a) provide quantitative evidence (e.g., free energy calculations, enhanced sampling) that the identified surface patch is more favorable for RNA polymerase binding in mutants versus wild type, or (b) temper the mechanistic claims to reflect that the simulations generate hypotheses that require experimental testing. If the latter, the discussion should be revised to clearly frame the work as hypothesis-generating rather than mechanism-establishing.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of binding energy calculations
- **Claim pointer** The manuscript states that MM/GBSA analyses show truncation reduces binding affinity specifically for Act3 (from −138.8 ± 6.2 to −112.8 ± 4.3 kcal/mol), and this is used to support the conclusion that the C-terminus maintains DNA binding in Act3.
- **Evidence pointer** Results section "C-terminal Truncation Reduces DNA Binding in Act3 Cro"; Table 1 (referenced)
- **Concern** The MM/GBSA results are presented as supporting evidence for differential binding, but the authors acknowledge that MM/GBSA "often overestimates absolute binding energies" and should be interpreted as "qualitative trends." However, the reported differences (approximately 26 kcal/mol for Act3) are then used to draw mechanistic conclusions. The standard errors reported (±6.2 and ±4.3 kcal/mol) suggest the difference is significant, but the methodology for calculating these errors is not described. Additionally, the analysis was performed only on frames where both subunits remained bound, which introduces a selection bias that could inflate apparent stability differences. The authors do not report whether the MM/GBSA results are consistent across individual replicates or whether the observed difference is driven by a single trajectory.
- **Why it matters** The conclusion that truncation specifically destabilizes Act3-DNA binding is a key finding. If the MM/GBSA results are not robust, this conclusion is unsupported. Given the acknowledged limitations of the method, the authors need to demonstrate that the observed difference is reproducible and not an artifact of the analysis protocol.
- **Resolution test** Provide per-replicate MM/GBSA values to show consistency, report the error calculation methodology, and consider using an alternative approach (e.g., umbrella sampling or metadynamics on the dissociation coordinate) to validate the relative binding affinities. If such validation is not feasible, the claims should be softened to reflect the qualitative nature of the evidence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Convergence and sampling adequacy
- **Claim pointer** The manuscript states that "multimicrosecond" simulations (5 μs per replicate) were performed and that postequilibration frames were used for analysis, with equilibration determined by RMSD stabilization after 200 ns.
- **Evidence pointer** Methods section "Molecular Dynamics Simulations" and "Simulation Analyses"; Figure 1 (referenced, RMSD data)
- **Concern** The authors use RMSD to determine equilibration, but RMSD stabilization is a necessary but not sufficient condition for convergence, particularly for flexible regions like the C-terminal tail and for protein-DNA interfaces. The manuscript does not report whether key observables (e.g., contact frequencies, hydrogen bond occupancies, tail conformations) have converged across replicates. For a system with a disordered tail and potentially multiple bound states, 5 μs may not be sufficient to sample the relevant conformational space, especially for the DNA-bound complexes. The authors do not discuss this limitation in the context of their conclusions.
- **Why it matters** If the simulations have not converged, the reported differences between wild type and mutants could reflect insufficient sampling rather than genuine biophysical differences. This is particularly relevant for the tail dynamics and the dissociation events observed in truncated Act3.
- **Resolution test** Show convergence metrics for key observables (e.g., block averaging or split-half analysis of contact maps and hydrogen bond occupancies) across replicates. If convergence is not demonstrated, the authors should acknowledge this as a limitation and temper claims about the robustness of the observed differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and methodological transparency
- **Claim pointer** The methods describe the use of the Dunbrack 2010 rotamer library for introducing mutations, the ff19SB force field, OPC water, and BSC1 DNA force field, with simulations run using Amber24 and pmemd.cuda.
- **Evidence pointer** Methods section "System Construction" and "Molecular Dynamics Simulations"
- **Concern** The manuscript does not provide sufficient detail for reproduction. Specifically: (1) the specific PDB structures used from the 1COP NMR ensemble are not identified (which model(s)?); (2) the protonation states of titratable residues are not described; (3) the salt concentration and ion placement protocol are not fully detailed; (4) the temperature and pressure coupling parameters are not specified; (5) the criteria for stopping simulations after dissociation are not defined; (6) the HADDOCK docking protocol is described only in the discussion without methodological detail. These omissions limit the reproducibility of the work.
- **Why it matters** Reproducibility is a core expectation for computational studies. Without complete methodological details, other groups cannot replicate or build upon these simulations, and the reliability of the conclusions cannot be independently assessed.
- **Resolution test** Provide a complete methods section with all simulation parameters, structure selection criteria, and analysis details. Include the HADDOCK docking protocol in the methods rather than the discussion. Consider depositing starting coordinates and key trajectories in a public repository.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Results section "Cro Mutations Form a New Interaction Patch"
- **Evidence pointer** Figures S1-S6 (referenced)
- **Issue** The text refers to "Figures S1-S6" for contact and hydrogen bonding data at residue positions 17, 21, 22, and 26, but does not clearly describe what each figure shows or how the data support the claims. The reader cannot assess the evidence without the supplementary material.
- **Required correction** Briefly describe the content of each supplementary figure in the text or figure legends, and explicitly state how the data support the conclusions drawn.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "C-terminal Truncation Reduces DNA Binding in Act3 Cro"
- **Evidence pointer** Table 1 (referenced)
- **Issue** The MM/GBSA values are reported as means with standard errors, but the number of samples (frames or replicates) used for the statistics is not stated. The authors also do not report whether the differences between full-length and truncated forms are statistically significant for each variant.
- **Required correction** Report the number of frames and replicates used for each MM/GBSA calculation, and provide statistical significance tests (e.g., t-tests or bootstrap confidence intervals) for the comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of docking results
- **Affected element** Discussion section
- **Evidence pointer** Figures S14-S19 (referenced)
- **Issue** The HADDOCK results are mentioned as showing "consistently more favorable binding of the α subunit" and "a slight preference for Act3 and Act8 over wild-type," but the differences are stated to be "within error." This is contradictory and the reader cannot evaluate the significance without seeing the scores and errors.
- **Required correction** Present the HADDOCK scores with their uncertainties in a table or figure, and clearly state whether the differences are statistically meaningful. If they are not, do not use them to support mechanistic claims.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "gain-of-function" is used throughout, but the manuscript does not clearly define what function is gained. The experimental work by Brödel et al. showed these variants act as dual-function transcription factors (both repression and activation), but the simulations do not directly measure transcriptional activity. The term should be used carefully to avoid implying that the simulations demonstrate the gain of function.
- **Required correction** Clarify that "gain-of-function" refers to the experimentally characterized phenotype, and that the simulations investigate the structural/dynamic correlates of this phenotype, not the phenotype itself.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The authors acknowledge that simulations began from experimentally determined structures and that 5 μs is short compared to biological timescales, but they do not discuss the potential impact of force field inaccuracies on their conclusions, particularly for protein-DNA interactions and disordered regions.
- **Required correction** Add a brief discussion of force field limitations for disordered regions and protein-DNA interfaces, and how these might affect the interpretation of the results.

## Risk / unsupported claims
- The claim that mutations create a "distinct interaction patch" suitable for RNA polymerase binding is inferred from surface properties and docking, but direct binding evidence is not provided. The docking results are presented as preliminary and within error, so this claim is not established.
- The statement that the C-terminal tail "acts as a structural probe" is metaphorical and not operationally defined. The evidence shows that the tail makes frequent contacts, but the functional significance of this behavior is speculative.
- The claim that "minimal sequence changes can reorganize interaction surfaces, shift DNA-binding modes, modulate binding affinities, and redistribute intramolecular communication pathways" is supported for the first three points (with caveats about MM/GBSA), but the redistribution of "intramolecular communication pathways" is based on dCNA community detection, which is a correlative analysis. The functional relevance of these community shifts is not demonstrated.
- The suggestion that "similar mechanisms underlie the gain-of-function mutations in other variants" is an extrapolation beyond the data, as only Act3 and Act8 were simulated. This is presented as an inference, which is acceptable, but it should be clearly labeled as speculation.
- The statement that the findings "offer a general framework for engineering compact regulators" is an overreach given the descriptive nature of the study and the lack of experimental validation.