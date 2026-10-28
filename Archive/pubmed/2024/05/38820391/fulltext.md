# Diagnostic performance of ultrasound-based artificial intelligence for predicting key molecular markers in breast cancer: A systematic review and meta-analysis


## Background
  Breast cancer (BC) diagnosis and treatment rely heavily on molecular markers such as HER2, Ki67, PR, and ER. Currently, these markers are identified by invasive methods.


## Objective
  This meta-analysis investigates the diagnostic accuracy of ultrasound-based radiomics as a novel approach to predicting these markers.


## Methods
  A comprehensive search of PubMed, EMBASE, and Web of Science databases was conducted to identify studies evaluating ultrasound-based radiomics in BC. Inclusion criteria encompassed research on HER2, Ki67, PR, and ER as key molecular markers. Quality assessment using Quality Assessment of Diagnostic Accuracy Studies (QUADAS-2) and Radiomics Quality Score (RQS) was performed. The data extraction step was performed systematically.


## Results
  Our meta-analysis quantifies the diagnostic accuracy of ultrasound-based radiomics with a sensitivity and specificity of 0.76 and 0.78 for predicting HER2, 0.80, and 0.76 for Ki67 biomarkers. Studies did not provide sufficient data for quantitative PR and ER prediction analysis. The overall quality of studies based on the RQS tool was moderate. The QUADAS-2 evaluation showed that the studies had an unclear risk of bias regarding the flow and timing domain.


## Conclusion
  Our analysis indicated that AI models have a promising accuracy for predicting key molecular biomarkers’ status in BC patients. We performed the quantitative analysis for HER2 and Ki67 biomarkers which yielded a moderate to high accuracy. However, studies did not provide adequate data for meta-analysis of ER and PR prediction accuracy of developed models. The overall quality of the studies was acceptable. In future research, studies need to report the results thoroughly. Also, we suggest more prospective studies from different centers.


## 1. Introduction
  Breast cancer (BC) is the most prevalent malignancy worldwide (11.7% of all cancer cases in 2020), and it is acknowledged as one of the leading causes of cancer-related mortality (6.9% of all cancer-related deaths in 2020), according to GLOBOCAN reports [1]. Traditional predictors such as tumoral and pathological properties are well-established in BC but could not classify the patients comprehensively regarding intra- and inter-patient heterogeneity. Therefore, developing more reliable and precise predictors could facilitate categorizing patients into subtypes with distinct characterizations [2, 3]. Molecular biomarker profiling of BC, determined by gene expression experiments, could classify patients into different subtypes based on different expression levels of these biomarkers in each subtype [4]. This classification revealed that BC subtypes have distinct diagnostic, therapeutic, and prognostic features that can significantly aid escalation/de-escalation options. Estrogen receptor (ER), progesterone receptor (PR), human epidermal growth factor receptor 2 (HER2), and Ki67 are the main molecular biomarkers in patients of BC [5]. Evidence has shown that hormone receptors such as ER and PR are associated with a good prognosis, and PR/ER-negative patients have a poorer prognosis [6]. Patients with positive HER2, a transmembrane tyrosine kinase receptor, have been shown to have a poorer prognosis and more aggressive features of the tumor [7]. Also, Ki67, as an expressed antigen in cell cycle phases, has a positive correlation with tumor aggressiveness and proliferative activity, hence poorer prognosis and recurrence in patients of BC [8]. ER, PR, HER2, and Ki67 are evaluated mainly by immunohistochemical (IHC) analysis after biopsy or surgically excised samples. However, this method is not only an invasive and time-consuming procedure, but a single local tumor specimen only sometimes captures the status of these biomarkers in the whole tumor. Therefore, it is urgently needed to establish a non-invasive, easy-to-do, and more representative method [9]. Current limitations of molecular paradigms to classify BC patients could be overcome by the new era of artificial intelligence (AI) algorithms. There are different AI methods, of which AI-powered radiomics and deep learning are the two main approaches. The AI-powered Radiomics method is an umbrella term for the extraction of quantitative and reproducible information from medical images such as ultrasonography (US), computed tomography (CT) scan, and magnetic resonance imaging (MRI), to develop decision support models recognizing complex patterns of images that are not visible by human naked eyes [10]. On the other hand, deep learning (DL), as a convolutional neural network-based algorithm, can also assist clinical decision-making by self-education of complex patterns of diagnostic images, bypassing the manual extraction of imaging features [11].

  Therefore, developing a non-invasive AI-based decision-making system using routine imaging modalities (US, CT, or MRI) before any invasive procedure is necessary to predict the essential molecular biomarkers in BC tissue. Herein, we searched databases and designed this systematic review and meta-analysis of current data on the accuracy of AI-based methods for predicting key molecular markers in BC and evaluating the quality of studies.


