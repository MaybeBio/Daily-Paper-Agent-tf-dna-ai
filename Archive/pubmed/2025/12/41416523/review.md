## Review setup
- **Input scope** Full manuscript text (abstract, materials and methods, results, discussion) without figures, tables, or supplementary data
- **Assessment boundary** Scientific claims, experimental design, methodological rigor, and internal consistency based solely on the provided text
- **Shared manuscript claim summary** The authors propose that MBD2 acts as a phase separation scaffold protein for pericentric heterochromatin, modulating compartmentalization and composition through liquid-liquid phase separation, with isoform-specific effects on histone acetylation and chromatin compaction
- **Visible evidence base** Text descriptions of proteomic analyses, in vitro phase separation assays, native mass spectrometry, cell-based imaging, and knockout experiments
- **Missing materials affecting confidence** All figures, tables, supplementary data, movies, and raw proteomic datasets referenced in the text but not provided

## Reviewer
- **Overall assessment** The manuscript presents a potentially interesting integrated approach to identify phase separation scaffolds in heterochromatin, with MBD2 as a central candidate. The combination of spatial proteomics, prediction tools, and in vitro reconstitution is conceptually appealing. However, the evidence as presented in the text alone is insufficient to fully establish the central claims. Key quantitative data, control experiments, and statistical analyses are referenced but not visible. The causal link between MBD2 phase separation and functional outcomes (histone acetylation, chromatin compaction) remains correlative rather than mechanistic. The manuscript would benefit from clearer presentation of the filtering pipeline and more direct evidence that phase separation, rather than other MBD2 functions, drives the observed phenotypes.
- **Who would be interested in the results, and why** Researchers studying heterochromatin organization, phase separation biology, epigenetic regulation, and chromatin architecture. The integrated proteomic-predictive approach may interest methodologists developing pipelines for identifying phase separation proteins. The MBD2 isoform-specific findings could interest those studying NuRD complex function and DNA methylation readers.
- **Major strengths** The integrated multi-approach strategy combining experimental and computational methods is commendable. The use of native mass spectrometry to detect oligomers adds biophysical rigor. The isoform-specific analysis (MBD2a/b vs MBD2c) provides functional granularity. The study addresses an important gap in understanding how heterochromatin compartments are organized.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** 
  - **Originality** Moderate to high. The integrated approach is novel, though individual components (proteomics, prediction tools, phase separation assays) are established. The MBD2-specific findings add new knowledge.
  - **Scientific importance** Moderate. Understanding heterochromatin compartmentalization is important, and identifying new phase separation scaffolds has broad implications. However, the significance relative to existing phase separation literature (HP1, MeCP2) needs clearer articulation.
  - **Interdisciplinary readership** Moderate. Will appeal to chromatin biologists, biophysicists studying phase separation, and computational biologists. The technical complexity may limit broader readership.
  - **Technical soundness** Cannot be fully assessed from text alone. The methods described are generally appropriate, but key validations and controls are not visible. The reliance on prediction tools without experimental validation for many candidates is a concern.
  - **Readability for nonspecialists** Adequate but dense. The manuscript assumes significant background knowledge in both phase separation and chromatin biology. Some sections (methods) are highly technical.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the approach is potentially powerful, but the current evidence as presented does not fully establish MBD2 as a phase separation scaffold with functional consequences. Major revisions with additional experimental evidence and clearer data presentation are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "MBD2 undergoes liquid-liquid phase separation via C-terminus-mediated homo-oligomerization, forming liquid-like condensates that regulate heterochromatin compartmentalization"
