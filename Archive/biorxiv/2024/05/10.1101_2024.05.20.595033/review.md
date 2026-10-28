## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, materials and methods, and supplementary figure/table legends
- **Assessment boundary** Scientific content, technical soundness, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors propose a model for transcriptional autoregulation of the Pseudomonas putida xre-res toxin-antitoxin system, in which a 4:2 Xre-RES heterohexameric complex binds to an imperfect inverted repeat (S4) in the promoter region via one Xre dimer, with a second Xre dimer engaging a secondary site between S3 and S4, and where a concentration-dependent equilibrium between a DNA-binding 4:2 form and a non-binding 2:2 form controls repression.
- **Visible evidence base** In vivo promoter activity assays with GFP reporter; SEC-MALS and analytical SEC binding assays; ITC binding measurements; X-ray crystal structure at 2.7 Å; mass photometry; AlphaFold 3 structural prediction
- **Missing materials affecting confidence** Coordinates and structure factors not available for independent validation; AlphaFold 3 prediction details and confidence metrics only partially described; raw data for statistical analyses not shown; supplementary figures and tables referenced but not provided; no in vivo binding or occupancy data; no direct demonstration of the proposed 2:2 to 4:2 transition in cells

## Reviewer
- **Overall assessment** This manuscript presents a structurally and biochemically detailed study of a bacterial toxin-antitoxin transcriptional regulator with an unusual 4:2 stoichiometry. The crystal structure of the Xre-RES complex bound to its operator DNA is a valuable contribution, and the observation of asymmetric DNA binding by the two Xre dimers is intriguing. The combination of in vivo reporter assays, in vitro biophysical measurements, and structural biology provides a multi-pronged approach. However, several claims regarding the secondary binding site and the dynamic equilibrium between 2:2 and 4:2 forms are not fully supported by the presented evidence. The AlphaFold 3 prediction, while interesting, is used to support a functional model without direct experimental validation of the secondary site. The in vivo relevance of the concentration-dependent transition remains speculative. The manuscript would be strengthened by additional experiments directly testing the proposed model, particularly regarding the secondary binding site and the functional consequences of the 2:2 to 4:2 transition.
- **Who would be interested in the results, and why** Researchers in bacterial transcriptional regulation, toxin-antitoxin systems, and structural biology of protein-DNA complexes would find this work of interest. The unusual asymmetric DNA binding mode and the proposed higher-order DNA interaction mechanism could inform studies of other multi-dimer transcriptional regulators. The work also contributes to the growing understanding of toxin-antitoxin system diversity and regulation, which has implications for bacterial stress responses and persistence.
- **Major strengths** 1. The crystal structure of the Xre-RES-DNA complex at 2.7 Å provides a solid structural foundation and reveals an unexpected asymmetric binding mode. 2. The combination of in vivo and in vitro approaches, including reporter assays, SEC-MALS, ITC, and mass photometry, provides complementary evidence. 3. The identification of a specific operator element (S4) and the demonstration of high-affinity binding are well supported. 4. The proposed model of concentration-dependent regulation is conceptually interesting and testable.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The secondary binding site claim relies on indirect evidence (crystal packing contacts and AlphaFold 3 prediction) without direct experimental validation. The in vivo significance of the 2:2 to 4:2 transition is not demonstrated. The ITC data for the 5'-perf and 3'-perf variants show extremely weak affinities (micromolar range) that are difficult to interpret reliably.
- **Assessment against Nature-style criteria** Originality: The asymmetric DNA binding mode and the proposed higher-order interaction mechanism are novel and would be of interest to a broad readership. Scientific importance: The work advances understanding of toxin-antitoxin system regulation and provides a potential paradigm for multi-dimer transcriptional regulators. Interdisciplinary readership: The combination of structural biology, biophysics, and microbiology would appeal to researchers across these fields. Technical soundness: The structural and biophysical methods are generally sound, but the support for the secondary binding site and the dynamic equilibrium model is incomplete. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume familiarity with structural biology terminology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the secondary binding site and the functional significance of the 2:2 to 4:2 transition.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence support for secondary binding site
- **Claim pointer** The authors claim that the Xre-RES complex binds to a secondary site in the promoter region between S3 and S4, based on crystal packing contacts and AlphaFold 3 prediction.
- **Evidence pointer** Results section "The structure of the Xre-RES Pp -DNA complex reveals an unusual, asymmetrical DNA binding site"; Discussion section; Figure 5F-G; Figure S7
- **Concern** The existence of a functional secondary DNA binding site is a central component of the proposed model, yet the evidence is indirect. The crystal structure shows interactions with a symmetry-related DNA duplex, which could be a crystallographic artifact. The AlphaFold 3 prediction, while supportive, is a computational model and the authors themselves note the confidence is in a "grey zone" (iPTM score 0.6). No direct biochemical or biophysical experiment demonstrates binding of the second Xre dimer to the proposed secondary site in the intact promoter. The in vivo data with the Δrepeat mutant shows partial repression, which is interpreted as evidence for a secondary site, but alternative explanations (e.g., residual binding to the mutated S4, or indirect effects) are not excluded.
- **Why it matters** The proposed model of higher-order DNA binding by the Xre-RES complex depends critically on the existence of a functional secondary binding site. Without direct evidence, the central mechanistic claim of the paper is not established.
- **Resolution test** Provide direct evidence of binding to the secondary site, such as electrophoretic mobility shift assays (EMSA) or fluorescence anisotropy with DNA fragments containing the proposed secondary site, with mutations abolishing binding. Alternatively, a structure of the complex bound to a longer DNA fragment containing both sites would be definitive. Mutational analysis of residues predicted to contact the secondary site, combined with in vivo repression assays, would also strengthen the case.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance of 2:2 to 4:2 transition
- **Claim pointer** The authors propose a concentration-dependent model in which the Xre-RES complex transitions between a non-binding 2:2 form and a DNA-binding 4:2 form, and that this transition regulates transcription.
- **Evidence pointer** Results section "The Xre Pp dimer is stabilised by higher-order complex formation and required for transcriptional repression"; Figure 5; Discussion
- **Concern** The mass photometry data show concentration-dependent changes in the oligomeric state of the complex, and the 2:2 form does not bind DNA in vitro. However, the in vivo relevance of this transition is not demonstrated. The authors do not show that the cellular concentration of the complex falls within the range where the transition occurs, nor do they demonstrate that the 2:2 form exists in cells or that its formation leads to derepression. The model is plausible but remains speculative without direct in vivo evidence.
- **Why it matters** The proposed regulatory mechanism relies on the physiological relevance of the 2:2 to 4:2 equilibrium. If this transition does not occur at cellular concentrations, the model would not be relevant to the native system.
- **Resolution test** Measure the cellular concentration of the Xre-RES complex and compare to the dissociation constants governing the oligomeric equilibrium. Use in vivo crosslinking or other methods to detect the 2:2 form in cells. Demonstrate that conditions favoring the 2:2 form (e.g., dilution or mutation) lead to derepression of the promoter in vivo.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of ITC data for S4 variants
- **Claim pointer** The authors report drastically reduced binding affinities for the 5'-perf and 3'-perf S4 variants (K D = 341 ± 264 µM and 80 ± 79 µM, respectively) compared to the native S4 (K D = 231 ± 46 nM), yet in vivo repression is maintained for these variants.
- **Evidence pointer** Results section "The Xre-RES Pp complex binds directly to S4 in vitro"; Table 2; Figure 2D
- **Concern** The micromolar affinities reported for the S4 variants are extremely weak and the errors are large, making these measurements unreliable. The conclusion that these variants still support repression in vivo despite such weak binding is paradoxical and suggests either that the ITC measurements do not reflect the relevant binding mode, or that the in vivo repression occurs through a different mechanism. The authors interpret this as evidence for a secondary binding site, but the data are not robust enough to support this conclusion.
- **Why it matters** The interpretation of the in vivo data for the S4 variants is used to support the existence of a secondary binding site. If the ITC measurements are unreliable, this line of evidence is weakened.
- **Resolution test** Repeat the ITC measurements with higher concentrations or use a more sensitive technique such as fluorescence polarization or surface plasmon resonance. Alternatively, perform competition experiments or use longer DNA fragments containing the full operator to assess binding in a more physiologically relevant context.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure legends
- **Affected element** Figure 5C
- **Evidence pointer** Results section "The Xre Pp dimer is stabilised by higher-order complex formation and required for transcriptional repression"
- **Issue** The mass photometry data in Figure 5C show multiple peaks at different concentrations, but the assignment of these peaks to specific oligomeric states (2:2, 3:2, 4:2) is not clearly described in the legend or text. The text mentions "roughly corresponds" but does not provide a precise assignment.
- **Required correction** Provide a clear table or annotation in the figure legend assigning each observed mass to the corresponding oligomeric state, and state the expected molecular weights for each state.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** In vivo repression assays
- **Evidence pointer** Results section "The P. putida xre-res locus is transcriptionally auto-regulated"; Figure 1C-D, Figure 2B-D
- **Issue** The number of biological replicates and the statistical test used for the in vivo repression assays are not clearly stated in the main text. The methods section mentions triplicates but does not specify whether these are technical or biological replicates.
- **Required correction** Clearly state the number of biological replicates and the statistical test used in the figure legends or methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** AlphaFold 3 methodology
- **Affected element** AlphaFold 3 prediction
- **Evidence pointer** Results section "Structural basis for Xre-RES Pp binding at two sites in the P XR promoter region"; Figure S7
- **Issue** The description of the AlphaFold 3 prediction is brief. The authors do not specify the input sequences used, the number of models generated, or the criteria for selecting the presented model. The pLDDT and iPTM scores are mentioned but not fully contextualized.
- **Required correction** Provide more details on the AlphaFold 3 prediction parameters, including the input sequences, model selection criteria, and a more detailed interpretation of the confidence scores.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The terms "operator" and "promoter" are used somewhat interchangeably. The S4 element is referred to as an "operator" in some places and as part of the "promoter region" in others. This could be confusing for readers.
- **Required correction** Define the terms clearly at first use and use them consistently throughout the manuscript.

## Risk / unsupported claims
- The existence of a functional secondary DNA binding site in the promoter region between S3 and S4 is not directly supported by experimental evidence; it relies on crystal packing contacts and an AlphaFold 3 prediction with moderate confidence scores.
- The claim that the 2:2 Xre-RES complex is a "non-binding form" that exists in a concentration-dependent equilibrium with the 4:2 form in vivo is not demonstrated; the in vitro data show the 2:2 form does not bind DNA, but the cellular relevance is not established.
- The interpretation that the Δrepeat mutant still shows partial repression due to a secondary binding site is not conclusive; alternative explanations are not excluded.
- The ITC measurements for the 5'-perf and 3'-perf S4 variants are unreliable due to very weak affinities and large errors, making the conclusion that these variants support repression through a secondary site unsupported.
- The claim that the AlphaFold 3 prediction "strongly supports" the secondary binding site is overstated given the moderate iPTM score and the lack of experimental validation.