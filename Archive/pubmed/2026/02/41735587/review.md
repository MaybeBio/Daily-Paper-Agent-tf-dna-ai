## Review setup
- **Input scope** Full manuscript text, including abstract, main text, results, discussion, methods, figure legends, and supplementary information descriptions.
- **Assessment boundary** Scientific content, methodological rigor, validity of conclusions, and presentation quality. Not assessed: editorial fit, ethical compliance, or data availability logistics beyond what is stated.
- **Shared manuscript claim summary** The authors present Pico-C, a low-input Micro-C method, to map 3D genome architecture in Drosophila embryos from nuclear cycles 9–14. They report dynamic, ordered emergence of chromatin loops before zygotic genome activation, context-dependent coupling of chromatin structure and state, site-specific effects of transcriptional elongation inhibition, machine learning-based identification of sequence motifs contributing to architecture, and orthogonal regulatory contributions of the pioneer factors Zelda and GAF.
- **Visible evidence base** Main figures 1–5, extended data figures 1–10, supplementary tables 1–2, supplementary data 1–7, and methods text. No raw sequencing data or processed data files were available for direct inspection.
- **Missing materials affecting confidence** Raw and processed sequencing data files, detailed quality control metrics for all datasets, code for model training and analysis, and complete parameter settings for several analyses. The manuscript states these are available but they were not provided for review.

## Reviewer
- **Overall assessment** This manuscript presents a valuable new resource and a series of observations about 3D genome organization during early Drosophila development. The Pico-C method appears to be a genuine technical advance, enabling high-resolution chromatin conformation capture from limited input material. The temporal series from NC9 to NC14 is a strength, and the integration of public epigenomic data adds context. However, the central claims of "orthogonal regulatory inputs" and "modular regulatory logic" are not fully supported by the data presented. The effects of perturbations are modest and often not statistically robust, and the causal relationship between the identified factors and the observed architectural changes remains correlative. The machine learning analysis is intriguing but the biological validation is incomplete. The manuscript would be strengthened by more direct functional experiments and a more cautious interpretation of the current results.
- **Who would be interested in the results, and why** Researchers studying 3D genome organization, chromatin structure and function, developmental biology, and gene regulation. The Pico-C method will be of interest to the chromatin biology community as a technical resource. The temporal maps of chromatin architecture during early embryogenesis will be a useful reference. The analysis of pioneer factor contributions to genome folding is relevant to those studying transcriptional regulation and cellular reprogramming.
- **Major strengths**
  1. The development of Pico-C is a significant technical advance, allowing high-resolution chromatin conformation capture from limited input material, which is a common bottleneck in developmental studies.
  2. The temporal resolution from NC9 to NC14 provides a detailed view of chromatin architecture changes leading up to ZGA, filling an important gap.
  3. The integration of multiple public datasets (ATAC-seq, ChIP-seq, RNA-seq) with the new Pico-C data provides a rich, multi-layered view of the regulatory landscape.
  4. The use of machine learning to identify sequence features associated with architectural changes is a forward-looking approach that generates testable hypotheses.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of conclusions
