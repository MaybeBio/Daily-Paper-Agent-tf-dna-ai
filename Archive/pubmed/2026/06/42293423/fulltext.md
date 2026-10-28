# Standardized contrast-enhanced CT-based radiomics for non-invasive prediction of TTF-1 status in lung adenocarcinoma: A cross-validated single-center study


## Objective
  Thyroid transcription factor-1 (TTF-1) is a clinically relevant immunohistochemical marker in lung adenocarcinoma with diagnostic, prognostic, and therapeutic implications. As tissue sampling is invasive and often limited by small biopsy specimens, non-invasive imaging biomarkers are of increasing interest. This study aimed to develop and internally validate a standardized contrast-enhanced CT-based radiomics workflow for prediction of TTF-1 expression, with emphasis on reproducibility and methodological robustness.


## Methods
  This retrospective single-center study included 164 treatment-naive patients with histologically confirmed lung adenocarcinoma and available TTF-1 immunohistochemistry. TTF-1 expression was assessed using routine immunohistochemical staining on biopsy or resection specimens, with binary classification based on nuclear staining. Primary tumors were semi-automatically segmented on contrast-enhanced CT using IBSI-compliant preprocessing. A total of 107 radiomic features were extracted. Interobserver reproducibility was evaluated in a subset of 55 tumors using intraclass correlation coefficients. Logistic regression, random forest, and XGBoost models were trained using five-fold stratified cross-validation. Performance was evaluated using AUC.


## Results
  Among 164 patients, 115 tumors (70.1%) were TTF-1 positive. XGBoost achieved the highest performance (mean AUC = 0.83 ± 0.04), significantly outperforming other models (p < 0.01). Radiomic features showed good interobserver reproducibility, particularly for shape and first-order features. SHAP analysis identified sphericity, entropy, and mean CT attenuation as key predictors.


## Conclusion
  A standardized CT-based radiomics approach shows promising performance for non-invasive prediction of TTF-1 status in lung adenocarcinoma. Given the retrospective single-center design and lack of external validation, further multicenter studies are required.


## Introduction
  Lung adenocarcinoma represents a biologically heterogeneous disease entity in which histopathological and molecular characterization plays a central role in diagnostic classification, prognostic stratification and therapeutic decision-making [1]. Among immunohistochemical markers, thyroid transcription factor−1 (TTF−1) is of particular clinical relevance, as it supports the differentiation of lung adenocarcinoma from squamous cell carcinoma and is associated with distinct molecular profiles, including epidermal growth factor receptor (EGFR) alterations [2], [3]. Furthermore, TTF−1 expression has become an important prognostic factor in lung adenocarcinoma, as TTF−1-negativity is predictive for poorer outcome in advanced NSCLC [4].

  Despite its established value, assessment of TTF−1 expression relies on tissue sampling, which is inherently invasive and may be constrained by limited specimen size, tumor heterogeneity, or procedural risk [5]. In routine clinical practice, insufficient tissue availability and delayed pathological results remain relevant challenges, particularly in patients with advanced disease or reduced performance status [6]. These limitations have stimulated growing interest in non-invasive imaging-based biomarkers that can provide complementary biological information [7].

  However, reliance on imaging-based prediction models also carries the risk of misclassification and cannot replace histopathological confirmation.

  Radiomics enables the high-throughput extraction of quantitative features from standard medical images, capturing tumor shape, attenuation and textural heterogeneity beyond visual assessment [8]. Previous studies have demonstrated associations between CT-derived radiomic features and histopathological, molecular and prognostic characteristics in lung cancer [9], [10], [11]. However, reproducibility across observers and the robustness of radiomic signatures remain critical barriers for clinical translation [12], [13].

  Therefore, the purpose of this study was to develop and validate a standardized, IBSI-compliant CT-radiomics workflow for non-invasive prediction of TTF−1 expression in lung adenocarcinoma, with particular emphasis on interobserver reproducibility and comparative evaluation of established machine-learning classifiers [14].


## Materials and methods

