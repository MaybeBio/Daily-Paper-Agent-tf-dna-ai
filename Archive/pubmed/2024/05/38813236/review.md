## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, ethics, data availability, funding, CRediT, declarations, supplementary data list)
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, internal consistency, and alignment with stated claims. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors report that ESPL1 is significantly upregulated in bladder cancer (BC) at both mRNA and protein levels, is predominantly expressed in BC epithelial cells, is associated with cell cycle-related pathways and immune cell infiltration, is regulated by upstream transcription factors (H2AZ, IRF5, HIF1A) and chromatin loops (promoter-super-enhancer and promoter-typical-enhancer), correlates with drug sensitivity to paclitaxel and gemcitabine, and that miR-299-5p is downregulated in BC blood and tissue samples with diagnostic potential.
- **Visible evidence base** Multicentre mRNA datasets (n = 1391), in-house IHC staining (n = 202), scRNA-seq (GSE176249), ATAC-seq, ChIP-seq, Hi-C data, immune infiltration analyses, drug sensitivity analyses, molecular docking, miRNA prediction and expression analyses (blood n = 6625, tissue n = 537).
- **Missing materials affecting confidence** Figures and supplementary materials referenced (Figs. 1–11, S1–S6, Table 1, Table 2, Supplementary Material 1) were not provided. Specific statistical outputs, quality control metrics for sequencing data, and detailed bioinformatics parameters are not available for independent verification.

