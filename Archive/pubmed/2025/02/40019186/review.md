## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to the database, its contents, or the full manuscript
- **Shared manuscript claim summary** The authors present KSHVbook, a web-based information-sharing database for Kaposi's sarcoma-associated herpesvirus (KSHV), integrating gene, coding sequence, protein, and regulatory region information, along with approximately 35,010 transcription factor binding sites (TFBSs), 342,010 KSHV miRNA-host target gene pairs, AlphaFold3-predicted protein structures, and qPCR primers. The platform also provides analytical tools for viral genome regions, TFBSs, and miRNA target genes, intended to identify regulatory relationships between host transcription factors and viral genes.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, database content, user interface, validation results, comparison with existing resources, and any quantitative performance metrics

## Reviewer
- **Overall assessment** The abstract describes a potentially useful community resource for KSHV researchers, but the evidence provided is insufficient to evaluate the database's accuracy, completeness, usability, or novelty. The claims are broad and largely unverifiable from the abstract alone. The resource may be of interest to the KSHV field, but the case for its value and reliability is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying KSHV biology, including those focused on viral gene regulation, miRNA-host interactions, and protein structure. Clinicians and translational scientists working on Kaposi's sarcoma, primary effusion lymphoma, multicentric Castleman's disease, and KSHV inflammatory cytokine syndrome may also find the resource useful for identifying potential regulatory mechanisms. The database could serve as a starting point for hypothesis generation in these areas.
- **Major strengths** The abstract identifies a clear gap in existing KSHV information platforms and proposes a centralized resource with multiple data types. The inclusion of TFBSs, miRNA-target relationships, and AlphaFold3-predicted structures suggests a broad scope. The development of analytical tools tailored to KSHV is a reasonable and potentially valuable addition.
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
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: The abstract does not provide sufficient detail to assess whether the database offers novel content or methods beyond existing resources. The claim of "relatively lack comprehensiveness" in existing platforms is not substantiated with specific comparisons.  
  - Scientific importance: The topic is relevant to a specialized but active research community. However, the abstract does not demonstrate how the database will advance fundamental understanding of KSHV biology or disease mechanisms.  
  - Interdisciplinary readership: The resource may appeal to virologists, molecular biologists, and bioinformaticians, but the abstract does not articulate cross-disciplinary relevance beyond the immediate KSHV field.  
  - Technical soundness: No methods, validation, or quality control measures are described. The accuracy of the TFBS, miRNA-target, and structure predictions cannot be evaluated.  
  - Readability for nonspecialists: The abstract is generally clear but uses field-specific terms without explanation. The lack of context for the database's utility limits accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a plausible resource, but the absence of validation, comparison, and technical detail prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Data accuracy and validation  
- **Claim pointer** The database includes approximately 35,010 TFBSs, 342,010 KSHV miRNA-host target gene pairs, and AlphaFold3-predicted protein structures.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract provides no information on how these data were generated, curated, or validated. No sources, algorithms, thresholds, or quality control measures are described.  
- **Why it matters** Without validation, the reliability of the database content is unknown. Users may base experimental hypotheses on incorrect or outdated data, undermining the resource's utility.  
- **Resolution test** Provide a methods section detailing data sources, prediction algorithms, filtering criteria, and validation against experimental or curated datasets. Include error rates or benchmarking results.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Novelty and comparison with existing resources  
- **Claim pointer** Existing information platforms "relatively lack comprehensiveness and do not provide efficient analysis tools tailored for KSHV."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not identify which existing platforms were considered or how KSHVbook differs from them. No comparative analysis is presented.  
- **Why it matters** The claim of filling a gap is central to the resource's justification. Without explicit comparison, the novelty and added value of KSHVbook cannot be assessed.  
- **Resolution test** Provide a table or section comparing KSHVbook with at least two existing herpesvirus or general viral databases, highlighting unique features and data coverage.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Tool functionality and usability  
- **Claim pointer** The analytical tools can "effectively identify the potential regulatory relationships between host transcription factors and viral genes."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No description of the tools' inputs, outputs, algorithms, or user interface is given. The claim of effectiveness is not supported by any example, benchmark, or case study.  
- **Why it matters** The tools are a key differentiator of the platform. Without evidence of functionality and usability, the claim that they facilitate discovery is unsubstantiated.  
- **Resolution test** Provide a detailed description of each tool, including a workflow example, output format, and a demonstration on a known KSHV regulatory interaction. Include user testing or performance metrics.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Database accessibility and maintenance  
- **Claim pointer** The platform is accessible at http://www.kshvbook.com and "will continue to be updated."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not state whether the database is freely accessible, whether registration is required, or how updates are managed. No information on data versioning, citation policy, or long-term sustainability is provided.  
- **Why it matters** For a community resource, accessibility and maintenance are critical for adoption and long-term value. Lack of clarity on these points reduces confidence in the resource's reliability.  
- **Resolution test** State access conditions, update frequency, data versioning, and funding or institutional support for maintenance. Provide a data availability statement.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of scope  
- **Affected element** Description of database contents  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract lists "genes, coding sequences, proteins, and the gene regulatory region" but does not specify the number of genes or the completeness of the genome representation.  
- **Required correction** Specify the number of KSHV genes and the genome version used, and clarify whether all known viral genes are included.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology accessibility  
- **Affected element** Use of field-specific terms  
- **Evidence pointer** Abstract, location not provided  
- **Issue** Terms such as "TFBSs" and "miRNA-host target gene relationships" are used without brief definitions, which may limit readability for nonspecialists.  
- **Required correction** Add brief parenthetical explanations for these terms on first use.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Quantitative claims  
- **Affected element** Counts of data entries  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The numbers 35,010 and 342,010 are presented as approximate but no confidence intervals or sources are given.  
- **Required correction** Provide the data version or retrieval date for these counts and cite the underlying sources.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Future plans  
- **Affected element** Statement on updates  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The statement that the database "will continue to be updated" is vague and does not indicate a timeline or mechanism.  
- **Required correction** Describe the update process, including how new data will be incorporated and how users will be notified.

## Risk / unsupported claims
- The claim that existing platforms "relatively lack comprehensiveness" is unsupported without specific comparisons.
- The claim that the analytical tools "can effectively identify" regulatory relationships is unsupported without examples or benchmarks.
- The accuracy and completeness of the TFBS, miRNA-target, and protein structure data are unverifiable from the abstract.
- The accessibility, maintenance, and long-term sustainability of the database are not assessable from the supplied material.