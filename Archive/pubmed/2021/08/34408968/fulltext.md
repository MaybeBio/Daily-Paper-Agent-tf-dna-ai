# VEGFR-2 kinase domain inhibition as a scaffold for anti-angiogenesis: Validation of the anti-angiogenic effects of carotenoids from Spondias mombin in DMBA model of breast carcinoma in Wistar rats


## Graphical abstract
  Graphical abstract


## Introduction
  Breast cancer is the most prevalent cancer in women [1]. Breast cancer will be diagnosed in 12 % of all women over their lifespan [1]. Mutation in genes that are responsible for cell cycle progression and subsequent loss of regulatory cell functions are responsible for the majority of breast cancer. Angiogenesis, the process of sprouting, cell division, migration, and assembly of endothelial cells (ECs) from pre-existing vessels [2] is a key player in the growth of cancer cells and one of the main causes of death from breast cancer [3]. The role of angiogenesis in tumor growth and metastasis has been established [3]. It plays a central role in embryogenesis and postnatal events including wound healing, the female reproductive cycle, and chronic inflammation [4]. In a normal cell, angiogenesis can be turned off and on but in neoplastic cells, it is perpetually turned on. The vascular endothelial growth factor (VEGF) and its receptor (VEGFR) are responsible for vasculogenesis and angiogenesis [5]. The seven members of VEGF include the VEGF-E, VEGF-A, and its receptors VEGFR-1 and VEGFR-2 control both physiological and pathological conditions. VEGF-C and D and their receptor VEGFR-3 control lymphangiogenesis and embryonic development [5]. The signal transduction cascades are set in motion when VEGF-A binds to VEGFR-1 (Flt-1) and VEGFR-2 (KDR/ Flk-1). VEGFR-2 is mainly responsible for the pro-angiogenic functions of the VEGFRs [5]. The VEGFR-2 carries signal transduction via the phosphatidylinositol-3-kinase/protein kinase B(PI3K/Akt) pathway [6]. VEGF and VEGFR-2 mediated tumorigenesis, metastasis, and angiogenesis are culpable in the high level of mortality associated with breast cancer and other forms of cancer [2]. The angiogenic process can be forestalled by either preventing the VEGF from binding to its receptors [7] and or inhibiting the phosphorylation of the tyrosine kinase domain by small molecules [7]. Small molecule inhibitors of the tyrosine kinase domain disrupt the activation of the receptor tyrosine kinases by preventing ATP binding. Natural compounds have been reported to inhibit the tyrosine kinase domain and also demonstrate antiangiogenic properties [5,8]. With the prevailing patients resistant to chemotherapeutic drugs, it imperative to come up with novel drugs particularly of plant origin considering the critical roles natural products (plants) play in the discovery and development of new pharmaceuticals [9].

  The use of plants for medical purposes is from time immemorial [9]. Modern drug discovery has incorporated the use of medicinal plants due to their perceived non-toxicity to normal cells and tolerability to the drug development pipeline [9. Phytochemicals have been reported to explore different mechanisms in their antitumor properties [10,11]. They selectively destroy proliferating cancerous cells, target anomaly expressed molecular factors, expunge oxidative stress, mediate cell growth factors, obstruct angiogenesis of cancerous tissue, and induce apoptotic cell death [10].

  It is important to adopt computational procedures in hit-to-lead optimization, to reduce cost, time, and cover a large number of drug-like candidates from the pool of plant-derived phytochemicals [12]. Virtual High Throughput Screening (vHTS) is a globally recognized alternative method to High Throughput Screening (HTS), a computational procedure of searching small molecule libraries for molecules that will bind drug targets [13].

  In this study, the anti-angiogenic potentials of six reported anti-cancer plants, Anacardium occidentale, Ocimum gratissimum, Momordica charantia, Spondias mombin, Piper guineese, and Gongronema latifolium were queried by vHTS against VEGFR-2 kinase domain as a scaffold for anti-angiogenesis. Carotenoids from Spondias mombin were the hit phytochemicals, and thus, they were isolated from the leaves of the plant, and their antiangiogenic effects were validated in 7, 12-Dimethylbenz[a]anthracene (DMBA) model of breast carcinoma in female Wistar rats.


## Methodology

### Data collection and preparation of target protein
  Three hundred and twenty-three (323) phytochemicals that were characterized from six reported anti-cancer plants, Anacardium occidentale, Ocimum gratissimum, Momordica charantia, Spondias mombin, Piper guineese, Gongronema latifolium [[14], [15], [16], [17], [18], [19]] were obtained from the literature [[23], [24], [25], [26], [27], [28]]. Phytochemicals were downloaded in the Structure data format (SDF format) from the PubChem repository (https://pubchem.ncbi.nlm.nih.gov) and were converted to the protein data bank (PDB) and protein data bank charged (PDBQT) formats respectively. The crystal structure of the human VEGFR-2 kinase domain with a novel pyrrolopyrimidine inhibitor (crystallographic resolution of 1.55 Aº and PDB ID: 3VHE) [20] was downloaded from the protein data bank (http://www.rcsb.org).

  Command lines;% babel H.sdf H.pdb -h -r -m --gen3D% for i in {1..50}; do ligprep -l H${i}.pdb -o H${i}.pdbqtWhere; H is the name of the file (that contains the phytochemicals).

  1..50 indicate the number of phytochemicals in the file


### Virtual high throughput screening and molecular docking
  Virtual High Throughput Screening (vHTS) was used to screen phytochemicals from Anacardium occidentale, Ocimum gratissimum, Momordica charantia, Spondias mombin Piper guineese, Gongronema latifolium against the ATP-binding pocket of VEGFR-2 (3VHE). The grid coordinates (X= -24.97, Y=-1.14, Z=-10.52) of the co-crystallized compound were used.


### Isolation of lead compounds and LC-ESI-MS analysis
  The lead phytochemicals, carotenoids from Spondias mombin leaves were extracted, isolated, and characterized according to the methods earlier reported by Rodriguez, (2001) [21] and Metibemu et al., 2020 [22].


### Experimental animals
  The G*Power 3 software [23] was used to determine the sample size of 30 female Wistar rats. Wistar rats between 40–50 days old were used for the experiment. The animals were acclimatized for two weeks before the induction of DMBA. The study was carried out with strict adherence to standard protocols of handling experiment animals. The experimental protocols were assessed and endorsed by the Institutional Animal Ethics Committee (IAEC).


### Experimental design
  The Wistar rats were randomized into 6 groups of 5 Wistar rats per group. Group 1 (control), received normal chow and water only. Groups 2–5 were induced intra-peritoneally (IP) with a single dose of 35 mg/kg of DMBA. Groups 3−5 were treated (Per os (p.o): administration through the mouth) for 4 weeks (after confirmation of mammary tumour in all the Wister rats) with 100 mg/kg carotenoid isolates, 200 mg/kg carotenoid isolates, and 100 mg/kg carotenoid isolates +100 mg/kg celecoxib respectively. Group 6 (without tumour induction with DMBA) was also treated with 200 mg/kg carotenoid isolates. The detailed experimental design is shown in Fig. 1.Fig. 1Experimental design to validate the anti-angiogenic effects of carotenoids from Spondias mombin.Fig. 1

  Celecoxib (an FDA approved COX-2 inhibitor) was introduced in group 5 to determine the combinatorial therapeutic effects of targeting both COX-2 and VEGFR-2 receptors in the DMBA model of breast carcinoma in Wistar rats. COX-2 expression is reported to be associated with angiogenesis and lymph node metastasis in human breast cancer [24].

  The doses of carotenoid isolates and DMBA employed for the present study were informed by previous studies [22,25].


### Tumor induction
  The method of Baross et al. (2004) [26] for DMBA induction of mammary tumour was adopted. The animals were administered intraperitoneally with a single dose of 35 mg/kg bodyweight of DMBA dissolved in corn oil. Tumour formation was observed after 24 weeks in all the Wistar rats. The animals were sacrificed and anaesthetized by cervical dislocation.


### Tumour volume
  The method proposed by Geran et al. (1972) [27] was used to determine the tumour volume. The measurement was carried out with the aid of Vernier calipers.


### Reverse transcription-polymerase chain reactions
  Trizol reagent (Gibco) was used to isolate the RNA from the mammary tumour. The RNA-free DNase (Roche, Switzerland) was used to dissolve the RNA for 15 min. at a temperature of 37 °C and purified with the RNeasy kit (Qiagen, Germany). The cDNA was synthesized by incubating 40 μg of the total RNA at 37 °C for 1 h with the reverse transcriptase (GE Healthcare, UK) and also with random hexanucleotides, following the manufacturer’s instructions. The Primers of interest were designed by the Snap gene software. The Primers were ordered from Sigma-Aldrich, USA. Glyceraldehyde-3-phosphate (GAPDH) was used as the control gene. The amplification of the genes was done for 50 cycles, 2 h 20 min with the aid of a thermocycler. The PCR products were run on 1.0 % agarose gels. Visualization was carried with the aid of ethidium bromide (EtBr) staining [28]. The primers of interest are;TARGET GENESFORWARD 5′-3′REVERSE 5′-3′MMP-2GCAGCCTAGCCAGTCGGATTTCCACGTGACAAGCCATGGGGCCCCGAPDHAAGGGCTCATGACCACAGTCGGATGCAGGGATGATGTTCTCHD1GTTCTTCGGGGAACAGAGCGAGTCCTCGTGAGCAATGACCAVEGFTGTGGGCTATGAGCCAAGTGCAACCGTGAGAGCAAGCAACEGFRGATTAATCCCGGAGAGCCAGATGAGCCTGTTACTTGTGCCTVEGFRTGTGGGCTATGAGCCAAGTGCAACCGTGAGAGCAAGCAACHIF-1GTTTACTAAAGGACAAGTCACCTTCTGTTTGTTGAAGGGAG


### Haematoxylin and Eosin for general histoarchitecture of the tumours
  The harvested mammary tumour samples were immersion-fixed in 10 % formo-saline. Water was run through the sample overnight to remove the fixative. After the samples were dehydrated, they were subsequently cleaned in methyl-benzoate. The samples were later immersed in paraffin wax. They were cut (3−5 μm thickness) and stained with hematoxylin and eosin. These were then photo-micrographed for viewing of the resultant histoarchitecture.


### Molecular docking of the phytoconstituents of carotenoid isolates
  Liquid chromatography–mass spectrometry (LC–MS) characterized carotenoid isolates; astaxanthin, beta-carotene-15,15′-epoxide, and 7,7′,8,8′-Tetrahydro-beta, beta-carotene were docked into the ATP pocket of VEGFR-2 (3VHE). Grid coordinates of the co-crystallized compounds X=-24.97, Y=-1.14, Z=-10, was adopted.


### Statistical analysis
  One-way analysis of variance (ANOVA) and Turkey’s multiple range tests in IBM-SPSS version 21.0 and GraphPad Prism version 7.0 were used. Data were denoted as the means ± standard error of the mean (SEM). Significance was set at p < 0.05.


## Results

### Virtual high throughput screening reveals carotenoids as leads
  Table 1, Table 2, Table 3 shows the docking scores of some of the 323 phytochemicals characterized from Anacardium occidentale, Ocimum gratissimum, Momordica charantia, Spondias mombin, Piper guineese, and Gongronema latifolium screened against the ATP catalytic domain of VEGFR-2 with PDB ID of 3VHE. The lead compounds from the virtual screening herein show alpha-carotene, beta-carotene, and beta-cryptoxanthin with a docking score of 11.3 kcal/mol, 11.1 kcal/mol, and 10.7 kcal/mol respectively from Spondias mombin. It is worthy of note that the lead compounds are carotenoids.Table 1Docking scores of Phytochemicals characterized from Anacardium occidentale and Ocimum gratissimum when screened against the catalytic domain of VEGFR-2.Table 1Anacardium occidentaleDocking ScoresOcimum gratissimumDocking scoresS/NPhytochemicalsPhytochemicals1Actinidine−6.21-Heptacosanol−6.62Adipostatatin A−7.31-Octen-3-ol−53Anthranilic acid−5.61-Phenyldecane−6.94Atisine−9.4Alloaromadendrene−7.15Atropine−7.7Alpha-Panasinsen−7.46Berberine−7.6Alpha-Pinene−6.57Bicuculine−8.1Alpha-Terpinene−6.48Brucine−6.9Alpha-Terpineol−6.49Cardanol−7.4Aromadendrene−7.210Carpaine−6.5Azulene−6.8Table 2Docking scores of Phytochemicals characterized from Momordica charantia and Spondias mombin when screened against the catalytic domain of VEGFR-2.Table 2Momordica charantiaDocking scoresSpondias mombinDocking scoresS/NPhytochemicalsPhytochemicals13-beta hyroxy 2 oxomanoyloxide−7.5Alpha-carotene−11.324-beta, 5-alpha-epoxy-4,5-dihydrocaryophyllene-14-ol−7.5Alpha-cubebene−736,7,8 trimethoxycoumarin−6.3Alpha-terpineol−6.24Allicin−4.2Amydalin−6.75Alpha-bulnesene−6.6Berberine−7.76Apha-elemene−6.5Beta-carotene−11.17Alpha-gualene−6.8Beta-caryopyllene−78Aplha-humulene−7.2Beta-cryptoxanthin−10.79Beta-bulnesene−6.7Caffeic acid−6.510Beta-gualene−8Caffeine−5.8Table 3Docking scores of Phytochemicals characterized from Piper guineese and Gongronema latifolium when screened against the catalytic domain of VEGFR2.Table 3Piper guineeseDocking scoreGongronema latifoliumDocking scoreS/NPhytochemicalsPhytochemicals1Allo-Aromadendrene−7.73, 4- Dihyroxyphenylacetic acid−5.92Aloe-emodin−84-(-ethoxymethyl)-phenol−5.63Aloin−8.54-hydroxybenzaldehyde−5.24Alpha-bergamotene−8.3Afrocylamin A−0.55Alpha-phellandrene−6.3Afrocylamin B−3.26Asimicin−9.1Alpha-phellandrene−6.37Azadirachtin1.1Alpha-terpinene−6.48Beta-caryophyllene−7.3Astraodoric acid D−5.99Beta-Pinene−6.2Benzaldehyde−510Borneol−6.5Beta-amyrin−7.2


### The leads inform the isolation of carotenoids from Spondias mombin leaves
  As revealed from the vHTS of phytochemicals from the selected plants (Table 1, Table 2, Table 3). The lead compounds, alpha-carotene, beta-carotene, and beta-cryptoxanthin with docking scores of 11.3 kcal/mol, 11.1 kcal/mol, and 10.7 kcal/mol respectively (Table 1, Table 2, Table 3) are carotenoids from Spondias mombin. Hence the extraction and isolation of carotenoids from the leaves of Spondias mombin.


### LC-ESI-MS revealed three carotenoids from Spondias mombin leaves
  Beta-carotene-15,15′-epoxide, astaxanthin, and 7,7′,8,8′-tetrahydro-β-β-carotene were identified from the LC-ESI-MS analysis of carotenoids isolated from Spondias mombin leaves [Table 4] [22].Table 4Carotenoid fragments obtained with positive ionization mode from Spondias mombin leaves.Table 4Peak no.IdentificationElemental CompositionMolecular ion [M+H+]MS/MS Fragmentation (positive ion mode) M/ZReferencesaAstaxanthinC40H52O4600311,283,166,88[29]bBeta-Carotene-15,15'-epoxideC40H56O552429,307,81[29,30]c7,7',8,8'-Tetrahydro-beta, beta-caroteneC40H60540311, 165, 102[31]


### Tumour formation and tumour volume
  The formation of tumour (Fig. 2) was observed after 24 weeks following a single intraperitoneal induction of 35 mg/kg bodyweight of DMBA. The Wistar rats were thereafter treated for 4 weeks. Fig. 3A and B show the excised mammary tumours and graph of tumor volumes respectively in the DMBA model of breast carcinoma in Wistar rats. In Fig. 3B, there is no significant difference between group 2 and group 3. There is a significant difference between group 2 and group 3. A significant difference also exists between group 2 and group 5.Fig. 2Breast carcinoma in female Wistar rats induced with DMBA.Fig. 2Fig. 3A. The excised mammary tumours. B: Graph of tumor volumes in the DMBA-induced breast carcinoma model of Wistar rats in the different experimental groups. Values are expressed as Mean ± Standard Error of Mean (n = 5/group). Significance was set at p < 0.05. The non-identical alphabets on the bars indicate a significant difference.Fig. 3


### mRNAs expression of angiogenic related genes in the mammary tumours of DMBA-model of breast carcinoma following treatment with carotenoid isolates

#### Relative expression of VEGF mRNA
  VEGF is the principal mediator of angiogenesis in cancer, it is upregulated by oncogene expression, growth factors, and hypoxia. Angiogenesis is essential for neoplastic proliferation and growth [32].

  In Fig. 4A, there was a significant downregulation in the expression of VEGF mRNA in group 3, group 4, group 5, and group 6 when compared with group 1, and group 2.Fig. 4mRNAs expression of angiogenic related genes in the mammary tumours of DMBA-model of breast carcinoma following treatment with carotenoid Isolates A: VEGF mRNA B: VEGR mRNA C. EGFR mRNA D: HIF-1 mRNA. E: CHD1 mRNA F: MMP-2 mRNA. Bars with different alphabets are significantly different at p < 0. 05.Fig. 4


#### Relative expression of VEGFR mRNA
  VEGFR and VEGF are co-expressed in primary breast carcinoma with further upregulation of VEGFR when neoplastic cells become angiogenetic phenotype [33].

  In Fig. 4B, there was a significant downregulation in the expression of VEGFR mRNA in group 3, group 4, group 5, and group 6 when compared with group 2.


#### Relative expression of EGFR mRNA
  EGFR is expressed in malignant and nonmalignant cells; however, it is upregulated in multiple forms of tumors. The expression of EGFR corresponds with poor response to treatment, disease progression, and poor survival [34].

  In Fig. 4C, the expression of EGFR mRNA was significantly downregulated in group 3, group 4, group, and group 6 when compared to group 2. There was a significant downregulation in EGFR mRNA expression in group 3 when compared to group 1.


#### Relative expression of HIF-1 mRNA
  HIF-1 displays principal roles in energy metabolism, apoptosis, angiogenesis, and control homeostatic reaction to hypoxia [35].

  In Fig. 4D, the expression of HIF-1 mRNA was significantly downregulated in group 3, group 4, group 5, and group 6 when compared with group 1.


#### Relative expression of CHD1 mRNA
  E-cadherin (CDH1) is a cell adhesion molecule that organizes pivotal morphogenetic processes regulating neoplastic development. A decreased level of CDH1 is a characteristic of the epithelial–mesenchymal transition, leading to an increase in the metastatic power of malignant cells [36].

  In Fig. 4E, the expression of CDH1 mRNA was significantly upregulated in groups 4 and 5 when compared with groups 1 and 2. The expression of CDH1 mRNA was upregulated in group 3 when compared with group 2, though not statistically significant at p < 0.05. However, the expression of CDH1 was significantly upregulated in groups 3, 4, 5, and 6 when compared with the basal control (group 1).


#### Relative expression of MMP-2 mRNA
  The MMP-2 mRNA directs the translation of Matrix Metallopeptidase 2. They are activated through hydrolysis and cause the degradation of the basement membrane (BM) and attenuating the ability of BMs to hinder tumor cell migration. MMP-2 plays a key role in the degradation of the extracellular matrices and encouraging tumor invasion and metastasis [37].

  In Fig. 4F, MMP-2 mRNA was significantly expressed in group 2 when compared to group 1, the expression of MMP-2 mRNA was significantly downregulated in groups 3, 4, 5, and 6 when compared to group 2. There was a significant upregulation in the expression of MMP-2 mRNA in groups 3, 4, 5, and 6 when compared to group 1.


### Histopathological analysis
  The breast tumours were biopsied and stained with hematoxylin and eosin (H&E) to accentuate various tissue structures; nuclei and cytoplasm. Fig. 5 shows the histopathological sections of the breast tumours.Fig. 5Photomicrograph of a non-malignant mammary lobe in breast tissue marked by black arrows (A), photomicrograph of non-infiltrating and intraductal tumours with central necrosis (marked by black arrow) and consistent with Comedo carcinoma (B), photomicrograph shows nests of malignant glands consistent with invasive ductal carcinoma (marked by arrows; C), intra- and inter-acini pleomorphic and hyperchromatic cells with high nuclear-cytoplasmic ratio (D). Haematoxylin and Eosin (H&E) stained. Magnification: X20 (A, B, and D; from test groups) and X5 (C; from the control group).Fig. 5

  Group 1 (control) had normal mammary lobes with non-malignant acini. Group 2 had spindle-shaped cells and atypical features consistent with sarcomatoid lesions and Comedo carcinoma. Group 3 developed invasive ductal carcinoma while the breast tissues of group 4 had evidence of moderate to extensive necrosis and inflammatory cells. Group 5 had a nest of malignant glands demarcated by a delicate fibrous tissue while group 6 also had non-malignant mammary lobes.


### Molecular docking of carotenoid isolates into the ATP-binding pocket of VEGFR-2
  Inhibitors of the tyrosine kinase domain disrupt the activation of the receptor tyrosine kinase (RTKs) by inhibiting ATP binding [5]. Table 5 shows the docking results of the carotenoid isolates within the ATP binding site. Beta-carotene-15,15′-epoxide, 7,7′,8,8′-tetrahydro-β,β-carotene, and astaxanthin possess binding energies of -10.5 kcal/mol, -10.3 kcal/mol, and -8.2 kcal/mol respectively (Table 5). Fig. 6 shows the crystal structure of the VEGFR-2 kinase domain in complex with the standard drug, axitinib, and carotenoid isolates (Beta-carotene-15,15′-epoxide, 7,7′,8,8′-Tetrahydro-β,β-carotene, and Astaxanthin). Fig. 7 shows the validation of the docking protocols employed in the present study.Table 5Docking score of the carotenoid isolates within the kinase domain of VEGFR-2.Table 5Carotenoid Isolate/Standard drugVEGFR-2Astaxanthin−8.2 kcal/mol7,7′,8,8′-Tetrahydro-β,β-carotene−10.3 kcal/molBeta-Carotene-15,15′-epoxide−10.5 kcal/molAxitinib−9.6 kcal/molFig. 6A (i). VEGFR-2 kinase domain in complex with axitinib (smudge green), axitinib occupies the cleft between the N- and C-lobes of the kinase domain (the ATP binding site). Axitinib binds to the inactive state of the kinase domain with the activation loop in the “closed” conformation and the DFG motif in the “in” conformation. (ii). Interactions of axitinib (blue) within the ATP binding pocket, the blue lines represent hydrogen bonds: B (i). VEGFR-2 kinase domain in complex with 7,7′,8,8′-Tetrahydro-β,β-carotene (orange). 7,7′,8,8′-Tetrahydro-β,β-carotene occupies the cleft between the N- and C-lobes of the kinase domain (the ATP binding site) and binds to the inactive state of the kinase domain with the activation loop in the “closed” conformation and the DFG motif in the “in” conformation. (ii). Interactions of 7,7′,8,8′-Tetrahydro-β,β-carotene (orange) within the ATP binding pocket, the red lines represent hydrophobic interactions: C (i). Crystal structure of the VEGFR-2 kinase domain in complex with astaxanthin (yellow). Astaxanthin occupies the cleft between the N- and C-lobes of the kinase domain (the ATP binding site) and binds to the inactive state of the kinase domain with the activation loop in the “closed” conformation and the DFG motif in the “in” conformation. (ii). Interactions of astaxanthin (yellow) within the ATP binding pocket, the red lines represent hydrophobic interactions: D (i). Crystal structure of the VEGFR-2 kinase domain in complex with beta-Carotene-15,15′-epoxide (blue). Beta-Carotene-15,15′-epoxide occupies the cleft between the N- and C-lobes of the kinase domain (the ATP binding site) and binds to the inactive state of the kinase domain with the activation loop in the “closed” conformation and the DFG motif in the “in” conformation. (ii). Interactions of Beta-Carotene-15,15′-epoxide (gray) within the ATP binding pocket, the red lines represent hydrophobic interactions.Fig. 6Fig. 7The binding mode of the re-docked (red) and the co-crystallized, 1-{2-fluoro-4-[(5-methyl-5H-pyrrolo[3,2-d] pyrimidin-4-yl) oxy] phenyl}-3-[3 (trifluoromethyl)phenyl]urea (pale green) within the ATP binding pocket of VEGFR-2.Fig. 7


## Discussion

### Virtual high throughput screening of phytochemicals from selected plants
  vHTS of 323 phytochemicals from the reported anti-cancer Plants; Anacardium occidentale, Ocimum gratissimum, Momordica charantia, Spondias mombin, Piper guineese, Gongronema latifolium revealed alpha-carotene, beta-carotene, and beta-cryptoxanthin with a docking score of 11.3 kcal/mol, 11.1 kcal/mol, and 10.7 kcal/mol (Table 3) respectively from Spondias mombin as the lead compounds. The lead compounds alpha-carotene, beta-carotene, and beta-cryptoxanthin are carotenoids. It suffices to say that carotenoids generally have been proven to possess anti-carcinogenic activities in several tissues [38,39]. The discovery of novel bioactive compounds with therapeutic benefits as obtained from the Virtual High Throughput Screening (vHTS) procedures adopted herein corroborated the significance of computer-aided drug design in the drug discovery pipeline [40].


### Liquid chromatography-electrospray ionization-mass spectrometry and metabolomics analysis
  The carotenoids isolated from the leaves of Spondias mombin were chromatographically separated into two fractions and afterward identified using Liquid Chromatography-Electrospray ionization-Mass Spectrometry. Compounds annotation was carried out based on the recommendation of the Metabolomics Society by combining information obtained from mass spectra characteristics, literature, and or databases [41]. The chromatogram of the carotenoids and positive ion electrospray ionization Mass Spectrometry fragmentation patterns show the presence of three (3) carotenoids [22]. Carotenoids tend to form stable protonated molecules ([M+H] +) with the positive mode of ionization, hence the analysis of the sample in the positive mode. Peak I was not identified in part due to the lower m/z 121 which is believed to be a non-carotenoid compound. Peak 2 with m/z 600 [M+4 H) + and fragmentation (311,283,166,88) corresponds to astaxanthin [29]. Peak 3 with m/z 552 (M+H) + and fragmentation (429,307,81) corresponds to beta-Carotene-15,15′-epoxide [30]. Lastly, peak 4 with m/z 540 (M+H) + and fragmentation (311, 165, 102) corresponds to 7,7′,8,8′-Tetrahydro-beta, beta-carotene [31].


### Angiogenic-related mRNAs expression profiling
  VEGF is an indispensable moderator of angiogenesis. Angiogenesis is important for neoplastic development and growth. The upregulation of VEGF mRNA commits the neoplastic cells to exponential growth. VEGF is central to tumour vasculature and survival 42]. The expression of VEGF mRNA was significantly downregulated in groups 3, 4, 5, and group 6 when compared with group 2. The significant downregulation of the VEGF mRNA expression by the carotenoid isolates (groups 3–6) depicts the anti-angiogenic properties of carotenoids, this is in agreement with the report of Kuhnen et al. (2009) [43] that carotenoids possess anti-angiogenic properties. The significant downregulation of VEGFR mRNA by the carotenoid isolates in groups 3–6, when compared with group 2 give credence to the inhibition of the Kinase Domain Receptor (KDR) of VEGFR as obtained from the Virtual Screening adopted in the present study.

  Epidermal growth factor receptor (EGFR) is a pivotal factor in neoplastic malignancies, and its activity promotes tumor growth, invasion, and metastasis [44]. The EGFR mRNA is over-expressed in different forms of carcinoma including breast carcinoma [44]. The expression of the EGFR mRNA was significantly downregulated in all the treatment groups (3−5) and group 6 when compared with group 2. The degree of downregulation of the EGFR mRNA was greater in group 3, treated with 100 mg/kg carotenoid isolates when compared with other treatment groups (4, 5, and 6). This further confirms the fact that carotenoids at lower concentrations display greater therapeutic effects. The combination of 100 mg/kg carotenoid isolates +100 mg/kg celecoxib fails to display equivalent or marching therapeutic effects when compared with group 3 treated with 100 mg/kg carotenoid isolates. The downregulation of the expression of VEGFR mRNA and EGFR mRNA by the carotenoid isolates demonstrates the inhibition of the tyrosine kinase receptor as a likely mechanism of the downregulation.

  HIF-1 displays principal roles in energy metabolism, apoptosis, angiogenesis, and control homeostatic reaction to hypoxia [35]. Elevated HIF-1 mRNA expression is associated with poor response to treatment and prognosis [45].

  The expression of HIF-1 mRNA was significantly downregulated in all the treatment groups 3, 4, and 5 when compared with group 2. This shows the carotenoid isolates administered as a treatment in the present study possess anti-metastatic, and anti-proliferating potentials [46] since HIF-1 is known to activate these pathways.

  E-cadherin (CDH1), an adhesion molecule, organizes pivotal morphogenetic processes regulating neoplastic development. A decreased level of CDH1 is a characteristic of neoplasm leading to an increase in the metastatic power of malignant cells [36]. Loss of E-cadherin function or expression is correlated with cancer progression and metastasis. Downregulation of CDH1 mRNA attenuates the firmness of cellular adhesion within a tissue, leading to cellular motility [47]. The expression of CDH1 mRNA was upregulated in the treatment groups 3, 4, and 5 when compared with group 1 and group 2. However, the upregulation of CDH1 mRNA in group 3 was not statistically significant when compared with group 2. It suffices to say that the treatments, carotenoid isolates hinder epithelial–mesenchymal transition (EMT), thereby in a way demonstrating anti-proliferative tendencies.

  The MMP-2 mRNA directs the translation of Matrix Metallopeptidase 2. They are activated through hydrolysis and cause the degradation of the basement membrane and attenuate its ability to hinder tumor cell migration. MMP-2 plays a key role in the degradation of the extracellular matrices and encouraging tumor invasion and metastasis [37]. The expression of MMP-2 mRNA was significantly downregulated in the treatment groups except in group 3 when compared with group 2. This observation further confirms the anti-metastatic, anti-angiogenic, and antiproliferative potentials of the carotenoid isolates.


### Molecular docking of the carotenoid isolates
  In the present study, the phytoconstituents of the carotenoid isolates, astaxanthin, 7,7′,8,8′-tetrahydro-β,β-carotene, and beta-carotene-15,15′-epoxide docked into VEGFR-2 kinase domain, bind between the N- and C- lobes with binding energies of -8.2 kcal/mol, -10.3 kcal/mol, and -10.5 kcal/mol respectively. Astaxanthin, 7,7′,8,8′-tetrahydro-β,β-carotene, and beta-carotene-15,15′-epoxide bound to the inactive VEGFR-2 state. The mode of binding of astaxanthin, 7,7′,8,8′-tetrahydro-β,β-carotene, and beta-carotene-15,15′-epoxide are in tandem with known tyrosine kinase inhibitors, nilotinib, and ponatinib [48]. The binding of astaxanthin, 7,7′,8,8′-tetrahydro-β,β-carotene, and beta-carotene-15,15′-epoxide to the ATP binding site led to the DFG-out conformation. Astaxanthin forms hydrophobic interactions with important residues within the ATP binding site (tyr-966, val-936, phe-935, pro-937, tyr-1130, arg-932, and ala-932), 7,7′,8,8′-tetrahydro-β,β-carotene on the other hand also forms hydrophobic interactions with arg-932, tyr-1130, ser-1101, leu-1101, and ala-1103. Lastly, beta-carotene-15,15′-epoxide forms hydrophobic interactions with leu-928, arg-929, lys-921, arg-932, phe-935, leu-1000, leu 1002, leu-1005, ile-1006, cys-1007, ile-1098, phe-1099, leu-1101, and tyr-1130 and also forms hydrogen bond interaction with lys-931, and arg-932. The lowest binding energy of beta-carotene-15,15′-epoxide, -10.5 kcal/mol, when compared with astaxanthin and 7,7′,8,8′-tetrahydro-β,β-carotene is likely due to its extensive hydrophobic interactions coupled with the hydrogen bond interactions with the ATP binding domain. It is worthy of note that the binding of beta-carotene-15,15′-epoxide span through the ATP binding domain, thereby making interactions with key residues that are needed for competitive inhibition of the kinase domain. The anti-angiogenic potential demonstrated in the present study is likely due to beta-Carotene-15,15′-epoxide because of its inhibition of the VEGFR-2 kinase domain. This observation confirms the report of (Guruvayoorappan and Kuttan (2007) [49] that β-carotene inhibits angiogenesis.

  The re-docking of 1-{2-fluoro-4-[(5-methyl-5H-pyrrolo[3,2-d]pyrimidin-4-yl)oxy]phenyl}-3-[3-(trifluoromethyl)phenyl]urea back into the ATP binding pocket of the VEGFR-2 (3VHE) gave RMSD value of 0.071 Å (Fig. 7) [50]. The re-docked pose overlaps with the experimental orientation, depicting that the virtual screening cum molecular docking employed in this study is accurate.


### Histopathological Analysis of DMBA model of breast carcinoma
  DMBA induces mammary tumor (Fig. 3) formation in an animal model [51]. Group 2 shows atypical features (pleomorphism and hyperchromasia) consistent with sarcomatoid lesions. This shows DMBA induces both sarcoma and comedo carcinoma. Comedo carcinoma of the breast is a type of ductal carcinoma in situ [52].

  In group 3, the formation of invasive ductal carcinoma was also observed, this shows that in the present study DMBA induces not only comedo carcinoma but also invasive ductal carcinoma subtypes of breast cancers. The formation of extensive necrosis in group 4 is believed to be due to the treatment with 200 mg/kg body weight of the carotenoid isolates. According to Amaravadi and Thompson, (2007) [53] necrosis can be the end product of apoptosis and therapy-induced necrotic cell death has been reported to initiate an immune response to tumor cells. Conclusively, the DMBA model of breast carcinoma in the present study induced comedo and invasive ductal subtypes of breast carcinoma.


### Tumour Volume in DMBA model of breast carcinoma
  Determining the tumour volume is evidenced to have prognostic importance in various studies [54,55]. Treatment of DMBA-induced breast cancer (Fig. 3) with the carotenoid isolates is shown to reduce the tumour volume (Fig. 4). The reduction in the mammary tumour volume observed in this study corroborated the earlier report of Chew et al. (1999) [56] that carotenoids decreased mammary tumor volume. Solid tumor growth is reliant on angiogenesis [57], thus the decrease in mammary tumour volume is probably due to the anti-angiogenic potential of the treatment (carotenoid isolates).


## Conclusion
  The binding of carotenoid isolates of Spondias mombin, astaxanthin, 7,7′,8,8′-tetrahydro-β,β-carotene, and beta-carotene-15,15′-epoxide to the ATP binding site of VEGFR2 kinase domain led to the DFG-out conformation and are in tandem with known tyrosine kinase inhibitors. Treatment with the carotenoid isolates of Spondias mombin demonstrated anti-angiogenic and anti-proliferating potentials in the DMBA model of breast cancer.


## CRediT authorship contribution statement
  Damilohun Samuel Metibemu: Conceptualization, Methodology, Software, Formal analysis, Writing - original draft, Writing - review & editing. Oluseyi Adeboye Akinloye: Supervision, Conceptualization, Investigation, Visualization. Adio Jamiu Akamo: Supervision, Data curation, Investigation. Jude Ogechukwu Okoye: Visualization, Formal analysis, Writing - review & editing. David Ajiboye Ojo: Supervision, Data curation, Investigation. Eric Morifi: Formal analysis, Visualization. Idowu Olaposi Omotuyi: Methodology, Software, Supervision.


## Declaration of Competing Interest
  The authors report no declarations of interest.


## Supplementary data
  The following is Supplementary data to this article:


## Acknowledgments
  The authors appreciate the Mass Spectrometry Laboratory, Witwatersrand University, Johannesburg for the Liquid Chromatography-Mass Spectrometry analysis.