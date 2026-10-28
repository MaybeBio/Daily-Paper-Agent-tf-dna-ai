## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, data availability) as provided by the user. No supplementary figures, tables, or methods details beyond what is in the text.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and clarity of the presented framework. No assessment of formatting, grammar, or editorial style beyond readability for a general scientific audience.
- **Shared manuscript claim summary** The authors present an integrative deep learning framework that links allele-specific enhancer prediction to TF-centered gene expression changes and drug-induced transcriptional profiles to prioritize drug repurposing candidates, using breast cancer as a proof-of-concept. They report recovery of fulvestrant and identification of 63 candidate compounds, with 54% showing anti-correlated transcriptional effects across eight breast cancer pathways.
- **Visible evidence base** Main text figures referenced (Fig. 1, 2, 3, 4, 5), supplementary figures (Fig. S1, S2), supplementary tables (Table S1, S2, S4), and main text Table 1. Methods section as provided. No actual figure images, table contents, or supplementary data were available for direct inspection.
- **Missing materials affecting confidence** Supplementary figures (S1, S2) and tables (S1, S2, S4) contents not provided. Full details of TREDNet architecture and training hyperparameters not included. Exact lists of the 63 prioritized compounds and 8 final shortlisted compounds not provided. Details of the LINCS data processing and normalization not fully specified. KnockTF 2.0 data processing and quality control not described.

## Reviewer

- **Overall assessment** This manuscript presents a conceptually interesting and potentially valuable framework for linking noncoding genetic variation to drug repurposing candidates. The integration of deep learning-based enhancer prediction, allele-specific variant scoring, TF-centered transcriptional analysis, and drug response data is a novel combination that addresses a real gap in the field. The proof-of-concept in breast cancer is well-chosen, and the recovery of fulvestrant provides a useful positive control. However, the manuscript has several significant methodological and evidentiary gaps that need to be addressed before the claims are fully supported. The reliance on computational predictions without experimental validation, the limited description of key methods, and the lack of direct comparison to existing approaches weaken the current case. The generalizability claims are also not fully substantiated by the data presented.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulation, variant interpretation, and drug repurposing would be the primary audience. Researchers studying breast cancer genomics and endocrine therapy resistance would also find the FOXA1-centered analysis relevant. The framework's potential for extension to other diseases could attract researchers in complex trait genetics and precision medicine. The work bridges regulatory genomics and pharmacology, which is an emerging area of interest for both fields.

- **Major strengths** 
  1. The conceptual framework is novel and addresses a genuine gap: most drug repurposing approaches do not explicitly model noncoding genetic variation.
  2. The integration of multiple data types (epigenomics, GWAS, TF perturbation, drug response) is ambitious and potentially powerful.
  3. The use of a well-characterized disease context (breast cancer) with a known positive control (fulvestrant) provides a useful validation strategy.
  4. The authors are appropriately cautious in their interpretation of motif enrichment as reflecting model-predicted regulatory contribution rather than direct binding evidence.
  5. The framework is described as generalizable, with clear steps for extension to other cell types and diseases.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the deep learning enhancer models "accurately distinguish active enhancers across seven cell lines" with AUROC of 0.91-0.98 and AUPRC of 0.58-0.86.