### Study design and patient cohort
  This retrospective, single-center cohort study included consecutive patients with histopathologically confirmed lung adenocarcinoma and available thyroid transcription factor−1 (TTF−1) immunohistochemistry. Patients were identified through institutional pathology and radiology databases and included patients from 2012 to 2022. The study was conducted in accordance with the Declaration of Helsinki and approved by the local ethics committee of the Friedrich-Alexander University Erlangen–Nürnberg (Medical Campus Upper Franconia–Bayreuth; approval No. EK−24–158-Br). Due to the retrospective nature of the study and irreversible anonymization of imaging and clinical data prior to analysis, the requirement for written informed consent was waived [14].

  A total of 164 patients were included in the final analysis. The median patient age was 67 years (range, 43–86 years), and 58% were male. All tumors were lung adenocarcinomas. Tumor location was classified as peripheral or central based on CT imaging, with peripheral tumors defined as lesions arising in the outer third of the lung parenchyma and central tumors involving the hilar or peribronchial regions [15]. Peripheral localization was observed in 66% of cases, while 34% were centrally located.

  Only baseline contrast-enhanced CT examinations acquired prior to any systemic or local oncologic therapy were considered eligible for radiomic analysis.

  A total of 210 patients with histologically confirmed lung adenocarcinoma and available CT imaging were initially identified.

  Forty-six patients were excluded due to insufficient CT image quality for reliable segmentation, inability to clearly delineate the primary tumor, or incomplete clinical or pathological data.

  The final study cohort therefore comprised 164 patients included in the radiomics analysis. The study was conducted and reported in accordance with TRIPOD [16] recommendations and current reporting guidelines for artificial intelligence in medical imaging (CLAIM) [17].


### Histopathological reference standard
  Thyroid transcription factor−1 (TTF−1) expression was determined as part of routine clinical histopathological assessment at the Institute of Pathology. Immunohistochemical analysis was performed on formalin-fixed, paraffin-embedded tumor tissue obtained from biopsy or surgical resection specimens.

  TTF−1 status was assessed according to routine diagnostic pathology reports and recorded as a binary variable (positive vs. negative). In clinical practice, TTF−1 positivity is defined by the presence of nuclear staining in tumor cells, without application of a fixed quantitative cutoff in routine reporting.

  Pathological assessment was performed by board-certified pathologists with expertise in thoracic pathology, who were blinded to the radiomic analysis. Detailed technical parameters of immunohistochemical staining (e.g., antibody clone, platform and scoring thresholds) were not consistently available due to the retrospective study design.


### CT imaging protocol
  All patients underwent contrast-enhanced chest CT as part of routine clinical staging. CT examinations were performed using institutional multi-detector scanners from different vendors, including a 256-row CT system (Philips iCT), a 16-row CT system (Philips Brilliance) and a 64-row CT system (Siemens SOMATOM go.Top). Image acquisition parameters were harmonized across scanners as far as clinically feasible to ensure comparability of radiomic feature extraction.

  All scans were acquired at a tube voltage of 120 kVp with automatic tube current modulation (effective mAs range: 80–250 mAs). Detector collimation was 0.6 mm and images were reconstructed with a slice thickness of 1.0–1.25 mm using a standard soft-tissue convolution kernel (Philips B / Siemens B30f). The in-plane matrix size was 512 × 512 for all examinations.

  Intravenous iodinated contrast material was administered in all patients (100 mL at a flow rate of 3–4 mL/s), followed by a saline flush. Image acquisition was performed during the venous phase according to institutional thoracic CT protocols. Only contrast-enhanced series covering the entire primary tumor were used for subsequent segmentation and radiomic analysis. Key acquisition and reconstruction parameters are summarized in Table 1.Table 1Overview of CT acquisition and reconstruction parameters.Acquisition ParameterSpecificationScanner systemsPhilips iCT (256-row), Philips Brilliance (16-row), Siemens SOMATOM go.Top (64-row)Tube voltage120 kVpTube currentAutomatic tube current modulation (80–250 mAs)Detector collimation0.6 mmSlice thickness1.0–1.25 mmReconstruction kernelStandard soft-tissue kernel (Philips B / Siemens B30f)Matrix size512 × 512Contrast agentIntravenous iodinated contrast, venous phaseContrast volume100 mLInjection rate3–4 mL/s

  To minimize the impact of technical variability on quantitative image analysis, all CT images were exported in Digital Imaging and Communications in Medicine (DICOM) format and processed using standardized preprocessing steps in accordance with Image Biomarker Standardisation Initiative (IBSI) recommendations [9].


