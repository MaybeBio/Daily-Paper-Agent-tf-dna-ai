# The role of Luteolin, Naringenin, and Scutellarin in breast cancer by inhibition of HDAC4/HDAC8


## Supplementary Information
  The online version contains supplementary material available at 10.1038/s41598-026-44279-w.


## Introduction
  Breast cancer remains one of the most common malignancies in women worldwide. It poses certain therapeutic challenges, despite improvements in current treatments. Although chemotherapy and radiation therapy are effective standard interventions, they are often associated with serious side effects, such as neuropathy, immunosuppression, and drug resistance1. Among natural products, phytochemicals, especially flavonoids, have garnered significant attention due to their diverse and potent pharmacological activities. Flavonoids are polyphenolic secondary metabolites present in fruits, vegetables, leaves, and seeds. Flavonoids have a benzopyrone backbone with variable phenolic substitutions and are synthesised through the phenylpropanoid pathway1. They are generally classified into seven subtypes: flavones, flavonols, flavanones, isoflavones, anthocyanidins, flavanols, and chalcones2.

  These flavonoids represent a wide range of biological activities, including anticancer3, anti-inflammatory4, antioxidant, antiviral, and cardioprotective effects. The anticancer efficacy of these flavonoids is attributed to several mechanisms, which may involve ROS scavenging, chelation of metal ions, activation of antioxidant defences, and modulation of various signalling pathways that participate in apoptosis, angiogenesis, or carcinogen detoxification3.

  Compounds such as Quercetin5, Luteolin6, and Kaempferol7 have exhibited the potential to cause apoptosis in cancerous cells and, hence, are considered anticancer agents.

  For this study, we chose three structurally diverse flavonoids, namely Luteolin, Naringenin, and Scutellarin, with known bioactive potential and possessing structural similarity to Quercetin.

  Luteolin is a flavone widely found in celery, broccoli, carrots, onion leaves, and chrysanthemum flowers. It generally exists in glycosidic form. It is a potent ROS inhibitor, with wide biological activity8.

  Naringenin is a flavanone known for its therapeutic effects in inflammatory diseases, sepsis, fibrosis, diabetes, insulin resistance, and cancer. It is widely studied for its modulatory effect on metabolic and inflammatory pathways9.

  Scutellarin has a variety of biological actions, including anti-inflammatory, anti-dementia, and anticancer properties. It has been demonstrated to suppress migration, proliferation, and apoptosis in cancer models, especially colorectal carcinoma (HCT116)10. We aimed to comprehensively evaluate and compare their anticancer, antioxidant, and anti-inflammatory properties in breast cancer and identify their molecular targets using both in silico and in vitro validation approaches.


## Results

### In silico studies revealed HDAC4 and HDAC8 as potential targets for the selected flavonoid compounds
  To identify potential protein targets of the selected flavonoids (Fig. 1A), ligand mapping was performed using ePharmaLib. Among the top 10 predicted targets based on the Tversky similarity index (ranging from 0 to 1), histone deacetylases, specifically HDAC4 and HDAC8 emerged as high-confidence hits. Screening of the known HDAC inhibitor Vorinostat further validated the reliability of the method, as it successfully identified HDACs among the top targets (Table 1).

  Fig. 1Structural representation and binding interactions of selected compounds. A Chemical structures of selected flavonoids. B–E Docking poses at the zinc-binding site of HDAC4 with LMK-235, Naringenin, Scutellarin and Vorinostat respectively. F–G Docking poses at the zinc-binding site of HDAC8 with PCI-34051and Luteolin respectively.

  Table 1Tversky index for the HDACs obtained from ePharmaLib.CompoundsHDAC4HDAC7HDAC8Quercetin0.847––Naringenin0.9310.7680.809Scutellarin0.9410.717–Luteolin0.9450.5060.593Vorinostat0.579–0.583

  AutoDock Vina was used for molecular docking in order to validate these results. For every flavonoid–protein complex, docking scores and binding energies were computed. Priority was given to poses that involved direct contact with the catalytic zinc ion. To find common interaction residues, the best-scoring conformations of each flavonoid were compared to those of established HDAC inhibitors (Fig. 1B–G). Naringenin, Quercetin, and Scutellarin exhibited increased binding to HDAC4, but Luteolin showed a greater affinity for HDAC8 (Table 2). These results were further supported by the number and nature of protein–ligand interactions (Tables 3, 4), strengthening the predictions from ePharmaLib and molecular docking.

  Table 2Binding energies of flavonoid compounds with two target proteins, highlighting common residues with protein-specific inhibitor conformations.Flavonoid compoundChemical structureTarget proteinPDB IDBinding energy (Kcal mol−1)Common residues with specific inhibitorLuteolin  HDAC42VQM− 7.7His159 Phe227ZnHDAC83SFF− 8.9His180 Gly303 Gly304ZnNaringenin  HDAC42VQM− 7.6His159 Phe227ZnHDAC83SFF− 6.8Asp267 Phe208 Met274ZnQuercetin  HDAC42VQM− 7.5ZnHDAC83SFF− 6.4Tyr306 His180 Met274ZnScutellarin  HDAC42VQM− 8.6His159 Phe227ZnHDAC83SFF− 8.1His180Gly303 Gly304Met274ZnVorinostat  HDAC42VQM− 6.2His159 Phe227 His198 Phe168 Pro156ZnHDAC83SFF− 7.8His180

  Table 3Docking score and the number of interactions each flavonoid has with the HDAC4 protein.HDAC4CompoundTarget proteinDocking scoreNumber of interactionsHydrogen bondElectrostaticHydrophobicLuteolinHDAC4− 7.7313NaringeninHDAC4− 7.6112QuercetinHDAC4− 7.5221ScutellarinHDAC4− 8.6813VorinostatHDAC4− 6.23-4Order of Binding affinity of HDAC4 with compounds: Scutellarin > Luteolin > Naringenin > Quercetin > Vorinostat.

  Table 4Docking score and the number of interactions each flavonoid has with the HDAC8 protein.HDAC 8CompoundTarget proteinDocking scoreNumber of interactionsHydrogen bondElectrostaticHydrophobicLuteolinHDAC8− 8.9419NaringeninHDAC8− 6.8123QuercetinHDAC8− 6.4213ScutellarinHDAC8− 8.1316VorinostatHDAC8− 7.83-4Order of Binding affinity of HDAC8 with compounds: Luteolin> Scutellarin > Vorinostat > Naringenin > Quercetin.


