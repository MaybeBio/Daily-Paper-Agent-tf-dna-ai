## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, supplementary figure/table legends as referenced)
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with stated evidence; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors propose ACNVE-K, an encoding method combining k-mer decomposition with asymmetric covariance natural vectors, and use it with three machine learning algorithms (GB, RF, XGBoost) to build five models predicting transcription factor identity, target gene status, and regulatory direction (activation/inhibition) in human and mouse genomes, with claims of high predictive performance and cross-species generalizability.
- **Visible evidence base** Main text figures (Figs 1–7), supplementary tables S1–S25, supplementary figures S1–S13, and GitHub code repositories as referenced
- **Missing materials affecting confidence** Supplementary tables and figures are referenced but not provided in the submitted material; exact equations for the asymmetric covariance features are indicated but not fully displayed; detailed hyperparameter settings and data preprocessing steps are only partially described; no baseline comparison details for the benchmarked methods are given beyond a summary statement

## Reviewer
- **Overall assessment** The manuscript presents a novel encoding strategy that extends natural vector methods to capture directional dependencies in biological sequences, and applies it to a relevant problem in transcriptional regulation. The core idea is interesting and the application domain is timely. However, the current manuscript has several significant gaps in methodological transparency, validation rigor, and interpretability of results that prevent the claims from being fully established. The cross-species and cross-database validations are promising but incomplete, and the biological interpretation of the most important features requires stronger support.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on transcription factor prediction, gene regulatory network reconstruction, and sequence representation learning would be the primary audience. Researchers developing machine learning methods for genomic sequence analysis may also find the encoding approach of interest. The potential application to precision medicine and regulatory genomics is mentioned, but the current evidence does not yet support direct translational use.
- **Major strengths**
  1. The asymmetric covariance natural vector encoding is a conceptually novel extension of existing natural vector methods, addressing a real limitation (loss of directional information) in prior approaches.
  2. The framework addresses a genuine gap in the field: most existing tools predict TF identity or binding sites, but few attempt to jointly infer target gene status and regulatory direction.
  3. The use of multiple machine learning algorithms with systematic comparison across k-mer sizes and genome versions is methodologically sound.
  4. The cross-species validation attempts, using human-trained models to predict mouse interactions and vice versa, are a valuable addition that strengthens the generalizability claims.
  5. The SHAP-based feature importance analysis provides interpretability, which is often lacking in sequence-based prediction models.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The ACNVE method is described as capturing "directional dependencies between nucleotides" and "directional structural patterns from nucleotide sequences," with the generalized formulation for arbitrary order k.
