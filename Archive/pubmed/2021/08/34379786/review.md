## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Methodological soundness, experimental design, evaluation rigor, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present Epitome, a deep neural network that predicts transcription factor binding and histone modification events in novel cell types by learning similarities in chromatin accessibility between reference cell types and a query cell type. The method uses a chromatin accessibility similarity vector (CASV) and an ensemble of cell-type-specific neural network channels to transfer epigenetic annotations from reference to query contexts. The authors claim state-of-the-art accuracy compared to existing methods, including DeFCoM, Catchitt, Avocado, and DeepHistone.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Discussion, Data Availability sections. Figures referenced but not fully visible: Figures 1-5, Supplementary Figures S1-S16, Supplementary Tables S1-S10.
- **Missing materials affecting confidence** Figure contents and detailed results (exact performance numbers, error bars, statistical significance tests) are not fully visible in the provided text. Supplementary figures and tables referenced throughout are not included. Algorithm 1 pseudocode is referenced but not shown. Hyperparameter details and model architecture specifics are partially described but not fully specified.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach to a practically important problem: predicting epigenetic events in cell types where only chromatin accessibility data are available. The idea of using local similarity between query and reference cell types, computed at multiple genomic resolutions, is sensible and well motivated. The authors compare against several relevant baselines and demonstrate competitive performance. However, the manuscript has several weaknesses that need to be addressed. The evaluation methodology has potential issues, particularly regarding the fairness of comparisons with methods that were not designed for the same task. The treatment of the upper bound on sensitivity is somewhat circular. The claim of state-of-the-art performance is not fully supported by the visible evidence, as exact numbers and statistical tests are not provided in the text. The writing is generally clear but some sections are dense and could benefit from more explicit explanation for a broader readership.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, particularly those interested in transferring epigenetic annotations across cell types. Researchers developing deep learning methods for genomics would also find the architecture and training scheme of interest. The practical utility for experimentalists who have generated ATAC-seq or DNase-seq data in a novel cell type and wish to prioritize ChIP-seq experiments would be significant. The open-source implementation and documentation make the method accessible.

- **Major Strengths**
  1. The problem is well defined and practically relevant. The ability to predict TF binding and histone modifications in cell types where only accessibility data exist has clear utility.
  2. The CASV concept is a thoughtful way to incorporate local, multi-resolution similarity between cell types, and the ablation-style analyses (e.g., varying genomic context size) help justify design choices.
  3. The comparison against multiple baseline methods spanning different methodological categories (footprinting, feature-based, imputation, sequence-based) is thorough.
  4. The application to neural differentiation time-course data provides a compelling real-world demonstration.
  5. The authors are transparent about limitations, including the upper bound on sensitivity imposed by the reference set and the potential for false negatives in poorly annotated regions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evaluation rigor
