## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with stated evidence; no assessment of formatting or editorial style beyond readability
- **Shared manuscript claim summary** The authors propose an unsupervised learning method, slow feature analysis (SFA), trained on short unbiased molecular dynamics (MD) simulations seeded from AlphaFold-generated conformational ensembles, to extract slowly varying features used as collective variables (CVs) in metadynamics. They claim this approach accelerates sampling of cryptic pocket opening, protein-ligand binding, and allosteric transitions in two protein systems: plasmepsin-II and RIPK2.
- **Visible evidence base** Methods descriptions for AlphaFold ensemble generation, MD simulation protocols, SFA implementation, metadynamics parameters, funnel metadynamics setup, and MSM construction; Results sections describing observed transitions and comparisons; Figures referenced (Figures 3, 4, 5, 7, 8, 9; Supplementary Figures S1-S17) but not provided
- **Missing materials affecting confidence** All figures and supplementary information are referenced but not included in the provided text; no numerical data, error bars, convergence metrics, or quantitative comparisons are given; no code or parameter files are provided; no experimental validation data are referenced

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting integration of AlphaFold-generated ensembles, SFA, and metadynamics to address rare event sampling in proteins. The core idea is timely and potentially useful for the computational biophysics community. However, the current text lacks sufficient quantitative detail and direct evidence to fully substantiate the claims. The absence of figures and supplementary data prevents verification of key results, including convergence, reproducibility, and the claimed acceleration. The methodological novelty relative to existing approaches (e.g., tICA-based methods) is not clearly delineated. The manuscript reads as a preliminary report rather than a fully established study.
- **Who would be interested in the results, and why** Computational biophysicists and chemists working on enhanced sampling methods, rare event simulation, and cryptic pocket identification; structural biologists interested in allostery and protein dynamics; drug discovery researchers seeking methods to accelerate binding site identification and ligand binding simulations. The potential to bridge AlphaFold predictions with dynamical simulations is broadly appealing.
- **Major strengths** 1) The conceptual framework of using AlphaFold-generated ensembles as starting points for SFA training is innovative and practical. 2) The application to multiple biologically relevant systems (plasmepsin-II, RIPK2) demonstrates potential generality. 3) The use of SFA as CVs in metadynamics is a reasonable and potentially powerful approach. 4) The identification of allosteric hotspots in RIPK2 with potential therapeutic relevance is a valuable direction.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative evidence), R1-M2 (insufficient methodological detail for reproducibility), R1-M3 (unclear novelty relative to existing methods), R1-M4 (incomplete validation of allosteric claims)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The combination of AlphaFold ensembles with SFA is novel, but SFA itself is established and similar ideas exist (e.g., tICA-based CVs). The specific integration is a useful increment rather than a paradigm shift.
  - Scientific importance: Potentially high if the method is robust and broadly applicable, but the current evidence is insufficient to establish this.
  - Interdisciplinary readership: The topic bridges AI-based structure prediction, MD simulation, and drug discovery, which could attract a broad audience. However, the presentation is technical and may not be accessible to nonspecialists without clearer context.
  - Technical soundness: The methods are plausible but not fully verifiable from the provided text. Key details on SFA implementation, convergence, and error analysis are missing.
  - Readability for nonspecialists: The abstract and introduction are clear, but the methods and results sections assume significant expertise. Figures would likely help but are not available for assessment.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential but requires substantial additional data, methodological detail, and clearer validation before the claims can be supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that SFA-metadynamics "manage[s] to sample 'deep' cryptic pocket opening within a few hundreds of nanoseconds which was beyond the reach of microsecond long unbiased molecular dynamics simulations" and that SFA-augmented funnel metadynamics "accelerates ligand binding."
