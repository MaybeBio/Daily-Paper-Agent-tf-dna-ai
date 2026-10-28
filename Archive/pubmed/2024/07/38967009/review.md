## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, conclusion, data availability)
- **Assessment boundary** Technical soundness of the knowledge graph schema, data integration methodology, query capabilities, and biological utility claims
- **Shared manuscript claim summary** The authors present a knowledge graph-based framework using RDF/SPARQL to integrate 25 enhancer databases and 2 TAD databases with the BioGateway knowledge network, enabling combined functional and location-based queries about gene regulation
- **Visible evidence base** Abstract, full methods, results sections, tables referenced (Tables 1-4), figures referenced (Figures 1-9), supplementary material descriptions
- **Missing materials affecting confidence** Actual SPARQL query code, query results data, supplementary figures and tables, GitHub repository contents, endpoint availability verification

## Reviewer
- **Overall assessment** The manuscript addresses a genuine and important problem in genomics data integration: the lack of interoperable, queryable resources that combine functional annotations with genomic location data for enhancers and TADs. The authors have undertaken a substantial data integration effort, processing 27 databases into a standardized RDF format. The schema design is thoughtful, reusing existing ontologies and linking to the Biolink Model. However, the manuscript has several significant weaknesses. The evaluation is limited to three use cases that are described at a high level without presenting actual query results or demonstrating that the queries produce biologically meaningful output. The claim that this is "the most powerful integrative resource in this field to date" is not substantiated with comparative benchmarks against existing resources like GenomicKB. The technical details of the data processing pipeline, particularly the mapping of non-standard terms to ontologies, are described only superficially. The manuscript would benefit from a more rigorous evaluation framework, including query performance metrics, comparison with existing resources, and validation of the biological findings from the use cases.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulation, particularly those interested in knowledge graph approaches for integrating heterogeneous genomics data. Researchers studying enhancer biology, chromatin organization, and gene regulatory networks would find the integrated resource valuable for hypothesis generation. The work is also relevant to the semantic web and biomedical ontology community, as it demonstrates practical application of RDF/SPARQL for genomics data integration and contributes to the Gene Regulation Knowledge Commons initiative.

