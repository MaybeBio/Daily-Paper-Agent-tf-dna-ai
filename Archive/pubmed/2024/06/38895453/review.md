## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific and technical evaluation of the OneSC platform as described; no code execution or independent benchmarking performed
- **Shared manuscript claim summary** The authors present OneSC, a computational platform that infers Boolean gene regulatory networks from single-cell RNA sequencing data and simulates cell state transitions using stochastic differential equations. They claim improved scalability over BoolODE, competitive edge recovery relative to 13 other GRN inference methods on BEAR/ BEELINE benchmarks, faithful recapitulation of myeloid differentiation trajectories from mouse progenitor data, and accurate prediction of perturbation outcomes matching prior experimental observations.
- **Visible evidence base** Abstract, Introduction, Methods (overview only), Results (benchmarking, scalability, myeloid application), Discussion, Conclusion; supplementary figures and tables referenced but not provided
- **Missing materials affecting confidence** Supplementary figures (S1–S13), Supplementary Tables, detailed algorithm pseudocode, parameter settings, code repository contents, full benchmarking results, and statistical details of comparisons

## Reviewer

- **Overall assessment** The manuscript describes a potentially useful computational platform that addresses a real need in the field: generating executable Boolean networks that can simulate cell state transitions and predict perturbation outcomes. The core idea of combining GRN inference with a scalable stochastic differential equation simulator is sound and builds on prior work (BoolODE, IQCELL). However, the evidence presented in the main text is insufficient to fully evaluate several key claims, particularly regarding benchmarking fairness, statistical significance of performance differences, and the biological fidelity of the myeloid simulations. The manuscript would benefit from more detailed methods, additional validation, and clearer presentation of quantitative results.

- **Who would be interested in the results, and why** Researchers in computational biology, systems biology, and developmental biology who work on gene regulatory network inference, cell fate decision modeling, and in silico perturbation prediction. The platform could also be of interest to experimental biologists seeking to prioritize transcription factor perturbations for directed differentiation or reprogramming experiments.

- **Major strengths**
  1. Addresses an important gap: most GRN inference methods are evaluated on edge recovery, not on dynamical fidelity or predictive utility.
  2. The combination of GRN inference and simulation in one platform with native perturbation support is practically valuable.
  3. The scalability improvement over BoolODE is a meaningful technical contribution.
  4. The application to mouse myeloid progenitors demonstrates a real-world use case with biologically relevant predictions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The mean F1 score of OneSC's GRNs was 0.61 which was as good as or higher than other GRN inference methods applied to the same data"
