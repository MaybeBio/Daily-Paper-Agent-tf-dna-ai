# Mechanism of Saikosaponin D in regulating ferroptosis in patient-derived lung adenocarcinoma organoids via upregulation of ATF3/CHOP/CHAC1 signaling


## Supplementary Information
  The online version contains supplementary material available at 10.1038/s41598-025-27251-y.


## Introduction
  Non-small-cell lung cancer (NSCLC) represents the primary cause of cancer-related mortality globally, with lung adenocarcinoma (LUAD) being the most common histological subtype, accounting for 40% of cases1. Despite significant advancements in the surgical and pharmacological lung cancer treatments, clinical outcomes often remain suboptimal because of tumor heterogeneity among patients2. Therefore, it is crucial to develop personalized, effective, and low-toxicity treatment strategies for patients with LUAD.

  The research and development of natural products and their derivatives from medicinal plants has been crucial for discovering potential anticancer compounds3 that play a significant role in tumor therapy. Among these, saponins are particularly noteworthy due to their ability to inhibit various cancers both in vitro and in vivo4,5. Increasing evidence suggests that saponins hold tremendous potential in treating a range of human cancers, including gastric, colorectal, liver, breast, and non-small cell lung cancers, by regulating tumor cell proliferation, apoptosis, invasion, metastasis, and autophagy6,7. Our literature review has identified five saponins with the most extensive research and promising effects: astragaloside IV8, ginsenoside Rg19, saikosaponin D (SSD)10, notoginsenoside R111, and hederagenin12. These compounds can induce lung cancer cell death by modulating macrophage polarization and inducing reactive oxygen species(ROS) accumulation, epithelial-mesenchymal transition, and ferroptosis12–15. However, prior research on the antitumor effects of these saponins has mainly concentrated on tumor cell lines or xenograft mouse models, which do not accurately reflect the human response to these drugs. Therefore, it is essential to establish in vitro models that closely mimic human responses to validate antitumor efficacy and advantages.

  Patient-derived tumor organoids (PDOs) retain the biological characteristics of the original tumor tissue16, closely mirroring individual patient drug responses during drug screening17. This preclinical model plays a crucial role in translating basic cancer research findings into personalized treatment options for patients with cancer and is ideal for drug screening. Although recent studies have emphasized the potential of PDOs for evaluating the efficacy of natural compounds from medicinal plants18, research on the potential anticancer activity and mechanisms of saponins in LUAD PDO models is lacking.

  In this study, we aimed to establish PDOs from 10 LUAD tissues. We then evaluated five saponin compounds from FDA-approved medicinal plants using LUAD PDOs to identify the most effective. We aimed to investigate the efficacy and toxicity of the identified saponin in LUAD PDOs using RNA-seq, flow cytometry, ferrous ion assays, RT-qPCR, western blotting, and molecular docking, to establish the potential of saponin-based treatments in LUAD treatment.


## Results

### PDO construction and histopathological characterization
  This study included 10 patients with LUAD, with baseline characteristics recorded for each individual (Table S2). PDOs were successfully constructed for all ten patients to meet the requirements for drug testing. The study design and Consort diagram are shown in Fig. 1A. All the organoids were passaged five times. After three days of culture, noticeable 3D cell spheres were formed, and the organoids significantly increased in size after 5–7 days (Fig. 1B). Primary cultures typically required 10–14 days to form mature PDOs with relatively few organoids initially. The PDOs were passaged approximately every 9–12 days, with increased numbers and robust growth (Fig. 1C).

  The PDOs from different patients exhibited slight morphological variations, mostly presenting as either vesicular or dense spheroid cell clusters of varying sizes with smooth edges (Fig. 1D). H&E staining confirmed these findings, showing PDOs with typical ring-like or solid/dense structures (Fig. 1E).

  We further examined LUAD-81 PDOs and primary tumor tissues using IHC staining for LUAD specific markers (CK7, TTF1, and Ki-67). The results demonstrated strong CK7 and TTF1 expression in both primary tumors and PDOs, whereas Ki-67 was partially stained in both tumors, consistent with the expression patterns of their parent tumors. These results suggest that the PDOs retained the biological characteristics of the primary tumors (Fig. 1E, F).

  Fig. 1Construction and tissue pathological characteristics of organoid of patients with lung adenocarcinoma. (A) Flowchart for PDO isolation from surgical tissue, PDO culture, and drug sensitivity testing. (B) LUAD-81 PDO P0 growth tracking. he ratio: 200 μm. (C) LUAD-81 Primary and passed by the bright field map, scale bar: 200 μm. (D) Three cases of PDO in the patient (have a typical form of lung cancer PDO), the ratio: 100 μm. (E) The representative images of the primary tumor and the PDO (LUAD-81) using H&E and IHC staining. (F) Immunofluorescence (IF) staining of primary tumors and PDO (LUAD-81). PDO, patient-derived organoids.


