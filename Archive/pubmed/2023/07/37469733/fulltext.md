# Network pharmacology and molecular docking-based analyses to predict the potential mechanism of Huangqin decoction in treating colorectal cancer


## BACKGROUND
  To analyze the potential action mechanism of Huangqin decoction (HQD) in colorectal cancer (CRC) treatment on the basis of network pharmacology and molecular docking.


## AIM
  To investigate the molecular mechanisms of HQD for CRC treatment by using network pharmacology and molecular docking.


## METHODS
  All HQD active ingredients were searched using the Systematic Pharmacology and Traditional Chinese Medicine Systems Pharmacology databases and the Bioinformatics Analysis Tool for Molecular Mechanisms in traditional Chinese medicine. Then, the targets of the active ingredients were screened. The abbreviations of protein targets were obtained from the UniProt database. A “drug–compound–target” network was constructed to screen for some main active ingredients. Some targets related to the therapeutic effect of CRC were obtained from the GeneCards, DisGeNET, Therapeutic Target Database, and Online Mendelian Inheritance in Man databases. The intersection of targets of Chinese herbs and CRC was taken. A Venn diagram was drawn to construct the intersection target interactions network by referring to the STRING database. Topological analysis of the protein interaction network was performed using Cytoscape 3.7.2 software to screen the core HQD targets for CRC. The core targets were imported into the DAVID 6.8 analysis website for gene ontology and Kyoto Encyclopedia of Genes and Genomes enrichment analyses and visualization. Finally, molecular docking was performed using AutoDockTool and PyMOL for validation.


## RESULTS
  In total, 280 potential drug-active ingredients were present in HQD, including 1474 targets of the drug-active ingredients. The main active ingredients identified were betulin, tetrahydropalmatine, and quercetin. In total, 10249 CRC-related targets and 1014 drug-disease intersecting targets were identified, including 28 core targets of action such as Jun proto-oncogene, AP-1 transcription factor subunit, signal transducer and activator of transcription 3, tumor protein p53, vascular endothelial growth factor, and AKT serine/threonine kinase 1. The gene ontology enrichment functional analysis yielded 503 enrichment results, including 406 biological processes that were mainly related to the positive regulation of both gene expression and transcription and cellular response to hypoxia, etc. In total, 38 cellular components were primarily related to polymer complexes, transcription factor complexes, and platelet alpha granule lumen. Then, 59 molecular functions were closely related to the binding of enzymes, homologous proteins, and transcription factors. The Kyoto Encyclopedia of Genes and Genomes pathway enrichment analysis yielded 139 enrichment results, involving epidermal growth factor receptor tyrosine kinase inhibitor resistance and HIF-1 and mitogen-activated protein kinase signaling pathways.


## CONCLUSION
  HQD can play a role in CRC treatment through the “multi-component-target–pathway”. The active ingredients betulin, tetrahydropalmatine, and quercetin may act on targets such as Jun proto-oncogene, AP-1 transcription factor subunit, signal transducer and activator of transcription 3, tumor protein p53, vascular endothelial growth factor, and AKT serine/threonine kinase 1, which in turn regulate HIF-1 and mitogen-activated protein kinase signaling pathways in CRC treatment. The molecular docking junction clarified that all four key target proteins could bind strongly to the main HQD active ingredients. This indicates that HQD could slow down CRC progression by modulating multiple targets and signaling pathways.


