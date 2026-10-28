## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors propose that RBPJ binding sites can be classified as "static" or "dynamic" based on their response to Notch pathway inhibition, and that dynamic sites, characterized by distal enhancer positioning and stronger binding, are predictive of Notch-responsive gene expression. They further claim that a machine learning model using binding strength, genomic position, and motif features can predict Notch responsiveness across cell types and species.
- **Visible evidence base** ChIP-seq data from mouse Beko cells, human TNBC lines (HCC1599, MB157), and human T-ALL line (CUTLL1); RNA-seq data; ATAC-seq data; histone modification ChIP-seq; motif analysis; machine learning model performance metrics
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (S1–S12) are not provided; raw data accession numbers are given but data not accessible in this review; detailed model hyperparameters and feature importance values not fully described; exact statistical test details for several comparisons not specified

## Reviewer
- **Overall assessment** This manuscript addresses an important question in Notch signaling: why only a subset of RBPJ-bound loci respond to pathway activation. The distinction between static and dynamic RBPJ binding sites, and the association of dynamic sites with enhancer positioning and transcriptional responsiveness, is a potentially valuable conceptual advance. The use of multiple cell types and cross-species validation strengthens the generalizability of the findings. However, several technical concerns need to be addressed, particularly regarding the definition of dynamic sites, the robustness of the machine learning approach, and the causal interpretation of the correlative data. The manuscript is well-written and the logical flow is clear, but the current evidence does not fully establish the predictive framework as presented.

- **Who would be interested in the results, and why** Researchers studying Notch signaling, transcriptional regulation, enhancer biology, and computational genomics would find this work relevant. The conceptual framework distinguishing static from dynamic transcription factor binding sites could inform studies of other inducible signaling pathways. Clinically, the application to TNBC and T-ALL suggests potential relevance for understanding Notch-driven cancers and identifying biomarkers of pathway dependence.

- **Major strengths** 
  1. The study addresses a fundamental and unresolved question in Notch biology: why RBPJ occupies thousands of sites but only a subset drives transcriptional responses.
  2. The integration of multiple genomic datasets (ChIP-seq, ATAC-seq, histone marks, RNA-seq) provides a comprehensive characterization of static versus dynamic sites.
  3. The cross-species and cross-cell-type validation (mouse, human TNBC, human T-ALL) substantially strengthens the generalizability of the findings.
  4. The machine learning approach offers a practical tool for predicting Notch-responsive loci, which could be broadly applicable.
  5. The washout experiments provide a complementary approach to GSI treatment, helping to confirm the reversibility of dynamic binding.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "only a small set of the total RBPJ sites show a dynamic binding behavior in response to Notch signaling" and define dynamic sites using a log2FC threshold of <–0.5 upon GSI treatment.
