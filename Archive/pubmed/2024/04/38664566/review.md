## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure legends
- **Assessment boundary** Scientific validity, technical rigor, and conceptual advance of the claims presented; no assessment of editorial fit or formatting
- **Shared manuscript claim summary** The authors investigate how the Drosophila ISWI chromatin remodeler functions in condensed nucleosome arrays. They report that chromatin fiber folding does not impede nucleosome sliding, that ISWI can enter and function within chromatin condensates, that ATP hydrolysis is required for ISWI mobility in condensates and prevents ISWI-mediated crosslinking/stiffening, and propose a "monkey bar" model for processive movement through dense chromatin.
- **Visible evidence base** Main figures 1-6, Extended Data figures 1-6, methods descriptions, simulation details
- **Missing materials affecting confidence** Raw source data files, full uncropped gel images, complete simulation parameter tables, detailed statistical analysis for some comparisons, and the supplementary movies referenced in the text

## Reviewer

- **Overall assessment** This manuscript addresses a fundamental and timely question: how chromatin remodeling enzymes function in condensed chromatin environments. The authors combine biochemical reconstitution, advanced imaging (FLIM-FRET), biophysical approaches (optical tweezers, holotomography), and coarse-grained simulations to build a compelling case that ISWI retains activity in condensed arrays and that ATP hydrolysis powers a "monkey bar" mechanism for diffusion. The work is technically ambitious and the conclusions are largely supported by the data presented. However, several concerns regarding quantitative rigor, alternative interpretations, and the generalizability of the model require attention before the case is fully established.

- **Who would be interested in the results, and why** Chromatin biologists studying remodeling enzymes, biophysicists interested in enzyme dynamics in crowded/condensed environments, researchers studying phase separation and biomolecular condensates, and those interested in the physical properties of chromatin in vivo. The work bridges chromatin biochemistry and phase separation biology, making it relevant to a broad readership.

- **Major strengths** 
  1. The study addresses a previously unexplored question with direct physiological relevance.
  2. The combination of multiple orthogonal techniques (biochemistry, imaging, biophysics, simulation) provides convergent evidence.
  3. The FLIM-FRET assay for measuring nucleosome sliding inside condensates is a novel and powerful methodological advance.
  4. The "monkey bar" model is conceptually elegant and provides a testable framework for future work.
  5. The authors carefully control for Mg2+ effects on ATPase activity, strengthening the conclusion that condensation itself does not impede remodeling.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor of rate comparisons
