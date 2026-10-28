# Predicting hormone receptor status in tumors: An innovative approach using breast ultrasound-radiomics combined model


## Abstract
  Hormone receptor (HR) status is a critical biomarker used to formulate treatment programs and prognosis in breast cancer. Traditional immunohistochemistry relies on invasive tissue samples and may not accurately reflect tumor heterogeneity. Radiomics is a noninvasive technique that involves extracting quantitative imaging characteristics from molecular profiles. The purpose of this study is to develop a combined ultrasound (US)-radiomics model to predict HR status in invasive breast cancer. A retrospective cohort of 186 patients with invasive breast carcinoma, which had been pathologically confirmed, was used in this study, comprising 150 cases (HR-positive (ER+/PR−, HER-2−)) and 36 cases (HR-negative (ER−/PR−, HER-2−)). B-mode US images of the tumor regions were manually segmented, and 463 radiomic features were obtained. T tests, ANOVA, and recursive methods were applied to create a list of features. A support vector machine with a radial basis function kernel was trained using leave-one-out cross-validation. To measure model performance, accuracy, sensitivity, specificity, area under the curve (AUC), and 95% confidence intervals (CIs) were used. The hybrid model had an AUC of 0.728 (95% CI: 0.701–0.755) and an accuracy of 67.9. The model with the highest AUC (0.753, 95% CI: 0.7240.782) was the internal echo-based model. HR-negative tumors were larger, had higher marker of proliferation (Ki-67) indices, and showed greater textural heterogeneity than HR-positive lesions (P < .05). US-radiomics combined modeling is a promising, cost-effective, and radiation-free approach to noninvasive imaging that can predict HR status in breast cancer. US biomarkers can be quantitative, providing insights into tumor microstructure to personalize diagnostic and therapeutic approaches.


## 1. Introduction
  Breast cancer is the most commonly diagnosed malignancy and a major cause of cancer-related deaths in women worldwide, with 2.3 million new cases and 670,000 deaths worldwide in 2022 alone.[1] This, along with the increasing global burden, underscores the need for improved diagnostic and prognostic strategies that enable precise tumor diagnosis and targeted therapeutic planning. A fundamental biomarker is HR status (i.e., estrogen receptor (ER), progesterone receptor (PR), and human epidermal growth factor receptor 2 (HER-2)), which dictates systemic treatment therapy and prognosis in breast cancer.[2,3] Proper detection of receptor profiles is crucial for prioritizing patients for endocrine treatment or HER-2-target therapy.[4,5]

  Conventionally, HR expression is determined by immunohistochemistry of a tissue sample either via core needle biopsy or surgical resection. Histopathological analysis is the gold standard, but has some disadvantages, such as intratumor heterogeneity, limited representativeness of the whole tumor microenvironment, and procedural risks, including bleeding and infection.[6,7] As a result, the development of noninvasive imaging biomarkers that may reflect the underlying molecular and histopathological features of tumors without requiring tissue extraction is gaining traction.[8,9]

  Ultrasound (US) is a primary imaging modality widely used in breast cancer detection and assessment because of its real-time performance, cost-effectiveness, safety, and lack of ionizing radiation.[10] Traditional US examination is also a qualitative method, but it is based on the Breast Imaging-Reporting and Data System criteria for morphology, margin, echogenicity, posterior acoustic features, and calcifications.[11] However, such qualitative measurements are operator-specific and subject to inter-observer variation, thereby restricting reproducibility and diagnostic reliability.[12]

  To address these issues, radiomics has emerged as a revolutionary analytical method that derives numerous quantitative features, such as intensity, shape, texture, and wavelet parameters, from common medical images to identify hidden patterns related to tissue biology.[8,13] Radiomics converts medical images into high-dimensional data, enabling data-driven, noninvasive tumor phenotyping complementary to traditional imaging interpretations. Radiomics has demonstrated promising potential in breast cancer by distinguishing between benign and malignant lesions, evaluating lymph node status, predicting molecular subtypes, and predicting treatment response rates.[14–16]

  US-based radiomics (US-radiomics) is becoming increasingly popular, although radiomics studies in breast cancer have primarily used MRI or PET/CT.[17,18] US-radiomics can measure tumor heterogeneity, internal echoes, and acoustic texture, which may indirectly reflect microstructural changes related to receptor expression and tumor biology.[19,20] For example, textural inhomogeneity and attenuation of posterior echoes can be signs of stromal fibrosis or necrotic areas, which are often associated with HR-negative or high-grade lesions.[21] Moreover, US-radiomics, when used with machine learning algorithms such as support vector machines (SVMs), strengthens the discriminatory capabilities of both HR-positive and HR-negative tumors.[22,23]

  Despite this improvement, several research gaps remain. Most US-radiomics studies have small sample sizes, no external validation, and a minimal, effective combination of quantitative biomarkers for imaging and clinicopathological variables.[24,25] In addition, although it has been demonstrated that radiomic texture features are associated with proliferative indices such as marker of proliferation (Ki-67),[26] few studies have examined whether radiomic texture features are directly related to HR performance in invasive breast cancer. Further studies are needed to confirm the validity of radiomics-based models and demonstrate their applicability for preoperative molecular stratification.

  The current investigation aims to establish and test an US-radiomics-combined model that has the potential to indicate the HR status of invasive breast cancer patients. This study aimed to identify noninvasive imaging biomarkers that predict ER/PR expression using qualitative US characteristics, quantitative radiomics descriptors, and machine learning classifiers. We hypothesized that radiomic markers derived from preoperative US images may be associated with the molecular phenotype of breast tumors, thereby providing a reliable, readily available, and cost-effective supplement to histopathological analyses to support personalized treatment planning.


