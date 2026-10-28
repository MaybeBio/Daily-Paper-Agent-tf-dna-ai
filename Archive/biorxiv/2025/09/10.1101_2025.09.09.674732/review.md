## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2025-09-15, DOI 10.1101/2025.09.09.674732)
- **Assessment boundary** Scientific and technical claims as presented in the manuscript text, including the Summary, Introduction, Materials and Methods, and Conclusion sections. No supplementary files, figures, tables, or code repositories were provided for inspection.
- **Shared manuscript claim summary** The authors present SMTrackR, an R/Bioconductor package that queries BigBed files hosted on a Galaxy server via the UCSC REST API to visualize and quantify protein-DNA binding states (protein-free, TF-bound, histone-bound) on individual DNA molecules from NOMe-seq, dSMF, and Nanopore (SMAC-seq) datasets. The package generates footprint heatmaps, reports occupancies, and produces Gviz-compatible scripts for gene track visualization. The authors also claim that a substantial fraction of in silico GpC footprints in mammalian genomes are short enough to report TF binding, and they provide compiled TF motif lists and in silico footprint files.
- **Visible evidence base** Manuscript text only. No figures, tables, supplementary materials, code, or data files were accessible for verification.
- **Missing materials affecting confidence** All figures (Figure 1, S1-S4), Supplementary Tables 1-2, the SMTHub database contents, the SMTrackR package source code, the web server implementation, and the snakemake pipelines. Without these, the functional claims, performance, and usability of the package cannot be independently assessed.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful software tool for a niche but growing community studying single-molecule protein-DNA binding. The concept of separating the database (SMTHub) from the front-end (SMTrackR) and using the UCSC REST API is reasonable and could lower the barrier for non-specialists. However, the manuscript as written is a brief software note with limited methodological detail. The core claims about functionality, data coverage, and the biological utility of the GpC footprint analysis are not verifiable from the provided text alone. The lack of any performance benchmarks, validation against existing tools, or demonstration on real biological questions weakens the case for broad adoption. The manuscript would benefit from a more complete description of the package architecture, a clear validation strategy, and a demonstration of the tool's utility on a concrete biological example.
- **Who would be interested in the results, and why** Researchers working on gene regulation, chromatin biology, and epigenomics, particularly those using single-molecule footprinting assays (NOMe-seq, dSMF, SMAC-seq, Fiber-seq). The tool could also be of interest to bioinformaticians and computational biologists seeking user-friendly visualization solutions for large-scale methylation-based footprint data. The web server version may appeal to experimentalists without strong programming backgrounds.
- **Major strengths** The tool addresses a real gap in the field, as no user-friendly interface currently exists for visualizing and quantifying single-molecule footprint data. The design choice to separate the database from the front-end and to leverage the UCSC REST API is pragmatic and could facilitate interoperability. The inclusion of a web server version and support for local BigBed files increases accessibility. The authors also provide pipelines for generating BigBed files, which is helpful for users with unpublished data.
- **Major Concerns** The manuscript lacks sufficient detail to evaluate the package's functionality, robustness, and biological utility. The claims about the SMTHub database (coverage, data sources, processing) are not substantiated. The biological claim about GpC footprint suitability for TF mapping is based on in silico analysis only, with no experimental validation. The package's performance (speed, memory, scalability) is not reported. No comparison with existing tools (e.g., other footprint visualization packages) is provided. The manuscript does not demonstrate the tool on a real dataset to show its practical value.
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide a clear description of the data processing pipeline used to generate the SMTHub BigBed files, including quality control steps, alignment parameters, and footprint calling thresholds. The criteria for assigning binding states (protein-free, TF-bound, histone-bound) are referenced to a previous publication but not summarized here, making the manuscript not self-contained. The claim about the "remove_dup" flag and its effect on pseudo-bulk data is not explained. The in silico GpC footprint analysis is described only in general terms, with no details on the genomic annotation used or the statistical significance of the overlap with ChromHMM states.
- **Assessment against Nature-style criteria** Originality: Moderate. The concept of a user-friendly front-end for single-molecule footprint data is not entirely new, but the specific combination of a centralized database and an R package is a useful contribution. Scientific importance: Moderate. The tool could facilitate wider use of single-molecule footprinting data, but the manuscript does not demonstrate a new biological insight or a significant methodological advance. Interdisciplinary readership: Limited. The tool is primarily for a specialized audience in epigenomics and computational biology. Technical soundness: Not assessable from the provided text. The core functionality is described at a high level, and no code, tests, or benchmarks are provided. Readability for nonspecialists: The manuscript is written in a clear and concise style, but the lack of figures and detailed methods makes it difficult for a non-specialist to understand the tool's capabilities and limitations.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript describes a potentially useful tool, but the claims are not verifiable without access to the code, data, and supplementary materials. The authors should provide a more detailed description of the package, a validation on real data, and a comparison with existing tools.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that SMTrackR "queries the single-molecule footprint database we built and hosted at Galaxy Server" and "plots footprint heatmap categorized in different binding states as well as report their occupancies."
- **Evidence pointer** Section 2.2, "SMTrackR"; location not provided
- **Concern** The manuscript does not provide any details on the implementation of the package, such as the functions, their arguments, the data structures used, or the error handling. The description of the querying process is limited to "queries BigBed files hosted at Galaxy using USCS REST API" and "retrieved JSON file is processed." No information is given on how the package handles large genomic regions, multiple samples, or missing data. The claim that the package "uniquely maps BigBed file with other relevant information" is not explained.
- **Why it matters** Without a clear description of the package's architecture and functionality, it is impossible for a potential user to assess whether the tool is suitable for their needs, how to install and use it, or how to troubleshoot issues. The lack of technical detail also prevents an independent evaluation of the correctness and robustness of the code.
- **Resolution test** The authors should provide a detailed description of the package's functions, their inputs and outputs, and the underlying data processing steps. A link to the package documentation (e.g., Bioconductor vignette) and a demonstration of the package on a sample dataset would be essential.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability and reproducibility
- **Claim pointer** The manuscript claims that the SMTHub database contains "BigBed files generated from NOMe-seq, dSMF, and Nanopore (SMAC-seq) datasets" and that it was built from "massive sequence analysis on NOMe-seq and dSMF data (∼1TB) from several studies."
- **Evidence pointer** Section 2.1, "SMTHub"; location not provided
- **Concern** The manuscript does not list the specific datasets used to build the SMTHub, the number of samples, the organisms, or the cell types covered. The processing pipeline is described only as "massive sequence analysis" with a reference to a previous publication. The criteria for merging biological replicates and generating pseudo-bulk data are not detailed. The quality of the footprint calls is not assessed.
- **Why it matters** The utility of the SMTrackR package depends entirely on the quality and coverage of the underlying SMTHub database. Without a clear description of the data sources and processing steps, users cannot trust the results obtained from the database. The lack of reproducibility also prevents other researchers from extending or updating the database.
- **Resolution test** The authors should provide a table listing all datasets used, including accession numbers, organisms, cell types, and sequencing depths. A detailed description of the processing pipeline, including software versions and parameters, should be included. The quality of the footprint calls should be assessed, for example, by comparing with known binding sites.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance and validation
- **Claim pointer** The manuscript claims that "about 35 percent (37,679,878 of 107,792,112) are less than 45 base pairs long, and overlaps with regulatory element characterized by ChromHMM" for in silico GpC footprints in mammalian genomes.
- **Evidence pointer** Section 2.3, "Sub-genome suitable for TF footprinting with NOMe-seq"; location not provided
- **Concern** This is a key biological claim that supports the utility of NOMe-seq for TF footprinting. However, the analysis is described only in a single sentence, with no details on the methods used to define in silico footprints, the genomic annotation used, or the statistical significance of the overlap with ChromHMM states. The claim is not validated experimentally, for example, by showing that the predicted TF binding sites are actually occupied in vivo.
- **Why it matters** If this claim is not robust, the main motivation for using NOMe-seq for TF footprinting is weakened. The lack of detail makes it impossible to reproduce the analysis or to assess its validity.
- **Resolution test** The authors should provide a detailed description of the in silico footprint analysis, including the definition of footprints, the genomic regions analyzed, and the statistical methods used. The overlap with ChromHMM states should be quantified with appropriate statistical tests. Ideally, the authors should validate the claim by showing that known TF binding sites with GpC in their motifs are indeed protected from methylation in NOMe-seq data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership and usability
- **Claim pointer** The manuscript claims that SMTrackR is a "user-friendly tool" and that the web server version is available.
- **Evidence pointer** Summary and Section 1, "Introduction"; location not provided
- **Concern** The manuscript does not provide any evidence of usability, such as a tutorial, a demonstration on a real dataset, or feedback from users. The web server is mentioned but not described in terms of its interface, features, or limitations. The claim of "user-friendly" is subjective and not supported by any data.
- **Why it matters** The tool is intended for a broad audience, including experimentalists who may not be familiar with R. Without a clear demonstration of its usability, it is unclear whether the tool will be adopted by the target community.
- **Resolution test** The authors should provide a step-by-step tutorial with screenshots or a video demonstrating the use of the package and the web server on a real dataset. They should also report on the performance of the web server, including response times and any usage limits.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Section 2.2, "SMTrackR"
- **Evidence pointer** location not provided
- **Issue** The manuscript states that the package "uniquely maps BigBed file with other relevant information like organism of interest, cell-type, conditions etc." but does not explain how this mapping is achieved or stored.
- **Required correction** Provide a brief description of the metadata structure used to map BigBed files to their associated information.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.1, "SMTHub"
- **Evidence pointer** location not provided
- **Issue** The manuscript mentions "minor changes to adapt the NOMe-seq data with this protocol" but does not specify what these changes were.
- **Required correction** List the specific modifications made to the original protocol for NOMe-seq data processing.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.2, "SMTrackR"
- **Evidence pointer** location not provided
- **Issue** The manuscript states that the package "uses base R functions to plot the heatmap" but does not mention any dependencies on other R packages (e.g., for data manipulation or visualization).
- **Required correction** Provide a list of all R package dependencies and their versions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3, "Sub-genome suitable for TF footprinting with NOMe-seq"
- **Evidence pointer** location not provided
- **Issue** The manuscript states that "a good number of molecules mapped to region of interest" is recommended but does not provide any quantitative guidance.
- **Required correction** Provide a minimum recommended number of molecules or a statistical framework for determining adequate coverage.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3, "Conclusion"
- **Evidence pointer** location not provided
- **Issue** The manuscript mentions that the tool "covers deeply sequenced dSMF data from Drosophila melanogaster S2 cells" but does not specify the number of datasets or the sequencing depth.
- **Required correction** Provide a summary of the dSMF datasets included in the SMTHub, including the number of samples and their coverage.

## Risk / unsupported claims
- The claim that SMTrackR is "user-friendly" is subjective and not supported by any usability study or demonstration.
- The claim that the SMTHub database is comprehensive and reliable is not supported by a detailed description of the data sources and processing pipeline.
- The claim that NOMe-seq can reliably map TF-bound states at a substantial fraction of genomic loci is based on an in silico analysis that is not described in sufficient detail and is not experimentally validated.
- The claim that the tool "enables this by mapping all binding states at single-molecule resolution in vivo" is not demonstrated on a real biological example.
- The performance and scalability of the package (e.g., speed, memory usage) are not reported.
- The compatibility of the package with different operating systems and R versions is not stated.