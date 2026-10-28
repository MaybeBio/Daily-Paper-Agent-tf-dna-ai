## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, and conceptual advance of the claims as presented in the provided text
- **Shared manuscript claim summary** The authors generate a kinetic multi-omic dataset in LNCaP cells following androgen stimulation and integrate these data into a graph-based regulatory network. They report that AR binding induces sequential epigenetic changes at enhancers, does not rewire chromatin loops but increases contact frequency of pre-existing loops, and that gene expression correlates with contact frequency changes. They propose and validate an "unbalanced multi-enhancer model" where dominant enhancers with the largest contact frequency changes have the greatest impact on target gene expression.
- **Visible evidence base** Main figures 1–6 (legends only), supplementary figure legends, methods text, and discussion
- **Missing materials affecting confidence** Actual data values, statistical outputs, quality control metrics, replicate information, and full supplementary data files were not available for assessment

## Reviewer

### Overall assessment
This manuscript addresses a fundamental question in transcriptional regulation: how multiple enhancers coordinately regulate target gene expression upon a transcription factor stimulus. The authors generate a substantial multi-omic dataset and apply a network-based framework to integrate these layers. The central claims, that AR binding does not rewire chromatin architecture but rather modulates contact frequency of pre-existing loops, and that enhancer contributions are heterogeneous and proportional to contact frequency, are potentially important. However, the strength of the conclusions depends heavily on analytical choices and statistical rigor that cannot be fully evaluated from the provided text. The CRISPRi validation is a commendable addition that strengthens the causal claims. The work is likely of interest to researchers in nuclear receptor biology, gene regulation, and chromatin structure, but several technical concerns need to be addressed before the case is fully established.

### Who would be interested in the results, and why
Researchers studying nuclear receptor biology, particularly androgen receptor function in prostate cancer, will find this directly relevant. The broader gene regulation community, especially those interested in enhancer-promoter communication, chromatin looping dynamics, and multi-enhancer integration, will also be interested. The methodological framework combining multi-omics with graph-based network analysis may appeal to computational biologists developing integrative approaches. The finding that pre-existing chromatin loops are modulated rather than rewired has implications for understanding how transcription factors achieve specificity and could inform therapeutic strategies targeting enhancer function.

