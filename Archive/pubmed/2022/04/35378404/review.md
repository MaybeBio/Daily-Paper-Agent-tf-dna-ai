## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract, as supplied
- **Shared manuscript claim summary** The authors report a systematic analysis of cancer-associated MDC1 mutations from ICGC, TCGA, and COSMIC databases, identifying 711 somatic mutations across 26 cancer types. They selected 6 truncation and 7 missense mutations for functional characterization, showing that truncation mutations abolish MDC1-gammaH2AX interaction and biological function, that 2 FHA domain missense mutations impair ATM phosphorylation, and that 5 BRCT domain missense mutations disrupt gammaH2AX interaction, foci formation of MDC1, 53BP1, and BRCA1, and G2/M checkpoint control. Structural modeling was used to propose mechanisms for the missense mutation defects. The authors conclude these mutations cause functional defects in DNA damage response and may serve as future cancer diagnostic biomarkers.
- **Visible evidence base** Abstract text only. No figures, tables, methods, statistical analyses, or supplementary data are provided.
- **Missing materials affecting confidence** Full manuscript, all figures and tables, detailed methods for mutation selection and functional assays, structural modeling parameters, raw data, statistical details, and any validation experiments.

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable survey of cancer-associated MDC1 mutations and initial functional characterization. The scope is relevant to DNA repair and cancer biology. However, the evidence base available for review is limited to the abstract, which prevents verification of key claims regarding mutation frequencies, functional assay results, and structural interpretations. The conclusion that these mutations may serve as biomarkers is speculative and not supported by the data described. The work could be of interest to the DNA repair and cancer genomics communities, but the current evidence does not establish the case as presented.
- **Who would be interested in the results, and why** Researchers studying DNA double-strand break repair, particularly the MDC1-mediated signaling cascade, and cancer geneticists interested in the functional impact of somatic mutations in DDR genes. The mutation catalog and functional data could inform variant interpretation in cancer genomics studies.
- **Major strengths** The abstract addresses a gap in systematic analysis of MDC1 mutations in cancer. The combination of database mining with functional assays and structural modeling is a reasonable approach. The selection of both truncation and missense mutations across key domains provides a broad initial survey.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: The systematic survey of MDC1 mutations is a useful contribution, but the functional findings largely recapitulate known MDC1 domain functions. Scientific importance: Moderate, as the work provides a catalog and initial functional data, but the biomarker claim is premature. Interdisciplinary readership: The topic bridges cancer genomics and DNA repair, which could attract a broad audience, but the abstract does not provide sufficient mechanistic depth. Technical soundness: Cannot be fully assessed from the abstract alone. Readability for nonspecialists: The abstract is generally clear, though some domain-specific terms are used without explanation.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if technical concerns are resolved and full data are made available.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that 711 somatic mutations of MDC1 were analyzed across 26 types of human cancers, and that 6 truncation and 7 missense mutations were selected for functional study.
- **Evidence pointer** Abstract only, location not provided
- **Concern** The abstract does not describe the criteria for mutation selection from the 711 identified mutations to the 13 studied mutations. It is unclear whether the selection was random, based on recurrence, predicted pathogenicity, or domain location. Without this information, the representativeness of the studied set cannot be evaluated.
- **Why it matters** If the selected mutations are not representative of the broader mutation spectrum, the conclusions about functional defects may be biased and not generalizable to cancer-associated MDC1 mutations as a whole.
- **Resolution test** Provide a clear description of the selection criteria, including any filtering steps, in the full manuscript. Ideally, show a comparison of the selected mutations to the full set in terms of domain distribution and mutation type.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that 6 truncation mutations abolish MDC1-gammaH2AX interaction and abrogate its biological functions in DNA damage repair.
- **Evidence pointer** Abstract only, location not provided
- **Concern** The abstract states that truncation mutations abolish gammaH2AX interaction, but no functional assay data are shown. It is not specified which biological functions were tested, how they were measured, or whether any residual function was observed. The claim of complete abrogation is strong and requires quantitative evidence.
- **Why it matters** Truncation mutations may retain partial function depending on the location of the truncation. Overstating the loss of function could mislead interpretations of the mutation impact in cancer.
- **Resolution test** Provide representative data for each truncation mutant showing gammaH2AX interaction (e.g., co-immunoprecipitation) and at least one functional assay (e.g., IR-induced foci formation, cell survival, or checkpoint activation) with appropriate controls and quantification.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that 5 missense mutations in the BRCT domain abolished interaction with gammaH2AX, resulting in defects in foci formation of MDC1, 53BP1, and BRCA1, as well as defects in G2/M checkpoints.
- **Evidence pointer** Abstract only, location not provided
- **Concern** The abstract reports multiple functional consequences for the BRCT domain mutants, but no data are presented. It is unclear whether all 5 mutants showed the same phenotype or whether there was variability. The relationship between loss of gammaH2AX interaction and downstream foci defects is expected based on known MDC1 biology, but the abstract does not demonstrate this directly.
- **Why it matters** The claim that all 5 mutants behave identically is strong and requires demonstration of consistency. Variability among mutants could indicate differential impacts and would affect the interpretation of the structural modeling.
- **Resolution test** Show individual data for each of the 5 BRCT mutants for gammaH2AX interaction, foci formation, and checkpoint assays. Include statistical analysis to support the claim of complete loss of function.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive overreach
- **Claim pointer** The authors conclude that these cancer-associated MDC1 mutations may serve as biomarkers for cancer diagnostics in the future.
- **Evidence pointer** Abstract only, location not provided
- **Concern** The abstract provides no data linking the functional defects of these mutations to clinical outcomes, diagnostic performance, or patient stratification. The biomarker claim is speculative and not supported by the evidence described.
- **Why it matters** Biomarker claims require demonstration of clinical relevance, such as association with prognosis, treatment response, or diagnostic accuracy. Without such data, the claim is premature and could be misleading.
- **Resolution test** Either remove the biomarker claim or provide preliminary evidence, such as correlation of mutation status with clinical features, in the full manuscript. If not available, frame the conclusion as a hypothesis for future work.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Mutation selection description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that mutations were summarized from ICGC, TCGA, and COSMIC databases, but it is not clear whether these databases were queried independently or combined, and how duplicate entries were handled.
- **Required correction** Clarify the database integration approach and any deduplication steps in the methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Structural modeling description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions structural modeling to analyze the mechanism of missense mutations, but does not specify the method (e.g., molecular dynamics, docking, or homology modeling) or the structural templates used.
- **Required correction** Provide details of the modeling approach and validation in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Precision
- **Affected element** Mutation count statement
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that 711 somatic mutations were analyzed, but it is unclear whether this number includes all mutation types (e.g., silent, intronic) or only protein-altering variants.
- **Required correction** Specify the mutation types included in the analysis and the filtering criteria applied.

## Risk / unsupported claims
- The claim that the studied mutations may serve as biomarkers for cancer diagnostics is unsupported by the evidence described in the abstract.
- The claim that truncation mutations "abrogate" biological functions is not verifiable without functional data.
- The claim that all 5 BRCT domain missense mutations abolish gammaH2AX interaction and downstream functions is not verifiable without individual mutant data.
- The representativeness of the 13 selected mutations relative to the 711 identified mutations is not assessable from the abstract.