## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions)
- **Assessment boundary** Scientific validity of the bioinformatic predictions, experimental confirmation, and interpretation of VDR/Partner composite elements
- **Shared manuscript claim summary** The authors propose that VDR can form functional complexes with transcription factors other than RXRA, specifically NR2C2 and PPARG, and that novel VDR/Partner composite elements in regulatory DNA of immune genes mediate vitamin D effects in atopic and respiratory diseases
- **Visible evidence base** Bioinformatics predictions (Web-MCOT, ChIP-Seq data from THP-1), AlphaFold protein complex modeling, RT-qPCR expression data in U937 cells, literature-based gene function annotations
- **Missing materials affecting confidence** Supplementary figures/tables referenced but not provided; no ChIP-seq validation of predicted CEs; no reporter assays or binding experiments; no protein-level confirmation of VDR-partner complexes in cells; statistical details incomplete

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in vitamin D biology, namely whether VDR can act through non-canonical partner transcription factors. The bioinformatic approach is reasonable and the identification of NR2C2 and PPARG as candidate partners is interesting. However, the experimental evidence is limited to mRNA expression changes in a single cell line, and the link between predicted CEs and observed expression changes is correlative rather than causal. The manuscript would benefit from direct binding assays, reporter gene experiments, or ChIP-qPCR to substantiate the functional relevance of the predicted composite elements. The discussion is speculative in places and the conclusions outpace the evidence presented.

- **Who would be interested in the results, and why** Researchers studying vitamin D signaling, transcriptional regulation, innate immunity, and respiratory/allergic disease pathogenesis. The potential identification of novel VDR partner factors could inform therapeutic strategies targeting vitamin D pathways in asthma, atopic dermatitis, and respiratory infections.

