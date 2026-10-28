## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific validity, methodological soundness, evidence sufficiency, and clarity of claims as presented in the provided text
- **Shared manuscript claim summary** The authors present CaVepP53, a TP53-specific variant effect predictor fine-tuned from the ESMC protein language model on deep mutational scanning and ClinVar data. They claim superior performance over general-purpose predictors (AlphaMissense, PrimateAI-3D), demonstrate experimental validation of 22 mutations via a competitive growth assay in prime-edited HCT-116 cells, identify 7 novel functional variants, and extend the framework to five additional cancer-related genes.
- **Visible evidence base** Abstract, full introduction, results narrative, discussion, methods descriptions, figure references (Figures 1-4, S1-S8), table references (Tables 1, S1-S5), data availability link
- **Missing materials affecting confidence** Actual figures and tables not provided; quantitative performance metrics (exact ACC, precision, F1, MCC values) not fully specified in text; details of the Stiewe dataset integration and filtering criteria incomplete; no code or model architecture details beyond high-level description; no statistical test details for experimental validation; no comparison of computational cost or runtime

## Reviewer

- **Overall assessment** The manuscript addresses an important problem in variant effect prediction by developing a gene-specific approach that integrates protein language models with perturbation-based functional data. The concept is timely and the experimental validation strategy is commendable. However, the current text lacks sufficient quantitative detail to fully assess the claims. Key performance metrics are referenced but not reported in the text, the experimental validation section is underdescribed, and the generalization claims to five additional genes are presented without supporting data in the visible text. The methodological novelty over existing fine-tuning approaches is not clearly delineated. The manuscript has potential but requires substantial additional detail and analysis to establish the case.

- **Who would be interested in the results, and why** Cancer geneticists and clinical genomics researchers would be interested in improved TP53 variant classification, particularly for reclassifying variants of uncertain significance. Computational biologists developing variant effect predictors would value the gene-specific fine-tuning approach and the integration of perturbation data. Precision oncology practitioners could benefit from more accurate pathogenicity calls for clinical decision-making. The framework's extension to other cancer genes broadens relevance to the wider cancer genomics community.

