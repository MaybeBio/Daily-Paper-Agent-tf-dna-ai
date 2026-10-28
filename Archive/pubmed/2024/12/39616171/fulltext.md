# Costunolide and dehydrocostus lactone alleviate ulcerative colitis via regulating TLR4, NF-κB and PI3K expression


## Supplementary Information
  The online version contains supplementary material available at 10.1038/s41598-024-77021-5.


## Introduction
  Ulcerative colitis (UC) is a chronic, non-specific bowel disease that mainly affects the colon and rectum1. Due to its persistent and recurrent nature, it is difficult to cure and often remains with patients for the duration of their lives. Although UC is unlikely to pose a life-threatening challenge, patients need lifelong treatment and strict self-management, so it is called green cancer2. UC is the most common inflammatory bowel disease. Clinically, it is mainly manifested as mucosal inflammation in the distal rectum. With the aggravation of the disease, it gradually spreads to local or even the whole colon. Bloody diarrhea, weight loss and fever are the most obvious symptoms of UC, but patients may also experience constipation, abdominal pain, incontinence and anal fissure3,4. The clinical course is characterized by alternating disease deterioration and remission5. Since the mid-20th century, the incidence of UC has steadily increased globally, and the annual incidence in Europe, America, and Oceania can go as high as 17.4–24.3 per 100,0006. Incidence of UC has increased 1.5–20 times in some Asian countries over the past four decades7. Treatment options include 5-aminosalicylic acid (5-ASA), corticosteroids, immunosuppressants, and colectomy, intending to alleviate clinical symptoms and endoscopy, and to improve the patient’s quality of life4.

  However, chronic administration of 5-ASA and corticosteroids tends to induce dependence, leading to side effects such as diabetes and osteoporosis. High cost of immunosuppressants imposes heavy financial burden and infection risk to patients. The side effects of these drugs may reduce the patient’s compliance and increase burden on medical insurance8,9,10]. As a result, more secure and efficient medication options are expected. Traditional Chinese medicine (TCM) may provide alternative illumination, with the properties of chemical diversity, long-history practice and convenient accessibility. In recent years, the literature on the treatment of UC with TCM has been emerging, and the efficacy is confirmed11.

  Aucklandiae radix (AR) is the dried root of Aucklandia lappaDecne., a traditional Chinese medicinal herb. AR has been used for thousands of years to treat gastrointestinal diseases such as abdominal pain and dysentery. The most common symptoms of UC are diarrhea and abdominal pain. This suggests that AR has the possibility to treat UC. It has been shown that AR can be used to treat UC in rat12. Costunolide (COS) and dehydrocostus lactone (DEH) are the two components with the highest content of AR, (the chemical structures of both are shown in Fig. 1) and it is very likely that two compounds play a role in the treatment of UC.

  Fig. 1Structural diagram of COS and DEH.

  Network pharmacology constructs a bio-information network through high-throughput omics data analysis, computer virtual computing, and retrieval results based on network databases, and performs topology analysis on the network. Network pharmacology can provide a theoretical basis for studying the mechanism of drug treatment of diseases, improve the success ratio of experiments, reduce scientific research costs, and provide new methods for drug research and development13. Molecular docking is a theoretical simulation method to study the mutual recognition between molecules (ligand and receptor) through spatial matching and energy matching, and to predict their binding mode14. Molecular docking can build a complex structural model of small molecules and macromolecular target proteins, predict the key sites for receptor binding, improve research efficiency and reduce research costs15.

  In this study, network pharmacology was used to predict the target proteins of COS and DEH in AR for the treatment of UC, and to find the key proteins among them through PPI analysis, GO analysis and KEGG analysis. Then, the binding affinity between the compounds and the proteins was verified by molecular docking. Finally, animal experiments were carried out to verify the regulatory effects of COS and DEH on target proteins in mice with UC.


## Result

### Results of network pharmacology analysis

#### Target collection results of COS, DEH and UC
  A total of 213 COS potential targets and 286 DEH potential targets were obtained. A total of 1094 UC related targets was obtained.


#### Intersecting targets
  Related targets of COS, DEH and UC were imported into Venny 2.1.0, so that 39 intersecting targets were obtained. The intersecting targets are PTGER3, ZAP70, NOS2, HSD11B2, etc.


#### PPI analysis of intersecting targets
  The PPI diagram consists of 38 nodes and 92 edges. It can be seen from Fig. 1C that the strongest interacting proteins are TLR4, PTGS2, RELA, NOS3 and MPO.


