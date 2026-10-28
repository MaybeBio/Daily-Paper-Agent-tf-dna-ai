## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends as embedded in text)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and structural/thermodynamic evidence as presented in the provided manuscript text. Figures and supplementary materials referenced but not fully visible are assessed only through textual description.
- **Shared manuscript claim summary** The authors report that deletion of the RecB nuclease domain (RecB Nuc) from E. coli RecBCD increases DNA binding affinity and reduces the extent of base pair melting upon binding to blunt DNA ends, as measured by ITC and visualized by cryo-EM. They propose that RecB Nuc exerts a long-range allosteric effect on DNA binding and melting, potentially via linker-linker interactions between RecB and RecC.
- **Visible evidence base** ITC binding and enthalpy data for RecB ΔNuc CD with blunt and twin-tailed DNA substrates; cryo-EM structures of RecB ΔNuc CD and RecB ΔNuc CD-DNA at 3.4 Å; sedimentation velocity data; structural comparisons with previously published RecBCD and RecBCD-DNA structures.
- **Missing materials affecting confidence** Full figures and supplementary figures/tables are not directly visible; exact DNA sequences and tail lengths for all substrates are not fully specified in the text; detailed cryo-EM validation metrics (FSC curves, model-to-map fit) are referenced but not shown; no kinetic data on DNA unwinding initiation for RecB ΔNuc CD are presented in this manuscript.

