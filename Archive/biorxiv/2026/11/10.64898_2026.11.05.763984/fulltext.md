## Joint protein-DNA language modeling enables prediction and engineering of DNA recognition specificity


## Abstract

Protein-DNA recognition specificity underlies transcriptional regulation, DNA replication, chromatin remodeling and genome editing. Protein-DNA recognition depends on both interacting sequences, yet language models that learn this cross-molecular dependence explicitly during pretraining remain limited. Here, we developed the Protein-DNA Language Models (PDLMs), interaction-aware language models that jointly represent protein and DNA sequences. PDLMs were built by continued pretraining from ESM2 with masked language modeling on paired protein-DNA sequences. A shared encoder places amino acids and nucleotides in the same molecular context, enabling conditional sequence scoring and transferable pair representations. We further introduced a domain-aware masking strategy that increased masking probability within DNA-binding domains to strengthen learning of interaction-relevant regions. Across downstream tasks, PDLMs improved protein-DNA pair classification relative to independent-encoder baselines and supported prediction of mutation-associated binding changes. Zero-shot scoring recovered known changes in DNA-recognition specificity and prioritized variants with higher editing activity. Learned representations also supported cross-study prediction of base editor activity. After fine-tuning on transcription factor binding data, PDLMs predicted DNA motifs directly from protein sequences. Together, PDLMs provide a framework for interaction-aware biomolecular language modeling, with potential applications in protein engineering and genome editing.


## Competing Interest Statement

W.W. is the founder and scientific advisor of EdiGene and Therorna. The authors declare that they have no other competing interests.


## Funder Information Declared

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area