## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary material references)
- **Assessment boundary** Scientific soundness, methodological validity, interpretation of results, and alignment with stated claims. No assessment of formatting or editorial style.
- **Shared manuscript claim summary** The authors use steered molecular dynamics (SMD) simulations with multiple replicas to study the mechanical unfolding of the ARNT PAS-B domain. They develop a self-organizing map (SOM) based approach to classify unfolding pathways and identify two distinct pathways, one of which contains a stable intermediate state. They report agreement with prior single-molecule AFM experiments and propose a structural model for the experimentally observed intermediate.
- **Visible evidence base** Abstract, full methods, results, discussion, and references to supplementary figures and tables. Supplementary material itself was not provided.
- **Missing materials affecting confidence** Supplementary figures (S1, S3, S4, S5, S6, S7, S8, S9, S10) and Table S1 are referenced but not available. The structural alphabet analysis methodology is described only in the Supporting Information. Raw simulation data and force-distance curves are not provided.

## Reviewer
- **Overall assessment** The manuscript presents a novel application of SOMs to classify and visualize unfolding pathways from SMD simulations. The approach is well described and the identification of two pathways with a putative intermediate state is potentially valuable. However, the evidence supporting the key claim of agreement with AFM experiments is partially indirect, and the statistical robustness of the pathway classification is not fully established. The structural model for the intermediate state is plausible but requires stronger validation. The work is of interest to the computational biophysics community, though its broader significance depends on the generalizability of the method.
- **Who would be interested in the results, and why** Computational biophysicists and molecular dynamics practitioners interested in protein unfolding mechanisms and pathway analysis. Researchers studying PAS domains and bHLH-PAS transcription factors may find the structural model of the intermediate state useful. Methodologists developing machine learning approaches for trajectory analysis would also be interested in the SOM-based pathway classification strategy.
- **Major strengths** The SOM-based approach for pathway classification is original and clearly described. The use of Cβ contact distances as descriptors is well justified. The identification of two pathways with probabilities comparable to AFM experiments is encouraging. The per-residue energy decomposition analysis provides mechanistic insight into the stability of the intermediate state. The retracing of low-speed simulations on the same SOM is a good consistency check.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical robustness of pathway classification), R1-M2 (quantitative comparison with AFM), R1-M3 (validation of intermediate state model), R1-M4 (force analysis interpretation).
- **Assessment against Nature-style criteria**  
  *Originality*: The SOM-based pathway classification is novel in this context. The application to SMD trajectory analysis is a creative contribution.  
  *Scientific importance*: The work addresses a relevant question about PAS domain unfolding mechanisms. The potential link to signal transmission is interesting but speculative. The importance is moderate, primarily of interest to specialists.  
  *Interdisciplinary readership*: The manuscript is likely to appeal mainly to computational biophysicists and MD practitioners. The broader biological implications are not developed enough to attract a wide interdisciplinary audience.  
  *Technical soundness*: The methods are generally sound, but several concerns about statistical robustness and validation need to be addressed. The force analysis interpretation requires clarification.  
  *Readability for nonspecialists*: The manuscript is clearly written and the SOM concept is explained well. However, some technical details may be challenging for readers unfamiliar with MD simulations or neural network approaches.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical robustness of the pathway classification and quantitative comparison with experimental data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness
