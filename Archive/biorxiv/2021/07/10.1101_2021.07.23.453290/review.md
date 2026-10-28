## Review setup
- **Input scope** Full manuscript text (abstract, background, construction and content, utility and discussion, declarations)
- **Assessment boundary** Scientific content, database utility, technical implementation, and claims as presented in the provided text. No independent testing of the web interface or database was performed.
- **Shared manuscript claim summary** The authors present PCRMS, a database of predicted cis-regulatory modules (CRMs) and transcription factor binding sites (TFBSs) in human and mouse genomes, generated using their dePCRM2 algorithm applied to CISTROME ChIP-seq datasets. They claim unprecedented completeness and high accuracy of predictions, and describe a web interface with browse, search, and functional analysis modules.
- **Visible evidence base** Abstract, Background, Construction and content (Datasets, Prediction of CRMs and constituent TFBSs, Technical implementation), Utility and discussion (Predicted CRMs and constituent TFBSs, Web interface, Browse, Functional analyses, Batch download, Future development), Conclusions, Declarations. Tables 1 and 2 are referenced but not shown. Figures 1-5 are referenced but not shown.
- **Missing materials affecting confidence** Tables 1 and 2, Figures 1-5, the dePCRM2 algorithm details (referenced as ref 47), validation data for mouse predictions (stated as manuscript in preparation), and any documentation of database schema or query performance. The web interface URL was not accessed.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful database resource for the regulatory genomics community. The core claims of unprecedented completeness and high accuracy rest on the dePCRM2 algorithm and prior validation, but the evidence presented here is largely descriptive and relies heavily on a separate publication. The database content is substantial in scale, and the web interface features are clearly described. However, the lack of direct validation data, comparative benchmarks within this manuscript, and absence of the referenced tables and figures limit the ability to fully assess the claims. The manuscript is more of a database report than a methods or discovery paper, and its suitability for a high-impact venue depends on the novelty and utility of the resource relative to existing databases.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, enhancer biology, non-coding variant interpretation, and comparative genomics would be interested. The database provides a large catalog of predicted CRMs and TFBSs that could be used for hypothesis generation, variant prioritization, and understanding gene regulatory networks. The web interface's functional modules for finding CRMs near genes and TFBSs for specific TFs are directly relevant to these users.
- **Major strengths** 1. The scale of the resource is substantial, with over 1.4 million and 0.9 million CRM candidates in human and mouse, respectively, and tens of millions of TFBSs. 2. The database addresses a gap by providing de novo predicted TFBSs within CRMs, which many existing enhancer databases lack. 3. The web interface is described with clear functionality for browsing, searching, and exporting data, which is essential for community adoption. 4. The use of a p-value cutoff system allows users to filter predictions by statistical confidence.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence for core claims
  - **Claim pointer** The manuscript claims "highly accurate and unprecedentedly complete maps of predicted CRMs and TFBSs" and that predictions are "substantially more accurate and more complete than those in existing databases."
  - **Evidence pointer** Abstract; Background; Utility and discussion, "Predicted CRMs and constituent TFBSs" section; Tables 1 and 2 (not shown)
  - **Concern** The central claims of accuracy and completeness are not directly supported by data presented in this manuscript. The authors reference a previous publication (ref 47) for validation of the human predictions, and state that mouse validation is "manuscript in preparation." Tables 1 and 2, which presumably contain comparative numbers, are not provided in the text. Without showing validation metrics (e.g., overlap with known enhancers, functional assays, conservation analyses) or comparative benchmarks against existing databases within this manuscript, the claims cannot be independently evaluated.
  - **Why it matters** The primary value proposition of the database is its accuracy and completeness. If these are not demonstrated in the manuscript itself, readers cannot assess whether the resource is reliable for their research. The claim of being "unprecedentedly complete" is strong and requires direct comparative evidence.
  - **Resolution test** Provide the data from Tables 1 and 2, including comparative statistics against ENCODE and GeneHancer. Include validation results for both human and mouse predictions, such as overlap with curated enhancer databases, expression quantitative trait loci (eQTL) enrichment, or experimental validation. If mouse validation is not yet complete, temper the claims accordingly.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility and technical transparency
  - **Claim pointer** The manuscript states that dePCRM2 was applied "using the default parameters" and describes the algorithm briefly, but the full details are in a separate publication.
  - **Evidence pointer** Construction and content, "Prediction of CRMs and constituent TFBSs" section
  - **Concern** The description of the prediction method is insufficient for reproducibility. The scoring functions are described with equations that are not fully defined in the text (e.g., the interaction score and CRM score formulas are incomplete). The parameters used, the exact filtering criteria for ChIP-seq peaks, and the thresholds for motif discovery are not specified. A reader cannot replicate the pipeline from this manuscript alone.
  - **Why it matters** For a database resource, reproducibility of the prediction pipeline is critical for user trust and for future updates. If the method is only available in a separate paper, the manuscript should at least provide a complete algorithmic description or a clear reference with sufficient detail.
  - **Resolution test** Provide a complete description of the dePCRM2 algorithm, including all formulas, parameters, and filtering steps, either in the main text or as supplementary material. Alternatively, provide a link to a publicly available code repository with documentation.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Utility and accessibility of the resource
  - **Claim pointer** The manuscript describes a web interface with browse, search, and functional analysis modules, and states that all predicted CRMCs can be downloaded.
  - **Evidence pointer** Utility and discussion, "Web interface", "Browse", "Functional analyses", "Batch download" sections; Figures 1-5 (not shown)
  - **Concern** The manuscript does not provide evidence that the web interface is functional, stable, or user-friendly. No screenshots are shown in the text (Figures 1-5 are referenced but not included). There is no mention of API access, which is increasingly important for programmatic use. The download functionality is mentioned but the format and size of the files are not described.
  - **Why it matters** A database is only useful if it is accessible and usable. Without evidence of a working interface or documentation of access methods, the practical value of the resource is unclear.
  - **Resolution test** Include screenshots of the web interface in the figures. Provide details on file sizes, download formats, and any API endpoints. Consider adding a usage tutorial or example workflows.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness
  - **Affected element** Background section, paragraph 2
  - **Evidence pointer** Background, paragraph 2
  - **Issue** The sentence "an exponentially increase number of datasets" contains a grammatical error. Also, the statement that existing databases "only cover a small portion of enhancers/CRMs" is made without specific citations or quantitative comparison.
  - **Required correction** Correct the grammatical error to "an exponentially increasing number of datasets." Provide specific examples or citations to support the claim about limited coverage of existing databases.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical accuracy
  - **Affected element** Construction and content, "Prediction of CRMs and constituent TFBSs" section
  - **Evidence pointer** Construction and content, "Prediction of CRMs and constituent TFBSs" section
  - **Issue** The equations for the interaction score and CRM score are incomplete. The text says "defined as," but the actual formulas are not fully rendered or explained. The variable definitions are also incomplete.
  - **Required correction** Provide complete equations with all variables clearly defined. If the equations are too complex for the main text, move them to a supplementary methods section.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data provenance
  - **Affected element** Construction and content, "Datasets" section
  - **Evidence pointer** Construction and content, "Datasets" section
  - **Issue** The manuscript states that ChIP-seq datasets were downloaded from CISTROME on 10/25/2018, but later states predictions were made using data available "6/1/2019." This discrepancy is confusing.
  - **Required correction** Clarify the timeline of data download and prediction. If additional data were added after the initial download, describe the update process.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness of resource description
  - **Affected element** Utility and discussion, "Functional analyses" section
  - **Evidence pointer** Utility and discussion, "Functional analyses" section
  - **Issue** The example of the GLI3 gene is described, but the text mentions "GL13" in one instance, which appears to be a typo.
  - **Required correction** Correct the typo "GL13" to "GLI3."
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Future directions
  - **Affected element** Utility and discussion, "Future development" section
  - **Evidence pointer** Utility and discussion, "Future development" section
  - **Issue** The future development section mentions adding predicted functional states, target genes, and causal variants, but does not mention any plans for incorporating single-cell data or chromatin conformation data, which are increasingly important for understanding gene regulation.
  - **Required correction** Consider adding these or other relevant future directions to strengthen the outlook.

