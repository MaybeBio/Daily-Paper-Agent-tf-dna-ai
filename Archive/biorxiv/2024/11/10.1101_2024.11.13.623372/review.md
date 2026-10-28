## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplementary table legends)
- **Assessment boundary** Scientific claims, methodology, and evidence as presented in the provided text; no external data or unpublished materials consulted
- **Shared manuscript claim summary** The authors propose that cis-regulatory codes controlling retinal cell class-specific gene expression are deeply conserved across vertebrates, including between jawed and jawless species, despite extensive turnover of cis-regulatory elements. They support this with comparative single-cell chromatin accessibility data from six species and machine learning models of regulatory grammar.
- **Visible evidence base** Abstract, introduction, results (narrative), discussion, methods, supplementary table legends; no figures or supplementary data files were provided for direct inspection
- **Missing materials affecting confidence** Figures 1-5, Supplementary Figures 1-8, all Supplementary Tables (data values), raw sequencing data, code, and detailed computational parameters; these are referenced but not available for verification

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in evolutionary cell biology: whether cis-regulatory codes controlling cell type identity are conserved over deep evolutionary time. The authors present a compelling conceptual framework and a substantial comparative dataset spanning six vertebrate species, including a jawless vertebrate. The central claim, that regulatory grammar is conserved despite element turnover, is plausible and important. However, the evidence as presented in the text alone is insufficient to fully establish this claim. Key quantitative results, statistical validations, and control analyses are referenced but not shown. The machine learning approach is promising but its interpretation requires careful scrutiny of the methods and validation metrics, which are not fully detailed. The manuscript is well-written and the conceptual framing is strong, but the current evidence base does not allow a definitive assessment of the central conclusions.
- **Who would be interested in the results, and why** Evolutionary biologists studying cell type evolution and homology, developmental biologists interested in cis-regulatory logic, computational biologists working on regulatory genomics, and vision researchers studying retinal development and evolution. The findings have implications for understanding how conserved regulatory programs can persist despite genomic turnover, which is relevant to both basic evolutionary theory and practical applications in comparative genomics.
- **Major strengths** 1) The question is of high conceptual importance and timely. 2) The inclusion of lamprey, a jawless vertebrate, provides a critical evolutionary outgroup spanning over 500 million years. 3) The multi-species comparative design using single-cell chromatin accessibility is methodologically ambitious and appropriate. 4) The use of de novo motif discovery avoids biases from known motif databases. 5) The machine learning approach to compare regulatory grammar across species is innovative. 6) The authors address the important confound of paralogous TF usage (e.g., NRL vs. MAFA in rods).
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The manuscript relies heavily on referenced figures and supplementary materials that were not provided. Without these, the quantitative basis for the central claims cannot be evaluated. Specific technical concerns include the lack of detail on motif clustering thresholds, the interpretation of machine learning model performance, and the statistical treatment of cross-species comparisons.
- **Assessment against Nature-style criteria** Originality: High. The concept of conserved cis-regulatory codes across half a billion years is novel and significant. Scientific importance: High. The findings could reshape understanding of cell type evolution and regulatory logic. Interdisciplinary readership: Broad appeal across evolution, development, genomics, and neuroscience. Technical soundness: Cannot be fully assessed from the text alone; methods are described but key validations and controls are not shown. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some computational details may be challenging for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved and the full evidence base is made available for review. The conceptual framework and preliminary results are promising, but the current submission does not provide sufficient evidence to fully establish the central claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that "conservation manifests as the clustering of multiple distinct high-affinity transcription factor (TF) binding sites toward the center of cell-class-specific open chromatin regions with little cross-species preservation of higher-order syntax."
- **Evidence pointer** Results section "Deep conservation of retinal cis-regulatory codes"; Figures 3 and 4; Supplementary Figures 3-5
- **Concern** The central claim of conserved motif positioning and lack of higher-order syntax conservation is presented without the actual data. The text describes the findings but does not provide the quantitative distributions, statistical comparisons, or representative examples that would allow a reader to evaluate the strength of this claim. The referenced figures and supplementary materials are not available for inspection.
- **Why it matters** This is the core finding of the manuscript. Without the underlying data, the claim cannot be verified or critically assessed. The distinction between conserved vocabulary and non-conserved syntax is a nuanced argument that requires careful examination of the evidence.
- **Resolution test** Provide the full figures and supplementary data showing motif distribution plots, statistical tests for positional enrichment, and comparative analyses of syntax across species. Include clear legends and statistical details.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The authors state that "hierarchical clustering of machine-learning models of retinal cis-regulatory codes from diverse species recovers six clusters corresponding to the six retinal cell classes."
- **Evidence pointer** Results section "Machine learning models of cis-regulatory grammar cluster by cell class"; Figure 5; Supplementary Figures 6-8
- **Concern** The machine learning approach is central to the claim of conserved regulatory grammar, but the methods and validation are insufficiently described. The text does not detail how the gkm-SVM models were compared, what distance metric was used for clustering beyond Pearson correlation, how the significance of clustering was assessed, or how potential confounders (e.g., species-specific biases, differences in data quality) were addressed. The silhouette score is mentioned but the actual values and their interpretation are not provided.
- **Why it matters** The clustering of models by cell class rather than species is a key piece of evidence for conserved regulatory codes. If the clustering is driven by technical artifacts or species-specific features rather than genuine regulatory grammar, the conclusion would be undermined.
- **Resolution test** Provide detailed methods for model training, comparison, and clustering. Show the full clustering dendrogram with bootstrap support values, silhouette scores for each cluster, and appropriate controls (e.g., permutation tests, cross-species validation).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and comparability
- **Claim pointer** The authors claim to have performed "comparative single-cell chromatin accessibility analysis of lamprey, fish, bird, and mammalian retinas" and to have identified cell class-specific open chromatin regions in all six species.
- **Evidence pointer** Results section "Single-cell chromatin accessibility profiling of vertebrate retinas"; Figure 1; Supplementary Figures 1-2; Supplementary Tables 5-6
- **Concern** The text describes the generation and analysis of single-cell chromatin accessibility data from six species, but provides no information on data quality metrics, sequencing depth, number of cells per cluster, reproducibility between replicates, or the robustness of cell type assignments. The number of open chromatin regions used for downstream analyses is referenced to Supplementary Table 6 but not provided. Differences in data quality across species could substantially affect the comparative analyses.
- **Why it matters** The validity of all downstream analyses depends on the quality and comparability of the underlying chromatin accessibility data. If some species have much lower data quality or fewer cells, the identification of cell class-specific open chromatin regions and the subsequent motif analyses could be biased.
- **Resolution test** Provide comprehensive data quality metrics for each species, including number of cells, median fragments per cell, transcription start site enrichment scores, and cluster resolution. Show that cell type assignments are robust and that the number of open chromatin regions is sufficient for the analyses performed.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors state that "we found that in all comparisons the meta-gene openness score was highest for the expected cell class."
- **Evidence pointer** Results section "Single-cell chromatin accessibility profiling of vertebrate retinas"; Figure 1d
- **Concern** The validation of cell type assignments using meta-gene openness scores is described qualitatively. The text does not provide the actual scores, the statistical significance of the differences, or the variability across species. It is unclear whether the meta-gene approach is sufficiently sensitive to distinguish between closely related cell types or whether the results are driven by a few highly expressed genes.
- **Why it matters** The meta-gene analysis is used to validate the cell type annotations, which are the foundation for all subsequent analyses. If the validation is weak or inconsistent across species, the reliability of the cell type assignments is questionable.
- **Resolution test** Provide the meta-gene openness scores for all cell types and species, with statistical tests showing that the expected cell type has significantly higher scores than others. Include an assessment of the robustness of the meta-gene approach.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of motif conservation
- **Claim pointer** The authors propose that "the retina's cellular Bauplan is controlled by cis-regulatory codes which predate the divergence of extant vertebrates and persist despite nearly complete enhancer turnover."
- **Evidence pointer** Discussion section; Figure 3; Supplementary Figure 3
- **Concern** The interpretation that conserved motifs within open chromatin regions indicate conserved regulatory codes assumes that the open chromatin regions are functional enhancers in all species. The authors do not provide direct evidence of enhancer activity (e.g., reporter assays, histone modifications, or chromatin conformation data) for the conserved regions. Additionally, the possibility that the conserved motifs are bound by different TFs in different species (despite similar binding preferences) is not fully addressed.
- **Why it matters** The claim of conserved regulatory codes controlling cell identity is stronger than the claim of conserved motif sequences. Without evidence of functional conservation, the interpretation may be overreaching.
- **Resolution test** Provide additional evidence for the functional relevance of the conserved open chromatin regions, such as histone modification data, transcription factor binding data, or reporter assays in at least a subset of species. Discuss the limitations of the current approach in establishing functional conservation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, last sentence
- **Issue** The phrase "cellular Bauplan" may be unfamiliar to some readers and is not defined in the abstract.
- **Required correction** Define "Bauplan" or use a more accessible term such as "body plan" or "cellular architecture."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods, "Cell-class meta-gene analysis"
- **Evidence pointer** Methods section
- **Issue** The description of the meta-gene analysis is brief and does not specify how the "top 1,000 genes with the highest tau index" were selected or whether this threshold was applied consistently across species.
- **Required correction** Provide additional detail on the selection criteria and any sensitivity analyses performed to test the robustness of the results to this threshold.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability
- **Evidence pointer** Code and data availability section
- **Issue** The statement "The code used for the analysis is available upon request" is not in line with current best practices for reproducibility.
- **Required correction** Deposit the code in a public repository (e.g., GitHub, Zenodo) and provide a persistent DOI or accession number.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results, "Extensive enhancer turnover during vertebrate evolution"
- **Evidence pointer** Results section; Figure 2
- **Issue** The text describes deviations from the Gompertz model at intermediate evolutionary distances but does not provide a quantitative measure of the goodness of fit or the statistical significance of the deviations.
- **Required correction** Provide goodness-of-fit statistics and confidence intervals for the model parameters, and clearly state which deviations are statistically significant.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of TF paralog choice (e.g., NRL vs. MAFA) is interesting but could be expanded to address the broader implications for the concept of "terminal selector" TFs and the definition of cell type homology.
- **Required correction** Consider adding a brief discussion of how the findings relate to the concept of core regulatory complexes (CoRCs) and the ongoing debate about the definition of cell type homology.

## Risk / unsupported claims
- The claim that cis-regulatory codes are conserved across all six retinal cell classes in all six species is not fully supported by the evidence provided, as the quantitative data are not shown.
- The claim that higher-order syntax is not conserved between jawed and jawless species is based on analyses that are not fully described or validated.
- The interpretation that conserved motifs indicate conserved regulatory codes assumes functional conservation, which is not directly demonstrated.
- The claim that the cis-regulatory codes "predate the divergence of extant vertebrates" is an inference from the data and cannot be directly tested with the current experimental design.
- The performance of the machine learning models in cross-species classification is described but the actual ROC-AUC values for all comparisons are not provided in the text.
- The statement that "the retina's cellular Bauplan is controlled by cis-regulatory codes" implies a causal relationship that is not directly tested in this study.