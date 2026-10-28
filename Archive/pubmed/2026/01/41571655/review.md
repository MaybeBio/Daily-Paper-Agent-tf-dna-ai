## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends.
- **Assessment boundary** Evaluation of the scientific claims, methodological soundness, and presentation quality based solely on the provided manuscript text. No external data, code, or supplementary materials were accessed.
- **Shared manuscript claim summary** The authors introduce HyDrop v2, an improved custom droplet-based scATAC-seq platform, and benchmark its suitability for training sequence-to-function (S2F) deep learning models against commercial 10x Genomics data in two species (mouse cortex and Drosophila embryo). They claim that lower fragment counts can be compensated by increased cell numbers, that S2F models trained on custom or commercial data perform comparably in enhancer prediction, sequence explainability, and TF footprinting, and that integrating data across platforms enables cost-efficient atlas construction for regulatory modeling.
- **Visible evidence base** Main text figures 1-5, supplementary figures S1-S7, supplementary tables S1-S5, and methods sections describing experimental protocols, data processing, and model training.
- **Missing materials affecting confidence** Supplementary figures and tables are referenced but not provided in the submitted text. The supplementary note describing HyDrop v2 technical improvements is not included. Source data files are mentioned but not accessible. Code availability and data availability statements are not present in the provided text.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question: how different scATAC-seq platforms perform as training data sources for S2F deep learning models. The authors present a substantial dataset generation effort and a systematic comparison framework. The core finding, that cell number matters more than per-cell fragment depth for S2F model training, is potentially valuable. However, the manuscript has several significant weaknesses. The benchmarking logic is incomplete, particularly regarding the confound between platform and cell number. The claim of "first benchmark" is overstated given prior comparative work. The statistical treatment of model performance differences is insufficient. The Tn5 bias analysis, while interesting, is not fully integrated with the S2F modeling results. The writing is dense and at times unclear, with some figures not adequately described in the text. The economic analysis is superficial and does not account for total workflow costs. Overall, the work has merit but requires substantial revision to establish its claims rigorously.

- **Who would be interested in the results, and why** Researchers developing or applying scATAC-seq technologies, particularly those building large-scale atlases for regulatory genomics. Computational biologists working on S2F models and cis-regulatory code inference will find the benchmarking results relevant. Laboratories considering cost-effective platform choices for single-cell epigenomics projects would benefit from the cost comparisons. The Drosophila community may value the large developmental atlas resource.

- **Major strengths**
  1. The study addresses a genuinely important and under-explored question: how platform choice affects S2F model training, not just standard QC metrics.
  2. The scale of data generation is substantial, particularly the Drosophila atlas with over 600,000 cells.
  3. The multi-species design (mouse and fly) strengthens the generalizability of the conclusions.
  4. The use of in vivo validated enhancers as a biological benchmark is a strong evaluation strategy.
  5. The open-source nature of HyDrop v2 and the detailed cost analysis are practical contributions.
  6. The integration of multiple evaluation dimensions (enhancer prediction, motif discovery, footprinting) provides a comprehensive assessment.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and confounding
