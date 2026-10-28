# Deep learning analysis of contrast-enhanced spectral mammography to determine histoprognostic factors of malignant breast tumours


## Objective
  To evaluate if a deep learning model can be used to characterise breast cancers on contrast-enhanced spectral mammography (CESM).


## Methods
  This retrospective mono-centric study included biopsy-proven invasive cancers with an enhancement on CESM. CESM images include low-energy images (LE) comparable to digital mammography and dual-energy subtracted images (DES) showing tumour angiogenesis. For each lesion, histologic type, tumour grade, estrogen receptor (ER) status, progesterone receptor (PR) status, HER-2 status, Ki-67 proliferation index, and the size of the invasive tumour were retrieved. The deep learning model used was a CheXNet-based model fine-tuned on CESM dataset. The area under the curve (AUC) of the receiver operating characteristic (ROC) curve was calculated for the different models: images by images and then by majority voting combining all the incidences for one tumour.


## Results
  In total, 447 invasive breast cancers detected on CESM with pathological evidence, in 389 patients, which represented 2460 images analysed, were included. Concerning the ER, the deep learning model on the DES images had an AUC of 0.83 with the image-by-image analysis and of 0.85 for the majority voting. For the triple-negative analysis, a high AUC was observable for all models, in particularity for the model on LE images with an AUC of 0.90 for the image-by-image analysis and 0.91 for the majority voting. The AUC for the other histoprognostic factors was lower.


## Conclusion
  Deep learning analysis on CESM has the potential to determine histoprognostic tumours makers, notably estrogen receptor status, and triple-negative receptor status.


## Key Points
  • A deep learning model developed for chest radiography was adapted by fine-tuning to be used on contrast-enhanced spectral mammography.

  • The adapted models allowed to determine for invasive breast cancers the status of estrogen receptors and triple-negative receptors.

  • Such models applied to contrast-enhanced spectral mammography could provide rapid prognostic and predictive information.


## Supplementary Information
  The online version contains supplementary material available at 10.1007/s00330-022-08538-4.


