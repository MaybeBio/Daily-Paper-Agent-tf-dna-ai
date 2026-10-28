## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure/table references
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report a crystal structure of the human Capicua HMG-box-C1 module bound to a DNA oligonucleotide containing the consensus TGAATGAA site, propose a bipartite DNA recognition mechanism, and use MD simulations and binding assays to probe the effects of cancer-associated and interface mutations on DNA binding
- **Visible evidence base** Crystal structure at 2.95 Å resolution, MST binding data, EMSA data, MD simulations, CD spectroscopy, DLS, western blotting
- **Missing materials affecting confidence** Coordinates and structure factors (PDB deposition not confirmed), raw MST traces, raw EMSA gel images, MD trajectory details, full statistical analysis of binding parameters, supplementary figures and tables referenced but not provided

## Reviewer
- **Overall assessment** This manuscript presents a structurally and biochemically informative study of the bipartite DNA recognition mechanism used by the Capicua HMG-box-C1 module. The crystal structure is a valuable contribution, revealing an unexpected HTH fold for the C1 domain and a cooperative binding mode with the HMG-box. The combination of structural, computational, and biochemical approaches is appropriate and generally well executed. However, several technical concerns, particularly regarding the interpretation of mutation effects, the discrepancy between EMSA and MST results, and the limited scope of the MD simulations, need to be addressed before the central claims are fully established.
- **Who would be interested in the results, and why** Researchers studying HMG-box proteins, transcriptional repressors, DNA recognition mechanisms, and cancer-associated mutations in transcriptional regulators. The structural insight into how an HMG-box and an HTH domain cooperate to recognize a specific DNA sequence will be of interest to the broader gene regulation and structural biology communities.
- **Major strengths** The crystal structure is a novel and significant contribution, revealing the first structure of a CIC DNA-binding module and demonstrating an unexpected HTH fold for the C1 domain. The study directly addresses a long-standing question about how the two domains cooperate. The combination of structural, computational, and biochemical methods provides a multi-pronged approach. The analysis of cancer-associated mutations is clinically relevant.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (mutation interpretation), R1-M2 (EMSA-MST discrepancy), R1-M3 (MD simulation scope)
- **Assessment against Nature-style criteria** Originality: High. The structure is novel and reveals an unexpected mechanism. Scientific importance: High for the gene regulation and cancer fields. Interdisciplinary readership: Moderate. The study will appeal to structural biologists, biochemists, and cancer researchers. Technical soundness: Generally sound, but with concerns about mutation interpretation and assay discrepancies. Readability for nonspecialists: Good. The manuscript is clearly written and the figures are well described.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of mutation effects
- **Claim pointer** The manuscript claims that cancer-associated mutations R201W and R215W affect DNA binding, and that the observed effects explain their pathogenic mechanism.
- **Evidence pointer** Figure 6, Table 2, Figure S7, Figure S8
- **Concern** The interpretation of the R201W and R215W mutation effects is not fully supported by the data presented. For R201W, the EMSA shows increased binding, while the MST shows slightly stronger binding with negative cooperativity. For R215W, the EMSA shows dramatically decreased binding, but the MST shows slightly stronger binding. These contradictory results between assays are not adequately explained. The authors suggest that R215W affects binding kinetics, but no kinetic data are provided. Furthermore, the claim that R201W and R215W "disrupt CIC activity" is based on prior cellular studies, but the connection between the in vitro binding data presented here and the in vivo effects is not established.
- **Why it matters** The manuscript's central claim is that the structure and binding data provide insights into the effects of cancer mutations. If the binding data are contradictory or not clearly linked to the pathogenic mechanism, this claim is weakened.
- **Resolution test** The authors should provide a more detailed explanation for the discrepancy between EMSA and MST results, possibly by performing additional experiments such as surface plasmon resonance or fluorescence anisotropy to obtain kinetic and equilibrium binding parameters. They should also discuss the limitations of the minimal constructs used and how the in vitro data relate to the full-length protein in a cellular context.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Assay discrepancy and data interpretation
- **Claim pointer** The manuscript claims that CICmin18 binds the ETV5 promoter with nM affinity and that the R215W mutation dramatically decreases DNA binding.
- **Evidence pointer** Figure 6, Table 2, Figure S7
- **Concern** The discrepancy between the EMSA and MST results for the R215W mutation is a major concern. The EMSA shows a dramatic decrease in binding, while the MST shows slightly stronger binding. The authors suggest that this is due to differences in binding kinetics, but this is speculative. The MST data for R215W are also potentially confounded by protein aggregation, which the authors note was a problem in initial experiments. The claim that R215W dramatically decreases DNA binding is based on the EMSA data, but the MST data contradict this. This inconsistency needs to be resolved.
- **Why it matters** The manuscript's conclusions about the effects of cancer mutations on DNA binding are directly based on these assays. If the assays give contradictory results, the conclusions are not robust.
- **Resolution test** The authors should perform additional binding assays, such as fluorescence polarization or isothermal titration calorimetry, to obtain a consistent measure of binding affinity. They should also investigate the potential for protein aggregation in the MST experiments more thoroughly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** MD simulation scope and interpretation
- **Claim pointer** The manuscript claims that MD simulations show the C1 domain maintains its position in the major groove and that the HMG-box-C1 interface is stable.
- **Evidence pointer** Figure 3, Figure S3
- **Concern** The MD simulations are limited to three 250 ns trajectories, which may not be sufficient to capture the full conformational dynamics of the complex. The simulations were started from the crystal structure, which may bias the results. The analysis focuses on RMSF and RMSD, but does not provide a detailed analysis of the interactions between the HMG-box and C1 domains or between the protein and DNA. The claim that the interface is "stable" is not well supported by the data presented.
- **Why it matters** The MD simulations are used to support the claim that the bipartite binding mode is stable and that the interface is important. If the simulations are not robust or the analysis is incomplete, this claim is weakened.
- **Resolution test** The authors should provide a more detailed analysis of the MD trajectories, including interaction energies, hydrogen bonding occupancy, and principal component analysis. They should also consider running longer simulations or multiple replicates to ensure convergence.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Results and Discussion, "DNA specificity of CICmin18 is driven by an unpredicted DNA binding mode for a HTH domain"
- **Evidence pointer** Location not provided
- **Issue** The section title is somewhat misleading. The authors show that the C1 domain binds the major groove, but they do not demonstrate that this is an "unpredicted" mode for an HTH domain. In fact, HTH domains are well known to bind the major groove.
- **Required correction** Revise the title to be more accurate, such as "DNA specificity of CICmin18 is enhanced by a non-canonical HTH domain binding mode."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Table 2
- **Evidence pointer** Table 2
- **Issue** The Hill coefficients for the mutants are reported, but the errors on these values are not provided. It is unclear if the differences in Hill coefficients are statistically significant.
- **Required correction** Provide standard errors or confidence intervals for the Hill coefficients and EC50 values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Results and Discussion, "Interrogating cancer mutations within the CIC DNA-binding domains"
- **Evidence pointer** Location not provided
- **Issue** The authors note that the R215W protein aggregated when expressed in the CICmin18 construct, but they do not discuss the potential implications of this for the interpretation of the MST data.
- **Required correction** Add a sentence discussing the potential for aggregation to affect the MST results and how this was addressed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Methods, "Microscale thermophoresis (MST)"
- **Evidence pointer** Location not provided
- **Issue** The MST methods do not specify the concentration of the labeled DNA used or the range of protein concentrations tested. This information is necessary for the reader to assess the quality of the binding data.
- **Required correction** Add the DNA concentration and protein concentration range to the methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 6
- **Evidence pointer** Figure 6
- **Issue** The EMSA gels are not shown in the provided text. It is difficult to assess the quality of the data without seeing the gels.
- **Required correction** Ensure that the EMSA gels are shown in the final figure with appropriate labels and that the quantification is clearly described.

## Risk / unsupported claims
- The claim that the C1 domain "adds specificity by destabilizing certain DNA sequences within the bent DNA binding mode" is speculative and not directly tested.
- The claim that the structural similarity between the C1 and FF domains "might implicate C1 in recognizing a phosphopeptide" is speculative and not supported by any experimental data.
- The claim that the observed effects of mutations on binding in minimal constructs "may guide future bioengineering of related DNA-binding constructs" is not supported by any bioengineering experiments.
- The claim that the structure "may facilitate the development of strategies to interfere with CIC-DUX activity" is speculative and not supported by any functional data.