## Review setup

- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion) from bioRxiv preprint
- **Assessment boundary** Scientific validity, methodological soundness, evidence quality, and clarity of claims as presented in the provided text
- **Shared manuscript claim summary** The authors present HiddenFoot, a biophysical modeling framework based on statistical mechanics, to infer transcription factor, nucleosome, and RNA Polymerase II occupancy on single DNA molecules from methylation-based footprinting data (SMF and Fiber-seq). They claim the method recovers known TF footprints, resolves Pol II pausing, distinguishes direct TF–TF cooperativity from nucleosome-mediated effects, and reveals nucleosome heterogeneity across diverse organisms and assay platforms.
- **Visible evidence base** Results sections describe analyses of mESC SMF data (246 amplicons, 258 JASPAR PWMs), HeLa HIV-1 reporter SMF data, and Drosophila S2 Fiber-seq data. Validation includes comparisons to ChIP-seq, MNase-seq, and ATAC-seq. Figures referenced: Fig. 1, Fig. 2, Fig. 3, Fig. 4, Fig. 5, Supplementary Figs. S1–S6, Supplementary Table 1.
- **Missing materials affecting confidence** Figures and supplementary materials are referenced but not provided in the submitted text. Specific numerical results (correlation coefficients, effect sizes, statistical tests) are only partially reported. Details of data preprocessing, parameter initialization, and convergence diagnostics for SGD and MCMC are not fully described. No comparison to existing tools (e.g., FootprintCharter, FiberHMM) is presented in the text.

## Reviewer

- **Overall assessment** The manuscript presents a conceptually appealing and technically ambitious framework that addresses a real gap in single-molecule chromatin accessibility analysis. The integration of statistical mechanics with probabilistic inference is a sensible and potentially powerful approach. However, the evidence as presented in the text is insufficient to fully evaluate the method's performance, robustness, and novelty relative to existing tools. Several claims, particularly regarding the distinction of direct versus indirect TF cooperativity and the biological significance of inferred interaction energies, require stronger validation and clearer reporting of quantitative results. The writing is generally clear but contains some typographical and grammatical errors that should be corrected.

- **Who would be interested in the results, and why** Researchers in gene regulation, chromatin biology, and computational biology would be interested. Specifically, those working on single-molecule footprinting assays, transcription factor binding dynamics, nucleosome positioning, and the development of probabilistic models for genomic data would find this framework relevant. The potential to extract mechanistic insights from sparse single-molecule data could appeal to a broad audience interested in regulatory genomics.

- **Major strengths**
  1. The conceptual framing of the problem as a thermodynamic equilibrium over binding configurations is principled and provides a mechanistic basis for inference, which is a clear advance over purely statistical or heuristic approaches.
  2. The method is designed to be general, applicable to different assay types (SMF, Fiber-seq) and organisms, which suggests potential for broad utility.
  3. The explicit modeling of competition between TFs, nucleosomes, and Pol II is a strength, as it addresses a key biological complexity often ignored in simpler analyses.
  4. The inclusion of a simulation framework for generating synthetic data is valuable for benchmarking and for testing the limits of the model.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that HiddenFoot "recovers known TF footprints" and "precisely resolved Pol II pausing" based on analyses of SMF and Fiber-seq data.
