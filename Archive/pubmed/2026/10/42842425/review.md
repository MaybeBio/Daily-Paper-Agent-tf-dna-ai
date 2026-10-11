## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full-text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present VAEBAC, a representation-learning framework for proteome-scale prediction of amyloidogenic proteins, and apply it to nucleic-acid-binding proteins (NABPs) from four organisms. They report consistent enrichment of predicted amyloidogenic NABPs in Gene Ontology categories related to transcriptional regulation, spatial separation between aggregation-prone regions and DNA-binding interfaces, and experimental validation of fibrillar assembly for selected proteins. They propose a conserved model of functional stratification of aggregation susceptibility across transcriptional regulatory tiers.
- **Visible evidence base** Abstract text only; no methodological details, quantitative results, figures, tables, or supplementary data were accessible
- **Missing materials affecting confidence** Full manuscript, all figures and tables, supplementary data, methodological descriptions, statistical outputs, experimental validation details, and the VAEBAC web resource were not available for assessment

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially interesting claim regarding the functional stratification of amyloidogenic potential within nucleic-acid-binding proteomes. However, the evidence base available for review is limited to the abstract, which precludes verification of the core methodological claims, statistical analyses, and experimental validations. The central conclusion, that aggregation susceptibility is selectively retained and functionally stratified in transcriptional regulators across 3.5 billion years of evolution, is a strong claim that requires substantially more evidence than the abstract can provide. The work may be of interest to the protein aggregation and bioinformatics communities, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in protein aggregation and amyloid biology, computational biology and machine learning applied to proteome-scale prediction, and those studying nucleic-acid-binding proteins and transcriptional regulation. The proposed framework could be of interest to developers of representation-learning tools for protein function prediction. The evolutionary claim may attract interest from comparative genomics and evolutionary biology communities.
- **Major strengths** The abstract addresses a potentially underexplored question regarding the distribution of aggregation susceptibility within regulatory proteomes. The use of four phylogenetically diverse organisms spanning prokaryotes and eukaryotes is a reasonable design choice for testing evolutionary conservation. The inclusion of experimental validation, though not detailed in the abstract, is a positive indicator. The proposed framework is made freely available, which supports reproducibility and community use.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The claim that VAEBAC performs "proteome-scale prediction of amyloidogenicity" with high reliability  
  - **Evidence pointer** Abstract, Results section; location not provided  
  - **Concern** The abstract provides no information on the architecture, training data, validation strategy, or performance metrics of the VAEBAC framework. Without details on how the model was trained, benchmarked, and compared against existing amyloidogenicity predictors, the reliability of the predictions cannot be assessed.  
  - **Why it matters** The entire study rests on the accuracy of the prediction framework. If the model has poor sensitivity or specificity, all downstream enrichment analyses and biological conclusions would be compromised.  
  - **Resolution test** Provide full methodological details, benchmark results against established predictors, cross-validation performance, and an independent test set evaluation in the full manuscript.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Statistical rigor  
  - **Claim pointer** The claim that predicted amyloidogenic proteins are "consistently and significantly enriched" in Gene Ontology categories related to transcriptional regulation across all four organisms  
  - **Evidence pointer** Abstract, Results section; location not provided  
  - **Concern** The abstract reports Fisher's exact test results only for eukaryotic proteomes, not for all four organisms. The claim of consistency across all four organisms is not supported by the statistical evidence described. Additionally, no effect sizes, multiple-testing corrections, or control analyses are mentioned.  
  - **Why it matters** The central biological conclusion depends on the robustness of the enrichment analysis. Inconsistent statistical reporting and lack of multiple-testing correction could lead to false-positive enrichment calls.  
  - **Resolution test** Report enrichment statistics for all four organisms individually, include effect sizes and confidence intervals, apply and describe multiple-testing corrections, and provide appropriate controls such as shuffled or negative-control protein sets.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** The claim that "residue-level mapping demonstrated spatial separation between predicted aggregation-prone regions and DNA-binding interfaces"  
  - **Evidence pointer** Abstract, Results section; location not provided  
  - **Concern** No details are provided on how DNA-binding interfaces were defined, how spatial separation was quantified, or what statistical or structural evidence supports this claim. The abstract does not indicate whether this analysis was performed on all predicted amyloidogenic NABPs or a subset.  
  - **Why it matters** This spatial separation claim is used to argue for "structural compatibility between regulatory function and conditional aggregation." Without rigorous structural or computational evidence, this claim is speculative.  
  - **Resolution test** Provide detailed methods for interface prediction, define the metric for spatial separation, report the number of proteins analyzed, and include statistical comparisons against appropriate controls.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** The claim that "experimental validation confirmed fibrillar assembly of selected proteins"  
  - **Evidence pointer** Abstract, Results section; location not provided  
  - **Concern** The abstract does not specify how many proteins were experimentally tested, which organisms they came from, what experimental methods were used, or whether the results were quantitative or qualitative.  
  - **Why it matters** Experimental validation is a key pillar of the study's conclusion. Without details on the scope and rigor of the experiments, the strength of this evidence cannot be evaluated.  
  - **Resolution test** Report the number of proteins tested, experimental methods (e.g., ThT fluorescence, electron microscopy, X-ray diffraction), and representative results in the full manuscript.

  - **Concern ID** R1-M5  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Claim scope  
  - **Claim pointer** The claim that the model is "conserved across 3.5 billion years of evolution"  
  - **Evidence pointer** Abstract, Results section; location not provided  
  - **Concern** The abstract provides no phylogenetic analysis, no divergence time estimates, and no comparative framework to support a specific evolutionary timescale. The four organisms studied do not bracket 3.5 billion years of evolution in a way that would justify this claim without additional ancestral state reconstruction or molecular dating.  
  - **Why it matters** This is a strong evolutionary claim that extends beyond the data presented. Overstating the evolutionary scope could mislead readers about the strength of the evidence.  
  - **Resolution test** Provide a phylogenetic framework, ancestral state reconstruction, or at minimum a clearly stated rationale for how the four organisms support the proposed evolutionary timescale.

- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Abstract, Motivation section  
  - **Evidence pointer** Abstract, Motivation section; location not provided  
  - **Issue** The phrase "whether aggregation-prone sequence architectures are selectively constrained within transcriptional networks" is ambiguous. It is unclear whether the authors mean selectively retained, selectively depleted, or something else.  
  - **Required correction** Rephrase to clearly state the hypothesis being tested, for example whether aggregation-prone sequences are enriched, depleted, or neutrally distributed within transcriptional networks.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Reporting completeness  
  - **Affected element** Abstract, Results section  
  - **Evidence pointer** Abstract, Results section; location not provided  
  - **Issue** The abstract mentions "three independent annotation tools" for validation of GO enrichment but does not name them.  
  - **Required correction** Name the three annotation tools in the abstract or indicate that they are described in the full manuscript.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Abstract, Availability section  
  - **Evidence pointer** Abstract, Availability section; location not provided  
  - **Issue** The abstract states that VAEBAC is freely accessible at a URL, but no version number, access date, or usage instructions are provided.  
  - **Required correction** Provide a version identifier and brief usage instructions, or indicate where these are documented.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Terminology  
  - **Affected element** Abstract, Results section  
  - **Evidence pointer** Abstract, Results section; location not provided  
  - **Issue** The term "conditional aggregation" is introduced without definition.  
  - **Required correction** Define what is meant by conditional aggregation, or replace with a more standard term.

## Risk / unsupported claims
- The claim that VAEBAC performs reliable proteome-scale prediction of amyloidogenicity is unsupported from the abstract alone, as no performance metrics or benchmarking are provided.
- The claim of consistent significant enrichment across all four organisms is not supported by the statistical evidence described, which mentions Fisher's exact test only for eukaryotic proteomes.
- The claim of spatial separation between aggregation-prone regions and DNA-binding interfaces is unsupported without methodological details.
- The claim of experimental validation of fibrillar assembly is unverifiable without experimental details.
- The claim of conservation across 3.5 billion years of evolution is unsupported by the evidence described in the abstract.
- The overall biological model of functional stratification of aggregation susceptibility is a reasonable hypothesis but is not established from the supplied material.