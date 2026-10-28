## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, figure legends, and supplementary information descriptions.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with Nature-style criteria. Editorial decisions and author rebuttals are outside scope.
- **Shared manuscript claim summary** The authors present a multimodal single-cell and spatial atlas of the mouse liver, integrating snRNA-seq, snATAC-seq, and single-cell multiome data. They identify hepatocyte zonation states and construct enhancer-driven gene regulatory networks (eGRNs) using SCENIC+. They identify TCF7L1 and TBX3 as zonation-specific transcriptional repressors. They train a deep learning model (DeepLiver) to predict enhancer activity and zonation from DNA sequence, and validate predictions using MPRA, ChIP-seq, and luciferase assays.
- **Visible evidence base** Main text figures 1-8, Extended Data figures 1-10, Supplementary figures 1-9, Supplementary tables 1-4, and methods sections. Specific data files and code repositories are referenced but not fully accessible in this review.
- **Missing materials affecting confidence** Raw sequencing data, processed data matrices, code for DeepLiver and SCENIC+ analyses, and full source data files are not provided. Details on hyperparameter tuning, model architecture specifics, and cross-validation splits for DeepLiver are partially described but not fully reproducible from the text. The full list of 100 genes used in the spatial panel and the complete MPRA library design are not fully detailed.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and technically ambitious resource for the liver biology and gene regulation communities. The integration of single-cell multi-omics, spatial transcriptomics, and deep learning is novel and the identification of TCF7L1 and TBX3 as zonation-specific repressors is a significant finding. The DeepLiver model and its validation through MPRA and luciferase assays are compelling. However, several technical aspects require clarification and additional validation to fully support the claims, particularly regarding the specificity of the repressor mechanisms, the robustness of the deep learning model, and the generalizability of the findings.
- **Who would be interested in the results, and why** Hepatologists, liver biologists, and researchers studying gene regulation, enhancer biology, and cellular zonation. The deep learning approach and the integration of multi-omic data will also be of interest to computational biologists and bioinformaticians developing methods for regulatory genomics. The resource itself (atlas, eGRNs, DeepLiver model) will be a valuable tool for the broader mammalian genomics community.
- **Major strengths**
    1.  The generation of a comprehensive, multi-modal single-cell and spatial atlas of the mouse liver, which is a valuable public resource.
    2.  The identification of TCF7L1 and TBX3 as novel zonation-specific transcriptional repressors, supported by multiple lines of evidence (SCENIC+, ChIP-seq, MPRA, luciferase).
    3.  The development of DeepLiver, a deep learning model that integrates enhancer activity and zonation prediction, and its validation with experimental data.
    4.  The use of transfer learning to overcome limited training data for the activity and zonation models is a smart methodological choice.
    5.  The validation strategy is multi-pronged, including in silico perturbation, MPRA in vitro and in vivo, and luciferase assays, which strengthens the conclusions.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical soundness / Reproducibility
        - **Claim pointer** The authors claim that DeepLiver can predict enhancer activity and zonation from DNA sequence, and that this model was validated using MPRA and luciferase assays.
        - **Evidence pointer** Methods: DeepLiver, Model performance; Figures 4, 7, 8; Extended Data Figure 7.
        - **Concern** The description of the DeepLiver model architecture, training, and evaluation is insufficient for reproducibility. The text mentions a "hybrid CNN-recurrent-neural-network multiclass classifier" and transfer learning, but lacks critical details such as the number of layers, filter sizes, pooling strategies, dropout rates, optimization algorithm, learning rate schedule, and the exact definition of the training/validation/test splits. The performance metrics (AUROC, AUPR) are reported, but the baseline for comparison (e.g., random classifier) is only mentioned for one metric. The correlation with external MPRA data (R=0.68) is presented, but the details of this external dataset and the analysis are not fully described.
        - **Why it matters** Without a complete and transparent description of the model and its evaluation, the results are not reproducible, and the claimed predictive power cannot be independently verified. This is a core methodological pillar of the paper.
        - **Resolution test** The authors must provide a complete, step-by-step description of the DeepLiver architecture, training procedure, and hyperparameter selection. They should also provide the code and trained model weights. The evaluation protocol should be clarified, including how the external MPRA dataset was used and what the baseline performance is.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Scientific importance / Validity of claims
        - **Claim pointer** The authors conclude that TCF7L1 and TBX3 are direct repressors of zonation-specific enhancers, and that their binding sites are an integral part of the enhancer grammar.
        - **Evidence pointer** Figures 2, 5, 6, 7, 8; Extended Data Figures 4, 5, 8, 9, 10.
        - **Concern** While the evidence for a repressive role is suggestive, the direct mechanism is not fully proven. The ChIP-seq for TBX3 shows binding to periportal regions, but the functional validation via MPRA and luciferase shows modest effect sizes. The in silico perturbation experiments are based on the SCENIC+ network predictions, which are themselves computational. The claim that these repressors "directly" regulate the enhancers would be strengthened by a more direct assay, such as a targeted perturbation of the specific binding sites in a reporter construct, or an epistasis experiment. The manuscript does not show that TCF7L1 binds directly to the predicted regions (no TCF7L1 ChIP-seq is presented).
        - **Why it matters** The central biological claim of the paper is that these two repressors are key drivers of zonation. If the evidence for direct repression is not conclusive, the significance of the finding is diminished.
        - **Resolution test** The authors should either provide direct evidence of TCF7L1 binding (e.g., ChIP-seq) or temper their conclusions to state that TCF7L1 and TBX3 are "predicted" or "likely" direct repressors. They could also perform a more definitive functional assay, such as mutating the specific binding sites in the context of a reporter and showing that this abolishes the zonation-specific repression.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Technical soundness / Interdisciplinary readership
        - **Claim pointer** The authors state that the spatial transcriptomics data (molecular cartography) was used to validate the zonation patterns and eGRN predictions.
        - **Evidence pointer** Figure 1g, 1h; Methods: Molecular cartography in the mouse liver.
        - **Concern** The description of the spatial data analysis is brief. The methods for cell segmentation, gene selection, and the integration of spatial data with the single-cell data are not fully detailed. The claim that the spatial data "confirms" the zonation patterns is based on visual inspection of a few genes. A more quantitative analysis, such as comparing the spatial expression gradients of eGRN target genes with the predicted zonation, would be more convincing.
        - **Why it matters** The spatial data is a key component of the "spatial multi-omics" claim in the title. If the analysis is not rigorous, the added value of this data over standard single-cell data is unclear.
        - **Resolution test** The authors should provide a more detailed and quantitative analysis of the spatial data, including a clear description of the image processing, cell segmentation, and statistical tests used to compare spatial expression patterns with the single-cell-derived zonation states.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Readability for nonspecialists
        - **Affected element** Abstract and Introduction
        - **Evidence pointer** Abstract; Main text, Introduction.
        - **Issue** The abstract and introduction are dense with jargon (e.g., "eGRNs," "topics," "zonation") without sufficient context for a general scientific audience. The significance of liver zonation and the concept of enhancer-driven gene regulation could be introduced more clearly.
        - **Required correction** Briefly explain what liver zonation is and why it is biologically important. Define "enhancer" and "gene regulatory network" in accessible terms.
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Technical soundness
        - **Affected element** Methods: MPRA data analysis
        - **Evidence pointer** Methods: MPRA data analysis.
        - **Issue** The statistical model used to call active versus inactive enhancers from the MPRA data is not fully described. The text mentions a Gaussian fit on shuffled controls, but the exact model and how the log2 fold change is calculated and thresholded is unclear.
        - **Required correction** Provide a more detailed description of the statistical analysis, including the model, the thresholding criteria, and how the false discovery rate is controlled.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Scientific importance
        - **Affected element** Discussion
        - **Evidence pointer** Main text, Discussion.
        - **Issue** The discussion of the limitations of the study is brief. The authors do not discuss the potential for false positives in the eGRN inference, the limitations of the in vitro models (HepG2, AML12), or the generalizability of the findings to other species or liver pathologies.
        - **Required correction** Expand the discussion of limitations to include these points, which will help readers interpret the findings appropriately.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1 (DeepLiver reproducibility)
    - R1-M2 (Direct evidence for repressor mechanism)
