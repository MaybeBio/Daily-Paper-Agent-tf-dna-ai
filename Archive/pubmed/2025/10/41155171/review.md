## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided by the author. No supplementary figures or tables were supplied beyond those referenced in the text.
- **Assessment boundary** The review is confined to the scientific content, methodology, data interpretation, and internal consistency of the provided manuscript. No external validation of database outputs or software results was performed.
- **Shared manuscript claim summary** The authors claim that three phthalates (DBP, BBP, DEHP) promote breast cancer through common molecular mechanisms centered on five transcription factor-associated hub genes (TP53, CTNNB1, PPARA, ESR1, CDKN2A), that molecular docking reveals direct PAE-hub protein interactions with BBP strongest and DEHP weakest, and that computer-aided molecular design identifies alkyl chain length and phenyl group presence as key structural determinants of binding affinity differences.
- **Visible evidence base** Network toxicology target identification (CTD), functional enrichment (Metascape), PPI network (STRING, Cytoscape), differential expression and survival analyses (TCGA/UALCAN, KM Plotter), molecular docking (AutoDock Vina), and pharmacophore-based molecular design with modified PAE variants. Results are presented in Figures 1–8 and Table 1, none of which were provided in the submitted material.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are referenced but not included. This includes Figure 1 (target Venn diagram, enrichment plots), Figure 2 (PPI network), Figure 3 (differential expression), Figure 4 (Kaplan–Meier curves), Figure 5 (docking poses), Figure 6 (heatmap), Figure 7 (statistical comparisons), Figure 8 (validation constructs), Table 1 (binding affinities), and Figure S1–S2. Without these, quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a plausible integrative workflow combining network toxicology, molecular docking, and computer-aided molecular design to address a relevant question about phthalate-mediated breast cancer mechanisms. The topic is of interest to environmental health and toxicology communities. However, the current submission has several critical issues: the evidence base is incomplete (all figures and tables missing), some statistical claims appear internally inconsistent, the molecular docking methodology lacks essential validation steps, and the causal link between in silico binding affinity and biological mechanism is asserted rather than demonstrated. The core conclusions are not established from the provided material.
- **Who would be interested in the results, and why** Environmental toxicologists studying endocrine-disrupting chemicals, breast cancer researchers investigating environmental risk factors, and computational chemists working on structure-activity relationships of plasticizers. The proposed workflow could serve as a template for similar toxicant-disease mechanism studies, and the SAR findings may inform safer plasticizer design.
- **Major strengths** The integration of three computational approaches (network toxicology, docking, molecular design) is methodologically ambitious and potentially transferable. The focus on common mechanisms across multiple phthalates rather than single-compound effects is a useful framing. The use of pharmacophore-based modification to explain binding affinity differences is a creative application of CAMD. The authors acknowledge limitations regarding metabolite effects and limited PAE number.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims specific binding affinities, differential expression patterns, survival associations, and modification effects, all of which are presented in figures and tables.
- **Evidence pointer** Figures 1–8, Table 1, Figures S1–S2; location not provided
- **Concern** None of the figures, tables, or supplementary materials were included in the submitted manuscript. All quantitative results, including binding affinity values, p-values, survival curves, and enrichment plots, are referenced but not visible.
- **Why it matters** The core scientific claims rest entirely on these data. Without access to the actual figures and tables, the reviewer cannot assess whether the statistical analyses are correct, whether the docking poses are physically plausible, whether the survival curves show meaningful separation, or whether the heatmap supports the stated conclusions. This is a fundamental barrier to evaluation.
- **Resolution test** Provide all figures, tables, and supplementary materials in a complete submission. Each figure must have clear axis labels, legends, and statistical annotations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical consistency
- **Claim pointer** Section 2.4 reports p-values for differential expression: PPARA (p = 1.6524 × 10−12), CTNNB1 (p = 1.44033.34 × 10−7), ESR1 (p < 1 × 10−12), TP53 (p = 6.1951 × 10−4), CDKN2A (p = 1.6524 × 10−12).
- **Evidence pointer** Section 2.4, Figure 3; location not provided
- **Concern** The p-value for CTNNB1 is written as "1.44033.34 × 10−7," which is not a valid number. Additionally, PPARA and CDKN2A are assigned identical p-values (1.6524 × 10−12), which is statistically implausible unless the test statistics are identical, and no explanation is given. The ESR1 p-value is reported as "< 1 × 10−12" while others are exact values, suggesting inconsistent reporting standards.
- **Why it matters** Statistical reporting errors undermine confidence in the differential expression analysis. If p-values are incorrect or misreported, the claim that these hub genes are "significantly impacted" in breast cancer is weakened. The identical p-values for two different genes raise concerns about data handling or copy-paste errors.
- **Resolution test** Correct the CTNNB1 p-value, verify the PPARA and CDKN2A p-values independently, and report all p-values with consistent precision. Provide the underlying test statistics or effect sizes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor (docking)
- **Claim pointer** Section 2.5 claims "direct interactions between the three PAEs and hub targets" with binding affinities, and Section 2.6 claims modification effects on binding affinity.
- **Evidence pointer** Section 2.5, Section 2.6, Table 1, Figures 5–8; location not provided
- **Concern** The molecular docking methodology lacks critical validation steps. No mention is made of docking pose validation (e.g., redocking of co-crystallized ligands), no RMSD values are reported, no ensemble docking or induced-fit considerations are described, and no negative controls are included. The authors do not state whether the protein structures were prepared with proper protonation states, whether water molecules were retained or removed, or how the search space was defined. The claim that "direct interactions" occur is based solely on affinity values without experimental validation or even consistency checks across multiple docking algorithms.
- **Why it matters** Molecular docking is highly sensitive to preparation protocols and scoring functions. Without validation, the reported binding affinities may be artifacts of the docking setup rather than genuine interactions. The subsequent CAMD conclusions about structure-activity relationships depend entirely on the reliability of these docking results. If the docking is not robust, the entire SAR argument collapses.
- **Resolution test** Describe the docking protocol in full detail, including protein and ligand preparation, grid box dimensions, exhaustiveness settings, and scoring function. Include a validation step such as redocking of a known ligand with RMSD < 2 Å. Consider using at least two docking programs or scoring functions to confirm results. Provide negative controls (e.g., a non-binding compound).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The abstract and conclusions state the study "elucidate[s] the potential mechanisms in common by which PAEs promote breast cancer progression" and that findings "provide a foundation for unified intervention strategies."
- **Evidence pointer** Abstract, Section 3, Section 5; location not provided
- **Concern** The study is entirely computational. No experimental validation (e.g., cell-based assays, gene expression knockdown/overexpression, animal models) is presented to support the claim that the identified hub genes mediate PAE effects on breast cancer. The differential expression and survival analyses are correlational. The docking results show binding potential, not biological activity. The leap from in silico predictions to mechanistic claims about breast cancer promotion is not justified.
- **Why it matters** The stated aim is to "elucidate mechanisms," which implies causal understanding. Computational predictions can generate hypotheses but cannot establish mechanisms. Overstating the conclusions may mislead readers and overstate the translational relevance for intervention design.
- **Resolution test** Either temper the language throughout to describe the study as hypothesis-generating, or add experimental validation (e.g., exposure of breast cancer cell lines to PAEs with measurement of hub gene expression, proliferation assays, or reporter assays for transcription factor activity).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Target selection rationale
- **Claim pointer** Section 2.2 states that 19 genes were selected for PPI analysis based on enrichment in transcription factor-related components, and Section 2.3 identifies five hub genes by betweenness centrality.
- **Evidence pointer** Section 2.2, Section 2.3, Figure 2; location not provided
- **Concern** The rationale for selecting 19 genes from the initial 47 common targets is not fully explained. The text states these were "enriched in transcription factor-related components," but the specific criteria (e.g., which GO terms, what enrichment threshold) are not given. The choice of betweenness centrality as the sole metric for hub gene identification is not justified, and no comparison with other centrality measures (degree, closeness, eigenvector) is provided.
- **Why it matters** The selection of hub genes is a critical step that determines all downstream analyses. If the selection criteria are arbitrary or not reproducible, the entire network analysis is called into question. Different centrality measures can yield different hub genes, and the authors do not demonstrate that their choice is robust.
- **Resolution test** Clearly state the inclusion criteria for the 19 genes, including specific GO terms and p-value thresholds. Justify the use of betweenness centrality or provide a sensitivity analysis showing that hub gene identification is consistent across multiple centrality measures.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Statistical analysis of docking modifications
- **Claim pointer** Section 2.6 reports that modification effects were statistically analyzed, with p-values for alkyl chain elongation (p = 0.003, p = 0.004) and phenyl removal (p = 0.022).
- **Evidence pointer** Section 2.6, Figures 7–8; location not provided
- **Concern** The statistical analysis of docking modification effects is not described. The authors state p-values but do not specify which statistical test was used, how many replicates were performed, whether the data met normality assumptions, or how multiple comparisons were handled. The three independent runs mentioned in Section 4.7 are insufficient for robust statistical inference without knowing the variance structure.
- **Why it matters** The p-values are used to support the conclusion that specific structural features (alkyl chain length, phenyl group) are critical for binding affinity. If the statistical analysis is flawed or underpowered, these conclusions are not supported.
- **Resolution test** Describe the statistical test used, report effect sizes and confidence intervals, and justify the sample size. If only three runs were performed, consider whether non-parametric tests or bootstrapping would be more appropriate.

