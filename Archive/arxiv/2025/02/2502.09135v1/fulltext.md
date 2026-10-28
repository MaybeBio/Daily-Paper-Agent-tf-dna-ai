## Interpreting and Steering Protein Language Models through Sparse Autoencoders

The rapid advancements in transformer-based language models have revolutionized natural language processing, yet understanding the internal mechanisms of these models remains a significant challenge. This paper explores the application of sparse autoencoders (SAE) to interpret the internal representations of protein language models, specifically focusing on the ESM-2 8M parameter model. By performing a statistical analysis on each latent component’s relevance to distinct protein annotations, we identify potential interpretations linked to various protein characteristics, including transmembrane regions, binding sites, and specialized motifs. We then leverage these insights to guide sequence generation, shortlisting the relevant latent components that can steer the model towards desired targets such as zinc finger domains. This work contributes to the emerging field of mechanistic interpretability in biological sequence models, offering new perspectives on model steering for sequence design.


## 1 Introduction

Since the introduction of the transformer architecture ( Vaswani 2017 ) , the capabilities of neural networks to model and generate natural language have increased dramatically. Yet, due to their black-box nature, we still lack a clear understanding of how these models achieve such capabilities ( Rai et al. 2024 ) . Recently, the mechanistic interpretability approach has been proposed, where researchers try to reverse engineer neural networks in a way similar to reverse engineering computer programs ( Olah 2022 ; Rai et al. 2024 ) . This involves understanding which features the network is learning from our input data, and then how it performs operations with this set of features.

It has been observed that neural networks tend to encode high-level features as linear directions in their representation space—such as the gender direction in word embeddings ( Park et al. 2023 ) . Additionally, these models can store more facts and features than their parameter counts would suggest, a phenomenon known as superposition ( Elhage et al. 2022 ) . This phenomenon represents a core problem for interpretability: as a single neuron activation can be polysemantic and represent multiple features simultaneously.

Recently, sparse autoencoders (SAEs) have been proposed as a method to disentangle internal representations in language models, extracting features from superposition in an unsupervised manner ( Templeton et al. 2024 ; Bricken et al. 2023 ; Cunningham et al. 2023 ) . Notably, these features appear to be actionable: artificially activating them during inference can steer a model’s output ( Templeton et al. 2024 ; Makelov 2024 ) . Such methods have been successfully applied to language ( Templeton et al. 2024 ; Cunningham et al. 2023 ; Gao et al. 2024 ) , as well as vision and multimodal models ( Gorton 2024 ; Surkov et al. 2024 ) , but biological and protein sequence models remain relatively unexplored ( Simon & Zou 2024 ; Adams et al. 2025 ) .

Protein language models have been shown to encode structural, functional, and evolutionary information in their internal representations ( Rives et al. 2019 ; Lin et al. 2023 ; Hayes et al. 2024 ) . Interpretability methods for these models could reveal biological mechanisms, and support model debugging and editing for safety considerations. Additionally, model steering can be incorporated into sequence design pipelines.

The main contributions of this paper are:

•A trained sparse autoencoder (SAE) for the ESM-2 8M parameter model, along with potential interpretations of its latent components (sections 2.2 , 3.1 and 3.3 ).

•A methodology for generating protein sequences by intervening on specific latents, demonstrating successful steering towards non-trivial features, such as zinc finger domains (section 3.4 ).

•A heuristic for selecting the model layer from which to extract representations using an intrinsic dimension estimator (section 3.2 ).


## 2 Background


## 2.1 Protein Language Models

Many advancements in Natural Language Processing have been successfully applied to biological sequence modeling. Transformer-based neural networks can be trained on protein sequences using the Masked Language Modeling (MLM) task, where each amino acid is treated as a token that can be randomly masked. The model learns to predict the masked tokens by minimizing the following loss function ( Rives et al. 2019 ) :

where x x is a protein sequence, M M is a set of masked indices and p ⁡ ( x i | x / M ) p(x_{i}|x_{/M}) is the probability assigned to the ground truth amino acid x i x_{i} given its sequence context.

Training on the Masked Language Modeling (MLM) task forces the network to learn dependencies between masked amino acids and their sequence context while simultaneously capturing various biological features present in the data. Embeddings extracted from these models have been shown to encode information about secondary structure, tertiary contacts (residue-residue interactions), function, remote evolutionary relationships, and factors relevant to predicting mutational effects ( Rives et al. 2019 ; Elnaggar et al. 2021 ; Meier et al. 2021 ; Lin et al. 2023 ; Hayes et al. 2024 ) . On the other hand, the attention mechanism appears to prioritize binding sites, with attention maps capturing information about residue-residue interactions. ( Vig et al. 2020 ) .


