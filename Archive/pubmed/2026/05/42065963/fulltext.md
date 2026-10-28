# Motif grammar and transcriptional programs decouple CTCF binding from nucleosome phasing to control cell-type-specific chromatin insulation


## SUMMARY
  CTCF organizes the genome via cohesin-mediated loop extrusion, insulating topologically associating domains (TADs) and constraining enhancer-promoter communication. Yet, CTCF binding varies across cell types and genomic contexts. In mouse, typically accessible sites combine strong motifs with higher CTCF/cohesin occupancy, while inaccessible sites use weaker motifs stabilized by flanking upstream (U) and downstream (D) sequences that engage peripheral zinc fingers to respectively enhance or dampen binding. Notably, TF motifs within ±35 bp bind cooperatively or competitively depending on expression and positional overlap, a finding supported by AlphaFold predictions and allele-specific perturbations. Favorable motif/TF environments can increase CTCF signal yet disrupt nucleosome phasing and weaken insulation, showing that binding strength and insulation can be uncoupled. Single-molecule maps show that nucleosome phasing regularity predicts insulation strength more reliably than CTCF peak intensity. Thus, differences in motif architecture and TF abundance between species and cell states provide a mechanism for cell-type-specific regulation of CTCF-mediated chromatin insulation.


## INTRODUCTION
  CTCF is an 11-zinc-finger protein that makes contact with a 12-to 15-bp DNA motif through its central zinc fingers (ZFs) 3–7. Together, CTCF and the cohesin complex promote the formation of chromatin loops within highly self-interacting topologically associated domain (TAD) structures, via a loop extrusion mechanism.1,2 The two factors are enriched at TAD boundaries, where they function as insulators promoting interactions between enhancers and promoters within a domain and restricting the action of regulatory elements to target genes outside a domain. CTCF-mediated chromatin folding plays a key role in gene regulation as exemplified by numerous studies showing that disruption of insulated TAD boundaries by deletion of CTCF-binding sites (CBSs) can alter gene expression, leading to defects in developmental processes and cancer initiation as a result of illegitimate enhancer-promoter contacts.3–7

  CTCF-dependent chromatin interactions can be conserved or cell type specific,8 yet the mechanisms linking sequence context, transcriptional environment, and architectural output remain incompletely understood. We and others have shown that CTCF can bind both accessible and inaccessible sites with distinct functional outcomes9,10 and that accessibility and CTCF signal strength correlate with cohesin occupancy and insulation potential. However, CTCF signal intensity alone cannot explain cell-type-specific binding or insulation differences, suggesting that additional sequence and transcriptional determinants contribute to these effects.

  Upstream (U) and downstream (D) motifs engaging peripheral CTCF zinc fingers have been shown to modulate binding stability in mice, but their influence within accessible versus inaccessible chromatin—and their relationship to cohesin overlap and insulation—remain unclear.11–14 Likewise, while several transcription factors (TFs) have been shown to stabilize CTCF binding at specific loci,11,15–19 a systematic framework linking local DNA grammar and cell-type-specific TF programs to CTCF behavior is lacking.

  Here, we integrate CTCF/cohesin chromatin immunoprecipitation sequencing (ChIP-seq), motif analysis, TF profiling, and single-molecule nanopore-based nucleosome occupancy and methylome sequencing (nano-NOMe-seq) in mouse and human cells to define how sequence composition and transcriptional context shape CTCF’s architectural output. We find that sequence elements within a ±35-bp window—including U/D motifs and cell-type-specific TF motifs—modulate CTCF and cohesin binding in an accessibility-dependent manner. Remarkably, stabilizing motif contexts and cooperative TF binding can enhance CTCF signal strength yet disrupt nucleosome phasing, weakening insulation. These findings reveal that nucleosome phasing predicts insulation strength more reliably than CTCF peak intensity, providing a mechanistic basis for cell-type-specific control of 3D genome architecture.


## RESULTS

