## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No supplementary tables or figures were available for direct inspection.
- **Shared manuscript claim summary** The authors present a genome-scale yeast one-hybrid (Y1H) screen of 2039 Arabidopsis transcription factors (TFs) against 224 promoters of primary (central carbon) and specialized (aliphatic glucosinolate) metabolism genes. They report 27,485 TF-promoter interactions, propose a "distributed" model of transcriptional regulation distinct from microbial master-regulator paradigms, validate a subset of predicted regulators via inducible overexpression and RNA-seq, and functionally characterize 17 TFs in TCA-cycle-dependent growth and salt stress responses.
- **Visible evidence base** Main text, figure legends (referenced but not shown), methods section, author contributions, acknowledgments. Supplementary tables are listed but their contents were not provided.
- **Missing materials affecting confidence** All figures, all supplementary tables (S1-S12), raw RNA-seq data, Y1H interaction data, statistical outputs, and detailed bioinformatics code. Without these, quantitative claims and statistical analyses cannot be independently verified.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and potentially valuable resource: a large-scale TF-promoter interaction network for Arabidopsis metabolic genes. The scope of the Y1H screen, covering over 80% of the Arabidopsis TF repertoire against promoters of central carbon and glucosinolate metabolism, is impressive and represents a significant technical undertaking. The authors' central hypothesis, that plant metabolic regulation is "distributed" rather than master-regulator-driven, is interesting and, if well-supported, would be of broad interest. However, the manuscript as provided has several critical weaknesses. The evidence for the central claims is largely indirect or correlative, the validation experiments are limited in scope, and the statistical and methodological details necessary to assess data quality are not fully visible. The claim of a fundamentally distinct regulatory architecture in plants versus microbes is a strong one that requires more direct comparative evidence than is presented. The functional validation, while a good start, covers only a small fraction of the network and does not fully establish the physiological relevance of the proposed regulatory model. The manuscript is well-written and the narrative is clear, but the gap between the scale of the resource and the depth of the functional validation leaves the central conclusions only partially supported.
- **Who would be interested in the results, and why** Plant systems biologists, researchers studying transcriptional regulation, and those interested in plant metabolism, particularly primary-specialized metabolism crosstalk. The resource itself (the interaction network) would be of use to the Arabidopsis community for hypothesis generation. Researchers studying TCA cycle regulation or stress responses would also find the functional data relevant. The conceptual claim about distributed versus master-regulator control would interest a broader audience of comparative regulatory biologists.
- **Major strengths**
  1. The scale and comprehensiveness of the Y1H screen is a major strength, providing a unique and extensive resource.
  2. The integration of a specialized metabolic pathway (glucosinolates) with primary metabolism in the same screen is a valuable design.
  3. The combination of binding data with inducible overexpression and phenotypic assays provides a multi-layered approach to validation.
  4. The focus on context-dependency (development, stress) of regulatory interactions is a sophisticated and appropriate framework for plant biology.
- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: Yes)
  - **R1-M4** (Blocking: No)
  - **R1-M5** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**
  - **Originality:** The work is original in its scale and integration. While individual components (Y1H, TF validation) are established, the combination at this scale for plant metabolism is novel. The conceptual claim of a "distributed" model, while not entirely new, is given a substantial new dataset.
  - **Scientific importance:** The resource is important for the plant community. The conceptual framework, if rigorously supported, would be important. However, the current evidence does not fully establish the importance of the conceptual claim over alternative explanations.
  - **Interdisciplinary readership:** The topic is primarily of interest to plant biologists and systems biologists. The broader claim about regulatory architecture could attract a wider readership, but the evidence is not yet compelling enough to make this a cross-disciplinary paper.
  - **Technical soundness:** The core Y1H methodology is sound, but the lack of visible quality control metrics and the limited scope of validation experiments are concerns. The statistical analysis of the phenotypic data is not fully described.
  - **Readability for nonspecialists:** The manuscript is clearly written and the narrative is accessible. The concepts are explained well. However, the density of gene names and pathway details may be challenging for a complete nonspecialist.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a valuable resource, but the central conceptual claims are not yet sufficiently supported by the data as presented. Major revisions and additional analyses are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** The authors claim that the network "suggests that plant metabolic design principles are distinct from that of microbes" and that regulation is "distributed" rather than master-regulator-driven.