## 2. Methods
  This systematic review and meta-analysis is conducted in line with the Preferred Reporting Items for Systematic Review and Meta-Analyses of Diagnostic Test Accuracy Studies (PRISMA-DTA) guidelines [12].


### 2.1. Search strategy
  Two independent observers (YF, and JZ) searched databases (PubMed, EMBASE, and Web of Science) from inception to October 30, 2023. After duplicate removal, YF and JZ independently screened the title and abstract of studies to evaluate the eligibility. Then, the full text of the remaining studies was screened according to the study selection criteria. The reference list of included studies was searched to identify possible eligible studies. Any disagreement during the database search was discussed and resolved by consultation.


### 2.2. Inclusion criteria
  We selected the studies for review if they met the following inclusion criteria based on PICO (Population, Index test, Comparator, and Outcome) elements:


### 2.3. Exclusion criteria
  We excluded the records that met the following exclusion criteria:


### 2.4. Data extraction
  We used standardized forms to review the included studies. Two independent reviewers (YF, and JZ) extracted the following data upon availability: The first author’s name, year of publication, type of study, country, name, and number of patient selection centers, aim of study, patients’ information (patient number, gender distribution, mean age), AI method, type of US, whether contrast agent is used or not. For radiomics studies, we extracted the following data specifically: segmentation method (automatic manual or semi-automatic), segmentation dimension and software, features number, type of extracted features, feature extraction software, feature selection methods, AI modeling algorithm, and whether the radiomics features are combined with other clinical data. Possible disagreements were discussed and resolved through a consensus.


### 2.5. Quality assessment
  We used the “Quality Assessment of Diagnostic Accuracy Studies (QUADAS-2)” tool to evaluate the presence of risk of bias and application concerns in different domains (“patient selection,” “index test,” “reference standard,” and “flow and timing”). Each domain assigned yes, no, or unclear for the assessment of risk of bias and low risk, high risk, or unclear for assessing applicability concerns. Also, we can tailor the QUADAS-2 signaling questions to our research questions to assess the risk of bias [13]. Moreover, we used the “Radiomics Quality Score (RQS)” system to measure the methodological rigor of the studies using the radiomics method. RQS has 16 items with corresponding scores under the following domains: data selection, medical diagnostic images, feature extraction, exploratory analysis, and model construction [14]. Two independent reviewers (JZ, and ZL) assessed the methodological quality and risk of bias using the QUADAS-2 and RQS tools, and disagreements were resolved by discussion and consultation.


### 2.6. Statistical analysis
  We used STATA (version 15; MIDAS module) for the meta-analysis. Sensitivity and specificity with 95% confidence interval (CIs) were calculated for pooling the effect sizes. We plotted the summary receiver operating characteristic curve (SROC) to calculate the area under the curve (AUC). We indicated the pooled effect sizes using the forest plot. A random-effect model was utilized to combine the effect sizes and address the potential heterogeneity of studies. We designed a deeks funnel plot for evaluation of the publication bias. Some studies did not have enough data for meta-analysis. We manually calculated the needed parameters using sensitivity, specificity, and the number of positive and negative classes of each molecular biomarker. The Fagan plot was created to evaluate the clinical utility of the included studies with post-test probability when the pretest probabilities were available.


