## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Statistical model design, simulation-based validation, application to amplicon-based and publicly available genome-wide NOMe-seq data in mouse embryonic stem cells
- **Shared manuscript claim summary** The authors present a statistical framework for quantitative analysis of single-molecule footprinting (SMF) data, comprising two components: (1) a "footprint spectral analysis" for estimating footprint length distributions and noise levels, and (2) a dynamic programming approach for predicting footprint positions within individual molecules. The framework is validated through in-silico simulations with Sobol' sensitivity analysis and applied to NOMe-seq data from mouse embryonic stem cells, revealing shorter-than-canonical nucleosome footprints and distinct TF footprint lengths.
- **Visible evidence base** Main text figures referenced (Figures 1-6), Extended Data Figures 1-3, Supplementary Table 1, Supplementary Text (referenced but not provided in full)
- **Missing materials affecting confidence** Supplementary Text (derivations, equations, Figure S1-S8), Extended Data Figures 1-3, Supplementary Table 1, actual figure images, code repository contents, detailed variational inference diagnostics

## Reviewer
- **Overall assessment** The manuscript addresses a genuine gap in the field: rigorous statistical tools for SMF data analysis are lacking, and the proposed framework is conceptually well-motivated. The two-component design (spectral analysis for length inference, then position prediction) is sensible and the authors have made a serious effort to validate their approach through extensive simulations and sensitivity analysis. However, the manuscript as presented has several issues that prevent full assessment. The most significant concern is that the core mathematical derivations are relegated to a Supplementary Text that was not provided, making it impossible to verify the correctness of the statistical model. Additionally, the biological findings, while interesting, are presented with limited validation against orthogonal methods, and the comparison to existing tools is incomplete. The writing is generally clear but the results section would benefit from more explicit statements of what was done versus what was found. The work has potential for publication in a high-impact venue if the technical concerns are addressed and the supplementary materials are made available for review.

- **Who would be interested in the results, and why** Researchers working on single-molecule epigenomics and chromatin biology, particularly those using NOMe-seq, Fiber-seq, or related SMF assays. The statistical framework and R packages (fetchNOMe, nomeR) would be of direct utility to this community. Computational biologists developing tools for epigenetic data analysis would also find the modeling approach of interest. The biological findings regarding nucleosome footprint lengths and TF binding site characteristics in mESCs would appeal to chromatin biologists studying genome regulation.

