## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, conclusions)
- **Assessment boundary** Computational study of allosteric effectors targeting TEAD4-YAP1 interaction; includes docking, MD simulations, MM/GBSA, t-ICA, and MSM analyses
- **Shared manuscript claim summary** The authors report six experimentally identified ligands from a DNA-encoded library screen against the TEAD4 central palmitate-binding pocket. They computationally modified these ligands by replacing a secondary methyl amide with chloromethyl ketone, inspired by the TED-347 inhibitor. Using docking, 150 ns MD simulations, MM/GBSA, t-ICA, and MSM, they claim the modified ligands bind similarly to the original ligands, induce distinct conformational changes in TEAD4-YAP1, and that four modified ligands enhance TEAD4-YAP1 binding affinity more than their original counterparts. Key residues Phe229, Thr332, Ile374, and Ile395 are proposed as essential for effective binding.
- **Visible evidence base** Main text with 10 figures/tables referenced (Figures 1-10, Tables 1-2), supplementary figures referenced (Figures S1-S6, Table S1)
- **Missing materials affecting confidence** Supplementary figures and tables not provided; experimental screening data not provided (credited as unpublished); PDB structure details not independently verified; no raw simulation trajectories or convergence metrics beyond RMSD

## Reviewer

- **Overall assessment** This manuscript presents a computational investigation of allosteric modulators targeting the TEAD4-YAP1 interaction, a relevant cancer therapeutic target. The study combines several established computational methods to characterize ligand binding and its effects on protein dynamics. The work is technically competent in its application of MD simulations and downstream analyses, but several concerns limit the strength of the conclusions. The most significant issues are the lack of experimental validation for the computationally predicted effects, the absence of key methodological details regarding the experimental screen, and the limited sampling time relative to the claims about conformational space exploration. The claim that four modified ligands enhance TEAD4-YAP1 binding affinity is based on MM/GBSA calculations with small energy differences that may be within error. The identification of key residues is based on a subset of ligands and may not generalize. The manuscript would benefit from clearer presentation of the relationship between the experimental screen and the computational follow-up, as well as more rigorous statistical treatment of the energy calculations.

- **Who would be interested in the results, and why** Researchers in cancer biology and drug discovery, particularly those focused on the Hippo signaling pathway and TEAD transcription factors, would find this work relevant. Computational chemists and biophysicists interested in allosteric regulation and protein-ligand interactions may also be interested in the methodological approach combining MD, t-ICA, and MSM. The identification of specific residues involved in ligand binding could inform future medicinal chemistry efforts targeting TEAD4.

- **Major strengths**
  1. The study addresses a clinically relevant target (TEAD4-YAP1 interaction) with therapeutic implications for solid tumors.
  2. The combination of multiple computational methods (docking, MD, MM/GBSA, t-ICA, MSM) provides a comprehensive approach to studying ligand effects on protein dynamics.
  3. The chemical modification strategy based on the TED-347 inhibitor is rational and clearly motivated.
  4. The identification of specific residues (Phe229, Thr332, Ile374, Ile395) provides testable hypotheses for experimental validation.
  5. The use of three independent MD replicates for each system is appropriate for improving statistical reliability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Four of the six modified ligands were associated with enhanced allosteric communication between the TEAD4 and YAP1 domains indicated by the relative free energy perturbation to original molecules."
