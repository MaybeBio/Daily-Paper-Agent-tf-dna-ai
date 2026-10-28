## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors report that persistent CTCF binding sites (P-CTCF-BSs), a subclass resistant to CTCF knockdown, exhibit elevated mutation rates across multiple cancer types. They developed a machine learning tool (CTCF-INSITE) to predict P-CTCF-BSs from genomic and epigenomic features, validated predictions against experimental data, and demonstrated that disruptive mutations at P-CTCF-BSs are enriched at chromatin loop anchors, suggesting functional impact on 3D genome organization in cancer.
- **Visible evidence base** Methods sections describing datasets, feature engineering, model training/validation, ChIP-seq and ChIA-PET processing, allele-specific analyses, FPDB assays, and permutation tests; Results sections with figures referenced (Figures 1–4, Supplementary Figures S1–S13, Supplementary Tables S1–S7)
- **Missing materials affecting confidence** Actual figure images and supplementary data files were not provided; specific numerical results (e.g., effect sizes, confidence intervals, exact p-values beyond thresholds) are not fully reported in the text; details on hyperparameter tuning, feature selection procedures, and model calibration are incomplete; information on multiple testing corrections for pan-cancer analyses is not fully described

## Reviewer

### Overall assessment
This manuscript addresses an important and timely question: whether a specific subclass of CTCF binding sites, those resistant to perturbation, are preferentially mutated in cancer. The authors present a compelling hypothesis, a novel computational tool, and a pan-cancer analysis that could have significant implications for understanding non-coding drivers of tumorigenesis. The combination of machine learning prediction with experimental validation (FPDB assays) and functional genomic analyses (allele-specific binding, looping) is a strength. However, the manuscript as presented has several technical gaps that need to be addressed before the central claims are fully established. The reliance on predicted rather than experimentally validated P-CTCF-BSs for the pan-cancer analysis, the incomplete description of model development and validation, and the potential for confounding factors in the mutation enrichment analyses require careful scrutiny. The work is potentially important, but the current evidence base is not sufficient to fully support all conclusions.

### Who would be interested in the results, and why
Cancer genomicists and computational biologists studying non-coding mutations and 3D genome organization would be the primary audience. The finding that a specific, functionally defined subclass of CTCF sites is a mutational hotspot across diverse cancer types could inform variant prioritization in cancer genome sequencing efforts. Researchers studying CTCF biology, chromatin architecture, and gene regulation would also be interested in the novel insights into the properties of persistent versus labile CTCF binding. The CTCF-INSITE tool itself may be of practical use to the broader epigenomics community for annotating CTCF sites based on predicted persistence.

