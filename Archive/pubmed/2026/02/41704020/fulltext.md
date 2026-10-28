# A Network‐Based Association of IBD and Colorectal Cancer Using Proteomics Data


## Background
  Colorectal cancer (CRC) is a major cause of morbidity and mortality, with chronic inflammation from inflammatory bowel disease (IBD) representing a well‐established risk factor. Clarifying shared molecular mechanisms may facilitate early detection and prevention strategies.


## Methods
  Proteomic data from the UK Biobank were analysed using the Olink proximity extension assay for seven CRC‐associated proteins (TFF3, TFF1, AHCY, RETN, LCN2, SELE and CEACAM5) previously identified via machine learning. Expression levels in CRC and IBD cases were compared with controls. Multilayer interaction networks, incorporating protein–protein, protein–metabolite and transcription factor–protein interactions, were generated using OmicsNet. Findings were validated in the Colonomics transcriptomic dataset.


## Results
  All seven proteins were significantly upregulated in CRC; six (excluding CEACAM5) were also elevated in IBD. Network analysis identified AHCY and LCN2 as central hubs linking inflammatory and metabolic pathways. NF‐κB and GATA2 emerged as recurrent transcriptional regulators. Colonomics validation confirmed upregulation of AHCY, LCN2 and SELE in CRC tissues.


## Conclusions
  This multi‐omics network analysis reveals a shared molecular framework between IBD and CRC, with inflammation as a key driver of colorectal carcinogenesis.


## Introduction
  Colorectal cancer (CRC) constitutes a significant global health challenge, ranking third in worldwide cancer incidence with 1.9 million new cases and over 900,000 deaths reported in 2022[1]. Incidence is higher in developed countries due to dietary habits and sedentary lifestyles [1, 2]. It is projected that CRC incidence is expected to reach 3 million by 2040, with developing nations experiencing a substantial increase linked to western lifestyle adoption and a rise in life expectancy [3].

  CRC arises through the gradual accumulation of genetic and epigenetic alterations, often from precancerous polyps such as adenomas and serrated polyps, which have high malignant potential [3]. The classical adenoma–carcinoma sequence involves APC, KRAS and TP53 mutations, while the serrated pathway is characterised by BRAF mutations and CpG island methylator phenotype (CIMP) progresses more rapidly following dysplasia [4, 5]. Another development pathway for tumorigenesis is chronic intestinal inflammation, particularly in the context of inflammatory bowel disease (IBD), where the inflammation‐dysplasia‐carcinoma sequence results from early TP53 mutations and chromosomal instability (Figure 1) [6, 7].

  Non‐modifiable CRC risk factors include age, gender and genetic syndromes such as lynch syndrome and familial adenomatous polyposis (FAP) [8]. Lynch syndrome involves germline mutations in mismatch repair genes, leading to microsatellite instability and a 30%–70% lifetime CRC risk [9]. FAP results from an inherited APC gene mutation, with nearly 100% lifetime risk of CRC if untreated [9]. Modifiable risk factors include smoking, alcohol, obesity, type 2 diabetes and diets high in red and processed meats [10, 11, 12, 13, 14, 15]. Oppositely, high fibre intake, physical activity and medications, like aspirin, display protective properties against CRC [16, 17, 18].

  Early detection through screening significantly reduces CRC mortality, with the faecal immunochemical test (FIT) now being the standard in the UK for individuals aged 54 to 74 [19, 20]. FIT has enhanced sensitivity compared to previous methods, resulting in better detection rates due to increased public uptake [21]. However, due to the nature of FIT being unpleasant the development of blood‐based markers and testing may increase early detection. Despite these advances, early‐onset CRC is rising in younger populations, often diagnosed at later stages due to symptom crossover with other gastrointestinal diseases [22, 23].

  IBD, including Crohn's disease and ulcerative colitis, is a chronic, incurable inflammatory disorder of the gastrointestinal tract and an established risk factor for CRC [24, 25]. As of 2019, IBD affects 4.9 million individuals worldwide, demonstrating a 47% increase in prevalence since 1990 [26]. Patients with extensive colitis or early IBD onset tend to face a significantly elevated CRC risk, up to 70% higher than the general population [24, 27]. Chronic inflammation from IBD drives epithelial damage, increasing mutation rates, which promotes carcinogenesis. Diagnostic delays are common for CRC as the symptoms like rectal bleeding and abdominal pain overlap with IBD flare‐ups.

  The intricate relationship between constant inflammation and the development of CRC is a pivotal area of research. While traditional molecular studies have found many potential biomarkers, they often do not fully represent the multifaceted nature of tumour biology. Multi‐omics integrates various high‐throughput omics technologies like genomics, transcriptomics, proteomics and metabolomics to provide a systems‐level overview of disease [28]. Multi‐omics techniques enhance cancer research by refining tumour classification, improving the understanding of disease mechanisms, facilitating biomarker discovery and optimising personal medicine [29, 30].

  Proteomics focuses on quantifying protein expression and interactions, crucial in CRC due to its heterogeneity [31, 32]. Transcriptomics analyses RNA expression and has contributed to defining consensus molecular subtypes (CMS1‐4) that differ in prognosis and treatment response [33]. Individual proteins do not function in isolation; they are integrated into complex networks involving other proteins, transcription factors and metabolites [34]. Understanding these networks is essential for revealing the mechanistic bridge between IBD‐driven inflammation and CRC progression.

  This study focuses on seven CRC‐associated proteins identified in the UK Biobank (TFF3, TFF1, AHCY, RETN, LCN2, SELE and CEACAM5) through machine learning‐based biomarker selection in a previous study by Radhakrishna et al. [35]. We hypothesise that these proteins are functionally interconnected within molecular networks and that elements of these networks also operate in IBD, suggesting shared mechanisms driving inflammation induced tumorigenesis.

  To explore this a multi‐omics approach was applied (1) the expression of the seven proteins in CRC and IBD using proteomic data from the UK Biobank, (2) constructed molecular interaction networks covering protein–protein, metabolite–protein and transcription factor–protein relationships using OmicsNet, (3) validated findings in independent datasets and (4) investigated how these networks may reflect inflammatory mechanisms that contribute to CRC development.


