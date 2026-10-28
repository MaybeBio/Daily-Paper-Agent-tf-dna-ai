# Hyaluronan-mediated motility receptor regulating the Wnt/β-catenin signaling resulting in hepatocellular carcinoma by inhibiting the phosphorylation activity of GSK-3β


## Background
  Hepatocellular carcinoma (HCC), the most common primary liver cancer, remains a major global health burden due to its aggressive metastatic behavior and poor prognosis. Clarification of the molecular basis underlying metastasis and recurrence is essential for advancing therapeutic development. The present study examines the contribution of hyaluronan-mediated motility receptor (HMMR) to HCC progression and its clinical implications.


## Methods
  Eighty paired HCC tumor and adjacent non-tumor tissues were obtained from patients who underwent radical resection. HMMR expression was evaluated by immunohistochemistry, Western blotting, and quantitative real-time PCR (qPCR). Kaplan–Meier and Cox regression analyses were employed to determine the association of HMMR expression with overall survival (OS) and recurrence-free survival (RFS). Functional assays were performed in Huh7 and Hep3B cells with HMMR knockdown or overexpression, including CCK-8 assays for proliferation, Transwell assays for migration and invasion, and Western blotting/qPCR for assessing epithelial–mesenchymal transition (EMT) markers (E-cadherin, N-cadherin, vimentin) and Wnt/β-catenin signaling components (GSK-3β, β-catenin, cyclin D1, c-myc). A subcutaneous xenograft model in nude mice was established to evaluate the effect of HMMR on tumor growth in vivo. Gene set variation analysis (GSVA) and molecular docking were applied to investigate HMMR-related pathways and potential protein–protein interactions.


## Results
  HMMR expression was markedly elevated in HCC tissues compared with adjacent tissues (p < 0.001) at both mRNA and protein levels. Patients with high HMMR expression exhibited reduced median OS (27.8 vs. 32.3 months, p = 0.012) and RFS (9.6 vs. 12.6 months, p = 0.017). In vitro experiments demonstrated that HMMR silencing suppressed Huh7/Hep3B cell proliferation, migration (p < 0.01), and invasion (p < 0.001), while increasing E-cadherin and GSK-3β expression and reducing N-cadherin, vimentin, β-catenin, cyclin D1, and c-myc. Conversely, HMMR overexpression produced opposite effects. In xenograft models, tumors with HMMR knockdown displayed slower growth. GSVA indicated a positive correlation of HMMR expression with EMT and Wnt/β-catenin signaling, and molecular docking confirmed the binding capacity of HMMR to GSK-3β and β-catenin. Mechanistic analysis showed that HMMR suppressed GSK-3β phosphorylation activity, limiting β-catenin ubiquitination and degradation, thereby activating Wnt/β-catenin signaling and driving EMT.


## Conclusions
  HMMR stabilizes β-catenin by suppressing GSK-3β phosphorylation activity, which reduces β-catenin ubiquitination and degradation. Knocking down HMMR enhances GSK-3β expression and its degradative effect on β-catenin, thereby lowering β-catenin protein levels.


## Supplementary Information
  The online version contains supplementary material available at 10.1186/s40001-025-03372-y.


## Introduction
  Among malignancies, hepatocellular carcinoma (HCC) exhibits one of the highest mortality rates, largely due to late-stage diagnosis [1–3] and the considerable risk of metastasis and recurrence in most patients [4]. Clarifying the molecular determinants of metastatic progression is essential for improving therapeutic strategies and patient outcomes [5]. Multiple genes appear to be involved in this process [6–8]. Hyaluronan-mediated motility receptor (HMMR) has been proposed as a potential contributor. This transmembrane glycoprotein is abundantly expressed on the surface of diverse tumor cells, where it mediates intercellular interactions and promotes dissemination through activation of the epithelial–mesenchymal transition (EMT) [9]. Experimental suppression of HMMR in certain tumor types has been shown to inhibit growth and metastatic potential by attenuating EMT dynamics [10].

  In HCC, the biological role of HMMR remains insufficiently defined, with only sporadic reports suggesting its potential involvement. Retrospective evaluation of TCGA-LIHC data demonstrated markedly higher HMMR mRNA levels in HCC tissues relative to normal liver, and elevated expression was associated with advanced pathological grade and vascular invasion [9]. In colorectal cancer, HMMR acts as a downstream effector of β-catenin/TCF4, where its overexpression enhances Wnt signaling through a positive feedback mechanism, thereby promoting EMT and metastatic dissemination [11]. Whether a comparable regulatory interaction occurs in HCC and how HMMR engages with Wnt pathway components (e.g., GSK-3β, β-catenin) to influence tumor progression remains unresolved. EMT, characterized by the suppression of epithelial adhesion molecules (e.g., E-cadherin) and acquisition of mesenchymal markers (e.g., vimentin, N-cadherin), constitutes a central step in HCC metastasis [12, 13].

  The present study examined alterations in HMMR expression in patient-derived HCC samples and cell lines, evaluated its potential role in metastasis through in vitro migration and invasion assays, and investigated signaling mechanisms involved using both cultured cell models and mouse xenografts.


## Materials and methods

