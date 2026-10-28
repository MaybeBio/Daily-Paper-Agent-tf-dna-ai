## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific validity, technical soundness, generalizability claims, and reproducibility of the described deep learning model and its validation
- **Shared manuscript claim summary** The authors present LectinOracle, a deep learning model combining transformer-based protein representations (ESM-1b) with graph convolutional neural networks for glycans (SweetNet), trained on 564,647 unique protein-glycan interactions from 3,328 glycan microarray experiments. They claim the model accurately predicts lectin-glycan binding, generalizes to new lectins and glycans, identifies lectin clusters with shared binding specificity, and can analyze whole lectomes in host-microbe interactions.
- **Visible evidence base** Abstract, introduction, results sections (Figures 1-4, Figures S1-S8, Tables 1, S1-S5 referenced), discussion, and methods sections as provided in the manuscript text
- **Missing materials affecting confidence** Actual figure images and supplementary tables (S1-S5) not provided; detailed model architecture hyperparameters partially described; exact training/validation split details not fully specified; code repository not reviewed; quantitative performance metrics (e.g., correlation coefficients, p-values) referenced but not fully tabulated in text

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable computational tool for predicting lectin-glycan interactions, addressing a significant gap in glycobiology. The combination of transformer-based protein embeddings with graph neural networks for glycans is methodologically sound and timely. However, several technical concerns regarding dataset construction, model validation, and the strength of generalizability claims need to be addressed. The independent validation on custom glycan arrays is encouraging but limited in scope, and the biological insights derived from lectome analysis require more rigorous statistical support.
- **Who would be interested in the results, and why** Glycobiologists studying lectin specificity and function; computational biologists developing protein-ligand interaction predictors; researchers investigating host-microbe interactions, particularly those studying pathogen adhesion mechanisms; and the broader glycoscience community interested in high-throughput lectin characterization tools.
- **Major strengths** 1) Novel integration of state-of-the-art protein language models with glycan graph representations; 2) Large curated training dataset (564,647 interactions) spanning diverse lectin classes; 3) Multiple independent validation strategies including custom glycan arrays; 4) Demonstrated sensitivity to both glycan structure and protein sequence mutations; 5) Practical utility demonstrated through lectome-scale analysis.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset leakage risk), R1-M2 (validation metric inadequacy), R1-M3 (statistical rigor of clustering claims), R1-M4 (mutation sensitivity analysis incompleteness)
- **Assessment against Nature-style criteria** **Originality**: High. The specific combination of ESM-1b and SweetNet architectures for lectin-glycan prediction is novel and represents a meaningful advance over existing approaches. **Scientific importance**: Moderate to high. Lectin-glycan interactions are fundamental to numerous biological processes, and a reliable predictive tool would have broad utility. However, the demonstrated improvements over existing methods are not quantified. **Interdisciplinary readership**: Moderate. The work bridges computational biology, glycobiology, and microbiology, but the presentation may be too technical for non-specialists in deep learning. **Technical soundness**: Moderate. The approach is reasonable but several validation and statistical concerns (detailed below) need to be addressed. **Readability for nonspecialists**: Adequate. The introduction and discussion are accessible, but the results section assumes familiarity with both deep learning and glycan chemistry.
- **Recommendation posture** Supportive if technical concerns are resolved. The core approach is promising and the validation strategy is thoughtful, but the current evidence does not fully establish the generalizability claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data leakage / training-validation contamination
- **Claim pointer** The authors claim the model generalizes to new lectins and glycans, supported by a train/test split ensuring "no proteins were present in both the training and the test set."
- **Evidence pointer** Methods, Dataset Construction; Methods, Data Processing; Results, Developing a deep learning-based model
- **Concern** The manuscript states that the dataset was split ensuring no protein overlap between training and test sets, but it is unclear whether glycans were also non-overlapping. Given that the same glycans may appear across multiple lectins, and the model concatenates protein and glycan representations, glycan overlap alone could inflate performance metrics. Additionally, the 3,328 original experiments were reduced to 2,709 after filtering for available protein sequences, but the criteria for "unique" interactions (564,647) are not fully specified. If multiple experiments with the same protein-glycan pair (differing only in concentration or buffer) were averaged, this is appropriate, but the exact deduplication procedure needs clarification.
- **Why it matters** Data leakage is a fundamental issue in machine learning validation. If glycans overlap between training and test sets, the reported generalizability to new glycans is overstated, and the model's utility for predicting interactions with unseen glycans is not established.
- **Resolution test** Provide a detailed description of the deduplication process and confirm whether the test set contains glycans absent from the training set. Ideally, report performance metrics separately for (a) seen glycans with unseen lectins, (b) unseen glycans with seen lectins, and (c) fully unseen protein-glycan pairs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation metric adequacy
- **Claim pointer** The authors claim "qualitative and quantitative agreement with experimental data" based on Pearson correlation coefficients between predicted and observed binding values on independent arrays.
- **Evidence pointer** Results, LectinOracle predictions match independent experimental observations; Figures 3A-L, S7A-D
- **Concern** The use of Pearson correlation as the primary validation metric is insufficient. Correlation measures monotonic association but does not assess calibration (i.e., whether predicted values match observed values on an absolute scale). The authors mention thresholding predictions into "bound"/"not bound" categories for some analyses, but the threshold selection procedure is not described. Furthermore, the manuscript reports "moderate" correlations (0.5-0.7) and "strong" correlations (>0.7) without providing confidence intervals or statistical significance tests. The biological relevance of a given correlation coefficient for this application is not established.
- **Why it matters** For a predictive tool intended to guide experimental work, both ranking accuracy (correlation) and absolute accuracy (calibration) matter. A model with high correlation but poor calibration could mislead researchers about the strength of binding. The lack of confidence intervals prevents assessment of estimate precision.
- **Resolution test** Report additional metrics such as root mean squared error (RMSE) or mean absolute error (MAE) between predicted and observed values. Provide confidence intervals for correlation coefficients and describe the threshold selection procedure for binary classification. If possible, compare model performance against simple baselines (e.g., sequence similarity-based predictions) to demonstrate added value.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor of clustering and enrichment analyses
- **Claim pointer** The authors claim identification of "lectin clusters with shared binding patterns" and "enrichment" of specific glycan motifs among predicted binders.
- **Evidence pointer** Results, Analyzing lectins with LectinOracle; Figures 2A-E, S8A-C; Results, Investigating lectomes in host-microbe interactions; Figures 4A-E
- **Concern** The clustering analyses (Figures 2, 4) are presented descriptively without quantitative assessment of cluster stability or significance. The enrichment analyses (e.g., for SNA, ConA, PSE41-5) report p-values from Wilcoxon tests, but the multiple testing burden across many lectins and motifs is not addressed. The comparison between ESM-1b-based clustering and LectinOracle-based clustering (Figure 2A vs 2B) lacks a quantitative metric for cluster quality or separation. The lectome analysis (Figure 4) appears to be entirely descriptive without statistical support for the claimed differences between pathobionts and commensals.
- **Why it matters** The biological insights derived from clustering and enrichment analyses are central to the paper's claims of utility. Without statistical rigor, these insights may be artifacts of the model or the clustering procedure, undermining confidence in the biological conclusions.
- **Resolution test** Provide quantitative cluster quality metrics (e.g., silhouette scores, bootstrap support) for the clustering analyses. Apply multiple testing corrections for enrichment analyses. For the pathobiont vs. commensal comparison, provide statistical tests (e.g., permutation tests) with appropriate corrections.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mutation sensitivity analysis completeness
- **Claim pointer** The authors claim that LectinOracle is "sensitive towards mutations of amino acids in the ligand binding pocket" based on the SubB alanine substitution experiment.
- **Evidence pointer** Results, Analyzing lectins with LectinOracle reveals lectin clusters with shared binding patterns; Figure 2E, S5
- **Concern** The SubB analysis demonstrates that alanine substitutions in the binding pocket abolish predicted binding, but this is a single example. The manuscript does not provide a systematic analysis of how model predictions respond to mutations across multiple lectins, nor does it compare the model's sensitivity to known experimental mutagenesis data. The claim of sensitivity is therefore based on limited evidence. Additionally, the manuscript does not address whether the model can distinguish between mutations that affect binding affinity versus those that affect specificity.
- **Why it matters** The ability to predict the effects of mutations on lectin-glycan binding would be a significant advance with practical applications. However, a single case study is insufficient to establish this capability, and the current analysis does not demonstrate that the model captures the nuanced effects of mutations on binding specificity.
- **Resolution test** Provide additional mutation analyses for multiple lectins with known experimental mutagenesis data. Compare model predictions with experimental measurements of binding affinity or specificity for mutated lectins. If such data are not available, temper the claim to reflect the limited evidence.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model training details
- **Evidence pointer** Methods, Model Training
- **Issue** The manuscript states that hyperparameters were optimized via cross-validation but does not specify the cross-validation scheme (e.g., k-fold, leave-one-out) or the range of hyperparameters explored. The final architecture (number of layers, hidden dimensions, dropout rates) is not fully specified.
- **Required correction** Provide a complete description of the model architecture, hyperparameter search space, and final hyperparameter values. Consider releasing the training code and configuration files to ensure reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary materials
- **Evidence pointer** Methods, Data Availability
- **Issue** The manuscript states that all data is available in supplementary tables, but the specific contents of Tables S1-S5 are not described in the text. The reader cannot assess the quality or completeness of the training data without accessing these tables.
- **Required correction** Provide a brief description of each supplementary table in the main text or methods section. Ensure that the supplementary tables are publicly accessible and contain all necessary metadata.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Baseline comparison
- **Affected element** Model evaluation
- **Evidence pointer** Results, Developing a deep learning-based model; Table 1
- **Issue** The manuscript compares different model variants (Table 1) but does not compare LectinOracle against existing lectin-glycan prediction tools or simpler sequence-based baselines. The claim of improved performance over existing methods is not directly supported.
- **Required correction** Include a comparison against at least one existing lectin-glycan prediction method or a simple baseline (e.g., sequence similarity-based nearest neighbor) to contextualize the model's performance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Correlation coefficients
- **Evidence pointer** Results, LectinOracle predictions match independent experimental observations; Figures 3A-L
- **Issue** Correlation coefficients are reported as single values without confidence intervals or sample sizes. The number of glycans or lectins used for each correlation is not stated.
- **Required correction** Report sample sizes and confidence intervals for all correlation coefficients. Consider using scatter plots with fitted regression lines to visualize the relationships.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Generalizable" in title and claims
- **Evidence pointer** Title; Abstract; Discussion
- **Issue** The term "generalizable" is used in the title and throughout the manuscript, but the evidence for generalizability is limited to a few independent arrays and lectome analyses. The model's performance on truly novel lectin families or glycan types not represented in the training data is not systematically evaluated.
- **Required correction** Either provide more comprehensive evidence of generalizability (e.g., leave-one-family-out validation) or temper the language to "generalizable within the training distribution" or similar.

## Risk / unsupported claims
- The claim that LectinOracle can "analyze whole lectomes and their role in host-microbe interactions" is not fully supported by the presented analyses, which are descriptive and lack statistical rigor.
- The claim of "qualitative and quantitative agreement with experimental data" is based on correlation coefficients without confidence intervals or calibration assessment.
- The claim that LectinOracle is "sensitive towards mutations of amino acids in the ligand binding pocket" is based on a single example (SubB) and may not generalize.
- The statement that the model "can be used generally to further probe the glycan-binding specificity of lectins" is not supported by systematic evaluation across diverse lectin families.
- The assertion that previous approaches "lack scalability and the possibility of providing predictions for novel lectins" is not directly compared or quantified in this work.