## INTRODUCTION
  The incidence of colorectal cancer (CRC) has continued to increase, accounting for nearly 10% of cancer patients. CRC is the second most common cause of cancer death[1,2]. Many pathogenic factors could cause CRC such as obesity, poor diet, alcohol addiction, and genetic mutations or familial inheritance[1-4]. According to domestic statistics, CRC incidence in China has increased each year from 1990 to 2019. Using the ARIMA model, the standardized CRC incidence in China is predicted to reach 33.93/100000 in 2025, bringing a huge burden to the Chinese healthcare system[5]. Radical surgical resection, chemotherapy, radiotherapy, and targeted therapy are the current main treatment modalities for CRC[6]. However, these treatments are generally deficient as they are prone to recurrence and side effects. Therefore, finding effective drugs with few side effects in CRC treatment is valuable.

  CRC is classified as “viscera toxin” and “intestinal accumulation” in traditional Chinese medicine (TCM). In the early CRC stage, clearing heat, regulating qi, dispelling dampness, eliminating phlegm, removing blood stasis, detoxifying, soft, and firm dispersing, and other treatment methods are used in TCM for dispelling evil spirits[7]. Huangqin Decoction (HQD) is derived from “Treatise on Febrile Diseases: Taiyang and Shaoyang combined disease, diarrhea, treat with HQD.” The HQD recipe consists of Scutellariae Radix (3 taels), Paeonia lactiflora Pall. (2 taels), Glycyrrhiza uralensis Fisch. (2 taels), and Ziziphus jujuba Mill. (12 pieces). Scutellariae Radix for the king, bitter, and cold can clear heat. Paeonia lactiflora Pall. can relieve pain. HQD can supply the qi. The combination of various drugs can clear heat and relieve pain[8]. HQD has been proven to treat CRC clinically with a remarkable effect, but the exact mechanism has not been elucidated.

  TCM is based on the formulation principles of “king, minister, adjuvant, and ambassador” and incompatibility taboo. With the characteristics of the multi-component-target-pathway and synergistic treatment, TCM has great potential to improve cancer symptoms. Network pharmacology is an emerging discipline based on systems biology theories. It analyses and calculates the relationship between relevant drugs and diseases through drug-compound-target interaction networks[9]. By inferring the treatment effects and regulatory mechanisms of drugs in disease through multiple targets, it also provides new methods for TCM application, thereby facilitating the promotion of the development and heritage of Chinese herbs and compounds. Using informatics, molecular docking predicts the potential binding conformation of ligands and receptors. It also verifies the binding affinity of core components and targets. We here constructed a drug-compound-target network according to the HQD active ingredients by using network pharmacology and molecular docking and thus analyzed and calculated the molecular mechanism and regulation signal pathways of HQD for CRC treatment. The study findings also provided a certain theoretical basis for future studies.


## MATERIALS AND METHODS

### Screening of bioactive components and targets of HQD
  In this study, Traditional Chinese Medicine Systems Pharmacology and Bioinformatics Analysis Tool for Molecular Mechanisms in traditional Chinese medicine databases were used to search the constituent herbs of HQD and their chemical and pharmacological data. Duplicate compounds were combined and removed to gather information about the HQD active ingredients. The targets of all these active ingredients were further searched and screened by referring to Traditional Chinese Medicine Systems Pharmacology and UniProt to realize the herb targets of HQD. All database URLs in this study are shown in Table 1.


### Construction of drug-compound-target interaction networks
  We analyzed the obtained components and targets and constructed a network of “drug-compound-target” by using Cytoscape 3.7.2. In this network, nodes represent drugs, compounds, and targets, and edges represent the relationship between the three nodes. We analyzed the number of connections of each node by calculating the “degree” value.


### Screening for CRC-related targets
  The term “colorectal cancer” was searched, and potential targets were screened for in GeneCards, TTD, OMIM, and DisGeNET databases. All CRC-related targets were acquired after removing duplicate targets. HQD action targets and CRC-related targets were imported into the online Wayne tool to map the intersection of HQD and CRC targets and visualize the results.


### Construction of the protein-protein interaction network and screening for core targets
  To elucidate the functional interactions between the screened proteins, the intersecting targets were put into the STRING database to construct the protein-protein interaction (PPI) network. This PPI network was then put into Cytoscape 3.7.2, and the CytoNCA plugin was applied to filter core proteins based on betweenness (BC), closeness (CNC), degree (DC), eigenvector (EC), local average connectivity (LAC)-based method, and network (NC) 2 times the median value of the core proteins.


### Gene ontology function and Kyoto Encyclopedia of Genes and Genomes pathway enrichment analyses
  We obtained information about the primary biological processes and signaling pathways by importing the screened core targets into the DAVID 6.8 database for gene ontology (GO) function and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment analyses. Then, the enrichment results were visualized using the LianChuan BioCloud platform.


