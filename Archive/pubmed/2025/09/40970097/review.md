## Review setup
- **Input scope** Full manuscript text (abstract, main text, figure description, references cited within text)
- **Assessment boundary** Scientific content, technical accuracy, completeness of the computational methods described, and alignment with the stated aims of a review article
- **Shared manuscript claim summary** The manuscript presents a narrative review of computational approaches for analyzing hematopoietic stem cell (HSC) genomics and transcriptomics, covering scRNA-seq, ChIP-seq, network inference, and machine learning, and argues that these tools collectively enable the discovery of novel HSC subtypes, regulatory factors, and therapeutic targets.
- **Visible evidence base** The manuscript text, including the abstract, introduction, sections 2 through 7, author contributions, conflict of interest statement, generative AI statement, abbreviations, and acknowledgements. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** Figure 1 (referenced in the Introduction and Section 2) and Table 1 (referenced in Section 3) were not provided. No reference list was provided, so the accuracy and relevance of cited works could not be verified. No original data or code were provided, which is expected for a review but limits assessment of any novel claims.

## Reviewer
- **Overall assessment** This is a broad, descriptive review of computational methods applied to HSC biology. The manuscript is clearly written and covers a reasonable range of tools and techniques. However, it lacks critical depth: it does not compare methods quantitatively, does not discuss limitations or failure modes of the described approaches, and does not provide a critical synthesis of the field. The case study in Section 6.3 is confusingly described and appears to conflate two different studies. The absence of figures and tables in the provided material makes it impossible to evaluate the claimed framework and tool summaries. The review would be of interest to newcomers to the field but does not currently offer sufficient analytical insight for a specialist audience.
- **Who would be interested in the results, and why** Early-career researchers, graduate students, and experimental hematologists seeking an introductory overview of computational tools for HSC data analysis would find this review useful as a starting point. Computational biologists entering the hematopoiesis field might also use it as a survey of available methods. However, specialists in either computational method development or HSC biology are unlikely to find new information or critical evaluation.
- **Major strengths** The manuscript is well-organized and readable. It covers a logical progression from data generation (scRNA-seq, ChIP-seq) to analysis (network inference, machine learning). The inclusion of specific tool names and example applications provides a useful entry point for readers. The emphasis on integration of multi-omics data is timely and appropriate.
- **Major Concerns** The concerns below identify issues that, if unaddressed, prevent the manuscript from making a substantive contribution to the review literature.
- **Minor Comments** The minor comments below address clarity, consistency, and presentation issues that should be corrected.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing figures and tables), R1-M2 (conflated case study), R1-M3 (uncritical method description), R1-M4 (unverifiable references).
- **Assessment against Nature-style criteria**  
  *Originality*: Low. The manuscript does not present a new framework, dataset, or critical synthesis. It is a descriptive catalog of existing methods.  
  *Scientific importance*: Moderate. The topic is important, but the treatment is superficial and does not advance understanding of how to choose or combine methods.  
  *Interdisciplinary readership*: Limited. The manuscript is aimed at a narrow audience of HSC researchers and does not frame the computational challenges in a way that would attract a broader computational or clinical readership.  
  *Technical soundness*: Weak. The description of methods is generally accurate but lacks critical evaluation. The case study in Section 6.3 is internally inconsistent.  
  *Readability for nonspecialists*: Acceptable. The prose is clear, but the lack of figures and tables in the provided material reduces accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial revision to address the missing materials, correct the case study, and add critical depth before it can be considered a valuable review.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Completeness of evidence  