- **Evidence pointer** Results sections "HiddenFoot Classifies Bound Molecules and Recovers Biologically Meaningful TF Footprints" and "HiddenFoot Reveals Pol-II Footprints in HIV-1 Promoter"; Figures 2 and 4
- **Concern** The text describes qualitative observations (e.g., "robust footprints emerge," "Pol II footprints are prominently localized") but does not provide quantitative metrics for the accuracy or precision of these recoveries. For example, what is the false discovery rate for TF footprint detection? How does the Pol II footprint position compare to known pause sites with base-pair precision? Without quantitative benchmarks, the claim of "recovery" and "precision" is not substantiated.
- **Why it matters** The central value proposition of HiddenFoot is its ability to accurately infer binding events at single-molecule resolution. If the accuracy of these inferences is not rigorously quantified, the method's utility over existing approaches cannot be assessed.
- **Resolution test** Provide quantitative performance metrics, such as precision-recall curves for TF footprint detection against a validated set of binding sites, and a comparison of inferred Pol II pause sites to high-resolution reference data (e.g., PRO-seq or ChIP-exo) with reported positional error.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The manuscript claims that HiddenFoot "distinguishes direct TF–TF cooperativity from nucleosome-mediated co-dependency by estimating pairwise interaction energies and comparing to null models under equilibrium."
- **Evidence pointer** Results section "HiddenFoot Distinguishes Nucleosome-Mediated and Direct Physical TF Cooperativity"; Figure 3
- **Concern** The method for distinguishing direct from indirect cooperativity relies on comparing real data to simulations that "represent equilibrium binding configurations in the absence of external remodeling forces or direct protein–protein contacts." However, the text does not specify how the simulation parameters are set, how the null model is calibrated, or what statistical test is used to determine whether a real interaction energy is significantly different from the simulated null. The biological validation of predicted cooperative pairs (e.g., MEIS1-SOX4) is only supported by literature references, not by independent experimental evidence within this study.
- **Why it matters** The ability to distinguish direct physical interactions from indirect effects is a key claimed novelty. If the null model is not carefully constructed or the statistical comparison is not rigorous, the inferred interaction energies could be artifacts of model misspecification.
- **Resolution test** Clearly describe the simulation procedure, including parameter choices and the number of simulations. Define a statistical threshold for calling a pair "cooperative" or "exclusive" based on the distribution of simulated interaction energies. Validate a subset of predicted cooperative pairs with an orthogonal experimental approach (e.g., single-molecule co-binding assays or mutant analysis).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Comparative benchmarking
- **Claim pointer** The manuscript positions HiddenFoot as an advance over existing tools, stating that "existing computational tools remain insufficient to decode complex binding events from sparse methylation data."
- **Evidence pointer** Introduction and Discussion sections
- **Concern** No direct comparison to existing methods (e.g., FootprintCharter, FiberHMM) is presented in the text. The claim of insufficiency is not empirically demonstrated. A benchmark against these tools on the same datasets would be necessary to establish the relative advantage of HiddenFoot.
- **Why it matters** For a methods paper, demonstrating clear superiority or complementary utility over existing approaches is critical for adoption by the community.
- **Resolution test** Run HiddenFoot and at least one existing tool (e.g., FootprintCharter) on the same datasets and report comparative performance metrics (e.g., accuracy, computational cost, scalability).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model assumptions and limitations
- **Claim pointer** The manuscript states that HiddenFoot models binding "under thermodynamic equilibrium" and assumes "local protein concentrations are constant across all molecules mapping to the same genomic region."
- **Evidence pointer** Methods sections "Biophysical Modelling of TF, Nucleosome, and Pol II Binding" and "Scope and Limitations of HiddenFoot"
- **Concern** The equilibrium assumption is acknowledged as a simplification, but the text does not discuss the potential impact of violating this assumption on the inferred binding probabilities. For example, if active processes (e.g., chromatin remodeling) create non-equilibrium states, how would this bias the results? The assumption of constant local concentrations across molecules is also a strong simplification, especially in heterogeneous cell populations. The manuscript mentions this limitation but does not explore its consequences.
- **Why it matters** The validity of the biological conclusions depends on the robustness of the model to its assumptions. If the model is sensitive to violations of equilibrium or concentration homogeneity, the inferred interaction energies and occupancy profiles could be misleading.
- **Resolution test** Perform sensitivity analyses by simulating data under non-equilibrium conditions or with varying concentrations and assessing the impact on inference accuracy. Discuss the expected magnitude of bias under realistic biological scenarios.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Methods section "SMF and Fiber-seq Datasets and Methylation Calling"
- **Evidence pointer** Methods section
- **Issue** The description of data processing is brief. For example, the text states "Custom R scripts were used to parse PacBio reads" but does not specify the criteria for read filtering, mapping, or methylation calling. The details of how methylation probabilities are converted to binary states are not provided.
- **Required correction** Provide a more detailed description of the data processing pipeline, including software versions, parameters, and quality control steps.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections reporting correlations and comparisons
- **Evidence pointer** Results sections "HiddenFoot Classifies Bound Molecules..." and "HiddenFoot Resolves TF-Induced Nucleosome Heterogeneity..."
- **Issue** Pearson correlation coefficients are reported for some comparisons (e.g., R = 0.97 for MNase-seq), but confidence intervals or p-values are not provided. The number of regions or molecules used for each correlation is not stated.
- **Required correction** Report confidence intervals and sample sizes for all correlation coefficients. Consider using non-parametric measures if assumptions of normality are not met.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Language and presentation
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** There are several typographical and grammatical errors, e.g., "equlibirum" (Methods), "promoteing" (Discussion), "avilability" (Methods), "nuclosome" (Results). The phrase "offering a foundation" in the abstract is grammatically awkward.
- **Required correction** Careful proofreading is needed to correct these errors and improve overall language quality.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Implementation and code avilability"
- **Evidence pointer** Methods section
- **Issue** The code is stated to be available on GitHub, but no version number or specific commit identifier is provided. The manuscript does not describe the computational resources required (e.g., runtime, memory) for the analyses presented.
- **Required correction** Provide a versioned release of the code and include a brief description of computational requirements and runtime for the datasets analyzed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1–5
- **Evidence pointer** Figures referenced in text
- **Issue** The figures are not provided in the submitted text, so their quality and clarity cannot be assessed. The text descriptions suggest complex multi-panel figures, but it is unclear if the key results are easily discernible.
- **Required correction** Ensure figures are high-resolution, clearly labeled, and that all panels are referenced in the text. Consider providing a schematic of the HiddenFoot workflow as a figure.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative benchmarks for footprint recovery and Pol II pausing precision.
  - R1-M2: Insufficient detail on the null model and statistical testing for distinguishing direct versus indirect cooperativity.
  - R1-M3: No comparison to existing computational tools.
  - R1-M4: Inadequate discussion of the impact of model assumptions on biological conclusions.

