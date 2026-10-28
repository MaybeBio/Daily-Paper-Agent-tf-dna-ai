# Integrating WGCNA and machine learning to identify and validate key biomarkers in MASLD


## Background
  Metabolic Dysfunction-Associated Steatotic Liver Disease (MASLD) represents the most prevalent chronic liver disease worldwide. The absence of approved pharmacotherapies is largely attributed to their profound molecular heterogeneity. The identification of novel hub genes in MASLD is therefore critical for unraveling the complex molecular mechanisms driving disease pathogenesis and progression.


## Methods
  We employed an integrative systems-biology approach utilizing Weighted Gene Co-expression Network Analysis (WGCNA) followed by multi-algorithm machine learning (LASSO, Random Forest, SVM-RFE) across GEO datasets (GSE89632, GSE63067) to identify hub genes. Key hub genes were validated in vitro with FFA-treated HepG2 cells and in vivo with an HFD-fed mouse model.


## Results
  Bioinformatic analyses revealed two distinct pathological networks. First, a lipogenesis-associated cluster revealed FMO1 and C10orf140 as upregulated, alongside JUNB downregulation. In vitro, the expression of these genes was significantly associated with the activation of the SREBP-1c/FASN lipogenic pathway. Second, WGCNA revealed a co-expression module that exhibited high correlation with inflammation (R = 0.59, p = 4e-05), from which 11 hub genes relating to inflammation (such as MAP3K8, PFKFB3) were identified. In vivo, HFD mice developed severe steatosis and demonstrated a key pathological paradox: high-level activation of both the pro-lipogenic p-AKT and the inhibitory p-AMPK pathways.


## Conclusion
  Our study identified the hub genes FMO1, C10orf140, and JUNB as novel regulators of MASLD lipogenesis through the SREBP-1c pathway. Additionally, we showed that co-activated p-AKT and p-AMPK in steatotic livers indicates “AMPK Resistance”. Ultimately, we describe a mechanism of pro-lipogenic signaling that is not curtailed and is accompanied by the inability to compensate for the inhibitory path. All findings reveal potential therapeutic targets for MASLD.


## Supplementary Information
  The online version contains supplementary material available at https://doi.org/10.1186/s12876-026-05071-2.


## Introduction
  Metabolic dysfunction-associated steatotic liver disease (MASLD) has emerged as the leading chronic liver condition globally, impacting about 38% of adults worldwide, and is closely linked to the rise in obesity and type 2 diabetes [1]. The histological spectrum spans from simple steatosis to metabolic dysfunction-associated steatohepatitis (MASH), fibrosis, cirrhosis, and hepatocellular carcinoma. However, no drug has been sanctioned for regular clinical application. The histological spectrum spans from simple steatosis to MASH, fibrosis, cirrhosis, and hepatocellular carcinoma [2]. The clinical need that remains unaddressed is due to the pronounced molecular heterogeneity of MASLD, where environmental factors, genetic modifiers, and epigenetic changes converge on complex transcriptional networks that are not fully elucidated [3]. The initial phase in discovering mechanism-based biomarkers and eventually creating targeted treatments involves pinpointing robust, functionally important hub genes that initiate and advance MASLD [4]. While high-throughput transcriptomics has significantly enhanced our perspective on MASLD pathophysiology, however, conventional analyses of differential expression often result in fragmented gene lists that fail to capture the coordinated, system-level behavior of hepatocytic and non-parenchymal gene modules [5]. By categorizing genes into biologically coherent modules, WGCNA surpasses this limitation, with their collective expression profiles linked to clinical traits [6]. Furthermore, integrating WGCNA with state-of-the-art machine-learning feature selection algorithms—such as LASSO regression, Random Forest, and SVM-RFE—enables the distillation of these complex modules into a core set of highly reliable hub genes [7].

  Previous studies that utilized WGCNA for MASLD typically ended at bioinformatic predictions or used only one machine-learning algorithm, such as LASSO, which resulted in large lists of candidates with high rates of false positives [8]. A key issue is that these studies typically miss systematic in-vitro and in-vivo functional validation, thus limiting their applicability in real-world scenarios [9]. Our study is unique because it integrates WGCNA with a multi-algorithm machine-learning framework, incorporating LASSO, Random Forest, and SVM-RFE [10]. Through cross-validation of these independent techniques, we derive a highly stable and minimal set of core hub genes.

  Simultaneously, performing methodical functional validation of in-silico predictions is important to prevent the reproducibility challenges associated with bioinformatics studies [11]. As the first step to functionally validate our in-silico predictions in a model of a controlled cellular environment, we chose free fatty acid (FFA)-treated HepG2 cells [12]. This controlled cellular environment facilitates the systematic evaluation of candidate gene effects on specific lipogenic pathways, such as SREBP-1c signaling [13]. Next, to test the pathological relevance of our experimental findings in a more complex in-vivo metabolic context, we used a mouse model fed a High Fat Diet (HFD) [14]. The HFD-fed mouse model allows for more closely reproducing the progressive disease spectrum seen in human MASLD and functions as an argument against other perturbations of systemic metabolism and signaling [e.g. AMPK/AKT pathways] [15]. Here we present a systems-biology pipeline that integrates WGCNA-based network inference with machine-learning feature selection to identify key regulatory genes driving MASLD. After candidate genes were validated at both the transcriptional and protein levels in FFA-treated hepatocytes and livers from HFD-fed mice, we next evaluated their influence on lipid-metabolic effector SREBP1-c, FASN and LPL and insulin-sensitizing signaling (AMPK, AKT) [16].

  We hypothesize that this rigorous analytical framework will uncover critical hub genes for MASLD progression that are overlooked by standard differential expression analyses. Furthermore, we postulate that these pivotal genes promote hepatocellular lipid accumulation by modulating the SREBP-1c/FASN-driven lipogenic pathway while engaging in complex crosstalk with AMPK/AKT signaling cascades.


