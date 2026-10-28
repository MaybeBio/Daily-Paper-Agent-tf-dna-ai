## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusion, methods) as provided
- **Assessment boundary** Scientific claims, methodological soundness, experimental design, and evidence quality as presented in the supplied text. No external data or code were accessed.
- **Shared manuscript claim summary** The authors propose PortalCG, a deep learning framework combining 3D binding site-enhanced sequence pretraining, end-to-end sequence-structure-function transfer learning, out-of-cluster meta-learning, and stress model selection, to predict chemical-protein interactions for "dark" proteins and gene families lacking known ligands. They report superior performance over the DISAE baseline and docking-based methods, and demonstrate utility in two case studies: selective dual-antagonists of dopamine receptors for opioid use disorder, and illuminating undruggable human genome targets.
- **Visible evidence base** Abstract, Introduction, Results sections 2.1-2.7, Conclusion, Methods section 4.1-4.3, Figure and Table references (Figures 1-5, Tables 1-6, Supplemental Figures S1-S9, Supplemental Tables S1-S7), Author Contributions, Data availability, Acknowledgements
- **Missing materials affecting confidence** Figures and tables themselves were not provided, only referenced. Supplemental materials (Tables S1-S11, Figures S1-S9, Schemes 1-5) were not accessible. Experimental details for compound synthesis and binding assays are only referenced. Code and trained models are stated to be available but were not inspected. No raw performance numbers beyond those quoted in text were available for independent verification.

## Reviewer

### Overall assessment
This manuscript addresses a genuinely important problem: predicting chemical-protein interactions for proteins with no known ligands, framed as an out-of-distribution generalization challenge. The proposed framework integrates several sophisticated components, and the authors report substantial improvements over strong baselines. The case studies, particularly the prospective synthesis and testing of 65 compounds for dopamine receptor selectivity, are commendable and add practical relevance. However, the manuscript as provided has several significant gaps that prevent full assessment. The most critical issues are the lack of accessible figures and tables, the absence of detailed ablation studies in the visible text, and insufficient clarity on the meta-learning formulation and its theoretical justification. The claim that PortalCG "surpassed the human design" in the multi-target screening case is striking but the evidence for this is not fully presented in the visible text. The work is potentially significant for the chemical genomics and drug discovery communities, but the current evidence base is insufficient to fully establish all claims.

