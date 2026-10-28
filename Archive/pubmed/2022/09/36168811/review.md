## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose dynDeepDRIM, a deep learning model that reconstructs gene regulatory networks (GRNs) from time-course single-cell RNA sequencing (scRNA-seq) data by representing joint expression of gene pairs as images and incorporating neighborhood context to remove transitive interactions. They report superior performance over six existing GRN reconstruction methods on simulation and four real time-course scRNA-seq datasets, and improved gene function annotation performance.
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or dataset descriptions are available
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, simulation details, real dataset descriptions, baseline method configurations, hyperparameter settings, and evaluation metrics

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting application of deep learning to a challenging problem in regulatory genomics. The core idea of encoding gene pair joint expression as images and using neighborhood context to filter transitive interactions is conceptually reasonable. However, the abstract alone provides insufficient evidence to evaluate the technical soundness, the validity of the performance claims, or the generalizability of the approach. Several claims are made without quantitative support, and the lack of methodological detail prevents independent assessment. The work may be of interest to computational biologists working on GRN inference, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians focused on gene regulatory network inference, single-cell transcriptomics analysis, and deep learning applications in genomics. The potential to improve direct interaction detection over existing tools would be relevant to researchers studying cell-type-specific regulatory programs and dynamic gene regulation.
- **Major strengths** The problem addressed is timely and important, as time-course scRNA-seq data are increasingly available but underutilized for GRN inference. The proposed approach of using image representations of gene pair expression and incorporating neighborhood context is a creative departure from standard vector-based or graph-based methods. The claim of effective removal of transitive interactions addresses a known limitation in GRN inference.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The model "represents the joint expression of a gene pair as an image and utilizes the image of the target TF-gene pair and the ones of the potential neighbors to reconstruct GRNs" and "model the gene expression dynamics using high-dimensional tensors."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract provides no details on how the image representation is constructed, how neighborhood context is defined and incorporated, or how high-dimensional tensors are used. Without this information, the architectural choices and their rationale cannot be evaluated. It is unclear whether the image representation preserves temporal ordering, how missing data or dropout events in scRNA-seq are handled, and how the model scales to genome-wide applications.
  - **Why it matters** The core novelty of the method rests on these design choices. If the image representation or tensor modeling is flawed or ad hoc, the claimed performance advantages may not be reproducible or generalizable. Reviewers and readers cannot assess whether the method is technically sound or whether it would work on other datasets.
  - **Resolution test** Provide a detailed description of the model architecture, including input encoding, layer types, and how neighborhood information is integrated. Include a schematic diagram and pseudocode. Demonstrate the method on a small example with clear visualization of the image representation and tensor operations.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** "dynDeepDRIM achieved substantially better performance than the other methods in inferring TF-gene interactions and eliminated the false positives effectively."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** No quantitative results are reported. The abstract does not state which metrics were used (e.g., AUROC, AUPRC, precision, recall), the magnitude of improvement, or the statistical significance of the differences. The phrase "substantially better" is subjective and unsupported. Additionally, the choice of six baseline methods and their configurations is not described, which is critical for fair comparison.
  - **Why it matters** Performance claims are the primary basis for the paper's contribution. Without numbers, confidence intervals, or statistical tests, the claims cannot be verified. The absence of baseline details raises concerns about potential bias in method comparison.
  - **Resolution test** Report AUROC and AUPRC values for all methods on all datasets, with standard deviations or confidence intervals. Include statistical significance tests (e.g., Wilcoxon signed-rank test) comparing dynDeepDRIM to each baseline. Describe baseline implementations and parameter tuning procedures.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The method was evaluated on "simulation and four real time-course scRNA-seq data."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not identify the simulation framework, the real datasets used, or the preprocessing steps. It is unclear whether the real datasets include ground truth regulatory interactions, which is essential for evaluating GRN inference performance. The simulation setup is not described, so the realism and difficulty of the simulated data cannot be assessed.
  - **Why it matters** Reproducibility is a core requirement for computational biology papers. Without dataset identifiers, preprocessing details, and ground truth definitions, other researchers cannot replicate the experiments or apply the method to their own data. The validity of the evaluation depends on the quality and appropriateness of the benchmarks.
  - **Resolution test** List the names and accessions of all real datasets, describe the simulation procedure (e.g., using a known GRN simulator), and specify how ground truth interactions were defined. Provide code and data availability statements.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Claim scope
  - **Claim pointer** "We also applied dynDeepDRIM to annotate gene functions and found it achieved evidently better performance than the other tools due to considering the neighbor genes."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The gene function annotation application is mentioned as a secondary result, but no details are given on how annotation was performed, what benchmark was used, or what metrics were reported. The causal attribution to "considering the neighbor genes" is speculative without controlled experiments.
  - **Why it matters** This claim extends the utility of the method beyond GRN inference, but the evidence is too thin to support it. If the annotation performance is a key selling point, it needs proper evaluation. If it is peripheral, the claim should be softened or removed.
  - **Resolution test** Describe the annotation task, the benchmark dataset, and the evaluation metrics. Include an ablation study that removes the neighborhood context to demonstrate its specific contribution to annotation performance.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The term "direct regulatory interactions" is used in the title and abstract, but the distinction between "direct" and "indirect" is not defined. The claim of removing "transitive TF-gene interactions" suggests a specific definition, but it is not stated.
  - **Required correction** Define what constitutes a direct interaction in the context of this work, and clarify how transitive interactions are identified and removed.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Baseline methods
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The six comparison methods are not named. This makes it difficult to contextualize the performance claims relative to known strengths and weaknesses of existing tools.
  - **Required correction** List the names and versions of all baseline methods in the abstract or introduce them in the main text with appropriate citations.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Abstract structure
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract is dense and mixes motivation, method description, and results in a way that may be hard for nonspecialists to follow. The phrase "high-dimensional tensors" is used without explanation.
  - **Required correction** Consider restructuring the abstract to separate motivation, method, and results more clearly. Briefly explain what tensors are in this context or use more accessible language.
