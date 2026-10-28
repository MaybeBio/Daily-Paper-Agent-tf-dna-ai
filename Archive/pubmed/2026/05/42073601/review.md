## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and support of claims by presented evidence. No assessment of journal fit or editorial decisions.
- **Shared manuscript claim summary** The authors present an integrated computational characterization of AP-2δ/TFAP2D in lung adenocarcinoma (LUAD) and lung squamous cell carcinoma (LUSC), combining expression profiling, survival analysis, clinical and molecular subclassification, differential expression, methylation-derived chromatin compartment analysis, cofactor rewiring, and structure-based pocket identification. They report subtype-specific regulatory architectures, with LUSC showing a broader chromatin-compartment footprint and LUAD showing more selective cofactor rewiring, and identify candidate ligandable pockets within the TF_AP-2 domain.
- **Visible evidence base** Full text including methods, results, discussion, and conclusions. Figures and tables are referenced but not provided. Supplementary files are referenced but not provided.
- **Missing materials affecting confidence** Figures 1-7, Tables 1, and Supplementary Files S1-S5 are referenced but not available for review. This substantially limits verification of quantitative results, statistical outputs, and visual data patterns.

## Reviewer
- **Overall assessment** This manuscript presents a broad, integrative computational analysis of a poorly characterized transcription factor in two major lung cancer subtypes. The scope is ambitious and the analytical framework is logically structured. However, the review is constrained by the absence of all figures, tables, and supplementary materials, which prevents verification of the central quantitative claims. The statistical approach for survival analysis, the handling of multiple testing in chromatin compartment analysis, and the interpretation of cofactor rewiring require clarification. The structural analysis is appropriately cautious but its connection to the regulatory findings is tenuous. The manuscript would benefit from clearer articulation of what is novel versus confirmatory, and from tempering language that implies functional significance where only correlational evidence exists.

- **Who would be interested in the results, and why** Researchers studying AP-2 transcription factors, particularly those interested in lineage-specific transcriptional regulation in lung cancer. The subtype-specific regulatory architecture described may interest investigators working on LUAD-LUSC differences. The structural analysis may appeal to those pursuing transcription factors as drug targets, though this is speculative. Computational biologists developing integrative frameworks for multi-omic cancer analysis may find the methodological combination of interest.

