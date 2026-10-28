## Review setup
- **Input scope** Full manuscript text, including main figures, methods, and supplementary information references
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present scover, a convolutional neural network tool that simultaneously discovers regulatory sequence motifs and quantifies their contribution to gene expression or chromatin accessibility from single-cell data, with applications to human kidney, mouse multi-tissue, and human brain datasets
- **Visible evidence base** Main text, figure legends, methods section, supplementary figure and table descriptions
- **Missing materials affecting confidence** Actual figure images, supplementary files (Tables S1-S3, Figures S1-S12), code repository contents, and detailed hyperparameter tuning results were not available for direct inspection

## Reviewer
- **Overall assessment** The manuscript describes a useful and flexible computational tool for motif discovery from single-cell data. The core idea of using a shallow convolutional network with a leave-one-out influence scoring strategy is sensible and addresses a genuine gap in the field. However, the evidence presented in the text is insufficient to fully evaluate the method's performance, robustness, and biological validity. Several claims regarding biological findings and method advantages require stronger quantitative support or clearer comparison to existing approaches. The manuscript is potentially publishable but needs substantial revision and additional analyses to establish the case.

- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and single-cell genomics would be interested. The tool addresses a practical need for linking sequence motifs to quantitative gene expression or chromatin accessibility readouts at single-cell resolution. Biologists studying cell-type-specific transcriptional regulation, particularly in tissues such as kidney, brain, and across multiple mouse organs, would find the application examples relevant. The method's flexibility across data modalities (scRNA-seq and scATAC-seq) broadens its appeal.