#### Gene ontology analysis and kyoto encyclopedia genes genomes enrichment analysis results
  A total of 401 GO terms, including 354 BPs, 26 CCs and 21 MFs, was obtained. As shown in Fig. 2, the GO enrichment analysis revealed that the BPs were mainly related to the response to hormone, cellular response to nitrogen compound and positive regulation of cytokine production. These showed that the therapeutic effects of COS and DEH on UC are reflected in BP, mainly related to OS, peptides, hormonal and inflammatory responses. The CCs where the target genes act mainly include vesicle lumen, secretory granule lumen, perinuclear region of cytoplasm, transcription regulatory complex, specific granule, membrane raft, and primary lysosome, etc. These results indicated that the therapeutic effects were mainly related to transcriptional translation, signal transduction and sterilization. The MFs mainly include transcription factor binding, protein kinase binding, kinase binding, oxidoreductase activity, calmodulin binding, etc. These indicated that the curative effects were mainly related to transcription and signal transduction.

  Fig. 2Network pharmacology analysis of COS and DEH for the treatment of UC. (A) The Venn diagram shows 39 intersecting targets of COS, DEH and UC. (B) PPI network diagram of COS and DEH treat ulcerative colitis. (C) GO-BP enrichment analysis of COS and DEH in the treatment of UC. (D) GO-CC enrichment analysis of COS and DEH in the treatment of UC. (E) (C) GO-MF enrichment analysis of COS and DEH in the treatment of UC. (F) KEGG enrichment analysis of COS and DEH in the treatment of UC.

  A total of 76 signaling pathways was obtained by KEGG enrichment. The main pathways of enrichment can be seen in Fig. 2D. For example, pathways in cancer, chemical carcinogenesis - reactive oxygen species and human cytomegalovirus infection. In addition, pathways such as chagas disease, HIF-1 signaling pathway, and NF-κB signaling pathway were also included. The top 20 enriched pathways were classified based on the Kyoto Encyclopedia of Genes and Genomes. Environmental Information Processing pathways: HIF-1 signaling pathway, NF-κB signaling pathway; Cellular Processes pathways: apoptosis; Organismal Systems pathways: C-type lectin receptor signaling pathway, NOD-like receptor signaling pathway; Human Diseases pathways: pathways in cancer, chemical carcinogenesis-reactive oxygen species, human cytomegalovirus infection, coronavirus disease-COVID-19, chagas disease, shigellosis, fluid shear stress and atherosclerosis, PD-L1 expression and PD-1 checkpoint pathway in cancer, small cell lung cancer, influenza A, measles, yersinia infection, acute myeloid leukemia and leishmaniasis. Fifteen of these pathways were distributed under the items of Human Diseases, the Human Diseases items are further subdivided into several items, with a higher distribution of 4 and 3 in the items Infectious diseases: viral and Cancer: overview, respectively.Table 1The binding energy of compounds to targets (Kcal∙mol-1).CompoundRELA (PDB: 3QXY)TLR4 (PDB: 3FXI)PIK3R1 (PDB: 3HHM)PTGS2 (PDB: 5KIR)MPO (PDB: 4C1M)NOS3 (PDB: 4D1O)CHUK (PDB: 5EBZ)COS-8.27-6.9-7.67-7.98-7.13-7.41-8.78DEH-7.93-7.55-7.87-8.17-7.36-7.76-9.37Original ligandSAM-7.54NAG-5.22KWT-8.91RCX-9.29NAG-3.89H4B-5.415TL-9.22


#### Component-target-pathway network
  It can be seen from Fig. 3 that the four targets with the highest degree of connectivity to the enriched pathway are PIK3R1, TLR4, RELA and CHUK.

  Fig. 3The component-target-pathway network of COS and DEH treating UC.


### Results of molecular docking
  The docking results are shown in Table 1 and Fig. 4. The docking results showed that the compound-target docking scores were low, indicating that the binding between them was relatively stable. And RELA, TLR4, PIK3R1 and other proteins could be used as therapeutic targets for the treatment of UC with COS and DEH.

  Fig. 4The docking results of key proteins with COS, DEH and original ligand molecules. The yellow sticks represent the compounds, the green cartoons represent the target proteins, and the sky-blue sticks represent the amino acids combined with the compounds. The hydrogen bonds formed by the compounds and the key proteins are indicated by yellow dotted lines, and the bond lengths are marked in the figure.


