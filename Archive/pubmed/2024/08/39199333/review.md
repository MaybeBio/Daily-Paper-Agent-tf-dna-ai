## Review setup
- **Input scope** Full manuscript text (review article, ~4,500 words)
- **Assessment boundary** Scientific content, technical accuracy, completeness of coverage, logical coherence, and adherence to review article standards
- **Shared manuscript claim summary** The authors present a review of noncoding cis-regulatory elements (CREs), covering high-throughput identification technologies (primarily MPRA and its variants), deep learning approaches for predicting and designing CREs, and applications in gene therapy, agriculture, and synthetic biology
- **Visible evidence base** Full text with 6 figures referenced, 141 citations listed, abstract, and all sections
- **Missing materials affecting confidence** Figures themselves were not provided for inspection; full reference list not available for verification of citation accuracy; no supplementary materials

## Reviewer
- **Overall assessment** This review provides a broad and generally accurate overview of CRE identification technologies and their applications. The manuscript is well-organized and covers an important and timely topic. However, it suffers from several significant weaknesses: (1) the depth of technical discussion is inconsistent across sections, with some areas treated superficially; (2) the deep learning section lacks critical evaluation of model limitations and comparative performance; (3) several claims are made without adequate supporting evidence or citations; (4) the manuscript contains some inaccuracies and oversimplifications that could mislead readers; and (5) the "Conclusions and Overlook" section is notably thin and does not synthesize the material effectively. The review would benefit from substantial revision to meet the standards expected of a high-quality review article in this field.

- **Who would be interested in the results, and why** Researchers in functional genomics, regulatory genomics, and gene regulation would find this review useful as an entry point to MPRA technologies and their applications. Computational biologists working on regulatory sequence prediction may find the deep learning section of interest, though they would likely find it too superficial. Researchers in gene therapy, agricultural genomics, and synthetic biology may find the applications sections relevant to their work. Graduate students and early-career researchers seeking an overview of CRE identification and design would be the primary audience.

