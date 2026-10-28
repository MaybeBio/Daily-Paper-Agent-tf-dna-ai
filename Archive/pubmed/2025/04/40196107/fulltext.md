# Integrated bioinformatics analysis and biological experiments to identify key immune genes in vascular dementia


## Objectives
  This study aimed to identify key immune genes to provide new perspectives on the mechanisms and diagnosis of vascular dementia (VaD) based on bioinformatic methods combined with biological experiments in mice.


## Methods
  We obtained gene expression profiles from a Gene Expression Omnibus database (GSE186798). The gene expression data were analysed using integrated bioinformatics and machine learning techniques to pinpoint potential key immune-related genes for diagnosing VaD. Moreover, the diagnostic accuracy was evaluated through receiver operating characteristic curve analysis. The microRNA, transcription factor (TF), and drug-regulating hub genes were predicted using the database. Immune cell infiltration has been studied to investigate the dysregulation of immune cells in patients with VaD. To evaluate cognitive impairment, mice with bilateral common carotid artery stenosis (BCAS) were subjected to behavioural tests 30 d after chronic cerebral hypoperfusion. The expression of hub genes in the BCAS mice was determined using a quantitative polymerase chain reaction(qPCR).


## Results
  The results of gene set enrichment and gene set variation analyses indicated that immune-related pathways were upregulated in patients with VaD. A total of 1620 immune genes were included in the combined immune dataset, and 323 differentially expressed genes were examined using the GSE186798 dataset. Thirteen potential genes were identified using differential gene analysis. Protein-protein interaction network design and functional enrichment analysis were performed using the immune system as the main subject. To evaluate the diagnostic value, two potential core genes were selected using machine learning. Two putative hub genes, Rac family small GTPase 1(RAC1) and CKLF-like MARVEL transmembrane domain containing 5 (CMTM5) exhibit good diagnostic value. Their high confidence levels were confirmed by validating each biomarker using a different dataset. According to GeneMANIA, VaD pathophysiology is strongly associated with immune and inflammatory responses. The data were used to construct miRNA hub gene, TFs-hub gene, and drug-hub gene networks. Varying levels of immune cell dysregulation were also observed. In the animal experiments, a BCAS mouse model was employed to mimic VaD in humans, further confirmed using the Morris water maze test. The mRNA expression of RAC1 and CMTM5 was significantly reduced in the BCAS group, which was consistent with the results of the integrated bioinformatics analysis.


## Conclusions
  RAC1 and CMTM5 are differentially expressed in the frontal lobes of BCAS mice, suggesting their potential as biomarkers for diagnosing and prognosis of VaD. These findings pave the way for exploring novel molecular mechanisms aimed at preventing or treating VaD.


## Introduction
  Vascular dementia (VaD) is the second leading cause of dementia after Alzheimer’s disease (AD), accounting for at least 20% of all dementia diagnoses (1). The primary manifestations of VaD include cognitive impairment, as well as behavioural and psychological symptoms (2). The persistent decline in the quality of life induced by VaD imposes significant medical and economic burdens on patients, families, and society. Therefore, an unmet need exists to investigate the molecular causes and prospective diagnostic indicators of VaD.

  Bioinformatics is an interdisciplinary field that combines biology, computer science, and information technology (3). The discipline not only assists researchers in processing and analysing large-scale biological data but also provides new insights and methods for the diagnosis, treatment, and prevention of diseases (4). For instance, through bioinformatics analysis, researchers can identify genes and biomarkers associated with AD, thereby supporting personalized medicine (5). A previous study using integrative systems biology analysis demonstrated that short-chain acylcarnitines/amino acids and medium/long-chain acylcarnitines are most closely related to AD, which is mediated by adenosine triphosphate-binding cassette transporter A1 and carnitine palmitoyltransferase 1A (6). In addition, three cerebrospinal fluid (CSF) proteins, CSF sodium-/potassium-transporting ATPase subunit beta-1, serglycin, and thioredoxin-dependent peroxide reductase mitochondria, may serve as potential novel diagnostic biomarkers (7). However, VaD has not garnered significant attention.

  Machine learning, an essential branch of artificial intelligence, leverages algorithms to learn from data and make predictions, and has been widely applied in data analysis across various domains (8). In bioinformatics, machine learning is employed for extracting valuable information from complex biological data, building predictive models, and identifying patterns (9). The application of machine learning has enabled bioinformatics research to process big data more efficiently, driving significant progress in areas such as disease prediction and drug discovery (10).

  The objective of this study was to screen and identify key genes associated with the occurrence and progression of VaD through comprehensive bioinformatics analysis. Additionally, the analysis also aimed to investigate the pathological mechanism of VaD. Initially, we acquired the gene expression profiles of patients with VaD and healthy brain samples from a public database. Subsequently, we identified significant modules and differentially expressed immune-related genes in VaD, and screened out the key VaD genes using machine learning algorithms. Moreover, we also assessed the expression of key genes in mice with bilateral common carotid artery stenosis (BCAS) and discovered that their expression was decreased in such mice, suggesting that these genes significantly contributed to the onset and development of VaD. Thereby offering novel insights for further investigation into the pathogenesis and diagnosis of VaD.