- **Major strengths** 1) The manuscript addresses a real and timely need for rigorous statistical tools in SMF analysis. 2) The two-component design (spectral analysis followed by position prediction) is conceptually sound and practically useful. 3) The extensive simulation-based validation, including Sobol' sensitivity analysis, demonstrates a commendable commitment to understanding method limitations. 4) The application to both amplicon-based and genome-wide datasets shows practical utility. 5) The development of user-friendly R packages (fetchNOMe, nomeR) increases the likelihood of community adoption. 6) The finding that nucleosome footprints appear shorter than canonical 147 bp is biologically interesting and potentially significant.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims to derive joint probabilities P(γ, θ|S) for a stochastic process of footprint placement, and to construct a Bayesian model for inference of footprint spectra and noise levels.
- **Evidence pointer** Methods section "Statistical footprint spectral analysis"; Results section "A statistical model for inference of footprint lengths in SMF datasets"; Supplementary Text (not provided)
- **Concern** The core mathematical derivations are entirely contained in the Supplementary Text, which was not provided for review. This includes the derivation of joint probabilities (Equation 36), the construction of the Bayesian model (Figure S6), and the dynamic programming approach with boundary conditions. Without access to these materials, it is impossible to verify the correctness of the statistical model, the validity of the assumptions (e.g., non-overlapping footprints, infinite sequence approximation), or the appropriateness of the variational inference approach. This is a blocking issue for assessment of technical soundness.
- **Why it matters** The entire manuscript rests on the statistical validity of the model. If the derivations contain errors or the assumptions are inappropriate for real SMF data, all subsequent results and biological conclusions would be compromised. The authors must provide the supplementary materials for a complete review.
- **Resolution test** Provide the Supplementary Text and all referenced figures (S1-S8) for review. The derivations should be checked for mathematical correctness, and the assumptions should be clearly stated and justified.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the model can "disentangle footprints of different lengths" and that the position prediction component "effectively disentangles footprints of different lengths, allowing for the masking of nucleosome footprints."
- **Evidence pointer** Results section "A computational model for disentangling footprints with different lengths in SMF datasets"; Figure 3
- **Concern** The validation of the position prediction component appears limited. The authors report AUROC values from simulations (Figure 3D), but the details of how these were computed, the range of conditions tested, and the performance characteristics (e.g., precision-recall, calibration) are not fully described in the provided text. More critically, the application to real data (Figures 4-6) lacks validation against orthogonal methods. For example, the claim that nucleosome footprints are shorter than 147 bp is based solely on the model's predictions, but there is no comparison to MNase-seq data, structural models, or other independent measurements of nucleosome positioning in the same cells. Similarly, the identification of TF footprints is not validated by comparison to ChIP-seq peak locations beyond the initial annotation of amplicons.
- **Why it matters** Without independent validation, it is unclear whether the model's predictions reflect true biological features or artifacts of the model's assumptions and parameters. The biological conclusions drawn from the model (shorter nucleosome footprints, distinct TF footprint lengths) would be considerably strengthened by orthogonal validation.
- **Resolution test** Provide additional validation analyses, such as comparison of predicted nucleosome positions to MNase-seq data in mESCs, comparison of predicted TF footprints to high-confidence ChIP-seq binding sites, and assessment of model calibration and precision-recall characteristics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript states that "rigorous statistical models for the analysis of datasets generated using these technologies are still missing" and implies that existing approaches are inadequate.
- **Evidence pointer** Introduction section; Discussion section
- **Concern** The manuscript does not provide a thorough comparison to existing computational methods for SMF data analysis. Several tools have been published for analyzing NOMe-seq and related data, including methods based on hidden Markov models, neural networks, and other statistical approaches. The authors mention these briefly in the introduction but do not provide a systematic comparison of their method's performance against these existing tools on benchmark datasets. Without such a comparison, it is difficult to assess the incremental contribution of the proposed framework.
- **Why it matters** For the method to be adopted by the community, it must demonstrate clear advantages over existing approaches. A head-to-head comparison on simulated and real data would establish the method's value proposition and help users decide when to use this framework versus alternatives.
- **Resolution test** Add a comparative analysis section where the proposed method is benchmarked against at least 2-3 existing SMF analysis tools on the same simulated and real datasets, with quantitative performance metrics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "the primary experimental limitation in SMF assays... is the enzyme's ability to provide accessibility information across as many positions as possible."
- **Evidence pointer** Results section "Sensitivity of statistical footprint spectral analysis to experimental factors in SMF assays"; Figure 2
- **Concern** While the Sobol' sensitivity analysis is a strength, the interpretation of the results may be overly simplified. The claim that enzyme choice is the "primary" limitation is based on the specific parameter ranges explored in the simulations. The ranges for sequencing depth (50-1,500 molecules) and noise levels (1-15%) may not fully capture the variability in real experiments. Additionally, the interaction effects between factors (e.g., between density of informative positions and sequencing depth) are mentioned but not fully explored in the provided text. The practical recommendations for experimental design that would follow from this analysis are not clearly articulated.
- **Why it matters** The sensitivity analysis has the potential to provide actionable guidance for experimental design, but the current presentation does not fully realize this potential. Clearer articulation of practical implications would increase the impact of this work.
- **Resolution test** Expand the discussion of the sensitivity analysis results to include explicit recommendations for experimental design, and consider exploring a wider range of parameter values or interaction effects.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript describes the application of the method to amplicon-based NOMe-seq data from mouse embryonic stem cells and reports "substantial variability in the estimated footprint lengths across amplicons targeting the same TF."
- **Evidence pointer** Results section "Statistical analysis of SMF experiments carried out with M.CviPI methyltransferase reveals higher methylation rates at nucleosome DNA entry-exit sites"; Figure 4
- **Concern** The biological application section is somewhat underdeveloped. The authors report variability in footprint lengths across amplicons targeting the same TF and attribute this to the spatial configuration of G/C sites relative to TF motifs. However, the analysis does not fully explore alternative explanations (e.g., genuine variability in TF binding modes, differences in chromatin context, or technical artifacts). The connection between the spectral analysis results and the subsequent position prediction analysis is not always clear. Additionally, the sample size (39 amplicons, 9 excluded) is modest, and the statistical treatment of the biological variability is not fully described.
- **Why it matters** The biological findings are presented as a demonstration of the method's utility, but the interpretation of these findings requires more careful consideration of potential confounders and alternative explanations. A more rigorous biological analysis would strengthen the case for the method's practical value.
- **Resolution test** Provide additional analyses that address alternative explanations for the observed variability, include appropriate statistical tests for comparing footprint lengths across conditions, and more clearly connect the spectral analysis results to the position prediction results.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section "A statistical model for inference of footprint lengths in SMF datasets"
- **Evidence pointer** Figure 1
- **Issue** The description of the statistical model in the main text is quite brief and relies heavily on the Supplementary Text for details. Readers may struggle to understand the model without consulting the supplementary materials.
- **Required correction** Consider expanding the main text description of the model to include a more intuitive explanation of the stochastic process, the key parameters, and the inference approach, while leaving detailed derivations to the supplement.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Software availability"
- **Evidence pointer** GitHub links provided
- **Issue** The manuscript states that the R packages are available on GitHub but does not provide version numbers, commit hashes, or documentation of dependencies. This makes it difficult for readers to reproduce the exact analyses presented.
- **Required correction** Provide version information, a detailed README, and possibly a Docker container or renv lockfile to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "In-silico simulation of SMF datasets and sensitivity analysis"
- **Evidence pointer** Figure 2
- **Issue** The description of the simulation procedure is somewhat terse. It is not entirely clear how the "random mutation" of positions was implemented, what specific distributions were used for the noise parameters, or how the "random selection of informative positions" was performed.
- **Required correction** Provide a more detailed description of the simulation procedure, including specific parameter values and distributions used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Evidence pointer** Figure 4
- **Affected element** Results section "Statistical analysis of SMF experiments carried out with M.CviPI methyltransferase reveals higher methylation rates at nucleosome DNA entry-exit sites"
- **Issue** The heatmap figures (Figure 4B) are described but not shown in the provided text. The description of the color coding (red for TF motifs, blue for flanking accessible G/C sites) is clear, but without seeing the figures, it is difficult to fully appreciate the findings.
- **Required correction** Ensure that the figures are clearly labeled and that the main text provides sufficient context for interpreting them.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Not applicable
- **Issue** The discussion is relatively brief and does not fully explore the broader implications of the findings, such as how the method could be extended to other SMF technologies, what the biological implications of shorter nucleosome footprints might be, or how the method could be integrated with other computational tools.
- **Required correction** Consider expanding the discussion to address these broader implications and potential future directions.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Analysis of publicly available genome-wide NOMe-seq data for mESC"
- **Evidence pointer** Not applicable
- **Issue** The description of the analysis of publicly available data is somewhat brief. It is not entirely clear how the 100,000 random 1-kb regions were selected, what criteria were used for including/excluding regions, or how the results from this analysis were aggregated.
- **Required correction** Provide more detail on the selection and analysis of the genome-wide data.

## Risk / unsupported claims
- The claim that the model can "disentangle" footprints of different lengths is not fully supported by the provided evidence, as the validation of the position prediction component is limited.
- The claim that nucleosome footprints in mESCs are shorter than the canonical 147 bp is based solely on the model's predictions and lacks orthogonal validation.
- The claim that the "primary experimental limitation" is enzyme choice is based on a limited range of simulation parameters and may not generalize to all experimental contexts.
- The claim that the method is "unbiased" is not fully justified, as the model requires user-defined footprint length ranges and prior parameters.
- The performance of the method compared to existing tools is not assessed, so claims of superiority or novelty relative to existing approaches are not supported.
- The generalizability of the method to other SMT technologies (e.g., Fiber-seq, FOODIE, DAF-seq) is claimed but not demonstrated with data from these technologies.