- **Evidence pointer** Section 2.4, Figure 9, Table S1
- **Concern** The claim that four modified ligands enhance TEAD4-YAP1 binding affinity is based on ΔΔG values calculated from MM/GBSA. The reported differences between original and modified ligands range from −3.29 to −14.31 kcal/mol for the favorable cases, but the error bars and statistical significance of these differences are not adequately discussed. MM/GBSA is known to have systematic errors and the differences may be within the method's uncertainty. Additionally, the text states that "all 12 ligands under study could stabilize the TEAD4-YAP1 complex" but Figure 9 shows positive ΔΔG values for Original 4 and 5, which would indicate destabilization, creating an internal inconsistency.
- **Why it matters** The central conclusion of the paper, that the chemical modification enhances the stabilizing effect on TEAD4-YAP1, rests on these energy calculations. If the differences are not statistically robust or the interpretation is inconsistent, the main claim is not supported.
- **Resolution test** Provide statistical analysis of the ΔΔG values across replicates, including confidence intervals. Clarify the sign convention and reconcile the statement that all ligands stabilize the complex with the positive ΔΔG values shown for some ligands. If possible, include error estimates from the MM/GBSA calculations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental grounding
- **Claim pointer** "Screening of a DNA-encoded library against the TEAD4 central pocket was performed experimentally to identify six new allosteric inhibitors."
- **Evidence pointer** Section 1 (Introduction), Section 4.1 (Materials and Methods)
- **Concern** The experimental screening that identified the six original ligands is described only as unpublished results. No experimental details are provided regarding the screen, the assay used, the potency of the identified compounds, or their binding affinity. The manuscript relies entirely on this unpublished work as the foundation for the computational study, but the reader cannot assess the quality or relevance of the starting compounds.
- **Why it matters** The computational study is built upon experimentally identified ligands, but without access to the experimental data, the significance of the computational findings cannot be properly evaluated. The compounds may have weak or nonspecific binding, which would affect the interpretation of the computational results.
- **Resolution test** Provide the experimental screening data as supplementary material or a supporting publication, including compound identities, binding affinities or potencies, and assay details. At minimum, include the chemical structures of the six original ligands.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor
- **Claim pointer** "The modified ligands affected the binding affinity between TEAD4 and YAP1 proteins to an extent exceeding the original molecules obtained from the experimental screening."
- **Evidence pointer** Section 2.4, Figure 9, Section 4.3
- **Concern** The ΔΔG values are calculated using MM/GBSA, which is acknowledged by the authors as less robust than free energy perturbation methods. The manuscript does not provide a convergence analysis of the MM/GBSA calculations, nor does it compare the results with an alternative method. The use of only three 50 ns replicates per system may be insufficient for converged free energy estimates, particularly for protein-protein interaction energies.
- **Why it matters** The quantitative claims about enhanced binding affinity depend on the reliability of the energy calculations. Without convergence analysis or cross-validation with another method, the numerical values may not be reliable.
- **Resolution test** Include convergence plots for the MM/GBSA calculations, extend simulation time or increase replicate number, and consider validating key findings with an alternative method such as umbrella sampling or metadynamics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive validity
- **Claim pointer** "Phe229, Thr332, Ile374, and Ile395 residues were revealed to be essential for the effective binding of the inhibitors."
- **Evidence pointer** Section 2.4, Figure 10, Figure S4
- **Concern** The claim that these four residues are "essential" is based on the observation that ligands with enhanced binding affinity form hydrogen bonds with all four residues, while ligands with less enhanced affinity do not. However, the analysis is based on a small number of ligands (six with enhanced affinity, six with less enhanced affinity), and the correlation between hydrogen bond formation and binding affinity is not statistically tested. The term "essential" implies a causal role that is not established by correlative observation.
- **Why it matters** If these residues are proposed as targets for future drug design, the evidence for their importance must be stronger than a qualitative correlation. Overstating the role of these residues could mislead future medicinal chemistry efforts.
- **Resolution test** Perform alanine scanning mutagenesis simulations or free energy decomposition to quantitatively assess the contribution of each residue to ligand binding. Provide statistical analysis of the correlation between hydrogen bond formation and binding affinity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Figure 3
- **Evidence pointer** Section 2.2
- **Issue** The text states that RMSD values "fluctuated between 1 and 3 Å for each of the experimentally identified and computationally modified ligands," but it is unclear whether this refers to the protein backbone, the ligand, or the protein-ligand complex. The figure is not available for inspection.
- **Required correction** Specify the atoms used for RMSD calculation and clarify whether the values refer to the protein, ligand, or complex.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.3.2, Figure 6
- **Evidence pointer** Section 2.3.2
- **Issue** The selection of eight macrostates for the ligand-bound systems and three macrostates for the apo system is described, but the criteria for choosing these numbers beyond the "apparent gap" in the implied time scale plot is not fully explained. The GMRQ scores are referenced but not shown in the main text.
- **Required correction** Provide a more detailed explanation of the model selection criteria and include the GMRQ score plots in the main text or supplementary material.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Section 2.4, Figure 9
- **Evidence pointer** Section 2.4
- **Issue** The text states that "all 12 ligands in this study" led to more favorable binding affinity between TEAD4 and YAP1, but Figure 9 reportedly shows positive ΔΔG values for Original 4 and 5, which would indicate less favorable binding. This appears contradictory.
- **Required correction** Clarify the sign convention for ΔΔG and reconcile the text with the figure. If positive ΔΔG values indicate destabilization, revise the statement about all ligands stabilizing the complex.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.2
- **Evidence pointer** Section 4.2
- **Issue** The simulation protocol states that 50 ns simulations were performed for each of three replicates, totaling 150 ns per system. However, the text in Section 2.2 refers to "all three 50 ns trajectories," which is consistent, but the total simulation time of 150 ns per system is relatively short for studying conformational changes in a protein-protein complex.
- **Required correction** Acknowledge the limitation of the simulation time scale and discuss whether the observed conformational changes are likely to be converged.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5
- **Issue** The section titled "Formatting of Mathematical Components" appears to be a methods section placed within the results. The equations are standard and correctly presented, but the placement is unusual.
- **Required correction** Consider moving this section to Materials and Methods or renumbering it as part of the methods description.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 1 (Introduction)
- **Evidence pointer** Section 1
- **Issue** The introduction cites references [1-25] but the reference list is not provided in the submitted material. The citation to unpublished results for the experimental screen is noted, but the lack of a reference list makes it difficult to assess the context of the work.
- **Required correction** Ensure the reference list is complete and accessible. Consider providing more detail on the unpublished experimental screen or making it available as a preprint.

## Risk / unsupported claims
- The claim that four modified ligands enhance TEAD4-YAP1 binding affinity is not fully supported due to lack of statistical analysis of MM/GBSA results and potential inconsistency in the reported ΔΔG values.
- The claim that Phe229, Thr332, Ile374, and Ile395 are "essential" for ligand binding is not supported by the evidence presented, which shows correlation rather than causation.
- The experimental identification of the six original ligands is based on unpublished data that is not accessible to the reader, making the foundation of the study unverifiable.
- The statement that "all 12 ligands under study could stabilize the TEAD4-YAP1 complex" appears inconsistent with the reported positive ΔΔG values for some ligands.
- The claim that the modified ligands "affected the binding affinity between TEAD4 and YAP1 proteins to an extent exceeding the original molecules" is based on MM/GBSA calculations that may not be sufficiently converged given the simulation time and number of replicates.
- The assertion that ligand binding "limits the conformational space explored by protein" is based on t-ICA and MSM analyses of relatively short simulations and may not reflect the full conformational landscape.
- The biological significance of the observed conformational changes is not experimentally validated, and the connection between computational predictions and functional outcomes remains speculative.