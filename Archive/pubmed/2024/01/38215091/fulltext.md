# Preliminary study on molecular mechanism of COVID-19 intervention by Polygonum cuspidatum through computer bioinformatics


## Abstract
  To explore the mechanism of action of Polygonum cuspidatum in intervening in coronavirus disease 2019 using a network pharmacology approach and to preliminarily elucidate its mechanism. The active ingredients and action targets of P cuspidatum were classified and summarized using computer virtual technology and molecular informatics methods. The active ingredients and relevant target information of P cuspidatum were identified using the TCM Systematic Pharmacology Database and Analysis Platform, the TCM Integrated Pharmacology Research Platform v2.0, and the SwissTarget database. The GENECARDS database was used to search for COVID-19 targets. The STRING database was analyzed and combined with Cytoscape 3.7.1 software to construct a protein interaction network map to screen the core targets. Kyoto Encyclopedia of Genes and Genomes pathway enrichment analysis was then performed. The core compound, polydatin, was selected and the core targets were analyzed by computer virtual docking using software such as discovery studio autodock tool. In vitro cell models were constructed to experimentally validate the activity of the core compound, polydatin. By computer screening, we identified 9 active ingredients and their corresponding 286 targets from P cuspidatum. A search of the GENECARDS database for COVID-19 yielded 303 core targets. By mapping the active ingredient targets to the disease targets, 27 overlapping targets could be extracted as potential targets for the treatment of COVID-19 with P cuspidatum. In addition, the enrichment analysis of Kyoto Encyclopedia of Genes and Genomes pathway on core targets showed that the coronavirus disease, MAPK signaling pathway, NF kappa B signaling pathway, and other signaling pathways were highly enriched. Combined with the degree-high target analysis in the protein interaction network, it was found to be mainly concentrated in the NF-kappaB (NF-κB) signaling pathway, indicating that the NF-κB signaling pathway may be an important pathway for P cuspidatum intervention. In vitro assays showed no effect of 0.1 to 10 μM polydatin on cell viability, but an inhibitory effect on the transcriptional activity of NF-κB-RE. Molecular docking showed stable covalent bonding of polydatin molecules with Il-1β protein at residue leu-26, TNF protein ser-60, residue gly-121, and residue ile-258 of ICAM-1 protein, indicating a stable docking result. The treatment of COVID-19 with P cuspidatum is characterized by multi-component, multi-target, and multi-pathway, which can exert a complex network of regulatory effects through the interaction between different targets, providing a new idea and basis for further exploration of the mechanism of action of P cuspidatum in the treatment of COVID-19.


## 1. Introduction
  Respiratory infectious diseases, such as coronavirus disease 2019 (COVID-19) and influenza, cause substantial morbidity and mortality.[1] COVID 19, is a zoonotic infectious disease caused by severe acute respiratory syndrome coronavirus 2.[2,3] The outbreak of severe acute respiratory syndrome coronavirus 2 was first reported in Wuhan,[4,5] In addition, due to the highly variable nature of the virus, the constant pandemic potential of newly emerging viruses remains a serious threat to public health, the economy, and society.[5–7] Therefore, studying new drugs and elucidating their pathogenic mechanisms are of great significance for respiratory infectious diseases.

  Polygonum cuspidatum has the ability to clear heat and detoxify the body and is commonly used to treat lung-heating coughs.[8–11] In the COVID-19 epidemic, P cuspidatum was widely used and its use was recognized by the Chinese medicine community.[11,12] Modern pharmacological studies have shown that the various active ingredients in P cuspidatum mainly include anthraquinones, flavonoids, phenols and other compounds, which have antibacterial, antiviral, antioxidant and microcirculatory improving effects.[13–16] However, the specific mechanism of action by which P cuspidatum exerts its value during epidemics is unclear. Therefore, this study took COVID-19 as an example to explore the possible components and targets of P cuspidatum.

  In this study, we used the method of network pharmacology and the combination of computer technology and biotechnology to initially discuss the relationship between the active components of P cuspidatum and COVID-19, and initially explore the mechanism of action of P cuspidatum in the treatment of COVID-19. Preliminary validation was conducted through in vitro experiments and molecular docking methods, providing an experimental basis for future research on the composition and mechanism of action of substances in P cuspidatum.