- **Evidence pointer** Results section "Identification of dynamic binding of transcription factor RBPJ"; Figure 1B, C
- **Concern** The threshold of log2FC <–0.5 for defining dynamic sites appears arbitrary and may not be statistically justified. The manuscript does not describe how this cutoff was determined, whether it was based on a null distribution, or how false discovery rates were controlled. Additionally, the use of DESeq2 for ChIP-seq differential binding analysis, while reasonable, requires careful normalization and the manuscript does not fully describe how sequencing depth, library complexity, or spike-in normalization were handled across replicates.
- **Why it matters** The central distinction between static and dynamic sites underpins all subsequent analyses. If the threshold is not rigorously justified, the classification may be unstable or biased, potentially affecting the validity of downstream conclusions about enhancer positioning, chromatin state, and gene responsiveness.
- **Resolution test** Provide a clear statistical justification for the log2FC threshold, including a null distribution or permutation-based approach. Describe the normalization strategy in detail, including how spike-in data were used. Show sensitivity analyses demonstrating that the main conclusions are robust to reasonable variations in the threshold.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "gene responsiveness is preferentially associated with dynamic RBPJ binding sites" based on the association of RBPJ sites to genes using a basal plus extension model.
- **Evidence pointer** Results section "Transcriptional response to Notch activation is preferentially associated with dynamic sites"; Figure 3A–C
- **Concern** The gene assignment method (basal plus extension, similar to GREAT) is a heuristic approach that may misassign enhancers to incorrect target genes, particularly for distal enhancers that can regulate genes over large genomic distances or skip intervening genes. The manuscript does not provide validation of the gene assignment, such as promoter capture Hi-C, eQTL data, or CRISPR perturbation of selected enhancers. Without such validation, the claim that dynamic sites are preferentially associated with responsive genes may reflect assignment artifacts rather than true regulatory relationships.
- **Why it matters** The functional interpretation of dynamic sites as drivers of transcriptional response depends critically on correct enhancer-promoter assignment. If assignments are inaccurate, the enrichment of responsive genes near dynamic sites could be spurious or underestimated.
- **Resolution test** Validate gene assignment for a subset of dynamic sites using orthogonal approaches (e.g., Hi-C, CRISPR interference at selected loci). Alternatively, show that the enrichment of responsive genes near dynamic sites is robust to different gene assignment methods (e.g., nearest gene, GREAT with different parameters).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the machine learning model can "predict Notch responsiveness with high confidence in different cellular contexts" using features including MSPC p-value, genomic position, and motif occurrence.
- **Evidence pointer** Results section "Predicting dynamic and static RBPJ sites"; Figure 6
- **Concern** The description of the machine learning approach is incomplete. The manuscript states that a random forest model was trained on combined Beko and MB157 data and tested on HCC1599 and CUTLL1, but does not provide key details: the number of trees, tree depth, feature importance scores, hyperparameter tuning procedure, or how class imbalance (158 dynamic vs. 3380 static sites in Beko) was handled. The reported accuracy and AUC values are mentioned but not shown in the provided text. Most critically, the model's performance on the test sets is described qualitatively ("high confidence") without quantitative metrics.
- **Why it matters** For the predictive framework to be useful and credible, the model must be fully described and its performance rigorously quantified. Without these details, readers cannot assess whether the model is overfitted, whether the features are genuinely predictive, or whether the performance generalizes.
- **Resolution test** Provide complete model specifications, feature importance rankings, confusion matrices, precision-recall curves, and AUC values for all training and test sets. Address class imbalance explicitly (e.g., through downsampling, class weights, or alternative metrics such as F1 score).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors propose that "the combination of binding strength and enhancer positioning are indicative of Notch responsiveness" and suggest this framework may apply to other transcription factors.
- **Evidence pointer** Discussion section
- **Concern** The causal relationship between dynamic binding and transcriptional responsiveness is not established. The data are largely correlative: dynamic sites are associated with responsive genes, and chromatin marks change upon pathway perturbation. However, the manuscript does not demonstrate that dynamic RBPJ binding is required for the transcriptional response, nor does it exclude the possibility that dynamic binding is a consequence rather than a cause of chromatin changes. The speculation that this framework applies to other transcription factors (p53, TCF/Wnt) is not supported by any data presented.
- **Why it matters** The broader significance of the work depends on whether dynamic binding is a driver of responsiveness or merely a correlate. If the framework is to be generalized, evidence of causality or at least a mechanistic model supported by perturbation experiments would be needed.
- **Resolution test** Perform perturbation experiments (e.g., CRISPR deletion of selected dynamic enhancers, tethering RBPJ to static sites) to test whether dynamic binding is necessary and/or sufficient for transcriptional response. For the generalization claim, provide pilot data from another signaling pathway or clearly frame this as speculation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "the code to run the prediction of dynamic and static RBPJ sites is available in Zenodo" and data are deposited at GEO under GSE235984.
- **Evidence pointer** Data availability section
- **Concern** While the deposition of data and code is commendable, the manuscript does not describe the computational environment, software versions, or dependencies required to run the code. The custom in-house tool for gene annotation is mentioned but not described in sufficient detail for others to implement. The exact parameters for all bioinformatics tools (MACS2, DESeq2, ROSE, MEME) are not fully specified.
- **Why it matters** Reproducibility is a core requirement for computational genomics studies. Without complete documentation of the analysis pipeline, independent researchers cannot verify or build upon the results.
- **Resolution test** Provide a detailed analysis pipeline document, including software versions, parameters, and a containerized environment (e.g., Docker or Conda) if possible. Describe the custom gene annotation tool in sufficient detail or make it available as part of the deposited code.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1C
- **Evidence pointer** Results section "Identification of dynamic binding of transcription factor RBPJ"
- **Issue** The text states that "RBPJ binding is stronger at dynamic sites compared to static sites when the Notch pathway is active," but the quantitative basis for this comparison is not described in the text. It is unclear whether this refers to peak intensity, area under the curve, or another metric.
- **Required correction** Specify the metric used to compare binding strength and provide the statistical test and p-value for this comparison.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3F
- **Evidence pointer** Results section "Transcriptional response to Notch activation is preferentially associated with dynamic sites"
- **Issue** The comparison of gene expression changes upon GSI treatment, dnMAML overexpression, and GSI washout is described, but the time points for each condition are not specified. It is unclear whether all conditions were assessed at the same time point, which could affect comparability.
- **Required correction** Clearly state the time points for each treatment condition and justify the comparability of the different perturbations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Supplementary Figure S6A
- **Evidence pointer** Results section "Transcriptional response to Notch activation is preferentially associated with dynamic sites"
- **Issue** The enrichment analysis of deregulated genes near dynamic versus static sites is described, but the statistical method used to assess enrichment (e.g., hypergeometric test, permutation test) is not stated.
- **Required correction** Describe the statistical test used for enrichment analysis and how multiple testing was controlled.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Prediction model"
- **Evidence pointer** Materials and methods section
- **Issue** The manuscript states that "after testing different features, intron and exon regions were combined to represent gene bodies," but the results of this feature testing are not shown. It is unclear which features were tested and why the final set was chosen.
- **Required correction** Provide a supplementary table or figure showing the feature selection process and the rationale for the final feature set.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of static sites as potential "gate-keeper" functions is speculative and not directly supported by the data presented. While this is an interesting hypothesis, it should be clearly labeled as speculation.
- **Required correction** Distinguish between conclusions supported by data and hypotheses that require further testing.

## Risk / unsupported claims
- The claim that dynamic RBPJ sites are "indicative of Notch responsiveness" is supported by correlative data but causality is not established; perturbation experiments are needed.
- The generalization of the framework to other transcription factors (p53, TCF/Wnt) is speculative and not supported by any data in this manuscript.
- The machine learning model's performance is described qualitatively; quantitative metrics are not provided in the text.
- The gene assignment method (basal plus extension) is not validated with orthogonal approaches, and the potential for misassignment affecting the enrichment analysis is not addressed.
- The claim that dynamic binding behavior is "repeatedly observed across different cell types and species" is based on analysis of human cell lines and mouse cells, but the number of replicates and the statistical power for cross-species comparisons are not fully described.
- The functional significance of the subtle differences in chromatin marks between static and dynamic sites is not fully explored; the manuscript does not demonstrate that these differences are functionally relevant for transcriptional regulation.