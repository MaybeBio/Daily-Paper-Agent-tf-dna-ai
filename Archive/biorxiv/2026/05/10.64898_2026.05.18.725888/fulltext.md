## ABSTRACT

Transcription factors (TFs) regulate gene expression by binding to specific DNA sequences. Widely used models of TF–DNA binding, such as position weight matrices (PWMs) and position-specific affinity matrices (PSAMs), assume binding free energy is the sum of independent base contributions. However, there is ample evidence that non-additive effects significantly influence TF binding. Here, we utilize data from a high-throughput in vitro assay ( ivt FOODIE) to generate genome-scale TF–DNA dissociation constants ( K d ) and systematically evaluate sequence-to-affinity models of increasing complexity. We demonstrate that pairwise additive models exhibit systematic deviations from the measured affinity landscapes. Models incorporating adjacent dinucleotide interactions and deep learning architectures achieve markedly improved agreement with experimental K d values. The magnitude of this non-pairwise-additivity depends strongly on the TF family. In silico mutation screening reveals widespread, TF-specific long-range interposition dependencies, highlighting the role of energetic coupling across distant positions in target recognition. These results provide a quantitative framework for comparing non-pairwise-additive energetic effects across diverse TFs.


## INTRODUCTION

Transcription factors (TFs) regulate gene expression by recognizing specific DNA sequences with varying strengths of affinity, typically quantified by the dissociation constant, K d . 1 A common assumption in modeling TF–DNA recognition is pairwise additivity, which posits that the total binding free energy is the sum of independent energetic contributions from individual bases at each position. 2 This principle underlies widely used frameworks, including position weight matrices (PWMs) 3 and position-specific affinity matrices (PSAMs) 4 . These pairwise additive models remain the standard for representing TF specificity due to their interpretability and computational efficiency. 5 , 6 , 7

However, the pairwise additive approximation often fails to capture the intricate physical determinants of TF–DNA binding. Evidence suggests that interdependent effects between nucleotides, where the contribution of one base depends on its neighbors, can significantly modulate affinity. 8 , 9 While some studies argue that pairwise additive models provide a reasonable approximation of specificity 10 , the extent to which this assumption holds across diverse TF families and expansive sequence spaces remains a subject of debate. The fundamental challenge lies in determining whether these non-pairwise-additive effects are marginal corrections or essential components of the binding energy landscape.

To move beyond the pairwise additive baseline, various modeling strategies have been developed, ranging from adjacent dinucleotide models 10 to complex deep learning architectures. In particular, convolutional neural networks (CNNs) 11 , 12 offer a powerful, non-parametric framework for capturing high-order sequence dependencies without prior assumptions of positional independence. By learning local sequence features, CNNs can capture the non-linear sequence determinants of binding, providing a complete representation of the sequence–affinity landscape. 13 , 14 , 15

The rigorous evaluation of these models has long been constrained by the nature of available high-throughput data. While technologies such as PBM 16 , HT-SELEX 17 , and ChIP-seq 18 have yielded vast catalogs of TF binding preferences, they primarily measure relative enrichment or occupancy rather than absolute thermodynamic parameters. This distinction is crucial: without absolute thermodynamic data, it is impossible to strictly quantify the energetic coupling between nucleotides at a physical level. While methods like MITOMI 19 and HiTS-FLIP 20 enable high-throughput K d measurements, their dependence on specialized instrumentation restricts their applicability and has impeded large-scale mapping of affinity landscapes across TF families.

To bridge this gap, we leverage our recently developed high-throughput assay, ivt FOODIE 21 , which provides precise K d measurements for 45 TFs across genome-wide DNA libraries. By integrating these absolute thermodynamic data with sequence-to-affinity models of increasing complexity, we systematically map the energetic limits of the pairwise-additive assumption. This framework allows us to evaluate model performance and to quantify the physical magnitude of non-additivity across different TF families. The results provide a direct, genome-scale assessment of the biophysical principles governing TF–DNA recognition, revealing the widespread prevalence of interposition dependencies.


## METHODS


## ivt FOODIE Assay and K d Estimation

TF–DNA dissociation constants were measured using the high-throughput ivt FOODIE assay. Briefly, purified TFs were incubated with a genomic DNA library (derived from ATAC-seq 22 ) until equilibrium. The double-stranded cytosine deaminase MGYPDa829 was then introduced to catalyze cytosine-to-uracil (C-to-U) conversion at solvent-exposed sites. Because TF binding sterically protects DNA from deamination, the C-to-U conversion frequency at each binding site inversely correlates with TF occupancy. By measuring these frequencies across a gradient of TF concentrations via high-throughput sequencing, we determined the binding fraction at each concentration. K d values were subsequently estimated by fitting these data to the Hill equation (Hill coefficient n = 1). 23

