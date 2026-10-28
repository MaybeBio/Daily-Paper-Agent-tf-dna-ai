# Protocol for tumor prognostic prediction, molecular stratification, and target discovery using a machine learning-driven approach


## Summary
  Accurate prediction of tumor prognosis, understanding molecular heterogeneity, and identifying druggable targets are critical for advancing precision oncology. Here, we present a protocol to analyze aging-associated prognosis and molecular heterogeneity in gastric tumors using a transcriptome-based, machine learning-driven approach. We describe procedures for developing a prognostic model using robust gene signature, identifying molecular subtypes, and building a machine learning classifier for subtype prediction. We further detail the inference of subtype-specific regulatory network and prioritization of druggable transcription factors through drug sensitivity analysis.

  For complete details on the use and execution of this protocol, please refer to Li et al.1


## Before you begin
  Identifying high-risk patients and delineating tumor heterogeneity are essential steps toward the development of individualized cancer therapies. Integrating specific biological or clinical parameters, such as patient age, can improve prognostic modeling, guide therapeutic decisions, and enable patient stratification into clinically meaningful subgroups. This strategy also facilitates the prioritization of druggable targets for subgroups with aggressive biological behavior.

  In this protocol, we employ aging as a biological criterion to identify high-risk gastric tumors and classify them into clinically relevant molecular subtypes. We first curated a list of 445 aging-associated genes from the Aging Atlas database2 and used these to construct an independent prognostic model, termed the Aging-Associated Index (AAI), based on a robust gene signature selected through machine learning. Molecular stratification was then performed using unsupervised clustering, followed by development of a machine learning-based classifier to predict patient subtypes in an independent cohort. Furthermore, we inferred a subtype-specific regulatory network of transcription factors (TFs) and prioritized key TFs through master regulatory analysis. Finally, we performed drug sensitivity analysis to repurpose candidate compounds targeting the master regulatory TFs.

  The pipeline described here is broadly applicable across cancer types and biological processes. Below, we outline the required software tools and input files necessary for successful implementation.