## 2. Methods

### 2.1. Study design and ethical approval
  This observational, retrospective study was conducted according to the Strengthening the Reporting of Observational Studies in Epidemiology (STROBE) guidelines to assess the diagnostic accuracy of an US-radiomics integrated model for predicting HR status in breast cancer. The study was conducted at Shandong Cancer Hospital and Institute, Shandong First Medical University, and Shandong Academy of Medical Sciences/August 2022–2024. The hospital’s Institutional Review Board approved the study (approval no. SDTHEC-202508031). All procedures were conducted in accordance with the principles of the Declaration of Helsinki, and all patients provided written informed consent for inclusion. The privacy of the clinical data and imaging information was ensured during the study.


### 2.2. Patient selection and classification
  Initial screening was conducted on 506 women with histologically confirmed breast cancer. The eligibility criteria were as follows: invasive breast carcinoma; presence of high-quality preoperative US images in Digital Imaging and Communications in Medicine format; absence of previously administered neoadjuvant chemotherapy and radiotherapy before tissue sampling; and complete clinicopathological and immunohistochemical information. The exclusion criteria were: low image quality due to artifacts or contrasting lesion presence; multifocal or bilateral lesions of the breast; absence of clinical or pathological data; and HER-2 positive tumor due to confounding interactions between receptors. Using these criteria, the analysis was eventually narrowed to 186 patients.

  HR disorders were determined using immunohistochemistry of excised specimens. The expression levels of the ER, PR, and HER-2 were assessed according to the American Society of Clinical Oncology/College of American Pathologists (ASCO/CAP) guidelines.[2] Patients were categorized into 2 groups: HR-positive (ER+/PR+/HER-2) and HR-negative (ER−/PR−/HER-2). The total number of HR-positive cases was 150, and 36 were HR-negative. This distribution reflects the inherent clinical imbalance in the receptor status in breast cancer populations.


### 2.3. US image acquisition and preprocessing
  All patients underwent US imaging on high-end diagnostic systems, namely SUPERSONIC Aixplorer (SuperSonic Imagine, France) and GE Logiq E9 (GE Healthcare, USA), both equipped with high-frequency linear array transducers (615 MHz). Two board-certified radiologists with more than 5 years of experience in breast imaging were examined. Acquisition parameters, such as fixed frequency, gain, and time-gain compensation, were used to control imaging conditions across patients. Longitudinal and transverse images of the lesions were obtained, and images of the maximum cross-sectional tumor area were stored in the Digital Imaging and Communications in Medicine format for analysis.

  To reduce inter-operator variability, radiologists independently reviewed and selected the best image slice for each lesion. In the event of any dispute, a consensus was reached. The identified US images were further normalized by intensity and gray-level resampling to equalize the pixel intensity distributions and eliminate variations caused by acquisition settings. Image preprocessing was performed using ITK-SNAP and Python-based in-house scripts to ensure reproducibility.


### 2.4. Lesion segmentation and radiomics feature extraction
  The breast tumor region was manually segmented using a phase-based active contour algorithm, which was potentiated in the ITK-SNAP. This segmentation system delivers the best results, including precise tumor boundary definition, by identifying the phase congruency and spatial frequency characteristics that ensure good separation of tumor regions from the parenchyma. The radiologists reviewed each segmented region of interest (ROI) and ensured boundary precision. Cases with segmentation discrepancies exceeding 5% in the ROI were reanalyzed to ensure consistency.

  Using Python libraries that conformed to the PyRadiomics framework, 463 radiomic features were extracted for each ROI. These characteristics are summarized as follows:

  Available features: wavelet features, which are high- and low-frequency textural patterns of various scales. To remove variability across patients, all extracted features were z-score-normalized.


