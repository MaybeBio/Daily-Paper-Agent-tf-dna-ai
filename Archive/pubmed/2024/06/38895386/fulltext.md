# An updated compendium and reevaluation of the evidence for nuclear transcription factor occupancy over the mitochondrial genome


## Abstract
  In most eukaryotes, mitochondrial organelles contain their own genome, usually circular, which is the remnant of the genome of the ancestral bacterial endosymbiont that gave rise to modern mitochondria. Mitochondrial genomes are dramatically reduced in their gene content due to the process of endosymbiotic gene transfer to the nucleus; as a result most mitochondrial proteins are encoded in the nucleus and imported into mitochondria. This includes the components of the dedicated mitochondrial transcription and replication systems and regulatory factors, which are entirely distinct from the information processing systems in the nucleus. However, since the 1990s several nuclear transcription factors have been reported to act in mitochondria, and previously we identified 8 human and 3 mouse transcription factors (TFs) with strong localized enrichment over the mitochondrial genome using ChIP-seq (Chromatin Immunoprecipitation) datasets from the second phase of the ENCODE (Encyclopedia of DNA Elements) Project Consortium. Here, we analyze the greatly expanded in the intervening decade ENCODE compendium of TF ChIP-seq datasets (a total of 6,153 ChIP experiments for 942 proteins, of which 763 are sequence-specific TFs) combined with interpretative deep learning models of TF occupancy to create a comprehensive compendium of nuclear TFs that show evidence of association with the mitochondrial genome. We find some evidence for chrM occupancy for 50 nuclear TFs and two other proteins, with bZIP TFs emerging as most likely to be playing a role in mitochondria. However, we also observe that in cases where the same TF has been assayed with multiple antibodies and ChIP protocols, evidence for its chrM occupancy is not always reproducible. In the light of these findings, we discuss the evidential criteria for establishing chrM occupancy and reevaluate the overall compendium of putative mitochondrial-acting nuclear TFs.


