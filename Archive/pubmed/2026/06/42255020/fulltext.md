# Searching for sequence features that control DNA cyclizability


## Abstract
  The mechanical properties of DNA molecules are crucial for many biological processes, from DNA packaging to transcription. While the mechanics of long DNA typically follow the worm-like chain polymer model, multiple studies have shown that the mechanics of short DNA, at the length scale of DNA–protein interactions, depend strongly on their sequence content. Motivated by recent high-throughput measurements of sequence-dependent DNA cyclizability—the DNA’s tendency to mechanically bend and form a loop—we developed a statistical-mechanics framework to systematically explore how cyclizability depends on the collective contributions of an increasing number of nucleotides in the sequence. By applying the method to datasets of randomly generated and biologically derived sequences, we identified a minimal pairwise model that describes the sequence-dependence of DNA cyclizability. The pairwise model enabled the extraction of characteristic sequence features that control DNA cyclizability and predicted the most and least cyclizable sequences, which we validated through all-atom molecular dynamics simulations. Our work advances current understanding of sequence-dependent DNA mechanics and its role in various biological processes, with implications for the growing field of DNA nanofabrication.


## Introduction
  The double-helical DNA is not just a passive repository of genetic information but also an active physical entity that interacts with diverse protein machinery to regulate essential biological processes, such as genome packaging, transcription, DNA replication, repair, and recombination. Increasingly, the mechanical properties of DNA are recognized to play critical roles in these processes (1, 2). For instance, DNA mechanics can influence where nucleosomes form (3, 4) and how DNA is packaged in cells (5, 6) or viruses (7), how DNA interacts with transcription factors (8, 9) and how probable it is to establish enhancer–promoter interactions via DNA looping (10, 11), as well as how DNA mismatches recruit repair machinery (12).

  The mechanical behavior of DNA is commonly described by the worm-like chain (WLC) polymer model (13, 14), which treats DNA as an elastic rod with a bending persistence length of ∼50 nm (∼150 base pairs). While the WLC model successfully captures the average DNA mechanics at long length scales, it predicts that DNA segments shorter than the persistence length are essentially rigid rods. However, such prediction is contradicted by observations of prevalent spontaneous large-angle bends in DNA at short length scales (tens of base pairs) (15, 16). More importantly, single-molecule assays over the years have shown that DNA segments can exhibit complex mechanical behaviors highly dependent on their nucleotide sequences (17–19). Epigenetic modifications (eg methylation) and DNA mismatches can further induce noncanonical DNA structures that significantly alter DNA mechanics, thereby modulating their functional outcomes (12, 20, 21).

  A key experimental approach to characterizing DNA mechanics is through the measurement of cyclizability, which quantifies a polymer’s ability to bend and form a loop. DNA cyclization has been investigated from a thermodynamic perspective as quantified by the Jacobson–Stockmayer (J) factor (22–24). Multiple studies have demonstrated that sequence content can significantly affect the J-factor of short DNA (18, 25, 26). However, a systematic characterization of how DNA cyclizability depends on sequence features has been lacking due to the limited number of probed sequences. Recently, a novel high-throughput sequencing-based method called loop-seq was developed (27) (Fig. 1), which enabled the simultaneous measurement of cyclizability across hundreds of thousands of sequences. This extensive dataset has inspired several deep neural network-based approaches to understand sequence-dependent DNA cyclizability and predict the DNA mechanics at the genome level (9, 28–31). Yet, while these machine-learning approaches achieve high predictive accuracy, they often operate as “black boxes,” providing limited physical insight into how DNA sequence encodes cyclizability.

  Here, we develop a statistical-mechanics framework to understand the sequence-dependence of DNA cyclizability using high-throughput loop-seq measurements. We first model cyclizability as a sum of collective contributions from an increasing number of nucleotides, from which we identify a minimal pairwise model that captures the observed sequence dependence. We then analyze the interaction matrix from the pairwise model to extract sequence features that encode cyclizability, and predict the most and least cyclizable sequences. Finally, we validate key model predictions using all-atom molecular dynamics simulations and discuss potential extensions to higher-order models.


