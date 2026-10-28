## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, conclusion, and methodology sections. Figures and supplementary materials are referenced but not provided.
- **Assessment boundary** The review is limited to the content presented in the provided manuscript text. Claims are evaluated based on the described methods, results, and interpretations as written.
- **Shared manuscript claim summary** The authors propose that incorporating DNA conformational flexibility descriptors, derived from experimental and computational sources, into predictive models of transcription factor (TF) binding specificity improves performance over sequence-only and DNA shape-based models. They report consistent gains across multiple in vitro platforms (HT-SELEX, SELEX-Seq, PBM) and in vivo ENCODE ChIP-seq data, and identify position-specific "flexibility hotspots" that align with structural data for the homeodomain TF MSX1.
- **Visible evidence base** The manuscript text describes results from PCA, regression models, and classification frameworks. Specific quantitative values are reported for PCA variance (PC1 14.8% vs 12.9%), R² improvements for several TF families, and classification metrics (88.2% of datasets with increased MCC). Structural analysis of MSX1 (PDB 1IG7) is described. All figures, tables, and supplementary materials are referenced but not included in the provided material.
- **Missing materials affecting confidence** All figures, tables, and supplementary figures are referenced but not provided. The GitHub repository link is given but its contents are not assessed. Specific statistical test results (e.g., p-values for Wilcoxon tests) are mentioned but not reported in detail. The full list of 215 TFs and their family assignments is not provided. The methodology for the in vivo classification framework is described but the specific datasets and quality control thresholds are not fully detailed.

## Reviewer

