## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supporting information references.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with stated conclusions. Editorial quality and formatting are considered only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors use weighted ensemble (WE) molecular dynamics simulations and ZZ-exchange NMR to characterize the unbinding pathway of the small-molecule ligand THS-017 from the buried cavity of the HIF-2α PAS-B domain. They identify two distinct unbinding pathway classes, propose two pairs of gating residues (N288/S304 for the major class, L272/M309 for the minor class), and validate the kinetic importance of N288 through mutagenesis and NMR experiments.
- **Visible evidence base** Simulation results (pathway clustering, committor analysis, contact maps), ITC binding data, ZZ-exchange NMR rate measurements, and HSQC spectra for wild-type and mutant proteins.
- **Missing materials affecting confidence** Full simulation trajectory data (only most probable pathways are publicly available), detailed analysis of the encounter complex structure, quantitative comparison of simulated and experimental rates beyond order-of-magnitude, and raw NMR fitting parameters.

## Reviewer
- **Overall assessment** This manuscript presents a technically sophisticated combination of enhanced sampling simulations and NMR experiments to address a biologically and pharmacologically relevant question: how ligands exit a buried protein cavity. The WE approach is well-suited for this rare-event problem, and the identification of specific gating residues with experimental validation is a notable advance. However, several concerns regarding the quantitative rigor of the kinetic comparisons, the robustness of the pathway classification, and the generalizability of the conclusions need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers in computational biophysics and drug discovery, particularly those studying ligand binding kinetics, cryptic pocket dynamics, and residence time prediction. The methodological demonstration of WE simulations for a seconds-timescale process will interest method developers. The specific findings on HIF-2α may inform ongoing drug development efforts targeting this protein.
- **Major strengths** 1) The combination of unbiased WE simulations with experimental NMR validation is powerful and rare in this field. 2) The identification of specific gating residues with clear mechanistic hypotheses is actionable for future studies. 3) The authors are transparent about the limitations of their force field and simulation setup. 4) The public availability of simulation inputs and most probable pathways is commendable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative kinetic comparison), R1-M2 (pathway classification robustness), R1-M3 (encounter complex characterization).
- **Assessment against Nature-style criteria** **Originality**: High. The application of WE to a buried cavity ligand unbinding problem with experimental validation is novel. **Scientific importance**: Moderate to high. The findings have implications for understanding ligand residence times in a clinically relevant target, but the generalizability to other systems is not yet demonstrated. **Interdisciplinary readership**: Moderate. The work bridges computational chemistry and structural biology, but the technical depth may limit broader appeal. **Technical soundness**: Generally sound, but with concerns about quantitative kinetic comparisons and pathway classification robustness. **Readability for nonspecialists**: The abstract and introduction are accessible, but the methods and some results sections are highly technical. The manuscript would benefit from clearer explanations of the WE method and its significance for a general audience.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the quantitative kinetic comparison and pathway classification robustness.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor of kinetic comparison
- **Claim pointer** The authors state that their simulated k_off (1.3 × 10^4 to 8.7 × 10^4 s^-1) is "three orders of magnitude higher than the experimental value (1.4 ± 0.3 s^-1)" and attribute this to the force field causing the cavity to open too quickly.
- **Evidence pointer** Results section, Figure S2, Table S4
- **Concern** The three-order-of-magnitude discrepancy between simulated and experimental k_off is substantial. While the authors acknowledge this and attribute it to force field limitations, this discrepancy undermines the quantitative predictive power of the simulations. The claim that the force field "is likely opening the cavity too quickly" is speculative without direct evidence, such as a comparison of cavity opening rates or free energy barriers between simulation and experiment. Furthermore, the experimental k_off values are derived from ZZ-exchange NMR, which measures k_ex (sum of on and off rates) and requires deconvolution using K_d from ITC. The error propagation in this deconvolution is not discussed.
- **Why it matters** The central claim of the paper is that the simulations reveal the mechanism of ligand unbinding. If the simulated kinetics are off by three orders of magnitude, the relevance of the simulated pathways to the actual experimental process is questionable. The authors need to provide stronger evidence that the simulated pathways are representative of the true unbinding process, despite the kinetic discrepancy.
- **Resolution test** Provide a more detailed analysis of the source of the kinetic discrepancy, such as comparing free energy barriers from simulation with those inferred from experimental rates. Alternatively, demonstrate that the simulated pathways are robust to force field modifications or that the relative rates of the two pathway classes are consistent with experimental observations. A quantitative comparison of the simulated and experimental encounter complex populations would also strengthen the case.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Robustness of pathway classification
- **Claim pointer** The authors claim to have identified two distinct pathway classes for ligand unbinding, with pathway class 1 being the major route (63%) and pathway class 2 the minor route (37%).
- **Evidence pointer** Results section, Figure 2b, Figure S3
- **Concern** The pathway classification is based on clustering of ligand exit points using the LPATH method. The choice of the six residues used for discretization (K253, A277, F280, S292, G305, L310) appears somewhat arbitrary, and it is unclear how sensitive the classification is to this choice. The manuscript does not report the robustness of the clustering, such as the silhouette score or the stability of the two clusters across different parameter choices. Additionally, the 63%/37% split is based on the number of pathways, not weighted by their probability or flux. A more meaningful metric would be the fraction of total probability flux through each pathway class.
- **Why it matters** The identification of two distinct pathway classes is a key finding of the paper. If the classification is not robust, the subsequent analysis of gating residues for each class may be misleading. The authors need to demonstrate that the two classes are genuinely distinct and that the assignment of pathways to each class is reliable.
- **Resolution test** Perform a sensitivity analysis of the clustering, varying the choice of residues and the clustering parameters. Report the probability flux through each pathway class, not just the number of pathways. Provide a statistical measure of cluster separation, such as the silhouette score.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Encounter complex characterization
- **Claim pointer** The authors state that the simulations reveal the formation of a metastable encounter complex intermediate, which is the first step in the unbinding mechanism.
- **Evidence pointer** Results section, Figure 2a, Figure S5
- **Concern** The encounter complex is defined as a state with ligand unbinding RMSD between 12 and 17 Å and a ligand-receptor distance <2.5 Å. This definition is based on geometric criteria, but the manuscript does not provide a detailed structural characterization of this intermediate. What are the specific contacts between the ligand and the receptor in the encounter complex? How long does the system reside in this state? Is the encounter complex observed in all three independent WE simulations? The manuscript would benefit from a more detailed analysis of this intermediate state, including representative structures and a comparison with the experimental encounter complex, if any.
- **Why it matters** The encounter complex is a key mechanistic finding, and its characterization is important for understanding the unbinding process. Without a detailed structural description, it is difficult to assess the biological relevance of this intermediate or to design experiments to probe it.
- **Resolution test** Provide representative structures of the encounter complex, a contact map between the ligand and receptor in this state, and a residence time distribution. If possible, compare the encounter complex with any experimentally characterized intermediates.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Materials and Methods, WE simulation details
- **Evidence pointer** Section 4.1
- **Issue** The description of the WE simulation setup is dense and lacks some details that would be important for reproducibility. For example, the exact number of bins in each dimension of the progress coordinate, the target number of trajectories per bin, and the criteria for determining convergence are not fully specified.
- **Required correction** Provide a more detailed description of the WE simulation parameters, including the binning scheme, target trajectory counts, and convergence criteria. Consider adding a table summarizing the simulation parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Results, ITC and NMR data
- **Evidence pointer** Table S2, Table S3, Table S4
- **Issue** The ITC and NMR data are presented with standard deviations, but the number of replicates is not stated. It is unclear whether the reported errors are from duplicate or triplicate measurements, and whether the fitting procedures account for all sources of error.
- **Required correction** State the number of independent replicates for each measurement and describe the error analysis in more detail.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The authors acknowledge the force field limitation but do not discuss other potential sources of error, such as the choice of water model, the truncation of the system, or the use of a single ligand (THS-017). A more comprehensive discussion of limitations would strengthen the manuscript.
- **Required correction** Add a paragraph discussing the potential impact of force field choice, water model, and system size on the results. Consider discussing whether the findings are likely to generalize to other ligands.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 2
- **Evidence pointer** Figure 2
- **Issue** The figure is informative but somewhat cluttered. The labels for the two pathway classes are not immediately clear, and the color scheme could be improved for accessibility.
- **Required correction** Consider simplifying the figure, using clearer labels for the pathway classes, and ensuring the color scheme is accessible to color-blind readers.

## Risk / unsupported claims
- The claim that the force field "is likely opening the cavity too quickly" is speculative and not directly supported by the data presented.
- The claim that the two pathway classes are "distinct" is not fully supported without a robustness analysis of the clustering.
- The claim that the encounter complex is "metastable" is based on geometric criteria but lacks a detailed kinetic or thermodynamic characterization.
- The generalizability of the findings to other ligands (e.g., belzutifan) is discussed but not tested, and should be framed as a hypothesis rather than a conclusion.
- The statement that the WE simulations provide "rigorous kinetics" is somewhat undermined by the three-order-of-magnitude discrepancy with experiment, and the authors should temper this claim.