- **Evidence pointer** Materials and methods, "Asymmetric covariance natural vector encoding method" and "Definition of basic statistics" sections; equations are referenced but not fully displayed
- **Concern** The mathematical formulation of the asymmetric covariance features is incomplete in the provided text. The equations for the second-order, third-order, and general k-order cases are indicated but not actually shown. Without the full mathematical definitions, it is impossible to verify that the method indeed captures directionality as claimed, or to assess potential issues such as normalization, handling of variable sequence lengths, and computational complexity. The illustrative example in Table 1 is mentioned but the table itself is not provided.
- **Why it matters** The core novelty of the manuscript rests on this encoding method. If the mathematical details are not fully specified, the method cannot be reproduced or evaluated by other researchers, which is a fundamental requirement for a methods-focused paper.
- **Resolution test** Provide the complete mathematical definitions of all equations, including the directional indicator function and the covariance formulas for all orders. Include the full illustrative example with the resulting feature vector. Clarify how sequences of different lengths are handled and whether any normalization is applied.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** "Benchmarking analyses demonstrated that XGBoost achieved the highest predictive performance across human and mouse genomes" and "the 5-mer configuration provided an optimal balance between feature richness and computational efficiency."
- **Evidence pointer** Results sections for Models 1–5; Figures 3–7; Supplementary Tables S1–S3
- **Concern** The performance comparisons are described in qualitative terms (e.g., "consistently achieved higher AUC values") without reporting actual numerical values, confidence intervals, or statistical significance tests. The claim that 5-mer is optimal is stated but the trade-off between performance gain and computational cost is not quantified. Additionally, the comparison across genome versions (H31 vs H43 vs H47) is mentioned but the magnitude of improvement is not reported. Without quantitative results, the reader cannot assess whether the observed differences are meaningful or within noise.
- **Why it matters** The central claims of the paper depend on demonstrating that the proposed method performs well and that specific configuration choices (5-mer, XGBoost) are justified. Qualitative descriptions are insufficient for a methods paper claiming superiority over existing approaches.
- **Resolution test** Report AUC values (with standard deviations or confidence intervals) for all models, k-mer configurations, and genome versions. Perform and report statistical significance tests (e.g., DeLong test for AUC comparison). Quantify the computational cost difference between k-mer configurations to support the "optimal balance" claim.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline comparison
- **Claim pointer** "ACNVE-K consistently achieved the best performance, with an average AUC of 0.9694 on the validation set and 0.9648 on the test set, substantially exceeding the strongest baseline model (AUC = 0.8519)"
- **Evidence pointer** Discussion section; Supplementary Table S25
- **Concern** The comparison against baseline methods (GatConv, GraphConv, GraphSAGE, Metapath2vec, HGETGI) is only described in the Discussion, not in the Results, and the details of this benchmarking are not provided. It is unclear whether the same data splits, hyperparameter tuning, and evaluation protocols were used for all methods. The baseline methods are graph-based, while ACNVE-K is sequence-based, so the comparison may not be apples-to-apples. Additionally, only one benchmark (TRRUST) is mentioned, and the specific experimental setup is not described.
- **Why it matters** The claim of superiority over existing methods is a key contribution of the paper. If the benchmarking is not rigorously described and controlled, the claim cannot be verified.
- **Resolution test** Move the baseline comparison to the Results section with full experimental details: data splits, hyperparameter tuning procedures, evaluation metrics, and statistical tests. Ensure all methods are evaluated under identical conditions. Consider adding more diverse baseline methods, including sequence-based approaches, for a fairer comparison.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** "the most important features identified by ACNVE-K and specific TF-binding architectures" and the discussion of RGL2 and MFRP as biologically plausible predictions
- **Evidence pointer** Discussion section; Supplementary Figures S7–S13; Supplementary Tables S5–S6
- **Concern** The biological interpretation of the top k-mer features (e.g., CGGCG, CGCCG, CGCAG) as resembling GC-box motifs is speculative. While the similarity to known GC-rich motifs is noted, no direct evidence is provided that these k-mers correspond to actual binding sites in the predicted target genes. The discussion of RGL2 and MFRP relies on evidence from other species (Arabidopsis for RGL2) or indirect evidence (MFRP as a target of other TFs), which is suggestive but not conclusive. The claim that these predictions "lend biological plausibility" is overstated given the indirect nature of the evidence.
- **Why it matters** The paper aims to provide biologically meaningful predictions. If the biological interpretation is not well-supported, the practical utility of the method is weakened.
- **Resolution test** Provide additional validation for the top k-mer features, such as enrichment analysis against known TF binding motifs in the predicted target gene promoters, or experimental validation of at least a few high-confidence predictions. For RGL2 and MFRP, provide more direct evidence of their regulatory roles in human or mouse systems.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data leakage and class imbalance
- **Claim pointer** The models are described as predicting TF identity, target gene status, and regulatory direction, with negative samples generated by "randomly pairing TFs (with prediction P < .1 from Model 1) and target genes (with prediction P < .1 from Model 2)."
- **Evidence pointer** Materials and methods, "Machine learning model frameworks" section
- **Concern** The negative sample generation strategy for Models 3–5 uses predictions from Models 1 and 2 to select TFs and target genes with low probability. This creates a potential information leak, as the same data used for training Models 1 and 2 is used to construct the training set for Models 3–5. Additionally, the class imbalance in the regulatory direction models (activation vs. inhibition) is not addressed; the dataset contains far more activating than inhibitory interactions, which could bias the models. The handling of this imbalance is not described.
- **Why it matters** If the negative sample generation introduces bias or information leakage, the reported performance of Models 3–5 may be inflated. Class imbalance can also lead to models that trivially predict the majority class.
- **Resolution test** Describe the data splitting strategy in detail, ensuring that Models 3–5 are trained on data independent from that used to train Models 1 and 2. Report the class distribution for each model and describe any techniques used to address class imbalance (e.g., class weights, resampling, or threshold adjustment).

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The models are available at GitHub repositories, and the data are stated to be available from public databases.
- **Evidence pointer** Code availability section; Data availability section
- **Concern** While the code repositories are mentioned, it is not clear whether they contain the full pipeline, including data preprocessing, feature extraction, model training, and evaluation scripts. The specific versions of the databases used (e.g., CollecTRI, TRRUST) are not specified with version numbers or access dates. The exact train/validation/test splits are not described in sufficient detail for reproduction.
- **Why it matters** Reproducibility is a core requirement for computational methods papers. Without complete code and data descriptions, other researchers cannot build upon or verify the results.
- **Resolution test** Provide a detailed description of the code repository structure, including all scripts needed to reproduce the results. Specify database versions and access dates. Describe the exact data splits and random seeds used.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "Using Leveraging eXtreme Gradient Boosting" contains a grammatical error ("Using Leveraging").
- **Required correction** Change to "Using eXtreme Gradient Boosting (XGBoost), Gradient Boosting (GB), and Random Forest (RF) algorithms."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results section
- **Evidence pointer** Results, "Representation of gene sequences in multidimensional feature spaces" section
- **Issue** The section heading is numbered "3Representation" with a missing space and number formatting issue.
- **Required correction** Correct the heading to "Representation of gene sequences in multidimensional feature spaces" or renumber appropriately.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Materials and methods, "Machine learning model frameworks" section
- **Issue** The description of the five models is somewhat repetitive, with the same algorithmic details repeated for each model. A consolidated description of the common training procedure would improve readability.
- **Required correction** Consider consolidating the common algorithmic details into a single paragraph and describing only the model-specific aspects (e.g., positive/negative sample definitions) for each of the five models.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph on benchmarking
- **Issue** The sentence "In plants, RGL2 has been characterized as a key gibberellin-responsive transcriptional repressor" is used to support a claim about human RGL2, but the relevance of plant data to human biology is not explicitly discussed.
- **Required correction** Add a sentence explaining the evolutionary conservation of RGL2 function or acknowledge the limitation of using plant data as supporting evidence.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Materials and methods, "Data source" section
- **Issue** The description of the CollecTRI database retrieval does not specify the version or download date, and the criteria for including/excluding interactions are not described.
- **Required correction** Add database version, access date, and any filtering criteria applied to the raw data.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results
- **Evidence pointer** Results, "Predicting potential TFs by model 1 framework" section
- **Issue** The text states "Most TF lacked TF characteristics" but the threshold for "lacking TF characteristics" is not defined.
- **Required correction** Define the probability threshold used to classify a gene as a TF or non-TF.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Materials and methods, "Machine learning model frameworks" section
- **Issue** The hyperparameter search ranges are given for GB and RF, but the final selected hyperparameters are not reported.
- **Required correction** Report the final hyperparameters for the best-performing models.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph on future directions
- **Issue** The mention of "FT_ANPD and Biformer networks" is brief and does not explain what these methods are or why they are relevant.
- **Required correction** Provide a brief description of these methods and their relevance to the proposed framework.

