# Dysregulated lncRNA and mRNA may promote the progression of ischemic stroke via immune and inflammatory pathways: results from RNA sequencing and bioinformatics analysis


## Background
  Long non-coding RNAs (lncRNAs) are widely involved in gene transcription regulation and which act as epigenetic modifiers in many diseases.


## Objective
  To determine whether lncRNAs are involved in ischemic stroke (IS), we analyzed the expression profile of lncRNAs and mRNAs in IS.


## Methods
  RNA sequencing was performed on the blood of three pairs of IS patients and healthy controls. Differential expression analysis was used to identify differentially expressed lncRNAs (DElncRNAs) and mRNAs (DEmRNAs). Based on the co-expression relationships between lncRNA and mRNA, a series of bioinformatics analysis including GO and KEGG enrichment analysis and PPI analysis, were conducted to predict the function of lncRNA.


## Results
  RNA sequencing produced a total of 5 DElncRNAs and 144 DEmRNAs. Influenza A pathway and Herpes simplex infection pathway were the most significant pathways. EP300 and NFKB1 were the most important target proteins, and Human leucocyte antigen (HLA) family were the key genes in IS.


## Conclusions
  Analysis of this study revealed that dysregulated lncRNAs in IS may lead to IS by affecting the immune and inflammation system.


## Supplementary Information
  The online version contains supplementary material available at 10.1007/s13258-021-01173-1.


## Introduction
  Ischemic stroke (IS) is one of the cardiovascular diseases and the leading cause of death and disability worldwide, especially in developing countries (Strong et al. 2007). Cardiovascular and cerebrovascular diseases, diabetes, dyslipidemia, obesity, smoking, drinking, and anticoagulants may be the main factors affecting the occurrence of IS (Lavados et al. 2005; O’Donnell et al. 2010). Factors may lead to IS through vascular and neuronal damage, dysfunction of molecular signaling pathways, inflammatory cytokine damage, and oxidative stress damage (Chaitanya et al. 2013; Jin et al. 2013; Li et al. 2018). Focusing on the mechanisms of IS injury, repair and inflammation, and its possible molecular mechanisms may provide a more theoretical basis for IS screening, prevention and treatment.

  Biomarkers associated with stroke are mainly a variety of proteins associated with pathological processes such as inflammation-related damage, neuronal apoptosis, and vascular endothelial dysfunction (Serena et al. 2005; An et al. 2013). However, due to the complex protein composition, there are various post-translational modifications, hydrolysis and denaturation, which makes it difficult to select the appropriate method for accurate detection (Calligaris et al. 2011; Lam et al. 2016). The physical and chemical properties of traditional biomarkers are unstable and poorly conserved, and their content is related to the regulation of gene expression. Therefore, rational application of gene expression variation can be used for diagnostic prediction in the early stages of the disease (Ebert et al. 2006; Sepramaniam et al. 2014).

  lncRNA is a group of non-protein coding RNA molecules, and their transcripts are more than 200 nucleotides in length (Yang et al. 2014). LncRNA regulates DNA methylation, histone modification or chromosome remodeling on multiple layers through diverse molecular regulation mechanisms, and participates in many important biological regulation processes such as genomic imprinting, transcriptional interference and nuclear transport (Wilusz et al. 2009; Chen and Carmichael 2010; Marchese et al. 2016, 2017). Current lncRNA research covers many fields, such as tumor, blood system diseases, cardiovascular and cerebrovascular diseases, especially in ischemic and hypoxic diseases (Harries 2012; Li and Chen 2013; Sánchez and Huarte 2013). LncRNA UCA1 can be used as a potential diagnostic marker and therapeutic target for acute myocardial infarction (Yan et al. 2016), lncRNA ANRIL is associated with the sensitivity of atherosclerotic disease and can be used as a marker for the diagnosis (Holdt and Teupser 2018). Changes in the expression of certain lncRNA after ischemia-reperfusion injury may be biomarkers of ischemia-reperfusion injury during liver surgery or transplantation (Chen et al. 2013). In addition, lncRNA is also considered effective in the treatment of ischemic diseases by promoting stem cell differentiation and preventing erythrocyte apoptosis (Yang and Lu 2016; Zhang et al. 2016).

  Although the regulatory mechanism of lncRNA and its relationship with some ischemic and hypoxic diseases have been preliminarily understood, the regulatory network of gene expression mediated by lncRNA and its molecular mechanism in IS remain to be further explored. To determine the functional significance of lncRNAs in the pathophysiological regulation of IS, RNA sequencing technology, which is superior to microarrays, was used to analyze lncRNA and mRNA expression profiles in this study.


