# Cartilage-protective effects of lopinavir/ritonavir: in vitro and in silico exploration of the HIF-1α/SOX9/IL-1β pathway


## Background
  This study aimed to investigate the effects of Lopinavir/Ritonavir (Lop/r) on chondrocyte structure and extracellular matrix (ECM) integrity, as well as its impact on key proteins involved in anabolic and catabolic pathways, using both in vitro and in silico approaches.


## Methods
  Drug-target interaction networks were constructed through bioinformatics analyses, and molecular docking was performed. Human primary chondrocytes were treated with Lop/r, and untreated cells served as controls. Cell viability, proliferation, and protein expression levels were assessed using standard in vitro techniques, including spectrophotometric assays and Western blotting.


## Results
  Molecular docking analyses revealed strong binding affinities between Lop/r and osteoarthritis-related targets such as HIF-1α, EP300, TNF, IL-6, KCNA5, and IL-1β, suggesting modulation of hypoxia, inflammatory, and epigenetic pathways. In vitro, Lop/r did not alter chondrocyte morphology or ECM structure and was not cytotoxic (p < 0.05). However, it significantly reduced the expression of critical proteins including HIF-1α, SOX9, and IL-1β (p < 0.05).


## Conclusion
  These findings suggest that Lop/r may exert regulatory effects on cartilage-related molecular pathways and holds promise as a repurposed therapeutic agent for osteoarthritis. Further studies are warranted to confirm its potential in clinical applications.


## Supplementary Information
  The online version contains supplementary material available at 10.1186/s13018-025-06068-5.


## Introduction
  Osteoarthritis (OA) is a disease characterized by cartilage damage, and extracellular matrix (ECM) degradation occurs in response to inflammation in chondrocytes that reduces the quality of life and health of patients all over the world. In addition, health expenses impose a great burden on health systems and countries’ economies. The underlying mechanisms of various types of diseases that progress with cartilage malformation and degeneration, especially OA, are still not fully understood [1]; treatment options are not optimal, and none of them have articular cartilage regeneration potential. Moreover, unfortunately, satisfactory results cannot be obtained from the current conservative/medical and/or surgical treatment modalities applied against degenerated or diseased cartilage tissue. For this reason, scientists have turned to researching different treatment methods. Among these trends, molecular research has gained popularity. While molecular studies commonly highlight the preservation of tissue integrity and cellular homeostasis, their principal pharmacomolecular goal is to inhibit, reverse, or promote the regeneration of degenerative processes in damaged tissues.

  Many different signaling pathways have been evaluated in research on degeneration and/or regeneration. Sex-determining region Y (SRY)-related high-mobility group (HMG) box 9 (SOX9), which is involved in anabolic pathways [2], as well as hypoxia-inducible factor-1 alfa (HIF-1α), which is involved in cell homeostasis [3], and interleukin (IL)- 1 beta (1β), which plays important roles in catabolic pathways [4], are among those signaling pathways evaluated in cartilage tissues.

  It has been reported that the application of human immunodeficiency virus (HIV) protease inhibitor lopinavir (Lop) alone or in combination with ritonavir (r) may affect IL-1β, HIF-1α, SOX9, and nuclear factor kappa-B (NF-κB) signaling pathways [5]. A review of the literature and bioinformatic analyses indicated that Lop/r has been studied to assess its potential in delaying the degeneration of intervertebral disc tissue [5]. However, it has been understood that the effect of Lop/r on chondrocytes, which are human cartilage tissue cells, has not been investigated.

  The selection of Lopinavir/Ritonavir (Lop/r) for investigation in the context of OA was based on its previously reported pleiotropic effects beyond antiviral activity, particularly its influence on inflammatory and cellular stress pathways. Lop/r has been shown to modulate key proinflammatory cytokines such as IL-1β, IL-6, and TNF-α, all of which are central to OA pathogenesis [6]. In vitro and in vivo studies have demonstrated that Lop/r can suppress NF-κB signaling, a major transcriptional regulator of inflammation in cartilage degeneration [7, 8].

  Furthermore, Lop/r has been reported to affect mitochondrial dynamics and autophagy, which are critical for chondrocyte survival and cartilage integrity under stress conditions [9, 10].

  Recent network pharmacology studies have proposed the repositioning of antiretroviral drugs, including Lop/r, as potential modulators of degenerative diseases due to their interaction with cellular stress responses, epigenetic regulators, and hypoxia signaling pathways [11]. Notably, a study by Yilmaz et al. (2022) revealed that Lop/r modulates HIF-1α and SOX9 expression in nucleus pulposus cells, suggesting its capacity to influence cartilage-related gene regulation [5]. These insights support the hypothesis that Lop/r may have therapeutic relevance in OA by simultaneously targeting inflammatory, hypoxic, and degenerative molecular mechanisms.

  This study aimed to investigate the potential of Lopinavir/Ritonavir to modulate key biological pathways implicated in OA by assessing their interactions with critical hub proteins through in-silico molecular docking analyses, followed by experimental validation. Furthermore, the study evaluated the cytotoxic effects of Lop/r on human primary chondrocyte cultures, its impact on extracellular matrix (ECM) morphology, and its regulatory influence on protein expression within the HIF-1α/SOX9/IL-1β signaling axis.