- **Claim pointer** The authors claim that "inhibition of transcriptional elongation has site-specific effects, retaining some early loops while weakening insulation at active promoters, suggesting distinct regulatory dependencies."
- **Evidence pointer** Figure 3e–h, Extended Data Fig. 7
- **Concern** The evidence for this claim is not fully convincing. The effects of α-amanitin treatment on chromatin architecture are described as "modest" and "site-specific," but the statistical framework for identifying these sites is not clearly described. The Chromosight analysis shows small mean score differences, and it is unclear whether these are biologically meaningful or within the range of technical noise. The claim of "distinct regulatory dependencies" is an interpretation that goes beyond the data, as the authors do not directly test the mechanism by which transcriptional elongation affects loop stability or insulation.
- **Why it matters** This is a central claim of the paper, as it links transcriptional activity to architectural changes. If the effects are not robust or are not specifically due to elongation inhibition, the conclusion is weakened.
- **Resolution test** Provide a clear statistical framework for identifying significant changes in loop and boundary strength. Show that the observed changes are reproducible across replicates and are not explained by global changes in chromatin compaction. Include a control experiment, such as treatment with a different transcriptional inhibitor, to demonstrate specificity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of conclusions
- **Claim pointer** The authors claim that "co-depletion of the pioneer factors Zelda and GAF leads to factor-specific perturbations in chromatin architecture, further highlighting a modular regulatory logic in genome establishment."
- **Evidence pointer** Figure 5, Extended Data Fig. 10
- **Concern** The Jabba-Trap system is used to deplete both Zelda and GAF simultaneously, but the authors do not present data on single depletions in this context. The claim of "factor-specific perturbations" is therefore not directly supported, as the observed effects could be due to either factor alone or their combination. The analysis shows that some clusters are affected more than others, but the link between these clusters and the specific binding sites of Zelda or GAF is not established. The statement that these are "orthogonal" inputs is an interpretation that requires direct evidence of independent pathways.
- **Why it matters** The concept of "orthogonal regulatory inputs" is a key conceptual advance claimed by the paper. Without single-depletion experiments, the independence of the two pathways cannot be assessed.
- **Resolution test** Perform single depletions of Zelda and GAF, in addition to the double depletion, and compare the architectural changes. Show that the effects of the double depletion are not simply the sum of the single depletions, or that distinct sets of loci are affected by each factor. Alternatively, demonstrate that the affected clusters are specifically bound by one factor but not the other.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "machine learning models trained on sequence features identify orthogonal, motif-specific contributions to architecture."
- **Evidence pointer** Figure 4, Extended Data Fig. 8
- **Concern** The machine learning analysis is described briefly, and the validation is limited. The models are trained on NC12 and NC14 data, but the performance metrics are only reported as Pearson's correlation (r = 0.68 for NC14, r = 0.42 for NC12). The lower correlation for NC12 is not discussed. The in silico mutagenesis identifies motifs, but the connection between these motifs and the actual factors that bind them is speculative. The "orthogonal" nature of the motif contributions is inferred from the lack of correlation between individual motif effects, but this is not a direct test of independence.
- **Why it matters** The machine learning approach is a major component of the paper's claim to identify new regulatory factors. If the models are not well-validated or the motif predictions are not accurate, the conclusions are not reliable.
- **Resolution test** Provide more detailed model performance metrics, including precision-recall curves or area under the curve values. Validate the motif predictions experimentally, for example by showing that mutations in the predicted motifs affect chromatin architecture. Discuss the lower performance of the NC12 model and its implications.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "spatial autocorrelation analysis points to context-dependent regulatory influences on chromatin."
- **Evidence pointer** Figure 3a–d, Extended Data Fig. 6
- **Concern** The Metaloci analysis is used to show that the relationship between chromatin state and structure varies by locus. However, the analysis is descriptive and does not provide a quantitative framework for understanding what "context-dependent" means. The authors do not identify the specific contextual features that determine whether a locus shows a strong or weak correlation between state and structure. The comparison between NC12 and NC14 is interesting, but the biological significance of the changes in Moran's I values is not clear.
- **Why it matters** This analysis is used to support the idea that chromatin architecture is shaped by multiple, context-dependent regulatory inputs. Without a more detailed understanding of what determines the context, this claim remains vague.
- **Resolution test** Identify specific genomic features (e.g., promoter presence, enhancer activity, gene density) that correlate with the strength of the state-structure relationship. Show that these features can predict the observed patterns.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "Pico-C maps achieve the same high-quality metrics as other publicly available Micro-C datasets."
- **Evidence pointer** Supplementary Table 1, Extended Data Fig. 1
- **Concern** The quality metrics are summarized in a supplementary table, but the details of how these metrics were calculated are not provided. The comparison to "other publicly available Micro-C datasets" is not shown directly. It is unclear whether the comparison is appropriate, as the other datasets may have been generated from different cell types or under different conditions.
- **Why it matters** The quality of the Pico-C data is foundational to all subsequent analyses. If the quality is not adequately demonstrated, the reliability of the conclusions is in question.
- **Resolution test** Provide a direct comparison of Pico-C quality metrics to those of published Micro-C datasets from similar samples. Include details on how the metrics were calculated and the statistical significance of any differences.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1c
- **Evidence pointer** Figure 1c
- **Issue** The figure shows three examples of architectural features (i, ii, iii) but the text does not clearly explain what the reader should observe in each panel. The description of the "bowtie structure" and "tether elements" is not defined in the text.
- **Required correction** Add a more detailed description of the features shown in Figure 1c in the main text or figure legend, including a definition of the terms "bowtie structure" and "tether elements."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Pico-C data processing"
- **Evidence pointer** Methods section
- **Issue** The description of the bin size determination is vague. The authors state that a "customized Python script" was used, but the criteria for selecting the bin size are not described.
- **Required correction** Provide a more detailed description of the bin size selection criteria, or cite a published method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "Multifaceted chromatin landscape underpins 3D genome"
- **Evidence pointer** Figure 2e
- **Issue** The ChromHMM analysis is described as using data from "four broader developmental timepoints," but the specific datasets used for each timepoint are not listed in the main text. The reader is referred to Supplementary Data 4, but this is not sufficient for a full understanding.
- **Required correction** List the specific datasets used for each timepoint in the main text or a supplementary table.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion compares the findings to vertebrate systems, but the comparison is brief and does not fully consider alternative interpretations. For example, the statement that "genome regulators in Drosophila function additively" is presented as a contrast to vertebrates, but the evidence for additivity is indirect.
- **Required correction** Expand the discussion to consider alternative interpretations of the data and to more carefully qualify the comparison to vertebrate systems.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Model training and evaluation"
- **Evidence pointer** Methods section
- **Issue** The description of the Orca model training is brief. The authors state that they "adapted" the model, but the specific modifications are not described.
- **Required correction** Provide a more detailed description of the model architecture and the modifications made, or cite a source where this information is available.

## Risk / unsupported claims
- The claim of "orthogonal regulatory inputs" is not directly supported by the data, as single-depletion experiments were not performed.
- The claim that "inhibition of transcriptional elongation has site-specific effects" is based on modest effects that may not be statistically robust.
- The biological significance of the changes in Moran's I values in the Metaloci analysis is not established.
- The machine learning model predictions are not validated experimentally, and the lower performance of the NC12 model is not discussed.
- The comparison of Pico-C quality to other datasets is not shown directly, making it difficult to assess the claim of equivalent quality.