## 2.2 Sparse Autoencoders

The sparse autoencoders used for interpretability are simple, single-layer models trained on the activations of a larger language model. To disentangle network features, the hidden layer is made significantly larger than the original embeddings, creating an overcomplete basis. A sparsity constraint is then applied to ensure that only a few latent neurons are active at a time, making the SAE’s hidden representation far more interpretable than standard language model components ( Templeton et al. 2024 ; Bricken et al. 2023 ; Cunningham et al. 2023 ) .

The autoencoder is composed of an encoding and a decoding function, given by:

Here f e ​ n ​ c f_{enc} is the encoder, that takes an embedded amino acid token x ∈ I ​ R d x\in{\rm I\!R}^{d} from a given layer in the model and returns a latent z ∈ I ​ R ≥ 0 n z\in{\rm I\!R}_{\geq 0}^{n} with a hidden dimension n n that is m m times bigger that of the original vector (expansion factor). The decoder f d ​ e ​ c f_{dec} approximately reconstructs x x given z z , through the decoding matrix W d ​ e ​ c ∈ I ​ R n × d W_{dec}\in{\rm I\!R}^{n\times d} and the bias weight b d ​ e ​ c ∈ I ​ R d b_{dec}\in{\rm I\!R}^{d} .

The loss function used for the training is a combination of the reconstruction error of the autoencoder ℒ M ​ S ​ E \mathcal{L}_{MSE} plus a sparsity constraint ℒ L 1 \mathcal{L}_{L_{1}} :

While training, we renormalize the W d ​ e ​ c W_{dec} matrix to have unit norm after each backward pass. This is necessary to prevent that autoencoder latents become arbitrarily small and satisfy the L 1 L_{1} constraint without actually being sparse.


## 3 Methods


## 3.1 Training Details

We use the ESM-2 family of models ( Lin et al. 2023 ) as our base, extracting activations from the final output of the transformer block. We train on approximately 15k non-redundant protein sequences from SCOPe 2.08 ( Fox et al. 2014 ) . Further details on the architecture, training procedures, and hyperparameter selection can be found in section A.1 of the appendix.


## 3.2 Layer Selection

We adopt a principled strategy to select the layer from which we extract representations for the sparse autoencoder. The initial intuition, in line with earlier studies ( Templeton et al. 2024 ; Gao et al. 2024 ) , is to choose a mid-to-late layer, where the model is assumed to have developed abstract features but is not yet focused on the output reconstruction task. However, unlike these prior works, we move beyond mere intuition by incorporating a quantitative measure based on intrinsic dimension.

Specifically, we compute the intrinsic dimension of each layer’s representations using the estimator proposed by ( Facco et al. 2017 ) , and then identify where this value plateaus. Previous research has shown that layers corresponding to local minima or plateaus in intrinsic dimension are where abstract information is most clearly encoded ( Valeriani et al. 2024 ) . Selecting a layer within this plateau increases the likelihood of capturing meaningful representations, providing a stronger foundation for interpretability and model steering.


## 3.3 Interpreting Autoencoder Latents

We extract protein annotations from the UniProt database ( Uniprot 2025 ) and convert them into binary labels for each amino acid in the sequence. We then compute the precision π \pi and recall ρ \rho of each latent component k k in detecting a given feature ϕ \phi .

Let A A be the set of all amino acids and A ϕ + A_{\phi^{+}} the set of amino acids that have been annotated with the feature ϕ \phi . Considering a latent k k to be active ( k + k^{+} ) for a given amino acid when its value z k z_{k} exceeds a certain threshold τ z \tau_{z} , we have:

This gives us a value of precision and recall for each pair of k k , ϕ \phi . We consider a latent component to be associated with a specific feature if its precision or recall exceed a predefined threshold that we set to 0.80 0.80 .


## 3.4 Generating steered sequences

Once a latent corresponding to a specific feature is identified, we can steer the model during inference to increase the likelihood of generating protein sequences that contain that feature. This approach, previously demonstrated in natural language models by ( Templeton et al. 2024 ) , is outlined in figure 1 .

We begin with a randomly generated amino acid sequence of fixed length. After a forward pass through the model and the encoder layer of the SAE, we modify the target latent z k z_{k} by scaling and shifting its value to increase its magnitude (equation 7 ). We then pass the modified value z k ∗ z_{k}^{*} through the decoder layer f d ​ e ​ c f_{dec} and add back the original reconstruction error of the embedding x x before passing it through the rest of the model (equation 8 ).