## Materials and methods

### In-silico studies

#### Analysis of osteoarthritis associated genes
  GeneCards [12] and PheGENI [13] databases were utilized to identify genes associated with OA. GeneCards is a comprehensive database that integrates information from genomic, transcriptomic, proteomic, and functional sources to provide detailed profiles of human genes. PheGENI (Phenotype-Genotype Integrator) links genotype data with phenotypic traits using information from genome-wide association studies (GWAS) and other large-scale projects. In this study, the keyword “Osteoarthritis” was searched in both databases to retrieve genes associated with the disease. Subsequently, the overlapping genes identified from both databases were used for downstream analyses. Gene ontology (GO) enrichment analyses of the selected gene set were performed using the SR Plot database [14], which provides a platform for systematic enrichment and visualization of biological pathways and molecular functions.


#### Analysis of lopinavir/ritonavir related genes
  PubChem [15], PharmGKB [16], Stitch [17], and Swiss Target Prediction databases [18] were utilized to analyze genes associated with Liponavir and Ritonavir. PubChem provides comprehensive information on chemical molecules and their biological activities. PharmGKB is a pharmacogenomics resource that links genetic variation to drug response. STITCH integrates known and predicted interactions between chemicals and proteins, while SwissTargetPrediction predicts potential drug targets based on chemical structure similarity. All analyses were conducted separately for both Ritonavir and Liponavir. Subsequently, the analysis continued by considering all identified targets. To identify the GO and biological processes associated with the identified gene targets, they were queried using the DAVID database [19], and the related biological processes were visualized with the SR Plot database.


#### Protein interaction map (PPI) of target genes
  GENEMENIA database [20] was utilized to identify the genes that interact with SOX9, HIF-1α, and IL-1β in cellular pathways. The GENEMENIA database was examined for all genes, revealing 100 genes with which they interacted.


#### Effects of lopinavir/ritonavir drugs on HIF-1α, SOX9 and IL-1β pathway
  The map of additional genes associated with HIF-1α, SOX9, and IL-1β was identified using the GENEMENIA database. Venn diagrams were created to illustrate whether Lopinavir/Ritonavir drugs share common genes with the identified targets of HIF-1α, SOX9, and IL-1β genes with which they interact. The Cytoscape program was subsequently utilized to unveil the interaction map of the identified common genes and to pinpoint hub genes. Hub genes were identified using the CytuHubba package with Degree, Closeness, and Betweenness parameters.


#### Determination of interactions of lopinavir/ritonavir drugs with identified hub genes
  All identified proteins were sourced from the AlphaFold database. The two-dimensional structure of the drug Lopinavir/Ritonavir was retrieved from the PubChem database. Docking studies were conducted using the CbDock2 database [21].


### In-vitro studies

#### Primary chondrocyte cultures and drug administration
  In response to in-silico studies, in-vitro studies were initiated. Approval was received from the Izmir Bakircay University Faculty of Medicine Local Ethics Committee (date: 30/05/2024 / number: 1603–1623) for the surgical resection of osteochondral tissues used in the preparation of human primary chondrocyte cultures.

  Patients had stage-4 gonarthrosis according to the Kellgren–Lawrence scale. Tissues obtained surgically from a total of eight cases, four males and four females, who did not respond to medical or conservative treatment and were to undergo total knee arthroplasty were included in this study. Osteochondral tissues of the distal femur and proximal tibia were resected during total knee arthroplasty. Primary chondrocyte cultures from osteochondral tissues were prepared according to the protocol of previous research [22].

  In the studies in the literature, the dose applied to cell cultures was taken as the basis. Therefore, the Lop/r (Kaletra, AbbVie Deutschland GmbH & Co. KG) concentration was determined to be 10.9 µM [5, 23].

  Before carrying out the experimental analyses, the half-life of Lop/r was taken as the basis. The time given for the half-life of this drug in the literature varies between 2.7 h and 7.4 days [5]. In this study, taking these half-lives into consideration, analyses were carried out at zero, 24, 48, and 72 h.


