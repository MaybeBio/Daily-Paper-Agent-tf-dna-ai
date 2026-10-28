## Abstract

The interplay between transcription factors (TFs) and nucleosomes is central to gene regulation, yet most studies adopt a protein-centric perspective that largely overlooks DNA sequence contributions. Here, we identify four distinct nucleosomal DNA classes, including the canonical WW/SS pattern (W = A/T, S = G/C). All four nucleosome types are widespread across the human genome both in vivo and in vitro . Nucleosomes sharing the same pattern are rotationally in phase, whereas different patterns exhibit specific rotational offsets, revealing distinct DNA-encoded codes for nucleosome positioning. Analysis of 747 TFs across eukaryotes shows that the WW/SS and anti-WW/SS patterns are strongly associated with TF binding in chromatin. Differences in the proportions of these two patterns, quantified as ΔNPS values, correlate closely with in vitro nucleosome occupancy. Integrating ΔNPS with in vivo nucleosome occupancy uncovers four distinct modes of nucleosome-TF interaction and provides new insight into nucleosome-depleted regions around TF binding sites.


## Introduction

Understanding the interaction modes between transcription factors (TFs) and nucleosomes is central to gene regulation 1 – 3 . The traditional view holds that TFs compete with nucleosomes for access to their binding sites 4 , 5 , a model supported by ChIP-seq analyses showing that TF-bound genomic regions are typically nucleosome-depleted regions (NDRs) 6 . However, numerous studies have demonstrated that a subset of TFs, including pioneer factors, can directly bind nucleosomal DNA 7 , 8 .

Most studies of nucleosome-TF interactions have relied on protein-centric experimental approaches, such as electrophoretic mobility shift assays 9 , 10 , single-molecule fluorescence methods 11 , 12 , cryogenic electron microscopy 13 – 15 , SELEX 16 , and protein microarray 17 . These experiments typically employed a limited number of nucleosomal DNA templates, including the synthetic ‘601’ sequence 18 or a small set of genomic loci with strong nucleosome positioning sequences (NPSs), such as yeast Hsp82 19 , ribosomal protein L30 genes 20 , mouse ALBN1, NRCAM, and CX3CR1 17 , and the human lin28b locus 21 . Consequently, prior work has focused primarily on TFs rather than their DNA binding partners.

Nucleosome-TF interactions are influenced by the rotational phasing of TF binding motifs within nucleosomes 22 – 25 . Early studies of the glucocorticoid receptors showed that motif accessibility depends on rotational positioning 22 , with similar effects observed for p53 23 , 24 and SRY-box 2 25 . Rotational positioning is defined by which face of the DNA duplex contacts the histone core 26 and is strongly determined by DNA sequence 27 – 33 .

One of the best-characterized sequence motifs is the WW/SS pattern (W = A/T, S = G/C), in which WW dinucleotides preferentially occupy minor-groove bending sites (minor-GBS) and SS dinucleotides occupy major-groove bending sites (major-GBS) 34 . This pattern exhibits a ∼10-bp periodicity and is structurally stabilized by conserved “sprocket” arginine residues that insert into minor grooves 35 – 37 , favoring interactions with AT-rich DNA that narrows the minor groove 38 – 40 . These periodic interactions form the structural basis for rotational positioning.

An opposite sequence motif, termed anti-WW/SS, places WW and SS dinucleotides in reversed groove contexts 41 , leading to less favorable histone–DNA interactions. We previously showed that anti-WW/SS nucleosomes are enriched in mammalian genic regions 42 and potentially stabilized by H4 and H2A histone N-tails 43 , but their role in nucleosome-TF interactions remained unclear.

Here, we identified four distinct nucleosomal DNA patterns in the human genome, Types 1-4. Nucleosomes sharing the same pattern are rotationally in phase, whereas different types exhibit specific phasing relationships. We show that Type-1 and Type-4 nucleosomes are preferentially associated with TF binding. The difference in their regional abundance, quantified as ΔNPS, strongly correlates with in vitro nucleosome occupancy (NO). Integrating ΔNPS with in vivo NO reveals multiple modes of nucleosome-TF interaction.


## Results


## Four types of nucleosomes are widespread across the human genome

