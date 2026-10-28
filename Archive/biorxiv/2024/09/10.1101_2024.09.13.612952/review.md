## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, author contributions, funding, and conflict of interest statements. Figures and tables are referenced but not provided. Supplementary materials are referenced but not provided.
- **Assessment boundary** The scientific claims, experimental design, data analysis approaches, and conclusions as presented in the manuscript text. Structural biology claims based on AlphaFold3 modeling are assessed within the limits of computational prediction. Cross-species comparisons rely on external datasets that are described but not fully accessible within this submission.
- **Shared manuscript claim summary** The authors present DAP-seq analysis of 14 of 16 Arabidopsis SPL transcription factors, identifying two classes based on DNA binding motifs. They report differential binding between paralogs AtSPL9 and AtSPL15, validated by reporter assays. Cross-species comparison with maize and wheat reveals species-specific motif preferences, with wheat SPLs binding longer palindromic motifs. AlphaFold3 modeling suggests protein-protein interactions stabilize dimeric binding in wheat SPLs, potentially explaining motif complexity.
- **Visible evidence base** Abstract, introduction, materials and methods, results narrative, discussion, author contributions, funding, and conflict of interest statements. Figures 1-5 are referenced but not included. Supplementary Tables S1-S4 are referenced but not included. External datasets from Zenodo (DOI 10.5281/zenodo.14991916) and NCBI GEO (GSE188699, GSE104916) are described.
- **Missing materials affecting confidence** All figures and figure legends are absent, preventing direct evaluation of peak distributions, motif logos, heatmaps, structural models, and statistical visualizations. Supplementary tables containing peak lists and reporter assay details are not available. The maize DAP-seq dataset provenance and quality metrics are not described in sufficient detail. The wheat DAP-seq dataset from GSE188699 is described but its original experimental conditions and quality are not independently verified here. Reporter assay details for the DI21 promoter construct are incomplete, including the rationale for choosing this particular promoter and the absence of mutagenesis controls.

## Reviewer

