## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supplementary figure references.
- **Assessment boundary** Scientific content, methodological rigor, interpretation of results, and alignment with claims made in the abstract and discussion. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors propose that four cancer-associated mutations in the intrinsically disordered p53 transactivation domain (TAD) perturb its disordered conformational ensemble, thereby altering its interactions with key regulatory partners (HDM2, TAZ1, TAZ2) and potentially contributing to cancer pathogenesis. They combine biolayer interferometry, NMR spectroscopy, and extensive atomistic simulations to support this claim.
- **Visible evidence base** Results sections describing binding assays (Figures 2, S1–3, Table 1), NMR chemical shift and relaxation analyses (Figures 4, 5, S5–13, Tables S1–21), and atomistic simulations (Figures 6, 7, S14–22). Methods sections for protein expression, mutagenesis, purification, binding assays, NMR experiments, and simulation protocols.
- **Missing materials affecting confidence** Raw NMR spectra and relaxation data files, simulation trajectory files, convergence metrics beyond those described, full statistical analysis details for binding assays, and any negative control data for the BLI experiments. The manuscript does not provide access to the simulation input files or force field parameters used.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question regarding the functional consequences of cancer-associated mutations in the intrinsically disordered p53 TAD. The combination of experimental and computational approaches is commendable, and the authors present a plausible mechanism whereby mutations perturb the disordered ensemble rather than directly disrupting binding interfaces. However, several technical concerns regarding the interpretation of NMR relaxation data, the quantitative rigor of the binding assays, and the ability of simulations to capture subtle ensemble changes need to be addressed before the central claims are fully established.
- **Who would be interested in the results, and why** Researchers studying intrinsically disordered proteins, p53 biology, cancer genetics, and protein-protein interaction mechanisms. The work also has relevance for those interested in the role of conformational ensembles in allosteric regulation and in the development of therapeutic strategies targeting IDPs.
- **Major strengths** The study combines multiple complementary techniques to address a biologically significant question. The use of extensive atomistic simulations (over 240 μs aggregate sampling) is notable and represents a significant computational investment. The observation that mutations outside known binding interfaces can dramatically affect interactions is an important conceptual contribution. The NMR relaxation analysis provides experimental evidence for changes in conformational dynamics that are not apparent from static structural views.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (binding assay quantification), R1-M2 (NMR relaxation interpretation), R1-M3 (simulation validation), R1-M4 (mechanistic link).
- **Assessment against Nature-style criteria**  
  - **Originality** The work is original in its focus on the disordered ensemble as a mediator of mutation effects, rather than on direct interface disruption. This is a relatively underexplored concept for p53 TAD mutations.  
  - **Scientific importance** The findings have potential implications for understanding how mutations in IDPs contribute to disease, which is a growing area of interest. The specific focus on p53, a critical tumor suppressor, enhances the importance.  
  - **Interdisciplinary readership** The work bridges structural biology, biophysics, computational chemistry, and cancer biology, making it of interest to a broad audience.  
  - **Technical soundness** The experimental and computational methods are generally sound, but several concerns (detailed below) need to be resolved to fully support the conclusions.  
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible, though some sections on NMR relaxation theory and simulation details may be challenging for nonspecialists. The figures are clear and support the text.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the data are suggestive, but the current evidence does not fully establish the mechanistic link between ensemble perturbations and functional outcomes.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Quantitative rigor of binding assays  
- **Claim pointer** The authors claim that cancer-associated mutations "significantly perturb the balance of p53 interactions with key activation and degradation regulators" and report specific KD values in Table 1.  
- **Evidence pointer** Results section, Figure 2, Table 1, Figures S1–3  
- **Concern** The BLI binding assays are used to derive kinetic and equilibrium constants, but the manuscript does not provide sufficient detail on the fitting procedures, the number of independent replicates, or the statistical significance of the observed differences. For interactions labeled "N.D." (not detectable), the authors estimate a lower limit for KD based on a 2–3% complex formation efficiency, but the basis for this estimate is not fully described. Additionally, the control experiments for non-specific binding are mentioned but not shown in detail.  
- **Why it matters** The central claim that mutations alter binding affinities relies on the accuracy and reproducibility of these measurements. Without proper statistical treatment and clear methodology, the quantitative conclusions are not robust.  
- **Resolution test** Provide full details of the fitting procedure, including the model used, the number of replicates, and the statistical comparison between WT and mutant KD values. Show representative raw BLI traces and the non-specific binding controls. For N.D. interactions, provide a more rigorous estimate of the detection limit based on the assay's signal-to-noise characteristics.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Interpretation of NMR relaxation data  
- **Claim pointer** The authors state that NMR relaxation analysis reveals "systematic mutation-induced changes in the p53-TAD conformational dynamics," including compaction for K24N and N29K/N30D and expansion for D49Y and W53G.  
- **Evidence pointer** Results section, Figure 5, Figures S10–13, Tables S6–21  
- **Concern** The interpretation of R2/R1 ratios and reduced spectral density parameters as indicators of compaction or expansion is not straightforward for a disordered protein. The authors do not provide a clear framework for how changes in these parameters translate to specific conformational changes. Additionally, the differences in mean NHNOE/NONOE ratios are reported with standard deviations that overlap substantially between WT and mutants, raising questions about statistical significance.  
- **Why it matters** The claim that mutations alter the conformational ensemble is a key part of the proposed mechanism. If the NMR data do not robustly support this, the mechanistic interpretation is weakened.  
- **Resolution test** Provide a more detailed analysis of the relaxation data, including per-residue error estimates and statistical tests comparing WT and mutants. Discuss the limitations of using R2/R1 ratios for IDPs and consider complementary analyses (e.g., reduced spectral density mapping with explicit model fitting) to support the interpretation.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Simulation validation and convergence  
- **Claim pointer** The authors claim that atomistic simulations "recapitulate the observation from NMR chemical shift analysis" and provide insights into the conformational ensembles of the mutants.  
- **Evidence pointer** Results section, Figures 6, 7, Figures S14–22  
- **Concern** While the simulations are extensive, the manuscript does not provide a direct quantitative comparison between simulated and experimental observables (e.g., chemical shifts, Rg from SAXS, FRET efficiencies). The convergence analysis is based on segmental comparisons, but the criteria for convergence are not clearly defined. Additionally, the PCA analysis using DRID is described, but the interpretation of the resulting clusters or basins is not fully explained.  
- **Why it matters** The simulations are used to support the mechanistic interpretation of the NMR data. Without proper validation against experimental data, the simulation results are not sufficient to establish the proposed mechanism.  
- **Resolution test** Provide a direct comparison of simulated and experimental observables (e.g., predicted chemical shifts from simulations vs. measured values, simulated Rg vs. SAXS data). Clearly define convergence criteria and show that the ensembles are stable over the simulation time. Explain the PCA results in more detail, including how the identified basins relate to specific conformational features.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mechanistic link between ensemble changes and functional outcomes  
- **Claim pointer** The authors propose that "subtle changes in the conformational ensemble of an IDP may produce distinct molecular responses" and that this is the mechanism by which the mutations affect binding.  
- **Evidence pointer** Discussion section  
- **Concern** The manuscript does not provide a direct mechanistic link between the observed ensemble changes and the altered binding affinities. For example, it is not shown that the compaction or expansion of the ensemble specifically affects the availability of binding residues or the entropic cost of binding. The authors speculate on this link but do not provide direct evidence.  
- **Why it matters** The proposed mechanism is the central conceptual contribution of the work. Without direct evidence linking ensemble changes to functional outcomes, the conclusions remain speculative.  
- **Resolution test** Perform additional analyses, such as calculating the population of binding-competent conformations in the simulated ensembles or measuring binding kinetics under conditions that modulate ensemble properties. Alternatively, discuss the limitations of the current data and propose specific experiments to test the mechanism.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of figure presentation  
- **Affected element** Figure 2  
- **Evidence pointer** Results section, Figure 2  
- **Issue** The BLI traces in Figure 2 are described but not shown in detail. The figure appears to show only the fitted curves, not the raw data.  
- **Required correction** Include representative raw BLI traces for each interaction, including the non-specific binding controls, to allow readers to assess the data quality.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Statistical reporting  
- **Affected element** Table 1  
- **Evidence pointer** Results section, Table 1  
- **Issue** The KD values in Table 1 are reported with standard deviations, but the number of replicates is not stated.  
- **Required correction** State the number of independent experiments for each measurement and the statistical test used to compare WT and mutant values.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness of methods  
- **Affected element** Materials and Methods, NMR section  
- **Evidence pointer** Materials and Methods, "Relaxation data acquisition and analysis"  
- **Issue** The methods for relaxation data analysis are described, but the software used for fitting and the specific parameters (e.g., relaxation delays) are not fully detailed.  
- **Required correction** Provide the software version and parameters used for fitting relaxation data, and include the relaxation delay values in the methods.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Discussion of limitations  
- **Affected element** Discussion section  
- **Evidence pointer** Discussion section  
- **Issue** The authors acknowledge that the study did not include phosphorylated forms of the mutants, but they do not discuss other potential limitations, such as the use of isolated TAD rather than full-length p53.  
- **Required correction** Add a brief discussion of the limitations of using isolated TAD and the potential effects of other p53 domains on the observed interactions.

## Risk / unsupported claims
- The claim that "at least three of these mutations likely modulate the disordered state of p53-TAD to perturb its interactions" is not fully supported by direct evidence linking ensemble changes to binding outcomes.
- The statement that "the four mutations studied in this work do not all directly disrupt the known interaction interfaces" is based on structural knowledge, but the manuscript does not provide a systematic analysis of all known interfaces.
- The estimate of the detection limit for N.D. interactions (2–3% complex formation efficiency) is not rigorously derived and should be treated as an approximation.
- The claim that the simulations are "probably one of the most extensive simulation studies of p53-TAD" is not verifiable from the provided data and should be supported by a comparison with published simulation lengths.