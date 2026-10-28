# MRI Radiomics Signatures of 21‐Gene Recurrence Score for Predicting Survival in ER+/HER2− Breast Cancer


## Background
  Oncotype DX 21‐gene assays are recommended for evaluating distant recurrence and guiding decisions on the use of adjuvant therapy in ER+/HER2− breast cancers. However, it cannot be widely applied due to the high cost and time consumption.


## Purpose
  To identify MRI radiomics signatures within tumor and peritumoral tissues associated with the 21‐gene recurrence score (RS) and explore their value in predicting 5‐year recurrence in young women with ER+/HER2− breast cancer.


## Methods
  Two datasets were analyzed; all the enrolled patients were diagnosed with ER+/HER2− breast cancers and underwent preoperative breast MRIs. The radiogenomic development dataset, with RS data obtained from April 2017 to March 2019, was used to identify optimal RS‐signatures based on tumoral, peritumoral, and dilation radiomics features as well as clinical‐imaging characteristics with the support vector machine method. The prognosis dataset, in which patients aged 18 to 40 years received breast surgery followed by adjuvant chemotherapy from 2012 to 2016, was used to evaluate the prognostic implication of the proposed optimal RS‐signatures by measuring 5‐year disease‐free survival (DFS) with the Cox proportional hazards model.


## Results
  159 patients (111 in the training and 48 in the validation groups) and 111 young patients (a mean follow‐up time of 49.6 months and a 5‐year DFS of 83.8%) were enrolled in these datasets, respectively. Areas under the receiver operating characteristic curve (AUCs) of the three optimal RS‐signatures were 0.74 (95% CI: 0.59–0.87), 0.75 (95% CI: 0.61–0.88) and 0.74 (95% CI: 0.59–0.87) respectively. In the prognosis dataset, there were significant differences in survival between the patients in the predicted high‐risk and low‐risk groups categorized by the above three signatures, and the predicted recurrence risks were independent factors for DFS.


## Conclusion
  The radiomic signatures within the tumor and peritumoral region exhibited potential to guide decisions on the use of chemotherapy and predict survival.


## Introduction
  Oncotype DX 21‐gene assays are recommended by the National Comprehensive Cancer Network (NCCN) guidelines for evaluating distant recurrence and guiding decisions on the use of adjuvant systemic therapy in ER+/HER2‐ patients [1]. The 3.2024 version of NCCN guidelines (available at NCCN.org) recommends that patients be stratified into low, medium, and high recurrence risk groups using the 21‐gene assay recurrence score (RS) of 15 and 26 as the cutoffs [1]. High‐risk patients benefit from adjuvant chemotherapy; low‐risk patients are recommended to be exempted from chemotherapy, and intermediate‐risk patients need to make decisions based on comprehensive clinical information. The 21‐gene test is currently not widely used in the clinic because it is costly and time‐consuming.

  Breast MRI is the most sensitive technology for diagnosis and treatment response evaluation in breast cancers [2, 3, 4, 5]. Extracting richer information from MRI images, such as objective quantitative features, instead of traditional subjective MR imaging features, is now possible due to the development of radiomics. What is more, the tumor microenvironment has been shown to play an important role in the development and progression of breast cancer [6, 7], so the region of interest in radiomics extends from the tumor to the peritumoral tissues. A few studies, which tried to identify MRI‐based biomarkers of RS, reported potential correlations between the RS and traditional MR imaging and tumoral and peritumoral radiomic features [8, 9, 10, 11, 12, 13, 14]. However, among the studies mentioned above, those adopting the latest RS cutoff are very limited [10, 11]. Additionally, some studies included patients with ER− or HER2+ breast cancer who do not meet the current guideline‐recommended application population [8, 9, 13, 14]. Studies involving T2WI sequences are rare and very few studies focused on the peritumoral environment [10, 11].

  On the other hand, although few studies have established RS‐prediction models based on radiomic characteristics [11, 14], the associations of these models with realistic clinical survival remain unclear. Only one study by Fan et al. [15] demonstrated that the RS‐prediction model has potential value in evaluating the efficacy of neoadjuvant therapy. To our knowledge, there has never been a published study exploring its value in assessing survival after adjuvant chemotherapy in young patients.

  Therefore, the objectives of this study were (1) to identify MRI radiomics signatures associated with RS within tumor and peritumoral tissues in patients with ER+/HER2− breast cancer and (2) to estimate the value of the proposed signatures in assessing survival after adjuvant chemotherapy in young women.


