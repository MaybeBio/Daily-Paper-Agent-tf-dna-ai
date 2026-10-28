## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, author contributions, acknowledgements, footnotes)
- **Assessment boundary** Scientific validity, technical soundness, reproducibility, and support of claims based solely on the provided manuscript text. No external data, figures, or supplementary materials were available for inspection.
- **Shared manuscript claim summary** The authors trained 18 cell-class-specific gkm-SVM models on human retinal snATAC-seq data to predict the functional impact of non-coding variants in cis-regulatory elements. They report >90% accuracy, cell-class specificity, validation against massively parallel reporter assays, and application to GWAS variants in retinal disease.
- **Visible evidence base** Abstract, Introduction, Methods (partial), Results (narrative only), Discussion, Author Contributions, Acknowledgements, Footnotes. No figures, tables, or supplementary files were provided.
- **Missing materials affecting confidence** All figures (Figure 1-4, S1-S3), all tables (Table S1, S2), the UCSC trackhub, the GitHub repository, and the full Methods section (including hyperparameters, cross-validation details, and MPRA comparison methodology) were not accessible. These are essential for evaluating the technical claims.

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable resource for the retinal genetics community: cell-class-specific machine learning models for variant effect prediction in non-coding regulatory elements. The conceptual approach is sound and builds logically on prior work. However, the provided text alone does not permit verification of the central claims. Accuracy metrics, cell-class specificity, MPRA correlations, and GWAS prioritization are all described narratively without supporting quantitative data. The absence of figures, tables, and detailed methods prevents assessment of model performance, statistical rigor, and biological validity. The manuscript is promising but currently not established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in inherited retinal disease genetics, ophthalmic genomics, regulatory genomics, and computational biology. The resource (csVISIONS) could aid in prioritizing non-coding variants for functional testing, which is a bottleneck in IRD diagnosis. The approach may also interest those applying gkm-SVM to single-cell epigenomic data in other tissues.
- **Major strengths** The use of single-nucleus ATAC-seq to achieve cell-class resolution is a meaningful advance over bulk tissue models. The integration of developmental timepoints and mature retina is commendable. The comparison to MPRA data, if robust, provides functional validation. The public availability of the trackhub and code is a strength for the community.
- **Major Concerns** See items R1-M1 through R1-M5 below.
- **Minor Comments** See items R1-m1 through R1-m4 below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (accuracy metrics not shown), R1-M2 (cell-class specificity not quantified), R1-M3 (MPRA correlation statistics incomplete), R1-M4 (GWAS prioritization not demonstrated), R1-M5 (Methods insufficient for reproducibility).
- **Assessment against Nature-style criteria**  
  - *Originality*: Moderate. The application of gkm-SVM to single-cell ATAC-seq for retinal cell classes is novel, but the underlying methodology is established. The originality lies in the resource and its cell-class resolution, not in the algorithmic approach.  
  - *Scientific importance*: Potentially high for the IRD community, as non-coding variant interpretation is a recognized challenge. However, the importance is contingent on demonstrated accuracy and utility, which are not verifiable from the provided text.  
  - *Interdisciplinary readership*: The work bridges computational biology, genomics, and clinical genetics. It could appeal to a broad readership if the resource is robust and accessible.  
  - *Technical soundness*: Not assessable from the provided material. Key technical details and validation data are missing.  
  - *Readability for nonspecialists*: The narrative is generally clear, but the Methods section is too brief for a nonspecialist to understand the modeling approach. The Results section relies heavily on figures that were not provided.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the core claims require verification with the missing data. A revised submission with full methods, figures, and quantitative results would be needed for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "These models demonstrate accuracy over 90% and a high degree of cell class specificity."  
