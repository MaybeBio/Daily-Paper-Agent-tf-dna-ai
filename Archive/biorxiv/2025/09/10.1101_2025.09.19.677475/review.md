## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability, author contributions, funding, acknowledgements)
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text. No external data or code was accessed.
- **Shared manuscript claim summary** The authors present Shorkie, a masked DNA language model pretrained on fungal genomes and fine-tuned on yeast expression data, which they claim substantially improves gene expression prediction, captures dynamic regulatory motif usage, and accurately predicts variant effects validated by eQTL and MPRA benchmarks.
- **Visible evidence base** Abstract, Introduction, Results sections (narrative form), Discussion, Online Methods, Data Availability statement. Figures and tables are referenced but not provided.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are referenced but not included. Quantitative results (e.g., performance metrics, statistical tests) are described narratively without numerical values. The new RNA-seq dataset is not described in detail beyond protocol information.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and timely approach to gene expression prediction in yeast using a pretrained DNA language model. The core idea, that evolutionary-scale pretraining on related fungal genomes can transfer regulatory knowledge to a compact genome with limited labeled data, is well-motivated and potentially impactful. The authors have assembled a substantial training dataset, including new high-resolution induction time-course data, and the architectural choices are reasonable. However, the manuscript as provided is essentially a narrative summary without the supporting quantitative evidence. The central claims of improved prediction, dynamic motif tracking, and variant effect accuracy cannot be evaluated without the figures, tables, and numerical results. The methods are described in sufficient detail to be reproducible, but the absence of results makes it impossible to assess whether the claims are supported. The work is likely of high interest to the genomics and regulatory biology communities, but the current form is not sufficient for publication.

- **Who would be interested in the results, and why** Computational biologists working on sequence-to-expression models, regulatory genomics researchers studying cis-regulatory code, yeast geneticists interested in transcriptional regulation, and researchers developing foundation models for genomics. The approach of cross-species pretraining for a data-sparse organism is a generalizable strategy that would interest a broad audience.

