## Abstract

Mutations in the DNA can affect cancer development and progression not only by changing the amino acid chain but also by affecting different regulatory elements such as transcription factors. This study introduces a novel pipeline to identify “mutation blocks” - small genomic areas with high mutation rates that potentially influence transcription factors binding. By analyzing GCB lymphoma patient data, mutations blocks were identified that correlated with gene expression changes and were linked to transcription factor activity. These mutation blocks suggest a selection for mutations that alter gene regulation, contributing to lymphoma development. The analysis identified 56 mutation blocks in germinal center B-cell like diffuse large B-cell lymphoma (GCB DLBCL) patients’ genomes, affecting genes such as BCL2, MYC, SGK1, and PIM1, and linked to transcription factors including MSC, TCFL5, HOXB7, FOXP3, and ZBTB6. A machine learning model that used gene ontology data suggested further potential transcription factors-gene pairs influencing cancer. These findings highlight the role of synonymous and silent mutations in altering transcription factors binding and gene expression, offering insights into the mechanisms of GCB lymphoma.


## 1 Introduction

Mutations in DNA are considered a central driver of neoplasm development and, consequently, cancer [ 1 ]. While some mutations are found in the coding region of the gene and may alter the protein by changing its amino acid sequence, other mutations, such as silent mutations, do not affect protein structure.

Regardless of its effect on the amino acid sequence, a mutation might affect gene regulatory mechanisms and contribute to cancer development[ 2 − 4 ]. Previous studies have shown mutations that disrupt exon splicing sites[ 5 , 6 ]. Other studies have identified synonymous mutations in the coding region that replace nucleotides without altering the amino acid sequence but still affect regulatory processes[ 7 − 9 ].

Transcription factors (TFs) are proteins that regulate gene transcription by binding to specific DNA sequences. Depending on their function, transcription factors may either activate transcription (activators) or suppress it (repressors). This regulatory mechanism plays a significant role in cancer development[ 10 , 11 ]. Thus, mutations in a gene may have little to no effect on the resulting protein but can significantly impact transcription factor binding sites, thereby altering gene regulation[ 12 − 14 ].

The BCL2 family comprises a group of genes responsible, for regulating apoptosis— the intrinsic cell death mechanism. One of its key members is the BCL2 (B-Cell lymphoma 2) gene, which functions as a pro-survival gene by inhibiting the release of cytochrome C. This, in turn, prevents the activation of caspase-9, thereby suppressing apoptosis. Due to its major role as a pro-survival gene, malfunction of BCL2 may interfere with the apoptosis system [ 15 , 16 ] and overexpression of BCL2 is known to be connected to large diffuse B-cell lymphoma (DLBCL), the most frequent B cell Non-Hodgkin’s lymphoma. The translocation BCL2(14;18)(q32;q21) is a common trait among DLBCL patients. This translocation found to be the cause of 20-30% of over-expression of BCL2 among DLBCL patients [ 17 , 18 ]. Moreover, the translocation BCL2(14;18)(q32;q21) is known to increase the creation of mutations on the BCL2 gene (hypermutation), synonymous mutations included[ 17 ]. Germinal Center B Cell-Like (GCB) is a sub-group of DLBCL, distinguished by gene expression profiling[ 19 ].

A previous study showed that among GCB lymphoma patients, two recurrent synonymous mutations in the coding region of the BCL2 gene may affect MSC repressor binding[ 8 ]. In this study, we did not focus on specific mutations but instead identified small genomic regions with high mutation density, which we termed mutation blocks. Since transcription factors bind to short DNA sequences, we hypothesize that different mutations within the same region may similarly impact cancer development by altering transcription factor binding sites. Therefore, we analyzed large-scale genomic data, including data from GCB lymphoma patients, to identify mutation blocks that may alter transcription factor binding potential.


## 2. Results


## 2.1 A pipeline for finding mutations affecting TF binding sites

A multistage data pipeline was developed to identify genomic regions and associated transcription factors that together exhibit all of the following features:

