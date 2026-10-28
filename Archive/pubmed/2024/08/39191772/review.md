## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, interpretation of results, and claims as supported by the presented evidence
- **Shared manuscript claim summary** The authors report that germline TP53 mutation carriers exhibit cancer-like cfDNA fragmentation patterns independent of cancer status, including increased short fragment proportions, A/T nucleotide enrichment at fragment ends, altered nucleosome positioning at p53 binding sites, and increased chromatin accessibility at developmental and cancer-associated loci. They further claim that machine learning classification can differentiate TP53 mutant from wildtype cfDNA samples and that longitudinal analysis of fragmentation signals enables early cancer detection.
- **Visible evidence base** Results sections covering patient cohort description, fragment size analysis, repeat element analysis, nucleosome footprint analysis, dinucleotide frequency analysis, genome-wide fragmentation profiles, p53 binding site analysis, transcription factor binding site analysis, cancer-associated chromatin analysis, machine learning classification, and longitudinal phenoconverter analysis. Methods sections describing study design, blood processing, sequencing, and computational analyses. Figure legends for Figures 1-9 and references to Supplementary Figures 1-18 and Supplementary Data 1-3.
- **Missing materials affecting confidence** Supplementary figures and datasets referenced throughout but not provided in the submitted text. Specific details on cohort demographics, clinical characteristics, and sample processing timelines are incomplete. The full machine learning methodology, including feature selection and hyperparameter tuning, is not fully described. Details on the longitudinal analysis framework and statistical methods for phenoconverter analysis are incomplete.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive fragmentomic analysis of cfDNA from germline TP53 mutation carriers, identifying several cancer-like fragmentation features that persist independent of cancer status. The study addresses an important gap in understanding how inherited cancer predisposition syndromes affect cfDNA fragmentation patterns, which has direct implications for liquid biopsy implementation in high-risk populations. The work is technically ambitious, integrating multiple fragmentomic features and demonstrating potential clinical utility through longitudinal analysis. However, several concerns regarding cohort composition, statistical rigor, validation of key findings, and the clinical utility claims require careful consideration. The observation of cancer-like fragmentation patterns in cancer-free TP53 mutation carriers is intriguing but raises questions about the specificity of fragmentomic features for cancer detection in this population. The machine learning results, while promising, need more rigorous validation and transparency in methodology. The longitudinal analysis for early cancer detection is based on a small number of phenoconverters and requires cautious interpretation. Overall, the manuscript presents novel and potentially important findings, but the strength of the conclusions needs to be tempered by the limitations in cohort size, validation approaches, and the inherent challenges of studying a rare syndrome.

- **Who would be interested in the results, and why** Researchers and clinicians working in liquid biopsy, cancer early detection, and hereditary cancer syndromes would find this work highly relevant. The findings have direct implications for implementing cfDNA-based surveillance in Li-Fraumeni syndrome patients and potentially other high-risk populations. The fragmentomic characterization of a cancer predisposition syndrome provides fundamental insights into how germline mutations affect chromatin structure and cfDNA biology. The study also contributes to the broader understanding of fragmentomic features in cancer detection, which is relevant to the rapidly growing field of liquid biopsy. The machine learning approaches and longitudinal analysis framework may be of interest to computational biologists and bioinformaticians working on cfDNA analysis. Clinicians managing LFS patients would be particularly interested in the potential for early cancer detection through blood-based assays.