- **Overall assessment** The manuscript addresses an important and timely question in gene regulation: whether DNA flexibility, beyond static shape, contributes to TF binding specificity. The authors present a systematic analysis across multiple large-scale datasets and report consistent improvements when flexibility descriptors are added to sequence-based models. The work is potentially significant, as it generalizes previous observations on a limited set of TFs to a broad range of families. However, the current manuscript has several technical and presentational issues that need to be addressed. The most critical concerns are the lack of a clear comparison to state-of-the-art methods, the absence of statistical rigor in some comparisons, and the incomplete description of the in vivo analysis. The structural interpretation for MSX1 is intriguing but requires more careful quantitative support. Overall, the core hypothesis is well-motivated and the results are promising, but the evidence as presented is not fully convincing.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational biology, and structural biology of protein-DNA interactions would be the primary audience. The work is also relevant to those developing predictive models for regulatory genomics, including methods for interpreting non-coding variants and understanding gene regulatory networks. The general finding that flexibility improves prediction across families could influence how TF binding sites are modeled in various applications.
- **Major strengths** The study leverages large, publicly available datasets, which lends statistical power to the analysis. The inclusion of multiple experimental platforms (HT-SELEX, SELEX-Seq, PBM) and in vivo data strengthens the generalizability of the claims. The systematic evaluation of different flexibility descriptors and the position-specific analysis provide a detailed view of where flexibility matters. The structural validation using MSX1 is a nice touch that connects the computational predictions to a concrete biological example.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that flexibility-augmented models "consistently outperform sequence-based models, and DNA shape augmented models to an extent" across multiple datasets.
- **Evidence pointer** Results section, Figures 2A-2E, Supplementary Figure 2
- **Concern** The comparison to DNA shape-based models is not rigorously quantified. The text states that flexibility models "match or exceed" shape models, but no statistical test is reported for this comparison. The claim of "to an extent" is vague. A direct, statistically rigorous comparison between flexibility-augmented and shape-augmented models is needed, with appropriate multiple-testing corrections across the many TF families and datasets.
- **Why it matters** The central claim of the paper is that flexibility adds predictive value beyond shape. Without a proper statistical comparison, this claim is not established. The reader cannot determine if the observed differences are meaningful or within noise.
- **Resolution test** Provide a clear table or figure comparing R² (or other metrics) for sequence-only, shape-augmented, and flexibility-augmented models for each TF family, with paired statistical tests (e.g., Wilcoxon signed-rank test) and effect sizes. Report the number of families where flexibility significantly outperforms shape, and vice versa.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "over half of the TFs analyzed (107 out of 215) exhibited more than a 10% increase in predictive performance upon inclusion of flexibility features."
- **Evidence pointer** Results section, Supplementary Table
- **Concern** The threshold of 10% increase is arbitrary and not justified. A 10% relative increase in R² may not be meaningful for TFs with very high baseline R². The analysis should report the distribution of improvements and use a statistically principled threshold, such as a significant improvement in cross-validated performance. Additionally, the relationship between improvement and dataset size or TF family should be explored.
- **Why it matters** The claim of widespread improvement is a key pillar of the paper. If the threshold is arbitrary, the conclusion may be overstated or understated. A more rigorous analysis would strengthen the claim.
- **Resolution test** Report the distribution of R² improvements across all TFs. Use a statistical test to determine if the improvements are significant for each TF, and report the number of TFs with significant improvements. Justify the choice of threshold or use a continuous measure of improvement.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors describe a classification framework for in vivo TF binding site prediction, reporting that "incorporating DNA flexibility substantially enhances the identification of functional TF binding sites."
- **Evidence pointer** Results section, Figure 5, Supplementary Figure 4
- **Concern** The description of the in vivo analysis is incomplete. The text mentions a quality control filter that retained 307 out of nearly 900 datasets, but the criteria for this filter are not fully specified. The choice of negative set (unbound motifs in open chromatin) is reasonable but the potential for biases should be discussed. The classification results are only summarized as "improvements" without specific numbers or statistical tests. The comparison to baseline models is not detailed.
- **Why it matters** The in vivo validation is crucial for establishing biological relevance. If the analysis is not fully described or rigorously quantified, the claim of in vivo utility is not supported.
- **Resolution test** Provide a detailed description of the quality control criteria and the number of datasets excluded at each step. Report the distribution of AUC and MCC for both models across all 307 datasets, with paired statistical tests. Show examples of TFs with large and small improvements.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Originality
- **Claim pointer** The authors claim that the role of DNA flexibility in TF binding "remains largely unexplored, particularly across diverse TF families."
- **Evidence pointer** Introduction, Discussion
- **Concern** The introduction and discussion do not adequately position this work relative to existing literature on DNA shape and flexibility in TF binding. Several studies have used similar descriptors (e.g., DNaseI sensitivity, nucleosome positioning) for predicting TF binding. The novelty of the current work needs to be more clearly articulated. Is the novelty in the systematic comparison across many families, the specific combination of descriptors, or the position-specific analysis?
- **Why it matters** For a Nature-style journal, the originality and conceptual advance must be clear. If the work is largely confirmatory of previous findings on a larger scale, the significance is diminished.
- **Resolution test** Revise the introduction and discussion to explicitly cite and compare with prior work on DNA shape and flexibility in TF binding prediction. Clearly state what new biological or methodological insight this study provides.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "PCA revealed that, first two principle components (PC) obtained from the combination of DNA flexibility and sequence features explained greater amount of variance in the current dataset (14.8% for PC1, and 9.1% for PC2), compared to the PC obtained from sequence only features(PC1: 12.9% and PC2: 9%)."
- **Evidence pointer** Results section, Figure 1A
- **Concern** The increase in explained variance from 12.9% to 14.8% for PC1 is modest. The authors should assess whether this increase is statistically significant and biologically meaningful. A permutation test or a comparison with random features would help establish that the improvement is not due to chance or increased dimensionality.
- **Why it matters** The PCA analysis is used to support the claim that flexibility adds information. If the increase is not significant, this support is weakened.
- **Resolution test** Perform a permutation test where flexibility features are randomly shuffled and the PCA is repeated. Report the distribution of explained variance under the null hypothesis and the p-value for the observed increase.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction use terms like "axial, torsional, and stretching dynamics" and "flexibility hotspots" without immediately defining them for a general reader. The concept of "indirect readout" is also introduced without a brief explanation.
- **Required correction** Provide brief definitions or a short explanatory sentence when these terms are first introduced. For example, "DNA flexibility, which encompasses bending (axial), twisting (torsional), and stretching motions, ..."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methodology, Model fitting
- **Evidence pointer** Methodology, "Model fitting and evaluations"
- **Issue** The choice of the regularization strength λ range [10⁻¹, 10⁶] is not justified. The range seems arbitrary and may not be appropriate for all datasets.
- **Required correction** Justify the range or describe a data-driven approach for selecting the range. Alternatively, state that the range was chosen based on preliminary experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, In vivo analysis
- **Evidence pointer** Results, "DNA Flexibility-Augmented Models Improve Predictive Performance for TF Binding Specificity In Vivo"
- **Issue** The text mentions "nearly 900 ENCODE TF ChIP-seq datasets" but the final number used is 307. The reasons for excluding the other ~600 datasets are not fully explained.
- **Required correction** Provide a breakdown of the exclusion criteria (e.g., insufficient peaks, no matched DNase-seq, etc.) in the methodology or results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of "flexibility signatures" and their relation to TF family-specific binding modes could be more accessible to readers who are not structural biologists.
- **Required correction** Consider adding a simple schematic or a more intuitive explanation of how flexibility at the 3' flank might facilitate the structural changes needed for binding.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methodology, Feature Encoding
- **Evidence pointer** Methodology, "Encoding DNA Flexibility Features of TFBS"
- **Issue** The manuscript states that "interaction terms of the each flexibility feature as a second-order representation" were used, but it is not clear what these interaction terms are. Are they products of flexibility values at different positions?
- **Required correction** Clarify the definition of the interaction terms and how they were included in the model.

