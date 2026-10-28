## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims, and suitability for a high-impact generalist journal
- **Shared manuscript claim summary** The authors present a computational pipeline combining structure-based (docking, structure-based pharmacophores) and ligand-based (pharmacophore) methods to predict compounds binding to estrogen receptor alpha (ERα), with the goal of identifying potential endocrine disrupting chemicals. They report that a consensus combination of docking and pharmacophore models outperforms individual models, achieving sensitivity of 0.81 and specificity of 0.54 on the EPA training database, with validation on two external datasets.
- **Visible evidence base** Full text including abstract, introduction, results, discussion, materials and methods, and conclusions. Tables 1-5, Figures 1-7, Supplementary Materials referenced.
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S5) referenced but not provided. The actual pharmacophore models and docking poses are not shown. The EPA database composition and the specific compound lists are not fully described. The manuscript does not provide the actual data or code used for the analysis.

## Reviewer
- **Overall assessment** This manuscript describes a carefully executed computational study combining multiple in silico methods for predicting ERα binding. The work is methodologically sound in its execution, with appropriate validation steps and consideration of potential biases. However, the study is largely confirmatory in nature, applying established methods (docking, pharmacophore modeling) in a combinatorial fashion without introducing fundamentally new approaches or insights. The reported performance metrics are modest, and the practical utility of the pipeline for prioritizing potential EDCs is not clearly demonstrated beyond what existing tools already offer. The manuscript is written clearly and would be of interest to a specialized audience in computational toxicology, but its novelty and broad significance are limited.

