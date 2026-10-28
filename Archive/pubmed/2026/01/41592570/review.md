## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and STAR Methods.
- **Assessment boundary** Scientific validity, technical soundness, methodological rigor, interpretability claims, and significance of the presented results. The review is based solely on the provided manuscript text; no external data or code was accessed.
- **Shared manuscript claim summary** The authors present ChromBERT, a foundation model pre-trained on a large collection of human ChIP-seq data (Cistrome-Human-6K, 6,391 cistromes, ~1,000 transcription regulators). The model learns interpretable representations of transcriptional regulatory networks (TRNs) at 1-kb genomic intervals. Through prompt-enhanced fine-tuning, it imputes unseen cistromes and, via lightweight fine-tuning on cell-type-specific tasks, identifies key regulators driving regulatory effects and cell-state transitions without additional ChIP-seq experiments.
- **Visible evidence base** Main text figures (Figures 1–4), supplementary figure references (Figures S1–S12), tables (Tables S1–S4), and STAR Methods descriptions. No raw data, code, or full supplementary material were available for direct inspection.
- **Missing materials affecting confidence** The full supplementary figures and tables (S1–S12, S1–S4) were not provided. Detailed hyperparameter settings, model architecture diagrams, and complete benchmark results are referenced but not fully visible. The code and datasets are publicly available but were not independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a novel and potentially impactful foundation model for transcriptional regulatory network analysis. The core idea of treating ChIP-seq binding profiles as a "language" of regulatory interactions, and the use of masked pre-training to learn interpretable TRN embeddings, is creative and timely. The demonstrated improvements in cistrome imputation and the ability to recover known regulators in cell-type-specific contexts are promising. However, several technical aspects require clarification and additional validation to fully establish the claims. The interpretability framework, while elegant, needs more rigorous benchmarking against existing methods and a clearer demonstration that the identified regulators are causal rather than merely correlated. The manuscript is well-written and the figures are informative, but the current evidence base is insufficient to fully support all stated conclusions.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing and applying foundation models to genomics. Researchers studying transcriptional regulation, chromatin biology, and gene regulatory networks, particularly those interested in cell-type-specific mechanisms. The model's ability to impute missing ChIP-seq data and identify key regulators without additional experiments will be of broad interest to the functional genomics community.
- **Major strengths**
    1.  **Novel conceptual framing**: Treating ChIP-seq binding profiles as a language and using BERT-style masked pre-training to learn regulatory syntax is a fresh and promising approach, distinct from sequence-only foundation models.
    2.  **Comprehensive pre-training corpus**: The assembly of the Cistrome-Human-6K dataset, covering ~1,000 regulators across many cell types, is a valuable community resource.
    3.  **Demonstrated utility in cistrome imputation**: The significant improvement over baseline methods and the state-of-the-art model Avocado for imputing unseen cistromes is a strong, concrete result.
    4.  **Interpretable, context-specific insights**: The framework for identifying key regulators via embedding shifts is intuitive and provides a path to hypothesis generation without requiring new experiments.
    5.  **Broad applicability**: The model is tested on diverse tasks (eQTL fine-mapping, enhancer activity prediction, cell-state transitions), suggesting generalizability.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness / Validation
    - **Claim pointer** The claim that ChromBERT "outperforms existing methods for imputing unseen cistromes" and the specific comparison to Avocado.
    - **Evidence pointer** Figure 2B, 2F; STAR Methods "Benchmark for cistrome imputation"
    - **Concern** The benchmark against Avocado is described as using "imputed tracks from ENCODE (ENCSR481OSA)" and is restricted to "cistromes withheld from the fine-tuning of ChromBERT and the training of Avocado." However, the exact number of test cistromes, the diversity of cell types and regulators in the test set, and the criteria for selecting them are not fully detailed. More critically, the comparison to Avocado is only possible for a subset of cistromes (those available in the ENCODE imputed tracks). The manuscript does not clarify whether the superior performance of ChromBERT holds across all tested cell types and regulators, or if it is driven by a specific subset. The baseline method, which uses "regulator-specific candidate peaks" and DNase-seq, is a reasonable but simple approach. A more thorough comparison, including a breakdown of performance by regulator class (e.g., transcription factors vs. chromatin modifiers) and cell-type category, is needed to substantiate the general claim of superiority.
    - **Why it matters** The central practical utility of ChromBERT is its ability to impute missing data. If the performance advantage is not robust across diverse scenarios, the model's practical value is diminished. A clear, detailed, and fair benchmark is essential to establish this core claim.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Interpretability / Causal inference
    - **Claim pointer** The claim that the interpretability framework can "infer regulatory roles of transcription regulators underlying these cell-type-specific regulatory outcomes" and identify "key regulators" driving cell-state transitions.
    - **Evidence pointer** Figure 3F, 4B, 4D; STAR Methods "Interpretation analysis for fine-tuned regulator embeddings"
    - **Concern** The core interpretability claim rests on the assumption that a shift in a regulator's embedding between two groups of regions (e.g., causal vs. non-causal eQTLs, or regions with increased vs. unchanged activity) indicates a causal role for that regulator. While plausible, this is a correlational measure. The manuscript does not provide a direct validation of this assumption. For example, in the eQTL fine-mapping task, the identified regulators are compared to known biology, but there is no systematic assessment of how many of the top-ranked regulators are known to be causal in the relevant tissues. Similarly, in the cell-state transition analysis, the recovery of known regulators is encouraging, but the false discovery rate is not estimated. The analysis of EP300 perturbation (Figure 3F) is a step in the right direction, but it is a single case study. A more rigorous validation, perhaps using perturbation data for multiple regulators or comparing against a gold-standard set of regulator-target interactions, is needed to support the claim that the embedding shifts provide causal insights.
    - **Why it matters** The interpretability framework is a major selling point of the manuscript. If the identified regulators are not genuinely causal, the method could generate misleading hypotheses and erode trust in the model's biological insights.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness / Ablation studies
    - **Claim pointer** The implicit claim that the specific design choices (e.g., 1-kb bins, 8-layer transformer, masked pre-training strategy, focal loss) are optimal or necessary for the model's performance.
    - **Evidence pointer** STAR Methods "Architecture and pre-training of ChromBERT"
    - **Concern** The manuscript does not include any ablation studies. It is unclear how sensitive the results are to key hyperparameters and design choices. For example, what is the impact of the bin size (1-kb vs. 200-bp vs. 4-kb)? How does the number of transformer layers affect performance? Is the masked pre-training strategy with focal loss crucial, or would a simpler approach work as well? The authors mention that models were pre-trained at different resolutions, but no comparison of their performance is shown. Without these analyses, it is difficult to assess whether the model's success is due to the core conceptual innovation or to specific, potentially arbitrary, engineering choices.
    - **Why it matters** Ablation studies are crucial for understanding the source of a model's predictive power. They provide insights into the underlying biology being learned and guide future improvements. Their absence weakens the technical contribution of the work.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness / Baseline comparisons
    - **Claim pointer** The claim that ChromBERT outperforms other methods in downstream tasks, specifically eQTL fine-mapping and enhancer activity prediction.
    - **Evidence pointer** Figure 3B, 3E, S7C
    - **Concern** The comparison to Enformer and DNABERT-2 is presented, but the details of the fine-tuning protocol for these models are sparse. The manuscript states they were "fine-tuned using the established method in the original studies with slight modification," but the specifics of these modifications are not provided. For a fair comparison, it is critical to know if the same training data, evaluation metrics, and cross-validation schemes were used. Furthermore, the choice of a random forest on top of Enformer embeddings is unusual and may not be the optimal way to use this model. A more standard fine-tuning approach for Enformer might yield different results. The lack of detail makes it difficult to assess the fairness of the comparison.
    - **Why it matters** The claim of superior performance is a key part of the paper's impact. If the baseline models are not given a fair chance, the comparison is not convincing.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity / Reproducibility
    - **Affected element** STAR Methods, "Fine-tuning with prompts for additional information incorporation"
    - **Evidence pointer** STAR Methods
    - **Issue** The description of the prompt engineering is somewhat vague. For example, how exactly are the DNase-seq or scGPT embeddings "concatenated" with the TRN embeddings? Are they projected to the same dimension first? What is the dimension of the final concatenated vector?
    - **Required correction** Provide a more detailed, step-by-step description of the prompt construction and integration, including all relevant dimensions and projection layers.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Statistical rigor
    - **Affected element** Figure 2F, 3B
    - **Evidence pointer** Figure legends
    - **Issue** The statistical significance of the performance differences between ChromBERT and the baselines is mentioned in the text (e.g., "statistical significance calculated by a two-sided Student's t test"), but the exact p-values or confidence intervals are not reported in the main text or figure legends.
    - **Required correction** Report the exact p-values or confidence intervals for the key performance comparisons in the figure legends or main text.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Clarity / Biological interpretation
    - **Affected element** Figure 3I
    - **Evidence pointer** Figure 3I
    - **Issue** The Circos plot in Figure 3I is visually complex. The criteria for defining the "classical" and "non-classical" groups are described in the legend, but it is difficult to discern the biological significance of the two groups from the figure alone.
    - **Required correction** Consider simplifying the figure or adding a more detailed explanation in the legend about the biological implications of the two groups and the significance of the highlighted regulators.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** STAR Methods, "Benchmark with enformer and DNABERT-2"
    - **Evidence pointer** STAR Methods
    - **Issue** The manuscript mentions that "the runtime comparisons between ChromBERT and DNABERT-2 were provided in Table S4." However, the runtime for Enformer is not mentioned.
    - **Required correction** Include runtime comparisons for all models, or state why Enformer was excluded.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: The benchmark for cistrome imputation needs to be more comprehensive and clearly described to substantiate the claim of superior performance.
    - R1-M2: The interpretability framework requires validation against causal gold standards to support the claim that it identifies causal regulators.
    - R1-M3: The lack of ablation studies prevents a full understanding of the model's key components and their contribution to performance.

