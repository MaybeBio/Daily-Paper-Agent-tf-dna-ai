## Review setup
- **Input scope** Full manuscript text, including abstract, background, results, discussion, conclusions, methods, and figure legends. Supplementary materials referenced but not provided.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and interpretation of results as presented in the manuscript. No assessment of editorial fit or publication venue.
- **Shared manuscript claim summary** The authors compare transcription factor binding site (TFBS) data from ENCODE and Cistrome across three human cell lines, showing that high signalValue peaks are more likely to overlap between databases, and that filtering on high signalValue improves the performance of a positional machine learning algorithm (TICA) for predicting TF-TF interactions.
- **Visible evidence base** Main text figures (Figures 1-7), tables (Table 1), and in-text statistics. Supplementary figures S1-S9 are referenced but not available for review.
- **Missing materials affecting confidence** Supplementary figures S1-S9, supplementary methods, and the full TICA output data. These are referenced for key claims (e.g., signalValue distributions, cell line comparisons, prediction heatmaps) and their absence limits full verification.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and practical question: whether two widely used TFBS repositories can be used interchangeably, and whether the signalValue feature can identify high-confidence overlapping regions. The authors provide a systematic comparison using Jaccard Index, Alroy-corrected Forbes coefficient, and conditional probability analyses, and demonstrate a downstream application with TICA. The work is clearly presented and the methodological choices are generally reasonable. However, several technical concerns regarding data processing, statistical interpretation, and validation of the machine learning results need to be addressed before the conclusions can be fully supported.
- **Who would be interested in the results, and why** Researchers who use public ChIP-Seq datasets for TFBS analysis, particularly those building or applying computational pipelines for regulatory genomics. The practical guidelines for filtering and merging ENCODE and Cistrome data will be of direct use to this community. The findings also have implications for anyone assessing data quality and consistency across genomic repositories.
- **Major strengths** The study addresses a practical and under-explored issue in genomic data reuse. The use of multiple overlap metrics (Jaccard, Alroy-Forbes) and conditional probability analysis is thoughtful. The downstream application with TICA provides a concrete demonstration of the impact of data filtering. The authors are transparent about limitations, including the unbalanced test set and the difficulty of defining negative cases.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical validity
  - **Claim pointer** "The vast majority of the overlaps fall into the M x M, M x H, H x M, and H x H bins, which are strongly over-represented compared to theoretical distribution (ratio greater than 1, red color)."
  - **Evidence pointer** Figure 3, Supplementary Figures S3 and S6
  - **Concern** The analysis of signal bin overlap ratios is based on a comparison to an expected distribution under independence, but the construction of the null expectation is not fully described. The bins are defined by within-database quantiles (25%, 50%, 25%), but it is unclear how the expected joint probabilities are computed when the marginal distributions differ between databases. If the marginal probabilities are not identical, the expected joint probability under independence is not simply the product of the marginal probabilities. The authors state P(E = H) = 0.25 and P(C = H) = 0.25, but this assumes identical marginal distributions, which may not hold after filtering and merging. The null model needs to be explicitly defined and justified.
  - **Why it matters** The central claim that high-signal peaks are more likely to overlap depends on the correctness of the null model. If the null expectation is mis-specified, the observed over-representation could be an artifact of the binning procedure rather than a biological or technical signal.
  - **Resolution test** Provide a clear mathematical definition of the null expectation, including how marginal probabilities are estimated for each database. Show that the null model is valid by simulation or by demonstrating that the marginal distributions are indeed identical after the described preprocessing. If marginal distributions differ, use a null model that accounts for this.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** "We ran the TICA pipeline on all the different JOINs between ENCODE and Cistrome described in Methods. We used the default settings for the HepG2 cell line, as described in [10]."
  - **Evidence pointer** Methods section, Figure 5, Figure 6
  - **Concern** The TICA evaluation is described as comparing recall, precision, and accuracy, but the exact procedure for computing these metrics is not fully specified. The authors state that the test set is unbalanced and that negative cases are not self-evident, but they do not describe how they handled this in the computation of precision and recall. Specifically, it is unclear how many positive and negative examples were used, how the threshold for calling a positive prediction was set, and whether the same threshold was used across all JOIN conditions. Without this information, the reported improvements in recall and specificity cannot be independently verified.
  - **Why it matters** The claim that filtering on high signalValue improves TICA performance is a key practical recommendation. If the evaluation procedure is not fully specified, readers cannot assess whether the improvement is robust or an artifact of the evaluation setup.
  - **Resolution test** Provide a detailed description of the evaluation protocol, including the number of positive and negative examples, the threshold selection procedure, and how precision and recall were computed. Ideally, provide the full confusion matrices for each condition. If possible, report confidence intervals or significance tests for the differences in performance.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Data processing
  - **Claim pointer** "We removed from our input all TF binding sites whose signalValue lies above the 90th percentile of the signalValue distribution."
  - **Evidence pointer** Methods section, Signal filtering and sample merging
  - **Concern** The rationale for removing peaks above the 90th percentile is stated as removing "significant outliers in the right tail" that are "unlikely to be actual biological phenomena as opposed to artifacts." This is a strong assumption that is not empirically justified. The authors state that removing peaks above the 85th or 95th percentile does not significantly alter results, but no data are shown. It is unclear whether this filter is applied per TF, per cell line, or globally. The choice of threshold could affect the downstream analyses, particularly the signal bin assignments.
  - **Why it matters** The filtering step directly affects which peaks are included in the analysis and how signal bins are defined. If the filter is applied inconsistently or without clear justification, the results may not be reproducible by other researchers.
  - **Resolution test** Clarify how the 90th percentile is computed (per TF, per cell line, or globally) and provide the sensitivity analysis mentioned in the text. Justify the biological rationale for removing high-signal peaks, or soften the claim that these are artifacts.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** "If both ENCODE and Cistrome are used as input data for position-based algorithms, we recommend that ENCODE data is used after filtering for binding sites overlapping with Cistrome-high sites."
  - **Evidence pointer** Discussion section, Figure 5
  - **Concern** The recommendation is based on results from three cell lines and a single downstream algorithm (TICA). The authors acknowledge this limitation in the conclusions, but the recommendation is stated quite strongly in the discussion. It is unclear whether the improvement in TICA performance would generalize to other algorithms that use different features or modeling approaches. The authors note that TICA does not use signalValue, which is a strength of the study design, but it also means the results may not apply to algorithms that do use signalValue.
  - **Why it matters** The practical value of the manuscript lies in the generalizability of the recommendations. If the findings are specific to TICA or to the three cell lines tested, the recommendations may be over-stated.
  - **Resolution test** Soften the recommendation or provide additional evidence that the filtering approach is beneficial for other types of algorithms. If such evidence is not available, clearly frame the recommendation as specific to positional algorithms similar to TICA.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 2
  - **Evidence pointer** Figure 2
  - **Issue** The color scale in Figure 2a and 2b is described as "darker color represent higher values," but the actual color mapping is not shown. It is difficult to interpret the scatterplots without a color legend.
  - **Required correction** Add a color bar or legend to Figure 2a and 2b to make the color mapping explicit.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, Data sources
  - **Evidence pointer** Methods section
  - **Issue** The authors state that data was downloaded in March 2020, but the manuscript was published in 2024. It is unclear whether the analysis reflects the state of the databases at the time of download or whether updates were incorporated.
  - **Required correction** Clarify whether the analysis is based solely on the March 2020 data snapshot or whether any updates were included.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion, paragraph on blacklisted regions
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of blacklisted regions and HOT regions is brief and somewhat speculative. The authors state that high-signal overlapping regions are rarely in HOT regions, but the analysis is only described in the supplementary materials.
  - **Required correction** Provide a brief summary of the HOT region analysis in the main text or move the discussion to the results section where the data are presented.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 5
  - **Evidence pointer** Figure 5
  - **Issue** The notation "EC-h" and "CI-h" is used in the figure legend, but the main text uses "EC-H" and "CI-H." This inconsistency could confuse readers.
  - **Required correction** Standardize the notation throughout the manuscript and figure legends.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods, Software
  - **Evidence pointer** Methods section
  - **Issue** The software section mentions that TICA is available at www.gqml.eu/tica, but no version number or access date is provided.
  - **Required correction** Provide a version number and access date for the TICA software.

