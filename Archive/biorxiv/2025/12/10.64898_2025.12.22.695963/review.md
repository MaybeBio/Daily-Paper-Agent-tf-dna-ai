## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Methods, Supplementary notes) as provided.
- **Assessment boundary** Scientific and technical soundness of the claims as presented in the provided text. Experimental validation results are described but primary data (figures, tables) are not fully available for independent verification.
- **Shared manuscript claim summary** The authors present Nucleotide Transformer v3 (NTv3), a multi-species genomic foundation model with a U-Net architecture that performs joint sequence-function modeling at up to 1 Mb context with single-base resolution. They claim state-of-the-art performance on functional track prediction and genome annotation across species, demonstrate a shared regulatory grammar, and show controllable sequence generation validated experimentally.
- **Visible evidence base** Text descriptions of results, benchmark methodology, model architecture, and experimental validation. Specific numerical results are cited in text but figures and tables are not fully accessible in the provided material.
- **Missing materials affecting confidence** Full figures, tables, and supplementary data files. Detailed benchmark results per task, statistical significance values, and complete experimental validation data for the 1,000 generated enhancers.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and ambitious effort to unify multiple paradigms in genomic deep learning within a single model. The technical achievements are impressive, particularly the scale of pre-training data, the architectural innovations for long-context modeling, and the integration of multiple output heads. The experimental validation of generated enhancers is a notable strength. However, the manuscript's central claims of "state-of-the-art" performance and "foundational" status require more rigorous and comprehensive evidence than is currently presented. The comparison to baselines, particularly for the benchmark, needs more detail on statistical significance and effect sizes. The claim of a "shared regulatory grammar" is intriguing but requires more direct evidence. The experimental validation, while valuable, is limited in scope and would benefit from additional replicates and controls.
- **Who would be interested in the results, and why** Researchers in computational genomics, particularly those working on regulatory genomics, variant effect prediction, and genome annotation. The model's ability to handle multi-species data and long-range context would be of interest to those studying gene regulation across evolutionary scales. The generative capabilities would appeal to synthetic biology and genome engineering communities. The practical "cookbooks" and open-source release lower the barrier for adoption, making this a potentially high-impact resource for the broader genomics community.
- **Major strengths**
  1. The unification of representation learning, supervised prediction, and generative modeling in a single architecture is a significant conceptual advance.
  2. The scale of pre-training (9 trillion base pairs, 128,000 species) is unprecedented and likely contributes to the model's strong performance.
  3. The U-Net architecture with single-base tokenization and 1 Mb context is a clever engineering solution to a major computational challenge.
  4. The experimental validation of 1,000 generated enhancers is a rigorous and commendable step beyond purely in silico evaluation.
  5. The release of code, models, and practical guides is a strong commitment to reproducibility and community adoption.