## Results

### High-throughput data on DNA cyclizability
  Recent loop-seq experiments (27) have chosen hundreds of thousands of DNA sequences that span yeast genome and random sequences, and estimated the intrinsic cyclizabilities of these sequences by measuring the probability that they close on themselves into a loop, Fig. 1a. In brief, selected variable sequences of length N=50 were flanked by fixed double-stranded adapters (length 25) and single-stranded complementary overhangs (length 10), and immobilized on a bead. The looping reaction was initiated in high-salt buffer for 1 min, which reduces electrostatic repulsion along DNA to promote loop formation. Afterward, the unlooped molecules were digested by an exonuclease that attacks only free ends. The remaining population of looped molecules was sequenced and compared with the control ensemble in which the digestion step was omitted. Cyclizability was defined as the natural logarithm of the probability ratio for finding a sequence in the looped versus control ensemble. Observations on a small number of sequences showed that this measure correlates very well with direct single-molecule measurements of cyclizability quantified by fluorescence resonance energy transfer. Please refer to Ref. (27) for experimental details.

  The measured cyclizability depends periodically on the location of the bead attachment. The intrinsic cyclizability C0 was defined as the mean over this variation. The values of C0 were further refined using a mathematical operation to eliminate the bias introduced by the adapters and overhangs. After these adjustments, C0 becomes independent of tether location and sequence orientation. Please refer to Ref. (9) for data processing details. The loop-seq data contains multiple libraries of sequences. In this study, we utilize two of them: the Random library, which consists of 12,404 randomly generated sequences, and the Tiling library, which consists of 81,801 sequences that tile around 576 selected genes in the Saccharomyces cerevisiae genome. The distributions of C0 across the sequences in the two libraries are shown in Fig. 1b.


### A statistical mechanics approach to sequence-dependent cyclizability
  The intrinsic cyclizability of a sequence is a collective variable determined by contributions from all base sites. To model the cyclizability, we developed a statistical mechanics approach in which cyclizability is systematically expressed in terms of collective contributions from an increasing number of bases. To make it concrete, we first convert nucleotide sequences into Potts variables (also known as one-hot encoding). We represent DNA sequences as {Siα}, where Siα=1 if the base at site i is of type α, and Siα=0 otherwise. The index i=1,2,…,N, where N is the sequence length, and α=1,2,3,4, corresponding to A, T, C, G. In the matrix form, every column of {Siα} is a unit vector denoting the encoded nucleotide type. For example, {Siα} for sequence AGTCGTT⋯AA is

  We then express the cyclizability as a cluster expansion, accounting for one-base, two-base, three-base contributions, and so on, in a hierarchical order:

  where Wiα, Jijαβ, and Gijkαβγ are the coupling constants.

  To provide a rationale for Eq. (1), we note that cyclizability is a global quantity which, in principle, would require a complete expansion in sequence variables to yield an exact description. In practice, however, experience from other contexts, such as maximum-entropy-type models, suggests that low-order contributions often capture much of the relevant dependence for many observables (32–34). Motivated by this perspective, we treat Eq. (1) as a systematic hierarchy and examine its terms order by order in the following, with the goal of identifying a minimal model that captures the essential sequence features governing cyclizability.


### A linear model
  The simplest model for how the cyclizability depends on sequence is linear, where the cyclizability is a weighted sum of contributions from the individual nucleotides:

  Here, W is analogous to the position weight matrices that appear in models of transcription factor binding (35–37). Without loss of generality, we can set ∑αWiα=0 at every site i since ∑αSiα=1, see “Details of theoretical methods, (1)” section. If the linear terms are sufficient, then we can extract the elements of W by performing a least squares fit of the data with respect to Eq. (2), or, in the particular case when the sequences are random, by computing a correlation function:

  where the average is over all sequences, see “Details of theoretical methods, (3)” section for a derivation. Fig. 2 shows the estimate of W that results from computing this correlation for the Random library. The results are consistent with W=0, suggesting that there is no linear term in the dependence of C0 on the sequence. Indeed, when we estimate W from 90% of the data and predict C0 for the remaining 10% using Eq. (2), the correlation coefficient between predictions and measurements is essentially zero, r=0.05±0.03.


