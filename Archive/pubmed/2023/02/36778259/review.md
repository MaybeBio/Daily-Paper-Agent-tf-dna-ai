## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv 2023.02.02.526909)
- **Assessment boundary** Scientific content, methodological soundness, claims vs. evidence, and presentation quality as presented in the provided text
- **Shared manuscript claim summary** The authors present SupirFactor, a knowledge-primed deep learning autoencoder framework for gene regulatory network (GRN) inference and transcription factor activity (TFA) estimation. The model constrains an intermediate latent layer to be TF-specific using prior regulatory evidence, enabling direct interpretation as TFA. A novel metric, explained relative variance (ERV), is introduced for model interpretation and weight ranking. The authors claim improved GRN recovery over existing methods, biologically relevant TFA predictions, and utility for pathway analysis via a hierarchical extension with meta-TFs (mTFs), demonstrated on bacterial, yeast, and mammalian single-cell datasets.
- **Visible evidence base** Abstract, Introduction, Results (Sections 2.1–2.5), Discussion, Methods (Sections 4.1–4.8), figure legends referenced (Figures 1–5), supplemental figure references (S1–S11), Table 1
- **Missing materials affecting confidence** Actual figures and supplemental figures not provided; exact numerical results, statistical test outputs, and dataset-specific performance metrics not fully detailed in text; code availability not stated; comparison details for Inferelator and AMuSR not fully specified

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting approach that combines knowledge priming with deep learning for GRN inference, addressing a real need for interpretable models in regulatory genomics. The core idea of constraining a latent layer to TF identities and interpreting its activity as TFA is sound and potentially valuable. The introduction of ERV as an interpretation metric is a useful contribution. However, the manuscript as presented has several significant weaknesses. The benchmarking claims are not fully substantiated with quantitative details in the text, the statistical rigor of some analyses (e.g., Fisher exact test, correlation comparisons) is not described, and the biological validation of TFA predictions is largely qualitative. The hierarchical model's added complexity and its claimed advantages over the shallow model require stronger evidence. The writing is dense and at times unclear, particularly in the methods section. Overall, the core ideas have merit, but the evidence presented is insufficient to fully establish the claimed advantages over existing methods.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, single-cell genomics, and interpretable deep learning. Researchers studying transcriptional regulation in yeast and mammalian immune cells would find the TFA and pathway analysis applications relevant. The ERV metric may be of interest to those developing interpretability tools for neural networks in genomics.
- **Major strengths**
  - The concept of structure-primed embedding, using prior regulatory knowledge to constrain a latent layer, is a novel and principled approach to improve interpretability in deep learning models for GRNs.
  - The explicit definition of the latent layer as TFA, with a non-negativity constraint via ReLU, provides a biologically meaningful and testable output.
  - The ERV metric offers a principled, bounded way to rank regulatory connections, addressing a key limitation of raw weight interpretation in neural networks.
  - The application to a multimodal single-cell dataset (PBMC ATAC+RNA) demonstrates a practical pathway for integrating epigenetic data into the model.
  - The demonstration of model generalization to unseen experimental data (new yeast RNA-seq datasets) is a strong point.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** "SupirFactor outperforms current leading GRN inference methods" (Abstract, Results Section 2.3)