## Introduction
  Mitochondria contain their own genome2 (mtDNA/chrM), usually circular in topology and highly compact, especially in metazoans. The mammalian chrM is around 16–17 kbp in size and encodes for 13 proteins (all of them components of electron transport chains), 22 tRNAs and two rRNAs3,4. It has a peculiar compared to the nuclear genome organization and is replicated, transcribed and regulated by its own dedicated set of information processing factors. The 13 genes and two rRNAs are densely packed, with only one notable non-coding region (NCR) – the so called displacement or D-loop5. The D-loop is major the site of replication and transcription initiation, the latter producing long polycistronic transcripts from both strands (referred to as the H- for “heavy” and L- for “light”), and contains three promoters – a light strand (LSP) and two heavy strand (HSP1 and HSP2) promoters6,7. Transcription is carried out by the mitochondrial-specific nuclear-encoded POLRMT RNA polymerase8, with several additional nuclear genome-encoded factors – TFAM9–11, TFB1M, and TFB2M12,13 – also involved in the process of initiation14.

  The modern organization of the mitochondrial genome is the result of a combination of extreme reduction and massive endosymbiotic gene transfer (EGT). Mitochondria originated very early in eukaryote evolution as a result of the establishment of endosymbiosis with their prokaryotic ancestor15–20, which was most likely a member of the α-proteobacteria clade20–23. Subsequently, the endosymbiont lost the vast majority of its genes, either outright, or through transfer to the nuclear genome, form which then their products were imported back into the mitochondrion.

  In addition to the well-characterized bona fide mitochondrial transcription and replication factors, since the 1990s there have been reports suggesting that nuclear transcription factors may also moonlight as direct regulators of events in mitochondria24–27. These include the glucocorticoid receptor GR28–31, a 43kDa isoform of the thyroid hormone T3 receptor T3Rα1 called p4332–35, the CREB TF36–39, the tumor suppressor transcription factor p5340–43, the estrogen receptor ER44,45, STAT346, AP-1 and PPARγ247–49, as well as MEF2D in mouse50.

  However, direct in vivo evidence for occupancy of mtDNA by nuclear factors was provided only for a handful of them by these original studies (e.g. CREB37 and p5343, and it was limited to only the D-loop region. The advent of high resolution techniques for genome-wide profiling of DNA-protein interactions such as ChIP-seq (Chromatin Immunoprecipitation coupled with deep sequencing51–54) eventually enabled the direct examination of evidence for mtDNA occupancy by a large number of nuclear TFs.

  At the end of the second phase of the ENCODE Project, we and others26,27 carried out a comprehensive survey of the existing at the time ChIP-seq datasets generated by the ENCODE, mouseENCODE and modENCODE efforts55–61 in human, mouse, the worm C. elegans and the fly D. melanogaster. Eight human TFs were identified as showing strong evidence for mtDNA occupancy (JUN, JUND, CEBPB, MAX, MafF, MafK, NFE2 and RFX5), three mouse TFs (MafK, MafF and Usf2), and no fly or worm ones. Furthermore, Blumberg et al.27 demonstrated directly the localization to mitochondria of JUN and JUND in HepG2 cells using immuno-gold labeling and electron microscopy while Marinov et al.26 showed MAFK localizing to mitochondria using immunocytochemical staining. Examination of available ChIP-seq data for TFs previously proposed to act in mitochondria (GR, ERα, CREB, STAT3, p53) found no putative occupancy sites.

  However, these studies did not reveal any obvious mechanisms through which these nuclear TFs might act to regulate mitochondrial transcription, as all the identified ChIP-seq peaks are away from the D-loop in the middle of the transcriptional units. The D-loop itself shows up as “enriched” in practically all ChIP-seq datasets, but this is almost certainly an experimental artifact as the ChIP signal there does not show the characteristics of proper occupancy sites. Thus the question about the potential role of nuclear TFs in mitochondria remains open and unresolved24,25.

  With the completion of the third62 and fourth phases of the ENCODE project, a vastly expanded collection of ChIP-seq datasets has now become available, encompassing an order-of-magnitude larger sampling of the human TF repertoire. Furthermore, many TFs have now been assayed using multiple different reagents or using endogenous tagging, thus potentially providing distinct lines of evidence for mtDNA occupancy, and powerful deep learning-based tools for analyzing the sequence patterns driving TF occupancy and predicting it from sequence have been developed63. In this study, we take advantage of these resources, survey the expanded ENCODE collection, and identify 50 nuclear TFs plus two other chromatin proteins exhibiting more or less robustly supported peaks over chrM. On the other hand, the picture revealed by the expanded collection is more complicated than previously perceived as in many cases occupancy profiles are not replicated in all cases where multiple immune reagents have been used to assay the same TF. We discuss the currently most reliable set of mtDNA-associated nuclear TFs, as well as the evidential criteria for establishing chrM occupancy using ChIP and other experimental methods.


## Results

### Evaluating the evidence for mitochondrial occupancy of nuclear TFs in the expanded ENCODE ChIP-seq collection
  According to the latest census of human transcription factors1, the human genome encodes 1,742 sequence-specific TFs, belonging to ~60 different families defined by their DNA binding domains (DBDs).

  Our previous analysis of the dataset collection generated as part of the second phase of the ENCODE Project encompassed a total of 151 transcription factors, which represents less than 10% of the total. After the fourth phase of ENCODE, the number of available datasets is now greatly expanded and covers ~44% of the known TFs.

  In order to evaluate putative physical associations of nuclear TFs with the mitochondrial genome (and also reevaluate previous observations), we examined 6,153 ChIP-seq datasets for 942 targets, of which 763 are sequence-specific TFs1 (Figure 1A). The additional 179 are non-sequence specific chromatin proteins, such as histone modifying enzymes and chromatin remodellers.

  The most recent ENCODE collection is also not merely a quantitative expansion. Multiple TFs have been assayed with different antibodies, which is extremely valuable because, especially when the antibodies are polyclonal, the possibility that mtDNA ChIP-seq peaks are the result of non-specific pull down can never be excluded (although that would still mean that some previously not known to do so protein is specifically occupying those regions of the mitochondrial genome). Many of the newly available TFs, but also some that have been mapped previously, have now been assayed using endogenous tagging with FLAG, GFP or HA tags, most commonly using CRISPR epitope tagging (CETCH-seq64) and site-specific recombination65. We note that in CETCH-eq tagging is carried out at the stop codon of the gene, i.e. at its C-terminus, thus it is unlikely that it would affect import into mitochondria, which is classically mediated by N-terminal targeting sequences66,67; however, that can nevertheless not be completely excluded as a possibility.

  We updated our pipeline for analyzing mitochondrial occupancy in several ways in order to allow for more comprehensive characterization of the current TF compendium.

  First, we previously mapped reads against a joint nuclear and mitochondrial genomic index, and excluded all reads mapping to multiple locations within that combined genomic space. A substantial portion of the human chrM in the context of the hg38 assembly is affected by such mappability limitations (Supplementary Figure 1). However, because of the very high copy number of mitochondrial genomes in a given cell relative to the diploid nuclear genome68, peaks observed over chrM are nearly always much stronger than even the very top nuclear ChIP-seq peaks, as previously demonstrated26. Furthermore, other hallmarks of TF occupancy, such as chromatin accessibility peaks and high levels of histone marks associated with active regulatory elements, which would be expected if chrM peaks arose from mitochondrial sequences that have been inserted in the nuclear genome (so called NUMTs69), are not seen over the peaks observed over the mitochondrial genome. This makes it highly unlikely that they arise from nuclear TF occupancy over NUMTs. For these reasons, we now evaluate putative mitochondrial occupancy based on read alignments generated entirely in mitochondrial space.

  Second, in our past work we sought corroborating evidence for the observed ChIP-seq profiles in the presence or absence of the cognate sequence recognition motifs for each TF. However, these motifs are often very short and degenerate, and thus only a small fraction of them is actually occupied in cells. In this work, we leverage the power of interpretative deep learning models to generate more reliable and specific predictions of TF occupancy profiles over chrM, which we then compare to experimental measurements. We use the state-of-the-art BPNet70 profile models, which take as input genomic sequence and the forward- and reversestrand ChIP-seq profiles, and then learn to predict these profiles as a function of genomic sequence. As part of the overall ENCODE effort, we have trained such models over the nuclear genome for all TFs for which data is available, and we used these models to predict chrM ChIP-seq profiles (see Methods for details).

  Figure 1B shows the observed chrM profiles for all 6,153 datasets. As discussed in our previous work26, the D-loop region appears as strongly “enriched” in nearly all ChIP datasets; this is certainly an artifact in almost all cases because the observed forward- and reverse-strand profiles do not exhibit the expected from true occupancy asymmetry around a punctate binding site71–74. It is most likely that the unique triple-stranded structure of the D-loop results in preferential enrichment in sequencing libraries. We also observe a few regions of weakly elevated signal in the middle of chrM, which are also present in the majority of datasets, and are also unlikely to represent true occupancy events.

  Disregarding these signals, we find some evidence for chrM occupancy for 50 sequence-specific TFs, which we discuss in detail below. In addition, two of the 179 non-sequence specific chromatin proteins also showed evidence for putative association with mtDNA.


### bZIP TFs
  The TF family with the largest and most notable set of members with strong chrM peaks is the bZIP (Basic Leucine Zipper) domain-containing proteins. In humans, 72 such TFs are annotated in the genome, and for 39 of them there is ENCODE ChIP-seq data.

  Remarkably, nearly half of them – 19/39 – exhibit evidence fo mtDNA occupancy (Figures 2–6A–C and Supplementary Figures 2–22). These TFs are ATF2, ATF3, ATF4, ATF7, CREB1, FOS, FOSL1, FOSL2, CEBPB, CEBPG, JUN, JUND, MAFF, MAFG, MAFK, NFE2, NFE2L1, NFE2L2, and NRL.

  Figure 2A shows the chrM ChIP-seq profile for the ATF2 TF in the K562 cell line, revealing a strong peak, with the classic strand asymmetry features of true sequence-specific TF occupancy, in the region around the MT-ND3 and MT-ND4L genes and the MT-TR tRNA gene. The BPNet-predicted profile corroborates the existence of such a peak, although BPNet also predicts high ChIP-seq signal in several other locations, which is not observed in the actual data (Supplementary Figure 2B). The same peak is observed in HepG2 cells using the same antibody (Supplementary Figure 2E), and in site-recombination-tagged experiment in the HEK293 cell line (Supplementary Figure 2D). It is not observed in H1-hESC using a different antibody (Supplementary Figure 2C), and also in a CRISPR-mediated endogenous tagging experiment in HepG2 cells (Supplementary Figure 2F). Thus for ATF2 we see evidence for occupancy using two different reagents (an α-ATF2 antibody and GFP-tagging), but not with another α-ATF2 antibody and FLAG-tagging.

  Figure 2B shows the chrM ChIP-seq profile for the ATF3 TF in the K562 cell line. In this case, at least four strong peaks are observed – the same one around MT-ND3 /MT-ND4L seen for ATF2, but also one over MT-ATP6, one over MT-ND4, and another over MT-CYB. All these peaks are corroborated by BPNet predictions (Supplementary Figure 3B), although here too BPNet predicts additional occupancy peaks. However, none of the experiments in other cell lines – H1-hESC, HCT116, HepG2, A549, GM12878, liver, and K562 again – carried out with a different antibody exhibit these peaks (Supplementary Figure 3C–I), and neither does CRISPR-mediated FLAG-tagging (Supplementary Figure 4J).

  Figure 2C shows the chrM ChIP-seq profile for the ATF4 TF in the K562 cell line. In this case we observe a single strong peak, at the same location as the ATF3 peak over the MT-CYB gene. Unfortunately, we were not able to train a good model for this TF, thus we do not have BPNet predictions over chrM for it (Supplementary Figure 4B). This peak is not seen in a CRISPR-mediated FLAG-tagging experiment in HepG2 cells (Supplementary Figure 4C).

  Figure 2D shows the chrM ChIP-seq profile for the ATF7 TF in the MCF-7 cell line. Its profile over chrM is similar to that of ATF3 (Figure 2B), with four peaks. BPNet models corroborate the strong peak over MT-ND3 /MT-ND4L, but are less concordant elsewhere in the genome. These peaks are also seen in GM12878 and K562 ChIP-seq experiments generated with the same antibody (Supplementary Figure 5C–D), but not in HepG2 ChIP-seq carried out with a different antibody (Supplementary Figure 5E).

  Figure 3A shows the chrM ChIP-seq profile for the CREB1 TF in the HepG2 cell line. CREB1 is notable for having been previously proposed to localize to mitochondria and play a functional role there37,39, and specifically to bind to the D-loop38. Just as in our previous effort26, we see no evidence that is unlikely to be an artifact for D-loop occupancy, but we observe a strong peak over the MT-ND1 gene, another one over MT-CO3 and several weaker others elsewhere in the genome. These match BPNet predictions qualitatively, but the magnitudes of observed and predicted signals differ significantly (Supplementary Figure 6B). The putative occupancy profiles are replicated in MCF-7 cells using the same antibody (Supplementary Figure 6D), in CRISPR FLAG-tagged HepG2 and GM23338 cells (Supplementary Figure 6C and E), and also in K562 cells using a different antibody (Supplementary Figure 6F). However, the latter antibody was also used in datasets in GM12878, H1-hESC and Ishikawa cells (Supplementary Figure 6G–I) resulting in a flat profile over chrM, as is the case with a CETCH-seq experiment in K562 cells (Supplementary Figure 6J).

  Figure 3B shows the chrM ChIP-seq profile for the FOS TF in the MCF-7 cell line. Two peaks are observed – a strong one over the MT-ATP6 gene and a weaker one at the same location as the ATF2, ATF3 and ATF7 peaks over MT-ND3 /MT-ND4L. Both are matched by BPNet predictions while several other BPNet-predicted peaks are not observed in the data (Supplementary Figure 7B). The pattern is replicated in K562 cells using the same antibody (Supplementary Figure 7C), but not in IMR90, endothelial cells of the umbilical vein, GM12878 or HeLaS3, all using the same antibody (Supplementary Figure 7D–G).

  Figure 3C shows the chrM ChIP-seq profile for the FOSL1 TF in the K562 cell line; this experiment uses GFP-tagged FOSL1. The same two peaks as for FOS are observed, but neither is particularly strong. BPNet predicts a large number of peaks all over mtDNA, which are not seen in the data (Supplementary Figure 8B). These peaks are not replicated by K562 CETCH-seq, HepG2 CETCH-seq, and ChIP-seq using an α-FOSL1 antibody in H1-hESC and HCT116 (Supplementary Figure 8C–F).

  Figure 3D shows the chrM ChIP-seq profile for the FOSL2 TF in the A549 cell line, using CRISPR-tagged cells. Again, the same two peaks are observed as for FOS and FOSL1. These are also predicted by BPNet (Supplementary Figure 9B), but the strongest BPNet prediction – over MT-CYB is not observed in the data. However, other experiments using two different antibodies in A549, MCF-7, HepG2 and SK-N-SH as well as CETCH-seq in MCF-7 and HepG2 do not shows these peaks (Supplementary Figure 9C–J).

  Figure 4A shows the chrM ChIP-seq profile for the CEBPB TF in the K562 cell line, using CRISPR-tagged cells. A strong peak is observed over the MT-ND4 gene, and a weaker one over MT-CO2, as well as a few other weak peaks. These are corroborated by BPNet (Supplementary Figure 10B); in fact BPNet predicts two distinct binding sites over MT-ND4 and two peaks associated with strand asymmetry are also seen in the CETCH-seq data. BPNet also predicts numerous other peaks that are not observed experimentally. A large number of different additional experiments are available for CEBPB (Supplementary Figure 10C–J and Supplementary Figure 11), using two different antibody lots. The observed putative mtDNA occupancy is replicated in IMR90 (Supplementary Figure 10D), HeLaS3 (Supplementary Figure 10F), HepG2 (Supplementary Figure 10J), A549 (Supplementary Figure 11E), but not in other experiments for HepG2 and A549 or the other cell lines – MCF-7, HCT116, Ishikawa, H1-hESC, GM12878 and non-tagged K562 – that have been assayed.

  Figure 4B shows the chrM ChIP-seq profile for the CEBPG TF in the K562 cell line, using CRISPR-tagged cells. A similar pattern to CEBPB is observed, but with a stronger peak over the MT-CYB gene. BPNet predictions match the observed profile (Supplementary Figure 12B). However, CRISRP-tagged MCF-7 and HepG2 cells do not show these peaks (Supplementary Figure 12C–D).

  Figure 4C shows the chrM ChIP-seq profile for the JUN TF in the HepG2 cell line. Two strong peaks are observed for JUN – one over the same MT-ND3 MT-ND4L region as seen for many other bZIP factors, and another over ND4. A weaker peak is seen over MT-ATP6. BPNet predicts all these peaks, as well as many others (Supplementary Figure 13B). These peaks are also observed in endothelial cells of the umbilical veins (Supplementary Figure 13C), where it is to be noted that the MT-ATP6 peak is stronger than the MT-ND4L one, but not in any of the other cell lines assayed-MCF-7, HeLa-S3, A549, K562, H1-hESC and in a HepG2 CETCH-seq sample (Supplementary Figure 13D–I). All of these ChIP-seq experiments were carried out with the same antibody. JUN was one of the factors whose presence in mitochondria was conclusively confirmed through immunogold electron microscopy previously27, thus the discrepancy between HepG2 ChIP-seq and CETCH-seq and it being observed only in two seemingly unrelated cell lines and not in any of the others are particularly puzzling observations.

  Figure 4D shows the chrM ChIP-seq profile for the JUND TF in the K562 cell line. The same three peaks are observed as for JUN, and these are also corroborated by BPNet predictions (Supplementary Figure 14B). Here too we observed discordance in the available datasets as these peaks are also seen in HepG2 (Supplementary Figure 14D) and SK-N-SH (Supplementary Figure 14H) cells, but not in any of the other ENCODE experiments for JUND-HeLaS3, GM12878, HCT116, H1-hESC, liver, MCF-7, T47D, A549, and most puzzling, additional datasets in K562, HepG2 and SK-N-SH (Supplementary Figure 14C,EG,I and Supplementary Figure 15). All of these experiments were carried out with the same Santa Cruz Biotech sc-74 antibody, except for the K562 experiments, both of which used GFP-tagged JUND. however, this antibody is polyclonal and there is no information available whether the same lot was used. It is possible the discrepancy arises as a result of lot differences; the other possibility is that the experimental protocols used are not the same as the discordant samples arise from two different production labs. As is the case with JUN, JUND’s presence in mitochondria was previously verified by immunogold electron microscopy in HepG2 cells27.

  Figure 5A shows the chrM ChIP-seq profile for the MAFF TF in the K562 cell line. Several peaks are observed – over the MT-CO1 and MT-ND5 genes as well as over the tRNA cluster between MT-ND4 and MT-ND5. These are also predicted by BPNet (Supplementary Figure 16B) together with multiple other peaks not observed in the ChIP data. The first two peaks are also observed in HepG2 and HeLa-S3 cells (all experiments carried out with the same antibody) but the latter is not.

  Figure 5B shows the chrM CETCH-seq profile for the MAFG TF in the K562 cell line. The three peaks observed for MAFF are also present in the MAFG profile, but in addition peaks are present over the MT-CYB and MT-ATP6 genes as well as a weaker one over the 16S rRNA. These peaks are corroborated by BPNet predictions (Supplementary Figure 17B), but are not seen in a HepG2 CETCH-seq experiment (Supplementary Figure 17C).

  Figure 5C shows the chrM ChIP-seq profile for the MAFK TF in the A549 cell line. The same peaks are observed as those for MAFF, and they are corroborated by BPNet predictions (Supplementary Figure 18B). They are also observed in GM12878, IMR-90, HeLa-S3, K562, MCF7 and HepG2 cells, but not in H1-hESC cells (Supplementary Figure 18C–I). Of note, they are seen in datasets generated with two different antibodies, and MAFK was previously shown to localize to mitochondria using immunocytochemical staining.

  Figure 5D shows the chrM ChIP-seq profile for the NFE TF in the K562 cell line. Five peaks are observed – over the 16S rRNA gene, over MT-ATP6, over MT-ND3, over the tRNA cluster between MT-ND4 and MT-ND5, and over MT-CYB. These are all sites where peaks are seen also for other bZIP factors. Most of them are predicted by BPNet (Supplementary Figure 19B), and they also seen in K562 CETCH-seq experiment (Supplementary Figure 19C). On the other hand, CETCH-seq in HepG2 (Supplementary Figure 19D) and ChIP-seq in GM12878 generated using a different antibody (Supplementary Figure 19E) show no peaks.

  Figure 6A shows the chrM ChIP-seq profile for the NFE2L1 TF in the K562 cell line. Three strong peaks are observed in this case – over the 16S rRNA gene, over MTATP6, and over the tRNA cluster between MT-ND4 and MT-ND5. BPNet predicts the latter two but not the one over the 16S rRNA (Supplementary Figure 20B). A HepG2 CETCH-seq experiment does not exhibit the same pattern (Supplementary Figure 20C).

  Figure 6B shows the chrM ChIP-seq profile for the NFE2L2 TF in the K562 cell line. It is very similar to what is observed for NFE2L1, and in this case too BPNet does not predict a 16S rRNA peak (Supplementary Figure 21B). These peaks are also seen in IMR-90 cells (Supplementary Figure 21C) and weakly in A549 and HeLaS3 cells (Figure 21D–E), using the same antibody for all experiments.

  Figure 6C shows the chrM ChIP-seq profile for the NRL TF in a HepG2 CETCH-seq experiment. In this case, multiple, and often potentially complex multisummit peaks are observed all over the genome. They generally match BPNet predictions (Supplementary Figure 22B).


### bHLH TFs
  The second major group of TFs exhibiting evidence for mtDNA occupancy are the basic helix–loop–helix (bHLH) transcription factors. Of 122 bHLH factors annotated in the genome, ChIP-seq data is available for 36, of which peaks over chrM are observed for four – BHLHE40, MAX, MITF, and SREBF1.

  Figure 6D shows the chrM ChIP-seq profile for the BHLHE40 TF in the K562 cell line. Two peaks are observed-over the MT-ATP6 gene and over NT-ND3 /MT-DN4L. However, the observed profile does not match the BPNet predicted one (Supplementary Figure 23B), and is also not seen in any other cell line (Supplementary Figure 23C–G). In the GM12878 cell line a different peak is observed over the MT-ND5 gene (Supplementary Figure 23D); the same antibody was used for both the IMR90 and GM12878 experiments, but a different antibody was used in A549 and HepG2 cells.

  Figure 7A shows the chrM ChIP-seq profile for the MAX TF in the K562 cell line. Strong peaks are observed over the 16S rRNA gene and over MT-CO3, which are also predicted by BPNet (Supplementary Figure 24B) together with a number of other peaks not seen in the data. Many different additional experiments are available for MAX (Supplementary Figures 24C–J and 25) – all generated with the same antibody, but including experiments from different production groups. These peaks are also seen in endothelial cells of umbilical vein (Supplementary Figure 24F) and H1hESC (Supplementary Figure 24J), generated by two different productions groups, but not in the rest of the experiments – A549, HepG2 (ChIP and CETCH-seq), GM12878, HCT116, HeLaS3, Ishikawa, liver, MCF-7 and SK-N-SH.

  Figure 7B shows the chrM ChIP-seq profile for the MITF TF in the K562 cell line. Peaks are observed over the MT-ND2 gene and on the boundary between MT-ATP6 and MT-CO3. However, these do not match the predicted BPNet profile (Supplementary Figure 21B).

  Figure 7C shows the chrM ChIP-seq profile for the SREBF1 TF in the A549 cell line. In this case, two potential peaks are seen at the very beginning of the 12S rRNA gene and another one over the MT-C03 gene. These are predicted by BPNet (Supplementary Figure 27B), together with many other peaks not observed in the data.


### RFX TFs
  The human genome encodes eight RFX TFs, of which ChIP-seq data now exists for four. Two of these shows evidence for mtDNA occupancy – RFX1 and RFX5.

  Figure 7D shows the chrM ChIP-seq profile for the RFX1 TF in the MCF-7 cell line. One peak is observed – over the MT-CYB gene – where multiple peaks summits are also predicted by BPNet (Supplementary Figure 28B). This profile is also observed in K562 cells (Supplementary Figure 28C), but not in HepG2 (Supplementary Figure 28D).

  Figure 8A shows the chrM ChIP-seq profile for the RFX5 TF in the K562 cell line. Three areas of elevated signal are observed – over MT-CO2, in the beginning of ND5, and in the MD-ND3 /MD-ND4L region. BPNet predicts multiple strong peaks (Supplementary Figure 29B), two of which match the MT-CO2 and MD-ND3 /MD-ND4L peaks, but not the ND5 one. This pattern is also seen in IMR90 cells (Supplementary Figure 29C). In HepG2 cells, a different profile is observed – a peak over the MT-ND1 gene (Supplementary Figure 29D). No peaks are seen in the available other experiments – SK-N-SH, GM12878, H1-hESC, A549, HeLa-S3, MCF-7 (Supplementary Figure 29E–J), all of which were generated using the same antibody.


### Forkhead TFs
  A total of 50 forkhead TFs are encoded in the human genome, for which 15 have been assayed by ENCODE. Two of them – FOXA1 and FOXA2 – show putative evidence for mtDNA occupancy.

  Figure 8B shows the chrM ChIP-seq profile for the FOXA1 TF in liver. A peak is observed over the tRNA cluster between MT-ND4 and MT-ND5, which is also predicted by BPNet (Supplementary Figure 30B), together with many other peaks not observed in the data. However, HepG2 ChIP-seq carried out with the same antibody does not show the same peak (Supplementary Figure 30D), and neither does HepG2 CETCH-seq (Figure 30E) nor do ChIP-seq datasets for A549, MCF-7 and K562 cells generated using two other different antibodies (Supplementary Figure 30C–D and F–H).

  Figure 8C shows the chrM ChIP-seq profile for the FOXA2 TF in liver. The same peak is observed as for FOXA1, but it is not strongly predicted by BPNet (Supplementary Figure 31B). As with FOXA1, it is not seen in cell line data – A549 ChIP-seq, HepG2 CETCH-seq and HepG2 ChIP-seq (Supplementary Figure 31C–E).


### C2H2 zinc finger TFs
  The largest TF family in mammals is the C2H2 zinc finger factors. The human genome encodes 774 of these, of which 419 have been now assayed by ENCODE, and 12 show some evidence for mtDNA occupancy – DZIP1, HIVEP1, ZNF225, ZNF274, ZNF350, ZNF598, ZNF768, ZNF839, ZNF891, ZNF263, ZNF280B, ZNF316. Most of these experiments have been carried out using endogenous epitope tagging as specific antibodies for most ZNFs are not available.

  Figure 8D shows the chrM ChIP-seq profile for the ZNF316 TF in the K562 cell line. Two strong peaks are observed – over the MT-CO1 and MT-ND5 genes, and several weaker ones elsewhere around chrM. These are predicted by BPNet models (Figure 32B). Howevr, a second K562 experiment, carried out by the same production group but with a different antibody does not exhibit any peaks over chrM.

  The DZIP1, HIVEP1, ZNF225, ZNF263, ZNF274, ZNF280B, ZNF350, ZNF598, ZNF768, ZNF839, ZNF891, all display a similar pattern over chrM, in, respectively, HepG2 CETCH-seq (Figure 9A), HepG2 CETCH-seq (Figure 9B), HepG2 CETCH-seq (Figure 9C), K562-ChIP-seq (Figure 9D), HepG2 CETCH-seq (Figure 10A), HepG2 CETCH-seq (Figure 10B), HepG2 CETCH-seq (Figure 10C), HepG2 ChIP-seq (Figure 10D), HepG2 CETCH-seq (Figure 11A), HepG2 CETCH-seq (Figure 11B), and HepG2 CETCH-seq Figure 11C). Nine out of eleven of these datasets are the result of endogenous epitope tagging experiments in HepG2 cells, but two are conventional ChIP-seq using TF-specific antibodies. They all display multiple peaks all over the length of the mitochondrial genome, and they are all generally matching the predicted BPNet profiles (Supplementary Figure 33B; Supplementary Figure 34B; Supplementary Figure 35B; Supplementary Figure 36B; Supplementary Figure 37B; Supplementary Figure 38B; Supplementary Figure 39B; Supplementary Figure 40B; Supplementary Figure 41B; Supplementary Figure 42B; Supplementary Figure 43B).

  For most of these TFs, these are the only datasets available, but in the cases where additional experiments exist, the observed peaks are not replicated – K562 CETCH-seq for HIVEP1 (Supplementary Figure 34C); HEK293 ChIP-seq (Supplementary Figure 35C) and HepG2 CETCH-seq (Supplementary Figure 35D) for ZNF263; HepG2, K562, H1-hESC, HeLa-S3, HCT116, HEK293, and GM12878 ChIP-seq and HEK293 CETCH-seq for ZNF274 (Supplementary Figure 35C–J); HEK293 ChIP-seq for ZNF350 (Supplementary Figure 39C); HEK293 ChIP-seq for ZNF768 (Supplementary Figure 41C).


