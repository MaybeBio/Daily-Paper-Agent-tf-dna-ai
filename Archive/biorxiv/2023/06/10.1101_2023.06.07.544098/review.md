## Review setup
- **Input scope** Full manuscript text (protocol article, bioRxiv preprint)
- **Assessment boundary** Scientific and technical soundness of the protocol as presented; clarity, completeness, and reproducibility of the described methods; alignment with the stated claims of a customizable platform for longitudinal recording of protein-DNA interactions
- **Shared manuscript claim summary** The authors present a comprehensive protocol for the "Calling Cards" platform, a genetically encoded system using piggyBac transposase to permanently record protein-DNA interactions over time in cells and tissues. The protocol covers reagent preparation, delivery (in vitro and in vivo), sample processing, library preparation, sequencing, and data analysis via a new nf-core computational pipeline. The authors claim the platform is customizable for specific transcription factors, works in complex tissues, and offers advantages over snapshot methods like ChIP-seq.
- **Visible evidence base** Abstract; Introduction; Strategic Planning section (design of TF-hyPB fusions, primer selection); Basic Protocols 1-5 (reagents, delivery, sample prep, library prep, sequencing, data analysis); Support Protocol 1 (barcode distribution QC); Commentary (development history, comparisons, limitations); Conflict of Interest, Data Availability, Author Contributions, Internet Resources, Acknowledgments, Footnotes. Figures and tables are referenced but not provided in the supplied material.
- **Missing materials affecting confidence** All figures (including Figure 1 showing data examples, Figure 2 workflow, Figure 3 reagent selection, Figure 4 fusion design, Figure 5 time-course data, Figure 6 library prep overview, Figure 7 qPCR QC, Figure 8 input titration, Figure 9 gel images, Figure 10 saturation analysis) and tables (Table 1 reagents, Table 2 primers, Table 3 method comparison, Table 5 summary metrics) are referenced but not included. Supplemental figures are also not provided. No step-by-step timing annotations for individual steps within protocols are visible. No raw data or example output files are provided.

## Reviewer
- **Overall assessment** This manuscript provides a detailed and thoughtfully structured protocol for a technically sophisticated platform. The authors have clearly invested in optimizing reagents, streamlining workflows, and providing a user-friendly computational pipeline. The writing is generally clear and the rationale for each step is well explained. However, the absence of all figures and tables in the provided material severely limits the ability to assess the validity of the presented data, the clarity of the visual aids, and the reproducibility of the protocol as a standalone resource. The claims regarding the platform's advantages and performance are plausible but cannot be fully verified from the text alone. The protocol appears to be a valuable contribution to the community, but the current evidence base is insufficient for a definitive endorsement.
- **Who would be interested in the results, and why** Researchers studying gene regulation, enhancer biology, transcription factor function, and developmental biology, particularly those interested in linking historical molecular events to cellular phenotypes. The protocol's focus on longitudinal recording and compatibility with complex tissues (e.g., brain) will appeal to neuroscientists and those studying aging or disease models. The detailed computational pipeline will be of interest to bioinformaticians and core facility staff. The method's potential for single-cell applications broadens its appeal to the single-cell genomics community.
- **Major strengths**
    1.  The manuscript addresses a genuine gap in the genomics toolkit by offering a method for cumulative, longitudinal recording of protein-DNA interactions, which is distinct from snapshot methods.
    2.  The protocol is presented in a highly structured, step-by-step format with clear materials lists and QC checkpoints, which is ideal for a methods-focused audience.
    3.  The inclusion of a new, containerized nf-core computational pipeline is a significant strength, as it lowers the barrier to entry for data analysis and promotes standardization.
    4.  The authors provide thoughtful discussion of limitations (e.g., inability to resolve temporal order, low insertions per cell) and practical considerations (e.g., reagent ratios, AAV size constraints), demonstrating a realistic understanding of the method's capabilities.
- **Major Concerns**
    - **R1-M1** (Blocking: Yes)
    - **R1-M2** (Blocking: Yes)
    - **R1-M3** (Blocking: No)
    - **R1-M4** (Blocking: No)
- **Minor Comments**
    - **R1-m1**
    - **R1-m2**
    - **R1-m3**
    - **R1-m4**
    - **R1-m5**
