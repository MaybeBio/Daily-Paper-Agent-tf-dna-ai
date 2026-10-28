# Deep-Learning to Predict BRCA Mutation and Survival from Digital H&E Slides of Epithelial Ovarian Cancer


## Abstract
  BRCA 1/2 genes mutation status can already determine the therapeutic algorithm of high grade serous ovarian cancer patients. Nevertheless, its assessment is not sufficient to identify all patients with genomic instability, since BRCA 1/2 mutations are only the most well-known mechanisms of homologous recombination deficiency (HR-d) pathway, and patients displaying HR-d behave similarly to BRCA mutated patients. HRd assessment can be challenging and is progressively overcoming BRCA testing not only for prognostic information but more importantly for drugs prescriptions. However, HR testing is not already integrated in clinical practice, it is quite expensive and it is not refundable in many countries. Selecting patients who are more likely to benefit from this assessment (BRCA 1/2 WT patients) at an early stage of the diagnostic process, would allow an optimization of genomic profiling resources. In this study, we sought to explore whether somatic BRCA1/2 genes status can be predicted using computational pathology from standard hematoxylin and eosin histology. In detail, we adopted a publicly available, deep-learning-based weakly supervised method that uses attention-based learning to automatically identify sub regions of high diagnostic value to accurately classify the whole slide (CLAM). The same model was also tested for progression free survival (PFS) prediction. The model was tested on a cohort of 664 (training set: n = 464, testing set: n = 132) ovarian cancer patients, of whom 233 (35.1%) had a somatic BRCA 1/2 mutation. An area under the curve of 0.7 and 0.55 was achieved in the training and testing set respectively. The model was then further refined by manually identifying areas of interest in half of the cases. 198 images were used for training (126/72) and 87 images for validation (55/32). The model reached a zero classification error on the training set, but the performance was 0.59 in terms of validation ROC AUC, with a 0.57 validation accuracy. Finally, when applied to predict PFS, the model achieved an AUC of 0.71, with a negative predictive value of 0.69, and a positive predictive value of 0.75. Based on these analyses, we have planned further steps of development such as proving a reference classification performance, exploring the hyperparameters space for training optimization, eventually tweaking the learning algorithms and the neural networks architecture for better suiting this specific task. These actions may allow the model to improve performances for all the considered outcomes.


## 1. Introduction
  Epithelial ovarian cancer (EOC) is strongly dominated by copy number changes without a focal gene driving mutation. Approximately half of cases exhibits defective DNA repair via homologous recombination (HR), frequently caused by inactivation of the breast cancer susceptibility (BRCA) genes (overall up to 30%) [1,2,3,4].

  Defective HR (HR-d) reflects underlying genomic instability, which has significant therapeutic implications in EOC. It is in fact associated to a striking platinum sensitivity and can be targeted by poly-ADP ribose polymerase inhibitors (PARPi).

  Although HR assessment is progressively overcoming BRCA testing, it is not yet integrated in clinical practice and can be challenging and expensive, being also still not refundable in many countries. Selecting patients who are more likely to benefit from it at an early stage of the diagnostic process (somatic BRCA 1/2 wild type [WT] patients), could allow an optimization of genomic profiling resources.

  Histologic phenotypes have been recognized to somehow reflect genetic alterations in cancer tissues [5,6,7,8,9,10]. BRCA-mutated (BRCA-mut) EOC were found to have more frequent Solid, pseudo-Endometrioid, and Transitional cell carcinoma-like morphology (SET features) and higher mitotic indexes compared to BRCA WT EOC [11].

  Since hematoxylin and eosin (H&E)-stained tissue slides are ubiquitously available for cancer patients, predicting mutations from tissue slides could be a time- and cost-effective method to characterize patients and address them to genomic profile.

  Advances in digital pathology and artificial intelligence have presented the potential to analyze gigapixel whole-slide images (WSI), providing information on tissue microenvironment, integrative image-omic, resistence to treatments but also somatic genomic status straight away [12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33].

  WSI is a complex domain with several unique challenges, that requires different deep-learning-based computational pathology approaches such as manual annotation of gigapixel WSIs in fully supervised settings or large datasets with slide-level labels in weakly supervised ones.

  The delineation of a pixel, patch or region-of-interest (ROI)-level annotations has produced promising results even if it cannot be directly generalized, and if it may suffer from noisy training labels and reduced reproducibility on data from different sources and imaging devices [34,35,36,37].

  On the other hand, weakly supervised approaches demonstrated an exceptional clinical-grade performance [38] but require thousands of WSIs to achieve performance comparable to fully supervised and ROI-level classifiers and may not be suitable for multi-class subtyping problems.

  A recent paper proposed a clustering-constrained-attention multiple-instance learning (CLAM) as a high-throughput deep-learning framework that aims to address the key challenges outlined above [39].

  The authors demonstrated that such approach can be used to localize well-known morphological features on WSIs without the need for spatial labels, overperforming standard weakly supervised classification algorithms and resulting adaptable to independent test cohorts, smartphone microscopy and different tissue content.

  In this study, we aimed at identifying somatic BRCA 1/2 mutational status directly from H&E slides using a CLAM-based approach. In particular we planned to evaluate negative and positive predictive values of the CLAM-based model compared to genomic sequencing as the reference standard. As secondary endpoints, we aimed at evaluating CLAM-based model accuracy in prognosis prediction measured as progression free survival (PFS).