- **Evidence pointer** Results sections "SFA captures critical fluctuations necessary for cryptic pocket opening" and "SFA augmented funnel metadynamics accelerates ligand binding in plasmepsin II"; Figures 3, 4, 5; location not provided
- **Concern** The central quantitative claims are not supported by any numerical data in the text. No free energy differences, transition times, sampling statistics, or comparisons to unbiased MD are provided. The statement that SFA-metadynamics outperforms unbiased MD is qualitative and cannot be evaluated without convergence metrics or error bars. Similarly, the claim of accelerated ligand binding lacks quantitative measures such as binding/unbinding rates or mean first passage times.
- **Why it matters** Without quantitative evidence, the core value proposition of the method (acceleration and enhanced sampling) is unsubstantiated. The reader cannot assess whether the method is genuinely superior to existing approaches or merely anecdotal.
- **Resolution test** Provide quantitative comparisons: e.g., free energy profiles from SFA-metadynamics vs. unbiased MD or MSM, with error estimates; convergence tests (e.g., block averaging, multiple independent runs); and metrics for ligand binding acceleration (e.g., number of binding events per unit time, comparison to traditional funnel metadynamics).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The methods section describes SFA implementation and metadynamics parameters, but key details are missing.
- **Evidence pointer** Methods sections "Slow Feature Analysis (SFA)" and "Metadynamics"; location not provided
- **Concern** The description of SFA is incomplete. The text mentions "linear SFA" and references a "sklearn SFA package," but does not specify the featurization of input data (e.g., which coordinates, distances, or angles were used), the number of features extracted, the criteria for selecting the first two slow features, or the preprocessing steps (e.g., normalization, dimensionality reduction before SFA). For metadynamics, the Gaussian width selection is described as "approximately one-third of the standard deviation," but the exact calculation and the rationale for choosing the first two slow features as CVs are not detailed. The funnel metadynamics setup is also incomplete (e.g., funnel geometry, restraint parameters).
- **Why it matters** Reproducibility is a cornerstone of scientific validity. Without full methodological detail, other researchers cannot replicate the work or build upon it. This is particularly critical for a methods-focused manuscript.
- **Resolution test** Provide a complete description of the SFA pipeline, including input features, hyperparameters, and code availability. Detail the metadynamics parameters (e.g., deposition rate, bias factor, CV definitions) and funnel setup. Consider depositing the code and parameter files in a public repository.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and contextualization
- **Claim pointer** The authors state that SFA "bridges the gap between AlphaFold, molecular dynamics simulation and metadynamics" and imply novelty in this integration.
- **Evidence pointer** Discussion section; location not provided
- **Concern** The novelty of the approach is not clearly established relative to existing methods. SFA is conceptually similar to time-structure based independent component analysis (tICA), which the authors acknowledge, but they do not discuss how SFA differs in practice or why it is preferable. Moreover, the use of AlphaFold-generated ensembles as starting points for MD is not new (e.g., references 10-12). The specific contribution of this work, beyond combining existing tools, is unclear.
- **Why it matters** For a methods paper, the novelty must be explicit and justified. If the approach is largely a combination of existing techniques, the authors need to demonstrate a clear advantage or new insight that justifies publication.
- **Resolution test** Add a comparative discussion of SFA vs. tICA and other dimensionality reduction methods (e.g., autoencoders, principal component analysis) in the context of CV selection. Clearly state what is new about the AlphaFold-SFA-metadynamics pipeline and provide evidence of its superiority or unique capabilities.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Validation of biological claims
- **Claim pointer** The authors claim that SFA-metadynamics "captures allosteric hotspots in RIPK2" and that specific residues (e.g., Phe165, Trp170, Arg65) are involved in the active-to-inactive transition that regulates XIAP binding.
- **Evidence pointer** Results section "SFA captures allosteric hotspots in RIPK2"; Figures 7, 8, 9; location not provided
- **Concern** The biological interpretation of the allosteric hotspots is based on simulation data alone, with no experimental validation or comparison to known mutational or functional data beyond a brief mention of XIAP binding. The claim that the identified residues "govern" the transition is strong and requires more evidence, such as correlation with experimental mutagenesis studies or comparison with other computational methods.
- **Why it matters** Overinterpretation of simulation results can mislead the field. The authors should temper their claims or provide additional evidence (e.g., free energy calculations, perturbation analysis) to support the functional significance of the identified residues.
- **Resolution test** Include a discussion of experimental evidence for the role of these residues (e.g., from literature) or perform additional simulations (e.g., alchemical mutations, correlation analysis) to strengthen the claim. Alternatively, soften the language to indicate that these are predicted hotspots requiring experimental validation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction, first paragraph; location not provided
- **Issue** The abstract and introduction use terms like "deep" cryptic pocket and "landing pad" without clear definitions. The abstract also states "we proposed a novel unsupervised learning approach termed as slow feature analysis (SFA)" but SFA is not new; the novelty is in its application. This could mislead readers.
- **Required correction** Define "deep" cryptic pocket explicitly (e.g., fully open state with specific structural criteria). Rephrase the abstract to clarify that the novelty is in the integration of SFA with AlphaFold-generated ensembles and metadynamics, not in SFA itself.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, MD simulations
- **Evidence pointer** Methods section "Molecular Dynamics Simulations"; location not provided
- **Issue** The number of ions added (17 Na+) is stated, but the total system size, water model, and salt concentration are not specified. The equilibration and production run lengths are given, but the number of replicates for the production runs is only mentioned for RIPK2 (10 independent runs), not for plasmepsin-II.
- **Required correction** Specify the water model (e.g., TIP3P), total system size, and salt concentration. Clarify the number of replicates for plasmepsin-II production runs and whether the 40 ns runs are sufficient for convergence.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure referencing
- **Affected element** Results sections
- **Evidence pointer** Results sections; Figures 3, 4, 5, 7, 8, 9; location not provided
- **Issue** The text frequently references figures but does not describe what is shown in each figure. For example, "Figure 3" is mentioned as showing agreement between metadynamics and MSM, but the specific comparison (e.g., free energy profiles, populations) is not described.
- **Required correction** Add brief descriptions of each figure in the text, including the type of plot, the quantities compared, and the key observations. This will help readers understand the results without needing to access the figures separately.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Discussion
- **Evidence pointer** Discussion, final paragraph; location not provided
- **Issue** The statement "SFA emerges as an innovative technique that bridges the gap in the estimation of kinetics linked to rare events" is vague. The authors do not specify what "gap" is being filled or how SFA improves upon existing kinetic estimation methods.
- **Required correction** Clarify the specific limitation in current kinetic estimation approaches that SFA addresses, and provide a concrete example or comparison to support this claim.

## Risk / unsupported claims
- The claim that SFA-metadynamics samples "deep" cryptic pocket opening within a few hundred nanoseconds is unsupported by quantitative data in the text.
- The claim that SFA-augmented funnel metadynamics "accelerates ligand binding" is not backed by numerical comparisons to traditional funnel metadynamics.
- The identification of allosteric hotspots in RIPK2 is based solely on simulation and lacks experimental validation or comparison to known functional data.
- The statement that SFA "bridges the gap" between AlphaFold, MD, and metadynamics is not substantiated with a clear demonstration of novelty or advantage over existing methods.
- The convergence of metadynamics simulations is claimed but not demonstrated with error analysis or multiple independent runs (except for RIPK2, where 10 runs are mentioned but no convergence metrics are provided).