- **Major strengths** The study addresses a clinically important question with direct translational relevance. The comprehensive multi-feature fragmentomic analysis is technically thorough, integrating fragment size, end motifs, nucleosome positioning, and chromatin accessibility. The inclusion of longitudinal samples from phenoconverters is a notable strength, providing preliminary evidence for early cancer detection potential. The authors appropriately control for technical variables including sequencing platform, collection tube, and sequencing run. The comparison with external healthy cohorts strengthens the generalizability of the findings. The study identifies specific biological mechanisms, such as altered p53 binding site accessibility and developmental transcription factor enrichment, that provide plausible explanations for the observed fragmentation patterns. The machine learning approach, while needing more validation, demonstrates the potential for clinical application.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and cohort composition
- **Claim pointer** The authors claim that TP53 mutation carriers exhibit cancer-like cfDNA fragmentation patterns independent of cancer status, based on comparison of 131 cancer-negative samples from TP53 mutation carriers versus 30 healthy wildtype controls.
- **Evidence pointer** Results section "A global reduction of cfDNA fragment size", Figure 2, Supplementary Figures 2 and 4
- **Concern** The control group of 30 healthy TP53-wildtype individuals is relatively small compared to the 131 cancer-negative TP53 mutation carrier samples. The manuscript does not provide details on the age and sex distribution of the control group, which could significantly affect cfDNA fragmentation patterns. Additionally, the TP53 mutation carrier group is heterogeneous, including individuals with different mutation types (missense, nonsense, splice site, etc.) and different cancer histories. The authors do not adequately address potential confounding factors such as age, sex, comorbidities, or medication use that could influence cfDNA fragmentation. The lack of detailed demographic and clinical characterization of both groups limits the interpretability of the observed differences.
- **Why it matters** Without adequate matching and control for confounding variables, the observed differences in cfDNA fragmentation between TP53 mutation carriers and wildtype controls could be attributed to factors other than TP53 mutation status. This is particularly important given the known effects of age, sex, and various physiological conditions on cfDNA fragmentation patterns. The small control group size also raises concerns about the stability and representativeness of the baseline measurements.
- **Resolution test** The authors should provide detailed demographic and clinical characteristics of both groups, including age, sex, body mass index, medication use, and comorbidities. Statistical analyses should be adjusted for these potential confounders. Alternatively, the authors could consider using a larger, well-matched control cohort or performing sensitivity analyses to ensure the robustness of their findings.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of machine learning model
- **Claim pointer** The authors claim that machine learning classification resulted in robust differentiation between TP53 mutant versus wildtype cfDNA samples with AUC-ROC values ranging from 0.710 to 1.000.
- **Evidence pointer** Results section "Classification of TP53 status using fragmentomic features", Figure 8, Supplementary Figure 15, Supplementary Table 1
- **Concern** The machine learning methodology lacks critical details necessary for evaluation and replication. The manuscript does not specify the exact features used in the final model, the feature selection procedure, or the hyperparameter tuning process. The reported AUC-ROC range of 0.710-1.000 is extremely wide, suggesting high variability across features or cross-validation folds. The AUC of 1.000 achieved with end motifs raises concerns about potential overfitting or data leakage, especially given the small sample size. The manuscript does not report confidence intervals for the integrated model or provide external validation in an independent cohort. The nested cross-validation approach is described but the implementation details are insufficient to assess its validity.
- **Why it matters** The clinical utility of the proposed approach depends on the reliability and generalizability of the machine learning model. Without proper validation and transparent methodology, the reported performance metrics may not reflect real-world performance. The extremely high AUC values, particularly the perfect classification with end motifs, suggest the possibility of overfitting or batch effects that could severely limit the model's utility in clinical settings.
- **Resolution test** The authors should provide a detailed description of the machine learning pipeline, including all features, feature selection methods, hyperparameter optimization, and the exact cross-validation scheme. They should report performance metrics with appropriate confidence intervals and, ideally, validate the model in an independent external cohort. The authors should also investigate whether the perfect classification with end motifs is driven by technical artifacts or batch effects.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Clinical utility claims for early cancer detection
- **Claim pointer** The authors claim that intra-patient longitudinal analysis of ctDNA fragmentation signal enabled early cancer detection, with specific examples of detection prior to clinical diagnosis.
- **Evidence pointer** Results section "Integrated longitudinal analysis for early cancer detection", Figure 8B, Supplementary Figure 18
- **Concern** The longitudinal analysis for early cancer detection is based on a very small number of phenoconverters (n=5 forward, n=9 reverse). The manuscript does not provide sufficient detail on the statistical framework used to define "detection" thresholds or how the cancer detection limits were established. The reported sensitivity and specificity values (NPV 73.91%, PPV 80.00%) are based on limited data and have wide confidence intervals. The authors do not adequately address the potential for lead-time bias or the clinical significance of the detection window. The comparison with conventional surveillance methods is not clearly defined, and the manuscript does not specify what "clinical diagnosis" means in this context or how it was confirmed.
- **Why it matters** The claim of early cancer detection has significant clinical implications for LFS patient management. However, the evidence base is too limited to support such claims. The small number of phenoconverters, lack of a predefined statistical framework, and absence of external validation make it difficult to assess the true clinical utility of the approach. Overstating the potential for early detection could lead to inappropriate clinical implementation.
- **Resolution test** The authors should clearly define the statistical framework for determining cancer detection thresholds, provide confidence intervals for sensitivity and specificity estimates, and discuss the limitations of the small sample size. They should also provide more detailed case descriptions of the phenoconverters, including the timeline of detection relative to clinical diagnosis and the clinical outcomes. External validation in a larger cohort would be necessary to support the clinical utility claims.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation and mechanistic claims
- **Claim pointer** The authors claim that altered nucleosome positioning at p53 binding sites and increased chromatin accessibility at developmental and cancer-associated loci in TP53 mutation carriers reflect germline TP53 dysfunction affecting chromatin architecture.
- **Evidence pointer** Results sections "Unstable nucleosome positioning at p53 associated sites" and "Increased chromatin accessibility at developmental and cancer-associated loci", Figures 6 and 7
- **Concern** The manuscript presents correlative observations linking cfDNA fragmentation patterns to chromatin structure but does not provide direct evidence for the proposed mechanisms. The inference that altered nucleosome positioning at p53 binding sites reflects p53 dysfunction is plausible but not directly tested. The authors do not account for potential confounding factors such as differences in blood cell composition between TP53 mutation carriers and wildtype controls, which could significantly affect cfDNA fragmentation patterns. The use of cfDNA to infer chromatin accessibility is an indirect approach that requires careful validation. The manuscript does not discuss alternative explanations for the observed patterns, such as differences in apoptosis or nuclease activity between groups.
- **Why it matters** The biological interpretation is central to the manuscript's significance. If the observed fragmentation patterns are not directly related to p53 function but rather to other factors, the conclusions would need substantial revision. The lack of direct mechanistic evidence weakens the causal claims and limits the generalizability of the findings.
- **Resolution test** The authors should provide additional evidence supporting the link between p53 dysfunction and the observed chromatin changes, such as comparison with TP53 knockout models or analysis of p53 target gene expression in the same samples. They should also control for blood cell composition differences and discuss alternative explanations for their findings.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation and reproducibility
- **Claim pointer** The authors claim that their fragmentomic analysis is robust across sequencing platforms, demonstrating high correlation between Illumina and Ultima sequencing data.
- **Evidence pointer** Results section "A global reduction of cfDNA fragment size", Supplementary Figure 2J-L
- **Concern** The comparison between Illumina and Ultima sequencing platforms is performed on a small subset of samples (n=58) and the manuscript does not provide sufficient detail on the validation approach. The correlation coefficients (R2 = 0.973-0.988) are reported but the manuscript does not specify whether these are Pearson or Spearman correlations or provide confidence intervals. The authors do not address potential systematic differences between platforms that could affect fragmentomic features, such as library preparation protocols, sequencing depth, or read length. The manuscript also does not describe how the platform comparison was integrated into the main analysis or whether platform-specific effects were adjusted for in the machine learning models.
- **Why it matters** Reproducibility across sequencing platforms is essential for clinical implementation. If the fragmentomic features are not consistent across platforms, the clinical utility of the approach would be severely limited. The lack of detailed validation information makes it difficult to assess the robustness of the findings.
- **Resolution test** The authors should provide a more detailed comparison of the two platforms, including analysis of potential batch effects, platform-specific biases, and the impact of sequencing depth on fragmentomic features. They should also describe how platform effects were handled in the main analysis and whether the machine learning models were trained and tested on data from both platforms.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of reporting
- **Affected element** Patient cohort description
- **Evidence pointer** Results section "Patient cohort", Figure 1A
- **Issue** The description of the patient cohort is incomplete. The manuscript does not provide details on the age range, sex distribution, or specific cancer types for the LFS-AC group. The criteria for classifying patients as "cancer-free" are not clearly defined, and the duration of cancer-free follow-up is not specified.
- **Required correction** Provide a comprehensive table of patient demographics and clinical characteristics, including age, sex, cancer history, and follow-up duration. Clearly define the criteria for cancer-free status and specify the surveillance methods used to confirm cancer status.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Multiple comparisons and effect sizes
- **Evidence pointer** Throughout Results, Supplementary Data 2 and 3
- **Issue** The manuscript reports numerous statistical tests across multiple fragmentomic features and comparisons but does not consistently report effect sizes or confidence intervals. The correction for multiple testing is mentioned but the specific methods and adjusted p-values are not consistently provided.
- **Required correction** Report effect sizes and confidence intervals for all main comparisons. Clearly describe the multiple testing correction method used and provide adjusted p-values for all reported comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Biological validation
- **Affected element** p53 binding site analysis
- **Evidence pointer** Results section "Unstable nucleosome positioning at p53 associated sites", Figure 6
- **Issue** The analysis of p53 binding sites relies on a single ChIP-seq dataset from the GTRD database. The manuscript does not discuss potential limitations of this dataset, such as cell type specificity or batch effects, and does not validate the findings using independent p53 ChIP-seq data.
- **Required correction** Discuss the limitations of the GTRD dataset and, if possible, validate the key findings using an independent p53 ChIP-seq dataset or experimental validation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clinical implications
- **Affected element** Discussion of clinical utility
- **Evidence pointer** Discussion section
- **Issue** The discussion of clinical utility is somewhat speculative and does not adequately address the practical challenges of implementing the proposed approach in clinical settings, such as cost, turnaround time, and integration with existing surveillance protocols.
- **Required correction** Provide a more balanced discussion of the clinical implications, including the practical challenges and potential solutions for implementing fragmentomic analysis in LFS patient management.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability
- **Evidence pointer** Methods section, Data availability statement
- **Issue** The manuscript does not provide a clear statement on the availability of the code and processed data used in the analysis. This limits the reproducibility of the findings.
- **Required correction** Provide a detailed data availability statement, including information on where the raw sequencing data, processed data, and analysis code can be accessed.

## Risk / unsupported claims
- The claim that machine learning classification achieved AUC-ROC of 1.000 using end-motif features is not adequately supported given the small sample size and lack of external validation. This perfect performance raises concerns about overfitting or data leakage.
- The claim of early cancer detection through longitudinal analysis is based on a very small number of phenoconverters (n=5) and lacks a predefined statistical framework. The reported sensitivity and specificity values have wide confidence intervals and should be interpreted with caution.
- The biological interpretation that altered nucleosome positioning at p53 binding sites reflects germline TP53 dysfunction is correlative and not directly tested. The manuscript does not provide mechanistic evidence supporting this causal claim.
- The comparison between Illumina and Ultima sequencing platforms is based on a small subset of samples and lacks sufficient detail to assess the robustness of the cross-platform validation.
- The claim that TP53 mutation carriers exhibit "cancer-like" fragmentation patterns is based on comparison with healthy controls, but the manuscript does not directly compare the fragmentation patterns of cancer-free TP53 mutation carriers with those of cancer patients without TP53 mutations, which would be necessary to fully support this characterization.