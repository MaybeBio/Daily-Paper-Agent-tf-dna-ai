# Investigation of the mechanism of euphornin against cervical cancer using network pharmacology


## Supplementary Information
  The online version contains supplementary material available at 10.1038/s41598-025-04522-2.


## Introduction
  Cervical cancer (CC) is a clinically common gynecological cancer, with 604,000 new confirmed cases and 342,000 new cases of death reported in 20201. Significant progress has been made in recent years in the prevention of CC in developed countries, primarily due to the effective implementation of HPV vaccination2. However, the morbidity of CC in China has been on the rise over the past three decades. Fortunately, with the gradual implementation of HPV vaccination and two-cancer (breast cancer and CC) screening programs, there is an optimistic future outlook for a significant decrease in both the morbidity and mortality of CC3. Given that conventional anticancer drugs are often associated with numerous toxicities and side effects, including bone marrow4, cardiac5, and intestinal toxicities6, it is urgent to develop new and effective anticancer drugs that have less toxicity and side effects.

  Recently, increasing attention has been given to the active components of traditional Chinese medicine (TCM), driven by their recognized attributes of safety, minimal side effects, as well as multi-target and multi-channel characteristics7,8. Among the active components in Euphorbia helioscopia is the diterpenoid ester, euphornin (Fig. 1), which has emerged as a potential anticancer drug worthy of attention. One study demonstrated that euphornin significantly inhibits HeLa cell proliferation, induces G2/M cell cycle arrest and promotes apoptosis9. The estrogen receptor 1 (ESR1) gene functions as a transcription factor encoding an estrogen receptor, exhibiting multiple enzyme-binding and transcriptional regulatory activities. Importantly, ESR1 is closely related to breast cancer metastasis10,11. Prior investigations have indicated that ESR1 expression is relatively low in CC12 and ESR1 overexpression can significantly inhibit the migration and invasion of CC cells13,14. However, the exact role of ESR1 expression in CC still remains to be elucidated. Network pharmacology has emerged as an increasingly powerful tool for investigating the pharmacological properties and mechanisms of TCM15. In the present study, network pharmacology and in vitro experiments were combinedly adopted to elucidate the potential mechanism through which euphornin could be used in treating CC.

  Fig. 1The chemical structure of euphornin.


## Materials and methods