- **Claim pointer** The authors claim that SMD simulations can be classified into two distinct unfolding pathways based on SOM mapping and hierarchical clustering of pathway trajectories.
- **Evidence pointer** Results section, "SOM Highlights Different Unfolding Pathways"; Figures 5, S6, S7, S8
- **Concern** The classification of pathways relies on hierarchical clustering of pathway distances, but the statistical significance of the two-cluster solution is not assessed. The dendrogram (Figure S8) shows additional small branches (pathways 1b and 2b) that are grouped into the main pathways based on "similarity in the first part of the unfolding process." This grouping appears subjective. No quantitative measure of cluster separation or stability (e.g., bootstrap analysis, silhouette values for pathway clusters) is provided.
- **Why it matters** The central claim of two distinct pathways is the foundation of the manuscript. If the classification is not statistically robust, the comparison with AFM data and the proposed intermediate state model are weakened. The manual grouping of sub-pathways undermines the objectivity of the approach.
- **Resolution test** Provide quantitative assessment of pathway clustering, such as bootstrap support for the dendrogram branches, silhouette widths for the pathway clusters, or an alternative clustering validation method. Justify the merging of sub-pathways with explicit criteria rather than visual similarity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative comparison with experiment
- **Claim pointer** The authors state that the two identified pathways are "in good agreement with the AFM findings" and that the intermediate state in pathway 1 has an extension consistent with the experimentally observed intermediate.
- **Evidence pointer** Results section, "SOM Highlights Different Unfolding Pathways"; Discussion; Figure 9
- **Concern** The comparison with AFM experiments is qualitative. The experimental intermediate was reported at 10.5 nm extension, while the authors report 9.4 ± 1.0 nm for neuron 41. The uncertainty range overlaps with the experimental value, but no statistical comparison is made. The probability distribution of pathways (24% vs 76%) is compared to experimental values (33% vs 67%), but no error bars or confidence intervals are provided for the simulation-derived probabilities. The AFM experiments also measured forces, but no comparison of force magnitudes is presented.
- **Why it matters** The claim of agreement with experiment is a key validation of the simulation approach. Without quantitative comparison, the reader cannot assess whether the agreement is meaningful or coincidental. The intermediate state model is presented as a possible structural interpretation of the AFM data, but the evidence linking the two is circumstantial.
- **Resolution test** Provide a quantitative comparison between simulation and experiment, including statistical measures of agreement for pathway probabilities and intermediate extension. If force data are available from AFM, compare simulated and experimental force profiles or peak forces. Discuss the limitations of the comparison given the different pulling speeds and loading rates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of intermediate state model
- **Claim pointer** The authors propose that conformations in neuron 41 represent a stable intermediate state along pathway 1, characterized by a split domain with two folded lobes.
- **Evidence pointer** Results section, "SOM Highlights Different Unfolding Pathways"; Figure 9; Figure S10
- **Concern** The identification of neuron 41 as an intermediate state is based on the observation of high average forces in cluster C and the structural features of the conformations. However, no free energy calculations or equilibrium simulations are provided to support the claim of stability. The per-residue energy decomposition analysis identifies stabilizing interactions, but this is not a measure of thermodynamic stability. The authors do not demonstrate that the intermediate state is kinetically accessible or that it represents a local free energy minimum.
- **Why it matters** The claim of a stable intermediate is central to the biological interpretation. Without thermodynamic or kinetic evidence, the "intermediate" could be a transient, non-equilibrium artifact of the SMD pulling protocol. The structural model may be misleading if it is presented as a physiologically relevant state.
- **Resolution test** Perform additional simulations or analyses to support the stability of the intermediate, such as equilibrium MD simulations starting from the intermediate conformation, free energy calculations (e.g., umbrella sampling or metadynamics), or analysis of the force spectra for signatures of a stable state. Alternatively, temper the claims to describe the intermediate as a "putative" state that requires further validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Force analysis interpretation
- **Claim pointer** The authors map average forces on the SOM and interpret high forces in cluster C as evidence of an unfolding barrier and intermediate state.
- **Evidence pointer** Results section, "SOM Highlights Different Unfolding Pathways"; Figure 8
- **Concern** The average force per neuron is calculated over frames belonging to that neuron, but the relationship between force and conformational state is not straightforward in SMD. High forces can arise from various factors, including pulling speed, linker stiffness, and non-equilibrium effects. The authors do not discuss how the force values depend on the pulling protocol or whether the force peaks are statistically significant across replicas. The interpretation of high forces as evidence of a barrier is plausible but not rigorously established.
- **Why it matters** The force analysis is used to support the existence of an intermediate state. If the force interpretation is flawed, the evidence for the intermediate is weakened. The manuscript should clarify what the force measurements represent and how they relate to the free energy landscape.
- **Resolution test** Provide a more detailed analysis of the force data, including force-distance curves for individual replicas, statistical analysis of force peaks across replicas, and discussion of how the pulling protocol affects the force measurements. Consider whether alternative explanations for high forces (e.g., solvent effects, entropic elasticity) can be ruled out.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** SOM training parameters
- **Evidence pointer** Methods section, "Self-Organizing Maps"
- **Issue** The manuscript states that an 8 × 8 SOM was used but does not provide details on the training parameters (e.g., learning rate, neighborhood function, number of training iterations, initialization method). The choice of these parameters can affect the resulting map and the classification of pathways.
- **Required correction** Provide the full training parameters or cite the software defaults. If different parameter sets were tested, describe the selection criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Simulation setup
- **Evidence pointer** Methods section, "Steered MD Simulations"
- **Issue** The pulling velocity is given as 0.2 nm/ns, but the spring constant is not explicitly stated in the main text. The force constant is mentioned as 500 kJ mol⁻¹ nm⁻², but the pulling rate and spring constant together determine the loading rate, which is critical for interpreting SMD results.
- **Required correction** State the spring constant explicitly in the main text and discuss the loading rate in the context of the AFM experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Pathway probabilities
- **Evidence pointer** Results section, "SOM Highlights Different Unfolding Pathways"
- **Issue** The authors report that pathway 2 was sampled in 74% of replicas, but the number of replicas is 50, so this corresponds to 37 replicas. The low-speed simulations (10 replicas) show 6 pathway 1 and 4 pathway 2, which is a different ratio. The authors note this is expected due to limited sampling, but no statistical analysis is provided.
- **Required correction** Provide confidence intervals for the pathway probabilities or discuss the statistical power of the comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Structural alphabet analysis
- **Evidence pointer** Results section, "Mapping Conformations Sampled by Steered MD on SOM"; Figure S5
- **Issue** The structural alphabet analysis is mentioned as identifying local patterns of unfolding, but the methodology is only described in the Supporting Information. The main text does not explain what the structural alphabet is or how the profiles were calculated.
- **Required correction** Provide a brief description of the structural alphabet method in the main text or move the essential details from the Supporting Information to the main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Biological implications
- **Evidence pointer** Discussion
- **Issue** The authors suggest that the unfolding pathways may be relevant to signal transmission mechanisms in bHLH-PAS transcription factors, but this connection is speculative and not developed. The discussion would benefit from a more explicit statement of how the mechanical unfolding relates to the proposed functional mechanisms.
- **Required correction** Either provide a more detailed discussion of the functional implications or temper the claims to avoid overinterpretation.

## Risk / unsupported claims
- The claim that the two identified pathways are "in good agreement with the AFM findings" is not quantitatively supported. The comparison is qualitative and lacks statistical rigor.
- The identification of neuron 41 as a "stable intermediate state" is not supported by thermodynamic or kinetic evidence. The term "stable" is used without free energy calculations or equilibrium simulations.
- The statement that the approach "will facilitate the study of other signal transmission mechanisms involving the folding/unfolding of PAS domains" is speculative and not directly supported by the results presented.
- The claim that the pulling speed of 0.2 nm/ns "is still able to capture lower energy pathways" is based on the comparison of work values, but the statistical significance of this comparison is not established.
- The biological relevance of the identified intermediate state to the function of bHLH-PAS transcription factors is not demonstrated and remains a hypothesis.