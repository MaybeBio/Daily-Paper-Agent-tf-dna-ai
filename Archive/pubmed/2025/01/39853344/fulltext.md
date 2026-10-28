# Detecting B-cell lymphoma-6 overexpression status in primary central nervous system lymphoma using multiparametric MRI-based machine learning


## Purpose
  In primary central nervous system lymphoma (PCNSL), B-cell lymphoma-6 (BCL-6) is an unfavorable prognostic biomarker. We aim to non-invasively detect BCL-6 overexpression in PCNSL patients using multiparametric MRI and machine learning techniques.


## Methods
  65 patients (101 lesions) with primary central nervous system lymphoma (PCNSL) diagnosed from January 2013 to July 2023, and all patients were randomly divided into a training set and a validation set according to a ratio of 8 to 2. ADC map derived from DWI (b = 0/1000 s/mm2), fast spin echo T2WI, T2FLAIR, were collected at 3.0 T. A total of 2234 radiomics features from the tumor segmentation area were extracted and LASSO were used to select features. Logistic regression (LR), Naive bayes (NB), Support vector machine (SVM), K-nearest Neighbor, (KNN) and Multilayer Perceptron (MLP), were used for machine learning, and sensitivity, specificity, accuracy F1-score, and area under the curve (AUC) was used to evaluate the detection performance of five classifiers, 6 groups with combinations of different sequences were fitted to 5 classifiers, and optimal classifier was obtained.


## Results
  BCL-6 status could be identified to varying degrees with 30 models based on radiomics, and model performance could be improved by combining different sequences and classifiers. Support vector machine (SVM) combined with three sequence group had the largest AUC (0.95) in training set and satisfactory AUC (0.87) in validation set.


## Conclusion
  Multiparametric MRI based machine learning is promising in detecting BCL-6 overexpression.


## Supplementary Information
  The online version contains supplementary material available at 10.1007/s00234-025-03551-y.


## Introuduction
  Primary central nervous system lymphoma (PCNSL) is a rare and aggressive form of extra-nodal non-Hodgkin lymphoma confined to the central nervous system (CNS), including the brain, spine, meninges, and eyes, with more than 90% of cases histologically classified as diffuse large B-cell lymphoma (DLBCL) [1–2]. In contrast to other high-grade non-Hodgkin lymphoma outside the CNS, PCNSL is particularly aggressive and the overall survival time of untreated PCNSL patients is limited to 1.5 months [3, 4]. The observed variations in clinical characteristics and treatment outcomes in DLBCL patients can be attributed to the significant genetic and molecular diversity that drives the disease aggressiveness and tumor advancement [5].

  The major molecular markers of PCNSL, including B-cell lymphoma-2 (BCL-2), MYC, B-cell lymphoma-6 (BCL-6), Ki-67, etc., are related to the prognosis. Overexpression of both BCL-2 and MYC proteins, known as double-expression lymphomas (DEL), has been well investigated. Previous studies have identified that BCL-6 expression is also an useful biomarker for predicting poor prognosis and reduced survival rates [5–8]. Therefore, the prognostic value of BCL-6 may aid in determining the relevant prognosis of PCNSL and guide the therapeutic decisions. In PCNSL, pathologic diagnosis is primarily made based on fine-needle aspiration, but biopsies are invasive and have the risk of undersampling [9]. Patients with PCNSL typically undergo brain MRI examinations prior to treatment, making MRI a possible non-invasive method for detecting the BCL-6 status [10].

  The potentials of radiomics analysis in predicting molecular characteristics in brain tumors have been reported [11–12]. Liu et al. has demonstrated that DEL and non-DEL status can be effectively differentiated using multiparametric MRI based machine learning radiomics in immunocompetent PCNSL [13]. Another study showed a significant correlation between whole tumor ADC histogram profiling and Ki-67 expression, a marker of active proliferation in PCNSL [3]. Bathla et al. reported that radiomics combined with machine learning model can distinguish PCNSL and glioblastoma excellently [14]. Additionally, previous studies have demonstrated the utility of radiomics in distinguishing among PCNSL, glioma, and metastasis [15–18]. In this study, our purpose was to determine whether multiparametric MRI radiomics features could help detect BCL-6 expression status in immunocompetent PCNSL.


## Materials and methods