- **Major Concerns**
  - **R1-M1** (Severity: Major, Blocking: Yes, Axis: Technical soundness)
    - **Claim pointer** The claim that NTv3 achieves "state-of-the-art accuracy for functional-track prediction and genome annotation across species" is central to the paper's significance.
    - **Evidence pointer** Section 2.3, Figure 3D-F, Supplementary Figure A.10
    - **Concern** The comparison to baselines, particularly Borzoi, is presented as a summary of relative performance. However, the text does not provide sufficient detail on the statistical significance of the observed differences. Are the improvements consistent across all tracks and species, or are they driven by a few specific assays? The text mentions "up to 3%" improvement for some assays but a "minor reduction" for RNA-seq. This heterogeneity needs to be quantified and discussed. A simple mean or median across tracks may mask important variability.
    - **Why it matters** The claim of state-of-the-art performance is a key justification for the model's utility. If the improvements are not statistically robust or are inconsistent, the claim is weakened. The reader needs to understand the distribution of performance differences, not just the average, to assess the model's true value.
    - **Resolution test** Provide a detailed breakdown of performance per track and per species, with confidence intervals or statistical tests (e.g., paired tests across chromosomes or genomic bins). Show the distribution of performance differences, not just the mean. Discuss the implications of the RNA-seq result.
  - **R1-M2** (Severity: Major, Blocking: Yes, Axis: Technical soundness)
    - **Claim pointer** The claim that NTv3 "consolidates a shared regulatory grammar across tasks" is a strong and interesting assertion.
    - **Evidence pointer** Section 2.7, Figure 6
    - **Concern** The evidence for a "shared regulatory grammar" is based on the model's ability to predict multiple tracks and interpret variants. However, the text does not provide a direct test of whether the model's internal representations are actually shared across tasks. For example, does the model use the same features to predict DNase and CAGE, or does it learn separate task-specific features? The attention maps and attribution analyses are suggestive but not conclusive. A more direct test would involve probing the model's representations, e.g., by ablating specific features and observing the effect on multiple tasks, or by analyzing the similarity of attribution maps across tasks.
    - **Why it matters** The claim of a "shared grammar" implies that the model has learned fundamental principles of gene regulation that are not task-specific. This is a more profound claim than simply "the model is good at predicting multiple tracks." If the model is merely learning task-specific features, the claim of a unified regulatory grammar is overstated.
    - **Resolution test** Perform analyses that directly test for shared representations. For example, train the model on one task and evaluate its zero-shot performance on another. Or, analyze the correlation between attribution maps for different tasks. Alternatively, use a probing classifier to test if the same internal features are predictive of multiple tasks.
  - **R1-M3** (Severity: Major, Blocking: Yes, Axis: Technical soundness)
    - **Claim pointer** The claim that NTv3 can be used for "controllable sequence generation" and that the generated enhancers "recapitulate the intended activity stratification and achieve the desired promoter-specific activation in cellulo."
    - **Evidence pointer** Section 2.8, Figure 7
    - **Concern** The experimental validation of 1,000 enhancers is a major strength. However, the text does not provide sufficient detail on the experimental design. How many biological replicates were performed? What were the controls? The text mentions "in cellulo" validation but does not specify the cell type or the number of independent experiments. The comparison to "DeepSTARR-selected" sequences is interesting, but the text does not state whether the NTv3-generated sequences were also selected based on DeepSTARR predictions, which would be a more direct comparison. The text also does not report the success rate of the generation process (i.e., what fraction of generated sequences met the desired criteria).
    - **Why it matters** The experimental validation is the strongest evidence for the model's practical utility. Without detailed experimental methodology, the results are difficult to interpret and reproduce. The reader needs to know the robustness of the effect and the potential for batch effects or other artifacts.
    - **Resolution test** Provide a detailed experimental methods section, including cell lines, culture conditions, number of replicates, and statistical analysis. Report the success rate of generation and the distribution of activities for generated vs. control sequences. If possible, include a comparison to a random sequence control.
  - **R1-M4** (Severity: Major, Blocking: No, Axis: Scientific importance)
    - **Claim pointer** The claim that NTv3 is a "foundational model" that can be "efficiently fine-tuned towards various downstream applications."
    - **Evidence pointer** Section 2.5, Figure 4
    - **Concern** The benchmark is a valuable contribution, but the text does not provide a clear comparison to the cost of fine-tuning NTv3 versus training a model from scratch. The claim of efficiency is relative. The authors show that NTv3 outperforms baselines, but they do not show the computational cost of achieving this performance. If fine-tuning NTv3 requires more compute than training a smaller model from scratch, the practical advantage is less clear.
    - **Why it matters** The "foundational" claim implies that the model provides a cost-effective starting point for downstream tasks. If the fine-tuning cost is prohibitive, the model's utility is limited to those with access to substantial computational resources.
    - **Resolution test** Provide a detailed analysis of the computational cost of fine-tuning NTv3 for each benchmark task, including GPU hours and memory requirements. Compare this to the cost of training the baseline models from scratch. Discuss the trade-offs between performance and cost.