These regions have a high mutation rate in cancer patients, suggesting positive selection for mutations in these sites

Mutations in these regions correlate with changes in gene expression within the same genomic region

A transcription factor-related mechanism may explain these changes We refer to these genomic regions as mutations blocks.

The pipeline begins with the selection identification stage, where mutations blocks (genomic regions with a high mutation rate in cancer patients) are first identified. Next, in the RNA validation stage, we identify mutation blocks where mutations correlate with changes in gene expression within the same region. Finally, we select mutation blocks that affect gene expression and proceed to the transcription factor analysis stage. This stage consists of three tests. The first test, tissue validation , ensures that the transcription factor is active in the same tissue where the cancer occurs. The second test, mechanism validation , verifies that the transcription factor’s role (activator or repressor) aligns with the observed gene expression changes from the RNA validation stage. The final test, binding change verification , calculates the predicted change in the transcription factor’s binding affinity (either stronger or weaker binding to the genome). Using this predicted binding change, we assess whether the observed gene expression effects are biologically plausible.

The final output of this pipeline consists of trios, each containing three components:

Mutation blocks with an increased mutation rate in a specific cancer type.

Genes where these mutation blocks are located and show altered expression.

Transcription factors influenced by these mutations, which are active in the relevant tissue and have a plausible regulatory mechanism.

A visualization of the pipeline is provided in Fig. 1 . All the details appear in the methods section.


## 2.2. Systems biology study of mutations blocks

Mutations in the binding sites of various transcription factors may play a key mechanism in the development of GCB Lymphoma – a selection toward numerous binding sites mutations blocks in different genes were found in GCB lymphoma patients. Mutations within these blocks are correlated with changes in the expression of the relevant genes. In addition, mutations in these mutations blocks Result in significant changes in the predicted binding affinity of transcription factors to the gene. Given the extensive number of mutations blocks identified, we hypothesize that this mechanism (mutations in the binding sites of transcription factors) is a key driver in GCB lymphoma.

Certain genes and transcription factors may play a crucial role in the development of GCB lymphoma – in some genes (BCL2, MYC, and SGK1) Multiple mutations blocks in potential binding sites have been identified. For some transcription factors (FOXP3, HOXB7, MSC, TCFL5 and ZBTB6) multiple sites of mutations blocks with binding potential for these transcription factors were found. The recurrence of these genes and transcription factors with mutation blocks exhibiting a high mutation rate in GCB patients suggests their key role in GCB lymphoma development.

The pipeline output includes 56 distinct mutations blocks identified in GCB patients. These mutations blocks are located in oncogenes with a high concentration of mutations. Patients with mutations in these blocks showed significant changes in the expression of the corresponding gene. In addition, Additionally, a plausible transcription factor-related mechanism was identified for each of these mutations blocks. Therefore, we hypothesize that these mutation blocks alter the binding affinity of specific transcription factors, thereby affecting gene expression.

Certain genes and transcription factors were identified multiple times in the results. suggesting their broader role in GCB DLBCL Their expression was affected in several distinct locations across the genome. A heatmap of the 56 mutations blocks, the genes in which they were found and the transcription factors that they might affect is on Fig. 2 . Note that each mutations block affects a single gene but may influence the binding of multiple transcription factors. Several mutation blocks were identified in the following genes :

BCL2 − out of 56 mutations blocks identified in the results, 14 are located along the BCL2 gene. BCL2 is a regulator that prevents apoptosis, the cellular death mechanism[ 15 ]. Mutation in all 14 mutations blocks are corelated with upregulation of BCL2 and thereby preventing cell death. Additionally, BCL2 is known for its association with DLBCL[ 18 ].

MYC − Five mutations blocks were identified along the MYC gene. MYC is an oncogene that influences various cellular processes, including apoptosis, DNA damage response, and the cell cycle[ 20 ]. All of the mutations blocks found in MYC lead to overexpression of the gene, which is also associated with DLBCL[ 21 , 22 ].