## 2. Results
  From November 2016 to November 2020, 1265 consecutive patients underwent BRCA 1/2 testing in our institution.

  A total of 664 patients was finally analyzed in the current study (see Figure 1). Regarding secondary endpoints, 8 patients were lost at follow-up and 656 patients were therefore lastly included.

  Table 1 shows main clinic-pathological characteristics. Overall, median age of included patients was 61 years old. More than half of the patients had positive family history for cancers (mainly breast). The vast majority of the population had a serous histotype (95.9%), grade 3 (97.1%) and III or IV FIGO stage (92.4%).

  Regarding BRCA 1/2 status, 431 (64.9%) patients resulted WT while 233 (35.1%) mutated, 51.5% of which were BRCA 1 mutated. We have reported specific mutations analyzed in the Table 1; with a majority of frameshift mutations of 40.4%.

  All mutated patients were addressed to genetic counselling and 86.6% were tested for germline BRCA 1/2 pathogenetic variants. A third (38.2%) had a germline alteration.

  Table 2 shows treatment and oncological outcome data. Regarding therapeutic choices, 54.5% of these patients underwent neoadjuvant chemotherapy with a median number of cycles prior to interval debulking surgery of 4, after a laparoscopic assessment. Three hundred and forty out of 644 (52.8%) recurred, but only 27.7% died.

  The whole process is represented in Figure 2. The outcome was BRCA 1/2 mutated yes/no, in which VUS were considered as mutated patients.


### 2.1. Phase 0: Reference Standard for BRCA Status Prediction
  A reference classification performance was established according to the classification accuracy and AUC ROC of an expert pathologist, based on available criteria [11]. On the whole 664 slides of the dataset, the reference performance was as follows: accuracy 0.629, specificity 0.879, sensitivity 0.167, negative predictive value 0.661, positive predictive value 0.428 (TN: 379, TP: 39, FN: 194, FP: 52).


### 2.2. Phase 1: WSI for Somatic BRCA Status Prediction
  The dataset was randomly split into into a development set, consisting of a training set and internal validation set, and an hold-out testing. The proportion between development and testing set set was 80% to 20%. Thus, we used 464 images for training (244/220), 132 images for validation (86/46), and 68 images were hold out for testing (44/24).

  The performance on the training set was 0.7 in terms of AUC, but on the testing set the AUC was 0.55. In detail, for training set class zero (BRCA wild type) the model correctly identified 153 out of 244 images, while for class one (BRCA mutated) 139 out of 220. In the testing set class zero, the model correctly identified 49 out of 86, while in class one 24 out of 46.


### 2.3. Phase 2: ROI on WSI for Somatic BRCA Status Prediction
  For this analysis, a subset of images were used, because of the time consuming process of manual ROI delineation. The process of dataset splitting was the same as before, only with slightly different proportions, so that we used 198 images for training (126/72), 87 images for validation (55/32), and only three images were hold out for testing (2/1), merely to create heatmaps of activation regions on unseen images.

  The outcome was BRCA 1/2 mutated yes or no, and VUS were considered as mutated patients.

  At the end of training, the model reached a zero classification error on the training set, but the performance of the predictive model on the validation set was 0.59 AUC ROC, with 0.57 validation accuracy (see Figure 3 and Figure 4). The model correctly classified 39 out of 55 class zero (BRCA wild type) images, and 11 out of 32 class one (BRCA mutated) images on the validation set. All of the three held out images were correctly classified.

  In particular, the model assigned to the BRCA 1/2 mutated held out image a probability of 98% of mutation, while a probability of 38% and <1% were assigned to the other two held out images (both WT), respectively.


