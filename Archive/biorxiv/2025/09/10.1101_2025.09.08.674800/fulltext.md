## Abstract

Protein sequence determines the structure, function, and dynamics of a protein. In recent years, enormous progress has been made in translating sequence information into structural information using machine learning approaches. However, because of the underlying methodology, it is an immense computational challenge to extract this information from the ever-increasing number of sequences. In the present study, we show that it is possible to create two-dimensional contact maps from sequences, for which only a few exemplary structures are available on a laptop without the need for GPUs or high-performance computing clusters. This is achieved by using a pattern matching approach. The resulting contact maps largely reflect the interactions in the three-dimensional structures. The validity of our method was tested on the 25 protein domains, with abundant structural data, achieving correlations of 0.73-0.94 between predicted and experimental contact maps. To demonstrate broader applicability, we further validated our approach on 7,599 poorly annotated sequences using homologous structural templates, achieving a mean F1-score of 0.609 ± 0.095 and mean accuracy of 0.954 ± 0.036 when compared against high-confidence AlphaFold structures. These results demonstrate that our pattern matching approach maintains robust performance even when relying on a small number of structural templates.


## Introduction

Despite the rapid growth of sequenced proteins, experimentally determined structures remain available for only a small fraction, creating a gap between sequence data and structural knowledge. This imbalance limits our ability to infer function, understand molecular mechanisms, and explore protein dynamics at scale. Machine learning-based structure prediction methods, including AlphaFold2 1 , RoseTTAFold 2 and ESMfold 3 , have transformed structural biology, yet they require substantial computational resources that limit their application in high-throughput analyses.

Contact maps, representing pairwise spatial relationships between amino acid residues, provide a simplified but informative representation of protein structure. These two-dimensional matrices capture essential structural features while reducing computational complexity. Here, we present a pattern-matching approach that leverages existing structural repositories to rapidly generate contact maps for query sequences. Rather than predicting full three-dimensional structures, the method identifies conserved contact patterns from homologous proteins and maps them onto query sequences. By integrating multiple structural templates, including alternative conformations, our approach captures dynamic features of proteins and can identify conserved motifs even when sequence similarity is limited. By analyzing contact patterns across multiple conformational states, one can gain insights into protein dynamics that might otherwise require extensive molecular dynamics simulations.

This strategy offers several advantages: it reduces computational cost, enables high-throughput analyses, and provides biologically meaningful predictions for proteins with limited structural information. To benchmark the method, we analyzed 25 well-characterized protein domains, comparing their predicted contact maps with experimentally determined reference structures. We further evaluated its applicability on poorly annotated sequences lacking comprehensive structural coverage, demonstrating that evolutionarily related homologs can still provide informative patterns for contact prediction.


## Methods


## Sequence and Structure Retrieval

We prepared two complementary datasets for method evaluation. The primary benchmark consisted of 25 well-characterized protein domains from InterPro 4 ( Table 1 ). We retrieved all available sequences and curated PDB structures for each entry to ensure high-quality annotation and capture conformational diversity. The second dataset comprised of 7,599 poorly annotated proteins from UniProt’s 5 TrEMBL 6 collection ( Table 2 , Table S2). Unreviewed sequences were filtered for low annotation scores(annotation scores of 1), sequence diversity, and high-confidence predicted structures (with average pLDDT ≥ 80). JackHMMER 7 was used to identify homologous PDB structures, applying additional filters to exclude sequences with excessive (>1,500) or insufficient (<50) structural hits. After filtering, the dataset included proteins with diverse secondary structure compositions representative of the general protein population. Specifics of the selection process are explained and shown in the Zenodo repository.

For both datasets, available PDB structures were filtered by resolution (≤3.0 Å), and all NMR structures were retained to preserve conformational variability. For domains lacking experimental structures, AlphaFoldDB can be used as a complementary structural source.


## Contact Pattern Identification

