## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, materials and methods, and supplementary figure/data set legends.
- **Assessment boundary** Scientific content, methodology, data interpretation, and internal consistency of the provided manuscript. No external data, code, or supplementary files were accessed.
- **Shared manuscript claim summary** The authors present a machine learning framework integrating known cis-regulatory elements, DAP-seq data, and DNase I hypersensitive sites to model temporal transcriptional responses to wounding in Arabidopsis thaliana. They identify novel putative cis-regulatory elements (pCREs) that improve prediction accuracy, validate several elements experimentally via CRISPR-Cas9 mutagenesis and in vitro binding assays, and characterize regulatory differences between jasmonic acid (JA)-dependent and JA-independent wound responses. They further apply the framework to the glucosinolate biosynthesis pathway.
- **Visible evidence base** Main text figures (Figures 1–10), supplemental figure legends (S1–S6), supplemental data set legends (S1–S13), and methods descriptions.
- **Missing materials affecting confidence** The actual supplemental data sets (S1–S13) were not provided. The GitHub repositories for code are referenced but not accessible in this review. Raw data, model performance metrics beyond those summarized in text, and full statistical outputs are not available for independent verification.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive and ambitious computational framework for dissecting the temporal cis-regulatory code of wounding response in Arabidopsis. The integration of multiple regulatory data types is timely and the experimental validation of predicted elements strengthens the study. However, several technical concerns regarding model evaluation, data handling, and the strength of some conclusions need to be addressed. The manuscript is of interest to plant molecular biologists and computational biologists, but the current evidence does not fully establish all claims, particularly regarding the novelty and functional significance of the newly identified pCREs.
- **Who would be interested in the results, and why** Researchers studying plant stress responses, transcriptional regulation, cis-regulatory element discovery, and systems biology. The framework is potentially transferable to other stress and hormone response systems, making it relevant to a broader computational biology audience. The identification of new regulatory elements for wounding and JA signaling could inform crop improvement strategies for stress tolerance.
- **Major strengths**
  1. The study addresses a significant gap in understanding the global regulatory logic of wounding response, moving beyond single-gene studies.
  2. The integration of diverse regulatory features (known motifs, DAP-seq, chromatin accessibility) into a unified predictive model is a methodological strength.
  3. The experimental validation of predicted elements using CRISPR-Cas9 and in vitro binding assays provides functional evidence that is often lacking in computational studies.
  4. The temporal resolution of the analysis (0.25–24 h) captures the dynamic nature of the response, which is a notable improvement over static analyses.
  5. The comparison of JA-dependent and JA-independent regulatory programs is a novel contribution.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of model evaluation