- **Claim pointer** "Epitome achieves state-of-the-art accuracy when predicting TF binding sites in held out cellular contexts and chromosomes."
- **Evidence pointer** Results section, Figure 2, Supplementary Figures S6-S11
- **Concern** The claim of state-of-the-art performance is not fully substantiated by the visible evidence. The text describes qualitative comparisons (e.g., "Epitome performs better than" or "comparable to") but does not provide exact performance numbers, confidence intervals, or statistical significance tests in the main text. The comparison with DeFCoM is restricted to motif-overlapping regions, which is a necessary constraint but also limits the generality of the comparison. The comparison with DeepSEA is described as "comparable," which is a weak claim given that DeepSEA does not use any cell-type-specific information. The comparison with Avocado and Catchitt is described in aggregate but individual per-TF results are not shown in the main text.
- **Why it matters** The central claim of the paper is that Epitome achieves state-of-the-art accuracy. Without precise quantitative results and statistical testing, the reader cannot assess the magnitude of improvement or whether differences are meaningful. This is particularly important given the variability in performance across TFs and cell types that is typical in this domain.
- **Resolution test** Provide a table with mean and standard deviation of auPRC and pAUC across all TFs and cell types for each method, along with paired statistical tests (e.g., Wilcoxon signed-rank test) comparing Epitome to each baseline. Include per-TF results in supplementary material. Report the number of TFs for which Epitome is significantly better, worse, or not significantly different.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological soundness
- **Claim pointer** "Epitome places an upper bound on maximum achievable sensitivity" and "we observe a mean level of coverage, or sensitivity, of over 90% for widely-assayed TFs and histone modifications."
- **Evidence pointer** Results section, Figure 1A, Processing ChIP-Atlas database section
- **Concern** The analysis of the upper bound on sensitivity is somewhat circular. The authors define the upper bound as the fraction of peaks in a held-out cell type that are present in at least one reference cell type. This is a reasonable definition, but the claim that this bound is "over 90%" depends on the number of reference cell types available. The analysis in Figure 1A shows that the fraction of unique peaks decreases with more cell types, but the text does not specify how many cell types are needed to reach 90% coverage, nor does it discuss the variability across TFs. More importantly, the upper bound analysis is used to justify the design choice of binary peak calls, but the authors do not compare against an alternative that uses continuous signal to see if the loss of information is actually detrimental in practice.
- **Why it matters** The upper bound analysis is used to motivate a key design decision (binary peak calls). If the bound is not robust or if continuous signal would yield better performance despite the bound, the design choice may be suboptimal. The reader needs to understand the conditions under which the 90% coverage claim holds.
- **Resolution test** Provide a more detailed analysis of the upper bound, including the distribution of coverage across TFs and the number of cell types required to achieve 90% coverage. Additionally, include a comparison of Epitome using binary peaks versus a version that uses continuous signal (e.g., read counts or fold enrichment) to empirically test whether the binary representation is indeed optimal.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "Epitome trains a model on n ENCODE cell types by using n – 1 cell types for features x and a held-out cell type as labels y."
- **Evidence pointer** Materials and Methods, Training an Epitome model, Algorithm 1
- **Concern** The training procedure is described at a high level, but several important details are missing. The cell type rotation mechanism is described, but it is unclear how the model is initialized and whether the rotation is performed in a specific order. The number of training epochs, learning rate schedule, and optimization algorithm are not specified. The architecture of the neural network (number of layers, hidden units, activation functions) is partially described, but the ensemble mechanism (how multiple models are combined) is not explained in detail. The text mentions "deep ensemble learning" in the title, but the ensemble aspect is not clearly described in the methods.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without full details on the training procedure and architecture, other researchers cannot reimplement or build upon the method. The ensemble aspect is highlighted in the title but not adequately explained.
- **Resolution test** Provide a complete description of the model architecture, training hyperparameters, and ensemble strategy. Include the pseudocode for Algorithm 1 in the main text or supplementary material. Specify how the ensemble predictions are aggregated (e.g., averaging probabilities, voting). Provide the code and trained models in a public repository.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evaluation rigor
- **Claim pointer** "Epitome can further improve predictions as more epigenetic events are collected from both the reference cell types and the query cellular context of interest."
- **Evidence pointer** Results section, Figure 3, Figure 4
- **Concern** The claim that adding more reference cell types improves performance is supported by Figure 3, but the analysis is limited to a single held-out cell type per model. The text states that performance increases with more reference cell types, but it is unclear whether this trend is consistent across all TFs and cell types or whether there is a plateau. The analysis of adding histone modifications to the CASV (Figure 4C, D) is also limited to 13 TFs and 4 cell lines, which is a relatively small set. The Shapley value analysis is interesting but the interpretation is somewhat brief.
- **Why it matters** The claim that the method improves with more data is important for users who may want to apply Epitome in settings where reference data are limited. The generalizability of the findings from 13 TFs and 4 cell lines to the broader set of TFs and cell types is unclear.
- **Resolution test** Extend the analysis in Figure 3 to show performance as a function of the number of reference cell types for multiple held-out cell types, with error bars. For the histone modification analysis, include more TFs and cell types if possible, or at least discuss the limitations of the current set. Provide a more detailed interpretation of the Shapley values, including which histone modifications are most informative and why.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that Epitome "copies over" signal from reference cell types. This phrasing is somewhat informal and could be misinterpreted as a simple copy operation rather than a learned prediction.
- **Required correction** Rephrase to something like "transfers" or "predicts based on" to more accurately describe the learning process.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and Methods, Equation (2)
- **Evidence pointer** Materials and Methods, Equation (2)
- **Issue** The loss function in Equation (2) is described as a modified logistic loss, but the derivation is not shown. The formula appears to be a standard stable softmax cross-entropy, but the connection to the logistic loss is not immediately obvious.
- **Required correction** Briefly explain how Equation (2) is derived from the logistic loss and why the modification is needed for numerical stability.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Materials and Methods, Processing ENCODE data
- **Evidence pointer** Materials and Methods, Processing ENCODE data
- **Issue** The text states that "only ChIP-seq targets that had experiments for more than three cell types were considered" but does not specify the exact number of TFs and cell types used in the final analysis. The number of cell types (17 for hg19, 93 for hg38) is mentioned, but the number of TFs is not clearly stated.
- **Required correction** Provide the exact number of TFs and cell types used in each analysis, either in the main text or in a supplementary table.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results, Section 3.1
- **Evidence pointer** Results, Section 3.1
- **Issue** The description of the comparison with DeFCoM is somewhat confusing. The text says "we only compare Epitome and DeFCoM in regions overlapping motifs," but then discusses the ratio of peaks not overlapping motifs. The logic of this comparison could be clearer.
- **Required correction** Clarify why the comparison is restricted to motif-overlapping regions and how this affects the interpretation of the results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and Methods, Resource requirements
- **Evidence pointer** Materials and Methods, Resource requirements
- **Issue** The resource requirements section mentions that models were trained on CPUs, but does not specify the runtime or memory usage for a typical model. This information would be useful for users who want to apply the method.
- **Required correction** Provide approximate runtime and memory requirements for training and inference on a typical dataset.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion mentions that Epitome can be used as a "mechanistic complement" to gene-ontology based approaches, but this point is not elaborated. A brief example or explanation of how the two approaches would be combined would strengthen the discussion.
- **Required correction** Add a sentence or two explaining how Epitome predictions could be integrated with gene-ontology based methods in practice.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative results and statistical tests), R1-M2 (circularity in upper bound analysis), R1-M3 (incomplete methodological details for reproducibility)

