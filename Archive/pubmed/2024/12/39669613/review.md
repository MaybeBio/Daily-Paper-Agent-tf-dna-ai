## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplemental figure/table references
- **Assessment boundary** Computational analyses and statistical claims as presented; no independent verification of raw data or code possible from supplied material
- **Shared manuscript claim summary** The authors present an untargeted, genome-wide computational framework integrating rare single-nucleotide variants (rSNVs) and copy-number variants (rCNVs) with regulatory genomic annotations, deep learning prioritization, and target gene prediction to implicate regulatory elements in spina bifida (SB) pathophysiology. They report enrichment of rSNVs in specific transcription factor binding sites (TFBSs), particularly CTCF, and significant localization of rCNVs to topologically associating domain (TAD) boundaries and brain-specific enhancers in SB cases versus controls.
- **Visible evidence base** Main text figures 1-6, supplemental figures 1-6, supplemental tables 1-2, methods descriptions, statistical results as reported in text
- **Missing materials affecting confidence** Raw variant call data, cohort-level genotype files, code or software version details, complete supplemental tables (only referenced), detailed demographic/ancestry matching metrics, multiple testing correction details for all analyses, effect size estimates with confidence intervals

## Reviewer
- **Overall assessment** This manuscript presents a methodologically ambitious and potentially valuable computational framework for investigating regulatory variant contributions to spina bifida. The integration of multiple annotation layers, deep learning prioritization, and 3D genomic context is commendable and represents a step beyond conventional protein-coding variant analyses. However, several technical concerns regarding statistical rigor, multiple testing burden, validation of computational predictions, and clarity of the analytical pipeline limit the strength of the conclusions as currently presented. The core finding of TFBS enrichment, particularly CTCF, is intriguing but requires stronger statistical support and functional validation to be fully convincing.
- **Who would be interested in the results, and why** Researchers in neurodevelopmental genetics, specifically those studying neural tube defects and structural birth defects, would find this work relevant. The computational framework itself may interest methodologists developing integrative approaches for noncoding variant interpretation. Clinicians and genetic counselors involved in SB risk assessment may also find the resource valuable, though clinical applicability remains distant.
- **Major strengths** The study addresses an important gap by moving beyond protein-coding variant analysis to systematically interrogate regulatory genomic elements in SB. The use of an untargeted, genome-wide approach avoids candidate gene bias. The integration of multiple complementary computational tools, including tissue-specific TFBS annotations, deep learning prioritization, and 3D genomic context, represents a sophisticated analytical strategy. The inclusion of orthogonal datasets for validation of enhancer associations strengthens the findings.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (multiple testing correction), R1-M2 (validation of deep learning predictions), R1-M3 (target gene assignment methodology), R1-M4 (CNV calling validation)
- **Assessment against Nature-style criteria** 
  - **Originality** Moderate to high. The integrative approach combining TFBS, deep learning, and 3D genomic context for SB is novel, though individual components have been applied in other contexts.
  - **Scientific importance** Moderate. The findings could inform SB genetics, but the lack of functional validation and modest effect sizes limit immediate impact.
  - **Interdisciplinary readership** Moderate. The work bridges computational genomics, developmental biology, and clinical genetics, but technical complexity may limit accessibility.
  - **Technical soundness** Currently insufficient. Several statistical and methodological concerns need resolution.
  - **Readability for nonspecialists** Adequate but could be improved. The methods are dense, and some results are presented without sufficient context for non-computational readers.
