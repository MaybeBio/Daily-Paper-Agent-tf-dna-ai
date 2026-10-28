## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, supplementary notes, and availability statements
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and presentation as presented in the supplied material
- **Shared manuscript claim summary** The authors benchmark six active learning selection strategies for sequence-to-expression models across two large-scale datasets and three model architectures, finding that uncertainty-based strategies outperform random sampling and diversity-based strategies, that a single large acquisition round captures most of the benefit of multiple smaller rounds, and that selected sequences share biological features such as high expression, specific dinucleotide composition, and TFBS density, yet no single biological feature fully explains the advantage of active learning.
- **Visible evidence base** Main figures 1 through 6 (referenced but not shown), supplementary figures 1 through 15 (referenced but not shown), supplementary notes, methods section, and abstract
- **Missing materials affecting confidence** All figures and tables are referenced but not provided; no numerical results, error bars, statistical test details, or model performance metrics are visible; the code repository and data availability links are provided but not assessed

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in regulatory genomics: how to select training data for sequence-to-expression models in a lab-in-the-loop setting. The study design is comprehensive, covering multiple strategies, architectures, datasets, and evaluation tasks. The finding that uncertainty-based methods consistently outperform random sampling and diversity-based methods is plausible and practically useful. The biological characterization of selected sequences is a valuable contribution. However, the absence of all figures and numerical results in the supplied material prevents verification of the central claims. The manuscript would benefit from clearer presentation of effect sizes, statistical significance, and the practical magnitude of performance gains. The claim that active learning is "critical" for improving sequence-to-expression models is somewhat strong given the modest absolute improvements reported in the text (e.g., r² increases of ~1.5-6%). The discussion of limitations is thoughtful, but the generalizability of the findings to other datasets and model architectures remains uncertain.
- **Who would be interested in the results, and why** Researchers developing sequence-to-expression models, particularly those using MPRA data, will find the benchmarking results directly relevant to experimental design. The finding that a single large acquisition round suffices is practically important for wet-lab scientists planning iterative experiments. The biological characterization of informative sequences will interest regulatory genomics researchers studying promoter architecture and TF binding. The nextFrag framework provides a useful tool for the community. The study may also appeal to machine learning researchers working on active learning for regression tasks in biology.
- **Major strengths** The study addresses a question of clear practical importance with a rigorous benchmarking design. The use of two large-scale datasets from different species and sequence types (genomic vs. random) strengthens the generalizability of the findings. The evaluation across three test types (ID, VEP, OOD) is thorough. The biological characterization of selected sequences goes beyond simple performance metrics and provides mechanistic insight. The comparison of iterative versus single-round acquisition is practically relevant. The authors are appropriately cautious in their interpretation of strategy-specific differences.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The absence of all figures and numerical results in the supplied material means that the central claims cannot be verified. The manuscript text alone does not provide sufficient quantitative detail to assess the magnitude of the reported effects.
- **Assessment against Nature-style criteria** Originality: The study is original in its comprehensive benchmarking of active learning strategies specifically for sequence-to-expression models with real experimental data. Scientific importance: The question of data-efficient training for regulatory genomics models is important, and the findings have direct practical implications. Interdisciplinary readership: The work bridges machine learning and regulatory genomics, and the practical recommendations are accessible to both communities. Technical soundness: The experimental design is sound in principle, but the absence of figures and numerical results prevents full assessment. Readability for nonspecialists: The manuscript is generally well-written and the practical recommendations are clearly stated, though some sections assume familiarity with active learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved and the full evidence base is made available for verification.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that "All strategies outperformed random sampling, with uncertainty-based methods performing best" and that "Active learning delivered major performance gains" across ID, VEP, and OOD test sets.
- **Evidence pointer** Figures 2A-H, Supplementary Figures 1-2, location not provided
- **Concern** All figures and tables are referenced but not included in the supplied material. The central quantitative claims of the manuscript cannot be verified without seeing the actual performance metrics, error bars, and statistical comparisons. The text reports r² increases of ~1.5% for ID and ~3-6% for OOD/VEP, but the significance and consistency of these effects across replicates and conditions cannot be assessed.
- **Why it matters** The core contribution of this manuscript is empirical: it benchmarks active learning strategies and reports their relative performance. Without the actual data, the claims are unverifiable. The magnitude of the reported improvements is also important for assessing practical significance, as a 1.5% r² increase may or may not justify the added complexity of active learning workflows.
- **Resolution test** Provide all main and supplementary figures with clear axis labels, error bars, and statistical annotations. Include exact numerical values for performance metrics in the text or tables, with confidence intervals or significance tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that "Different strategies selected substantially overlapping sets of sequences" and that "active learning consistently outperformed selection based on these biological properties alone."
- **Evidence pointer** Figures 4A-F, 6A-F, Supplementary Figures 6-7, location not provided
- **Concern** The overlap analyses and comparisons to biological feature-based selection are described qualitatively in the text, but no statistical framework is described for assessing whether observed overlaps exceed chance expectations or whether performance differences between active learning and biological feature-based selection are significant. The expected overlap calculations are mentioned for the human dataset (30.9%) and yeast dataset (1%), but the statistical uncertainty around these estimates and the observed overlaps is not discussed.
- **Why it matters** The claim that active learning captures something beyond individual biological features is central to the paper's contribution. If the performance differences between active learning and biological feature-based selection are not statistically robust, the conclusion that "informativeness is not fully captured by any single feature" would be weakened.
- **Resolution test** Provide statistical tests for overlap significance (e.g., permutation tests or hypergeometric tests) and for performance comparisons between active learning and biological feature-based selection (e.g., paired tests across replicates). Report effect sizes with confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The manuscript claims that "active learning as a critical tool for improving sequence-to-expression models" and provides "practical guidelines for implementing active learning in sequence-to-expression modeling."
- **Evidence pointer** Discussion section, location not provided
- **Concern** The study is limited to two datasets (human genomic and yeast random) and three model architectures. The authors acknowledge this limitation, but the strength of the recommendation ("critical tool") seems disproportionate to the evidence base. The finding that a single large round performs similarly to multiple smaller rounds is based on only one comparison (3x20k vs 1x60k), and it is unclear how this generalizes to other dataset sizes, model types, or acquisition budgets.
- **Why it matters** The practical recommendations are likely to be adopted by researchers designing lab-in-the-loop experiments. If the recommendations are based on a narrow evidence base, they may not generalize to other settings, potentially leading to suboptimal experimental designs.
- **Resolution test** Either temper the strength of the recommendations to match the evidence base, or provide additional analyses demonstrating robustness across a wider range of conditions (e.g., different dataset sizes, acquisition budgets, model architectures).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The manuscript claims that "active learning consistently outperformed selection based on these biological properties alone, indicating that informativeness is not fully captured by any single feature."
- **Evidence pointer** Figures 5A-H, 6C-F, Supplementary Figures 9-12, location not provided
- **Concern** The biological characterization of selected sequences is interesting, but the causal interpretation is unclear. The authors show that active learning selects sequences with high expression, specific dinucleotide composition, and TFBS density, but they do not demonstrate that these features are causally related to informativeness for model improvement. The correlation between these features and active learning selection could be confounded by other sequence properties.
- **Why it matters** The claim that informativeness is not captured by any single biological feature is important, but the evidence presented is correlational. Without causal evidence or at least a more rigorous analysis of confounding factors, the interpretation may be overreaching.
- **Resolution test** Provide analyses that control for potential confounders (e.g., sequence similarity to training data, GC content, etc.) or conduct intervention experiments where sequences are selected based on specific biological features and their informativeness is directly measured.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that "All strategies outperformed random sampling" but does not specify the magnitude of the improvement or whether this was consistent across all datasets and test sets.
- **Required correction** Add a brief quantitative summary of the performance gains (e.g., "improving r² by X% on average across test sets") to give readers a sense of the practical significance.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Description of Sequence Selection Strategies"
- **Evidence pointer** Methods section, location not provided
- **Issue** The description of the "all arch" ensemble states that it contains "3 models total with one of each architecture," but the earlier text mentions "three types of ensembles differing in composition and size." It is unclear whether the "all arch" ensemble uses one model per architecture or multiple replicates per architecture.
- **Required correction** Clarify the exact composition of each ensemble type, including the number of models per architecture and whether replicates are used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, "AL benchmarking workflow"
- **Evidence pointer** Results section, location not provided
- **Issue** The text reports that "the difference in median r² values between configurations in both datasets was, in most cases, less than 0.004" but does not provide confidence intervals or variability measures for these medians.
- **Required correction** Report the distribution of r² values across replicates (e.g., interquartile range or standard deviation) to allow readers to assess the uncertainty in the median differences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results, "AL is more reliable than biologically-driven acquisition functions"
- **Evidence pointer** Results section, location not provided
- **Issue** The term "reliable" is used to describe the performance of active learning compared to biologically-driven approaches, but it is not defined. It could mean consistency across replicates, magnitude of improvement, or something else.
- **Required correction** Define what is meant by "reliable" in this context, or use a more precise term such as "consistently superior" or "more robust."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section, location not provided
- **Issue** The discussion mentions that "future work should incorporate diverse sequence generation approaches" but does not discuss potential challenges or limitations of such approaches in the context of active learning.
- **Required correction** Add a brief discussion of the challenges associated with generative sequence design in active learning loops, such as mode collapse, evaluation of generated sequences, or the risk of selecting sequences that are too far from the training distribution.

## Risk / unsupported claims
- The claim that "active learning is a critical tool for improving sequence-to-expression models" is not fully supported by the evidence presented, as the reported improvements are modest (~1.5-6% r²) and the study is limited to two datasets and three architectures.
- The claim that "informativeness is not fully captured by any single feature" is based on correlational evidence and may be confounded by other sequence properties.
- The claim that "most of the benefit of active learning can be captured in a single large selection round" is based on a single comparison (3x20k vs 1x60k) and may not generalize to other settings.
- The biological characterization of selected sequences (enrichment for high expression, TFBS density, specific dinucleotide composition) is descriptive and does not establish causality.
- The performance of the "combined" strategy (often-uncertain + often-diverse) is described as sometimes matching but rarely exceeding the best individual strategy, but the conditions under which this occurs are not specified.
- The generalizability of the findings to other model architectures, dataset sizes, and sequence types is not established.