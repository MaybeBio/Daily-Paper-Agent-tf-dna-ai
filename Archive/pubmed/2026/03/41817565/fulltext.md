# Ferroptosis regulator NOX1 acts a diagnostic biomarker and mediates disease progression with the transcriptional regulation of STAT3 in glaucoma


## Purpose:
  Primary open-angle glaucoma (POAG) is the leading cause of irreversible blindness. Regrettably, the roles of ferroptosis-related (FR) genes in POAG remain elusive.


## Design:
  Five GEO data sets and a series of experimentations in vitro were used for bioinformatic exploration and biological validation.


## Methods:
  Using multiple machine learning algorithms, four critical FR genes in POAG progression were screened. The clinical value and biological function of NOX1 were comprehensively analyzed using bioinformatic approaches. A POAG in vitro model was constructed using H2O2 treatment. NOX1 effects on the viability of retinal ganglion cells (RGCs) and ferroptosis process were determined through CCK8, EdU, ROS detection, and transmission electron microscopy. Its upstream transcriptional mechanisms were determined through dual luciferase assays, and chromatin immunoprecipitation (ChIP).


## Results:
  NOX1 was identified as the critical FR gene in POAG progression and served as an effective diagnostic biomarker. High-NOX1 expression was tightly associated with increased infiltration levels of multiple subtypes of T cells, such as T cells CD8 and T cells CD4. However, the enrichments of eight metabolic gene sets did not differ between the POAG samples with high- and low-NOX1 expression groups. Silencing NOX1 maintained RGC survival and inhibited the ferroptosis process. Mechanistically, STAT3 upregulated NOX1 by binding its promoter region that was located at the 429th to 419th bases upstream of the NOX1 transcriptional start site. NOX1 overexpression reversed the inhibitory effects of silencing STAT3 on RGC survival and the ferroptosis process.


## Conclusions:
  NOX1 was a good biomarker for characterizing POAG and promoted POAG progression through STAT3-mediated transcriptionally activation.


## Methods

### Data source
  Five GEO data sets were used for a series of bioinformatic analyses in this study [Table 1]. Due to the maximum sample size of GSE9963 (n = 81), we selected it as the training cohort for identifying pivotal FR genes involved in glaucoma pathogenesis.


### Weighted gene co-expression network analysis (WGCNA)
  WGCNA was performed through multiple R packages, including ‘WGCNA,’ ‘MatrixStats,’ ‘Hmisc,’ ‘Foreach,’ ‘DoParallel,’ ‘Fastcluster,’ and ‘dynamicTreeCut.’ When merging the modules with similar expression proles, the threshold value was set as 0.25. When the optimal power value was determined, the model fit threshold was set as 0.8, while the higher connectivity the better.


### Machine learning algorithms
  Lasso regression analysis and support vector machine recursive feature elimination (SVM-RFE) aimed to screen potential hub genes in glaucoma progression. The former was conducted using the ‘glmnet’ R package and was based on the 10-fold cross-validation scheme.[11] The latter was conducted using ‘KeBABS’ R package.


### Diagnostic Meta-analysis
  Meta-analysis was fulfilled using the Review Manager 5.2 software (The Cochrane Collaboration, Oxford, UK). Odds ratio (OR) was adopted as the evaluation indicator. The heterogeneity was quantized through I2 value. The overall effectiveness was evaluated by Z-test. The funnel plots were used to detect the bias risk.


### Immune analysis and gene set enrichment analysis (GSEA)
  The immune effects of NOX1 were investigated through the CIBERSORT algorithm[12] and the single-sample gene set enrichment analysis (ssGSEA).[13] GSEA was applied to investigate metabolic effects of NOX1. Relevant gene sets were obtained from MSigDB database [Supplementary Table 1]. The number of permutations was set as 1000. There was no collapse in gene symbols.


### Prediction of regulatory mechanisms
  TRRUST, hTFtarget, and GeneCards databases were applied for predicting the upstream transcription factors (TFs) of NOX1.[141516] JASPAR database was used to predict the binding sites between TFs and the promoter region of NOX1.[17]