- **Technical failings that need to be addressed before the case is established** The primary technical failing is the lack of verifiable evidence due to missing figures and tables. Specifically, the claims of data quality, reproducibility, and performance (e.g., saturation, peak calling, comparison to ChIP-seq) cannot be assessed. The protocol's reproducibility hinges on the clarity of these visual aids and the completeness of the data tables.
- **Assessment against Nature-style criteria**
    - **Originality:** High. The concept of using a transposase to leave permanent, cumulative marks for longitudinal recording is a creative and distinct approach compared to standard chromatin profiling methods.
    - **Scientific importance:** Potentially high. The ability to correlate past molecular states with current phenotypes addresses a fundamental limitation in genomics and could enable new types of experiments in development and disease.
    - **Interdisciplinary readership:** Moderate. The protocol is primarily of interest to molecular biologists, geneticists, and bioinformaticians. The technical complexity may limit its immediate appeal to a broader interdisciplinary audience, though the potential applications in neuroscience and aging could broaden its reach.
    - **Technical soundness:** Currently unassessable. The written protocol is logical, but the absence of figures and tables prevents evaluation of the data quality, the validity of the QC thresholds, and the performance of the computational pipeline.
    - **Readability for nonspecialists:** Good. The authors do an excellent job of explaining the rationale and concepts in plain language, making the protocol accessible to researchers with basic molecular biology experience, as stated in the abstract.