### U and D motifs are enriched at inaccessible sites in mouse cells
  In mouse embryonic stem cells (mESCs), accessible CBSs more closely match the consensus CTCF motif, whereas inaccessible CBSs show a modest shift toward weaker core motifs, including slight enrichment of an A9-biased ZF5-contact variant (Figure 1A). In human WTC11 induced pluripotent stem cells (iPSCs) by contrast, accessible and inaccessible CBSs have highly similar core motifs, with no consistent enrichment of the weaker T10 variant. Thus, core-motif differences are modest and do not fully explain accessibility-linked differences in CTCF occupancy.

  Because auxiliary U and D motifs can engage non-core CTCF zinc fingers,11–14 we next asked whether these features better explain occupancy differences. In mESCs, canonical U and D motifs, positioned 7 bp upstream and 11 bp downstream of the core motif, are enriched at inaccessible CBSs and are predominantly associated with weaker, A9-biased motifs (Figure 1B; Figure S1). In human WTC11 cells, canonical U motifs are rare and D motifs are absent; instead, the upstream window contains degenerate U-like sequences (Figure 1B; Figure S2; Table S1).

  To test whether U/D grammar affects occupancy, we analyzed CTCF and SMC3 profiles in wild-type (WT) and zinc-finger-mutant CTCF complementation lines9 (Figure 1C). Consistent with prior work,12 U motifs at accessible mESC CBSs are associated with increased CTCF signal, whereas D motifs reduce it; SMC3 often follows the same trend (Figure 1D; Figure S3). These effects persist in CTCF mutants with disrupted binding profiles20 but vary in magnitude, and sometimes direction, depending on the zinc-finger mutation (Figure 1D; Figure S3A). Similar mutant-dependent effects are seen at inaccessible CBSs, where the overall CTCF signal is lower (Figure 1D; Figure S3B). At accessible UD sites, U largely offsets the negative effect of D, whereas at inaccessible UD sites, this compensation is incomplete and stronger CTCF occupancy does not necessarily increase SMC3 signal (Figure 4; Figures S3A and S3B). In WTC11 cells, U motifs have similar directional effects when present, but they are infrequent and D motifs are absent (Figure 1E). More broadly, mouse cells contain a higher fraction of inaccessible CBSs than human cells (Figure S4; Tables S2 and S3), consistent with greater reliance on U/D grammar. Thus, despite conservation of CTCF itself, CTCF binding-site architecture differs between mouse and human.