### Cell culture and in vitro cell model
  Mouse retinal ganglion cells (RGCs) (CP-M122) were purchased from the Procell Life Science and Technology Company (Wuhan, China). The recombinant lentiviral vectors of NOX1 and STAT3 were designed and synthesized by GenePharma (Shanghai, China) [Supplementary Table 2].

  A classical oxidative stress injury model was adopted to mimic glaucoma onset, which has been used extensively in various glaucoma studies.[1819202122] The modeling process was similar to the previous strategy[1819202122] as follows: RCGs were treated with 200 μM H2O2 for 12 h incubation.


### RT-PCR
  Total RNA was extracted using TRIzol Reagent (TakaRa, Japan) and reverse-transcribed into cDNA with the PrimeScript RT Reagent Kit (TaKaRa, Japan). RT-qPCR was then performed on an ABI Prism 7900 system using SYBR-Green PCR Reagent (Takara, Japan). Primer sequences are listed in Supplementary Table 3.


### Western blot
  Western blot assays were performed similar to the previous study.[23]


### EdU assay
  Cells were seeded in 96-well plates (1 × 103 cells/well), incubated with 50 μM EdU reagent for 2 h, and fixed with 4% paraformaldehyde for 15 min at room temperature.


### CCK8 assay
  Cells were seeded in 96-well plates (3 × 104 cells/well). After adding 10% CCK-8 reagent, cells were incubated for 1 h at 37°C, and the absorbance at 450 nm was measured.


### Transmission electron microscopy (TEM) detection
  Collected cells were fixed with 2.5% glutaraldehyde for 8 h, dehydrated through a graded ethanol series, and freeze-dried. Sample observation was performed by WEIPU testing company (Shanghai, China).


### ROS detection
  Cells were seeded in 12-well plates with a seeding density of 2 × 105 per well for 24 h incubation. 50 μM fluorescence dye BODIPY-C11 (581/591) (ABclonal Biotech company, Wuhan, China) was added in each experimental group, and cells were incubated for 1 h at 37℃. Flow cytometry was used to detect the cell proportion of fluorescence emission peak shifting from 590 nm to 510 nm.


### Dual luciferase assays
  The recombinant vectors were designed and synthesized+ by Hanheng biotechnology company (Shanghai, China). For detection, 50 μL cell lysate and 10 μL firefly luciferase reaction solution were mixed and added to the microplate. Firefly luciferase activity was measured first within 30 minutes. Next, 10 μL renilla luciferase reaction solution was added and renilla luciferase activity was measured. The ratio of two fluorescence intense was calculated for estimating binding site occupancies.


### Chromatin immunoprecipitation (ChIP)
  ChIP was performed using the BeyoChIP™ ChIP Assay Kit (P2080S, Beyotime, China). When HEK293T cells reached 90% confluency, they were cross-linked with the reagent and lysed with SDS buffer followed by ultrasonication. Using ultrasound, DNA was broken into 100–500 bp fragments. Specific antibody targeting STAT3 or normal mouse IgG were used to pull down the DNA immune complex.


## Results
  The flowchart of this study is presented in Fig. 1.

  The red arrow indicated that the four candidate genes were upregulated in POAG samples according to the differential expression analyses. FR, ferroptosis-related; ROC, receiver operating characteristic curve; PCA, principal component analysis; SVM-RFE, support vector machine recursive feature elimination; TEM, transmission electron microscopy; ROS, reactive oxygen species; ChIP, Chromatin immunoprecipitation.


### Ferroptosis regulatory genes have great performance to characterize POAG
  Using MSigDB and FerrDb database, we constructed a comprehensive ferroptosis gene set consisting of 253 members [Fig. 2a]. The PPI network of these FR genes is displayed [Fig. 2b]. Biological function analysis revealed that selected 253 genes were enriched in multiple biological processes, such as ferroptosis (WP4313), response to oxidative stress (GO: 006979), and reactive oxygen species metabolic process (GO: 0072593) [Fig. 2c]. These observations highlighted the reliability of our FR gene set.

  Next, we developed two cluster patterns for discriminating POAG patients and the normal population [Fig. 2d and e]. ROC confirmed that FR cluster patterns held a great variety of diagnostic abilities [Fig. 2f, AUC = 0.793). Moreover, FR clusters could explain up to 87.6% of differences in sample types [Fig. 2g].


