## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, data availability) without supplementary figures, tables, or detailed protocols
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive consistency as presented in the main text; supplementary materials referenced but not independently verifiable from the provided content
- **Shared manuscript claim summary** The authors propose an extended photocycle for the LOV–HTH transcription factor EL222, in which photoexcitation of FMN leads sequentially to a covalent FMN–Cys78 adduct state (lit1) and a fully reduced, noncovalent hydroquinone state (lit2). They argue that these distinct flavin redox/adduct states differentially shift EL222 toward an open conformation, promoting oligomerization and DNA binding, and that DNA binding occurs in the dark as a transient encounter complex but only becomes stable and high-population under blue light.
- **Visible evidence base** Crystal structures (PDB 8A5R, 8A5S) at 1.85 Å; solution NMR (1H–15N correlation spectra, T2 relaxation, DOSY, TRACT); IR and UV–visible spectroscopy; MD and metadynamics simulations; engineered variants (C78A, AQTrip, W31pCNF)
- **Missing materials affecting confidence** Supplementary Tables S1–S5, Supplementary Figures S1–S16, detailed MD/metaD parameters, NMR assignment statistics, crystallographic refinement statistics, and kinetic fitting details were not provided. These are essential for full assessment of data quality, particularly for the lit2 state characterization and the metadynamics conclusions.

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious and largely well-executed multi-method study of the EL222 photocycle. The identification and characterization of a second lit state (lit2) with fully reduced FMN is potentially significant, and the authors are appropriately cautious in framing its physiological relevance. The combination of crystallography, NMR, vibrational spectroscopy, and simulation is appropriate and complementary. However, several central claims—particularly the sequential population of lit1 and lit2 under illumination, the structural distinction between lit1 and lit2, and the quantitative interpretation of DNA-binding equilibria—rest on data presented in supplementary materials that were not available for assessment. The dark-state DNA encounter complex is an interesting observation, but the evidence that this complex is functionally distinct from the lit-state complexes is indirect. The metadynamics results are suggestive but presented with insufficient methodological detail to evaluate their robustness. Overall, the work is potentially important for the optogenetics and LOV photoreceptor communities, but the core conclusions are not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in optogenetics, particularly those using EL222 or related LOV–HTH transcription factors for light-controlled gene expression, will be directly interested in the refined mechanistic model of activation, including the existence of a second lit state and its implications for dynamic range and reversibility. The broader photoreceptor community studying LOV domain photochemistry and signal transduction will find the flavin redox state analysis and the proposed coupling between FMN chemistry and conformational equilibria of interest. Methodologically, the integrative use of NMR, IR, and MD/metaD to characterize protein conformational states in solution will appeal to structural biologists working on dynamic protein systems.
- **Major strengths** The study employs a genuinely integrative and complementary set of methods, each applied under photostationary conditions where possible, which is a notable strength. The identification of a second, slowly accumulating lit state (lit2) with fully reduced FMN extends the current understanding of LOV photocycles and is well supported by the combination of NMR, UV–visible, and IR data, even if the full evidence is in the supplementary materials. The use of the C78A mutant and the W31pCNF infrared probe are elegant controls that strengthen the assignment of the lit1 state to the covalent adduct. The observation of a dark-state DNA encounter complex with fast exchange kinetics is a novel and potentially important contribution. The authors are appropriately cautious in discussing the physiological relevance of lit2 and the limitations of their metadynamics approach.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency for a central claim
  - **Claim pointer** The manuscript claims that two distinct lit states (lit1 and lit2) become sequentially populated under continuous illumination, with lit1 being the covalent N5-protonated adduct and lit2 being the noncovalent, fully reduced hydroquinone form.
  - **Evidence pointer** Results section, Figures 2 and 3, Supplementary Figures S3, S5, S7, S10; location not provided for specific data points
  - **Concern** The sequential population of lit1 and lit2 is a central claim of the paper, but the kinetic evidence for this sequence is presented only in supplementary figures (S3) that were not available for review. The NMR spectra showing the lit1 and lit2 states are described but not shown in the main text. The assignment of lit2 as the fully reduced hydroquinone relies on UV–visible spectra (Supplementary Fig. S10) and NMR data (Supplementary Fig. S7) that are not presented. Without these data, the existence and identity of lit2 cannot be independently evaluated.
  - **Why it matters** The entire mechanistic model proposed in the paper—that the flavin redox state, not just adduct formation, controls EL222 conformation and DNA binding—depends on the correct identification and characterization of lit2. If lit2 is an artifact of prolonged illumination or oxygen depletion rather than a physiologically relevant state, the conclusions would be substantially weakened.
  - **Resolution test** Provide the supplementary figures and tables, including kinetic traces for lit1-to-lit2 conversion, UV–visible spectra of the lit2 state, and NMR assignment data. The authors should also clarify the quantum yield and oxygen dependence of lit2 formation, and discuss whether lit2 can form under conditions relevant to optogenetic applications.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Interpretive validity of DNA-binding conclusions
  - **Claim pointer** The manuscript claims that all three EL222 states (dark, lit1, lit2) can associate with DNA, but only under blue-light irradiation is a high population of stable complexes obtained, and that lit1 forms 100% 2:1 complexes while lit2 forms only ~75%.
  - **Evidence pointer** Results section, Figures 5 and 6, Supplementary Figures S15 and S16; location not provided for specific data points
  - **Concern** The dark-state DNA encounter complex is inferred from NMR chemical shift perturbations and intensity losses, but the authors do not provide a quantitative binding affinity or kinetic rate constants for this interaction. The claim that lit1 forms 100% 2:1 complexes is based on NMR intensity reductions, which could also be explained by intermediate-exchange broadening or precipitation. The comparison between lit1 and lit2 DNA-binding is made using different experimental conditions (WT vs C78A mutant), which may not be directly comparable.
  - **Why it matters** The functional significance of the different flavin states for DNA binding is a key conclusion of the paper. If the dark-state encounter complex is not quantitatively characterized, or if the lit1/lit2 comparison is confounded by the use of different protein variants, the claim that flavin redox state controls DNA-binding activity is not firmly established.
  - **Resolution test** Provide quantitative binding affinities (e.g., from ITC or fluorescence anisotropy) for dark, lit1, and lit2 states. Clarify whether the C78A mutant is a valid proxy for the lit2 state of the WT protein. Provide evidence that the NMR intensity changes reflect a true 2:1 complex rather than aggregation or exchange broadening.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological robustness of simulations
  - **Claim pointer** The metadynamics simulations reveal that the covalent adduct state (lit1) has shorter domain separation times and lower bias requirements compared to oxidized and reduced states, supporting the view that adduct formation enables large-scale conformational changes.
  - **Evidence pointer** Results section, Figure 4, Supplementary Figures S13 and S14; location not provided for specific data points
  - **Concern** The metadynamics methodology is described only briefly. Key parameters such as the collective variable definition, bias deposition rate, convergence criteria, and the number of replicas are not provided in the main text. The normalization of separation times relative to the oxidized state is described, but the absolute values and statistical uncertainties are not reported. The authors acknowledge that the simulations were not intended to yield absolute kinetic values, but the comparative claims (0.75 vs 0.93 vs 1.0) require error estimates to be meaningful.
  - **Why it matters** The simulation results are used to support the mechanistic interpretation that adduct formation specifically accelerates domain separation. Without proper error analysis and methodological detail, these comparative claims could be overinterpreted.
  - **Resolution test** Provide full metadynamics parameters, convergence checks, and error bars for the separation times and bias values. If possible, include additional replicas or alternative collective variables to demonstrate robustness.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Structural interpretation of crystallographic data
  - **Claim pointer** The crystal structures of dark and lit states show only subtle differences, with the lit state containing a mixture of noncovalent and covalent FMN populations (70%/30% occupancy).
  - **Evidence pointer** Results section, Figure 1, Supplementary Tables S2 and S3; location not provided for specific data points
  - **Concern** The occupancy refinement of 70%/30% for the two FMN populations in the lit structure is a critical parameter, but the refinement details and the evidence supporting this specific ratio are not presented in the main text. The authors do not discuss whether alternative occupancy ratios or disordered models were tested. The functional significance of a 30% adduct population in the crystal is unclear, especially given that the solution studies suggest much higher conversion.
  - **Why it matters** The crystallographic data are used to support the claim that the lit1 state is structurally similar to the dark state. If the occupancy refinement is not robust, or if the crystal structure does not represent the dominant solution state, this conclusion is weakened.
  - **Resolution test** Provide refinement statistics including R-free, occupancy refinement details, and difference density maps. Discuss whether the 30% occupancy is consistent with the solution population of lit1 under the illumination conditions used.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness of methods
  - **Affected element** Materials and methods, MD simulation section
  - **Evidence pointer** Materials and methods, "Molecular modeling simulations" subsection; location not provided
  - **Issue** The description of the MD simulations states that production runs lasted 1 ms, which is likely a typo for 1 μs or 1 ns. Standard all-atom MD simulations of a protein of this size cannot reach millisecond timescales.
  - **Required correction** Correct the simulation time unit and provide the actual simulation length, number of replicas, and force field version used.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results section, NMR data
  - **Evidence pointer** Results section, "EL222 photocycle in solution" subsection; location not provided
  - **Issue** The authors state that lit1 converts to lit2 on a timescale of hours but do not provide the actual rate constant or half-life. The statement that the conversion rate increases linearly with light power is mentioned but the data are only in supplementary figures.
  - **Required correction** Provide the rate constants and their light-power dependence in the main text or clearly reference the supplementary figure and table numbers.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion, first paragraph; location not provided
  - **Issue** The authors use the term "in crystallo" which is nonstandard; the common term is "in crystallo" is occasionally used, but "crystallographic" or "in the crystal" would be clearer.
  - **Required correction** Replace with "crystallographic studies" or "in the crystal state" for clarity.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretive caution
  - **Affected element** Discussion section, lit2 physiological relevance
  - **Evidence pointer** Discussion, paragraph on lit2; location not provided
  - **Issue** The authors state that lit2 is not expected to be an abundant intermediate in canonical LOV photocycles but then suggest it may play a role in noncanonical LOV proteins. This speculation is reasonable but could be more clearly separated from the experimental findings.
  - **Required correction** Clearly distinguish between experimentally supported conclusions and speculative extensions in the discussion.
