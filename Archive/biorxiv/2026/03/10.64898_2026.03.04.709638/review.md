## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and methods as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present TFBSpedia, a new integrated database of human and mouse transcription factor binding sites (TFBS) built from ENCODE ATAC-seq and Cistrome ChIP-seq data, combined with four existing TFBS resources. They report that existing resources contain substantial unique predictions, that multi-database-supported TFBS regions are more likely to be biologically meaningful, and that two scores (confidence and importance) capture prediction reliability and functional relevance. A lightweight search engine is introduced.
- **Visible evidence base** Abstract text only; no datasets, benchmarking details, statistical analyses, or software implementation descriptions are visible
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods section, database schema, search engine implementation details, evaluation dataset descriptions, and any code or data availability statements

## Reviewer
- **Overall assessment** The abstract describes a potentially useful community resource, but the evidence presented is insufficient to evaluate the core claims. The benchmarking approach is mentioned but not described in any detail, and the two proposed scores lack operational definitions. The claim that multi-database-supported regions are more likely to be true binding sites requires statistical support that is not visible. The work addresses a real gap in the field, but the current abstract does not establish that the gap has been convincingly filled.
- **Who would be interested in the results, and why** Researchers in gene regulation, epigenomics, and computational genomics would be the primary audience. The database could serve as a reference resource for interpreting non-coding variants, designing experimental validation studies, and benchmarking new TFBS prediction algorithms. Clinically oriented groups studying regulatory variants in disease would also find value if the importance score is validated.
- **Major strengths** The integration of multiple data types and existing resources addresses a recognized need for harmonized TFBS annotation. The scale of the resource (11.3 million human and 1.87 million mouse TFBS) is substantial. The explicit focus on benchmarking across sequencing technologies and algorithms is a valuable framing. The introduction of two distinct scores for reliability and functional relevance is conceptually useful.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The benchmarking methodology is not described, the scoring definitions are absent, the evaluation datasets are not characterized, and no validation statistics are provided. Without these, the central claims cannot be assessed.
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The integration approach is not conceptually novel, but the scale and combination of resources may offer a new contribution.  
  - Scientific importance: Potentially high if the resource is accurate and widely usable, but this is not established from the abstract.  
  - Interdisciplinary readership: The topic is relevant to genomics, molecular biology, and computational biology, but the abstract does not demonstrate broad accessibility.  
  - Technical soundness: Cannot be evaluated from the abstract; no methods or validation are visible.  
  - Readability for nonspecialists: The abstract is clear and well structured, but technical terms such as ATAC-seq, ChIP-seq, and footprint are used without explanation.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a promising resource, but the core claims require the full manuscript for evaluation. Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that no study has systematically benchmarked TFBS databases across different sequencing technologies and computational algorithms, and that they addressed this gap.  
- **Evidence pointer** Abstract, benchmarking description; location not provided  
- **Concern** The abstract states that benchmarking was performed but provides no description of the benchmarking methodology, including which databases were compared, what metrics were used, how ground truth was defined, or how sequencing technology and algorithm differences were controlled.  
- **Why it matters** The claim of addressing a field gap rests entirely on the quality and rigor of the benchmarking. Without methodological detail, the reader cannot determine whether the comparison was fair, comprehensive, or statistically valid.  
- **Resolution test** The full manuscript must provide a detailed benchmarking protocol, including dataset selection criteria, evaluation metrics, statistical tests, and a clear statement of what constitutes a meaningful difference between databases.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that TFBS regions predicted by multiple databases are more likely to represent true and biologically meaningful binding sites.  
- **Evidence pointer** Abstract, evaluation section; location not provided  
- **Concern** This claim is presented as a finding, but no supporting statistics, effect sizes, or significance tests are reported. The abstract does not specify how "true" and "biologically meaningful" were operationalized or how the ten independent genomic annotation datasets were used to reach this conclusion.  
- **Why it matters** This is a central claim that justifies the value of the integrated database. If the evidence is weak or the analysis is circular, the entire resource loses credibility.  
- **Resolution test** The manuscript must show quantitative results, such as enrichment scores, precision-recall curves, or odds ratios with confidence intervals, comparing multi-database-supported regions against single-database regions, using clearly defined external annotations.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The authors introduce two scores for each predicted TFBS region: a confidence score reflecting prediction reliability and an importance score representing biological functional relevance.  
- **Evidence pointer** Abstract, scoring description; location not provided  
- **Concern** The abstract does not define how either score is calculated, what inputs they use, or how they were validated. Without this information, the scores are not interpretable or reproducible.  
- **Why it matters** Scores are only useful if users understand their meaning and limitations. If the scoring methodology is opaque, the database cannot be used responsibly.  
- **Resolution test** The full manuscript must provide formal definitions, formulas, input features, and validation results for both scores, including comparisons against independent functional readouts.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Interdisciplinary readership  
- **Claim pointer** The authors state that mapping TFBS is essential for advancing treatments for diseases driven by DNA modifications, including epigenetic changes and sequence variants.  
- **Evidence pointer** Abstract, introduction; location not provided  
- **Concern** The link between TFBS mapping and disease treatment is asserted but not elaborated. No examples, mechanisms, or clinical contexts are provided.  
- **Why it matters** For a broad readership, the translational relevance needs to be made concrete. Without examples, the claim remains rhetorical rather than substantive.  
- **Resolution test** The manuscript should include at least one concrete example or case study showing how the database can be used to interpret disease-associated variants or epigenetic changes.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, terminology  
- **Evidence pointer** Abstract, first paragraph; location not provided  
- **Issue** The terms ATAC-seq, ChIP-seq, and footprint are used without definition or context.  
- **Required correction** Provide brief definitions or explanatory phrases for these technologies in the abstract or introduction.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Database description  
- **Evidence pointer** Abstract, database construction; location not provided  
- **Issue** The abstract does not state how the ENCODE and Cistrome datasets were processed, filtered, or harmonized before integration.  
- **Required correction** Include a brief description of the processing pipeline or refer to a methods section.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Usability  
- **Affected element** Search engine description  
- **Evidence pointer** Abstract, final sentence; location not provided  
- **Issue** The search engine is described as "lightweight and efficient" but no performance metrics or usage examples are given.  
- **Required correction** Provide query response times, database size, or a simple use case to substantiate the efficiency claim.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Accessibility  
- **Affected element** Data availability  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No mention of data access, download options, or licensing terms for the database.  
- **Required correction** State where and how the database and search engine can be accessed.

## Risk / unsupported claims
- The claim that no prior study has systematically benchmarked TFBS databases across sequencing technologies and algorithms is unverifiable from the abstract alone and may be overstated.
- The claim that multi-database-supported TFBS regions are more likely to be true and biologically meaningful is unsupported without statistical evidence.
- The confidence and importance scores are undefined and therefore not assessable.
- The translational relevance to disease treatment is asserted without supporting examples or references.
- The efficiency of the search engine is claimed but not demonstrated.