- **Evidence pointer** Results section, Figure 1C, Figure S1 (not provided)  
- **Concern** The claim of >90% accuracy is stated in the abstract and results, but no accuracy values, confidence intervals, or statistical comparisons are provided in the text. The referenced figures (Figure 1C, Figure S1) are not available for inspection.  
- **Why it matters** Accuracy is the primary quantitative claim of the manuscript. Without the actual ROC curves, AUROC values, and any measure of variance, the reader cannot assess whether the models perform as stated.  
- **Resolution test** Provide the AUROC values for all 18 models, including confidence intervals, and show the ROC curves in the main text or supplement. State the number of cross-validation folds and the variance across folds.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "a high degree of cell class specificity" and "clustering of related cell classes"  
- **Evidence pointer** Results section, Figure 1D (not provided)  
- **Concern** The claim of cell-class specificity is supported only by a narrative description of hierarchical clustering. No quantitative measure of specificity (e.g., classification accuracy, enrichment scores, or pairwise distances) is provided.  
- **Why it matters** Cell-class specificity is a central novelty of this work. Without quantitative evidence, it is unclear whether the models truly distinguish cell classes or merely reflect shared regulatory features.  
- **Resolution test** Provide a quantitative specificity metric, such as a confusion matrix of model scores on outgroup peaks, or a permutation test showing that self-scores are significantly higher than cross-scores.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "Correlations to massively parallel reporter assays support the predictive value of VIP scores to model single nucleotide variants and indels in a cell-class-specific manner."  
- **Evidence pointer** Results section, Figure 3B-E, Figure S3 (not provided)  
- **Concern** The correlation values are reported for bipolar cells (0.575) and rods (0.49), but no p-values, confidence intervals, or sample sizes are given. The comparison is limited to a single locus (Gnb3 promoter) and a single TF (CRX).  
- **Why it matters** The MPRA comparison is the only functional validation presented. The reported correlations are moderate, and without statistical context or additional loci, the generalizability of the models is unclear.  
- **Resolution test** Provide p-values and confidence intervals for the correlations, state the number of variants tested, and ideally include validation at additional loci or in additional cell types.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** "GWAS Predictions Narrow Variant Search Window" and the ARMS2 example  
- **Evidence pointer** Results section, Figure 4A-C (not provided)  
- **Concern** The GWAS application is described for a single locus (ARMS2) with two variants (rs36212732 and rs36212733). The claim that VIP scores can narrow the search window is based on this one example. No systematic evaluation across GWAS loci is presented.  
- **Why it matters** The utility of the resource for disease variant prioritization is a key selling point. A single anecdotal example is insufficient to establish this utility.  
- **Resolution test** Provide a systematic analysis of VIP scores across all GWAS variants in Table S2, including a comparison to random expectation or to other prioritization methods.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** "Models were trained with ls-gkm gkmtrain as previously described."  
- **Evidence pointer** Methods section  
- **Concern** The Methods section is severely abbreviated. Key parameters (k-mer length, number of gapped k-mers, SVM hyperparameters, negative set construction, GC-matching procedure, cross-validation scheme) are not described. The referenced GitHub repository was not accessible for review.  
- **Why it matters** Reproducibility is a core requirement for computational work. Without full methods, other researchers cannot replicate the models or assess potential biases in training data.  
- **Resolution test** Provide a complete Methods section with all hyperparameters and data processing steps. Ensure the GitHub repository is publicly accessible and contains all code and intermediate data.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The phrase "characterizing the functional impact of most regulatory variants remains challenging" is vague. It would be clearer to specify the scale of the challenge (e.g., number of variants, lack of functional assays).  
- **Required correction** Rephrase to provide a concrete statement of the problem, such as "the functional impact of the vast majority of non-coding variants is unknown, and experimental characterization is low-throughput."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Results section, Figure 2  
- **Evidence pointer** Results section, "Variant Impact Predictions Identify Critical Sequence Motifs"  
- **Issue** The description of Figure 2A-F is dense and assumes familiarity with the figure layout. The text does not clearly state what is plotted on the axes.  
- **Required correction** Add a sentence describing the figure axes and the meaning of the VIP score heatmap or line plot.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical rigor  
- **Affected element** Results section, Figure 3  
- **Evidence pointer** Results section, "Models Recreate CRE-Directed Expression Changes in Class-Specific Manner"  
- **Issue** The correlation values are reported without any measure of uncertainty.  
- **Required correction** Add p-values and confidence intervals for all reported correlations.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Resource accessibility  
- **Affected element** Methods section, Data availability  
- **Evidence pointer** Methods section, "Training data"  
- **Issue** The GEO accession for the snATAC-seq data is provided, but the RPE dataset accession is not explicitly stated.  
- **Required correction** Provide the GEO accession for the RPE dataset (GSE99287) in the main text.

## Risk / unsupported claims
- The claim of >90% accuracy is unsupported without the actual ROC curves and AUROC values.
- The claim of "high degree of cell class specificity" is unsupported without quantitative specificity metrics.
- The claim that MPRA correlations "support the predictive value" is only weakly supported by two moderate correlations at a single locus.
- The claim that GWAS predictions "narrow variant search window" is based on a single anecdotal example and is not generalizable from the provided evidence.
- The claim that the csVISIONS resource is "available" could not be verified, as the URL was not accessible during review.
- The claim that the code is available at the GitHub repository could not be verified, as the repository was not accessible during review.