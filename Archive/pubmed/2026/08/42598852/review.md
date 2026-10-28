## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and availability sections. Supplementary materials referenced but not provided.
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and presentation quality. No assessment of code functionality or web server performance beyond what is described.
- **Shared manuscript claim summary** The authors present DNAreader, a transformer-based predictor of DNA-binding residues (DBRs) in both structured and disordered protein regions, trained with a combination of batch training and contrastive learning. They claim it is the first tool designed to predict DBRs for both protein types, that it outperforms 14 existing methods on two low-similarity test sets, and that it produces substantially fewer cross-predictions than current tools. A secondary module, DNAreaderDBIDR, predicts DNA-binding IDRs.
- **Visible evidence base** Full text of the manuscript including methods descriptions, results narratives, and figure captions. No actual figures, tables, or supplementary data were provided for inspection.
- **Missing materials affecting confidence** All figures (Figs 1-3), all supplementary tables (S1-S8), and all supplementary figures (S1-S7) are referenced but not available. Exact numerical results, statistical test outputs, and dataset composition details cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a genuine gap in the field: no existing predictor is designed to handle DBR prediction across both structured and disordered regions, and cross-prediction rates among current tools are acknowledged to be problematic. The methodological approach, combining a transformer encoder with contrastive learning and custom batch training, is reasonable and potentially impactful. However, the core claims rest entirely on results presented in figures and supplementary materials that were not available for review. The statistical rigor of the comparisons, the validity of the test set construction, and the magnitude of the reported improvements cannot be assessed from the provided text alone. The manuscript is well written and the logic is clear, but the evidence base is incomplete for a definitive evaluation.

- **Who would be interested in the results, and why** Computational biologists working on protein function prediction, particularly those focused on DNA-binding proteins and protein-nucleic acid interactions. Developers of similar prediction tools would be interested in the contrastive learning and batch training innovations. Experimental biologists studying protein-DNA interactions may find the web server useful for generating hypotheses. The work is also relevant to researchers working on disordered protein function, given the explicit focus on IDRs.

- **Major strengths**
  1. The problem is well motivated and the gap in the literature is clearly articulated. The distinction between DBR prediction and DNA-binding IDR prediction, and the inconsistency between these annotation types, is an important observation.
  2. The methodological innovations, particularly the multi-center contrastive loss with six anchor types and the custom batch training, are thoughtfully designed and appear well justified by the ablation analysis described.
  3. The comparative evaluation includes a broad and representative set of 14 methods, including recent predictors, meta-predictors, and a baseline from a different ligand type.
  4. The authors address cross-predictions and over-predictions explicitly, which is a known weakness in this field and often ignored.
  5. The work is accompanied by a web server and source code, which enhances usability and reproducibility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The central claim that DNAreader statistically outperforms existing tools on both test sets, with AUROC of 0.86-0.89 versus 0.79 for the best comparator, and substantially lower cross-prediction rates.
