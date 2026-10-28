# Transactivation DNA-binding protein–related genes were associated with salivary gland injury in primary Sjögren syndrome


## Abstract
  The purpose was to identify transactivation DNA-binding protein–related genes in salivary gland injury in primary Sjögren syndrome (pSS) in southwest China.

  We downloaded the datasets of GSE7451, GSE23117, and GSE40611. In order to screen the candidate genes, 2 kinds of machine learning algorithms were used. We collected blood from 28 patients and 20 controls to verify the expression of candidate genes using quantitative real-time polymerase chain reaction. The receiver operating characteristic curve was used to evaluate the diagnostic efficiency. Correlations between candidate genes and immune cells were examined.

  A total of 31 differentially expressed genes were obtained. Through different algorithms, 6 genes including IFIT1, CSF2RB, TRIM22, PPM1H, VAMP7, and C21orf2 were getted. Validation results suggested that the expression of CSF2RB, VAMP7, IFIT1, C21orf2, and TRIM22 was significantly increased in pSS. The area under the curve of CSF2RB was 0.937 and that of TRIM22 was 0.915. Immune infiltration analysis showed that the percentage of activated mast cells was lower than the controls (P = .025). Correlation analysis suggested that CSF2RB was associated with immune cell infiltration. The expression of CSF2RB was significantly upregulated, which could be related to the increase of γδ T cells.

  We revealed that CSF2RB could be the candidate gene of pSS. CSF2RB was involved by regulating various immune cells. The expression of CSF2RB was significantly upregulated, which was related to the increase of γδ T cells.


## 1. Introduction
  Xerostomia and dry eye are mainly symptoms of primary Sjögren syndrome (pSS).[1] Due to the lack of typical clinical presentation, it is easy to be ignored or misdiagnosed (38757225). The main purpose of treatment is to relieve symptoms. Genetic factors, infections, and immunological changes are believed to be the main causes.

  The transactivation DNA-binding protein was a highly conserved DNA/RNA. TAR DNA binding protein-43 (TDP-43) was mainly processed and degraded by autophagy and the ubiquitin-proteasome system in normal cells. Dysregulation of autophagy was associated with disease progression in autoimmune diseases.[2] In salivary glands (SGs), autophagy was increased and positively correlated with the expression of interleukin (IL)-21 and IL-23. Autophagy of Cell surface differentiation antigen (CD4+) T cells was suggested to play a key role in the pathogenesis of pSS.[3] In animal models, autophagy modulators, such as phosphopeptide P140, could significantly downregulate the activation of CD44high/CD62LlowCD4+ T cells and maturation of B cells, which ultimately reduced the secretion of IgG and autoantibody.[4]

  Based on the above findings, we used bioinformatics combined with machine learning to find out the correlation between the expressions of genes and immune infiltration in pSS. First, we downloaded the Gene Expression Omnibus datasets to determine the differentially expressed genes (DEGs). Then, we verified the candidate genes and evaluated the diagnostic efficiency by the receiver operating characteristic curve. Finally, we investigated the association of candidate genes with abnormally expressed immune cells in SGs’ microenvironment. Our results provided evidence to explore the candidate genes involved in SGs’ injury.


## 2. Materials and methods

### 2.1. Research processes
  According to Figure 1, we downloaded 3 datasets from the Omnibus database. We merged and normalized all the data. Finally, we obtained gene expression arrays from 38 pSS and 46 controls. Through the differential expression analysis, and based on different machine learning algorithms, we obtained 6 candidate genes. We collected blood from 28 patients and 20 controls matched by sex and age from July 2019 to July 2021. Next, we detected the expression levels of 6 genes. We compared the diagnostic efficiency based on experimental validation. Finally, we selected the key gene with the highest diagnostic efficiency and predicted correlation between this gene and immune cells. The research was in line with the Declaration of Helsinki. Ethical approval was obtained from the Ethics Committee of Peoples Hospital of Deyang City (number: 2020-04-160-K01).


