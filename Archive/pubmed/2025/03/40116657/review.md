## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusion, methods, and supplementary references) as provided.
- **Assessment boundary** Scientific and technical evaluation of the MOSim simulator's design, validation, and claims, based solely on the supplied text. No external code, figures, or supplementary files were accessed.
- **Shared manuscript claim summary** The authors present MOSim, an R/Bioconductor package for simulating bulk and single-cell multilayer regulatory networks, generating count matrices for transcriptomics and associated regulatory omics (e.g., ATAC-seq, miRNA-seq, ChIP-seq, methylation, transcription factors) with user-defined experimental designs, differential expression, and regulatory relationships, intended for benchmarking multi-omics integration and GRN inference tools.
- **Visible evidence base** Abstract; Introduction; Results sections on workflows, bulk and single-cell validation, multilayered GRN simulation, benchmarking with MORE, and benchmarking with scDHA; Discussion; Conclusion; Methods; Data availability; Author contributions; Funding.
- **Missing materials affecting confidence** Supplementary File 1 (detailed algorithm implementation), all figures (Figures 1–4), all tables (Tables 1–4), the actual R package code, and the GitHub repository contents. These are referenced but not provided, limiting verification of algorithmic details, quantitative results, and reproducibility.

## Reviewer
- **Overall assessment** The manuscript describes a timely and potentially useful tool for simulating multi-omics data with regulatory relationships, addressing a genuine gap in benchmarking resources. The conceptual design is sound, and the authors demonstrate applications with two benchmarking examples. However, the provided text lacks sufficient quantitative detail and access to key validation results (figures, tables, supplementary algorithms) to fully assess technical soundness and reproducibility. The claims of realism and utility are plausible but not fully established from the supplied material alone.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or benchmarking multi-omics integration methods, GRN inference algorithms, and single-cell analysis pipelines. The tool's ability to generate ground-truth data with known regulatory relationships is directly relevant for method validation and comparison studies.
- **Major strengths** 1) Addresses a clear need for simulation tools that model regulatory relationships across multiple omics layers, which is underexplored. 2) Supports both bulk and single-cell data in one package, offering flexibility. 3) Uses real datasets as seeds, potentially enhancing realism over purely synthetic generators. 4) Provides user control over experimental design, differential expression, and regulatory effects. 5) Demonstrates practical utility through benchmarking with MORE and scDHA.
- **Major Concerns** 
  - R1-M1: Insufficient algorithmic detail in the main text to evaluate the simulation methodology.
  - R1-M2: Validation metrics are reported without full context or statistical rigor.
  - R1-M3: The benchmarking demonstrations are limited in scope and do not compare against existing simulators.
  - R1-M4: The claim of "realistic" data generation is not quantitatively supported.
- **Minor Comments** 
  - R1-m1: The term "multilayer" is used but not formally defined in the context of the simulator.
  - R1-m2: The relationship between the seed data and the simulated output is not fully explained.
  - R1-m3: The choice of validation metrics (e.g., correlation thresholds) is not justified.
  - R1-m4: The Discussion mentions limitations but does not address potential biases in the simulation approach.
- **Technical failings that need to be addressed before the case is established** R1-M1 (algorithmic detail), R1-M2 (validation rigor), R1-M4 (realism claim).
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The concept of multi-omics simulation with regulatory relationships is not entirely new, but the combination of bulk and single-cell in one tool with user-defined GRNs is a useful contribution.
  - Scientific importance: Moderate to high. Benchmarking tools are essential for advancing method development, and a reliable simulator could have broad impact.
  - Interdisciplinary readership: Moderate. The tool is relevant to bioinformatics, genomics, and systems biology, but the manuscript is written for a specialized audience.
  - Technical soundness: Not fully assessable from the provided text. The algorithmic details are deferred to supplementary materials, and validation metrics lack statistical context.
  - Readability for nonspecialists: Acceptable. The text is clear but assumes familiarity with omics data types and simulation concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is valuable, but the manuscript must provide sufficient algorithmic detail, rigorous validation, and comparative analysis to establish the tool's credibility and utility.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that MOSim "simulates both bulk and single-cell multi-omics data" with precise control over regulatory relationships, but the main text only provides a high-level workflow description.