### A pairwise model
  If Eq. (2) does not work, because the data are consistent with W=0, the next simplest model is then a pairwise model, where the intrinsic cyclizability is a weighted sum of contributions from pairs of nucleotides:

  Again, without loss of generality, we can set ∑αJijαβ=∑βJijαβ=0 since ∑αSiα=1, see “Details of theoretical methods, (2)” section. As with the linear model, we can extract the elements of J by performing a least squares fit of the data with respect to Eq. (4), or, in the case of Random library, directly recover the underlying interaction parameters by computing correlation functions over random sequences:

  see “Details of theoretical methods, (4)” section for a derivation. For ease of presentation, we further combine the indices (i,α)→iα and (j,β)→jβ, so that Jijαβ→Jiα,jβ. Figure 3 shows the estimates of Jiα,jβ from computing the above correlation for the Random library. Compared to the J matrix of the shuffled data in Fig. S1, the J matrix in Fig. 3 shows clear signals near the diagonal line, highlighting the importance of nearest neighbor interactions. However, when we estimate J from 90% of the data and predict C0 for the remaining 10% using Eq. (4), the correlation coefficient between predictions and measurements is r=0.45±0.02, which is not high.


### Physical constraints on the J matrix
  At first glance, it seems that the pairwise terms are not sufficient to capture the sequence dependence of intrinsic cyclizability, as indicated by the low correlation between the predictions and measurements of the Random library. Therefore, it seems necessary to include higher-order terms in the model. However, a close inspection reveals that there are 9,800 independent elements in the J matrix, comparable to the total number of sequences (12,404) in the Random library. The limited number of sequences can lead to a low signal-to-noise ratio in the inferred J matrix, reducing its predictive power. To improve the performance of the pairwise model, we apply physical constraints to the J matrix to reduce the number of variables.

  First, Jijαβ is a coupling parameter between the bases at positions i and j, we expect it to depend on separation but not on absolute position, leading to translational invariance:

  Further, the double helical structure of DNA suggests that a sequence and its reverse complement should have the same cyclizability, leading to reverse-complement invariance:

  where α′ and β′ denote the complements of α and β (ie A↔T and C↔G), and translational invariance is used in deriving the last step. We note that by imposing translational and reverse-complement invariances, the number of independent elements in the J matrix is reduced from 9,800 to 294.

  We impose translational invariance by replacing each matrix element of J in Fig. 3 with the average of all elements at the same separation of j−i,

  We impose reverse-complement invariance by

  Figure 4a shows the J matrix for the Random library after imposing the symmetry conditions. A positive (negative) component Jijαβ indicates that the nucleotide pair (α,β) separated by a distance j−i promotes (suppresses) cyclization. For example, the dinucleotides TA and GC increase cyclizability, whereas TC and GA decrease it, since J12TA and J12GC are positive and J12TC and J12GA are negative (Fig. 4a, inset). The “symmetrized” J not only shows clear signals near the diagonal, suggesting strong nearest-neighbor interactions but also displays a set of stripes separated at half-helical (∼5 bp) and helical (∼10 bp) period of DNA, suggesting a role of longer-ranged interactions collectively contribute to DNA cyclizability.

  Imposing translational and reverse-complement invariances raises the signal-to-noise ratio of the inferred J matrix, and consequently raises the predictive performance of the model. Predictions versus measurements of intrinsic cyclizability are shown in Fig. 4b as a joint density plot, which are obtained from multiple random 90/10 splits of the Random library into training and testing data. The correlation between predictions and measurements is now r=0.68±0.02.


