## Review setup
- **Input scope** Full manuscript text including abstract, significance statement, introduction, materials and methods, results, discussion, data availability, and supplementary figure/table legends
- **Assessment boundary** Scientific content, methodological rigor, claims versus evidence alignment, and technical soundness as presented in the provided text. No line numbers were provided; references to specific locations use section and figure/table names.
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations to characterize the binding of the PHD finger and a PHD-linker-bromodomain fragment of BPTF to a full nucleosome core particle, compared to binding to an H3 peptide and to free states. They report that nucleosome engagement induces compaction of the BPTF multidomain structure, displaces the H3 tail from DNA, increases H3 tail flexibility, promotes compensatory H4 tail binding to DNA, reduces overall histone-DNA hydrogen bonding, and that van der Waals interactions dominate over electrostatic repulsion in stabilizing reader-nucleosome association.
- **Visible evidence base** Results sections with Figures 1-9, Tables 1-2, and references to Supplementary Figures S1-S19 and Tables S1-S5. Methods descriptions for system construction, simulation protocols, and analysis approaches.
- **Missing materials affecting confidence** The actual figures, supplementary figures, and supplementary tables were not provided. Raw trajectory data and analysis scripts are stated to be available online but were not accessed. No experimental validation data are included. Convergence assessments beyond RMSD-based equilibration determination are not fully described.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and technically ambitious simulation study addressing an important question in chromatin biology: how a multidomain reader protein engages a full nucleosome substrate and what consequences this has for nucleosome dynamics. The work is timely, as most structural and simulation studies of reader proteins use short histone peptides that may not capture the full nucleosomal context. The authors have generated a large simulation dataset (35 microseconds total) and performed a range of analyses that collectively support several interesting conclusions. However, the manuscript has significant limitations that temper enthusiasm. The most concerning issues are the lack of validation of the simulation model against experimental data, the absence of quantitative convergence assessments, the reliance on MM/GBSA free energy estimates without adequate caveats, and the speculative nature of the mechanistic claims given the limited sampling. The claim that BPTF binding "may facilitate chromatin remodeling" is not directly supported by the data presented. The writing is generally clear, but some methodological details are insufficient for reproduction. Overall, the study is a useful contribution to the field, but the strength of the conclusions needs to be tempered and several technical issues need to be addressed.

- **Who would be interested in the results, and why** Researchers studying chromatin structure and dynamics, particularly those interested in histone post-translational modification readout by PHD fingers and bromodomains. Computational biophysicists working on nucleosome simulations will find the methodological approach and system construction details useful. Structural biologists studying reader-nucleosome complexes may benefit from the predicted conformational behavior of BPTF. The finding that H3 tail displacement by a reader promotes H4 tail binding to DNA could be of interest to those studying cross-talk between histone modifications and chromatin remodeling.

