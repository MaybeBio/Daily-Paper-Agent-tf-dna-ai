# Potential molecular mechanisms of Ermiao san in the treatment of hyperuricemia and gout based on network pharmacology with molecular docking


## Abstract
  A network pharmacology integrated molecular docking strategy was used to predict the underlying molecular mechanism of Ermiao san in the treatment of hyperuricemia and gout. Traditional Chinese medicine systems pharmacology (TCMSP) database and analysis platform were used to screen out the active compounds and their targets of Ermiao san. The disease target genes related to hyperuricemia (HUA) and gout were obtained by searching CTD, DisGeNET, DrugBank, GeneCards, OMIM, TTD, and PharmGKB databases with “Hyperuricemia” and “Gout” as keywords, respectively. The potential targets of Ermiao san in the treatment of HUA and gout were screened through a Venn diagram. The protein–protein interaction network was constructed using Cytoscape software. Gene ontology and Kyoto Encyclopedia of Genes and Genomes enrichment analyses were then conducted. Finally, some compounds and core targets were selected for molecular docking verification by Autodock Vina and Pymol software. Forty-six active compounds, such as quercetin, wogonin and beta-sitosterol, etc were identified. Ermiao san plays a therapeutic role in HUA and gout regulating various biological processes, cellular compounds, and molecular functions. The core targets of Ermiao san for treating HUA and gout are AT1 (namely Protein Kinase Bα), interleukin-1 beta, prostaglandin-endoperoxide synthase 2, JUN, etc. And the key pathways are nuclear factor-κB, interleukin-17 and tumor necrosis factor. The results of molecular docking analyses suggested that active compounds of Ermiao san could bind well to the core protein receptors. Ermiao san has a synergistic mechanism of multiple compounds, multiple targets, and multiple pathways in the treatment of HUA and gout, which provides a good theoretical basis for the clinical application.


## 1. Introduction
  Uric acid (UA) is the end product of purine and nucleic acid metabolism. Hyperuricemia (HUA) is caused by disorders of purine metabolism in the body, increased production and/or decreased excretion of UA, and abnormal blood UA levels. Gout is a recurrent inflammatory disease caused by increased purine biosynthesis and metabolism, excessive production of UA or poor excretion of UA, resulting in elevated blood UA and deposition of urate crystals in joint synovium, bursa, cartilage, and other tissues. The disease is characterized by the discovery of birefringent sodium urate monohydrate crystals in synovial fluid and tophi. Its clinical features are: HUA and interstitial nephritis caused by characteristic acute arthritis, tophi, and urate crystals and deposits. HUA is a risk factor for gout and its occurrence is strongly correlated with gout.[1,2] In recent years, with economic development and lifestyle changes, the incidence of HUA and gout has been steadily increasing to 0.58–2.89/1000 people worldwide[3] and 0.03% to 10.47% in China.[4] The incidence of HUA among adolescents is also increasing.[5] Thus, HUA and gout have become increasingly common serious diseases that threaten human health and tend to occur at younger ages than in the past.

  At present, drugs such as allopurinol, febuxostat, and benbromarone are commonly used to reduce UA levels[6] since studies have shown that allopurinol and febuxostat can effectively reduce serum uric acid (SUA) levels. However, they may increase the frequency of acute gout flares in the initial use, and their cardiovascular safety in patients with gout is controversial.[7,8]

  The main goal of Western medicine treatment of gout is to stop acute attacks, control SUA and avoid recurrences. Although the current treatment effect of stopping acute attacks and controlling SUA is good, it has been found in practical applications that good control of SUA cannot prevent recurrences of gout. There is also no effective treatment for the core problem of urate deposition removal. The use of these drugs is often accompanied by gastrointestinal reactions, hypersensitivity reactions, liver and kidney damage and other adverse reactions,[9,10] which are difficult for patients to tolerate and their SUA levels generally increase after drug withdrawal.

  Therefore, in recent years, clinical medicine has often been combined with traditional Chinese medicine (TCM) to control HUA and gout. Chinese medicine has a unique curative effect on HUA and gout. As a classical Chinese medicine prescription, the Ermiao san formula has been widely used for treating HUA and gout. Ermiao san, derived from the Danxi Heart method, is a TCM comprised of Rhizoma Atractylodis (Cang Zhu) and Cortex Phellodendri (Huang Bo). It is mainly used for lower limb weakness and weakness caused by hot and humid betting, redness, swelling, and heat pain in the feet and knees, under the humid tropical zone, lower wet sores, short yellow urine, yellow greasy tongue coating, etc. It has the function of clearing heat and drying dampness.

  This prescription mainly treats the dysfunction syndrome of damp-heat betting. In the prescription, Phellodendron is bitter and cold to clear away heat, Atractylodes is bitter, warm, and dry, and it is a wonderful medicine for treating yin-divided damp-heat dysfunction syndrome. The medicine has only 2 flavors, but the effect is outstanding.[11] Clinical studies have also shown that Ermiao san significantly reduces SUA, inhibits the synthesis of UA, dissolves urate, alleviates inflammatory reactions, and protects the kidney.[12] However, the underlying pharmacological mechanism is still unclear, which limits its clinical application and promotion. In this study, the mechanism of Ermiao san in treating HUA and gout was further studied based on network pharmacology and molecular docking.


