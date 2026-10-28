# Exploring the potential molecular mechanism of Gualou Guizhi decoction in the treatment of rheumatoid arthritis based on network pharmacology and molecular docking


## Background:
  Traditional Chinese medicine (TCM) has been used in China for a long time and is gradually gaining more and more recognition worldwide. Gualou Guizhi Decoction (GGD) has long been used as a folk medicine for the treatment of rheumatic diseases, but its bioactive components and therapeutic mechanisms are still unclear.


## Methods:
  An integrated approach using network pharmacology and molecular docking and using methotrexate as a positive control drug.


## Results:
  We obtained 157 active ingredients of GGD, 7542 RA disease targets and 49 intersecting targets. GO and KEGG enrichment analysis revealed that their functions were mainly related to cytokine active metal ion binding, enzyme binding and DNA binding, and enriched in TNF signaling pathway, T cell receptor signaling pathway, Toll-like receptor signaling pathway, RA pathway and other signaling pathways that are closely related to RA. The molecular docking results show that the effector components of GGD bind better to the core targets of RA, and some are even better than methotrexate.


## Conclusion:
  The therapeutic effect of GGD for RA is achieved by affecting the core targets such as VEGFA, IL-1β, IL6, CXCL8, CCL2, and JUN, which together interfere with the tumor necrosis factor signaling pathway and RA pathway to treat RA. The above study provides new ideas for further exploration of this classic formula in the future.


