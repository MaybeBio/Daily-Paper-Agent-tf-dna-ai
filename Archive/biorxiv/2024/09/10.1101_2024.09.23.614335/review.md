## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided in full)
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text; no assessment of figures or supplementary materials beyond what is described
- **Shared manuscript claim summary** The authors present woT-ChIC, a single-cell co-mapping assay for histone modifications (H3K27me3, H3K4me1) and full-length transcriptomes, applied to zebrafish embryos from 4 to 24 hpf. They report that chromatin and transcriptional states are initially decoupled, become progressively coupled during gastrulation and somitogenesis, that developmental gene silencing involves cis-spreading of H3K27me3, and that TF activities can be classified as activators or repressors using an interpretable machine learning model integrating chromatin state and expression.
- **Visible evidence base** Text descriptions of results, methods, and supplementary figure references; no actual figures, tables, or numerical data provided in the submitted material
- **Missing materials affecting confidence** All figures, supplementary tables, numerical results, statistical details, and validation analyses are absent from the provided text. The manuscript is incomplete as submitted for review.

## Reviewer
- **Overall assessment** This manuscript addresses a significant gap in developmental biology by jointly profiling histone modifications and transcriptomes in single cells during early zebrafish embryogenesis. The technical advance is substantial and the biological questions are well motivated. However, the provided text lacks the actual data presentation, figures, and quantitative results necessary to evaluate the validity of the central claims. The methods are described in sufficient detail to assess feasibility, but the evidence base for the conclusions cannot be verified from the submitted material. The conceptual framework, particularly the decoupling of chromatin and transcription states followed by progressive coupling, is interesting but requires rigorous statistical support that is not visible in the text alone.

- **Who would be interested in the results, and why** Developmental biologists studying chromatin dynamics and cell fate specification during embryogenesis; researchers in single-cell genomics and multi-omics method development; investigators interested in polycomb-mediated gene silencing and epigenetic regulation of transcription factors. The methodological advance of co-mapping histone modifications with full transcriptomes in single cells will be of broad interest to the epigenomics and single-cell communities.

- **Major Strengths**  
  1. The technical advance of co-mapping two histone modifications with full-length transcriptomes in single cells is significant and addresses a clear methodological gap.  
  2. The biological question regarding the temporal relationship between chromatin state and transcription during vertebrate development is important and timely.  
  3. The use of an interpretable machine learning model to classify TF function is a thoughtful analytical approach.  
  4. The observation of cis-spreading of H3K27me3 as a mechanism for developmental gene silencing is mechanistically interesting.  
  5. The inclusion of nuclei and whole-cell batches to address maternal RNA contamination is a careful experimental consideration.

- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The manuscript claims that "before the formation of germ layers, the chromatin and transcription states of cells are uncoupled, and become progressively connected during gastrulation and somitogenesis."  
- **Evidence pointer** Results section "Global chromatin state of cells is decoupled from gene expression during early development"; Figure 3c-d; Figure S6d  
- **Concern** The central claim of decoupling followed by progressive coupling between chromatin state and transcription is presented without any quantitative metrics in the text. The correlation values, statistical significance, and effect sizes are not reported. The claim that "the correlation between the gene-body H3K4me1 and transcription increases with the average latent time of a metacell" requires specific correlation coefficients, confidence intervals, and appropriate statistical tests. Without these, the strength and reproducibility of the observed relationship cannot be assessed.  
- **Why it matters** This is the primary conceptual finding of the manuscript. If the decoupling-coupling transition is not robustly demonstrated with appropriate statistics, the entire interpretive framework is weakened.  
- **Resolution test** Provide correlation coefficients (e.g., Spearman or Pearson) with confidence intervals for the relationship between H3K4me1 signal and transcription across metacells at each developmental stage. Include permutation-based or bootstrap-based significance testing. Show that the increase in correlation over latent time is statistically significant and not driven by outliers or batch effects.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical validation  
- **Claim pointer** The manuscript claims that woT-ChIC provides "a multimodal measurement of full-length transcriptome and histone modifications in individual cells" and that the data quality is sufficient for the analyses performed.  
- **Evidence pointer** Methods section "Whole-organism T-ChIC of zebrafish embryos"; Figure S1a-g; Supplementary Tables 1-2  
- **Concern** The validation of the woT-ChIC method is described only in text. Key quality metrics are not reported: the fraction of cells passing QC, the sensitivity of histone modification detection relative to bulk data, the reproducibility between biological replicates, the specificity of the antibody-based cleavage, and the concordance between the transcriptome and chromatin data from the same cell. The claim that the "nuclei" batch shows a 4-fold higher ratio of unspliced to spliced RNA is presented without variance or statistical comparison. The co-clustering of T-noChIC and T-ChIC cells is mentioned but not quantified.  
- **Why it matters** The entire manuscript rests on the reliability of the co-mapping assay. Without rigorous validation metrics, readers cannot determine whether the observed decoupling of chromatin and transcription is a biological phenomenon or an artifact of the method.  
- **Resolution test** Provide detailed quality metrics: number of cells before and after QC, median genes detected per cell, median H3K27me3 and H3K4me1 fragments per cell, correlation with bulk ChIP-seq/CUT&RUN data at matched time points, and reproducibility across biological replicates. Show that the transcriptome component of woT-ChIC is comparable to standard scRNA-seq in sensitivity and accuracy.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Analytical rigor  
- **Claim pointer** The manuscript claims that "Combining transcription factor (TF) expression and chromatin states within an interpretable machine learning model, we classify TFs as lineage-specific activators and repressors and identify a subset of TFs that are epigenetically regulated."  
- **Evidence pointer** Results section "The chromatin state of binding sites predicts the function of transcription factors during gastrulation"; Figure 4a-c; Figure S8a-c; Supplementary Table 4  
- **Concern** The machine learning model is described conceptually but the implementation details are insufficient. The features used, the model architecture, the training procedure, the hyperparameter selection, and the evaluation metrics beyond R² are not specified. The claim that the model "predicted the H3K4me1 activity at TFBS with high accuracy (R² > 0.6) for 45 TFs" requires information on how many TFs were tested, how the threshold was chosen, and whether the R² values are out-of-sample or in-sample. The classification of TFs as activators or repressors based on model weights requires validation against known biology beyond the few examples given.  
- **Why it matters** The TF classification is a major output of the manuscript and is presented as a novel analytical contribution. Without sufficient methodological detail and validation, the classifications cannot be independently assessed or reproduced.  
- **Resolution test** Provide complete model specifications, including feature lists, regularization parameters, cross-validation scheme, and out-of-sample performance metrics. Validate the activator/repressor classifications against independent experimental data (e.g., known TF knockout or overexpression phenotypes, ChIP-seq binding data). Report the number of TFs classified in each category and the confidence intervals for the classifications.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Interpretive caution  
- **Claim pointer** The manuscript claims that "Silencing of developmental genes is achieved by local spreading of repressive chromatin together with cell-type specific demethylation."  
- **Evidence pointer** Results section "Spatiotemporal spreading of H3K27me3 associates with the silencing of gene expression during development"; Figure 2b-f; Figure S4a-i  
- **Concern** The causal language used in this claim ("is achieved by") is not supported by the correlative evidence described. The text describes associations between H3K27me3 spreading and gene silencing, and between demethylation and gene activation, but no perturbation experiments are described that would establish causality. The regression analysis predicting gene expression from H3K27me3 density is correlative.  
- **Why it matters** The manuscript proposes a mechanistic model for developmental gene silencing. Overstating causal relationships could mislead readers and future research directions.  
- **Resolution test** Soften the language to describe associations rather than causal mechanisms, or provide perturbation data (e.g., knockdown of demethylases, inhibition of PRC2) that directly tests the proposed mechanism.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability  
- **Claim pointer** The manuscript claims that "the spread of H3K27me3 signal from promoters might be a conserved phenomenon" based on re-analysis of mouse embryo data.  
- **Evidence pointer** Results section "Spatiotemporal spreading of H3K27me3 associates with the silencing of gene expression during development"; Figure S4i  
- **Concern** The evidence for conservation across species is described as a re-analysis of a single published mouse dataset. The text does not specify the developmental stages compared, the statistical approach used to demonstrate spreading, or whether the spreading pattern in mouse is quantitatively similar to that observed in zebrafish. A single comparison point is insufficient to establish conservation.  
- **Why it matters** The claim of conservation strengthens the general significance of the findings. If the evidence is weak, the claim should be appropriately qualified.  
- **Resolution test** Provide detailed methods for the mouse data re-analysis, including the specific stages compared, the metrics used to define spreading, and statistical comparisons. If possible, include additional species or independent datasets to strengthen the conservation claim.

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The phrase "Establishing a cell-type-specific chromatin landscape is crucial for the maintenance of cell identity during embryonic development" is somewhat vague. It is not clear whether "establishing" refers to the process during development or the maintenance function in adult tissues.  
- **Required correction** Clarify the intended meaning, for example by specifying "the establishment of cell-type-specific chromatin landscapes during embryonic development is crucial for the subsequent maintenance of cell identity."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Methodological detail  
- **Affected element** Methods, "Whole-organism T-ChIC of zebrafish embryos"  
- **Evidence pointer** Methods section, paragraph 1  
- **Issue** The description of the "nuclei" batch mentions a modified buffer with saponin instead of Tween20, but the rationale for this change is not explained. The text states it "leads to the expulsion of cytoplasmic RNA" but does not describe how this was verified or whether it affects chromatin recovery.  
- **Required correction** Provide a brief explanation of the rationale for the saponin-based buffer and any validation data showing that chromatin quality is unaffected.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical reporting  
- **Affected element** Results, "Spatiotemporal spreading of H3K27me3 associates with the silencing of gene expression during development"  
- **Evidence pointer** Results section, paragraph 3  
- **Issue** The text mentions "significant loss of H3K27me3 (log2-FC < -1, FDR < 0.05)" but does not report the number of genes tested, the number of comparisons, or the multiple testing correction method beyond FDR.  
- **Required correction** Report the total number of genes tested, the number of significant genes, and the specific FDR method used (e.g., Benjamini-Hochberg).

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods, "Processing and quality control of T-Chip data"  
- **Evidence pointer** Methods section, paragraph 2  
- **Issue** The custom Python script for splitting raw fastq files is mentioned but not described in detail. The GitHub link is provided, but the text does not specify the version or the exact logic for distinguishing RNA and ChIC barcodes.  
- **Required correction** Provide a brief description of the barcode formats and the splitting logic, or reference a specific version of the script.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Results, "Global chromatin state of cells is decoupled from gene expression during early development"  
- **Evidence pointer** Results section, paragraph 1  
- **Issue** The term "bivalent chromatin state" is used to describe promoters co-marked by H3K4me1 and H3K27me3. This term is typically reserved for H3K4me3/H3K27me3 co-marking in embryonic stem cells. Using it for H3K4me1/H3K27me3 may cause confusion.  
- **Required correction** Consider using a more precise term, such as "co-marked" or "dual-marked," or explicitly define the usage of "bivalent" in this context.