To align model outputs with physical energetics, measured K d values were converted to binding affinities defined as –log 10 K d . Given the thermodynamic identity Δ G °= RT ln( K d ), this scale ensures that the target metric is linearly proportional to the standard Gibbs free energy of binding. All K d values were standardized to molar units prior to conversion.


## Sequence Representation, Model Training, and Evaluation

To systematically evaluate non-additivity in TF– DNA recognition, we implemented four sequence-to-affinity models with increasing representational capacity:

PWM: A motif-based baseline generated with STREME 24 using DNA sequences from de novo TF footprints identified in the ivt FOODIE data, representing statistically enriched base patterns.

PSAM: A linear regression model that assumes independent energetic contributions from individual bases, serving as the pairwise-additive limit.

Adjacent Dinucleotide Model: An extension of PSAM incorporating nearest-neighbor coupling terms to capture local non-additivity.

CNN: A non-linear architecture comprising two 1D convolutional layers (each followed by batch normalization and ReLU activation) and two fully connected layers.

All models, except PWM, were trained on one-hot encoded DNA sequences to predict –log 10 K d . Predictive accuracy was assessed using the Pearson correlation coefficient ( r ) between experimental and predicted affinities on held-out DNA sequences.


## In Silico Mutations Analysis

To quantify energetic coupling between positions i and j , we defined the interposition dependency score, , using an in-silico double-mutant approach: where F denotes the CNN-predicted affinity (– log 10 K d ), WT is the consensus binding sequence, and B ∈ { A, C, G, T } is the substituted base.

To ensure the robustness of ε across various sequence contexts, for each TF, we embedded the mutated core motifs into 256 distinct flanking sequences that exhibited the highest experimental affinities. For each position pair ( i, j ), we calculated the signed mean ε across all flanking contexts and possible base substitutions. A non-zero ε indicates a deviation from the pairwise additive assumption, reflecting energetic epistasis.


## RESULTS


## Non-Pairwise-Additive Models Improve TF–DNA Affinity Prediction

To systematically evaluate the pairwise additive approximation in TF–DNA recognition, we benchmarked four sequence-to-affinity models of increasing architectural complexity against genome-scale K d measurements from the ivt FOODIE assay (Methods). Our dataset encompasses absolute binding affinities for 45 diverse TFs. As conceptually outlined in Figure 1 , the PWM and PSAM served as our pairwise additive baselines. To capture non-pairwise-additive sequence dependencies, we extended the PSAM framework to include adjacent dinucleotide interactions. Concurrently, we deployed a CNN to map higher-order, non-linear relationships. All predictive performances were rigorously evaluated on held-out test sequences to ensure robust generalization (Methods).

We first examined representative TFs (SP1, YY1, and CTCF) to visualize the impact of model complexity on predictive accuracy ( Figure 2 ). The traditional PWM exhibited the weakest correspondence with experimental affinities, characterized by broad scatter and low correlation coefficients. By directly regressing on –log 10 K d , the PSAM model substantially tightened the prediction scatter, capturing a greater portion of the affinity landscape. For each representative TF, incorporating adjacent dinucleotide interactions further enhanced accuracy, while the non-linear CNN visually achieved the strongest agreement with experiment.

This qualitative observation is supported by global statistics across the full 45 TF dataset s ( Figure 3 ). The pairwise additive baselines, PWM and PSAM, achieved median Pearson’s r of 0.513 and 0.641, respectively. Relaxing the pairwise additive constraint significantly improved predictive power, with the adjacent dinucleotide model increasing the median r to 0.701. The CNN achieved the highest global performance with a median r of 0.751. Thus, while pairwise additive contributions establish the core binding motif, incorporating nearest-neighbor and high-order sequence dependencies provides a more faithful mathematical representation of the TF–DNA energetic landscape.


## The Extent of Non-Pairwise-Additivity Varies across TF Families

TFs recognize DNA sequences through diverse DNA-binding domain (DBD) architectures. We hypothesized that the magnitude of non-pairwise-additivity is TF-family-dependent. To quantify this, we used the performance gap (Δ r ) between the CNN and PSAM models as a macroscopic metric for non-pairwise-additive energetic effects ( Figure 4 ). We observed striking family-specific divergence. For instance, HOX family homeodomains (e.g., HOXA1, HOXA6, HOXB5) exhibited only marginal non-pairwise-additivity, tightly adhering to the pairwise additive approximation. In contrast, AP-2 family members (TFAP2B, TFAP2C) displayed large predictive gains (Δ r ≈ 0.3) with the CNN, indicating profound non-pairwise-additive coupling. The C2H2 zinc finger family, the largest in our dataset, generally exhibited moderate non-pairwise-additivity (Δ r ≈ 0.1). Thus, the energetic binding constraints, expressed here as non-pairwise-additive interaction effects are intrinsically linked to the physical structure of the TF.


