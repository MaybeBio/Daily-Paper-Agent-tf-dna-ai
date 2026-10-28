## Abstract

Background and Objectives Mixed-field agglutination in ABO phenotyping (A 3 , B 3 ) has been linked to genetically different blood cell populations like in chimerism, or to rare variants in either ABO exon 7 or regulatory regions. Clarification of such cases is challenging and would greatly benefit from sequencing technologies that allow resolving full-gene haplotypes at high resolution.

Materials and Methods We used long-read sequencing by Oxford Nanopore Technologies to sequence the entire ABO gene, amplified in two overlapping long-range PCR fragments, in a blood donor presented with A 3 B phenotype. Confirmation analyses were carried out by Sanger sequencing and included samples from other family members.

Results Our data revealed a novel heterozygous g.10924C>A variant on the ABO*A -allele located in the transcription factor binding site for RUNX1 in intron 1 (+5.8 kb site). Inheritance was shown by the results of the donor’s mother, who shared the novel variant and the anti-A specific mixed-field agglutination.

Conclusion We discovered a regulatory variant in the 8-bp RUNX1 motif of ABO , which extends current knowledge of three other variants affecting the same motif and also leading to A 3 or B 3 phenotypes. Overall, long-range PCR combined with nanopore sequencing proved powerful and showed great potential as emerging strategy for resolving cases with cryptic ABO phenotypes.


## Introduction

Reduced activity of the ABO glycosyltransferase protein is in the vast majority of cases caused by single nucleotide variants (SNVs) in exonic and splice site regions of the ABO gene[ 1 ]. However, a particular complex phenotype of reduced activity, the so-called A 3 or B 3 phenotype, which presents as a mixed-field agglutination with anti-A or anti-B, can also be caused by variation in ABO regulatory elements located in flanking or intronic regions of the gene[ 2 ]. Standard diagnostic workflows often fail to detect these variants, as sequencing is typically limited to exons. Correctly characterizing A 3 and B 3 phenotypes is made even more challenging since mixed-field agglutination can also be caused by either chimerism (i.e., the presence of allogenic blood cells as a consequence of twin pregnancy[ 3 ], recent transfusion, or stem cell transplantation) or hematopoietic mosaicism[ 4 ]. To unambiguously resolve such cases, additional laborious methods like digital PCR (dPCR) or sequencing to a high read-depth using short- or long-read sequencing need to be performed.

Latest third-generation long-read sequencing by Oxford Nanopore Technologies (ONT) has the potential to resolve these complex weak ABO phenotypes. In combination with long-range PCR[ 5 ], this method enables the generation of fully resolved haplotypes of the entire gene including flanking regions. Additionally, high read-depth obtained by amplicon sequencing allows identifying cases of chimerism or mosaicism by facilitating variant calling in subclonal cell populations. Here, we describe the case of a 23-year-old female blood donor presenting with an A 3 B phenotype. Sequencing the entire ABO gene with ONT, we found an unknown SNV affecting the RUNX1 motif in the regulatory 5.8 kb site in ABO intron 1. Causality for the observed phenotype was corroborated by additional analyses in the index case as well as other family members.


## Materials and Methods

The ABO phenotype of the blood donor was determined by standard serological methods for ABH including gel cards (Grifols, Spain) and tube tests (Bio-Rad, Switzerland), as well as by anti-A 1 and anti-H specific agglutination (Bio-Rad Seraclone, Switzerland). Genotyping of main ABO variants was carried out by commercially available kits (Inno-train, Germany) based on PCR with sequence-specific primers (PCR-SSP). Presence of A- and B-antigen on erythrocytes was quantified on a FACSCanto II flow cytometer (BD Biosciences, Switzerland) using monoclonal IgM antibodies (anti-A and anti-B from clones BIRMA-1 and LB-2, respectively). Potential chimerism was investigated by analysing the allelic distribution of 24 genetic variants across the genome using dPCR (Stilla, France). The entire ABO gene including flanking regions was amplified by two overlapping long-range PCRs (∼16 and ∼13 kb, respectively) and sequenced on part of a MinION R9.4 flowcell (ONT). Both ONT sequencing and bioinformatical analyses were carried out as described recently[ 5 ]. Nanopore sequencing results were verified by Sanger sequencing of all seven ABO exons as well as the identified candidate region containing the RUNX1 motif in intron 1. To elucidate a somatic versus germline origin of the identified candidate variant, we extended phenotypic and genetic analyses to the donor’s mother and brother. Sanger sequencing was limited to the candidate region in intron 1.


## Results

Genotyped as ABO*A1 and ABO*B by PCR-SSP, the proband’s forward phenotyping showed a double population in the agglutination with anti-A and strong reactions with anti-B and anti-AB ( Table 1 ). Agglutination with anti-H and anti-A 1 was weak and absent, respectively. All observations were in agreement with an A 3 B phenotype. Flow cytometry revealed that ∼80% of erythrocytes lacked the A-antigen. No sign of chimerism was identified by dPCR.

To resolve the genetic basis of the observed A 3 B phenotype, we sequenced the entire ABO gene. Read depth of nanopore sequencing exceeded 10,000x for both PCR amplicons allowing variant calling in subclonal cell populations. Genetic variation in the overlapping region of PCR amplicons enabled read-based phasing of all genetic variants across the entire gene. As expected, one of the two ABO haplotypes corresponded to an ABO*B allele, comprising all seven ABO*B . 01 defining exonic SNVs. They were all heterozygous. The second haplotype was identified as an ABO*A1 allele. No exonic variant was found that would explain the mixed-field agglutination. However, we discovered on this haplotype a novel C>A variant at NG_006669.2:g.10924 (alternatively: NM_020469.3:c.28+5871C>A), located in a known transcription factor binding site for RUNX1 in the +5.8 kb site of intron 1 ( Figure 1 )[ 6 ].