### Flavonoids inhibit HDAC4 and HDAC8 enzyme activity and expression
  Biochemical enzyme assays using immunoprecipitated HDAC4 and recombinant HDAC8 were carried out to examine the flavonoid molecules for their HDAC inhibitory potential. Exposure to 1 nM of Luteolin, Naringenin, and Scutellarin significantly reduced enzymatic activity relative to controls (Fig. 2A). HDAC8 inhibition was particularly pronounced with Naringenin and Scutellarin (Fig. 2B).

  Fig. 2Enzymatic and Biochemical Assay for HDAC4 and HDAC8 and their Protein Expression after different flavonoid treatment for 24 h in MCF-7 and MDA-MB-231 cells. A–D Significant reduction in HDAC4 and HDAC8 activity is seen after flavonoid treatment, at par with the known inhibitor SAHA. E–F Representative Western blot analysis Bands shown in this panel were cropped from the same original gel and graphical representation of fold change values after densitometry analysis showing protein expression levels of Acetyl Tubulin, Alpha Tubulin, HDAC4 and HDAC8, and GAPDH as a loading control. Cropping boundaries are indicated with clear dividing space. The full-length image is provided in Supplementary Fig. 3A, images of uncropped gel is provided in Supplementary Fig. 3B-3 K. *p < 0.05, **p < 0.01, ***p < 0.001 and ****p < 0.0001 compared to control.

  The inhibitory effect was also confirmed in breast cancer cell lines (MCF-7 and MDA-MB-231) following 24-hour treatment with flavonoids. HDAC8 activity was significantly reduced, with SAHA (Vorinostat) demonstrating the highest inhibition as expected in both cell lines (Fig. 2C, D).

  Western blot analysis further confirmed HDAC8 inhibition by assessing levels of acetylated tubulin, a known HDAC8 substrate. Both MCF-7 and MDA-MB-231 cells showed a marked increase in acetylated tubulin following flavonoid treatment, indicating enzymatic inhibition. Additionally, flavonoid treatment resulted in reduced expression of HDAC4 and HDAC8 proteins, suggesting transcriptional or post-translational modulation (Fig. 2E, F).


### Flavonoids suppress proliferation of breast cancer cells
  Given that HDACs are established targets in cancer therapy, we next examined the cytotoxic effects of flavonoids on breast cancer cell lines (MCF-7 and MDA-MB-231) and a non-cancerous breast epithelial line (MCF-10 A). The MTT assay was used to measure the viability of cells treated with increasing doses of Luteolin, Naringenin, Scutellarin, and Quercetin. The viability of MCF-7 and MDA-MB-231 cells decreased in a dose-dependent manner, but MCF-10 A cells were relatively resistant (Fig. 3A–C). Apoptotic cell death was further confirmed by DAPI labelling, which showed nuclear condensation and disintegration in treated cancer cells (Fig. 3D–E).

  Fig. 3Anti-proliferative effects of flavonoids on breast cancer cells. Cell viability percentages in A MCF-10 A, B MCF-7, and C MDA-MB-231 at various concentrations of the compounds. D DAPI Fluorescence images of MCF-7 & MDA-MB-231 cells showing apoptosis. *p < 0.05, **p < 0.01, ***p < 0.001 and ****p < 0.0001 compared to control.