### 2.5. Feature selection and model development
  A multistep feature-reduction pipeline was used to avoid overfitting and minimize redundancy. Univariate statistical tests (independent-samples t test and ANOVA) were performed to identify features associated with the HR status (P < .05). Variables that did not satisfy the required significance level were excluded. The remaining features were further polished using Recursive Feature Elimination with a SVM classifier. It ranks features by importance and sequentially eliminates the least informative features until the model achieves optimal performance.

  A SVM classifier with a Radial Basis Function kernel was selected because it performs better in high-dimensional spaces and supports non-linear relationships. The hyperparameter grid search (penalty parameter C and kernel coefficient 7) was optimized using cross-validation (leave-one-out cross-validation (LOOCV)), where 1 model was left out at each iteration. The LOOCV approach was used due to the moderate sample size and the need for sound model generalization. At each iteration, a single case was set aside as the test set, and the remaining cases were used for training. The process was repeated until each case was used once as a test set.


### 2.6. Performance evaluation and statistical analysis
  Accuracy, sensitivity, specificity, and area under the receiver operating characteristic (ROC) curve (AUC) were used to quantify model performance. All metrics are reported with 95% confidence intervals (CIs) generated via bootstrapping with 1000 iterations. Sensitivity denotes the true-positive rate (appropriate identification of HR-positive tumors), and specificity denotes the true-negative rate (appropriate identification of HR-negative tumors). ROC curves were constructed to demonstrate discriminative performance at various decision thresholds. The independent-samples t test or Mann–Whitney U test was used to compare continuous variables between the groups, whereas the chi-square test was used to compare categorical variables. Statistical significance was set at P < .05.

  All statistical and modeling operations were performed in Python (version 3.8; Python Software Foundation) using the NumPy, Pandas, Scikit-learn, and Matplotlib packages. Reproducibility Version-controlled scripts were maintained in the Conda environments and Git repositories. All modeling was performed on a Linux-based high-performance computing server equipped with NVIDIA RTX graphics.


### 2.7. Reproducibility, validation, and data management
  All data preprocessing, feature extraction, and modeling parameters were logged into an exhaustive dataset to ensure the reproducibility of the experiment. A code was used to anonymize each patient, and it was important not to re-identify a patient (through this method, each patient was assigned a distinct, unique anonymized code). Internal validation of the trained SVM model was performed using LOOCV, where the final model with the highest mean AUC across folds was selected as the optimal classifier. Even though external validation data were not available at this stage, the study design provides a basis for a future multicenter prospective study to test the model’s generalizability.


## 3. Results

### 3.1. Schematic workflow diagram
  The schematic in Figure 1 summarizes the overall methodological workflow, including image acquisition, segmentation, feature extraction, feature selection, and model development.


### 3.2. Patient enrollment and grouping
  Of 506 breast cancer cases screened initially, 186 met all inclusion criteria and were included in the final analysis (Fig. 2). The HR-positive (ER−PR, HER-2−) group, consisting of 150 (80.6) patients, and the HR-negative (ER−PR−, HER-2) group, comprising 36 (19.4) patients, were matched. The HR-positive group had a mean age of 53.7 ± 8.5, and the HR-negative group had a mean age of 56.8 ± 9.2 (no significant difference, P = .071). The general procedure for patient selection is shown in Figure 2.


### 3.3. Clinicopathological characteristics
  Table 1 shows the baseline clinicopathological features of the study groups. No significant differences were observed between the groups for surgical approach, histopathological subtype, lymph node status, or area of vascular invasion (P > .05). Nonetheless, the tumor volume (cm3) was notably lower in cases with HR-positive tumors (2.38 cm3), but not in cases with HR-negative tumors (2.69 cm3; P = .033). Similarly, the Ki-67 proliferation index showed a significant difference between HR-negative tumors (P = .002), consistent with their aggressive biological behavior.


### 3.4. US morphological and radiomic characteristics
  Both qualitative and quantitative US characteristics were assessed and compared with the HR expression levels. As shown in Table 2, there were significant differences between the HR-positive and HR-negative groups in some 2-dimensional US characteristics. In the HR-positive population, tumors were more likely to have an irregular morphology and anterior acoustic attenuation (P < .001). In contrast, HR-negative lesions were more likely to have round contours and anterior enhancement (P < .001). Burr-interval margins or microlobulations were more frequently observed in HR-positive tumors (26.8%) than in HR-negative tumors (3.9%; P = .001). The difference between calcifications was not significant (P = .928).