### Major Strengths
1. The generation of a comprehensive kinetic multi-omic dataset (RNA-seq, ATAC-seq, ChIP-seq for multiple factors, HiChIP, and Start-seq) across five time points represents a substantial resource for the field.
2. The integration of these diverse data types into a graph-based regulatory network provides a principled framework for quantitative analysis of enhancer-promoter interactions.
3. The distinction between chromatin loop rewiring versus modulation of contact frequency is an important conceptual contribution that addresses a controversial area in the field.
4. The CRISPRi-based experimental validation of the "dominant enhancer" model provides causal evidence that strengthens the correlative findings.
5. The observation that epigenetic changes occur at all AR-bound enhancers regardless of gene expression direction, while contact frequency changes are selective, is an interesting dissociation that may have broader implications.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Statistical rigor
- **Claim pointer** The authors claim that AR binding "increases the contact frequency of pre-existing loops to target promoters" and that this change is significant and specific to AR-regulated genes.
- **Evidence pointer** Figure 3C–E, Methods: "Calculation of chromatin contact frequency change"
- **Concern** The statistical framework for assessing contact frequency changes is not fully described. The authors use a bootstrapping approach with 1000 iterations, but the details of how significance is determined, how multiple testing is corrected for across the large number of loops tested, and how the random gene sets are matched to the target gene set (beyond expression level) are not provided. The choice of seed values and the stability of the results across different seeds are also not discussed. Given that the central claim of the paper rests on these comparisons, the statistical rigor needs to be clearly established.
- **Why it matters** If the significance thresholds or the matching of control gene sets are not appropriately rigorous, the observed differences in contact frequency could be artifacts of the analytical approach rather than genuine biological phenomena. This would undermine the primary conclusion of the paper.
- **Resolution test** Provide a detailed description of the statistical testing procedure, including how the null distribution is generated, how multiple testing is controlled, and how the random gene sets are matched on relevant covariates (e.g., genomic distance to enhancers, chromatin state, baseline expression). Demonstrate that the results are robust to different seeds and matching strategies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Data quality
- **Claim pointer** The authors state that "AR binding induces sequential changes in the epigenetic features at CREs, independent of gene expression" and describe a temporal cascade of AR, FOXA1, H3K27ac, and chromatin accessibility changes.
- **Evidence pointer** Figure 2A–B, Methods: "Epigenetic changes of CREs and kinetic changes of enhancers of AR-regulated genes"
- **Concern** The description of the "sequential" nature of epigenetic changes is based on comparing the timing of peak signals across different marks. However, the resolution of the time points (0m, 30m, 4h, 16h, 72h) is coarse, and the statistical comparison of timing across marks is not described. It is unclear whether the apparent sequence (AR/FOXA1 first, then H3K27ac, then accessibility) is statistically significant or simply reflects differences in antibody quality, ChIP efficiency, or signal-to-noise ratios across the different assays. Additionally, the claim that these changes are "independent of gene expression" is based on comparing enhancers linked to up- versus down-regulated genes, but the statistical power for this comparison is not discussed.
- **Why it matters** The temporal ordering of epigenetic events is a key part of the proposed model. If the ordering is not robustly established, the mechanistic interpretation of the data is weakened. The claim of independence from gene expression direction is also important for the model, as it suggests that epigenetic changes alone do not determine transcriptional outcomes.
- **Resolution test** Provide statistical tests comparing the timing of peak signals across marks, with appropriate error estimates. Include power calculations for the comparison of enhancers linked to up- versus down-regulated genes. If the temporal ordering is not statistically robust, temper the language accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Data interpretation
- **Claim pointer** The authors propose an "unbalanced multi-enhancer model" where "the impact on gene expression of AR-bound enhancers is heterogeneous, and is proportional to their contact frequency with target gene promoters."
- **Evidence pointer** Figure 5A–D, Figure 6A–B, Methods: "Contact frequency, expression correlation", "Random forest regressor", "Gini index analysis"
- **Concern** The model is tested using three summary statistics (average, maximum, sum) of contact frequency to predict expression. The finding that sum and maximum outperform average is interpreted as evidence for a "dominant" enhancer. However, the distinction between these models is subtle, and the biological interpretation may be confounded by the fact that genes with more enhancers will trivially have higher sum values. The Gini index analysis shows inequality in contact frequencies, but the threshold for "dominance" is not defined. The CRISPRi validation targets only a small number of enhancers (n=20 across 6 genes), and the criteria for selecting these enhancers for perturbation are not fully clear. The correlation between CRISPRi effect and contact frequency change (Figure 6B) is presented, but the effect sizes and confidence intervals are not provided in the text.
- **Why it matters** The proposed model is a central conceptual contribution of the paper. If the model is not rigorously distinguished from alternative explanations (e.g., additive effects of many weak enhancers), or if the validation is limited in scope, the strength of the claim is not fully supported.
- **Resolution test** Provide a more rigorous model comparison, including cross-validation or information criteria, to distinguish between the proposed models. Clearly define the criteria for "dominant" enhancers. Expand the CRISPRi validation or provide a clear rationale for why the selected enhancers are representative. Report effect sizes and confidence intervals for the CRISPRi experiments.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Conceptual advance
- **Claim pointer** The authors state that "AR does not induce new chromatin loops, but instead increases the contact frequency between gene promoters and selective AR-bound enhancers."
- **Evidence pointer** Figure 3A–E, Supplementary Figure 6
- **Concern** The claim that no new loops are formed is based on comparing loop calls at each time point and finding few overlapping loops. However, the authors acknowledge that this could be due to "loop calling methodologies and experimental noise." They then use a reference loop set merged across time points. This approach is reasonable, but it means that the claim of "no new loops" is not directly tested. The possibility that AR induces weak or transient new loops that are below the detection threshold of the current analysis cannot be excluded. The distinction between "increased contact frequency" and "new loop formation" may be a matter of degree rather than kind.
- **Why it matters** The claim that AR does not rewire chromatin architecture is presented as a key finding. If this claim is overstated, it could mislead the field about the plasticity of chromatin interactions.
- **Resolution test** Provide a more direct test of new loop formation, such as comparing contact matrices at high resolution or using a different loop-calling approach that is more sensitive to weak interactions. Alternatively, temper the claim to state that no substantial rewiring was detected within the limits of the assay.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Methods: "CRISPRi"
- **Evidence pointer** Methods: "CRISPRi"
- **Issue** The description of the CRISPRi experiments is brief. The number of guide RNAs per enhancer, the number of biological replicates, and the specific qRT-PCR assays used are not fully detailed.
- **Required correction** Provide a more complete description of the CRISPRi experimental design, including the number of guides, replicates, and the specific primers used for each gene.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity / Data presentation
- **Affected element** Figure 3F
- **Evidence pointer** Figure 3F legend
- **Issue** The figure legend describes a "min-max normalized standard deviation" for multiple features across six genes. It is unclear how the standard deviation is calculated across time points and how the min-max normalization is applied across features with different scales.
- **Required correction** Clarify the calculation and normalization procedure in the figure legend or methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness / Data analysis
- **Affected element** Methods: "Annotation of cis-regulatory elements/defining background genes"
- **Evidence pointer** Methods: "Annotation of cis-regulatory elements/defining background genes"
- **Issue** The definition of AR-regulated genes relies on the MSigDB HALLMARKS_ANDROGEN_RESPONSE gene set. The overlap between this gene set and the genes identified as differentially expressed in the authors' own RNA-seq data is not described.
- **Required correction** Provide a comparison between the MSigDB gene set and the authors' own differential expression analysis to justify the use of this gene set.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Methods: "HiC combined with capture ChIP-seq (HiChIP)"
- **Evidence pointer** Methods: "HiC combined with capture ChIP-seq (HiChIP)"
- **Issue** The number of biological replicates for the HiChIP experiments is not stated. The text mentions "one replicate for each broad and narrow peak" for H3K4me3, but the overall replicate structure is unclear.
- **Required correction** Clearly state the number of biological replicates for each assay and time point.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity / Data interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the "activity-by-contact (ABC) model" is brief. A more explicit comparison between the proposed model and the ABC model would help position the work in the context of existing frameworks.
- **Required correction** Expand the discussion of how the proposed model relates to and differs from the ABC model.

