## Abstract

Non-coding variants discovered by genome-wide association studies (GWAS) are enriched in regulatory elements harboring transcription factor (TF) binding motifs, strongly suggesting a connection between disease association and the disruption of cis-regulatory sequences. Occupancy of a TF inside a region of open chromatin can be detected in ATAC-seq where bound TFs block the transposase Tn5, leaving a pattern of relatively depleted Tn5 insertions known as a “footprint”. Here, we sought to identify variants associated with TF-binding, or “footprint quantitative trait loci” (fpQTLs) in ATAC-seq data generated from 170 human liver samples. We used computational tools to scan the ATAC-seq reads to quantify TF binding likelihood as “footprint scores” at variants derived from whole genome sequencing generated in the same samples. We tested for association between genotype and footprint score and observed 693 fpQTLs associated with footprint-inferred TF binding (FDR < 5%). Given that Tn5 insertion sites are measured with base-pair resolution, we show that fpQTLs can aid GWAS and QTL fine-mapping by precisely pinpointing TF activity within broad trait-associated loci where the underlying causal variant is unknown. Liver fpQTLs were strongly enriched across ChIP-seq peaks, liver expression QTLs (eQTLs), and liver-related GWAS loci, and their inferred effect on TF binding was concordant with their effect on underlying sequence motifs in 80% of cases. We conclude that fpQTLs can reveal causal GWAS variants, define the role of TF binding site disruption in disease and provide functional insights into non-coding variants, ultimately informing novel treatments for common diseases.

Graphical Abstract We leverage footprinting methods to infer transcription factor binding likelihood genome-wide across 170 liver ATAC-seq samples and implicate 693 SNPs with a genetic influence on binding. Unlike other comparable approaches, this analytical method is not limited in resolution by the constraints of linkage disequilibrium, and can prioritize likely causal variants at GWAS loci for subsequent experimental validation.


## Introduction

More than 90% of GWAS-implicated variants are located in non-coding genomic regions with uncharacterized effects on gene regulation 1 – 4 , limiting their utility in characterizing disease biology and implicating novel targets for treatment. Furthermore, given the structure of linkage disequilibrium (LD) across the genome, a variant with a true biological effect on some trait (i.e., a causal variant) will be correlated with nearby variants, making it challenging to distinguish which variants among them is causal 5 – 7 . A second challenge after association mapping is to determine the effector gene(s) regulated by a given causal variant through which the trait effect is conferred. Single nucleotide polymorphisms (SNPs) associated with gene expression, i.e. expression quantitative trait loci (eQTLs), as catalogued by the GTEx Consortium, are strongly linked with approximately 43% of disease-associated GWAS signals 8 , and on average only 11% of disease heritability is estimated to be explained by GTEx gene expression 9 . A recent study modeled that GWAS loci and eQTLs are systematically biased towards different types of cis-regulatory variants, suggesting that additional connections beyond those provided by eQTLs are needed to provide mechanistic insights into observed complex trait association signals 10 . Other variant-to-gene mapping approaches which use 3D chromatin architecture data from Hi-C or Capture-C require the causal variant to be nominated before implicating the effector gene 11 – 13 . Methods to experimentally validate the effects of putative causal SNPs on gene expression are expensive and time consuming, making the prioritization of candidate variants a key bottleneck in disease genomics.

Non-coding GWAS-implicated variants are concentrated in regulatory regions and near transcription factor (TF) binding motifs 1 , 14 , 15 , suggesting that the disruption of cis-regulatory sequence plays a mechanistic role in conferring disease risk. ATAC-seq, an experimental method traditionally used to measure chromatin accessibility, can also be used to detect TF binding. In this method, the transposase Tn5 inserts sequencing adapters into DNA, preferentially at genomic locations where chromatin is open 16 . However, bound TFs can partially block Tn5, leaving a pattern of relatively depleted Tn5 insertion sites known as a “footprint” 17 . Unlike ChIP-seq, which requires a high-quality antibody and can only be run for one TF at a time, ATAC-seq footprints can detect binding sites without specifically knowing the identity of the bound TF. In recent years, multiple algorithms have been developed to quantify binding strength using footprint patterns in ATAC-seq or DNase-seq data, albeit in relatively small sample sizes 18 – 21 . Footprinting analysis is valuable for implicating causal variants, as it can overcome limitations of resolution in GWAS/eQTL studies due to LD constraints by precisely locating TF binding, and implicate specific TFs based on binding motifs at the footprint location 22 .