### Molecular docking of active ingredients to core targets
  The three-dimensional (3D) structure of the core target proteins was first obtained from the PDB database. The MOL2 file of the core active compounds was then obtained from the PubChem platform. Chem 3D was used to optimize the total amount of core component energy. PyMOL software was used to optimize the number of core target proteins removed for water molecule hydrogenation and charge calculation. Molecular docking and binding activity analyses were performed using the AutoDock Vina program. Finally, docking sites were visualized on the PLIP platform. When the binding energy of the molecular docking conformation was lower, the binding conformation was more stable. This reflects the greater likelihood of binding between the receptor molecule and ligand. Therefore, only the highest absolute value of binding energy for each molecular docking pair was retained for the docking results.


## RESULTS
  We identified the HQD active ingredients and the potential therapeutic targets and mechanisms of HQD in CRC treatment by conducting network pharmacology and functional gene pathway analyses.


### Screening of bioactive ingredients and targets of HQD
  Among the active ingredients obtained, 46 were Scutellariae Radix, 28 were Paeonia lactiflora Pall., 160 were Glycyrrhiza uralensis Fisch., and 58 were Ziziphus jujuba Mill. Then, 280 compounds and 1474 potential targets were obtained for the action of the ingredients after removing the duplicate information.


### Construction of drug-compound-target network
  The network “drug-compound-target” was built using Cytoscape 3.7.1 software. It included 1695 nodes and 5567 edges (Figure 1), with red squares representing drug co-components. The specific information is presented in Table 2. The HQD compounds with high activity are betulin, tetrahydropalmatine, and quercetin, which may be crucial for CRC treatment.


### Screening for CRC-related targets
  We obtained 10249 CRC-related targets for its treatment from the disease databases of Genecards, OMIM, DisGeNET, and TTD. The targets of both CRC and the HQD active ingredients were imported into the Venn diagram editing website, and then 1014 potential targets of HQD in CRC treatment were identified (Figure 2).


### PPI network analysis and key target screening
  The STRING was used to obtain key proteins for CRC treatment with HQD. The analysis data were imported into Cytoscape 3.7.2. Based on the BC, CNC, DC, EC, LAC, and NC values of topological parameters calculated using CytoNCA, 28 targets that play key roles in CRC, such as Jun proto-oncogene, AP-1 transcription factor subunit (JUN), signal transducer and activator of transcription 3 (STAT3), tumor protein p53 (TP53), vascular endothelial growth factor (VEGFA), and AKT serine/threonine kinase 1 (AKT1) were screened (Figure 3). These targets could be considered the HQD core targets in CRC treatment.


### GO function and KEGG pathway enrichment analyses
  We imported 28 core targets into the DAVID 6.8 database to identify the relevant HQD biological functions in CRC treatment by analyzing GO functional enrichment. This analysis revealed 503 enrichment results, including 406 biological processes, 38 cellular components, and 59 molecular functions. The biological processes were mainly related to the positive regulation of gene expression and transcription and cellular response to hypoxia. The cellular components were principally related to the macromolecular complex, transcription factor complex, platelet alpha granule lumen, etc. The molecular functions primarily involved the binding of enzymes, identical proteins, and transcription factors. The GO enrichment results were sorted from the smallest to the largest P value. The top 10 entries were selected to create a histogram (Figure 4). To determine the potential mechanism underlying CRC treatment with HQD, we performed the KEGG pathway enrichment analysis and obtained 139 HQD-associated signaling pathways for CRC treatment. The top 20 pathways were visualized in descending order of the P value (Figure 5). These mainly included signaling pathways such as epidermal growth factor receptor (EGFR) tyrosine kinase inhibitor resistance, HIF-1, and mitogen-activated protein kinase (MAPK), suggesting that HQD can treat CRC through these pathways.


