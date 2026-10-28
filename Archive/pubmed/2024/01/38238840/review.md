## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, figure legends) as provided.
- **Assessment boundary** Scientific and technical evaluation of the claims, methodology, and evidence presented in the provided text. No assessment of supplementary figures or external data beyond what is described.
- **Shared manuscript claim summary** The authors present SupirFactor, a knowledge-primed autoencoder framework for gene regulatory network (GRN) inference and transcription factor activity (TFA) estimation. The model constrains the first latent layer to known TF-target relationships from a prior network, enabling direct interpretation of latent activations as TFA. A novel metric, explained relative variance (ERV), is introduced for ranking and interpreting GRN edges. The authors benchmark SupirFactor against existing methods on bacterial, yeast, and human PBMC datasets, and demonstrate applications including context-specific GRN inference, TFA estimation, and pathway analysis via a hierarchical extension with meta-TFs (mTFs).
- **Visible evidence base** Main text figures (Fig. 1-5) and tables (Table 1) as referenced; methods section describing model architecture, training, and data preprocessing. Supplementary figures referenced but not provided.
- **Missing materials affecting confidence** Supplementary figures (Additional file 1: Figs. S1-S13) are referenced extensively but not available for review. Detailed hyperparameter settings, model training curves, and statistical significance values for key comparisons are not fully described in the provided text. Code availability and implementation details are not specified.

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting approach to GRN inference that addresses a key limitation of deep learning models: interpretability. The idea of using prior knowledge to constrain latent space structure is not entirely new, but the specific formulation, the ERV metric, and the demonstration across multiple organisms and data types are valuable contributions. The results are generally supportive of the claims, but several technical details and validation aspects require clarification and strengthening before the case is fully established. The manuscript is well-written and the figures, as described, appear informative. The main concerns relate to the rigor of benchmarking, the statistical significance of key results, and the generalizability of the approach.

- **Who would be interested in the results, and why** Researchers in computational biology, specifically those working on gene regulatory network inference, single-cell transcriptomics analysis, and interpretable machine learning for genomics. The paper offers a practical tool (SupirFactor) and a metric (ERV) that could be adopted by the community. The demonstration of TFA estimation and pathway analysis in both yeast and human PBMCs broadens the potential audience to experimental biologists interested in regulatory mechanisms.

