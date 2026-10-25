## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and evidentiary support based solely on the provided text; figures, tables, and supplementary data referenced but not directly assessable
- **Shared manuscript claim summary** The authors propose that MBD2 binding to methylated CpG DNA involves a bistable equilibrium between two distinct bound conformations, with residue S189 acting as a key macro-switch; the S189A mutation shifts the equilibrium toward a secondary, lower-affinity state while preserving mCpG selectivity, as supported by MD simulations, NMR spectroscopy, and fluorescence polarization experiments
- **Missing materials affecting confidence** All figures, tables, supplementary information (including Supplementary Table S1 and all Supplementary Figures), the Zenodo repository data, and the previously published NMR assignments (BMRB entry 16936) were not available for direct verification

## Reviewer

### Overall assessment
This manuscript presents a computational and experimental study of MBD2 recognition of methylated CpG DNA, proposing a bistable binding equilibrium with two distinct bound conformations. The work combines extensive classical MD simulations (277 µs total) with NMR and fluorescence polarization experiments to support the existence of a secondary bound state and the role of S189 as a macro-switch. The central claim is novel and potentially significant for understanding protein-DNA recognition mechanisms. However, the manuscript as provided has several critical gaps that prevent full evaluation: the absence of all figures and tables makes it impossible to assess the quality of the data presentation, the statistical robustness of the clustering analyses, or the convergence of the free energy calculations. The experimental validation is limited to a single point mutant, and the connection between the simulated secondary state and the experimentally observed reduced affinity of S189A, while plausible, is not directly demonstrated. The broader claim that bistable equilibria may be a general feature of protein-DNA recognition is speculative and would require additional evidence beyond the two systems cited. The manuscript is well-written and the methodology is described in sufficient detail for reproduction, but the evidentiary basis for the central claims cannot be fully verified from the text alone.

### Who would be interested in the results, and why
Researchers in the fields of epigenetic regulation, protein-DNA recognition, and computational biophysics would find these results of interest. The study addresses a fundamental question about how DNA-binding proteins achieve both high specificity and conformational adaptability, which is relevant to understanding MBD2's role in gene silencing and the broader MBD protein family. The identification of a secondary bound state with reduced affinity but retained selectivity has implications for interpreting mutational studies in MBD proteins, including disease-associated mutations such as the S134C mutation in MeCP2. The methodological approach, combining unbiased MD simulations with free energy calculations and experimental validation, would also be of interest to computational biologists studying protein-DNA interactions.