## Materials and methods

### Bioinformatic analyses

#### Data acquisition and preprocessing
  Two publicly available microarray datasets, GSE89632 and GSE63067, comparing hepatic tissue from patients with MASLD/NAFLD with histologically normal controls, were downloaded from the Gene Expression Omnibus (GEO) database. Raw CEL files were imported into R (v4.3.1) using the GEO query package. Probe-level intensities were background-corrected, log2-transformed, and quantile-normalized using the RMA algorithm. The ComBat function from the sva package was applied to correct for batch effects introduced by different platforms. Probes with an average signal < 3 across all samples were filtered out, and the two cohorts were merged for downstream analyses.


#### Differential expression analysis
  Differentially expressed genes (DEGs) between MASLD/NAFLD and control samples were identified using the limma package. A linear model was fitted incorporating age, sex, and BMI as covariates, followed by empirical Bayes moderation10. Genes were considered significant if they had an adjusted P-value (Benjamini-Hochberg) of less than 0.05 and a log2 fold-change of at least 1.


#### Weighted Gene Co-expression Network Analysis (WGCNA)
  A signed co-expression network was constructed using the WGCNA package. A soft-thresholding power of β = 8 (scale-free topology R²>0.85) was chosen. Modules were defined using the dynamic tree cut method (deepSplit = 2, minModuleSize = 30). Module–trait relationships were calculated using Pearson’s correlation between each module eigengene (ME) and clinical variables (e.g., NAS score, steatosis grade, lobular inflammation). Modules exhibiting a correlation > 0.35 and P < 0.05 were designated as key modules for further analysis.


#### Machine-learning feature selection for hub genes
  Genes that were present in both the significant DEGs list and the key WGCNA modules were retained as candidate genes. To identify the strongest hub genes, three machine-learning algorithms were applied, one of which was the Least Absolute Shrinkage and Selection Operator (LASSO) regression with 10-fold cross-validation (glmnet package). Feature importance was ranked by MeanDecreaseGini. The top 20 features from each algorithm were intersected. The final hub list (e.g., FMO1, C10orf140, JUNB) comprised the genes consistently ranked highest across all three methods.


### Animal experiments

#### Animals and ethical statement
  All animal protocols were approved by the Laboratory Animal Ethics Committee of Xi’an Jiaotong University Health Science Center (No. 2023 − 1034). Eight-week-old male C57BL/6 mice were purchased from the Laboratory Animal Center of Xi’an Jiaotong University. Mice were housed in a specific pathogen-free (SPF) facility under controlled conditions: a 12-hour light/dark cycle, an ambient temperature of 22 ± 2°C, and a relative humidity of 50 ± 10%. They were housed in groups of 4 per cage in individually ventilated cages (IVC) with standard bedding material. Environmental enrichment was provided in each cage, including nesting material, a shelter, and a gnawing block. Animals had ad libitum access to their respective diets (see below) and autoclaved water. Animal health and well-being were monitored daily by trained personnel.


