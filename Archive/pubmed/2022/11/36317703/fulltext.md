# SOX10 modulated SMARCA4 dysregulation alleviates DNA replication stress in cutaneous melanoma


## Abstract
  Cutaneous melanoma (CM) is the most fatal type of skin cancer with a high potency of metastasis, yet the treatment for metastatic melanoma remains limited. In this study, we are devoted to addressing the prognostic value and underlying mechanism of DNA damage repair‐related genes in CM. We utilized integrated bioinformatic approaches and machine learning models to identify a cluster of convergently expressed DNA damage repair‐related genes in melanoma. With multivariate Cox regression, SMARCA4 (also known as BRG1) was identified as an independent prognostic marker for melanoma patients. Yet the expression of SMARCA4 is not altered with the pathological staging or the metastasis condition. SMARCA4 is an essential ATPase subunit of the mammalian SWI/SNF complex. Mechanistically, we demonstrated that SMARCA4 could resolve DNA replication stress and guarantee the proliferation of melanoma cells. Furthermore, we predicted the binding of different transcription factors on the SMARCA4 promoter and unveiled the modulated expression of SMARCA4 by SOX10 in melanoma. Together, we performed integrated approaches to identify SMARCA4 as a promising prognostic marker for melanoma, which was transcriptionally regulated by SOX10 and promoted melanoma cell proliferation by ameliorating DNA replication stress.


## BACKGROUND
  Arising from the melanocytes, cutaneous melanoma is the most fatal type of malignant skin neoplasm, 1 ,  2  accounting for 75% of death cases in skin cancer. Meanwhile, as one of the most rapidly increasing types of cancer worldwide, melanoma cases were predominantly diagnosed in western populations. 3  Early staged melanoma is a curable disease with surgical interventions. 4  However, due to the lack of specific and sensitive diagnostic markers, metastasis was common in melanoma patients and their prognosis decreases dramatically. 5  Previous studies have unveiled the critical role of exosome, 6  AKT pathway 7  and immunology alterations 8  in the progression of melanoma, yet effective approaches for melanoma, especially for late‐staged patients, are still lacking. Therefore, screening for potent prognostic markers and druggable targets for melanoma is urgent.

  Reactive oxygen species (ROS) is primarily produced in mitochondria and is the most prevalent cause of oxidative DNA damage in cells. 9  Specifically, ROS features a high affinity to guanine and produces 8‐oxo‐dG, the most predominant form of oxidized nucleotides in cells. 10  Single‐stranded DNA was exposed during the S phase and becomes highly vulnerable to ROS, 11  leading to strand breaks in genome DNA. 12  And the unrepaired DNA strand breaks would activate different cell cycle checkpoints and cause cell cycle arrest. 13 ,  14  Therefore, cells are highly dependent on the DNA damage repair pathways to adequately deal with oxidized lesions and to maintain proliferation, especially in cancer cells.

  Cancer cells harbour frequent mutations in DNA damage repair‐related genes with high proliferation potential, which convergently causes the accumulation of oxidized lesions and strand breaks in the genomic DNA. 15 ,  16  To survive such replication stress, multiple DNA damage repair pathways are persistently activated during the S phase, especially with diverse gain‐of‐function mutations. 17  Specifically, melanoma cells feature activated DNA damage repair pathways, among which homologous recombination pathway (HR) and nucleotide excision repair pathway (NER) are typically activated during DNA replication. 18 ,  19 ,  20  Also, the mutations in the NER pathway could cause the collision of the replication fork and the termination of DNA replication during the S phase. 18 ,  21  Yet the detailed mechanism unveiling how NER pathway genes could prevent DNA replication stress and contribute to the proliferation of melanoma remains poorly understood.

  SMARCA4 (also known as BRG1) in the SWI1/SNF1 family is the central component of the SWI1/SNF1 complex with high helicase/ATPase activity. 22 ,  23  The alteration of the SWI/ SNF complex is generally considered the centre of chromatin remodelling and epigenetic modifications. 22  Besides, SMARCA4 is reported to be involved in the transcription of multiple downstream genes, such as EGFR signalling in colon cancer 24  and SREBP1c in lipid metabolism. 25  SMARCA4 also regulates gene expression 26  by binding with H3K27me3 modifiers and suppresses transcription‐associated genomic instability by recruiting TOP1. 27  More importantly, SMARCA4 could increase chromatin accessibility and promote the repair of double‐strand DNA damage via the NER pathway 28  and participate in the solution of R‐loop‐mediated transcription–replication conflicts in cells. 29  However, the crucial role of SMARCA4 in the elimination of replication stress in melanoma remains elusive.