### Results of an animal experiment

#### Results of changes in body weight, colon length, and DAI score
  The changes in body weight, DAI scores, and colon length of mice are shown in Fig. 5. The mice in the control group had no significant weight loss. After the fifth day, the model mice developed muddy stools, the color of their feces changed to red, they lost weight, and their DAI score increased. After the administration of the drug, weight loss and DAI scores of mice in the 5-ASA group, COS group and DEH group were improved compared with the model group. The activity of mice increased, diarrhea and bloody stool improved. Among them, the 5-ASA group, the H-DEH group and the H-COS group were more effective in relieving weight loss. The effects of the 5-ASA group, H-COS group, and M-COS group were more significant in DAI. DSS shortened the colon of mice, but the colon length was prolonged after administration of 5-ASA or COS or DEH, and the therapeutic effect was better with increasing dose.

  Fig. 5Effects of COS, DEH and AR extracts on body weight, colon length and DAI of UC mice (n = 6). (A) Body weight changes of mice in each group during the experimental period. (B) Colonic length of mice in each group. (cm) (C) DAI scores of mice in each group during the experimental period.


#### Effects of COS and DEH on histopathological changes in colon tissues
  Histologically characteristic lesions in UC are crypt abscesses, branching, shortening, and decreased density16. In addition, inflammatory cells accumulate in the crypts and surrounding lamina propria, mucin is depleted, and the surface epithelium ruptures17. As the disease progresses, inflammatory cells spread from the mucous layer of the colon to the muscular layer18. The HE sections showed the histopathological changes of the colon in each group of mice (Fig. 6). The colonic crypts of mice in the control group were normal, and no inflammatory cell infiltration was found in the mucous, submucosa, and muscular layer. In the model group, the crypts were arranged in disorder, some crypts were lost, goblet cells were reduced, and inflammatory cells infiltrated into the submucosa. The mice in the 5-ASA group showed inflammatory cell infiltration, more lymphocytes, and the loss of crypts was improved. With the increase of drug concentration, the loss of crypts and the infiltration of inflammatory cells decreased gradually, and the arrangement of crypts became regular in COS group mice. In the L-DEH group, the number of goblet cells in the mucous layer decreased, the crypts were abnormally arranged, and lymphoid follicles were formed. With the increase of drug concentration, lymphoid follicles and inflammatory cell infiltration decreased, and the number of crypts increased.

  Fig. 6Representative images (magnification ×20) of HE staining in the colon of different treatment groups. (A-J) represent the control group, model group, 5-ASA group, L-COS group, M-COS group, H-COS group, L-DEH group, M-DEH group and H-DEH group. Scale bar, 50 μm.


#### Results of the effects of COS and DEH on TLR4, PI3K, and NF-κB p65 in colonic tissues of UC mice were detected by western blot (WB)
  It can be observed from Fig. 7 the expressions of TLR4, PI3K, and NF-κB p65 (proteins encoded by TLR4, PIK3R1, and RELA) in the model group mice were all upregulated, and the upregulation of TLR4 and PI3K was significantly higher than that of the control group mice. The 5-ASA-treated mice exhibited downregulation of these proteins compared with the model group. After treatment with COS or DEH, the expressions of the three proteins decreased with increasing dose.

  Fig. 7The protein expression of TLR4, PIK3R1 and RELA was analyzed by WB. (A) Representative WB image. (B-D) Data are presented as mean ± SD (n = 3). #P < 0.05, ##P < 0.01, ###P < 0.001, vs. the control group; *P < 0.05, **P < 0.01, ***P < 0.001, vs. the model group.


#### Results of the effects of COS and DEH on TLR4, PI3K, and NF-κB p65 in colonic tissues of UC mice were detected by enzyme-linked immunosorbent assay (ELISA)
  As shown in Fig. 8, the levels of TLR4, PI3K, and NF-κB p65 in the colon tissue of mice in the model group were significantly higher than those in the control group (P < 0.001). However, the concentration of three proteins decreased after administration. The TLR4 level was significantly decreased in the 5-ASA group, H-DEH group and H-COS group (P < 0.001). The effects of the M-COS group and the H-DEH group on the reduction of NF-κB p65was most significant (P < 0.001). The 5-ASA group and H-DEH group had the most significant effect on the decrease of PI3K. In addition, UC mice were given different doses of COS or DEH to produced effects showed that the degree of reduction in the concentration of TLR4, NF-κB p65, PI3K was proportional to the drug concentration.

  Fig. 8The protein expression of TLR4, PIK3R1 and RELA in colonic tissues was ELISA analyzed. (A-C) Diagram of TLR4, PIK3R1 and RELA protein expression (n = 6). #P < 0.05, ##P < 0.01, ###P < 0.001, vs. the control group; *P < 0.05, **P < 0.01, ***P < 0.001, vs. the model group.