### TF motifs enriched within 35 bp of CTCF-bound sites stabilize CTCF binding
  Adjacent TF binding has been proposed to stabilize CTCF occupancy,11,15–19 but this has not been examined systematically across accessible and inaccessible CBSs. We therefore used spacing motif enrichment analysis (SpaMo21) to test for TF motif enrichment within ±35 bp of the CTCF motif, focusing on this interval because little enrichment was detected beyond it (Figure 2A; Figure S5). We defined four windows relative to the CTCF core motif: the U motif window (6–8 bp upstream), the U spacer (0–7 bp upstream), the D spacer (0–9 bp downstream), and the D motif window (10–11 bp downstream) (Figure 2A).

  In mESCs, TF motif enrichment outside canonical U/D motifs is more prominent at inaccessible than accessible CBSs, whereas in human WTC11 cells, the opposite pattern is observed, with greater overall enrichment at accessible CBSs (Figure 2A). This difference parallels the higher proportion of accessible CBSs in human cells. Human WTC11 cells also contain far fewer canonical U motifs and no D motifs compared with mESCs, although degenerate U-like motifs are detected at lower frequency (Figure 1B; Figures S6B, S9A, and S9B). In mESCs, a small subset of U motifs is associated with an upstream E-box and is enriched at inaccessible sites (Figure S6A). Across both species, enriched motifs in the U/D windows and spacer regions include multiple TF families, with recurrent family-level redundancy, including HOX factors in the U window and ETS factors in the U spacer (Figure 2B; Figure S6B, S6C, S7A, S7B, and S9–S11). Complete motif frequencies are provided in Tables S4 and S5, with statistical support for the primary accessible versus inaccessible comparisons in Table S3.

  Because most CBSs contain one or more nearby TF motifs and individual motifs tend to contribute modestly, these patterns suggest that many TFs can potentially modulate CTCF occupancy in a partially redundant, cell-type-specific manner. Since TF composition varies across tissues and cells (Table S5), differences in transcriptional state could shape the TF environments surrounding CBSs.

  To test whether nearby TF motifs are associated with altered CTCF/cohesin occupancy, we examined CTCF and SMC3 profiles at CBSs containing enriched upstream and/or downstream TF motifs. In WT mESCs, enrichment of TF motifs upstream, downstream, or at both positions is associated with increased CTCF signal at accessible CBSs, with SMC3 generally following the same trend (Figure 2C). Similar effects are observed in CTCF zinc-finger mutants, although the magnitude varies by mutant (Figure 2C; Figure S8A). At inaccessible CBSs, overall CTCF and SMC3 signals are lower and the effects of upstream versus downstream motifs are more distinct: upstream TF motifs have the stronger positive association when present alone, whereas downstream motifs can dampen the effect of upstream motifs when both are present (Figure 2C; Figure S8B). In human WTC11 cells, nearby TF motifs are likewise associated with increased CTCF occupancy (Figure 2D), indicating that despite species differences in motif composition, TF enrichment near CBSs is similarly linked to stronger CTCF binding.

  Together, these results indicate that nearby TF motifs are widespread at CBSs in both mouse and human and are associated with increased CTCF occupancy. The motif families present within each window are partly redundant and vary across cell types, suggesting that local TF environments provide a flexible, transcription program-dependent layer of CTCF regulation (Tables S4 and S5).


### Transcriptional programs are associated with cell-type-specific CTCF occupancy
  In both mESCs and human iPSCs, TFs whose motifs occur near CTCF sites are more highly expressed at accessible than inaccessible CBSs (Figure 3A). However, the relationship between TF expression and nearby motif representation differs by species: inaccessible sites are more responsive in mESCs, whereas accessible sites show stronger relationship in human iPSCs (Figure 3B), possibly reflecting the greater fraction of inaccessible CBSs in mouse. These enrichment patterns are summarized in Table S6, with full results in Tables S4 and S5.

  Across isogenic WT and mutant CTCF mESC lines, differences in TF expression are associated with changes in the fraction of occupied CTCF peaks containing the corresponding nearby motif (Figure 3C; Table S4), indicating that transcriptional state is linked to which CBSs are occupied. Because the genome sequence is fixed, these analyses reflect changes in occupied loci rather than changes in motif content. Similar expression-dependent associations are observed across human ENCODE datasets (Figure 3D; Table S7). Together, these results support a model in which transcriptional programs help bias CTCF occupancy in a cell type-specific manner.


### Individual TFs are associated with stronger CTCF occupancy and can either co-bind or compete with CTCF
  To move from motif enrichment to specific factors, we examined CTCF co-occupancy with representative TFs at accessible CBSs. For KLF4, OCT4, MYC, SOX2, and YY1, co-bound sites show stronger CTCF signal than CTCF-only sites, indicating that co-occupancy is associated with increased CTCF binding (Figure 4A). At the same time, the heatmaps and profiles show that for most TFs, CTCF-free CBSs occupied by TFs display stronger TF signal than co-bound sites (Figure 4A; Figure S12). At these TF-only CBSs, TF peak summits are centered close to the oriented CTCF motif, consistent with competition between CTCF and the TF. By contrast, at co-bound sites, TF signal is detected both over the CBS and within the regions flanking it. The corresponding inaccessible-site profiles are shown in Figure S12.

  To test whether these interactions are structurally plausible, we used AlphaFold3 to model TF-CTCF-DNA complexes. At co-bound YY1 sites, YY1 is predicted to bind outside the CTCF core motif or within the U spacer, generally with limited perturbation of CTCF conformation, although local DNA geometry can shift (Figure 4B). By contrast, at YY1-only CBSs, YY1 is predicted to overlap the CTCF core or extended binding site, consistent with direct competition with CTCF (Figure 4C). Comparable AlphaFold3 predictions for KLF4, MYC-MAX, OCT4, and SOX2-OCT4 are shown in Figure S13. Together, these data support both cooperative and competitive modes of TF-CTCF interaction.


