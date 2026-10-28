## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report NMR-based characterization of the interaction between the intrinsically disordered CR2C region of FOXO4 and the KIX domain of CBP. They report binding interface mapping by chemical-shift perturbation, observation of two sets of amide cross-peaks for CR2C, evidence for distinct conformational subpopulations from proline mutagenesis and truncation, independent apparent K(d) estimates for these subpopulations, retention of disorder upon binding by circular dichroism, and docking models suggesting multiple disordered binding conformations on the KIX MLL site. They conclude that an adjacent poly-proline tract modulates KIX binding through conformational heterogeneity.
- **Visible evidence base** Abstract text only; no experimental details, spectra, fitting parameters, or model coordinates provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental methods, NMR assignment details, titration data, K(d) fitting procedures, mutagenesis construct descriptions, circular dichroism spectra, docking methodology and validation, and any statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting biophysical study of a disordered transcription factor region binding to a well-characterized globular domain. The observation of conformational heterogeneity in a disordered ligand upon binding is a topic of broad relevance. However, the abstract alone provides insufficient detail to evaluate the rigor of the K(d) estimates, the interpretation of cross-peak splitting, or the validity of the docking models. The central claim that conformational heterogeneity modulates binding behavior is plausible but not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying intrinsically disordered proteins and their binding mechanisms, structural biologists using NMR to characterize protein-protein interactions, and investigators focused on FOXO transcription factor regulation or CBP KIX-mediated transcriptional coactivation. The methodological approach may also interest NMR spectroscopists working on conformational exchange in disordered systems.
- **Major strengths** The study addresses a specific and previously uncharacterized interaction, namely FOXO4 CR2C binding to CBP KIX, which fills a gap given prior work on FOXO3a. The combination of multiple biophysical techniques, including NMR chemical-shift perturbation, mutagenesis, circular dichroism, and docking, provides a multifaceted approach. The observation of two cross-peak sets in a disordered region is a concrete and potentially significant finding that could reveal biologically relevant conformational behavior.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of K(d) estimation
  - **Claim pointer** The abstract states that apparent K(d) values were estimated independently for distinct conformational subpopulations.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The abstract does not describe how the two subpopulations were resolved for independent K(d) determination. In NMR titration experiments, overlapping or exchanging resonances typically complicate separate quantification. Without details on the fitting model, whether the two sets of peaks were treated as independent binding events or as interconverting species, and how the populations were assigned, the reliability of these K(d) values cannot be assessed.
  - **Why it matters** Independent K(d) values for two subpopulations are a central quantitative result. If the fitting approach conflates exchange broadening, differential relaxation, or partial peak overlap with true population differences, the reported affinities could be artefactual. This would undermine the conclusion that the poly-proline tract modulates binding through conformational heterogeneity.
  - **Resolution test** Provide the full titration data, the fitting equations, the number of parameters, and the uncertainties for each K(d). Show that the two-state model is statistically justified compared to a single-site model, and demonstrate that the two cross-peak sets correspond to slowly exchanging conformations rather than to artefacts of sample heterogeneity or differential protonation.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of conformational subpopulation assignment
  - **Claim pointer** The abstract states that systematic proline mutagenesis and truncation support the presence of distinct conformational subpopulations.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The abstract does not specify which prolines were mutated, how many constructs were tested, or what the truncation boundaries were. It is unclear whether the mutagenesis was designed to disrupt the poly-proline tract specifically or whether it targeted the PhiXXPhiPhi motif. Without this information, the link between the poly-proline tract and the observed subpopulations is not established.
  - **Why it matters** The central mechanistic claim is that the poly-proline tract modulates binding behavior. If the mutagenesis did not isolate the effect of this tract, alternative explanations, such as changes in the PhiXXPhiPhi motif itself or in overall chain length, remain possible. The conclusion would then be overstated.
  - **Resolution test** List the exact mutations and truncation constructs, show the corresponding NMR spectra or binding data for each, and demonstrate that perturbations to the poly-proline tract specifically alter the population ratio or binding affinity while mutations elsewhere do not.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of docking model interpretation
  - **Claim pointer** The abstract states that docking models suggest FOXO4 CR2C binds in multiple disordered conformations on the KIX MLL site.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The abstract provides no information on the docking method, the ensemble size, the scoring function, or how the models were validated against the NMR data. For a disordered peptide, docking is notoriously prone to false positives, and the claim of multiple disordered conformations requires demonstration that the models are consistent with the experimental restraints rather than merely being plausible poses.
  - **Why it matters** The structural interpretation is a key part of the conclusion. If the docking models are not restrained by or validated against the chemical-shift and mutagenesis data, they add little evidential weight. The claim of multiple disordered conformations would then rest on the NMR data alone, which may be insufficient to define the binding mode.
  - **Resolution test** Describe the docking protocol, show how the resulting models satisfy the experimentally identified binding interface, and provide a quantitative comparison between predicted and observed chemical-shift perturbations or intermolecular contacts. If possible, include relaxation or dynamics data that support the disordered nature of the bound state.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of terminology
  - **Affected element** Use of the term "PhiXXPhiPhi"
  - **Evidence pointer** Abstract text
  - **Issue** The abstract uses the notation "PhiXXPhiPhi" without defining Phi. While this may be standard in the field, a brief definition would improve accessibility for readers outside the transcription factor or disordered protein community.
  - **Required correction** Define Phi as a hydrophobic residue at first use, for example by writing "Phi (hydrophobic)XXPhi(hydrophobic)Phi(hydrophobic)" or adding a parenthetical note.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness of reporting
  - **Affected element** K(d) values
  - **Evidence pointer** Abstract text
  - **Issue** The abstract mentions apparent K(d) values but does not report any numerical values or units. This makes it impossible for a reader to gauge the affinity range or compare with other KIX interactions.
  - **Required correction** Include representative K(d) values with uncertainties in the abstract, or state that the values are reported in the main text with a summary range.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretive caution
  - **Affected element** Statement that CR2C "remains disordered upon binding"
  - **Evidence pointer** Abstract text
  - **Issue** Circular dichroism is a low-resolution technique and may not detect partial folding or local ordering in a bound disordered peptide. The statement is presented as definitive, but the evidence level may not support a strong claim of full disorder retention.
  - **Required correction** Soften the claim to indicate that circular dichroism shows no significant gain in secondary structure, or add a qualifier such as "under the conditions tested" and note the limitations of the technique.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, and R1-M3 are blocking. The K(d) estimation method, the mutagenesis design, and the docking validation are all insufficiently described in the abstract to support the central conclusions. Without these details, the claim that conformational heterogeneity modulates binding is not established.
