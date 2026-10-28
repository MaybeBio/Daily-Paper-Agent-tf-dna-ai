## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary data references.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No external validation of data or methods was performed.
- **Shared manuscript claim summary** The authors propose that the KEAP1 C151 active site catalyzes the reaction of electrophilic NRF2 activators with C151, explaining the selective targeting of this cysteine over other cellular thiols. They report a pKa of 6.9 for C151, rapid reaction with monobromobimane, competition results with clinical NRF2 activators, a crystal structure of the BTB-bimane conjugate, and docking models suggesting a catalytic proximity effect and hydrogen bonding to the electrophilic carbonyl.
- **Visible evidence base** Abstract, Introduction, Results (four subsections), Discussion, Methods, figure legends (Figs. 1–7), supplementary figure/table references, and author contributions.
- **Missing materials affecting confidence** Raw kinetic data, full crystallographic statistics table (only referenced as SI Table S1), complete docking scores for all poses (only partially provided in SI Tables S2–S7), and details of the 4D model construction. The manuscript states data will be made available on request, which limits independent verification.

## Reviewer
- **Overall assessment** This manuscript addresses a significant and long-standing question in the NRF2 field: why do diverse electrophilic activators preferentially target KEAP1 C151? The authors provide a compelling combination of biochemical, structural, and computational evidence supporting an active-site catalysis model. The pKa determination, competition assays, and docking analyses are logically connected and generally well-executed. However, several technical concerns, particularly regarding the interpretation of the pKa measurement, the quantitative basis for the "catalysis" claim, and the validation of the 4D docking model, need to be addressed before the central conclusions are fully established. The work is of interest to the redox biology and drug discovery communities, and the findings have potential translational implications.
- **Who would be interested in the results, and why** Researchers studying NRF2/KEAP1 signaling, redox biology, and electrophile sensing. Drug discovery scientists developing NRF2 activators for chronic diseases (e.g., neurodegenerative, inflammatory, metabolic) would find the mechanistic insights valuable for rational design of selective compounds. Structural biologists interested in protein–ligand interactions and cysteine modification would also be engaged.
- **Major strengths** 1. The study tackles a fundamental mechanistic question with broad implications. 2. The combination of experimental (pKa, kinetics, crystallography) and computational (4D docking) approaches is powerful. 3. The competition assay design directly tests the hypothesis of active-site catalysis. 4. The correlation between biochemical blocking and cellular potency strengthens the translational relevance. 5. The crystal structure, despite ligand flexibility, provides a valuable experimental anchor.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (pKa interpretation), R1-M2 (quantitative basis for catalysis), R1-M3 (4D model validation), R1-M4 (crystal structure ambiguity).
- **Assessment against Nature-style criteria** **Originality:** High. The concept of an active site catalyzing electrophile addition to a sensor cysteine is novel and challenges the prevailing pKa-centric view. **Scientific importance:** High. Provides a mechanistic framework for understanding selectivity of clinically used drugs and could guide future drug design. **Interdisciplinary readership:** Moderate to high. Relevant to redox biology, pharmacology, structural biology, and computational chemistry. **Technical soundness:** Moderate. The experimental design is generally sound, but several technical concerns (detailed below) need resolution. **Readability for nonspecialists:** Good. The manuscript is clearly written, with helpful figures and a logical flow from question to hypothesis to evidence.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the data are suggestive, but the current evidence does not fully exclude alternative explanations (e.g., non-catalytic factors) and some quantitative claims require stronger support.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** The authors claim that the pKa of C151 is 6.9, providing optimal reactivity at physiological pH.
- **Evidence pointer** Results section "The pKa of KEAP1 C151 is optimized for reactivity...", Fig. 3B, Methods "pKa determination"
- **Concern** The pKa was determined by measuring initial fluorescence after reaction with mBBr at various pH values. However, the authors also report that the reaction of mBBr with C151 is remarkably fast and that the environment suppresses the fluorescence quantum yield of the conjugate. These two observations could confound the pKa measurement. If the reaction is very fast, the "initial" timepoint may not capture the true initial rate, especially at higher pH where the thiolate fraction is larger. Additionally, if the fluorescence quantum yield is pH-dependent or environment-dependent, the fluorescence signal may not be directly proportional to the amount of conjugate formed. The authors should validate the pKa measurement using an independent method (e.g., direct thiolate absorbance, NMR, or a different probe) or provide control experiments showing that the fluorescence signal is linearly proportional to conjugate concentration across the pH range used.
- **Why it matters** The pKa value of 6.9 is a central pillar of the paper's argument. If this value is inaccurate, the conclusion that the pKa is "optimized" for physiological pH is weakened, and the relative contribution of pKa versus other catalytic factors becomes uncertain.
- **Resolution test** Provide independent validation of the pKa (e.g., using a non-fluorescent thiol-reactive probe with UV detection, or by monitoring the reaction at multiple timepoints to ensure initial-rate conditions). Show that the fluorescence quantum yield of the mBBr-thiol conjugate is constant across the pH range 4–9, or correct for any pH-dependent changes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for claims
- **Claim pointer** The authors state that mBBr reacts with C151 "much faster" than with a small-molecule thiolate (NAC), and that the active site "catalyzes" the reaction.
- **Evidence pointer** Results section "The pKa of KEAP1 C151 is optimized for reactivity...", Fig. 2C–D, Discussion
- **Concern** The comparison between mBBr reaction with C151 in the BTB domain and with NAC is not a controlled comparison. NAC is a small molecule in solution, while C151 is in a protein environment. The observed rate difference could be due to factors other than active-site catalysis, such as: (a) the effective concentration of the thiol in the protein, (b) the local dielectric environment, (c) the presence of the protein affecting the fluorescence quantum yield (as the authors themselves note), or (d) the pKa difference (6.9 vs 9.43 for NAC). To claim catalysis, the authors should compare the rate of mBBR reaction with C151 in the BTB domain to a matched control, such as a peptide or a denatured protein, or to a C151-containing peptide with a similar pKa. Additionally, the authors should provide quantitative rate constants (k2) for both reactions, not just qualitative fluorescence traces.
- **Why it matters** The central claim of the paper is that the active site catalyzes the reaction, not just that C151 has a lower pKa. Without a proper control and quantitative rate comparison, the "catalysis" claim is not established.
- **Resolution test** Provide second-order rate constants for mBBr reaction with BTB C151 and with a suitable control (e.g., a C151-containing peptide, or NAC at a pH where its thiolate fraction matches that of C151 at pH 7.4). If the protein environment accelerates the reaction beyond what is expected from the pKa alone, the catalysis claim is supported.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational model validation
- **Claim pointer** The 4D flexible docking model is used to propose specific interactions (e.g., hydrogen bonding to G148) that orient electrophiles for reaction with C151.
- **Evidence pointer** Results sections "The use of x-ray crystallography and 4D molecular modeling..." and "KEAP1-C151 active site interactions with class 1 electrophiles", Figs. 4, 6, SI Tables S2–S7
- **Concern** The 4D docking model is a central tool for generating mechanistic hypotheses, but its validation is not described in sufficient detail. The authors state that seven crystal structures were used to create the flexible model, but do not provide details on how the model was constructed, how the flexibility was parameterized, or how the docking accuracy was assessed. The claim that the model can accurately reproduce the binding mode of CDMe (Fig. 4B–C) is based on a single comparison. The authors should provide a more thorough validation, such as cross-validation with multiple known ligands, or comparison with the experimentally determined structure of the BTB-bimane conjugate. Additionally, the docking scores for the top poses of each ligand should be reported with estimates of uncertainty.
- **Why it matters** The docking model is used to make specific predictions about the mechanism (e.g., the role of G148, the distance of the electrophilic carbon to C151). If the model is not well-validated, these predictions are speculative and the mechanistic conclusions are weakened.
- **Resolution test** Provide a detailed description of the 4D model construction and validation. Show that the model can correctly predict the binding poses of multiple known KEAP1 ligands (e.g., from the crystal structures used to build the model, using leave-one-out cross-validation). Report docking scores with error estimates.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural evidence
- **Claim pointer** The crystal structure of the BTB-bimane conjugate shows "no specific orientation in the active site after covalent addition," and this is used to support the idea that the pre-covalent complex is the key determinant of selectivity.
- **Evidence pointer** Results section "The use of x-ray crystallography and 4D molecular modeling...", Fig. 4A, SI Table S1
- **Concern** The crystal structure is a key experimental anchor, but the interpretation is limited by the ambiguous and discontinuous electron density. The authors modeled two conformations with refined occupancies of 0.52 and 0.48, which suggests that the density is not clearly interpretable. The authors should provide a more detailed analysis of the electron density, including maps at different contour levels, and discuss the possibility that the ligand may be present in more than two conformations or that the density may represent a mixture of states. Additionally, the resolution of the structure (1.80 Å) is good, but the authors should report the B-factors for the ligand atoms and the real-space correlation coefficients to support the modeling.
- **Why it matters** The crystal structure is used to support the claim that the post-covalent state is not specifically oriented, which is part of the argument that the pre-covalent state is the key determinant. If the structure is not well-determined, this conclusion is not robust.
- **Resolution test** Provide a more detailed crystallographic analysis, including electron density maps at multiple contour levels, B-factors for ligand atoms, and real-space correlation coefficients. Discuss alternative interpretations of the density and how the two-conformation model was chosen.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 2C–D
- **Evidence pointer** Fig. 2C–D
- **Issue** The fluorescence traces for the reaction of mBBr with BTB C151 and NAC are shown on different scales (Fig. 2C vs. 2D), which makes direct visual comparison difficult. The authors state that the BTB reaction is "remarkably fast," but the figure does not clearly convey the magnitude of the rate difference.
- **Required correction** Plot both reactions on the same time axis and, if necessary, use a log scale for the y-axis to show the full time course. Alternatively, provide a table of initial rates or k2 values.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Competition assay
- **Evidence pointer** Fig. 5B–D, Methods "Direct competition assay"
- **Issue** The competition assay uses a 10-fold excess of mBBr over the BTB protein, and equimolar amounts of the competing electrophile and mBBr. The authors should clarify whether the concentrations of the competing electrophiles were chosen based on their known potencies or cellular concentrations, and whether the results are sensitive to the concentration ratio.
- **Required correction** Provide a brief justification for the concentrations used and discuss the sensitivity of the assay to the mBBr:electrophile ratio.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Fig. 7B
- **Evidence pointer** Fig. 7B
- **Issue** The authors show that Cd2+ partially blocks mBBr binding to C151, but they do not discuss the potential mechanism (e.g., direct coordination to the thiolate vs. binding elsewhere). This is relevant to the claim that the active site is specific for Class 1 electrophiles.
- **Required correction** Add a brief discussion of how Cd2+ might interact with C151 and whether this is consistent with the proposed active-site model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph on screening implications
- **Issue** The statement that "affinity for the C151 pocket alone will likely not correlate with the rate of reaction" is an important implication, but it is not fully developed. The authors could provide more specific guidance on what screening metrics would be most predictive.
- **Required correction** Expand this section to suggest specific computational or experimental approaches that could capture the catalytic factors (e.g., transition-state modeling, QM/MM methods, or kinetic assays in high-throughput format).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Data availability section
- **Issue** The statement "Data will be made available on request" is vague and does not meet the standards of many journals that require deposition of structural data and computational models.
- **Required correction** Specify that the crystal structure has been deposited in the PDB (as stated in the Methods) and provide the accession code. Consider depositing the 4D model parameters or making them available as supplementary material.

## Risk / unsupported claims
- The claim that the pKa of C151 is 6.9 is based on a single method (mBBr fluorescence) that may be confounded by the very fast reaction and environment-dependent fluorescence quantum yield. This claim is not fully supported without independent validation.
- The claim that the active site "catalyzes" the reaction of C151 with Class 1 electrophiles is not quantitatively supported, as no rate constants are provided and the comparison to NAC is not a controlled experiment.
- The claim that the 4D docking model accurately represents the pre-covalent binding of electrophiles is not fully validated, as the model construction and validation are not described in sufficient detail.
- The prediction that 15d-PGJ2 reacts with C151 via the δ-carbon rather than the β-carbon is presented as a testable hypothesis, but it is not experimentally tested in this work. This should be clearly framed as a prediction, not a finding.
- The statement that "enzymatic catalysis is the primary reason that C151 acts as a sensor cysteine" is a strong conclusion that goes beyond the data presented, which show enhanced reactivity in the isolated BTB domain but do not directly compare to other KEAP1 cysteines in the full-length protein or in cells.