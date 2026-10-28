## Review setup
- **Input scope** Full manuscript text including abstract, introduction, experimental section, results and discussion, conclusions, and supplementary material references.
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and claims as presented in the provided manuscript. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The authors report that the B-box domain of HMGB1 forms self-associates approximately 30 nm in size, that these associates bind heparin with higher apparent affinity than the monomeric form, that the secondary and tertiary structure of the protein is preserved upon association, and that AlphaFold modeling suggests charge redistribution in oligomers enhances electrostatic attraction to polyanions.
- **Visible evidence base** DLS data, CD spectra, fluorescence spectra, cw-EPR spectra, native gel electrophoresis, TIM-MS data, and AlphaFold modeling results, all as described in the text and referenced figures.
- **Missing materials affecting confidence** Actual figure images, supplementary figures (S1–S10), raw data files, experimental replicates, statistical analyses, and detailed AlphaFold model validation metrics were not provided. The manuscript text alone limits quantitative verification.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question regarding the role of B-box self-association in modulating polyelectrolyte binding, with potential implications for HMGB1 function in inflammation and phase separation. The experimental design is logical, and the combination of biophysical techniques is appropriate. However, several claims are not fully supported by the evidence as presented, particularly regarding the size and stoichiometry of the associates, the quantitative comparison of binding affinities, and the mechanistic interpretation of the EPR data. The AlphaFold-based explanation, while plausible, lacks experimental validation. The work is of interest to the biophysics and protein-polyelectrolyte communities but requires substantial revisions to establish the core conclusions.
- **Who would be interested in the results, and why** Researchers studying HMGB1 biology, protein-polyelectrolyte interactions, liquid-liquid phase separation, and the biophysical basis of alarmin function. The findings may also interest those working on heparin-based therapeutics and the design of protein-polyelectrolyte complexes.
- **Major strengths** The study combines multiple orthogonal biophysical techniques to characterize both structure and interaction. The observation that self-association enhances polyelectrolyte binding without structural perturbation is novel and potentially significant. The use of EPR to probe local dynamics around a specific residue provides site-specific insight. The work addresses a gap in the literature regarding the B-box domain's role in polyanion binding.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality: The finding that B-box self-association enhances heparin binding is novel, though the broader concept of multivalency in protein-polyelectrolyte interactions is established. Scientific importance: Moderate to high for the HMGB1 field, but the broader impact on immunology or phase separation biology is not fully demonstrated. Interdisciplinary readership: The work will appeal to biophysicists, biochemists, and structural biologists, but the presentation may be too specialized for a general audience. Technical soundness: The methods are appropriate, but several quantitative claims lack sufficient support. Readability for nonspecialists: The manuscript is clearly written but assumes familiarity with EPR and polyelectrolyte concepts; a brief primer on key techniques would improve accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding quantitative characterization of associates, binding affinity comparisons, and validation of the AlphaFold model.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the B-box forms "30 nm large self-associates" and that these associates are present in solution prior to filtration.
- **Evidence pointer** Results section, "Formation of B-Box Associates during the Expression Procedure"; Figure 1 (DLS data)
- **Concern** The DLS data show a peak at approximately 32 nm, but the manuscript does not provide information on the polydispersity index, the intensity-weighted versus number-weighted size distribution, or the reproducibility across multiple preparations. The assignment of this peak to a specific oligomeric state is not quantitatively justified. The estimate of "approximately eight monomers" per associate is based on a simplistic volume argument (2.3 nm to 32 nm) that assumes spherical packing and uniform density, which is not validated. Furthermore, the manuscript does not address whether the associates are equilibrium species or kinetically trapped aggregates formed during expression.
- **Why it matters** The central claim of the paper is that self-association modulates heparin binding. Without a robust characterization of the associates (size, stoichiometry, stability, and homogeneity), the interpretation of all subsequent functional experiments is compromised.
- **Resolution test** Provide DLS data with polydispersity indices, size distributions from multiple independent preparations, and a more rigorous determination of oligomer stoichiometry (e.g., analytical ultracentrifugation, size-exclusion chromatography with multi-angle light scattering, or native mass spectrometry). Address whether the associates are reversible and whether their size distribution changes with concentration or time.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support
- **Claim pointer** The authors claim that the associated form of the B-box exhibits "significantly enhanced" binding to heparin compared to the monomeric form, based on EPR-detected changes in 2Azz values.
- **Evidence pointer** Results section, "B-Box Binding Patterns to Heparin in Single and Self-Associated States"; Figure 3
- **Concern** The manuscript reports changes in 2Azz values as a function of heparin concentration, but no quantitative binding parameters (e.g., dissociation constants, binding stoichiometry) are provided. The claim of "significantly enhanced" binding is based on a qualitative comparison of the onset of spectral changes. The EPR data are not analyzed to extract binding affinities or to distinguish between specific binding and nonspecific electrostatic association. Additionally, the manuscript does not report error bars or replicate measurements for the 2Azz values, making it impossible to assess the statistical significance of the observed differences.
- **Why it matters** The central functional claim of the paper is that self-association enhances polyelectrolyte binding. Without quantitative binding data, the magnitude and significance of this enhancement cannot be evaluated, and the mechanistic interpretation remains speculative.
- **Resolution test** Perform quantitative binding assays (e.g., isothermal titration calorimetry, surface plasmon resonance, or fluorescence anisotropy) to determine binding affinities for both monomeric and associated forms. Provide replicate EPR measurements with error analysis and, if possible, fit the 2Azz changes to a binding model to extract apparent affinities.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of EPR data
- **Claim pointer** The authors claim that the EPR spectral changes upon heparin binding indicate that the interaction site is "close to the Cys19 residue" and that the observed line broadening reflects "reduced amplitude of motion" consistent with a "bidentate label."
- **Evidence pointer** Results section, "B-Box Binding Patterns to Heparin in Single and Self-Associated States"; Figure 3
- **Concern** The interpretation of the EPR line shapes is not sufficiently supported. The manuscript states that the broadening of the high-field minimum is "consistent with" reduced averaging of the g-tensor z-component, but no spectral simulation or quantitative analysis of the EPR spectra is provided. The claim that the interaction site is near Cys19 is inferred from changes in the local motion of the spin label, but alternative explanations (e.g., global tumbling changes, aggregation, or conformational changes elsewhere in the protein) are not excluded. The reference to a "bidentate label" is not explained or justified.
- **Why it matters** The EPR data are the primary evidence for the interaction site and for the similarity of binding modes between monomeric and associated forms. Without rigorous spectral analysis, these conclusions are not established.
- **Resolution test** Perform spectral simulations of the EPR data to extract rotational correlation times and order parameters. Provide control experiments with spin labels at other positions or with a non-binding mutant to confirm the specificity of the observed changes. Justify the "bidentate label" interpretation with appropriate references or data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The authors claim that AlphaFold modeling reveals "charge redistribution" in oligomers, resulting in "an extended positively charged region that enhances electrostatic attraction" to heparin.
- **Evidence pointer** Results section, "B-Box Binding Patterns to Heparin in Single and Self-Associated States"; Figure 4
- **Concern** The AlphaFold predictions are presented as a mechanistic explanation for the experimental observations, but no validation of the predicted oligomer structures is provided. The manuscript does not report confidence scores (e.g., pLDDT, PAE), nor does it compare the predicted structures with any experimental data (e.g., cross-linking, small-angle X-ray scattering, or mutagenesis). The claim that charge redistribution is the cause of enhanced binding is purely correlative and not tested experimentally.
- **Why it matters** The proposed mechanism is a key conclusion of the paper. Without experimental validation, the AlphaFold-based explanation remains speculative and does not constitute evidence.
- **Resolution test** Provide AlphaFold confidence metrics and validate the predicted oligomer interfaces with experimental approaches (e.g., site-directed mutagenesis of predicted interface residues, cross-linking mass spectrometry, or SAXS). Test the charge redistribution hypothesis by engineering charge-altered mutants and measuring binding affinity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Control experiments
- **Claim pointer** The authors claim that the B-box binds heparin in solution, as demonstrated by native gel electrophoresis.
- **Evidence pointer** Results section, "Heparin Binds B-Box in Solution"; Figure 2
- **Concern** The native gel electrophoresis experiment lacks essential controls. The manuscript does not show a control with a non-heparin polyanion (e.g., chondroitin sulfate or DNA) to demonstrate specificity, nor does it show a control with a mutant B-box lacking basic residues. The stoichiometry of the complex is not addressed, and the possibility of nonspecific aggregation during electrophoresis is not excluded.
- **Why it matters** The gel shift assay is used to support the claim of solution binding. Without appropriate controls, the observed band shift could be due to nonspecific interactions or artifacts of the gel system.
- **Resolution test** Include controls with a non-heparin polyanion and a charge-neutralized B-box mutant. Perform the gel shift at multiple protein-to-heparin ratios to assess stoichiometry. Consider an orthogonal solution-based binding assay (e.g., fluorescence polarization or pull-down) to confirm the interaction.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the B-box "forms 30 nm large self-associates" but does not specify the method used or the conditions under which this was observed. This may mislead readers unfamiliar with DLS.
- **Required correction** Briefly mention the technique (DLS) and the buffer conditions in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Experimental section, "Protein Filtration"
- **Evidence pointer** Experimental section, "Protein Filtration"
- **Issue** The filtration step uses a 30 kDa cutoff membrane, but the manuscript does not report the recovery yield or the concentration of the monomeric fraction after filtration. This information is important for assessing the reliability of subsequent experiments.
- **Required correction** Report the protein concentration and recovery after filtration, and confirm that the monomeric fraction remains monomeric over the time course of the experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section, "Formation of B-Box Associates during the Expression Procedure"
- **Evidence pointer** Figure 1
- **Issue** The DLS data are presented as a single representative trace. No information is given on the number of replicates or the variability between measurements.
- **Required correction** Provide averaged size distributions with standard deviations from at least three independent measurements.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section, "Impact of Association on the Structure of the B-Box"
- **Evidence pointer** Figure 2 (CD and fluorescence)
- **Issue** The fluorescence intensity difference between monomeric and associated forms is attributed to "quenching" or "charge redistribution," but no quantitative analysis (e.g., quantum yield measurements or lifetime measurements) is provided to support this interpretation.
- **Required correction** Either provide additional data to support the quenching interpretation or soften the claim to note that the intensity difference is not fully explained.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Conclusions
- **Evidence pointer** Conclusions
- **Issue** The conclusions state that "the interaction with heparin leads to changes in the association of the B-box," but this is not directly measured. The EPR data suggest changes in complex size, but no direct evidence for altered association state is provided.
- **Required correction** Revise the statement to reflect that the data are consistent with, but do not directly demonstrate, changes in association.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction assumes familiarity with the HMGB1 domain structure and the concept of polyelectrolyte interactions. A brief schematic or a more explicit description of the domain architecture would help nonspecialist readers.
- **Required correction** Add a brief description of the A-box, B-box, and C-terminal tail, and their known functions, in the introduction.

## Risk / unsupported claims
- The claim that associates consist of "approximately eight monomers" is based on an unvalidated volume estimate and is not supported by direct measurement.
- The claim that "charge redistribution" in oligomers enhances electrostatic attraction is based solely on AlphaFold predictions without experimental validation.
- The claim that the interaction site is "close to Cys19" is inferred from EPR line-shape changes but is not confirmed by site-directed mutagenesis or other approaches.
- The claim that the associated form has "significantly enhanced" binding affinity is not supported by quantitative binding data.
- The claim that the B-box associates are "dynamic" is not directly tested; the manuscript only shows that the monomeric fraction is stable over 6 hours, not that the associates are in equilibrium with monomers.