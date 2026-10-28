## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, data interpretation, and claims as presented in the supplied text; no external verification of data or resources
- **Shared manuscript claim summary** The authors present GDC, a new database integrating multi-omic and phenotypic data for hearing loss research, and use it to characterize the genetic landscape of HL, identify mutational hotspots, compare human and mouse phenotypes, and apply machine learning to predict candidate HL genes, with TBX2 proposed as a newly confirmed HL gene
- **Visible evidence base** Text descriptions of results, figures referenced (Figures 1–8, S1–S10), tables referenced (Tables S1–S7), methods descriptions, statistical details in the Statistical Analysis section
- **Missing materials affecting confidence** No actual database content, no figure panels or table data visible, no code or model parameters, no detailed variant-level data, no access to the GDC website, no supplementary files, no raw or processed sequencing data

## Reviewer
- **Overall assessment** This manuscript describes a substantial data integration effort and presents several analyses of potential interest to the hearing loss genetics community. The database itself may be a useful resource. However, the manuscript as presented has significant issues that prevent full evaluation: key results are described without visible data, the machine learning approach has methodological ambiguities, the validation of TBX2 is referenced rather than shown, and several claims go beyond what the presented evidence can support. The work is potentially valuable but is not currently established from the provided material.
- **Who would be interested in the results, and why** Researchers in hearing loss genetics, clinical geneticists involved in diagnostic testing for deafness, bioinformaticians working on disease gene prioritization, and developers of disease-specific databases. The mutational hotspot analysis and the machine learning approach for candidate gene identification may also interest those working on variant interpretation and gene discovery in other Mendelian disorders.
- **Major strengths** The integration of a large number of public resources into a single HL-focused database is a useful contribution. The analysis of variant pathogenicity across 201 genes, including the identification of mutational hotspots, addresses a real need in clinical variant interpretation. The comparison of human and mouse phenotypes highlights an important and often underappreciated issue in model organism research. The machine learning approach, while having issues, represents a reasonable attempt to leverage integrated data for gene discovery.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (database accessibility and content verification), R1-M2 (machine learning methodology), R1-M3 (TBX2 validation), R1-M4 (statistical reporting), R1-M5 (data availability)
- **Assessment against Nature-style criteria** Originality: moderate. The database is new but the concept of integrating genomic resources is not novel. The hotspot analysis and machine learning application have elements of novelty. Scientific importance: potentially high for the HL genetics community, but the impact depends on the database being a widely used resource, which is not yet demonstrated. Interdisciplinary readership: limited; the work is primarily relevant to genetics and audiology researchers. Technical soundness: not fully assessable from the provided material; several methodological details are missing or ambiguous. Readability for nonspecialists: the manuscript is generally readable but assumes familiarity with genetics and bioinformatics concepts; some sections are dense.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript describes a potentially useful resource and presents interesting analyses, but key claims cannot be verified from the material provided. Major revisions and additional data presentation are required before the case is established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data accessibility and verification
- **Claim pointer** The authors claim that GDC is a "comprehensive and unified repository" integrating data from 51 public databases and the CDGC, comprising 5,983,613 variants across 201 HL genes.
- **Evidence pointer** Abstract; Results section "Overview of GDC"; Figure 1; Tables S1 and S2
- **Concern** The central claim of this manuscript is the creation of a comprehensive database, yet no evidence of the database's content, structure, or functionality is visible in the provided material. The figures and tables that would demonstrate the database are referenced but not shown. The database website (http://gdcdb.net/) is mentioned but cannot be accessed for verification. The number of variants (5,983,613) is stated, but the breakdown by source, the overlap between sources, and the quality control measures applied are not described in sufficient detail.
- **Why it matters** The database is the foundation of the entire manuscript. Without the ability to verify its content, the downstream analyses cannot be evaluated. A database paper must demonstrate that the resource is real, accessible, and of sufficient quality to be useful. The current presentation does not allow this.
- **Resolution test** Provide a detailed description of the database schema, data sources, and quality control procedures. Show representative examples of the database interface and output. Provide summary statistics of the data content, including variant type distribution, gene coverage, and population representation. Ensure the website is accessible and functional for reviewers.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Machine learning methodology
- **Claim pointer** The authors claim that a SMOTE-Random Forest model identified 18 candidate HL genes, and that TBX2 was "newly confirmed as an HL gene."
- **Evidence pointer** Results section "Identification of Candidate HL Genes by Integrating Expression and Function Datasets"; Figure 8; Table S6 and S7
- **Concern** The machine learning methodology is described at a high level but lacks critical details. The feature set is described as including expression levels, expression correlations, GO terms, and pathways, but the exact features, their construction, and their preprocessing are not specified. The use of SMOTE is mentioned, but the oversampling ratio and its justification are not given. The random forest parameters (e.g., number of trees, depth) are not stated. The evaluation procedure is unclear: the authors mention ten models trained on ten datasets, but the cross-validation scheme, the metric used for model selection, and the threshold for calling a gene "positive" are not described. The claim that TBX2 is "newly confirmed" is referenced to another publication [60] but no data from that validation is presented here.
- **Why it matters** The machine learning analysis is a key component of the manuscript, demonstrating the utility of the GDC resource. Without a clear description of the methodology, the results cannot be reproduced or evaluated. The claim of a "newly confirmed" gene is a strong one that requires direct evidence, not just a citation.
- **Resolution test** Provide a complete description of the feature engineering, model training, hyperparameter tuning, and evaluation procedure. Include a detailed flowchart of the analysis. Present the validation data for TBX2, including patient phenotypes, variant segregation, and functional studies, or clearly state that this is described in a separate publication and limit the claim here to "candidate gene identification."

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of novel gene claim
- **Claim pointer** The authors state that "TBX2, newly confirmed as an HL gene" was identified among the 18 candidate genes.
- **Evidence pointer** Results section "Identification of Candidate HL Genes by Integrating Expression and Function Datasets"; Discussion
- **Concern** The claim that TBX2 is a confirmed HL gene is a major finding, but the evidence is not presented in this manuscript. The text refers to reference [60] for the validation, but no details of the validation are provided. It is unclear whether the validation was performed by the same group, whether it involved human cohorts, functional assays, or animal models, and what the strength of the evidence is. The manuscript cannot make this claim without presenting the supporting data.
- **Why it matters** Confirming a novel disease gene is a significant scientific contribution. The claim must be supported by direct evidence within the manuscript, or the claim must be appropriately qualified. Referencing another paper without showing the data is insufficient for a claim of this magnitude.
- **Resolution test** Either present the full validation data for TBX2 (genetic, functional, and phenotypic) in this manuscript, or revise the claim to state that TBX2 was "identified as a candidate gene and validated in a separate study [60]." The current wording is misleading.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical reporting
- **Claim pointer** The authors report correlation coefficients (R2 0.718–0.752) for cross-species expression comparisons and various statistical analyses throughout the results.
- **Evidence pointer** Results sections "Expression Features of HL Genes in Human, Mouse, and Rhesus Macaque Cochlea"; "Discrepancies of HL Phenotype Between Human and Mouse Models"; Statistical Analysis
- **Concern** The statistical reporting is inconsistent and often incomplete. For the correlation analyses, only R2 values are given without confidence intervals or p-values. The phenotype comparison between human and mouse models is described qualitatively without statistical tests. The GO and pathway enrichment analyses are mentioned but the statistical methods and multiple testing corrections are not described. The likelihood ratio calculations are described in the methods but the results are not presented with confidence intervals in the text.
- **Why it matters** The scientific claims depend on the statistical robustness of the analyses. Without proper statistical reporting, the reader cannot assess the strength of the evidence. This is particularly important for the cross-species comparisons and the enrichment analyses, which are used to support major conclusions.
- **Resolution test** Provide complete statistical details for all analyses: p-values, confidence intervals, effect sizes, and multiple testing corrections. For the correlation analyses, provide scatter plots with regression lines and confidence bands. For the enrichment analyses, specify the statistical test, the background set, and the multiple testing correction method.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data availability
- **Claim pointer** The authors state that "The data that support the findings of this study are available from the corresponding author upon reasonable request."
- **Evidence pointer** Data Availability Statement
- **Concern** For a database paper, this data availability statement is inadequate. The entire point of the manuscript is to present a resource that the community can use. The data should be publicly accessible, either through the GDC website or through a public repository. Requiring a request to the corresponding author is not consistent with the goal of a community resource and does not meet modern standards for data availability.
- **Why it matters** The utility of the GDC depends on its accessibility. If the data are not publicly available, the resource cannot be used by the community, and the claims of the manuscript cannot be verified.
- **Resolution test** Make the database publicly accessible, either through the GDC website or through a public repository such as Zenodo, Figshare, or a genomic data repository. Provide clear instructions for access and usage. Update the Data Availability Statement accordingly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Results section "Overview of GDC"
- **Evidence pointer** Figure 1; Tables S1 and S2
- **Issue** The text states that GDC "amalgamated data from 51 public sources" and lists several categories of information, but the figure and table references are not specific. It is unclear which figure panel or table section corresponds to which data category.
- **Required correction** Refer to specific panels or table sections when describing each data category. For example, "as shown in Figure 1B" or "detailed in Table S2, columns 3–5."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract; Results; Discussion
- **Issue** The terms "HL genes," "deafness genes," and "hearing loss genes" are used interchangeably. The term "genetic deafness" is used in the database name, but the manuscript focuses on hearing loss. This inconsistency could confuse readers.
- **Required correction** Use one consistent term throughout the manuscript, preferably "hearing loss (HL) genes" to match the title and abstract.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarification of "hotspot" definition
- **Affected element** Results section "Identification of 'Hotspots' for Pathogenic Missense Variants"
- **Evidence pointer** Figure 5; Table S4
- **Issue** The authors identify "six novel mutational hotspots within the DNA-binding domains of transcription factors" but the criteria for defining a "hotspot" are not explicitly stated. The Gaussian kernel density estimation is mentioned, but the threshold for calling a region a "hotspot" is not given.
- **Required correction** State the specific criteria used to define a hotspot, including the density threshold and the minimum number of variants required.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarification of PS score
- **Affected element** Results section "Discrepancies of HL Phenotype Between Human and Mouse Models"
- **Evidence pointer** Figure 6B
- **Issue** The phenotype similarity (PS) score is introduced but its calculation is not described in the methods. It is unclear what data were used and how the score was computed.
- **Required correction** Add a description of the PS score calculation to the methods section, including the data sources and the formula used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarification of "novel" hotspots
- **Affected element** Abstract; Results section "Identification of 'Hotspots' for Pathogenic Missense Variants"
- **Evidence pointer** Figure 5; Table S4
- **Issue** The authors state that six hotspots are "novel," but it is not clear what this means. Were these regions not previously described as hotspots for any gene, or not previously described for these specific genes? The comparison to existing knowledge is not stated.
- **Required correction** Clarify what "novel" means in this context and describe the comparison to previously reported hotspots.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarification of "confirmed" genes
- **Affected element** Results section "Identification of Candidate HL Genes by Integrating Expression and Function Datasets"
- **Evidence pointer** Figure 8E; Table S7
- **Issue** The text states that 18 candidate genes "exhibited HL phenotypes in mice." It is unclear whether this means the genes were previously known to cause HL in mice, or whether the authors performed new mouse experiments. The distinction is important for interpreting the significance of these candidates.
- **Required correction** Clarify the source of the mouse phenotype data and whether these are previously published findings or new experimental results.

## Risk / unsupported claims
- The claim that GDC is a "comprehensive and unified repository" cannot be evaluated without access to the database itself.
- The claim that TBX2 is "newly confirmed as an HL gene" is not supported by evidence presented in this manuscript; it is referenced to another publication.
- The claim of "six novel mutational hotspots" cannot be fully evaluated without the underlying variant data and the criteria for hotspot definition.
- The claim that the SMOTE-Random Forest model identified 18 candidate genes cannot be evaluated without the full methodological details and the underlying data.
- The cross-species expression correlations (R2 0.718–0.752) are reported without confidence intervals or p-values, making the strength of the correlation unclear.
- The phenotype comparison between human and mouse models is described qualitatively without statistical support.
- The GO and pathway enrichment analyses are mentioned but the statistical methods and results are not presented in sufficient detail.
- The claim that GDC "covers 17 out of 24 lines of evidence applicable to genetic HL as outlined by HL-ACMG" is not supported by a detailed mapping of which lines are covered and how.