### GCLC, NOX1, HSF1, and BECN1 are the potential diagnostic biomarkers of POAG
  50 FR DEGs are identified [Fig. 3a]. With the combined consideration of the fitness and connectivity, the optimal power value in WGCNA analysis was 4 [Fig. 3b and c]. The cluster dendrogram showed a low similarity between different hierarchical branches, revealing that each module harbors notable clustering features [Fig. 3d]. Furthermore, all modules were correlated with sample type [Fig. 3e]. Among that, brown and turquoise modules were screened for further analyses due to their higher correlation coefficients of 0.6 and 0.51 [Fig. 3e]. Following that, we obtained 14 and 4 eigengenes using Lasso regression and SVM-RFE analyses, respectively [Fig. 3f and g]. The intersection part between the above three screening approaches was obtained through a Venn diagram [Fig. 3h]. Their clinical heatmap is presented in Fig. 3i.


### NOX1 is superior in diagnosing POAG and is involved in multiple cellular biological processes
  Using the transcriptome and clinical data of GSE9963 dataset, we assessed the expressive trend and diagnostic accuracy of GCLC, NOX1, HSF1, and BECN1. All four genes were upregulated in POAG [Fig. 4a]. Their accuracies for diagnosing POAG ranged from 0.641 to 0.898, and NOX1 possessed the best diagnostic performance of 0.898 [Fig. 4b-e]. GO analyses revealed that the genes highly correlated with NOX1 (correlation coefficient ≥ 0.8) may be involved in multiple signaling processes [Fig. 4f-g].

  In addition, we found that plasma membrane and endosome were the main subcellular localization of NOX1 [Fig. 4h and i]. The three-dimensional protein structure of NOX1 provided some convenience for artificially synthesizing NOX1 agonist or inhibitor [Fig. 4j].


### Diagnostic ability of NOX1 is successfully tested in three validation datasets
  To confirm the NOX1 capacity for diagnosing POAG, we applied three validation datasets (GSE2378, GSE27276, and GSE101727) [Fig. 5a-f]. Clearly, a certain difference in NOX1’s diagnostic performance was observed among all datasets (0.540–0.898, Fig. 5g]. A meta-analysis showed that NOX1 expressive level and POAG onset were with high association degrees [Fig. 5h]. Besides, adjusted funnel plot showed no publication bias [Supplementary Fig. 1].


### NOX1 affects the immune microenvironment of POAG
  CIBERSORT results revealed that the infiltration levels of multiple T cell subsets were affected by NOX1 expressive levels [Fig. 6a-d]. For instance, the infiltration levels of T cells CD4 naïve, T cells follicular helper (TFH), and T cells gamma delta were increased in high-NOX1 expression group, whereas those of T cells CD4 memory resting and macrophage M1 and M2 were decreased [Fig. 6e].

  ssGSEA analyses indicated that NOX1 also affected the activities of immune-related pathways to some extent [Fig. 6f-i]. High NOX1 expression was concomitant with the increased activities of T cell function, APC function, and cytolytic activity signaling pathways [Fig. 6j]. Through literature review [Table 2], we found that affected immune cells and signaling pathways promoted POAG progression to varying degrees.


### NOX1 has limited effects on multiple metabolic processes in POAG
  The enrichment of pyruvate metabolism was not associated with NOX1 expression [Supplementary Fig. 2a-h]. Only one glycolytic set was related to high-NOX1 expression in GSE2378 dataset [Supplementary Fig. 2i-p]. Similarly, there were no significant differences in enrichments of cholesterol and glutamine metabolisms between high- and low-NOX1 expression groups [Supplementary Fig. 3a-p]. Despite the critical roles of the above metabolic processes in POAG pathogenesis [Table 3], NOX1 had extremely limited effects on the metabolic reprogramming.


### NOX1 is upregulated in POAG in vitro model and suppresses RGCs viability
  Specific sh-RNA and overexpression plasmid could effectively manipulate NOX1 expressions [Fig. 7a and b]. The mRNA expression of NOX1 was significantly upregulated in POAG cell model [Fig. 7c and d], line with its protein expression [Fig. 7e]. CCK8 assays revealed that NOX1 overexpression suppressed RGC viability, whereas silencing NOX1 possessed the protective effects [Fig. 7f]. The EdU assays showed the similar results [Fig. 7g and h].


