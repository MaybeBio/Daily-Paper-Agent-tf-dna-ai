## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supplementary figure/table references
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to presented evidence, and clarity of presentation. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors present a deep learning framework (eMotif-RE) that identifies transcription factor motifs enriched in active versus non-active enhancer sets derived from ATAC-seq and H3K27ac ChIP-seq data during human embryonic stem cell differentiation into GABAergic-like interneurons. They report ASCL1 and SOX4/11 motif enrichment in active enhancers, ZEB1, CTCF, NEUROG2, and NR2F1 motif enrichment in non-active enhancers, and functional validation of two non-active enhancers as repressed elements via zebrafish assays with motif deletion.
- **Visible evidence base** Main text figures (Figures 1-6), supplementary figures S1-S4, supplementary tables S1-S10, methods descriptions for computational and experimental procedures
- **Missing materials affecting confidence** Raw sequencing data not directly inspected (GEO accession provided but not accessed), supplementary tables S1-S10 not provided in the submitted material, detailed hyperparameter search results not shown, complete TF-MoDISco output parameters not specified, statistical details of enhancer assay quantification not fully described

## Reviewer

### Overall assessment
The manuscript addresses a relevant question in neurodevelopmental gene regulation by applying deep learning to classify enhancer states and discover transcription factor motifs. The integration of computational prediction with in vivo validation is commendable. However, the evidence presented does not fully establish several key claims. The distinction between "non-active enhancers" and other regulatory element classes is not rigorously defined, the statistical framework for motif enrichment is incompletely described, and the functional validation is limited to two elements with modest effect sizes. The claim of a "novel framework" requires clearer benchmarking against existing methods beyond what is shown. The manuscript would benefit from more rigorous quantitative analysis and clearer presentation of validation statistics.

### Who would be interested in the results, and why
Researchers studying transcriptional regulation during neurogenesis, particularly those focused on interneuron development and the roles of ASCL1, SOX4/11, ZEB1, and CTCF. The computational approach may interest bioinformaticians developing deep learning methods for regulatory genomics. Clinicians and geneticists studying neurodevelopmental disorders may find relevance given the connection to epilepsy and autism-associated genes, though this connection is not deeply explored.