## 2. Materials and methods

### 2.1. Materials
  Polydatin (Institute of Chinese Medicine, Tianjin University of Traditional Chinese Medicine), HEK293T (ATCC Cell Bank, USA), DMEM medium (Gibco, USA), fetal bovine serum (BI, Israel), penicillin-streptomycin (Gibco, USA), 0.25% trypsin + 0.02% EDTA (Gibco, USA), CCK-8 assay kit (Tong Ren Chemical Research Institute, Japan), PBS solution (Solebro, China), pGL4.32[luc2P/NF-κB-RE/Hygro] Vector (Premega, USA), pGL4.75[hRluc/CMV] Vector (Premega, USA), TNF-α, PEI and Dexamethasone (Sigma, USA), and dual luciferase reporter gene kit (Premega, USA).


### 2.2. Screening of active ingredients
  TCM Systematic Pharmacology Database and Analysis Platform (TCMSP; https://old.tcmsp-e.com/tcmsp.php) is a unique systemic pharmacological platform for herbal medicines where we can obtain the relationship between drug, target and disease.[17,18] TCM Integrated Pharmacology Research Platform v2.0 (TCMIP) (http://www.tcmip.cn/ETCM/index.php/Home/) is known as the Traditional Chinese Medicine Encyclopedia.[19] The database contains 402 herbal medicines, 3959 remedies and 7284 active ingredients, in addition to 2266 possible gene targets of active ingredients and 4323 diseases. The database also provides the methodology and results of systematic analysis.


### 2.3. Prediction of drug targets
  The TCMSP database, TCMIP database, SwissTarget database, and Perl software were used to find and predict the targets related to the active ingredients, and then the UNIPROT online protein database was used to find the corresponding standard genes for the selected species “HOMO SAPIENS.” The targets of the active ingredients were obtained by searching the UNIPROT online protein database for the corresponding standard gene names.


### 2.4. Predicting disease targets
  GENECARDS is a comprehensive, integrated database that integrates genomic, transcriptomic, proteomic and clinical information related to genes, providing concise genomic, proteomic, transcriptional, genetic and functional access to all known and predicted human genes.[20,21] Use the GENECARDS database to access COVID-19 related content.


### 2.5. Core target screening
  Overlap mapping of tiger nut drug target information and target information of COVID-19 was performed to obtain overlapping core targets using the R Programming Language operations.


### 2.6. Building a protein interaction network (PPI) network
  The String database (https://string-db.org/) is one of the most data-rich and widely used databases for studying protein interactions.[22,23] The String database has now been updated to Version 11.5. It contains information on over 14,000 species, over 60 million proteins and more than 20 billion interactions. These protein interactions include both direct physical interactions as well as indirect functional correlations. With the STRING database, we can easily retrieve the interactions between known proteins, contributing to a better understanding of the complex regulatory networks in living organisms. Overlapping core targets are imported into the STRING data analysis platform for computational purposes, and PPIs can be constructed based on the strength of the interactions between targets with the aid of Cytoscape 3.7.1 software (www.cytoscape.org).[24]


### 2.7. Constructing the “active ingredient-target” network
  The information obtained on the active ingredients and the core targets of the P cuspidatum was collated and the “active ingredient-target” network was mapped using Cytoscape 3.7.1 software.


### 2.8. Analysis of the Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment
  KEGG-related information was obtained by converting the overlapping target names of TIGER and COVID-19 into ENTREZ Gene IDs using the R Programming Language and then analyzing the KOBAS database. P value was used as the reference value for screening and then analyzed in the R Programming Language to obtain the pathway enrichment analysis.


### 2.9. Cell viability screening
  The cells were resuscitated and seeded at a density of 3 × 105 cells/mL in a 96-well plate, and the cells were administered in groups (100 μL of basal medium per well for one group, and 100 μL of basal medium containing 0.01, 0.1, 1, and 10 μM polydatin for the remaining 4 groups) when the cells reached about 80% wall growth, and the culture was continued for 24 hours. The cell viability was calculated by adding 100 μL of PBS solution containing 10% CCK-8 to each well and incubating for 90 minutes at 37°C, protected from light, and measuring the absorbance at 450nm on a multifunctional enzyme marker.


### 2.10. Construction of NF-kappaB (NF-κB) promoter-luciferase constructs and luciferase assay
  The pGL4.32 and pGL4.75 were extracted separately according to the instructions and the transfection solution was prepared according to the requirements at the time of use. Cells in good growth condition were seeded in 96-well plates at a density of 3 × 105 cells/mL. 0.1, 1, 10 μM polydatin and 10–2 μM Dexamethasone in TNF-α medium, and then the reporter gene activity was tested according to the procedure provided by the reagent company.


### 2.11. Computerized virtual validation
  Molecular docking is a method to predict the binding force and binding mode between molecules by computer simulation. Based on the pre-prediction and validation, the target sites in NF-κB pathway were selected and docked with polydatin for validation. The 3D structure of the target protein was downloaded from the PDB database in pdb format, and the 2D structure of the small molecule polydatin was downloaded from the PubChem database in sdf format, and the docking simulation was validated using Autodock tool and discovery studio software, and the results were visualized using PYMOL software.


### 2.12. Ethical considerations
  Because this study does not involve the ethical issues of clinical and animal experiments, and it is a study about network pharmacology, bioinformatics, and cell experiments, it does not need ethical approval.


## 3. Results

### 3.1. Screening of active ingredients and determination of action targets in Polygonum cuspidatum
  A search of the TCMSP database was carried out to obtain a total of 62 active ingredients of P cuspidatum, including polydatin, emodinanthrone, rhein, and oleanolic. The screening conditions were set as OB ≥ 20% and DL ≥ 0.40 (OB is the oral bioavailability, which refers to the rate and degree of absorption of the active ingredient or active group of the drug into the body circulation; DL is the drug-like property, which refers to the drug contains some specific functional groups or has the same or similar physical characteristics as most drugs), and 9 items were obtained, as detailed in Table 1. The 9 components of TCMSP, TCMIP, and SwissTarget databases were used to obtain 286 targets.


### 3.2. Potential targets of Polygonum cuspidatum for the treatment of COVID-19
  The active ingredients from 3.1 and the potential therapeutic targets obtained were imported into Cytoscape 3.7.1 software to calculate the “active ingredient-target” network (Fig. 1A). In the diagram, the outer pink triangles are the 9 active ingredients of P cuspidatum and the middle purple circles are the 303 potential targets of P cuspidatum for the treatment of COVID-19.


### 3.3. Prediction of core target points of active ingredients in Polygonum cuspidatum
  Using TCMSP database, TCMIP database, SwissTarget database, and Perl software, the 9 active ingredients of P cuspidatum were screened for 286 targets. By searching COVID-19 in GENECARDS database, 4913 COVID-19 disease targets were obtained, and 303 targets were obtained by setting “Relevance score > 2” as the parameter. Using the R Programming Language to intersect the active ingredient targets with the screened COVID-19 disease targets, a Venn diagram of the targets for COVID-19 was obtained, and finally 27 core targets were obtained (Fig. 1B).

  The core targets were analyzed in the STRING database and combined with Cytoscape 3.7.1 software to obtain the PPI network diagram (Fig. 1C), where the target size and color change represent the relative size of the Degree value. In the PPI network, “node” represents the target, and the Degree value is used to measure the importance of the target, the larger the value, the more the target is at the core of the network; “edge” represents the association between the targets, and is represented by the higher the value, the higher the degree of binding. The topological analysis shows that the core targets are TNF, IL-1β, ICAM1, EGFR, STAT3, etc. The target proteins are mainly involved in inflammation and apoptosis.


### 3.4. Analysis of KEGG pathway enrichment of core components in Polygonum cuspidatum
  The overlapping target names were converted into ENTREZ Gene IDs using Perl Language, and the KOBAS database was used for the calculation, of which the first one was “Coronavirus disease – COVID-19” (Table 2). The KEGG pathway enrichment graph (Fig. 1D) was obtained by using the R Programming Language, the vertical coordinates are the names of the pathways and the horizontal coordinates are the number of targets involved.


### 3.5. Polydatin in Polygonum cuspidatum inhibits NF-κB transcriptional activity
  Compared with the normal culture group, there was no significant difference in the cell viability of each group after 24 hours incubation with different concentrations of polydatin (Fig. 2A). The results, expressed as values of measured L/S, showed that polydatin at 0.1 to 10 μM inhibited the transcriptional activity of NF-κB, with 1 μM and 10 μM having more significant effects (Fig. 2B).


### 3.6. Polydatin in Polygonum cuspidatum has obvious binding ability with core target protein
  Since IL-1β, TNF and ICAM1 are the core targets in PPI analysis, and the enrichment of NF-κB pathway is high in KEGG pathway enrichment, the 3 targets of IL-1β, TNF and ICAM1 were verified by molecular docking with polydatin respectively. It was shown that the ability of small molecules to spontaneously bind to NF-κB pathway proteins was determined by the binding energy, the lower the binding energy, the stronger the affinity. The results of molecular docking are shown in Figure 3. The binding energies of polydatin to IL-1β, TNF and ICAM1 were −7.7, −8.0, and −9.0 kcal/mol respectively, all of which were less than zero, indicating that they could bind spontaneously, and the binding energies were all less than −5 kcal/mol, indicating stable binding.


## 4. Discussion
  In recent years, novel coronavirus pneumonia has spread widely around the world.[25,26] With the gradual implementation of unified response measures to the epidemic in various countries, the development of COVID-19 in various countries has been effectively controlled. However, we should always be alert to the high variability of the virus and the complexity of the disease, and establish better defense measures before the disease occurs.[27] The understanding of COVID-19 in Chinese medicine classifies it as a disease caused by epidemics, with the nature of the disease being related to “dampness” and the location of the disease being mainly in the lung, on the basis of which there are various types of evidence and recommended prescriptions.[28,29] On this basis, the team of academician Zhang Boli arrived at the formula “Xuanfeibaidu formula” through the study of classical literature, clinical experience and the optimization of modern components, which has proven to be clinically effective and has been included in the treatment of the common type in the New Coronary Pneumonia Treatment Protocol, Eighth Edition. In this study, we selected the Chinese herb tiger stick in the formula and the results obtained overlapped with the core compounds in the anti-COVID-19 formula obtained from other studies in the literature,[30,31] and the results were more consistent. In clinical practice, P cuspidatum is also used in up to 80% of cases in the treatment of COVID-19 in Tianjin.

  The active ingredients of P cuspidatum obtained by the network pharmacology algorithm in this study are polydatin, emodinanthrone, rhein and oleanolic, which are consistent with the core ingredients in other anti-COVID-19 formulations. Polydatin is one of the index components of polydatin as stipulated in the Chinese Pharmacopoeia and belongs to the class of stilbene compounds.[32] Modern pharmacological studies have shown that polydatin have antioxidant, anti-inflammatory and microcirculatory improving effects in the treatment of respiratory diseases and that they can act by inhibiting inflammatory factors such as TNF-α and IL-6 and blocking the NF-κB pathway,[33,34] and these findings are consistent with the results of this study. Emodin is one of the main active ingredients of P cuspidatum, which belongs to the anthraquinone group and has antibacterial and antiviral pharmacological activities, and can act by inhibiting the adsorption and penetration process of viruses and preventing their replication.[35–37] Quercetin is a natural flavonoid with antioxidant, antiviral and anticancer effects.[38,39] Rhein is a free anthraquinone compound with anti-inflammatory, bacterial inhibition, anti-viral and preventive effects against lung diseases and improved kidney function.[40] The other components obtained in this study also have similar effects to varying degrees.

  In this study, a total of 27 potential targets for the treatment of COVID-19 with P cuspidatum were obtained by searching for overlapping targets of P cuspidatum and COVID-19. Combined with the PPI network analysis map obtained from this experiment, it can be seen that P cuspidatum affects the treatment of COVID-19 through multiple targets and multiple signaling pathways, which exert synergistic relationships with each other in various ways. In this study, the potential targets for the treatment of COVID-19 with P cuspidatum were IL-1β, TNF and ICAM1. Inflammatory factor storms are commonly present in patients and can cause damage to pulmonary capillary endothelial cells and pulmonary epithelial cells, leading to damage to the body.[41,42] Inflammatory factor storms are an important manifestation of clinical critical symptoms. TNF is an important member of inflammatory cytokines, mainly produced by activated macrophages, NK cells, and T lymphocytes.[43] Its main function is to regulate immune cells. As an endogenous heat source, it can cause fever, cause cell apoptosis, prevent tumor occurrence and virus replication, etc. Its dysfunction is believed to be related to various diseases.[43]

  In order to further analyze the signaling pathways involved in the targets of COVID-19 treatment, this study conducted KEGG pathway enrichment analysis on the potential targets of COVID-19 treatment with active ingredients in P cuspidatum and found that they mainly involved IL-17, MAPK, NF-κB and PI3K-Akt signaling pathways, all of which are closely related to inflammation and immunity. It has been shown that PI3K-Akt signaling pathway has an important role in the treatment of respiratory diseases.[44] Experiments by Wen Yang and others demonstrated that the expression of NF-κB pathway was significantly elevated in rats with severe pneumonia, and after drug treatment, the activity of this signaling pathway was significantly inhibited, demonstrating the role of this pathway in the treatment of pneumonia. It has also been shown that modulation of the NF-κB pathway can reduce the liver, lung and kidney damage caused by pneumonia[45] and can inhibit viral pneumonia by activating the NF-κB pathway.[46] It has been reported in the literature that the IL-17 pathway has a significant inhibitory effect on viral infection. It has been speculated that blocking IL-17 may have a role in ameliorating the abnormal immune response to COVID-19.[47] Toll-like receptors are important mediators of immune recognition, initiating the innate immune response as well as activating the adaptive immune response by recognizing pathogens.[48]

  Using the Chinese Pharmacopoeia as a standard, this study selected polydatin, an index component of P cuspidatum, for subsequent validation. The inhibition of NF-κB transcriptional activity by polydatin was demonstrated in vitro experiments, suggesting that polydatin have stable anti-inflammatory effects and that interference with NF-κB signaling pathway transduction may be the source of the mechanism of action. And the enrichment of core targets IL-1β, TNF and ICAM1 were also known to be the targets of action of NF-κB signaling pathway in the PPI network diagram. Molecular docking experiments were performed to verify the connection between polydatin and active targets respectively, and the results suggested that stable covalent bonds could be generated between polydatin and all 3 active targets. The results suggested that the 3 active targets could be connected by covalent bonds, and it is likely that the interaction of polydatin with the above 3 targets could lead to the modulation of NF-κB signaling pathway, thus producing anti-inflammatory effects.

  In summary, polydatin, emodin, β-sitosterol and other constituents in the P cuspidatum can exert anti-inflammatory, anti-viral and immune enhancing functions. They can regulate various aspects of the inflammatory response, such as inhibiting the release of pro-inflammatory cytokines and also inhibiting the NF-κB signaling pathway to exert anti-inflammatory effects. Based on the network pharmacology and using various databases and software, this study preliminarily explored the mechanism of action of P cuspidatum for the treatment of COVID-19 by conducting PPI analysis, KEGG pathway enrichment analysis and GO gene function analysis on the screened potential targets for the treatment of COVID-19, and also validated the preliminary results with molecular docking and in vitro experiments, laying the foundation for further studies. Most of our studies are carried out on computer simulation and in vitro. Whether the core component of P cuspidatum can also affect the study in vivo remains to be determined. Therefore, the mechanism of it in the treatment of COVID-19 by regulating immune inflammation should be the subject of future studies. Our study preliminarily explored the mechanism of P cuspidatum in the treatment of COVID-19, and provided reference for further research and clinical application in the future.


## Author contributions
  Conceptualization: Tao Liu.

  Data curation: Rui Han.

  Methodology: Yiqi Yan.

  Project administration: Tao Liu.

  Resources: Rui Han.

  Software: Yiqi Yan.

  Supervision: Tao Liu.

  Validation: Rui Han.

  Visualization: Yiqi Yan.

  Writing – original draft: Rui Han.

  Writing – review & editing: Tao Liu.