## Materials and methods

### Participants and study design
  Three patients first diagnosed IS and three healthy controls, Han Chinese males, 40–60 years old (Supplementary Table 1), were recruited from the hospital of Jilin University from July to December 2017. IS patients were diagnosed for the first time based on the “Chinese guidelines for diagnosis and treatment of acute ischemic stroke 2014”, and all of them had no history of using antiplatelet or antidiabetic agents. All objectives with history of diabetes mellitus, atrial fibrillation, myocardial infarction, tumor, acute infectious disease, immunity disease, blood disease, renal or liver failure, and hemorrhagic stroke or recurrent stroke were excluded. Written informed consent was obtained. The study was approved by the Ethics Committee of School of Public Health, Jilin University. The design flow chart of this study was shown in Fig. 1.

  Fig. 1Flow diagram of the study design


### Sample preparation and RNA sequencing
  Peripheral blood samples were collected in the next morning after the participants had fasted for ten hours or overnight. Total RNA was isolated and purified using standard TRIzol Reagent (Invitrogen, Carlsbad, CA) according to the manual. RNA concentration and purity, RNA integrity were then assessed using the Nanodrop2000 spectrophotometer (Thermo Fisher Scientific, Wilmington, DE) and an Agilent 2100 Bioanalyzer (Agilent Technologies, Santa Clara, CA). The cDNA library was constructed using the Truseq RNA sample Prep Kit (Illumina, Inc., San Diego, CA). RNA sequencing (2*150 bp) was conducted on the Illumina HiSeq 4000 sequencing system (Illumina, Inc.).