#### MASLD model induction and tissue collection
  After one week of acclimatization, mice were randomly divided into two groups (n = 8 per group): Male C67BL/6J weaned mice were fed a 60% fat diet (F3282, Bio-Serv) or a normal fat diet (ND) (F4031, Bio-Serv) for 16 weeks. After the feeding period, mice were fasted overnight and euthanized. Liver tissues were rapidly excised. A part was fixed in 4% paraformaldehyde for 24 h for paraffin embedding, designated for H&E and IHC. Another part was embedded in O.C.T. compound, rapidly frozen in liquid nitrogen, and kept at -80 °C for Oil Red O staining.


#### Histopathology and Immunohistochemistry (IHC)
  Paraffin-embedded liver tissues were sectioned into 4 µm sections. For histopathology, sections were deparaffinized and stained with H&E. For lipid staining, 8 µm cryosections were fixed, rinsed, and stained with 0.3% Oil Red O solution. Paraffin sections for IHC were deparaffinized, rehydrated, and subjected to antigen retrieval using citrate buffer in a microwave. Endogenous peroxidase activity was blocked with 3% H₂O₂. Sections were then blocked with 5% BSA and incubated overnight at 4°C with primary antibodies against: phosphorylated-AMPK (p-AMPK; cat. no. 2535, 1:1000), phospho-Akt (p-Akt; cat. no. 4060, 1:1000). Sections were then incubated with HRP-conjugated secondary antibody, visualized using a DAB (3,3’-diaminobenzidine) kit, and counterstained with haematoxylin.


### Cell culture and in-vitro steatosis model
  Human hepatoma HepG2 cells (ATCC HB-8065) were cultured in DMEM-high glucose supplemented with 10% FBS and 1% penicillin/streptomycin at 37°C in 5% CO₂. To induce steatosis, a 2:1 molar mixture of palmitate and oleate (FFA) was complexed to 1% fatty-acid-free BSA. HepG2 cells were exposed to the FFA mixture at final concentrations of 0.25, 0.5, and 1.0 mM for 24–48 h. Control cells received 1% BSA vehicle alone.


### In-vitro validation assays

#### Transfection and RNA interference
  Using Lipofectamine RNAMAX (Invitrogen) as per the manufacturer’s instructions, siRNA transfection was carried out. The siRNA was obtained from Shanghai BioTend Biotech Co., and the sequences can be found in Supplementary Table S1.


#### Lipid accumulation assays
  Intracellular triglycerides (TG) were quantified using a commercial colorimetric kit (Applygen, China) and normalized to total cellular protein (BCA assay, Pierce). For qualitative assessment, cells were fixed with 4% paraformaldehyde, stained with 0.3% Oil Red O, and counterstained with haematoxylin. BODIPY staining was conducted according to standard procedures. Briefly, cells were incubated with the BODIPY staining solution (Servicebio, GP1104), followed by nuclear staining with Hoechst and examination by confocal microscopy.


#### RNA Extraction and Quantitative PCR (qPCR)
  Total RNA was isolated using TRIzol reagent (Invitrogen) and then reverse-transcribed using the PrimeScript RT kit (Takara). Quantitative PCR was performed on a CFX96 system (Bio-Rad) using SYBR Green. Relative expression was calculated by the 2−△△Ct method, using β-actin as the endogenous control. Primer sequences were listed in Table 1.

  Table 1Primer sequences for quantitative PCRNameForward Sequence(5’~3’)Reverse Sequence(5’~3’)FMO1TGC CAG TGT CCT GGA GAA TAGGCA GCA GGT CAA GTT CTT TCAC10orf140TGC TGC TGA AGG ACG ACT ACCCA GCA GGT TCT CCA TCA TCJUNBCGC TGC CCA CGA CGAGTT CAT GTT CTT GGA GTC CGT GPPARATAT TCG GTG TCT TCA AGA ATG CCGGC CTT GTA GCA CGT GTA TCTSREBF1GCA TCT GAC CGC TTC AGCCAG ATA GCA CGG ATG GCA GTFASNAAG GAC CTG TCT AGG TTT CGA TTGG CTT CGC AGG TAC TCTβ-actinCAT GTA CGT TGC TAT CCA GGCCTC CTT AAT GTC ACG CAC GAT


