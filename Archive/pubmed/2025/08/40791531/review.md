## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, resource availability) as provided.
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and alignment with Nature-style criteria. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors present an integrated framework (CEseek → MPRA → GRACE) to discover, functionally characterize, and model composite DNA elements (CEs) composed of stereospecifically arranged transcription factor motifs. They report a large catalog of CEs with synergistic or antagonistic transcriptional activity, validate a subset via in vivo and in vitro binding data, train a deep learning model (GRACE) on custom MPRA data, and demonstrate convergence with an orthogonal chromatin accessibility model (ChromBPNet). They further apply GRACE to predict functional impacts of autoimmune disease-associated variants.
- **Visible evidence base** Abstract, full introduction, full results section, full discussion, methods (CEseek, MPRA library design and construction, transfections, RNA processing, MPRA data analysis, GRACE architecture and training, enrichment analyses, GWAS variant analysis), resource availability, and acknowledgements. Figures and tables are referenced but not provided. Supplementary tables are referenced but not provided.
- **Missing materials affecting confidence** Figures 1–6 and S1–S7 are not provided, preventing direct evaluation of key data visualizations. Supplementary Tables S1–S12 are not provided, including the full CE catalog, MPRA oligo sequences, and detailed statistical outputs. The GRACE model code is referenced but not reviewed. The ChromBPNet comparison methodology is described but the specific implementation details for the joint analysis are incomplete. The GWAS variant analysis relies on an external dataset (reference 51) that is not described in sufficient detail to assess variant selection and validation criteria.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and ambitious effort to expand the transcriptional regulatory lexicon by systematically identifying and functionally testing composite DNA elements. The integration of computational discovery, high-throughput experimental validation, and deep learning is commendable and addresses a genuine gap in the field. The recovery of known CEs (EICE, AICE) and the identification of numerous novel CEs with functional validation in multiple cell lines are potentially valuable contributions. The convergence between GRACE and ChromBPNet is an interesting finding that suggests biological validity. However, the manuscript as provided has several significant limitations that prevent full assessment. The absence of all figures and supplementary tables is a major barrier. The statistical framework for CE discovery and synergy quantification is not fully described. The MPRA design, while thoughtful, has potential biases that are not fully addressed. The GWAS variant analysis, while promising, is presented with insufficient detail to evaluate its robustness. The claims of "single-nucleotide resolution" and "base pair resolution" for GRACE predictions require more careful justification given the training data and architecture. The discussion of limitations is honest but the overall case for a "lexicon" would be strengthened by clearer evidence that CEs function as discrete, reusable regulatory units beyond the specific contexts tested.

- **Who would be interested in the results, and why** This work will be of interest to researchers in transcriptional regulation, gene regulatory networks, computational genomics, and functional genomics. Specifically, those studying combinatorial TF binding, enhancer logic, and the interpretation of non-coding variants will find the CE catalog and GRACE model potentially useful. The methodological framework (CEseek → MPRA → deep learning) could serve as a template for similar studies in other cell types or organisms. The convergence between transcriptional activity and chromatin accessibility models is relevant to those developing integrative regulatory genomics approaches. The application to autoimmune disease variants may attract interest from the human genetics community.

- **Major strengths**
  1. The integrated framework combining computational discovery, experimental validation, and deep learning is a significant methodological advance.
  2. The scale of the analysis (5,063 CEs, 60,714 MPRA sequences, three cell lines) is impressive.
  3. The recovery of known CEs validates the approach, and the identification of novel CEs with synergistic activity extends the known regulatory lexicon.
  4. The convergence between GRACE and ChromBPNet, trained on orthogonal data types, provides cross-validation of the expanded lexicon.
  5. The application to disease-associated variants demonstrates practical utility and potential clinical relevance.
  6. The authors are transparent about limitations and provide resources (code, data) for community use.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims identification of 5,063 high-confidence CEs and functional validation of 893 activating CEs across three cell lines.
