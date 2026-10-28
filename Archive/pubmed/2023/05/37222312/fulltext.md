# Relationship between body composition and PBRM1 mutations in clear cell renal cell carcinoma: a propensity score matching analysis


## OBJECTIVE:
  This study aimed to examine the relationship between body muscle and adipose tissue composition in clear cell renal cell carcinoma patients with PBRM1 gene mutation.


## METHODS:
  Cancer Genome Atlas Kidney clear cell renal cell carcinoma and Clinical Proteomic Tumor Analysis Consortium clear cell renal cell carcinoma collections were retrieved from the Cancer Imaging Archive. A total of 291 clear cell renal cell carcinoma patients were included in the study retrospectively. Patients’ characteristics were obtained from Cancer Imaging Archive. Body composition was assessed with abdominal computed tomography using the automated artificial intelligence software (AID-U™, iAID Inc., Seoul, Korea). Body composition parameters of the patients were calculated. To investigate the net effect of body composition, the propensity score matching procedure was applied over age, gender, and T-stage parameters.


## RESULTS:
  Of the patients, 184 were males and 107 were females. Mutations in the PBRM1 gene were detected in 77 of the patients. While there was no difference in adipose tissue areas between the PBRM1 mutation group and those without PBRM1 mutation, statistically significant differences were found in normal attenuated muscle area parameters.


## CONCLUSION:
  This study shows that there was no difference between adipose tissue areas in patients with PBMR1 mutation, but normal attenuated muscle area was found to be higher in PBRM1 patients.


## INTRODUCTION
  Owing to the emergence of new genetic sequencing techniques and the increasing availability of open-source genetic and radiological datasets, a recent field of research called radiogenomics is facing rapid development 1 . Radiogenomics is primarily based on the relationship between the imaging features of diseases (imaging phenotypes) and gene expression patterns, gene mutations, and other genome-related features 2 . This field aimed to obtain preliminary predictive data for diagnostic, noninvasively prognostic, and, finally, ideal therapeutic evaluation 3,4 .

  The recent developments in genetics have led to the discovery of multiple mutations or genetic changes in clear cell renal cell carcinomas (ccRCCs), including mutations or alterations of genes encoding von Hippel-Lindau (VHL), polybromo-1 protein (PBRM1), BRCA1-associated protein m 1, SET domain containing 2 enzymes, and lysine-specific demethylase 5C 5,6 . Inactivation of the VHL tumor suppressor gene is the most common oncogenic event in ccRCC. Although the most widespread and famous mutation identified in ccRCCs is the VHL tumor suppressor gene (VHL), the ultimate meta-analysis has shown that there is no clear consensus on the prognostic or predictive effect of a VHL mutation in patients 7 . The second most commonly identified mutation in ccRCC involves the tumor suppressor PBRM1 gene. A recent meta-analysis reported that a mutation or decreased expression of a gene in PBRM1 was associated with poorer survival, advanced tumor, node, metastasis categories, tumor stage, and a higher Fuhrman nuclear grade in patients with RCC 8 . The latest studies have investigated the relationship between the success of immunotherapy and targeted therapy in advanced-stage RCC patients and the PBRM1 mutation 9 .

  Obesity is the real pandemic of today’s world. According to a meta-analysis, obesity increases the incidence of RCC 10 . In contrast, some studies have shown that obesity improves prognosis, even if it increases frequency 11 . There are also studies showing that it worsens prognosis and increases surgical complications 12 . This interesting situation encountered in some malignant and nonmalign processes besides RCC is called the “obesity paradox” 13 . In most of these studies, it is said that patients should be evaluated with radiological measurements, although it is cumbersome, so that the paradox can be understood more deeply 14 . It would be more correct to evaluate this situation not only in terms of obesity, but also in terms of the holistic aspect of body composition. In RCC, parameters such as skeletal muscle area and distribution and amount of adipose tissue based on radiological measurements are associated with overall and cancer-specific survival, treatment-related toxicity, and survival after radical nephrectomy 15,16 .

  It is more accurate to investigate the complex effect of body composition at the genomic level in a heterogeneous tumor group such as RCC. Therefore, we aimed to examine the relationship between RCC and the body composition of the PBRM1 gene mutation, which we think affects both survival and response to treatment.


