## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, footnotes) as provided
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality based solely on the supplied material
- **Shared manuscript claim summary** The authors present a machine learning framework using transcription factor binding and epigenomic features at gene promoters to predict disease-gene associations, with a focus on explainability to identify regulatory TFs and cell-type contexts, and to predict novel associations including non-coding RNAs.
- **Visible evidence base** Abstract, Introduction, Methods (partial), Results (partial), Discussion, Footnotes. Figures and supplementary materials are referenced but not provided.
- **Missing materials affecting confidence** Full Methods section (only partial text provided), all figures (Figure 1-4), supplementary tables and files, detailed model performance metrics, feature lists, and complete results for all disease gene sets.

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely problem: linking disease-associated genes to regulatory mechanisms in a cell-type-specific manner. The core idea of using TF binding and epigenomic features at promoters for explainable disease-gene prediction is novel and potentially valuable. However, the provided material is incomplete, and several key claims cannot be evaluated without the missing figures, supplementary data, and full methods. The validation strategies are reasonable in principle, but the evidence presented is insufficient to fully establish the case.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, disease genetics, and computational biology would be interested. The approach offers a way to generate hypotheses about disease-relevant TFs and cell types, which could aid in prioritizing experimental validation. Clinicians and translational researchers may also find the prognostic implications relevant.
- **Major strengths** The conceptual framing is strong, emphasizing explainability and cell-type context, which are often lacking in disease-gene prediction methods. The inclusion of non-coding RNAs is a notable advantage over ontology-based approaches. The use of multiple validation strategies (PubMed mining, GWAS, survival analysis) is commendable.
- **Major Concerns** Several concerns are identified below.
- **Minor Comments** Several minor issues are listed below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality is high, as the combination of TF binding and epigenomic features for explainable disease-gene prediction is not standard. Scientific importance is potentially high, given the need for mechanistic insights in disease genetics. Interdisciplinary readership is plausible, spanning genomics, bioinformatics, and clinical research. Technical soundness cannot be fully assessed due to missing methods and figures. Readability for nonspecialists is moderate, with some sections requiring domain expertise.
- **Recommendation posture** Supportive if technical concerns are resolved and full evidence is provided. Currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that random forest models achieve an average AUROC of 80% from five-fold cross-validation across disease gene sets.
- **Evidence pointer** Figure 1A, location not provided
- **Concern** The AUROC value is stated, but the variance across gene sets, the number of gene sets analyzed, and the criteria for selecting gene sets are not reported. Without these details, the robustness of the performance claim cannot be assessed.
- **Why it matters** A single average AUROC without distribution or context is insufficient to establish that the models perform well across diverse disease gene sets, which vary in size and biological coherence.
- **Resolution test** Provide a table or figure showing AUROC distributions, number of gene sets, and statistical comparisons to null models.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the null model with shuffled features yields an average AUROC of 55%, compared to 85% for unshuffled features.
- **Evidence pointer** Figure 1B, location not provided
- **Concern** The null model procedure is described as shuffling features, but the details of the shuffling scheme (e.g., within-gene vs. across-gene, number of permutations) are not provided. The difference between 55% and 85% is large, but without error bars or statistical testing, it is unclear if this is consistent across gene sets.
- **Why it matters** The null model is critical for demonstrating that the predictive signal is not an artifact of the feature set or model training. Incomplete description undermines confidence in the specificity claim.
- **Resolution test** Describe the shuffling procedure in full, report the distribution of null AUROC values, and include statistical significance tests.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that predicted non-coding RNA-disease associations are validated by PubMed abstract mining and GWAS data.
- **Evidence pointer** Figure 2A and 2B, location not provided
- **Concern** The validation results are mentioned, but the effect sizes, statistical methods, and the number of predictions tested are not reported. For PubMed mining, the criteria for co-occurrence and the background model for random expectations are unclear. For GWAS, the overlap method and significance thresholds are not specified.
- **Why it matters** Validation is essential to support the utility of the predictions. Without quantitative details, the strength of the validation cannot be judged.
- **Resolution test** Provide detailed methods for both validation approaches, including statistical tests, effect sizes, and the number of predictions evaluated.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that survival analysis of top predictive TFs for BLCA shows significant results with p < 0.05.
- **Evidence pointer** Figure 3, location not provided
- **Concern** Only one cancer type (BLCA) is shown, and the analysis is described as showing "some" TFs with promising results. The number of TFs tested, the multiple testing correction, and the criteria for selecting top predictors are not described. The statement that predicted genes do not show promising results is also concerning, as it weakens the overall utility claim.
- **Why it matters** Survival analysis is used as a functional validation, but incomplete reporting makes it impossible to assess whether the results are robust or selective.
- **Resolution test** Report the full survival analysis results for all cancers, including the number of TFs tested, multiple testing corrections, and the proportion of significant findings.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The claim that the method can predict novel disease-gene associations, including non-coding RNAs, with regulatory insights.
- **Evidence pointer** Supplementary Table 1 and 2, location not provided
- **Concern** The case studies (ZNF366, LDB1) are interesting, but the selection criteria for these examples are not stated. It is unclear whether these are representative or cherry-picked. The supplementary tables are referenced but not provided, so the full set of predictions and their quality cannot be evaluated.
- **Why it matters** The novelty of the approach depends on the breadth and reliability of the predictions. Without access to the full results, the generalizability of the method is unverified.
- **Resolution test** Provide the full supplementary tables and describe the criteria for selecting case studies, including how many predictions were examined.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section
- **Evidence pointer** Methods, location not provided
- **Issue** The description of feature score calculation is dense and lacks a clear summary of the final feature matrix dimensions and preprocessing steps.
- **Required correction** Add a brief summary of the feature matrix (number of genes, features, normalization steps) and a flowchart or schematic of the pipeline.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section
- **Evidence pointer** Results, location not provided
- **Issue** The results section is brief and does not report quantitative outcomes for most disease gene sets, focusing only on selected examples.
- **Required correction** Include a summary table of model performance across all gene sets, with key statistics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion of "divergence and convergence of cell types" is interesting but not clearly tied to specific results or examples.
- **Required correction** Provide concrete examples from the results to illustrate this point.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods, location not provided
- **Issue** The software versions and parameters for the machine learning packages are not specified.
- **Required correction** List all software packages, versions, and key parameters used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract is dense and could benefit from a clearer statement of the main finding and its implications.
- **Required correction** Revise the abstract to include a specific example of a novel prediction and its validation.

## Risk / unsupported claims
- The claim that the method "highlights the link between TF binding patterns and diseases in the context of cell types" is only supported by two case studies, and the full scope is not assessable.
- The claim that "such links to be genuine and potentially useful for prognosis" is based on limited survival analysis for one cancer type and is not fully supported.
- The claim that the approach "provides regulatory insights" is plausible but not systematically demonstrated across the full set of predictions.
- The claim that the method can predict non-coding RNA-disease associations is supported only by indirect validation (PubMed, GWAS) and not by direct experimental evidence.
- The overall performance claim of 80% AUROC is not robustly supported without distribution and variance data.