### Allele-specific SNP analyses support both cooperative and competitive TF-CTCF interactions
  Analysis of 145 ENCODE TF ChIP-seq datasets in GM12878 showed that 69% of CTCF peaks overlap at least one TF (Table S8). We, therefore, used allele-specific analyses at heterozygous SNPs that disrupt either CTCF or nearby TF motifs (Table S9). SNPs disrupting the CTCF motif are associated with reduced CTCF, co-bound TF, and RAD21 binding, with variable effects on accessibility (Figures 5A and 5B), whereas SNPs disrupting TF motifs can either reduce CTCF binding, as seen for IKZF2 (Figure 5C), or favor CTCF binding, as seen for BHLHE40 (Figure 5D). These examples support both cooperative and competitive TF-CTCF interactions.

  Genome-wide, we identified 131 regions with allele-specific CTCF binding accompanied by allele-specific binding of at least one cofactor (1,064 CTCF–TF pairs; Tables S9 and S10). Of these, 65 primarily affect the cofactor motif, 50 the CTCF motif, and 16 both. CTCF and the cofactor preferentially bind the same allele in 118/131 regions, whereas only 13/131 show opposite allelic bias, indicating that cooperative coupling is more common than competition.


### CTCF asymmetrically repositions and phases flanking nucleosomes
  To ask how CTCF binding affects nucleosome positioning in a context-specific manner, we performed long-read Nano-NOMe-seq and WGBS-NOMe-seq in WT mESCs. Both assays allow us to assess nucleosome positioning using exogenous 5mC at HGC (GC excluding CGC) and endogenous 5mC/5hmC at WCG (CG excluding GCG and CCG) at the single-molecule level. WGBS-NOMe-seq generates shorter informative molecules and in contrast to Nano-NOMe-seq is unable to distinguish 5mC from 5hmC. Nano-NOMe-seq and WGBS-NOMe-seq in WT mESCs gave similar nucleosome and methylation patterns, although nano-NOMe-seq showed a lower baseline methylation estimate (Figure S14A). Restricting analyses to GpC-containing CTCF motifs confirmed that these sites behave similarly to the full CBS set and allowed orientation-aware separation of bound and unbound molecules (Figure S14B).

  At CTCF peaks, bound molecules show asymmetric repositioning and phasing of flanking nucleosomes, with the N-terminal nucleosome displaced farther from the CBS than the C-terminal nucleosome (Figure 6A). This pattern is retained at both accessible and inaccessible sites, but inaccessible and weak-CTCF peaks show narrower spacing and less-organized phasing (Figure 6A). Sites with strong SMC3 show similar well-phased patterns, whereas SMC3-negative CTCF peaks contain more unbound molecules and weaker phasing (Figure 6B), consistent with strong SMC3 marking longer-lived CTCF-binding states.20

  At CTCF-free, motif-containing sites, most molecules are occupied by a narrow non-nucleosomal footprint consistent with TF binding (Figure 6C), in line with the TF analyses in Figures 3, 4, and 5. Unlike CTCF-bound CBSs, these sites show more symmetric nucleosome positioning around the motif, indicating that CTCF and non-CTCF TFs impose distinct local chromatin architectures.


