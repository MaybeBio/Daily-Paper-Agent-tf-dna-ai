## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv 2023.01.18.524603)
- **Assessment boundary** Structural model, NMR validation, biochemical and single-molecule DNA-binding assays, cross-species modeling
- **Shared manuscript claim summary** The authors report a structural model of the Rec114–Mei4 trimer interface, validate it by NMR, and demonstrate that this minimal domain binds DNA, forms condensates, and bridges coaligned DNA molecules in a reversible, force-generating manner
- **Visible evidence base** Main text, figures referenced (Figs 1–6, supplementary figures s1–s11), methods section
- **Missing materials affecting confidence** Supplementary figures and tables not provided in full; supplemental movies referenced but not available; raw NMR chemical shift assignments not deposited; AlphaFold2 model coordinates not provided as supplementary file

## Reviewer
- **Overall assessment** This manuscript presents a compelling structural and functional characterization of the Rec114–Mei4 trimer interface, a key meiotic DSB factor. The combination of AlphaFold2 modeling, NMR validation, and single-molecule experiments is well integrated and the conclusions are largely supported by the data shown. The DNA-bridging activity is novel and of broad interest. However, several technical concerns regarding the interpretation of single-molecule data, the quantitative treatment of binding affinities, and the generalizability of the structural model across species require clarification before the case is fully established.
- **Who would be interested in the results, and why** Researchers in meiosis and recombination, chromosome dynamics, structural biology of protein–DNA interactions, and biophysics of condensate formation. The DNA-bridging and force-generating activities are relevant to the broader field of genome organization and phase-separated nuclear bodies.
- **Major strengths** 1) First structural model of the Rec114–Mei4 trimer interface, validated by NMR. 2) Demonstration that the minimal domain is sufficient for DNA binding and condensation. 3) Novel single-molecule evidence for reversible DNA bridging with force generation. 4) Cross-species structural predictions despite low sequence conservation. 5) Clear writing and logical flow from structure to function.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (single-molecule bridging interpretation), R1-M2 (quantitative binding affinity), R1-M3 (cross-species generalizability)
- **Assessment against Nature-style criteria** **Originality**: High. The DNA-bridging activity is unexpected and provides a new mechanistic framework for RM function. **Scientific importance**: High. Meiotic DSB regulation is a fundamental process, and the structural and mechanistic insights are significant. **Interdisciplinary readership**: Moderate to high. The work bridges structural biology, biophysics, and meiosis research, but the single-molecule methods may be less accessible to non-specialists. **Technical soundness**: Generally good, but with concerns noted below regarding quantitative interpretations and controls. **Readability for nonspecialists**: Good. The abstract and introduction are clear, and the figures are well organized, though some methods details are dense.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the interpretation of single-molecule bridging data and the quantitative treatment of binding affinities.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of single-molecule data
- **Claim pointer** "We conclude that the RM-TMD domain has a bridging activity that is able to bundle DNA molecules together reversibly."
- **Evidence pointer** Figure 5, Supplemental Movies 1–3
- **Concern** The conclusion that the RM-TMD domain bridges DNA molecules is based on observations of protein binding along coaligned DNA tethers and bundling of dangling DNA. However, the authors do not provide a quantitative analysis of the stoichiometry of protein complexes at bridging sites, nor do they rule out the possibility that the observed bundling is due to non-specific protein aggregation rather than specific bridging activity. The sudden appearance of bright foci (Fig. 5g) is interpreted as pre-formed assemblies, but the composition and specificity of these assemblies are not characterized.
- **Why it matters** The claim of a specific DNA-bridging activity is central to the manuscript's significance. If the observed effects are due to non-specific aggregation, the mechanistic conclusions would be substantially weakened.
- **Resolution test** Provide quantitative analysis of fluorescence intensity at bridging sites to estimate protein copy number. Perform control experiments with a non-DNA-binding mutant or with a protein that lacks the trimerization interface to demonstrate specificity. Characterize the composition of the bright foci (e.g., by single-molecule pull-down or co-localization with labeled DNA).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative binding affinity
- **Claim pointer** "The RM-TMD domain showed roughly comparable abilities to bind to linear DNA substrates of different lengths ranging from 80 to 1000 bp (C50 of ~80–100 nM), while binding to a 20-bp substrate occurred with substantially lower apparent affinity (C50 of ~800 nM)."
- **Evidence pointer** Figure 4a,b, Figure s7
- **Concern** The authors use C50 values (concentration at 50% binding) as a proxy for affinity, but acknowledge they cannot estimate Kd due to unknown stoichiometry. However, the comparison of C50 values across different DNA lengths is only meaningful if the number of binding sites per DNA molecule is similar, which is not established. The authors also do not report error bars or replicate numbers for the C50 measurements, making it difficult to assess the significance of the differences.
- **Why it matters** The claim that the minimal domain binds DNA with length-dependent affinity is used to support the model of cooperative binding. Without proper quantitative treatment, this conclusion is not robust.
- **Resolution test** Provide replicate measurements with error bars. Estimate the number of protein binding sites per DNA molecule (e.g., by stoichiometry analysis in EMSA or by fluorescence correlation spectroscopy). If possible, perform competition experiments to estimate true Kd values.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Cross-species generalizability
- **Claim pointer** "AlphaFold2 predicts similar structural models for RM orthologs across diverse taxa despite their low degree of sequence similarity."
- **Evidence pointer** Figure 3d,e, Figure s6c
- **Concern** The authors show AlphaFold2 models for RM orthologs from S. pombe, mouse, Arabidopsis, and C. elegans, but they do not provide quantitative measures of structural similarity (e.g., RMSD between models) or confidence scores for the key interface residues. The statement that the models are "similar" is qualitative. Additionally, the functional significance of the variable DNA-binding surface (Fig. 6d) is not experimentally tested in any non-yeast system.
- **Why it matters** The claim of evolutionary conservation of the trimer interface is important for the generalizability of the findings. Without quantitative comparison and functional validation in at least one other species, the claim remains speculative.
- **Resolution test** Provide RMSD values for the aligned models and pLDDT scores for interface residues. If possible, test DNA-binding activity of a non-yeast RM-TMD domain (e.g., mouse) to determine whether the variable surface affects function.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** NMR validation
- **Affected element** Figure 2, Figure s2
- **Evidence pointer** Figure 2c,d, Figure s2
- **Issue** The NMR validation is based on chemical shift assignments and TALOS-N secondary structure predictions, but the authors do not report the completeness of assignments or provide a deposition number for the chemical shifts. The number of assigned residues is not stated.
- **Required correction** Report assignment completeness and deposit chemical shifts in a public database (e.g., BMRB). State the number of assigned residues for both Rec114C and Mei4N.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** AFM analysis
- **Affected element** Figure 4c,g,h, Figure s7
- **Evidence pointer** Figure 4c,g,h
- **Issue** The AFM analysis of protein-DNA complexes relies on volume measurements to estimate protein copy number, but the calibration of the volume-to-protein-number conversion is not described in detail. The authors state an average of 2.2 particles per DNA molecule, but the distribution of particle sizes is not shown.
- **Required correction** Provide a more detailed description of the volume calibration, including the protein density assumption and the uncertainty in the estimate. Show the distribution of particle volumes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Throughout results
- **Evidence pointer** Figures 4, 5, 6
- **Issue** The manuscript does not report statistical tests for most comparisons (e.g., C50 differences, dissociation rates, particle sizes). Error bars are shown in some figures but the number of replicates and the type of error (SD vs SEM) are not consistently stated.
- **Required correction** Add statistical analysis for key comparisons, state the number of replicates, and define error bars in all figure legends.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The authors propose that DNA bridging and condensation are related activities but do not discuss alternative models, such as the possibility that the observed condensation is driven by non-specific electrostatic interactions rather than specific protein-protein or protein-DNA contacts.
- **Required correction** Add a brief discussion of alternative interpretations and how the data distinguish between them.

## Risk / unsupported claims
- The claim that the RM-TMD domain "can generate force to condense DNA" is supported by the observation of DNA bundling against flow, but the magnitude of the force is not quantified. The claim is therefore qualitative.
- The statement that "AlphaFold2 predicts similar structural models for RM orthologs across diverse taxa" is not quantitatively supported (no RMSD or confidence metrics provided).
- The inference that the bright foci observed in single-molecule experiments are "pre-formed assemblies" is speculative; their composition and formation mechanism are not characterized.
- The claim that the DNA-binding surface is "variable" between species is based on sequence conservation analysis, but the functional consequences of this variability are not experimentally tested.
- The statement that "the minimal folded RM-TMD alone is sufficient to bind DNA" is supported, but the claim that it is "sufficient to form condensates" is based on experiments at relatively high protein concentrations (200 nM–2 μM) and may not reflect physiological conditions.