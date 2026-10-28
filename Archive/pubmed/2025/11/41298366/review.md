## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, and significance of the proposed structural models for TDP-43 CTD conserved region multimerization
- **Shared manuscript claim summary** The authors propose that the conserved region (CR, residues 319–341) of TDP-43's C-terminal domain adopts α-helical structure under physiological conditions and mediates dynamic, multimeric (primarily tetrameric) helical assemblies. They integrate NMR spectroscopy, analytical ultracentrifugation, AlphaFold2-Multimer predictions, and all-atom molecular dynamics simulations to derive structural models. They further link these assemblies to phase separation, nuclear retention, and toxicity, and suggest the structures are pharmacologically targetable.
- **Visible evidence base** NMR chemical shift data (Fig. 1), saturation concentration measurements for ~20 alanine variants (Fig. 2A), DIC microscopy (Fig. 2B), CSP correlations (Fig. 2C), two-chain MD contact maps (Fig. 2D–G), AUC data (Fig. 3), NOE data (Fig. 4), AF2-Multimer confidence scores and MD stability analyses (Fig. 5), plus supplementary figures and tables referenced throughout
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; source data files not accessible; specific NMR assignment tables not shown; detailed parameters for AUC global fitting not fully described; raw trajectories and validation metrics for MD simulations not available

## Reviewer
- **Overall assessment** This manuscript addresses a significant and timely question: the structural basis of TDP-43 CTD conserved region self-assembly, which is central to understanding TDP-43 function and dysfunction in ALS/FTD. The integrative approach combining multiple biophysical methods with computational modeling is appropriate and ambitious. The correlation between in vitro phase separation data, NMR-derived assembly metrics, and cellular nuclear retention is compelling. However, the central structural claim, that a specific tetrameric helical assembly (Tet-1) represents the physiologically relevant multimeric state, rests on indirect evidence. The AF2-Multimer predictions have low confidence, the MD simulations are short relative to the timescales of assembly/disassembly, and the NOE data are qualitative. The manuscript would be strengthened by more direct validation of the proposed tetramer model, such as cross-linking mass spectrometry, paramagnetic relaxation enhancement-derived distance restraints, or engineered disulfide-trapped variants with functional readouts. The claim of pharmacological targetability is speculative at this stage.

- **Who would be interested in the results, and why** Researchers studying TDP-43 biology, particularly those focused on phase separation, liquid-liquid phase separation mechanisms, and the molecular basis of ALS/FTD. The work will also interest structural biologists studying dynamic, transient protein assemblies that are refractory to traditional structure determination methods, as well as computational biologists developing and benchmarking integrative modeling approaches for IDPs. The methodological framework combining AF2-Multimer with MD and experimental constraints may serve as a template for similar systems.

- **Major strengths**
  1. The manuscript addresses a critical gap: the structural details of the conserved region of TDP-43 CTD, which has been implicated in function and disease but lacked atomic-level characterization.
  2. The integrative approach is well conceived, combining multiple orthogonal techniques (NMR, AUC, AF2-Multimer, MD) to compensate for the limitations of each individual method.
  3. The alanine-scanning mutagenesis across the entire CR is systematic and provides a comprehensive functional map linking specific residues to phase separation.
  4. The correlation between in vitro biophysical data (CSP, csat) and cellular readouts (nuclear retention) strengthens the physiological relevance of the findings.
  5. The authors are appropriately cautious in several places, acknowledging the dynamic and heterogeneous nature of the assemblies and the limitations of their data.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for central structural claim
