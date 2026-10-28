## Review setup
- **Input scope** Full manuscript text, including abstract, background, results, discussion, methods, and supplementary information descriptions.
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and clarity of claims based solely on the provided manuscript text. No external data or code were accessed.
- **Shared manuscript claim summary** The authors present DeepHBV, an attention-based deep learning model using convolutional neural networks, to predict hepatitis B virus (HBV) integration sites in the human genome. The model is trained and tested on data from the dsVIS database, with additional validation on the independent VISDB dataset. The authors report that adding genomic features, specifically repeat peaks and TCGA Pan-Cancer peaks, improves model performance. They further use the attention mechanism to identify transcription factor binding sites (TFBS) enriched near predicted integration sites, suggesting novel integration preferences.
- **Visible evidence base** Main text, Figure 1 (model architecture), Figure 2 (ROC/PR curves), Figure 3 (attention weight distributions), Figure 4 (genomic context of attention-intensive sites), Table 1 (cross-validation metrics), Table 2 (enriched TFBS motifs), and references to supplementary files (Additional files 1-4).
- **Missing materials affecting confidence** Supplementary figures and tables (Additional files 1-4) were not provided. The full model architecture details, hyperparameter settings, and training procedures are only partially described. The exact composition of the training and testing datasets, including the number of unique integration sites and potential sample overlap, is not fully detailed. Code and trained model weights are not mentioned as being publicly available.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely topic, applying deep learning to predict HBV integration sites, which is a key step in HBV-related carcinogenesis. The use of an attention mechanism to provide interpretability is a commendable approach. However, the current manuscript has several significant methodological weaknesses and reporting gaps that prevent a full assessment of the model's validity and the robustness of the biological conclusions. The performance improvement from adding genomic features is presented, but the analysis lacks critical controls and comparisons. The biological interpretation, particularly the TFBS enrichment, is based on a limited and potentially biased sample selection. The manuscript would benefit from a more rigorous evaluation framework, clearer reporting of methods, and a more cautious interpretation of the findings.
- **Who would be interested in the results, and why** Researchers in computational biology, virology, and cancer genomics would be interested. Specifically, those studying viral integration mechanisms, developing predictive models for genomic features, and investigating the role of HBV in hepatocellular carcinoma would find the model and the identified TFBS motifs of potential interest. The work could also be relevant to researchers applying deep learning to other viral integration or genomic feature prediction problems.
- **Major strengths**
    - The study addresses a clinically and biologically important problem: understanding HBV integration preferences.
    - The application of an attention-based deep learning model is a modern and appropriate approach for sequence-based prediction tasks.
    - The use of an independent dataset (VISDB) for validation is a positive aspect of the study design.
    - The attempt to interpret the model's predictions through attention weights and TFBS enrichment is a valuable step towards biological insight.
- **Major Concerns**
    - **R1-M1**: The baseline performance of DeepHBV (AUROC 0.6363) is only marginally better than random, and the improvement from adding genomic features is presented without a clear comparison to simpler models or a demonstration that the model is learning HBV-specific signals rather than general sequence features.
    - **R1-M2**: The methodology for creating positive and negative training samples is not described with sufficient detail. The criteria for selecting negative samples, the genomic distance from known integration sites, and the potential for overlapping or redundant samples are not fully addressed, which could lead to data leakage and inflated performance metrics.
    - **R1-M3**: The biological interpretation, particularly the TFBS enrichment analysis, is based on a small, highly selected subset of samples (those with prediction values > 0.95). This selection bias could lead to the identification of spurious motifs that are not representative of the broader integration site population.
    - **R1-M4**: The manuscript lacks a clear statement on data and code availability, which is essential for reproducibility and for the community to build upon this work.
