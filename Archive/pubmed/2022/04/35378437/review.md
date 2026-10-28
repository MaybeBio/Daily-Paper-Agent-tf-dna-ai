## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose DeepDNAbP, a hybrid deep learning predictor for DNA-binding proteins (DBPs) that combines three feature extraction methods (PSSM, PseAAC, TPC), applies SHAP-based feature selection, and uses a CNN classifier. They report superior prediction performance in K-fold cross-validation compared to existing predictors and provide a web application and curated datasets.
- **Visible evidence base** Abstract text only; no quantitative performance metrics, dataset descriptions, or methodological details are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, dataset composition and size, cross-validation protocol details, baseline predictor descriptions, statistical significance tests, web application functionality, and code availability

## Reviewer
- **Overall assessment** The abstract presents a plausible pipeline for DBP prediction, but the evidence provided is insufficient to evaluate the technical soundness or the validity of the claimed superiority. Key quantitative results, dataset details, and methodological specifics are absent, making the core claims currently unverifiable from the supplied material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those developing or benchmarking sequence-based predictors for DNA-binding proteins. The proposed hybrid feature and SHAP-based selection approach may also interest researchers applying interpretable machine learning to biological sequence classification.
- **Major strengths** The combination of three complementary feature types (evolutionary, compositional, and local sequence patterns) is a reasonable strategy for capturing diverse aspects of DBP sequence characteristics. The use of SHAP for feature selection is a modern and interpretable approach that could improve model transparency. The stated intention to provide a web application and curated datasets is commendable for community utility.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "The final DeepDNAbP predictor achieves superior prediction performance in K-fold cross-validation tests and outperforms other existing predictors of DNA-protein binding methods."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** No quantitative performance metrics (e.g., accuracy, sensitivity, specificity, MCC, AUC) are reported in the abstract. The claim of "superior" and "outperforms" is made without any numerical comparison to existing predictors or statistical significance testing.
  - **Why it matters** Without concrete metrics and statistical validation, the central claim of improved performance cannot be assessed. Superiority claims in computational biology require rigorous benchmarking against established methods with appropriate significance tests.
  - **Resolution test** Provide performance metrics for DeepDNAbP and all compared predictors on the same benchmark datasets, including confidence intervals or p-values for performance differences.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** "we perform three feature extraction methods... SHAP are employed to remove the redundant and irrelevant features... the best features are provided to the CNN classifier"
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract lacks essential methodological details: dataset composition and size, how training and test sets were partitioned, the specific CNN architecture, hyperparameter settings, the threshold for SHAP-based feature selection, and how "best features" were determined.
  - **Why it matters** Reproducibility is a fundamental requirement for computational predictors. Without these details, other researchers cannot replicate the method or verify the results, undermining the scientific contribution.
  - **Resolution test** Include full methodological details in the manuscript, including dataset statistics, architecture specifications, hyperparameters, and feature selection criteria.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data availability and validation
  - **Claim pointer** "The web application and curated datasets in this study are freely available at: http://deepdbp.sblog360.blog/"
  - **Evidence pointer** Abstract, URL provided
  - **Concern** The abstract does not describe the datasets used for training and evaluation, including their sources, sizes, sequence redundancy levels, or whether independent test sets were used. The web application URL is provided but its functionality and data accessibility cannot be verified from the abstract.
  - **Why it matters** Dataset quality and independence are critical for assessing generalizability. Without dataset descriptions, the risk of overfitting or biased evaluation cannot be evaluated. A non-functional or inaccessible web resource would also limit practical utility.
  - **Resolution test** Describe dataset sources, sizes, and redundancy filtering in the manuscript. Verify that the web application is functional and provides access to all datasets and predictions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract background
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The phrase "sometimes biased toward prediction" is unclear and grammatically awkward. It likely intends to convey that experimental methods can be biased, but the wording is confusing.
  - **Required correction** Rephrase to clarify the intended meaning, for example "experimental identification is time-consuming and can be biased" or similar.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Method description
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract states "the best features are provided to the CNN classifier" but does not explain how "best" was determined beyond SHAP-based removal. The selection criterion is ambiguous.
  - **Required correction** Specify the SHAP-based selection threshold or procedure used to determine which features were retained.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interdisciplinary readership
  - **Affected element** Abstract conclusion
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The claim "DeepDNAbP is poised to be a powerful computational resource" is promotional and not supported by evidence in the abstract.
  - **Required correction** Replace with a factual statement about the tool's availability and potential applications, or remove the claim.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no quantitative performance evidence), R1-M2 (insufficient methodological detail for reproducibility), R1-M3 (inadequate dataset description and unverified web resource)
- **Assessment against Nature-style criteria**  
  **Originality** The combination of PSSM, PseAAC, and TPC with SHAP-based selection and CNN is not clearly novel, as similar hybrid approaches exist in the DBP prediction literature. The abstract does not articulate a distinct conceptual advance.  
  **Scientific importance** DBP prediction is a relevant problem in functional genomics, but the abstract does not demonstrate a significant improvement over existing methods, limiting the perceived importance.  
  **Interdisciplinary readership** The topic bridges bioinformatics and machine learning, but the abstract is too brief to engage readers outside the immediate DBP prediction community.  
  **Technical soundness** Cannot be assessed from the abstract alone. The absence of performance metrics and methodological details precludes evaluation of the approach's validity.  
  **Readability for nonspecialists** The abstract is generally accessible but contains unclear phrasing and lacks context for readers unfamiliar with DBP prediction.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient quantitative or methodological support for the central claims. A supportive assessment would require access to the full manuscript with detailed performance metrics, dataset descriptions, and reproducible methodology.

## Risk / unsupported claims
- The claim of "superior prediction performance" and "outperforms other existing predictors" is unsupported by any quantitative data in the abstract.
- The assertion that DeepDNAbP is "a powerful computational resource" is promotional and not evidenced.
- The availability and functionality of the web application and curated datasets cannot be verified from the abstract.
- The methodological pipeline (feature extraction, SHAP selection, CNN classification) is described only at a high level, and its effectiveness cannot be evaluated without full details.