### Patient cohort
  This retrospective study was approved by the hospital’s ethics committee (No. S2022-671-01), and the requirement for written informed consent was waived. Between January 2013 and July 2023, 69 pathologically proved PCNSL patients were retrieved from the PACS of our hospital. Four of them were excluded due to the usage of steroid treatment before MR scan or blurred MR images. Finally, 65 patients (101 lesions) were included in this study, among whom 40 were BCL-6 overexpression (23 males and 17 females, mean age, 58.11 ± 13.65 years) and 25 were BCL-6 underexpression (16 males and 9 females, mean age, 56.59 ± 12.40 years). Patients were included according to the following criteria: (1) pathologically confirmed DLBCL; (2) immunohistochemical staining results of BCL-6 (> 30% was defined as BCL-6 overexpression [BCL-6 (+)], ≤ 30% was defined as BCL-6 underexpression [BCL-6 (-)]); (3) patients were immunocompetent (determined by past history and laboratory tests including HIV, lymphocyte ratio, IgG, etc.); and (4) over 18 years of age. The exclusion criteria included: (1) incomplete MRI protocol or obvious artifacts in MR images; (2) MR scans after chemotherapy, radiotherapy, or steroid usage; (3) MR scans after tumor resection; and (4) incomplete histological results. All the clinical data, MRI protocol, and MR image artifacts were collected and assessed by A (6-year work experience), B (6-year work experience), and C (3-year work experience). The flowchart of patient inclusion was shown in Fig. 1. Risk score was assessed using three categories (low, intermediate, and high) based on the International Extranodal Lymphoma Study Group (IELSG) [19] and the Memorial Sloan-Kettering Cancer Center prognostic model (MSKCC) [20], respectively.

  Fig. 1Flowchart of the study cohort. PCNSL = primary centeral nervous system lymphoma


### MRI protocol
  MR images were acquired on a 3T MRI system (Discovery 750, GE Healthcare, Milwaukee, WI) with a 32-channel head coil. MR imaging protocol included axial fast spin echo T2 weighted imaging (T2WI, repetition time [TR]/echo time [TE] = 5642/93 msec, field of view [FOV] = 24 × 24 cm, matrix = 512 × 512, number of excitation [NEX] = 1.50), coronal T2 fluid-attenuated inversion recovery (T2FLAIR) (TR/TE/inversion time [TI] = 8527/162/2100 msec, FOV = 24 × 24 cm, matrix = 288 × 224, NEX = 1.00), axial diffusion-weighted imaging (DWI, TR/TE = 3000/65.5 msec, FOV = 24 × 24 cm, b = 0/1000 sec/mm2, matrix = 160 × 160, and NEX = 2.00), with a slice thickness of 5.0 mm and gap of 1.5 mm for all the axial and coronal images.


### Tumor segmentation
  DICOM images were converted to the NIfTI format, and the image structure was segmented using ITK-SNAP [21]. The areas of interest were comprised of tumor solid components and necrosis or cystic changes, except the hemorrhage. Meanwhile, lesions with a minimum diameter of more than 5 mm were included so as to ensure a reliable measurement. Three dimension Segmentations were delineated on ADC, T2WI, and T2FLAIR, respectively, and intergroup consistency by intraclass correlation coefficient (ICC) was conducted. Regions of interest were drawn by A (6-year work experience) and B (6-year work experience). Tumor segmentation on different MRI sequences was demonstrated in Fig. 2.

  Fig. 2An example of tumor segmentation. The red label represented the solid part of the tumor


### Feature extraction
  Radiomics features were extracted by a customized version of Pyradiomics from Python (Version 3.8.8). A total of 2234 radiomics characteristics were extracted from each tumor segment in each set of images used in the machine learning models. The interpretation and calculation formulas, as well as all radiomics features, were presented on Pyradiomics website (https://pyradiomics.readthedocs.io/en/latest/features.html). The extracted features contained 14 shape features, 36 first-order histogram features, and 75 s-order features (also called texture features).

  Filters such as the original image, 8 wavelet transforms, 5 log-sigma transforms, square, square root, logarithmic, exponential, gradient, and LBP-2D transform images were used to select the features.


### Feature selection
  Feature reduction was performed through the following steps.1) The extracted features with ICC ≥ 0.80 were selected. 2) Levene assay was used to analyze the normal distribution of test features. The correlation between features and BCL-6 expression was then assessed by t-test, and features with P < 0.05 were considered as potential predictors. 3) Least absolute shrinkage and selection operator (LASSO) regression was used to select features. 4) The final subset of features was filtered based on this number and the ranking of the feature weights.