### Tumor segmentation and radiomic feature extraction
  Primary lung tumors were segmented semi-automatically on contrast-enhanced CT images using the LIFEx software package (version 7.1.0, www.lifexsoft.org), based on established procedures, previously reported by our group [18]. Two readers with experience in thoracic imaging independently performed tumor delineation using identical segmentation settings and windowing conditions in accordance with Image Biomarker Standardisation Initiative (IBSI) recommendations [19].

  Tumor segmentation was performed in three dimensions and only the largest connected tumor component per lesion was retained for subsequent analysis to ensure consistency and avoid partial inclusion of adjacent structures. Care was taken to exclude surrounding vessels, atelectasis and pleural effusions from the segmentation masks. The overall radiomics workflow, including segmentation, feature extraction and data export, is illustrated in Fig. 1.Fig. 1Radiomics workflow for tumor segmentation and feature extraction.

  Following segmentation, a total of 107 quantitative radiomic features were extracted from each tumor volume. These features were computed in three dimensions and comprised shape-based, first-order statistical and higher-order texture features, capturing complementary aspects of tumor morphology and intralesional heterogeneity.

  Shape features (n = 14) describe the three-dimensional geometry of the tumor, including volume, surface area, compactness, elongation and sphericity. These features are independent of voxel intensity values and reflect macroscopic tumor phenotype [20].

  First-order statistical features (n = 18) were derived from the distribution of Hounsfield unit values within the segmented tumor volume and characterize global attenuation properties such as mean intensity, variance, skewness, kurtosis, and entropy.

  Texture features (n = 75) quantify spatial relationships and patterns of gray-level intensities within the tumor and were calculated using established texture matrices, including the gray-level co-occurrence matrix (GLCM), gray-level run length matrix (GLRLM), gray-level size zone matrix (GLSZM), gray-level dependence matrix (GLDM) and neighborhood gray-tone difference matrix (NGTDM). These features provide a quantitative description of intratumoral heterogeneity that may reflect underlying biological properties such as cellularity, necrosis and architectural complexity [11], [20].

  All extracted radiomic features were exported in standardized comma-separated value (CSV) format to ensure transparency and reproducibility. Subsequent preprocessing and machine-learning analyses were performed using Python (version 3.11) with established scientific libraries.


### Image preprocessing
  To reduce the influence of scanner-related variability on quantitative image analysis, standardized image preprocessing was applied prior to radiomic feature extraction. All preprocessing steps were performed within the LIFEx software environment in accordance with Image Biomarker Standardisation Initiative (IBSI) recommendations.

  All CT volumes were resampled to an isotropic voxel spacing of 1 × 1 × 1 mm using trilinear interpolation. Image intensity values were normalized using fixed absolute Hounsfield unit bounds (−1000 to +3000 HU). Gray-level discretization was subsequently performed using a fixed bin width of 10 HU to ensure consistent feature calculation across examinations.


### Interobserver reproducibility
  To assess interobserver reproducibility of radiomic feature extraction, a randomly selected subset of 55 tumors was independently segmented by a second reader using identical IBSI-compliant settings and preprocessing parameters. Both readers were blinded to pathological TTF−1 status and to each other’s segmentations.

  Radiomic features derived from paired segmentations of Reader 1 and Reader 2 were compared to quantify agreement and measurement stability. Feature-wise reproducibility was evaluated using the intraclass correlation coefficient (ICC(3,1)), based on a two-way mixed-effects model with absolute agreement for single measurements. This ICC model was chosen as it reflects interobserver agreement under fixed reader conditions and is recommended for radiomics reproducibility studies [10].

  In addition to ICC analysis, the relative deviation between observers (Δ_rel, %) was calculated for each feature as a complementary measure of absolute interobserver difference. Median ICC values and interquartile ranges (IQR) were subsequently computed across all 107 radiomic features and summarized according to feature class (shape, first-order and texture features).

  This combined approach allowed for a comprehensive assessment of feature robustness, capturing both correlation-based agreement and absolute variability between observers.


