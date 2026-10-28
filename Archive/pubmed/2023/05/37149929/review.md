## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and supplementary figure/table legends as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No assessment of editorial quality or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors identify MEST as a driver of esophageal squamous cell carcinoma (ESCC) metastasis via genome-wide CRISPR/Cas9 screening and gene profiling. They propose a MEST-PURA interaction that activates SRCIN1/RASAL1-ERK-snail signaling, with miR-449a as an upstream regulator silenced by promoter hypermethylation. They further report a small-molecule compound, G699-0288, that disrupts the MEST-PURA interaction and suppresses metastasis in preclinical models.
- **Visible evidence base** Results sections describing CRISPR/Cas9 screening, in vitro invasion assays, in vivo metastasis models, co-immunoprecipitation, ChIP-qPCR, RNA-seq, whole-genome bisulfite sequencing, methylation-specific PCR, molecular docking, SPR, and modified ELISA. Figure legends for Figures 1–7 and Supplementary Figures S1–S9 are referenced. Supplementary Tables S1–S13 are mentioned but not provided in full.
- **Missing materials affecting confidence** Full supplementary tables (S1–S13) with raw screening data, gene lists, and statistical details are not provided. Western blot images are referenced but not shown. Detailed animal experimental protocols (e.g., sample sizes, randomization, blinding) are not fully described. The chemical structure and specificity data for G699-0288 are not provided. The manuscript text contains apparent truncation artifacts in several methods sections (e.g., bisulfite PCR, co-IP, Western blot descriptions), which may indicate incomplete data presentation.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive and potentially impactful study identifying MEST as a novel driver of ESCC metastasis, with a proposed mechanistic axis involving PURA-mediated transcriptional repression of SRCIN1 and RASAL1. The combination of unbiased CRISPR screening, multi-omics approaches, and preclinical therapeutic validation is ambitious and largely well-executed. However, several critical concerns limit the current strength of the conclusions. The mechanistic link between MEST-PURA interaction and transcriptional repression of SRCIN1/RASAL1 is not fully established, with missing chromatin-level evidence. The specificity and in vivo efficacy of the lead compound G699-0288 require further validation. The clinical correlative data, while supportive, are based on a limited cohort and require independent replication. The manuscript would benefit from additional mechanistic depth and clarification of several methodological details.
- **Who would be interested in the results, and why** Cancer biologists studying metastasis mechanisms, particularly in esophageal and other squamous cell carcinomas. Researchers interested in CRISPR screening methodologies for identifying therapeutic targets. Scientists working on protein-protein interaction inhibitors as anticancer agents. Clinicians and translational researchers focused on prognostic biomarkers and targeted therapies for ESCC.
- **Major strengths**
  - The study employs a rigorous unbiased approach combining genome-wide CRISPR/Cas9 screening with transcriptomic profiling of highly metastatic cell lines, providing a solid foundation for target identification.
  - The identification of MEST as a metastasis driver in ESCC is novel, as the authors correctly note the lack of prior functional characterization of MEST in cancer.
  - The multi-pronged validation strategy, including gain- and loss-of-function studies, in vivo metastasis models, and patient tissue analysis, strengthens the biological relevance of the findings.
  - The discovery of a small-molecule inhibitor targeting the MEST-PURA interaction represents a potentially translatable therapeutic approach.
  - The clinical correlation data linking MEST expression to poor prognosis and lymph node metastasis in ESCC patients adds translational significance.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic evidence