## Assessment against Nature-style criteria
- **Originality**: High. The conceptual approach of modeling ChIP-seq binding profiles as a language and using BERT-style pre-training to learn TRN syntax is a novel and creative contribution, distinct from sequence-based foundation models.
- **Scientific importance**: High. The model addresses a critical bottleneck in regulatory genomics: the sparsity of cell-type-specific transcription factor binding data. The ability to impute these data and identify key regulators has broad implications for understanding gene regulation in development and disease.
- **Interdisciplinary readership**: Medium-High. The work is primarily of interest to computational biologists and bioinformaticians. However, the clear biological applications and the potential for hypothesis generation will likely attract interest from experimental biologists studying transcriptional regulation.
- **Technical soundness**: Medium. The core methodology is sound, but the lack of ablation studies and the incomplete details of the benchmark comparisons prevent a full assessment of the model's robustness and the fairness of the comparisons.
- **Readability for nonspecialists**: Medium. The manuscript is well-written, but the technical details of the model architecture and the interpretability framework may be challenging for readers without a strong computational background. The figures are helpful, but some, like the Circos plot, are complex.

## Risk / unsupported claims
- The claim that ChromBERT "significantly enhances our ability to model and interpret transcriptional regulation across a wide range of biological contexts" is a broad statement that is not fully supported by the presented evidence, which focuses on a limited set of tasks and cell types.
- The claim that the interpretability framework can "infer regulatory roles" and identify "key regulators" is presented as a causal inference, but the analysis is based on correlational embedding shifts. This causal link is not directly validated.
- The statement that ChromBERT "outperforms existing methods" is based on comparisons to a limited set of baselines (Avocado, Enformer, DNABERT-2) under conditions that are not fully detailed, making the generalizability of this claim uncertain.
- The claim that the model can be "readily adapted to more diverse biological contexts through tailored prompt engineering" is a forward-looking statement that is not demonstrated in the current manuscript.