- **Major strengths**
  1. The conceptual framing of using evolutionary-scale pretraining to overcome the data limitation of a compact genome is novel and well-argued.
  2. The generation of a large new high-resolution induction time-course dataset is a significant contribution in itself.
  3. The architecture, combining a U-Net with transformer blocks, is a sensible and flexible design for multi-resolution sequence modeling.
  4. The breadth of validation, including motif discovery, dynamic motif tracking, eQTL classification, and MPRA concordance, is ambitious and appropriate.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The manuscript claims that Shorkie "substantially improves gene expression prediction" and "outperforms leading sequence-to-expression models in cis-eQTL classification."
  - **Evidence pointer** Results sections "Shorkie: LM transfer learning enables improved gene expression prediction" and "Shorkie predicts cis-eQTL regulatory impacts"; Figures 3 and 7 (not provided)
  - **Concern** The central quantitative claims of the paper are presented without any numerical data. No performance metrics (e.g., correlation coefficients, AUROC, AUPRC) are given in the text. The figures that would contain this information are not included in the provided material. It is impossible to assess the magnitude of the claimed improvements, the statistical significance of the differences, or the robustness of the comparisons.
  - **Why it matters** The primary contribution of this work is a quantitative improvement in prediction accuracy. Without the actual numbers, the claims are unverifiable and the scientific contribution cannot be assessed.
  - **Resolution test** Provide the full results section with all figures and tables, including exact performance values, confidence intervals, and statistical tests comparing Shorkie to all baselines.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental design
  - **Claim pointer** The manuscript claims that the new induction time-course data were used to fine-tune Shorkie and that the model "tracks dynamic cis-regulatory motif usage."
  - **Evidence pointer** Results section "Shorkie captures dynamic cis-regulatory motif changes across time-course TF inductions"; Figure 5 (not provided)
  - **Concern** The description of the new time-course experiments is incomplete. Only three TF perturbations are mentioned (MSN2, MSN4, MET4) in the results, but the methods state that 8 TF perturbations were performed. The selection criteria for these TFs, the number of replicates, the time points sampled, and the quality control metrics for the new dataset are not described. The validation of the dynamic motif tracking appears to rely on comparison with RNA-seq fold-changes, but the statistical framework for this comparison is not described.
  - **Why it matters** The new dataset is a key contribution and the dynamic tracking claim is a novel aspect of the work. Without a clear description of the experimental design and the analysis framework, the validity of the conclusions drawn from this data cannot be evaluated.
  - **Resolution test** Provide a complete description of the experimental design, including TF selection, replicate numbers, time points, and QC metrics. Describe the statistical methods used to compare predicted and experimental dynamic trajectories.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript claims that the "165_Saccharomycetales-trained model... represents the optimal evolutionary scale for S. cerevisiae generalization."
  - **Evidence pointer** Results section "Yeast language model design and training across evolutionary divergences"; Figure 1F-G (not provided)
  - **Concern** The selection of the optimal training set is based on validation loss, but the manuscript does not describe how this choice affects downstream task performance. It is unclear whether the lowest validation loss corresponds to the best performance on expression prediction, motif discovery, or variant effect prediction. The comparison across the four training sets (R64, 80_strains, 165_Saccharomycetales, 1341_Fungus) is only described in terms of loss, not in terms of the actual tasks the model is intended for.
  - **Why it matters** The choice of training data is a central design decision. If the optimal training set for language modeling is not optimal for downstream tasks, the model selection is potentially suboptimal.
  - **Resolution test** Provide a comparison of the four training-set models on the downstream tasks (expression prediction, motif discovery, variant effect prediction) to demonstrate that the chosen model is indeed optimal for the intended applications.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparison with existing methods
  - **Claim pointer** The manuscript claims Shorkie "outperforms leading sequence-to-expression models" and "outperformed DREAM models when predicting endogenous gene expression."
  - **Evidence pointer** Results sections "Shorkie predicts promoter variant effects validated by MPRA" and "Shorkie predicts cis-eQTL regulatory impacts"; Figures 6 and 7 (not provided)
  - **Concern** The comparison with existing models is described only in relative terms. The manuscript does not describe which specific models were compared, how they were trained or obtained, whether hyperparameters were optimized for each model, or whether the comparisons were statistically rigorous. The claim of outperformance is made without any quantitative context.
  - **Why it matters** A fair and rigorous comparison with existing methods is essential to establish the value of the new model. Without details on the comparison protocol, the claim of superiority cannot be verified.
  - **Resolution test** Provide a detailed description of the baseline models, their training procedures, hyperparameter tuning, and the statistical tests used to establish significant differences.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The phrase "remains challenging due to complex regulatory codes" is vague. The specific challenges (e.g., motif syntax, context-dependence, chromatin state) are not articulated.
  - **Required correction** Specify the key challenges in the abstract to better frame the contribution.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, "Shorkie LM data preprocessing"
  - **Evidence pointer** Methods section, paragraph on repeat masking
  - **Issue** The description of the repeat masking pipeline is detailed but the parameters for RepeatModeler and RepeatMasker are not fully specified (e.g., RepeatModeler's species-specific settings, RepeatMasker's -species flag).
  - **Required correction** Provide the exact command lines or configuration files used for the repeat masking pipeline.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, "Shorkie captures dynamic cis-regulatory motif changes"
  - **Evidence pointer** Results section, Figure 5D, 5I
  - **Issue** The correlation values between predicted and experimental RNA-seq (0.55-0.65 for MSN2, 0.45-0.70 for MSN4) are reported as ranges without confidence intervals or significance tests.
  - **Required correction** Report confidence intervals and p-values for all reported correlations.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data Availability statement
  - **Evidence pointer** Data Availability section
  - **Issue** The statement indicates that data are hosted on Google Cloud Storage and code on GitHub, but no accession numbers, version numbers, or DOIs are provided.
  - **Required correction** Provide stable identifiers (e.g., Zenodo DOI for code, GEO/SRA accession for data) to ensure long-term accessibility.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion, paragraph on model limitations
  - **Evidence pointer** Discussion section, paragraph on ChIP-exo limitations
  - **Issue** The discussion of ChIP-exo limitations is brief and does not address whether the model's performance on this assay type could be improved with different loss functions or target transformations, despite the methods mentioning this possibility.
  - **Required correction** Expand the discussion to consider potential remedies for the ChIP-exo limitations.

## Risk / unsupported claims
- The claim that Shorkie "substantially improves gene expression prediction" is unsupported without numerical results.
- The claim that Shorkie "outperforms leading sequence-to-expression models" is unsupported without details on the comparison protocol and results.
- The claim that the 165_Saccharomycetales training set is "optimal" is unsupported without downstream task comparisons.
- The claim that Shorkie "tracks dynamic cis-regulatory motif usage" is unsupported without the time-course analysis figures and statistical framework.
- The claim of "high concordance with massively parallel reporter assays" is unsupported without the correlation values and scatter plots.
- The claim that the new induction time-course dataset is of high quality is not verifiable without QC metrics and comparison to existing datasets.