### THAP finger TFs
  The human genome encodes 12 THAP finger TFs, for five of which datasets exist in the ENCODE collection.

  Figure 11A shows the chrM CETCH-seq profile for the THAP9 TF in the HepG2 cell line. This factor displays largely the same profile as most of the C2H2 zinc finger TFs discussed above, and it too matches BPNet predictions (Supplementary Figure 44B).


### Rel TFs
  Of the ten Rel TFs in the human genome, six have been assayed by ENCODE.

  Figure 12A shows the chrM CETCH-seq profile for the NFKB2 TF in the HepG2 cell line. This dataset too exhibits a similar pattern as THAP9 and most of the C2H2 zinc finger TFs, matched by BPNet predictions (Supplementary Figure 45B).


### Nuclear receptors
  Of the 46 human nuclear receptors, 26 have been assayed by ENCODE.

  Figure 12B shows the chrM CETCH-seq profile for the RXRA TF in the HepG2 cell line. This is another case of the same pattern observed for most of the C2H2 zinc finger TFs, THAP9 and NFKB2, and it too largely matches BP-Net predictions (Supplementary Figure 46B). This pattern is not replicated in any of the ChIP-seq datasets available for RXRA in HepG2, GM12878, H1-hESC, liver and SK-N-SH, generated using α-RXRA antibodies.


