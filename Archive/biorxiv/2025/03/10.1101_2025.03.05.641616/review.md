## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, declarations)
- **Assessment boundary** Technical soundness and validity of the claims as presented in the provided text; no external validation or replication attempted
- **Shared manuscript claim summary** The authors introduce pMPBA, an in-vivo method for parallel analysis of peptide-DNA binding, and apply it to map DNA-binding determinants across budding yeast transcription factors, revealing that both DBDs and nonDBD disordered regions contribute to DNA association, with charge and disorder as key determinants.
- **Visible evidence base** Results sections describing validation experiments, domain library analysis, tiling library analysis, and mutation screen; methods sections for experimental procedures and analysis; references to supplementary figures and tables
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S7) not provided; raw sequencing data not accessible; detailed statistical analysis code not reviewed; specific numerical results (effect sizes, p-values, confidence intervals) largely absent from the main text

## Reviewer

- **Overall assessment** The manuscript presents a novel and potentially valuable method for high-throughput analysis of peptide-DNA binding in vivo. The conceptual advance of reversing the MPBA approach to scan peptide libraries against a fixed DNA sequence is interesting and well-motivated. However, the current text provides insufficient quantitative detail to fully evaluate the robustness of the method and the strength of the biological conclusions. Several claims, particularly regarding the functional relevance of nonDBD disordered regions, require stronger statistical support and clearer controls. The manuscript would benefit from more explicit presentation of effect sizes, variability, and the criteria used to define "binding" versus "non-binding" peptides.

- **Who would be interested in the results, and why** Researchers studying transcription factor DNA-binding specificity, particularly those interested in the role of intrinsically disordered regions in TF function. The method itself will be of interest to the broader gene regulation and functional genomics community, as it offers a new approach for dissecting peptide-DNA interactions at scale. The map of DNA-binding determinants across yeast TFs will serve as a resource for computational biologists developing predictive models of TF binding.

- **Major strengths**
  1. The conceptual inversion of MPBA to study peptide-DNA binding is creative and addresses a genuine gap in the field.
  2. The application to a comprehensive set of yeast TFs provides a systematic resource.
  3. The inclusion of a mutation screen on a specific nonDBD region (Msn2) adds mechanistic depth.
  4. The authors acknowledge key limitations, including the inability to distinguish direct from indirect DNA binding.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of the binding assay