- **Evidence pointer** Figure 2C, Section 2.3, "location not provided" for specific AUPR values
- **Concern** The central claim of superior performance is based on comparisons to the Inferelator, but the text does not provide the actual AUPR values, confidence intervals, or statistical tests for the comparisons. The description "improves significantly" is not supported by any reported p-values or effect sizes. Furthermore, the choice of the Inferelator as the sole comparator is limited; the claim of "outperforms current leading methods" requires benchmarking against a broader set of state-of-the-art GRN inference tools.
- **Why it matters** The primary contribution of the paper is a new method, and its claimed superiority is the main justification for its adoption. Without quantitative, statistically rigorous evidence, the central claim is unsubstantiated.
- **Resolution test** Provide a table with AUPR (and other relevant metrics) for SupirFactor and at least 2-3 other leading methods (e.g., GENIE3, GRNBoost2, PIDC) across all benchmark datasets, including standard deviations and statistical significance tests (e.g., Wilcoxon signed-rank test).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological validation of TFA
- **Claim pointer** "predicts biologically relevant TFA" (Abstract, Results Section 2.4)
- **Evidence pointer** Figure 3A–E, Section 2.4
- **Concern** The biological validation of TFA is largely qualitative. The claim that TFA peaks in expected cell cycle phases is based on visual inspection of Figure 3A, with no quantitative comparison to known phase-specific activity or to expression data. The correlation analyses for TF pairs (Figure 3C) are reported as single correlation coefficients without confidence intervals or tests against a null distribution. The rapamycin perturbation analysis (Figure 3E) is described narratively without a systematic assessment of known TOR pathway targets.
- **Why it matters** A key selling point of the method is that it provides biologically meaningful latent variables. If the TFA estimates cannot be rigorously validated against known biology, the interpretability advantage is not demonstrated.
- **Resolution test** Provide quantitative comparisons of TFA to independent activity measurements (e.g., Western blots, phosphorylation assays, or published perturbation datasets). For cell cycle, compare TFA dynamics to a gold-standard set of phase-specific targets using a statistical enrichment test. For TF pairs, report correlation values with confidence intervals and compare to correlations from shuffled or null models. For rapamycin, perform a rank-based enrichment analysis of known TOR-responsive genes among the top differentially active TFs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity and justification
- **Claim pointer** "hierarchical SupirFactor...elucidates functional regulatory pathways through aggregation of TFs" (Abstract, Results Section 2.5)
- **Evidence pointer** Figure 4A–D, Section 2.5, Methods Section 4.1
- **Concern** The biological interpretation of the meta-TF (mTF) layer is not rigorously justified. The claim that mTFs represent "pathways" is inferred from KEGG enrichment of their target genes, but the text does not explain how the aggregation of TFs into an mTF is biologically distinct from simple co-regulation or correlation. The choice of the number of mTFs (148) and the interpretation of their activity as pathway activity requires more formal justification. The comparison of mTF activity across conditions (Figure 4B) is descriptive.
- **Why it matters** The hierarchical model is presented as a major extension, but its added value over the shallow model for generating biological hypotheses is not clearly demonstrated. If mTFs are just clusters of correlated TFs, the claim of "pathway" discovery is overstated.
- **Resolution test** Provide a formal definition of what constitutes a "pathway" in this context and demonstrate that mTFs capture known regulatory modules better than, for example, simple clustering of TF expression or activity. Show that mTF activity provides information beyond the average activity of its constituent TFs. Validate a subset of mTF-target gene predictions experimentally or against independent perturbation data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Robustness and stability of the model
- **Claim pointer** "maintains interpretability to perform GRN inference and estimate TFA" (Abstract, Section 2.1)
- **Evidence pointer** Methods Section 4.3, Section 2.2, Supplemental Figures S2–S9
- **Concern** The manuscript does not report on the stability of the inferred GRN and TFA estimates across different random seeds, initialization schemes, or data subsamples. The hyperparameter search is described, but the sensitivity of the final model to these choices is not discussed. The pruning procedure (Section 2.2) is described as iterative, but the convergence criteria and the impact of pruning on the final network's stability are not detailed.
- **Why it matters** Deep learning models are notoriously sensitive to initialization and training stochasticity. For a method to be useful, users need to know how much the results might vary. Without stability analysis, the reliability of the inferred networks and TFA is unknown.
- **Resolution test** Run the model with multiple random seeds (e.g., 10) and report the variance in AUPR, TFA estimates, and the overlap of top-ranked edges. Perform bootstrap subsampling of cells and assess the stability of the inferred network structure. Report the convergence of the pruning procedure and the sensitivity of the final network to the pruning threshold.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparison to alternative deep learning approaches
- **Claim pointer** "Deep learning frameworks may offer a solution...However, these methods often discard central concepts...in favor of increased model complexity" (Introduction)
- **Evidence pointer** Introduction, Section 2.3
- **Concern** The introduction critiques deep learning methods for lacking interpretability, but the manuscript does not compare SupirFactor to any other deep learning-based GRN inference method. The comparison is only to the Inferelator, a linear regression-based method. To substantiate the claim that SupirFactor addresses the limitations of deep learning approaches, a comparison to at least one other interpretable or knowledge-primed deep learning model (e.g., a variational autoencoder with sparse priors, or a graph neural network with attention) is necessary.
- **Why it matters** The positioning of the paper is against "black box" deep learning, but without a direct comparison, the claimed advantage is not demonstrated.
- **Resolution test** Include a comparison to a state-of-the-art deep learning GRN method (e.g., DeepSEM, GRNTransformer, or a VAE-based approach) on the same benchmark datasets, evaluating both performance (AUPR) and interpretability (e.g., ability to recover known regulatory motifs).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Section 1
- **Issue** The abstract and introduction are dense and use jargon without clear definitions (e.g., "transcription factor manifold", "white-box machine learning"). The motivation for the hierarchical model is not clearly stated in the abstract.
- **Required correction** Simplify the abstract to state the problem, the method, and the key findings in more accessible language. Define "transcription factor manifold" and "white-box" in the introduction. Briefly state the rationale for the hierarchical extension in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.4, Table 1
- **Evidence pointer** Table 1, Section 2.4
- **Issue** The Fisher exact test for cell cycle phase enrichment is mentioned, but the p-values are not reported in the text or table. The threshold for significance is not stated.
- **Required correction** Report the p-values for the enrichment analysis in Table 1 or in the text, and state the significance threshold used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods Section 4.7.2
- **Evidence pointer** Section 4.7.2
- **Issue** The RobustMinScaler is described, but the rationale for this specific normalization choice over other methods (e.g., log1p followed by scaling) is not given. The impact of this choice on the results is not discussed.
- **Required correction** Provide a brief justification for the RobustMinScaler and, if possible, a sensitivity analysis showing the effect of different normalization methods on the benchmark results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Data Availability
- **Evidence pointer** Section 4.6, Data Availability statement (not present)
- **Issue** The manuscript does not state whether the code and processed data are publicly available. This is critical for reproducibility.
- **Required correction** Add a Data and Code Availability statement specifying where the code, processed data, and any trained models can be accessed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality and presentation
- **Affected element** Figures 1–5
- **Evidence pointer** Figure legends
- **Issue** The figure legends are referenced but the figures themselves are not provided. Based on the legends, the figures appear complex and may be difficult to interpret. For example, Figure 1A–E appears to combine multiple schematics and results.
- **Required correction** Ensure figures are clear, well-labeled, and self-contained. Consider splitting complex figures into multiple panels with clear sub-figure labels.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative performance comparison with statistical rigor.
  - R1-M2: Lack of quantitative biological validation of TFA.
  - R1-M3: Unclear biological justification for the mTF layer.
  - R1-M4: No analysis of model stability and robustness.
  - R1-M5: No comparison to other deep learning methods.

