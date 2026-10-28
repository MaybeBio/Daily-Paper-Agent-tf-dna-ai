## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, conclusions, supplementary data description, conflict of interest, funding, data availability, and acknowledgements.
- **Assessment boundary** Scientific content, methodological transparency, data curation rigor, integration of deep learning models, and consistency of claims with presented evidence. No assessment of code quality, website functionality, or database accessibility beyond what is described.
- **Shared manuscript claim summary** The manuscript reports the 2026 update of the JASPAR database, including expansion of the CORE and UNVALIDATED collections of transcription factor binding profiles, integration of a deep learning collection of 1259 BPNet models for 240 human TFs, introduction of an LLM-based TF-target gene annotation pipeline, and updates to associated tools and genome tracks.
- **Visible evidence base** Abstract, Introduction, Results sections (including subsections on classical profile expansion, clustering, deep learning collection, and tools), Conclusions, Supplementary data description, Conflict of interest, Funding, Data availability, and Acknowledgements. No figures, tables, or supplementary files were provided.
- **Missing materials affecting confidence** All figures, tables, supplementary tables (S1, S2, S3), supplementary figures (S1, S2, S3), and the Supplementary Text are referenced but not provided. This limits verification of quantitative claims, quality control metrics, and methodological details.

## Reviewer
- **Overall assessment** This manuscript describes a substantial update to a widely used community resource. The expansion of curated TF binding profiles and the introduction of a deep learning collection represent meaningful contributions. However, the absence of all figures, tables, and supplementary materials prevents verification of key quantitative claims and quality control procedures. The LLM-based TF-target annotation section is described with limited methodological detail and a modest validation set, which raises questions about scalability and accuracy. The manuscript is well written and accessible, but several claims are currently not fully supported by the provided evidence.
- **Who would be interested in the results, and why** Computational biologists, experimental researchers studying gene regulation, bioinformatics tool developers, and curators of biological databases. The expanded profile collections and the new deep learning models will be of direct use for TF binding site prediction, regulatory variant interpretation, and benchmarking of new methods. The integration of LLM-based annotations is relevant to the growing community applying large language models to biomedical text mining.
- **Major strengths** The manuscript addresses a clear community need by expanding a standard reference resource. The inclusion of a deep learning collection with interpretable motifs is timely and aligns with current trends in regulatory genomics. The manual curation process, including orthogonal validation and promotion of previously unvalidated profiles, reflects a rigorous approach. The integration of simulation tools and updated programmatic access packages enhances the utility of the resource.
- **Major Concerns** The concerns below are listed in order of importance.
- **Minor Comments** The minor comments are listed after the major concerns.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality: The update is incremental in nature, as expected for a database resource, but the deep learning collection introduces a novel component not present in previous releases. Scientific importance: High, given the widespread use of JASPAR in the field. Interdisciplinary readership: The resource is relevant to molecular biology, computational biology, and bioinformatics communities. Technical soundness: Cannot be fully assessed due to missing figures, tables, and supplementary materials. Readability for nonspecialists: The manuscript is clearly written and provides sufficient context for readers unfamiliar with the specific methods.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the provision of missing evidence and clarification of the LLM-based annotation methodology.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that 11,565 profiles were manually curated and that 306 new profiles were added to the CORE collection (12% increase) and 433 to the UNVALIDATED collection (60% increase).
- **Evidence pointer** Results section, subsection "Expansion and update of the classical TF binding profiles"; Table 1; Figure 1; Supplementary Table S2; location not provided for specific data points.
- **Concern** The quantitative claims regarding the number of curated profiles, the percentage increases, and the breakdown by taxonomic group are presented without the corresponding tables and figures. The reader cannot verify these numbers or assess the distribution of new profiles across taxa. Additionally, the criteria for promoting 41 profiles from UNVALIDATED to CORE are described only in general terms, and the specific literature support is not shown.
- **Why it matters** These numbers are central to the manuscript's claim of database expansion. Without the underlying data, the accuracy of the reported statistics cannot be confirmed, and the reproducibility of the curation process is not established.
- **Resolution test** Provide Table 1, Figure 1, and Supplementary Table S2, and describe the specific evidence used for the promotion of the 41 profiles. The numbers in the text should match the provided tables and figures exactly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The manuscript claims that 1259 BPnet models were trained on ENCODE ChIP-seq data from 240 TFs, and that quality control metrics were applied to ensure that identified motifs are supported by in vitro orthogonal evidence.
- **Evidence pointer** Results section, subsection "Deep learning collection"; Supplementary Figure S2; Supplementary Table S3; Supplementary Text; location not provided for specific quality control details.
- **Concern** The training procedure, hyperparameters, data preprocessing, and quality control metrics are not described in the main text. The reader is referred to the Supplementary Text, which is not provided. The claim that motifs are supported by in vitro orthogonal evidence is not substantiated with specific examples or a description of the comparison method. The number of models per TF and the criteria for selecting primary versus alternative motif patterns are also unclear.
- **Why it matters** The deep learning collection is a major new feature of this release. Without a clear description of the training and validation pipeline, the reliability of the models and the derived motifs cannot be assessed. This is critical for users who will rely on these models for downstream analyses.
- **Resolution test** Provide a detailed description of the training procedure, including data preprocessing, model architecture, hyperparameters, and quality control metrics. Include Supplementary Figure S2 and Supplementary Table S3, and describe the specific in vitro datasets used for orthogonal validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that the LLM-based approach achieved 88% accuracy (308/350) in extracting TF-target gene relationships, and that the most common errors were attributed to modifier-related and hypothetical statements.
- **Evidence pointer** Results section, subsection "Large language model-based TF-target gene associations"; Figure 2; Supplementary Text; location not provided for the error analysis details.
- **Concern** The validation set of 350 relationships is small, and the manual curation process for the initial set is described only briefly. The error analysis is mentioned but not detailed. The manuscript does not specify how the accuracy was calculated, whether it was at the level of individual relationships or entire sentences, or how the four relationship categories were balanced in the validation set. The generalizability of the approach to the full corpus is not demonstrated.
- **Why it matters** The LLM-based annotation is presented as a new feature, but the limited validation and lack of methodological detail make it difficult to judge the reliability of the annotations. Users may unknowingly rely on incorrect TF-target relationships.
- **Resolution test** Provide a detailed description of the prompt, the JSON schema, the manual curation protocol, and the error analysis. Report accuracy per relationship category and discuss potential biases in the validation set. If possible, include a larger validation set or a comparison with existing curated resources.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim consistency
- **Claim pointer** The abstract states that 306 new profiles were added to the CORE collection, while the Introduction states that 265 new profiles were added to the CORE collection and 421 to the UNVALIDATED collection, totaling 686 new profiles.
- **Evidence pointer** Abstract; Introduction; Results section, subsection "Expansion and update of the classical TF binding profiles"; location not provided.
- **Concern** There is a numerical discrepancy between the abstract and the Introduction. The abstract reports 306 new CORE profiles, while the Introduction reports 265 new CORE profiles and 421 new UNVALIDATED profiles. The Results section also reports 265 new CORE profiles and 871 new UNVALIDATED profiles, which is inconsistent with the Introduction's 421. The total number of new profiles also differs (306 vs. 686 vs. 1,136).
- **Why it matters** Inconsistent numbers across sections undermine the credibility of the reported statistics and confuse the reader. This is a basic factual error that should be corrected.
- **Resolution test** Reconcile the numbers across the abstract, Introduction, and Results. Ensure that the total number of new profiles and the breakdown by collection are consistent throughout the manuscript and match the provided tables.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the inMOTIFin tool allows users to generate simulated sequences with precise control over motif frequencies, positions, and co-occurrences, and that it is integrated into the JASPAR website.
- **Evidence pointer** Results section, subsection "Incorporation of the regulatory sequence and motif simulation tool, inMOTIFin"; reference [28]; location not provided for the tool's documentation.
- **Concern** The description of inMOTIFin is brief, and the manuscript does not provide details on the underlying algorithm, the parameters that can be controlled, or the validation of the tool. The reference to the standalone package is given, but the integration with JASPAR is not described in terms of user interface or output format. The claim of "precise control" is not supported by specific examples or benchmarks.
- **Why it matters** The tool is presented as a new feature, but without a clear description of its capabilities and limitations, users cannot assess whether it meets their needs. The lack of validation also raises questions about the reliability of the simulated data.
- **Resolution test** Provide a more detailed description of the inMOTIFin tool, including its algorithm, parameters, and validation. Include examples of simulated sequences and a comparison with existing simulation tools.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided.
- **Issue** The abstract states that the DL collection provides "a paradigm shift in modeling and characterizing TF-DNA interactions," which is a strong claim that is not fully supported by the described content. The DL collection is a valuable addition, but the term "paradigm shift" may overstate its novelty.
- **Required correction** Consider softening the language to "a significant advancement" or "a new approach" to better match the scope of the contribution.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, subsection "Large language model-based TF-target gene associations"
- **Evidence pointer** Results section, subsection "Large language model-based TF-target gene associations"; location not provided.
- **Issue** The manuscript mentions that the LLM-based annotations are available in the JASPAR interface, but it does not specify how users can access or query these annotations. The relationship between the LLM-based annotations and the existing TF-centric information is also unclear.
- **Required correction** Add a brief description of how the LLM-based annotations are displayed and how they complement existing data, such as a link to an example page or a search function.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Results section, subsection "Deep learning collection"
- **Evidence pointer** Results section, subsection "Deep learning collection"; location not provided.
- **Issue** The manuscript states that all trained BPnet models are available to users, but it does not specify the format or the platform for downloading them. The link to the MotifCompendium tool is given, but the models themselves are not linked.
- **Required correction** Provide a clear statement on how to access the models, including a URL or a description of the download process.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Introduction
- **Evidence pointer** Introduction; location not provided.
- **Issue** The Introduction provides a brief history of JASPAR and the rationale for the DL collection, but the transition from the discussion of traditional PWMs to the DL collection is abrupt. A more explicit connection between the limitations of PWMs and the advantages of DL models would improve readability.
- **Required correction** Add a sentence that explicitly links the limitations of PWMs to the motivation for the DL collection, such as "To address these limitations, we introduce a deep learning collection that captures complex binding patterns beyond the assumptions of position independence."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results section, subsection "Expansion and update of the classical TF binding profiles"
- **Evidence pointer** Results section, subsection "Expansion and update of the classical TF binding profiles"; location not provided.
- **Issue** The text mentions that 11 profiles were removed (seven from CORE and four from UNVALIDATED), but the reasons for removal are not specified. This is a minor point, but it would be helpful to know whether the removals were due to redundancy, data quality, or other factors.
- **Required correction** Add a brief explanation for the removals, such as "due to redundancy with newly added profiles" or "due to lack of supporting evidence."

## Risk / unsupported claims
- The claim of 88% accuracy for the LLM-based TF-target extraction is based on a small validation set of 350 relationships and may not generalize to the full corpus.
- The claim that the DL collection provides "a paradigm shift" is not fully supported by the described content.
- The numerical discrepancies between the abstract, Introduction, and Results regarding the number of new profiles are unresolved and undermine the reliability of the reported statistics.
- The quality control metrics for the DL models are referenced but not described, making the claim of "in vitro orthogonal evidence" unverifiable.
- The performance of the inMOTIFin tool is not validated, and the claim of "precise control" over sequence features is not demonstrated.