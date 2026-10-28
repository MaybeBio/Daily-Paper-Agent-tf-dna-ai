## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2022-12-20)
- **Assessment boundary** Scientific content, methodology, data interpretation, and internal consistency of the provided manuscript text. No external data or code were accessed.
- **Shared manuscript claim summary** The authors propose that chromatin accessibility during Drosophila zygotic genome activation is a two-tier process: pioneering by Zelda (and GAF) opens chromatin in a motif-affinity-dependent manner, while patterning transcription factors (Dorsal, Twist, Bicoid, Caudal) further increase accessibility only in contexts where they mediate enhancer activation. This is supported by deep learning models (BPNet, ChromBPNet) trained on new ChIP-nexus and ATAC-seq data, validated by in silico mutagenesis, motif injection, and genetic perturbations (zld-, gd7, cic6 mutants).
- **Visible evidence base** Main text figures (Figures 1-5), supplementary figures (1-14), methods section, supplemental file descriptions. No raw data, code, or supplementary files were available for direct inspection.
- **Missing materials affecting confidence** Supplementary figures and files (including detailed model performance metrics, motif island lists, and differential accessibility tables) were not provided. The manuscript states that trained models will be available only after review. This limits independent verification of several quantitative claims.

## Reviewer
- **Overall assessment** This is a technically sophisticated and conceptually important study that addresses a fundamental question in gene regulation: how to distinguish pioneer transcription factors from non-pioneer factors using sequence-based deep learning. The combination of high-resolution ChIP-nexus, ATAC-seq time courses, interpretable deep learning, and Drosophila genetics is powerful and appropriate. The central claim, that pioneering and enhancer activation are separable processes with distinct effects on chromatin accessibility, is well-supported by the presented data. However, several aspects of the analysis, particularly the interpretation of the ChromBPNet contribution scores and the generalizability of the two-tier model, require further clarification and validation. The manuscript is well-written and will be of broad interest, but the current evidence base is not fully sufficient to establish all claims without access to the supplementary materials and model details.
- **Who would be interested in the results, and why** This work will be of high interest to researchers in gene regulation, chromatin biology, developmental biology, and computational biology. Specifically, those studying pioneer factors, enhancer function, and the application of deep learning to genomics will find the methodological framework and the proposed two-tier model directly relevant. The study also provides a valuable resource of high-resolution TF binding and chromatin accessibility data in the early Drosophila embryo.
- **Major strengths**
    1.  The study addresses a long-standing problem (distinguishing pioneer from non-pioneer TFs) with a novel and rigorous computational approach.
    2.  The integration of multiple data types (ChIP-nexus, ATAC-seq, MNase-seq, ChIP-seq) and orthogonal validation (in silico, in vivo genetics) is exemplary.
    3.  The use of interpretable deep learning (BPNet/ChromBPNet) to extract base-resolution rules is state-of-the-art and provides mechanistic insight.
    4.  The genetic experiments (zld-, gd7, cic6) elegantly dissect the distinct contributions of pioneering and activation to accessibility.
    5.  The manuscript is clearly written and the figures are informative.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical soundness / Interpretation
        - **Claim pointer** The claim that "patterning TFs augment chromatin accessibility in sequence contexts in which they mediate enhancer activation" is a central conclusion.
        - **Evidence pointer** Figure 2f, Figure 4b-d, Figure 5b-e, and related text.
        - **Concern** The evidence for this claim relies heavily on the interpretation of ChromBPNet contribution scores and the correlation between TF binding and accessibility contributions. The manuscript does not fully address whether the observed correlation for patterning TFs (e.g., Dorsal at late time points) is a direct effect of the TF on chromatin or an indirect consequence of the TF's role in recruiting co-activators that remodel chromatin. The distinction between "pioneering" and "activation-mediated" accessibility is inferred, but the causal link is not directly tested. The gd7 and cic6 experiments show that accessibility changes with TF activity, but they do not formally prove that the TF itself is the direct agent of chromatin opening versus a downstream consequence of transcription or co-factor recruitment.
        - **Why it matters** The central thesis of the paper rests on this distinction. If the increased accessibility at active enhancers is an indirect effect of transcription or other downstream processes, the "two-tier" model would be an oversimplification.
        - **Resolution test** The authors should provide a more direct test of causality. For example, a system where a patterning TF can be induced to bind without activating transcription (e.g., a dominant-negative or a TF with a mutated activation domain) could be used to see if accessibility still increases. Alternatively, a time-resolved analysis (e.g., with inducible TF nuclear entry) could show whether accessibility changes precede or follow transcriptional activation.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical soundness / Reproducibility
        - **Claim pointer** The claim that "low-affinity Zelda motifs can promote accessibility, but to a lesser extent than high-affinity motifs" is a key quantitative finding.
        - **Evidence pointer** Figure 3f-g, Supplemental figure 10d-e.
        - **Concern** The selection of the "250 highest and lowest affinity" motifs is a critical step. The manuscript does not provide sufficient detail on how these sets were defined and whether they are matched for other confounding factors, such as genomic context, nucleosome positioning, or the presence of other TF motifs. The analysis of "regions with a single high-affinity or low-affinity Zelda motif" is also potentially confounded by the presence of other, unmapped motifs. The manuscript states that regions with "no other mapped motif nearby" were selected, but the criteria for "nearby" and the completeness of the motif set are not fully described.
        - **Why it matters** The quantitative comparison between high- and low-affinity motifs is a cornerstone of the "affinity-proportional" pioneering model. If the comparison is confounded, the conclusion is weakened.
        - **Resolution test** The authors should provide a detailed description of the motif selection process, including the distribution of motif scores, the distance criteria for "no other motif," and a demonstration that the high- and low-affinity sets are matched for other relevant features. A permutation-based control, where motif identity is shuffled, would also strengthen the analysis.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Scientific importance / Generalizability
        - **Claim pointer** The claim that "chromatin accessibility is a two-tier process" is presented as a general model.
        - **Evidence pointer** Discussion section.
        - **Concern** The study is performed exclusively in the early Drosophila embryo, a system with a relatively simple chromatin landscape and a dominant pioneer factor (Zelda). The generalizability of the two-tier model to other developmental contexts or organisms, where multiple pioneer factors may act redundantly or where the chromatin environment is more complex, is not established. The authors acknowledge this in the discussion but do not provide a clear framework for how the model could be tested or refined in other systems.
        - **Why it matters** The title and framing of the paper suggest a universal principle. Overstating the generalizability could mislead the field.
        - **Resolution test** The authors should temper the general claim or provide a more explicit discussion of the conditions under which the two-tier model is expected to hold. They could also analyze publicly available data from other systems (e.g., mouse ES cells) to test if the model's predictions hold.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Clarity
        - **Affected element** Figure 1e
        - **Evidence pointer** Figure 1e
        - **Issue** The heatmap showing cross-contributions of motifs to TF binding is dense and difficult to interpret. The color scale and the specific values are not clearly defined.
        - **Required correction** Please provide a clearer figure legend, possibly with a more intuitive color scale and annotations for the key interactions (e.g., Zelda -> all TFs).
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Technical detail
        - **Affected element** Methods: ChromBPNet training
        - **Evidence pointer** Methods section "ChromBPNet model training and optimization"
        - **Issue** The description of the "frozen, pre-trained model" for Tn5 bias is somewhat unclear. It is not specified how this model is trained and whether it is the same for all time points.
        - **Required correction** Please clarify the training procedure for the Tn5 bias model and state whether a single model is used for all time points or if separate models are trained.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Data presentation
        - **Affected element** Figure 5b
        - **Evidence pointer** Figure 5b
        - **Issue** The volcano plot for differential accessibility in gd7 mutants is informative, but the labels for the enhancer categories (mesoderm, neuroectoderm, dorsal ectoderm) are not clearly visible.
        - **Required correction** Please ensure that the category labels are legible and that the color scheme is consistent with other figures.
    - **R1-m4**
        - **Severity** Minor
        - **Axis** Interpretation
        - **Affected element** Discussion of GAF
        - **Evidence pointer** Discussion section
        - **Issue** The role of GAF is somewhat ambiguous. The models predict it is a pioneer factor, but the experimental validation focuses on Zelda. The manuscript does not fully address why GAF's pioneering role is not tested genetically.
        - **Required correction** Please add a sentence or two explaining the rationale for focusing on Zelda and how GAF's role might be tested in future work.
    - **R1-m5**
        - **Severity** Minor
        - **Axis** Clarity
        - **Affected element** Abstract
        - **Evidence pointer** Abstract
        - **Issue** The phrase "two-tier process" is not defined in the abstract. It is clear from the main text, but a brief definition would improve accessibility.
        - **Required correction** Consider rephrasing to "a two-tier process, where pioneering by one class of TFs is followed by activation-dependent accessibility increases by another class."