### Drug screening
  Ten LUAD PDOs were used for drug screening. The LUAD PDOs were cultured in 96-well plates and treated with five different saponins at a concentration of 10 µM, applied in two replicate wells. Four days later, the viability of PDOs was quantified using a CCK-8 assay. The inhibition rate of each drug was determined by comparing the treated PDOs with those treated with solvent (Fig. 2A, B). The five saponins exhibited varied inhibitory effects on different PDOs, with the strongest inhibition observed for LUAD-81, likely due to tumor heterogeneity. Among the five saponins tested, SSD demonstrated the most potent inhibitory effect on the growth of all PDOs. (Fig. 2A, B).

  Fig. 2Organoid-based drug screening. (A) Cell viability obtained by adding five drugs at 10 µM to 10 organoids for 96 h, compared with the control group. (B) Representative images of PDO, with cell viability ratios of 20%, 50%, and 100% relative to lytic agent treatment, scale bar: 500 μm. (Data are presented as mean ± SD, *p < 0.05, **p < 0.01, ***p < 0.001). PDO, patient-derived organoids.


### Assessment of SSD sensitivity
  The PDOs were treated with varying concentrations of SSD (0, 0.18, 0.54, 1.62, 4.86, 14.58, 43.74 µM). Under a microscope, we observed a decrease in organoid size with increasing drug concentrations, and complete disintegration of PDOs at 4.86 µM, indicating a dose-dependent reduction in PDO cluster size (Fig. 3A). We determined the IC50 values of SSD to assess PDO sensitivity, which ranged from 1 to 5.5 µM across the 10 PDOs, with LUAD-77 and LUAD-95 showing significantly higher sensitivity (Fig. 3B, C). Overall, the varied sensitivity and IC50 values for SSD demonstrated its antitumor efficacy and highlighted heterogeneity among patients.

  We compared the sensitivity of PDOs to SSD and cisplatin (DDP), treating them with DDP at concentrations of 0, 0.1, 1, 10, and 100 µM. No disintegration was observed at 10 µM DDP, with IC50 values ranging from 16 to 38 µM (Fig. 3D), indicating higher sensitivity to SSD compared to that for DDP.

  To preliminarily assess the safety of SSD, we extracted and cultured alveolar organoids from the normal lung tissue of one patient and treated them with SSD for 96 h. The IC50 value for SSD in normal lung organoids was higher than that in tumor organoids, indicating the safety of SSD (Fig. 3E, F).

  Fig. 3Response of lung adenocarcinoma PDO and cells to SSD. (A) Bright field images of different concentrations of SSD acting on LUAD-90, scale bar: 200 μm. (B) CCK-8 detection of the viability of organoids after 96 h of SSD treatment of 10 LUAD PDOs with different concentrations. Compared with the control group (n = 3). (C) Dose-response curves of 10 PDOs after 96 h. Each PDO was measured three times each time(n = 3). (D) IC50 of SSD and DDP acting on PDO, respectively (n = 3). (E) Dose-response curves of SSD in normal lung organoids and tumor organoids in the same individual (LUAD-95), where the IC50 in normal lung organoids is 2.4 µM, while the IC50 in tumor organoids is 1.0 µM (n = 3). (F) Bright field images of SSD acting on normal lung organoids and lung cancer PDOs, scale bar: 100 μm. (Data are presented as mean ± SD, *p < 0.05, **p < 0.01, ***p < 0.001). PDO, patient-derived organoids; SSD, saikosaponin D.