- **Concern ID** R1-M7
- **Severity** Major
- **Blocking** No
- **Axis** Literature integration
- **Claim pointer** Section 3 discusses the role of transcription factors in PAE-induced breast cancer and cites prior studies on ESR1, PPARA, and CTNNB1.
- **Evidence pointer** Section 3; location not provided
- **Concern** The discussion of prior literature is selective and does not engage with contradictory evidence. For example, the claim that CTNNB1 is "often reported to serve as a critical component of the Wnt/β-catenin signaling pathway" in PAE-induced diseases is presented without acknowledging studies that report no such association. The discussion of ESR1 and tamoxifen response is relevant but does not address the complexity of ESR1 signaling in breast cancer subtypes.
- **Why it matters** A balanced discussion of the literature strengthens the credibility of the study. Selective citation may bias the interpretation of the results and overstate the novelty of the findings.
- **Resolution test** Expand the discussion to include studies that report conflicting or null findings. Address the heterogeneity of breast cancer subtypes and how this may affect the generalizability of the hub gene findings.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** Figure 1A; location not provided
- **Issue** The description of the target gene identification is unclear. The text states "a total of 2269 target genes were identified" but then lists DBP (156), BBP (86), and DEHP (2027), which sum to 2269. However, the text also states "47 shared common target genes among all three PAEs," and the intersection with breast cancer genes yields 47. It is unclear whether the 47 common targets are the same as the 47 potential gene targets.
- **Required correction** Clarify the relationship between the 47 common targets and the 47 potential gene targets. If they are the same, state this explicitly. If not, explain the difference.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 2.4
- **Evidence pointer** Figure 3; location not provided
- **Issue** The text states PPARA and CTNNB1 were "downregulated" while ESR1, TP53, and CDKN2A were "upregulated." However, the direction of regulation is not defined in terms of log2 fold change or other thresholds. The p-values alone do not indicate the magnitude of the effect.
- **Required correction** Report the log2 fold change values or state the threshold used to define upregulation and downregulation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Section 4.4
- **Evidence pointer** Section 4.4; location not provided
- **Issue** The homology modeling of CDKN2A is described, but the template selection criteria and the quality of the resulting model (e.g., QMEAN, GMQE scores) are not reported.
- **Required correction** Report the template used, the sequence identity, and the model quality scores to allow assessment of the structural reliability.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.6
- **Evidence pointer** Section 4.6; location not provided
- **Issue** The docking protocol states that AutoDock Vina was used, but the version is not specified in the methods (only in the results section as "AutoDock Vina 1.2.5"). The grid box parameters are described as "defined" but the actual coordinates and dimensions are not given.
- **Required correction** Specify the AutoDock Vina version in the methods and provide the grid box center coordinates and dimensions for each docking run.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Section 4.1
- **Evidence pointer** Section 4.1; location not provided
- **Issue** The CTD database access date is given as 15 February 2025, but the manuscript is dated 29 October 2025. This is internally consistent, but the authors should confirm that the database version used is the most recent and that no major updates occurred between access and submission.
- **Required correction** Confirm the database version and access date, and note any updates that may have occurred.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Section 3
- **Evidence pointer** Section 3; location not provided
- **Issue** The phrase "breast carcer" appears in the discussion, which is a typographical error for "breast cancer."
- **Required correction** Correct the typographical error.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 5
- **Evidence pointer** Figure 5; location not provided
- **Issue** The text describes "the most probable binding conformations" but does not specify how these were selected from the docking output (e.g., lowest energy cluster, most populated cluster).
- **Required correction** Describe the criteria for selecting the displayed binding conformations.