- **Claim pointer** "we establish atomic-level structural models of TDP-43 multimeric assemblies" and "TDP-43 CR forms dynamic, multimeric helical assemblies stabilized by a methionine-rich core"
- **Evidence pointer** Fig. 5, Supplementary Figs. 11, 16–25
- **Concern** The central structural model (Tet-1) is derived from AF2-Multimer predictions that the authors themselves note have low confidence scores. The MD simulations, while extensive (~100 μs aggregate for dimers, 4–5 μs for multimers), are short relative to the timescales of assembly and disassembly of weak, dynamic complexes. The stability of Tet-1 in MD simulations does not establish that this is the dominant or functionally relevant state in solution. The NOE data are qualitative and cannot distinguish between the proposed tetramer and other possible arrangements. The authors state "the data suggest but cannot conclusively demonstrate that the most stable multimeric form is the tetramer" in the AUC section, yet the abstract and discussion present the tetramer model more definitively.
- **Why it matters** The structural model is the central contribution of the paper. If the tetramer model is not robustly validated, the mechanistic interpretations and the proposed therapeutic implications are substantially weakened. The field needs reliable structural information to guide functional studies and drug design.
- **Resolution test** Provide additional experimental validation of the tetramer model. This could include: (1) cross-linking mass spectrometry to identify intermolecular contacts in solution; (2) PRE-based distance restraints between singly labeled variants to validate the proposed helix-helix interface; (3) analytical ultracentrifugation or mass photometry at higher concentrations approaching the Kd to directly observe tetramer formation; (4) engineered disulfide-trapped tetramers with functional assays to demonstrate that the tetrameric state supports nuclear retention and splicing function. Alternatively, the authors should temper the language throughout to clearly present Tet-1 as a plausible model rather than an established structure.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of AUC analysis
- **Claim pointer** "the data suggest but cannot conclusively demonstrate that the most stable multimeric form is the tetramer" and the monomer-dimer-tetramer model with Kd,mon-dim of 2.4 mM and Kd,dim-tet of 2.7 ± 0.6 µM
- **Evidence pointer** Fig. 3, Supplementary Table 1
- **Concern** The AUC analysis is presented with limited quantitative detail. The authors state that a monomer-dimer-tetramer model provided the best fit, but do not show how alternative models (e.g., monomer-tetramer, isodesmic self-association) were compared statistically. The Kd values are reported with confidence intervals, but the quality of the global fit is not demonstrated. The statement that "two state monomer-dimer or monomer-trimer models and three state monomer-dimer-trimer models resulted in poorer fits" is not supported by shown data or statistical comparison metrics.
- **Why it matters** The stoichiometry of the assembly is a key claim. If the AUC data do not robustly distinguish between models, the tetramer conclusion is weakened. The Kd values are used to argue for weak dimerization and cooperative tetramerization, which is central to the proposed assembly mechanism.
- **Resolution test** Provide the full AUC fitting results, including residuals for each model tested, statistical comparison (e.g., F-test or AIC/BIC values), and the confidence intervals for all fitted parameters. Show the c(s) distributions at all concentrations and the global fit overlay. If possible, include sedimentation equilibrium data to provide model-independent molecular weight information.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance of the tetramer model
- **Claim pointer** "helix-mediated TDP-43 self-assembly aids nuclear retention, mitigating improper localization and toxicity"
- **Evidence pointer** Fig. 2H, Supplementary Figs. 4, 5
- **Concern** The cellular experiments show that mutations altering phase separation also affect nuclear retention, but the link to the specific tetrameric structure is indirect. The authors do not demonstrate that the tetrameric state, as opposed to any form of enhanced self-assembly, is what promotes nuclear retention. The yeast toxicity data are correlative and based on a published dataset, not direct experiments. The statement that "mutations at W334 increased toxicity, except for L and M substitutions" is interesting but not mechanistically explained in the context of the proposed structure.
- **Why it matters** The claim that the tetrameric structure is functionally important for nuclear retention and toxicity is a key translational aspect of the paper. Without direct evidence linking the specific structure to function, the physiological relevance of the model remains uncertain.
- **Resolution test** Design experiments that specifically test the functional role of the tetramer. For example: (1) engineer a constitutively tetrameric CR (e.g., via fusion to a tetramerization domain) and test whether it rescues nuclear retention in a TDP-43 knockout background; (2) create mutants that specifically disrupt the tetramer interface without affecting monomeric helicity and test their effects on nuclear retention and splicing; (3) use FRAP or single-molecule imaging to compare the dynamics of WT and mutant TDP-43 in cells.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the structural model
- **Claim pointer** "these structures here explain why the entire 21-residue CR is conserved"
- **Evidence pointer** Fig. 5, Supplementary Fig. 12
- **Concern** The structural model is based on a fragment (residues 310–350) rather than the full-length CTD or full-length TDP-43. While the authors show that the Tet-1 model remains stable within the full-length CTD in simulations, this does not account for the influence of the N-terminal domain, RNA binding, or post-translational modifications on the assembly. The claim that the conservation of the entire CR is explained by the tetramer model is strong, given that the model is derived from a fragment and the simulations may not capture all relevant interactions.
- **Why it matters** TDP-43 functions in the context of the full-length protein, and the CTD is known to interact with the NTD and RNA. A model based on an isolated fragment may not capture the physiologically relevant assembly.
- **Resolution test** Perform MD simulations or experimental studies on the full-length CTD or full-length TDP-43 to test whether the tetramer interface is maintained. Use cross-linking mass spectrometry on full-length TDP-43 to identify intermolecular contacts. Compare the assembly behavior of the fragment with the full-length CTD using AUC or NMR.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Fig. 2A
- **Evidence pointer** Fig. 2A
- **Issue** The csat values are presented as a bar graph with error bars, but the individual data points are not shown. Given the small number of replicates (n=3), showing individual points would help assess the variability and the robustness of the differences.
- **Required correction** Add individual data points to the bar graph, or use a dot plot with mean and SD overlaid.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Fig. 2H
- **Evidence pointer** Fig. 2H
- **Issue** The statistical test used for the nuclear retention data is stated as Mann-Whitney U test, but the number of replicates and the exact p-values are not provided in the figure legend. The legend states "Mean ± SD is shown for ≥5 independent replicates" but does not specify n for each variant.
- **Required correction** Provide the exact n for each variant and the p-values in the figure legend or in a supplementary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** NMR relaxation experiments
- **Evidence pointer** Methods section, NMR spectroscopy
- **Issue** The methods describe the NMR experiments but do not provide details on how the 15N R2 values were calculated from the experimental data or how they were compared to the simulated values. The statement "consistent with the slowed motions observed in experiments" is vague.
- **Required correction** Provide details on the R2 calculation, including the relaxation delays used, the fitting procedure, and the uncertainty in the measured values. Describe how the simulated R2 values were computed and the criteria for agreement.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "native state" is used to describe the α-helical conformation of the CR. Given that the CR is part of an intrinsically disordered region, the term "native state" may be misleading. The authors likely mean the state under physiological conditions in the absence of denaturants or aggregation.
- **Required correction** Consider using "physiological state" or "solution state under native conditions" instead of "native state" to avoid confusion with the traditional meaning of a folded protein's native state.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The authors do not discuss alternative models for CR self-assembly, such as the possibility of a dynamic equilibrium between multiple oligomeric states or the role of transient β-sheet formation in the native assembly. Given the known amyloidogenic propensity of this region, a more thorough discussion of how the helical tetramer relates to pathogenic β-sheet conversion would strengthen the paper.
- **Required correction** Add a paragraph in the Discussion addressing alternative assembly models and the relationship between the functional helical tetramer and the pathogenic β-sheet state.