- **Evidence pointer** Results section, Figure 2A; location not provided
- **Concern** The benchmarking comparison against 13 other methods is described only in summary form. It is unclear whether the performance differences are statistically significant, how thresholds were selected for each method, and whether the same data preprocessing and clustering were used across all methods. The claim of "as good as or higher" is vague and not supported by error bars or statistical tests in the text.
- **Why it matters** Without rigorous benchmarking, the claim that OneSC is competitive with or superior to existing methods cannot be assessed. This is central to the platform's value proposition.
- **Resolution test** Provide full benchmarking results including per-method precision, recall, and F1 scores with variance estimates; perform and report statistical significance tests (e.g., paired tests across datasets); describe threshold selection procedures explicitly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "OneSC generated the correct number of steady states in 5 out of 10 gold standard datasets" and "OneSC networks generated steady states that were identical to the steady states of gold standard networks in dyn-BF, dyn-BFC, dyn-TF, dyn-CY and VSC structures"
- **Evidence pointer** Results section, Figure 2B–C; location not provided
- **Concern** The steady state analysis is described qualitatively. It is unclear how "correct number" is defined, how similarity is computed beyond a brief mention of "maximum percent agreement," and whether the comparison to gold standard steady states is appropriate given that the gold standard networks were used to generate the synthetic data. The results for dyn-CY (0 identical steady states) and the lower similarity for HSC and mCAD are not discussed in sufficient depth.
- **Why it matters** The ability to recapitulate steady states is a key claim of the platform. Without clear metrics and interpretation of failures, the reader cannot judge the practical utility of OneSC for real biological systems.
- **Resolution test** Provide a detailed description of the steady state analysis methodology, including how similarity is calculated, how "correct" is defined, and a discussion of why certain networks perform poorly. Include quantitative results for all 10 datasets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "in silico perturbations resulted in cell state compositions that largely match in vivo and in vitro genetic perturbations"
- **Evidence pointer** Results section, Figure 5B, S13A–B; location not provided
- **Concern** The comparison between in silico perturbation predictions and experimental observations is described only qualitatively. It is unclear how "largely match" is quantified, which specific experimental studies were used for comparison, and whether the comparisons are appropriate (e.g., same cell types, same perturbation timing, same readouts). The selection of five TFs for detailed comparison is not justified.
- **Why it matters** The predictive power of the platform is its most significant potential contribution. Without rigorous quantitative comparison to experimental data, this claim remains anecdotal.
- **Resolution test** Provide a systematic comparison table listing each TF perturbation, the predicted outcome, the experimentally observed outcome, and a quantitative measure of agreement. Justify the selection of TFs and experimental studies.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "OneSC's simplified stochastic differential equations to model regulation allows OneSC to be more scalable and faster when simulating dense networks"
- **Evidence pointer** Results section, Figure 3A–B; location not provided
- **Concern** The scalability benchmarking is described but the results are not presented in sufficient detail. It is unclear what "faster" means quantitatively, how runtime was measured, and whether the comparison to BoolODE is fair (e.g., same hardware, same number of simulations, same convergence criteria). The failure of BoolODE at certain edge counts is mentioned but not explained.
- **Why it matters** Scalability is a key claimed advantage over existing tools. Without clear quantitative evidence, this advantage cannot be verified.
- **Resolution test** Provide runtime measurements with error bars, describe hardware and software environments, and explain the conditions under which BoolODE fails. Include scaling plots for both single-core and multi-core settings.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, first paragraph
- **Evidence pointer** Introduction; location not provided
- **Issue** The introduction assumes familiarity with GRN inference methods and Boolean network concepts. A brief explanation of what a Boolean network is and why it is useful for modeling cell state transitions would improve accessibility.
- **Required correction** Add one or two sentences defining Boolean networks and their relevance to cell fate modeling.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "An overview of using OneSC"
- **Evidence pointer** Methods section; location not provided
- **Issue** The description of the genetic algorithm is too brief. Key parameters (population size, mutation rate, crossover rate, convergence criteria) and the fitness function are not described.
- **Required correction** Provide a detailed description of the genetic algorithm implementation, including all parameters and the fitness function used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Results, myeloid application
- **Evidence pointer** Results section, Figure 4; location not provided
- **Issue** The preprocessing steps for the mouse myeloid progenitor dataset are not described. It is unclear how normalization, feature selection, clustering, and pseudotime computation were performed.
- **Required correction** Add a subsection in Methods describing the data preprocessing pipeline, including software versions and parameters.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion, limitations paragraph
- **Evidence pointer** Discussion; location not provided
- **Issue** The limitations section is brief and does not address potential issues with the Boolean network assumption (e.g., loss of quantitative information, inability to capture graded responses).
- **Required correction** Expand the limitations section to discuss the inherent limitations of Boolean network models and how they might affect predictions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, benchmarking
- **Evidence pointer** Results section, Figure 2A; location not provided
- **Issue** The comparison to IQCELL is mentioned but not shown in the benchmarking results. It is unclear whether IQCELL was included in the 13 methods compared.
- **Required correction** Clarify whether IQCELL was included in the benchmarking and, if so, present its results explicitly.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Insufficient benchmarking detail and lack of statistical rigor
  - R1-M2: Incomplete steady state analysis methodology and results
  - R1-M3: Qualitative perturbation validation without quantitative comparison
  - R1-M4: Incomplete scalability benchmarking details

- **Assessment against Nature-style criteria**
  - **Originality**: The combination of GRN inference with a scalable stochastic differential equation simulator and native perturbation support is a novel integration of existing ideas. However, the individual components (Boolean networks, genetic algorithm inference, stochastic simulation) are not new. The originality lies in the specific integration and the focus on dynamical fidelity rather than edge recovery.
  - **Scientific importance**: The platform addresses a real need in the field and could be useful for hypothesis generation in developmental biology and cell engineering. However, the importance is somewhat incremental, building on BoolODE and IQCELL, and the demonstrated biological insights are limited to one system.
  - **Interdisciplinary readership**: The work is primarily of interest to computational biologists and systems biologists. The biological application to myeloid differentiation may attract some experimental hematologists, but the technical focus limits broader appeal.
  - **Technical soundness**: The core ideas are sound, but the evidence presented is insufficient to fully evaluate the claims. The benchmarking and validation need more rigor and detail.
  - **Readability for nonspecialists**: The manuscript is generally well-written but assumes familiarity with GRN inference and Boolean network concepts. Some sections, particularly the Results, are dense and would benefit from clearer explanations of the methods and metrics.

- **Recommendation posture** Supportive if technical concerns are resolved. The platform has clear potential value, but the current manuscript does not provide sufficient evidence to fully establish the claims of competitive performance, faithful recapitulation, and accurate prediction. The authors should address the major concerns regarding benchmarking rigor, steady state analysis, and perturbation validation before the case is fully established.

## Risk / unsupported claims
- The claim that OneSC is "as good as or higher" than 13 other methods is unsupported without statistical tests and full benchmarking results.
- The claim that in silico perturbations "largely match" experimental observations is unsupported without a systematic quantitative comparison.
- The claim that OneSC "faithfully recapitulate the four myeloid differentiation trajectories" is not fully supported by the presented evidence, as the similarity metrics are not described in sufficient detail.
- The scalability advantage over BoolODE is not quantitatively supported in the main text.
- The statement that OneSC "can accurately predict cell fate decision biases" is an overstatement given the limited validation presented.