We extracted nucleosome core particle (NCP) DNA from a human in vitro nucleosome map 44 and an in vivo map generated in GM12878 cells 45 (Supplementary Table S1). As shown previously 42 , NCP fragments of 147 bp can be classified into four sequence patterns, Types 1-4, based on the relative frequencies of WW and SS dinucleotides across the 12 minor- and 12 major-GBS ( Figure 1A ). Type-1 nucleosomes exhibit the canonical WW/SS pattern, with WW enriched in minor-GBS and SS enriched in major-GBS. Type-2 and Type-3 nucleosomes display “mixed” patterns: Type-2 nucleosomes show higher WW and SS occurrence in minor-GBS than in major-GBS, whereas Type-3 nucleosomes show the opposite. Type-4 nucleosomes represent the inverse of the WW/SS pattern, with WW enriched in major-GBS and SS enriched in minor-GBS ( Figure 1B ) and are therefore referred to as anti-WW/SS nucleosomes.

All four nucleosome types are present in both in vivo ( Figure 1B ) and in vitro (Supplementary Figure 1) maps. In both datasets, Type-1 nucleosomes are the most abundant class, followed by Type-4, Type-2, and Type-3 nucleosomes (Supplementary Tables S2–S3). Comparing their relative fractions reveals notable differences between in vitro and in vivo landscapes. The in vitro map contains ∼3% more Type-1 nucleosomes and ∼3% fewer Type-4 nucleosomes compared to the in vivo map, whereas the differences for Type-2 and Type-3 nucleosomes are much smaller (∼1%). This suggests that Type-1 nucleosomes are energetically favored in vitro , likely because nucleosome positioning in the absence of chromatin-associated proteins reflects intrinsic histone-DNA preferences.

These observations imply that chromatin-associated proteins, such as transcription factors, chromatin remodelers, and RNA polymerase, redistribute nucleosomes with different DNA-encoded patterns. Notably, this redistribution exerts stronger effects on Type-1 and Type-4 nucleosomes than on Type-2 and Type-3. Consistently, the difference in abundances between Type-1 and Type-4 nucleosomes is 9.8% in vitro , nearly three-fold higher than the corresponding difference in vivo (3.3%). In contrast, the shift between Type-2 and Type-3 nucleosomes is more modest (7.6% in vitro versus 5.6% in vivo , Supplementary Table S4).

In summary, two key conclusions emerge. First, all four nucleosome types are broadly distributed across the human genome in both in vitro and in vivo conditions. Second, Type-1 and Type-4 nucleosomes exhibit substantially larger differences between in vitro and in vivo contexts than Type-2 and Type-3, indicating that chromatin proteins exert stronger regulatory influence on nucleosomes with these two sequence patterns.


## The four types of nucleosomes exhibit distinctive genomic organization

To investigate how the four nucleosome types are organized across the genome in vivo and in vitro , we first computed normalized nucleosome occupancy at every base pair and then calculated pairwise correlations between nucleosome maps. Both in vivo and in vitro datasets revealed a consistent pattern. The full nucleosome map showed the highest correlation with the Type-1 map (0.74 in vivo , 0.76 in vitro ; Figure 2A and Supplementary Figure S3A), consistent with the fact that Type-1 nucleosomes are the most abundant class (Supplementary Table S4). The second-highest correlation was observed between the full map and the Type-4 map (0.72 in vivo , 0.71 in vitro ; Figure 2D and Supplementary Figure S3D). Lower correlations were observed for Type-2 (0.60 in vivo , 0.63 in vitro ; Figure 2B ) and Type-3 (0.45 in vivo , 0.54 in vitro ; Figure 2C ), reflecting their lower abundance. Notably, the ranking of these correlations mirrors the relative frequencies of the four nucleosome types (Supplementary Table S4).

Comparisons among the four nucleosome-type maps yielded several additional insights. First, Type-1 and Type-4 nucleosome maps exhibited the strongest cross-correlation (0.51 in vivo , 0.47 in vitro ; Supplementary Figures S2C and S3G). Second, Type-2 and Type-3 maps showed the next highest correlation values (0.41 in vivo , 0.39 in vitro ; Supplementary Figures S2D and S3H). Third, all remaining pairwise comparisons displayed relatively low correlations, ranging from 0.13–0.24 in vivo (Supplementary Figures S2A–B, S2E–F) and 0.27–0.32 in vitro (Supplementary Figures S3E–F, S3I–J).