### Surrounding motifs modulate nucleosome phasing and insulation at CTCF sites
  We previously found that U and UD motifs are associated with stronger CTCF occupancy, whereas D motifs are associated with weaker occupancy (Figure 1D), and that nearby upstream and downstream TF motifs likewise have distinct effects on CTCF signal (Figure 2C). These surrounding motifs do not alter the asymmetric positioning of the N- and C-terminal flanking nucleosomes, but they do affect the regularity of nucleosome phasing. Across both U/D-defined and TF-defined classes, destabilizing motif contexts are associated with disrupted phasing, whereas stronger CTCF signal does not necessarily correspond to more ordered nucleosome organization (Figures 7A and 7B). Thus, CTCF occupancy and nucleosome phasing can be uncoupled.

  To ask whether these phasing differences are reflected in higher-order chromatin structure, we analyzed high-throughput chromosome conformation capture (Hi-C) insulation in WT mESCs using the pipeline described by Do et al.9 U-, UD-, and D-motif classes show category-level differences in insulation that parallel their effects on nucleosome phasing (Figures 7A–7C). The same relationship is observed for TF-motif-defined classes (Figures 7B–7D): categories with less-regular phasing show weaker insulation, whereas categories with more-regular phasing show stronger insulation. Together, these data indicate that nucleosome phasing across sequence-context classes tracks insulation strength better than CTCF peak height alone.


## DISCUSSION
  CTCF and cohesin organize loop domains and insulation through cohesin-mediated loop extrusion, but CTCF occupancy does not always predict boundary strength or transcriptional output, indicating that additional features determine whether a bound site functions as an effective insulator.1,2,22,23 By integrating motif architecture, chromatin context, TF programs, and single-molecule nucleosome mapping, we show that CTCF signal strength, nucleosome organization, and insulation can be partially decoupled and that nucleosome phasing provides an intermediate layer linking sequence context to topological output.

  Within ±35 bp of the core motif, we identify two classes of contextual features that modulate CTCF behavior: auxiliary upstream/downstream motifs that engage peripheral CTCF zinc fingers12 and nearby TF motifs, which show substantial family-level redundancy and likely provide context-dependent regulatory input.19 TF motif environments near CTCF therefore create an adaptable interface through which transcriptional programs can shape CTCF occupancy and cell-type-specific binding profiles.

  Our data further indicate that TFs can bind either cooperatively or competitively at CBSs. AlphaFold3 modeling suggests that at co-bound loci, TFs typically bind outside the CTCF core motif or within the flexible spacer between zinc fingers, preserving overall CTCF-DNA geometry, whereas at TF-only CBSs they frequently overlap the CTCF motif, consistent with steric competition. These structural patterns agree with allele-specific analyses showing that SNPs disrupting either TF or CTCF motifs cause reciprocal changes in CTCF occupancy.

  Across these sequence contexts, nucleosome phasing tracks insulation better than CTCF signal alone: sites with irregular phasing show weaker insulation even when CTCF signal strength is high. Differences between mouse and human binding largely reflect shifts in the prevalence of particular CTCF site classes—likely influenced by species-specific transposable element expansions—rather than changes in the fundamental mechanism of CTCF function.24 However, across both species, local motif features and TF environments modulate binding behavior, while nucleosome phasing remains the closer correlate of insulation output.

  Together, these findings show that stable CTCF binding is necessary but not sufficient for insulation. Instead, nucleosome phasing provides the key chromatin intermediary linking local sequence grammar, TF environments, and higher-order genome architecture. In this framework, motif context and TF programs tune CTCF occupancy, while nucleosome organization influences whether cohesin-driven loop extrusion is effectively blocked, providing a mechanistic link between transcriptional regulation and genome folding.


### Limitations of the study
  Many results in this study come from genome-wide comparisons across large site sets and should be interpreted as associations with effect sizes rather than deterministic rules at individual loci. The single-molecule nano-NOMe heatmaps provide qualitative visualization of nucleosome phasing patterns. Although aggregate profiles and class-level comparisons support these observations, we did not perform formal spectral analyses (e.g., fast Fourier transform [FFT] or autocorrelation) to quantify periodicity or phasing strength. Future work applying quantitative periodicity metrics to single-molecule data will refine the relationship between nucleosome spacing, regularity, and insulation at CTCF-bound sites.


## RESOURCE AVAILABILITY

### Lead contact
  Further information and requests for resources should be directed to and will be fulfilled by the lead contact, Jane A. Skok (jane.skok@nyulangone.org).


