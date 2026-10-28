## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided.
- **Assessment boundary** Scientific content, methodological soundness, and internal consistency of the reported computational study. No external validation or replication was performed.
- **Shared manuscript claim summary** The authors use atomistic molecular dynamics simulations to propose that the glucocorticoid receptor DNA-binding domain recognizes DNA through sequence-specific contacts within a moulded major groove, while RNA recognition is governed by shape-based, predominantly electrostatic interactions with hairpin motifs, and that this dual mechanism may extend to other zinc finger transcription factors.
- **Visible evidence base** Methods section, results and discussion sections, figures referenced (Figures 1-7), supplementary figures and tables referenced (Figures S1-S23, Tables S1), and data availability statement.
- **Missing materials affecting confidence** The actual figures, supplementary figures, tables, and movies referenced in the text were not provided. This limits verification of quantitative claims, trajectory analyses, and structural interpretations.

## Reviewer
- **Overall assessment** This manuscript presents a computational investigation into the dual recognition of DNA and RNA by the glucocorticoid receptor DNA-binding domain. The study addresses a timely and interesting question regarding the structural basis of transcription factor-RNA interactions. The authors employ a reasonable set of molecular dynamics simulations and analyses to support their conclusions. However, the absence of the actual figures and supplementary data prevents a full evaluation of the quantitative results. The central claims are plausible and consistent with the experimental literature cited, but several methodological details and interpretive steps require clarification or additional evidence to be fully convincing.
- **Who would be interested in the results, and why** Researchers in the fields of transcription factor biology, structural biology of protein-nucleic acid interactions, and computational biophysics would find these results of interest. The proposed dual recognition mechanism, if substantiated, could have implications for understanding how transcription factors achieve specificity for RNA targets and for the design of experiments probing such interactions. The work may also be relevant to those studying glucocorticoid receptor function and its regulation by non-coding RNAs.
- **Major strengths** The study addresses a significant gap in understanding transcription factor-RNA recognition. The use of multiple RNA systems (hairpin, bulge-containing hairpin, dsRNA) and comparison with the cognate DNA complex is a sensible approach. The analysis framework, distinguishing specific versus nonspecific contacts and examining groove geometry, is appropriate for the question. The authors are careful to note limitations, such as sampling timescales and the use of modelled RNA structures.
- **Major Concerns** The major concerns are detailed below. The most significant issues relate to the lack of provided figures, the reliance on modelled RNA structures without experimental validation, the limited sampling time, and the interpretation of interaction energies in the context of binding affinity.
- **Minor Comments** Several minor points regarding clarity, terminology, and presentation are listed below.
- **Technical failings that need to be addressed before the case is established** The primary technical failing is the inability to assess the data due to missing figures. Beyond that, the use of a single force field combination and the lack of convergence analysis for the simulations are notable gaps. The interpretation of configurational entropy changes as directly reflecting binding thermodynamics is an oversimplification that needs to be addressed.
- **Assessment against Nature-style criteria** The manuscript addresses a problem of potential originality and scientific importance, but the current evidence base is insufficient to fully establish the claims. The interdisciplinary readership is plausible, but the technical soundness cannot be fully verified from the provided material. The readability for nonspecialists is adequate, though some sections are dense.
- **Recommendation posture** Supportive if technical concerns are resolved and the full data is made available for review.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript makes quantitative claims regarding RMSD values, contact networks, interaction energies, and groove widths, all of which are presented in figures and supplementary materials.
- **Evidence pointer** Figures 1-7, Figures S1-S23, Tables S1, Movies S1-S60
- **Concern** The manuscript text refers extensively to figures, supplementary figures, tables, and movies, but none of these are provided in the submitted material. Without these data, it is impossible to verify the quantitative results, the structural interpretations, or the statistical significance of the reported differences between systems. For example, the claim that "Gas5_RNA shows greater conformational changes upon the binding of GR with the RMSD values of ∼3 Å" cannot be assessed. Similarly, the contact maps, energy values, and PCA results are all unverifiable.
- **Why it matters** The core conclusions of the paper rest entirely on the analysis of simulation trajectories. If the data presentation is incomplete, the scientific case is not established. Reviewers and readers must be able to inspect the evidence to judge the validity of the claims.
- **Resolution test** Provide all figures, supplementary figures, tables, and movies. Ensure that all quantitative claims in the text are directly supported by the displayed data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model construction and validation
- **Claim pointer** The authors state that RNA structures were derived using RNAFold and 3dRNA webservers, and complexes were generated via docking with HDOCK. They also state that the docking generated complexes matching experimental criteria among the top-ten scored decoys.
- **Evidence pointer** Methods: Systems Preparation; Figure S1, Figure S2
- **Concern** The RNA structures are computational models, not experimentally determined. The accuracy of these models is critical, as the conclusions about groove geometry and accessibility depend on the starting structures. The authors do not provide any validation of the modelled RNA structures (e.g., comparison to known structures, assessment of model quality). Furthermore, the docking protocol is described briefly, and the criteria for selecting the "correct" docked pose are not fully detailed. The statement that the top-ten scored decoys matched the criteria is not sufficient; the actual scores and the structural rationale for selection should be provided.
- **Why it matters** If the starting RNA structures are inaccurate or the docked poses are not representative, all subsequent analyses and conclusions about recognition mechanisms could be flawed. The study's foundation depends on the quality of these models.
- **Resolution test** Provide a detailed validation of the modelled RNA structures, including comparison with any available experimental data or high-quality predictions. Justify the docking pose selection with scores and structural analysis. If possible, include control simulations starting from alternative conformations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Sampling and convergence
- **Claim pointer** The authors performed 600 ns MD simulations for each system, discarding the first 100 ns as equilibration.
- **Evidence pointer** Methods: Molecular Dynamics Simulation; Trajectory Analysis
- **Concern** A 500 ns production run may be insufficient to sample the conformational space of protein-nucleic acid complexes, particularly for RNA which can be highly dynamic. The authors do not provide any convergence analysis (e.g., block averaging, RMSD convergence plots, or checks on the stability of key observables over time). The claim that the GR-dsRNA complex shows "the beginning of the protein dissociation" suggests that the system may not have reached a stable state within the simulation time. This raises concerns about whether the observed differences between systems are due to genuine mechanistic differences or simply insufficient sampling.
- **Why it matters** Molecular dynamics conclusions are only valid if the simulations are converged. Without evidence of convergence, the quantitative comparisons and mechanistic interpretations are not reliable.
- **Resolution test** Provide convergence analysis for all simulations, such as time evolution of RMSD, contact numbers, and key geometric parameters. Consider extending simulations or performing replicate runs to ensure reproducibility of the observed trends.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of interaction energies
- **Claim pointer** The authors calculate interaction energies and state that the trend "GR-Gas5_RNA_model2 >> GR(mon1)-DNA > GR(mon1)-DNA > GR-Gas5_RNA_model1 ≈ GR-GRE_RNA >> GR-dsRNA" is consistent with experimental binding affinities.
- **Evidence pointer** Results: Protein–Nucleic Acids Interaction Energies and Configurational Entropies; Figure 5
- **Concern** The interaction energies are computed from a single trajectory for each system. These energies are highly dependent on the specific conformation sampled and do not include entropic or solvation contributions. The authors acknowledge the challenge of calculating accurate energies but then use these values to draw conclusions about binding preferences. The comparison between a monomeric RNA complex and a dimeric DNA complex is particularly problematic, as the energy values are not directly comparable. The statement that a monomer can bind RNA "even stronger than DNA" is based on this potentially flawed comparison.
- **Why it matters** The conclusion that the simulation trend matches experimental binding preferences is a key part of the paper's argument. If the energy calculations are not robust, this conclusion is weakened.
- **Resolution test** Use more rigorous free energy calculation methods (e.g., MM-PBSA, thermodynamic integration) or at least provide error estimates and a clear discussion of the limitations of the energy comparison. Re-frame the comparison between monomeric and dimeric complexes.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Specificity of the proposed mechanism
- **Claim pointer** The authors conclude that "the combination of structural motifs defines the GR-RNA selective binding: a recognition mechanism, which may be shared by other zinc finger TFs."
- **Evidence pointer** Conclusions
- **Concern** The study only examines one protein (GR) and a limited set of RNA structures. The claim that this mechanism may be shared by other zinc finger transcription factors is highly speculative and not supported by any comparative data. The authors do not discuss what features of GR are unique or generalizable. The role of the specific amino acid sequence in the recognition helix and helix 4 in enabling this dual mechanism is not explored in a comparative context.
- **Why it matters** The broader significance of the work depends on the generality of the proposed mechanism. Without evidence for generality, the claim remains a hypothesis, not a conclusion.
- **Resolution test** Either temper the claim to be specific to GR, or provide a comparative analysis with other zinc finger proteins, even if only through sequence or structural analysis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "the protein effectively moulds its binding site within DNA major groove" and "the protein to anchor itself through nonspecific electrostatic contacts". The term "moulds" is somewhat vague. It would be clearer to specify the structural changes observed (e.g., widening, deepening).
- **Required correction** Rephrase to be more specific about the structural changes in the DNA major groove.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology detail
- **Affected element** Methods: Systems Preparation
- **Evidence pointer** Methods: Systems Preparation
- **Issue** The authors state that helix 4 was excluded during docking to avoid steric hindrance. The rationale is given, but the potential impact of this exclusion on the final docked poses is not discussed. Helix 4 is later shown to be important for RNA interactions.
- **Required correction** Add a sentence discussing the potential limitations of this approach and whether the final simulations included helix 4 in a way that could compensate for its absence during docking.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results: Protein–Nucleic Acids Contacts
- **Evidence pointer** Results: Protein–Nucleic Acids Contacts
- **Issue** The authors use the term "specific contacts" to mean contacts between protein side chains and nucleic acid bases. This is a reasonable definition, but it should be explicitly stated in the methods or at first use to avoid confusion with the more general biochemical meaning of "specific".
- **Required correction** Define "specific" and "nonspecific" contacts clearly in the Methods section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results: Protein–Nucleic Acids Interaction Energies and Configurational Entropies
- **Evidence pointer** Table 1
- **Issue** The configurational entropy values are presented in Table 1, but the units are not stated in the text. The magnitude of the changes (e.g., 15 kcal/mol) is discussed, but the reader cannot assess the significance without units.
- **Required correction** State the units of the configurational entropy in the text and table caption.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results: Nucleic Acids Helical and Groove Parameters
- **Evidence pointer** Results: Nucleic Acids Helical and Groove Parameters
- **Issue** The authors state that "the major groove width distributions for dsRNA are broader, which indicates larger structural fluctuations, which contribute to the instability of the GR-dsRNA contacts network". This is a plausible interpretation, but it is presented as a fact. The link between broader distributions and instability is not directly demonstrated.
- **Required correction** Soften the language to indicate this is an interpretation, e.g., "suggests" or "may contribute".

## Risk / unsupported claims
- The claim that the proposed dual recognition mechanism "may be shared by other zinc finger transcription factors" is unsupported by any comparative data presented in the manuscript.
- The quantitative comparison of interaction energies between monomeric RNA complexes and a dimeric DNA complex is not robust and may be misleading.
- The conclusion that the GR-dsRNA complex is unstable and shows "the beginning of the protein dissociation" is based on a single 500 ns trajectory and may not be a converged observation.
- The statement that the unfolding of helix 4 in the GR-DNA trajectory is due to "GRE-flanking regions being too short" is presented as a likely explanation but is not tested or supported by additional simulations.
- The overall claim of a "dual recognition mechanism" is well-supported by the qualitative description of the simulations, but the quantitative evidence (energies, entropies) is not sufficiently robust to fully establish the thermodynamic basis of this mechanism.