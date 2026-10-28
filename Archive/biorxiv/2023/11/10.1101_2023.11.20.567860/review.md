## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary table description
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors systematically evaluate six markers of active regulatory elements for their ability to identify functional non-coding genetic variants, benchmarking against molecular QTL datasets. They report that the combination of DNase footprints and enhancer RNA provides high precision for prioritising functional variants from GWAS, and present this as a framework called FINDER.
- **Visible evidence base** Abstract, Introduction, Results sections (partial), Discussion, Methods, Figure legends referenced in text (Figures 1-7, Supplemental Figures 1-4), Supplementary Table 1 description
- **Missing materials affecting confidence** Full figure panels and legends, Supplementary Tables 1-3 data content, detailed statistical outputs, complete methods for all analyses, exact numbers for precision/recall calculations, and the full set of results not shown in the provided text

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in human genetics, namely the prioritisation of functional non-coding variants from GWAS. The authors present a systematic comparison of six regulatory markers and identify a combination of DNase footprints and eRNA as high-precision predictors. The central claim is potentially valuable, but the evidence as presented is incomplete in several respects. The precision values reported are modest in absolute terms, and the manuscript would benefit from clearer presentation of the benchmarking strategy, additional validation, and a more thorough discussion of limitations. The work is relevant to a broad audience in functional genomics and statistical genetics, but the current version does not fully establish the case for the FINDER framework as a generalisable tool.
- **Who would be interested in the results, and why** Statistical geneticists and bioinformaticians developing variant prioritisation tools would be interested in the benchmarking of regulatory markers. Experimental biologists studying gene regulation would find the emphasis on DNase footprints and eRNA mechanistically informative. Clinically oriented researchers using GWAS for disease gene discovery would value any improvement in narrowing candidate variant lists. The work is also relevant to those developing fine-mapping and polygenic risk score methodologies.
- **Major strengths** The study addresses a well-recognised bottleneck in post-GWAS interpretation. The use of multiple independent molQTL benchmarks is a sensible design choice. The systematic comparison of six markers across a large number of datasets is a substantial undertaking. The application to a real GWAS trait (leukocyte count) and an LD-based example (asthma) demonstrates practical utility. The random forest analysis provides an independent line of evidence supporting the main conclusion.
- **Major Concerns** The absolute precision values are low, raising questions about practical utility. The benchmarking strategy conflates cell-type-specific effects by merging all biosources. The recall is acknowledged to be low, but the trade-off is not quantified in a way that allows comparison with existing tools. The manuscript does not compare FINDER against existing computational prediction methods. The validation using Mendelian disease variants is limited by small numbers and potential ascertainment bias. The asthma example is a single case and does not establish generalisability.
- **Minor Comments** The writing is generally clear but some methodological details are missing. The figures are referenced but not fully described in the text provided. The choice of Z-score normalisation for precision values needs justification. The random forest model performance (predictive value 0.64) is modest and should be discussed. The statement that eRNA has not been used in variant prediction should be checked against the literature.
- **Technical failings that need to be addressed before the case is established** The lack of comparison with existing tools, the absence of a clear statement of the number of variants in each benchmark set, and the incomplete description of the random forest feature engineering are the most significant technical gaps.
- **Assessment against Nature-style criteria** Originality: The combination of DNase footprints and eRNA as a prioritisation signature is novel, although individual markers have been studied before. Scientific importance: The problem is important, and the findings could inform variant prioritisation, but the modest precision and lack of comparison with existing methods limit the immediate impact. Interdisciplinary readership: The work bridges statistical genetics, functional genomics, and computational biology, and would appeal to readers across these fields. Technical soundness: The overall approach is reasonable, but several technical details are missing and the benchmarking strategy has limitations that need to be addressed. Readability for nonspecialists: The manuscript is largely accessible, but the methods section assumes familiarity with genomic terminology and the results section would benefit from clearer explanations of the precision calculations.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the data appear to support the main conclusion, but the manuscript requires additional analyses and clearer presentation before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the combination of DNase footprints and eRNA provides high precision for identifying functional non-coding variants, and present this as a framework called FINDER.
- **Evidence pointer** Results section, Figures 3A and 3B, location not provided
- **Concern** The precision values reported are low in absolute terms. The range of precision values across molQTL benchmarks is 7.5-55.46% for bQTL, 0.42-3.53% for raQTL, and 4.02-27.7% for caQTL. Even the best combination achieves a precision of approximately 55% for bQTL, meaning that nearly half of the prioritised variants are false positives. The fold change over random SNVs for the DNase footprints and eRNA combination is 13.89, which is impressive relative to other markers, but the absolute precision remains modest.
- **Why it matters** The central claim of the manuscript is that FINDER provides high precision for prioritising functional variants. If the absolute precision is low, the practical utility of the framework for narrowing candidate variant lists is limited. Users of the framework would still need to validate a large number of variants experimentally. The claim of high precision needs to be contextualised with respect to the prior probability of a variant being functional and the expected precision of alternative approaches.
- **Resolution test** The authors should report the absolute numbers of true positives, false positives, true negatives, and false negatives for each marker combination and each molQTL benchmark. They should also compare the precision of FINDER with existing variant prioritisation tools, such as CADD, Eigen, or LINSIGHT, using the same benchmark sets. If the absolute precision remains low, the authors should temper their claim of high precision and instead emphasise the relative improvement over other markers.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigour
- **Claim pointer** The authors state that they took a cell-type agnostic approach by merging all biosources for each marker, which overcomes the issue that the cell-type in which a variant is functional is not known a priori.
- **Evidence pointer** Results section, "Prioritisation of genetic variants by combinations of regulatory markers", location not provided
- **Concern** The cell-type agnostic approach, while pragmatic, may obscure important biological signal. Functional non-coding variants often act in a cell-type-specific manner, and merging all biosources could dilute the signal from the relevant cell type. The authors acknowledge this in the Discussion but do not provide an analysis that addresses the potential loss of information. The claim that the approach overcomes the issue of unknown cell-type is only partially true; it avoids the need to specify a cell type, but it does not ensure that the relevant cell type is represented in the merged data.
- **Why it matters** If the goal is to prioritise functional variants for a specific trait, the relevant cell type is often known or can be inferred. A cell-type-agnostic approach may miss variants that are functional only in a specific cell type. The authors demonstrate cell-type enrichment for the leukocyte count trait, but this is a post hoc analysis and does not validate the approach for traits where the relevant cell type is less clear. The framework should be tested in a scenario where the relevant cell type is known and compared against a cell-type-specific analysis.
- **Resolution test** The authors should perform a cell-type-specific analysis for at least one trait where the relevant cell type is well established, and compare the precision of variants prioritised using cell-type-specific markers versus the merged markers. If the cell-type-specific approach yields higher precision, the authors should acknowledge this limitation and provide guidance on when the cell-type-agnostic approach is appropriate.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** External validity
- **Claim pointer** The authors validate their findings using a set of 210 curated non-coding variants associated with Mendelian diseases, and report that the combination of DNase footprints and eRNA shows the highest precision at 0.65 with low recall of 0.25.
- **Evidence pointer** Results section, "Replication with functional, rare, non-coding Mendelian disease-associated variants", Figure 4D, location not provided
- **Concern** The validation set of 210 Mendelian disease variants is small, and the precision of 0.65 is based on a spike-in of approximately 4,000 random variants, giving a true positive rate of approximately 0.05. The confidence intervals around the precision estimate are likely to be wide given the small number of true positives. Additionally, Mendelian disease variants may not be representative of common complex trait variants, as they are often more penetrant and may be enriched for stronger regulatory effects. The authors do not report the number of true positives in this validation, which makes it difficult to assess the reliability of the precision estimate.
- **Why it matters** The validation using Mendelian disease variants is the only independent replication of the FINDER framework. If the precision estimate is unreliable or the variants are not representative, the generalisability of the framework to common complex traits is not established. The authors should provide confidence intervals for the precision and recall estimates and discuss the potential differences between Mendelian and complex trait variants.
- **Resolution test** The authors should report the number of true positives and the confidence intervals for the precision and recall estimates. They should also consider validating the framework using a larger set of experimentally validated functional variants, such as those from massively parallel reporter assays or CRISPR screens, if such data are available.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparative evaluation
- **Claim pointer** The authors state that computational models to predict functional non-coding variants poorly predict effects for common variants, and imply that FINDER offers an improvement.
- **Evidence pointer** Introduction, Discussion, location not provided
- **Concern** The manuscript does not include a direct comparison of FINDER with existing computational prediction methods. The authors mention that current approaches poorly predict functional variants, but they do not benchmark FINDER against any of these methods. Without such a comparison, it is difficult to assess whether FINDER offers a meaningful improvement over the state of the art. The random forest analysis provides an internal comparison of the six markers, but this does not address the external validity of the framework.
- **Why it matters** The claim that FINDER improves upon existing methods is central to the manuscript's contribution. If existing tools perform similarly or better, the novelty of the framework is diminished. A direct comparison would also help users decide which tool to use for their specific application.
- **Resolution test** The authors should compare FINDER with at least two or three existing variant prioritisation tools, such as CADD, Eigen, LINSIGHT, or FunSeq2, using the same benchmark sets and evaluation metrics. The comparison should include precision-recall curves or similar metrics to allow a fair assessment.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors describe the FINDER framework and state that the merged datasets can be found at a GitHub repository.
- **Evidence pointer** Methods, Data Availability, location not provided
- **Concern** The methods section does not provide sufficient detail for the FINDER framework to be reproduced. The description of the random forest model is brief, and the exact features used, hyperparameters, and evaluation procedure are not fully specified. The GitHub repository is mentioned but its contents are not described. The authors also do not provide a clear statement of the computational resources required to run the framework.
- **Why it matters** Reproducibility is a core requirement for computational tools. If the framework cannot be reproduced from the manuscript alone, its utility is limited. The authors should provide a detailed description of the framework, including all parameters and settings, and ensure that the GitHub repository contains the necessary code and documentation.
- **Resolution test** The authors should expand the methods section to include a full description of the FINDER framework, including the random forest model, feature engineering, and evaluation procedure. They should also provide a link to the GitHub repository and describe its contents, including any code, data, and documentation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the framework is called FINDER but does not expand the acronym. This may be confusing for readers who are not familiar with the manuscript.
- **Required correction** Expand the acronym in the abstract, for example, "FINDER (Functional SNV IdeNtification using DNase footprints and Enhancer RNA)".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, precision calculations
- **Evidence pointer** Results section, "Prioritisation of genetic variants by combinations of regulatory markers", location not provided
- **Issue** The precision values are reported as ranges, but the number of variants in each benchmark set is not stated. This makes it difficult to assess the reliability of the estimates.
- **Required correction** Report the number of variants in each benchmark set and the number of true positives for each marker combination.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction, location not provided
- **Issue** The statement that eRNA has not been used in the prediction of functional genetic variants may be too strong. There may be prior work using eRNA or related features for variant prioritisation.
- **Required correction** Soften the statement and cite any relevant prior work, or clarify that the combination of DNase footprints and eRNA is novel.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure presentation
- **Affected element** Figure 3
- **Evidence pointer** Results section, Figure 3, location not provided
- **Issue** The heatmap in Figure 3A is described as showing Z-scores of precision values, but the colour scale and clustering method are not described in the text.
- **Required correction** Add a description of the colour scale and clustering method in the figure legend or the main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results, "Centrality in open chromatin"
- **Evidence pointer** Results section, location not provided
- **Issue** The term "centrality" is used to describe the position of variants relative to DHS summits, but this term is not defined. It may be confused with network centrality measures.
- **Required correction** Define the term clearly, for example, "distance from the DHS summit" or "position relative to the DHS summit".

## Risk / unsupported claims
- The claim that the combination of DNase footprints and eRNA provides "high precision" is not fully supported by the absolute precision values reported, which are modest in several benchmark sets.
- The claim that eRNA has not been used in the prediction of functional genetic variants is not supported by a literature search and may be inaccurate.
- The generalisability of the FINDER framework to all complex traits is not established, as the validation is limited to one trait (leukocyte count) and one LD-based example (asthma).
- The statement that ATAC-seq and H3K27ac are "poor predictors" is based on the authors' benchmarking, but the comparison is not made against existing computational tools, so the relative performance is unclear.
- The manuscript does not provide a quantitative assessment of the trade-off between precision and recall, making it difficult to evaluate the practical utility of the framework.