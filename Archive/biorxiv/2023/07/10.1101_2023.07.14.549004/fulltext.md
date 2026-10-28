## Abstract

Motivation Genetic variants in noncoding regions can drive changes in phenotype disrupting transcription factor binding site (TFBS) motifs. Other tools including motifbreakR have been developed to assess the impact of TFBS-disrupting variants. Here we introduce the tfboot package for statistically evaluating the TFBS disruption across a set of variants in upstream promoter regions.

Results The tfboot package builds on motifbreakR, plyranges, and GenomicRanges to provide methods for bootstrapping TFBS disruption to statistically quantify the impact across gene sets of interest compared to an empirical null distribution. We demonstrate the analysis here on variants in the elephant genome. The tfboot package readily integrates with Bioconductor and tidyverse-based workflows.

Availability The tfboot package is implemented as an R package and is released under the MIT license at https://github.com/colossal-compsci/tfboot .


## 1 Introduction

Transcription factor binding sites (TFBS) are short DNA sequence motifs in the promoter or enhancer regions of genes where transcription factors bind to regulate gene expression. Phenotypic changes can be driven by genetic variants such as single nucleotide polymorphisms (SNPs) which disrupt TFBS ( Reshef et al ., 2018 ) – indeed the vast majority of human disease-related SNPs found through genome-wide association studies are in noncoding regions ( Edwards et al ., 2013 ; Buniello et al ., 2018 ).

The motifbreakR R package provides methods to ascertain the impact of SNPs disrupting TFBS ( Coetzee et al ., 2015 ) which function on any genome curated within Bioconductor. motifbreakR evaluates whether the sequence surrounding a SNP is a good match for a TFBS motif drawn from various sources, and assesses how the polymorphism impacts the TFBS motif compared to the wild type sequence.

A common analysis task is evaluating the collective impact SNPs in a set of genes or regions. For example, in our research we have a collection of genes known to contribute to body size in various mammalian species. Given a set of genome-wide SNPs from sequencing and a collection of genes of interest, a common question arises: do SNPs upstream of this gene set of interest disrupt TFBS more than SNPs in a randomly selected set of genes ?

Several existing tools provide methods to assess the enrichment of genomic intervals for a given feature, including LOLA ( Nagraj et al ., 2018 ), and nullranges ( Davis et al ., 2023 ). Here we introduce the tfboot package, which builds upon the motifbreakR R package to facilitate statistical analysis of SNPs disrupting transcription factor binding sites (TFBS) in gene sets using bootstrap resampling to create empirical null distributions.


## 2 Methods


## 2.1 TFBS analysis for SNPs in promoter regions

The tfboot package works with common Bioconductor objects such as GRanges for easy integration with existing Bioconductor-based workflows ( Gentleman et al ., 2004 ; Lawrence et al ., 2013 ), and bootstrapping analysis takes advantage of list-columns in tibbles as implemented in the tidyverse suite of packages ( Wickham et al ., 2019 ).

A motifbreakR + tfboot analysis starts with a VCF read in with tfboot’s read_vcf() function, which is a wrapper around motifbreakR functions for reading VCF files and returns a GRanges object. The get_upstream_snps() internally uses plyranges ( Lee et al ., 2019 ) to take in a list of SNPs as a GRanges object together with a TxDb object ( Carlson et al ., 2016 ), and returns a GRanges object containing SNPs in the upstream promoter region of genes in the TxDb object.

A standard motifbreakR analysis is then performed on the SNPs in the upstream region of these k genes of interest, followed by a motifbreakR analysis on the universe of all annotated genes. This step is time-consuming, but precomputing the motifbreakR results on all genes allows for extremely fast bootstrap resampling of b bootstrap resamples of k genes from this background set. Because all downstream analysis uses standard tidyverse tibbles instead of Bioconductor GRanges objects, tfboot package provides convenience functions to create compact tibbles from the motifbreakR results to reduce disk space and facilitate downstream analysis.


## 2.2 Statistical analysis with bootstrapping