- **Concern ID** R1-m6  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Results, "Paired profiling of histone modifications and transcriptome of single cells during zebrafish embryogenesis"  
- **Evidence pointer** Results section, paragraph 2  
- **Issue** The text states that "the analysis of genomic bins ranked by H3K27me3 signal shows improved signal enrichment of our data relative to the publicly available bulk sequencing data at a comparable sequencing depth." The metric "signal enrichment" is not defined, and the comparison is not quantified.  
- **Required correction** Define the metric used for signal enrichment and report the numerical values for both the woT-ChIC data and the public data.

## Risk / unsupported claims
- The claim that chromatin and transcription states are "uncoupled" before germ layer formation and "become progressively connected" during gastrulation and somitogenesis is not supported by quantitative evidence in the provided text.
- The claim that H3K27me3 cis-spreading "achieves" gene silencing implies causality that is not established by the correlative analyses described.
- The claim that TF classification as activators or repressors is validated is not supported by the text, which mentions only a few examples without systematic validation.
- The claim of cross-species conservation of H3K27me3 spreading is based on a single re-analyzed dataset and is not sufficiently supported.
- The overall data quality and reproducibility of woT-ChIC cannot be assessed without the actual QC metrics and validation figures.
- The statistical methods for the regression analyses, differential H3K27me3 analysis, and machine learning model are described only in general terms and cannot be evaluated for appropriateness.