SGK1 − Another five mutation blocks were identified on the SGK1 gene, leading to its overexpression. SGK1 is a protein kinase whose malfunction is associated with various types of cancer[ 23 ]. Additionally, SGK1 is known to generate hyper-stable proteins in DLBCL patients, which affect the progression of DLBCL[ 24 ].

PIM1 − Three of the 56 mutation blocks were identified in the PIM1 gene. PIM1 is a serine/threonine kinase that is overexpressed in many human cancers[ 25 ] including DLBCL[ 26 ]. All three mutations blocks found in PIM1 lead to upregulation of the gene.

The following transcription factors were identified as potential contributors to multiple mutation blocks:

MSC (also known as ABF1) − Six of the 56 mutation blocks were found to potentially affect the binding of the MSC repressor. MSC is a transcription factor known to be active in lymphocytes[ 27 ] and has previously been associated with lymphoma[ 28 ]. These six mutation blocks may lead to overexpression of BCL2 (three blocks), MYC (two blocks), and SGK1.

TCFL5 − four mutations blocks were found to potentially affect TCFL5 binding. The TCFL5 repressor plays an important role in spermatogenesis, the immune system, and cancer[ 29 ]. In all four mutation blocks, the binding affinity of TCFL5 is reduced, leading to overexpression of BCL2 (two blocks), PIM1, and BCL7A.

HOXB7 − three mutations blocks out of 56 found to potentially affect the binding of HOXB7 activator. HOXB7 regulates a variety of genes and several oncogenic pathways, and it is overexpressed in cancer[ 30 ] and has also been correlated with DLBCL[ 31 ]. Mutation in all three mutation blocks are corelated with increase in the binding of HOXB7, leading to the overexpression of the genes RHOH, MYC, and SGK1.

FOXP3 − three out of the 56 mutations blocks found to potentially affect the binding of the repressor FOXP3. FOXP3 induces immunosuppressive functions in cells[ 32 ] and is highly expressed in the tissues of DLBCL patients[ 33 ]. Two of these mutation blocks are located along the BCL2 gene, and one is on MYC, all of them reduce the binding affinity of the FOXP3 repressor, leading to overexpression of the BCL2 and MYC genes.

ZBTB6 − three mutations blocks found to potentially affect the binding of ZBTB6 repressor. ZBTB6 is a member of the BTB-ZF transcription factor family and has been connected to B-cell development[ 34 ]. Mutations in all three mutations blocks are corelated with overexpression of different genes: BCL2, PIM1 and SGK1.

As an example of the pipeline results, a single mutation block analysis will be presented. Additional analyses of five mutation blocks related to MSC can be found in the supplementary data section 2, along with a csv table summarizing all 56 mutations blocks.

Mutations block 63319682 − MSC binding affecting BCL2:

This mutations block includes 14 different mutations in the 5’ prime UTR that were found 32 times (among 241 GCB DLBCL patients). The block is located on chromosome 18: 63319682-63319692, where the BCL2 gene is found. A detailed representation of the identified mutations is provided in Fig. 3 .

To validate the effect of this mutation on gene expression, BCL2 expression levels were analyzed. Patients with the mutations exhibited significantly higher BCL2 expression compared to randomized groups of GCB lymphoma patients (P-value = 0.0013; see Fig. 4 ) This overexpression of BCL2 may contribute to cancer progression due to its anti-apoptotic function.

A search for relevant transcription factors that could explain the observed change in expression was conducted. Only transcription factors expressed in EBV-transformed lymphocytes were considered and analyzed for changes in their binding ability to the relevant genomic region. One transcription factor was identified as a potential cause of the observed BCL2 overexpression: MSC. The mutations in the identified mutation block interfere with the binding of the MSC repressor to BCL2, as shown in Fig. 5 , potentially leading to BCL2 overexpression.


## 2.3 Gene ontology is associated with the reported TF-gene induced by cancer mutations