## Materials and Methods

### Dataset
  This retrospective study was approved by the ethics committee of Fudan University Shanghai Cancer Center (2203252‐23), and informed consent was waived. Two independent datasets were involved: the radiogenomic development dataset and the prognosis dataset. The radiogenomic development dataset was used to identify radiomics signatures associated with the recurrence risk quantified by RS, obtaining a model to predict recurrence risk, while clinical, MR imaging, and radiomic characteristics of prognosis dataset patients were applied to verify the prognostic value of the proposed models in young women who did not perform 21‐gene tests. The study framework is shown in Figure 1.


#### Radiogenomic Development Dataset
  Patients with invasive breast cancer who underwent preoperative MRI examination and Oncotype DX 21‐gene assay in our hospital from April 2017 to March 2019 consecutively were screened (n = 170) for the radiogenomic development dataset, and clinicopathological information and MRI data were collected. The patients were divided into a training group and a validation group according to the time order and ratio of 7:3 (Figure 1a).


#### Prognosis Dataset
  The prognosis dataset included patient data from the SPECTRUM (Substitution of paclitaxel for cyclophosphamide on survival outcomes and resumption of menses in young women with ER‐positive breast cancer) trial [16]. Patients aged 18 to 40 years and diagnosed with unilateral operable breast cancer who underwent breast conservation surgery or mastectomy at our hospital from 2012 to 2016 were screened. All the patients were ER+/HER2− confirmed by postoperative pathology. Patients with preoperative breast MRI data who received adjuvant epirubicin/cyclophosphamide followed by weekly paclitaxel (EC‐wP) or epirubicin/paclitaxel followed by weekly paclitaxel (EP‐wP), followed by endocrine therapy for at least 5 years were enrolled (n = 197) (Figure 1b).


#### Exclusion Criteria for the Two Datasets
  The exclusion criteria for the two datasets were as follows: had positive or equivocal HER2 expression; no pathological information; poor image quality; and nonnegligible movement artifacts; MRI sequences were incomplete; lesions were not clearly visible on the MR images; lesions on the MR images were incomplete, and parts of the lesions were out of range on the MR images; and MRIs were obtained after minimally invasive breast surgery.


#### Follow‐Up of the Prognosis Dataset
  All the patients in the prognosis dataset were followed up in June 2019. The follow‐up information was as follows: (a) whether recurrence or metastasis occurred, and if so, when recurrence or metastasis occurred; (b) whether there was a second primary breast cancer or other second primary malignant tumor, and if so, the first time of detection; and (c) whether the patient died, and if so, the cause and time of death. Disease‐free survival (DFS) was defined as the time from the beginning of postoperative chemotherapy to the occurrence of recurrence, metastasis, second primary breast cancer, other second primary cancers or death.


### Clinical Characteristics
  Clinical information of the patients in the radiogenomic development dataset was obtained from the electronic medical record system, including age, body mass index, and whether they were postmenopausal. We also obtained their pathology type, progesterone receptor (PR) status, tumor size, invasive malignancy grade, whether they had concomitant ductal carcinoma in situ, and whether they had lymph node metastasis from the pathology report.

  For the prognosis dataset, age, type of surgery, chemotherapy regimen, whether or not they received radiotherapy, PR status, tumor size, invasive malignancy grade, and whether or not they had lymph node metastasis were used in the analysis.


