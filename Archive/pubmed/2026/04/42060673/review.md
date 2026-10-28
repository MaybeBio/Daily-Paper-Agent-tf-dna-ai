## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) and metadata
- **Assessment boundary** Scientific content, experimental logic, evidence quality, and internal consistency of the claims as presented; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The authors propose that in vivo replication of potato spindle tuber viroid (PSTVd) in Nicotiana benthamiana is catalyzed by a remodeled, 7-subunit RNA polymerase II complex lacking Rpb4/5/6/7/9, that the host transcription factor TFIIIA-7ZF bridges this remodeled Pol II to the PSTVd RNA template, and that structural predictions from AlphaFold3 combined with experimental validation support a model in which TFIIIA-7ZF binds the left terminal domain of PSTVd RNA, induces bending at loop 8, and recruits Pol II via its C-terminus interacting with Rpb2.
- **Visible evidence base** Results sections describing RIP, coIP, BiFC, EMSA, and AlphaFold3 predictions; figures referenced as Fig 1A–D, Fig 2A–D, Fig 3A–D, Fig 4, S1–S4 Figs, S1 Video, S1 Table; methods for plant growth, cloning, RIP/coIP, BiFC, and EMSA
- **Missing materials affecting confidence** Figures and supplementary materials not provided; raw data, statistical details, and replicate information not available; AlphaFold3 prediction confidence metrics not shown; primer sequences and construct details not accessible

## Reviewer
- **Overall assessment** The manuscript addresses a significant and underexplored question in viroid biology: the molecular organization of the Pol II complex when transcribing RNA templates in vivo. The central claim that a remodeled Pol II lacking Rpb4/5/6/7/9 operates on PSTVd RNA in planta is potentially important and builds logically on prior in vitro work. However, the evidence presented in the text is insufficient to fully establish this claim. Key experimental details, quantitative data, and figure content are not available for verification. The AlphaFold3 predictions are used as a central structural framework, but the limitations of such predictions for RNA-protein complexes are not adequately addressed. The discrepancy between RIP and EMSA results for the ZF2 mutant is acknowledged but not resolved. Overall, the study is conceptually interesting and likely of interest to the viroid and RNA polymerase communities, but the current evidence base does not fully support the strength of the conclusions drawn.

- **Who would be interested in the results, and why** Researchers studying viroid replication and host interactions, RNA polymerase biology, and the broader question of RNA-templated transcription by DNA-dependent RNA polymerases. The proposed remodeled Pol II organization and the role of TFIIIA-7ZF as a bridging factor would also interest those working on transcription factor plasticity and noncoding RNA biology.