- **Major strengths** The study addresses an important gap in the field by simulating reader proteins in the context of a full nucleosome rather than isolated peptides. The simulation protocol is state-of-the-art, using the ff19SB force field, OPC water, and appropriate ion conditions. The comparison across multiple systems (free, peptide-bound, nucleosome-bound) is well designed. The analysis of interdomain angles and binding pocket volumes provides useful structural insight. The data availability statement is commendable, with inputs and scripts provided.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the first 300 ns of each simulation were considered equilibration time" based on RMSD from the first frame and visual inspection of H3 tail collapse.
- **Evidence pointer** Materials and methods, MD simulations section; Figure 1
- **Concern** The determination of equilibration time is based on subjective criteria (visual inspection) and a single metric (RMSD from the first frame). For a study that draws quantitative conclusions about hydrogen bonding, contact frequencies, and free energies, the equilibration protocol needs to be more rigorously justified. The choice of 300 ns as a universal cutoff across all systems is questionable, as different systems may converge at different rates. Additionally, the RMSD is calculated relative to the first frame, which may not represent an equilibrated state. The authors should provide block analysis, autocorrelation times, or other quantitative convergence metrics for key observables (e.g., hydrogen bond counts, contact numbers, interdomain angles) to demonstrate that the post-equilibration trajectories are stationary.
- **Why it matters** If the trajectories are not fully equilibrated, all quantitative claims about binding energies, contact frequencies, and conformational preferences could be biased by the initial conditions. The 300 ns cutoff removes a substantial fraction of the simulation data, and if this cutoff is not well-justified, the effective sampling may be even more limited than stated.
- **Resolution test** Provide quantitative convergence analysis for key observables, such as block averaging or split-half analysis, demonstrating that the post-equilibration period yields stable estimates. Show that conclusions are robust to the choice of equilibration cutoff (e.g., 200 ns vs 400 ns).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report MM/GBSA binding energies (Table 2) and use these to conclude that "van der Waals interactions drive the stability of the association between the nucleosome core and reader domains."
- **Evidence pointer** Results, Table 2; Materials and methods, Simulation analyses section
- **Concern** The MM/GBSA approach is known to be highly sensitive to the choice of internal dielectric constant, entropy contributions are neglected, and the method has well-documented limitations for protein-nucleic acid complexes. The reported values (e.g., ΔEtotal of -132.8 and -155.9 kcal/mol) are large and likely overestimated in magnitude. The authors acknowledge that "MM/GBSA estimates should be interpreted with caution," but then proceed to draw mechanistic conclusions from these numbers. The comparison between PHD and BPTF systems is also complicated by the different sizes of the binding interfaces. No error estimates beyond standard error of the mean are provided, and the standard errors appear small given the known variability of MM/GBSA calculations.
- **Why it matters** The conclusion that van der Waals interactions dominate binding is a central claim of the manuscript. If the MM/GBSA calculations are not reliable, this conclusion is not established. The authors need to either provide more robust free energy estimates (e.g., with entropy corrections, different internal dielectric constants, or comparison to potential of mean force calculations) or temper their conclusions.
- **Resolution test** Provide MM/GBSA results with different internal dielectric constants (e.g., 1, 2, 4) to show robustness. Include entropy estimates or explicitly state the limitations. Alternatively, use an orthogonal method (e.g., umbrella sampling or metadynamics) to validate the relative binding affinities.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that "BPTF engagement modulates nucleosome structure and may facilitate chromatin remodeling" and that their results "provide insight into the allosteric influence of reader domains within chromatin."
- **Evidence pointer** Abstract; Discussion section
- **Concern** The connection between the observed simulation results and chromatin remodeling is speculative. The authors observe a reduction of 16-17 hydrogen bonds between histones and DNA, increased H3 tail fluctuations, and H4 tail redistribution, but they do not demonstrate that these changes would facilitate nucleosome sliding or remodeling. The timescale of their simulations (1 microsecond) is far too short to observe remodeling events, and they acknowledge this. The claim that these changes "may facilitate" remodeling is not directly testable from their data. The authors should either provide a more concrete mechanistic link (e.g., through comparison with known remodeling mechanisms or through additional simulations with remodeler components) or clearly frame these as hypotheses for future work.
- **Why it matters** The potential to explain how reader proteins contribute to chromatin remodeling is a key motivation for the study. If this connection is not established, the broader significance of the work is diminished. The manuscript would be strengthened by a more careful discussion of what the observed changes might mean for remodeling, without overclaiming.
- **Resolution test** Either provide additional data linking the observed structural changes to remodeling (e.g., through comparison with experimental remodeling assays or through simulations with remodeler components) or revise the discussion to clearly state that the remodeling implications are speculative and require further investigation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "BPTF consistently adopted more compact conformations when bound to the full nucleosome compared to the H3 fragment" and that "nucleosome engagement induces compaction of the multidomain structure."
- **Evidence pointer** Results, BPTF conformations section; Figures 7, S17, S18
- **Concern** The interdomain angle and radius of gyration analyses show broad distributions with substantial overlap between conditions. The authors report shifts in the mode of the distributions, but it is unclear whether these differences are statistically significant given the limited number of independent simulations (5 replicates per condition). The angle measurements rely on a specific definition of the interdomain angle (using centers of mass of selected residues), and it is unclear how sensitive the results are to this choice. Additionally, the authors do not report whether the observed compaction is driven by specific interdomain contacts or by general electrostatic effects.
- **Why it matters** The claim that nucleosome binding induces compaction is a notable finding, but if the effect is small relative to the conformational variability, it may not be biologically meaningful. The authors need to demonstrate that the observed differences are robust and significant.
- **Resolution test** Provide statistical tests comparing the angle and RG distributions across conditions (e.g., Kolmogorov-Smirnov tests or bootstrap confidence intervals). Show that the results are robust to the choice of angle definition and analysis parameters.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors report that "the first six residues preferentially associate with the reader" and that "reader binding excluded the N-terminal H3 tail residues from interacting with nucleosomal DNA."
- **Evidence pointer** Results, Reader binding alters H3 tail conformation section; Figures 2, S5
- **Concern** The contact analysis uses a 4.5-Å cutoff between heavy atoms, which is reasonable, but the authors do not report how sensitive their conclusions are to this cutoff choice. The claim that H3 tail residues are "excluded" from DNA is based on comparing contact counts between unbound and reader-bound systems, but the authors do not report the absolute contact counts or the fraction of time that specific residues are in contact with DNA. The statement that "the first six residues preferentially associate with the reader" is based on the observation that residues H3A1 through H3T6 form 169-175 contacts with the reader, but it is unclear how this compares to the total possible contacts or to the contacts formed by other residues.
- **Why it matters** The competition between reader and DNA for H3 tail binding is a central finding. If the contact analysis is not robust, this conclusion is weakened. The authors should provide more detailed contact analysis, including per-residue contact probabilities and sensitivity to cutoffs.
- **Resolution test** Provide contact maps showing the probability of each H3 residue being in contact with DNA or the reader as a function of time. Show that conclusions are robust to contact cutoff choices (e.g., 3.5 Å, 5.5 Å).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "BPTF adopts distinct conformational states depending on its binding context" but does not provide quantitative information about the magnitude of these differences. The abstract also uses the phrase "localized destabilization of the nucleosome core" without defining what "localized" means in this context.
- **Required correction** Consider adding a quantitative descriptor of the conformational differences (e.g., "a 3.1 Å decrease in radius of gyration") and clarifying what is meant by "localized destabilization."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and methods, System construction
- **Evidence pointer** Materials and methods, System construction section
- **Issue** The description of how the H3 tails were remodeled to extend away from the nucleosome core is brief. The authors state that UCSF Chimera's Modeller interface was used, but do not specify the template structures or the validation of the remodeled tails. The choice to remodel the tails may introduce bias, and the authors should describe how they ensured the remodeled tails are physically reasonable.
- **Required correction** Provide more detail on the remodeling procedure, including the template used, the number of models generated, and the criteria for selecting the final model. Consider showing a comparison of the remodeled tail conformations to experimentally observed tail conformations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and methods, MD simulations
- **Evidence pointer** Materials and methods, MD simulations section
- **Issue** The authors state that hydrogen mass repartitioning was used to enable a 4-fs timestep, but do not specify the SHAKE algorithm settings or the thermostat/barostat coupling parameters. These details are important for reproducibility.
- **Required correction** Provide the full simulation parameters, including SHAKE tolerance, thermostat coupling constant, and barostat coupling constant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the biological implications of the observed H4 tail redistribution is brief. The authors note that H4 tail binding to DNA increases, but do not discuss what this might mean for the recognition of H4 acetylation marks by bromodomains or for the stability of the nucleosome.
- **Required correction** Expand the discussion of the potential functional consequences of H4 tail redistribution, particularly in the context of bromodomain recognition of H4 acetylation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results, BPTF conformations section
- **Evidence pointer** Results, BPTF conformations section; Figure 7
- **Issue** The description of the interdomain angle measurement is difficult to follow without seeing Figure S1. The authors should briefly describe the angle definition in the main text to make the results accessible to readers who do not consult the supplementary material.
- **Required correction** Add a brief description of the angle definition in the main text, or move Figure S1 to the main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, Electrostatic repulsion section
- **Evidence pointer** Results, Electrostatic repulsion section; Table 2
- **Issue** The authors report that the electrostatic penalty is larger for the PHD-bound system (179.7 kcal/mol) than for the BPTF-bound system (134.0 kcal/mol), but do not explain why this might be the case. The difference is not discussed in the text.
- **Required correction** Provide a brief explanation for the difference in electrostatic penalties between the two systems, or acknowledge that the reason is unclear.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the limitations of the study is brief and does not mention the potential limitations of the force field for describing protein-DNA interactions, the absence of post-translational modifications beyond H3K4me3, or the lack of explicit treatment of the nucleosome's dynamic behavior (e.g., breathing).
- **Required correction** Expand the limitations paragraph to address these points.

## Risk / unsupported claims
- The claim that BPTF binding "may facilitate chromatin remodeling" is not directly supported by the data and should be framed as a hypothesis.
- The claim that "van der Waals interactions drive the stability of the association" is based on MM/GBSA calculations that are known to be unreliable for absolute binding energies and should be tempered.
- The claim that "nucleosome engagement induces compaction of the multidomain structure" is based on shifts in distribution modes that may not be statistically significant given the limited sampling.
- The claim that "the first six residues preferentially associate with the reader" is based on contact counts that are not fully contextualized (e.g., compared to total possible contacts or to other residues).
- The statement that "the first 300 ns of each simulation were considered equilibration time" is based on subjective criteria and needs quantitative justification.
- The claim that "these effects are not captured by peptide-based models" is not directly tested in this study, as the authors did not simulate peptide-bound systems with the same analysis protocols for all observables.