### Major strengths
- Integration of multiple epigenetic datasets (ATAC-seq, H3K27ac, H3K27me3) to define enhancer states
- Combination of deep learning classification with interpretability methods (Integrated Gradients, TF-MoDISco) for motif discovery
- Inclusion of in vivo functional validation via zebrafish enhancer assays
- Comparison with established motif discovery tools (MEME, DREME, BaMM)
- Clear presentation of the computational pipeline and availability of code

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their framework identifies "enriched motifs" in active and non-active enhancer sets, and that these motifs correspond to functionally relevant transcription factors.
- **Evidence pointer** Results section "A novel framework for enriched motifs in regulatory elements (eMotif-RE) discovers neuronal TF motifs in putative non-active enhancers"; Figure 3; Supplementary Tables S3-S5
- **Concern** The statistical framework for determining motif enrichment is not adequately described. The authors state that AME was used to test enrichment, but the specific methodology for how the deep learning-derived motifs were converted to position weight matrices and tested for enrichment is unclear. The criteria for filtering spurious motifs (bias, length, stringency, correspondence, overlap, q-value, differential expression) are listed but the thresholds and their justification are not fully explained. The q-value threshold of 0.05 is mentioned but the multiple testing correction approach is not described.
- **Why it matters** Without a clear statistical framework, the central claim of identifying enriched motifs cannot be evaluated. The filtering criteria appear to be applied post hoc and may introduce bias. The differential expression filter (2-fold change) is particularly concerning as it may exclude legitimate motifs for transcription factors that are not differentially expressed but are constitutively active.
- **Resolution test** Provide a complete description of the statistical testing procedure, including how motifs were derived from TF-MoDISco output, how enrichment was calculated, what background model was used, and how multiple testing was addressed. Show the number of motifs identified at each filtering step and justify each threshold.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the non-active enhancer set represents "poised/repressed enhancers and putative silencers" and that the identified motifs in this set have repressive function.
- **Evidence pointer** Results section "Determining putative active and non-active enhancers in MGE-like progenitors"; Figure 2A; Methods section "Data pre-processing and filtering"
- **Concern** The definition of "non-active enhancers" is problematic. The authors define these as open chromatin regions without H3K27ac, but this category could include many regulatory element types, including promoters, insulators, and uncharacterized regions. The use of REPTILE trained on mouse embryonic stem cell data with only H3K27ac as the functional mark is a significant limitation. The authors acknowledge the lack of methylation data but do not address how this affects the reliability of the classification. The term "non-active enhancer" is used interchangeably with "poised/repressed enhancer" and "silencer" without clear operational definitions.
- **Why it matters** The classification of regulatory elements is foundational to all subsequent analyses. If the non-active set is heterogeneous, the motif enrichment results may reflect different regulatory mechanisms. The claim that ZEB1 and CTCF motifs are enriched in "repressed enhancers or silencers" requires that the non-active set be more rigorously defined.
- **Resolution test** Provide a more detailed characterization of the non-active enhancer set, including genomic distribution, overlap with known regulatory elements, and comparison with established enhancer databases. Justify the use of REPTILE with limited input features and discuss how this may affect classification accuracy. Consider validating the classification with additional marks (e.g., H3K4me1, H3K4me3) or functional assays.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that their results "elucidated novel functions of TFs and their corresponding REs" and that the approach "can be applied to better understand gene regulation not only in inhibitory interneuron differentiation but in other tissue and cell types."
- **Evidence pointer** Abstract; Discussion section
- **Concern** The novelty of the findings is not clearly established. The transcription factors identified (ASCL1, SOX4, SOX11, ZEB1, CTCF, NEUROG2, NR2F1) are all well-known regulators of neurogenesis with established roles. The claim of "novel functions" is supported only by the enhancer assay data for two elements, which shows modest effects. The broader applicability claim is speculative and not demonstrated.
- **Why it matters** The scientific importance of the work depends on whether it provides new biological insights beyond what is already known about these transcription factors. If the framework merely recapitulates known biology, the contribution is primarily methodological.
- **Resolution test** Clearly articulate what specific new biological insights are provided. Compare the identified motifs and regulatory elements with existing databases and publications to demonstrate novelty. Provide evidence that the framework identifies elements or mechanisms not discoverable by existing methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the deep learning model "performed much better than a linear-regression model" and that the framework is superior to established motif discovery methods.
- **Evidence pointer** Results section "A novel framework for enriched motifs in regulatory elements (eMotif-RE)"; Supplementary Figure S3; Supplementary Table S5
- **Concern** The comparison with other methods is not presented in sufficient detail. The authors state that DREME, MEME, and BaMM "found only spurious motifs or detected only the ZEB1 motif among a long list of spurious motifs," but the specific results are not shown. The performance metrics for the deep learning model versus the linear regression model are not provided. The hyperparameter search is mentioned but the results are not shown.
- **Why it matters** The claim of methodological superiority requires rigorous benchmarking. Without detailed comparison results, the reader cannot evaluate whether the deep learning approach provides genuine advantages over existing methods.
- **Resolution test** Provide a comprehensive benchmarking analysis showing the performance of all methods on the same datasets, including precision, recall, and false discovery rates. Show the hyperparameter search results and justify the final model choices. Include runtime and computational cost comparisons.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "deletions of ZEB1 and CTCF binding sites increase the RE1 and RE6 activity in this assay suggesting that these open chromatin regions might function as repressed enhancers."
- **Evidence pointer** Results section "Deletions of ZEB1 and CTCF predicted binding motifs increased the activity of their targeted regulatory elements"; Figure 6; Table 1
- **Concern** The functional validation is limited to two elements (RE1 and RE6) out of eight tested. The effect sizes are described as "6-fold" and "2-fold" increases, but the statistical significance of these differences is not reported. The number of embryos and replicates is not specified in the main text. The specificity of the effect is not demonstrated, as no control elements with mutations in non-ZEB1/CTCF regions are shown.
- **Why it matters** The functional data is the primary evidence for the biological relevance of the identified motifs. Without proper statistical reporting and appropriate controls, the conclusion that these elements function as repressed enhancers is not fully supported.
- **Resolution test** Report the number of embryos, replicates, and statistical tests for all enhancer assay experiments. Include control experiments with mutations in regions not predicted to bind ZEB1 or CTCF. Show the full quantification data for all eight tested elements, including those that did not show enhancer activity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2
- **Evidence pointer** Figure 2
- **Issue** The schematic of the eMotif-RE framework is complex and difficult to follow. The relationship between the different components (REPTILE, CNN training, Integrated Gradients, TF-MoDISco, post-analysis) is not immediately clear.
- **Required correction** Simplify the figure or add a more detailed legend that walks the reader through each step of the pipeline.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Deep neural network architecture"
- **Evidence pointer** Methods section "Deep neural network architecture"
- **Issue** The description of the CNN architecture lacks specific details on the number of layers, filter sizes, pooling strategies, dropout rates, and other hyperparameters. The code is available on GitHub, but the manuscript should be self-contained.
- **Required correction** Provide a complete description of the network architecture and training procedure in the main text or supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Determining putative active and non-active enhancers in MGE-like progenitors"
- **Evidence pointer** Results section "Determining putative active and non-active enhancers in MGE-like progenitors"; Supplementary Figure S2
- **Issue** The GC content comparison between active and non-active enhancers reports p-values from Wilcoxon rank-sum tests but does not report effect sizes or confidence intervals.
- **Required correction** Report median differences and confidence intervals in addition to p-values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the potential role of ZEB1 and CTCF as repressors in this context is speculative and not well integrated with the existing literature on these factors.
- **Required correction** Provide a more focused discussion that connects the findings to specific published evidence on ZEB1 and CTCF function in neurogenesis.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary Tables
- **Evidence pointer** Supplementary Tables S1-S10
- **Issue** The supplementary tables are referenced throughout but were not provided with the manuscript. The reader cannot verify the complete lists of enhancers, motifs, and primer sequences.
- **Required correction** Ensure all supplementary tables are available and clearly formatted with descriptive headers and legends.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Methods section "Site-directed mutagenesis by overlap extension using the polymerase chain reaction"
- **Evidence pointer** Methods section "Site-directed mutagenesis by overlap extension using the polymerase chain reaction"
- **Issue** The description of the mutagenesis procedure is brief and lacks details on the PCR conditions, primer design, and verification of mutations beyond Sanger sequencing.
- **Required correction** Provide additional details on the mutagenesis protocol, including PCR cycling conditions and the number of clones screened.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "most of the tested putative REs from the non-active enhancer set have no enhancer activity" but does not specify the exact numbers or the criteria for "no activity."
- **Required correction** Include the specific numbers (e.g., "six of eight") and define the threshold for positive enhancer activity.

