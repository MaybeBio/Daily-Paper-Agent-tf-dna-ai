## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, STAR+METHODS, and supplementary figure/table legends as referenced.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment of evidence with conclusions. No assessment of grammatical style or formatting beyond readability for a general scientific audience.
- **Shared manuscript claim summary** The authors present CaRNetS, a computational framework that integrates ATAC-seq and transcriptomic data from 371 patients across 22 cancer types to construct directed gene regulatory networks, identify key transcription factors (TFs) per patient cluster, and predict druggable gene targets by correlating TF essentiality with DepMap dependency data. Four predicted targets (NAMPT, PPAT, MDM2, BRD9) were validated in vitro using cell viability assays in representative cell lines.
- **Visible evidence base** Abstract, full introduction, full results, full discussion, STAR+METHODS (including data processing, model training, validation approaches, and in vitro protocols), and references to Supplementary Figures 1–15 and Supplementary Tables 1–10.
- **Missing materials affecting confidence** Supplementary figures and tables are referenced but not provided in the submitted material. These include detailed validation metrics (Supplementary Figure 2), cluster assignments (Supplementary Figure 1, Supplementary Table 4), DepMap comparisons (Supplementary Table 5), CaCTS comparisons (Supplementary Table 6), drug target lists (Supplementary Table 9), and raw viability data (Supplementary Figure 9). Without these, several quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach that combines chromatin accessibility, transcriptomics, and network inference to nominate therapeutic targets. The integration of three-dimensional genomic data for enhancer-promoter contacts is a notable methodological advance over correlation-based approaches. However, the evidence provided in the main text is insufficient to fully establish the predictive validity of CaRNetS. The in vitro validation is limited to four targets in three cell lines with a single control cell line per experiment, and the statistical framework for comparing effects across cell lines is not fully described. The claim that CaRNetS outperforms existing approaches is supported only by indirect comparisons that require the missing supplementary materials for verification. The manuscript would benefit from clearer presentation of the scoring equations and a more rigorous demonstration that the identified targets are specifically relevant to the predicted cancer types rather than general cytotoxic effects.
- **Who would be interested in the results, and why** Computational biologists and cancer researchers focused on therapeutic target discovery, particularly those working with ATAC-seq and transcriptomic data. The approach may also interest researchers studying lineage plasticity and master transcription factor regulation. The potential clinical relevance for neuroendocrine, liver, and renal cancers, which have limited targeted options, could attract translational oncology groups.
- **Major strengths** 1) The use of machine learning trained on three-dimensional genomic data to infer enhancer-promoter contacts is a sophisticated and potentially more accurate method than standard correlation-based approaches. 2) The integration of multiple data types (ATAC-seq, RNA-seq, DepMap, drug databases) into a single scoring framework is comprehensive. 3) The identification of known drug targets (e.g., ESR1, KRAS, EGFR) as high-ranking candidates provides a form of internal validation. 4) The focus on cancers with poor prognosis and limited therapeutic options addresses an important clinical need.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (validation specificity), R1-M2 (scoring equation clarity), R1-M3 (statistical rigor of in vitro data), R1-M4 (missing supplementary evidence).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate to high. The combination of chromatin accessibility, network inference, and drug target prediction is not entirely novel, but the use of three-dimensional genomic data for training is a distinctive contribution.  
  *Scientific importance*: Potentially high if the predictions are robust, given the clinical need in the target cancers. However, the current evidence is preliminary.  
  *Interdisciplinary readership*: The work bridges genomics, computational biology, and oncology, which could appeal to a broad audience. The methods section is technical but accessible to specialists.  
  *Technical soundness*: The computational framework is logically constructed, but the validation is insufficient to confirm predictive accuracy. The in vitro experiments lack the statistical power and controls needed to draw firm conclusions.  
  *Readability for nonspecialists*: The abstract and introduction are clear, but the results section assumes familiarity with network centrality measures and DepMap data. The scoring equations are presented without sufficient context for a general reader.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the current evidence does not fully establish the validity of CaRNetS as a reliable target discovery tool. The authors should provide the missing supplementary data, clarify the scoring methodology, and strengthen the experimental validation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that CaRNetS identifies therapeutic targets validated by in vitro experiments showing "statistically significant effects on cell growth" for BRD9, MDM2, NAMPT, and PPAT inhibitors in respective cell lines.  