## Introduction
  Worldwide, breast cancer accounts for 11.6% of cancers of all genders and ages. 2.08 million new cases and 626,679 deaths are estimated in 2018.

  Contrast-enhanced spectral mammography (CESM), also called contrast-enhanced dual-energy mammography (CEDM), is an emerging technique used to evaluate neovascularity of a breast lesion, usually associated with malignancy [1], by using an iodine-based contrast intravenous agent.

  In this dual-energy breast imaging, a low-energy image (LE), comparable to conventional digital mammography (full-field digital mammography – FFDM) [2], is acquired and a recombined image (dual-energy subtracted DES) is obtained by subtracting both high- and low-energy images. The iodinated contrast material better absorbs high-energy X-photons, thus revealing regions of angiogenesis [3].

  CESM has shown its superiority to FFDM in terms of sensitivity (92.7% vs 71.5%) and specificity (67.9% vs 51.8%) to detect primary breast cancers in dense breasts [4]. CESM has also a similar sensitivity and a slightly higher specificity compared to breast magnetic resonance imaging (MRI) which is considered the most sensitive technique for breast cancer detection (up to 100% sensitivity for both, with a specificity of 94% for CESM versus 88% for MRI in the studies) [5–7]. Moreover, compared to bMRI, CESM is more comfortable for the patients (position and faster acquisition time) but also less expensive [8, 9]. CESM is also efficient for the assessment of the extent of disease [10], for the evaluation of tumour response to neoadjuvant chemotherapy [11], for post-therapy monitoring [12], and as a problem-solving tool in association with other examinations [13].

  According to the European Society of Breast Imaging (EUSOBI), CESM is currently recommended in case of bMRI contraindication or if bMRI is not available [14].

  In parallel to the development of CESM, deep learning algorithm which attempts to learn multiple levels of representation of increasing complexity and abstraction [15] is a new powerful wave in all fields of radiology. Deep learning is a sub-domain of the machine learning (which is a sub-domain of artificial intelligence).

  One of the latest examples of its use is in chest radiography, where a deep learning model, called CheXNeXt, can detect 14 clinically important pathologies [16]. On a validation set of 420 images for which the majority vote of 3 cardiothoracic speciality radiologists served as ground truth, the algorithm achieved performance equivalent to the practising radiologists on 10 pathologies, better on 1 pathology, and worse on 3 pathologies [16].

  Concerning mammography, an international study has already shown that a deep learning model could be used successfully for the screening of primary breast cancers on FFDM. A combination of human and machine results had a performance equivalent to that of the traditional double-reading process but reduces the workload of the second reader by 88% [17]. More works are however needed for use in clinical practice [18].

  As CESM is a recent technique, the contribution of deep learning to its interpretation has, to our knowledge, not been studied yet. In addition, following the EUSOBI recommendations, CESM is rather used as a second line after FFDM screening in place of bMRI.

  Thus, rather than differentiating between benign and malignant in primary screening, CESM could be used to determine prognostic factors (as a histologic grade, Ki67 proliferation index, cell receptors) in case of cancer to adapt the treatment, as a “deep-radiomics” tool [19]. Most prognostic factors are determined histologically. However, it is possible that the histological phenotype can also be identified in X-ray imaging [20], notably through deep learning analysis.

  However, as CESM is a new technique, available data is still scarce. In such a situation, it is possible to use transfer learning with fine-tuning to adapt a deep learning model, learned on a large dataset (e.g., more than 100,000 images) to a new task with fewer images (e.g., less than 1000 images). Transfer learning from CheXNeXt has already been used on FFDM to detect malignant lesions, with the best accuracy of 90.38% [21]. More recently, transfer learning from CheXNeXt has been used to detect COVID-19 infection (COVID-CXNet) with an accuracy of 94.20% [22].

  The aim of this study was to evaluate if a deep learning model can be used to characterise breast malignant lesions on CESM.


## Materials and methods

### Data set
  This was a retrospective mono-centric study (Henri Becquerel Cancer Center, Rouen Normandy, France) approved by the local ethics committee. Patients were informed that their anonymised images could be used for research and gave their consent. Indications for CESM in our institution were the assessment of the extent of invasive disease (all invasive cancers, excluding in situ cancers), the evaluation of tumour response to neoadjuvant chemotherapy, post-therapy monitoring, and as a problem-solving tool. CESM was performed also in case of contraindications to performing bMRI or if bMRI was not available.

  All CESM images performed between August 2017 and January 2019 were retrieved. Only biopsy-proven invasive cancers with an enhancement on CESM were included. CESM with benign lesions or borderline lesions or non-enhanced malignant lesions were not included. The exclusion criteria were as follows: chemotherapy prior to CESM, lack of histological data, the presence of artefacts (no possible visual analysis), a non-contributory examination (a lesion with very low enhancement, or a masking background enhancement making reliable segmentation of the lesion impossible) (Fig. 1).Fig. 1Flowchart of the final analysis cohort. *Non-contributory examinations (artefacts, insufficient image quality, lesions with very low enhancement, or a limited field of view of CESM)

  For each lesion, its size (maximum diameter) was recorded. The breast density was evaluated according to the BI-RADS lexicon and the background parenchymal enhancement was scaled from 0 to 3 (0 = no enhancement, 1 = minimal enhancement, 2 = moderate enhancement, and 3 = marked enhancement). The type of enhancement (mass or non-mass enhancement) and the biopsy markers were retrieved.

  In the case of multi-focal disease, the lesion with the maximum diameter was selected and the other lesions could also be selected if they were well separated with clear limits in at least one incidence.


