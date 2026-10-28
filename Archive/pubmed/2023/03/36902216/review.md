## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Technical and scientific evaluation of the proposed PROTRAIT framework, its validation, and claims, based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors propose PROTRAIT, a unified deep learning framework based on a ProbDep Transformer Encoder, for single-cell ATAC-seq analysis. The framework claims to predict chromatin accessibility, annotate cell types, denoise scATAC-seq data, and infer transcription factor activity at single-cell and single-nucleotide resolution, with demonstrated scalability to over one million cells.
- **Visible evidence base** Results sections 2.1-2.5, Figures 1-7 (referenced but not shown), Materials and Methods section 3, Abstract
- **Missing materials affecting confidence** Figures and tables are referenced but not provided; no quantitative performance metrics (e.g., AUROC values, ARI scores) are reported in the text; no statistical significance tests are described; no comparison of computational efficiency metrics beyond runtime; no details on hyperparameter search ranges or final model configuration; no code availability statement

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting application of transformer-based architectures to scATAC-seq analysis, with the ambition of unifying multiple downstream tasks in a single framework. However, the evidence provided in the text is insufficient to substantiate the major claims. Key quantitative results are absent, figures are not available for inspection, and several methodological details are either missing or ambiguous. The work has potential merit, but the current manuscript does not establish the case for its stated advantages over existing methods.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on single-cell epigenomics, particularly those developing or applying deep learning methods for scATAC-seq data. The unified framework concept and the use of transformer encoders for regulatory grammar learning may appeal to researchers interested in sequence-based models of gene regulation. The scalability claim could be of interest to those analyzing large-scale atlases.
- **Major strengths** The conceptual framing of scATAC-seq analysis as a language modeling problem is timely and potentially impactful. The ambition to unify prediction, annotation, denoising, and TF activity inference in one framework is commendable. The use of ProbDep attention to capture long-range dependencies is a reasonable design choice. The scalability experiments on a million-cell dataset address an important practical need.
- **Major Concerns** (see detailed items below)
- **Minor Comments** (see detailed items below)
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative results), R1-M2 (inadequate baseline comparisons), R1-M3 (unvalidated denoising approach), R1-M4 (insufficient TF activity validation), R1-M5 (scalability claim not substantiated)
- **Assessment against Nature-style criteria** Originality: moderate, as transformer-based models for scATAC-seq exist, though the unified framework is a distinguishing feature. Scientific importance: potentially high if validated, but current evidence is insufficient. Interdisciplinary readership: the topic is relevant to both machine learning and genomics audiences, but the presentation assumes significant domain expertise. Technical soundness: cannot be fully assessed due to missing details and results. Readability for nonspecialists: the manuscript is dense and would benefit from clearer explanations of the method and its advantages.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial revision, including the addition of quantitative results, proper baseline comparisons, and methodological clarifications, before the claims can be evaluated.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim PROTRAIT "substantially outperforms all competitors" in chromatin accessibility prediction (Section 2.1) and achieves "state-of-the-art performance" across various analysis scenarios (Section 1, Abstract).
- **Evidence pointer** Section 2.1, Figure 2 (not provided)
- **Concern** The text states that PROTRAIT outperforms baselines but provides no quantitative metrics, such as AUROC values, confidence intervals, or statistical significance tests. The referenced figures are not available for inspection.
- **Why it matters** Without numerical results, the central claim of superior performance cannot be verified. The reader cannot assess the magnitude of improvement or whether differences are meaningful.
- **Resolution test** Provide AUROC values (or other relevant metrics) for all methods and input lengths, with error bars or confidence intervals, and state whether differences are statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative validity
- **Claim pointer** The authors claim PROTRAIT outperforms "current approaches" including Basset, DeepSEA, scBasset, and Basenji (Section 2.1).
- **Evidence pointer** Section 2.1, Figure 2 (not provided)
- **Concern** The comparison is potentially unfair. The baseline models were designed for bulk or different single-cell data and may not have been retrained or tuned for the scATAC-seq setting. The manuscript does not describe how baselines were trained, whether hyperparameters were optimized, or whether the same data splits were used.
- **Why it matters** An unfair comparison undermines the validity of the performance claims. The reader cannot determine whether PROTRAIT is genuinely superior or whether the baselines were disadvantaged.
- **Resolution test** Describe the training and tuning protocol for all baselines, including data splits, hyperparameter search, and any modifications made for the scATAC-seq context. Ensure all methods are evaluated under identical conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The authors claim PROTRAIT "denoises these values based on predicted chromatin accessibility" and outperforms existing denoising methods (Section 2.3).
- **Evidence pointer** Section 2.3, Figure 4 (not provided)
- **Concern** The denoising approach relies on a mixture model to identify dropout events, but the manuscript does not provide details on how the model parameters are initialized, how the number of mixture components is determined, or how the threshold T is chosen. The evaluation metric (label score) is described but no quantitative results are given.
- **Why it matters** The denoising claim is a key contribution of the framework. Without methodological details and quantitative evaluation, the approach cannot be reproduced or assessed.
- **Resolution test** Provide full details of the mixture model, including parameter estimation, model selection, and threshold selection. Report label scores for all methods and conditions, with appropriate statistical comparisons.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation depth
- **Claim pointer** The authors claim PROTRAIT can infer TF activity at single-cell and single-nucleotide resolution, and that the inferred activities are consistent with literature (Sections 2.4, Abstract).
- **Evidence pointer** Section 2.4, Figures 5 and 6 (not provided)
- **Concern** The TF activity inference is validated only through qualitative comparison with literature for a small set of TFs. No quantitative assessment (e.g., correlation with known TF binding, enrichment analysis) is provided. The single-nucleotide resolution results are described for one enhancer only.
- **Why it matters** TF activity inference is a central claimed capability. The current validation is anecdotal and does not demonstrate generalizability or accuracy.
- **Resolution test** Provide quantitative validation, such as comparison with independent TF binding data (e.g., ChIP-seq), enrichment of inferred active TFs in known cell-type-specific regulators, or ROC-style analysis for motif predictions. Include multiple enhancers and cell types.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Scalability evidence
- **Claim pointer** The authors claim PROTRAIT "is suitable for analyzing a sizeable scATAC-seq compendium" and demonstrate scalability to over one million cells (Sections 2.5, Abstract).
- **Evidence pointer** Section 2.5, Figure 7 (not provided)
- **Concern** The scalability experiment reports runtime and memory usage but provides no comparison with other methods. The observed runtime of 2084 minutes (about 35 hours) on a single GPU may not be competitive. The manuscript does not discuss whether the model can be trained on such large data in practice, given memory constraints.
- **Why it matters** Scalability is a claimed advantage, but without comparative benchmarks, the reader cannot judge whether PROTRAIT is more scalable than existing approaches.
- **Resolution test** Compare runtime and memory usage with at least one state-of-the-art method on the same data and hardware. Discuss practical implications of the observed resource usage.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2.1, Equation (3)
- **Evidence pointer** Section 3.2.1
- **Issue** The equation for the uniform input representation is incomplete. It reads "X(0)=αu+PE(,)" where the arguments to PE are missing.
- **Required correction** Provide the complete equation with the correct arguments for the position encoding.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 3.2.2, Equation (5)
- **Evidence pointer** Section 3.2.2
- **Issue** The approximation for the long-range dependency measurement is stated without justification or reference. The sampling strategy for query-key pairs is not described.
- **Required correction** Provide a reference for the approximation or a derivation, and describe the sampling procedure in detail.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1
- **Issue** The description of the Buenrostro 2018 dataset mentions 10 cell populations but only lists 9 (CLP, CMP, GMP, HSC, LMPP, MEP, MPP, pDC, mono, and an uncharacterized population). The text says "10 FACS cell populations" but the list appears to include 10 items if the uncharacterized population is counted. This is ambiguous.
- **Required correction** Clarify the exact number of cell populations and list all of them explicitly.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract, Sections 1, 2
- **Issue** The term "ProdDep" is used inconsistently. In some places it is "ProdDep" and in others "ProbDep". The correct name should be used consistently.
- **Required correction** Use a single consistent name for the transformer encoder throughout the manuscript.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2, Figure 3 (not provided)
- **Issue** The clustering evaluation reports ARI, AMI, and v-score but does not state whether these are averaged over multiple runs or whether the clustering is deterministic.
- **Required correction** State whether results are averaged over multiple runs and report standard deviations or ranges.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 3.4
- **Evidence pointer** Section 3.4
- **Issue** The threshold T for dropout identification is mentioned but its value is not specified.
- **Required correction** Provide the value of T or describe how it is determined.

## Risk / unsupported claims
- The claim of "state-of-the-art performance" across all analysis scenarios is unsupported because no quantitative results are provided in the text.
- The claim that PROTRAIT "substantially outperforms" baselines in chromatin accessibility prediction is unsupported without numerical metrics.
- The claim of scalability to over one million cells is only partially supported by runtime and memory data, but no comparison with other methods is provided.
- The claim that TF activity inference is consistent with literature is based on qualitative assessment for a small number of TFs and is not quantitatively validated.
- The claim that the denoising approach outperforms existing methods is unsupported without quantitative label scores.
- The methodological description of the ProbDep attention mechanism is incomplete, making the novelty and technical soundness difficult to assess.