- **Technical failings that need to be addressed before the case is established**
  1. The central tetramer model (Tet-1) requires additional experimental validation beyond MD stability (R1-M1).
  2. The AUC analysis needs more quantitative rigor, including model comparison statistics (R1-M2).
  3. The link between the specific tetramer structure and cellular function needs direct testing (R1-M3).
  4. The generalizability of the fragment-based model to full-length TDP-43 needs demonstration (R1-M4).

- **Assessment against Nature-style criteria**
  - **Originality**: The work is original in its specific focus on the structural details of the TDP-43 CR multimerization. While previous studies have identified the importance of this region, no atomic-level models of the assembled state have been proposed. The integrative approach is not entirely novel but is applied to a new system.
  - **Scientific importance**: The question is important. TDP-43 pathology is central to ALS/FTD, and understanding the native assembly of the CTD is crucial for understanding both function and dysfunction. However, the importance is somewhat diminished by the lack of direct validation of the proposed structure.
  - **Interdisciplinary readership**: The work will appeal to structural biologists, biophysicists, and neuroscientists studying protein aggregation and phase separation. The methodological framework may interest computational biologists. The clinical relevance to ALS/FTD broadens the potential audience.
  - **Technical soundness**: The NMR experiments appear well-executed, and the MD simulations use a state-of-the-art force field validated for IDPs. However, the central structural claim is not sufficiently validated. The AUC analysis lacks quantitative detail. The cellular experiments are correlative.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible. The figures are clear. However, some sections, particularly the MD methods, may be challenging for non-specialists. The abstract is concise and understandable.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question with a well-conceived integrative approach. The data are suggestive but not conclusive for the central structural claim. If the authors can provide additional experimental validation of the tetramer model, or substantially temper their claims to present it as a plausible model, the paper would be suitable for publication. The current version, however, does not fully establish the case from the provided evidence.