## Discussion
  In this study, network pharmacology was used to find the target proteins of COS and DEH for the treatment of UC. Then, the target proteins were analyzed by PPI analysis, GO analysis and KEGG analysis. After PPI of the target proteins, we found that TLR4, PTGS2, RELA, NOS3, and MPO had the strongest interactions among the target proteins, indicating that COS and DEH may exert their therapeutic effects on UC through the interactions of these five proteins.

  The GO enrichment results showed that the BPs of COS and DEH in the treatment of UC were mainly reflected in the response to peptides, hormones and OS. Studies on UC have shown that prostaglandins and thromboxane A may mediate the inflammatory process of UC19,20. In addition, the expression of multiple peptides in UC patients differs from that in healthy people. Animal experiments have demonstrated that the expression of corticotropin releasing hormone in the colonic mucosal epithelium of UC rats is increased, and the increase of the hormone may promote the development of UC21,22. Several studies have shown that AR or DEH may treat diseases by reducing the levels of these hormones23,24. In the process of inflammation, neutrophils produce a large amount of ROS, leading to OS. Excessive ROS act on endothelial cells, leading to cell damage, aggravating inflammatory cell infiltration, forming a vicious circle and promoting ulcerative necrosis of the intestinal mucosa25. Enhanced OS is not only the main factor promoting UC, but also leads to DNA damage and promotes the transition from inflammation to tumor26,27. Reducing OS can alleviate inflammatory manifestations of UC28. Several studies have shown that COS and DEH can reduce the cell damage caused by OS for the treatment of OS-induced diseases29,30,31. It can be seen from 3.1.5 that the therapeutic effect is primarily related to the transcription and translation of proteins and peptides, signal transduction, sterilization, transcription factor binding, and protein kinase binding. The major transport mechanisms for colonic absorption of proteins and peptides are paracellular transport, intercellular transport, carrier-mediated transport, and receptor-mediated transport32. These have covered most of the CCs where network pharmacology predicts the action of key proteins. This is mutually corroborated with the enriched BPs described above.

  KEGG enrichment results included cancer pathways, chemical carcinogenesis-ROS, human cytomegalovirus infection, HIF-1 signaling pathway, NF-κB signaling pathway and other pathways. During immunosuppressive therapy, UC patients are prone to human cytomegalovirus infection due to low immunity33. Human cytomegalovirus can induce PI3K/AKT activation and lead to cancer development, which may lead to refractory UC33. After treatment with PI3K inhibitors, the symptoms of UC in UC patients and experimental animals were alleviated34. COS and DEH can inhibit the PI3K/AKT pathway, and they may alleviate UC by inhibiting the pathway35,36. HIF-1α can promote angiogenesis and induce autophagy, and its expression level is positively correlated with disease severity in UC patients37. COS and DEH can regulate HIF-1 to mediate disease development38,39. Downregulating the NF-κB pathway in UC patients can reduce the secretion of inflammatory factors and relieve the symptoms of UC40. COS can regulate the LPS-TLR4-NF-κB pathway, regulate OS, and reduce inflammation41.

  Through PPI analysis and compound-target-pathway network analysis, we concluded that the key targets were TLR4, PTGS2, RELA, NOS3, MPO, CHUK and PIK3R1. The seven targets were docked with the compounds. The results showed that the docking effects were good except that CHUK was not easily able to form hydrogen bonds with COS and DEH. This suggested that TLR4, PTGS2, RELA, NOS3, MPO and PIK3R1 may be the key binding targets of COS and DEH in treating UC. The research on COS and DEH regulating MPO in the treatment of UC has been reported38,42. TLR4, RELA and PIK3R1 proteins have been widely studied. Therefore, these three target proteins were selected to be carried out in animal experiments. The effects of COS and DEH on UC mice were observed through the weight changes, colon length, DAI score, pathological changes and protein expression of the colon during the experiment.

  The experimental results showed that COS and DEH can alleviate DSS-induced weight loss, diarrhea, hematochezia and colonic histopathological changes of mice. The results of WB and ELISA also showed that the upregulation of TLR4, PI3K, and NF-κB p65 caused by DSS could be reduced by treating mice with COS or DEH. Overall, in terms of the regulation of these target proteins by the different doses of COS and DEH, the trend of down-regulation of the target proteins was more obvious as the dose increased. In addition, the effects of COS and DEH on the expression levels of three target proteins may be slightly different, which may be related to the tightness of protein-molecule binding. It needs to be demonstrated in further experiments.


