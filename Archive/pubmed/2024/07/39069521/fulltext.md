# Target analysis and identification of curcumin against vascular calcification


## Abstract
  To investigate the mechanism of curcumin (CUR) on vascular calcification (VC), we screen for common targets of CUR and atherosclerosis and verify the targets genes in vivo and in vitro experiments. The common targets of CUR and AS were screened and obtained using different databases. These target genes were analyzed by GO and KEGG pathway enrichment analysis. PPI network analysis was performed and to analyze the key targets. A rat VC model was constructed and CUR was fed for three weeks. The changes of vascular structure and calcium salt deposition were observed in H&E and Von Kossa staining. Further, the expression of these target proteins was detected in the primary VSMCs of VC. The 31 common targets were obtained. GO functional enrichment analysis obtained 1284 terms and KEGG pathway enriched 66 pathways. The key genes were identified in the cytoHubba plugin. The molecular docking analysis showed that CUR bound strongly to EGFR, STAT3 and BCL2. The animal experiments showed the deposition calcium salt reduced by the CUR administration. These proteins BMP2, RUNX2, EGFR, STAT3 and BAX expression were upregulated in VC group and CUR attenuated the upregulated expression. The signal protein Akt and p65 expression increased in VC group and decreased in CUR group. We identified some common target genes of CUR and AS and identified these key genes. The anti-VC effect of CUR was associated with the inhibition of upregulation of EGFR, STAT3 and RUNX2 expression in VSMCs.


## Introduction
  Atherosclerosis (AS) is the common cause of high cardiovascular mortality and morbidity. The pathogenesis of AS is accepted as a chronic, multi-component inflammatory disease that leads to the development of lesions in the vessel wall1. Vascular calcification (VC) is a common condition found in advanced atherosclerotic lesions. Accordingly, a detailed understanding the pathogenesis of VC may be the key to the prevention of AS progression2.

  The underlying mechanisms suggested that vascular smooth muscle cells (VSMCs) initially exhibited a contractile phenotype through the expression of MYOCD-regulated contractile proteins. Conversely, these cells manifest as hydroxyapatite deposition in calcified vessel walls, resulting in an increased risk of cardiovascular disease3,4. Our previous studies have shown that RUNX2 is part of a class of cartilage markers associated with VC5. By promoting the signaling pathways of RUNX2 and BMP2, Methoxy flavonoids might promote osteoblast differentiation and enhanced bone mass6. Therefore, understanding of the regulation of target genes and pathways in VC may be the key to finding new drug treatments.

  Chinese medicine has demonstrated unique efficacy in the pretreatment of some chronic metabolic disorders. Curcuma longa (Turmeric) is a plant of the Zingiberaceae family cultivated in China7. Turmeric is extracted from the root of Curcuma longa L. and contains the bioactive polyphenolic compounds of the curcuminoids (Curcumin, CUR), demethoxycurcumin, and bisdemethoxycurcumin. CUR is found in the rhizome of the turmeric plant and makes up about 77% of the curcuminoids. Curcuminoids are considered to be safe by the US Food and Drug Administration (FDA)8. Therefore, identification of target genes and pathways in CUR may be useful for the application of its therapeutic and pharmacological effects.

  Curcumin has shown the therapeutic potential of anti-inflammatory and anti-tumor activity8,9. CUR decreases the expression of pro-inflammatory molecules, such as AP-1, and improves medial elastin structural integrity in the abdominal aorta10,11. CUR attenuated aortic aneurysm formation by downregulating nuclear factor-κB activation in mice12. CUR could reduce total cholesterol and low-density lipoprotein levels, which was effective against AS and myocardial infarction13,14. These studies indicated that CUR might be a promising therapeutic agent for osteoarthritis by reducing inflammation and oxidative stress. However, whether CUR has a therapeutic modality on VC has not been reported.

  CUR is a natural product with pleiotropic properties that encompass multimodal pathways in the treatment of vascular diseases15. In this study, we screened the common targets of CUR and AS and identified target genes. We performed and the therapeutic modality of CUR on VC in animal experiments and validated the expression of target genes in VSMCs. The current study proposes that CUR has therapeutic potential against VC by a multidisciplinary approach. We expected that this study will provide therapeutic strategies for clinical management.


## Materials and methods