### 3.5. Quantitative radiomics analysis
  Segmented tumor regions were extracted into a total of 463 radiomic features. Screening t tests and ANOVA revealed that 87 features exhibited significant group-level differences (P < .05). This was further narrowed to feature elimination (Recursive Feature Elimination), which identified 50 optimal features as those that contributed the most to model performance. Table 3 shows the quantitative measures of HR status correlated with the significant measures. The HR-negative group showed greater differences in the mass area, texture roughness, and posterior echo intensity, indicating increased internal heterogeneity.


### 3.6. Model performance evaluation
  The SVM classifier with a Radial Basis Function kernel achieved good predictive performance when combined with radiomic and morphological features. The combined model, as shown in Table 4, had an overall accuracy of 67.9% (95% CI: 63.2–72.5) and an AUC of 0.728 (95% CI: 0.701–0.755) when predicting HR status using leave-one-out cross-validation. The radiomics subset of internal echoes showed the best discriminative ability (AUC = 0.753; 95 percent CI: 0.724–0.782); 2nd, the models based on the form (AUC = 0.553); and 3rd, the models based on edge features (AUC = 0.662). A comparison of morphological categories in terms of classification performance is shown in Figure 3, which presents the ROC curve.

  The diagnosis revealed several significant imaging biomarkers for the HR status. HR-negative breast cancers are also more likely to have larger lesion areas, smooth edges, elevated internal heterogeneity in the echo, acoustic enhancement in the back, and histological aggressiveness. In contrast, HR-positive tumors commonly exhibit posterior attenuation, irregular shapes, and high edge roughness values. The radiomics-integrated model demonstrated strong, noninvasive predictive power for HR status and may be used in preoperative molecular profiling and personalized treatment planning.


## 4. Discussion
  The study showed that an US-radiomics composite model, combining routine B-mode parameters with quantitative image biomarkers and machine-learning models, can predict HR status in invasive breast cancer with an AUC of 0.728 and an internal echo-based subset AUC of 0.753. These results support the possibility of using US-radiomics as a noninvasive diagnostic adjunct to histopathology to profile receptors and plan personalized treatment.


### 4.1. Interpretation of findings
  The model’s moderate performance has a clinically significant impact, given its noninvasive nature and the widespread availability of US. The higher AUC for the internal echo features indicates that intratumoral texture heterogeneity and acoustic attenuation may contain information about receptor expression. The features of HR-negative tumors include necrosis, stromal desmoplasia, and diminished glandular differentiation, which create a coarser texture and posterior acoustic enhancement on US.[21] HR-positive tumors, usually well-differentiated and fibroglandular, on the other hand, usually exhibit posterior attenuation and irregular but well-delimiting margins.[26] These microstructural variations, which are radiometrically measured by intensity variation, gray-level evenness, and wavelet energy, are probably the basis for imaging biological correlations.


### 4.2. Comparison with Previous Research
  The AUC of our combined model (0.728) was comparable to those of radiomics models developed using other imaging modalities. Li et al. (2019)[27] reported an AUC of 0.70 for predicting ER status using MRI radiomics, and Kim et al. (2020) reported an AUC of 0.68 with features derived from PET-CT.[28] A recent pooled meta-analysis of radiomics-based predictions of molecular subtypes in breast cancer identified a pooled modal value of 0.69–0.75.[15] Thus, the simplicity of the US-based model, coupled with its low cost, aligns with more resource-intensive approaches. Furthermore, compared with MRI or PET, US is radiation-free, inexpensive, portable, and repeatable longitudinally, which is highly beneficial in low- and middle-income healthcare centers.

  This reproducibility potential was emphasized by Tian et al. (2024), who developed a multicenter US-radiomics transfer learning model with diagnostic accuracy (AUC = 0.75) similar to that of a single-center model, thereby demonstrating the modality’s potential.[18] Our results are also supported by a study published in Frontiers in Oncology (2024) that used deep-texture descriptors combined with handcrafted US-radiomics to improve molecular subtyping. Recently, a Photoacoustics (2025) study revealed that radiomic features combined with photoacoustic biomarkers improved the prediction of ER/PR expression, further underscoring the growing importance of hybrid US modalities in breast molecular imaging.[29]


