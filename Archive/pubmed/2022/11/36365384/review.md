## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the manuscript
- **Shared manuscript claim summary** The manuscript reports that tomato hybrids VRTH-16-3 and VRTH-17-68 exhibit superior drought tolerance, characterized by lower electrolytic leakage, higher relative water content, enhanced proline accumulation, increased antioxidant enzyme activity, and upregulation of NAC and stress-defence genes. The authors also present in silico structural and functional characterization of the SlNAC1 protein, including homology modelling, DNA docking, and protein-protein interaction analysis.
- **Visible evidence base** Full text including abstract, introduction, results, discussion, methods, and conclusions. Figures and tables are referenced but not fully visible in the provided material. Supplementary materials are mentioned but not provided.
- **Missing materials affecting confidence** Figures 1-7, Tables 1-5, and all Supplementary Materials (Figures S1-S5, Tables S1-S2) are referenced but not available for inspection. Statistical details (e.g., exact p-values, error bars, replication numbers) are not fully reported in the text. Primer sequences are only listed in Supplementary Table S2, which is not provided.

## Reviewer

- **Overall assessment** The manuscript addresses a relevant topic in crop stress biology, combining physiological, biochemical, and bioinformatic approaches to evaluate NAC transcription factor involvement in drought tolerance in tomato hybrids. The physiological data, if accurately reported, support the identification of two drought-tolerant hybrids. However, the link between the bioinformatic characterization of SlNAC1 and the physiological observations is largely correlative and not experimentally validated. Several methodological details are missing, and the statistical reporting is incomplete. The claim that specific amino acid residues "improve" plant growth and development is not supported by functional evidence. The manuscript would benefit from clearer hypothesis framing, additional experimental validation, and more rigorous statistical presentation.

- **Who would be interested in the results, and why** Plant stress physiologists, tomato breeders, and researchers working on NAC transcription factors in abiotic stress responses. The identification of drought-tolerant tomato hybrids and the expression profiling of stress-related genes may be of practical interest for breeding programs. The bioinformatic characterization of SlNAC1 may interest researchers studying NAC protein structure-function relationships, though the lack of functional validation limits its impact.

- **Major strengths**
  1. The study combines multiple levels of analysis (physiological, biochemical, gene expression, and bioinformatics), providing a broad overview of drought stress responses in tomato hybrids.
  2. The identification of two hybrids (VRTH-16-3 and VRTH-17-68) with consistently superior performance across multiple physiological parameters is a potentially useful finding for breeding programs.
  3. The in silico characterization of SlNAC1, including homology modelling, docking, and interaction network analysis, is reasonably thorough and follows established bioinformatic workflows.
  4. The manuscript is generally well-organized and the writing is clear, making it accessible to a broad plant science audience.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and causal link
