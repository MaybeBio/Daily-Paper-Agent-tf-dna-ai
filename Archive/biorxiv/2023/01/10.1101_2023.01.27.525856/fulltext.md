## Abstract

This study was designed to test the idea that human gene promoters have evolved to be resistant to the effects of mutations in their primary function, the control of gene expression. It is proposed that the transcription factor/transcription factor binding site (TF/TFBS) pair having the greatest effect on control of a gene is the one with the highest abundance in the promoter. Other pairs would have the same effect on gene expression and would predominate in the event of a mutation in the most abundant pair. It is expected that the overall promoter architecture proposed here will be highly resistant to mutagenic change that would otherwise affect expression of the gene. The idea was tested beginning with a database of 42 human genes highly specific for expression in brain. For each gene, information was accumulated about its expression level and about the TFBS occupancy of the five most abundant TF/TFBS pairs. Expression level was then plotted against TFBS occupancy separately for each of the five pairs, and the plots were compared with each other. The plots were found to be similar, and the results were interpreted to indicate that the TFBS occupancy ranks evolved to yield the same effect on gene expression level with multiple ranks able to function in the event of mutation in another. A similar analysis was conducted with a database of 31 human liver specific genes, and the overall result was found to be the same. Backup TFBS occupancy ranks were interpreted to be present in both brain and liver specific genes. Finally, the TFBSs in the brain specific and liver specific gene populations were compared with each other with the goal of identifying any brain selective or liver selective TFBSs. Of the 89 TFBSs in the pooled population, 58 were found only in brain specific but not liver specific genes, 8 only in liver specific but not brain specific genes and 23 were found in both brain and liver specific genes. The results were interpreted to emphasize the large number of TFBS in brain specific but not liver specific genes.


## 1. Introduction

Investigators continue to be puzzled by the large number of transcription factor binding sites present in the promoters of human genes. Whereas in prokaryotic organisms one or a very few TF binding sites suffice for the regulatory needs of most genes, hundreds are the rule in human gene promoters. For instance, a total of 357 TFBS are annotated in DLGAP3, a human gene of average length. High TFBS numbers are also the rule in the genomes of other eukaryotes. Further, in many human genes distinct TFBS clusters are observed outside the promoter but within the coding region of a gene. Five such clusters are annotated in DLGAP3 [ 1 , 2 ].

Reasonable suggestions have been advanced to account for the large number of TFBS found in the genomes of eukaryotes. TFs and TFBSs have been proposed, for example, to be involved in specifying the tissue where a gene is expressed, a feature less relevant in prokaryotes [ 3 – 6 ]. Eukaryotic gene expression could be controlled by combinations of TFs in a way that would require an increased number of TFBSs [ 7 – 9 ]. Despite the availability of reasonable suggestions, however, there is currently no consensus about the role of the “extra” TF/TFBSs present in eukaryotic genomes.

The study described here was carried out to test the idea that the large number of TFBSs in eukaryotic promoters has evolved to protect the regulatory region from the effects of mutations. Since the interaction of a TFBS with its TF occurs in the promoters of many different genes, it is reasonable to expect that additional protection against mutagenic change may be required for TFBS compared to DNA regions with fewer interaction targets. The hypothesis tested in the present study proposes that the additional TFBS in eukaryotes has evolved to meet the need for the additional protection against mutation in the TF/TFBS contact.

The mechanism proposed for protection depends on the abundance of binding sites for a TF in the promoter. It is suggested that expression of a gene depends to the greatest extent on the TF that binds in the highest abundance TFBS. Lesser effects on transcription would be provided by TFBS with lower abundance in the promoter. This situation would prevail until there is a mutation causing loss of the highest abundance TF/TFBS interaction. In that case the second most abundant TFBS/TF pair would become the most abundant and gene expression would continue unchanged because the new highest abundance TFBS would dominate regulation of transcription. The proposal depends on the idea that transcription regulation depends on the identity of the highest abundance TF/TFBS pair, not on the identity of the individual TF/TFBS pair involved. A variety of different TF/TFBS pairs are proposed to be able dominate regulation of a gene if the pair is the most abundant one in the promoter.

The study described here was designed to test the idea outlined above for control of gene expression. It was reasoned that if control were indeed dominated by the most abundant TF/TFBS pair, then a recognizably similar result should be obtained if one plotted gene expression level against TFBS occupancy for the most abundant TFBS/TF pair or the second most abundant or the third and so on. If the second most abundant pair has evolved to take the place of the most abundant in the event of a mutation, then the second most abundant pair should have a similar effect on transcription as the first.