Together, these results indicate that nucleosomes with certain DNA sequence patterns tend to co-localize across the genome. Specifically, Type-1 and Type-4 nucleosomes appear to occur together, whereas Type-2 and Type-3 nucleosomes form a separate organizational group. This suggests that the four nucleosome types exhibit distinct spatial distributions along chromatin, likely reflecting the DNA-encoded rotational preferences and their interactions with chromatin-associated factors.


## Nucleosomes with different sequence patterns have specific rotational phasing

To examine the relative positioning of the four nucleosome types across the genome, we applied the distance auto-correlation (DAC) and distance cross-correlation (DCC) functions described previously 46 . The DAC function measures the positional relationships between pairs of NCPs from the same set (e.g., all Type-1 nucleosomes), whereas the DCC function measures positional relationships between NCPs from two different sets (e.g., Type-1 versus Type-4 nucleosomes).

We first computed the DAC function for the complete nucleosome set, which contains all four sequence patterns. In the in vitro dataset, weak peaks appear approximately at 10, 20, 30, and 40 bp (Supplementary Figure S4), consistent with earlier reports 44 . These ∼10-bp periodicities reflect overlapping nucleosome positions that share the same rotational orientation, indicating that DNA is wrapped such that the helical face contacting the histone octamer repeats every full turn of the DNA helix. In contrast, the in vivo dataset showed no such periodicity (Supplementary Figure S4), suggesting that the intrinsic rotational pattern can be disrupted by chromatin-associated proteins.

We then computed the DAC function for each nucleosome type separately. Strikingly, all four nucleosome types exhibited strong ∼10-bp periodicity both in vivo and in vitro ( Figure 3A–D ). Type-1 nucleosomes showed clear peaks at ∼10-bp intervals ( Figure 3A ), as did Type-2 ( Figure 3B ), Type-3 ( Figure 3C ), and Type-4 ( Figure 3D ) nucleosomes. These patterns indicate that nucleosomes sharing the same sequence pattern are rotationally in phase with one another, regardless of cellular context.

Analysis of the DCC function between different nucleosome types yielded several additional insights. First, DCC peaks were generally stronger in the in vivo dataset than in vitro (Supplementary Figure S4), likely to reflect the larger number of the in vivo NCPs (Supplementary Tables S2-S3). Second, Type-1 and Type-4 nucleosomes displayed strong out-of-phase peaks at ∼5, ∼15, ∼25, ∼35, and ∼45 bp (Supplementary Figure S5C) in both datasets, indicating a consistent half-turn rotational offset. Third, the same out-of-phase relationship was observed between Type-2 and Type-3 nucleosomes (Supplementary Figure S5D). Finally, all other pairwise comparisons produced two sets of peaks, one at ∼13, ∼23, ∼33 bp and another at ∼18, ∼28, ∼38 bp, across multiple type pairs (Supplementary Figure S5A–B, E–F), further demonstrating that nucleosomes with distinct sequence patterns have characteristic rotational spacing.

Because the sum of all individual DAC and DCC functions recapitulates the DAC function of the complete nucleosome population (Supplementary Table S5-S6), these patterns reveal that nucleosomes with different sequence motifs are arranged in a highly regular but previously hidden rotational organization.

Based on these results, we propose a rotational phasing model for the four nucleosome types, using Type-1 nucleosomes as the reference ( Figure 3E ). Type-1 nucleosomes are positioned ∼10 bp apart due to their in-phase relationships. Type-4 nucleosomes, which are out of phase with Type-1, are offset by ∼5 bp. For Type-2 and Type-3 nucleosomes, Type-1 nucleosomes are separated by distances of either 10n + 3 bp or 10n + 8 bp (where n = 0, 1, 2, …), consistent with the two peak groups observed in the DCC analyses (Supplementary Figure S5A–B). Type-2 and Type-3 nucleosomes themselves are ∼5 bp apart, reflecting their out-of-phase relationship (Supplementary Figure S5D).

