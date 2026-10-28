# TRIM29 drives ulcerative colitis by disrupting lipid metabolism via lysosomal dysfunction: a multi-omics and experimental study


## Background
  The pathogenesis of ulcerative colitis (UC) involves genetic susceptibility and immune dysregulation. However, a more comprehensive understanding of its underlying mechanisms is still required.


## Methods
  Weighted correlation network analysis (WGCNA) and Mendelian randomization (MR) were used to investigate the association and causality between lipid metabolism and UC. Hub genes were identified by applying ensemble machine learning (LASSO, SVM, XGBoost) to the merged transcriptomic data, followed by cell-type-specific localization using public single-cell RNA-seq data from UC tissues. Pathophysiological relevance was confirmed in a DSS-induced colitis mouse model. The mechanistic role of the key hub gene was defined through knockdown LPS challenge in colonic epithelial cells, coupled with transcriptomic profiling.


## Results
  Integrated WGCNA and MR analyses established a strong association between UC and lipid metabolic pathways, which was experimentally confirmed by marked intracellular lipid accumulation in UC models. Mechanistically, this dysregulation was traced to lysosomal dysfunction, a finding solidified by pharmacological modulation with Rapamycin (enhancer) and Chloroquine (inhibitor), which directly demonstrated that lysosomal activity governs lipid metabolic disturbance. Subsequent machine-learning-based feature selection from lysosome-related genes pinpointed TRIM29 as a central regulator. Functional and transcriptomic analyses together demonstrated that TRIM29 knockdown attenuates UC progression by rescuing the lysosome-lipid metabolism axis, as evidenced by restored lysosomal function, enhanced cytoskeletal transport, improved lipid catabolism, a resolved pro-inflammatory immune profile, and downregulated inflammatory signaling.


## Conclusion
  This study identifies TRIM29 as a master regulator that drives UC progression by disrupting lysosomal function and reprogramming lipid metabolism. Our work delineates the TRIM29-lysosome-lipid metabolism axis, providing a mechanistic rationale for targeting TRIM29 as a promising therapeutic strategy in UC.


## Introduction
  Ulcerative colitis (UC) is a chronic, non-specific inflammatory bowel disease with multifactorial origins (1). It primarily affects the rectal and colonic mucosa and is characterized by recurrent episodes of mucopurulent bloody stools, abdominal pain, and systemic symptoms. In the 21st century, the global incidence of UC has risen rapidly (2). Although its etiology and pathogenesis remain unclear, they are thought to involve genetic predisposition, epithelial barrier dysfunction, immune dysregulation, and environmental factors (3–6). This lack of clear mechanistic understanding continues to pose challenges for diagnosis and treatment. In recent years, computational approaches, particularly in bioinformatics and machine learning (ML), have played increasingly important roles in UC research (7).

  By integrating multi-omics data, researchers can identify novel UC-associated biomarkers and potential therapeutic targets (8). In transcriptomics, bioinformatics approaches have matured, with weighted gene co-expression network analysis (WGCNA) being widely applied to identify disease-related gene modules (9, 10). Such analyses provide new perspectives on disease mechanisms, offering opportunities for improved diagnosis and treatment (11, 12). Moreover, ML offers distinct advantages in multi-omics research and shows strong potential for elucidating disease mechanisms. When combined with WGCNA, it enables the identification of key diagnostic genes from large-scale transcriptomic datasets and facilitates the construction of predictive models. These models can support disease subtype classification and predict progression and treatment responses (12–17). Together, WGCNA and ML provide complementary perspectives on the molecular mechanisms of disease pathogenesis and hold promise for clinical translation.

  In this study, we analyzed UC-specific mRNA expression profiles from NCBI, employing an integrated approach of WGCNA and ML to investigate key molecular mechanisms underlying UC pathogenesis. Our computational findings were further validated through molecular biology experiments. This work aims to provide new insights into the mechanisms driving inflammation and disease progression in UC.


## Method

### Data acquisition
  All mRNA datasets were retrieved from the Gene Expression Omnibus (GEO) Datasets in the NCBI (National Center for Biotechnology Information) database. Using the keyword “ulcerative colitis” and restricting the organism to “Homo sapiens”, We manually screened the GEO repository and selected two independent mRNA expression datasets, GSE206285 (comprising only placebo-treated patients with stage IV ulcerative colitis, representing a pure UC cohort) and GSE87466, for model construction. Two additional datasets, GSE75214 and GSE107597, were prospectively reserved for independent external validation.


### Cell lines and model inflammatory model construction
  The human intestinal epithelial cell line NCM460 was obtained from the BeNa Culture Collection (BNCC, Beijing, China) and authenticated by short tandem repeat (STR) profiling to exclude cross-contamination. Cells were cultured in Dulbecco’s Modified Eagle’s Medium (DMEM, Hyclone, Cytiva, MA, USA) supplemented with 10% fetal bovine serum (FBS, Gibco) and 1% penicillin/streptomycin (Biosharp, China) at 37°C in a 5% CO2 incubator.

  NCM460 cells were seeded into 6-well plates and 24-well plates, incubated overnight, and then treated with lipopolysaccharide (LPS, 5 µg/mL, 24 hours, Sigma, USA) (18–21).


