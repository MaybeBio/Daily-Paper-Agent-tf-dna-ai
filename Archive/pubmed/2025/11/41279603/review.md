## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2025)
- **Assessment boundary** Scientific content, methodology, data analysis, claims, and interpretation as presented in the provided text. No external data or supplementary files were assessed.
- **Shared manuscript claim summary** The authors present UDI-UMI-STARR-seq, a modified STARR-seq approach with dual indexes and unique molecular identifiers, to profile enhancer activity across 253,632 fragments from 46,142 candidate enhancers in HEK293T cells. They assess the impact of CRISPR/Cas9-mediated knockout of six transcription factors (ATF2, CTCF, FOXA1, LEF1, TCF7L2, SCRT1) on enhancer activity and gene expression, identify responsive enhancers, link them to target genes, and train deep learning models to predict enhancer activity. The framework is applied to a 16p12.1 deletion model to identify disease-relevant regulatory networks.
- **Visible evidence base** Main text, figures referenced (Fig 1-5), methods section, data availability statement, code availability statement. Supplementary figures and tables are referenced but not provided.
- **Missing materials affecting confidence** Supplementary figures (S1-S4), Supplementary tables (S1-S2), Supplementary Information (detailed protocols, validation data), processed data files, and code repository contents were not available for review. These are essential for verifying key claims regarding data quality, reproducibility, and model performance.

## Reviewer

### **Overall assessment**
This manuscript presents a technically ambitious and potentially valuable framework for quantifying enhancer dynamics under genetic perturbation. The integration of UDI-UMI-STARR-seq with RNA-seq and deep learning is a logical and potentially powerful combination. However, the current version has several significant gaps in evidence presentation and validation that prevent full assessment of the claims. The core findings are plausible but not fully established from the provided material. The manuscript would benefit from clearer presentation of validation metrics, more direct evidence for the enhancer-gene linking strategy, and a more critical discussion of the limitations of the episomal STARR-seq assay in the context of disease-associated variants.

### **Who would be interested in the results, and why**
- Researchers in gene regulation and enhancer biology, particularly those using high-throughput reporter assays (STARR-seq, MPRA).
- Computational biologists developing deep learning models for regulatory genomics.
- Geneticists studying the functional impact of disease-associated non-coding variants, especially copy number variants.
- Groups interested in transcription factor biology and regulatory network rewiring.

### **Major Strengths**
1. The UDI-UMI-STARR-seq design addresses real technical challenges in STARR-seq (index hopping, PCR duplicates) and represents a methodological improvement.
2. The scale of the study (253,632 fragments, 46,142 candidate enhancers, six TF knockouts) is substantial and provides a rich dataset for the community.
3. The combination of experimental perturbation, enhancer activity measurement, transcriptomics, and deep learning is a comprehensive and integrated approach.
4. The application to a disease-associated CNV (16p12.1) demonstrates a clear path toward clinical relevance.
5. The observation that enhancer responsiveness correlates with baseline activity and motif density is an interesting and potentially generalizable finding.

