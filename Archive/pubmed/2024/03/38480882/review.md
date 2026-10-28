## Review setup
- **Input scope** Full manuscript text including methods, extended data descriptions, and supplementary material references
- **Assessment boundary** Scientific claims, methodological rigor, and evidence quality as presented in the provided text; no external data or unpublished materials were accessed
- **Shared manuscript claim summary** The authors propose that AIRE's target gene specificity in thymic T-cell tolerization is governed by Z-DNA-forming motifs at gene promoters, which promote DNA double-strand breaks (DSBs) that facilitate transcriptional poising and subsequent AIRE binding, with Nfe2l2 as a cooperating transcription factor
- **Visible evidence base** CNN-based sequence analysis, in silico mutagenesis, natural genetic variation (B6/NOD F1 hybrids), ChIP-seq, ATAC-seq, BLISS, CUT&Tag, ChIPmentation, bulk and single-cell RNA-seq, and pharmacological interventions (spermidine, topotecan)
- **Missing materials affecting confidence** Figure panels referenced but not fully described in text (e.g., exact effect sizes for several comparisons), supplementary notes and tables not provided, detailed statistical outputs for some analyses, and complete information on replication numbers for certain experiments

## Reviewer
- **Overall assessment** This manuscript presents a compelling and multi-faceted investigation into the molecular logic underlying AIRE's target gene selection, a long-standing question in immunology. The authors employ an impressive array of complementary approaches, from deep learning-based sequence analysis to sophisticated genetic and pharmacological perturbations in vivo. The convergence of evidence from computational predictions, natural genetic variation, and direct experimental manipulation strongly supports the central hypothesis that Z-DNA-forming motifs are key determinants of AIRE target specificity. The proposed mechanism, involving Z-DNA-promoted DSBs and transcriptional poising, is mechanistically plausible and well-supported by the data presented. However, several technical concerns regarding the specificity of the Z22 antibody, the interpretation of spermidine effects, and the quantitative strength of some correlations warrant careful consideration before the conclusions can be fully accepted.

- **Who would be interested in the results, and why** This work will be of significant interest to immunologists studying central tolerance and autoimmune disease mechanisms, as it provides a novel framework for understanding how AIRE selects its thousands of target genes. Additionally, the findings will appeal to molecular biologists investigating non-B DNA structures and their regulatory roles in transcription, as well as computational biologists interested in applying deep learning to decipher cis-regulatory codes. The potential connection between Z-DNA, DSBs, and transcriptional regulation has broad implications beyond the thymus, making this relevant to researchers studying genome stability, chromatin dynamics, and gene regulation in various contexts.

- **Major strengths** 
  1. The study employs an exemplary multi-pronged approach, integrating computational prediction with experimental validation across multiple levels (genomic, transcriptomic, and functional).
  2. The use of natural genetic variation between mouse strains as an orthogonal validation strategy is particularly elegant and provides strong causal evidence.
  3. The pharmacological interventions with spermidine and topotecan offer direct functional tests of the proposed mechanism.
  4. The authors are careful to distinguish between AIRE binding and AIRE-dependent gene upregulation, addressing a common confound in the field.
  5. The manuscript is generally well-written and accessible, with clear methodological detail.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that Z-DNA is detected at gene promoters in mTECs using the Z22 antibody, and that Z-DNA levels correlate with AIRE binding and gene expression.