- **Minor Comments**
    - **R1-m1**: The description of the model architecture is incomplete. The number of layers, filter sizes, pooling strategies, and the specific implementation of the attention mechanism are not fully specified.
    - **R1-m2**: The choice of the 2000 bp window size is justified empirically, but a more thorough analysis of the effect of window size on performance would strengthen the paper.
    - **R1-m3**: The manuscript would benefit from a comparison with other state-of-the-art prediction tools or simpler machine learning baselines (e.g., logistic regression on k-mer frequencies) to contextualize the performance of DeepHBV.
    - **R1-m4**: The discussion of the biological relevance of the identified TFBSs is somewhat speculative. The authors should more clearly distinguish between correlation and causation and suggest specific, testable hypotheses.
    - **R1-m5**: The text in the Results section describing the attention weight distribution is somewhat unclear. A more precise description of the normalization and visualization procedure would be helpful.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**
    - **Originality**: The application of an attention-based deep learning model to HBV integration site prediction is a novel combination, but the underlying concept of using sequence features for prediction is not new. The originality is moderate.
    - **Scientific importance**: The problem is important, but the current evidence does not strongly demonstrate that DeepHBV provides a significant advance over existing methods or yields fundamentally new biological insights. The importance is currently not fully established.
    - **Interdisciplinary readership**: The topic is of interest to a niche but significant interdisciplinary audience at the intersection of computational biology, virology, and oncology. The broad appeal is limited.
    - **Technical soundness**: The technical soundness is currently questionable due to the lack of detailed methodology, potential for data leakage, and the absence of robust baseline comparisons. The evaluation is not yet convincing.
    - **Readability for nonspecialists**: The manuscript is generally readable, but the methods section is dense and would be challenging for a non-specialist to follow. The biological interpretation section is more accessible.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the major methodological concerns and lack of critical details must be addressed before the claims can be considered valid.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that DeepHBV "effectively predicts HBV integration sites" and that adding genomic features "significantly improved model performance."