### Materials availability
  The WT and mutant CTCF mESC lines are available upon reasonable request.


### Data and code availability

## STAR★METHODS

### EXPERIMENTAL MODEL AND STUDY PARTICIPANT DETAILS

#### Cell line generation and culture
  Vectors for doxycycline-inducible expression of WT and mutant mouse Ctcf cDNAs and targeting into E14Tg2a mESCs (19, XY; 129/Ola isogenic background) were generated as described in Do et al.9 Cells and derived clones were cultured feeder-free on 0.1% gelatin-coated dishes in DMEM supplemented with 15% FBS, 100 U/mL penicillin/100 μg/mL streptomycin, 1× GlutaMAX, 1 mM sodium pyruvate, 1× MEM non-essential amino acids, 50 μM β-mercaptoethanol, 10 ^4 U/mL LIF, 3 μM CHIR99021, and 1 μM PD0325901, as described in Do et al.9


### METHOD DETAILS

#### Induction of auxin inducible degradation of CTCF and doxycycline induced expression
  Endogenous CTCF was degraded by addition of 500 μM indole-3-acetic acid (IAA). Transgene expression was induced with 1 μg/mL doxycycline (Dox). Cells were treated with IAA and/or Dox for 2 days.


#### WGBS and nano-NOMe-seq sample and library preparation
  After 2 days of IAA/Dox treatment, 1 × 10 ^6 cells were collected, washed in cold PBS, and nuclei were isolated as described in Battaglia et al.,37 using cold lysis buffer (10 mM Tris-HCl pH 7.4, 10 mM NaCl, 0.5 mM spermidine, 1.5 mM MgCl2, 0.1 mM EDTA, 0.25% IGEPAL CA-630) for 3–6 min, followed by washing in nuclei wash buffer (10 mM Tris-HCl pH 7.4, 50 mM NaCl, 0.5 mM spermidine, 1.5 mM MgCl2, 0.1 mM EDTA).

  For GpC methyltransferase labeling, nuclei were resuspended in 1× GpC MTase reaction buffer and equilibrated to 37°C. Methyl ation was performed in two sequential 6-min incubations with M.CviPI and SAM. Reactions were stopped with prewarmed 2× stop buffer (20 mM Tris-HCl pH 7.4, 600 mM NaCl, 10 mM EDTA, 1% SDS), followed by proteinase K digestion (200 μg/mL, 4 h at 56°C), RNase A treatment (100 μg/mL, 30 min at 37°C), and a second proteinase K digestion (200 μg/mL, 30 min at 37°C).

  High-molecular-weight DNA was extracted by phenol-chloroform, precipitated with 0.7–1 volumes isopropanol, washed in 70% ethanol, resuspended in EB buffer, and quantified by Nanodrop 2000. DNA size was assessed using Agilent genomic DNA ScreenTape.


#### WGBS-NOMe-seq library preparation
  For WGBS-NOMe-seq, DNA was sonicated (Diagenode Bioruptor) to ~350 bp, bisulfite-converted using the EZ DNA Methylation-Gold Kit (Zymo), and libraries were prepared with the xGen Methyl-Seq DNA Library Prep Kit (IDT) according to the manufacturers’ protocols. Libraries were sequenced as 150-bp paired-end reads on a NovaSeq X to a theoretical depth of ~20× per sample.


#### Nano-NOMe-seq library preparation
  For Nano-NOMe-seq, DNA was sheared to ~20 kb using a Covaris G-Tube, size-checked by Agilent ScreenTape, and 1.5 μg DNA was used for library preparation with the Oxford Nanopore SQK-LSK114 kit. Libraries were quantified by Qubit dsDNA HS, loaded at 150–200 fmol onto PromethION R10.4.1 flow cells, and sequenced on a PromethION P24 for 72 h. Runs used standard settings with rejection of fragments <1 kb, detection of 5mC and 5hmC, and super-accurate basecalling enabled.


#### Datasets and data processing