### 2.2. Analysis of DEGs and Kyoto Encyclopedia of Genes and Genomes/gene ontology
  To obtain genes related to TDP-43, the Pearson correlation analysis was used. All genes with a correlation of TDP-43 in the range of 0.3 to 1.0 were screened. In screening for DEGs, the “limma” package was used. The cutoff values were both an adjusted P < .05 and fold change of log2 > 0.5. The “ggplot2” and “pheatmap” packages were used to draw correlation volcano and heatmap, respectively. For human genome annotation, the “org.Hs.e.g..db” package was used. For visual enrichment, the “clusterProfiler” and “enrichplot” packages were used.[5] The “DOSE” package was used for enrichment between gene and disease. The threshold was an adjusted P < .05 and a count ≥ 3.


### 2.3. Machine learning to screen candidate genes
  In order to screen genes effectively, we used 2 different algorithms, which were least absolute shrinkage and selection operator regression (LASSO) and support vector machine regression recursive feature elimination (SVM-RFE). We used the “glmnet” package for LASSO and “msvmRFE.R” package for SVM-RFE. Finally, we used the “VennDiagram” package to carry out the intersection genes, namely candidate genes.


### 2.4. Verification of candidate genes and comparison of diagnostic efficiency
  We detected the mRNA levels of candidate genes. The complete gene sequences were searched from the National Center for Biotechnology Information database. “Primer Premier” was used to design and screen specific primers. All primers were designed and synthesized by Shanghai Shenggong Company (Table S1, Supplemental Digital Content, http://links.lww.com/MD/N622), and they were purified by ULTRAPAGE. Extraction of total RNA was performed using cell/tissue total RNA reagent (Yeasen, China). Reaction system was configured with TB Green Premix Ex Taq II (Tli RNaseH Plus, China). Quantitative real-time polymerase chain reaction instrument was used to detect the amplified products (ThermoFisher, USA). The amplification condition was as shown (Table S2, Supplemental Digital Content, http://links.lww.com/MD/N623). A total of 45 cycles were performed.

  The diagnostic efficiency of each gene was based on verification. We used the “pROC” package to construct the prediction model. Area under the curve (AUC) was used to evaluate the efficiency of the prediction model. A P < .05 was considered significant.


### 2.5. Immune cells and candidate genes
  We analyzed changes of immune cells between pSS and controls by the “CIBERSORT” package.[6] To compare the immune cell distribution, the “violin” package was used. We used the “corrplot” package to analyze and show the correlation between different immune cells. We selected 1 gene with the highest AUC value and analyzed the correlation between candidate gene and immune cells. The “ggpubr” and “reshape2” packages were used to draw a lollipop chart. When P was ≤ .05, the gene was considered to be correlated with the immune cell.


## 3. Results

### 3.1. TDP-43–related genes and DEGs
  In this study, 5841 genes associated with TDP-43 were obtained. Among them, 2302 were downregulated and 3539 were upregulated. It was shown that 31 DEGs were obtained. Volcano plot displayed that 27 were upregulated and 4 were downregulated, as shown in Figure 2A. The top 4 upregulated genes were IFIT1, STAT1, CSF2RB, and IFI44L, and the 4 downregulated genes were SOX21-AS1, PPM1H, DLG1-AS1, and C21orf2, as shown in Figure 2B. Results of the Kyoto Encyclopedia of Genes and Genomes showed that pathways were significantly enriched in Epstein–Barr virus infection, antigen processing, and presentation, as shown in Figure 2C. According to the gene ontology analysis, DEGs were primarily enriched in biological processes and cellular components. In terms of biological processes, DEGs were involved in defense response to virus, defense response to symbiont, antigen processing, and presentation of endogenous peptide antigen via major histocompatibility complex (MHC) class I. In terms of cellular components, DEGs were involved in phagocytic vesicle membrane, phagocytic vesicle, endocytic vesicle membrane, and endocytic vesicle, as shown in Figure 2D.


### 3.2. Screening and validation of candidate genes
  We screened the 31 DEGs by LASSO regression, and 8 genes were obtained, as shown in Figure 3A and 3B. Then, SVM-RFE was used, and 19 genes were obtained, as shown in Figure 3C. Finally, an intersection of 6 genes was obtained by the 2 algorithms, as shown in Figure 3D. These candidate genes were IFIT1, CSF2RB, TRIM22, PPM1H, VAMP7, and C21orf2.

  The results of verification indicated that the expression levels of CSF2RB, VAMP7, IFIT1, C21orf2, and TRIM22 were higher in pSS. However, the levels of PPM1H were not detected in half of the patients with pSS. CSF2RB, VAMP7, IFIT1, C21orf2, and TRIM22 were selected for construction of diagnostic models, as shown in Table 1 and Figure 3E through 3I.


### 3.3. Diagnostic efficiency of candidate genes
  Based on validated data, we evaluated the efficacy of candidate genes. We found that CSF2RB (AUC = 0.937, 95% confidence interval [CI] = 0.898–0.976) and TRIM22 (AUC = 0.915, 95% CI = 0.859–0.970) had high accuracies. The AUC of VAMP7 (AUC = 0.796), IFIT1 (AUC = 0.815), and C21orf (AUC = 0.702) indicated that they also had certain accuracies in the diagnosis, as shown in Figure 4A and Table 2. Then, we verified the expression of CSF2RB and TRIM22 in SGs at the tissue level. The results suggested that CSF2RB (AUC = 0.803, 95% CI = 0.703–0.895) also had good diagnostic efficacy in the tissue. The diagnostic efficacy of TRIM22 (AUC = 0.774, 95% CI = 0.666–0.868) was slightly lower in the tissue, as shown in Figure 4B and 4C.


### 3.4. Correlation analysis between immune cells and candidate genes
  We tried to analyze and compare the differences in immune cell distribution between pSS and controls. Activated mast cells were lower in pSS than in controls (P = .025). According to Figure 4D, no significant differences were found in the other 21 immune cells. Correlation analysis showed that activated mast cells had the highest correlation with eosinophils. However, the correlation coefficient was 0.32, indicating a low correlation, as shown in Figure 4E. A relationship was also found between the levels of immune cell infiltration and the expression of CSF2RB. Results suggested that CSF2RB was positive with abnormal γδ T cells, naive CD4+ T cells, and M2 macrophages. However, it was negative with plasma cells, CD8+ T cells, and monocytes, as shown in Figure 4F. It was suggested that the expression of CSF2RB participated in SGs by regulating a variety of immune cells. The expression of CSF2RB was significantly upregulated, which was related to the increase of γδ T cells.


## 4. Discussion
  The presence of infiltrating lymphocytes in SGs and lacrimal glands was the most common manifestation of pSS. Excessive activation of B cells was a key factor, which was regarded as a target for treatment.[7] T helper 17, follicular helper T, and CD8+ T cells were also important participants.[8–10] At the same time, the abnormality of innate immunity was also involved.[11] Studies have shown that lymphoma was the most common concomitant tumor in patients with pSS.[12,13] Therefore, we speculated that DEGs played important roles in disorders of the immune microenvironment. Investigating the association between DEGs and the immune microenvironment could enhance our comprehension of the pathogenesis of pSS.

  In this study, we aimed to identify potential target genes associated with TDP-43. Consistent with prior research, we screened DEGs utilizing existing databases and employed 2 distinct algorithms to identify target genes. Previous investigations have highlighted the benefits of machine learning algorithms in the identification of potential biomarkers.[14] Specifically, 1 study employed SVM-RFE, k-nearest neighbor, and random forest as classification models, demonstrating that SVM-RFE exhibited superior accuracy and sensitivity compared to the other methods.[15] The aforementioned results demonstrated that machine learning was a valuable tool with promising application prospects. To further identify potential biomarkers, this study employed machine learning algorithms, including LASSO regression and SVM-RFE. Unlike previous studies, this research was validated using a local population after identifying potential candidate genes and assessed the diagnostic efficacy in blood to verify the results. Compared to outcomes derived solely from bioinformatics, the findings exhibited greater concordance with empirical data.

  The results of the Kyoto Encyclopedia of Genes and Genomes and gene ontology analyses indicated that TDP-43–related genes were actively involved in the inflammatory process. Previous studies have suggested that viral proteins of the Epstein–Barr virus acted as autoimmune triggers. Specifically, molecular mimicry between EBER-1/EBER-2 and La antigen, as well as between EBNA-2 and Ro-60 antigen, has been identified as a significant mechanism in the induction of autoimmunity.[16] Furthermore, mesenchymal stem cells were upregulated in response to the persistent inflammatory environment characteristic of autoimmune diseases.[17] Subsequent evaluations demonstrated that CSF2RB was highly expressed in the peripheral blood and tissues of pSS patients.

  CSF2RB was a protein-coding gene, and the protein served as a common signal transduction subunit for IL-3 and IL-5. In tumor tissues, CSF2RB expression was reduced, establishing it as an independent prognostic factor. CSF2RB could undergo carcinogenic mutations in KAIMRC1 cells, with the resultant mutation signals being transmitted via the jauns kinase/ signal transducer and activators of transcription and phosphoinosmde-3-kinase/the mammalian target of rapamycin pathways.[18,19] Our findings indicated that CSF2RB expression was elevated compared to controls, which contrasted with observations in cancer. Additionally, it was demonstrated that CSF2RB expression was upregulated in regulatory T cells (Tregs) of patients with autoimmune conditions. Although the high expression of CSF2RB was positively associated with the number of Tregs, no correlation between CSF2RB and cytokines was observed in an in vitro model.[20,21] These findings suggested that while CSF2RB could regulate Tregs, it could not influence the function or phenotype in autoimmune diseases. In transcriptomic datasets of multiple sclerosis and systemic lupus erythematosus, CSF2RB was significantly overexpressed in Tregs.[22] This indicated that CSF2RB could serve as a novel biomarker for certain autoimmune diseases. In this study, no significant correlation was identified between Tregs and CSF2RB in SGs. However, elevated expression of CSF2RB was associated with the levels of various immune cells, including γδ T cells, naive CD4+ T cells, and M2 macrophages. Notably, γδ T cells were implicated in the regulation of multiple autoimmune diseases. They facilitated the production of inflammatory cytokines such as interferon-γ (IFN-γ), IL-12, and tumor necrosis factor-α and were involved in the pathogenesis of conditions such as collagen-induced arthritis, experimental autoimmune encephalomyelitis, and airway hyperreactivity.[23]

  Naive CD4+ T cells, also referred to as T helper type 0 cells, differentiated into T helper type 1 (Th1) and T helper type 2 cells in response to various stimulating antigens. In the presence of IFN-γ and IL-12, naive CD4+ T cells received intense T cell receptor stimulation and differentiated into Th1 Teff cells, characterized by high expression levels of T-bet, STAT5, and B lymphocyte induced maturation protein 1. Th1 Teff cells produced IFN-γ, which recruited and supported innate effector cells such as macrophages.[24] Correlation analysis revealed that γδ T cells were positively correlated with naive CD4+ T cells and negatively correlated with plasma cells and CD8+ T cells.

  This study also has some limitations. There is a need to enhance the comprehensiveness of the machine learning content. Providing more detailed explanations would facilitate a deeper understanding of the material presented in this article. Future research should aim to incorporate additional experimental data to further substantiate our findings.


## 5. Conclusions
  Our study identified TDP-43–associated genes, including CSF2RB, as potential candidate genes for pSS. CSF2RB played a role in the regulation of various immune cells. Notably, the expression of CSF2RB was significantly upregulated, correlating with an increase in γδ T cells.


## Author contributions
  Data curation: Naidan Zhang, Hongsheng Zhang.

  Formal analysis: Naidan Zhang.

  Funding acquisition: Naidan Zhang.

  Investigation: Naidan Zhang, Xiao Bao.

  Project administration: Naidan Zhang, Chengliang Yuan.

  Software: Naidan Zhang.

  Writing – original draft: Naidan Zhang.

  Writing – review & editing: Naidan Zhang, Chengliang Yuan.

  Methodology: Hongsheng Zhang, Chengliang Yuan.

  Resources: Xiao Bao.

  Supervision: Xiao Bao.

  Conceptualization: Chengliang Yuan.


## Supplementary Material