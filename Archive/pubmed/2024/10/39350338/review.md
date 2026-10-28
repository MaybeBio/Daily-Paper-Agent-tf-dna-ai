## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific and technical evaluation of the reported method, experimental design, results, and claims; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors propose MLSNet, a deep learning architecture combining multisize convolutional fusion with LSTM for DNA sequence processing and Super Token Attention with Bi-LSTM for DNA shape feature extraction. They report that MLSNet outperforms several state-of-the-art methods on 165 ChIP-seq datasets, with average ACC of 0.8306, AUROC of 0.8992, and AUPRC of 0.9035, surpassing the second-best method by 1.82%, 1.68%, and 1.54% respectively.
- **Visible evidence base** Abstract, introduction, methods description, results narrative, tables referenced (Tables 1-4, S1-S11), figures referenced (Figs 1-6, S1-S2), supplementary text referenced (Texts S1-S7)
- **Missing materials affecting confidence** Actual tables and figures not provided; supplementary materials not accessible; no detailed hyperparameter values beyond batch size; no statistical significance testing reported; no ablation study details beyond two variants; no runtime or computational cost comparison

## Reviewer
- **Overall assessment** The manuscript presents a reasonable engineering contribution to TFBS prediction by combining existing architectural components (multisize convolutions, LSTM, attention mechanisms) in a novel configuration. The reported performance improvements over baselines are modest but consistent. However, the manuscript has several weaknesses that limit its current impact: the novelty is incremental relative to existing methods such as DeepSTF, the experimental validation lacks statistical rigor, and several claims are not fully supported by the evidence presented. The writing is generally clear but contains some grammatical errors and unclear passages.
- **Who would be interested in the results, and why** Researchers working on computational prediction of transcription factor binding sites and regulatory genomics. The work may also be of interest to those developing deep learning architectures for biological sequence analysis, particularly regarding the combination of sequence and structural features. The comparative benchmarking on 165 ChIP-seq datasets provides a useful reference point for method development in this area.
- **Major strengths** 1) The manuscript addresses a relevant problem in regulatory genomics with practical implications. 2) The use of a large, standardized benchmark dataset (165 ChIP-seq datasets) enables fair comparison with prior work. 3) The architectural design is clearly described and the code is made publicly available. 4) The authors provide some analysis of performance across cell lines and transcription factors, which adds practical insight. 5) The incremental ablation via MLSNet-1 and MLSNet-2 helps isolate contributions of different components.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The architectural combination is novel but incremental, building directly on existing components and closely following the DeepSTF framework. Scientific importance: The problem is important, but the reported improvements are modest and the biological insights are limited. Interdisciplinary readership: The work is primarily of interest to computational biologists and bioinformaticians; the general biological significance is not strongly articulated. Technical soundness: The methodology is generally sound but lacks statistical validation and some implementation details. Readability for nonspecialists: The manuscript is accessible to those with background in deep learning and genomics, but some sections are dense and contain grammatical issues.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical validation, clarification of the novelty claim relative to DeepSTF, and provision of missing experimental details.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The claim that MLSNet "consistently outperforms several state-of-the-art algorithms" and the specific improvement percentages (1.82%, 1.68%, 1.54%) over the second-best method.
- **Evidence pointer** Results section, Tables 2 and 4, location not provided
- **Concern** The manuscript reports average performance metrics across 165 datasets but provides no statistical significance testing. It is unclear whether the observed improvements over baselines are statistically significant given potential variance across datasets. The claim of "consistent" outperformance is not supported by any measure of variability (e.g., standard deviation, confidence intervals) or paired statistical tests.
- **Why it matters** Without statistical validation, the reported improvements could be within the range of random variation. This is particularly important given the modest effect sizes reported (1-2% improvement). The claim of consistent superiority is a central conclusion of the paper and requires appropriate statistical support.
- **Resolution test** Provide statistical significance testing (e.g., paired Wilcoxon signed-rank test or McNemar's test) comparing MLSNet against each baseline across the 165 datasets, and report effect sizes with confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and positioning
- **Claim pointer** The claim that MLSNet is a "novel deep learning architecture" and the implicit claim that it addresses limitations of prior methods.
- **Evidence pointer** Introduction, Model description, location not provided
- **Concern** The manuscript does not clearly articulate how MLSNet differs from DeepSTF beyond the specific architectural choices. DeepSTF already combines CNN, Bi-LSTM, and transformer components with DNA shape data. The authors state that DeepSTF "overemphasizes shape features while neglecting sequence features," but do not provide evidence for this claim or explain how MLSNet specifically addresses it. The novelty appears to be primarily in the specific arrangement of components (multisize convolution fusion with LSTM for sequence, Super Token Attention with Bi-LSTM for shape) rather than a fundamentally new approach.
- **Why it matters** The contribution of the paper depends on establishing a clear advance over existing methods. Without a precise articulation of the novelty and its advantages, the scientific contribution is difficult to assess. The claim that prior methods neglect sequence features is a strong statement that requires empirical support.
- **Resolution test** Provide a detailed comparison of architectural differences between MLSNet and DeepSTF, and present experimental evidence (e.g., ablation or feature analysis) demonstrating that MLSNet captures sequence features more effectively than DeepSTF.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental completeness
- **Claim pointer** The claim that MLSNet's performance is validated through comprehensive comparison with state-of-the-art methods.
- **Evidence pointer** Results section, Table 4, location not provided
- **Concern** The manuscript mentions comparison with "several state-of-the-art algorithms" but does not specify which methods are included in Table 4 beyond DeepSTF. The selection criteria for baselines and the hyperparameter tuning process for baselines are not described. Additionally, the manuscript does not report whether the same train/validation/test splits were used for all methods, which is critical for fair comparison.
- **Why it matters** Fair and reproducible benchmarking is essential for establishing the validity of the reported improvements. Without details on baseline selection, tuning, and evaluation protocol, the comparison may be biased and the results not reproducible by others.
- **Resolution test** List all baseline methods compared, describe their hyperparameter tuning procedures, confirm identical data splits across methods, and provide the evaluation code or detailed protocol to ensure reproducibility.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical clarity
- **Claim pointer** The description of the MLSNet architecture and its components.
- **Evidence pointer** Model description, Fig. 1, Tables S5-S7, location not provided
- **Concern** The manuscript provides high-level descriptions of the architecture but lacks sufficient detail for reproduction. Key hyperparameters (number of layers, hidden dimensions, learning rate, dropout rate, etc.) are not fully specified. The exact fusion mechanism for combining sequence and shape features is described only vaguely. The role of the "symmetric processing structure" is unclear. The manuscript states that "the exact parameter settings of the model are specified in Table 1," but Table 1 is not provided in the manuscript text.
- **Why it matters** Reproducibility is a fundamental requirement for computational research. Without complete architectural and training details, other researchers cannot implement or build upon the method. The lack of clarity also makes it difficult to assess the soundness of the design choices.
- **Resolution test** Provide complete architectural specifications including all hyperparameters, layer dimensions, fusion mechanism details, and training procedures either in the main text or supplementary materials.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Abstract, Introduction
- **Evidence pointer** Location not provided
- **Issue** The abstract and introduction contain some awkward phrasing and grammatical errors. For example, "To addition to these methods" in the Introduction should be "In addition to these methods." The sentence "This research delineates the effectiveness of combining multi-size convolutional layers with LSTM and DNA shape-based features in enhancing predictive accuracy" is somewhat redundant with the earlier description.
- **Required correction** Revise for clarity and grammatical correctness throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Fig. 1
- **Evidence pointer** Location not provided
- **Issue** The manuscript references Fig. 1 for the architecture but the figure is not provided. Based on the text description, the figure should clearly show the data flow through both the sequence and shape processing branches and their fusion point.
- **Required correction** Ensure Fig. 1 clearly illustrates the complete architecture with all components labeled and the fusion mechanism visible.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Result interpretation
- **Affected element** Results section, Cross cell lines and Cross-transcription factors subsections
- **Evidence pointer** Location not provided
- **Issue** The analysis of performance across cell lines and transcription factors is descriptive rather than analytical. The authors note that certain TFs or cell lines yield high performance across all models but do not investigate why this might be the case or what biological or technical factors contribute to these patterns.
- **Required correction** Add discussion of potential reasons for observed performance patterns, or acknowledge this as a limitation and suggest future investigation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and code availability
- **Evidence pointer** Location not provided
- **Issue** The manuscript states that code is available at a GitHub repository, but the repository is not described in detail. It is unclear whether the code includes all preprocessing steps, model training scripts, and evaluation scripts needed for full reproduction.
- **Required correction** Provide a clear description of the repository contents and ensure all code needed for reproduction is included.

## Risk / unsupported claims
- The claim that MLSNet "consistently outperforms" state-of-the-art methods is not statistically supported.
- The claim that prior methods "overemphasize shape features while neglecting sequence features" is not empirically demonstrated.
- The specific improvement percentages (1.82%, 1.68%, 1.54%) are reported without measures of variance or significance.
- The claim that MLSNet "effectively captures DNA-sparse higher-order sequence features" is not directly validated through feature analysis or interpretability studies.
- The generalizability claim that MLSNet "could also be leveraged for other bioinformatics challenges" is speculative and not supported by experiments.
- The performance comparison across cell lines and transcription factors is descriptive and lacks statistical or biological interpretation.