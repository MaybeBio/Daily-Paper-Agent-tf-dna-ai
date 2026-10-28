## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, acknowledgments, footnotes)
- **Assessment boundary** Scientific content, methodological soundness, evidence consistency, and claim support based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present a kinetic multi-omics dataset (RNA-seq, ATAC-seq, ChIP-seq for AR, FOXA1, H3K27ac, H3K4me3, HiChIP, Start-seq) across five time points after androgen stimulation in LNCaP cells. They report that AR binding induces sequential epigenetic changes at enhancers, does not rewire chromatin loops but increases contact frequency of pre-existing loops, and that gene expression correlates with contact frequency changes. They propose and validate an "unbalanced multi-enhancer dominance model" where a subset of enhancers with higher contact frequency disproportionately influence transcription.
- **Visible evidence base** Abstract, full introduction, full methods, full results, full discussion, acknowledgments, footnotes. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** All figures, tables, supplementary tables (Supp Table 1, Supp Table 2), supplementary figures (Supp Fig 1-10), and the referenced GitHub repository contents. Statistical details, effect sizes, and raw data are not directly assessable.

## Reviewer
- **Overall assessment** This manuscript addresses a significant and timely question in transcriptional regulation: how multiple AR-bound enhancers contribute to target gene expression. The authors have generated a substantial multi-omics dataset and propose a "dominance model" that is conceptually interesting and potentially impactful. However, the current text, without access to figures and supplementary materials, leaves several key claims insufficiently supported. The central claims regarding the absence of loop rewiring, the temporal ordering of epigenetic events, and the dominance model's predictive power require careful scrutiny of the underlying data, which are not visible in the provided material. The manuscript is well-written and the conceptual framework is appealing, but the evidence base as presented is incomplete for a definitive assessment.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, nuclear receptor biology, chromatin organization, and gene expression control would be interested. The work is also relevant to prostate cancer biology given the AR focus. The multi-omics integration approach and the proposed dominance model could inform studies on enhancer-promoter communication and the functional interpretation of chromatin contact data.
- **Major strengths** The study design is comprehensive, integrating multiple genomic assays across a time course. The focus on contact frequency rather than loop presence is a nuanced and important distinction. The proposed dominance model is testable and the CRISPRi validation is a strong addition. The use of a graph-based framework for integrating multi-omic data is a modern and appropriate approach.
- **Major Concerns** The major concerns are detailed below. They primarily relate to the lack of visible data to support key claims, the potential for technical artifacts in HiChIP analysis, and the generalizability of the dominance model.
- **Minor Comments** Several minor points regarding clarity, statistical reporting, and interpretation are listed below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria**  
  - **Originality** High. The concept of "dominant" enhancers with proportional contact frequency effects, validated by CRISPRi, is a valuable contribution beyond existing models.  
  - **Scientific importance** High. Understanding how multiple enhancers integrate to control gene expression is a fundamental question. The findings have implications for interpreting disease-associated non-coding variants.  
  - **Interdisciplinary readership** Moderate to high. The work bridges genomics, epigenetics, and computational biology. The clear writing makes it accessible to a broad biological audience.  
  - **Technical soundness** Currently not fully assessable. The methods are described in detail, but the absence of figures and supplementary data prevents verification of the key results and statistical claims.  
  - **Readability for nonspecialists** Good. The abstract and introduction are clear. The results and discussion are logically structured, though some sections assume familiarity with genomic techniques.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual advance is significant, but the current evidence base, as presented, is insufficient to fully establish the claims. Access to the figures and supplementary data is essential for a complete evaluation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "AR binding induces sequential changes in the epigenetic features at CREs, independent of gene expression" and that "binding of AR does not result in a substantial rewiring of chromatin loops, but instead increases the contact frequency of pre-existing loops to target promoters."