## 3. Results

### 3.1. Literature search
  We outline the study selection process details using the PRISMA flowchart in Fig 1. Our initial search identified 363 articles, of which 93 records were duplicates. The titles and abstracts of the 270 records were screened, and 235 articles were removed. After reading through the full text of the remaining 35 articles, twelve more records were removed due to the following reasons: 1) four studies were not about AI methods; 2) two studies did not predict the key molecular biomarkers in BC patients; 3) three studies were not in English; 4) three studies did not provide sufficient data for the review process. Then, we included 23 studies with a total number of 11005 patients for the qualitative review process [15–37].

  Of these 23 studies, 15 studies were available for quantitative analysis, and eight studies were not included in the meta-analysis due to inadequate data.


### 3.2. Study characteristics
  We showed the general characteristics of 23 included studies in Table 1, of which 14 were radiomics. The characteristics of the radiomics workflow are summarized in Table 2. Overall, twenty-one (21/23) studies were from China, and the other two were from Romania [33] and Canada [21]. Three studies [15, 25, 33] were prospective (3/23), while the remaining twenty were designed retrospectively (20/23). Regarding AI methods, fourteen studies used radiomics (14/23), six studies used deep learning (6/23), and three studies used machine learning methods (3/23). Three studies [15, 25, 33] retrieved patients from multiple centers (3/23), and the remaining twenty studies were from only one center (20/23). The overall number of patients was 11.005, with a mean age of 52.7 years. However, two studies [20, 23] did not provide the mean age of subjects. One study [36] included men BC; the remaining studies were from the female population. Regarding radiomics studies (14/23), we investigated different steps of radiomics workflow, including segmentation, feature processing, and modeling. Three studies [19, 32, 33] used the automatic/semiautomatic method to delineate the region of interest (ROI). The remaining 19 studies were segmented manually. Only one study [31] did not specify the segmentation method. The open-source ITK-SNAP software was the most commonly used tool for the segmentation process (5/14), and it was utilized in five studies [22, 28, 34, 36, 37]. Two studies used deep learning (2/14) for the segmentation process. Time-intensity curve software, GNU image manipulation program (GIMP), 3D-Slicer, and Darwin Research Platform were used once in the studies. Three studies [25, 31, 35] did not mention the segmentation software. Most studies extracted the shape, first-order, second-order, and wavelet radiomics features regarding the feature processing step. The PyRadiomics package was the most utilized tool to extract the features from ROIs. The extracted features in studies ranged from 86 to 5234. Among these features, the most robust ones should be selected, and different methods are utilized in studies to select them. The Least Absolute Shrinkage and Selection Operator (LASSO) regression was the most commonly used method among studies. Then, the selected features are fitted into a machine learning algorithm to train the data. The logistic regression (LR) algorithm was used in nine studies (9/14) for the model construction.


### 3.3. Quality assessment
  The 23 studies reached a mean RQS score of 12.64 with a minimum of 6 and a maximum of 19 out of 36 possible points. Table 1 shows the RQS score of each study in the corresponding column. The individual ratings for each RQS item and each study are provided in S1 Table. The following items were evaluated in none of the studies: phantom study, imaging at multiple points, cut-off analyses, potential clinical application, cost-effectiveness analyses, open science, and data.

  Details of the assessment of included studies using QUADAS-2 are shown in S1 Fig and Fig 2 All studies assigned are “unclear” regarding the flow and timing item because none of the studies provided the timing of biopsy before US examination. Hao Cui et al. and Jia‑wei Li et al. assigned a “High risk of bias” because the imaging process approach and validation step were not specified.