### Who would be interested in the results, and why
Computational chemists and bioinformaticians working on chemical-protein interaction prediction, particularly those concerned with generalization to unseen protein families, would find the methodological contributions relevant. Drug discovery researchers interested in polypharmacology, off-target prediction, and target de-orphaning would value the demonstrated applications. The broader machine learning community working on out-of-distribution generalization and meta-learning might also find the OOC-ML algorithm of interest, though the formulation is domain-specific. The case study on dopamine receptor antagonists for opioid use disorder could attract medicinal chemists, though the experimental validation is limited to binding assays.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim PortalCG "considerably outperformed state-of-the-art techniques of machine learning and protein-ligand docking when applied to dark gene families" and report specific PR-AUC values (0.714 vs 0.603 for DISAE).
- **Evidence pointer** Section 2.3, Figure 3, Table 2, Supplemental Figures S4-S6
- **Concern** The key quantitative results are presented in figures and tables that were not provided in the submitted material. The text quotes a few numbers (PR-AUC 0.714 vs 0.603, p-value < 1e-40), but the full performance comparison across all baselines, the breakdown by protein family, and the statistical significance testing methodology cannot be verified. The ablation study in Table 2 is referenced but its contents are not visible. Without access to these data, the central performance claims cannot be independently assessed.
- **Why it matters** The core contribution of this work is the claimed performance improvement. If the figures and tables are not available for review, the evidence base is fundamentally incomplete, and the manuscript cannot be properly evaluated.
- **Resolution test** Provide all figures and tables with full captions, including error bars, sample sizes, and statistical test details. Ensure the ablation study (Table 2) is fully described and discussed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The OOC-ML algorithm is described as "out-of-cluster meta-learning" that "extracts and accumulates information learned from predicting ligands of distinct gene families (meta-data) and applies the meta-data to a dark gene family." The authors state it differs from ensemble learning in three key ways, including using gradients of mapping functions as meta-data.
- **Evidence pointer** Section 2.1, Section 4.2, Algorithm 1, Figure 1B
- **Concern** The description of OOC-ML is conceptually interesting but lacks mathematical precision. The pseudocode (Algorithm 1) is referenced but not provided in the visible text. The claim that gradients of low-level models are used as meta-data for the high-level model is unusual and requires a clear formalization. How exactly are gradients aggregated across tasks? What is the loss function for the high-level model? How does this relate to established meta-learning methods like MAML or Reptile? The text mentions similarities to MAML but does not articulate the differences clearly. Without the algorithm pseudocode and a formal problem statement, the method cannot be reproduced or fully understood.
- **Why it matters** The OOC-ML component is presented as a key novelty of the work. If the algorithm is not precisely specified, the scientific contribution is unclear and the results cannot be reproduced by others.
- **Resolution test** Provide the full pseudocode for OOC-ML, a formal mathematical statement of the optimization problem, and a clear explanation of how gradients are computed, aggregated, and used to update the high-level model. Include a comparison with existing meta-learning methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors state "in an external validation for the multi-target compound screening, the performance of PortalCG surpassed the human design" and describe a case study where PortalCG was used to design selective dual-antagonists of DRD1 and DRD3 for opioid use disorder.
- **Evidence pointer** Section 2.6, Figure 4, Supplemental Table S2
- **Concern** The claim that PortalCG surpassed human design is strong and requires careful scrutiny. The text mentions 65 synthesized compounds with a 15.4% success rate for the dual-antagonist criteria, and states PortalCG achieved 20.0% and 50.7% success rates for all three or any two dopamine receptors predicted correctly, respectively. However, the comparison with "human design" is not clearly defined. What was the human-designed success rate? How was the comparison made? Was it a prospective, blinded comparison? The experimental details of the binding assays are only referenced to supplemental materials. The criteria for "success" (Ki thresholds) are stated but the distribution of results is not shown. This is a critical claim that needs full transparency.
- **Why it matters** The claim of surpassing human design is a headline result that, if true, would be significant. However, without a clear definition of the comparator and full experimental details, this claim cannot be evaluated and risks overstatement.
- **Resolution test** Clearly define the "human design" comparator, including the criteria and the success rate. Provide full experimental details for the binding assays, including raw data, replicates, and statistical analysis. Clarify whether the comparison was prospective and blinded.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Baseline fairness
- **Claim pointer** The authors compare PortalCG against DISAE and PLD-based methods (Autodock Vina, PLD+SIGN) and claim superior performance.
- **Evidence pointer** Section 2.3, Section 2.5, Table 3, Figure 3
- **Concern** The comparison with DISAE is reasonable given the architectural similarity, but the comparison with docking-based methods may not be entirely fair. The docking baselines use only structural information, while PortalCG uses sequence and chemical information. The authors acknowledge this limitation but do not discuss whether the comparison is apples-to-apples. For the DUD-E benchmark, the authors state PortalCG outperforms Autodock Vina on 6 of 8 targets, but the text does not specify the performance of PLD+SIGN on all targets or the statistical significance of these differences. The choice of DUD-E targets and the training protocol for the docking baselines need more detail.
- **Why it matters** If the baselines are not optimally configured or the comparison is not fair, the claimed improvements may be overstated.
- **Resolution test** Provide full details on the configuration of all baselines, including hyperparameters and any tuning performed. Discuss the fairness of comparing sequence-based methods with structure-based docking methods and acknowledge any inherent advantages or disadvantages.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability claims
- **Claim pointer** The authors claim PortalCG "is a viable solution to the OOD problem in exploring the understudied protein functional space" and demonstrate its application to the "undruggable" human genome.
- **Evidence pointer** Section 2.7, Tables 4-5, Supplemental Tables S3-S11
- **Concern** The application to the undruggable human genome is interesting but the validation is limited. The authors predict binding for 12,475 proteins against ~6,000 drugs and identify 267 proteins with low false positive rates. However, these predictions are not experimentally validated. The functional enrichment analysis is presented but the biological significance of the predicted interactions is not discussed in depth. The claim of "illuminating" the undruggable genome is strong given that no experimental confirmation is provided.
- **Why it matters** The generalizability of the method to novel protein families is a key claim. Without experimental validation of the predictions, the practical utility remains uncertain.
- **Resolution test** Provide additional validation, such as literature evidence for a subset of predicted interactions, or clearly state that these are computational predictions requiring experimental confirmation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Section 2.1, Section 4.2
- **Issue** The term "out-of-cluster meta-learning" is used but not formally defined. The relationship between "cluster" and "gene family" is implied but not explicit.
- **Required correction** Define "cluster" in this context and clarify whether it refers to gene families, sequence clusters, or functional clusters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Section 4.1, Data and software availability
- **Issue** The authors state that data can be downloaded from public resources, but specific version numbers, access dates, and preprocessing scripts are not described in the visible text.
- **Required correction** Provide a detailed data availability statement with specific database versions, download URLs, and preprocessing code.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Performance metrics
- **Evidence pointer** Section 2.3, Figure 3
- **Concern** The text reports PR-AUC values and a p-value but does not specify the statistical test used, the number of replicates, or the confidence intervals.
- **Required correction** Report the statistical test used, the number of independent runs, and confidence intervals for all reported metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 5 description
- **Evidence pointer** Section 2.7, Figure 5
- **Issue** The description of the drug-target interaction network for Alzheimer's disease is brief. The criteria for including nodes and edges, and the threshold of 0.67, are mentioned but not explained in context.
- **Required correction** Provide a clear description of the network construction, including the meaning of the threshold and the source of the interaction data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Related work
- **Evidence pointer** Section 1
- **Issue** The introduction cites several relevant works but does not provide a comprehensive comparison with recent deep learning methods for CPI prediction, particularly those addressing OOD or few-shot scenarios.
- **Required correction** Expand the related work discussion to include recent methods and explicitly state the novelty of PortalCG relative to each.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Typos and language
- **Affected element** Throughout
- **Evidence pointer** Section 2.7, Section 4.2
- **Issue** There are minor typographical errors, e.g., "PortaCG" in the section heading for the algorithm description, and "low leverl" in Section 4.2.
- **Required correction** Proofread the manuscript for typographical errors.