#### Morphological evaluation and cell viability analyses
  In the microscopic evaluation of cell morphology and ECM, an Olympus CKX41 invert microscope was used, and the images were analyzed and reported using the Olympus cell soft imaging system program. Two different staining techniques were used in the microscopic examinations. The first of these was acridine orange (AO) and propidium iodide (PI) staining (AO Cat no: A1301 and PI Cat no: J66584. AB, ThermoFisher Scientific Inc., ABD). The other was Hoechst 33,342 (Cat no: R37165, Invitrogen), which can be taken up by both live and dead cells. Hoechst and AO/PI-stained samples were viewed under a fluorescent microscope. Inverted microscopy and Hoechst staining were used to distinguish the morphology of chondrocytes, where live cells have flat nuclei with no condensed chromatin, and dead cells have small nuclei with condensed, sometimes fragmented chromatin.

  AO produces green fluorescence by penetrating the membrane of dead and living cells and staining the nucleus. On the other hand, PI only penetrates the ruptured membranes of dead nucleated cells and produces red fluorescence [5].

  In addition to these stainings, cell viability, toxicity, and proliferation analysis were performed by following the 3-(4,5-dimethylthiazol-2-yl)-2,5-diphenyltetrazolium bromide (MTT) cell commercial kit (Cat no: M6494, ThermoFisher Scientific Inc., ABD) instructions. For viability and cell toxicity measurements, a Mindray MR 96 microplate reader device from the People’s Republic of China was used.


#### Western blot analyses
  In addition to histopathological evaluation, HIF-1α (Cat no. MA1-516, Thermo Fisher Scientific Inc., ABD), IL-1β (Cat no. M421B, Thermo Fisher Scientific Inc., ABD), and SOX9 (Cat no. 14-9765-82, Thermo Fisher Scientific Inc., ABD) protein expressions, with and without Lop/r-treated human primary chondrocyte cultures, were determined by western blotting analysis after sodium dodecyl sulphate-polyacrylamide gel electrophoresis (SDS-PAGE). β-actin (Cat no. MA5-11869, Thermo Fisher Scientific Inc., ABD) was used as the internal control gene (housekeeping gene, endogenous control).

  The total protein concentration in the protein lysates obtained from each sample was determined spectrophotometrically with the Bradford assay (Pierce™ Bradford Protein Assay Kit Cat no: 23200 Thermo Fisher Scientific Inc., ABD), and immunoblotting was performed to determine protein expression levels. For this, the proteins were first separated using a 10% SDS-PAGE methodology. Then, polyvinylidene difluoride (PVDF) membranes were used to ensure the transfer of proteins. A WesternBreeze Chemiluminescent kit (Cat no. WB7104, Thermo Fisher Scientific Inc., ABD) was used for immunoblotting of HIF-1α, IL-1β, and SOX9 target proteins. Then, sequential washings were performed by adding primary antibodies specific to these proteins. After the addition of alkaline phosphatase-conjugated secondary antibody, the membranes were washed three times, and substrate solution was added [5]. The protein bands transferred to an X-ray film (Cat no. 34090, Thermo Fisher Scientific Inc., USA) were analyzed using ImageJ software, where the specific amount of protein in each sample was determined [5].


### Statistical analyses
  Statistical analyses of the data obtained in the Minitab (Version 22) package program were performed. For intergroup comparisons, an analysis of variance (ANOVA) was used first. If there was a statistical difference between groups, the significance of this difference was learned using Tukey’s honestly significant difference (HSD) test, which is one of the multiple comparison tests. In addition, the strength of the relationship between HIF-1α, IL-1β, and SOX9 target proteins and their relationships with each other were measured using the Pearson correlation test. Data were tested at a 95% confidence interval, with p < 0.05 considered statistically significant.


## Results