### NOX1 promotes the ferroptosis process in POAG in vitro model
  Inhibiting NOX1 expression moderately increased the protein expressions of SLC7A11 and GPX4 in vitro model [Fig. 8a]. TEM further revealed that silencing NOX1 gave a remission on the above microstructural changes of ferroptosis [Fig. 8b]. ROS detections also confirmed that high levels of lipid peroxidation occurred in POAG, while NOX1 overexpression further elevated this process [Fig. 8c-f].

  CCK8 assays showed that Fer-1 intervention increased the cell viability under H2O2-modeling treatment [Fig. 8g]. The similar findings were observed in EdU detections [Fig. 8h and i]. Altogether, inhibiting NOX1 could maintain RGC viability in POAG progression through suppressing the ferroptosis process.


### STAT3 is the potential transcriptional regulator of NOX1 in POAG
  Using TRRUST, hTFtarget, and GeneCards databases, the potential transcription factors (TFs) were predicted [Fig. 9a]. STAT3 was significantly upregulated in four datasets, whereas STAT1 was either downregulated (GSE9963 and GSE2378) or expressively unchanged (GSE27276 and GSE101727) [Fig. 9b-e]. Moreover, STAT3 expression was positively correlated with NOX1 expression in four datasets [Fig. 9f-i]. Thus, STAT3 was speculated as the candidate TF of NOX1.

  Silencing STAT1 failed to downregulate NOX1 expression in H2O2 model, but STAT3 could achieve this [Fig. 9j]. Line with NOX1, STAT3 was also upregulated after H2O2 treatment [Fig. 9k]. Besides, STAT3-related recombinant vectors were able to alter STAT3 expressions and thus were used for subsequent analyses [Fig. 9l and m].


### STAT3 upregulates NOX1 expression through binding its promoter region
  Overexpression of STAT3 could increase NOX1 protein expression [Fig. 10a]. NCBI Gene database revealed that NOX1 was mapped to the antisense strand of chromosome X [Fig. 10b]. The motif sequence of STAT3 was obtained, which reflected the sequence feature of the binding site [Fig. 10c]. The possible binding sites between STAT3 and the promoter region of NOX1 were also predicted [Fig. 10d and e]. Dual luciferase assay confirmed that predicted sites 2 and 3 were the true binding sites between STAT3 and NOX1 [Fig. 10f]. Further ChIP assay indicated that the immunoprecipitated complex captured by protein A/G magnet beads contained a host of predicted site 3 sequence, but rare predicted site 2 sequence [Fig. 10g and h]. Thus, the detailed binding site was located at the 419th to 429th bases upstream of NOX1 TSS.


### Overexpression of NOX1 reverses the inhibitory effects of silencing STAT3 on POAG progression and ferroptosis
  STAT3 deletion maintained the viability of RGCs in POAG in vitro model [Fig. 11a]. The proportion of EdU-positive cells in STAT3 deletion group was also significantly higher than that in H2O2-modeling group [Fig. 11b and c]. Further rescue experiments revealed that overexpression of NOX1 could reverse the protective effects of silencing STAT3 on RGC viability in POAG model [Fig. 11a-c]. ROS assay showed that silencing STAT3 reduced the lipid peroxidation level in POAG model, whereas NOX1 overexpression reversed the above inhibitory effects [Fig. 11d].


