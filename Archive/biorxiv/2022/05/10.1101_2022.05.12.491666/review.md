## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials provided
- **Shared manuscript claim summary** The authors propose a framework that uses CpG methylation data to score PWM-identified TF binding motif locations, report improved prediction of TF binding compared to standard PWM scores across most TFs in six cell lines, identify exceptions where TFs bind methylated promoter regions, and demonstrate generalizability to proximally measured methylation.
- **Visible evidence base** Abstract text only; no quantitative results, statistical details, or methodological descriptions
- **Missing materials affecting confidence** Full methods, all figures and tables, detailed results, cell line and TF lists, data processing pipelines, and validation procedures

## Reviewer
- **Overall assessment** The abstract presents a potentially useful concept for integrating epigenetic context into TF binding prediction, but the evidence base is too limited to evaluate the validity, robustness, or generalizability of the claims. The central assertion that methylation-based scoring outperforms PWM scores lacks quantitative support, and the reported exceptions and generalizability are not substantiated with specific data. The work may interest computational biologists and epigenetics researchers, but the current abstract does not establish the case.
- **Who would be interested in the results, and why** Computational biologists studying TF binding prediction, epigenetics researchers investigating methylation's role in gene regulation, and bioinformaticians developing integrative models for regulatory genomics. The approach could inform methods for context-specific binding inference, which is relevant to understanding gene regulatory networks in development and disease.
- **Major strengths** The concept of incorporating methylation data into PWM-based scoring is a logical and potentially impactful extension of existing methods. The abstract addresses a recognized limitation of PWM scores, namely the lack of epigenetic context. The proposed generalizability to proximally measured CpGs is a practical consideration that could enhance applicability.
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
- **Assessment against Nature-style criteria**  
  - Originality: The idea of using methylation to score motif locations is not entirely novel, as methylation-TF interactions have been studied, but the specific framework may offer a new angle. However, originality cannot be fully assessed without methods and comparison to prior work.  
  - Scientific importance: If validated, the approach could improve TF binding prediction, which is important for regulatory genomics. The abstract suggests context-specific effects, which could have broad implications, but the importance is not yet demonstrated.  
  - Interdisciplinary readership: The topic bridges computational biology and epigenetics, potentially appealing to a broad audience, but the abstract lacks the detail needed to engage nonspecialists.  
  - Technical soundness: Not assessable from the abstract; no statistical or methodological details are provided.  
  - Readability for nonspecialists: The abstract is generally clear but uses field-specific terms without sufficient context, and the lack of quantitative results reduces accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but requires full manuscript review to determine if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "for most TFs, binding is better predicted using methylation-based scoring compared to standard PWM scores"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract claims improved prediction for most TFs but provides no quantitative metrics, such as AUC, correlation, or enrichment scores, nor any statistical significance tests. No comparison details are given, such as the number of TFs tested, the magnitude of improvement, or the variability across cell lines.  
- **Why it matters** Without quantitative evidence, the central claim cannot be evaluated for validity or practical significance. The reader cannot determine whether the improvement is marginal or substantial, or whether it is consistent across conditions.  
- **Resolution test** Provide specific performance metrics (e.g., AUC or precision-recall) for methylation-based scoring versus PWM scores, with confidence intervals or statistical tests, for each TF and cell line.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity  
- **Claim pointer** "we developed a framework to score inferred TF binding locations using CpG methylation data"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not describe how methylation data are integrated into the scoring framework. It is unclear whether the method uses binary methylation status, continuous beta values, or a probabilistic model, and how motif scores are combined with methylation information.  
- **Why it matters** Reproducibility and assessment of the method's novelty depend on a clear description of the scoring algorithm. Without this, the framework cannot be evaluated or compared to existing approaches.  
- **Resolution test** Detail the scoring function, including how methylation values are normalized, weighted, and combined with PWM scores, and provide a step-by-step description in the methods.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Generalizability support  
- **Claim pointer** "our approach can be generalized to infer TF binding when methylation information is only proximally available"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The claim of generalizability to proximally measured CpGs is stated without any supporting data. No results are shown for this scenario, and it is unclear how the method handles distance, linkage, or imputation of methylation status.  
- **Why it matters** This claim extends the method's utility, but without evidence, it remains speculative. If the method fails for proximal CpGs, the practical applicability is reduced.  
- **Resolution test** Present results comparing direct overlap versus proximal CpG scoring, including performance metrics and a description of how proximal CpGs are selected and weighted.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Context specificity  
- **Claim pointer** "the role of methylation in TF binding may be cell-type and context specific"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract mentions exceptions where TFs bind methylated promoter regions but does not specify which TFs, cell lines, or genomic contexts show this behavior. No data are provided to support the claim of context specificity.  
- **Why it matters** The claim of context specificity is a key insight, but without specific examples and supporting data, it cannot be verified. This limits the interpretation of the findings.  
- **Resolution test** List the TFs and cell lines that show binding to methylated regions, and provide statistical evidence for the context-specific patterns, such as enrichment analyses or interaction tests.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** "six cell lines"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not name the cell lines or specify their tissue types, which is relevant for interpreting context specificity.  
- **Required correction** List the six cell lines and their origins in the abstract or methods.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "proximally available"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "proximally available" is vague and could be misinterpreted. It is unclear what distance threshold or genomic relationship defines "proximal."  
- **Required correction** Define the distance or genomic feature used to classify proximal CpGs, and provide a concrete example.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** "compared with experimental data characterizing TF binding (ChIP-seq)"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not specify the number of ChIP-seq datasets, the TFs covered, or the quality controls used for comparison.  
- **Required correction** Provide details on the ChIP-seq datasets, including TF identities, cell line matches, and any filtering criteria.

## Risk / unsupported claims
- The claim that methylation-based scoring improves TF binding prediction for most TFs is unsupported due to lack of quantitative results.
- The claim of generalizability to proximally measured CpGs is unsupported as no data are presented.
- The claim of cell-type and context-specific exceptions is unsupported without specific examples or statistical evidence.
- The overall framework's validity and novelty cannot be assessed without methodological details.