## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) without figures, tables, or supplementary material
- **Assessment boundary** Scientific validity of claims, methodological soundness, evidence quality, and alignment with stated conclusions; no assessment of code functionality or reproducibility beyond what is described
- **Shared manuscript claim summary** The authors evaluate how different negative sampling techniques for training TFBS prediction models affect performance, using high-quality test datasets derived from matched ChIP-seq and ATAC-seq data. They report that genomic sampling performs best on high-quality test sets, dinucleotide shuffling produces overoptimistic estimates and poor real-world performance, and a simple PWM-based approach outperforms several deep learning models trained with certain negative sampling strategies.
- **Visible evidence base** Text descriptions of methods and results, including reported average AUROC values, counts of best-performing cases across cross-validation combinations, and qualitative descriptions of figures (Fig. 1a–d, Fig. 2, Fig. 3, Fig. 4, Fig. 5, Tables 1–7)
- **Missing materials affecting confidence** All figures, tables, and supplementary material are referenced but not provided; exact per-TF results, confidence intervals, statistical tests, and detailed dataset statistics are unavailable; code repository is mentioned but not reviewed

## Reviewer
- **Overall assessment** The manuscript addresses an important and underappreciated problem in TFBS prediction: the choice of negative samples can substantially influence model performance and interpretation. The use of ATAC-seq data to construct high-quality test sets is a valuable contribution. However, the evidence as presented is incomplete. Key figures and tables are not available for inspection, statistical significance of reported differences is not established, and several claims go beyond what the described analyses can support. The core finding that genomic sampling outperforms other methods on high-quality test sets is plausible but not fully verifiable from the supplied material.
- **Who would be interested in the results, and why** Researchers developing or applying deep learning models for TFBS prediction, computational biologists working on regulatory genomics, and method developers in bioinformatics who need guidance on training data construction. The results are also relevant to the broader community studying the impact of negative sampling in genomic machine learning.
- **Major strengths** The problem is well-motivated and practically important. The use of ATAC-seq data to define true negatives is a thoughtful and rigorous approach. The comparison across multiple negative sampling techniques is comprehensive. The inclusion of a PWM baseline provides a useful reference point. The finding that dinucleotide shuffling, a common practice, leads to poor real-world performance is potentially impactful.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing statistical evidence), R1-M2 (incomplete evidence base), R1-M3 (overinterpretation of cross-TF results), R1-M4 (unclear dataset construction details)
- **Assessment against Nature-style criteria** Originality: moderate to high. The problem is not new, but the systematic comparison using ATAC-seq-derived negatives is a useful contribution. Scientific importance: moderate. The findings could influence practice in the field, but the impact is incremental rather than transformative. Interdisciplinary readership: limited. The work is primarily of interest to computational biologists and bioinformaticians. Technical soundness: not fully assessable from the supplied material. The methods are described at a high level, but key details and results are missing. Readability for nonspecialists: acceptable. The writing is clear, but the manuscript assumes familiarity with TFBS prediction and deep learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is sound and the findings are potentially useful, but the evidence base must be completed and statistical rigor added before the claims can be accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that genomic sampling performs best on high-quality test sets, with average HQ AUROC around 86%, and that dinucleotide shuffling produces poor real-world performance with average HQ AUROC around 76%.
- **Evidence pointer** Section 3.2, Fig. 1a, location not provided
- **Concern** The reported differences in average AUROC values are presented without any measure of variability or statistical testing. It is unclear whether the observed differences between methods are significant given the spread across TFs and cross-validation splits. The claim that genomic sampling is "by far the best" requires formal comparison, such as paired tests across TFs or confidence intervals.
- **Why it matters** Without statistical evidence, the central conclusion of the paper cannot be distinguished from noise. The field needs reliable guidance on method selection, and unsupported claims could mislead practitioners.
- **Resolution test** Provide per-TF AUROC values or distributions, and perform appropriate statistical tests (e.g., Wilcoxon signed-rank test across TFs) comparing genomic sampling to each other method. Report effect sizes and confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript makes multiple claims about performance differences across methods, per-TF behavior, and cross-cell-line generalization.
- **Evidence pointer** Figures 1–5 and Tables 1–7, all referenced as supplementary or main figures but not provided in the supplied material
- **Concern** All quantitative results are described only in text. The figures and tables that would allow verification of the claims are not available. This includes the main results figure (Fig. 1), the detailed per-TF comparisons, the PWM comparison, the dataset size analysis, and the cross-cell-line results. Without these, the evidence base is incomplete and the claims cannot be independently assessed.
- **Why it matters** Peer review requires access to the actual data and visualizations to evaluate whether the conclusions follow from the results. The current submission does not permit this.
- **Resolution test** Provide all figures and tables in the manuscript or as accessible supplementary material. Ensure that each claim in the text is traceable to a specific figure or table.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors state that models trained on genome-sampled datasets show good cross-TF performance, which "might indicate that there is some commonality in the binding patterns of the TFs that the model is able to capture."
- **Evidence pointer** Section 3.6, Fig. 4, location not provided
- **Concern** The interpretation of cross-TF performance is speculative. Good cross-TF performance could also arise from learning generic sequence features unrelated to TF binding, such as GC content or chromatin state. The authors do not provide evidence that the model is capturing genuine binding commonalities rather than confounding factors.
- **Why it matters** The claim has implications for how the field should think about multi-label models and shared binding mechanisms. Overinterpretation could lead to incorrect conclusions about model behavior.
- **Resolution test** Provide additional analyses, such as motif enrichment in model predictions or ablation studies, to support the claim that cross-TF performance reflects shared binding patterns.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological detail
- **Claim pointer** The authors describe the construction of high-quality datasets using ATAC-seq data, defining negatives as positions that are accessible but not bound by the TF.
- **Evidence pointer** Section 2.1, location not provided
- **Concern** The description of how ATAC-seq peaks are selected and how negatives are defined is incomplete. It is unclear how the authors distinguish between "accessible but not bound" and "accessible but binding not detected due to technical limitations." The threshold for calling a position "not bound" is not specified. Additionally, the overlap between ChIP-seq positives and ATAC-seq regions is reported but the implications of low overlap for certain TFs are not discussed in sufficient detail.
- **Why it matters** The validity of the high-quality test sets is central to the paper's conclusions. If the negative definition is flawed, all downstream comparisons are compromised.
- **Resolution test** Provide a detailed description of the negative selection criteria, including thresholds, filtering steps, and handling of ambiguous cases. Discuss the potential impact of TFs with low ChIP-seq/ATAC-seq overlap on the reliability of the test sets.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.1, discussion of standard AUROC scores
- **Evidence pointer** Section 3.1, location not provided
- **Issue** The interpretation of standard AUROC scores is somewhat confusing. The authors note that high performance on shuffled datasets indicates the model learns to differentiate real from shuffled sequences, but then state that genome-sampled datasets also perform well. The distinction between "learning to recognize binding sites" and "learning dataset-specific features" could be clarified.
- **Required correction** Clarify the reasoning for why high standard AUROC on genome-sampled datasets is more meaningful than on shuffled datasets, given that both involve distinguishing positives from negatives.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.5, dataset size analysis
- **Evidence pointer** Section 3.5, Fig. 3, location not provided
- **Issue** The dataset size analysis is described only briefly. It is unclear how many TFs were included, how the TFs were selected, and whether the results are representative.
- **Required correction** Provide more detail on the selection of TFs for this analysis and the range of dataset sizes tested.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.3, model training
- **Evidence pointer** Section 2.3, location not provided
- **Issue** The description of the model architecture and training procedure is high-level. Details such as the number of parameters, regularization, early stopping criteria, and hyperparameter search ranges are not provided.
- **Required correction** Provide a more detailed description of the model and training procedure, or reference a prior publication with full details.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.4, PWM comparison
- **Evidence pointer** Section 3.4, Fig. 2, location not provided
- **Issue** The PWM comparison is presented as a "surprising" result, but the authors do not discuss why this might be the case or what implications it has for the field.
- **Required correction** Add a brief discussion of why the PWM approach performs relatively well and what this means for the value of deep learning methods in this context.

## Risk / unsupported claims
- The claim that genomic sampling is "by far the best" method is not supported by statistical evidence in the supplied material.
- The claim that models trained on genome-sampled datasets capture "commonality in the binding patterns of the TFs" is speculative and not directly supported by the described analyses.
- The claim that dinucleotide shuffling is "a common practice in the field" is stated without citation or evidence.
- The claim that the findings "highlight the importance of carefully selecting negative sampling techniques" is reasonable but the generalizability across all TFs and cell lines is not established.
- The performance of the PWM-based approach relative to deep learning models is reported as "surprising" but the implications are not discussed in sufficient depth.
- The statement that "the choice of negatives can be the difference between a model that is an improvement over the capabilities of a simple motif scan and one that is not" is a strong claim that requires the full results to verify.