#### Western blot analysis
  Cells were lysed in RIPA buffer with inhibitors. Proteins (30 µg) were resolved on 10% SDS-PAGE, transferred to PVDF membranes, and probed with primary antibodies against: phosphorylated-AMPK (p-AMPK; cat. no. 2535, 1:1000), AMPK (cat. no. 2532, 1:1000), phospho-Akt (p-Akt; cat. no. 4060, 1:1000), Akt (cat. no. 9272, 1:1000), GAPDH (cat. no. HRP-60004, 1:1,000), HRP-conjugated secondary antibodies (cat. no. ab6721; 1:5,000) were added to the membranes and visualized with ECL-plus, and band intensities were quantified using Image J.


### Statistical analysis
  All experiments were performed in triplicate, and data are presented as mean ± SD. Comparisons between two groups were analyzed by a two-tailed unpaired Student’s t-test. Multiple groups were evaluated by one-way ANOVA followed by Tukey’s post-hoc tes. A P-value < 0.05 was considered statistically significant.


## Results

### Bioinformatic identification of DEGs and WGCNA co-expression modules
  We first performed a comprehensive bioinformatic analysis using the combined GSE89632 and GSE63067 datasets, which included 50 MASLD patients and 31 healthy controls. A total of 6,771 differentially expressed genes (DEGs) were identified (3,947 upregulated, 2,824 downregulated) based on the criteria of |log2 FC| > 1 and adjusted p < 0.05 1. Figure 1A presents the volcano plot of all DEGs, highlighting significantly altered genes such as FMO1, C10orf140 (upregulated), and JUNB (downregulated). Using these 6,771 DEGs, a weighted gene co-expression network analysis (WGCNA) was performed. The genes were hierarchically clustered into 27 distinct co-expression modules, each designated by a unique color code for systematic identification (Fig. 1B). To help find modules associated with MASLD pathology, we correlated the eigengene (ME) of each module with clinical traits, specifically “Inflammation Response” and “Inflammation Composite”. The heatmap output (Fig. 1C) demonstrated that the turquoise module had the strongest positive association with Inflammation Response (R = 0.56, p = 1e-04) and Inflammation Composite (R = 0.59, p = 4e-05), although the red module demonstrated a significant positive association as well. Subsequent examination of the red module (Fig. 1D) showed a high correlation between gene significance (GS) for inflammation and module membership (MM), showing that genes in the red module are closely associated with the inflammatory process. In conclusion, LASSO regression was employed, with Fig. 1E illustrating the cross-validation error curve that helped identify the optimal λ parameter for feature reduction.

  Fig. 1Bioinformatic screening and WGCNA identify key modules and genes in MASLD. A Volcano plot of differentially expressed genes (DEGs) from the combined GSE89632 and GSE63067 datasets (10 MASLD vs. 32 healthy controls)1. Red dots indicate upregulated genes (3,947) and blue dots indicate downregulated genes (2,824)2. The threshold (dashed lines) was set at an adjusted p-value < 0.05 and |log2 fold-change| > 0.58. B A heatmap visualizing the correlations between 27 WGCNA module eigengenes (MEs). Lines connect MEs to the clinical traits of “Inflammation_Response” and “Inflammation_Composite”. C Module-trait relationship heatmap. Each cell contains the Pearson’s correlation coefficient (top number) and p-value (bottom number, in parentheses)3. Red indicates a strong positive correlation, while blue indicates a negative correlation. The turquoise module shows the strongest positive correlation with inflammation traits. D Scatterplot of Gene Significance (GS) for inflammation versus Module Membership (MM) within the red module, demonstrating a significant positive correlation. E Plot of the mean-squared error from 10-fold cross-validation in the LASSO regression model, used to determine the optimal tuning parameter (λ)6


### Correlation between identified hub genes and inflammation score
  Following WGCNA and subsequent machine learning-based screening for inflammation-related signatures, we identified a core set of 11 hub genes. To further evaluate their clinical relevance, we assessed the correlation between the expression profiles of these candidate genes and the calculated “Inflammation Score” within the patient cohort. As shown in Figs. 2A-K, each of the identified 11 hub genes, including MAP3K8, PFKFB3, MAFF, IFNGR1, TRIM15, RRP12, TGFB3, DDX5, TNFIP6, LOC388796, and RIPK2, exhibited a robust and highly significant positive correlation with the Inflammation Score. The correlation coefficients ranged from 0.80 to 0.94, and all P values were less than 2.2 × 10− 16, confirming that these genes are tightly linked to hepatic inflammation in MASLD.

  Fig. 2Correlation analysis of 11 identified hub genes with the inflammation score. A-K Scatterplots illustrating the significant positive correlation between the expression levels (x-axis) of 11 hub genes (MAP3K8, PFKFB3, MAFF, IFNGR1, TRIM15, RRP12, TGFB3, DDX5, TNFIP6, LOC388796, and RIPK2) and the Inflammation Score (y-axis) in the patient cohort. Pearson’s correlation coefficient (R) and p-value are displayed in each plot. The shaded area represents the 95% confidence interval of the regression line


