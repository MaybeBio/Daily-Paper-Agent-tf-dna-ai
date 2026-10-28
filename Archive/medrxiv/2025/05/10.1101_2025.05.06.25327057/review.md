## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose a computational framework using sequence-based deep learning models to prioritize rare and ultra-rare somatic SNVs in promoter regions, identify promoter regions enriched for putatively functional mutations, validate findings across cohorts and with an independent model, and nominate candidate cancer genes including both known and novel loci
- **Visible evidence base** Abstract text only; no quantitative results beyond a single p-value, no cohort details, no model performance metrics, no validation statistics
- **Missing materials affecting confidence** Full methods, all figures and tables, cohort descriptions, model training and evaluation details, cross-cohort validation procedures, replication analysis with Borzoi, and any supplementary data

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable framework for addressing a difficult problem in cancer genomics, namely the interpretation of rare non-coding variants. The use of sequence-based models trained on functional data is a reasonable and timely approach. However, the abstract provides insufficient detail to evaluate the robustness of the methods, the validity of the statistical claims, or the biological significance of the findings. Several claims appear to be under-supported or internally inconsistent, and the lack of methodological transparency prevents a rigorous assessment of the framework's utility.
- **Who would be interested in the results, and why** Cancer genomics researchers, particularly those studying non-coding driver mutations and regulatory elements; computational biologists developing and applying deep learning models for variant effect prediction; clinical genomics groups interested in interpreting rare variants in cancer genomes. The framework could also be of interest to researchers studying promoter function and gene regulation in disease contexts.
- **Major strengths** The problem addressed is important and timely, as non-coding driver discovery remains a major challenge. The use of a large cohort of 24,529 whole-tumour genomes provides substantial statistical power. The inclusion of cross-cohort validation and replication with an independent model (Borzoi) is a strong design element that increases confidence in the findings. The identification of both known cancer genes and novel candidates suggests the framework has potential for discovery.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: The approach of applying sequence-based deep learning models to prioritize rare promoter mutations is not entirely novel, as similar strategies have been proposed for coding variants and for non-coding variants in other contexts. However, the specific combination of PARM, large-scale tumor genome data, and cross-model validation may offer some originality. The abstract does not clearly articulate what is conceptually new beyond the specific implementation.
  - Scientific importance: The problem is of high importance, and the potential to identify novel cancer genes through non-coding mutations would be a significant contribution. However, the abstract does not provide enough evidence to establish the importance of the specific findings, particularly the novel candidate genes.
  - Interdisciplinary readership: The work sits at the intersection of cancer genomics, computational biology, and regulatory genomics, and could appeal to readers across these fields. The abstract is written in a way that is largely accessible, though some technical terms (e.g., PARM, Borzoi) are not explained.
  - Technical soundness: Cannot be adequately assessed from the abstract alone. The statistical methods, model validation, and replication procedures are not described in sufficient detail. The apparent inconsistency in the list of novel genes raises concerns about the rigor of the analysis.
  - Readability for nonspecialists: The abstract is generally readable, but the lack of context for the models and the statistical methods may limit accessibility for readers outside the immediate field.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting framework and potentially important findings, but the lack of methodological detail and apparent internal inconsistencies prevent a supportive recommendation. A full manuscript with detailed methods and results would be required to assess whether the claims are substantiated.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** "We identified up to 492 promoter regions significantly enriched for putatively functional SNVs" and "functional promoter mutations are significantly enriched in established cancer-driver genes (p-value = 9.7·10-5)"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract reports a single p-value for enrichment of functional promoter mutations in cancer-driver genes but provides no details on the statistical test used, the null model, multiple testing corrections, or the number of comparisons performed. Similarly, the identification of "up to 492 promoter regions" is presented without any description of the significance threshold, the correction method, or the variability across cohorts implied by the phrase "up to."