### DSS-induced colitis mouse model
  Six-week-old male C57BL/6J mice were purchased from Shubeili Biotechnology Co., Ltd. (Wuhan, China). Mice (n = 6 per group) were randomly divided into two groups: a control group receiving water and an experimental group receiving 2.5% dextran sodium sulfate (DSS, MP Biomedicals) in drinking water for 7 days.


### WGCNA
  WGCNA was used to identify co-expressed gene modules and their associations with phenotypic traits. A weighted co-expression network was built from pairwise gene expression correlations. The adjacency matrix was calculated using a soft-thresholding power (β) to meet scale-free topology criteria (R² > 0.8) and was then transformed into a topological overlap matrix (TOM) to improve robustness. Genes were hierarchically clustered based on TOM dissimilarity, and modules were defined using dynamic tree cutting. Module eigengenes (MEs), represented by the first principal component, summarized module expression profiles. Associations between MEs and clinical traits were tested (p < 0.05, Bonferroni-corrected). Significant modules were further analyzed by functional enrichment (GO/KEGG). All analyses were performed using the WGCNA R package (v1.72) (22) (Supplementary Figure S2).


### Machine learning modeling and validation
  The bulk transcriptomic datasets GSE206285 and GSE87466 were integrated and batch effects were removed using the removeBatchEffect function from the limma R package (Supplementary Figure S1), with disease status (UC vs. control) preserved as a biological variable. The combined cohort was then randomly partitioned into training (60%), validation (20%), and test (20%) sets. LASSO regression, support vector machine (SVM), and XGBoost algorithms were applied to the training set to identify key feature genes from the lysosomal gene set that were differentially expressed between UC and HC.

  Hyperparameters for SVM and XGBoost were optimized using the validation set. The final performance of all three models was evaluated on the test set.


### LASSO regression
  After preprocessing the mRNA expression matrix and binary phenotypic data, we performed L1-regularized logistic regression using the R package glmnet (v4.1-8). The normalized gene expression matrix was used as the independent variable, and the binary phenotype as the dependent variable. Genes with non-zero coefficients were selected by 10-fold cross-validation based on the minimum λ (min λ) criterion to generate the candidate gene set. Key parameters: alpha = 1, nfold = 10, family = “binomial”, type.measure = “class”.


### SVM machine learning
  The curated mRNA expression matrix was input into a support vector machine (SVM) implemented in the R package e1071 (v1.7-13). A linear kernel was used, and the hyperparameter C was optimized by 5-fold grid search. Model performance was evaluated by cross-validation area under the curve (AUC). The absolute values of the retained weights were used to define the feature gene set.


### XGBoost machine learning
  The whole-genome expression matrix was analyzed using the xgboost package (v1.7.8.1) with the following parameters: eta = 0.1, eval_metric = “logloss”, nthread = 2, eval_metric = “auc”, and nrounds = 100. The top-ranked genes were selected based on gain weights, and their contributions to the model were visualized using SHAP values.