### In vitro validation of steatosis model and gene expression
  To explore the cellular mechanisms of MASLD, we established an in vitro model of hepatocyte steatosis by treating HepG2 cells with a free fatty acid (FFA) mixture. To validate the in vitro model, Oil Red O staining was performed to assess lipid accumulation. Qualitative analysis revealed a dramatic, time-dependent increase in intracellular lipid droplets in FFA-treated (1.0 mM) cells at both 24 h and 48 h post-treatment (Fig. 3A), with significantly higher lipid deposition observed compared to vehicle-treated control (CTRL) cells. This finding was quantified by measuring intracellular TG levels. Figure 3B-C showed that FFA treatment induced a significant and dose-dependent increase in TG content. Next, we measured the expression of key DEGs and genes of the de novo lipogenesis (DNL) pathway in this model. Consistent with the patient data, FMO1 and C10orf140 were significantly upregulated by FFA in a dose-dependent manner (Fig. 3). Conversely, JUNB expression was significantly downregulated, also matching the in-silico findings. Simultaneously, the master regulator SREBP-1c and its downstream target FASN were both significantly upregulated. The expression of RRARα was also increased.

  Fig. 3FFA treatment induces steatosis and alters gene expression in HepG2 cells. A Representative Oil Red O staining images of HepG2 cells. Cells were treated with vehicle control (CTRL) or 1.0 mM FFA mixture for 24 h and 48 h. Red staining indicates intracellular lipid droplets. B, C Quantification of intracellular triglyceride (TG) content in HepG2 cells treated with increasing concentrations of FFA (0, 0.25, 0.5, 1.0 mM) for 24 h (B) and 48 h (C). D-I Relative mRNA expression levels of FMO1, C10orf140, JUNB, RRARα, SREBP-1c, and FASN in HepG2 cells after 24 h of FFA treatment. J-O Relative mRNA expression levels of the same six genes after 48 h of FFA treatment. All mRNA expression was measured by qPCR and normalized to β-actin. Data are presented as mean ± SD from three independent experiments. **p < 0.01 vs. the 0 mM control group


### In vivo validation of HFD-induced steatosis and signaling
  An HFD-fed mouse model was used for in vivo verification. H&E staining showed that compared with the normal liver structure in the ND group, HFD mice developed pronounced macrovesicular steatosis, with large lipid droplets pushing the hepatocyte nuclei aside (Fig. 4A). Oil Red O staining confirmed a significant deposition of neutral lipids in the liver tissues of HFD mice, with no apparent lipid staining in the control group (Fig. 4B). IHC results showed that the expression of p-AMPK (energy stress marker) and p-AKT (key molecule of insulin signaling) was both significantly elevated in liver tissues of HFD mice (Fig. 4C-D), suggesting simultaneous activation of two functionally antagonistic signaling pathways in steatotic liver.

  Fig. 4HFD induces severe hepatic steatosis and alters metabolic signaling pathways in vivo. Representative images of liver sections from mice fed a normal diet (ND) or a high-fat diet (HFD) for 16 weeks. A Haematoxylin and Eosin (H&E) staining, showing normal liver architecture in the ND group and severe macrovesicular steatosis in the HFD group. B Oil Red O staining, demonstrating extensive neutral lipid accumulation (red) in the HFD liver, which is absent in the ND control. C Immunohistochemistry (IHC) staining for phosphorylated-AMPK (p-AMPK, brown). D IHC staining for phosphorylated-AKT (p-AKT, brown). In (C) and (D), nuclei were counterstained with DAPI (blue). All scale bars = 200 μm


