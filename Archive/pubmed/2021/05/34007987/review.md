## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that genetic variants in two hypoxia-sensing genes, EGLN1 and HIF1AN, are associated with high-altitude pulmonary edema (HAPE) in three human groups. They identify three EGLN1 SNPs and haplotypes as significant, show differential blood gene expression and protein levels correlated with clinical parameters and alleles, and provide functional evidence for allele-specific transcription factor binding at these loci using multiple assays and docking simulations.
- **Visible evidence base** Abstract text only; no raw data, statistical details, cohort descriptions, or methodological specifics are provided
- **Missing materials affecting confidence** Full manuscript, cohort demographics and sample sizes, genotyping and sequencing protocols, statistical models and multiple-testing corrections, all figures and tables, supplementary data, and detailed functional assay results

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting genetic and functional study of HAPE susceptibility, with a plausible link between EGLN1 variants and transcription factor binding. However, the evidence as summarized is insufficient to establish the central claims. Key statistical, methodological, and functional details are absent, and the abstract does not demonstrate that the reported associations are robust or that the functional assays are conclusive. The work may be of interest to researchers in high-altitude medicine and hypoxia biology, but the case is not currently established from the provided material.
- **Who would be interested in the results, and why** Researchers studying high-altitude physiology and pathology, genetic predisposition to hypoxia-related disorders, and transcriptional regulation of hypoxia-inducible factors. Clinicians managing HAPE may also find the genetic markers relevant for risk stratification, though clinical utility is not demonstrated here.
- **Major strengths** The study addresses a clinically relevant condition with a clear genetic hypothesis. The use of multiple complementary approaches, including sequencing, genotyping, haplotyping, expression analysis, and functional assays, suggests a comprehensive design. The identification of specific transcription factors and allele-specific binding adds mechanistic depth.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate, as genetic associations in EGLN1 with HAPE have been previously reported, though the transcription factor binding mechanism may be novel. Scientific importance is limited by the lack of demonstrated robustness and clinical translation. Interdisciplinary readership is possible but not strongly supported given the narrow focus. Technical soundness cannot be assessed from the abstract alone, and several methodological concerns remain. Readability for nonspecialists is acceptable, but the abstract assumes familiarity with genetic and molecular terminology.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if the technical concerns are resolved with full data and analyses.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness
- **Claim pointer** The abstract states that three EGLN1 SNPs and their haplotypes emerged significant in HAPE.
- **Evidence pointer** Abstract, results section; location not provided
- **Concern** The abstract does not report effect sizes, confidence intervals, or P values for the SNP and haplotype associations. It is unclear whether multiple-testing corrections were applied, given that multiple SNPs and haplotypes were tested. The sample sizes for the three groups are not stated, and the power to detect associations is unknown.
- **Why it matters** Without these details, the reported significance cannot be evaluated for false-positive risk. Genetic association studies in complex traits are prone to spurious findings, and the absence of correction and effect size information undermines confidence in the primary claim.
- **Resolution test** Provide the full statistical results, including adjusted P values, odds ratios or equivalent effect measures, and sample sizes. State the multiple-testing correction method used and justify the study power.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional evidence
- **Claim pointer** The abstract claims that allele-specific transcription factor binding of FUS with rs1538664A, ARHDGIA with rs479200T, and HYOU1 with rs480902C was confirmed by luciferase assay, EMSA, LC-MS/MS, and supershift assays.
- **Evidence pointer** Abstract, results section; location not provided
- **Concern** The abstract does not specify which assays were used for which SNP, the magnitude of allele-specific differences, or the number of replicates. It is unclear whether the transcription factor identities were validated by independent methods or whether the LC-MS/MS results were confirmed by supershift for all three factors. The functional relevance of these transcription factors in pulmonary edema is not established.
- **Why it matters** The mechanistic claim is central to the paper's novelty. If the allele-specific binding is not robustly demonstrated or if the transcription factors are not functionally linked to HAPE pathophysiology, the conclusion that these variants regulate hypoxia-inducible responses is unsupported.
- **Resolution test** Provide detailed assay results, including quantitative data for allele-specific differences, replicate numbers, and statistical tests. Clarify which transcription factors were confirmed by which methods and show that the identified factors are expressed in relevant cell types and affect downstream hypoxia-responsive genes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Correlation with clinical parameters
- **Claim pointer** The abstract states that blood gene expression and protein levels differed significantly and correlated with clinical parameters and respective alleles.
- **Evidence pointer** Abstract, results section; location not provided
- **Concern** The abstract does not specify which clinical parameters were correlated, the direction of correlations, or the correlation coefficients and P values. It is unclear whether the expression and protein differences were adjusted for confounders such as age, sex, or medication use. The biological relevance of blood-based expression to lung-specific pathophysiology is not addressed.
- **Why it matters** The claim that expression and protein levels correlate with clinical parameters is used to support the functional significance of the genetic variants. Without clear statistical and clinical context, this correlation could be spurious or clinically meaningless.
- **Resolution test** List the clinical parameters tested, provide correlation statistics with confidence intervals, and describe adjustment for potential confounders. Discuss the relevance of blood expression to pulmonary edema mechanisms.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Study design and population
- **Claim pointer** The abstract describes three well-characterized groups: highland natives, HAPE-free controls, and HAPE-patients.
- **Evidence pointer** Abstract, methods section; location not provided
- **Concern** The abstract does not define the criteria for HAPE diagnosis, the matching of groups for age, sex, ethnicity, or altitude exposure, or the recruitment setting. It is unclear whether the HAPE-free controls were sojourners or highland natives, which would affect the interpretation of genetic associations. Population stratification is a major concern in genetic studies of high-altitude populations.
- **Why it matters** If the groups are not well matched or if population stratification is not addressed, the reported genetic associations could reflect ancestry differences rather than HAPE susceptibility. The validity of the entire study depends on the comparability of the groups.
- **Resolution test** Provide detailed cohort descriptions, including diagnostic criteria, sample sizes, matching variables, and methods to control for population stratification, such as principal component analysis or ancestry-informative markers.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract, methods section
- **Evidence pointer** Abstract, methods section; location not provided
- **Issue** The term "multifactor dimensionality reduction" is used without explanation. Nonspecialist readers may not understand what this method entails or why it was chosen.
- **Required correction** Briefly describe the method or provide a citation in the abstract, or move the technical detail to the full text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of results
- **Affected element** Abstract, results section
- **Evidence pointer** Abstract, results section; location not provided
- **Issue** The abstract mentions HIF1AN in the introduction but does not report any results for this gene. It is unclear whether HIF1AN was analyzed and found non-significant or omitted from the analysis.
- **Required correction** State the outcome for HIF1AN, even if negative, to avoid ambiguity about the scope of the study.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Docking simulation interpretation
- **Affected element** Abstract, results section
- **Evidence pointer** Abstract, results section; location not provided
- **Issue** The abstract states that docking simulation studies were "in sync" with structural variations, but does not specify what was simulated or what the structural variations were. This claim is vague and not verifiable from the abstract.
- **Required correction** Provide a brief description of the docking approach and the key structural findings, or refer to a figure in the full text.

## Risk / unsupported claims
- The claim that the three EGLN1 SNPs and haplotypes are significant in HAPE is unsupported without effect sizes, P values, and multiple-testing corrections.
- The claim that allele-specific transcription factor binding was confirmed is unsupported without detailed assay results and replication.
- The claim that expression and protein levels correlate with clinical parameters is unsupported without specific correlation statistics and confounder adjustment.
- The claim that the two hydroxylases are crucial in regulation of hypoxia-inducible responses is an overstatement based on the abstract, as no direct functional link to HIF pathway activity is shown.
- The relevance of the identified transcription factors to HAPE pathophysiology is not established from the abstract.