## Discussion
  Ferroptosis is a novel pattern of programmed death, intimately connecting with oxidative stress and mitochondria dysfunction. Due to the fact that the above two factors deeply mediated POAG progression and neurodegeneration,[24] increasing numbers of studies have focused and confirmed the relationships between ferroptosis and POAG. For instance, Guo M et al.[10] have found that inhibition of ferroptosis promotes RGC survival in experimental optic neuropathies. Similarly, our findings also highlighted the critical roles of ferroptosis in POAG. NOX1 could aggravate POAG through increasing RGCs resistance to ferroptosis. Moreover, ferroptosis inhibitor Fer-1 was also able to relieve cell damage caused by H2O2-modeling treatment. Thus, targeting ferroptosis has great potential for treating POAG.

  Available evidence has witnessed that a host of immune factors participate in POAG pathogenesis. Yang X et al.[25] have found that the distribution and activity of T-Lymphocyte subset are altered in glaucoma samples. Moreover, the aggregation of residential immune cells in retina results in autoimmune-mediated ophthalmoneuritis, which leads to optic nerve injury in POAG.[26] Herein, we found that different NOX1 expressions were associated with the infiltrations of multiple immune cells, such as CD8 T cells, CD4 T cells, monocytes, and macrophages. In fact, it has been observed that NOX1 could worsen other diseases through affecting immune cell infiltration, such as atherosclerosis,[27] hypertension,[28] and gastrointestinal carcinoma.[29] Hence, our findings preliminarily depicted the immune outline of NOX1 in POAG.

  NOX1 is a member of NADPH oxidase (NOX) family, which is responsible for the catalytic one-electron transfer of oxygen to generate superoxide or hydrogen peroxide. Due to the pivotal functions of NOXs in the biological oxidation process and cell respiratory chain, NOXs have been recognized to act as the mediator in many human diseases, including neurodegenerative disorders,[30] cancers, and vascular diseases.[31] Herein, we identified NOX1 as an excellent biomarker for diagnosing POAG, and impaired cell survival of RGCs in POAG model. These findings expended the map of NOX family in human disease research. Recently, Yamamoto K et al.[32] have developed a novel Rho kinase inhibitor K-115 for neuroprotective treatment in glaucoma and the drug could markedly decrease the expression of NOX1, supporting the clinical applicable future of NOX1 inhibitor.

  To date, there is no available research elucidating the molecular mechanisms of NOX family in POAG progression. In the present study, we predicted and verified that STAT3 was an upstream transcription regulator of NOX1. Interestingly, some observations from previous studies unintentionally showed STAT3 functions in POAG. For instance, miR-93-5p protects RGCs in an acute ocular hypertension model through inhibiting STAT3 expression.[33] Opioids reduce neuroinflammation via STAT3-dependent pathway in the chronic glaucoma model.[34] Yang J et al.[35] have found that STAT3 expression increased with intraocular pressure (IOP). Similarly, we observed the upregulation of STAT3 in POAG in vitro model. Moreover, ChIP and luciferase assays revealed that STAT3 elevated NOX1 expression through binding the promoter region of NOX1. Our findings, to the best of our knowledge, were the first evidence for unveiling regulatory mechanisms of NOX1 in POAG, providing important clues for identifying new therapeutic targets.

  Naturally, several limitations should not be ignored in this study. First, only a H2O2-treated in vitro model was employed to mimic the pathophysiology of POAG. Animal models should be used to confirm the biofunctions of NOX1 and STAT3 in POAG. Second, NOX1 expressive trend needs to be further determined through clinical samples. Third, although we confirmed STAT3 could promote POAG progression through transcriptional upregulating NOX1, NOX1 regulatory mechanisms were imperfect. Whether any cofactors and signaling pathways involved in the above process still remained unclear. Thus, there was still a lengthy path for elucidating the roles of NOX1 in POAG.


## Conclusions
  NOX1 was identified as an excellent biomarker for characterizing POAG. In the in vitro model, overexpression of NOX1 led to RGC damage and promoted ferroptosis. Mechanistically, STAT3 drove POAG progression through transcriptionally upregulating NOX1. In conclusions, our findings confirmed the critical roles of STAT3-NOX1 axis in POAG progression, providing new insights into POAG treatment.


### Author contribution
  HW conceived and designed the study. FWZ, XRW and JXY analyzed and interpreted the data. FWZ, XRW and JXY wrote the manuscript. FWZ and XRW conduced the vitro experiments. HW, FWZ and XRW made revised version. All authors have read and approved the manuscript.


### Availability of data and materials
  The datasets used and/or analyzed in the current study are available from the corresponding author upon reasonable request.


### Ethics approval and informed consent
  The animal study was reviewed and approved by the Animal Ethics Committee of the Second Affiliated Hospital of Jilin University.


### Conflicts of interest
  There are no conflicts of interest.


## N/A

## Acknowledgements
  All authors would like to thank Jilin University for its support.