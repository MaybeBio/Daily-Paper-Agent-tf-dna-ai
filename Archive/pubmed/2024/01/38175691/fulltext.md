# Identification of aging-related genes in diagnosing osteoarthritis via integrating bioinformatics analysis and machine learning


## Abstract
  Background: Osteoarthritis (OA) is one of the main causes of pain and disability in the world, it may be caused by many factors. Aging plays a significant role in the onset and progression of OA. However, the mechanisms underlying it remain unknown. Our research aimed to uncover the role of aging-related genes in the progression of OA.

  Methods: In Human OA datasets and aging-related genes were obtained from the GEO database and the HAGR website, respectively. Bioinformatics methods including Gene Ontology (GO), Kyoto Encyclopedia of Genes Genomes (KEGG) pathway enrichment, and Protein-protein interaction (PPI) network analysis were used to analyze differentially expressed aging-related genes (DEARGs) in the normal control group and the OA group. And then weighted gene coexpression network analysis (WGCNA), the least absolute shrinkage and selection operator (LASSO) regression, and the Random Forest (RF) machine learning algorithms were used to find the hub genes.

  Results: Four overlapping hub genes: HMGB2, CDKN1A, JUN, and DDIT3 were identified. According to the nomogram model and receiver operating characteristic (ROC) curve analysis, four hub DEARGs had good diagnostic value in distinguishing normal from OA. Furthermore, the qRT-PCR test demonstrated that HMGB2, CDKN1A, JUN, and DDIT3 mRNA expression levels were lower in OA group than in normal group.

  Conclusion: Finally, these four-hub aging-related genes may help us understand the underlying mechanism of aging in osteoarthritis and could be used as possible diagnostic and therapeutic targets.


## INTRODUCTION
  Osteoarthritis (OA) is one of the main causes of pain and disability among the elderly in the world. With the population aging, this disease burdens increasing. The cause of OA is not completely clear. Risk factors include age, obesity, sex, injury, and heredity [1]. More evidence suggests that OA is a disease involving the whole joint, including structural changes in hyaline articular cartilage, subchondral bone, synovium, ligaments, articular capsule, subpatellar fat pad, and muscles around the joint [2]. The traditional diagnosis of OA depends on patients’ symptoms and radiography evaluation, however, there are limited value in the detection of early OA. In the past few years, more and more researchers have devoted themselves to finding biomarkers that can be used for early diagnosis and treatment of OA. Although the practice process is full of challenges, its clinical application is a relatively distant prospect [3].

  The increase of senescent cells in diverse tissues is one of the markers of aging. The senescent cells still retain their activity and metabolic capabilities despite losing their ability to divide. It has an effect on the surrounding normal tissues and cells by secreting a large number of pro-inflammatory cytokines, chemokines, Matrix metalloproteinases (MMPs), and angiogenic factors, which form the senescence-associated secretory phenotype (SASP) [4, 5]. In some animal disease model studies, the application of senolytics, a class of drugs that target to induce senescence cell death (quercetin and dasatinib et al.), and senomorphics, a type of SASP inhibitor (apigenin and resveratrol et al.) had achieved satisfactory results and were progressing to the clinical trial stage [6, 7]. As a result, the elimination of senescent cells is considered to be a promising treatment for OA [8].

  Bioinformatics and machine learning analyses are critical for understanding the molecular mechanisms of disease and screening key genes [9]. In this study, we screened the differentially expressed aging-related genes (DEARGs) in the normal control group and the OA group by bioinformatic analysis including differential gene analysis and WCGNA, and then LASSO and the Random Forest (RF) algorithm, the machine learning were employed to identify diagnostic biomarkers in OA progression, thereby providing new possibilities for OA therapy.


## RESULTS

### Identification of DEARGs in OA
  The study flowchart was depicted in Figure 1. Differential gene analysis was performed using 307 aging-related genes in 20 cases of OA cartilage tissues and 18 cases of normal cartilage tissues, with an adjusted p-value of 0.05 and an FC absolute value of >1 as the standard. There were 42 DEARGs in total, with 22 up-regulated genes and 20 down-regulated genes. These DEARGs between the OA group and control group are displayed in the heat map and volcano map (Figure 2A, 2B).


