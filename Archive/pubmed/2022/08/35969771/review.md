## Review setup
- **Input scope** Full manuscript text (main text, methods, and supplementary figure/table references as provided)
- **Assessment boundary** Theoretical modeling, simulation, and experimental validation of time-shifted transcriptional correlations for gene regulatory network inference
- **Shared manuscript claim summary** The authors propose that gene regulatory relationships can be inferred from stochastic transcriptional variation in single cells at steady state, using time-shifted correlations between TF and target gene RNA levels. They develop a quantitative model, simulate regulatory pairs, and validate the approach using a temporally resolved scRNA-seq dataset in K562 cells.
- **Visible evidence base** Main text figures (Fig. 1–4), supplementary figures (Fig. S1–S4), supplementary table (Table S1), methods descriptions, and references to deposited data (GSE202292) and code (GitHub)
- **Missing materials affecting confidence** Full supplementary information (equations, detailed methods, and supplementary figures) was not provided; raw data and code were not directly inspected; figure panels referenced but not all visible in the provided text

## Reviewer

### Overall assessment
This manuscript presents a conceptually interesting and potentially valuable theoretical framework for inferring gene regulatory relationships from steady-state single-cell transcriptional data. The core idea, that time-shifted correlations arising from transcriptional bursting can distinguish regulatory covariation from cell-state mixture artifacts, is well-motivated and clearly explained. The modeling is grounded in experimentally derived parameters, and the authors provide a thoughtful analysis of experimental feasibility. However, the manuscript would be strengthened by a more thorough treatment of several technical aspects, including the robustness of the approach to model misspecification, the statistical power calculations under realistic conditions, and the interpretation of the experimental validation results. The current evidence base is sufficient to support the theoretical claims, but the experimental demonstration is preliminary and does not fully establish the practical utility of the method.

### Who would be interested in the results, and why
This work will be of interest to researchers in gene regulatory network inference, single-cell genomics, and computational biology. The theoretical framework provides a principled basis for extracting regulatory information from steady-state data, which could complement existing perturbation-based approaches. The analysis of experimental design requirements (cell number, detection efficiency) will be useful for experimentalists planning time-resolved single-cell studies. The discussion of distinguishing regulatory covariation from cell-state artifacts addresses a fundamental challenge in the field and will be relevant to a broad audience of single-cell data analysts.

