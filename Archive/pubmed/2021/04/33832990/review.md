## Review setup
- **Input scope** Full manuscript text, including abstract, results, discussion, methods, and data access sections.
- **Assessment boundary** The scientific claims, methodological soundness, and interpretability of the findings as presented in the provided manuscript text. No external data, figures, or supplementary materials were available for review.
- **Shared manuscript claim summary** The authors present a new integrative approach combining phased whole-genome sequencing, matched epigenomic and transcriptomic profiling, and a cell state–aware deep learning model (DeepMEL2) to identify and interpret allele-specific chromatin accessibility variants (ASCAVs) in melanoma. They report that DeepMEL2 outperforms motif-based and generic deep learning models, that a substantial fraction of ASCAVs are explained by TF motif changes (particularly AP-1), and that augmenting the model with GABPA ChIP-seq data enables identification of known TERT promoter mutations.
- **Visible evidence base** Main text figures (Fig. 1A–F, 2A–F, 3A–G, 4A–F, 5A–H) are referenced but not provided. Supplemental figures and tables (S1–S17, T1–T12) are referenced but not provided. Methods descriptions are available in the main text.
- **Missing materials affecting confidence** All figures, supplemental tables, and supplemental methods are not provided. This severely limits the ability to assess data quality, statistical robustness, model performance metrics, and the validity of the bioinformatics pipeline. Specific numerical results (e.g., AUC values, effect sizes, confidence intervals) are not available in the text.

## Reviewer
- **Overall assessment** This manuscript addresses an important problem in cancer genomics: interpreting noncoding variants that affect cis-regulatory function. The authors combine a rich, matched multi-omics dataset (10 melanoma lines with phased WGS, ATAC-seq, RNA-seq, H3K27ac ChIP-seq, and AP-1 ChIP-seq) with a purpose-built deep learning model that is explicitly aware of melanoma cell states. The conceptual advance of training a model on topic-defined regulatory programs and using it to interpret allele-specific accessibility is timely and potentially impactful. However, the manuscript as presented has several critical gaps. The absence of all figures and supplementary data makes it impossible to verify the central claims, including the performance comparisons, the enrichment analyses, and the validation experiments. The text alone does not provide sufficient quantitative detail to assess the robustness of the ASCAV calling, the statistical significance of the enrichments, or the actual predictive power of DeepMEL2. The claim that 15–20% of ASCAVs are explained by TF motif changes, while an improvement over previous work, still leaves the majority unexplained, and the manuscript does not adequately discuss what other mechanisms might be at play. The TERT promoter analysis is interesting but appears to be a single-case demonstration rather than a systematic evaluation. Overall, the study has strong potential, but the current evidence base is insufficient to establish the case.

- **Who would be interested in the results, and why** Cancer genomicists and computational biologists studying noncoding mutations and gene regulation would be the primary audience. Researchers working on melanoma biology, particularly those interested in cell state heterogeneity and AP-1 signaling, would also find the data and model relevant. The broader community interested in applying deep learning to interpret regulatory genomics would be interested in the methodological advances, especially the use of topic-based cell state awareness and the integration of ChIP-seq data to augment model interpretability. The public availability of the models and code is a significant asset for this community.

- **Major strengths**
  1. The study design is strong: using phased genomes in pure cancer cell populations to directly measure allele-specific chromatin accessibility is a rigorous approach that avoids confounding from normal cell admixture.
  2. The integration of multiple matched omics layers (WGS, ATAC-seq, RNA-seq, H3K27ac, AP-1 ChIP-seq) in the same cell lines is a valuable resource.
  3. The development of a cell state–aware deep learning model is a conceptual improvement over generic models, and the authors demonstrate its utility in specific contexts (e.g., MEL vs. MES topics).
  4. The validation using allele-specific TF binding (ChIP-seq) and luciferase reporter assays provides functional evidence for a subset of predictions.
  5. The work is well contextualized within the existing literature, and the discussion of limitations (e.g., context dependence of models) is thoughtful.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that DeepMEL2 outperforms motif-based scoring and generic deep learning models (e.g., Basset, DeepSEA) in identifying ASCAVs.