To further exclude the non-inherited phenomena of chimerism and mosaicism as a possible explanation for the A 3 B phenotype, we also analysed the proband’s mother and brother. The mother was genotyped ABO*A1 / ABO*O . 01 by PCR-SSP and also showed a mixed-field agglutination with anti-A ( Table 1 ). Compared to her daughter, the proportion of erythrocytes presenting A-antigen was higher (∼35%). This may support the allelic enhancement hypothesis, i.e. the assumption that the in-trans allele impacts the expression level of the weak allele[ 7 , 8 ]. Sanger sequencing confirmed the heterozygous presence of the novel variant NG_006669.2:g.10924C>A in the RUNX1 binding site. As expected, the brother, who was genotyped as ABO*O . 01 / ABO*O . 01 , did not show any variation in the RUNX1 motif ( Table 1 ).


## Discussion

We resolved the genetic basis of an elusive A 3 phenotype using latest third-generating long-read sequencing. In light of the diverse sources for phenotypes of mixed-field agglutination, including genetic variants in exonic regions, regulatory elements and subclonal cell populations, we employed nanopore sequencing as our method of choice. In combination with long-range PCR, this sequencing technology allowed to comprehensively investigate the complete ABO gene at high read-depth as well as constructing entire ABO haplotypes. Our approach revealed a novel regulatory variant in the RUNX1 binding site of the ABO intron 1 underlying the observed A 3 phenotype.

Typically, assessing causality for an expression-linked variant would require additional experiments like reporter gene assays or electrophoretic mobility shift assays[ 9 ]. However, in this particular case, the available evidence strongly supports the causal association. First, the presence of genetically different cell populations was excluded by dPCR and by the observed heritability of the cryptic phenotype. As a consequence, additional analyses like identifying variants in subclonal cell populations were no longer necessary. Second, beside the ABO*B . 01 defining SNVs, no variants were detected in the coding or splice site regions of the ABO gene. Third, the identified intronic C>A variant is exceedingly rare based on its absence in large databases like dbSNP, lied on the haplotype representing an ABO*A1 allele and was inherited along with the A 3 phenotype from the mother. Finally, and most convincingly, three SNVs targeting the core consensus sequence[ 6 ] (5’-CCACA-3’, Figure 1 ) of the 8-bp RUNX1 binding site had already been reported previously and had experimentally been shown to be causative for A 3 and B 3 phenotypes ( Table 2a )[ 8 , 10 , 11 ]. While our understanding of the mutational consequences at positions outside the core element remains limited ( Table 2a ), it is noteworthy that variants in the direct vicinity have been reported to cause the same phenotype ( Table 2b )[ 8 , 12 ]. Interestingly, the deletion of the entire RUNX1 motif results in stronger A m or B m phenotypes ( Table 2a )[ 9 , 13 , 14 ], characterised by complete absence of the respective A or B-antigen on erythrocytes. Other cell types, however, are not affected as this regulatory motif acts in an erythroid-specific manner. Accordingly, there is no formation of isoagglutinins in these phenotypes.

Overall, long-read sequencing greatly simplified the discovery of the causal variant of the observed A 3 phenotype as it enabled the efficient investigation of the complete ABO gene, including regulatory sites in introns and flanking regions. Such regulatory regions may often be either unknown or overlooked, and consequently not covered by standard approaches like Sanger sequencing. Of note, variants affecting the RUNX1 motif in the ABO gene had so far almost exclusively been reported from East Asian populations ( Table 2 ) and were never transferred to public databases for blood group alleles[ 1 ] or for clinically relevant variant data (e.g. ClinVar). Lack of submission to appropriate databases unfortunately hampers knowledge dissemination and may foster incomprehensive investigation of such weak or cryptic phenotypes.

In summary, we detected a novel regulatory variant in the ABO RUNX1 binding site in intron 1 by ONT sequencing. The resulting A 3 phenotype adds to the growing knowledge on mutational consequences in this regulatory element. More broadly, long-range PCR combined with long-read sequencing represents a promising strategy to generally resolve cases with cryptic ABO phenotypes.


## Conflict of Interest

None of the authors declares any conflicts of interest.


## Funding Information

This work was financially supported by the Blood Transfusion Service Zurich SRC (Switzerland).


## Data Availability Statement

A 402 bp region of the +5.8 kb site of ABO intron 1, causative for ABO blood group phenotype A 3 , has been submitted to GenBank (accession number OP479978 ) . The identified variant has been submitted to ClinVar (accession number VCV001707607.1).


## Acknowledgements

S.M. and M.P.M.-G. designed the study, supervised the data analysis and reviewed and edited the manuscript. G.A.T. and M.G. performed the experiments, analysed the data and wrote the manuscript. S.S., E.M, E.G., L.S., Y.M., N.T. and K.N. contributed to experiments. C.E. and B.M.F. contributed to the design of the study and facilitated sample acquirement. All authors read and approved the final manuscript.

We thank the proband’s mother and brother for their willingness to donate blood for research purpose.