### Datasets and Methods Used
  The design of this multi‐omics study and analysis workflow is summarised in Figure 2. The study utilises proteomic data from the UK Biobank to identify protein expression patterns in CRC and IBD cases.


### Proteomic Data From the UK Biobank
  Data were obtained from the UK Biobank, a prospective population‐based cohort study comprising 500,000 individuals [36]. Participants aged 40–69 were recruited between 2006 and 2010 across 22 assessment centres in the United Kingdom, where they were selected based on geographic proximity. The cohort was followed longitudinally for a wide range of health outcomes, including cancer, cardiovascular disease and inflammatory conditions, producing a vast database of phenotypic and omics data that provides an ideal source for proteomics studies.


### Case and Control Data Matching
  CRC and IBD case and control cohorts were derived from UK Biobank using ICD‐10 diagnostic codes. A total of 9890 participants were identified to have CRC. This was further filtered with 6372 participants having CRC from multiple sources and 3518 from a single source. Of the 3518 CRC participants with a single source, the ICD‐10 were registered from different sources: 2737 hospital records, 382 self‐reported, 325 cancer registries and 74 death registries. Age and sex matched controls without ICD‐10 diagnosis for CRC diagnosis were selected using the MatchIt package in R. This resulted in a dataset of 19,784 participants (9890 case and 9894 controls). This was further filtered to data from 509 individuals with complete metabolite (as of July 2021) and proteomic (as of July 2023), as performed in Radhakrishnan et al. [35].

  For IBD, 1002 cases matched the inclusion criteria based on relevant ICD‐10 codes for IBD. These were compared to 51,486 healthy control individuals without a diagnosis of IBD. Proteomic data for CRC and IBD participants and controls were from plasma samples which were analysed using the Olink high‐throughput platform. Controls were healthy individuals with no diagnosis of CRC or IBD, selected from the UK Biobank. The data selection steps are shown in the Figure S10.


### Rationale for Protein Selection
  Seven proteins (TFF3, TFF1, AHCY, RETN, LCN2, SELE and CEACAM5) were selected for further analysis based on findings from a recent machine learning‐based study from Radhakrishnan et al. [35]. This study utilised machine learning LASSO, XGBoost and LightGBM classifiers with SHAP analysis to identify proteins that are the most predictive of CRC. These seven proteins continuously emerged as key biomarkers across multiple models.


