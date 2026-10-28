## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided by the user.
- **Assessment boundary** Scientific content, methodological soundness, interpretation of results, and alignment with stated claims. Editorial and formatting issues are noted only where they affect comprehension or reproducibility.
- **Shared manuscript claim summary** The authors report four rare germline JAK/STAT variants (JAK3P151R, JAK3R925S, STAT5AV494L, STAT6Q633H) in a three-generation Tyrolean family, inherited without clinical manifestations, and associated with enhanced basal and virus-induced immune transcriptomes in a subset of carriers. They propose context-dependent and combinatorial effects, including possible epistasis with TYK2 variants.
- **Visible evidence base** WES data from 17 family members; RNA-seq data from 13 family members (baseline and post-Omicron infection); in silico pathogenicity predictions (AlphaMissense, PolyPhen-2, REVEL); AlphaFold3 structural predictions; ClinVar and population frequency annotations; differential expression and gene set enrichment analyses.
- **Missing materials affecting confidence** No raw sequencing data, no variant-level quality metrics, no full differential expression tables (only volcano plots and enrichment summaries), no statistical model details for epistasis analysis, no functional validation experiments, no clinical phenotype details beyond absence of overt manifestations, and no access to supplementary tables (Table S1–S4) referenced in the text.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in human genetics: the heritability and functional impact of rare germline variants in JAK/STAT pathways. The family-based design is a strength, and the integration of WES, RNA-seq, and structural prediction is commendable. However, the evidence presented is largely descriptive and associative. The claim that these variants contribute to enhanced immune transcriptomes is supported only in a subset of carriers, with small numbers and no functional validation. The inconsistency among in silico tools is acknowledged but not resolved. The manuscript would benefit from clearer statistical frameworks, additional validation, and a more cautious interpretation of causality. The current evidence does not fully establish the central claim of context-dependent transcriptional impact.
- **Who would be interested in the results, and why** Geneticists and immunologists studying rare variants, incomplete penetrance, and modifier effects in immune pathways. Clinicians interested in JAK/STAT-related disorders may find the family-based inheritance data useful. Researchers using AI-based structural prediction tools may also be interested in the application of AlphaFold3 to variant interpretation.
- **Major strengths** 1) Family-based design with three generations, reducing environmental confounding. 2) Integration of multiple data types (WES, RNA-seq, structural prediction, population frequency). 3) Identification of a novel variant (STAT5AV494L) not previously catalogued. 4) Honest acknowledgment of limitations, including the inability of in silico methods to determine gain- or loss-of-function. 5) Discussion of combinatorial and epistatic effects is conceptually valuable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (small sample size and lack of statistical power), R1-M2 (lack of functional validation), R1-M3 (inconsistent in silico predictions not resolved), R1-M4 (confounded comparison between baseline and infection states), R1-M5 (epistasis analysis not adequately described or validated).
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The concept of context-dependent effects of rare variants is not new, but the specific family and variant combination are novel.  
  - **Scientific importance** Moderate. The findings are potentially relevant to understanding incomplete penetrance and modifier effects, but the evidence is too preliminary to have broad impact.  
  - **Interdisciplinary readership** Limited. The manuscript will appeal mainly to specialists in immunogenetics and JAK/STAT biology.  
  - **Technical soundness** Weak. The analysis is largely descriptive, with small sample sizes and no functional validation. Statistical methods for differential expression and epistasis are not fully described.  
  - **Readability for nonspecialists** Acceptable. The text is generally clear, but some sections (e.g., structural analysis) assume familiarity with JAK/STAT domain architecture.  
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an interesting case report but does not provide sufficient evidence to support the claim that these variants causally influence immune transcriptomes. Major revisions and additional data are required.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical power and sample size  
- **Claim pointer** The authors claim that the variants are associated with enhanced basal and virus-induced immune transcriptomes in a subset of carriers.  
- **Evidence pointer** Section 2.2, Figures 3 and 4, Tables S3 and S4  
- **Concern** The analysis is based on 13 individuals with RNA-seq data, and the number of carriers for each variant is very small (e.g., only one individual for some combinations). Differential expression analyses with such small groups are prone to false positives and lack statistical power. The authors do not report effect sizes, confidence intervals, or correction for multiple testing beyond a single mention of Benjamini–Hochberg.  
- **Why it matters** Without adequate power, the observed transcriptional differences cannot be reliably attributed to the variants. The claim of association is therefore not robust.  
- **Resolution test** Provide a power analysis, report effect sizes and confidence intervals, and consider using mixed-effects models that account for family structure. If sample size cannot be increased, the claims should be tempered to descriptive observations.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Functional validation  
- **Claim pointer** The authors suggest that the variants may have functional impact, particularly JAK3R925S and STAT6Q633H, based on structural and in silico predictions.  
- **Evidence pointer** Section 2.1, Section 3, Table 1  
- **Concern** No functional experiments are performed. The manuscript relies entirely on computational predictions and transcriptomic associations. The authors acknowledge this limitation but do not provide any experimental evidence to support the proposed effects.  
- **Why it matters** In silico predictions are not sufficient to establish biological function. Without functional validation, the claim that these variants impact immune transcriptomes remains speculative.  
- **Resolution test** Perform in vitro assays (e.g., reporter assays, phosphorylation assays, or cell-based functional studies) for at least the most promising variants. Alternatively, clearly state that the study is hypothesis-generating and remove causal language.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** In silico prediction inconsistency  
- **Claim pointer** The authors state that in silico tools presented a complex and contradictory picture, with some suggesting pathogenicity and others benign effects.  
- **Evidence pointer** Section 3, Table 1  
- **Concern** The inconsistency among prediction tools is acknowledged but not resolved. The authors do not provide a framework for interpreting conflicting predictions, nor do they prioritize which tools are most reliable for these specific variants.  
- **Why it matters** If the predictions are contradictory, the evidence for pathogenicity or functional impact is weak. The manuscript should either reconcile these differences or explicitly state that the predictions are inconclusive.  
- **Resolution test** Provide a detailed comparison of prediction scores, discuss the strengths and limitations of each tool, and justify any conclusions drawn from them. If predictions are inconclusive, state this clearly and avoid overinterpretation.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Confounded comparison between baseline and infection states  
- **Claim pointer** The authors compare baseline transcriptomes and post-Omicron infection transcriptomes, and claim that carriers show enhanced responses.  
- **Evidence pointer** Section 2.2, Figures 3 and 4  
- **Concern** The baseline and infection data were collected at different times, and the infection state may introduce confounding factors such as time since symptom onset, immune status, and treatment. The authors do not describe how these factors were controlled for.  
- **Why it matters** Without controlling for these confounders, the observed differences between carriers and non-carriers may be due to factors other than the variants.  
- **Resolution test** Provide detailed clinical metadata for each individual, including time since infection, symptom severity, and any medications. Use statistical models that adjust for these covariates.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Epistasis analysis  
- **Claim pointer** The authors performed epistasis analyses using the Epistasis Disease Atlas and detected no significant interactions.  
- **Evidence pointer** Section 2, Table S2  
- **Concern** The epistasis analysis is described in a single sentence, with no details on the methods, the variants tested, the statistical model, or the power to detect interactions. The maximum-likelihood scores from NeEDL are mentioned but not explained.  
- **Why it matters** The claim that there are no significant epistatic interactions is not supported without a clear description of the analysis.  
- **Resolution test** Provide a full description of the epistasis analysis, including the variants included, the statistical model, and the criteria for significance. If the analysis is underpowered, state this limitation.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of methods  
- **Affected element** Section 4.3  
- **Evidence pointer** Section 4.3  
- **Issue** The RNA-seq variant calling pipeline uses hg19 for alignment, while WES uses hg38. The text states that coordinates were lifted from hg19 to hg38, but it is unclear whether this was done for all variants and whether any variants were lost in the lift-over process.  
- **Required correction** Clarify the lift-over procedure and report any variants that could not be mapped.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reporting of clinical data  
- **Affected element** Section 4.1  
- **Evidence pointer** Section 4.1  
- **Issue** The authors state that all family members lived in the same geographical area and had similar lifestyles, but no specific details are provided.  
- **Required correction** Provide a brief description of the family’s living conditions and any relevant lifestyle factors.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Figure quality  
- **Affected element** Figures 2 and 3  
- **Evidence pointer** Figures 2 and 3  
- **Issue** The figures are referenced but not described in detail. It is unclear whether the volcano plots show all genes or only significant ones, and whether the structural models are annotated clearly.  
- **Required correction** Ensure figures are self-explanatory, with clear labels and legends.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Language and terminology  
- **Affected element** Section 1  
- **Evidence pointer** Section 1  
- **Issue** The introduction contains a sentence that appears incomplete or garbled: "The STAT6Q633H variant is located in the SH2 linker region and gain." This is likely a typographical error.  
- **Required correction** Correct the sentence to read clearly, e.g., "and gain-of-function germline mutations have been identified in this region."

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Supplementary data accessibility  
- **Affected element** Tables S1–S4  
- **Evidence pointer** Tables S1–S4  
- **Issue** The manuscript references four supplementary tables, but their content is not described in the text.  
- **Required correction** Provide a brief description of each supplementary table in the main text or in a supplementary file legend.

## Risk / unsupported claims
- The claim that the variants are associated with enhanced basal and virus-induced immune transcriptomes is not robustly supported due to small sample sizes and lack of statistical power.
- The claim that JAK3R925S and STAT6Q633H may be gain-of-function variants is speculative and not supported by functional data.
- The claim that the variants act as genetic modifiers rather than standalone drivers is an interpretation that is not directly tested.
- The epistasis analysis is not described in sufficient detail to be evaluated.
- The absence of clinical manifestations is based on limited clinical data, and the authors do not specify what clinical assessments were performed.