- **Claim pointer** "The temporal changes in the abundance of each peptide sequence, relative to cells in which MNase was not activated, providing an estimate of the relative DNA occupancy compared to all tested peptides."
- **Evidence pointer** Results section "Protein Massively Parallel Binding Assay for defining DNA interacting protein domains"; Figure 1
- **Concern** The manuscript does not provide a clear quantitative definition of what constitutes a "binding" peptide. The validation with Msn2 DBD mutants shows expected trends, but no threshold, statistical test, or effect size is reported. It is unclear how the binding score is calculated beyond "distance from the regression line" and what the dynamic range and reproducibility of this score are across biological replicates. The correlation between replicates (r=0.86) is reported, but this is a global measure and does not address the reliability of individual peptide measurements.
- **Why it matters** Without a clear, quantitative definition of binding and its statistical confidence, the subsequent biological conclusions (e.g., which peptides are "bound" and which are not) cannot be properly evaluated. This is the foundation of the entire study.
- **Resolution test** Provide a clear description of the binding score calculation, including the regression model, the threshold used to define binding, and the variability across replicates. Report the distribution of binding scores for known positive and negative controls, and demonstrate that the assay can reliably distinguish them with appropriate statistical power.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for the central claim regarding nonDBD disordered regions
- **Claim pointer** "a considerable fraction of nonDBD peptides, most of which were predicted as intrinsically disordered" showed strong DNA binding; "the proportion of bound peptides in both DBDs and disordered non-DBDs were comparable and were twice as high as these within structured nonDBD regions (41%, 47% and 21%, respectively)"
- **Evidence pointer** Results sections "NonDBD-derived peptides display a range of DNA binding comparable to annotated DBDs" and "TF non-DBD-derived binding determinants are disordered and enriched in positive charge"; Figure 4A
- **Concern** The comparison between disordered and structured nonDBD regions relies on computational predictions of disorder, but the manuscript does not specify which predictor was used for this classification (IUPred is mentioned later for a different analysis). The percentages (41%, 47%, 21%) are presented without confidence intervals or statistical tests. It is also unclear whether these proportions are corrected for the relative abundance of disordered versus structured sequence in the proteome, which could bias the comparison.
- **Why it matters** The claim that disordered regions are enriched for DNA-binding determinants is a central finding. If the classification is not robust or the comparison is not properly controlled, the conclusion may be an artifact of the analysis.
- **Resolution test** Specify the disorder prediction method used for the classification in Figure 4A. Provide statistical tests (e.g., chi-square or Fisher's exact test) with effect sizes and confidence intervals for the comparison of binding proportions. Consider controlling for the overall prevalence of disordered versus structured sequence in the TF set.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of the mutation screen
- **Claim pointer** "swapping that increased peptide charge led to higher-than-WT binding scores as exemplified by the swapping GP or ST to KR"; "binding scores were largely invariant to the precise positioning of the 17 NQ residues"
- **Evidence pointer** Results section "Mutation screen of the Msn2 TF"; Figure 5
- **Concern** The mutation screen is described qualitatively, with examples given but no systematic quantitative analysis. It is unclear how many mutations were tested in each category, what the distribution of effects was, and whether the observed trends are statistically significant. The statement that NQ positioning has no effect is based on a null result, but the power to detect such an effect is not discussed.
- **Why it matters** The mutation screen is presented as a key validation of the sequence determinants identified in the tiling library. Without rigorous statistical analysis, the conclusions about which features matter (charge, disorder, positioning) are not firmly established.
- **Resolution test** Provide a comprehensive analysis of the mutation screen, including the number of mutations per category, the distribution of binding scores, and statistical comparisons between categories (e.g., ANOVA or Kruskal-Wallis test). Report the power to detect effects of the size observed.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the findings
- **Claim pointer** "We apply this method to scan the full sequence space of budding yeast TFs for peptides that bind a long non-specific DNA region."
- **Evidence pointer** Results sections "DBD-annotated domains show a range of DNA binding capacities" and "NonDBD-derived peptides display a range of DNA binding comparable to annotated DBDs"
- **Concern** The study uses a single long DNA region (~2.6 kb) that includes coding sequences and a promoter. The authors state that binding is "dominated by non-specific association," but the sequence composition of this region could still bias which peptides bind. The generalizability of the findings to other DNA sequences, particularly native TF target sites, is not demonstrated.
- **Why it matters** The conclusions about TF binding determinants are meant to be general, but they are derived from a single DNA substrate. If the sequence composition of the test region influences the results, the findings may not extend to other genomic contexts.
- **Resolution test** Discuss the sequence composition of the test DNA region and its potential biases. Ideally, validate key findings with at least one additional DNA sequence of different composition, or provide a rationale for why the current region is representative.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Binding score normalization
- **Evidence pointer** Methods section "Analysis and statistics"
- **Issue** The description of the linear regression between abundance and fold change is brief. It is unclear whether the regression is performed on all peptides together or per experiment, and how outliers are handled.
- **Required correction** Provide a more detailed description of the regression procedure, including whether it is a simple linear regression, how the "distance from the regression line" is calculated (signed or absolute), and any outlier exclusion criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Methods section "Analysis and statistics"
- **Issue** The authors state that code and processed data are available on GitHub, but the manuscript does not provide a version number or a persistent identifier (e.g., Zenodo DOI).
- **Required correction** Provide a persistent identifier for the code repository and consider depositing the processed data in a permanent archive.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation of results
- **Affected element** Figure 2G and related text
- **Evidence pointer** Results section "DBD-annotated domains show a range of DNA binding capacities"
- **Issue** The correlation between DBD ohnologs (r=0.85) is mentioned, but it is unclear how many ohnolog pairs were analyzed and whether this correlation is significantly different from that expected by chance.
- **Required correction** Report the number of ohnolog pairs and provide a p-value or confidence interval for the correlation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of evolutionary analysis
- **Affected element** Figure S2C
- **Evidence pointer** Results section "DBD-annotated domains show a range of DNA binding capacities"
- **Issue** The statement that "strong binders diverged more slowly in evolution" is intriguing but the analysis is not described in the main text. It is unclear how divergence rate was measured and whether this analysis controls for other factors such as gene essentiality.
- **Required correction** Briefly describe the evolutionary analysis in the main text or refer to a detailed methods section, and discuss potential confounding factors.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "nonDBD" usage
- **Evidence pointer** Throughout
- **Issue** The term "nonDBD" is used to refer to regions outside the DBD, but this is potentially confusing as it could also be read as "non-DNA-binding domain" in a functional sense. The authors clarify that these regions can bind DNA, so the term is somewhat misleading.
- **Required correction** Consider using a more neutral term such as "regions outside the DBD" or "non-DBD regions" consistently, or define "nonDBD" clearly at first use.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of a clear, quantitative definition of binding and its statistical confidence.
  - R1-M2: Insufficient statistical support for the enrichment of binding in disordered regions.
  - R1-M3: Qualitative presentation of the mutation screen without systematic quantitative analysis.

- **Assessment against Nature-style criteria**
  - **Originality** The method is a novel adaptation of an existing approach and addresses a real need. The application to a comprehensive TF set is valuable. However, the conceptual advance is incremental rather than transformative.
  - **Scientific importance** The findings have the potential to inform models of TF-DNA binding, particularly regarding the role of disordered regions. The resource generated will be useful to the community. The importance is moderate to high, depending on the robustness of the conclusions.
  - **Interdisciplinary readership** The work is primarily of interest to molecular biologists and computational biologists studying gene regulation. The method could have broader applications, but the current presentation is focused on the yeast TF system.
  - **Technical soundness** The experimental design is reasonable, but the lack of quantitative detail and statistical rigor in key analyses prevents full assessment. The method validation is incomplete.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible. The abstract and introduction are clear. However, the results sections assume familiarity with the MPBA method and yeast TF biology.

- **Recommendation posture** Supportive if technical concerns are resolved. The method is promising and the biological questions are important, but the current manuscript does not provide sufficient quantitative evidence to fully support the central claims. The authors should address the major concerns regarding the definition of binding, statistical support for the disorder enrichment, and the analysis of the mutation screen before the case is established.