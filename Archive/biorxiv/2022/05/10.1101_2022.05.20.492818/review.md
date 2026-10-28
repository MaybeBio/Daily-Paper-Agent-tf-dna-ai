## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no figures, tables, methods, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce ExplaiNN, a neural additive model adaptation for genomics, where predictions are a linear combination of independent CNNs each with a single convolutional filter and fully connected layers. They claim performance comparable to state-of-the-art methods for transcription factor binding and chromatin accessibility prediction, equivalent motif discovery to specialized algorithms, and a plug-and-play platform integrating pretrained models and annotated position weight matrices.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, dataset descriptions, or methodological specifications
- **Missing materials affecting confidence** Full manuscript, figures, tables, methods section, supplementary information, code availability, and benchmark definitions

## Reviewer
- **Overall assessment** The abstract presents a conceptually appealing approach that combines CNN expressiveness with linear model interpretability for genomic sequence analysis. The core idea of using neural additive models with single-filter CNNs is timely and potentially useful. However, the abstract provides no quantitative evidence, no benchmark specifications, and no methodological details sufficient to evaluate the validity of the performance and equivalence claims. The claims are plausible but currently unverifiable from the supplied material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or applying deep learning models for regulatory genomics, particularly those focused on transcription factor binding prediction, chromatin accessibility analysis, and de novo motif discovery. The interpretability focus would also appeal to experimental biologists seeking transparent models for sequence analysis.
- **Major strengths** The conceptual framing is clear and addresses a recognized limitation in genomic deep learning. The proposed architecture is simple and potentially scalable. The claim of providing both global and local interpretability is attractive. The stated goal of a plug-and-play platform with pretrained models and reference PWMs is practical and could lower adoption barriers.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is moderate; neural additive models are established in other domains, and their adaptation to genomics is a reasonable but not transformative step. Scientific importance is potentially high if the interpretability claims hold, but this is not demonstrated. Interdisciplinary readership is plausible given the relevance to both computational and experimental genomics. Technical soundness cannot be assessed from the abstract alone. Readability for nonspecialists is good, with clear language and minimal jargon, though the abstract assumes familiarity with deep learning concepts.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but lacks the quantitative and methodological detail required to support the core claims. A full manuscript with benchmarks, comparisons, and implementation details would be necessary for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Performance claim
- **Claim pointer** The authors claim "performance levels comparable to state-of-the-art methods" for TF binding and chromatin accessibility prediction.
- **Evidence pointer** Abstract only; no figures or tables provided
- **Concern** The abstract provides no quantitative metrics, no comparison baselines, no dataset descriptions, and no statistical tests to support the performance equivalence claim. Without specific AUC, AUPRC, or correlation values and their variances, the claim is unsubstantiated.
- **Why it matters** The central value proposition of ExplaiNN depends on not sacrificing predictive accuracy for interpretability. If performance is not rigorously demonstrated to be comparable to established methods, the practical utility of the tool is questionable.
- **Resolution test** Provide benchmark results on standard datasets (e.g., ENCODE, Roadmap Epigenomics) with clear baselines, error bars, and statistical significance tests. Show that performance differences are within acceptable thresholds.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Motif discovery equivalence claim
- **Claim pointer** The authors claim ExplaiNN "identifies equivalent motifs to those obtained from specialized algorithms across a range of datasets."
- **Evidence pointer** Abstract only; no motif comparison results provided
- **Concern** The term "equivalent" is undefined. No criteria for motif similarity (e.g., Tomtom q-values, Pearson correlation on position frequency matrices) are given. No datasets or comparison algorithms are specified. The claim of equivalence across "a range of datasets" is too broad without supporting evidence.
- **Why it matters** Motif discovery is a key application area, and the claim of equivalence to specialized tools is a strong statement. If the equivalence criteria are lax or the datasets are narrow, the claim could be misleading.
- **Resolution test** Define quantitative motif similarity metrics, specify comparison tools (e.g., MEME, HOMER), and report results across multiple diverse datasets with clear thresholds for equivalence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability claim
- **Claim pointer** The authors claim ExplaiNN provides "global (cell state level) as well as local (individual sequence level) biological insights."
- **Evidence pointer** Abstract only; no interpretability analysis or examples provided
- **Concern** The abstract does not explain how global and local insights are derived from the model architecture, nor does it provide any example biological findings. The claim that the architecture inherently provides interpretability is plausible but not demonstrated.
- **Why it matters** Interpretability is the primary motivation for the work. Without concrete examples of biological insights that are novel or actionable, the added value over existing interpretation methods (e.g., saliency maps, DeepLIFT) is unclear.
- **Resolution test** Provide case studies showing specific TFs or regulatory elements identified by ExplaiNN, with validation against known biology or experimental data. Compare interpretability outputs with existing methods to show added value.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of architecture description
- **Affected element** Model description
- **Evidence pointer** Abstract, first paragraph
- **Issue** The description "each consisting of a single convolutional filter and fully connected layers" is ambiguous regarding the depth and width of the fully connected layers and how the linear combination is implemented.
- **Required correction** Provide a clear architectural diagram or pseudocode in the full manuscript, and specify the number of independent CNNs used in practice.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Platform claim
- **Evidence pointer** Abstract, final paragraph
- **Issue** The "plug-and-play platform" claim implies software availability, but no repository, documentation, or installation instructions are mentioned.
- **Required correction** State the software availability (e.g., GitHub link, package manager) and provide usage examples in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope of evaluation
- **Affected element** Benchmark breadth
- **Evidence pointer** Abstract, second paragraph
- **Issue** The abstract mentions TF binding and chromatin accessibility as the two tasks, but does not specify the number of cell types, TFs, or datasets used.
- **Required correction** List the datasets, cell types, and TFs in the full manuscript, and justify the choice of these benchmarks as representative.

## Risk / unsupported claims
- Performance comparable to state-of-the-art methods (no quantitative evidence)
- Equivalent motif discovery to specialized algorithms (no defined criteria or results)
- Global and local biological insights provided (no examples or methodology)
- Plug-and-play platform functionality (no software or documentation evidence)
- Generalizability across "a range of datasets" (no dataset list or diversity analysis)