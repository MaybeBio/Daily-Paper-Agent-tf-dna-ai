## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided
- **Assessment boundary** Scientific validity, technical soundness, and clarity of claims based solely on the supplied text; no external data or figures were available for verification
- **Shared manuscript claim summary** The authors trained 18 cell-class-specific gapped k-mer support vector machine models on human retinal single nucleus ATAC-seq data to predict the functional impact of non-coding variants in cis-regulatory elements. They report >90% model accuracy, cell-class specificity, validation against massively parallel reporter assays, and application to GWAS variants for inherited retinal diseases. A resource called csVISIONS is introduced.
- **Visible evidence base** Abstract, Introduction, Methods, Results, Discussion sections; references to Figures 1–4, Figure S1–S3, Tables S1–S2; no actual figures, tables, or supplementary data were provided
- **Missing materials affecting confidence** All figures, tables, supplementary materials, and code repository contents were not accessible; quantitative results (e.g., AUROC values, correlation coefficients) are referenced but not shown; detailed hyperparameters, data preprocessing steps, and validation procedures are only partially described

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable computational resource for prioritizing non-coding variants in retinal cell classes. The methodological approach is reasonable and builds on prior work. However, the provided text alone does not allow verification of the central claims regarding model accuracy, specificity, and functional validation. Several technical details are missing or ambiguous, and the evidence base is incomplete without access to the figures and supplementary data. The work is of interest to the retinal genetics and regulatory genomics communities, but the case for its broad impact and reliability is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying inherited retinal diseases, particularly those seeking to interpret non-coding variants from patient genomes; computational biologists working on regulatory variant prediction; and investigators using single-cell epigenomic data for cell-type-specific functional genomics. The resource could aid variant prioritization in diagnostic and research settings.
- **Major strengths** The use of single nucleus ATAC-seq data to achieve cell-class resolution is a clear advance over bulk tissue approaches. The integration of multiple developmental timepoints and inclusion of RPE data broadens the scope. The comparison to independent MPRA data provides an external validation strategy. The public availability of the resource and code is commendable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (model accuracy claim not verifiable), R1-M2 (MPRA validation correlation strength), R1-M3 (GWAS variant interpretation overreach), R1-M4 (resource scope and generalizability)
- **Assessment against Nature-style criteria** Originality: moderate; similar gkm-SVM approaches exist, but the retinal cell-class application is novel. Scientific importance: potentially high for IRD genetics, but the impact depends on demonstrated reliability. Interdisciplinary readership: likely to appeal to geneticists, ophthalmologists, and computational biologists. Technical soundness: not fully assessable from text alone; several methodological details are missing. Readability for nonspecialists: generally clear, but some sections assume familiarity with machine learning and genomics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved and the evidence base is made available for verification. Currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "These models demonstrate accuracy over 90% and a high degree of cell class specificity" (Abstract); "All models performed extremely well, with Area Under the Curve (AUROC) values above 0.90 for each" (Results)
- **Evidence pointer** Figure 1C, Figure S1; location not provided
- **Concern** The accuracy and AUROC values are stated but the actual data are not shown in the provided text. It is unclear whether the reported accuracy refers to classification of held-out peaks, cross-validation performance, or something else. The method for computing AUROC and the definition of "accuracy" are not specified. Without access to the figures or numerical results, these claims cannot be independently assessed.
- **Why it matters** The central premise of the manuscript is that these models are accurate and cell-class-specific. If the performance metrics are not properly defined or are inflated due to data leakage or inappropriate validation, the entire predictive framework is compromised.
- **Resolution test** Provide the actual AUROC curves and accuracy values for all 18 models, specify the exact validation scheme (e.g., cross-validation folds, holdout sets), and clarify the definition of accuracy. Show that performance is significantly better than appropriate baselines (e.g., shuffled sequences, GC-matched controls).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Correlations to massively parallel reporter assays support the predictive value of VIP scores to model single nucleotide variants and indels in a cell-class-specific manner" (Abstract); "Correlation of VIPs to variant reporter expression is highest in bipolar cells with a Pearson correlation of 0.575, with correlations of 0.49 in rod photoreceptors" (Results)
- **Evidence pointer** Figure 3B–E, Figure S3; location not provided
- **Concern** The reported Pearson correlations of 0.575 and 0.49 are modest. The text does not provide confidence intervals, p-values, or the number of variants tested. It is unclear whether these correlations are statistically significant and whether they are consistent across biological replicates. The claim that the models "recreate" expression changes may be overstated given the moderate correlation values.
- **Why it matters** The MPRA comparison is the primary external validation. If the correlations are weak or not statistically robust, the predictive value of the models for functional variant impact is not convincingly demonstrated.
- **Resolution test** Provide the full MPRA dataset details, including the number of variants, replicates, and statistical significance of the correlations. Show scatter plots of predicted vs. observed effects. Discuss whether the correlation values are comparable to other published gkm-SVM applications.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "To predict which variants are most likely to have an impact on a cell type of interest, we generated VIP scores for all variants in an aggregated table of GWAS-identified sequence variants across four retinal diseases" (Results); "only rs36212733 has a predicted impact" (Results)
- **Evidence pointer** Figure 4B–C, Table S2; location not provided
- **Concern** The GWAS analysis is presented as a demonstration of the models' utility, but the text only describes a single example (ARMS2 region). It is unclear how many GWAS variants were scored, how many were predicted to have high impact, and whether any predictions were experimentally validated. The claim that VIP scores can "narrow the search window" is plausible but not quantitatively supported.
- **Why it matters** The clinical relevance of the resource depends on its ability to prioritize variants that are truly functional. Without a systematic evaluation of GWAS variants and some form of validation, the practical utility is uncertain.
- **Resolution test** Provide a summary of the GWAS variant analysis, including the number of variants scored, the distribution of VIP scores, and the number of high-impact predictions. If possible, validate a subset of predictions experimentally or against known functional variants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "We therefore extended these scores to include a more inclusive set of 39,437 putative retinal CREs as defined by both our original ATAC-seq regions, as well as the top 10,000 peaks of retina-associated previously generated38 TF ChIP-seq data" (Results)
- **Evidence pointer** Methods, Results; location not provided
- **Concern** The extension to 39,437 CREs is described, but the criteria for including ChIP-seq peaks are not detailed. It is unclear how the models trained on ATAC-seq peaks generalize to ChIP-seq-defined regions, which may have different characteristics. The text does not specify whether new models were trained for this expanded set or if the existing models were applied directly.
- **Why it matters** The csVISIONS resource is a key deliverable. If the methodology for the expanded set is not rigorous, the resource may contain unreliable predictions.
- **Resolution test** Clarify the model training and application for the expanded CRE set. Provide performance metrics for the expanded set and discuss potential biases introduced by combining data from different assay types.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, Model Training
- **Evidence pointer** "Models were trained with ls-gkm gkmtrain[31] as previously described. Validation and sequence scoring similarly follows as previously described[27]."
- **Issue** The methods rely heavily on "as previously described" without providing sufficient detail for replication. Key parameters such as k-mer size, number of gapped k-mers, and SVM hyperparameters are not stated.
- **Required correction** Provide a full description of the training procedure, including all relevant hyperparameters, or include a detailed supplementary methods section.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Models Built From snATAC are Accurate and Specific
- **Evidence pointer** "The peak sets were split such that 80% of the peaks were used for model training. The remaining 20% of peaks were cross referenced against the outgroups from other cell classes and combined to create a universal test set."
- **Issue** The description of the test set construction is ambiguous. It is unclear whether the "universal test set" contains peaks from all cell classes or only those that are not shared. The potential for data leakage between training and test sets is not addressed.
- **Required correction** Clarify the exact composition of the test set and describe how overlap between training and test peaks was avoided.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results, Variant Impact Predictions Identify Critical Sequence Motifs
- **Evidence pointer** "Scanning across the core sequence of a motif and its surrounding sequence context, we have demonstrated the cell-class-specific effect of motif disruption"
- **Issue** The term "VIP scores" is used extensively but not formally defined in the text. The relationship between VIP scores and deltaSVM scores is not explicitly explained.
- **Required correction** Define VIP scores clearly in the methods or results, and explain how they relate to the deltaSVM framework.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, A Resource for cell-class-specific Human Retinal Regulatory Variant Predictions
- **Evidence pointer** "This analysis entitled 'Cell-class-Specific Variant Impact Scores in Ocular Non-coding Sequences' (csVISIONS) is available on the UCSC genome browser"
- **Issue** The URL is provided, but the text does not describe the user interface, data format, or how to query the resource. This limits the immediate usability for readers.
- **Required correction** Include a brief description of the resource's features and usage instructions, or refer to a detailed online documentation.

## Risk / unsupported claims
- The claim of "accuracy over 90%" is unsupported without access to the actual performance data and validation details.
- The claim that "Correlations to massively parallel reporter assays support the predictive value" is weakly supported given the modest correlation values and lack of statistical context.
- The statement that "VIP scores highlight still other motifs that are predicted to be more essential in mature cells than developing cells" is not backed by specific data in the text.
- The generalizability of the models to ChIP-seq-defined CREs in the expanded csVISIONS resource is not established.
- The claim that the models can "rapidly prioritize patient variants" is plausible but not demonstrated with a concrete clinical example or benchmark.