### Runt TFs
  Three RUNT TFs are encoded in the human genome. Two of these have been assayed by ENCODE.

  Figure 12C shows the chrM ChIP-seq profile for the RUNX3 TF in the GM12878 cell line. One strong peak is observed over the MT-ND5 gene, two weaker ones over MT-CO1, as well as several other loci of slight enrichment. We were not able to train a high quality BPNet model for this TF (Supplementary Figure 47B).


### HSF TFs
  ENCODE has assayed three out of eight HSF TFs.

  Figure 12D shows the chrM ChIP-seq profile for the HSF1 TF in HepG2 cells treated with forskolin + 1mM pyruvate. One peak is observed over the MT-CO2 gene, but it is not corroborated by BPNet predictions (Supplementary Figure 48B) and is not replicated in HSF1 ChIP-seq datasets in GM12878 and MCF-7 cells (Figure 48C–D).


### Homeodomain TFs
  Homeodomain transcription factors are the second largest class of TFs in mammalian genomes. The human genome encodes 202 of them, plus seven CUT Homeodomain TFs, 16 POU Homeodomain TFs, and nine Paired-box Homeodomain TFs (treated separately in the classification followed here1). We observe evidence for mtDNA occupancy for two Homeodomain TFs and one CUT Homeodomain TF.

  Figure 13A shows the chrM ChIP-seq profile for the MEIS2 TF in the K562 cell line. One moderate peak is observed over the MT-ND1 gene. BPNet predicts elevated signal over that region, but also over many other sites in the mitochondrial genome (Supplementary Figure 49B).

  Figure 13B shows the chrM ChIP-seq profile for the PKNOX1 TF in the K562 cell line. The same peak as for MEIS2 is seen, and in this case too BPNet predictions do not match well the observed profile (Figure 50B). The peak is replicated in HEK293T cells (Supplementary Figure 50D), but not in GM12878 (Supplementary Figure 50C) or MCF-7 (Supplementary Figure 50E).

  Figure 13C shows the chrM ChIP-seq profile for the CUX1 TF in the MCF-7 cell line. Two strong peaks are observed – over the 12S rRNA gene and over MT-ND2, as well as a weaker one over MT-ATP6. BPNet predictions include these peaks but also many others, and their relative predicted and observed strengths do not match well (Supplementary Figure 51B). These patterns are replicated in K562 CETCH-seq experiment (Supplementary Figure 51D), but not in K562 ChIP-seq and GM12878 experiments carried out with the same α-CUX1 antibody (Supplementary Figure 51C,E).