Recent studies have investigated the sequence dependency of TF binding via allele-specific cleavage patterns in ATAC-seq 23 , multiplex protein-DNA binding array 24 , or allele-specific ChIP-seq 25 . Most recently, a study used DNase-seq footprints in LCLs from 57 genotyped individuals to uncover SNPs associated with footprint-inferred TF binding, known as footprint QTLs (fpQTLs) 26 . However, this study, and many other footprinting studies 20 , 21 , 27 were limited to sites which overlapped known TF sequence motifs. Given the limited ability of sequence motifs to computationally predict true binding locations 24 , 28 , this motif-centric approach is much less powered to detect binding events compared to motif-agnostic approaches.

Here, we applied footprinting analysis to a uniformly generated dataset of human liver ATAC-seq samples from 170 genotyped individuals, the largest sample size to date, to measure TF binding strength genome-wide. GWAS have uncovered hundreds of loci associated with liver-related traits including metabolic associated steatotic liver disease (MASLD, formerly NAFLD) 29 – 31 , type 2 diabetes (T2D) 32 , hyperlipidemia 13 , 33 , enzyme levels 34 , and T2D risk factors such as obesity 35 – 37 , most of which have unknown functional mechanisms 38 . We report 693 fpQTLs associated with TF binding at an FDR of 5%. fpQTLs are enriched in transcription start site (TSS)-proximal regions, ChIP-seq peaks for liver-expressed TFs, lipid-associated loci, and molecular QTLs for expression (eQTLs) and chromatin accessibility (caQTLs) mapped in human liver. Notably, the measured effect of an fpQTL on TF binding was highly concordant with its effect on an underlying sequence motif. Finally, we demonstrate that fpQTL discovery can fine-map GWAS loci by pinpointing the causal variant and implicate a specific TF whose binding motif is disrupted. Our map of genotype-dependent TF binding sites offers the opportunity to (1) interpret functional non-coding variants by proposing TF binding as a biological mechanism for association, and (2) aid the identification of the active variant(s) at GWAS loci where the causal variant was previously unknown due to LD-related constraints.


## Materials and Methods


## Study population

