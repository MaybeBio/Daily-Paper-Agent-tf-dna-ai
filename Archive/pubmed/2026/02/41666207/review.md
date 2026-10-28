## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methodology, results, discussion, conclusion, supporting information references)
- **Assessment boundary** Computational findings only; no experimental validation data provided
- **Shared manuscript claim summary** The authors claim that stomidazolone binds to the ACTL domain of the bHLH transcription factor MUTE with high affinity, forming a stable complex characterized by specific hydrogen bonds (Arg62, Ser69, Glu163), reduced conformational flexibility, and altered inter-domain communication, thereby providing a molecular mechanism for its experimentally observed inhibition of stomatal differentiation.
- **Visible evidence base** DFT calculations (HOMO/LUMO, MESP, global reactivity descriptors), molecular docking (MOE), 300 ns all-atom MD simulations (GROMACS), RMSD/RMSF/Rg/SASA analyses, DCCM, PCA, FEL, multiple sequence alignment
- **Missing materials affecting confidence** Coordinates of the AlphaFold model used; docking scores and enrichment metrics; force field parameters for the ligand; convergence criteria for MD simulations; replicate simulations; statistical significance tests for RMSD/RMSF differences; raw trajectory data; experimental binding affinity data; details of the Nakagawa et al. binding site definition