### 2.4. Phase 3: Exploration of the Hyperparameters Space for Training Optimization
  Given the results obtained in the previous two phases, we looked for chances of performance improvement by exploring the CLAM model hyperparameters space through a grid search. To do so, we let the following hyperparameters vary: patch level between zero and 2; attention branch single or multiple; bag loss function and clustering loss function one between support vector machine or cross entropy; the relative weight of the two loss in the overall loss function between 0.2 and 0.8 with 0.1 steps; the number of highest and lowest attention patches to be fed to the clustering algorithm within the set 4, 8, 16, 32, 64, 100, 500, 1000. The dataset splitting was the same as phase 1. Grid search type was random search with an early stopping criterion on validation loss decreasing. For each patch level, the best five experiments in terms of validation AUC were retained for performance assessment on the testing set. None of these hyperparameters combination led to significant or even relevant BRCA classification performance improvement neither in the validation nor in the testing set.


### 2.5. Phase 4: WSI for Predicting Relapse
  For this analysis, slide resolution was taken to be fixed at the highest available value on the image (called “patch level zero” in CLAM framework). As in the previous steps, the dataset was split into a development set (training and validation) and a testing set. Grid search on hyperparameters was performed on the development set to select the five highest performing models, which were later assessed on the hold-out testing set for predictive performance.

  The combination of parameters led to a grid search on 64 different models for 200 epochs training length with an early stopping criterion of 20 epochs non-decreasing loss for each outcome.

  On a total of 656 images (229 class 0; 427 class 1), 394 images were assigned to training set, 131 images to validation set, 131 images were hold out for testing (46/85). The AUC on the testing set was 0.71 (see Figure 5).


## 3. Discussion
  Molecular profiling in cancer patients has been increasingly important to determine the optimal therapeutic strategy. The combination of the digitization of pathology WSI with deep learning to predict somatic mutations, could be a promising approach to achieve a time- and cost-effective complementary method for personalized treatment.

  When applied on our dataset, the available morphological criteria (SET features) showed disappointing results (accuracy 0.629, negative predictive value 0.661). This suggests that phenotype and genotype may not be strongly related, as previously suggested [11].

  In our phase 1 (high testing and validation errors), we focused on the specific features/patterns within the tissue images that the model recognized to make response predictions. Looking at the activation map (heatmap) of the highest and lowest prediction on the testing set (see Figure 6a–c), we found that the model identified tumor cells in the mutated cases and stroma in the wild type case which could reflect the morphological differences previously described namely solid phenotype and higher mitotic index [11].

  However, given the performances, we hypothesize that the highest attention pattern should be focused on tumor areas on which reported differences might be more evident thus useful for outcome prediction. It was necessary to tweak parameters, starting from optimal tissue identification in the segmentation process.

  Unfortunately, the process of manually delineating ROI by a dedicated pathologist did not improve the overall performances and neither did the exploration of the hyperparameters space for training optimization, even tweaking the learning algorithms and the neural networks architecture for better suiting the task of BRCA 1/2 status identification.

  Several issues and limitations have been encountered during the analysis.

  First, the retrospective nature of the study represents an unavoidable source of selection bias and imaging data inhomogeneity.

  Although we collected only H&E slices of peritoneal tissue and checked for a minimum percentage of tumor cells in all specimens, patients were not divided in subgroups according to the type of surgery performed; thus small biopsies obtained from exploratory laparoscopy might have provided less representative specimens and images of lower quality compared to peritonectomies.

  Second, the absence of an external validation does not allow us to draw any definitive conclusion on the replicability of the model, though the use of H&E slides for cancer diagnosis is spread all over the world. Moreover, we are well aware that there are concerns of between-center variation in imaging results which might significantly impact on the reproducibility of the model results.

  Third, our BRCA 1/2 testing was mainly performed on fresh frozen ovarian cancer tissue. We assumed that all other areas of the disease within the same patient shared the same mutational status but this consideration may not be entirely correct. given the significant EOC heterogeneity.

  Fourth, our patients were only screened for BRCA 1/2: no other genes involved in the HRD pathways were included in the analysis. Therefore, we cannot exclude the presence of mutations in the other genes whose mutational status could correlate with imaging features typical of mutated patients. Moreover, any type of BRCA 1/2 pathogenic variant was labeled as “mutated”. There are not enough data to establish whether different mutations produce different downstream effects but we cannot rule out differences in phenotype. This might have affected our analysis.

  Fifth, the analysis was carried out using open source pipelines such as the CLAM model which are not customized for the purpose of the study. Entirely in-house designed pipelines, tailored on genomic status identification, might improve final results.

  Overall, the model could provide a critical information at the very beginning of the diagnostic process and, if proven effective, tailor further genomic testing (e.g., only BRCA testing or HRD testing) and optimizing genomic testing resources.