### Mendelian randomization
  Genome-wide association study (GWAS) datasets were retrieved from the IEU database (https://gwas.mrcieu.ac.uk/) using the keywords “Ulcerative Colitis” and “Hyperlipidemia”. After screening and confirming disease-related entries, six hyperlipidemia-associated GWAS datasets were selected: ebi-a-GCST90104007, ebi-a-GCST90104006, ebi-a-GCST90104005, ebi-a-GCST90104004, ebi-a-GCST90104003, and ebi-a-GCST90090994. In addition, multiple UC-related datasets were included: ieu-a-970, ukb-b-19386, ukb-b-7584, ukb-a-104, ebi-a-GCST90018933, ebi-a-GCST90038684, ebi-a-GCST90018713, ukb-a-553, ukb-d-ULCERNAS, finn-b-ULCERNAS, finn-b-K11_UC_STRICT_PSC, finn-b-K11_UC_STRICT, finn-b-K11_UC_STRICT2, finn-b-K11_UC_NOCD, finn-b-K11_ULCER, finn-b-ULCEROTH, ieu-a-972, ebi-a-GCST90020072, ieu-a-971, ieu-a-973, ebi-a-GCST000964, ieu-a-968, ieu-a-32, ebi-a-GCST003045, ebi-a-GCST004133, and ukb-a-553.

  MR analyses were performed using the R packages TwoSampleMR (v0.6.19), MRPRESSO (v1.0), and ieugwasr (v1.0.4) (23, 24).

  Results were filtered in three steps: (1) preliminary screening for causal significance; (2) exclusion of effects with β values close to zero (biologically negligible); and (3) removal of results with β directions opposite to meta-analysis findings, retaining only exposure-outcome pairs with consistent directions and clear biological relevance.

  For each exposure-outcome pair, the primary causal estimate was selected based on heterogeneity: if Cochran’s Q test indicated significant heterogeneity (p < 0.05), the inverse-variance weighted model with multiplicative random effects (IVW-MRE) was applied; otherwise, the fixed-effects inverse-variance weighted model (IVW-FE) was used. All significant associations reported herein satisfied this pre-specified robustness criterion (Supplementary Figure S3).


### Single-cell RNA-seq analysis
  Single-cell RNA-seq data were retrieved from the scIBD database (http://scibd.cn), a curated repository of inflammatory bowel disease-associated single-cell transcriptomes. We queried the database with the following parameters: Tissue = “largeInt”, Location = “colon, rectum”, and Disease state = “Healthy, UC_non_inflamed, UC_inflamed”. Gene expression patterns of candidate genes were visualized and extracted using the built-in analysis tools of the platform.


### Inflammatory microenvironment profiling
  Immune cell infiltration was estimated using the immunedeconv R package (v2.1.0), which provides a unified interface for multiple deconvolution algorithms. Specifically, the quanTIseq and MCP-counter methods were applied to the batch-corrected bulk RNA-seq data to quantify the relative proportions of immune cell subsets. Results from both methods were used for downstream correlation and group-comparison analyses.


### Western blot
  Cells were lysed in RIPA buffer (Servicebio, Wuhan, China) supplemented with 1% protease, phosphatase (Servicebio), and acetylase inhibitors (Beyotime, #P1112). Lysates were centrifuged at 12,000 rpm for 15 min at 4°C (Centrifuge 5424R, Eppendorf). Supernatants were mixed with loading buffer and denatured by heating.


### Quantitative real-time polymerase chain reaction
  Total RNA was extracted using an RNA extraction solution (Servicebio, Wuhan, China, G3013–100 mL). mRNA was reverse transcribed into complementary DNA (cDNA) using the Evo M-MLV Reverse Transcription Kit II (Accurate Biology, Changsha, China, AG11711). qPCR was performed with a CFX Connect Real-Time PCR System (Bio-Rad, Hercules, CA, USA) and 2X Universal SYBR Green Fast qPCR Mix (Abclonal, China, #RK21203). Relative expression levels were calculated using the 2^-ΔΔCt method, with β-actin as the reference gene.


### Oil red O staining
  Oil Red O (Sudan Red 5B) is a lipophilic azo dye that selectively stains neutral lipids, mainly triglycerides, producing red to orange-red droplets with minimal affinity for phospholipids and steroids. In this study, adherent cells treated with a lipid mixture (Sigma-Aldrich, L0288-100ML) were stained with Oil Red O (Servicebio, Wuhan, China, G1015–100 mL) to visualize intracellular lipid deposition.


### BODIPY fluorescence
  Cells were seeded on sterile glass coverslips in 24-well plates and treated with LPS for 24 h. The medium was then replaced with a 200 µM lipid mixture, and cells were incubated for an additional 24, 48, or 72 h. After three PBS washes, cells were stained with 40 µM BODIPY™ FL C12 (Thermo Fisher Scientific, #D3822) for 30 min at 37°C, fixed with 4% paraformaldehyde, and counterstained with DAPI.


### LysoSensor fluorescent staining
  Cells were seeded on sterile glass coverslips in 24-well plates and treated with LPS for varying durations. They were then incubated with LysoSensor for 30 min and Hoechst 33342 for 15 min to label lysosomes and nuclei, respectively.


### Statistical analysis
  All quantitative imaging data were measured using ImageJ, averaged with cell counts obtained from Cellpose segmentation (25), and subsequently visualized along with statistical analyses using GraphPad Prism. The exact sample sizes for each group are detailed in the figure legends.


## Result

### Integrated WGCNA and Mendelian randomization implicate dysregulated lipid metabolism in ulcerative colitis
  In the bioinformatics analysis of mRNA gene sets, heatmaps, principal component analysis (PCA), and volcano plots can effectively illustrate expression differences across groups. Therefore, we conducted these three basic analyses for the GSE206285 and GSE87466 datasets (Figures 1A–C). The merged dataset revealed marked differences in mRNA expression profiles between healthy controls (HC) and UC patients, underscoring its research feasibility and value. Accordingly, we applied WGCNA using the WGCNA R package.

  We performed WGCNA to construct a gene co-expression network, identify modules, and assess their associations with the UC phenotype (Figures 1D–F). Among all modules, the darkgreen module demonstrated the strongest positive correlation with the UC phenotype (correlation coefficient = 0.73, p = 2 × 10−50), indicating a highly significant association (Figure 1G).

  KEGG and GO enrichment analyses of key genes from the darkgreen module revealed significant enrichment in pathways related to fatty acid metabolism (Figures 1H, I). These results suggest that dysregulated fatty acid metabolism is strongly associated with UC pathogenesis and may play a crucial role in disease development.

  Although the WGCNA analysis revealed strong associations between lipid metabolism modules and UC, observational studies cannot establish causal direction or account for confounding factors. To explore whether lipid metabolism abnormalities serve as genetic causal risk factors for UC, we conducted a two-sample MR analysis (Supplementary Figure S4A). Since hyperlipidemia represents a hallmark phenotype of disordered lipid metabolism (26), we focused on the genetic relationship between hyperlipidemia and UC.

  Our MR analyses identified 11 significant exposure-outcome pairs that passed stringent quality control: all exhibited strong instrumental variables (minimum F-statistic = 29.9-37.9) and no evidence of horizontal pleiotropy (MR-Egger intercept p = 0.32-0.83) (Table 1). Of these, eight pairs indicated that genetic predisposition to UC was causally associated with a reduced risk of hyperlipidemia (β = -0.043 to -0.095, p < 0.05) (Supplementary Figures S4D, E), while three pairs suggested a reciprocal protective effect of hyperlipidemia on UC risk (β = -0.0003 to -0.246, p < 0.05). The strongest effect was observed for the influence of familial combined hyperlipidemia (Mexico criteria) on UK Biobank-defined UC (β = -0.246, p = 5.2 × 10−4).


### Reduced lipid metabolism capacity in an experimental UC model
  To further explore the relationship between UC and lipid metabolism, we established a mouse model of UC using 2.5% DSS. After 7 days of DSS treatment, the mice’s average body weight decreased to 79.8% of the initial weight, the average colon length was reduced by 3.1 cm, and both the DAI and spleen indices (spleen weight/initial body weight) significantly increased, confirming the successful induction of UC (Figures 2A–E). HE and AB-PAS staining of colonic sections revealed crypt destruction (Figures 2F, G), inflammatory infiltration, loss of goblet cells, and significantly reduced mucin abundance in the 2.5% DSS group. Transmission electron microscopy (TEM) showed disrupted tight junctions in the intestinal epithelium, lipid droplet accumulation within epithelial cells, and markedly impaired lipid degradation in the 2.5% DSS group (Figures 2I, J).

  Our mouse experiments confirmed that DSS-induced UC significantly suppresses lipid metabolism. To investigate the underlying mechanism, we further established an in vitro colitis model using NCM460 cells. The successful establishment of the inflammatory model was validated by Western Blotting to assess the relative levels of specific proteins (Figure 2L). Following LPS induction, we observed an increase in the pro-apoptotic protein BAX, while levels of the anti-apoptotic protein BCL-2 and the barrier function proteins Occludin and ZO-1 decreased, confirming the successful establishment of the in vitro inflammatory model.

  Additionally, NCM460 cells were exposed to a high-fat (HF) environment for varying durations after the same duration of inflammatory treatment. Total lipid content and average lipid droplet area were quantified using BODIPY and Oil Red O staining, respectively (Figures 2K, M). Under inflammatory conditions, both total lipid content and average lipid droplet area at 24 hours were significantly lower than in the control group. At 48 hours, both the average lipid droplet area and total lipid content in inflamed cells were higher than those in the control group. However, at 72 hours, total lipid content in the inflamed cells decreased significantly below the control level. Although the average lipid droplet area also decreased, it remained significantly higher than in the control group (Figures 2H, N).


### Lysosomal dysfunction mediates impaired lipid metabolism in UC
  Our data demonstrate a distinct lipid metabolism disorder phenotype in UC. As lysosomes are the primary organelles responsible for intracellular lipid degradation, a process known as lipophagy (27), we hypothesized that lysosomal dysfunction may act as a critical upstream event impairing lipid turnover in our colitis model. We next performed GSEA on the merged dataset, which revealed a significant enrichment of the lysosomal gene signature in UC samples, indicating a heightened transcriptional profile of lysosomal pathways (Figure 3A, Supplementary Datasheet 1).

  We further assessed lysosomal function in an in vitro inflammation model. Lysotracker confocal imaging revealed that, under inflammatory conditions, the number of NCM460 lysosomes increased at 12 hours but decreased at 24 hours, while their size progressively enlarged over time (Figures 3B, D). Concurrently, Lysosensor staining demonstrated that lysosomal pH significantly increased at 24 hours, plateaued thereafter, and reached its peak at 72 hours under inflammatory conditions (Figures 3E, F).

  We further employed Western Blotting to evaluate lysosomal autophagic capacity. Under inflammatory conditions, we observed elevated levels of the lysosomal membrane proteins LAMP1 and LAMP2, together with increased expression of the autophagosome marker LC3 and the autophagy substrate p62 (Figure 3C).

  Furthermore, electron microscopy of colonic tissues in the in vivo model revealed pronounced accumulation of lysosomal contents under inflammatory conditions. In contrast, the control group displayed smaller lysosomal contents, indicating preserved degradation capacity (Figure 3G).

  To further determine the role of lysosomes in lipid metabolism, we manipulated lysosomal biogenesis and function using Rapamycin, an inducer of lysosomal biogenesis, and Chloroquine (CQ), an inducer of lysosomal dysfunction. Following intervention, the number of lysosomes in Rapamycin-treated cells showed a statistically significant difference compared with the inflammation-only control group at 24 hours. Moreover, the relative lysosomal area was significantly reduced at both 12 and 24 hours (Figures 3H, I).

  In lipid metabolism assays, Rapamycin treatment led to increased average lipid droplet area and total lipid content at 24 hours, whereas CQ inhibited these effects. At 48 hours, significant differences emerged, with both parameters showing an overall upward trend. The Rapamycin-treated group exhibited the largest average lipid droplet area, whereas the CQ-supplemented group exhibited the smallest. Concurrently, the inflammation-only group showed the highest total lipid content, with no significant differences between the other two groups, although the Rapamycin-treated group exhibited a slight increase. By 72 hours, the average lipid droplet area had decreased across all three groups. Comparisons revealed that the Rapamycin-treated group had the smallest average lipid droplet area, whereas the inflammation-only group had the largest. However, total lipid content exhibited an opposite trend: it was lowest in the Rapamycin-treated group and highest in the Rapamycin plus CQ-treated group (Figures 3J–M).

  Together, these findings indicate that lysosomal dysfunction is closely linked to lipid metabolic disorders during the progression of inflammation.


### Machine learning screening of key genes in the lysosomal gene set: TRIM29
  We next analyzed the previously merged mRNA dataset with the lysosomal gene set. Heatmap and volcano plot analyses of differentially expressed genes revealed marked differences between the inflammatory and control groups (Supplementary Figures S5A, B).

  To further explore the role of lysosomal pathways in inflammatory progression, we performed protein-protein interaction (PPI) network analysis of differentially expressed lysosomal genes via the STRING database, and identified hub genes (MCC ≥10) using the cytoHubba plugin in Cytoscape.

  Complementing this network-based approach, we applied three ML algorithms, LASSO regression, SVM, and XGBoost, to the same mRNA dataset using R software (Figures 4A–C, Supplementary Figure S5C). Integration of ML-derived features with PPI hub genes (MCC ≥10) identified TRIM29 as the top consensus candidate (Table 2, Figure 4D).

  Feature genes selected by LASSO regression demonstrated excellent diagnostic performance in distinguishing UC from HC, with AUC values of 0.8190 and 0.8259 in the validation and test sets, respectively (Figures 4E, F). Following hyperparameter optimization on the validation set, both the SVM (AUC = 0.869, 95% CI: 0.7991-0.9392) and XGBoost (AUC = 0.703, 95% CI: 0.4559-0.9490) models achieved satisfactory predictive performance in the independent test set (Figures 4G, H).

  Subsequent validation confirmed that TRIM29 was upregulated in Ulcerative colitis (UC) across human datasets: its mRNA expression was lowest in healthy colon tissue and highest in active UC in both GSE75214 and GSE107597 (Figures 4I, J). Immunohistochemical data from the Human Protein Atlas showed minimal TRIM29 protein in healthy colon (Supplementary Figure S6A). Additionally, in vitro inflammation modeling via qPCR and Western blotting demonstrated significant upregulation under inflammatory conditions (Supplementary Figures S6B, C).

  Notably, TRIM29 exhibited diagnostic accuracy for UC comparable to canonical inflammatory cytokines IL-6, IL-1β, and TNF-α in GSE107597 (Figure 4K), and significantly outperformed IL-1β in GSE75214 (Figure 4L), supporting its role as a lysosome-associated inflammatory biomarker with robust diagnostic and translational potential in UC (Supplementary Figure S6D).


### TRIM29 expression correlates with immune infiltration and is enriched in epithelial cell in UC
  To investigate the immunological role of TRIM29 in ulcerative colitis (UC), we first analyzed bulk transcriptomic data. Samples from merged datasets were stratified into TRIM29-high and TRIM29-low groups based on median expression. Immune cell infiltration was quantified using both quanTIseq and MCP-counter algorithms.

  Both methods consistently revealed a significant increase in B cell infiltration in the TRIM29-high group (Figures 5A, C). Furthermore, quanTIseq indicated elevated levels of regulatory T cells (Tregs), while MCP-counter detected increased proportions of monocytes/macrophages, endothelial cells, natural killer (NK) cells, Fibroblasts, and neutrophils. Correlation analysis confirmed that TRIM29 expression was significantly associated with five immune cell types by quanTIseq and nine by MCP-counter (Figures 5B, D), underscoring its broad link to the UC immune microenvironment.

  To complement these findings and pinpoint the cellular sources of TRIM29, we leveraged the online platform scIBD to analyze single-cell RNA sequencing data. This analysis confirmed broad TRIM29 expression across epithelial cells in UC, with levels positively correlating with mucosal inflammation (Figures 5E, F). TRIM29 expression showed a progressive increase from HC to UC_non_inflamed (non-inflamed mucosa from UC patients) and UC_inflamed groups, with the highest levels specifically localized to epithelial cells in UC_inflamed lesions (Figure 5G).


### TRIM29 knockdown restores lysosomal biogenesis and function in NCM460 cells and markedly alleviates inflammation
  To further validate the functional role of the key gene TRIM29 in inflammatory processes, we generated a stable NCM460 cell line stably expressing GFP-tagged shRNA targeting TRIM29 and confirmed efficient knockdown by qPCR and immunofluorescence analyses (Supplementary Figures S7A–C).

  We next assessed lipid metabolic capacity and lysosomal morphology in the stable cell lines under inflammatory conditions. The shTRIM29 inflammation group showed significant differences in lysosomal number and average lysosomal area compared with the shNC group at 12 and 24 hours, characterized by an increased lysosomal number and a reduced average area (Figures 6A–C). Similarly, Western blot analysis of autophagy-related lysosomal proteins revealed increased LC3B levels, decreased p62, and reduced expression of LAMP1 and LAMP2 in the shTRIM29 group (Figure 6H).

  Compared with the shNC inflammation group, the shTRIM29 group had a smaller mean lipid droplet area at 24 hours. Although this value increased at 48 hours, it remained lower than that of the shNC group. By 72 hours, the lipid droplet area in the shTRIM29 group continued to increase, in contrast to the declining trend in the shNC group (Figures 6D, E).

  Finally, TUNEL staining and Western Blotting were conducted to evaluate the effects of TRIM29 knockdown on cellular inflammation. The apoptosis rate was significantly lower in the shTRIM29 group than in the shNC group (Figures 6F, G). Additionally, Western Blotting revealed higher expression of the pro-apoptotic protein BAX and lower expression of the anti-apoptotic protein BCL-2 in the shTRIM29 group, along with increased levels of the tight junction proteins ZO-1 and Occludin (Figure 6I).


### TRIM29 depletion induces transcriptomic signatures of membrane-cytoskeleton remodeling and ether lipid metabolism
  After comparing the transcriptome sequencing data between the LPS group and shTRIM29+LPS group (Figures 7A–C), we performed KEGG, GO, and GSEA enrichment analyses.

  KEGG, GO and GSEA enrichment results showed that lysosome function (Figure 7F, G) and membrane transport-related terms were significantly enriched, including endocytic vesicle lumen and membrane raft-related structural domains such as membrane raft, membrane microdomain, plasma membrane raft, and basolateral plasma membrane (Figure 7E). Simultaneously, cytoskeleton-related pathways including Motor proteins and Cytoskeleton in muscle cells were significantly enriched in KEGG analysis (Figure 7D).

  GSEA analysis further revealed that lipid metabolism-related pathways were highly enriched across multiple databases, including Cholesterol metabolism, Arachidonic acid metabolism, alpha-Linolenic acid metabolism, Linoleic acid metabolism, and Ether lipid metabolism in the KEGG database (Figure 7H), as well as sterol transporter activity and lipoprotein particle receptor binding in GO molecular functions (Figure 7I). Inflammation-related pathways were also significantly enriched, including TNFα/NF-κB signaling pathway, interferon alpha response, and interferon gamma response in the Hallmark database, along with Complement and coagulation cascades and NOD-like receptor signaling pathway in the KEGG database. Additionally, KRAS signaling pathway reached significant enrichment levels in Hallmark analysis (Figure 7J).

  These transcriptome data, though derived from a limited sample size, systematically suggest potential molecular mechanisms underlying TRIM29 knockdown, spanning from lysosome-membrane transport system alterations to lipid metabolism reprogramming, and ultimately to inflammatory responses.


## Discussion
  In this study, we first applied WGCNA and MR to identify key evidence supporting a potential association between UC and disorders of lipid metabolism. This relationship was subsequently validated using both in vivo and in vitro experimental models of UC. Given the established link between lipid metabolism and lysosomal function, we employed ML algorithms to screen for lysosome-related hub genes, through which TRIM29 was identified as a key candidate.

  We then performed bioinformatic analyses to examine TRIM29 associations with immune infiltration and its subtype-specific expression patterns. Finally, a stable TRIM29-knockdown cell line was established. Using this model, we experimentally validated the proposed TRIM29-lysosome-lipid metabolism-UC axis and performed transcriptomic profiling to explore the potential mechanisms underlying this axis.

  Prior evidence from WGCNA has implicated lipid metabolism dysregulation in UC pathogenesis.

  Unlike the typical association of metabolic disorders with elevated lipid levels (28), patients with UC frequently exhibit hypolipidemia, characterized by reduced total cholesterol, low-density lipoprotein Cholesterol, high-density lipoprotein Cholesterol, and sometimes triglycerides (29), with these alterations being more marked in severe disease (30).

  The apparent discrepancy, whereby UC is linked to lower systemic lipids in clinical and MR studies, yet associates with intracellular lipid accumulation in our cellular models, does not represent a true contradiction. Instead, it reflects complementary biological processes operating at different scales: systemic metabolism versus cellular metabolic mechanisms.

  This gap is critical: although systemic lipid alterations in UC are well-documented, the intracellular mechanisms governing lipid handling during inflammation remain unclear. Importantly, common comorbidities such as malabsorption and malnutrition (31, 32) can account for systemic lipid reduction, highlighting a disconnect between whole-body and cellular metabolism. We therefore focused on lysosomes, the central organelles for intracellular lipid degradation, as potential mediators linking mucosal inflammation to lipid dysregulation. To address this, we investigated how inflammation reshapes lipid metabolism and lysosomal function in colonic epithelial cells.

  Correspondingly, in our in vivo and in vitro UC models, we observed marked intracellular lipid accumulation under inflammatory conditions. This cellular lipid retention likely underpins the MR finding that UC genetically predisposes to a reduced risk of hyperlipidemia, as lipids are sequestered within the epithelium rather than circulating systemically.

  Although MR revealed statistically significant causal estimates in both directions, these signals arose from distinct exposure-outcome pairs and differed markedly in magnitude. The effect of hyperlipidemia on UC risk was negligible (β ≈ -0.0003 in most significant pairs), whereas UC consistently reduced hyperlipidemia risk with a substantially larger effect size, aligning with our experimental observation of inflammation-driven intracellular lipid sequestration.

  The average lipid droplet area and total cellular lipid content exhibited dynamic, non-linear changes (33). Under high-fat conditions with inflammation, both metrics initially decreased and later increased, but followed distinct temporal patterns. This suggests an early phase in which cells suppress lipid uptake to prioritize inflammatory responses, followed by a subsequent phase of impaired lysosomal degradation that drives lipid accumulation.

  The later apparent divergence, where total lipid levels declined while average droplet area increased, can be explained by a combination of lipid droplet fusion (producing larger droplets) and the selective loss of severely lipid-laden cells through lipotoxic apoptosis (34), which our microscopy data support. This aligns with the lipid droplet retention observed in the colonic epithelium of DSS-induced colitis mice.

  High-fat diets are standard for inducing hyperlipidemia in animal models. When given before colitis induction, such a diet promotes systemic alterations, including gut microbiota dysbiosis (35–37), immune dysregulation (38), and metabolic disorders (39), that may exacerbate disease. Clinically, without high-fat intake, UC patients typically show reduced serum lipid levels, especially in severe cases. Correspondingly, in animal models, a high-fat diet worsens the pathology of DSS-induced colitis compared to a normal diet (40). Conversely, after colitis onset, switching to a low-fat, high-fiber diet significantly alleviates symptoms, reduces inflammatory markers, and improves gut microbiota composition in patients (41).

  Previous work by Teixeira et al. showed that a high-fat diet alone induces hyperlipidemia without causing significant colonic pathology. Building on this, we propose that during DSS-induced colitis, a high-fat background creates a specific vulnerability: substantial lipids enter intestinal epithelial cells, but concurrently, inflammation progressively impairs lysosomal function. As the primary site for lipid degradation, dysfunctional lysosomes fail to process this lipid influx.

  Consequently, undegraded lipids, such as cholesterol and triglycerides, accumulate and form intra-lysosomal droplets, which further suppress enzymatic activity, creating a self-perpetuating vicious cycle (42). The resulting severe decline in lysosomal activity then engages a bidirectional cascade with inflammatory pathways, leading to cellular damage, pathway activation, and exacerbated colitis (43).

  Based on our findings, we propose that under high-fat conditions, the lysosome acts as a critical mediator linking hyperlipidemia to exacerbated colitis. To test this, we employed Rapamycin to enhance lysosomal biogenesis and CQ to inhibit lysosomal function. Rapamycin treatment effectively enhanced lysosomal lipid metabolism, reduced lysosomal swelling, and consequently led to a marked decline in lipid deposition, evidenced by lower total lipid content and a smaller mean lipid droplet area. Conversely, CQ administration abolished these benefits, confirming that lysosomal dysfunction directly mediates the lipid metabolic disorder in cellular inflammation. Together, these opposing pharmacological effects underscore the central role of lysosomal homeostasis in inflammatory progression.

  To elucidate potential mechanisms of lysosomal dysfunction in UC, we analyzed the merged expression matrix using ML approaches applied to a lysosome-associated gene set. This approach identified TRIM29 (Tripartite Motif Containing 29) as a candidate key molecule. TRIM29 is located on human chromosome 11q23.3 and encodes a 588-amino-acid protein with a molecular weight of approximately 66 kDa.

  Current research on TRIM29 is predominantly in oncology, where it exhibits distinct and sometimes opposing effects across cancer types. It functions as a tumor suppressor in hepatocellular carcinoma and prostate cancer (44), yet promotes tumor progression in thyroid and colorectal cancers (45). In enterovirus-induced intestinal inflammation, TRIM29 targets and degrades NLRP6/NLRP9b, thereby suppressing the host innate immune response and facilitating viral replication (46, 47). Mechanistically, TRIM29 regulates multiple signaling pathways, including Wnt/β-catenin, PI3K/AKT/mTOR, NF-κB, the KRAS-β-catenin synergy, and the STAT3-SNAI1 axis (48). However, the specific role of TRIM29 in UC remains undefined.

  Transcriptomic analysis revealed that elevated TRIM29 expression was broadly associated with altered immune cell infiltration. Specifically, TRIM29 levels showed a positive correlation with the proportions of B cells and monocytes/macrophages, but a negative correlation with natural killer (NK) cells. This profile, characterized by an increase in pro-inflammatory lineages and a decrease in NK cells, reflects a pro-inflammatory shift in the immune milieu linked to high TRIM29 expression.

  Single-cell analysis via the scIBD platform further revealed that TRIM29 expression is elevated in active UC and predominantly localized to intestinal epithelial cells, supporting the rationale for selecting the human colonic epithelial cell line NCM460 in our experimental validation.

  To specifically interrogate TRIM29’s intrinsic role in colonic epithelium, we established stable TRIM29-knockdown NCM460 cells and assessed their response to inflammatory stimulation. TRIM29 knockdown significantly ameliorated lysosomal dysfunction and attenuated inflammatory responses. Mechanistically, the knockdown initially enhanced lysosome-mediated lipolysis, reducing lipid deposition. This was directly evidenced by Oil Red O staining, which showed that after 48–72 hours of high-fat treatment, shTRIM29 cells exhibited smaller individual lipid droplets compared with shNC controls, even as the total lipid droplet area increased, indicating accelerated lipolysis. Paradoxically, TRIM29 knockdown also promoted the survival of metabolically stressed cells, leading to retention of dysfunctional cells and subsequent compensatory lipid overload. As a result, the average lipid droplet area in shTRIM29 cells exhibited a biphasic change: an initial decrease followed by a later increase.

  Thus, these findings establish TRIM29 as a critical node coordinating lysosomal function, lipid metabolism, and cell fate in inflamed epithelium. Our data demonstrate that TRIM29 drives pathological lipid accumulation via lysosomal dysfunction and sustains inflammatory responses in UC. This epithelium-intrinsic defect mechanistically explains the pro-inflammatory immune microenvironment linked to high TRIM29. Future studies using intestinal organoids or cell-type-specific models are needed to validate these functions within native colonic cell contexts.

  Building on this, we delineate a pathogenic axis in UC: inflammation upregulates epithelial TRIM29, which disrupts lysosomal function and lipid metabolism. This leads to barrier failure that drives a pro-inflammatory microenvironment marked by increased B cells and macrophages alongside decreased NK cells. Our work thereby establishes the TRIM29-lysosome-lipid metabolism-UC axis, providing a mechanistic foundation for targeting TRIM29.

  Despite these findings, our study has several limitations. First, due to technical constraints with fluorescently tagged shRNA constructs, we were unable to assess lysosomal pH or total lipid content in the shTRIM29 inflammation model. Second, our functional insights into TRIM29 are primarily derived from LPS-treated NCM460 colonic epithelial cells, an in vitro model that has been widely used to mimic inflammatory conditions in UC (18–21). However, this monoculture system cannot fully recapitulate the complex multicellular architecture, immune-epithelial crosstalk, and microenvironmental heterogeneity characteristic of human UC. To better capture the pathophysiological relevance of the TRIM29–lysosome–lipid metabolism axis in UC, future studies should incorporate more physiologically representative models, such as patient-derived intestinal organoids or primary human colonic epithelial cells. Third, the upstream regulators and downstream pathways mediating TRIM29’s role in colitis were largely inferred from transcriptomic data and require direct experimental validation to elucidate the precise molecular mechanisms involved.


## Conclusion
  In summary, our findings identify TRIM29 as a novel regulatory hub linking lysosomal dysfunction to pathological lipid metabolism in UC. TRIM29 is upregulated in inflamed mucosa and correlates with disease severity. Knockdown of TRIM29 attenuates lysosomal impairment and inflammation in colonic epithelial cells, with accompanying transcriptomic shifts in ether lipid metabolism and membrane-cytoskeleton organization. These results implicate TRIM29 in UC pathogenesis and support therapeutic targeting of the TRIM29-lysosome-lipid metabolism axis.


## Data availability statement
  The original contributions presented in the study are included in the article/Supplementary Material. Further inquiries can be directed to the corresponding authors.


## Ethics statement
  Ethical approval was not required for the studies on humans in accordance with the local legislation and institutional requirements because only commercially available established cell lines were used. All animal experiments were conducted in compliance with the Hubei Provincial Regulations for Animal Experiment Personnel and were approved by the Animal Ethics Committee (Ethics Approval Number: WDRM-20231005B). The study was conducted in accordance with the local legislation and institutional requirements.


## Author contributions
  X-ZG: Data curation, Formal Analysis, Investigation, Methodology, Visualization, Writing – original draft, Writing – review & editing. L-YZ: Validation, Visualization, Writing – original draft, Writing – review & editing. Z-BT: Formal Analysis, Investigation, Methodology, Writing – original draft. H-DH: Data curation, Investigation, Writing – original draft. Y-FL: Investigation, Methodology, Writing – original draft. B-PY: Formal Analysis, Writing – review & editing. W-GD: Funding acquisition, Methodology, Writing – review & editing.


## Conflict of interest
  The author(s) declared that this work was conducted in the absence of any commercial or financial relationships that could be construed as a potential conflict of interest.


## Generative AI statement
  The author(s) declared that generative AI was not used in the creation of this manuscript.

  Any alternative text (alt text) provided alongside figures in this article has been generated by Frontiers with the support of artificial intelligence and reasonable efforts have been made to ensure accuracy, including review by the authors wherever possible. If you identify any issues, please contact us.


## Publisher’s note
  All claims expressed in this article are solely those of the authors and do not necessarily represent those of their affiliated organizations, or those of the publisher, the editors and the reviewers. Any product that may be evaluated in this article, or claim that may be made by its manufacturer, is not guaranteed or endorsed by the publisher.


## Supplementary material
  The Supplementary Material for this article can be found online at: https://www.frontiersin.org/articles/10.3389/fimmu.2025.1728932/full#supplementary-material


## Acknowledgments
  We acknowledge the platform support provided by the Key Laboratory of Digestive System Diseases of Hubei Province and the Central Laboratory of Wuhan University People’s Hospital.