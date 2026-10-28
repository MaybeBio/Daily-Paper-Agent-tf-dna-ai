## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and data availability statements. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific claims, methodological soundness, structural interpretation, functional validation via smFRET, and consistency between evidence and conclusions as presented in the manuscript text.
- **Shared manuscript claim summary** The authors report cryo-EM structures of Rad51 and Dmc1 presynaptic and postsynaptic complexes, identify two residues in Loop2 (V273/D274 in hRAD51; P274/G275 in hDMC1) as key determinants of differential mismatch tolerance, and support this with MD simulations and smFRET assays using reciprocal mutants.
- **Visible evidence base** Main text figures referenced (Figures 1–4), Supplementary Figures S1–S5, Supplementary Tables S1–S4, methods descriptions, and deposited PDB/EMDB accession codes.
- **Missing materials affecting confidence** Supplementary figures and tables not provided; raw smFRET traces and statistical details not shown; MD simulation parameters and convergence criteria not fully described; no negative control data for smFRET without Hop2-Mnd1; no direct binding affinity measurements.

## Reviewer
- **Overall assessment** This manuscript addresses an important question in homologous recombination: how two highly conserved recombinases achieve different mismatch tolerance. The combination of cryo-EM, MD simulation, and single-molecule FRET is appropriate and potentially powerful. The structural data appear to be of good quality based on reported resolutions. However, several concerns weaken the current case. The functional smFRET data are presented without sufficient statistical detail or raw trace examples. The MD simulation methodology is incompletely described, particularly regarding system setup, equilibration, and convergence. The mechanistic model, while plausible, is not fully tested by the mutagenesis data. The claim that D274 acts as a "proofreading" residue is inferred from indirect measurements and requires more direct evidence. The manuscript would be strengthened by additional controls, clearer presentation of quantitative data, and a more cautious interpretation of the simulation results.

- **Who would be interested in the results, and why** Researchers in DNA repair, homologous recombination, meiosis, and structural biology would find these results of interest. The identification of specific residues governing mismatch tolerance has implications for understanding how Rad51 and Dmc1 achieve their distinct biological functions. The structural comparisons between Rad51 and Dmc1 filaments also contribute to the growing body of knowledge on RecA family recombinases. Those studying genetic diversity and genome stability mechanisms would also find the work relevant.