- **Major strengths** The study addresses a genuinely undercharacterized member of the AP-2 family in a clinically relevant context. The analytical design is multi-layered and attempts to integrate transcriptomic, epigenetic, and structural perspectives. The authors appropriately acknowledge the exploratory nature of their findings and avoid overclaiming causal relationships. The distinction between LUAD and LUSC regulatory architectures is a potentially valuable contribution. The structural analysis is appropriately framed as hypothesis-generating.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim summary** The manuscript reports specific quantitative results including hazard ratios, p-values, enrichment scores, and structural pocket metrics across Figures 1-7 and Tables 1.
- **Evidence pointer** Figures 1-7, Table 1, Supplementary Files S1-S5 (location not provided)
- **Concern** None of the figures, tables, or supplementary files were provided for review. This includes all survival curves, differential expression visualizations, chromatin compartment plots, cofactor rewiring data, and structural pocket representations. Without these, the quantitative claims cannot be verified.
- **Why it matters** The central conclusions rest on these data. For example, the claim that TFAP2D-low groups show shorter progression-free interval in both LUAD and LUSC (HR = 1.67 and 1.79) cannot be assessed without the Kaplan-Meier curves and confidence intervals. Similarly, the chromatin compartment differences and cofactor rewiring results are entirely dependent on figures not available.
- **Resolution test** Provide all figures, tables, and supplementary files for review. Verify that all reported statistics match the displayed data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim summary** The manuscript states that optimal TFAP2D expression thresholds were identified using the "Cutp" method for survival stratification, and that hazard ratios were estimated with Cox regression.
- **Evidence pointer** Section 2.3, Section 3.2 (location not provided)
- **Concern** The "Cutp" method for optimal cutoff selection is known to inflate type I error rates due to multiple testing across potential cutpoints. The manuscript does not describe any correction for this. Additionally, the proportional hazards assumption is stated to have been assessed, but no results of this assessment are reported. The choice of PFI as the only endpoint showing significance, while OS, DSS, and DFI do not, raises questions about whether this reflects a true biological signal or a multiple comparisons artifact.
- **Why it matters** Survival analysis with data-derived cutpoints can produce spurious associations. If the PFI finding is a statistical artifact, a key pillar of the manuscript's clinical relevance claim collapses.
- **Resolution test** Describe the multiple testing correction applied for cutoff selection. Report the results of proportional hazards assumption testing. Provide justification for why PFI specifically was the only significant endpoint, and discuss whether this pattern is consistent with a priori hypotheses.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim summary** The manuscript claims that methylation-derived A/B compartments can be used to identify Hi-C-like chromatin structure, and that significant differences in compartment organization exist between TFAP2D-high and TFAP2D-low groups.
- **Evidence pointer** Section 2.7, Section 3.5 (location not provided)
- **Concern** The use of 450k methylation data to infer A/B compartments is a proxy method with known limitations. The manuscript does not validate this approach against actual Hi-C data in these samples. The threshold of requiring at least three consecutive significant 100-kb bins for block merging is arbitrary and not justified. The biological interpretation of a "broader chromatin-compartment footprint" in LUSC is unclear without understanding the magnitude and direction of compartment switches.
- **Why it matters** The chromatin compartment analysis is a central pillar of the claim that LUSC shows a distinct regulatory architecture. If the proxy method is unreliable or the interpretation overreaches, this conclusion is weakened.
- **Resolution test** Validate the methylation-based compartment inference against available Hi-C data in lung cancer cell lines or tissues. Justify the bin merging threshold. Clarify what "broader footprint" means in terms of genomic coverage and effect size, and discuss the biological plausibility of the observed direction of compartment changes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive rigor
- **Claim summary** The manuscript states that LUAD shows "more selective cofactor rewiring" involving TRIM24, TRRAP, YAP1, ZMYND8, and USP7, and interprets this as evidence of a distinct regulatory architecture.
- **Evidence pointer** Section 3.6, Figure 6B (location not provided)
- **Concern** The cofactor rewiring analysis is based on differential correlation of TFAP2D with a panel of transcriptional cofactors between high and low expression groups. The biological interpretation of these correlations as "rewiring" is speculative. Correlation differences do not establish regulatory relationships. The manuscript acknowledges this is exploratory, but the language in the abstract and conclusions ("distinct regulatory architecture") implies stronger evidence than warranted.
- **Why it matters** The central claim of the manuscript is that AP-2δ operates within distinct regulatory architectures in LUAD versus LUSC. If the cofactor analysis is merely correlational and not validated, this claim is overstated.
- **Resolution test** Temper the language to reflect correlational evidence. Consider whether any orthogonal validation (e.g., ChIP-seq, perturbation experiments) exists in public data that could support the rewiring interpretation. If not, clearly state this as a hypothesis.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Structural analysis relevance
- **Claim summary** The manuscript identifies five unified pockets (UP1-UP5) in the AP-2δ AlphaFold model, with UP1-UP3 prioritized as candidate ligandable sites, and states these are located within the TF_AP-2 domain.
- **Evidence pointer** Section 2.9, Section 3.7, Figure 7 (location not provided)
- **Concern** The structural analysis is disconnected from the regulatory findings. The manuscript does not explain how the identified pockets relate to the observed transcriptional or chromatin differences. The statement that UP1 and UP2 are "complementary top candidates" based on different scoring metrics is not a meaningful prioritization. The lack of experimental validation is acknowledged, but the relevance of this section to the overall narrative is unclear.
- **Why it matters** The structural analysis is presented as a major component of the "integrated characterization," but its connection to the biological findings is not established. This weakens the coherence of the manuscript.
- **Resolution test** Clarify the rationale for including the structural analysis. Explain how the pockets might be functionally relevant to AP-2δ activity in lung cancer. If the connection is purely speculative, state this explicitly and consider whether this section adds sufficient value to justify its inclusion.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2 (location not provided)
- **Issue** The description of Monocle3 usage for expression dynamics evaluation is unclear. Monocle3 is typically used for trajectory analysis in single-cell data, but the manuscript appears to apply it to bulk RNA-seq data. The rationale for this choice is not explained.
- **Required correction** Clarify the analytical purpose of using Monocle3 in this context. If it is used for dimensionality reduction and clustering of bulk samples, explain why this is appropriate and what biological insight it provides beyond standard approaches.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1 (location not provided)
- **Issue** The manuscript reports that TFAP2D is more highly expressed in LUAD than LUSC (p < 0.001) but does not report the effect size or the statistical test used.
- **Required correction** Report the test statistic, effect size, and sample sizes for this comparison.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Section 3.5
- **Evidence pointer** Section 3.5 (location not provided)
- **Issue** The manuscript states that LUSC exhibited a "markedly broader genomic footprint" than LUAD in chromatin compartment differences, but also notes that the median per-locus effect size was similar between cohorts. The term "broader footprint" is ambiguous.
- **Required correction** Define "broader footprint" precisely, whether it refers to number of significant bins, genomic span, or number of blocks, and report the relevant numbers.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 3.2
- **Evidence pointer** Section 3.2 (location not provided)
- **Issue** The manuscript discusses the prognostic association of TFAP2D with PFI but does not compare this finding with previous studies on TFAP2D in lung cancer beyond noting that prior work was limited to OS.
- **Required correction** Provide a more detailed comparison with any existing literature on TFAP2D expression and survival outcomes in other cancer types, to contextualize the PFI finding.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Section 2.9
- **Evidence pointer** Section 2.9 (location not provided)
- **Issue** The description of the structural analysis does not specify the version of the AlphaFold model used, the software versions for the pocket detection tools, or the criteria for "cross-tool consensus."
- **Required correction** Provide software versions, model version, and explicit criteria for what constitutes consensus support for a pocket.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Abstract and Conclusions
- **Evidence pointer** Abstract, Section 4 (location not provided)
- **Issue** The phrase "distinct regulatory architecture" is used in the abstract and conclusions, but the manuscript itself acknowledges the findings are exploratory and correlational. This language overstates the strength of the evidence.
- **Required correction** Use more cautious language, such as "suggestive of distinct regulatory architecture" or "associated with distinct regulatory patterns," in the abstract and conclusions.

## Risk / unsupported claims
- The claim that TFAP2D-low groups show shorter progression-free interval in both LUAD and LUSC is unverifiable without the survival curves and full statistical outputs.
- The claim that LUSC shows a "broader chromatin-compartment footprint" is unverifiable without the compartment analysis figures and quantitative summaries.
- The claim that LUAD shows "more selective cofactor rewiring" involving specific cofactors is unverifiable without the correlation data and statistical testing details.
- The claim that UP1-UP3 are prioritized candidate pockets is unverifiable without the structural figures and scoring tables.
- The statement that TFAP2D expression "delineates biologically distinct states" is an interpretation that goes beyond the correlational evidence presented.
- The claim that the study provides "the first TFAP2D-focused analysis of lung cancer" is a strong novelty claim that requires a more thorough literature search to substantiate.
- The functional significance of the identified pockets for AP-2δ activity is entirely speculative and not supported by any experimental or computational evidence beyond pocket detection.