### **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Data quality validation
- **Claim pointer** The authors claim high data quality based on inter-replicate correlations (Pearson coefficient 0.80-0.99) and that UDI-UMI-STARR-seq enables accurate quantification of enhancer activity.
- **Evidence pointer** Figure 2C, Methods (STARR-seq reads processing and data quality assessment)
- **Concern** The data quality assessment is described only in a single sentence with a correlation range. No details are provided on how many replicates were used, whether the correlation is on raw counts or normalized values, how the UMI deduplication rate was assessed, or how the efficiency of UDI in preventing index hopping was quantified. The correlation range of 0.80-0.99 is very wide, and the lower bound suggests potential reproducibility issues in some libraries.
- **Why it matters** The entire downstream analysis (differential activity, enhancer-gene linking, deep learning) depends on the reliability of the STARR-seq measurements. Without robust evidence of data quality, including UMI performance metrics and replicate consistency, the core quantitative claims are not verifiable.
- **Resolution test** Provide detailed quality control metrics: number of reads before/after deduplication, UMI collision rate estimates, per-replicate correlation plots, and a clear description of how the Pearson correlation was computed. Show that the correlation is high (e.g., >0.9) for all libraries, not just a range.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Differential activity analysis
- **Claim pointer** The authors define responsive enhancers as fragments with significant differential activity (p-adjusted < 0.01) in KO lines relative to control, and report percentages of responsive fragments per KO line.
- **Evidence pointer** Methods (Differential activity analysis), Figure 3
- **Concern** The differential activity analysis uses DESeq2 on read counts from 500-bp overlapping fragments. However, the manuscript does not describe how library size factors were estimated, whether the fragment-level counts were adjusted for the varying number of fragments per candidate enhancer region, or how the overlap between fragments (50-bp step) was handled in the statistical model. Overlapping fragments are not independent, which could inflate significance. Additionally, the threshold for calling responsive fragments is not justified, and no effect size threshold is applied.
- **Why it matters** The identification of responsive enhancers is the central experimental readout. If the statistical approach is flawed or overly liberal, the lists of responsive enhancers and all subsequent analyses (gene linking, pathway enrichment, disease application) could be unreliable.
- **Resolution test** Describe the DESeq2 model in detail, including how overlapping fragments were handled (e.g., using a non-overlapping window or a mixed model). Provide a volcano plot or MA plot for at least one KO line. Justify the p-value threshold and consider adding an effect size cutoff. Show that the results are robust to the choice of fragment size and step.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / Enhancer-gene linking
- **Claim pointer** The authors state that using a combination of the nearest-gene method and a modified activity-by-contact model, 84% of differentially active enhancers were mapped to their target genes.
- **Evidence pointer** Methods (Connecting enhancers to target genes), Figure 4A
- **Concern** The enhancer-gene linking is a critical step for interpreting the functional consequences of enhancer activity changes. However, the description is brief. The ABC model requires Hi-C or similar contact data, but the manuscript does not state what contact data were used for HEK293T cells. The modification to the ABC model (using STARR-seq activity instead of the default chromatin-based activity) is a significant deviation that needs validation. The 84% mapping rate seems very high and may reflect the permissive nature of the nearest-gene method rather than true regulatory connections.
- **Why it matters** The biological interpretation of the TF knockout effects and the 16p12.1 deletion analysis depends entirely on the accuracy of enhancer-gene linking. If the linking is inaccurate, the reported target genes and pathways may be spurious.
- **Resolution test** Specify the source of contact data for the ABC model. Validate the modified ABC model against a gold standard set of enhancer-gene pairs (e.g., from CRISPR perturbation or eQTL studies). Report the distribution of distances between enhancers and their assigned target genes. Show that the 84% mapping rate is not simply an artifact of the nearest-gene assignment.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Deep learning model
- **Claim pointer** The authors claim that a deep learning model (ResNet) recapitulates core principles of enhancer grammar, including cooperative motif syntax and the influence of flanking sequence context, and outperforms linear models.
- **Evidence pointer** Figure 4B-4D, Methods (Sequence determinant analysis)
- **Concern** The deep learning section is underdeveloped. The manuscript does not provide key architectural details (number of layers, filter sizes, pooling strategies), training hyperparameters, or a clear description of the training/validation/test split. The performance metrics are mentioned but not shown in detail. The claim that the model recapitulates "cooperative motif syntax" is based on TF-MoDISco analysis, but the presentation is superficial. The comparison to linear models is mentioned but the specific metrics and statistical significance are not reported.
- **Why it matters** The deep learning model is presented as a major contribution, but without sufficient detail, the results cannot be reproduced or evaluated. The claim about learning enhancer grammar is strong and requires robust evidence.
- **Resolution test** Provide a complete description of the model architecture and training procedure. Show performance metrics (e.g., AUPRC, AUROC) for both linear and deep learning models on held-out test data, with confidence intervals. Present TF-MoDISco results more rigorously, including motif logos, enrichment statistics, and a comparison to known motifs. Demonstrate that the model's predictions are significantly better than a sequence composition baseline.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Disease application
- **Claim pointer** The authors apply the framework to a 16p12.1 deletion model and identify responsive enhancers linked to genes involved in axon guidance, synaptic plasticity, and translational control.
- **Evidence pointer** Figure 5, Results (Regulatory network for neurodevelopmental disease-associated 16p12.1 deletion)
- **Concern** The 16p12.1 deletion analysis is presented as a key application, but the results are described in a single paragraph. The number of responsive enhancers, the specific genes identified, and the validation of these findings are not detailed. The authors acknowledge the limitation of using a cancer cell line, but this is a major caveat for a neurodevelopmental disorder. The pathway enrichment analysis is mentioned but not shown.
- **Why it matters** The disease application is likely to be a major draw for readers. If the findings are not robustly presented and validated, the translational relevance of the framework is weakened.
- **Resolution test** Provide a detailed description of the 16p12.1 deletion experiment, including the number of responsive enhancers, the specific target genes, and the pathway enrichment results. Discuss the limitations of the HEK293T cell model more thoroughly. If possible, validate a subset of the enhancer-gene links using an orthogonal method (e.g., CRISPRi or luciferase assays).