- **Major strengths** (1) The manuscript covers a timely and important topic with broad relevance across multiple disciplines. (2) The organization is logical, progressing from identification technologies to computational prediction to applications. (3) The MPRA section provides a useful catalog of technology variants and their specific applications. (4) The inclusion of silencer and insulator identification, which are often overlooked in similar reviews, adds value. (5) The discussion of MPRA limitations in Section 2.8 is practical and reflects hands-on experience.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "deep learning models for predicting and designing regulatory elements require continuous development and adjustment of algorithms, as well as more high-quality experimental data to expand the training sets and improve prediction accuracy" (Section 4.4), and Section 3 broadly claims that deep learning models can "accurately predict activity" of CREs.
- **Evidence pointer** Section 3, Sections 3.1-3.4
- **Concern** The deep learning section is substantially underdeveloped relative to the MPRA section. It reads as a catalog of model names (DeepBind, DeepSEA, Basset, Enformer, DeepSTARR, FactorNet, DeepMARS, Xpresso, etc.) with minimal technical depth. Critically, the manuscript does not provide: (a) a comparative assessment of model performance across different tasks; (b) discussion of the fundamental limitations of these models (e.g., sequence length constraints, training data biases, transferability across cell types and species); (c) the relationship between model architecture choices and biological questions; or (d) validation strategies for de novo designed CREs. The claim that these models "accurately predict" CRE activity is presented without critical examination of what "accurate" means in this context, what benchmarks were used, or how prediction accuracy varies across genomic contexts. The section on challenges (3.4) is generic and could apply to any deep learning application in genomics.
- **Why it matters** A review that claims to cover "prediction and de novo design" of CREs must provide readers with sufficient technical depth to understand the state of the art, the reliability of current methods, and the key open problems. Without this, the review fails to serve as a useful resource for researchers deciding which computational approaches to use or how to interpret their outputs. The superficial treatment risks giving readers an overly optimistic view of current predictive capabilities.
- **Resolution test** The authors should expand Section 3 to include: (a) a table comparing model architectures, training data, tasks, and reported performance metrics; (b) a critical discussion of model limitations with specific examples; (c) a description of how de novo designed CREs are validated experimentally; and (d) a more nuanced discussion of the gap between in silico prediction and in vivo function.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / Completeness
- **Claim pointer** The manuscript claims to provide "an overview of high-throughput technologies for identifying CREs" (Section 1) and discusses "potential applications of noncoding regulatory elements in various fields" (Section 1).
- **Evidence pointer** Sections 2, 4
- **Concern** The review omits several important topics that would be expected in a comprehensive review of CRE identification and design. Specifically: (a) CRISPR-based screens for regulatory element function (e.g., CRISPRi, CRISPRa, tiling screens) are mentioned only in passing in the context of applications, not as identification technologies; (b) the growing literature on enhancer-promoter interactions and 3D genome organization as it relates to CRE function is barely touched; (c) the emerging field of single-cell epigenomics (scATAC-seq, sc-methylation) for CRE identification is not discussed; (d) the application section on agriculture is thin and does not adequately cover the substantial literature on livestock and crop regulatory genomics; (e) the discussion of synthetic biology applications is speculative and lacks concrete examples of successful CRE engineering in microbial systems. The manuscript also does not discuss the important question of how CREs are defined and annotated across different cell types and developmental stages, which is a major challenge in the field.
- **Why it matters** For a review to be valuable, it must provide comprehensive coverage of the topic or clearly delimit its scope. The current manuscript implies broad coverage but delivers selective coverage. Readers in the CRISPR screening or single-cell genomics communities would find the review incomplete, and the omission of these topics weakens the review's utility as a reference.
- **Resolution test** The authors should either (a) expand the review to include these topics, or (b) clearly state the scope and limitations of the review in the introduction, explaining why certain technologies were excluded. If the review is intended to focus specifically on MPRA and deep learning, this should be stated explicitly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** Section 2.3 states that "for enhancer identification, weak promoters or elements with inherently low promoter activity are preferred to enhance the sensitivity of detection" and that "robust promoters, such as phosphoglycerate kinase (PGK) or super core promoter 1 (SCP1), are indispensable for the effective identification of silencers."
- **Evidence pointer** Section 2.3
- **Concern** The discussion of silencer identification via MPRA is oversimplified and contains potential inaccuracies. The claim that strong promoters are "indispensable" for silencer identification is too absolute; the choice of promoter strength depends on the specific biological question and the sensitivity of the detection system. Additionally, the manuscript does not discuss the important issue of context-dependence in silencer function, nor does it address the challenges of distinguishing true silencers from other repressive elements or from artifacts of the assay system. The statement that "the promoter activity of the ORI element in the ORI-STARR-seq backbone is quite weak, which may result in some false positives when identifying silencers" is presented without sufficient context or explanation of why this would cause false positives specifically.
- **Why it matters** Silencer biology is an area of active research with significant technical challenges. An oversimplified treatment could mislead readers about the reliability of silencer identification and the interpretation of MPRA results for repressive elements.
- **Resolution test** The authors should provide a more nuanced discussion of silencer identification, including the trade-offs in promoter choice, the issue of context-dependence, and the specific technical challenges and potential artifacts in silencer MPRA.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Readability for nonspecialists
- **Claim pointer** The abstract states that "A deeper understanding of CRE operational dynamics is crucial for harnessing their versatile regulatory properties" and the manuscript aims to provide an overview accessible to a broad audience.
- **Evidence pointer** Abstract, Sections 2, 3
- **Concern** The manuscript assumes significant prior knowledge of genomics and molecular biology. Terms such as "CUT&RUN," "CUT&Tag," "Hi-ChIP," "massively parallel reporter assay," and various deep learning architectures are introduced with minimal explanation. For example, the difference between MPRA and STARR-seq is not clearly explained for a reader unfamiliar with both techniques. The figures are referenced but not described in sufficient detail in the text to be understood without viewing them. The manuscript would benefit from a glossary of terms, more careful introduction of acronyms, and clearer explanations of how the different technologies relate to one another.
- **Why it matters** The stated goal of the review is to provide an overview for researchers across "life sciences, genetic evolution, disease treatment, and animal husbandry and breeding." Readers from these diverse fields will have varying levels of familiarity with the technical methods described. Without adequate context, the review will be accessible only to specialists in regulatory genomics.
- **Resolution test** The authors should revise the manuscript to include brief explanations of key technologies when first introduced, add a glossary or table of acronyms, and ensure that the relationship between different methods is clearly explained.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** Section 4.4 states that "The study of noncoding functional CREs is intensely active, and a plethora of experimental and analytical methods are continuously being developed" and the manuscript concludes with expectations of "significant breakthroughs in an increasing number of areas."
- **Evidence pointer** Section 4.4
- **Concern** The concluding section is disproportionately brief relative to the scope of the review. It does not synthesize the material presented, does not identify key open questions or controversies in the field, and does not provide a forward-looking perspective that would help readers understand where the field is heading. The discussion of applications in Section 4 is also uneven: the gene therapy section is reasonable, but the agriculture and synthetic biology sections are thin and lack concrete examples or critical assessment of challenges. The conclusion reads as an afterthought rather than a substantive synthesis.
- **Why it matters** A strong conclusion is essential for a review article. It should integrate the material presented, highlight the most important advances and remaining challenges, and provide guidance for future research. The current conclusion fails to do this, diminishing the overall impact of the review.
- **Resolution test** The authors should substantially expand Section 4.4 to include: (a) a synthesis of the key themes from Sections 2 and 3; (b) a discussion of the most important open questions in the field; (c) a critical assessment of the challenges that need to be overcome; and (d) a more detailed and concrete discussion of future directions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 2.2, statement about STARR-seq
- **Evidence pointer** Section 2.2
- **Issue** The manuscript states that STARR-seq was "first applied to map enhancer activity throughout the Drosophila genome" but does not provide the citation for this seminal work in the text (citation [38] is listed but not discussed in context).
- **Required correction** Add the citation in the appropriate place in the text and briefly describe the significance of this landmark study.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.6, discussion of 3' UTR MPRA
- **Evidence pointer** Section 2.6
- **Issue** The discussion of 3' UTR MPRA systems does not mention the important distinction between assays that measure mRNA stability versus those that measure translation efficiency. The Fast-UTR system is mentioned but not clearly distinguished from other approaches.
- **Required correction** Clarify the different types of information that can be obtained from 3' UTR MPRA and how different assay designs address different questions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 3.1, description of deep learning models
- **Evidence pointer** Section 3.1
- **Issue** The description of the "5' UTR language model" is vague and does not explain what makes it a "language model" in the technical sense. This is a potentially confusing usage of the term for readers familiar with language models in NLP.
- **Required correction** Either explain the technical meaning of "language model" in this context or use a different term.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 4.1, gene therapy discussion
- **Evidence pointer** Section 4.1
- **Issue** The discussion of gene therapy applications is somewhat generic and does not provide specific examples of how CRE optimization has been applied or what the current limitations are.
- **Required correction** Add specific examples of CRE-based gene therapy approaches and discuss the challenges that remain.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 4.2, agriculture discussion
- **Evidence pointer** Section 4.2
- **Issue** The statement that "a breakthrough study by Song et al. used CRISPR-Cas9 to induce a 54-bp deletion in the rice IPA1 gene promoter, which simultaneously increased tiller number and panicle size" is presented without critical discussion of the broader applicability of this approach or its limitations.
- **Required correction** Provide more context for this example and discuss whether similar approaches have been successful in other crops or livestock.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.8, limitations of MPRA
- **Evidence pointer** Section 2.8
- **Issue** The discussion of MPRA limitations does not mention the issue of assay context (e.g., plasmid-based assays versus genomic context) or the potential for position effects and copy number effects to influence results.
- **Required correction** Add discussion of these important technical limitations.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.1, MPRA promoter
- **Evidence pointer** Section 2.1
- **Issue** The description of the MPRA promoter assay would benefit from a clearer explanation of how the input-to-output ratio is calculated and what it represents biologically.
- **Required correction** Add a brief explanation of the normalization and analysis approach.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 3.2, model interpretability
- **Evidence pointer** Section 3.2
- **Issue** The statement that deep learning models are "misunderstood as opaque 'black boxes'" is presented without discussing the specific interpretability methods that have been developed (e.g., attribution methods, in silico mutagenesis) or their limitations.
- **Required correction** Provide a brief discussion of interpretability methods and their limitations.