### Reagents and materials
  Curcumin, von Kossay, and alizarin red were bought from Sigma-Aldrich (St. Louis, MO, USA). These primary antibodies were prepared in this study: anti-BMP2, anti- RUNX2, anti-GAPDH, anti-BCL2, anti-Bax, anti-AKT, anti-p65, anti-STAT3 and anti-EGFR purchased from Santa Cruz Biotechnology (Santa Cruz, CA, USA). These secondary antibodies were purchased from Proteintech Group. The animal procedures were conducted in accordance with the National Institutes of Health Guide for the Care and Use of Laboratory Animals of the National Institute of Health (NIH publication 86-23, revised 2011) and approved by the Institutional Animal Care and Use Committee at Hubei University of Science and Technology, China.


### Animals and grouping

#### VC model and CUR administration
  We calculated the sample power with eight animals per group is needed to show significant differences of 20% or more. The acceptable power level was considered to be between 0.8 and 0.9.The rat model of VC was constructed according to the previously described method16. Briefly, the male Sprague–Dawley rats (4-week-old, 200–250 g) were randomly divided into three groups (n = 8 per group): control (NC) group, model (VC) group, CUR administration after model (CUR) group. After the rats administered with the vitamin D3 (5 mg/kg) by intra-muscular injection for five days, the left common carotid artery was elastically ligated and incubated with calcium chloride (0.12 mol/L) for 30 min. The control group was administered saline. After successful modeling, the CUR group was fed with CUR (200 mg/kg/d, oral gavage) for three weeks. All animals were sacrificed with CO2 inhalation, and the left common carotid arteries were prepared for the following experiments. The flow chart of experiments is shown in Fig. 1. All animals were randomized and analyzed in a blinded fashion for in vivo experiments.Figure 1A diagram showing the experimental workflow of CUR in the treatment of AS. The attenuated calcification effect of CUR against AS were analyzed by the calcification artery tissues. Hub genes were extracted by network pharmacology. Hub targets were further verified by molecular docking and were identified the calcification smooth muscle cells (SMCs).


#### HE and Von Kossa staining
  The samples were fixed in 10% formalin and were embedded in paraffin17. Sections were obtained and stained with hematoxylin and eosin (H&E). The tissue pathology under microscope was observed.

  Von Kossa staining was conducted using the method described previously5. The 2% silver nitrate solution incubated with arterial sections on an ultraviolet transilluminator and arterial sections were incubated by 5% sodium thiosulfate. The specimens were counterstained with Nuclear Fast Red (Sigma) and observed.


### Network pharmacology analysis

