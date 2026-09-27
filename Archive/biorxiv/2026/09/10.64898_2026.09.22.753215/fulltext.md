## A Taxonomy-Informed Sparse DNA Foundation Model for Microbial Genomics


## Abstract

Microorganisms are indispensable to terrestrial ecosystems, with their genomic material underpinning critical functions and applications across agriculture, biotechnology, and human health. Although genomic language models have advanced representation learning in DNA sequences, the extensive diversity of microorganisms and imbalanced taxonomic representation in the pretraining corpora pose challenges for effective microbial genomic sequence modeling. Here we present MicroGlot, a taxonomy-informed microbial DNA foundation model pretrained on 3.70 million sequences comprising 378.3 billion nucleotides across 99{,}700 species. MicroGlot encodes the hierarchical relations among taxa through hyperbolic embeddings, incorporating microbial taxonomic knowledge into a sparse mixture-of-experts architecture. Zero-shot evaluation of MicroGlot's layer embeddings demonstrates that the model's representations encode phenotypic traits and taxonomic identity. Comparison with a taxonomy-ablated variant trained under the same pretraining scheme shows that incorporating taxonomic knowledge consistently improves representation quality across the layers of MicroGlot. MicroGlot also combines optimized training techniques with efficient architectural components from modern large language models, achieving leading zero-shot performance across layers and competitive fine-tuning performance with low computational overhead. In a 1000-species set sampled from major cellular domains and viral realms, MicroGlot's routing fingerprints show greater agreement with taxonomic groups than tetranucleotide composition, reflecting taxonomically structured expert routing in multilingual modeling of microbial genomes. Overall, we show that MicroGlot serves as an efficient and effective DNA foundation model for microbial genomic analysis.


## Competing Interest Statement

The authors have declared no competing interest.

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area