We suspected that additional TF-gene pairs influencing cancer may have been missed due to data limitations. To address this, we applied machine learning techniques to identify potential TF-gene pairs that were not detected in our initial analysis. To achieve this, we utilized two distinct datasets, both separately and in an integrated manner:

Gene Ontology (GO)[ 35 , 36 ] as the connection between transcription factor and gene can be examined by assessing their functional relationships.

Protein-Protein Interactions (PPI)[ 37 ] as the connection between transcription factor and gene can be examined by assessing their functional relationships based on the relationships between different proteins

For each method (GO and PPI), a graph was constructed: for PPI, a graph of genes, and for GO, a graph of terms and genes. For each node in these graphs, a vector representation was generated using the Node2Vec algorithm[ 38 ]. Each possible transcription factor-gene pair was then represented by a joint vector, created by merging the respective vectors of the transcription factor and the gene. The previously identified cancer-related mutation blocks in genes were used as positive data, while pseudo-negative data was generated. Finally, a LightGBM[ 39 ] supervised learning model was trained on this data and evaluated for accuracy. To verify the significance of the results, another GO graph was created, this time with randomized associations between gene/term and their respected vectors.

Using only GO data, the model was able to predict gene-transcription factor pairs with a modest accuracy (all results above 0.5, best accuracy result is 0.589). In contrast, the randomised GO version and using only PPI data did not yield any significant results. When the two datasets (GO and PPI) were merged, the results were similar to those obtained using only GO data (see full results in supplementary data table 1). These findings suggest that the functional relationship between the gene and transcription factor, as represented by the GO data, provides some predictive value for their potential connection to cancer. However, their ability to physically bind, as represented by the PPI data, did not contribute significantly to the prediction.


## 3 Discussion

The findings of this study highlight the critical role that synonymous and silent mutations, particularly within transcription factor binding sites, play in the development of GCB lymphoma. Traditionally, the focus of cancer genomics has been on mutations in coding regions that directly alter protein function. However, this study expands the perspective by demonstrating that synonymous mutations or those in synonymous and silent regions can have a profound impact by modifying gene regulation through changes in transcription factors binding affinity.

The identification of 56 mutation blocks in GCB DLBCL patients highlights the significance of clustered mutations in specific regions of the genome. These mutations, correlated with changes in gene expression, suggest a selective pressure in cancer development towards disrupting expression using regulatory mechanisms. Notably, the study points to genes such as BCL2, MYC, SGK1, and PIM1—all known to be involved in oncogenesis. The change in expression of these genes, likely driven by disrupted transcription factors binding, aligns with their established roles in promoting cell survival, proliferation, and tumor progression.

An important contribution of this work is its focus on the transcription factors MSC, TCFL5, HOXB7, FOXP3, and ZBTB6. These transcription factors are already known to play a role in cancer or lymphocytes, but the discovery of multiple mutation blocks affecting their binding sites suggests that these transcription factors might have even broader implications in GCB DLBCL pathogenesis. For example, the recurrent mutation blocks found in BCL2 associated with MSC binding, support a model in which disrupted transcription factors regulation contributes to their overexpression and thus, to lymphoma development. These TFs may serve as potential therapeutic targets or biomarkers, as their activity seems to be linked to key oncogenic processes in lymphoma.

Furthermore, the use of machine learning to predict additional transcription factors-gene pairs based on gene ontology (GO) data represents a novel approach that can expand the scope of the study beyond the available dataset. The modest predictive success of gene ontology-based models indicates that while functional relationships between genes and transcription factors can inform their cancer relevance, further refinement in the model—perhaps integrating more nuanced datasets or additional biological features—may be needed to improve predictions. The lack of signal in the protein-protein interaction (PPI) dataset is intriguing and suggests that the functional relationship between gene and transcription factors as reflected by interactions between proteins, may not be as critical in this context as their functional associations. This may be related to the fact that transcription factors mainly interact with DNA molecules and not proteins and/or to noise and bias in PPI networks.