- **Major strengths** The study combines multiple complementary approaches to address a mechanistically important question. The cryo-EM structures provide a foundation for understanding the architectural differences between Rad51 and Dmc1 filaments. The use of smFRET to quantify strand exchange efficiency and mismatch tolerance at the single-molecule level is methodologically sound in principle. The reciprocal mutagenesis strategy between hRAD51 and hDMC1 is a logical approach to test the functional importance of specific residues. The deposition of structures in public databases is commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The authors claim that V273 and D274 in hRAD51, corresponding to P274 and G275 in hDMC1, are "the key residues regulating mismatch tolerance during strand exchange in HR."
- **Evidence pointer** Figure 3, Table 1, Supplementary Figure S4
- **Concern** The smFRET data supporting the central functional claim are presented as summary statistics without showing raw FRET trajectories, histograms of FRET efficiencies, or the distribution of individual molecule behaviors. The reported efficiencies (e.g., 25 ± 1% for hRAD51 wt) lack information on the number of independent experiments, number of molecules analyzed per condition, and statistical tests used. Without this information, it is difficult to assess whether the differences between variants are robust and reproducible. Additionally, the smFRET assay measures a population-level outcome (fraction of molecules showing FRET) rather than directly measuring strand exchange kinetics or mismatch discrimination at the molecular level.
- **Why it matters** The central conclusion of the paper rests on the smFRET functional data. If these data are not rigorously quantified and statistically validated, the claim that specific residues regulate mismatch tolerance is not established.
- **Resolution test** Provide raw smFRET traces for representative molecules, FRET efficiency histograms for each condition, the number of molecules and independent experiments, and appropriate statistical tests comparing conditions. Show that the observed differences are reproducible across biological replicates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational methodology
- **Claim pointer** The authors use MD simulations to calculate binding free energies (MM-GBSA) and conclude that "V273 and D274 in Loop2 of hRAD51, corresponding to P274 and G275 of hDMC1, play a crucial role in the DNA binding."
- **Evidence pointer** Methods section "Molecular dynamic simulation" and "MM-GBSA calculation", Figure 2D, Supplementary Tables S3 and S4
- **Concern** The MD simulation methodology is insufficiently described. Key details are missing, including the initial structure preparation, solvation box dimensions, ion concentration, equilibration protocol, simulation length, temperature and pressure coupling methods, and convergence criteria. The MM-GBSA method is known to be sensitive to the choice of internal dielectric constant, entropy contributions, and snapshot selection. The authors state that five independent simulations were run for 1 μs each, but no information is provided on whether the trajectories converged, how the five replicates were combined, or whether the reported binding free energies are averaged over replicates with associated errors. The construction of hDMC1 models based on ScDmc1 structures also requires validation.
- **Why it matters** The MD simulation results are used to support the structural interpretation and to guide the mutagenesis strategy. If the simulations are not rigorously performed and validated, the conclusions drawn from them are not reliable.
- **Resolution test** Provide complete simulation details, including system setup, equilibration, production run parameters, and convergence analysis. Show that the binding free energy calculations are reproducible across replicates and robust to analysis parameters. Validate the hDMC1 models against the recently published cryo-EM structures.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural interpretation
- **Claim pointer** The authors state that "the major conformational differences between these two proteins are located in their Loop2 regions" and that these differences explain the distinct mismatch tolerance.
- **Evidence pointer** Figures 1 and 2, Supplementary Figure S3
- **Concern** The structural comparison between hRAD51 and ScDmc1 is complicated by the use of different species. While the authors argue that sequence conservation justifies this comparison, the interpretation would be strengthened by a direct comparison of hRAD51 and hDMC1 structures. The authors mention that hDMC1 structures were recently published and used to validate their MD models, but they do not provide a detailed structural comparison between their ScDmc1 structures and the hDMC1 structures. Additionally, the claim that Loop2 is the "major" conformational difference is qualitative; no quantitative comparison of structural differences across the entire protein is provided.
- **Why it matters** The structural comparison is the foundation for identifying the key residues. If the comparison is not rigorous or is confounded by species differences, the identification of specific residues as functionally important is weakened.
- **Resolution test** Provide a quantitative structural comparison between hRAD51 and hDMC1 (or ScDmc1) complexes, including per-residue RMSD or displacement analysis. Discuss the relevance of species differences and validate the ScDmc1 structures as faithful models for hDMC1.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic model
- **Claim pointer** The authors propose a model where "the rigid electrostatic interaction formed by R-D may prevent R235 from binding to the loose and flexible mismatch containing complementary strand," thereby providing a proofreading mechanism.
- **Evidence pointer** Figure 4, Discussion
- **Concern** The proposed mechanism is speculative and not directly tested. The authors do not provide direct evidence that the R-D interaction is rigid or that it prevents R235 from binding mismatched DNA. The binding free energy calculations show differences, but these are indirect. The model also does not fully explain why Dmc1, which lacks the D residue, would be more tolerant to mismatches. The authors suggest that P274 in Dmc1 forms a weaker interaction with R236, but this is not directly demonstrated.
- **Why it matters** The mechanistic model is the main conceptual contribution of the paper. If the model is not well-supported by direct evidence, the paper's impact is diminished.
- **Resolution test** Provide additional experimental or computational evidence directly testing the proposed mechanism. This could include mutations that disrupt the R-D interaction specifically, measurements of R235 conformational dynamics, or enhanced sampling simulations that directly compare the behavior of R235 with matched and mismatched DNA in the presence and absence of D274.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3
- **Evidence pointer** Figure 3E and F
- **Issue** The bar graphs showing strand exchange efficiencies lack individual data points and error bars are shown without specifying what they represent (SD, SEM, or confidence intervals).
- **Required correction** Show individual data points, specify the error bar type, and indicate the number of independent experiments.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The rate constants (kapp) are reported without confidence intervals or statistical comparison between variants.
- **Required correction** Provide confidence intervals for rate constants and perform appropriate statistical tests comparing variants.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methods clarity
- **Affected element** smFRET assay
- **Evidence pointer** Methods section "Acquisition of smFRET data"
- **Issue** The smFRET assay description lacks details on how the strand exchange efficiency was calculated from the raw data, what constitutes a "FRET spot," and how background and false positives were handled.
- **Required correction** Provide a more detailed description of the smFRET data analysis, including criteria for identifying FRET spots and how the efficiency was calculated.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Structural validation
- **Affected element** hDMC1 models
- **Evidence pointer** Methods section "Molecular dynamic simulation"
- **Issue** The hDMC1 models built by homology are not validated against the recently published cryo-EM structures of hDMC1.
- **Required correction** Compare the hDMC1 models to the published cryo-EM structures and discuss any differences.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The discussion of previous work on mismatch tolerance in Rad51 and Dmc1 is brief and does not fully contextualize the current findings within the existing literature.
- **Required correction** Expand the discussion of prior studies on mismatch tolerance and how the current work advances or challenges previous conclusions.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "proofreading" is used to describe the function of D274, but this term has specific connotations in DNA replication and may be misleading in the context of homologous recombination.
- **Required correction** Consider using a more neutral term such as "fidelity control" or "mismatch discrimination" and define the term clearly when first used.

## Risk / unsupported claims
- The claim that V273 and D274 are "the key residues regulating mismatch tolerance" is not fully supported because the smFRET data lack statistical rigor and the MD simulations are not fully validated.
- The proposed mechanistic model involving a "rigid electrostatic interaction" between D274 and R235 is speculative and not directly tested.
- The statement that "the major conformational differences between these two proteins are located in their Loop2 regions" is qualitative and not supported by quantitative structural comparison.
- The functional significance of the identified residues is inferred from mutagenesis and simulation, but no direct binding measurements or kinetic analyses are provided.
- The claim that the "8 nt-microhomology" requirement is confirmed by the smFRET data is not fully supported because the data for 6nt-paired DNA are presented without sufficient detail.
- The relevance of the ScDmc1 structures for understanding hDMC1 function is assumed but not rigorously established.