- **Major strengths** The study tackles a fundamental and poorly understood mechanism. The combination of in vivo RIP/coIP with structural prediction and functional assays is a reasonable multi-pronged approach. The use of a splicing variant of TFIIIA with seven zinc fingers as a specific host factor for viroid transcription is a novel angle. The authors also connect their findings to broader observations of Pol II subunit heterogeneity in other systems.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that Rpb4/5/6/7/9 are not involved in PSTVd transcription in planta and that the remodeled Pol II consists of Rpb1/2/3/8/10/11/12.
- **Evidence pointer** Results section "The composition of in vivo Pol II complex on RNA templates"; Fig 1A
- **Concern** The conclusion that Rpb4/5/6/7/9 are absent from the active Pol II complex on PSTVd RNA rests on RIP experiments showing no significant enrichment of these subunits with PSTVd RNA. However, the text does not provide quantitative data, statistical values, or the full set of controls. Negative RIP results are inherently difficult to interpret, as lack of enrichment could reflect technical limitations, epitope accessibility, or suboptimal antibody/GFP-trap efficiency rather than true absence from the complex. The authors also do not address whether these subunits might be present at lower stoichiometry or transiently associated.
- **Why it matters** The central claim of the paper is the existence of a remodeled 7-subunit Pol II in vivo. If the negative RIP results are not robustly quantified and controlled, the claim is not established. This is the foundation on which the rest of the manuscript rests.
- **Resolution test** Provide quantitative RIP data with appropriate positive and negative controls, including a known Pol II-interacting RNA or DNA target, and demonstrate that the absence of enrichment for Rpb4/5/6/7/9 is not due to poor expression or capture of these subunits. Ideally, include an independent method such as reciprocal RIP or a different crosslinking approach.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural evidence
- **Claim pointer** The authors state that AlphaFold3 predicted the structure of the remodeled Pol II with PSTVd RNA and TFIIIA-7ZF, and that the predicted structure is supported by experimental data.
- **Evidence pointer** Results sections "Structure overview of the TFIIIA-7ZF/Pol II complex on the (+) PSTVd RNA templates" and "Testing the geometry of TFIIIA-7ZF in the Pol II/TFIIIA-7ZF/PSTVd complex"; Fig 1C, Fig 2A–B
- **Concern** AlphaFold3 predictions for RNA-protein complexes are not experimentally validated structures. The authors acknowledge low confidence in nucleic acid portions but do not provide the confidence metrics or discuss the implications of this limitation for their specific claims about RNA bending and TFIIIA-7ZF positioning. The predicted interactions between TFIIIA-7ZF residues and Rpb2 are presented with specific residue numbers, but no experimental validation of these specific contacts is provided. The BiFC data only report proximity, not direct interaction interfaces.
- **Why it matters** The structural model is used to explain functional data and to propose a mechanism. If the prediction is not reliable, the mechanistic conclusions are speculative. The specific claim that the C-terminus of TFIIIA-7ZF moves from RNA binding to Rpb2 binding upon Pol II recruitment is entirely based on the predicted model and is not tested experimentally.
- **Resolution test** Provide AlphaFold3 confidence scores (e.g., pLDDT, PAE) for the relevant interfaces. Include experimental validation of the TFIIIA-7ZF C-terminus-Rpb2 interaction, such as mutagenesis of the predicted interface residues followed by coIP or pull-down assays. Address the conformational change claim with a direct experimental test, such as crosslinking or hydrogen-deuterium exchange.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance
- **Claim pointer** The authors claim that the loop 8 region of PSTVd RNA is important for TFIIIA-7ZF binding and that bending at this site is functionally relevant for replication.
- **Evidence pointer** Results section "Structure of TFIIIA-7ZF/viroid complex"; Fig 3A–C
- **Concern** The loop 8 mutant was previously reported to have reduced replication efficiency, and the current study shows it impairs TFIIIA-7ZF binding. However, the text does not clarify whether the reduced replication is directly due to impaired TFIIIA-7ZF binding or to other structural changes in the RNA. The mutant changes the loop to a rigid double-stranded conformation, which could affect other RNA-RNA interactions or RNA structure beyond TFIIIA-7ZF binding.
- **Why it matters** The claim that RNA bending at loop 8 is functionally important for TFIIIA-7ZF interaction and replication requires a more direct causal link. Without ruling out alternative explanations, the conclusion is not fully supported.
- **Resolution test** Test additional loop 8 mutants that preserve the loop structure but alter sequence, or mutants that restore bending in a different position. Show that the replication defect correlates specifically with TFIIIA-7ZF binding affinity across a panel of mutants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data availability
- **Claim pointer** The manuscript references multiple figures and supplementary materials that are not provided in the submitted text.
- **Evidence pointer** Fig 1A–D, Fig 2A–D, Fig 3A–D, Fig 4, S1–S4 Figs, S1 Video, S1 Table
- **Concern** The review is based on text only. Key data such as the RIP blots, coIP results, BiFC images, EMSA gels, and AlphaFold3 structural figures are not available. This prevents verification of the claims and assessment of data quality.
- **Why it matters** The conclusions depend heavily on these figures. Without them, the evidence base is incomplete and the claims cannot be properly evaluated.
- **Resolution test** Provide all figures and supplementary materials for full review.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "Reorganizing the RNA polymerase II complex" in the title and abstract implies a dynamic process, but the data presented are largely static interaction and structural prediction data. The dynamic aspect is not directly demonstrated.
- **Required correction** Consider rephrasing to reflect that the study characterizes a distinct Pol II composition on RNA templates, rather than a reorganization event.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "Testing the geometry of TFIIIA-7ZF in the Pol II/TFIIIA-7ZF/PSTVd complex"
- **Evidence pointer** Fig 2C
- **Issue** The BiFC assay shows complementation between TFIIIA-7ZF and Rpb12 but not Rpb3. The authors interpret this as supporting the predicted geometry, but the absence of signal for Rpb3 could also be due to the fusion orientation or steric hindrance of the YFP fragments.
- **Required correction** Acknowledge this alternative explanation and, if possible, include a positive control for the Rpb3 fusion construct.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Materials and methods, EMSA
- **Evidence pointer** EMSA section
- **Issue** The EMSA binding curves are described but the calculation of the fraction of RNA bound and the determination of the half-saturation concentration (K) are not detailed. The number of replicates and error analysis are not stated.
- **Required correction** Provide details on curve fitting, replicates, and statistical analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The discussion mentions that the remodeled Pol II contains the intact Rpb3 subassembly, but the RIP data show that Rpb3 interacts with PSTVd RNA. However, the coIP data show that TFIIIA-7ZF interacts with Rpb3 only in infected samples. The relationship between these two observations and the order of assembly is not clearly explained.
- **Required correction** Clarify the proposed sequence of events: whether TFIIIA-7ZF binds RNA first and then recruits Pol II, or whether Pol II and TFIIIA-7ZF pre-assemble before RNA binding.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 2
- **Issue** The introduction cites prior work on the in vitro remodeled Pol II but does not discuss any alternative models or competing hypotheses for viroid replication.
- **Required correction** Briefly mention alternative models, if any exist, to position the current work within the broader field.

## Risk / unsupported claims
- The claim that Rpb4/5/6/7/9 are not involved in PSTVd transcription in vivo is not fully supported without quantitative RIP data and appropriate controls.
- The claim that the AlphaFold3-predicted structure reflects the actual in vivo complex is not established, given the acknowledged low confidence in nucleic acid predictions and the lack of experimental validation of specific interfaces.
- The claim that TFIIIA-7ZF undergoes a conformational change from RNA binding to Rpb2 binding is speculative and not directly tested.
- The functional relevance of loop 8 bending for replication is not causally established, as alternative explanations for the mutant phenotype are not excluded.
- The in vivo existence of a stable 7-subunit Pol II complex is inferred from interaction data but not directly demonstrated by, for example, size exclusion chromatography or native mass spectrometry of the endogenous complex.