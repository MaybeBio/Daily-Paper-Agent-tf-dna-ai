## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the supplied text
- **Shared manuscript claim summary** The authors propose that Cre recombinase achieves DNA binding specificity through two mechanisms: (1) autoinhibition by the C-terminal helix, which reduces affinity to both cognate and non-cognate DNA, and (2) indirect readout via binding-coupled conformational changes in both protein and DNA, with a large positive binding enthalpy serving as a thermodynamic signature of cognate complex formation.
- **Visible evidence base** ITC binding data for WT Cre and CreΔ330 against cognate (loxP21) and non-cognate (NCD1) DNA; CD spectra of free and bound DNA; 2D ¹H-¹⁵N TROSY-HSQC spectra of apo and DNA-bound Cre; predicted DNA shape analysis referenced but not shown
- **Missing materials affecting confidence** Figure 1 (Cre structure and DNA sequences), Figure 2 (ITC thermograms and fits), Figure 3 (CD spectra), Figure 4 (NMR overlays), Figure 5 (residue-specific CSP analysis), Figure S1-S6, full experimental replicates and error analysis, NMR assignment details, ITC fitting residuals, and raw data availability

## Reviewer
- **Overall assessment** The manuscript addresses a significant question in site-specific recombination: how Cre achieves specificity despite limited base-specific contacts. The combination of ITC, CD, and NMR is appropriate and potentially powerful. However, the current text does not provide sufficient quantitative detail to evaluate the robustness of the thermodynamic analysis, the statistical significance of the CD differences, or the assignment confidence in the NMR spectra. The central claims regarding autoinhibition and induced-fit are plausible and consistent with prior structural work, but the evidence as presented is incomplete. The manuscript would benefit from clearer presentation of fitting procedures, error propagation, and control experiments, as well as a more direct test of the proposed three-state model.
- **Who would be interested in the results, and why** Researchers in genome engineering, site-specific recombinase biology, and protein-DNA recognition. The work has translational relevance for improving Cre-based tools and for engineering recombinases with altered specificity. The thermodynamic framework may also interest biophysicists studying indirect readout mechanisms.
- **Major strengths** (1) The study directly tests a previously proposed autoinhibition model using a deletion mutant, providing quantitative affinity comparisons. (2) The combination of ITC, CD, and NMR offers complementary views of binding thermodynamics and conformational changes. (3) The use of two non-cognate controls (NCD1 and NCD2) strengthens the claim that observed NMR differences are sequence-specific. (4) The discussion thoughtfully connects the findings to prior structural data and to practical implications for recombinase engineering.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (three-state model parameter identifiability), R1-M2 (NMR assignment confidence), R1-M3 (CD data quantification and controls), R1-M4 (ITC fitting and error reporting)
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The autoinhibition concept has been proposed previously (ref 9), and the induced-fit idea is not entirely new, but the direct thermodynamic characterization is a useful contribution.  
  *Scientific importance*: High for the recombinase field and for genome editing applications. Understanding specificity determinants could inform engineering efforts.  
  *Interdisciplinary readership*: Moderate. The topic is specialized, but the mechanistic insights could appeal to biophysicists and protein engineers.  
  *Technical soundness*: Currently not fully assessable due to missing quantitative details and controls. The experimental design is reasonable, but the analysis needs strengthening.  
  *Readability for nonspecialists*: Generally clear, though some sections assume familiarity with recombinase biology and NMR spectroscopy. The abstract is accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the experimental approach is appropriate, but the current evidence does not fully establish the proposed model. Additional quantitative analysis, controls, and clearer presentation are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data analysis and model validation
