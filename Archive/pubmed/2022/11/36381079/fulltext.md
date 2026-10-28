# Artificial neuronal network analysis in investigating the relationship between oxidative stress and endoplasmic reticulum stress to address blocked vessels in cardiovascular disease


## Background
  Cardiovascular disease is the leading cause of death in the world and is associated with significant morbidity. Atherosclerosis is the main cause of cardiovascular disease (CVD), including myocardial infarction (MI), heart failure, and stroke. The mechanism of atherosclerosis has not been well investigated in different aspects, such as the relationship between oxidative stress and endothelial function. This project aims to investigate whether an oxidative enzyme vascular peroxidase 1 (VPO1) and activating transcription factor 4 (ATF4) can be used as biomarkers in highlighting the pathogenesis of the disease and in evaluating the prognosis of the relationship with endoplasmic reticulum and oxidative stress. This paper used artificial neural network analysis to predict cardiovascular disease risk based on new generation biochemical markers that combine vascular inflammation, oxidative and endoplasmic reticulum stress.


## Methods
  For this purpose, 80 patients were evaluated according to the coronary angiography results. hs-CRP, lipid parameters and demographic characteristics, VPO1, ATF4 and Glutathione peroxidase 1(GPx1) levels were measured.


## Results
  We found an increase in VPO1 and hs-CRP levels in single-vessel disease as compared to controls. On the contrary, ATF4 and GPx1 levels were decreased in the same group, which was not significant. Our results showed a significant positive correlation between ATF4 and lipid parameters. A statistically significant positive correlation was also observed for VPO1 and ATF4 (r=0.367, P<0.05), and a negative correlation was found for ATF4 and GPx1 (r=-0.467, P<0.01). A significant negative relationship was noted for GPx1 and hs-CRP in two/three-vessel disease (r=-0.366, P<0.05). Artificial neural network analysis stated that body mass index (BMI) and smoking history information give us an important clue as compared to age, gender and alcohol consumption parameters when predicting the number of blocked vessels.


## Conclusions
  VPO1 and ATF4 might be potential biomarkers associated with coronary artery disease, especially in the follow-up and monitoring of treatment protocols, in addition to traditional risk factors.


## Introduction
  Endothelial dysfunction is an early stage of many cardiovascular diseases, such as atherosclerosis, coronary heart disease, and hypertension. Oxidative stress promotes endothelial dysfunction via several mechanisms such as increasing lipid, protein oxidation, or inflammatory burden.

  Oxidized low-density lipoproteins (ox-LDLs) contribute to the formation and progression of atherosclerotic lesions by promoting local inflammation and toxic events, which might cause endothelial dysfunction [1] [2]. The subendothelial retention of low-density lipoprotein (LDL) and its oxidative form, oxidized LDL (ox-LDL), activates signalling pathways resulting in an oxidative stress response, which leads to atherosclerosis [3] [4].

  Oxidative stress plays a crucial role in abdominal aortic aneurysm (AAA) formation and regulates VSMC phenotypic switch. Hydrogen peroxide (H2O2), an important key reactive oxygen species, acts as an important signalling molecule that modulates VSMCs [5].

  A heme-containing peroxidase, called VPO1 (vascular peroxidase 1), is mainly expressed by vascular endothelial cells, cardiac, and smooth muscle cells [6]. VPO1 plays a critical signalling role in mediating the development and progression of cardiovascular disease [7] [8] [9]. It generates hypochlorous acid (HOCl), which is a strong reactive oxygen substance (ROS) from hydrogen peroxide (H2O2) and chloride anion (Cl). Recently, it was also reported that HOCl contributes to the acceleration of endothelial ageing in hyperlipidemic rats or in ox-LDL-treated cells [10].

  The main player of the energy metabolism, mitochondria, contributes to ROS formation via high energy metabolism. While ROS are vital for life, due to their high chemical reactivity, growing evidence support that some organelles such as ER need ROS to appreciate their function. The ER is responsible for correcting misfolding of proteins into their functional conformations. The disulfide bonds play a crucial role during this process which is assisted by protein disulfide isomerases (PDI), endoplasmic reticulum oxidoreductin 1 (ERO1), and glutathione (GSH) [10].

  Of the machine learning techniques used in predicting coronary artery disease, neural network analyses are popularly used to improve performance accuracy. Neural network analyses make it possible to discover new patterns and information related to coronary artery disease by analyzing complex data [11].

  We, therefore, hypothesized that the changes of VPO1 activity during the progression of atherosclerosis might affect ER stress which induces antioxidant gene expression (ATF6). To test this hypothesis, we investigated VPO1 activity, ATF6 and hs-CRP levels, and glutathione peroxidase-1 activity according to the coronary angiography results in patients with cardiovascular disease.


