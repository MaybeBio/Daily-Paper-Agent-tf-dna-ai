## Review setup

- **Input scope** Full manuscript text (abstract, main text, figure legends referenced but not provided, code/data availability statement)
- **Assessment boundary** Scientific claims, methodology as described, evidence consistency, and interpretation based solely on the supplied text
- **Shared manuscript claim summary** The authors use BPNet models trained on ~2,000 ENCODE TF ChIP-seq profiles to test whether motif cooperativity contributes substantially to genome-wide TF binding predictions. They report that cooperative interactions among direct motifs and between direct and non-direct motifs are largely negligible, that models capture differential binding preferences among TFs with similar motifs in the same cell type, and that chromatin accessibility alone is insufficient to explain selective TF binding.
- **Visible evidence base** Abstract, main text narrative, references to Figures 1-4 and Figures S1-S2, code/data availability statement
- **Missing materials affecting confidence** All figures, figure legends, supplementary figures, methods section, model training details, perturbation protocol specifics, statistical tests, and quantitative results are not provided. The manuscript text alone does not permit independent verification of the central claims.

## Reviewer

- **Overall assessment** The manuscript addresses a timely and important question in gene regulation, namely whether motif cooperativity is a major determinant of TF binding specificity at the genomic scale. The authors leverage a powerful and widely used deep learning framework (BPNet) across a large compendium of ENCODE data, which is a sensible and potentially impactful approach. However, the text as provided is a narrative summary without the accompanying figures, methods, or quantitative details. The central claims, while plausible, cannot be evaluated for technical soundness or statistical support from the supplied material. The conclusion that cooperativity is negligible is strong and would require rigorous demonstration that the perturbation assays are sensitive enough to detect cooperativity when it exists, and that the model's additive behavior is not an artifact of training objectives or sequence composition. The manuscript is well written and accessible, but the evidence base is incomplete for a definitive assessment.

- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational genomics, and machine learning applied to functional genomics would be interested. The work challenges a prevailing assumption about cooperativity and offers a framework for interrogating sequence determinants of TF binding at scale. It would also be of interest to those developing or interpreting deep learning models for regulatory genomics, as it addresses the interpretability and biological validity of model-derived features.