- **Claim pointer** The authors claim that "MEST activates SRCIN1/RASAL1-ERK-snail signaling by interacting with PURA" and that PURA directly regulates transcription of SRCIN1 and RASAL1.
- **Evidence pointer** Figure 4g (ChIP-qPCR), Figure 4e (co-IP with mutants), Supplementary Figure S5 (PURA knockdown/overexpression)
- **Concern** The mechanistic model proposes that MEST binds PURA and enhances PURA-mediated transcriptional repression of SRCIN1 and RASAL1. However, the evidence for direct transcriptional regulation is incomplete. ChIP-qPCR demonstrates PURA enrichment at promoter regions, but the functional consequence of this binding on transcriptional activity is not directly shown. The authors do not present luciferase reporter assays with promoter mutations to confirm the functional relevance of the identified binding sites. Furthermore, the mechanism by which MEST enhances PURA's transcriptional activity is not addressed. Does MEST affect PURA's DNA binding affinity, recruitment of co-repressors, or chromatin remodeling? The current data support a correlation between MEST-PURA interaction and downstream gene expression changes, but the causal chain is not fully established.
- **Why it matters** The central claim of the manuscript rests on the MEST-PURA interaction as the mechanistic link between MEST overexpression and ERK pathway activation. Without direct evidence for how this interaction leads to transcriptional repression, the proposed model remains speculative. This is critical for the therapeutic rationale of targeting the MEST-PURA interface.
- **Resolution test** Provide luciferase reporter assays with wild-type and mutant promoter constructs to demonstrate that PURA binding sites are functionally required for repression. Perform chromatin immunoprecipitation for histone marks (e.g., H3K27me3, H3K9me2) or DNA methylation at SRCIN1/RASAL1 promoters in the presence and absence of MEST. Use a PURA mutant that cannot bind MEST to show that the interaction is required for transcriptional repression.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Pharmacological validation
- **Claim pointer** The authors claim that "G699-0288 targets the MEST-PURA interaction and significantly inhibits cancer metastasis" and that it suppresses metastasis more effectively than selumetinib (93.4% vs 81.1% inhibition).
- **Evidence pointer** Figure 7c (SPR), Figure 7e (modified ELISA), Figure 7h–j (in vitro and in vivo functional assays), Supplementary Figure S9f (comparison with selumetinib)
- **Concern** The specificity and mechanism of action of G699-0288 are not sufficiently characterized. SPR and modified ELISA demonstrate binding to MEST and disruption of MEST-PURA interaction, but the selectivity of this compound for MEST over other proteins is not shown. The in vivo efficacy data are presented without detailed pharmacokinetic or toxicity profiles. The comparison with selumetinib is made in a single supplementary figure without statistical analysis or experimental details. Most critically, the on-target specificity of G699-0288 is only addressed through the MEST-knockout rescue experiment (Figure 7k), but the data are not fully described in the text. The authors state that G699-0288 did not suppress metastasis in MEST-KO cells, but the experimental design, sample sizes, and statistical power are not provided.
- **Why it matters** The therapeutic potential of G699-0288 is a major translational claim of the manuscript. Without rigorous evidence of target specificity, selectivity, and in vivo efficacy, the clinical relevance of this compound is not established. The comparison to an approved MEK inhibitor (selumetinib) requires robust statistical analysis and appropriate experimental controls.
- **Resolution test** Provide dose-response curves for G699-0288 in vitro and in vivo. Include a selectivity panel against related proteins or kinases. Present full in vivo data with sample sizes, statistical analysis, and toxicity parameters (body weight, organ histology). Perform a formal statistical comparison between G699-0288 and selumetinib with appropriate controls. Validate on-target activity using a structurally distinct MEST-PURA inhibitor or a genetic approach that recapitulates the compound's effect.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Clinical relevance
- **Claim pointer** The authors claim that "High MEST expression was associated with poor patient survival" and that MEST is a "promising predictor for the prognosis of ESCC patients."
- **Evidence pointer** Figure 2a–g, Table 1, TCGA data analysis
- **Concern** The clinical correlative data are based on a single-center cohort of 242 ESCC patients. The authors do not provide details on the treatment regimens, follow-up duration, or whether the cohort is representative of the general ESCC population. The TCGA analysis is limited to mRNA expression data without protein-level validation. The multivariate analysis, if performed, is not described. The authors do not address whether MEST expression is an independent prognostic factor when adjusted for known clinical variables such as TNM stage, lymph node status, and treatment modality.
- **Why it matters** The prognostic biomarker claim has potential clinical utility, but requires validation in independent cohorts and demonstration of independent prognostic value. Overstated clinical claims could mislead future study designs.
- **Resolution test** Perform multivariate Cox regression analysis including MEST expression, TNM stage, lymph node status, and other relevant clinical variables. Validate MEST protein expression by immunohistochemistry in an independent cohort. Provide details on cohort composition, treatment, and follow-up. If possible, include a meta-analysis of publicly available ESCC datasets.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data completeness
- **Claim pointer** The manuscript describes multiple high-throughput datasets including CRISPR screening, RNA-seq, whole-genome bisulfite sequencing, and proteomics (IP-MS), with results presented in Figures 1–7 and Supplementary Tables S1–S13.
- **Evidence pointer** Supplementary Tables S1–S13, Figures 1–7
- **Concern** The full supplementary tables are not provided in the manuscript text, making it impossible to assess the quality and completeness of the screening data. The CRISPR screening results are summarized but the full gene list, hit criteria, and statistical thresholds are not described. The RNA-seq data analysis is not detailed (e.g., differential expression thresholds, multiple testing correction). The IP-MS data for MEST interactors is mentioned but the full list of identified proteins is not shown. Several methods sections appear truncated (e.g., bisulfite PCR, co-IP), suggesting missing procedural details.
- **Why it matters** The reproducibility and rigor of the study depend on complete data availability and detailed methodology. The inability to assess the primary screening data undermines confidence in the hit selection and downstream validation.
- **Resolution test** Provide all supplementary tables with complete data. Describe the CRISPR screening analysis pipeline, including quality control metrics, hit calling criteria, and statistical methods. Detail the RNA-seq and methylation sequencing analysis parameters. Include the full IP-MS dataset with identified proteins and enrichment scores. Complete the truncated methods sections.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors state that "the student's t test" was used for comparisons throughout the manuscript, with significance indicated as ∗, P < 0.05; ∗∗, P < 0.01; ∗∗∗, P < 0.001.
- **Evidence pointer** Figure legends for Figures 1–7, Methods section "Statistical analysis"
- **Concern** The statistical methods are described only as "the student's t test" without specifying whether tests were one- or two-tailed, paired or unpaired, and whether corrections for multiple comparisons were applied. For animal experiments, the number of biological replicates is not consistently stated. The in vivo imaging data are presented as representative images with quantification, but the statistical analysis of these data is not described. The comparison between G699-0288 and selumetinib lacks any statistical assessment.
- **Why it matters** Rigorous statistical analysis is essential for the validity of the conclusions. Inadequate reporting of statistical methods prevents assessment of the robustness of the findings and could lead to overinterpretation of marginal effects.
- **Resolution test** Provide detailed statistical methods including test selection rationale, assumptions, and software used. State sample sizes for all experiments, including animal numbers. Apply appropriate multiple testing corrections where applicable. Include effect sizes and confidence intervals where possible. Provide statistical analysis for the G699-0288 vs selumetinib comparison.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction section
- **Issue** The abstract states that "MEST activates SRCIN1/RASAL1-ERK-snail signaling by interacting with PURA" but does not mention the miR-449a regulatory axis, which is a significant component of the study. The introduction could more clearly distinguish between the screening approach and the mechanistic validation.
- **Required correction** Revise the abstract to include the miR-449a regulatory component. Consider restructuring the introduction to separate the screening rationale from the mechanistic hypothesis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1d
- **Issue** The heatmap in Figure 1d displays 8927 significantly depleted sgRNAs targeting 1489 genes, but the color scale and clustering method are not described. The selection of the 17 overlapping genes in Figure 1e is not explained in detail.
- **Required correction** Add a legend describing the heatmap color scale and clustering parameters. Describe the criteria for selecting the 17 overlapping genes in the figure legend or methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods section "Whole-genome-based bisulfite sequencing (WGBS)"
- **Evidence pointer** Methods section
- **Issue** The WGBS description is incomplete and contains apparent text truncation ("Next, we predicted the methylation sites in miR-449a promoter..."). The analysis pipeline for methylation calling and differential methylation analysis is not described.
- **Required correction** Complete the WGBS methods description, including library preparation details, sequencing depth, alignment, methylation calling, and differential methylation analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph 2
- **Issue** The discussion states that "the role of MEST in cancer has not been reported till now," but the authors themselves cite references 33 and 34 in the Results section indicating prior reports of MEST functioning as both tumor suppressor and oncogene. This is contradictory.
- **Required correction** Revise the statement to accurately reflect prior literature, e.g., "the role of MEST in ESCC metastasis has not been previously characterized."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Nomenclature
- **Affected element** Methods section "Cell lines and drugs"
- **Evidence pointer** Methods section
- **Issue** The cell line KYSE150 is described as "KYSE150 (CVCL_1348)" and KYSE270 as "KYSE270 (CVCL_1350)", but the source is listed as DSMZ. The authors should verify the correct CVCL identifiers and source for each cell line.
- **Required correction** Verify and correct cell line identifiers and sources. Include authentication and mycoplasma testing details.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Molecular docking"
- **Evidence pointer** Methods section
- **Issue** The molecular docking methodology is not described in the Methods section, although it is referenced in the Results and Discussion. The software, parameters, and scoring functions used are not specified.
- **Required correction** Add a detailed description of the molecular docking methodology, including software, protein preparation, ligand preparation, docking parameters, and scoring criteria.

## Risk / unsupported claims
- The claim that G699-0288 suppresses metastasis with 93.4% inhibition compared to selumetinib's 81.1% is not supported by statistical analysis or detailed experimental data.
- The claim that MEST is a "promising predictor for the prognosis of ESCC patients" is based on a single cohort without multivariate analysis or independent validation.
- The mechanistic model of MEST enhancing PURA-mediated transcriptional repression is not fully supported by direct evidence of transcriptional regulation.
- The claim that systemically delivered miR-449a mimic suppresses metastasis "without overt toxicity" is based on limited toxicity data not fully described.
- The statement that "the role of MEST in cancer has not been reported till now" is contradicted by the authors' own citations.
- The specificity of G699-0288 for MEST over other proteins is not established.
- The clinical relevance of the MEST-PURA interaction in human ESCC metastasis is inferred from correlative data without functional validation in patient-derived models.