### Major strengths
1. The conceptual insight is clear and well-articulated: time-shifted correlations can distinguish regulatory relationships from cell-state mixture effects, which is a significant advance over simple simultaneous correlation approaches.
2. The model is grounded in experimentally measured parameters, lending credibility to the simulation results.
3. The authors provide a thoughtful quantitative analysis of experimental feasibility, including power calculations that will guide future experimental design.
4. The experimental validation, while preliminary, uses a state-of-the-art temporally resolved scRNA-seq method and provides suggestive evidence that the approach can identify regulatory targets.
5. The manuscript is generally well-written and accessible to a broad audience, with clear explanations of the underlying biology and modeling assumptions.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "with enough data, it should be possible to identify regulatory relationships within a cell type without need for perturbation, by leveraging the intrinsic stochasticity in transcriptional bursting across individual cells at steady-state."
- **Evidence pointer** Results section "Transcriptional Bursting in Cells at Steady State Gives Rise to Temporal Covariation between TFs and Their Target Genes"; Fig. 2; SI Appendix, Fig. S2
- **Concern** The claim that regulatory relationships can be identified from steady-state data relies on the assumption that the model correctly captures the underlying biology. The authors use a two-state bursting model with a Hill function response, but real regulatory relationships may involve more complex dynamics, including feedback loops, post-transcriptional regulation, and chromatin state effects. The sensitivity of the time-shifted correlation to these model misspecifications is not systematically explored. For example, if the target gene's response to TF protein is not instantaneous but involves delays due to chromatin remodeling or RNA polymerase recruitment, the predicted time-shifted correlation curve could be substantially altered. The authors acknowledge some limitations but do not provide a quantitative analysis of how robust their conclusions are to deviations from the assumed model.
- **Why it matters** If the time-shifted correlation pattern is not robust to realistic biological complexity, the proposed approach may not work in practice, and the central claim of the paper would be weakened.
- **Resolution test** The authors should perform additional simulations with alternative model formulations (e.g., including delays in target gene activation, feedback regulation, or more complex response functions) and demonstrate that the qualitative features of the time-shifted correlation (rise and fall) are preserved. Alternatively, they could provide a theoretical argument for why the pattern is expected to be robust.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "to reliably detect relevant increases in time-shifted correlation, it will be necessary to improve current methods for time-resolved labeling by increasing 1) transcript detection efficiency, 2) the number of cells that it is feasible to study, or 3) both."
- **Evidence pointer** Results section "From Theory to Experimental Design"; Fig. 3G; SI Appendix, Fig. S3C–G
- **Concern** The power calculations are based on a specific scenario with particular parameter values (e.g., Hill coefficient = 2, specific burst frequencies and half-lives). The authors do not provide a comprehensive analysis of how the required sample size and detection efficiency scale with the strength of the regulatory effect, the noise in the system, or the number of genes being tested. In particular, the multiple testing burden of genome-wide regulatory network inference is not addressed. If thousands of TF-target pairs are tested simultaneously, the required sample size to achieve adequate power after multiple testing correction could be substantially larger than the estimates provided.
- **Why it matters** The feasibility of the proposed approach depends critically on whether the required sample sizes and detection efficiencies are achievable with current or near-future technology. If the authors' estimates are overly optimistic, the practical utility of the method is questionable.
- **Resolution test** The authors should provide a more comprehensive power analysis that includes multiple testing correction, a range of effect sizes, and a discussion of how the required sample size scales with the number of hypotheses tested. They should also discuss whether the required improvements in detection efficiency are realistic given current technological trends.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "many of the genes that show simultaneous correlations are likely to be regulatory targets" based on the experimental validation in K562 cells.
- **Evidence pointer** Results section "Leveraging Simultaneous Correlations in a Single-Cell Dataset to Enrich for Gene Regulation"; Fig. 4C–D; SI Appendix, Fig. S4G–H
- **Concern** The experimental validation is based on a single cell type (K562) and a single TF (GATA1) analyzed in detail. The enrichment of correlated genes in GATA1 ChIP-seq data and perturbation data is suggestive but does not establish that the approach will work generally across many TFs and cell types. The analysis of 56 TFs with ChIP-seq data shows enrichment in 53/56 cases, which is encouraging, but the effect sizes and statistical significance of these enrichments are not fully reported. Additionally, the analysis is based on simultaneous correlations, not the time-shifted correlations that are the main focus of the theoretical framework.
- **Why it matters** The experimental validation is the primary evidence that the approach works in practice. If it is limited to a specific context or if the enrichment is modest, the broader applicability of the method is uncertain.
- **Resolution test** The authors should provide more detailed statistics on the ChIP-seq enrichment analysis, including effect sizes and confidence intervals. They should also discuss how the approach might be extended to time-shifted correlations in future experiments and whether the current validation provides evidence for the specific mechanism proposed in the theoretical model.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the temporal pattern is important because it allows one to distinguish correlation arising due to gene regulation from correlation arising from an important alternative possibility" (i.e., cell-state mixtures).
- **Evidence pointer** Results section "Distinguishing Cell State-Based Structure from Regulatory Covariation"; Fig. 3F; SI Appendix, Fig. S3B
- **Concern** The comparison between regulatory covariation and cell-state mixture is based on a specific simulation of two stable cell states. In reality, cell-state mixtures can be more complex, involving continuous gradients, multiple states, or states that change over time. The authors do not explore whether the time-shifted correlation pattern remains distinguishable from more realistic cell-state structures. Additionally, the analysis assumes that the cell-state mixture is static over the time window of measurement, which may not hold in practice.
- **Why it matters** The ability to distinguish regulatory covariation from cell-state artifacts is a central claim of the paper. If the distinction breaks down under more realistic conditions, the approach may produce false positives in real data.
- **Resolution test** The authors should simulate more complex cell-state structures (e.g., continuous gradients, multiple states, or time-varying states) and demonstrate that the time-shifted correlation pattern remains distinguishable from regulatory covariation. They should also discuss potential strategies for identifying and correcting for cell-state effects in real data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results section "Transcriptional Bursting in Cells at Steady State Gives Rise to Temporal Covariation between TFs and Their Target Genes"
- **Evidence pointer** Fig. 2E
- **Issue** The description of the temporal dynamics of TF(RNA), TF(P), and Target(RNA) following a burst at t = 0 is somewhat dense and could be clarified for readers who are not familiar with stochastic gene expression models. The distinction between the dynamics of nascent and total RNA is important but may be confusing.
- **Required correction** Consider adding a brief intuitive explanation of why the different quantities peak at different times, perhaps with a simple analogy or a more explicit description of the underlying processes.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and Methods section "Simulating Two-Gene Regulation in a Population of Cells at Steady State"
- **Evidence pointer** Location not provided
- **Issue** The description of the simulation is brief, and it is not entirely clear how the stochastic simulations were implemented (e.g., the time step, the number of independent runs, the handling of initial conditions). The authors mention that they confirmed equivalence to Gillespie simulations, but the details of this comparison are not provided.
- **Required correction** Provide more details on the simulation implementation, including the time step, the number of runs, and the criteria used to confirm equivalence to Gillespie simulations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Results section "From Theory to Experimental Design"
- **Evidence pointer** Fig. 3G
- **Issue** The power calculations are presented in a way that may be difficult for experimentalists to interpret. The relationship between the coefficient of variation of the effect size estimate and the required sample size is not immediately intuitive.
- **Required correction** Consider presenting the power calculations in a more accessible format, such as a plot showing the required sample size as a function of detection efficiency for a fixed power level, or a table with example scenarios.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "Leveraging Simultaneous Correlations in a Single-Cell Dataset to Enrich for Gene Regulation"
- **Evidence pointer** Fig. 4C
- **Issue** The enrichment analysis for GATA1 correlated genes in perturbation data is described briefly. It is not clear how the significance threshold was chosen for the perturbation data, or whether the enrichment is robust to the choice of threshold.
- **Required correction** Provide more details on the perturbation data analysis, including the significance threshold used and a sensitivity analysis to confirm the robustness of the enrichment.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Discussion section
- **Evidence pointer** Location not provided
- **Issue** The discussion of limitations is thorough but could be more clearly organized. Some limitations are mentioned in passing (e.g., nuclear buffering, TF autoregulation) without a clear explanation of how they might affect the results.
- **Required correction** Consider reorganizing the limitations paragraph to group related issues and provide a brief explanation of how each limitation might impact the proposed approach.

