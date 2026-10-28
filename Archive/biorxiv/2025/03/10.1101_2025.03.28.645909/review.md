## Review setup
- **Input scope** Full manuscript text (abstract, introduction, experimental, results, discussion, conclusions) without figures, tables, or supplementary information
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive validity based solely on the provided text; no assessment of data quality beyond what is described
- **Shared manuscript claim summary** The authors report that the HMGB1 B-box domain forms ~30-nm self-associates during recombinant expression, that these associates retain the monomeric secondary/tertiary structure, and that the associated state binds heparin more strongly than the monomeric state. They propose that oligomerization-induced positive charge accumulation enhances electrostatic interactions with polyanions, supported by AlphaFold modeling and EPR spectroscopy.
- **Visible evidence base** Text descriptions of DLS, CD, fluorescence, EPR, native PAGE, heparin-affinity chromatography, ion mobility-mass spectrometry, and AlphaFold modeling; references to Figures 1, 2, 4, 5, 6, 7, and Supplementary Figures S0–S4, S7
- **Missing materials affecting confidence** All figures, tables, and supplementary information; raw spectra, quantitative fitting parameters, statistical analyses, and experimental replicates; AlphaFold confidence metrics and charge calculation methodology

## Reviewer
- **Overall assessment** The manuscript addresses a potentially interesting question regarding how self-association of the HMGB1 B-box domain modulates polyelectrolyte binding. The combination of biophysical techniques is appropriate in principle, and the observation that the associated state enhances heparin binding is potentially novel. However, the evidence as presented in the text is insufficient to firmly establish the central claims. Key quantitative data, control experiments, and methodological details are missing, and the interpretive link between AlphaFold predictions and the experimental observations is not rigorously justified. The manuscript would benefit from substantial additional experimentation and analysis before it could be considered for publication in a high-impact venue.
- **Who would be interested in the results, and why** Researchers studying HMGB1 biology, particularly its extracellular functions as a damage-associated molecular pattern and its interactions with glycosaminoglycans; investigators interested in protein-polyelectrolyte interactions and the functional consequences of protein self-association; and those working on the biophysics of intrinsically disordered or partially disordered proteins and their phase behavior.
- **Major strengths** The study addresses a relevant and under-explored question about the functional role of B-box self-association in polyelectrolyte binding. The use of multiple complementary biophysical techniques (DLS, CD, fluorescence, EPR, native PAGE, IM-MS) is commendable. The observation that the associated state enhances heparin binding, despite structural preservation of the monomeric fold, is an interesting finding that could have implications for understanding HMGB1 function in inflammatory contexts.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that the B-box forms ~30-nm self-associates and that approximately half of the protein is present in complexed form.
  - **Evidence pointer** Results section "Formation of B-box associates during the expression procedure"; Figure 1; Supplementary Figure S4
  - **Concern** The DLS data are described only qualitatively. No size distribution plots, polydispersity indices, or replicate measurements are provided. The assignment of the ~32-nm species to specific oligomeric states is not supported by any independent method (e.g., size-exclusion chromatography with multi-angle light scattering, analytical ultracentrifugation). The claim that "approximately half" of the protein is in complexed form is based on UV-Vis absorbance of filtered fractions, which is an indirect and potentially unreliable measure. No mass balance or recovery data are shown.
  - **Why it matters** The central premise of the study is that the associated state is functionally distinct from the monomeric state. If the size, stoichiometry, and abundance of the associates are not rigorously characterized, all subsequent comparisons between "monomeric" and "associated" samples are on uncertain footing.
  - **Resolution test** Provide quantitative DLS data with size distributions and polydispersity for at least three independent preparations. Confirm the oligomeric state using an orthogonal method such as SEC-MALS or AUC. Report protein concentrations and mass balance for the filtration step.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that the associated state binds heparin with considerably higher affinity than the monomeric state, based on EPR spectral changes.
  - **Evidence pointer** Results section "B-box binding patterns to heparin in single and self-associated states"; Figure 6; Supplementary Figure S7
  - **Concern** The EPR data are described in terms of changes in the outer splitting (2Azz) as a function of heparin concentration, but no quantitative binding analysis is presented. No dissociation constants, binding stoichiometries, or error estimates are given. The claim of "considerably increased" binding affinity is not supported by any fitted parameter. The interpretation that the associated state has higher affinity is inferred from the onset of spectral changes at lower heparin concentrations, but this could also reflect differences in local concentration, aggregation state, or non-specific effects. The text states that the final state at high heparin excess is similar for both samples, which complicates the interpretation of differential affinity.
  - **Why it matters** The central functional claim of the manuscript is that self-association enhances polyelectrolyte binding. Without quantitative binding parameters, this claim is not established. The observation that both samples converge to similar spectra at high heparin excess could indicate that the associated state simply provides a higher local concentration of binding sites rather than a fundamentally different binding mode.
  - **Resolution test** Perform quantitative binding titrations with a suitable method (e.g., ITC, SPR, or fluorescence anisotropy) for both monomeric and associated states. Report binding constants, stoichiometries, and statistical comparisons. Alternatively, provide a rigorous EPR-based binding model with fitted parameters and confidence intervals.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Interpretive validity
  - **Claim pointer** The authors claim that AlphaFold modeling reveals that oligomerization induces charge redistribution, creating an extended positively charged region that enhances electrostatic attraction to heparin.
  - **Evidence pointer** Results section "B-box binding patterns to heparin in single and self-associated states"; Figure 7
  - **Concern** The AlphaFold predictions are presented as providing a mechanistic explanation for the enhanced binding, but no details are given regarding model confidence (pLDDT, PAE), the selection of oligomeric states, or the method used to calculate charge distributions. The text acknowledges that the modeled oligomers (2–8 units) are not representative of the ~30-nm associates observed experimentally, yet the authors extrapolate from these small oligomers to the larger assemblies. This extrapolation is not justified. Furthermore, the claim that "charge redistribution" occurs upon oligomerization is not supported by any quantitative comparison of electrostatic potentials between monomeric and oligomeric states.
  - **Why it matters** The proposed mechanism is a key part of the manuscript's conceptual contribution. If the computational evidence is not rigorous or is not quantitatively linked to the experimental observations, the mechanistic claim is speculative.
  - **Resolution test** Provide AlphaFold confidence metrics, a description of how oligomeric models were generated and selected, and a quantitative analysis of electrostatic surface potentials for monomer versus oligomers. Ideally, validate the predicted charge accumulation experimentally (e.g., via mutagenesis of key basic residues and testing binding).
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological rigor
  - **Claim pointer** The authors claim that the secondary and tertiary structure of the B-box is preserved in the associated state based on CD, fluorescence, and EPR spectroscopy.
  - **Evidence pointer** Results section "Impact of association on the structure of the B-box"; Figure 2
  - **Concern** The CD spectra are described as "very comparable," but no quantitative comparison (e.g., secondary structure deconvolution, normalized root-mean-square deviation) is provided. The fluorescence data show a reduced intensity in the associated state, which is attributed to quenching, but alternative explanations (e.g., partial unfolding, changes in solvent exposure) are not excluded. The EPR spectra are stated to be "virtually the same," but no line-shape analysis or quantitative comparison is shown. The conclusion that the structure is "preserved" is therefore based on qualitative visual inspection rather than rigorous analysis.
  - **Why it matters** The claim that the associated state preserves the monomeric fold is important for interpreting the functional differences as being due to avidity/charge effects rather than structural changes. If the structure is subtly altered, the interpretation changes.
  - **Resolution test** Provide quantitative spectral comparisons (e.g., secondary structure deconvolution for CD, center-of-mass analysis for fluorescence, spectral simulation for EPR). Include appropriate statistical tests.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Experimental section, protein expression
  - **Evidence pointer** "Cloning of the B-box domain into a modified pet22b(+) vector"
  - **Issue** The text states that an Ala-Arg-Ile (ARI) triplet was inserted after the N-terminal methionine "for better expression," but no data or reference supporting this claim is provided. The rationale is unclear.
  - **Required correction** Provide a reference or data supporting the claim, or remove the statement.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Experimental section, spin labeling
  - **Evidence pointer** "Spin labeling and CW EPR spectroscopy"
  - **Issue** The labeling efficiency is stated to be near 100% based on IM-MS, but the text does not specify how this was quantified or whether the labeled protein was tested for functional activity.
  - **Required correction** Provide the quantification method and, if available, a functional assay confirming that labeling does not alter heparin binding.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretive caution
  - **Affected element** Results section, heparin-affinity chromatography
  - **Evidence pointer** "B-box binds to heparin-sepharose"; Figure 4
  - **Issue** The binding of the B-box to a heparin-Sepharose column under low salt conditions is presented as evidence of heparin binding, but this is a qualitative affinity step, not a quantitative binding measurement. The text should acknowledge this limitation.
  - **Required correction** Clarify that this is a qualitative demonstration of binding and refer to the EPR data for quantitative insights.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results section, EPR analysis
  - **Evidence pointer** "B-box binding patterns to heparin in single and self-associated states"; Figure 6
  - **Issue** The text refers to "15 mol%" and "100 mol%" heparin, but the basis for these molar ratios is unclear (i.e., relative to monomer or to the associated species). This ambiguity affects interpretation.
  - **Required correction** Define the molar ratios explicitly and consistently throughout.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results section, AlphaFold modeling
  - **Evidence pointer** "AlphaFold modeling"
  - **Issue** The text mentions that models were optimized using the adaptive Poisson-Boltzmann solver within CHARMM, but no details are given on the charge calculation method or the dielectric constants used.
  - **Required correction** Provide methodological details or a reference for the charge calculation approach.