- **Claim pointer** The manuscript claims that NAC transcription factors "regulate" redox homeostasis and drought tolerance in tomato hybrids, and that the observed upregulation of NAC genes is a cause of the superior performance of VRTH-16-3 and VRTH-17-68.
- **Evidence pointer** Section 2.11, Figure 7B; Section 3 (Discussion)
- **Concern** The study is purely correlative. The authors measure NAC gene expression and physiological parameters in different hybrids, but no loss-of-function, gain-of-function, or transgenic experiment is performed to demonstrate that NAC genes directly regulate the observed drought tolerance phenotypes. The title and framing imply a functional role, but the evidence does not establish causation.
- **Why it matters** Without functional validation, the central claim that NAC TFs play a regulatory role in redox homeostasis under drought stress is not established. The observed expression changes could be a consequence, not a cause, of differential stress tolerance. This weakens the scientific contribution and the manuscript's ability to support its title and conclusions.
- **Resolution test** The authors should either (a) perform functional experiments (e.g., virus-induced gene silencing, overexpression in tomato or a heterologous system) to demonstrate that altering NAC expression changes drought tolerance or redox parameters, or (b) substantially revise the claims to clearly state that the study is correlative and hypothesis-generating, removing causal language from the title, abstract, and conclusions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and data reporting
- **Claim pointer** The manuscript reports significant differences in physiological parameters (e.g., RWC, electrolytic leakage, proline, catalase) between hybrids and treatments, with percentage changes and ranges provided.
- **Evidence pointer** Section 2.9, Tables 3-4; Section 4.15
- **Concern** The statistical reporting is incomplete. The authors state that two-way ANOVA and Duncan's Multiple Range Test were used, but no F-values, degrees of freedom, exact p-values, or measures of variance (SD/SE) are reported in the text. The tables are not visible in the provided material, so it is impossible to assess whether the claimed differences are statistically robust. Additionally, the number of biological replicates for physiological measurements is not clearly stated (Section 4.15 mentions three biological replicates, but it is unclear if this applies to all assays).
- **Why it matters** The core physiological findings depend entirely on the statistical validity of the comparisons. Without transparent reporting of variance and exact test statistics, the reader cannot evaluate the reliability of the conclusions. This is a fundamental requirement for publication in any scientific journal.
- **Resolution test** The authors must provide full statistical details, including exact p-values, F-statistics, degrees of freedom, and measures of variance for all reported comparisons. The number of replicates for each assay must be explicitly stated. If the data do not meet normality or homoscedasticity assumptions, appropriate non-parametric tests should be used and reported.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Bioinformatic interpretation and overstatement
- **Claim pointer** The manuscript states that DNA docking "discovered that the SlNAC1 protein becomes activated and exerts a stress-defence response after the possible interaction of conserved DNA elements using Pro72, Asn73, Trp81, Lys82, Ala83, Thr84, Gly85, Thr86 and Asp87 residues" (Abstract) and that these residues "improve NAC protein plant growth and developmental process under abiotic stress conditions" (Conclusions).
- **Evidence pointer** Section 2.6, Figure 5A; Section 5 (Conclusions)
- **Concern** The language used to describe the docking results is overinterpreted. Docking studies provide in silico predictions of potential binding interfaces, not evidence of activation or functional outcomes. The claim that specific residues "improve" plant growth is not supported by any experimental data. The abstract and conclusions use causal and functional language that goes beyond what the computational analysis can demonstrate.
- **Why it matters** Overstatement of bioinformatic results misleads readers and inflates the significance of the findings. It also undermines the credibility of the manuscript. The distinction between prediction and experimental validation must be clearly maintained.
- **Resolution test** The authors should revise the language throughout to clearly indicate that the docking and interaction analyses are predictive. Phrases such as "becomes activated" and "improve plant growth" should be replaced with "is predicted to interact" and "may contribute to" or similar. The conclusions should be tempered to reflect the hypothesis-generating nature of the computational work.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The manuscript describes the use of homology modelling, docking, and interaction network analysis, and reports specific RMSD values, DOPE scores, and interaction partners.
- **Evidence pointer** Sections 2.4-2.7, 4.3-4.6; Tables 1-2
- **Concern** Several methodological details are missing. For example: (a) the template selection criteria for homology modelling are not fully described; (b) the DNA sequence used for docking is not specified; (c) the parameters for the docking server are not provided; (d) the confidence level and settings for STRING analysis are only briefly mentioned; (e) the criteria for selecting the ten interaction partners are not explained. Without these details, the reproducibility of the computational analyses is questionable.
- **Why it matters** Reproducibility is a cornerstone of scientific publication. Computational analyses must be described with sufficient detail to allow independent replication. The current level of detail is insufficient for a reader to repeat the analyses.
- **Resolution test** The authors should expand the Methods section to include all relevant parameters, software versions, and selection criteria for each computational step. If space is a concern, this information can be provided in the Supplementary Materials.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Results section
- **Evidence pointer** Sections 2.1-2.11
- **Issue** The text frequently references figures and tables (e.g., "Figure 1A,B", "Table 3") without describing the key features shown in each panel. This makes it difficult for the reader to follow the narrative without constantly cross-referencing the figures.
- **Required correction** Add brief descriptions of what each figure panel shows when first referenced (e.g., "Figure 1A shows the phylogenetic tree..."). This will improve readability.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract; Section 2.9
- **Issue** The abstract states that drought stress caused a "significant increase in membrane damage and reduced relative water, chlorophyll and proline content." However, Section 2.9 reports that proline content increased in the tolerant hybrids. The abstract's phrasing is ambiguous and could be misread as proline decreasing in all hybrids.
- **Required correction** Clarify the abstract to specify that proline content increased in tolerant hybrids while decreasing or remaining lower in susceptible ones. For example: "Drought stress increased membrane damage and reduced relative water and chlorophyll content, while proline accumulation was enhanced in the tolerant hybrids."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reference to supplementary materials
- **Affected element** Results and Methods
- **Evidence pointer** Sections 2.3, 2.4, 4.4
- **Issue** Several supplementary figures and tables are referenced (e.g., Figure S1, S2, S3, Table S1, S2), but the content of these materials is not summarized in the text. The reader cannot assess the relevance of these data.
- **Required correction** Briefly describe the content of each supplementary item when first referenced, or at least state what type of data it contains (e.g., "Supplementary Figure S1 shows the multiple sequence alignment of NAC domains").

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language and grammar
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** There are several instances of awkward phrasing and minor grammatical errors (e.g., "redundantly affected" in the Introduction, "the slightest disturbance occurred during the evolution" in the Discussion). These do not impede understanding but detract from the professional tone.
- **Required correction** A thorough language edit is recommended to improve clarity and fluency.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Inconsistent naming of hybrids
- **Affected element** Results and Discussion
- **Evidence pointer** Sections 2.9-2.11, 3
- **Issue** The hybrids are sometimes referred to as "VRTH-16-3" and "VRTH-17-68" and sometimes as "VRTH 16-3" and "VRTH 17-68" (with or without hyphen). This inconsistency is confusing.
- **Required correction** Use a consistent naming convention throughout the manuscript.

- **Technical failings that need to be addressed before the case is established**
  1. Lack of functional validation for the role of NAC genes in drought tolerance (R1-M1).
  2. Incomplete statistical reporting, including missing variance measures and exact p-values (R1-M2).
  3. Overinterpretation of docking results as evidence of protein activation and functional outcomes (R1-M3).
  4. Insufficient methodological detail for computational analyses, hindering reproducibility (R1-M4).

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The combination of physiological screening and bioinformatic characterization of NAC TFs in tomato hybrids is not entirely novel, as similar approaches have been reported in other crops. The specific hybrids and the integration of multiple data types provide some novelty, but the lack of functional experiments limits the conceptual advance.
  - **Scientific importance**: Moderate. Drought tolerance in tomato is an important agronomic trait, and identifying tolerant hybrids is practically useful. However, the mechanistic insight into NAC function is limited, reducing the broader scientific impact.
  - **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to plant stress biologists and breeders. The bioinformatic component is standard and unlikely to attract computational biologists. The scope is too narrow for a high-impact general journal.
  - **Technical soundness**: The physiological and biochemical methods are standard and appear sound, but the statistical reporting is incomplete. The computational methods are appropriate but lack detail. The absence of functional validation is a significant technical gap.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible, but the overinterpretation of computational results and the lack of clear figure descriptions may confuse nonspecialist readers.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents correlative data and computational predictions that are interesting but do not substantiate the causal claims made in the title and conclusions. Major revisions, including functional validation or substantial reframing of the claims, are required before the case for NAC-mediated drought tolerance regulation is established.