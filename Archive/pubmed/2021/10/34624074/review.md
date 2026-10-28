## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) without supplementary figures or tables
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text
- **Shared manuscript claim summary** The authors present a comprehensive analysis of nucleic acid binding sites for three interaction partner classes (ligands, proteins, nucleic acids), propose structural and preference features distinguishing binding from non-binding sites, and introduce NABS, an integrative prediction framework combining feature-based ensemble learning, template-based modeling, and random walk post-processing
- **Visible evidence base** Main text tables (Tables 1-5), figures referenced in text (Figures 1-7), supplementary materials referenced but not provided
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S25), detailed dataset composition, performance comparison data, web server implementation details

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in nucleic acid binding site prediction by systematically comparing binding sites across three interaction partner types and proposing a unified prediction framework. The biological analyses of binding site preferences are informative and potentially useful. However, the methodological contributions are incremental relative to existing tools, and several technical aspects require clarification. The performance claims, particularly regarding superiority over existing methods, cannot be fully evaluated from the provided text alone. The manuscript would benefit from clearer presentation of validation strategies and more rigorous statistical comparisons.

- **Who would be interested in the results, and why** Researchers in structural bioinformatics and computational biology, particularly those working on nucleic acid function prediction, RNA-protein interactions, and drug design targeting nucleic acids. The biological characterization of binding site preferences may also interest experimentalists studying nucleic acid recognition mechanisms.

