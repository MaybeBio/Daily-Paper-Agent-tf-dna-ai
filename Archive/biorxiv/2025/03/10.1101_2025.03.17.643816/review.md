## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and interpretability of results as presented in the provided text
- **Shared manuscript claim summary** The authors present Omics Graph Learning (OGL), a graph neural network framework that integrates multi-omics data to predict gene expression across 20 cell lines and tissues. They claim high predictive accuracy, and through over 81 million in-silico perturbations, they uncover tissue-specific feature utilization, non-additive interactions among epigenetic marks, and context-dependent regulatory elements with both activating and repressive roles.
- **Visible evidence base** Abstract, Introduction, Results (partial), Methods (partial), Extended Data figure legends (partial), Supplementary figure/table references
- **Missing materials affecting confidence** Full Results section, all figures and tables, Supplementary Information, Methods details for data processing and model training, code repository contents

## Reviewer

- **Overall assessment** The manuscript presents a conceptually interesting and technically ambitious framework for integrating diverse genomic and epigenomic data into a graph-based deep learning model for gene expression prediction. The interpretability-first design and the scale of in-silico perturbation experiments are notable strengths. However, the current text, as provided, lacks sufficient detail in the Results and Methods sections to fully evaluate the validity of the core claims. The evidence for key conclusions, such as non-additive feature interactions and context-dependent bifunctionality, is presented in a summarized form without access to the underlying data or statistical analyses. The manuscript would benefit from a more detailed presentation of the results and a clearer articulation of the novelty relative to existing sequence-based and graph-based models.

- **Who would be interested in the results, and why** Researchers in computational genomics, regulatory genomics, and deep learning applied to biology would be interested. The framework offers a new way to integrate multi-omics data and provides a tool for generating hypotheses about regulatory mechanisms. The large-scale perturbation analysis and the focus on interpretability could be valuable for those studying gene regulation beyond sequence-based models.

- **Major strengths**
  1. The conceptual shift from sequence-based to feature-rich graph-based modeling is a timely and potentially impactful idea, directly addressing a known limitation of models like Enformer.
  2. The scale of in-silico perturbation experiments (over 81 million) is impressive and provides a rich resource for the community.
  3. The interpretability-first design, with multiple levels of analysis (broad-scale and fine-scale), is a thoughtful approach to dissecting model behavior.
  4. The integration of diverse data types (3D chromatin, histone marks, methylation, static genomic features) into a single framework is a significant technical undertaking.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for core claims
