## Review setup
- **Input scope** Full manuscript text, including abstract, results, discussion, methods, and figure legends as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors investigate the molecular basis for divergent co-TF (Pho2) dependence between two Pho4 orthologs in yeast. They propose and test two non-mutually exclusive models: enhanced activity and autoinhibition. Through chimeric TF analysis, they identify three key differences: (1) CgPho4 binds DNA with 3–4-fold higher affinity, (2) CgPho4 contains two activation enhancer domains (AEDs) in intrinsically disordered regions, and (3) ScPho4 has a dual-function Pho2 interaction domain (P2ID) that both enhances activity with Pho2 and inhibits activity without it.
- **Visible evidence base** Figures 1–7 (as referenced), Supplementary Figures 1–9, Table 1, and Methods section. Specific data points and statistical values are referenced but not all raw data are visible in the provided text.
- **Missing materials affecting confidence** Raw data files, full figure panels with all subpanels, exact numerical values for all measurements, and complete statistical outputs are not fully visible. The Source Data file and GEO accessions are mentioned but not accessible in this review context.

## Reviewer

- **Overall assessment** This manuscript presents a thorough and systematic dissection of the molecular basis for divergent co-TF dependence in two Pho4 orthologs. The chimeric approach is well-designed and the identification of multiple contributing regions, particularly the unexpected role of IDRs, is a valuable contribution. The work is technically sound in most aspects, but several concerns regarding data interpretation, statistical rigor, and mechanistic depth need to be addressed. The study is likely to be of interest to researchers in gene regulation, transcription factor biology, and evolutionary biology.

- **Who would be interested in the results, and why** Researchers studying eukaryotic transcription factor function and combinatorial control, particularly those interested in the role of intrinsically disordered regions in TF activity. Evolutionary biologists studying how gene regulatory networks evolve. Yeast molecular biologists working on the PHO pathway. The findings on IDR-mediated modulation of activation potential and autoinhibition have broader implications for understanding TF regulation beyond the specific system studied.

