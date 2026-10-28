## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific and technical evaluation of the proposed method, benchmarking claims, and biological validation, based solely on the provided text
- **Shared manuscript claim summary** The authors present scRegulate, a variational autoencoder-based framework that embeds prior TF-target gene regulatory knowledge into a deep generative model to infer cell-specific TF activities and cell-type-specific gene regulatory networks from scRNA-seq data. They claim superior performance over existing methods in clustering accuracy, GRN inference, TF activity prediction under perturbation, and computational efficiency.
- **Visible evidence base** Text descriptions of results, benchmark datasets, and evaluation metrics; specific numerical values for some clustering metrics and perturbation results; references to figures and supplementary materials not provided
- **Missing materials affecting confidence** All figures, supplementary tables, supplementary notes, and detailed benchmark results are not available. This substantially limits verification of the quantitative claims and methodological details.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing approach that integrates prior regulatory knowledge into a variational inference framework for TF activity inference. The motivation is clear and the method addresses a genuine gap in the field. However, the provided text alone is insufficient to fully evaluate the technical soundness and the strength of the benchmark claims. Several methodological details are vague, and the absence of figures and supplementary materials prevents verification of key results. The biological validation on PBMC data is qualitative and relies on known regulators, which is supportive but not definitive. The computational efficiency claim is promising but requires more rigorous comparison. Overall, the work has potential, but the current evidence base is insufficient to fully establish the stated advantages.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing and applying single-cell analysis tools, particularly those focused on gene regulatory network inference and transcription factor activity estimation. The method's interpretability and efficiency could appeal to researchers analyzing large-scale scRNA-seq datasets where existing tools are computationally prohibitive. The integration of prior knowledge with deep learning may also interest method developers seeking hybrid approaches.
- **Major strengths** The conceptual design of embedding prior regulatory knowledge into a VAE is a meaningful contribution. The three-phase training strategy (prior initialization, dynamic inference, cell-type-specific fine-tuning) is well motivated. The use of multiple benchmark types (synthetic, experimental, perturbation) is comprehensive. The reported computational efficiency is a practical advantage. The PBMC case study demonstrates biological interpretability through recovery of known lineage-defining TFs.
- **Major Concerns** 
  - R1-M1: The quantitative benchmark results are not verifiable from the provided text. Key figures and supplementary tables are referenced but not included, making it impossible to assess the statistical significance and magnitude of the claimed improvements.
  - R1-M2: The description of the model architecture and training procedure is incomplete. Critical details such as the exact loss function formulation, hyperparameter ranges, and the specific implementation of the dynamic scheduling of the prior mask and regularization are not fully specified.
  - R1-M3: The evaluation of GRN inference on synthetic data relies on the GRouNdGAN simulator, but the realism and potential biases of this simulator are not discussed. The generalizability of performance from synthetic to real biological networks is not established.
  - R1-M4: The Perturb-seq validation is limited to a small set of TFs and the analysis approach is not fully described. The claim of "higher precision" compared to alternatives is not supported by quantitative comparison in the text.
  - R1-M5: The PBMC case study is largely qualitative. While recovery of known TFs is encouraging, the text does not provide a systematic comparison to alternative methods on this dataset, nor does it quantify the novelty of the inferred GRNs beyond known biology.
- **Minor Comments** 
  - R1-m1: The abstract states "Comprehensively benchmarking on public experimental and synthetic datasets demonstrates scRegulate’s superior ability" but the term "superior" is not qualified. It would be more precise to specify against which methods and under which metrics.
  - R1-m2: The introduction mentions "unprecedented resolution" in studying cell-type-specific regulatory mechanisms. This phrasing is overstated given the lack of direct comparison to methods that also produce cell-type-specific outputs.
  - R1-m3: The methods section states that genes must have at least one associated TF in the prior GRN to be included. This filtering step could introduce bias and should be discussed in terms of its impact on the analysis.
  - R1-m4: The discussion of limitations focuses on prior GRN dependence, but other potential limitations such as sensitivity to hyperparameters, scalability to very large datasets, and the interpretability of the latent space are not addressed.
  - R1-m5: The GitHub repository is mentioned, but the manuscript does not state the software license or provide a versioned release, which is important for reproducibility.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: The approach of embedding prior regulatory knowledge into a VAE with a dynamic mask for GRN inference is a novel combination of existing ideas. It is not entirely unprecedented but offers a distinct contribution.
  - Scientific importance: TF activity inference is a central problem in single-cell biology. A method that improves accuracy and efficiency while providing interpretable outputs would be of significant value to the community.
  - Interdisciplinary readership: The work is primarily of interest to computational biologists and bioinformaticians. The biological validation on PBMC data may attract some experimental biologists, but the technical focus limits broader interdisciplinary appeal.
  - Technical soundness: The conceptual framework is sound, but the incomplete methodological details and unverifiable quantitative results prevent a full assessment of technical soundness.
  - Readability for nonspecialists: The manuscript is generally well written and accessible to readers with a computational biology background. The introduction and discussion are clear, but the methods section assumes familiarity with VAE terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the preliminary results are encouraging, but the current evidence base is insufficient to fully establish the claimed advantages. The authors must provide the missing figures, tables, and methodological details to allow a rigorous evaluation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims that scRegulate "consistently outperformed" baseline methods in clustering accuracy, GRN inference, and perturbation prediction across multiple datasets.
