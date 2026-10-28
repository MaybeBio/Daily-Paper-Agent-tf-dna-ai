## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided.
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality of the manuscript as submitted to bioRxiv.
- **Shared manuscript claim summary** The authors propose ASCARIS, a method for featurizing single amino acid variations (SAVs) using positional annotations from UniProt and structural information from PDB and AlphaFold. They claim the resulting 74-dimensional representations are informative for predicting variant effects, perform competitively against state-of-the-art predictors, and offer complementary value, particularly on challenging cases.
- **Visible evidence base** Abstract, full introduction, methods sections 2.1–2.6, results sections 3.1–3.3, conclusion, and references to figures and tables (Figure 1–5, Tables 1–4, Supplementary items S1–S5).
- **Missing materials affecting confidence** Figures and tables referenced in the text (Figures 1–5, Tables 1–4, Supplementary Figures S1–S5, Tables S1–S5) were not provided. Detailed hyperparameter settings and code implementation specifics are only partially described. Benchmark dataset construction details and exact statistical test outputs are not fully reproducible from the text alone.

## Reviewer
- **Overall assessment** The manuscript presents a novel featurization approach for SAVs that integrates sequence annotations with structural information, addressing an important gap in variant representation. The methodological framework is logical and the inclusion of AlphaFold structures is timely. However, the absence of the actual figures and tables limits the ability to fully evaluate the results. The claims of competitive performance and complementarity are partially supported by the text but require the missing data to be fully verified. The writing is generally clear but contains some redundancy and occasional imprecise language.
- **Who would be interested in the results, and why** Researchers in computational biology, bioinformatics, and genomics, particularly those working on variant effect prediction, protein structure-function analysis, and integrative omics modeling. The method's interpretability and potential for combination with other feature types may also appeal to those developing machine learning models for clinical decision support.
- **Major strengths** The proposed method addresses a real need for interpretable, function-centric SAV representations. The integration of multiple annotation types and structural data is comprehensive. The inclusion of AlphaFold structures extends applicability to proteins without experimental structures. The authors provide a practical open-source tool and demonstrate potential applications beyond prediction, such as integrative modeling.
- **Major Concerns** The most significant concern is the lack of access to the figures and tables that contain the core results. Without these, the statistical analyses, performance comparisons, and visualizations cannot be independently assessed. Additionally, the manuscript does not clearly describe how missing structural data were handled for proteins without PDB structures or AlphaFold predictions, which could introduce bias. The comparison with state-of-the-art methods is described but the exact protocols and potential confounders (e.g., dataset overlap, threshold choices) are not fully detailed.
- **Minor Comments** The text contains some typographical errors (e.g., "takinf" in section 2.3.1) and informal phrasing (e.g., "we decided to base our predictor"). The description of the feature set could be more concise. The rationale for choosing specific thresholds for physicochemical property changes is not fully justified. The discussion of the "no domain" group's high deleterious rate is speculative and could be better supported.
- **Technical failings that need to be addressed before the case is established** The manuscript must include the actual figures and tables to substantiate the reported results. The handling of missing structural data needs explicit description. The benchmark comparison methodology requires more detail to ensure fairness and reproducibility. The statistical tests should be reported with effect sizes and confidence intervals, not just p-values.
- **Assessment against Nature-style criteria**  
  - *Originality*: The approach is original in its combination of positional annotations with structural distance features, particularly the use of AlphaFold structures. This is a novel contribution to the field.  
  - *Scientific importance*: The work addresses a relevant problem in variant interpretation and offers a potentially useful resource. However, the demonstrated impact is currently limited to prediction performance, and broader biological insights are not deeply explored.  
  - *Interdisciplinary readership*: The method is relevant to computational biologists, geneticists, and structural biologists. The interpretability of features may appeal to a broader audience, but the manuscript is primarily technical.  
  - *Technical soundness*: The overall approach is sound, but the missing data and incomplete methodological details prevent full verification. The reliance on p-values without effect sizes is a weakness.  
  - *Readability for nonspecialists*: The manuscript is accessible to those with a background in bioinformatics, but the dense description of features and methods may be challenging for a general scientific audience. The abstract is clear, but the main text could benefit from more intuitive explanations.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the method has potential utility, but the current submission lacks the necessary evidence (figures, tables, methodological details) to fully establish the claims. The authors should be encouraged to revise and resubmit with complete data and clearer methodology.