### Install required software and packages
  Timing: ∼2 h 1.Install R and RStudio.

  Ensure that R (version 4.1.3 or higher) and RStudio are installed on your machine.Note: R can be downloaded from The Comprehensive R Archive Network (CRAN, https://www.r-project.org/), and RStudio can be downloaded from Posit (https://posit.co/downloads/). Both tools are platform-independent and support Windows, macOS, and Linux.2.Install required R packages.Install the following R packages needed for downstream analysis:a.tidyverse.b.broom.c.survival.d.RTN.e.ggpubr.f.limma.g.randomForest.h.glmnet.i.magrittr.j.impute.k.factoextra.l.ConsensusClusterPlus.m.pROC.n.survminer.> if (!requireNamespace("BiocManager", quietly = TRUE))> install.packages("BiocManager")> BiocManager::install(c("tidyverse","broom","ggpubr","survminer","RTN","limma","randomForest","glmnet","magrittr","impute","ConsensusClusterPlus","factoextra","pROC"))Note: You can select the most responsive CRAN mirror in RStudio based on your geographic location to accelerate the installation process.3.Download required datasets and gene signatures.

  Download the curated datasets and signature genes.> git clone https://github.com/SYSUSH-LiLab/STAR_PROTOCOL_Code.gitNote: Preprocessed gene expression and clinical data for the TCGA-STAD (training dataset) and GSE62254 (validation dataset) are provided in the Datasets subdirectory of the main project folder, STAR_PROTOCOL_Code.Note: Set STAR_PROTOCOL_Code as your working directory in RStudio before proceeding.Note: If Git is not available on your machine, you can download the repository as a compressed .zip file from the corresponding GitHub page and extract its content manually.Note: The approximate size of the files to be downloaded (in ZIP format) is around 25 MB.4.Download drug sensitivity and expression profiles.

  These data can be accessed from the Cancer Therapeutics Response Portal (https://discover.nci.nih.gov/rsconnect/cellminercdb/).Note: Due to potentially slow speeds, we have included preprocessed versions of these datasets in the Datasets subdirectory.Note: No specific desktop operating system is required for this protocol. However, we recommend using a 64-bit machine with at least 8 GB of available memory and 100 GB of storage space.


### Innovation
  This protocol provides a comprehensive and adaptable framework for transcriptome-based prognostic modeling, molecular stratification, and therapeutic target prioritization in cancer. It integrates classical machine learning with regulatory network inference to identify clinically relevant subtypes and actionable targets. The method emphasizes interpretability and reproducibility by combining multivariate Cox modeling, consensus clustering, and random forest classification, offering a robust alternative to deep learning approaches that are often prone to overfitting, especially in studies with limited sample sizes. Additionally, the protocol supports cross-platform applicability by enabling model validation across datasets generated by different technologies (e.g., RNA-seq and microarrays), addressing a common challenge in translational bioinformatics. Its modular design allows users to incorporate alternative gene signatures, biological processes, or tumor types, making it highly extensible. Beyond risk prediction, the pipeline links subtype-specific regulators to drug response data, enabling the prioritization of druggable transcription factors and informing targeted therapy strategies. This integration of prognostic modeling, subtype classification, and drug sensitivity analysis into a single, scalable workflow enhances its translational potential and utility in precision oncology applications.


## Key resources table
  REAGENT or RESOURCESOURCEIDENTIFIERDeposited dataTCGA-STADTCGAhttps://xenabrowser.net/datapages/GSE62254Gene Expression Omnibus (GEO)https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE62254Cancer Therapeutics Response PortalCellMinerCDBhttps://discover.nci.nih.gov/rsconnect/cellminercdb/Aging-related genesAging Altashttps://ngdc.cncb.ac.cn/aging/indexEMT signature genesdbEMThttps://bioinfo-minzhao.org/dbemt/dbemt1/index.htmlTranscription factorsAnimalTFDBhttp://bioinfo.life.hust.edu.cn/AnimalTFDB4/Software and algorithmssurvivalCRANhttps://cran.r-project.org/web/packages/survival/glmnetCRANhttps://cran.r-project.org/web/packages/glmnet/consensusClusterplusBioconductorhttps://bioconductor.org/packages/release/bioc/html/ConsensusClusterPlus.htmlclusterCRANhttps://cran.r-project.org/web/packages/cluster/NbClustCRANhttps://cran.r-project.org/web/packages/NbClust/randomForestCRANhttps://cran.r-project.org/web/packages/randomForest/limmaBioconductorhttps://www.bioconductor.org/packages/release/bioc/html/limma.htmlRTNBioconductorhttps://www.bioconductor.org/packages/release/bioc/html/RTN.htmlfactoextraCRANhttps://cran.r-project.org/web/packages/factoextra/index.htmlimputeBioconductorhttps://bioconductor.org/packages/release/bioc/html/impute.htmlpROCCRANhttps://cran.r-project.org/web/packages/pROC/survminerCRANhttps://cran.r-project.org/web/packages/survminer/ggpubrCRANhttps://cran.r-project.org/web/packages/ggpubr/index.htmlR version 4.1.3R softwarehttps://www.r-project.org/


## Step-by-step method details

### Develop a prognostic model using robustly prioritized signature genes
  Timing: ∼30 min

  This section describes the prioritization of aging-associated genes with prognostic value and the development of a robust risk model to predict patient outcomes. While the focus is on aging in gastric cancer, this workflow is adaptable to other biological parameters and cancer types.1.Prioritize prognostic signature genes.> library(tidyverse)> library(survival)> library(broom)> setwd("/path/to/STAR_PROTOCOL_Code")> load("Datasets/TCGA-STAD.rda")> tmp <- gc.expr[aging.gene$Symbol,] %>% t() %>% as.data.frame() %>% bind_cols(gc.subtype)> age.os.cox <- lapply(aging.gene$Symbol, function(x){ formu <- sprintf("coxph(Surv(OS.time, OS) ∼ %s, data = tmp)", x) ### Build Cox formula for each gene res <- eval(parse(text = formu)) %>% tidy(exponentiate = T) ### Fit model and extract HR/p-value }) %>% do.call(rbind, .) ### Combine results into one dataframe> train.gene <- age.os.cox$term[age.os.cox$p.value < 0.1]### Select genes with nominal prognostic significanceNote: The R object “train.gene” contains 54 aging-associated genes with prognostic significance. A p value threshold of 0.1 is used to retain an adequate number of genes; this threshold can be adjusted as needed.2.Iteratively select top signature genes (Key Step).Figure 1Robustly prioritized signature genes were selected to develop a prognostic modelWe performed LASSO-based dimensionality reduction 100 times and prioritized genes that appeared in at least 85 iterations for downstream prognostic model development. This figure refers to the ‘Figure 2’ in our reference manuscript.> library(glmnet)> library(magrittr)> lasso.gene <- lapply(1:100, function(x){ fit <- cv.glmnet(gc.expr[train.gene,] %>% t(), as.matrix(Surv(gc.subtype$OS.time,gc.subtype$OS)), family = "cox", alpha = 1, nfolds = 5) efs <- coef(fit, s=fit$lambda.min) %>% as.matrix() gene.lasso <- rownames(efs)[efs[,1] != 0] return(train.gene %in% gene.lasso)}) %>% do.call(cbind, .) %>% magrittr::set_rownames(train.gene) %>% rowSums()> final.gene <- names(lasso.gene)[lasso.gene > 85]> lasso.gene %>% as.data.frame() %>% rownames_to_column('term') %>% magrittr::set_colnames(c('term','freq')) %>% filter(freq > 0) %>% left_join(age.os.cox[,c('term','estimate','p.value')]) %>% dplyr::mutate(HR = ifelse(estimate > 1, 'Risk', 'Protective'), estimate=round(estimate, 1)) %>% ggdotchart(x = "term", y = "freq", color='HR', dot.size = 8, sorting = "descending", add = "segments", palette = 'Dark1', ggtheme = theme_pubr(),label = 'estimate', font.label = list(color = "white", size = 9, vjust = 0.5))+geom_hline(yintercept=85, linetype='dashed', color='#FC4E07')+labs(x='', y='Occurance', color='Hazard ratio')Note: To reduce computational time, we use 100 iterations (Figure 1), but increasing this to >500 can reduce random error.Note: The cross-validation fold number (nfold) is set to 5 due to a relatively small sample size (n = 196).Note: Although using “set.seed” function improves reproducibility, it may overlook the variability induced by random splits in cross-validation.3.Build a multivariate Cox regression-based risk model.Figure 2The developed risk model could be used as a prognostic indicator of GC tumorsPatients with high AAI scores exhibited the poorest overall and disease-free survival in both the discovery dataset (A) TCGA-STAD and the validation dataset (B) GSE62254. Survival curves were compared via log rank test. This figure refers to the ‘Figure 3’ in our reference manuscript.> asi.expr <- gc.expr[final.gene,] %>% t() %>% as.data.frame() %>% bind_cols(gc.subtype[,c('OS.time','OS')])> asi.fit <- coxph(Surv(OS.time, OS) ∼ ., data = asi.expr)> gc.subtype$asi.score <- sapply(gc.expr[final.gene,], function(x){sum(x ∗ coef(asi.fit)) %>% return()})> coxph(Surv(OS.time, OS) ∼ asi.score, data = gc.subtype) %>% broom::tidy(exponentiate = T)> coxph(Surv(DFI.time, DFI) ∼ asi.score, data = gc.subtype) %>% broom::tidy(exponentiate = T)> gc.subtype$ASI.HL <- ifelse(gc.subtype$asi.score > median(gc.subtype$asi.score), 'ASI-H', 'ASI-L')> survfit(Surv(OS.time, OS) ∼ ASI.HL, data=gc.subtype) %>% ggsurvplot(pval = TRUE,conf.int = F, risk.table = T,risk.table.col = "strata",size=1,pval.size=8, xlab='Follow up (months)', ylab='OS (%)', legend.title = '',legend.lab=c('AAI-H', 'AAI-L'), ggtheme = theme_classic2(), palette = c('#FC4E07','#E7B800'), title = 'TCGA-STAD', font.x=15, font.y=15, font.main=18, font.legend=15,font.tickslab=12)Note: The resulting prognostic is available as a Shiny web server (https://jli-bioinfo.shinyapps.io/AAI_Aging/).Note: Code for Kaplan-Meier plots of the TCGA-STAD dataset is included in the shared R scripts (Figure 2A).4.Validate the risk model on an independent dataset.> load("Datasets/GSE62254.rda")> identical(colnames(GSE62254.expr), GSE62254.subtype$GEO_ID)> GSE62254.subtype$asi.score <- sapply(GSE62254.expr[names(asi.fit$coefficients),], function(x){sum(x ∗ coef(asi.fit))})> coxph(Surv(OS.m, Death) ∼ asi.score, data = GSE62254.subtype) %>% broom::tidy(exponentiate = T)> coxph(Surv(DFS.m, Recur) ∼ asi.score, data = GSE62254.subtype) %>% broom::tidy(exponentiate = T)> GSE62254.subtype$ASI.HL <- ifelse(GSE62254.subtype$asi.score > median(GSE62254.subtype$asi.score), 'ASI-H','ASI-L')Note: A univariate Cox regression model is used to assess the significance of the risk score. Code for Kaplan-Meier plots is included in the shared R scripts (Figure 2B).5.Survival plot on an independent dataset.> survfit(Surv(OS.m, Death) ∼ ASI.HL, data=GSE62254.subtype) %>% ggsurvplot( pval = TRUE,conf.int = F, risk.table = T,risk.table.col = "strata",size=1,pval.size=8, xlab='Follow up (months)', ylab='OS (%)', legend.title = '',legend.lab=c('AAI-H', 'AAI-L'), ggtheme = theme_classic2(),palette = c('#FC4E07','#E7B800'), title = 'GSE62254', font.x = 15,font.y=15,font.main=18,font.legend=15,font.tickslab=1 2)


### Identify molecular subtypes via unsupervised clustering
  Timing: ∼2 h

  This section enables molecular stratification using unsupervised clustering and the construction of a subtype classifier with machine learning, validated on an independent cohort.6.Determine the optimal number of clusters using NbClust.> best.cluster <- NbClust::NbClust( data = t(gc.expr[train.gene,]), method = 'kmeans', min.nc = 2, max.nc = 5)> best_nc <- as.data.frame(t(best.cluster$Best.nc), stringsAsFactors = TRUE)> table(best_nc$Number_clusters) %>% as.data.frame() %>% filter(Var1 != 0) %>% ggbarplot(x='Var1', y='Freq', fill='darkgrey', color='darkgrey')+labs(x='Number of clusters', y='Frequency among all indices') + ggtitle('Optimal number of clusters')Note: NbClust evaluates multiple indices and selects the cluster number supported by the majority of criteria.7.Perform unsupervised clustering to define molecular subtypes.Figure 3Two molecular subtypes of GC tumors were identified and validated(A) Two molecular subtypes were identified in the TCGA-STAD dataset using the NbClust algorithm.(B–D) Silhouette analysis confirmed high intra-cluster similarity. These subtypes exhibited distinct and consistent prognostic outcomes for both overall and disease-free survival in the (C) TCGA-STAD and (D) GSE62254 datasets. Survival curves were compared via log rank test. This figure refers to the ‘Figure 4’ in our reference manuscript.> gc.cc.fit <- ConsensusClusterPlus::ConsensusClusterPlus(d = as.matrix(gc.expr[train.gene,]), maxK = 5, clusterAlg = 'km',plot='pdf')> gc.subtype$Consensus.subtype <- paste0('Cluster', gc.cc.fit[[2]]$consensusClass)> factoextra::fviz_silhouette( sil.obj = cluster::silhouette( gc.cc.fit[[2]]$consensusClass, dist(t(gc.expr[train.gene,])) ), palette = c('#609EA2','#C27664'))Note: Clustering is done using k-means with a maximum of 5 clusters. Default settings are retained for other parameters. The optimal number of clustering is determined by the NbClust algorithm (Figure 3A).Note: The output is a set of PDFs showing cluster assignments. Silhouette analysis is used to evaluate inter- and intra-cluster similarity (Figure 3B).Note: In ConsensusClusterPlus function, parameter “seed” could be set for the reproducible results.8.Train a molecular subtype classifier using machine learning.> library(randomForest)> gc.consensus.cluster.rf <- randomForest::randomForest( x = gc.expr[names(sort(apply(gc.expr, 1, mad), decreasing = T)[1:1000]),] %>% t() %>% scale(), y = as.factor(gc.subtype$Consensus.subtype))Note: A random forest classifier is trained on normalized expression data. The top 1,000 genes with the highest median absolute deviation (MAD) are used as features.Note: The trained classifier is available via the primary study’s Shiny server (https://jli-bioinfo.shinyapps.io/AAI_Aging/).Note: The prognostic differences between the two identified subtypes were assessed using the log rank test and visualized with Kaplan-Meier survival curves (Figure 3C).9.Validate the classifier on an independent dataset.> GSE62254.subtype$Consensus.subtype <- predict( gc.consensus.cluster.rf, GSE62254.expr[rownames(importance(gc.consensus.cluster.rf) ),] %>% t() %>% scale() ) %>% as.character()Note: Ensure that gene expression in the validation cohort is normalized using the same approach as the training set.Note: The identified molecular subtypes demonstrated consistent survival patterns in the validation dataset (Figure 3D).


### Establish a subtype-specific regulatory network
  Timing: ∼1 h

  This step focuses on constructing a transcription factor (TF) regulatory network specific to aggressive subtypes, followed by master regulatory analysis.10.Perform differential expression analysis.> identical(colnames(gc.expr), gc.subtype$sample)> consen.subtype.limma <- limma::lmFit(object = gc.expr, design = model.matrix(∼ifelse(gc.subtype$Consensus.subtype == 'Cluster2',1,0))) %>% limma::eBayes() %>% limma::topTable(coef = 2, number = Inf, adjust.method = 'BH')Note: In the reference study, Cluster2 (with poor prognosis) shows enriched epithelial-to-mesenchymal transition (EMT) and stromal features. This subtype is used for regulatory network analysis.11.Identify candidate TF regulons and target genes.> load('Datasets/TF_EMT_signature.rda')> mRNA.limma <- consen.subtype.limma[setdiff(rownames(gc.expr), tf.emt.sgt$TF$Symbol),]> tf.limma <- consen.subtype.limma[tf.emt.sgt$TF$Symbol,]> TF.regulon <- rownames(tf.limma %>% filter(adj.P.Val < 0.001 & abs(logFC) > 0.5))> mRNA.target <- rownames(mRNA.limma %>% filter(adj.P.Val < 0.05 & abs(logFC) > 1))12.Construct an integrative regulatory network.> rtni <- RTN::tni.constructor( expData = gc.expr[TF.regulon,] %>% t() %>% scale() %>% t() %>% as.data.frame() %>% bind_rows( gc.expr[mRNA.target,] %>% t() %>% scale() %>% t() %>% as.data.frame()) %>% as.matrix(), regulatoryElements = TF.regulon) %>% RTN::tni.permutation(nPermutations = 1000) %>% RTN::tni.bootstrap() %>% RTN::tni.dpi.filter()Note: This network processing may take some time; the visualization of the results can be found in “Figure 6” of our referenced manuscript.13.Perform master regulatory analysis.> data4enrich <- mRNA.limma$logFC> names(data4enrich) <- rownames(mRNA.limma)> rtna <- RTN::tni2tna.preprocess(object = rtni, phenotype = data4enrich, hits = tf.emt.sgt$EMT.gene$GeneSymbol) %>% RTN::tna.mra() %>% RTN::tna.get(what="mra", ntop = -1)Note: EMT-related genes are used as the phenotype-specific signature, but other gene sets can be substituted depending on study focus.14.Prioritize prognostically significant master regulators.> regulon <- rtna$Regulon[rtna$Pvalue < 0.05]> tmp <- gc.expr[regulon,] %>% t() %>% as.data.frame() %>% bind_cols(gc.subtype)> regulon <- lapply(regulon, function(x){ res.cox<-base::eval(parse(text = sprintf('coxph(Surv(OS.time, OS) ∼ %s, data=tmp)',x))) return(res.cox %>% broom::tidy()) }) %>% do.call(rbind, .) %>% filter(p.value < 0.05) %>% pull(term)Note: A hypergeometric test is used to assess enrichment of regulons in the selected signature. TFs are ranked based on hypergeometric p values and univariate Cox regression significance.


### Prioritize therapeutic candidates via drug sensitivity analysis
  Timing: ∼30 min

  This section outlines how to correlate TF expression with drug sensitivity in gastric cancer cell lines to prioritize potential therapeutic targets.15.Preprocess CTRP gene expression and drug activity dataNote: Due to large file sizes, raw data are not publicly hosted. Processed data are included for demonstration. Code is provided in the shared R scripts.16.Create a results data frame to store computed correlations.> load('Datasets/CTRP_GC.rda')> genes<-c('ELK3','SOX7')> drug.gene.df<-expand.grid(genes, rownames(ctrp.drug),stringsAsFactors = F) %>% as.data.frame()> colnames(drug.gene.df)<-c('gene','drug')> drug.gene.df$anova.p<-NA> drug.gene.df$auc<-NA17.Compute gene-drug correlations.Figure 4Two druggable TFs could be prioritized using drug sensitivity analysisThe results of the drug sensitivity analysis of (A) ELK3 and (B) SOX7. This figure refers to the ‘Figure 7’ in our reference manuscript.> for(i in 1:nrow(drug.gene.df)){ df<-data.frame( gene=ctrp.expr[as.character(drug.gene.df$gene[i]),] %>% unlist(), drug=ctrp.drug[as.character(drug.gene.df$drug[i]),] %>% unlist() ) drug.gene.df$anova.p[i]<-anova(lm(drug∼gene, df))[1,5] drug.gene.df$auc[i]<-pROC::roc( ifelse(df$drug > median(df$drug),1,0), df$gene,quiet=T,direction='<' )$auc }Note: Linear regression is used to model the relationship between gene expression and drug activity scores.Note: AUC values > 0.75 indicate sensitivity, while AUC values < 0.25 indicate resistance to the drug. These thresholds are adjustable (Figures 4A and 4B).Note: Correlation significance is assessed using ANOVA on the regression models.18.Visualize the results of drug sensitivity analysis.> drug.gene.df[drug.gene.df$gene == 'ELK3',] %>% left_join(drug.info[,c('ID','CLINICAL.STATUS')],by=c('drug '='ID')) %>% ggplot(aes(x=auc,y=-log10(anova.p)))+ geom_point(aes(color=I(ifelse((auc >= 0.75 | auc <= 0.25) & anova.p < 0.05 & CLINICAL.STATUS =='FDA approved', 'red','lightgrey'))))+theme_classic()+labs(x='AUC',y='ANOV A -log10 (P)',title='ELK3')+geom_hline(yintercept = - log10(0.05),lty='dashed',color='lightgrey')+geom_vline(xin tercept = c(0.25,0.75),lty='dashed',color='lightgrey')+ ggrepel::geom_label_repel(aes(label=ifelse((auc >= 0.75 | auc <= 0.25) & anova.p < 0.05 & CLINICAL.STATUS =='FDA approved', drug,'')),label.size = NA,max.overlaps=Inf)+ theme( legend.position = 'none', axis.text= element_text(size=15,family ="sans"), axis.title= element_text(size = 15,family ="sans") )Note: This visualization code is using master regulator “ELK3” as the example.


## Expected outcomes
  This protocol provides a comprehensive pipeline for developing a transcriptome-based prognostic model using machine learning-prioritized gene signatures (Figure 1). It enables the identification of clinically relevant molecular subtypes, construction of a subtype classifier, and inference of subtype-specific regulatory networks to prioritize master regulatory transcription factors (TFs). Ultimately, the pipeline supports the repurposing of candidate therapeutics targeting these key TFs.

  The resulting prognostic model offers a robust, clinically interpretable indicator of patient risk (Figures 2A and 2B), while the subtype classifier facilitates the stratification of independent cohorts (Figures 3A–3D). The drug sensitivity analysis further enhances precision oncology efforts by identifying subtype-specific druggable targets (Figures 4A and 4B).

  Importantly, this protocol is flexible and can be applied across various cancer types using different biological or clinical parameters (e.g., aging, immune status, metabolism). The machine learning-based strategy offers a reproducible and scalable framework for integrating biological processes with patient outcomes, tumor heterogeneity and therapeutic vulnerabilities.

  Collectively, this protocol provides a standardized modular workflow that can be adopted to predict tumor prognosis; define molecular subtypes; prioritize master regulators and further repurpose drugs for targeted therapy in heterogeneous tumor populations.


## Limitations
  A primary limitation of this protocol is the restricted exploration of machine learning algorithms for classifier construction. While we implemented a random forest-based classifier, alternative algorithms—such as support vector machines (SVMs)3 and nearest template prediction (NTP)4—have shown robust performance in tumor classification tasks. These methods were not benchmarked in the current workflow but will be considered in future updates. Although we evaluated a deep learning-based classifier, our results indicated susceptibility to overfitting, likely due to the relatively small sample size and limited number of input features.5

  Another limitation involves platform heterogeneity. The training dataset was derived from RNA sequencing data (TCGA-STAD), whereas the validation dataset was generated using microarray technology. This discrepancy may introduce batch effects and reduce reproducibility across platforms, potentially limiting the generalizability of the classifier and molecular subtypes to other datasets.

  Finally, this computational pipeline lacks experimental validation to confirm the biological relevance and clinical applicability of the inferred regulatory networks and drug sensitivity predictions. While the analytical steps are comprehensive, follow-up functional assays and clinical correlation studies are essential to substantiate the findings and advance toward translational utility.


## Troubleshooting

### Problem 1
  Genes used for classifier training are missing in the validation dataset (related to ‘Validate the classifier on an independent dataset’ section in Step 2).


### Potential solution
  Ensure consistent gene sets by selecting overlapping genes during the data pre-processing step. This helps maintain compatibility between training and validation datasets.


### Problem 2
  R packages fail to install properly (related to ‘Install R and RStudio’ section).


### Potential solution
  This issue is often due to unstable internet connections or inaccessible CRAN mirrors. Choose the most reachable CRAN mirror in RStudio or install packages locally by downloading their source files.


### Problem 3
  NA values appear in the gene expression matrix after applying the ‘scale()’ function (related to ‘Validate the classifier on an independent dataset’ section in Step 2).


### Potential solution
  Apply alternative normalization methods such as quantile normalization or min-max normalization to mitigate the issue of unit inconsistencies and prevent missing values.


### Problem 4
  No significant master regulatory transfection factors (TFs) are identified (related to ‘Prioritize prognostically significant master regulators’ section in Step 3).


### Potential solution
  Increase the number of candidate regulons and target genes to expand the regulatory network and improve detection sensitivity. Alternatively, consider integrating other regulatory layers, such as microRNA (miRNA)6 or long non-coding RNA (lncRNA),7,8 by incorporating their matched expression profiles for network inference.


### Problem 5
  Risk scores across datasets are not in the same range (related to ‘Validate the risk model on an independent dataset’ section in Step 1).


### Potential solution
  Apply min-max normalization to scale the risk scores to a standardized range (e.g., 0 to 1), ensuring comparability between datasets.


## Resource availability

### Lead contact
  Further information and requests for resources and reagents should be directed to and will be fulfilled by the lead contact, Dr. Jiang Li (author 4) (lijiang29@mail.sysu.edu.cn).


### Technical contact
  Questions regarding the technical specifics of performing the protocol should be directed to and will be fulfilled by the technical contact, Dr. Jiang Li (author 1) (lijiang37@mail.sysu.edu.cn).


### Materials availability
  This study did not generate new unique reagents.


### Data and code availability
  The authors declare that all datasets and original R codes used in this protocol are publicly available on GitHub (https://github.com/SYSUSH-LiLab/STAR_PROTOCOL_Code) and have also been deposited on Zenodo: https://doi.org/10.5281/zenodo.17078223.


## Acknowledgments
  This research was funded by the Shenzhen Science and Technology Program, grant nos. JCYJ20230807110302006 and JCYJ20240813150456074; by the Shenzhen Key Laboratory of Chinese Medicine Active substance screening and Translational Research, grant no. ZDSYS20220606100801003; and by the Seventh Affiliated Hospital of Sun Yat-Sen University, grant no. ZSQYBRJH0024.


## Author contributions
  Jiang Li (author 1): conceptualization, software, methodology, investigation, formal analysis, visualization, data curation, and writing – original draft. X.H.: investigation and writing – review and editing. Z.Z. and Jiang Li (author 4): conceptualization, writing – review and editing, funding acquisition, project administration, and supervision.


## Declaration of interests
  The authors declare no competing interests.