- **Technical failings that need to be addressed before the case is established**
  1. Incomplete mathematical formulation of the ACNVE method (R1-M1)
  2. Lack of quantitative performance metrics and statistical testing (R1-M2)
  3. Insufficient detail on baseline comparison methodology (R1-M3)
  4. Potential data leakage in negative sample generation for Models 3–5 (R1-M5)
  5. Incomplete description of data preprocessing and train/validation/test splits (R1-M6)

## Risk / unsupported claims
- The claim that ACNVE-K "offers a robust and interpretable framework for decoding transcriptional regulation" is not fully supported without quantitative performance metrics and statistical validation.
- The claim that the top k-mer features resemble GC-box motifs and provide a "mechanistic link" to TF binding is speculative and not directly tested.
- The cross-species validation results are described qualitatively; the actual predictions for specific cross-species regulatory relationships are not presented in sufficient detail to evaluate their significance.
- The statement that "99.1% of known human and 98.5% of mouse activation relationships had P > 99%" is presented without context on how these thresholds were chosen or what the baseline rates would be.
- The biological relevance of RGL2 and MFRP predictions relies on indirect evidence from other species or databases and is not experimentally validated in this study.
- The claim that newer genome versions "yielded superior model performance" is stated without reporting the magnitude of improvement or whether the differences are statistically significant.
- The comparison with existing methods (GatConv, GraphConv, etc.) is only described in the Discussion with a single summary AUC value, which is insufficient to establish superiority.