- **Recommendation posture** Supportive if technical concerns are resolved. The protocol is well-conceived and clearly written, but the manuscript cannot be accepted in its current form without the inclusion and careful review of all referenced figures and tables. The core claims of the platform's utility and performance are not verifiable from the provided text alone.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence integrity and verifiability
- **Claim pointer** The manuscript claims the platform successfully records protein-DNA interactions, with examples shown in Figure 1B-F, and that the protocol is optimized for robust recovery of insertions.
- **Evidence pointer** Figure 1, Figure 5, Figure 7, Figure 9, Figure 10, Table 5 (all "location not provided")
- **Concern** The manuscript relies heavily on figures and tables to substantiate its central claims of functionality, data quality, and reproducibility. None of these are included in the material provided for review. Without seeing the actual data (e.g., insertion maps, QC traces, saturation curves, peak calling results), it is impossible to verify that the protocol performs as described or that the recommended QC thresholds are meaningful. This is a critical omission that prevents a full scientific assessment.
- **Why it matters** The core value of a protocol paper lies in its demonstrated utility and reproducibility. The claims of successful recording, reproducibility across replicates, and data quality are entirely dependent on the visual evidence presented in the figures. The absence of this evidence makes the manuscript's central assertions unverifiable.
- **Resolution test** The authors must provide all referenced figures and tables. The reviewer must be able to inspect the data to confirm that the platform generates specific, reproducible signals, that the QC metrics are appropriate, and that the computational pipeline produces sensible outputs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and protocol completeness
- **Claim pointer** The protocol claims to be a comprehensive guide enabling users with basic molecular biology experience to process samples into sequencing libraries in 1-2 days.
- **Evidence pointer** Basic Protocols 1-5, Strategic Planning (all "location not provided")
- **Concern** While the step-by-step instructions are detailed, the protocol lacks specific quantitative details for several critical steps. For example, the amount of starting material (cells or tissue) is not specified in the provided text. The number of PCR cycles is stated to require optimization, but no starting point or range is given. The density of AAV injection is given as a concentration, but the total volume and number of viral particles per injection are not clearly stated. These omissions make it difficult for a user to perform the protocol without significant trial and error, contradicting the claim of a streamlined, accessible guide.
- **Why it matters** A protocol's primary purpose is to be reproducible by others. Missing critical parameters, such as input amounts and reaction conditions, directly undermines this goal and forces users to engage in costly and time-consuming optimization, which is contrary to the stated aim of the manuscript.
- **Resolution test** The authors should provide a table or clearly state in the text the recommended starting amounts of cells/tissue, the recommended range for PCR cycle numbers, and the exact injection parameters (volume, titer, number of sites) for the in vivo protocol. The protocol should be self-contained enough for a competent researcher to execute without needing to contact the authors for missing information.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Validation and comparative performance
- **Claim pointer** The manuscript states that "in test cases examined so far, Calling Cards data is concordant with ChIP-seq data" and implies the method is a viable alternative or complement.
- **Evidence pointer** Commentary section, "location not provided"
- **Concern** The claim of concordance with ChIP-seq is made without presenting the comparative data. The manuscript does not provide a systematic or quantitative comparison (e.g., overlap statistics, correlation coefficients) between Calling Cards and ChIP-seq datasets. The single example mentioned is not sufficient to establish the general validity of this claim.
- **Why it matters** For a new method to be adopted, its performance must be benchmarked against established techniques. A vague statement of concordance is insufficient. The community needs to see a rigorous comparison to understand the strengths, weaknesses, and specific use cases where Calling Cards is most appropriate.
- **Resolution test** The authors should include a figure or table that directly compares Calling Cards and ChIP-seq data for the same TF and cell type, including quantitative metrics of overlap and a discussion of any discrepancies. This would provide the necessary evidence to support the claim of concordance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data analysis pipeline validation
- **Claim pointer** The manuscript introduces a new nf-core computational pipeline for processing Calling Cards data and claims it is ready for use.
- **Evidence pointer** Basic Protocol 5, "location not provided"
- **Concern** The description of the pipeline is high-level. There is no information on how the pipeline was validated, what the expected runtime and resource requirements are, or how the output compares to the previous, non-pipeline version of the analysis tools. The manuscript mentions a "newly deployed computational pipeline" but does not provide evidence of its accuracy or robustness.
- **Why it matters** A computational pipeline is a critical component of the workflow. If it is not thoroughly tested and validated, it can produce erroneous results. Users need to have confidence in the pipeline's output before they can rely on it for their own data analysis.
- **Resolution test** The authors should provide details on the pipeline's test datasets, validation results (e.g., comparison to a gold standard or previous methods), and performance benchmarks. A link to a publicly available test dataset and expected outputs would be highly beneficial.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and consistency
- **Affected element** Protocol structure and timing
- **Evidence pointer** Basic Protocols 1-5, "location not provided"
- **Issue** The "timing" annotations are only provided at the protocol level (e.g., "1 hr", "variable"), not for individual steps. This makes it difficult for users to plan their time and identify potential bottlenecks.
- **Required correction** Add estimated timings for each major step within the protocols, as is common in other methods journals (e.g., "30 min", "overnight").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Reagent details
- **Evidence pointer** Basic Protocol 1, Materials section, "location not provided"
- **Issue** The protocol refers to a "complete list" of plasmids in Table 1, but the table is not provided. It is unclear if all plasmids are available from Addgene and if the specific catalog numbers are listed.
- **Required correction** Ensure Table 1 is included and contains all necessary details, including Addgene catalog numbers, for each plasmid.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data analysis
- **Affected element** Peak calling parameters
- **Evidence pointer** Basic Protocol 5, "location not provided"
- **Issue** The description of the peak calling step is brief. It mentions CCcaller and Blockify but does not specify the default parameters or how to choose between them.
- **Required correction** Provide a brief description of the default parameters for each peak caller and guidance on when one might be preferred over the other.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Example dataset
- **Evidence pointer** Data Availability Statement, "location not provided"
- **Issue** The manuscript mentions a "vignette" with data for benchmarking, but the accession number (GSE223926) is only mentioned in the Data Availability Statement. It would be helpful to also reference this in the main text where the vignette is discussed.
- **Required correction** Add a reference to the GEO accession number in the section describing the illustrative vignette.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Terminology
- **Evidence pointer** Introduction, "location not provided"
- **Issue** The term "Calling Cards" is used throughout, but the concept of a "cumulative record" could be clarified further for readers unfamiliar with the method. The distinction between this and a simple "snapshot" is made, but a more explicit explanation of the "integration" event would be helpful.
- **Required correction** Add a sentence in the introduction explicitly stating that the transposase integrates the reporter construct into the genome, and that this integration event is the "call" that is later read out.

## Risk / unsupported claims
- The claim that "Calling Cards data is concordant with ChIP-seq data" is unsupported by the provided evidence, as no comparative data is shown.
- The claim that the protocol is optimized for "robust recovery of insertions" is unverifiable without the data in Figure 5, Figure 7, and Figure 9.
- The claim that the new computational pipeline is ready for use is unverifiable without details on its validation and testing.
- The claim that the platform can be "adapted to profile specific transcription factor binding" is plausible but the success rate and generalizability of this adaptation are not quantified in the provided text.
- The claim that the protocol can be completed in "1-2 days" is not verifiable without the timing annotations for individual steps.