### **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Methods (STARR-seq plasmid library preparation)
- **Evidence pointer** Methods section
- **Issue** The methods section for library preparation is detailed but lacks specific information on the number of biological replicates for each condition and the total number of cells used per transfection. This information is critical for assessing statistical power and reproducibility.
- **Required correction** Add the number of biological replicates for each cell line and condition, and specify the cell count per transfection.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3
- **Evidence pointer** Figure 3A-3G
- **Issue** The activity maps in Figure 3 are described but not shown in the text. The description of the variance analysis (Figure 3C) is unclear; it is not specified whether the variance is calculated across KO lines for each fragment or across fragments for each KO line.
- **Required correction** Clarify the variance calculation and ensure the figure legend explains all panels clearly.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the episomal context of STARR-seq is brief. The authors note that the assay may not capture endogenous chromatin effects, but they do not discuss the implications of this for the interpretation of their results, particularly for the disease application.
- **Required correction** Expand the discussion on the limitations of episomal assays and how they might affect the generalizability of the findings.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods (RNA-seq data analysis)
- **Evidence pointer** Methods section
- **Issue** The RNA-seq analysis is described in a single sentence. No details are provided on the alignment parameters, the reference annotation used, or the differential expression analysis beyond the DESeq2 default. The PCA for quality assessment is mentioned but not shown.
- **Required correction** Provide more detail on the RNA-seq processing pipeline and include the PCA plot in the supplementary materials.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the framework is "generalizable to genetic mutations," but the manuscript only tests six TF knockouts and one CNV deletion. This overstates the generalizability.
- **Required correction** Soften the claim in the abstract to reflect the specific perturbations tested.

### **Technical failings that need to be addressed before the case is established**
- R1-M1: Insufficient data quality validation for STARR-seq libraries.
- R1-M2: Incomplete description of the differential activity analysis, particularly regarding overlapping fragments.
- R1-M3: Lack of validation for the modified ABC model and the high enhancer-gene mapping rate.
- R1-M4: Under-specified deep learning model and performance evaluation.

### **Assessment against Nature-style criteria**
- **Originality**: The combination of UDI-UMI-STARR-seq with TF knockout and deep learning is a novel integration of existing technologies. The scale of the dataset is a significant contribution. However, the individual components (STARR-seq, TF knockout, deep learning for enhancer prediction) are established, and the novelty lies primarily in their integration.
- **Scientific importance**: The question of how genetic mutations affect enhancer dynamics is of fundamental importance to gene regulation and disease. The framework has the potential to be widely used. However, the current evidence does not fully establish the framework's reliability or the biological significance of the findings.
- **Interdisciplinary readership**: The work bridges molecular biology, genomics, and computational biology. It would appeal to a broad readership if the technical concerns are addressed.
- **Technical soundness**: The experimental design is reasonable, but the technical validation is incomplete. The statistical analysis of differential activity and the deep learning model require more rigor and detail.
- **Readability for nonspecialists**: The manuscript is generally well-written and accessible, but the results section is dense and would benefit from clearer explanations of the key concepts and findings.

### **Recommendation posture**
**Supportive if technical concerns are resolved.** The manuscript presents a potentially valuable framework and a large dataset, but the current evidence is insufficient to fully support the claims. The authors must address the major concerns regarding data quality, statistical analysis, enhancer-gene linking, and deep learning model validation before the case is established.

## Risk / unsupported claims
- The claim that UDI-UMI-STARR-seq provides accurate quantification of enhancer activity is not fully supported without detailed quality control metrics.
- The claim that 84% of differentially active enhancers were mapped to target genes is unsupported without validation of the modified ABC model.
- The claim that the deep learning model recapitulates "core principles of enhancer grammar" is not supported by the limited model description and performance evaluation.
- The claim that the framework is "generalizable to genetic mutations" is overstated given the limited number of perturbations tested.
- The biological significance of the findings for the 16p12.1 deletion is not fully established due to the limited presentation of results and the acknowledged limitations of the cell line model.