- **Evidence pointer** Results section, Figure 2, Table 1
- **Concern** The baseline performance of the model (AUROC 0.6363) is only slightly above 0.5, which is a weak starting point. The improvement to 0.9430 with TCGA Pan-Cancer features is substantial, but it is unclear if this is due to the model learning a meaningful biological signal or if it is an artifact of the data preparation. The authors do not compare DeepHBV to a simpler model, such as a logistic regression or a random forest on k-mer frequencies, to demonstrate that the complex deep learning architecture is necessary or superior. Furthermore, the model is trained and tested on data from the same database (dsVIS), and the improvement from adding features is not validated with a proper ablation study that controls for the number of features or the model capacity.
- **Why it matters** Without a robust baseline comparison and a clear demonstration that the model is not overfitting or learning trivial patterns, the claim of "effective prediction" is not convincing. The reported performance could be a result of the specific data split or the model's ability to memorize the training set rather than generalize.
- **Resolution test** The authors should provide a comparison with at least one simpler baseline model (e.g., logistic regression, SVM, or a random forest) trained on the same data. They should also perform an ablation study to show the contribution of each component of the model (e.g., CNN vs. attention). Additionally, they should report performance on a more challenging and realistic test set, such as a hold-out chromosome or a dataset with a different distribution of integration sites.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The methods describe the preparation of positive and negative samples but lack critical details.
- **Evidence pointer** Methods section, Data preparation
- **Concern** The description of negative sample selection is insufficient. The authors state that "negative samples should be twice the number of positive samples" and that regions within 50,000 bp of known integration sites were ignored. However, it is not clear how the negative samples were randomly selected from the remaining regions. Were they selected from the entire genome? Were they matched for GC content, repeat density, or other confounding factors? The lack of detail makes it impossible to assess the potential for data leakage. For example, if a negative sample is selected from a region that is close to a known integration site but just outside the 50,000 bp exclusion window, it could be a false negative, which would make the model's task artificially easier.
- **Why it matters** The validity of the entire model hinges on the quality of the training data. If the negative samples are not representative of the true non-integration background, the model's predictions and the subsequent biological interpretations will be unreliable. The reported AUROC and AUPR values could be inflated by a poorly constructed negative set.
- **Resolution test** The authors should provide a detailed, step-by-step description of the negative sample selection process, including the exact criteria and any filtering steps. They should also perform a sensitivity analysis by generating negative samples using different strategies (e.g., random genomic regions, regions matched for GC content, or regions from other chromosomes) and show that the model's performance is robust to these choices.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the TFBS enrichment analysis "revealed a novel integration preference for HBV."
- **Evidence pointer** Results section, Table 2, Figure 4
- **Concern** The TFBS enrichment analysis was performed only on a subset of samples with prediction values higher than 0.95. This is a highly selected and potentially biased subset. The authors do not provide the number of samples in this subset, nor do they compare the enriched motifs in this subset to those found in the full set of positive samples or in a set of random genomic regions. The enrichment of motifs like AR-halfsite, Arnt, and CLOCK could be a general property of the genome or a result of the model's specific predictions, rather than a true biological preference of HBV integration.
- **Why it matters** The biological conclusions are a major part of the paper's significance. If the TFBS enrichment is an artifact of the analysis strategy, the claim of a "novel integration preference" is not supported. The authors need to demonstrate that the identified motifs are specifically enriched in HBV integration sites and not in the general genomic background.
- **Resolution test** The authors should perform the TFBS enrichment analysis on the full set of positive samples and on a matched set of negative samples. They should also compare the enriched motifs to those found in a set of random genomic regions. The analysis should be repeated with different prediction thresholds to show that the results are not dependent on a specific cutoff.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes a new model but does not state whether the code or trained model is available.
- **Evidence pointer** Methods section, DeepHBV model evaluation
- **Concern** The manuscript does not include a "Data Availability" or "Code Availability" statement. For a computational biology paper, the availability of the source code and the trained model is essential for reproducibility and for other researchers to apply the method to their own data. Without this, the work cannot be fully evaluated or built upon.
- **Why it matters** The lack of code and data availability severely limits the impact and utility of the work. It prevents independent verification of the results and hinders the adoption of the method by the research community.
- **Resolution test** The authors should provide a clear statement on the availability of the code, the trained model, and the processed datasets. Ideally, they should provide a link to a public repository (e.g., GitHub, Zenodo) and a DOI.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, Feature extraction
- **Evidence pointer** Methods section, Feature extraction
- **Issue** The description of the model architecture is incomplete. The number of convolutional layers, filter sizes, pooling sizes, and the specific implementation of the attention mechanism are not fully specified. The text mentions "two de-convolutions and one de-pooling operation" for visualizing attention, but the forward pass architecture is not clear.
- **Required correction** Provide a complete description of the model architecture, including a table or figure that lists all layers, their parameters, and the flow of data. This is essential for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Model performance
- **Evidence pointer** Results section, Figure 2, Table 1
- **Issue** The text states that the 2000 bp length had the "largest accuracy... and the most of the performance results among all tested lengths." This phrasing is awkward and unclear. It is not clear which metric was used to select the optimal length.
- **Required correction** Rephrase the sentence to clearly state that the 2000 bp length was selected because it yielded the highest performance across most metrics, and specify which metric was the primary criterion.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, TFBS enrichment
- **Evidence pointer** Results section, Table 2
- **Issue** The list of enriched TFBSs is presented as a long, unformatted list within the text. This is difficult to read and interpret.
- **Required correction** Present the list of enriched TFBSs in a clear table format, with columns for the TF name, p-value, and possibly the number of target sequences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the biological relevance of the identified TFBSs is somewhat speculative. The authors mention that these TFs are "related to tumor development" but do not provide a specific mechanistic hypothesis for how their binding near integration sites could promote carcinogenesis.
- **Required correction** Strengthen the discussion by proposing specific, testable hypotheses. For example, the authors could suggest that the binding of CLOCK or BMAL1 at these sites might alter local chromatin structure, making the region more accessible for integration.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Attention mechanism
- **Evidence pointer** Results section, Figure 3
- **Issue** The description of the attention weight distribution is unclear. The text states that "a cluster of attention weights that were much higher than other weights in the same sample often occurred in positive samples." It is not clear what constitutes a "cluster" or how this was quantified.
- **Required correction** Provide a more precise definition of the "cluster" and describe the statistical method used to determine that this pattern is more frequent in positive samples.

## Risk / unsupported claims
- The claim that DeepHBV "effectively predicts" HBV integration sites is not fully supported due to the lack of comparison with baseline models and the potential for data leakage in the negative sample construction.
- The claim of a "novel integration preference for HBV" based on TFBS enrichment is not supported, as the analysis was performed on a biased subset of high-confidence predictions without proper controls.
- The claim that the attention mechanism "helps determine the investigated patterns" and "highlights positions with potentially important biological meanings" is not rigorously validated. The authors do not demonstrate that the attention weights are more informative than other feature attribution methods.
- The generalizability of the model to other datasets or viral integration events is not assessed. The validation on VISDB is a positive step, but the performance drop from dsVIS to VISDB is not discussed in detail.