- **Technical failings that need to be addressed before the case is established**
    - R1-M1 (causality of activation-mediated accessibility)
    - R1-M2 (confounding factors in high/low-affinity motif comparison)
- **Assessment against Nature-style criteria**
    - **Originality** High. The study presents a novel conceptual framework (two-tier model) and a new methodological approach (using deep learning to dissect pioneer vs. non-pioneer activity). This is a significant advance over previous descriptive studies.
    - **Scientific importance** High. The question of how TFs navigate chromatin is fundamental. The proposed model has the potential to reshape thinking about enhancer regulation and pioneer factor function. The study also provides a valuable resource of high-resolution data.
    - **Interdisciplinary readership** High. The work bridges computational biology, developmental biology, and chromatin biology. The findings will be of interest to a broad audience, including those studying gene regulation, epigenetics, and computational genomics.
    - **Technical soundness** The core computational and experimental approaches are sound and state-of-the-art. However, the causal interpretation of the "activation-mediated" accessibility and the potential confounding in the affinity analysis are significant concerns that need to be addressed to fully support the claims.
    - **Readability for nonspecialists** The manuscript is well-written and the logic is clear. The use of figures is effective. However, the deep learning methods may be challenging for some readers. The authors do a good job of explaining the concepts in the main text.
- **Recommendation posture** Supportive if technical concerns are resolved. The study is potentially important and the data are rich. However, the central claims regarding the two-tier model and the affinity-proportional pioneering require stronger causal evidence and a more rigorous analysis of potential confounding factors. The manuscript is not currently established from the provided evidence, but the issues are addressable.

## Risk / unsupported claims
- The claim that "patterning TFs augment chromatin accessibility in sequence contexts in which they mediate enhancer activation" is not fully supported by direct causal evidence. The genetic experiments show correlation but not causation.
- The claim that "low-affinity Zelda motifs can promote accessibility, but to a lesser extent than high-affinity motifs" is potentially confounded by unaccounted genomic features in the selection of high- and low-affinity motif sets.
- The generalizability of the "two-tier" model to other organisms or developmental contexts is not established and is presented as a universal principle.
- The statement that "GAF does not play the same role as Zelda in helping other TFs bind" is based on model predictions and in silico injections, but is not directly validated experimentally.
- The claim that "patterning TFs require an already accessible state for their binding" is inferred from the data but not directly tested.