- **Technical failings that need to be addressed before the case is established** The manuscript does not present original research, so the standard of "case established" applies to the review's completeness and accuracy. The following technical issues need to be addressed: (1) the deep learning section needs substantial expansion with critical evaluation of model performance and limitations; (2) the review omits important topics (CRISPR screens, single-cell epigenomics) that should either be included or explicitly scoped out; (3) several claims in the applications sections need more specific examples and critical assessment; (4) the conclusion needs to be substantially expanded to provide synthesis and forward-looking perspective.

- **Assessment against Nature-style criteria**
  - **Originality**: The review does not present original research or a novel conceptual framework. Its originality lies in the specific combination of topics covered (MPRA technologies, deep learning, and applications), though this combination is not unique in the recent review literature.
  - **Scientific importance**: The topic is of high importance given the growing recognition of the role of noncoding regulatory elements in disease, evolution, and biotechnology. However, the review's importance is diminished by incomplete coverage and insufficient critical depth.
  - **Interdisciplinary readership**: The topic has potential appeal across genomics, molecular biology, computational biology, and applied fields. However, the current presentation is likely to be accessible primarily to specialists in regulatory genomics, limiting its interdisciplinary reach.
  - **Technical soundness**: The MPRA sections are generally accurate, though some statements are oversimplified. The deep learning section lacks technical depth and critical evaluation. Several claims lack adequate supporting evidence.
  - **Readability for nonspecialists**: The manuscript assumes substantial background knowledge and would benefit from more careful introduction of technical concepts and a glossary of terms.