- **Evidence pointer** Results sections "MBD2 is a candidate scaffold for pericentric heterochromatin compartmentalization" and "MBD2 spherical condensate formation is driven by its C-terminus and modulated by the CC domain in an isoform dependent manner in vitro"; location not provided
- **Concern** The central claim that MBD2 phase separation regulates heterochromatin compartmentalization in vivo is not directly supported by the evidence described in the text. The in vitro experiments demonstrate phase separation capacity, and the cell-based experiments show correlations between MBD2 expression and heterochromatin phenotypes, but a direct mechanistic link is missing. The text does not describe experiments that manipulate MBD2 phase separation specifically (e.g., using phase separation-deficient mutants) and observe effects on heterochromatin organization.
- **Why it matters** Without direct evidence that phase separation per se (rather than other MBD2 functions such as DNA binding or protein-protein interactions) drives the observed effects on heterochromatin, the central claim remains correlative. This is critical for establishing MBD2 as a bona fide phase separation scaffold with functional relevance.
- **Resolution test** Provide experiments where MBD2 mutants that specifically disrupt phase separation (e.g., CC domain deletions or point mutations that abolish oligomerization without affecting DNA binding) are tested for their effects on heterochromatin compartmentalization, histone acetylation, and chromatin compaction in cells. Alternatively, rescue experiments in MBD2 KO cells with phase separation-deficient variants would strengthen the causal link.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative data availability
- **Claim pointer** "Mass spectrometric analysis yielded around 1000 proteins from which 250 were predicted to have scaffold phase separation properties using machine learning-based phase separation protein prediction tools. From these, 20 proteins, including methyl-CpG binding domain protein 2 (MBD2), were localized to pericentric heterochromatin compartments using gene ontology annotation analysis."
- **Evidence pointer** Results section "The heterochromatin fraction phase separates in vitro" and "Predicting phase separation scaffold proteins using multiple machine learning-based predictors"; location not provided
- **Concern** The filtering pipeline from approximately 1000 proteins to 20 candidates is described only qualitatively. No quantitative thresholds, statistical measures, or validation of the prediction tools' performance on this dataset are provided. The text does not describe how the three prediction tools were calibrated or whether their outputs were weighted or combined. The overlap between experimental proteomics and computational predictions is not quantified beyond the final count.
- **Why it matters** The identification of MBD2 as a candidate depends entirely on this filtering pipeline. Without transparent criteria and quantitative justification for each filtering step, the reader cannot assess the robustness of the candidate selection or the potential for false positives/negatives. This is particularly important given the known limitations of phase separation prediction tools.
- **Resolution test** Provide a detailed description of the filtering criteria at each step, including specific scores or thresholds used. Include a table or figure showing the number of proteins passing each filter and the overlap between prediction tools. Validate the prediction approach by showing that known phase separation proteins (e.g., HP1, MeCP2) are correctly identified in the pipeline.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** "MBD2a and MBD2b exclude histone acetyltransferases (e.g. Kat7) and recruit histone deacetylases (e.g. HDAC11, GATAD2b) at pericentric heterochromatin, resulting in subsequent deacetylation of histone H3 K27 and K9 within heterochromatin"
- **Evidence pointer** Results section "MBD2a/b modulates heterochromatin epigenetics via phase separation-driven molecular exclusion and inclusion"; location not provided
- **Concern** The text describes correlative observations (MBD2 overexpression leads to changes in localization of acetylation-related enzymes and histone acetylation levels) but does not establish causality. The claim that phase separation drives the exclusion/inclusion of specific proteins is inferred from colocalization and CoIP data, but alternative explanations (e.g., direct protein-protein interactions independent of phase separation, changes in chromatin accessibility affecting enzyme access) are not excluded. The text acknowledges this limitation for NuRD assembly but not for the broader claims about enzyme recruitment/exclusion.
- **Why it matters** The functional significance of MBD2 phase separation depends on demonstrating that the observed changes in heterochromatin composition and histone modifications are specifically due to phase separation-mediated mechanisms rather than other MBD2 activities. Without this distinction, the model proposed in the discussion remains speculative.
- **Resolution test** Use phase separation-deficient MBD2 mutants in the same experimental systems to show that the effects on enzyme localization and histone acetylation are dependent on phase separation capacity. Alternatively, use optogenetic or chemical dimerization tools to induce MBD2 phase separation independently of other functions and observe downstream effects.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative imaging data
- **Claim pointer** "MBD2a increased the fractions of highly compacted heterochromatin (classes 5-7) and concomitantly decreased the fractions of low chromatin compaction (classes 2-3). This effect was further enhanced by CC deletion"
- **Evidence pointer** Results section "MBD2 modulates pericentric heterochromatin dynamics in an isoform-dependent manner"; location not provided
- **Concern** The text describes quantitative image analysis of chromatin compaction classes but does not provide the actual data, statistical values, or effect sizes. The classification into seven compaction classes is mentioned but the criteria for this classification are not described. The number of cells analyzed, biological replicates, and statistical tests are not stated in the text.
- **Why it matters** The claim that MBD2 isoforms differentially affect chromatin compaction is a key functional outcome. Without quantitative data and statistical support, the reader cannot evaluate the robustness or magnitude of the observed effects. This is particularly important given the subtle differences described between isoforms.
- **Resolution test** Provide the quantitative data as figures or tables with clear statistical analysis. Describe the criteria for compaction class assignment and include information on sample sizes, replicates, and statistical tests used.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Physiological relevance
- **Claim pointer** "MBD2 modulates pericentric heterochromatin compartmentalization and composition" and "MBD2 phase separation increases the compaction of heterochromatin, reduces the accessibility of various active molecular machineries"
- **Evidence pointer** Results sections "MBD2 modulates pericentric heterochromatin dynamics in an isoform-dependent manner" and "MBD2a/b modulates heterochromatin epigenetics via phase separation-driven molecular exclusion and inclusion"; location not provided
- **Concern** The physiological relevance of the findings is not established. The text describes experiments with ectopic overexpression of MBD2 constructs at concentrations of 15-35 µM, which are described as "levels found in tissues" but the endogenous MBD2 concentration in the relevant cell types is not directly measured. The MBD2 KO experiments show effects on heterochromatin size, but the text does not describe whether these effects are rescued by re-expression of wild-type MBD2 or whether they correlate with changes in gene expression or other functional outcomes.
- **Why it matters** Overexpression experiments can produce artifacts, and the physiological relevance of phase separation at endogenous protein levels is a major question in the field. Without evidence that endogenous MBD2 phase separation occurs and is functionally important, the significance of the findings for normal heterochromatin biology remains unclear.
- **Resolution test** Measure endogenous MBD2 concentration in the cell types used and compare to the concentrations used in overexpression experiments. Perform rescue experiments in MBD2 KO cells with wild-type and phase separation-deficient MBD2 to establish physiological relevance. If possible, use knock-in approaches or endogenous tagging to study MBD2 behavior at native expression levels.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Protein purification and phase separation assay conditions
- **Evidence pointer** Materials and methods section "Protein purification, labelling and analysis" and "In vitro phase separation and detection"; location not provided
- **Issue** The text describes phase separation assays but does not specify the buffer conditions, protein concentrations tested, or the range of conditions explored. The statement "various concentrations of salt, protein, crowding agents, and DNA" is vague.
- **Required correction** Provide a detailed description of the phase separation assay conditions, including the range of protein concentrations, salt concentrations, and crowding agent concentrations tested. Specify how phase separation was quantified (e.g., turbidity threshold, droplet size distribution).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Native mass spectrometry oligomer detection
- **Evidence pointer** Results section "MBD2 spherical condensate formation is driven by its C-terminus and modulated by the CC domain in an isoform dependent manner in vitro"; location not provided
- **Issue** The text states that native mass spectrometry detected oligomers from pentamers to 26mers in MBD2∆N condensate fractions, and that this was "largely abolished" by CC depletion. However, the functional significance of these specific oligomeric states is not discussed.
- **Required correction** Clarify whether the detected oligomers represent the building blocks of the condensates or are merely present in the condensate fraction. Discuss whether the specific oligomer sizes have functional implications.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** MBD2 isoform nomenclature
- **Evidence pointer** Results section "MBD2 spherical condensate formation is driven by its C-terminus and modulated by the CC domain in an isoform dependent manner in vitro"; location not provided
- **Issue** The text uses MBD2, MBD2a, MBD2b, and MBD2c interchangeably in different sections. The relationship between the constructs used in vitro (MBD2, MBD2∆N, MBD2∆C) and the endogenous isoforms (MBD2a, MBD2b, MBD2c) is stated but could be clearer.
- **Required correction** Use consistent nomenclature throughout, or provide a clear table mapping the constructs to the isoforms they represent.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of phase separation mechanisms
- **Evidence pointer** Discussion section; location not provided
- **Issue** The discussion of phase separation mechanisms and the distinction between LLPS and PPPS is brief and does not fully engage with the recent literature on the role of DNA and chromatin in phase separation.
- **Required correction** Expand the discussion to place the findings in the context of recent work on chromatin phase separation, including the role of nucleic acids and the relationship between phase separation and chromatin state.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Quantitative image analysis
- **Evidence pointer** Materials and methods section "Quantitative image analysis"; location not provided
- **Issue** The text states that "Significances were calculated by unpaired t-test" but does not describe how multiple comparisons were handled when comparing multiple constructs or concentration groups.
- **Required correction** Describe the statistical approach for multiple comparisons, or state that no correction was applied and justify this choice.

## Risk / unsupported claims
- The claim that MBD2 phase separation "regulates heterochromatin compartmentalization" is not directly supported by the evidence described; the text shows correlation but not causation.
- The claim that MBD2 phase separation "modulates the composition" of heterochromatin through exclusion/inclusion mechanisms is inferred from colocalization and CoIP data but not directly demonstrated.
- The statement that MBD2 phase separation "promotes overall low acetylation levels" at pericentric heterochromatin is based on correlative overexpression data and does not establish a mechanistic link.
- The physiological relevance of the findings at endogenous MBD2 levels is not established; all functional experiments appear to use overexpression.
- The filtering pipeline from approximately 1000 proteins to 20 candidates lacks quantitative transparency and validation.
- The claim that MBD2a∆CC shows stronger phase separation while MBD2b∆CC shows weaker phase separation is described but the mechanistic basis for this isoform-specific difference is not explained.
- The text mentions "reduced chromatin accessibility and diminished transcriptional activity" as consequences of MBD2 phase separation, but no direct measurements of chromatin accessibility or transcriptional activity are described in the provided text.