### Flavonoids induce apoptosis in breast cancer cells
  To validate apoptotic induction, Annexin V–PE staining was performed. Flow cytometry revealed a significant increase in early and late apoptotic cells in both MCF-7 and MDA-MB-231 lines treated with flavonoids compared to controls (Fig. 4A–B).

  Fig. 4Apoptosis and Cell Cycle Analysis in MCF-7 and MDA-MB-231 cells using Flow Cytometry. Annexin/Pi Apoptosis of A MCF-7, B MDA-MB-231 cells. FACS analysis of cell cycle using PI, C MCF-7 and D MDA-MB-231 cells.

  PI staining was used in a cell cycle analysis to further validate these findings. When MCF-7 cells were treated with Luteolin and Scutellarin, the percentage of sub-G0/G1 cells rose, which is a sign of apoptotic DNA fragmentation (Fig. 4C). These substances, however, had little effect on the more aggressive and resistant MDA-MB-231 cells (Fig. 4D). As a positive control, quercetin caused 44.6% of MDA-MB-231 cells to become sub-G0/G1 (Supplementary Fig. 1). Collectively, these data indicate that among the selected flavonoids, Luteolin is a potent inducer of apoptosis in MCF-7 cells and may serve as a promising candidate for further development in breast cancer therapy. However, their effectiveness against more aggressive subtypes such as MDA-MB-231 warrants further investigation.


### Luteolin and Scutellarin exhibit strong antioxidant activity
  Oxidative stress plays a key role in cancer progression, and flavonoids are widely known for their antioxidant potential. To evaluate and compare the antioxidant capacities of the selected flavonoids, standard DPPH and ABTS radical scavenging assays were conducted.

  In the DPPH assay, at 75 µM, Luteolin and Scutellarin demonstrated significant free radical inhibition (69.0% and 88.5%, respectively) (Fig. 5A; Table 5), which matched closely that of Quercetin (89%) (Supplementary Fig. 2A; Supplementary Table 1). In the ABTS assay, at 15 µM ABTS, Scutellarin (73.6%) demonstrated significant free radical inhibition (Fig. 5C; Table 5), and it was comparable to Quercetin (Supplementary Fig. 2B; Supplementary Table 1) in radical scavenging efficiency.

  Fig. 5Representative diagrams showing the antioxidant activity A–D and reducing powers E–G of the compounds. A DPPH radical scavenging activity of flavonoid compounds at 75 µM. B Graph showing inhibition percentages of compounds at chosen concentrations of 12.5µM, 25 µM, 50µM and 75µM. C ABTS radical scavenging activity of flavonoid compounds at 15µM. D Graph showing inhibition percentages of compounds at chosen concentrations of 4µM, 8µM, 12µM and 16µM. E FRAP Assay and F CUPRAC Assay expressed as Ascorbic Acid Equivalents (µMol AAE/µMol Substance). G Total phenolic content estimation using Folin-Ciocalteu reagent, expressed as Gallic Acid Equivalents (µMol GAE/ µMol Substance). *p < 0.05, **p < 0.01, ***p < 0.001 and ****p < 0.0001 compared to the control.

  Table 5DPPH and ABTS activity assay of the flavonoids.CompoundsDPPH radical scavenging activity at 75µMIC50 of compounds evaluated using DPPH assay (µM)ABTS radical scavenging activity at 15µMIC50 of compounds evaluated using ABTS assay (µM)Luteolin69.042 ± 0.13958.98 ± 4.01331.573 ± 0.0021–Naringenin3.251 ± 0.093–17.563 ± 0.0034–Scutellarin88.544 ± 0.66040.995 ± 0.37173.688 ± 0.01911.3678 ± 0.0497

  The antioxidant capacity of the active flavonoids was further supported by the IC₅₀ values found for these experiments (Fig. 5B and D; Table 4).

  Standard curves created with ascorbic acid were used in FRAP and CUPRAC experiments to measure antioxidant capacity. Luteolin and Scutellarin demonstrated antioxidant potency equal to or higher than ascorbic acid at 5 µM (FRAP) and 20 µM (CUPRAC) (Fig. 5E–F; Table 5). In the CUPRAC assay, all compounds except Naringenin outperformed ascorbic acid.

  Table 6FRAP and CUPRAC antioxidant assay of the flavonoids.CompoundFRAP assay (µMol AAE/ µMol of substance)CUPRAC assay (µMol AAE/ µMol of substance)Total phenolics estimated using Folin-Ciocalteu’s reagent (µMol GAE/ µMol of substance)Luteolin1.049 ± 0.0953.397 ± 0.0460.955 ± 0.015Naringenin0.057 ± 0.0041.514 ± 0.0781.641 ± 0.006Scutellarin0.36 ± 0.0323.795 ± 0.0510.825 ± 0.048

  Further, the total phenolic content (TPC) assay using Folin–Ciocalteu reagent revealed that all flavonoids had TPCs comparable to or greater than gallic acid. Among the selected flavonoids, Naringenin exhibited the highest phenolic content (Fig. 5G; Table 6).