## Conclusion
  The results of this work confirmed that COS and DEH may treat UC by regulating genes, such as those related to protein transcription, signal transduction, and coagulation. Subsequently, the molecular docking of COS and DEH with the key target proteins TLR4, RELA and PIK3R1 screened by network pharmacology revealed that the compounds docked well with the target proteins. The results of animal experiments also showed that COS and DEH alleviated the symptoms of UC mice and downregulated the expression of TLR4, PIK3R1 and RELA to reduce the inflammatory manifestations. The results indicated that COS and DEH have potential in the treatment of UC, and laid the foundation for the treatment of UC with AR.


## Materials and methods

### Collection of compound targets and UC targets
  The websites and references of the databases used in the experiments are listed in Supplementary Table S1. Targets were collected from TCMSP database, STITCH database, BindingDB database, Drugbank database, SEA database, SwissTargetPrediction database, Pharmapper database, TCMID database, ETCM database, ChEMBL database and SuperPred database with the search terms of “costunolide” and “dehydrocostus lactone,” respectively. Using “ulcerative colitis” as the search term, the targets were collected from TCMSP database, DisGeNET database, OMIM database, DrugBank database, Therapeutic Target Database database, Gene cards database, and Malacards database. Those targets were merged and deduplicated to get target proteins of compounds and disease respectively.


### Obtain the intersecting targets
  The compound targets and disease targets were standardized through the Uniprot database. The common target of the compound-disease was screened to obtain the potential target of COS and DEH in treating UC.


### Build protein protein interaction network
  The intersecting targets were imported into STRING database to build a protein protein interaction (PPI) network diagram. The obtained tsv file of PPI was imported into cytoscape 3.8.0 software, rearranged the nodes according to the degree values, and reconstructed the PPI network diagram.


### Gene ontology analysis and kyoto encyclopedia genes genomes enrichment analysis of intersecting targets
  The intersecting targets were imported into the metascape database, and GO analysis and KEGG analysis were performed on the intersecting targets.


### Build the component-target-pathway network
  Based on the selected intersecting targets and KEGG analysis results, a component-target-pathway network was constructed by cytoscape.


### Molecular docking of compounds to target proteins
  The PubChem database was used to download the sdf files of COS and DEH. Two files were imported into Chem3D 20.0, and they were saved as mol2 files. The pdb files of key proteins were downloaded from the RCSB PDB database. The compound’s files and target proteins were preprocessed by AutoDock. Docking boxes were predicted by proteinsplus. Molecular docking was performed by AutoDock software, and the docking results were output by Pymol software.


### Animal experiments design and procedures
  Male C57BL/6 mice (body weight, 18–22 g) were obtained from SPF (Beijing) Biotechnology Co., Ltd. (Beijing, China). All animals were raised on a 12 h light/dark cycle with a room temperature of 25 ± 2 °C and humidity of 60–65%. All animals were allowed to eat and drink freely and were fed adaptively for one week. Mice were randomly assigned into ten groups of six mice each: control, model, 5-ASA (50 mg∙kg-1∙day-1), L-COS (6 mg∙kg−1∙day−1), M-COS (12 mg∙kg−1∙day−1), H-COS (24 mg∙kg−1∙day−1), L-DEH (6 mg∙kg−1∙day−1), M-DEH (12 mg∙kg−1∙day−1), H-DEH (24 mg∙kg−1∙day−1). The dosages were calculated by administration and dosage of AR in Pharmacopoeia of the People’s Republic of China (2020)and the approximate decoction rate43,44,45. On days 1–7, mice in the control group drank normal water, and the other groups drank 2% dextran sulfate sodium (DSS). On days 8–10, the mice in each group were given normal drinking water. Every two days, fresh drinking water was made. Mice in each group were given the corresponding doses of drugs. The control group and model group were given the same volume of 0.5% CMC-Na solution (10 ml∙kg−1) for 10 days. Mice were executed on day 11. The colon tissue of mice was isolated and washed with normal saline solution. About 0.5 cm of mice colon tissue were cut and fixed in 4% paraformaldehyde for histological analysis. The remaining colon tissue was stored in a -80 °C freezer. With regard to the toxicological studies of different doses of COS and DEH, the author found that 10 mg/kg, 20 mg/kg, 40 mg/kg, 80 mg/kg and 160 mg/kg of COS were not toxic to rats and no obvious toxicity was found when 30 mg/kg COS was administered to mice for 28 days after reviewing the literature33,46. Doses of 10 mg/kg and 15 mg/kg of DEH showed no significant toxicity in nude mice; doses of 20 mg/kg and 40 mg/kg of DEH did not cause noticeable damage to the liver, spleen, and kidneys in tumor-bearing nude mice47,48.