## Reviewer
- **Overall assessment** This manuscript presents a broad, multi-platform investigation of ESPL1 in bladder cancer, combining public database mining, in-house protein validation, single-cell analysis, epigenetic profiling, and miRNA assessment. The scope is ambitious and the dataset integration is commendable. However, the manuscript suffers from several critical weaknesses: the causal relationship between the identified regulatory mechanisms and ESPL1 upregulation is not experimentally validated; the drug sensitivity and molecular docking results are correlative and lack functional confirmation; the diagnostic claims for miR-299-5p are based on retrospective analyses with heterogeneous cohorts; and several statistical and methodological details are insufficiently reported. The conclusions, as stated, are not fully supported by the evidence presented.
- **Who would be interested in the results, and why** Researchers in bladder cancer biology, cancer epigenetics, and translational oncology would be interested. The identification of ESPL1 as a potential biomarker and therapeutic target, along with the proposed upstream regulatory network, could inform future mechanistic studies and diagnostic development. The miR-299-5p findings may interest those working on noninvasive cancer biomarkers.
- **Major Strengths** (1) Large sample size for mRNA expression analysis (n = 1391) with multicentre coverage. (2) Protein-level validation via in-house IHC on 202 samples, which strengthens the translational relevance. (3) Integration of multiple high-throughput data types (scRNA-seq, ATAC-seq, ChIP-seq, Hi-C) to explore regulatory mechanisms. (4) Inclusion of drug sensitivity and molecular docking analyses, adding a therapeutic dimension. (5) The study addresses a gap in understanding ESPL1 regulation in BC, which has been underexplored.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Causal inference
  - **Claim pointer** The authors claim that H2AZ, IRF5, and HIF1A act as upstream transcription factors regulating ESPL1 expression, and that promoter-enhancer loops mediated by RAD21 enhance ESPL1 transcription.
  - **Evidence pointer** Results section "Regulatory mechanisms of elevated ESPL1 expression", Figure 8
  - **Concern** The evidence for transcriptional regulation is entirely bioinformatic and correlative. ChIP-seq peaks and chromatin loops demonstrate potential binding and spatial proximity, but do not establish that these factors functionally regulate ESPL1 expression. No knockdown, overexpression, or reporter assays are provided to confirm causality.
  - **Why it matters** The central mechanistic claim of the paper, that specific TFs and chromatin architecture drive ESPL1 upregulation in BC, is not experimentally substantiated. Without functional validation, the proposed regulatory model remains speculative.
  - **Resolution test** Provide experimental evidence such as siRNA/shRNA knockdown of H2AZ, IRF5, or HIF1A in BC cell lines followed by ESPL1 expression analysis, or chromatin conformation capture (3C/qPCR) to confirm enhancer-promoter interactions. Alternatively, CRISPR-based perturbation of the identified enhancer regions would strengthen the claim.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Clinical and functional significance
  - **Claim pointer** The authors claim that ESPL1 expression is associated with drug sensitivity to paclitaxel and gemcitabine, and that molecular docking shows high affinity, suggesting these drugs play vital roles in treating BC.
  - **Evidence pointer** Results section "Correlation between ESPL1 expression and drug sensitivity in BC patients", Figure 9B and 9C
  - **Concern** The drug sensitivity analysis is purely correlative, based on IC50 values derived from computational predictions. Molecular docking scores do not demonstrate functional drug-target interaction in a biological context. No in vitro or in vivo experiments are presented to show that ESPL1 expression levels actually affect drug response.
  - **Why it matters** The claim that ESPL1 affects drug sensitivity has direct clinical implications. If unsupported, it could mislead future therapeutic strategies. The current evidence does not establish a functional link between ESPL1 expression and drug efficacy.
  - **Resolution test** Perform cell viability assays (e.g., IC50 determination) in BC cell lines with modulated ESPL1 expression (overexpression or knockdown) treated with paclitaxel and gemcitabine. This would provide direct evidence of whether ESPL1 alters drug sensitivity.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Diagnostic claim validity
  - **Claim pointer** The authors claim that miR-299-5p has "great potential for early screening" of BC based on its downregulation in blood and tissue samples.
  - **Evidence base** Results section "miR-299-5p showed low expression in BC blood and tissue samples", Figures 10 and 11
  - **Concern** The diagnostic performance of miR-299-5p is assessed using AUC values from ROC analyses, but the cohorts are heterogeneous, and the authors acknowledge that some datasets did not show statistically significant results. The sensitivity and specificity values are not consistently reported across all cohorts. The claim of "great potential for early screening" is overstated given the variability and lack of prospective validation.
  - **Why it matters** Early screening claims require robust, reproducible diagnostic performance. Overstating the potential of a biomarker based on retrospective, heterogeneous data could lead to inappropriate clinical expectations.
  - **Resolution test** Provide a meta-analysis with subgroup analyses by cohort type, report pooled sensitivity and specificity with confidence intervals, and clearly state the limitations of retrospective data. Prospective validation or at least a well-designed independent replication cohort would be needed to support the screening claim.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor and data integration
  - **Claim pointer** The authors state that "ESPL1 was significantly overexpressed at the mRNA level (p < 0.05, SMD = 0.75; 95% CI = 0.09, 1.40)" based on a meta-analysis of 11 datasets.
  - **Evidence base** Results section "Expression of ESPL1 in BC tissues", Figure 2
  - **Concern** The meta-analysis shows high heterogeneity (I² = 88%), and only 7 of 11 datasets showed statistically significant upregulation. The random-effects model is appropriate, but the wide confidence interval (0.09 to 1.40) and the high heterogeneity raise questions about the consistency and generalizability of the finding. The authors do not adequately explore the sources of heterogeneity (e.g., platform differences, sample types, normalization methods).
  - **Why it matters** A robust meta-analytic conclusion requires understanding and addressing heterogeneity. The current presentation may overstate the consistency of ESPL1 upregulation across BC cohorts.
  - **Resolution test** Perform subgroup analyses (e.g., by platform, sample type, or country), report I² with confidence intervals, and discuss potential sources of heterogeneity. Consider sensitivity analyses excluding outlier datasets.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness
  - **Affected element** Methods section "Data collection and processing"
  - **Evidence pointer** Methods section, Table 1
  - **Issue** The description of data processing is brief. The specific normalization methods, quality control thresholds, and criteria for merging datasets are not fully detailed. The statement "The miRNA and mRNA datasets were processed with log2 (x + 0.01) and log2 (x + 1), respectively" is unclear regarding which datasets received which transformation.
  - **Required correction** Provide a detailed step-by-step description of data processing, including specific R packages and parameters, quality control metrics, and the rationale for dataset merging. Clarify the transformation applied to each data type.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Figure quality and accessibility
  - **Affected element** Figures 1–11
  - **Evidence pointer** Figures 1–11 (not provided)
  - **Issue** The figures are referenced but not available for review. Based on the text, some figures (e.g., Figure 8) appear to contain complex multi-panel data that may be difficult to interpret without clear annotations.
  - **Required correction** Ensure all figures are self-explanatory with clear labels, legends, and annotations. Consider simplifying complex panels or providing additional explanatory text in the figure legends.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology precision
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section
  - **Issue** The phrase "first comprehensive study" is used, which is a strong claim. While the study is broad, the term "comprehensive" is subjective and may be challenged.
  - **Required correction** Rephrase to "one of the first studies to integrate..." or "this study provides a broad analysis..." to avoid overclaiming.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data availability statement
  - **Evidence pointer** Data availability statement
  - **Issue** The statement says data are available in public databases or Supplementary Material 1, but the specific accession numbers for GEO datasets, TCGA, and other databases are not listed in the text.
  - **Required correction** Provide a comprehensive list of all data sources with accession numbers in the Data Availability section or in a supplementary table.