### Technical failings that need to be addressed before the case is established
1. The robustness of the time-shifted correlation pattern to model misspecification is not systematically explored (R1-M1).
2. The power calculations do not account for multiple testing in genome-wide applications (R1-M2).
3. The experimental validation is based on simultaneous correlations, not the time-shifted correlations that are the main theoretical contribution (R1-M3).
4. The distinction between regulatory covariation and cell-state mixtures is only demonstrated for a simple two-state model (R1-M4).

### Assessment against Nature-style criteria
- **Originality** The concept of using time-shifted correlations from transcriptional bursting to infer regulatory relationships is novel and represents a conceptual advance over existing approaches that rely on simultaneous correlations or perturbations. The idea is well-motivated and clearly presented.
- **Scientific importance** If validated, this approach could provide a powerful new tool for gene regulatory network inference from steady-state single-cell data, which would be of broad interest to the genomics and systems biology communities. The potential to infer regulation without perturbation is significant.
- **Interdisciplinary readership** The work bridges theoretical modeling, computational simulation, and experimental validation, and should appeal to researchers in quantitative biology, computational genomics, and experimental single-cell biology. The writing is generally accessible, though some sections may be challenging for nonspecialists.
- **Technical soundness** The modeling is grounded in experimental data, and the simulations are carefully designed. However, the robustness of the conclusions to model assumptions and the statistical power analysis need further development. The experimental validation is preliminary and does not fully establish the practical utility of the method.
- **Readability for nonspecialists** The main text is well-written and the key concepts are explained clearly. However, some technical sections (e.g., the description of the temporal dynamics and the power calculations) could be made more accessible.

### Recommendation posture
Supportive if technical concerns are resolved. The theoretical framework is conceptually strong and potentially important, but the current evidence does not fully establish the robustness and practical utility of the approach. The authors should address the concerns regarding model robustness, statistical power, and the interpretation of the experimental validation before the case is fully established.

## Risk / unsupported claims
1. The claim that "with enough data, it should be possible to identify regulatory relationships within a cell type without need for perturbation" is supported by simulations but not fully validated experimentally. The experimental data only demonstrate enrichment of simultaneous correlations, not the time-shifted correlation approach.
2. The claim that time-shifted correlations can distinguish regulatory covariation from cell-state mixtures is only demonstrated for a simple two-state model. The robustness to more complex cell-state structures is not established.
3. The power calculations suggest that ~50,000 cells are needed for reliable detection with current detection efficiency, but this estimate is based on a specific parameter set and does not account for multiple testing. The generalizability of this estimate is uncertain.
4. The statement that "the temporal pattern is important because it allows one to distinguish correlation arising due to gene regulation from correlation arising from an important alternative possibility" is a key claim, but the evidence for this distinction is based on simulations with specific assumptions that may not hold in all real-world scenarios.