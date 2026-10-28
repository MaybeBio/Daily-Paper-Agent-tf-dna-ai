# Polo‐like kinase2 regulates renal tubulointerstitial fibrosis via notch signaling pathway in diabetic kidney disease


## Abstract
  Renal tubulointerstitial fibrosis is considered as an important pathological feature of diabetic kidney disease (DKD). However, the underlying mechanism remains unclear. Polo‐like kinase2 (PLK2) is a known player in the regulation of organ fibrosis. Herein, we investigated the expression and function of PLK2 in renal tubular epithelial cells in DKD. Data from the GSE30529 datasets were subjected to analyze the differentially expressed genes (DEGs) in non‐diabetic and diabetic renal tubule samples. Molecular docking analysis and Co‐IP assay were performed to investigate the interaction between PLK2 and NOTCH1. Immunohistochemistry, immunofluorescent staining, qRT‐PCR, and western blot were performed. Our research revealed an increased expression of PLK2 in both DKD mouse kidney tissues and HK‐2 cells stimulated by high glucose (HG). Silencing PLK2 remarkably reduced the expression of the renal fibrosis‐related markers fibronectin (FN), connective tissue growth factor (CTGF) and alpha smooth muscle actin(αSMA). Furthermore, we verified the interaction between PLK2 and NOTCH1. Silencing PLK2 significantly inhibited the activation of the Notch signaling pathway, and concurrently overexpressing HES1 rescued the downregulation of FN, CTGF, and αSMA induced by transfecting si‐PLK2. Finally, we found that treatment with DAPT suppressed the activation of the Notch signaling pathway and reversed the progression of renal fibrosis caused by HG. This study demonstrates that PLK2 mediates renal tubulointerstitial fibrosis in DKD by activating the Notch signaling pathway, suggesting that PLK2 may be a potential therapeutic target for DKD.


## INTRODUCTION
  Diabetic kidney disease (DKD), one of the common microvascular complications of diabetes, is a vital cause of end‐stage renal disease (ESRD) and is recognized as a public health problem worldwide. The global proportion of the prevalent ESRD patients with diabetes increased from 19.0% in 2000 to 29.7% in 2015, whereas the percentage of newly diagnosed ESRD patients attributed to diabetes increased from 22.1% to 31%. 1  However, the pathogenesis of DKD is still obscure. In order to figure out its molecular basis, further investigation is necessary.

  The occurrence and development of DKD encompasses a variety of pathological alterations, including basement membrane thickening, podocyte loss, mesangial expansion, tubular atrophy, and renal interstitial inflammation and fibrosis. 2  Glomerular damage has long been viewed as the core of the progression of DKD. However, increasing evidence suggested that renal tubular injury may occur earlier than glomerular damage. Latest research indicated that mitochondrial dynamics alterations in proximal tubular epithelial cells (PTECs) were observed prior to the occurrence of proteinuria and renal histopathological changes in diabetic rats. 3  Additionally, another study revealed that, in early‐stage DKD, microalbuminuria resulted from hindered albumin reabsorption in the proximal tubule, rather than enhanced albumin filtration at glomeruli. 4  Consequently, renal tubular injury plays an essential role in the development of DKD.

  Polo‐like kinase2 (PLK2) is a member of the family of serine/threonine kinases(STKs), and is considered a regulatory factor in many aspects, including cell cycle, 5 ,  6 ,  7  cell differentiation, 8 ,  9 ,  10  stress response, 11  tumorigenesis, 12 ,  13  and neurodegenerative diseases. 14 ,  15  Lately, a growing number of research studies revealed a significant link between PLK2 and the progression of fibrosis. KÜNZEL S R et al. found that the irregular activity of the PLK2/ERK1/2/OPN axis critically contributed to atrial fibrillation‐related atrial fibrosis. 16  What's more, KANT's studies shed light on the importance of PLK2 in regulating pulmonary fibrosis. 17  In addition, recent studies reported that PLK2 was associated with the procedure of DKD. 18 ,  19  However, these studies are limited in exploring the role of PLK2 in podocytes and mesangial cells, and whether PLK2 has a similar effect in PTECs needs further investigation.

  The Notch signaling pathway consists of four transmembrane receptors (Notch1‐Notch4), two Jagged family ligands (Jag1 and Jag2), and three Delta‐like ligands (DLL1, DLL3, and DLL4). 20  When receptors engage with ligands on neighboring cells, Notch transforms to the activated form Notch intracellular domain (NICD), which enters the nucleus to regulate the expression of downstream targets, and ultimately results in pathological conditions. 21  Clearly, the Notch signaling pathway is necessary and sufficient for the onset and development of renal fibrogenesis in DKD. 22  Nevertheless, whether PLK2 regulates the progression of DKD via activation of the Notch signaling pathway is still unclear. In this study, we aimed to investigate the mechanism through which PLK2 regulates the Notch signaling pathway to promote renal interstitial fibrosis in DKD.