## METHODS

### Patient selection
  A total of 236 RCC patients from the Cancer Genome Atlas Kidney Renal Clear Cell Carcinoma (TCGA-KIRC) dataset and 63 RCC patients from the Clinical Proteomic Tumor Analysis Consortium Clear Cell Renal Cell Carcinoma [CPTAC-CCRCC] collection were retrieved from the Cancer Imaging Archive TCIA 17–19 . Patients’ characteristics were obtained from TCIA, including age, gender, pathologic grade, the American Joint Committee on Cancer (AJCC) stage, and PBRM1 genomic profile. Informed consent was not required since TCIA data contained no personally identifying information.

  Inclusion criteria were as follows: (a) a diagnosis of pathologically proven ccRCC, (b) pre-operative abdominal CT examination, and (c) the images were complete and the necessary clinical information was complete. The exclusion criteria were as follows: (a) patients receiving pre-operative chemotherapy or radiotherapy treatment, (b) patients inadequate for an assessment of CT images, and (c) patients with lumbar surgical material. As a result of the criteria, 57 ccRCC patients from the CPTAC-CCRCC dataset and 234 from the TCGA-KIRC dataset, totaling 291 ccRCC patients, were included in the study.


### Assessment of body composition
  Body composition was evaluated by abdominal CT using automated artificial intelligence software (AID-U™, iAID Inc., Seoul, Korea), which was advanced using a fully convolutional network segmentation technique 20 . An abdominal radiologist specialist, blind to the clinical information, semi-automatically selected the axial CT sections at the level of the L3 vertebral lower end plaque with the help of sagittal reconstructed images. Later, the selected images were automatically segmented to generate the border of total abdominal muscles, subcutaneous adipose tissue (SAT), and visceral adipose tissue (VAT). For muscle quality assessment, the cross-sectional area of selected axial muscle images (i.e., psoas, paraspinal, transversus abdominis, rectus abdominis, quadratus lumborum, and internal and external obliques) were onward segmented by predetermined Hounsfield units (HU) thresholds as follows: (i) normal attenuation muscle area (NAMA; +30 to +150 HU), reflecting healthy muscle with little intramuscular fat; (ii) low attenuation muscle area (LAMA; -29 to +29 HU), reflecting unhealthy muscle with intramuscular lipid pool; and (iii) intramuscular adipose tissue (IMAT; -190 to -30 HU), reflecting the apparent fat tissue between muscle groups and muscle fibers 21,22 . Total abdominal muscle area (TAMA, -190 to +150 HU) was defined as a whole area including all skeletal muscles and fat tissues (TAMA=NAMA+LAMA+IMAT). An example of the interface of the tool can be seen in Figure 1.


### Statistical analysis
  Continuous variables were given as mean (±standard deviation [SD]), and categorical variables were given as a number (ratio). Normality tests were made for continuous variables Kolmogorov-Smirnov and Shapiro-Wilk tests. Comparisons between groups were made using the following statistical tests: chi-square test for categorical variables, Student’s t-test for normal-distributed continuous variables, and Mann-Whitney U test for non-normal-distributed continuous variables.

  We also used propensity score matching (PSM) with a 1:1 ratio to minimize selection bias and adjust the imbalance between groups. SPSS R plug-in (SPSS R Essentials) was applied for matching. We used the SPSS “PS Matching” feature to perform propensity score-matched analysis. Matching factors include age, gender, grade, and stage. Patients with PBRM1 mutations and patients without mutation and unknown mutation status were matched 1:1 in a multivariable logistic analysis using stepwise regression based on a greedy matching algorithm with a caliper of 0.05 times the SD of the logit. After applying 1:1 PSM, 76 eligible patients were matched to each group.


## RESULTS
  Of the patients, 184 were males and 107 were females. In all, 134 of the patients were of low grade (grades 1–2), and 157 were of high grade (grades 3–4). According to the AJCC staging, 148 patients were noted as stage 1, 27 patients as stage 2, 74 patients as stage 3, and 42 patients as stage 4.

  Mutations in the PBRM1 gene were detected in 77 of the patients. When the distribution of PBRM1 mutations was examined, no statistically significant difference was found according to gender, grade, and stage, but the frequency of PBRM1 mutations increased in advanced stage and stage disease (p=0.143, p=0.146, and p=0.304, respectively). The mean age was 60.04 (11.0) in the PBRM1 mutation group and 60.2 (12.7) in the other group, so no difference was found (p=0.875).

  When the PBRM1 mutation group and the other group were examined according to body composition parameters, statistically significant differences were found in NAMA and total muscle area parameters, p=0.002 and 0.006, respectively. More detailed evaluation according to other body composition parameters is given in Table 1.


