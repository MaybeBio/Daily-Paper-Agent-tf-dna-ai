## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, reproducibility, and presentation quality
- **Shared manuscript claim summary** The authors benchmark eleven recent machine learning-based DNA-binding protein (DBP) identification tools alongside traditional tools (BLAST, ScanProsite, HMMER), identify data leakage in existing datasets, introduce new evaluation datasets (BTD, EBTD, HBTD), and propose an ensemble method combining the two best tools with BLAST that improves DBP identification performance.
- **Visible evidence base** Abstract, Introduction (Section 2), Benchmarked Tools (Section 3), Current Dataset Details and Limitations (Section 4), Benchmarking Dataset Development (Section 5), Tool Evaluation (Section 6), Error Analysis (Section 7), Discussion and Recommendations (Section 8), Conclusion (Section 9), Footnotes
- **Missing materials affecting confidence** Full tables (Tables 1-6) and figures (Figures 1-6) referenced but not fully visible; Supplementary Data files (S1-S9) not provided; GitHub repository contents not independently verified; exact hyperparameter settings, training configurations, and computational resources not fully described

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely problem: the reliability of computational DBP identification tools. The authors identify a critical issue, data leakage in existing benchmark datasets, and provide evidence that reported performances are inflated. The introduction of new datasets and the ensemble approach are potentially valuable contributions. However, the manuscript has significant methodological gaps, particularly in the reproducibility of the benchmarking pipeline, the handling of class imbalance, and the statistical rigor of comparisons. The claims of "unbiased" benchmarking are not fully supported given the incomplete description of experimental controls and the inability to verify several key results from the provided materials.

- **Who would be interested in the results, and why** Computational biologists developing or using DBP prediction tools; researchers in protein function annotation; machine learning practitioners working on biological sequence classification; reviewers of bioinformatics tools who need to assess the validity of reported performance metrics. The findings on data leakage and inflated performance are broadly relevant to any protein classification task.

- **Major strengths** 
  1. The identification and quantification of data leakage in widely used benchmark datasets is a significant and actionable contribution.
  2. The introduction of new evaluation datasets (BTD, EBTD, HBTD) with controlled similarity thresholds addresses a real gap in the field.
  3. The systematic comparison of eleven tools under unified training conditions is a substantial undertaking.
  4. The error analysis (sequence length, E-ratio, motif score) provides useful insights into model limitations.
  5. The ensemble method is simple, practical, and demonstrates clear added value over individual tools.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors claim to have benchmarked eleven tools and report specific performance metrics (e.g., MCC scores in Tables 3-6), but the manuscript does not provide sufficient detail on how each tool was configured, trained, and evaluated.
