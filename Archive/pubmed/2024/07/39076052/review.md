## Review setup
- **Input scope** Full manuscript text, including abstract, results, discussion, and experimental methods. Figures and supplementary materials are referenced but not provided.
- **Assessment boundary** Evaluation is limited to the claims, methods, and results as described in the supplied text. No independent verification of data, code, or supplementary figures was possible.
- **Shared manuscript claim summary** The authors propose a nucleotide-level deep neural network (NLDNN) for transcription factor binding prediction, a dual-path adversarial training framework (NLDNN-AT) for cross-species prediction, and a method to directly compare sequence-level and nucleotide-level models using maximum coverage values.
- **Visible evidence base** Text descriptions of results, including performance comparisons, correlation values, and qualitative statements. References to figures (Figure 1-6) and supplementary figures/tables, none of which were available for inspection.
- **Missing materials affecting confidence** All figures, supplementary figures, tables, and detailed numerical results. The manuscript states "The data that support the findings of this study are available in the supplementary material of this article," but this material was not provided. This significantly limits the ability to assess the validity of the reported results.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational genomics, namely the cross-species prediction of transcription factor binding, and proposes a novel architecture with an adversarial training component. The idea of using maximum coverage values as a bridge to compare sequence-level and nucleotide-level models is interesting and potentially useful. However, the manuscript as presented has several major weaknesses. The most critical issue is the lack of access to the actual results, figures, and supplementary data, making it impossible to verify the reported performance. Even based on the text alone, there are concerns about the clarity of the experimental setup, the statistical rigor of the comparisons, and the generalizability of the claims. The discussion of limitations is superficial, and the comparison with state-of-the-art methods, particularly transformer-based models, is presented in a way that undermines the proposed method's novelty. The writing is often unclear and would benefit from significant revision.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, specifically those developing and applying deep learning methods for transcription factor binding prediction, variant effect prediction, and cross-species analysis. The proposed NLDNN architecture and the adversarial training framework could be of interest to researchers seeking to improve cross-species model performance. The method for comparing sequence-level and nucleotide-level models may also be of methodological interest.
- **Major strengths**
    1.  The problem of cross-species TF binding prediction is important and challenging, and the manuscript addresses a clear gap in direct training of cross-species models.
    2.  The proposed NLDNN architecture, with its U-Net-like design and use of a bidirectional GRU and SPPM, is a reasonable and potentially effective approach for nucleotide-level prediction.
    3.  The idea of using maximum coverage values as a bridge for comparing sequence-level and nucleotide-level models is a practical and potentially valuable contribution.
    4.  The dual-path adversarial training framework is a sensible adaptation of GAN principles to the domain adaptation problem in genomics.
    5.  The evaluation considers multiple criteria (prediction, variant effects, localization), which is a more comprehensive approach than simply reporting a single performance metric.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence and reproducibility
    - **Claim pointer** The manuscript claims that NLDNN outperforms competing methods in multiple prediction tasks, and that adversarial training improves cross-species prediction performance.
    - **Evidence pointer** Figures 2, 5, 6; Figure S1, S2, S10, S13; location not provided for specific data points.
    - **Concern** The core findings of the paper are presented in figures and supplementary materials that were not provided for review. The text provides only qualitative summaries (e.g., "NLDNN performs best," "NLDNN-AT outperforms") without specific numerical values, error bars, or statistical significance tests. It is impossible to assess the magnitude of the reported improvements, the variability of the results, or whether the differences are meaningful. The claim that "adversarial training can improve the overall performance" is a central conclusion, but the evidence for it cannot be evaluated.
    - **Why it matters** A scientific claim must be supported by verifiable evidence. Without access to the actual results, the validity of the manuscript's central claims cannot be established. This is a fundamental requirement for publication.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness and methodology
    - **Claim pointer** The manuscript proposes a method to directly compare sequence-level and nucleotide-level models using the maximums of coverage values.
    - **Evidence pointer** Section "Classification Versus Regression Models"; Figure 2a; Section "Maximums of Coverage Values".
    - **Concern** The proposed comparison method is not clearly validated. The authors state that the maximum coverage value is closely related to binding strength (correlation 0.9 for human, 0.818 for mouse), but this is a correlation with the number of reads in a peak, not necessarily with the functional "strength" of binding. More importantly, the method for comparing models is not fully described. For sequence-level regression models, the "maximums of coverage values" are used as labels. For nucleotide-level models, the maximum of the predicted coverage vector is used. This is a specific and potentially arbitrary choice. The manuscript does not discuss alternative ways to derive a scalar summary from nucleotide-level predictions (e.g., mean, sum) and why the maximum is the most appropriate. The comparison could be biased by this choice.
    - **Why it matters** The proposed comparison method is a key contribution of the paper. If the method is not robust or is biased, the conclusions drawn from the comparisons (e.g., that NLDNN is superior) may be invalid.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific importance and context
    - **Claim pointer** The manuscript states that "transformer-based models could provide enhanced predictive capacities" and that a combination of transformer, long-range sequence, and multi-task learning is the trend for TF binding prediction.
    - **Evidence pointer** Discussion section, last paragraph.
    - **Concern** The manuscript's own discussion significantly weakens the case for the novelty and importance of the proposed NLDNN-AT. It states that a standard transformer-based model (Enformer) "significantly outperforms" NLDNN. This admission, while honest, raises the question of what the specific contribution of the proposed adversarial training framework is, given that a more powerful, existing architecture is available. The authors suggest that the dual-path framework can be transferred to other architectures, but this is speculative and not demonstrated. The manuscript does not provide a clear argument for why the proposed method is a meaningful advance over simply using a transformer model.
    - **Why it matters** For a paper to be significant, it must offer a clear advance over the state of the art. If the proposed method is outperformed by an existing method, the authors need to make a much stronger case for the value of their specific contribution, such as showing that the adversarial training framework can be successfully applied to transformer-based models to achieve even better performance.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness and methodology
    - **Claim pointer** The manuscript claims that the dual-path adversarial training framework improves cross-species prediction by "pulling the domain space of human and mouse species closer."
    - **Evidence pointer** Section "Adversarial Training Can Improve the Performance of Cross-Species TF Binding Prediction"; Figure 6.
    - **Concern** The mechanism of the adversarial training is not clearly explained. The manuscript describes a GAN-like setup with a generator, predictor, and discriminator, but the training procedure is described in a high-level manner. The exact loss functions, the training schedule (e.g., how often the discriminator is updated relative to the generator), and the convergence criteria are not fully specified. The claim that the method "pulls the domain space closer" is a qualitative statement that is not supported by any quantitative analysis of the learned feature spaces (e.g., t-SNE plots, MMD distance). The manuscript does not show that the adversarial training actually results in a more aligned feature distribution.
    - **Why it matters** A clear and detailed description of the method is essential for reproducibility. Without a full understanding of the training dynamics, it is difficult to assess why the method works or to apply it to other problems. The lack of evidence for the proposed mechanism makes the explanation for the improved performance speculative.

    - **Concern ID** R1-M5
    - **Severity** Major
    - **Blocking** No
    - **Axis** Readability and clarity
    - **Claim pointer** The manuscript describes the NLDNN architecture and the adversarial training framework.
    - **Evidence pointer** Section "Models—NLDNN", "Models—Encoder Architecture", "Models—Decoder Architecture", "Models—Connection Architecture", "The Framework of Adversarial Training".
    - **Concern** The description of the model architecture is difficult to follow. The text refers to "a symmetrical 'U' shape architecture" and mentions components like "SPPM" and "RRB" but does not provide a clear, self-contained description of these components or how they are connected. The description of the adversarial training framework is also confusing, particularly the roles of the "source generator" and "target generator" and how they interact with the predictor and discriminator. The text would benefit greatly from a more formal and precise description, possibly with equations and a clear data flow diagram.
    - **Why it matters** A paper describing a new method must be clear enough for a knowledgeable reader to understand and potentially reproduce the method. The current description is too vague and relies heavily on the (unavailable) figures.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and precision
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract, first sentence.
    - **Issue** The phrase "rapid evolutionary turnover of individual TF binding sites" is used without a precise definition. It is unclear if this refers to the gain/loss of sites, sequence divergence within sites, or something else.
    - **Required correction** Define the term "evolutionary turnover" in the context of TF binding sites, perhaps with a brief explanation or a reference.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Statistical rigor
    - **Affected element** Results, "Predictive Performance"
    - **Evidence pointer** Figure 2c; Figure S2.
    - **Issue** The manuscript reports performance improvements but does not mention any statistical significance testing (e.g., paired t-test, Wilcoxon signed-rank test) across the 18 datasets.
    - **Required correction** Add statistical tests to support the claim that NLDNN is significantly better than the competing methods.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Results, "Variant Effect Prediction"
    - **Evidence pointer** Section "Variant Effect Prediction—TF-Specific SNPs".
    - **Issue** The manuscript mentions "filtered or non-filtered TF-specific SNPs" but does not explain what "filtered" means in this context.
    - **Required correction** Clarify the filtering criteria for the TF-specific SNPs.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Discussion
    - **Evidence pointer** Discussion, first paragraph.
    - **Issue** The statement "improved predictions may not necessarily lead to learning better motifs" is interesting but is not discussed in sufficient depth. The authors should elaborate on why this might be the case and what the implications are for model evaluation.
    - **Required correction** Expand the discussion on the relationship between predictive performance and motif discovery.

    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Experimental Section, "Data Processing"
    - **Evidence pointer** Section "Data Processing".
    - **Issue** The manuscript states that "p-value tracks were better suitable for the proposed method than fold change over control tracks" but does not provide the data or analysis supporting this choice.
    - **Required correction** Provide a brief justification or reference for this choice, or show a comparison in the supplementary material.

