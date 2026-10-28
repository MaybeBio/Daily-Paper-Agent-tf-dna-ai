## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, and methods sections
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors characterize genomic features that control estrogen receptor alpha (ER) binding and its effects on gene expression in endometrial cancer, using machine learning applied to EREs in Ishikawa and T-47D cells, and validate SOX17 as a key regulator of ER activity in endometrial cancer
- **Visible evidence base** Results sections describing ERE identification, feature prediction analyses, CRISPR KO screen, SOX17 validation experiments, and associated figures referenced in text
- **Missing materials affecting confidence** Figures and supplemental tables referenced but not provided; detailed methods for machine learning, CRISPR screen, and ChIP-seq analyses not fully described; raw data not accessible

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in understanding ER biology in endometrial cancer, where therapeutic options remain limited compared to breast cancer. The systematic approach of using EREs as anchors and applying machine learning to identify predictive features is methodologically sound and the identification of SOX17 as a key regulator is potentially significant. However, the manuscript has several technical concerns that need to be addressed, particularly regarding the validation of the machine learning models, the interpretation of the CRISPR screen results, and the generalizability of the findings beyond the two cell lines studied. The claim that SOX17 controls ER activity through both transcriptional regulation of ESR1 and co-binding at ER sites is intriguing but requires stronger experimental support. The manuscript would benefit from clearer presentation of the model performance metrics and more rigorous statistical comparisons between cell lines.

- **Who would be interested in the results, and why** Researchers studying estrogen receptor biology, particularly those focused on endometrial cancer, would find this work directly relevant. The findings on cell type-specific ER regulation could inform therapeutic development for endometrial cancer, where ER-targeted therapies have been less successful than in breast cancer. The machine learning approach for predicting ER binding and regulatory activity could be of interest to computational biologists working on transcription factor genomics. The identification of SOX17 as a regulator of ER in endometrial cancer may also interest researchers studying SOX family transcription factors in cancer biology.