### Histopathology
  The histological characteristics were based on analysis of the surgical specimen or percutaneous biopsy if the definitive histologic analysis was not available or if the patient had received neoadjuvant chemotherapy.

  For each lesion, histological type, Nottingham histological score (histologic grade), estrogen receptor (ER) status, progesterone receptor (PR) status, HER-2 status, Ki-67 proliferation index, and the size of the invasive tumour were retrieved.

  According to current guidelines in France, the status was considered positive when the hormonal receptors (ER and PR) had a value ≥ 10% [23]. According to the GEFPICS recommendation, HER2 was considered positive if IHC results are 3 + or 2 + amplified on ISH (in situ hybridization) [24]. Similarly, the Ki 67 was considered high if it was ≥ 20% [25]. Triple-negative status, a known poor prognostic factor [26], was considered for a combination of ER-negative, PR-negative, and HER2-negative.


### CESM image acquisition
  CESM was performed on mammography system (Angiologic Stephanix, Hologic®) using an automated single-shot intravenous injection of iodinated contrast-agent (Iomeron 350 mg/mL, Bracco®) with the dose of 1.5 mL/kg body weight with a flow rate of 3 mL/s followed by a saline flush, after eliminating contraindications. CESM image protocol acquisition is described in supplemental data.


### Image pre-processing
  Patient images were extracted from the PACS (Picture Archiving and Communication System) and anonymised. Manual segmentation of the images was performed by a radiologist using an in-house plugin for the ImageJ software [27]. All available breast incidences were considered. In the case of a visible lesion, the regions of interest (ROI) of the lesions were segmented as the smallest rectangular ROI encompassing the entire lesion [28] on the DES images, the subtracted images corresponding to the vascularisation. The segmented ROI was then propagated on the low-energy images, corresponding to an image similar to FFDM. Images were normalised to an 8bit (0–255) images. Images were then cropped from a 2560 × 3328 array to 1024 × 1024 array with the ROI lesion at the centre. In the case of a ROI lesion larger than 1024 in at least one axis (e.g., in case of large breast masses), the ROI lesion was proportionally resized to a 1024 × 1024 array. Image augmentation is utilised in order to prevent over-fitting by using orthogonal (90°, 180°, and 270°) rotations. Images were down-sized to 320 × 320 array to prevent resource exhaustion and decrease GPU RAM usage.


### Deep learning analysis
  Dataset was separated randomly on training (2 × 787 images, 64%), validation (2 × 195 images, 16%), and testing (2 × 248 images, 20%) datasets. Images of one patient could only be in one of these datasets, even if multiple lesions were segmented. Frequencies of the different issues were equalised between the datasets.

  The deep learning model used was a CheXNet-based model [29], fine-tuned on CESM dataset. CheXNet is based on a densely connected convolutional network with 121 layers (DenseNet-121 [30]) that takes a chest X-ray image as input and outputs the probability of a pathology. The CheXNet model was trained on a dataset containing 112,120 frontal-view chest X-ray images individually labelled with up to 14 different thoracics [29]. This model, specialised in the analysis of thoracic radiographs, can be adapted by fine-tuning, a partial relearning on a new database, in order to analyse new pathologies, such as COVID, but also other examinations, notably mammography [21, 22]. For the fine-tuning, similar to the one performed in [22], Adam optimiser was used with a learning rate of 0.0001 and 10 epochs. A fully connected layer followed by a dropout layer with a 0.2 dropping rate to prevent overfitting was used. The architecture of the model and fine-tuning performed is presented in Fig. 2.Fig. 2Architecture of the deep learning model used based on the CheXNet model, himself based on a DenseNet-121 architecture. FC is fully connected layers

  Three models were trained. The first one on the DES images only, the second one on the LE images only, and the third one on both DES and LE images. Images were analysed independently of the incidence. A majority voting, combining all the incidences for one tumour, was also performed for the three models. The learning of the models was done using python 2.7.17, tensorflow 2.4.1, and keras 2.4.3.