- **Why it matters** Without a clear description of the statistical framework, it is impossible to assess whether the reported enrichments are robust or could arise from multiple testing, confounding factors, or model biases. The p-value alone is insufficient to establish the significance of the finding.
- **Resolution test** Provide a detailed description of the statistical methods, including the null model, multiple testing correction, and sensitivity analyses. Report the number of significant regions per cohort and the consistency of the enrichment across cohorts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency
- **Claim pointer** "These genes included well known cancer genes such as including TERT, TP53 and PMS2, but also several new candidates for which no coding mutations have previously been implicated in cancer, including PMS2, AIMP2, SASS6, RPL13A, ALKBH4, FICD and YAE1"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract lists PMS2 both as a "well known cancer gene" and as a "new candidate for which no coding mutations have previously been implicated in cancer." This is internally contradictory. PMS2 is a well-established DNA mismatch repair gene with known cancer associations, so its inclusion in the novel candidate list is confusing and undermines the credibility of the claims.
- **Why it matters** Internal inconsistencies in the reporting of key results raise questions about the rigor of the analysis and the accuracy of the gene lists. If the novel candidate list contains known cancer genes, the claim of discovering "new candidates" is weakened.
- **Resolution test** Clarify the classification of genes as known versus novel. Provide a clear definition of what constitutes a "new candidate" and ensure that the lists are mutually exclusive and accurate.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Cross-cohort validation and replication using an independent sequence-based model (Borzoi) identified nine candidate cancer genes where the prioritized promoter mutations were shown to be functional by affecting gene expression levels"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract claims that nine candidate genes were identified through cross-cohort validation and replication with Borzoi, and that the prioritized mutations were "shown to be functional by affecting gene expression levels." However, no details are provided on the nature of the functional evidence, the effect sizes, the statistical significance of the expression effects, or the criteria for selecting the nine genes. The term "shown to be functional" implies experimental validation, but it is unclear whether this refers to computational predictions, reporter assays, or endogenous expression analyses.
- **Why it matters** The claim of functional validation is central to the paper's contribution. Without details on how functionality was demonstrated, the strength of the evidence cannot be evaluated, and the claim may overstate the findings.
- **Resolution test** Describe the functional validation approach in detail, including the assays used, the number of mutations tested, the effect sizes, and the statistical significance. Clarify whether the evidence is computational or experimental.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "We analysed SNVs derived from 24,529 whole-tumour genomes from three cohorts and applied the sequence-based model PARM, which was trained on massively parallel reporter assay data"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not describe the criteria for selecting SNVs, the definition of promoter regions, the filtering steps applied, or the handling of germline variants and population stratification. Additionally, the choice of PARM and the rationale for its use are not explained, nor is the threshold for classifying a mutation as "putatively functional."
- **Why it matters** The framework's utility depends on the rigor of the variant filtering and the appropriateness of the model. Without these details, the results cannot be reproduced or independently assessed, and potential biases in variant selection or model application cannot be ruled out.
- **Resolution test** Provide a detailed description of the variant calling, filtering, and annotation pipeline, as well as the criteria for defining promoter regions and functional mutations. Justify the choice of PARM and describe its performance characteristics.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Gene list
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "well known cancer genes such as including TERT, TP53 and PMS2" contains a grammatical error ("such as including") and is redundant. Additionally, the list of novel candidates includes genes that may not be widely recognized, and the abstract does not provide any context for their potential roles in cancer.
- **Required correction** Revise the sentence for clarity and grammatical correctness. Consider providing a brief explanation of why the novel genes are plausible cancer candidates.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "ultra-rare"
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "ultra-rare" is used without a definition. It is unclear what allele frequency threshold distinguishes "rare" from "ultra-rare" in this context.
- **Required correction** Define the allele frequency thresholds used to classify variants as rare or ultra-rare.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Model description
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract mentions PARM and Borzoi without explaining what these models are or why they were chosen. Readers unfamiliar with these tools may struggle to understand the approach.
- **Required correction** Provide brief descriptions of PARM and Borzoi, including their training data and intended applications.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reporting
- **Affected element** "up to 492"
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "up to 492 promoter regions" is vague. It is unclear whether this number varies across cohorts, thresholds, or model versions, and the abstract does not explain the source of the variability.
- **Required correction** Specify the conditions under which 492 regions were identified and report the range or distribution of significant regions across cohorts.

## Risk / unsupported claims
- The claim that "functional promoter mutations are significantly enriched in established cancer-driver genes" is supported only by a single p-value with no methodological context; the statistical robustness cannot be assessed.
- The claim that nine candidate genes were "shown to be functional by affecting gene expression levels" is unsupported without details on the functional assays or analyses.
- The list of novel candidate genes is internally inconsistent (PMS2 appears in both known and novel categories), undermining the reliability of the gene classifications.
- The identification of "up to 492 promoter regions" is presented without sufficient detail on thresholds or cohort-specific results, making the claim difficult to interpret.
- The general utility of the framework for "uncovering regulatory elements implicated in cancer" is a broad claim that cannot be evaluated from the abstract alone.