### Functional enrichment and protein-protein interaction analysis of DEARGs
  GO and KEGG enrichment analyses were performed utilizing the R software to identify the potential biological functions of DEARGs. We obtained 1037 and 95 terms for the GO and KEGG enrichment analyses, respectively, based on the screening criterion of adjusted P-value 0.05 (Supplementary Tables 1, 2). DEARGs were primarily involved with aging, response to lipopolysaccharide, and response to molecules of bacterial origin (Biological Process, BP). RNA polymerase II transcription regulator complex, transcription regulator complex, cyclin−dependent protein kinase holoenzyme complex (Cellular Component, CC). DNA−binding transcription activator activity RNA polymerase II−specific, DNA−binding transcription activator activity, DNA−binding transcription factor binding (Molecular, Function, MF) (Figure 3A). The most significant KEGG pathways included Transcriptional misregulation in cancer, Human T−cell leukemia virus1 infection, MAPK signaling pathway, Cellular senescence, and Cell cycle, The top five KEGG pathways are shown in Figure 3B. The PPI network uncovered the close interactions between proteins encoded by the DEARGs (Figure 3C).


### Establishment of a co-expression network
  The WGCNA algorithm was used to identify co-expressed genes and modules based on the expression profiles of all genes. The soft-threshold power of = 4 (R2 = 0.87; slope = 1.01) was adopted to ensure that the network was scale-free (Figure 4A, 4B). Then, the co-expression modules in the network were identified by the “cutree Dynamic” function, and 9 gene modules were obtained. The correlations of the above-mentioned modules with OA and healthy controls were presented with heat maps, with green (cor = 0.9; P = 1e-14) and greenyellow (cor = −0.69; P = 2e-06) modules showing the strongest positive and negative connection with OA, respectively (Figure 5A–5C). In the green module we could gain 462 key genes based on the screening criteria (|GS|> 0.60;|MM|> 0.70). As a result, the 462 key genes in the green module were studied further. Finally, 13 intersecting genes were discovered in the green module between 42 DEARGs and 462 key genes. (Figure 5D). The intersection genes were as follows: TOP2A, TFDP1, ELN, IGFBP3, EFEMP1, and NGF. JUN, ARNTL, CDKN1, AMXI1, DDIT3, HMGB2, and IRS2.


### Identification of candidate Hub aging-related genes via machine learning
  Subsequently, the LASSO regression and RF machine learning algorithms were further applied to screen for candidate aging-related hub genes, the LASSO regression algorithm identified six candidate genes (Figure 6A, 6B), RF algorithm ranked each gene based on gene importance (Figure 6C, 6D). The intersection of six genes from LASSO and the top five most important genes from the RF was visualized by a Venn diagram. Finally, the four intersectional aging-related biomarker genes we obtained are as follows: JUN, CDKN1A, DDIT3, and HMGB2 (Figure 6E).


### Hub aging-related genes expression levels
  The expression levels of the four hub genes were validated by using box plots. The results of the training set GSE114007 revealed that the expression levels of HMGB2, CDKN1A, JUN, and DDIT3 were significantly lower in OA samples than in normal samples (p < 0.001) (Figure 7A). To verify the reliability of the result, we used an external data set GSE169077 to further validate the expression levels of the four hub genes (Figure 7B). Consistent with the training set results, the expression levels of HMGB2, CDKN1A, and DDIT3 were significantly lower in OA samples than in normal samples (p < 0.01). However, compared with normal samples, although the expression levels of JUN were lower in OA, there was no statistical difference (P > 0.05) (Figure 7B).


### Hub aging-related genes diagnostic value in OA and normal samples
  We chose four hub aging-related genes as the final risk prediction model for OA and built the corresponding nomogram to demonstrate the diagnostic value of these hub genes. The nomogram score was used to predict the possibility of suffering from OA (Figure 8A). The calibration curve indicated that nomogram model performed very well in predicting OA (Figure 8B). Also, the DCA indicated the nomogram model has a high clinical application value (Figure 8C). Additionally, ROC curve analysis aims to explore the sensitivity and specificity of nomogram and individual genes in the diagnosis of OA. In the training set GSE114007, the area under the curve (AUC) value of 1.000 for the nomogram was obtained. In the prediction of OA, the AUC values for HMGB2, CDKN1A, JUN, and DDIT3 were 0.986, 0.975, 0.972, and 1.000, respectively (Figure 8D). In the validation set GSE169077, we obtained similar results indicating that all hub aging-related genes and nomogram have good diagnostic values (Figure 8E).


