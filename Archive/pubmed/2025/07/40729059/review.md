## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided
- **Assessment boundary** Scientific validity of claims, methodological soundness, interpretation of results, and alignment with stated objectives
- **Shared manuscript claim summary** The authors use molecular docking and short molecular dynamics simulations to compare three chlorogenic acid isomers (3CGA, 4CGA, 5CGA) as potential antagonists of p53 transcription factor, proposing 4CGA as the most promising candidate for adjuvant radiotherapy protection of normal tissues.
- **Visible evidence base** Physicochemical and pharmacokinetic predictions (SwissADME), docking scores and interaction analyses (AutoDock), and 5 ns MD simulations (Visual Dynamics/Gromacs) with RMSD, RMSF, and Rg metrics
- **Missing materials affecting confidence** No structural figures of docking poses or MD plots are included in the provided text; no validation of docking protocol (e.g., redocking, enrichment); no statistical analysis of MD trajectories; no experimental validation; no details on force field parameters or simulation settings beyond minimal description

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in radiation oncology, namely the identification of natural compounds that could protect normal tissues from p53-mediated apoptosis during radiotherapy. The comparison of three CGA isomers is a reasonable extension of prior work focused on 5CGA. However, the study is purely computational with several methodological weaknesses that undermine the strength of the conclusions. The docking results are presented with inconsistent values between the abstract and results section, the MD simulation is very short and lacks rigorous analysis, and the link between binding affinity and functional antagonism is not established. The claim that 4CGA is the most promising candidate is not fully supported by the evidence presented.
- **Who would be interested in the results, and why** Researchers in radiation biology and radiation oncology, particularly those interested in radioprotective agents and natural product-based adjuvants. Computational chemists working on p53-targeting small molecules may also find the docking comparison of interest. The work could be relevant to groups studying chlorogenic acid isomers and their differential biological activities.
- **Major strengths** The study addresses a clinically relevant problem with an underexplored set of compounds. The comparison of three isomers is a useful contribution given that most prior work focused on 5CGA alone. The authors appropriately acknowledge the dual-edged nature of p53 modulation in radiotherapy. The use of publicly available tools and the provision of replication details are commendable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (docking value inconsistency), R1-M2 (MD simulation length and analysis), R1-M3 (functional inference from binding), R1-M4 (docking protocol validation)
- **Assessment against Nature-style criteria** Originality: moderate. The concept of comparing CGA isomers is a reasonable incremental step, but the approach is not novel. Scientific importance: limited at this stage. The findings are hypothesis-generating at best and require experimental validation. Interdisciplinary readership: narrow. The work is primarily of interest to computational biologists and radiation researchers. Technical soundness: insufficient. Several methodological issues need to be addressed, including inconsistent data reporting, lack of protocol validation, and inadequate MD analysis. Readability for nonspecialists: acceptable. The manuscript is generally clear, though some technical terms could be better explained.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revisions to address the technical concerns before the conclusions can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data consistency and reporting
- **Claim pointer** The abstract states that 4CGA has the highest binding energy of -5.41 kCal/mol, while the results section reports -5.26 kcal/mol for the best docking pose of 4CGA.
- **Evidence pointer** Abstract, Results section, Table 5
- **Concern** The binding energy value for 4CGA is reported as -5.41 kCal/mol in the abstract and -5.26 kcal/mol in the results section. This is a direct numerical inconsistency that affects the central claim of the manuscript. Additionally, the units are written inconsistently (kCal/mol vs kcal/mol). Such discrepancies undermine confidence in the accuracy of the reported data.
- **Why it matters** The primary conclusion that 4CGA is the most promising isomer rests on the docking energy values. If the reported values are not reliable or are internally inconsistent, the main claim cannot be evaluated. This also raises questions about the overall quality control of the data reporting.
- **Resolution test** The authors must verify the correct binding energy value for 4CGA and ensure consistent reporting across the abstract, results, and tables. All energy values should be reported with consistent units and precision.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological adequacy of MD simulations
- **Claim pointer** The authors claim that MD simulations spanning 5 ns demonstrate stability of the p53-ligand complexes and that 4CGA stabilizes residue fluctuations in the L1/S3 pocket.
- **Evidence pointer** Methods section (Molecular dynamic simulation), Results section (Molecular dynamics), Figure 7
- **Concern** A 5 ns simulation is generally considered too short to draw meaningful conclusions about protein-ligand complex stability. Protein conformational changes and ligand binding stability typically require simulation times of at least 100 ns, and often longer, to reach equilibrium. The authors do not report whether the systems reached equilibrium within the 5 ns timeframe, nor do they provide any convergence analysis. The RMSD values reported (median 0.16-0.20 nm for complexes) are all very similar and within a narrow range, making it difficult to distinguish meaningful differences between the complexes. Additionally, the RMSF analysis is presented qualitatively without statistical treatment, and the claim that 4CGA reduces fluctuations at specific residues is based on visual inspection of plots that are not included in the provided text.
- **Why it matters** The MD simulation is the primary tool used to validate the docking results and support the claim that 4CGA stabilizes the p53 pocket. Without adequate simulation length, convergence analysis, and statistical treatment, the MD results cannot support the conclusions drawn. The claim of differential stabilization between isomers is particularly vulnerable given the small differences in RMSD values.
- **Resolution test** The authors should extend the MD simulations to at least 100 ns per system, include replicate simulations, report convergence metrics (e.g., RMSD plateau, block averaging), and provide statistical analysis of RMSF differences between complexes. If longer simulations are not feasible, the claims should be substantially weakened and the limitations clearly stated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional inference from binding data
- **Claim pointer** The authors conclude that CGA isomers "potentially play role as anti-apoptotic agent through binding with p53's pocket that involves in DNA transcriptional activity" and that 4CGA has the "highest potential" as a p53 antagonist.
- **Evidence pointer** Conclusion, Discussion section
- **Concern** The manuscript equates binding to the L1/S3 pocket with functional antagonism of p53 transcriptional activity. However, binding affinity alone does not demonstrate antagonism. A molecule could bind without affecting function, or could act as an agonist. The authors reference PQ1 as a known antagonist that binds to this pocket, but they do not provide any comparative functional data or mechanistic evidence that binding of CGA isomers would produce antagonistic effects. The inference from binding energy to biological function is a significant logical leap that is not supported by the computational data presented.
- **Why it matters** The entire premise of the manuscript is that these compounds could serve as radioprotective adjuvants by inhibiting p53-mediated apoptosis. Without evidence that binding translates to functional antagonism, the clinical relevance of the findings remains speculative. This is particularly important given the authors' own acknowledgment that p53 inhibition could also reduce tumor apoptosis and thus compromise radiotherapy efficacy.
- **Resolution test** The authors should either (a) provide additional computational evidence for antagonism, such as free energy calculations, conformational analysis of the p53-DNA interface upon ligand binding, or comparison with known antagonists in the same binding site, or (b) substantially temper their conclusions and clearly state that functional antagonism remains to be experimentally demonstrated.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Docking protocol validation
- **Claim pointer** The authors report docking results using AutoDock with a grid box of 40 x 4 x 40 Å3 and 15 Lamarckian Genetic Algorithm runs.
- **Evidence pointer** Methods section (Molecular docking studies)
- **Concern** The grid box dimensions are unusual, with the Y dimension being only 4 Å. This is extremely narrow and may not adequately sample the binding site or allow for proper ligand pose exploration. Additionally, 15 GA runs is a very small number for AutoDock, which typically requires 50-100 runs to achieve reliable docking results. The authors do not report any validation of their docking protocol, such as redocking of a co-crystallized ligand to assess the accuracy of the docking procedure. The grid center coordinates are taken from a previous study, but it is not clear if the grid box size is appropriate for the binding site of the specific PDB structure used (6ZNC).
- **Why it matters** The docking results are the foundation of the entire study. If the docking protocol is not validated and the parameters are suboptimal, the reported binding energies and interaction patterns may not be reliable. This directly affects the comparison between isomers and the identification of 4CGA as the best candidate.
- **Resolution test** The authors should validate their docking protocol by redocking a known ligand into the 6ZNC structure and comparing the predicted pose with the crystallographic pose (RMSD < 2 Å). They should also justify the grid box dimensions and increase the number of GA runs to at least 50. If the grid box dimensions are correct, the authors should explain the rationale for the 4 Å Y dimension.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and terminology
- **Affected element** Abstract and throughout
- **Evidence pointer** Abstract, Results section
- **Issue** The term "binding energy" is used interchangeably with "free binding affinity" and "docking score." These are distinct concepts in computational chemistry. Docking scores are empirical estimates, not true binding free energies.
- **Required correction** Use consistent terminology throughout. Docking scores should be referred to as such, and the authors should avoid implying that these are experimentally determined binding free energies.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, Molecular dynamics subsection
- **Evidence pointer** Results section (Molecular dynamics), Figure 7
- **Issue** The RMSD and RMSF values are reported as medians with ranges, but no information is provided about the number of data points, the time window used for the median calculation, or any measure of variability beyond the range. The range values are also reported in a confusing manner, e.g., "range of range of 2.1 x 10-6 – 0.19".
- **Required correction** Clarify the statistical treatment of the MD data. Specify the time window used for analysis, report standard deviations or confidence intervals, and correct the typographical errors in the range reporting.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 1-7
- **Evidence pointer** Figures 1-7 (referenced but not provided in the text)
- **Issue** The figures are referenced but not included in the provided text. Based on the descriptions, Figure 7 (RMSF plots) is critical for the claim about residue stabilization, but the reader cannot assess the quality of the data presentation.
- **Required correction** Ensure all figures are of publication quality with clear labels, legends, and appropriate resolution. Figure 7 should clearly indicate the residues of interest and the differences between complexes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language and grammar
- **Affected element** Throughout
- **Evidence pointer** Abstract, Introduction, Results, Discussion
- **Issue** The manuscript contains several grammatical errors and awkward phrasings, e.g., "it present threat by damaging or kill adjacent normal cells", "the p53 protein is assed", "the position of esteriﬁcation on the quinic moiety had no impact on the physicochemical and pharmacokinetic of CGA isomers", "the p53 apoporotein is at 0.14 (range of range of 2.1 x 10-6 – 0.19) nm".
- **Required correction** The manuscript should be carefully proofread and edited for grammar, spelling, and clarity. The phrase "range of range of" appears multiple times and should be corrected.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Introduction, Discussion
- **Evidence pointer** References [1-35] (not individually verified)
- **Issue** The authors cite reference [13] for both the Lipinski rule of five and the SwissADME tool. Reference [13] appears to be attributed to Lipinski et al., but SwissADME was developed by Daina et al. This may be a citation error.
- **Required correction** Verify all references and ensure that each citation accurately corresponds to the appropriate source. Separate citations for Lipinski's rules and SwissADME should be provided.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods section
- **Evidence pointer** Methods section (Molecular dynamic simulation)
- **Issue** The authors state that "the model simulations are too extensive to archive" and provide only general information for replication. This is not consistent with current standards for computational reproducibility.
- **Required correction** Provide input files, parameter files, and analysis scripts as supplementary materials or in a public repository to enable replication of the simulations.

## Risk / unsupported claims
- The claim that CGA isomers "satisfy the drug-likeness for a potential oral medicine" is based on a single computational prediction tool (SwissADME) and may not reflect in vivo behavior.
- The claim that 4CGA has the "highest potential" as a p53 antagonist is based on docking scores that differ by less than 1 kcal/mol between isomers, which is within the typical error range of docking methods.
- The claim that binding to the L1/S3 pocket implies antagonism of p53 transcriptional activity is unsupported by functional data.
- The claim that MD simulations "validate" the docking results is overstated given the short simulation time and lack of convergence analysis.
- The statement that "the CGA isomers are not use the p-glycoprotein transporter for absorption, excretion and various activity of the compounds" is an overinterpretation of a computational prediction.
- The comparison of 4CGA binding energy to PQ1 is not meaningful without standardized docking protocols and energy scales.
- The conclusion that CGA isomers could serve as adjuvant radiotherapy agents is speculative and not supported by the computational evidence alone.