Contact patterns were defined as spatial arrangements of up to five amino acid residues whose centers of mass are located within a maximum distance of 8.0 Å from each other. For each structure, all pairwise residue distances were computed, and clusters meeting this criterion were extracted as patterns. Each pattern was encoded using a simple notation: residues involved in contacts were represented by uppercase letters, and intervening residues by lowercase letters. Patterns were stored in a domain- or sequence-specific library for subsequent alignment.

Predicted contact maps were generated by aligning patterns from the library to query sequences using MATLAB’s(MATLAB R2023b) localalign function, with an increased gap-opening penalty of 10 to favor precise motif matching. When a pattern is successfully aligned to the query sequence, corresponding elements of the N × N contact matrix and their symmetric counterparts were incremented by 1. This process was repeated for all patterns in the domain or sequence-specific pattern library, cumulatively building the contact map through pattern alignment on the query sequence.


## Benchmarking and Validation

A two-tier benchmarking strategy was employed:

For each of the 25 protein domains in our benchmark set ( Table 1 ), we compared mean contact maps generated by our pattern matching approach with mean reference contact maps derived from experimentally determined structures.To address the substantial size difference between prediction datasets and experimental datasets, we employed a bootstrap resampling framework with 1,000 iterations. Multiple sequence alignments were generated using Clustal Omega 8 to establish correspondence between predicted and experimental structures.

The statistical analysis implemented a dual-metric approach evaluating both full alignments and filtered regions, with Pearson correlation coefficients and bias metrics including mean absolute error and systematic deviation calculated across all aligned positions for full alignment analysis. In parallel, a filtering strategy addressed alignment quality differences by eliminating MSA columns with high gap content, calculating per-position coverage for both datasets and applying an intersection strategy to identify positions where both achieved at least 30% coverage for unbiased comparison. Statistical significance was established through bootstrap distributions enabling calculation of 95% confidence intervals and paired t-tests, with p-values computed for both comparison scenarios. The analysis extended to distance-dependent characterization examining sequence separations of 1, 5, 10, 15, 20, and 25 residues, and regional classification grouping contacts into short-range (|i-j| < 12), medium-range (12 ≤ |i-j| < 24), and long-range (|i-j| ≥ 24) categories. Performance evaluation encompassed comprehensive classification metrics including ROC curves with AUC values, precision-recall curves, and F1 scores at optimal thresholds, computed for both full and filtered analyses, providing statistically robust evidence for comparing datasets of vastly different sizes while accounting for varying data quality.

Predicted contact maps were validated against high-confidence AlphaFold models. Standard classification metrics were computed for each sequence, including accuracy, precision, recall, specificity, F1-score, and Matthews Correlation Coefficient (MCC). Population-level performance was summarized by mean and standard deviation across all sequences, and best/worst performers were identified to illustrate range of applicability.

This dual-validation framework allows robust assessment of method performance across datasets with vastly different structural coverage, ensuring applicability to both well-characterized protein families and poorly annotated sequences with limited structural information.


## Results

Application of the pattern-matching approach yielded contact maps that closely recapitulated the characteristic residue–residue networks of known protein folds. Across diverse protein families, the method reliably recovered conserved interaction patterns that could be directly compared with experimentally determined contact maps. This approach builds upon the successful framework demonstrated by Bradley, Kim, and Berger (2002) 9 for identifying structural motifs that represent specific protein fold characteristics. As illustrated in Figure 1 , this procedure reconstructs contact networks that align well with structural reference data.

To assess the performance of our approach, we applied it to two complementary datasets. The primary benchmark consisted of 25 well-characterized protein domains from InterPro 4 ( Table 1 ). These domains are supported by well-curated sets of PDB structures, often capturing distinct conformational states, and thus provide a stringent test set with comprehensive structural annotation.

As a second benchmark, we assembled a dataset of sequences from UniProt’s 5 TrEMBL 6 collection. Unlike the curated InterPro domains, these proteins lack extensive experimental annotation. This dataset therefore evaluates the applicability of the method under conditions where structural information is sparse, reflecting a more realistic scenario for newly identified proteins.


## Performance on well-characterized protein domains

