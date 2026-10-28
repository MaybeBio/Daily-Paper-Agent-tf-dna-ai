# Analysis of potential targets of 20S-protopanaxadiol on diabetic nephropathy based on network pharmacology, molecular docking, and experimental validation


## Purpose
  This study aims to investigate the protective effects and mechanisms of 20S-protopanaxadiol (PPD), a key component derived from ginseng folium, against diabetic nephropathy (DN).


## Methods
  Ingredients of ginseng folium were collected and screened using the TCMSP database. Therapeutic target genes for ginseng folium against DN were obtained, and protein-protein interaction (PPI) networks were constructed. Gene Ontology (GO) function and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathway enrichments were conducted on these targets. Furthermore, the results of network pharmacology were validated via molecular docking. Subsequently,the effects of PPD on TGF-β1/Smads signaling pathway were assessed in db/db mice and HK-2 cells using biochemical assays and Western blotting.


## Results
  A total of 246 target genes for ginseng folium against DN were identified. KEGG analysis revealed significant enrichment in AGE-RAGE signaling in diabetic complications, PI3K-AKT, MAPK, and TNF pathways. PPD intragastric administration improved renal function in db/db mice and significantly reduced the expression of TGF-β1, α-SMA, p-Smad3, and Smad4 in renal tissue (p < 0.05). Furthermore, PPD decreased the expression of TGF-β1, p-Smad3, and Smad4 in high glucose-induced HK-2 cells.


## Conclusion
  PPD potentially alleviates renal fibrosis in db/db mice and HK-2 cells by inhibiting the TGF-β1/Smads pathway, thereby delaying DN progression.


## Introduction
  Diabetes is a global health emergency that demands urgent attention. According to a survey by the International Diabetes Federation, the global prevalence of type 2 diabetes mellitus (T2DM) is projected to be 783 million people by 2045 [1]. Diabetic nephropathy (DN) is one of the most common microvascular complications of diabetes and will affect 20% to 40% of diabetic patients [2]. In China, DN has been the leading cause of end-stage renal disease (ESRD) among the general population since 2011 [3]. Current treatments for DN primarily include renin-angiotensin system (RAS) antagonists, sodium-glucose cotransporter 2 (SGLT2) inhibitors, glucagon-like peptide-1 receptor (GLP-1R) agonists, and mineralocorticoid receptor antagonists (MRAs) [4]. However, these therapies cannot prevent progression to ESRD. Therefore, there is an urgent need to identify novel therapeutic targets for DN treatment.

  Chinese herbal medicine and its components possess unique advantages in disease prevention and treatment due to their multi-target, multi-component, and multi-pathway characteristics. Ginseng, a traditional Chinese medicinal plant, has been studied since the 1920s, and it has been found to have a hypoglycemic effect [5]. The hypoglycemic activity of ginseng extract is mainly attributed to ginsenosides. According to high-performance liquid chromatography (HPLC) analysis, the concentration of ginsenosides is highest in leaves, berries, and roots [6]. Edible ginseng roots and rhizomes are harvested from 5-year-old ginseng, while medicinal ginseng roots and rhizomes come from 6-year-old ginseng. Given that ginseng folium is a short-term renewable resource and can be harvested annually, its application is more economical than roots and stems [7]. The composition of ginseng folium extract differs from that of ginseng root extract [8], yet both possess significant medicinal value. Studies have demonstrated that ginseng folium extract exhibits hypoglycemic effects in diabetic rat models [9], comparable to those observed with ginseng root extract. Moreover, ginseng folium has been shown to possess various pharmacological properties. Compared to ginseng root extract, ginseng folium extract components not only offer significant medicinal value but also provide a more cost-effective solution. However, the mechanism underlying the therapeutic effects of ginseng folium in treating DN remains unclear. This article investigates the pharmacological actions of ginseng folium in DN treatment.

  The main active component in ginseng is ginsenosides, and 20S-protopanaxadiol (PPD) has been reported to bind to TGF-βR1 and TGF-βR2, blocking the TGF-β1 signaling pathway and inhibiting the activation of hepatic stellate cells (HSCs), thereby achieving the therapeutic goal of treating liver fibrosis [10]. However, the role and mechanism of PPD in renal function have not been thoroughly investigated. This study aims to explore the potential pharmacological targets of ginseng folium components in DN and lay the foundation for future research into novel DN treatments.


