## Review setup
- **Input scope** Full manuscript text (Introduction, Methods, Results, Discussion, Conclusion) with figure legends and table; supplementary figure list referenced but not provided.
- **Assessment boundary** Computational predictions of binding modes and inferred impacts on nucleic acid dynamics for three small molecule inhibitors (SPIs) targeting the Pol II-Spt5 complex, based on docking and molecular dynamics simulations.
- **Shared manuscript claim summary** The authors predict binding sites for three SPIs at the Pol II-Spt5 interface, show that two bind strongly while one binds weakly with multiple sites, and report that strong binding alters Spt5-nucleic acid interactions, stabilizing RNA and destabilizing DNA at the exit tunnels.
- **Visible evidence base** Docking results (Table 1, Fig. 2, Fig. S4), MD simulation analyses (Figs. 3-6, Figs. S1-S3, S5-S14), methods descriptions for docking, MD, and MM/GBSA calculations.
- **Missing materials affecting confidence** Supplementary figures S1-S14 are referenced but not provided; no PDB accession codes for starting structures beyond PDB ID 5OIK; no force field parameter validation data for SPI ligands; no convergence or sampling adequacy analysis; no error estimates for MM/GBSA energies beyond standard deviation; no experimental validation data.

## Reviewer
- **Overall assessment** The manuscript presents a computational study of small molecule inhibitor binding to the Pol II-Spt5 complex, a relevant target for neurodegenerative disease therapy. The work combines docking and MD simulations to predict binding sites and infer effects on nucleic acid dynamics. While the topic is of interest and the computational approach is reasonable, several technical concerns limit the strength of the conclusions. The claim that SPI binding "impacts RNA and DNA stability" is inferred from simulation data without direct experimental validation, and the statistical robustness of the observed differences is not fully established. The manuscript would benefit from more rigorous sampling analysis, additional replicates, and clearer presentation of uncertainties.
- **Who would be interested in the results, and why** Researchers in transcription regulation, structural biology of RNA polymerase complexes, and computational drug discovery for neurodegenerative diseases such as Huntington's disease. The work provides initial structural hypotheses for how small molecules might disrupt DSIF function, which could inform future experimental studies and drug development efforts.
- **Major strengths** The study addresses an important and timely question regarding the mechanism of action of recently identified transcription inhibitors. The use of experimentally guided docking is a sensible strategy given the challenges of docking to large, flexible complexes. The comparison of three inhibitors with different binding behaviors provides useful contrast. The analysis of indirect effects on nucleic acid dynamics through Spt5 is a thoughtful approach.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (sampling adequacy), R1-M2 (statistical significance), R1-M3 (force field validation), R1-M4 (experimental context).
- **Assessment against Nature-style criteria** **Originality**: Moderate. The application of computational methods to this specific system is novel, but the overall approach (docking plus MD) is standard. **Scientific importance**: Moderate to high. Understanding how these inhibitors work could have therapeutic implications, but the current study provides predictions rather than definitive mechanisms. **Interdisciplinary readership**: Limited. The work is primarily of interest to computational biophysicists and transcription biologists; the clinical relevance is discussed but not demonstrated. **Technical soundness**: Adequate but with concerns about sampling, statistical treatment, and force field validation. **Readability for nonspecialists**: The manuscript is generally well-written and accessible, though some methodological details could be clarified for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core computational work is reasonable, but the strength of the conclusions regarding nucleic acid stability needs to be better supported by sampling analysis, statistical testing, and acknowledgment of limitations.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that SPI binding impacts RNA and DNA stability based on MD simulation results, including RMSF, RMSD, and distance map analyses.
- **Evidence pointer** Fig. 5, Fig. 6, Figs. S7-S9, S13-S14; Methods section "MD simulations"
- **Concern** The manuscript does not provide evidence that the 200 ns simulations (three replicates per system) are sufficient for convergence of the observed differences in nucleic acid dynamics. No block-averaging analysis, autocorrelation analysis, or convergence metrics are presented. The RMSF and RMSD differences between systems could be within statistical noise if sampling is inadequate, particularly for large, slow-moving complexes like Pol II.
- **Why it matters** Without demonstrated convergence, the observed differences in nucleic acid dynamics cannot be reliably attributed to SPI binding rather than insufficient sampling. This directly affects the central claim of the manuscript.
- **Resolution test** Provide convergence analysis (e.g., block-averaged RMSF/RMSD with error bars, split-half analysis, or cumulative average plots) showing that the reported differences are stable over the simulation time. Alternatively, extend simulations or increase replicate number and show consistent results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "SPIs I and III bind more favorably compared to II" and that "strong binding of the formers altered Spt5-nucleic acid interactions."
- **Evidence pointer** Table 1, Fig. 3, Fig. 4
- **Concern** The MM/GBSA binding energies are reported as mean ± standard deviation, but no statistical test (e.g., t-test, Mann-Whitney U) is applied to determine whether the differences between SPI I/III and SPI II are significant. The standard deviations appear to overlap or nearly overlap for some comparisons. Additionally, the MM/GBSA method is known to have large systematic errors, and the authors acknowledge this but do not provide error estimates beyond standard deviation.
- **Why it matters** The distinction between "strong" and "weak" binding is a key finding. Without statistical support, the claim that SPI II binds more weakly may not be robust, which would weaken the interpretation of its different effects on nucleic acid dynamics.
- **Resolution test** Apply appropriate statistical tests to the MM/GBSA energies across replicates. Report effect sizes and confidence intervals. Consider additional binding free energy methods (e.g., MM/PBSA, FEP) or at least discuss the limitations more quantitatively.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors use the CHARMM c36/c36m force fields and CGenFF for SPIs, and state that "the ligand conformations were slightly changed and their positions along the complex were unaltered during the equilibration."
- **Evidence pointer** Methods section "MD simulations"; Fig. S3
- **Concern** No validation of the CGenFF parameters for the three SPI molecules is provided. The authors do not report partial charge derivation details, parameter fitting quality, or comparison with quantum mechanical calculations. For drug-like molecules with multiple functional groups, incorrect parameters can lead to artifacts in binding behavior and dynamics.
- **Why it matters** The reliability of the binding predictions and the observed effects on nucleic acid dynamics depend on accurate ligand parameters. Without validation, the results may not be reproducible or physically meaningful.
- **Resolution test** Provide CGenFF parameter validation, including comparison of optimized geometries, electrostatic potentials, or torsional profiles against QM references. Report the CGenFF penalty scores for each molecule. If penalties are high, consider reparameterization or alternative approaches.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors suggest that their findings "could be directly related to the functional roles of DSIF in transcription elongation" and that the inhibition mechanism "could be related to Spt5-nucleic acid interactions."
- **Evidence pointer** Discussion section
- **Concern** The manuscript does not connect the computational predictions to experimental observations beyond citing the prior study by Bahat et al. The authors do not discuss whether the predicted binding sites are consistent with known functional regions of Spt5 or whether the observed effects on nucleic acid dynamics would be expected to alter transcription in a way that matches experimental inhibition data. The relevance of the findings to the selective inhibition of mutant Huntingtin gene transcription remains speculative.
- **Why it matters** For the work to have broader impact, the computational predictions need to be placed in a testable biological context. Without this, the significance of the findings is limited to a computational exercise.
- **Resolution test** Discuss how the predicted binding modes and effects on nucleic acid dynamics could be tested experimentally (e.g., mutagenesis, crosslinking, single-molecule assays). Compare the predicted binding sites with known functional domains of Spt5 and discuss whether the predicted effects are consistent with the observed selectivity for mutant Huntingtin gene transcription.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Docking of SPIs on the Pol II-DSIF complex"
- **Evidence pointer** Methods section
- **Issue** The docking protocol is described briefly, but details such as the number of docking runs, the scoring function used for ranking, and the criteria for selecting the "best" pose are not fully specified. The statement "The best binding conformation with a minimum total binding energy among all the docking conformations was used" is vague.
- **Required correction** Provide more details on the docking protocol, including the number of genetic algorithm runs, the population size, the number of evaluations, and the clustering parameters. Specify the exact AutoDock scoring function and any post-docking filtering criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Two SPIs manifested strong binding to the Pol II-DSIF complex"
- **Evidence pointer** Fig. 3, Fig. 4
- **Concern** The description of the PCA analysis for ligand positions is somewhat unclear. The authors state that PCA was applied to the relative center of mass of the ligand, but it is not clear how the free energy plots were generated from the PCA data or how the "minimum energy positions" were extracted.
- **Required correction** Clarify the methodology for the PCA-based free energy analysis, including how the 2D histograms were converted to free energy surfaces and how the minimum energy structures were selected.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "SPIs impact RNA and DNA stability"
- **Evidence pointer** Fig. 5, Fig. 6
- **Concern** The authors report increased DNA fluctuations and decreased RNA fluctuations in the presence of SPIs, but do not provide quantitative comparisons (e.g., average RMSF values with error bars) or statistical tests for these differences. The visual inspection of RMSF plots may not be sufficient to support the claims.
- **Required correction** Provide quantitative summaries of the RMSF/RMSD data (e.g., mean ± SD over replicates) and apply appropriate statistical tests to support the claim that SPI binding alters nucleic acid dynamics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Initial structures of SPIs"
- **Evidence pointer** Methods section
- **Concern** The authors state that "the conformations were optimized using Gaussian09 with MP2 geometry optimization method and 6-31G(d) basis" and that B3LYP was also used for comparison. However, the final choice of which optimized structure was used for docking is not specified.
- **Required correction** Specify which optimized structure (MP2 or B3LYP) was used for each SPI and whether the choice affected the docking results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Docking predicted binding of the SPIs to the Pol II-Spt5 interface"
- **Evidence pointer** Fig. 2, Table 1
- **Concern** The docking energies in Table 1 are reported without units. While kcal/mol is implied, this should be stated explicitly.
- **Required correction** Add units to the docking and MM/GBSA energy values in Table 1 and in the text.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Concern** The authors mention that "the stereochemistry of the SPIs may also have effects in their inhibition activity" and present results for the R-enantiomer of SPI-I. However, the S-enantiomer results are only briefly mentioned in the supplementary figure legend. A more detailed comparison of the two enantiomers in the main text would strengthen the discussion.
- **Required correction** Provide a more detailed comparison of the R and S enantiomers of SPI-I in the main text, including binding energies, binding sites, and effects on nucleic acid dynamics.

## Risk / unsupported claims
- The claim that SPI binding "impacts RNA and DNA stability" is based solely on MD simulations without experimental validation. The term "stability" is used loosely and could be misinterpreted as thermodynamic stability rather than dynamic fluctuations.
- The claim that "strong binding of the formers altered Spt5-nucleic acid interactions" is inferred from correlation between binding strength and observed changes in nucleic acid dynamics, but causality is not established.
- The statement that "the increased interactions made the RNA exit tunnel tighter, and potentially caused the further stabilization of RNA" is speculative and not directly supported by the data presented.
- The hypothesis that "RNA stabilization at the exit site could be larger with the mutant Htt gene that may induce pausing, or alternatively largely destabilized upstream DNA may cause transcription defects" is presented without supporting evidence.
- The claim that "SPI-II has multiple binding sites, which may cause multiple mechanisms of inhibiting different genes" is speculative and not tested in this study.
- The relevance of the findings to the selective inhibition of mutant Huntingtin gene transcription is not established, as the simulations use a generic Pol II-Spt5 complex without the Huntingtin gene sequence.