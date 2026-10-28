## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and supplementary figure/table legends
- **Assessment boundary** Scientific content, technical validity, and claims as presented in the provided manuscript material
- **Shared manuscript claim summary** The authors construct a dynamic regulome for 27 shoot-apical-meristem-related homeobox transcription factors (KNOX, WOX, ZF-HD subfamilies) in maize by integrating tsCUT&Tag, ATAC-seq, and expression data, and validate a predicted regulatory relationship (WOX13A-Gn1) through mutant analysis
- **Visible evidence base** Main text figures 1-7, methods section, supplementary figure and table legends (S1-S15, Tables S1-S16)
- **Missing materials affecting confidence** Raw data files, complete figure images, supplementary tables content, code availability, detailed machine-learning model architecture and hyperparameters, statistical test details for several comparisons

## Reviewer
- **Overall assessment** This manuscript presents a substantial genomic resource for maize shoot apical meristem biology, combining multiple high-throughput datasets to generate testable regulatory hypotheses. The integration of tsCUT&Tag with machine-learning approaches is methodologically interesting, and the functional validation of WOX13A-Gn1 provides a concrete example of the resource's utility. However, several technical aspects require clarification, particularly regarding the machine-learning model's generalizability, the statistical framework for defining hub genes and hot regions, and the strength of evidence for some regulatory claims. The manuscript would benefit from clearer presentation of validation metrics and more cautious interpretation of predictive results.
- **Who would be interested in the results, and why** Plant developmental biologists studying meristem function and plant architecture, maize geneticists and breeders interested in regulatory networks underlying agronomic traits, and computational biologists developing methods for transcription factor target prediction using chromatin accessibility and binding data. The resource aspect of the work (46 transcriptome, 16 translatome datasets, 27 TF regulomes) will be valuable for the maize community.
- **Major strengths** 1) The scale of the dataset collection and integration is impressive, providing a community resource. 2) The combination of tsCUT&Tag with machine-learning prediction across tissues is a novel methodological contribution. 3) The functional validation through CRISPR-generated wox13a mutant provides experimental support for the resource's predictive power. 4) The analysis of duplicated gene pairs and their regulatory divergence adds evolutionary insight.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (machine-learning model validation), R1-M2 (hub gene and hot region statistical definition), R1-M3 (WOX13A-Gn1 causal evidence)
- **Assessment against Nature-style criteria** Originality: The work is original in its scale and integration approach, though individual components (tsCUT&Tag, ATAC-seq, regulome construction) have been described elsewhere. Scientific importance: The resource has clear value for maize research and plant architecture studies, but the conceptual advance beyond existing regulome resources is incremental. Interdisciplinary readership: The work bridges genomics, computational biology, and developmental biology, with potential interest across these fields. Technical soundness: Generally sound but with concerns detailed below regarding model validation and statistical thresholds. Readability for nonspecialists: The manuscript is reasonably accessible, though the methods section assumes familiarity with multiple genomic techniques.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding machine-learning model validation and the statistical framework for defining regulatory features.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validity of machine-learning approach
- **Claim pointer** The authors claim that machine-learning models can predict TF binding sites across different tissues and stages by combining tsCUT&Tag, ATAC-seq, and expression profiling, with reported accuracy of approximately 70%
- **Evidence pointer** Methods section "Inference of an integrated transcription-regulatory network and tissue-dynamic networks"; Results section "Tissue- or stage-dynamic networks of SAM-related TFs"; Additional file 12: Table S11
- **Concern** The manuscript reports model accuracy ranging from 0.75 to 0.96 for the 27 TFs, but the training and evaluation framework is not fully described. The model is trained on etiolated seedling data (tsCUT&Tag and ATAC-seq) and then applied to predict binding in SAM based solely on ATAC-seq. The critical assumption that binding preferences learned in one tissue generalize to another is not explicitly validated. Additionally, the positive-to-negative sample ratio in training, the feature encoding scheme, and the evaluation metrics (accuracy vs. AUROC vs. AUPRC) are not specified. For imbalanced genomic data, accuracy can be misleading. The claim of approximately 70% accuracy in the discussion appears inconsistent with the 0.75-0.96 range reported in Table S11, and this discrepancy needs clarification.
- **Why it matters** The entire SAM dynamic network construction depends on the reliability of these predictions. If the model does not generalize across tissues, the predicted SAM binding sites and the resulting network may contain substantial false positives, undermining the central resource claim.
- **Resolution test** Provide detailed model architecture, training/validation split strategy, class balance information, and performance metrics including AUROC and AUPRC. Validate the cross-tissue generalizability by testing model predictions against independent ChIP-seq data for at least a subset of TFs in SAM or closely related tissues. Clarify the relationship between the reported accuracy range and the approximately 70% figure cited in the discussion.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical definition of hub genes and hot regions
- **Claim pointer** The authors define 3,168 hub target genes bound by 13 or more TFs and 3,053 hot regions bound by 12 or more TFs, based on the 99th percentile of randomized distributions
- **Evidence pointer** Results section "Target hubs and HOT regions are enriched for regulatory genes"; Additional file 8: Table S7
- **Concern** The randomization procedure for establishing the 99th percentile threshold is described only briefly. It is unclear whether the randomization preserves the genomic features of the original data (e.g., chromosome distribution, GC content, repeat content, proximity to genes). If the null model does not account for these features, the thresholds may be inappropriate. Furthermore, the manuscript does not report the distribution of the number of TFs per gene or per region, making it difficult to assess whether the 13-TF and 12-TF thresholds are reasonable or overly arbitrary. The relationship between hub genes and hot regions (2,608 of 3,168 hub targets overlap with hot regions) is presented but not deeply analyzed.
- **Why it matters** Hub genes and hot regions are presented as important features of the regulome. If their definition is statistically flawed, downstream interpretations about regulatory complexity and important nodes in the network are compromised.
- **Resolution test** Describe the randomization procedure in detail, including what features are preserved. Provide the full distribution of TF occupancy per gene and per region, and justify the chosen thresholds. Consider using multiple testing correction or alternative statistical approaches to define significance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal evidence for WOX13A-Gn1 regulation
- **Claim pointer** The authors claim that WOX13A directly regulates Gn1 expression to modulate plant height, based on the wox13a mutant phenotype and luciferase reporter assays
- **Evidence pointer** Results section "Loss of ZmWOX13A function contributes to plant-height variation in maize"; Figure 7
- **Concern** The evidence for direct regulation of Gn1 by WOX13A is based on: 1) Gn1 being among differentially expressed genes in the wox13a mutant, 2) Gn1 being a predicted target from tsCUT&Tag, and 3) a luciferase reporter assay showing activation. However, the manuscript does not demonstrate that WOX13A binds directly to the Gn1 promoter region in vivo (e.g., through an independent ChIP experiment or electrophoretic mobility shift assay). The luciferase assay shows activation in a heterologous system but does not establish direct binding. Additionally, the phenotypic analysis of the wox13a mutant is limited to plant height and ear height measurements at two locations; no data on Gn1 expression levels in the mutant versus wild type are shown in the main figures, and the magnitude of the height difference and its consistency across locations are not fully described.
- **Why it matters** The WOX13A-Gn1 module is presented as a key validation of the regulome's predictive power. If the direct regulatory relationship is not firmly established, the claim of "directly regulates" is overstated, and the validation of the resource is weakened.
- **Resolution test** Provide in vivo binding evidence (e.g., ChIP-qPCR or ChIP-seq for WOX13A in relevant tissue) showing enrichment at the Gn1 promoter. Show Gn1 expression data in the wox13a mutant versus wild type. Consider additional genetic evidence, such as rescue experiments or analysis of Gn1 expression in a tissue-specific manner. If direct binding cannot be demonstrated, revise the claim to indicate that WOX13A likely regulates Gn1 through direct or indirect mechanisms.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of tsCUT&Tag data
- **Claim pointer** The authors state that tsCUT&Tag can deduce the targets of TFs across different plant tissues and stages based on a comprehensive machine-learning model, and they use this approach to construct regulomes for 27 TFs
- **Evidence pointer** Results section "Genome-wide binding sites of maize SAM-related TFs"; Methods section "Protoplast isolation, transformation, and tsCUT&Tag assay"
- **Concern** The tsCUT&Tag experiments were performed in protoplasts derived from etiolated seedlings, which may not fully recapitulate the chromatin environment of the tissues where these TFs normally function (e.g., SAM, internodes). The manuscript does not discuss potential artifacts introduced by the protoplast isolation procedure, such as changes in chromatin accessibility or stress responses. Additionally, the number of biological replicates and the consistency of peak calling across replicates are not fully described.
- **Why it matters** If the tsCUT&Tag data are not representative of in vivo binding, the regulome may contain tissue-specific artifacts. This affects the reliability of all downstream analyses and the resource's utility.
- **Resolution test** Discuss the limitations of protoplast-based assays and provide evidence that the binding sites identified are relevant in vivo. If possible, compare a subset of tsCUT&Tag results with published ChIP-seq data for the same or closely related TFs. Provide details on replicate numbers and peak-calling consistency.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1A-C
- **Issue** The heatmap in Figure 1A uses a color scale that is not clearly defined, and the tissue labels are small and difficult to read. The statistical test used for Figure 1C is not specified in the figure legend.
- **Required correction** Add a clear color scale legend, increase font size for tissue labels, and specify the statistical test used in Figure 1C.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Incomplete methods for luciferase assays
- **Affected element** Methods section "Transient luciferase-reporter assays"
- **Evidence pointer** Methods section
- **Issue** The methods for luciferase assays do not specify the number of biological replicates, the statistical analysis used, or the normalization approach (e.g., internal control such as Renilla luciferase).
- **Required correction** Add details on replicates, normalization, and statistical analysis for the luciferase assays.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Results and Discussion sections
- **Issue** The terms "regulome," "dynamic regulome," and "integrated network" are used somewhat interchangeably, which may confuse readers about what exactly is being described in each context.
- **Required correction** Define these terms clearly at first use and use them consistently throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Missing discussion of false positive rate
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion acknowledges the possibility of false positives in the regulome but does not provide an estimate of the expected false discovery rate or discuss how users of the resource should interpret predicted targets that are not experimentally validated.
- **Required correction** Add a brief discussion of expected false positive rates and provide guidance for users on how to prioritize predicted targets for validation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability statement
- **Affected element** Data availability
- **Evidence pointer** Not explicitly stated in the provided material
- **Issue** The manuscript does not include an explicit data availability statement describing where raw sequencing data, processed data, and code can be accessed.
- **Required correction** Add a data availability statement with accession numbers for all raw and processed data, and a link to any deposited code.

## Risk / unsupported claims
- The claim that WOX13A "directly regulates" Gn1 expression is not fully supported by the evidence presented, as no in vivo binding data are shown
- The claim that the machine-learning model can predict TF binding sites across tissues with approximately 70% accuracy is not clearly reconciled with the reported accuracy range of 0.75-0.96
- The statement that the regulome "presents an unprecedented opportunity" is somewhat overstated given existing regulome resources in other species
- The claim that hub genes and hot regions are "enriched for regulatory genes" relies on GO enrichment analysis, but the statistical framework and multiple testing correction are not fully described
- The generalizability of tsCUT&Tag results from protoplasts to intact tissues is assumed but not explicitly validated