### MRI Protocol
  The MRI scans were completed under three different MRI scanners, and the scanning parameters are shown in Table S1. During examination, patients were in a prone position, and both breasts were naturally placed in a 16‐channel mammary coil. The MRI examinations included T2WI and dynamic contrast enhancement (DCE) in the transverse plane, T2WI used turbo spin–echo or short time inversion recovery sequence, and DCE was obtained using T1‐weighted volume imaging for breast assessment (VIBRANT) or 3D gradient‐echo volumetric interpolated breath‐hold examination (VIBE) sequence. After a plain scan, the contrast agent was injected (Magnevist, Bayer HealthCare Pharmaceuticals Inc., Wayne, USA) at a rate of 1.5–2.0 mL/s at a dose of 0.1 mmol/kg, followed by a 20 mL saline flush. The first phase of enhanced images was collected at 30–46 s after the injection of the contrast agent; then, 3–4 phases of enhanced scanning images were obtained continuously without intervals, and the image acquisition time of each phase was 38–40 s.


### Recurrence Score
  All enrolled patients of the radiogenomic development dataset underwent a 21‐gene expression assay, and the RS was obtained at our hospital. The RS ranged from 0 to 100; the greater the RS, the higher the 10‐year recurrence risk and the greater the benefit of chemotherapy. According to the 3.2024 version of the National Comprehensive Cancer Network (NCCN) clinical practice guidelines for breast cancer (available at NCCN.org) [1], this study used 26 as the cutoff value and divided the patients into a low‐risk group (RS < 26) and a high‐risk group (RS ≥ 26).


### MR Imaging Feature Evaluation
  Two experienced breast radiologists (with 11 and 6 years of experience in breast imaging diagnosis) reviewed and evaluated the patients' MR images according to the 2013 version of the Breast Imaging Reporting and Data System (BI‐RADS) lexicon [17]. The amount of fibroglandular tissue was divided into extreme fibroglandular tissue, heterogeneous fibroglandular tissue, scattered fibroglandular tissue, and almost entirely fat. The degree of background parenchymal enhancement was divided into four categories: minimal, mild, moderate, and marked. MRI findings included non‐mass enhancement (NME) and mass, and their enhancement curve type (persistent, plateau type, or washout) and BI‐RADS classification were evaluated. If MRI showed a mass, it was necessary to describe the shape (round, oval, or irregular), margin (circumscribed, irregular, or spiculated), and internal enhancement characteristics (homogeneous, heterogeneous, rim enhancement, or dark internal septation). If an NME was observed, its internal enhancement characteristics (homogeneous, heterogeneous, clumped or clustered ring) and distribution (focal, linear, segmental, regional, multiple regions or diffuse) were recorded.

  If the evaluation results of these two radiologists were inconsistent, a third senior radiologist (with 21 years of experience in breast imaging diagnosis) reviewed the images and determined the final results. The three radiologists knew that all the lesions were invasive breast cancers, but they were blind to the RSs.