- **Who would be interested in the results, and why** Researchers in computational toxicology and environmental health sciences would be the primary audience. Those working on endocrine disruption prediction, particularly in regulatory contexts (e.g., prioritization of chemicals for testing under programs like the US EPA's Endocrine Disruptor Screening Program), would find the pipeline potentially useful. Computational chemists developing virtual screening workflows for nuclear receptors might also be interested in the comparative evaluation of docking and pharmacophore methods. However, the audience is narrow and specialized.

- **Major strengths** 
  1. The study uses a well-curated training dataset (EPA) and two external validation sets (NR-DBIND, EADB), which strengthens the reliability of the reported performance metrics.
  2. The systematic evaluation of multiple docking tools and scoring functions, followed by rational threshold selection using predictiveness curves, is methodologically rigorous.
  3. The combination of structure-based and ligand-based pharmacophores into a unified set (SBLB) is a sensible approach to maximize chemical space coverage.
  4. The authors explicitly address potential biases, including the imbalance between binders and non-binders in the training set and the pharmacological profile distribution of hits.
  5. The practical consideration of computational time in choosing between hierarchical and consensus protocols is useful for real-world applications.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and significance
- **Claim pointer** The manuscript claims that the proposed pipeline provides a useful approach for predicting ERα binding and identifying potential EDCs, implying added value over existing methods.
- **Evidence pointer** Abstract, Sections 2.4, 3.5, Conclusions
- **Concern** The pipeline combines well-established computational methods (docking, pharmacophore modeling) without introducing any fundamentally new methodology, algorithm, or conceptual framework. The individual components have been extensively used and validated in previous studies for nuclear receptor binding prediction. The combination of methods in consensus or hierarchical fashion is a standard practice in virtual screening. The reported performance (sensitivity 0.81, specificity 0.54 on the training set) is modest and does not clearly demonstrate superiority over existing tools such as the EPA's own CompTox dashboard models or other published QSAR models for ER binding. The authors do not provide a direct comparison with state-of-the-art existing models on the same datasets, which is essential to establish the added value of their pipeline.
- **Why it matters** For a high-impact journal, the work must offer a significant advance over the current state of the art. Without a clear demonstration of improved predictive performance or a novel methodological contribution, the study does not meet the threshold of originality and significance expected for Nature-level publications.
- **Resolution test** The authors would need to provide a direct, quantitative comparison of their pipeline's performance against existing state-of-the-art ERα binding prediction models (e.g., CERAPP, VirtualToxLab, or machine learning models) on the same external validation sets, demonstrating statistically significant improvement. Alternatively, they would need to introduce a genuinely novel methodological element that addresses a known limitation of current approaches.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness and validation
- **Claim pointer** The manuscript claims that the consensus protocol with a docking threshold of -6 achieves sensitivity of 0.81 and specificity of 0.54 on the EPA database, and that this represents the best-suited approach for toxicological screening.
- **Evidence pointer** Section 2.4.1, Table 5
- **Concern** The reported specificity of 0.54 for the consensus protocol on the EPA database is low, meaning that nearly half of the non-binders are predicted as binders. For a toxicological screening application, this would result in a large number of false positives requiring experimental follow-up. The authors acknowledge this trade-off but do not provide a clear justification for why this level of specificity is acceptable or how it compares to the practical requirements of chemical prioritization. Furthermore, the performance on the NR-DBIND external validation set shows a striking discrepancy: sensitivity of 1.0 and specificity of 0.005 (for threshold -6). This near-zero specificity on one external set raises serious questions about the generalizability of the pipeline. The authors attribute this to dataset imbalance but do not adequately address whether the pipeline is genuinely useful for prioritizing chemicals in a real-world regulatory context where false positive rates must be controlled.
- **Why it matters** The central claim of the manuscript is that the pipeline can effectively identify potential EDCs. If the pipeline cannot discriminate non-binders with reasonable accuracy on external datasets, its practical utility is severely compromised. The validation results as presented do not convincingly support the claim that the pipeline is "best suited" for toxicological screening.
- **Resolution test** The authors should provide a more balanced analysis of the pipeline's performance, including precision-recall curves and analysis of the trade-off between sensitivity and specificity. They should also discuss the practical implications of the observed false positive rates and provide guidance on how the pipeline should be used in a real screening context, including appropriate thresholds for different applications.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and transparency
- **Claim pointer** The manuscript describes the construction of the pipeline and the generation of pharmacophore models, claiming that the models are available in the Supplementary Materials.
- **Evidence pointer** Sections 4.3, 4.4, Supplementary Materials
- **Concern** The manuscript does not provide sufficient detail for full reproducibility. The specific parameters for pharmacophore generation (beyond what is briefly described), the exact composition of the training and test sets after curation, and the criteria for selecting the "best" pharmacophore from each cluster are not fully specified. The docking box coordinates are given for one structure (1a52) but it is unclear how they were adapted for the other structures. The manuscript states that the EPA database is available in Supplementary Materials, but this is not verifiable from the provided text. The pharmacophore models are said to be available in pml format, but the actual files are not provided in the manuscript.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publications. Without complete methodological details and access to the models and data, other researchers cannot independently verify the results or apply the pipeline to their own datasets.
- **Resolution test** The authors should provide complete methodological details, including all parameters used for each software tool, the full composition of all datasets (or clear instructions on how to access them), and the actual pharmacophore model files. Ideally, the code used for the analysis should be made available in a public repository.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation and discussion of results
- **Claim pointer** The manuscript states that "the combination of models performed better than each model taken individually" and that the consensus protocol is "best suited for our toxicological study."
- **Evidence pointer** Sections 2.4, 3.5, Tables 4-5
- **Concern** The claim that the combination performs better than individual models is not consistently supported by the data. While the consensus protocol does improve sensitivity compared to individual pharmacophore models, the improvement comes at the cost of substantially reduced specificity. The hierarchical protocol achieves high specificity but very low sensitivity. The authors do not provide a clear framework for evaluating the overall utility of each approach, such as a combined metric (e.g., Matthews correlation coefficient, F1 score) or a cost-benefit analysis that weighs the consequences of false positives versus false negatives in the context of EDC screening. The discussion of why the consensus protocol is "best suited" for toxicological studies is somewhat subjective and not fully justified by the quantitative results.
- **Why it matters** The central conclusion of the manuscript rests on the claim that the combined approach is superior. If this claim is not rigorously supported, the main contribution of the work is weakened.
- **Resolution test** The authors should provide a more comprehensive comparison of the different approaches using appropriate combined performance metrics and discuss the trade-offs in the context of specific screening applications. They should also consider whether the choice of threshold could be optimized to achieve a better balance between sensitivity and specificity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 2.2.1, Table 1
- **Evidence pointer** Section 2.2.1, Table 1
- **Issue** The manuscript states that "7 molecular docking tools" were explored but then lists only 6 scoring functions (smina-vina, smina-vinardo, smina-dkoes_scoring, smina-adt4, PLANTS, Surflex-dock). The smina software is used with 4 different scoring functions, which accounts for 4 of the 6 listed. The text should clarify whether "7 tools" refers to 7 distinct software packages or 7 scoring function/software combinations.
- **Required correction** Clarify the count of docking tools/scoring functions used. If smina with 4 scoring functions is counted as 4 tools, then the total should be 6, not 7. Alternatively, if a 7th tool was used, it should be listed.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 4.3.1
- **Evidence pointer** Section 4.3.1
- **Issue** The manuscript states that the bounding box coordinates were determined based on the crystal structure of 1a52 used as reference to align the remaining structures. However, it is not clear how the alignment was performed and whether the box coordinates were adjusted for each structure individually. This detail is important for reproducibility.
- **Required correction** Provide details on the structural alignment procedure and whether the docking box was defined separately for each protein structure or only once based on 1a52.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 2.4, Tables 4-5
- **Evidence pointer** Section 2.4, Tables 4-5
- **Issue** The manuscript reports sensitivity and specificity values but does not provide confidence intervals or statistical tests to assess whether differences between approaches are significant. Given the relatively small number of binders in the EPA database (223), the reported differences could be within the range of random variation.
- **Required correction** Provide confidence intervals for the reported performance metrics or perform appropriate statistical tests to support claims of superiority of one approach over another.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** Section 4.1.1
- **Evidence pointer** Section 4.1.1
- **Issue** The manuscript states that the EPA database was downloaded in February 2019 and that the platform has since been removed. It is not clear whether the data used in this study are still accessible to other researchers, which could affect reproducibility.
- **Required correction** Provide the exact version of the dataset used, or make the dataset available as a supplementary file or in a public repository.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion completeness
- **Affected element** Section 3.5
- **Evidence pointer** Section 3.5
- **Issue** The discussion compares the performance of the proposed pipeline with other studies but does not include a quantitative comparison with state-of-the-art machine learning models for ERα binding prediction, which typically report AUC values above 0.8. The authors acknowledge that machine learning methods perform well but do not directly compare their results with these methods on the same datasets.
- **Required correction** Include a direct quantitative comparison with at least one or two representative state-of-the-art models on the same external validation sets, or clearly state why such a comparison is not feasible.

## Risk / unsupported claims
- The claim that the consensus protocol is "best suited for our toxicological study" is not fully supported by the data, given the very low specificity observed on the NR-DBIND external validation set.
- The claim that "the combination of models performed better than each model taken individually" is only partially supported and depends on the specific performance metric considered.
- The manuscript does not demonstrate that the pipeline outperforms existing state-of-the-art methods for ERα binding prediction, which is essential to establish its added value.
- The practical utility of the pipeline for prioritizing chemicals in a regulatory context is asserted but not demonstrated with a realistic use case or cost-benefit analysis.
- The generalizability of the pipeline to novel chemical spaces beyond the training and validation sets is not established, given the low structural similarity between the training and external validation sets.