## Interdependency between Motif Positions Varies Substantially across TFs

To systematically map the spatial distribution of these non-pairwise-additive interactions, we used an in-silico double-mutant framework to compute the energetic epistasis ( ε ) between motif positions (Methods). Visualizing the signed pairwise dependency matrices revealed highly idiosyncratic architectural patterns ( Figure 5a ). The strongest long-range dependencies were predominantly observed in known obligate or facultative dimers (e.g., TFAP2C, NFKB1, JUND, and NRF1), directly reflecting energetic coupling between the two sub-monomer binding half-sites. The physical nature of this coupling varied dramatically: TFAP2C exhibited strong synergistic (positive) inter-monomer dependencies, whereas NFKB1 displayed pronounced antagonistic (negative) coupling. Conversely, TFs like SP1 and HEY1 lacked strong inter-site communication, with epistasis heavily concentrated at the core motif or strictly restricted to adjacent base pairs. Collectively, the matrices demonstrate that non-pairwise-additivity is a structurally-coupled, TF-specific thermodynamic signature.

Focusing strictly on these distal dependencies, we quantified the maximum absolute epistasis and aggregate contribution to the total non-pairwise-additivity of long-range dependencies (separation >= 4 bp, Figure 5b ). Strikingly, even for TFs lacking acute individual long-range interactions, distal coupling collectively accounted for up to 40% of the non-pairwise-additive energy landscape.

Broadly, as expected, the average dependency strength decayed rapidly with increasing distance between mutated positions, confirming that nearest-neighbor and short-range interactions generally dominate non-pairwise-additivity ( Figure 5c ). However, a distinct heavy-tail distribution emerged for distal pairs. While the mean long-range ε was modest (0–0.2), a critical subset of position pairs exhibited strong long-range epistasis with | ε | approaching 1.0. Given our – log 10 K d scale, an | ε | of 1.0 translates to an order-of-magnitude shift in binding affinity, underscoring that distal co-mutations can exert large functionally significant synergistic or antagonistic energetic effects.


## DISCUSSION AND CONCLUSION

By integrating genome-wide thermodynamic K d measurements with deep learning, we have systematically mapped the limits of the pairwise additive assumption in TF–DNA recognition. Our results provide definitive evidence that while pairwise additive frameworks (PWMs and PSAMs) capture essential binding motifs, they fundamentally fail to resolve a substantial portion of the affinity landscape. The superior performance of non-linear models, particularly CNNs, quantifies the energetic magnitude of these missing interactions, establishing non-pairwise-additivity as a defining feature of the TF–DNA binding energy landscape rather than a marginal correction.

Importantly, the extent of these non-pairwise-additive effects is intrinsically tied to the architectural logic of TF DBDs. Our data reveal a distinct functional spectrum: homodimer families like AP-2 (TFAP2C) and Rel (NFKB1) exhibit profound non-additivity, reflecting highly cooperative coupling between subunits, whereas HOX homeodomains adhere closely to the pairwise additive limit ( Figure 4 ). As a striking manifestation of this complex energetic landscape, the widespread prevalence of long-range interposition dependencies observed in our in-silico screens provides a direct thermodynamic signature of distal energetic coupling ( Figure 5 ). Such family-specific divergence implies that evolution has fine-tuned the exploitation of these energetic dependencies, allowing different TFs to achieve varying levels of regulatory precision through the selective use of non-pairwise-additive energetics.

Our framework directly relies on absolute thermodynamic K d , meaning the predicted epistasis represents true physical interaction energies rather than statistical correlations. This strict energetic mapping is what uniquely enables the resolution of subtle allosteric communications that typically evade traditional occupancy-based assays.

Several challenges remain. While our dataset spans 45 TFs, expanding to the entire human repertoire is essential for a comprehensive accounting of non-pairwise-additive DNA recognition. Bridging the gap between an in vitro biophysical baseline and the complexities of chromatin in vivo , including nucleosome positioning and co-factor competition, is a critical next step.

In summary, we established a rigorous quantitative deep learning framework that circumvented non-pairwise-additivity. This study provides quantitative models necessary to describe thermodynamics of TF-DNA interactions in genomic regulatory regions.


## Data Availability

Code for the models is available on GitHub ( https://github.com/shenxiaoke/ivtFOODIE-CNN_dinucle_PSAM-train ).


## ACKNOWLEDGMENTS

This project was financially supported by Changping Laboratory (Grants No. 2021C0402) and the Ministry of Science and Technology of China.

We thank Prof. Mingchen Chen (Changping Laboratory, Beijing, P. R. China.) and Prof. Jian Yan (Department of Biomedical Sciences, College of Biomedicine, City University of Hong Kong, Hong Kong SAR, China.) for helpful discussions.


## Funder Information Declared