### Statistical analysis
  The receiver operating characteristic (ROC) curve and area under (AUC) of the ROC curve were calculated to assess the ability of the CNN to determine tumour grade (1 and 2 vs. 3), hormone receptor status (ER positive vs. ER negative, PR positive vs. PR negative), Her2 (Her2 positive vs. Her2 negative), and Ki 67 (high or not), and triple negative vs. other.

  The model was evaluated image by the image on DES and LE images separately, and then for all images simultaneously. Then results were calculated by majority voting (including all the incidences for one tumour) on the DES, LE images, and for the combination of LE and DES images.

  We computed overall classification accuracy, as well as sensitivity, specificity, from the results image by image on DES and LE images separately, and then for all images simultaneously.

  Statistical analysis was performed with python 2.7.17.


## Results

### Patient population and lesion characteristics
  A total of 447 malignant lesions in 389 patients (mean age, 61.7 ± 12.6 years; age range, 27–91) were detected on CESM with pathological evidence, which ultimately represents 2460 images analysed.

  Patient demographics and imaging characteristics are provided in Table 1. The median size of enhancing lesions was 28.3 mm ± 23.0 (range 5.0–130.0). A description of the types of lesions and their histoprognostic factors are given in Table 2.Table 1Patient characteristics No. of patients389No. of lesions447Age *61.7 ± 12.6 (27 – 91)Number of images per lesion (mean)5.5Radiographic appearanceBI-RADS density rating  Fatty (category A)22 (5.6)  Scattered fibroglandular density (category B)281 (72.2)  Heterogeneously dense (category C)78 (20.1)  Extremely dense (category D)8 (2.1)Background parenchymal enhancement  Minimal224 (57.6)  Mild96 (24)  Moderate42 (10.8)  Marked27 (6.9)Type of enhancement  Enhancing masses396 (88.6)  Non-mass enhancement51 (11.4)Number of lesion with biopsy markers35 (7.8)Lesion size (mm) *28.3 ± 23.0 (5.0 -130.0)Unless otherwise specified, data are numbers of lesions with percentages in parentheses*Data are means ± standard deviations with ranges in parenthesesTable 2Histopathologic characteristicsParameterNo. of tumours (n = 447)Size of lesions (mm) *20.6 ± 17.4 (2.0 -105.0)Histologic type according to the WHO classification of tumours—Breast tumours 5th Edition 2019 (37)Invasive breast carcinoma of no special type (invasive ductal carcinoma)343Invasive lobular carcinoma72Mixed invasive ductal and lobular carcinoma7Other carcinoma (n = 25)  Mucinous carcinoma8  Invasive breast carcinoma of no special type associated with mucinous carcinoma4  Invasive breast carcinoma of no special type associated with an encapsulated papillary carcinoma2  Invasive breast carcinoma of no special type associated with invasive micropapillary carcinoma1  Encapsulated papillary carcinoma1  Metaplastic carcinoma4  Invasive micropapillary carcinoma1  Neuroendocrine carcinoma2  Tubular carcinoma1Mucinous carcinoma with invasive micropapillary carcinoma1Estrogen receptor status  Positive (≥ 10%)390 (87.2)  Negative (< 10%)57 (12.8)Progesterone receptor status  Positive (≥ 10%)322 (72.0)  Negative (< 10%)125 (28)HER2 status  Amplified50 (11.2)  Not amplified397 (88.8)Ki67 status   ≥ 20%239 (53.5)   < 20%208 (46.5)Tumour grade  Grade 158 (13.0)  Grade 2267 (59.7)  Grade 3122 (27.3)Triple-negative breast cancer (TNBC)35 (7.8)Unless otherwise specified, data are numbers of lesions with percentages in parentheses*Data are means ± standard deviations with ranges in parentheses

  There were no significant differences between the training, the validation, and the testing sets in terms of histological grade, estrogen receptor (ER) status, progesterone receptor (PR) status, HER-2 status, Ki-67 proliferation index, or triple negative.