- **Recommendation posture** Supportive if technical concerns are resolved. The framework is promising and the findings are potentially important, but the current evidence base does not fully establish the case for regulatory variant contributions to SB.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report significant enrichment of rSNVs in specific TFBSs, particularly CTCF, KLF5, and BATF, in SB cases versus controls.
- **Evidence pointer** Results section "TFBS motifs are enriched in SB cases by rare single-nucleotide variants", Figure 2
- **Concern** The enrichment analysis tests thousands of TFBS motifs simultaneously, yet the manuscript does not describe how multiple testing was addressed. The reported hypergeometric P values for individual motifs, including the top hits CTCF, KLF5, and BATF, appear to be uncorrected. With thousands of motifs tested, the probability of false positives is substantial. The authors must specify the total number of motifs tested, the multiple testing correction method applied, and report adjusted P values or false discovery rates.
- **Why it matters** Without appropriate multiple testing correction, the central claim of TFBS enrichment in SB cases cannot be distinguished from chance findings. This is the foundational result upon which subsequent analyses depend.
- **Resolution test** Provide the total number of motifs tested, apply and report Benjamini-Hochberg or equivalent correction, and confirm that CTCF, KLF5, and BATF remain significant after correction. If they do not, the claim of specific TFBS enrichment must be revised.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of computational predictions
- **Claim pointer** The authors state that deep learning prioritization using DeepSEA identified functionally relevant variants, and that variants were classified as likely to alter gene expression (LAGE).
- **Evidence pointer** Methods section "Deep learning prioritization", Results section "TFBS motifs are enriched in SB cases by rare single-nucleotide variants"
- **Concern** The manuscript does not provide any validation of DeepSEA predictions in this specific context. DeepSEA was trained on different cell types and genomic contexts, and its transferability to neural tube development is assumed but not demonstrated. The authors do not report how many variants were classified as LAGE, what threshold was used, or whether any independent evidence supports these predictions. The claim that specific variants are "likely to alter gene expression" requires either experimental validation or at minimum cross-validation with orthogonal computational methods.
- **Why it matters** The entire downstream analysis, including target gene identification and pathway enrichment, depends on the reliability of LAGE classifications. If these classifications are inaccurate, all subsequent conclusions are compromised.
- **Resolution test** Provide the distribution of DeepSEA scores, the threshold used for LAGE classification, and validation using an independent method (e.g., alternative deep learning models, experimental datasets of regulatory variants, or CRISPR validation in relevant cell lines). If validation is not possible, temper the language from "likely to alter gene expression" to "predicted to alter gene expression."

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Target gene assignment
- **Claim pointer** The authors used GeneHancer to predict target genes for TFBS-rSNVs and identified 107 genes overrepresented in SB cases, which were then used for pathway and functional module analyses.
- **Evidence pointer** Methods section "Target gene prediction and enrichment", Results section "TFBS motifs are enriched in SB cases by rare single-nucleotide variants", Figure 3
- **Concern** GeneHancer assigns enhancer-gene relationships based on a combination of evidence types, but the accuracy of these assignments varies considerably by genomic context. The manuscript does not describe how many TFBS-rSNVs were assigned to target genes, the confidence levels of these assignments, or how the 107 overrepresented genes were selected. The comparison of observed versus expected chromosomal distributions (Supplemental Figure 1) is mentioned but not described in sufficient detail. The pathway enrichment results depend entirely on the accuracy of these gene assignments.
- **Why it matters** If target gene assignments are inaccurate, the pathway and functional module analyses will produce misleading results. The claim that specific biological processes are affected in SB requires confidence in the gene-level assignments.
- **Resolution test** Provide detailed statistics on GeneHancer assignments, including the number of variants assigned, confidence score distributions, and sensitivity analyses using alternative enhancer-gene mapping approaches. Confirm that the 107-gene set is robust to different assignment strategies.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** CNV calling and interpretation
- **Claim pointer** The authors report significant enrichment of rCNVs overlapping TAD boundaries and brain-specific enhancers in SB cases versus controls.
- **Evidence pointer** Results section "Rare CNVs localize to relevant functional regulatory elements", Figure 5
- **Concern** The CNV calling pipeline is described as "high-confidence" and "previously detailed," but no performance metrics are provided for this specific dataset. The manuscript does not report the number of rCNVs detected per individual, the size distribution, or the false discovery rate of the calling pipeline. The comparison of rCNV localization to TAD boundaries and enhancers requires careful consideration of genomic background rates, as these features cover substantial portions of the genome. The authors must demonstrate that the observed enrichment is not simply due to the genomic coverage of these features.
- **Why it matters** CNV calling is notoriously prone to false positives, particularly for smaller events. If the CNV calls are unreliable, the enrichment findings are meaningless. The interpretation of TAD boundary disruption as a mechanism requires confidence in both the CNV calls and the boundary annotations.
- **Resolution test** Provide CNV calling performance metrics (precision, recall) for this dataset, the number and size distribution of rCNVs, and a background model that accounts for the genomic coverage of TAD boundaries and enhancers. Consider orthogonal validation of a subset of CNV calls.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Ancestry matching
- **Evidence pointer** Methods section "Study population and genome sequencing"
- **Issue** The description of ancestry matching is vague. The authors state that cases and controls were "ancestry matched" based on "population structure analyses using PLINK," but no details are provided on the number of principal components used, the threshold for matching, or the resulting distribution of ancestries in both groups.
- **Required correction** Provide specific details on the ancestry matching procedure, including the number of principal components, the matching algorithm, and a table or figure showing the ancestry distribution of cases and controls.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Effect sizes
- **Evidence pointer** Results sections throughout
- **Issue** The manuscript reports P values for various comparisons but rarely provides effect sizes or confidence intervals. For example, the enrichment of rCNVs at TAD boundaries is reported with a P value but no measure of the magnitude of enrichment.
- **Required correction** Report effect sizes (e.g., odds ratios, fold enrichments) with confidence intervals for all significant findings to allow readers to assess the biological relevance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability
- **Evidence pointer** Data Availability section
- **Issue** The data availability statement indicates that data are available upon request, but no mention is made of code availability. Given the computational nature of this study, the lack of code availability limits reproducibility.
- **Required correction** Provide a statement on code availability, ideally with a link to a public repository containing the analysis scripts and pipelines.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Discussion of limitations
- **Evidence pointer** Discussion section
- **Issue** The limitations section focuses on the cell-type specificity of regulatory dynamics but does not address the fundamental limitation that all findings are computational predictions without experimental validation. The authors mention future functional studies but do not acknowledge the provisional nature of their conclusions.
- **Required correction** Add a paragraph explicitly stating that all findings are computational predictions requiring experimental validation, and discuss the potential for false positives in the absence of such validation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 4
- **Evidence pointer** Figure 4
- **Issue** Figure 4C is described as showing nucleotide-level resolution, but the figure as described appears to be a genome browser screenshot. The resolution and readability of this figure may be limited in print.
- **Required correction** Consider providing a higher-resolution version or a simplified schematic that clearly shows the variant positions relative to the TFBS and gene structure.

## Risk / unsupported claims
- The claim that specific TFBSs, particularly CTCF, are enriched for rSNVs in SB cases is unsupported without evidence of multiple testing correction.
- The claim that variants are "likely to alter gene expression" (LAGE) is unsupported without validation of DeepSEA predictions in this context.
- The claim that rCNVs at TAD boundaries may disrupt insulation and promote ectopic enhancer-promoter contacts is speculative and not directly tested.
- The pathway and functional module analyses are dependent on GeneHancer target gene assignments, which are not validated in this study.
- The biological significance of the identified genes and pathways is inferred from computational predictions without experimental evidence.
- The generalizability of findings beyond the specific cohorts studied is unclear given the limited description of population structure and potential confounding factors.