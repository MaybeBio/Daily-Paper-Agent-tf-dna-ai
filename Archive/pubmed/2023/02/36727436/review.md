## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, reproducibility, and fit for a high-impact generalist journal
- **Shared manuscript claim summary** The authors present MELD-DNA, an extension of the MELD Bayesian inference framework, to predict protein–DNA complex structures, sequence-dependent binding preferences, and relative binding affinities. They report success on 15 protein–DNA complexes, sequence sensitivity in three systems, and relative affinity rankings for six sequences binding the P22 repressor, using aggregated ~1 ms of sampling.
- **Visible evidence base** Main text: Figures 1–5, Tables 1–3; Supplementary Figures S1–S23, Supplementary Table S1; Methods descriptions; Data availability links
- **Missing materials affecting confidence** Supplementary Information content referenced but not provided in full (e.g., "Specific Results" section, Figures S1–S23, Table S1); no structural coordinates or trajectory data; no detailed error analysis or convergence diagnostics; no explicit force field validation against experimental binding affinities

## Reviewer
- **Overall assessment** This manuscript describes a technically ambitious extension of the MELD framework to protein–DNA complexes, with a clear presentation of three application protocols. The central claims—that MELD-DNA can sample native binding modes, identify them via clustering, and show sequence sensitivity—are partially supported by the presented evidence. However, several methodological details and validation metrics are insufficiently reported, and the comparison with existing methods is limited. The work is of interest to the structural biology and computational chemistry communities, but the current evidence does not fully establish the method's general utility or quantitative accuracy.
- **Who would be interested in the results, and why** Computational structural biologists, researchers developing or using docking and molecular dynamics methods for nucleic acid complexes, and experimentalists seeking structural models of protein–DNA assemblies. The freely available software and protocols will appeal to practitioners needing accessible tools for binding mode prediction.
- **Major strengths** 1) The Bayesian inference framework is well-motivated and extends a proven approach (MELD) to a challenging problem class. 2) The three-protocol structure provides a flexible toolkit for different questions (structure prediction, sequence effects, relative affinities). 3) The use of ambiguous, noisy data is a pragmatic and potentially powerful strategy for enhancing sampling. 4) The study includes a diverse test set of 15 complexes with varying DNA deformation. 5) The manuscript is clearly written and the figures are informative.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1 (convergence), R1-M2 (quantitative validation), R1-M3 (comparison fairness), R1-M4 (reproducibility)
- **Assessment against Nature-style criteria** **Originality**: Moderate. The extension of MELD to DNA is incremental but addresses a real gap. **Scientific importance**: Moderate. Protein–DNA structure prediction is important, but the demonstrated accuracy and scope are limited. **Interdisciplinary readership**: Limited. The methods are specialized; the biological insights are not yet deep enough to attract a broad audience. **Technical soundness**: Partially sound. The approach is reasonable, but key validations (convergence, quantitative accuracy) are missing. **Readability for nonspecialists**: Good. The writing is accessible, though the methods require domain expertise.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly convergence demonstration, quantitative validation against experimental data, and fairer benchmarking.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "MELD-DNA successfully: (i) samples multiple binding modes; (ii) identifies the experimental binding mode through clustering the ensembles; and (iii) is sensitive to DNA sequences and conformations."
- **Evidence pointer** Results section, Figures 3–5, Supplementary Figures S1–S23
- **Concern** The manuscript does not provide sufficient evidence that the replica exchange simulations have converged. For a method that relies on equilibrium sampling to identify native binding modes, convergence is essential. No autocorrelation times, replica exchange acceptance rates, or block-averaging analyses are reported. The claim that "the lowest replica index will be enriched on the state with the lowest RMSD" (Results) is presented without quantitative support.
- **Why it matters** Without convergence demonstration, the observed native-like clusters could be artifacts of incomplete sampling or biased initial conditions. The central claim of identifying the native binding mode from the ensemble is not robustly established.
- **Resolution test** Provide replica exchange acceptance ratios, effective sample sizes, and a comparison of ensemble properties across independent simulations (e.g., different random seeds or initial velocities). Show that the identified native cluster is stable across these replicates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative validation
- **Claim pointer** "Relative binding affinities identify structure/sequence preferences during binding" and "the consensus sequence was preferred in all cases."
- **Evidence pointer** Results section, Figure 5, Table 2
- **Concern** The relative binding affinity results are presented qualitatively (e.g., "preferred," "decreased") without numerical free energy differences or statistical uncertainties. The self-competition test (57/43) is mentioned but no error bars or confidence intervals are given. The claim that the consensus is preferred in all cases is not quantified, and the magnitude of the preference is unknown.
- **Why it matters** For a method that aims to provide "qualitative binding preferences," the lack of quantitative metrics (e.g., ΔΔG values with uncertainties) limits the utility and prevents comparison with experimental or other computational data. The reader cannot assess whether the observed preferences are significant or within noise.
- **Resolution test** Report free energy differences (e.g., from population ratios) with bootstrapped or block-averaged uncertainties. Compare at least one predicted preference with an experimental measurement or a well-established computational benchmark.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Benchmarking fairness
- **Claim pointer** "We first assess performance on a dataset of 15 protein–DNA complexes and compare it with state-of-the-art methodologies."
- **Evidence pointer** Results section, Table 3, Supplementary Figures S18–S19
- **Concern** The comparison with HADDOCK and RF2NA is limited and potentially unfair. For HADDOCK, the authors note they used it "as regular users," which may not reflect optimal performance. For RF2NA, only one structure per complex was generated, and the method's known limitations with homodimers are highlighted. No metrics such as success rate, ranking of native-like solutions, or computational cost are systematically compared.
- **Why it matters** The claim of superiority or complementarity to existing methods is not convincingly supported. A fairer benchmark would use standard protocols, multiple runs, and established evaluation criteria (e.g., CAPRI criteria).
- **Resolution test** Use standardized docking benchmarks (e.g., from Dockground or a protein–DNA subset of CAPRI) and report success rates, ranks of near-native solutions, and interface RMSD distributions for all methods under comparable conditions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "The general pipeline is available on GitHub" and "Scripts and sample data used for this report are available."
- **Evidence pointer** Data Availability section
- **Concern** While the code and sample data are deposited, the manuscript does not provide sufficient detail on input preparation, parameter choices, or the exact commands needed to reproduce the simulations. The description of the restraint setup (e.g., how the "dummy atom" approach is implemented, how the contact lists are generated) is high-level and may not be sufficient for independent reproduction.
- **Why it matters** Reproducibility is a core expectation for computational method papers. Without detailed protocols, the community cannot easily adopt or validate the method.
- **Resolution test** Provide a step-by-step tutorial or configuration files for at least one test case, including all input structures, restraint definitions, and simulation parameters. Ideally, include a containerized environment or a script that runs end-to-end.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states the method "can: (i) sample multiple binding modes; (ii) identify the preferred binding mode from the ensembles; and (iii) provide qualitative binding preferences between DNA sequences." The phrase "qualitative binding preferences" is vague; the reader does not know if this means rank-ordering, relative populations, or something else.
- **Required correction** Clarify in the abstract what "qualitative" means, e.g., "rank-order binding preferences" or "identify the most likely bound sequence among a set."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, Protocol 1
- **Evidence pointer** Methods section, Protocol 1
- **Issue** The description of how the "dummy atom" is placed at the N1 position of purines is brief. It is unclear whether this is a virtual particle or an actual atom with specific parameters, and how this affects the interaction with protein Cα atoms.
- **Required correction** Provide a more detailed description of the dummy atom implementation, including its force field parameters (if any) and how it is used in the energy function.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, Figure 5
- **Evidence pointer** Figure 5
- **Issue** The population ratios in Figure 5B are presented as a single value (57/43) without error bars or replicate information. It is unclear if this is from a single simulation or an average.
- **Required correction** Report the number of independent simulations and the standard deviation or confidence interval for the population ratio.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions "the DNA has more flexibility than the protein system" but does not discuss the potential impact of this asymmetry on the results, particularly for systems where protein flexibility is important for binding.
- **Required correction** Add a brief discussion of how the differential flexibility might affect the method's applicability to different protein–DNA systems.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Data Availability
- **Evidence pointer** Data Availability section
- **Issue** The Zenodo links are provided, but it is not stated whether the deposited data include all input structures, output trajectories, or only scripts and sample data.
- **Required correction** Specify the exact contents of the Zenodo deposits (e.g., "all input PDB files, simulation parameter files, and analysis scripts").

## Risk / unsupported claims
- The claim that MELD-DNA "successfully predicted 10 of them as high population clusters" (Discussion) is not directly supported by the Results, which state 11 of 15 in top five clusters. The discrepancy between "10" and "11" is unexplained.
- The statement that "the method samples accurate atomic structures representative of the native state for most of the systems studied" is an overstatement given the lack of convergence evidence and the 2/15 failures.
- The relative binding affinity results are presented without numerical values or uncertainties, making the claim "the consensus sequence was preferred in all cases" unverifiable from the provided evidence.
- The comparison with RF2NA is based on a single prediction per complex, which is insufficient to assess the method's typical performance.
- The claim that "HADDOCK predictions can readily be incorporated as structural seeds" is speculative and not demonstrated in this work.