### Major strengths
1. The identification of P-CTCF-BSs as a distinct subclass with elevated mutation rates is a novel and potentially significant observation that extends previous work on CTCF mutations in cancer.
2. The development of CTCF-INSITE, a machine learning tool that integrates multiple genomic and epigenomic features, is a valuable resource. The out-of-sample validation on an independent cell line (IMR-90) is a good practice.
3. The multi-layered validation approach, including allele-specific binding analysis, ChIA-PET-based looping analysis, and in vitro FPDB assays, provides orthogonal evidence for the functional impact of the identified mutations.
4. The pan-cancer scope (12 cancer types) strengthens the generalizability of the findings and suggests a common mechanism.
5. The use of permutation tests and trinucleotide context simulation to control for background mutation rates is methodologically sound.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Reproducibility
- **Claim pointer** The claim that CTCF-INSITE accurately predicts P-CTCF-BSs, which is foundational for the pan-cancer analysis.
- **Evidence pointer** Methods: "Prediction of P-CTCF-BSs"; Results: "P-CTCF-BSs can be predicted from distinct genomic and epigenomic features" (Figure 1B)
- **Concern** The description of the machine learning model development is insufficient for reproducibility and critical evaluation. Key details are missing: (1) the exact list of 15 features and how each was computed for the training data (e.g., how "constitutive binding" was defined across the 40-cell-line panel); (2) the procedure for hyperparameter tuning for the random forest model (e.g., number of trees, tree depth, and how 'mtry' was optimized beyond stating the optimal value is 3); (3) the handling of class imbalance between P- and L-CTCF-BSs; (4) the criteria for choosing the probability threshold to define "persistent" vs "non-persistent" for downstream analysis; (5) the performance metrics (AUC, AUC-PR) are reported for the out-of-sample test, but the variance or confidence intervals are not provided, making it difficult to assess the stability of the model. Furthermore, the model was trained on LNCaP data and tested on IMR-90, but the features used for IMR-90 were a subset (13 features, excluding chromatin looping and replication timing). The manuscript does not clarify if the model was retrained with these 13 features for the out-of-sample test, or if the model trained on 15 features was applied with missing values. This is a critical methodological distinction.
- **Why it matters** The entire pan-cancer analysis relies on the accuracy of CTCF-INSITE predictions. If the model is not robust, well-calibrated, or its development is not transparent, the downstream conclusions about mutational enrichment at predicted P-CTCF-BSs are undermined. The lack of detail prevents other researchers from replicating the tool or assessing its potential biases.
- **Resolution test** The authors must provide a complete and detailed description of the model development pipeline, including all feature definitions, hyperparameter tuning procedures, class imbalance handling, threshold selection, and a clear explanation of how the out-of-sample test was conducted (i.e., retraining with 13 features or imputation). They should also report performance metrics with confidence intervals and, ideally, perform an additional out-of-sample validation on a third, independent cell line.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / Support for claims
- **Claim pointer** The claim that P-CTCF-BS mutations are "disruptive" and lead to reduced CTCF binding and altered looping, implying a functional role in cancer.
- **Evidence pointer** Results: "P-CTCF-BS mutations are enriched at sites of potential 3D genome dysregulation" (Figure 3, Supplementary Figures S8–S10)
- **Concern** The evidence linking predicted disruptive mutations to functional consequences is indirect and incomplete. The FPDB assay validated only four mutations, which is a very small sample size. The selection criteria for these four mutations are not stated (e.g., were they chosen to represent different positions or types of mutations?). The correlation between Δscore and allelic imbalance (Spearman's rs² = 0.41) and between Δscore and looping imbalance (rs² = 0.35) is moderate, and the manuscript does not report the significance of these correlations or the number of sites analyzed. More critically, the analysis showing enrichment of disruptive mutations at loop anchors is performed on predicted P-CTCF-BSs, not experimentally validated ones. The statement that "disruptive mutations were only enriched at loop anchors" needs to be supported by a statistical test comparing enrichment at loop anchors versus non-anchor regions, with appropriate controls for genomic context (e.g., replication timing, chromatin state).
- **Why it matters** The central hypothesis is that these mutations are not just passengers but have functional consequences that may drive cancer. The current evidence, based on a handful of in vitro experiments and correlative genomic analyses, is suggestive but not conclusive. Overstating the functional significance without stronger evidence could mislead the field.
- **Resolution test** The authors should expand the FPDB validation to a larger, systematically selected set of mutations (e.g., 10–20) covering different mutation types and positions. They should provide statistical significance for the correlations between Δscore and allelic imbalance. For the loop anchor enrichment analysis, they should perform a formal statistical test (e.g., logistic regression) that controls for potential confounders and clearly report the effect size and confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Confounding factors
- **Claim pointer** The claim that the elevated mutation rate at P-CTCF-BSs is not driven by location-specific effects (e.g., replication timing, chromatin accessibility).
- **Evidence pointer** Results: "P-CTCF-BSs show a highly elevated mutation rate" (Figure 2, Supplementary Figures S4–S5)
- **Concern** While the authors control for trinucleotide context and examine replication timing, the analysis may not fully account for all known confounders of mutation rate variation. For example, the manuscript does not mention controlling for local GC content, chromatin accessibility (e.g., DNase hypersensitivity), or transcription-associated mutagenesis. The comparison of mutation rates between P- and L-CTCF-BSs is done at the level of peaks, but the peaks may differ in length (200–2000 bp), which could affect the mutation count. The permutation test, as described, samples subsets of all CTCF-BSs, but it is unclear if this accounts for the genomic distance between sites or the clustering of mutations.
- **Why it matters** If the observed enrichment is partly or wholly due to a known confounder, the specific claim about P-CTCF-BS biology would be weakened. The authors need to demonstrate that the enrichment is specific to the "persistence" property, not just a proxy for another genomic feature.
- **Resolution test** The authors should perform a more comprehensive confounding analysis, including controlling for peak length, GC content, and other known mutation rate covariates. They could use a regression-based approach that models mutation count as a function of persistence status and these covariates. They should also consider a matched analysis, where P- and L-CTCF-BSs are matched on key genomic features.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership / Clarity
- **Claim pointer** The overall narrative that P-CTCF-BS mutations are a pan-cancer phenomenon with potential clinical relevance.
- **Evidence pointer** Abstract; Results: "P-CTCF-BS mutations are enriched across multiple cancer types" (Figure 4)
- **Concern** The pan-cancer analysis is presented as a key finding, but the manuscript lacks a clear description of the statistical methods used to compare mutation rates across the 12 cancer types. It is unclear if a single combined analysis was performed or if each cancer type was tested independently. The multiple testing burden (12 cancer types) is not addressed. The choice of the top 10% most persistent sites for the pan-cancer analysis is arbitrary and not justified. The manuscript also does not discuss the clinical or biological significance of the effect sizes. For example, a 1.3-fold enrichment, while statistically significant, may have limited practical impact.
- **Why it matters** The claim of a "pan-cancer" phenomenon is strong and implies broad relevance. The analysis must be statistically rigorous and the effect sizes must be presented in a way that allows the reader to judge their biological importance.
- **Resolution test** The authors should clearly describe the statistical model used for the pan-cancer analysis, including how multiple testing was handled. They should justify the choice of the top 10% threshold and show that the results are robust to this choice (e.g., sensitivity analysis with different thresholds). They should report effect sizes with confidence intervals for each cancer type and discuss the potential biological and clinical implications of these effect sizes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of P-CTCF-BSs
- **Evidence pointer** Methods: "Experimentally-determined P-CTCF-BSs"
- **Issue** The definition of P-CTCF-BSs relies on "resistance to CTCF knockdown," but the exact criteria (e.g., percentage of remaining signal, statistical threshold) are not stated in the main text. This is a critical operational definition.
- **Required correction** Provide a precise, quantitative definition of P-CTCF-BSs as used in this study, referencing the original method paper (Khoury et al.) and stating the specific thresholds applied.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Feature engineering
- **Evidence pointer** Methods: "Features"
- **Issue** The manuscript states that 15 features were investigated, but the list is not explicitly enumerated in the main text. The description of how some features (e.g., "constitutive binding") were calculated is vague.
- **Required correction** Provide a complete list of the 15 features in the main text or a clearly referenced supplementary table, with a brief description of how each was computed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Data availability section
- **Issue** While code and data availability are mentioned, the manuscript does not specify the versions of software packages used (e.g., R, randomForest) or provide a detailed software environment description.
- **Required correction** Include a statement on software versions and dependencies, or provide a container/environment file (e.g., conda environment.yml) for reproducibility.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 4D
- **Evidence pointer** Results: "P-CTCF-BS mutations are enriched across multiple cancer types" (Figure 4D)
- **Issue** The description of the per-base mutation rate analysis is brief. It is unclear how the "relative mutation rate" was calculated and what the error bars represent.
- **Required correction** Clarify the calculation of relative mutation rate and the statistical basis for the error bars in the figure legend or methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion of clinical relevance
- **Evidence pointer** Discussion
- **Issue** The discussion mentions the potential importance of these mutations but does not adequately address the limitations of the study, such as the reliance on predicted sites and the lack of direct evidence for a causal role in tumorigenesis.
- **Required correction** Add a paragraph in the discussion explicitly acknowledging the limitations and outlining what additional evidence would be needed to establish a causal role.

### Technical failings that need to be addressed before the case is established
- R1-M1: Incomplete description of machine learning model development and validation, preventing reproducibility and critical assessment.
- R1-M2: Insufficient experimental and statistical evidence to firmly establish the functional impact of the identified mutations.
- R1-M3: Incomplete control for potential confounding factors in the mutation enrichment analysis.

### Assessment against Nature-style criteria
- **Originality**: The concept of focusing on a functionally defined subclass of CTCF sites (persistent) as mutational hotspots is novel and extends previous work. The development of a predictive tool is a new contribution. This criterion is met.
- **Scientific importance**: If the findings are robust, they could have significant implications for understanding non-coding drivers of cancer and for prioritizing variants in cancer genomes. The potential importance is high, but the current evidence base does not fully establish the significance. This criterion is partially met.
- **Interdisciplinary readership**: The topic sits at the intersection of cancer genomics, epigenomics, and computational biology. The findings would be of interest to researchers in these fields. However, the manuscript is written in a way that may be challenging for non-specialists to fully grasp the methodological nuances. This criterion is partially met.
- **Technical soundness**: The study employs a range of appropriate techniques (machine learning, genomics, biochemistry). However, the lack of detail in the model development and the incomplete statistical analyses are significant technical weaknesses that need to be addressed. This criterion is not fully met.
- **Readability for nonspecialists**: The abstract and introduction are clear, but the methods and results sections are dense and assume significant prior knowledge. The key findings could be communicated more effectively for a broader audience. This criterion is partially met.

### Recommendation posture
**Supportive if technical concerns are resolved.** The central hypothesis is interesting and potentially important. The authors have assembled a substantial dataset and performed a multi-faceted analysis. However, the manuscript in its current form has significant gaps in methodological detail and statistical rigor that prevent full endorsement. The authors should be encouraged to revise the manuscript to address the major concerns, particularly the transparency of the machine learning pipeline and the robustness of the functional and pan-cancer analyses. If these issues are adequately resolved, the work could make a valuable contribution to the field.

## Risk / unsupported claims
- The claim that P-CTCF-BS mutations are "disruptive" and lead to reduced CTCF binding is based on a very small number of in vitro experiments (n=4) and is not fully supported.
- The claim that the enrichment of mutations at P-CTCF-BSs is a "pan-cancer phenomenon" is based on a single analysis with an arbitrary threshold (top 10%) and lacks a clear description of the statistical model and multiple testing correction.
- The claim that the observed mutational enrichment is not driven by location-specific effects is not fully supported, as the analysis does not comprehensively control for all known confounders.
- The generalizability of CTCF-INSITE to all cell types and cancer types is not fully established, as it was trained on a single cell line (LNCaP) and validated on only one other (IMR-90).