## Materials and methods

### Microarray data source
  Datasets GSE186798 (11) and GSE122063 (12) were downloaded from the Gene Expression Omnibus (GEO) database. The microarray data from GSE186798 included 10 samples each from vascular dementia-associated post-stroke dementia, post-stroke non-dementia, and healthy controls. Only fit and post-stroke dementia samples were selected from this dataset. All brain tissue samples were obtained from the frontal brain regions. The GSE122063 microarray data used as the validation set comprised brain samples from 44 healthy individuals, 36 individuals with VaD, and 56 with AD. Only gene expression data from the frontal lobe of 18 patients with VaD and 22 matched controls were retained. The GSE186798 dataset was sequenced using GPL23159, and GSE122063 using GPL16699, both of which are derived from the human body.

  The ImmPort (13), GeneCards (14), and Molecular Signatures Databases (MSigDB) (15) were used to obtain 1791, 15898, and 20741 immune-related genes, respectively. Finally, 1620 immune-related genes were identified at the intersection of the three gene sets.


### Identification of VaD-associated immune-differentially expressed genes
  Differential gene analysis was performed using the R package “limma” to determine the DEGs between control and VaD samples (16). The thresholds for differential genes were set at a log2 fold change (log2FC) > 0.5 and a p-value < 0.05, indicating DEGs with increased expression. Potentially downregulated DEGs were represented by log2FC < −0.5 and p-value < 0.05. Volcano plots were employed to illustrate the results of differential gene expression. Differentially expressed immune genes were identified by intersecting DEGs and immune genes.


### Gene set enrichment analysis and gene set variation analysis
  GSEA was performed to identify significantly enriched functional gene sets using the R package “clusterProfiler” (17). This method determines whether a priori-defined gene set demonstrates statistically significant concordant differences between two biological states or phenotypes (18). The MSigDB contains functional annotations of the gene sets used in GSEA. Additionally, the dataset was analysed simultaneously for multiple gene sets. The gene set was considered significantly enriched if a result of a nominal P-value < 0.05 and a Q-value of < 0.25 was acquired. Gene sets meeting the abovementioned conditions were sorted from high to low according to enrichment score (ES).

  GSVA is a method used to estimate the variation of gene set enrichment across samples in an expression dataset, conducted utilising the R package “GSVA” (19). The ES for gene signatures was then calculated using GSVA. Between-group differences in gene set enrichment were determined using the Limma package. Only the gene set with a P-value of < 0.05 was considered significant.


### Function enrichment analysis
  Gene Ontology (GO) annotation of the DEGs, consisting of biological process (BP), cellular component (CC), and molecular function (MF) terms, was performed using the R package “clusterProfiler”. The top three BP, CC, and MF outcomes were illustrated as Laplace plots utilising ggplot2, with a cutoff criterion of P < 0.05.

  Functional enrichment of the Kyoto Encyclopedia of Genes and Genomes (KEGG) pathways for DEGs was performed using the R package “clusterProfiler”. Moreover, ggplot2 generated Laplace plots for the top three significant KEGG pathways based on P< 0.05.


### Protein-protein interaction network
  The STRING online database was utilized to determine interacting genes (20). To fully comprehend the functional interactions between proteins and select essential hub genes, the PPI network was visualised and analysed using the Cytoscape software. The MCODE algorithm was used to search for highly clustered subnetworks (21).


### Machine learning
  Two machine learning algorithms were used to investigate candidate genes for VaD diagnosis. The Least Absolute Shrinkage and Selection Operator (LASSO) is recognised as a type of penalised regression that can be used to screen variables and strengthen prediction accuracy (22). Random forest (RF), recognised as a feature selector, ranks genes based on their impact on the accuracy of the RF (23). This method forecasts continuous variables and identifies patterns with noticeable variations (24). The LASSO regression and RF analysis were carried out utilising the R packages “glmnet” (25) and “randomForest” (26). Intersecting genes identified by LASSO and RF were proposed as potential hub genes for VaD diagnosis. The positions of the identified genes were mapped to chromosomes using R packages “circlize” (27).