The tfboot package provides downstream functions for summarization, bootstrapping, and statistical analysis of TFBS disruption in gene sets of interest. The tfboot function mb_summarize will summarize the results from a motifbreakR analysis into a single-row table with the following columns:

ngenes : The number of genes in the SNP set.

nsnps : The total number of SNPs disrupting TFBS.

nstrong : The number of SNPs with a “strong” effect.

alleleDiffAbsMean The mean of the absolute values of the alleleDiff scores.

alleleDiffAbsSum The sum of the absolute values of the alleleDiff scores.

alleleEffectSizeAbsMean The mean of the absolute values of the alleleEffectSize scores.

alleleEffectSizeAbsSum The sum of the absolute values of the alleleEffectSize scores.

The mb_bootstrap() function takes in precalculated motifbreakR results from the universe of all background genes and the number k of genes in a gene set to sample, and resamples k genes from the precomputed motifbreakR analysis b times to create an empirical null distribution of the values calculated above. Finally, the mb_bootstats() function takes as input both the summary on the gene set of interest with the bootstrapping results on the background set of genes and calculates p-values comparing the critical value from the user’s gene set of interest against the empirical null. The plot_bootstats() function takes the results from this analysis as input to create a visual representation of the critical values against the background null distribution.


## 3 Results

Here we demonstrate a motifbreakR and tfboot analysis on SNPs in Asian elephant ( Elephas maximus ) compared to an African savanna elephant reference genome ( Loxodonta africana ). As Elephas maximus morphologically differs from Loxodonta africana in ear size and shape, we selected the set of nine genes annotated for outer ear morphogenesis (GO:0042473), as shown in Table 1 .

Briefly, we used minimap2 to map PacBio HiFi reads sequenced in the Asian elephant using the African elephant chromosome-level reference genome ( Rhie et al ., 2021 ) we released earlier this year (NCBI genome accession GCA_030014295.1), and used GATK HaplotypeCaller to call variants run on the Form Bio platform ( https://formbio.com/ ). Asian elephant sequencing data is available on the GenomeArk ( https://registry.opendata.aws/genomeark/ ).

After precalculating the motifbreakR results for upstream promoter regions in all genes in this background set, the tfboot analysis 1,000 bootstrap resamples took approximately 20 seconds on a single CPU on an Apple M2 Macbook Pro. The primary results from the tfboot analysis are shown in Table 2 .

While there may be individual SNPs that disrupt TFBS in promoters of individual genes, the results in Table 2 indicate that there is no statistically significant TFBS disruption in SNPs in the promoter regions of this set of genes of interest compared to a null background set of genes of the same size. After calculating bootstrap statistics, the plot_bootstats() function can be used to visually display the critical values for motifbreakR TFBS metrics of the gene set of interest against the empirical null distribution (gray), as shown in Figure 1 .


## 4 Conclusion

Here we introduce the tfboot package for statistical analysis of TFBS-disrupting SNPs in gene sets using motifbreakR. We demonstrate an analysis on SNPs between the Asian and African elephant in a set of nine developmentally important genes involved in outer ear morphogenesis, showing that bootstrap resampling and statistical analysis on precomputed motifbreakR results requires <1 minute of compute time. The tfboot package can be run on any genome with available Bioconductor BSGenome and TxDb objects, either publicly available or custom-created from FASTA+GTF files. The tfboot package works with GRanges and other Bioconductor data structures for integration into existing workflows, and results are returned as tibbles with bootstrapping results as nested list columns, facilitating downstream analysis with tidyverse tools. The tfboot package is implemented as an R package and is freely available under the MIT license at https://github.com/colossal-compsci/tfboot .


## Funding

This work received no external funding.


## Acknowledgements

The authors thank Vijay Kandali and Amanda Kowalczyk for testing and feedback on tfboot package. The authors also thank Brandi Cantarel and Ketaki Bhide for assistance with alignment and variant calling Asian elephant reads against the African elephant reference genome.


## Footnotes

https://github.com/colossal-compsci/tfboot

https://colossal-compsci.github.io/tfboot/