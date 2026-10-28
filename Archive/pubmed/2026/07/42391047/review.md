## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, and supplementary figure/table references
- **Assessment boundary** Scientific content, experimental design, data interpretation, structural biology claims, genetic evidence, and overall coherence of the proposed model
- **Shared manuscript claim summary** The authors identify critical residues in Bacillus subtilis DnaB required for DNA replication initiation, determine a cryo-EM structure of the DnaB tetramer, and use AlphaFold3 predictions plus bacterial two-hybrid assays to propose that DnaB acts as a protein-protein interaction hub coordinating DnaA, DnaD, and DnaI during helicase loading at oriC
- **Visible evidence base** Genetic alanine scanning (447 mutants), growth assays, marker frequency analysis, fluorescence microscopy, bacterial two-hybrid assays, single-particle cryo-EM at 3.1 Å, AlphaFold3 structural predictions, sequence conservation analysis across Firmicutes pathogens
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (S1-S18) are not provided; cryo-EM map and model validation metrics (FSC curves, local resolution, model-to-map fit statistics) are only summarized in Supplementary Table S10; raw growth curves and statistical details for all spot assays are not fully visible; the specific alanine substitution list and all 447 mutant phenotypes are not fully enumerated in the main text

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive genetic and structural analysis of the essential helicase loader DnaB in Bacillus subtilis. The work identifies 13 critical residues, provides a new cryo-EM structure revealing an unexpected asymmetric tetramer, and integrates AlphaFold3 predictions with two-hybrid data to propose a mechanistic model for helicase loading. The genetic screening approach is thorough, and the combination of structural and interaction data is compelling. However, several concerns regarding the directness of evidence linking specific residues to specific protein-protein interactions, the functional validation of the proposed model, and the interpretation of the asymmetric tetramer require clarification before the central claims can be fully accepted.
- **Who would be interested in the results, and why** Researchers studying bacterial DNA replication initiation, particularly those focused on Firmicutes biology and the mechanisms of helicase loading. The work also has relevance for understanding how protein-protein interaction hubs coordinate multi-step assembly processes at origins of replication. Given the conservation of DnaB in clinically important pathogens such as Staphylococcus aureus, Listeria monocytogenes, and Streptococcus pneumoniae, the findings may inform future antimicrobial development targeting replication initiation.
- **Major strengths** 1) The genetic screen is systematic and identifies a manageable number of critical residues, providing a clear foundation for mechanistic dissection. 2) The cryo-EM structure reveals a novel asymmetric tetrameric architecture that challenges previous assumptions based on the Geobacillus stearothermophilus structure. 3) The integration of multiple approaches (genetics, structure, prediction, interaction assays) strengthens the overall argument. 4) The proposed model for sequential helicase loading is mechanistically thoughtful and testable. 5) The conservation analysis extends the relevance beyond B. subtilis to pathogenic Firmicutes.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - **Originality** The work is original in its identification of specific DnaB residues and the asymmetric tetramer structure. The concept of DnaB as an interaction hub is not entirely new, but the molecular detail provided here represents a significant advance.
  - **Scientific importance** The study addresses a fundamental gap in understanding bacterial replication initiation, specifically the molecular choreography of helicase loading. The findings have implications for a broad range of Firmicutes species.
  - **Interdisciplinary readership** The work will primarily appeal to molecular microbiologists, structural biologists, and biochemists. The broader cell biology community may find the interaction hub concept interesting, but the specialized nature of the system limits cross-disciplinary reach.
  - **Technical soundness** The genetic and structural approaches are generally sound, but several concerns (detailed below) regarding the directness of evidence and validation of the model need to be addressed.
  - **Readability for nonspecialists** The manuscript is clearly written and the figures are well-referenced, but the density of structural and genetic detail will challenge nonspecialists. The model figure (Fig. 8) helps convey the key concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core genetic and structural data are valuable, but the manuscript currently overreaches in some interpretations and under-delivers in direct functional validation of the proposed interaction interfaces.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for interaction mapping