### Classifier modeling
  Based on the 3 MRI sequences, 6 sequence groups (ADC, T2WI, T2FLAIR, ADC + T2WI, ADC + T2FLAIR, and ADC + T2WI + T2FLAIR) were selected. One sequence group (T2 + T2FLAIR) was deleted since no features were presented. Subsequently, five possible classifiers built on the machine learning tool kit of scikit-learn (https://scikit-learn.org) were used to adapt to these combinations. The following classifiers were used: logistic regression (LR), Naive Bayes (NB), support vector machine (SVM), K-nearest neighbor (KNN), and Multilayer Perception (MLP). The best features were combined with five different machine learning algorithms to filter the optimal model. Five-fold cross-validation was performed in the training set. Finally, the validity of 30 different models were evaluated. Default parameters were used for all machine learning models in this study.


### Tumor Morphologic Assessment
  Based on previous studies, [22–23] tumor morphology was selected and evaluated: (1) Tumor location was determined by the lesion center and divided into two groups: supratentorial or infratentorial, peripheral or median parenchyma (basal ganglia, thalamus, brainstem, and cerebellum). (2) The maximum and minimum diameters of the maximum layer of tumor were measured on T2WI. (3) ADC values, including ADCmean, ADCmax, ADCmin, ADC percentile, and ADC uniformity were calculated (4) Necrosis or cystic changes were defined as areas showing hyperintensity on T2WI.5) Edema (Table S1 in the Supplemental Material) and mass effect levels (Table S2 in the Supplemental Material). These tumor morphologic features were assessed by A. (6-year work experience), B (6-year work experience), and C (3-year work experience). Representative case images in BCL-6(+) and BCL-6(-) were shown in Fig. 3.

  Fig. 3MRI in a 47-year-old male PCNSL patient with BCL-6(-). The tumor shows isointensity on axial T2WI (a), restriction on axial ADC map (b), and slight hyperintensity on coronal T2FLAIR (c). MRI in a 76-year-old female PCNSL patient with BCL-6(+). The tumor shows slight hyperintensity on axial T2WI (d), restriction on axial ADC map (e), and isointensity on coronal T2FLAIR (f)


### Statistical analysis
  The statistical product service solutions (version 26.0) were utilized to analyze statistical differences in clinical data and MR imaging features of lesion between BCL-6 (+) and BCL-6 (-) groups. Continuous variables were assessed by the t-test, while categorical variables were assessed by the nonparametric test. P value < 0.05 were considered statistically significant. The inter group consistency was tested by ICC, and ICC ≥ 0.80 was considered to be a strong correlation. Sensitivity, specificity, accuracy, F1-score, and area under curve (AUC) for each machine learning model were calculated.


## Results