### Machine-learning models
  Three supervised machine-learning classifiers were implemented to model TTF−1 expression based on CT-derived radiomic features: logistic regression, random forest and extreme gradient boosting (XGBoost). These algorithms were selected to represent complementary learning paradigms, including linear modeling, bagging-based ensemble learning, and gradient-boosted decision trees.

  Logistic regression was used as a baseline model, assuming a linear relationship between radiomic features and the probability of TTF−1 positivity. This model provides high interpretability and served as a reference for comparison with more complex classifiers [21].

  Random forest was implemented as a non-linear ensemble model consisting of 400 decision trees trained on bootstrapped samples with random feature selection at each split. By aggregating predictions across multiple trees, random forest improves robustness and reduces variance, although performance may be limited in highly correlated, high-dimensional feature spaces [22].

  XGBoost was employed as the primary predictive model. This gradient-boosting algorithm builds decision trees sequentially, with each iteration focusing on correcting errors made by previous learners, while incorporating regularization to control model complexity [13]. Optimized hyperparameters included 500 estimators, a maximum tree depth of 5, a learning rate of 0.05, subsampling of 0.8, column subsampling of 0.7, and L2 regularization (λ = 1.0). Hyperparameter tuning was performed exclusively within the training folds to avoid information leakage.

  A simplified schematic overview of the different machine-learning approaches is provided in Fig. 2 for conceptual illustration only.Fig. 2Simplified schematic illustration of linear, bagging-based and gradient-boosting machine-learning models used for CT-based radiomics prediction of TTF−1 status.


### Model evaluation and explainability
  All machine-learning models were developed and evaluated using five-fold stratified cross-validation to preserve the distribution of TTF−1–positive and TTF−1–negative cases across folds.

  Within each cross-validation iteration, all preprocessing steps, feature handling and model training were performed exclusively on the respective training subset and subsequently applied to the corresponding validation fold, thereby preventing information leakage. Hyperparameter tuning for the XGBoost model was conducted within the training data of each fold.

  Model discrimination was primarily assessed using the area under the receiver operating characteristic curve (AUC). Secondary performance metrics included accuracy, sensitivity, specificity, precision and F1-score. Pairwise comparisons of AUC values between classifiers were performed using the DeLong test based on aggregated out-of-fold predictions across cross-validation folds [23].

  No additional class balancing techniques such as oversampling or class weighting were applied; stratified cross-validation was used to preserve class distribution across folds.

  Model calibration was assessed using the Brier score, calibration curve and calibration slope and intercept, based on aggregated out-of-fold predictions across the cross-validation folds [24]. Calibration metrics were calculated using aggregated predictions from all validation folds to ensure an unbiased estimate of model performance.

  To enhance interpretability of the machine-learning models, Shapley Additive Explanations (SHAP) were computed for the best-performing classifier. SHAP values quantify the contribution of individual radiomic features to each prediction at the patient level and allow identification of the most influential features across the cohort. All statistical analyses were performed using Python (version 3.11). A two-sided p-value < 0.05 was considered statistically significant.


## Results

### Patient and tumor characteristics
  Of the 164 included patients, 115 tumors (70.1%) were TTF−1 positive and 49 tumors (29.9%) were TTF−1 negative.

  Peripheral tumor localization was significantly more frequent in TTF−1–positive tumors compared with centrally located tumors (p = 0.04). No statistically significant differences between TTF−1–positive and TTF−1–negative groups were observed with respect to patient age or sex.

  Baseline characteristics stratified by TTF−1 status are summarized in Table 2.Table 2Baseline characteristics of the study cohort stratified by TTF−1 status. Statistical comparisons are reported in the text.CharacteristicOverall (n = 164)TTF−1 + (n = 115)TTF−1- (n = 49)Age, years (median, range)67(43–86)66(43–84)69(45–86)Sex, male95 (58%)64 (56%)31 (63%)Tumor localization: Peripheral108 (66%)82 (71%)26 (53%)Tumor localization: Central56 (34%)33 (29%)23 (47%)


### Interobserver reproducibility
  Interobserver reproducibility was assessed in a randomly selected subset of 55 tumors independently segmented by two readers. Across all 107 extracted radiomic features, the median intraclass correlation coefficient (ICC(3,1)) was 0.82, with an interquartile range (IQR) of 0.78–0.93, indicating overall good reproducibility.

  When stratified by feature class, shape features demonstrated the highest stability, with a median ICC of 0.89 and a median relative deviation (Δ_rel) of 4.2%. First-order statistical features showed moderate to good reproducibility (median ICC = 0.71; Δ_rel = 6.7%). In contrast, texture features exhibited substantially greater variability, with a median ICC of 0.55 and a median Δ_rel of 12.8%.

  The distribution of ICC values across feature classes is illustrated in Fig. 3, highlighting the superior robustness of shape-based features compared with first-order and texture-derived features.Fig. 3Interobserver reproducibility of radiomic feature classes.

  A detailed summary of interobserver reproducibility metrics stratified by feature category is provided in Table 3.Table 3Interobserver reproducibility of radiomic feature classes.Feature ClassNo. of featuresMedian ICC (3,1)IQRMedian Δ_rel (%)Shape140.890.84–0.934.2First-order180.710.66–0.786.7Texture750.550.47–0.6312.8All features1070.820.78–0.938.9


