## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and references to supporting material
- **Assessment boundary** Scientific content, methodological rigor, validity of conclusions, and presentation quality as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors use equilibrium molecular dynamics (MD) simulations and umbrella sampling (US) with replica exchange (REUS) to characterize the DNA gate opening mechanism of M. smegmatis topoisomerase 1A (Msm Top1A). They identify electrostatic interactions stabilizing the closed state, describe three major domain motions during gate opening including a D3 swivel, and reconstruct free energy profiles for gate opening in apo and ssDNA-bound systems.
- **Visible evidence base** Main text figures referenced as Figures 1 through 8, supplementary figures S1 through S15, Table S1, Notes S1 and S2, and supporting videos S1 through S3
- **Missing materials affecting confidence** The supporting material (Document S1, Document S2, Figures S1-S15, Table S1, Notes S1 and S2, Videos S1-S3) was not provided for review. Simulation parameter details, force field validation, convergence criteria, and specific numerical values for free energy barriers are referenced but not fully detailed in the main text.

## Reviewer
- **Overall assessment** This manuscript presents a computational study of the DNA gate opening mechanism in Msm Top1A using atomistic MD simulations with enhanced sampling techniques. The work addresses a genuinely challenging and biologically important question, namely the transient open state of type 1A topoisomerases that has been difficult to capture experimentally. The authors combine equilibrium simulations, umbrella sampling, and principal component analysis to propose a multi-step gate opening mechanism involving D1 displacement, D3-D4 separation, and D3 swiveling. The study is potentially valuable for understanding topoisomerase catalysis and for antibacterial drug design. However, the manuscript as presented has several significant limitations that prevent full assessment of the claims. The supporting material, which contains critical details on convergence, free energy calculations, and PCA results, was not available for review. The authors acknowledge lack of full convergence in their simulations, which substantially weakens the quantitative free energy claims. The choice of reaction coordinate and its validation are not thoroughly discussed. The relationship between the simulated open state and experimentally observed open conformations requires more careful consideration. The manuscript would benefit from clearer presentation of methodological details and more cautious interpretation of the free energy results.

- **Who would be interested in the results, and why** Researchers in the fields of DNA topology, topoisomerase enzymology, and computational biophysics would find this work relevant. The study provides mechanistic hypotheses about gate opening that could inform experimental mutagenesis studies and single-molecule experiments. The identification of specific electrostatic interactions stabilizing the closed state may be of interest to those studying topoisomerase inhibitors, particularly in the context of mycobacterial infections where Top1A is a validated drug target. The methodological approach combining US and REUS with PCA could also be of interest to computational biologists studying large-scale conformational changes in other protein systems.

- **Major strengths**
  1. The study addresses a biologically important and technically challenging question, namely the transient open state of type 1A topoisomerases, which has been difficult to characterize experimentally.
  2. The combination of equilibrium MD, umbrella sampling, REUS, and PCA provides a multi-faceted computational approach to probe the gate opening mechanism.
  3. The identification of specific electrostatic interactions across the gate interface and their conservation analysis adds mechanistic detail that could guide experimental validation.
  4. The authors acknowledge limitations in convergence and discuss potential improvements, showing scientific honesty.
  5. The work connects to prior experimental observations, including single-molecule force spectroscopy and recent cryo-EM structures, providing context for the computational findings.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have reconstructed free energy profiles of gate opening for all simulations using umbrella sampling combined with WHAM, and that REUS resulted in lower free energy barriers and better convergence.