The study utilized data collected from 189 specimens obtained from liver transplant recipients from their respective donor cohorts at the University of Pennsylvania, collected in 2012-2017 and 2018-2020 enrolled under the BioTIP study (Biorepository of the Transplant Institute at the University of Pennsylvania). Participants were enrolled in the prospective biorepository and clinical databases, collecting biological samples and clinical data at the time of transplantation, and at predetermined intervals after transplantation. The study was approved by the University of Pennsylvania’s Institutional Review Board (2018-2020: FWA00004028, protocol #814870). All research was conducted in accordance with both the Declarations of Helsinki and Istanbul. The participants signed informed consent forms before transplantation and at the time of organ donation. Specimens collected from this protocol used in this study were deidentified and subsequently anonymized.


## ATAC-seq Library Generation

Human liver wedge biopsies were supplied by the Penn Transplant Institute. Samples were derived from human livers deemed fit for transplantation, and were collected at the time of the surgery. Samples were flash frozen and stored at −80 C. Chromatin accessibility profiles were generated using a modified Assay for Transposase Accessible Chromatin with high-throughput sequencing (ATAC-seq) called Omni-ATAC 16 , 39 . Briefly, approximately 20 mg of tissue was dounce homogenized in a homogenization buffer. Tissue homogenate was layered over Iodixanol density gradient and spun. Nuclei were extracted post-centrifugation and quantified using a hemocytometer. Approximately 50,000 nuclei were rinsed and added to the Omni-ATAC reaction mix. Transposition reactions were incubated at 37 C for thirty minutes. Reactions were cleaned with spin columns and eluted. Polymerase chain reaction (PCR) was initially performed for five cycles. At this point, a qPCR reaction was performed to determine the additional number of PCR cycles to use. The additional number of PCR cycles was determined by calculating the qPCR cycle at which the fluorescence intensity was equal to one-third the maximum fluorescent intensity of the reaction. Libraries were purified and profiles were measured using Bioanalyzer High-Sensitivity DNA Analysis Kit (Agilent). Libraries that passed visual quality control and concentration checks were frozen at −20 C.


## ATAC-seq Library Sequencing

Libraries were pooled in two separate groups, 93 samples and 96 samples, and sequenced at Vanderbilt University Medical Center (VUMC VANTAGE (Vanderbilt Technologies for Advanced Genomics)) on the Illumina NovaSeq 6000 with PE150 sequencing. Libraries were pooled and sequenced such that each sample was covered by approximately fifty million sequencing reads.


## ATAC-seq Data Processing

ATAC-seq data were processed following the ENCODE processing pipeline, with slight modification. Briefly, FASTQ files were processed with fastp (v.0.12.5) with parameters “-y -c -g”. FastP processed FASTQ files were aligned to GRCh38 using bwa mem (v. 0.7.17-r1188) and piped into samtools (v.1.9) view with parameters “-S -b -f 2 - > outFile.bam” to generate bam files. Duplicate reads were marked and removed using Picard Tools (v.1.141) MarkDuplicates with parameters “ASSUME_SORTED=true, REMOVE_DUPLICATES=true”. Autosomal reads only were retained using samtools view with parameters “input.bam -b {1..22} > ${i}.auto.bam”. Open chromatin peaks were called on all 189 samples using Genrich (v0.6.1) ( https://github.com/jsh58/Genrich ) with parameters -j, -m 10 and -g 50.


## Genotyping and Imputation from Low Coverage Whole Genome Sequencing

Sample genotype was obtained using low-pass whole genome sequencing from Gencove. Genotypes were filtered to retain only polymorphic sites within our sample population. Polymorphic genotypes were filtered on minor allele frequency (MAF) > 0.05 and genotype posterior probability (GP) > 0.8. Genotypes were phased using Eagle (v2.4.1) 40 .

Of the 189 ATAC-seq samples, 14 were removed for poor genotyping quality, and 5 were removed for having a low read count (< 30 million reads), leaving 170 samples used in fpQTL discovery (see Supplementary Table 1, Figure S1A for sample ancestry and covariate information).


## Calculation of footprint scores

Footprint scores were calculated using PRINT 41 ( https://github.com/HYsxe/PRINT , commit 2023-05-14). ATAC-seq bam files were processed into fragment files as described on the PRINT Github ( Web Resources ). Read pairs were removed during this step if (i) both reads mapped to a different chromosome, or (ii) read 1 mapped to the - strand, but did not cover the entire fragment (insertions at these reads did not show the expected Tn5 sequence bias).

Every variant that was found within an open chromatin peak and had MAF > 0.05 within our samples was expanded into a region with 100 bp on either side of the variant (by default, PRINT uses a “context radius” of 100 bp, meaning the outer 100 bp of a region are needed to calculate the background insertion distribution). The Tn5 sequence bias in these regions was calculated by PRINT using the model trained by Hu et al 41 .

For every ATAC-seq sample, getTFBS() was run on the variant regions, following the vignette provided on the PRINT Github ( Web Resources ). The only non-default parameter was tileSize = 1, to measure only the FP score at the variant. The vector of TF binding scores (FP scores) across all variants was extracted for each sample, and these vectors were combined into the footprint score matrix (n = 170, # variants = 3,258,578).


## fpQTL discovery

The distribution of FP scores in each sample was quantile-transformed using the average empirical distribution observed across all samples, following the lead of GTEx cis -eQTL mapping 42 . However, the FP scores for each variant were not transformed to the quantiles of the standard normal distribution, in order to preserve the signal of extreme FP scores (i.e. FP score ≈ 1)

For every variant considered, the following regression was run in R: Where y is the vector of FP scores across all samples, g is the vector of genotypes across all samples (represented by an additive model as the number of non-reference alleles), and X c is a matrix of covariates across samples which includes sex, sequencing batch, and the first three principal components inferred from genotypes. The estimate of β 1 was taken as the estimated fpQTL effect size of the variant, and the fpQTL significance was calculated as the P -value of the t-test (two-sided) under the null hypothesis that β 1 = 0. To test the effect of covariates on regression results, we also performed this regression analysis excluding covariates and observed that SNP P -values did not change drastically ( Figure S2E ). Multiple test correction was performed using a false discovery rate (FDR) q-value method 43 , 44 . Variants with a calculated FDR q-value < 0.05 were labeled fpQTLs.


## Allele-specific footprinting

For a given fpQTL, the allelic origin of aligned fragments within heterozygous samples could be determined if at least one of the paired reads overlapped the SNP. Such fragments were separated by allele, and the resulting insertion sites were combined across samples (due to low coverage of allelic fragments) to create “allele-specific insertion patterns”. These insertion patterns were then fed into PRINT separately to calculate allele-specific footprint scores for that fpQTL.


## Gene locations

The locations of transcription start sites (TSSs) were based on NCBI RefSeq’s curated list of genes 45 . The table ncbiRefSeqCurated was downloaded from the UCSC Genome Browser on Jan 22, 2024.


## Liver eQTLs

Association data for expression QTLs from GTEx Analysis V8 were downloaded from the GTEx Portal 8 (GTEx_Analysis_v8_eQTL.tar)


## Liver caQTLs

caQTLs were called using the same 189 liver samples, as described in a companion manuscript by B.M.W. (in preparation).


## fpQTL overlap with GWAS loci

GWAS summary statistics and lead variants for BMI 36 , T2D 32 , MASLD 31 , enzymes (alanine transaminase/ALT, alkaline phosphatase/ALP, gamma-glutamyl transferase/GGT) 34 , and lipids 33 were downloaded from their respective publications ( Supplementary Table 5 ). LD proxies for lead variants were found using the online tool SNiPA 46 with Variant Set = 1000 Genomes Phase 3v5, Population = European, and LD (r 2 ) threshold = 0.8.

For each liver-related trait, we constructed a 2×2 table, where one dimension represented fpQTLs, and the other dimension represented SNPs which were in LD (r 2 > 0.8) with a GWAS sentinel variant for that trait. 52805 SNPs, including 20 fpQTLs, did not have LD info in the 1000 Genomes Phase 3v5 SNP set used by SNiPA, and so were not included in the tables. P -values and odds ratios were computed using Fisher’s exact test on this table.


## fpQTL enrichment for disease heritability

We performed stratified LD score regression using LDSC ( http://www.github.com/bulik/ldsc ) v.1.0.1 with the --h2 flag to estimate SNP-based heritability of liver-related traits. We created an annotation consisting of only significant fpQTL SNPs, which was then used to compute annotation-specific LD scores and enrichment for each liver trait.

The baseline model LD scores, plink filesets, allele frequencies and variants weights files for the European 1000 genomes project phase 3 in hg38 were downloaded from the Alkes group ( Web Resources ).


## ChIP-seq peaks

ChIP-seq peaks from ENCODE 3 47 were downloaded on the UCSC Genome browser (tables encRegTfbsClustered and encRegTfbsClusteredSources) on April 25, 2022. Peaks were considered “liver TF peaks” if at least one of the listed sources was HepG2, liver, or hepatocyte (see Supplementary Table 3 for list of TFs).


## fpQTL motif matching

Position weight matrices (PWMs) for transcription factor motifs were downloaded from the JASPAR 2024 CORE non-redundant vertebrate database 48 . See Supplementary Table 4 for list of motifs and corresponding ChIP-seq TFs.

Motif scores were calculated by matching JASPAR motifs to a window around each SNP (for both the reference and alternate allele) using the motifmatchr 49 (v1.20.0) package, a wrapper for the MOODs 50 library. SNPs were removed from this analysis if the base in the hg38 sequence did not match the reference or alternate allele from genotyping (n=317 SNPs filtered, remaining # SNPs = 3,258,261). Windows were sized based on motif length, to guarantee that a matched motif would overlap the SNP. We defined an fpQTL-motif overlap to occur when an fpQTL overlapped both a motif and a liver ChIP-seq peak from the corresponding TF.


## Coordinate intersections

All coordinate intersections were calculated in R (v4.4.0) using GenomicRanges (v1.56.0). Coordinates were lifted between hg38 and hg19 as necessary using rtracklayer (v1.64.0).


## fpQTL enrichment with allele-specific ChIP-seq peaks

rsIDs for all fpQTLs were fed into the online tool ANANASTRA 51 , which calculates enrichment for SNPs within the ADASTRA 25 database for allele-specific ChIP-seq peaks, using the Local (1 Mb) background option.


## Calculation of Tn5 insertion density

To assess the general enrichment in chromatin accessibility near the ends of chromosomes, we divided the genome into bins with a width of 200 bp (the width that PRINT uses to calculate FP score). For each sample, we counted the number of Tn5 insertions in each bin using the fragment file. The first and last 10,000 bins on each chromosome (i.e. within 2 Mb of a chromosome end) were labeled “near-telomeric” bins, and the other bins were labeled “central”. We then averaged the number of insertions in non-empty near-telomeric and central bins to calculate the mean insertion density for these two regions.


## Inversion haplotyping

We used the scoreInvHap 52 (v1.20.0) R package ( https://rdrr.io/bioc/scoreInvHap/ ) to call inversion haplotypes using the genotypes of nearby SNPs. Data for the inversions called are included in the package.


## Correcting for Tn5 insertion bias when visualizing Tn5 insertions

For every variant in every sample, PRINT considers the Tn5 insertions at the x -th position within a 200 bp window around the variant. If Ox represents the observed cut sites at the x -th position in the sample, then we calculated the corrected cut sites C x in that sample as: where E x is the expected number of cutsites at position x calculated by: where bx is the Tn5 bias at the x- th position reported by PRINT, and and are the means of O x and b x calculated across all x positions within the 200 bp window.


## Results


## Discovery of liver fpQTLs in liver open chromatin

Using a human liver ATAC-seq dataset uniformly generated from 170 genotyped donors ( Figure S1A ), we first scored all common SNPs residing within open chromatin regions for their potential of TF footprints by calculating a footprint score (FP score) for each sample at every SNP position ( Materials and Methods, Figure 1A ). For each SNP, we then performed linear regression analysis to estimate the effect of change in genotype on FP score as the outcome, including covariates ( Materials and Methods , Figure 1B ). 693 SNPs exceeded an FDR q-value < 0.05 multiple-testing threshold and were labeled as fpQTLs ( Figure 2A , Supplementary Table 2 ).

When comparing fpQTL positions to the locations of gene transcription start sites (TSSs), we observed that TSS-proximal SNPs were more likely than distal SNPs to be detected as fpQTLs, and TSS-proximal fpQTLs had higher effect sizes than distal fpQTLs ( Figures 2B and 2C ). It has been shown previously that proximal loci are more likely to be in highly accessible chromatin and to have regulatory significance 53 , suggesting greater power to detect fpQTLs in TSS-proximal regions. As such, we reasoned that our observed enrichment was likely due to greater statistical power to detect, rather than proximal SNPs having a stronger effect on TF binding.

To account for systematic biases in ATAC-seq insertion across samples, we next considered the differences in insertion patterns on each allele within heterozygous samples. We predicted that for true fpQTLs, the allele associated with increased binding within heterozygous samples would also be associated with FP score across all samples. For each fpQTL, we calculated allelic footprint scores using insertions from the reference and alternate alleles separately within heterozygous samples ( Materials and Methods ). We observed that the difference between alternate and reference footprint scores was significantly correlated with fpQTL effect size in the expected direction ( Figure 2D ).


## fpQTL effects are concordant with TF binding motifs

For TFs with high-quality antibody availability, binding sites can be mapped with very high confidence using chromatin immunoprecipitation sequencing (ChIP-seq) data 54 . To assess the accuracy of our footprint binding detection, we compared the locations of our fpQTLs to known binding locations from liver ChIP-seq data in ENCODE 47 ( Materials and Methods ). After correcting for multiple testing, we observed that fpQTLs were over-represented in liver ChIP-seq peaks for 49 of the 121 TFs with available data. In particular, we observed enrichment for several TFs known to be associated with liver metabolism and disease, including HNF4A 55 (OR = 4.1, P = 6.6×10 -16 ), FOXA1 (OR = 2.6, P = 3.7×10 -5 ), FOXA2 56 (OR = 2.6, P = 1.5×10 -5 ), and JUND 57 (OR = 3.5, P = 1.1×10 -10 ) ( Supplementary Table 3 , Figures 3A and S3A ).

We next examined how fpQTLs altered the strength of binding motifs underlying these ChIP-seq peaks. Specifically, we assessed whether fpQTLs were “concordant” with the motifs they overlapped; that is, if the allele with the stronger motif match was associated with a higher FP score 25 . Among the fpQTL-motif overlaps that we identified at ChIP-seq peaks, a large proportion (181/227, 80%) were concordant ( Supplementary Table 4 , Figure 3B ; binomial P -value < 2.2×10 -16 ). Additionally, increasing the motif matching significance ( P -value) threshold by a factor of 10 increased this concordance proportion to 91% ( Figure S4 ). Furthermore, the allelic change in motif score was significantly correlated with the FP score-inferred change in TF binding ( Figure 3C , Spearman’s rho = 0.18, P -value = 5.8×10 -3 ), suggesting that variants with a larger impact on a given motif are more likely to be concordant.

To test our hypothesis that fpQTLs represent allele-specific binding, we compared our fpQTLs to SNPs which showed allele-specific ChIP-seq peaks in the ADASTRA 25 database. We found that our set of fpQTLs were significantly enriched for SNPs with allele-specific binding in ChIP-seq for HepG2 cells and liver ( Figure S3C ), suggesting that fpQTLs reflect true allele-specific binding effects. Taken together, these results suggest that fpQTLs influence TF binding strength by disrupting the binding sequence motif for the given TF.


## fpQTLs are significantly enriched in other liver QTLs and lipid GWAS signals

To assess the role of fpQTLs in regulating gene expression, we investigated the overlap of fpQTLs with genetic variation associated with expression in liver (i.e., liver eQTLs) from GTEx 8 , and caQTLs discovered using the same set of liver samples studied here. We observed a highly significant enrichment of fpQTLs for liver eQTLs (odds ratio = 4.01, P = 1.1×10 -20 ), and an even higher enrichment for caQTLs (odds ratio = 29.3, P < 2.2×10 -308 ; Supplementary Table 5 ). For the set of n=76 SNPs that were both fpQTLs and eQTLs, the allele associated with increased TF-binding was also associated with increased gene expression in 55 (72%) SNPs ( Figure S5A ). This suggests that most of the regulatory elements harboring fpQTLs act as enhancers of gene expression, where TF-binding promotes transcription, rather than as silencers. An even stronger directional correspondence was observed for chromatin accessibility, where 344 (93%) fpQTL/caQTLs act in the same direction, compared to only 27 in the opposite direction ( Figure S5B ).

We next queried if fpQTLs can account for a proportion of the characterized genetic component of disease. We examined the overlap of fpQTLs with lead SNPs and their LD proxies identified by liver-related GWAS ( Materials and Methods ). fpQTLs were significantly enriched for GWAS SNPs for four out of five lipid traits; however, we did not observe any fpQTLs overlapping with GWAS SNPs for BMI, T2D, or MASLD ( Supplementary Table 5 , Figure 4A ). However, fpQTLs were not depleted for any trait, suggesting that the lack of overlap is in part driven by the small number of fpQTLs (i.e., low statistical power).

Given that odds ratio enrichment tests do not take into account the LD structure of SNP associations, we also evaluated enrichment for disease heritability at fpQTLs using stratified LD score regression 58 . Despite observing very high estimated heritability enrichment for MASLD and lipid traits ( Figure 4B ), none of these tests were statistically significant given the fpQTL annotation was relatively small compared to the entire genome. However, the high heritability enrichment in traits without a high overlap with lead SNPs or proxies suggests that fpQTLs overlap several sub-significant signals which the GWAS were not powered to detect. Overall, the enrichment of fpQTLs with GWAS signals was much lower compared to enrichment with other forms of QTL.


## Greater chromatin accessibility increases power to detect fpQTLs

We also observed that the likelihood of a SNP being labelled as an fpQTL increased with the degree of openness of its chromatin peak. Indeed, fpQTLs are located within peaks with a higher average openness across samples (measured in ATAC-seq fragment counts per million, or CPM) compared to non-fpQTL SNPs ( Figure S6A ), and the measured effect size and significance of fpQTLs is significantly correlated with the average number of Tn5 insertions near the fpQTL ( Figures S6B and S6C ). We hypothesize that this effect is due to both (i) enrichment of functional significance in highly accessible regions 58 – 60 , and (ii) greater power to detect footprint activity when PRINT can consider more Tn5 insertions to calculate FP score. For example, if a TF-bound SNP is located in a relatively inaccessible peak, then the lack of local insertions will prevent PRINT from confidently assigning a high FP score, despite the presence of a TF.

We next tested whether chromatin accessibility increases fpQTL power or if this effect is driven solely by increased functional activity within highly accessible peaks. We elected to measure the relationship between the average number of insertions near a SNP and its average FP score across samples. We observed that high insertion counts corresponded to higher FP scores even after removing SNPs with known regulatory function ( Figures S6D-F ). This observation suggests that PRINT skews towards assigning higher FP scores to SNPs near more insertions, regardless of functional activity.

The increase in fpQTL power due to chromatin accessibility explains our observation that fpQTLs are enriched nearer the ends of chromosomes, closer to the telomeres. Of SNPs within 2 Mb of the chromosome ends, 130 (0.08%) are fpQTLs, compared to 563 (0.02%) for the more central SNPs (odds ratio = 4.3, Fisher’s P -value < 2.2×10 -16 ). These “telomeric-neighboring” regions were in fact not enriched for the ChIP-seq peaks of any TF, which therefore did not explain the high concentration of fpQTLs at these locations. Instead, we hypothesize that telomeric-neighboring regions are enriched for fpQTLs because they are more accessible on average than other regions, therefore increasing fpQTL detection power. Indeed, telomeric-neighboring regions (within 2 Mb of chromosome ends) had significantly higher insertion density compared to central regions in all of our liver ATAC-seq samples ( Figure S7A ). fpQTLs in these telomeric-neighboring regions resided in peaks with a significantly higher mean CPM and were flanked by a higher number of Tn5 insertions ( Figures S7B and S7C ).

In addition to an enrichment of fpQTLs near the ends of chromosomes, the fpQTL Manhattan plot showed a highly significant signal on chromosome 17, which we mapped to a known common inversion at the 17q21.31 locus 61 . Calling inversion haplotypes on our samples and including them in the regression revealed that the significant SNPs on the ends of the inversion were tagging the inversion itself, potentially altering TF binding at its boundary regions. Additionally, this correction revealed four SNPs within the inversion associated with TF binding ( Figure S8 ). Indeed, this inversion has been implicated in HDL lipid levels and other obesity related traits 62 , along with brain morphology and neuroticism 63 , 64 .


## fpQTLs can be used to fine-map GWAS loci

Unlike GWAS and other forms of QTLs, the trait tested against each SNP in fpQTL discovery (footprint score) is different at every SNP, meaning test statistics between nearby SNPs are not correlated due to LD. As a result, fpQTLs provide single-SNP resolution to fine-map GWAS loci or QTLs by pinpointing a putatively causal SNP among a credible set of GWAS/QTL variants. To explore the fine-mapping ability of fpQTLs, we examined GWAS loci for liver traits harboring at least one significant fpQTL.

First, we examined the lipid-associated SORT1 locus, which has been extensively studied through experimental validation to determine that the association is driven specifically by rs12740374, creating a TF binding site 65 , 66 . Our fpQTL results identified the same SNP as the causal variant, given rs12740374 was the most significant at the locus ( Figures 5A and 5B ). Assessing the bias-corrected insertions around rs12740374 (see Materials and Methods for insertion corrections), samples with the alternate allele showed a strong depletion of insertions directly adjacent to the variant, suggesting a genotype-dependent binding event consistent with previous results 65 ( Figure 5C ). This rediscovery of a known causal SNP supports the hypothesis that fpQTL discovery can be a powerful tool in fine-mapping.

We next sought to investigate fpQTLs which could explain less defined GWAS loci. At the lipid (LDL)-associated ZFPM1 locus, the fpQTL rs55823018 was by far the most significant compared to adjacent SNPs in partial LD ( Figure 5D ). This SNP increased TF binding and resided in a ChIP-seq peak for the Retinoid X receptor alpha (RXRA), and concordantly increased the matching strength of the underlying NR1H4::RXRA sequence motif. A second instance was observed at the lipid-associated SLC12A8 locus, where the fpQTL rs11710930 overlapped a ChIP-seq peak for hepatocyte nuclear factor 4 alpha (HNF4A) and was concordant for the underlying motif ( Figure 5E ). HNF4A is well-established as an important TF for liver function, and has been previously implicated in liver dysregulation 55 , 67 – 69 . Furthermore, SLC12A8 has been implicated as an effector gene for T2D risk 70 , but the role of this locus in lipid levels remains to be investigated. Taken together with orthogonal ChIP-seq and eQTL results, our fpQTL method adds to the confluence of evidence implicating this specific variant as causal for increased lipid levels.


## Discussion

A significant limitation to GWAS and QTL studies is the unwieldy number of candidate causal variants due to constraints of LD, making it challenging to pinpoint which among them is truly causal. Here, we leveraged statistical inference of TF binding likelihood from experimental data at base-pair resolution to discover fpQTLs, i.e., variants associated with TF binding. We showed that liver fpQTLs were concentrated in ChIP-seq peaks, eQTLs, caQTLs, and lipid-associated loci. Additionally, the vast majority of fpQTLs were concordant with underlying sequence motifs, increasing our confidence that fpQTLs represent SNPs that are very likely to be causal for TF binding differences. We also observed specific examples of GWAS loci where fpQTL discovery implicated both a causal variant and a corresponding disrupted TF binding motif.

The main limitation of this study was the high level of noise in ATAC-seq insertion positions, resulting in high variance in footprint score despite our large read count. Additionally, we used ATAC-seq data from bulk tissue samples rather than single-cell samples, which may mask footprint signals that only occur in a specific cell type. However, given the majority (60%) of liver cells are hepatocytes 71 , we are likely capturing most of the footprint signals from hepatocytes without introducing false signals from mixed cell types. Furthermore, our fpQTL discovery did not consider the effect that each SNP could have on the Tn5 sequence bias, which weakly influences the positions where Tn5 is inserted 16 , 72 . PRINT corrects for this Tn5 sequence bias, but relies on the reference genome, and so the bias of the alternative allele is not considered. Another limitation of this fpQTL discovery effort was the lack of enrichment in several relevant GWAS traits, limiting their ability to explain disease associations. We propose that this is due to systematic differences between QTL and GWAS discovery. A recent study showed that compared to eQTL signals, GWAS signals are further away from transcription start sites and tend to be near genes under strong selective constraint with more complicated regulatory landscapes 10 . This published model suggests that regulatory variants targeting genes with large trait effects (detected by GWAS) will be less frequent due to natural selection, therefore reducing QTL detection power. Under this model, fpQTL discovery would be similarly hindered at genes with large trait effects, leading to less GWAS enrichment.

Curiously, all of our ATAC-seq samples showed greater Tn5 insertion density in telomeric-neighboring regions compared to other regions. This warrants further investigation to (1) assess the consistency of this phenomenon across cell types and experimental parameters, (2) understand the implication for this bias in peak-calling and multiple-testing correction due to changes in power, and (3) determine the source of this bias, whether technical or biological. However, we deemed these questions outside the scope of our current investigation.

Our results demonstrate that fpQTL characterization enables the capture of genetically regulated TF binding signals in human liver with a resolution not constrained by LD patterns. The approach therefore has the potential to identify regulatory SNPs among trait-associated loci from GWAS or QTL studies, which typically harbor many variants in LD with the causal SNP. fpQTLs also suggest transcription factor binding as the mechanism by which non-coding GWAS variants affect disease risk. Overall, our map of genotype-dependent TF binding sites is a valuable resource for understanding the genetic etiology of complex traits in the context of liver. By implicating specific regulatory elements in these liver-related traits, our fpQTL discovery method should improve research aimed at developing novel therapies by prioritizing variants and TFs for further experimental study. Furthermore, this method can be equally applied to other tissues and cell types, expanding the number of genetic traits that can be addressed.


## Author contributions

C.D.B. and M.F.D. conceptualized the method. B.M.W. generated and processed the ATAC-seq libraries. M.F.D. performed the data analysis and wrote the manuscript. B.M.W., L.A., and S.F.A.G. reviewed the manuscript and contributed to the statistical methodology. C.D.B is credited posthumously; all other authors read and approved the final manuscript.


## Declaration of interests

The authors declare no competing interests.


## Web Resources

PRINT: https://github.com/HYsxe/PRINT

- Fragment extraction: https://github.com/HYsxe/PRINT/issues/6

- Vignette: https://github.com/HYsxe/PRINT/blob/main/analyses/BMMCTutorial/BMMCVignette.pdf

Genrich (v0.6.1): https://github.com/jsh58/Genrich

GTEx Portal (v8): https://gtexportal.org/home/downloads/adult-gtex/overview JASPAR (2024): https://jaspar.elixir.no

SNiPA (v3.4): https://snipa.org/snipa3/

LDSC (v1.0.1): http://www.github.com/bulik/ldsc

- Data files download: https://console.cloud.google.com/storage/browser/broad-alkesgroup-public-requester-pays/LDSCORE

ANANASTRA (Bill Cipher v5.1.3): https://ananastra.autosome.org/


## Data and code availability

Raw sequencing files for the ATAC-seq samples used in this study have been uploaded to GEO and will be available upon publication. The FP score matrix, genotype matrix, and full fpQTL summary statistics have been uploaded to Zenodo [pending publication, available upon reasonable request]. All intermediate files used in this analysis are available upon request. All code used to process the ATAC-seq samples, run fpQTL discovery, and produce the figures in this manuscript are available on GitHub at https://github.com/maxdudek/fpQTL .


## Supplementary Figures


## Acknowledgments

We thank all members of the Grant and Almasy labs for their feedback on this project. We thank Matt Pahl and Khanh Trang for their assistance running ldsc. We thank Iain Matheson for feedback on this manuscript as well as for sitting on the thesis committee of M.F.D., along with Klaus H. Kaestner and Alexis Battle. We would especially like to acknowledge the mentorship of Christopher D. Brown, who passed soon after this study began, and without whom it would not have been possible. M.F.D. is supported by the National Science Foundation Graduate Research Fellowship Program (NSF GRFP). C.D.B. is funded by R01 HL133218. L.A. is funded by NIAAA U10 AA008401. B.F.V. gratefully acknowledges support from the NIH/NIDDK (UM1 DK126194 and U24 DK138512). S.F.A.G. is funded by UM1 DK126194, R01 HD056465 and the Daniel B. Burke Endowed Chair for Diabetes Research.


## Footnotes

https://github.com/maxdudek/fpQTL