## Materials and methods
  A total of 80 individuals, 20 patients with N-vessel disease, 30 patients with one vessel disease, 30 patients with two-three vessel disease from Cerrahpasa Medical School, Department of Cardiology, at the University of Istanbul-Cerrahpasa, were enrolled in this study. The study protocol was previously reviewed and approved by the Ethics Committee of the University of Istanbul, Cerrahpasa Medical School (Issue Number: 83045809-604.01.02, 03.05.2016). Written informed consent was obtained from all participants. All blood samples were collected following the Declaration of Helsinki.

  Patients with chronic liver disease, chronic renal failure, cancer, serious systemic infections, chronic lung disease, or any endocrine disease were excluded. The patients were angiographically determined. According to their angiography results, subjects were split into three groups as defined above. The patients with no-vessel disease (N vessel disease) had no obstructed vessels. Still, they suffered from chest pain similar to angina pectoris. All of them were admitted with unstable angina pectoris. None of them were significant alcohol consumers.


### Samples
  Samples for the determinations of vascular peroxidase 1 (VPO1), transcription activation factor 4 (ATF4), glutathione peroxidase 1 (Gpx1), hs-C-reactive protein (hs-CRP), and lipid parameters were obtained from venous blood after a 12 h fasting by centrifugation of clotted specimen within 30 min. It was centrifuged at 4400 rpm for 10 min. The separated serum and plasma samples were stored in several small aliquots at − 30°C until being assayed.

  Total cholesterol (TC), high density lipoprotein (HDL), low density lipoprotein (LDL), triglyceride (TG) and hs-CRP levels were analyzed in the autoanalyzer of the faculty's central biochemistry laboratory.

  Enzyme-linked immunosorbent assay (ELISA) procedure was used to determine the serum VPO1 (Human Peroxidasin Homolog (PXDN)-(CUSABIO, CSB-EL019106HU-USA)), ATF4-transcription activation factor-4 (MYBIOSOURCE-MBS762729-USA) and Gpx1 (CUSABIO, CSB-EL009866HU-USA), levels according to the procedure from the manufacturer. CRP was measured immunoturbidimetrically in routine clinical chemistry analyzer (Roche, Hitachi, Basel, Switzerland) by using reagents purchased from the same manufacturer.


### Statistical analysis
  Analysis of data was done with SPSS statistical analysis software (version 20.0; SPSS Inc, Chicago,IL, USA). Results were expressed as means ± SD or median and interquartile range. ATF4, Gpx1, hs-CRP levels were logarithmically transformed to achieve normal distributions. Correlation analysis was done by Pearson correlation analysis. All analyses were twotailed, and P-values less than 0.05 were considered statistically significant. Then we applied artificial neural network analysis to check the importance of our parameters on blocked vessels. In the analysis; age, gender, CAD history, smoking and alcohol comsumption defined as a factor. BMI, VPO1, ATF4, Gpx1, hs-CRP, HDL, LDL, total cholesterol, triglyceride defined as covariates.


