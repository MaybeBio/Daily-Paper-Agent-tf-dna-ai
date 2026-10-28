# DiffChIPL: a differential peak analysis method for high-throughput sequencing data with biological replicates based on limma


## Motivation
  ChIP-seq detects protein–DNA interactions within chromatin, such as that of chromatin structural components and transcription machinery. ChIP-seq profiles are often noisy and variable across replicates, posing a challenge to the development of effective algorithms to accurately detect differential peaks. Methods have recently been designed for this purpose but sometimes yield conflicting results that are inconsistent with the underlying biology. Most existing algorithms perform well on limited datasets. To improve differential analysis of ChIP-seq, we present a novel Differential analysis method for ChIP-seq based on Limma (DiffChIPL).


## Results
  DiffChIPL is adaptive to asymmetrical or symmetrical data and can accurately report global differences. We used simulated and real datasets for transcription factors (TFs) and histone modification marks to validate and benchmark our algorithm. DiffChIPL shows superior performance in sensitivity and false positive rate in different simulations and control datasets. DiffChIPL also performs well on real ChIP-seq, CUT&RUN, CUT&Tag and ATAC-seq datasets. DiffChIPL is an accurate and robust method, exhibiting better performance in differential analysis for a variety of applications including TF binding, histone modifications and chromatin accessibility.


## Availability and implementation
  https://github.com/yancychy/DiffChIPL.


## Supplementary information
  Supplementary data are available at Bioinformatics online.