- **Technical failings that need to be addressed before the case is established** The primary technical failing is the lack of a rigorous statistical comparison between flexibility-augmented and shape-augmented models. The claim that flexibility adds value beyond shape is central and must be supported with appropriate statistical tests. The in vivo analysis also needs more detail and quantitative reporting. The PCA analysis needs a significance test. These issues are captured in R1-M1, R1-M2, R1-M3, and R1-M5.
- **Assessment against Nature-style criteria** 
  - Originality: The work is a systematic extension of previous studies on DNA shape and flexibility. The originality lies in the scale and breadth of the analysis, but the conceptual advance over existing work needs to be more clearly articulated. The position-specific analysis and the structural validation for MSX1 are original elements.
  - Scientific importance: The question of how TF binding specificity is determined is of fundamental importance. If the claims are substantiated, the work would have broad implications for understanding gene regulation and for improving predictive models. The demonstration that flexibility is a general determinant across families would be a significant contribution.
  - Interdisciplinary readership: The topic is of interest to molecular biologists, computational biologists, and structural biologists. The manuscript is written in a way that is largely accessible, but some terms and concepts could be better explained for a general audience.
  - Technical soundness: The overall approach is sound, but the statistical rigor of the comparisons needs improvement. The lack of a direct, statistically tested comparison to shape-based models is a significant weakness. The in vivo analysis is under-described.
  - Readability for nonspecialists: The abstract and introduction are reasonably clear, but the results section is dense and would benefit from more interpretation and context. The figures, which are not provided, would likely help.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the preliminary results are promising. However, the current evidence does not fully establish the central claim that flexibility provides a significant and general improvement over shape-based models. The authors need to provide a more rigorous statistical analysis and a more complete description of the in vivo experiments.

## Risk / unsupported claims
- The claim that flexibility-augmented models "consistently outperform" shape-based models is not supported by the provided evidence, as no statistical comparison is reported.
- The claim that "over half of the TFs analyzed exhibited more than a 10% increase" is based on an arbitrary threshold and is not statistically validated.
- The claim that "DNA flexibility substantially enhances the identification of functional TF binding sites" in vivo is not supported by specific quantitative results or statistical tests.
- The biological interpretation of the MSX1 structural analysis is presented as supportive but is based on a qualitative comparison; the quantitative link between the flexibility scores and the structural observations is not fully established.
- The statement that the improvements are "robust across different organism, experimental design" is a general claim that is not fully supported by the data presented, as the number of datasets and organisms is limited.