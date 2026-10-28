## Review setup
- **Input scope** Full manuscript text (abstract, background, results, discussion, conclusions, methods, declarations)
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and alignment with stated claims; not editorial or formatting issues
- **Shared manuscript claim summary** The authors propose that sequence-derived DNA conformational flexibility descriptors, implemented in a new Python package (DNAflexpy), improve quantitative prediction of transcription factor binding to nucleosomal DNA across diverse TF families, and that these descriptors capture an interpretable "indirect readout" signal that complements sequence composition and DNA shape. They further claim that position-resolved flexibility footprints align with structural and dynamic evidence from SOX11-bound nucleosomes, and that flexibility features improve classification of occupied versus unoccupied nucleosomal TF binding sites in vivo.
- **Visible evidence base** Abstract, full background, results narrative (without figures), discussion, conclusions, methods, data availability statements
- **Missing materials affecting confidence** All figures and supplementary figures (Fig. 1a–f, 2a–j, 3a–d, 4a–g, 5a–g, 6a–g, S1–S6), figure legends, supplementary tables, and any supplementary methods; specific numerical results (e.g., exact ΔR² values, p-values, effect sizes) are referenced but not fully reproducible from text alone

## Reviewer

### **Overall assessment**
This manuscript addresses a timely and important question: whether sequence-derived DNA flexibility descriptors can quantitatively improve prediction of TF binding to nucleosomal DNA, and whether such descriptors provide interpretable evidence for indirect readout in chromatin contexts. The authors have assembled a substantial dataset (226 NCAP-SELEX datasets, PIONEAR-seq, ENCODE ChIP-seq/MNase-seq) and developed a new software package (DNAflexpy) that is a potentially useful community resource. The core idea, that flexibility descriptors capture information beyond k-mer composition, is plausible and supported by the reported trends. However, the manuscript as presented has several critical gaps that prevent full evaluation: (1) all figures are missing, making it impossible to assess the magnitude and quality of the reported effects; (2) the statistical framework for comparing models (e.g., nested cross-validation, significance testing of ΔR²) is not fully described; (3) the interpretation of "indirect readout" is correlative and the causal link is not established; (4) the in vivo classification analysis appears to have potential circularity issues (using the same data for feature selection and evaluation). The work is promising and likely of interest to the chromatin and TF biology communities, but the current evidence base is insufficient to fully support the strong conclusions drawn.

### **Who would be interested in the results, and why**
- **Chromatin biologists** studying how TFs access nucleosomal DNA, particularly those interested in pioneer factors and the mechanisms of nucleosome recognition.
- **Computational biologists** developing predictive models of TF-DNA binding, especially those incorporating structural or biophysical features beyond sequence.
- **Biophysicists** interested in DNA mechanics and how sequence-dependent flexibility influences protein-DNA recognition.
- **Developers of bioinformatics tools** who may adopt DNAflexpy as a new resource for computing flexibility descriptors.
- **Researchers studying regulatory genomics** who want to interpret noncoding variants in terms of structural compatibility rather than just sequence motif disruption.