For each position in the sequence, we randomly sample an amino acid according to the probability distribution predicted by the model under the intervention. We repeat this process starting from the predicted sequence and perform 100 iterations of inference-prediction to refine the sequence. We select the sequence at the iteration where the value of the activation z k z_{k} is maximum.


## 4 Results


## 4.1 Interpreting Latents

For the interpretability analysis, we focus on the autoencoder that provides the best trade-off between sparsity and reconstruction quality, as described in section A.3.2 of the appendix. We compute recall and precision for all [ k k , ϕ \phi ] pairs, following the methodology outlined in section 3.3 , using three increasing thresholds of latent activation. This allows us to assess the robustness of the identified features.

We find 395 putative [ k k , ϕ \phi ] associations, detailed in table 1 . Among these, there are latent components associated to different binding sites, cellular regions and motifs like zinc fingers. The complete set of latent - feature associations is available in the supplementary data (see section 5 ).

We also identify many potential associations with a lower confidence (lower values of precision or recall). To get an idea of how many putative association are found for each value of precision/recall (as well as a combined F1-score) we plot their cumulative distributions in figure 2 .

Intuitively, a latent component that perfectly matches an annotation type should exhibit both high precision and recall, resulting in a high F1-score. However, since the model is trained to optimize a masked language modeling loss, the features it learns may not directly align with those in the manually curated dataset. For instance, a latent k k might encode a more specific subcategory of a dataset label ϕ \phi , such as identifying the starting amino acid of a helix rather than the entire helix structure (as seen by Adams et al. 2025 on some features). In such cases, the association between k k and ϕ \phi would likely have high precision but low recall.

Similarly, a high recall but low precision may indicate that the model has learned a more coarse-grained feature than those defined in the dataset. This is evident in cases such as latent k = 610 k=610 , which activates across various types of zinc fingers, and latent k = 555 k=555 , which responds to alpha-keto acids. To prevent selecting latents with high recall due to trivial reasons – such as activating indiscriminately on all amino acids – we also assess the proportion of times a latent is active on amino acids lacking a given label, denoted as P ⁡ ( k + | ϕ − ) P(k^{+}|\phi^{-}) , before confirming an association. In section A.3.3 , we present examples of the distributions of P ⁡ ( k + | ϕ + ) P(k^{+}|\phi^{+}) and P ⁡ ( k + | ϕ − ) P(k^{+}|\phi^{-}) for a zinc finger region.


## 4.2 Sequence Generation

We test the sequence generation procedure with shortlisted latents with a clear association to the zinc finger region annotations (high recall in this specific case). We probe different values of sequence length ( [ 22 , 27 , 30 , 35 , 40 , 60 ] [22,27,30,35,40,60] ), of the scaling a a ( [ 2 , 5 , 10 , 20 , 30 ] [2,5,10,20,30] ) and shift b b ( [ 0.1 , 1 , 10 , 50 , 100 , 200 ] [0.1,1,10,50,100,200] ), for a total of 180 combinations, obtaining one sequence for each.

Using an online tool for automatic annotation of zinc finger regions ( Sathyaseelan et al. 2023 ) , we look for known zinc finger motifs and Pfam family matches in our generated sequences. We find 24 matching regions (out of 180 sequences) when we simultaneously intervene on the two most prominent latents (highest recall) displaying a zinc finger association. In contrast, intervening on the most prominent latent produces only 3 matches, while generating sequences from the baseline model or intervening on a random latent or a random pair of latents produces no matches in any case. Among the matched sequences, the highest percent similarity was 48 % 48\% , with an average sequence similarity of 31 % 31\% , indicating a good level of diversity among the generated sequences.

While this sequence generation pipeline requires parameter fine-tuning to improve the success rate, the process can be automated by introducing appropriate heuristics to search the parameter space efficiently. To the best of our knowledge, this is the first application of steering with sparse autoencoder features to generate complex protein sequences, extending beyond trivial features like specific amino acids or simple amino acid repeats.


## 5 Discussion and conclusions

In this study, we demonstrate the potential of sparse autoencoders (SAEs) for interpreting and manipulating the internal representations of protein language models. By training a SAE on the ESM-2 8M parameter model, we identified and interpreted latent features associated with various protein annotations, including transmembrane regions, binding sites, and zinc finger motifs.

We have also demonstrated, for the first time, that these latent components can be leveraged to steer the model towards generating protein sequences with non-trivial structural features, like zinc finger motifs. The results highlight the utility of SAEs in disentangling the complex, polysemantic representations within protein language models, paving the way for more interpretable and controllable sequence generation. This approach not only deepens our understanding of how these models encode biological features but also opens up new possibilities for protein design and engineering. Future work could extend these methods to larger models and a wider range of protein features, further bridging the gap between interpretability and practical applications in computational biology.