- **Major strengths** The manuscript addresses a clear and important gap: no existing method simultaneously performs de novo motif discovery and quantifies motif impact on gene expression from single-cell data. The architecture is appropriately simple, which aids interpretability and reduces overfitting risk with modest sample sizes. The pooling strategy to reduce sparsity is practical and well described. The application to three diverse datasets demonstrates versatility. The benchmarking against FIMO-based regression and random forest models is a useful comparison. The authors are transparent about limitations, including computational cost and the minority of motifs used by the model.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that scover simultaneously discovers regulatory motifs and quantifies their contribution to gene expression, and that this joint approach provides a better fit than FIMO-based regression or random forest models.
- **Evidence pointer** Results section, Figure 2, Additional file 2: Figure S4
- **Concern** The performance comparison between scover and FIMO-based models is reported only as variance explained (R2) values in supplementary figures. The text states scover explains 15% of variance for kidney, 28% for Tabula Muris, and 19% for brain, with FIMO-based models performing worse. However, no statistical significance testing, confidence intervals, or effect sizes are reported. The comparison is also confounded by the fact that FIMO uses a fixed motif database, while scover performs de novo discovery, making the comparison not directly apples-to-apples. The claim that joint discovery is advantageous is not rigorously established.
- **Why it matters** The central methodological claim of the paper is that joint motif discovery and impact quantification is superior to separate steps. Without proper statistical comparison, this claim is not supported. Readers cannot assess whether the observed differences are meaningful or within noise.
- **Resolution test** Provide statistical tests comparing model performance across folds (e.g., paired tests on R2 values), report confidence intervals, and include a controlled comparison where FIMO is given the same motif set discovered by scover to isolate the benefit of joint optimization.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The methods state that hyperparameters are optimized via Bayesian optimization with specific priors and defaults, and that reproducibility is achieved by running the model multiple times.
- **Evidence pointer** Methods section, "Training the neural network"
- **Concern** The description of the hyperparameter optimization is incomplete. The text mentions priors for learning rate and weight standard deviations, but does not specify the full search space, the number of hyperparameter trials, the criteria for early stopping, or how the final hyperparameters were selected across folds. The statement that "reproducibility can be achieved by running it r times" is vague. No information is provided on the variance of results across runs or folds, which is critical for a stochastic optimization method.
- **Why it matters** Reproducibility is a core requirement for computational tools. Without detailed hyperparameter settings, search ranges, and run-to-run variability metrics, other researchers cannot reliably apply or validate the method.
- **Resolution test** Provide a complete table of hyperparameter search spaces, final selected values per dataset, the number of trials, and report mean and standard deviation of performance metrics across multiple independent runs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that scover identifies known and novel regulatory motifs with cell-type-specific impact, including findings such as SNAI2 and Ebox/CACCTG association with proximal tubule development, and MEF2 and TBR1 as repressors in brain.
- **Evidence pointer** Results section, Figures 2e, 5b, 5c, 6e
- **Concern** The biological findings are presented descriptively without rigorous statistical validation. For example, the correlation between SNAI2 expression and Ebox/CACCTG influence scores is reported, but no significance threshold, multiple testing correction, or effect size is given. The claim that MEF2 motifs are associated with smaller peak sizes in glutamatergic neurons is based on visual inspection of 2D histograms (Figure 6e) without quantitative analysis. The pseudotime analysis correlating motif influence with developmental trajectories lacks statistical assessment.
- **Why it matters** The biological insights are a key selling point of the tool. If these findings are not statistically robust, the utility of scover for generating testable hypotheses is undermined.
- **Resolution test** Add statistical tests for all reported correlations and associations, including multiple testing corrections. For the pseudotime analysis, provide regression or correlation statistics with confidence intervals. For the brain data, quantify the relationship between motif influence and peak size with appropriate models.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that the pooling strategy using k-nearest neighbors and geometric sketching preserves cell-type heterogeneity and produces homogeneous pools.
- **Evidence pointer** Methods section, "Pooling", Additional file 2: Figure S1
- **Concern** The evaluation of pooling quality is limited to descriptive statistics in supplementary figures. The claim that pools are "relatively homogenous" with one cell type accounting for more than 80% is presented without a formal metric or comparison to alternative pooling strategies. The choice of k and the number of pools p are not systematically justified. The impact of pooling parameters on downstream motif discovery is not explored.
- **Why it matters** The pooling strategy is a critical preprocessing step that affects all downstream results. If pooling introduces biases or loses rare cell types, the motif influence scores could be misleading.
- **Resolution test** Provide quantitative metrics for pool homogeneity (e.g., entropy, purity) across different parameter settings. Perform a sensitivity analysis varying k and p to show results are robust. Compare to alternative pooling approaches such as simple averaging within annotated cell types.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The manuscript claims that scover is compatible with the scanpy workflow and is available under an open-source license, implying ease of use for the broader community.
- **Evidence pointer** Results section, Discussion, GitHub repository link
- **Concern** The manuscript does not provide sufficient documentation of the software's usability. No runtime information, memory requirements, or input/output format specifications are given. The dependency on specific GPU resources is mentioned only in passing. The claim of scanpy compatibility is not demonstrated with a concrete example or tutorial.
- **Why it matters** For a tool to be adopted by the community, especially by biologists who may not be computational experts, clear documentation and usability guidelines are essential.
- **Resolution test** Provide a detailed user guide, a step-by-step tutorial with example data, and benchmark runtime and memory usage on standard hardware. Include information on CPU-only execution if possible.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1 legend
- **Issue** The figure legend describes the workflow but does not clearly indicate what the input and output dimensions are at each stage. The relationship between the convolutional filters and the motif alignment step is not visually explicit.
- **Required correction** Add annotations to the figure showing tensor dimensions and data flow, and clarify how filters are converted to position frequency matrices.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "Alignment of motifs"
- **Evidence pointer** Methods section
- **Issue** The description of how motifs are aligned to CIS-BP using Tomtom is brief. The threshold of 0.05 is mentioned, but the multiple testing correction method used by Tomtom is not stated.
- **Required correction** Specify the Tomtom options used, including the q-value threshold and the significance method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, Figure 3b
- **Evidence pointer** Figure 3b legend
- **Issue** The text states that 55 of 132 TFs are strongly correlated with |r| > 0.5 and significant p-values, but the p-value adjustment method is not described in the main text.
- **Required correction** State the multiple testing correction method used for the correlation analysis in the figure legend or methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions that non-matching motifs may represent biologically meaningful signals, but this is speculative. The authors could strengthen this by analyzing the sequence content of non-matching motifs.
- **Required correction** Add a brief analysis of the nucleotide composition or positional bias of non-matching motifs to support the interpretation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Data processing"
- **Evidence pointer** Methods section
- **Issue** The filtering thresholds for genes and ATAC regions are described, but the exact criteria for the "expressed in less than X% of pools" filters are not fully specified for all datasets.
- **Required correction** Provide a complete table of filtering thresholds for each dataset.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract does not mention the benchmarking against FIMO or the limitations of the method, which are important for setting expectations.
- **Required correction** Add a sentence summarizing the benchmarking result and a brief note on computational cost.

## Risk / unsupported claims
- The claim that scover provides a better fit than FIMO-based models is not statistically supported (R1-M1).
- The biological findings regarding SNAI2, MEF2, and TBR1 are presented without statistical validation (R1-M3).
- The claim that the pooling strategy retains cell-type heterogeneity is not quantitatively demonstrated (R1-M4).
- The statement that non-matching motifs are "likely biologically meaningful" is speculative and not supported by analysis.
- The claim of scanpy compatibility is not demonstrated with a concrete example.
- The reproducibility of the method across runs is asserted but not quantified.