### RT-PCR validation of the 4 Hub genes
  The results indicated that the relative mRNA expression levels of four hub aging-related genes including HMGB2, CDKN1A, and JUN were consistent with the results of the previous analysis. The DDIT3 showed no statistically significant difference (Figure 9).


## DISCUSSION
  OA may cause by many factors, including mechanical overload, low-grade chronic inflammation, oxidative stress, and cell senescence [5, 10–12]. Cell senescence is an important sign of aging that is characterized by permanent cell cycle arrest and SASP release, destroying the extracellular matrix and affecting cell metabolism, inducing senescence of normal cartilage and synovial cells, and aggravating OA [13–15].

  A series of studies on the role of aging-related genes in tumors have been conducted in recent years, but there have been few studies on non-neoplastic aging-related diseases such as idiopathic pulmonary fibrosis, Alzheimer’s disease, atherosclerosis, and so on [16–19]. However, while OA is one of the most common aging-related diseases, it is unclear that the role of aging-related genes in OA progression.

  More and more evidence supports that there is a close link between aging and OA. For example, the removal of local senescent cells alleviates the occurrence of traumatic OA and is beneficial to the repair of tissue injury [20]; YAP or FOXD1 reduces cellular senescence in local bone joints and contributes to creating a chondrogenic environment [21]; Up-regulation of MFG-E8 protects against OA by targeting chondrocyte senescence and inhibiting NF-κB pathway [22], and miR-29b-5p alleviates OA via inducing a decline in catabolic enzymes and senescence-related genes and a rising in cartilage ECM synthesis [23]. These findings suggest that senescence plays a vital role in the progression of OA. In this study, we use bioinformatics and machine learning methods to investigate the role of senescence-related genes in OA, as this may provide new ideas for regulating cell senescence and alleviating OA.

  We downloaded and analyzed OA patients’ sequencing data from the GEO database. The first 307 aging-related genes were extracted. 42 DEARGs filtered in R using the limma package were crossed with key module genes in WGCNA to yield 13 important genes, and then four hub aging-related genes: HMGB2, CDKN1A, JUN, and DDIT3 were screened using LASSO regression and RF machine learning algorithm. The diagnostic ability of four hub DEARGs to OA was validated using a nomogram and ROC curve based on an external data set. Finally, the qRT-PCR method was used to confirm the credibility of the results.

  The high-mobility group box 2 (HMGB2) protein is a chromatin-binding protein that can increase protein binding to chromatin and regulate transcription, DNA damage, and repair [24]. Accumulating research has demonstrated that HMGB2 plays a significant role in controlling cell senescence and aging-related disorders, such as orchestrating the chromatin landscape of SASP gene loci. This suggests that part of HMGB2’s function in regulating aging may be through SASP secretion inhibition [25]. HMGB2 Downregulation Promotes Cellular Senescence in Microvascular Endothelial Cells [26]. In articular cartilage, HMGB2 is mainly distributed in the superficial zone, the expression of HMGB2 decreases with aging. OA occurs earlier and more severely in HMGB2 gene deficiency mice [27]. These reports are consistent with the results of our study.

  The CDKN1A gene encodes the cyclin-dependent kinase inhibitor p21/WAF1/CIP1/CDKN1A, a mainly transcriptional target of p53. It can inhibit cell cycle progression and cause cell cycle arrest by inactivating cyclin-dependent kinase (CDK) [28, 29]. The p21 also shows a significant expression in normal non-proliferating adult chondrocytes, which indicated it plays an important role in the chondrocyte. Indeed, according to reports, the down-regulation of p21 decreased ACAN expression and increased MMP13 expression through STAT3 phosphorylation in the cartilage tissue. CDKN1A-deficient mice are susceptible to inflammation-related OA [30–32]. In this study, compared with the normal group, the expression of p21 was significantly down-regulation in OA. It might well be one reason or at least one mediator of the “de-blocking” of cell cycle progression in OA chondrocytes. In addition, p21 is mainly activated in the early stage of induced senescence, and p16 is necessary to maintain cellular senescence [33–35].

  The JUN is the transcription factor subunit of activating protein-1 family (AP-1). The exact involvement of AP-1 in osteoarthritis is unknown [36]. Previous research has demonstrated that JUN plays an important function in regulating cell proliferation and apoptosis [37]. JUN was able to suppress p53 gene transcription, and Jun knockout mouse embryonic fibroblasts (MEF) increased the expression of p53, resulting in severe proliferation deficiency and early senescence [38, 39]. The Jun NH2-terminal kinase (JNK) pathway may contribute to the regulation of TGF-β-mediated biological responses [40]. Interestingly, recent studies in the intervertebral disc have found that-Jun can up-regulate the expression of TGF-β, TIMP-3, and COL2A1 mRNA and protein while inhibiting the expression of inflammatory factors, such as IL-1β and TNF-α. Therefore, delaying intervertebral disc degeneration [41]. TGF-β deficiency could be susceptible to osteoarthritis [42]. JUN may regulate the development of OA by regulating TGF- β signal transduction. The down-regulation of JUN may be an important factor in promoting the development of OA in this study. However, more studies are still needed to fully reveal the roles of JUN in OA.

  DNA damage-inducible transcript 3(DDIT3), also known as C/EBP homologous protein (CHOP) is an endoplasmic reticulum (ER) stress marker [43]. DDIT3/CHOP is activated in response to cellular stressors such as DNA damage, ER stress, cell cycle arrest, and apoptosis [44]. Previous research in mice and ATDC5 chondrocytes has demonstrated that DDIT3 plays a functional role in chondrocyte metabolism [45]. In the early stages of OA, decreasing ER stress protein (CHOP) production can ameliorate OA caused by ER stress [46]. A recent study, however, has shown that DDIT3/CHOP can promote autophagy in ATDC5 chondrocytes [47]. In the present study, compared to the normal group, DDIT3 expression was down-regulated in advanced osteoarthritis, we hypothesized that the decreased autophagy end of osteoarthritis could be connected to the downregulation of DDIT3 expression. This must be demonstrated by further animal experiments.

  In general, this study obtained four hub DEARGs via combining bioinformatics analysis and two machine learning algorithms. These genes were shown by the nomogram model to have good diagnostic value for OA, and this was confirmed in another data sets. In addition, qRT-PCR analysis revealed that the expression of four genes was down-regulated in the OA group compared to the normal group, suggesting that these genes may be potential targets for therapeutic intervention.

  However, the current study has certain limitations. To begin, our findings are based on public datasets containing a small number of patients. Second, we started with a small number of clinical samples to validate these ARGs identified by the model. More clinical samples, basic experiments, and molecular processes for this signature must be validated in future investigations.


