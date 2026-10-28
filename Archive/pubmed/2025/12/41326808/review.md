## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present PDIScore, a deep learning scoring function for protein-DNA interactions, built on a graph representation with GraphGPS architecture and Mixture Density Networks. They report training on ~7000 complex structures and validation on three test sets, claiming superior performance in screening, docking, and ranking tasks, with case studies supporting biological interpretability.
- **Visible evidence base** Abstract text only; no numerical tables, figures, or methodological details beyond those summarized
- **Missing materials affecting confidence** Full manuscript, dataset composition and curation details, model architecture specifics, hyperparameters, training/validation split procedures, baseline method descriptions, statistical significance tests, case study details, and code or data availability statements

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable contribution to the field of protein-DNA interaction scoring, addressing a real gap in structure-based scoring functions. The methodological combination of graph neural networks with attention mechanisms and mixture density networks is reasonable and contemporary. However, the abstract alone provides insufficient detail to assess the rigor of the training data, the validity of the evaluation protocol, or the robustness of the reported performance gains. Several claims, particularly regarding generalizability and interpretability, are not substantiated at the level of evidence provided.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein-nucleic acid interactions, drug discovery researchers interested in transcription factor targeting, and developers of scoring functions for molecular docking. The work may also appeal to methodologists in geometric deep learning applied to biomolecular systems.
- **Major strengths** The problem is well-motivated, addressing a genuine limitation in PDI scoring. The use of nucleotide flexibility in the graph representation is a thoughtful design choice. The architecture is scalable and modern, and the evaluation across three distinct tasks (screening, docking, ranking) is commendable. The reported performance metrics, if reproducible, would represent a meaningful advance.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1 (dataset curation and leakage), R1-M2 (evaluation protocol and comparability), R1-M3 (statistical robustness)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The combination of existing components (GraphGPS, BigBird, MDN) is novel in this application domain, but the abstract does not clearly articulate what is fundamentally new beyond the specific integration.
  - Scientific importance: Potentially high, given the importance of PDI scoring in drug design and gene regulation. However, the abstract does not demonstrate that the improvements are biologically meaningful beyond metric gains.
  - Interdisciplinary readership: The work bridges machine learning and molecular biology, which could attract a broad audience. The abstract is written accessibly, though some technical terms may require background.
  - Technical soundness: Cannot be fully assessed from the abstract. The evaluation design raises questions about data leakage and baseline comparability that must be resolved.
  - Readability for nonspecialists: The abstract is clear and well-structured, with appropriate context and explanation of key concepts. The case study mention helps ground the work in biological relevance.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the current evidence base is insufficient to establish the claims of superiority and generalizability.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data integrity and leakage