- **Evidence pointer** Fig. S1A-B, Methods section "Cell type-specific enhancer modeling"
- **Concern** The performance metrics are reported only as summary statistics without details on the evaluation procedure. The AUPRC range of 0.58-0.86 is notably lower than the AUROC range, which may indicate class imbalance issues. The text does not specify how the positive and negative sets were defined for evaluation, what the baseline performance would be, or how the models performed across different cell types individually. The claim of "accurate" distinction is not well-supported without these details.
- **Why it matters** The entire framework depends on the reliability of the enhancer predictions. If the models are not consistently accurate across cell types, the downstream variant scoring and TF motif inference could be compromised. The discrepancy between AUROC and AUPRC needs explanation.
- **Resolution test** Provide per-cell-type performance metrics, describe the evaluation procedure in detail (including how positives and negatives were defined), report baseline performance (e.g., random classifier), and discuss the AUROC-AUPRC gap. Show that the models perform consistently well across all seven cell types.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that 1,537 variants (7.5%) were identified as candidate regulatory variants based on the top 10th percentile of |Δscore| distribution and the threshold of at least one allele exceeding the 10% FPR threshold.
- **Evidence pointer** Results section "Allele-specific TF convergence at breast cancer risk loci", Methods section "Allele-specific enhancer effect and motif inference"
- **Concern** The filtering criteria are described but the rationale for these specific thresholds is not provided. The text states that the 10th percentile threshold was selected based on maximization of approved drug enrichment, but this is described in the drug prioritization section, not for the variant filtering. It is unclear whether the variant filtering threshold was chosen a priori or based on the same optimization. The number of variants passing each filter step is not reported, making it difficult to assess whether the filtering is overly permissive or restrictive.
- **Why it matters** The variant filtering directly determines which variants are used for TF motif inference. If the thresholds are arbitrary or data-driven in a way that could introduce bias, the subsequent TF enrichment results could be affected. The lack of transparency in threshold selection undermines confidence in the robustness of the findings.
- **Resolution test** Clearly state whether the variant filtering thresholds were pre-specified or data-driven. Report the number of variants passing each filtering step. Provide sensitivity analyses showing how the results change with different thresholds. Justify the choice of the 10% FPR threshold for enhancer prediction.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The claim that the framework "establishes a computational link between noncoding genetic risk, TF-centered gene expression, and pharmacologically relevant candidate compounds" and that the prioritized compounds are "candidate therapeutics" for breast cancer.
- **Evidence pointer** Results sections "Drug candidate prioritization through FOXA1-centered transcriptional concordance" and "Prioritized compounds exhibit transcriptional signatures anti-correlated with breast cancer-associated pathways", Table 1
- **Concern** The manuscript does not provide any experimental validation of the prioritized compounds. The recovery of fulvestrant is presented as validation, but this is a single known positive control. The 54% anti-correlation across pathways is a computational metric that does not demonstrate actual therapeutic efficacy. The final shortlist of 8 compounds is presented without any discussion of their known mechanisms, potential off-target effects, or how they would be prioritized for experimental testing. The claim of "candidate therapeutics" is therefore premature.
- **Why it matters** The ultimate goal of drug repurposing is to identify compounds that can be tested in patients. Without experimental validation or at least a clear discussion of the limitations of computational predictions, the clinical relevance of the findings is overstated. The framework's utility for drug discovery cannot be assessed without evidence that the prioritized compounds have actual biological activity in relevant models.
- **Resolution test** Provide experimental validation of at least a subset of the prioritized compounds in relevant breast cancer cell lines or organoid models. Alternatively, clearly reframe the claims as "computational predictions requiring experimental validation" and discuss the limitations of the approach for identifying clinically actionable compounds.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that "FOXA1 perturbation affected the expression of 3,090 genes, of which 205 (6.6%) overlapped with tumor-associated differentially expressed genes (odds ratio = 1.18; p = 0.024)" and that "202 FOXA1-regulated genes overlapped with genes mapped to breast cancer GWAS loci."
- **Evidence pointer** Results section "Allele-specific TF convergence at breast cancer risk loci", Table S1
- **Concern** The overlap statistics are reported but the significance of these overlaps is not adequately contextualized. An odds ratio of 1.18 with p = 0.024 is a weak effect, and the biological significance of a 6.6% overlap is unclear without knowing the expected overlap by chance. The overlap with GWAS loci is reported without a statistical test. The text does not discuss whether these overlaps are specific to FOXA1 or would be observed with any TF.
- **Why it matters** These overlap analyses are used to support the relevance of FOXA1 to breast cancer. If the overlaps are not significantly greater than expected by chance, the claim that FOXA1 is a central mediator of breast cancer risk is weakened. The lack of appropriate statistical testing undermines the strength of this evidence.
- **Resolution test** Provide appropriate statistical tests for the overlap analyses (e.g., permutation-based tests that account for gene set sizes and genomic background). Report expected overlap by chance and effect sizes. Compare FOXA1 overlap to other TFs to demonstrate specificity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The claim that the framework "can be extended to other complex traits as matched epigenomic, perturbation, and drug transcriptional datasets become available."
- **Evidence pointer** Discussion section, Results section "Overview of the framework"
- **Concern** The generalizability claim is not supported by any demonstration beyond the breast cancer example. The manuscript mentions that seven cell lines were retained for analysis and that "significant heritability enrichment was observed for trait-cell line pairs consistent with known cell type identity," but no results from these other cell lines are presented. The framework's applicability to non-cancer traits is asserted but not demonstrated.
- **Why it matters** The broader impact of the framework depends on its generalizability. Without evidence that the approach works in other disease contexts, the claim of generalizability is speculative. The manuscript would be strengthened by showing at least one additional example of the framework applied to a different trait or cell type.
- **Resolution test** Provide results from at least one additional trait-cell line pair, or clearly state that the generalizability claim is a hypothesis that requires further testing. If additional results are not available, temper the language in the discussion and conclusions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Background section
- **Issue** The abstract and introduction use technical terms (e.g., "allele-specific enhancer prediction," "TF-centered gene expression changes," "attribution-based motif discovery") without sufficient explanation for readers outside computational biology. The significance of the approach and its novelty relative to existing methods could be clearer.
- **Required correction** Provide brief explanations of key technical concepts in the introduction and abstract. Consider adding a sentence that explicitly states what the framework does differently from existing approaches and why this matters for drug discovery.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "TF Knockdown concordance score"
- **Evidence pointer** Methods section
- **Issue** The concordance score formula is described as "Mean(z_up) - Mean(z_down)" but the text does not specify whether these are means across all genes in the respective sets or whether genes are weighted equally. The relationship to the connectivity score framework is mentioned but the adaptation is not fully explained.
- **Required correction** Clarify the exact computation of the concordance score, including how gene-level z-scores are aggregated and whether any weighting or normalization is applied. Provide a more explicit description of how the connectivity score framework was adapted.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Pathway-level anti-correlation analysis"
- **Evidence pointer** Methods section
- **Issue** The description of the anti-correlation analysis is brief. The text mentions "preranked GSEA" and "a signed disease direction vector" but does not explain how the direction vector is constructed or how the Spearman correlation is computed across genes within a pathway.
- **Required correction** Provide more detail on the construction of the disease direction vector and the exact procedure for computing the Spearman correlation. Clarify how pathway-level scores are aggregated across genes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Results section "Curated drug-gene interactions provide independent support for prioritized candidates"
- **Evidence pointer** Results section, Fig. 5
- **Issue** The text states that 13 of 63 compounds have documented interactions with FOXA1-regulated genes, but does not discuss the significance of this proportion. It is unclear whether 13/63 is higher than expected by chance.
- **Required correction** Provide a statistical test or at least a discussion of whether the proportion of compounds with documented interactions is significantly enriched compared to the full LINCS library.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations is brief and does not address the potential for confounding factors in the analysis, such as the choice of cell line, the quality of the GWAS data, or the assumptions of the deep learning model.
- **Required correction** Expand the limitations section to address these potential confounders and discuss how they might affect the interpretation of the results.