### Machine-learning model performance
  Among the evaluated machine-learning models, the XGBoost classifier achieved the highest discriminative performance for prediction of TTF−1 status. Across five-fold stratified cross-validation, XGBoost yielded a mean area under the receiver operating characteristic curve (AUC) of 0.83 ± 0.04.

  In comparison, logistic regression and random forest models demonstrated lower predictive performance, with mean AUC values of 0.67 and 0.62, respectively. Pairwise comparison of AUCs using the DeLong test confirmed that the performance of the XGBoost model was significantly superior to both logistic regression and random forest classifiers (p < 0.01 for both comparisons).

  Detailed performance metrics, including accuracy, sensitivity, specificity and F1-score for all evaluated models are summarized in Table 4.Table 4Performance of machine-learning models for CT-based prediction of TTF−1 status.ModelAUC (mean ± SD)AccuracySensitivitySpecificityF1-scoreLogistic regression0.67 ± 0.050.650.680.590.66Random forest0.62 ± 0.060.610.640.550.62XGBoost0.83 ± 0.040.770.810.690.79

  Receiver operating characteristic curves for the three classifiers are shown in Fig. 4, illustrating the improved sensitivity–specificity trade-off achieved by the gradient-boosting approach.Fig. 4Receiver operating characteristic (ROC) curves for prediction of TTF−1 status.

  Calibration analysis of the XGBoost model demonstrated reasonable overall agreement between predicted probabilities and observed outcomes, as reflected by a Brier score of 0.12. However, the calibration curve revealed deviations from the ideal diagonal, particularly in the intermediate probability range. Quantitatively, calibration slope and intercept were 0.14 and 0.60, respectively, indicating a tendency towards overconfident predictions and systematic probability misestimation (Fig. 5).Fig. 5Calibration curve of the XGBoost model based on aggregated out-of-fold predictions. The diagonal line indicates perfect calibration.


### Feature importance and model explainability
  Feature importance analysis was performed for the best-performing XGBoost model using Shapley Additive Explanations (SHAP). SHAP values were computed to quantify the contribution of individual radiomic features to model predictions at both the patient and cohort level.

  Across cross-validation folds, shape-based features consistently ranked among the most influential predictors of TTF−1 status. In particular, tumor sphericity demonstrated the highest overall impact on model output. In addition, first-order features reflecting global attenuation characteristics, including mean CT attenuation and texture-derived entropy measures were identified as important contributors to model predictions.

  Notably, the top-ranked features exhibited low interfold variability, indicating stable feature importance across cross-validation runs.