### Major strengths
1. The study addresses a significant and under-explored question: the conformational dynamics of specific protein-DNA recognition beyond the static structures captured by X-ray crystallography.
2. The computational approach is extensive and well-designed, with multiple independent replicas and long simulation timescales (up to 35 µs for the secondary state).
3. The combination of unbiased MD simulations with biased free energy calculations (SMD plus umbrella sampling) and experimental validation (NMR, fluorescence polarization) provides a multi-pronged approach to test the central hypothesis.
4. The identification of S189 as a specific residue controlling the equilibrium between two bound states is a concrete and testable mechanistic proposal.
5. The use of a second, biologically relevant DNA sequence to test the generality of the secondary state strengthens the claim.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that MD simulations reveal two stable bound conformations (primary and secondary states) of the MBD2-mCpG complex, with the secondary state being a distinct, well-defined conformation that persists over multiple microseconds.
- **Evidence pointer** Results section "The secondary state adopts a distinct complex conformation"; Figures 2C, 3A-D; Supplementary Figures S6-S13
- **Concern** The identification of two distinct conformational states relies entirely on RMSD clustering and visual inspection of representative structures. The manuscript does not provide quantitative measures of state separation, such as free energy differences between the states, transition rates, or statistical tests demonstrating that the two clusters are significantly distinct. The claim that the secondary state is "stable" is based on persistence over microseconds, but without a free energy landscape or potential of mean force calculation, the thermodynamic stability of this state relative to the primary state cannot be assessed. Furthermore, the clustering analysis is performed on a combined dataset from different simulation types (search, recognition, interrogation), and it is unclear whether the clustering parameters were chosen a priori or optimized to produce the observed separation.
- **Why it matters** The central claim of the paper is the existence of a bistable equilibrium. Without quantitative evidence of two distinct free energy minima and an estimate of the barrier between them, the claim of bistability is not established. The distinction between a genuinely stable alternative state and a transient, partially bound conformation is critical for the biological interpretation.
- **Resolution test** Provide a free energy profile along a suitable reaction coordinate connecting the primary and secondary states, with error estimates. Alternatively, provide a rigorous statistical analysis of the clustering results, including cluster validity indices, bootstrap analysis, and demonstration that the two states are separated by a free energy barrier significantly exceeding kT.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The manuscript claims that NMR experiments confirm that the S89A mutation does not alter mCpG selectivity, and that fluorescence polarization measurements reveal a reduced binding affinity consistent with MD simulations.
- **Evidence pointer** Results section "S189A mutation retains MBD2 selectivity for mCpG but reduces binding affinity"; Figure 5C-D
- **Concern** The experimental validation is limited to a single mutant (S189A) and does not directly test the bistable equilibrium hypothesis. The NMR experiment shows that three specific cross-peaks (G169, R166, A172) remain unchanged upon mutation, which is interpreted as retained selectivity. However, this is an indirect readout: the authors do not demonstrate that the secondary state is populated in the wild-type protein, nor do they show that the S189A mutant actually adopts the secondary state conformation in solution. The fluorescence polarization measurement provides a single dissociation constant for the mutant, which is compared to a previously published value for the wild-type. The claim that the experimental binding free energy "falls between the two computed free energy bounds" is suggestive but does not constitute a direct validation of the secondary state. The error bars on the FP measurement and the statistical significance of the 10-fold difference are not reported in the text.
- **Why it matters** The experimental data are presented as validation of the computational predictions, but they do not directly test the existence of the secondary state. The interpretation relies on the assumption that reduced affinity with retained selectivity is equivalent to a shift toward the secondary state, which is not demonstrated. Without direct experimental evidence for the secondary state (e.g., NMR structure of the mutant complex, or relaxation dispersion experiments showing conformational exchange), the validation is incomplete.
- **Resolution test** Provide direct experimental evidence for the secondary state, such as a solution structure of the S189A mutant bound to mCpG DNA, or NMR relaxation dispersion data showing conformational exchange between two bound states. Alternatively, perform a more comprehensive mutational analysis with multiple residues predicted to be involved in the primary vs. secondary state, and show a correlation between predicted and measured binding affinities.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Force field validation
- **Claim pointer** The manuscript claims that the MD simulations accurately capture the conformational dynamics of the MBD2-mCpG complex, including the transition from a nonspecific to a specific bound state.
- **Evidence pointer** Materials and methods "Molecular dynamics simulation"; Results sections on search simulations
- **Concern** The simulations use AMBER14SB and AMBER parmbsc1 force fields with a combined protocol for 5mC parameters. While these are standard and well-tested force fields, the manuscript does not provide any validation of the force field parameters for the methylated cytosine specifically. The authors do not compare simulated structural ensembles with experimental data (e.g., NMR residual dipolar couplings, chemical shift perturbations) to validate that the force field accurately reproduces the conformational preferences of the MBD2-mCpG complex. The observation that the X-ray-derived simulations remain stable while the NMR-derived simulations do not is interpreted as evidence for the importance of the DNA conformation, but it could also reflect force field artifacts or differences in the starting structures.
- **Why it matters** The conclusions of the study depend critically on the accuracy of the MD simulations. If the force field does not accurately describe the methylated DNA or the protein-DNA interactions, the identified secondary state could be an artifact. Validation of the force field against experimental data is essential for the credibility of the computational predictions.
- **Resolution test** Provide validation of the simulation setup against experimental data, such as comparing simulated chemical shifts or scalar couplings with NMR data, or reproducing known binding affinities for wild-type and mutant MBD2. Alternatively, perform simulations with an alternative force field (e.g., CHARMM36) to demonstrate that the bistable behavior is not force field dependent.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Free energy calculation reliability
- **Claim pointer** The manuscript claims that umbrella sampling simulations yield binding free energy differences of (2.4 ± 0.34) kcal/mol between the wt-primary state and S189A, and (1.2 ± 0.43) kcal/mol between the wt-secondary state and S189A.
- **Evidence pointer** Results section "S189A mutation retains MBD2 selectivity for mCpG but reduces binding affinity"; Figure 5E; Supplementary Figures S25-S28
- **Concern** The free energy calculations rely on SMD trajectories to generate starting configurations for umbrella sampling. The manuscript states that SMD was used "to generate smooth unbinding trajectories" and that the funnel potential was applied to prevent artificial sliding. However, the choice of pulling speed, the selection of only one trajectory per system for umbrella sampling, and the equilibration protocol are not described in sufficient detail. The convergence analysis (Supplementary Figure S28) is referenced but not shown. The error estimates are based on block averaging of 5-ns intervals, which may not capture the full statistical uncertainty if the sampling is correlated. The manuscript does not report the overlap between umbrella sampling windows quantitatively, nor does it provide the full PMF profiles.
- **Why it matters** The quantitative agreement between the experimental binding free energy difference and the computed values is a key piece of evidence supporting the bistable model. If the free energy calculations are not converged or are biased by the SMD protocol, the agreement could be fortuitous. The reliability of the computed free energy differences must be established for the conclusions to be robust.
- **Resolution test** Provide the full PMF profiles with error bars, quantitative measures of histogram overlap, and a demonstration of convergence using multiple independent SMD trajectories and/or longer equilibration times. Report the pulling speed and justify its choice. Consider using multiple reaction coordinates or a more rigorous free energy method (e.g., metadynamics) to cross-validate the results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "bistable equilibrium" is used without prior definition. While the concept is explained later in the manuscript, the abstract would benefit from a brief clarification of what is meant by bistable in this context.
- **Required correction** Add a brief explanatory phrase, e.g., "two distinct, interconvertible bound conformations" to the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and methods, MD simulation protocol
- **Evidence pointer** Materials and methods "MD simulations protocol"
- **Issue** The manuscript states that "all molecular dynamics simulations were performed with the GROMACS 2018.4 and GROMACS 2022.5 package" but does not specify which version was used for which simulation set. This is important for reproducibility.
- **Required correction** Specify which GROMACS version was used for each type of simulation (recognition, interrogation, search, SMD, umbrella sampling).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, fluorescence polarization
- **Evidence pointer** Results section "S189A mutation retains MBD2 selectivity for mCpG but reduces binding affinity"; Figure 5D
- **Issue** The manuscript reports a K_D value of (11.5 ± 0.6) µM for the S189A mutant but does not report the number of independent experiments or the statistical test used to compare this to the wild-type value.
- **Required correction** Report the number of replicates and the statistical method used to determine significance of the difference between wild-type and mutant K_D values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, comparison to other systems
- **Evidence pointer** Discussion, paragraph on bistable binding in other systems
- **Issue** The discussion cites Liu et al. on bistable oscillations in the WRKY domain but does not provide sufficient context for how this system compares to MBD2. The relevance of the comparison would be strengthened by a brief description of the WRKY system and its timescales.
- **Required correction** Add one or two sentences describing the WRKY system and how its bistable behavior compares to that observed for MBD2.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results, S189A mutation section
- **Evidence pointer** Results section "S189A mutation shifts the MBD2-mCpG complex toward the secondary state conformation"
- **Issue** The term "macro-switch" is used to describe S189, but this term is not defined. It appears to refer to a residue whose interaction state determines which of two conformational states is adopted, but this should be stated explicitly.
- **Required correction** Define "macro-switch" at first use, e.g., "a residue whose interaction with the DNA backbone determines the conformational state of the complex."

