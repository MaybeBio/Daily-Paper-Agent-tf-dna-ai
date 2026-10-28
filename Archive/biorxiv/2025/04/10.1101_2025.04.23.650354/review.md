## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, and methods summary) as provided
- **Assessment boundary** Scientific content, methodological rigor, and claim support based solely on the supplied text; no external data or supplementary materials were accessed
- **Shared manuscript claim summary** The authors use all-atom MD simulations to propose that HIF-2 PAS-B ligands (agonists vs antagonists) differentially modulate local binding-site conformation, heterodimer stability, global complex dynamics, and DNA-binding domain structure, and they present a multiscale virtual screening framework based on these descriptors
- **Visible evidence base** Abstract, Introduction, Results (including Figures 1–3 references), and Discussion; supplementary figures and tables are referenced but not provided
- **Missing materials affecting confidence** Supplementary Information (methods details, Figures S1–S6, Tables S1–S2), raw simulation data, force field parameters, docking scores, and statistical analyses are not available; this limits verification of quantitative claims

## Reviewer
- **Overall assessment** The manuscript addresses a clinically relevant and mechanistically important question, namely how small molecules can differentially modulate HIF-2 activity through allosteric effects on the HIF-2/ARNT complex. The use of long MD simulations and the proposal of a multiscale screening strategy are commendable. However, the evidence presented in the provided text is insufficient to fully establish the central claims. Key quantitative results are described without adequate statistical detail, the link between simulation-derived descriptors and functional outcomes is asserted rather than rigorously demonstrated, and the virtual screening framework is presented as a proposal without prospective validation. The work is potentially interesting but currently not established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in hypoxia signaling, structural biology of transcription factors, and computational drug discovery would find the mechanistic insights and the proposed screening approach relevant. The potential to distinguish agonists from antagonists in silico could inform therapeutic development for renal anemia and cancer, attracting interest from both academic and pharmaceutical sectors.
- **Major strengths** The study tackles a clinically important problem with a sophisticated computational approach. The use of long MD simulations (1.5 µs per state) and the integration of local, global, and DNA-binding domain descriptors is thoughtful. The observation that ΔΔG separates known agonists from antagonists is promising, and the emphasis on including holo-state conformers for docking is a practical insight.
- **Major Concerns** The following concerns are identified.
- **Minor Comments** The following minor comments are noted.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The concept of using multiple MD-derived descriptors to distinguish HIF-2 modulators is novel, though individual components (e.g., MM/PBSA, RMSF analysis) are standard. Scientific importance: The potential to improve virtual screening for HIF-2 is significant, but the current evidence does not yet demonstrate practical utility. Interdisciplinary readership: The topic bridges structural biology, biophysics, and drug discovery, which could appeal to a broad audience if claims are substantiated. Technical soundness: The methods are generally appropriate, but the lack of statistical rigor and validation undermines confidence. Readability for nonspecialists: The text is largely accessible, but some technical terms (e.g., order parameters, protection factors) are introduced without sufficient explanation for a general audience.
- **Recommendation posture** Currently not established from the provided evidence; supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that PT2385 binding leads to a ~50% increase in per-residue RMSF of the HIF-2/ARNT complex, and that M1001 slightly decreases it (Figure 3A).
- **Evidence pointer** Figure 3A, location not provided
- **Concern** The quantitative claim of a 50% increase is presented without error bars, replicate-level data, or statistical testing. It is unclear whether this difference is significant given the variability across three 500 ns replicates.
- **Why it matters** Without statistical support, the central mechanistic distinction between agonist and antagonist effects on global dynamics is not robustly established, which undermines the proposed descriptor's reliability.
- **Resolution test** Provide per-replicate RMSF values with standard deviations, and perform a statistical test (e.g., t-test or ANOVA) comparing apo, PT2385-bound, and M1001-bound states.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors state that ΔΔG completely separates known agonists from antagonists, with agonists ranging from 2.9 to 3.5 kcal/mol and antagonists from -2.8 to -1.3 kcal/mol.
- **Evidence pointer** Figure 1D, location not provided
- **Concern** The separation is based on a small set of 10 ligands (8 antagonists, 2 agonists). The claim of "complete separation" is fragile given the small sample size, and the overlap of decoy distributions with both classes is acknowledged but not fully addressed.
- **Why it matters** The proposed ΔΔG metric is a cornerstone of the virtual screening framework. If it cannot reliably distinguish agonists from antagonists in a larger, more diverse ligand set, its practical utility is questionable.
- **Resolution test** Validate ΔΔG on a larger, independent set of known HIF-2 modulators, and report sensitivity, specificity, and confidence intervals for the separation threshold.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors used QM/MM-derived partial charges for ligands, which yielded the lowest deviation (~1 Å) from experimental poses.
- **Evidence pointer** Figure S1, location not provided
- **Concern** The details of the QM/MM calculations (e.g., level of theory, basis set, partitioning scheme) are not provided in the main text, and the supplementary methods are not accessible. This limits reproducibility.
- **Why it matters** The accuracy of ligand charges is critical for the reliability of MD simulations and docking results. Without full methodological details, the validity of the simulations cannot be independently assessed.
- **Resolution test** Include complete QM/MM setup in the main text or supplementary, and provide a comparison of simulation outcomes with alternative charge models.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance
- **Claim pointer** The authors claim that antagonist binding reduces protection of bHLH residues, implying weakened DNA binding, while agonist binding increases protection, implying enhanced DNA binding.
- **Evidence pointer** Figure 2C, location not provided
- **Concern** The link between computed protection factors and actual DNA-binding affinity is inferred but not directly tested. No experimental or computational data on DNA binding are presented to support this claim.
- **Why it matters** The manuscript's central thesis is that these descriptors predict transcriptional activity. Without direct evidence connecting bHLH dynamics to DNA-binding function, the claim remains speculative.
- **Resolution test** Perform DNA-binding simulations or experiments (e.g., electrophoretic mobility shift assay) to correlate protection factors with binding affinity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Virtual screening validation
- **Claim pointer** The authors present a multiscale approach for high-throughput virtual screening to separate agonists, antagonists, and decoys.
- **Evidence pointer** Discussion, location not provided
- **Concern** The proposed framework is described as a strategy, but no prospective validation is shown. The authors do not demonstrate that the descriptors can identify novel modulators from a large chemical library.
- **Why it matters** The practical value of the work hinges on the framework's ability to enrich for true actives in real screening scenarios. Without validation, the approach remains a hypothesis.
- **Resolution test** Apply the framework to a test set of known modulators and decoys, and report enrichment factors and hit rates; ideally, include a prospective screen with experimental confirmation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1B
- **Evidence pointer** Figure 1B, location not provided
- **Issue** The distribution of cavity volumes is shown, but the y-axis label and units are not described in the text.
- **Required correction** Add axis labels and units to the figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Order parameters θ_M252 and φ_Y281
- **Evidence pointer** Figure 2A-B, location not provided
- **Issue** The definitions of these order parameters are given, but the rationale for choosing these specific geometric measures is not explained.
- **Required correction** Briefly justify why these parameters are sensitive to ligand-specific effects.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** MM/PBSA calculations
- **Evidence pointer** Figure 3B, location not provided
- **Issue** The authors note that MM/PBSA overestimates binding energies but do not provide error estimates or a discussion of the method's limitations in this context.
- **Required correction** Include standard deviations and a brief caveat about the method's applicability to protein-protein complexes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Simulation setup
- **Evidence pointer** Methods summary, location not provided
- **Issue** The number of replicates and total simulation time are stated, but the equilibration protocol and temperature/pressure coupling details are only in the supplementary.
- **Required correction** Summarize key equilibration steps in the main text for reproducibility.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 2D
- **Evidence pointer** Figure 2D, location not provided
- **Issue** The fraction of trajectories showing expected conformational changes is plotted, but the time points for the 100 ps and 10 ns observations are not clearly marked.
- **Required correction** Add time annotations or a time axis to clarify the temporal evolution.

## Risk / unsupported claims
- The claim that ΔΔG "completely separates" agonists from antagonists is unsupported due to the small ligand set and acknowledged decoy overlap.
- The claim that antagonist binding weakens DNA binding via bHLH dynamics is unsupported without direct DNA-binding data.
- The proposed virtual screening framework is presented without prospective validation, making its efficacy unassessable.
- The quantitative RMSF increase of 50% is unverifiable without statistical details.
- The use of QM/MM charges is described but not fully detailed, limiting reproducibility assessment.