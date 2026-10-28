## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific and technical evaluation of the LEPAE method, its validation, and the claims made; no assessment of code functionality or data reproducibility beyond what is described
- **Shared manuscript claim summary** The authors present LEPAE, a neural network-based method that scores pairwise associations between genomic windows using large-scale epigenomic and transcription factor binding data, and demonstrate that these scores capture biologically meaningful relationships as validated against gene annotations, chromatin states, TADs, and fine-mapped GWAS variants
- **Visible evidence base** Main text figures referenced (Figs 1-6), supplementary figures and methods referenced but not provided, data availability statements, methodological descriptions in Section 2
- **Missing materials affecting confidence** Supplementary figures and methods (Figs 1-10 in supplementary), Table 1, actual figure images, detailed hyperparameter search results, code repository contents, validation dataset details

## Reviewer
- **Overall assessment** The manuscript describes a conceptually interesting approach to a challenging problem in genomics, namely learning pairwise associations between genomic loci from diverse functional genomics data. The method builds on a previously published framework (LECIF) and adapts it to the intra-genomic setting. The validation strategy is thoughtful, using multiple independent annotations not provided as input features. However, the manuscript as presented has several technical gaps that need to be addressed, particularly around the interpretation of the predictive performance metric, the handling of distance-dependent effects, and the clarity of the validation analyses. The claims are largely supported by the described analyses, but the absence of supplementary materials limits full assessment.
- **Who would be interested in the results, and why** Researchers in computational genomics, particularly those working on enhancer-promoter interactions, 3D genome organization, and functional annotation of non-coding variants. The method could also be of interest to those developing machine learning approaches for genomic data integration. The resource aspect (precomputed scores for millions of pairs) may appeal to a broader genomics community.
- **Major strengths** 
  1. The problem is well-motivated and the limitations of existing approaches (Hi-C, correlation-based methods) are clearly articulated.
  2. The Siamese network architecture is appropriate for the pairwise classification task and the adaptation from LECIF is logical.
  3. The validation strategy using multiple independent annotations (genes, chromatin states, TADs, GWAS variants) is comprehensive and thoughtful.
  4. The method produces a potentially useful community resource with scores for a large number of genomic pairs.
  5. The authors are transparent about limitations and future directions.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "LEPAE has strong predictive power when differentiating positive pairs from negative pairs" (Section 3.2)
  - **Evidence pointer** Section 3.2, Figure 3a
  - **Concern** The predictive performance is measured as AUROC for distinguishing positive pairs (pairs at a fixed distance d) from negative pairs (randomly mismatched pairs from the same chromosome). However, the negative pairs are not necessarily at a different distance from the positive pairs, since they are created by shuffling the pairing of positive pairs. This means the classifier could be learning to distinguish pairs at distance d from pairs at other distances, rather than learning about genuine biological associations. The authors do not clearly address whether the AUROC reflects distance discrimination rather than association evidence.
  - **Why it matters** If the classifier is primarily learning distance information rather than biological association patterns, the interpretation of LEPAE scores as evidence of functional association would be undermined. The modest correlation with genomic distance (PCC of -0.18 and -0.26) suggests distance is not the dominant factor, but the AUROC values could still be inflated by distance-related features.
  - **Resolution test** The authors should provide an analysis that controls for distance effects, such as comparing LEPAE performance against a baseline that uses only distance information, or showing AUROC for pairs at the same distance but with shuffled labels. Alternatively, they could demonstrate that LEPAE scores for pairs at the same distance but with different biological contexts (e.g., within TAD vs. across TAD) are distinguishable.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "LEPAE captures biologically meaningful pairwise relationships between genomic loci" (Abstract, Section 3.3)
  - **Evidence pointer** Section 3.3, Figure 4
  - **Concern** The validation using gene annotations compares pairs within the same gene body to pairs crossing gene boundaries. However, the control set is described as "pairs of bases for the same set of genes and the same distance apart but with one base inside and the other outside the gene body." This control design may not adequately control for all confounders, such as the fact that pairs within a gene body are more likely to be in the same chromatin domain or have similar epigenetic states. The authors do not describe how they matched for chromatin state composition or other potential confounders.
  - **Why it matters** If the control set is not adequately matched, the observed differences in LEPAE scores could be driven by known differences in chromatin features between gene bodies and non-genic regions, rather than by genuine pairwise association patterns learned by the model.
  - **Resolution test** The authors should provide a more detailed description of the matching procedure, or perform additional analyses that control for chromatin state composition, GC content, repeat content, or other relevant genomic features.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** "The LEPAE scores and the software are available" (Availability section)
  - **Evidence pointer** Availability section, Data availability section
  - **Concern** While the authors state that code and scores are available, the manuscript does not provide details on the exact format of the scores, the versioning of the software, or the computational requirements for running LEPAE on new data. The supplementary materials (referenced as available at Bioinformatics online) are not provided for this review, limiting the ability to assess reproducibility.
  - **Why it matters** For a method paper that claims to provide a community resource, reproducibility and usability are critical. Without clear documentation of the software interface, input/output formats, and dependencies, other researchers may find it difficult to apply LEPAE to their own data.
  - **Resolution test** The authors should provide a detailed user guide, example input/output files, and a description of the computational environment required. If possible, they should also provide a containerized version of the software.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.1
  - **Evidence pointer** Section 2.1
  - **Issue** The description of the Siamese network architecture is brief. The authors state that "all sub-networks had a single hidden layer, resulting in two hidden layers in total," but it is unclear whether the final combining sub-network also has a single hidden layer or if this refers to the two identical sub-networks only.
  - **Required correction** Clarify the architecture description, specifying the number of layers in each component of the network.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Section 3.3
  - **Evidence pointer** Section 3.3, Figure 4
  - **Concern** The authors report Wilcoxon signed-rank test P<.0001 for the comparison of LEPAE scores within gene bodies vs. crossing boundaries, and Mann-Whitney U test P<.0001 for comparing the difference with Hi-C and Jaccard index. However, the exact sample sizes and the nature of the paired comparisons are not described.
  - **Required correction** Provide details on the number of pairs analyzed, whether the comparisons are paired or unpaired, and how the statistical tests were applied.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Section 3.4
  - **Evidence pointer** Section 3.4
  - **Concern** The authors report a low mean PCC of 0.06 between LEPAE scores and Hi-C contact frequencies, but then report that LEPAE scores are higher within TADs than across TAD boundaries. The relationship between these two findings is not fully explored. If LEPAE scores are largely uncorrelated with Hi-C contact frequencies, why would they align with TAD boundaries, which are derived from Hi-C data?
  - **Required correction** Provide a more detailed discussion of the relationship between LEPAE scores, Hi-C contact frequencies, and TAD boundaries, possibly including an analysis of LEPAE scores within TADs vs. across TADs at matched distances.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 3.5
  - **Evidence pointer** Section 3.5, Figure 6
  - **Concern** The analysis of fine-mapped GWAS variants is described briefly. The authors state that 73-78 of 94 traits had higher LEPAE scores for original pairs compared to controls, but the range of 73-78 suggests variability across fine-mapping methods and resolutions. The details of how this comparison was performed and how significance was assessed are not fully described.
  - **Required correction** Provide a more detailed description of the GWAS variant analysis, including how pairs were defined, how controls were matched, and how the binomial test was applied.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The predictive performance metric may reflect distance discrimination rather than biological association; needs a control analysis
  - R1-M2: The gene body validation may be confounded by genomic features; needs better matching or additional controls