### Tissue samples and data from patients
  Tumor and adjacent non-tumorous liver tissues were collected from 80 consecutive patients with hepatocellular carcinoma who underwent treatment at the Department of Hepatobiliary Surgery, Guangxi Medical University Tumor Hospital, between July 2017 and July 2019. Eligibility required (a) histopathological confirmation of diagnosis, (b) radical resection as the primary therapeutic approach, and (c) absence of concomitant malignancies.

  Clinical and demographic data were retrieved from medical records, while follow-up information was obtained from records or telephone contact through October 2022. Recurrence-free survival was defined as the interval from surgery to either tumor recurrence, death from any cause, or last follow-up. Overall survival was defined as the interval from surgery to death from any cause.

  The Ethics Committee of the Affiliated Cancer Hospital of Guangxi Medical University approved the use of patient samples and data (approval LW2024065). The requirement for written informed consent was waived because consent for the anonymized use of clinical data for research had been provided at the time of treatment.


### Cell culture
  The human hepatocellular carcinoma cell lines Huh7, Hep3B, HepG2, 97H, and LM3 were obtained from the Cell Bank of the Chinese Academy of Sciences. Cells were maintained in Dulbecco’s modified Eagle medium (Gibco, C1199500BT) supplemented with 10% fetal bovine serum (Gibco) and 1% streptomycin, under standard culture conditions of 37 ℃ in a humidified atmosphere containing 5% CO₂.


### Over-and under-expression of HMMR in hepatocellular carcinoma cell lines
  Cell lines were transfected with short interfering RNA targeting HMMR or with a non-targeting negative-control RNA (Shanghai Sangon, Shanghai, China) using Lipofectamine 2000 (Thermo Fisher). In parallel, plasmid PSE6012 expressing human HMMR or the corresponding empty vector was introduced as a control.

  To extend transient manipulation of HMMR expression, stable cell lines were generated through infection with recombinant lentiviruses encoding either a short hairpin RNA against HMMR or a non-targeting sequence (Shanghai Shenggong). Following 72 h of infection, cells were cultured in puromycin at 1.5 μg/mL for 1 week, and stable clones were subsequently maintained in 0.375 μg/mL puromycin.


### Effect of over-and under-expression of HMMR on hepatocellular carcinoma growth in mice
  All procedures were approved by the Animal Experimentation Committee of Guangxi Medical University (approval KY2024482). Male nude mice (6 weeks old, 20.6 ± 1.2 g) were housed under standard conditions in the Laboratory Animal Center of Guangxi Medical University.

  Huh7 cells stably under-or over-expressing HMMR (100 μL, 2 × 106 cells) were subcutaneously injected into the mid-posterior axilla and mid-upper groin. By day 7, palpable tumors the size of mung beans had formed. Tumor growth was monitored twice weekly over 25 days, after which animals were sacrificed and tumors excised. Excised specimens were subjected to immunohistochemistry, western blotting, and real-time PCR to evaluate HMMR expression and associated molecular changes.


### Quantitation of HMMR mRNA in cell lines and tissues
  Cells from cultures, patient tissues, or mouse xenografts were lysed in TRIzol, and total RNA was isolated using a commercial kit (AriaMx, Agilent). Subsequently, 1 μg of RNA was reverse-transcribed into complementary DNA with a commercial kit (Applied Biosystems®, 4375786). Quantification of HMMR mRNA was performed using the SYBRGreen kit (Takara) under the following PCR conditions: 40 amplification cycles comprising denaturation at 95 ℃ for 10 s, annealing at 60 ℃ for 30 s, and extension at 72 ℃ for 30 s. The primers used were:

  HMMR upstream, 5ʹ-GCACCATCTCCAGGTGCTTA-3′;

  HMMR downstream, 5′-AGCTGAAGCAGGCAAGGTAG-3′;

  DLGAP5 upstream, 5′-GGTGGCTCAGGATGTCTTCA-3′;

  DLGAP5 downstream, 5′-CCAAAGTGTCTATTTCGTTCGT-3′;

  c-myc upstream, 5′-GAACGCGCGCCCATTAATAC-3′;

  c-myc downstream, 5′-CTCCACACCGAGAACGCAC

  cyclin D1 upstream, 5′-CTGCGAAGTGGAAACCATCC-3′;

  cyclin D1 downstream, 5′-TGAAGTAGGACACCGAGGGC-3′;

  p-GSK-3β upstream, 5′-AGAATCAGGCCGAACCTTCAA-3′;

  p-GSK-3β downstream, 5′-AATTGCAGGCACTCTATGGAT-3′;

  β-catenin upstream, 5′-GTCTGAGGAGCAGCTTCAGT-3′;

  β-catenin downstream, 5′-AGTAGCCATTGTCCACGCT-3′;

  E-cadherin upstream, 5′-ATGCTGATGCCCCCAATACC-3′;

  E-cadherin downstream, 5′-GCTGCTTGGCCTCAAAATCC-3′;

  Vimentin upstream, 5′-TCCGCACATTCGAGCAAAGA-3′;

  Vimentin downstream, 5′-GCTCCTAGCGGTTTAGGGGA-3′;

  N-cadherin upstream, 5′-AGGCTTCTGGTGAAATCGCA-3′;

  N-cadherin downstream, 5′-AGAGGCTGTCCTTCATGCAC-3′;

  ACTB upstream, 5′-AGTCATTCCAAATATGAGATGCGTT-3′;

  ACTB downstream, 5′-TGCTATCACCTCCCCTGTGT-3′.

  Levels of HMMR mRNA relative to those of discs large homolog-associated protein 5 (DLGAP5) mRNA were determined using the 2−△△Ct method.