### Hub genes validated by gene expression values and receiver operating characteristic analysis
  To verify the expression of hub genes in the diseased and normal states, the GSE186798 and GSE122063 datasets were used as the internal and external validation sets, respectively. T-test and the “ggplot2” package of R language were used to assess and illustrate the expression of hub genes. Box plots were generated to ascertain whether the predicted VaD target genes exhibited significant differential expression in the validation set.

  The “pROC” package was employed to evaluate the diagnostic predictive significance of essential genes (28). VaD was identified using the area under the curve (AUC) and 95% confidence interval (CI). An AUC >0.7 was regarded as a potential diagnostic value (29).


### Immune infiltration analysis
  CIBERSORT, a computational method utilising tissue gene expression profiles, was used to ascertain the proportion of immune cells in the samples (30). We calculated 22 immune cell types using the CIBERSORT method in the R package. A violin plot was generated to reveal striking differences in the relative compositions of immune cell populations between the VaD and control groups. Spearman’s correlation was utilized to examine the association between immune cell subtypes.


### GeneMANIA analysis and prediction of potential microribonucleic acid, transcription factor, and drugs related to hub genes
  The GeneMANIA database was used to construct networks that generated gene function hypotheses, examined gene lists, and determined gene priority through functional analysis (31). NetworkAnalyst, JASPAR, and Comparative Toxicogenomics Database (CTD) were used to predict potential miRNAs, TF, and drugs associated with hub genes. NetworkAnalyst is a comprehensive visualisation and analysis tool for gene expression data (32). JASPAR is a database of nucleotide profiles describing the binding preferences of TF, which provides predicted TF-deoxyribonucleic acid (DNA) interactions (33). The CTD is a comprehensive, publicly accessible database that offers manually curated information regarding chemical–gene/protein interactions, chemical–disease associations, and gene–disease correlations.


### Experimental animals
  The use of all animal experiments was approved by the Animal Care and Use Committee of Beijing Neurosurgical Institute. Male C57BL/6 mice aged 8–10 weeks (22–25 g) were purchased from Charles River Laboratory Animal Technology Co., Ltd. (Beijing, China). The mice were housed at the Laboratory Animal Center of the Beijing Neurosurgical Institute with free access to water and lab chow and were maintained under a 12-h light/dark cycle. The mouse model of BCAS was generated following the methods previously described (34). The mice were randomly divided into the following groups (N=7 mice per group): (1) BCAS: both common carotid arteries (CCAs) were constricted with micro-coils of an internal diameter of 0.18 mm; (2) Sham: same surgical procedure as that applied for the BCAS group except for the implantation of micro-coils.


### Morris water maze test
  Cognitive function was assessed using the MWM test on day 30 after BCAS. The MWM test was performed as previously described (35, 36). Briefly, the MWM involved a round water tank divided into four quadrants. The water temperature was maintained at 24 ± 2°C. The escape platform (10 cm in diameter) was fixed in the centre of the southwest quadrant (target quadrant) and immersed approximately 1 cm beneath the surface of the water. During the training session, mice were delicately positioned into the water maze, released facing the wall from one of the four quadrants in random order, and allowed to swim freely in search of the hidden platform. The mice were provided 60 s to discover the hidden platform, and the latency to reach the escape platform was recorded. If the mouse failed to find the platform within 60 s, it was guided to the platform and allowed to remain there on the platform 30 s. Each mouse was tested four times daily, beginning from different quadrants, with 40-min intervals between trials. Additionally, the mean was calculated as the daily score. The probe trial was conducted 24 h after the final training trial. Each mouse was allowed to swim freely in the tank and the platform was removed for 60 s. The latency to find the target quadrant, the frequency with which the mouse crossed the original platform, and the swimming velocity were automatically recorded using video tracking software (EthoVision, Noldus, Netherlands).


### Quantitative real-time polymerase chain reaction
  Brain tissue was rapidly removed from the frontal lobe, and the messenger RNA (mRNA) levels of RAC1 and CMTM5 were measured using qRT-PCR. Total RNA was isolated using the TRIzol reagent, and complementary DNA synthesis was conducted using a Revert Aid First Strand complementary DNA Synthesis Kit (Yeasen) in accordance with the manufacturer’s guidelines. qRT-PCR was performed using SYBR Green Real-Time PCR Master Mix (Yeasen) on a StepOne Plus Real-Time PCR System (Applied Biosystems). Glyceraldehyde-3-phosphate dehydrogenase was used as a reference gene. All quantitative PCR was performed in triplicate using seven independent purified RNA samples. The primer sequences are listed in  Table 1 .


