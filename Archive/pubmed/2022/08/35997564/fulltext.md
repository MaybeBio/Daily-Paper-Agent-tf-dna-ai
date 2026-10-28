# MMGraph: a multiple motif predictor based on graph neural network and coexisting probability for ATAC-seq data


## Motivation
  Transcription factor binding sites (TFBSs) prediction is a crucial step in revealing functions of transcription factors from high-throughput sequencing data. Assay for Transposase-Accessible Chromatin using sequencing (ATAC-seq) provides insight on TFBSs and nucleosome positioning by probing open chromatic, which can simultaneously reveal multiple TFBSs compare to traditional technologies. The existing tools based on convolutional neural network (CNN) only find the fixed length of TFBSs from ATAC-seq data. Graph neural network (GNN) can be considered as the extension of CNN, which has great potential in finding multiple TFBSs with different lengths from ATAC-seq data.


## Results
  We develop a motif predictor called MMGraph based on three-layer GNN and coexisting probability of k-mers for finding multiple motifs from ATAC-seq data. The results of the experiment which has been conducted on 88 ATAC-seq datasets indicate that MMGraph has achieved the best performance on area of eight metrics radar score of 2.31 and could find 207 higher-quality multiple motifs than other existing tools.


## Availability and implementation
  MMGraph is wrapped in Python package, which is available at https://github.com/zhangsq06/MMGraph.git


## Supplementary information
  Supplementary data are available at Bioinformatics online.


## 1. Introduction
  Identifying the corresponding transcription factor binding sites (TFBSs) which are short and conserved DNA motifs, is crucial for studying transcription factor (TF) regulations. The footprints of Assay for Transposase-Accessible Chromatin using sequencing (ATAC-seq) can simultaneously reveal more kinds of TFBSs than traditional sequencing technologies (Bentsen et al., 2020). Furthermore, a graph neural network (GNN) can be considered as the extension of convolutional neural network, which learns the representation of target nodes via their neighbors (Feng et al., 2020). GNN has great potential in finding multiple motifs from ATAC-seq data. In this study, we develop a robust and effective tool, named MMGraph, for finding multiple motifs from ATAC-seq data.


## 2. Materials and methods
  MMGraph is based on GNN and coexisting probability of k-mers, where the coexisting probability represents the degree of association between k-mers. It consists of three components (Fig. 1): (i) a heterogeneous graph; (ii) a three-layer GNN model to get embeddings of k-mers and sequences; and (iii) coexisting probability calculation for finding multiple motifs.


### 2.1 Constructing the heterogeneous graph
  The sequence set S contains n sequences s(⋅), s(⋅)∈S. If s(i) contains TFBSs, we set label of s(i) as positive ‘1’, otherwise as negative ‘0’, i∈[1,…,n]. s(⋅) is trimmed into the same length fragments of k-mers as k(⋅) by the step of one base. We set lenk=length(k(⋅)), lenk≥5 is used in previous paper (Fletez-Brant et al., 2013). Ks(i) is a k-mer set that contains all unique k(⋅) existing in s(i). K is an m k-mer set that contains all unique Ks(⋅) in all Ks(i) of S. Three edge types are defined (i.e. similarity edges, coexisting edges and inclusive edges) to build a heterogeneous graph where s(⋅) and k(⋅) are nodes. where Wsim represents the weight matrix of similarity edges,   p ,q∈[1,…,m]. where Wco represents the weight matrix of coexisting edges, num(k(⋅)) represents the total number of Ks(⋅) that contain k(⋅); nums(k(p),k(q)) is the total number of Ks(⋅) that contain both k(p) and k(q). where Winclu represents the weight matrix of inclusive edges, tf(k(p),s(i)) is the number of k(p) existing in s(i), i∈[1,…,n].


### 2.2 Building the GNN model
  MMGraph decomposes the heterogeneous graph into three sub-graphs, i.e. similarity graph, coexisting graph and inclusive graph. Then, it uses the labels of s(⋅) as targets to train a three-layer of GNN model. The first layer learns the concatenated embedding of k(⋅) as Esc(k(⋅))∈Rds+dc, where ds and dc are the embedding dimensions of Es(k(⋅))∈Rds and Ec(k(⋅))∈Rdc from similarity graph and coexisting graph respectively. The second layer learns the embedding of s(⋅) as Esq(s(⋅))∈Rdsq from inclusive graph, where dsq is the dimension of Esq(s(⋅)). The third layer is a fully connected layer, which identifies whether a label of s(⋅) is ‘1’ that contains TFBSs or not by threshold 0.5 (Supplementary material).


### 2.3 Finding multiple motifs
  After getting the embeddings of k(⋅) and s(⋅), we calculate mutual information (MI) of k(⋅) and s(⋅) by their corresponding embedding Esc(k(⋅)) and Esq(s(⋅)). The mi(p,i) measures the information that k(p) and s(i) shared. In order to indicate MI for different s(⋅) with labels, we subdivide S into Slabel by sequences’ label of ‘1’ and ‘0’, as well as nlabel, mlabel, slabel(⋅), Kslabel(⋅) and Klabel for n, m, s(⋅), Ks(⋅) and K. The whole procedure of motifs finding includes four steps.


## 3. Experiments and results
  The experiment has been conducted on 88 ATAC-seq datasets. For each sequence set, sequences in this set were acquired by ATAC-seq footprints, which were all positive sequences with label ‘1’. We randomly shuffled all bases within a positive sequence to generate a negative sequence with label ‘0’ (Alipanahi et al., 2015). The negative sequence did not contain TFBSs, but with the same GC content as the positive sequence. The area of eight metrics radar (AEMR) was used to evaluate tools’ capability in identifying whether the sequence contains TFBSs (Zhang et al., 2022), and the P-value was used to measure the quality of tools’ found motifs. Our results show that MMGraph achieved the highest AEMR score of 2.31 while lenk=5, and could find 207 higher-quality motifs compare to four comparison tools (Supplementary data).


## Funding
  This work was supported by the National Natural Science Foundation of China [62072212]; Jilin province project (20220508125RC) and the Chinese Postdoctoral Science Foundation [2021M691211].

  Conflict of Interest: The authors declare that they have no conflict of interest.


## Supplementary Material

## Data Availability
  The data underlying this article are available in its online supplementary material.