- **Assessment against Nature-style criteria**
  - **Originality** The adaptation of the LECIF framework to intra-genomic pairwise association scoring is a novel contribution. While the underlying concept of using functional genomics data to infer relationships between loci is not new, the specific methodological approach and the scale of application are original.
  - **Scientific importance** The problem of identifying pairwise associations between genomic loci is important for understanding gene regulation, and a method that can systematically score such associations from large-scale data could be valuable. However, the incremental advance over existing methods (e.g., correlation-based approaches, Hi-C) needs to be more clearly demonstrated.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and bioinformaticians. The potential broader impact on experimental biologists or clinical researchers is not fully articulated, though the resource aspect could broaden the audience.
  - **Technical soundness** The methodological approach is reasonable, but the validation strategy has potential confounders that need to be addressed. The lack of supplementary materials limits full assessment of technical details.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible to readers with a background in computational genomics. The motivation and results are clearly stated, though some technical details could be explained more clearly.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the resource could be valuable, but the validation needs to be strengthened to rule out distance-based artifacts and confounding in the gene body analysis. The authors should also provide more detail on the reproducibility of the method.

## Risk / unsupported claims
- The claim that LEPAE "captures biologically meaningful pairwise relationships" is supported by the gene body and TAD analyses, but the potential confounding in the gene body analysis and the unclear relationship with Hi-C data mean this claim is not fully established.
- The claim that LEPAE "achieves better predictive power than a score learned by decision trees" is stated but the comparison details are not provided in the main text.
- The claim that LEPAE scores are "largely distinct from 1D genomic distance" is supported by the modest PCC values, but the AUROC analysis does not fully rule out distance-based discrimination.
- The generalizability of LEPAE to other species or data types is discussed as future work and is not claimed as a current capability.