### Flavonoids enhance antioxidant enzyme activity and reduce intracellular ROS
  To assess intracellular antioxidant effects, catalase activity was measured in MCF-7 and MDA-MB-231 cells treated with 1 nM of each flavonoid. All three flavonoids significantly enhanced catalase activity in MCF-7 cells, with Luteolin, Naringenin, and Scutellarin (Fig. 6A) showing high potency, comparable to that of Quercetin (Supplementary Fig. 2C). In MDA-MB-231 cells, Luteolin and Naringenin significantly increased catalase activity (Fig. 6B), with Luteolin outperforming Quercetin (Supplementary Fig. 2D).

  Fig. 6Effects of flavonoids on the activity of catalase and intracellular ROS. A MCF-7, B MDA-MB-231 cells. C FACS analysis of intracellular ROS in MCF-7 & MDA-MB-231 cells. Data is presented as Mean ± SD (n = 2); *p < 0.05, **p < 0.01, ***p < 0.001 and ****p < 0.0001 compared to the control cells.

  Using DCFDA-based flow cytometry, intracellular ROS levels were assessed. Strong ROS scavenging activity was demonstrated in MCF-7 cells by Luteolin and Scutellarin (Fig. 6C), which was greater than that of Quercetin. All flavonoids significantly decreased ROS levels in MDA-MB-231 cells (Fig. 6C), demonstrating their antioxidant activity in a variety of breast cancer cell lines.


### Flavonoid treatment attenuates inflammation by modulating cytokine expression
  Given the tight link between oxidative stress and inflammation in cancer, the anti-inflammatory effects of flavonoids were evaluated using qPCR and Western blot analysis in LPS-stimulated THP-1 macrophages.

  LPS exposure significantly elevated pro-inflammatory cytokines, including COX-2, IL-12, TNF-α, and NF-κB. Treatment with Luteolin, Naringenin, and Scutellarin (1 nM) led to a marked downregulation of NF-κB, COX-2, IL-12, and TNF-α, and upregulation of IL-10, an anti-inflammatory cytokine (Fig. 7A–E). Naringenin was particularly effective at inducing IL-10 expression. Western blot analysis confirmed these findings at the protein level. LPS-stimulated THP-1 cells exhibited strong induction of COX-2 and NF-κB (p65), which was significantly reduced upon flavonoid treatment. Overall, Luteolin and Naringenin caused a significant reduction in NF-κB and COX-2 protein expression, as seen in Fig. 7F, representing their strong anti-inflammatory activity.

  Fig. 7Anti-inflammatory effects of the compounds on Thp1 cells studied using mRNA expression of pro-inflammatory and anti-inflammatory cytokines using qPCR and protein Expression of COX2 and NFκB after different flavonoid treatment for 24 h in THP1 cells. A–E During LPS stimulation, significant increase in COX2, IL-12, IL10, TNF-alpha and NFκB was observed. Flavonoid treatment significantly reduced the mRNA expression of proinflammatory cytokines and increased the anti-inflammatory cytokines. F Representative Western blot analysis showing protein expression levels of COX-2 (~ 72 kDa), NF-κB p65 (~ 65 kDa), and GAPDH (~ 37 kDa) as a loading control. Representative Western blot analysis Bands shown in this panel were cropped from the same original gel. Cropping boundaries are indicated with clear dividing space. The full-length, uncropped gel is provided in Supplementary Fig. 4, full blot of which is provided in Supplementary Fig. 5A-C. NFκB decreased after treatment with Luteolin and Naringenin. COX2 expression decreased significantly in each flavonoid treatment condition. *p < 0.05, **p < 0.01, ***p < 0.001 and ****p < 0.0001 compared to LPS.

  These results further emphasize the multifaceted bioactivity of the selected flavonoids, especially Luteolin, Scutellarin, and Naringenin, in modulating oxidative stress and inflammatory responses that are important both for cancer progression and therapeutic resistance.