- **Technical failings that need to be addressed before the case is established** (1) Lack of experimental validation for the proposed transcriptional regulatory mechanism (R1-M1). (2) Lack of functional evidence linking ESPL1 expression to drug sensitivity (R1-M2). (3) Overstated diagnostic claim for miR-299-5p without prospective validation (R1-M3). (4) Inadequate handling and reporting of heterogeneity in the meta-analysis (R1-M4).
- **Assessment against Nature-style criteria**  
  **Originality:** Moderate. The application of multi-omics integration to ESPL1 in BC is relatively novel, but the individual components (expression analysis, pathway enrichment, immune correlation) are standard approaches. The epigenetic regulatory analysis adds some originality, but it is purely computational.  
  **Scientific importance:** Moderate. ESPL1 as a cancer-related gene is known; the specific focus on BC and the proposed regulatory network could be of interest, but the lack of functional validation limits the significance of the findings.  
  **Interdisciplinary readership:** Limited. The manuscript is primarily relevant to cancer biologists and bioinformaticians. The clinical implications are speculative, and the diagnostic claims are not sufficiently robust to attract a broader clinical audience.  
  **Technical soundness:** The bioinformatics analyses are generally appropriate, but the lack of experimental validation and the incomplete reporting of statistical details undermine the technical rigor. The heterogeneity in the meta-analysis is a concern.  
  **Readability for nonspecialists:** The manuscript is dense and assumes familiarity with multiple high-throughput techniques. The abstract is clear, but the methods and results sections would be challenging for nonspecialists. The figures, if provided, would need to be highly accessible.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a broad correlative analysis, but the central mechanistic claims and the clinical implications are not supported by functional experiments. Major revisions, including experimental validation of the regulatory mechanisms and drug sensitivity, are required before the case is established.

## Risk / unsupported claims
- The claim that H2AZ, IRF5, and HIF1A "act as upstream transcription factors" regulating ESPL1 is unsupported; only computational prediction is provided.
- The claim that ESPL1 "might promote BC growth" is speculative and not directly tested.
- The claim that ESPL1 expression "affects the sensitivity and therapeutic efficacy" of paclitaxel and gemcitabine is unsupported by functional data.
- The claim that miR-299-5p has "great potential for early screening" is overstated given the heterogeneous and retrospective nature of the data.
- The statement that this is the "first comprehensive study" on ESPL1 in BC is not verifiable and is likely an overclaim.
- The conclusion that ESPL1 is "an immune-related predictive and diagnostic marker" is not supported by survival analysis or prospective validation.