The study was performed beginning with a database of 42 human genes each with highly selective expression in the brain. Public databases were used to accumulate the expression level of each gene and the ChIP-seq signal from each of the five most abundant TFBSs. Expression and ChIP-seq results were then plotted for each TFBS abundance level with the expectation that the plots with the different abundance levels would resemble one another. Such similarity would support the view that the second most abundant rank of TFBS would have the ability to replace the first if the first were lost due to mutation.

A similar study was conducted with a database of human genes with highly selective expression in liver. Information was collected about gene expression level and TFBS occupancy for different abundance ranks as described for the brain database. Plots of expression against ChIP-seq signal were created in the same way. It was anticipated that the outcome of the liver study would clarify whether the brain results are unique to brain or if they would apply more broadly.

Finally, a study was focused on the TFBSs present in the brain database. All TFBSs in the brain population were pooled and compared to the similar pool of TFBSs in the liver group. The results were expected to identify any instances of brain-selective or liver-selective TFBSs.


## 2. Materials and Methods


## 2.1 Gene databases: gene expression and TF binding levels

Brain specific genes were accumulated for the study from a combination of locally curated genes and those from the database of Sonawane et al, [ 3 ]. Focus was on a tissue specific gene population to maximize the possibility that conclusions would apply to the level of gene expression and minimize contributions from the potential effects of TFs on tissue distribution. Tissue expression for each gene was obtained from the GTEx Portal of RNA-seq results found in the UCSC Genome Browser (version hg38 ( https://genome.ucsc.edu/ )). A gene was considered to be brain-specific if its expression was 10-fold or greater in brain than in the tissue with the next highest expression level. The database of liver-specific genes was curated using the same procedure described above for brain.

For each gene examined, the TF binding abundance of each TFBS was determined from the ChIP-seq values reported in the ENCODE project database of cis-Regulatory Elements (3 November 2018 version) by way of the UCSC Genome Browser. Entries were included from the promoter and from other TFBS clusters within the gene coding region. Table Browser was searched on Regulation followed by TF Clusters, and the output was focused on the “score” entry. The score was summed for each TFBS as there were several (usually ~3-10) identical TFBS in each gene. The highest scoring TFBS and its score were then recorded in the brain-specific or liver-specific database under the heading “ChIP1.” Values for the second highest TFBS were recorded under ChIP2 and so on through ChIP5. Note that the TFBS associated with the ChIP1 rank cannot be the same as that for ChIP-seq2, or ChIP-seq 3 and so on. For each gene, each ChIP-seq rank has its own TFBS.


## 2.2 Gene databases

TFBSs in brain specific and liver specific gene promoters Two TFBS populations were accumulated for the brain specific genes, (1) all TFBSs present in the database (i.e., 5 for each gene) and (2) all non-redundant TFBSs in the database. The same two populations were accumulated for the liver-specific genes.


## 2.3 Data analysis

Data were manipulated with RStudio and Excel. Graphic rendering was done with SigmaPlot v14.5.


## 3. Results


## 3.1 Experimental strategy

The analyses described here were designed to test the idea that the promoter regions of human genes have evolved to create redundant layers of TFBS groups able to substitute for one another in the event of mutagenic damage to the promoter. Relevant TFBS groups were identified according to the abundance of their occupancy by the cognate TF as determined from the results of ChIP-seq studies. For each gene, the highest abundance TFBS/TF pair was put into one pool (rank 1), the second most abundant was put in a second pool (rank 2) and so on to rank 5. Each data point therefore has its own TF and its own level of TFBS occupancy. If the information described above is to function in a redundant or backup manner to control the level of gene expression, then it is expected that each TFBS/TF rank will have the same effect on the level of gene expression. This is the expectation that was tested in the studies described below. It was assumed that a positive result would support the existence of redundant layers of regulatory control in human gene promoters.


## 3.2 Effect of TFBS occupancy rank on brain specific gene expression

The effect of TFBS occupancy rank on gene expression was examined with a population of 42 protein coding, human, brain specific genes (see Supplementary Table 1 ). For each occupancy rank the ChIP-seq signal was plotted against the gene expression level, and the results for the first three ranks are shown in Fig. 1 . Clear similarities were observed among the three ranks in the expression/ChIP-seq signal relationship. For instance, in the lower left of the plot the RTP1, PNMA6F and FGF3 genes are found in similar locations in the three abundance ranks. Near the center of the plot, HTR5A, HCRT and TLX3 are located similarly. CACNG8, TBR1 and CREG2 locations are related in all three plots. The results are interpreted to indicate that the three ChIP-seq abundance ranks have the potential to serve in a redundant fashion to drive expression of the genes to the same level. It is suggested that the small differences observed in ChIP-seq signal for the same gene in separate ranks might produce tolerable results if one rank needed to be substituted for another.


## 3.3 Effect of TFBS occupancy rank on liver specific gene expression

To test the generality of the results described above with brain specific genes, a similar analysis was carried out with liver specific genes. A population of 31 liver specific human genes was first identified, and each gene was assigned to a set of five ranks based on TFBS occupancy in the promoter (see Supplementary Table 2 ). The occupancy score, as measured by the ChIP-seq signal, was then plotted against the gene expression level.

The results showed that the same genes were found in similar locations in the three plots (see Fig. 2 ). CFHTR3 and UGT2B10, for instance, are located in the high expression part of each plot with CFHR3 at the lower ChIP-seq signal end. An arc of four genes with varying expression levels is found in all three plots near the low ChIP-seq signal level (see SPP2, SERPINA7, F13B and SLC22A10). All plots also have a cluster of four genes at the high end of the ChIP-seq axis (i.e., genes MBL2, INHBC, SLC22A25 and INS-IGF2). The results are interpreted to indicate that the three ChIP-seq abundance ranks can serve in a redundant or backup manner to shield expression of the gene from mutagenic change in the promoter. Further, the results show that the same backup promoter design is found in liver specific as well as brain specific human genes.


## 3.4 TFBSs in the promoters of brain and liver specific human genes: all database TFBSs

The information accumulated here about promoter content of TFBSs provides the opportunity to compare the promoters of brain specific and liver specific genes (see Supplementary Tables 1 and 2 ). While previous studies have demonstrated a degree of tissue selectivity to TFBSs, it is rare for such studies to involve the large populations of tissue-specific genes available here [ 10 ]. For analysis, TFBSs in the promoters of brain specific genes were assembled in two forms, (1) all the TFBSs shown in Supplementary Table 1 . That is, the five most abundant TFBSs in each of the 42 brain specific genes or 210 TFBSs in all: and (2) the population of non-redundant TFBSs. Each TFBS is counted only once regardless of how many times it occurs in the overall population. The same two TFBS populations were assembled for the liver-specific genes. Finally, histograms were plotted to show the count of each TFBS in the total population ( Figs. 3 and 4 ).

The results for brain specific genes emphasize binding of TFs that use histone methylation to influence gene expression ( Fig. 3 ). For instance, of the five most abundant TFBSs three (EZH2, SUZ12 and RNF2) are components of polycomb repressive complex 2 (PRC2), a complex that uses histone methylation to attenuate gene expression [ 11 , 12 ]. A fourth, KDM4A, also uses histone methylation to regulate transcription [ 13 ]. The result points to an important role for histone methylation in the regulation of brain specific genes.

No similar emphasis on histone methylation was observed with liver-specific genes ( Fig. 4 ). Of the seven most abundant TFBSs, three bind TFs that attract transcription machinery by binding to the promoter region (i.e., FOXA1, FOXA2 and HNF4A) [ 14 – 16 ]. Three of the four remaining TFBSs affect transcription of a wide variety of genes. RXRA mediates the effects of retinoids while SP1 and YY1 can activate or repress gene expression depending on other factors [ 17 – 19 ]. Comparing the brain and liver specific gene populations suggests the dominant mechanisms of gene regulation are distinct in the two tissues.


## 3.5 TFBSs in the promoters of brain and liver specific human genes: all unique database TFBSs

Non-redundant TFBS in the brain and liver specific databases were accumulated with the expectation that they might identify TFBSs found in brain-specific genes, but not in liver specific ones. TFBS found in liver specific, but not brain specific genes would also be identified. Scans of Supplementary Tables 1 and 2 revealed the presence of 81 non-redundant TFBS among the 210 total brain-specific genes and 31 among the 155 liver-specific genes ( Table 1 ). Percentages were 39% in the case of brain specific genes and 20% for liver. Among the 81 non-redundant brain TFBS, 58 (72%) were found in the brain population only and 23 (28%) in both brain and liver populations. In the 31 non-redundant TFBS in liver, 8 (26%) were found in liver, but not brain and 23 (74%) in both liver and brain.

Two conclusions stand out from analysis of the non-redundant TFBS populations described above. First is the high proportion of non-redundant TFBS among the brain specific genes (58 in the 81 total non-redundant TFBS population). For liver, the comparable figures are 8 of 31 non-redundant TFBS. The high proportion among brain genes may result from a greater need for gene regulatory activity in the brain due perhaps to a greater number of functionally distinct regions in the brain or to a more diverse developmental program.

Second is the absence of any evidence for a tissue specific TFBS. All the TFBS found in the brain-specific gene population, for instance, are those that can be readily identified in the promoters of non-brain genes. The same is true for the TFBS identified here in liver specific, but not brain specific genes ( Table 1 ). All can be found abundantly in other human genes. The overall finding indicates that the role of TF in influencing the tissue where a gene is expressed must involve multiple TFs or TFs in combination with other regulatory mechanisms.


## 4. Discussion


## 4.1 Backup organization to allow promoter function to co-exist with mutagenic damage

The backup system of promoter organization suggested by the results described here is distinct from other methods humans use to deal with mutagenic change to the genome. The suggested system does not result in prevention of mutations or correction of them once they have occurred. Rather, the system describes a method promoters use to continue to function normally despite the existence of mutations in their own sequences. The results indicate the existence of backup or redundant systems of TFBS that are each able to provide gene regulatory function in the event of mutagenic damage to another. An individual promoter is thereby able to co-exist with a diverse background of mutagenic events using methods that complement other mechanisms that prevent or correct mutations.

The backup system can be understood as related to other genome-wide features that are able to allow the individual to accommodate potentially disastrous mutagenic events. An example is the way genes encoding proteins that are parts of a single structure or function are distributed widely in the genome rather than being together in a cluster. The 31 genes encoding distinct protein components of the human nuclear pore complex are an example. The genes are spread among 17 different chromosomes increasing the likelihood that damage to any one gene might be able to be accommodated by the overall structure [ 20 , 21 ]. This arrangement prevents a mutation in a single chromosome from affecting more than one or a few nuclear pore genes. Other distributed genomic elements that enable humans to co-exist in a mutagenic environment include gene enhancers, homologous genes and exons distributed within the same gene [ 22 – 25 ].


## 4.2 High TFBS content of eukaryotic promoters

The system of backup TFBSs proposed here is consistent with and supports the observation that the promoters of human genes and those of other eukaryotic organisms contain many more TFBSs than those of prokaryotes. The ChIP-seq signal from the most abundant TFBS is in most cases a sum of several individual TFBSs in the promoter. The same is true of the second most abundant TFBS, the third and so on. It is easy to imagine therefore that the number of individual TFBSs in the aggregate of all abundance classes (i.e. ranks) might reach the high number observed in an entire gene promoter region.


## 4.3 Tissue specific genes

This study was focused on tissue specific genes with the idea that the results might clarify the way tissue specificity is encoded in promoters. The results confirmed a previously noted selectivity of HNF4A for liver genes [ 26 ]. A binding site for HNF4A was observed to be among the five most abundant in 19 of the 31 liver specific genes examined here (see Supplementary Table 2 ). Evidence for other tissue specific TFBSs was less convincing. For instance, 21 different TFBS were found among the 42 highest abundance TFBS in the brain specific genes examined here (see Supplementary Table 1 ). Overall, the results provide little support for the view that there is a single TF that uniquely determines the tissue location of a brain or liver specific human gene.


## 4.4 Role of TFBS occupancy in the level of gene expression

The results described here provide a test of the idea that the level of TF binding to its TFBS may influence the level of a gene’s expression, at least in some cases. Support for the idea would be obtained if the level of TFBS occupancy as measured by the ChIP-seq signal were found to be correlated with the level of gene transcription. Such correlations can be found in both the brain and liver gene populations examined here (see Figs. 1 and 2 ).

Among the brain genes an inverse correlation is observed among the genes ZP2, BARHL1, CREG2, CACNG8 and TBR1 in all three abundance ranks plotted. In the liver gene population, a positive correlation is observed relating genes F13B, SERPIN7, SPP2 and UGT2B10 in all three ranks shown. The results suggest that expression of genes in the brain group is repressed by TFBS occupancy in all three TF ranks while expression is activated in the liver gene group. In both cases the results support the view that interaction of TF and TFBS can have an influence on transcription level in the genes involved.


## Supplementary Tables