- **Evidence pointer** Results sections "Androgen stimulation leads to stepwise epigenetic changes" and "AR-bound enhancers increase contact frequency to AR-upregulated gene promoters"; Figures 2 and 3 (not provided)
- **Concern** The central claims of sequential epigenetic changes and the absence of loop rewiring are based on data presented in figures that were not provided. The text describes trends (e.g., "reached its peak at 4h and then subsequently decreased") but does not provide effect sizes, confidence intervals, or statistical test results. The claim that loop rewiring does not occur is a strong negative result that requires robust evidence, including a demonstration that the HiChIP assay is sensitive enough to detect changes if they existed. The comparison of loop numbers across time points is mentioned, but the actual numbers and statistical comparisons are not visible.
- **Why it matters** These are the foundational observations of the paper. If the temporal ordering is not robust or if loop rewiring does occur to some extent, the proposed model would need substantial revision. The negative result on loop rewiring is particularly important because it contrasts with earlier literature.
- **Resolution test** Provide the figures with clear statistical annotations (e.g., error bars, p-values, effect sizes) for all time-course comparisons. For the loop rewiring claim, include a power analysis or a positive control demonstrating the assay's ability to detect induced loop changes. Show the distribution of loop numbers and contact frequencies for all time points.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validity
- **Claim pointer** The authors state that "we instead generated a reference loop set, normalized the count matrix, and compared contact frequencies similar to published work."
- **Evidence pointer** Methods section "Bioinformatics Analyses"
- **Concern** The decision to merge HiChIP data from all time points to create a reference loop set is a critical methodological choice. This approach can introduce bias, as loops that are present only at specific time points may be diluted or missed. The authors do not discuss the potential impact of this merging on their ability to detect time-specific changes in loop presence or contact frequency. The normalization procedure (TMM) is mentioned, but the details of how the reference set is used for per-time-point comparisons are not fully described.
- **Why it matters** If the reference loop set is biased, the subsequent analysis of contact frequency changes could be systematically flawed, potentially leading to the false conclusion that no rewiring occurs.
- **Resolution test** Provide a detailed description of how the reference loop set was constructed and validated. Show that the reference set is representative of all time points. Perform a sensitivity analysis, e.g., by calling loops per time point and comparing the results to the reference set approach. Discuss the potential limitations and biases of this method.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that "the dominant loops were not solely based on proximity to the gene promoter as they were the closest CRE in only 27% of AR-regulated genes (n=24) at any time point."
- **Evidence pointer** Results section "Multi-enhancers influence transcription proportional to contact frequency"; Supp Fig 8 (not provided)
- **Concern** The identification of "dominant" loops relies on a threshold (scaled contact frequency > 0.8) that is not justified. The choice of this threshold could significantly affect the results. The statistical significance of the 27% figure is not assessed; it is unclear if this is significantly different from what would be expected by chance. The analysis of dominance is performed on a small subset of genes (n=88), and the generalizability of the findings is unclear.
- **Why it matters** The dominance model is a key conceptual contribution. If the identification of dominant loops is arbitrary or not statistically robust, the model's validity is weakened.
- **Resolution test** Justify the threshold for dominance with a data-driven approach or a sensitivity analysis. Provide a statistical test comparing the observed 27% to a null expectation. Discuss the selection of the 88 genes and whether the findings are representative of all AR-regulated genes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors state that "we found that the dominant AR-bound CREs (D+) had significantly (p<0.0001) higher dynamic change in contact frequency than non-dominant AR-bound CREs (D-) that interacts with AR-regulated gene promoters."
- **Evidence pointer** Results section "Multi-enhancers influence transcription proportional to contact frequency"; Figure 5C (not provided)
- **Concern** The p-value is reported, but the effect size and the number of observations are not. The text does not describe the statistical test used. The comparison between D+ and D- is central to the model, but the data supporting it are not visible.
- **Why it matters** This is a direct test of the dominance model. Without details on the effect size and the test used, the significance of the finding cannot be evaluated.
- **Resolution test** Provide the effect size, the number of D+ and D- loops, and the specific statistical test used. Show the data distribution in Figure 5C.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "inhibiting those CREs, that had a dominant chromatin loop, significantly impacted androgen-induced transcription" and that "the highest gene expression inhibition is observed at these ARBSs."
- **Evidence pointer** Results section "CRISPR-based perturbations confirm the existence of 'dominant' chromatin loops"; Figure 6 (not provided)
- **Concern** The CRISPRi validation is a critical component of the paper. The text states that inhibition of dominant loops impacted transcription, but the magnitude of the effect, the number of replicates, and the statistical analysis are not provided. The claim that the highest inhibition is observed at the dominant ARBSs is qualitative and not supported by visible data. The text also does not discuss potential off-target effects or the efficiency of the CRISPRi knockdown.
- **Why it matters** This is the experimental validation of the model. Without robust data, the model remains correlative.
- **Resolution test** Provide the full CRISPRi data, including the number of independent experiments, the effect sizes, and the statistical tests. Show the data in Figure 6. Discuss the efficiency of the CRISPRi system and any potential off-target effects.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Bioinformatics Analyses"
- **Evidence pointer** Methods section
- **Issue** The description of the graph-based framework is brief. The text states that "any pair of CREs are included as nodes in the network with TMM normalized HiChIP contact frequency as weighted edges," but it is unclear how the network is used for the downstream analyses (e.g., identifying dominant loops, calculating first-degree summaries).
- **Required correction** Provide a more detailed description of the network construction and the specific graph algorithms used for the analyses.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, "Androgen stimulation leads to stepwise epigenetic changes"
- **Evidence pointer** Results section
- **Issue** The text states that "there was no statistically significant change at any time point in the AR-bound enhancers of either up or downregulated genes (p>0.1)." The specific test used is not mentioned, and the p-value threshold is unusual.
- **Required correction** Specify the statistical test used and report the exact p-values or a range.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion states that "recent work has suggested that gene expression may occur through already-existing interactions." The authors do not cite this work in the provided text, making it difficult to contextualize their findings.
- **Required correction** Add the relevant citation(s) to support this statement.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Experimental"
- **Evidence pointer** Methods section
- **Issue** The methods state that "LNCaP cells were authenticated by sequencing and comparing short tandem repeats to parental LNCaP cells in the ATCC database." The specific STR loci analyzed are not listed.
- **Required correction** List the STR loci used for authentication.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Multi-enhancers influence transcription proportional to contact frequency"
- **Evidence pointer** Results section
- **Issue** The text mentions "first-degree summarization models (average, maximum, and sum)" but does not clearly define what "first-degree" means in this context.
- **Required correction** Define "first-degree" in the text or refer to a figure that illustrates the concept.

## Risk / unsupported claims
- The claim that AR binding induces sequential epigenetic changes independent of gene expression is not fully supported without the time-course data and statistical analyses.
- The claim that no substantial loop rewiring occurs is a strong negative result that is not adequately supported without a demonstration of assay sensitivity and a detailed comparison of loop numbers.
- The dominance model's predictive power is not fully established without the full CRISPRi dataset and the statistical analysis of the correlation between contact frequency changes and expression changes.
- The generalizability of the dominance model to all AR-regulated genes is unclear, as the analysis is performed on a small subset of genes.
- The statement that "the same dominant loops were commonly found at every time point" is not supported by visible data.
- The claim that the dominance model aligns with the ABC model is an interpretation that is not directly tested in this manuscript.