- **Major strengths** 
  1. The hypothesis is clearly formulated and addresses a genuine gap in the field, namely the low frequency of canonical VDR/RXRA CE identification in ChIP-Seq data
  2. The combination of computational prediction (Web-MCOT), structural modeling (AlphaFold), and experimental validation (RT-qPCR) represents a multi-pronged approach
  3. The selection of genes with clear relevance to atopic and respiratory diseases enhances translational significance
  4. The authors acknowledge limitations regarding cell line differences and competing binding scenarios

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The manuscript claims that predicted VDR/NR2C2 and VDR/PPARG composite elements are functionally relevant for vitamin D-mediated gene regulation
- **Evidence pointer** Section 2.2, Figure 2, Table 4
- **Concern** The experimental evidence consists solely of RT-qPCR measurements of mRNA levels in U937 cells treated with calcitriol. No direct evidence is provided that the predicted composite elements are bound by VDR-partner complexes, that they are required for the observed transcriptional responses, or that the proposed VDR-NR2C2/PPARG interactions occur in these cells. The correlation between predicted CE presence and expression changes is suggestive but does not establish causality.
- **Why it matters** Without functional validation of the predicted CEs, the central claim of the paper remains speculative. The field requires evidence that these elements are occupied by the proposed transcription factor complexes and that their disruption abolishes vitamin D responsiveness.
- **Resolution test** Provide ChIP-qPCR or ChIP-seq data demonstrating VDR and partner factor occupancy at the predicted CE loci in U937 or THP-1 cells; perform reporter gene assays with wild-type and mutated CE sequences; or use siRNA/CRISPR knockdown of NR2C2/PPARG to show loss of vitamin D-mediated regulation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors state that calcitriol increased expression of PDCD1LG2, NFKBIA, IRF5, and LGALS9, with statistical significance at p < 0.05
- **Evidence pointer** Section 2.2, Figure 2, Section 4.2.5
- **Concern** The statistical methods are inadequately described. The authors state that Student's t-test was applied for pairwise comparisons, but no information is provided on whether data were normally distributed, whether multiple testing corrections were applied, or how many independent experiments were performed. The results are presented as "mean values" without error bars or dispersion measures in the text description. The figure is not available for inspection.
- **Why it matters** The reliability of the expression data underpins the entire experimental section. Inadequate statistical reporting prevents assessment of effect robustness and increases risk of false-positive findings, particularly given the small number of genes tested.
- **Resolution test** Provide full statistical details including number of biological replicates, dispersion measures, normality testing, and multiple comparison corrections. Show individual data points or error bars in figures. Consider reporting effect sizes and confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Bioinformatics rigor
- **Claim pointer** The authors claim that Web-MCOT identified NR2C2 and PPARG as top candidate VDR partners with high statistical significance
- **Evidence pointer** Section 2.1, Table 1, Figure 1
- **Concern** The description of the bioinformatic analysis is insufficiently detailed. The authors do not specify the parameters used for Web-MCOT, the background model for significance testing, how multiple testing was handled across the large number of motifs tested, or how the threshold for "top 10" was determined. The p-values reported for individual motifs (e.g., 9.1 × 10⁻³⁴ for NR2C2) are presented without context regarding the total number of motifs tested.
- **Why it matters** Without clarity on the statistical framework, the reader cannot assess whether the identified motifs represent true enrichments or artifacts of multiple testing. This is particularly important given that the authors themselves note that PPARA may be an artifact due to motif similarity with PPARG.
- **Resolution test** Provide complete Web-MCOT parameters, background model description, multiple testing correction method, and the total number of motifs tested. Show the full distribution of p-values or q-values to demonstrate that the top hits are outliers.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Cell line relevance
- **Claim pointer** The authors use U937 cells for experimental validation while the bioinformatic predictions were derived from THP-1 ChIP-Seq data, and they acknowledge potential differences between cell lines
- **Evidence pointer** Section 2.2, Section 4.2.1
- **Concern** The mismatch between the cell line used for ChIP-Seq (THP-1) and the cell line used for expression validation (U937) introduces a significant confound. The authors acknowledge this but do not address it experimentally. Chromatin accessibility, transcription factor expression levels, and enhancer activity can differ substantially between cell lines, even those of similar origin. The authors state that VDR, RXRA, PPARG, and NR2C2 are expressed in U937 but provide no data supporting this claim.
- **Why it matters** The validity of extrapolating CE predictions from THP-1 to U937 is unverified. If the chromatin landscape differs, the predicted CEs may not be accessible or functional in U937 cells, undermining the interpretation of the expression data.
- **Resolution test** Provide expression data for VDR, RXRA, PPARG, and NR2C2 in U937 cells. Ideally, perform ChIP-seq or ATAC-seq in U937 cells to confirm that the predicted CE regions are accessible. Alternatively, validate predictions in THP-1 cells directly.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of AlphaFold results
- **Claim pointer** The authors use AlphaFold to model VDR-NR2C2 complex formation as supporting evidence for their hypothesis
- **Evidence pointer** Section 2.1, Supplementary Figure S1
- **Concern** The AlphaFold modeling is mentioned only briefly, and the supplementary figure is not available for review. No details are provided regarding the confidence scores, the specific domains predicted to interact, or how the predicted complex relates to DNA binding. AlphaFold predictions of protein-protein interactions, while valuable, do not demonstrate that such complexes form in cells or that they bind DNA cooperatively.
- **Why it matters** The AlphaFold result is presented as supporting evidence but cannot be evaluated without details. Overinterpretation of computational structural predictions could mislead readers about the strength of evidence for VDR-NR2C2 complex formation.
- **Resolution test** Provide AlphaFold confidence metrics (pLDDT, PAE), show the predicted interface residues, and discuss whether the predicted interaction mode is consistent with known VDR and NR2C2 DNA-binding mechanisms. Ideally, validate the interaction using co-immunoprecipitation or proximity ligation assays.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, Table 1
- **Evidence pointer** Table 1
- **Issue** The criteria for selecting the "top 10" motifs are not stated. It is unclear whether this is based on p-value, q-value, or a combined score.
- **Required correction** State the ranking criterion explicitly in the text or table legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.1, Table 2
- **Evidence pointer** Table 2
- **Issue** The ChEA 2022 analysis is mentioned but the methodology for this analysis is not described in the Methods section.
- **Required correction** Add a brief description of how the ChEA 2022 analysis was performed, including the input gene set and significance thresholds.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section 2.2, Figure 2
- **Evidence pointer** Figure 2
- **Issue** The text states that NOD2 and CD14 "did not respond to calcitriol" but does not provide the actual data or statistical comparison for these genes.
- **Required correction** Report the expression values and statistical results for all tested genes, including those with no significant change.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.4
- **Evidence pointer** Section 3.4
- **Issue** The discussion of "putative synergism" between CEs is speculative. The authors do not provide a mechanistic model for how two CEs at distant locations would synergize.
- **Required correction** Clarify whether the proposed synergism involves cooperative DNA binding, chromatin looping, or additive transcriptional activation, and discuss alternative interpretations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Section 4.2.1
- **Evidence pointer** Section 4.2.1
- **Issue** The concentration of calcitriol used (10 nM and 100 nM) is stated, but the solvent control conditions are not described.
- **Required correction** Specify the vehicle control used and confirm that solvent alone had no effect on gene expression.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 4.2.4
- **Evidence pointer** Section 4.2.4
- **Issue** The 2−∆∆Ct method is cited but the reference for this method is not provided.
- **Required correction** Add the appropriate citation for the 2−∆∆Ct method (e.g., Livak and Schmittgen, 2001).

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Section 2.1, Table S1
- **Evidence pointer** Table S1
- **Issue** The supplementary table listing all 98 genes is not provided in the manuscript.
- **Required correction** Ensure supplementary materials are accessible and referenced appropriately.

## Risk / unsupported claims
- The claim that VDR/NR2C2 and VDR/PPARG CEs are functionally relevant for vitamin D-mediated gene regulation is unsupported by direct experimental evidence; only correlative mRNA expression data are provided
- The claim that AlphaFold modeling supports VDR-NR2C2 complex formation cannot be evaluated without the supplementary figure and confidence metrics
- The assertion that RXRA would "likely displace" PPARG and NR2C2 in competing binding scenarios is speculative and not experimentally tested
- The extrapolation of bioinformatic predictions from THP-1 to U937 cells is unvalidated
- The statement that "changes in expression levels are directly correlated to the number of VDR/Partner CEs" (Haussler model) is presented as a framework but not quantitatively tested in this study
- The clinical relevance of the findings for atopic dermatitis, asthma, allergic rhinitis, and pulmonary infections is inferred from gene function annotations rather than demonstrated experimentally