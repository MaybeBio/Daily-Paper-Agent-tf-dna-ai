## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and methods as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors use two sequence-to-function models, AlphaGenome and AlphaMissense, to quantify the predicted disruption of somatic mutations across 8,800 TCGA patients and 33 cancer types. They report that recurrent hotspot mutations show larger predicted protein-level effects while non-hotspot mutations show larger regulatory effects. They aggregate variant-level predictions into patient-gene disruption profiles covering transcriptional activity, chromatin accessibility, transcription factor binding, and splicing. These profiles are reported to be gene- and modality-specific, to reflect tissue of origin, cancer type, and microsatellite-instability status, and to retain information beyond tumor mutational burden. Among patients lacking recurrent hotspot mutations in a given cancer gene, higher predicted disruption is associated with overall survival, with the strongest signal for chromatin accessibility. In an independent treatment-annotated cohort, gene-level disruption is associated with survival within treatment-defined subgroups.
- **Visible evidence base** Abstract text only; data availability statement lists TCGA, TCGA-CDR, IntOGen, POG570, and Cancer Hotspots v2 as sources
- **Missing materials affecting confidence** Full manuscript, all figures, all tables, supplementary materials, methodological details, cohort composition, statistical models, and validation procedures

## Reviewer

- **Overall assessment** The abstract presents a conceptually interesting framework for moving beyond discrete driver mutations toward continuous, multidimensional gene-level disruption profiles. The use of two complementary sequence-to-function models is sensible, and the proposed distinction between protein-level effects of hotspots and regulatory effects of non-hotspots is potentially valuable. However, the abstract alone provides insufficient methodological detail to evaluate the validity of the aggregation procedure, the statistical models used for survival associations, the handling of confounding variables, or the robustness of the findings. The central claims are plausible but currently not established from the provided evidence.
- **Who would be interested in the results, and why** Cancer genomics researchers interested in functional interpretation of somatic mutations, computational biologists working on sequence-to-function models, clinical oncologists seeking prognostic biomarkers, and researchers studying tumor heterogeneity and the role of non-coding mutations. The proposed framework could be of interest to those working on integrating genomic and clinical data for precision oncology.
- **Major strengths** The conceptual shift from discrete driver mutations to continuous disruption profiles is timely and potentially impactful. The use of two complementary models, one focused on protein effects and one on regulatory effects, is a reasonable approach. The analysis across 8,800 patients and 33 cancer types provides substantial scale. The inclusion of an independent treatment-annotated cohort for validation is a strength. The claim that disruption profiles retain information beyond tumor mutational burden suggests potential clinical utility.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that aggregating variant-level predictions into patient-gene disruption profiles produces biologically meaningful and clinically informative measures.
  - **Evidence pointer** Abstract; methods not provided
  - **Concern** The abstract does not describe how variant-level predictions are aggregated into patient-gene disruption profiles. It is unclear whether the aggregation is a sum, mean, maximum, or some weighted combination across variants, and whether the aggregation accounts for variant allele frequency, clonality, or the number of variants per gene. Without this information, the biological interpretation of a "disruption profile" is ambiguous.
  - **Why it matters** The aggregation method directly determines the validity of all downstream analyses. If the aggregation is not carefully designed and justified, the resulting profiles may not reflect meaningful gene-level disruption, and all subsequent associations with survival or cancer type could be artifacts of the aggregation procedure.
  - **Resolution test** Provide a detailed description of the aggregation method, including the mathematical formulation, justification for the chosen approach, and sensitivity analyses demonstrating that results are robust to alternative aggregation strategies.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor
  - **Claim pointer** The authors claim that higher predicted disruption is associated with overall survival among patients lacking recurrent hotspot mutations, with the strongest signal for chromatin accessibility.
  - **Evidence pointer** Abstract; statistical details not provided
  - **Concern** The abstract does not describe the statistical models used for survival analysis. It is unclear whether Cox proportional hazards models were used, whether continuous or dichotomized disruption scores were employed, what covariates were included, and how multiple testing across genes and modalities was handled. The claim of association with survival requires appropriate adjustment for known prognostic factors and multiple comparison correction.
  - **Why it matters** Survival associations in cancer genomics are frequently confounded by tumor stage, age, treatment, and other clinical variables. Without evidence of appropriate adjustment and multiple testing control, the reported associations may not be robust or clinically meaningful.
  - **Resolution test** Describe the statistical models, covariates, multiple testing correction methods, and provide effect sizes with confidence intervals. Show that associations persist after adjustment for established prognostic factors and after correction for multiple comparisons.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validation and generalizability
  - **Claim pointer** The authors claim that gene-level disruption is associated with survival within treatment-defined subgroups in an independent treatment-annotated cohort.
  - **Evidence pointer** Abstract; cohort details not provided
  - **Concern** The abstract does not specify the size of the independent cohort, the cancer types included, the treatments administered, or the number of patients per treatment subgroup. It is unclear whether the subgroup analyses were pre-specified or exploratory, and whether the sample sizes were adequate to detect meaningful associations.
  - **Why it matters** Treatment-defined subgroup analyses are prone to false positives, especially when many subgroups are examined. Without details on cohort composition, subgroup definitions, and statistical power, the validity of these findings cannot be assessed.
  - **Resolution test** Provide detailed cohort characteristics, subgroup definitions, sample sizes, and clearly state whether subgroup analyses were pre-specified or exploratory. Report results for all subgroups examined, not only those with significant findings.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Definition of "disruption"
  - **Evidence pointer** Abstract
  - **Issue** The term "disruption" is used throughout but is not explicitly defined. It is unclear whether this refers to predicted functional impact, loss-of-function probability, or some other metric derived from the models.
  - **Required correction** Provide an explicit definition of "disruption" as used in this study, including how it relates to the outputs of AlphaGenome and AlphaMissense.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Model versions and parameters
  - **Evidence pointer** Abstract; methods not provided
  - **Issue** The abstract does not specify which versions of AlphaGenome and AlphaMissense were used, nor the exact parameters or thresholds applied.
  - **Required correction** Specify model versions, relevant parameters, and any thresholds used for classifying variants or constructing profiles.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretability
  - **Affected element** Clinical relevance
  - **Evidence pointer** Abstract
  - **Issue** The abstract states that disruption profiles are associated with survival but does not indicate the magnitude of the effect or whether the effect size is clinically meaningful.
  - **Required correction** Report effect sizes, such as hazard ratios, and discuss their clinical relevance in the context of existing prognostic markers.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The aggregation method, statistical approach, and validation details are all essential to establishing the validity of the central claims and are currently not described.