## Results
  Clinical characteristics of 80 patients according to the angiographic results were summarized in Table 1. Mean age of the patients was similar (55, 59 and 60, respectively; P>0.05). There were no significant differences between BMI and the lipid parameters among groups (P>0.05).

  ATF4, VPO1, Gpx1 and hs-CRP levels in patients according to the blocked vessels were shown in Table 2. The decline in ATF4 level was observed in one vessel and two-three vessel disease as compared to N-vessel disease. A significant decrease was detected in one vessel disease compared to N-vessel disease (1.57 vs 1.96; P< 0.05). No significant change was seen for other parameters among groups (P>0.05). We recognized a decline in Gpx1 levels in one vessel and two/three-vessel disease as compared to N-vessel disease (114, 117 vs 143, respectively), but this difference did not reach significance (P>0.05).

  The percentage of blocked vessel disease increases among men (45%, 77%, 70%, respectively) as compared to women counterpart (55%, 23%, 30%, respectively). The prevalence of LDL highness (75%, 63.3%, 70%, respectively), and CAD history (60%, 53.3%, 19%, 63.3%) were for N-vessel, one vessel, two/three vessel disease, respectively (Figure 1).

  Afterward, we checked associations of the biochemical markers within the subjects. A significant but opposite relationship was observed between VPO1 and Gpx1 (r=-0.285, P<0.05). No significant association was seen for other parameters in Table 3. We next analyzed the correlations between the same biochemical and lipid parameters in Table 4. A significant, positive association were observed between ATF4 and triglyceride (r=0.294, P<0.001), total cholesterol (r=0.359, P<0.001), and LDL cholesterol (r=0.317, P<0.001). No other significant correlations were observed between other counterparts.

  Regarding the observed relationship, which was seen in Table 3 and Table 4, we next checked the similar correlations among the same biochemical parameters across blocked vessel disease. We could not find any significant association for N-vessel disease. We found a positive and significant association between VPO1 and ATF4 (r=0.367, P<0.05), also a negative and significant association between ATF4 and Gpx1 (r=-0.467, P<0.01). In two-three vessel disease counterpart, we observed a negative but significant correlation between hs-CRP and Gpx1 levels (r=-0.366, P<0.05) (Table 5).

  In Figure 2, we analyzed the synaptic weight of the tested parameters. We used the »standardized« method for covariates; the number of hidden layers was »1«, the activation function was »hyperbolic tangent«, and the activation function of the output layer was »sigmoid«. Our artificial neural networks model, trained using 65 data, has been tested in test data. Estimates were made using our model on 15 patients whose final output was stored. In fact, 11 out of 13 patients who were sick, estimated correctly, so the specificity was found to be 84.6%. The specificity rate for the training data set is 93.6%. Likewise, the sensitivity rate was 50% in test data and training data. The values of the created model were calculated as 81.25%, with 65 correct results for the whole data set. Performance values of our model are over 80% in both data groups. We confirmed the results by ROC graph, where the under curve area (UCA) was 82%.

  The independent variable importance figure shows us which factors are important when estimating artificial neural network algorithm. Accordingly, GPx1, HDL, VPO1 are the most important variables. At the same time, we can say that body mass index (BMI) and smoking history information are more important than age, gender and alcohol consumption parameters in predicting blocked vessels (Figure 3).