We first benchmarked our approach on 25 InterPro domains representing diverse architectures and supported by abundant structural data ( Table 1 ). These domains span 20–250 residues and cover a wide range of secondary structure compositions, from loop-rich EGF-like domains (76.6% loops) to highly ordered spectrin repeats (9.0% loops). The large number of available experimental structures per domain (on average 473, up to 2,047 for the ubiquitin family) provided a robust basis for statistical evaluation.

Across all 25 families, the pattern-matching method showed robust performance, with correlation coefficients between predicted and reference contact maps ranging from 0.735 to 0.942. Classification accuracy was consistently high, with ROC AUC scores between 0.865 and 0.995, and F1 scores between 0.664 and 0.931. Thus, even in families with more modest correlations, discrimination between true and false contacts remained excellent (AUC >0.9 in all cases).

Family-specific differences were observed. Top-performing domains such as PF01023 (S-100), PF00505, PF00435 (Spectrin repeat), PF00001 (7TM receptor), and PF00249 consistently achieved correlations above 0.92 and F1 scores above 0.91, reflecting strong evolutionary constraints. By contrast, families such as PF00089 (Trypsin) showed lower correlations (0.735) but still maintained strong classification accuracy (AUC = 0.910).

Systematic biases in contact probability calibration varied by family, with small domains (25– 30 residues; e.g., PF00400, PF00096, PF00036) tending to under-predict contacts, while larger domains (83–250 residues; e.g., PF00089, PF00085, PF00017) showed slight over-prediction. These trends suggest that structural constraints and domain size jointly shape predictive behavior.

Contact range analysis revealed that short-range contacts (≤5 residues) were predicted most accurately (r = 0.772–0.929), while medium-range (5–15 residues) and long-range (>15 residues) contacts showed greater variability across families. Notably, the EF-hand domain (PF00036) achieved exceptional long-range prediction (r = 0.946), whereas the ligand-gated ion channel domain (PF00060) performed less well (r = 0.424).

Secondary structure composition strongly influenced predictive accuracy. Domains with higher loop content consistently exhibited reduced correlations: the loop-rich EGF-like domain (PF00008, 76.6% loops) reached r = 0.836, below the overall mean of 0.867. In contrast, the spectrin repeat (PF00435, 9.0% loops) achieved the highest correlation (r = 0.932). By contrast, domain size itself showed no significant correlation with accuracy, indicating that loop content, rather than length, is the primary determinant of performance.

Representative examples illustrate the range of outcomes. The S-100 domain (PF01023; r = 0.942, AUC = 0.972; Figure 2 ) exemplifies high accuracy, the RNA recognition motif (PF00076; r = 0.872, AUC = 0.988; Figure 3 ) shows intermediate performance, and trypsin (PF00089; r = 0.735, AUC = 0.911; Figure 4 ) represents lower correlations but still strong classification. Additional examples are provided in Figures S1–S50, with detailed metrics in Supplementary Text Files S1–S26.

Overall, these results demonstrate that the pattern-matching approach achieves highly reliable contact prediction across structurally diverse protein families, with performance primarily influenced by secondary structure composition rather than domain length.


## Performance on poorly annotated sequences

To test the generalizability of our approach, we next evaluated 7,599 poorly annotated sequences, which lack curated experimental annotation and can only be represented by reference AlphaFold models. The method maintained robust predictive performance: over 90% of sequences achieved accuracies above 0.90 ( Fig. 5A ), and precision–recall analyses confirmed balanced classification with relatively few outliers ( Fig. 5B–C ). Additional measures, including specificity and Matthews Correlation Coefficient (MCC), consistently supported the reliability of contact predictions across diverse protein families ( Fig. 5D–F ).

Prediction accuracy was strongly affected by secondary structure content. Proteins dominated by well-ordered helices or sheets showed near-perfect predictions—for example, A2AIM4, with only 1% loop residues, achieved accuracy = 0.995 and MCC = 0.919. By contrast, highly disordered proteins performed more poorly: Q7M4S4, composed entirely of loops, reached only 0.550 accuracy and MCC = 0.379. Representative examples of high-, medium-, and low-accuracy cases are shown in Figures 6 – 8 . Overall, these results highlight that loop-rich or intrinsically disordered regions are the main challenge for contact prediction, whereas structured domains yield excellent agreement with reference models.