- **Minor Comments**
  - **R1-m1** (Severity: Minor, Axis: Readability for nonspecialists)
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract, Section 1
    - **Issue** The abstract and introduction are dense with jargon and assume a high level of familiarity with both deep learning and genomics. Terms like "U-Net-like architecture," "masked language modeling," and "conditional generative models" are used without sufficient explanation for a general scientific audience.
    - **Required correction** Provide brief, accessible explanations of these key concepts in the introduction. For example, a sentence explaining that "masked language modeling" is a self-supervised learning technique where the model learns to predict missing parts of the input, analogous to filling in blanks in a sentence.
  - **R1-m2** (Severity: Minor, Axis: Technical soundness)
    - **Affected element** Section 2.2, Figure 3
    - **Evidence pointer** Section 2.2, Figure 3
    - **Issue** The text states that post-training improves performance, but it does not clearly separate the effects of continued pre-training (MLM) from the supervised fine-tuning on functional tracks. Is the improvement due to the additional data, the new task heads, or both?
    - **Required correction** Include an ablation study where the model is post-trained with only the MLM objective (no supervised heads) and compared to the full post-trained model. This would isolate the contribution of the supervised component.
  - **R1-m3** (Severity: Minor, Axis: Technical soundness)
    - **Affected element** Section 4.3, Methods
    - **Evidence pointer** Section 4.3
    - **Concern** The description of the post-training loss function is incomplete. The text mentions a "three part loss function" but only describes the Poisson and multinomial terms. The third term is not specified.
    - **Required correction** Clearly state the three components of the loss function and their relative weights.
  - **R1-m4** (Severity: Minor, Axis: Interdisciplinary readership)
    - **Affected element** Section 2.7, Figure 6
    - **Evidence pointer** Section 2.7
    - **Issue** The variant effect prediction analysis is described in detail, but the connection to the broader theme of "shared regulatory grammar" is not fully articulated. The authors should more explicitly link the variant analysis to the claim of a unified model.
    - **Required correction** Add a sentence or two explaining how the variant analysis demonstrates the model's ability to integrate information across scales and tasks, supporting the "shared grammar" claim.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of statistical rigor in benchmark comparisons.
  - R1-M2: Insufficient evidence for the "shared regulatory grammar" claim.
  - R1-M3: Incomplete experimental methodology for enhancer validation.
- **Assessment against Nature-style criteria**
  - **Originality** High. The unification of representation learning, supervised prediction, and generation in a single model is a novel contribution. The U-Net architecture for genomic foundation models is a creative adaptation of existing ideas.
  - **Scientific importance** High. If the claims are substantiated, this model could serve as a powerful resource for the genomics community, enabling more accurate predictions and more efficient fine-tuning for a wide range of tasks.
  - **Interdisciplinary readership** Moderate. The work is primarily of interest to computational biologists and machine learning researchers. The experimental validation may attract a broader biological audience, but the technical complexity of the model may limit its accessibility.
  - **Technical soundness** Moderate. The technical approach is sound, but the evidence for the central claims is incomplete. The lack of statistical rigor in the benchmark and the insufficient evidence for the "shared regulatory grammar" are significant concerns.
  - **Readability for nonspecialists** Low. The manuscript is written for a specialist audience and would be challenging for a general scientific reader to follow.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially important contribution, but the central claims are not fully established from the provided evidence. The authors should address the concerns regarding statistical rigor, the "shared regulatory grammar" claim, and the experimental methodology before the case is fully made.

## Risk / unsupported claims
- The claim of "state-of-the-art" performance is not fully supported due to lack of statistical significance testing and potential heterogeneity across tasks.
- The claim of a "shared regulatory grammar" is not directly tested and is an interpretation of indirect evidence.
- The claim of "controllable" generation is supported by experimental data, but the robustness and generalizability of this result are not fully established.
- The claim that NTv3 is a "foundational model" that is "efficiently fine-tuned" is not supported by a cost-benefit analysis.
- The claim that NTv3 is the "largest trained genomics model to date" is based on token count, but the comparison to other models in terms of parameters and architecture is not clear.