## Technical failings that need to be addressed before the case is established
- R1-M1: Lack of direct validation and comparative data in the manuscript for the core claims of accuracy and completeness.
- R1-M2: Insufficient algorithmic detail for reproducibility of the prediction pipeline.

## Assessment against Nature-style criteria
- **Originality** Moderate. The database is a new resource, but the underlying algorithm (dePCRM2) is previously published. The novelty lies in the scale and completeness of the predictions, but this is an incremental advance over existing databases.
- **Scientific importance** Potentially high. A comprehensive and accurate catalog of CRMs and TFBSs would be a valuable community resource for understanding gene regulation and interpreting non-coding variants. However, the importance is contingent on the validity of the accuracy and completeness claims, which are not fully demonstrated here.
- **Interdisciplinary readership** Moderate. The resource would be of interest to molecular biologists, geneticists, and bioinformaticians. The manuscript is written in a way that is accessible to these groups, but the lack of validation data may limit broader appeal.
- **Technical soundness** The technical implementation of the database is described, but the algorithmic details are incomplete. The validation of the predictions is not presented in this manuscript, which is a significant technical shortcoming.
- **Readability for nonspecialists** The manuscript is generally readable, but the incomplete equations and reliance on a separate publication for algorithm details may hinder understanding for nonspecialists. The use of acronyms (CRM, TFBS, ChIP-seq) is standard for the field.

## Risk / unsupported claims
- The claim of "unprecedentedly complete" collections is not directly supported by data in this manuscript.
- The claim of "highly accurate" predictions is not directly supported by validation data in this manuscript.
- The statement that predictions are "substantially more accurate and more complete than those in existing databases" is not supported by comparative data shown here.
- The claim that mouse predictions are equally accurate as human predictions is unsupported, as validation is stated to be in a separate manuscript in preparation.
- The statement that the database contains "the most comprehensive collections" is a strong claim that requires direct comparison with all existing resources, which is not provided.

## Recommendation posture
Currently not established from the provided evidence. The manuscript describes a potentially useful resource, but the core claims of accuracy and completeness are not substantiated within the text. The authors must provide validation data, comparative benchmarks, and complete algorithmic details before the case for the database's value is established. If these concerns are addressed, the resource could be of significant interest to the community.