## Risk / unsupported claims
- The claim that the study "elucidate[s] the potential mechanisms in common by which PAEs promote breast cancer progression" is unsupported because no experimental validation is provided; the study is purely computational and correlational.
- The claim that "BBP had the strongest PAE-hub gene interaction and DEHP had the weakest one" is unverifiable without Table 1 and Figure 5, which were not provided.
- The claim that "the binding affinity disparity between BBP and DEHP arises from BBP's shorter side chain and presence of a phenyl group" is based on a limited set of modifications (14 functional groups) and lacks statistical robustness, as the analysis method is not described.
- The claim that "the findings provide a foundation for unified intervention strategies" is overstated given the lack of experimental validation and the limited number of phthalates studied.
- The differential expression and survival analysis results are reported with p-values but without effect sizes, confidence intervals, or multiple testing corrections, making the clinical significance unclear.
- The statement that "the three PAEs exhibited relatively weak binding affinity to CTNNB1" is presented as a quantitative finding, but no threshold for "weak" binding is defined.
- The claim that "extending BBP's carbon chain to match DEHP's length significantly decreased binding affinity compared to native BBP (p = 0.026), though it remained stronger than DEHP (p = 0.04)" is confusing: if the modified BBP is stronger than DEHP, the difference from DEHP should be in the same direction as the difference from BBP, but the p-values suggest otherwise. This requires clarification.
- The manuscript does not address potential confounding factors in the network toxicology analysis, such as the quality of the underlying databases or the potential for false-positive target identification.