- **Assessment against Nature-style criteria**
  - **Originality** The concept of applying a statistical mechanics framework to single-molecule footprinting data is novel and represents a conceptual advance over purely statistical approaches. The idea of using simulations to distinguish direct from indirect interactions is also creative. However, the originality is somewhat tempered by the fact that the underlying biophysical principles are well-established, and the novelty lies primarily in the application.
  - **Scientific importance** The ability to decode combinatorial binding events at single-molecule resolution is of high importance for understanding gene regulation. If the method is validated, it could provide new insights into the mechanisms of TF cooperativity and nucleosome dynamics. The potential for broad applicability across organisms and assay types increases its importance.
  - **Interdisciplinary readership** The work sits at the intersection of biophysics, computational biology, and molecular biology. The methods are likely to be of interest to computational biologists and biophysicists, while the biological findings would appeal to molecular biologists. The writing is generally accessible, but the methods section assumes familiarity with statistical mechanics and dynamic programming.
  - **Technical soundness** The mathematical framework is sound in principle, and the use of dynamic programming for efficient computation is appropriate. However, the lack of detailed validation and benchmarking in the provided text prevents a full assessment of technical soundness. The sensitivity of the results to model assumptions is not adequately explored.
  - **Readability for nonspecialists** The abstract and introduction are clear and provide a good overview. The results sections are readable but would benefit from more explicit statements of quantitative findings. The methods section is dense and would be challenging for nonspecialists.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the framework is potentially valuable, but the current evidence base is insufficient to fully establish the method's accuracy, robustness, and novelty. The authors should address the major concerns regarding quantitative validation, comparative benchmarking, and model assumption analysis before the claims can be fully supported.

## Risk / unsupported claims

- The claim that HiddenFoot "recovers known TF footprints" is not quantitatively supported in the provided text.
- The claim that HiddenFoot "precisely resolved Pol II pausing" is not supported by positional error metrics.
- The claim that HiddenFoot "distinguishes direct TF–TF cooperativity from nucleosome-mediated co-dependency" is not supported by a clearly described and validated statistical framework.
- The claim that "existing computational tools remain insufficient" is not empirically demonstrated through comparative benchmarking.
- The biological significance of the inferred interaction energies (e.g., for MEIS1-SOX4) is supported only by literature references, not by independent experimental validation within this study.
- The generalizability of HiddenFoot to "any other single-molecule chromatin accessibility mapping approach" is stated as a possibility but not demonstrated.