### E2F TFs
  The E2F family consists of 11 TFs in the human genome, for which data is available for ten.

  Figure 13D shows the chrM ChIP-seq profile for the E2F1 TF in the K562 cell line. A strong peak is observed over the MT-ND1 gene, as well as elevated signal around several other loci in the mitochondrial genome. However, this does not match the BPNet-predicted profile (Supplementary Figure 52B), and it is also not replicated in any of the other available datasets – ChIP-seq in K562 cells generated using a different α-E2F1 antibody (Supplementary Figure 52C), ChIP-seq in MCF-7 cells carried out using HA-tagged E2F1 (Supplementary Figure 52D), ChIP-seq in HeLaS3 cells carried out using a third α-E2F1 antibody (Supplementary Figure 52E), and CETCH-seq experiments in HepG2 and HeLa-S3 cells (Supplementary Figure 52F–G).


### ARID/BRIGHT TFs
  Eight out of 15 ARID/BRIGHT TFs in the human genome have been assayed by ENCODE.

  Figure 14A shows the chrM ChIP-seq profile for the ARID1B TF in the K562 cell line. A single peak is observed over the MT-ATP6 gene, but we do not have BPNet support for it (Supplementary Figure 53B), and there are no other datasets available for orthogonal evidence.


### AP-2 TFs
  One of the five AP-2 TFs in the human genome has been assayed by ENCODE.

  Figure 14B shows the chrM profile for the TFAP2C TF in a CETCH-seq experiment in the MCF-7 cell line. Two very strong peaks are observed – over the MT-ND1 and MT-ND4 genes. In this case we were not able to train a good BPNet model, and there are no other experiments available for TFAP2C.