## METHODS AND MATERIALS

### Differential gene expression analysis
  The gene expression data was obtained from the free public database Gene Expression Omnibus (GEO) database (http://www.ncbi.nlm.nih.gov/geo). The following screening criteria were used: “diabetic kidney disease”, “Homo sapiens”, “tubule” and “expression profiling by array”. Eventually, mRNA datasets GSE30529 met the requirement of the above conditions. The GSE30529 dataset includes 10 diabetic tubule samples and 12 non‐diabetic tubule samples, detected by [HG‐U133A_2] Affymetrix Human Genome U133A 2.0 Array. The DEGs in non‐diabetic and diabetic renal tubule samples were screened using the limma package in the R software (version 4.0.5), with |log2FC| >1 and p < .05 considered significant. The DEGs were visualized by volcano map and heatmap.


### Animal modeling and grouping
  C57BL/6J male mice (6–7 weeks old) were purchased from the experimental animal center of Southern Medical University and randomly divided into a control group (n = 8) and a DM model group (n = 8). Firstly, the control mice were fed with a normal diet, while the DM mice were fed with a high‐fat diet (HFD, D12492, HFK Bioscience, Beijing, China) for 4 weeks. Then the DM mice were fasted for 12 h before receiving an intraperitoneal injection of streptozotocin (STZ, 50 mg/kg daily for five days, in citrate buffer, pH = 4.5, Biofroxx). After 1 week of STZ injection, a random blood glucose level > 16.7 mmol/L was observed, which indicates successful establishment of the diabetes model in the mice. Both the control mice and the DM mice were sacrificed 16 weeks after the successful model establishment. The animal experiments were conducted according to the established institutional and state guidelines for the care and use of laboratory animals, and approved by the committee of the Laboratory Animal Center, Nanfang Hospital, Southern Medical University, Guangzhou, China (certificate number: IACUC‐LAC‐20230323‐003).


### Immunohistochemistry
  The kidney tissue sections were stained with anti‐PLK2 (1:200, Bioss, bs‐12730R), anti‐FN1(1:200, Proteintech, 15613‐1‐AP), anti‐CTGF(1:150, Proteintech, 25474‐1‐AP), anti‐αSMA antibodies (1:200, Proteintech, 14395‐1‐AP) at 4°C overnight, and then the appropriate secondary antibody for the immunohistochemical analysis was added. Images were acquired by light microscopy.


### Cell culture and transfection
  The human proximal tubular cell line (HK‐2) was obtained from the China Center for Type Culture Collection (CCTCC) and cultured in DMEM with 5.5 mmol/L glucose containing 10% fetal bovine serum (FBS) in a 5% CO2 incubator at 37°C. After starvation with 2% FBS for 24 h, the cells were cultured in DMEM with 30 mmol/L and 5.5 mmol/L glucose, respectively.

  The small interfering RNA targeting PLK2 (si‐PLK2) (Ribobio, Guangzhou, China) was transfected into HK‐2 cells at a final concentration of 50 nM for 48 h. The sequences of si‐PLK2 are as follows: 5′‐GCTGATGTCTGGCTGTTCA‐3′. In order to overexpress HES1, the pcDNA3‐HES1 plasmid was transfected into HK‐2 cells. All transfections were conducted with Lipofectamine® 3000 (Invitrogen, Carlsbad, CA, United States) according to the manufacturer's instructions.


### Quantitative real‐time PCR
  Total RNA from all samples was isolated with the TRIzol reagent (TaKaRa, Dalian, China) and RNA quality was assessed by measuring the OD260/OD280 ratio using a NanoDrop micro spectrophotometer (Thermo Fisher). Reverse transcription was performed with PrimeScript™ RT Master Mix (Takara, Dalian, China). qRT‐PCR was conducted in a Roche LightCycler 480 Real‐Time PCR System (Roche, Basel, Switzerland) with SYBR® Premix Ex Taq™ (Takara, Dalian, China). The primer sequences are listed in Table S1. The expression of each gene was calculated using the 2−ΔΔCt method, and β‐actin was used as an internal control.


### Western blot
  The total protein was extracted with RIPA lysis buffer (Fdbio science, Hangzhou, China), and the protein concentration was detected with a BCA assay (Takara, Dalian, China). Proteins (20 μg) were separated using 8%–10% SDS‐PAGE (Bio‐Rad, Hercules, CA, USA) and then transferred to polyvinylidene difluoride (PVDF) membranes (Millipore, Billerica, MA). After blocking with 10% skimmed milk powder (Sigma, United States) for 1 h at room temperature, the membranes were incubated with the following primary antibodies overnight at 4°C: anti‐FN (Proteintech, 1:2000, 15613‐1‐AP), anti‐CTGF (Proteintech, 1:4000, 25474‐1‐AP), anti‐αSMA antibodies (Proteintech, 1:2000, 14395‐1‐AP), anti‐PLK2 (Abclonal, 1:1000, A7066), anti‐NOTCH1 (Abclonal, 1:1000, A7636), anti‐HEY1 (Proteintech, 1:2000, 19929‐1‐AP), anti‐HES1 (Abclonal, 1:1000, A11718), anti‐β‐Tubulin (Proteintech, 1:10 000, 10094‐1‐AP). Next, the membranes were incubated with appropriate secondary antibodies (Proteintech, goat anti‐mouse, SA00001‐1, and goat anti‐rabbit, SA00001‐2, 1:15 000) at room temperature for 1 h. Images were acquired using an enhanced chemiluminescence (ECL) (Fdbio science, Hangzhou, China)‐based imaging detection system (GelViewm 6000 Pro, Guangzhou, China) and analyzed with ImageJ software.


### Immunofuorescence
  Slides of HK‐2 cells were fixed with 4% paraformaldehyde for 15 min, permeabilized with 0.3% Triton X‐100 for 30 min, then incubated in 5% BSA with primary antibodies against PLK2(Bioss, 1:500, bs‐12730R) overnight at 4°C. The slides were incubated with the secondary antibody (Invitrogen, 1:200, A11008) at room temperature in the dark for 1 h. Finally, nuclei were counterstained with DAPI. The slides were photographed under a fluorescence microscope (Imager D2, ZEISS).


### Co‐immunoprecipitation (co‐IP)
  Cells were collected and lysed with lysis buffer (20 mM Tris HCl pH = 8, 137 mM NaCl, 1% Triton X‐100, 2 mM EDTA, protease inhibitor cocktail) on ice. The lysate was sonicated 3 times in ice‐cold water, and then centrifuged (16 000 g, 10 min, 4°C) to remove cellular debris. Total protein, 50 μg, was used for immunoprecipitation with anti‐Flag beads (Bimake, B26101) and the precipitated protein complex was used for Western blotting with antibodies against Flag (Proteintech, 20543‐1‐AP).


### Molecular docking analysis
  To investigate the interaction between PLK2 and NOTCH1, rigid protein–protein docking was performed by using GRAMM‐X (http://gramm.compbio.ku.edu/). The protein structural domains of PLK2 and NOTCH1 were obtained from the Protein Data Bank PDB database (http://www.rcsb.org/).

  PDBePISA (https://www.ebi.ac.uk/pdbe/pisa/) and Pymol (Version 2.4) were used to investigate protein–protein interactions and further visual analysis.


### Statistical analysis
  The results were presented as the mean ± SEM. Two‐tailed Student's t tests were used for pairwise comparisons of independent groups. Statistical analysis was performed by GraphPad Prism version 7.00 for Windows (GraphPad Software Inc., La Jolla, CA, USA), and differences with p < .05 were considered significant.


## RESULTS

### DEGs in renal tubules of DKD patients and controls
  To identify DEGs in renal tubules between diabetic patients and normal healthy adults, data from GSE30529 were downloaded and normalized. Eventually, after removing the duplicate probe, we identified 779 DEGs in GSE30529. It contained 670 upregulated and 109 downregulated genes. The volcano map for DEGs was shown in Figure 1A. The heatmap for the top 60 DEGs was displayed in Figure 1B. Obviously, the upregulated DEGs contained lots of fibrotic‐associated genes, including COL1A2, COL3A1, Vimentin, and FN. Among all, PLK2, previously identified as a vital regulator in the cell cycle and recently thought to be a pro‐fibrotic factor, had caught our attention. The latest research highlighted the critical involvement of PLK2 in the progression of myocardial and pulmonary fibrosis. 16 ,  17  However, whether PLK2 has a similar effect in regulating the renal fibrosis process has not been reported yet. Moreover, Zou et al. demonstrated that silencing PLK2 attenuated HG‐induced podocyte apoptosis and inflammation, which underscored PLK2's detrimental impact on glomeruli in the DKD condition. 19


### PLK2 is upregulated in the kidneys of the DKD mouse model
  To investigate the regulatory function of PLK2 in renal tubules during the progression of DKD, firstly we established a DKD mouse model through HFD and STZ. The random blood glucose, serum creatinine, and urinary albumin‐to‐creatinine ratio (UACR) were significantly increased in DKD mice (Figure 2A,C,D), while the body weight of DKD mice was lighter than that of normal mice remarkably (Figure 2B). H&E, Masson's trichrome, PAS staining, and picrosirius red staining demonstrated that the DKD model was successfully constructed. Tubular edema, basement membrane thickening, glycogen, and collagen deposition can be observed in the kidney cortexes of DKD mice (Figure 2E,G–I). Immunohistochemistry and semiquantitative analyses of the renal tissues showed that, compared to control mice, PLK2 and fibrosis markers (FN, CTGF and αSMA) were significantly increased in DKD mice (Figure 2F,J). The qRT‐PCR and western blot results also indicated the enhanced expression of PLK2, FN, CTGF, and αSMA (Figure 2K–M). Taken together, these results suggest that PLK2 is related to the process of renal fibrosis in DKD.


### PLK2 is associated with renal fibrosis in HG‐induced HK‐2 cells
  In HK‐2 cells treated with 30 mM HG, both mRNA and protein expression levels of fibrosis indicators were gradually increased. Furthermore, PLK2 was significantly upregulated in HG‐induced HK‐2 cells, the same as we observed in vivo (Figure 3A–C). As shown in Figure 3D, immunofluorescence indicated that the levels of PLK2(green) were enhanced after the treatment with HG. Thus, we speculated that PLK2 may play an important role in renal fibrosis in DKD.

  In order to clarify the effect of PLK2 in tubulointerstitial fibrosis, we inhibited PLK2 by transfecting si‐PLK2. The western blot results indicated that the expression levels of PLK2 were successfully suppressed (Figure 3E,F). Then we found that the upregulation of FN, CTGF, and αSMA in HG conditions was restrained by silencing PLK2, which emphasizes the relationship between PLK2 and renaltubular injury in DKD (Figure 3G–I).


### PLK2 interacts with NOTCH1
  Previous studies suggested that many signaling pathways are of importance in regulating renal fibrosis, such as the Wnt/β‐Catenin signaling pathway, TGF‐β signaling pathway, PI3K/Akt signaling pathway, Notch signaling pathway, and so on. 22  In ALAFATE W's study, PLK2 was proved to be a tumor suppressor by attenuating chemoresistance in glioblastoma. Overexpressing PLK2 suppressed cell growth, colony formation, and migratory ability by inhibiting the Notch signaling pathway, indicating that PLK2 may regulate biological behavior via the Notch signaling pathway. 23  However, whether PLK2 could promote renal fibrosis by activating the Notch signaling pathway in tubular epithelial cells in DKD is still unclear.

  To verify whether PLK2 could interact with NOTCH1, we performed rigid protein–protein docking between PLK2 and NOTCH1. As shown in Figure 4A–C, PLK2 and NOTCH1 formed hydrogen bonds through amino acid residue sites such as SER 567 –GLN 2315 and HIS 349 –ARG 2313, revealing that PLK2 and NOTCH1 formed a stable protein docking model. Moreover, we transfected vector and FLAG‐PLK2 plasmid in HEK‐293 T cells, respectively, and found that PLK2 interacted with NOTCH1 by Co‐IP assay (Figure 4D). These results support the hypothesis that the Notch signaling pathway may be downstream of PLK2.


### PLK2 promotes fibrogenesis in HG‐treated HK‐2 cells via the Notch signaling pathway
  In order to verify the above hypothesis, we detected the relative targets of the Notch signaling pathway including NOTCH1, HEY1, and HES1 after silencing PLK2 in HG‐stimulated HK‐2 cells. Compared with that in HG conditions, loss of PLK2 downregulated the expression of NOTCH1, HEY1, and HES1, indicating a suppression of the Notch signaling pathway (Figure 5A–C). Then, we overexpressed HES1, the downstream target of the Notch signaling pathway; a western blot assay was carried out to confirm its transfection efficiency (Figure 5D). Obviously, the overexpression of HES1 reversed the anti‐fibrotic effect benefited from the knockdown of PLK2(Figure 5E–G), demonstrating that PLK2 facilitated the process of fibrosis in HG‐induced HK‐2 cells via the Notch signaling pathway.


### The important role of the Notch signaling pathway in modulating the process of tubulointerstitial fibrosis
  To investigate whether the Notch signaling pathway participated in promoting tubulointerstitial fibrosis in DKD, qRT‐PCR and western blot analyses were performed. In HG‐treated HK‐2 cells, relative targets of the Notch signaling pathway, NOTCH1, HEY1, and HES1, were remarkably increased (Figure 6A–C), suggesting the activation of the Notch signaling pathway in HG conditions. Next, we concurrently treated HG‐induced HK‐2 cells with DAPT, a Notch signaling pathway inhibitor, to validate its influence on regulating renal fibrosis. At mRNA and protein levels, DAPT inhibited the enhancement of both the Notch signaling pathway's relative targets (Figure 6A–C) and the renal fibrosis markers (Figure 6D–F). These findings underscore the profibrotic impact of the Notch signaling pathway in DKD.


## DISCUSSION
  Diabetic kidney disease, one of the most common complications of diabetes mellitus, is characterized by basement membrane thickening, mesangial expansion, podocyte injury, renal interstitial inflammation, and fibrosis. In recent years, a growing number of studies have revealed the importance of renal tubular injury in the occurrence and development of DKD. Clinical observations have found that among DKD patients with microalbuminuria, only one‐third exhibit typical glomerular structural changes, one‐third have no or only minimal glomerular damage but severe tubular injury, and another one‐third have normal kidney structures but still show varying degrees of tubular damage. 24  Otherwise, a five‐year follow‐up study including 177 patients with DKD reveals that the levels of tubulointerstitial injury markers, such as urinary neutrophil gelatinase‐associated lipocalin (NGAL), kidney injury molecule1 (KIM‐1), and plasma fibroblast growth factor 23 (FGF23) are significantly correlated with the decline of eGFR in DKD patients. 25  In addition, Kim et al. observed 237 patients with DKD for 29 months and found that urinary cystatin C levels, a biomarker of tubular injury, were positively correlated with the decline of kidney function. 26  These findings draw a conclusion that, in patients with DKD, tubular injury is a key aspect in the progression of DKD.

  The Polo‐like kinases (PLK) family is a group of serine/threonine protein kinases (STK), including five members: PLK1, PLK2, PLK3, PLK4 and PLK5, among which PLK1 has been widely studied in the last two decades. As a founding member of the PLK family, PLK1 plays an essential role in regulating various stages of cell cycle, such as centrosome maturation, 27  mitotic entry, 28  chromosome segregation 29  and cytokinesis. 30  However, growing evidence indicates that PLK1's role extends beyond mere cell proliferation. In recent years, researchers revealed the significance of PLK1 in the progression of kidney disease. For instance, Du et al. discovered that PLK1 aggravated renal tubulointerstitial fibrosis by regulating autophagy/lysosome axis. 31  Wang et al. found that bromodomain‐containing protein 4(BRD4) interacted with PLK1, subsequently leading to the activation of the NOD‐like receptor thermal protein domain associated protein 3(NLRP3) inflammasome and cell pyroptosis, inflammation, and fibrosis in DKD. 32  Zhang et al. observed that PLK1 inhibitor, BI‐2536, ameliorated DKD progression by dampening the NF‐kB and Smad3 signal transduction and transcriptional activation. 33

  Likewise, besides the regulation of the cell cycle, the role of PLK2 in the development of disease has attracted growing attention. Recent studies found that insulin resistance‐associated diabetes aggravated the development and progression of Parkinson's disease through PLK2‐mediated mitochondrial dysfunction, upregulated ROS production, and enhanced Alpha‐synuclein (SNCA) signaling, suggesting that PLK2 may be a vital regulatory factor in metabolic disease. 15  Currently, studies on PLK2's role in kidney disease are solely concentrated on glomerular damage. Li et al. observed that PLK2 knockdown reversed the hypertrophy, extracellular matrix production, and oxidative stress by suppressing the activation of p38‐MAPK signaling in mesangial cells. 18  And Zou et al. discovered that PLK2 was increased in HG‐induced podocytes and silencing PLK2 significantly attenuated HG‐triggered podocyte apoptosis and inflammation. 19  Our studies found that PLK2 was upregulated in HG‐treated HK‐2 cells correspondingly, and silencing PLK2 remarkably alleviated renal tubulointerstitial fibrosis, emphasizing the modulatory effect of PLK2 in renal tubular injury in DKD.

  Renal fibrosis is a complex pathological process involving the crosstalk of multiple signaling pathways. The Notch, TGF‐β/Smad, Wnt/β‐Catenin, and Hedgehog signaling pathways play important roles in renal fibrosis, and the crosstalk between these signaling pathways further complicates the pathological mechanisms of renal fibrosis. As a classic pro‐fibrotic signaling pathway, the activation of the Notch signaling pathway was observed both in tubular interstitial fibrosis (TIF) patients and in TIF mouse models. Additionally, it has been established that the Notch signaling pathway is necessary and sufficient for the occurrence and development of TIF. 34  Xiao et al. found that loss of Homeobox A5 (HOXA5) via DNA methylation contributed to fibrogenesis in kidney diseases by activating the Notch signaling pathway. 35  In this study, we found that the Notch signaling pathway was activated in HG‐induced HK‐2 cells. The treatment of DAPT significantly inhibited the activation of the Notch signaling pathway, as well as the progression of renal fibrosis.

  Interestingly, recent studies reported that PLK1 modulated the activation of the Notch signaling pathway in various diseases. Chhabra et al. indicated that PLK1‐mediated epithelial‐mesenchymal transition (EMT) changes in human melanoma may be interceded through phosphorylation of NUMB Endocytic Adaptor Protein (NUMB) and/or Notch signaling pathway activation. 36  Besides, Zhi et al. revealed that the knockdown of ubiquitin‐specific protease 24 (USP24) reduced the stability of PLK1 and consequently decreased the activity of NOTCH1, resulting in alleviating tumor progression. 37  Likewise, PLK2 was proved to be a regulator of the Notch signaling pathway. ALAFATE W's studies found that PLK2 overexpression attenuated temozolomide resistance in glioblastoma cell lines by destabilizing NOTCH1. 23  However, whether PLK2 could mediate fibrogenesis in DKD by activating the Notch signaling pathway is still elusive. In this study, we firstly investigated the interaction of PLK2 and NOTCH1 by molecular docking analysis and Co‐IP assay, followed by a rescue assay to verify that PLK2 accelerated renal fibrosis by regulating the activation of the Notch signaling pathway.

  Although our study provides crucial insights into the role of PLK2 in DKD, it is important to acknowledge limitations in our research. Firstly, the lack of mice with tubule‐specific deletion of PLK2 restrained us from further exploring the role of PLK2 in vivo. Secondly, the effect of the PLK2 inhibitor, ON1231320, should be studied in vivo and in vitro in order to ensure the therapeutic possibility of anti‐PLK2 in DKD. Additionally, due to resource constraints and experimental limitations, we were unable to examine the specific mechanisms by which PLK2 modulated the activation of the Notch signaling pathway, especially since PLK2 is located in the cytoplasm while NOTCH1 is a membrane receptor. Future research efforts should aim to address this limitation by conducting cell‐based experiments, such as yeast two‐hybrid assay or bimolecular fluorescence complementation assay. Besides, increasing evidence indicates that intracellular location is strongly associated with post‐translational modifications of proteins. Whether the translocation of PLK2 from the cytoplasm to the cell membrane is mediated by some kind of post‐translational modifications needs further investigation.

  Collectively, this research provides evidence that PLK2 is involved in the process of renal tubulointerstitial fibrosis through the Notch signaling pathway in diabetic kidney disease. This mechanism lays the groundwork for future therapeutic strategies for patients with DKD.


## AUTHOR CONTRIBUTIONS
  Jiayi Luo, Yaoming Xue, and Yijie Jia designed the research; Jiayi Luo, Haibin Xu, Cailin Su, Wenhui Dong, Manlu Xiao, and Nan Xiao performed the animal experiments; Jiayi Luo, Haibin Xu, and Nan Xiao performed the in vitro experiments; Jiayi Luo analyzed data and was a major contributor in writing the manuscript; Yaoming Xue and Yijie Jia gave a valuable and selfless guidance in the experimental process and article writing. All authors read and approved the final manuscript.


## FUNDING INFORMATION
  This work was supported by the National Natural Science Foundation of China (No. 82470855) and (No. 82070848) and the Natural Science Foundation of Guangdong (No. 2024A1515010811).


## DISCLOSURES
  The authors declare that they have no competing interests.


## N/A

## ETHICAL APPROVAL
  The animal study protocol was approved by the committee of the Laboratory Animal Center, Nanfang Hospital, Southern Medical University. All experimental procedures adhered strictly to the guidelines outlined in the National Institutes of Health Guide for the Care and Use of Laboratory Animals, thereby ensuring the welfare and ethical treatment of the animal subjects.


## CONSENT FOR PUBLICATION
  Not applicable.


## Supporting information

## DATA AVAILABILITY STATEMENT
  All data generated or analyzed during this study are included in this published article; they can also be requested from the corresponding author (xueyaoming999@126.com).


## ACKNOWLEDGMENTS
  Not applicable.