- **Claim pointer** The manuscript claims that specific DnaB residues mediate interactions with DnaA, DnaD, and DnaI based primarily on bacterial two-hybrid assays and AlphaFold3 predictions
- **Evidence pointer** Results sections "DnaBNTD residues mediate interaction with DnaA domain I", "DnaBCTD residues mediate interaction with the DnaD C-terminal tail", "DnaBCTT residues mediate interaction with the DnaI CTD"; Figures 5-7
- **Concern** The bacterial two-hybrid assay is used as the primary evidence for mapping specific interaction interfaces, but the assay only reports binary interaction presence or absence. The manuscript does not provide quantitative binding data (e.g., affinity measurements, competition assays) to support the claim that the identified residues are the primary determinants of these interactions. Furthermore, the AlphaFold3 predictions are used to support the interaction interfaces, but these predictions are not experimentally validated with techniques such as cross-linking mass spectrometry, mutagenesis of the predicted partner interface, or in vitro binding assays with purified proteins.
- **Why it matters** The central claim of the manuscript is that DnaB acts as an interaction hub through specific interfaces. Without direct biochemical validation that the identified residues are bona fide interaction hotspots, the model remains speculative. The genetic data show these residues are important for function, but the link to specific protein-protein interactions is inferred rather than demonstrated.
- **Resolution test** Provide in vitro binding assays (e.g., pull-downs, surface plasmon resonance, or isothermal titration calorimetry) with purified wild-type and mutant DnaB variants against DnaA, DnaD, and DnaI. Alternatively, perform cross-linking mass spectrometry to validate the predicted interfaces. At minimum, demonstrate that the interaction-defective mutants in the two-hybrid assay also show reduced binding in an orthogonal biochemical assay.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation of the asymmetric tetramer
- **Claim pointer** The cryo-EM structure reveals an asymmetric tetramer with two compact and two extended chains, and the manuscript proposes that this asymmetry is functionally relevant for sequential helicase loading
- **Evidence pointer** Results section "A new domain architecture for B. subtilis DnaB reveals critical residue clusters"; Figure 4; Supplementary Figures S5-S7
- **Concern** The manuscript does not provide functional evidence that the observed asymmetry is biologically meaningful. The cryo-EM structure may represent a snapshot of a dynamic equilibrium, and the asymmetric conformation could be an artifact of the grid preparation or a minor population. The authors do not test whether mutations that stabilize or destabilize the asymmetric conformation affect helicase loading or replication initiation. Additionally, the resolution of the cryo-EM map (3.1 Å) may not be sufficient to unambiguously assign the conformational differences between chains, particularly in flexible regions.
- **Why it matters** The proposed model for sequential helicase loading depends critically on the asymmetric arrangement of the DnaB tetramer. If the asymmetry is not functionally relevant, the model loses its mechanistic foundation. The field needs to know whether the observed conformation is a stable, functionally important state or a transient, possibly non-physiological state.
- **Resolution test** Perform mutagenesis to lock the tetramer in either the symmetric or asymmetric conformation and test the effects on replication initiation in vivo and helicase loading in vitro. Alternatively, use hydrogen-deuterium exchange mass spectrometry or cross-linking to probe conformational dynamics in solution. Provide local resolution estimates and validate the conformational differences between chains with focused classification or 3D variability analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness of genetic evidence
- **Claim pointer** The alanine screen identified 13 critical residues, and the manuscript claims these are required for DNA replication initiation
- **Evidence pointer** Results section "Identification of critical residues in DnaB required for DNA replication initiation"; Figures 2-3; Supplementary Figures S2-S3
- **Concern** The manuscript reports that 13 residues were identified as critical, but the full results of the alanine screen are not presented. It is unclear how many of the 447 mutants showed intermediate phenotypes, whether the screen was saturating, and whether any residues outside the three identified clusters also showed partial defects. The marker frequency analysis and fluorescence microscopy data are presented for the critical mutants, but the quantitative data (e.g., ori:ter ratios, statistical comparisons) are only in Supplementary Table S8, which is not provided. Without the complete screen results, it is difficult to assess whether the identified residues represent the complete functional surface of DnaB.
- **Why it matters** The genetic screen is the foundation of the manuscript. If the screen was not saturating or if the phenotypic thresholds were arbitrary, the list of critical residues may be incomplete, and the proposed interaction map may miss important functional surfaces. The field needs confidence that the identified residues are the key determinants of DnaB function.
- **Resolution test** Provide the complete results of the alanine screen, including all 447 mutants and their phenotypes. Include a clear description of the phenotypic thresholds used to define "critical" residues. Present the quantitative ori:ter ratios and statistical analyses for all critical mutants in the main text or a fully accessible supplementary table.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation and alternative interpretations
- **Claim pointer** The manuscript proposes a specific model for sequential helicase loading where DnaB orchestrates the loading of two helicases on opposite DNA strands
- **Evidence pointer** Discussion section "Model of DnaB interacting with DnaA, DnaD, and DnaI"; Figure 8
- **Concern** The proposed model is largely speculative and goes beyond the direct experimental evidence. The manuscript does not test the model with experiments designed to distinguish between sequential and simultaneous helicase loading, nor does it address alternative models such as DnaB functioning as a scaffold that pre-assembles the loading machinery before DNA binding. The stoichiometry of the DnaB complex with DnaA, DnaD, and DnaI is not experimentally determined. The model also assumes that the observed interactions occur simultaneously, but the two-hybrid data only show pairwise interactions.
- **Why it matters** The model is presented as a major conclusion of the manuscript, but it is not directly tested. If the model is incorrect, the interpretation of the data could be misleading. The field needs experimentally testable predictions and validation of the proposed mechanism before accepting it as the definitive model for helicase loading in B. subtilis.
- **Resolution test** Design experiments to test the sequential loading model, such as single-molecule assays to visualize helicase loading in real time, or biochemical assays with defined reaction intermediates. Determine the stoichiometry of the DnaB complex with its interaction partners using analytical ultracentrifugation or mass photometry. Test whether mutations that disrupt specific interactions affect the order of assembly at oriC.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 1
- **Evidence pointer** Results section "DnaB is an interaction hub for DNA replication initiation proteins"; Figure 1
- **Issue** The two-hybrid assay results in Figure 1B are presented as a qualitative readout (blue vs. white colonies), but the figure legend does not specify the quantitative threshold for a positive interaction. It is also unclear whether the assay was performed with all pairwise combinations or only against DnaB.
- **Required correction** Clarify the scoring criteria for positive interactions in the figure legend. State explicitly which pairwise combinations were tested and include a positive and negative control description.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Marker frequency analysis and fluorescence microscopy data
- **Evidence pointer** Results section "Identification of critical residues in DnaB required for DNA replication initiation"; Figure 3
- **Issue** The manuscript states that all DnaB variants displayed lower ori:ter ratios compared to wild-type, but the statistical significance of these differences is not reported in the main text. The number of biological replicates is mentioned in the methods, but the specific p-values are only in Supplementary Table S8.
- **Required correction** Include the statistical significance values (p-values or confidence intervals) for the ori:ter ratio comparisons in the main text or figure legends. State the number of biological replicates for each experiment in the figure legend.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Structural model completeness
- **Affected element** Hybrid DnaB model
- **Evidence pointer** Results section "A new domain architecture for B. subtilis DnaB reveals critical residue clusters"; Figure 4C-E
- **Issue** The hybrid model combines cryo-EM density with AlphaFold3 predictions, but the manuscript does not clearly describe how the AF3-predicted regions were validated or whether they were refined against the experimental density. The quality of the fit for the modeled regions is not quantified.
- **Required correction** Provide a description of how the AF3-predicted regions were fitted and validated. Include a measure of model-to-map fit for the complete hybrid model, such as correlation coefficients or Q-scores for the added regions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Conservation analysis depth
- **Affected element** Sequence conservation analysis
- **Evidence pointer** Results section "Critical DnaB PPIs are predicted to be conserved in human pathogens"; Supplementary Figure S17
- **Issue** The conservation analysis is presented as sequence alignments, but the manuscript does not provide a quantitative measure of conservation (e.g., conservation scores, percent identity) for the identified interaction residues. The statement that interactions are "highly conserved" is not supported by statistical analysis.
- **Required correction** Provide quantitative conservation scores for the critical residues across the analyzed species. Consider using a tool like ConSurf or calculating percent identity for the interaction interfaces.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The manuscript does not explicitly discuss the limitations of the two-hybrid assay for mapping interaction interfaces, particularly the possibility of false positives or negatives due to overexpression and the heterologous E. coli host.
- **Required correction** Add a paragraph in the Discussion acknowledging the limitations of the two-hybrid approach and describing how the conclusions might be affected by these limitations.

## Risk / unsupported claims
- The claim that DnaB acts as an interaction hub orchestrating dual helicase loading is a reasonable hypothesis but is not directly supported by functional experiments testing the proposed mechanism
- The specific interaction interfaces proposed for DnaB with DnaA, DnaD, and DnaI are supported by two-hybrid data and AF3 predictions but lack orthogonal biochemical validation
- The functional relevance of the asymmetric tetramer observed in cryo-EM is not experimentally tested
- The conservation of the identified interaction interfaces across Firmicutes pathogens is based on sequence alignments but lacks quantitative conservation scoring
- The claim that the 13 identified residues represent the complete set of critical functional residues in DnaB is not fully supported, as the complete alanine screen results are not presented
- The proposed sequential helicase loading model is speculative and not directly tested with experiments designed to distinguish between alternative mechanisms