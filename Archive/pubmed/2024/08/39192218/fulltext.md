# Identification of RCAN1’s role in hepatocellular carcinoma using single-cell analysis


## Background
  The regulator of calcineurin 1 (RCAN1) is expressed in multiple organs, including the heart, liver, brain, and kidney, and is closely linked to the pathogenesis of cardiovascular diseases, Down syndrome, and Alzheimer’s disease. It is also implicated in the development of various organ tumors; however, its potential role in hepatocellular carcinoma (HCC) remains poorly understood. Therefore, the objective of this study was to investigate the potential mechanisms of RCAN1 in HCC through bioinformatics analysis.


## Methods
  We conducted a joint analysis based on the NCBI and TCGA databases, integrating both bulk transcriptome and single-cell analyses to examine the principal biological functions of RCAN1 in HCC, as well as its roles related to phenotype, metabolism, and cell communication. Subsequently, an RCAN1-overexpressing cell line was established, and the effects of RCAN1 on tumor cells were validated through in vitro experiments. Moreover, we endeavored to identify potential related drugs using molecular docking and molecular dynamics simulations.


## Results
  The expression of RCAN1 was found to be downregulated in 19 types of cancer tissues and upregulated in 11 types of cancer tissues. Higher levels of RCAN1 expression were associated with improved patient survival. RCAN1 was predominantly expressed in hepatocytes, macrophages, endothelial cells, and monocytes, and its high expression not only closely correlated with the distribution of cells related to the HCC phenotype but also with the distribution of HCC cells themselves. Additionally, Rcan1 may directly or indirectly participate in metabolic pathways such as alanine, aspartate, and glutamate metabolism, as well as butanoate metabolism, thereby influencing tumor cell proliferation and migration. In vitro experiments confirmed that RCAN1 overexpression promoted apoptosis while inhibiting proliferation and invasion of HCC cells. Through molecular docking of 1615 drugs, we screened brompheniramine as a potential target drug and verified our results by molecular dynamics.


## Conclusion
  In this study, we revealed the relationship between RCAN1 and HCC through bioinformatics methods, verified that RCAN1 can affect the progress of the disease through experiments, and finally identified potential therapeutic drugs through drug molecular docking and molecular dynamics.


## Supplementary Information
  The online version contains supplementary material available at 10.1186/s12885-024-12807-4.


## Introduction
  Cancer Statistics (2023) indicates that liver cancer has experienced the most rapid increase in mortality rates in recent years. The incidence of liver cancer reached 8.6/100,000 between 2015 and 2019, and the mortality reached 6.6/100,000 between 2016 and 2020. In 2023, it is estimated that there will be 41,210 new cases of liver cancer in the United States, with 29,380 deaths. The 5‐year survival rate for liver cancer has increased to 21% for the patients diagnosed during 2012 through 2018 [1]. Hepatocellular carcinoma (HCC) accounts for around 90% of all instances of primary liver cancer and is the second most common cause of cancer-related fatalities worldwide [2]. Although the understanding of the molecular mechanisms underlying the development of HCC has deepened among researchers, the number of developed targeted drugs remains low, and their efficacy is limited, which cannot meet the increasing treatment expectations. Therefore, in order to discover more specific and sensitive biomarkers and lay a solid foundation for the development of more targeted drugs, we need to further explore the mechanisms underlying the development and metastasis of HCC.

  Calcineurin, a calcium and calmodulin-dependent serine/threonine protein phosphatase, is associated with multiple cellular and tissue physiological functions [3]. As an inhibitor of calcineurin, regulator of calcineurin 1 (RCAN1) is expressed in multiple organs such as the heart, liver, brain, and kidneys, and is closely associated with the pathological mechanisms of cardiovascular diseases, Down syndrome, Alzheimer’s disease, etc. [4–6]. In the field of oncology, as research on RCAN1 deepens, it has been found to play a role in inhibiting tumor growth in many organ tumors, such as esophageal squamous cell carcinoma, lymphoma, osteosarcoma, thyroid cancer, liver cancer, etc. [7–11].

  Current research indicates that in HCC, RCAN1 can inhibit tumor growth and metastasis by suppressing calcineurin activity and nuclear translocation of NFAT1 [11, 12]. There is still limited research on the mechanism of action of this gene. Here, in order to provide more insights into the mechanistic analysis of this gene, we attempted to utilize bioinformatics to investigate the internal connection between RCAN1 and HCC, starting from transcriptomics and single-cell analysis. Additionally, we conducted cellular functional experiments to explore the role of RCAN1 in HCC cell proliferation and invasion. This approach aims to provide a more comprehensive understanding of the association between RCAN1 and HCC.