### Data expression and statistical analysis
  Statistical analyses were performed using GraphPad Prism software (version 7.00; GraphPad Software Inc., USA). All data were presented as the mean ± standard error of the mean. Comparisons between groups were statistically evaluated using Student’s t-test. Statistical significance was set at P < 0.05.


## Results

### Data processing and identification of VaD-related pathways
  Figure 1  depicts the flow chart for the bioinformatics analysis in this study. Information sets were obtained from the GEO database (GSE186798), including brain samples from 10 patients with VaD and 10 controls. In the comparison of VaD and control samples, 323 DEGs were identified, of which 138 were upregulated and 185 were downregulated.  Figure 2A  illustrates a volcano plot of the DEGs. Furthermore, GSEA revealed distinct upregulated gene sets linked to VaD, and the top five pathways were selected. We identified that the immune-related pathways were significantly activated in the VaD group, including “prostaglandin signalling”, “interleukin (IL)-17 pathway”, “cytokine-cytokine receptor interaction”, “overview of inflammatory and profibrotic mediators”, and “lym pathway” ( Figures 2B–F ). The GSVA revealed similar results. Moreover, “IL6-JAK-STAT signalling and “inflammatory responses” were highly activated in the VaD group, whereas oxidative phosphorylation was hyperactivated in the control group ( Figures 2G, H ).


### Screening of immune-associated DEGs, functional enrichment analysis and PPI construction
  The immune-related genes of the three immune datasets interacted with the DEGs to identify 13 immune-related DEGs ( Figures 3A, B ). According to KEGG analysis, “T cell receptor signalling pathway”, “Hematopoietic cell lineage” and “FC gamma R-mediated phagocytosis” were the three conditions where common genes (CGs) were most highly enriched. GO analysis indicated that CGs were predominantly enhanced in BP terms, including “FC receptor-mediated stimulatory signalling pathway”, “positive regulation of response to external stimulus”, and “positive regulation of cell-matrix adhesion”. Concerning CC metaphysics, the CGs primarily settled within the “immunological synapse”, “focal adhesion”, and “ruffle membrane”. MF analysis demonstrated that “epidermal growth factor receptor binding”, “SH3 domain binding”, and “cytokine receptor activity” were crucial elements in the metric system ( Figure 3C ). Enrichment analysis revealed that VaD was primarily associated with inflammatory responses, which strongly correlated with the pathological progression of the disease.

  We constructed a PPI network to identify node genes and searched for densely connected subnetworks. As depicted in Cytoscape, the PPI network of the immune DEGs contained 12 paired interactions and involved nine genes. Node genes were displayed using the MCODE plug-in ( Figures 3D, E ). Additionally, we conducted a correlation analysis of the immune DEGs. DEFB107A and DEFB107B demonstrated a notable positive correlation, while RAC1 and CD3E exhibited a significant negative correlation ( Figure 3F ).


### Identifying potential hub genes using machine learning
  Candidate genes were screened utilizing LASSO regression and RF machine learning methodologies for diagnostic value assessment.  Figures 4A, B  demonstrate that the LASSO regression algorithm identified 10 probable candidate biomarkers.  Figures 4C, D  demonstrate that the RF algorithmic program systematically arranged the sequences to facilitate the estimation of the relative importance of each gene. When the Venn diagram illustrating the overlap of the 10 most essential genes identified by LASSO and the five probable candidate genes from RF was presented ( Figure 4E ), four hub genes (RAC1, FABP6, DEFB107B, and CMTM5) were identified for final confirmation.  Figure 4F  displays the positions of hub genes on the chromosomes.


