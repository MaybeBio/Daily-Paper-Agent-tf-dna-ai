## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided on bioRxiv.
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided text. Assessment is limited to the information available in the manuscript; no external data or code was accessed.
- **Shared manuscript claim summary** The authors present PlantCAD2, a DNA foundation model pre-trained on 65 angiosperm genomes with an 8,192 bp context window. They claim it efficiently captures evolutionary conservation, outperforms larger generalist models (e.g., Evo2) on plant-specific zero-shot tasks, and, when fine-tuned, achieves state-of-the-art cross-species predictions for chromatin accessibility, gene expression, and translation.
- **Visible evidence base** Main text figures (Figure 1-6), supplementary figures (Figure S1-S16), and supplementary tables (Table S1-S11) are referenced. The manuscript includes detailed methods for model architecture, pre-training, and downstream task evaluation.
- **Missing materials affecting confidence** The manuscript text was provided without the actual figures, tables, and supplementary data files. Consequently, the numerical results, statistical significance tests, and detailed benchmark comparisons referenced in the text could not be independently verified. Code and model weights are available online but were not accessed for this review.

## Reviewer
- **Overall assessment** This manuscript describes a timely and potentially valuable resource for the plant genomics community. The core idea of a plant-specific, long-context DNA language model is well-motivated, and the authors present a comprehensive evaluation across multiple tasks. The claims of efficiency and strong zero-shot performance are intriguing. However, the current manuscript, as presented, has several technical ambiguities and a lack of accessible evidence in the provided text that prevent a full assessment of its central claims. The comparison with Evo2, while compelling, requires more careful analysis of the evaluation protocols to rule out potential biases. The work is a solid incremental advance over the authors' previous PlantCAD model, but its novelty relative to other recent plant DNA LMs needs to be more clearly articulated.
- **Who would be interested in the results, and why** This work will be of high interest to plant geneticists, crop scientists, and computational biologists working on genome annotation, regulatory genomics, and evolutionary biology. The model's ability to predict functional elements and conservation across diverse angiosperm species, including those without extensive experimental data, could be a powerful tool for prioritizing variants and understanding gene regulation. The efficiency gains over much larger models also make it practically appealing for labs with limited computational resources.
- **Major strengths**
    1.  **Well-motivated problem and design:** The focus on a plant-specific model with a long context window (8kb) directly addresses a known limitation of shorter-context models and the potential dilution of signal in generalist models.
    2.  **Comprehensive evaluation:** The authors evaluate the model on a wide range of tasks, from zero-shot conservation prediction to fine-tuned predictions of chromatin accessibility, gene expression, and translation. This provides a holistic view of the model's capabilities.
    3.  **Strong empirical results (as described):** The reported performance improvements over Evo2 and AgroNT, particularly with a much smaller model, are significant and suggest that domain-specific pre-training is highly effective.
    4.  **Practical considerations:** The analysis of model size, inference speed, and memory usage is valuable and demonstrates a clear path for adoption by the community.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** The claim that PlantCAD2's zero-shot conservation predictions are superior to Evo2's, and that its fine-tuned models outperform baselines across all tasks.
    - **Evidence pointer** Figures 2, 5, 6; Supplemental Tables 2, 5, 8, 10
    - **Concern** The manuscript text does not provide sufficient detail on the statistical significance of the reported performance differences. For example, in Figure 2B, the AUROC difference between PlantCAD2-L and Evo2 is mentioned, but it is unclear if this is a statistically significant improvement. Similarly, for the fine-tuning tasks, are the differences in AUPRC or correlation coefficients significant across multiple runs or seeds? The text mentions "five random seeds" for one experiment (Supplemental Table 9), but this is not applied to all key comparisons.
    - **Why it matters** Without measures of variance and statistical testing, it is impossible to determine if the observed improvements are robust or simply due to noise, especially given the large number of tasks and models being compared. This is critical for establishing the reliability of the model's claimed superiority.
    - **Resolution test** Provide confidence intervals or standard deviations for all key metrics and perform appropriate statistical tests (e.g., paired tests, bootstrap) to demonstrate that the performance gaps are significant.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** The claim that the "multi-species" fine-tuned model for chromatin accessibility is more robust and generalizable.
    - **Evidence pointer** Figure 5C; Supplemental Table 6
    - **Concern** The description of the multi-species fine-tuning experiment is incomplete. The text states it was fine-tuned on "accessible chromatin regions from multiple plant genomes" but does not specify which species were used for training and which were held out (beyond maize and barley). It is also unclear if the held-out species (maize, barley) were completely excluded from the pre-training data. If they were included in pre-training, the evaluation is not truly "zero-shot" for those species, and the performance could be inflated.
    - **Why it matters** The generalizability of the model to unseen species is a key selling point. If the evaluation protocol is not clean, the claim of cross-species robustness is weakened.
    - **Resolution test** Clearly state the species used for multi-species fine-tuning and the species used for testing. Explicitly confirm whether the test species were excluded from the pre-training dataset. If not, the claims should be tempered.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Originality
    - **Claim pointer** The implicit claim that PlantCAD2 represents a significant conceptual advance over existing models.
    - **Evidence pointer** Introduction, Discussion
    - **Concern** The novelty of PlantCAD2 relative to the authors' previous PlantCAD model and other recent plant DNA LMs (e.g., AgroNT) is not clearly delineated. The primary architectural change is swapping Mamba1 for Mamba2 blocks and increasing the context length. While these are meaningful engineering improvements, the manuscript would be strengthened by a more explicit discussion of what fundamentally new scientific capabilities this model enables compared to its predecessor and other state-of-the-art models.
    - **Why it matters** For a high-impact journal, the conceptual advance needs to be clear. If the contribution is primarily incremental (better architecture, more data), the significance is diminished.
    - **Resolution test** Add a section in the Discussion that explicitly contrasts PlantCAD2's capabilities and performance with PlantCAD and AgroNT, highlighting the specific new biological insights or prediction tasks that are now possible.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical Soundness
    - **Claim pointer** The claim that the model's performance on masked motif prediction reflects an understanding of "functional" sites.
    - **Evidence pointer** Figure 3; Supplemental Table 3
    - **Concern** The zero-shot masked motif prediction task, while clever, may be biased by sequence composition. For example, the model might perform well on TIS prediction simply because the ATG motif is highly conserved in a specific sequence context (Kozak-like sequences) that is easy to learn, rather than because it understands the functional importance of the site. The comparison to Evo2, which is causal, is also potentially unfair given the different training objectives. The manuscript should discuss these potential biases.
    - **Why it matters** The interpretation of the results as evidence for "functional" understanding is a strong claim. If the task can be solved by learning local sequence statistics, the conclusion is less impactful.
    - **Resolution test** Include control experiments, such as predicting random motifs or shuffled motifs, to demonstrate the task is not trivially solvable. Also, discuss the inherent differences between masked and causal language model evaluation.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Readability for Nonspecialists
    - **Affected element** Abstract
    - **Evidence pointer** Abstract
    - **Issue** The abstract is dense and uses jargon (e.g., "reverse-complement equivariance") without explanation. The significance of the 8,192 bp context window is not immediately clear to a general reader.
    - **Required correction** Briefly explain the key concepts in plain language. For example, state that the model can "read" longer stretches of DNA, which is important for capturing distant regulatory elements.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** Methods, "Preparing pre-training genomes"
    - **Evidence pointer** Methods
    - **Issue** The method for selecting the 65 genomes is described, but the rationale for the final number is not given. Why 65? Was this a practical limit or a deliberate choice based on phylogenetic coverage?
    - **Required correction** Provide a brief justification for the number of genomes and the selection criteria, perhaps referencing a saturation analysis or a specific phylogenetic sampling strategy.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical Soundness
    - **Affected element** Results, "PlantCAD2 predicts functional structural variants"
    - **Evidence pointer** Figure 4
    - **Concern** The description of the simulated deletions is clear, but the choice of the Arabidopsis genome for this task is not justified. Would the results be similar in a larger, more complex genome like maize?
    - **Required correction** Add a sentence explaining the choice of Arabidopsis and discuss whether the findings are likely to generalize to other species.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Readability for Nonspecialists
    - **Affected element** Discussion
    - **Evidence pointer** Discussion
    - **Issue** The discussion of allele-specific effects is interesting but somewhat tangential and introduces a new topic (variant effect prediction) that was not a primary focus of the results.
    - **Required correction** Consider streamlining this section to focus on the main findings and their implications, or move the detailed discussion of allele-specific modeling to a separate section.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1 (Lack of statistical significance testing) is a blocking concern. The core claims of superiority need to be backed by rigorous statistical analysis.
    - R1-M2 (Ambiguity in multi-species fine-tuning protocol) is a blocking concern. The evaluation protocol must be clearly defined to validate the generalizability claims.

## Risk / unsupported claims
- The claim that PlantCAD2 "efficiently captures evolutionary conservation" is supported by the described results but requires the statistical analysis from R1-M1 to be fully validated.
- The claim that the model is a "versatile foundation model" is supported by the range of tasks, but the performance on gene expression and translation tasks is mixed (e.g., cross-species translation regression was less effective), which is acknowledged but should be more prominently featured in the abstract.
- The claim that the model's performance on masked motif prediction reflects an understanding of "functional" sites is not fully supported and could be an artifact of sequence composition (R1-M4).
- The performance comparison with Evo2, while favorable, is based on a potentially unfair evaluation protocol (zero-shot vs. causal) and needs more careful discussion.