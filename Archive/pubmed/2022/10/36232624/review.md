## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Structural modeling and molecular dynamics simulation study of PRMT5 phosphorylation effects on histone H4 binding
- **Shared manuscript claim summary** The authors constructed atomic-level models of human PRMT5-MEP50 in complex with full-length histone H4, both unmodified and T80-phosphorylated, using in situ fragment-based assembly and molecular dynamics simulations. They claim to provide structural explanations for (1) increased methyltransferase activity of phosphorylated PRMT5 and (2) the inability of PRMT5 to methylate nucleosome-bound histone H4.
- **Visible evidence base** Abstract, Introduction, Results and Discussion sections 2.1-2.3, Materials and Methods sections 3.1-3.6, Conclusions, Acknowledgments. Figures referenced but not provided. Supplementary materials referenced but not provided.
- **Missing materials affecting confidence** Figures 1-6 and Supplementary Figures S1-S5, Tables S1-S3, and all structural coordinates/trajectories are not available for direct inspection. This limits verification of structural claims and interaction analyses.

## Reviewer
- **Overall assessment** This manuscript presents a computational modeling study aimed at explaining experimentally observed differences in PRMT5 activity upon T80 phosphorylation. The work addresses a relevant question in epigenetic regulation and cancer biology. However, the study is entirely computational, and the central claims rest on a single modeled complex built by fragment assembly, with no experimental validation. The evidence provided is insufficient to establish the mechanistic conclusions as presented. The manuscript would benefit from clearer presentation of validation steps, convergence analyses, and a more cautious interpretation of the results given the inherent limitations of the modeling approach.

- **Who would be interested in the results, and why** Researchers in the fields of epigenetics, protein arginine methylation, structural biology, and computational drug design would be interested. The proposed structural model of the PRMT5-H4 complex could inform inhibitor design efforts targeting PRMT5, which is a validated oncology target. The study also addresses a general question about how post-translational modifications of enzymes can modulate substrate binding and catalytic activity.