- **Major strengths**
  1. The core idea of structure-primed embedding is elegant and directly addresses the interpretability problem in deep learning for GRNs.
  2. The ERV metric is a novel and potentially useful contribution for model interpretation beyond this specific application.
  3. The evaluation across multiple datasets (prokaryotic, fungal, human) and data types (bulk, single-cell, multi-omic) is commendable and demonstrates versatility.
  4. The application to context-specific GRN inference and the identification of cell-type-specific TFA and mTF activity in PBMCs are compelling demonstrations of biological utility.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Validation
  - **Claim pointer** The claim that "SupirFactor performs favorably" compared to current state-of-the-art GRN inference methods (Results, "SupirFactor benchmarking demonstrates improved biological regulatory network recovery").
  - **Evidence pointer** Figure 2C; Methods, "SupirFactor benchmark" (not explicitly detailed in provided text).
  - **Concern** The benchmarking comparison appears limited. The text mentions comparison to the Inferelator, GRNBoost2, and GENIE3, but the details of this comparison are not provided in the text. It is unclear if the comparison is fair (e.g., same data splits, same hyperparameter tuning for baselines, same evaluation metrics). The claim of "favorable" performance needs a more rigorous and transparent benchmarking setup, including statistical tests to show significance of any improvements.
  - **Why it matters** Without a rigorous and fair comparison, the central claim of improved performance is not convincingly established. The reader cannot assess whether the observed performance is due to the model architecture or to favorable evaluation conditions.
  - **Resolution test** Provide a detailed description of the benchmarking protocol, including data splits, hyperparameter selection for all methods, and the exact evaluation metrics. Include statistical significance tests (e.g., Wilcoxon signed-rank test) across multiple runs or datasets to support the claim of improvement.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Reproducibility
  - **Claim pointer** The claim that ERV is a valid metric for ranking and interpreting GRN edges (Results, "SupirFactor benchmarking demonstrates improved biological regulatory network recovery"; Methods, "Explained relative variance (ERV)").
  - **Evidence pointer** Figure 2A; Methods, "Explained relative variance (ERV)".
  - **Concern** The ERV metric is central to the paper's contribution, but its properties are not fully explored. The text states it is based on the coefficient of partial determination, but the behavior of ERV under different conditions (e.g., correlated TFs, non-linear interactions, noise levels) is not analyzed. The claim that ERV is superior to using raw model weights for ranking edges is supported by a single comparison (Fig. 2A), but the robustness of this finding is unclear. The threshold for what constitutes a "predictive" edge (ERV > 0) is not justified.
  - **Why it matters** If ERV is not a stable or reliable metric, the interpretability and utility of the model are compromised. The paper's contribution hinges on this metric being a meaningful and robust measure of edge importance.
  - **Resolution test** Provide a more detailed analysis of ERV's properties, including its behavior on simulated data with known ground truth, its sensitivity to model architecture and hyperparameters, and a comparison to other interpretation methods (e.g., permutation importance, SHAP values). Justify the choice of threshold for edge inclusion.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance / Novelty
  - **Claim pointer** The claim that the hierarchical model "facilitates biological analysis acquiring novel functional and regulatory insight" (Conclusion) and that mTFs represent "regulatory pathways".
  - **Evidence pointer** Figure 4; Results, "Hierarchical SupirFactor combines TFs into pathways".
  - **Concern** The interpretation of mTFs as pathways is based on enrichment analysis of target genes. While this is a reasonable approach, the novelty and depth of the biological insight are not fully demonstrated. The analysis appears descriptive (e.g., identifying mTFs enriched for glycolysis). It is not clear if this provides new biological knowledge beyond what could be obtained with standard pathway analysis tools on differentially expressed genes. The claim of "novel insight" needs to be substantiated with a more focused biological validation or a comparison to existing methods.
  - **Why it matters** The paper positions the hierarchical model as a tool for generating biological hypotheses. If the insights are not demonstrably novel or are simply recapitulating known biology, the impact of the work is diminished.
  - **Resolution test** Provide a more in-depth biological validation of one or two mTFs, e.g., by showing that the predicted target genes are co-regulated under specific conditions, or by comparing the mTF activity to known pathway activity scores. Alternatively, demonstrate that the mTF layer can identify regulatory modules that are not captured by standard clustering or pathway analysis methods.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness / Validation
  - **Claim pointer** The claim that TFA estimated by SupirFactor is a better estimate of TF activity than expression (Results, "SupirFactor model regulation of mammalian PBMCs with multimodal single cell sequencing data").
  - **Evidence pointer** Figure 3; Results, "SupirFactor model regulation of mammalian PBMCs with multimodal single cell sequencing data".
  - **Concern** The validation of TFA is largely based on correlation with known biology (e.g., cell cycle phases, response to rapamycin). While this is encouraging, it is not a direct validation. The comparison to Inferelator's TFA is mentioned (Fig. 3C), but the details and significance of this comparison are not provided. The claim that TFA is "distinct from expression" is shown, but the added value of TFA over expression for predicting target gene expression is not quantified.
  - **Why it matters** The paper's contribution includes TFA estimation. If the estimated TFA is not demonstrably more informative than expression, the practical utility of this aspect is questionable.
  - **Resolution test** Provide a quantitative comparison of TFA vs. expression in terms of their ability to predict target gene expression on held-out data. Include a more detailed comparison to Inferelator's TFA, including statistical significance.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity / Reproducibility
  - **Affected element** Methods, "Data preprocessing and model parameterisation"
  - **Evidence pointer** Methods section.
  - **Issue** The description of hyperparameter selection is vague. The text mentions cross-validation for L2 and dropout but does not specify the range of values tested, the criteria for selection, or the final chosen values for each dataset.
  - **Required correction** Provide a table or detailed text listing the hyperparameters (learning rate, batch size, number of epochs, L2 values, dropout values, architecture details) for each model and dataset.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "Epigenetic masking"
  - **Evidence pointer** Equation 16 and surrounding text.
  - **Concern** The epigenetic masking procedure is described briefly. It is unclear how the ATAC-seq data is used to mask the input expression data. Is it a binary mask, a soft mask, or a multiplicative scaling? The equation is not fully explained in the provided text.
  - **Required correction** Provide a more detailed explanation of the masking procedure, including a clear definition of all variables in Equation 16 and a description of how the mask is applied during training and inference.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Results, "SupirFactor benchmarking demonstrates improved biological regulatory network recovery"
  - **Evidence pointer** Figure 2.
  - **Issue** The text describing Figure 2 is dense and could be clearer. The differences between panels (A) and (B) are not immediately obvious from the text.
  - **Required correction** Add a sentence or two to clarify the specific comparison being made in each panel of Figure 2 and the key takeaway from each.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results, "Hierarchical SupirFactor combines TFs into pathways"
  - **Evidence pointer** Figure 4.
  - **Issue** The selection of the 12 glycolysis-enriched mTFs for detailed analysis is not justified. Why these 12? Are they the most significant? The criteria for focusing on this subset should be stated.
  - **Required correction** State the criteria for selecting the 12 mTFs for detailed analysis (e.g., highest enrichment score, largest number of target genes).

- **Technical failings that need to be addressed before the case is established**
  - R1-M1 (Benchmarking rigor) and R1-M2 (ERV validation) are the primary technical issues that need to be resolved. The lack of detail in the benchmarking protocol and the limited analysis of ERV's properties prevent a full assessment of the method's validity and performance.

- **Assessment against Nature-style criteria**
  - **Originality** The concept of using prior knowledge to structure the latent space of an autoencoder for GRN inference is a creative and useful idea. The ERV metric is a novel contribution. However, the individual components (autoencoders, prior knowledge integration, feature importance metrics) are established; the originality lies in their specific combination and application.
  - **Scientific importance** GRN inference and TFA estimation are important problems in biology. A method that improves interpretability and provides a metric for model understanding could have a significant impact on the field. The demonstration of cell-type-specific TFA and pathway analysis in PBMCs suggests practical utility.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and bioinformaticians. The biological applications (yeast, PBMCs) may attract some experimental biologists, but the technical nature of the manuscript may limit its broader appeal.
  - **Technical soundness** The technical soundness is currently not fully established due to the concerns raised about benchmarking and ERV validation. The model architecture is reasonable, but the evidence supporting its superiority is incomplete.
  - **Readability for nonspecialists** The manuscript is well-written but is highly technical. The abstract and introduction are accessible, but the methods and results sections require a strong background in machine learning and genomics. The use of equations and model descriptions may be challenging for a general reader.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the potential impact is significant. However, the current evidence is insufficient to fully support the claims of improved performance and biological insight. The authors must address the concerns regarding benchmarking rigor and ERV validation to make a convincing case.