- **Claim pointer** "PDIScore was trained on a self-collected dataset of ~7000 protein-nucleic acid complex structures and validated on three rigorous test sets"
- **Evidence pointer** Abstract, dataset description; location not provided
- **Concern** The abstract does not describe how the training set was curated, how redundancy was controlled, or whether the test sets share sequence or structural similarity with the training set. Without this information, the reported performance could be inflated by data leakage, particularly given the use of AlphaFold3 structures in the screening set, which may have been derived from templates overlapping with the training data.
- **Why it matters** Data leakage is a well-documented pitfall in machine learning for structural biology. If the test sets are not sufficiently disjoint from the training set, the reported metrics (EF(1%) = 14.13, AUROC = 0.82) may not reflect true generalization to novel protein-DNA complexes.
- **Resolution test** Provide a detailed description of dataset construction, including sequence and structural similarity thresholds between training and test sets. Demonstrate that no test complex shares significant homology with any training complex, and report performance on a truly independent benchmark.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evaluation protocol and comparability
- **Claim pointer** "PDIScore significantly outperformed existing methods: it achieved the best screening power on the screening set (e.g., EF(1%) = 14.13, AUROC = 0.82 using AlphaFold3 structures), the highest docking success rate on the docking set (48.94% top1), and superior ranking capability on the ranking set (PCC = 0.50)"
- **Evidence pointer** Abstract, results summary; location not provided
- **Concern** The abstract does not specify which existing methods were compared, how their parameters were optimized, or whether the same input structures and decoy sets were used across all methods. The use of AlphaFold3 structures for the screening set is particularly concerning, as this may introduce a bias if the baseline methods were not given the same structures or if AlphaFold3 predictions are not representative of the docking scenario.
- **Why it matters** Fair benchmarking is essential for establishing superiority. If baselines were not given equivalent inputs or were not tuned appropriately, the reported improvements may be artifacts of the evaluation setup rather than genuine advances in scoring accuracy.
- **Resolution test** Provide a full description of the benchmark protocol, including the list of baseline methods, their input structures, parameter settings, and any preprocessing steps. Show that all methods were evaluated under identical conditions, and consider reporting results on both experimental and predicted structures for all methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness
- **Claim pointer** "PDIScore significantly outperformed existing methods"
- **Evidence pointer** Abstract, results summary; location not provided
- **Concern** The abstract reports single-point metrics (e.g., EF(1%) = 14.13, AUROC = 0.82, 48.94% top1, PCC = 0.50) without any indication of variance, confidence intervals, or statistical significance testing. The word "significantly" is used without supporting statistical evidence.
- **Why it matters** Performance metrics in structure prediction and scoring are known to be sensitive to dataset composition and random initialization. Without measures of variance or significance testing, it is impossible to determine whether the reported improvements are robust or within the noise of the evaluation.
- **Resolution test** Report performance across multiple random seeds or cross-validation folds, provide confidence intervals or standard deviations for all key metrics, and perform appropriate statistical tests (e.g., paired tests) comparing PDIScore to each baseline.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and biological relevance
- **Claim pointer** "Case studies demonstrated PDIScore's ability to elucidate biological mechanisms (e.g., adenovirus transcription, SOCS1 regulation) and its interpretability at the nucleotide level for identifying key interaction sites"
- **Evidence pointer** Abstract, case study description; location not provided
- **Concern** The abstract claims biological interpretability and mechanistic insight, but provides no details on how interpretability was assessed, whether the identified sites were experimentally validated, or how the case studies were selected. The link between model predictions and biological conclusions is not established.
- **Why it matters** Interpretability claims are increasingly scrutinized in the machine learning community. Without a clear methodology for extracting and validating nucleotide-level importance, these claims risk being overstated and may not withstand independent evaluation.
- **Resolution test** Provide a detailed description of the interpretability method (e.g., attention weights, gradient-based attribution), show quantitative or qualitative validation of identified sites against known experimental data, and clarify whether the case studies were pre-registered or selected post hoc.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methodology
- **Affected element** Model architecture description
- **Evidence pointer** Abstract, methods summary; location not provided
- **Issue** The abstract states that PDIScore "utilizes a comprehensive graph representation to capture nucleotide flexibility" but does not explain how flexibility is encoded in the graph features. This is a key design choice that distinguishes the method from prior work.
- **Required correction** Clarify in the abstract or methods how flexibility is represented (e.g., B-factors, ensemble conformations, or predicted dynamics) and why this representation is expected to improve scoring.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Dataset description
- **Affected element** Training data composition
- **Evidence pointer** Abstract, dataset description; location not provided
- **Issue** The abstract mentions "~7000 protein-nucleic acid complex structures" but does not specify the source databases, the resolution cutoff, or the balance between protein-DNA and protein-RNA complexes. This limits the reader's ability to assess the generalizability of the model.
- **Required correction** Provide a breakdown of the dataset by complex type, source, and resolution, and state any filtering criteria used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Metric interpretation
- **Affected element** Screening performance
- **Evidence pointer** Abstract, results summary; location not provided
- **Issue** The abstract reports EF(1%) = 14.13 and AUROC = 0.82 for the screening set using AlphaFold3 structures. It is unclear whether these metrics are computed on the same decoy set and whether the enrichment factor is normalized for the fraction of true positives in the set.
- **Required correction** Define the screening task precisely, including the composition of the decoy set and the calculation of EF(1%), and report the baseline random expectation for context.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Availability and reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not mention whether the model, training data, or evaluation scripts will be made publicly available. Reproducibility is a core expectation for computational methods.
- **Required correction** State a clear availability statement for code, data, and trained model weights, ideally with a permanent repository link.

## Risk / unsupported claims
- The claim of "significantly outperformed" is unsupported without statistical testing or variance reporting.
- The claim of "robust, generalizable tool" is unsupported given the lack of detail on dataset diversity and external validation.
- The claim of "interpretability at the nucleotide level for identifying key interaction sites" is unsupported without a described methodology or experimental validation.
- The specific performance numbers (EF(1%) = 14.13, AUROC = 0.82, 48.94% top1, PCC = 0.50) are not independently verifiable from the abstract alone and should be treated as preliminary until full methods are reviewed.
- The use of AlphaFold3 structures in the screening set raises concerns about comparability with experimental structures, which is not addressed in the abstract.