### Construction of Molecular Interactions
  To investigate the molecular interactions associated with the seven target proteins (TFF3, TFF1, SELE, AHCY, RETN, LCN2 and CEACAM5), an in silico network‐based analysis was performed using OmicsNet 2.0 (https://www.omicsnet.ca/). OmicsNet 2.0 is a web‐based platform that enables multi‐omics data integration and interactive network visualisation [37]. Protein–protein, protein–metabolite and transcription factor–protein interactions were mapped to characterise the molecular associations of the seven selected proteins.

  The seven proteins were input as seed nodes to construct interaction networks. Protein–protein interactions were obtained from InnateDB [38], STRING [39], IntAct [40] and HuRI [41]. Metabolite protein interactions were from KEGG [42] and Recon3D [43]. Transcription factor–protein interactions were from TTRUST [44], ENCODE [45], JASPAR [46] and ChEA [47].


### Network Topology Analysis
  A network topology analysis was performed to explore the structural organisation of the interaction networks. Each network outputs the number of nodes and edges representing the interactions and seeds, which are the inputted proteins. Two centrality measures were applied: degree and betweenness [48].

  Degree centrality measures the number of direct connections a node has within the network, representing its local importance. Nodes with high degree values are considered to be hubs and often participate in biological functions due to their extensive direct interactions.

  Betweenness centrality is a global measure that quantifies how frequently a node is on the shortest path between other nodes. Unlike degree, it depicts a node's role in connecting network regions. Nodes with high betweenness may not have many direct links but often act as bridges or bottlenecks, facilitating the flow across functional modules [48].

  In this analysis, proteins exhibiting a high degree and betweenness were prioritised for further investigation, as their topological prominence suggests potential roles in molecular regulation, pathway integration or disease progression.


### Transcriptomic Validation via Colonomics
  Colonomics (https://www.colonomics.org/) is a multi‐omics database combining genotyping, DNA methylation, gene expression, miRNA expression, whole exome sequencing and copy number variations [49]. The dataset contains 100 paired tumour and adjacent normal tissues, which were collected 10 cm from the tumour margin, from patients diagnosed with stage II microsatellite stable (MSS) colon cancer. Additionally, 50 healthy colon mucosa samples were obtained from individuals who underwent colonoscopies and detected no lesions.

  Gene expression profiling was performed using Affymetrix microarrays. In this study, gene expression levels were investigated for each of the seven CRC associated proteins. Gene expression levels were compared across normal mucosa, adjacent tissue and tumour tissue to assess differential expression. Further analyses were conducted on gender, CMS, BRAF V600E mutation, KRAS mutation and CIMP status.

  These findings were subsequently used to validate the findings of the UK Biobank and deepen the understanding and biological relevance of the results.


### Statistical Analysis
  For the UK Biobank colon cancer dataset, descriptive statistics (mean ± standard error of the mean (SEM)) were calculated for the expression of seven proteins in case and control groups. For the IBD dataset, descriptive statistics (mean ± SEM) were calculated for six proteins. CEACAM5 was not found and considered missing. Protein expression values were normalised through autoscaling, where each value was transformed by subtracting the variable's mean and dividing it by its standard deviation (SD). This ensures a comparative analysis and reduces potential bias. Due to the large datasets, normality was assumed based on the Central Limit Theorem [50]. Therefore, a comparison between the case and control was conducted using a one‐tailed Student's t‐test to assess upregulation in protein expression for the case compared to the control. Proteomic statistical analyses were performed using R (version 4.4.2), and graphical visualisations were created using GraphPad Prism (version 10.4.2).

  For the Colonomics dataset, descriptive statistics (mean ± SD) were derived for gene expression across tissue types, molecular subtypes, mutation status and clinical features. We have used two‐tailed testing and FDR correction using the Benjamini–Hochberg (BH) method. Statistical significance was set at p < 0.05 (FDR corrected).


## Results

### Protein Expression in Colon Cancer
  Protein expression levels of seven CRC associated proteins (TFF3, TFF1, SELE, RETN, LCN2, AHCY and CEACAM5) were analysed in control and colon cancer samples from the UK Biobank. All seven proteins demonstrated significantly elevated expression in colon cancer cases compared to the control (p < 0.05) (Figure 3). TFF1 displayed the highest mean expression in both groups (colon cancer = 0.43 and control = 0.17), whereas SELE had the lowest average expression across both groups (colon cancer = 0.07 and control = −0.091). SELE, RETN, LCN2 and AHCY showed negative protein expression levels in control samples due to the normalisation of the dataset. Nevertheless, all CRC samples exhibited positive mean expression for all proteins.


### Protein Expression in IBD
  To investigate the potential intersection between CRC and IBD, the expression of six CRC associated proteins (TFF3, TFF1, AHCY, RETN, LCN2 and SELE) were analysed in IBD cases (n = 1002) and control (n = 51486) groups from the UK Biobank dataset (Figure 4). CEACAM5 was not detected in this dataset for IBD. All six proteins displayed a significant increase in expression for IBD samples (p < 0.05) compared to control samples. All control samples had negative or near zero expression, due to normalisation. LCN2 had the highest mean expression out of the IBD cases. These results present a strong upregulation of these six CRC associated proteins in IBD.


### Protein–Protein Interactions
  To explore molecular interactions between seven CRC‐associated proteins (TFF3, TFF1, AHCY, RETN, LCN2, SELE and CEACAM5), PPI networks were constructed using OmicsNet via four databases: InnateDB, STRING, IntAct and Huri.

  In InnateDB (Figure 5), 118 nodes and 117 edges formed three subnetworks. AHCY emerged as the central hub (degree = 52 and betweenness = 4375.5), followed by SELE, TFF1 and CEACAM5. TFF3 and RETN showed minimal connectivity (degree = 1). Key non‐seed interactors included SP1, ATF2, RELA and NF‐κB, indicating regulatory relevance.

  STRING (Supporting Information) generated the smallest and most fragmented network (31 nodes, 50 edges). Each protein formed isolated subnetworks. LCN2 was most connected (degree = 10), while CEACAM5, TFF1 and TFF3 had minimal interaction. RETN was not detected.

  IntAct (Figure 6) presented the largest and most integrated network (148 nodes, 195 edges). All seven proteins were included. AHCY and LCN2 were central across separate subnetworks. TFF1 showed moderate and RETN minimal connectivity. Notably, all seed proteins had nonzero betweenness, indicating both local and global network roles. Additional hubs included SGTA, UBQLN1 and UBQLN2

  HuRI (Supporting Information) formed a 66‐node network with three subnetworks. LCN2 again acted as a central hub (degree = 57). TFF1 and TFF3 were peripherally connected. RETN and AHCY each formed isolated single‐interaction subnetworks. SELE and CEACAM5 were not detected.

  In summary, AHCY and LCN2 consistently emerged as key hubs, with TFF3 and RETN showing low connectivity. Network structure and protein centrality varied by database, highlighting the need for multisource validation.


### Metabolite–Protein Interactions
  To investigate potential metabolite–protein interactions (MPIs), all seven CRC associated proteins (TFF3, TFF1, AHCY, RETN, LCN2, SELE and CEACAM5) were inputted into KEGG and Recon3D on OmicsNet (Figure 7). In both databases, only AHCY was found to interact with metabolites, forming a metabolic hub, while the other six proteins displayed no associations. In the KEGG MPI network (Figure 9A) AHCY interacted with six metabolites (S adenosylhomocysteine, homocysteine, adenosine, H2O, Se‐adenosylselenohomocysteine and selenohomocysteine). Centrality analysis revealed AHCY as a dominant hub with a degree of 6 and a betweenness centrality of 15. All six metabolites were peripheral nodes (degree = 1 and betweenness = 0), indicating AHCY as a central metabolic enzyme. The Recon3D network (Figure 9B) replicated these findings with the same six metabolites identified. AHCY also have the same degree and betweenness as well as the metabolites having the same centrality measures. This supports the robustness of AHCY metabolic interactions and reduces potential database bias. This reproducibility from independent metabolic databases reinforces the biological relevance of AHCY in CRC‐associated metabolism.


### Transcription Factor—Protein Interactions
  To investigate transcriptional regulation of seven CRC‐associated proteins (TFF3, TFF1, AHCY, RETN, LCN2, SELE and CEACAM5), transcription factor–protein interaction (TFPI) networks were generated using TTRUST, ENCODE, JASPAR and ChEA via OmicsNet.

  TTRUST (Supporting Information) produced 38 nodes across three subnetworks. The largest included TFF1, SELE, TFF3 and LCN2, linked to shared transcription factors (TF) such as RELA, NF‐κB, SP1 and STAT1. TFF1 was the most connected (degree = 17 and betweenness = 330.25), followed by SELE and TFF3. RETN and CEACAM5 formed smaller, minimally connected subnetworks, while AHCY was not detected.

  ENCODE (Supporting Information) revealed 122 nodes and 134 edges, with six proteins in the main network (AHCY, LCN2, TFF1, TFF3, SELE and CEACAM5). AHCY was the most transcriptionally regulated (degree = 67 and betweenness = 5241.7), followed by LCN2 and TFF1. RETN formed an isolated subnetwork with only two TFs (REST, LSMBTL2), indicating low regulatory integration.

  JASPAR produced a single 34‐node network with all seven proteins. AHCY, TFF1 and SELE showed the highest centrality (Figure 8). GATA2 was the most connected TF (degree = 6), regulating all seed proteins except LCN2, with higher centrality than some seed nodes. Other notable TFs included ESR1, NF‐κB and FOXF2.

  ChEA identified 120 nodes and 179 edges. AHCY, TFF1 and SELE again showed the highest centrality (Figure 9). GATA2 was a prominent TF across all proteins except LCN2. RETN remained the least connected.

  Overall, AHCY, TFF1 and SELE were the most transcriptionally regulated, while GATA2 and NF‐κB were recurrent key regulators across multiple datasets.


### Transcriptomics Validation Using Colonomics Dataset
  Transcriptomic validation of the seven CRC associated genes (TFF3, TFF1, SELE, RETN, LCN2, AHCY and CEACAM5) was performed using the Colonomics dataset in stage II microsatellite stable (MSS) colon cancer. Expression was analysed across tissue types, gender, molecular subtypes, tumour location and mutation status. TFF3 showed the highest expression in normal mucosa and was significantly downregulated in adjacent and tumour tissues (p < 0.001), while TFF1 followed a similar trend but without statistical significance. SELE displayed the lowest expression in normal tissue and was significantly upregulated in tumour samples (p < 0.001) (Figure 10). AHCY was downregulated in adjacent tissue but upregulated in tumour tissue (p < 0.001), indicating dynamic regulation. LCN2 was significantly elevated in tumour samples, whereas RETN and CEACAM5 showed stable expression with no significant changes. These expression patterns differed from UK Biobank proteomic data, where all seven proteins were upregulated in CRC patients.

  No statistically significant differences in gene expression were observed between male and female tumour samples (Supporting Information), suggesting that gender does not strongly influence transcriptional activity for these markers. When grouped by CMS (Figure 11), TFF3 was significantly elevated in CMS1 compared to CMS2 (p < 0.05), AHCY was higher in CMS2 and CMS3, and SELE was significantly increased in CMS4. The remaining genes did not show significant variation, implying more general CRC involvement. LCN2 was the only gene with a statistically significant difference based on tumour location, with higher expression in right‐sided tumours (p = 0.002). Expression of other genes differed minimally between left and right sides (Supporting Information). Analysis by CIMP revealed no significant expression differences between CIMP‐high and CIMP‐low groups (Supporting Information). Similarly, BRAF V600 (Supporting Information) mutation status did not significantly impact expression of any of the seven genes, however, TFF3, TFF1, SELE and LCN2 showed modest upregulation trends in mutant samples. Finally, KRAS mutation status showed that only SELE expression was significantly reduced in KRAS‐mutant tumours (p < 0.05), while the other six genes were unaffected (Supporting Information). Overall, these findings suggest differential regulation of specific CRC‐associated genes across tumour contexts, with notable variation in TFF3, SELE, AHCY, LCN2 and SELE particularly linked to subtype and mutation‐specific processes.


## Discussion
  This study aimed to investigate the molecular interplay between CRC and IBD through a multi‐omics approach, with a specific focus on seven previously identified CRC associated proteins (TFF3, TFF1, AHCY, RETN, LCN2, SELE and CEACAM5). The findings of this study verify the hypothesis, revealing significant upregulation of all seven proteins in CRC and six in IBD, then identifying AHCY and LCN2 as central network hubs. Furthermore, the overlap in regulatory nodes, particularly transcription factors such as NF‐κB and GATA2, suggests a shared inflammatory mechanism underlying both conditions. These results reinforce the concept of inflammation driven tumorigenesis and highlight potential associations that bridge chronic inflammation and colorectal carcinogenesis.


### Protein Expression and Functional Implications
  This study identified significant upregulation of seven CRC associated proteins (TFF3, TFF1, SELE, RETN, AHCY, LCN2 and CEACAM5) in CRC samples compared to controls from the UK Biobank. Furthermore, six of these proteins (except CEACAM5) also displayed significant upregulation in IBD patients in the UK Biobank. The simultaneous upregulation of these proteins in both conditions is consistent with the well‐established link between inflammation and tumorigenesis in the colon [51]. The finding that chronic inflammation drives an increase in pro‐tumorigenic protein supports the hypothesis that IBD associated molecular pathways can underpin the foundation for colorectal tumours.

  TFF3 and TFF1 were elevated in CRC, aligning with prior studies that show they are overexpressed in tumour tissues and patient serums [52]. TFF3 has been linked to aggressive cancers as it promotes the epithelial mesenchymal transition and invasion, correlating with poor survival [52]. This suggests that TFF3 in normal conditions protects mucosal integrity but may facilitate cancer progression when chronically overexpressed in inflammatory environments. TFF1's involvement within CRC appears to be more complex. TFF1 has previously been identified as a noninvasive urinary biomarker panel for early CRC detection [53]. However, evidence suggests that TFF1 may play a dual and context dependent role in CRC. Previous studies indicate that TFF1 possesses tumour suppressive properties, as overexpression in CRC cells reduces proliferation, motility and metastasis [54]. One study also reported TFF1 expression was associated with differentiated tumours and tumours lacking metastasis, suggesting TFF1 is linked with less aggressive disease [55]. This suggests that the upregulation could serve as an initial protective response to counteract tumour progression but may become dysfunctional over time, allowing for malignancy to proceed.

  LCN2 showed the highest expression out of the proteins in IBD samples and was also significantly elevated in CRC. LCN2 is an innate immune protein that increases during intestinal inflammation, like IBD, and is a biomarker of mucosal injury [56]. The upregulation of LCN2 in both conditions may be a host defence mechanism to maintain inflammation and prevent tumour progression. However, previous studies showed LCN2 decreases in the transition from long term ulcerative colitis to dysplasia contradicting the UK Biobank findings [57]. This inconsistency suggests the role of LCN2 may differ between inflammation driven and sporadic tumorigenesis where it is a protective factor in preneoplastic inflammation that is lost as the dysplasia develops.

  CEACAM5 was absent in the IBD dataset despite significant upregulation in CRC samples. CEACAM5 is a well‐established CRC biomarker in clinical use for diagnosis and prognosis. Higher CEACAM5 tumour expression is associated with worse outcomes [58]. CEACAM5's absence in IBD and elevation in CRC supports its specificity to differentiate between tumours and inflammation.

  RETN is an adipokine and inflammatory cytokine upregulated in CRC and IBD. This aligns with literature that IBD patients have higher circulating RETN compared to healthy individuals [59]. The upregulation in both conditions further reinforces the inflammatory environment's contribution to tumour biology.


### Molecular Interaction Network Analysis
  Network analysis revealed how these seven CRC associated proteins interact within broader molecular networks. Through the construction of PPIs, MPIs and transcription factor–protein networks, central hub nodes that may be involved in inflammation and CRC were identified.

  AHCY emerged as a central hub across protein–protein, metabolite–protein and transcription factor–protein networks. It demonstrated high connectivity in many networks (degree = 67 in ENCODE) and was the only protein directly interacting with metabolites, highlighting its central role. This importance aligns with AHCY's function associating cellular methylation through hydrolysing S‐adenosylohomocysteine (SAH) to adenosine and homocysteine. SAH is a methyltransferase inhibitor. Therefore, its removal promotes DNA, RNA and histone methylation, leading to epigenetic alterations, a key process in tumorigenesis [60]. Further supporting this, AHCY has been found to be upregulated in human CRC tissue and promotes tumour cell proliferation, invasion, angiogenesis and pro‐inflammatory signalling [61]. This, in combination with the upregulation of AHCY, means there is increased AHCY mediated breakdown of SAH, promoting methylation potential. This leads to altered transcriptional activity and epigenetic plasticity, which are hallmarks of cancer [62].

  LCN2 displayed multiple connections with inflammatory signalling pathways, like STAT3, NF‐κB and SP1. This supports LCN2's role as a key inflammatory mediator in transcriptional networks. LCN2's overexpression in intestinal epithelial cells promotes inflammation in colitis through triggering pyroptosis and epithelial damage through the NF‐κB/NLRP3/GSDMD pathway, contributing to an environment that supports tumour initiation [63]. It was also found to drive CRC progression through promoting IL‐6/STAT3/NF‐κB signalling, creating a positive feedback loop that sustains both inflammation and cell proliferation in colitis associated cancer models [64]. The interaction between SP1 and LCN2 has been previously demonstrated, with SP1 directly binding to the LCN2 promoter and enhancing its transcription under inflammatory conditions [65]. This transcriptional regulation supports LCN2's role as a functionally integrated proinflammatory mediator in mucosal inflammation.

  TFF3 was involved in the transcription factor networks more than protein networks. TFF3 displayed connections to NF‐κB in all transcription factor–protein networks except ENCODE. This interaction has been previously described with TFF3 transiently activating NF‐κB. The transient activation of NF‐κB through TFF3 does not lead to pro‐inflammatory factor induction through the upregulation of TWIST [66]. This suggests that TFF3 creates a feedback loop regulating inflammation, which fits the picture of the inflammatory background of both IBD and CRC.

  SELE and TFF1 demonstrated a moderate connection within the network with higher relevance in transcription factor–protein interactions. CEACAM5 showed lower connectivity but still connected within molecular networks; however, RETN was isolated in many of the network models, with them both playing more peripheral roles. This indicates that RETN's regulation is mainly independent of the core networks. This reflects RETN's role as a systemic inflammatory marker rather than a local protein in CRC pathways.

  Transcription factor analysis provided further insight into potential regulators linking inflammation and CRC. GATA2 emerged as a prominent transcription factor interacting with all seven proteins, except LCN2, across two networks with high centrality. It regulates angiogenesis, vital for tumour progression and GATA2 overexpression has been associated with advanced CRC and poor outcomes [67]. Mechanistically, GATA2 activates a miR‐31‐mediated pathway that represses SELE, reducing SELE mediated adhesion and migration of colon cancer cells, supporting its potential role as a regulatory hub influencing tumour progression and inflammation‐associated pathways in CRC [68].

  Overall, these networks indicate that the proteins upregulated in CRC and IBD are not working in isolation but are involved in complex, integrated pathways with distinct key hubs.


### Independent Validation Using the Colonomics Dataset
  Validation with the Colonomics dataset assists in the application of the findings. SELE, AHCY and LCN2 were significantly upregulated in colon tumour tissues compared to normal mucosa, mirroring the results of the plasma protein expression, strengthening their relevance as disease linked markers. This agreement reinforces the idea that these proteins are involved in CRC, not just anomalies. However, some proteins displayed discrepancies between systemic and tissue expression. TFF3 expression was downregulated in colon tumour samples and adjacent tissue compared to normal mucosa. This suggests the increased TFF3 in plasma may be due to inflammatory processes or tumour microenvironment rather than the tumour cells themselves. TFF3 demonstrated significantly higher expression in CMS1 compared to the canonical CMS2 subtype. This supports the link between IBD and CRC through CMS1 as the inflammatory subtype displayed the highest expression of TFF3, which is in line with the UK Biobank findings. AHCY demonstrated dynamic expression with significant upregulation in tumour tissue compared to normal mucosa, however, it demonstrated downregulation in adjacent tissue compared to normal mucosa. AHCY was also higher in CMS2 and CM3 compared to CMS1, which fits AHCY's role in metabolism and proliferation. TFF1, RETN or CEACAM5 did not display significant expression differences between tissue types, highlighting that these proteins may not play a significant role in stage II MSS colon cancer. This may be due to the use of stage II samples, as RETN expression is known to increase in later cancer stages [69].

  LCN2 was significantly higher in right‐sided tumours compared to left‐side. It has been found right sided CRC tend to experience more immune infiltration [70]. This aligns with previous studies linking LCN2 expression to increased infiltration of CD8+ T cells and macrophages [71]. This proposes that LCN2 may contribute to creating an immunologically active. SELE was higher in CMS4 and the only protein to differ by KRAS mutation status.

  None of the proteins showed significant differences by gender, CIMP or BRAF status, inferring that their expression patterns are not restricted to specific molecular subtypes. Further strengthening the relevance of these proteins representing core inflammatory and oncogenic processes rather than subtype specific alterations.


### Strengths and Limitations of this Study
  This study used robust and strong datasets, each presenting its strengths and limitations [72]. Through integrating proteomics and transcriptomics, it progresses beyond isolated expression profiles to examine proteins in their broader functional context. The use of a large cohort from UK Biobank increases the statistical power and robustness, followed by the independent Colonomics dataset which adds a layer of validation, strengthening the application of the findings. This study went beyond differential expression to explore molecular interaction networks, allowing the identification of functional hubs rather than relying only on expression magnitudes.

  Despite this, there are limitations to this study. The UK Biobank data are curated from plasma using Olink's PEA, which reflects systemic expression rather than tissue specific expression. The values are normalised and relative, reducing their ability for direct comparison to gene expression in Colonomics. The Colonomics dataset only includes stage II MSS tumours from 150 patients, meaning other disease states are not represented, such as late stage colon cancer or MSI tumours. The UK Biobank lacks clinical annotations on tumour location, therapy, IBD duration and disease course. This limits the ability to stratify results or to infer disease progression pathways. The IBD dataset lacked CEACAM5 detection and case and control were not matched.

  The databases within OmicsNet displayed inconsistencies with the networks produced, complicating the biological interpretation due to data curation differences. The use of Bioinformatic tools offers powerful exploration, which would not be achievable using conventional methods, but often lack experimental validation. Therefore, interactions and pathways are theoretical until confirmed in vivo or in vitro. The network analysis relied on centrality measures to identify central nodes, and while they are beneficial, they do not provide information on causality and the context of the connection.


### Future Research
  To build upon the findings of the study further research must be performed to enhance the biological relevance and translational potential. Initially, the in silico predictions require experimental biological validation. Key nodes like AHCY and LCN2 should be prioritised for functional studies in CRC models. For example, knockout models of these genes produced through CRISPR‐cas9 or siRNA of CRC cell lines (e.g., HCT116 and SW480) could reveal their roles in cell proliferation, apoptosis and inflammation associated signalling pathways. Overexpression studies of the peripheral proteins, like RETN and CEACAM5, in model systems may demonstrate oncogenic potential that is not obvious from the network alone. These gain and loss of function studies will help to confirm which proteins are drivers and which are passengers of the CRC process.

  Second, the generalisability of the results should be evaluated in more diverse populations and cohorts. Both datasets were based on European cohorts, therefore, validating the seven proteins in multi‐ethnic or larger cohorts like The Cancer Genome Atlas would be valuable. This could confirm whether the networks observed can be universally applied or if there are population differences. This approach would also enable subtype analysis, such as investigations into whether these networks can be applied to MSI tumours or colitis associated CRC.

  Third, longitudinal data to identify the proteomic changes during the transition from high risk groups, like IBD to CRC. This would help to understand if the proteins upregulated in CRC and IBD are predictors of malignant transformation or if they indicate the inflammatory state.

  Finaly, it is important to explicitly distinguish systemic or circulating biomarkers from tissue‐level expression profiles in our interpretation. Circulating protein levels do not necessarily reflect the expression of the corresponding genes in tumour cells or the tumour microenvironment. For example, Trefoil factors themselves are known to be highly tissue‐specific in their normal expression patterns TFF1 predominantly in gastric mucosa and TFF3 in intestinal goblet cells and their dysregulated expression in tumor tissue is well documented across multiple cancers (e.g., increased TFF3 or TFF1 in colorectal and other solid tumors), but these tissue patterns do not necessarily translate to equivalent changes in plasma [73]. Therefore, care should be taken when interpreting plasma proteomic signals as indicators of tumor cell biology; systemic biomarker fluctuations may reflect broader host responses or nontumor cellular contributions.

  Future studies should incorporate and adjust for confounders such as age, diet, BMI, smoking status and comorbidities, which all influence inflammation and cancer risk [74]. Adjusting for these parameters will clarify if observed differences are truly due to CRC and IBD and reduce bias.


## Conclusion
  This multi‐omics study provides a novel insight into the molecular architecture of CRC and the molecular interplay between chronic inflammation and CRC. The seven associated proteins identified from UK Biobank (TFF3, TFF1, AHCY, RETN, LCN2, SELE and CEACAM5) presented with upregulation in CRC and six of these are also elevated in an inflammatory condition (IBD). AHCY and LCN2 emerged as central hubs with interaction networks, implicating them in key associations involving inflammation, metabolism and epigenetic modification. The concurrent upregulation of six of these proteins in IBD highlights a potential inflammatory bridge between chronic colonic inflammation and malignant transformation, especially through NF‐κB, which was often involved in the networks.

  Validation with the Colonomics dataset supported the expression of several proteins, specifically with LCN2, SELE and AHCY, further strengthening their functional relevance. In conclusion, this research strongly supports the hypothesis that inflammatory and oncogenic pathways in the colon are linked through protein interaction networks. These results encourage further experimental validation and open the avenue for developing therapeutic targets for inflammation‐driven colorectal carcinogenesis. The integration of proteomic data with network biology and validation across independent cohorts could be applied to other complex disease intersections, ultimately improving our ability to intervene in CRC development and mechanistic aspects driven by chronic inflammation.


## Author Contributions
  J.D. and S.K.R. performed the data analysis and drafted the manuscript. A.A. conceived and designed the study. A.A. supervised and coordinated the study's design. L.B.M. and D.R. helped to get the data from Biobank. SM provided feedback on the analysis. D.R. and A.B.A. provided feedback on biological interpretation. N.D. and R.G. provided feedback on the draft and wrote first draft. All authors revised the manuscript, read and approved the final manuscript.


## Funding
  The authors have nothing to report.


## Conflicts of Interest
  The authors declare no conflicts of interest.


## Supporting information

## Data Availability Statement
  All the data is available online at https://www.colonomics.org/.


## Acknowledgments
  This research has been conducted using the UK Biobank Resource under application number 31224.