### Screening of common targets of Euphornin and CC
  To obtain potential targets of CC, we initiated a search in GeneCards (https://www.genecards.org/) (score ≥ 0.8762). Additional databases, including SEA (https://sea.bkslab.org/), PharmMapper database (http://lilab-ecust.cn/pharmmapper/index.html) (score ≥ 0.5377), Super-Pred (https://prediction.charite.de/) (p value ≥ 50%), and SwissTargetPrediction (https://www.sib.swiss/) (top 100 scores), were also used to predict euphornin’s targets. Data were standardized using Uniprot (https://www.uniprot.org/) and GENE modules. A Venn diagram was used to determine euphornin’s core targets in the context of CC. The String database (https://cn.string-db.org/) and the Cytoscape software (v 3.10.0) were used for protein-protein interaction (PPI) network construction. Additionally, a euphornin-target-CC network diagram was constructed. To identify core targets within this constructed network, we calculated the degree score of each target using Cytohubba (v 0.1), ultimately selecting the top 10 targets as the core targets.


### Biological function analysis
  Biological function of the 10 core targets was analyzed through enrichment analysis in both the Gene Ontology (GO) (ftp://ftp.geneontology.org/pub/go/godatabase/archive/latest-lite/) and the Kyoto Encyclopedia of Genes and Genomes (KEGG) (https://www.kegg.jp/kegg/pathway.html) databases (April 3rd, 2023). Hypergeometric distribution model was used to evaluate the probability of target enrichment to a specific term. The enrichment results of the core targets were obtained with P value < 0.01 and visualized using the Cluster Profiler Package (v 4.4.4) on the R platform (v 4.2.3).


### Molecular docking
  The chemical structural formula of euphornin was downloaded from the Zinc website (https://zinc15.docking.org/), and the target protein for docking was obtained from the PDB website (https://www.rcsb.org/). Specifically, the target protein was separated from the original ligand using PyMol (v 2.3.0), with concurrent removal of the water molecules. The ligands and receptors were introduced into AutoDockTools (v 1.5.6). During this process, polar hydrogens were added, and charges were distributed. The original protein ligand was set as the center of the docking box, and the fpocket tool (v 4.2.2) was employed for in-depth analysis. Molecular docking was carried out using AutoDock Vina (v 1.1.2). To further elucidate the interaction mode, the combination with the lowest affinity was visualized using PyMol.


### Cell culture and grouping
  HeLa and SiHa cells (Shanghai Cell Bank of China Academy of Sciences) were cultured in Dulbecco’s modified Eagle medium (DMEM) (Thermo Fisher Scientific, 11960077) containing 10% fetal bovine serum (Thermo Fisher Scientific, 16140089) at 37℃ with 5% CO2. Euphornin (Shanghai Yuanye Bio-Technology Co., Ltd, B29352) was dissolved in 1% dimethyl sulfoxide (Sangon Biotech, A600163). These cells were subjected to treatment with euphornin at concentrations of 50, 100, and 200 mg/L, respectively, with three replicates set in each group. The experiment comprised a total of eight groups: Control-HeLa, 50-HeLa, 100-HeLa, 200-HeLa, Control-SiHa, 50-SiHa, 100-SiHa, and 200-SiHa.


### Cell transfection
  ESR1 and GAPDH quantitative PCR primers (Table 1), as well as the pcDNA3.1 and pcDNA3.1 + ESR1 plasmids, were all purchased from Sangon Biotech (Shanghai) Co., Ltd. Cell transfection was carried out once the monolayer reached 80% confluency. 2 µg of pcDNA3.1 was added to 250 µL of Opti Reduced Serum Medium (Thermo Fisher Scientific, 31985070), and 5 µL of Lipofectamine reagent (Sangon Biotech, E607403) was mixed with 250 µL of Opti medium for 5 min. Subsequently, incubation of the two solutions was performed at room temperature for 25 min. After adding 1.5 mL Opti medium to a 6-well plate, the cells were cultured for 6 ~ 8 h, after which they were cultured in DMEM medium.

  Table 1Primer sequence.GeneSequence 5’-3’ESR1ForwardGAGTATGATCCTACCAGACCCTTCReverseCCTGATCATGGAGGGTCAAATCGAPDHForwardTCAACAGCAACTCCCACTCTTCCAReverseACCCTGTTGCTGTAGCCGTATTCA


### Cell counting Kit-8 (CCK-8) assay
  100 µL of DMEM serum-free medium was used for the pre-culture of the transfected cells in 96-well plates, with three replicates for each group. Following a 6 ~ 8 h incubation, cell adhesion was observed under a microscope. Subsequently, the cells were cultured for 24 h, 48 h, and 72 h, respectively, followed by addition of 10 µL of CCK-8 reagent (Sangon Biotech, E606335). Through detection using the Microplate Reader (ABS Plus, Molecular Devices, USA), the value of optical density at 450 nm (OD450) of each well was obtained.


### Wound healing assay
  Cells were inoculated into a 12-well plate at a density of 2 × 104/mL. Once the cell confluence reached 90%, a straight-line scratch was made on the bottom of the culture dish. Following this, the cells underwent three washes with phosphate-buffered saline (PBS), and were continuously cultured in serum-free medium. After 24 h, the degree of wound healing was observed and photographed under a microscope (Axio Observer. A1, Zeiss, Germany), and the scratch spacing was measured.


### Transwell assay
  The basement membrane was solidified for 1 h in an incubator at 37℃. Subsequently, each chamber was inoculated with 1 × 105 cells. After incubation for 12 ~ 16 h, the cells were treated with 4% paraformaldehyde (Solarbio, P1110) for fixation for 30 min and incubated with 1 mL of 0.1% crystal violet (Solarbio, G1062) for 20 min. Afterward, the cells that failed to pass through the basement membrane were removed, and the chamber was dried. Images were taken, and the cells were counted using Image J software (v 1.8.0).


### Western blot
  After complete cell lysis performed with the cell lysis buffer (Sangon Biotech, C500035), we detected the protein concentration with a BCA protein quantitative kit (Solarbio, PC0020). Protein samples were electrophoresed in 12% SDS-PAGE gel for 2 h, followed by a subsequent transfer to PVDF membranes (Sangon Biotech, F019533). Following this, the membrane was incubated with the primary antibody overnight at 4℃. The following antibodies were purchased from Abcam: anti-MMP-2 (ab92536, 1/5000), anti-MMP-9 (ab76003, 1/5000), anti-Caspase3 (ab184787, 1/2000), anti-MDM2 (ab259265, 1/1000), anti-ESR1 (ab32063, 1/1000), anti-EGFR (ab52894, 1/1000), anti-p53 (phospho S392) (ab33889, 1/2000), anti-p53 antibody (ab32049, 1/1000), anti-Actin (ab179467, 1/5000), and anti-Cleaved Caspase-3 (ab2302, 1/500). Cleaved Caspase-8 (Asp374) (#9496, 1/1000) and Cleaved Caspase-9 (Asp315) (#20750, 1/1000) were antibodies purchased from Cell Signaling Technology, Inc. Goat anti-rabbit secondary antibody (Lianke Bio, GAR007, 1/10000) was used, and incubation was carried out for 1 h at room temperature. The developed bands were visualized using ECL luminescence reagent (Sangon Biotech, C500044) and detected with an imaging system (iBright™ FL1500, Thermo Fisher Scientific, USA). The gray value was quantified using the Quantity One software (v 4.6.2).


### Flow cytometry
  The collected cell samples were washed with cold PBS, centrifuged for 5 min at 1000×g, resuspended in 500 µL of binding buffer, and incubated with 5 µL of Annexin V-FITC (Sangon Biotech, E606336) for 10 min in the dark. The cells were subsequently washed, resuspended in binding buffer, and treated with 10 µL of propidium iodide. Flow cytometry (Becton, Dickinson and Company, USA) was used for detecting the cell apoptosis rate.


### Data analysis
  GraphPad Prism (v 9.2.0) was employed for carrying out statistical analysis. All data were presented as mean ± standard deviation (x̄±S). Statistical comparisons between groups were analyzed using Student’s t-test, while one-way ANOVA followed by Sidak’s multiple comparisons test was applied for multi-group comparisons. P < 0.05 denotes a statistically significant difference.


## Results

### Common target genes of Euphornin and CC
  We identified 1080 CC-related targets and 346 potential euphornin-related targets, and found 53 common targets (Fig. 2A, B). The euphornin-CC target network is displayed in Fig. 2C. EGFR, CASP3, ESR1, STAT3, MDM2, ANXA5, CASP8, HIF1A, PTGS2, and CCNB1 were revealed to be the top 10 core targets (Fig. 2D).

  Fig. 2Target prediction and network analysis. (A) Venn diagram showing the screening of euphornin-CC targets. (B) PPI network of the euphornin-CC targets. (C) Euphornin-CC target network diagram. Green: CC-related targets. Purple: euphornin-related targets. Red: euphornin-CC targets. (D) Mutual mapping of core target networks. Darker colors indicate higher degree scores.


### Biological function analysis of the core target genes
  GO enrichment analysis revealed 54 molecular function-related terms for the 10 core targets (Fig. 3A), which included ubiquitin/ubiquitin-like ligase binding and cysteine endopeptidase activity involved in apoptosis; 523 biological process-related terms (Fig. 3B), such as response to estradiol and metabolism/transcription/regulation of miRNA; and 9 cell component-related terms (Fig. 3C). Through KEGG enrichment analysis, it was shown that the core targets were primarily enriched in 49 pathways (Fig. 3D), such as proteoglycan in cancer, multiple virus infections, the p53 signaling pathway, and the FoxO signaling pathway. Notably, the p53 signaling pathway exhibited the highest enrichment factor.

  Fig. 3Enrichment analysis. (A) The top 15 MF enrichment terms. MF: molecular function. (B) The top 15 BP enrichment terms. BP: biologic process. (C) The top 9 CC enrichment terms. CC: cellular component. (D) The top 15 enriched KEGG pathways.


### Verification of core target proteins and the MDM2-p53 signaling pathway through Western blot
  In comparison with the control group, euphornin decreased the expression of EGFR (Fig. 4A) and MDM2 (Fig. 4B) proteins in HeLa and SiHa cells (P < 0.0001), increased the expression of caspase3, ESR1 (Fig. 4A, P < 0.0001), p-p53, and p53 (Fig. 4B, P < 0.0001) proteins.

  Fig. 4Verification of the target proteins and the MDM2-p53 signaling pathway. (A) Verification of the target proteins through Western blot. (B) Verification of the MDM2-p53 signaling pathway through Western blot. Compared to the control group, d: P < 0.0001.


### Euphornin inhibits the migration and invasion of CC cells
  Euphornin, at different doses, significantly reduced both the invasive cell number and scratch healing rate of HeLa and SiHa cells compared to the control group (Fig. 5, P < 0.0001). After 48 h of intervention with euphornin, the expression of MMP-2 and MMP-9 proteins in both CC cell lines were significantly decreased, although the inhibitory effect of euphornin at 50 mg/L was relatively weak (Fig. 6). Compared to the control group, no significant changes in MMP-2 protein expression were observed in the 50-SiHa and 50-HeLa groups.

  Fig. 5Euphornin inhibits CC cell migration and invasion. (A) Detection of cell migration by wound healing assay. (B) Detection of cell invasion by transwell assay. d: Compared to the control group, P < 0.0001.

  Fig. 6Detection of the relative expression of MMP-2 and MMP-9 proteins by Western blot. (A) Protein schematic diagram of MMP-2 and MMP-9 proteins. (B) Comparison of the relative expression of MMP-2 protein between groups. (C) Comparison of the relative expression of MMP-9 protein between groups. Compared to the control group, a: P < 0.05, b: P < 0.01, c: P < 0.001, d: P < 0.0001.


### Molecular docking
  Among the four core target genes, ESR1’s role in CC is yet to be fully understood. Therefore, we conducted a preliminary investigation into ESR1’s role in CC cells. We performed molecular docking of the ESR1 protein with euphornin. The spatial coordinates of the center of the grid box were x: 17.65, y: 109.04, z: -16.47, with the number of grid points as: x: 52, y: 81, z: 64. Euphornin molecules interacted with the active sites of ESR1 at Gln 214, Gln 238, and Tyr 219 through hydrogen bonds (Fig. 7A). Additionally, ESR1 formed hydrophobic interactions with euphornin at five amino acid sites (Lys 235, Tyr 191, Tyr 184, Arg 211, and Gly 215) (Fig. 7B). These findings demonstrate strong affinity between euphornin and ESR1.

  Fig. 7Molecular docking diagram of euphornin with ESR1. (A) Three-dimensional structure diagram of molecular docking. (B) Euphornin-bound amino acid residues. Affinity= -5.7 kcal·mol-1.


### ESR1 is highly expressed in transformed CC cells
  In comparison with the pcDNA3.1 group, ESR1’s mRNA and protein expression in HeLa and SiHa cells in the pcDNA3.1 + ESR1 group increased significantly (Fig. 8A, B, P < 0.0001).


### Overexpression of ESR1 does not affect the proliferation of CC cells
  No significant difference was revealed in the proliferation of HeLa and SiHa cells between the pcDNA3.1 and pcDNA3.1 + ESR1 groups (Fig. 8C), suggesting that overexpression of ESR1 had no impact on CC cell proliferation.

  Fig. 8CCK-8 detection of the impact of ESR1 overexpression on CC cell proliferation. (A–B) Marked increase in the mRNA and protein expression of ESR1 in transfected CC cells. (C) Proliferation of CC cells expressing ESR1 assessed by CCK-8 assay. d: Compared to the control group, P < 0.0001.


### Overexpression of ESR1 represses the migration and invasion of CC cells
  HeLa and SiHa cells’ scratch healing rate in the pcDNA3.1 + ESR1 group significantly reduced compared to the pcDNA3.1 group (Fig. 9A, P < 0.0001), and the number of invasive cells also significantly decreased (Fig. 9B, P < 0.0001), indicating that ESR1 overexpression represses CC cell migration and invasion.

  Fig. 9Impact of ESR1 overexpression on CC cell migration and invasion. (A) Detection of cell migration by wound healing assay. (B) Detection of cell invasion by transwell assay. d: Compared to the pcDNA3.1 group, P < 0.0001.


### Overexpression of ESR1 induces the apoptosis of CC cells
  HeLa and SiHa cells’ apoptosis rate increased significantly in the pcDNA3.1 + ESR1 group compared to the pcDNA3.1 group (Fig. 10A, P < 0.001), so as the relative expression of cleaved-caspase3, cleaved-caspase8, and cleaved-caspase9 (Fig. 10B, P < 0.001), indicating that overexpression of ESR1 induces CC cell apoptosis.

  Fig. 10Impact of ESR1 overexpression on CC cell apoptosis. (A) Apoptosis rate of CC cells overexpressing ESR1 detected by flow cytometry. (B) The expression levels of apoptosis-related proteins in CC cells overexpressing ESR1 detected by Western blot. Compared to the pcDNA3.1 group, c: P < 0.001, d: P < 0.0001.


### Underexpression of ESR1 promotes the migration and invasion of CC cells treated with 200 mg/L euphornin and inhibits apoptosis
  To investigate whether euphornin can regulate CC cells’ biological behavior of by targeting ESR1, we constructed HeLa cells with low expression of ESR1. Compared to the si-NC group, the mRNA and protein expression levels of ESR1 significantly reduced in the si-ESR1 group (P < 0.0001) (Fig. 11A-B). Compared to the control group, the cell migration and invasion in the euphornin group decreased significantly (Fig. 11C-D, P < 0.0001), but the cell apoptosis rate increased significantly (Fig. 11E, P < 0.001), along with a significant increase in the expression levels of cleaved-caspase3, cleaved-caspase8, and cleaved-caspase9 (Fig. 11F, P < 0.0001). In contrast, compared to the euphornin + si-NC group, the cell migration and invasion in the euphornin + si-ESR1 group increased significantly (P < 0.001), but the cell apoptosis rate decreased significantly (P < 0.001), along with a significant decrease in the expression levels of cleaved-caspase3, cleaved-caspase8, and cleaved-caspase9 (P < 0.01). The above results suggest that euphornin partially inhibits HeLa cell migration and invasion and promotes HeLa cell apoptosis by upregulating ESR1.

  Fig. 11Underexpression of ESR1 inhibits the migration and invasion of HeLa cells treated with 200 mg/L euphornin, and promotes apoptosis. (A–B) Verification of transfection efficiency. (C) Detection of cell migration by wound healing assay. (D) Detection of cell invasion by transwell assay. (E) Detection of HeLa cells’ apoptosis rate by flow cytometry. (F) Detection of the expression of apoptosis-related proteins by Western blot. Compared to the control group, d: P < 0.0001. Compared to the euphornin + si-NC group, e: P < 0.01, f: P < 0.001.


## Discussion
  CC is reported as a prevalent malignant tumor that affects the female. To reduce the mortality of patients with CC, identifying additional potential biomarkers and candidate drugs is of paramount importance16. In the current research, we made investigation into the underlying mechanisms of euphornin in the context of CC by screening potential targets with high binding activity to euphornin through network pharmacology. The subsequent GO enrichment analysis demonstrated that these identified targets have a variety of transcriptional regulatory and enzyme-binding activities, and are enriched in multiple biological processes, including the regulation of fibroblast proliferation and the metabolism/transcription/regulation of miRNA. Furthermore, KEGG enrichment analysis revealed a close relationship between these targets and diverse cancer-related pathways, various virus infection pathways, and apoptosis-related pathways. These targets are also involved in signaling pathways, such as the p53, FoxO, and IL-17 pathways.

  The core targets investigated in this study are closely linked to the development of tumor cells, such as EGFR17, CCNB118, and MDM219. EGFR is abnormally highly expressed in approximately 90% of CC cells, and EGFR expression is closely associated with clinical features20. Downregulation of EGFR has been shown to prolong the cell cycle to the G2/M phase while reducing the G1 phase by inducing apoptosis, thus inhibiting the proliferation of SiHa cells21. As an E3 ubiquitin ligase, MDM2 is highly expressed in multiple human tumors and mediates p53 ubiquitination of proteasome degradation, consequently decreasing p53 levels within cells22. Numerous studies18,23,24 have confirmed the close relationship between regulating the MDM2-p53 signaling pathway and combating CC. Silencing CCNB1 has previously been demonstrated to inhibit the proliferation of cervical squamous cell carcinoma and promote cell cycle arrest and apoptosis17. Li et al. proved9 that euphornin triggers cell cycle arrest by upregulating CDK1Tyr15 protein expression, and induces concentration-dependent cell apoptosis. These results support the predictions of this study. However, the role of euphornin in tumor cell migration and invasion is still unknown. Our in vitro experiments demonstrated that euphornin decreased CC cell migration and invasion, and reduced the expression of MMP-2 and MMP-9 proteins. These findings suggest that euphornin may suppress cancer cell migration and invasion by inhibiting MMP-2/9 activity and reducing extracellular matrix degradation. However, this study did not examine epithelial-mesenchymal transition (EMT) markers (e.g., E-cadherin, N-cadherin, or Snail), leaving it unclear whether the observed anti-metastatic effects are mediated through EMT regulation. Further investigation is needed to elucidate this mechanism. Concurrently, euphornin remarkably decreased the expression of EGFR, increased the expression of ESR1 and caspase3, and regulated the MDM2-p53 signaling pathway. In addition, it was found that these changes caused by euphornin on CC cells were dose-dependent. These findings supported the use of euphornin as a novel strategy to combat CC and elucidated its molecular mechanism for promoting apoptosis.

  Evidence indicates that ESR1 mutations serve as pleiotropic regulators that modulate metastatic processes in breast cancer in a context-dependent manner25. A recent study demonstrated that ESR1 expression, in the presence of estradiol, suppresses malignant behaviors (including tumorigenesis and cellular invasion) of endometrial cancer stem cells26. ESR1 has been previously reported to be linked with CC cell migration and invasion13,14, yet it appears to have no impact on CC cell proliferation27. Research conducted by Li et al. suggested that ESR1 may be related to the apoptosis of CC cells28. Hence, our study further investigated the role of ESR1 on CC cells, demonstrating that overexpression of ESR1 weakens CC cell migration and invasion as well as induces apoptosis, without affecting cell proliferation. Moreover, low expression of ESR1 in euphornin-treated Hela cells led to promoted cell migration and invasion, but inhibited apoptosis. These findings indicate that euphornin may inhibit CC cell migration and invasion by targeting ESR1, but promote apoptosis. However, this conclusion still needs to be validated in vivo.


## Conclusion
  In the current study, we predicted 10 core targets of euphornin on CC and observed favorable binding activity between euphornin and ESR1 through molecular docking analysis. Our in vitro experiments provided evidence that EGFR, ESR1, CASP3, and MDM2 are potential targets of euphornin in the treatment of CC, and the MDM2-p53 signaling pathway is possibly one of its main pro-apoptosis pathways. In addition, our study also proved that overexpression of ESR1 could inhibit CC cell migration and invasion while promoting CC cell apoptosis, supporting ESR1 as a potential target for treating CC. In conclusion, this study reveals and emphasizes the potential targets and molecular mechanisms underlying euphornin’s efficacy in the treatment of CC, and identifies euphornin as a potentially promising candidate drug for the treatment of CC.


## Electronic supplementary material
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2


## Acknowledgements
  None.