In summary, we identify four distinct nucleosomal DNA sequence patterns that serve as DNA-encoded rotational positioning codes across the human genome. Nucleosomes with the same sequence pattern align rotationally in phase, whereas nucleosomes with different patterns adopt specific, predictable rotational offsets relative to one another.


## Type-1 and Type-4 nucleosomes are associated with TF binding

Because Type-1 and Type-4 nucleosomes show the largest differences between in vitro and in vivo maps (Supplementary Table S4), we hypothesized that these two nucleosome types influence TF binding in vivo , and that such effects should be reduced at motifs not bound by TFs. We used CTCF as a model system because its nucleosome organization has been extensively characterized 47 .

We began by examining nucleosome occupancy around CTCF motifs. As expected, in vivo NO shows a characteristic pattern: nucleosomes are depleted directly over CTCF-bound motifs and form strongly ordered arrays in the flanking regions (solid line, Figure 4A ), consistent with previous studies 47 . In contrast, unbound motifs exhibit a prominent occupancy peak with a normalized value of ∼1.25 (dashed line, Figure 4A ). The in vitro data reveal an occupancy peak with a similar height for both bound and unbound motifs ( Figure 4B ). Together, these observations show that CTCF binding leads to local nucleosome depletion, whereas in the absence of CTCF, a nucleosome is intrinsically favored at the motif.

Next, we examined the distribution of the four nucleosome types around bound CTCF motifs in vivo . Type-1 and Type-4 nucleosomes exhibit substantial changes across the motif relative to surrounding regions (Supplementary Figure S6A), whereas changes for Type-2 and Type-3 nucleosomes are minimal (Supplementary Figure S6B). This suggests that Type-1 and Type-4 nucleosomes play a dominant role in shaping nucleosome organization near CTCF-bound sites.

To investigate this further, we quantified the fractions of Type-1 and Type-4 nucleosomes near CTCF motifs. For both bound and unbound motifs, Type-1 nucleosomes are enriched at the motif center ( Figure 4C ). This enrichment is significantly greater for bound motifs than for unbound motifs (Student’s t -test, p < 10⁻⁷). Conversely, Type-4 nucleosomes are depleted at the motifs, with significantly stronger depletion for bound than unbound motifs ( Figure 4D ; Student’s t -test, p < 10⁻³).

To capture the contrasting behaviors of Type-1 and Type-4 nucleosomes, we used a previously defined metric, ΔNPS 42 , which measures the percentage difference between Type-1 and Type-4 nucleosomes in a given region. Because these two nucleosome types correspond to complementary DNA sequence patterns, WW/SS and anti-WW/SS, ΔNPS reflects the intrinsic strength of DNA-encoded nucleosome positioning. Higher ΔNPS values indicate stronger intrinsic nucleosome formation. Consistent with this, CTCF-bound motifs exhibit significantly higher ΔNPS values than unbound motifs ( Figure 4D ; Student’s t -test, p < 10⁻⁷), suggesting that intrinsically strong nucleosomes tend to occupy CTCF motifs and may compete with CTCF for binding.


## In vivo nucleosome occupancy and ΔNPS exhibit distinct patterns around TF binding sites

To investigate how TFs influence nucleosome organization at their genomic binding sites, we compared, for each TF, its in vivo NO profile with its ΔNPS profile. For CTCF, we observed a clear DIP/PEAK pattern: in vivo NO shows a pronounced dip over bound motifs, while the ΔNPS profile shows a corresponding peak (red and blue lines in Supplementary Figure S7A).

Plotting the in vitro NO profile revealed a strong peak centered on the motifs, closely resembling the ΔNPS profile (green line in Supplementary Figure S7A). This concordance reinforces the conclusion that ΔNPS captures the intrinsic strength of nucleosome positioning around TF-bound motifs. Because GC content has previously been linked to in vitro nucleosome occupancy at TF sites 48 , we also examined GC content around CTCF motifs. Indeed, GC content peaks at the motif center, mirroring the in vitro NO profile (Supplementary Figure S7C).