- **Recommendation posture** The manuscript has potential value as a review of MPRA technologies and their applications, but it requires substantial revision to address the major concerns identified. The deep learning section needs significant expansion and critical evaluation, the coverage needs to be either broadened or explicitly scoped, and the conclusion needs to be substantially strengthened. I would be supportive of the manuscript if these concerns are addressed, but in its current form, the review does not provide the comprehensive and critical treatment expected of a high-quality review in this field.

## Risk / unsupported claims
- The claim that "more than 90% of genetic variation lies within these noncoding regions" (Section 1) is presented without qualification; this statistic depends on how "genetic variation" is defined and the specific GWAS catalog used.
- The statement that "the promoter activity of the ORI element in the ORI-STARR-seq backbone is quite weak, which may result in some false positives when identifying silencers" (Section 2.3) is presented without supporting data or citation.
- The claim that "deep learning models... accurately predict activity" (Section 3) is too broad and not supported by specific performance metrics or benchmarks.
- The statement that "optimizing regulatory elements... can significantly boost the transcription and expression levels of introduced genes" (Section 4.1) is presented without specific examples or quantitative evidence.
- The claim that "a breakthrough study by Song et al. used CRISPR-Cas9 to induce a 54-bp deletion in the rice IPA1 gene promoter, which simultaneously increased tiller number and panicle size, thus overcoming the inherent trade-offs" (Section 4.2) is presented without critical discussion of reproducibility or broader applicability.
- The statement that "future research could enable the custom design of CREs that are responsive to temperature, light, and pH" (Section 4.3) is speculative and not grounded in specific current research directions.
- The manuscript claims to provide "an overview of high-throughput technologies for identifying CREs" but omits several important technologies (e.g., CRISPR screens, single-cell ATAC-seq), making the coverage claim unsupported.