- **Assessment against Nature-style criteria**
  - **Originality:** The concept of using a knowledge-primed latent layer for TFA inference is a novel contribution. The ERV metric is also a new and potentially useful tool. However, the overall architecture (autoencoder) is not new, and the novelty lies in the specific application and constraints.
  - **Scientific importance:** GRN inference and TFA estimation are important problems in genomics. A method that improves interpretability and performance would be valuable. The demonstration on a multimodal dataset is a step towards practical application. However, the importance is not fully established due to the lack of rigorous benchmarking and validation.
  - **Interdisciplinary readership:** The work is primarily of interest to computational biologists and bioinformaticians. The biological applications (yeast cell cycle, PBMC cell types) may attract some experimental biologists, but the technical complexity may limit broader appeal.
  - **Technical soundness:** The core methodology is plausible, but the technical soundness is undermined by the lack of statistical rigor in the performance comparisons and the lack of stability analysis. The description of the ERV calculation and the hierarchical model's training procedure is incomplete.
  - **Readability for nonspecialists:** The manuscript is not easily accessible to nonspecialists. The abstract and introduction are dense, and the methods section is highly technical. The biological findings are not presented in a way that would be clear to a general biology audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The core ideas are promising and address a real need. However, the current evidence is insufficient to support the central claims of superior performance and biological relevance. The authors must provide quantitative, statistically rigorous benchmarking, a more thorough biological validation of TFA, and an analysis of model stability. The manuscript would also benefit from improved clarity and accessibility.

## Risk / unsupported claims
- The claim that SupirFactor "outperforms current leading GRN inference methods" is unsupported by the provided evidence, as only a single comparison to the Inferelator is described without quantitative results.
- The claim that the model "predicts biologically relevant TFA" is weakly supported, as the validation is largely qualitative and lacks statistical rigor.
- The claim that mTFs represent "functional regulatory pathways" is an interpretation that is not rigorously justified.
- The claim that the model "scales to single cell genomic data" is supported by the PBMC application, but the performance and scalability compared to other methods on this data type are not quantified.
- The generalizability of the model to other organisms and data types beyond those tested is not demonstrated.