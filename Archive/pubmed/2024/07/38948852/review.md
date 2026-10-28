## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors integrate single-cell RNA-seq (scRNA-seq) and single-cell ATAC-seq (scATAC-seq) data to identify cooperative transcription factors (TFs) regulating target gene (TG) expression in oligodendrocytes. They identify co-binding TF pairs in oligodendrocyte-specific regulatory regions, train a deep learning model to predict TG expression from TF expression, and use Shapley interaction scores to quantify TF importance and TF-TF interactions. They report that known TF pairs (SOX10-TCF12, SOX10-MYRF, SOX10-OLIG2) show significantly higher Shapley scores, identify 153 oligodendrocyte-associated eQTLs in regulatory regions, and validate selected TF pairs via ChIP-seq co-enrichment analysis in rat peripheral nerve.
- **Visible evidence base** Abstract text only; no methodological details, quantitative results beyond p-values, or experimental data are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, model architecture and training details, statistical analysis specifics, and ChIP-seq validation results

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting integrative approach to studying TF cooperativity in oligodendrocytes, with a plausible pipeline from multi-omics data to deep learning-based inference. However, the evidence provided in the abstract is insufficient to evaluate the technical soundness, statistical rigor, or biological validity of the claims. The central findings, particularly the Shapley score comparisons and eQTL identification, lack necessary context and validation details. The experimental validation is limited to a single tissue type and species, which may not directly support the human oligodendrocyte claims.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, oligodendrocyte biology, myelin disorders, and computational genomics would find this relevant. Those working on TF cooperativity mechanisms, single-cell multi-omics integration, and interpretable deep learning for gene regulation would be the primary audience. Clinicians studying genetic variants in brain disorders may also be interested given the eQTL findings.
- **Major strengths** The integration of scRNA-seq and scATAC-seq to identify co-binding TF pairs is a reasonable approach. The use of Shapley interaction scores for interpretable deep learning is a modern and appropriate method for quantifying TF-TF interactions. The focus on known biologically relevant TF pairs provides a sanity check for the computational pipeline. The identification of eQTLs in oligodendrocyte-specific regulatory regions has potential translational relevance.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: The combination of co-binding site identification, deep learning, and Shapley interaction scores is somewhat novel, but similar integrative approaches exist in the literature. The specific application to oligodendrocytes adds domain novelty.  
  - Scientific importance: The findings could be important for understanding TF cooperativity in myelination and related disorders, but the abstract does not demonstrate broad biological insight beyond confirming known TF pairs.  
  - Interdisciplinary readership: The work bridges genomics, machine learning, and neurobiology, which could attract a broad audience if the methods and results are clearly presented.  
  - Technical soundness: Not assessable from the abstract alone; critical details on data processing, model training, statistical tests, and validation are missing.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses jargon (e.g., Shapley scores, eQTLs) without sufficient explanation for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially useful pipeline, but the lack of methodological detail and validation prevents assessment of whether the claims are supported. Supportive if technical concerns are resolved in the full manuscript.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** "co-binding TF pairs involving known important TF pairs for oligodendrocyte differentiation, such as SOX10-TCF12, SOX10-MYRF, and SOX10-OLIG2, exhibited significantly higher Shapley scores than others (t-test, p-value < 1e-4)"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract reports a t-test with p-value < 1e-4 but does not specify the comparison group, the number of TF pairs tested, whether multiple testing correction was applied, or the effect size. The selection of "known important TF pairs" may introduce bias if these pairs were used to guide model training or feature selection.  
- **Why it matters** Without knowing the comparator set and correction for multiple comparisons, the reported significance could be inflated. If the known pairs were used in model development, the result would be circular.  
- **Resolution test** Provide the full statistical details, including the null distribution, number of tests, correction method, and effect sizes. Clarify whether the known TF pairs were excluded from model training or feature selection.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "we trained a deep learning model to predict the expression level of each TG using the expression levels of co-binding TFs"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No details are given on the model architecture, training data, feature selection, hyperparameters, or evaluation metrics. It is unclear how the model handles the high dimensionality of TF expression data, how overfitting is avoided, and how prediction accuracy is assessed.  
- **Why it matters** The validity of the Shapley interaction scores depends entirely on the quality and interpretability of the deep learning model. If the model is poorly trained or overfitted, the interaction scores may not reflect true biological cooperativity.  
- **Resolution test** Provide model architecture, training/validation/test splits, performance metrics (e.g., correlation, RMSE), and demonstrate that the model generalizes to held-out data.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Biological validation  
- **Claim pointer** "we experimentally validated some identified TF pairs such as SOX10-OLIG2 and SOX10-NKX2.2 by co-enrichment analysis, using ChIP-seq data from rat peripheral nerve"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The validation uses ChIP-seq data from rat peripheral nerve, which is a different tissue and species from the human oligodendrocyte data used for the main analysis. The relevance of this validation to the human oligodendrocyte context is unclear. Additionally, co-enrichment analysis is a weak form of validation for cooperative TF binding, as it does not demonstrate functional interaction.  
- **Why it matters** The validation is meant to support the biological relevance of the identified TF pairs. If the validation is performed in a non-comparable system, it does not adequately confirm the findings in oligodendrocytes.  
- **Resolution test** Provide validation in human oligodendrocytes or a closely related system, and use functional assays (e.g., perturbation experiments) or at least demonstrate that the co-enrichment is specific and statistically significant.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Data provenance and interpretation  
- **Claim pointer** "we identified 153 oligodendrocyte-associated eQTLs that reside in oligodendrocyte-specific enhancers or promoters where their eGenes (TGs) are regulated by cooperative TFs"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not specify the source of the eQTL data, the criteria for "oligodendrocyte-associated," or how the link between eQTLs and cooperative TF regulation is established. The claim of "potential novel regulatory roles" is speculative without functional validation.  
- **Why it matters** The eQTL finding is presented as a key translational outcome, but without details on data sources and analytical methods, the claim cannot be evaluated. The biological significance of these eQTLs is unclear.  
- **Resolution test** Specify the eQTL dataset, the definition of oligodendrocyte-associated, the statistical methods for linking eQTLs to TF regulation, and provide functional evidence or at least a clear hypothesis for the regulatory role.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, methods description  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not define "co-binding TF pairs" or "oligodendrocyte-specific regulatory regions" clearly.  
- **Required correction** Provide brief definitions or references for these terms to improve accessibility.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Data availability  
- **Evidence pointer** Abstract, location not provided  
- **Issue** No mention of data availability or code availability.  
- **Required correction** State where the scRNA-seq, scATAC-seq, and ChIP-seq data are deposited, and whether the deep learning code is publicly available.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Presentation  
- **Affected element** Abstract, results summary  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract lists three steps but does not summarize the overall performance of the model or the number of TF pairs identified beyond the known ones.  
- **Required correction** Include a brief quantitative summary of the model performance and the total number of significant TF pairs identified.

## Risk / unsupported claims
- The claim that known TF pairs exhibit significantly higher Shapley scores is unsupported without details on the comparator group and multiple testing correction.
- The claim of "potential novel regulatory roles" for the 153 eQTLs is speculative and not supported by functional evidence in the abstract.
- The experimental validation using rat peripheral nerve ChIP-seq data does not directly support the human oligodendrocyte findings and is therefore insufficient to validate the main claims.
- The overall biological significance of the identified cooperative TF pairs beyond confirming known interactions is not established from the abstract.