### 4.3. Clinical and Translational Implications
  Translationally, these studies’ results indicate that radiomics-based US analysis can supplement biopsy-based receptor assessment across multiple clinical settings. First, when core needle sampling cannot be performed, or only inconclusive results are obtained, noninvasive radiomic prediction can assist in screening patients for further testing or initial therapy. Second, US biomarkers may be used to monitor treatment by measuring changes within tumors before morphological shrinkage occurs. Finally, radiomics signatures could also help risk-stratify screening programs by characterizing lesions that are more likely to be HR-negative and aggressive, thereby guiding management decisions.

  Radiomics requires an interpretable and reproducible model to be integrated into the clinical workflow. New explainable-AI methods, such as SHAP (Shapley Additive Explanations (SHAP) and Local Interpretable Model-Agnostic Explanations (LIME)), can explain the contribution of each radiomic feature to the classification result.[30] Such frameworks may be applied to our SVM classifier to visualize the texture, shape, or wavelet parameters that primarily affect HR prediction, thereby enabling clinicians to trust and regulate their acceptance.


### 4.4. Strengths and Methodological Considerations
  The current study used a standardized image acquisition protocol, strict feature extraction via a developed radiomics pipeline, and LOOCV to reduce overfitting. It combines morphological and quantitative US parameters, and consequently, its diagnostic accuracy is greater than that of models using traditional descriptors alone. Additional evidence supporting the biological plausibility of the model is that Ki-67 data were strongly correlated with HR-negative tumors, which is consistent with the radiomic evidence of increased tumor heterogeneity.

  However, several methodological drawbacks must be mentioned. The retrospective, single-center design and small sample size, particularly the imbalance between HR-positive (n = 150) and HR-negative (n = 36) cases, could limit the generalizability of the model. LOOCV helped alleviate overfitting, but external validation should be conducted using multicenter data to assess robustness. Differences in US systems, worker techniques, and image processing across institutes can affect feature reproducibility. Therefore, it is important to harmonize acquisition settings and image normalization procedures to ensure cross-site use. Furthermore, all 463 features were extracted 1st, with the descriptors being of high order and not necessarily biologically meaningful. To establish imaging phenotypes related to molecular pathways, future research must include a framework for feature interpretability and correlative histopathology.


### 4.5. Limitations
  This research also has several limitations, including its retrospective design, small sample size, and single-centricity, which limit its external validity. The imbalance between positive and negative HR cases, lack of external verification, and fluctuations in US machine performance and operator technique can contribute to a decline in the reliability and reproducibility of the findings. Moreover, manual segmentation and the derivation of many radiomic features that lack clear biological significance are problematic for interpretability. The omission of HER-2-positive tumors and the emphasis on HR-positive and HR-negative targets further limit the model’s applicability, as other subtypes have not been investigated. Finally, no longitudinal data were available, limiting the ability to assess treatment response or tumor recurrence over time.


### 4.6. Future directions
  To test these findings further, prospective multicenter studies are warranted to provide external validation of the model and establish benchmarks for reproducibility. Automated segmentation and deep learning feature extraction can enhance the efficiency and scalability. In addition, when US-radiomics is combined with other omics layers (transcriptomics, proteomics, or circulating tumor DNA), it can be applied to a fully radiogenomic profile for precision oncology. As hybrid imaging systems such as elastography and photoacoustic modalities continue to develop, incorporating multiparametric US information could further improve predictive performance and enhance biological interpretability.


## 5. Conclusion
  In conclusion, this study assessed the viability of a composite US-radiomics model for predicting HR status in invasive breast cancer. The model had sufficient (AUC = 0.728) but stable precision, suggesting the potential of US-radiomics as a helpful, readily available, radiation-free method for molecular characterization. This characteristic allows mapping of imaging phenotypes to receptor biology, facilitating a shift in the paradigm of noninvasive precision diagnostics that will enable the management of breast cancer patients at the individual level.


## Author contributions
  Conceptualization: Xue Yin, Zhen Wang.

  Data curation: Qinxian Zhao.

  Formal analysis: Qinxian Zhao, Xincun Zhang, Tian Sang, Changjie Shao.

  Funding acquisition: Zhen Wang.

  Investigation: Tian Sang, Changjie Shao.

  Methodology: Xue Yin, Zhen Wang.

  Project administration: Zhen Wang.

  Resources: Qinxian Zhao, Changjie Shao.

  Supervision: Zhen Wang.

  Validation: Xue Yin, Tian Sang.

  Writing – review & editing: Xue Yin, Xincun Zhang.

  Writing – original draft: Zhen Wang.