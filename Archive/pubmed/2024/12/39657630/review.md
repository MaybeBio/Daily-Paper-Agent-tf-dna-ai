## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and conclusion sections. No supplementary files, figures, or tables were provided for review.
- **Assessment boundary** Evaluation is limited to the claims and evidence presented in the provided manuscript text. Claims referencing supplementary data, figures, or tables are assessed based on textual descriptions only.
- **Shared manuscript claim summary** The authors benchmark 11 recent computational tools for DNA-binding protein identification, introduce new evaluation datasets (BTD, EBTD, HBTD) to address data leakage and class imbalance issues in existing benchmarks, demonstrate inflated performance in prior studies due to data doppelgangers, and show that an ensemble of the two best tools with BLAST significantly improves prediction performance.
- **Visible evidence base** Manuscript text only. Tables 1-6, Figures 1-6, and all supplementary materials are referenced but not provided.
- **Missing materials affecting confidence** All figures, tables, supplementary data files, and the GitHub repository contents. Without these, quantitative results, dataset construction details, and statistical analyses cannot be independently verified.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely problem in computational biology: the reliability of DNA-binding protein prediction tools. The authors identify a critical issue, data leakage in existing benchmarks, and propose new datasets to mitigate it. The benchmarking methodology is thoughtful, and the finding that simple homology-based tools like BLAST remain competitive is valuable. However, the manuscript has several significant weaknesses. The lack of reproducibility details for the new datasets, incomplete reporting of hyperparameters and training procedures, and the absence of statistical significance testing for performance differences weaken the conclusions. The error analysis is insightful but limited in scope. The discussion of limitations and recommendations is useful but somewhat speculative. Overall, the work has merit but requires substantial revisions to establish its claims rigorously.
- **Who would be interested in the results, and why** Computational biologists developing protein function prediction tools, bioinformaticians working on genome annotation pipelines, and researchers in the broader machine learning for biology community. The benchmarking methodology and the new datasets will be of particular interest to those developing new DBP prediction methods, as they provide a more realistic evaluation framework. The finding that ensemble methods combining simple homology search with learned models perform well is practically relevant for tool users.
- **Major strengths** 1) The identification and quantification of data leakage in widely used benchmark datasets is an important contribution with broad implications. 2) The introduction of new benchmarking datasets with controlled similarity thresholds and class imbalance is methodologically sound. 3) The comprehensive evaluation pipeline, including multiple training scenarios and error analyses, is thorough. 4) The comparison with traditional tools like BLAST provides a valuable baseline that is often missing in such studies. 5) The provision of user-friendly software and datasets is commendable for reproducibility.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The work is original in its systematic identification of data leakage in DBP benchmarks and the construction of new evaluation datasets. However, the concept of benchmarking computational tools is not novel per se. Scientific importance: The findings have significant implications for the DBP prediction field, potentially changing how tools are evaluated and developed. The demonstration of inflated performance in prior studies is important. Interdisciplinary readership: The work is primarily of interest to computational biologists and bioinformaticians. The technical depth may limit broader interdisciplinary appeal, though the general issue of data leakage in machine learning benchmarks has cross-disciplinary relevance. Technical soundness: The benchmarking methodology is generally sound, but several technical details are missing or unclear, including dataset construction specifics, hyperparameter choices, and statistical testing. The reproducibility of the new datasets is not fully established. Readability for nonspecialists: The manuscript is clearly written and accessible to readers with a background in computational biology. The abstract and introduction provide sufficient context. However, some technical sections may be challenging for those without machine learning expertise.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially valuable, but the manuscript requires substantial revisions to address the methodological gaps and strengthen the evidence base.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors claim to introduce new benchmarking datasets (BTD, EBTD, HBTD) that address data leakage and class imbalance issues.
- **Evidence pointer** Section 4 "Benchmarking dataset development", location not provided
- **Concern** The description of dataset construction lacks critical details necessary for reproducibility. The authors state that DBPs were extracted from UniProtKB with a review score of 5, but do not specify the exact search queries, the date of extraction, or the version of the database used. The filtering criteria for excluding sequences with non-amino acid characters and length ranges are mentioned, but the specific thresholds and implementation details are not provided. The CD-HIT clustering parameters beyond the similarity threshold are not described. Most critically, the process for constructing the negative set relies on keyword-based filtering to identify potential DBPs, but the exact keyword list is not provided, making it impossible to replicate or assess the completeness of this filtering step.
- **Why it matters** The new datasets are a central contribution of this work. Without detailed construction protocols, other researchers cannot reproduce the datasets, verify their quality, or use them for future benchmarking. The validity of the entire evaluation depends on the quality and representativeness of these datasets.
- **Resolution test** Provide a detailed step-by-step protocol for dataset construction, including exact database versions, search queries, keyword lists, filtering thresholds, and CD-HIT parameters. Make the full pipeline code available in the GitHub repository. Ideally, provide the raw data before filtering to allow independent verification.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim** The authors claim that combining the predictions of the two best computational tools with BLAST-based prediction significantly enhances DBP identification capability.
- **Evidence pointer** Section 5.5 "Combining BLAST with the best tools", Table 6, location not provided
- **Concern** The claim of "significant enhancement" is not supported by any statistical testing. The manuscript reports sensitivity, specificity, and MCC values for individual tools and the ensemble, but no confidence intervals, standard errors, or hypothesis tests are provided. The improvement in MCC from 0.4493 (Local-DPP) to 0.5079 (ensemble) is reported, but it is unclear whether this difference is statistically significant given the test set size. Additionally, the ensemble method uses majority voting, but the manuscript does not describe how ties are broken or whether weighted voting was considered.
- **Why it matters** The ensemble method is a key practical recommendation of the paper. Without statistical evidence, readers cannot assess whether the improvement is real or due to chance. The lack of uncertainty quantification undermines the reliability of the conclusions.
- **Resolution test** Perform statistical significance testing (e.g., McNemar's test for paired binary classifications, or bootstrap resampling for MCC differences) to compare the ensemble against individual tools. Report confidence intervals for all performance metrics. Describe the voting scheme in detail, including tie-breaking rules.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim** The authors claim to benchmark 11 state-of-the-art computational tools, reproducing their reported performance.
- **Evidence pointer** Section 2 "Benchmarking tools", Table 1, location not provided
- **Concern** The manuscript states that six out of eleven tools did not have code available and could not be retrieved even after contacting authors. For these tools, the authors must have re-implemented the methods based on the original papers. However, the manuscript does not describe the re-implementation process, the choices made when the original papers were ambiguous, or how the authors verified that their re-implementations match the original methods. For tools with available code, the manuscript does not specify the exact versions, dependencies, or any modifications made. The statement that "we simply followed the code" when inconsistencies were found between code and paper is concerning, as it is unclear how these inconsistencies were identified and resolved.
- **Why it matters** Reproducibility of the benchmark results is essential for the credibility of the study. If the re-implementations are not faithful to the original methods, the performance comparisons may be unfair or incorrect. The lack of detail on this process makes it impossible for others to verify the results.
- **Resolution test** Provide a detailed description of the re-implementation process for each tool without available code, including all parameter choices and assumptions. For tools with code, specify the exact versions and any modifications made. Ideally, provide the exact commands or scripts used to run each tool in the GitHub repository.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim** The authors claim that the poor performance of iDNAProt-ES and DeepDBP is due to feature-related issues, including errors in third-party feature determination and increased dimensionality.
- **Evidence pointer** Section 7 "Discussion and recommendations", location not provided
- **Concern** The manuscript reports a 40% drop in MCC for iDNAProt-ES and over 80% drop for DeepDBP when reproducing their results. The authors attribute this to "errors in the determination (by third-party tools) of these features" and "severely increased curse of dimensionality." However, no evidence is provided to support these claims. The manuscript does not analyze the specific features that may be problematic, does not compare the features generated by third-party tools to any ground truth, and does not perform any ablation studies to isolate the cause of the performance drop. The attribution to dimensionality is speculative without a systematic analysis of feature importance or redundancy.
- **Why it matters** Understanding why certain tools fail is important for guiding future improvements. The current explanation is speculative and not evidence-based. If the performance drop is actually due to implementation errors in the re-implementation process, the conclusions would be incorrect.
- **Resolution test** Conduct a systematic analysis of the features used by iDNAProt-ES and DeepDBP, including quality assessment of third-party tool outputs, feature importance analysis, and ablation studies. Compare the features generated in the authors' pipeline to those used in the original papers to identify any discrepancies.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim** The authors claim that the BLAST-based approach with a 35% identity threshold is a valid baseline for DBP identification.
- **Evidence pointer** Section 5.4 "Comparison with traditional tools", location not provided
- **Concern** The manuscript does not provide sufficient detail on how the BLAST-based prediction was implemented. It is unclear whether the positive training set was used as the database, how the 35% identity threshold was chosen, and whether this threshold was optimized on the training set or fixed a priori. The manuscript also does not describe how the E-value threshold was selected for the results shown in Table 6. The choice of these thresholds can significantly affect the performance of the BLAST baseline, and without justification, the comparison may be biased.
- **Why it matters** The comparison with BLAST is a key contribution of the paper, as it demonstrates the value of simple homology-based methods. If the BLAST baseline is not implemented optimally or fairly, the comparison may be misleading.
- **Resolution test** Describe the BLAST-based prediction pipeline in detail, including the database construction, threshold selection criteria, and whether thresholds were optimized. Provide a sensitivity analysis showing how performance varies with different identity and E-value thresholds.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the authors "highlight the data leakage issue in conventional datasets leading to inflated performance" but does not provide any quantitative indication of the magnitude of this inflation.
- **Required correction** Include a brief quantitative summary in the abstract, such as the average performance drop observed when evaluating on the new datasets.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Table 1
- **Evidence pointer** Table 1, location not provided
- **Issue** The manuscript references Table 1 for tool categorization but does not describe the table contents in the text. It is unclear what specific information is presented.
- **Required correction** Add a brief description of Table 1 in the text, summarizing the key categorization criteria and the number of tools in each category.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Section 5.1
- **Evidence pointer** Section 5.1 "Training on proposed dataset", location not provided
- **Issue** The manuscript states that "DNABP, Local-DPP, StackDPPred, PDBP-Fusion, LSTM-CNN_Fusion, and PreDBP-PLMs performed the best" but does not provide the actual performance values in the text.
- **Required correction** Include the performance values (sensitivity, specificity, MCC) for all tools in the text or refer explicitly to the corresponding table entries.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 6.2
- **Evidence pointer** Section 6.2 "E-ratio analysis", location not provided
- **Issue** The manuscript reports p-values for the Wilcoxon rank-sum test but does not state the sample sizes or effect sizes. The p-value alone is insufficient to assess the practical significance of the findings.
- **Required correction** Report the sample sizes for each comparison and provide a measure of effect size, such as the median difference in E-ratios between correctly classified and misclassified samples.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 7
- **Evidence pointer** Section 7 "Discussion and recommendations", location not provided
- **Issue** The discussion of AlphaFold as a potential tool for structural feature generation is speculative and not directly related to the benchmarking results. It is unclear whether the authors are recommending this as a future direction or have preliminary evidence.
- **Required correction** Clarify whether this is a speculative suggestion or a tested approach. If speculative, label it as such and consider moving it to a "future directions" paragraph.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 5.3
- **Evidence pointer** Section 5.3 "Evaluation after training dataset improvement", location not provided
- **Issue** The manuscript describes two class balancing techniques (random undersampling and oversampling) but does not specify the exact implementation details, such as the random seed used or the oversampling ratio.
- **Required correction** Provide the implementation details for both balancing techniques, including any random seeds, to ensure reproducibility.

## Risk / unsupported claims
- The claim that the ensemble method "significantly enhances" performance is unsupported without statistical testing.
- The attribution of poor performance in iDNAProt-ES and DeepDBP to feature-related issues is speculative and not evidence-based.
- The claim that the new datasets are "unbiased" is not fully supported, as the construction process may introduce other biases not discussed.
- The claim that the reported performance of existing tools is "largely inflated" is based on the authors' re-implementations, which may not be faithful to the original methods.
- The generalizability of the findings to other DBP prediction tools not included in this benchmark is not established.
- The practical utility of the ensemble method in real-world settings is not demonstrated beyond the specific test sets used.