## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and support of claims by presented evidence; not editorial or formatting issues
- **Shared manuscript claim summary** The authors characterize the N-terminal low complexity domain of EWS (EWS LCD) using NMR, analytical ultracentrifugation, microscopy, and atomistic simulations, proposing that tyrosine residues drive intramolecular interactions and phase separation, that the domain adopts a tripartite architecture with compact N- and C-termini connected by an extended linker, and that dilute-phase interactions inform condensed-phase behavior.
- **Visible evidence base** Abstract; Introduction; Materials and Methods (protein purification, fluorescent labeling, microscopy, turbidity, pelleting, AUC, SEC, NMR including PRE, CG and AA simulations); Results sections on domain architecture, physicochemical properties, dynamics, tyrosine mutagenesis, and condensed-phase simulations; Discussion; Supplemental figure/table descriptions (content not provided)
- **Missing materials affecting confidence** Supplemental figures and tables (Supp. Figs. 1–7, Supp. Tables 1–2) are referenced but not provided; NMR assignment details and spectra are not shown; raw turbidity and pelleting data are not shown; simulation parameters for condensed-phase systems are partially described; no sequence alignment or conservation analysis is shown

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive biophysical and computational study of the EWS LCD, addressing an important gap in understanding FET family phase separation. The combination of experimental and simulation approaches is ambitious and potentially valuable. However, the central claims regarding tyrosine-driven interactions and the transferability of dilute-phase contacts to the condensed phase rest on indirect evidence and cross-method comparisons that are not fully validated. Several key controls and quantitative comparisons are missing, and the presentation of results is at times difficult to follow. The work is of interest to the phase separation and FET protein communities, but the case is not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers studying biomolecular condensates and liquid-liquid phase separation, particularly those focused on FET family proteins (FUS, EWS, TAF15) and their roles in cancer and neurodegeneration. The study also speaks to the broader community interested in sequence determinants of phase separation, the use of integrative structural biology approaches for intrinsically disordered proteins, and the relationship between single-chain behavior and condensed-phase properties. The methodological framework combining NMR, simulations, and mutagenesis may serve as a template for similar studies.
- **Major strengths** 1) Addresses a significant knowledge gap by directly studying EWS LCD rather than inferring behavior from FUS. 2) Integrates multiple complementary techniques (NMR, AUC, SEC, turbidity, microscopy, CG and AA simulations) to build a multiscale picture. 3) The comparison between dilute-phase intramolecular contacts and condensed-phase intermolecular contacts is conceptually important. 4) Mutational analysis targeting tyrosine residues provides causal evidence for their role. 5) The observation of domain-level architectural differences between EWS and FUS LCDs is novel and potentially impactful.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1 (tyrosine claim), R1-M2 (dilute-to-condensed transferability), R1-M3 (simulation-experiment agreement), R1-M4 (condensed-phase simulation validation)
- **Assessment against Nature-style criteria** Originality: The study is original in its focus on EWS LCD and its integrative approach, though the conceptual framework (tyrosine-driven phase separation, dilute-to-condensed correspondence) builds on prior FUS work. Scientific importance: Potentially high for understanding FET family biology and EWS::FLI1 oncogenesis, but the impact is tempered by the indirect nature of key evidence. Interdisciplinary readership: The work bridges biophysics, structural biology, and cancer biology, and should appeal to a broad readership if the claims are solidified. Technical soundness: The methods are generally appropriate, but several validation steps are missing, and the quantitative agreement between experiment and simulation is not rigorously established. Readability for nonspecialists: The manuscript is dense and assumes significant background in NMR and simulation methods; the logic of the results section could be streamlined for broader accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the validation of tyrosine-mediated interactions, the quantitative comparison between dilute and condensed phases, and the demonstration that simulation results faithfully reproduce experimental observations.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim that "tyrosine residues primarily drive the interactions vital for EWS LCD phase separation" and that "a higher density and proximity of tyrosine residues amplify the likelihood of condensate formation."
- **Evidence pointer** Results sections "Tyrosine Residues Mediate Phase Separation of the EWS LCD" and "Tyrosine Residues Affect the Dynamics of EWS LCD"; Figures 4 and 5 (referenced, not shown); Table 1 (referenced, not shown)
- **Concern** The claim that tyrosine residues are the primary driver of phase separation is supported by turbidity and pelleting assays on mutant constructs, but the evidence is presented qualitatively. The phase diagrams in Figure 4 are described but not shown, and the quantitative shift in saturation concentration (C sat) upon mutation is not reported with error bars or statistical significance. The authors state that single point mutations "slightly increase" solubility while Y170S or Y170S/Y172S "enhance" solubility, but no numerical values are provided. The 7YS and 13YS mutants show greater than 90% solubility, but the relationship between the number of tyrosines mutated and the observed effect is not systematically analyzed. Furthermore, the claim that "density and proximity" of tyrosines matter is based on the YxY and YxxY motif analysis, but no direct test of spacing versus number is presented. The simulation data in Figure 5C show decreased contacts upon mutation, but the correlation with experimental phase behavior is not quantified.
- **Why it matters** The central mechanistic claim of the paper rests on the role of tyrosines. Without quantitative evidence linking specific mutations to changes in phase separation propensity, and without demonstrating that the effect is due to loss of tyrosine-mediated interactions rather than general perturbation of the sequence, the claim remains suggestive rather than established. This is critical because the authors use this claim to differentiate EWS from FUS and to propose therapeutic implications.
- **Resolution test** Provide quantitative phase diagrams with C sat values and error bars for WT and all mutants. Perform a systematic analysis correlating the number and position of mutated tyrosines with the observed shift in phase boundary. Include a control mutation of non-aromatic residues in the same regions to rule out general sequence perturbation effects. Report statistical significance for all comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim that "interactions observed in the dilute phase inform on atomic interactions driving phase separation" and that condensed-phase simulations show "a strong correlation" between dilute and condensed phase contact patterns.
- **Evidence pointer** Results section "Condensed Phase Intermolecular Contacts Mimic Intramolecular Interactions in the Dilute Phase"; Figures 6C and 6D (referenced, not shown)
- **Concern** The transferability of dilute-phase intramolecular contacts to condensed-phase intermolecular interactions is a key conceptual claim, but the evidence is indirect. The correlation between dilute and condensed phase contact maps is stated but not quantified with a correlation coefficient or statistical test. The comparison is made between single-chain simulations in dilute conditions and multi-chain simulations in a slab geometry, but the two systems differ in concentration, temperature, and possibly force field parameters. The authors do not address whether the observed correlation is specific to EWS LCD or would be expected for any disordered protein. The claim that "the same residue types responsible for compaction in a dilute phase also serve to stabilize the condensed phase" is supported only by qualitative similarity in contact patterns, not by direct measurement of interaction energies or free energies in the condensed phase.
- **Why it matters** The claim that dilute-phase measurements can predict condensed-phase behavior is methodologically important and would have broad implications for studying phase-separating systems. If this claim is not rigorously established, the relevance of the extensive dilute-phase NMR and simulation data to understanding phase separation is weakened. The authors themselves note that condensed-phase NMR was not feasible, so the simulation comparison is the only bridge between the two regimes.
- **Resolution test** Provide a quantitative correlation analysis (e.g., Pearson or Spearman correlation coefficients) between dilute and condensed phase contact maps, with appropriate statistical testing. Discuss whether the observed correlation is expected from polymer physics or is specific to the sequence. Consider validating the condensed-phase simulations against experimental observables such as saturation concentration or cluster size distributions. If possible, perform a limited set of condensed-phase NMR experiments or use alternative experimental probes to test the predicted intermolecular contacts.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical rigor
- **Claim pointer** The authors state that "relaxation rates from single chain atomistic simulations with 15 μs total run time reproduces the salient features of the experimental data, which gives us confidence for using the simulated ensemble in interpreting the underlying molecular details."
- **Evidence pointer** Results section "Peptide Chain Dynamics and Self-Association of the EWS LCD"; Supp. Fig. 3 (referenced, not shown); Methods section "All-Atom (AA) Simulation"
- **Concern** The agreement between simulation and experiment is stated qualitatively, but no quantitative comparison is provided. The authors note that simulation rates are "slower than experiment" and suggest reweighting strategies, but they do not apply such strategies or quantify the discrepancy. The R2 profile from simulations is said to show a "similar trend" to experimental data, but the magnitude of the differences is not reported. The simulation time of 15 μs per system may be insufficient for a 264-residue disordered protein to fully sample conformational space, and the authors do not demonstrate convergence. The choice of force field (Amber99SBws-STQ) and water model (TIP4P/2005) is appropriate, but the authors do not compare with alternative force fields or discuss potential biases.
- **Why it matters** The simulations are used to interpret the experimental NMR data and to make claims about the conformational ensemble and contact networks. If the simulations do not quantitatively reproduce experimental observables, the interpretations drawn from them are uncertain. The authors' confidence in the simulated ensemble is central to several conclusions, including the tripartite architecture and the role of specific residue types.
- **Resolution test** Provide quantitative metrics of agreement between simulated and experimental relaxation rates (e.g., root-mean-square deviation, correlation coefficients). Demonstrate convergence of the simulations by showing that observables are stable over time and across replicas. If reweighting is needed, apply it and show how the conclusions change. Consider comparing with an alternative force field to assess robustness.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical rigor
- **Claim pointer** The authors use condensed-phase atomistic simulations with 25 chains in a slab geometry to draw conclusions about the condensed phase, including chain expansion and intermolecular contact patterns.
- **Evidence pointer** Methods section "AA Condensed Phase Simulation"; Results section "Condensed Phase Intermolecular Contacts Mimic Intramolecular Interactions in the Dilute Phase"; Figure 6 (referenced, not shown)
- **Concern** The condensed-phase simulation methodology is described briefly, and several critical details are missing. The system size (25 chains) is small, and finite-size effects may be significant. The simulation length (1 μs production) may be insufficient to equilibrate a multi-chain system, and the authors do not show that the system has reached steady state. The method for preparing the initial configuration from CG simulations is described, but the equilibration protocol is not detailed. The authors do not report the density or concentration of the condensed phase, which is essential for interpreting the results. The comparison between dilute and condensed phases is made at different temperatures (300 K for dilute, 320 K for condensed), which complicates the interpretation.
- **Why it matters** The condensed-phase simulations are the primary evidence for the claim that dilute-phase interactions inform condensed-phase behavior. If the simulations are not well-equilibrated or are subject to finite-size artifacts, the conclusions drawn from them are unreliable. The temperature difference between dilute and condensed simulations is particularly concerning, as it could affect the contact patterns and chain conformations.
- **Resolution test** Provide details on system size, density, and equilibration. Show that the condensed-phase system is stable over the production run and that observables have converged. Discuss the potential impact of finite-size effects and consider larger systems if feasible. Justify the temperature difference or perform simulations at matching temperatures. Report the concentration of the condensed phase and compare with experimental estimates.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "EWS Domain Architecture and Differences between FUS and EWS"
- **Evidence pointer** Figure 1 (referenced, not shown)
- **Issue** The description of the domain architecture comparison between EWS and FUS is clear, but the figure is not available for review. The claim that EWS is "enriched in alanine, threonine, and proline and depleted in glycine" would benefit from a quantitative comparison, such as a composition difference plot or a table of residue frequencies.
- **Required correction** Provide the figure or a quantitative summary of residue composition differences to support the textual claims.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Nuclear Magnetic Resonance"
- **Evidence pointer** Methods section "Nuclear Magnetic Resonance"
- **Issue** The NMR methods section describes the experiments but does not provide key acquisition parameters, such as the number of scans, relaxation delays, or the concentration of the NMR samples. The assignment of backbone resonances is mentioned but not described.
- **Required correction** Add the missing acquisition parameters and a brief description of the assignment strategy, or reference a prior publication where these details are provided.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "Tyrosine Residues Affect the Dynamics of EWS LCD"
- **Evidence pointer** Figure 5 (referenced, not shown)
- **Issue** The interpretation of the PRE data for the 7YS mutant is somewhat ambiguous. The authors state that PREs are "prominently reduced" when the spin label is within the mutated region, but it is not clear whether this is due to loss of specific interactions or to a general change in the conformational ensemble. The comparison between the S40C and S260C positions is interesting but could be discussed more explicitly.
- **Required correction** Clarify the interpretation of the PRE differences and discuss alternative explanations, such as changes in local dynamics or overall compaction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the yin-yang hypothesis from Chong et al. is brief and could be expanded. The authors mention that their results provide "necessary insight" but do not explicitly connect their findings to the proposed mechanism of transcriptional activation versus repression.
- **Required correction** Expand the discussion to explicitly state how the EWS LCD structural and interaction data inform the proposed dual roles of the FET fusion proteins in transcription.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Coarse-Grained (CG) Simulation"
- **Evidence pointer** Methods section "Coarse-Grained (CG) Simulation"
- **Issue** The CG simulation methods are described briefly, and the HPS-Urry model parameters are not provided. The temperature for CG simulations is not stated, and the protocol for determining C sat from simulations is not described in detail.
- **Required correction** Provide the model parameters, simulation temperature, and a clear description of how C sat was extracted from the coexistence simulations.

## Risk / unsupported claims
- The claim that "tyrosine residues primarily drive the interactions vital for EWS LCD phase separation" is not quantitatively supported by the presented data; the phase diagrams and C sat values are not shown.
- The claim that "a higher density and proximity of tyrosine residues amplify the likelihood of condensate formation" is based on motif analysis but lacks direct experimental testing of spacing versus number.
- The claim that "interactions observed in the dilute phase inform on atomic interactions driving phase separation" is supported only by qualitative similarity in contact maps; no quantitative correlation is provided.
- The claim that "the C-terminal region is the most FUS-like in terms of sequence composition" is stated without a quantitative sequence comparison.
- The claim that "the results presented here provide the necessary insight into the structure and function of EWS LCD" is an overstatement given the indirect nature of several key pieces of evidence.
- The statement that "elevated PRE rates were observed when spin labels introduced within the N-terminal or C-terminal regions compared with the PRE rates arising from spin-labels placed in the central linker region" is not fully supported by the data shown in the text; the PRE profiles are not displayed.
- The claim that "the simulations support the experimental observations, that compared to FUS LCD, EWS LCD forms droplets at lower protein concentrations and its critical temperature is higher" is based on CG simulations that are not validated against experimental phase diagrams for EWS LCD.