- **Major strengths**
  1. Comprehensive comparison of binding sites across three interaction partner types in both RNA and DNA, addressing a gap in the field
  2. Novel application of structural features (depth, protrusion, Laplacian norm) to nucleic acid binding site prediction
  3. Integration of feature-based and template-based approaches with post-processing, showing thoughtful method design
  4. Analysis of predicted structures extends practical applicability
  5. Web server availability enhances usability

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Our unified prediction framework yielded promising results for different binding sites and outperformed existing methods"
- **Evidence pointer** Tables 1-5, Figure 4, location not provided
- **Concern** The claim of outperforming existing methods is not adequately supported. The comparison with Rsite, Rsite2, RBind, and RNAsite appears limited to specific datasets, and the statistical significance of performance differences is not clearly established. The text mentions P-values in supplementary tables, but the main text does not summarize these results. Furthermore, the comparison with sequence-based methods (RBPbinding, DeepSNR, D-AEDNet) uses different evaluation protocols, making direct comparison questionable.
- **Why it matters** The central contribution of this work is the prediction framework. Without rigorous, clearly presented comparative evaluation, the claimed advantage over existing methods cannot be verified, undermining the manuscript's primary contribution.
- **Resolution test** Provide clear summary statistics of performance comparisons in the main text, including effect sizes and confidence intervals. Ensure evaluation protocols are consistent across methods. If different protocols are necessary, justify their use and discuss potential biases.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "we performed a comprehensive comparison between binding and nonbinding sites and among different categories of binding sites"
- **Evidence pointer** Figures 2-3, 5-6, location not provided
- **Concern** The statistical analysis of binding site preferences appears descriptive. The text reports observed differences in nucleotide composition, functional group usage, and structural features, but does not describe formal statistical testing of these differences. Without appropriate statistical tests (e.g., permutation tests, bootstrapping), the claimed differences may not be robust, particularly given the varying dataset sizes across interaction types.
- **Why it matters** The biological insights regarding binding site preferences are a key contribution. If these differences are not statistically validated, the conclusions may be overstated and the biological interpretation unreliable.
- **Resolution test** Apply appropriate statistical tests to compare binding versus non-binding sites and across interaction types. Report effect sizes and confidence intervals. Address multiple testing concerns where applicable.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "we established a feature-based ensemble learning classifier" and "we designed a template-based classifier"
- **Evidence pointer** Methods section, location not provided
- **Concern** Critical implementation details are missing. The text does not specify hyperparameter values, the exact composition of the 210 classifiers (beyond counts), the threshold for feature selection, or the criteria for defining "high-quality templates" in the template-based module. The random walk parameters (beyond beta and T) and the construction of nucleotide interaction networks require clarification. Without these details, the methods cannot be reproduced.
- **Why it matters** Reproducibility is fundamental to computational biology research. The lack of implementation details prevents other researchers from applying or extending the method, limiting the work's impact.
- **Resolution test** Provide complete parameter specifications, pseudocode or code availability, and detailed descriptions of all algorithmic components. Consider depositing the code in a public repository.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data quality
- **Claim pointer** "we performed a comprehensive comparison between binding and nonbinding sites"
- **Evidence pointer** Data preparation section, location not provided
- **Concern** The dataset construction criteria are not fully described. The text mentions resolution thresholds, sequence identity cutoffs, and exclusion of metal ion binding sites, but does not specify the exact numbers of structures in each dataset after filtering, the distribution of structure types, or potential biases in the PDB (e.g., overrepresentation of certain RNA families or DNA-binding proteins). The imbalance ratios mentioned (e.g., 1:5.6 for RL) suggest significant class imbalance that may affect both analysis and prediction.
- **Why it matters** Dataset composition directly affects the validity of both biological conclusions and prediction performance. Biased or poorly characterized datasets can lead to overfitting and limited generalizability.
- **Resolution test** Provide detailed dataset statistics, including numbers of structures, chains, nucleotides, and binding sites per dataset. Discuss potential PDB biases and their implications. Consider stratifying analyses by RNA/DNA type or structural class.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "we suggested that RNAs and proteins could use structurally similar strategies to interact with other molecules, but DNAs may choose a different way"
- **Evidence pointer** Results section, Figures 2-3, 5-6, location not provided
- **Concern** The biological interpretation of the observed differences between RNA and DNA binding sites is limited. The text notes that DNA binding sites tend to be near the middle of chains and RNA uses pockets for ligands and protruding surfaces for proteins, but does not discuss the structural or functional implications in depth. The comparison with protein binding site literature is superficial.
- **Why it matters** The biological insights are presented as a key contribution, but the interpretation lacks depth. A more thorough discussion of the structural basis for these differences and their functional implications would strengthen the work's significance.
- **Resolution test** Expand the discussion to relate observed binding site preferences to known structural features of nucleic acids, discuss exceptions and their implications, and connect findings to broader questions in nucleic acid biology.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states "we performed a comprehensive comparison" but does not summarize key findings of this comparison. The abstract focuses on method description and performance claims.
- **Required correction** Include 1-2 sentences summarizing the main biological findings regarding binding site preferences.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Feature selection
- **Evidence pointer** Methods, Feature-based prediction module, location not provided
- **Issue** The text states that SBS was performed using RFECV but does not specify the scoring metric used for feature ranking or the stopping criterion for feature elimination.
- **Required correction** Specify the scoring metric and stopping criteria for the feature selection procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, RNA binding site analyses
- **Evidence pointer** Results, Analyses of preference features, location not provided
- **Issue** The text reports "the RL dataset displayed the strongest binding preference for G" but does not provide quantitative values or confidence intervals for these preferences.
- **Required correction** Include quantitative measures (e.g., preference scores with standard errors) in the main text or refer clearly to supplementary tables.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Performance evaluation
- **Evidence pointer** Methods, Performance evaluation, location not provided
- **Issue** The text mentions 5-fold CV, leave-one-chain-out validation, and 10-fold CV but does not specify how these were implemented (e.g., stratification, random seeds, repeated runs).
- **Required correction** Provide details on CV implementation, including whether results are averaged over multiple runs and how variance is reported.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Web server
- **Evidence pointer** Discussion, location not provided
- **Issue** The web server URL is provided, but no details on input requirements, output format, or computational time are given.
- **Required correction** Briefly describe the web server interface and expected usage in the main text or supplementary materials.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion of limitations is brief and does not address potential overfitting, generalizability to non-PDB structures, or the impact of dataset imbalance on prediction performance.
- **Required correction** Expand the limitations section to address these concerns explicitly.

## Risk / unsupported claims
- The claim of "outperforming existing methods" is not fully supported by the evidence presented in the main text
- The biological interpretation that "RNAs and proteins could use structurally similar strategies" is presented without sufficient comparative analysis
- The applicability of NABS to predicted RNA structures is claimed but the performance on such structures is not clearly quantified
- The statement that "the unified framework could be used to predict different types of binding nucleotides" implies generalizability that is not fully demonstrated across all six interaction types
- The claim that "structural features were essential for the prediction of binding sites in RNA" is not quantified in the main text
- The assertion that "the ensemble strategy could enhance the robustness" is not supported by variance or stability analyses
- The performance comparison with sequence-based methods (RBPbinding, DeepSNR, D-AEDNet) uses different evaluation protocols and may not be directly comparable