### Technical failings that need to be addressed before the case is established
R1-M1 (missing figures and tables), R1-M2 (incomplete algorithm specification), and R1-M3 (unclear comparison with human design) are the most critical. Without access to the primary data and a complete method description, the central claims cannot be verified. The manuscript should not be considered for publication until these are resolved.

### Assessment against Nature-style criteria
- **Originality** The combination of binding site-enhanced pretraining with out-of-cluster meta-learning is a novel contribution. The framing of dark protein prediction as an OOD problem is appropriate and timely. However, the individual components (sequence pretraining, meta-learning) are established techniques, and the novelty lies in their integration.
- **Scientific importance** The problem addressed is of high importance. The ability to predict ligands for dark proteins would have broad implications for chemical genomics, drug discovery, and functional annotation. If the claims are substantiated, this would be a significant advance.
- **Interdisciplinary readership** The work bridges machine learning, computational chemistry, and drug discovery. The potential readership is broad, but the manuscript is written in a way that assumes familiarity with both deep learning and cheminformatics terminology. The abstract is accessible, but the methods section is dense.
- **Technical soundness** The technical approach is plausible, but the current evidence base is insufficient to fully assess soundness. The missing figures, tables, and algorithm pseudocode prevent a thorough evaluation. The statistical rigor of the comparisons is not fully described.
- **Readability for nonspecialists** The abstract and introduction are reasonably accessible. The results and methods sections are more technical and would be challenging for a nonspecialist. The use of domain-specific terms like "distogram," "masked language modeling," and "meta-learning" without sufficient explanation could be a barrier.

### Recommendation posture
Supportive if technical concerns are resolved. The core idea is promising and the problem is important, but the manuscript in its current form does not provide sufficient evidence to fully establish the claims. The missing figures and tables, incomplete algorithm description, and unclear comparison with human design must be addressed. If these are resolved and the claims hold, this could be a valuable contribution. Currently, the case is not fully established from the provided evidence.

## Risk / unsupported claims
- The claim that PortalCG "surpassed the human design" in the multi-target compound screening case is not fully supported by the visible evidence. The comparator and the details of the comparison are not clearly defined.
- The claim that PortalCG "considerably outperformed state-of-the-art techniques" is based on data in figures and tables that were not provided.
- The claim that the method is "a viable solution to the OOD problem" is a strong generalization from the presented benchmarks and case studies, which may not cover all OOD scenarios.
- The claim that "protein structure information serve as an intermediate layer could be superior to conventional methodology" is presented as a suggestion but is not rigorously tested against a direct comparison with structure-input methods.
- The generalizability of the method to all dark proteins is not established, as the benchmarks may not represent the full diversity of protein families and chemical space.