- **Claim pointer** The Introduction states that "Figure 1 presents a comprehensive framework for unraveling the complexity of HSC regulation by integrating multi-omics data with advanced computational pipelines." Section 3 states that "Table 1 outlines the fundamental computational processes involved in analyzing scRNA-seq data and the commonly employed tools for HSC-specific research."  
- **Evidence pointer** Figure 1 and Table 1 are referenced but not provided in the submitted material.  
- **Concern** The manuscript relies on Figure 1 and Table 1 to convey the central framework and tool summaries, respectively. Without these materials, the reader cannot evaluate whether the framework is comprehensive or whether the tool selection is appropriate.  
- **Why it matters** The review's value depends on the accuracy and completeness of its visual and tabular summaries. Their absence makes the core claims unverifiable.  
- **Resolution test** Provide Figure 1 and Table 1 in the revised submission. The figure should clearly depict the integration pipeline described in the text, and the table should list tools with their specific applications to HSC data.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Internal consistency  
- **Claim pointer** Section 6.3 states: "A complete machine learning pipeline was demonstrated in a study aimed at decoding HSCs based on their morphological features, using microscopy images, enabling rapid identification of HSCs and progenitor cells (Wang et al., 2024)." The same section then states: "The SVM model was trained and validated using cross-validation techniques after applying a mutual information-based minimum redundancy maximum relevance algorithm for feature selection (Dhal and Azad, 2022)."  
- **Evidence pointer** Section 6.3, location not provided.  
- **Concern** The case study conflates two distinct studies. The first sentence describes a study using microscopy images and morphological features, while the second sentence describes an SVM model with mRMR feature selection, which is a different methodological approach. It is unclear whether these describe the same study or two different ones.  
- **Why it matters** A case study is meant to illustrate a complete pipeline. If the description is inaccurate or conflates sources, the reader cannot trust the presented workflow.  
- **Resolution test** Clarify which study is being described. If the case study is about morphological classification, describe the actual feature extraction and model training steps used in that study. If it is about gene expression data, remove the microscopy reference. Ensure that all citations in this section correspond to the described work.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Critical depth  
- **Claim pointer** The manuscript states in Section 2: "These methods enable in-depth exploration of transcriptional heterogeneity, regulatory mechanisms, and trajectory inference." Section 3.5 states: "DGE analysis has been instrumental in uncovering transcriptional regulators of HSCs associated with differentiation, aging, and lineage commitment."  
- **Evidence pointer** Sections 2 and 3.5, location not provided.  
- **Concern** The manuscript describes what each method can do but does not critically evaluate when one method should be preferred over another, what their limitations are, or how they perform on HSC-specific data. For example, no mention is made of the challenges of dropout in scRNA-seq, the impact of sequencing depth on normalization choices, or the difficulty of validating inferred GRNs.  
- **Why it matters** A review that only lists tools without comparing their strengths and weaknesses does not help readers make informed choices. The stated aim of "deciphering regulatory circuits" requires an understanding of method limitations.  
- **Resolution test** Add a critical comparison subsection for each major method category (scRNA-seq, ChIP-seq, network inference, machine learning). Discuss at least two limitations per method and suggest criteria for method selection based on data type and biological question.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Reference verification  
- **Claim pointer** The manuscript cites numerous studies throughout, including "Wang et al., 2024" (Sections 2, 6, 6.1.1, 6.3), "Dhal and Azad, 2022" (Sections 6.2.2, 6.3), and "Fidanza et al., 2020" (Section 6).  
- **Evidence pointer** Reference list not provided in the submitted material.  
- **Concern** The reference list was not included in the provided manuscript text. Without it, the accuracy of citations, the relevance of the cited works, and the completeness of the bibliography cannot be assessed.  
- **Why it matters** A review's credibility depends on accurate and complete citations. Unverifiable references undermine trust in the manuscript.  
- **Resolution test** Provide the full reference list in the revised submission. Ensure that every in-text citation appears in the list and that each reference is relevant to the claim it supports.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 3.1, quality control and preprocessing  
- **Evidence pointer** Section 3.1, location not provided.  
- **Issue** The text states: "Cell Ranger evaluates sequencing quality, total read count, and genome-mapping percentages, while Seurat utilizes metrics such as the number of detected genes, UMI counts, and mitochondrial gene content to identify and exclude low-quality cells." This is accurate but does not mention that Cell Ranger also performs UMI counting and generates the feature-barcode matrix, which is described later in the same section.  
- **Required correction** Reorganize the paragraph to avoid redundancy. Either describe Cell Ranger's full pipeline in one place or cross-reference the later description.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Consistency  
- **Affected element** Section 4.2, HSC ChIP-Seq studies  
- **Evidence pointer** Section 4.2, location not provided.  
- **Issue** The text states: "A study employed ChIP-seq to map genome-wide TF occupancy in HSCs subpopulations (Subramanian et al., 2023). MACS2 was used for peak calling and HOMER for motif discovery (Zhang et al., 2008) identified dynamic changes in cis-regulatory landscapes during differentiation." The sentence structure is grammatically awkward and the citation placement is confusing.  
- **Required correction** Rewrite the sentence to clearly attribute the methods to the study. For example: "A study employed ChIP-seq to map genome-wide TF occupancy in HSC subpopulations, using MACS2 for peak calling and HOMER for motif discovery, and identified dynamic changes in cis-regulatory landscapes during differentiation (Subramanian et al., 2023; Zhang et al., 2008)."

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Precision  
- **Affected element** Section 6.1.2, TensorFlow  
- **Evidence pointer** Section 6.1.2, location not provided.  
- **Issue** The text states: "TensorFlow constructs a neural network model to predict gene expression in single HSCs (Athanasiadis et al., 2017)." This is a specific claim about a single study, but it is presented as a general capability of the tool.  
- **Required correction** Clarify that this is an example application, not a built-in feature of TensorFlow. For example: "TensorFlow has been used to construct neural network models for predicting gene expression in single HSCs (Athanasiadis et al., 2017)."

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Section 6.3, case study  
- **Evidence pointer** Section 6.3, location not provided.  
- **Issue** The case study is described in only two sentences and does not provide enough detail for the reader to understand the pipeline, the data used, or the evaluation metrics.  
- **Required correction** Expand the case study to include the dataset description, preprocessing steps, model architecture, training procedure, and evaluation results. If this level of detail is not available, consider removing the case study or replacing it with a more fully described example.

## Risk / unsupported claims
- The claim that "Figure 1 presents a comprehensive framework" is unsupported because the figure was not provided.
- The claim that "Table 1 outlines the fundamental computational processes" is unsupported because the table was not provided.
- The claim in Section 6.3 that a "complete machine learning pipeline" was demonstrated is unsupported because the description conflates two different studies and lacks methodological detail.
- The claim in Section 3.5 that DGE analysis "has been instrumental in uncovering transcriptional regulators of HSCs" is a general statement without specific examples or quantitative evidence in the provided text.
- The claim in Section 7 that "integrating multi-omics datasets with predictive modeling and functional validation is poised to unlock deeper mechanistic insights" is aspirational and not supported by evidence presented in the review.
- The accuracy of all citations cannot be assessed because the reference list was not provided.