### Sequence features that control DNA cyclizability
  The predictive power of the model would improve further if we incorporate the three-base interaction terms in Eq. (1). Yet, to keep the model minimal, we defer these extensions and instead search for sequence features that control DNA cyclizability within the pairwise model. To identify sequence features, we apply eigenvalue decomposition (or principal component analysis) to the J matrix:

  where n is the mode index and the eigenvectors are orthonormal,

  We show in Fig. 5a the spectrum of eigenvalues {λn} in rank order and compare with data that have been shuffled to break any correlations between sequence and cyclizability. We first notice that, in both the real and shuffled data, there are some true zero eigenvalues. These arise because we have ∑αSiα=1 at each site i, by definition. In the shuffled data, we see a spreading of the eigenvalues, which arises because the J matrix is estimated from a finite sample (38, 39). Last and most importantly, in the real data, the eigenvalues stand out from the shuffled background with high signal-to-noise ratios at both large positive and negative values, especially at the two largest eigenvalues. We show in Fig. 5b the first and last two eigenvectors, which pick out the most and least cyclizable modes of sequence variation. The first two eigenvectors come as a quadrature pair, showing an approximate ten-base periodicity that aligns with the pitch of the double helix DNA. The last two modes, with their eigenvalues less clearly distinguished from the background noise (Fig. 5a), are less clearly periodic and exhibit boundary effects.

  We can decompose the sequence variations into modes defined by the eigenvectors:

  where

  Equation (4) is then simplified to

  where the sum is over all the modes. In Fig. 5c, we show the dependence of the cyclizability C0 on fn at the extremes of the spectrum. To avoid overfitting, we estimate Jijαβ and subsequently the eigenvectors wiα(n) from random half of the sequences, and then probe C0 versus fn in the other half. The mean behavior is quadratic for each mode, consistent with the prediction of Eq. (14), supporting the validity of the model in Eq. (4).

  Equation (14) further enables the separation of contributions from individual modes to cyclizability. Including only the first two modes, ie sum over n=1,2 in Eq. (14), results in r=0.60±0.02 in the predictive performance, suggesting that these two modes make the largest contribution, but including all modes provides better predictions, Fig. S2.


### Comparison of Random and Tiling libraries
  Above, we adopted a statistical-mechanics approach to analyze cyclizability of sequences in the Random library. Yet biologically relevant sequences are not random. For example, the yeast genome has a base composition of approximately 62% A/T and 38% C/G (40), which deviates significantly from random sequences. To test if our findings from the Random library extend to biological sequences, we analyze a second available dataset, the Tiling library, which comprises sequences from the genome of S. cerevisiae (27).

  In the analysis of the Random library, we utilized the statistical properties of random sequences to compute the matrices W and J directly from data, using Eqs. (3) and (5), respectively. These two equations however no longer hold for the Tiling library. Nevertheless, as briefly mentioned before, it is possible to extract the matrices with a least-squares fit directly applied to Eqs. (2) and (4). To validate the least-squares approach, we first apply it to the Random library. The resulting W and J matrices match almost exactly those obtained from Eqs. (3) and (5), with Pearson correlation coefficients r=0.99 and 0.98, respectively (Fig. S3). We then apply the least-squares approach to the Tiling library. In Fig. S4, we show the extracted W which again is consistent with W=0. The correlation coefficient between predictions and measurements of the linear model is r=0.07±0.01, slightly higher than that of the Random library. In Fig. S5, we show the extracted J matrix, which shares many similarities with the one from the Random library. The correlation coefficient between predictions and measurements of the pairwise model is r=0.68±0.01, comparable to that of the Random library. For a direct comparison between the Tiling and Random libraries, the matrix elements of J for the two libraries were plotted against each other in Fig. 6a, which are highly correlated with r=0.90. The most and least cyclizable modes of the two libraries were compared in Fig. 6b. While the most cyclizable modes are consistent between the two datasets, the least cyclizable modes are clearly different.

  We can further construct the most and least cyclizable sequences from the eigenvectors of the two libraries. Because the eigenvectors are orthonormal, increasing the projection of a sequence onto one eigenvector necessarily decreases its projection onto others, the highest and lowest values of C0 are thus predicted to occur in sequences that have maximal squared projection onto the first and last modes, respectively. Mathematically, this means we look for sequences {Siα} that maximize f12 and f2002 in Eq. (13). We note that because λ1 and λ2 (similarly, λ199 and λ200) come almost as a degenerate pair, sequences that maximize f22 and f1992 will have comparable cyclizabilities as the most and least cyclizable ones. The predicted most and least cyclizable sequences for the two libraries are listed in Table 1. The most cyclizable sequences are identical for both libraries, which consists of 5–6 bp tracts of TA-rich segments (eg TTAAA) followed by 5–6 bp tracts of GC-rich segments (eg GGGCCC) periodically. In contrast, the least cyclizable sequence for the Random library consists of short ∼3 bp segments with nucleotides in the order of ATCG, while the sequence for the Tiling library exhibits a periodic structure similar to the most cyclizable sequence but with longer 8–10 bp tracts of AT-rich segments where As appear in front of Ts (eg AAAAATTTTT).