- **Evidence pointer** Results sections "Bulk multi-omic GRNs: the mosim functionality" and "Single-cell multi-omic GRNs: the sc_mosim functionality"; algorithm details deferred to "Supplementary File 1" (location not provided).
- **Concern** The core algorithms for both mosim and sc_mosim are not described in the main text. The sections listing workflow steps are incomplete, and the reader is referred to a supplementary file that is not available for review. Without a clear explanation of how the simulation parameters are derived from the seed data, how regulatory relationships are modeled, and how noise is introduced, the technical validity of the approach cannot be assessed.
- **Why it matters** The manuscript's primary contribution is a simulation tool. If the underlying methodology is not transparent and reproducible, the tool cannot be trusted for benchmarking purposes, and the scientific claims are unverifiable.
- **Resolution test** Provide a detailed algorithmic description in the main text or ensure the supplementary file is accessible and contains complete mathematical formulations, pseudocode, and parameter estimation procedures.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The validation sections report specific metrics, e.g., "99.4% of interactions with a modelled activator or repressor effect displayed a correlation value >0.9" and "3.3% of simulated profiles assigned to an incorrect cluster," but these are presented without statistical uncertainty or comparison to null expectations.
- **Evidence pointer** Results sections "Validation of the bulk (mosim) simulation approach" and "Validation of the single-cell (sc_mosim) simulation approach"; figures and tables referenced but not provided.
- **Concern** The validation metrics are reported as point estimates without confidence intervals, standard errors, or statistical tests. For example, the correlation threshold of 0.9 is arbitrary, and the "incorrect cluster" rate of 3.3% is not compared to a baseline or alternative methods. The PCA plots are described qualitatively but not shown. This limits the ability to judge whether the simulation performs well or merely adequately.
- **Why it matters** Benchmarking tools must demonstrate robust performance with rigorous statistical evidence. Without such evidence, the claims of "realistic" and "diverse" data generation are not substantiated.
- **Resolution test** Include statistical analyses (e.g., confidence intervals, permutation tests) for all reported metrics, provide the actual figures and tables, and compare performance against existing simulators or null models.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript states that MOSim fills a gap in multi-omics simulation, but the benchmarking demonstrations only test with MORE and scDHA, without comparing to other simulators like InterSIM, OmicsSIMLA, or sismonr.
- **Evidence pointer** Results sections "Application of MOSim for benchmarking a GRN inference tool" and "Benchmarking scMOSim's scRNA-Seq simulations using a deep learning algorithm"; Discussion mentions existing tools but no direct comparison.
- **Concern** The utility of MOSim is demonstrated through two specific applications, but no comparative benchmarking against existing simulators is provided. This makes it difficult to assess whether MOSim offers advantages over current tools, as claimed in the Introduction.
- **Why it matters** For a tool to be adopted, it must demonstrate clear benefits over alternatives. Without comparative analysis, the claim of filling a "critical gap" is not fully supported.
- **Resolution test** Add a comparative study where MOSim and existing simulators are used to generate data for the same benchmarking tasks, with quantitative performance metrics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims MOSim generates "realistic" data, but this is not quantitatively defined or validated against real datasets.
- **Evidence pointer** Abstract and Discussion; validation sections use clustering and correlation metrics but do not compare simulated data to real data distributions.
- **Concern** The term "realistic" is used repeatedly, but no formal comparison is made between simulated and real data (e.g., distributional similarity, feature-level concordance). The validation only checks internal consistency (e.g., profiles match expected patterns), not external realism.
- **Why it matters** If the simulated data do not resemble real data, benchmarking results may not generalize to actual applications. The claim of realism is central to the tool's value proposition.
- **Resolution test** Perform a systematic comparison of simulated data against real datasets (e.g., STATegra, pbmc.multiome) using metrics like gene expression distribution, dropout rates, and regulatory relationship recovery.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Throughout the manuscript
- **Issue** The term "multilayer" is used to describe the regulatory networks, but it is not formally defined. It is unclear whether it refers to multiple omics types, multiple regulatory layers (e.g., TF, miRNA, methylation), or both.
- **Required correction** Provide a clear definition of "multilayer" in the context of the simulator, and use consistent terminology throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Seed data handling
- **Evidence pointer** Results section "Overview of MOSim's workflows"
- **Issue** The manuscript states that MOSim requires a "single sample of seed count data" for each omics type, but it is unclear how the seed data are used to infer distributions and whether the choice of seed data significantly affects the simulation output.
- **Required correction** Clarify the role of seed data in the simulation process and discuss the sensitivity of results to different seed datasets.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Validation metrics
- **Evidence pointer** Results sections on validation
- **Issue** The choice of correlation thresholds (e.g., >0.9 for bulk, >0.7 for single-cell) is not justified. It is unclear why different thresholds are used for different data types.
- **Required correction** Provide a rationale for the chosen thresholds, or use a more principled approach (e.g., ROC curves, effect sizes).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion mentions limitations but does not address potential biases in the simulation approach, such as the reliance on user-provided association files or the assumption of linear regulatory relationships.
- **Required correction** Expand the Discussion to explicitly acknowledge these limitations and their potential impact on benchmarking results.

## Risk / unsupported claims
- The claim that MOSim generates "realistic" data is unsupported without quantitative comparison to real datasets.
- The claim that MOSim fills a "critical gap" is not fully supported without comparative benchmarking against existing simulators.
- The specific performance metrics (e.g., 99.4% correlation, 3.3% misclassification) are unverifiable without access to the referenced figures and tables.
- The algorithmic details of both mosim and sc_mosim are not assessable from the provided text, as they are deferred to a supplementary file that was not supplied.
- The statement that "several tools have already been tested using MOSim simulations" (listing DEGRE, scAI, JISAE, GR-NIC, scLRTD) is not verifiable from the provided material, as no citations or details are given.