### In-silico studies
  The keyword “Osteoarthritis” was used in the GeneCards database, and 5394 associated genes were discovered. In the PheGENI database, 1016 associated genes were identified with the same keyword. 1014 common genes among these were identified, and enrichment analyses were conducted using the SR Plot database. The common genes associated with OA disease, sourced from the GeneCards and PheGENI databases, along with the results of the enrichment analysis of these genes, are presented in Fig. 1.

  Fig. 1Identification and Functional Analysis of Genes Associated with OA and Drug Targets of Lopinavir/Ritonavir. A: Venn diagram showing the number of genes associated with OA identified from GeneCards and PheGENI databases, revealing 1014 common genes. B: Gene interaction network illustrating the relationships between the 1014 OA-associated genes and other genes. C: Gene Ontology (GO) enrichment analysis of the biological processes affected by the 1,014 common genes. D: Predicted target genes of Lopinavir and Ritonavir obtained from multiple drug-target databases. E: Protein-protein interaction (PPI) network constructed for the identified target genes of Lopinavir and Ritonavir. F: GO enrichment analysis showing the biological processes influenced by the Lopinavir/Ritonavir-associated target genes

  In this study, HIF-1α, SOX9, and IL-1β genes were selected from the differentially expressed genes commonly identified in the GeneCards and PheGENI databases, based on their critical roles in OA pathogenesis and their overlap with predicted targets of Lop/r. Gene enrichment analysis revealed that HIF-1α is significantly associated with biological processes such as “regulation of angiogenesis,” “regulation of vasculature development,” and “response to molecule of bacterial origin,” all of which are closely linked to OA pathology. Notably, HIF-1α plays a dual role in OA: while it promotes chondrocyte survival and metabolic adaptation under physiological hypoxia—a characteristic feature of healthy cartilage—it may also contribute to pathological changes when overactivated, including abnormal angiogenesis and inflammation in the osteoarthritic joint environment. Therefore, interpretation of HIF-1α enrichment in this context should consider both its protective and potentially detrimental effects in OA progression. In the enrichment analysis, SOX9 was associated with processes such as “epithelial cell proliferation,” “regulation of epithelial cell proliferation,” and “collagen-containing extracellular matrix,” supporting its role in preserving tissue homeostasis during OA progression. Gene enrichment results demonstrated that IL-1β is significantly involved in processes such as “Regulation of inflammatory response,” “Positive regulation of cytokine production,” and “Cytokine activity.”

  Therefore, HIF-1α, SOX9, and IL-1β were selected as target genes in this study for their representation of key biological mechanisms implicated in OA pathophysiology.

  Subsequently, a total of 416 potential interacting genes were identified across all databases where gene targets for Lopinavir/Ritonavir drugs were screened. After removing genes that were repeated in different databases, 278 unique target genes were identified. The interaction network of genes targeted by Lopinavir/Ritonavir and the corresponding enrichment analysis results are presented in Fig. 1.

  Enrichment analysis of the biological processes affected by lopinavir and ritonavir revealed that these drugs predominantly influence key pathways associated with xenobiotic stimulus response, metabolic regulation, oxygen sensing, and cell cycle transitions. Notably, significant enrichment was observed in pathways such as “response to xenobiotic stimulus,” “steroid metabolic process,” “response to lipopolysaccharide,” and “response to oxygen levels,” suggesting that Lopinavir and Ritonavir may modulate cellular metabolism, inflammatory signaling, and hypoxia-related responses.

  Analyses were conducted to identify the genes that interact with HIF-1α, IL-1β, and SOX9, as well as the genes that Lop/r drugs can target, in order to find the hub genes these drugs can affect. For the HIF-1α, IL-1β, and SOX9 genes, the network of other interacting genes was identified using the GENEMENIA database, and the map of 100 interacting genes is presented in Fig. 2.

  Fig. 2Interaction Networks and Common Targets Between OA-Related Genes and Lopinavir/Ritonavir. A: Interaction network of HIF-1α with its associated genes, highlighting the common genes shared with the predicted targets of Lopinavir and Ritonavir. B: Interaction network of IL-1β with its associated genes, indicating the overlap with Lopinavir and Ritonavir predicted targets. Χ: Interaction network of SOX9 with its associated genes, showing the common genes between SOX9 interactors and the predicted targets of Lopinavir and Ritonavir. Venn diagrams below each network illustrate the number of overlapping genes between the interaction partners of HIF-1α, IL-1β, and SOX9 and the drug-predicted gene targets

  Additionally, Fig. 2 presents a Venn diagram demonstrating the common genes that interact with key cartilage-related regulators (HIF-1α, IL-1β, and SOX9) and are also predicted targets of Lopinavir/Ritonavir. HIF-1α, HDAC2, UBC, VEGFA, EP300, HSP90AA1, SMAD3, CDKN2A, CDK1, and CDK1 are the genes that HIF-1α and its interacting genes, along with Lopinavir/Ritonavir drugs, are predicted to target in common. The genes identified in common between IL-1β and its interacting genes, as well as Lopinavir/Ritonavir drugs, include IL-1β, CASP1, CXCL8, CASP3, IL6, NFKB1, RELA, CXCL1, CCL4, CCL3, TNF, NFKBIA, CCL2, LIF, ALOX5AP, CCL20, NOS3, ICAM1, NAMPT, REL, and CXCL5. The genes identified in common between SOX9 and its interacting genes, along with Lopinavir/Ritonavir drugs, are SOX9 and KCNA5.

  Following the identification of common genes potentially targeted by Lopinavir and Ritonavir in OA, hub genes were subsequently determined. As illustrated in Fig. 3, Cytoscape software was utilized to construct the gene interaction networks for HIF-1α and IL-1β, and CytoHubba plugin was employed to identify key hub genes based on Degree, Closeness, and Betweenness centrality metrics. The overlap among the identified hub genes, particularly HIF-1α, EP300, and CDKN2A, is further depicted through a Venn diagram, highlighting their potential central roles in the disease network.

  Fig. 3Network Analysis of Genes Interacting with HIF-1α and IL-1β and Identification of Hub Genes Targeted by Lopinavir/Ritonavir A: Visualization of HIF-1α and genes that interact with it, along with common genes targeted by Lopinavir/Ritonavir drugs using the Cytoscape program. B: Hub 5 genes of HIF-1α identified with the Degree parameter via CytoHubba. C: Hub 5 genes identified using the Closeness filter in CytoHubba. D: Hub 5 genes determined with the Betweenness parameter. E: IL-1β and the visualization of genes that interact with it, as well as the common genes targeted by Lopinavir/Ritonavir drugs using the Cytoscape program. F: IL-1β hub 5 genes identified by Degree, Betweenness, and Closeness filters, with the same genes appearing across all parameters. G: Venn diagram representation of HIF-1α, EP300, and CDKN2A genes identified as common among the hub 5 genes found using the Degree, Closeness, and Betweenness parameters of HIF-1α and its interacting genes

  After identifying the hub genes predicted to be targeted by Lopinavir/Ritonavir drugs, docking studies were conducted to assess the effect scores of these genes and the binding sites of the drugs. Table 1; Fig. 4 present the scores and visualizations from the ligand-protein docking study.

  Table 1Binding sites and scores of hub genes identified with lop/r drugsLigandProteinProtein Binding Score and RegionLopinavir/RitonavirKCNA51: -7,7/GLU222-GLU5302: -7,5/ PHE267-ARG406SOX91: -6,9/ LYS62-GLU1502: -6,9/ ARG107-ILE275IL-1β1: -7,7/ PRO102-GLN2322: -7,5/ PRO102-LYS210IL61: -7,2/ GLU87-SER1972: -6,6/ LEU61-ARG210TNF1: -7,3/ HIS91-VAL2262: 6,5/ VAL93-GLY224CCL21: -6,3/ VAL45-THR992: -6,0/ THR33-ALA76CXCL81: -6,8/ SER28-LYS812: -6,7/ TYR40-LYS91HIF-1α1: -8,1/ TYR66-PRO4922: -8,1/ PRO236-LEU539CDKN2A1: -6,7/ ASP105-ILE1452: -5,8/ ASP14-LEU117EP3001: -8,1/ THR1660-LYS17942: -8,0/ PRO1172-MET1835

  Fig. 4Docking results of hub genes identified with Lop/r drugs

  Docking studies indicate that IL-1β, HIF-1α, TNF, EP300, IL-6, and KCNA5 proteins, along with Lopinavir/Ritonavir (Lop/r) drugs, exhibit the highest interaction scores, suggesting a potential for strong molecular binding that may modulate critical pathways involved in OA progression.