### Materials
  Costunolide (No. MXJNZ20220110) and dehydrocostus lactone (No. QQMXJNZ20220110) were purchased from the Nanjing Spring and Autumn Biological Engineering Co., Ltd. (Nanjing, China). DSS (No. OK220315T) was purchased from the Tai’an Jiangzhou Biotechnology Co., Ltd. (Shandong, China). 5-Aminosalicylic acid (No. RH363912) was purchased from the Shanghai Yien Chemical Technology Co., Ltd. (Shanghai, China). Carboxymethylcellulose sodium (No. 2101110) was purchased from the Xilong Science Co., Ltd. (Guangdong, China). NF-κB p65 (No. AF5006) and PI3K p85 alpha (No. AF6241) were purchased from the Affinity Biosciences, Inc. (Cincinnati, OH, USA). TLR4 (No. bs-20594R) was purchased from the Beijing Bioss Biotechnology Co., Ltd. (Beijing, China). β-Actin (No. ab8226) was purchased from the Abcam. HRP-Goat anti Rabbit (No. E-AB-1003) and HRP-Goat anti Mouse (No. E-AB-1001) were purchased from the Elabscience Biotechnology Co., Ltd. (Wuhan, China). TRIS (No. 0497–500 g) was purchased from the Amresco Inc. (Solon, OH, USA). Tween 20 (#T8220) was purchased from the Beijing Solarbio Science & Technology Co., Ltd. (Beijing, China). RIPA lysate (No. P0013D), PMSF (No. ST505) and protease phosphatase inhibitor (No. P1046) were purchased from the Beyotime Biotechnology Co., Ltd. (Shanghai, China). The TLR4 kit (No. 202209), RELA kit (No. 202209) and PIK3R1 kit (No. 202209) were purchased from the Jingmei Biotechnology Co., Ltd. (Jiangsu, China).


### External indicators of pathological changes in ulcerative colitis mice
  Body weight, stool consistency and blood in the stool of mice were recorded daily and scored according to Supplementary Table S2. After the mice were sacrificed, the colon length was measured.


### Histopathology observation
  Fixed colon tissues were dehydrated, transparent, waxed, embedded and stained. The changes of histopathology were observed under an optical microscope.


### WB
  Proteins in colon tissues were extracted by using the RIPA lysis buffer. The proteins were separated by sodium dodecyl sulfate polyacrylamide gel electrophoresis, transferred to a polyvinylidene fluoride (PVDF) membrane, and blocked with 5% skimmed milk for 1 h. The blocked PVDF membrane was incubated with primary antibodies (dilution, 1:1000) overnight and washed five times with TBST. Subsequently, the membrane was incubated with secondary antibodies (dilution, 1:3000) for 1 h and washed five times with TBST. The protein side of the membrane was dripped with the newly prepared ECL mixture. The exposure conditions were adjusted. The film was developed, fixed and scanned. The results were analyzed by ImageJ software.


### ELISA
  The remaining colon tissue was homogenized, and the supernatant was obtained by centrifugation. The contents of TLR4, RELA and PIK3R1 were detected by ELISA kits.


### Statistical analysis
  All data were expressed as mean ± standard deviation (SD) and analyzed by one-way analysis of variance followed by LSD’s post hoc test and Tamhane’s post hoc test with the SPSS 19.0 software to evaluate the significant difference between groups. A value of P < 0.05 was considered statistically significant. GraphPad Prism 9.4.1 visualizes the analysis results.


## Electronic supplementary material
  Below is the link to the electronic supplementary material.

  Supplementary Material 1


## Acknowledgements
  The authors would like to thank Hua Du of the School of Pharmacy of Chengdu University of Traditional Chinese Medicine for helpful suggestions for revising this article. Any errors are our own.