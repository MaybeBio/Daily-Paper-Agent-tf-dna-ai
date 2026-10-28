## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, data/code availability statements)
- **Assessment boundary** Scientific and technical evaluation of the manuscript as submitted; no assessment of editorial fit or publication venue decisions
- **Shared manuscript claim summary** The authors propose a multi-label temporal convolutional framework for predicting transcription factor binding sites, claiming that multi-label learning can capture cooperative TF binding patterns and reveal biologically meaningful motifs, outperforming a Bi-LSTM baseline.
- **Visible evidence base** Abstract, Sections 1 through 6, Tables 1-3 (referenced), Figures 1-10 (referenced but not visible), References
- **Missing materials affecting confidence** Figures 1-10 not provided; Table 1-3 contents not visible; dataset identifiers not listed; code not provided; hyperparameter details referenced but not visible

## Reviewer

- **Overall assessment** The manuscript addresses a relevant problem in regulatory genomics, namely the shift from single-TF binary classification to multi-label TF binding prediction. The motivation is sound and the choice of TCNs is reasonable. However, the manuscript as presented is incomplete in critical ways. The absence of all figures and tables makes it impossible to evaluate the actual results, the claimed performance gains, or the biological validity of the attribution analysis. The methods section contains placeholder text and incomplete formal definitions. The comparison with the Bi-LSTM baseline is described qualitatively but the quantitative evidence is not visible. The attribution analysis is limited to a single dataset and the authors acknowledge that the pipeline is not fully adapted to the multi-label setting. The data and code availability statements are weak, with code available only upon request and dataset identifiers not listed. The manuscript has potential but the current submission does not establish the core claims from the provided evidence.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on TF binding prediction, regulatory genomics, and deep learning applications to genomics. The multi-label framing is of interest to researchers studying cooperative TF interactions. The TCN architecture comparison against RNN baselines may interest the broader deep learning for genomics community. The attribution analysis, if fully developed, would interest researchers focused on model interpretability in genomics.

- **Major Strengths**
  - The problem framing is novel and relevant: moving from single-TF binary classification to multi-label prediction is a meaningful step forward.
  - The motivation for using TCNs over RNNs and attention-based models is clearly articulated and technically sound.
  - The authors acknowledge limitations of their attribution pipeline and position their work as a hypothesis-generating framework.
  - The benchmarking against a widely used binary classification dataset provides a useful sanity check.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence completeness
  - **Claim pointer** The manuscript claims that the TCN-based model outperformed the Bi-LSTM baseline on almost all metrics across all datasets and labels, with significant gains in AP, AUC, F1, precision, and recall.
  - **Evidence pointer** Section 3.2, Figures 9, Tables 1-3 (not visible)
  - **Concern** All quantitative results are presented in figures and tables that are not included in the provided material. The reader cannot verify any of the claimed performance numbers, the magnitude of the gains, or the statistical significance of the differences. The text describes trends but provides no actual values.
  - **Why it matters** The central claim of the paper is that the TCN model achieves superior multi-label performance. Without the actual results, this claim is unverifiable and the scientific contribution cannot be assessed.
  - **Resolution test** Provide all figures and tables with clear axis labels, error bars or confidence intervals, and explicit numerical values for all metrics discussed in the text.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript states that the TCN architecture is based on Bai et al. and describes causal convolutions, dilated convolutions, and residual connections as the key components.
  - **Evidence pointer** Section 2.3, Figure 3 (not visible)
  - **Concern** The formal definitions of dilated convolution and residual connections are incomplete. The equation for dilated convolution is missing the summation and the residual connection equation is not fully specified. The text contains placeholder symbols and incomplete mathematical notation. The description of the receptive field and effective history is qualitative and lacks the formal treatment needed to understand the architectural choices.
  - **Why it matters** The technical contribution depends on the specific TCN architecture. Without complete formal definitions, the architecture cannot be reproduced or compared against other implementations.
  - **Resolution test** Provide complete mathematical definitions for all architectural components, including the dilated convolution equation, the residual block formulation, and the receptive field calculation.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The manuscript states that datasets were constructed from ENCODE ChIP-seq data and that the full list of ENCODE identifiers is available upon request.
  - **Evidence pointer** Section 2.1, Section 5
  - **Concern** The dataset construction is described at a high level but the specific ENCODE identifiers, peak calling parameters, filtering criteria, and preprocessing steps are not provided. The data availability statement says the full list of identifiers is available upon request, which is not consistent with open science best practices. The code is also only available upon request.
  - **Why it matters** Reproducibility is a core requirement for computational biology papers. Without access to the exact data and code, other researchers cannot replicate the results or build upon the work.
  - **Resolution test** Provide a complete list of ENCODE identifiers in the manuscript or supplementary material, and make the code publicly available on a repository with a DOI.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological validation
  - **Claim pointer** The attribution analysis reveals two known motifs belonging to MYC and E2F6, suggesting the model captures biologically meaningful patterns.
  - **Evidence pointer** Section 3.3, Figure 10 (not visible)
  - **Concern** The attribution analysis is performed only on the H-M-E2F dataset and the authors acknowledge that the pipeline is not fully adapted to the multi-label setting. The claim that the model captures biologically meaningful motifs is based on visual inspection of sequence logos, but no quantitative comparison against known motif databases is provided. The analysis is limited to two motifs and does not address whether the model captures cooperative binding patterns beyond individual motifs.
  - **Why it matters** The paper claims that multi-label learning can reveal cooperative TF interactions. The attribution analysis as described does not directly test this claim. A more rigorous analysis comparing discovered motifs against known databases and testing for co-binding patterns would strengthen the biological claims.
  - **Resolution test** Provide quantitative motif enrichment analysis against known databases, and extend the attribution analysis to at least one additional dataset to demonstrate generalizability.

  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Baseline comparison
  - **Claim pointer** The TCN model outperforms the Bi-LSTM baseline, with the highest gains on the least frequent class USF2, suggesting the TCN captures label-specific features the RNN cannot learn.
  - **Evidence pointer** Section 3.2
  - **Concern** The comparison is limited to a single Bi-LSTM baseline. No comparison is made against state-of-the-art deep learning models for TF binding prediction, such as DeepBind, DeepSEA, or BPNet. The authors acknowledge this for the binary case but not for the multi-label case. The claim that TCNs are superior to RNNs would be stronger with additional baselines.
  - **Why it matters** The scientific contribution depends on demonstrating that the proposed approach is competitive with or superior to existing methods. A single baseline is insufficient to establish this.
  - **Resolution test** Add at least one or two additional baseline models, ideally including a transformer-based model and a well-established CNN model for TF binding prediction.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.1, dataset description
  - **Evidence pointer** Section 2.1
  - **Issue** The description of the dataset construction is confusing. The text says "we used all the ChIP-seq profiles available on the ENCODE portal matching the selection criteria we now describe" but the selection criteria are not clearly enumerated. The relationship between the two approaches (enrichment-based and hand-curated) and the resulting datasets is not clearly explained.
  - **Required correction** Clearly enumerate the selection criteria and provide a step-by-step description of how each dataset was constructed.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 2.5, hyperparameters
  - **Evidence pointer** Section 2.5, Table 2 (not visible)
  - **Issue** The hyperparameter tuning is described but the final hyperparameters are only in Table 2, which is not visible. The text mentions a custom learning rate scheduler but does not describe the specific parameters.
  - **Required correction** Provide the final hyperparameters in the text or ensure Table 2 is included with full details.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Language
  - **Affected element** Section 3.2, dataset names
  - **Evidence pointer** Section 3.2
  - **Issue** The dataset names "D-5TF-3CLdataset" and "D-7TF-4CLdataset" appear without spaces in some places, making the text difficult to read.
  - **Required correction** Ensure consistent formatting of dataset names throughout the text.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 5, data availability
  - **Evidence pointer** Section 5
  - **Issue** The data availability statement is incomplete. The sentence about the manually curated dataset is cut off and does not specify the source track clearly.
  - **Required correction** Complete the data availability statement and provide clear information about all data sources.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 3.1, binary classification results
  - **Evidence pointer** Section 3.1, Table 3, Figures 7-8 (not visible)
  - **Issue** The text states the comparison is "unfavorable" for the TCN model but then says results are "comparable and in line with the state-of-the-art." This is contradictory and needs clarification.
  - **Required correction** Clarify whether the comparison is favorable or unfavorable and provide specific numbers to support the claim.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: All quantitative results are in missing figures and tables
  - R1-M2: Incomplete formal definitions of the architecture
  - R1-M3: Data and code not accessible for reproducibility