### **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that "flexibility-augmented models improved prediction over mononucleotide baselines in most datasets" and that "position-resolved flexibility footprints revealed deformation signatures at cognate motifs and flanking regions across diverse TF families."
- **Evidence pointer** All figures (Fig. 1–6) and supplementary figures (S1–S6) are referenced but not provided in the submitted text
- **Concern** The entire results section is written as a narrative referencing figures that are not included in the provided material. Without the figures, it is impossible to evaluate the magnitude of the reported effects, the quality of the model fits, the distribution of ΔR² values across datasets, the visual clarity of the flexibility footprints, or the validity of the family-level comparisons. The text alone provides summary statistics (e.g., median ΔR² = 10.46 over 1-mer baseline) but these cannot be independently verified or contextualized.
- **Why it matters** The central claims of the paper rest on quantitative comparisons and visualizations that are entirely absent from the provided material. A reviewer cannot assess whether the reported improvements are meaningful, consistent, or potentially driven by outliers or artifacts.
- **Resolution test** Provide all figures and supplementary figures with complete legends, including axis labels, error bars, and statistical annotations. Ensure that the figures directly support the specific claims made in the text (e.g., show per-dataset ΔR² distributions, family-level boxplots, footprint heatmaps, ROC curves).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that "flexibility features retained predictive value after trinucleotide sequence context had already been included" and that "the residual gain was smaller but indicates that the flexibility descriptors capture predictive information not fully represented by trinucleotide composition."
- **Evidence pointer** Methods section "Multiple linear regression" and "Quantifying nonredundant model performance using Cohen's f²"
- **Concern** The statistical framework for comparing nested models is not fully described. Specifically: (1) How is the significance of ΔR² or ΔMCC assessed? The text reports p-values from Wilcoxon signed-rank tests, but it is unclear whether these are computed on per-dataset ΔR² values or on some aggregated metric. (2) The nested cross-validation procedure is described, but the variance of the performance estimates across outer folds is not reported. (3) For the Cohen's f² calculation, the formula is given, but the interpretation of f² values in the context of cross-validated R² (which can be negative) is not discussed. (4) The comparison between DNAflexpy and ShapeFL features is described as showing "strong concordance," but no formal test of equivalence or non-inferiority is provided.
- **Why it matters** The claim that flexibility descriptors provide non-redundant predictive information is central to the paper's thesis. Without a rigorous statistical framework, it is unclear whether the observed improvements are statistically significant, practically meaningful, or within the noise of the cross-validation procedure.
- **Resolution test** Provide a detailed description of the statistical testing procedure, including how p-values are computed, whether multiple testing corrections are applied, and how the variance of performance estimates is handled. Report confidence intervals for ΔR² and ΔMCC values. Consider using paired statistical tests that account for the correlation between models evaluated on the same data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Circularity in in vivo analysis
- **Claim pointer** The manuscript claims that "flexibility signatures distinguish nucleosomal from non-nucleosomal OSK binding sites and pioneered from non-pioneered GATA3 regions, and improve classification of occupied TF binding sites across multiple ENCODE cell lines and TF families."
- **Evidence pointer** Methods section "Genome-wide classification of TF binding sites in nucleosomal regions with XGBoost"
- **Concern** The classification framework uses ChIP-seq peaks as positives and unbound motif instances in nucleosomal regions as negatives. However, the feature set includes flexibility descriptors computed from the same sequence that defines the motif and its flanks. If the flexibility descriptors are derived from sequence composition, they may be partially redundant with the k-mer features, and the improvement in classification may reflect overfitting to the training data rather than a generalizable signal. Additionally, the hyperparameter tuning is performed on a pooled HepG2 set and then applied to other cell lines, but it is unclear whether the model is retrained for each cell line or whether the same model is applied. The potential for data leakage between training and evaluation sets is not addressed.
- **Why it matters** The in vivo classification analysis is the most direct evidence that flexibility descriptors are relevant in a genomic context. If the analysis is circular or overfitted, the conclusions about the biological relevance of flexibility would be substantially weakened.
- **Resolution test** Describe the exact training and evaluation protocol, including how hyperparameters are selected, whether features are standardized within each cell line, and how the train/test split is performed. Consider using a nested cross-validation scheme for hyperparameter tuning and report performance on held-out cell lines. Address the potential redundancy between flexibility and k-mer features by reporting the correlation between feature sets and using ablation studies.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability of flexibility footprints
- **Claim pointer** The manuscript claims that "position-resolved flexibility footprints recover TF mediated DNA deformation signatures" and that "the same central motif positions carry the strongest flexibility footprint, undergo structural deformation in the SOX11-DNA crystal structure, separate high-from low-affinity sites by MGW, and stabilize after SOX binding."
- **Evidence pointer** Results section "Position resolved flexibility footprints recover TF mediated DNA deformation signatures"
- **Concern** The comparison between model-derived flexibility footprints and MD simulations is compelling but the methodology for aligning the two is not fully described. Specifically: (1) How are the footprint positions (from the regression model) mapped to the MD simulation positions? (2) The MD simulations are described as "taken from the public dataset of Ozden et al." but the specific systems analyzed (SHL0, SHL2, SHL4) and the criteria for selecting these positions are not justified. (3) The statistical comparison between footprint peaks and MD-derived flexibility peaks is not described; is this a qualitative visual comparison or a quantitative test?
- **Why it matters** The convergence of model predictions with structural and dynamic data is the strongest evidence for the biological validity of the flexibility descriptors. Without a rigorous quantitative comparison, the claim of "recovery" is not fully supported.
- **Resolution test** Provide a detailed description of how footprint positions are aligned to MD simulation positions, including any sequence alignment or coordinate mapping. Report quantitative correlations or overlap statistics between footprint peaks and MD-derived flexibility peaks, with appropriate significance testing.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of DNAflexpy descriptors
- **Claim pointer** The manuscript claims that "DNAflexpy descriptors capture a sequence-encoded structural signal" and that "the convergence with an independent shape-fluctuation model argues against the flexibility signal being an artifact of a single parametrization."
- **Evidence pointer** Results section "DNAflexpy and Deep DNAshape identify overlapping structural signals in TF-nucleosome binding"
- **Concern** The comparison with ShapeFL features is limited to a single analysis (NCAP-SELEX). It is unclear whether the concordance between DNAflexpy and ShapeFL is consistent across different datasets, TF families, or sequence contexts. Additionally, the manuscript does not discuss the potential limitations of the DNAflexpy descriptors themselves, such as their sensitivity to the choice of window size, the specific parameterization of each descriptor, or the extent to which they capture correlated information.
- **Why it matters** The claim that DNAflexpy captures a generalizable structural signal is important for the utility of the package. If the descriptors are highly correlated with each other or with sequence composition, their added value may be limited.
- **Resolution test** Provide a correlation analysis between the five DNAflexpy descriptors and between DNAflexpy and ShapeFL features. Discuss the independence of the descriptors and their potential redundancy. Consider testing the robustness of the results to different parameterizations of the descriptors.

