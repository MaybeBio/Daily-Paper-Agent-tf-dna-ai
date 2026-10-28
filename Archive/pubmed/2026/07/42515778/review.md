## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and conclusions
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and interpretation of results as presented in the manuscript
- **Shared manuscript claim summary** The authors present an integrative deep learning framework that links allele-specific enhancer prediction to drug repurposing candidates through two complementary strategies (TF-based and gene-based), using MCF7 breast cancer as a proof-of-concept. They report recovery of approved breast cancer therapeutics and propose 15 high-confidence repurposing candidates.
- **Visible evidence base** Full text with figures referenced (Figure 1, 2, 3, 4, S1-S4), tables (Table 1, S1-S11), and methods section
- **Missing materials affecting confidence** No code availability statement, no data availability statement, no supplementary figures or tables provided for direct inspection, no hyperparameter details for TREDNet fine-tuning, no details on LINSC dataset versioning or processing pipeline

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting integration of deep learning-based enhancer prediction with drug repurposing strategies. The core idea of using allele-specific regulatory predictions to guide therapeutic prioritization is timely and potentially valuable. However, the manuscript has several significant methodological gaps and overstatements that need to be addressed. The validation is largely computational and self-referential, with limited independent benchmarking. The claim of "recovery" of known drugs is presented as validation but lacks a formal statistical framework to assess whether this recovery rate exceeds chance. The pathway anti-correlation analysis is described as complementary but the authors acknowledge it is not independent validation. The manuscript would benefit from clearer articulation of what is genuinely novel versus what is an application of existing tools, and from more rigorous statistical controls throughout.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics and drug repurposing would be the primary audience. Researchers interested in integrating GWAS data with functional genomics for therapeutic discovery would find the framework relevant. The work may also interest pharmaceutical scientists exploring computational approaches to drug repurposing, though the lack of experimental validation limits immediate translational appeal.