### Molecular docking of potential active ingredients to core target proteins
  Five key target proteins (JUN, STAT3, TP53, VEGFA, and AKT1) were molecularly docked to three core components (betulin, tetrahydropalmatine, and quercetin) to assess the binding capacity of the target and ligand proteins. The binding capacity was predicted using AutoDock software, with binding energies typically < -5.0 kcal·mol−1 indicating significant binding activity between the molecules. All three active components exhibited a strong binding capacity to JUN, TP53, VEGFA, and AKT1 (Table 3), with birudinol failing to bind well to STAT3. The 3D model plots of the three active ingredients docked with JUN, TP53, VEGFA, and AKT1 were visualized using PyMOL and PLIP software (Figures 6-8).


## DISCUSSION
  According to TCM, the diseased region in CRC is the large intestine. Moreover, CRC is closely related to the spleen and stomach. “Miraculous Pivot” mentioned that “The injury of the stomach, the blood overflow in the parenteral, the parenteral cold, the juice foam and blood phase kneading, the combination of condensation cannot be dispersed, and the product into.” Several clinical studies have retrospectively investigated the TCM symptoms of CRC patients and their associated factors. These studies have found that the most common TCM classification of CRC is the syndrome of damp heat accumulation[10-12]. HQD was first mentioned by Zhang Zhongjing in “Treatise on Febrile Diseases.” According to this monograph, HQD could clear away heat and relieve pain and is a classic therapeutic formula for damp heat in Chinese medicine.

  We conducted a network pharmacological analysis to determine active compounds, potential targets, and action mechanisms of HQD in CRC treatment. In total, 280 core ingredients of HQD were screened. The topological analysis of the “drug-compound-target” network revealed that the top-ranked compounds were betulin, tetrahydropalmatine, and quercetin. These may be the potential compounds of HQD in CRC treatment. Among them, betulinol induced apoptosis of CRC cells through the MAPK signaling pathway and significantly inhibited malignant metastasis of CT26 cells in the lungs[13]. The therapeutic efficacy of tetrahydropalmatine has been demonstrated in various cancers[14,15], suggesting that tetrahydropalmatine can be used as a potential novel therapeutic agent for CRC patients. Quercetin, a flavanol compound, has various biological activities, such as antioxidant activity. Quercetin could interfere with CRC development in various ways, such as inhibiting growth and proliferation and affecting the cycle of CRC cells. Thus, it could induce apoptosis and inhibit metastasis and invasion of CRC[16-19]. The aforementioned results proved that the main active ingredients of HQD play a crucial role in CRC treatment, suggesting that HQD is an effective therapeutic formula for CRC treatment.

  On the basis of BC, CNC, DC, EC, LAC, and NC, the top five key targets, namely JUN, STAT3, TP53, VEGFA, and AKT1, were finally screened through cascading analysis of key targets using the PPI network. JUN is a transcription factor that recognizes and binds to the enhanced heptameric motif 5’-TGA[CG]TCA-3’. JUN can upregulate HuR expression by inhibiting miR-22 transcriptional regulation, which in turn leads to proliferation, migration, and tumor growth in CRC cells[20].

  STAT3, a member of the STAT cytoplasmic transcription factor family, is the family member most associated with CRC development[21]. Large amounts of STAT3 are activated in CRC to promote tumor growth, invasion, migration[22], and proliferation of cancer cells. These features suggest that STAT3 can be used as a therapeutic target in CRC.

  TP53 encodes the tumor suppressor p53, which is the major driver gene for suppressing the development of various cancers. The TP53 mutation has been observed in up to 80% of patients with advanced metastatic CRC[23], and this mutation can lead to poor prognosis in various cancer patients, including CRC patients[24].

  VEGFA, the subtype of the vascular endothelial growth factor (VEGF), has a critical role in angiogenesis. According to some studies, tumor growth, spread, and metastasis depend on angiogenesis. VEGFA is a major proangiogenic factor in CRC and is strongly related to metastasis in this cancer[25]. The receptor targeting the tyrosine kinase VEGF can inhibit the angiogenesis, proliferation, and growth of liver metastases in CRC. This anti-angiogenic therapy significantly increases endothelial and tumor cell apoptosis, thereby suggesting that VEGF has a crucial role in the tumor endothelium[26].

  AKT is a member of the serine/threonine kinase proto-oncogene family that regulates different inflammatory and metabolism-related signaling pathways and is involved in cancer cell proliferation, survival, and metabolic processes[27]. Approximately 70% of CRC exhibits highly activated AKT, which is closely associated with cancer development.

  During molecular docking, the three core ingredients of HQD exhibited strong affinity to the four key target proteins, confirming the targeting effect of HQD in CRC treatment. The predicted results thus theoretically elucidate the ameliorative effect of HQD on CRC and help in the further investigation of the action mechanism of HQD or its bioactive compounds as an alternative treatment for CRC. The GO functional enrichment suggested that CRC treatment with HQD was mainly related to the positive regulation of gene expression and transcription as well as a cellular response to hypoxia. The KEGG pathway revealed that the pathways most closely related to CRC were EGFR tyrosine kinase inhibitor resistance, and HIF-1 and MAPK signaling pathways.

  EGFR is closely associated with CRC recurrence and deterioration. Studies have demonstrated that miR-323a-3p can promote the apoptosis of CRC cells by directly targeting EGFR signaling[28]. Acquired resistance to 5-fluorouracil is a clinical challenge for CRC treatment. The HIF-1α and 5-fluorouracil combination significantly enhances the antitumor effects of 5-fluorouracil[29]. Therefore, targeting HIF-1α could act as an effective therapeutic strategy for 5-fluorouracil-resistant CRC. The MAPK signaling pathway is activated by peptide growth factors, cytokines, oxidative stress, etc. This pathway then regulates tumor cell proliferation, differentiation, survival, and death[30]. Several MAPK, ERK, c-Jun, and JNK subfamilies are involved in CRC pathogenesis[31], with ERK/MAPK playing a crucial role in cell proliferation[30]. Therefore, EGFR tyrosine kinase inhibitor resistance and HIF-1 and MAPK signaling pathways are closely linked to CRC development.