### Our Results in the Context of Other Observations
  Preliminary but encouraging results have been published in the last 3 years on computational pathology.

  In 2020, Jang and colleagues showed that APC, KRAS, PIK3CA, SMAD4, and TP53 mutations can be predicted from H&E pathology images using deep learning-based classifiers [40]. The AUCs for ROC curves ranged from 0.693 to 0.809 for frozen WSIs and from 0.645 to 0.783 for the FFPE WSIs.

  Xu et al., developed a deep learning model to accurately classify chromosomal instability status on a cohort of 1010 patients with breast cancer (Training set: n = 858, Test set: n = 152) from The Cancer Genome Atlas achieving, an area under the curve of 0.822 with 81.2% sensitivity and 68.7% specificity in the test set. Patch-level predictions of chromosomal instability status suggested intra-tumor heterogeneity within slides [41].

  Fu et al. in 2020 quantified histopathological patterns across 17,396 H&E stained histopathology slide images from 28 cancer types and successfully correlate these with matched genomic, transcriptomic and survival data [5].

  Moreover, computational histopathology highlighted prognostically relevant areas, such as necrosis or lymphocytic aggregates. The authors underlined the remarkable potential of computer vision in characterizing the molecular basis of tumor histopathology.

  Kiehl et al. developed a deep learning model from routine histological slides and/or clinical data to predict lymph node metastasis in colorectal cancer [42]. The deep learning model achieved an AUROC of 71.0%, the clinical classifier achieved an AUROC of 67.0% and a combination of the two classifiers yielded an improvement to 74.1%.

  Finally, Wang et al. trained a deep convolutional neural network of ResNet on WSIs to predict the gBRCA mutation in breast cancer [43]. One hundred and sixty six images were combined from two different datasets. The model reached in the external validation dataset an AUC of 0.766 (0.763–0.769) at 40× magnification. The authors reported the role of histological grade on the accuracy of the prediction.

  It has also to be acknowledged that new data are emerging regarding the relevance of BRCA status in the upfront surgical treatment. Not only BRCA WT OC patients seems to benefit more that BRCA mutated ones from hyperthermic intraperitoneal chemotherapy performed at primary debulking surgery but even a neoadjuvant chemotherapy approach has been supposed to be less detrimental in patients harboring BRCA mutation [44,45,46]. If these data are confirmed, the turnaround time of BRCA status acquisition will became crucial. Artificial intelligence applied to digital pathology holds much promise in bringing innovative solutions to this possible future clinical unmet need.


## 4. Materials and Methods

### 4.1. Patients and Study Design
  This is an observational study with patients retrospectively enrolled at the Fondazione Policlinico Universitario “Agostino Gemelli” IRCCS of Rome, Italy, from November 2016 to November 2020.

  A weakly supervised deep learning-based model on H&E in EOC patients was set up for BRCA1/2 status prediction.

  The retrospective data on BRCA1/2 testing performed on patients with NGS technique was considered as the reference standard of the computational pathology analysis. H&E slides were prepared by a technician and evaluated by a dedicated pathologist, according to current international indications.

  In a second step, clinical and follow-up data including therapeutic regimens, progression free survival (PFS) and overall survival (OS), were considered as outcomes to be predicted.

  This study was conducted in accordance with the declaration of Helsinki and was approved by the Ethical committee of Fondazione Policlinico Universitario Agostino Gemelli IRCCS (Prot.; 001134″3/21; ID: 3894, 25 March 2021), with the requirement for informed consent. The research was founded by the Italian Ministry of Health providing Institutional Financial Support 5 × 1000 (2020).


