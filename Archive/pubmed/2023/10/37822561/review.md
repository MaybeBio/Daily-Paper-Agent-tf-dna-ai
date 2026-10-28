## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusion sections. Figures and tables are referenced but not fully visible in the provided text.
- **Assessment boundary** Evaluation is limited to the scientific content, methodology, results, and claims as presented in the manuscript text. Code functionality, web service usability, and reproducibility were not independently verified.
- **Shared manuscript claim summary** The authors propose ASCARIS, a method for featurizing single amino acid variations (SAVs) using 30 types of positional functional annotations from UniProt, structural features, and physicochemical properties. They demonstrate that these features carry information relevant to variant effects and that machine learning models trained on ASCARIS representations achieve competitive and complementary performance compared to state-of-the-art variant effect predictors.
- **Visible evidence base** Statistical analyses of feature-variant effect associations (Fisher's exact tests), ablation studies across feature combinations, classifier comparisons, benchmark evaluations against established predictors on multiple datasets, and a deep mutational scanning benchmark.
- **Missing materials affecting confidence** Full figures (Fig. 1-5) and supplementary tables (Table S1-S6) are referenced but not fully visible. Detailed hyperparameter optimization results (Table S4) and benchmark dataset descriptions (Supplementary Information S5) are not fully accessible. Code implementation details and validation of the web service were not independently tested.

## Reviewer
- **Overall assessment** The manuscript presents a novel and potentially useful contribution to the field of variant effect prediction by introducing a function-centric featurization approach based on positional annotations and structural information. The method is well-motivated, and the authors provide a thorough evaluation demonstrating the utility of their representations. The work is technically sound in its core methodology, though several concerns regarding dataset construction, evaluation rigor, and generalizability need to be addressed. The writing is clear and accessible, with appropriate context provided for nonspecialist readers. Overall, this is a solid contribution that could be suitable for publication after addressing the concerns outlined below.

- **Who would be interested in the results, and why** Researchers in computational biology, bioinformatics, and genomics, particularly those working on variant effect prediction, protein structure-function relationships, and integrative modeling of genomic data. The method's interpretability and complementary nature to existing predictors make it relevant for clinical genetics applications and for developers of multi-omics integration frameworks.

- **Major strengths**
  1. Novel featurization approach that leverages underutilized positional functional annotations, providing a fresh perspective compared to sequence conservation-based methods.
  2. Comprehensive evaluation including ablation studies, multiple benchmark datasets, and comparison against a wide range of state-of-the-art predictors.
  3. Practical utility demonstrated through open-source tool availability and web service implementation.
  4. Interpretable feature vectors that can be combined with other approaches, enhancing flexibility for downstream applications.
  5. Clear and well-structured writing with appropriate context for nonspecialist readers.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and bias
- **Claim pointer** The authors claim that combining data from three databases (UniProt, ClinVar, PMD) into a unified neutral/deleterious classification is valid and that the resulting dataset is suitable for training predictive models.
- **Evidence pointer** Section 2.1 (Data), Table 2c
- **Concern** The authors combine data from three databases with different annotation criteria. UniProt "polymorphisms" are labeled neutral, but these may include variants with unknown or uncharacterized effects. ClinVar classifications are based on clinical significance, while PMD uses stability/activity changes. These different labeling schemes may introduce systematic biases. The authors do not analyze inter-database label agreement or potential conflicts beyond removing explicit contradictions.
- **Why it matters** If the training labels are noisy or biased, the reported performance metrics may not reflect true generalization to real-world variant effect prediction tasks. The claim that the combined dataset improves performance (Table 2c) could be an artifact of dataset size rather than label quality.
- **Resolution test** Provide a detailed analysis of label agreement between databases for overlapping variants, quantify potential label noise, and demonstrate that performance improvements from combining datasets are not due to dataset size alone. Consider reporting performance on each database's test set separately.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evaluation methodology
- **Claim pointer** The authors claim that ASCARIS achieves competitive and complementary performance against state-of-the-art predictors, particularly on challenging cases.
- **Evidence pointer** Section 3.2.3, Table 3, Fig. 5
- **Concern** The benchmark comparisons appear to use different training/test splits for ASCARIS compared to the competing methods. For the MutationTaster dataset, the authors filtered their training data temporally, but it is unclear whether competing methods were retrained under the same conditions or used their pre-trained models. For the deep mutational scanning benchmark, the authors removed overlapping data points from their training set, but the competing methods' training data may have included these variants.
- **Why it matters** Inconsistent training conditions can lead to unfair comparisons. If competing methods were not subject to the same data filtering, the reported performance differences may reflect data leakage or training set composition rather than methodological superiority.
- **Resolution test** Clearly describe the training conditions for all methods in each benchmark. Ideally, retrain all methods under identical conditions or use pre-trained models consistently. Provide a detailed description of data splits and any filtering applied to each method's training data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and external validation
- **Claim pointer** The authors suggest that ASCARIS representations can be used for various purposes beyond variant effect prediction, including multi-omics integration and precision medicine.
- **Evidence pointer** Section 4 (Conclusion)
- **Concern** The manuscript only demonstrates the utility of ASCARIS for binary variant effect classification. No evidence is provided for its effectiveness in other proposed applications, such as regression tasks, multi-omics integration, or clinical decision support. The claim of broad applicability is speculative.
- **Why it matters** The stated potential applications are ambitious and may not be achievable with the current feature set. Overstating applicability without evidence could mislead potential users.
- **Resolution test** Either provide proof-of-concept demonstrations for at least one additional application (e.g., continuous severity prediction, integration with gene expression data) or temper the claims about broader applicability in the conclusion.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and feature importance
- **Claim pointer** The authors claim that ASCARIS produces interpretable feature vectors where each dimension corresponds to a predefined property.
- **Evidence pointer** Section 3.2.1, Fig. S4
- **Concern** While the feature vectors are indeed interpretable in principle, the authors do not provide a detailed analysis of which features are most informative for variant effect prediction. The feature importance analysis (Fig. S4) is only briefly mentioned, and no biological interpretation of the important features is provided.
- **Why it matters** Interpretability is a key claimed advantage of the method. Without a deeper analysis of which annotations and structural features drive predictions, the practical value of interpretability is not fully realized.
- **Resolution test** Provide a more detailed feature importance analysis, including discussion of which specific annotation types (e.g., active sites vs. glycosylation sites) are most predictive and why. Consider providing examples of how the feature vectors can be used to generate biological hypotheses.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methodology
- **Affected element** Section 2.3.4 (Mapping of positional annotations)
- **Evidence pointer** Section 2.3.4
- **Issue** The description of how spatial distances are calculated between SAVs and annotated regions is somewhat vague. It is unclear how distances to region-based annotations (e.g., domains) are computed when the region spans multiple residues.
- **Required correction** Clarify the distance calculation methodology, including how representative residues are chosen for region-based annotations and how multiple annotated regions of the same type are handled.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.1.4 (Positional sequence annotation-based evaluation)
- **Evidence pointer** Section 3.1.4, Fig. 4b
- **Issue** The authors report p-values for associations between annotation categories and variant effects but do not provide effect sizes or confidence intervals. The practical significance of the associations is unclear.
- **Required correction** Report effect sizes (e.g., odds ratios) and confidence intervals alongside p-values to better convey the magnitude of associations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Comparison fairness
- **Affected element** Section 3.2.3 (Performance comparison with other methods)
- **Evidence pointer** Table 3
- **Concern** The comparison table does not include standard deviations or confidence intervals for the performance metrics, making it difficult to assess whether observed differences are statistically significant.
- **Required correction** Report variability measures (e.g., standard deviation across cross-validation folds) or perform statistical significance testing for performance differences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Tool documentation
- **Affected element** Section 3.4 (SAV representation construction tool)
- **Evidence pointer** Section 3.4
- **Issue** The manuscript mentions that the tool is available but does not provide details on input/output formats, dependencies, or example usage beyond a brief description.
- **Required correction** Provide a more detailed description of the tool's usage, including example commands, expected input formats, and output file structure. Consider including a small example in the main text or supplementary materials.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and clarity
- **Affected element** Section 3.1.4
- **Evidence pointer** Section 3.1.4, paragraph 2
- **Issue** The sentence "SAV does not tstructural properties" appears to be a typographical error and is grammatically incorrect.
- **Required correction** Correct the typo and rephrase the sentence for clarity.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Missing details on data preprocessing
- **Affected element** Section 2.1 (Data)
- **Evidence pointer** Section 2.1
- **Issue** The manuscript does not describe how variants from different databases were mapped to a common reference (e.g., genome build, transcript version) or how potential mismatches were resolved.
- **Required correction** Provide details on the variant mapping and harmonization process, including any filtering steps applied to resolve inconsistencies.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Computational efficiency
- **Affected element** Section 3.4 (SAV representation construction tool)
- **Evidence pointer** Section 3.4
- **Issue** The manuscript does not report computational performance metrics (e.g., time per variant, memory usage) for the tool, which could be important for users processing large variant sets.
- **Required correction** Include basic performance benchmarks for the tool, such as average processing time per variant and total runtime for a representative dataset.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.4 (Classification)
- **Evidence pointer** Section 2.4
- **Issue** The manuscript does not specify the random seed or provide the exact code used for model training, which could hinder reproducibility.
- **Required correction** Provide the random seed used for all experiments and ensure the code repository includes the exact scripts used for model training and evaluation.

## Risk / unsupported claims
- The claim that ASCARIS can be used for "omics-based modeling of cells or patients for precision medicine" is not supported by any experimental evidence in the manuscript.
- The statement that "the noise in data is expected to be low" due to curated annotations is an assumption that is not empirically verified.
- The claim that ASCARIS produces "concise, effective, interpretable, and reusable variant representations" is only partially supported; interpretability is demonstrated structurally but not biologically.
- The assertion that the AlphaFold version performs better due to "high quality structure predictions with almost complete coverage" is speculative and not directly tested.
- The generalizability of the method to non-human organisms is implied through the inclusion of PMD data but not explicitly validated.
- The claim of "competing and complementary performance" is supported by the benchmarks, but the degree of complementarity is not quantified beyond Venn diagram analysis.