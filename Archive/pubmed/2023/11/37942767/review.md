## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors combine Gaussian accelerated molecular dynamics (GaMD) simulations with mass spectrometry (MS) to characterize γ-secretase activation for cleavage of the Notch1 substrate. They report that simulations starting from the cryoEM structure (PDB: 6IDF) fail to capture experimentally observed cleavage sites, and that correcting an apparent registry error by building a model from the APP-bound structure (PDB: 6IYC) enables capture of proper cleavage of both wildtype (G34) and L36F mutant (C33) Notch.
- **Visible evidence base** Abstract, full methods, results, discussion, conclusions, figure legends referenced in text (Figures 1–3, S1–S9, Table S1)
- **Missing materials affecting confidence** Actual figures and supplementary figures/tables not provided; raw MS spectra not shown; no coordinates or trajectory data; no convergence metrics for GaMM simulations beyond those described

## Reviewer
- **Overall assessment** This manuscript presents a potentially useful computational protocol for modeling γ-secretase–substrate interactions, with the key finding being an apparent registry error in the cryoEM structure of Notch-bound γ-secretase. The combination of MS experiments and GaMD simulations is appropriate, and the observation that the L36F mutation shifts the cleavage site is consistent with prior work on analogous APP mutants. However, the central claim that the model built from the APP-bound structure "correctly" captures cleavage is based on indirect geometric criteria rather than direct simulation of the catalytic reaction, and the evidence for the registry error relies on a single structural alignment. The manuscript would benefit from clearer presentation of the MS data, quantitative validation of the model, and discussion of alternative interpretations.
- **Who would be interested in the results, and why** Researchers studying intramembrane proteolysis, γ-secretase function and substrate recognition, and those using enhanced sampling MD simulations to study enzyme–substrate complexes. The finding of a potential registry error in a widely used cryoEM structure is of general interest to the structural biology community.
- **Major strengths** 1) The study addresses an under-explored area (Notch cleavage by γ-secretase) with a combined experimental–computational approach. 2) The identification of a potential registry error in the 6IDF structure is a novel and potentially important observation. 3) The use of GaMD for enhanced sampling is appropriate for capturing conformational transitions relevant to enzyme activation. 4) The experimental MS data provide a clear benchmark for the computational predictions.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (model validation), R1-M2 (MS data presentation), R1-M3 (protonation state rationale)
- **Assessment against Nature-style criteria** **Originality:** Moderate. The application of GaMD to Notch cleavage is new, and the registry error finding is original, but the overall approach closely follows prior work from the same group on APP. **Scientific importance:** Moderate. The findings are relevant to understanding γ-secretase substrate recognition, but the impact is limited by the indirect nature of the computational evidence for cleavage. **Interdisciplinary readership:** Limited. The work is primarily of interest to computational biophysicists and biochemists studying γ-secretase; the MS data are straightforward and do not broaden the appeal. **Technical soundness:** The GaMD methodology is well-established and appears correctly applied, but the validation of the model is indirect and the MS data are not fully presented. **Readability for nonspecialists:** The manuscript is generally well-written and accessible, though some sections (e.g., detailed descriptions of conformational states) are dense.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding model validation and MS data presentation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the model built by mutating APP residues to Notch residues in the 6IYC structure "successfully captured" proper cleavage of WT and L36F Notch, based on the presence of "Active" states in 2D PMF free energy profiles.
- **Evidence pointer** Results section "Free Energy Profiles of Cleavage of WT and L36F Notch by γ-Secretase in the Model Systems"; Figure 1E,F
- **Concern** The "Active" states are defined solely by geometric criteria: the D257–D385 distance being ~6–7 Å and the D385–substrate carbonyl distance being ~2.5–3 Å. These criteria are necessary but not sufficient for proteolysis. The simulations do not include the nucleophilic water molecule explicitly in the reaction coordinate, nor do they model the chemical step. The claim that cleavage is "captured" is therefore an inference from geometry, not a demonstration of reactivity. The authors should either (a) perform simulations that explicitly include and track the nucleophilic water, (b) use a more rigorous reaction coordinate (e.g., QM/MM or EVB), or (c) temper the language to state that the simulations capture a "pre-reactive" or "activation-competent" state.
- **Why it matters** The central conclusion of the paper rests on the ability of the simulations to distinguish productive from non-productive enzyme–substrate conformations. If the geometric criteria are not validated, the claim that the model "correctly" captures cleavage is not established.
- **Resolution test** Provide evidence that the "Active" states are competent for catalysis, e.g., by showing that a water molecule is stably positioned between D257 and D385 and the substrate carbonyl in the active states, or by performing QM/MM calculations on representative snapshots to show a viable reaction pathway.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The MS analysis identifies cleavage at G34 for WT Notch and C33 for L36F Notch.
- **Evidence pointer** Results section "Cleavage of WT and L36F Notch-Bound γ-Secretase in Biochemical Experiments"; Figure 1A
- **Concern** The MS data are described only in text; no spectra, peak assignments, or quantitative details (e.g., signal-to-noise, reproducibility across replicates) are shown. The assignment of cleavage sites from MS data is non-trivial and requires careful interpretation. Without the raw or annotated spectra, the experimental benchmark cannot be independently assessed.
- **Why it matters** The experimental cleavage sites are the ground truth against which the simulations are compared. If the MS assignments are incorrect or ambiguous, the entire computational analysis loses its anchor.
- **Resolution test** Provide the annotated MS spectra in the main text or supplementary material, including the assignment of fragment ions that define the cleavage sites. Include information on replicate experiments and the criteria used to assign the cleavage sites.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that D385 was protonated based on previous pKa calculations, and that this protonation state is required for the observed hydrogen bonding with the substrate carbonyl.
- **Evidence pointer** Methods section "Simulation System Setup"; Results section "Free Energy Profiles of Cleavage of WT and L36F Notch by γ-Secretase in the CryoEM Systems"
- **Concern** The choice of protonating D385 (rather than D257) is stated to be based on prior work, but the sensitivity of the results to this choice is not explored. If D257 were protonated instead, would the "Active" states still be observed? The authors note that they observed activation with either protonation in prior APP studies, but this is not tested here for Notch.
- **Why it matters** The protonation state of the catalytic aspartates is a critical determinant of the simulation outcome. If the results are highly sensitive to this choice, the conclusions are less robust.
- **Resolution test** Perform control simulations with D257 protonated (and D385 unprotonated) for at least one of the model systems, and show that the "Active" state is either preserved or explain why the alternative protonation state is not relevant.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1C–F
- **Issue** The 2D PMF free energy profiles are described in the text, but the figure itself is not provided in the manuscript text. The labels "Active-35," "Active-34," "Active-33," "E1," "E2," "E3," "M1," "M2," and "M3" are used extensively, but it is difficult to follow the discussion without seeing the figure.
- **Required correction** Ensure that Figure 1 is clearly labeled and that the states mentioned in the text are easily identifiable in the figure. Consider adding a schematic or table summarizing the key geometric features of each state.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Simulation System Setup"
- **Evidence pointer** Methods section "Simulation System Setup"
- **Issue** The description of the model building states that "every residue of the APP substrate was systematically mutated to the corresponding Notch residue," but the correspondence is not defined. How were the APP and Notch sequences aligned? What is the numbering scheme for Notch residues (e.g., relative to the full-length protein or the transmembrane domain)?
- **Required correction** Provide the sequence alignment used for the mutation, and clearly define the Notch residue numbering used throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Conclusions section
- **Evidence pointer** Conclusions section
- **Issue** The authors suggest that the cryoEM structure (6IDF) "deviates from activation-compatible conformation" based on the simulations. This is a strong statement given that the simulations are classical MD with a fixed protonation state and no chemical reactivity. The cryoEM structure may represent a different functional state (e.g., substrate recognition vs. catalysis) rather than an "incorrect" registry.
- **Required correction** Soften the language to acknowledge that the 6IDF structure may represent a pre-activation state, and that the model built from 6IYC may represent a later state along the activation pathway.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Simulation Protocol"
- **Evidence pointer** Methods section "Simulation Protocol"
- **Issue** The number of replicate simulations (three) is stated, but the total simulation time per replicate and the criteria for considering the simulations converged are not explicitly stated beyond the description of GaMD parameters.
- **Required correction** Provide the total simulation time for each replicate and a brief statement on convergence assessment (e.g., block averaging of PMF profiles, stability of key distances).

## Risk / unsupported claims
- The claim that the model built from 6IYC "successfully captured" cleavage of Notch is not fully supported, as the simulations do not model the chemical step and the "Active" state is defined by geometric criteria alone.
- The claim that the 6IDF structure has an "incorrect registry" is an interpretation based on a single structural alignment and simulation outcomes; alternative explanations (e.g., different functional states) are not ruled out.
- The statement that "the β3 β-sheet might not be the critical factor for γ-secretase to determine the cleavage site" is based on correlative observations and is not directly tested.
- The proposal that "proton exchange very likely takes place between the two catalytic aspartates" is speculative and not directly demonstrated by the simulations.
- The MS data, which form the experimental foundation of the study, are not presented in sufficient detail to be independently evaluated.