### Technical failings that need to be addressed before the case is established
- R1-M1: Statistical framework for contact frequency changes is not fully described
- R1-M2: Temporal ordering of epigenetic changes is not statistically validated
- R1-M3: Model selection and validation for the "dominant enhancer" model is incomplete

### Assessment against Nature-style criteria
- **Originality** The work is original in its integration of multiple omics layers into a network framework to study enhancer dynamics. The specific finding that AR modulates contact frequency of pre-existing loops rather than rewiring chromatin architecture adds a new perspective to the field. However, the concept of "dominant" enhancers has precedents in the literature, and the novelty lies primarily in the systematic quantification.
- **Scientific importance** The question of how multiple enhancers coordinate to regulate gene expression is of fundamental importance. The findings have potential implications for understanding androgen receptor function in prostate cancer and for the broader field of transcriptional regulation. The dataset itself is a valuable resource.
- **Interdisciplinary readership** The work bridges cancer biology, chromatin structure, and computational biology. The network-based approach may appeal to a broad audience, but the technical complexity of the analyses may limit accessibility to non-specialists.
- **Technical soundness** The experimental methods are generally sound, and the generation of a multi-omic dataset is commendable. However, the statistical rigor of the key analytical comparisons needs to be strengthened, as detailed in the major concerns. The CRISPRi validation is a strength, but its scope is limited.
- **Readability for nonspecialists** The manuscript is generally well-written, but the results section is dense and assumes significant background knowledge. The figures are complex and may be difficult for non-specialists to interpret. The abstract and introduction are accessible, but the results and discussion would benefit from additional context and clearer explanations of the analytical approaches.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses an important question and presents a substantial dataset with a potentially valuable conceptual framework. However, the statistical rigor of the key claims needs to be strengthened, and the model validation needs to be more complete. If these concerns are adequately addressed, the work would be a significant contribution to the field.

## Risk / unsupported claims
- The claim that AR binding does not induce new chromatin loops is not directly tested and may be overstated given the limitations of the loop-calling approach.
- The claim that epigenetic changes are "independent of gene expression" is based on a comparison with limited statistical power that is not fully described.
- The "unbalanced multi-enhancer model" is supported by correlative analyses and a limited CRISPRi validation; the generalizability of the model beyond the tested genes is not established.
- The statement that "the same enhancer typically had both the highest change in epigenetic features and contact frequency" (Figure 3F) is based on a small number of genes and lacks statistical testing.
- The claim that the findings "develop a mechanistic framework to investigate nuclear receptor mediated perturbations" is aspirational and not directly supported by the data presented.