One of the most significant implications of these findings is the potential for clinical translation. Identifying mutation blocks that disrupt transcription factors binding opens new avenues for precision oncology. Drugs targeting specific transcription factors or the pathways they regulate could be developed or repurposed to counteract the deregulation caused by these mutations. Moreover, the mutation blocks identified in this study could serve as biomarkers for GCB DLBCL prognosis or treatment response, allowing for more personalized therapeutic strategies.

However, there are some limitations to consider. The study’s reliance on genomic data from a specific cancer type, GCB lymphoma, means that the generalizability of the findings to other cancers remains uncertain. Additionally, while correlations between mutation blocks, transcription factors binding, and gene expression changes are compelling, further experimental validation is needed to confirm the causal role of these mutations in altering transcription factors binding and driving cancer progression. Functional assays could be employed to directly measure transcription factors binding in these regions.

In conclusion, this study provides compelling evidence that mutations, including synonymous and silent mutations which affect transcription factors binding sites, are key drivers in GCB lymphoma. The pipeline developed here offers a robust framework for identifying similar mutation blocks in other cancers, paving the way for deeper insights into cancer regulatory mechanisms. Future work should focus on validating these findings experimentally and exploring the therapeutic potential of targeting the transcription factors implicated in these mutation blocks.


## 4. Methods

A pipeline was developed to detect driver mutations in cancer that affect transcription factor binding. This pipeline processes patient mutation data from a specific cancer type using a step-based method to identify relevant mutations. First, we search for areas in the genome with a high mutation rate, particularly within cancer-related genes. A high mutation rate suggests selective pressure in cancer development. Next, we validate, using RNA sequencing data, that mutations in these regions—referred to as mutation blocks—are correlated with changes in gene expression, as expected for transcription factor-related mutations. We then examine which transcription factors might be impacted by these mutation blocks, based on their binding ability and the effect of mutations on this binding. Lastly, we apply three validation methods to ensure the pipeline outputs relevant mutations: confirming that the transcription factor is active in the tissue relevant to the cancer type, verifying the biological logic of the proposed mechanism, and validating the significance of the binding affinity change. A detailed explanation of each step follows. A visualization of the method is shown in Fig. 1 .


## 4.1 Selection identification

Data from patients with malignant lymphoma, specifically those with germinal center B-cell derived lymphomas (GCB), were obtained from the ICGC-MMML-Seq (Molecular Mechanisms in Malignant Lymphoma by Sequencing) Consortium[ 40 ]. This dataset includes simple somatic mutations (SSMs) from 241 patients and sequence-based gene expression data for 105 patients. Initially, we performed a preprocessing step to enhance our SSM data. During this step, we converted the mutation locations in the genome from GRCh37 to GRCh38 using the UCSC Genome Lift Tool[ 41 ].

To identify the mutations blocks − areas in the genome with high mutations rate we have used the following process. First, for each chromosome all mutations of GCB patients were acquired. Then the initial blocks were created using a sliding window in the size of 10 nucleotides. Afterwards, high mutated blocks were chosen by taking only 5% of blocks with the highest number of mutations (out of blocks that have one or more mutations). Lastly all high mutated blocks that were overlapping blocks were merged into a bigger block, and these are the final blocks that resemble areas with high mutations rate in GCB patients.


## 4.2 RNA validation

Using the highly mutated blocks and cancer related genes database (COSMIC[ 42 ]) we identified cancer related genes that are found in the blocks’ locations. Then, going over each of these genes and using RNA-seq data from the ICGC of GCB patients a data set of the expression of certain gene per patient is created. We then calculated the mean expression of the gene for patients with a mutation in the block area, is found. In parallel, a random model of expression was created by randomly selecting groups of patients (same size as the number of patients with mutations in the relevant block) and calculating their mean expression. We repeated this process 10,000 times to generate a random model that was created and the patients with mutations in the block mean expression were measured against it to calculate p-value.


## 4.3 Transcription factor analysis

