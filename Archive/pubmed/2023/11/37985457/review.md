## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and significance of the claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose GNNLink, a supervised graph neural network framework that frames gene regulatory network inference from single-cell RNA-seq data as a link prediction task. The method uses a GCN-based encoder to learn gene features from expression data and a prior GRN, then predicts regulatory links via dot product scoring. Performance is evaluated against six baselines on seven BEELINE datasets.
- **Visible evidence base** Text descriptions of methods, results, and performance metrics (AUROC, AUPRC); references to Figures 2-5, Tables 1-2, and Supplementary Figures/Tables
- **Missing materials affecting confidence** All figures, tables, and supplementary materials; detailed mathematical formulations; hyperparameter settings; baseline method descriptions; statistical significance testing; ablation study details

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely GRN inference from scRNA-seq data using graph neural networks. The framing of GRN inference as a link prediction task is reasonable and the use of GCNs is well motivated. However, the manuscript as presented has several critical gaps that prevent full evaluation of the method's validity and contribution. The absence of figures, tables, and supplementary materials makes it impossible to verify the reported results or assess the methodological details. The writing contains multiple typographical and grammatical errors that detract from clarity. The novelty claim is weakened by the existence of prior work such as GENELink, which the authors themselves cite, and the incremental nature of the proposed approach is not clearly articulated. The experimental evaluation, as described, lacks statistical rigor and does not adequately address potential confounding factors such as data leakage or the choice of negative sampling strategy.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, particularly those interested in applying deep learning and graph-based methods to single-cell data. The work may also be of interest to researchers developing supervised approaches for biological network reconstruction and those working on link prediction problems in genomics.

- **Major strengths** The problem is well motivated and relevant. The use of a GCN-based encoder for gene feature learning is a sensible design choice. The authors evaluate on multiple datasets with diverse ground truth sources, which is commendable. The provision of code and data on GitHub supports reproducibility. The parameter analysis and robustness studies, as described, suggest a thorough empirical investigation.

- **Major Concerns** The following concerns are identified:

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim superior performance of GNNLink over six baseline methods across seven datasets, with specific quantitative improvements reported in the text.
- **Evidence pointer** Figure 3, Table 2, location not provided
- **Concern** The reported performance metrics and comparisons cannot be verified because the actual figures and tables are not included in the provided material. The text states specific percentage improvements (e.g., 9.2% and 18.3% higher AUROC than GENELink and GNE) but without the underlying data, statistical tests, or visualization, these claims are unverifiable. Furthermore, no confidence intervals or significance tests are mentioned, making it impossible to assess whether observed differences are meaningful.
- **Why it matters** The central claim of the paper is that GNNLink outperforms existing methods. Without access to the actual results and appropriate statistical analysis, this claim cannot be evaluated. The absence of error bars or significance testing is particularly concerning given the known variability in deep learning performance across random seeds.
- **Resolution test** Provide the actual figures and tables with error bars or confidence intervals, and include statistical significance testing (e.g., paired tests across datasets) to support the claimed improvements.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The authors describe a GCN-based interaction graph encoder and a loss function for training, but the mathematical formulations are incomplete.
- **Evidence pointer** Methods section, "GCN-based interaction graph encoder" and "Model optimization", location not provided
- **Concern** The GCN layer update equation is referenced but not fully presented. The loss function is described in words but the exact formulation, including the role of the weighting factor lambda and the composition of positive and negative sample sets, is not fully specified. The negative sampling strategy is described as "uniform random" but the implementation details, such as the ratio of negatives to positives and whether hard negatives are mined adaptively, are unclear.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without complete mathematical specifications and implementation details, other researchers cannot reimplement or build upon the method. The choice of negative sampling strategy is particularly important for link prediction tasks and can significantly affect performance.
- **Resolution test** Provide complete mathematical formulations for the GCN layers, the loss function, and the negative sampling procedure. Include pseudocode or a detailed algorithm box.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and positioning
- **Claim pointer** The authors state that GNNLink is a "novel framework" and that it addresses limitations of prior methods, particularly GENELink.
- **Evidence pointer** Introduction, last paragraph; Discussion, location not provided
- **Concern** The manuscript does not clearly articulate the specific limitations of GENELink that GNNLink overcomes, beyond a brief mention of "lack of negative sample data and high computational complexity." The methodological differences between GNNLink and GENELink are not systematically compared. Given that GENELink also uses graph attention networks for link prediction, the incremental contribution of GNNLink needs to be more clearly delineated.
- **Why it matters** For a methods paper, the novelty and contribution must be clearly established. If GNNLink is largely similar to GENELink with minor modifications, the scientific contribution is limited. The authors need to explicitly state what is new and why it matters.
- **Resolution test** Add a dedicated section or paragraph that systematically compares GNNLink with GENELink and other GNN-based GRN inference methods, highlighting specific architectural and methodological differences and their implications for performance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Experimental rigor
- **Claim pointer** The authors claim that GNNLink demonstrates "robustness" and "stability" based on experiments with reduced training data and added noise.
- **Evidence pointer** "Robustness of GNNLink" section, Figure 4, Supplementary Table S1, location not provided
- **Concern** The robustness experiments are described only qualitatively. The text states that performance improves with more training data and that all methods decline with added noise, but no quantitative results are provided. The claim that GNNLink "exhibits good stability and robustness, effectively avoiding the issue of overfitting" is not supported by specific evidence. The comparison with other methods under these conditions is not described.
- **Why it matters** Robustness is an important property for practical applicability. Without quantitative results and comparisons, the robustness claims are unsubstantiated. The statement about avoiding overfitting is particularly problematic without learning curves or regularization analysis.
- **Resolution test** Provide quantitative results for the robustness experiments, including performance metrics at each training data fraction and noise level, with comparisons to baseline methods.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Imputation analysis
- **Claim pointer** The authors state that imputation with DeepImpute improves GNNLink performance by 5.55% (AUROC) and 6.12% (AUPRC) on average.
- **Evidence pointer** "Impacts of single-cell data imputation" section, Figure 5, location not provided
- **Concern** The imputation analysis is presented as a single result without comparison to other imputation methods or analysis of why imputation helps. The authors do not discuss potential risks of imputation, such as introducing artificial correlations or masking true biological variability. The choice of DeepImpute over other available methods is not justified.
- **Why it matters** The imputation result has practical implications for users of the method. Without a broader analysis, it is unclear whether the improvement is specific to DeepImpute or generalizable. The potential negative effects of imputation should be discussed.
- **Resolution test** Include comparisons with at least one additional imputation method and discuss the trade-offs of imputation in the context of GRN inference.