- **Technical failings that need to be addressed before the case is established** R1-M1 (evidence for lit2 identity and sequential population), R1-M2 (quantitative DNA-binding data), R1-M3 (metadynamics error analysis), R1-M4 (crystallographic occupancy refinement details). The manuscript also contains a likely typo in the simulation time (1 ms) that must be corrected.
- **Assessment against Nature-style criteria**  
  *Originality*: The identification of a second lit state (lit2) with fully reduced FMN in a LOV–HTH transcription factor is novel and extends the current photocycle model. The observation of a dark-state DNA encounter complex is also original. However, the overall conceptual framework—light-induced conformational change leading to DNA binding—is well established for EL222.  
  *Scientific importance*: The findings have clear relevance for optogenetics and for understanding LOV domain signaling diversity. The potential physiological role of lit2 in noncanonical LOV proteins is intriguing but speculative. The importance is moderate to high, depending on the robustness of the lit2 characterization.  
  *Interdisciplinary readership*: The work bridges photochemistry, structural biology, and biophysics, and will appeal to researchers in these fields. The optogenetics community will be particularly interested. The writing is accessible to specialists but may be challenging for a broader audience.  
  *Technical soundness*: The multi-method approach is appropriate and generally well executed. However, the central claims rely heavily on supplementary data that were not available for review, and the metadynamics analysis lacks error estimates. The crystallographic occupancy refinement requires additional detail.  
  *Readability for nonspecialists*: The abstract and introduction are clear, but the results section assumes substantial background knowledge in NMR spectroscopy and flavin photochemistry. The discussion is well written and places the findings in context.
- **Recommendation posture** Supportive if technical concerns are resolved. The study is potentially important and the methodology is largely appropriate, but the central claims regarding lit2 and the quantitative DNA-binding conclusions cannot be fully evaluated from the provided evidence. The authors should be asked to provide the supplementary data, address the methodological concerns, and correct the simulation time typo before the case is established.

## Risk / unsupported claims
- The claim that lit2 is a fully reduced, noncovalent hydroquinone state is not fully supported by the data presented in the main text; the UV–visible and NMR evidence is only in supplementary materials.
- The claim that lit1 converts to lit2 sequentially under continuous illumination is supported only by supplementary kinetic data.
- The claim that lit1 forms 100% 2:1 DNA complexes while lit2 forms only ~75% is based on NMR intensity changes that could have alternative explanations.
- The metadynamics-derived relative domain separation times (0.75, 0.93) are presented without error estimates, making the comparative claims difficult to evaluate.
- The speculation that lit2 may play a physiological role in noncanonical LOV proteins is not experimentally supported.
- The statement that the lit2 state is not expected to be an abundant intermediate in canonical LOV photocycles is presented as a conclusion but is largely based on the authors' specific experimental conditions.