### **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract and Background
- **Evidence pointer** Abstract, Background paragraph 1
- **Issue** The term "indirect readout" is used throughout but is not explicitly defined. The authors should clarify whether they refer to sequence-dependent DNA deformability that is recognized by the TF, or to the energetic cost of deforming DNA to fit the TF, or both.
- **Required correction** Add a brief definition of "indirect readout" in the Background, distinguishing it from direct base-specific contacts.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility of software
- **Affected element** Methods, DNAflexpy section
- **Evidence pointer** Methods section "DNAflexpy software and DNA flexibility descriptors"
- **Issue** The manuscript states that DNAflexpy is available on GitHub, but does not specify the version, dependencies, or a DOI for archival purposes. This limits reproducibility.
- **Required correction** Provide a versioned release with a DOI (e.g., via Zenodo) and list the main dependencies (e.g., NumPy, SciPy) in the Methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Declarations, Availability of data and materials
- **Evidence pointer** Declarations section
- **Issue** The PIONSEQ data accession is listed as GSE293508 in the Declarations, but the Methods section references GSE293487. This inconsistency needs to be resolved.
- **Required correction** Verify the correct GEO accession and use it consistently throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, DNAflexpy improvement section
- **Evidence pointer** Results section "DNAflexpy flexibility features improve TF-nucleosome affinity prediction beyond sequence baselines"
- **Issue** The text reports "99.6 of datasets" and "86.6 gained more than 5 percentage points" without specifying whether these are percentages or counts. This is ambiguous.
- **Required correction** Clarify whether these are percentages (e.g., "99.6% of datasets") or counts (e.g., "225 of 226 datasets").

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion does not explicitly address the limitations of the study, such as the correlative nature of the in vivo analyses, the potential confounding effects of chromatin state, or the limited number of TF families with structural validation.
- **Required correction** Add a "Limitations" paragraph to the Discussion, acknowledging these caveats and suggesting future experimental directions.

### **Technical failings that need to be addressed before the case is established**
- R1-M1 (missing figures) is a blocking issue; the manuscript cannot be evaluated without the figures.
- R1-M2 (statistical rigor) is a blocking issue; the significance of the reported improvements is not established.
- R1-M3 (circularity in in vivo analysis) is a blocking issue; the classification results may be overfitted.
- R1-M4 (interpretability of footprints) is a non-blocking but important issue; the quantitative link to MD simulations is not established.

### **Assessment against Nature-style criteria**
- **Originality**: The idea of using DNA flexibility descriptors to model TF-nucleosome binding is not entirely new, but the systematic evaluation across 226 datasets and the integration with MD simulations and in vivo data is a substantial and original contribution. The development of DNAflexpy as a community resource adds value.
- **Scientific importance**: The question of how TFs access nucleosomal DNA is of fundamental importance to gene regulation. If the claims are substantiated, this work could provide a new framework for understanding pioneer factor activity and interpreting noncoding variants. The potential impact is high.
- **Interdisciplinary readership**: The work bridges computational biology, biophysics, and chromatin biology. The writing is generally accessible, but the Methods section is dense and may be challenging for non-specialists. The authors should consider adding a plain-language summary of the key findings and their implications.
- **Technical soundness**: The methodological approach is reasonable, but the statistical framework and the potential for circularity in the in vivo analysis are significant concerns. The lack of figures prevents a full assessment of the technical quality.
- **Readability for nonspecialists**: The abstract and introduction are clear and well-written. The results section is narrative and would benefit from more explicit connections to the figures. The discussion is thoughtful but could be more concise.

### **Recommendation posture**
**Currently not established from the provided evidence.** The manuscript addresses a significant question and presents a plausible framework, but the absence of all figures and the unresolved statistical concerns prevent a full evaluation. The authors should be invited to resubmit a revised version that includes all figures, addresses the statistical rigor issues, and clarifies the in vivo analysis methodology. If these concerns are adequately resolved, the work could be suitable for publication in a high-impact journal.