### In-vitro studies
  The body mass indexes of the cases with four males and four females were overweight, between 25 kg/m2 and 29.9 kg/m2. While the average age was 65.5 ± 9.80 years, their age distribution varied between 48 and 80 years.

  In the microscopic analysis, no change in cell and extracellular matrix morphology was detected in the drug-treated samples (Fig. 5: Lanes 1 and 2). As can be clearly seen in the figure, no cell death was detected in the AO/PI stainings performed to detect possible cell death and confirm the results of the MTT analysis (Fig. 5: Lane 3).

  Fig. 5Inverted and fluorescent microphotograph section of the treated chondrocyte cultures. Lane 1 (a, b, c and, d) inverted microscopy under 20X magnification; Lane 2 (e, f, g and h; 10X magnification) chondrocyte cells stained by the Hoechst 33,258; Lane 3 (i, j, k and, l; 10X magnification) chondrocyte cells stained by AO/PI. Microscopic images are demonstrative. For all treatments, at least three cultures were established from samples obtained from eight cases (n = 8)

  When the percent viability was calculated by assuming 0 h as a control in the drug-applied cultures, it was determined that the viability decreased by approximately 14% at the 24th hour and by 13% at the 48th hour, but the viability and proliferation increased by 104% by the recovery of the cells at the 72nd hour, and this was statistically significant (p < 0.05) (Table 2).

  Table 2Results of evaluation of data obtained from MTT analysis with Tukey HSD test after one-way ANOVA with 95% confidence intervalVariableHoursMean ± StDevAdj SSAdj MSF-Valuep-ValueTukey’s HSD groupingTimes240.29271 ± 0.010.0006450.0003226.130.009B480.29386 ± 0.01B720.30500 ± 0.01AFrom A to B, with a being the highest and B the lowest cell proliferation and viability. Anova, analysis of variance; adj, adjusted; ss, sum of square; ms, mean square.

  When Western blotting results were evaluated, HIF-1α expression decreased 0.31-fold at the 24th hour, 0.44-fold at the 48th hour, and 0.61-fold at the 72nd hour. SOX9 expression decreased 0.17-fold at the 24th hour, 0.36-fold at the 48th hour, and 0.55-fold at the 72nd hour, while IL-1β expression was decreased 0.32-fold at the 24th hour, 0.42-fold at the 48th hour, and 0.60-fold at the 72nd hour compared to the control group samples without Lop/r application (Fig. 6).

  Fig. 6Western blots (left) and fold change graph of Hif1-α Sox9, and IL-1β proteins expressions (right) (n = 8). For each protein expression, the significance of the difference between groups is reported from A to D. The letter A represents the highest signal (protein expression) from antibodies bound to nitrocellulose membrane, while D represents the lowest signal

  Western blotting results of targeted protein expressions showed HIF-1α (F-value: 191.82; p = 0.000), SOX9 (F-value: 138.73; p = 0.000), and IL-1β (F-value: 184.08; p = 0.000). Again, there was a statistically significant difference between the groups.

  After the correlation evaluation of the target proteins between SOX9 and HIF-1α (r = 0.918; p = 0.000), between SOX9 and IL-1β (r = 0.902; p = 0.000), and between IL-1β and HIF-1α (r = 0.918; p = 0.000), it was understood that there was a strong positive and statistically significant relationship (Fig. 7).

  Fig. 7Matrix plot view of Hif-1α, SOX9, and IL-1β in Pearson correlation findings


