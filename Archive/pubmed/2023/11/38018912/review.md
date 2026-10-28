## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the manuscript
- **Shared manuscript claim summary** The authors present machine learning models to predict the oncogenic effect of missense mutations in p53, integrating experimental assays and computational biophysical features. They claim comparable performance to state-of-the-art p53-specific methods, interpretability via nine features, and clinical utility through a saturation mutagenesis landscape.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Discussion, Funding, Data Availability, Acknowledgements. Figures and tables referenced but not provided. Supplementary files referenced but not provided.
- **Missing materials affecting confidence** Figures 1–5, Tables 1–2, all Supplementary Figures and Tables, source code, and the clinical validation dataset are not available for inspection. This limits verification of reported performance metrics and statistical claims.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in cancer genomics: predicting functional consequences of p53 missense mutations. The authors build on prior work (TP53_PROF) and aim to improve interpretability and reduce feature complexity. The methodological approach is reasonable, and the integration of biophysical features with experimental data is sensible. However, the manuscript has several weaknesses. The claim of "comparable performance" to TP53_PROF is not fully substantiated without access to the comparison details. The clinical validation set is small (n=67) and the handling of class imbalance is not described. The qualitative analysis using Wilcoxon tests on multiple features without multiple testing correction is a concern. The saturation mutagenesis landscape is presented as a key output, but its validation is limited. The manuscript would benefit from clearer reporting of model selection, hyperparameter tuning, and uncertainty estimates. The writing is generally clear but some sections are dense. Overall, the work has merit but requires revisions to strengthen the evidence base and clarify claims.

- **Who would be interested in the results, and why** Researchers in cancer genomics, computational biology, and clinical genetics would be interested. The work offers a practical tool for interpreting p53 mutations, which is relevant for cancer diagnosis and treatment planning. The methodological approach of combining biophysical features with machine learning could be of interest to those developing variant effect predictors for other proteins.