A second pattern, DIP/DIP, was observed for SPI1: both in vivo NO and ΔNPS exhibited a dip at bound motifs (Supplementary Figure S7B). The nearest ΔNPS peak is located ∼70–80 bp away from the center of the motifs. The in vitro NO profile also shows a dip, correlating well with ΔNPS. However, GC content behaves differently here: it shows a peak at the motif (Supplementary Figure S7D), indicating that GC content does not correlate with intrinsic nucleosome occupancy in this case.

Two additional patterns were identified in other TFs. NFIC displayed a PEAK/PEAK pattern, where both in vivo NO and ΔNPS profiles show peaks at bound motifs (Supplementary Figure S8A). NFYA showed a PEAK/DIP pattern, with in vivo NO showing a peak but ΔNPS showing a dip (Supplementary Figure S8B). For both TFs, the in vitro NO profile matches the ΔNPS profile. GC content correlates with intrinsic NO for NFIC (Supplementary Figure S8C), but not for NFYA (Supplementary Figure S8D).

Using these patterns, we classified 515 mammalian TFs and 232 yeast TFs into four groups, DIP/PEAK, DIP/DIP, PEAK/PEAK, and PEAK/DIP, according to their in vivo NO and ΔNPS profiles (Supplementary Tables S7-S9). Representative average profiles for each group are shown in Figure 5A-D . We also identified an AMBIGUOUS category for TFs lacking either a clear peak or dip in their in vivo NO profiles (Supplementary Figure S9).

Because about 20% of the 515 mammalian TFs exhibit different profile patterns across cell lines (Supplementary Table S7), we classified TFs into two datasets: a stringent set containing 413 TFs and a non-stringent set containing 515 TFs (Supplementary Table S10). The stringent set includes only TFs with a single dominant profile pattern across all examined cell lines. In contrast, the non-stringent set includes all TFs, including those with tied dominant patterns, which are assigned to each corresponding profile group.

Importantly, these profile groups found in human TFs are conserved across species: the same categories are observed in mouse TFs (Supplementary Figure S10) and yeast TFs (Supplementary Figure S11). This indicates that these patterns likely represent evolutionarily conserved modes of nucleosome-TF interactions.


## Discussion

Based on our data, we propose a unified model for the modes of nucleosome-TF interactions in vivo ( Figure 6 ) using the stringent set (Supplementary Table S10).

DIP/PEAK group (41% of TFs). These TFs have strong intrinsic nucleosomes located directly over their binding motifs. The in vivo depletion of nucleosomes indicates direct competition between TFs and these intrinsically positioned nucleosomes. In other words, TF binding displaces strong DNA-encoded nucleosomes.

DIP/DIP group (32% of TFs). These TFs have strong intrinsic nucleosomes positioned ∼70–80 bp away from the motif center. Thus, motifs are situated either in linker DNA or near the nucleosome edge, making them easily accessible. The absence of a strong DNA-encoded nucleosome at the motif itself is likely to contribute to the NDRs observed in vivo .

PEAK/PEAK group (11% of TFs). These TFs have strong intrinsic nucleosomes centered on their motifs. The enrichment of nucleosomal DNA in vivo suggests that these TFs bind DNA while it remains wrapped around a nucleosome, binding “at the center” relative to the nucleosome ends, though not necessarily at the dyad. These TFs appear to recognize or stabilize a well-positioned nucleosome.

PEAK/DIP group (3% of TFs). These TFs lack strong DNA-encoded nucleosomes near their motifs (ΔNPS shows a dip), yet nucleosomes are enriched in vivo . This suggests that nucleosome positioning is imposed not by DNA sequence but by protein factors such as chromatin remodelers or even the TFs themselves.

Our data indicates that, for DIP/DIP TFs, NDRs may arise because the local DNA sequence disfavors the formation of strong, stable nucleosomes. In this case, the genomic region is intrinsically nucleosome-poor, and TF binding does not require competition with nucleosomes. In contrast, TFs in the DIP/PEAK group are associated with strong intrinsic nucleosomes positioned over their motifs, as reflected by high ΔNPS values. For these TFs, NDRs likely result from direct competition, in which DNA-encoded nucleosomes are displaced or excluded upon TF binding.

Together, these results show that NDRs can arise through at least two distinct sequence-driven mechanisms: (i) the absence of strong intrinsic nucleosomes (DIP/DIP) and (ii) TF–nucleosome competition at sites with strong intrinsic nucleosomes (DIP/PEAK).