## Discussion
  OA is characterized by the progressive degeneration of articular cartilage, closely linked to disruptions in metabolic homeostasis, chronic inflammation, and impaired cellular adaptation to hypoxia [24].

  In this study, we investigated whether the combination of Lopinavir/Ritonavir may affect biological processes associated with OA using network pharmacology methods. Potential effects were then assessed through in silico molecular docking analysis of the binding affinities of Lop/r and OA-related target genes with common hub genes linked to these proteins. The primary goal of the docking experiments was to determine the binding affinity of Lop/r drugs to proteins believed to play a significant role in the pathogenesis of OA, thereby predicting potential therapeutic effects. Subsequently, in vitro experiments were conducted to confirm the in silico findings.

  The results indicate that Lop/r binds with high affinity to proteins linked to inflammation, hypoxia response, and epigenetic regulation, particularly HIF-1α, EP300, TNF, IL6, KCNA5 and IL-1β (binding score: -8.1). The results of docking studies and in-vitro studies support each other. This suggests that Lop/r drugs extend beyond antiviral effects and may serve as potential candidates for drug repurposing in chronic inflammatory degenerative diseases such as OA.

  Strong binding to transcriptional regulators like HIF-1α and EP300 implies that Lop/r may be involved in hypoxia response and cartilage degeneration processes. Binding to proinflammatory cytokines such as IL-1β, IL6, and TNF supports the notion that Lop/r may suppress inflammatory responses. In this context, docking studies reveal the potential of Lop/r to act on multiple targets in the treatment of OA; from a network pharmacology perspective, these findings advocate for the evaluation of Lop/r as a polypharmacologic agent.

  In addition, there are very few studies in the literature that include signaling pathways related to the molecular mechanisms of OA and pyroptosis, apoptosis, and necroptosis (PANoptosis) at the transcriptome level; studies at the molecular level can provide important data on this subject [25].

  Although the exact mechanism of HIFs in OA pathogenesis needs to be further elucidated, many drugs that act directly or indirectly on HIF signaling pathways have been validated in animal experiments and are considered promising treatments for OA. In a study on the mechanism of cartilage metabolism, it was reported that HIFs are key regulatory genes that maintain the balance between cartilage catabolism and ECM anabolism, and it has been emphasized that HIFs will be the main target genes in the future treatment of OA [26].

  In the future treatment of OA pathology, which is related to the imbalance between anabolic and catabolic signaling pathways at the subchondral level [27] or related to the loss of both cell and tissue homeostasis of chondrocytes and cartilage tissue due to reasons such as aging and/or overuse, pharmacological targeting of these biological pathways is very important [28].

  As is known, all mammals have certain compensatory mechanisms to detect hypoxia and respond to correct it. The most important component of this response is mediated by HIFs [29]. Among these, HIF-1α in particular is responsible for the expression of many genes that regulate cell survival and metabolism in hypoxic conditions and also increase angiogenesis to alleviate hypoxia [30].

  HIF-1α, a gene protein whose activation is the primary defensive mechanism against hypoxia in the tissue, has been reported to be the main regulator of oxygen distribution and use in the tissue [31]. However, it has also been reported that, in tissue ischemia, increased HIF-1α activity stimulates the release of the angiogenic growth factor necessary for vascular remodeling and collateral formation [31]. Decreased gene expression of HIF-1α may lead to impaired adaptive responses to hypoxia [31]; HIF-1α functions in the preservation of cellular oxygen and plays a key role in energy production and biochemical reactions in the mitochondria [32]. However, it has been emphasized in the literature that not only the increase or decrease in the expression level of HIF-1α but also its balance is important for intracellular homeostasis [33].

  During the progression of OA, cartilage is exposed to exacerbated hypoxic conditions, mechanical stress, and local inflammation. In response, the expression of HIF-1α increases to regulate chondrocyte activity and metabolism through the induction of downstream factors such as vascular endothelial growth factor [34]. It has also been reported in the literature that the role of HIF-1α in OA remains unclear under the conditions of hypoxia, oxidative stress, and inflammation [34].

  HIF-1α serves as a key transcription factor in the adaptation to hypoxic conditions and plays a central role in regulating metabolic pathways, angiogenesis mechanisms, and inflammatory responses [35].

  In a study in which abnormal subchondral bone restructured caused by overactivated osteoclastogenesis led to articular cartilage degeneration and OA progression, but the mechanism was unclear, a mouse OA model with anterior cruciate ligament transection was used. The research results emphasized that cartilage degeneration occurred in association with the widespread expression of HIF-1α in chondrocytes. Additionally, HIF-1α stabilization has been reported to delay cartilage degeneration [36]. Another issue that is at least as important for HIF-1α is the claim that stabilization of HIF-1α can alleviate OA by increasing mitophagy [37]. It has also been reported in another study that not only stabilization but also inhibition of HIF-1α can indirectly alleviate ferroptosis-related OA [38].

  In this study, it was observed that HIF-1α protein expression decreased by 0.31-fold at the 24th hour, 0.44-fold at the 48th hour, and 0.61-fold at the 72nd hour, compared to the control group without Lop/r application. While the decrease in HIF-1α expression can be interpreted as a potentially beneficial outcome due to its association with reduced angiogenesis and inflammation, this interpretation must be approached with caution. HIF-1α has been shown to exert both protective and pathological effects in OA depending on the context and disease stage. It plays a critical role in maintaining cartilage homeostasis under physiological hypoxia by supporting chondrocyte survival and ECM integrity. However, its overexpression in later stages of OA may contribute to abnormal angiogenesis and catabolic signaling. Therefore, the downregulation of HIF-1α observed in this study should not be regarded as solely advantageous; rather, it highlights the complexity of HIF-1α signaling in OA pathophysiology and the need for a finely tuned therapeutic approach. The observed reduction in HIF-1α protein expression levels following Lop/r treatment aligns with the strong binding affinity identified in docking assays, indicating a direct modulatory effect.

  Apart from HIF-1α, another popular genetic pathway that is emphasized in the literature to be targeted in OA treatment is SOX9.

  The SOX9 transcription factor is essential for embryonic chondrogenesis, but its postnatal roles remain unclear despite evidence that it is downregulated in OA and heterozygously inactivated in campomelic dysplasia, a severe skeletal dysplasia characterized by postnatal small stature and kyphoscoliosis [39]. SOX9, a chondrocyte-specific transcription factor, has been reported to affect the concentration of vital type-2 collagen in the content of both the chondrocyte in the general articular cartilage as well as the chondrogenic nucleus pulposus cells. In fact, it was underlined that the expression level of SOX9, which is claimed to increase type-2 collagen production, decreases cartilage degeneration [40].

  SOX9 functions as a pivotal regulator in cartilage development, cellular differentiation, and the maintenance of extracellular matrix integrity [41].

  SOX9, expressed early in the mesenchymal tissue, is vital for both cartilage and skeleton formation throughout embryo development. When the activity of SOX9, which is also known to regulate the set of cartilage ECM genes, decreases, major skeletal abnormalities occur due to the inhibition of the production of cartilage ECM proteins, such as type II collagen, and aggrecan, a proteoglycan. Additionally, increased expression of SOX9, which has been emphasized as playing a vital role not only in embryo development but also after birth, inhibits IL-1β-induced inflammation in human chondrocytes, and it has been reported that SOX9 can prevent OA by protecting chondrocytes. In summary, the common scientific consensus is that SOX9 is required for cartilage ECM gene expression.

  No findings were observed in our morphological examinations that Lop/r could cause ECM destruction at the doses and durations applied within the scope of this study. However, in this study, it was determined that SOX9 protein expression decreased by 0.17-fold at the 24th hour, 0.36-fold at the 48th hour, and 0.55-fold at the 72nd hour compared to the control group without Lop/r application. This significant decrease in SOX9 expression shows that it should be taken into consideration that the drug may affect ECM continuity, especially in long-term use. Given that SOX9 is a master regulator of chondrogenesis and is essential for maintaining cartilage ECM integrity, its downregulation may indicate a risk of compromised matrix homeostasis.

  Notably, SOX9 is known to be positively regulated by HIF-1α, which promotes SOX9 transcription under hypoxic conditions to support ECM production and chondrocyte survival [42, 43].

  The simultaneous downregulation of both HIF-1α and SOX9 observed in this study suggests a potentially unfavorable effect on cartilage homeostasis, despite the anti-inflammatory benefits indicated by reduced IL-1β expression. This dual reduction may reflect a broader suppression of chondrocyte activity rather than selective targeting of catabolic pathways. Therefore, while Lop/r may initially alleviate inflammation, its long-term effects on cartilage regeneration and ECM preservation warrant further investigation. Supporting this, previous studies have demonstrated that HIF-1α-SOX9 axis integrity is critical for chondrocyte phenotype maintenance, and disruptions in this signaling cascade may accelerate cartilage degeneration [44, 45]. Further research is needed to elucidate whether the observed protein expression changes are dose- or time-dependent and to assess whether compensatory mechanisms may mitigate their long-term impact. The noted reduction in SOX9 expression could be a downstream effect of the modulation of upstream regulators like HIF-1α, IL-1β and KCNA5 which exhibit a strong binding affinity with Lop/r in silico.

  Inflammatory molecules play an important role in the anabolic and catabolic signaling pathways. IL-1β is a pro-inflammatory catabolic cytokine that causes proinflammation by leading chondrocytes to apoptosis. Thus, this molecule causes intervertebral disc degeneration by affecting the annulus fibrosus and chondrocyte-like nucleus pulposus cells, or causes OA by rupturing chondrocytes. It even uses IL-1β to induce inflammation in chondrocytes of living mammalian subjects, both in cell culture [46], and in an in vivo experimental study [47, 48]. Meanwhile, IL-1β, a potent proinflammatory cytokine, plays a major role in shaping the inflammatory microenvironment characteristic of OA [48]. Again, an in vivo study reported that IL-1β causes ECM degradation and cell apoptosis by significantly activating the NF-kB signaling pathway [49].

  In this study, it was observed that IL-1β expression decreased by 0.32-fold at the 24th hour, 0.42-fold at the 48th hour, and 0.60-fold at the 72nd hour in the Lop/r applied group compared to the control group without Lop/r application. This suggests that it can be used in the treatment of OA by preventing or regressing cartilage degeneration. The observed reduction IL-1β protein expression levels following Lop/r treatment aligns with the strong binding affinity identified in docking assays, indicating a direct modulatory effect.

  In the literature, we seek to answer the question of whether Lop/r, an HIV protease inhibitor, can improve disc physiology and slow down intervertebral disc degeneration through in silico and in vitro experimental methods; IL-1β, SOX9, HIF-1α, and NF-κB protein expressions were tested [5]. They reported that annulus fibrosus and nucleus pulposus cell proliferation decreased in the Lop/r applied group, but no cell deaths were observed. It has been reported that Lop/r application suppresses IL-1β and NF-κB and induces SOX9 and HIF-1α. In addition, they concluded that Lop/r application can make significant contributions to pharmaco-regenerative treatment methods for intervertebral disc degeneration [5].

  The observed enrichment of biological processes including ‘cell cycle G1/S phase transition’ and ‘G1/S transition of mitotic cell cycle’ indicates a potential role for Lopinavir and Ritonavir in regulating chondrocyte proliferation and cell cycle progression, both of which are pivotal to cartilage preservation and regenerative mechanisms. Collectively, these findings suggest that Lopinavir and Ritonavir may impact multiple cellular mechanisms relevant to OA pathophysiology. By influencing metabolic regulation, inflammatory responses, oxidative stress pathways, and cell cycle dynamics, these drugs may offer novel insights into the modulation of disease progression and the development of new therapeutic strategies for OA. Importantly, the biological pathways modulated by Lopinavir and Ritonavir are closely aligned with the molecular mechanisms governed by IL-1β, HIF-1α, and SOX9, further supporting their potential relevance in targeting key processes underlying OA progression.

  As a result, in this study, it was understood that Lop/r was not toxic to human chondrocyte cells and did not cause cell death. It was observed that it did not disrupt the morphology of chondrocytes and ECM. However, it was also understood that it caused a decrease in SOX9, HIF-1α, and IL-1β protein expressions. Moreover, a strong positive relationship was observed between SOX9 and Hif-1α, between SOX9 and IL-1β, and between IL-1β and HIF-1α. All these findings were found to be statistically significant.

  Despite the promising in vitro and in silico results, this study has several limitations. First, the findings are based solely on preclinical models using human primary chondrocyte cultures and computational predictions, which do not fully replicate the complex systemic environment of an osteoarthritic joint. The absence of in vivo experiments limits the ability to evaluate pharmacokinetic properties, long-term safety, and off-target effects of Lop/r in joint tissues. Additionally, individual genetic, epigenetic, and environmental variations that may influence drug response were not accounted for in this controlled in vitro setting.

  Future studies should aim to validate these results in relevant animal models of osteoarthritis to assess tissue-specific effects, dosing strategies, and long-term outcomes. Moreover, exploring the role of other regulatory pathways and transcriptional networks potentially affected by Lop/r could provide a more comprehensive understanding of its therapeutic profile.


## Conclusion
  The observed decrease in IL-1β and HIF-1α expressions suggests that Lop/r may have potential therapeutic effects in the context of OA by modulating inflammatory pathways. However, the concurrent reduction in SOX9 expression indicates that prolonged exposure could pose risks related to ECM degradation and cartilage integrity. While the use of human primary chondrocyte cultures lends physiological relevance to our findings, these results remain preclinical and may be influenced by individual genetic, epigenetic, and environmental factors in vivo. Therefore, further in vivo and clinical studies are necessary to validate the safety, efficacy, and long-term impact of Lop/r in the treatment of OA.


## Electronic supplementary material
  Below is the link to the electronic supplementary material.

  Identification of Common Targets Between Lop/r and Osteoarthritis-Related Genes: A Bioinformatic, Molecular Docking, and In-vitro verification Study


## Acknowledgements
  None.