- **Claim pointer** "Condensation, however, is not the major cause of this drop in the activity, as the higher Mg2+ concentration also reduced the ATPase activity in presence of mononucleosomes to a similar extent"
- **Evidence pointer** Figure 2d, Extended Data Figure 1b, Extended Data Figure 2c
- **Concern** The authors compare remodeling rates in solution versus condensates and attribute the ~8-fold reduction to Mg2+ effects on ATPase activity rather than condensation per se. However, the comparison relies on ATPase measurements with mononucleosomes at different Mg2+ concentrations, while the remodeling assays use nucleosome arrays. The relationship between bulk ATPase activity and the rate of nucleosome sliding is not necessarily linear, and the authors do not directly measure ATPase activity under condensate conditions with arrays. The conclusion that condensation poses "no substantial barrier" may be overstated given that a 2.6-fold reduction in sliding rate is still observed when comparing condensates to solution at the same Mg2+ concentration (Figure 3d).
- **Why it matters** The central claim of the paper is that ISWI functions largely unimpeded in condensed environments. If the rate comparison is not rigorously controlled, this conclusion is weakened.
- **Resolution test** Directly measure ATPase activity of ISWI on nucleosome arrays under both solution and condensate conditions at matched Mg2+ concentrations. Alternatively, perform remodeling assays at varying Mg2+ concentrations in solution to establish a quantitative relationship between ATPase rate and sliding rate, then use this to predict expected sliding rates in condensates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Alternative interpretation of FRAP data
- **Claim pointer** "ATP hydrolysis is required not only for productive remodeling, but also to ensure rapid diffusion of ISWI within condensates"
- **Evidence pointer** Figure 4b, Extended Data Figure 4a,b
- **Concern** The FRAP experiments show that ISWI is immobile without ATP and mobile with ATP. However, an alternative interpretation is that ATP hydrolysis is required for ISWI to release from nucleosomes at all (i.e., the ATPase cycle gates release), rather than a specific "monkey bar" mechanism where the enzyme actively moves along nucleosomes. The authors' model predicts that ISWI remains bound to chromatin at all times during diffusion, but the FRAP data cannot distinguish between (a) ISWI hopping between nearby nucleosomes while remaining bound, and (b) ISWI undergoing rounds of complete dissociation and rebinding. The distinction matters for the mechanistic model proposed.
- **Why it matters** The "monkey bar" model is a key conceptual contribution. If the data equally support a simpler "bind-release-rebind" mechanism, the novelty of the model is reduced.
- **Resolution test** Perform single-molecule tracking of ISWI in condensates to determine whether the enzyme remains continuously associated with chromatin during diffusion, or use FRAP with different-sized bleached regions to distinguish between diffusion modes. Alternatively, test whether ISWI mutants that cannot hydrolyze ATP but can still bind nucleosomes show any mobility.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the model
- **Claim pointer** "We speculate that 'monkey-bar' mechanisms could be shared with other chromatin factors"
- **Evidence pointer** Discussion section
- **Concern** The authors speculate that the monkey bar mechanism may be shared with other chromatin factors, but provide no direct evidence for this. The ISWI ATPase cycle has specific features (e.g., the role of the HSS domain, the specific nucleotide-state dependencies) that may not generalize. The speculation is presented without sufficient caveats about the unique features of ISWI.
- **Why it matters** Overgeneralization could mislead the field about the universality of this mechanism.
- **Resolution test** Soften the speculation or provide specific predictions that could be tested in other remodeler systems. Alternatively, cite specific structural or biochemical features that are conserved across remodeler families and would support the generalization.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Simulation model validation
- **Claim pointer** "Molecular dynamics simulations of a 'monkey-bar' model... qualitatively agree with our data"
- **Evidence pointer** Figure 6, Extended Data Figure 6
- **Concern** The simulations are described as "qualitative" agreement, but the authors do not provide a systematic comparison between simulation and experiment. The simulation parameters (e.g., interaction strengths, off-rates) are chosen to reproduce the experimental observations, raising concerns about circularity. The authors acknowledge technical constraints but do not provide a sensitivity analysis showing that the qualitative conclusions are robust to parameter choices.
- **Why it matters** The simulation is used to support the mechanistic model. If the conclusions are sensitive to parameter choices, the support is weakened.
- **Resolution test** Provide a sensitivity analysis showing that the qualitative conclusions (e.g., ATP-dependent mobility, prevention of stiffening) hold across a range of reasonable parameter values. Alternatively, make falsifiable predictions from the model that could be tested experimentally.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 3d
- **Evidence pointer** Figure 3d
- **Issue** The initial velocities for nucleosome sliding inside condensates (0.77±0.06 s-1) and in solution (2.15±0.15 s-1) are reported as mean ± SD, but the number of independent replicates and the statistical test used for comparison are not stated.
- **Required correction** Report the number of independent experiments and the statistical test used (e.g., t-test, Mann-Whitney) with the resulting p-value.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** FLIM-FRET assay
- **Evidence pointer** Figure 3, Methods
- **Issue** The FLIM-FRET assay is a key methodological advance, but the methods section does not fully describe how the FRET efficiency is calibrated to nucleosome sliding distance. The relationship between donor lifetime and the position of the nucleosome on the DNA construct is not explicitly stated.
- **Required correction** Add a brief description of the calibration procedure, including how the FRET efficiency changes with nucleosome position and how the initial velocity is extracted from the lifetime changes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2b
- **Evidence pointer** Figure 2b
- **Issue** The partition coefficients for dextrans of different molecular weights are shown, but the error bars and number of replicates are not described in the figure legend.
- **Required correction** Add the number of independent measurements and the type of error bars (SD, SEM, etc.) to the figure legend.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of dextran exclusion data
- **Affected element** Figure 2b
- **Evidence pointer** Figure 2b
- **Issue** The authors use dextran exclusion to estimate the pore size of the condensates, but the relationship between dextran molecular weight and pore size is indirect and depends on the shape and flexibility of the dextran molecules. The authors do not discuss this limitation.
- **Required correction** Add a brief discussion of the limitations of using dextran exclusion to estimate pore sizes, and consider whether the conclusions about ISWI accessibility would change with different pore size estimates.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Optical tweezers experiments
- **Evidence pointer** Methods, Figure 5
- **Issue** The optical tweezers fusion experiments are described, but the trap stiffness calibration, the force threshold for determining fusion onset, and the criteria for excluding events are not fully described.
- **Required correction** Provide additional details on the trap calibration and the data analysis pipeline for the fusion experiments.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity of the model
- **Affected element** Figure 6a
- **Evidence pointer** Figure 6a, Extended Data Figure 6a
- **Issue** The schematic of the "monkey bar" model is clear, but the relationship between the model states and the specific nucleotide states of ISWI (ATP, ADP-Pi, ADP, apo) is not fully annotated. The reader is left to infer which states correspond to "strong" and "weak" binding.
- **Required correction** Add explicit labels to the model schematic indicating which nucleotide states correspond to which binding affinities.

## Risk / unsupported claims
1. The claim that "condensation poses no substantial barrier for remodeling" is not fully supported by the quantitative comparison, as the 2.6-fold reduction in sliding rate inside condensates (Figure 3d) is not directly attributed to a specific cause.
2. The speculation that "monkey-bar mechanisms could be shared with other chromatin factors" is unsupported by direct evidence and should be presented as a hypothesis with appropriate caveats.
3. The statement that "ISWI cross-links and thereby stiffens condensates, except when ATP hydrolysis is possible" is supported by the fusion experiments, but the molecular details of the crosslinking (which domains, how many contacts) are not directly demonstrated.
4. The claim that "energy from ATP hydrolysis therefore fuels ISWI's diffusion through chromatin" is supported by the FRAP data, but the mechanism (processive monkey-bar movement vs. facilitated dissociation-rebinding) is not uniquely determined by the data.
5. The simulation results are described as "qualitative agreement" but the degree of agreement and the robustness of the conclusions to parameter choices are not systematically assessed.