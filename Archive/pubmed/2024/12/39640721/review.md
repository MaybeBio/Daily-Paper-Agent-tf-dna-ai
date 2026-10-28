## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Methods, Results, Discussion, Conclusion, and supplementary file descriptions)
- **Assessment boundary** Scientific content, methodological rigor, reproducibility, and claims as presented in the provided manuscript text. No independent verification of data or code was performed.
- **Shared manuscript claim summary** The authors present a comprehensive comparative evaluation of computational tools for plant transcription factor binding region (TFBR) discovery, covering three stages: peak calling, TFBR identification, and motif discovery. They report that most existing tools, including those claimed to be plant-specific, perform poorly in cross-species applications, with PTFSpot emerging as the only reliable tool for cross-species TFBR identification. They also propose a redefinition of TFBS as "binding region marker motifs" and provide corrected scripts for buggy tools.
- **Visible evidence base** Figures 1-11, Tables 1-4, Supplementary Materials S1-S5 (referenced but not fully provided), GitHub repository link
- **Missing materials affecting confidence** Supplementary data files (S1-S5) are referenced extensively but not provided in the submitted material. The GitHub repository contents were not independently verified. Detailed numerical results (e.g., performance metrics tables) are not fully visible in the text. The specific datasets used for Dataset "A" construction are not fully enumerated.

## Reviewer