## Discussion
  This study demonstrates that a standardized, IBSI-compliant CT-based radiomics workflow enables reproducible non-invasive prediction of TTF−1 expression in lung adenocarcinoma using routine contrast-enhanced CT imaging. However, several important limitations should be considered when interpreting these findings. The present analysis is based on a retrospective, single-center cohort and relies exclusively on internal cross-validation without external validation, which may limit generalizability and result in optimistic performance estimates.

  Within these constraints, the XGBoost model achieved the highest discriminative performance among the evaluated classifiers, outperforming both logistic regression and random forest models. In addition, systematic interobserver reproducibility analysis showed good overall robustness of radiomic feature extraction, particularly for shape- and first-order features, supporting the methodological reliability of the proposed approach.

  Previous studies have reported associations between CT-derived radiomic features and molecular or immunohistochemical characteristics, including tumor subtype and oncogenic driver alterations [8], [18], [24], as well as between PET- and low-dose CT-derived radiomic features and molecular characteristics in lung cancer[25]. However, reported predictive performance varies widely and reproducibility is often insufficiently addressed. By explicitly evaluating interobserver agreement and applying standardized image preprocessing, the present study addresses a key limitation of earlier radiomics work [9]. The observed superiority of gradient-boosting–based models is consistent with prior radiomics literature, in which boosting approaches frequently outperform linear models and random forest classifiers in high-dimensional feature spaces[26]. Notably, the predictive performance achieved in this study is competitive with previously published CT-based approaches for TTF−1 prediction, despite relying exclusively on routine clinical CT data without integration of clinical or molecular variables[27].

  Interobserver reproducibility analysis revealed marked differences in robustness across radiomic feature classes. Shape features demonstrated the highest stability, followed by first-order features, whereas texture features showed substantially greater variability. These findings are in line with prior reports highlighting segmentation sensitivity as a major source of variability in radiomics and underscore the importance of reproducibility testing prior to model development[28]. The consistency of feature importance across cross-validation folds further suggests that model predictions were driven by stable imaging characteristics rather than spurious correlations. These imaging-derived features may reflect underlying tumor biology, including cellular density, structural organization, and intratumoral heterogeneity, thereby providing a plausible biological link between radiomic patterns and TTF−1 expression.

  While the model demonstrated good discriminative performance and acceptable overall calibration as reflected by the Brier score, more detailed calibration analysis revealed deviations between predicted probabilities and observed outcomes, with evidence of overconfident predictions. This finding highlights a common limitation of machine-learning models trained on relatively small, single-center datasets and underscores the need for further calibration and external validation before clinical application.

  From a clinical perspective, non-invasive prediction of TTF−1 status may complement histopathological assessment, particularly in situations where tissue sampling is limited, delayed, or associated with increased procedural risk. Importantly, this approach is not intended to replace histopathology but rather to provide additional quantitative information that may support diagnostic workflows and multidisciplinary decision-making. Given the association of TTF−1 expression with tumor subtype and molecular profiles, radiomics-based prediction may also serve as a hypothesis-generating tool for imaging-based tumor phenotyping.

  Several limitations of this study should be acknowledged. First, this was a retrospective, single-center analysis and external multicenter validation is required to confirm generalizability. Second, although standardized imaging protocols and IBSI-compliant preprocessing were applied, residual variability related to scanner vendor, reconstruction kernel, and contrast-enhancement timing cannot be fully excluded and may have influenced radiomic feature values. Third, tumor segmentation was performed semi-automatically and future studies should investigate fully automated segmentation approaches to improve scalability and clinical applicability. Finally, the analysis focused exclusively on imaging features; integration of clinical and molecular parameters may further enhance predictive performance.


## Conclusion
  In summary, this study demonstrates that a standardized, IBSI-compliant CT-based radiomics workflow shows promising performance for non-invasive prediction of TTF−1 expression in lung adenocarcinoma. Gradient-boosted machine learning achieved superior predictive performance compared with linear and bagging-based models. Radiomic feature analysis revealed that shape- and first-order features provide the highest interobserver robustness.

  However, given the retrospective single-center design and lack of external validation, further multicenter studies are required before clinical application. With continued validation and methodological refinement, CT-based radiomics may serve as a complementary imaging-based decision-support tool alongside histopathological and molecular diagnostics.


## Ethical Statement
  This retrospective single-center study was conducted in accordance with the Declaration of Helsinki. Approval was obtained from the local institutional ethics committee (approval number: EK−24–158-Br). Due to the retrospective study design and the use of fully anonymized imaging and clinical data, the requirement for informed consent was waived.


## CRediT authorship contribution statement
  Thorsten Klink: Writing – review & editing, Validation, Supervision. Jens Krugmann: Supervision. Stefan Förster: Writing – review & editing, Supervision. Jan-Niklas Trinks: Software, Formal analysis, Data curation. Nuessel Martin: Writing – original draft, Visualization, Validation, Software, Resources, Project administration, Methodology, Investigation, Funding acquisition, Formal analysis, Data curation, Conceptualization.


## Declaration of Generative AI and AI-assisted technologies in the writing process
  During the preparation of this manuscript, the authors used ChatGPT (OpenAI) to support language editing, structuring of the manuscript, and clarification of methodological descriptions. After using this tool, the authors critically reviewed and edited all content, ensured its scientific accuracy, and take full responsibility for the content of the published article.


## Declaration of Competing Interest
  The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.