##### ChIP-seq, RNA-seq, and ATAC-seq
  CTCF ChIP-seq, RNA-seq, and ATAC-seq data for WT and mutant mESCs were generated and processed as described previously9 using the Seq-N-Slide pipeline.38 For human analyses, we downloaded ENCODE biosamples with matched CTCF ChIP-seq, RNA-seq, and ATAC-seq data (Tables S1A, S1B, and S4). CTCF peaks were scanned for the CTCF consensus motif (JASPAR MA0139.2)25 using FIMO29 (p < 5 × 10 ^-5), and only samples with ≥20% motif-containing CTCF peaks were retained. CBSs were defined as CTCF ChIP-seq peaks containing a consensus CTCF motif. CBSs overlapping an ATAC-seq peak were classified as accessible, and those without ATAC overlap as inaccessible, using bedtools intersect.39

  For GM12878, we downloaded 145 ENCODE TF ChIP-seq narrowPeak files to quantify TF co-binding at CTCF sites (Table S4). For allele-specific analyses, BAM files for CTCF, RAD21, IKZF2, BHLHE40, ARNT, and ATAC-seq were also obtained (Table S4), together with phased GM12878 genotypes from the Platinum Genomes project40 (PRJEB3246). To validate TF co-binding in mESCs, KLF4, OCT4, SOX2, MYC, YY1, and input ChIP-seq datasets were downloaded from GEO (GSE201852 and GSE236376)25 and processed with Seq-N-Slide.38 Reads were aligned to mm10 with Bowtie241 and peaks were called with MACS2.42 CTCF-oriented heatmaps and profiles were generated with deepTools30 using the 15-bp CTCF core motif as the centered region.


##### Hi-C data
  Hi-C data were generated with the Arima Hi-C kit and processed with HiC-Pro and HiCExplorer as described previously.9 Matrices were generated at 10-kb resolution. Insulation scores were computed with GENOVA,42 and CTCF-oriented insulation profiles were generated with deepTool.30 Unless otherwise stated, insulation analyses were summarized across the same CBS categories used throughout the manuscript.


##### WGBS-NOMe-seq and nano-NOMe-seq processing
  WGBS-NOMe-seq FASTQs were trimmed with Trim Galore,28 aligned to mm10 with Bismark.31 deduplicated, and processed in NOMe-seq mode to extract methylation in WCG and HGC contexts. GCG sites were excluded because of ambiguity, and CCG sites were excluded to account for off-target GpC methyltransferase signal. The first base at the 3′ end of read 2 was ignored (–ignore_3prime_r2 1) because of methylation bias. Positive and negative strands were combined because we did not detect substantial hemi-methylation genome-wide or at CTCF peaks. GpC/CpG sites overlapping ENCODE blacklist regions27 or showing >100× coverage were excluded.

  For nano-NOMe-seq, pod5 files were basecalled and modification-called with Dorado,32 aligned to mm10, filtered for MAPQ ≥10, and processed with Dorado pileup and modkit extract33 to obtain single-molecule methylation calls in WCG and HGC contexts. ENCODE blacklist-overlapping sites27 and sites with >100× coverage were excluded.

  CTCF-oriented methylation profiles were generated with deepTools,30 and single-molecule heatmaps in R. Molecules were classified as CTCF-bound or CTCF-unbound based on methylation at a GpC within the CTCF motif. For KLF4, OCT4, SOX2, MYC, and YY1, TF-bound and TF-unbound molecules were defined using methylation within a 10-bp window centered on the TF motif, because most of these motifs lack a GC dinucleotide.


### QUANTIFICATION AND STATISTICAL ANALYSIS
  All statistical tests were two-sided unless otherwise stated. For comparisons of continuous or distributional variables across site sets (e.g., numbers of tissues or conditions with motif enrichment), we used the Mann–Whitney U test and report Cliff’s delta as effect size, with 95% confidence intervals estimated by bootstrapping (1,000 resamples). For comparisons of proportions (e.g., classification as “similar to U/D motif” or enrichment present versus absent), we used Fisher’s exact test and report odds ratios with 95% confidence intervals. Where multiple related hypotheses were tested, p values were adjusted by the Benjamini–Hochberg procedure and q values (FDR) are reported. Full statistical results supporting Tables S1B and S2A/S2B are provided in Table S1C, and statistical outputs supporting Figures 3, 4, and 5 are provided in Tables S3, S4, and S5A, including BH-FDR q values in Table S5A.