### Knockdown of candidate genes promotes lipotoxicity of hepatocytes via AMPK/AKT pathways
  As summarized in Fig. 5, expressions of p-AMPK and p-Akt were increased after FFA stimulation in a dose-dependent manner. These results suggested that FFA modulated hepatic lipogenesis at least partly by acting on p-AMPK/p-Akt signaling pathways. Bioinformatics analysis suggested that FMO1 and JUNB might mainly impact lipolysis and inflammation. Therefore, we conducted loss-of-function assays to detect the effect of candidate genes on hepatic inflammation and lipid accumulation by using Small interfering RNA (siRNA) to knock down those genes in HepG2 cells. Two interference sequences against those genes were transfected into HepG2 cells, respectively, and the expression of genes was detected (Fig. 6A). First, bodipy staining results showed that knockdown of three hub genes attenuated the intensity of lipid after FFA treatment (Fig. 6B). In comparison with the control group, the level of triglyceride accumulation in HepG2 cells was significantly lowered by FMO1 knockdown (Fig. 6C). Similar results were observed in siJUNB groups. Thus, those data revealed that FMO1and JUNB were involved in hepatic lipolysis. The de novo lipogenesis genes SREBP1c, FASN, and ACC1 were significantly lower in the siFMO1 and siJUNB groups compared to the siCON group. We further screened the status of AMPK and AKT signaling pathways. As shown in Fig. 6E, compared to the si-CON group, the ratio of p-Akt/Akt was reduced, and the ratio of p-AMPK/AMPK were increased in the si-FMO1 group (p < 0.06), while JUNB interference decreased the ratio of p-AKT/AKT and increased the ratio of p-AMPK/AMPK. We then examined the effect of FMO1 and JUNB interference on cell viability with a cell counting assay. In comparison with scrambled siRNA-transfected HepG2, HepG2 cells transfected with FMO1 and JUNB siRNA had significantly higher proliferative ability (Fig. 6F). Also, knockdown of FMO1 impaired inflammatory cytokine expression (TNF-α, IL-6, IL-1β).

  Collectively, this data revealed that the hub genes FMO1 and JUNB are key regulators of MASLD lipotoxicity through the AMPK/AKT/SREBP1 pathway in hepatocytes.

  Fig. 5FFA treatment regulated the AMPK/PI3K/Akt signaling pathways in HepG2 cells. A Cells were treated with FFA for 24 h, and the protein expressions of T-AMPK, p-AMPK, T-Akt, and p-Akt in cells were detected by western blotting. B Cells were treated with FFA for 48 h, and the protein expressions of T-AMPK, p-AMPK, T-Akt, and p-Akt in cells were detected by western blotting. Data are presented as mean ± SD from three independent experiments. **p < 0.01 vs. the 0 mM control group

  Fig. 6FMO1 and JUNB interference alleviates FFA-induced lipid accumulation and modulates the AMPK/AKT signaling pathway in HepG2 cells. Validation of knockdown efficiency by qPCR. Cells were transfected with siFMO1, siJUNB, or non-targeting control siRNA (siCON) for 48 h. **p < 0.01 vs. siCON group. B Representative images of Bodipy staining. Green staining indicates intracellular lipid droplets. Scale bar = 100 μm. C Quantification of intracellular triglyceride (TG) content. D Relative mRNA expression levels of lipogenic genes (SREBP-1c, FASN, ACC1) measured by qPCR. E Western blot analysis of total and phosphorylated AMPK and AKT. F Cell viability assay. To determine cell viability, cells were examined using a CCK-8 assay. G Relative mRNA expression levels of lipogenic genes (SREBP-1c, FASN, ACC1) and inflammatory factors (IL-6, TNF-α, IL-1β) measured by qPCR


## Discussion
  The present study integrated bioinformatics mining and multi-level experimental validation to screen and characterize key regulatory genes driving the progression of metabolic dysfunction-associated steatotic liver disease (MASLD). We systematically identified and verified FMO1 and C10orf140 as core hub genes that modulate hepatic lipogenesis in MASLD. Further mechanistic exploration revealed that these genes exert biological functions by regulating the SREBP-1c-mediated lipogenic pathway and interfering with the homeostasis of the AMPK/AKT signaling network. Our findings provide novel molecular insights into the pathogenesis of MASLD and offer potential candidate biomarkers and therapeutic targets for this prevalent liver disorder.