- **Assessment against Nature-style criteria**
    - **Originality** High. The combination of single-cell multi-omics, spatial transcriptomics, and deep learning to dissect enhancer-driven GRNs in a tissue context is novel. The identification of TCF7L1 and TBX3 as zonation-specific repressors is a new finding.
    - **Scientific importance** High. The work provides a mechanistic understanding of how liver zonation is encoded at the level of enhancer regulation. The resource and the DeepLiver model will be of broad utility.
    - **Interdisciplinary readership** Moderate to High. The topic is of interest to cell biologists, developmental biologists, and computational biologists. The deep learning aspect may attract a broader computational audience, but the dense presentation may limit accessibility.
    - **Technical soundness** Moderate. The multi-omic data generation and initial analyses appear sound. However, the lack of detail on the deep learning model and the incomplete evidence for direct repression are significant technical weaknesses that need to be addressed.
    - **Readability for nonspecialists** Low to Moderate. The manuscript is written for a specialist audience and would benefit from clearer explanations of key concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially important, but the manuscript requires substantial revisions to improve reproducibility, strengthen the mechanistic claims, and enhance accessibility before it can be considered for publication.

## Risk / unsupported claims
- The claim that TCF7L1 and TBX3 "directly" repress zonation-specific enhancers is not fully supported by the data presented. The evidence is correlative and based on computational predictions and indirect functional assays.
- The claim that DeepLiver can "decode" enhancer grammar and predict the effect of mutations is supported by correlations, but the predictive power is not demonstrated to be superior to simpler models, and the model's generalizability is not tested.
- The claim that the spatial data provides a "spatial multi-omics" view is not fully supported by the analysis presented, which appears to be a limited validation of the single-cell data.
- The generalizability of the findings to female mice, other strains, or pathological conditions is not assessed, despite the authors noting that their core GRNs are not affected by sex.