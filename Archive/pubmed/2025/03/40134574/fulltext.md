# Suppression of regulatory factor X 7 alleviates airway remodeling and inflammation in childhood asthma


## Objective:
  Childhood asthma is a chronic heterogeneous syndrome composed of distinct disease entities or phenotypes. This study was conducted to characterize regulatory factor X 7 (RFX7) in childhood asthma.


## Material and Methods:
  Two available transcriptome datasets (GSE65204 and GSE27011) were used to analyze regulatory factor X (RFX) family members in childhood asthma. Random forest, logistic regression, and linear support vector machine (SVM) analyses were performed to construct an RFX-based classification model. Airway smooth muscle cells (ASMCs) were induced through platelet-derived growth factor-BB (PDGF-BB) for an asthma in vitro model. RFX7 expression was measured through immunoblotting. RFX7 was knocked out by transfection of RFX7 small-interfering RNAs, and then airway remodeling and inflammation were assayed.


## Results:
  Among RFX family members, RFX3, RFX7, and RFX-associated protein displayed differential expression in childhood asthma versus healthy controls. Thus, SVM, logistic regression, and random forest-based machine learning models were built. The random forest model presented the best diagnostic efficacy (area under the curve [AUC] = 1 and 0.67 in discovery and verification sets). RFX7 was found to be effective in diagnosing childhood asthma (AUC = 0.724 and 0.775 in discovery and verification sets). In addition, RFX7 was overexpressed in PDGF-BB-stimulated ASMCs (✶✶P < 0.01). Silencing RFX7 remarkably attenuated the proliferative and migrative capacities of ASMCs with PDGF-BB stimulation (✶✶P < 0.01). In addition, RFX7 was positively related to neutrophil infiltration in childhood asthma, and its knockdown downregulated the levels of pro-inflammatory cytokines in PDGF-BB-stimulated ASMCs (✶✶P < 0.01).


## Conclusion:
  The findings of this study indicate that RFX7 is a novel molecule that is correlated with airway remodeling and inflammation in childhood asthma, providing insights into the mechanism underlying this disease and its potential clinical importance.


## INTRODUCTION
  Asthma remains a prevalent chronic non-communicable disease with reversible airflow obstruction, which affects approximately 350 million individuals and results in a notable socio-economic and health burden worldwide.[1] Children are more susceptible to asthma due to their immature physical development and immune systems.[2] As a dominating chronic inflammatory disease in childhood, the estimated prevalence of childhood asthma ranges from 2.6% to 30.5%,[3] which continues to increase in many regions and countries, particularly in low-and middle- income countries.[4] Several risk factors for childhood asthma have been investigated, for example, parental asthma, childhood overweight or obesity, and preterm birth.[5-7] Asthma symptoms range from mild to severe, with a multifactorial etiology that begins in the fetal period.[8] At present, mild asthma can be controlled; nonetheless, severe asthma remains an alarming burden. Improving childhood asthma control is an urgent need globally, particularly in less affluent countries.[9] Serious distortion of airway smooth muscle cells (ASMCs) represents a frequent phenomenon of severe asthma.[10] Asthmatic ASMCs play a role in hyperresponsiveness as well as inflammatory and remodeling processes.[11,12] In addition, aberrant ASMCs in asthma can result in hyperplasia, hypertrophy, and the secretion of inflammatory mediators and extracellular matrix (ECM) proteins.[13-15] Hence, the development of effective treatment regimens needs an in-depth understanding of the machinery of asthmatic ASMCs.

  Childhood asthma is a highly heterogeneous syndrome composed of diverse disease entities or phenotypes, which is due to complex gene-gene and gene-environment interactions.[16] Regulatory factor X (RFX) family members share a highly conserved winged-helix DNA-binding domain that recognizes X-box DNA motifs, which were first discovered in mammals.[17] RFX transcription factors protect major histocompatibility complex class II genes against epigenetic silencing by DNA methylation.[18] One DNA microarray profiling-based study indicated that RFX genes mediate antigen processing and presentation pathways in childhood asthma.[19] RFX5 is a close relative of RFX7, and the expression of most RFX genes is limited to specific cell types. RFX1, RFX5, and RFX7 show universal expression.[20] RFX7 has emerged as a tumor suppressor,[21] which can be activated by p53 and cellular stress (DNA damage, ribosomal stress, etc.) across diverse cell types.[20] In addition, RFX7 hinders the metabolic activity of natural killer cells as well as facilitates their maintenance and immunity.[22] Nonetheless, RFX7 is uncharacterized in childhood asthma. In addressing the aforementioned limitation, the importance and potential transcriptional mechanisms in childhood asthma were systematically assessed in this study.


