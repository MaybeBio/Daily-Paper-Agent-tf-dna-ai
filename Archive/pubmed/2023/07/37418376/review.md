## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, and methods
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to evidence presented, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors integrate RNA-seq transcriptomics, DAP-seq, and deep learning (CRNN) to infer gene regulatory networks in soybean upon infection by Phytophthora sojae, identifying WRKY and RAV transcription factors as central hubs and proposing cross-species predictive utility of Arabidopsis-trained models
- **Visible evidence base** RNA-seq differential expression (6,042 DEGs), DAP-seq for GmWRKY30 and GmRAV, AmpDAP-seq for GmWRKY2 and GmMYB61, CRNN performance metrics (accuracy, false positive rates), FIMO overlap, hub node prioritization metrics, GO/KEGG enrichment
- **Missing materials affecting confidence** Raw sequencing data, DAP-seq peak files, model architecture code, hyperparameter details, validation on independent biological replicates, functional validation of predicted targets, statistical details for hub prioritization thresholds, and supplementary figures/tables referenced but not fully described

## Reviewer
- **Overall assessment** The manuscript presents a novel integration of transcriptomic and DAP-seq data with deep learning to construct gene regulatory networks in the soybean-P. sojae pathosystem. The conceptual approach is timely and the generation of new DAP-seq data for GmWRKY30 is a valuable contribution. However, several methodological gaps and overinterpretations weaken the central claims. The cross-species prediction results show modest accuracy, and the biological validation of predicted regulatory interactions is absent. The hub node prioritization relies on correlational metrics without functional confirmation. While the work has potential, the current evidence does not fully establish the claimed regulatory network or its utility for breeding durable resistance.
- **Who would be interested in the results, and why** Plant pathologists studying oomycete diseases, soybean geneticists and breeders seeking molecular targets for resistance, computational biologists developing deep learning approaches for regulatory genomics, and researchers interested in cross-species TF binding prediction. The DAP-seq dataset for GmWRKY30 and the CRNN framework could serve as resources for similar studies in other crops.
- **Major strengths** 1) First comparative transcriptomic study of compatible and incompatible soybean-P. sojae interactions within a single genotype. 2) Generation of novel DAP-seq data for GmWRKY30, a defense-associated TF. 3) Demonstration that CRNNs trained on one TF can predict binding sites for other family members with reasonable accuracy. 4) Integration of multiple data types (expression, binding, motif, co-occurrence) for network inference. 5) Transparent discussion of limitations including temporal resolution and inoculation artifacts.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that CRNN models can predict TF binding sites for other members of the same family with "reasonable accuracy" and use this to justify cross-species predictions
  - **Evidence pointer** Results section "DNN prediction of TFBS", Tables 1-4, Figure 5
  - **Concern** The generalization testing is circular. The GmWRKY30 model is tested on GmWRKY2, but both are WRKY family members with potentially similar binding preferences. The modest accuracy (82%) for intraspecies prediction and 61% for cross-species prediction raises questions about whether the models are learning genuine TF-specific binding rules or generic sequence features. The authors do not compare against simpler baseline methods (e.g., position weight matrix scanning, k-mer based classifiers) to demonstrate that the CRNN adds predictive value beyond existing approaches. Additionally, the cross-species prediction accuracy of approximately 60% is barely above chance for a binary classification and may not justify the claim of successful cross-species transfer.
  - **Why it matters** The central methodological contribution is the deep learning approach for TFBS prediction. If the models do not outperform simpler alternatives or if the generalization is not robust, the entire network inference pipeline is undermined. The cross-species claim is a key novelty and requires stronger evidence.
  - **Resolution test** Provide baseline comparisons (e.g., FIMO alone, simple k-mer SVM) and statistical significance testing for accuracy improvements. Validate cross-species predictions with independent experimental data (e.g., electrophoretic mobility shift assay or reporter assays for a subset of predicted targets). Report precision-recall curves and area under the curve for cross-species predictions, not just accuracy and false positive rate.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence strength
  - **Claim pointer** The authors claim that hub nodes (13 genes encoding 14 TFs) are "core components of the defense-growth tradeoff in soybean" based on network centrality and target annotation
  - **Evidence pointer** Results section "GRN inference underpinning host defense", Figure 6
  - **Concern** The hub node identification relies on degree centrality, co-occurrence, and expression, but these are purely computational metrics without functional validation. The claim that hubs regulate the defense-growth tradeoff is speculative. The authors note that 62% of hub targets have primary metabolism annotations, but this could reflect the overall gene pool composition rather than specific hub function. No experimental evidence (e.g., overexpression, knockdown, or mutant analysis) is provided to support the regulatory role of these hubs. The network itself is static and inferred from a single time point (24 hpi), limiting causal inference.
  - **Why it matters** The biological significance of the network depends on the validity of hub identification. Without functional validation, the hubs remain computational predictions, and the claim about the defense-growth tradeoff is unsupported.
  - **Resolution test** Perform targeted validation of at least 2-3 hub TFs (e.g., virus-induced gene silencing or stable transformation in soybean) to assess impact on P. sojae resistance and expression of predicted targets. Alternatively, compare hub predictions against published mutant or overexpression phenotypes for orthologous genes in Arabidopsis or other species.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The authors describe a complex bioinformatics pipeline involving RNA-seq, DAP-seq, CRNN training, FIMO scanning, and network construction
  - **Evidence pointer** Methods section, Tables 1-3, Figure 4
  - **Concern** Critical methodological details are missing. The CRNN architecture is described at a high level, but hyperparameters (learning rate schedule, batch size rationale, early stopping criteria, number of training epochs) are incomplete. The data splitting strategy (e.g., chromosome-level holdout to prevent data leakage) is not described. The threshold for considering a gene a "target" (at least one positive window) is extremely permissive and likely inflates the number of predicted targets. The FIMO overlap procedure is described but the stringency of overlap criteria is unclear.
  - **Why it matters** Reproducibility is a core requirement for computational studies. Without complete methodological details, other researchers cannot replicate or build upon this work. The permissive target definition could lead to a high false positive rate in the final network.
  - **Resolution test** Provide full model architecture details, hyperparameter values, and data splitting strategy in supplementary materials. Report the distribution of positive windows per gene and justify the target calling threshold. Make code and processed data publicly available.

- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 2D description
  - **Evidence pointer** Results section "Transcriptome analysis and virulence screening"
  - **Issue** The description of K-means clustering results is brief. The authors state that clusters 1, 2, 4, 5, 7, 8, and 9 are "up-regulated clusters" but do not specify the number of genes per cluster or the statistical criteria for cluster assignment.
  - **Required correction** Provide cluster sizes and a brief description of cluster-specific expression patterns to aid interpretation.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Hypergeometric enrichment test
  - **Evidence pointer** Results section "Identification of defense-related TF families"
  - **Issue** The hypergeometric test for TF family enrichment is mentioned, but the multiple testing correction is not described.
  - **Required correction** State whether and how p-values were corrected for multiple comparisons across TF families.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Supplementary data
  - **Evidence pointer** Methods section, Supplementary information
  - **Issue** The manuscript references multiple supplementary tables and figures, but their content is not described in the text.
  - **Required correction** Add a brief description of each supplementary item in the main text or a supplementary file legend.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of compatible vs incompatible responses
  - **Evidence pointer** Discussion section
  - **Issue** The authors suggest that overlapping expression profiles between compatible and incompatible interactions may reflect PTI signatures, but this interpretation is not directly tested.
  - **Required correction** Soften the language or suggest a specific test (e.g., comparison with known PTI marker genes) to support this claim.

- **Technical failings that need to be addressed before the case is established** R1-M1 (baseline comparisons and statistical rigor for CRNN generalization), R1-M2 (functional validation of hubs), R1-M3 (reproducibility details)

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The integration of DAP-seq with deep learning for GRN inference in a crop pathosystem is novel, but the individual components (transcriptomics, DAP-seq, CRNN) are established. The cross-species prediction angle adds originality.
  - Scientific importance: Moderate. The work addresses a significant disease and provides a framework that could be applied to other systems. However, the lack of functional validation limits the immediate impact on understanding soybean immunity.
  - Interdisciplinary readership: Limited. The work is primarily relevant to plant pathologists and computational biologists. The deep learning aspects may attract a broader audience, but the biological context is specialized.
  - Technical soundness: Weak. The CRNN evaluation lacks baseline comparisons and statistical rigor. The network inference pipeline has potential circularity issues and permissive thresholds. Reproducibility is compromised by missing methodological details.
  - Readability for nonspecialists: Adequate. The manuscript is generally well-written, but the methods section assumes familiarity with deep learning and genomics. The abstract and introduction are accessible.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising framework but requires substantial revisions to address the technical concerns, particularly baseline comparisons for the deep learning models, functional validation of hub predictions, and complete methodological transparency. If these issues are resolved, the work could be suitable for publication in a specialized journal, though it may not meet the broad impact bar for Nature.

## Risk / unsupported claims
- The claim that CRNN models can generalize across TF families is supported only by accuracy metrics without baseline comparisons or statistical testing
- The claim that hub nodes regulate the defense-growth tradeoff is unsupported by functional evidence
- The claim that cross-species prediction from Arabidopsis to soybean is successful is based on approximately 60% accuracy, which is not convincingly above chance
- The statement that GmWRKY30 regulates other TFs and signaling components is inferred from binding data alone without expression validation
- The suggestion that differential methylation during infection prevents autoimmunity is speculative and not directly tested
- The claim that the study provides "novel insight into molecular plant-pathogen interaction" is overstated given the lack of functional validation