## CONCLUSION
  This study identified 4 hub DEARGs (HMGB2, CDKN1A, JUN, and DDIT3) associated with OA. These genes could be served as potential therapeutic targets for OA. However, more experimental studies are required to confirm its role in OA.


## MATERIALS AND METHODS

### Data download and processing
  A total of 307 aging-related genes were downloaded from the Human Ageing Genomic Resources (HAGR) (https://genomics.senescence.info/genes/index.html) [48], the detailed information of genes is listed in Supplementary Table 3. The original sequencing data of GSE114007 were downloaded from the Gene Expression Omnibus (GEO) database, which served as the training dataset. Expression profile data consisted of 18 normal and 20 OA knee cartilage tissue samples. The GSE169077, which as the validation dataset contains 5 normal and 6 OA knee cartilage tissue samples, is based on the GPL96 platform (Affymetrix Human Genome U133A Array). First, the platform annotation information was downloaded to match gene probes to gene names. When numerous probes identified the same gene, the mean expression was determined, and when a gene was expressed in all samples at 0, the gene was eliminated. The data were then normalized using the “quantile normalization” algorithm in the R software “limma” package’s “normalizeBetweenArrays” function.


### Differential expression analysis of aging-related genes
  Differentially expressed aging-related genes (DEARGs) were presented between normal and osteoarthritis samples by using the limma software package [49]. The DEARGs satisfied an adjusted P value < 0.05 and |log2-fold-change| > 1. The “heatmap” and “ggplot2” software packages of R were used to draw heat maps and volcano maps.


### Gene ontology, pathway enrichment and PPI network analysis of DEARGs
  We performed GO functional enrichment and KEGG pathway enrichment analysis on DEARGs using the “Clusterprofiler” R package [50–52]. The STRING database (https://string-db.org/) was used to observe the PPI network between the DEARGs [53].


### Weighted gene co-expression network analysis (WGCNA)
  Weighted gene co-expression network analysis (WGCNA) is an algorithm that may identify co-expressed gene modules of significant biological value and investigate the association between gene networks and diseases. The dataset was utilized for weighted co-expression network construction using the “WGCNA” package for R to choose the best soft threshold (β) using the “pickSoftThreshold” function. The matrix data were converted into an adjacency matrix, which was then transformed into a topological overlap matrix (TOM) and the corresponding dissimilarity (1-TOM), which were separated into different modules based on similarly expressed genes and represented by different colors. The expression profile of each module was represented by a module eigengene (ME), and the correlation between each ME and clinical characteristics was calculated [54].


### Identification of potential biomarkers in normal and OA
  Two machine learning algorithms were used to further screen candidate genes for OA diagnosis. The DEARGs and genes from key modules were intersected, and then the least absolute shrinkage and selection operator (LASSO) and Random Forest (RF) were employed to screen the diagnostic genes. The “glmnet” package in R was used to perform LASSO, a regression analysis algorithm that applies regularization to variable selection [55, 56]. RF is a popular machine learning algorithm that is widely used in bioinformatics analysis to screen important genes, and it can be accomplished by using the “randomForest” package in R software [57]. Overlapping genes resulting from two algorithms as hub aging-related genes in OA diagnosis.


### Identification of Hub aging-related genes expression levels and diagnostic model construction
  Hub gene expression levels in healthy and OA individuals were assessed with the help of box plots. Hub aging-related genes were incorporated to construct a nomogram as a diagnostic model via using the “rms” package in R software, nomogram construction is critical for clinical OA diagnosis [58]. The predictive ability and clinical practicability of the nomogram model were evaluated by calibration curve and decision curve analysis (DCA), respectively [59]. Receiver operating characteristic (ROC) curves were plotted using the “pROC” packages of R to assess the levels of hub aging-related genes distinguishing between healthy and OA individuals, Furthermore, the expression levels and diagnostic value of the hub aging-related genes were validated with a separate external data set GSE169077.


### Patients’ samples
  The human cartilage samples were obtained from ten OA patients who underwent total knee arthroplasty and the normal cartilage samples were collected from six patients with anterior cruciate ligament rupture. All patients signed informed consent and samples were collected, processed, and analyzed under the guidance of the ethics committee of the Guangzhou Red Cross Hospital of Jinan University (Ethics number 2018–292).


### qRT-PCR
  The hub DEARGs were validated using quantitative real-time PCR. Total RNA was reverse-transcribed to cDNA according to the manufacturer’s instructions using the PrimeScript RT reagent Kit (TaKaRa, Japan). GAPDH was used as the housekeeping gene and relative mRNA expression levels were determined using the 2−ΔΔCt comparative method from the mean of triplicate treatments averaged from 3 replicate PCR reactions. The primer sequences are as follows. GAPDH Forward: 5′-ACACCCACTCCTCCACCTTT-3′; Reverse: 5′-TTACTACTTGGAGGCCATGT-3′; HMGB2 Forward: 5′-CCGGACTCTTCCGTCAATTTC-3′; Reverse: 5′-GTCATAGCGAGCTTTGTCACT-3′; CDKN1A Forward: 5′-GGCATTCTGGGAGCTTCATCT-3′; Reverse: 5′-AGGGTGCCCTTCTTCTTGTG-3′; JUN Forward: 5′-TCCAAGTGCCGAAAAAGGAAG-3′; Reverse: 5′-CGAGTTCTGAGCTTTCAAGGT-3′; DDIT3, Forward strand: 5′-GGAAACAGAGTGGTCATTCCC-3′; Reverse: 5′-CTGCTTGAGCCGTTCATTCTC-3′.


### Statistical analysis
  R project (version 4.1.0) was used for our data processing and analysis. The data of qRT-PCR were analyzed using the SPSS 22 (IBM SPSS Statistics, USA). Differences between experimental and control groups were calculated using an unpair t-test as the statistical method. p value < 0.05 was considered as statistically significant. Data were presented as mean ± standard deviation (SD).


### Data availability
  All data, models, and code developed or utilized during the study are available from the corresponding author upon reasonable request.


## Supplementary Materials