- **Evidence pointer** Figure 3G, Supplemental Figure S11, location not provided.
- **Concern** The central performance comparison is presented only through figure references. No quantitative metrics (e.g., AUROC, AUPRC, sensitivity at fixed specificity) are reported in the text. The claim of "outperforms" cannot be evaluated without these numbers and the associated statistical tests.
- **Why it matters** This is the core methodological claim of the paper. Without quantitative evidence, the reader cannot judge whether DeepMEL2 provides a meaningful improvement over existing tools, which is essential for the paper's contribution to the field.
- **Resolution test** Provide the performance metrics (with confidence intervals) for all models on the ASCAV classification task, including the statistical significance of any differences. This should be presented in the main text or a clearly referenced table.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that 15–20% of ASCAVs can be explained by gains or losses of TF binding sites, with AP-1 being dominant.
- **Evidence pointer** Figure 2A–F, Supplemental Tables S10, location not provided.
- **Concern** The enrichment analysis is described, but the actual results (e.g., the list of enriched motifs, the effect sizes, the false discovery rates) are not presented in the text. The claim that AP-1 is dominant is a key finding, but its robustness (e.g., how it varies across cell lines and cell states) is not described.
- **Why it matters** This is a major biological finding of the paper. The reader needs to see the data to understand the strength of the enrichment and to assess whether the conclusion is well-supported. The lack of detail also prevents others from reproducing or building on this analysis.
- **Resolution test** Present the enrichment results in a clear table or figure, including the number of ASCAVs explained per motif family, the statistical significance, and the breakdown by cell state. Discuss the fraction of ASCAVs that remain unexplained and potential reasons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the ASCAV calling pipeline is robust to copy number aberrations by using BaalChIP.
- **Evidence pointer** Methods section "Identification of allele-specific events in ATAC-seq data", Supplemental Figures S3, S4, location not provided.
- **Concern** The description of the ASCAV calling pipeline is high-level. The text states that BaalChIP was used to correct for copy number variation, but the details of how this correction was applied, how the model was parameterized, and how the results were validated are not provided. The supplemental figures are referenced but not available.
- **Why it matters** The accuracy of ASCAV calling is foundational to all downstream analyses. If the pipeline is not robust, all subsequent claims are compromised. The authors need to demonstrate that their approach effectively handles the complexities of cancer genomes (e.g., aneuploidy, subclonality).
- **Resolution test** Provide a detailed description of the ASCAV calling pipeline, including the specific parameters used for BaalChIP, the filtering thresholds, and a validation analysis (e.g., comparison to an independent method or simulation study) demonstrating its accuracy and robustness.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability / Reproducibility
- **Claim pointer** The manuscript claims that augmenting DeepMEL2 with GABPA ChIP-seq data (as a 48th topic) enables identification of TERT promoter mutations.
- **Evidence pointer** Figure 5A–E, location not provided.
- **Concern** This is presented as a final, somewhat separate analysis. The text states that the model "does not predict the oncogenic gains of GABPA sites themselves" before augmentation, but after augmentation, the mutations are identified. The details of this augmentation and the evaluation are not provided. It is unclear if this is a single example or a systematic evaluation across all known TERT mutations.
- **Why it matters** This is a clinically relevant finding, as TERT promoter mutations are common in melanoma. However, the current presentation is more of a case study. A more systematic evaluation would strengthen the claim that this approach can identify oncogenic mutations.
- **Resolution test** Provide a more detailed description of the augmentation strategy and a systematic evaluation of its performance on all known TERT promoter mutations in the dataset, including sensitivity and specificity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided.
- **Issue** The abstract states that "15%–20% can be explained by gains or losses of transcription factor binding sites." This is a key number, but it is not clear if this refers to the fraction of all ASCAVs or a subset. The abstract could be clearer about the denominator.
- **Required correction** Clarify the denominator in the abstract, e.g., "15–20% of all ASCAVs" or "15–20% of ASCAVs in accessible regions."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "A cell state–aware deep learning model can interpret ASCAVs"
- **Evidence pointer** Figure 3D, location not provided.
- **Concern** The text mentions "in silico saturation mutagenesis on the MEL-type IRF4 enhancer" and states it "highlights the outperformance of DeepMEL2 compared with DeepMEL." The specific result (e.g., correlation with experimental data) is not given.
- **Required correction** Provide the quantitative result of this comparison (e.g., correlation coefficient) in the text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "The DeepMEL2 neural network"
- **Evidence pointer** Methods, location not provided.
- **Concern** The description of the model architecture is brief. The text mentions "hybrid CNN-RNN" and "128 convolutional filters" but does not provide details on the number of layers, the size of the LSTM, the training procedure, or the hyperparameters.
- **Required correction** Provide a more complete description of the model architecture and training details, either in the main text or in a supplementary methods section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "Identification of ASCAVs using linked-read genome sequencing and ATAC-seq"
- **Evidence pointer** Figure 1E, location not provided.
- **Concern** The text states that "both early and late variants are detectable as ASCAVs, confirming that our pipelines are robust in the face of copy number changes." This is a qualitative statement. It is not clear if this is a statistical test or a visual inspection of a figure.
- **Required correction** Provide a statistical test or a clear quantitative metric to support the claim of robustness.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data access section
- **Evidence pointer** Data access, location not provided.
- **Concern** The data access statement mentions that WGS data are submitted to EGA, which is appropriate for human data. However, it is not clear if the processed data (e.g., ASCAV calls, model predictions) are available in a more accessible format.
- **Required correction** Consider providing processed data tables (e.g., ASCAV lists, model scores) as supplementary files or in a public repository to facilitate reuse.

## Risk / unsupported claims
- The claim that DeepMEL2 outperforms other models is unsupported without the actual performance metrics.
- The claim that 15–20% of ASCAVs are explained by TF motif changes is unsupported without the enrichment analysis results.
- The claim that the ASCAV pipeline is robust to copy number aberrations is unsupported without the validation data.
- The claim that the augmented model can identify TERT promoter mutations is only supported by a single example and is not systematically evaluated.
- The claim that "a considerable fraction of ASCAVs are caused by changes in AP-1 binding" is supported by the enrichment analysis, but the quantitative details are missing.
- The generalizability of the approach to other cancer types is discussed but not demonstrated.