- **Evidence point** Figures 2–3, Supplementary Tables S1, S3–S5 (referenced but not provided)
- **Concern** The core results of this manuscript are presented in figures and supplementary tables that are not included in the provided material. Without these, it is impossible to evaluate the quality of the CE discovery, the MPRA data, the statistical significance of the findings, or the validity of the synergy classifications. The text alone is insufficient to assess whether the claims are supported by the data.
- **Why it matters** The central claims of the manuscript rest entirely on data that cannot be reviewed. This is a fundamental barrier to assessment.
- **Resolution test** Provide all figures and supplementary tables for review. The CE catalog, MPRA results, and statistical analyses must be fully accessible.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that CEseek identifies statistically enriched CE configurations using Fisher's exact test with a threshold of p < 1e-20, and that 22,698 significant configurations were identified.
- **Evidence point** Methods section "CEseek computational framework" and "Delineation of candidate CEs in ImmGen cis-Regulatory atlas"
- **Concern** The multiple testing burden is substantial: 744,192 possible configurations were tested. The manuscript does not describe how multiple testing correction was applied, if at all. A raw p-value threshold of 1e-20 is extremely stringent, but with this many tests, the expected number of false positives is still non-trivial (744,192 × 1e-20 ≈ 7.4e-15, which is negligible, so this specific threshold may be adequate). However, the later enrichment analyses for MPRA-validated CEs and ChIP-seq comparisons use different thresholds (p < 1e-10, FDR < 0.05) and the correction methods are not described. The synergy quantification method is described only in general terms without a clear statistical model.
- **Why it matters** Without a clear description of multiple testing correction and the statistical model for synergy, the reliability of the CE catalog and the classification of synergistic versus antagonistic interactions cannot be assessed.
- **Resolution test** Provide a detailed description of the statistical framework, including multiple testing correction methods for all analyses, the model used to quantify synergy, and the criteria for classifying CE types.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The manuscript claims GRACE achieves strong predictive performance (Pearson correlation 0.802 in GM12878, 0.813 in K562, 0.766 in Jurkat) and that its learned CWM motifs align with CEseek PWMs at high concordance rates (80.3–95.6%).
- **Evidence point** Results section "Using GRACE to predict TF motif and CE activities across cell types", Figures 5 and S5 (not provided)
- **Concern** The model validation is described but the details are insufficient. The comparison of GRACE predictions to biological replicate correlations is mentioned but the actual numbers are not fully contextualized. The concordance rates between CWMs and PWMs are reported but the methodology for this comparison is not described in sufficient detail. The claim of "single-nucleotide resolution" is not fully justified given that the model is trained on 30-bp sequences with mutations at two consecutive positions. The model's ability to generalize to endogenous sequences, which are longer and more complex, is not fully demonstrated.
- **Why it matters** The GRACE model is a central component of the manuscript. Without rigorous validation and clear description of the evaluation methodology, the reliability of its predictions and the claimed convergence with ChromBPNet cannot be assessed.
- **Resolution test** Provide full details of the model training, hyperparameter selection, validation strategy, and the methodology for comparing CWMs to PWMs. Include the actual correlation values and confidence intervals. Justify the "single-nucleotide resolution" claim with appropriate analyses.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological significance
- **Claim pointer** The manuscript claims that CEs represent a higher-order lexicon in the gene regulatory code and that they enable combinatorial regulatory logic, including AND, AND-NOT, and XOR gates.
- **Evidence point** Results section "Functional characterization of cCEs using a TF-motif MPRA library", Discussion
- **Concern** The classification of CEs into logic gates is based on MPRA activity measurements, but the manuscript does not fully address whether these classifications reflect endogenous regulatory mechanisms. The MPRA uses short 30-bp sequences with a minimal promoter, which may not capture the full context of endogenous enhancers or promoters. The claim that CEs are "widespread" is based on computational prediction, but the functional validation covers only a subset. The biological relevance of the XOR gate, with only a single example, is unclear.
- **Why it matters** The manuscript makes strong claims about the biological importance of CEs. Without evidence that the MPRA-based classifications reflect endogenous regulatory logic, these claims are not fully supported.
- **Resolution test** Provide additional evidence that CE classifications are consistent with endogenous regulatory mechanisms, such as comparisons with endogenous enhancer activity, TF binding, or genetic perturbation data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The manuscript claims the framework is scalable and generalizable, and that the CE catalog will facilitate future studies.
- **Evidence point** Methods, Resource Availability
- **Concern** While the code and data are deposited, the manuscript does not provide sufficient detail for others to reproduce the CEseek pipeline or the GRACE model without significant reverse engineering. The MPRA library construction is described in detail, but the oligo design and selection criteria are not fully specified. The GRACE model architecture is described but the specific hyperparameters, training details, and data preprocessing steps are incomplete.
- **Why it matters** Reproducibility is a core requirement for scientific manuscripts. Without complete methodological details, other groups cannot build on this work.
- **Resolution test** Provide complete methodological details, including all hyperparameters, data preprocessing steps, and a step-by-step guide for running CEseek and GRACE.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence point** Abstract, last sentence
- **Issue** The phrase "enabling joint predictions of motif contributions and the impact of variants on chromatin structure and transcriptional activity in diverse cellular contexts" is vague. It is unclear what "joint predictions" means and how they are made.
- **Required correction** Clarify the nature of the joint predictions and specify the contexts in which they are made.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction, Results
- **Evidence point** Introduction, paragraph 2; Results, "Discovery of Composite Elements using CEseek"
- **Issue** The terms "cCE" and "CE" are introduced but the distinction is not consistently maintained throughout the text. In some places, "CE" is used when "cCE" is meant, and vice versa.
- **Required correction** Ensure consistent use of "cCE" for candidate elements and "CE" for validated elements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results, "Functional characterization of cCEs using a TF-motif MPRA library"
- **Evidence point** Results, paragraph 3
- **Issue** The manuscript reports "893 unique activating CEs" but does not provide a breakdown of how many were tested in each cell line or the overlap between cell lines. This information is important for understanding the cell-type specificity of CEs.
- **Required correction** Provide a summary table or figure showing the number of CEs tested and active in each cell line, with overlaps.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, "GRACE learns genome-wide transcription and chromatin features"
- **Evidence point** Results, paragraph 5
- **Issue** The manuscript states that GRACE predictions align with GRO-cap signals, but the direction of the relationship is not specified. It is unclear whether higher predicted activity corresponds to higher or lower GRO-cap signal.
- **Required correction** Specify the direction of the correlation and its biological interpretation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence point** Discussion, paragraph 4
- **Issue** The discussion of limitations is honest but does not address the potential for false positives in the CE catalog due to the computational discovery method. The authors note that not all CEs were functionally validated, but they do not estimate the false discovery rate.
- **Required correction** Add a discussion of the potential false discovery rate and how it might affect the interpretation of the CE catalog.