#### Downstream analyses

##### Motif logos and motif spacing enrichment analysis
  Motif logos centered on FIMO-identified CTCF motifs29 were generated with ggseqlogo.35 Enriched TF motif spacings around bound CTCF motifs were identified with SpaMo21 using a 500-bp window centered on each CBS and stratified by accessibility. TF PWMs were obtained from JASPAR 202425 and U/D PWMs from **Nakahashi et al.12 Motif clustering and tree construction were performed with universalmotif36 for the upstream spacer, U window, further upstream region, downstream spacer, D window, and further downstream region.


##### Association between TF motif enrichment and TF expression
  To test whether TFs enriched at accessible CBSs were more highly expressed in WT mESCs and human iPSCs, we defined accessible-enriched TFs as those showing a ≥2-fold increase in motif frequency within 35 bp of the CTCF motif by SpaMo. Associations between TF expression (log2 TPM) and chromatin accessibility were tested using multivariate linear regression with backward-stepwise selection, controlling for motif orientation and enrichment window relative to the CTCF motif. Adjusted expression estimates and pairwise comparisons of predictive margins were computed in STATA v17.

  To test the overall relationship between TF expression and motif enrichment, we performed aggregated analyses across WT and mutant mESCs or across ENCODE human samples (Table S1A). TF expression and motif frequencies were summarized by sample, accessibility class, enrichment window, and motif orientation, and analyzed by multivariate linear regression controlling for accessibility, orientation, and window. Differential effects were estimated from adjusted slopes (interaction terms with TF expression) using model margins and pairwise comparisons in STATA v17. Bivariate linear regressions for individual TFs were performed in R.


##### AlphaFold3 prediction
  AlphaFold334 was used to assess local steric compatibility of TF–CTCF co-occupancy versus occlusion on short genomic segments centered on candidate motifs. Because models used naked DNA and did not include nucleosomes or higher-order chromatin features, results were interpreted qualitatively. For KLF4, OCT4, SOX2, MYC, and YY1, loci were sampled from CTCF-only, CTCF–TF cobound, and TF-only classes. Positive- and negative-strand DNA sequences centered on the relevant motif with 35-bp flanks were extracted with bedtools.39 Protein sequences were obtained from UniProt43 and CTCF ZF1–11 coordinates from **Yang et al.44 Structures were visualized in PyMOL 3.10, and RMSDs were calculated in PyMOL.


##### Allele-specific binding analyses
  Allele-specific binding (ASB) in GM12878 was analyzed by separating ChIP-seq or ATAC-seq reads overlapping phased heterozygous SNPs in R. Allele-specific BAM and bigwig files were then generated using samtools45 and bamCoverage.30 To identify ASB SNPs disrupting the TF motif, allele-specific motif affinity was computed using the R package, atSNP.46


## Supplementary Material

## ACKNOWLEDGMENTS
  This work was supported by 1R35GM122515 (J.A.S.) and NIH P01CA229086 (J.A.S.). G.J. was supported by a fellowship from the NCC. The authors thank the Skok lab members for helpful scientific discussions, New York University School of Medicine High Performance Computing Facility (HPCF) for computing technical support, Adriana Heguy and the Genome Technology Center (GTC) core for sequencing efforts, and NYU Flow Cytometry and Cell Sorting Center for FACS analysis and sorting. GTC is a shared resource partially supported by the Cancer Center Support Grant P30CA016087 at the Laura and Isaac Perlmutter Cancer Center. The authors thank Sofia Battaglia from Bernstein’s lab for her advice and protocols for the nano-NOMe-seq library preparation.