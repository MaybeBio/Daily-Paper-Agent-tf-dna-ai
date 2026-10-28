## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors report genotyping of three prioritized variants in a small case-control sample from the Azeri population of Iran, with two variants showing significant association with type 2 diabetes and supporting in-silico structural and dynamic evidence, while a third variant shows no association and only subtle in-silico effects.
- **Visible evidence base** Abstract text only; includes reported odds ratios, p-values, variant identifiers, gene names, and qualitative descriptions of molecular dynamics outcomes
- **Missing materials affecting confidence** Full methods, genotyping quality control details, population stratification assessment, multiple testing correction, structural model validation, docking protocols, simulation convergence criteria, and all figures and tables

## Reviewer

- **Overall assessment** The abstract presents a plausible integrative approach combining genetic association with computational structural analysis. However, the evidence as presented is insufficient to establish the claimed associations as robust or the mechanistic interpretations as well-supported. The small sample size, lack of multiple testing correction, and absence of methodological details limit confidence. The work may be of interest to researchers in T2D genetics and computational biology, but the current abstract does not provide enough information to assess technical soundness or reproducibility.
- **Who would be interested in the results, and why** Researchers studying genetic susceptibility to type 2 diabetes, particularly those focused on regulatory variants and zinc transporter biology, may find the candidate variants worth pursuing. Computational biologists interested in integrating molecular dynamics with population genetics could also find the approach relevant, though the preliminary nature of the findings limits immediate utility.
- **Major strengths** The study combines genetic association with mechanistic in-silico analysis, which is a useful strategy for prioritizing variants. The inclusion of Sanger sequencing validation for variant calls is a positive quality control step. The identification of a regulatory variant in PPP2R3A with a plausible transcription factor binding context adds biological interest.
- **Major Concerns** The concerns below identify critical limitations in statistical rigor, sample size, and evidence integration that must be addressed before the claims can be considered established.
- **Minor Comments** Several reporting and interpretive issues should be corrected to improve clarity and avoid overstatement.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate; the combination of genotyping and molecular dynamics is not novel but is applied to understudied variants. Scientific importance is limited by the small, single-population sample and lack of replication. Interdisciplinary readership is possible but not strongly supported given the preliminary nature. Technical soundness cannot be fully assessed from the abstract, but several statistical concerns are evident. Readability for nonspecialists is adequate, though some terms such as "RegulomeDB 2a" and "RMSD/RMSF" are used without explanation.
- **Recommendation posture** Currently not established from the provided evidence. The abstract reports promising signals, but the statistical and methodological limitations are substantial. A revised manuscript with full methods, corrected analyses, and appropriate caveats could be reconsidered.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** The abstract claims significant association for PPP2R3A rs184442184 (allelic OR approximately 1.71, p = 0.014; TT OR approximately 2.92, p = 0.020) and SLC39A11 rs61736066 (allelic OR approximately 1.87, p = 0.002; AA OR approximately 3.49, p = 0.005).
- **Evidence pointer** Abstract Results section
- **Concern** The reported p-values do not appear to account for multiple testing. Three variants were tested, and for each variant multiple genetic models (allelic, genotypic, and possibly others) were evaluated. The abstract does not state whether any correction was applied. With 101 cases and 100 controls, the effective sample size is small, and the reported effect sizes are large, which raises the possibility of winner's curse or type I error inflation.
- **Why it matters** Without multiple testing correction, the probability that at least one of the reported associations is a false positive is substantial. The small sample size further increases the risk of unstable effect estimates. The claims of association cannot be considered reliable without addressing this issue.
- **Resolution test** Provide adjusted p-values using an appropriate method (e.g., Bonferroni or false discovery rate) across all variants and models tested. Report confidence intervals for all odds ratios. If corrections are not applied, justify their omission explicitly and interpret results as exploratory.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Population genetics and confounding
- **Claim pointer** The abstract states that genotyping was performed in 101 T2D cases and 100 controls from the Azeri population of Iran, and implies that the observed associations are attributable to the tested variants.
- **Evidence pointer** Abstract Methods and Results sections
- **Concern** The abstract provides no information on population stratification, which is a well-known confounder in case-control genetic association studies, particularly in populations with complex admixture history. There is no mention of principal component analysis, genomic control, or any other adjustment for ancestry. Additionally, no information is given on matching of cases and controls for age, sex, or body mass index, which are relevant for T2D.
- **Why it matters** Unadjusted population stratification can produce spurious associations, especially with small sample sizes. If cases and controls differ in ancestry or key covariates, the reported odds ratios may reflect confounding rather than true variant effects.
- **Resolution test** Report the results of population stratification assessment (e.g., principal component analysis) and any adjustments made. Provide demographic and clinical characteristics of cases and controls, and state whether analyses were adjusted for relevant covariates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence integration and causal inference
- **Claim pointer** The abstract concludes that PPP2R3A rs184442184 and SLC39A11 rs61736066 are "promising T2D candidate variants, supported by concordant genetic signals and mechanistic in-silico effects."
- **Evidence pointer** Abstract Results and Conclusion sections
- **Concern** The abstract does not establish a direct mechanistic link between the in-silico findings and the genetic association. For PPP2R3A, the variant is located at a transcription factor binding site, but no functional validation is provided to show that the variant alters binding or gene expression. For SLC39A11, the molecular dynamics results are described qualitatively (increased RMSD/RMSF, helix displacement, modest destabilization), but the abstract does not state whether these changes are predicted to affect protein function in a way that would influence T2D risk. The concordance between genetic and in-silico evidence is asserted rather than demonstrated.
- **Why it matters** The conclusion of "promising candidates" relies on the assumption that the in-silico effects are biologically meaningful and related to the disease mechanism. Without functional validation or a clear mechanistic model, the in-silico results are speculative and do not strengthen the genetic association.
- **Resolution test** Provide a clear mechanistic hypothesis linking each variant to T2D pathophysiology, supported by quantitative in-silico results (e.g., binding affinity changes, free energy calculations) and, ideally, preliminary functional data (e.g., reporter assays, expression analysis). If functional data are not available, state this limitation explicitly and temper the conclusions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and methodological transparency
- **Claim pointer** The abstract describes structural modelling, ligand docking, and 100-nanosecond molecular dynamics simulations as part of the methods.
- **Evidence pointer** Abstract Methods section
- **Concern** The abstract provides no details on the software, force fields, model validation, or simulation convergence criteria used for the in-silico analyses. For molecular dynamics, 100 nanoseconds is a relatively short timescale, and the abstract does not report whether simulations reached equilibrium or whether multiple replicates were performed. Docking results are not described quantitatively. Without these details, the in-silico findings cannot be reproduced or independently evaluated.
- **Why it matters** Reproducibility is a core requirement for scientific claims. The lack of methodological detail prevents assessment of whether the in-silico results are robust or artifacts of the chosen parameters.
- **Resolution test** Provide full methodological details in the manuscript, including software versions, force fields, validation metrics, simulation convergence analysis, and replicate information. Report quantitative docking scores and simulation statistics.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reporting clarity
- **Affected element** Abstract Results section
- **Evidence pointer** Abstract Results section
- **Issue** The abstract uses "approximately" for odds ratios and p-values, which is unusual for statistical results. Exact values should be reported.
- **Required correction** Report exact odds ratios, confidence intervals, and p-values to the appropriate precision.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract Background section
- **Evidence pointer** Abstract Background section
- **Issue** The term "TF-binding-site" is used without specifying the transcription factor or the evidence for the binding site. The later mention of "EGR1/SP motifs" is helpful but should be introduced earlier.
- **Required correction** Define the variant type and the relevant transcription factor context in the Background or Methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretive caution
- **Affected element** Abstract Conclusion section
- **Evidence pointer** Abstract Conclusion section
- **Issue** The conclusion states that the results "provide testable biological hypotheses," which is appropriate, but the preceding sentence calls the variants "promising T2D candidate variants," which overstates the evidence given the limitations.
- **Required correction** Soften the language to reflect the exploratory nature of the findings, such as "warrant further investigation."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract Methods section
- **Evidence pointer** Abstract Methods section
- **Issue** The abstract does not state how the three variants were prioritized from the initial two-group comparative genotyping. This is a key step in the study design.
- **Required correction** Briefly describe the prioritization criteria in the Methods section.

## Risk / unsupported claims

- The claim that PPP2R3A rs184442184 and SLC39A11 rs61736066 are "promising T2D candidate variants" is unsupported due to lack of multiple testing correction, small sample size, and absence of functional validation.
- The claim of "concordant genetic signals and mechanistic in-silico effects" is not established because the abstract does not demonstrate a direct link between the in-silico results and the genetic associations.
- The in-silico findings for SLC39A11 (increased RMSD/RMSF, helix displacement, modest destabilization) are reported qualitatively and cannot be evaluated without quantitative data and methodological details.
- The absence of any association for the TPCN2 variant is reported, but the abstract does not state whether the study was adequately powered to detect an effect, making the null result difficult to interpret.
- The generalizability of the findings to other populations is not addressed, and the abstract does not discuss potential population-specific effects.