### Quantitation of HMMR and key proteins in cell lines and tissues based on western blotting
  Cells, tissues from patients, or mouse-derived xenografts were lysed in TRIzol buffer, and 30 μg of total soluble protein was resolved by 10% SDS-PAGE. Proteins were then transferred onto polyvinylidene difluoride membranes, blocked in TBST with 5% milk for 2 h, washed three times in TBST, and incubated overnight at 4 ℃ with constant agitation in TBST containing specific primary antibodies (Proteintech): HMMR (1:2000,15820-1-AP), E-cadherin (1:1000), N-cadherin (1:1000), vimentin (1:2000), GSK-3β (1:1000), β-catenin (1:2000), cyclin D1 (1:1000), c-myc (1:2000), p-GSK-3β (Try216, 1:15000), p-Ser9 (1:4000), or DLGAP5 (1:5000). After additional washes, membranes were exposed to horseradish peroxidase-conjugated secondary antibodies at room temperature. Antibody binding was visualized by enhanced chemiluminescence (Biosharp, BL523A).


### Quantitation of HMMR in tissues based on immunohistochemistry
  Paraffin-embedded tumor tissues and matched adjacent liver tissues from patients or mouse xenografts were incubated overnight at 55 ℃, sectioned at 4-µm thickness, and dried for 10 min at 95 ℃. After deparaffinization, antigen retrieval, and permeabilization, sections were treated for 10 min at room temperature with an endogenous peroxidase inhibitor, followed by 1 h blocking with goat serum. Slides were then incubated for 1 h at 37 ℃ with anti-HMMR antibody (1:1000), rinsed with phosphate-buffered saline, and subsequently exposed for 1 h to a biotin-conjugated secondary antibody. Signal development was achieved with DAB, followed by hematoxylin counterstaining, dehydration through graded alcohol and xylene, and sealing with neutral resin. Microscopic images were obtained, and HMMR expression was semi-quantified. Staining intensity was scored as 0 (none), 1 (light red), 2 (red), or 3 (dark red). The percentage of positive cells was graded as ≤ 25% (1), 26–50% (2), 51–75% (3), or > 75% (4). The composite score, calculated by multiplying the two values, ranged from 0–12, with 0–4 defined as low expression and 5–12 as high expression. All evaluations were independently performed by two senior pathologists blinded to clinical data, with discrepancies resolved by consensus.


### Viability and proliferation of hepatocellular carcinoma cells in culture
  For cell viability and proliferation assays, hepatocellular carcinoma cells were seeded in triplicate into 96-well plates (100 µL/well) and allowed to adhere overnight. At 0, 24, 48, or 72 h, 10 µL of CCK-8 solution (Solarbio, CA1210) was added to each well, followed by incubation for 1 h. Absorbance at 450 nm was then determined using a microplate reader.


### Migration and invasion by hepatocellular carcinoma cells in culture
  For migration assays, cells were pretreated with 5 μg/mL mitomycin C (Sigma–Aldrich) for 2 h, centrifuged, resuspended in 300 μL serum-free Dulbecco’s modified Eagle medium, and seeded into Transwell chambers (Corning, NY, USA) at a density of 8 × 104 cells per chamber. Each chamber was supplied externally with 800 μL of medium containing 10% serum and incubated for the designated duration.

  Invasion assays followed the same procedure except that chambers were precoated with Matrigel. After 24 h, chambers were collected, rinsed twice with phosphate-buffered saline, gently swabbed, fixed in 4% paraformaldehyde for 15 min, washed twice with double-distilled water, and stained with 0.1% crystal violet for 30 min. The chambers were washed again twice, air-dried, and examined microscopically. Quantification was based on the average number of cells that traversed the membrane in five randomly chosen fields.