### Clinical and lesion characteristics
  In clinical characteristics, no significant difference was found in age (P = 0.36), gender (P = 0.60), MSKCC (P = 0.42), number of lesions (P = 1.00), or pathologic measure (P = 0.52) between BCL-6 (+) and BCL-6 (-) (Table 1). IELSG (P = 0.02) shows significant difference between BCL-6 (+) and BCL-6 (-). As for MR imaging features, location (P > 0.05), maximum diameter (P = 0.15), minimum diameter (P = 0.35), ADCmax (P = 0.76), ADCmin (P = 0.10), ADC 5 percentile (P = 0.18), ADC uniformity (P = 0.26), necrosis or cystic change (P = 0.13), edema (P = 0.56), or mass effect (P = 0.81) did not show significant difference between BCL-6 (+) and BCL-6 (-). ADCmean (P = 0.00) showed significant difference between BCL-6 (+) and BCL-6 (-). (Table 2).

  Table 1Clinical data between BCL-6 (+) and BCL6 (-)ALLBCL-6 (+)BCL-6 (-)P valueNumber of patients654025Age (mean ± SD, year)57.52 ± 13.1458.11 ± 13.6556.59 ± 12.400.36Gender (%)0.60Male39 (60.00)23 (57.50)16 (64.00)Female26 (40.00)17 (42.50)9 (36.00)IELSG (%)0.02Low17 (26.15)8 (20.00)9 (36.00)Intermediate45 (69.23)32 (80.00)13 (52.00)High3 (4.62)0 (0)3 (12.00)MSKCC (%)0.42Low16 (24.62)11 (27.50)5 (20.00)Intermediate36 (55.38)23 (57.50)13 (52.00)High13 (20.00)6 (15.00)7 (28.00)Number of lesions(%)1.00Single39 (60.00)24 (60.00)15 (60.00)Mutiple26 (40.00)16 (40.00)10 (40.00)Pathologic measure(%)0.52Stereotactic biopsy38 (58.46)23 (57.50)15 (60.00)Partial excision9 (13.85)7 (17.50)2 (8.00)Whole excision18 (27.69)10 (25.00)8 (32.00)Distribution of BCL-6 expression status was reported as absolute counts (%). Age was reported as mean ± SD. BCL-6 (+), BCL-6 overexpression; BCL-6 (-), BCL-6 underexpression; IELSG, International Extranodal Lymphoma Study Group; MSKCC, Memorial Sloan-Kettering Cancer Center score for PCNSL outcome; SD, standard deviation

  Table 2MR Imaging features of the lesionsALLBCL-6 (+)BCL-6 (-)P valueNumber of lesions1016239Location (%)Supratentorial86 (85.15)56 (90.32)30 (76.90)0.07Infratentorial15 (14.85)6 (9.68)9 (23.10)Midline56 (55.45)38 (61.29)18 (46.15)0.14Peripheral45 (44.55)24 (38.71)21 (53.85)Maximum diameter (mean ± SD, mm)29.71 ± 13.9228.82 ± 14.9331.18 ± 12.180.15Minimum diameter (mean ± SD, mm)16.71 ± 9.7215.69 ± 8.7518.33 ± 11.010.35ADCADCmean0.91 ± 0.310.83 ± 0.380.95 ± 0.260.00ADCmax2.47 ± 0.992.47 ± 1.022.48 ± 0.940.76ADCmin0.14 ± 0.410.19 ± 0.400.06 ± 0.430.10ADC 5 percentile0.56 ± 0.280.59 ± 0.250.51 ± 0.320.18ADCuniformity0.27 ± 0.100.26 ± 0.100.30 ± 100.26Necrosis or cystic change (%)0.13Yes35 (34.65)25 (40.32)10 (25.64)No66 (65.35)37 (59.68)29 (74.36)Edema (%)0.56153 (52.48)35 (56.45)18 (46.15)233 (32.67)18 (29.03)15 (38.46)315 (14.85)9 (14.52)6 (15.38)Mass effect (%)0.81018 (17.82)12 (19.35)6 (15.38)140 (39.60)24 (38.71)16 (41.03)211 (10.89)8 (12.90)3 (7.69)323 (22.77)12 (19.35)11 (28.21)49 (8.91)6 (9.68)3 (7.69)Distribution of BCL-6 expression status was reported as absolute counts(%). Maximum diameter and minimum diameter were reported as mean ± SD. BCL-6 (+), BCL-6 overexpression; BCL-6 (-), BCL-6 underexpression; SD: standard deviation


### Performance of the classification models
  After feature selection, the remaining features (sequence, feature filter, feature type, and feature name) for each sequence group were as follows: ADC (number of features [nfeature] = 10), T2WI (nfeature = 4), T2FLAIR (nfeature = 5), ADC + T2WI (nfeature = 15), T2WI + T2FLAIR (nfeature = 0), ADC + T2FLAIR (nfeature = 11), and ADC + T2WI + T2FLAIR (nfeature = 17) (Table S3 in the Supplemental Material). The pipeline for BCL-6 expression detection was depicted in Fig. 4.

  Fig. 4The pipeline for BCL-6 overexpression detection


