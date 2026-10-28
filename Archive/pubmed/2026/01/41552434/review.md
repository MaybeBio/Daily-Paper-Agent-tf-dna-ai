## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure references
- **Assessment boundary** Scientific validity, methodological rigor, interpretation of results, and alignment with claims made in the abstract and discussion
- **Shared manuscript claim summary** The authors use molecular dynamics simulations of full-length p53 (including intrinsically disordered N- and C-terminal regions) to show that the Y220C mutation disrupts DNA-binding through long-range allosteric effects, and that PK11000 partially restores wild-type-like behavior primarily through electrostatic and hydrogen-bonding networks rather than large-scale structural changes. They also compare full-length versus DBD-only simulations to argue that the disordered termini are essential for capturing true p53 dynamics.
- **Visible evidence base** Simulation trajectories (4 × 1 μs per construct, plus 10 × 200 ns seeded simulations for FL constructs), RMSD, dihedral RMSD, RMSF, secondary structure analysis, hydrogen bonding analysis (TRT and EHBS), electrostatic network analysis with embedding errors, clustering analysis, Ramachandran plots
- **Missing materials affecting confidence** No explicit force field validation data for the Phyre2 model; no convergence assessment metrics (e.g., block averaging, autocorrelation times); no error bars or statistical significance tests for hydrogen bonding and electrostatic differences; no raw trajectory data or input files visible; no comparison to experimental data beyond qualitative references; no details on the "extensive testing" mentioned in Methods

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question: whether full-length simulations of p53, including disordered termini, reveal allosteric mechanisms of Y220C destabilization and PK11000 rescue that are missed by DBD-only studies. The computational effort is substantial (4 μs per FL construct, 6 μs total per FL construct with seeding), and the use of dihedral RMSD for intrinsically disordered proteins is a thoughtful methodological choice. However, the manuscript suffers from several critical weaknesses. First, the central claim of "rescue" is supported primarily by indirect metrics (hydrogen bonding, electrostatic networks) without a clear, quantitative definition of what constitutes functional rescue. Second, the comparison between FL|DBD and DBD is confounded by the fact that the DBD-only simulations lack the DNA-binding context that the FL simulations include, making the comparison potentially misleading. Third, the electrostatic network analysis methodology is described too briefly to assess its validity, and the embedding error metric is not clearly defined. Fourth, the manuscript lacks any statistical treatment of the simulation data, making it impossible to distinguish genuine effects from noise. The writing is generally clear but the results section is overly long and would benefit from sharper focus on the key findings. The work has potential value as a methodological contribution and hypothesis-generating study, but the current evidence does not fully establish the claims made in the abstract.
- **Who would be interested in the results, and why** Researchers in computational biophysics and drug discovery, particularly those studying p53 and intrinsically disordered proteins. The methodological framework (dihedral RMSD clustering, electrostatic network analysis) could be of interest to the broader MD simulation community. The findings on the importance of disordered termini in allosteric regulation may also interest experimentalists studying p53 function and regulation.
- **Major strengths** 1) The study addresses a significant gap by simulating full-length p53, which is rarely done due to computational cost and the challenge of modeling disordered regions. 2) The use of dihedral RMSD as a metric for disordered proteins is a thoughtful and appropriate methodological choice. 3) The comparison between FL and DBD simulations is a valuable contribution to understanding the limitations of truncated constructs. 4) The electrostatic network analysis provides a novel perspective on allosteric communication. 5) The computational effort is substantial and the seeding strategy for enhanced sampling is reasonable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of statistical treatment), R1-M2 (confounded FL|DBD vs DBD comparison), R1-M3 (inadequate definition of "rescue"), R1-M4 (insufficient methodological detail for electrostatic network analysis)
- **Assessment against Nature-style criteria** **Originality**: Moderate. The application of full-length p53 simulations is novel, but the overall approach (MD simulations to study mutation effects and ligand rescue) is well-established. **Scientific importance**: High. Understanding p53 allosteric regulation and rescue mechanisms has significant implications for cancer therapy. **Interdisciplinary readership**: Moderate. The work is primarily of interest to computational biophysicists and p53 researchers; the broader cancer biology community may find the conclusions relevant but the methods inaccessible. **Technical soundness**: Currently insufficient. The lack of statistical analysis, unclear methodology for key analyses, and confounded comparisons undermine confidence in the conclusions. **Readability for nonspecialists**: The introduction and discussion are accessible, but the results section is dense and would benefit from clearer framing of the key findings.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential but requires substantial revisions to address the methodological and statistical concerns before the claims can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that PK11000 "restores wild-type-like behavior" in the Y220C mutant based on hydrogen bonding and electrostatic network analyses.
- **Evidence pointer** Results sections "Hydrogen Bond Analysis" and "Electrostatic Network Analysis"; Figures 5 and 6 (locations not provided)
- **Concern** The manuscript reports differences in hydrogen bonding (TRS, EHBS) and electrostatic network metrics between constructs without any statistical treatment. No error bars, confidence intervals, or significance tests are provided. With only 4 replicates per construct, it is impossible to determine whether the observed differences are meaningful or within the range of natural simulation variability. The authors state that "PK11000 lowers the total number of unique bonds" and "restores wild-type electrostatic networks," but these claims are based on point estimates without uncertainty quantification.
- **Why it matters** The central claim of the paper is that PK11000 rescues the Y220C mutant through specific molecular mechanisms. Without statistical evidence, these claims are not supported. The differences in hydrogen bonding metrics (e.g., TRS of 13.9 vs 15.3) could easily arise from sampling noise given the high dimensionality of the system and the limited sampling time.
- **Resolution test** Provide per-replicate values, standard deviations, and appropriate statistical tests (e.g., bootstrapping, permutation tests) for all reported metrics. If the differences are not statistically significant, the claims of rescue must be tempered accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The authors claim that "the full-length protein is essential to capture the true dynamics of the protein" and that DBD-only simulations are insufficient.
- **Evidence pointer** Results section "Comparison between FL|DBD and DBD"; Figures 7 and 8 (locations not provided)
- **Concern** The comparison between FL|DBD and DBD is confounded by the presence of DNA in the FL simulations but not in the DBD-only simulations. The FL constructs include bound DNA (as stated in Methods: "DNA that interacts directly with p53"), while the DBD-only simulations appear to lack DNA. This means that any observed differences could be due to the presence of DNA rather than the presence of the disordered termini. The authors do not address this confound or provide DBD-only simulations with DNA as a control.
- **Why it matters** The claim that disordered termini are essential for capturing true p53 dynamics is a key conclusion of the paper. If the comparison is confounded by the presence of DNA, this conclusion is not supported. The authors need to either include DBD-only simulations with DNA or explicitly acknowledge and discuss this limitation.
- **Resolution test** Include DBD-only simulations with bound DNA as a control, or clearly state that the comparison is between FL-with-DNA and DBD-without-DNA, and discuss the implications of this difference for the interpretation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** The abstract states that PK11000 "restores stability and reinstates activity" and the discussion claims "rescue" of the Y220C mutant.
- **Evidence pointer** Abstract; Discussion section "Rescue of Y220C Mutant in FL vs DBD"
- **Concern** The term "rescue" is used throughout the manuscript to describe the effect of PK11000 on the Y220C mutant, but the criteria for what constitutes "rescue" are never explicitly defined. The authors show that PK11000 affects hydrogen bonding and electrostatic networks, but they do not demonstrate that these changes correspond to functional rescue (e.g., restored DNA-binding affinity, transcriptional activity, or thermal stability). The manuscript would benefit from a clear, quantitative definition of rescue, such as "restoration of wild-type-like hydrogen bonding patterns" or "recovery of wild-type electrostatic network topology."
- **Why it matters** The use of "rescue" implies a functional outcome that the simulations do not directly measure. Overstating the implications of the results could mislead readers and overstate the therapeutic potential of PK11000. The authors should either provide a clear operational definition of rescue or use more cautious language.
- **Resolution test** Define specific, measurable criteria for rescue (e.g., "restoration of wild-type hydrogen bonding occupancy at key DNA-binding residues") and demonstrate that these criteria are met. Alternatively, revise the language to describe the observed effects without implying functional rescue.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The authors state that "extensive testing" was conducted to select force fields and protonation states, and that the electrostatic network analysis follows established procedures.
- **Evidence pointer** Methods sections "Force Field and Parameter Selection" and "Electrostatic Analysis"
- **Concern** The Methods section describes the electrostatic network analysis too briefly. The procedure for computing residue-by-residue electrostatic interaction matrices, the normalization scheme, the thresholding at 0.003, and the embedding error calculation are not described in sufficient detail to be reproduced. The authors reference Cowan et al. and Abramson et al., but the specific adaptations made for this study are unclear. Similarly, the "extensive testing" of force fields and protonation states is mentioned but not documented.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without detailed methods, other researchers cannot replicate the analysis or assess its validity. The lack of detail also makes it difficult to evaluate whether the chosen parameters are appropriate.
- **Resolution test** Provide a detailed description of the electrostatic network analysis, including all parameters, equations, and code or pseudocode. Document the force field and protonation state testing in the Supporting Information.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Convergence assessment
- **Claim pointer** The authors claim that their simulations provide "a first-order exploration into the behavior of full-length p53" and draw conclusions about the dynamics of the system.
- **Evidence pointer** Methods section "Molecular Dynamics Simulations"; Results sections throughout
- **Concern** No convergence assessment is provided for the simulations. The authors do not report whether the 1 μs trajectories reached equilibrium, whether the seeded 200 ns simulations converged to similar distributions, or whether the sampling is sufficient to draw conclusions about the conformational landscape of a protein with large disordered regions. For intrinsically disordered proteins, convergence is particularly challenging and should be explicitly addressed.
- **Why it matters** If the simulations have not converged, the conclusions drawn from them may be artifacts of insufficient sampling. This is especially critical for the claims about allosteric communication and rescue, which depend on the system sampling relevant conformational states.
- **Resolution test** Provide convergence metrics such as block-averaged RMSD, autocorrelation times, or split-half analysis. Show that the seeded simulations converge to similar distributions and that the conclusions are robust to the choice of analysis window.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that PK11000 "restores stability and reinstates activity" but the manuscript does not directly measure stability or activity. The abstract overstates the findings.
- **Required correction** Revise the abstract to accurately reflect the scope of the study, e.g., "restores wild-type-like conformational and electrostatic properties" rather than "restores stability and reinstates activity."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1
- **Evidence pointer** Figure 1 (location not provided)
- **Issue** The structural diagram of full-length p53 generated by Phyre2 is described but not shown in the text. The figure would benefit from a clearer labeling of the N- and C-terminal regions and the Y220C mutation site.
- **Required correction** Add clear labels to Figure 1 and consider including a zoomed-in view of the Y220C/PK11000 binding site.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Methods section "Dihedral RMSD"
- **Evidence pointer** Methods section "Dihedral RMSD"
- **Issue** The term "dihedral RMSD" is used, but the manuscript does not clearly explain how this differs from standard RMSD or why it is more appropriate for disordered proteins. A brief justification would help readers understand the choice.
- **Required correction** Add a sentence explaining the rationale for using dihedral RMSD over Cartesian RMSD for intrinsically disordered proteins.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods section "Molecular Dynamics Simulations"
- **Evidence pointer** Methods section "Molecular Dynamics Simulations"
- **Issue** The manuscript states that "Example input files are included in the supplemental files" but does not specify where these files can be accessed or what they contain.
- **Required correction** Provide a clear reference to the Supporting Information and describe the contents of the input files.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section "Rescue of Y220C Mutant in FL vs DBD"
- **Evidence pointer** Discussion section "Rescue of Y220C Mutant in FL vs DBD"
- **Issue** The authors note that the WT_PK11000 construct has the highest EHBS score and attribute this to "a transient conformation that forms an unusually high number of hydrogen bonds." This interpretation is speculative and not supported by direct evidence.
- **Required correction** Either provide evidence for the transient conformation (e.g., cluster analysis showing a distinct state) or present the observation without speculation.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction cites several studies on p53 allostery and MD simulations but does not clearly position this work relative to prior computational studies of Y220C. A brief comparison with existing MD studies of Y220C would strengthen the novelty claim.
- **Required correction** Add a paragraph in the Introduction discussing prior MD studies of Y220C and explicitly stating what this study adds.

## Risk / unsupported claims
- The claim that PK11000 "restores stability and reinstates activity" (abstract) is not directly supported by the simulation data, which measure structural and electrostatic properties rather than functional activity.
- The claim that "the full-length protein is essential to capture the true dynamics of the protein" is confounded by the presence of DNA in FL simulations but not in DBD-only simulations.
- The interpretation that WT_PK11000's high EHBS is due to "a transient conformation" is speculative and not supported by direct evidence.
- The claim that "rescue" occurs "most readily" in the electrostatic network is based on a single analysis method without statistical validation.
- The statement that "the Phrye2 model is more compact" and therefore more physical is a subjective judgment not supported by quantitative comparison with experimental data or other models.