# Statistical relationships across epigenomes using large-scale hierarchical clustering


## Motivation
  Recent advances in genomics and sequencing platforms have revolutionized our ability to create immense data sets, particularly for studying epigenetic regulation of gene expression. However, the avalanche of epigenomic data is difficult to parse for biological interpretation given nonlinear complex patterns and relationships. This attractive challenge in epigenomic data lends itself to machine learning for discerning infectivity and susceptibility. In this study, we explore over 3000 epigenomes of uninfected individuals and provide a framework to characterize the relationships among epigenetic modifiers, their modifiers, genetic loci, and specific immune cell types across all chromosomes using hierarchical clustering.


## Results
  Hierarchical clustering of epigenomic data revealed consistent epigenetic patterns across chromosomes, demonstrating that variation due to epigenetic modifiers is greater than variation between cell types. Gene Ontology and KEGG pathway analyses indicated significant enrichment of genes involved in chromatin remodeling, mRNA splicing, immune responses, and the regulation of microRNAs and snoRNAs. Epigenetic modifiers frequently formed biologically relevant clusters, including the cohesin complex, RNA Polymerase II transcription factors, and PRC2 complex members. These clustering behaviors remained consistent across all chromosomes, supported by entropy analysis and high Adjusted Rand Index scores, indicating robust cross-chromosomal similarity. Co-occurrence analysis further revealed specific sets of modifiers that consistently appeared together within clusters, reflecting shared biological functions and interactions. Validation using another dataset confirmed the reproducibility of these clustering patterns and modifier co-occurrence relationships, underscoring the reliability and generalizability of the methodology.


## Availability and implementation
  The analysis pipeline for this study is freely available online at the GitHub repository: https://github.com/lanl/epigen.