## Materials and methods

### Screening of components in ginseng folium
  The Traditional Chinese Medicine Systems Pharmacology Database and Analysis Platform (TCMSP, https://old.tcmsp-e.com/tcmsp.php) [11] was used to search for the keyword “ginseng folium” and retrieve the relevant components. After screening the ginseng folium ingredients for drug-likeness (DL) ≥ 0.2 and oral bioavailability (OB) ≥ 25%, we identified the selected components.


### Prediction of target genes for ginseng folium components
  The targets of the identified ginseng folium components were retrieved using TCMSP. The targets were converted into gene names using the UniProt database (https://www.uniprot.org/) [12] to identify the gene targets associated with ginseng folium components. For components of ginseng folium with corresponding targets identified in TCMSP, we downloaded their .mol2 format files from TCMSP and input them into ChemMapper (http://lilab-ecust.cn/chemmapper/) [13–15] for prediction.


### Screening of target genes for DN
  To collect disease gene targets related to DN, we searched the GeneCards database (https://www.genecards.org/, Version 5.19) [16] and the OMIM database (https://www.omim.org/) [17] using the term “diabetic nephropathy”. Genes obtained from the GeneCards database were ranked by relevance score, with a median score of 2.86 as the threshold. Target genes with scores above 2.86 were selected as DN disease targets. We merged the DN-related target genes from GeneCards and OMIM databases, removed duplicates, and obtained a comprehensive list.


### Prediction of component-target network
  The screened ingredients and target genes of ginseng folium were used to construct a component-target gene network diagram using Cytoscape 3.10.1. In Figure 1, pink nodes represent ginseng folium components, and blue nodes denote target genes.


### Identification of common targets between ginseng folium and DN
  The ginseng folium component targets and DN disease targets were input into Venny 2.1.0 (https://bioinfogp.cnb.csic.es/tools/venny/) to generate a Venny diagram of the common targets.


### Construction of the protein-protein interaction (PPI) network and identification of core targets
  To build a PPI network diagram, we used the STRING platform (https://www.string-db.org/) [18]. The PPI data were saved in .tsv format and imported into Cytoscape. Using the CentiScape plugin in Cytoscape to identify the top 10 core targets.


### Gene Ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) enrichment analyses
  To conduct GO and KEGG enrichment analyses, the common genes between ginseng folium and DN were input into DAVID 6.8 (https://david.ncifcrf.gov/). We collected the results for biological process (BP), molecular function (MF), cellular component (CC), and KEGG pathways from the enrichment analysis in DAVID. The enrichment results were sorted by ascending Benjamini-adjusted p-value, and the top ten GO terms and top twenty KEGG pathways were selected for plotting using RStudio (version 4.3.2).


### Molecular docking validation
  The molecular structures of pharmaceutical compounds were retrieved from the PubChem database (https://pubchem.ncbi.nlm.nih.gov) [19]. The 3D structures of key target proteins were obtained from the RCSB Protein Data Bank (PDB, https://www.rcsb.org) [20]. Molecular docking simulations were performed using AutoDock to assess the binding affinities of pharmaceutical components and the target proteins based on binding energy scores. Molecular docking interaction diagrams were generated using PyMOL.


### Animal experiments
  Male db/db mice (Strain No. T002407) and db/m mice (Strain No. N000214) on a C57BLKS genetic background that are 11 weeks old and weigh 34–45 g as well as db/m mice weighing 18–22 g, were obtained from GemPharmatech Co., Ltd (Nanjing, Jiangsu, China). All animal experiments adhered to the Guidelines for Ethical Review of Laboratory Animal Welfare (Ministry of Science and Technology of China). The mice were housed under controlled laboratory conditions: temperature at 22±2 °C, humidity at 50%–60%, and a 12-h light/dark cycle. Animal studies were performed in compliance with the ethical guidelines for animal studies and were approved by the Institutional Animal Care and Ethics Committee of Beijing Friendship Hospital.


### Reagents and antibodies
  20S-protopanaxadiol was purchased from MedChemExpress (HY-N079). Primary antibodies against TGF-β1 (21898-1-AP) and α-SMA (80008-1-RR) were purchased from Proteintech. The internal reference antibody β-actin (66009-0-lg) was purchased from Proteintech. Primary antibodies against Smad3 (ET1607-41) and Smad4 (ET1604-12) were purchased from Hangzhou HuaAn Biotechnology Co., Ltd. Anti-phospho-Smad3 (p-Smad3; 9520 T) was purchased from Cell Signaling Technology. Secondary antibodies, including HRP-conjugated goat anti-mouse IgG (SA00001-1) and goat anti-rabbit IgG (SA00001-2), were obtained from Proteintech.


### Establishment of DN mouse models, grouping, and drug treatment
  After a short adaptation period, db/m mice were randomly divided into two groups (n = 4/group): the db/m group and the db/m + PPD group. Similarly, db/db mice were randomly divided into two groups (n = 6/group): the control db/db group and the db/db + PPD group. Mice in the db/m + PPD and db/db + PPD groups were administered 20 mg/kg PPD by gavage daily for 3 weeks, while those in the control db/m and db/db groups received an equal volume of 0.9% sodium chloride solution. At the endpoint, mice were euthanized. Blood and renal tissues were collected, snap-frozen in liquid nitrogen, and stored at −80 °C.


### Intraperitoneal glucose tolerance test (IPGTT)
  Before the IPGTT, mice were fasted overnight and subsequently injected intraperitoneally with 50% glucose solution at a dose of 2 g/kg body weight. Blood samples were collected from the tail vein, and blood glucose concentration was measured at 0, 15, 30, 60, 90, and 120 min after injection.


### Immunohistochemistry (IHC) staining
  After dewaxing the paraffin-embedded sections of mouse kidney tissues, sections were incubated with a blocking solution containing sheep serum at room temperature for 1 h. Primary antibodies were then applied and incubated overnight at 4 °C. The following day, after washing with PBS, sections were incubated with secondary antibodies for 30 min at room temperature. Chromogenic development was performed using diaminobenzidine (DAB), followed by counterstaining with hematoxylin. Sections were dehydrated, cleared, and mounted with neutral mounting medium. DAB-positive areas were quantified using ImageJ.


### Western blotting
  Total protein was extracted from tissues or cells using RIPA lysis buffer, phenylmethylsulfonyl fluoride (PMSF), and protease inhibitor (PI). The supernatant was collected by centrifugation for subsequent analysis. Protein concentration was determined using the BCA protein assay kit. After adding the loading buffer, the protein samples were denatured in a heat block at 100 °C for 5 min. The samples were separated by SDS-PAGE and transferred to methanol-activated PVDF membranes. The membranes were incubated with primary antibodies and the corresponding secondary antibodies. The following primary antibodies were used in this study: β-actin (1:5000), TGF-β1 (1:1000), α-SMA (1:1000), Smad3 (1:2000), p-Smad3 (1:1000), and Smad4 (1:3000). Protein bands were analyzed by ImageJ software.


### Cell culture
  HK-2 cells (ATCC, CRL-2190TM) were cultured in DMEM/F12 medium containing 10% fetal bovine serum (FBS) and incubated at 37°C in a humidified atmosphere of 5% CO2. DMEM/F12 medium (PM150310), DMEM/F12 glucose-free medium (PM150322), and fetal bovine serum (FBS, 164210) were purchased from Pricella Biotechnology Co., Ltd (Wuhan, China). Trypsin-EDTA solution (T1300) was obtained from Solarbio Science & Technology Co., Ltd (Beijing, China). The BCA Protein Assay Kit (P0012) was purchased from Keygen BioTECH (Jiangsu, China). 20S-protopanaxadiol (HY-N0797) was purchased from MedChemExpress (Monmouth Junction, NJ, USA).


### Determined the expression levels of fibrosis-related proteins in HK-2 cells
  When the cells reached approximately 80% confluence, they were divided into the following groups: low-glucose (LG) group (5 mM glucose), high-glucose (HG) group (30 mM glucose), and PPD treatment groups: PPD5 (30 mM glucose + 5 μM PPD), PPD15 (30 mM glucose + 15 μM PPD), and PPD20 (30 mM glucose + 20 μM PPD). After 24 h of drug treatment, cells were collected, and cell proteins were extracted. Based on these results, the optimal PPD concentration (20 μM) was selected for subsequent experiments. Cells were re-treated under three conditions (LG, HG, HG + PPD) for 24 h before final protein extraction.


### Statistical analysis
  GraphPad Prism 8.0.2 and IBM SPSS Statistics 27.0 were used for data plotting and statistical analysis. Results are expressed as mean ± standard error of the mean (SEM).Differences between two groups were analyzed using unpaired two-tailed Student’s t-tests. For multi-group comparisons, one-way ANOVA with Tukey’s post hoc test was applied. Statistical significance was defined as p < 0.05.


## Results

### Screening of active components from ginseng folium
  After screening in the TCMSP database, 16 components from ginseng folium were identified (Table 1). By querying both the TCMSP database and ChemMapper, 695 disease-associated protein targets associated with these components were revealed. Cytoscape 3.10.1 software was used to construct the component-target network diagram as shown in Figure 1.


### Therapeutic targets of ginseng folium in DN
  By integrating the genes from both the GeneCards and OMIM databases, a total of 2226 disease-associated targets for DN were obtained. The 695 target genes associated with ginseng folium and the 2226 disease targets for DN were analyzed using Venny 2.1, yielding 246 common genes, which are potential therapeutic targets for ginseng folium against DN (Figure 2).

  The 246 targets for ginseng folium against DN were analyzed via STRING to construct a PPI network (Figure 3). The resulting network contained 251 nodes and 6504 edges, with an average node degree of 51.8. The PPI network was imported into Cytoscape (version 3.10.1) for visualization and further analyzed using the Centiscape plugin. The top 10 hub genes were identified as CCL2, NFKB1, IFNG, CRP, IL1B, STAT3, ICAM1, PPARG, ALB, and NOS3.


### GO enrichment analysis of overlapping targets
  The 246 targets were analyzed through the DAVID platform. GO enrichment yielded 990 BP terms, 117 CC terms, and 177 MF terms. Terms were sorted by ascending Benjamini-adjusted p-value, and the top 10 significant entries were selected for visualization (Figure 4). BP analysis showed that the intersection genes between ginseng folium and DN are primarily involved in: response to xenobiotic stimulus, positive regulation of gene expression, negative regulation of apoptotic process, positive regulation of transcription from RNA polymerase II promoter, positive regulation of cell proliferation, positive regulation of MAPK cascade, cellular response to lipopolysaccharide, protein phosphorylation, response to hypoxia, and inflammatory response. CC analysis indicated that these genes are mainly localized in: extracellular space, plasma membrane, extracellular region, caveola, an integral component of plasma membrane, cytosol, cell surface, receptor complex, external side of plasma membrane, and cytoplasm. MF enrichment analysis primarily highlighted activities related to: RNA polymerase II transcription factor activity, ligand-activated sequence-specific DNA binding, enzyme binding, identical protein binding, protein serine/threonine/tyrosine kinase activity, protein binding, zinc ion binding, protein tyrosine kinase activity, protein kinase activity, serine-type endopeptidase activity, and heme binding.


### KEGG enrichment analysis
  The 246 targets were subjected to KEGG enrichment analysis via the DAVID platform. Among 195 enriched terms, the top 20 pathways with Benjamini-adjusted p < 0.05 were selected and visualized (Figure 5). The results indicated that the significantly enriched pathways include: Pathways in cancer, Lipid and atherosclerosis, AGE-RAGE signaling pathway in diabetic complications, Hepatitis B, Prostate cancer, Fluid shear stress and atherosclerosis, Chemical carcinogenesis—receptor activation, PI3K-Akt signaling pathway, MAPK signaling pathway, Chagas disease, and TNF signaling pathway.


### Molecular docking analysis
  From the 16 core bioactive components in ginseng folium, the top 4 with the highest connectivity in the component-target network were selected. Molecular docking between these components and key targets was performed using AutoDock Vina. The resulting binding poses were visualized in PyMOL (Figure 6). Notably, Gypnoside V_qt exhibited strong binding to CCL2 with an energy of −6.65 kcal/mol. 20(R)-ginsenoside Rh2 showed moderate interaction with PPARγ (−5.43 kcal/mol), while ginsenoside Rg3_qt demonstrated high affinity for IL-1β (−7.30 kcal/mol). A structurally complex ginsenoside derivative (3S,5R,8R,9R,10R,12R,13R,14R,17S)-17-[(2S)-2-hydroxy-6-methylhept-5-en-2-yl]-4,4,8,10,14-pentamethyl-2,3,5,6,7,9,11,12,13,15,16,17-dodecahydro-1H-cyclopenta[a]phenanthrene-3,12-diol has binding ability to TGF-β1 (binding energy = −5.68 kcal/mol). The absolute value of binding energy indicates affinity and conformational stability: > 4.25 suggests some binding activity, > 5.0 indicates good binding activity, and > 7.0 indicates strong binding activity.

  Molecular docking indicated that “(3S,5R,8R,9R,10R,12R,13R,14R,17S)-17-[(2S)-2-hydroxy-6-methylhept-5-en-2-yl]-4,4,8,10,14-pentamethyl-2,3,5,6,7,9,11,12,13,15,16,17-dodecahydro-1H-cyclopenta[a]phenanthrene-3,12-diol”, also known as 20S-protopanaxadiol (PPD), exhibited good binding ability with TGF-β1. Meanwhile, PPD was also well bound to both Smad3 (binding energy −5.65 kcal/mol) and Smad4 (binding energy −6.06 kcal/mol). Integrating enrichment analysis, molecular docking, and literature studies, we hypothesized that the main components of ginseng folium may prevent DN by modulating inflammatory factors and fibrotic pathways. The top 4 components of ginseng folium successfully docked with key targets expression, indicating their multi-target potential against DN. To investigate the primary mechanism of ginseng folium on DN, we selected PPD for in vivo and in vitro validation within the classic TGF-β1/Smads fibrosis signaling pathway.


### In vivo experiment

#### Effects of PPD on body weight in DN mice
  Db/m and db/db mice received daily oral gavage of PPD or 0.9% normal saline for 3 weeks. Body weight was measured at baseline and endpoint. At baseline, there was no statistically significant difference in body weight between the PPD-treated and control groups in both db/m and db/db mice (Figure 7A). After 3 weeks of treatment, there remained no significant difference in body weight between the experimental group and the control group, indicating that PPD administration did not significantly affect body weight in mice (Figure 7B).


#### Effect of PPD on blood glucose in DN mice
  The IPGTT was performed after 3 weeks of PPD treatment. Compared to the db/m control group, the db/m + PPD group exhibited significantly lower blood glucose levels at 15 and 30 min after intraperitoneal glucose injection, although the overall area under the curve (AUC) did not differ significantly. In contrast, the db/db + PPD group exhibited reduced blood glucose and a significantly decreased AUC compared to the db/db group (p < 0.001) (Figure 7C,D). These results indicate that PPD improves glucose tolerance specifically in DN mice.


#### Effects of PPD on serum creatinine and urea nitrogen in DN mice
  The urea nitrogen level and serum creatinine of mice in the db/db group were significantly increased compared with db/m group. Compared to the diabetic db/db group, PPD treatment significantly reduced serum creatinine and urea nitrogen levels in the db/db + PPD group (p < 0.05). No significant differences were observed between the non-diabetic db/m + PPD group and the db/m control group (p > 0.05) (Figure 7E,F). The kidney index was significantly decreased in db/db mice compared to db/m controls (p < 0.05). However, no significant difference in kidney index was observed between PPD-treated db/db mice and untreated db/db mice (Figure 7G).


#### Effects of PPD on renal TGF-β1 expression in DN mice
  We evaluated the expression of TGF-β1 in mouse kidney tissues using IHC (Figure 8). IHC analysis of kidney tissues revealed significantly elevated TGF-β1 expression in db/db mice compared to db/m. PPD treatment markedly reduced TGF-β1 levels in the db/db + PPD group, while no significant difference was observed between the db/m and db/m + PPD groups. These findings demonstrate that PPD treatment can attenuate renal TGF-β1 overexpression in DN mice.


#### Effects of PPD on fibrosis indexes and TGF-β1/Smads signaling pathway in renal tissue of DN mice
  Western blotting demonstrated significantly elevated expression levels of fibrosis-related proteins TGF-β1 in db/db mice compared to db/m controls, while these levels were markedly reduced in db/db + PPD mice (p < 0.001) (Figure 9A,B). Additionally, p-Smad3 (p < 0.05) and Smad4 (p < 0.001) expression, downstream effectors in the TGF-β1 pathway, were significantly upregulated in db/db mice, with this trend being reversed in db/db + PPD mice (Figure 9E,F). In db/db mice, the expression of α-SMA showed an upward trend, but the difference was not statistically significant, and this trend was attenuated by PPD treatment (p < 0.05) (Figure 9C). These findings indicate that PPD attenuates renal fibrosis in DN by inhibiting the TGF-β1/Smads signaling axis.


### In vitro experiment

#### Effect of PPD on HG-induced HK-2 cells and target proteins
  To establish the threshold glucose concentration for inducing fibrotic responses in HK-2 cells, we conducted a dose-response analysis using physiological (5 mM) and hyperglycemic conditions (25, 30, and 35 mM). Quantitative analysis of fibrotic markers demonstrated a concentration-dependent upregulation of α-SMA (Figure 10B,E), peaking at 30 mM glucose. This concentration was selected as the HG model for subsequent experiments. Western blotting analysis further revealed that TGF-β1 expression was significantly elevated in the HG group compared to the LG group (p < 0.01). In contrast, co-treatment with PPD dose-dependently attenuated TGF-β1 levels (p < 0.05) (Figure 10A,D).

  Consistent with in vivo findings, exposure of HK-2 cells to HG induced fibrosis via the TGF-β1/Smads signaling pathway. Western blot analysis revealed a significant upregulation of TGF-β1 expression in the HG group. Hyperglycemia further activated downstream Smad signaling, as an increase in the phosphorylation of Smad3 and an elevation in nuclear Smad4 expression. PPD treatment attenuated these effects, reducing p-Smad3 (p < 0.01) and Smad4 levels (p < 0.05) (Figure 10C,H,I). While α-SMA expression showed a trend toward an increase under HG conditions, PPD treatment partially reversed this response, though statistical significance was not achieved (p > 0.05) (Figure 10C,F). These in vitro findings, corroborating in vivo data, collectively demonstrate that PPD mitigates hyperglycemia-driven renal fibrosis by targeting the TGF-β1/Smads signaling axis.


## Discussion
  The primary pathogenic mechanisms of DN include inflammatory response, oxidative stress, apoptosis, autophagy, activation of the RAS, accumulation of advanced glycation end products (AGEs) and epithelial-mesenchymal transition (EMT). Unfortunately, current treatments are not yet able to fully stop the progression of DN. Chinese herbal medicine has received widespread attention due to its unique therapeutic advantages. Moreover, ginsenosides—the primary bioactive components of ginseng extract—exhibit protective effects by inhibiting inflammatory responses, reducing oxidative stress, and ameliorating fibrosis in DN.

  Multiple studies in vivo and in vitro have demonstrated that quercetin inhibits high glucose-induced ferroptosis in HK-2 cells via the Nrf2/HO-1 signaling pathway to protect against DN [21–23]. Furthermore, animal experiments have shown that the combination of quercetin and dasatinib can reduce podocyte dedifferentiation by activating autophagy and improving renal function in db/db mice [24]. Numerous studies have demonstrated that kaempferol can delay the progression of DN through multiple signaling pathways. Specifically, kaempferol prevents DN progression by upregulating the Nrf-2/HO-1 axis, which mediates antioxidant effects, and alleviates pathological changes in DN by downregulating TRAF6 expression. TRAF6 serves as a signal transducer in the Toll-like receptor 4 (TLR4) and NF-κB pro-inflammatory signaling pathway [25,26]. Another study found that kaempferol can alleviate DN by inhibiting the RhoA/Rho kinase-mediated inflammatory signaling pathway [27]. Collectively, these findings indicate that components within ginseng folium have significant potential for improving DN.

  In the main ingredients of ginseng folium obtained through our screening, Ginsenoside Rh2 can delay the progression of DN by inhibiting renal fibrosis and renal cell apoptosis [28]. Ginsenoside-Rg3 can improve DN in db/db mice by upregulating the PPARγ expression and downregulating biomarkers of inflammation and fibrosis [29]. The core components that play a protective role in DN include ginsenoside Rh2, ginsenoside-Rg3, protopanaxadiol, quercetin, and kaempferol. Specifically, PPD can alleviate pulmonary and liver fibrosis through multiple signaling pathways [10,30]. Therefore, it is reasonable to speculate that ginsenoside Rh2, ginsenoside Rg3, and PPD are likely the key components of ginseng folium responsible for its therapeutic effects on DN.

  There is limited research on the effects of Gypnoside V_qt on DN. However, studies have shown that other gypenosides can improve insulin resistance [31] and protect against diabetic retinopathy in DN mice. Specifically, Gypenoside A has been found to alleviate insulin resistance in high-fat diet-induced diabetic mice by inhibiting PDX1, which is closely related to pancreatic β-cell dysfunction [31]. However, whether Gypnoside V_qt also has protective effects on diabetes and DN remains to be explored. Additionally, there is limited research on the relationship between icosa-11,14,17-trienoic acid methyl ester and 9,12,15-tocotrienol, as well as dammar-20(22),24-diene-3β,6α,12β-triol, and their potential roles in diabetes and its complications. Therefore, further investigation is warranted.

  This study employs network pharmacology to explore the potential targets of ginseng folium in the treatment of DN and systematically analyzes the mechanism by which ginseng folium exerts its therapeutic effects on DN. The resulting PPI network comprises 251 target genes, among which are key targets such as CCL2, NFKB1, IFNG, CRP, IL1B, STAT3, ICAM1, PPARG, ALB, and NOS3. Ginseng folium acts through these key targets.

  Through PPI and molecular docking, we identified 10 key targets for ginseng folium in the treatment of DN. Our molecular docking simulations verified that the key targets, including CCL2, IL-1β, and PPARγ, exhibit strong binding activity with the core components of ginseng folium, such as Gypnoside V_qt, 20-(R)-ginsenoside Rh2_qt, ginsenoside-Rg3_qt, and PPD. Renal macrophage accumulation is related to renal cell death, renal fibrosis, and decline in renal function in DN [32]. The monocyte chemoattractant MCP1/CCL2 can serve as the main promoter of inflammation, renal injury, and fibrosis in DN [33], thereby promoting the accumulation of macrophages. IL1B encodes the pro-inflammatory cytokine IL-1β, which is significantly elevated in DN patients compared with healthy individuals. Secreted by immune cells and glomerular intrinsic cells such as podocytes, endothelial cells, and mesangial cells, IL-1β promotes DN progression and increases renal interstitial fibrosis following injury [34]. NF-κB, encoded by NFKB1, is a key mediator of inflammation activated through classical and non-classical pathways. Its activation mediates inflammasome activation, HIF signaling, and AMPK signaling, while inhibiting the SIRT1 pathway, which is closely related to noninfectious chronic diseases, thereby promoting DN development. The expression of NF-κB is increased in renal biopsies of DN patients [35]. Moreover, IL-6 levels are increased in DN mice. The target gene IFNG encodes the pro-inflammatory cytokine interferon gamma (IFN-γ). Serum levels of IFN-γ are significantly higher in DN patients compared to non-diabetic renal failure patients and diabetic patients without renal failure [36]. CRP is an inflammatory marker. Research using WT rat DN models has demonstrated that CRP inhibits podocyte autophagy by suppressing the C3a/C3aR signaling pathway, thereby accelerating DN progression [37]. STAT is a transcription factor involved in autophagy. Activation of the JAK/STAT pathway influences podocyte autophagy [38] and promotes extracellular matrix deposition in renal tubular epithelial cells [39], leading to renal fibrosis and accelerating the progression of DN.

  Renal fibrosis represents a cardinal pathological feature of DN and a deterministic endpoint in the progression to irreversible chronic kidney disease [40]. Hyperglycemia promotes the activation of the diabetic renal fibrosis program [41], leading to various pathological changes such as EMT, endothelial-mesenchymal transition (EndoMT), and activation of fibroblasts and pericytes. Histopathologically, DN kidneys exhibit glomerular basement membrane thickening, mesangial matrix expansion, and tubulointerstitial fibrosis, collectively driving the irreversible decline of renal function. Multiple signaling pathways, including TGF-β1, MAPK, Wnt/β-catenin, PI3K/Akt, JAK/STAT, and Notch, contribute to diabetic renal fibrosis. Cross-talk among these pathways drives fibrosis, so inhibiting them may alleviate renal dysfunction and delay the progression of DN [42].

  GO and KEGG pathway analyses have highlighted the AGE-RAGE and TNF signaling pathways as key mechanisms in DN. The AGE-RAGE pathway and PI3K/Akt, MAPK, and TGF-β1 signaling pathways play a crucial role in renal fibrosis. Targeting these pathways is a potential therapeutic strategy to ameliorate DN [40]. Therefore, we conducted both in vivo and in vitro experiments using PPD, a key active ingredient of ginseng folium. Additionally, we selected TGF-β1/Smads, the most classical signaling pathway for renal fibrosis, for verification. By gavaging PPD to db/db and db/m mice, we discovered that the expression of renal fibrosis marker TGF-β1, p-Smad3, and Smad4 in the PPD group was significantly decreased compared with the control group. Consistent with the in vivo experiments, in vitro experiments revealed that the increased expression of TGF-β1, p-Smad3 and Smad4 in HK-2 cells under HG conditions could be reversed after PPD treatment. All these findings suggest that PPD can ameliorate renal fibrosis in DN through the TGF-β1/Smads signaling pathway. Therefore, we conclude that the protective effect of ginseng folium on DN is mediated by its ability to ameliorate renal fibrosis.

  This network pharmacological study revealed that ginseng folium contains a diverse array of components, multiple targets, and signaling pathways underlying its protective effect on DN. Subsequent in vivo and in vitro experiments confirmed that PPD effectively attenuates renal fibrosis in DN via the TGF-β1/Smads signaling pathway. Notably, this study is the first to demonstrate the PPD-mediated amelioration of renal fibrosis. These findings lay a preclinical foundation for the translational application of ginseng folium in the treatment of DN. However, this study has limitations: only PPD was investigated in this study, whereas the roles of other components remain underexplored and require further research. The variation in sample sizes between db/m and db/db groups, though ethically justified under the 3 R principles, may introduce heterogeneity in statistical comparisons. Future studies should adopt standardized group sizes to enhance reproducibility. Additionally, the study relied on a single cell line and the db/db mouse model, which incompletely replicates advanced human DN pathophysiology. Future work should incorporate patient-derived cells or alternative models.


## Conclusion
  Numerous studies have explored the effects of ginseng root extract on DN, but limited research has focused on ginseng folium extract. This study establishes the therapeutic potential of ginseng folium extract in DN, demonstrating that its bioactive component PPD mitigates renal fibrosis through targeted inhibition of the TGF-β1/Smads signaling axis. By integrating network pharmacology predictions with experimental validation, we identified the therapeutic targets of PPD. Molecular docking revealed strong binding affinity to both TGF-β1 and its downstream effectors, Smad3 and Smad4. In vivo, PPD administration significantly suppressed TGF-β1, p-Smad3, and Smad4 expression in db/db mice renal tissues. Complementary in vitro experiments confirmed dose-dependent attenuation of TGF-β1/Smads signaling activation in HG-induced HK-2 cells. Demonstrating a protective effect of ginseng folium extract in DN could reduce therapeutic costs and broaden its clinical application in DN treatment. This study establishes a preclinical foundation for the use of ginseng folium extract in DN treatment. These findings bridge the gap between traditional herbal use and DN therapy.


## Authors’ contributions
  MX Yuan conceived and designed the study. CF Li designed the research and performed the analyses. CF Ma and RX Zhao performed the animal and cell study. XF Li and HC Yu interpreted the experiments results. All authors participated in the editing of the manuscript. All authors contributed to the article and approved the submitted version.


## Disclosure statement
  The authors declare that they have no conflicts of interest to disclose.


## Data availability statement
  The datasets analyzed in this study were obtained from the following publicly accessible databases. Traditional Chinese Medicine Systems Pharmacology Database and Analysis Platform (TCMSP, https://old.tcmsp-e.com/tcmsp.php), UniProt (https://www.uniprot.org/), ChemMapper (http://lilab-ecust.cn/chemmapper/), GeneCards (https://www.genecards.org/, Version 5.19), OMIM (https://www.omim.org/), Venny 2.1.0 (https://bioinfogp.cnb.csic.es/tools/venny/), DAVID 6.8 (https://david.ncifcrf.gov/), STRING platform (https://www.string-db.org/), PubChem database (https://pubchem.ncbi.nlm.nih.gov), and RCSB PDB database (https://www.rcsb.org).


## Acknowledgment
  Not applicable.