## Reviewer
- **Overall assessment** This manuscript presents a focused and mechanistically informative study on the regulatory role of the RecB nuclease domain in RecBCD function. The combination of thermodynamic measurements and cryo-EM structures provides complementary evidence that RecB Nuc deletion alters DNA binding energetics and reduces base pair melting. The claim that RecB Nuc exerts a long-range allosteric effect is plausible and well-supported by the structural comparisons, though the specific mechanistic proposal involving linker-linker interactions remains speculative. The work will be of interest to the helicase and DNA repair communities. However, several technical and interpretive points require clarification before the conclusions can be fully accepted.
- **Who would be interested in the results, and why** Researchers studying helicase mechanisms, particularly SF1A family helicases and their regulation; investigators interested in DNA double-strand break repair and homologous recombination; structural biologists studying multi-domain molecular machines by cryo-EM; and biophysicists using ITC to dissect protein-DNA interaction energetics.
- **Major strengths** The study addresses a clear and important question regarding the regulatory function of a mobile domain in a multi-subunit helicase. The combination of ITC and cryo-EM is powerful and appropriate. The comparison between RecB ΔNuc CD and previously published RecBCD data allows quantitative assessment of the nuclease domain's contribution. The observation that RecB Nuc deletion increases DNA binding affinity is counterintuitive and interesting, suggesting allostery rather than direct contact. The cryo-EM structures provide direct evidence for reduced base pair melting.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative link between ΔΔH and number of melted base pairs), R1-M2 (structural interpretation of RecB 2B and RecC Cter conformational differences), R1-M3 (generality of the allosteric model).
- **Assessment against Nature-style criteria** Originality: The finding that a nuclease domain regulates DNA binding and melting allosterically is novel and extends previous work on RecBCD. Scientific importance: The results have implications for understanding how multi-domain helicases coordinate DNA unwinding and processing, which is relevant to DNA repair mechanisms. Interdisciplinary readership: The work bridges enzymology, structural biology, and biophysics, and should appeal to a broad readership in these areas. Technical soundness: The experimental approaches are generally sound, but the quantitative interpretation of ITC data in terms of base pair numbers requires more rigorous justification. Readability for nonspecialists: The manuscript is clearly written and the logic is easy to follow, though some domain-specific terminology may require familiarity with helicase biology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the quantitative link between thermodynamic measurements and the number of melted base pairs, and the structural interpretation of conformational differences.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative interpretation
- **Claim pointer** The authors state that "RecB ΔNuc CD binding to a blunt DNA end is associated with a large favorable ΔH obs, but much smaller than observed for RecBCD, suggesting that deletion of RecB Nuc limits bp melting from a blunt DNA." They further estimate that RecB ΔNuc CD melts 7-9 bp versus 9-12 bp for RecBCD.
- **Evidence pointer** Results section "RecB ΔNuc CD melts fewer base pairs than RecBCD upon binding a blunt DNA end"; Figure 2D; Supplementary Table 3
- **Concern** The estimate of the number of melted base pairs is derived from the difference in ΔH between blunt and pre-melted DNA substrates, divided by a per-base-pair enthalpy cost. This approach assumes that the per-base-pair enthalpy of melting is constant and independent of sequence and context, and that the final bound states are identical between blunt and pre-melted substrates. The authors do not provide a rigorous justification for these assumptions, nor do they account for potential differences in protein-DNA contacts between the two substrate types. The per-base-pair enthalpy values cited from the literature may not be directly applicable to the specific DNA sequences and buffer conditions used here.
- **Why it matters** The quantitative claim about the number of melted base pairs is a central conclusion of the paper and is used to support the regulatory role of RecB Nuc. If the per-base-pair enthalpy assumption is not valid, the estimated number of melted base pairs could be substantially in error, weakening the conclusion.
- **Resolution test** The authors should provide a more detailed error analysis, including propagation of uncertainties from the ITC measurements and the literature values for per-base-pair melting enthalpy. They should also discuss the validity of the assumption that the final bound states are identical for blunt and pre-melted substrates, and ideally test this by comparing structures of RecB ΔNuc CD bound to both substrate types.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Structural interpretation
- **Claim pointer** The authors state that "the docking and undocking of RecB Nuc can influence the conformations of RecB 2B and RecC Cter in the DNA free state of RecBCD" and propose that this occurs via linker-linker interactions.
- **Evidence pointer** Results section "RecB Nuc can exert long-range allosteric effects on DNA binding by affecting the conformations of RecB 2B and RecC Cter domains"; Table 1; Figure 4
- **Concern** The structural comparisons show RMSD differences in RecB 2B and RecC Cter between RecB ΔNuc CD and RecBCD, but the interpretation that these differences are caused by RecB Nuc docking/undocking is indirect. The authors compare structures with RecB Nuc deleted versus present, but do not directly observe the undocked state of RecB Nuc in the same complex. The proposal that linker-linker interactions mediate the allosteric effect is speculative and not directly tested. Additionally, the functional significance of the observed conformational differences is not established.
- **Why it matters** The proposed allosteric mechanism is a key conceptual contribution of the paper. If the structural differences are not causally linked to RecB Nuc docking status, the mechanistic model is weakened.
- **Resolution test** The authors should either provide direct structural evidence for the undocked RecB Nuc state and its interactions with the linkers, or perform mutagenesis experiments targeting the proposed linker-linker interface to test the functional predictions of the model.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors suggest that "RecB Nuc may manifest its long-range allosteric effect on DNA binding and DNA melting via linker-linker interactions between RecB and RecC."
- **Evidence pointer** Discussion section
- **Concern** The proposed mechanism is based on a single variant (RecB ΔNuc CD) and a limited set of DNA substrates. It is unclear whether the observed effects are specific to the deletion construct or represent a general regulatory mechanism. The authors do not test whether the effects scale with the size of the deletion or whether point mutations in the linker regions phenocopy the deletion.
- **Why it matters** The claim of a general allosteric mechanism requires evidence that the effect is not an artifact of the specific deletion construct used.
- **Resolution test** The authors should test additional variants, such as point mutations in the RecB linker or RecC linker, to determine whether the observed effects are recapitulated. They should also test a range of DNA substrates with different tail lengths and sequences to establish the generality of the effect.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2D
- **Evidence pointer** Results section "RecB ΔNuc CD melts fewer base pairs than RecBCD upon binding a blunt DNA end"
- **Issue** The figure legend for Figure 2D is not provided in the manuscript text, making it difficult to fully interpret the plotted data points and error bars.
- **Required correction** Provide a complete figure legend for Figure 2D, including the number of independent replicates, the meaning of error bars, and the statistical tests used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methods clarity
- **Affected element** ITC methods
- **Evidence pointer** Methods section "Isothermal Titration Calorimetry"
- **Issue** The ITC fitting model is described as an "N independent and identical sites model," but the manuscript does not specify whether the stoichiometry N was fixed or floated during fitting, and how the reported uncertainties were calculated.
- **Required correction** Clarify the fitting procedure, including whether N was fixed or floated, and describe how uncertainties were propagated from the fits.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Structural validation
- **Affected element** Cryo-EM structures
- **Evidence pointer** Methods section "Image processing and model building"
- **Issue** The manuscript reports overall resolutions of 3.4 Å for both structures but does not provide local resolution estimates or validation metrics such as FSC curves, model-to-map correlation, or MolProbity scores.
- **Required correction** Include standard cryo-EM validation metrics in the supplementary materials, including FSC curves, local resolution maps, and model validation statistics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the allosteric mechanism would benefit from a more explicit comparison with other SF1A helicases where 2B domain movements have been shown to regulate activity, beyond the brief mention of PcrA, Rep, UvrD, and M. tuberculosis UvrD1.
- **Required correction** Expand the discussion to more thoroughly contextualize the proposed mechanism within the broader helicase field.

## Risk / unsupported claims
- The quantitative estimate of 7-9 bp melted by RecB ΔNuc CD is not fully supported due to assumptions in the per-base-pair enthalpy calculation (R1-M1).
- The claim that RecB Nuc exerts its allosteric effect via linker-linker interactions is speculative and not directly tested (R1-M2).
- The statement that "RecB Nuc may manifest its long-range allosteric effect on DNA binding and DNA melting via linker-linker interactions between RecB and RecC" is presented as a hypothesis but is not distinguished from other possible mechanisms.
- The claim that the nuclease domain is responsible for formation of the (RecBCD)2 hexamer is based on the absence of hexameric RecB ΔNuc CD in purification, but this is not directly tested and may be influenced by other factors.
- The functional significance of the observed conformational differences in RecB 2B and RecC Cter is not established, as no functional assays are presented that link these conformational states to DNA binding or melting activity.