## MATERIAL AND METHODS

### Data acquisition
  Microarrays of 36 atopic asthmatic and 33 non-atopic nonasthmatic children were acquired from GSE65204 of the Gene Expression Omnibus (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE65204).[23] The dataset was based on the GPL14550 platform. Microarrays of 36 childhood asthma and 18 controls were also collected from GSE27011 (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE27011).[24,25] The microarray data were converted from logarithm to base 2. GSE65204 and GSE27011 were adopted as discovery and verification sets, respectively.


### Differential expression analysis
  Limma software (R 3.6.1 software) package powers differential expression analysis for microarray and RNA-sequencing data.[26] Asthmatic and non-asthmatic groups were compared using the package. Differentially expressed genes (DEGs) were selected on the basis of fold change >1.2 and P < 0.05.


### Enrichment analyses of Gene ontology (GO) and Kyoto Encyclopedia of Genes and Genomes (KEGG) pathways
  Clusterprofiler package (×4) can automate biological term classification and enrichment analysis of specified genes.[27] Through running this package, GO and KEGG pathway enrichment analyses of DEGs were implemented. Terms or pathways with P < 0.05 were considered significantly enriched.


### Gene set variation analysis (GSVA)
  GSVA, a gene set enrichment approach (GSEA), provides enhanced power to evaluate the variation in pathway activity in an unsupervised manner.[28] Based on the RFX family members, the single–sample GSEA (ssGSEA) score of the RFX signature was estimated.