### Other proteins
  We did not find any putative chrM peaks for TFs in the following families (Figure 15): AT hook (8/16 assayed), CBF/NF-Y (1/1), CENPB (2/11), CG-1 (1/2), CSD (2/8), CSL (1/2), CxxC (1/11), EBF1 (1/4), Ets (17/28), GATA (7/11), GTF2I-like (1/4), Grainyhead (2/6), HMG/Sox (18/58), IRF (6/9), MADF (1/3), MADS box (1/6), MBD (4/11), Myb/SANT (16/42), NFX (1/2), Ndt80/PhoG (1/2), Pipsqueak (2/2), p53 (1/3), SAND (5/10), SMAD (10/12), STAT (6/7), T-box (5/17), TBP (2/3), TCR/CxC (1/2), TEA (4/5), BED ZF (3/11), CCCH ZF (8/43), and MYM-type ZF (2/16).

  We observed notable chrM peaks for two other chromatin proteins – C11orf30/EMSY and ATM.

  Figure 14C shows the chrM ChIP-seq profile for the C11orf30/EMSY protein in the K562 cell line. Two very strong peaks are observed – over the MT-CO1 and MT-ND5 genes. We trained a BPNet model which predicts peaks over a large set of loci, but does include these two peaks (Supplementary Figure 48B). No other datasets are available as orthogonal evidence.

  Figure 14D shows the chrM ChIP-seq profile for the ATM TF in the HepG2 cell line. A peak is observed over the MT-CO2 gene, but the existing BPNet model does not make high-quality predictions over chrM (Supplementary Figure 56B)