### Radiomics model construction
  Of the 101 lesions, 81 lesions, including 49 BCL-6 (+) and 32 BCL-6 (-), were in the training set, and 20 lesions, including 13 BCL-6 (+) and 7 BCL-6 (-), were in the validation set.

  In the training set, the diagnostic performance of five machine learning with single and three sequences was shown in Table 3. Among the five machine learning methods, SVM with three sequence group achieved better classification performance (AUC = 0.95) than the others, with a sensitivity of 92.0%, specificity of 88.0%, accuracy of 93.0%.

  Table 3Model performance of single sequence groups and three sequence group in training setSequenceModelSensitivitySpecificityAccuracyF1 scoreAUCADCLR0.850.750.760.820.78NB0.920.500.780.830.75SVM0.920.750.880.900.85KNN0.770.880.830.870.86MLP0.770.880.810.860.82T2WILR0.730.860.630.650.70NB0.641.000.720.770.73SVM0.910.860.720.720.80KNN0.461.000.780.810.84MLP0.820.860.740.800.74T2FLAIRLR0.671.000.690.750.71NB0.830.860.680.750.64SVM0.670.880.790.840.80KNN0.830.380.740.790.76MLP0.751.000.680.690.76Three sequenceLR0.750.750.900.890.86NB0.830.630.780.820.82SVM0.920.880.930.940.95KNN0.831.000.800.820.85MLP0.750.880.860.890.93AUC, area under curve; LR, logistic regression; NB, Naive Bayes; SVM, support vector machine; KNN, K-nearest neighbor; MLP, Multilayer Perception

  In the validation set, the diagnostic performance of five machine learning with single and three sequences was shown in Table 4. SVM with three sequence group also achieved satisfactory classification performance (AUC = 0.87) with a sensitivity of 98.0%, specificity of 84.0%, accuracy of 90.0%. The diagnostic performance of five machine learning with two sequence groups could be seen in Table S4 and S5 in the Supplemental Material.

  Table 4Model performance of single sequence groups and three sequence group in validation setSequenceModelSensitivitySpecificityAccuracyF1 scoreAUCADCLR0.880.580.810.850.84NB0.880.610.760.830.73SVM0.920.830.860.890.89KNN0.940.650.810.830.87MLP0.920.650.810.830.86T2WILR0.510.790.780.630.81NB0.770.660.780.780.86SVM0.610.900.890.910.83KNN0.790.760.670.630.76MLP0.880.520.830.860.84T2FLAIRLR0.740.610.800.800.85NB0.760.550.800.830.72SVM0.900.610.750.760.72KNN0.800.650.650.740.61MLP0.580.840.850.860.87Three sequenceLR0.920.770.750.780.77NB0.840.680.750.820.69SVM0.980.840.900.910.87KNN0.720.940.900.910.91MLP0.860.870.800.820.80AUC, area under curve; LR, logistic regression; NB, Naive Bayes; SVM, support vector machine; KNN, K-nearest neighbor; MLP, Multilayer Perception


