## Contrastive Learning Improves Generalization on M2OR Olfactory Binding Dataset


## Abstract

Olfaction-based biosensors stand to have profound impacts in fields such as medical diagnostics, national security, and drug discovery. A promising mode of vapor phase biodetection mimics volatile organic compound-olfactory receptor (VOC-OR) interactions with target-specific protein or peptide probes; however, lack of experimental coverage remains a core bottleneck. Current computational approaches aim to improve prediction of VOC-OR binding to reduce experimental burden, and current machine learning approaches fail to demonstrate a level of generalization that addresses current engineering challenges. Here, using the Molecular to Olfactory Dataset (M2OR) and Insect Olfactory Binding Protein Database (iOBPdb) datasets, data partitioning methods and their performance are evaluated on a neural network and contrastive learning framework on such VOC-OR binding datasets, varying: model training, architecture, and structure of the input data distribution. It was found that holding out certain chemical or proteomic motifs from the training data diminished model performance with a two layer neural network model. The model was able to generalize to state of the art performance (0.88 AUCROC) on every data split by applying a contrastive learning objective defined by shared molecular constituents and a stochastic sampler. This suggests the contrastive objective provides a strong inductive bias for neural networks to predict novel VOC-OR pairs. These findings highlight that model performance on pairwise biological interaction datasets can be inflated through identity leakage from constituent overlap, and emphasize the need for more robust evaluation protocols. Furthermore, we show contrastive regularization mitigates dataset degeneracy through enforcement of compatibility in the models latent geometry that may extend to other binder target-datasets where identity leakage confounds evaluation.


## Competing Interest Statement

The authors have declared no competing interest.

Supplementary Material

Thank you for your interest in spreading the word about bioRxiv.

NOTE: Your email address is requested solely to identify you as the sender of this article.


## Citation Manager Formats


## Subject Area