- **Evidence pointer** Results section, Figures 1-2 (not visible), Discussion
- **Concern** The central conceptual claim of a "distributed" regulatory model distinct from microbes is not directly tested. The evidence presented is that most TFs bind to multiple pathways (Figure 1C) and that pairwise pathway overlaps are higher than expected (Figure 2). However, this is a property of the binding data, not a demonstration of functional regulatory architecture. The comparison to microbes is purely qualitative and based on literature, not on a direct comparative analysis. The authors do not provide a quantitative definition of "distributed" versus "master-regulator" that could be tested against their data or microbial datasets. The claim that this is a distinct design principle is therefore an interpretation, not a conclusion derived from the data.
- **Why it matters** This is the primary conceptual advance claimed by the manuscript. If the evidence is only correlative and the comparison is not rigorous, the main message of the paper is overstated. The field needs a clear, testable framework for comparing regulatory architectures across organisms.
- **Resolution test** The authors should either (a) provide a quantitative, testable definition of "distributed" versus "master-regulator" regulation and apply it to their data and to comparable microbial datasets, or (b) temper the claim to be a hypothesis generated by their resource, not a conclusion. A direct comparison of network properties (e.g., degree distribution, modularity, centrality) between their plant network and published microbial regulatory networks would be a strong addition.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation of Y1H data
- **Claim pointer** The manuscript claims a "comprehensive set of protein-DNA interactions" and reports 27,485 interactions between 1930 TFs and 220 promoters.
- **Evidence pointer** Results section, Figure 1, Table S3 (not visible)
- **Concern** The Y1H assay is known to have high false positive and false negative rates. The manuscript does not report any quality control metrics for the Y1H screen, such as the rate of autoactivation, the reproducibility between replicates, or the validation rate of a random subset of interactions by an orthogonal method (e.g., EMSA, ChIP-qPCR, or plant one-hybrid). The authors acknowledge that Y1H suffers from false positives and negatives, but they do not provide any data to estimate the error rate in their specific dataset. The claim of "comprehensive" is therefore not supported by the evidence presented.
- **Why it matters** The entire resource and all downstream analyses are built on this interaction dataset. If the error rate is high, the network properties (e.g., multi-pathway binding) could be artifacts. The field standard for large-scale interaction datasets is to provide some estimate of data quality.
- **Resolution test** The authors should provide a detailed quality control section for the Y1H screen, including: (1) the number of TFs that autoactivate and were excluded, (2) the reproducibility rate between biological replicates, and (3) a validation rate of a random sample of interactions (e.g., 50-100) by an independent method. This is essential for the resource to be credible.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of functional validation
- **Claim pointer** The authors claim that "all seventeen TFs tested have an effect on plant growth in the dark and TCA-cycle dependent nutrition" and that specific TFs affect salt stress responses.
- **Evidence pointer** Results section, Figures 5-6, Tables S10-S12 (not visible)
- **Concern** The phenotypic analyses are described as using a two-way ANOVA, but the details of the model are not fully specified. The text mentions "generalized nested linear mixed model" but the random effects structure is only partially described. The authors do not report effect sizes, confidence intervals, or the results of post-hoc tests in the main text. The claim that "all seventeen TFs tested have an effect" is a strong statement that requires a clear presentation of the statistical evidence. The normalization procedure for the bulked lines is described but the potential bias introduced by this normalization is not discussed. The correlation between the number of significant phenotypes and C/N content phenotypes (r = 0.53, P = 0.03) is presented as supportive, but this is a correlation across a small number of genotypes and may be driven by a few outliers.
- **Why it matters** The functional validation is the key evidence that the network has biological relevance. If the statistical analysis is not rigorous or is not fully reported, the conclusions drawn from it are not reliable. The claim that all 17 TFs affect growth is particularly strong and needs robust support.
- **Resolution test** The authors should provide a complete description of the statistical models used, including all fixed and random effects. They should report effect sizes and confidence intervals for the key comparisons. The post-hoc test results should be presented in a clear and accessible format (e.g., a supplementary table with all pairwise comparisons). The authors should also discuss the potential limitations of their normalization procedure.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of correlation analysis
- **Claim pointer** The authors use correlation analysis across five microarray datasets to support the claim of context-dependent regulation.
- **Evidence pointer** Results section, Figure S3, Table S8 (not visible)
- **Concern** The correlation analysis is used to infer context-dependency, but the logic is not fully explained. The authors state that few interactions are common across datasets, but this could be due to technical variation between datasets (e.g., different platforms, normalization methods) rather than true biological context-dependency. The threshold for "highly correlated" (|r| > 0.8) is stated, but the sensitivity of the results to this threshold is not explored. The authors do not compare their observed overlap to a null expectation (e.g., random gene sets).
- **Why it matters** The claim of context-dependency is a key part of the proposed model. If the analysis is confounded by technical artifacts, the conclusion is weakened.
- **Resolution test** The authors should provide a more rigorous analysis of the correlation data. This could include: (1) a permutation-based null model to test whether the observed overlap between datasets is less than expected by chance, (2) a sensitivity analysis with different correlation thresholds, and (3) a discussion of the potential technical sources of variation between the datasets.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the model
- **Claim pointer** The authors propose that their findings on the TCA cycle and glucosinolate pathways can be generalized to a "distributed" model of plant metabolic regulation.
- **Evidence pointer** Discussion
- **Concern** The screen covers central carbon metabolism and one specialized pathway (glucosinolates). The authors generalize their findings to all of plant metabolism. This is a significant extrapolation. Other specialized metabolic pathways (e.g., phenylpropanoids, terpenoids, alkaloids) may have different regulatory architectures. The authors do not discuss this limitation.
- **Why it matters** The generality of the proposed model is a key part of its significance. If the model only applies to the pathways studied, its importance is reduced.
- **Resolution test** The authors should either (1) provide evidence that their findings extend to other pathways (e.g., by analyzing publicly available ChIP-seq or DAP-seq data for other metabolic pathways), or (2) clearly state that the model is proposed for the pathways studied and that testing in other pathways is a future direction.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Results section, first paragraph
- **Evidence pointer** Location not provided
- **Issue** The sentence "This dataset showed that 90% of TFs bind to promoters of metabolic genes with all TFs binding to promoters of multiple metabolic pathways" is slightly ambiguous. It is unclear if "all TFs" refers to all 1930 TFs that had at least one interaction, or all 2039 TFs in the library.
- **Required correction** Rephrase to clarify: "Of the 1930 TFs that bound to at least one promoter, 90% bound to promoters of metabolic genes, and all of these bound to promoters from multiple metabolic pathways."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, TCA cycle sub-network
- **Evidence pointer** Location not provided
- **Issue** The text states "71.4% of the Y1H-predicted WRI3 TCA cycle targets were recovered in the RNA-Seq analysis (Figure 3E, P=0.0006, Fisher's exact test)." The number of targets is not stated, making it difficult to assess the strength of this enrichment.
- **Required correction** State the number of predicted targets and the number recovered. For example, "Of the 7 Y1H-predicted WRI3 TCA cycle targets, 5 were recovered in the RNA-Seq analysis (P=0.0006, Fisher's exact test)."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods, Data and Code Availability
- **Evidence pointer** Location not provided
- **Issue** No data or code availability statement is present in the manuscript.
- **Required correction** Add a Data and Code Availability statement specifying where the Y1H interaction data, RNA-seq data, and analysis code will be deposited (e.g., Gene Expression Omnibus, The Arabidopsis Information Resource, GitHub).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods, Y1H screen
- **Evidence pointer** Location not provided
- **Issue** The methods describe the Y1H screen but do not specify the number of biological replicates for the Y1H assay or the criteria for calling a positive interaction.
- **Required correction** Add details on the number of replicates and the scoring criteria for a positive interaction (e.g., growth on selective media for X days, minimum colony size).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation of TF family enrichment
- **Affected element** Results, TF family enrichment
- **Evidence pointer** Location not provided
- **Issue** The text states that TF family enrichment was "constrained to specific enzyme isoforms targeted to defined cellular compartments." This is an interesting finding, but the biological significance is not discussed. Why would certain TF families preferentially target isoforms in specific compartments?
- **Required correction** Add a brief discussion of the potential biological implications of this compartment-specific enrichment.

## Risk / unsupported claims
- The claim that plant metabolic regulation is "distributed" and "distinct from that of microbes" is not directly supported by the data presented. It is a plausible interpretation but is not tested against a quantitative null model or a direct comparison with microbial networks.
- The claim that the Y1H network is "comprehensive" is unsupported without quality control metrics (e.g., false positive/negative rates, validation by an orthogonal method).
- The claim that "all seventeen TFs tested have an effect on plant growth in the dark and TCA-cycle dependent nutrition" is not fully supported by the statistical details provided in the text. The effect sizes and the results of all post-hoc comparisons are not reported.
- The generalizability of the proposed "distributed" model to all of plant metabolism is an extrapolation from the pathways studied (central carbon and glucosinolates) and is not supported by data from other pathways.
- The correlation analysis across microarray datasets is used to support context-dependency, but the analysis does not include a null model to rule out technical variation as an explanation for the low overlap between datasets.