We also examined whether the number of structural homologs in the PDB influences prediction accuracy. Surprisingly, performance showed a negative correlation on the number of PDB hit counts with MCC and F1 scores, the correlation values are -0.164 and -0.178 respectively; Fig. 9B– C ). Grouping sequences by homolog abundance revealed slightly declining MCC and F1 scores as hit counts increased ( Fig. 9D ). Thus, adding more distant homologs does not improve performance and may in fact dilute the signal. Tables 3 and 4 list the best and worst performers, further illustrating that accuracy is not driven by homolog availability.

These findings demonstrate that the pattern-matching approach remains effective for poorly annotated proteins, even when only predicted structures are available. Performance is primarily determined by secondary structure composition rather than dataset curation or homolog abundance. The comparable results between curated domains and unreviewed sequences suggest that the essential structural motifs captured by the 8.0 Å contact patterns are conserved across wide evolutionary distances, supporting the biological relevance of this representation for newly discovered proteins, including archaeal candidates.


## Discussion

Understanding the protein structure is essential for explaining the biological function, yet the gap between sequenced proteins and experimentally determined structures continues to widen. In this study, we developed a pattern-matching approach that uses existing structural data to rapidly generate contact maps from sequence information alone. By validating the method on both well-characterized protein domains and poorly annotated sequences, we demonstrate its versatility, robustness, and practical utility across a wide range of proteins.

Our approach accurately predicts contacts across diverse protein families, capturing both short- and long-range interactions. Prediction performance is influenced by protein architecture, secondary structure composition, and evolutionary constraints, with well-structured domains yielding the most reliable results and loop-rich or intrinsically disordered proteins remain more challenging, highlighting the method’s dependence on conserved structural motifs for optimal accuracy.

The method also performs robustly for poorly annotated sequences, using distant homologs to generate meaningful contact predictions. This demonstrates its applicability to metagenomic datasets and proteins from organisms with limited structural coverage. Examples of such uncharacterized proteins include archaeal sequences, where our predictions show good agreement with AlphaFold reference structures (supplementary contact maps provided). Interestingly, increasing the number of structural homologs does not necessarily improve prediction quality, suggesting that a modest set of representative templates are sufficient to capture essential structural patterns.

A key advantage of our approach is its computational efficiency and interpretability, requiring minimal resources while revealing which structural motifs drive contact predictions. By integrating patterns from multiple structural states, the method inherently captures conformational flexibility, providing insights into dynamic protein behavior and allosteric mechanisms that would otherwise require extensive molecular dynamics simulations. This capability enables practical applications in functional annotation and drug discovery, allowing researchers to identify potential binding sites, infer allosteric pathways with additional methods, and guide structural characterization for novel proteins, even when experimental structures are unavailable.

Despite these advantages, the approach has limitations. Prediction accuracy is reduced for proteins dominated by loops or disorder, and the current 8.0 Å contact cutoff may not capture all functionally relevant long-range interactions in very large proteins. Future improvements could involve adaptive cutoffs or expanded pattern libraries to enhance coverage and accuracy.

Our study demonstrates that pattern-based contact map prediction provides a practical alternative to full structure prediction, bridging the gap between sequence and structure in a computationally efficient manner. As structural databases continue to expand, this approach can be readily adapted for exploratory studies in emerging protein families.


## Availability of the code

The data that support the findings of this study are openly available in the Zenodo repository with the link https://zenodo.org/records/17043595 .

Acknowledgments

This work was supported by the Swiss National Science Foundation (Grant 310030_219549 to D.F.). We thank the Division de Calcul et Soutien à la Recherche of the UNIL for access to the university’s computer infrastructure. We thank all members of the Fasshauer Laboratory for helpful discussions.


## Author contributions

A.H. designed the study, performed the experiments, and analyzed the data; A.H. and D.F. wrote the paper.


## Competing interests

The authors declare no competing interests.


## Abbreviations