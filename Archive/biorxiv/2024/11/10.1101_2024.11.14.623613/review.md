## Review setup
- **Input scope** Full manuscript text including abstract, main text, and appendices
- **Assessment boundary** Scientific validity of the claims as presented in the provided manuscript; no assessment of code functionality or reproducibility beyond what is described
- **Shared manuscript claim summary** The authors propose an unsupervised method using ESM2 masked language model reconstruction loss to rank protein-peptide binding affinities without labeled data, structural information, or complex features, validated against five IC50 datasets and extended preliminarily to protein-protein interactions and docking
- **Visible evidence base** Main text sections 1-5, Appendix sections A.1-A.7, Tables A1-A5 referenced, Figures 1-2 and A3-A7 referenced
- **Missing materials affecting confidence** Actual figures and tables are not provided in the submitted material; code repository is referenced but not reviewed; statistical significance testing details are incomplete; the PPI-Affinity comparison methodology relies on published results without live access

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting extension of binary protein interaction classification to affinity ranking using unsupervised protein language models. The core idea of using masked reconstruction loss to score mutation positions relative to a reference peptide is novel and potentially useful for prioritising candidates in mutation campaigns. However, the evidence presented is insufficient to fully establish the method's reliability. The results are mixed across datasets, with acknowledged failures on MDM2/MDMX, and the manuscript lacks rigorous statistical validation, ablation studies, and a clear articulation of when the method can be expected to work. The extension to protein-protein interactions and docking is preliminary and underdeveloped. The writing is generally clear but contains typographical errors and some methodological ambiguities that need resolution.
- **Who would be interested in the results, and why** Researchers in computational protein engineering, peptide therapeutics, and protein interaction prediction would find this work relevant. The unsupervised nature of the approach and its speed make it attractive for screening large variant libraries before experimental validation. The method could be useful for prioritising mutation sites in directed evolution campaigns. The broader protein language model community may also be interested in this application of ESM2 beyond its typical classification and generation tasks.
- **Major strengths** The manuscript addresses a practical problem with a simple, fast, and unsupervised approach. The use of ESM2 in evaluation mode avoids expensive training and structural inputs. The method is tested on multiple datasets with different protein targets, providing some breadth of evaluation. The authors are transparent about limitations, particularly the MDM2/MDMX failures and the inability to distinguish same-position mutations. The code is made available, which supports reproducibility.
- **Major Concerns** The evidence base is incomplete as figures and tables are not provided. The method's performance is inconsistent across datasets, and the authors do not provide a principled explanation for when it succeeds or fails. The comparison with PPI-Affinity is limited by reliance on published results. Statistical significance of ranking improvements over baseline is not rigorously established. The extension to protein-protein interactions and docking is too preliminary to support the claims made. The method's inability to distinguish mutations at the same positions is a significant limitation that is acknowledged but not addressed.
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide sufficient detail on the experimental setup, including hyperparameters, masking strategies, and the exact computation of the loss. The choice of reference peptide and its impact on results is not systematically explored. The evaluation metrics are described but their application is not fully transparent. The statistical comparison against random baseline is mentioned but the details of the Fisher combined test application are unclear.
- **Assessment against Nature-style criteria** Originality: The application of MLM loss to affinity ranking is a novel contribution, building on prior binary classification work. Scientific importance: The problem is relevant, but the demonstrated performance is not yet compelling enough to establish broad utility. Interdisciplinary readership: The work bridges machine learning and protein biology, but the presentation assumes familiarity with both fields without sufficient context for either audience. Technical soundness: The core idea is plausible, but the evaluation is incomplete and the mixed results raise questions about reliability. Readability for nonspecialists: The manuscript is generally readable but contains jargon and lacks sufficient background for a general scientific audience. The abstract is clear, but the methods section assumes prior knowledge of language model architectures.
- **Recommendation posture** Currently not established from the provided evidence. The core idea has merit, but the manuscript requires substantial additional validation, clearer methodology, and a more rigorous treatment of the mixed results before the claims can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim the method "aligns closely with experimental rankings" and demonstrates "robust performance in ranking effectiveness" across datasets
- **Evidence pointer** Figures 1, 2, A3-A7; Tables A1-A5; location not provided
- **Concern** The manuscript references multiple figures and tables that are not included in the submitted material. Without these, the core evidence for the method's performance cannot be evaluated. The claims of alignment with experimental rankings, NDCG values, and precision scores are unverifiable from the text alone. This is a fundamental issue that prevents assessment of the method's validity.
- **Why it matters** The central claim of the manuscript is that the proposed method effectively ranks binding affinities. This claim rests entirely on the visual and quantitative comparisons presented in the missing figures and tables. Without access to these, the scientific case cannot be assessed.
- **Resolution test** Provide all figures and tables referenced in the manuscript, with clear captions and axis labels, so that the claimed performance can be independently evaluated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The method is described as measuring "the amount of mutual information between Q and the P_ref contained in the masked positions, which can be considered as an indicator of binding affinity"
- **Evidence pointer** Section 2.4; location not provided
- **Concern** The manuscript does not provide sufficient detail on the exact computational procedure. The loss function in Equation 2 is defined, but the masking strategy, the handling of multiple mutation positions, the choice of which positions to mask, and the exact computation of the loss for concatenated sequences are not fully specified. The relationship between the loss and "mutual information" is asserted but not formally justified. The algorithm descriptions are high-level and lack implementation details.
- **Why it matters** Reproducibility is a core requirement for scientific claims. Without precise methodological details, other researchers cannot implement or validate the method. The conceptual link between MLM loss and binding affinity is not rigorously established, which weakens the theoretical foundation of the approach.
- **Resolution test** Provide a detailed, step-by-step description of the algorithm, including pseudocode with specific masking strategies, handling of sequence concatenation, and the exact computation of the loss. Justify the connection between MLM loss and binding affinity with formal reasoning or empirical evidence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validation
- **Claim pointer** The authors report NDCG, precision@K, and Kendall's tau values and state that statistics are "calculated against a random baseline"
- **Evidence pointer** Section 3, Appendix A.6; location not provided
- **Concern** The statistical comparison against a random baseline is mentioned but the details are incomplete. The Fisher combined probability test is referenced but its application is not described. It is unclear how many random runs were performed, how the p-values were computed, and whether the reported improvements are statistically significant. The manuscript does not report confidence intervals or effect sizes for the ranking metrics.
- **Why it matters** Without proper statistical validation, the reported performance improvements could be due to chance, particularly given the small dataset sizes and the acknowledged failures on some datasets. The claim that the method outperforms random ranking needs rigorous support.
- **Resolution test** Provide a complete description of the statistical testing procedure, including the number of random runs, the computation of p-values, and the results of significance tests for each dataset and metric. Report confidence intervals for the ranking metrics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state the method "can be applied both to ranking sets of variants suggested by other methods, and for narrowing the search space of semi-rational mutation campaigns"
- **Evidence pointer** Section 1, Section 4.1; location not provided
- **Concern** The method is tested on five datasets, but these are limited to specific protein families (HtrA1, HtrA3, MDM2, MDMX, EPI-X4). The authors do not discuss the diversity of these systems or the potential for the method to generalise to other protein-peptide interactions with different characteristics, such as different binding modes, peptide lengths, or affinity ranges. The failure on MDM2/MDMX raises questions about the conditions under which the method is reliable.
- **Why it matters** The claimed utility of the method depends on its applicability beyond the tested cases. Without a broader evaluation or a principled understanding of when the method works, the practical value is uncertain.
- **Resolution test** Discuss the characteristics of the tested systems and their representativeness. Provide a hypothesis for why the method fails on some systems and succeeds on others. If possible, include additional test cases with diverse characteristics.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with existing methods
- **Claim pointer** The authors compare their method against PPI-Affinity and report superior or comparable performance
- **Evidence pointer** Section 3.1, Section 3.3, Appendix A.4; location not provided
- **Concern** The comparison with PPI-Affinity is limited. For HtrA1/HtrA3, the comparison relies on results "directly copied from their publication" without live access to the PPI-Affinity server. The authors do not describe the conditions under which PPI-Affinity was applied, whether the same datasets were used, or whether the comparison is fair. For EPI-X4, the comparison is described but the details are in the missing figures. No comparison is made with other unsupervised or language model-based methods.
- **Why it matters** A claim of improved or comparable performance requires a fair and transparent comparison. Without this, the relative merit of the proposed method is unclear.
- **Resolution test** Provide a detailed description of the PPI-Affinity comparison, including the exact datasets, parameters, and conditions. If possible, run PPI-Affinity on the same datasets and report the results. Include comparisons with other relevant methods.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Extension to protein-protein interactions and docking
- **Claim pointer** The authors claim "promising results" for protein-protein interactions and docking scenarios
- **Evidence pointer** Appendix A.2, A.3; location not provided
- **Concern** The extension to protein-protein interactions and docking is presented as preliminary, but the claims of "promising results" are not supported by sufficient evidence. The DPP4-MERS-CoV analysis compares rankings with Mutabind2 but the agreement is described qualitatively. The PD1-PDL1 docking analysis identifies candidate regions but the evaluation is based on proximity to experimentally determined regions, which is a weak validation. The methodology for these extensions is not fully described.
- **Why it matters** The claims of generalizability to protein-protein interactions and docking are part of the manuscript's contribution. If these are not rigorously supported, the scope of the claimed utility is overstated.
- **Resolution test** Provide quantitative results for the protein-protein interaction and docking analyses, including the full comparison with Mutabind2 and a more rigorous evaluation of the docking predictions. Clearly state the limitations of these preliminary results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Abstract, Section 1, Section 4
- **Evidence pointer** location not provided
- **Issue** The manuscript contains typographical errors and awkward phrasing, such as "resons" in Section 3.2 and "effectivenes" in Section 4.1. Some sentences are overly long and could be clarified.
- **Required correction** Proofread the manuscript carefully and revise for clarity and grammatical correctness.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 2.2, Section 2.3
- **Evidence pointer** location not provided
- **Issue** The term "mutual information" is used to describe the relationship between the MLM loss and binding affinity, but this is not formally defined or justified. The connection between reconstruction loss and information-theoretic concepts is not established.
- **Required correction** Either provide a formal justification for the use of "mutual information" or use a more neutral term such as "reconstruction-based score."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reference completeness
- **Affected element** Section 1, Section 3
- **Evidence pointer** location not provided
- **Issue** Some references are cited with numbers but the reference list is not provided in the submitted material. This makes it impossible to verify the cited works.
- **Required correction** Provide the complete reference list.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1, 2, A3-A7
- **Evidence pointer** location not provided
- **Issue** The figures are not provided, so their quality and clarity cannot be assessed. The captions referenced in the text suggest they contain the key evidence for the method's performance.
- **Required correction** Provide all figures with clear captions, axis labels, and legends.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Code availability
- **Affected element** Appendix A.1
- **Evidence pointer** location not provided
- **Issue** The code repository is referenced but not described. It is unclear what the repository contains, whether it is documented, and whether it can be used to reproduce the results.
- **Required correction** Provide a brief description of the repository contents and instructions for use.

## Risk / unsupported claims
- The claim that the method "aligns closely with experimental rankings" is unsupported because the figures and tables showing this alignment are not provided.
- The claim of "robust performance in ranking effectiveness" for HtrA3 is unsupported without the quantitative results.
- The claim of "promising results" for protein-protein interactions and docking is unsupported because the evidence is qualitative and the methodology is incomplete.
- The claim that the method "overcomes the need for labelled datasets and complex feature engineering" is supported by the unsupervised nature of the approach, but the practical utility of this advantage is not demonstrated.
- The claim that the method can be used to "reduce the number of candidates sent to the lab" is plausible but not validated with any cost-benefit analysis or practical demonstration.
- The statistical significance of the reported improvements over random baseline is not established from the provided material.