## Online Methods


## Genome-wide nucleosome positioning (MNase-seq) datasets

Both in vitro and in vivo nucleosome maps from yeast and higher eukaryotes were used in this study, comprising ten in vivo datasets and two in vitro datasets (Supplementary Table S1). The ten in vivo nucleosome maps included eight human datasets, one mouse dataset, and one yeast dataset. The human datasets were derived from eight cell lines: GM12878 (GSM920558), K562 (GSM920557), MCF-7 (GSE51097), H1-hESC (GSM1194220), HepG2 (GSM3718063), HeLa (GSE100401), HCT116 (GSM3889219), and IMR90 (GSM1095279). The mouse dataset was generated from mouse embryonic stem cells (mESC; GSM2183911), and the yeast dataset was obtained from cells grown to late-log phase in synthetic complete medium (GSM651368). Two in vitro nucleosome positioning datasets were also analyzed—one from humans (GSE25133) and one from yeast (GSE13622).

Nucleosome occupancy maps were obtained either directly from ENCODE or generated by aligning MNase-seq short reads to the corresponding reference genomes using Bowtie2 (Supplementary Figure S12). For example, occupancy tracks (bigWig format) for GM12878 and K562 were downloaded from ENCODE. To generate occupancy profiles for each of the four nucleosome types, every nucleosome was first assigned to Type-1, Type-2, Type-3, or Type-4 based on its DNA sequence pattern. Genome-wide nucleosome occupancy for each type was then computed from dyad counts using a center-weighted scheme 49 .

For human cell lines without pre-computed occupancy files, MNase-seq reads in the FASTQ format were mapped to the genome using Bowtie2 with the following parameters: --sensitive -I 0 -X 500 --no-discordant. Mapped reads were extended from their 5′ ends to a canonical 147-bp fragment length. Nucleosome occupancy for these datasets was calculated following our previous protocols 46 .

The mESC dataset was provided as center-weight scores, which we converted to BedGraph format before downstream processing. For yeast datasets and both in vitro nucleosome maps, occupancy profiles were generated directly from dyad counts using the same center-weighting procedure 49 .


## Classification of nucleosomes with different NPS patterns

Nucleosomal DNA sequences were classified into four types, e.g., Type-1, Type-2, Type-3, and Type-4, based on the relative abundance of WW and SS dinucleotides in minor- and major-GBS 42 . Type-1 nucleosomes exhibit the canonical WW/SS pattern. For a 147-bp NCP fragment, if (1) the total number of WW dinucleotides in the 12 minor-GBS is greater than that in the 12 major-GBS, and (2) the total number of SS dinucleotides in the 12 major-GBS is greater than that in the 12 minor-GBS, the fragment is classified as Type-1. Type-4 nucleosomes display the anti-WW/SS pattern, the inverse of Type-1. A 147-bp fragment is assigned to Type-4 if (1) WW dinucleotides are more abundant in the 12 major-GBS than in the minor-GBS, and (2) SS dinucleotides are more abundant in the 12 minor-GBS than in the major-GBS. Type-2 and Type-3 nucleosomes represent “mixed” patterns. Type-2 fragments contain more WW and more SS dinucleotides in minor-GBS than in major-GBS. Type-3 fragments contain more WW and more SS dinucleotides in major-GBS than in minor-GBS.

For any genomic region, we quantify the relative contributions of the two complementary sequence patterns using ΔNPS, defined as ΔNPS = Type 1 (%) – Type 4 (%), which reflects the balance between WW/SS and anti-WW/SS nucleosome patterns (Supplementary Figure S13).

Type-1 through Type-4 nucleosomes were identified in both in vivo (GM12878; Supplementary Table S2) and in vitro datasets (Supplementary Table S3). Overall, the number of nucleosomes detected in the in vitro dataset is approximately one-third of that detected in vivo (compare Supplementary Tables S2 and S3).


## Genome-wide protein-DNA interaction (ChIP-seq) datasets

Human and mouse ChIP-seq datasets were obtained from ENCODE. For each TF, we downloaded the processed BED files containing mapped ChIP fragments. For approximately 50% of TFs across all analyzed cell lines, the position-specific scoring matrix of the corresponding TF binding motif was obtained by matching TF names to entries in the HOCOMOCO v11, JASPAR 2022, and FactorBook motif databases.