- **Evidence pointer** Figures 2A-C, Supplementary Tables S6-S8, Supplementary Figures S5-S7. Location not provided in the text for specific numerical values.
- **Concern** All quantitative results supporting the main claims are contained in figures and supplementary tables that were not provided with the manuscript. The text describes outcomes but does not include the actual numbers, confidence intervals, or effect sizes. Without access to these materials, the magnitude and statistical significance of the reported improvements cannot be verified. The claim that DNAreader is "the first predictor specifically designed to predict DBRs in the structured and disordered sequence regions" is also stated without a systematic literature search to confirm novelty.
- **Why it matters** The primary contribution of this work is empirical: a new method that performs better than existing ones. If the underlying data cannot be examined, the central claims are unverifiable. The novelty claim also requires evidence that no prior tool has attempted this specific combination.
- **Resolution test** Provide the full figures and supplementary tables for review. Include exact numerical values for all metrics, confidence intervals or standard deviations, and the full output of the statistical tests. Provide a systematic search strategy and results demonstrating that no prior predictor targets both structured and disordered DBRs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset construction and comparability
- **Claim pointer** The two test sets are described as low-similarity and comparable, with test set 1 containing 430 proteins and test set 2 containing 231 proteins, including new disordered proteins with DBR annotations.
- **Evidence pointer** "Datasets" section under Materials and methods. Supplementary Table S2. Location not provided.
- **Concern** The description of how the new disordered proteins with DBR annotations were collected and annotated is incomplete. The authors state that 62 proteins were identified with DBRs within IDRs or LIP regions, but the criteria for selecting these proteins, the source databases, and the annotation methods are not fully described. The claim that test set 2 has "similar proportions of disordered, structured, and binding residues" to test set 1 is stated but not demonstrated. The process for ensuring <25% sequence similarity between training and test sets is described but the details of the clustering are not fully transparent.
- **Why it matters** The validity of the comparative evaluation depends on the test sets being fair and representative. If the new disordered proteins were collected or annotated differently from the existing test proteins, comparisons could be biased. The similarity control is critical for avoiding inflated performance estimates.
- **Resolution test** Provide a detailed description of the data collection and annotation process for the 62 new proteins, including inclusion and exclusion criteria. Show the distribution of sequence lengths, disorder content, and binding residue fractions for both test sets. Provide the full clustering results and demonstrate that the similarity constraint is satisfied.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological justification
- **Claim pointer** The choice of six anchor types for contrastive learning is presented as optimal based on comparisons with three, five, and eight anchors, with six anchors producing the best results.
- **Evidence pointer** "Step 2: Design and training of the transformer encoder-based network" section. Supplementary Figure S1. Location not provided.
- **Concern** The description of the anchor selection process is brief. The authors state that six anchors performed best but do not provide the actual performance values for each configuration. The differences between five and six anchors, and six and eight anchors, are described as significant in one case and not significant in the other, but the specific metrics and p-values are not given. The rationale for why six anchors is the natural choice is not fully explained.
- **Why it matters** The contrastive learning design is a key innovation of the paper. If the anchor selection is not rigorously justified, readers cannot assess whether the chosen configuration is truly optimal or whether the results are sensitive to this choice.
- **Resolution test** Provide the full results of the anchor comparison, including all metrics for each configuration. Explain the conceptual rationale for why six anchor types is the appropriate granularity. Show that the performance differences are robust across multiple random seeds or initializations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparative evaluation fairness
- **Claim pointer** DNAreader is compared against 14 methods, including 8 structure-trained, 2 disorder-trained, 3 meta-predictors, and ANCOHR2 as a baseline.
- **Evidence pointer** "Selection of methods for comparative evaluation" section. Supplementary Table S1. Location not provided.
- **Concern** The criteria for selecting the 14 comparison methods are clear, but the details of how each method was run are not provided. It is not stated whether default parameters were used, whether the methods were retrained on the authors' training data, or whether the methods' own recommended protocols were followed. The inclusion of ANCOHR2, which predicts protein and peptide binding rather than DNA binding, is justified as a baseline, but the interpretation of its results needs care.
- **Why it matters** Fair comparison is essential for establishing that DNAreader is genuinely better. If some methods were run with suboptimal settings, the comparison would be biased in favor of DNAreader.
- **Resolution test** Provide a detailed protocol for how each of the 14 methods was run, including parameter settings, any retraining procedures, and the version of each tool used. State whether the authors contacted the developers of the original methods for guidance on optimal usage.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalization and robustness
- **Claim pointer** The authors claim DNAreader performs well for both structured and disordered proteins and produces few cross-predictions, based on results on two test sets.
- **Evidence pointer** "Comparative assessment on test dataset 1" and "Comparative assessment on test dataset 2" sections. Figures 2B-C. Location not provided.
- **Concern** The two test sets, while low-similarity, may not capture the full diversity of protein-DNA interactions. The authors do not discuss potential limitations of their test sets, such as bias toward certain protein families or interaction types. The performance on disordered proteins is based on a relatively small number of proteins with DBR annotations in IDRs. The generalizability of the results to other organisms, interaction types, or sequence diversity is not addressed.
- **Why it matters** A predictor that works well on the test sets but fails on other types of proteins would have limited utility. The authors should acknowledge the scope of their evaluation and discuss potential limitations.
- **Resolution test** Provide an analysis of the diversity of the test sets in terms of protein families, organisms, and interaction types. Discuss potential biases and how they might affect the generalizability of the results. If possible, include additional validation on independent datasets.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of notation
- **Affected element** Loss function equations
- **Evidence pointer** "Step 2: Design and training of the transformer encoder-based network" section. Location not provided.
- **Issue** The equations for the loss function are presented without clear definitions of all variables. The notation for the margin parameter and the distance function is introduced but the full mathematical formulation is not explained in the text.
- **Required correction** Provide a clear definition of all variables in the loss function equations, including the dimensions of the latent space vectors and the interpretation of the margin parameter.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Hyperparameter settings
- **Evidence pointer** "Step 2: Design and training of the transformer encoder-based network" section. Location not provided.
- **Issue** The manuscript does not provide a complete list of hyperparameters used for training, including learning rate, batch size, number of epochs, and the specific grid search ranges for the anchor proportions and loss weight.
- **Required correction** Include a table or supplementary section listing all hyperparameters and the ranges explored during optimization.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Performance comparisons
- **Evidence pointer** "Comparative assessment on test dataset 1" and "Comparative assessment on test dataset 2" sections. Location not provided.
- **Issue** The text reports p-values for comparisons but does not specify which statistical test was used, whether corrections for multiple testing were applied, or whether the comparisons were paired or unpaired.
- **Required correction** Specify the statistical tests used, the correction method for multiple comparisons, and whether the tests were paired or unpaired.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Case study interpretation
- **Affected element** Figure 3
- **Evidence pointer** "Case studies" section. Location not provided.
- **Issue** The case studies are described qualitatively. The claim that DNAreader "correctly identifies" the second protein as not interacting with DNA is based on visual inspection of scores, but no quantitative threshold or statistical criterion is given for what constitutes a "correct" identification.
- **Required correction** Provide quantitative criteria for evaluating the case study predictions, such as the number of false positives at a given threshold or a comparison with the native annotations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** "Introduction" and "Summary and discussion" sections. Location not provided.
- **Issue** The manuscript mentions that 42 of 47 existing methods are structure-trained, but does not discuss in detail why disorder-trained methods have lagged behind or what specific challenges they face.
- **Required correction** Add a brief discussion of the specific challenges in predicting DBRs in disordered regions, such as the lack of training data or the different nature of binding in disordered contexts.