- **Evidence pointer** Figures 2, 3, 4, 5 and supplementary figures/tables referenced in Sections 3.1, 3.2, 3.3, 3.4; location not provided
- **Concern** The central quantitative claims of the paper are presented only as text summaries. The actual figures, tables, and supplementary materials containing the benchmark results are not available for review. This makes it impossible to verify the magnitude of the reported improvements, the statistical significance beyond the stated P-values, or the fairness of the comparisons. For example, the claim that scRegulate achieved an ARI of 0.814 on PBMC is presented without the corresponding results for all baseline methods in a comparable format.
- **Why it matters** The primary contribution of the paper is the empirical demonstration of superior performance. Without access to the underlying data and visualizations, the validity of these claims cannot be assessed. This is a fundamental requirement for establishing the scientific case.
- **Resolution test** Provide all figures and supplementary tables with full benchmark results, including error bars, statistical test details, and a clear description of the comparison protocol. The authors should also make the code and processed data available for independent verification.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The methods section describes a VAE with a three-phase training procedure, but the exact formulation of the loss function, the scheduling of the prior mask, and the hyperparameter choices are not fully specified.
- **Evidence pointer** Section 2.3, including 2.3.1, 2.3.2, 2.3.3, 2.3.4; location not provided
- **Concern** The description of the model is incomplete. The loss function is stated as the sum of the ELBO and a GRN regularization loss, but the exact form of the ELBO (e.g., whether it includes a KL divergence term and how it is weighted) is not given. The dynamic scheduling of the prior mask m(t) is described qualitatively, but the specific schedule and the criteria for transitioning between phases are not defined. The hyperparameter ranges for the number of layers, latent dimensions, learning rates, and regularization coefficients are not provided. The text also mentions a "find-tunning" procedure in Section 2.5.2, which appears to be a typo for "fine-tuning," but the details of this procedure are not described.
- **Why it matters** Reproducibility is a cornerstone of computational biology. Without a complete specification of the model and training procedure, other researchers cannot implement or build upon the method. The lack of detail also raises questions about the robustness of the approach to hyperparameter choices.
- **Resolution test** Provide a complete mathematical specification of the loss function, the exact scheduling algorithm for the prior mask, and a table of all hyperparameters and their ranges. Include a description of the fine-tuning procedure and how it differs from the global training. Consider releasing the code with a configuration file that documents all settings.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The manuscript states that GRouNdGAN simulated datasets were used as a "controlled benchmark" for GRN inference, and that scRegulate "consistently outperformed" SCENIC, CellOracle, and BITFAM on these datasets.
- **Evidence pointer** Section 2.3.5 and Section 3.2; location not provided
- **Concern** The use of synthetic data from GRouNdGAN is appropriate for benchmarking, but the manuscript does not discuss the potential limitations of this approach. GRouNdGAN is itself a generative model, and its simulated data may not fully capture the complexity and noise of real biological data. The text does not describe the parameters used for the simulation, the number of cells and genes, or the specific ground-truth networks imposed. Without this information, it is difficult to assess whether the benchmark is fair and whether the results generalize to real data.
- **Why it matters** Synthetic benchmarks are only useful if they are realistic and well-characterized. If the simulation parameters are not disclosed, the reader cannot judge the difficulty of the task or the potential for bias in favor of certain methods.
- **Resolution test** Provide a detailed description of the GRouNdGAN simulation parameters, including the number of cells, genes, cell types, and the properties of the ground-truth networks. Discuss the limitations of synthetic benchmarks and how the results on synthetic data relate to performance on real biological data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims that on the Perturb-seq dataset, scRegulate "demonstrated higher precision in detecting TF knockdowns" compared to SCENIC, decoupleR, and BITFAM, and that some alternative methods failed or produced incorrect results.
- **Evidence pointer** Section 3.3 and Figure 3B; location not provided
- **Concern** The text provides specific P-values and LFC values for scRegulate's results on selected TFs, but the comparison to alternative methods is only qualitative. The claim of "higher precision" is not supported by a quantitative comparison, such as a table of precision-recall metrics or a statistical test comparing the methods' performance across all perturbed TFs. The text also does not specify how "precision" is defined in this context.
- **Why it matters** The perturbation experiment is a key validation of the method's biological relevance. A qualitative claim of superiority is not sufficient to establish that scRegulate is genuinely better than existing tools. A rigorous quantitative comparison is needed.
- **Resolution test** Provide a quantitative comparison of all methods on the Perturb-seq dataset, including metrics such as precision, recall, and F1-score for detecting significantly repressed TFs. Specify the statistical tests used and the criteria for defining a "correct" prediction.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** The PBMC case study claims that scRegulate identifies cell-type-specific TFs and GRNs that are "aligned with known regulatory pathways" and that the inferred GRNs are biologically relevant.
- **Evidence pointer** Section 3.4 and Figures 4, 5, 8, 9; location not provided
- **Concern** The validation on PBMC data is largely qualitative. The text lists known TFs for each cell type, which is supportive but does not demonstrate that scRegulate provides new biological insights or outperforms other methods in this context. The functional enrichment analysis is mentioned but not described in detail, and the results are not shown. The comparison to PCA in Figure 7 is mentioned but not quantified.
- **Why it matters** The biological case study is intended to demonstrate the practical utility of the method. A qualitative recovery of known biology is a necessary but not sufficient validation. The manuscript would be strengthened by a more systematic analysis, such as a comparison of the inferred GRNs to known regulatory networks or a demonstration that scRegulate identifies novel regulators that are experimentally validated.
- **Resolution test** Provide a more detailed description of the PBMC analysis, including the number of differentially active TFs per cell type, the results of the functional enrichment analysis, and a quantitative comparison of the inferred GRNs to known regulatory interactions. Consider including a comparison to GRNs inferred by alternative methods on the same dataset.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, Results section
- **Issue** The abstract states that benchmarking "demonstrates scRegulate's superior ability" without specifying the comparison methods or the metrics. This is an overgeneralization.
- **Required correction** Specify the baseline methods and the key metrics in the abstract, or soften the claim to "competitive or superior performance" with a reference to the results section.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Language
- **Affected element** Introduction
- **Evidence pointer** Section 1, paragraph 4
- **Issue** The phrase "unprecedented resolution" is an overstatement. The method provides cell-specific GRNs, but other methods also produce cell-type-specific outputs.
- **Required correction** Replace with a more measured phrase such as "a higher-resolution view" or "cell-type-specific resolution."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2, Data preprocessing
- **Issue** The filtering criterion requiring genes to have at least one associated TF in the prior GRN may exclude genes that are relevant but not annotated in the prior. The potential impact of this filtering is not discussed.
- **Required correction** Add a sentence discussing the potential bias introduced by this filtering and its implications for the inferred GRNs.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Section 4, Discussion and conclusions
- **Issue** The discussion of limitations is brief and focuses only on prior GRN dependence. Other potential limitations, such as sensitivity to hyperparameters, the choice of the prior network, and the interpretability of the latent space, are not addressed.
- **Required correction** Expand the limitations paragraph to address these additional points.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Availability and implementation
- **Evidence pointer** Availability and implementation section
- **Issue** The manuscript states that results and scripts are available on GitHub, but it does not specify the software license or provide a versioned release. This is important for long-term reproducibility.
- **Required correction** Add a license and a versioned release (e.g., a Zenodo DOI) to the GitHub repository and mention this in the manuscript.

## Risk / unsupported claims
- The claim of "superior ability" in the abstract and "consistently outperformed" in the results is not fully supported by the provided text, as the quantitative data are in missing figures and tables.
- The claim of "higher precision" on the Perturb-seq dataset is not quantitatively substantiated in the text.
- The claim that scRegulate provides "unprecedented resolution" is not supported by any comparative analysis.
- The biological relevance of the PBMC case study is supported only by qualitative recovery of known TFs, not by a systematic comparison or novel findings.
- The computational efficiency claim is mentioned but not quantified in the text, making it unverifiable.
- The generalizability of the method to datasets with different characteristics (e.g., different species, technologies, or prior network qualities) is not discussed or evaluated.