The weights for the trained sparse autoencoder model are available from huggingface at: https://huggingface.co/evillegasgarcia/sae_esm2_6_l3 . The code is available from github at: https://github.com/edithvillegas/plm-sae . Supplementary data is available from zenodo at https://doi.org/10.5281/zenodo.14837817

We thank the technical support of the Laboratory of Data Engineering staff and acknowledge the AREA Science Park supercomputing platform ORFEO.

A.A. ws supported by the project “Supporto alla diagnosi di malattie rare tramite l’intelligenza artificiale”- CUP: F53C22001770002, and by the European Union – NextGenerationEU within the project PNRR ”PRP@CERIC” IR0000028 - Mission 4 Component 2 Investment 3.1 Action 3.1.1. E.N.V.G. was supported by the project PON “BIO Open Lab (BOL) - Raforzamento del capitale umano”—CUP: J72F20000940007.


## References


## Appendix A Appendix


## A.1 Sparse Autoencoder Training

We train our model using the Astral SCOPe 2.08 dataset, filtered to 40 % 40\% sequence identity, which includes approximately 15k highly non-redundant protein sequences ( Fox et al. 2014 ) . This dataset provides a manageable number of tokens, enabling faster iteration over different hyperparameters while maintaining a diverse range of protein sequences and structural domains. This diversity allows the autoencoder to learn a broad spectrum of features.

We check how frequently each of the latents activates over a subsample of tokens (50 batches of 4096 tokens) at regular intervals during training (every 500 batches). When this frequency is close to zero ( < 10 − 5 <10^{-5} ), we consider that the latent is “dead” and we re-initialize its weights to “revive” it.

To decide which hyperparameters (learning rate, sparsity penalty λ \lambda , SAE hidden size n n ) produce the best sparse autoencoder, we use the following metrics:

L 0 L_{0} : The average number of non-zero components in the latent vector z z for a given amino acid token. This is our measure of the sparsity level of the autoencoder.

Number of dead latents: The number of components in the latent space that are never non-zero over a large number of sample tokens ( ∼ 10 5 \sim 10^{5} ). This is a general metric for sparse autoencoders quality.

Cross Entropy (CE) Increase: Difference between the average cross entropy loss of the original model and the cross entropy loss of the model when we substitute the activations in a given layer by the corresponding activations reconstructed by the autoencoder. This indicates how much of the model’s performance the sparse autoencoder fails to reconstruct.

We perform a hyperparameter sweep with the following values: learning rate [ 5 ​ e − 4 5e^{-4} , 1 ​ e − 4 1e^{-4} , 1 ​ e − 3 1e^{-3} ]; L 1 L_{1} penalty [ 0.0003 , 0.001 , 0.005 0.0003,0.001,0.005 ] and dictionary size multiplier [ 32 , 10 , 5 32,10,5 ].

We use the evaluation metrics detailed in section A.1.3 to decide on the best combination of hyperparameters. Specifically, we aim to find a model that balances reconstruction error and sparsity by focusing on the “elbow” part of the CE increase against L 0 L_{0} plot, where increasing the density of active latents in the latent space does not significantly reduce the CE increase, indicating an optimal trade-off.


## A.2 Interpretability

As ground truth features for the interpretability analysis, we use the following protein annotations from Uniprot version 2024_1 :

Transmembrane region

Topological domain

Binding site

Zinc finger region

Region of interest

Intramembrane region

Active site

Disulfide bond

Glycosylation site

Helix

Turn

Strand


## A.3 Additional Results

We estimate the intrinsic dimension across all layers of ESM-2 8M following the methodology outlined by ( Valeriani et al. 2024 ) . The resulting curve, shown in Figure 4 , guides our decision to extract embeddings from layer 3. Larger models in the ESM-2 family exhibit a similar intrinsic dimension profile across different model sizes, with a more pronounced plateau region of comparatively low intrinsic dimension in the same relative layer position.

We evaluate all versions of the trained autoencoder primarily on two metrics: cross-entropy increase and sparsity (measured by L 0 L_{0} ). These two goals are in conflict with each other, so we select what we think is a good compromise at the bend of the Pareto frontier (figure 5 ). The selected autoencoder has an average L 0 L_{0} per amino acid of 18, and a cross-entropy increase of 0.10, with a hidden size that is 10 times larger than the original hidden size of the ESM-2 model. The number of dead latents in this SAE is 573. Decreasing the cross-entropy even more would entail a significant increase in activation density, which we want to avoid.