## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, funding, acknowledgments) as provided by the author.
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and alignment with stated claims. Editorial and formatting issues are noted only where they affect comprehension or reproducibility.
- **Shared manuscript claim summary** The authors report that the SARS-CoV-2 nucleocapsid N-terminal domain (N-NTD), with or without the SR-rich motif, binds single- and double-stranded TRS DNA with nanomolar affinity, melts dsDNA, and undergoes liquid-liquid phase separation (LLPS) in a TRS-dependent manner. They propose structural models from NMR-guided docking and MD simulations, and suggest that unfavorable energetic contributions, particularly involving the TTT motif and β-sheet II residue E174, underlie duplex destabilization and sequence-specific recognition.
- **Visible evidence base** Abstract, full introduction, complete methods for protein purification, DNA constructs, fluorescence spectroscopy, FRET, NMR, docking, MD, and LLPS assays; results sections with figures referenced (Figures 1–7, S1–S17) and tables (S1–S8); discussion and funding statements.
- **Missing materials affecting confidence** Raw data files, complete figure panels, supplementary tables (S1–S8) and figures (S1–S17) are referenced but not fully provided in the submitted text. Specific numerical values for Kd, ΔH, ΔS, and ΔG are cited in tables not included. Full NMR assignment details and validation metrics for docking models are not described. Statistical analysis details for LLPS quantification are incomplete.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive biophysical characterization of the SARS-CoV-2 N-NTD interaction with DNA, with implications for understanding nucleocapsid function and antiviral design. The combination of fluorescence, NMR, and computational approaches is appropriate and the data are largely internally consistent. However, several claims, particularly regarding sequence specificity and the mechanistic link between energetics and melting, are not fully supported by the evidence presented. The LLPS findings are interesting but require additional controls and quantitative rigor. The manuscript would benefit from clearer presentation of quantitative data and a more cautious interpretation of specificity.
- **Who would be interested in the results, and why** Structural biologists and biophysicists studying nucleic acid-protein interactions, virologists interested in SARS-CoV-2 replication mechanisms, and researchers in the field of biomolecular condensates and LLPS. The potential therapeutic implications for N-targeting aptamers or inhibitors may also attract drug discovery audiences.
- **Major strengths** 1) The study addresses an important and under-explored question regarding the molecular basis of N-NTD binding to DNA and its functional consequences. 2) The use of multiple complementary techniques (fluorescence, FRET, NMR, MD) provides a multi-layered view of the interaction. 3) The inclusion of both specific (TRS) and non-specific (NS) sequences allows for comparative analysis. 4) The LLPS experiments extend the functional relevance of the findings beyond simple binding.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data interpretation and claim support
  - **Claim pointer** The authors claim that "a well-defined pattern (ΔH > 0 and ΔS > 0 for ssTRS, and ΔH < 0 and ΔS < 0 for dsTRS) for the thermodynamic profile of binding" is a key finding supporting sequence-specific recognition.
  - **Evidence pointer** Results section "N-NTD and N-NTD-SR bind tighter to ssTRS(–) than ssTRS(+)", Figure 2D, Table S7
  - **Concern** The thermodynamic parameters are derived from van't Hoff analysis of fluorescence quenching data. The authors do not provide confidence intervals or statistical comparisons between TRS and NS conditions. The claim of a "well-defined pattern" is based on qualitative inspection of ΔH and ΔS signs, but the magnitude of differences and their significance are not established. Moreover, the van't Hoff method assumes constant ΔH over the temperature range, which is not validated. The interpretation that hydrophobic contacts dominate ssTRS binding and hydrogen bonds dominate dsTRS binding is speculative without direct calorimetric measurements (e.g., ITC).
  - **Why it matters** The thermodynamic signature is central to the proposed mechanism of specificity and melting. If the pattern is not robust or is an artifact of the fitting procedure, the mechanistic conclusions are weakened.
  - **Resolution test** Provide ITC or DSC data to directly measure ΔH, ΔS, and ΔG. Report standard errors and perform statistical tests (e.g., t-tests) comparing TRS vs. NS for each thermodynamic parameter. Validate the van't Hoff assumption by measuring binding at more temperatures or by using a global fitting model that does not assume linearity.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Structural model validation
  - **Claim pointer** The authors state that "Based on experimental NMR data, we calculated structural models for the interaction of N-NTD with single and double-stranded TRS DNAs" and use these models to propose specific contacts, including the TTT motif interacting with β-sheet II.
  - **Evidence pointer** Results section "Mapping the N-NTD and N-NTD-SR interaction with DNA", Figures 3G–3I, Methods "Computation simulations"
  - **Concern** The docking and MD protocol is described, but no validation metrics are provided. The authors do not report the HADDOCK scores, cluster sizes, RMSD values from the experimental restraints, or any cross-validation (e.g., back-calculation of chemical shifts from the models). The claim that the models are "based on experimental NMR data" is not substantiated without demonstrating that the models satisfy the experimental restraints. The 25° orientation difference between dsTRS and dsNS is presented as significant, but the uncertainty in this angle is not quantified.
  - **Why it matters** The structural models are used to rationalize specificity and melting. If the models are not well-validated, the atomic-level interpretations (e.g., E174 positioning) are unreliable.
  - **Resolution test** Provide a table of HADDOCK statistics (e.g., Z-scores, RMSD from restraints, buried surface area). Show that the models reproduce the observed CSPs (e.g., by calculating predicted CSPs from the models and comparing to experimental values). Report the standard deviation of the orientation angle across the ensemble of models.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** LLPS specificity and controls
  - **Claim pointer** The authors claim that "the preference for TRS over NS DNAs in the formation of liquid condensates" indicates sequence specificity.
  - **Evidence pointer** Results section "N-NTD-SR phase separation is triggered by the SR motif and modulated by TRS binding", Figure 7, Figures S12–S15
  - **Concern** The LLPS experiments show that N-NTD-SR forms condensates with dsTRS and ssTRS but not with ssNS, and forms crystals with dsNS. However, the authors do not report the ionic strength, pH, or protein concentration dependence of these observations beyond a single condition. The reentrant behavior (dissolution at high DNA concentration) is only shown for dsTRS, not for dsNS or ssTRS. The claim of specificity is based on a single non-specific sequence; a single NS sequence may not be representative. The authors also do not quantify the saturation concentration or critical concentration for LLPS, which would strengthen the comparison.
  - **Why it matters** The LLPS data are presented as a functional consequence of TRS binding specificity. Without systematic variation of conditions and multiple NS controls, the conclusion that TRS specifically promotes LLPS is premature.
  - **Resolution test** Perform LLPS assays with multiple NS sequences of similar length and GC content. Measure the saturation concentration for N-NTD-SR with dsTRS, ssTRS, and dsNS. Vary salt and protein concentration to map the phase boundary. Include a control with a mutant N-NTD-SR lacking the SR motif to confirm its role.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of DNA as a model for RNA
  - **Claim pointer** The authors use DNA as a proxy for RNA, stating that "the use of DNA is supported by the chemical shift profiles observed for dsDNA (either TRS or NS), which are largely similar to those obtained with dsRNA."
  - **Evidence pointer** Results section "N-NTD and N-NTD-SR melt double-stranded DNA", Figure 1, Figure S2
  - **Concern** The authors justify the use of DNA by citing similarity of CSPs to RNA, but no direct comparison data are shown in the manuscript. The melting activity is only demonstrated for DNA, not RNA. The LLPS experiments use DNA only. The conclusions about TRS recognition and melting are framed in the context of viral RNA transcription, but the key experiments are performed with DNA. The structural differences between DNA and RNA (e.g., A-form vs B-form helix, 2'-OH) could affect binding and melting.
  - **Why it matters** The biological relevance of the findings depends on the assumption that DNA mimics RNA. Without direct RNA experiments, the translational value of the conclusions is limited.
  - **Resolution test** Repeat key experiments (melting, LLPS, and at least one binding titration) with the corresponding RNA sequences. If RNA experiments are not feasible, explicitly state this limitation and temper the conclusions accordingly.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of quantitative data
  - **Affected element** Results section "N-NTD and N-NTD-SR bind tighter to ssTRS(–) than ssTRS(+)"
  - **Evidence pointer** Table S7
  - **Issue** The text states that "The affinities for are higher than those for , and ssTRSs display greater affinities than those observed for ssNSs," but the actual Kd values are not reported in the main text. The reader is forced to consult the supplementary table.
  - **Required correction** Report the mean Kd values with standard deviations in the main text for at least the key comparisons (ssTRS(–) vs ssTRS(+), dsTRS vs dsNS).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results section "N-NTD-SR phase separation is triggered by the SR motif and modulated by TRS binding"
  - **Evidence pointer** Figure 7E
  - **Issue** The turbidity data are presented as mean values, but error bars and the number of replicates are not described in the figure legend or text.
  - **Required correction** Add error bars and state the number of independent experiments in the figure legend.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** Methods section "Computation simulations"
  - **Evidence pointer** Methods, "Computation simulations"
  - **Issue** The description of the MD simulations lacks details on the equilibration protocol, the number of replicas, and the criteria for convergence.
  - **Required correction** Provide a more detailed description of the MD protocol, including the number of replicas, equilibration time, and convergence criteria.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation of LLPS data
  - **Affected element** Results section "N-NTD-SR phase separation is triggered by the SR motif and modulated by TRS binding"
  - **Evidence pointer** Figure 7D
  - **Issue** The DAPI staining is used to confirm DNA in condensates, but the authors do not discuss whether DAPI itself could affect LLPS.
  - **Required correction** Add a control showing that DAPI alone does not induce or inhibit LLPS.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion, first paragraph
  - **Issue** The discussion of LLPS in viral systems is brief and does not cite recent work on other viral nucleocapsid proteins that undergo phase separation.
  - **Required correction** Expand the discussion to include relevant literature on LLPS in other viruses (e.g., measles, rabies) and compare the findings.
- **Technical failings that need to be addressed before the case is established** 1) Lack of direct thermodynamic measurements (ITC) to validate van't Hoff-derived parameters. 2) Absence of structural model validation metrics. 3) Insufficient controls and quantitative analysis in LLPS experiments. 4) No direct RNA experiments to support the DNA-to-RNA extrapolation.
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The application of biophysical methods to N-NTD-DNA interactions is not entirely novel, but the combination of melting, LLPS, and structural modeling in a single study provides some new insights.  
  *Scientific importance*: Moderate to high. Understanding N protein function is relevant to SARS-CoV-2 biology and therapeutic development, but the use of DNA rather than RNA limits the direct biological impact.  
  *Interdisciplinary readership*: Moderate. The study will appeal to biophysicists and structural biologists, but the virological implications are not developed enough to attract a broad audience.  
  *Technical soundness*: The methods are generally appropriate, but the lack of validation and statistical rigor in key areas (thermodynamics, models, LLPS) undermines confidence.  
  *Readability for nonspecialists*: The manuscript is dense and assumes familiarity with NMR, MD, and LLPS concepts. The abstract is accessible, but the results and discussion require specialized knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially interesting, but the current evidence does not fully establish the claims of sequence specificity and the mechanistic link between energetics and melting. Addressing the major concerns, particularly with direct thermodynamic measurements, model validation, and RNA controls, would substantially strengthen the manuscript.

## Risk / unsupported claims
- The claim of a "well-defined pattern" for thermodynamic profiles is unsupported without statistical analysis and direct calorimetric validation.
- The structural models are presented as "based on experimental NMR data" but no validation is shown; the models should be considered preliminary.
- The assertion that DNA binding is a valid proxy for RNA is not directly supported by comparative data in this manuscript.
- The claim that "the preference for TRS over NS DNAs in the formation of liquid condensates" indicates sequence specificity is based on a single NS sequence and limited conditions.
- The suggestion that E174 acts as a "trigger for duplex destabilization" is speculative and not directly tested by mutagenesis in this study.