### Inhibitory mechanism of SSD transcriptional changes in SSD-treated PDOs
  To investigate the mechanism of SSD-induced PDO death, we conducted a transcriptomic analysis of three PDOs treated with appropriate concentrations of SSD Genes with |log2FC| ≥ 0.585 and P < 0.05 were considered differentially expressed genes (DEGs). Analysis revealed 318 upregulated and 147 downregulated genes. (Fig. 4A). GO analyses were performed to identify major functions and pathways associated with DEGs. Using |log2FC| ≥ 1, we listed the top 10 pathways that may respond to drug action in LUAD progression. Glutathione (GSH) metabolism was the most enriched in the GO analysis (Fig. 4B). Among the top 20 GO terms, five were associated with ferroptosis, including GSH metabolism, iron-ion homeostasis, and ER stress (Fig. 4C). Because GSH metabolism regulates ferroptosis19, we hypothesized that SSD-induced organoid death might involve ferroptosis.

  We retrieved ferroptosis-related genes from the FerrDb database (http://www.zhounan.org/ferrdb) and intersected them with the DEGs to identify 12 common genes (Fig. 4D, E): CHAC1, SLC7A11, FADS2, JUN, CREB5, ALOXE3, ATF3, ASNS, DDIT3, SLC7A5, TRIB3, and CXCL2. GO and KEGG enrichment analyses of these 12 genes revealed that CHOP-ATF3 was the pathway with the highest Rich factor in GO enrichment20,21 (Fig. 4F). Recent studies have suggested that the ATF3-CHOP pathway induces an unfolded protein response and ER stress22, leading to ferroptosis. ATF3 upregulation is a potential pharmacodynamic marker of ferroptosis23. Therefore, we speculate that SSD-induced cancer cell death is related to the dysregulation of GSH metabolism and ER stress-induced ferroptosis.

  The DEG CHAC1 is induced by ER stress and acts as a positive regulator of ferroptosis. It degrades GSH, leading to ferroptosis and is regulated by ATF3, which plays a role in ER stress and ferroptosis24. Based on this, we hypothesized that SSD induces ferroptosis through upregulation of the ATF3/CHOP/CHAC1 axis, causing ER stress.

  Fig. 4Transcriptional changes in organoids. (A) DEG volcano plot. (B) GO bubble plot of drug-treated group VS control group, |log2FC| ≥ 1. (C) GO bar chart of drug-treated group VS control group, |log2FC| ≥ 1. (D) Venn diagram of DEGs and ferroptosis-related genes in FerrDb. (E) Heat map expression of ferroptosis related genes. (F) GO bubble plot of ferroptosis-related genes. DEG, differentially expressed genes; GO, gene ontology.


### SSD promotes ferroptosis in cells
  To assess the impact of various SSD concentrations on the proliferation of lung adenocarcinoma A549 cells, we treated the cells with 0, 0.18, 0.54, 1.62, 4.86, 14.58, and 43.74 µM SSD and measured cell viability with CCK-8 after 24 h. The results indicated that SSD inhibited A549 cell proliferation in a dose-dependent manner relative to that in the control group (Fig. 5A).

  The wound healing assay showed that SSD treatment significantly inhibited cell migration over time compared to the control (0 µM SSD). After 48 h, the inhibition rate.

  of the SSD treatment groups (1µM, 2µM) decreased by 5% and 12% respectively compared with the control group. After 72 h, the migration rates decreased by 16% and 25% respectively (Fig. 5B, C). These results suggested that SSD inhibited the proliferation and migration of A549 cells.

  We measured ROS and ferrous iron levels to determine whether ferroptosis is involved in SSD-induced A549 cell death. Using DCFH-DA probes and flow cytometry, we quantified and compared fluorescence and found elevated ROS production in the treated cells (Fig. 5D, E). Additionally, we measured ferrous iron levels, which revealed a significant increase in the SSD-treated group (Fig. 5F). These results suggest that SSD induces ferroptosis in A549 cells, corroborating the sequencing results.

  Fig. 5SSD induces ferroptosis in A549 cells. (A) Cell viability of A549 cells treated with SSD. Compared with the control group (n = 3). (B) Scratch experiment of SSD-treated A549 cells, scale bar: 200 μm (n = 3). (C) Measurement statistics chart of the A549 cell scratch experiment. Data were tested using two-way ANOVA (n = 3). (D) Intracellular ROS levels evaluated using flow cytometry (n = 3). (E) Quantified intracellular ROS levels using flow cytometry and calculated significance (n = 3). (F) Ferrous ion content of A549 cells in the experimental and control groups (n = 3); (Data are presented as mean ± SD, *p < 0.05, **p < 0.01, ***p < 0.001). ROS, reactive oxygen species.


### SSD induced ferroptosis in cells by negative regulation of glutathione induced by ER stress
  Sequencing and analysis suggested that glutathione metabolism is linked to ferroptosis. GSH depletion and loss of GPX4 activity are the primary causes of ferroptosis related to glutathione metabolism25. We measured GPX4 expression in SSD-treated PDOs. Western blot analysis revealed decreased GPX4 protein levels in treated PDOs compared to the controls (Fig. 6A, B). This result was confirmed in A549 cells, which showed reduced GPX4 levels after SSD treatment (Fig. 6A, B).

  Molecular docking results showed that SSD could bind to the ATF3 protein domain with a docking energy of -6.0009 kcal/mol, indicating strong binding affinity (Fig. 6C). To validate the binding interaction between SSD and ATF3, we used SSD-treated organoids to perform a Drug Affinity Response Target Stability (DARTS) assay. The DARTS results demonstrated that SSD significantly enhanced the stability of ATF3 during pronase-induced degradation (Fig. 6D). Based on the sequencing results, the ATF3/CHOP/CHAC1 pathway was likely activated by SSD-induced ER stress. We performed RT-qPCR on five PDOs, including the initial three sequenced PDOs and two randomly selected PDOs, to measure mRNA levels following drug treatment, which showed significant differences (Fig. 6E). Western blot analysis of the two LUAD PDOs revealed increased ATF3/CHOP/CHAC1 protein levels, confirming ER stress (Fig. 6F, G). These findings were consistent with those observed in the A549 cells (Fig. 6F, G).

  Fig. 6SSD induces ferroptosis via downregulation of GPX4 through ER stress. (A) Western blot analysis of GPX4 in PDO and A549 cells treated with 2 µM SSD and control groups, β-Actin was used as a loading control. (B) Statistical analysis of GPX4 expression levels from three independent experiments (n = 3). (C) Molecular docking of SSD and ATF3 protein. (D) DARTS-Western blot analysis showed the resistance of ATF to pronase E digestion under the treatment of SSD (10 µM), n = 3. (E) RT-qPCR analysis of mRNA expression levels of PDO-related genes ATF3, CHOP, and CHAC1 treatment with SSD (n = 3). (F,G) Western blot analysis of protein expression (ATF3, CHOP, CHAC1) in A549 cells and PDOs after treatment with 2 µM SSD(n = 3). (H) Mechanism of SSD acting on lung adenocarcinoma. (Data are presented as mean ± SD, *p < 0.05, **p < 0.01, ***p < 0.001). ER, endoplasmic reticulum; PDO, patient-derived organoids; SSD, saikosaponin D. SD, standard deviation.


## Discussion
  The prevalence of NSCLC is a major global medical concern. Natural compounds derived from herbs have shown tremendous potential in drug discovery26,27. We established 10 lung adenocarcinoma organoid models and demonstrated that these organoids retained the histological characteristics of the original tumors. This indicated that our PDOs are suitable for use in preclinical drug screening. To identify new drugs, we screened monomers from five clinically effective traditional Chinese medicines and found that SSD exhibited the strongest inhibitory effect on lung cancer PDOs, warranting further investigation.

  SSD, a major bioactive component of bupleurum, has anti-inflammatory, antitumor, and antioxidant properties28. Its anticancer activity may be due to immunomodulation, inhibition of proliferation, and promotion of tumor cell autophagy and apoptosis. It functions by regulating M2 macrophage polarization, activating autophagy via the CaMKKβ-AMPK-mTOR pathway29, and inducing ROS accumulation while inhibiting the STAT3 and NF-κB pathways30.

  SSD dose-dependently inhibited the growth of lung cancer organoids and A549 cells Sensitivity to SSD varied among PDOs, likely because of tumor heterogeneity. Compared to normal alveolar organoids from patients, SSD showed higher sensitivity to tumor organoids. Further validation using the LUAD cell line, A549, included cell viability and migration assays, which yielded results consistent with those of lung adenocarcinoma PDOs.

  Transcriptomic analyses of gene expression are crucial for studying cellular phenotypes and functions. To investigate SSD’s potential mechanism of SSD, we conducted an RNA-seq analysis of treated PDOs and identified GSH metabolism as a significant pathway. The decreased intracellular GSH activity induces lipid peroxidation and ferroptosis31. The GSH/GPX4 system is crucial for regulating ferroptosis32, and GPX4 reduces toxic lipid hydroperoxides33. GPX4 inactivation leads to lipid peroxidation and increased ROS production, whereas excess Fe2+ from transferrin receptor uptake further enhances ROS production via the Fenton reaction, triggering ferroptosis34. Our study showed that SSD promotes lipid peroxidation, increases ferrous ion concentration and ROS accumulation, and decreases GPX4 protein expression in lung adenocarcinoma PDOs, confirming ferroptosis. We used the FerrDb database to identify genes related to ferroptosis and performed GO analysis. We then determined that ER stress is essential for ferroptosis and ATF3-CHOP is a key complex.

  ATF3-CHOP represents a key branch in the UPR/ER stress pathway. ER stress is a fundamental process for maintaining cellular homeostasis and serves as the central hub driving lipid peroxidation24. ATF3 is a stress response factor that plays a role in oxidative stress, glutathione metabolism, and cancer35,36. As a marker of ER stress, ATF3 upregulates CHOP expression, leading to increased CHAC1 mRNA expression. Our experiments demonstrated elevated mRNA and protein levels of ATF3/CHOP/CHAC1, confirming ER stress. The expression level of CHAC1 is linked to the induction of ER stress37, and its elevated expression is commonly recognized as an early marker of ferroptosis, linked to the degradation of GSH and the onset of ferroptosis. Thus, CHAC1 serves as a pivotal gene that bridges the upstream ATF3-CHOP regulation to the onset of ferroptosis.

  These results suggest that SSD-induced cell ferroptosis in lung adenocarcinoma cells was initiated by CHAC1 activation through ER stress-mediated ATF3 and induced cell death caused by intracellular ROS accumulation and iron overload. The potential mechanism was shown in Fig. 6H.

  However, we acknowledged that there were several limitations in this study. Firstly, due to technical constraints, we were unable to achieve ATF3 knockdown in PDOs to conduct the definitive functional validation. Furthermore, the therapeutic potential of SSD requires further evaluation through preclinical animal studies, such as xenograft models, to assess its in vivo efficacy and potential toxicity. These areas will be the focus of our future research.


## Conclusion
  We first used the lung adenocarcinoma PDO model to demonstrate that SSD is an effective and promising drug. We found that SSD may activate endoplasmic reticulum stress in lung adenocarcinoma PDO to reduce GPX4, causing the accumulation of intracellular ferrous ions and ROS, thereby leading to the occurrence of ferroptosis.


## Materials and methods

### Tumor tissue processing and organoid establishment
  Human samples were collected from LUAD patients who underwent lung tumor resection at Sichuan Cancer Hospital. This study was approved by the Ethics Committees of the Sichuan Cancer Hospital (SCCHEC-02-2022-109) and the Hospital of Chengdu University of Traditional Chinese Medicine (2022KL-051). Written informed consent was obtained from all patients, and all procedures were conducted in accordance with the TRI-Council Policy Statement: Ethical Conduct for Research Involving Humans.

  Sufficiently large surgical samples were divided into two portions: one was fixed in formalin or frozen in liquid nitrogen, and the other was stored in DMEM/F12 (C11330500BT, Thermo, USA). The tissues were first washed and sectioned before being digested with collagenase I (17100017, Gibco, USA) and collagenase IV (17104019, Gibco, USA). The solution was then filtered through a 100 μm filter. After removing the supernatant, the cell pellet was resuspended in Matrigel (356237; Corning, USA) and seeded into a 48-well plate. Lung Adenocarcinoma Organoid culture medium (K2138-LA-100 ml, Lung Adenocarcinoma Organoid kit, bioGenous, China) was added, and the plate was incubated at 37 °C with 5% CO₂.


### Cell cultures and chemical compounds
  The A549 cell line was generously provided by State Key Laboratory of Biotherapy and Cancer Center, Sichuan University and cultured in DMEM (L110KJ, BasalMedia, China), supplemented with 10% fetal bovine serum (HB-FBS-500, HAKATA, China) at 37 °C with 5% CO2. SSD (S5454, Purity:99.50%), Astragaloside IV (S3901, Purity:100.00%), Ginsenoside Rg1 (S3923, Purity:99.18%), Notoginsenoside R1 (S3785, Purity:98.92%), Hederagenin (S3899, Purity:98.00%), Cisplatin (S1166, Purity:99.84%) were purchased from Selleck Chemicals.


### Histology and IHC
  The organoids were fixed in paraformaldehyde. They were subsequently transferred to ethanol for dehydration, and we then embedded, sectioned, dewaxed, and stained the tissues with hematoxylin-eosin. For IHC, Deparaffinization was performed using an environmentally friendly deparaffinization solution, followed by gradient ethanol dehydration. Following blocking, we incubated the sections overnight with primary antibodies against TTF1 (EP1584Y; Abcam, UK), CK7 (ab181598, Abcam, UK), and Ki-67 (HA721115, Huabio, China). Following washes, incubated with secondary antibodies and then stained with DAB. Nuclear staining was performed with hematoxylin, sections were scanned using the Pannoramic MIDI digital pathology scanner, and images were processed using Caseviewer software.


### Immunofluorescence
  The deparaffinized sample sections were dehydrated using an environmentally friendly deparaffinization solution and gradient ethanol concentrations. After blocking, we incubated the sections overnight with primary antibodies against TTF1, CK7, and Ki-67. The following day, incubated with secondary antibodies. Nuclear staining was performed with DAPI, and images were captured using the VS200 scanner (Olympus LS, Tokyo).


### Drug testing on PDOs
  Organoids harvested after 1–2 weeks of culture were dissociated using TrypLE (12605028, Gibco, USA). After the obtained organoids were isolated, we seeded approximately 3,000 cells per well in a 96-well plate. The organoids were cultured for 4–6 days before treatment with diluted compounds with an equivalent dose of DMSO (0219605580; MP, USA) used as a control. Following a 96-hour drug incubation period, cell viability was assessed using the CCK-8 assay.


### CCK-8 assay
  Organoid viability was assessed using the CCK-8 assay kit (HY-K0301; MCE, USA). CCK-8 solution was added and incubated in the dark for 2–3 h. The absorbance was measured at 450 nm using a BioTek plate reader. The IC50 values were calculated using GraphPad Prism 9.5 (GraphPad Software, La Jolla, USA).


### Cell migration assay
  Cells were seeded at a density of 5 × 10^5 cells per well in a 6-well plate. After 24 h of cell attachment, the cells were scratched using a 200 µL sterile pipette tip and then cultured with medium containing 1% FBS and different concentrations of SSD. After 48 h, and 72 h of incubation, images of cell migration were captured using an inverted microscope. The migration area was quantified using ImageJ software.


### RNA extraction and RNA-sequencing analysis
  Three organoid samples were randomly selected from the ten samples for analysis. These samples were divided into a treatment group (with 2 µM drug administered for 24 h) and a control group, with each sample tested in triplicate. Total RNA integrity, quality, and purity were assessed. Bioinformatic analysis and sequencing were performed by LC-Bio Technology Co, Ltd (Hangzhou, China) using the Illumina NovaSeq platform (Illumina, San Diego, USA).


### Gene differential expression and pathway enrichment analysis
  FPKM was used to estimate the relative abundance of all transcripts and the expression levels of mRNA. Differentially expressed mRNAs were identified using the R packages edgeR and DESeq2, with a significance threshold of P < 0.05.


### RT-qPCR
  Total RNA was extracted from organoids using the TRIzol (15596026, Applied Biosystems) reagent. cDNA was synthesized with the cDNA Synthesis Kit (R323-01-AB, Vazyme) following the manufacturer’s protocol. qPCR was performed with SYBR Green PCR Master Mix (A25741, Applied Biosystems). All reactions were repeated in three independent experiments, with each sample undergoing three technical replicates. The primers used in this experiment were listed in Table S1.


### Western blotting
  Organoids in Matrigel were dissociated using TrypLE Express and lysed with RIPA buffer (P0013K; Beyotime, China). Protein concentration was measured using a BCA Protein Assay Kit (CW0014S; CWBIO, China). The denatured proteins were then separated using YoungPAGE gels (M00928, GenScript, China) in MOPS running buffer. Following electrophoresis, the separated proteins were transferred onto PVDF membranes (IPVH00D10; Merck Millipore, USA) using a wet transfer system. Then blocked with 5% BSA for 1 h. Reaction with specific antibodies against the following proteins: β-Actin (A00730, Genscript, China), ATF3 (DF3110, Affinity, USA), GPX4 (ET1706-45, HUABIO, China), CHOP (15204-AF6277, Affinity, USA), and CHAC1 (15207-1-AP, Proteintech, China). Protein detection was performed using ECL reagent (P10300; NCM Biotech, China).


### Ferrous iron assay
  Ferrous iron levels in A549 cells treated with 2 µM SSD were quantified using a ferrous iron colorimetric assay kit (E-BC-K881-M, Elabscience, China). Briefly, cells were lysed and extracted using lysis buffer. Gradient concentrations of iron standards were prepared, and supernatant was treated with an iron probe or control reagent at 37 °C for a certain period of time. We measured absorbance at 593 nm using a BioTek plate reader (Agilent, Santa Clara, USA) and analyzed the data using Gen5 2.0 software.


### Flow cytometry
  ROS levels were assessed using a ROS Assay Kit (S0033S, Beyotime, China). The cells were loaded with DCFH-DA in serum-free medium. After washes, the cells were resuspended in flow cytometry buffer. ROS fluorescence was measured using a flow cytometer (NovoCyte, ACEA, USA) Data were analyzed with FlowJo software.


### Molecular docking
  Molecular docking studies were conducted to explore the binding mode of SSD to ATF3. Obtained the 2D structure of SSD ligand through the PubChem database (http://pubchem.ncbi.nlm.nih.gov/). Protein targets were selected from the Uniprot database (https://www.uniprot.org/). Molecular Operating Environment (MOE) 2019 software was used for energy minimization of the compound and preprocessing of the target protein to identify the active site. The docking simulations were conducted using MOE 2019. Binding affinity was evaluated based on docking energy, and the results were processed using PyMOL 2.6.0 and Discovery Studio 2019.


### Drug affinity responsive target stability (DARTS) experiment
  Organoids in Matrigel were dissociated using TrypLE Express and lysed with NP-40 extraction reagent (Beyotime Biotechnology, Jiangsu, China). Following quantification with the BCA assay, the cell lysates were incubated with 10 µM SSD for 1 h at room temperature. Subsequently, the lysates were digested with pronase E(10165921001, sigma) at enzyme-to-protein ratios of 1:800, 1:400, and 1:200 for 30 min. After the addition of loading buffer, the samples were boiled for 5 min, separated by SDS-PAGE, and finally probed with antibodies specific to the protein of interest.


### Statistical analysis
  All graphs were plotted using GraphPad Prism Software combined with SPSS 26.0 software. The Student’s two-tailed t-test was used to assess the statistical significance between two groups, while one-way or two-way ANOVA was used to assess the statistical significance between multiple groups, and Tukey post hoc test was used for multiple comparisons. Data are presented as mean ± standard deviation (SD). P < 0.05 was considered statistically significant.


## Supplementary Information
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2


## Acknowledgements
  We thank Professor Chong Chen from the State Key Laboratory of Biotherapy and Cancer Center, Sichuan University, for his guidance and assistance in this study.