- **Overall assessment** This manuscript addresses an important gap in plant bioinformatics: the systematic evaluation of computational tools for TFBR discovery, with a focus on cross-species applicability. The authors have undertaken a substantial benchmarking effort across 19 tools and three computational stages, and they identify a critical issue: most tools fail in cross-species scenarios due to genomic variability. The finding that PTFSpot outperforms all other tools is potentially significant. However, the manuscript has several major weaknesses: the benchmarking methodology is not fully described (e.g., how datasets were split, how hyperparameter optimization was performed for each tool), the results are presented in a largely qualitative manner without rigorous statistical comparisons, and the claim that PTFSpot is the "only" reliable tool requires stronger evidence. The manuscript also contains numerous grammatical errors and unclear passages that impede readability. The proposed redefinition of TFBS as "binding region marker motifs" is conceptually interesting but not sufficiently developed or justified.
- **Who would be interested in the results, and why** Plant molecular biologists and bioinformaticians working on gene regulation, particularly those involved in TF binding site prediction, genome annotation, and cross-species comparative genomics. The practical guidance on tool selection and the corrected scripts would be valuable to researchers who need to apply these tools. The study also has relevance for developers of computational tools for regulatory genomics, as it highlights the importance of incorporating genomic variability into model design.
- **Major strengths** 1) The manuscript addresses a timely and important problem: the lack of plant-specific tools for TFBR discovery and the poor cross-species performance of existing tools. 2) The scope of the benchmarking is broad, covering 19 tools across three computational stages (peak calling, TFBR identification, motif discovery). 3) The authors identify and fix bugs in existing tools, making them usable for the community, and provide corrected scripts. 4) The analysis of TF structural variability across plant species using AlphaFold2 is a novel and valuable contribution. 5) The recommendation to decouple motif discovery from TFBR discovery is conceptually sound and aligns with recent advances in the field.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that PTFSpot outperforms all other tools across all datasets and metrics, and that it is the only tool suitable for cross-species TFBR identification.
- **Evidence pointer** Figure 8, Supplementary Table S4
- **Concern** The claim of PTFSpot's superiority is based on a single figure (Fig. 8) and supplementary tables that are not fully visible in the provided text. The manuscript does not provide statistical tests (e.g., significance testing, confidence intervals) to support the claim that PTFSpot's performance is significantly better than other tools. Furthermore, the benchmarking methodology is not fully described: it is unclear how hyperparameter optimization was performed for each tool (e.g., whether the same search space was used, how many trials, what metric was optimized), and whether the tools were evaluated on the same train/test splits. Without this information, the comparative results are difficult to interpret or reproduce.
- **Why it matters** The central conclusion of the manuscript rests on the claim that PTFSpot is uniquely reliable. If this claim is not rigorously supported, the manuscript's main contribution is weakened. The lack of statistical rigor and methodological detail undermines the credibility of the benchmarking results.
- **Resolution test** Provide a detailed description of the benchmarking protocol, including dataset splits, hyperparameter optimization procedure for each tool, and the number of independent runs. Report performance metrics with confidence intervals and perform statistical significance testing (e.g., paired tests) to support the claim of PTFSpot's superiority. Make the full results tables available in the main text or supplementary materials.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that they fixed bugs in existing tools and provide corrected scripts at a GitHub repository.
- **Evidence pointer** GitHub link, Supplementary Material S3
- **Concern** The manuscript does not provide a clear description of the bugs found, the fixes applied, or how the corrected scripts were validated. The GitHub repository is mentioned but its contents are not described in the manuscript. Without a detailed changelog or validation results, it is impossible for readers to assess whether the fixes are correct and whether the corrected tools produce reliable results.
- **Why it matters** The provision of corrected scripts is a claimed contribution of the manuscript. If the fixes are not documented and validated, this contribution cannot be evaluated or trusted by the community.
- **Resolution test** Provide a supplementary document detailing each bug found, the specific fix applied, and the validation results (e.g., comparison of outputs before and after the fix on a test dataset). Ensure the GitHub repository includes a README with clear instructions and a versioned release.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors propose redefining TFBS as "binding region marker motifs" and argue that motif discovery should be decoupled from TFBR discovery.
- **Evidence pointer** Section "Need to redefine the transcription factors binding sites (TFBS) as binding region marker motifs", Figure 10
- **Concern** The conceptual argument for redefining TFBS is interesting but not well-developed. The authors do not provide a clear operational definition of "binding region marker motifs" or explain how this redefinition would change practical analysis workflows. The evidence presented (Fig. 10) shows that tools vary in their sensitivity to input data size and their agreement with experimentally reported motifs, but this does not directly support the need for a redefinition. The distinction between TFBS and "marker motifs" is not clearly articulated.
- **Why it matters** This is presented as a key conceptual contribution of the manuscript. If the redefinition is not clearly justified and operationalized, it may be seen as a semantic change rather than a substantive contribution.
- **Resolution test** Provide a clear, operational definition of "binding region marker motifs" with specific criteria for how they differ from traditional TFBS. Explain how this redefinition would affect downstream analyses (e.g., motif scanning, genome annotation). Provide concrete examples demonstrating the practical utility of the proposed redefinition.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "most of the CNN and ML approach" tools performed poorly, and that tools using advanced deep learning (transformers, DenseNet) performed better.
- **Evidence pointer** Figure 8, Section "Performance across different validated datasets"
- **Concern** The manuscript does not provide a clear analysis of why certain architectures perform better than others. The comparison is confounded by differences in training data, hyperparameter optimization, and the specific datasets used. For example, PTFSpot and TSPTFBS 2.0 were trained on plant-specific data, while many other tools were trained on human data. The authors note that animal-based tools performed well when retrained on plant data, but this observation is not systematically explored. The manuscript would benefit from a more controlled comparison, e.g., training all tools on the same data with the same hyperparameter optimization protocol.
- **Why it matters** The manuscript aims to provide guidance on tool selection. If the reasons for performance differences are not understood, the guidance may be misleading.
- **Resolution test** Perform a more controlled comparison where all tools are trained on the same data with the same hyperparameter optimization protocol. Analyze the contribution of architecture, training data, and feature encoding to performance differences.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Readability for nonspecialists
- **Claim pointer** The manuscript claims to be a "comprehensive study" and a "guide" for researchers.
- **Evidence pointer** Entire manuscript
- **Concern** The manuscript is difficult to follow in several places. There are numerous grammatical errors and unclear sentences (e.g., "The reason is an argument that in actual condition imbalanced distribution of the positive and negative instances happens"). The organization of the results section is confusing, with overlapping descriptions of datasets and performance metrics. The figures are not well integrated into the text, and the reader is often left to interpret complex figures without sufficient guidance. The manuscript would benefit from a thorough editing pass and a clearer structure.
- **Why it matters** The manuscript is intended to serve as a guide for plant biologists, who may not be experts in machine learning. If the text is not clear and well-organized, the practical value of the manuscript is diminished.
- **Resolution test** Revise the manuscript for clarity and conciseness. Ensure that each figure is clearly explained in the text. Provide a summary table of tools, their features, and recommended use cases. Have the manuscript reviewed by a researcher who is not an expert in computational biology.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is overly long and contains too much detail about the specific tools and datasets. It does not clearly state the main findings and recommendations.
- **Required correction** Shorten the abstract and focus on the key findings: (1) most tools fail in cross-species applications, (2) PTFSpot is the most reliable tool, (3) the importance of considering genomic variability, and (4) the availability of corrected scripts.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Section "Dataset for transcription factor binding regions"
- **Issue** The description of Dataset "B" construction is incomplete. The authors state that they used DAP-seq data for 265 TFs from the Plant Cistrome Database, but do not specify the exact data processing steps (e.g., how peaks were called, how positive and negative instances were defined, what sequence lengths were used).
- **Required correction** Provide a detailed step-by-step description of the dataset construction process, including all parameters and thresholds used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results
- **Evidence pointer** Section "Performance benchmarking using transcription factor ChIP-seq data"
- **Issue** The authors state that "LanceOtron emerged as the top performer" for peak calling, but the criteria for "top performer" are not clearly defined. It is unclear whether this is based on the number of peaks, overlap with experimental data, or other metrics.
- **Required correction** Clearly define the evaluation criteria for peak calling tools and report all relevant metrics (e.g., precision, recall, F1-score) for each tool.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Section "Discussion"
- **Issue** The discussion section is largely a repetition of the results and does not provide a critical analysis of the findings. The authors do not discuss the limitations of their study or the implications of their findings for future research.
- **Required correction** Rewrite the discussion to critically evaluate the findings, discuss limitations (e.g., the limited number of plant species and TFs), and propose future directions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Section "Data and code availability"
- **Issue** The authors state that all data are available in supplementary files, but the supplementary files are not provided in the submitted material. The GitHub repository link is given, but its contents are not described.
- **Required correction** Ensure that all supplementary files are provided with the manuscript and that the GitHub repository is fully documented and accessible.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods
- **Evidence pointer** Section "Performance evaluation strategies for TFBRs identification software tools"
- **Issue** The authors state that "default parameters were considered for Dataset 'A'" but do not specify what these default parameters are for each tool. This makes it difficult to reproduce the results.
- **Required correction** Provide a table listing the default parameters for each tool, or provide a reference to where these parameters are documented.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results
- **Evidence pointer** Section "Most of the tools have limited practical utility due to poor cross-species performance"
- **Issue** The authors state that "10 out of the total of 14 software tools merely attained an average accuracy value between 50% and 60%", but it is unclear which 14 tools are being referred to (the text mentions 16 tools were tested on Dataset "C").
- **Required correction** Clarify the number of tools tested on Dataset "C" and provide a clear list of which tools were included and which were excluded, with reasons for exclusion.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results
- **Evidence pointer** Section "Need to redefine the transcription factors binding sites (TFBS) as binding region marker motifs"
- **Issue** The authors state that "PTF-Vāc was able to discover the motifs regardless of the number of input sequences," but this claim is based on a single figure (Fig. 10A) and is not supported by quantitative data.
- **Required correction** Provide quantitative results (e.g., number of motifs discovered, similarity scores) for each tool at different input data sizes, and perform statistical tests to support the claim.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction is overly long and contains too much background information that is not directly relevant to the study. The authors should focus on the specific problem of plant TFBR discovery and the need for a comparative evaluation.
- **Required correction** Shorten the introduction and focus on the specific aims of the study.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods
- **Evidence pointer** Section "Dataset for transcription factors binding motif identification"
- **Issue** The authors state that they selected 10 TFs for motif identification based on "the availability of high-quality and highest number of peaks," but do not provide the criteria for "high-quality" or the specific number of peaks for each TF.
- **Required correction** Provide a table listing the 10 TFs, the number of peaks for each, and the criteria used for selection.

- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical rigor of benchmarking), R1-M2 (documentation of bug fixes), R1-M4 (confounded comparison of tools), R1-M3 (unclear conceptual contribution), R1-M5 (readability).

- **Assessment against Nature-style criteria** 
  - **Originality**: The manuscript addresses a relevant problem, but the approach is largely a benchmarking study of existing tools. The conceptual contribution (redefining TFBS) is not sufficiently developed to be considered highly original. The use of AlphaFold2 to analyze TF structural variability is a novel element.
  - **Scientific importance**: The problem of cross-species TFBR discovery in plants is important, and the finding that most tools fail in this context is significant. However, the manuscript does not provide a clear solution to this problem, beyond recommending PTFSpot.
  - **Interdisciplinary readership**: The manuscript is primarily of interest to plant bioinformaticians and molecular biologists. It is unlikely to attract a broad interdisciplinary readership.
  - **Technical soundness**: The benchmarking methodology has significant weaknesses, as described in R1-M1 and R1-M4. The lack of statistical rigor and the confounded comparison undermine the technical soundness of the study.
  - **Readability for nonspecialists**: The manuscript is not well-written and would be difficult for nonspecialists to follow. The organization is confusing, and there are numerous grammatical errors.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an important problem and has the potential to be a valuable resource for the plant bioinformatics community. However, the major methodological weaknesses, particularly the lack of statistical rigor and the confounded comparison, prevent the main claims from being fully supported. The manuscript would require substantial revisions, including a more rigorous benchmarking methodology, a clearer description of the bug fixes, and a more developed conceptual framework, before it could be considered for publication.

## Risk / unsupported claims
- The claim that PTFSpot is the "only" reliable tool for cross-species TFBR identification is not fully supported by the evidence presented, as the benchmarking methodology is not fully described and no statistical tests are performed.
- The claim that "most of the CNN and ML approach" tools performed poorly is confounded by differences in training data and hyperparameter optimization.
- The claim that PTF-Vāc is "immune to data-volume sensitivity" is based on a single figure and is not supported by quantitative data.
- The claim that the authors "fixed" bugs in existing tools is not verifiable without a detailed description of the bugs and fixes.
- The proposed redefinition of TFBS as "binding region marker motifs" is not clearly defined or operationalized.
- The statement that "10 out of the total of 14 software tools" performed poorly on Dataset "C" is unclear, as the text mentions 16 tools were tested.