## Discussion
  With 2.3 million women diagnosed in 2020 alone, breast cancer continues to be a major worldwide health concern11. Although radiation therapy and cytotoxic chemotherapy are prevalent therapies, they frequently have crippling side effects, including bone loss, infertility, and cardiotoxicity12. These limitations highlight the urgent need for alternative therapies that are both effective and less toxic.

  Natural compounds, particularly flavonoids, have emerged as promising anticancer agents due to their diverse biological activities, including antioxidant, anti-inflammatory, and pro-apoptotic effects3,4. Increasing evidence has established strong causal links between oxidative stress, chronic inflammation, and cancer progression13–15. Flavonoids possess functional hydroxyl groups that can donate electrons or hydrogen atoms to neutralize free radicals and stabilize them through resonance. Naturally occurring compounds, especially flavonoids, are appearing as encouraging anticancer agents because of their varied bioactivities, including antioxidant, anti-inflammatory, and pro-apoptotic actions. Indeed, a growing number of reports have established that oxidative stress and chronic inflammation are causally related to the initiation and progression of cancer. Flavonoids have functional hydroxyl groups that are capable of donating electrons or hydrogen atoms to neutralize free radicals and stabilize them by resonance.

  In this study, three flavonoids, Luteolin, Naringenin, and Scutellarin, were examined for their anticancer, antioxidant, and anti-inflammatory activities, given that Quercetin is a well-known flavonoid with an anticancer effect. Their possible molecular targets relevant to breast cancer were also explored. Most natural compounds are biologically active via multiple pathways, and thus, target identification is crucial for further therapeutic development16.

  Given the benefits of targeted chemotherapy in minimizing off-target toxicity17, we employed structure-based pharmacophore mapping and target fishing using ePharmaLib, which identified HDAC4, HDAC7, and HDAC8 among the predicted targets with a good score. HDACs have been known drug targets for the treatment of several diseases, including cancer18. However, due to the presence of 18 HDAC isoforms with high homology in the catalytic domain, most of the inhibitors (HDACi) inhibit more than one isoform, leading to side effects and thus development and identification of isoform-specific HDACi is the current focus of research19.

  Docking studies confirmed preferential binding affinities where Naringenin, Quercetin, and Scutellarin showed stronger interaction with HDAC4, whereas Luteolin had higher affinity for HDAC8. These in silico results are in line with previous studies reporting that flavonoids can target histone deacetylases20.

  The predictions from docking study were validated by biochemical, cell-based enzyme activity assays and immunoblotting, which demonstrated HDAC inhibition by all tested flavonoids and are consistent with earlier studies21. Additional validation was provided by MTT, Annexin V, FACS-based cell cycle analysis and fluorescence microscopy using DAPI, confirming apoptosis induction by the flavonoids in MCF-7 cells.

  Previous studies have shown the involvement of HDAC4 and HDAC8 in cancer progression via ROS production and inflammatory pathways22,23. Furthermore, given the known antioxidant and anti-inflammatory roles of flavonoids, we tried to assess these activities in the context of breast cancer. Catalase activity assays revealed that Luteolin and Naringenin increased antioxidant enzyme activity in both MCF-7 and MDA-MB-231 cells, with Luteolin performing the best. Interestingly, Naringenin, though relatively weak in chemical radical scavenging assays, significantly enhanced catalase activity, consistent with prior reports24.

  Radical scavenging assays further supported the antioxidant potential of Scutellarin and Luteolin, which matched Quercetin in DPPH assays. The importance of hydroxyl group substitution in radical scavenging was emphasized by Huang et al.25, explaining Scutellarin’s potency. In the ABTS assay, Scutellarin performed well, though Luteolin showed reduced activity, consistent with prior findings26. The differential response to DPPH and ABTS radicals may stem from structural interactions, such as nitrogen shielding in DPPH27.

  Luteolin and Scutellarin showed a similar reducing power to that of ascorbic acid in the FRAP assay. CUPRAC results confirmed strong reducing potential for all flavonoids except Naringenin, which agreed with their structural features28. In the selected series of flavonoids, Luteolin lacked the 3-hydroxy group, Scutellarin lacked B-ring dihydroxy substitution, and Naringenin lacked either the double bond or dihydroxy groups, hence their relative potencies. Quercetin, however, possesses all three important structural motifs, viz. the 5-hydroxy-4-keto group, the 2,3-double bond, and the 3’,4’-dihydroxy substitution on the B ring, all of which together combine to give its very high antioxidant power.

  Total phenolic content (TPC) assays support these trends. Naringenin showed high reactivity, though Scutellarin’s relatively lower response in this assay, despite high antioxidant performance, warrants further mechanistic investigation.


## Conclusion
  Phytochemicals, in general, and flavonoids, in particular, have attracted increasing interest due to their broad-spectrum antioxidant, anti-inflammatory, and anticancer properties. The main objective of this study was to systematically evaluate the bioactive potential of three selected flavonoids (Luteolin, Scutellarin, and Naringenin) and correlate their efficacies. Our results indicate that all flavonoids tested showed anticancer and antioxidant activity in at least one of the experimental assays utilized. Most interestingly, Luteolin and Scutellarin were found to be consistently among the most promising compounds, with strong activities in numerous parameters such as HDAC inhibition, induction of apoptosis, radical scavenging, catalase activation, and anti-inflammatory gene modulation. Our results imply that Luteolin and Scutellarin could be promising candidates for therapeutic management in breast cancer and probably other oxidative stress and inflammation related diseases due to their multi-targeted bioactivity. Further validation in vivo experiments and pharmacokinetic profiling will be needed to develop these compounds toward clinical application (Table 7).

  Table 7Overall summary of the study results of potent biological activities of the flavonoids.