- **Technical failings that need to be addressed before the case is established** R1-M1 (oligomer characterization), R1-M2 (quantitative binding), R1-M3 (computational mechanism)
- **Assessment against Nature-style criteria**  
  **Originality** The observation that B-box self-association enhances heparin binding is potentially novel, as the literature has traditionally attributed heparin binding to the A-box. However, the conceptual advance is incremental unless the mechanism is rigorously established.  
  **Scientific importance** The findings could have implications for understanding HMGB1's extracellular functions and its interactions with glycosaminoglycans in inflammatory contexts. However, the physiological relevance of the ~30-nm associates is not demonstrated, limiting the immediate significance.  
  **Interdisciplinary readership** The topic bridges protein biophysics, immunology, and glycosaminoglycan biology, which could appeal to a broad audience. However, the manuscript currently lacks the quantitative rigor and clear narrative needed to engage non-specialists.  
  **Technical soundness** The combination of techniques is appropriate, but the lack of quantitative analyses, controls, and methodological details undermines the technical rigor. The AlphaFold-based mechanistic claim is not sufficiently validated.  
  **Readability for nonspecialists** The text is generally clear but contains some jargon and ambiguous terminology (e.g., "mol%" ratios, "self-complexes"). The logical flow from observation to mechanism could be improved.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an interesting question and has potential, but the central claims regarding the size and functional significance of the B-box associates, the quantitative enhancement of heparin binding, and the mechanistic role of charge accumulation are not sufficiently supported. Substantial additional experimentation and analysis are required.

## Risk / unsupported claims
- The claim that ~50% of the protein is in complexed form is based on indirect UV-Vis measurements without mass balance or recovery data.
- The claim that the associated state has "considerably" higher heparin binding affinity is not supported by any quantitative binding parameter.
- The claim that AlphaFold modeling reveals charge redistribution as the mechanistic basis for enhanced binding is speculative, given the acknowledged size mismatch between modeled oligomers and observed associates, and the lack of confidence metrics or quantitative electrostatic analysis.
- The claim that the ARI triplet insertion improves expression is unsupported by data or reference.
- The claim that the structure is "preserved" in the associated state is based on qualitative spectral comparisons without statistical or quantitative analysis.