### FMO1, C10orf140, and JUNB as major regulators of lipogenesis
  We first performed bioinformatic mining based on clinical transcriptome data, and further validated the results via multiple in vitro experiments. The expression trends of FMO1 (upregulated) and C10orf140 (upregulated) in FFA-induced HepG2 steatosis model were consistent with those in MASLD patient samples. This essential trend was exactly recapitulated in our FFA-induced HepG2 steatosis model [17]. Functional experiments confirmed that these three hub genes are closely linked to the de novo lipogenesis (DNL) pathway. Their altered expression was positively correlated with the activation of SREBP-1c and FASN in a time- and dose-dependent manner. These findings indicate that FMO1 and C10orf140 can promote lipid deposition in hepatocytes by activating the SREBP-1c/FASN lipogenic pathway [18].


### AMPK resistance as a key pathological feature in the HFD model
  While in vitro experiments clarified the upstream drivers of lipogenesis, the high-fat diet (HFD)-fed mouse model recapitulated a typical metabolic disorder phenotype during MASLD progression. As a core upstream regulator of lipogenesis, the AKT signaling pathway was markedly activated in HFD mouse livers, which is consistent with its established role in triggering SREBP-1c-dependent DNL [19]. Notably, we observed simultaneous robust activation of p-AMPK, a key energy-sensing kinase that physiologically suppresses lipogenesis by inhibiting SREBP-1c. Under physiological energy deficiency, activated AMPK acts as a protective signal to restrict excessive lipid synthesis. However, in HFD-induced steatotic liver, sustained p-AMPK activation failed to block the pro-lipogenic signaling mediated by AKT and SREBP-1c [20]. This paradoxical co-activation of two functionally antagonistic pathways strongly demonstrates the existence of AMPK resistance in the diseased liver [21]. In this pathological state, hepatocytes initiate a compensatory AMPK response against metabolic stress, but downstream lipogenic machinery loses responsiveness to AMPK-mediated inhibition, leading to unconstrained lipid accumulation and persistent hepatic steatosis [20].


### The inflammatory network as a consequence of lipotoxicity
  A total of 11 inflammation-related hub genes were identified from the inflammation-associated co-expression module via WGCNA analysis. Correlation analysis confirmed that their expression levels were strongly positively associated with clinical hepatic inflammation scores, indicating a close linkage to liver inflammatory injury. Combined with our functional data, we propose that these inflammatory genes are not independent pathogenic factors, but secondary molecular events induced by sustained lipotoxicity. The FMO1/C10orf140/AKT/SREBP-1c axis drives continuous lipid overload in hepatocytes, and prolonged lipotoxicity further triggers hepatic innate immune response and inflammatory cascade [22], accompanied by the upregulation of inflammatory hub genes such as MAP3K8 and PFKFB3 [23]. This molecular chain of events explains the pathological transition from simple hepatic steatosis to metabolic dysfunction-associated steatohepatitis (MASH) in MASLD.


### The FMO1 and JUNB function as the prognostic biomarker and trigger lipotoxicity via the AMPK/AKT/SREBP1c pathway
  Building upon the identification of the AMPK/AKT/SREBP-1c dysregulation, we further elucidated the specific molecular executors within this network. Bioinformatics analysis and experimental validation highlighted FMO1 and JUNB as central nodes within the lipotoxic signature. Rather than being just passive markers, these molecules play a crucial role as intermediaries that uphold the pathological feed-forward loop. Mechanistically, the heightened expression of FMO1 and JUNB is seemingly induced by hyperactive AKT signaling, and they jointly act to reduce the functional effects of AMPK, despite its elevated phosphorylation. The ongoing signaling cascade keeps SREBP-1c perpetually active, leading to hepatocytes being in a constant state of lipogenesis and metabolic stress [24]. Consequently, the persistent elevation of FMO1 and JUNB serves as a quantifiable indicator of ‘AMPK Resistance’ severity. In clinical settings, elevated expression of these two genes is closely linked to the progression from simple steatosis to inflammatory liver cell damage, highlighting their potential as reliable prognostic biomarkers for identifying patients at risk of progressing to steatohepatitis.


## Conclusion
  In conclusion, this study identifies and validates FMO1, C10orf140, and JUNB as core hub genes regulating hepatic lipogenesis in MASLD through the SREBP-1c pathway. More importantly, our in vivo data provide strong evidence for “AMPK Resistance” as a key pathological state in MASLD. The data showed a situation in which AKT/SREBP-1c continues to be active, whereas the compensatory inhibition by AMPK has not been effective.


## Supplementary Information
  Supplementary Material 1.

  Supplementary Material 2.

  Supplementary Material 3.

  Supplementary Material 4.