- **Major strengths** 
  1. The conceptual framework of linking noncoding variant effects to drug prioritization is novel and addresses a genuine gap in the field
  2. The two complementary strategies (TF-based and gene-based) provide methodological diversity
  3. The use of allele-specific enhancer prediction rather than simple proximity or eQTL approaches is more mechanistically grounded
  4. The recovery of known breast cancer drugs (fulvestrant, toremifene, raloxifene) provides face validity
  5. The sensitivity analysis for the |Δscore| threshold is a good practice

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that recovery of approved breast cancer therapeutics "supports the biological relevance of deep learning-predicted regulatory variants" and that the framework "establishes a regulatory variant-guided drug repurposing framework."
- **Evidence pointer** Section 2.4, Section 2.5, Section 3
- **Concern** The recovery of known drugs is presented as validation, but there is no formal statistical framework to assess whether this recovery rate exceeds what would be expected by chance. The authors do not report the total number of drugs in the LINSC L1000 library that have breast cancer indications, nor do they compute enrichment statistics for known drug recovery against a null expectation. Without this, the "recovery" could be coincidental given the large number of compounds screened.
- **Why it matters** The central claim of biological validity rests on this recovery. Without a statistical framework, the reader cannot assess whether the method has genuine predictive power or whether the recovery is within the range expected from screening thousands of compounds.
- **Resolution test** Provide a formal enrichment analysis comparing the recovery rate of approved breast cancer drugs in the prioritized set versus the background LINSC library, with appropriate statistical testing (e.g., Fisher's exact test with the full contingency table, or permutation-based null distributions).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that "TREDNet achieved stronger performance for enhancer variant-effect prediction across multiple datasets" and use this as justification for model selection.
- **Evidence pointer** Section 1, Section 4.2
- **Concern** The comparative analysis supporting TREDNet selection is referenced as "previous comparative analyses from our group" but no data, figures, or statistical comparisons are provided in this manuscript. The reader cannot evaluate whether TREDNet is indeed the most appropriate model. Additionally, no comparison is made against alternative approaches for allele-specific effect prediction (e.g., Enformer, Borzoi) within the specific context of this study.
- **Why it matters** Model selection is foundational to the entire framework. If TREDNet is not the optimal choice, the downstream results may be compromised. The lack of transparency prevents independent assessment.
- **Resolution test** Provide the comparative analysis data as supplementary material, or include a benchmark comparison of TREDNet against at least one alternative model (e.g., Enformer) for the specific task of allele-specific enhancer prediction in this context.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation and benchmarking
- **Claim pointer** The authors state that "Both strategies identified compounds with anti-correlated transcriptional signatures across core breast cancer hallmark pathways" and that this supports the prioritization.
- **Evidence pointer** Section 2.6, Figure 4
- **Concern** The pathway anti-correlation analysis is performed on the same LINSC data used for prioritization, creating a potential circularity. The authors acknowledge this in Section 4.8 but still present it as supporting evidence. There is no independent validation using external datasets (e.g., patient-derived expression data, independent drug response databases like GDSC or CTRP). The claim that 54% of prioritized compounds show positive anti-correlation across all eight pathways is not compared against a null distribution of randomly selected compounds.
- **Why it matters** Without external validation or appropriate null comparisons, the pathway analysis does not provide independent support for the prioritization. The circularity weakens the evidential value of this analysis.
- **Resolution test** Validate the prioritized compounds against an independent drug response or expression dataset, or at minimum provide a permutation-based null distribution showing that the observed anti-correlation enrichment is significantly greater than expected by chance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and biological plausibility
- **Claim pointer** The authors state that "FOXA1-associated motif features were strongly enriched in risk alleles" and interpret this as evidence of FOXA1's central role in breast cancer regulatory biology.
- **Evidence pointer** Section 2.3, Figure S2
- **Concern** The interpretation of motif enrichment as evidence of FOXA1's functional importance requires more careful consideration. FOXA1 is a well-known pioneer factor in breast cancer, and its motifs are ubiquitous in enhancer regions. The enrichment could reflect the baseline frequency of FOXA1 motifs in enhancers rather than a specific disease-relevant mechanism. The authors do not compare against a null expectation of motif frequency in non-risk enhancers or account for motif redundancy across the 32 identified TF classes.
- **Why it matters** The biological interpretation drives the TF-based prioritization strategy. If the FOXA1 enrichment is not specifically disease-relevant, the prioritization may be biased toward compounds that modulate FOXA1-related pathways for reasons unrelated to the specific genetic variants.
- **Resolution test** Provide a control analysis showing that FOXA1 motif enrichment is specific to risk alleles compared to matched control variants, and demonstrate that the enrichment is not simply a reflection of general enhancer motif composition.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors describe a multi-step computational pipeline involving TREDNet, DeepLIFT, TF-MoDISco, LINSC, KnockTF, and DGIdb.
- **Evidence pointer** Section 4
- **Concern** No code availability statement is provided, and no version numbers or specific processing details are given for several key tools (e.g., TREDNet version, LINSC data processing pipeline, exact parameters for TF-MoDISco). The manuscript states "TREDNet v0.1" but provides no link to code or documentation. The LINSC data processing is described as "obtained from the Broad Institute LINSC Project" without details on normalization or quality control.
- **Why it matters** Reproducibility is a core requirement for computational biology manuscripts. Without code and detailed parameters, independent researchers cannot replicate or build upon this work.
- **Resolution test** Provide a code repository (e.g., GitHub) with all analysis scripts, a detailed data processing pipeline, and version numbers for all software dependencies.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3, Figure S2C
- **Issue** The statement that risk alleles are "associated with both increases and decreases in enhancer prediction score" is presented without quantification. The distribution of positive versus negative Δscore values is not described.
- **Required correction** Provide the proportion of risk alleles with positive versus negative Δscore values, and discuss whether this balance is expected given the model architecture.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2, Figure S1C
- **Issue** The heritability enrichment analysis reports a single p-value for the MCF7-breast cancer pair but does not report the number of trait-cell line pairs tested or whether multiple testing correction was applied.
- **Required correction** Report the total number of trait-cell line pairs tested and the multiple testing correction method used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5, Table S6
- **Issue** The gene-based prioritization uses proximity-based mapping (two nearest genes within 1000 kb). This is acknowledged as a limitation, but the potential impact on results is not discussed. Many enhancer-promoter interactions span greater distances or skip nearest genes.
- **Required correction** Discuss the potential bias introduced by proximity-based mapping and consider whether alternative approaches (e.g., Hi-C-based mapping) would substantially alter the results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 2.4, Figure 3
- **Evidence pointer** Section 2.4, Figure 3B
- **Issue** The ranking of compounds by concordance score is presented, but the figure does not clearly show the distribution of scores across all 6605 compounds, making it difficult to assess where the prioritized compounds fall relative to the full distribution.
- **Required correction** Include a density plot or histogram showing the full distribution of concordance scores with the prioritized compounds highlighted.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.7, Table 1
- **Evidence pointer** Section 2.7, Table 1
- **Issue** The final list of 15 high-confidence candidates is presented in Table 1, but the criteria for inclusion in this final list are not fully specified. The text mentions "literature reported evidence" but does not define what constitutes sufficient evidence.
- **Required correction** Provide explicit inclusion criteria for the final 15 candidates, including how literature evidence was assessed and weighted.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Section 2.6
- **Evidence pointer** Section 2.6, Figure 4
- **Issue** The phrase "anti-correlated transcriptional signatures" is used repeatedly but the directionality of the anti-correlation is not always clear. For some pathways, anti-correlation might mean suppression of oncogenic programs, while for others it might mean activation of tumor-suppressive programs.
- **Required correction** Clarify the interpretation of anti-correlation for each pathway and whether the directionality is consistent with therapeutic benefit.

## Risk / unsupported claims
- The claim that recovery of approved breast cancer drugs "supports the biological relevance" of the framework is not statistically substantiated without a formal enrichment analysis against chance expectation
- The claim that TREDNet is the optimal model for this task is unsupported by data presented in this manuscript
- The pathway anti-correlation analysis is presented as supporting evidence but is acknowledged by the authors to be non-independent, limiting its evidential value
- The biological interpretation of FOXA1 motif enrichment as disease-relevant is not adequately controlled for baseline motif frequency in enhancer regions
- The generalizability of the framework to other disease contexts is stated as a strength but is not demonstrated beyond the MCF7 breast cancer proof-of-concept
- The 15 high-confidence candidates are presented as having "translational relevance" but no experimental validation is provided, and the criteria for this designation are not fully transparent