### Quality control and quantification
  Quality-control filtering was performed by removing the adapter sequences and low-quality bases, and high-quality clean reads were generated. The clean reads were mapped to the reference using HISAT2 v2.0.4 (Pertea et al. 2016) and the reference-based assembly of transcripts was performed using Stringtie v1.3.1 (Pertea et al. 2015) (reference genome sequence and annotation files were downloaded from GENCODE (GRCh38, https://www.gencodegenes.org/)). The lncRNAs were screened out according to the number of exons, length, known annotation and coding potential of transcripts. Then transcripts including mRNAs, lncRNAs and transcripts of unknown coding potential (TUCPs) were quantified by StringTie-eB.


### Differential expression analysis
  To identify differentially expressed lncRNAs and mRNAs between IS patients and controls, differential expression analyses were performed by “ballgown” package of R software (Pertea et al. 2016). From the perspective of statistical significance, different types of transcripts (lncRNA, TUCPs and mRNA) were analyzed as a whole, so that the results had no preference for molecular types. Transcripts with a P-value < 0.05 and |log2foldchange| >1 were assigned as differentially expressed.


### GO and KEGG enrichment analysis
  Gene Ontology (GO) enrichment analysis of differentially expressed genes or lncRNAs target genes were implemented by the “GOseq” R package, in which gene length bias was corrected (Young et al. 2010). Corrected P-value < 0.05 were considered to be significantly enriched. Kyoto Encyclopedia of Genes and Genomes (KEGG) is a database resource for understanding high-level functions and utilities of the biological system (Kanehisa et al. 2008). We used KOBAS software to test the statistical enrichment of differential expression genes or lncRNA target genes in KEGG pathways (Mao et al. 2005). P-value was used to determine whether the pathways were significant.


### PPI analysis
  Protein-Protein Interaction (PPI) analysis of differentially expressed genes was based on the online database resource which known as STRING (https://string-db.org/cgi/input.pl) and predicted interactions between proteins. We used mRNAs co-expressed with DElncRNAs to construct the PPI network and visualized it in Cytoscape 3.6.1 (Shannon et al. 2003).


### Network construction of GO/KEGG pathways of DEmRNAs
  GO/KEGG Enrichment Pathways Network was constructed using all differentially expressed mRNAs with a plug-in called “ClueGO” in Cytoscape 3.6.1 (Bindea et al. 2009). ClueGO integrates the terms of Gene Ontology (GO) and the KEGG/BioCarta pathways, it could achieve comprehensive visualization by creating a GO/KEGG pathways network.


### Cross validation
  Gene expression profiling of GSE22255 dataset was performed in peripheral blood mononuclear cells of 20 IS patients and 20 sex- and age-matched controls using GPL570 [HG-U133_Plus_2] Affymetrix Human Genome U133 Plus 2.0 Array. In order to be consistent with the design of this study, we only downloaded the expression matrix of male cases and male healthy controls (10 vs. 10), and used R software “limma” package (Ritchie et al. 2015) for standardization and differential expression analysis, and obtained the log2(foldchange) value and P value to validate significance of RNAs that we have found.


## Results

### Quality control and mapping
  After filtering out the reads with adapter, the reads with N base more than 10 % and the low quality reads from raw reads, 97,077,054, 86,224,578 and 104,855,436 clean reads were produced in IS patients, and 97,740,922, 97,583,408 and 100,893,034 clean reads were produced in the control group (Supplementary Table 2). The percentage of total mapped reads was 94.96%, 95.37% and 96.44% in IS patients group, and 95.34%, 97.23% and 96.32% in control group, respectively. The total mapped rate was more than 90%, indicating that the selection of reference genome was appropriate and there was no pollution in the experiment (Supplementary Table 3). A total of 86,983 transcripts were detected, including 80,863 mRNAs, 2469 novel lncRNAs, 2369 annotated lncRNAs and 1282 TUCPs. A total of 24,566 genes were detected, including 19,627 mRNAs, 2137 novel lncRNAs, 1854 annotated lncRNAs and 948 TUCPs.


### Differentially expressed lncRNAs and mRNAs in IS
  A total of five lncRNAs were differentially expressed in IS, including 4 up-regulated lncRNAs and 1 down-regulated lncRNA (Table 1). There were 144 differentially expressed mRNAs, among which 70 were up-regulated and 74 were down-regulated, each top 10 were listed in Table 2, respectively.

  Table 1Differentially expressed lncRNAs in ischemic strokeTranscript IDGene symbolStatusRegulationAverage FPKMlog2 (foldchange)P-valueNumber of co-expressionIS groupControl groupmRNAsLNC_000015–NovelUp176.71419.3253.1930.0223118ENST00000602573.1SNHG8AnnotatedUp2.8080.9381.5820.0158356ENST00000381051.6MIRLET7BHGAnnotatedUp3.0131.1501.3900.0067497LNC_001727–NovelUp11.6395.8021.0040.0015895ENST00000574212.1AF001548.5AnnotatedDown1.7074.790− 1.4880.00649643

  Table 2Top 10 up- and downregulated mRNAs in ischemic strokeTranscript IDGene nameRegulationAverage FPKMlog2 (foldchange)P-valueIS groupControl groupENST00000468133MAPK14Up2.2550Inf5.78E−05ENST00000254066RARAUp2.6440Inf0.00181ENST00000443308SHISA5Up3.8580Inf0.00754ENST00000475880WDR45Up9.3280Inf0.01142ENST00000367026TRAF3IP3Up2.7430.00112.3290.00429ENST00000616058SUCOUp2.8940.0088.4840.02382ENST00000620123TAP2Up3.5600.0108.4540.03042ENST00000596676SMCO4Up2.0290.0794.6890.00839ENST00000337907REREUp2.7200.1104.6260.017ENST00000381733ASAH1Up4.0500.2104.2700.00272ENST00000434651HLA-DQB1Down012.974− Inf0.00101ENST00000400908REREDown04.746− Inf0.00089ENST00000557140NFKBIADown04.301− Inf0.00355ENST00000343139HLA-DQA1Down04.082− Inf0.01339ENST00000394690STX5Down04.060− Inf0.04904ENST00000351660DHPSDown02.554− Inf0.0465ENST00000396009NFATC2Down02.319− Inf0.002ENST00000531372IGLL5Down02.123− Inf0.00743ENST00000507711FRYLDown02.113− Inf0.00036ENST00000542643RAP1GAPDown01.810− Inf0.03751Inf maximum, represents the highest degree of up regulation, − Inf minimum, represents the highest degree of down regulation


### LncRNA/mRNA co-expression analysis and GO/KEGG annotation to predict the probable functions
  LncRNA can regulate the expression of target coding genes to achieve function (Bazin et al. 2017). We analyzed the function of mRNA co-expressed with lncRNA to clarify the biological role of DElncRNA. The lncRNA-mRNA co-expression network (Supplementary Fig. 1) was established to show co-expression relationships of them, the network comprised 946 nodes and 1009 connections. The most crucial sub-network was constructed by the transcripts with a high degree, which would be the core regulatory modules of the entire co-expression network. Thus, lncRNA AF001548.5, which has the most co-expressed mRNAs was the most important lncRNA in the network. GO enrichment analysis showed the top 20 terms of three types, biological process, cellular component, and molecular function (Supplementary Fig. 2 and Supplementary Table 4). KEGG enrichment analysis showed that the DElncRNAs play roles mainly in Influenza A pathway and Herpes simplex infection pathway (Fig. 2 and Supplementary Table 5).

  Fig. 2Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway analyses of mRNAs co-expressed with DElncRNAs in ischemic stroke. The size of the circle represents the number of genes enriched, and the color represents the significance


### PPI analysis of mRNAs co-expressed with DElncRNAs
  The PPI network (Fig. 3) contains 417 nodes and 810 edges, protein interactions were evaluated with the highest confidence (0.9). Degree was used to assess the importance of genes, and the genes with top 30° were listed, EP300 and NFKB1 were regarded as the most important top two target genes that regulated protein expression (Fig. 4).

  Fig. 3Protein–protein interaction networks constructed by Search Tool for the Retrieval of Interacting Genes/Proteins (STRING) based on the mRNAs co-expressed with DElncRNAs. The larger the circle and the redder the color, representing the greater degree of the gene, and the more genes that are connected to it. Conversely, the smaller the circle and the bluer the color, representing the smaller degree of the gene, and the fewer number of genes connected to it

  Fig. 4Top 30 degree genes involved in the PPI network


### Network construction of GO/KEGG pathways of DEmRNAs
  We utilized all DEmRNAs for the GO and KEGG analysis and constructed a GO/KEGG pathway network to illustrate the critical mRNAs in the process of IS. The network built 13 groups composed of GO terms and KEGG pathways, and these functional groups with target genes of mRNAs were shown in Table 3. HLA-DQB1, HLA-DQA1 and HLA-DRB5 were the key genes which had overlapped in at least four pathway groups, and all of them were belonged to the HLA family (Fig. 5). In addition, these three genes were mainly involved in the inflammatory bowel disease (IBD) pathway and asthma pathway, both in Th17 cell differentiation group.

  Table 3ClueGO results: functional groups with genesFunctionGroupsGroup genesApoptosisGroup01ACTG1,AKT1,BIRC2,CAPN2,GZMB,NFKBIA,SPTAN1,TUBA1AInfluenza AGroup09ACTG1,AKT1,ARHGDIA,CAMK2G,CCND2,HLA-DQA1,HLA-DQB1,HLA-DRB5,IL2RG,MAPK14,MX1,NFKBIA,OAS1,OSBPL8,STAT5APertussisGroup02C4B,CFL1,MAPK14,SERPING1S100 protein bindingGroup00AHNAK,EZR,S100A6Th17 cell differentiationGroup13ACTG1,AKT1,ARHGDIA,BIRC2,C4B,CAMK2G,CCND2,CD2,CD37,GLG1,GZMB,HIST1H2BD,HIST1H2BE,HLA-DQA1,HLA-DQB1,HLA-DRB5,IL2RG,MAPK14,MX1,NFATC2,NFKBIA,OAS1,OASL,RARA,STAT5A,STX5,TAP2,TBKBP1,TMBIM6,VCANToxoplasmosisGroup10AKT1,ARHGDIA,BIRC2,CAMK2G,HLA-DQA1,HLA-DQB1, HLA-DRB5,MAPK14,NFATC2, NFKBIA,OSBPL8,TBKBP1Immunological synapseGroup07ARHGDIA,CD37,ELF1,EZR,GZMB,PTPRJNegative regulation of protein kinase B signalingGroup04AKT1,CD2,PTPRJPositive regulation of myoblast fusionGroup12CAPN2,MAPK14,NFATC2,RIPOR2Protein deacylationGroup08CHD4,HDAC6,JDP2,NIPBL,SIRT5,TAP2Regulation of GTP bindingGroup05C9orf72,CSNK1A1,RAP1GAP,RIPOR2Regulation of nuclease activityGroup11AKT1,CAMK2G,HLA-DQA1,HLA-DQB1,HLA-DRB5,IFI6, IFITM2,MX1,OAS1,OASL,TMBIM6Tertiary granule lumenGroup06ARMC8,ASAH1,SPTAN1Transferase activity, transferring pentosyl groupsGroup03PARP8,SIRT5,TYMPBold genes were the key genes which had overlapped in at least four pathway groups, and all of them were belonged to the HLA family

  Fig. 5GO/KEGG pathways network constructed by ClueGO app in Cytoscape. Hexagons represent significantly enriched KEGG pathways; big ellipses indicate significantly enriched GO pathways; small ellipses indicate mRNAs that act as the link hinge between the pathways. Hexagons and big ellipses of the same color represent a functional group, while a hexagon or a big ellipse contains different colors, meaning that it belongs to different functional groups at the same time. When a small ellipse consists of different colors, it is included in a different path (colour figure online)


### Cross validation
  Five valuable coding genes and three DElncRNAs in this study were verified. Because the early microarray sequencing was not enough to detect all genes in this study, we can only verify the expression of seven IS related genes. EP300, NFKB1, SNHG8 and MIRLET7BHG met the differential expression criteria of P < 0.1 and HLA-DQB1, HLA-DQA1, HLA-DRB5 met the criteria |log2foldchange| > 1 (Table 4).

  Table 4Expression of valuable genes validated in the GSE22255Gene nameTypeGSE22255tPLog2FCEP300Important target genes of DElncRNAs− 2.16640.0417− 0.30725NFKB1Important target genes of DElncRNAs− 2.935760.00779− 0.35679HLA-DQB1Key genes− 1.696710.104− 1.08079HLA-DQA1Key genes− 1.589180.127− 1.63289HLA-DRB5Key genes− 1.696710.104− 1.08079SNHG8DElncRNAs− 1.729650.0981− 0.34551MIRLET7BHGDElncRNAs1.9152360.06890.185295AF001548.5DElncRNAs–––


## Discussion
  In this study, 5 DElncRNAs were identified that differentially expressed in IS, among which LNC_000015, LNC_001727 were novel lncRNAs, SNHG8, MIRLET7BHG, AF001548.5 are annotated lncRNA in the database. After a series of bioinformatics analysis, we mainly found that dysregulated lncRNAs and mRNAs in IS vs. controls may lead to IS by affecting the immune system of the body.

  There are few published RNA-Seq studies of IS patients, and some of these studies have not strictly controlled variables, so a large number of differentially expressed lncRNAs have been screened. Some of the DE-genes may not be related to IS, but related to other IS parallel diseases due to selection bias. In our study, only five differentially expressed lncRNAs were screened by setting strict inclusion and exclusion criteria of patients and control group. Among the five differentially expressed lncRNAs, the lncRNA SNHG8 has been widely reported. Up regulation of lncRNA SNHG8 is a risk factor for many diseases. It plays an important regulatory role in the occurrence and development of acute myocardial infarction (Zhuo et al. 2019), a variety of cancers (such as liver cancer, pancreatic cancer, nasopharyngeal carcinoma, endometrial cancer, esophageal squamous cell carcinoma, ovarian cancer, gastric cancer, breast cancer, cervical cancer, non-small cell lung cancer, prostate cancer, etc.) (Yuan et al. 2021) and ischemic diseases (Liu et al. 2019; Tian et al. 2020). Liu et al. (2019) verified that Snhg8/miR-384/Hoxa13/FAM3A axis regulating neuronal apoptosis in ischemic mice model, and then Tian et al. (2020) proved that LncRNA Snhg8 attenuates microglial inflammation response and blood-brain barrier damage in IS through regulating miR-425-5p mediated SIRT1/NF-κB signaling. Similarly, we found the hub genes EP300 and NFKB1 in the constructed PPI network of DElncRNAs co-expression mRNA. The conclusion of Tian et al. (2020) is consistent with our study. Although the other four DElncRNAs have not been reported to be associated with IS. They can be used as potential biomarkers and therapeutic targets of IS, which providing direction for future research.

  Stroke is still a severe challenge for either developed countries or developing countries, poses a substantial socioeconomic burden (Addo et al. 2012). It’s urgent to find its pathogenesis and control it effectively. KEGG analysis found that Influenza A and Herpes simplex infection pathway were the most significant two pathways in this study, both related to immune and inflammation. Inflammation is considered involved in all forms of brain damage, and immune mechanisms play an important role in the risk and progression of stroke and in cerebral ischemia (Smith et al. 2013; Fu et al. 2015). Recent data from clinical and experimental research clearly show that systemic inflammatory diseases such as atherosclerosis, obesity, diabetes or infection are associated with dysregulated immune responses, which can profoundly contribute to cerebrovascular inflammation and injury in the central nervous system (Ling et al. 2015). Some findings have shown that several immune-mediated diseases (IMDs) are linked to cerebrovascular diseases, and many hospitalizations of IMDs have been proved to be related to the increased risk of ischemic or hemorrhagic stroke (Zöller et al. 2012; Cho et al. 2014).

  Evidence suggests that acute bacterial and viral infections are prime factors for an increased risk of IS (Urbanek et al. 2010), and the mortality from vascular disease and hospitalization for stroke increased during and after the influenza pandemic. Influenza vaccination can reduce hospitalization and mortality in the elderly and prevent incapacity in working-aged adults (Madjid et al. 2009). Herpes Simplex Virus (HSV) Type 2, a class of influenza virus, was regarded as a cause of IS, and researchers found that untreated HSV-2 meningitis could lead to vascular inflammation and IS ultimately (Snider et al. 2014; Zis et al. 2016). The pathophysiological mechanism of stroke caused by varicella zoster virus (VZV) infection is believed to be similar to the pathophysiological mechanism of IS caused by HSV central nervous system infection, the prevention of VZV infection is considered as a treatable factor for transient IS (Nagel and Gilden 2014).

  In this study, Ep300 and NFKB1 were the hub target genes in PPI network, which regulate protein expression in IS. EP300 was known as Histone acetyltransferase p300 or p300 which is an enzyme encoded by EP300 gene (Eckner et al. 1994). It regulates transcription of genes via chromatin remodeling, which has been found to play an essential role in the biological function of regulatory T cells and is expected to be used in cancer immunotherapy in the future (Liu et al. 2013; Ghosh et al. 2016). Unfortunately, no studies have found the mechanism of action of EP300 related to IS up to now. However, given the important role of EP300 in PPI network, we believe that EP300 should be paid more attention in future studies when studying the molecular mechanism of IS. As for NFKB1, which is a factor that inhibits inflammation, aging and cancer, is thought to be associated with cerebral ischemia-reperfusion injury, and a study of Korean adults found that genetic polymorphisms of NFKB1 are associated with stroke susceptibility (Cartwright et al. 2016; Kim et al. 2018; Zhu et al. 2018). NFKB1 has been confirmed as a potential biomarker for the diagnosis and treatment of IS in the study of Liang (2015), indicating that PPI network in this study has certain accuracy to predict the hub genes.

  From the network of GO/KEGG pathways, we found that HLA-DQB1, HLA-DQA1A and HLA-DRB5 were the key genes which had overlapped in at least four pathway groups, in addition, both of them were belonged to the human leucocyte antigen (HLA) family. A previous study on IS patients in China has shown that the HLA-DRB1*04, HLA-DRB1*03, and the HLA-DRB1*12 alleles have protective effects on stroke (Liu et al. 2011). Similarly, a study on South Indian patients presented the association of human leucocyte antigen HLA-DRB1/DQB1 alleles and haplotypes with IS (Murali et al. 2016). Interestingly, we found that the HLA alleles (HLA-DQB1, HLA-DQA1, HLA-DRB5) at the same time in the channel were connected to the inflammatory bowel disease (IBD) pathway. It is worthy to note that IBD was considered to increase the risk of IS in a retrospective cohort study of a Taiwanese population, because of the systemic inflammatory burden that IBD led to may be a key determinant of atherosclerotic thrombosis (Huang et al. 2014). This finding was supported by previous studies that have shown a disease severity-dependent could increase the risk of developing stroke and myocardial infarction among patients with other chronic inflammatory diseases such as rheumatoid arthritis and psoriasis (Solomon et al. 2010; Ahlehoff et al. 2012).

  As this study is a preliminary exploratory study, further experiments are expected to be conducted to validate the sequencing results, and we included a total of 6 subjects (3 patients vs. 3 controls), the sample size of RNA sequencing may be small, so expanding of the sample size is expected to verify the results of this study.


## Supplementary Information

### N/A
  Below is the link to the electronic supplementary material. Supplementary material 1 (DOCX 812.2 kb)


## Acknowledgements
  We would like to express our gratitude to the Novogene Co., LTD for providing the high-throughput sequencing technology helps.