- **Overall assessment** This manuscript presents a valuable and comprehensive DAP-seq dataset for the Arabidopsis SPL transcription factor family, addressing an important gap in understanding DNA binding specificity across this key plant TF family. The identification of two major binding classes, the detailed paralog comparison between AtSPL9 and AtSPL15, and the cross-species analysis with maize and wheat are significant contributions. The integration of AlphaFold3 structural modeling to propose a dimerization-based mechanism for motif diversification is innovative and thought-provoking. However, the manuscript has several technical concerns that need to be addressed. The absence of key experimental validations, particularly for the dimerization hypothesis, weakens the mechanistic claims. The cross-species comparisons rely on datasets with potentially different experimental conditions, and the statistical framework for comparing motif preferences across species needs clarification. The reporter assay validation is limited to a single promoter and lacks appropriate controls. The structural modeling conclusions, while intriguing, are based on predictions that require experimental corroboration. The manuscript would be strengthened by additional validation experiments, clearer statistical reporting, and a more cautious interpretation of the structural predictions.
- **Who would be interested in the results, and why** Plant molecular biologists studying transcription factor families, particularly those interested in SPL/SBP proteins and their roles in development and stress responses. Researchers working on gene regulatory network evolution across plant species will find the cross-species comparisons valuable. The DAP-seq dataset for the Arabidopsis SPL family will serve as a community resource for future studies. Scientists interested in the mechanisms of transcription factor DNA binding specificity, including the role of dimerization, will find the structural modeling and motif analyses relevant. Crop researchers studying maize and wheat architecture and stress responses may benefit from the identification of SPL target genes in these species.
- **Major strengths** The comprehensive coverage of 14 of 16 Arabidopsis SPL family members provides a systematic view of DNA binding specificities within a complete TF family. The identification of two major binding classes based on motif analysis is a clear and useful framework. The paralog comparison between AtSPL9 and AtSPL15 is well-designed and includes both bioinformatic and experimental validation. The cross-species comparison spanning Arabidopsis, maize, and wheat addresses evolutionary questions about TF binding specificity. The use of AlphaFold3 to generate testable hypotheses about dimerization mechanisms is forward-looking. The DAP-seq dataset will be a valuable resource for the plant biology community.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of structural modeling claims
- **Claim pointer** The authors claim that "wheat SPLs preferentially bind to longer, palindromic motifs distinct from the GTAC core motif in Arabidopsis" and that "these motif differences may arise from enhanced protein-protein interactions that stabilize dimeric binding" based on AlphaFold3 structure modeling.
- **Evidence pointer** Results section "Structure modeling links protein-protein interaction preferences to DNA binding motif variation across SPL homologs"; Figure 5
- **Concern** The dimerization hypothesis is supported only by AlphaFold3 predictions. The authors report low confidence scores for the overall structures (ipTM 0.51-0.59, pTM 0.29-0.31) and high fractions of disordered regions (0.80-0.81). While the SBP domain superposition with the crystal structure is reassuring, the claim that protein-protein interactions stabilize dimeric binding to the GTASTAC motif requires experimental validation. The LIS score differences between species-preferred and cross-species motifs are presented as statistical comparisons, but the biological significance of these differences is not established. The authors do not provide any biochemical or biophysical evidence for dimer formation, such as electrophoretic mobility shift assays with purified proteins, size exclusion chromatography, or mutagenesis of predicted dimer interfaces.
- **Why it matters** The dimerization mechanism is a central claim of the paper and is used to explain the evolution of motif complexity across species. If this claim is not experimentally supported, the mechanistic interpretation of the cross-species motif differences remains speculative. The Nature-style criteria for technical soundness require that computational predictions be validated with appropriate experimental approaches, particularly when they form the basis of a mechanistic model.
- **Resolution test** Provide experimental evidence for SPL dimerization, such as EMSA showing cooperative binding to the GTASTAC motif with two protein molecules, or mutagenesis of residues predicted to form the dimer interface that abolishes binding to the longer motif. Alternatively, the authors could temper the claims to present the dimerization model as a hypothesis requiring further testing, and clearly separate the well-supported descriptive findings from the speculative mechanistic model.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of cross-species comparisons
- **Claim pointer** The authors claim that "wheat SPLs preferentially bind to longer, palindromic motifs distinct from the GTAC core motif in Arabidopsis" and that "SPL family members diversify through DNA-binding evolution" based on cross-species comparisons.
- **Evidence pointer** Results section "Comparative analysis of SPL target genes in Arabidopsis, maize, and wheat suggests conserved functions" and "SPL homologs bind to variations of the GTAC motifs"; Figure 4
- **Concern** The cross-species comparison uses DAP-seq data from different sources with potentially different experimental conditions. The maize data were obtained from Zenodo and the wheat data from NCBI GEO, but the authors do not describe how these datasets were generated, what tissues or conditions were used, or whether the peak calling thresholds and quality metrics are comparable across species. The definition of "conserved target genes" relies on homology relationships from Phytozome, but the criteria for establishing orthology and the thresholds for peak sharing across species are not clearly stated. The motif discovery was performed on peaks associated with conserved target genes, but the number of peaks used, the statistical significance of motif enrichment, and the comparison framework for declaring motifs "species-specific" are not described in sufficient detail.
- **Why it matters** The evolutionary conclusions about motif diversification across species depend on the comparability of the underlying datasets. If the DAP-seq conditions differ substantially across species, the observed motif differences could reflect experimental artifacts rather than genuine evolutionary changes. The claim of species-specific motif preferences requires rigorous statistical comparison that accounts for differences in genome size, complexity, and dataset quality.
- **Resolution test** Provide detailed descriptions of the maize and wheat DAP-seq datasets, including experimental conditions, quality metrics, and peak calling parameters. Describe the statistical framework used to compare motif enrichment across species, including how genome size and complexity differences were accounted for. If the datasets are not directly comparable, acknowledge this limitation and temper the evolutionary claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and completeness of reporter assay validation
- **Claim pointer** The authors state "These differences were supported by motif analysis and protoplast reporter assays" referring to differential binding between AtSPL9 and AtSPL15, particularly at the AtDI21 promoter.
- **Evidence pointer** Results section "DAP-seq revealed differential DNA binding specificities between paralogs AtSPL9 and AtSPL15"; Figure 3E; Supplementary Table S1
- **Concern** The reporter assay validation is limited to a single promoter (AtDI21) and lacks important controls. The authors do not describe whether the 758 bp promoter fragment contains additional regulatory elements that could confound the interpretation. There is no mention of mutagenesis experiments to demonstrate that the differential binding is specifically due to the identified motif differences. The number of biological replicates is stated as three, but the statistical analysis used to determine significance is not described. The choice of AtDI21 as the validation target is not justified, and it is unclear whether this promoter is representative of the broader differential binding patterns.
- **Why it matters** The reporter assay is the primary experimental validation for the functional significance of differential binding between AtSPL9 and AtSPL15. Without appropriate controls and a clear statistical framework, the strength of this validation is limited. The claim that differential binding leads to differential gene regulation requires more robust experimental support.
- **Resolution test** Include additional reporter assays with mutated motif sequences to demonstrate that the observed differential regulation is specifically due to the identified binding motifs. Provide details on the statistical analysis used to compare reporter activities. Consider validating differential binding at additional target promoters to demonstrate the generality of the findings.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor of LIS score comparisons
- **Claim pointer** The authors state "Statistical comparisons between predictions for species-preferred versus cross-species motifs (Wilcoxon rank-sum test, p < 0.05; orange background panels in Figure 5D) revealed a consistent and striking pattern."
- **Evidence pointer** Results section "Structure modeling links protein-protein interaction preferences to DNA binding motif variation across SPL homologs"; Figure 5D
- **Concern** The Wilcoxon rank-sum test is used to compare LIS scores between species-preferred and cross-species motifs, but the number of independent samples is unclear. The ten motif instances for each condition may not represent independent observations if they are drawn from the same genomic regions or if the structural predictions are correlated. Multiple testing corrections are not mentioned, despite multiple proteins and conditions being compared. The authors do not report effect sizes or confidence intervals, making it difficult to assess the biological significance of the observed differences.
- **Why it matters** The statistical framework underpins the claim that protein-protein interactions differ between motif types. If the statistical analysis is not rigorous, the mechanistic conclusions drawn from these comparisons are weakened.
- **Resolution test** Clarify the independence of the motif instances used for statistical comparison. Apply appropriate multiple testing corrections. Report effect sizes and confidence intervals in addition to p-values. Consider using mixed-effects models that account for potential correlations between samples from the same protein or genomic region.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of classification criteria
- **Affected element** Results section "Genome-wide binding and DNA sequence motifs support two major classes in the SPL family"
- **Evidence pointer** Figure 2A-B
- **Issue** The criteria for assigning SPL family members to Class A versus Class B are not explicitly stated. The text mentions hierarchical clustering of binding patterns and motif preferences, but the threshold for class assignment and the robustness of the classification are not described.
- **Required correction** Provide explicit criteria for class assignment, including the distance metric used, the clustering method parameters, and a measure of cluster stability such as bootstrap support.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of GO enrichment analysis description
- **Affected element** Results section "Genome-wide binding site analysis of Arabidopsis SPL family by DAP-seq"
- **Evidence pointer** Figure 1E
- **Issue** The GO enrichment analysis is described briefly, but the background gene set, the multiple testing correction method, and the significance threshold are not stated. The heatmap in Figure 1E is referenced but not visible.
- **Required correction** Describe the GO enrichment analysis parameters, including the background set, the correction method, and the significance threshold. Clarify whether the top 10 enriched terms are selected by p-value or by other criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Justification for peak number thresholds
- **Affected element** Results section "Genome-wide binding site analysis of Arabidopsis SPL family by DAP-seq"
- **Evidence pointer** Figure 1A
- **Issue** The number of peaks ranges from 854 to 34,301 across family members, but the authors do not discuss what constitutes a "strong" binding activity or why AtSPL11 and AtSPL13 with fewer peaks are considered less detectable. The relationship between peak number and biological relevance is not addressed.
- **Required correction** Provide context for interpreting peak numbers, such as comparison with known transcription factor datasets or discussion of how peak number relates to binding affinity and biological function.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Description of maize and wheat homolog selection
- **Affected element** Results section "Comparative analysis of SPL target genes in Arabidopsis, maize, and wheat suggests conserved functions"
- **Evidence pointer** Figure 4A-B
- **Issue** The criteria for selecting ZmSBP8/30 and TaSPL7/13 as the maize and wheat homologs of AtSPL9/15 are not described. The text mentions homology from PhytoBestHit, but the sequence identity thresholds and the phylogenetic basis for the orthology assignment are not provided.
- **Required correction** Describe the homology assignment criteria, including sequence identity thresholds and any phylogenetic analysis used to establish orthology.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarification of "conserved target genes" definition
- **Affected element** Results section "Comparative analysis of SPL target genes in Arabidopsis, maize, and wheat suggests conserved functions"
- **Evidence pointer** Figure 4A-B
- **Issue** The definition of "conserved target genes" is ambiguous. The text states that conserved targets are genes associated with peaks shared between homologs, but the criteria for peak sharing and the treatment of one-to-many or many-to-many homology relationships are not described.
- **Required correction** Provide a precise definition of conserved target genes, including the peak overlap criteria and how homology relationships were resolved.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reporting of AlphaFold3 confidence metrics
- **Affected element** Results section "Structure modeling links protein-protein interaction preferences to DNA binding motif variation across SPL homologs"
- **Evidence pointer** Figure 5A-B
- **Issue** The authors report ipTM and pTM scores for the overall structures but do not report local confidence metrics for the specific protein-protein and protein-DNA interfaces that are central to their conclusions. The pLDDT scores for the interface residues are not mentioned.
- **Required correction** Report local confidence metrics for the interface regions, such as pLDDT scores for residues involved in protein-protein and protein-DNA contacts, to support the reliability of the interface predictions.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Discussion of alternative explanations
- **Affected element** Discussion section
- **Evidence pointer** Not applicable
- **Issue** The discussion does not adequately consider alternative explanations for the observed motif differences across species, such as differences in chromatin context, DNA methylation, or the presence of interacting partners that could influence binding specificity.
- **Required correction** Add a paragraph discussing alternative explanations and limitations of the current study, including the possibility that factors other than intrinsic DNA binding specificity contribute to the observed differences.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Accessibility of data and code
- **Affected element** Materials and Methods section
- **Evidence pointer** Not applicable
- **Issue** The manuscript does not state whether the DAP-seq data, analysis scripts, and structural models will be deposited in public repositories. Given the community resource value of the dataset, this information should be provided.
- **Required correction** Add a data availability statement describing where the raw sequencing data, processed peak calls, analysis scripts, and AlphaFold3 models will be deposited.

## Risk / unsupported claims

- The claim that "wheat SPLs preferentially bind to longer, palindromic motifs" and that "these motif differences may arise from enhanced protein-protein interactions that stabilize dimeric binding" is not experimentally supported. The AlphaFold3 predictions have low overall confidence scores, and no biochemical validation of dimerization is provided.
- The claim that "SPL family members diversify through DNA-binding evolution" is a broad evolutionary conclusion drawn from comparisons of datasets generated under potentially different experimental conditions. The comparability of the cross-species datasets is not established.
- The claim that "AtSPL15 and AtSPL9 have distinct roles in regulating different biological processes" is based on GO enrichment of differentially bound peaks, but the functional significance of these differences is only validated for a single promoter (AtDI21).
- The statement that "DAP-seq can predict transcriptionally regulated genes by the relevant TFs" is supported only by the GSEA analysis for AtSPL7, and the strength of this predictive relationship for other family members is not established.
- The classification of SPL family members into Class A and Class B is presented as a clear dichotomy, but the robustness of this classification and the criteria for assignment are not fully described.
- The claim that "conserved target genes" between species represent functionally important binding events is not directly tested. The conservation of target genes is inferred from peak sharing, but the functional relevance of these shared targets is not experimentally validated.