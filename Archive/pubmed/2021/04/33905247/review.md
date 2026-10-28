## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) with supplementary figure/table references but no supplementary material provided.
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and support of claims by presented evidence. No assessment of formatting, grammar, or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors use massively parallel explicit-solvent MD simulations and Markov State Models (MSMs) to study four cyclic β-hairpin ligands of MDM2. They report that (1) peptide 1 is highly preorganized in solution, (2) solution-state preorganization correlates strongly with experimental binding affinities, (3) binding occurs via conformational selection, and (4) multi-ensemble Markov models (MEMMs) improve off-rate predictions.
- **Visible evidence base** Main text figures (Figures 2–7), tables (Tables 1–4), and referenced supplementary items (Figures S1–S25, Tables S1–S8). No supplementary material was provided for direct inspection.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S25, S1–S8), force field parameter files, simulation input files, and the full NAMFIS output. These are referenced for key validations (e.g., convergence, state definitions, null set construction) and cannot be independently verified.

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious and largely well-executed computational study addressing a question of genuine interest in peptide ligand design: how solution-state conformational preorganization relates to binding affinity and mechanism. The use of MSMs to dissect binding pathways and the application of TRAM to improve kinetic estimates are commendable. However, the central claim that preorganization "determines" binding affinity rests on a correlation analysis with only four peptides, and the mechanistic distinction between conformational selection and induced fit is inferred from tICA landscapes without rigorous kinetic validation. Several technical choices (e.g., force field, feature sets, state definitions) are reasonable but not fully justified, and the comparison with experimental NMR data is presented in a way that obscures a notable discrepancy in folded populations. The manuscript would be strengthened by additional validation, more transparent uncertainty quantification, and a more careful framing of the causal claims.
- **Who would be interested in the results, and why** Computational biophysicists and medicinal chemists working on peptide macrocycle design, particularly those targeting protein-protein interactions such as MDM2-p53. The methodological comparison of MSM and MEMM approaches for binding kinetics will also interest method developers in the molecular simulation community.
- **Major strengths** (1) Large-scale simulation effort with over 3 ms of aggregate trajectory data, enabled by distributed computing. (2) Clear and systematic comparison of multiple quantitative metrics for preorganization. (3) Novel application of TRAM to improve off-rate estimates for cyclic peptide ligands. (4) Honest discussion of limitations in MSM-based rate estimation. (5) The joint MSM approach for comparing conformational landscapes across peptide variants is a useful methodological contribution.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim support / statistical rigor
  - **Claim pointer** "Comparison of predicted native state population with experimental binding affinities reveals a remarkable correlation (R2 = 0.950) between preorganization and experimental binding affinity" and "solution-state preorganization completely determines the binding affinity of the four peptides."
  - **Evidence pointer** Figure 3a, Table 2, Conclusion section
  - **Concern** The central claim of the paper is that preorganization determines binding affinity, but this is based on a correlation with only four data points. With n = 4, an R2 of 0.95 is not statistically distinguishable from a chance correlation, and no confidence intervals or significance tests are provided. Moreover, the causal direction is assumed, not demonstrated. The authors acknowledge that the correlation "might not be observed for sequence variants which more directly perturb the binding interface," which substantially weakens the generality of the claim. The statement that preorganization "completely determines" binding affinity is an overreach given the evidence.
  - **Why it matters** The paper's primary conclusion and its potential impact on peptide design depend on this correlation being robust and causal. With only four peptides, the finding may not generalize, and the causal interpretation is not supported by the data presented.
  - **Resolution test** Provide a statistical analysis of the correlation (e.g., confidence intervals, permutation test). If possible, include additional peptide variants to increase the sample size. Reframe the conclusion to state that preorganization is "strongly associated with" rather than "determines" binding affinity, unless additional evidence for causality is provided.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic interpretation / validation
  - **Claim pointer** "In contrast to an MSM study of p53 TAD binding to MDM2, MSMs of cyclic β-hairpin binding show a conformational selection mechanism."
  - **Evidence pointer** Figures 6, 7, S24, S25; Results section "Binding mechanisms of designed cyclic MDM2 ligands"
  - **Concern** The assignment of a conformational selection mechanism is based primarily on visual inspection of tICA landscapes. The authors state that for peptides 2–4, the slowest motion corresponds to binding and the next-slowest to folding, and that "the vast majority of binding pathways must first visit intermediates where the peptide is folded." However, no quantitative flux analysis (e.g., transition path theory with committor probabilities) is presented to substantiate this claim. For peptide 1, the interpretation is further complicated by the presence of "trap" states, and the authors do not clearly demonstrate that these are off-pathway rather than on-pathway intermediates. The distinction between conformational selection and induced fit is mechanistically important and requires more rigorous support.
  - **Why it matters** The mechanistic conclusion is a key finding of the paper and is contrasted with a previous study. If the assignment is incorrect or not well-supported, the paper's contribution to understanding binding mechanisms is diminished.
  - **Resolution test** Perform a quantitative TPT analysis to compute fluxes through folded vs. unfolded states along binding pathways. Provide committor probability distributions for key states. If possible, compare the inferred mechanism with an independent experimental probe (e.g., kinetics under different denaturant conditions).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical validation / force field sensitivity
  - **Claim pointer** "MSMs of cyclic β-hairpin binding show a conformational selection mechanism" and "changes in peptide conformational populations predicted by the MSMs suggest that entropy loss upon binding is the main factor influencing affinity."
  - **Evidence pointer** Methods section "Molecular Simulation of Cyclic Hairpin Designs"; Results section "MSMs suggest a highly preorganized solution-state conformational ensemble for peptide 1"
  - **Concern** All simulations use a single force field (AMBER ff99sb-ildn-NMR) with GAFF parameters for non-natural residues. The choice of force field is known to significantly affect the conformational ensembles of cyclic peptides, which are highly flexible and often populate multiple metastable states. The authors do not discuss the sensitivity of their conclusions to force field choice, nor do they provide any validation against experimental data beyond the NMR comparison, which itself shows non-negligible discrepancies. The entropy calculations, which are central to the affinity correlation, are particularly sensitive to the accuracy of the conformational ensemble.
  - **Why it matters** If the force field biases the conformational ensemble, the preorganization rankings and entropy estimates could be artifacts. The paper's conclusions would be more robust if the authors demonstrated that their findings are not force field dependent.
  - **Resolution test** Repeat key simulations (at least for peptide 1 and one other peptide) with an alternative force field (e.g., CHARMM36m or a newer AMBER variant) and show that the preorganization rankings and binding mechanism conclusions are unchanged. Alternatively, provide a detailed discussion of why the chosen force field is expected to be reliable for these systems.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Data availability / reproducibility
  - **Claim pointer** "Over 3 ms of aggregate trajectory data was collected for analysis" and "The trajectory data included both unbiased simulations starting from unbound state, and umbrella simulations starting from bound state."
  - **Evidence pointer** Methods section "Molecular Simulation of Cyclic Hairpin Designs"; Tables S2–S4
  - **Concern** The manuscript does not state whether simulation data, analysis scripts, or model input files will be made publicly available. Given the computational expense of these simulations and the importance of reproducibility in computational biology, the absence of a data availability statement is a significant omission. The supplementary material is referenced extensively but was not provided for review.
  - **Why it matters** Without access to the data and analysis code, other researchers cannot reproduce the results or build upon them. This limits the impact and credibility of the work.
  - **Resolution test** Add a data availability statement indicating where simulation trajectories, parameter files, and analysis scripts can be accessed (e.g., a public repository). Ensure that the supplementary material is complete and self-contained.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity / presentation
  - **Affected element** Figure 3
  - **Evidence pointer** Figure 3a–c
  - **Issue** The three panels of Figure 3 present correlations with different metrics, but the axes and units are not clearly labeled in the text description. The reader must infer what is plotted on each axis.
  - **Required correction** Add explicit axis labels and units to Figure 3, and describe each panel in the figure caption with sufficient detail for the reader to understand the comparison without referring to the main text.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods section "Umbrella simulations of cyclic hairpins"
  - **Evidence pointer** Methods section, Table S4
  - **Issue** The choice of the reaction coordinate for umbrella sampling (distance between Cβ of 6-Cl-Trp and Cα of Gly58) is not justified. It is unclear whether this single distance adequately captures the binding/unbinding process.
  - **Required correction** Provide a brief justification for the chosen reaction coordinate, or acknowledge its limitations and discuss potential artifacts.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Results section "Comparison of simulated ensembles with structural NMR measurements"
  - **Evidence pointer** Figure 5, Tables S5–S8
  - **Issue** The comparison with NMR data is presented as validation, but the authors note that the simulations were performed in water while NMR was in DMSO. This solvent mismatch is acknowledged but not discussed in terms of its potential impact on the comparison. The discrepancy in folded populations between MSM and NAMFIS is attributed to this solvent difference, but this is speculative.
  - **Required correction** Expand the discussion of solvent effects on conformational preferences and explicitly state the limitations of the NMR comparison as a validation of the simulations.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Conclusion section
  - **Evidence pointer** Conclusion section
  - **Issue** The conclusion states that "simulation-based prediction of the solution-state properties of cyclic peptide binders may be key to discovering peptides with enhanced binding affinity," but the paper does not provide a forward-looking perspective on how this would be implemented in practice.
  - **Required correction** Add a brief paragraph in the conclusion discussing practical implications for peptide design and potential next steps.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical rigor of the central correlation), R1-M2 (quantitative support for conformational selection mechanism), R1-M3 (force field sensitivity), R1-M4 (data availability).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The application of MSMs to cyclic β-hairpin ligands of MDM2 is novel, and the comparison of MSM vs. MEMM for kinetic estimates is a useful contribution. However, the conceptual framework (preorganization affects binding) is well established.  
  *Scientific importance*: Moderate. The findings could inform peptide design, but the limited number of peptides and the correlational nature of the key result limit the immediate impact.  
  *Interdisciplinary readership*: Limited. The manuscript is written for a specialized computational chemistry/biophysics audience. The methods and results would be challenging for a general biology or chemistry reader.  
  *Technical soundness*: Generally sound, but with notable gaps in statistical rigor, mechanistic validation, and force field sensitivity analysis.  
  *Readability for nonspecialists*: Poor. The manuscript assumes significant familiarity with MSM methodology, tICA, and related concepts. The abstract and introduction are accessible, but the results and discussion are dense and technical.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant question with a substantial computational effort, and the methodological contributions (joint MSMs, TRAM application) are valuable. However, the central claims require stronger statistical support and more rigorous mechanistic validation before they can be considered established.

## Risk / unsupported claims
- The claim that "solution-state preorganization completely determines the binding affinity" is unsupported by the evidence, which shows only a correlation with four data points.
- The claim of a "conformational selection mechanism" is not quantitatively validated and is inferred from tICA landscapes without flux analysis.
- The statement that "the simulated ensembles agree well with the experimental NMR spectroscopy" is weakened by the solvent mismatch (water vs. DMSO) and the acknowledged discrepancy in folded populations.
- The claim that "replacing the highly flexible glycine with L-proline can significantly rigidify the overall cyclic peptide structure" is presented as a general conclusion but is based on a comparison of only one peptide pair.
- The accuracy of the TRAM-based kinetic estimates is presented as "improved" but is only compared to a conventional MSM, not to experimental kinetics for peptides 2–4.