- **Major strengths** The focus on TP53, a clinically critical gene with abundant variant data, is well chosen. The integration of perturbation-based DMS data with a modern protein language model addresses a recognized limitation of correlation-based training labels. The experimental validation using prime editing and a competitive growth assay provides functional evidence beyond computational benchmarks. The ablation studies (DMS vs ClinVar, CNN baseline) are well designed to isolate the contributions of data source and model architecture. The extension to additional genes suggests potential generalizability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "CaVepP53 consistently outperformed competing models" with "nearly 6% improvement in MCC over AM"
- **Evidence pointer** Figure 2c, Table S2; location not provided for exact values
- **Concern** The text references performance metrics (ACC, precision, F1, MCC, ROC-AUC) but does not report the actual numerical values in the manuscript body. The claim of "nearly 6% improvement in MCC" is stated without the baseline MCC value or confidence intervals. Without these numbers, the reader cannot evaluate the magnitude or statistical significance of the improvement.
- **Why it matters** The central claim of the manuscript is superior predictive performance. Without explicit quantitative results and appropriate uncertainty measures, this claim cannot be verified or compared against existing literature.
- **Resolution test** Provide a table or text listing exact values for all metrics (ACC, precision, recall, F1, MCC, ROC-AUC) for CaVepP53, AM, and PrimateAI-3D on the same test set, including confidence intervals or standard deviations across cross-validation folds.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation rigor
- **Claim pointer** "Competitive growth assay validation of 22 mutations... including 7 functional novel variants absent in the ClinVar database"
- **Evidence pointer** Figure 4, Tables S4-S5; location not provided for detailed results
- **Concern** The experimental validation section is described only at a high level. The text states that 22 mutations were tested and 15/22 were correctly classified, but does not describe the selection criteria for the 19 additional mutations beyond the initial 3 controls, the statistical methods used to determine significance of growth differences, the number of replicates, or how "correct" classification was defined against the experimental outcome. The in vivo mouse experiments for 3 mutants are mentioned but no results are presented.
- **Why it matters** Experimental validation is the key differentiator of this work from purely computational studies. Insufficient detail prevents assessment of whether the validation is robust and whether the conclusions drawn from it are justified.
- **Resolution test** Provide a detailed description of the experimental design, including mutation selection criteria, replicate numbers, statistical tests used, effect sizes with confidence intervals, and clear definitions of functional vs non-functional outcomes. Present the in vivo results with appropriate histological and molecular evidence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability claim
- **Claim pointer** "We further extended this framework to five additional cancer-related genes (VHL, ATM, BRCA1, RAD51C, and BAP1)"
- **Evidence pointer** Figure S7, Table S3; location not provided for detailed results
- **Concern** The extension to five additional genes is presented as a single sentence in the abstract and a brief mention in the results, with all supporting data relegated to supplementary figures. The text does not describe the DMS datasets used for these genes, the training procedure, the evaluation metrics, or how performance compares to TP53. The claim of "robust performance" is not quantified in the main text.
- **Why it matters** The generalizability of the framework is a major selling point. Without adequate presentation of these results, the claim that this approach transfers to other genes is not established.
- **Resolution test** Include a main-text figure or table showing performance metrics for all five genes, with dataset descriptions, training details, and comparison to baseline models. Discuss any gene-specific challenges or failures.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological novelty
- **Claim pointer** "integrating protein language models with experimentally validated functional data" and "perturbation-informed"
- **Evidence pointer** Methods section, Figure 1
- **Concern** The methodological contribution is described as fine-tuning ESMC on DMS data with an added classification head and Euclidean distance-based pathogenicity scoring. This appears to be a standard fine-tuning approach applied to a new dataset. The novelty relative to existing fine-tuned PLM predictors is not clearly articulated. The Euclidean distance metric is acknowledged to correlate "only modestly" with functional scores, raising questions about its utility as a pathogenicity measure.
- **Why it matters** For a high-impact journal, the methodological advance must be clearly distinguished from incremental applications of existing techniques. The current description does not establish what is fundamentally new.
- **Resolution test** Clearly articulate the specific methodological innovations, compare against other fine-tuned PLM approaches (not just zero-shot models), and either demonstrate the added value of the Euclidean distance metric or remove it as a claimed contribution.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data leakage and evaluation bias
- **Claim pointer** "completely independent external test dataset containing 3945 missense mutations... after rigorously excluding any variants overlapping with the internal training and test datasets"
- **Evidence pointer** Results section, Figure 2f; location not provided for exclusion details
- **Concern** The text claims rigorous exclusion of overlapping variants, but the details of how this was done are not provided. Specifically, it is unclear whether the exclusion was performed at the variant level (exact amino acid substitution) or at the position level (any variant at the same residue). Position-level exclusion is more stringent and appropriate. Additionally, the ClinVar-derived training data may contain variants that were originally classified based on functional assays similar to those used in the external test set, creating potential circularity.
- **Why it matters** Data leakage is a common source of inflated performance estimates in variant effect prediction. The evaluation's credibility depends on the rigor of the exclusion procedure.
- **Resolution test** Describe the exact exclusion criteria (variant-level vs position-level), report the number of variants excluded at each step, and discuss potential circularity between training labels and external test labels.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, statistical analysis
- **Evidence pointer** Statistical Analyses section
- **Issue** The text states "For comparisons between ewo groups" which appears to be a typo for "two groups." Additionally, the statistical methods are described only briefly, with no mention of multiple testing correction despite many comparisons.
- **Required correction** Fix the typo and provide a more complete description of statistical tests, including multiple testing correction where applicable.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model training details
- **Evidence pointer** Table 1, Model Training section
- **Issue** The text mentions hyperparameters are summarized in Table 1, but the table is not visible in the provided text. Key details such as batch size, learning rate schedule specifics, and hardware used are not described in the text.
- **Required correction** Ensure Table 1 includes all relevant hyperparameters and that the text describes the computational environment for reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, saturation mutagenesis
- **Evidence pointer** Figure 3, Results section
- **Issue** The text states that 2737 of 7467 variants were classified as pathogenic and predominantly located in the DNA-binding domain, but does not discuss the biological plausibility of the 4694 benign predictions, particularly for variants in known functional regions outside the DBD.
- **Required correction** Add a brief discussion of the distribution of predictions across protein domains and any unexpected patterns.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion, limitations
- **Evidence pointer** Discussion section
- **Issue** The limitations section mentions only two points (dynamic cellular systems and synonymous mutations). Other potential limitations, such as the reliance on a single cell line for validation, the use of growth assays as a proxy for pathogenicity, and the potential for off-target effects in prime editing, are not discussed.
- **Required correction** Expand the limitations discussion to address these additional concerns.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "we present CaVepP53" and describes the model, but does not mention the experimental validation or the extension to other genes until the final sentence. The abstract could better balance the computational and experimental contributions.
- **Required correction** Consider restructuring the abstract to more clearly highlight the experimental validation as a key contribution.

## Risk / unsupported claims
- The claim of "causal prediction" in the title is not supported by the methods described, which are correlational in nature (classifying variants based on learned patterns from labeled data). The term "causal" is not defined or justified anywhere in the text.
- The statement "achieving higher accuracy, precision, and F1-score" is made without reporting specific values in the text, making it unverifiable from the provided material.
- The claim of "7 functional novel variants absent in the ClinVar database" is presented without showing the experimental data for these specific variants or how novelty was confirmed against other databases.
- The generalization to five additional genes is claimed but no performance data for these genes is presented in the visible text.
- The statement that the model "enables accurate, interpretable, scalable variant effect prediction" is an overreach given that interpretability is only weakly supported by the Euclidean distance metric, which the authors acknowledge correlates only modestly with functional scores.
- The in vivo tumorigenesis experiments for 3 mutants are mentioned but no results are presented, making the claim of "confirming their tumorigenic potential in vivo" unsupported in the visible text.
- The assertion that DMS data provide "causal" labels is not justified, as the functional assays measure correlation between variant and phenotype under specific experimental conditions, not causation in a strict sense.