## CONCLUSION
  In conclusion, by analyzing “multi-components-targets-biological pathways,” this study found that HQD could exert therapeutic effects. Our findings also provide a clue regarding the theoretical basis for the active ingredients of HQD that are most effective in CRC treatment. However, because of the deficiencies of network pharmacology and molecular docking, follow-up in vivo and in vitro experiments are warranted to verify the action mechanism of HQD in CRC treatment.


## ARTICLE HIGHLIGHTS

### Research background
  Colorectal cancer (CRC) is the second most common cause of cancer death in recent years. CRC is a danger to human health.


### Research motivation
  The side effects caused by radiotherapy severely hinder the treatment progress of CRC patients. Huangqin decoction (HQD) can improve the immunity of CRC patients and enhance their quality of life.


### Research objectives
  This study exploited network pharmacology and molecular docking to uncover the potential targets and mechanisms of HQD for CRC treatment. It also provided a molecular biological basis for CRC treatment with HQD in a clinical setting.


### Research methods
  This study involved preliminary exploration of the potential targets and mechanisms of HQD for CRC treatment by using network pharmacology and molecular docking.


### Research results
  The active ingredients betulin, tetrahydropalmatine, and quercetin in HQD may act on targets such as Jun proto-oncogene, AP-1 transcription factor subunit, signal transducer and activator of transcription 3, tumor protein p53, vascular endothelial growth factor, and AKT serine/threonine kinase 1, which in turn regulate HIF-1 and mitogen-activated protein kinase signaling pathways in CRC treatment.


### Research conclusions
  HQD could treat CRC by regulating HIF-1 and mitogen-activated protein kinase signaling pathways.


### Research perspectives
  At present, many shortcomings still exist in studying the action mechanisms of herbal medicine for various diseases on the basis of network pharmacology. Future research should be focused on in vivo and in vitro experiments to verify the key targets and type pathways and then combined proteomics and metabolomics to more systematically elucidate the action mechanism of HQD in CRC treatment.


## Data sharing statement
  No additional data are available.