- **Major strengths** The study uses a comprehensive chimeric approach with 50 constructs, providing a systematic map of functional regions. The combination of in vitro DNA binding assays (BLI, EMSA, PBM) with in vivo activity measurements is rigorous. The identification of AEDs as a new class of regulatory elements in IDRs is novel. The dual-function P2ID concept is elegantly demonstrated. The authors test and integrate two models rather than treating them as mutually exclusive.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** The authors claim that "CgPho4 binds the same consensus motif with a higher affinity compared to ScPho4" and that this contributes to reduced Pho2 dependence.
- **Evidence pointer** Figure 2D, E; Supplementary Figure 4; Results section "CgPho4 binds the same consensus motif with a higher affinity compared to ScPho4"
- **Concern** The binding affinity difference (KD = 5.2 nM vs 1.2 nM) is measured using isolated DBDs in vitro. However, the chimeric experiments show that swapping the DBD alone does not increase activity, and in fact reduces it. The authors acknowledge this discrepancy but do not resolve it. The claim that binding affinity contributes to Pho2 independence is not directly supported by the functional data. The authors suggest that the effect may only manifest at lower nuclear Pho4 concentrations, but this is speculative and not tested.
- **Why it matters** The title and abstract emphasize the role of IDRs, but the binding affinity difference is presented as one of three key findings. If the functional relevance of this affinity difference is not demonstrated, the claim is weakened. The authors need to either provide direct evidence for the functional impact of the affinity difference or temper the claim.
- **Resolution test** Provide experimental evidence showing that the affinity difference affects gene expression under conditions where nuclear Pho4 is limiting. Alternatively, revise the claim to state that the affinity difference is a correlative observation whose functional significance remains to be determined.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors state that "R1:Cg and NLS:Cg each had significant, positive effects on their own on both APHO2 and Apho2∆" and that there is "positive epistasis with AD:Cg."
- **Evidence pointer** Figure 5D; Methods section "Epistasis between regions R1, AD, and NLS of CgPho4"
- **Concern** The linear model used to estimate main effects and interactions is described, but the results are only shown as a heatmap. The actual coefficients, standard errors, and confidence intervals are not presented. The Holm-Bonferroni correction is mentioned, but the number of tests and the specific P-values are not reported. Without these details, it is difficult to assess the robustness of the claimed epistatic effects.
- **Why it matters** The epistasis analysis is central to the conclusion that multiple IDRs contribute non-additively to Pho2 dependence. If the statistical evidence is not transparent, the conclusion is not fully supported.
- **Resolution test** Provide a supplementary table with all model coefficients, standard errors, t-statistics, raw and corrected P-values for the epistasis analysis. Include confidence intervals for the effect sizes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic depth
- **Claim pointer** The authors propose that the P2ID in ScPho4 has a dual function: "allowing for enhanced activity with Pho2 and restricting its activity without Pho2."
- **Evidence pointer** Figure 6A–C; Results section "A double-edged sword"
- **Concern** The dual-function model is inferred from chimeric constructs, but the molecular mechanism is not explored. How does the P2ID inhibit activity in the absence of Pho2? Is it an autoinhibitory intramolecular interaction? Does it involve conformational changes? The authors do not provide any biochemical or biophysical evidence for the proposed autoinhibition mechanism.
- **Why it matters** The autoinhibition model is a key part of the paper's conceptual framework. Without mechanistic evidence, the model remains speculative. The authors cite a previous study suggesting autoinhibition but do not build on it with new data.
- **Resolution test** Perform experiments to directly test autoinhibition, such as intramolecular FRET, limited proteolysis, or hydrogen-deuterium exchange, comparing ScPho4 with and without Pho2. Alternatively, use mutations in the P2ID that disrupt autoinhibition and show they affect activity in the predicted manner.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state that "our study provides a detailed molecular picture of how co-TF dependence is mediated and how it evolves, particularly through IDR changes."
- **Evidence pointer** Discussion section
- **Concern** The study is limited to two Pho4 orthologs. The authors mention preliminary analysis of eight orthologs in the Discussion (Supplementary Fig. 8), but this is not described in the Results and the data are not shown in the provided text. The claim of a "detailed molecular picture" of evolution is overstated given the limited taxonomic sampling.
- **Why it matters** The broader evolutionary conclusions depend on demonstrating that the identified mechanisms are generalizable across Pho4 orthologs. Without presenting the comparative data, the claim is not supported.
- **Resolution test** Include the analysis of eight Pho4 orthologs in the Results section with full data presentation. If the data are preliminary, temper the evolutionary claims accordingly.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1C
- **Evidence pointer** Figure 1C
- **Issue** The domain architecture diagram is described in the text but the figure itself is not visible in the provided text. The boundaries for R1, AD, NLS, P2ID, and DBD are listed in Table 1, but it would be helpful to have a clear visual representation.
- **Required correction** Ensure Figure 1C clearly labels all domains with amino acid positions and indicates the breakpoints used for chimeric constructs.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Yeast one-hybrid and yeast two-hybrid"
- **Evidence pointer** Methods section
- **Issue** The yeast one-hybrid assay uses a GAL1pr-mCherry reporter, but the specific strain background and the details of the flow cytometry gating strategy are not fully described. The number of biological replicates for each construct is not stated.
- **Required correction** Provide the full genotype of the reporter strain, the number of independent transformants tested, and the gating strategy used for flow cytometry analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5A
- **Evidence pointer** Figure 5A
- **Issue** The activity values for 32 chimeric constructs are shown in a single panel. It is difficult to discern individual data points and variability. The authors state that "ratios between the two were consistent and characteristic of the specific construct," but the variability is not shown.
- **Required correction** Consider showing individual data points with error bars for each construct, or provide a supplementary table with mean, standard deviation, and number of replicates for each construct.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, paragraph on binding affinity
- **Evidence pointer** Discussion section
- **Concern** The authors discuss the potential impact of the binding affinity difference but do not address the possibility that the higher affinity of CgPho4 might be due to the R252K change in the basic region. This residue is conserved in ScPho4 but not in CgPho4.
- **Required correction** Discuss whether the R252K change could affect DNA binding affinity and whether this has been tested experimentally.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, paragraph 1
- **Evidence pointer** Introduction
- **Issue** The introduction cites references 1–9 but does not discuss recent work on IDRs in transcription factors, which is directly relevant to the study. The authors should place their findings in the context of the growing literature on IDR function in TFs.
- **Required correction** Add a brief discussion of recent studies on IDR-mediated regulation of TF activity and evolution, with appropriate citations.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results, "Domain organization and sequence divergence"
- **Evidence pointer** Results section
- **Issue** The term "P2ID" is used to describe a region that interacts with both Pho80 and Pho2. However, the authors later show that the first half of P2ID interacts with Pho2 and the second half has an autoinhibitory function. The name "P2ID" may be misleading.
- **Required correction** Consider renaming the region or clearly defining the sub-functions of the two halves in the text.

## Risk / unsupported claims
- The claim that the binding affinity difference contributes to Pho2 independence is not directly supported by functional data and remains speculative.
- The claim of a "detailed molecular picture" of co-TF dependence evolution is overstated given the limited taxonomic sampling (two orthologs).
- The preliminary analysis of eight Pho4 orthologs (Supplementary Fig. 8) is mentioned but not described in the Results, making it impossible to evaluate.
- The mechanistic basis for the proposed autoinhibition by P2ID is not experimentally tested.
- The functional significance of the AEDs in the native context is inferred from chimeric constructs but not directly validated in CgPho4.