### Technical failings that need to be addressed before the case is established
- The statistical framework for motif enrichment is incompletely described, preventing evaluation of the central claim (R1-M1)
- The definition and characterization of "non-active enhancers" is insufficient to support the interpretation of these elements as poised/repressed enhancers or silencers (R1-M2)
- The benchmarking against existing methods is not presented in sufficient detail to support the claim of methodological superiority (R1-M4)
- The functional validation data lacks proper statistical reporting and appropriate controls (R1-M5)

### Assessment against Nature-style criteria
- **Originality**: Moderate. The application of deep learning to enhancer classification during interneuron differentiation is a reasonable extension of existing approaches, but the individual components (CNN classification, Integrated Gradients, TF-MoDISco) are established methods. The specific combination and application context provide some novelty, but the biological findings largely recapitulate known roles of the identified transcription factors.
- **Scientific importance**: Moderate. The work addresses a relevant question in neurodevelopmental gene regulation, but the insights provided are incremental rather than transformative. The connection to disease (epilepsy, autism) is mentioned but not developed.
- **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to computational biologists and researchers in neurodevelopmental gene regulation. The presentation assumes significant familiarity with both deep learning and epigenomics.
- **Technical soundness**: The computational pipeline is reasonable but incompletely described. The statistical framework for motif enrichment needs clarification. The functional validation is limited in scope and statistical power.
- **Readability for nonspecialists**: Below average. The manuscript uses technical jargon without adequate explanation, and the figures are complex and not fully accessible to readers outside the immediate field.

### Recommendation posture
Currently not established from the provided evidence. The manuscript presents an interesting computational approach with some promising results, but the statistical framework for the central claims is incompletely described, the definition of key regulatory element classes is problematic, and the functional validation is limited. The authors should address the major concerns regarding statistical rigor, benchmarking, and validation before the case for the framework's utility and the biological conclusions can be established.

## Risk / unsupported claims
- The claim that the framework identifies "novel functions" of transcription factors is not supported by the evidence presented, as the identified factors are well-known regulators of neurogenesis
- The claim that the approach "can be applied to better understand gene regulation in other tissue and cell types" is speculative and not demonstrated
- The classification of non-active enhancers as "poised/repressed enhancers or silencers" is not rigorously supported by the data
- The claim that the deep learning model "performed much better than a linear-regression model" cannot be evaluated without performance metrics
- The statement that competing methods found "only spurious motifs" is not supported by presented data
- The functional significance of the identified motifs is only tested for two elements, limiting generalizability
- The evolutionary conservation claim for zebrafish orthologs is presented without statistical analysis or context