- **Technical failings that need to be addressed before the case is established** R1-M1 (model architecture not described), R1-M2 (no quantitative results), R1-M3 (datasets and simulation not described). These are blocking because the core claims of the paper cannot be evaluated without them.
- **Assessment against Nature-style criteria**  
  Originality: The idea of using image representations of gene pair expression and neighborhood context is somewhat novel, but the abstract does not clearly differentiate it from existing deep learning approaches for GRN inference. The originality is plausible but not fully demonstrated.  
  Scientific importance: The problem of inferring direct regulatory interactions from time-course scRNA-seq data is important, and improvements over existing methods would be valuable. However, the importance of the specific contribution is not quantified.  
  Interdisciplinary readership: The work sits at the intersection of machine learning and genomics, which has broad appeal. The abstract is accessible to computational biologists but may be challenging for experimental biologists due to the lack of context.  
  Technical soundness: Cannot be assessed from the abstract. The lack of architectural details and evaluation methodology is a major gap.  
  Readability for nonspecialists: The abstract is moderately readable but uses jargon without definition. The structure could be improved.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising idea, but the absence of methodological detail, quantitative results, and dataset descriptions prevents any meaningful assessment of the claims. The authors should be encouraged to provide the full manuscript and supporting materials for a complete review.

## Risk / unsupported claims
- The claim of "substantially better performance" is unsupported because no numerical results are provided.
- The claim of "effectively removed transitive interactions" is unsupported without an ablation study or comparison to methods that do not use neighborhood context.
- The claim of "evidently better performance" in gene function annotation is unsupported without details on the benchmark and metrics.
- The generalizability of the method to other time-course scRNA-seq datasets is not assessable from the abstract alone.