### Validation of the hub genes
  The GSE186798 dataset was used as an internal validation set to verify the reliability of hub genes. Violin plots were employed to determine the expression levels of screened hub genes. The results demonstrated that the expression of RAC1, FABP6, DEFB107B, and CMTM5 significantly differed in the VaD group compared to that in the control group ( Figure 5A ). Additionally, RAC1 (AUC 0.71, CI 0.58–0.85), FABP6 (AUC 0.70, CI 0.56–0.83), DEFB107B (AUC 0.75, CI 0.63–0.88), and CMTM5 (AUC 0.71, CI 0.58–0.85) had a potential diagnostic value for VaD based on the plotting of ROC curves ( Figures 5B–E ).

  As DEFB107B was not tested, RAC1, FABP6, and CMTM5 were validated using an external validation set (GSE122063 dataset). Our results demonstrated that RAC1 and CMTM5 were significantly decreased in the VaD group compared to those in the control group ( Figure 5F ). Furthermore, ROC analysis revealed that these two hub genes, RAC1 (AUC 0.83, CI 0.69–0.97), and CMTM5 (AUC 0.76, CI 0.60–0.92) had a good diagnostic value for VaD. Nevertheless, the diagnostic significance of FABP6 (AUC 0.50, CI 0.31–0.69) was poor, with AUC values falling below 0.70 ( Figures 5G–I ). Therefore, hub genes RAC1 and CMTM5 were used in subsequent experiments.


### GeneMANIA, and immune cell infiltration analysis
  A functional network established using GeneMANIA indicated that these pathways were closely linked to immune and inflammatory responses ( Figure 6A ). As memory B cells, follicular helper T cells, activated dendritic cells, and activated mast cells were not expressed in the sample, they were excluded from the subsequent phase of the analysis. Macrophages M1 and resting natural killer cells exhibited a notable positive correlation. Conversely, macrophages M0 and macrophages M2 cells had a significant negative correlation. Spearman’s test was used to assess significant differences in immune cell infiltration between patients with VaD and the control group ( Figure 6B ). In addition, we evaluated the proportions of 18 immune cell subtypes between the groups. The findings revealed a strikingly different immune cell presence in the VaD group compared to that in the control group. Gamma-delta T cells were significantly reduced in patients with VaD compared to those in the controls, indicating the necessity of increasing this type of cell within the VaD immune microenvironment ( Figure 6C ).


### Establishment of regulatory network for miRNAs, TFs, and drugs-hub genes
  Furthermore, miRNAs perform various functions in the regulation of gene expression. Hub gene and miRNA regulatory networks were constructed using Cytoscape to predict miRNAs targeting hub genes based on the NetworkAnalyst database. In  Figures 7A, B , the two hub genes and their associated regulatory miRNA molecules are displayed. Similarly, we predicted the TFs of the target genes using the JASPAR database, which could be harnessed as innovative regulators of VaD pathogenesis ( Figures 7C, D ). Moreover, the CTD was used to conduct our final drug discovery search to lay the foundation for VaD treatment ( Figures 7E, F ).


### Vascular dementia in BCAS mice and qRT-PCR validation of data
  To investigate whether the BCAS model induces cognitive impairment in mice, we conducted the MWM test. On day 5 of the training phase, the BCAS group exhibited a longer escape latency to the platform in comparison to that observed in the sham group ( Figure 8A ). Representative images of the traces from the spatial probe assessment are displayed in  Figure 8B . Compared with the sham group, escape latency ( Figure 8C ) was significantly higher and the frequency of times crossing the target ( Figure 8D ) was significantly lower in the BCAS group, indicating that cognitive dysfunction was triggered by chronic cerebral hypoperfusion (CCH). Furthermore, no significant difference was observed in swimming velocity between the two groups ( Figure 8E ), suggesting that the MWM test performance was not affected by variations in swimming, motor ability, or motivational deficits.

  To verify the bioinformatic findings, qRT-PCR was performed. The results demonstrated that the mRNA expression levels of RAC1 and CMTM5 were significantly lower in the VaD group than in the control group. This indicates that the data mining outcomes were reliable and have considerable research significance ( Figures 9A, B ).