### Deep learning analysis
  Figures 3 and 4 illustrate the performance of the CNN algorithm area under the receiver operating characteristic curve for the analysis image by image and by majority voting respectively.Fig. 3Diagnostic performance of the deep learning system image by image on DES (a) and LE images (b) separately, and then for all images simultaneously (c)Fig. 4Diagnostic performance of the deep learning system by majority vote on DES (a) and LE (b) images separately, and then for all images simultaneously (c)

  Concerning the ER, the deep learning model on the DES images had an AUC of 0.83 with the image-by-image analysis and of 0.85 for the majority voting. These results were slightly higher than those obtained for the LE images (0.73 and 0.72, respectively) but comparable to those obtained when DES and LE images were combined (0.85 and 0.86, respectively). For the triple-negative analysis, a high AUC was observable for all models, in particularity for the model on LE images with an AUC of 0.90 for the image-by-image analysis and 0.91 for the majority voting.

  The AUCs for the other histoprognostic factors were lower; for example, when DES and LE images were combined, AUC = 0.65 for the diagnosis of the HER2 status or AUC = 0.62 to predict grade 3.

  The sensitivity, specificity, and accuracy of the deep learning model image by the image on DES and LE images separately, and then for all images simultaneously for each category are provided in Table 3.Table 3Performance of the deep learning model image by image on DES and LE images separately, and then for all images simultaneously for each categoryDES ImagesLE ImagesDES and LE ImagesSensitivitySpecificityAccuracySensitivitySpecificityAccuracySensitivitySpecificityAccuracyER81.8681.8281.8574.8872.7374.680.2380.380.24PR60.9462.7161.3556.2557.1456.4559.6459.8259.68HER256.6760.5560.0856.6761.4760.896054.8255.44Ki 6758.9661.460.0855.9757.0256.4555.9756.1456.05GRADE60.3462.1161.6958.626059.6860.3460.2660.28TNBC72.2281.380.6583.3384.7884.6872.2273.2673.19All data are in percentages (%)

  The best results were observed with the determination of the ER status on DES images with a sensitivity, a specificity, and an accuracy of 82% and with the determination of the triple-negative status on LE images with a sensitivity of 83%, a specificity of 85%, and an accuracy of 85%.

  To illustrate a decision taken by the deep learning model, a representation of a gradCAM (a heat map showing the part of the image where the algorithm is focused for its decision) of the models for a triple-negative cancer is shown in Fig. 5.Fig. 5Heat map with grad cam algorithm showing the regions where the decision for triple-negative status is taken by the deep learning model for DES and LE images of a same lesion