## 2. Materials and Methods

### 2.1. Materials
  The data and software used were: TCMSP (traditional Chinese medicine systems pharmacology database and analysis platform, http://tcmspw.com/tcmsp.php), Human Gene Database (GeneCards, https://www.genecards.org/), Online Mendelian Inheritance in Man (OMIM, https://www.omim.org/), the Pharmacogenomics Knowledge Base database (PharmGKB, https://www.pharmgkb.org/), DrugBank database (https://www.drugbank.ca/), DisGeNET database (https://www.disgenet.org/), Therapeutic Target Database (TTD, http://db.idrblab.net/ttd/), Comparative Toxicogenomics Database (CTD, http://ctdbase.org/), UniProt database (https://www.UniProt.org/); PubChem database (https://pubchem.ncbi.nlm.nih.gov/), STRING (Protein Interaction Network Database, https://string-db.org/); RCSB PDB (http://www. rcsb.org/); Perl5.32.1.1 software; Cytoscape3.8.0 software; PyMOL software; ChemBio3D 2014 software, AutoDock Vina software, OpenBabel 3.1.1 software; R 4.1.1 Software and related R software packages.


### 2.2. Methods

#### 2.2.1. Screening the active compounds and targets of Ermiao san.
  The compounds of Rhizoma Atractylodis and Cortex Phellodendri in Ermiao san were collected and summarized in TCMSP, oral bioavailability (OB) ≥ 30% and drug-like (DL) ≥ 0.18 were selected as the screening criteria for the active compounds, and the similarity was removed. Then, Perl software and UniProt database were used to determine the human gene abbreviation of each target point, and the possible target protein of Ermiao san was obtained.


#### 2.2.2. Screening of disease targets for HUA and gout.
  Using “Hyperuricemia” or “Gout” as keywords, the CTD, DisGeNET, DrugBank, GeneCards, OMIM, TTD, and PharmGKB databases were used to search for disease targets related to HUA and gout. The results of each database were collected, duplicates were deleted, and the combination set was selected.


#### 2.2.3. Construction of the protein–protein interaction network (PPI) and identification of core targets.
  The active ingredient targets and disease targets obtained in 2.1 and 2.2 were imported into the STRING database for PPI analysis, and the interaction network diagram of Ermiao san treating HUA and gout was constructed by using the Cytoscape visualization protein interaction network. The core targets were screened by the Cytoscape plug-in CytoNCA.


#### 2.2.4. Gene ontology (GO) functional enrichment and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichment analyses.
  Through R software and related packages, GO and KEGG enrichment analyses were carried out under the conditions of Fisher’s test P < .05 and q < 0.05 (q is the corrected P value). The smaller the P value is, the higher the enrichment degree is. The top 30 entries with the highest enrichment degree in KEGG are shown in a histogram constructed with R software and related packages. GO enrichment analyses were performed for each of the 3 GO categories: biological process (BP), cellular component (CC), and molecular function (MF), and screened out the first 10 functional categories to construct a histogram.


#### 2.2.5. The main active ingredient was docked with the target molecule.
  The molecular structure of the key target was retrieved and downloaded from the RCSB PDB database. The ligand and nonprotein molecules, such as water molecules, in the target proteins were removed by using PyMOL software and the results were saved as PDB files. The PubChem database was used to download PDB latticed documents of the major active partitioned 2D structures, which were then converted to MOL2 format by OpenBabel software. Finally, they were imported into the AutoDock Vina online platform for molecular docking verification. It is generally believed that when the docking result of the system is <0, this indicates that there is a certain binding activity between the ligand and the receptor molecule. The closer the ligand binds to the receptor, the greater the energy released, and the lower the binding energy.[13,14]


## 3. Results

### 3.1. Prediction of active compounds and targets of Ermiao san
  With OB ≥ 30% and DL ≥ 0.18 as filtering conditions, a total of 46 active compounds of Ermiao san were screened from the TCMSP database (Table 1), and 189 targets of active compounds of Ermiao san were predicted by the TCMSP database.


### 3.2. Prediction of targets and common targets of HUA and gout
  A total of 1132 targets associated with HUA and gout diseases were identified using the CTD, DisGeNET, DrugBank, GeneCards, OMIM, TTD, and PharmGKB databases (Fig. 1A). After the intersection of 1132 disease targets and 189 action targets of Ermiao san’s active compounds, 119 common targets were obtained (Fig. 1B), which are the main potential targets of Ermiao san in the treatment of HUA and gout.


### 3.3. Network construction of target interactions of Ermiao san active compounds in HUA and gout
  Forty-six active compounds were associated with 119 targets of Ermiao san for the treatment of HUA and gout, and a network diagram of Ermiao san-compound-target disease was drawn through Cytoscape (Fig. 2). The network consists of 138 nodes (27 compounds, 119 targets) and 287 edges.


### 3.4. PPI network of Ermiao san in the treatment of HUA and gout
  The PPI network was visualized by Cytoscape software with 119 nodes and 2356 edges based on the protein–protein interactions from the String database (Fig. 3A). The 6 topological features were calculated by CytoNCA and used to identify candidate targets: “degree centrality (DC), betweenness centrality (BC), closeness centrality (CC), eigenvector centrality (EC), local average connectivity (LAC), and network centrality (NC)”. According to the DC, BC, CC, EC, LAC, and NC values, the core target was obtained after 2 topological analyses (Fig. 3B and C); finally, 14 nodes and 1133 lines with the highest degree were screened as hub genes, which included AKT1, tumor protein p53 (TP53), matrix metallopeptidase 9 (MMP9), hypoxia-inducible factor 1-alpha (HIF1α), caspase-3 (CASP3), vascular endothelial growth factor A (VEGFA), JUN, epidermal growth factor (EGF), prostaglandin-endoperoxide synthase 2 (PTGS2), NF-kappaB inhibitor alpha (NFKBIA), interleukin-6 (IL-6), Fibronectin 1 (FN1), myelocytomatosis oncogene (MYC), and interleukin-1 beta (IL-1β) (Fig. 3D).


### 3.5. Enrichment analysis of Ermiao san on prediction targets of HUA and gout
  GO and KEGG enrichment analyses were carried out by R software and the related R software packages with Fisher’s test P < .05 and q < 0.05 as conditions. The smaller the q value was, the higher the enrichment degree was. In addition, 2266 BP, 35 cell CC and 154 MF were enriched by GO analysis, and 167 KEGG pathways were enriched by pathway enrichment. To draw the GO function histogram of Ermiao san in HUA and gout, the top 10 BP, CC, and MF results at P < .05 were selected (Fig. 4A).

  The top 30 pathways with the highest degree of enrichment were selected for enrichment analysis, among which the lipid and atherosclerosis signaling pathways had the highest degree of enrichment (Fig. 4B).


### 3.6. Molecular docking
  Furthermore, AutoDock Vina software was adopted for the molecular docking study of the core active compounds and core targets (TP53, FN1, MMP9, HIF1α, CASP3, VEGFA, IL-6, JUN, EGF, PTGS2, MYC, AKT1, EGFR, and IL-1β). A higher binding activity between the compound and the target protein receptor implied a lower binding energy. The results showed that the docking of active compounds with the core target protein receptors was <0 kcal/mol (a majority were <−5 kcal/mol) (Table 2). The molecular docking partial results of the compounds with the highest binding energy corresponding to the fourteen targets are displayed (Fig. 5).


## 4. Discussion
  Network pharmacology is an emerging interdisciplinary subject that analyzes the interaction among TCM compounds, targets and diseases by a systematic network model based on existing databases and provides a new theoretical basis and methodological basis for exploring the mechanism of TCM compound therapy for complex diseases.[15–17] In this study, 46 active compounds of Ermiao san were screened out, and 119 targets for the treatment of HUA and gout were predicted by a network pharmacology research strategy. The network diagram suggested that quercetin, wogonin and beta-sitosterol, etc might be the key effective compounds of Ermiao san in the treatment of HUA and gout. GO enrichment analysis suggested that Ermiao san was mainly related to transcription factor DNA binding, RNA polymerase II-specific transcription factor DNA binding, ubiquitin-like protein ligase binding, etc in the treatment of HUA and gout. KEGG enrichment analysis suggested that Ermiao san may treat HUA and gout through the NF-κB, IL-17 and TNF signaling pathways. Meanwhile, several compounds, including quercetin, wogonin, and beta-sitosterol, were selected for docking simulation with candidate target molecules, such as CASP3, JUN, PTGS2, and IL-1β, to verify the prediction results of the network pharmacology. AutoDock Vina docking results showed that the compounds (quercetin, wogonin, and beta-sitosterol) had good docking activity with the targets. The above results indicate that Ermiao san has the effect of “multicompounds, multitarget and multipathway” in the treatment of HUA and gout, which has been verified by preliminary molecular simulations.

  Quercetin and wogonin are important effective compounds in Ermiao san for the treatment of HUA and gout. Studies have shown that quercetin can exert analgesic and anti-inflammatory effects by inhibiting the activation of the NF-κB pathway in MSU-induced gout mouse models.[18] Related studies have shown that quercetin reduces SUA levels by inhibiting the activity of xanthine oxidase in HUA mice.[19] Quercetin has also been proven to regulate the expression of MAPK8.[20] Studies have shown that wogonin can inhibit NF-κB-dependent transcriptional activity without affecting NF-κB translocation, thereby exerting an anti-inflammatory effect.[21]

  The above results can confirm to a certain extent that network pharmacology and molecular docking can preliminarily clarify the mechanism of Ermiao san in the treatment of HUA and gout at a theoretical level.

  According to the enrichment analysis results, the bioactive compounds of Ermiao san act on multiple targets to treat HUA and gout through multiple pathways involving multiple signaling pathways, including TNF, IL-17 and apoptosis. It is well known that TNF signaling, especially TNF-α, plays a major role in the pathological progression of hyperuricemia and gout. TNF-α is a pro-inflammatory cytokine, which can not only induce RA to secrete lipopolysaccharide, but also promote the proliferation of fibroblast-like synoviocytes.[22] Studies have shown that TNF-α expression is significantly increased in MSU crystal-induced gout arthritis mice, and is positively correlated with the severity of arthritis.[23] A clinical study has shown that the TNF-α inhibitor etanercept significantly reduces clinical manifestations and laboratory findings in gouty arthritis.[24] The compound quercetin has been shown to reduce TNF-α levels.[25] Ermiao san has been confirmed to inhibit the production of NO, TNF-α and IL-6 in RAW264.7 cells stimulated by lipopolysaccharide (LPS).[26] This suggests that Ermiao san may treat gout and hyperuricemia by inhibiting the TNF signaling pathway. IL-17 is a characteristic cytokine secreted by TH17 cells that is involved in the inflammatory response in vivo. Studies have found that the use of neutralizing antibodies against IL-17 can reduce joint swelling and inflammatory infiltration of tissues in a gout animal model[27] and improve the symptoms of the disease. Experimental studies have shown that the binding of IL-17 to its receptors can activate downstream signaling pathways including NF-κB and MAPK, resulting in the expression of pro-inflammatory cytokines such as IL-6 and TNF-α, thereby promoting inflammation.[28,29] IL-17 can activate the NF-κB pathway by activating related receptors; at the same time, inflammatory cytokines such as TNF-α and IL-1β can also enhance the activity of IL-17 and promote the matrix metalloproteinase MMP1/3/9/13 generation.[28] In patients with gouty arthritis, the NF-κB and activating protein 1 (AP-1) pathways are activated,[30] resulting in the proinflammatory cytokines IL-1β, IL-8, IL-17, TNF-α, and NLRP3 increased inflammasome.[31] Studies have shown that compounds such as stigmasterol[32] and Quercetin[33] can inhibit IL-17 levels. This suggests that Ermiao san may treat gout and hyperuricemia by inhibiting the IL-17 signaling pathway. It has been shown that increased UA levels can induce apoptosis of renal tubular cells by disrupting the balance between antiapoptotic and proapoptotic proteins.[34] In addition, renal tubular epithelial cell apoptosis has also been found in renal biopsies of patients with familial gout nephropathy.[35] Therefore, it can be speculated that treatment of HUA and gout with Ermiao san is closely related to its anti-inflammatory and anti-apoptotic effects.

  Through the screening of network targets, the results showed that Ermiao san may treat HUA and gout through core targets such as AKT1, IL-1β, PTGS2, and JUN. AKT1 (namely, protein kinase B α) is mainly involved in various biological processes, such as metabolism, proliferation, cell growth and angiogenesis. Studies have found that UA can induce the phosphorylation of AKT in monocytes and activate mTOR, thus inhibiting autophagy.[14] However, UA plays a dual role in oxidative stress. In an acute HUA mouse model induced by potassium oxazinate, UA inhibits AKT phosphorylation and reduces insulin sensitivity in liver cells through a ROS-dependent pathway,[36] indicating that AKT is one of the important targets of UA signal transduction. IL-1β participates in the inflammatory response of gout[37] and is considered to be a key factor in the induction of inflammation by sodium urate crystals.[38] PTGS2 (i.e., COX-2) plays an important role in regulating inflammation and relieving pain. It is highly expressed in acute gouty arthritis, and blocking its expression can effectively inhibit the occurrence of inflammation.[39] It is worth noting that one of the main mechanisms of action of drugs currently used to treat HUA and gout attacks is to inhibit xanthine oxidase, and the main target of these drugs is xanthine dehydrogenase (XDH). Although XDH is not included in the core targets, the role of XDH in the mechanism of lowering uric acid is not denied. In general, it is speculated that Ermiao san can treat HUA and gout by reducing inflammation and antioxidation and reducing UA levels through multiple targets.

  This study has some limitations. As a new methodology, although certain results have been achieved in the study of Chinese medicine for the treatment of diseases, there are some shortcomings in network pharmacology itself. First, network pharmacology research relies on database mining. The completeness of the data in the database dramatically affects the reliability of the results. Second, this research lacks experimental verification. Follow-up studies need to be based on these findings to verify the core targets and clarify the mechanism of action of Ermiao san on HUA and gout. Third, there were many target pathways identified in this study, but only some important compounds and pathways of key targets could be analyzed, and the mechanism of action could not be fully studied. Finally, most network pharmacology tends to study compounds corresponding to protein molecules, while the metabolic processes of herbal medicines through gut microbiota and their role in disease treatment are often underexplored. In the future, we will conduct further in-depth research on other signaling pathways and the metabolic process of Ermiao san through the intestinal flora, and fully explore the mechanism of Ermiao san in the treatment of hyperuricemia and gout.


## 5. Conclusion
  In summary, Ermiao san may play a role in reducing inflammation, antioxidation, and anti-apoptotic activity and lowering UA levels through AKT1, IL-1β, PTGS2, and JUN etc core targets and NF-κB, IL-17 and TNF main signaling pathways in the treatment of HUA and gout. The compounds-target-pathway network constructed in this study provides a theoretical basis for the treatment of HUA and gout, suggesting ways for clinicians to use drugs, and provides an evidence-based basis for the modernization of traditional Chinese medicine.


## Author contributions
  Conceptualization: Yin-Hong Geng.

  Data curation: Jia-Hui Yan.

  Formal analysis: Liang Han.

  Investigation: Zhe Chen.

  Methodology: Lin-Qi Zhang, Ya-Fei Liu.

  Project administration: Lin-Qi Zhang.

  Resources: Ya-Fei Liu.

  Software: Chun-Dong Song.

  Supervision: Sheng-Hao Tu.

  Validation: Feng-Yang Duan.

  Visualization: Feng-Yang Duan.

  Writing – original draft: Yin-Hong Geng.

  Writing – review & editing: Ya-Fei Liu.