- **Evidence pointer** Results section "Free energy curves show variability in the gate opening process", Figures 6B, S9-S11
- **Concern** The authors explicitly state that "longer simulations than those conducted for this study may be needed to ensure that convergence has been fully achieved" and that "we were unable to see complete convergence even with increasing simulation time." This admission fundamentally undermines the quantitative free energy claims presented in Figure 6B. The free energy barriers and profiles cannot be considered reliable if convergence was not achieved. The authors present these profiles as results without clearly demarcating which aspects are converged and which are not. The lack of convergence also affects the claim that REUS improved convergence, as the evidence for this improvement is not quantitatively demonstrated in the main text.
- **Why it matters** Free energy profiles are central to the manuscript's claims about the relative stability of closed versus open states and the barriers to gate opening. If these profiles are not converged, the quantitative conclusions about the energetics of gate opening are not supported. This affects the core scientific contribution of the work.
- **Resolution test** The authors should provide quantitative convergence metrics (e.g., block error analysis, multiple independent REUS runs with different initial conditions, comparison of free energy profiles from different simulation lengths) demonstrating that the reported free energy profiles are converged. Alternatively, the claims should be substantially softened to reflect the preliminary nature of the energetic results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that gate opening comprises three major domain motions identified from US simulations and PCA: detachment and downward motion of D1 away from D3, detachment of D3 from the D1+D4 interface, and swiveling of D3 out of the plane of the protein.
- **Evidence pointer** Results section "Gate opening involves swivel of D3", Figure 7, Table S1, Notes S1 and S2
- **Concern** The PCA results are stated to be affected by the US bias, yet the authors use these results to identify "functional motions" of the protein. The manuscript does not adequately address how the applied biasing potential along the chosen reaction coordinate influences the PCA modes. The claim that the three components describe "most of the fluctuations of the system (>85%)" is presented without the supporting data (Figure S15, Note S1) being available for review. The overlap between components across simulations is mentioned but the quantitative measure of this overlap is not provided in the main text. The distinction between motions that are intrinsic to the protein versus those induced by the biasing protocol is not clearly established.
- **Why it matters** The identification of the three domain motions is a central mechanistic claim of the paper. If these motions are artifacts of the biasing protocol rather than intrinsic features of the protein's conformational landscape, the mechanistic conclusions would be invalid. The manuscript does not provide sufficient evidence to distinguish these possibilities.
- **Resolution test** The authors should provide a more rigorous analysis separating the effects of the biasing potential from intrinsic protein dynamics. This could include unbiased MD simulations initiated from the open state, comparison of PCA modes from unbiased and biased simulations, or validation of the identified motions against experimental structures or other computational studies.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and methodological completeness
- **Claim pointer** The authors claim to have conducted equilibrium MD simulations, US simulations, and REUS simulations for both apo and ssDNA-bound systems, with specific simulation lengths and replica numbers.
- **Evidence pointer** Materials and methods section, Results section
- **Concern** The manuscript lacks sufficient methodological detail to assess the adequacy of sampling. The number of US windows, the total simulation time per window, the number of replicas for equilibrium simulations, and the specific parameters for REUS exchange attempts are not clearly stated in the main text. The statement that "each window was sampled for at least 2, 4, or 10 ns in all simulations" is vague and does not specify which windows used which durations. The criteria for selecting the reaction coordinate and the validation of this choice are not thoroughly described. The equilibration protocol is described but the criteria for determining when systems were equilibrated are not provided beyond RMSD stabilization.
- **Why it matters** Reproducibility is a fundamental requirement for computational studies. Without clear specification of simulation parameters, other researchers cannot replicate or build upon this work. The adequacy of sampling directly affects the reliability of all reported results, including free energy profiles and identified motions.
- **Resolution test** The authors should provide a complete description of all simulation parameters, including the number of windows, simulation times per window, replica counts, exchange rates for REUS, and the specific criteria used to determine equilibration. This information should be in the main text or clearly referenced in the supporting material.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance and interpretation
- **Claim pointer** The authors claim that the identified electrostatic interactions across the gate interface contribute to closed-state stability and that their findings have implications for understanding the topoisomerase catalytic cycle and for drug design.
- **Evidence pointer** Results section "Stability of the gate-closed conformation", Figures 4-5, Discussion
- **Concern** The manuscript identifies several electrostatic interactions that stabilize the closed state, but the functional significance of these interactions is not experimentally validated or compared against known mutational data. The authors suggest that mutagenesis studies targeting these residues would provide insights, but do not discuss whether any existing experimental data on homologous residues in other topoisomerases support or contradict their findings. The connection between the simulated open state and the experimentally observed open conformation in the recent cryo-EM structure of Hs Top3β is mentioned but not analyzed in detail. The authors do not discuss whether the open state they observe is consistent with the experimentally determined open conformation in terms of domain positions and gate dimensions.
- **Why it matters** The biological significance of the computational findings depends on their connection to experimental observations. Without validation against existing experimental data or clear predictions that can be experimentally tested, the claims about the catalytic cycle and drug design remain speculative.
- **Resolution test** The authors should compare their simulated open state with the experimentally determined open conformation of Hs Top3β or other available structures, discussing similarities and differences in domain positions. They should also discuss any existing mutational or biochemical data on the identified gate interface residues and how their findings relate to those data.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Presentation and clarity
- **Affected element** Figure 1 description
- **Evidence pointer** Figure 1 and its caption
- **Issue** The figure caption describes the structure and features of Msm Top1A but the description of the unstructured loop and its position relative to the gate interface is somewhat unclear. The relationship between the "front face" and "back face" of the protein and how these relate to the gate opening direction could be more clearly explained.
- **Required correction** Clarify the description of the unstructured loop position and the definition of front and back faces in the figure caption or in the main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Reaction coordinate definition
- **Evidence pointer** Materials and methods, Figure 6A
- **Issue** The reaction coordinate is defined as the distance between the centers of mass of two protein regions, but the rationale for choosing this particular coordinate and its relationship to the experimentally measured gate opening distance (>5 nm) is not clearly explained.
- **Required correction** Provide additional justification for the choice of reaction coordinate and discuss how the range of RC values sampled relates to the experimentally observed gate opening distances.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of alternative pathways
- **Evidence pointer** Results section "Free energy curves show variability in the gate opening process"
- **Issue** The authors state that the protein can open through multiple pathways but do not clearly define what constitutes a distinct pathway or how the pathways differ beyond the free energy profiles. The relationship between the observed variability and the lack of convergence is not fully addressed.
- **Required correction** Clarify the definition of distinct pathways and discuss whether the observed variability reflects genuine multi-pathway behavior or insufficient sampling.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Comparison with experimental data
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript mentions single-molecule experiments that observed gate opening under applied force, but does not discuss how the simulation results compare with the force-dependent kinetics or the measured opening distances from these experiments.
- **Required correction** Add a discussion comparing the simulation results with available single-molecule experimental data, including any quantitative comparisons of opening distances or barriers where possible.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "several electrostatic interactions contribute to the closed-state stability" and that gate opening "composed of three major domain motions" but does not provide any quantitative information about the free energy barriers or the magnitude of the motions.
- **Required correction** Consider including key quantitative findings in the abstract, such as approximate free energy barriers or the extent of domain motions, to better convey the significance of the results.

## Risk / unsupported claims
- The quantitative free energy profiles and barrier heights are not fully supported due to acknowledged lack of convergence in the simulations.
- The claim that the three PCA-identified motions represent the major functional motions of gate opening is not fully supported because the PCA results are affected by the US bias and the supporting data were not available for review.
- The claim that the identified electrostatic interactions are important for closed-state stability is supported by simulation data but lacks experimental validation or comparison with existing mutational data.
- The statement that the unstructured loop has a regulatory role during supercoil relaxation is based on prior work and is presented as context, but the current simulations do not directly test this hypothesis.
- The suggestion that the findings will aid in antitopoisomerase drug design efforts is speculative and not directly supported by the data presented.
- The claim that the open state observed in simulations is consistent with the cryo-EM structure of Hs Top3β is mentioned but not analyzed in sufficient detail to be evaluated.
- The assertion that the protein can follow multiple pathways to gate opening is plausible but not definitively established given the acknowledged convergence issues.