## Reviewer
- **Overall assessment** This manuscript presents a purely computational investigation of stomidazolone binding to the MUTE ACTL domain. The workflow is standard and internally consistent, but the scientific advance over the prior experimental work of Nakagawa et al. is incremental. The central claims regarding stable complex formation and functional inhibition are supported by the simulations only in a weak sense, as the observed differences between Apo and complex states are modest and the functional interpretation is speculative. The manuscript would benefit from a clearer articulation of what is genuinely new here, and from a more rigorous treatment of simulation uncertainty and validation.
- **Who would be interested in the results, and why** Researchers working on chemical biology of plant development, specifically those interested in small-molecule modulation of transcription factors. The work may also be of interest to computational chemists studying protein-ligand interactions in plant systems, and to groups developing drought-resilience strategies through stomatal manipulation. The residue-level interaction map could inform future medicinal chemistry efforts, though the immediate utility is limited by lack of experimental validation.
- **Major strengths** The study addresses a relevant biological question with potential agricultural applications. The computational pipeline is comprehensive, combining DFT, docking, and MD with multiple post-simulation analyses. The identification of specific residues (Arg62, Ser69, Glu163) provides testable hypotheses for mutagenesis. The authors appropriately acknowledge the limitations of computational approaches and outline clear experimental validation strategies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no experimental validation), R1-M2 (no docking validation), R1-M3 (no replicate simulations), R1-M4 (overinterpretation of functional significance)
- **Assessment against Nature-style criteria** Originality: Moderate. The concept of targeting transcription factors with small molecules is not new, and the specific target (MUTE) was already identified by Nakagawa et al. The novelty here is limited to the computational characterization of binding, which is incremental. Scientific importance: Moderate. Understanding stomatal regulation is important for crop engineering, but the current study does not establish functional significance beyond what was already known experimentally. Interdisciplinary readership: Limited. The work is primarily of interest to plant biologists and computational chemists; the broader significance for general readers is not clearly articulated. Technical soundness: Adequate but with notable gaps. The methods are standard and generally well-executed, but the lack of validation, replicates, and statistical rigor weakens the conclusions. Readability for nonspecialists: Acceptable. The manuscript is clearly written, though some sections are repetitive and the functional interpretation in the discussion goes beyond what the data support.
- **Recommendation posture** Currently not established from the provided evidence. The computational results are plausible but do not, on their own, establish the claimed molecular mechanism of inhibition. The manuscript would require substantial additional work, including experimental validation or at minimum rigorous computational benchmarking, before the central claims could be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The manuscript claims that stomidazolone binding to MUTE "effectively suppresses stomatal differentiation" and that the identified interactions "underpin its inhibitory effect."
- **Evidence pointer** Abstract; Section 3.5; Section 3.6; Section 4
- **Concern** The central functional claim, that stomidazolone inhibits stomatal differentiation through the identified molecular interactions, rests entirely on prior experimental work by Nakagawa et al. The present study provides no new experimental data, and the computational results are correlative rather than causal. The simulations show that stomidazolone binds to MUTE in a stable manner, but this does not demonstrate that this binding is responsible for the observed biological inhibition. Alternative mechanisms, such as off-target effects, aggregation, or interference with upstream regulators, are not addressed.
- **Why it matters** The stated significance of the work, as a molecular-level explanation of stomidazolone's inhibitory mechanism, cannot be established without experimental validation. As presented, the study is a characterization of a binding mode, not a mechanistic elucidation.
- **Resolution test** The claim would be supported if the authors provided experimental evidence, such as mutagenesis of Arg62, Ser69, and Glu163 showing loss of inhibition, or binding assays (ITC, SPR) confirming the predicted affinity and stoichiometry. Alternatively, the manuscript should be reframed as a computational prediction with clearly stated hypotheses to be tested.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that docking identified the "most favorable binding sites and key interacting residues" and that the resulting complex was used for MD simulations.
- **Evidence pointer** Section 2.3; Section 3.5
- **Concern** No docking scores, enrichment metrics, or comparison with alternative binding poses are reported. The selection of the "best" pose appears to be based solely on the lowest docking score, but no information is given on the distribution of scores, the structural diversity of top poses, or whether the chosen pose is representative. Furthermore, the binding site was "abstracted from the work of Nakagawa et al.," but the details of this site are not described, making it impossible to assess whether the docking was constrained appropriately or whether the site is biologically relevant.
- **Why it matters** Docking is highly sensitive to pose prediction and scoring. Without validation, the identified interactions may be artifacts of the scoring function rather than genuine binding determinants. The subsequent MD simulations inherit any errors from the initial pose.
- **Resolution test** The authors should report docking scores for all generated poses, the RMSD between top-scoring poses, and a comparison of the chosen pose with any experimental structural data. Ideally, cross-docking or self-docking validation should be performed. If the binding site is known from prior work, a description of how it was defined and why it is appropriate should be provided.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that the complex is more stable and compact than the Apo state, based on RMSD, RMSF, and Rg analyses.
- **Evidence pointer** Section 3.6; Section 3.7; Section 3.8; Fig 3; Fig 4; Fig 5
- **Concern** All MD results are derived from a single simulation per system. No replicate simulations are reported, and no block averaging or statistical error analysis is provided. The reported differences in RMSD (1.45 vs 1.65 nm) and Rg (1.89 vs 1.97 nm) are small and may not be statistically significant. The RMSF differences for individual residues are described qualitatively without confidence intervals. The claim that the complex is "more stable" is therefore not supported by the data as presented.
- **Why it matters** Molecular dynamics simulations are stochastic, and single trajectories can be misleading. Without replicates or error estimates, the observed differences between Apo and complex states cannot be distinguished from thermal noise.
- **Resolution test** The authors should run at least three independent simulations per system (ideally more) and report mean values with standard deviations or standard errors. Statistical tests (e.g., t-test or Mann-Whitney U test) should be applied to the RMSD, Rg, and RMSF distributions. Alternatively, the claims should be softened to describe trends rather than significant differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The manuscript claims that the observed changes in correlated motion (DCCM), reduced conformational space (PCA/FEL), and decreased solvent accessibility (SASA) upon ligand binding "support a mechanism of conformational inhibition" and that this "likely prevents heterodimerization with SCRM."
- **Evidence pointer** Section 3.9; Section 3.10; Section 3.11; Section 3.12; Section 3.13
- **Concern** The functional interpretation of the biophysical observables is speculative. Reduced conformational flexibility and altered correlation patterns do not necessarily imply inhibition of protein-protein interactions. The link between the observed changes and the specific disruption of MUTE-SCRM heterodimerization is not demonstrated. The authors do not simulate the MUTE-SCRM complex, nor do they provide any binding free energy calculations for the dimerization interface in the presence versus absence of stomidazolone.
- **Why it matters** The proposed mechanism of action, that stomidazolone stabilizes MUTE in a conformation incompatible with SCRM binding, is a central claim of the manuscript. Without direct evidence, this remains a hypothesis.
- **Resolution test** The authors could perform MD simulations of the MUTE-SCRM complex in the presence and absence of stomidazolone, or calculate binding free energies (e.g., MM-PBSA) for the dimerization interface. Alternatively, the claim should be explicitly framed as a hypothesis requiring experimental testing.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The DFT calculations are described as being performed "in a vacuum condition," but the rationale for this choice is not given. Since the docking and MD simulations are performed in implicit or explicit solvent, the relevance of gas-phase DFT results to the biological context is unclear.
- **Required correction** Provide a brief justification for the vacuum condition, or acknowledge this as a limitation and discuss how it might affect the interpretation of the electronic properties.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The MD simulation protocol states that the system was solvated in a cubic box, but the box size and the minimum distance between the protein and the box edges are not reported. The number of water molecules and ions is also not specified.
- **Required Correction** Provide the box dimensions, the number of water molecules and ions, and the minimum solute-to-box distance to ensure the simulations are reproducible.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.5
- **Evidence pointer** Section 3.5; Fig 2
- **Issue** The interaction diagram in Fig 2 is described in the text, but the figure itself is not available in the provided material. The description mentions hydrogen bonds, van der Waals contacts, and electrostatic interactions, but the specific residues involved in each type of interaction are not fully enumerated in the text.
- **Required Correction** Ensure the figure is included and that the text provides a complete list of interacting residues and the type of interaction for each.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.11
- **Evidence pointer** Section 3.11; Fig 8
- **Issue** The hydrogen bond analysis reports a mean number of 1.93 +/- 0.96, but it is not clear whether this is the mean over time for a single trajectory or averaged over multiple trajectories. The standard deviation is reported, but no confidence intervals are given.
- **Required Correction** Clarify the statistical treatment of the hydrogen bond data and report confidence intervals or standard errors.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 1; Section 4
- **Evidence pointer** Section 1; Section 4
- **Issue** The introduction and conclusion reference the prior work of Nakagawa et al. but do not provide a critical comparison of the present findings with that work. It is unclear what new information the computational study adds beyond the experimental observations.
- **Required Correction** Add a paragraph in the discussion explicitly comparing the computational predictions with the experimental data of Nakagawa et al., highlighting what is new and what is consistent.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The phrase "the catenated systems comprising of MUTE and stomidazolone" is awkward and potentially confusing. "Catenated" is not a standard term in this context.
- **Required Correction** Replace with "the systems comprising MUTE and stomidazolone" or "the MUTE-stomidazolone complex systems."

## Risk / unsupported claims
- The claim that stomidazolone "effectively suppresses stomatal differentiation" through the identified molecular mechanism is unsupported by the present data, as no functional assays are provided.
- The claim that the complex is "stable and compact" based on single MD trajectories is weakly supported and lacks statistical rigor.
- The claim that reduced conformational flexibility "likely prevents heterodimerization with SCRM" is speculative and not directly tested.
- The claim that the identified residues (Arg62, Ser69, Glu163) are "critical" for binding is based on a single docking pose and hydrogen bond occupancy analysis, without mutational or energetic validation.
- The DFT-derived electronic properties are presented as relevant to biological activity, but the connection between gas-phase quantum chemical descriptors and in vivo inhibition is not established.
- The statement that this study provides "the first mechanistic, residue-level insight" into stomidazolone binding to MUTE is a strong claim that cannot be fully evaluated without a comprehensive literature search, and the authors do not provide evidence that no prior computational study exists.