### 3.4. Predictive performance of AI methods for HER2
  Seventeen studies (17/23) predicted the HER2 status in BC patients, of which ten studies (10/17) had adequate data for quantitative analysis. Studies with insufficient data [15, 17, 18, 23, 27, 30, 37] were excluded from the quantitative analysis. For the prediction of HER2 status, pooled estimates were sensitivity, specificity, and summary receiver operating characteristic (SROC) with a 95% confidence interval. Table 3 shows the categorized extracted data for quantitative analysis. According to the generated forest plot (S2 Fig), the pooled sensitivity and specificity were 0.76 [0.65, 0.84] and 0.78 [0.70, 0.84], indicating a high rate of heterogeneity for both sensitivity (I2 = 67.16 [45.31, 89.01]) and specificity (I2 = 91.41 [87.42, 95.40]). Pooled results from the AUC estimates were 0.84 [0.15, 0.99].

  The funnel plot did not show publication bias (p: 0.46) (S3 Fig). Regarding clinical utility, the Fagan plot (S4 Fig) showed that AI models of HER2 status would increase the post-test probability to 46% from 20% with a PLR of 3 when the pretest was positive and would reduce the post-test probability to 7% with an NLR of 0.31 when the pretest was negative.

  Bo-Yang Zhou et al. [15] designed a prospective study showing that the US-based convolutional neural network (CNN) model has a high accuracy (AUC: 0.89–0.96). This study differs from the other studies by the type of prediction model that distinguishes four classes of molecular biomarkers (HER2, ER, PR, Ki67). For this reason, we did not include this study in the meta-analysis.

  Meng Jiang et al. [17] designed a similar study to Bo-Yang Zhou et al. They constructed a deep-learning model of US images that differentiates the four categories of BC (Luminal A, Lumina B, HER2+, and Triple-negative) based on key molecular biomarkers. In two test sets, the model yielded a good accuracy of 80.07% to 97.02% and 87.94% to 98.83%. Compared to the study of Bo-Yang Zhou et al., this study used two test sets with accuracy similar to the mentioned study. The high level of accuracy may be due to the overfitting since both studies are deep-learning models.

  Xianyu Zhang et al. [23] developed a deep learning US model for three-class classification of BC, including HER2, hormone receptor, and triple-negative. The deep learning model achieved an accuracy of 85.6%, with a gold standard of pathological results in the test set. Also, the model’s accuracy was 90% in an external test set. Interestingly, this study and the two previous [15, 17] studies with deep learning models had a high accuracy in test sets.

  Similar to the previous studies, Zilong Xu et al. [30] constructed a deep learning US model. The model yielded an AUC of 0.84 and an accuracy of 80.56% in the validation set for HER2 status prediction.

  Linyong Wu et al. [37] developed a US-radiomics model in patients with breast ductal carcinoma in situ (DCIS) to predict HER2, ER, PR, and Ki67. Since this study did not specify the exact number of positive and negative classes of each biomarker in training and testing sets, we did not include it in the quantitative analysis. Evaluations indicated that the model had an AUC of 0.94 and 0.74 in the training and test set for HER2 status prediction.

  Mengwei Ma et al. [18] fitted the US texture features to different machine learning algorithms. They established different models for different tasks. All machine learning models yielded a similar AUC for differentiating HER2 from other subtypes. However, the Random Forest model performed slightly better, with an AUC of 0.855 in the test set. On the other hand, the logistic regression model outperformed other models to differentiate HER2+ from HER2- with a slightly better AUC of 0.744.

  Taken together, AI models determined the HER2 status in BC patients with moderate to high precision in the quantitative analysis with a pooled sensitivity, specificity, and AUC of 0.76, 0.78, and 0.84, respectively. Deep learning models showed that outperformed the other AI methods for the prediction of HER2 status.


