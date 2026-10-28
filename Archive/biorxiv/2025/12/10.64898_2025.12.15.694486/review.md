## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, conclusions, methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, and support of claims based solely on the supplied material
- **Shared manuscript claim summary** The authors propose that methionine oxidation in the TDP-43 C-terminal domain disrupts phase separation through two distinct, position-dependent mechanisms: oxidation of methionines in the conserved region (CR) destabilizes the helical structure and impairs helix-helix association, while oxidation of methionines in the flanking intrinsically disordered regions (IDRs) disrupts long-range intramolecular contacts. Both mechanisms contribute to loss of phase separation.
- **Visible evidence base** Abstract, introduction, results narrative, conclusions, methods, figure legends referenced in text (Figures 1-6, S1-S18)
- **Missing materials affecting confidence** Actual figures and figure panels are not provided; numerical data (e.g., CSP magnitudes, Rg distributions, contact ratios) are described qualitatively only; statistical analyses are not reported; simulation convergence metrics beyond Rg autocorrelation are not fully described; AlphaFold model quality metrics are not provided

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question regarding the molecular mechanisms by which methionine oxidation disrupts TDP-43 phase separation. The combination of NMR spectroscopy and all-atom MD simulations is well suited to the problem, and the authors present a plausible dual-mechanism model. However, the current evidence base is incomplete in several respects. The experimental distinction between CR and IDR methionine oxidation relies on sequence variants that alter amino acid composition, and the interpretation of these results depends on assumptions about the equivalence of Ala-substituted and Met-oxidized states that are not fully validated. The simulation results are extensive but presented largely qualitatively, and the connection between monomer-level conformational changes and the observed loss of phase separation is inferred rather than directly demonstrated. The manuscript would be strengthened by quantitative reporting of key observables, explicit statistical comparisons, and a more direct test of the proposed mechanism.
- **Who would be interested in the results, and why** Researchers studying TDP-43 biology, ALS and FTD pathogenesis, biomolecular condensates and phase separation, oxidative stress in neurodegeneration, and the application of integrative structural biology (NMR plus simulation) to disordered proteins. The findings may also interest those developing therapeutic strategies targeting post-translational modifications in neurodegeneration.
- **Major strengths** The combination of experimental and computational approaches is appropriate and potentially powerful. The use of sequence variants to separate CR and IDR contributions is a reasonable strategy. The authors address a controversy in the literature (Lin et al. vs. Carrasco et al.) and provide a potential resolution. The simulation work is extensive, including multi-microsecond trajectories and dimer dissociation studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The work addresses a specific and under-explored question (position-dependent effects of methionine oxidation on TDP-43 CTD) and proposes a dual-mechanism model that goes beyond prior studies. The claim of distinct CR versus IDR mechanisms is novel. Scientific importance: TDP-43 pathology is central to ALS/FTD, and oxidative stress is a well-established disease correlate. Understanding how oxidation disrupts phase separation has clear translational relevance. However, the importance of the specific mechanistic distinction (CR versus IDR) for disease biology is not fully established in the manuscript. Interdisciplinary readership: The topic bridges biophysics, cell biology, and neurodegeneration, and should appeal to a broad audience. Technical soundness: The methods are generally appropriate, but several concerns (see below) limit confidence in the conclusions as currently presented. Readability for nonspecialists: The manuscript is generally well written and accessible, though some simulation details may be dense for experimental readers. Overall, the work has potential for a high-impact venue, but the current evidence does not fully establish the central claims.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and interpretation
- **Claim pointer** The authors claim that oxidation of CR methionines disrupts helical structure and impairs helix-helix association, while oxidation of IDR methionines disrupts long-range contacts, and that both contribute to loss of phase separation.
- **Evidence pointer** Results sections "Methionine oxidation of CTD disrupts phase separation and reduces CR helicity" and "Oxidation of methionine impairs phase separation regardless of position but disrupts CR helicity only upon CR oxidation"; Figures 2, 4
- **Concern** The central experimental strategy uses Ala-substitution variants (5M→A IDR and 5M→A CR + 5A→M IDR ) to isolate the contributions of CR versus IDR methionines. However, Ala substitution is not equivalent to methionine oxidation. Ala is smaller and less polar than methionine sulfoxide, and the authors previously showed that Ala substitution itself impairs phase separation (ref 54). The manuscript does not adequately address whether the observed effects in the variants are due to loss of methionine-mediated interactions (as intended) or to the introduction of Ala residues with different physicochemical properties. The 5M→A CR + 5A→M IDR variant is particularly problematic, as it introduces five new methionines into the IDRs, potentially creating new interaction surfaces that do not exist in the wild-type protein. The authors should provide control experiments or explicit justification for why Ala substitution is an appropriate proxy for the unoxidized state in these comparisons.
- **Why it matters** The central conclusion that CR and IDR methionines contribute to phase separation through distinct mechanisms depends on the validity of this experimental design. If the Ala substitutions introduce confounding effects, the interpretation of the variant experiments is not reliable.
- **Resolution test** Provide additional control experiments, such as comparing the phase separation behavior of the variants with and without oxidation to wild-type under matched conditions, or using a different substitution strategy (e.g., norleucine) that better mimics methionine hydrophobicity. Alternatively, provide direct evidence that the Ala-substituted variants behave equivalently to the unoxidized wild-type in terms of the specific interactions being probed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative evidence
- **Claim pointer** The authors claim that oxidation leads to "significant disruption of helical structure," "dramatic reorganization" of the interaction network, and "notably more expanded" conformations.
- **Evidence pointer** Results sections as above; Figures 2, 3, 5
- **Concern** Throughout the results, key observables are described qualitatively (e.g., "large CSPs," "strong positive value," "dramatic reduction," "notably more expanded") without reporting numerical values, uncertainties, or statistical significance. For example, the secondary chemical shift analysis (ΔδCα-δCβ) is described as showing a shift "closer to those of a random coil," but the actual values and the magnitude of the change are not provided. Similarly, the Rg distributions are described as "more expanded" but the mean values, standard deviations, and overlap between distributions are not reported. The contact ratio analysis in Figure 3E is described in terms of "nearly two-fold or more" decreases, but the underlying data and variability are not shown.
- **Why it matters** Nature-style manuscripts require quantitative reporting of key results to allow readers to assess the magnitude and significance of the observed effects. Without numerical data and statistical comparisons, the strength of the evidence cannot be evaluated.
- **Resolution test** Report numerical values for all key observables (CSP magnitudes, secondary chemical shifts, Rg means and distributions, contact ratios) with appropriate measures of uncertainty and statistical tests comparing conditions. Provide the data underlying Figures 2-5 in a supplementary table or source data file.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation methodology and validation
- **Claim pointer** The authors claim that multi-microsecond MD simulations provide mechanistic insights into how oxidation impacts CTD structure and interactions.
- **Evidence pointer** Computational Procedures; Figures 3, 5, S2-S18
- **Concern** The simulation methodology has several potential issues. First, the force field (Amber99sb-stq) and water model (TIP4P/2005s) are not commonly used together, and the authors do not validate this combination for TDP-43 CTD or for methionine sulfoxide. Second, the methionine sulfoxide parameters are taken from Irani et al. (2013), but the authors do not state whether these parameters were validated for the Amber99sb-stq force field. Third, the authors state that "there is no preferential formation of one diastereomer of Met sulfoxide" and therefore used only the R diastereomer, but this assumption may not hold in the context of the protein structure. Fourth, the dimer simulations are only 250 ns, which may be too short to observe meaningful dissociation events, especially if the dimer interface is stabilized by multiple contacts. The authors report that "most models showed significant loss of CR-CR contacts," but the criteria for "significant" are not defined.
- **Why it matters** The simulation results are used to support the mechanistic model, but if the force field parameters or simulation lengths are inadequate, the conclusions may not be reliable.
- **Resolution test** Provide validation of the force field and water model combination for this system, including comparison to experimental observables where possible. Justify the choice of the R diastereomer or test both diastereomers. Provide additional analysis of the dimer simulations, including the time course of dissociation and the criteria used to define "significant" loss of contacts. Consider longer simulations or enhanced sampling methods to ensure convergence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Connection between monomer and phase behavior
- **Claim pointer** The authors claim that monomer-level conformational expansion upon oxidation is "linked to CTD's inability to undergo phase separation."
- **Evidence pointer** Results section "Methionine oxidation promotes expansion of the CTD monomer and disrupts interactions involving polar, aliphatic, and aromatic residues"; Figure 3
- **Concern** The manuscript establishes a correlation between monomer expansion (in simulations) and loss of phase separation (in experiments), but the causal link is not directly demonstrated. The authors cite previous work establishing a correlation between chain compaction and phase separation propensity, but this correlation may not hold for all systems or under all conditions. The manuscript would be strengthened by a more direct test of the proposed mechanism, such as measuring the effect of oxidation on intermolecular interactions in a concentration-dependent manner, or by using simulation to directly probe the effect of oxidation on the free energy of phase separation.
- **Why it matters** The central claim of the manuscript is that oxidation disrupts phase separation through specific molecular mechanisms. If the link between monomer conformation and phase behavior is not established, the mechanistic model remains speculative.
- **Resolution test** Provide additional experimental or computational evidence directly linking the observed monomer-level changes to phase separation behavior. This could include measurements of intermolecular interactions (e.g., NMR relaxation dispersion, diffusion measurements) as a function of concentration and oxidation state, or coarse-grained simulations that directly model phase separation with and without oxidation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness of evidence for "all methionines are vulnerable"
- **Claim pointer** The authors claim that "all methionine residues are vulnerable to oxidation" based on mass spectrometry showing a ~176 Da increase corresponding to 11 oxygen atoms.
- **Evidence pointer** Results section "Methionine oxidation of CTD disrupts phase separation and reduces CR helicity"; Figure S1B
- **Concern** The mass spectrometry data show that the predominant species has all 11 methionines oxidized (10 native plus 1 cloning artifact), but the manuscript does not report the distribution of partially oxidized species. If partial oxidation states are present, the interpretation of the NMR and phase separation experiments may be complicated by heterogeneous samples. Additionally, the authors do not report whether the oxidation conditions (1% H2O2, 30 min) are saturating or whether longer exposure would lead to further modifications (e.g., over-oxidation to sulfone).
- **Why it matters** The claim that all methionines are vulnerable to oxidation is important for the interpretation of the experiments. If the sample is heterogeneous, the observed effects may be due to a subpopulation of fully oxidized protein, and the conclusions about position-dependent effects may not be straightforward.
- **Resolution test** Report the full mass spectrometry profile showing the distribution of oxidation states. If partial oxidation is present, discuss the implications for the interpretation of the results. Consider performing experiments with different oxidation times or H2O2 concentrations to establish the dose-response relationship.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure legends
- **Affected element** Figures 1-6 and S1-S18
- **Evidence pointer** Figure legends as referenced in text
- **Issue** The figure legends are not provided in the manuscript text, making it difficult to assess the specific details of each experiment and analysis.
- **Required correction** Include full figure legends with detailed descriptions of experimental conditions, sample sizes, and statistical analyses.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reporting of simulation replicates
- **Affected element** Computational Procedures
- **Evidence pointer** Computational Procedures section
- **Issue** The authors state that triplicate simulations were performed for the monomer systems, but the variability between replicates is not reported. The statement that "distinct (non-overlapping) peaks in the Rg distribution observed across the replicas" suggests significant inter-replicate variability, which may indicate insufficient sampling.
- **Required correction** Report the Rg distributions for each replicate separately and discuss the implications of inter-replicate variability for the conclusions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Definition of "long-range" contacts
- **Affected element** Results section "Methionine oxidation promotes expansion of the CTD monomer"
- **Evidence pointer** Results section; Figure 3C inset
- **Issue** The term "long-range" is used to describe interactions between residues with sequence separation exceeding 40 residues, but the rationale for this cutoff is not explained.
- **Required correction** Provide justification for the 40-residue cutoff or use a more standard definition of long-range contacts.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarification of the 5M→A CR + 5A→M IDR variant design
- **Affected element** Results section "Oxidation of methionine impairs phase separation regardless of position but disrupts CR helicity only upon CR oxidation"
- **Evidence pointer** Results section; Figure S8A
- **Issue** The rationale for the specific Ala-to-Met substitutions in the IDRs of the 5M→A CR + 5A→M IDR variant is not fully explained. The authors state that this variant "preserves the overall amino acid composition," but the choice of which Ala positions to convert to Met is not justified.
- **Required correction** Provide a clear explanation of the design rationale, including how the specific Ala positions were selected and whether these positions are structurally or functionally relevant.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Conclusions
- **Evidence pointer** Conclusions section
- **Issue** The conclusions section does not discuss the limitations of the study, such as the use of Ala-substitution variants, the potential for heterogeneous oxidation, or the limitations of the simulation approach.
- **Required correction** Add a paragraph discussing the limitations of the study and the potential impact of these limitations on the conclusions.

## Risk / unsupported claims
- The claim that "oxidation of CR methionines disrupts helical structure and directly impairs intermolecular helical association" is partially supported by NMR and simulation data, but the direct link to intermolecular association is inferred from monomer simulations and not directly measured.
- The claim that "oxidation of IDR methionines disrupts long-range contacts" is supported by simulation data, but the experimental evidence for this specific mechanism is indirect.
- The claim that "all methionine residues are vulnerable to oxidation" is supported by mass spectrometry, but the distribution of partial oxidation states is not reported, and the functional significance of partial oxidation is not addressed.
- The claim that "these findings establish methionines as critical redox-sensitive modulators of TDP-43 phase behavior" is a reasonable interpretation, but the physiological relevance is not directly demonstrated in this manuscript.
- The claim that the observed effects "provide molecular insights into how oxidative stress may contribute to TDP-43 dysregulation in neurodegenerative diseases" is speculative and not directly tested.
- The simulation results are presented as supporting the experimental findings, but the force field validation and convergence criteria are not fully described, limiting the confidence in these results.