- **Evidence pointer** ChIP-seq using Z22 antibody; Figure 3a-c; Methods section "ChIP-seq library preparation"
- **Concern** The Z22 antibody is known to cross-react with both Z-DNA and Z-RNA, and its specificity for Z-DNA in the context of chromatin immunoprecipitation has been questioned. While the authors state that Z-RNA was removed during the ChIP-seq procedure, the details of this removal are not provided in the main text. Given the central role of Z-DNA detection in this study, it is critical to demonstrate that the ChIP signal is specifically due to Z-DNA and not Z-RNA or other cross-reactive epitopes. The authors should provide validation experiments, such as competition assays with Z-DNA versus Z-RNA, or genetic perturbations that eliminate Z-RNA.
- **Why it matters** If the Z22 ChIP signal is not specific to Z-DNA, the entire premise of the study, that Z-DNA is enriched at AIRE target promoters, would be undermined. This is a foundational claim upon which subsequent mechanistic experiments are built.
- **Resolution test** Provide additional validation of Z22 specificity in mTECs, including but not limited to: (1) RNase A versus RNase III treatment to distinguish Z-DNA from Z-RNA; (2) competition with excess Z-DNA or Z-RNA oligonucleotides; (3) demonstration that Z22 ChIP signal is lost in cells treated with a Z-DNA-stabilizing drug that does not affect Z-RNA; or (4) orthogonal detection of Z-DNA using an alternative method (e.g., a different antibody or a chemical probe).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that spermidine treatment enhances Z-DNA formation, which in turn increases DSB generation and AIRE-dependent gene expression, based on the observation that spermidine partially rescues AIRE loss in knockout mice.
- **Evidence pointer** Figure 3d; Extended Data Figure 5; Methods section "Mice"
- **Concern** Spermidine is a polyamine with pleiotropic cellular effects, including modulation of chromatin structure, translation, and autophagy. The authors attribute the observed effects on gene expression and DSB formation specifically to Z-DNA stabilization, but they do not provide direct evidence that spermidine's effects in their system are mediated through Z-DNA. For instance, they do not show that spermidine increases Z-DNA levels in mTECs (e.g., by Z22 ChIP) or that the effects are dependent on the presence of Z-DNA-forming motifs. The claim that spermidine "partially rescues" AIRE loss is based on a modest proportion of genes (8.5% with fold-change >2), and the specificity of this effect to Z-DNA-containing promoters is not fully demonstrated.
- **Why it matters** The spermidine experiments are presented as key functional evidence for the role of Z-DNA in AIRE function. If spermidine's effects are not specifically due to Z-DNA stabilization, the causal link between Z-DNA and AIRE-dependent gene expression is weakened.
- **Resolution test** Provide direct evidence that spermidine treatment increases Z-DNA formation at AIRE target promoters in mTECs (e.g., by Z22 ChIP-seq before and after treatment). Additionally, demonstrate that the spermidine-induced gene expression changes are enriched at genes with Z-DNA-forming motifs compared to those without, and that this enrichment is statistically significant after controlling for other factors such as baseline expression level.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor
- **Claim pointer** The authors claim that "longer Z-DNA motifs" and "more proximal" Z-DNA motifs are associated with a higher likelihood of a gene being AIRE-induced, based on the analysis shown in Figure 1g,h.
- **Evidence pointer** Figure 1g,h; Methods section "Weakly expressed genes"
- **Concern** The analysis in Figure 1g,h appears to be based on a univariate approach, examining the effect of Z-DNA motif length and distance from TSS separately. However, these two features are likely correlated (e.g., longer motifs may tend to be more proximal or vice versa), and other genomic features (e.g., CpG content, chromatin state, presence of other transcription factor motifs) could confound the observed associations. A multivariate analysis that simultaneously considers multiple features would strengthen the claim that Z-DNA motif properties are independently predictive of AIRE targeting.
- **Why it matters** The quantitative relationship between Z-DNA features and AIRE targeting is a central claim of the paper. If the observed associations are confounded by other variables, the specificity of the Z-DNA effect would be called into question.
- **Resolution test** Perform a multivariate logistic regression or similar analysis, including Z-DNA motif length, distance from TSS, and other relevant genomic features (e.g., baseline expression, chromatin accessibility, presence of Nfe2l2 motifs) as predictors of AIRE-induced status. Report the independent contribution of Z-DNA features after controlling for covariates.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretational clarity
- **Claim pointer** The authors propose a model in which Z-DNA-promoted DSBs at AIRE target promoters enhance transcriptional poising, and that this is a prerequisite for AIRE binding and function.
- **Evidence pointer** Figure 4a-e; Extended Data Figure 7-8; Discussion section
- **Concern** The causal ordering of events in the proposed model is not fully established. While the data show correlations between Z-DNA, DSBs, chromatin accessibility, and AIRE binding, the temporal relationship is unclear. For example, it is possible that AIRE binding itself promotes chromatin remodeling and DSB formation, rather than DSBs being a prerequisite for AIRE binding. The experiments with topotecan, which increases DSB persistence, show increased AIRE binding, but this could be an indirect effect of altered chromatin state rather than a direct consequence of DSBs. The authors should discuss alternative models and, ideally, provide time-course experiments or other approaches to establish the temporal hierarchy.
- **Why it matters** The proposed model has important implications for understanding AIRE function and the role of DNA damage in gene regulation. If the causal ordering is incorrect, the mechanistic model would need to be revised.
- **Resolution test** Perform time-course experiments following AIRE activation (e.g., by inducing AIRE expression in a controlled system) to measure the kinetics of Z-DNA formation, DSB generation, chromatin accessibility changes, and AIRE binding. Alternatively, use genetic approaches to ablate DSB repair factors and assess the effect on AIRE function.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of "weakly expressed genes"
- **Evidence pointer** Methods section "Weakly expressed genes"
- **Issue** The threshold for "weakly expressed genes" (TPM < 0.35) is stated, but the rationale for this specific cutoff is not provided. It is unclear whether this threshold was chosen a priori or based on the data.
- **Required correction** Provide a brief justification for the chosen threshold, or state that it was determined empirically and describe the sensitivity of the results to this choice.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** CNN model architecture and training details
- **Evidence pointer** Methods section "CNN model architecture" and "CNN model pre-train"
- **Issue** While the architecture is described in reasonable detail, some hyperparameters (e.g., learning rate schedule, weight initialization, data augmentation) are not specified. This may hinder reproducibility by other groups.
- **Required correction** Provide a complete list of hyperparameters and training details, or make the code publicly available in a repository.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Correlation analyses
- **Evidence pointer** Figure 3c, 4d,e; Extended Data Figure 7a, 8c
- **Issue** For several correlation analyses (e.g., Z-DNA signal vs. AIRE binding, DSB signal vs. chromatin accessibility), the correlation coefficients and p-values are not explicitly stated in the text, making it difficult to assess the strength of the relationships.
- **Required correction** Report the correlation coefficients and p-values for all key correlation analyses, either in the text or in the figure legends.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Nfe2l2 knockout experiments
- **Evidence pointer** Extended Data Figure 9f-i
- **Issue** The Nfe2l2 knockout experiments show a "mild effect" on AIRE-induced gene expression. The authors attribute this to redundancy with other Nfe2l family members, but they do not directly test this hypothesis (e.g., by examining expression of Nfe2l1 and Nfe2l3 in the knockout).
- **Required correction** Either provide data on the expression of other Nfe2l family members in the knockout, or explicitly acknowledge this as a limitation and suggest it as a direction for future work.

## Risk / unsupported claims
- The claim that Z-DNA is specifically detected by the Z22 antibody in mTECs is not fully supported without additional validation of antibody specificity (R1-M1).
- The causal role of Z-DNA in mediating spermidine's effects on gene expression and DSB formation is not directly demonstrated (R1-M2).
- The proposed temporal hierarchy (Z-DNA → DSB → poising → AIRE binding) is not experimentally established; alternative causal orderings are possible (R1-M4).
- The claim that Nfe2l2 cooperates with Z-DNA to regulate AIRE target genes is supported by correlative and loss-of-function data, but the mechanistic details of this cooperation remain speculative.
- The generalizability of the proposed mechanism beyond the thymus and AIRE biology is discussed only briefly and should be considered speculative.