## Discussion
  In this work we review the current evidence for mtDNA occupancy by nuclear transcription factors using the vastly expanded collection of ChIP-seq datasets generated by the most recent phases of the ENCODE Project Consortium together with interpretable deep neural network modeling of TF occupancy, continuing from our previous work on the subject a decade ago26,27. Some evidence for physical association with mtDNA is found for 50 sequence-specific TFs and two other proteins. However, the interpretation of these observations is less straightforward than it was in the past.

  The updated ENCODE collection is qualitatively distinct relative to the much smaller second-phase ENCODE set in that now many TFs have been assayed multiple times, in many different cell lines, and using different combinations of distinct antibodies and/or endogenous epitope tagging. This potentially provides stronger evidence than the more limited data previously available as it can mitigate against the several major concerns that have always existed about observed ChIP-seq peaks over chrM. These are:

  The expanded ENCODE collection provides numerous examples of lack of complete concordance between the different available experiments for each TF. It is thus reasonable to provisionally consider TFs to be likely in vivo mtDNA binders if there are at least two orthogonal lines of evidence for their chrM occupancy, i.e. ChIP-seq peaks in datasets generated with at least two different antibodies or an antibody and endogenous tagging, or what is the ideal gold evidential standard – a combination of peaks observed in ChIP-seq datasets and demonstration of localization to mitochondria using immunogold electron microscopy. The latter is however not entirely possible for e.g. many of the C2H2 ZFs, for which epitope tagging was used for ChIP-seq due to the unavailability of immune reagents; in such cases aberrant localization to mitochondria as a result of the tagging cannot be entirely excluded.

  With these considerations in mind, we can summarize the available evidence for mtDNA occupancy as follows.

  What immediately stands out in the current data is the large number of bZIP factors for which chrM peaks are observed – nearly half (19/39) of the ones that have been assayed. This is unlikely to be an artifact as numerous lines of evidence converge onto bZIP factors playing a role in mitochondria, even though the evidence for each individual TF can be contradictory. For example, ATF2 chrM peaks are seen with multiple antibodies, but not with all or in all epitope tagging experiments; ATF7 peaks are seen in multiple cell lines, but only with one of two antibodies used; FOSL1, FOSL2 and NFE2L1 peaks are not replicated beyond a single dataset, and CEBPG peaks are observed in one epitope-tagged cell line but not in others. On the other hand, CREB1 and MAFK chrM peaks are replicated with multiple different antibodies and NFE peaks in both ChIP-seq and CETCH-seq (although not in all cell lines).

  The bZIP factors also include the three TFs for which direct microscopy evidence exists for localization to mitochondria – MAFK, JUN and JUND.

  They also exhibit collocalization to a few distinct sites in the mitochondrial genome, which lends mutual support to each other’s mtDNA occupancy because many bZIP factors form heterodimers in the form of the AP-1 transcription factor75. Thus, they would be expected to co-occupy the same sites. AP-1’s nuclear functions also happen to be generally associated with the regulation of growth and proliferation; these are processes in which mitochondria play important roles. While it is currently not clear how AP-1 might be playing a regulatory role in mitochondria mechanistically, this is an obvious functional connection to consider.

  On the other extreme of reliability of the available evidence lies the set of C2H2 ZF TFs (DZIP1, HIVEP1, ZNF225, ZNF263, ZNF274, ZNF280B, ZNF350, ZNF598, ZNF768, ZNF839, ZNF891) together with THAP9, NFKB2 and RXRA. All of these datasets exhibit almost the same ChIP-seq profile, are almost all derived from epitope tagging experiments, and they also show elevated signal over nearly all predicted occupancy sites. These peaks are not replicated by any antibody ChIP-seq datasets where available, and thus they are most likely an artifact, although it is not clear why only these CETCH-seq experiments would generate such an artifact and not the hundreds others.

  Evidence is also currently weak for mtDNA occupancy by BHLHE40, MITF, FOXA1, FOXA2, HSF1, E2F1, due to lack of replication and/or lack of support from BPNet predictions.

  For factors such as MAX, RFX1, RFX5 and PKNOX1 ChIP-seq peaks are seen in multiple cell lines, although not in others. They are provisionally more likely to be truly occupying mtDNA than not.

  Yet other factors – SREBF1, RFX1, RUNX3, CUX1, ARID1B, TFAP2C, C11orf30/EMSY and ATM – have only been assayed in a single cell line, and thus the available evidence is simply too limited to say much more about them.

  Nevertheless, some broad trends emerge. While the bZIP factors appear to be particularly enriched for potential mitochondrial moonlighting, other large and important TF families show very little such evidence. Even if the 12 C2H2 ZFs turn out not to be the result of an experimental artifact, they would represent only a small fraction (12/419) of the huge diversity of such TFs. Other large TF families that, although not exhaustively sampled, don’t seem to bind to chrM include HMG/Sox, nuclear receptors, Homeodomain TFs, and Myb/SANT. A few of the smaller TF families have also been almost exhaustively sampled and they too show no evidence for mitochondrial localization. These include GATA, IRF, SMAD, STAT, and TEA.

  In summary, our work represents the most comprehensive catalog of human TFs potentially occupying mitochondrial DNA compiled so far, and provides the foundation for the subsequent direct validation and characterization of the possible functions of these factors in mitochondrial gene regulation.