## 1. Introduction
  Rheumatoid arthritis (RA) is a systemic autoimmune disease that involves chronic inflammation of multiple joints. The obvious histopathological changes in RA patients are persistent inflammation and cell proliferation in the synovial membrane, various inflammatory cell infiltrates, vascular opacification formation, articular cartilage damage and bone matrix destruction, joint swelling and morning stiffness, and ultimately joint deformity and loss of function. Based on the clinical manifestations and signs of RA, it is now considered to belong to the category of “paralysis” in Chinese medicine.[1,2] RA affects 0.5% to 1% of today population, and to date, RA cannot be completely cured; current clinical medications can only relieve pain or reduce the progression of inflammation, with poor therapeutic effects and many side effects from long-term use.[3,4] Therefore, finding therapeutic agents with clear efficacy and few side effects remains a challenge for medical practitioners.

  Classical prescriptions are the treasures of Chinese medicine culture in China, and the expansion of their application and “modern use of ancient prescriptions” is strongly advocated by the state. Modern pharmacological techniques have achieved a more accurate and systematic analysis of the components of Traditional Chinese Medicines[5] and compound prescriptions[6] by means of mass spectrometry and chromatography. Professor Liu Ximing fully analyzed the essence of Gualou Guizhi Decoction (GGD) and used the GGD of the <<Jin Kui Essentials>> as the base formula with addition and subtraction changes, establishing the method of benefiting yin and regulating yin, and penetrating evil to pass paralysis, which is applicable to the treatment of RA with yin deficiency and paralysis of evil (Supplementary material 1, http://links.lww.com/MD/L270), with significant clinical efficacy, but the specific mechanism of action is still unclear.[7] GGD formula: “ Trichosanthes (gualou, GL), 2 taels; Ramulus Cinnamomi (guizhi, GZ), 3 taels; Radix Paeoniae Alba (shaoyao, SY), 3 taels; Licorice (gancao, GC), 2 taels; Ginger (shengjiang, SJ), 3 taels; Jujube (dazao, DZ), twelve pieces.”[8] Chinese medicine treats diseases through multi-target and multi-pathway, with good effect and less side effects.[9]

  Recently, the rise of network pharmacology approaches and molecular docking techniques has brought light to explore the mechanism of action of herbal medicines/herbal compounding and new drug development, and many existing databases, pathway analysis and network analysis can be used to explore the mechanism of action of herbal medicines for the treatment of diseases.[10] Based on the previously proposed TCM pathogenesis of RA, the author investigated the potential targets and enrichment pathways of GGD for the treatment of RA at the level of molecular regulatory network with the help of network pharmacology method, and molecularly docked the main components of GGD and the representative NSAID, methotrexate, with the core targets of RA, and compared the degree of binding to provide a basis for further experimental studies, hoping to enrich the clinical application and translation of GGD in RA (Fig. 1).


## 2. Material
  Traditional Chinese Medicine Systematic Pharmacology Database and Analysis Platform (TCMSP) (https://old.tcmspe.com/tcmsp.php); UniProt Database(https://www.uniprot.org); STRING 11.5 Database(https://cn.string-db.org); GeneCards Database(https://www.genecards.org); OMIM Database(https://www.omim.org); DisGeNET Database(https://www.disgenet.org); Strawberry Perl 5.32.0.1; Cytoscape 3.9.0; RStudio 1.41717.0; UltraEdit 29.0.0.102; PyMOL 2.5.2; AutoDockTools 1.5.6 Software, etc.


## 3. Methods

### 3.1. Screening of the active ingredients and targets of GGD
  The chemical constituents of GGD, Trichosanthes (gualou, GL), Ramulus Cinnamomi (guizhi, GC), Radix Paeoniae Alba (shaoyao, SY), Licorice (gancao, GC), Ginger (shengjiang, SJ), Jujube (dazao, DZ) in GGD were retrieved in TCMSP and screened according to absorption, distribution, metabolism and excretion (ADME) parameters with the screening criteria of oral bioavailability (OB) ≥ 30%; drug-like properties (DL) ≥ 0.18. The relevant action targets of GGD components were obtained, and the potential targets related to the active ingredients were obtained by applying Strawberry Perl software, filtering through UniProt database, and standardization.


### 3.2. Acquisition and integration of RA disease-related targets
  Gene targets of RA were searched in GeneCards, OMIM and DisGeNET databases using “Rheumatoid arthritis” as the search term, and those with scores >10 in GeneCards database were used as spare genes, and those with scores > 0.3 in DisGeNET database were used as spare genes. The genes obtained from the GeneCards database with scores >10 were used as spare genes, and those obtained from the DisGeNET database with scores > 0.3 were used as spare genes, and the duplicates were removed and their names were normalized to obtain the intersecting genes.


### 3.3. Acquisition of active ingredients of drugs and RA intersection genes and production of Venn diagram
  RStudio 1.41717.0 software was used to match the active ingredient targets of GGD with the disease targets of RA to obtain the intersecting genes and produce a Venn diagram to visualize the results.


### 3.4. “Chinese medicine – active ingredient – common target – disease” network construction
  The common targets obtained from the screening under “2.3” were used to reverse screen the corresponding active ingredients in GGD. The information of Chinese medicine, active ingredient, common target and disease in GGD is imported into Cytoscape 3.9.0 software to build “Chinese medicine – active ingredient – common target – disease” network construction.


### 3.5. Common Target PPI Network Construction and Analysis
  The common targets screened under “2.3” were entered into STRING 11.5 database to construct the common target PPI network, with “HomoSapiens” selected as the species and “Medium Confidence’‘>0.4 and “Combined score > 0.4” were selected as the screening criteria, and the common target PPI network interactions and PPI relationship data were obtained and saved as “. tsv” format file. RStudio 1.41717.0 software was used to analyze the “. tsv” format files and find out the core genes based on the degree of the target in the PPI network, the higher the degree value means the more important the target is in the PPI network, and visualize the core gene bar graph.


### 3.6. GO function and KEGG pathway enrichment analysis
  The DAVID 2021 biomolecular functional annotation system was used to perform gene ontology (GO) functional analysis of the common targets screened under “2.3” and to annotate gene functions at 3 levels: cell composition (CC), biological process (BP) and molecular function (MF). Gene ontology (GO) and Kyoto Encyclopedia of Genomes (KEGG) pathway enrichment were performed by RStudio 1.41717.0 software using “bioconductor” and “DOSE” for the intersecting genes. The enrichment analysis was visualized with the screening criteria of P value ≤ 0.05 and q value ≤ 0.05, and the results were ranked according to the P value.


### 3.7. Molecular docking

#### 3.7.1. Selection of ligands and preparation of documents.
  The network of active drug components obtained in 2.4 was evaluated for activity intensity in terms of the number of targets, sorted and selected the top 8 components as ligands, imported into the TCMSP database to screen the molecular structures of the compounds, exported in mol2 format and saved. The 2D structure of the corresponding ligand for methotrexate (Methotrexate) was obtained from the PubChem database and converted to the 3D spatial conformation of the minimum free energy using Chembio3D for format conversion.


#### 3.7.2. Target protein receptor file preparation.
  Based on the top 30 core target genes obtained by PPI network screening, the 6 genes most relevant to RA were selected by combining the KEGG results, which were entered into UniProt website to select the protein ids belonging to human respectively, and then the obtained protein ids were entered into RCSB PDB protein structure database to obtain protein 3D structures, which were exported and saved in PBD format. The obtained receptor protein files were imported into PyMOL for dehydration, removal of small molecule ligands, etc, imported into AutoDockTools 1.5.6 software for hydrogenation, and then converted to pdbqt format for storage.


#### 3.7.3. Molecular docking.
  The Grid function of AutoDockTools 1.5.6 software is used to identify structural domains on protein receptors that can bind to drug-forming allocations, i.e., pockets of activity. Based on the parameters obtained in the previous step, molecular docking was performed using Autodock vina 1.1.2 software, and PyMOL and other software were used to analyze the docking strength, hydrogen bonding, Pi-Pi conjugation, hydrophobicity of amino acid residues, etc. Finally, the result with the best binding degree was selected and presented graphically.


## 4. Research results

### 4.1. The main active ingredients and targets of GGD
  The initial screening through the TCMSP database yielded 157 components of GGD, including 11 of Trichosanthes (gualou, GL), 7 of Ramulus Cinnamomi (guizhi, GZ), 13 of Radix Paeoniae Alba (shaoyao, SY), 92 of Licorice (gancao, GC), 5 of Ginger (shengjiang, SJ), and 29 of Jujube (dazao, DZ), and 145 components were obtained after the duplicate values were removed by re-screening. A total of 268 action targets of GGD drug components were obtained from the TCMSP database, and a total of 223 potential action targets of active ingredients were obtained by applying Strawberry Perl software for drug target ID conversion.


### 4.2. RA disease-related targets
  The search terms “Rheumatoid arthritis” were used to search the GeneCards, OMIM and DisGeNET databases. In the GeneCards database, 4807 genes were retrieved (Supplementary material 2, http://links.lww.com/MD/L271), and 327 genes with scores >10 were selected; in the OMIM database, 12 genes were retrieved (Supplementary material 3, http://links.lww.com/MD/L272); in the DisGeNET database, 2723 genes were retrieved (Supplementary material 4, http://links.lww.com/MD/L273), 176 genes with scores greater than or equal to 0.3 were selected, and a total of 515 gene targets were obtained, and 434 gene targets were obtained after duplicate values were removed by re-screening.


### 4.3. Intersection of drug-RA targets of action
  The drug-RA action targets were intersected and Venn diagrams were produced using RStudio 1.41717.0 software, with 49 intersected targets, and the results are shown in Figure 2.


### 4.4. Chinese medicine – active ingredient – common target – disease network
  In order to elucidate the interrelationship between multi-component and multi-target of GGD and diseases, 106 corresponding active ingredients in GGD were reverse screened using 49 common targets, and the results are shown in Supplementary material 5, http://links.lww.com/MD/L274. Among them, there are 5 kinds of ingredients from GL, 5 kinds of GZ, 4 kinds of SY, 83 kinds of GC, 3 kinds of SJ, and 14 kinds of DZ. The 106 active ingredients were connected with the corresponding herbal medicines and targets, and the “herbal medicine – active ingredient – common target – disease” network of GGD for RA was constructed by using Cytoscape 3.9.0 software, and the results are shown in Figure 3. The network contained 162 nodes and 575 edges, and the extracted ingredient-target sub-network found that each active ingredient acted on an average of 3.88 targets and each target was connected to an average of 2.16 compounds, fully reflecting the complex network relationship of 1 drug with multiple targets and 1 target with multiple drugs. Among them, the top 8 active ingredients in terms of Degree are Quercetin (Degree = 76), kaempferol (degree = 30), beta-sitosterol (degree = 20), (+)-catechin (degree = 12), beta-carotene (degree = 8), formononetin (degree = 7), naringenin (degree = 7) and licochalcone a (degree = 7), these compounds may be key active ingredients in GGD for the treatment of RA due to their high number of targets of action.


### 4.5. PPI network construction and core target screening
  The PPI network diagram of GGD treatment of RA target proteins is shown in Figure 4, with 49 points and 1406 edges. RStudio 1.41717.0 software was used to analyze the “. tsv” format files, and the top 30 targets in terms of degree were visualized to obtain the core gene bar graphs, see Figure 5.


### 4.6. GO function and KEGG pathway enrichment analysis
  GO enrichment analysis revealed that the targets of GGD for RA were mainly enriched in 72 Biological process (BP), 30 Molecular function (MF) and 19 Cellular component (CC). Among them, the 14 biological processes, 14 molecular functions and 14 cellular components with high significance are shown in Figure 6.

  RStudio 1.41717.0 software was used to perform gene ontology (GO) enrichment analysis of the intersecting genes by “bioconductor,” “DOSE,” etc. A total of 51 enrichment results were obtained, and the top 20 results were visualized. Among them, cytokine activity, cytokine receptor binding, receptor-ligand activity, signal receptor activator activity, chemokine receptor binding, growth factor receptor binding, antioxidant activity, MAP kinase activity, chemokine activity, and peroxidase activity were the best enriched. Figure 7.

  The Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment analysis was performed by RStudio 1.41717.0 software using “bioconductor” and “DOSE” for the intersecting genes, and a total of 108 pathways were obtained. A total of 108 relevant pathways were obtained, and the top 20 results with the best enrichment were visualized in Figure 8. The pathways with high enrichment significance mainly include: IL-17 signaling pathway, TNF signaling pathway, T cell receptor signaling pathway, Toll-like receptor signaling pathway, Th17 cell differentiation, Th1 and Th2 cell differentiation, RA pathway, etc, among which RA signaling pathway is more directly related to RA, see Figure 9. The most significant pathway was IL-17 signaling pathway, which was enriched to PTGS2, JUN, IL6, IKBKB, MAPK8, MMP1, MAPK14, IL4, MAPK1, MMP3, MMP9, NFKBIA, IL1B, CCL2, CXCL8, IFNG, CXCL2, and CXCL10.


### 4.7. Molecular docking

#### 4.7.1. Screening of constituents of GGD.
  See Table 1.


#### 4.7.2. Target protein receptor files.
  According to the core target protein bar graphs obtained from PPI network screening (Fig. 5) and combined with KEGG results (Fig. 9), 6 were selected as docking target proteins, VEGFA, IL1B, IL6, CXCL8, CCL2, and JUN, respectively, with UniProt id and RCSB PDB protein structure database protein numbers of VEGFA (P15692, 1BJ1), IL1B (P01584, 1HIB), IL6 (P05231, 1ALU), CXCL8 (P10145, 1ICW), CCL2 (P13500, 1DOK), JUN (P05412, 5T01).


#### 4.7.3. Molecular docking and analysis of results.
  After molecular docking by Autodock vina 1.1.2 software, the binding energy between each active ingredient and the receptor protein was obtained, the lower the binding energy of the ligand and receptor docking indicated a more solid molecular binding and a higher possibility of interaction, the binding was better at binding energy ≤ −5.0 kcal-mol−1 and very good at binding energy ≤ −7.5 kcal-mol−1,[11,12] the docking results were visualized and processed with Strawberry Perl, PyMOL software, and the results are tabulated and summarized in Figures 10 and 11 (As can be seen from Supplementary material 5, http://links.lww.com/MD/L274, ingredient A is contained in 4 kinds of Traditional Chinese Medicine, so ingredient A is more important. As can be seen from Figure 3, component D has the most connections with core genes, so component D is relatively important. I choose A and D results for presentation. See Supplementary material 6, http://links.lww.com/MD/L275 for the docking results of other components.).


## 5. Discussion
  In this study, we applied the network pharmacology method and molecular docking technology to obtain a large amount of ingredient-disease target-related information of GGD by searching the TCMSP database, and performed network construction and collation analysis to visually and multifacetedly show the connection and variability among the active ingredients in this formula, the complex molecular networks such as core ingredient-disease target interactions, biogenetic annotations and pathways between them, and compare the binding ability between each ingredient and its target by molecular docking and compare it with the conventional drug methotrexate for RA treatment.[13,14]

  Since each drug has multiple active ingredients and multiple targets, the therapeutic effect of GGD on RA is not a simple superposition of a single effect, but a synergistic effect between each other, with the characteristics of multi-pathway and multi-target regulation that Chinese medicine generally possesses. RA belongs to the category of “paralysis,” which is often caused by wind, cold, and dampness, resulting in blockage of the meridians, stagnation of the yin and yang, and blockage of the qi and blood, resulting in joint pain, while GGD can establish a method to benefit the yin and regulate the yin, and penetrate the evil to pass the paralysis, and its potential mechanism to intervene in RA needs to be explored.[7,12,15]

  In this study, 49 targets were screened for the intersection of GGD components and RA, and 30 core targets were identified, including VEGFA, IL1B, IL6, CXCL8, CCL2, JUN, etc. IL-1B promotes the expression of acid-sensing ion channel 1a (ASIC1a) through the activation of mitogen-activated protein kinase (MAPK) and NF-κB signaling, resulting in bone and chondrocyte damage in RA. The synovial fluid of RA patients shows a certain degree of acidosis, and the dynamic balance of cartilage is affected by the local pH. ASIC1a is a calcium channel that is highly expressed in chondrocytes, and extracellular acidification can lead to articular chondrocyte damage through ASIC1a-mediated intracellular [Ca2+]i overload.[16,17] IL-1B, IL-6 can promote the differentiation of CD4 + T cells, which secrete large amounts of inflammatory factors.[18] IL-1B induces endothelial cells to promote the aggregation of neutrophils and other cells, and promotes the secretion of prostaglandins by neutrophils, which increases the expression of collagenases and the secretion of JAK2 and JAK3 kinases in synovial cells and chondrocytes, leading to local inflammatory responses and articular cartilage damage, and promotes the expression of matrix metalloproteinases (MMPs) leading to cartilage degradation.[19,20] IL-6 stimulates significant activation of JAK2/STAT3 and MAPK/NF-κB signaling pathways in articular chondrocytes, thereby promoting ASIC1a expression and function to enhance acid-induced apoptosis of articular chondrocytes, resulting in articular cartilage destruction in RA.[21] IL-6 mainly mediates inflammation of the synovial membrane, while VEGFA is an important factor involved in vascular growth in vivo,[22] the pathological manifestations of RA are not only recurrent and persistent synovitis, but also capillary hyperplasia and vascular opacification, the interaction of which leads to a more severe RA condition.[23] CXCL8 is probably the most potent and abundant chemokine in RA synovial fluid, and CXCL8 expression positively correlates with infiltration of activated mast cells, monocytes, resting dendritic cells, neutrophils, and activated NK cells.[24,25] JUN can directly activate the pro-inflammatory factor COX-2 in macrophages to promote RA development.[26] The main function of CCL2 is to recruit macrophages and promote the development of RA disease.[27]

  The results of GO analysis show that GGD targets the action of RA mainly through positive regulation of RNA polymerase II promoter transcription, positive regulation of DNA template transcription, immune response and other BPs, involving CCs such as extracellular gap, cytoplasm, etc. The highest MF enrichment is cytokine active metal ion binding, enzyme binding. These 3 levels are the top level of GO enrichment analysis for gene description, reflecting the diverse biological processes carried out by different molecules or genes in different cellular structures/regions.

  Those with high enrichment in KEGG analysis include IL-17 signaling pathway, TNF signaling pathway, T cell receptor signaling pathway, Toll-like receptor signaling pathway, and RA pathway. Studies have shown that IL-17 plays a key role in the development and progression of RA,[28] Lee[29] showed that IL-17 upregulated TLR3 in the STAT3 pathway in fibroblast-like synoviocytes of RA. The TNF signaling pathway mediates leukocyte recruitment and inflammatory responses, and various anti-TNF inhibitors have also produced significant and effective effects on RA.[30] In addition, Toll-like receptors (TLR) and their corresponding downstream signaling pathways, such as Wnt, NF-κB and MAPK signaling pathways, have been demonstrated in the biology of synovial inflammation and bone remodeling in RA.[31,32] The RA pathway is even more directly related to RA. In summary, the potential mechanisms of GGD for RA treatment may be attributed to the following: inhibition of the immune inflammatory response, reduction of chemokine release, and reduction of capillary production.

  In this study, the interaction between GGD and key target molecules was verified by molecular docking, and the results showed that GGD bound well to the core target proteins, and the top 8 target number of GGD active ingredients were docked to RA-related receptors, and it was found that all docking binding energies were < −5.0 kcal-mol−1, and the number of binding energies < −7.5 kcal-mol−1 was found in the docking with The number of binding energy < −7.5 kcal-mol−1 accounted for 50% in the docking with VEGFA, 37.5% in the docking with IL1B, 0% in the docking with IL6, 50% in the docking with CXCL8, 25% in the docking with CCL2, and 0% in the docking with JUN, and the combined statistics accounted for 20.3%, which to a certain extent can indicate that GGD binds very well to the RA target receptor protein. Compared with methotrexate-receptor binding energy, GGD-receptor binding energy was smaller for most of the components, and the ratios of the 6 groups that were less than or equal to methotrexate-receptor binding energy were 12.5%, 50%, 12.5%, 50%, 62.5% and 62.5%, respectively. The degree of docking binding of active components was generally better than that of methotrexate.

  The 5 groups with the best binding status were VEGFA-naringenin, VEGFA-β-sitosterol, CXCL8-β-carotene, VEGFA-β-carotene, and CXCL8-β-sitosterol. The best binding state, i.e. the lowest binding energy, is VEGFA-naringenin, which is one of the important active components of licorice. naringenin exerts anti-inflammatory effects by modulating immune cells, inhibiting chemokines, cyclooxygenase-2 (COX-2), cytokines and pro-inflammatory transcription factors,[33] and naringenin may inhibit oxidative stress by activating the endoplasmic reticulum and PI3K/ Akt signaling pathway to inhibit oxidative stress.[34] Furthermore, results from in vitro studies and in vivo animal models suggest that naringin can downregulate the expression of several inflammatory markers, such as TLR4, TNF-α, IL-1β, IL-6, inducible nitric oxide synthase (iNOS) and COX-2, by inhibiting the NF-κB pathway and activating AMPK, which is associated with the inhibition of several proinflammatory signaling pathways.[35] Three of the best 5 sets of docking relationships were generated with VEGFA, which promotes endothelial cell proliferation and macrophage infiltration,[36] is involved in inflammation-mediated injury, has multiple effects on the vascular and hematopoietic systems, promotes vascular opacification formation, and exacerbates joint damage in RA.[37,38] Professor Liu Ximing achieved good efficacy in treating RA with GGD, but the specific therapeutic mechanism is still unclear,[7] In this paper, we study that the active components of GGD can dock well with the above-mentioned receptors, which validates the clinical treatment of Professor Liu Ximing, indicating that these receptors may be important potential targets for the action of GGD on RA, providing a basis for future research on the specific mechanism of action of GGD in treating RA.


## 6. Conclusion
  Based on the network pharmacology method combined with molecular docking technology, this study has gradually elucidated the molecular mechanism of the active ingredients of traditional formula GGD against RA through multi-target combination and multi-pathway collaboration, which brings a new perspective and direction for the subsequent experimental mechanism research of this formula for the treatment of RA, and also provides a basis for the rational clinical application, ancient prescriptions and new drug development.


## Author contributions
  Conceptualization: You Zhou.

  Funding acquisition: You Zhou, Shigang Li.

  Resources: Shuai Ma, Jinglang Liu.

  Writing – original draft: Zhihao Duan, Can Jin.

  Writing – review & editing: Shigang Li, You Zhou.


## Supplementary Material