### Volume of Interest Segmentation
  A radiologist (6 years of experience) manually delineated the lesion contour layer by layer in the last phase of post‐enhancement (CL) images to obtain the tumoral volume of interest (VOI), with all lesions included. Then, the VOI was copied onto T2W, pre‐enhancement (C0), first phase of post‐enhancement (CF), and middle phase of post‐enhancement (CM) images. The VOIs were checked one by one, and manual adjustments were made for those that did not match the lesion well. Open source software (ITK‐SNAP, version 3.8.0, http://www.itksnap.org/) was used for manual VOI segmentation and adjustment, and VOI replication was completed in Python (version 3.8).

  On the basis of the tumoral VOI, Python 3.8 was used to automatically dilate the VOI contour outward, with dilation ranges of 2, 4, 6, 8, and 10 mm. In this way, dilated VOIs (tumor + circular peritumor regions of 2, 4, 6, 8, and 10 mm) were obtained. By subtracting the tumoral VOI from the dilated VOI, the peritumoral VOI could be obtained (circular areas of 2, 4, 6, 8, and 10 mm around the tumor, excluding the internal region of the tumor). Check each dilated and peritumoral VOI, and manually adjust the VOI beyond the breast contour. An example of the VOI segmentation is shown in Figure 2.


### Image Preprocessing and Radiomic Feature Extraction
  Because the MRI examinations were obtained with three different MRI scanners, the scanning parameters were not completely consistent. Before feature extraction, the image signal intensity was standardized, and the spatial resolution was unified. (1) The formula for image signal intensity standardization was as follows: Inormalize=I−μσ×100

  I normalize is the normalized image gray value, I is the original image signal intensity, and μ and σ are the mean value and standard deviation of I, respectively. (2) Using the cubic spline interpolation algorithm, the spatial resolution of the DCE images (including C0, CF, CM and CL) was resized to 0.9 × 0.9 × 2.2 mm, and the spatial resolution of the T2W images was resized to 1.2 × 1.2 × 7 mm.

  After image preprocessing, 1046 features were extracted from each VOI, including 100 original image features, 258 Laplacian of Gaussian (LoG) image features, and 688 wavelet image features. LoG features were extracted by filtering the original images with a LoG filter with δ values of 2.0, 3.0, and 4.0. We also filtered the original images with a wavelet filter to extract the wavelet features. The bin width was set to 5. The Python package from PyRadiomics (v1.3.1, PyRadiomics Community) was used to extract features, and all other parameters were set to their default values.


### Feature Selection and Radiomic Model Construction
  All features were standardized by the z score method, and the validation group features were standardized using the average and standard deviation of the training group features. To reduce multicollinearity between features, Pearson correlation coefficient screening and recursive feature elimination (RFE) methods were implemented. First, the Pearson correlation coefficient was calculated between every feature pair. For those with a Pearson correlation coefficient > 0.9, the mean Pearson correlation coefficient was calculated between each of them and all other features, and the feature with the higher mean Pearson correlation coefficient was removed. The base estimator for RFE feature filtering was the least absolute shrinkage and selection operator (LASSO) algorithm, and α was set to the default value of 1. The upper limit for feature number was 10% of the sample size, and the feature set with the highest model accuracy was selected as the optimal one.

  Due to the imbalanced distribution between the low‐risk and high‐risk groups in the training group, the synthetic minority oversampling technique (SMOTE) was used to resample the training group before establishing the model, while the data from the validation group patients were not resampled. Then, an RS‐prediction model was constructed using the linear support vector machine (SVM) method. The predictive performance of the model was evaluated by receiver operating characteristic (ROC) curve analysis. The data processing above was completed in Python (version 3.8).


#### Tumoral Model Construction
  DCE (C0, CF, CM, CL) and T2 sequences were used to construct tumoral models. The optimal tumoral model was fused with clinical‐imaging features to obtain a fusion model (Model 1).


#### Construction of the Peritumoral Model
  Peritumoral models were constructed based on the features of CL and T2W images, and the optimal peritumoral model was selected to be fused with “Model 1” to construct a fusion model (Model 2), which included peritumoral, tumoral, and clinical‐imaging information. In the model fusion process, a logistic regression analysis was performed by combining the predicted probability of the optimal peritumoral model with that of Model 1.


#### Dilation Model Construction
  The dilation classifiers were developed using features from dilated VOIs on CL, T2W images and their combination. The optimal dilation model was subsequently selected and combined with clinical‐imaging features to generate a fusion model (Model 3).


### Assessment of the Prognostic Implications of Radiogenomic Signatures
  We identified predictive RSs (predRSs) of the prognosis dataset by incorporating their characteristics into the top 3 predictive models (Model 1–3).

  The Kaplan–Meier method was used to analyze the survival of patients in different predRS groups; the log‐rank test was performed to determine whether differences existed between the predRS groups. The univariate log‐rank test was used to select supplementary clinical‐imaging features related to the DFS, which were incorporated into the Cox proportional hazards model as well as the predRS, with duplicate features removed. The Cox model was visualized and evaluated by a forest plot, nomogram, and calibration curve.

  A p value < 0.05 was considered to indicate statistical significance. The relevant data processing and statistical plotting were performed using Python (version 3.8), GraphPad Prism (version 9.5.0), and SPSS software (version 25.0).


## Results

### Clinical and MR Imaging Characteristics of the Radiogenomic Development Dataset
  According to the chronological order and 7:3 ratio, patients in the radiogenomic development dataset who underwent the 21‐gene assay from April 2017 to July 2018 were classified into the training group, including a total of 111 patients, 34 at low risk and 77 at high risk. Patients who underwent the 21‐gene assay testing from August 2018 to March 2019 were included in the validation group, which included 48 patients, 24 at low risk and 24 at high risk. In the training group, the average age of the low‐risk patients was significantly higher than that of the high‐risk patients, and there was a significant difference in the tumor margins between patients with different recurrence risks (Tables 1 and 2). The other clinical features and imaging characteristics were not significantly different (Tables 1 and 2).


### Performance of Radiogenomic Signatures

#### Performance of Tumoral Models
  For tumoral models, the CL‐T2 model had the highest performance, with an AUC of 0.71 in the validation group. The CL‐T2‐ClinicalImaging model (Model 1) was constructed by incorporating clinical‐imaging features into the CL‐T2 model; the performance of Model 1 was further improved, with an AUC of 0.74.

  The Model 1 included a total of eight features, involving three features from T2W images (T2_log‐sigma‐4‐0‐mm‐3D_Gray‐Level Size Zone Matrix_SmallAreaLowGrayLevelEmphasis, T2_wavelet‐LLH_Gray‐Level Co‐occurrence Matrix_Idn and T2_wavelet‐LLL_Gray‐Level Dependence Matrix _LargeDependenceLowGrayLevelEmphasis), one feature from CL (CL_wavelet‐HHL_firstorder_Kurtosis), and four clinical‐imaging features (PR status, mass margin, amount of fibroglandular tissue and NME internal enhancement).

  The performance of each tumoral model is shown in Figure 3 and Table S2, and the incorporated radiomic features are shown in Figure S1.


#### Performance of Peritumoral Models
  Among the 15 peritumoral models in the validation group, the highest AUC was achieved by the model within the 4 mm peritumoral region on T2W images (T2_p4), with an AUC of 0.66 (95% CI = 0.49–0.81) and an accuracy, sensitivity, and specificity of 0.60, 0.67, and 0.54, respectively (Figure 4a and Table S3).

  The T2_p4 model was combined with Model 1 to construct a fusion model (Model 2). In the validation group, the AUC of Model 2 was 0.75, which was higher than that of the T2_p4 model (AUC = 0.66) and Model 1 (AUC = 0.74) (Figure 4b,c).

  The features included in these models are shown in Appendix S1.


#### Performance of the Dilation Models
  Among the 15 dilation models, the AUC for the 4 mm dilation region on CL (CL_d4) was highest in the validation group (0.69, 95% CI = 0.51–0.82) (Table 3 and Figure S2a).

  Clinical‐imaging features were incorporated into CL_d4 model. The AUC of CL_d4‐ClinicalImaging (Model 3) was 0.74, which was higher than those of CL_d4 (AUC = 0.69) and ClinicalImaging (AUC = 0.68) models (Figure S2b,c).

  The features included in the dilation models are shown in Appendix S2.


### Characteristics of the Prognosis Dataset
  A total of 111 patients were included in the prognosis dataset, whose clinical‐imaging characteristics are summarized in Table 4. The mean follow‐up time was 49.6 months (range 10–84 months); a total of 18 patients (16.2%) experienced recurrence, metastasis, or death, with a mean disease‐free survival (DFS) of 30.9 months (range 10–60 months). Three of them experienced local recurrence, 11 had distant metastasis, two had contralateral primary breast cancer, one had a second primary malignancy, and one died.


### Predictive RS
  The top three proposed models were selected: the CL‐T2‐Clinicalimaging model (Model 1), the T2_p4‐Model1 model (Model 2) and the CL_d4‐ClinicalImaging model (Model 3). Three groups of predicted RSs were generated by plugging the features of the prognosis dataset into the above three models; these RSs were denoted as model1_predRS, model2_predRS, and model3_predRS.

  Model 1 predicted 79 high‐risk patients, 16 of whom had recurrence or metastasis, and the recurrence rate was 20.3% (16/79). Two of the predicted low‐risk patients developed recurrence and metastasis, for a recurrence rate of 6.3% (2/32). Model 2 and Model 3 predicted 78 high‐risk patients, 16 of whom had recurrence and metastasis, for a recurrence rate of 20.5% (16/78). Two of the predicted low‐risk patients experienced recurrence and metastasis, for a recurrence rate of 6.1% (2/33).

  K–M curves of the predRSs are shown in Figure 5. The log‐rank test showed that there were significant differences between the predicted high‐risk group and the low‐risk group stratified by the three models.


### Prognostic Assessment of Radiogenomic Signatures
  Univariate log‐rank test showed that there were significant differences in lesion size, surgical type, and tumor margin in the prognosis dataset (Table 4), which along with predRS were included in Cox proportional hazards analysis (Figure 6, Figures S3 and S4).

  All three Cox models showed that both predRS and surgery type had significant impacts on survival time, with recurrence or metastasis more likely to occur in patients with predicted high risk and mastectomy. The Cox1 and Cox2 models also showed that pT2/3 lesions were associated with a greater risk of recurrence or metastasis than pT1 lesions.

  The nomogram showed how different factors predict 3‐ and 5‐year survival. The calibration curves indicated good agreement between the prediction and observation data for the three Cox models; the 3‐year survival prediction calibration performance was better than that of the 5‐year survival prediction.


## Discussion
  The National Comprehensive Cancer Network (NCCN) guidelines recommend using the 21‐gene assay to assist in the decision of whether chemotherapy is required after surgery for ER+/HER2− early breast cancer [18, 19]. However, this test is expensive and time‐consuming. In this study, a 21‐gene RS‐prediction model was constructed using radiomic features extracted from tumor and peritumoral tissues, which indicated that these radiomic features could reflect recurrence risk. Additionally, the predictive model has the potential to reflect survival after adjuvant chemotherapy in young patients with breast cancer.

  We constructed tumoral prediction models using different phases of DCE and T2W images, and the CL‐T2 model performed best. Several previous studies have shown that there was a correlation between DCE radiomics characteristics and the RS [9, 14, 20, 21], I which is consistent with the findings of the present study. Moreover, compared with those of the C0‐ and CM‐based models, the CF and CL models had higher AUCs, suggesting that the vascular distribution and permeability may differ between high‐ and low‐risk lesions and that early and delayed enhancement have greater value in predicting prognosis. For T2W images, some published studies have also indicated that T2W images have potential value in evaluating the prognosis of breast cancer patients, although the molecular type and clinical stage of the patients involved are different [22, 23, 24, 25]. In a study by CHEN Y et al. [11], a T2‐based RS‐prediction model was established, similar to the results of the present study, with an AUC of 0.60. The predictive performance of the CL‐T2 model was better than that of the models based on CL or T2 alone. Several studies have also supported the use of T2W combined with DCE features, which are useful for identifying not only breast cancer but also other tumors [24, 26, 27]. After adding clinical‐imaging features to the CL‐T2 model, the performance improved, with an AUC of 0.74 in the validation group. These results indicated that there could be complementary information in CL, T2WI, and clinical‐imaging features.

  In this study, multiple RS‐prediction models involving the peritumoral environment (including peritumoral and dilatation models) were established, suggesting that peritumoral features have potential value in predicting prognosis. A study published in 2021 focused on locally advanced rectal cancer showed that combining intratumoral features with peritumoral features could help to predict the efficacy of neoadjuvant therapy [28]. In terms of breast cancer, Piero et al. [10] developed a partial least square regression model by using peritumoral and intertumoral radiomic features to predict the RS, indicating the potential value of the peritumoral region. However, in addition to the small sample size (n = 62), this study focused only on CF and CL and never explored the value of T2W images.

  This study showed that the proposed RS‐prediction model could independently affect the survival time of breast cancer patients. Fan Ming et al. [15] also established an RS‐prediction model based on MRI radiomics and found that the model was an independent predictor for evaluating the outcome after neoadjuvant therapy, which was partially consistent with the findings of the present study. To the best of our knowledge, this study is the first to investigate RS‐predictive models for evaluating survival after adjuvant chemotherapy in young patients. Moreover, this study focused not only on the tumoral radiomic features extracted from DCE images, as in Fan Ming et al.'s study [15], but also on the peritumoral and T2WI characteristics.

  Our study showed that the predicted RS was positively correlated with the recurrence rate; that is, patients in the predicted high‐risk group had a higher recurrence rate than those in the low‐risk group. A study by Woodward et al. [29] showed the 10‐year local recurrence rate of low‐risk patients (RS < 18) was 9.7%, which was significantly lower than that of patients in the medium‐high‐risk group (16.5%). The research subjects in Maoli Wang et al.'s study [30] included a total of 4059 patients from the Surveillance, Epidemiology and End Results database; these patients were stratified with an RS of 11 and 25 as the cutoffs. The results showed that the RS risk groups were positively correlated with pathological and prognostic stage (p < 0.001), and there were significant differences in breast cancer‐specific survival and overall survival among the RS groups (p < 0.001). Our study is to some extent consistent with these two studies.


## Limitations
  The study had some limitations. First, although the validation group was set up in this study, the number of subjects in our study was limited, especially compared with numerous imaging radiomics features, and the subjects were from one center, which might cause population selection bias. Studies with larger sample sizes are needed to further explore this topic. Second, the MRI examination in this study was completed under different scanners with different scanning parameters. Although we have adopted a number of methods to improve the robustness of the model, the interscanner variability still could not be completely avoided. Third, this study did not involve DWI sequence, which was important in breast MRI, and it is necessary to carry out relevant studies on DWI prediction of RS in the future. Finally, the tumoral VOI was segmented manually and time‐consumingly. In the future, automatic or semiautomatic VOI segmentation methods, combined with automatic correction technology, probably will improve the work efficiency and repeatability of VOI segmentation.


## Conclusion
  In conclusion, we identified and validated 21‐gene RS‐prediction signatures based on both tumoral and peritumoral radiomics characteristics, suggesting information on the MR images could reflect the biological behavior of tumors. The proposed RS‐prediction model could provide an alternative for patients who cannot afford the 21‐gene assay or reduce the medical costs for patients who could afford it, which was an attempt to increase cost‐effectiveness as well as expand the number of patients who would benefit from the 21‐gene assay to some extent. Our study also explored extending the applicable population of the RS‐prediction model to young patients with adjuvant chemotherapy, and the results revealed that the proposed RS‐signature was associated with the 5‐year recurrence rate of them, which was an attempt to predict individual survival and assist stratification management in young patients.


## Author Contributions
  Weijun Peng: conceptualization (equal), resources (equal). Yang Chen: conceptualization (equal), formal analysis (equal), writing – original draft (equal), writing – review and editing (equal). Lizhi Xie: conceptualization (equal), formal analysis (equal), writing – original draft (equal), writing – review and editing (equal). Wei Tang: conceptualization (equal), resources (equal). Qin Xiao: data curation (equal). Li Liu: data curation (equal). Tianwen Xie: methodology (equal). Yan Huang: data curation (equal). Qifeng Wang: methodology (equal). Keda Yu: conceptualization (equal), resources (equal). Yajia Gu: conceptualization (equal), funding acquisition (lead), resources (equal).


## Ethics Statement
  The study was approved by the ethics committee of Fudan University Shanghai Cancer Center (2203252–23), and all measures of the study were in accordance with the Declaration of Helsinki guidelines.


## Consent
  The informed consent requirement was waived by virtue of this study's retrospective design.


## Conflicts of Interest
  The authors declare no conflicts of interest.


## Supporting information

## Data Availability Statement
  The clinical data related to patients and MRI images can be obtained from the corresponding author on reasonable request.


## Acknowledgments
  The authors thank Ling Zhang (Department of Radiology, Fudan University Shanghai Cancer Center, 270 Dongan Road, Shanghai 200032, China) and Rong Li (Department of Radiology, Fudan University Shanghai Cancer Center, 270 Dongan Road, Shanghai 200032, China) for their help in image collection and MR technical problems. The authors also thank Caixia Fu (MR Application Development, Siemens Shenzhen Magnetic Resonance Ltd., Shenzhen, China) for her suggestions on image preprocessing.