## Discussion
  Atherosclerosis is a chronic inflammatory disease caused by various factors such as lipids, various genes, immune cells and different kinds of enzymes. Apart from several mechanisms proposed for the pathogenesis of atherosclerosis, there is still a considerable gap in explaining the big picture [12]. In recent studies, the relationship between oxidative stress and endoplasmic reticulum stress became important in the pathogenesis of the disease [13]. Our current study aimed at a preliminary study to determine a biomarker that can contribute to the diagnosis and treatment of coronary artery disease, based on previous research findings in this field.

  We observed that VPO1 and CRP levels were significantly higher in single vessel patients than in control subjects, whereas ATF4 and GPx1 levels were lower. In studies examining the relationship between VPO1 and CAD, it is suggested that VPO1 is closely related to oxidative stress and therefore plays an important role in the pathogenesis of the disease [14] [15]. In a rabbit model with myocardial ischemia-reperfusion injury, VPO1 mRNA levels and its expression have been shown to increase with the increase in oxidative damage [16]. Another study conducted on spontaneously hypertensive rabbits revealed that VPO1 expression increased significantly in arterial tissues [17].

  In our study, a statistically significant positive correlation was found between VPO1 and ATF4 levels in single-vessel patients. This positive relationship between VPO1 and ATF4 suggests that increased oxidative stress induces the transcription factor ATF4, which actuates the antioxidant defence system. ATF4 is co-activated with UPR in human aortic endothelial cells exposed to oxidized phospholipids, an important trigger of the atherosclerotic process [18]. In studies examining the proapoptotic role of ATF4, it was determined that ATF4 activates the signal pathway in endothelial cells, in which CHOP and ATF3 also take part [19]. On the other hand, ATF4 mediates the upregulation of GRP78, which is one of the major regulators of endoplasmic reticulum stress [20] [21]. ATF4 is thought to protect endothelial cells from oxidative stress-induced cellular damage by these mechanisms and attenuates lipid metabolism [22]. Our study found a statistically significant relationship between ATF4, provoking the antioxidant defence system, triglyceride, total cholesterol, and LDL cholesterol levels, which are substrates of oxidative lipid damage.

  In the correlation analysis results in which all our cases were included, it was observed that there was a statistically significant negative relationship between VPO1 and GPx1.

  Harding et al. [23] showed that ATF4-mediated integrated stress response provides a supply of amino acids for protein and glutathione biosynthesis and protects cells against oxidative stress. We think that activation of the ATF4-mediated antioxidant system consumes GPx1, a member of this system. GPx1 reduces H2O2 to water, preventing the formation of more dangerous radical products. Therefore, the decrease in GPx1 levels we detected may actually result from the compensation mechanism for increased H2O2 clearance. VPO1 uses H2O2 to form more toxic HOCl in the presence of Cl-ions. Since the substrate of VPO1 will also decrease due to the decreased H2O2 in the environment, there may be no change in its synthesis [5] [24]. We think that the inverse relationship between GPx1 and VPO1 observed in both the total group and the patient group with a single blocked vessel may be related to the decreased H2O2 levels.

  In our study, a statistically significant negative correlation was found between Gpx1 and CRP levels in two and three-vessel patients. Increasing oxidative stress due to the decrease in Gpx1 levels triggers inflammation. Therefore, increased oxidative stress in the early stages of the disease activates the antioxidant defence system but triggers inflammation in the more advanced stages of the disease [25].

  The relationship between oxidative stress and endoplasmic reticulum stress with the pathogenesis of atherosclerosis has not been demonstrated in detail [26]. We believe that our findings will explain the relationships mentioned above and elucidate the pathogenesis of atherosclerosis. In this context, we believe that VPO1 and ATF4 may be biomarkers associated with CAD and will provide significant benefits in the follow-up and monitoring of the treatment process of the disease in addition to traditional risk factors. Our results should be confirmed by extensive studies in different populations and wider patient groups, in which oxidative stress will be evaluated together with protein and lipid damage markers and will be examined with specific vascular inflammation markers.

  Azuma et al. [27] developed a good and straightforward statistical model with remarkable accuracy in discriminating coronary artery lesions using common parameters used in clinical medicine. This method helps decide the time and type of therapy for coronary artery disease formation in the future [27]. Kim et al. proposed a new model which may aid in the prevention of heart disease in coronary artery patients. This analysis method might greatly benefit people in terms of predicting, beyond a simple prediction of the coronary artery disease risk and the quantitative survival time [11].

  We acknowledge some of the limitations of this study. Patients taking any medication that could affect endothelial function, including statins and antihypertensive agents, were not excluded from the study. Our sample size is small. Female individuals' menopausal status was not evaluated. We defined patients according to their angiography results and evaluated lipid cut-off according to the European Society of Cardiology Score.


## Dodatak

### Acknowledgements
  We thank Ozcan Arkan for the assistance of artificial neural network statistical analysis. This work was supported by the grant of the University of Istanbul Research Foundation. The project number is »TYL-2017-22043«.


### Conflict of interest statement
  All the authors declare that they have no conflict of interest in this work.