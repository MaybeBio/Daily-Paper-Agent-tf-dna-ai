## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusions) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodological soundness, and claims as presented in the provided text; no supplementary figures or data were available for inspection
- **Shared manuscript claim summary** The authors use equilibrium MD and umbrella sampling simulations to characterize the gate-opening mechanism of M. smegmatis topoisomerase 1A, identifying key electrostatic interactions stabilizing the closed state, three major domain motions during opening, and free energy profiles for the process
- **Visible evidence base** Main text figures referenced (Figures 1-8), methods descriptions, and results narrative; supplementary figures mentioned but not provided
- **Missing materials affecting confidence** Supplementary figures (1-7), supplementary tables, supplementary notes, simulation input files, force field parameters, and raw trajectory data were not available for review

## Reviewer
- **Overall assessment** This manuscript presents a computational study of the gate-opening mechanism in M. smegmatis topoisomerase 1A using equilibrium MD and umbrella sampling simulations. The work addresses a genuinely important and challenging problem: the transient nature of the open state has made experimental characterization difficult, and computational approaches are well suited to provide mechanistic insight. The authors identify specific electrostatic interactions that stabilize the closed state, describe three major domain motions during opening, and present free energy profiles. However, the manuscript has several significant weaknesses that currently prevent the case from being fully established. The methods section lacks critical details on system preparation, equilibration protocols, and umbrella sampling parameters. The free energy calculations are presented without convergence analysis or error estimates. The relationship between the simulated open state and the experimentally observed open conformation is not rigorously established. The biological significance claims, particularly regarding drug design, are speculative and not directly supported by the data presented. The manuscript would benefit from a more careful and complete presentation of the computational methodology and a more measured interpretation of the results.

- **Who would be interested in the results, and why** Researchers studying topoisomerase mechanisms, particularly type 1A topoisomerases, would find this work relevant. The study also has potential interest for computational biophysicists working on conformational transitions in large protein-DNA complexes. Given the drug target status of mycobacterial topoisomerases, investigators in antibacterial drug discovery may find the identified electrostatic interactions and domain motions useful for structure-based design efforts. However, the current presentation is primarily of interest to a specialized audience of topoisomerase researchers and MD practitioners.

