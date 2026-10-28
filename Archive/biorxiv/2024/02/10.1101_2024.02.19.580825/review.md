## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, and supplementary statements) as provided.
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, results, and reproducibility as presented in the supplied material. No external data or code verification performed.
- **Shared manuscript claim summary** The authors present RUDEUS, a Python library with hierarchical machine learning models to identify DNA-binding proteins and classify them as single-stranded or double-stranded DNA-binding. They report high performance (95% precision for DNA-binding identification, 89% for strand type discrimination), a generalizable training pipeline integrating protein language models, supervised learning, and Bayesian optimization, and demonstrate utility by annotating over 20,000 sequences and validating three proteins via molecular docking.
- **Visible evidence base** Abstract, Introduction, Methods (Sections 2.1–2.5), Results and Discussion (Sections 3.1–3.3), Conclusion, and availability statements. Figures and tables are referenced but not provided in the supplied text.
- **Missing materials affecting confidence** Figures 1–4, Tables 1–2, dataset details, hyperparameter grids, code repository contents, and full performance metrics are not included. This limits verification of statistical claims, model selection, and docking validation.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful software tool with a reasonable machine learning pipeline for DNA-binding protein classification. The reported performance is competitive, and the integration of protein language models with Bayesian optimization is sensible. However, the evidence base is incomplete, with key figures and tables absent, and several methodological details are underspecified. The claims of generalizability and superiority over existing methods are not fully supported by the provided material. The structural validation via docking is described only qualitatively, and the large-scale annotation lacks independent verification. The work may be of interest to computational biologists, but the current presentation does not establish the case with sufficient rigor.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those developing machine learning tools for DNA-binding protein annotation. Researchers in protein engineering and design may also find the library useful for integrating predictive models into pipelines for directed evolution or mutational analysis. The comparative benchmarking against existing methods could interest method developers seeking state-of-the-art baselines.
- **Major Strengths** The manuscript addresses a relevant problem with a practical software solution. The pipeline is described as modular and generalizable, which is a strength for adoption. The use of multiple protein language models and a statistical selection process is methodologically sound. The reported performance metrics are strong, and the inclusion of a structural validation component adds a useful dimension. The availability of code and models under an open license supports reproducibility.
- **Major Concerns** The absence of figures and tables prevents assessment of the actual results, including confusion matrices, precision-recall curves, and comparative benchmarks. The statistical selection process is described but not fully justified, and the criteria for choosing final models are vague. The claim of "generalizable pipeline" is not demonstrated beyond the two tasks presented. The structural docking validation is described for only three proteins, with no quantitative metrics or comparison to experimental data. The large-scale annotation of 20,000 sequences is mentioned but not analyzed for accuracy or biological relevance. Overfitting is acknowledged but not quantified or addressed in the final model selection.
- **Minor Comments** The abstract and introduction contain some redundancy in describing the tool's capabilities. The methods section would benefit from clearer definitions of dataset sources and preprocessing steps. The conclusion overstates the "superior performance" without full comparative data. The GitHub link in the text appears duplicated and may be a typographical error. The author contributions and funding statements are clear.
- **Technical failings that need to be addressed before the case is established** The lack of actual figures and tables is a critical failing, as the core results are not visible. The statistical selection method needs a clearer mathematical formulation and justification. The docking protocol requires more detail, including scoring functions, input preparation, and how the "best pose" was determined. The large-scale annotation should include error analysis or validation on a held-out set. The overfitting issue must be addressed with regularization or cross-validation results.
- **Assessment against Nature-style criteria** Originality: Moderate. The combination of protein language models with Bayesian optimization for DNA-binding classification is not entirely novel, but the specific library and pipeline may offer practical value. Scientific importance: Moderate. The problem is relevant, but the incremental advance over existing tools is not clearly demonstrated. Interdisciplinary readership: Limited. The manuscript is primarily technical and may not appeal to a broad biological audience without clearer biological insights. Technical soundness: Weak as presented, due to missing evidence and underspecified methods. Readability for nonspecialists: The abstract is accessible, but the methods and results sections assume familiarity with machine learning and docking terminology.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the missing figures and tables, along with methodological gaps, prevent a supportive recommendation. The authors should provide the full results and clarify the methods before resubmission.