### Major Concerns
- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence completeness  
- **Claim pointer** The manuscript claims competitive performance and complementarity against state-of-the-art methods, supported by results in Tables 3 and 4 and Figures S2 and S5.  
- **Evidence pointer** Tables 3a, 3b, 4a, 4b, 4c; Figures S2, S5; location not provided for actual data  
- **Concern** The core results, including all performance comparisons, statistical analyses, and visualizations, are presented in figures and tables that were not included in the provided manuscript. Without these, the validity of the claims cannot be assessed.  
- **Why it matters** The manuscript's central conclusions rest on these data. The absence of the actual results prevents verification of the reported metrics, the fairness of comparisons, and the significance of the findings.  
- **Resolution test** Provide all figures and tables with clear captions and ensure they are referenced accurately in the text. Include raw data or a public repository link for reproducibility.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity  
- **Claim pointer** The method incorporates structural information from PDB and AlphaFold, but the handling of proteins without available structures is not described.  
- **Evidence pointer** Section 2.2; location not provided  
- **Concern** The manuscript states that variations without structural data were removed, but it does not specify how many were removed, whether this introduced selection bias, or how the AlphaFold version handled proteins with partial coverage.  
- **Why it matters** If a significant fraction of SAVs were excluded due to missing structures, the resulting dataset may not be representative, and the performance claims could be biased.  
- **Resolution test** Clearly describe the criteria for including/excluding SAVs based on structural data availability. Report the number of excluded cases and discuss potential biases.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Statistical rigor  
- **Claim pointer** The manuscript reports p-values for associations between features and variant effects but does not provide effect sizes or confidence intervals.  
- **Evidence pointer** Section 3.1; location not provided  
- **Concern** The use of p-values alone, especially with large sample sizes, can be misleading. The manuscript does not report the magnitude of the observed effects, which is important for assessing practical significance.  
- **Why it matters** Without effect sizes, readers cannot judge the strength of the associations or compare them meaningfully across features.  
- **Resolution test** Report effect sizes (e.g., odds ratios, Cohen's d) and confidence intervals for all statistical tests.

### Minor Comments
- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Language and clarity  
- **Affected element** Section 2.3.1  
- **Evidence pointer** "takinf" typo; location not provided  
- **Issue** Typographical error in the text.  
- **Required correction** Correct "takinf" to "taking".

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Methodological detail  
- **Affected element** Section 2.5  
- **Evidence pointer** Hyperparameter grid search values; location not provided  
- **Issue** The specific hyperparameter values tested in the grid search are not listed in the text, only the selected values are given.  
- **Required correction** Provide the full list of hyperparameter values considered in the grid search.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Section 3.1  
- **Evidence pointer** Discussion of "no domain" group; location not provided  
- **Issue** The explanation for the high deleterious rate in the "no domain" group is speculative and not supported by data.  
- **Required correction** Either provide supporting evidence or temper the speculation with a more cautious interpretation.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Section 3.3  
- **Evidence pointer** Tool description; location not provided  
- **Issue** The manuscript states the tool is available but does not describe the software dependencies or installation instructions in the text.  
- **Required correction** Include a brief description of dependencies and installation steps, or refer to the repository for details.

## Risk / unsupported claims
- The claim that ASCARIS representations are "comprehensive" and "universally applicable" is not fully supported, as the method depends on the availability and completeness of annotations and structural data.
- The claim that the method "performs well on challenging cases" is based on a single benchmark subset and requires further validation across diverse datasets.
- The statement that "each feature carries information" is supported by statistical tests, but the practical significance of each feature is not quantified.
- The generalizability of the method to non-human proteins or proteins without any structural information is not demonstrated.