- **Assessment against Nature-style criteria**
  - **Originality** The multi-label framing for TF binding prediction is a meaningful departure from the standard single-TF binary classification paradigm. The application of TCNs to this problem is not entirely novel but the multi-label perspective adds a new dimension. However, the originality claim is weakened by the lack of visible results demonstrating what the multi-label approach uniquely enables.
  - **Scientific importance** The problem of cooperative TF binding is biologically important and the potential to predict multiple TF binding events simultaneously is valuable. If the claims are substantiated, this could be a useful contribution to the field. However, the current evidence base is insufficient to assess the magnitude of the contribution.
  - **Interdisciplinary readership** The work sits at the intersection of deep learning and regulatory genomics. The writing is accessible to computational biologists but may be challenging for experimental biologists due to the technical depth of the methods section. The biological motivation is well explained in the introduction.
  - **Technical soundness** The architectural choices are reasonable and well motivated. However, the incomplete formal definitions and the limited baseline comparison undermine the technical rigor. The attribution analysis is acknowledged as preliminary and not fully adapted to the multi-label setting.
  - **Readability for nonspecialists** The introduction is well written and accessible. The methods section is dense and contains placeholder text and incomplete equations. The results section is difficult to follow without the figures and tables. Overall readability is mixed.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant problem with a reasonable approach, but the absence of all figures and tables, incomplete technical definitions, and weak data/code availability statements prevent a proper evaluation of the claims. The authors should be encouraged to resubmit a complete version with all figures, tables, and formal definitions included, and with improved data and code availability.

## Risk / unsupported claims
- The claim that the TCN model outperforms the Bi-LSTM baseline on almost all metrics is unsupported because the quantitative results are in missing figures and tables.
- The claim that the attribution analysis reveals biologically meaningful motifs is weakly supported because the analysis is limited to one dataset and no quantitative comparison against known motif databases is provided.
- The claim that the TCN model captures label-specific features that the recurrent baseline cannot learn is unsupported because the evidence is in missing figures.
- The claim that the model exhibits robust performance in data-scarce regimes is unsupported because the relevant results are in missing figures.
- The claim that multi-label learning can reveal cooperative TF interactions is not directly tested by the presented analysis.
- The statement that the comparison with state-of-the-art binary classification is "unfavorable" is contradicted by the claim that results are "comparable and in line with the state-of-the-art."