- **Technical failings that need to be addressed before the case is established**
  1. The complete set of figures and supplementary materials must be provided for verification of all quantitative claims.
  2. The dataset construction process, particularly for the new disordered proteins with DBR annotations, needs to be described in sufficient detail to allow replication.
  3. The statistical analysis methodology needs to be specified, including the tests used and whether corrections for multiple testing were applied.
  4. The protocol for running the 14 comparison methods needs to be documented to ensure fair comparison.

- **Assessment against Nature-style criteria**
  - **Originality**: The concept of a unified predictor for both structured and disordered DBRs is novel. The combination of contrastive learning with batch training in this context appears to be a new contribution. However, the originality claim is weakened by the lack of a systematic comparison with prior attempts to address the structured-disordered dichotomy.
  - **Scientific importance**: The problem is important. DNA-binding is a fundamental biological process, and accurate prediction of DBRs has practical utility. The explicit focus on disordered regions addresses a gap in current tools. The importance is somewhat diminished by the narrow scope of the evaluation, which uses only two test sets.
  - **Interdisciplinary readership**: The work is primarily of interest to computational biologists and bioinformaticians. The biological insights are limited, and the methodological innovations are specific to the machine learning community working on protein prediction. The interdisciplinary appeal is moderate.
  - **Technical soundness**: The methodological design is sound in principle, with appropriate use of modern architectures and training strategies. However, the technical soundness cannot be fully assessed without the actual results. The ablation study is a good practice, but the details are insufficient.
  - **Readability for nonspecialists**: The manuscript is clearly written and the logic is easy to follow. The authors explain the motivation well and the distinction between DBRs and DNA-binding IDRs is made accessible. The methods section is technical but appropriate for the target audience. The case studies help illustrate the practical behavior of the tool.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a real gap, the approach is well motivated, and the writing is clear. However, the central claims cannot be verified without the full set of results. The dataset construction and statistical methodology need to be documented more thoroughly. If the provided materials confirm the reported performance, this would be a valuable contribution to the field.