## Methods

### ChIP-seq data processing
  Raw sequencing reads for transcription factor ChIP-seq datasets were downloaded from the ENCODE Consortium Portal76 (https://www.encodeproject.org/; data current as of May 1st 2022). Reads were aligned using Bowtie77 (version 1.1.1) as 1 × 36mers against an index containing the mitochondrial genome, with the following settings ‘‘-v 2 -k 2 -m 1 -t --best --strata’’.

  The hg38 version of the Homo sapiens genome was used for all analysis.


### Screening for TF occupancy over the mitochondrial genome
  We then generated plusand minus-strand coverage tracks over chrM for all datasets and made Circos78 plots for each such pair. These Circos plots were manually examined to identify likely TF occupancy events and to screen out potentially artifactual high ChIP signal localization events that do not display the expected asymmetric pattern around true occupancy sites.


### Mappability track generation
  Mappability was assessed as follows. Sequences of length N bases were generated starting at each position in the mitochondrial genome. The resulting set of “reads” was then mapped against the same bowtie index used for mapping real data. Positions covered by N reads were considered fully mappable. In this case, N = 36 as this is the read length for most of the sequencing data analyzed in this study.


### BPNet model training and predictions
  Uniformly processed ChIP-seq datasets were downloaded from the ENCODE portal. For experiments utilizing paired-end sequencing, PCR duplicates were eliminated. However, for experiments with single-end sequencing, all reads were retained due to the absence of a dependable method for removing duplicates without sacrificing significant genuine signal. Then we generated base resolution signal tracks from the 5’ end of the mapped reads.

  The BPNet model architecture and the training approach were adapted from70. The model was designed to accept a one-hot-encoded input DNA sequence of 2,114 base pairs, predicting signals at a 1,000-basepair output window. Additionally, a control input DNA track was also provided to predict the residuals of the ChIP signal from the control track using input sequences. The model outputs comprised of a profile output and a total log counts output for 1,000-bp windows.

  The model architecture consisted of nine consecutive convolutional layers with ReLU activation. The initial convolutional layer featured a filter size of 21 with no dilation, while subsequent layers utilized filter sizes of 3 with a stride of 1 and increasing dilation rates (power of two) in subsequent layers. Each layer had 64 filters, with residual connections between the convolution layers and zero padding across all layers. Profile prediction was calculated by passing the last dilated convolution output to another convolutional layer with a kernel size of 75 (stride 1) and no padding and no activation, followed by stacking with the control profile tracks and feeding to a final convolutional filter of size 1, operating on one base of the logits and control profiles at a time to generate the predicted profile logits. The log of total read counts was computed by performing global average pooling on last dilated convolution output layer. The pooled output was then fed to a dense layer and then concatenated with the log of the total counts across both strands from the control experiment, and then further processed through a final dense layer predicting the log of the total counts across both strands. The predicted profile logits were converted into probabilities using a single softmax function, generating the profile predictions for both strands, and a negative log-likelihood loss was calculated. Mean squared error of the log of total counts across both strands was also computed.

  Training epochs comprised of IDR79-thresholded (Irreproducibility Discovery Rate) peaks and non-peak regions (selected to match the GC content of the peak regions) at a 3:1 ratio. Outlier peak regions with signals exceeding 1.2 times the 99th quantile were removed. Additionally, peak sequences were randomly jittered up to 128 bp to augment positive examples. Reverse-complement augmentation was also employed during training. Models were trained and evaluated using 5-fold cross-validation by chromosomes, ensuring no overlap between training, validation, and test sets. Predictions were averaged across both the forward and reverse-complement of the input sequences. All BPNet models and associated outputs will be released as part of the ENCODE Consortium Phase 4 flagship manuscript.

  Trained models were then used to generated predicted occupancy profiles for both strands over the mitochondrial genome by splitting the mitochondrial genome into 2,114 bp tiles.


## Supplementary Material

## Data availability
  The mitochondrial forward- and reverse-strand tracks analyzed in this study can be found as a UCSC Track Hub at https://mitra.stanford.edu/kundaje/marinovg/oak/public/hubDirectory-chrM/


## Acknowledgments
  The authors would like to thank members of the Kundaje and Greenleaf labs for useful comments and discussions. This work was supported by NIH grants 1UM1HG009436 to W.J.G. and A.K., 1DP2OD022870-01 and 1U01HG009431 to A.K, and P50HG007735, RO1 HG008140, U19AI057266 and UM1HG009442 to W.J.G, the Rita Allen Foundation (to W.J.G.), the Baxter Foundation Faculty Scholar Grant, and the Human Frontiers Science Program grant RGY006S (to W.J.G). W.J.G also acknowledges grants 2017-174468 and 2018-182817 from the Chan Zuckerberg Initiative. Fellowship support also provided by the Stanford School of Medicine Dean’s Fellowship (G.K.M.).