### Machine learning
  Scikit-learn (https://scikit-learn.org/stable/), a Python machine learning library, was adopted for random forest, logistic regression, and linear support vector machine (SVM) analyses to establish an RFX-based classification model. The performance was evaluated on the basis of the receiver operating characteristic (ROCs) curves, with subsequent estimation of the area under the ROCs.


### Cell culture and treatment
  Human ASMCs (CTCC-056ASMC, Pubebio, Wuxi, China) were maintained in Dulbecco’s Modified Eagle’s Medium (Solarbio, Beijing, China) composed of 10% fetal bovine serum (FBS; S9020, Solarbio, Beijing, China) with 1% penicillin/streptomycin (P7630, Solarbio, Beijing, China) in a 5% Carbon dioxide incubator (Scientific 8000, Thermo, USA) at 37°C. The culture medium was changed every three days. To establish an asthma cell model, ASMCs were administrated with 50 ng/mL platelet-derived growth factor BB (PDGF-BB; abs05159, Absin, Shanghai, China) for 24 h.[29] Cell lines were authenticated by the Genomics Unit at Clinical Laboratory Management Association (CLMA), using short tandem repeat profiling (AmpFLSTR ldentifler Plus polymerase chain reaction [PCR] Amplification Kit; Applied Biosystems 4427368). A mycoplasma test was performed in all cell lines every other week using the MycoAlert Mycoplasma Detection Kit (LT07–710, LONZA, USA).


### Western blot
  ASMCs were mixed with radio-immunoprecipitation assay buffer (P0013B, Beyotime, Shanghai, China) combined with protease and phosphatase inhibitors (ST505, Beyotime, Shanghai, China), with subsequent homogenization at 4°C for 30 min. Following centrifugation, supernatant samples were collected. Protein concentration was tested by utilizing a bicinchoninic acid reagent (BL521A, Biosharp, Beijing, China). A total of 20 μg of proteins was subjected to sodium dodecyl sulfate-polyacrylamide gel electrophoresis, with subsequent transference onto nitrocellulose membranes (HATF00010, Millipore, Boston, USA). A primary antibody targeting RFX7 (1 μg/mL, Rabbit; A303–062A, Thermo Fisher Scientific, USA) or glyceraldehyde-3-phosphate dehydrogenase (GAPDH; 1/10000; Rabbit; ab181602; Abcam, Boston, USA) was adopted in accordance with the manufacturer’s specifications. Horseradish peroxidaseconjugated goat anti-rabbit immunoglobulin G (IgG) (1/5000; ab97051; Abcam, Boston, USA) was utilized as the secondary antibody. Enhanced chemiluminescence reagent (ECL) (Millipore, Bedford, MA) was used to visualize protein bands. Such protein bands were developed on a ChemiDoc XRS system (Bio-rad, Hercules, USA). Quantitative analyses were conducted using ImageJ software (National Institutes of Health, Maryland, USA).


### Transient transfection
  Small interfering RNAs (siRNAs) against RFX7 (which is known as small interfering RFX7 [si-RFX7]) and their controls (small interfering-negative control [si-NC]) were synthesized on the basis of GenePharma (Shanghai, China). The transfection sequence is presented as follows: (si-RFX7-1: AGUUCUUGAUCUUGUGUUGCA CAACACAAGAUCAAGAACUCC; siRFX7-2: UUAGAUUGUACAGUUUUGCAG GCAAAACUGUACAAUCUAAAG; siRFX7-3: UUUAGAUUGUACAGUUUUGCA CAAAACUGUACAAUCUAAAGU; siRNANC: UUCUCCGAACGUGUCACGUTT ACGUGACACGUUCGGAGAATT). ASMCs were seeded onto six-well plates (2 × 105 cells/mL). When confluence reached 80%, transient transfection was conducted by using Lipofectamine 3000 (L3000150, Invitrogen, Carlsbad, USA) in accordance with the manufacturer’s procedures. ASMCs were gathered following 48-h transfection for subsequent experiments.


### 5-Ethyny-2'Edeoxyuridine (EdU) assay
  ASMC proliferation was evaluated using the EdU assay. ASMCs were seeded onto a 24-well plate. Subsequently, they were exposed to a fresh medium supplemented with 50 nM EdU reagent (C0075S, Beyotime, Shanghai, China) for 2 h at 37°C, with subsequent fixation by 4% paraformaldehyde (P0099, Beyotime, Shanghai, China). After staining with Hoechst 33258 (C1017, Beyotime, Shanghai, China), ASMCs were subjected to fluorescence microscopy (IX73, OLYMPUS, Germany).


### Wound healing assay
  ASMCs were inoculated into six-well plates (2 × 106/well) and then mechanically disrupted utilizing a sterile 200 μL pipette tip, thereby creating a linear wound. After rinsing with phosphate-buffered saline, the wells were filled with a culture medium without FBS and then further incubated for 48 h. Under a light microscope (Zeiss), photographs were acquired at appropriate times, and closure ratios were estimated using ImageJ software.


### Transwell assay
  Transwell filter chambers with an 8-μm pore (Corning, New York, USA) were adopted for migration evaluation. ASMCs (4 × 105 cells/mL) in a serum-free medium were planted onto the upper well of the chamber, with 500 μL of culture medium supplemented with 10% FBS added to the lower well. Subsequently, cells were continuously incubated for 24 h. Then, migrated cells were fixed in 4% paraformaldehyde (Beyotime) for 15 min and dyed with 0.1% crystal violet reagent (Beyotime) for 15 min. Furthermore, the migrated cells were photographed by using a light microscope (XDS-1A, Shanghai Precision Scientific Instrument Co., LTD., China). The data were analyzed using ImageJ software.


### Immunofluorescent staining
  ASMCs were fixed in 4% paraformaldehyde for 15 min, with subsequent permeabilization with 0.3% Triton X-100 (P0096, Beyotime, Shanghai, China). Following administration with 5% bovine serum albumin buffer (ST2249, Beyotime, Shanghai, China), ASMCs were incubated with a primary antibody against alpha-smooth muscle actin (α-SMA; 1/250; ab124964; Abcam, Boston, USA), N-cadherin (1/250; ab18203; Abcam; Boston, USA), or E-cadherin (1/250; ab40772; Abcam; Boston, USA) overnight at 4 °C. Afterward, they were exposed to goat anti-rabbit IgG H&L Alexa Fluor 488 (1/200; ab150077; Abcam; Boston, USA) or Alexa Fluor 647 (1/200; ab150079; Abcam; Boston, USA) for 1 h at room temperature. Subsequently, coverslips were dyed by Hoechst 33258. Slides were mounted and detected using a fluorescence microscope (OLYMPUS IX73, Japan).


### Reverse transcription quantitative PCR (RT-qPCR)
  Total RNA extraction was achieved using TRIzol (15596018CN, Invitrogen, USA) in accordance with the manufacturer’s procedures. Complementary DNA was synthesized using the PrimeScript RT reagent Kit (K1622, Thermo, USA). Subsequently, RT-qPCR was implemented using synergetic binding reagent (SYBR) Premix Ex Taq II (F-415XL, Thermo, USA) on ABI (real-time fluorescence quantitative PCR instrument) 7500 Real-Time PCR System (ABI7500, ThermoFisher, Waltham, USA). The primers used were as follows: tumor necrosis factor alpha (TNF-α), 5'-TCTTCTCCTTCCTGATCGT-3' (sense), 5'-GCTACAGGCTTGTCACTC-3' (antisense); interleukin (IL)-1 beta, 5'-ATGACCTGAGCACCTTCT-3' (sense), 5'-GGACCAGACATCACCAAG-3' (antisense); IL-6 (IL-6), 5'-TGAGAGTAGTGAGGAACAAG-3' (sense), 5'-CGCAGAATGAGATGAGTTG-3' (antisense); GAPDH, 5'-CATCACCATCTTCCAGGAG-3' (sense), 5'-AGGCTGTTGTCATACTTCTC-3' (antisense). Relative expression values were estimated using the 2−ΔΔCT approach.


### Transcription factor prediction
  TRANSFAC is a database on transcription factors, as well as their genomic binding regions and DNA-binding profiling (http://transfac.gbf.de/TRANSFAC/).[30] Based on the database, transcription factors of RFX7 were inferred.


### Data analysis
  GraphPad Prism 9.0.1 (GraphPad Software, San Diego, CA) was used for statistical analyses and plotting the data. All values were presented as the means ± standard deviation. Student’s t-test or one-way analysis of variance was utilized to assess the significance of differences with the LSD post hoc test. Correlation analysis was achieved using a Pearson test. P < 0.01 indicated statistical significance. All experiments were repeated three times.


## RESULTS

### Aberrant transcriptome programs in children with persistent atopic asthma
  In this study, transcriptome profiling of 36 children with persistent atopic asthma and 33 healthy children was performed. First, the characteristics of childhood asthma were investigated using the transcriptome program. The DEGs were selected in childhood asthma versus healthy controls. Consequently, 341 DEGs presented notable downregulation, with 361 presenting a notable upregulation in childhood asthma [Figure 1a and b]. In particular, the first 20 down-or upregulated DEGs are shown in Figure 1c and Table 1. Subsequently, the biological roles of the DEGs were evaluated. The biological processes underlying asthma include ECM organization, epidermal development, secretion by cells, response to wounding, peptidase activity, and fibroblast growth factor receptor signaling pathway [Figure 1d]. Cellular components such as extracellular vesicles or exosomes, integral components of membrane, plasma membrane, collagen-containing ECM, secretory granules, or vesicles may be modulated by DEGs [Figure 1e]. In addition, such components may possess key molecular functions such as protease binding, anion transmembrane transporter activity, and symporter activity [Figure 1f]. The crucial KEGG pathways, for example, oxidative phosphorylation, thermogenesis, ECM–receptor interaction, bile secretion, and metabolic pathways, were remarkably enriched by the DEGs [Figure 1g]. These findings unveil the key functions of the DEGs in childhood asthma.


### Machine learning models based on RFX family members for diagnosing childhood asthma
  Among RFX family members, RFX3, RFX7, and RFX-associated protein (RFXAP) presented differential expression in childhood asthma. On the basis of RFX3, RFX7, and RFXAP, the RFX ssGSEA score in childhood asthma and control specimens was estimated. The RFX ssGSEA score was remarkably higher in childhood asthma than in controls [Figure 2a and b], indicating the activation of RFX in childhood asthma. Thus, RFX family members can be used to diagnose childhood asthma. In addition, SVM, logistic regression, and random forest-based machine-learning models were established. Subsequently, the diagnostic efficacy was evaluated. In the discovery set, the AUC values of the SVM, logistic regression, and random forest-based models were 0.83, 0.83, and 1.00, respectively [Figure 2c-e]. Reproducibility was further proven in the verification set. Consequently, the AUC values of the SVM, logistic regression and random forest-based models were 0.58, 0.64, and 0.67, respectively. Overall, the random forest-based model presented the best diagnostic efficiency in childhood asthma. The efficiency of single RFX family members in childhood asthma diagnosis was also assessed. The AUC values of RFX3, RFX7, and RFXAP were 0.657, 0.724, and 0.766, respectively, in the discovery set, and 0.617, 0.775, and 0.566, respectively, in the verification set [Figure 2f-h]. Only the larger area under the curve of the G-chart indicates that RFX7 has the most favorable diagnostic effect on childhood asthma. Hence, among the RFX family members, RFX7 had the most favorable efficacy in diagnosing childhood asthma.


### RFX7 presents remarkable overexpression in asthma cell models
  A total of 50 ng/mL PDGF-BB-induced ASMCs were utilized for the establishment of asthma cell models. RFX7 expression was greatly activated in PDGF-BB-induced ASMCs versus control [Figure 3a and b]. For further evaluating the role of RFX7 in asthma, three specific siRNAs targeting RFX7 were transfected into ASMCs. RFX7 was efficiently knocked out in ASMCs by its siRNAs compared with si-NC [Figure 3c-e]. Considering that RFX7 siRNA#3 had the best knockout effect, it was used for follow-up experiments.


### Suppression of RFX7 alleviates PDGF-BB-induced ASMC proliferation
  The improved proliferative capacity of ASMCs is greatly linked with asthma.[12] As expected, ASMC proliferation was prominently heightened in the context of PDGF-BB stimulation [Figure 4a and b]. In addition, we focused on whether RFX7 influenced PDGF-BB-stimulated ASMC proliferation. As a result, RFX7 knockdown efficiently alleviated the proliferative ability of ASMCs in the context of PDGF-BB.


### RFX7 knockdown ameliorates ASMC migration stimulated by PDGF-BB
  The excessive migration of ASMCs directly results in airway remodeling in asthma.[31] The migrative capacity of ASMCs was evaluated using wound healing and Transwell assays. Consequently, closure ratios were greatly improved by PDGF-BB stimulation in ASMCs [Figure 5a and b]. RFX7 inhibition efficiently attenuated the closure ratios of ASMCs under PDGF-BB administration. In addition, the number of migrative ASMCs was prominently elevated following PDGF-BB administration [Figure 5c and d]. RFX7 suppression greatly reduced the number of migrative ASMCs stimulated by PDGF-BB. Hence, silencing RFX7 impaired ASMC migration under PDGF-BB stimulation.


### Silencing RFX7 weakens PDGF-BB-stimulated ASMC remodeling
  An in-depth assessment was conducted to determine the influence of RFX7 on ASMC remodeling. α-SMA [Figure 6a and b] and N-cadherin [Figure 6c and d] levels displayed a remarkable increase in ASMCs with regard to PDGF-BB stimulation. Meanwhile, E-cadherin levels presented a reduction in PDGF-BB-stimulated ASMCs [Figure 6e and f]. RFX7 suppression efficiently decreased α-SMA and N-cadherin levels as well as increased E-cadherin levels in PDGF-BB-induced ASMCs. The abovementioned data indicated that silencing RFX7 alleviated PDGF-BB-stimulated ASMC remodeling.


### Targeting RFX7 decreases inflammatory response in PDGF-BB-stimulated ASMCs
  RFX ssGSEA score and RFX7 positively correlated with neutrophil infiltration in childhood asthma [Figure 7a]. Pro-inflammatory cytokines: TNF-α, IL-1 β, and IL-6 presented notably elevated levels in ASMCs with regard to PDGF-BB administration [Figure 7b-d]. RFX7 suppression efficiently decreased the levels of TNF-α, IL-1 β, and IL-6 in ASMCs stimulated by PDGF-BB. Collectively, RFX7 silencing decreased inflammatory response in PDGF-BB-induced ASMCs


### Prediction of the transcription factors of RFX7
  A total of 59 transcription factors of RFX7 were estimated, including AT-rich interaction domain 3A, bromodomain containing 2, bromodomain containing 4, cyclin dependent kinase 7, cyclin-dependent kinase 9, CCAAT enhancer-binding protein beta, cAMP responsive element-binding protein 1, CREB-binding protein, CCCTC-binding factor, CCCTC-binding factor like, E2F transcription factor 6, E74 like ETS transcription factor 1, ETS proto-oncogene 1, transcription factor, Fli-1 proto-oncogene, ETS transcription factor, Forkhead box A2, Forkhead box P1, GATA-binding protein 1, host cell factor C1, histone deacetylase 2, Hes-related family bHLH transcription factor with YRPW motif 1, hepatocyte nuclear factor 4 alpha, hepatocyte nuclear factor 4 gamma, lysine acetyltransferase 2B, lysine demethylase 5B, KLF transcription factor 9, lamin B1, MYC-associated zinc finger protein, mediator complex subunit 12, MYB proto-oncogene, transcription factor, myogenic determining factor 3, nuclear factor I C, Notch receptor 1, Paired box 5, PHD finger protein 8, RNA polymerase II subunit A, POU class 2 homeobox 1, RAD21 cohesin complex component, RB-binding protein 5, histone lysine methyltransferase complex subunit, RUNX family transcription factor 3, Retinoid X receptor gamma, SET domain bifurcated histone lysine methyltransferase 1, SIN3 transcription regulator family member A, structural maintenance of chromosomes 1A, structural maintenance of chromosomes 3, Sp4 transcription factor, Spi-1 proto-oncogene, SRC protooncogene, non-receptor tyrosine kinase, serum response factor, STAG1 cohesin complex component, signal transducer and activator of transcription 1, TATA-box-binding protein-associated factor 1, TATA-box-binding protein, transcription factor 3, transcription factor AP-4, tumor protein p63, upstream binding transcription factor, WD repeat domain 5, YY1 transcription factor, and zinc finger protein 263 [Table 2]. RFX7 might be transcriptionally modulated by the above-mentioned transcription factors.


## DISCUSSION
  The etiology of asthma is complex, covering complicated genetic and environmental factors.[32] Nonetheless, the mechanisms underlying the disease need definitive characterization. In this study, the transcriptome program features of childhood asthma were unveiled, and a machine learning RFX-based model was built for childhood asthma diagnosis. The random forest model presented the most excellent diagnostic efficiency, which might be applied in clinical practice. The favorable efficacy of RFX7 in diagnosing childhood asthma was also proven.

  Airway smooth muscle response exerts a crucial significance in asthma. For example, the crosstalk of CD34+ fibrocytes with ASMCs (a dominating structural component of the airway) triggers IL-8 generation and activates the Akt (Serine/threonine kinase 1)/PRAS40 (Proline-rich AKT substrate)/mTOR (mechanistic target of rapamycin kinase) pathway in asthma.[33] During the pathologic development of asthma, the proliferation and migration of ASMCs can be elicited by distinct stimuli (such as PDGF-BB), thereby increasing ASM thickness and inducing airway wall remodeling. Hence, suppressing aberrant ASMC proliferation and migration is a potential therapy against asthma. PDGF-BB can be secreted by activated platelets and endothelial, epithelial, glial, and inflammatory cells, which has been proven as a dominating stimulus for promoting ASMC proliferation and hypertrophy as well as ASMC migration.[34] The expression level of RFX7 was greatly elevated in PDGF-BB-stimulated ASMCs. Silencing RFX7 attenuated the proliferative and migrative capacities of ASMCs with regard to PDGF-BB. In addition, RFX7 inhibition efficiently decreased α-SMA and N-cadherin levels as well as increased E-cadherin levels in PDGF-BB-induced ASMCs. Accordingly, therapeutic targeting of RFX7 might be a potential therapeutic regimen for childhood asthma.

  Asthma symptoms are triggered by airway inflammation, inducing multiple processes, for example, mucus generation, airway wall remodeling, and bronchial hyperresponsiveness.[35] Airway neutrophil infiltration has been extensively proven to be associated with asthma severity.[36] Notably, neutrophil infiltration is associated with asthma that is unresponsive to corticosteroids, a mainstay of asthma therapy.[37] Nevertheless, effective regimens to alleviate neutrophilic airway inflammation in serious asthma remain elusive. Our data indicated that RFX7 presented a positive interaction with neutrophil infiltration in childhood asthma. The pathological characteristics of asthma include persistent airway inflammation, infiltration of inflammatory cells, and the release of pro-inflammatory cytokines and mediators.[38] TNF-α, IL-1 β, and IL-6 are potent inflammatory cytokines that result in airway inflammation, influencing therapeutic outcomes in asthma.[39,40] Silencing RFX7 decreased the levels of TNF-α, IL-1 β, and IL-6 in PDGF-BB-stimulated ASMCs, thereby alleviating inflammatory response during asthma.

  Nonetheless, several limitations should be pointed out. In the follow-up study, the overexpression of RFX7 will be considered. Prospective cohorts are also necessary to further verify the diagnostic efficiency of the machine learning-based RFX model and RFX7 in childhood asthma. Furthermore, the transcriptional mechanisms and influence of RFX7 in the disease need in-depth investigations.


## SUMMARY
  Collectively, the random forest-based RFX model presented the best efficiency in diagnosing childhood asthma. Notably, RFX7 promoted the diagnosis of childhood asthma among RFX family members. RFX7 was proven to be upregulated in PDGF-BB-stimulated ASMCs; moreover, the suppression of RFX7 remarkably alleviated PDGF-BB-induced airway remodeling and inflammation. Hence, RFX7 was regarded as a therapeutic molecule for childhood asthma.


## AVAILABILITY OF DATA AND MATERIALS
  The datasets used and analyzed during the present study are available from the corresponding author on reasonable request.


## ABBREVIATIONS
  ANOVA: One-way analysis of variance

  ASMCs: Airway smooth muscle cells

  DEGs: Differentially expressed genes

  ECM: Extracellular matrix

  EdU: 5-Ethyny-2’-deoxyuridine

  GO: Gene Ontology

  GSEA: Gene set enrichment approach

  GSVA: Gene set variation analysis

  KEGG: Kyoto Encyclopedia of Genes and Genomes

  MHCII: MHC class II

  PDGF-BB: Platelet-derived growth factor BB

  RFX: Regulatory factor X

  ROCs: Receiver operating characteristic curves

  RT-qPCR: Reverse transcription quantitative polymerase chain reaction

  siRNAs: Small interfering RNAs

  ssGSEA: Simple-sample GSEA

  SVM: Support vector machine


## AUTHOR CONTRIBUTIONS
  YHW and FL: Designed the research; JWQ, JG and JTF: Performed the experiments; JM, TSD, and XLL: Analyzed the data. All authors contributed to editorial changes in the manuscript. All authors read and approved the final manuscript.


## ETHICS APPROVAL AND CONSENT TO PARTICIPATE
  This study was approved by Ethics Committee of Ji’an Hospital, Shanghai East Hospital ([2021] Research Preliminary Review No. [04]), and all experiments complied with approved protocols.


## CONFLICT OF INTEREST
  The authors declare no conflict of interest.


## EDITORIAL/PEER REVIEW
  To ensure the integrity and highest quality of CytoJournal publications, the review process of this manuscript was conducted under a double-blind model (authors are blinded for reviewers and vice versa) through an automatic online system.


## ACKNOWLEDGMENT
  Not applicable