- **Claim pointer** The authors claim that pCRE-based models outperform models using known CREs, DAP-seq, and DHSs (e.g., "pCRE-based models (F-measures: 0.73–0.87) outperformed both known CREs (0.67–0.74) and known CREs/DAP-seq/DHSs-based models (0.66–0.73; Figure 9)").
- **Evidence pointer** Results section "Finding important temporal putative cis-regulatory elements for wound response" and "Modeling the regulatory code of JA-dependent and JA-independent gene response across wounding time-points"; Figure 2A, Figure 9; Supplemental Data Set S4.
- **Concern** The comparison of model performance across feature sets is potentially confounded by the number of features. The pCRE set is likely much larger than the known CRE set, and models with more features can achieve higher training performance due to overfitting, even if generalization is not improved. The authors do not report whether feature selection or dimensionality reduction was applied to the pCRE set before model building. The F-measure improvements are modest (e.g., 0.69 to 0.74 for early time points) and the statistical significance of these differences is not reported. Without proper control for feature count and without confidence intervals or significance tests, the claim of superiority for pCRE-based models is not fully established.
- **Why it matters** The central conclusion of the paper, that newly identified pCREs provide predictive power beyond known elements, rests on this comparison. If the improvement is an artifact of feature count, the biological interpretation of the pCREs as functionally important regulatory elements is weakened.
- **Resolution test** The authors should report model performance using matched feature counts (e.g., top N pCREs vs. N known CREs), provide confidence intervals or statistical tests for F-measure differences, and ideally evaluate on a held-out temporal time point to test generalization.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data provenance and suitability
- **Claim pointer** The study relies on the wounding time-course data from Kilian et al. (2007) and hormone data from Goda et al. (2008), assuming these datasets are directly comparable for identifying JA-dependent and JA-independent genes.
- **Evidence pointer** Methods "Expression data sets and analysis"; Results "Modeling the regulatory code of JA-dependent and JA-independent gene response across wounding time-points".
- **Concern** The wounding and hormone datasets were generated in different laboratories, potentially under different growth conditions, developmental stages, and with different microarray platforms or processing pipelines. The authors state that plants were grown under similar conditions, but this is not a substitute for a controlled comparison. The classification of genes as JA-dependent or JA-independent is based on the intersection of wounding and JA responses, but the comparability of the absolute expression values and fold changes across datasets is not demonstrated. Batch effects or platform differences could lead to misclassification and confound the subsequent regulatory analysis.
- **Why it matters** The JA-dependent vs. JA-independent comparison is a key part of the study's contribution. If the underlying gene classification is unreliable, the conclusions about distinct regulatory programs for these two classes are not robust.
- **Resolution test** The authors should provide a detailed comparison of the experimental conditions and data processing for the two datasets. They should also perform a sensitivity analysis, e.g., using different thresholds for defining JA-responsive genes, to show that their conclusions are robust to the classification criteria.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Experimental validation scope
- **Claim pointer** The authors state that they "experimentally validated four of the predicted elements, three of which were not previously known to function in wound-response regulation."
- **Evidence pointer** Results "Experimental validation of important CREs in early wound response" and "Experimental validation of important unknown pCREs at later time-points"; Figures 6–8.
- **Concern** The experimental validation is limited to promoter mutations in two genes (JAZ2 and GER5) for early time points, and in vitro binding plus reporter assays for three pCREs at later time points. The functional validation of the later time point pCREs is indirect, relying on reporter constructs rather than endogenous gene expression. The manuscript does not demonstrate that mutation of these later pCREs affects the expression of their predicted target genes in planta. The validation is therefore incomplete, particularly for the claim that these elements are "important" for wounding response.
- **Why it matters** The study's impact depends on the confidence that the predicted pCREs are biologically functional. The current validation provides proof-of-concept for the approach but does not fully establish the functional relevance of the newly identified elements, especially at later time points.
- **Resolution test** The authors should extend the CRISPR-Cas9 mutagenesis to at least one target gene for a later time point pCRE and demonstrate altered wounding-induced expression. Alternatively, they should temper the claim of "importance" for these elements and clearly state the limitations of the reporter-based validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of chromatin accessibility data
- **Claim pointer** The authors find that DHSs are among the most important features for predicting wounding response, particularly at later time points, and interpret this as evidence for the role of chromatin accessibility in regulating temporal responses.
- **Evidence pointer** Results "Determining the relative importance of known motifs and additional regulatory information for predicting temporal wound response"; Figure 3.
- **Concern** The DHS data used were generated from unwounded plants (Zhang et al., 2012). The authors acknowledge this limitation but still use these data to infer the importance of chromatin accessibility in wounding response. The interpretation is problematic because chromatin accessibility is highly dynamic and stress-responsive. A DHS that is important in the prediction model may simply be a marker of a constitutively open region, not a region that changes accessibility upon wounding. The claim that these DHSs are "important" for wounding response is therefore not directly supported by the data.
- **Why it matters** The study aims to understand the regulatory logic of wounding response. Using static chromatin data to infer dynamic regulatory processes could lead to incorrect conclusions about the role of chromatin remodeling in this response.
- **Resolution test** The authors should either obtain DHS data from wounded plants or clearly reframe their conclusions to state that they are identifying features associated with wounding-responsive genes in their basal chromatin state, not features that change upon wounding. The latter interpretation is more accurate but less impactful.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the model
- **Claim pointer** The authors suggest that their framework "can be applied to assess the cis-regulatory mechanisms in other contexts."
- **Evidence pointer** Conclusion section.
- **Concern** The model is trained and tested on a single stress condition (wounding) in a single species (Arabidopsis). The pCREs identified are specific to this context. The claim of generalizability is not supported by any evidence, such as application to a different stress or dataset. The framework itself may be generalizable, but this is not demonstrated.
- **Why it matters** The broader impact of the study is partly predicated on its applicability to other systems. An unsupported claim of generalizability overstates the findings.
- **Resolution test** The authors should either provide an example application to another stress or dataset, or temper the claim to state that the framework is "potentially applicable" and describe the steps required for such application.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Methods "Machine learning models"
- **Evidence pointer** Methods section.
- **Issue** The description of the machine learning pipeline lacks sufficient detail for reproduction. The exact parameters for the grid search are given, but the criteria for selecting the "optimal" hyperparameters are not stated. The number of trees in the random forest and the kernel parameters for the SVM are not fully specified.
- **Required correction** Provide a complete list of hyperparameters tested and the selection criterion (e.g., maximizing F-measure on the validation set). Consider making the code and a sample dataset publicly available in a repository with a clear license.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results "Experimental validation of important CREs in early wound response"
- **Evidence pointer** Figure 6.
- **Issue** The statistical analysis for the RT-qPCR data is not described in the main text. The number of biological replicates is stated, but the statistical test used and the error bars shown in the figure are not defined.
- **Required correction** Add a description of the statistical test used for the RT-qPCR data in the figure legend or methods, and define the error bars (e.g., standard error of the mean, standard deviation).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout the manuscript.
- **Evidence pointer** Abstract, Results, Discussion.
- **Issue** The term "regulatory code" is used to describe the set of pCREs and their importance. This term is often used to imply a complete, decipherable set of rules. The authors' model is predictive but not fully explanatory, and the term may overstate the completeness of the understanding.
- **Required correction** Consider using more precise terms such as "predictive regulatory model" or "cis-regulatory features" instead of "regulatory code" to avoid overstatement.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Figure 1A
- **Evidence pointer** Figure 1A.
- **Issue** The heatmap in Figure 1A is described in the text, but the color scale and the meaning of the diagonal and lower triangle values are not fully explained in the figure legend.
- **Required correction** Expand the figure legend to clearly explain the color scale, the diagonal values, and the lower triangle values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods "Accession numbers"
- **Evidence pointer** Methods section.
- **Issue** The accession numbers for the processed data (e.g., the list of genes in each cluster, the pCREs identified) are not provided. Only the raw data sources are listed.
- **Required correction** Provide accession numbers or a persistent link to the processed data files, such as the gene lists and pCRE coordinates, to facilitate reuse.

## Risk / unsupported claims
- The claim that pCRE-based models outperform known CRE-based models is not fully supported due to potential feature-count confounding and lack of statistical testing.
- The classification of genes into JA-dependent and JA-independent groups is based on cross-dataset comparisons that are not validated for comparability.
- The functional importance of pCREs at later time points is not directly demonstrated in planta; the reporter assays provide indirect evidence only.
- The interpretation of DHS importance as evidence for the role of chromatin accessibility in wounding response is not supported by the data, as the DHS data are from unwounded plants.
- The claim of generalizability of the framework to other contexts is not supported by any evidence in the manuscript.