- **Claim pointer** The authors state that the three-state model yields an isomerization constant K_iso = 5.3 ± 1.7 and an autoinhibited population of 85%, based on comparing WT and CreΔ330 affinities.
- **Evidence pointer** Results section "Autoinhibition by the C-terminus of Cre decreases affinity towards cognate and non-cognate DNA"; equations 1 and 2
- **Concern** The three-state model assumes that CreΔ330 binding affinity directly reflects the binding-competent state (K_D) and that the only difference between WT and CreΔ330 is the absence of autoinhibition. This assumption is not validated. The deletion of residues 330-343 could alter protein stability, folding, or the intrinsic DNA binding interface beyond simply removing the autoinhibitory interaction. The authors do not provide independent evidence (e.g., circular dichroism or NMR of the free proteins) that CreΔ330 is structurally equivalent to the binding-competent state of WT Cre. Furthermore, the model does not account for potential differences in binding stoichiometry or aggregation states between the two proteins. The reported K_iso and population estimates are therefore model-dependent and may not be uniquely determined by the data.
- **Why it matters** The claim of 85% autoinhibited population is a central quantitative result. If the model assumptions are incorrect, the interpretation of the affinity difference as purely due to autoinhibition is unsupported, weakening the mechanistic conclusion.
- **Resolution test** Provide structural or biophysical evidence (e.g., CD spectra, NMR ¹H-¹⁵N HSQC of free WT and CreΔ330) showing that the deletion does not globally perturb the protein fold. Perform a global fit of the ITC data to the three-state model without fixing K_D from the CreΔ330 experiment, and report confidence intervals. Alternatively, use a mutant that specifically disrupts the autoinhibitory interaction without deleting the entire helix.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation and evidence strength
- **Claim pointer** The authors claim that NMR spectra reveal "unique conformational changes" in Cre when bound to cognate loxP DNA, including CSPs at residues distal to the DNA binding interface (G93, T140, V304) and peak doubling at Phe64 and Asp233, which are not observed in non-cognate complexes.
- **Evidence pointer** Results section "Cognate DNA Binding Induces Unique Protein Structural Changes"; Figures 4 and 5
- **Concern** The NMR data are presented qualitatively. The authors state that "well-resolved signals could be tentatively assigned," but no assignment strategy, confidence metrics, or validation is described. Without sequence-specific assignments, the claim that specific residues (G93, T140, V304, Phe64, Asp233) show differential behavior cannot be verified. Additionally, the observation of peak doubling is attributed to "slow time-scale dynamics," but no relaxation dispersion or lineshape analysis is provided to support this interpretation. The possibility that peak doubling arises from sample heterogeneity, partial dissociation, or non-specific binding is not excluded. The statement that "residues adjacent to prolines appear to exhibit peak doubling" is vague and not quantified.
- **Why it matters** The NMR data are used to support the central claim of induced-fit conformational changes. If the assignments are not reliable or the peak doubling is not rigorously characterized, the evidence for unique protein conformational changes in the cognate complex is weak.
- **Resolution test** Provide a detailed assignment table with resonance-specific CSP values and uncertainties. Show that assignments are based on standard triple-resonance experiments or mutagenesis. Quantify peak doubling (e.g., intensity ratios, exchange rates) and demonstrate that it is specific to the cognate complex and not an artifact of sample conditions. Include control experiments with a non-specific DNA sequence at matched ionic strength.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Data interpretation and controls
- **Claim pointer** The authors state that CD spectra show "large decreases in molar ellipticity" for loxP21 upon Cre binding, while NCD1 shows "less structural changes and opposite" effects, supporting sequence-specific DNA bending.
- **Evidence pointer** Results section "Cre induces unique deformations in loxP DNA half sites upon binding"; Figure 3
- **Concern** The CD data are presented without quantitative analysis. The authors do not report the magnitude of the ellipticity changes, the wavelength of maximum difference, or any statistical comparison between cognate and non-cognate conditions. The statement that NCD1 shows "opposite" changes is not supported by a quantitative metric. Furthermore, the CD signal in the 250-310 nm region reports on base stacking, but protein contributions cannot be fully excluded, especially at the high protein concentrations used. The authors do not describe how the protein background was subtracted or whether the CD changes correlate with the degree of binding (e.g., titration series).
- **Why it matters** The CD data are used to support the induced-fit model. Without quantification and proper controls, the conclusion that cognate binding induces unique DNA deformations is not robust.
- **Resolution test** Report mean residue ellipticity values with standard deviations from at least three independent replicates. Perform a titration to show that the CD change saturates at the expected binding stoichiometry. Subtract protein-only spectra and show that the observed changes are DNA-dependent. Provide a statistical test (e.g., t-test) comparing cognate vs. non-cognate changes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data reporting and reproducibility
- **Claim pointer** The authors report ITC-derived K_D, ΔH, and TΔS values for WT Cre and CreΔ330 binding to loxP21 and NCD1.
- **Evidence pointer** Results section "Autoinhibition by the C-terminus of Cre decreases affinity towards cognate and non-cognate DNA"; Figure 2
- **Concern** The ITC results are reported as single values with uncertainties, but the number of replicates, the fitting model details, and the quality of the fits are not described. The authors state that fits were performed using ITCSIMLIB to a single-site model, but do not report the stoichiometry (n) or the residuals. For the WT Cre-NCD1 interaction, the authors state that "no net heat" was observed, but do not provide a detection limit or an upper bound on K_D. The reported ΔH for CreΔ330-loxP21 (+25.1 kcal/mol) is substantially more positive than for WT-loxP21 (+17.1 kcal/mol), which is counterintuitive if the deletion removes an autoinhibitory interaction that would be expected to stabilize the complex. This discrepancy is not discussed.
- **Why it matters** Thermodynamic parameters are the primary quantitative evidence for the autoinhibition model. Without proper error analysis, replicate numbers, and discussion of unexpected trends, the reliability of the conclusions is uncertain.
- **Resolution test** Report the number of independent titrations (n ≥ 3), the stoichiometry parameter, and the standard deviation for each parameter. Show representative fits with residuals. For the WT-NCD1 interaction, provide an upper limit on K_D based on the detection limit of the instrument. Discuss the physical basis for the more positive ΔH for CreΔ330.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "conservative site-specific tyrosine recombinase" is used without defining "conservative" in this context. Readers unfamiliar with recombinase biology may misinterpret this as a statement about evolutionary conservation rather than the absence of DNA synthesis or degradation during recombination.
- **Required correction** Define "conservative" (i.e., no net gain or loss of nucleotides) at first use, or rephrase to "site-specific tyrosine recombinase that catalyzes conservative DNA rearrangements."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "Autoinhibition by the C-terminus of Cre decreases affinity towards cognate and non-cognate DNA"
- **Evidence pointer** Figure 2 legend (not provided)
- **Issue** The text refers to "Figure 2a" and "Figure 2d" but does not describe what panels b and c contain. The reader cannot follow the figure structure.
- **Required correction** Ensure the figure legend clearly describes all panels, or renumber the panels to match the text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results section "Autoinhibition by the C-terminus of Cre decreases affinity towards cognate and non-cognate DNA"
- **Evidence pointer** Text describing K_D values
- **Issue** The text states that CreΔ330 binds loxP21 with K_D = 2.72 ± 0.84 nM, which is approximately 6-fold tighter than WT (17.8 ± 2.5 nM). However, the text later states that "autoinhibition reduces affinity ∼6-fold towards cognate DNA," which is consistent. The discrepancy is that the ΔH for CreΔ330 is more positive than for WT, which would normally imply a less stable complex. The authors do not address this apparent contradiction.
- **Required correction** Add a sentence explaining how a more positive ΔH can be offset by a more favorable entropy change to yield tighter binding, or discuss alternative interpretations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods section "Isothermal Titration Calorimetry"
- **Evidence pointer** Methods, ITC section
- **Issue** The text mentions "CreΔ300" in the methods, but the mutant is referred to as "CreΔ330" throughout the rest of the manuscript. This is likely a typographical error.
- **Required correction** Correct the mutant name to "CreΔ330" in the methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section "A role for induced-fit in site-selection by Cre"
- **Evidence pointer** Discussion, paragraph 2
- **Issue** The authors state that "the lack of base-specific contacts between Cre and loxP appears to be overcome through an indirect readout mechanism," but they do not cite specific structural studies that quantify the number of base-specific contacts. A brief comparison with prior structural analyses (e.g., from the cited crystal structures) would strengthen the argument.
- **Required correction** Add a sentence referencing the relevant structural studies and the observed number of direct base contacts.

## Risk / unsupported claims
- The claim that the C-terminal autoinhibition "may also play a role in the ability for Cre to rapidly scan DNA" is speculative and not directly tested by the presented experiments. The authors do not provide kinetic or single-molecule data to support this.
- The statement that "the large unfavorable enthalpy of Cre binding to loxP half-sites arises in large part from the energetic cost of deforming the loxP DNA" is an inference. The authors do not measure the deformation energy independently or compare to a control DNA that is pre-bent.
- The claim that "binding-coupled conformational changes are major contributors to the large CSPs observed in the cognate Cre-loxP complexes" is based on qualitative NMR comparisons. Without quantitative CSP analysis or a structural model, the relative contributions of direct contacts versus conformational changes cannot be deconvolved.
- The extension of conclusions from half-site binding to full loxP site recognition in the context of tetrameric complexes is not directly supported by the data, as the authors acknowledge but do not test.