### Major Concerns
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims high performance (95% precision for DNA-binding, 89% for strand type) and superior benchmarking against existing methods.
- **Evidence pointer** Figures 2–3, Tables 1–2 (not provided)
- **Concern** The core results are presented only as references to figures and tables that are not included in the supplied material. Without these, the performance claims cannot be verified, and the comparative benchmarking is unassessable.
- **Why it matters** The central claims of the manuscript rest on these results. Their absence prevents any meaningful evaluation of the tool's effectiveness or its standing relative to prior work.
- **Resolution test** Provide all figures and tables with clear captions, including confusion matrices, precision-recall curves, ROC curves, and full comparative data. Ensure the numbers cited in the text match the displayed results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The statistical selection process is described as filtering models based on Bernoulli events and binomial distributions, but the details are incomplete.
- **Evidence pointer** Section 3.1, location not provided
- **Concern** The description of the statistical filter is vague. The quantile thresholds, the definition of "success," and the rationale for the 16 events are not fully specified. The criteria for final model selection ("highest performances, lowest overfitting, simplicity") are subjective and not operationalized.
- **Why it matters** Without a clear and reproducible selection method, the choice of final models cannot be independently validated, and the claim of a "generalizable pipeline" is weakened.
- **Resolution test** Provide a formal mathematical description of the selection algorithm, including all thresholds and decision rules. Show the distribution of successes and how the final models were chosen.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of structural claims
- **Claim pointer** The structural docking validation is claimed to confirm the DNA-binding interactions for three proteins (1BNZ, 1HRY, 3ULP).
- **Evidence pointer** Section 3.3, Figure 4 (not provided)
- **Concern** The docking results are described qualitatively, with no quantitative metrics such as docking scores, RMSD values, or comparison to known experimental structures. The selection of the "best pose" is not justified, and the biological relevance of the identified residues is not critically assessed.
- **Why it matters** The structural validation is presented as a key feature of the tool, but without quantitative evidence, it does not substantiate the claim that the predictions are biologically meaningful.
- **Resolution test** Include docking scores, cluster statistics, and a comparison of predicted interaction residues with experimental or literature-derived data. Provide clear images of the docking poses with labeled residues.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Overfitting and generalization
- **Claim pointer** The models are claimed to have high performance, but overfitting is acknowledged in the text.
- **Evidence pointer** Section 3.2, location not provided
- **Concern** The text states that differences between training and validation metrics indicate overfitting, yet the final models are still selected. The extent of overfitting is not quantified, and no regularization or alternative validation strategies are described.
- **Why it matters** Overfitting undermines the generalizability claim and the reliability of the tool on unseen data. Without addressing this, the reported performance may not reflect real-world utility.
- **Resolution test** Report training and validation metrics for all models, quantify the overfitting gap, and describe any measures taken to mitigate it (e.g., cross-validation, regularization, or early stopping).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Dataset and preprocessing transparency
- **Claim pointer** The datasets are collected from literature and databases, and filters are applied, but the details are incomplete.
- **Evidence pointer** Section 2.1, location not provided
- **Concern** The sources of the datasets are cited but not described in detail. The criteria for "redundancy" filtering and the length cutoffs are mentioned but not justified. The class imbalance (26,982 negative vs. 20,518 positive for DNA-binding) is not discussed in terms of its impact on model training.
- **Why it matters** Dataset composition and preprocessing directly affect model performance and comparability with other methods. Lack of transparency limits reproducibility and fair benchmarking.
- **Resolution test** Provide detailed descriptions of each dataset, including accession numbers, sequence counts, and preprocessing steps. Discuss how class imbalance was handled.

### Minor Comments
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction contain overlapping statements about the tool's capabilities and performance, which could be streamlined for clarity.
- **Required correction** Condense redundant descriptions and focus on the unique contributions of the work.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5, location not provided
- **Issue** The GitHub link appears duplicated in the text, which may be a typographical error. The repository contents are not described in detail.
- **Required correction** Correct the link and provide a clear description of the repository structure, including dependencies and usage examples.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.2
- **Evidence pointer** Section 3.2, location not provided
- **Issue** The text mentions "more than 10000 combinations" but does not specify the exact number or the breakdown across tasks.
- **Required correction** Provide the exact number of combinations and clarify how they were generated.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 3.2
- **Evidence pointer** Section 3.2, location not provided
- **Issue** The term "Beronulli" appears to be a typo for "Bernoulli."
- **Required correction** Correct the spelling.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Comparative analysis
- **Affected element** Table 2 (not provided)
- **Evidence pointer** Table 2, location not provided
- **Issue** The comparative table is referenced but not included, and the criteria for selecting comparison methods are not stated.
- **Required correction** Include the table and describe how the comparison methods were chosen.

## Risk / unsupported claims
- The claim of "superior performance" over state-of-the-art methods is unsupported without the full comparative data in Table 2.
- The claim of "generalizable pipeline" is not demonstrated beyond the two tasks and lacks evidence of applicability to other protein classification problems.
- The structural validation claims for 1BNZ, 1HRY, and 3ULP are not quantitatively supported.
- The annotation of over 20,000 sequences is mentioned without any accuracy assessment or biological validation.
- The statistical selection process is described but not fully specified, making the model selection non-reproducible.
- The overfitting issue is acknowledged but not quantified or resolved, undermining the reliability of the reported performance.