## Dicussion
  In the present study, the BCL-6 status was determined using multiparametric MRI based machine learning, which involved the selection of an optimal model from a total of 30 models comprising 6 distinct sequence groups and 5 classifiers. This approach offers a promising and non-invasive means for identifying the molecular subtypes, specifically the expression of BCL-6, in PCNSL. The multiparametric MRI radiomics model exhibited a high level of diagnostic accuracy in identifying BCL-6 status, as evidenced by an AUC of 0.95 (95% CI 0.883–1.000), in the training set. Furthermore, the model demonstrated consistent performance in the validation set, achieving an AUC of 0.87 (95% CI: 0.703–1.000), indicating its reliability.

  DLBCL mainly presents in two distinct molecular subtypes, with gene expression reflecting varying stages of B-cell differentiation. One subtype exhibited gene expression patterns typical of germinal center B cells, referred to as “germinal center B-like DLBCL”, while the other subtype displayed gene expression signatures consistent with in vitro activation referred to as “activated B-like DLBCL” [24]. Notably, the germinal center B-like DLBCL signature prominently features the BCL-6 gene, a widely recognized germinal center marker and the most commonly translocated gene in DLBCL [25]. The specific expression of BCL-6 protein in normal germinal center B lymphocytes, along with its essential role in germinal center development, suggests a complex interplay between the functions of BCL-6 in both normal and malignant B cells. The BCL-6 protein is a transcriptional repressor with the potential to regulate lymphocyte differentiation and promote lymphomas through the modulation of key downstream target genes [25]. As such, the impact of BCL-6 on the prognosis of patients with PCNSL remains a subject of inquiry. A prospective multicenter trial (CALGB 50202) conducted in 2013 sought to address this question, and ultimately demonstrating a significant association between BCL-6 expression and decreased survival rates[6]. Other studies also indicated that BCL-6 assume clinical relevance as an unfavorable prognostic biomarker in PCNSL [7, 26].

  IELSG scoring system is frequently utilized to stratify the risk levels of patients with PCNSL. IELSG added age, performance status, lactate dehydrogenase, cerebrospinal fluid protein, and deep brain lesions involvement as risk factors for PCNSL. In this study, IELSG score showed marginally significant difference between BCL-6 (+) and BCL-6 (-) (P = 0.02). Further research with larger sample size is needed to investigate the correlation between the IELSG scoring system and BCL-6 expression status.

  In immunocompetent patients, PCNSL typically shows hypo- or isointense on T1-weighted imaging (T1WI) and iso- to slight hyperintense on T2WI. Most lesions show evident homogeneous enhancement on TICE, and slight low to iso- perfusion on perfusion-weighted imaging (PWI). In clinical practice, diffuse gliomas, including glioblastoma, are more commonly encountered. IDH-wildtype glioblastomas usually demonstrate hypointense on T1WI and heterogeneous hyperintense on T2WI. Hemorrhage and necrosis are more commonly revealed, and heterogeneous enhancement and hyperperfusion are seen in glioblastomas. Therefore, the differentiation between PCNSL and glioblastoma is relatively easy to implement.

  In our study, conventional MR imaging findings did not demonstrate marked differences between BCL-6(+) and BCL-6(-) in PCNSL. MR imaging findings, such as location, necrosis or cystic change, maximum diameter, minimum diameter, edema, or mass effect, could not be used to detect BCL-6 overexpression. Besides, relevant quantitative ADC parameters were calculated, and only ADCmean values showed significant difference between BCL-6 (+) and BCL-6 (-). ADCmean value in BCL-6(+) group was lower than that in BCL-6(-) group. ADC values, a quantitative index of diffusion characteristics, could provide information about cellular density and the tortuosity of the extracellular space, and tend to decrease in areas with restricted diffusion [27]. Low ADC values were associated with poorer clinical outcomes in various cancers [28–29], and our findings were consistent with the result that low ADC value was regarded as an independent unfavorable prognostic factor in PCNSL patients [30].

  Radiomics is a new translational field in which a range of attributes, such as geometry, strength, and texture [31–32], are determined from radiological images to allow for capturing different imaging patterns [33–34]. These patterns have the potential to aid in tumor classification, grading, and staging when integrated with clinical, histopathological, molecular, and traditional imaging parameters [14, 32–33, 35]. In our study, a combined conventional sequence (ADC + T2WI + T2FLAIR) based radiomics and machine learning approach was used to successfully identify BCL-6 expression status. The most effective model in this study was found to be SVM with an AUC of 0.95 and a Confidence Interval (CI) of 0.883–1.000. SVM, grounded in the principles of VC dimension and minimum structural risk theory in statistics [36], has been widely applied in various medical fields including preoperative diagnosis, prognostic prediction, disease differentiation, and clinical grading [37–38]. It was noteworthy that we only used three non-contrast MR sequences to achieve the satisfactory performance, and the result suggests that BCL-6 could still be detected in patients who are not suitable for contrast-enhanced MR scan.


### Limitation
  Firstly, this was a single-center study conducted on single scanner, and the sample size was relatively small, leading to a possible selection bias. Secondly, post-contrast MR scan or MR perfusion techniques were not used in our study. Thirdly, only BCL-6 was investigated in this study, neglecting the detection of other biomarkers such as Ki-67, BCL-2, and MYC. Lastly, default parameters were applied to all machine learning models without delving into the specific settings of individual models. Further analysis to determine the optimal parameters for each model will be pursued in future studies.


## Conclusion
  In this study, multiparametric MRI based machine learning combining three conventional sequences (ADC, T2WI, and T2FLAIR) with SVM had the best performance in detecting BCL-6 status, providing a potential and promising tool in therapeutic planning and prognostic assessment in PCNSL.


## Electronic supplementary material
  Below is the link to the electronic supplementary material.

  Supplementary Material 1


## Acknowledgements
  We thank all the subjects for participating in the study.