### Molecular dynamics simulations of most and least cyclizable sequences
  To support our predictions of the most and least cyclizable sequences in Table 1, we performed all-atom molecular dynamics simulations of these sequences in a 1M NaCl solution at constant temperature (300 K) with periodic boundary conditions. The simulations were carried out using the NAMD software (41) with the CHARMM36 force field (42), see “Details of molecular dynamics simulations” section for details of the simulation setup. We show in Fig. 7a–c representative snapshots of DNA for each sequence (taken at 72 ns). Remarkably, the most cyclizable sequence curves into a semicircle (Fig. 7a), whereas the least cyclizable sequences for both libraries remain straight (Fig. 7b and c). To quantify the bending differences, we extracted the helical axis of the DNA molecule using the Curves+ program (43) and computed the end-to-end distance at each frame along the trajectories. While all sequences were initialized in an extended state, the end-to-end distance of the most cyclizable sequence decreases noticeably after around 20 ns, compared to those of the two least cyclizable sequences, which remain relatively extended throughout the run (Fig. 7d). Corresponding videos can be found in the Zenodo data repository (DOI: 10.5281/zenodo.18698120). Observations from the end-to-end distance plot and simulation videos further suggest that the least cyclizable sequence of the Tiling library is slightly more dynamically flexible than that of the Random library. Overall, these results strongly support the predictions of our statistical model.