- **Major strengths** The question is fundamental and the approach is genome-wide and systematic. The use of BPNet across ~2,000 ENCODE experiments is a substantial resource. The authors explicitly acknowledge the distinction between predictive accuracy and biological mechanism, which is a mature and important perspective. The in silico perturbation strategy is a principled way to test additivity versus cooperativity, provided the controls and sensitivity analyses are adequate.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Cooperative interactions among direct motifs made a negligible contribution to model-predicted TF binding" and "cooperativity between direct and non-direct motifs made a negligible contribution to genome-wide binding predictions"
- **Evidence pointer** Figures 2D-F, 3D-E; location not provided
- **Concern** The central claim of negligible cooperativity rests entirely on the in silico perturbation analysis, but the text does not describe the perturbation protocol, the thresholds for calling a motif, the definition of "additive," the statistical framework for comparing observed versus expected combined effects, or the sensitivity of the assay. Without these details, it is impossible to assess whether the assay would detect cooperativity if it were present. The authors note that cooperative effects were detected at individual peaks and were more prominent for FOXA1 and FOXA2, which suggests the assay can detect cooperativity in some cases, but the criteria for "negligible" at the genome-wide level are not defined.
- **Why it matters** The conclusion that cooperativity is negligible is the central finding of the manuscript. If the perturbation assay is underpowered, biased by sequence context, or confounded by model architecture, the conclusion would be unsupported. The reader cannot judge the robustness of the claim without the methodological details and the distribution of effect sizes.
- **Resolution test** Provide the full perturbation methodology, including how motifs are defined and mutated, how additivity is modeled, what statistical test is used to detect deviations from additivity, and a power analysis or positive control demonstrating that the assay can detect cooperativity when it is known to exist. Show the full distribution of interaction effect sizes across peaks and TFs, not just summary statements.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The models captured differences in binding preferences between TFs with similar motif preferences, even within the same cellular environment" and "canonical motif recognition and a shared chromatin environment are insufficient to fully explain TF genomic selectivity"
- **Evidence pointer** Figures 4A-E, Figure S2; location not provided
- **Concern** The claim that models capture differential binding among TFs with similar motifs is presented with examples (FOX and SP/KLF families), but the text does not describe how "similar motif preferences" are defined, how binding profiles are compared, what metric is used to assess model accuracy in capturing differences, or whether the differences are statistically significant beyond noise. The statement that differences "persisted when mutating the major seqlets" is intriguing but unexplained. Without a quantitative comparison of model predictions versus ChIP-seq data for these TFs, and a demonstration that the differences are not due to trivial sequence features, the claim is not established.
- **Why it matters** This claim is used to argue that additional sequence determinants beyond canonical motifs and chromatin accessibility exist. If the model differences are driven by subtle motif variants, spacing, or other features that are not described, the interpretation is incomplete. The claim is central to the paper's broader message that prevailing models are insufficient.
- **Resolution test** Provide the definition of motif family similarity, the metric for comparing binding profiles, the quantitative accuracy of model predictions for the exemplified TFs, and a description of what sequence features drive the differential predictions. Show that the differences are robust to model architecture and training data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "The models' interpretation framework identifies sequence regions contributing to predictions at individual binding peaks, termed seqlets, and clusters these into recurrent patterns summarized as contribution weight matrices (CWMs). These patterns often correspond to individual TF-binding motifs, as well as composite motifs representing combinations of binding sites that could reflect cooperative TF interactions."
- **Evidence pointer** Figure 1E-I; location not provided
- **Concern** The text states that composite motifs were detected but occurred in a minority of peaks, and that seqlets contained approximately 12 bits of information. However, the criteria for calling a composite motif, the fraction of peaks with composite motifs across TFs, and the relationship between seqlet information content and binding specificity are not quantified. The claim that "neither composite motifs nor high-information-content sequence patterns contribute substantially" is a negative result that requires a clear definition of "substantial" and a demonstration that the interpretation framework is sensitive enough to detect such patterns if they existed.
- **Why it matters** This is the first line of evidence against cooperativity. If the interpretation framework is biased toward simple motifs or if the clustering parameters obscure composite patterns, the conclusion would be weakened. The reader needs to see the distribution of seqlet information content and the frequency of composite motifs across the full set of TFs.
- **Resolution test** Provide the distribution of seqlet information content, the fraction of peaks with composite motifs per TF, and a positive control showing that the framework can recover known composite motifs or cooperative interactions in synthetic or well-characterized cases.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We used control-free predicted count scores, as BPNet predictions were often dominated by the free-DNA control"
- **Evidence pointer** Figure 1D; location not provided
- **Concern** The decision to use control-free predicted count scores is mentioned in passing but is not justified in detail. If the free-DNA control dominates predictions, it is unclear what the model is actually learning and whether the perturbation analysis is measuring TF-specific binding or a generic DNA accessibility signal. The authors do not describe how the control-free scores were computed or whether this choice affects the additivity analysis.
- **Why it matters** The validity of the perturbation assay depends on the predicted scores reflecting TF binding rather than experimental artifacts. If the control dominates, the model may not be capturing TF-specific sequence determinants, which would undermine all subsequent conclusions.
- **Resolution test** Provide a detailed description of the control-free score computation, a comparison of model performance with and without the control, and a demonstration that the perturbation effects are specific to TF binding rather than generic sequence features.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that cooperativity made a "negligible contribution" but does not define the quantitative threshold for negligible. This is a strong claim that should be qualified with a specific effect size or fraction of peaks.
- **Required correction** Add a quantitative definition of "negligible" in the abstract, such as the median interaction effect size or the fraction of peaks with interaction effects above a threshold.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Code and data availability statement
- **Issue** The code and notebooks are available, but the text does not specify whether the trained BPNet models, the ENCODE data preprocessing pipelines, and the perturbation analysis scripts are all included. The statement is too brief to ensure full reproducibility.
- **Required correction** Specify which components are included in the deposited code, and provide a link to the ENCODE data versions used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of alternative mechanisms
- **Evidence pointer** Final paragraph, location not provided
- **Issue** The discussion of weak, distributed sequence signals and IDR contributions is speculative and not directly tested in this manuscript. While appropriate as a discussion point, it should be clearly separated from the empirical findings.
- **Required correction** Frame these as hypotheses for future work, and avoid implying that the current data support them.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figures 2-3
- **Evidence pointer** Figures 2D-F, 3D-E; location not provided
- **Issue** The text reports that cooperative effects were detected at individual peaks and were more prominent for certain TFs, but no statistical significance or effect size distributions are provided in the text.
- **Required correction** Report the number of peaks and TFs analyzed, the distribution of interaction effect sizes, and the statistical test used to identify significant deviations from additivity.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4. The manuscript as provided lacks the methodological detail and quantitative evidence required to support the central claims. The perturbation assay, the interpretation framework, and the comparison of TF families are all described at a high level without the necessary technical specifications.

- **Assessment against Nature-style criteria** 
  - Originality: The question of whether cooperativity contributes to TF binding specificity at the genomic scale is not entirely new, but the systematic use of BPNet across ~2,000 ENCODE experiments is a novel and potentially impactful approach. The negative result, if robust, would challenge a widely held assumption.
  - Scientific importance: High. Understanding the determinants of TF binding specificity is fundamental to gene regulation. A rigorous demonstration that cooperativity is negligible would redirect research toward other mechanisms.
  - Interdisciplinary readership: The topic is relevant to molecular biology, genomics, and computational biology. The writing is accessible, but the lack of methodological detail limits the ability of a broad audience to evaluate the claims.
  - Technical soundness: Cannot be assessed from the provided text. The perturbation analysis, interpretation framework, and statistical methods are not described in sufficient detail.
  - Readability for nonspecialists: The text is clearly written and the narrative is easy to follow, but the absence of figures and quantitative results makes it difficult for nonspecialists to grasp the evidence.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an important question and the approach is promising, but the central claims cannot be evaluated without the figures, methods, and quantitative results. The authors should provide the full methodological details and evidence before the case for negligible cooperativity can be assessed.

## Risk / unsupported claims
- The claim that cooperativity is negligible at the genomic scale is unsupported without the full perturbation methodology and effect size distributions.
- The claim that models capture differential binding among TFs with similar motifs is unsupported without quantitative comparisons and definitions of motif family similarity.
- The claim that chromatin accessibility is insufficient to explain TF selectivity is presented as a conclusion but is not directly tested in the text.
- The discussion of weak, distributed sequence signals and IDR contributions is speculative and not supported by data presented in the manuscript.
- The statement that "neither composite motifs nor high-information-content sequence patterns contribute substantially" is a negative claim that requires sensitivity analysis and positive controls to be meaningful.