- **Evidence pointer** Results section, Figure 5A–D, Supplementary Figure 9; location not provided for specific data points.  
- **Concern** The in vitro validation uses only one cell line per target (HepG2 for BRD9, A498 for MDM2, DMS53 for NAMPT/PPAT) and a single control cell line (HCC1143) for all experiments. This design does not adequately demonstrate target specificity. The observed effects could reflect general cytotoxicity rather than on-target activity in the predicted cancer types. Additionally, the claim of "statistically significant effects" is not supported by the presented data, as no statistical test, effect size, or variance measure is described in the main text. The inability to identify IC50s in the control cell line is mentioned, but the criteria for this determination are not defined.  
- **Why it matters** The central claim of the manuscript is that CaRNetS can identify valid therapeutic targets. Without rigorous, target-specific validation, the predictive power of the framework is not established. General cytotoxic effects would not support the clinical relevance of the predictions.  
- **Resolution test** Provide dose-response curves with multiple biological replicates for each inhibitor in at least two additional cell lines per cancer type, including a non-target cell line as a negative control. Report statistical comparisons (e.g., ANOVA with post-hoc tests) and effect sizes. Demonstrate that the inhibitors' effects correlate with expression or dependency of the predicted target genes.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity  
- **Claim pointer** The authors state that CaRNetS scores are computed using a formula that integrates correlation, essentiality, and drug-target interactions, and that this scoring "optimizes" known drug targets.  
- **Evidence pointer** Methods section, "Identifying druggable gene candidates and prioritizing drugs"; location not provided.  
- **Concern** The scoring equations are presented without derivation or justification. The formula Scorei = Di*(abs(Rix)−abs(Ei)−EDi−ESi)*(1+1/Ux)*(1+1/Ix)*(1−Ti) is not explained in terms of how each term contributes to the final score or why this particular combination is optimal. The Drug_Scorec formula is similarly opaque. The claim that the scoring "optimizes" known targets is not supported by a formal optimization procedure or a comparison against alternative scoring schemes.  
- **Why it matters** Reproducibility is a core requirement for computational methods. If the scoring is arbitrary or overfit to known targets, the generalizability of CaRNetS is questionable. Readers cannot assess the validity of the approach without understanding the rationale for each term.  
- **Resolution test** Provide a step-by-step derivation of the scoring formulas, including the biological rationale for each term. Perform a sensitivity analysis showing how the ranking of known targets changes when individual terms are removed or weights are altered. Compare CaRNetS scores against simpler alternatives (e.g., correlation alone, essentiality alone) using a benchmark dataset.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The authors claim that the clustering of patients based on TF scores identifies biologically meaningful groups, including a neuroendocrine cluster (LUAD-PCPG-STAD-Cluster21) validated by pathological examination of one STAD sample.  
- **Evidence pointer** Results section, Figure 1C, Figure 2A, Supplementary Figure 5; location not provided.  
- **Concern** The validation of the neuroendocrine cluster relies on a single pathological examination of one STAD sample. This is anecdotal evidence and does not constitute a systematic validation of the cluster assignment. The statistical significance of the cluster separation is not reported, and the choice of clustering parameters (e.g., number of clusters, epsilon in DBSCAN) is not justified with a stability analysis. The claim that TF-score-based clustering captures biology beyond what is possible with RNA-seq or ATAC-seq alone is not quantitatively demonstrated.  
- **Why it matters** The clustering is the foundation for all downstream target predictions. If the clusters are not robust or biologically meaningful, the target predictions may be spurious. The authors need to demonstrate that their clustering approach provides reproducible and validated groupings.  
- **Resolution test** Perform cluster stability analysis (e.g., bootstrap resampling) and report adjusted Rand index or similar metrics. Validate the neuroendocrine cluster using additional independent samples with pathological annotation. Compare cluster assignments against known molecular subtypes using external datasets.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that CaRNetS performs better than DepMap dependency data alone in 14/19 clusters based on an AUPRC comparison.  
- **Evidence pointer** Results section, Supplementary Figure 10; location not provided.  
- **Concern** The AUPRC comparison is only presented in the supplementary materials, which were not provided. Without the actual data, the claim cannot be evaluated. Additionally, the comparison is against a single baseline (DepMap dependency), and it is unclear whether the improvement is statistically significant or practically meaningful. The choice of AUPRC as the metric is not justified, and the authors do not report precision-recall curves or confidence intervals.  
- **Why it matters** This comparison is a key piece of evidence for the utility of CaRNetS. If the improvement over DepMap is marginal or not significant, the added complexity of the method may not be warranted.  
- **Resolution test** Provide the full AUPRC data in the main text or as a clearly accessible supplement. Report statistical significance of the differences (e.g., bootstrap or permutation tests). Include a comparison against additional baselines, such as correlation-based networks or random gene sets.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, "Here we present a computational approach..."  
- **Issue** The abstract states that CaRNetS "identifies drug targets based on tumor lineage," but the concept of lineage is not defined in the abstract. The relationship between TF-score-based clusters and lineage is implied but not explicitly stated.  
- **Required correction** Clarify in the abstract that lineage is inferred from TF regulatory networks and that clusters may contain multiple cancer types sharing similar regulatory programs.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods, "Identifying targets of regulatory elements (DGTAC)"  
- **Evidence pointer** Methods section, DGTAC description; location not provided.  
- **Issue** The DGTAC method is described in two steps, but the hyperparameters for ElasticNet and the random forest model are not specified. The number of features, regularization strength, and tree depth are not reported.  
- **Required correction** Provide all hyperparameters and a description of the cross-validation procedure used for model selection.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Data availability  
- **Affected element** Methods, "Data and code availability"  
- **Evidence pointer** Methods section, Data and code availability.  
- **Issue** The code is available on GitHub, but the repository is not versioned or linked to a DOI. The sequencing data are deposited at GSE202511, but the specific files used for each analysis are not listed.  
- **Required correction** Provide a versioned release of the code with a DOI and a detailed README listing all input files and parameters. Include a data manifest in the GEO submission.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Results, "Drug targets identified using CaRNetS"  
- **Evidence pointer** Results section, Figure 4C; location not provided.  
- **Issue** The authors state that CaRNetS identifies targets for clusters with "few or no targeted therapies," but the figure only shows rankings, not the clinical landscape of existing therapies for each cluster.  
- **Required correction** Add a supplementary table listing existing approved therapies for each cancer type in the cluster to support the claim of unmet need.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Technical detail  
- **Affected element** Methods, "Validating drug candidates in vitro"  
- **Evidence pointer** Methods section, in vitro validation; location not provided.  
- **Issue** The cell viability assays are described as using CellTiter-Glo, but the incubation times vary (6h for RG-7112, 48h for TP-472, etc.). The rationale for these different time points is not explained.  
- **Required correction** Justify the chosen time points for each inhibitor or provide time-course data to show that the effects are consistent over time.

## Risk / unsupported claims
- The claim that CaRNetS identifies targets validated by in vitro experiments is not fully supported due to the limited cell line panel and lack of statistical detail.
- The claim that TF-score-based clustering captures biology beyond RNA-seq or ATAC-seq alone is not quantitatively demonstrated.
- The claim of superior performance over DepMap dependency data is unverifiable without the supplementary AUX materials.
- The claim that the neuroendocrine cluster is validated by pathological examination is based on a single sample and is anecdotal.
- The claim that CaRNetS accounts for drug toxicity in scoring is not supported by the presented data, as the toxicity term Ti is acknowledged to not improve scores.