- **Assessment against Nature-style criteria**
  - **Originality** The approach of using multi-resolution local similarity between cell types to transfer epigenetic annotations is a novel contribution. The CASV concept is a reasonable and well-motivated design choice. However, the overall idea of predicting epigenetic marks from accessibility data is not entirely new, and the novelty lies primarily in the specific implementation and the ensemble approach.
  - **Scientific importance** The problem is important. The ability to predict TF binding and histone modifications in novel cell types has practical implications for understanding gene regulation and prioritizing experiments. The method could be useful to a broad community of researchers.
  - **Interdisciplinary readership** The manuscript is likely to appeal primarily to computational biologists and bioinformaticians. The writing is generally accessible, but some sections (e.g., the detailed description of the CASV and the neural network architecture) may be challenging for readers without a machine learning background. The authors make an effort to explain the biological motivation, which helps.
  - **Technical soundness** The technical approach is sound in principle, but the evaluation has weaknesses. The lack of precise quantitative results and statistical tests is a significant issue. The comparison with DeepSEA is described as "comparable," which is a weak claim. The analysis of the upper bound on sensitivity is somewhat circular. The methodological details are incomplete, which hinders reproducibility.
  - **Readability for nonspecialists** The abstract and introduction are clear and accessible. The results and methods sections are more technical and may be difficult for nonspecialists to follow. The authors use jargon (e.g., "auPRC," "pAUC," "CASV") without always defining it clearly for a general audience. A brief explanation of these terms in the text or a glossary would be helpful.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the method appears to work well, but the manuscript needs to provide more rigorous quantitative evidence, address the circularity in the upper bound analysis, and provide complete methodological details for reproducibility. If these issues are addressed, the manuscript could make a valuable contribution to the field.