- **Major strengths** The study addresses a biologically important and technically challenging problem: characterizing a transient conformational state that has been difficult to observe experimentally. The use of umbrella sampling to bias the system toward the open state is an appropriate and potentially powerful approach. The identification of specific electrostatic interactions that stabilize the closed state provides testable hypotheses for mutagenesis experiments. The comparison with experimental structures and single-molecule measurements helps contextualize the simulation results. The authors' observation that ssDNA binding lowers the free energy barrier for gate opening is an interesting finding that could have mechanistic implications.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have reconstructed free energy profiles of gate opening using umbrella sampling combined with WHAM, and present these as quantitative results in Figure 6(F)
- **Evidence pointer** Methods section, Results section, Figure 6(F)
- **Concern** The manuscript does not provide sufficient details on the umbrella sampling protocol to assess the validity of the free energy calculations. Critical information is missing, including the number of windows, the spacing between windows, the total simulation time per window, the convergence criteria used, and whether the simulations were run in duplicate or triplicate. Furthermore, no error bars or statistical uncertainties are presented for the free energy profiles. The WHAM analysis requires careful assessment of overlap between adjacent windows and convergence of the weighted histograms, none of which is described or demonstrated.
- **Why it matters** Free energy profiles are central to the manuscript's claims about the energetics of gate opening. Without demonstrated convergence and error analysis, the quantitative free energy barriers and the comparison between apo and ssDNA-bound systems cannot be evaluated. The claim that ssDNA lowers the barrier is a key finding, but it cannot be assessed without proper statistical treatment.
- **Resolution test** The authors should provide a complete description of the umbrella sampling protocol, including the number of windows, simulation lengths, and convergence analysis. They should show histogram overlap plots, time evolution of the free energy estimates, and provide error bars on the final profiles. Ideally, independent replicate simulations should be performed to assess statistical uncertainty.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the gate opening comprised of three major domain motions that were determined from simulation trajectories and Principal Component Analysis" and identify these as (a) detachment and downward motion of D1 away from D3, (b) detachment of D3 from the D1+D4 interface, and (c) swiveling of D3 out of the plane of the protein
- **Evidence pointer** Results section, Figure 7, Supplementary Figure 7, Supplementary Note 1
- **Concern** The PCA methodology is described only briefly, and the criteria for identifying the "top three components" as the major functional motions are not fully justified. The claim that these components describe "most of the fluctuations of the system (>85%)" is referenced to supplementary material that was not provided for review. More importantly, the manuscript does not demonstrate that these PCA-derived motions are functionally relevant to gate opening as opposed to being dominant thermal fluctuations. The overlap between components across different simulations is mentioned but not quantified in the main text.
- **Why it matters** The identification of specific domain motions is a central result of the study. If the PCA is not properly validated, the mechanistic interpretation of gate opening could be incorrect. The claim that these are the "major functional motions" requires more rigorous support, including comparison with the free energy calculations and demonstration that these motions are coupled to the reaction coordinate.
- **Resolution test** The authors should provide a more detailed description of the PCA methodology, including how the covariance matrix was constructed, how many trajectories were used, and how the components were validated. They should show the cumulative variance explained by the top components and demonstrate that the identified motions are indeed coupled to the reaction coordinate. Ideally, the PCA results should be compared with an independent method for identifying functional motions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "several electrostatic interactions contribute to the closed-state stability of the protein which were broken during the gate opening" and identify specific residue pairs including K537-E322, R377/K380-E522/E523/D583, and K25/K28-E333
- **Evidence pointer** Results section, Figures 4 and 5, Supplementary Figures 1-3
- **Concern** The interaction energy calculations are described as using the VMD NAMDEnergy plugin with a dielectric constant of 70, but the manuscript does not explain why this particular dielectric constant was chosen or how the results depend on this choice. The use of a distance-dependent or constant dielectric is a significant approximation that can substantially affect the calculated interaction energies. Furthermore, the manuscript does not provide a clear definition of which residue pairs were considered "contacts" and how the cutoff criteria were determined. The time evolution of interaction energies is shown, but the statistical significance of differences between apo and ssDNA-bound systems is not assessed.
- **Why it matters** The identification of specific electrostatic interactions that stabilize the closed state is a key finding that could guide mutagenesis experiments. If the interaction energy calculations are not robust to the choice of dielectric constant or other parameters, the specific residue pairs identified may not be reliable. The claim that these interactions are important for closed-state stability requires more rigorous validation.
- **Resolution test** The authors should justify their choice of dielectric constant and show that the identified interactions are robust to reasonable variations in this parameter. They should provide a clear definition of what constitutes a "contact" and demonstrate that the interaction energy differences between apo and ssDNA-bound systems are statistically significant. Ideally, the results should be validated with more accurate electrostatic treatments or compared with experimental mutagenesis data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "Results of this study provide mechanistic details of gate opening. This information furthers the understanding of the topoisomerase catalytic cycle which will aid in anti-topoisomerase drug design efforts."
- **Evidence pointer** Abstract, Significance statement, Conclusions
- **Concern** The drug design implications are stated prominently but are not directly supported by the data presented. The study identifies electrostatic interactions and domain motions, but does not demonstrate how this information could be used to design inhibitors that trap the open state. The connection between the simulation results and drug design is speculative and not developed in the manuscript.
- **Why it matters** The significance statement and abstract emphasize the drug design implications, which may overstate the direct applicability of the findings. If the drug design claims are not supported, the broader significance of the work may be overstated.
- **Resolution test** The authors should either provide a more concrete discussion of how the identified interactions and motions could be targeted by small molecules, or temper the drug design claims to match what is directly supported by the data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the system with ssDNA present at the active site has lower barrier heights than the apo system" and that "binding of the ssDNA highly affects the initial detachment of D1 from D3"
- **Evidence pointer** Results section, Figure 6(F), Supplementary Figures 1 and 2
- **Concern** The comparison between apo and ssDNA-bound systems is complicated by the fact that the starting structures for these systems are different, and the equilibration protocols may not have produced equivalent starting states for the umbrella sampling simulations. The manuscript does not describe how the systems were equilibrated to ensure that the comparison is meaningful. Additionally, the free energy profiles are presented without error bars, making it impossible to assess whether the observed differences between apo and ssDNA-bound systems are statistically significant.
- **Why it matters** The claim that ssDNA binding lowers the free energy barrier for gate opening is an important mechanistic finding. If this claim is not statistically robust, the interpretation of the results could be incorrect.
- **Resolution test** The authors should provide error bars on the free energy profiles and demonstrate that the differences between apo and ssDNA-bound systems are statistically significant. They should also describe how the systems were prepared to ensure that the comparison is meaningful.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section
- **Evidence pointer** Methods section, "For gate opening, simulations were run using the biasing technique Umbrella Sampling(US)"
- **Issue** The methods section contains incomplete sentences and missing mathematical notation. For example, the sentence describing the angle calculation between unit vectors is incomplete, and the equation for the restraining potential is not fully written out.
- **Required correction** The methods section should be carefully edited to ensure all sentences are complete and all mathematical expressions are properly formatted.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, system preparation
- **Evidence pointer** Methods section, "Missing residues within the truncated protein structure were modeled using Modeller via ChimeraX"
- **Issue** The manuscript does not specify which residues were missing from the crystal structure or how many models were generated. The criteria for selecting the best model (lowest z-DOPE score) are mentioned, but the quality of the final model is not assessed.
- **Required correction** The authors should specify which residues were modeled and provide some assessment of the model quality, such as Ramachandran plot statistics or comparison with the crystal structure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, simulation parameters
- **Evidence pointer** Methods section, "All MD simulations were atomistic in scale and run using NAMD 2.14 or NAMD 3.0"
- **Issue** The manuscript does not specify the integration time step, the thermostat and barostat parameters, or the frequency of trajectory saving. These details are important for reproducibility.
- **Required correction** The authors should provide complete simulation parameters, including time step, thermostat/barostat settings, and trajectory saving frequency.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section, Figure 6(F)
- **Evidence pointer** Results section, "US and WHAM generate free energies for the gate opening process"
- **Issue** The description of the free energy curves in Figure 6(F) is somewhat confusing. The authors refer to "red vs blue dash-dotted curves" and "solid blue curve" without clearly explaining which system each curve corresponds to.
- **Required correction** The figure legend and text should clearly identify which curve corresponds to which system and simulation condition.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion of biological implications
- **Evidence pointer** Conclusions section
- **Issue** The conclusions section is relatively brief and does not fully discuss the implications of the findings in the context of the broader topoisomerase literature. The relationship between the simulated open state and the experimentally observed open conformation of human Top3 beta is mentioned but not developed.
- **Required correction** The authors should expand the discussion to more thoroughly contextualize their findings within the existing experimental and computational literature on type 1A topoisomerases.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, sequence alignment
- **Evidence pointer** Methods section, "NCBI Blast was used for multiple sequence alignment"
- **Issue** The manuscript does not specify which sequences were aligned or how the conservation percentages in Figure 4(D) were calculated.
- **Required correction** The authors should specify the sequences used for alignment and the method for calculating conservation percentages.

## Risk / unsupported claims
- The claim that ssDNA binding lowers the free energy barrier for gate opening is not supported by statistical analysis, as no error bars are provided on the free energy profiles
- The claim that the identified electrostatic interactions are important for closed-state stability is based on calculations with a specific dielectric constant (70) that is not justified or tested for robustness
- The claim that the three PCA-derived motions are the "major functional motions" of gate opening is not rigorously validated
- The drug design implications stated in the abstract and significance statement are speculative and not directly supported by the data
- The relationship between the simulated open state and the experimentally observed open conformation of human Top3 beta is asserted but not quantitatively compared
- The claim that the unstructured loop may have a regulatory role is speculative and not directly tested in this study
- The statement that "the gate is considered open when D1 residues detach from D3" is a definition chosen by the authors and is not validated against experimental measurements of gate opening