- **Assessment against Nature-style criteria**  
  Originality: The study addresses a specific uncharacterized interaction and reports a potentially novel observation of conformational heterogeneity in a disordered ligand. This is a reasonable incremental advance but not a conceptual breakthrough.  
  Scientific importance: The FOXO4-CBP KIX interaction is biologically relevant, and understanding how poly-proline tracts modulate disordered protein binding could have broader implications. However, the importance is moderate and depends on the robustness of the findings.  
  Interdisciplinary readership: The topic would appeal to structural biologists, biophysicists, and researchers in transcription regulation. The abstract is written in a way that is largely accessible, though the specialized NMR terminology may limit broader readership.  
  Technical soundness: Cannot be fully assessed from the abstract. The described methods are appropriate in principle, but the lack of detail on K(d) fitting, mutagenesis design, and docking validation prevents a positive assessment.  
  Readability for nonspecialists: The abstract is concise and generally clear, but the undefined "PhiXXPhiPhi" notation and the absence of numerical results reduce accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The study has potential merit, and the authors may be able to address the concerns with the full manuscript. A revised assessment would be supportive if the technical details on K(d) estimation, mutagenesis design, and docking validation are provided and if the claims are appropriately calibrated to the evidence.

## Risk / unsupported claims
- The claim that apparent K(d) values were estimated independently for two subpopulations is unsupported without details on the fitting model and data treatment.
- The claim that proline mutagenesis and truncation support distinct conformational subpopulations is unsupported without construct details and corresponding data.
- The claim that docking models suggest multiple disordered binding conformations is unsupported without method description and validation.
- The statement that CR2C remains disordered upon binding is weakly supported by circular dichroism alone, given the technique's limited resolution for detecting partial folding.
- The overall conclusion that the poly-proline tract modulates KIX binding through conformational heterogeneity is not established from the abstract-level evidence.