- **Technical failings that need to be addressed before the case is established**
  1. Missing figures and supplementary tables (R1-M1).
  2. Incomplete statistical methodology, particularly for multiple testing correction and synergy quantification (R1-M2).
  3. Insufficient model validation details for GRACE (R1-M3).
  4. Lack of evidence that MPRA-based logic gate classifications reflect endogenous regulatory mechanisms (R1-M4).
  5. Incomplete methodological details for reproducibility (R1-M5).

- **Assessment against Nature-style criteria**
  - **Originality** The concept of systematically expanding the CE lexicon using an integrated computational-experimental-deep learning framework is original and addresses a recognized gap. The specific combination of CEseek, custom MPRA, and GRACE is novel.
  - **Scientific importance** If the claims are fully supported, this work would be important for understanding combinatorial transcriptional regulation and interpreting non-coding variants. The CE catalog could be a valuable community resource.
  - **Interdisciplinary readership** The work bridges computational biology, genomics, and molecular biology. The findings are relevant to researchers in gene regulation, functional genomics, and human genetics. The potential application to disease variants broadens the appeal.
  - **Technical soundness** The technical approach is generally sound, but the lack of methodological detail and missing data prevent full assessment. The statistical framework and model validation need to be more rigorous and transparent.
  - **Readability for nonspecialists** The manuscript is well-written and accessible. The concepts are introduced clearly, and the flow from discovery to validation to modeling is logical. However, the density of information in the results section may be challenging for nonspecialists.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a potentially important framework and findings, but the absence of all figures and supplementary tables, combined with incomplete methodological details, prevents a full assessment. The authors should be invited to resubmit with complete data and methods. If the data support the claims, this could be a significant contribution.