This step is composed of three different sub-steps: the binding grade change verification, tissue validation and mechanism understanding. Together, these sub-steps provide a comprehensive approach that is greater than the sum of its parts. These three results help identify transcription factors whose binding is significantly impacted by the mutations in the mutations block (binding grade change verification), that are active in the relevant tissue (tissue validation) and that their mechanism of action is consistent with the effect seen in the previous expression test.


## 4.4 Binding change verification

In this step the effect of the mutations on the binding ability of different transcription factors is tested. Using JASPAR’s[ 43 ] PSSM binding data, we acquired the binding score (which represents the binding probability) of each human transcription factor (746 in total) to the mutations block area without the mutations and compared it to the mean score of the mutated block (by applying each mutation independently and normalizing by the number of mutations found in patients). Afterwards we considered only transcription factors that were highly affected by the mutations in the mutations block, by considering only transcription factors that their change in the binding score has a z score higher than three or lower than minus three (using all other transcription factors as a background model).


## 4.5 Tissue validation

This step is crucial in order to validate that the transcription factor found is indeed relevant to this cancer type. To this end, GTEx database, which provides expression data across various tissues[ 44 ] was used to validate whether the highly influenced transcription factors from the binding grade verification are indeed present in the relevant tissue − lymphocytes, compared their expression levels to other tissues.


## 4.6 Mechanism validation

Finally, we assessed if whether the proposed mechanism, in which mutations in transcription factor binding sites influence gene expression, is biologically valid. Therefore, using gene ontology[ 35 , 36 , 45 ] the transcription factor type (either it is an activator or a repressor) was found. Then, we took each trio of transcription factor type, binding probability change, and gene expression change and checked if the trio form a biologically plausible mechanism. For example, if the binding of a repressor was harm and an increase in the gene expression was found − the entire suggested mechanism makes a biologically reasonable mechanism.


## 4.7 System biology analysis

Finally, a macro-level analysis of the results was made as a means to discover the broad effects of these mechanisms. In this analysis the results from all chromosomes were aggregated and grouped according to transcription factors and influenced genes. This approach revealed transcription factors and genes that were recurrently affected across the dataset.


## 4.8 Machine Learning

To expand our results and identify more possible duos of transcription factors and gens that are influenced by our suggested mechanism, a machine learning approach was employed. We tried four different approaches by constructing two distinct graphs:

Gene Ontology (GO) − We constructed a graph of all GO terms[ 35 , 36 , 45 ] and then added to this graph all genes found in GO by incorporated genes associated with each term by adding them as nodes. Each gene node was then connected to the relevant GO terms. Additionally, for each cancer-related gene from COSMIC[ 42 ], if it was not already represented in the graph, we manually added it (without linking it to any GO term).

Protein-Protein Interactions (PPI) - Similar to the GO graph, we constructed a graph of all proteins and their interactions[ 37 ]. Then, we added cancer-related genes from COSMIC that were not already represented as new nodes.

Afterwards we performed a grid search with different parameters (vector length of 8, 16 and 32; walk length of 4, 8 and 16; window size of 4,8 and 16). For each group of parameters in the grid search, the following steps were taken. First we created two node2vec[ 38 ] models, one for each graph (GO and PPI). Then we represented each gene by his vector representation of its place in the graph using four different approaches − GO, PPI, merged approach (by concatenating the two previous vectors) and randomized GO in which after generating vectors for each node, we shuffled the node− vector assignments. Lastly we trained a LGBM model[ 39 ]. For positive examples we took all gene-transcription factors duos found in our study. For pseudo negative examples we took random pairs of gene-transcription factors (taking into consideration that there are millions of possible duos and only a few hundred were found in our research). To the end of measuring our results we performed 10-fold cross validation test, ensuring no leakage between the training and test sets in each fold. Specifically, a gene would appear in either the training or the test set, but not both, and the same rule applied to each transcription factor.


## Acknowledgments

The study was partially supported by the koret-berkeley-tau initiative.