## DISCUSSION
  In this study, we investigated for the first time the relationship of PBRM1, one of the genetic mutations of ccRCC, with fat and muscle tissue distribution in patients matched for age, sex, nuclear grade, and disease stage. In our study, no difference was found between patients with and without PBRM1 mutations in the SAT, VAT, and TAT areas. In a few studies conducted in ccRCC patients, regardless of genetic mutations, there is evidence that SAT and VAT values can be used as prognostic factors in predicting survival and nuclear grade 23,24 . In some of these studies, it has been shown that adipose tissue has a positive contribution to survival. However, in our study, we found that there was no relationship between the PBRM1 mutations of adipose tissue components. This may be due to the lack of matching in previous studies or the failure to evaluate genetic mutations. To reveal the importance of adipose tissue, prospective studies with large participation are needed, considering the genetic conditions.

  Another body component we evaluated in our study is muscle tissue. IMAT and LAMA were not associated with mutation either before or after matches. However, we found that NAMA values were higher in patients with mutations in the evaluation made before and after matching in all cases. We find it interesting that the normal attenuation muscle mass is higher in patients with PBMR1 mutation. Studies evaluating the relationship between ccRCC survival and sarcopenia in the literature have shown that nonsarcopenic patients have a longer survival 25 . However, most previous survival studies have been performed without considering the genetic mutations of ccRCC patients. The evaluation of patients with genetic mutations in our study was a different aspect of this study compared to others. The relative increase in normal-density muscle area in patients with PMBR1 mutation may be an issue that needs to be investigated.

  Mutations in the PBRM1 gene are the second most common mutation in ccRCC development 26 . The PBRM1 mutation acts as a direct effector as it influences the expression of proteins. In recent years, a few studies have shown that PBRM1 expression can serve as a promising biomarker in predicting the survival of various tumors. However, another study showed that reduced expression of PBRM1 is a poor predictor of overall survival, cancer-specific survival, progression-free survival, and recurrence-free survival in patients with RCC 27 . In contrast, contrary to studies showing that PBRM1 mutation is a poor prognostic factor, studies showing that this mutation can be a good predictor of response to both antiangiogenic and immunotherapy create a paradox 28 . McDermott et al. 29  found that patients with PBRM1 mutations may have increased neoangiogenesis. Miao et al. 30  found decreased expression of immune inhibitory ligands in those with intact PBRM1. We think that this paradox should be examined further, considering body composition.

  There are studies examining the effects of sarcopenia and other body composition parameters in RCC with very different results 25 . This may be because the body composition is formed as a result of quite complex genetic, epigenetic, and environmental factors. For example, if we look at our study from this perspective, it is unclear whether the increased muscle area in patients with PBRM1 mutations is a cause or an effect. On the contrary, it is not clear how the biology of the tumor changes when the PBMR1 gene mutation occurs and how this change affects body metabolism. For this reason, we think that body composition may contain much more information and secrets than we can imagine. There is a need to investigate patients with PBRM1 mutation with prospectively planned studies including a normal control group, which will explain the increased muscle area even in patients with all conditions matched. A more in-depth study of the net effect of body composition on tumor behavior still remains.

  There are some limitations to our study, namely, the retrospective nature of our study, lack of height and weight information of our patients, and lack of race information of all patients.


## CONCLUSION
  Our study shows that NAMA is greater in patients with PBMR1 mutation, even after PSM. We find that body composition plays a critical role in understanding the complex effect of PBRM1.


### Practical application
  Many studies have investigated the effects of body composition and genomic profile on survival and treatment response in RCC. Previous studies sought to evaluate without matching parameters such as tumor stage, grade, patient sex, and metastasis.


## INFORMED CONSENT AND PATIENT DETAILS
  The authors declare that this report does not contain any personal information that could lead to the identification of the patients.