## MATERIAL AND METHOD

### Data collection
  mRNA array data, DNA methylation data and clinical data of melanoma patients and other cancer types were acquired from the TCGA SKCM database (https://tcga‐data.nci.nih.gov/) and 3 GEO database (GSE22155, GSE50509 and GSE65904, https://www.ncbi.nlm.nih.gov). PAN‐Cancer expression patterns of SMARCA4 are acquired from the GEPIA database (http://gepia.cancer‐pku.cn/index.html). Gene expression of SMARCA4 in normal skin and Skin cutaneous melanoma were compared with the OncoDB tool (http://oncodb.org/).


### SC3 (Single Cell Consensus Clustering) unsupervised clustering
  Single‐cell consensus clustering (SC3) was carried out with the mRNA array data from the TCGA SKCM database. The corresponding script was acquired from Bioconductor (http://www.bioconductor.org/) and modified by the author.

  The dimension reduction with the tSNE method was achived with python and the script was acquired and modified from CSDN (https://blog.csdn.net/).


### Network analysis and Procrustes analysis
  The network analysis and Procrustes analysis were performed on the Tutools platform (https://www.cloudtutu.com/).

  Network analysis and Procrustes analysis were performed to analyse the correlation within a cluster of genes or compare the co‐occurrence patterns between mRNA and copy number variation in the TCGA SKCM database.


### Kaplan–Meier analysis
  Kaplan–Meier analysis was performed in this study to compare the overall survival (OS), disease‐specific survival (DSS) and disease‐free interval (DFI) in melanoma patients.

  Kaplan–Meier analysis was performed with GraphPad (https://www.graphpad.com/) to calculate the Hazard ratio and log‐rank significance in different groups of melanoma patients. Besides, Kaplan–Meier analysis was performed with SPSS to stratify patients concerning metastasis status in melanoma patients.

  The cut‐off value for all the Kaplan–Meier analyses in this article is defined by the median of its corresponding expression level. Gene expression higher than the cut‐off value is defined as the high‐expression group and vice versa.


### Multiple variate Cox regression
  Multiple variate Cox regression was performed with SPSS software (SPSS 22.0, https://www.ibm.com/cn‐zh/analytics/spss‐statistics‐software) to select independent factors for the prognosis of melanoma patients. The forward stepwise method was used in the multivariate Cox Regression model with p < 0.05 to enter and p < 0.10 to exit.

  Independent factors which are significant in predicting OS, DSS and DFI were selected and the risk score for OS and DFI were separately established with the multivariate Cox regression model in the melanoma patients.


### Heatmap and hierarchical clustering
  Heatmap with hierarchical clustering was achieved with R software (https://www.r‐project.org/). For Heatmap, the expression level of each gene was normalized to the median in each patient and the colour scale was normalized as indicated. Hierarchical clustering was performed with the Euclidean clustering method with complete linkage and optimized gene/sample order. For heatmaps describing the Pearson correlation between two genes, the Euclidean clustering was directly performed without normalization.

  Heatmap and the following hierarchical clustering enabled us to directly visualize and comprehend the expression pattern of a certain cluster of genes or samples.


### Correlation analysis and student's t‐test
  Correlation between two groups of samples (including Figures 2H and 5C, Figures S3F and S5D) was performed with SPSS and plotted with GraphPad. Linear regression was performed with GraphPad with 95% CI labelled.

  Student's t‐test (including Figures 3D–E, 4A,B,D,F–G, 5D–G, Figures S1C–E and S3B–E) was performed with GraphPad.


### Prediction of the transcriptional modulation of SMARCA4
  To further explore the potential transcriptional modulation of SMARCA4 in melanoma patients, we first acquired the DNA sequence of the SMARCA4 promoter (−2000 bp to −1 bp) in the UCSC database (http://www.genome.ucsc.edu/index.html). Then, we predicted the binding affinity of all the known human transcription factors listed in the JASPAR database (http://jaspar.genereg.net/)and the PROMO database (http://alggen.lsi.upc.es/recerca/frame‐recerca.html).

  Next, the transcription factors with at least 2 binding site <5% dissimilarly in the PROMO database and with a relative profile score >90% was selected as potential transcription factors for the modulation of SMARCA4. We then analysed the expression level of SMARCA4 and candidate transcription factors in 4 different databases with Pearson analysis.


### Cell culture
  Two melanoma cell lines, M14 and A375, were purchased from the National Collection of Authenticated Cell Culture in the Chinese Academy of Sciences. Cells were cultured in DMEM supplemented with 10% FBS and 1% penicillin and streptomycin at 37 degrees in a humidified chamber with 5% CO2.


### Cell proliferation assay and clonogenic assay
  For the proliferation assay, cells were seeded in the 96‐well plate at 2000 cells/well and cultured for 5 days. The proliferation curve was plotted with CCK8 (Cell Counting Kit‐8).

  For the clonogenic assay, cells were depleted of SMARCA4 with specific siRNA transfection. 24 h after transfection, cells were re‐seeded into the 6‐well plate at 200 cells/well at triplicates and cultured for 14 days. Cells were stained with crystal violet and manually counted under the microscope.


### siRNAs, Constructs and transfections
  siRNAs sequences used in this study were reported earlier 24 ,  30  and were purchased from Shanghai Genomeditech. siRNA transfection was performed with JetPRIME Polyplus (Polyplus114‐01) according to the manufacturer's instructions and the siRNA efficacy was measured 72 h post‐transfection.

  siRNA sequences are as follows:siSMARCA4 s1: 5′‐ UCGCUUUG GUUCGCAAAUC3’.

  siSMARCA4 s2: 5′‐ UUCCUCCUCAUUCAGGUCC‐3’.

  siSOX10 s1: 5′‐ GAACGAAAGUGACAAGCGC‐3’.

  siSOX10 s2: 5′‐ GCGGGAAGCCUCACAUCGA‐3′.


### Antibody and reagents
  The following primary antibodies were used:SMARCA4PA5‐40697RbThermoChIPγH2AX9718 SRbCSTIF

  The following secondary antibodies were used:Alexa Fluor® 555 anti‐Rabbitab150078GoatAbcamIF


### Immunofluorescence and EdU staining
  Immunofluorescence was performed as previously described. 30  Briefly, cells were fixed with 4% PFA and permeabilization with 0.1% Triton, then cells were washed twice with PBS and blocked for 1 h in 3% BSA. Cells were incubated with indicated primary antibody (diluted in 3% BSA) and the corresponding secondary antibody, followed by washing with PBS. Finally, cells were counterstained with DAPI before image acquisition.

  For the γH2AX‐EdU colocalization experiment, cells were first transfected with specific siRNAs for 72 hours before EdU (C0081S, Beyotime) was added to the cells. After incubation with 1:1000 EdU for 30 min, cells were fixed with 4% PFA, followed by cell permeabilization, blocking, and incubation with primary/secondary antibodies. Last, the EdU‐Click reaction is performed according to the manufacturer's protocol. After 5 times washing with PBS, cells were counterstained with DAPI, and images were acquired. The colocalization results were analysed with Cell profiler (https://cellprofiler.org/).


### Chromatin immunoprecipitation (ChIP)
  ChIP was performed with a Chromatin Immunoprecipitation kit (Merck Millipore, MA, USA) per the manufacturer's instructions. Briefly, cells were cultured in a 15 cm dish till 80% confluency and were crosslinked with 550ul 37% formaldehyde (1% final concentration) for 10 min at room temperature. Cells were harvested and the nuclear was isolated and resuspended in SCW buffer. After sonication on ice, samples were centrifuged and the supernatant was collected. At the same time, Magna ChIP Protein A/G Magnetic Beads were washed and incubated with SOX10 antibody (Thermo Fisher, PA5‐40697) or IgG control. Then, samples were immunoprecipitated with antibody‐labelled magnetic beads overnight. Samples were repeatedly washed and incubated with Elution Buffer with proteinase K.

  Immunoprecipitated DNA was collected, and the enrichment of the DNA template was analysed by conventional quantitative PCR, using primers specific for SMARCA4 promoter (targeting the ‐586 bp to −489 bp region) and negative control primers (targeting the ‐431 bp to −331 bp region). Primers sequences were listed as follows:

  ChIP_1442_F: 5′‐ TCCTTCCCCACTAGACCGAG −3’.

  ChIP_1442_R: 5’‐GCAAAACTTCCCAAGTGCCA −3’.

  ChIP_Neg_F: 5′‐ CAGGTCAGGGATCAAAGCGG −3’.

  ChIP_Neg_R: 5′‐ TAGGAACCCTGGACCGTAGG −3′.


### Quantitative polymerase chain reaction (qPCR)
  Qiagen RNA isolation kit and reverse transcriptase were used to extract total RNA from tissues and cultured cells and to synthesize complementary DNA.

  qPCR was performed using SYBR Premix Ex Taq (Takara) in a Bio‐Rad CFX‐96 Real‐Time PCR detector, using GAPDH as the internal control. The stability of GAPDH was examined in Figure S5 E. The Primers used in this study are as follows:

  h_ GAPDH _F: 5′‐ GCCATGTAGACCCCTTGAAGAGC‐3′;

  h_ GAPDH _R: 5′‐ ACTGGTTGAGCACAGGGTACTTTAT‐3′.

  h_ SMARCA4 _F: 5′‐ CAGATCCGTCACAGGCAAAAT −3′;

  h_ SMARCA4 _R: 5′‐ TCTCGATCCGCTCGTTCTCTT −3′.


### Dual‐luciferase reporter assay
  Dual‐luciferase reporter assay was performed according to the manufacturer's protocol (Beyotime, RG027). Briefly, cells were co‐transfected with firefly luciferase control plasmid along with renilla reporter plasmid at a ratio of 10:1. After 48 h, cells were harvested and lysed in the lysis buffer. The activity of luciferase was detected by the Dual‐Luciferase Reporter Assay System. The results were normalized to the renilla activities.

  SMARCA4 promoter regions (−600 bp to −300 bp) used in the study:

  GTCCTCCTTCCCCACTAGACCGAGGGCTCCACGGCGGCTGGGACACAGTAGCAGATCAATAAATATTTGCTAAGCTAATTAATGGCACTTGGGAAGTTTTGCAGAGAAGGCGGCCACGGTCGGGCCCCGCCTTGCCTCCCCAAATAGGCCTCGCCGCCCCAGGTCAGGGATCAAAGCGGTTCCCAGGCGCGCCCTTGGCCCGCGGGAAACCACTGCCCGGTCTTGGTCCAGGCGGCCCGTCCTACGGTCCAGGGTTCCTATTTCCGAGCCTCAGGGACCTCCTTTCCCCACGGACCCCAC.

  Binding domain depleted SMARCA4 promoter (−600 bp to −300 bp) used in the study:

  GTCCTCCTTCCCCACTAGACCGAGGGCTCCACGGCGGCTGGGTAGCAGATCAATAAATATTTGCTAAGCTAATTAATGGCACTTGGGAAGTTTTGCAGAGAAGGCGGCCACGGTCGGGCCCCGCCTTGCCTCCCCAAATAGGCCTCGCCGCCCCAGGTCAGGGATCAAAGCGGTTCCCAGGCGCGCCCTTGGCCCGCGGGAAACCACTGCCCGGTCTTGGTCCAGGCGGCCCGTCCTACGGTCCAGGGTTCCTATTTCCGAGCCTCAGGGACCTCCTTTCCCCACGGACCCCAC.


## RESULTS

### Melanoma patients harbour distinct patterns of DNA damage repair‐related genes
  To comprehend how DNA damage participates in the remodelling of distinct features of melanoma cells, we performed unsupervised clustering with all DNA damage repair‐related genes in melanoma patients from the TCGA database (Figure 1A). And melanoma patients were categorized into 2 to 4 clusters with the single cell consensus clustering (SC3) method and patients showed better consistency when clustered into 3 groups (Figure 1A–B). In concert with this, we noticed only Cluster 3 showed significantly reduced overall survival when divided into 3 groups (Figure 1C). Also, both the disease‐specific survival (DSS) and the disease‐free interval (DFI) were reduced in Cluster 3 patients (Figure S1A–B).

  We further compared the expression level of DNA damage repair genes and the clinical features of Cluster 3 melanoma patients. We noticed that Cluster 3 patients were synergistically overexpressed in a cluster of DNA damage repair‐related genes, defined as Cluster 3 marker genes. However, there is no significant difference in the metastasis condition (Figure 1D), age (Figure S1C), Breslow depth value (Figure S1D) and mitotic cell counts (Figure S1E). Also, the distribution of pathological staging (Figure S1F), radiation therapy condition, pharmaceutical therapy condition, neoadjuvant treatment condition, additional surgery condition (Figure S1G), Clark value level (Figure S1H) or the types of new tumour events (Figure S1I) were not altered in Cluster 3 melanoma patients.


### Identification of prognostic markers in Cluster 3 marker genes in melanoma
  We further plotted the expression level of Cluster 3 marker genes in melanoma patients and selected the top 38 synergistically expressed genes with Pearson correlation >0.3 (Figure S2A–B). Higher DNA damage repair level was closely correlated with the prognosis of melanoma patients (Figure 2A–B and Figure S2C–D) and differentially expressed Cluster 3 marker genes were selected (Figure S2 E). Differentially expressed Cluster 3 marker genes showed similar expression patterns (Figure 2C) and consistency to copy number variation (Figure 2D).

  A multivariate Cox regression model was used to avoid bias from the co‐linearity of Cluster 3 marker genes. The result showed that SMARCA4, XAB2 and NUDT1 were potent markers for the overall survival (OS) and disease‐specific survival (DSS) (Figure 2E–F) and SMARCA4 was shown to correlate with XAB2 and NUDT1 expression in melanoma patients (Figure 2G). Besides, SMARCA4 was a promising prognostic marker for the disease‐free interval (DFI) in melanoma patients (Figure S2 E) and was significantly elevated in melanoma patients, compared with normal skin tissues (Figure 2H).


### SMARCA4 correlates with the proliferation potential of melanoma patients
  To decipher potent prognostic markers for melanoma, we performed the Kaplan–Meier analysis and observed only SMARCA4 could accurately predict the unfavourable prognosis of melanoma patients (Figure 3A and Figure S3A). Therefore, we were devoted to unveiling the prognostic value and the biological function of SMARCA4 in melanoma.

  SMARCA4 is generally overexpressed in multiple cancer types compared to the non‐tumour control (Figure 3B) and the predicted unfavourable outcome in the GEO database (GSE65904, Figure 3C). The expression of SMARCA4 is not altered after dabrafenib or vemurafenib treatment in melanoma patients (Figure 3D) and is highly increased in proliferative melanoma and ki67 positive (>30%) melanoma (Figure 3 E). But the expression level of SMARCA4 is not changed with the BRAF status, TNM staging, Clark value level, metastasis status or Breslow depth value (Figure S3B–F).

  Further analysis revealed that SMARCA4 especially correlated with favourable prognosis in metastatic and highly proliferative melanoma patients, but not in primary melanoma patients (Figure 3F–H). Also, SMARCA4 mutation and reduced SMARCA4 copy number predicted favourable prognosis in melanoma patients (Figure S4A–B).


### SMARCA4 resolves DNA replication stress in melanoma cells
  To better elucidate the biological function of SMARCA4 in melanoma, we examined the proliferation ability and the clonogenic ability of M14 and A375 cells. The result showed reduced proliferation and clonogenic ability in SMARCA4‐depleted melanoma cells (Figure 4A–B).

  Replication stress features increased DNA replication damage, cell cycle arrest (typically in the S phase) and increased apoptosis in cells. To explore the underlying mechanism of SMARCA4, the DNA replication fork was labelled with EdU, and DNA damage sites were labelled with γH2AX in cells. As a result, SMARCA4‐depleted M14 and A375 cells showed significantly reduced replication (Figure 4C–D) and increased DNA damage by γH2AX staining (Figure 4 E–F). Increased colocalization of EdU and γH2AX was observed in SMARCA4 depleted cells, suggesting increased DNA damage at the replication site (Figure 4 E,G). Flow cytometry results showed a significant accumulation of S phase cells (Figure 4H), but not necrotic/apoptotic cells after SMARCA4 depletion (Figure S4C).


### SOX10 transcriptionally regulates SMARCA44 expression in melanoma
  SMARCA4 gene was highly methylated in the TCGA database (Figure S5A) and cg08151828, cg26967868 and cg23963476 showed the highest correlation with SMARCA4 mRNA level (Figure S5B), among which cg23963476 is negatively correlated with SMARCA4 and correlates with the survival of melanoma patients (Figure S5C–D).

  To further explore the upstream regulation of SMARCA4, we predicted the binding of all the listed transcription factors in the PROMO database and JASPAR database. Transcription factors with <5% in dissimilarity or >90% in relative profile score were shown in Figure 5A–B. Then, we analysed the correlation between the expression level of SMARCA4 and separate transcription factors in the TCGA database with Pearson regression. Pearson regression results from 4 different melanoma databases showed that SOX10 and USF2 were positively correlated with the expression of SMARCA4, yet TBX15 and ETS2 were negatively correlated with the expression of SMARCA4 (Figure 5C). Both SOX10 and TBX15 were correlated with the unfavourable prognosis of melanoma patients, and SOX10 positively correlates with SMARCA4 (Figure 5D).

  SOX10 is a well‐established transcription factor, whose function has been discussed in multiple cancer types 31 ,  32  and is critical for the proliferation of melanoma. 33  Meanwhile, SMARCA4 was reported to regulate SOX10 expression or function as a co‐activator of SOX10 in melanoma. 34 ,  35 ,  36  Here, we hypothesized that SOX10 could transcriptionally modulate SMARCA4 expression and maintain melanoma cell proliferation. SOX10 expression was depleted with specific siRNAs and the transcription of SMARCA4 was dramatically suppressed (Figure 5 E–F). Also, the ChIP experiment in M14 and A375 cells suggested that SOX10 could specifically bind to the promoter region of SMARCA4 (Figure 5G). Consistently, dual‐luciferase reporter assay showed the transcription of SMARCA4 is greatly suppressed by SOX10 depletion (Figure 5H).


## DISCUSSION
  Melanoma is a fatal skin malignancy prevalently diagnosed in western populations. 1 ,  2  So far, the treatment for metastatic melanoma is limited and the prognosis of melanoma patients remains unsatisfactory. 37  The pathological function of multiple DNA damage repair‐related genes, especially the NER‐related genes, in the carcinogenesis and the progression of melanoma has been suggested, 38  yet how SMARCA4 promotes the proliferation of melanoma cells has not been discussed.

  With unsupervised clustering with machine learning, we managed to divide melanoma patients into different clusters. Interestingly, we observed that the Cluster 3 patients showed the worst prognosis, independent of the metastasis status of melanoma patients (Figure 1 and Figure S1). By looking into the expression pattern of marker genes in Cluster 3 patients, we set up a multivariate Cox regression model and selected SMARCA4 as the potential prognostic marker for melanoma (Figure 2 and Figure S2).

  The expression of SMARCA4 was elevated with the proliferation potential of melanoma and effectively predicted the prognosis of metastatic and proliferative melanoma patients (Figure 3 and Figure S3). Consistently, somatic mutations and decreased copy number of SMARCA4 predicted a tendency towards the favourable outcome of melanoma patients (Figure S4), indicating SMARCA4 was involved in the proliferation of melanoma.

  To further explore the function of SMARCA4, we compared the proliferation and clonogenic ability of SMARCA4‐depleted melanoma cells. As a result, we showed significantly increased DNA replication damage and suppressed DNA replication after SMARCA4 depletion (Figure 4), which suggests that SMARCA4 functions to eliminate DNA replication damage and maintains cell proliferation.

  To explore the potential upstream regulation network of SMARCA4, we predicted the binding affinity of all the potential transcription factors with the promoter of SMARCA4 in the PROMO and JASPAR database. And SOX10 was predicted to bind to the promoter region of SMARCA4 and correlated with SMARCA4 across 4 different databases. Interestingly, multiple studies have reported that SMARCA4 could directly modulate SOX10 expression 34 ,  36  or function as a co‐activator of SOX10 in melanoma. 35  However, whether SOX10 could directly modulate SMARCA4 transcription remains unknown. Eventually, the binding of SOX10 at the promoter of SMARCA4 was validated with ChIP‐qPCR and its effect in promoting SMARCA4 transcription was validated with dual luciferase assay (Figure 5).

  Together, we described the overall landscape of DNA damage repair in melanoma and clustered melanoma patients with distinct prognoses. We demonstrated the expression pattern and the clinical relevance of SMARCA4 and unveiled its physiological function in resolving DNA replication damage. Lastly, we predicted and validated the potential transcription factors for SMC4 expression. And the limitation of the study is that the study was largely based on computational results. Therefore, further exploration into the mechanisms and further validation with in vitro/in vivo models and melanoma patients is needed. While it seems a long way to find a promising approach for melanoma, we believe SMARCA4 could be a promising target for the treatment of melanoma patients.


## AUTHOR CONTRIBUTIONS
  Xiangjian Fang: Conceptualization (equal); data curation (equal); formal analysis (equal); investigation (equal); methodology (equal); validation (equal); visualization (equal); writing – original draft (equal); writing – review and editing (equal). Zhiyi Wei: Conceptualization (equal); formal analysis (equal); investigation (equal); methodology (equal); visualization (equal); writing – original draft (equal); writing – review and editing (equal). Juntao Cheng: Conceptualization (equal); data curation (equal); formal analysis (equal); project administration (equal); supervision (equal); validation (equal); writing – original draft (equal); writing – review and editing (equal). Keqiang Rao: Formal analysis (equal); methodology (equal); writing – review and editing (equal).


## CONFLICT OF INTEREST
  The authors declare that they have no competing interests.


## Supporting information

## DATA AVAILABILITY STATEMENT
  The datasets generated and/or analysed during the current study are available in the TCGA SKCM database (https://tcga‐data.nci.nih.gov/) and GEO database (https://www.ncbi.nlm.nih.gov).


## ACKNOWLEDGEMENT
  We thank Yuan Sun from Shanghai Jiao Tong University, School of Mathematics, for the discussion and design of the research.