## Discussion
  The mechanical properties of DNA play an important role in many biological processes. Recent experiments have revealed that the mechanics of short DNA molecules depends strongly on their sequences. However, a systematic characterization of the sequence features that control DNA mechanics has been lacking. In this work, we developed a statistical mechanics approach to analyze high-throughput measurements of DNA cyclizability of randomly generated and biologically derived sequences. We found that a minimal model with pairwise interactions between nucleotides is sufficient to account for the sequence dependence of cyclizability, leading to the prediction of the most and least cyclizable sequences. We further validated these findings through all-atom molecular dynamics simulations of predicted sequences.

  How do our findings compare to those in the literature? Early studies on the sequence dependence of DNA mechanics primarily focused on the influence of dinucleotide pairs due to limited data (44, 45). Recent development in high-throughput methods have enabled investigations that extend nucleotide interactions to longer length scales. In many respects, our findings align with the consensus knowledge in the field (2, 46). Specifically, our predicted most cyclizable sequence is consistent with findings from recent SELEX experiments, where the selected highly loopable sequences are enriched with alternating short segments of A/T and C/G separated by half a helical pitch of DNA (47). Mechanistically, both dynamic flexibility and static bending contribute to the cyclizability of a sequence. Our all-atom simulations suggest that the increased cyclizability of the most cyclizable sequence is mainly due to constructive bending toward one direction, driven by intrinsic curvatures encoded in the sequence. This is analogous to the previously reported globally curved structures formed by sequences with in-phased A-tract repeats (48–50). Our predicted least cyclizable sequence from the Random library is enriched in CpG steps, which was reported to increase the rigidity of the sequence (51, 52). The least cyclizable sequence from the Tiling library is enriched in out-phased A-tracts, also known to be very rigid (18). While our findings are largely consistent with previous studies, our systematic framework allows us to extract sequence features more comprehensively, providing a deeper and more quantitative understanding of the determinants of DNA cyclizability.

  One limitation of the pairwise model is that its predictive power is lower than that of recent deep neural network models. The Pearson correlation coefficient between predictions and measurements is r≈0.7 for the pairwise model, compared with r≈0.8–0.9 for deep neural networks (28–31) and notably r=0.96 in the most recent development (9). This indicates that higher-order interaction terms are necessary to fully capture DNA cyclizability. In a separate (unpublished) study, we incorporated three-body interaction terms in Eq. (1) and improved the predictive power to r≈0.92, validating that cyclizability is a highly collective property. Because sequence features inferred from the pairwise model may inherit a similar level of inaccuracy, we checked their robustness by comparing extreme sequences predicted by our model to those inferred from a deep-learning approach (9) (Table S1). Despite the neural network retaining higher-order correlations, both approaches identify a common coarse-grained organization: high-cyclizability sequences are enriched for alternating short (5–6 bp) AT-rich tracts and GC-rich tracts, whereas low-cyclizability sequences contain longer (8–10 bp) AT-rich tracts with comparatively shorter GC-rich interruptions. These shared motif-level trends suggest that such coarse-grained features inferred from the pairwise model are robust. However, there are differences in finer-scale nucleotide ordering within tracts. For example, our most cyclizable sequence has T preceding A (eg TTAAA), whereas the deep-learning approach predicts A preceding T (eg AAAAAT) or pure A/T tracts (eg AAAAAA). Moreover, the GC-rich segments in the low-cyclizability sequences from the deep-learning approach are mostly CG dinucleotide, whereas our sequence contains GC-rich segments with G preceding C in most cases (eg GGGCC). These finer-scale differences motivate feature interpretation in higher-order models. Nevertheless, the pairwise model stands out for its simplicity and physical interpretability. It captures leading-order sequence determinants, and offers a starting point for systematic higher-order extensions.

  Moving beyond sequence-dependent DNA mechanics, our method establishes a general framework to address a broad class of problems, where the input lives in a high-dimensional space and the output represents a functional property of the system. With the continued advancement of high-throughput technologies, we anticipate the method developed here to have broad applications. Representative problems in this class include the search for relevant sequence features of DNA, RNA, and proteins that determine their structures, interactions, and functions, as well as the search for relevant stimulus features that govern the responses of sensory neurons.


## Methods

### Details of theoretical methods
  For case I, we have

  where Eq. (17) was used to derive the last line. Similarly, for case II, we have

  Substituting results in Eqs. (20) and (21) into Eq. (19), we have

  which is Eq. (5).


### Details of molecular dynamics simulations
  All-atom molecular dynamics simulations of 50-bp DNA sequences in Table 1 were conducted following the outlined steps below, which were adapted from a previously developed pipeline for quantifying the flexibility of DNA molecules (21).


## Supplementary Material

## Supplementary material
  Supplementary material is available at PNAS Nexus online.


## Competing interest
  The authors declare no competing interests.


## Funding
  M.G. and Y.Z. were supported by a startup fund at Johns Hopkins University and by NIH award R35GM162296. Y.Z. acknowledges support from Sloan Foundation through a Sloan Research Fellowship (FG-2025-25076). W.B. and Y.Z. were supported in part by the National Science Foundation through the Center for the Physics of Biological Function (PHY-1734030) and by NSF grant PHY-1607612. A.B. was a Simons Foundation Fellow of the Life Sciences Research Foundation, and T.H. is an Investigator at the Howard Hughes Medical Institute.


## Preprints
  This manuscript was posted on a preprint: https://doi.org/10.1101/2025.01.02.631081.


## Data availability
  The analysis code supporting the findings of this study is available on GitHub (https://github.com/Zhang-Lab-JHU/DNA-cyclizability-code), which includes scripts for the statistical mechanics model and molecular dynamics simulations, along with the corresponding input cyclizability data. All-atom simulation outputs are deposited in Zenodo (DOI: 10.5281/zenodo.18698120), which includes DNA trajectories stripped of solvent and ions, and the associated helical axis trajectories.


## Acknowledgments
  We are grateful to Ana Damjanovic, Albert Lau, and Mankun Sang for insightful discussions and constructive feedback on the manuscript.