- **Minor Comments** The following minor comments are identified:

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Throughout the manuscript
- **Evidence pointer** Multiple sections, location not provided
- **Issue** The manuscript contains numerous typographical and grammatical errors, including "have have" in the GCN section, inconsistent use of tense, and awkward phrasing. These errors detract from readability and professionalism.
- **Required correction** Thorough proofreading and editing for grammar and style.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** GCN formulation
- **Evidence pointer** "GCN-based interaction graph encoder" section, location not provided
- **Concern** The normalization of the adjacency matrix is described as A~ = D^(-1/2) A D^(1/2), which appears to be a typographical error. The standard symmetric normalization is D^(-1/2) A D^(-1/2).
- **Required correction** Correct the normalization formula to the standard symmetric normalization.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of contribution
- **Affected element** Introduction, final paragraph
- **Evidence pointer** "our main contributions are summarized as follows", location not provided
- **Concern** The list of contributions is not actually provided in the text. The sentence ends without enumerating the contributions.
- **Required correction** Provide the enumerated list of contributions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Baseline description
- **Affected element** "Baseline methods" section
- **Evidence pointer** Location not provided
- **Concern** The baseline methods are listed but not described. The reader is referred to supplementary materials for details, which are not available in the provided material.
- **Required correction** Provide brief descriptions of each baseline method in the main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Parameter sensitivity
- **Affected element** "Parameter analysis" section
- **Evidence pointer** Figure 2, location not provided
- **Concern** The parameter analysis is described but the specific parameter ranges and their effects are not detailed in the text.
- **Required correction** Provide more detail on the parameter search space and the rationale for chosen values.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data preprocessing
- **Affected element** "Preprocessing of raw data" section
- **Evidence pointer** Location not provided
- **Concern** The preprocessing steps are described but the final number of genes retained after filtering is not reported for each dataset.
- **Required correction** Include the number of genes and cells for each dataset after preprocessing.

## Risk / unsupported claims
- The claim of "superior performance" over all baselines cannot be verified without the actual figures and statistical analysis.
- The claim that GNNLink "effectively avoids overfitting" is not supported by the provided evidence.
- The claim of "robustness" across dataset scales is not quantitatively substantiated.
- The statement that GNNLink can be applied to "diverse cell RNA-seq datasets and plant cells" is speculative and not supported by experiments.
- The claim that the method addresses the "lack of negative sample data" limitation of GENELink is not clearly demonstrated.
- The reported improvements of 9.2% and 18.3% in AUROC and 5.55% and 6.12% in AUROC/AUPRC after imputation are unverifiable without the underlying data.
- The computational complexity comparison in Table 2 cannot be assessed without the table contents.