### 4.2. Study Population
  Eligible population includes: (i) women affected by EOC, with known somatic BRCA 1/2 mutational profile and (ii) available Formalin-Fixed Paraffin-Embedded peritoneal tissue sample, collected at the time of first diagnosis of EOC with at least 30% of cancer cells.

  For the second step only those patients for whom we had complete follow-up information (minimum follow up 18 months) were included.

  The exclusion criteria were: (i) patients affected by recurrent ovarian cancer; (ii) samples collected after chemotherapy; (iii) patients with extra-ovarian tumors with metastases to ovaries; (iv) patients with history of other malignancies in the past 5 years; (v) patients who received any type of target therapy prior to EOC diagnosis.

  All the enrolled women were required to sign written informed consent.

  Standardized procedures according to previously published workflows were observed to achieve somatic BRCA 1/2 genes mutational status [47,48,49].


### 4.3. Deep Learning Approach (CLAM)
  CLAM is a deep-learning-based weakly supervised method that uses attention-based learning to automatically identify sub regions of high diagnostic value to accurately classify the whole slide, while also enabling the use of instance-level clustering over the representative regions identified to constrain and refine the feature space.

  CLAM is publicly available as a Python package over GitHub (https://github.com/mahmoodlab/CLAM, accessed on 29 August 2022) [50].

  For whole-slide-level learning without annotation, CLAM uses an attention-based pooling function [51] to aggregate patch-level features into slide-level representations for classification. At a high level, during both training and inference, the model examines and ranks all patches in the tissue regions of a WSI, assigning an attention score to each patch, which informs its contribution or importance to the collective slide-level representation for a specific class.

  This interpretation of the attention score is reflected in the slide-level aggregation rule of attention-based pooling, which computes the slide-level representation as the average of all patches in the slide weighted by their respective attention score. Unlike the standard MIL algorithm [45,46], which was designed and widely used for weakly supervised positive/negative binary classification (for example, cancer versus normal), CLAM is designed to solve generic multi-class classification problems. A CLAM model has N parallel attention branches that together calculate N unique slide-level representations, where each representation is determined from a different set of highly attended regions in the image viewed by the network as strong positive evidence for the one of N classes in a multi-class diagnostic task. Each class-specific slide representation is then examined by a classification layer to obtain the final probability score predictions for the whole slide.

  The slide-level ground-truth label and the attention scores predicted by the network can be used to generate pseudo labels for both highly and weakly attended patches as a technique to increase the supervisory signals for learning a separable patch-level feature space. During training, the network learns from an additional supervised learning task of separating the most- and least-attended patches of each class into distinct clusters. In addition, it is possible to incorporate domain knowledge into the instance-level clustering to add further supervision.

  The pipeline provided by Lu et al., first automatically segments the tissue region of each slide and divides it into many smaller patches, so that they can serve as direct inputs to a CNN. Next, using a CNN for feature extraction, the tool converts all tissue patches into sets of low-dimensional feature embeddings. Following this feature extraction, both training and inference can occur in the low-dimensional feature space instead of the high-dimensional pixel space. The volume of the data space is decreased nearly 200-fold, drastically reducing the subsequent computation required to train supervised deep-learning models.


### 4.4. WSI Processing

#### 4.4.1. Scanning
  Clinical slides were reviewed with the supervision of a dedicated pathologist and selected hematoxylin and eosin-stained slides containing tumor were scanned using the C13220-31 NanoZoomer S360 (Hamamatsu, Japan).

  Each slide was scanned using a 40× objective lens (scanning resolution 0.23 µM/pixel) of the NanoZoomer and the slide code details, the scanning area and the number of focus points for each slide were determined by the user. The number of focal points was approximately 15 focus points per slide.

  Place the glass slides in the cassettes and set them in the holder of the machine, each slide was automatically handled and scanned. The approximate time taken to scan the image of the whole slide per case was up to 1 min.

  Scanned images in their proprietary NDP Image (NDPI) file format were checked for the whole and details of the tissues using the NDP.view2 image viewing software for NanoZoomer on a desktop computer with a high-definition resolution screen (1920 × 1080 pixels). NDPI stores an image pyramid in TIFF directory entries.

  Images and data were stored and exported to an external storage device.


#### 4.4.2. Segmentation
  The first step is an automated segmentation of the tissue regions. The first step focuses on segmenting the tissue and excluding any holes. The segmentation of specific slides can be adjusted by tuning the individual parameters. The pipeline input is digitized whole slide image data in well-known standard formats (.svs, .ndpi, .tiff etc.). The WSI is read into memory at a down sampled resolution, converted from RGB to the HSV color space. A binary mask for the tissue regions (foreground) is computed based on thresholding the saturation channel of the image after median blurring to smooth the edges and is followed by additional morphological closing to fill small gaps and holes [52]. The approximate contours of the detected foreground objects are then filtered based on an area threshold and stored for downstream processing while the segmentation mask for each slide is made available for optional visual inspection. A human-readable text-file is also automatically generated, which includes the list of files processed along with editable fields containing the set of key segmentation parameters used.


#### 4.4.3. Patching
  After segmentation, the background is removed from images for each slide and the remaining pixels are grouped into a grid of smaller images (256 × 256 patches) from within the segmented foreground contours at the user-specified magnification and stores stacks of image patches along with their coordinates and the slide metadata using the Hierarchical Data Format version 5 (HDF5).

  This is not a computationally intensive process and is dependent on resolution level.

  The number of patches extracted from each slide can range from hundreds (biopsy slide patched at ×20 magnification) to hundreds of thousands (large resection slide patched at ×40 magnification). Output is a representation of images through patches in a high dimensional feature (HDF) space generated by a pre-trained convolutional neural network.


#### 4.4.4. Feature Extraction
  Following patching, we used the pre-trained ResNet50 model [53] already embedded in CLAM to compute a low-dimensional feature representation for each image patch of each slide. Features extraction from patches is a computationally intensive step. Requiring about one minute per whole slide image on NVIDIA Quadro RTX 5000.


#### 4.4.5. Attention Branch
  Each patch feature vector then enters an attention network which is trained to recognize patterns often associated with a particular Slide-level label (over-simplification).

  At the end of training, the overall model should be able to identify characteristic regions of activation and make classification at the whole slide image level.


### 4.5. Statistical Analysis
  The sample size available for the analysis consisted of 664 histological images. For computational reasons, the pipeline was first applied to about 30% of available data (171 images) and then incremented to 298 in order to measure the performance gain due to increased sample size.

  The dataset was split into a training and validation set, respectively 80% and 20% of the considered number of samples.

  Classification performance of the predictive model was monitored during training with ROC AUC, negative and positive predictive value on the validation set. The final model was then applied to held out images to generate activation maps on unseen BRCA mutated images. The model was trained for 300 epochs on a NVDIA Quadro RTX 5000. All statistical analysis was performed in Python version 3.7.4.


## 5. Conclusions
  Our results confirm that models applied to H&E slides cannot yet match the performance level of the gold standards thus their use in current clinical practice cannot be advocated. Nevertheless, its potentiality as a screening tool for personalization and optimization of genomic testing warrants further investigation.

  From a clinical point of view, the information obtained directly from frozen section H&E slides, may give clinicians a crucial information at an early stage of the therapeutic decision making process that could be integrated with already validated clinical scores or multiomics translational approaches [54,55,56].

  For all these reasons, we believe that further developments are well worth carrying out. We have already planned to enlarge the dataset collecting cases from December 2020 to August 2022. Moreover, we are working on improving data input for CLAM analysis by using a recently released segmentation model code (https://github.com/MSKCC-Computational-Pathology/DMMN-ovary, accessed on 29 August 2022) [57]. On the other hand, we are exploring in collaboration with other groups, new approaches such as the development of a persistent homology-based model on the same dataset [58].

  Future studies must include data across multiple centers not used in the model training to demonstrate high accuracy and reproducibility. A deeper involvement of pathologists should be pursued in order to achieve the finest tuning possible according to well recognized features.


## Acknowledgments
  We would like to acknowledge the contribution of Nikon for the free trial of Nanozoomer S360, G-STeP Immunohistochemistry, Data collection and Radiomics core facilities (https://gstep.policlinicogemelli.it/#/, accessed on 29 August 2022).