- **Major strengths** The authors address a clinically important problem with a practical tool. The integration of multiple biophysical measurements is thoughtful. The comparison with several existing methods is useful. The provision of a precomputed landscape for all possible missense mutations is a valuable resource. The emphasis on interpretability is commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim "comparable predictive performance with the state-of-the-art p53 specific method" (Abstract) and "outperformed other generalized, widely used predictors" (Abstract).
- **Evidence pointer** Results section, Tables 1 and 2 (not provided)
- **Concern** The performance comparison with TP53_PROF and other methods is presented in tables that are not available for review. The methodology for this comparison is not fully described. Specifically, it is unclear whether the same training and test splits were used, whether hyperparameters were optimized on the test set, and how cutoffs for continuous predictors were determined. The claim of "comparable" performance is vague without confidence intervals or statistical tests of significance.
- **Why it matters** The central claim of the manuscript is that the proposed models are competitive with existing tools. Without transparent and rigorous comparison, this claim cannot be evaluated. If the comparison is not fair, the conclusions may be overstated.
- **Resolution test** Provide the full comparison tables with confidence intervals. Describe the exact protocol for training, validation, and testing for all methods. Perform statistical tests (e.g., McNemar's test) to assess whether performance differences are significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "a two-tailed Wilcoxon signed-rank test was implemented to statistically compare the difference between functional and non-functional mutations of numerous computational biophysical measurements" (Materials and Methods, Qualitative analysis).
- **Evidence pointer** Materials and Methods, Qualitative analysis; Results, Biophysical properties
- **Concern** The authors perform multiple Wilcoxon tests across numerous features without any correction for multiple comparisons. This increases the risk of false positives. The number of tests performed is not stated. The results are reported as significant with P-values as low as 1.02 × 10⁻²¹, but it is unclear how many features were tested and whether any would survive a correction such as Benjamini-Hochberg.
- **Why it matters** The identification of "oncogenic drivers" is a key contribution. If the statistical evidence is inflated by multiple testing, the proposed drivers may not be robust. This could mislead downstream research.
- **Resolution test** Report the total number of tests performed. Apply a multiple testing correction (e.g., FDR) and report adjusted P-values. Re-evaluate which features remain significant.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** External validity
- **Claim pointer** "we present two interpretable machine learning models leveraging both experimental assays and in silico biophysical measurements to accurately predict the functional consequences on p53 and validate their robustness on clinical data" (Abstract).
- **Evidence pointer** Materials and Methods, Independent clinical assessment; Results, Tables 1 and 2
- **Concern** The clinical validation set contains only 67 mutations, with 52 benign and 15 pathogenic. This is a small and imbalanced set. The authors do not report how the models handle this imbalance, nor do they provide precision-recall curves or other metrics appropriate for imbalanced data. The generalizability of the models to diverse clinical populations is unclear.
- **Why it matters** The clinical utility claim rests on this validation. A small, imbalanced set may give optimistic or unstable performance estimates. Without appropriate metrics and analysis, the robustness of the models in clinical settings is not established.
- **Resolution test** Report precision-recall curves and the area under the precision-recall curve. Describe any class weighting or resampling strategies. Consider bootstrapping to provide confidence intervals for performance metrics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "All the predictions, along with their confidence estimation, are available in the Supplementary Files" (Results, Mutational landscape).
- **Evidence pointer** Data Availability section
- **Concern** The source code is available, but the manuscript does not describe the computational environment, dependencies, or instructions for reproducing the models. The saturation mutagenesis landscape is provided as a supplementary file, but the methodology for generating it is not fully detailed. Specifically, the process of applying the model to all possible missense mutations and the handling of features for mutations outside the structured domains is not clear.
- **Why it matters** Reproducibility is a core principle of scientific research. Without clear documentation, other researchers cannot build on this work or verify the results.
- **Resolution test** Provide a detailed description of the computational workflow, including software versions, hyperparameters, and any preprocessing steps. Include a README with the code repository. Clarify how features are computed for mutations in disordered regions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity
- **Claim pointer** "The final model based on nine features obtained comparable predictive performance" (Abstract).
- **Evidence pointer** Materials and Methods, Model development; Results, Feature interpretations
- **Concern** The process of feature selection is described as "greedy" but the specific algorithm, stopping criteria, and the initial feature set are not fully detailed. The manuscript states that 289 features were used for the ExpAssay model, but the composition of these features is not fully described. The nine features selected for the final model are mentioned in the Results, but their definitions are not all clear. For example, "polar atom distances" and "changes in p53 stability" are mentioned, but the exact computational tools and parameters are not specified.
- **Why it matters** The interpretability claim depends on the clarity of the features. If the features are not well-defined, the interpretation is meaningless. Other researchers cannot apply the model without knowing exactly what features to compute.
- **Resolution test** Provide a complete list of all 289 features with definitions. Describe the greedy feature selection algorithm in detail, including the metric used for selection and the stopping criterion. For the nine final features, provide precise definitions and the tools used to compute them.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The phrase "informing a bias of deleterious mutations with destabilizing effects" is awkward and unclear. It is not immediately obvious what "informing a bias" means.
- **Required correction** Rephrase to something like "revealing that deleterious mutations tend to have destabilizing effects" for clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and Methods, Structural information
- **Evidence pointer** Materials and Methods, Structural information of p53 homotetramer
- **Issue** The manuscript states that the AlphaFold2 model was used because no experimental full-length homotetramer was available. However, the RMSD values for the DBD and OD compared to crystal structures are reported. It would be helpful to state whether the full tetramer model was validated in any other way, such as by checking interface contacts.
- **Required correction** Add a sentence describing any additional validation of the tetramer model, or state that no further validation was performed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reporting
- **Affected element** Results, Performance comparison
- **Evidence pointer** Results, Performance comparison
- **Issue** The manuscript mentions that "both our ExpAssay and noExpAssay models outperform those tools" but does not provide the actual performance numbers in the text. The reader is referred to tables that are not available.
- **Required correction** Include the key performance metrics (e.g., MCC, AUC) in the text for the main comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the "polar environment at the mutation site" as a risk factor is brief. It would be helpful to explain why this might be biologically plausible.
- **Required correction** Add a sentence or two on the potential biological mechanism linking polar environment to p53 dysfunction.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** There are some grammatical errors and awkward phrasings. For example, "Dysfunctions caused by genetic variants on tumour suppressor p53 is one of the leading drivers" should be "are one of the leading drivers."
- **Required correction** A thorough language edit is recommended.

- **Technical failings that need to be addressed before the case is established** The lack of access to figures, tables, and supplementary materials prevents full verification of the reported results. The multiple testing issue in the qualitative analysis must be addressed. The performance comparison protocol needs to be clarified to ensure fairness. The small and imbalanced clinical validation set requires more appropriate evaluation metrics.

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The problem is important, and the integration of biophysical features is not entirely novel but is applied in a new context. The saturation mutagenesis landscape is a useful contribution.
  - Scientific importance: High. p53 mutations are central to cancer, and improved prediction tools have clinical relevance.
  - Interdisciplinary readership: Moderate. The work will appeal to computational biologists and cancer geneticists, but the methods are not broadly accessible to a general scientific audience.
  - Technical soundness: The methodology is generally sound, but the statistical analysis has flaws (multiple testing) and the comparison protocol is not fully transparent. The small clinical set limits the strength of the validation.
  - Readability for nonspecialists: The manuscript is written for a specialized audience. The methods section is dense, and the abstract could be clearer. The clinical implications are stated but not elaborated.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is valuable, and the models appear to perform well, but the statistical rigor and transparency of the comparison need improvement. The authors should address the multiple testing issue, provide full details of the feature selection and model training, and present the clinical validation with appropriate metrics. Once these are addressed, the manuscript could be suitable for publication.