- **Major strengths**
  1. Addresses a real and pressing need for standardized, interoperable representation of enhancer and TAD data
  2. Substantial data integration effort covering 27 databases with detailed provenance tracking
  3. Thoughtful schema design that reuses existing ontologies and connects to the Biolink Model
  4. Open access implementation with SPARQL endpoint, web tool, and code repository
  5. The use case approach demonstrates practical applications of the resource

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "We demonstrate its use in a set of advanced queries (three use cases) that until now were not efficiently possible"
- **Evidence pointer** Results section "Queries", Figures 7-9, Supplementary Figures S8-S9
- **Concern** The three use cases are described only at a conceptual level. The manuscript does not present the actual SPARQL queries, the results obtained, or an analysis of what those results mean biologically. For example, the rs4784227 mutation analysis is mentioned but no results are shown. Without concrete query examples and results, the reader cannot evaluate whether the resource actually delivers on its promise of enabling "versatile queries" and "new hypotheses."
- **Why it matters** The central claim of the paper is that this knowledge graph enables novel types of queries. This claim cannot be assessed without seeing the queries and their outputs. The use cases are the primary evidence for the utility of the resource, and their absence undermines the paper's main contribution.
- **Resolution test** Provide the full SPARQL queries for each use case, the results obtained (including number of hits and example entries), and a brief biological interpretation of the findings. Ideally, include a comparison with what would be required to obtain the same information using existing resources.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative analysis
- **Claim pointer** "creating the most powerful integrative resource in this field to date"
- **Evidence pointer** Discussion section, Introduction section
- **Concern** The claim of being "the most powerful integrative resource" is made without any comparative evaluation against existing resources. The authors mention GenomicKB as an alternative approach but do not provide a systematic comparison of coverage, query capabilities, performance, or usability. The statement in the Discussion that "we believe that our BGW resource offers several advantages" is presented as opinion rather than demonstrated through evidence.
- **Why it matters** Without a comparative analysis, the reader cannot assess whether this resource represents a genuine advance over existing tools or merely a different implementation. The claim of superiority needs to be supported with data on coverage, query performance, and feature comparison.
- **Resolution test** Provide a systematic comparison with GenomicKB and potentially other relevant resources (e.g., ENCODE, Ensembl Regulation) covering: number of enhancers covered, overlap with existing annotations, query response times, types of queries supported, and unique capabilities. Present this as a table or figure with quantitative metrics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation
- **Claim pointer** "The data processing method included four steps: data collection, data pre-processing, RDF file generation, file loading, and graph generation"
- **Evidence pointer** Materials and methods section "The data integration method", Figure 5
- **Concern** The data processing pipeline is described at a high level, but critical details are missing. The manuscript states that "a manual mapping had to be carried out" for ontology terms but does not describe the extent of this manual effort, the criteria used for mapping decisions, or the potential for errors. The remapping of coordinates to hg38 is mentioned but the methodology (e.g., liftOver parameters, handling of multi-mapping regions) is not described. The quality control measures for the integrated data are not specified.
- **Why it matters** The reliability of the knowledge graph depends entirely on the quality of the data integration. Without details on the mapping methodology, quality control, and error rates, users cannot assess the confidence they should place in query results. This is particularly important for clinical or hypothesis-generating applications.
- **Resolution test** Provide detailed methodology for the coordinate remapping (including software, parameters, and handling of ambiguous mappings), describe the manual ontology mapping process (including inter-annotator agreement if multiple annotators were used), and report quality metrics such as the proportion of sequences successfully mapped and the proportion of ontology terms that required manual mapping.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "All the generated code, a SPARQL tutorial to facilitate the use of the BGW knowledge network, as well as the use case queries and the results obtained are available in a repository generated for this purpose"
- **Evidence pointer** Data availability section, GitHub repository link
- **Concern** The manuscript states that code and data are available in a GitHub repository and Zenodo, but the actual contents of these resources are not described. The reader cannot verify that the repository contains the necessary code, data, and documentation to reproduce the work. The SPARQL endpoint is mentioned but its availability and stability are not discussed.
- **Why it matters** Reproducibility is a core requirement for scientific publications. Without verification that the repository is complete and functional, the work cannot be independently validated or built upon by other researchers.
- **Resolution test** Describe the repository structure, list the key files and their purposes, provide a quick-start guide for reproducing the data integration, and confirm the endpoint is publicly accessible. Consider providing a Docker container or virtual machine image for easy reproduction.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract section
- **Issue** The abstract states "we exploit these location and functional aspects together to develop new strategies to enable advanced data querying" but does not give a concrete example of what makes these queries "advanced" or "versatile." The abstract would benefit from one specific example of a query type that is now possible.
- **Required correction** Add one sentence in the abstract with a concrete example of a query that combines location and functional constraints, such as "for example, identifying all enhancers within a specified genomic distance of genes associated with a given disease."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Table 3
- **Evidence pointer** Table 3, Materials and methods section
- **Issue** Table 3 lists the databases used but does not include the version or download date for each database. This information is critical for reproducibility and for understanding the temporal coverage of the data.
- **Required correction** Add columns to Table 3 indicating the version and download date for each database.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Query performance
- **Evidence pointer** Supplementary Table S9, Results section
- **Issue** The manuscript mentions execution times of queries in Supplementary Table S9 but does not discuss these in the main text. Query performance is an important practical consideration for users.
- **Required correction** Add a brief discussion of query performance in the Results or Discussion section, including typical response times and any optimization strategies employed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Biological validation
- **Affected element** Use case 3
- **Evidence pointer** Results section "Queries", Figure 9
- **Issue** The third use case claims to provide "a biologically relevant and novel dataset" but the biological significance of the results is not discussed. The manuscript does not explain why the identified molecular contributors to diseases are novel or important.
- **Required correction** Provide a brief biological interpretation of the results from use case 3, highlighting any novel findings or hypotheses generated.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction section, Discussion section
- **Issue** The terms "enhancer" and "CRM" (cis-regulatory module) are used somewhat interchangeably. While the authors note that enhancers are the most studied type of CRM, the distinction could be made clearer throughout the manuscript.
- **Required correction** Define the relationship between enhancers and CRMs early in the manuscript and use terminology consistently throughout.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** SPARQL endpoint
- **Evidence pointer** Data availability section
- **Issue** The SPARQL endpoint URL is provided, but there is no information about usage limits, authentication requirements, or service level guarantees. This is important for researchers planning to use the resource.
- **Required correction** Add a brief statement about endpoint accessibility, including any usage policies or contact information for support.

## Risk / unsupported claims
- The claim that BGW is "the most powerful integrative resource in this field to date" is unsupported by comparative analysis
- The claim that the use cases demonstrate queries "that until now were not efficiently possible" is not substantiated with actual query results or comparison to alternative approaches
- The statement that the knowledge graph "enables the development of new hypotheses" is plausible but not demonstrated with concrete examples of novel biological insights
- The assertion that the resource "offers several advantages" over GenomicKB is presented as opinion without supporting evidence
- The claim that the schema "facilitates the inclusion of new relationships" and is "open to future extensions" is not tested or demonstrated
- The statement that the resource "represents another step forward towards the knowledge commons for gene regulation" is aspirational and not directly supported by the presented work