### 3.5. Predictive performance of AI methods for Ki67
  Thirteen studies (13/23) predicted the Ki67 status in BC patients, of which seven studies (7/13) had adequate data for quantitative analysis. Studies with insufficient data were excluded from the quantitative analysis [15, 17, 18, 31, 33, 37].

  For the prediction of Ki67 status, pooled estimates were sensitivity, specificity, and SROC with a 95% confidence interval. Table 3 shows the categorized extracted data for quantitative analysis. According to the generated forest plot (S5 Fig), the pooled sensitivity and specificity were 0.80 [0.67, 0.89] and 0.76 [0.69, 0.81], indicating a high rate of heterogeneity for both sensitivity (I2 = 89.99 [84.49, 95.48]) and specificity (I2 = 62.76 [34.22, 91.30]). Pooled results from the AUC estimates were 0.81 [0.78, 0.84].

  The funnel plot did not show publication bias (p: 0.09) (S6 Fig). Regarding clinical utility, the Fagan plot (S7 Fig) showed that AI models of Ki67 status would increase the post-test probability to 45% from 20% with a PLR of 3 when the pretest was positive and would reduce the post-test probability to 6% with an NLR of 0.26 when the pretest was negative.

  Hao Cui et al. [31] examined the accuracy of a US radiomics model for Ki67 status prediction. Sensitivity and specificity are the two main metrics for evaluating diagnostic tools. This study did not report these two metrics and Ki67 classes in the dataset. However, the regression model achieved an AUC of 0.71.

  In contrast to all other studies, Ioana Bene et al. [33] showed that no texture parameter was statistically significant in the univariate analysis for the Ki67 biomarker prediction in BC patients.

  Also, Mengwei Ma et al. [18] developed different machine-learning models. In contrast to HER2 status prediction, the Naive Bayes (NB) model performed better than other algorithms. For differentiating high Ki67 from low Ki67 expression, the NB model had an AUC of 0.739 in the test set.

  Altogether, AI models determined the Ki67 status in BC patients with moderate to high precision in the quantitative analysis with a pooled sensitivity, specificity, and AUC of 0.80, 0.76, and 0.81, respectively.


### 3.6. Predictive performance of AI methods for ER and PR
  Six studies (6/23) predicted the ER and PR status in BC patients, of which only two studies (2/6) had adequate data [22, 33], which is not enough to pool the effect sizes for quantitative analysis. As mentioned, Bo-Yang Zhou et al. [15] designed a CNN model of US features with high accuracy (AUC: 0.89–0.96) in predicting BC molecular subtypes’ four-classification (HER2, ER, PR, Ki67). Also, Linyong Wu et al. [37] constructed a US-radiomics model to predict HER2, ER, PR, and Ki67 biomarkers. Analysis showed that the model had an AUC of 0.94 and 0.74 in the training and test set. We noted that Meng Jiang et al. [17] constructed a deep-learning model that could differentiate the four categories of BC (Luminal A, Lumina B, HER2+, and Triple-negative) based on key molecular biomarkers such as ER and PR. The model yielded a good accuracy of 80.07% to 97.02% and 87.94% to 98.83% in the two test sets.

  Also, Mengwei Ma et al. [18] developed several machine-learning models. The LR algorithm showed the highest AUC of 0.878 among all machine learning algorithms for differentiating ER+ and ER- patients. Similarly, the LR algorithm outperformed others in differentiating PR+ and PR- patients with an AUC of 0.879.

  We can conclude from the data that AI models of ER and PR status prediction have the potential to be applied in future clinical practice since models showed promising precision for differentiating ER and PR biomarkers in BC patients.


