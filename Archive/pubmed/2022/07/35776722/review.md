## Review setup
- **Input scope** Full manuscript text (Methods, Results, Discussion, Conclusion) without figures or supplementary files
- **Assessment boundary** Scientific validity, methodological soundness, and interpretability of claims based solely on the provided text
- **Shared manuscript claim summary** The authors present SIMPA, a machine learning-based imputation method for sparse single-cell ChIP-seq data that leverages bulk ENCODE reference data. They claim single-cell specificity, accurate imputation from few input bins, preservation of cell-type clustering, improved pathway enrichment, and interpretability via feature importance analysis.
- **Visible evidence base** Text descriptions of cross-validation results, simulation studies, real data applications on human (Grosselin et al.) and mouse (Zhu et al.) datasets, and comparisons to a reference-free method
- **Missing materials affecting confidence** All figures, supplementary files (S1 Table, S1 File with Supplementary Notes and Figs S1-S7), and code repository contents are not provided, limiting verification of quantitative results and methodological details

## Reviewer
- **Overall assessment** The manuscript addresses a relevant gap in scChIP-seq data analysis by proposing a reference-based imputation approach with an interpretability extension. The conceptual framework is sound and the application to real datasets demonstrates potential utility. However, the absence of figures and supplementary materials prevents full evaluation of the quantitative claims, and several methodological details require clarification to establish robustness.
- **Who would be interested in the results, and why** Researchers working on single-cell epigenomics, particularly those analyzing scChIP-seq or scATAC-seq data, would find this method valuable for addressing data sparsity. Computational biologists developing imputation tools for sparse genomic data and those interested in interpretable machine learning for biological applications would also benefit.
- **Major strengths** The use of bulk reference data to guide single-cell imputation is a novel and sensible strategy, addressing a limitation of reference-free methods. The interpretability extension (InterSIMPA) adds value beyond imputation by enabling biological insight. The validation on both simulated and real datasets, including cross-species application, strengthens the claims.
- **Major Concerns** The lack of quantitative results in the text (all figures and supplementary materials are missing) makes it impossible to assess the magnitude of reported improvements. The computational cost of training per-cell, per-candidate-bin models is acknowledged but not quantified, raising scalability concerns. The choice of Random Forest without hyperparameter tuning or comparison to other classifiers is not justified. The biological validation relies on pathway enrichment and co-expression correlations, which are indirect and may not fully establish functional relevance.
- **Minor Comments** The manuscript would benefit from clearer definitions of "single-cell specificity" and how it is measured. The discussion of future integration with multi-omics data is speculative and could be condensed. The GitHub repository is mentioned but its contents and usability are not described in sufficient detail.
- **Technical failings that need to be addressed before the case is established** The absence of all figures and supplementary data prevents verification of the central claims. The cross-validation methodology is described only briefly, and the handling of class imbalance in the binary classification problem is not discussed. The simulation procedure for generating "single cells" from bulk data is not fully detailed, and the criteria for selecting the 24 genes in the interpretability analysis are not provided.
- **Assessment against Nature-style criteria** Originality: The reference-based approach for scChIP-seq imputation is novel, though it builds on existing concepts from bulk imputation. Scientific importance: Addressing scChIP-seq sparsity is timely and relevant, but the impact is moderate given the niche application. Interdisciplinary readership: The method will appeal to computational biologists and epigenomics researchers, but the presentation is too specialized for a broad audience. Technical soundness: The methodology is plausible but cannot be fully assessed without figures and supplementary materials. Readability for nonspecialists: The manuscript is clearly written but assumes familiarity with ChIP-seq and machine learning concepts.
- **Recommendation posture** Supportive if technical concerns are resolved, specifically if the missing quantitative evidence is provided and methodological details are clarified.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim summary** The authors claim accurate imputation, single-cell specificity, and improved pathway enrichment, but all quantitative results are in figures and supplementary files not provided.
- **Evidence pointer** Figures 1-6, S1-S7; Supplementary Notes 1-6 in S1 File
- **Concern** The manuscript text describes results qualitatively (e.g., "high area under ROC-curve values," "moderate positive correlation") without reporting specific numbers, error bars, or statistical tests. Without access to the figures and supplementary materials, the magnitude and significance of the reported improvements cannot be evaluated.
- **Why it matters** The central claims of the paper rest on quantitative performance metrics. Without these, the reader cannot assess whether SIMPA offers meaningful improvements over existing methods or whether the results are robust.
- **Resolution test** Provide all figures and supplementary files for review, or include key quantitative results (e.g., AUC values, correlation coefficients, p-values) in the main text.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim summary** The cross-validation and simulation procedures are described only briefly, and the handling of class imbalance and hyperparameter selection is not addressed.
- **Evidence pointer** Methods section "Cross validations" and "Validation on simulated data"
- **Concern** The text states that stratified ten-fold cross-validation was used, but details on how the training and test sets were constructed, how the class imbalance (few positive bins) was handled, and whether hyperparameters were tuned are missing. The simulation procedure for generating sparse profiles from bulk data is also not fully specified.
- **Why it matters** These details are critical for reproducibility and for assessing whether the reported performance is an artifact of the evaluation setup rather than a genuine property of the method.
- **Resolution test** Expand the Methods section to include full details on cross-validation splits, class imbalance handling, hyperparameter selection, and the simulation algorithm.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational feasibility
- **Claim summary** The method trains a separate model for each candidate bin and each cell, which is acknowledged as computationally intensive, but the actual cost is not quantified.
- **Evidence pointer** Methods section "The SIMPA algorithm" and Discussion
- **Concern** The text mentions that results were obtained on a high-performance cluster within 1-2 days, but no details on the number of cells, bins, or computational resources are provided. This makes it difficult to assess whether the method is practical for larger datasets or typical laboratory settings.
- **Why it matters** If the computational cost is prohibitive, the method's utility is limited, especially for researchers without access to high-performance computing.
- **Resolution test** Report runtime and resource usage for the datasets analyzed, and discuss scalability to larger datasets.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim summary** The interpretability analysis claims that feature importance values correlate with co-expression, suggesting biological relevance, but the analysis is limited to a small set of genes.
- **Evidence pointer** Results section "Model interpretability on real data" and "InterSIMPA applied on mouse scChIP-seq data"
- **Concern** The analysis uses only 24 genes in the human dataset and 4 genes in the mouse dataset. The selection criteria for these genes are not provided, and the correlation coefficients are described as "moderate" without specific values or significance testing.
- **Why it matters** The biological relevance of the imputed data is a key selling point of the method. A limited and potentially biased gene selection weakens the evidence for this claim.
- **Resolution test** Provide the gene selection criteria, report correlation coefficients with confidence intervals and p-values, and consider a more comprehensive or unbiased analysis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of "single-cell specificity"
- **Evidence pointer** Results section "Validation on simulated data"
- **Issue** The term "single-cell specific" is used to describe the imputation results, but it is not formally defined. It is unclear whether this refers to the imputed profile being closer to the origin cell than to other cells, or to some other metric.
- **Required correction** Provide a clear definition of "single-cell specificity" and describe how it is quantified.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Availability section and GitHub link
- **Issue** The GitHub repository is mentioned, but its structure, dependencies, and usage instructions are not described in the manuscript. The reference data files are also not detailed.
- **Required correction** Include a brief description of the repository contents, required Python packages, and instructions for reproducing the main results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Comparison fairness
- **Affected element** Benchmarking against SCALE
- **Evidence pointer** Results section "Performance on cell-type clustering and functional analysis"
- **Issue** The comparison to SCALE is described, but it is unclear whether SCALE was run with optimal parameters or whether the comparison is apples-to-apples given that SCALE is reference-free.
- **Required correction** Clarify the benchmarking setup, including parameter choices for SCALE and any preprocessing steps.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Performance metrics
- **Evidence pointer** Results sections throughout
- **Issue** The text reports qualitative descriptions of performance (e.g., "high," "moderate") without specific values or variability measures.
- **Required correction** Report exact values for key metrics (e.g., AUC, correlation coefficients) with standard deviations or confidence intervals.

## Risk / unsupported claims
- The claim that SIMPA "accurately preserves cell type clustering" is unsupported without the t-SNE plots and clustering metrics in Figure 5.
- The claim that imputed profiles are "single-cell specific" in over 95% of simulations is unverifiable without Figure 3.
- The claim that InterSIMPA reveals "biologically relevant promoter-promoter relations" is weakly supported by the limited gene set and qualitative correlation descriptions.
- The claim that SIMPA is "better" than the reference-free method is not substantiated without quantitative comparisons in the text.
- The generalizability of the method to other histone marks or transcription factors beyond those tested is not established.