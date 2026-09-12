## Predicting Capsid Protein Binding Sites in Single-Stranded RNA Viruses Using Machine Learning from Local Geometric Features


## Abstract

Selective recognition of viral RNA by capsid proteins is essential for genome packaging during the assembly of single-stranded RNA (ssRNA) viruses. However, identification of capsid protein binding sites in the RNA genome remains challenging because current experimental techniques are labor-intensive and low-throughput, motivating the development of computational approaches. Here, we present a sequence-based framework that integrates RNA tertiary structural modeling, local geometric feature extraction, and machine learning to predict capsid protein binding sites. Using the Qbeta; bacteriophage as a proof-of-concept system, we constructed a benchmark dataset of experimentally identified binding and non-binding RNA fragments. We designed a set of geometric descriptors to characterize the local structural features of the RNA backbone. When repeatedly trained and tested with these geometric descriptors on different subsets of the benchmark dataset, the neural network showed a strong ability to distinguish capsid protein binding sites from non-binding RNA fragments, achieving an area under the receiver operating characteristic curve (AUC) of 0.88 in a 5-fold cross-validation. To evaluate whether the model can predict RNA binding sites without experimental structures, we applied it to local geometric features derived from AlphaFold-predicted RNA structures. Despite substantial structural differences between predicted and experimentally determined models, the classifier retained considerable predictive performance (AUC = 0.75), indicating that approximate RNA tertiary structures may still preserve biologically meaningful information for capsid binding site prediction. Furthermore, the failed predictions suggest that viral genome packaging is not only governed by intrinsic RNA structural features, but also by additional dynamic factors beyond static RNA conformations. In summary, our findings provide new mechanistic insights into RNA-capsid interactions and establish a foundation for extending this approach to diverse ssRNA viruses.


## Competing Interest Statement

Junjie Zhang is the co-founder of Phanetica LLC.


## Footnotes

https://github.com/melody144/CPBSpred


## Funder Information Declared

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area