## Discussion
  The aim of this retrospective study was to define if a deep learning model based on transfer learning can be used to characterise breast malignant lesions on CESM. Our results demonstrated a good performance to characterise estrogen receptor (ER) status and to differentiate triple-negative breast cancers (TNBC).

  The characterisation of tumours is essential to define the best management and choose the different therapeutics. The analysis by deep learning allows the study of an entire tumour and of each detected lesion quickly and non-invasively. This model could serve as a virtual biopsy and could also help radiologists target their biopsy to areas of interest.

  Previous studies on CESM and machine learning have focused on the development of CAD systems to classify breast masses as benign or malignant.

  Patel et al. used a machine learning algorithm based on SVM (support vector machine) classification and added radiomics analysis to show the diagnostic performance of computer-assisted contrast-enhanced spectral mammography (CAD-CESM) on 50 lesions described on the CESM. Their results showed that this CAD-CESM can provide an overall diagnostic accuracy of 90% in predicting the malignancy of a lesion and that it could help radiologists’ interpretation, mainly by reducing the number of false-positive results [31]. Massafra et al. evaluated on 58 ROIs from 53 patients a CAD based on a radiomics analysis with 464 features of different kinds (such as points and corners of interest, textural and statistical features) on native or filtered images. After a principal component analysis (PCA), dimension reduction technique, and the use of random forest classifier, they obtained a model able to predict benign/malignant ROIs with median values for sensitivity and specificity of 88.37% and 100% [32]. These results improved on previous results obtained by the same team with median values of sensitivity and specificity of 87.5% and 91.7%, respectively [33].

  In the study by Danala et al., they developed a CAD scheme of CESM images to classify breast masses. They demonstrated that CESM images could improve the accuracy of mass segmentation of a CAD and classify 111 lesions as benign or malignant using perceptron-based multilayer machine learning. Their results also showed that LE and DES images contain valuable additional information and that the combination of these two types of images significantly improved CAD lesion classification performance [34].

  Perek et al. [35] compared two CNN methods, fine-tuning a pre-trained network and fully training a convolutional neural network, for the classification of CESM breast mass as benign or malignant on 129 randomly selected breast lesions and obtained the following results using a multimodal network with 100% sensitivity and 66% specificity.

  Gao et al. [36] evaluated a deep-CNN using 49 CESM cases employed to extract novel features from LE, recombined or “virtual” recombined images to classify the cases as benign vs. cancer. They proved that the model performance can achieve an accuracy of 0.85 and an AUC of 0.84 using LE imaging, and they have shown to improve the accuracy of 0.89 with an AUC of 0.91 using both LE and DES imaging.

  There are no studies to date on the potential of deep learning to characterise malignant lesions. In addition, previous studies on machine learning and CESM were conducted on a smaller number of cases.

  In a study by La Forgia et al. performed on 68 lesions from 52 patients, seven features (histogram and texture parameters) were extracted from each original ROI from both LE and DES images or 14 features per ROI. With a multivariate linear discriminant analysis, they found that for the tasks to differentiate ER status, PR status, Ki67, grade, TNBC status, and HER status, AUC values of 83.79%, 75.50%, 84.80%, 79.85%, 76.80%, and 90.89%, respectively should be achieved.

  In another study performed by Marino et al., which also deals with CESM and artificial intelligence, the authors used another area of machine learning and radiomics analysis with the extraction of tumour features followed by a machine learning classification, to characterise breast lesions. They showed in their retrospective study of 103 breast cancers that radiomics analysis with CESM was able to differentiate invasive tumours from non-invasive and define their hormone receptor status and tumour grade [37].

  We found comparable results for the determination of ER status but not for the PR status and the grade. However, we found that our deep learning model was able to determine the TNBC status. For TNBC, the results observed can be related to the characteristics of these tumours that present a specific appearance in imaging (an irregular non-calcified mass with ill-defined or spiculated margins on mammography, and a hypoechoic or complex mass with an irregular shape and non-circumscribed margins on ultrasound [38] and a rim enhancement on DCE-MRI for example) [39]. Interestingly, in accordance with the radiological semiology described, the models developed in this study seem to take their decision on the ring for the DES images and on the ill-defined or spiculated margins for the LE images in case showed in Fig. 5. The quick detection before any surgery of TNBC is very interesting for this type of aggressive tumour for which patients can benefit from neoadjuvant chemotherapy in some cases. However, the results obtained with the LE images, comparable to the FFDM, and with the DES images were globally similar without any obvious improvement of the results by combining them with the majority voting system. This could call into question the interest of injection for this indication, although tumour localisation and segmentation are greatly facilitated by injection.

  Our study has several limitations. First, it is a retrospective study mono-centric with a relatively small number of patients for deep learning analysis although we used data augmentation and transfer learning with fine-tuning to overcome this limitation.

  In our study, all the examinations were performed on the same mammography machine, which made it possible to obtain standardised images, but the results may not be applicable in other centres using other equipment.

  Finally, we did not take into account lesions that do not enhancement on the CESM and are only visible on the low-energy image, which may induce a selection bias in our study.


## Conclusion
  In conclusion, our results demonstrate that deep learning analysis on CESM has the potential to determine histoprognostic tumour makers, notably estrogen receptor status and triple-negative receptor status, which could provide rapid prognostic and predictive information.


## Supplementary Information

### N/A
  Below is the link to the electronic supplementary material.Supplementary file1 (DOC 983 KB)