## Materials and methods

### Reagents
  1X Phosphate Buffer Saline, MTT, Trypan blue, DMEM and RPMI (GIBCO), FBS, Antibiotic-Antimycotic (100X), Trypsin, RIPA buffer, Hydrogen Peroxide, Protease inhibitor, BSA, Methanol, Glacial acetic acid, 1,1-diphenyl-2-picryl-hydrazyl (DPPH), Ascorbic acid, Ferric chloride, Acetate buffer, 2,2’-azino-bis(3-ethylbenzothiazoline-6-sulphonate (ABTS), potassium persulfate, 2,4,6-tri(2-pyridyl-1,3,5-triazine) (TPTZ), dichlorodihydrofluoresceindiacetate (DCFDA), Paraformaldehyde, Triton-X, DAPI, TRIzol (Invitrogen), iScript™ cDNA Synthesis Kit, Luna® Universal qPCR Master Mix, Nuclease-free water, Tris Base, Glycine, Sodium Chloride, Sodium Dodecyl Sulphonate, Acrylamide, Bis-acrylamide, Ammonium persulphate, TEMED (HiMedia), Bradford Reagent (SIGMA), SM powder (HiMedia), Anti-Alpha tubulin(Sigma-Aldrich), Anti-Acetylated Tubulin (Sigma-Aldrich) Anti-HDAC4 (Invitrogen), Anti-HDAC8(Abcam), Anti-COX2 antibody (Abcam), Anti-NFκB antibody (Abcam), Anti-GAPDH Antibody (Santa Cruz), and femtoLUCENT™ PLUS-HRP (G-Biosciences). Equipment used for image acquisition is Image LabTm Touch software. Instrument Type: ChemiDocTm MP, Serial number: 734BR4214; exposure 0.1 to 30 s.

  Luteolin (Sigma-Aldrich, Cat. No. L9283), Naringenin (Carl Roth, Cat. No. Art. 8524.1), and Scutellarin (Sigma-Aldrich, Cat. No. PHL89788) were purchased from Sigma-Aldrich (St. Louis, MO, USA) and Carl Roth (Karlsruhe, Germany).


### Target identification and validation

#### Structure-based pharmacophore mapping of natural products
  For pharmacophore mapping, initially, the 2D structure of the query molecule (Luteolin, Naringenin, and Scutellarin) is converted to a 3D structure and geometrically optimized with Openbabel. A conformer database of 100 conformers was generated for each molecule. The conformer database is mapped onto a library of 15,148 e-pharmacophores (ePharmaLib), representing 4616 unique target proteins, modelled from therapeutically relevant protein-ligand complexes of the screening Protein Data Bank29, using Align-it program via command line. Vorinostat, the known inhibitor of HDACs, were also mapped using ePharmaLib for comparison.


### Molecular docking study
  The 3D conformer structures (SDF format) of the flavonoids, namely Luteolin, Naringenin, Quercetin and Scutellarin along with Vorinostat, PCI-34,051, and LMK-235 were obtained from PubChem. PubMed was searched for the specific inhibitors of HDAC4 and HDAC8, and LMK-23530 and PCI-34,05131 were chosen respectively. Specific inhibitors of HDAC4 and HDAC8 were chosen to draw out comparisons between the best protein-flavonoid poses and protein-specific inhibitor poses having favorable interactions with Zinc. This was done to find out if the selected flavonoids possessed inhibitory activity.

  X-ray crystal structures of HDAC8 (PDB ID: 3SFF, resolution: 2.00 Å) and HDAC4 (PDB ID: 2VQM, resolution: 1.80 Å) were obtained from the RCSB protein data bank in PDB format.

  PyMol software v2.x (Schrodinger) and AutoDock Tools-1.5.7 were used to process the proteins. Water molecules and other ligands interacting with the protein were cleaned using PyMol software v2.x (Schrodinger). AutoDock Tools 1.5.7 was used for the addition of polar Hydrogens and Kollmann charges. The grid was built using AutoDock tools 1.5.7, keeping the Zinc atom as the center and grid dimensions as 25(x) × 25(y) ×25(z). This was done because compounds interacting with Zinc were more likely to show inhibitory activity. Molecular docking was performed using AutoDock Vina32 and the outputs were visualized using Discovery Studio visualizer 2021.


### HDAC4 enzymatic assay
  For HDAC4 activity assay, the HDAC4 enzyme was immunoprecipitated from HeLA cells and was used as the enzyme source along with FLUOR DE LYS®-HDAC deacetylase substrate (ENZO lifesciences) in presence or absence of, Luteolin (1nM), Naringenin (1nM) and Scutellarin (1nM).


### HDAC8 enzymatic assay
  The HDAC8 enzyme activity using recombinant HDAC8 protein and FLUOR DE LYS®- HDAC8 deacetylase substrate (BML-Kl178-0005, ENZO Life Sciences) in presence or absence of Luteolin, Naringenin, and Scutellarin was performed as described previously33.

  Further, for in-vitro assay, MCF-7 and MDA-MB- 231 cells were seeded in 60 mm dishes, and upon attaining 80–90% confluency, cells were treated with or without flavonoids for 24 h, and the cell lysates were prepared as described earlier. The crude cell lysate was used as an enzyme source and HDAC8 Enzyme activity assay was performed as described above.


### Anti-cancer activity

#### Cell lines and cell culture conditions
  Two human Breast cancer cell lines, non-metastatic luminal A MCF-7 and metastatic MDA-MB-231, human cervical cancer cell line, HeLA and immortalized normal breast cell line, MCF10A, were procured from the National Centre for Cell Science (NCCS, Pune, India). MCF10A was cultured in Dulbecco’s modified Eagle’s medium: Ham’s F12 (1:1) (DMEM: F12; Gibco) supplemented with 10% Horse serum (Gibco), 10% Fetal Bovine Serum (FBS: Gibco), 1% Mammary Epithelial Growth Supplement (MEGS: Gibco) in the presence of 1% penicillin-streptomycin (Anti-Anti: Gibco), however, HeLA, MCF7 and MDA-MB-231 cultured in high glucose Dulbecco’s modified Eagle’s medium (DMEM; GIBCO) supplemented with 10% fetal bovine serum (FBS; GIBCO) in the presence of 1% penicillin-streptomycin (GIBCO) at 37 °C humidified atmosphere in an incubator with 5% CO2 saturation.


### MTT assay
  All three breast cell lines, MCF-10A, MCF-7 and MDA-MB-231, were seeded into 96 well plates at 5000 cells per well. After adherence, they were treated with different concentrations of Luteolin, Naringenin, and Scutellarin for 24 h. The cell viability was assessed using 3-(4,5-Dimethylthiazol-2-yl)-2,5 Diphenyltetrazolium Bromide (MTT) as described earlier34.


### Fluorescence microscopy
  MCF-7 and MDA-MB-231 cells were seeded onto coverslips, and after adherence, they were treated with 1 nM of bioactive molecules for 24 h. For DAPI staining, a method previously described35 was followed, and the images were taken using the LEICA DMi8 instrument, LEICA SP8 Confocal microscope with software Leica Application Suite X. Image processing was done using ImageJ Fiji software.


### Cell apoptosis assessment by FACS
  Annexin V Assay was performed to assess the Cell apoptosis. MCF-7 and MDA-MB-231 cells were seeded at a density of 0.3 × 106 cells/well in a 6-well plate and subsequently treated with the above-mentioned concentrations of the 5 bioactive flavonoids for 24 h. The cells were then harvested and proceeded for Annexin V assay as per the manufacturer’s protocol. In addition, the cells were stained with PI to assess the cell cycle stage during apoptosis condition.


### Western blotting
  The target validation of the flavonoids was further assessed in the breast cancer cell lines using Immunoblot. A 60 µg of treated protein lysates were separated on 10% to 12% SDS gel followed by Western blot using primary antibodies, HDAC8 (AB187139) HDAC4 (PA5-29103), GAPDH (G9545), Acetylated Alpha Tubulin (T6793) and Alpha Tubulin (T5168). The bands were developed using luminol solution (G Biosciences) and visualized using chemidoc. The densitometry analysis was performed using ImageJ Fiji software.


### Antioxidant assays

#### Biochemical assays
  Antioxidant potentials of the selected compounds were evaluated using 1,1-diphenyl-2-picryl-hydrazyl (DPPH) radical scavenging, 2,2′-azino-bis(3-ethylbenzothiazoline-6-sulphonate) (ABTS) radical scavenging, Ferric reducing antioxidant power (FRAP) and CUPRAC (Cupric reducing antioxidant capacity) Assays. DMSO was used as the negative control, and Ascorbic acid was used as the positive control for analyzing the antioxidant potency of the compounds.

  DPPH assay was performed according to the method described previously36, with slight modification where 0.4 mM DPPH solution was used for the assay.

  Inhibition% was calculated according to the following formula:

  \documentclass[12pt]{minimal} 				\usepackage{amsmath} 				\usepackage{wasysym}  				\usepackage{amsfonts}  				\usepackage{amssymb}  				\usepackage{amsbsy} 				\usepackage{mathrsfs} 				\usepackage{upgreek} 				\setlength{\oddsidemargin}{-69pt} 				\begin{document}$$inhibition\% =\frac{{{A_{Control}} - {A_{Sample}}}}{{{A_{Control}}}} \times 100$$\end{document}

  The concentration of the sample providing 50% free radical scavenging activity (IC50) was calculated from the graph of % inhibition vs. sample concentration.

  ABTS radical scavenging activities of the selected compounds were carried out using the method described by Chittasupho et al.37 with slight modifications to fit a reaction volume of 200uL. Ascorbic acid was used as standard. IC50 was calculated using the same calculation previously described in the DPPH Assay from the graph of % inhibition vs. sample concentration.

  FRAP Assay was performed according to the method of Li et al.38 CUPRAC Assay was performed using the previously described method39.

  All measurements were made in duplicate. For the CUPRAC assay and FRAP assay, the standard graph equation was used to convert the absorbance to Ascorbic acid equivalents (AAE). Data is depicted in terms of µMol of AAE/µMole of substance.


### Determination of total phenolic content
  Total phenolic content was evaluated using the Folin Ciocalteu (FC) method according to the method previously described40. Gallic acid monohydrates of concentrations 25, 50, 75, 100, 125 and 150 µM were used to construct the calibration curve. All measurements were made in duplicate. Upon obtaining absorbance values, the standard graph equation was used to convert them to Gallic acid equivalents (GAE). Data is depicted in terms of µMol of GAE/µMole of substance.


### Catalase assay
  Catalase activity was measured using hydrogen peroxide as the substrate by the method described by Aebi41 in the protein isolates of MCF-7 and MDA -MB-231 cells treated with Luteolin, Naringenin, and Scutellarin at 1nM concentration. The activity of Catalase was estimated using the first-order reaction and was represented as U/mg protein.


### Intracellular ROS analysis
  After 24 h of treatment with a 1nM concentration of flavonoids in MCF-7 and MDA-MB -231 cells, ROS production was measured using the dichlorodihydrofluoresceindiacetate (DCFDA) dye as discussed previously42. The intracellular ROS levels were analyzed using BD LSR Fortessa flow cytometry. Data on the BD flow cytometry was collected using FlowJo software.


### Anti-inflammatory studies

#### Cell culture and induction of inflammation
  THP1 cells were procured from the National Centre for Cell Science (NCCS) cell repository in India. The cells were cultured in RPMI 1640 (GIBCO) medium supplemented with 10% FBS (Fetal Bovine Serum) and 1x penicillin and streptomycin, cells were seeded in 6-well plates and grown at 37 °C and 5% CO2. The exponentially growing THP1 cells were subject to PMA (10nM) treatment for 48 h and differentiated into macrophages; following one hour LPS stimulation the flavonoid treatments were given for 24 h.


### RNA isolation and real-time PCR (qPCR)
  RNA isolation from the cells treated with or without flavonoids was carried out using Tris Reagent (Trizol) as previously described43. iScript™ cDNA Synthesis Kit was used to synthesize cDNA from the RNA samples (Concentration – 1 µg/ml).

  The 2-ΔΔCT method was used to normalise the control cells in order to calculate the mRNA expression levels following Real-time qPCR (Table 8)43. Further, western blotting was performed using primary antibodies of COX2, NFKB and GAPDH. The bands were developed using luminol solution (G Biosciences) and visualized using chemidoc. The densitometry analysis was performed using ImageJ Fiji software.

  Table 8The sequences of the primers used.SequenceAnnealing temperature 1. COX2 Primer Forward primer5′ GCACCCCGACATAGAGAGC 3′54 °CReverse primer5′ CTGCGGAGTGCAGTGTTCT 3′ 2. NFκBPrimer Forward primer5′ TGAACCGAAACTCTGGCAGCTG 3′55 °CReverse primer5′ CATCAGCTTGCGAAAAGGAGCC 3′ 3. IL10 Primer Forward primer5′ GACTTTAAGGGTTACCTGGGTTG 3′53 °CReverse primer5′ TCACATGCGCCTTGATGTCTG 3′ 4. IL12 Primer Forward primer5′ ACCCTGACCATCCAAGTCAAA 3′52 °CReverse primer5′ TTGGCCTCGCATCTTAGAAAG 3′ 5. TNFα Primer Forward primer5′ GAGGCCAAGCCCTGGTATG 3′55 °CReverse primer5′ CGGGCCGATTGATCTCAGC 3′ 6. GAPDH Primer Forward primer5′ GAGAAGGCTGGGGCTCATTTGC 3′58 °CReverse primer5′ TGGTGCAGGAGGCATTGCTGATG 3′


### Statistical analysis
  The experimental data was reported as mean ± SD or mean ± SEM. Data collection and the experimental procedure are handled in a double-blind manner. For statistical analysis, GraphPad Prism version 10.0.0 for Windows was utilised. Differences among multiple groups were tested using one-way ANOVA. p < 0.05 was considered to be a significant difference, which was marked in the graphs accordingly.


## Supplementary Information
  Below is the link to the electronic supplementary material.

  Supplementary Material 1

  Supplementary Material 2


## Acknowledgements
  This work was supported partially by NMPB (Grant# Z.18017/187/CSS/R&D/TL-01/2021-22-NMPB-IVA) to AMK. UoH-IoE, DST-FIST (SR/FST/LSII-041/2015) and DBT-BUILDER are acknowledged for infrastructural support.