## Material and method

### Data retrieval and download
  We conducted a search on National Center for Biotechnology Information (NCBI, https://www.ncbi.nlm.nih.gov/), for hepatocellular carcinoma using the search terms “ Hepatocellular Carcinoma”, “Array expression analysis,” and “High-throughput sequencing expression analysis”. We ultimately selected two datasets, GSE149614 and GSE151530 for our analysis, the former comprises 10 tumor samples and 18 normal samples, while the latter includes 46 tumor samples. Additionally, employing the same search criteria, we sourced a single-cell dataset, CNP0000650, from the China National Center for Bioinformation (CNCB, https://www.cncb.ac.cn/), which consists of 18 tumor samples and 1 normal sample. The bulk RNA-Seq data was downloaded from the The Cancer Genome Atlas Program (TCGA https://www.cancer.gov/ccg/research/genome-sequencing/tcga), comprising 50 normal samples and 374 tumor samples.


### Pan-cancer analysis
  Pan-cancer analysis refers to the comprehensive study of multiple cancer types collectively, aiming to identify common molecular alterations and pathways across different cancers. To analyze the importance of RCAN1, we conducted a pancancer analysis using the TCGAplot R package [13].


### Single-cell sequencing data processing
  We processed the GSE149614 data (There are 18 samples in total, including 10 tumor samples and 8 normal samples) using Seurat version 4.3 [14]. We selected cells based on the following criteria: features greater than 500, UMI counts less than 15,000, and mitochondrial percentage proportion below 25%, We standardize the dataset through ‘SCTransform’. Finally, we obtained 63,100 cells. For the data set GSE149614, we use the R package ‘Harmony’ [15] to process it in batches, the parameter is set to max.iter.harmony = 30, lambda = 1. Pc.num were set to 10 and resolution to 0.5 for PCA dimensionality reduction and visualized the data using UMAP. For the annotation of single-cell datasets, we divided the entire dataset into nine types of cells, namely Hepatocyte, Macrophage, T/NK, Endothelial, Monocyte, Fibroblast, Plasma B, Mature B, and DC. For the single-cell datasets GSE151530 and CNP0000650, the original authors had already processed the data. Therefore, we did not subject them to any additional processing.


### Disease phenotype analysis
  To analyze the relationship between cells, genes, and disease phenotypes, we used the Scissor R package to perform a joint analysis of the single-cell dataset GSE149614 and CNP0000650, respectively, and the Bulk dataset downloaded from TCGA with parameters of “family = binary, alpha = 0.01” [16].


### Single-cell metabolic analysis
  To discern the metabolic difference between tumor and control in snRNA-seq datasets, we used the R package scMetabolism [17] to quantify the metabolic differences between normal and tumor samples, using the ‘VISON’ method and selecting the Kyoto Encyclopedia of Genes and Genomes (KEGG) metabolic dataset,statistical analyses of metabolic pathways across different groups are provided in Supplementary file 1.


### Copykat
  To further explore malignant cells in the overall single-cell data, we used the copykat package to analyze and visualize all single-cell data [18]. The parameter is set as ngene.chr = 5, LOW.DR = 0.05, UP.DR = 0.1, win. size = 25, KS.cut = 0.1, distance set to ‘euclidean’, genome set to ‘hg20’.


### Cellchat
  To quantify and visualize cell signaling and communication networks between cells, we conducted analysis using the Cellchat package [19]. We choose secret signaling for analysis of cellchat’s database. All results of the cellular communication analysis can be found in Supplementary file 2.


### Cell culture
  The HepG2 cell line was purchased from the Chinese Academy of Sciences (Shanghai) and cultured in DMEM medium containing 10% FBS and 1% penicillin at 37 °C in 5% CO2.


### Construction of RCAN1 Overexpression cell lines
  To investigate the role of RCAN1 in cellular processes, we generated cell lines that overexpressed RCAN1. We collaborated with Hao Yang Biotechnology (Xi’an, China) to synthesize the overexpression plasmid vector for RCAN1, denoted as OE-RCAN1. The detailed information of the plasmid vector is provided in Supplementary file 3. Subsequently, the synthesized plasmid vector was transfected into HepG2 cells following the manufacturer’s protocol. The transfection was carried out using Lipofectamine 2000 reagent (11,668–019, Invitrogen). The infected cells were then selected with puromycin to establish stable cell lines that overexpressed RCAN1.


### Quantitative RT–PCR
  Total RNA was isolated following the recommended protocol provided by the manufacturer (Thermo Fisher, USA) using TRIzol reagent. Subsequently, cDNA synthesis was performed using the HiScript® II Q Select RT SuperMix for qPCR (R233, VAZYME, China). The resulting cDNA served as the template for quantitative RT–PCR, which was carried out using the ABI (ViiA-7) 7500 apparatus (Applied Biosystems). The primer sequences for RT–PCR can be found in Supplementary file 4.


### Western blot
  Total protein was extracted using SDS-PAGE, followed by transfer onto a PVDF membrane (Millipore, China). Subsequently, the membrane was incubated with primary antibodies, including β-actin (T0022, Affinity, China), Bcl2 (3498 T, CST, USA), Caspase3 (9665S, CST, USA), and Bax (ab32503, abcam, UK). To detect the target proteins, the membrane was further incubated with a 1:10,000 dilution of horseradish peroxidase-conjugated goat anti-rabbit (Beyotime, China) or goat anti-mouse (Proteintech, China) secondary antibodies.


### Cell function assays
  To examine the alterations in the biological behaviors and functions of liver cancer cells resulting from the overexpression of RCAN1, we conducted three experiments. In the CCK8 experiment, we specifically selected cells in logarithmic growth phase with robust growth status and seeded them at a density of 5 × 103 cells/well in a 96-well cell culture plate. The plate was subsequently incubated overnight at 37 °C with 5% CO2. After the required culture time, we added 10 μl of enhanced CCK-8 reagent (QS-S321, Keycell, China) to each well and incubated them for 2 h at 37 °C. The absorbance of each well was measured at 450 nm using a microplate reader (C22.2NO.1010.1, BioTek, USA).

  For the cell invasion experiment, we added 800 μl of pre-cooled 10% FBS MEM culture medium (containing double antibiotics) to a 24-well plate, which was then placed in a transwell chamber (353,097, Falcon, USA). Subsequently, 100 μl of 0.5 mg/ml Matrigel (356,234, Corning, USA) was added to the center of the bottom chamber of the transwell, and it was allowed to solidify at 37 °C. Once the Matrigel had solidified, 200 μl of cell suspension from each group was added to the upper chamber of the transwell, and the plate was incubated at 37 °C with 5% CO2. After a period of 3 days, the cells were fixed with 70% ice-cold ethanol for 1 h and stained with 0.5% crystal violet staining solution (G1014, Servicebio, China), and scanned at × 200 magnification [20].

  To detect cell apoptosis, we employed the fluorescence TUNEL assay [21]. Following the manufacturer’s instructions, we fixed the cells with 4% paraformaldehyde, permeabilized them with 0.2% Triton X-100 (diluted in 1 × PBS) (ST795, Beyotime, China), and allowed them to equilibrate at room temperature for 5 min. Subsequently, we added 1 × Equilibration Buffer (diluted 1:10 with deionized water) to the permeabilized cells and incubated them at room temperature for 15 min. The excess Equilibration Buffer was removed using absorbent paper, and the reaction working solution was added to the cells, which were then incubated at 37 °C for 60 min. Following incubation of the coverslips in darkness for 5 min with DAPI, nuclear staining was performed and excess DAPI was washed away. Finally, the sealed slides were observed and images were captured using a fluorescence microscope after applying an anti-fluorescence quenching mounting medium (0100–01, Southernbiotech, USA) on the slides.


### Drug screen
  We downloaded the protein structure of RCAN1 from the Alphafold [22] and predicted the active sites of the protein using deepSite [23]. Next, we downloaded 1615 FDA-approved drugs from the ZINC database [24], and then converted the target drugs into three-dimensional structures using ADFRsuite [25]. Based on the obtained three-dimensional structures of the drugs and the RCAN1 protein, we sequentially screened molecular docking using Autodock [26].

  Following docking results, the drug with the lowest binding energy was selected for molecular dynamics simulation with RCAN1 using Gromacs (v2022.3) [27, 28]. The small molecule was pre-processed with AmberTools22 to append the GAFF force field and subjected to hydrogen addition and RESP charge calculation using Gaussian 16W, with the resulting electrostatic potential data integrated into the molecular dynamics system topology. Simulations were conducted at a constant temperature of 300 K and pressure of 1 Bar, utilizing the Amber99sb-ildn force field, with water molecules represented by the Tip3p model, and the system’s net charge was neutralized by the addition of Na + ions as necessary. Energy minimization was initially performed using the steepest descent method, followed by equilibration in the canonical (NVT) ensemble for 100,000 steps and the isobaric-isothermal (NPT) ensemble for an equal number of steps, both with a coupling constant of 0.1 ps over a duration of 100 ps. The free molecular dynamics simulation was executed for a total of 5,000,000 steps with a time step of 2 fs, culminating in a 100 ns trajectory. The structures of the drugs used for molecular docking, the docking outcomes, and the results of the molecular dynamics simulations are available in the Supplementary file 5.


### Statistical analysis
  Statistical analysis was conducted using GraphPad Prism 7, Seurat (version 4.3), and R (version 4.2.3). Survival curves were generated using the Kaplan–Meier method. All experiments were independently performed at least three times. Quantitative data were presented as mean ± standard deviation. The t-test was employed to analyze differences between two groups, while analysis of variance (ANOVA) was utilized for differences among multiple groups. A significance level of P < 0.05 was considered statistically significant.


## Results

### Comprehensive pan-cancer analysis
  Utilizing the TCGAplot package, we have conducted an extensive pan-cancer analysis encompassing gene expression, immune infiltration, functional enrichment, and survival-related assessments.

  We obtained pan-cancer data from the TCGA database and compared the expression differences of RCAN1 between tumor and normal groups using the R package. The results showed that among the 33 cancer types, RCAN1 expression was decreased in 14 cancer tissues, increased in 3, and showed no statistical significance in 16. Specifically, the expression of RCAN1 in HCC cells is lower than normal tissue. The results were visualized using a grouped box plot (Fig. 1A). Utilizing the R package, we conducted a prognostic analysis on the acquired pan-cancer data. The K-M survival curve (Fig. 1B) shows that both the 2.5-year overall survival (OS) rate and the 5-year OS rate are higher in the RCAN1 high-expression group compared to the low-expression group. The mOS was 6.8 years in the RCAN1 high-expression group, while 3.8 years in the RCAN1 low-expression group. This indicates that high expression of RCAN1 is associated with improved patient survival and reflects its excellent anti-tumor effect.

  Fig. 1RCAN1 expression and its association with LIHC survival time. A Differential expression of RCAN1 among different types of cancer; B Survival curve based on the expression level of RCAN1 in patients with liver cancer

  There is a significant correlation between RCAN1 expression and immune cell infiltration in most types of cancer, suggesting that RCAN1 may play a crucial role in these tumors (Fig. 2A). Based on the expression of RCAN1, tumor samples from the bulk RNA-Seq data were further divided into high-expression and low-expression groups. We identified differentially expressed genes (DEGs) between these two groups. Subsequently, we performed Gene Ontology (GO) functional enrichment analysis based on genes co-expressed with RCAN1 (Fig. 2B). Additionally, we utilized Gene Set Enrichment Analysis (GSEA), including GSEA-GO (Fig. 2C) and GSEA-KEGG (Kyoto Encyclopedia of Genes and Genomes) (Fig. 2D), for pathway enrichment. The top five pathways from each enrichment method are displayed in the figures.

  Fig. 2RCAN1 pan cancer analysis. A Analysis of the association and statistical differences between RCAN1 and 22 different immune cells in 33 types of cancer. *P<0.05 ** P<0.001; B Enrichment analysis and differential gene heatmap drawing were performed separately by grouping RCAN1 expression differences; C GSEA-GO analysis of the DEGs between RCAN1 high- and low-expression groups in HCC, and the top 5 GO pathways were shown; D GSEA-KEGG analysis of the DEGs between RCAN1 high- and low-expression groups in HCC, and the top 5 KEGG pathways were shown


### Single-cell sequencing results of RCAN1 expression
  Based on the single-cell sequencing dataset GSE149614, we utilized the UMAP algorithm for data dimensionality reduction, resulting in 9 cellular subtypes, namely Hepatocyte, Macrophage, T/NK, Endothelial, Monocyte, Fibroblast, Plasma B, Mature B, DC. The results are displayed in the dimensionality reduction plot (Fig. 3A). We then extracted the representative genes of these 9 cellular subtypes from the dataset and compared them with the well-established and traditional marker genes of these cellular subtypes, finding a high degree of concordance (Fig. 3B).

  Fig. 3Visualization of single cell dataset GSE149614, malignant cell and disease phenotypic correlation analysis. A UMAP dimensionality reduction visualization of single-cell liver cancer; B Bubble plot for annotation of single-cell liver cancer data; C Visualization of RCAN1 expression distribution in different cells; D Scissor analysis to calculate cell types positively or negatively correlated with liver cancer phenotypes; E Malignant cell analysis in single-cell liver cancer data; F The expression difference of RCAN1 in different cell cycles

  We observed that RCAN1 is predominantly expressed in Hepatocyte, Macrophage, Endothelial, and Monocyte (Fig. 3C). Subsequently, we used the scissors algorithm to accurately identify cells associated with HCC and normal cell phenotypes from the single-cell data, and we found that the distribution of cells with high expression of RCAN1 closely matched the distribution of cells associated with HCC phenotypes (Fig. 3D). Therefore, we have reason to believe that RCAN1 is closely associated with HCC phenotypes. By analyzing the dataset using the copycat algorithm, tumor cells are primarily distributed in liver cells and some lymphocytes (Fig. 3E). We found that the distribution of RCAN1 is also consistent with the distribution of tumor cells, indicating that Rcan1 is expressed in most liver tumor cells. Additionally, upon grouping the single-cell dataset GSE149614 according to cell cycle stages, we observed an upregulation of RCAN1 expression during the G1 phase. This elevation in expression may suggest that RCAN1 predominantly exerts a suppressive effect on the onset of HCC during the G1 phase (Fig. 3F).

  To validate the results, the datasets GSE151530 and CNP0000650 were analyzed. Based on the GSE151530 dataset and the malignant cells defined by the original authors, we found that the distribution of RCAN1 overlapped with the distribution of malignant cells, similar to the results we studied in the manuscript. The cell expression distribution, cell cycle distribution, and scissor analysis results of RCAN1 in the single-cell dataset CNP0000650 were consistent with those in the single-cell dataset GSE149614. Due to the quality differences between datasets, we have included the specific results in the Supplementary figure.


### Differences in inter-group metabolic pathways
  Metabolic mechanisms play a crucial role in the mechanism of tumor occurrence and development. In order to investigate the alterations in metabolic pathways between liver cancer and normal tissue, we utilized the R package “scMetabolism” to analyze the metabolic landscape. A total of 85 metabolic pathways were compared between groups, and significant differences were observed in multiple pathways: Alanine, Aspartate and glutamate metabolism, Butanoate metabolism, D-Glutamine and D-glutamate metabolism, Fatty acid degradation, Glycerolipid metabolism, Glycine, serine and threonine metabolism, Nicotinate and nicotinamide metabolism, Nitrogen metabolism, One carbon pool by folate, Synthesis and degradation of ketone bodies, Terpenoid backbone biosynthesis, Tyrosine metabolism, Valine, leucine and isoleucine degradation, etc. We present here a partial display of representative findings in Fig. 4A. Through observation, we found that all the aforementioned metabolic pathways were expressed as metabolically active in liver cancer tissues and their distribution is consistent with Rcan1, suggesting that the expression of Rcan1 may directly or indirectly associated with the activity of these metabolic pathways, thereby impacting tumor cell proliferation and migration.

  Fig. 4Single-cell cell metabolism and cell communication analysis. A Cellular metabolism analysis in single cell liver cancer data; B Network diagram of cell communication quantity difference; C Heat map of cell communication quantity and intensity; D Histogram of cell communication quantity difference; E Major differences in cell communication between liver cancer and normal tissue


### Interaction between hepatocytes and other cellular subtypes by cell-chat analysis
  The differential interaction number and strength among the 9 cell types were analysis by R package “CellChat”. We found strong interactions between hepatocytes and fibroblasts, endothelial cells, and macrophages (Fig. 4B, C). The overall strength and number of cell subpopulation interactions in HCC tissue are significantly higher than in normal tissue (Fig. 4D), which further confirms the complexity and diversity of HCC mechanisms [29]. Additionally, the analysis of ligand-receptor interactions provides further details on intercellular signaling, as shown in Fig. 4E. We found that the signaling pathways of SPP1, GDF, and PDGF are exclusively present in HCC tissue cells, which may be associated with the specificity of HCC cells. On the other hand, the signaling flow of the CXCL pathway in HCC tissue is significantly lower than in normal tissue, suggesting its potential inhibition by tumor cells. However, further exploration and validation are needed.


### RCAN1 inhibits the proliferation and invasion of HCC cells and promotes apoptosis
  To investigate the role of RCAN1 in tumor cells, we constructed a RCAN1-overexpressing cell line (OE-RCAN1) (Fig. 5A, B, C). The expression level of Caspase3, Bax and Bcl2 in OE-RCAN1 group was confirmed by conducting Western blotting analysis (Fig. 6A). Full uncropped Gels and Blots images can be found in the Supplementary file 6. In order to evaluate the impact of RCAN1 expression on cell proliferation and invasion in HepG2 cells, the CCK-8 cell proliferation assay and cell invasion assay were employed. The findings demonstrated that the OE-RCAN1 group exhibited significantly diminished cell proliferation and invasion capabilities in comparison to the HepG2 group (Fig. 6B, C, D).

  Fig. 5Cell invasion and proliferation assay. A Representative images of cell invasion assay; B Average number of invading cells within each group; C Cell proliferation ability was detected using the CCK-8 assay in 3 groups

  Fig. 6After overexpression of RCAN1, apoptosis in HepG2 cells can be induced. A The expression level of Caspase3, Bax and Bcl2 conducted by Western blotting; B The differential expression of Caspase-3 among different groups; C The differential expression of Bax among different groups; D The differential expression of Bcl2 among different groups

  The results of our study revealed higher protein expression levels of Caspase3 and Bax in the OE-RCAN1 group compared to the HepG2 group. Conversely, the expression level of Bcl2 was lower in the OE-RCAN1 group. Caspase-3 is a crucial effector caspase involved in cell apoptosis, playing an essential role in various processes associated with cell disintegration and apoptotic body formation [30]. Bcl2, on the other hand, is a significant regulatory factor in the programmed cell death pathway that inhibits cell apoptosis [31]. Bax, a member of the Bcl-2 gene family, is the most prominent pro-apoptotic gene in the human body. By interacting with mitochondria, Bax exerts an inhibitory effect on Bcl-2, thus regulating cell death [32]. The observed increase in caspase-3 and Bax expression levels, along with the decrease in Bcl2 expression, provides evidence that RCAN1 promotes cell death in liver cancer cells. To provide a more tangible observation, the fluorescence TUNEL experiment was conducted, revealing that the proportion of TUNEL-positive cells significantly increased in the OE-RCAN1 group compared to the HepG2 group (Fig. 7).

  Fig. 7Representative images of TUNEL stained cells. Blue represents cell nuclei, while red represents apoptotic cells


### Drug screening
  We screened drugs based on molecular docking, and finally obtained brompheniramine as a potential binding drug, which has the lowest binding energy among 1615 drugs: -10.2 kcal/mol. Brompheniramine has strong antihistamine effect, short duration, and sedative effect. The subunit that RCAN1 mainly binds to brompheniramine is Asn317 (a) (Fig. 8A, B). Molecular dynamics simulations were performed on RCAN1 in complex with Brompheniramine, and the stability of the interaction was assessed by plotting the Root Mean Square Deviation (RMSD). The RMSD values for both the protein and the small molecule were observed to be higher during the initial 20 ns, after which they plateaued, indicating a stabilization of the complex overall (Fig. 8C).

  Fig. 8Visualization of docking results based on RCAN1 molecules. A The combination of RCAN1 and brompheniramine for 3D visualization; B The combination of RCAN1 and bromphe fniramine for two-dimensional visualization. C The RMSD graph depicting the dynamic interaction between RCAN1 and brompheniramine based on molecular dynamics simulations


## Disscusion
  HCC is a significant global health concern, with the incidence and mortality rates on the rise, necessitating the development of effective prevention strategies and improved treatment approaches [33]. The invasive nature of HCC often leads to rapid disease progression and metastasis, further complicating treatment [34]. The identification of tumor targets has emerged as a crucial breakthrough in current HCC therapy [35]. Current research on RCAN1 in the context of cancer primarily centers on the RCAN1.4 isoform. The other subtype, RCAN1.1, is relatively understudied in terms of its role in tumorigenesis. In previous research, RCAN1.2 has been primarily implicated in association with the prognosis of esophageal squamous cell carcinoma [7]. Therefore, we have also chosen to focus our investigations on RCAN1.4 [36]. In this study, we employed bioinformatics analysis to establish a correlation between the expression of RCAN1 and overall survival rates in patients, finding that higher RCAN1 expression is associated with improved overall survival. Single-cell analysis revealed a similar distribution pattern of RCAN1 expression as that of HCC cell phenotypes, malignant cell distribution, and related metabolic pathway distribution. Cell functional experiments further validated the significant anti-cancer effect of RCAN1 overexpression, suggesting a strong intrinsic connection between RCAN1 and HCC. Based on our findings, RCAN1 expression prevalent in macrophages, hepatocytes, fibroblasts, and endothelial cells. The literature elucidates that RCAN1 orchestrates the proliferation and migration of malignant endothelial cells and hepatocytes while concurrently diminishing their invasive capabilities [12, 37]. Nonetheless, the precise role of RCAN1 in modulating fibroblast and macrophage function necessitates further investigation [38–40].

  RCAN1 is located in the critical region of human chromosome 21q22.12, which is known as the Down syndrome critical region. As an inhibitor of calcineurin, RCAN1 and its isoforms have been found to exert antitumor effects in various organ tumors. Patients with Down syndrome have a lower incidence of breast cancer, and studies have demonstrated that overexpression of RCAN1.4 can block the calcineurin-NFATc1 pathway, thereby inhibiting tumor growth [41]. Wang et al. confirmed that in thyroid cancer, NFE2L3 has been shown to increase cell invasiveness, and RCAN1, functioning as a growth and metastasis inhibitor, acts through NFE2L3 [10]. Zhang et al. demonstrated that RCAN1 is a downstream molecule of miR-103a-3p, and the knockout of miR-103a-3p leads to tumor suppression, while silencing RCAN1 reverses this inhibitory effect [42]. It has been demonstrated by scholars that RCAN1.4 serves as the target of miR-619-5p. Suppression of RCAN1.4 has been shown to facilitate angiogenesis and induce proliferation and metastasis of NSCLC cells [43]. In this study, CCK-8 and invasion assays confirmed that upregulation of RCAN1 inhibited proliferation and invasion of HCC cells.

  Previous studies have established a strong correlation between RCAN1 and apoptosis within the field of medicine. For instance, a study conducted on neuroblastoma demonstrated that the prolonged accumulation of RCAN1.1L in SH-SY5Y cells triggers apoptosis by activating caspase-3 [44]. Similarly, in the context of renal fibrosis, the overexpression of RCAN1.4 was observed to induce apoptosis in myofibroblasts through the inhibition of the calcineurin/NFAT2 signaling pathway [45]. Additionally, numerous investigations have illustrated that RCAN1 can impede cancer growth by inhibiting the NF-κB signaling pathway [8, 46, 47], a well-established pathway in cancer biology. Notably, the NF-κB signaling pathway plays a pivotal role in the regulation of cell proliferation and apoptosis [48]. In this study, we validated the upregulation of RCAN1’s effect on apoptosis in liver cancer cells through Western blot and TUNEL assays. All the assays suggested that RCAN1 may serve as a novel target for anticancer therapy in HCC.

  In order to explore the potential interacting drugs of RCAN1, we screened drugs through molecular docking and selected brompheniramine as a potential binding drug. Brompheniramine, an antihistamine, has been commonly used in cardiovascular and respiratory diseases in the past [49, 50], but little is known about its research in tumor diseases. What antihistamines can find in tumor research is that it can significantly reduce the probability of transformation from hepatitis patients to cancer [51]. In addition, antihistamines can significantly affect the survival cycle of the disease in a variety of cancers [52]. RCAN1 is a potential core gene in the progression of liver cancer disease. Antihistamines screened by molecular docking may be used as therapeutic drugs for liver cancer in the future. A study conducted by the Icahn School of Medicine at Mount Sinai has demonstrated the efficacy of anti-allergy drugs in anti-cancer therapy [53]. Its researchers discovered an allergic pathway in a mouse model of non-small cell lung cancer (NSCLC) that releases anti-tumor immunity when blocked. Infiltrating immune cells in lung cancer can exhibit characteristics of “type 2” immune responses, which are typically associated with allergic diseases such as eczema and asthma, similar phenomena have also been observed in other cancer studies. What is more astonishing is that a lung cancer patient did not control the growth of his cancer after receiving PD1 inhibitor treatment, but his cancer was effectively controlled after receiving three doses of anti-allergy drugs. Furthermore, the blockade of IL-4 enhanced the response of mice and 6 patients with treatment-resistant lung cancer to checkpoint blockade. Whether brompheniramine has similar anti-tumor cell mechanisms in liver cancer remains to be further verified through in vivo and in vitro experiments.

  Although we have identified an association between RCAN1 and HCC through bioinformatic methods and confirmed the antitumor effects of RCAN1 through in vitro experiments, we must acknowledge the limitations of this study. We have not yet delved into the specific mechanism of RCAN1’s action. In addition, considering the existence of multiple isomers of RCAN1, our verification was carried out in a relatively generalized manner, rather than experimentally verified from the perspective of isomers. Although we have successfully screened potential disease therapies through molecular docking and molecular dynamics, unfortunately we have not been able to verify them at the animal or cellular level. Therefore, we urgently need to conduct further comprehensive studies to fully elucidate the complex mechanism of action of RCAN1 in HCC.


## Conclusions
  This study focuses on the currently popular single-cell analysis methods to investigate the potential intrinsic association between RCAN1 and HCC. All analyses conducted in this study consistently indicate a significant correlation between RCAN1 and HCC, as well as its association with patient prognosis. Furthermore, the inhibitory effect of RCAN1 on HCC tumor cells was further validated through in vitro experiments. These findings suggest that RCAN1 may serve as a novel prognostic marker and therapeutic target for HCC.


## N/A

### Supplementary Information
  Supplementary Material 1: Supplementary Figure. Single-cell analysis of CNP0000650 and GSE151530.

  Supplementary Material 2: Supplementary File 1. Single cell metabolic results.

  Supplementary Material 3: Supplementary File 2. Single cell cell chat results.

  Supplementary Material 4: Supplementary File 3. Verification and results of overexpression of RCAN1.

  Supplementary Material 5: Supplementary File 4. Primer sequences.

  Supplementary Material 6: Supplementary File 5. Molecular docking drugs and molecular dynamics results.

  Supplementary Material 7: Supplementary File 6. Full uncropped Gels and Blots image.


## Acknowledgements
  Not applicable.