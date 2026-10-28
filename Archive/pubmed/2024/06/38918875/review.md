## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** The manuscript as provided, including all main text sections, tables, and figure legends. Supplementary material is referenced but was not available for review.
- **Shared manuscript claim summary** The authors use molecular modelling, docking, and molecular dynamics simulations to investigate how three HIV-1 subtype C-specific amino acid substitutions (C31S, R57S, Q63E) in the Tat protein affect binding to the TAR RNA element. They report that single substitutions reduce docking scores relative to subtype B Tat, with R57S showing the largest decrease, but that MMPBSA binding free energies from MD simulations indicate Q63E and R57S bind more strongly than wild-type. They conclude these positions are important for Tat-TAR interaction and may contribute to differential pathogenesis between subtypes.
- **Visible evidence base** Main text, Table 1, Table 2, Figures 1-8, Methods section
- **Missing materials affecting confidence** Supplementary Material 1 (referenced in Limitations, containing HADDOCK docking results) was not provided. Raw simulation trajectories, force field parameter files, and system preparation details are not available. No experimental validation data are included.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant question in HIV-1 biology, namely whether subtype C-specific Tat polymorphisms alter TAR binding. The computational workflow is reasonable in principle, and the authors are appropriately cautious in some interpretations. However, the study has substantial technical weaknesses that undermine confidence in the conclusions. The most serious issue is the direct contradiction between the docking results and the MMPBSA results, which the authors acknowledge but do not adequately resolve. The manuscript also lacks key methodological details, particularly regarding the MD simulation protocol, convergence assessment, and the treatment of the highly disordered Tat protein. The biological interpretation overreaches the computational evidence, and the clinical implications are speculative. The manuscript would benefit from a more rigorous analysis, clearer presentation of methods, and a more measured discussion of what in silico predictions can and cannot establish.
- **Who would be interested in the results, and why** Researchers studying HIV-1 Tat structure and function, particularly those interested in subtype-specific differences in viral pathogenesis and neurocognitive disorders. Computational biologists working on protein-RNA interactions may also find the methodological approach of interest. Clinicians or translational researchers focused on subtype-specific treatment strategies might have peripheral interest, though the direct clinical relevance is limited.
- **Major strengths** The study addresses a gap in the literature by examining specific subtype C polymorphisms rather than comparing whole subtypes. The use of full-length Tat is an improvement over earlier truncated constructs. The combination of docking, MD simulation, and MMPBSA analysis is a standard and appropriate computational pipeline for this type of question. The authors are transparent about the discrepancy between docking and MMPBSA results, which is commendable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (contradictory results), R1-M2 (missing MD methodological details), R1-M3 (disordered protein treatment), R1-M4 (overinterpretation of biological significance)
- **Assessment against Nature-style criteria** Originality: moderate. The specific question of individual subtype C variants has not been directly addressed computationally before, but the overall approach is not novel. Scientific importance: limited. The findings are preliminary and would need experimental validation to have significant impact. Interdisciplinary readership: narrow. The work is primarily of interest to HIV researchers and computational biologists. Technical soundness: inadequate in its current form due to the issues detailed below. Readability for nonspecialists: acceptable, though some sections are repetitive and the discussion could be more focused.
- **Recommendation posture** Not established from the provided evidence. The manuscript requires major revisions to address the technical concerns before the conclusions can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency of results
- **Claim pointer** The authors report that docking scores rank TatWt highest, but MMPBSA binding free energies rank TatQ63E and TatR57S higher than TatWt. Both are presented as measures of binding affinity, and the discrepancy is acknowledged but not resolved.
- **Evidence pointer** Table 1, Table 2, Results sections "Molecular docking: HDOCK" and "Molecular mechanics poisson-boltzmann surface area (MMPBSA) calculations", Discussion
- **Concern** The central results of the paper are internally contradictory. Docking scores indicate TatWt binds TAR most strongly, while MMPBSA free energies indicate Q63E and R57S bind more strongly. These are not minor quantitative differences but rank-order reversals that lead to opposite conclusions about which variants enhance or reduce binding. The authors state that "the binding free energies obtained from MD simulations are in contrast with the results of molecular docking" but do not provide a mechanistic explanation for this discrepancy. This is not merely a technical nuance; it fundamentally undermines the ability to draw any conclusion about the effect of these substitutions on Tat-TAR binding. The paper cannot support its conclusions while this contradiction remains unresolved.
- **Why it matters** The primary claim of the paper is that specific amino acid substitutions affect Tat-TAR binding. If two complementary computational methods give opposite answers, the reader cannot determine which, if either, is correct. The paper currently leaves this ambiguity unresolved, making the central conclusion unsubstantiated.
- **Resolution test** The authors must either (a) provide a rigorous explanation for the discrepancy, supported by additional analysis such as per-residue energy decomposition, trajectory analysis of key contacts, or free energy components that clarify which interactions dominate; (b) perform additional simulations with different starting conditions or force fields to test robustness; or (c) explicitly reframe the conclusions to acknowledge that the two methods give conflicting predictions and that no firm conclusion can be drawn without experimental validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The authors state that MD simulations were performed for 500 ns per system and analyzed using the AMIA pipeline, but provide insufficient detail on simulation setup, equilibration, and validation.
- **Evidence pointer** Methods section "Molecular dynamic (MD) simulation", Results section "MD simulation"
- **Concern** The MD simulation methodology is described at a level of detail that is insufficient for reproducibility. The authors do not specify the simulation temperature and pressure coupling details beyond the equilibration phase, the number of replicates, the criteria for determining equilibration, or how convergence was assessed. The choice of 500 ns for a disordered protein like Tat, which can sample many conformations on much longer timescales, requires justification. The authors also do not report error estimates for the MMPBSA calculations beyond standard deviations, and it is unclear how many frames were used and whether they were independent. The AMIA pipeline is referenced but not described in sufficient detail for the reader to understand what analyses were performed and how.
- **Why it matters** Without adequate methodological detail, the results cannot be reproduced or independently verified. This is a fundamental requirement for computational studies. The lack of convergence assessment is particularly concerning for a disordered protein where sampling artifacts could easily produce misleading results.
- **Resolution test** The authors must provide a complete description of the MD simulation protocol, including software versions, force field parameters, thermostat and barostat settings, simulation length and any replicate simulations, equilibration criteria, and convergence metrics. They should also report the number of frames used in MMPBSA calculations and provide error estimates that account for correlation between frames.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Treatment of intrinsically disordered protein
- **Claim pointer** The authors model Tat as a folded protein with a single stable structure, using homology modelling to generate a 3D structure and then performing docking and MD simulations on this structure.
- **Evidence pointer** Methods sections "Three-dimensional protein structure prediction using MODELLER v10.4" and "Molecular docking using HDOCK", Results section "3D Structure prediction and quality assessment"
- **Concern** HIV-1 Tat is an intrinsically disordered protein, particularly in its N-terminal and C-terminal regions. The authors do not address this fundamental property. They generate a single homology model and use it for docking and MD simulations, which implicitly assumes a single dominant folded conformation. This is likely to be a poor representation of the biologically relevant ensemble. The authors do not discuss how disorder might affect the interpretation of their results, nor do they attempt to sample multiple conformations or use ensemble-based approaches. The quality assessment they report (ERRAT, Verify3D, PROCHECK) evaluates the stereochemical quality of the model but does not address whether the model is representative of the conformational ensemble that Tat adopts in solution.
- **Why it matters** If Tat is disordered, the binding mechanism and affinity may be governed by conformational selection or induced fit, which cannot be captured by simulations starting from a single static structure. The conclusions about which residues are important for binding may be artifacts of the particular model chosen. This is a fundamental limitation that affects the validity of the entire computational pipeline.
- **Resolution test** The authors must either (a) justify their use of a single static structure despite the known disorder of Tat, with reference to experimental evidence that the relevant regions are structured under their conditions, or (b) use ensemble-based methods such as multiple starting structures, enhanced sampling, or coarse-grained models that account for disorder. At minimum, they should discuss how disorder might affect their conclusions and acknowledge this as a limitation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Overinterpretation of biological significance
- **Claim pointer** The authors conclude that the identified amino acid positions "likely contribute significantly to Tat-TAR interaction and the differential pathogenesis and neuropathogenesis observed between subtype B and subtype C" and suggest these could be therapeutic targets.
- **Evidence pointer** Conclusions, Discussion
- **Concern** The leap from computational predictions to biological and clinical significance is not supported by the data. The authors have not performed any functional assays, and the computational results are internally inconsistent as noted in R1-M1. Even if the computational results were consistent, in silico predictions of binding affinity changes do not directly translate to effects on viral transactivation, replication, or neuropathogenesis. The suggestion that these positions could be therapeutic targets is speculative and not grounded in any experimental evidence. The discussion of clinical implications, including the repeated emphasis on subtype-specific treatment strategies, is not justified by the scope of this study.
- **Why it matters** Overstating the implications of computational findings can mislead readers and potentially influence future research directions. The authors should present their results as preliminary computational predictions that require experimental validation, not as established biological findings.
- **Resolution test** The authors should temper their conclusions to match the evidence. They should explicitly state that these are computational predictions that require experimental validation, and remove or substantially soften claims about therapeutic targets and clinical implications.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Discussion section, final paragraph
- **Evidence pointer** Discussion, last paragraph
- **Issue** The final paragraph of the Discussion contains a sentence that appears to be incomplete or corrupted: "We therefore provide insight into By investigating the influence of subtype-specific sequence variations, we can gain deeper insights into the molecular mechanisms underlying the neurological effects of HIV-1 in PLWH." This reads as a drafting error.
- **Required correction** Rewrite this sentence to be grammatically correct and coherent.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Redundancy
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraphs 6 and 7
- **Issue** The Discussion contains two consecutive paragraphs that make nearly identical points about the need for subtype-specific treatment approaches and the importance of considering subtype variation in HIV-1 research. This appears to be unintentional duplication.
- **Required correction** Merge these paragraphs or remove the redundant one.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** Figure 1 is described as a "Clustering tree representing template structural similarity" but the figure itself is not shown in the manuscript text. The legend is minimal and does not explain what the clustering is based on or how to interpret it.
- **Required correction** Provide the figure and expand the legend to explain the clustering method and interpretation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Table 2
- **Evidence pointer** Table 2
- **Issue** The MMPBSA results are reported as mean ± standard deviation, but it is unclear how many independent samples or simulation frames these statistics are based on. Standard deviations for some values appear large relative to the means, and it is unclear whether these reflect genuine variability or insufficient sampling.
- **Required correction** Report the number of frames used, the block size for error estimation, and clarify whether the standard deviations represent frame-to-frame variability or block-averaged errors.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reference to supplementary material
- **Affected element** Limitations section
- **Evidence pointer** Limitations section
- **Issue** The authors state that HADDOCK docking gave different predicted binding scores and that this is shown in the Supplementary file. However, the supplementary material was not provided with the manuscript, so this comparison cannot be evaluated.
- **Required correction** Ensure the supplementary material is available to reviewers and readers, or summarize the HADDOCK results in the main text.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The authors use the term "binding affinity" to refer to docking scores, MMPBSA free energies, and interaction counts interchangeably. These are distinct quantities and should be clearly distinguished.
- **Required correction** Use precise terminology for each quantity, such as "docking score," "MMPBSA binding free energy," and "number of hydrogen bonds," rather than the generic "binding affinity."

## Risk / unsupported claims
- The claim that TatQ63E and TatR57S have higher binding affinity for TAR than TatWt is unsupported due to the direct contradiction with the docking results and the lack of experimental validation.
- The claim that the identified amino acid positions "likely contribute significantly" to differential pathogenesis and neuropathogenesis is unsupported, as no functional assays were performed.
- The suggestion that these positions could serve as therapeutic targets is speculative and unsupported.
- The claim that this is the first study to evaluate single amino acid changes from Tat subtype B to subtype C amino acids is not verifiable from the provided material and would require a more thorough literature search to substantiate.
- The statement that the results "offer insights into potential reasons for lower viral fitness when comparing different subtypes" is not supported by the data, as the study did not measure viral fitness.