#### The targets prediction for AS and CUR
  The analysis flow was as followed (Fig. 1): The candidate targets for AS were filtered by searching the keywords ‘‘atherosclerosis” from Traditional Chinese Medicine Systems Pharmacology Database and Analysis Platform (TCMSP, http://tcmspw.com/tcmsp.php) and GeneCards (https://www.genecards.org/). The molecular targets for CUR were screened by searching the keywords ‘‘curcumin” in Swiss Target Prediction (http://www.swisstargetprediction.ch/) and ChEMBL (https://www.ebi.ac.uk/chembl/). The PubChem CID (458-37-7) of CUR was searched in BATMAN-TCM to gain the target-pathway network and CUR was imported into Swiss Target Prediction to acquire the related targets. The intersection was thought to the predicted target of CUR against AS. These targets were exported into UniProtKB (https://www.uniprot.org/) to standardize the named of gene and protein. Mapping of CUR and AS disease common targets, CUR predicted targets and AS targets of action were entered into Wayne Online software to obtain common targets of AS and CUR.


#### GO and KEGG analysis of common targets genes
  We used genes from the R software package “org.Hs.e.g.db” for GO annotation and the “KEGG rest API” (https://www.kegg.jp/kegg/rest/keggapi.html) for the latest KEGG pathway gene annotation18. Taking the annotation as the background, the genes are mapped into the background set. GO and KEGG enrichment analysis was performed using the R software package “clusterProfiler” (version 3.14.3) to obtain the gene set enrichment results. Both a false discovery rate (FDR) < 0.05 and a P < 0.05 were thought statistical significance.


#### PPI network and Hub genes analysis
  These common targets genes were imported into the STRING database (https://string-db.org/) to obtain the relationships through protein–protein interaction (PPI) information19. The information of PPI was further conducted to the Cytoscape software (3.7.2)20, which evaluated the relationship between targets encoding proteins. The node degree was calculated by the Network Analyzer plug-in, which identified the number of these hub genes interconnections. Molecular complex detection (MCODE) was further analyzed for the PPI network modules in Cytoscape.


#### Molecular docking
  The CUR structure is from PubChem Compound and the crystal structures obtained from the RCSB Protein Data Bank (https://www.rcsb.org/). The top six targets proteins were studied. The original format of CUR and target protiens were converted to pdbqt formats using AutoDockTools21. The structures were organized by adding hydrogen atoms and removing water molecules. The molecular docking was conducted with CUR as the ligand and the target protein as the docked acceptor using Autodock Vina. The docking process was determined using the Genetic Algorithm and the docking results were optimised using PyMoL22. The docking score AFFINITY was screened for targets with binding activity and where a docking score of AFFINITY <  − 4.25 kcal/mol was considered as binding activity. A score of − 5.0 kcal/mol indicated better binding activity and the score of − 7.0 kcal/mol indicated strong docking activity between ligand and target23.


### Cell experiments

#### Primary VSMCs culture and treatment with CUR
  Primary VSMCs were prepared from rat aortas using the explant technique as described previously and cultured in Dulbecco’s modified eagle medium (DMEM, Hyclone, USA) supplemented with hydrocortisone, bovine brain extract, gentamicin, amphotericin B, epidermal growth factor and 10% heat-inactivated fetal calf serum until the third passage. CUR was dissolved in dimethylsulfoxide (DMSO) with a stock concentration of 1 mM. Cells were harvested at different time points for the assays.


#### Alizarin Red S staining
  Alizarin Red staining was performed as previously described24. Briefly, the Cells was fixed by 4% paraformaldehyde for 15 min and the sections were rinsed with PBS and incubated with 1% Alizarin Red S solution for 30 min at room temperature. The Alizarin Red S solution was removed, and the specimens were washed with PBS. The specimens stained with Alizarin Red were observed under a light microscope.


#### Real-time PCR
  Total RNA was isolated and cDNA was synthesized using a Servicebio®RT First Strand cDNA Synthesis Kit (ZCIBIO, China) according to the manufacturer’s instructions. 2 × SYBR Green qPCR Master Mix (ZCIBIO, China) was used for real-time PCR. All primer sequences were listed in Supplementary Table 1. The program was as follows: 95 °C for 10 min, followed by 40 cycles of 95 °C for 15 s and 60 °C for 1 min. Three samples were used for PCR array analysis in each group. Relative fold changes of gene expression were calculated according to the manufacturer’s ((ZCIBIO) instructions.


#### Western blotting
  The Western blot assay was conducted as previously described24. Proteins were extracted and centrifuged after the VSMCs were treated with 0-, 10-, 20- and 30-μM CUR for 24 h. The protein extracts were isolated by 10% SDS-PAGE and transferred to polyvinylidene difluoride membranes. The primary antibodies incubated with these membranes and the bands were visualized using an enhanced chemiluminescence reagent. Proteins were quantified by densitometric analysis and GAPDH was used as internal control.


### Statistical analysis
  All data was assessed for normality of distribution and homogeneity of variance prior to statistical analysis. Data was expressed as mean ± SD from at least 3 independent experiments. All data were analyzed by the SPSS21.0 software (IBM, USA). Statistical analysis was performed using one-way analysis of variance or paired t-tests. We performed post-hoc tests with pairwise comparisons, P values were corrected for multiple comparisons using the Bonferroni method. P values less than 0.05 were considered significant.


### Ethical approval
  All animal experiments were performed according to ARRIVE guidelines and the National Institutes of Health Guide for the Care and Use of Laboratory Animals (NIH publication 86-23, revised 2011). All protocols were carried out according to the current legislation relating to animals and experiments involving animals and were approved by the Institutional Animal Care and Use Committee of Hubei University of Science and Technology (approval Number: 2022-01-018).


## Results

### CUR attenuates vascular pathological damage and calcium salt deposition
  We constructed an animal model of vascular calcification (VC), and HE staining analysis was performed to investigate the effect of CUR on calcium salt-induced vascular calcification. Compared to the NC group, HE staining showed intimal hyperplasia, structural disorder, and significant calcium salt deposition in the vessel wall in the VC group. However, the CUR group showed a more intact vessel wall structure and less calcium salt deposition compared with the AS group. Histologic pathology analysis indicated that CUR promoted the structural integrity of the vessel wall and inhibited calcium salt deposition (Fig. 2A).Figure 2The anti-calcification effects of CUR in the rat model of VC. (A) H&E staining images of the common carotid artery sections. (B) Von kossa staining images of the common carotid artery sections. The right images were magnified. The scale bars are 100 μm.

  Von Kossa staining was used to determine the calcium salt deposition in the vessel wall. Compared to the NC group, the staining in the VC group showed significant perivascular calcium salt deposition, indicating more calcium salt deposition (Fig. 2B). After administration of CUR, the vessel wall maintained its structural integrity with less darkened areas, which indicated the reduced calcium salt deposition. The amount of calcium salts was examined. The CUR group attenuated the increased calcium salt content compared to the VC group. These results suggested that CUR effectively inhibited vascular calcification and could reduce calcium salt deposition.


### The targets of CUR and AS
  To obtain the target gene of the effect of CUR on VC, we analyzed network pharmacology. The CAS number of CUR (458-3-7-7) and the molecular formula (C21H20O6) were obtained from the TCMSP online database. Subsequently, the C21H20O6 was searched in the PubChem database and 97 drug targets were screened and normalized using the UNIPORT database. To identify the atherosclerosis-related targets, we searched GeneCards and DRUGBANK databases, eventually obtaining 1157 disease-related targets after removing duplicate targets and merging similar elements. A Venn diagram obtained the intersection of targets from CUR and AS. 25 disease-related targets were performed (Fig. 3A).Figure 3Network pharmacology analysis of CUR-AS targets. (A) Venn map of the 29 common target genes. (B) BP enrichment analysis of the common target genes. (C) CC enrichment analysis of the common target genes. (D) MF enrichment analysis of the common target genes. The X-axis represents gene ratio and the color indicates the P value. (E) KEGG enrichment analysis of the common target genes.


### GO and KEGG enrichment analysis of CUR-AS targets
  GO and KEGG pathway enrichment analysis was performed based on the METOSCAPE database, and the thresholds were set as P < 0.05. Three types of GO functional enrichment analysis obtained 1284 terms. Biological process (BP), molecular function (MF), and cellular component (CC) had 1126, 130, and 28 terms, respectively. Arranged in ascending order of P value, the top 10 items in each group are presented with the GO analysis histogram (Fig. 3B–D). BP categories showed enrichment in response to endogenous stimulus (GO:0009719), defense response (GO:0006952), and inflammatory response (GO:0006954). Analysis of MF categories included that enzyme binding (GO:0019899), protein domain specific binding (GO:0019904), and DNA binding transcription factor binding (GO:0140297) were enriched. The enriched CC categories showed a perinuclear region of cytoplasm (GO:0048471), anchoring junction (GO:0070161), and membrane microdomain (GO:0098857). KEGG pathway enriched 66 pathways. The top 10 significantly enriched KEGG pathways were presented (Fig. 3E). KEGG pathway enrichment analysis indicates EGFR tyrosine kinase inhibitor resistance (hsa01521), Toxoplasmosis (hsa05145), and Pathways in cancer (hsa05200). These findings suggested that CUR alleviates AS through different levels and different pathways.


### Network analysis of CUR-AS targets
  The protein–protein interaction analysis was performed and the 25 disease-related targets of CUR and AS were imported into the online STRING database. The analysis of the PPI network obtained 25 nodes and 95 edges with a P value of 1e−16 and a confidence level of 0.4. The network presented in Fig. 4A. The PPI protein interaction network results were induced to Cytoscape software to establish a network model of the active ingredient disease-related target, and the core gene network was constructed by the cytoHubba plugin. The top 10 hub genes with higher degrees of connectivity were STAT3, EGFR, HSP90AA1, PPARG, CXCL8, CDKN2A, JAK1, JAK2, NFE2L2 and RUNX2, were obtained (Fig. 4B). The higher degree and closeness centrality of the top 10 hub genes listed in Supplementary Table 2, and the betweenness and stress centrality was analyzed and listed Supplementary Table 2. The degree and closeness-centrality of the 10 hub genes network were analyzed25,26 and showed in Supplementary Fig. 2. The top 10 hub targets were scored after ranking by the different analysis patterns in the cytoHubba plugin in Supplementary Table 3.Figure 4Network pharmacology analysis of AS-CUR targets. (A) PPI Network of the common targets. (B) The 10 core targets of the common targets, color intensity increases with degree index, color changes from yellow to red. (C) The 12 genes cluster of the Module.

  Furthermore, the MCODE plugin of Cytoscape identified gene cluster modules and obtained one significant gene cluster module. The Module (significant gene cluster) contained 12 nodes and 96 edges with a score of 8.727. The 12 genes were STAT3, EGFR, HSP90AA1, PPARG, CXCL8, CDKN2A, JAK1, JAK2, TLR7, NOS2, NFE2L2, and RUNX2. The property network of the 12 genes was analyzed26 and showed in Fig. 4C.


### CUR inhibited the calcification marker in VSMCs
  The calcification model of VSMCs under calcification fluid was constructed and the calcium salt deposition was observed in VSMCs by Alizarin Red staining. The Alizarin Red staining was enhanced in the VC group compared to the NC group (Fig. 5A). After the administration of CUR intervention, the Alizarin Red staining attenuated in the CUR group compared with the VC group. The Alizarin Red staining decreased significantly in the 20 μmol/L CUR group. These results indicated that the calcium salt content attenuated in VSMCs under CUR treatment (Fig. 5B,C).Figure 5(A–C) Alizarin Red staining of calcification VMSCs. (D, E) The protein levels of calcification biomarkers including BMP2 and RUNX2 in calcification VMSCs. Data are expressed as the mean ± SD. *P < 0.05 versus Con group; #P < 0.05, versus VC group.


### CUR inhibited the calcification marker expression in VSMCs
  Calcification markers can effectively distinguish the calcification tissues from the normal tissues. The expression of the bone morphogenetic protein 2 (BMP2) was examined by Western blot analysis. As shown in Fig. 5D, the expression of BMP2 was significantly upregulated in the VC group compared to the NC group. Compared to the VC group, the BMP2 expression was significantly down-regulated in the CUR group.

  The osteogenic transcription factor RUNX2 is a common transcription factor for cytosolic calcification. The protein expression of RUNX2 was determined by Western blotting analysis. As shown in Fig. 5E, the expression of RUNX2 was significantly upregulated in the VC group compared to the NC group. Compared to the VC group, the RUNX2 expression was significantly down-regulated in the CUR group.


### CUR regulated the target gene expression in calcified VSMCs
  We detected the expression of target genes in calcified VSMCs. EGFR, the epidermal growth factor receptor, is an important cell membrane surface receptor involved in various signaling pathways. The EGFR protein upregulated in the VC group compared to the NC group. The EGFR expression was significantly downregulated in the CUR group compared to the VC group. The results suggested that CUR regulates EGFR and inhibits vascular calcification (Fig. 6A).Figure 6The predicted targets expression of the calcification VMSCs. Representative western blotting images and bar graphs of the relative expressions of EFGR (A) and SATA3 (B) in each group. *P < 0.05 versus Con group; #P < 0.05, versus VC group.

  The signal transducer and activator of transcription 3 (STAT3), an important signaling transcription factor, is involved in multi-pathway signaling. The STAT3 protein upregulated in the VC group compared to the NC group, and the STAT3 expression significantly attenuated in the CUR group compared with the VC group. The results suggested that CUR regulates the transcription factor STAT3 to inhibit vascular calcification (Fig. 6B).


### CUR increased apoptosis protein in calcified VSMCs
  To explore whether CUR attenuated the calcification process by affecting cell apoptosis, we detected the BCL-2 and Bax protein expression levels. The anti-apoptotic BCL-2 could inhibit apoptosis through an intrinsic apoptotic pathway. As shown in Fig. 7A, Western blot analysis showed that the BCL2 expression significantly decreased in the VC group and CUR enhanced the decreased expression in the CUR group. Bax protein is a pro-apoptotic related protein and would induce apoptosis. The BAX protein levels significantly enhanced in the VC group, and CUR increased the enhanced expression in the CUR group (Fig. 7B). These results indicated that CUR increased the apoptosis in the calcification process of VSMCs.Figure 7The protein expression of the calcification VMSCs. The effect of CUR on the apoptosis relative protein BCL2 (A) and Bax (B) expression in each group. The western blot images and bar graphs of the AKT (C) and p65 (D) expressions in each group. *P < 0.05 versus Con group; #P < 0.05, versus VC group.


### CUR regulates the expression of the signaling pathway
  To determine whether CUR regulated the activation of signaling pathways, we evaluated the AKT1 and NF-κB p65 expression by Western blot analysis. As shown in Fig. 7C, the AKT protein expression significantly decreased in the VC group compared with the NC group, and the AKT expression enhanced significantly in the CUR group compared with the VC group. We also evaluated the CUR effect on the NF-κB protein expression. As shown in Fig. 7D, the p65 protein expression significantly decreased in the VC group compared with the NC group, and the p65 protein expression significantly increased in the CUR group compared to the VC group. However, the Erk1/2 protein did not exhibit the change expression (data not shown). These results indicated that CUR could activate the AKT1 and NF-κB signaling pathways, which might be involved in the VC process. We performed the mRNA expression levels of these genes and the analysis results were consistent with the protein expression (Supplementary Fig. 1).


### Molecular docking results
  The 10 hub genes were molecularly docked to CUR and only 6 ligand-receptor docking results were obtained according to the threshold values of − 4.25 kcal/mol. These ID and binding energy of EGFR, CXCL8, TLR7, STAT3, BCL2, and CDKN2A protein docked to CUR were listed in Supplementary Table 4.

  The EGFR protein binds to CUR with the strongest binding energy of − 7.2 kcal/mol. Two amino acid residues, MET793 and GLN791, were bound to CUR (Fig. 8A). The binding pocket region showed that four hydrogen bonds of 3.0 A and 2.7 A were formed by CUR to the active residues of the EGFR protein, indicating that the compound CUR binds strongly to the EGFR protein binding pocket.Figure 8Molecular docking results. The representative 3D docking complex diagrams of CUR and the key targets of EGFR (A), CXCL8 (B), TLR7 (C), STAT3 (D), BCL2 (E), and CDKN2A (F).

  The CXCL8 protein binds to CUR with an energy of − 6.9 kcal/mol, and the amino acid residues are LYS9, GLN6, and ILE8 (Fig. 8B). The distances between CUR and CXCL-8 hydrogen bonds are 3.4 A, 2.8 A, and 2.2 A, respectively. These distances are less than the conventional 3.5 A, which reflects that CUR binds well to CXCL-8.

  The TLR7 protein binds to CUR with an energy of − 6.2 kcal/mol, and the amino acid residues are GLY113, GLN136, and GLN139 (Fig. 8C). The distances between CUR and TLR7 hydrogen bonds are 3.4A, 2.9A and 2.2A, respectively. These results reflected that CUR binds well to TLR7.

  The STAT3 protein binds to CUR with a binding energy of − 6.1 kcal/mol, and the amino acid residues were GLH1033, ASP992, and SER1137. The distances between the CUR and STAT3 hydrogen bonds are 2.6 A, 2.5 A, and 2.0 A, respectively (Fig. 8D). The hydrogen bond formation is a good indication that CUR binds well to protein STAT3 and may be a potential target inhibitor.

  The BCL2 protein binds to CUR with an energy of − 6.0 kcal/mol and the binding amino acid residue is SER14 with a hydrogen bond distance of 2.8 A (Fig. 8E).

  The CDKN2A protein binds to CUR with an energy of − 5.3 kcal/mol and the binding amino acid residues were GLN14 and THR106 with a hydrogen bond distance of 3.3 A and 2.0A, respectively (Fig. 8F). These results showed a good level of binding activity.


## Discussion
  We observed that CUR inhibited the calcium salt deposition in the arterial VC wall and promoted the integrity of the vascular wall in animal experiments. Cellular experiments confirmed that CUR inhibited the upregulation expression of EGFR, STAT3, and RUNX2 in the VC model, and CUR promoted the anti-apoptotic protein BCL2 expression. The network pharmacology analysis displayed that CUR intervention for AS was associated with the inhibition of transcription factors RUNX2, STAT3, and BCL2 expression. These results revealed that CUR may attenuate the pathological process of VC through these gene targets.

  Atherosclerosis (AS) was associated with oxidative stress and chronic inflammatory condition in the artery27,28. Studies have shown that improved endothelial dysfunction by reducing reactive oxygen species (ROS) prevents the development of AS29. CUR has strong antioxidant effects and can successfully scavenge free radicals. H&E staining results in animal models show that CUR promotes the structural integrity of the vessel wall. The results demonstrated that CUR attenuated the vascular pathological damage and regulated the AKT1 and NF-κB p65 expression of the signaling pathway. The evidences suggested that CUR had a protective effect against AS and CUR was associated with the reduced markers of inflammation and the oxidative stress.

  VC is the deposition of calcium in the walls of the arteries24,30. In calcified arteries some key osteogenic regulators have been identified, including osteopontin, matrix metalloproteinases, BMP-2 and the master osteogenic transcription factor, RUNX231. The Von Kossa staining significantly enhanced in the model group compared to the control group, and the black areas insignificant attenuated in the CUR group. The morphological changes suggested that CUR attenuated the calcium salt deposition. The main pathological basis may be the migration of VSMCs in the vessels to the endothelium. This continuous proliferation and transformation of VSMCs transit from a contractile phenotype to an osteogenic phenotype. The transformation of VSMCs into osteoblast-like cells can secrete osteogenic-associated proteins that promote calcium binding to hydroxyapatite, leading to calcium salt deposition in the vessel wall30. The transformed VSMCs upregulated the osteochondral markers RUNX2 and BMP232. RUNX2 promotes bone formation through its effect on osteoblast activity, and the RUNX2 expression increased in AS patients. These results showed that CUR significantly downregulated the protein and mRNA expression of calcification marker RUNX2 and BMP2. This evidence suggests that CUR treatment presented the anti-AS effect in the AS progression.

  Epidermal growth factor receptor (EGFR) plays a crucial role in the pathogenesis of VC. Studies have shown that EGFR activation can promote the differentiation of VSMCs into osteoblast-like cells, which leads to calcium deposition in the arterial walls. The inhibition of EGFR has been shown to reduce and improve VC33,34. Our results showed that CUR significantly down-regulated the mRNA and protein expression of EGFR. The results suggested that targeting EGFR signaling may represent a potential therapeutic approach for the prevention and treatment of VC.

  It has been demonstrated that the activation of STAT3 promotes the differentiation of VSMCs into osteoblast-like cells35. Moreover, the activation of STAT3 has been shown to increase the expression of osteogenic genes, such as RUNX2 and osteopontin, and to inhibit the expression of anti-calcification genes, such as matrix Gla protein and osteoprotegerin32. Our results showed that CUR significantly decreased the STAT3 expression and indicated that the activation of STAT3 attenuated under CUR treatment. Some studies showed that STAT3 inhibitors can block the progression of AS4. Therefore, targeting the STAT3 signaling pathway could be a potential therapeutic approach for the treatment of VC.

  BCL2 and BAX play a critical role in the regulation process of apoptosis and have been implicated in cardiovascular disease. Several studies have shown that BCL-2 expression may be involved in the development of VC36,37. Furthermore, the dysregulation of BAX and BCL-2 expression has been shown to promote osteogenic differentiation and VC progression38,39. The results showed that CUR significantly increased the BCL-2 and BAX expression. The results suggested the upregulation of BAX and BCL2 activation might represent a potential therapeutic target for the prevention of VC by regulating apoptosis.

  AKT1 is a serine/threonine kinase involved in a variety of cellular processes, including cell survival, proliferation, and metabolism. The upregulation of AKT activity could increase VSMC proliferation and osteogenic differentiation39. NFkB-p65 is a protein complex that plays a critical role in the regulation of inflammation and immune responses40. The NF kB-p65 activation increased the expression of inflammatory cytokines, which contributed to the development of VC37. In addition, NFkB-p65 has been shown to regulate the expression of several key proteins involved in VC, including osteopontin and matrix Gla protein. These results showed that CUR significantly inhibited the AKT1 and p65 expression. The results suggested the inhibition of AKT1 and NF kB-p65 activity can attenuate the development of VC, possibly through its regulation of between inflammation and osteogenic differentiation.

  In summary, we concluded that CUR inhibited calcium deposition in the artery wall and promoted structural integrity of the vascular wall. The mechanism is that CUR inhibited the upregulated expression of RUNX2, EGFR, and STAT3. Our results demonstrated the effects of CUR on VC were associated with the regulation progress of anti-inflammation and anti-apoptosis through these targets (Fig. 9).Figure 9The possible mechanism of the anti-VC effects of CUR might be medicated by STAT3 and RUNX2 on the VC process.


## N/A

### Supplementary Information
  Supplementary Information 1.Supplementary Information 2.


## Supplementary Information
  The online version contains supplementary material available at 10.1038/s41598-024-67776-2.