### Bioinformatic identification of molecular pathways involving HMMR in hepatocellular carcinoma
  Genes exhibiting at least a twofold difference in expression between hepatocellular carcinoma and normal liver tissue, with expression levels positively or negatively correlated with HMMR, were identified. These genes were subjected to enrichment analysis for Kyoto Encyclopedia of Genes and Genomes (KEGG) pathways as well as biological processes, molecular functions, and cellular components within Gene Ontology (GO). Enrichment was evaluated using the DAVID platform (https://david.ncifcrf.gov).


### Molecular docking
  Protein structures of HMMR, GSK-3β, and β-catenin were obtained from the UniProt database and processed with PyMOL. HMMR was defined as the ligand, while GSK-3β and β-catenin served as receptor proteins for docking performed through the HDOCK Server. Visualization and interpretation of docking complexes were subsequently carried out using PyMOL.


### Statistical analysis
  All statistical evaluations were conducted with SPSS 26.0 (IBM, Armonk, NY, USA), and results with P < 0.05 were deemed statistically significant. The Shapiro–Wilk test was applied to assess the distribution of continuous variables. Normally distributed data were expressed as mean ± standard deviation, whereas non-normally distributed data were presented as median with interquartile range. Comparisons between groups were analyzed using the independent-samples t test for normally distributed variables and the Mann–Whitney U test for non-normally distributed variables. Differences in categorical variables were examined using the Chi-squared test. Patient survival was estimated using the Kaplan–Meier method, with significance assessed by the log-rank test. Variables associated with survival at P < 0.05 in univariate analysis were subsequently incorporated into multivariate Cox regression.


## Results

### HMMR was overexpressed in hepatocellular carcinoma
  HMMR exhibited marked upregulation in hepatocellular carcinoma. Elevated expression was consistently detected across all five hepatocellular carcinoma cell lines at both mRNA and protein levels (Fig. 1A). Analysis of patient-derived samples further confirmed significantly higher HMMR expression in tumor tissues compared with adjacent non-tumor liver, as determined by real-time PCR of extracted RNA (Fig. 1B). Immunohistochemistry demonstrated a comparable pattern of overexpression in tumor specimens (Fig. 1C, Table 1), and western blotting revealed a mean tumor-to-normal intensity ratio of 1.62 ± 0.29 (t = 8.33, P < 0.001; 15 patients), indicating consistent elevation of HMMR in malignant tissue.Fig. 1Expression of HMMR in hepatocellular carcinoma and adjacent liver tissues. A HMMR exhibited strong expression in LM3, Hep3B, and Huh7 hepatocellular carcinoma cell lines. B Tumor biopsies from patients demonstrated markedly elevated HMMR RNA levels compared with adjacent non-tumorous liver tissue. C Immunohistochemistry confirmed significant overexpression of HMMR in carcinoma tissuesTable 1Semi-quantitation of HMMR in hepatocellular carcinoma and adjacent normal liver tissue based on immunohistochemistryType of tissueLow expression scoresHigh expression scoresTotal0–22–45–89–12Tumor187223380Normal51243280Total69312535160


### Association of HMMR expression with disease characteristics of patients and their survival
  Stratification of patients based on tumor HMMR expression revealed significant differences in several clinicopathological parameters, including sex, age, Barcelona Clinic Liver Cancer (BCLC) stage, and the presence of microvascular invasion or portal vein tumor thrombus (Table 2).Table 2Univariate and multivariate Cox regression to identify factors associated with overall survival of patients with hepatocellular carcinoma at our hospitalCharacteristicsUnivariate analysisMultivariate analysisHazard ratio (95%CI)p-valueHazard ratio (95%CI)p-valueLow or high expression of HMMR0.139 (0.039–0.492)0.002*3.725 (1.334–6.863)0.227Age, year1.566 (0.829–2.957)0.166Sex1.727 (0.751–3.971)0.198BCLC stage5.579 (2.819–11.040)0.000*4.027 (1.903–8.524)0.000*Portal vein tumor thrombus32.449 (5.470–192.492)0.000*2.819 (0.235–33.794)0.413Child–Pugh classification1.747 (0.526–5.802)0.363Number of tumors1.258 (0.657–2.408)0.488Tumor size, cm1.282 (0.678–2.423)0.445Tumor differentiation grade1.200 (0.638–2.257)0.572Liver cirrhosis0.920 (0.481–1.757)0.800Intact envelope1.482 (0.788–2.785)0.222p53 expression1.210 (0.640–2.286)0.557Ki-67 expression0.876 (0.443–1.735)0.705Lymph node metastasis25.673 (5.257–125.377)0.000*2.578 (0.325–20.462)0.370Early recurrence1.435 (0.726–2.836)0.299Microvascular invasion1.682 (0.875–3.232)0.119Total bilirubin0.989 (0.971–1.006)0.203Alanine aminotransferase0.996 (0.988–1.004)0.296Aspartate aminotransferase0.995 (0.985–1.006)0.359Albumin1.069 (0.967–1.182)0.194Prothrombin time0.908 (0.720–1.145)0.414Alpha-fetoprotein0.754 (0.404–1.406)0.374Chronic infection with hepatitis B virus0.835 (0.236–2.956)0.780Intraoperative blood loss, ml1.000 (0.999–1.000)0.766Type of resection0.576 (0.278–1.193)0.138Family history of HCC1.267 (0.553–2.905)0.576Liver capsule invasion1.865 (0.926–3.753)0.081BCLC Barcelona Clinic Liver Cancer, HCC hepatocellular carcinoma*Statistically significant p values are given in bold, p < 0.05

  Transcriptomic data from TCGA indicated widespread expression of HMMR across multiple tissues such as brain, lung, pancreas, liver, gastrointestinal tract, and breast, with marked upregulation in malignancies of these organs, including hepatocellular carcinoma, acute myeloid leukemia, and testicular germ cell tumors (Figure S1A, S1B). Within the hepatocellular carcinoma cohort, HMMR mRNA abundance correlated positively with pathological grade and was elevated in tumors with lymph node metastasis or p53 mutation compared with their counterparts lacking these features, while expression was consistently lower in non-tumor liver tissue (Fig. 2A–E).Fig. 2HMMR expression across tumor subtypes based on TCGA analysis. A Evaluation by clinical stage revealed progressive elevation of HMMR mRNA from stage 1 to stage 3, followed by a decline at stage 4. B Pathological grading analysis demonstrated that higher grades corresponded with increased HMMR mRNA expression. Among histological subtypes, fibrolamellar hepatocellular carcinoma displayed the highest expression, followed by conventional HCC. C Ethnicity-based analysis indicated elevated HMMR mRNA levels relative to healthy populations, with the highest values observed in African Americans, followed by Caucasians and Asians. D Patients with lymph node metastasis showed higher HMMR expression compared with lymph node–negative cases. E Tumors harboring TP53 mutations also exhibited increased HMMR mRNA expression

  In the present patient cohort, median overall survival was significantly reduced in cases with high HMMR expression relative to those with low expression (27.8 vs. 32.3 months, P = 0.012; Fig. 3A), with a parallel pattern observed for median recurrence-free survival (9.6 vs. 12.6 months, P = 0.017; Fig. 3B). Among the clinicodemographic variables associated with overall survival in univariate analysis, only BCLC stage retained independent prognostic value (Table 2). Analysis of the larger TCGA cohort confirmed that tumors with lower HMMR expression were linked to significantly longer overall survival, consistent with the findings in the current patient set (Fig. 3C–D).Fig. 3Prognostic relevance of HMMR expression in hepatocellular carcinoma. A Patients with low HMMR expression exhibited longer overall survival (OS) compared with those with high expression. B Low HMMR expression was also associated with extended recurrence-free survival (RFS). C, D Broader cohort analysis from the Cancer Genome Atlas confirmed that reduced HMMR mRNA levels correlated with significantly improved OS and RFS


### HMMR promoted proliferation, invasion and migration of hepatocellular carcinoma cells in culture
  Suppression of HMMR by short hairpin RNA markedly attenuated the proliferative capacity of Huh7 and Hep3B cells, whereas HMMR overexpression produced the opposite response (Fig. 4A). Comparable effects were observed in Transwell assays assessing migratory and invasive behavior (Fig. 4C–F).Fig. 4Effects of HMMR modulation on proliferation, migration, and invasion of Huh7 and Hep3B cells. A Suppression of HMMR by short hairpin RNA markedly reduced proliferation of Huh7 and Hep3B hepatocellular carcinoma cell lines. B Growth of Huh7 xenografts in nude mice was significantly delayed after HMMR knockdown (groups from top to bottom: 1. control; 2. sh-HMMR NC; 3. sh-HMMR; 4. OE-HMMR NC; 5. OE-HMMR). C, D Knockdown of HMMR diminished transwell migration in Huh7 and Hep3B cells. E, F Invasion through transwell chambers was substantially impaired in Huh7 and Hep3B cells following HMMR silencing. G Tumor size and weight of transplanted Huh7 xenografts in nude mice are presented as histograms, demonstrating the inhibitory effect of HMMR suppression


### HMMR promoted growth of hepatocellular carcinoma xenografts in mice
  In Huh7 xenografts, HMMR knockdown substantially delayed tumor expansion, while its overexpression accelerated growth (Fig. 4B, G), aligning with the in vitro observations.


### Molecular pathways involving HMMR in hepatocellular carcinoma
  Analyses of patient specimens, cultured cells, and xenografts indicated that HMMR was involved in promoting proliferation and metastatic behavior of hepatocellular carcinoma cells. To further clarify the underlying mechanisms, bioinformatic interrogation of publicly available genomic datasets was conducted. Transcriptomic comparison of hepatocellular carcinoma cases in the TCGA database revealed a positive correlation between HMMR and tumorigenic genes such as DEPDC1, SGOL1, and BUB1, while an inverse correlation was observed with tumor-suppressive genes including CCL14, FAM167B, and TMEM88 (Fig. 5A).Fig. 5Correlation of HMMR expression with associated genes and signaling pathways in hepatocellular carcinoma tissues analyzed using TCGA data. A Multiple tumor-suppressive genes, including CCL14, FAM167B, and TMEM88, displayed negative correlations with HMMR expression. B Gene set variation analysis revealed positive correlations between HMMR expression and Wnt pathway components AXIN2, GSK-3β, and β-catenin, whereas inverse associations were observed with cyclin D1 and c-myc. C HMMR expression was positively correlated with E-cadherin, N-cadherin, and vimentin, all of which are key participants in epithelial–mesenchymal transition

  Genes co-expressed with HMMR were significantly enriched in GO molecular functions related to protein and ion binding, localized to cellular compartments such as membranes, nuclei, and membrane-bound organelles, and were associated with biological processes involving regulation and metabolism (Figure S2A). Pathway enrichment further demonstrated positive associations with KEGG pathways including cell cycle regulation, DNA replication, and meiosis—frequently dysregulated in tumors [14]—and negative associations with cytochrome P450-dependent xenobiotic metabolism (Figure S2B).

  Gene set variation analysis revealed a strong positive correlation between HMMR expression and the Wnt pathway components AXIN2, GSK-3β, and β-catenin, whereas negative correlations were observed with cyclin D1 and c-myc (Fig. 5B). Additionally, HMMR expression aligned positively with E-cadherin, N-cadherin, and vimentin, which are central mediators of EMT (Fig. 5C).

  Collectively, the data indicate that HMMR promotes hepatocellular carcinoma progression and metastatic dissemination through the enhancement of tumor cell proliferation and EMT.


### HMMR drove Wnt/β-catenin signaling and the EMT in hepatocellular carcinoma cells in culture
  To experimentally substantiate the bioinformatic predictions, HMMR expression was either silenced or enforced in HCC cell lines, and subsequent alterations in Wnt/β-catenin signaling and EMT were examined. In both Huh7 and Hep3B cells, HMMR silencing increased GSK-3β while reducing β-catenin, cyclin D1, and c-myc at both the mRNA (Fig. 6A, B) and protein levels (Fig. 6C, D). Conversely, HMMR overexpression produced reciprocal changes. These regulatory effects were partially counteracted by reciprocal modulation of DLGAP5, regardless of whether expression was assessed at the mRNA (Fig. 7A, B) or protein level (Fig. 8A, B). The data collectively indicate that HMMR enhances Wnt/β-catenin signaling, in agreement with the bioinformatic analyses. Similar expression patterns were observed in HCC xenografts in mice, where modulation of HMMR yielded the same outcomes as in cultured cells at both the mRNA (Fig. 9A) and protein levels (Fig. 9B).Fig. 6Impact of HMMR silencing on DLGAP5, GSK-3β, β-catenin, cyclin D1, and c-myc in Huh7 and Hep3B cells. A In Huh7 cells, HMMR knockdown increased GSK-3β while reducing β-catenin, cyclin D1, and c-myc at the mRNA level. B In Hep3B cells, HMMR knockdown produced similar changes at the mRNA level. C In Huh7 cells, HMMR knockdown increased GSK-3β and reduced β-catenin, cyclin D1, and c-myc at the protein level. D In Hep3B cells, HMMR knockdown induced comparable alterations at the protein levelFig. 7Impact of HMMR overexpression on DLGAP5, GSK-3β, β-catenin, cyclin D1, and c-myc in Huh7 and Hep3B cells. A In Huh7 cells, HMMR overexpression in combination with DLGAP5 modulation altered mRNA expression, with the knockdown of HMMR elevating GSK-3β and suppressing β-catenin, cyclin D1, and c-myc. B In Hep3B cells, analogous mRNA-level changes were observed under conditions of HMMR knockdown with or without DLGAP5 modulationFig. 8Effects of HMMR overexpression and underexpression on DLGAP5, GSK-3β, β-catenin, cyclin D1, and c-myc in Huh7 and Hep3B cells. A In Huh7 cells, HMMR knockdown combined with DLGAP5 modulation increased GSK-3β and reduced β-catenin, cyclin D1, and c-myc at the protein level. B In Hep3B cells, HMMR knockdown under similar conditions produced consistent changes in protein expressionFig. 9Effects of HMMR overexpression and underexpression on DLGAP5, GSK-3β, β-catenin, cyclin D1 and c-myc in Huh7 cells within nude mouse liver cancer tissues. A In xenograft tumors, HMMR knockdown increased GSK-3β and decreased β-catenin, cyclin D1, and c-myc at the mRNA level. B At the protein level, xenograft tumors with HMMR knockdown exhibited the same regulatory pattern

  In parallel, HMMR silencing in both Huh7 and Hep3B cells elevated E-cadherin while reducing N-cadherin and vimentin expression at both the mRNA (Fig. 10A, B) and protein levels (Fig. 10C, D). Overexpression of HMMR induced the opposite effects. Again, reciprocal modulation of DLGAP5 partially counterbalanced these changes at both transcriptional (Fig. 11A, B) and protein levels (Fig. 11C, D). These results indicate that HMMR promotes EMT in HCC, a process associated with tumor invasion and metastatic progression. Consistent effects were reproduced in HCC xenografts, where modulation of HMMR expression altered EMT marker expression at both the mRNA (Fig. 12A) and protein levels (Fig. 12B).Fig. 10Effects of HMMR modulation on EMT-related markers in Huh7 and Hep3B cells. A In Huh7 cells, HMMR knockdown upregulated E-cadherin while downregulating N-cadherin and vimentin at the mRNA level. B In Hep3B cells, HMMR knockdown produced the same mRNA expression changes. C In Huh7 cells, protein analysis confirmed increased E-cadherin and decreased N-cadherin and Vimentin following HMMR knockdown. D In Hep3B cells, the knockdown of HMMR resulted in comparable protein-level alterationsFig. 11Effects of combined modulation of HMMR and DLGAP5 on EMT-related markers in Huh7 and Hep3B cells. A In Huh7 cells, either overexpression or silencing of DLGAP5, together with HMMR knockdown, led to increased E-cadherin and reduced N-cadherin and vimentin protein levels. B Similar results were observed in Hep3B cells. C Parallel experiments in Huh7 cells confirmed consistent protein-level changes. D In Hep3B cells, modulation of DLGAP5 with concurrent HMMR knockdown again enhanced E-cadherin while reducing N-cadherin and vimentinFig. 12Effects of HMMR overexpression and underexpression on E-cadherin, N-cadherin, and vimentin in Huh7 cells within nude mouse liver cancer tissues. A HMMR knockdown increased E-cadherin and reduced N-cadherin and vimentin mRNA levels. B HMMR knockdown similarly increased E-cadherin and reduced N-cadherin and vimentin protein levels

  Data derived from tumor cell lines and mouse xenografts indicate that HMMR promotes hepatocellular carcinoma cell migration and invasion through activation of Wnt/β-catenin signaling and induction of epithelial–mesenchymal transition.

  Mechanistically, HMMR suppresses β-catenin ubiquitination and subsequent degradation by limiting the phosphorylation capacity of GSK-3β (Figs. 6C, 9B). Under physiological conditions, GSK-3β phosphorylates β-catenin, targeting it for proteasomal degradation; however, HMMR silencing markedly elevates GSK-3β expression (Fig. 6A–B), thereby enhancing β-catenin degradation and reducing its protein abundance.

  In contrast, HMMR overexpression diminishes GSK-3β activity, stabilizes β-catenin protein, and promotes its nuclear accumulation (Figs. 6D, 8B).


### Experimental evidence support
  In vitro analyses revealed that HMMR knockdown significantly decreased β-catenin protein levels without affecting its mRNA expression (Fig. 6A–D), indicating that HMMR regulates β-catenin post-transcriptionally via the protein degradation pathway.

  In vivo, xenograft assays in nude mice demonstrated that HMMR silencing reduced nuclear β-catenin protein, whereas transcriptional activity remained unaltered (Fig. 9A–B).

  Furthermore, protein–protein docking analyses confirmed direct interactions between HMMR and GSK-3β as well as HMMR and β-catenin, with stable docking observed in both cases (Figure S3A, S3B, 13A; Figure S3A, S3C, 13B).Fig. 13Protein docking analysis demonstrating interaction between HMMR and GSK-3β (A), as well as between HMMR and β-catenin (B)


## Discussion
  Current research on HCC encompasses diverse domains addressing molecular mechanisms, etiological factors, diagnostic strategies, therapeutic interventions, and prognosis. Investigations emphasize genetic alterations and signaling pathways that drive tumor initiation, progression, and metastasis [15]. In parallel, the contributions of chronic hepatitis B and C infections, alcohol intake, and non-alcoholic fatty liver disease to HCC pathogenesis have been extensively examined [16–19].

  Diagnostic studies increasingly prioritize the discovery of novel biomarkers and advanced imaging modalities to enable early detection and precise staging. Therapeutic research highlights the development of more effective and individualized approaches, including targeted agents, immunotherapies, and combination regimens [20, 21]. Ongoing clinical trials continue to assess the efficacy of emerging pharmacological strategies in improving survival and quality of life [22].

  Additional efforts focus on dissecting the tumor microenvironment, immune dynamics, and mechanisms of therapeutic resistance in HCC [23, 24], aiming to uncover new molecular targets and refine treatment strategies for this highly aggressive malignancy.

  Our experiments involving hepatocellular carcinoma tissues, cultured cell lines, and xenograft models demonstrated that HMMR expression was elevated in tumors, driving cell proliferation and metastatic potential through activation of Wnt/β-catenin signaling and the consequent EMT. These outcomes indicate potential applications in developing therapeutic strategies aimed at delaying or preventing disease progression, as well as in establishing biomarkers capable of predicting metastatic risk and guiding more intensive patient management.

  Experimental observations, supported by bioinformatic analyses, align with the established role of HMMR in modulating Wnt/β-catenin signaling and EMT [9, 11], a process partly regulated by TCF/LEF transcription factors [19]. Collectively, the study highlights multiple gene expression and signaling pathways that warrant further investigation as potential biomarkers of hepatocellular carcinoma progression and metastasis, or as therapeutic targets for intervention.

  The interplay between DLGAP5 and HMMR represents a significant focus in molecular and cellular research. DLGAP5, a regulator of cell division and cell cycle progression, is frequently overexpressed in diverse malignancies, including hepatocellular carcinoma, lung cancer, breast cancer, and colorectal cancer, where it correlates with aggressive tumor behavior and unfavorable prognosis. HMMR, associated with reverse transcriptase activity, contributes to cell migration and proliferation. In the present study, DLGAP5 served as a reference gene, functioning as a control in the evaluation of HMMR expression.

  High HMMR expression in hepatocellular carcinoma correlated with reduced overall and recurrence-free survival, indicating its potential as a prognostic biomarker. Further investigations are required to clarify the signaling mechanisms linking HMMR to patient outcomes.

  The Wnt/β-catenin pathway regulates key biological processes, including cell proliferation, differentiation, and stem cell self-renewal [25–27]. Given its role in cell migration and proliferation, HMMR appears closely associated with Wnt/β-catenin signaling [28–30], and previous evidence has suggested that HMMR functions as an upstream target gene within this pathway [31, 32]. Experimental results demonstrated that HMMR overexpression elevated β-catenin levels, suppressed GSK-3β, and markedly enhanced the expression of cyclin D1 and c-myc, whereas HMMR silencing produced opposite effects. Although Gene Set Variation Analysis (GSVA)-based analyses reported a negative correlation between HMMR and cyclin D1 (cell cycle protein D1)/c-myc, direct experimental evidence indicated that HMMR overexpression significantly increased both proteins. This inconsistency may reflect the complex nonlinear and multi-layered regulation between gene expression and cellular function. Collectively, the data confirm that HMMR modulates cell proliferation, migration, and invasion by altering Wnt/β-catenin signaling activity, and the extent of pathway activation may be strongly influenced by HMMR expression levels.

  EMT is characterized by reduced or absent expression of epithelial markers such as E-cadherin and cytokeratin, together with elevated expression of mesenchymal markers including N-cadherin and vimentin. The downregulation of E-cadherin coupled with the upregulation of N-cadherin and vimentin alters the cytoskeletal structure of tumor cells, diminishes adhesive capacity, and enhances their propensity to detach from the primary lesion, thereby enabling invasion and metastatic spread to adjacent tissues [12, 13, 33]. Experimental data demonstrated that HMMR modulated the expression of EMT-associated markers E-cadherin, N-cadherin, and vimentin, thereby driving EMT in hepatocellular carcinoma cells. This regulatory effect appears to involve the Wnt/β-catenin signaling pathway, influencing EMT induction and malignant progression.

  β-catenin likely represents the central mediator of HMMR activity, as supported by the following mechanistic and experimental evidence.


### Core correlation at the mechanistic level

#### Hub role in signaling pathway
  β-catenin functions as a principal effector of the Wnt/β-catenin cascade, with its stability and activity directly influenced by HMMR. Evidence indicates that HMMR suppresses the phosphorylation-dependent degradation of β-catenin by inhibiting GSK-3β, thereby enhancing its nuclear accumulation and transcriptional activation of downstream targets such as Cyclin D1 and c-myc. Through this mechanism, HMMR promotes hepatocellular carcinoma cell proliferation and metastatic progression, establishing this axis as the principal route by which HMMR exerts its oncogenic function.


#### Direct linkage with EMT
  Once translocated to the nucleus, β-catenin engages TCF/LEF transcription factors to induce mesenchymal markers (N-cadherin, vimentin) while repressing epithelial markers (E-cadherin), thereby driving EMT. Experimental observations demonstrate that HMMR overexpression markedly enhances nuclear β-catenin localization together with elevated EMT marker expression, whereas HMMR silencing reverses these effects. These data identify β-catenin as an essential intermediary through which HMMR regulates EMT dynamics.


### Direct support from experimental evidence

#### Validation of molecular interaction
  In vitro assays demonstrated that HMMR silencing in Huh7 and Hep3B cells markedly reduced β-catenin mRNA and protein abundance, whereas HMMR overexpression enhanced β-catenin expression (Fig. 6A–D).

  In vivo, xenografts with HMMR knockdown exhibited diminished nuclear β-catenin and reduced transcription of downstream targets, including Cyclin D1 and c-myc (Fig. 12A–B).


#### Validation by rescue experiments
  Reintroduction of β-catenin following HMMR knockdown partially restored the migratory and invasive capacity of HCC cells, indicating that β-catenin acts as a direct effector of HMMR-mediated regulation (Fig. 9A–B).


### Clinical and prognostic correlations

#### Expression correlation
  In HCC tissues, HMMR levels positively correlated with nuclear β-catenin positivity (Spearman r = 0.32, p < 0.01). Elevated expression of both markers was significantly linked to reduced overall survival (Table 2, Fig. 3).


#### Pathway enrichment analysis
  Gene Set Variation Analysis (GSVA) revealed a strong association between HMMR expression and activation of Wnt signaling pathway genes, including AXIN2, GSK-3β, and β-catenin, reinforcing the central role of β-catenin within the HMMR regulatory axis (Fig. 5B).


## Conclusions
  From the perspectives of mechanistic pathways, experimental validation, and clinical correlation, β-catenin is the core protein through which HMMR mediates HCC metastasis. By regulating the stability and nuclear translocation of β-catenin, HMMR regulates the Wnt signaling pathway and EMT process, thereby driving the malignant phenotype of tumors. Its role cannot be substituted by other markers.


## Limitations of the study
  The experimental design primarily relied on two HCC cell lines, Huh7 and Hep3B. Although additional lines such as HepG2, 97H, and LM3 were obtained, functional validation of HMMR knockdown or overexpression was not extended to them. Genetic heterogeneity among HCC cell lines, including differences in p53 status and differentiation grade, may influence experimental outcomes; for example, Hep3B lacks p53, whereas Huh7 carries p53 mutations. The influence of p53 status on HMMR function was not explored, which may render the mechanistic interpretation incomplete. Furthermore, the investigation confirmed only the tumor-promoting role of HMMR without incorporating interventional approaches, such as the application of HMMR-specific inhibitors or shRNA-based delivery systems. Consequently, the therapeutic potential of HMMR remains unverified, as neither the efficacy nor the safety of HMMR targeting in normal hepatocytes was evaluated. This omission limits the translational relevance of the current findings and restricts direct clinical extrapolation.


## Supplementary Information
  Supplementary Material 1. Figure S1. Analysis of HMMR expression profiles in different types of tumors based on the TCGA database. Figure S2. Analysis of HMMR expression and its associations with signaling pathways in hepatocellular carcinoma tissues based on the TCGA database. Figure S3. Protein docking verification for HMMR and GSK-3β, as well as HMMR and β-catenin, respectively.