- **Claim pointer** The authors claim that "S2F models trained on custom or commercial data perform comparably in enhancer prediction, sequence explainability, and transcription factor footprinting" (Abstract) and that "lower fragment counts can be compensated for by increased cell numbers" (Abstract).
- **Evidence pointer** Figure 2c, 2d, 2e; Results section "Increased cell number improves S2F model performance"
- **Concern** The central comparison between HyDrop v2 and 10x platforms is confounded by cell number. The HyDrop v2 dataset contains 67,080 cells versus 19,478 for 10x in mouse, and 340,604 versus 266,736 in fly. The authors show that increasing cell number improves model performance (Figure 2d), yet they do not adequately disentangle whether the comparable performance of HyDrop v2 models is due to the platform itself or simply the larger cell count. The downsampling experiments partially address this, but the comparison at matched cell numbers (e.g., 19,478 cells for both platforms) is not clearly presented as the primary comparison. The claim that "lower fragment counts can be compensated for by increased cell numbers" is presented as a general finding, but the compensation ratio is not systematically characterized across multiple cell number and depth combinations. This confounding undermines the central comparative claim.
- **Why it matters** If the performance difference is primarily driven by cell number rather than platform, the conclusion that HyDrop v2 is "comparable" to 10x is trivially true and not a platform-specific finding. The practical recommendation for atlas construction depends on understanding the trade-off surface between cell number, depth, and cost across platforms.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors state "Model performance comparison (Test Pearson correlation) of the models shown in (b)" (Figure 2c legend) and report differences in performance across scenarios.
- **Evidence pointer** Figure 2c, 2d; Figure 3a; Results sections on model training and evaluation
- **Concern** The manuscript reports Pearson correlation coefficients as the primary performance metric but provides no confidence intervals, statistical tests, or effect size measures for the differences between models. With 10-fold cross-validation, the authors have 10 per-fold models, yet the variability across folds is not reported. The claim that models "perform comparably" is not supported by any statistical evidence. Similarly, the statement that "reducing the sequencing depth per cell does not impact the precision and recall" (Results) is made without statistical backing. The manuscript needs either formal hypothesis tests with appropriate multiple testing correction, or at minimum, confidence intervals and clear reporting of fold-to-fold variability.
- **Why it matters** Without statistical rigor, the reader cannot assess whether observed differences are meaningful or noise. The practical recommendations (e.g., "depth does not matter") have resource implications for the community, and these should be supported by appropriate statistical evidence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and positioning
- **Claim pointer** The authors claim "we perform the first benchmark of scATAC-seq platforms focusing on its capacity to train S2F models" (Introduction) and "To date, scATAC benchmarking papers have not evaluated the suitability of specific scATAC-seq technologies to train sequence-to-function (S2F) deep learning models" (Discussion).
- **Evidence pointer** Introduction, Discussion
- **Concern** The claim of "first benchmark" is difficult to verify from the provided text alone, but the authors themselves cite ChromBPNet (reference 13) and other works that have trained S2F models on scATAC data from different platforms. The statement in the Discussion that "DL tool (benchmarking) papers did not compare training data generated on different platforms" may be accurate, but the manuscript does not provide a systematic literature review to support this. The positioning would be strengthened by a more careful and nuanced statement of what is novel, acknowledging prior comparative work on scATAC platforms (e.g., reference 9) and prior S2F model training studies.
- **Why it matters** Overstated novelty can undermine credibility. A precise statement of the specific gap being filled would better position the work and help readers understand its contribution relative to prior art.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Tn5 bias analysis
- **Claim pointer** The authors state "we find that microfluidic platforms (HyDrop v2 and 10x) using their respective standard Tn5 produce identical Tn5 biases" (Discussion) and present footprinting comparisons in Figure 5.
- **Evidence pointer** Figure 5; Results section "Footprint comparison between scATAC platforms"
- **Concern** The Tn5 bias comparison is presented as a key result, but the analysis appears descriptive. The manuscript shows correlation scatterplots (Figure 5f, 5g) and example footprint tracks, but does not provide a quantitative comparison of Tn5 bias across platforms, cell types, or species. The claim of "identical" biases is strong and requires statistical support. Additionally, the relationship between the Tn5 bias analysis and the S2F model performance is not clearly articulated. If the biases are identical, does this mean footprinting is equally reliable across platforms? The manuscript would benefit from a more rigorous quantitative comparison and a clearer link to the S2F modeling results.
- **Why it matters** The Tn5 bias claim is a specific and potentially useful finding, but without quantitative support it remains anecdotal. The connection between platform-specific biases and downstream modeling performance is important for the community to understand which platforms are suitable for footprinting applications.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Cost analysis
- **Claim pointer** The authors state "The cost to generate a dataset of 67k cells using HyDrop v2 is estimated at 668 euros (excluding sequencing), which is an improvement compared to HyDrop v1 (852 euros), and 14 times cheaper than 10x (9338 euros, Figure 1f)" (Results).
- **Evidence pointer** Figure 1f; Supplementary Tables S4 and S5
- **Concern** The cost comparison is presented as a major advantage of HyDrop v2, but the analysis appears to consider only library preparation costs, excluding sequencing. The manuscript does not account for the higher sequencing depth required for HyDrop v2 (as acknowledged in the Discussion, "HyDrop v2 libraries reach a comparable number of unique fragments per cell to 10x data but require a higher sequencing depth"). The total cost including sequencing could substantially reduce or eliminate the cost advantage. The cost analysis should be presented as a total cost per usable cell or per usable fragment, including all consumables, labor, and sequencing.
- **Why it matters** Cost is a major factor in platform choice. An incomplete cost analysis could mislead readers and undermine the practical recommendations of the paper.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure descriptions
- **Affected element** Figure 2 and Figure 3 legends
- **Evidence pointer** Figure 2c, 2d, 3a legends
- **Issue** The figure legends are terse and do not fully explain the experimental design. For example, Figure 2c legend states "Model performance comparison (Test Pearson correlation) of the models shown in (b)" but does not specify what the error bars represent, how many models are compared, or what the statistical significance of differences is.
- **Required correction** Expand figure legends to include sample sizes, definition of error bars, statistical tests performed, and clear descriptions of each panel.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methods clarity
- **Affected element** Model training section
- **Evidence pointer** Methods, "Model training" subsection
- **Issue** The description of model training is incomplete. The manuscript states "We trained models with an identical model architecture and identical hyperparameters" but does not specify the hyperparameters, the number of training epochs, the learning rate, or the early stopping criteria. The description of the "dilated CNN model architecture" and "deeptopic_cnn model architecture" lacks sufficient detail for reproducibility.
- **Required correction** Provide full hyperparameter details, training procedures, and architecture specifications, or reference a public repository where these are documented.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and code availability statements
- **Evidence pointer** Not present in the provided text
- **Issue** The manuscript does not include data availability or code availability statements. Given the emphasis on open-source tools and the potential value of the generated atlases, these statements are essential.
- **Required correction** Add explicit statements describing where raw sequencing data, processed count matrices, trained models, and analysis code can be accessed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The terms "sequence-to-function (S2F) model" and "deep learning model" are used somewhat interchangeably. The manuscript would benefit from a clear definition of what constitutes an S2F model in this context and consistent usage throughout.
- **Required correction** Define S2F models early in the introduction and use the term consistently.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The Discussion does not adequately address limitations of the study, such as the confound between platform and cell number, the lack of statistical testing, the incomplete cost analysis, and the limited species examined (only mouse and fly).
- **Required correction** Add a dedicated limitations paragraph acknowledging these issues and suggesting how future work could address them.

## Risk / unsupported claims
- The claim that HyDrop v2 and 10x produce "identical Tn5 biases" is not quantitatively supported by the presented analysis.
- The claim that "lower fragment counts can be compensated for by increased cell numbers" is presented as a general principle but is only demonstrated for a limited set of conditions.
- The cost advantage of HyDrop v2 is presented without accounting for sequencing costs, which may substantially alter the conclusion.
- The claim of performing "the first benchmark" of scATAC platforms for S2F model training is not supported by a systematic literature review in the manuscript.
- The statement that "all major cell types" are uncovered in both atlases is not quantitatively demonstrated with cell type identification metrics.
- The claim that S2F models trained on different platforms "perform comparably" is not supported by statistical evidence.
- The assertion that the HyDrop v2 atlas requires "no batch correction" across 35 experiments is stated but not rigorously demonstrated with quantitative batch effect metrics.