## Technical failings that need to be addressed before the case is established
- R1-M1: The null model for the signal bin overlap analysis is not fully specified, and the assumption of identical marginal distributions between databases is not justified. This is a blocking issue because the central claim of the manuscript depends on the validity of this null model.
- R1-M2: The TICA evaluation protocol is not fully described, including the handling of the unbalanced test set and the threshold for calling positive predictions. This is a blocking issue because the practical recommendations are based on these results.

## Assessment against Nature-style criteria
- **Originality** Moderate. The question of cross-repository consistency is not new, but the specific focus on signalValue as a filtering criterion and the systematic comparison across multiple metrics is a useful contribution.
- **Scientific importance** Moderate. The findings are practically relevant for researchers using public TFBS data, but the scope is limited to three cell lines and one downstream algorithm. The importance would be higher if the recommendations were shown to generalize more broadly.
- **Interdisciplinary readership** Limited. The manuscript is primarily of interest to computational biologists and bioinformaticians working with ChIP-Seq data. The methods and terminology are specialized.
- **Technical soundness** The overall approach is reasonable, but the concerns above regarding the null model and the TICA evaluation protocol need to be addressed. The data processing steps are described in sufficient detail for the most part, but some choices (e.g., the 90th percentile filter) lack clear justification.
- **Readability for nonspecialists** The manuscript is clearly written and the figures are generally informative. However, some sections (e.g., the description of the genometric JOIN operators) assume familiarity with specialized concepts. The abstract and introduction are accessible to a broader audience.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses a practical and relevant question, and the overall approach is sound. However, the blocking concerns regarding the null model and the TICA evaluation protocol must be addressed before the conclusions can be fully supported. The authors should provide a clear mathematical definition of the null expectation, justify the assumption of identical marginal distributions, and provide a detailed description of the TICA evaluation procedure.

## Risk / unsupported claims
- The claim that high signalValue peaks are more likely to overlap between ENCODE and Cistrome is not fully supported until the null model is properly specified and validated.
- The claim that filtering on high signalValue improves TICA performance is not fully supported until the evaluation protocol is described in sufficient detail.
- The claim that high-signal overlapping regions are rarely in HOT regions is not verifiable from the main text alone, as the analysis is only described in the supplementary materials.
- The claim that removing peaks above the 90th percentile removes artifacts is not empirically justified in the main text.
- The generalizability of the recommendations to other cell lines and algorithms is not established from the provided evidence.