### Technical failings that need to be addressed before the case is established
1. Absence of quantitative evidence for two distinct free energy minima (R1-M1)
2. Incomplete experimental validation of the secondary state (R1-M2)
3. Lack of force field validation for the methylated DNA parameters (R1-M3)
4. Insufficient detail on the convergence and reliability of free energy calculations (R1-M4)

### Assessment against Nature-style criteria
- **Originality**: The concept of a bistable equilibrium in specific protein-DNA recognition is novel and extends beyond the static view provided by crystal structures. The identification of a specific residue (S189) as a conformational switch is an original contribution. However, the broader idea of multiple bound conformations is not entirely new, and the manuscript would benefit from a more explicit statement of what is conceptually novel beyond the specific system.
- **Scientific importance**: The findings have potential importance for understanding MBD2 function in epigenetic regulation and for the broader field of protein-DNA recognition. The suggestion that bistable equilibria may be a general feature of specific protein-DNA complexes is significant if supported by sufficient evidence. The clinical relevance of the S189 position, given the analogous S134C mutation in MeCP2 causing Rett syndrome, adds to the importance.
- **Interdisciplinary readership**: The work bridges computational biophysics, structural biology, and epigenetics. The manuscript is written in a way that is largely accessible to researchers in these fields, though some of the computational details may be challenging for experimentalists. The broader implications for epigenetic regulation would interest a wider readership.
- **Technical soundness**: The simulation protocol is generally sound, with appropriate force fields, long timescales, and multiple replicas. However, the lack of quantitative free energy analysis and the incomplete validation of the force field for methylated DNA are significant technical gaps. The experimental methods are appropriate but limited in scope.
- **Readability for nonspecialists**: The manuscript is clearly written and the logic is easy to follow. The abstract and introduction provide sufficient background. However, the results section is dense with technical details that may be difficult for nonspecialists to fully appreciate. The figures (not available for review) would be critical for accessibility.

### Recommendation posture
Supportive if technical concerns are resolved. The central hypothesis is interesting and potentially significant, and the combination of computational and experimental approaches is appropriate. However, the case for bistability is not fully established from the provided evidence. The authors must provide quantitative evidence for two distinct free energy minima, strengthen the experimental validation of the secondary state, and address the force field and free energy calculation concerns before the claims can be considered robust. The manuscript is not currently suitable for publication in its present form.

## Risk / unsupported claims
1. The claim that the secondary state represents a "stable" conformation is not quantitatively supported without free energy calculations or other thermodynamic measures.
2. The claim that the S189A mutation "shifts the equilibrium toward the secondary state" is inferred from MD simulations but not directly demonstrated experimentally.
3. The broader claim that "bistable binding behavior at the mCpG site may serve as a mechanism by which MBD2 optimizes the balance between binding specificity and dynamic adaptability" is speculative and not directly tested.
4. The claim that "such alternative bound-state equilibria may represent an inherent feature of specific protein-DNA complexes" is based on only two systems (MBD2 and WRKY) and is not sufficiently supported.
5. The statement that the experimental binding free energy "falls between the two computed free energy bounds" is presented as validation but the statistical significance of this agreement is not assessed.
6. The claim that the secondary state "retains comparable selectivity for mCpG" is based on the observation that key base-specific interactions are preserved, but quantitative measures of selectivity are not provided.