- **Evidence pointer** Section 3, Section 6, Tables 3-6 (location not provided)
- **Concern** The manuscript states that tools were trained on their respective datasets and later on a merged dataset, but does not describe the exact training procedures, hyperparameter settings, early stopping criteria, or computational resources used. For deep learning tools (e.g., LSTM-CNN_Fusion, PDBP-Fusion), the number of epochs, batch size, learning rate, and optimizer are not specified. For classic ML tools (e.g., Local-DPP, DNABP), the number of trees, tree depth, and feature selection procedures are not detailed. Without this information, the benchmarking results cannot be reproduced or independently verified.
- **Why it matters** Reproducibility is a core requirement for benchmarking studies. If the training configurations are not specified, other researchers cannot replicate the results, and the validity of the performance comparisons is questionable. The authors themselves note that some tools had code inconsistencies, which further underscores the need for precise documentation.
- **Resolution test** Provide a supplementary table or appendix detailing the exact configuration for each tool, including all hyperparameters, training/validation splits, and any modifications made to the original code. Ideally, provide a configuration file or script for each tool that can be run to reproduce the reported results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that the ensemble method "significantly enhances" DBP identification capability and that the performance differences between tools are meaningful, but no statistical significance testing is reported.
- **Evidence pointer** Section 6.5, Table 6, Figure 3 (location not provided)
- **Concern** The manuscript reports MCC scores, sensitivity, and specificity for each tool and for the ensemble, but does not provide confidence intervals, standard deviations, or statistical tests (e.g., McNemar's test, paired bootstrap) to determine whether the observed differences are statistically significant. The claim that the ensemble "significantly enhances" performance is not supported by any statistical evidence. Additionally, the comparison between tools is based on a single train-test split, which does not account for variance due to data sampling.
- **Why it matters** Without statistical testing, the reader cannot determine whether the reported performance differences are robust or due to chance. This is particularly important given the moderate performance gains reported (e.g., MCC improvement from 0.4493 to 0.5079). The field of bioinformatics benchmarking increasingly expects statistical rigor, and its absence weakens the manuscript's conclusions.
- **Resolution test** Perform statistical significance testing (e.g., McNemar's test for paired binary predictions, or bootstrap resampling for MCC differences) between the top tools and the ensemble. Report confidence intervals for all key metrics. If possible, use multiple train-test splits or cross-validation to assess variance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset validity
- **Claim pointer** The authors claim that BTD is a "more realistic and unbiased" dataset, but the construction process may introduce new biases that are not fully addressed.
- **Evidence pointer** Section 5, Figure 1 (location not provided)
- **Concern** The BTD positive set is constructed from UniProtKB proteins with a review score of 5, which are manually annotated. This is a reasonable source, but the authors do not report the taxonomic distribution, functional diversity, or sequence length distribution of the final BTD set compared to the original datasets. The negative set is constructed by excluding potential DBPs from Swiss-Prot, but the authors do not report how many proteins were excluded and whether the remaining negative set is representative of the true non-DBP population. Additionally, the filtering step that removes non-DBPs with over 40% similarity to BTD positives may introduce a bias by removing proteins that are structurally or functionally similar to DBPs but are not actually DNA-binding, which could make the negative set artificially easy.
- **Why it matters** The validity of the entire benchmarking study depends on the quality and representativeness of the BTD dataset. If the dataset has hidden biases, the performance rankings of the tools may not generalize to real-world applications. The authors' claim of "unbiased" evaluation is not fully supported without a thorough characterization of the dataset.
- **Resolution test** Provide a detailed characterization of BTD, including taxonomic distribution, sequence length distribution, functional annotation distribution, and a comparison with existing datasets. Report the number of proteins excluded at each filtering step and the impact of the similarity-based filtering on the negative set. Consider providing a version of BTD without the similarity-based negative filtering to assess its impact.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of comparison
- **Claim pointer** The authors benchmark eleven recent ML tools and three traditional tools, but the selection criteria for these tools are not clearly justified, and some potentially relevant tools may be missing.
- **Evidence pointer** Section 3, Table 1 (location not provided)
- **Concern** The manuscript does not explain how the eleven tools were selected. Were they all published within a certain time frame? Were they the most cited? Were they the most accessible? The authors note that six out of eleven tools did not have code available, which raises the question of whether the selection was biased toward tools with available code. Additionally, the authors do not compare against more recent tools that may have been published after their selection cutoff, nor do they include tools based on protein language models that are not specifically designed for DBP identification but could be adapted for this task.
- **Why it matters** A benchmarking study should be comprehensive and transparent about its selection criteria. If the selection is biased, the conclusions about the "state of the art" may be incomplete or misleading. The authors' recommendation that "future tools should provide code" is valid, but the selection process should be documented to allow readers to assess the completeness of the comparison.
- **Resolution test** Provide a clear rationale for tool selection, including search criteria, inclusion/exclusion criteria, and the date of the literature search. Consider including a broader set of tools, including those without available code, and discuss the potential impact of their exclusion on the conclusions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The authors claim that their findings on data leakage and inflated performance apply broadly to DBP identification and potentially to other protein classification tasks, but the evidence is limited to a specific set of tools and datasets.
- **Evidence pointer** Section 4, Section 8 (location not provided)
- **Concern** The data leakage analysis is based on four datasets (PDB1075, PDB186, PDB14K, PDB2272) and eleven tools. While the finding that 85/93 and 1007/1153 test samples have high similarity to training samples is striking, the authors do not systematically analyze the impact of different similarity thresholds (e.g., 30%, 50%) on the reported performance inflation. The claim that "the same benchmarking strategy should be readily applicable to studying these problems" is plausible but not demonstrated.
- **Why it matters** The manuscript's broader implications depend on the generalizability of the findings. If the data leakage issue is specific to these datasets or tools, the recommendations may not be widely applicable. A more systematic analysis of the leakage threshold and its impact would strengthen the conclusions.
- **Resolution test** Perform a sensitivity analysis using different similarity thresholds (e.g., 20%, 30%, 50%) to show how the degree of leakage varies and how it affects tool performance. Discuss the implications for other protein classification tasks and provide guidance on how to apply the benchmarking strategy to new problems.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 6.5, ensemble method description
- **Evidence pointer** Section 6.5 (location not provided)
- **Issue** The description of the majority voting ensemble is brief. It is unclear whether the voting is simple majority (2 out of 3) or weighted, and how ties are resolved.
- **Required correction** Provide a clear description of the voting scheme, including how ties are handled and whether any weighting is applied.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 7.2, E-ratio analysis
- **Evidence pointer** Section 7.2, Figure 5 (location not provided)
- **Issue** The E-ratio analysis is described in detail, but the interpretation of the results is brief. The authors state that misclassified samples have lower E-ratios, but do not discuss the practical implications of this finding for tool development.
- **Required correction** Expand the discussion of the E-ratio results, including what they mean for the design of future DBP prediction tools.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 8, Discussion
- **Evidence pointer** Section 8 (location not provided)
- **Issue** The discussion of AlphaFold is brief and somewhat tangential. The authors mention it as a potential source of structural features but do not provide a concrete proposal for how it could be integrated into DBP prediction.
- **Required correction** Either expand the discussion of AlphaFold with a concrete proposal for its use, or remove it to keep the discussion focused.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 6.4, BLAST configuration
- **Evidence pointer** Section 6.4 (location not provided)
- **Issue** The BLAST-based prediction method is described, but the specific BLAST parameters (e.g., word size, gap penalties, matrix) are not provided.
- **Required correction** Specify the exact BLAST parameters used, or provide a configuration file in the GitHub repository.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract (location not provided)
- **Issue** The abstract states that the authors "recommend solutions" for the identified issues, but the specific recommendations are not summarized in the abstract.
- **Required correction** Briefly summarize the key recommendations in the abstract to give readers a clearer sense of the manuscript's contributions.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1 (reproducibility of tool configurations) must be resolved before the benchmarking results can be considered reliable.
  - R1-M2 (lack of statistical testing) must be resolved before the claim of "significant" improvement can be accepted.
  - R1-M3 (dataset bias characterization) must be resolved before the claim of "unbiased" evaluation can be accepted.

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The identification of data leakage in existing DBP datasets is a valuable and somewhat novel contribution, but the overall approach of benchmarking tools is not new. The ensemble method is simple and not particularly innovative.
  - **Scientific importance**: High. The findings on data leakage have implications for the entire field of DBP prediction and potentially for other protein classification tasks. The new datasets are a useful resource.
  - **Interdisciplinary readership**: Moderate. The manuscript is primarily of interest to computational biologists and bioinformaticians. The broader molecular biology community may find the findings relevant but the technical detail may be a barrier.
  - **Technical soundness**: Currently insufficient. The lack of detailed experimental configuration and statistical testing undermines the technical rigor of the study.
  - **Readability for nonspecialists**: Moderate. The manuscript is generally well-written, but the technical detail in Sections 3 and 6 may be challenging for nonspecialists. The key findings on data leakage are presented clearly.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important problem and provides a useful resource, but the current version lacks the methodological detail and statistical rigor required for a high-impact publication. The authors should address R1-M1, R1-M2, and R1-M3 before the case is fully established.

## Risk / unsupported claims
- The claim that the ensemble method "significantly enhances" DBP identification capability is unsupported without statistical testing.
- The claim that BTD is "unbiased" is not fully supported without a thorough characterization of the dataset and its potential biases.
- The claim that the reported performance of existing tools is "inflated" is supported by the leakage analysis, but the magnitude of the inflation is not quantified.
- The claim that the benchmarking strategy is "readily applicable" to other protein classification problems is plausible but not demonstrated.
- The performance of PB_DBP could not be verified due to the unavailability of its training dataset, and this limitation is not discussed in the main text.