## Discussion
  The immune response is a protective process against external stimuli or internal injuries involving various immune cells and cytokines (37). Studies have demonstrated that the immune response of the nervous system plays a crucial role in VaD (38). CCH, the leading cause of VaD (39, 40), induces endothelial dysfunction, increases blood-brain barrier permeability, and facilitates the leakage of plasma proteins into the brain, culminating in robust immune and inflammatory responses (41). Animal research on VaD induced by CCH has validated that microglia become activated following the onset of cerebral hypoperfusion, ultimately resulting in white matter damage and VaD (42, 43). Consistently, the GSEA and GSVA results of our study revealed that immune-related pathways were highly activated in the VaD group, indicating that the immune response plays an important role in the development of VaD.

  The involvement of multiple molecular pathways in neuroimmune regulation gives rise to several potential biomarkers (44, 45). However, investigations of these potential biomarkers in the context of VaD have yielded inconsistent results. This inconsistency makes the application of inflammatory biomarkers in VaD problematic. To resolve this issue, we incorporated integrated bioinformatic analysis and machine learning to identify two hub genes (RAC1 and CMTM5) with diagnostic potential. These results were validated using in vivo experiments.

  RAC1, a member of the Rho GTPase family, was ubiquitously expressed (46). The activity of RAC1 within cells is regulated by its binding state with GTP (guanosine triphosphate) and GDP (guanosine diphosphate). Specifically, RAC1 is active when bound to GTP and inactive when bound to GDP (47). When activated, RAC1 facilitates the allosteric regulation of p21-activated kinase, thereby promoting its phosphorylation and subsequent activation (48). Additionally, RAC1 functions include the regulation of various physiological processes such as cytoskeletal reorganisation, cell migration, and cell adhesion (49). A previous study demonstrated that neuronal RAC1 significantly enhanced cognitive recovery after stroke by activating various signalling pathways, including promoting axonal plasticity and reducing the astrocytic barrier (50). Another study showed that RAC1 promoted axonal regeneration and alleviated cognitive dysfunction by regulating glial fibrillary acidic protein signalling (51). RAC1 is involved in NADPH oxidase activation, leading to ROS production, which influences immune signalling and antioxidant regulation (52). Our results indicated that the expression of RAC1 was reduced in VaD, which is consistent with these results.

  CMTM5 is a novel tumour suppressor belonging to the CMTM family that contains a MARVEL domain in its structure and was initially reported by the Human Disease Gene Research Center of Beijing University in 2003 (53). CMTM5 played a potentially crucial role in transmembrane signalling and inhibiting tumour cell proliferation, adhesion and migration through regulating EGFR and PI3K/AKT Pathway (54, 55). However, the role of CMTM5 in VaD is not well established. To the best of our knowledge, this is the first study to demonstrate that CMTM5 expression is downregulated in the brain tissue of mice with VaD. Furthermore, we predicted miRNAs, TFs, and drugs linked to CMTM5 using internet databases, which provided clues for the diagnosis and treatment of VaD.

  Our study has certain limitations. Firstly, owing to the differences in analytical thinking and approaches, our investigation may be a secondary mining of a previously released dataset, yielding divergent findings. The two hub genes screened in this study have not been experimentally validated in human brain tissue. Secondly, our analysis was based on a limited sample size, necessitating additional evidence to confirm our hypotheses. Further research with large sample size is required to ascertain the diagnostic accuracy of hub genes for VaD, to elucidate the connection between hub gene levels and future treatment strategies, and to identify the immune-related pathological mechanisms underlying VaD. Thirdly, this study utilised only the BCAS animal model for VaD, and further experiments are necessary to validate these findings in other models of VaD.

  In conclusion, we identified two hub genes (RAC1 and CMTM5) associated with VaD, reinforcing the potential of specific hub genes as biomarkers. These findings pave the way for future research into accurate diagnosis and enhanced understanding of VaD pathogenesis.


## Data availability statement
  The original contributions presented in the study are included in the article/ Supplementary Material . Further inquiries can be directed to the corresponding authors.


## Ethics statement
  The animal study was approved by Animal Care and Use Committee of Beijing Neurosurgical Institute. The study was conducted in accordance with the local legislation and institutional requirements.


## Author contributions
  YZ: Conceptualization, Data curation, Formal analysis, Investigation, Methodology, Resources, Validation, Visualization, Writing – original draft. WX: Methodology, Resources, Software, Writing – review & editing. WC: Conceptualization, Project administration, Supervision, Validation, Writing – review & editing. YW: Conceptualization, Funding acquisition, Methodology, Project administration, Supervision, Validation, Writing – review & editing.


## Conflict of interest
  The authors declare that they have no competing financial interests or personal relationships that may have influenced the work reported in this study.


## Generative AI statement
  The author(s) declare that no Generative AI was used in the creation of this manuscript.


## Publisher’s note
  All claims expressed in this article are solely those of the authors and do not necessarily represent those of their affiliated organizations, or those of the publisher, the editors and the reviewers. Any product that may be evaluated in this article, or claim that may be made by its manufacturer, is not guaranteed or endorsed by the publisher.


## Supplementary material
  The Supplementary Material for this article can be found online at: https://www.frontiersin.org/articles/10.3389/fimmu.2025.1560438/full#supplementary-material


## Acknowledgments
  We thank Xiantao Academic Tools (https://www.xiantaozi.com) for assistance with the data analysis.