- **Claim pointer** The manuscript claims that OGL "uncovers tissue-specific regulatory patterns, non-additive relationships between epigenetic marks, and the context-dependent ability of elements to function as both activators and repressors."
- **Evidence pointer** Results sections "Broad-scale perturbations reveal non-additive, directional effects of molecular features" and "Node-level ablations reveal context-specific regulatory complexity"; Figures 3, 4, 5; Extended Data Fig. 4
- **Concern** The core biological conclusions are presented in a highly summarized narrative form. The text describes observations (e.g., "sustained deviations from additivity", "differential impacts of histone modifications") but does not provide the quantitative evidence, statistical tests, or effect sizes that would support these claims. For example, the claim of non-additivity is based on joint ablations, but the text does not describe how additivity was defined or tested, nor does it provide the magnitude of the deviations. Similarly, the classification of elements as activating or repressive is binary, but the criteria for this classification and the distribution of effects are not detailed. Without access to the figures and the underlying data, these central claims are not verifiable from the provided text.
- **Why it matters** The biological insights are the primary contribution of the paper. If the evidence for these insights is not rigorously presented and statistically supported, the paper's main conclusions are not established.
- **Resolution test** The authors must provide a detailed description of the statistical methods used to define and test for non-additivity, including specific examples with effect sizes and confidence intervals. The classification of activating/repressive elements must be clearly defined, and the distribution of effects and the performance of this classification (e.g., against CRISPRi data) must be shown. The figures must clearly present the data supporting these claims.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness and validation
- **Claim pointer** The manuscript claims "state-of-the-art performance compared to other deep learning models predicting gene-level expression in K562" and "highly accurate gene expression prediction across 20 cell lines and tissues."
- **Evidence pointer** Results section "OGL accurately predicts sample-specific gene expression"; Figure 2; Supplementary Table 3
- **Concern** The claim of state-of-the-art performance is difficult to assess. The text notes that "performance is difficult to compare directly due to varying data processing and model design," which is a valid caveat, but it does not provide a clear framework for comparison. The average Pearson's R of 0.83 across all samples and 0.87 for cell lines is presented, but the variance across samples, the number of genes tested, and the baseline performance of simpler models (e.g., linear models using the same features) are not reported. The comparison in Supplementary Table 3 is not visible. A robust validation would include a comparison to a non-graph baseline (e.g., a multi-layer perceptron on the same features) to demonstrate the added value of the graph structure.
- **Why it matters** The predictive performance is the foundation for the interpretability analyses. If the model is not demonstrably better than simpler alternatives, the biological conclusions drawn from its internal mechanisms are less compelling.
- **Resolution test** Provide a clear benchmark table with standard deviations, including comparisons to at least one non-graph deep learning baseline and a classical machine learning method (e.g., random forest) trained on the same features. Report performance per cell line/tissue and discuss the variance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and positioning
- **Claim pointer** The introduction states that "GNNs can represent the interactions that characterize gene regulatory networks as direct relationships" and that previous binning approaches "hinders interpretability."
- **Evidence pointer** Introduction; Results section "Feature-rich graph deep neural network model"
- **Concern** The novelty of the approach needs to be more clearly articulated. While the use of biologically meaningful nodes (genes, enhancers, promoters) is a clear advantage over fixed-size bins, the text does not thoroughly discuss other graph-based approaches to gene expression prediction that may use similar node definitions or feature sets. The specific contribution of the "feature-rich" aspect, the dynamic attention mechanism, and the multi-task learning setup should be clarified in the context of existing literature.
- **Why it matters** For a Nature-style audience, the paper must clearly state what is conceptually new and why it matters. If similar graph-based frameworks exist, the unique contribution of OGL needs to be highlighted.
- **Resolution test** Expand the discussion of related work to explicitly compare and contrast OGL with other graph-based models for regulatory genomics. Clearly state the specific architectural or conceptual innovations that OGL introduces.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction
- **Issue** The abstract and introduction are dense and use jargon (e.g., "feature rich graph neural networks", "relational inductive bias") that may be challenging for a non-specialist reader. The key innovation and the main biological findings could be stated more directly.
- **Required correction** Simplify the language in the abstract to make the core concept and findings accessible to a broader scientific audience. For example, explicitly state what "contextualizing gene expression" means in practice.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "Model training"
- **Evidence pointer** Methods section "Model training"
- **Issue** The description of the training process is incomplete. The text mentions "joint neural architecture and hyperparameter optimization search space" but does not provide details on the search space, the optimization algorithm, or the compute resources used.
- **Required correction** Provide a more detailed description of the hyperparameter search, including the ranges of values explored and the selection criteria for the final model.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and materials availability
- **Evidence pointer** Data and materials availability
- **Issue** The statement "All code is available at https://github.com/sciencesteveho/ogl" is insufficient. It is not clear if the code includes all scripts for data processing, model training, and analysis, or if it is just the model architecture.
- **Required correction** Clarify the contents of the code repository and provide a link to a stable release or a versioned archive.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative evidence and statistical analysis for the core biological claims (non-additivity, bifunctionality).
  - R1-M2: Incomplete validation of predictive performance against appropriate baselines.
  - R1-M3: Insufficient articulation of novelty relative to other graph-based methods.

- **Assessment against Nature-style criteria**
  - **Originality** The concept of using a graph of biological entities with rich features for gene expression prediction is a creative and potentially original contribution. The scale of the perturbation analysis is also notable. However, the originality of the specific architectural choices needs to be better positioned against existing work.
  - **Scientific importance** If the claims are fully validated, the framework could provide a new standard for integrative and interpretable modeling of gene regulation. The findings on non-additive interactions and context-dependent element function are potentially important, but their significance is currently undermined by a lack of evidence.
  - **Interdisciplinary readership** The topic is of interest to computational biologists, molecular biologists, and AI researchers. The manuscript's current form is likely too technical for a general biology audience and not technical enough for a machine learning audience. The presentation needs to be balanced.
  - **Technical soundness** The technical approach is ambitious, but the soundness of the conclusions is not yet established due to the missing details on validation and statistical analysis.
  - **Readability for nonspecialists** The abstract and introduction are not accessible to a non-specialist. The writing is dense and assumes significant prior knowledge.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising framework and interesting preliminary observations, but the core claims are not supported by the level of detail provided in this text. A full evaluation requires access to the figures, tables, and detailed methods. The authors should be encouraged to resubmit a revised version that addresses the major concerns, particularly the lack of quantitative evidence for the biological findings and the incomplete validation of the model's performance.