- **Assessment against Nature-style criteria** Originality is high, as the conceptual framework of continuous gene-level disruption profiles is a departure from the discrete driver paradigm. Scientific importance is potentially high, given the potential relevance to cancer biology and clinical prognostication. Interdisciplinary readership is plausible, spanning cancer genomics, computational biology, and clinical oncology. Technical soundness cannot be assessed from the abstract alone, as the key methodological details are missing. Readability for nonspecialists is adequate, though the abstract assumes familiarity with sequence-to-function models and genomic terminology.

## Risk / unsupported claims

- The claim that recurrent hotspots show larger protein-level effects while non-hotspots show larger regulatory effects is not supported by quantitative data in the abstract.
- The claim that disruption profiles reflect tissue of origin, cancer type, and microsatellite-instability status is not supported by any statistical measures in the abstract.
- The claim that disruption profiles retain information beyond tumor mutational burden is not supported by any comparative analysis in the abstract.
- The claim that higher predicted disruption is associated with overall survival is not supported by effect sizes, confidence intervals, or p-values in the abstract.
- The claim that gene-level disruption is associated with survival within treatment-defined subgroups is not supported by any cohort details or statistical results in the abstract.
- The overall conclusion that the findings support a continuous, multidimensional view of cancer gene perturbation is an interpretation that cannot be evaluated without the underlying data and analyses.