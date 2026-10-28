## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion, supplementary methods) as provided on bioRxiv.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to the presented evidence, and general interest. No assessment of editorial fit or formatting.
- **Shared manuscript claim summary** The authors present TFBlearner, a scalable machine learning platform using gradient-boosted decision trees with extensive feature engineering, to predict transcription factor (TF) binding across human cell types from ATAC-seq data. They benchmark against existing methods, generate a large compendium of predictions for 1108 chromatin-associated proteins across 43 cell types, and use these predictions to investigate the phenomenon of "crowded" or high-occupancy target (HOT) regions, proposing that such regions are functional and linked to 3D chromatin contacts.
- **Visible evidence base** Abstract, full results section (Sections 1.1-1.10), methods overview (Section 2), discussion, and supplementary methods (Appendix A). Figures and tables are referenced but not directly viewable.
- **Missing materials affecting confidence** The actual figures, tables, and supplementary figures/tables are not provided. This significantly limits the ability to verify quantitative claims, assess model performance metrics, and evaluate the statistical analyses. Specific numerical results (e.g., AUPRC values, p-values, effect sizes) are largely absent from the text.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and potentially valuable resource in the form of a large-scale, scalable TF binding prediction platform. The methodological choices, particularly the emphasis on feature engineering and information sharing across cell types, are well-motivated and represent a sensible alternative to purely deep learning-based approaches. The biological observations regarding crowded regions, especially the link to 3D chromatin contacts and the evidence for their functionality, are intriguing and could be of significant interest to the regulatory genomics community. However, the current manuscript has several major weaknesses that prevent a full endorsement. The most critical issue is the lack of direct evidence for the central claims, as the key figures and quantitative results are not available for review. Furthermore, the analysis of crowded regions, while interesting, appears to be largely correlative, and the proposed "tethered binding" model, while plausible, is not directly tested. The claim of "state of the art" performance needs to be more carefully qualified given the acknowledged limitations in predicting novel binding sites. The manuscript would be significantly strengthened by a more direct experimental or quasi-experimental test of the proposed model for crowdedness.

- **Who would be interested in the results, and why** This work will be of primary interest to researchers in regulatory genomics, computational biology, and gene expression regulation. The TFBlearner platform and the compendium of predictions across 43 cell types, including understudied brain cell types, will be a useful resource for the community. The analysis of HOT regions and their link to 3D genome organization will also appeal to scientists studying chromatin architecture and transcriptional regulation. The methodological framework for scalable prediction may also be of interest to those working on similar large-scale genomics prediction problems.

- **Major strengths**
    1.  **Scalability and Scope:** The development of a platform that can scale to over 1000 TFs and hundreds of cell types is a significant technical achievement, addressing a clear bottleneck in the field. The resulting compendium of predictions is a valuable community resource.
    2.  **Biologically-Motivated Feature Engineering:** The focus on features like TF cooperativity, binding similarity across cell types, and ATAC-seq fragment patterns is a thoughtful and effective strategy that likely improves generalizability and interpretability compared to purely sequence-based deep learning models.
    3.  **Pre-registered Benchmark:** The use of a pre-registered benchmark on held-out cell types is a strong methodological practice that enhances the credibility of the performance comparisons.
    4.  **Biological Insights:** The investigation into crowded regions, moving beyond simple prediction to explore the biological implications of promiscuous binding, elevates the work from a purely technical contribution to one with biological relevance. The observation that crowded promoters engage in more 3D contacts is a novel and interesting finding.

- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence
    - **Claim pointer** The manuscript claims that TFBlearner achieves "state of the art binding predictions in unseen cell types" and "compares favorably to alternative methods in a pre-registered benchmark."
    - **Evidence pointer** Section 1.4, Figure 2, Supplementary Figures 4-8
    - **Concern** The central performance claims cannot be evaluated. The text describes the benchmark and its outcomes but does not provide the actual quantitative results (e.g., AUPRC values, precision-recall curves, or statistical comparisons) in the manuscript text. The key figures (Figure 2, Supplementary Figures 4-8) are not available for review. Without this data, it is impossible to assess whether the performance is indeed "state of the art" or merely comparable to existing methods. The claim of "favorable" comparison needs to be substantiated with specific numbers and statistical tests.
    - **Why it matters** The primary technical contribution of this work is the predictive model. If the performance claims are not verifiable, the core value proposition of the manuscript is undermined. The reader cannot judge the utility of the TFBlearner platform or the reliability of the downstream biological analyses that depend on its predictions.
    - **Resolution test** Provide the full benchmark results, including AUPRC values for all methods across all TF-cell type combinations, with appropriate statistical comparisons (e.g., paired tests). Show the precision-recall curves and clearly state the variance in performance across TFs. The figures must be made available for review.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence
    - **Claim pointer** The manuscript claims that "most TF occupancy at crowded promoters can be explained as tethered bindings from distal regulatory elements."
    - **Evidence pointer** Section 1.10, Figure 7
    - **Concern** This is a strong mechanistic claim that is not directly tested. The evidence presented appears to be correlative: crowded promoters have more 3D contacts, and the TFs binding at a promoter are also found at its distal contacts. This is consistent with the "tethered binding" hypothesis, but it does not rule out other explanations, such as the promoter and enhancer being independently bound by the same TFs due to shared sequence features or being part of a larger, pre-assembled complex. The analysis does not appear to include a direct test of whether the binding at the promoter is *dependent* on the 3D contact or the binding at the distal element.
    - **Why it matters** This is a key biological conclusion of the paper. Overstating the evidence for a specific mechanism could mislead the field. The distinction between "correlated binding" and "tethered binding" is fundamental to understanding the mechanism of transcriptional regulation at these loci.
    - **Resolution test** The authors should either (1) soften the claim to state that the data is "consistent with" a tethered binding model, or (2) provide a more direct test. For example, they could analyze whether the probability of a TF binding at a promoter is higher when a specific, bound distal element is in close 3D proximity, controlling for the promoter's intrinsic accessibility and sequence features. Alternatively, they could use a statistical model to test if the observed co-binding is more than what would be expected by chance given the accessibility profiles of the two loci.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical Soundness
    - **Claim pointer** The manuscript states that "all models fail at finding, for most TFs, truly generalizable patterns" and that "simply using nucleosome-free ATAC signal alone" performed well for novel sites.
    - **Evidence pointer** Section 1.4, Supplementary Figure 9
    - **Concern** This is a significant and somewhat sobering finding that is mentioned in the discussion but appears to be underemphasized in the results. If the models are largely predicting binding at sites that were already observed in training data, and are no better than a simple accessibility signal for novel sites, then the claim of "state of the art" prediction is misleading. The practical utility of the compendium for predicting *new* regulatory interactions in previously uncharacterized cell types is questionable. The manuscript should more prominently feature this limitation and discuss its implications for the field.
    - **Why it matters** This finding directly impacts the interpretation of the large-scale prediction compendium. If the predictions are not generalizable, then the resource is primarily a catalog of known binding events rather than a tool for discovering new ones. This is a crucial caveat for any user of the resource.
    - **Resolution test** The authors should clearly separate performance metrics for "seen" vs. "unseen" sites in the main text and figures. They should explicitly state the performance of their model and the simple baseline on the "novel site" prediction task. The discussion should be reframed to acknowledge this as a central limitation of current prediction methods, including their own.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Section 1.2, Figure 1D
    - **Evidence pointer** Section 1.2, Figure 1D
    - **Issue** The text states that "for most TFs a large fraction of peaks fail to show a clear motif for the TF." This is an important observation, but the definition of a "clear motif" is not provided in the text. The threshold for a motif match can significantly influence this result.
    - **Required correction** Define the criteria used to determine whether a peak contains a "clear motif" (e.g., p-value threshold, relative score). This will allow readers to interpret the finding appropriately.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Section 1.4, Benchmark
    - **Evidence pointer** Section 1.4, Methods 2.4.3
    - **Issue** The benchmark section mentions that "Catchitt... was initially included but subsequently excluded as it repeatedly exceeded the pre-registered resource limits." This is a notable omission, as Catchitt was a strong performer in the ENCODE-DREAM challenge. Its exclusion could bias the comparison.
    - **Required correction** Provide more detail on the resource limits that were exceeded and the number of times this occurred. Acknowledge in the discussion that the exclusion of Catchitt may affect the generalizability of the benchmark conclusions.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Methods 2.2, Feature Engineering
    - **Evidence pointer** Methods 2.2, Table 1
    - **Issue** The feature engineering is a core part of the method, but the description in the main text is high-level. The full details are in the supplementary methods, which are extensive. It is difficult to assess the novelty and potential overfitting of the feature set without a clear, concise summary in the main text.
    - **Required correction** Provide a more detailed summary of the feature groups in the main text, perhaps with a table listing the feature categories and the biological rationale for each. This will make the method more accessible to a broader audience.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Presentation
    - **Affected element** Section 1.9, Figure 6
    - **Evidence pointer** Section 1.9, Figure 6
    - **Issue** The text describes the cell-type specificity of crowded regions, but the quantitative measure of this specificity is not clearly defined in the text.
    - **Required correction** Clearly define how cell-type specificity of crowded regions was quantified (e.g., Jaccard index, overlap coefficient) and state the specific values or ranges observed.

- **Technical failings that need to be addressed before the case is established**
    - The primary technical failing is the lack of access to the data and figures that support the main quantitative claims. The manuscript cannot be fully evaluated without them.
    - The analysis of the "tethered binding" model is not a direct test of the hypothesis. The evidence is correlative and does not exclude alternative models.
    - The manuscript does not adequately address the poor generalizability of the models to novel binding sites, which is a critical limitation for the practical use of the prediction compendium.

## Risk / unsupported claims
- The claim of "state of the art" performance is unsupported without the benchmark data.
- The claim that crowded occupancy is explained by "tethered bindings from distal regulatory elements" is an overstatement of the correlative evidence presented.
- The claim that the models provide "biological insights on the TFs" based on feature importance is plausible but not rigorously demonstrated in the text provided.
- The generalizability of the models to entirely novel cell types and conditions is not established, and the manuscript's own data suggests this is a major challenge.