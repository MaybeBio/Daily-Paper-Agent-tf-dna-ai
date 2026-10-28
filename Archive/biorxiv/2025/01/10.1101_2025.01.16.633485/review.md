## Review setup
- **Input scope** Full manuscript text (abstract, introduction, theory, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, and claims as presented in the provided text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors use coarse-grained Molecular Dynamics simulations with metadynamics to compute 3D and 2D dimerization free energies for the BAR-domain protein LSP1, showing that membrane localization can dramatically alter the free energy landscape and that the rigid-body approximation for the lengthscale h fails when protein flexibility is considered, with enthalpic stabilization driving enhanced 2D binding for the MARTINI 3.0 parameterization.
- **Visible evidence base** Main text figures referenced (Figs 1-7), Table 1, and methods descriptions; supplementary figures and tables mentioned but not provided
- **Missing materials affecting confidence** Supplementary Information (SI) with extended derivations, Figures S1-S19, Tables S1-S4, and Movies S1-S6; full convergence data for metadynamics; experimental validation data

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in membrane protein biophysics: how does 2D confinement alter dimerization thermodynamics relative to 3D solution, and can rigid-body estimates capture this? The authors present a rigorous simulation study with a clear theoretical framework, and the finding that enthalpic effects can dominate over entropic rigid-body predictions is potentially significant. However, the manuscript has several issues that need to be addressed: the presentation of key equations is incomplete (equations appear truncated), the statistical analysis of the free energy differences needs more detail, and the generalizability claims require more careful qualification given the force-field dependence demonstrated. The work is original and likely to interest a broad readership, but the current form does not fully establish the case.
- **Who would be interested in the results, and why** Membrane biophysicists and computational biologists studying protein-protein interactions on surfaces; experimentalists working on BAR-domain proteins and membrane remodeling; theorists developing coarse-grained models of 2D binding. The h lengthscale concept is broadly applicable to any system where dimensional reduction matters, so the framework could be adopted by researchers studying receptor clustering, signaling complexes, and viral assembly on membranes.
- **Major strengths** 1) The theoretical framework connecting h to partition functions is clearly laid out and provides a useful generalization beyond rigid-body treatments. 2) The use of three distinct simulation environments (3D, 2D bilayer, 2D pseudo-membrane) is a clever design that isolates the effects of geometric restriction from explicit lipid interactions. 3) The comparison between two force fields (MARTINI 2.0 vs 3.0) provides insight into parameterization sensitivity, which is valuable for the community. 4) The analysis of configurational sampling and potential energies goes beyond simple free energy differences to provide mechanistic insight.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "both 2D environments induce backbone configurations that better match the crystal structure and produce more enthalpically favorable dimer states" and that this leads to h ≪ h_RIGID for LSP_M3.0.
  - **Evidence pointer** Figure 5, Figure 6, Table 1
  - **Concern** The statistical significance of the free energy differences between 3D and 2D environments is not adequately established. The authors mention block averaging and 95% confidence intervals, but the actual error bars on ΔG values in Table 1 are not shown in the provided text. Given that the differences between environments appear to be on the order of a few kJ/mol (based on the text mentioning "kJ/mol" offsets), it is critical to demonstrate that these differences exceed the statistical uncertainty. The authors state that KS tests confirm the distributions are different, but this does not directly address whether the mean ΔG values are significantly different. Please provide the error estimates for all ΔG values and demonstrate that the 3D vs 2D differences are statistically significant.
  - **Why it matters** The central claim of the paper is that 2D environments alter binding thermodynamics beyond rigid-body predictions. If the free energy differences are within statistical noise, the conclusions are not supported.
  - **Resolution test** Provide error bars on all ΔG values in Table 1, and perform a statistical test (e.g., bootstrap or t-test) comparing the 3D and 2D ΔG distributions for each system. Show that the differences are significant at p < 0.05.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "contact with an explicit lipid bilayer is not necessary to drive these changes, as the solvated pseudo membrane induces this same result."
  - **Evidence pointer** Figure 2, Table 1
  - **Concern** The pseudo-membrane simulations use harmonic restraints derived from the 2D bilayer simulations. This means the pseudo-membrane is not an independent test of the effect of geometric restriction; it is a parameterized approximation of the bilayer. The authors acknowledge this in the methods but do not discuss the circularity concern. If the restraints are derived from the bilayer simulations, then the similarity between 2D and 2D-Ps results is partly by construction. The authors should clarify what independent information the 2D-Ps simulations provide, or acknowledge this limitation more explicitly.
  - **Why it matters** The claim that explicit lipid contacts are not needed is important for the mechanistic interpretation. If the pseudo-membrane is not truly independent, this claim is weakened.
  - **Resolution test** Discuss the extent to which the pseudo-membrane restraints are derived from the bilayer simulations and what independent validation the 2D-Ps results provide. Consider testing the sensitivity of the results to the restraint parameters.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors state that "our approach provides simple metrics to move beyond rigid-body estimates of 2D affinities and assess whether conformational flexibility selects for enhanced stability on membranes."
  - **Evidence pointer** Discussion section
  - **Concern** The generalizability of the findings is not well established. The authors study a single protein (LSP1) with two force fields. The dramatic difference between MARTINI 2.0 and 3.0 results suggests that the conclusions are highly parameterization-dependent. The authors acknowledge this but do not provide guidance on how to determine which force field is more accurate for this system. Without experimental validation or a systematic comparison across multiple proteins, the claim that this approach provides "simple metrics" for general use is premature.
  - **Why it matters** The broader impact of the work depends on whether the framework can be applied to other systems. If the results are too sensitive to force-field choice, the practical utility is limited.
  - **Resolution test** Discuss the force-field dependence more thoroughly and suggest criteria for selecting appropriate force fields for such studies. If possible, compare to any available experimental data for LSP1 or related BAR domains.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "the most stable structure is very close to the crystal structure" for the 2D environments of LSP_M3.0.
  - **Evidence pointer** Figure 2, Figure 5
  - **Concern** The definition of "close to the crystal structure" is not quantified in the provided text. The RMSD values in Figure 5 appear to be around 0.3-0.4 nm for the 2D environments, which is reasonable but not extremely close. The authors should provide a quantitative threshold for what constitutes "close" and discuss whether the deviations are functionally significant. Additionally, the relationship between the most stable structure in the FES and the crystal structure should be clarified, as the FES minimum may not correspond exactly to the structure with lowest RMSD to the crystal.
  - **Why it matters** The claim that 2D environments select for the native structure is central to the mechanistic interpretation. Without clear quantification, this claim is difficult to evaluate.
  - **Resolution test** Provide quantitative RMSD values for the most stable structures in each environment, and discuss the structural differences between the 3D and 2D most stable states.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Theory section (Section II)
  - **Evidence pointer** Section II
  - **Issue** Several equations appear to be missing or truncated in the provided text. For example, the equations for K_D in 3D and 2D, and the definition of h, are referenced but not fully displayed. This makes it difficult to follow the theoretical development.
  - **Required correction** Ensure all equations are fully displayed and properly numbered. If the text was truncated in submission, provide the complete version.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods section (Section V.A)
  - **Evidence pointer** Section V.A
  - **Issue** The text mentions "improved MARTINI parameters" and references a paper (Ref 68) but does not specify which parameters were improved or how this affects the results. This is important for reproducibility.
  - **Required correction** Specify which parameters were modified and provide a brief justification for the changes.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Results section (Section III)
  - **Evidence pointer** Section III
  - **Issue** The text contains several instances of duplicated or garbled sentences (e.g., "The parameterization of the LSP_M2.2p dimer produces extraordinarily favorable potential energies of bound states and ultimately binding free energies ΔG that are not representative of The parameterization of the LSP_M2.2p dimer produces extraordinarily favorable potential"). This appears to be a copy-paste error.
  - **Required correction** Clean up the text to remove duplicated phrases and ensure clarity.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion section
  - **Evidence pointer** Section IV
  - **Issue** The discussion of experimental relevance is brief. The authors mention that "experiments find significant increases in oligomerization on membranes" but do not provide specific citations or quantitative comparisons. A more detailed comparison to experimental data would strengthen the paper.
  - **Required correction** Add specific experimental references and discuss how the simulation results compare quantitatively to experimental measurements where available.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods section (Section V.B)
  - **Evidence pointer** Section V.B
  - **Issue** The description of the block averaging procedure is incomplete. The text mentions "we evaluated the error by considering different block sizes (varying N) for each simulation as shown in Fig S5" but does not explain how the optimal block size was chosen or how the 95% CI was calculated in detail.
  - **Required correction** Provide a more detailed description of the block averaging procedure, including how block sizes were selected and how the confidence intervals were computed.

- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical significance of free energy differences), R1-M2 (independence of pseudo-membrane results), R1-M3 (generalizability given force-field dependence)
- **Assessment against Nature-style criteria** 
  - Originality: High. The application of the h lengthscale framework to flexible peripheral membrane proteins with explicit consideration of enthalpic effects is novel. Most prior work has focused on rigid-body treatments or bridging receptors.
  - Scientific importance: Moderate to high. Understanding how 2D confinement alters binding thermodynamics is relevant to many biological processes, and the finding that enthalpic effects can dominate is potentially important. However, the force-field dependence limits the immediate impact.
  - Interdisciplinary readership: Moderate. The work will appeal primarily to computational biophysicists and membrane biologists. The theoretical framework is accessible, but the heavy reliance on simulation details may limit broader appeal.
  - Technical soundness: The simulation methodology is generally sound, but the statistical analysis needs strengthening (R1-M1), and the pseudo-membrane approach has a circularity concern (R1-M2). The force-field comparison is valuable but raises questions about robustness.
  - Readability for nonspecialists: The manuscript is reasonably well-written but contains some technical jargon and duplicated text that detract from clarity. The key concepts (h lengthscale, rigid-body approximation) are explained well, but the results section could benefit from more explicit interpretation of the physical meaning of the findings.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the simulation design is thoughtful, but the statistical significance of the key results must be established, and the limitations of the pseudo-membrane approach and force-field dependence need to be addressed more thoroughly.

## Risk / unsupported claims
- The claim that "both 2D environments induce backbone configurations that better match the crystal structure" is not fully supported by the data presented, as the RMSD distributions in Figure 5 are not quantitatively compared to the crystal structure.
- The claim that "contact with an explicit lipid bilayer is not necessary to drive these changes" is weakened by the circularity of the pseudo-membrane construction.
- The statement that "assembly will be dramatically enhanced on the membrane" based on the computed h values assumes that the simulation results are representative of the true experimental system, which is not established given the force-field dependence.
- The claim that "the 3D system will already have mostly LSP1 dimers" relies on a concentration estimate from UniProt that is not verified in the text.
- The generalizability of the findings to other BAR-domain proteins is asserted but not demonstrated.