- **Major strengths** The study addresses a biologically and clinically relevant question with potential therapeutic implications. The authors identify a genuine gap in the structural literature, as no full-length H4-PRMT5 complex structure exists. The computational approach is reasonable as a first step, and the authors acknowledge the absence of experimental structures. The connection between the modeled T80 phosphorylation effects and previously published experimental activity data provides a useful framework for hypothesis generation.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that their modeled complex provides "an atomic level explanation" for the increased methyltransferase activity of phosphorylated PRMT5 and for the inactivity of PRMT5 on nucleosome-bound H4.
  - **Evidence pointer** Sections 2.1-2.3, Figures 2-6, Tables S2-S3
  - **Concern** The central mechanistic conclusions are derived from a single modeled complex built by in situ fragment assembly. The manuscript does not provide sufficient evidence that the assembled full-length H4 structure is reliable. No validation against experimental data (e.g., cross-linking, mutagenesis, or known binding affinities) is presented. The interaction energy differences between the unmodified and phosphorylated complexes are small relative to the expected error of the computational method, and no error estimates or replicate simulations are shown. The claim of "atomic level explanation" is therefore overstated.
  - **Why it matters** The conclusions rest entirely on the accuracy of the modeled complex. If the assembled H4 structure is incorrect, all downstream analyses and mechanistic interpretations are invalid. The lack of validation undermines confidence in the central claims.
  - **Resolution test** The authors should provide validation of the modeled complex, such as comparison with known experimental constraints, convergence analysis of the MD simulations, replicate simulations with different initial velocities, and a quantitative assessment of the uncertainty in the interaction energy calculations. Alternatively, the claims should be substantially softened to reflect the hypothesis-generating nature of the study.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "the phosphorylation of T80 resulted in a favourable Einter, lowering the activation energy barrier" and that this explains increased enzymatic activity.
  - **Evidence pointer** Section 2.3, Figure 2B, Table S2
  - **Concern** The manuscript equates a lower interaction energy (Einter) between enzyme and substrate with a lower activation energy barrier for catalysis. This is a conceptual leap. Einter is a ground-state binding energy, not a transition state energy. A more favorable ground-state binding can actually increase the activation barrier if the transition state is not stabilized to the same degree. The authors do not compute or estimate transition state energies, nor do they provide any kinetic or thermodynamic framework to support this interpretation.
  - **Why it matters** The central mechanistic claim about increased activity is not supported by the type of calculation performed. The interpretation conflates binding affinity with catalytic rate enhancement, which is a fundamental error in enzymology.
  - **Resolution test** The authors should either (a) provide a clear theoretical framework connecting Einter to activation barriers, (b) perform calculations that directly address the catalytic step (e.g., QM/MM calculations of the methyl transfer transition state), or (c) substantially revise the interpretation to state that the phosphorylation affects substrate binding, not necessarily catalysis.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The authors claim their model explains why PRMT5 cannot methylate nucleosome-bound H4, specifically through the competition between PRMT5 pT80 and nucleosomal DNA for H4 residue R45.
  - **Evidence pointer** Section 2.3, Figure 6, Table S3
  - **Concern** The argument that R45-DNA interactions in the nucleosome prevent PRMT5 binding is based on a static comparison of two different structures (the modeled PRMT5 complex and the nucleosome structure). The authors do not demonstrate that R45 is actually required for PRMT5 binding in their model, nor do they account for the possibility that other H4 residues could compensate. The claim that this "explains" the experimental observation is not supported by any direct test, such as a simulation of PRMT5 binding to a nucleosome substrate or mutagenesis analysis.
  - **Why it matters** This is presented as a key finding of the study, but it is a speculative inference from indirect evidence. Without direct testing, the claim remains a hypothesis.
  - **Resolution test** The authors should either perform simulations of PRMT5 with a nucleosome substrate, provide experimental validation (e.g., mutagenesis of R45 and binding assays), or clearly label this as a hypothesis requiring experimental testing.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The authors describe their simulation protocol in Section 3.3, including force field, water model, and simulation lengths.
  - **Evidence pointer** Section 3.3
  - **Concern** The manuscript does not report key simulation parameters that are essential for reproducibility, including the specific version of GROMACS, the barostat and thermostat parameters beyond the algorithm names, the integration time step, the equilibration protocol details, and the number of replicate simulations. The convergence of the simulations is not demonstrated with block averaging or other standard analyses. The selection of the "plateau" regions P1 and P2 appears subjective and is not justified with quantitative criteria.
  - **Why it matters** Reproducibility is a core requirement for computational studies. Without these details, other researchers cannot replicate the simulations or assess the robustness of the results.
  - **Resolution test** The authors should provide complete simulation parameters, including software versions, all coupling parameters, time steps, equilibration steps, and a quantitative definition of the plateau regions. They should also provide evidence of convergence, such as block-averaged energy or structural properties.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.1, Figure 2B
  - **Evidence pointer** Section 2.1
  - **Issue** The description of the T1 and T2 transient regions and the P1 and P2 plateau regions is unclear. The criteria for distinguishing these regions are not stated, and the assignment of T1 as a "technical equilibrating region" is not justified.
  - **Required correction** Provide a clear definition of the transient and plateau regions, including the time windows and the quantitative criteria used to identify them.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 2.1, Figure 3
  - **Evidence pointer** Section 2.1
  - **Issue** The statement that "MEP50 does not play a direct role in histone binding" is presented as a finding, but the evidence is only referenced as "S4" (presumably a supplementary figure or table). The main text does not describe the analysis that supports this conclusion.
  - **Required correction** Summarize the evidence for this claim in the main text, or move the claim to the supplementary material with a clear reference.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.3, Figure 6
  - **Evidence pointer** Section 2.3
  - **Issue** The comparison between the PRMT5-H4 interaction and the nucleosomal H4-DNA interaction is described qualitatively. The figure is not available for inspection, and the text does not provide quantitative details of the interaction energies or distances involved.
  - **Required correction** Provide quantitative data for the interactions described, such as interaction energies or hydrogen bond distances, to support the comparison.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Language
  - **Affected element** Throughout
  - **Evidence pointer** Location not provided
  - **Issue** The manuscript contains several instances of awkward phrasing and grammatical errors that impede readability. Examples include "the phosphorylation of PRMT5 on T80 residue increases its methyltransferase activity" and "the PRMT5 methylates only the free form of histone H4 not bound in the nucleosome."
  - **Required correction** The manuscript should be carefully edited for grammar and clarity by a native English speaker.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 3.1
  - **Evidence pointer** Section 3.1
  - **Issue** The description of the fragment-based construction of H4 is brief. The authors state that "after several attempts of superimposing of the abovementioned fragments to the resolved H4-PRMT5 complex, only the backbone alignment... resulted a complex without collision." This suggests a trial-and-error process, but the details of the attempts and the criteria for "without collision" are not provided.
  - **Required correction** Provide more detail on the assembly process, including the specific residues used for alignment and the criteria used to assess collisions.

## Risk / unsupported claims
- The claim that the modeled complex provides an "atomic level explanation" for increased enzymatic activity is unsupported, as the calculations do not address the catalytic transition state.
- The claim that competition between PRMT5 pT80 and nucleosomal DNA for H4 R45 explains the lack of methylation of nucleosome-bound H4 is speculative and not directly tested.
- The interpretation of Einter differences as reflecting activation energy differences is not justified.
- The conclusion that MEP50 does not play a direct role in histone binding is not adequately supported in the main text.
- The overall reliability of the modeled full-length H4 structure is not established, as no validation against experimental data is provided.
- The convergence and statistical robustness of the MD simulations are not demonstrated.