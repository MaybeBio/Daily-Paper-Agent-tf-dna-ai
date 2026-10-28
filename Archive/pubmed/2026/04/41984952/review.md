## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary materials list
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors develop a CNN-based cross-species prediction framework to identify human-specific open chromatin regions with increased accessibility (hPICAs) across 111 cell types, and demonstrate their functional relevance through TF binding site alterations and phenotypic associations
- **Visible evidence base** Main text figures referenced (Fig. 1-6), supplementary figures (fig. S1-S11), data files (data S1-S7), and detailed methods
- **Missing materials affecting confidence** Actual figures, supplementary data files, and code outputs were not provided; only text descriptions of results are available

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting approach to identifying human-specific regulatory regions by leveraging deep learning for cross-species prediction. The core idea, that CNNs trained on human chromatin accessibility data can predict accessibility in other primates and that prediction differences can identify evolutionarily relevant regions, is novel and potentially impactful. However, the evidence provided in the text is insufficient to fully evaluate the robustness of the claims. Several key analyses are described but not shown, and the statistical rigor of some comparisons is unclear. The manuscript would benefit from clearer presentation of validation metrics, effect sizes, and the biological significance of the identified regions beyond statistical enrichment.

- **Who would be interested in the results, and why** Evolutionary biologists studying human-specific traits, computational biologists developing deep learning methods for genomics, and researchers interested in regulatory genomics and noncoding variant interpretation. The approach offers a way to overcome the scarcity of nonhuman primate epigenomic data, which is a major limitation in the field.

- **Major strengths** The study addresses a significant problem, the limited availability of great ape epigenomic data, with a creative computational solution. The framework is generalizable and could be applied to other species and epigenetic features. The integration of multiple analyses, from cross-species prediction to TF binding site alterations to phenotypic associations, provides a comprehensive view. The use of ancestral sequence reconstruction to identify human-specific changes is methodologically sound.

- **Major Concerns** 
  - R1-M1: The claim that CNNs achieve "accurate predictions in other primates" is based on AUROC and AUPRC values, but the text does not provide sufficient context for what constitutes "accurate" in this imbalanced classification setting. The AUPRC values (0.232-0.478) are modest, and the baseline values are very low (0.004-0.008), which may inflate the perceived improvement.
  - R1-M2: The identification of hPICAs relies on a threshold of ΔPr > 0.3 with adjusted P < 0.05, but the rationale for this specific threshold is not justified. The sensitivity of the results to this choice is not explored.
  - R1-M3: The comparison between hPICAs and HARs is interesting but the overlap is described as "minimal" without providing quantitative data. The claim that hPICAs capture different information than HARs needs stronger support.
  - R1-M4: The functional validation is entirely computational. The two illustrative cases (GSK3B and LEP) are presented as evidence but lack experimental verification. The connection between predicted accessibility changes and actual gene expression changes is not demonstrated.
  - R1-M5: The positive selection analysis using the McDonald-Kreitman-like test is described but the statistical power and potential confounding factors, such as background selection or demographic history, are not discussed.

- **Minor Comments**
  - R1-m1: The abstract states "variants within hPICAs are more likely to affect chromatin accessibility by altering TF binding sites" but this is only shown for prioritized variants, not all variants in hPICAs.
  - R1-m2: The description of the regression model comparison is brief. The conclusion that the classification model is "more suitable" needs more detailed justification.
  - R1-m3: The methods for identifying cell type-specific TFs using WhichTF and predicting binding sites with FIMO are described, but the thresholds and quality controls are not fully specified.
  - R1-m4: The GWAS enrichment analysis uses European populations for both GWAS data and LD calculations, but the hPICAs are identified across diverse cell types. The potential population stratification issues are not addressed.
  - R1-m5: The statement that "hPICAs exhibited significantly higher cell type specificity" is supported by a Kolmogorov-Smirnov test, but the effect size and biological relevance of this difference are not quantified.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4

- **Assessment against Nature-style criteria** 
  - Originality: High. The application of cross-species deep learning prediction to identify human-specific regulatory regions is a novel contribution.
  - Scientific importance: Moderate to high. The approach could be widely used, but the biological insights are preliminary and require experimental validation.
  - Interdisciplinary readership: Moderate. The work bridges computational biology, evolutionary genomics, and regulatory biology, but the presentation is heavily computational.
  - Technical soundness: Moderate. The methods are generally appropriate, but several key validations and sensitivity analyses are missing.
  - Readability for nonspecialists: Moderate. The manuscript is clearly written but assumes familiarity with deep learning and genomics concepts.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the framework is potentially valuable, but the current evidence does not fully establish the claims. The authors should provide more detailed validation metrics, justify the threshold choices, and ideally include some experimental validation or at least stronger computational evidence for the functional relevance of hPICAs.

## Risk / unsupported claims
- The claim that CNNs "achieve accurate predictions in other primates" is not fully supported without more detailed performance metrics and comparison to baselines.
- The biological significance of hPICAs is inferred from statistical enrichments and computational predictions, but direct experimental evidence is lacking.
- The two case studies (GSK3B and LEP) are presented as illustrative but are not validated experimentally.
- The claim that hPICAs are under positive selection relies on a single analysis with potential confounding factors not addressed.
- The statement that hPICAs offer "a previously unexplored perspective for investigating human evolution" is somewhat overstated given the existing literature on comparative epigenomics.