TF binding sites were identified by scanning each ChIP fragment with the corresponding PSSM using MEME suite tools. When multiple motif hits were present within a fragment, the highest-scoring site was retained for downstream analysis. For yeast, we used the processed ChIP-seq dataset 50 in which the centers of binding motifs were already provided for each ChIP fragment.

For CTCF, unbound motifs were generated as follows. The human genome was scanned with the CTCF PSSM (CTCF_human_h11MO.meme) using FIMO with a significance threshold of 10⁻⁴. Motifs overlapping ChIP-identified binding sites were removed to obtain a set of unbound motifs. The same number of unbound motifs as their ChIP-derived counterparts were then randomly selected for further analysis.


## Classification of TF patterns using in vivo nucleosome occupancy and ΔNPS profiles

Transcription factors were classified into five categories, DIP/PEAK, DIP/DIP, PEAK/PEAK, PEAK/DIP, and AMBIGUOUS, based on the patterns of in vivo NO and ΔNPS profiles centered on TF binding motifs (position 0 in Figure 5 ).

Classification criteria were defined using the relative positions of global maxima and minima within each profile, normalized by the full dynamic range of the signal:

DIP/PEAK: The in vivo NO profile exhibits a global minimum (or a value below the lower one-third of its dynamic range), while the ΔNPS profile exhibits a global maximum (or a value above the upper one-third of its range) at the motif center.

DIP/DIP: Both the in vivo NO and ΔNPS profiles show a global minimum (or values within the lowest one-third of their respective ranges) at the motif center.

PEAK/PEAK: Both the in vivo NO and ΔNPS profiles display a global maximum (or values within the upper one-third of their ranges) at the motif center.

PEAK/DIP: The in vivo NO profile shows a global maximum (upper one-third of its range), while the ΔNPS profile shows a global minimum (lower one-third of its range) at the motif center.

AMBIGUOUS: TFs whose in vivo NO profiles exhibit no clear peak or dip, i.e., values at the motif center fall between the lower and upper one-third thresholds, were placed in the AMBIGUOUS group.

This classification scheme ensures that each TF is assigned based on robust, quantitative features of nucleosome organization and intrinsic DNA-encoded nucleosome strength around its binding motifs.


## Pattern Labeling

Some transcription factors exhibited more than one TF pattern across different cell lines. To derive a consensus label for each TF, we counted the occurrences of all patterns observed for that TF and assigned as its consensus classification the pattern(s) tied for the highest frequency. Thus, a TF could have a single consensus label (e.g., DIP/DIP) or multiple labels if ties occurred (e.g., DIP/DIP, DIP/PEAK, and AMBIGUOUS). In addition to this comprehensive dataset, we generated a stringent dataset in which TFs with more than one consensus label were removed. The stringent dataset, therefore, contains only TFs that exhibit a single, consistent pattern across all examined cell lines.


## Inter-nucleosome distance correlation function

To quantify the relative spatial organization of nucleosomes, we applied DAC and DCC functions 46 . For every pair of nucleosomal DNA fragments, we calculated the distance between their start positions. When multiple identical nucleosome sequences occurred at the same genomic location, all occurrences were counted multiplicatively—for example, if two specific sequences occurred 5 and 10 times, respectively, the DAC contribution for that pair was counted as 5 × 10 = 50.


## Funding

The research was supported by federal grants from NIH (R15GM116102 and R15GM149587) and Faculty Education And Development (FEAD) grant from College of Science at RIT.


## Availability of methods

All computational methods and pipelines are available in GitHub https://github.com/rit-cui-lab/Hidden-DNA-codes-influence-the-interaction-between-nucleosomes-and-transcription-factors/tree/main


## Disclosure of potential conflict of interest

No potential conflicts of interest were disclosed.


## Acknowledgments

The authors thank Victor B. Zhurkin for his guidance and stimulating discussions. We are grateful to the Thomas H. Gosnell School of Life Sciences and the College of Science at RIT for administrative and financial support. We also acknowledge the RIT Research Computing team for providing computational resources and support.


## Funder Information Declared