## Risk / unsupported claims
- The claim that the framework "establishes a computational link between noncoding genetic risk, TF-centered gene expression, and pharmacologically relevant candidate compounds" is not fully supported without experimental validation of the prioritized compounds.
- The claim of generalizability to other complex traits is not supported by data presented in the manuscript.
- The claim that the deep learning models "accurately distinguish active enhancers" is not fully supported without detailed evaluation metrics and baseline comparisons.
- The overlap statistics between FOXA1-regulated genes and tumor-associated genes or GWAS loci are reported without appropriate statistical testing.
- The selection of the 10th percentile threshold for drug prioritization is described as based on maximization of approved drug enrichment, but the details of this optimization are not provided, making it difficult to assess potential overfitting.
- The statement that "54% of prioritized compounds showed anti-correlated transcriptional effects across eight core breast cancer pathways" is presented as a validation, but the biological significance of this metric is not established.

## Assessment against Nature-style criteria
- **Originality** The framework is original in its integration of deep learning-based enhancer prediction with TF-centered transcriptional analysis for drug repurposing. This combination is not commonly found in the literature and represents a novel contribution.
- **Scientific importance** The problem addressed is important: linking noncoding genetic variation to therapeutic hypotheses is a major challenge in precision medicine. However, the current evidence does not fully establish the framework's utility, as it relies on computational predictions without experimental validation.
- **Interdisciplinary readership** The work bridges computational biology, genomics, and pharmacology, which could appeal to a broad audience. However, the technical complexity may limit accessibility for readers without a computational background.
- **Technical soundness** The methods are generally sound but have several gaps in detail and validation. The lack of per-cell-type performance metrics, the unclear threshold selection, and the absence of appropriate statistical tests for overlap analyses are significant concerns.
- **Readability for nonspecialists** The manuscript is written for a specialized audience and would benefit from clearer explanations of key concepts and the significance of the approach for a broader scientific readership.

## Recommendation posture
Supportive if technical concerns are resolved. The framework is conceptually interesting and addresses an important problem, but the current evidence does not fully support the claims made. The authors need to provide more detailed methods, appropriate statistical tests, and ideally some experimental validation or at least a clear discussion of the limitations of computational predictions. The generalizability claims should be tempered or supported with additional examples.