- **Technical failings that need to be addressed before the case is established**
    1.  **Lack of access to results (R1-M1):** The central claims of the paper cannot be verified without the figures and supplementary data. This is a blocking issue.
    2.  **Unvalidated comparison method (R1-M2):** The proposed method for comparing sequence-level and nucleotide-level models needs to be more rigorously justified and validated.
    3.  **Unclear mechanism of adversarial training (R1-M4):** The description of the adversarial training process is too vague to be reproducible or to fully understand the proposed mechanism of improvement.

## Risk / unsupported claims
- The claim that "NLDNN outperforms the competing methods" is unsupported without access to the actual results and statistical analysis.
- The claim that "adversarial training can improve the overall performance of cross-species TF binding prediction" is unsupported without access to the actual results and statistical analysis.
- The claim that "the framework corrects some mispredictions by amplifying the coverage values of incorrectly predicted peaks" is a qualitative observation that is not supported by quantitative data.
- The claim that "transformer-based models could provide enhanced predictive capacities" is presented as a conclusion but is based on a single comparison with Enformer, which is not the focus of the paper.
- The claim that the dual-path framework "can easily be transferred to other architectures" is speculative and not demonstrated.
- The claim that "the maximums of coverage values are closely related to the binding strength" is based on a correlation with read counts, which is an indirect measure of binding strength.