## 4. Discussion
  This systematic review and meta-analysis showed promising diagnostic test accuracy for differentiating key molecular biomarkers of BC patients using AI methods such as radiomics and deep learning. The results of the quantitative analysis demonstrated moderate to high precision in differentiating key biomarkers of BC patients, especially HER2 and Ki67 molecules.

  Data from the current analysis indicated that AI models could identify the status of HER2 and Ki67 biomarkers with an AUC of 84% and 81%, respectively. The current traditional method to determine the status of key molecular biomarkers in BC patients is mainly based on invasive procedures such as biopsy and excision samples of the tumor. Acquisition of tissue sampling using such local invasive methods can only capture a snapshot of the entire tumor since there is an intrinsic heterogeneity inside the tumor [9]. The new era of AI offers novel diagnostic methods for BC patients by exploring the tumor texture using mathematical and embedded algorithms and extracting quantitative distinct features non-invasively. In contrast to conventional methods, AI models not only explore the entire tumor instead of only a single part of the tumor but also do not lead to patient discomfort due to invasive procedures [10, 11].

  This study meta-analysis supports the reliability of US-based AI models in differentiating HER2+ from HER2- with a sensitivity and specificity of 76% and 78%. Also, the analysis showed that US-based AI models could differentiate Ki67+ from Ki67- patients with a sensitivity and specificity of 80% and 76%. Regarding ER and PR markers, we could not pool the effect sizes and determine the accuracy of AI models quantitatively due to a small number of studies with adequate data for analysis. However, individual studies demonstrated promising diagnostic accuracy.

  Breast US is the primary imaging modality to diagnose breast diseases since it is radiation-free, economical, real-time dynamic, tolerable by patients, and convenient for physicians. Meanwhile, the US has a relatively high accuracy for detecting breast diseases with different imaging features such as shape, margin, acoustic enhancement, vascularity, and calcification [38–40]. Thus, we emphasize the role of breast US as a reliable diagnostic test with valuable potential in detecting breast diseases, especially breast tumors, while highlighting the promising value of US to expedite the detection of key molecular biomarkers. Despite the promising findings of the quantitative analysis and the high accuracy of the models, there were some concerns about the methodological quality of the included studies. The QUADAS-2 tool indicated a low risk of bias in the patient selection, index test, and reference standard. However, no study reported the biopsy’s timing since tissue sampling could alter the texture features after the intervention. Also, studies showed no applicability concern for patient selection, index test, and reference standard.

  Regarding radiomics studies, the RQS tool also proposed that the included literature has a moderate quality regarding RQS items. However, some ignored items by the studies deserve more attention. One of them is data and programming code sharing since it will increase the repeatability and producibility of the present data.


### 4.1. Limitations and future prospects
  Although we reviewed the included studies comprehensively, this study encountered some inherent limitations. in this study, we included eligible studies regarding key molecular biomarkers in BC patients to pool the diagnostic effect sizes. However, several studies were short of enough data for quantitative analysis, which restricted us from reporting more reliable results, especially a single diagnostic metric for ER and PR markers. Therefore, we suggest future research provide data as far as possible to assist future meta-analyses in pooling the valuable findings to reach a single valuable finding. Only three studies retrieved the patients from multiple data centers. Since data collection from a single institute may not reflect the characteristics of the entire population, it is recommended to recruit patients from multiple data centers. Most of the included studies collected the data retrospectively. Since retrospective data collection has a high potential to cause bias, we need more prospective studies in the upcoming research. Since the assessment of the risk of bias and the quality of the literature showed some limitations, we are going to offer some recommendations: 1) Specify the selection criteria, study type, and patient characteristics; 2) Show the data acquisition, image processing, and validation process details; 3) apply the same reference standard to all patients as far as possible.


## 5. Conclusion
  This meta-analysis indicated that AI models (radiomics, deep learning, machine learning) have a promising accuracy for predicting the status of key molecular biomarkers (HER2, Ki67, PR, ER) in patients with breast cancer. We performed the quantitative analysis for HER2 and Ki67 biomarkers which yielded a moderate to high accuracy. However, studies did not provide adequate data for meta-analysis of ER and PR prediction accuracy of developed models. The overall quality of studies, according to the QUADAS-2 and RQS tools, was acceptable. Considering the different US operators and machines, we suggest establishing standardized international protocols for performing ultrasound examinations, conducting interobserver agreement studies, and using standardized reporting systems. In future research in this field, we also need the studies to report the results thoroughly. Also, we suggest more prospective studies from different centers.


## Supporting information