- **Major strengths** The systematic use of EREs as a consistent genomic anchor across cell lines is a thoughtful approach. The combination of multiple data types (ChIP-seq, ATAC-seq, PRO-seq, HiChIP) provides a comprehensive view of the regulatory landscape. The validation of computational predictions with functional CRISPR screens and follow-up experiments strengthens the conclusions. The comparison between endometrial and breast cancer cell lines addresses an important clinical question about why ER-targeted therapies work differently in these cancers.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of machine learning approach
  - **Claim pointer** The authors claim that machine learning models can predict ER binding and regulatory activity with high sensitivity and specificity, and that specific features such as relative affinity, chromatin accessibility, and transcription are predictive.
  - **Evidence pointer** Results sections "Predictive multivariable model of ERE binding" and "Predictive multivariable model of regulatory EREs"; Supplemental Figures 4 and 7
  - **Concern** The manuscript reports sensitivity and specificity values for the logistic regression models but does not provide information on how these models were validated. It is unclear whether the reported performance metrics are from training data, cross-validation, or held-out test sets. The risk of overfitting is particularly high given the large number of features tested (including 270 motif clusters) relative to the number of positive examples (935 regulatory EREs in Ishikawa cells). Additionally, the models are trained and tested on the same cell lines, so it is unclear whether the identified features would generalize to other endometrial cancer cell lines or patient samples.
  - **Why it matters** Without proper validation, the reported model performance may be optimistically biased, and the identified predictive features may not be robust. This undermines the central claim that specific genomic features can predict ER binding and regulatory activity.
  - **Resolution test** The authors should provide details on the validation strategy (e.g., cross-validation, held-out test sets) and report performance metrics for each. Ideally, they should validate the models in an independent endometrial cancer cell line or patient-derived data to demonstrate generalizability.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental validation of SOX17 mechanism
  - **Claim pointer** The authors claim that SOX17 controls ER activity in endometrial cancer cells through two mechanisms: (1) regulating ESR1 transcription by binding near the ESR1 gene locus, and (2) binding at ER sites to facilitate ER-driven transcription regulation.
  - **Evidence pointer** Results section "SOX17 is important for ER activity in Ishikawa cells"; Figures 6G and 6H
  - **Concern** The evidence for SOX17 regulating ESR1 transcription is based on ChIP-seq showing SOX17 binding near the ESR1 locus and the observation that ESR1 expression decreases in SOX17 KO cells. However, the manuscript does not demonstrate that SOX17 directly regulates ESR1 transcription through these binding sites. The decrease in ESR1 expression could be an indirect effect of SOX17 loss. Additionally, the claim that SOX17 binding at ER sites facilitates ER-driven transcription is based on overlap analysis, but the manuscript does not show whether SOX17 is required for ER binding at these sites or whether it acts downstream of ER binding.
  - **Why it matters** The proposed dual mechanism for SOX17 action is a key finding of the manuscript. If the mechanisms are not clearly established, the significance of SOX17 as a regulator of ER activity in endometrial cancer is weakened.
  - **Resolution test** The authors should perform additional experiments to demonstrate direct regulation, such as luciferase reporter assays with ESR1 promoter constructs containing wild-type or mutant SOX17 binding sites, or chromatin conformation capture to show SOX17-mediated looping between its binding sites and the ESR1 promoter. For the co-binding mechanism, they could perform ER ChIP-seq in SOX17 KO cells to determine whether ER binding is reduced at sites where SOX17 normally binds.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of findings
  - **Claim pointer** The authors claim that their findings identify genomic features that control ER in endometrial cancer and that these differ from breast cancer, with implications for understanding why ER-targeted therapies are less successful in endometrial cancer.
  - **Evidence pointer** Results sections throughout; Discussion section
  - **Concern** The study relies on two cell lines, Ishikawa and T-47D, to represent endometrial and breast cancer, respectively. While the authors validate some findings in HCI-EC-23, this is only for the predictive models and not for the SOX17 mechanism. The manuscript does not address whether the identified features and mechanisms would be consistent across a broader panel of endometrial cancer cell lines or in patient samples. The patient data analysis is limited to comparing bound EREs between cancer types and does not validate the functional importance of the identified features.
  - **Why it matters** The clinical relevance of the findings depends on whether they generalize beyond the specific cell lines studied. If the identified features are cell line-specific, the implications for understanding and treating endometrial cancer would be limited.
  - **Resolution test** The authors should validate the key findings, particularly the role of SOX17, in additional endometrial cancer cell lines and ideally in patient-derived samples. They could also use publicly available data from larger panels of cell lines to test whether the predictive features generalize.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor of comparisons
  - **Claim pointer** The authors claim that certain features are better predictors of ER binding in one cell line over the other, and that there are significant differences in the features associated with ER activity between endometrial and breast cancer cells.
  - **Evidence pointer** Results sections "Several factors predict ERE binding in a cell type–specific manner" and "Factors that contribute to ER binding are mostly cell type specific"; Figures 2G and 2H
  - **Concern** The manuscript reports differences in predictive features between cell lines but does not provide statistical tests to determine whether these differences are significant. For example, the claim that FOXA1 and JUN are better predictors in T-47D cells while ATAC-seq, LSD1, and SIN3A are better in Ishikawa cells is based on visual comparison of importance scores or AUC values, but no confidence intervals or statistical comparisons are provided. Similarly, the comparison of bound EREs between patient samples uses a Wilcoxon signed-rank test, but the analysis is not described in sufficient detail.
  - **Why it matters** Without statistical rigor, the claim that features are cell type-specific may not be supported. This is a central conclusion of the manuscript and needs to be robustly demonstrated.
  - **Resolution test** The authors should provide statistical comparisons of feature importance or AUC values between cell lines, including confidence intervals or appropriate tests. For the patient sample analysis, they should describe the statistical methods in more detail and ensure the analysis accounts for potential confounders.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of methods
  - **Affected element** Machine learning methodology
  - **Evidence pointer** Methods section "Classification and analysis of bound and regulatory EREs"
  - **Issue** The methods for the machine learning analysis are described only briefly, with reference to Supplemental Methods. The description of the Boruta algorithm and logistic regression models is insufficient to evaluate the appropriateness of the approach.
  - **Required correction** Provide a more detailed description of the machine learning methodology in the main text or ensure the Supplemental Methods contain all necessary details, including hyperparameters, feature selection criteria, and handling of correlated features.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Public data sources
  - **Evidence pointer** Methods section "ChIP-seq" and "ATAC-seq"
  - **Issue** The manuscript states that previously published data were used but does not provide accession numbers or references for all datasets. This limits the ability of readers to reproduce the analyses.
  - **Required correction** Provide a table listing all datasets used, their sources, and accession numbers, either in the main text or as a supplemental table.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation of evolutionary analysis
  - **Affected element** ERE count analysis
  - **Evidence pointer** Results section "Very few EREs in the genome are bound by ER and affect gene expression"
  - **Issue** The shuffling analysis of Chromosome 1 is used to argue for evolutionary pressure maintaining ERE numbers, but the analysis is limited to one chromosome and does not account for potential confounding factors such as GC content or chromatin structure.
  - **Required correction** Acknowledge the limitations of this analysis and consider extending it to additional chromosomes or using more sophisticated null models.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Presentation of CRISPR screen results
  - **Affected element** CRISPR KO screen
  - **Evidence pointer** Results section "CRISPR KO screen reveals factors important for ER activity in Ishikawa cells"
  - **Issue** The description of the CRISPR screen results is brief, and the criteria for defining "significant genes" are not clearly stated. The manuscript mentions 18 significant genes but does not provide the full list or the effect sizes.
  - **Required correction** Provide the full list of significant genes with their effect sizes and statistical significance, either in the main text or as a supplemental table.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity of figures
  - **Affected element** Figures 2, 3, and 6
  - **Evidence pointer** Results sections referencing Figures 2, 3, and 6
  - **Issue** The figures are referenced but not provided in the manuscript text. It is difficult to evaluate the claims without seeing the actual data visualizations.
  - **Required correction** Ensure that all figures are included in the manuscript and that they clearly present the data supporting the claims, with appropriate labels and legends.

- **Technical failings that need to be addressed before the case is established** R1-M1 (model validation), R1-M2 (SOX17 mechanism), R1-M3 (generalizability)

## Risk / unsupported claims
- The claim that SOX17 directly regulates ESR1 transcription is not fully supported by the presented evidence; ChIP-seq binding near the ESR1 locus and reduced ESR1 expression in KO cells are suggestive but not conclusive.
- The claim that SOX17 binding at ER sites facilitates ER-driven transcription is based on overlap analysis but lacks functional validation.
- The claim that the identified features are cell type-specific is not statistically tested.
- The generalizability of the findings beyond Ishikawa and T-47D cells is not established.
- The evolutionary interpretation of ERE counts based on a single chromosome analysis is speculative.
- The performance of the machine learning models may be optimistically biased without proper validation.