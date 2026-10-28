# Promoter recognition specificity of Corynebacterium glutamicum stress response sigma factors σD and σH deciphered using computer modeling and point mutagenesis


## Supplementary Information
  The online version contains supplementary material available at 10.1007/s10822-024-00577-x.


## Introduction
  Corynebacterium glutamicum is a non-sporulating gram-positive soil bacterium belonging to actinobacteria. Since its isolation in 1957 in Japan, C. glutamicum has been widely used as an industrial producer of amino acids and other useful substances such as diamines, carboxylic acids, polymers or biofuels [1, 2]. Strains of C. glutamicum also serve as expression systems for the production of heterologous proteins [3]. Due to their importance in biotechnology, production strains were bred both by classical and molecular methods. Regulation of transcription in C. glutamicum was studied in detail and its complete genome was finally sequenced [4].

  Bacterial transcription is catalyzed by the RNA polymerase (RNAP) holoenzyme that consists of the multi-subunit core enzyme and an additional subunit called the sigma factor. Sigma factors are responsible for the recognition of promoters, local melting of dsDNA strands, and initiation of transcription [5].

  C. glutamicum genome encodes 7 sigma factors (σA, σB, σC, σD, σE, σH, and σM) [6]. All of them belong to the σ70-related family. Primary factor σA, the only member of group 1 is responsible for transcription of housekeeping genes [6, 7]. Primary-like σB (group 2) is active mainly during the transition from exponential growth to stationary phase and in general stress response conditions [8]. Extra-cytoplasmic function (ECF) sigma factors σC, σD, σE, σH, and σM of group 4 are involved in various cell responses to stress [6].

  The DNA sequence where RNAP binds and starts the transcription is called a promoter. Most of the bacterial promoters (housekeeping, vegetative) that are active during exponential growth are recognized by σA or less by σB. They have two essential sequence elements (−35 and −10) that are mostly separated by the spacer with a length of 16–18 nucleotides. In most cases, the −10 element is AT-rich which allows the melting of the DNA double helix during the initiation of transcription [9–11]. The other promoters recognized by alternative σ factors have also two sequence elements (called generally −35 and −10 as well) that are variable, but highly conserved depending on the σ factor in control.

  Different consensus nucleotide sequences of the −35 and −10 elements are thus recognized by various σ subunits with conserved amino acids that interact with particular nucleotides of the promoters. More specifically, the σ4.2 domain binds to the −35 element and the σ2.4 domain binds to the −10 element [12]. Despite substantial differences regarding the amino acid sequences of various σ subunits, the spatial arrangement of the σ4.2 and σ2.4 domains is highly conserved.

  Although the number of crystal and cryo-EM structures of σ factors from various bacteria in the Protein Data Bank is steadily increasing, it has not yet been sufficiently elucidated which specific amino acids of σ subunits are crucial for the sequence-specific recognition of −10 and −35 promoter elements of various promoters in C. glutamicum.

  We have long been interested in the functions of the stress subunits σH and σD of RNAP and the corresponding promoters in C. glutamicum (Busche et al., 2012; Taniguchi et al., 2017). Regarding σH-dependent promoters, the GGAAT nucleotide sequence is typical in the −35 element and the consensus GTT sequence is usually found in the −10 element. The N18–20 spacer separates these elements. The analogous −35 and −10 elements of σD-dependent promoters show the consensus sequence GTAAC-N18–20-GAT. In our previous study [13], we analyzed using computer modeling and point mutagenesis the naturally occurring hybrid σHD-dependent C. glutamicum promoter Pcg0607, having the GGAAC sequence (as a σH-dependent promoter; σH-matching) in the −35 element, and the GAT sequence (as a σD-dependent promoter) in the −10 element. As expected, we found that the Lys-53-Ala mutation (transforming σH protein closer toward σD) in the domain recognizing the σD-like GAT in the −10 region of the Pcg0607 promoter resulted in substantially increased transcription with σD. The 168-AlaValArgValAla-172 mutation in σH (i.e. again towards σD) in the domain recognizing the σH-matching −35 element GGAAC of the Pcg0607 promoter prevented transcription [13], in agreement with our assumption.

  Here we followed up on our previous study [13] with the efforts to elucidate the contradictory points. We focused on another naturally occurring σD/σH-dependent hybrid promoter Pcg0441, which has the CTAACG sequence close to the σD consensus at the −35 element and GTT that is σH consensus. We studied transcription from this promotor using a set of systematically mutated σH subunits designed based on computer modeling. Similarly, we analyzed in detail transcription from canonical σD-dependent (PrsdA) and σH-dependent (PuvrD3) promoters. Finally, we created an artificial hybrid promoter combining the −10 element from the PuvrD3 promoter and the −35 element from the PrsdA promoter. This artificial hybrid promoter showed almost optimal properties in terms of bio-orthogonal transcription.


## Materials and methods

### Strains and cultivation conditions
  The strain Escherichia coli TOP10 (Thermo Fisher Scientific Inc.) was used for cloning purposes. Wild-type strain Corynebacterium glutamicum ATCC 13032 was used as a host for the construction of two-plasmid clones containing pEPR1- and pEC-XT99A-derived recombinant plasmids. Plasmid PEPR1 [14] served as a promoter test vector and plasmid pEC-XT99A [15] served as an expression vector. E. coli was cultivated at 37 °C and C. glutamicum was cultivated at 30 °C, both in 2xYT medium or on 2xYT agar plates [16]


### DNA manipulations
  PCR, plasmid DNA isolation, restriction enzyme digestion, ligation, and transformation of strains of E. coli were performed by using standard techniques [17]. Strains of C. glutamicum were transformed using electroporation [18]. In the case of the development of two-plasmid systems in C. glutamicum, the plates of 2 × YT medium were supplemented with tetracycline (5 µg/ml) and kanamycin (20 µg/ml) for selection of the transformants. DNA fragments for cloning promoters in pEPR1 were constructed of hybridized nucleotides with overhangs ready for ligation with vector digested by restriction enzymes BamHI and NsiI (New England Biolabs Inc.). Mutations in the sigH gene were performed by using the Q5 Site-Directed Mutagenesis Kit (New England Biolabs Inc.) according to the user guide of the manufacturer.


### Mutagenesis
  All mutated sigH genes were produced using Q5® Site-Directed Mutagenesis Kit (New England BioLabs. Inc.) according to instructions of the manufacturer. PCR amplicons were produced with Q5 Hot Start High-Fidelity 2X Master Mix and appropriate oligonucleotide primers. The oligonucleotides for the mutagenesis were designed using the NEB online primer design software NEBaseChanger™ (NEBaseChanger.neb.com) and listed in supplementary Table 1S. The plasmids based on expression vector pEC-XT99A carrying the native sigH gene from C. glutamicum or its mutants were used as templates. Expression plasmids pEC-XT99A + x (x = sigH, sigH_4aa, sigH_6aa, σH_4aa_K and σH_6aa_K, respectively) were thus constructed.


### Promoter activity assay with two-plasmid C. glutamicum clones
  To measure the promoter activity, a fluorescence intensity assay was used [19]. C. glutamicum culture inoculated in 2YT medium with antibiotics (30 µg/ml kanamycin, 10 µg/ml tetracycline) grown for 20 h at 30 °C was diluted into OD600 = 0.1. The cells were then cultivated on a shaker at 30 °C to OD600 = 1.0. After reaching OD600 = 1.0, approximately 15 ml of culture was taken from the flask to determine the "baseline specific fluorescence intensity" value. 30 ml of culture was then transferred to a new culture flask and supplemented with IPTG (time 0, fin. conc. 1 mM) for induction. The remaining culture was further cultured as a control of a non-induced sample.

  Cells were harvested 3, 6, and 24 h after adding IPTG. Each harvest contained 7.2 mg of dry biomass. The sample was washed in PBS buffer supplemented with 1 mM phenylmethylsulfonyl fluoride (PMSF). All samples were homogenized by glass beads using FastPrepTm (MP Biomedical; 3 × 60 s at speed 6 m/s with Lysing Matrix B in 2-ml tubes). Homogenized samples were centrifuged and the supernatant was transferred into 96-well plate Nunclone™ Delta Surface and the fluorescence intensity was determined using a Saphire2 microplate spectrophotometer (Tecan; excitation wavelength 397 nm; emission wavelength 509 nm, excitation bandwidth 5 nm, emission bandwidth 20 nm, shake duration 5 s, settle time 10 s, read mode – bottom and integration time 40 µs). The protein concentration was determined using Bradford assays [20].


### Homology modeling and molecular dynamics simulations
  The homology models of the σH and σD domains which recognize the −10 and −35 nucleotide sequences of the respective promoters were produced by using the Swiss-Model server [21]. The crystal structures of E. coli σE, PDBid: 4LUP (for −10 element GTC) [22], and PDBid: 2H27 (for −35 element GGAAC) [23] were used as templates. The nucleotides within the consensus of the E. coli σE-dependent promoters were replaced to match the consensus for C. glutamicum σH- or σD-dependent promoters, where necessary. Molecular dynamics (MD) simulations were done using the software package AMBER [24] and Linux computer nodes with powerful NVIDIA GPUs that enable the accumulation of 800-ns MD trajectories at 280 K.


## Results

### Choice of promoters and design of nucleotide alterations
  In our previous study [13], we analyzed using computer modeling and point mutagenesis the naturally occurring H35D10-hybrid promoter Pcg0607, having the σH-matching sequence GGAAC in the −35 element and the σD-matching GAT sequence in the −10 element (Table 1). The 168-AlaValArgValAla-172 mutation in σH in the domain recognizing the σH-matching −35 element GGAAC of the Pcg0607 promoter (to make it more σD-like) prevented transcription [13]. In other words, the naturally occurring H35D10 hybrid promoter Pcg0607 was not recognized by the artificially constructed hybrid σD35H10 subunit.Table 1Nucleotide sequence of promoters used in this studyGenNucleotide sequencecg0607TTGCGCGTTAATAAGGAACAATATCGGTGTGATTCGCGATATATTAATCAH35D10cg0441 (lpd)ATTTCGGCAGAGTGCTAACGGTTAGGCACTATTTTCCGTTAGTTCTTTTGD35H10uvrD3TTTAACCGCTATCTGGAATGATTGATAGCTCCCAAGTGTTGTATCTATTCσH-deprsdAGGTCAGCGATGGAAGTAACAGAGTTAGGGAACTTCTCGATCTACTGAGTGσD-deprsdA_uvrD3GGTCAGCGATGGAAGTAACAGAGTTAGGGTCCCAAGTGTTGTATCTATTCD35H10The conserved promoter −35 and −10 motifs are in bold underlined letters

  These results led us to the idea that this σD35H10 subunit could be used for transcription from artificial D35H10 hybrid promoters. In the best-case scenario, this hybrid promoter would be recognized neither by the σD nor σH native subunits and the transcription with the artificial σD35H10 subunit would therefore be bio-orthogonal (not disturbing natural biological processes).

  First, we focused on the naturally occurring D35H10 hybrid promoter Pcg0441 (Table 1, Fig. 1), which has the CTAAC sequence close to the σD-matching consensus (GTAAC) at the −35 element. Regarding the −10 element, the GTT sequence of Pcg0441 corresponds to the σH-matching consensus promoter. Further, we analyzed in detail transcription from canonical σH-dependent PuvrD3 and σD-dependent PrsdA promoters (Table 1, Fig. 1). Regarding σH-dependent promoters, the GGAAT/N18–20/GTT sequence is nearly completely conserved in the −35/spacer/ −10 sequence (Fig. S1). The analogous −35 and −10 elements of σD-dependent promoters show the consensus sequence GTAAC-N17–18-GAT.Fig. 1Duplexes consisting of 11 base pairs spanning positions −37 to −27 from the Pcg0441, PuvrD3, and PrsdA promoters. Color code: Adenine—red, Thymine—pink, Guanine—blue, Cytosine—cyan

  Finally, we created an artificial D35H10 hybrid promoter combining the −35 element from the σD-dependent PrsdA promoter and the −10 element from the σH-dependent PuvrD3 promoter (Table 1). Therefore, this promoter is hereinafter called the artificial D35H10 hybrid promoter PD35-rsdAH10-uvrD3.


### Design and creation of hybrid σD35H10 from σH by point mutagenesis
  Transcription from the tested promoters (Table 1) was studied using a set of systematically mutated σH subunits (see Table 2, Fig. 2) designed on the base of computer modeling. These mutations are located in region 4 of σH-based subunits which interacts with the −35 element. To avoid any confusion, amino acids through the following text are numbered according to C. glutamicum σH to highlight which amino acids are in spatially equivalent positions. For slightly shifted (2 aa) numbering of C. glutamicum σD subunit see Fig. 5 in [13], where sequence alignment with E. coli σE region 4 can be found as well (its structure PDB id: 2H27 served as a template for our homology models).Table 2Set of mutations in the region 4 of the sigH geneSigma factorName of mutationSequence changeH4AAT168M170S171R172 → A168R170V171A172H4AA + KE140 T168M170S171R172 → K140 A168R170V171A172H6AAP165L166T168M170S171R172 → T165P166A168R170V171A172H6AA + KE140 P165L166T168M170S171R172 → K140 T165P166A168R170V171A172Amino acids are numbered according to C. glutamicum σH to highlight which amino acids are in spatially equivalent positionsFig. 2Domains 4.2 of mutant σH subunits interacting with the −35 elements of the studied promoters. σH amino acids have red labels, and mutated amino acids have blue labels. Labels of amino acids that appeared to be particularly significant in MD simulations are highlighted in bold. For clarity, the amino acids are shown separately: (top) those distinguishing the 4aa and 6aa mutants; (middle) amino acids from the initial 4aa mutation set that were mutated in all cases; (bottom) the amino acid at position 140, where K140 is supposed to compensate for the R172 to A172 mutation. Next, the crucial R175, which interacts with the nucleotide in position −34, and the basic amino acids K178, R171, R177, and K156, which are important for the interaction with the sugar-phosphate backbone of the nucleic acids


### Mutations

#### σH_4aa
  First, the σD35H10 mutant from our previous study [13] was used. In this mutant, a set of amino acids 168-ThrValMetSerArg-172 in σH was replaced by 168-AlaValArgValAla-172 in the central helix of the σH domain which recognizes the −35 element [13]. Since V169 was not mutated, a total of just 4 amino acids were changed. Therefore, this mutant is hereinafter referred to as σH_4aa. This variant was thought to be more σD-like. Further mutations aimed to create an σD35H10 mutant, which is even more σD-like in the −35 binding region.


#### σH_4aa_K
  Our computer models based on Pcg0607 and the σH_4aa mutant showed that the positively charged basic amino acid R172 in σH, which was altered to provide σH_4aa mutant, significantly interacted with the negatively charged phosphate groups in the sugar-phosphate backbone of the non-template-strand-of-DNA and formed thus salt bridges. Further, the model of a complex involving the σD subunit and Pcg0607 showed that another basic amino acid K140 in σD interacted with the identical phosphate groups as R172 in σH. Interestingly, K140 of σD is situated outside the central helix, but its long and flexible side chain points to the same location as R172 in σH.

  Therefore, we decided to create the σD35H10 variant, where in addition to the four amino acids mentioned above, the amino acid E140 was replaced by K140. This mutant is hereinafter referred to as σH_4aa_K.


#### σH_6aa
  Two other amino acids in σH (T165, P166) and in σD (P165, L166) near the mutated σH sequence 168–172, are not conserved between σH and σD. These amino acids undergo close contact with the non-template strand of DNA. Therefore, we created another σD35H10 mutant, having a total of six amino acids altered. The amino acids 165-ProLeuGlyThrValMetSerArg-172 in σH were thus replaced by 165-ThrProGlyAlaValArgValAla-172 in this mutant named σH_6aa. Note that Gly167 and Val169 are in both sigma subunits, and therefore, a total of just 6 amino acids were changed. Further, both hydroxyl groups of T168 and T165 aim for the same phosphate group of DNA. So the corresponding mutation at position 165 (Pro-165-Thr) was to ensure that the resulting mutant was not weakened compared to the parent σH when Thr168 was exchanged.


#### σH_6aa_K
  Finally, we merged all point mutations mentioned above in a construct hereinafter referred to as σH_6aa_K.

  To summarize, this study involves in total four promoters: Pcg0441, PuvrD3, PrsdA, and PD35-rsdAH10-uvrD3 (Table 1), and six different σ subunits: σD, σH, σH_4aa, σH_4aa_K, σH_6aa and σH_6aa_K (Table 2).


### The activity of σD and σH and its mutant variants with promoters
  In the biological part of this study, the ability of σD, σH, and all constructed σH mutants (σH_4aa, σH_4aa_K, σH_6aa, and σH_6aa_K - Table 2) to drive transcription (as subunits of RNAP) in all combinations with the four promoters (Pcg0441, PuvrD3, PrsdA, and PD35-rsdAH10-uvrD3—Table 1) was tested by two-plasmid in vivo assay [19].


### (A) Natural D35H10 hybrid promoter Pcg0441
  While the activity of the natural D35H10 hybrid Pcg0441 promoter with the overproduced σD was high, it was almost undetectable with overproduced σH (Fig. 3a). The promoter activity with the σH_4aa and σH_6aa mutants was negligible as well. Nevertheless, it was slightly higher with the σH_4aa_K and significantly with the σH_6aa_K mutant. The natural D35H10 hybrid Pcg0441 promoter did not meet our requirements regarding its bio-orthogonality because it was strongly transcribed with natural σD.Fig. 3Determination of promoter activity in C. glutamicum WT with overexpressed σD, σH, and σH mutants (σH_4aa, σH_4aa_K, σH_6aa, and σH_6aa_K) by using the two-plasmid assay. The strain with the empty expression vector pECXT99A was used as a control (gray bars). The promoter activity was measured as the Gfpuv fluorescence intensity of the cell extracts. The fluorescence of cultures without IPTG is shown as light bars. The fluorescence of cultures with IPTG induction is shown as dark bars. AU, arbitrary units. The standard deviations of three biological replicates are depicted by error bars


### (B) σH-dependent promoter PuvrD3
  In the case of the σH-dependent PuvrD3 promoter, all studied sigma subunits except σD, initiated transcription (Fig. 3b). The σH-dependent PuvrD3 promoter activity was high with σH as expected. However, the non-negligible expression was observed more or less for all mutant σH subunits. It was not so much expected. In particular, it was surprising that a mutant of the σ subunit, the σH_6aa_K, which is most similar to σD, stimulated transcription strongly, even with the same intensity as the natural σH factor (Fig. 3b).


### (C) σD-dependent promoter PrsdA
  Further, we examined transcription driven by the strong σD-dependent PrsdA promoter (Fig. 3c). As expected, this promoter was active only in combination with σD. For other σ factors, no increase in transcription above the basal level of fluorescence intensity was observed.


### (D) Artificial hybrid promoter PD35-rsdAH10-uvrD3
  Promoter activity assay with the artificial/synthetic hybrid promoter PD35-rsdAH10-uvrD3 was high with all σH mutants (Fig. 3d). Equally important, however, was the finding that there was no increase in the PD35-rsdAH10-uvrD3 promoter activity in the presence of the overproduced σD factor (Fig. 3d). Similarly, there was almost no increase in the PD35-rsdAH10-uvrD3 promoter activity in the presence of overproduced factor σH (Fig. 3d). It means that both native σD and σH subunits did not recognize this artificial D35H10 hybrid promoter PD35-rsdAH10-uvrD3. Taken together, only engineered σH subunits with point mutations could initiate transcription. Thus, this artificial hybrid promoter PD35-rsdAH10-uvrD3 appears to have almost optimal properties needed for bio-orthogonal transcription.

  Further, an equally important point is whether the mutant σH subunits induced any transcription from both native σD- and σH-dependent promoters (Fig. 3b and c). The requirement of missing activity was undoubtedly met for the σD-dependent PrsdA promoter (Fig. 3c) since none of the mutant σH subunits showed any activity with PrsdA (Fig. 3c). In the case of the σH-dependent promoter PuvrD3, the σH_6aa mutant had the lowest and rather transient activity (Fig. 3b). It goes perfectly with the finding that the σH_6aa mutant has the highest activity with the artificial/synthetic hybrid promoter PD35-rsdAH10-uvrD3.

  The σH_6aa subunit and artificial/synthetic hybrid promoter PD35-rsdAH10-uvrD3 thus seem to be the most suitable candidates for creating the σ-promoter pair, which can ensure bio-orthogonal transcription.

  To sum up, the wet-lab experiments demonstrated that we achieved the main goal, to construct the bio-orthogonal transcription. However, many partial results were in various aspects rather unexpected and counter-intuitive, especially in the case of the natural hybrid Pcg0441 promoter and the σH-dependent PuvrD3 promoter. Therefore, in the following paragraphs, we will try to decipher and interpret these partial results using homology modeling and MD simulations. We consider the compliance of the results of the in vivo measurements with the computational models the crucial point of the study that provides clues for future development and fine-tuning of bio-orthogonal D35H10 hybrid σ subunits and promoters.


## Computer modeling
  In the following paragraphs, we summarize the findings on the crucial nucleotides and amino acids involved in mutual interactions that were achieved using our computer models. Further, we present here the results of extensive MD simulations of 18 complexes covering all possible combinations of six σ4 segments (see Table 2), and three −35 elements derived from our four promoters (σD-dependent PrsdA and synthetic hybrid promoter PD35-rsdAH10-uvrD3 share the same −35 element—see Table 1). Finally, we will provide tentative explanations of the observed biological activities (see Fig. 3).

  Our computer models (Figs. 4, 5) show that interactions between amino acids and nucleotides can be divided into sequence-specific, which involve nucleobases, and sequence non-specific, which involve negatively charged sugar-phosphate backbone of DNA attracting long and flexible side-chains of basic amino acids (arginines or lysines). Further, amino acids with hydroxyl groups that can form hydrogen bonds (for example Y155 or T165) are also involved.Fig. 4Domain 4.2 of the σH subunit interacting with the −35 element of the PuvrD3 promoter. Amino acids from σH that were mutated in this study have red labels. Labels of amino acids that significantly interacted with the promoter in MD simulations are highlighted in bold. For clarity, amino acids are shown separately: (left) mutated only in 6aa mutants; (middle) mutated in all cases; (right) amino acid E140, which was mutated in the 4aa_K and 6aa_K mutants to compensate for the R172 to A172 mutation. I.e. so that a positively charged amino acid side chain is present at the site that could interact with the negatively charged backbone of the nucleic acid. In addition, R175, which interacts with the nucleotide base at position −35, as well as the basic amino acids K178, R171, R177, and K156, which are important for interaction with the sugar-phosphate backbone of the nucleic acids, are shown hereFig. 5Domain 4.2 of the σD subunit interacting with the −35 element of the PrsdA promoter. Amino acids from σD that were mutated have blue labels. Labels of amino acids that appeared to be particularly important in MD simulations are highlighted in bold. For clarity, amino acids are shown separately: (left) mutated only in 6aa mutants; (middle) mutated in all cases; (right) K140 from the 4aa_K and 6aa_K mutants that compensates for the R172 to A172 mutation. Also shown is the crucial R175 interacting with the nucleotide base at position −35 and the basic amino acids R181 and R148, which are important for interaction with the sugar phosphate backbone of the nucleic acids


### Nucleotides involved in σ4 region–promoter interactions
  In the promoters, Pcg0441, PuvrD3, PrsdA/PD35-rsdAH10-uvrD3, the non-conserved bases at the first and second (i.e. −35, −34) positions within the −35 elements of the non-template DNA strand (CTAAC/GGAAT/GTAAC)and the non-conserved base at the fifth (i.e. −31) position of the opposite (template) DNA strand (GATTG/CCTTA/CATTG) were found to participate in the most important sequence-specific interactions with polar amino acids of σ4 subunits (Figs. 4, 5).

  Specifically, the C−35ntT−34nt–G−31t bases within the σD35H10-dependent promoter Pcg0441, are involved in these contacts. In the case of the σH-dependent promoter PuvrD3, the G−35ntG−34nt-A−31t bases are involved. Finally, in the case of the σD-dependent PrsdA, and the hybrid promoter PD35-rsdAH10-uvrD3, the G−35ntT−34nt–G−31t bases are involved (Figs. 4, 5).

  Furthermore, the conserved bases −33, −32 (more specifically AA/TT in the non-template/template DNA chain) are in close contact with the σ4.2H/σ4.2D helix between the mutated amino acids at positions 170 and 171 (i.e. M170, S171 or R170, V171). The methyl groups of both T bases participate in stabilizing hydrophobic interactions, especially with the bulky non-polar side-chain of V171.

  Moreover, several nucleotides surrounding the canonical −35 element may be in at least occasional contact with mutated amino acids. This may to some extent modulate the recognition between specific σ-subunits and promoters. For example, the −30 nucleotide interacts with the amino acid R170 or M170, or the −37, and −36 nucleotides interact with the amino acid K140.


### Amino acids involved in σ4–promoter interactions
  The central helix of the σ4.2H/σ4.2D segments is involved in interactions with the −35 elements of promoters.

  The G/A base at position −31 of the template strand of DNA interacts with R170 at σD. In particular, if G is in position −31, up to two stabilizing hydrogen bonds may be formed. Alternatively, the long flexible side chain of R170 can create the so-called salt bridge with negatively charged phosphate groups of the sugar–phosphate backbone of DNA.

  In the case of σH, the G/A base at position −31 interacts with M170. Methionine cannot form hydrogen bonds with bases or salt bridges with phosphate groups of the sugar–phosphate backbone of DNA like R170. However, the M170 side chain forms a tight cluster with the side chains of amino acids L166, Y155, and R177 (not present in σD). The latter two amino acids interact with the sugar–phosphate backbone of DNA. This seems to be how the presence of an either optimal or suboptimal interaction partner i.e. A−31 or G−31 in the vicinity of M170 can result in either stabilization or destabilization of the σ–promoter complex.

  In the case of mutant σD35H10 subunits, a specific situation occurs (Fig. 6). There is R170 transferred from σD, but there are also amino acids L166, Y155, and R177 from σH. In our MD simulations, it took usually quite a while before long side chains of R170 and Y155 relaxed and settled properly into an arrangement without steric conflicts/clashes between them.Fig. 6In the case of mutant σD35H10 subunits (bottom), a specific situation occurs. There is R170 transferred from σD (top right) but there is also amino acid Y155 from σH (top left). In MD simulations, it took quite a while before the long side chains of R170 and Y155 relaxed and settled properly into an arrangement without steric clashes between them. More specifically, the optimal interaction of R170 with base −31 was mostly observed when spatially close Y155 was not bound to the phosphate group of DNA. Steric conflicts between R170 and Y155 could be one of the reasons, why we generally observed weaker transcription with the σD35H10 mutants than was achieved with σD that lacks Y155

  The G/T bases at position −34 of the non-template DNA strand interact with amino acids that are specific for σH (S171) and σD (V171) subunits (Fig. 7). While S171 forms stabilizing hydrogen bonds with the G–34 base, the attraction of V171 and T–34 stems from their hydrophobicity.Fig. 7The G/T bases at position −34 of the non-template DNA strand interact with amino acids that are specific for σH (S171] and σD (V171) subunits. While S171 forms stabilizing hydrogen bonds with the G−34 base, the attraction of V171 and T−34 stems from their hydrophobicity

  Close contacts of atypical interacting partners S171 and T−34 (in σH complexes with the σD-dependent promoter PrsdA, natural D35H10 hybrid promoter Pcg0441, and artificial hybrid promoter PD35-rsdAH10-uvrD3) are destabilizing. This is because a hydrogen bond formed between the hydroxyl group of S171 and oxygen atom O4 of T–34 leads ultimately to the disruption of other stabilizing interactions.

  In contrast, close contacts of atypical interacting partners V171 and G–34 in complexes of σD and σD35H10 mutants (σH_4aa, σH_4aa_K, σH_6aa, and σH_6aa_K) with the σH-dependent promoter PuvrD3, don't seem to be destabilizing.

  Base G at the position −35 of the non-template DNA strand of either σH-dependent PuvrD3 or σD-dependent PrsdA interacts (via two hydrogen bonds involving atoms O6 and N7) with an arginine side chain R175 (Fig. 8), which is present in the equivalent spatial position of both σH and σD subunits. These hydrogen bonds with the involvement of R175 (conserved in σH and σD) we consider to be the most important. After their disruption, a substantial repositioning of the DNA:DNA duplex relative to σ4 domains usually followed quickly.Fig. 8(Left) Base G at the position −35 of the non-template DNA strand of either σH-dependent PuvrD3 or σD-dependent PrsdA interacts (via two hydrogen bonds involving atoms O6 and N7) with an arginine side chain R175, which is present in the equivalent spatial position of both σH and σD subunits. (Right) The C base at the first position of the Pcg0441 −35 element does not allow usual hydrogen bonding with the R175 side chain. Instead, this R175 side chain interacts with the guanine base at position −35 in the complementary template strand of DNA

  As regards sequence non-specific interactions, R181 of both σ4H/σD domains interact with the negatively charged sugar–phosphate backbone of DNA chains and provide further stabilization of σ4–promotor complexes. Further, there is another basic amino acid K178, which is present only in σ4H and in its mutants.


### Stability of σ4D–promoter complexes in MD simulations
  Let us summarize the results of 800 ns MD simulations for 18 simulated systems grouped based on the involved σ4 subunits.


### Interactions of σ4H with promoters
  As expected, σ4H created the most stable complex with the σH-dependent promoter PuvrD3. All possible stabilizing interactions mentioned above were found: sequence-specific (G–35–R175, G–34–S171, A−31–M170) as well as sequence non-specific (i.e. mediated by binding of side chains of Y155, R177, K156, R172, T168, R181, K178 to the sugar–phosphate backbone of nucleic acids).

  On the other hand, in σD- and σD/σH-dependent promoters (i.e. PrsdA, Pcg0441, and PD35-rsdAH10-uvrD3), most of these interactions were interrupted, the orientation of the DNA:DNA duplex relative to σ4H was significantly changed, or even this complex was completely abrogated. In any case, hydrogen bonding between undue partners (S171 and T–34) was a primary destabilizing factor.


### Interactions of σ4D with promoters
  All complexes were quite stable and only small deviations were observed for σ4D, expected stabilizing interactions mentioned above were observed: sequence-specific (C/G–35–R175, T–34–V171, G–31–R170) as well as sequence non-specific (i.e. mediated by binding of side chains of R148, E156, K140, T165, R181 to the sugar phosphate backbone of nucleic acids).

  The only exception was the σH-dependent promoter PuvrD3, where significantly greater disturbance of interactions was transiently observed, and it is questionable whether this complex would remain stable during a longer MD simulation.


### Interactions of σ4H mutants with promoters
  Mutations of only 4–7 amino acids that bring σH closer towards σD (resulting in σH_4aa, σH_6aa, σH_4aa_K, or σH_6aa_K constructs) were sufficient for the stabilization of complexes of all mutated σH subunits with σD- and σD/σH-dependent promoters (PrsdA, Pcg0441 and PD35-rsdAH10-uvrD3).

  On the contrary, due to these mutations, certain destabilization of complexes with the σH-dependent PuvrD3 promoter occurred. Here, the most stable was the complex with σH_6aa_K,

  The optimal interaction of R170 with base -31 was mostly observed when spatially close Y155 was not bound to the phosphate group of DNA. Steric conflicts between those two amino acids could be one of the reasons, why we generally observed weaker transcription with the σD35H10 mutants than was achieved with σD that lacks Y155.


## Interpretation of experimental results based on homology models and MD simulations

### (A) Natural PD35H10 hybrid promoter Pcg0441
  While the activity of the Pcg0441 promoter with the overproduced σD was high, it was almost undetectable with overproduced σH in the biological assays (Fig. 3A). In MD simulations, the complex of the −35 element of Pcg0441 with σ4D was stable, while the complex with σ4H was unstable—apparently due to the stabilizing interaction of the T–34 base with V171 (σ4D) or destabilizing interactions of the T–34 base with S171 (σ4H).

  Although experimental results and MD simulations are in agreement, the fact that Pcg0441 is strongly σD-dependent is not entirely obvious given that the GTT sequence in the −10 element is typical for σH-dependent promoters. Nevertheless, the completely inappropriate −10 element of Pcg0441 was not an obstacle for σD to very strongly stimulate transcription from this natural hybrid promoter.

  A detailed analysis of MD trajectories showed that this could be related to the atypical base at the first position of the −35 element (in the non-template strand of DNA). Here, the Pcg0441 promoter has the C base. It means that it carries sequence CTAAC instead of GTAAC canonical for σD-dependent promoters.

  Our MD simulations showed that the C base at the first position of the Pcg0441 −35 element does not allow usual hydrogen bonding with the R175 side chain. Instead, this R175 side chain interacts with the guanine base at position −35 in the complementary template strand of DNA. In addition, the R175 side chain also interacts with the guanine base in the non-template DNA strand, however, at position –36 (i.e., at the position immediately preceding the −35 element).

  This atypical interaction of R175 has effects on the interactions of R170. The R170 side chain ideally contributes to sequence-specific recognition of the base at the fifth position of the −35 element (specifically in the template strand). Here, however, the R170 side chain prefers sequence-non-specific interactions with phosphate groups in the sugar–phosphate backbone of the DNA template strand. In other words, a salt bridge is formed.

  R170 is the last amino acid that substantially interacts with the −35 element. In structures of open RNAPs with resolved complete transcription bubbles, a ~ 17–18 bp spacer DNA:DNA duplex connecting the −35 and −10 elements follows (Table 2). It seems that subtle rearrangements of key interactions between Pcg0441 and σ subunits that appear due to the atypical C base at the first position of the −35 element are somehow transmitted through R170 and the spacer duplex toward the −10 element region, where it could slightly disturb spatial RNAP–DNA arrangement as well as underlying interactions between amino acids and nucleotides. Among other things, this could cause σD to be able to recognize GTT (typical rather for σH-dependent promoters) in the −10 element of the natural PD35H10 hybrid promoter Pcg0441.

  Further, the natural PD35H10 hybrid promoter Pcg0441 activity with the σH_4aa and σH_6aa mutants was negligible. Transcription was slightly higher with the σH_4aa_K and especially with the σH_6aa_K mutant. However, it fell far short of the level of transcription observed with σD. We attribute this mainly to the fact that in MD simulations the crucial R170 was not able to establish an interaction with the base G–31 or with a nearby phosphate group (as was the case with σD). The obvious reason was the side chain of Y155 (which is missing in σD, where it is replaced by the less bulky A155), with which R170 is in very close contact that disrupts to some extent interactions of both Y155 and R170 with nucleic acids.

  Overall, the natural PD35H10 hybrid promoter Pcg0441 was a bit of a disappointment to us, as it did not meet our expectations as regards the level and bio-orthogonality of transcription achieved with mutant σ subunits. However, the atypicality of Pcg0441 concerning its base at position −35 and the resulting differences in the arrangement of the σ4-promoter complexes found in the MD simulations raised our hope that a hybrid PD35H10 promoter is in principle possible to create.


### (B) σH-dependent promoter PuvrD3
  In the case of the σH-dependent PuvrD3 promoter, all studied sigma subunits except σD more or less initiated transcription (Fig. 3b). Nevertheless, natural σH and σ4H_6aa_K stimulated transcription by far the most.

  Our MD simulations show that not only natural σ4H and σ4H_6aa_K but also σ4Dcan recognize the −35 element of the PuvrD3 promoter. Nevertheless, in the case of σ4D, the crucial interaction between the R175 side chain and the base at the −35 position was remarkably less stable. R170 from D was not able to establish stable contact with the phosphate group of the DNA backbone, as was the case with σ4H_6aa_K. MD simulation showed that this was again partly due to the absence or presence of Y155. Nevertheless, Y155 now had opposite effects on R170 than in the case of σ4D vs. σ4H_6aa_K and the Pcg0441 promoter.


### (C) σD-dependent promoter PrsdA
  The strong σD-dependent PrsdA promoter was active only in combination with σD (Fig. 3c). For other σ factors, no increase in transcription above the basal level of fluorescence intensity was observed.

  Our MD simulations showed that except σ4H all other studied σ4 subunits can recognize the −35 element of the σD-dependent PrsdA promoter. The crucial interaction between the R175 side chain and the base at the −35 position of the −35 element was stable leading to the classic arrangement of complexes.

  The in-vivo inability of mutant σD35H10 subunits to stimulate transcription from this σD promotor probably lies in their inability to recognize the GAT nucleotide sequence in the −10 element, which is typical for σD-dependent promoters.


### (D) Artificial hybrid promoter PD35-rsdAH10-uvrD3
  Finally, we used the PuvrD3 and PrsdA promoters to construct an artificial hybrid PD35-rsdAH10-uvrD3 promoter that combines the canonical −35 element of the σD-dependent PrsdA and the canonical −10 element of the σH-dependent PuvrD3. Promoter activity assay with this synthetic hybrid promoter PD35-rsdAH10-uvrD3 provided high transcriptional activity with all σH mutants (Fig. 3d).

  This confirmed our hypotheses that just the incompatible −10 element of PrsdA (Fig. 3c) and the atypical −35 element of natural PD35H10 hybrid promoter Pcg0441 (Fig. 3a) hindered transcription of these promotors using our mutant σH subunits.

  Both native σD and σH subunits did not recognize the hybrid PD35-rsdAH10-uvrD3 promoter (Fig. 3d). Thus, this artificial promoter appears to have optimal properties needed for bio-orthogonal transcription.

  None of the mutant σH subunits show any activity with σD-dependent PrsdA. Further, in the case of the σH-dependent promoter PuvrD3, the σH_6aa mutant had the lowest activity (Fig. 3b).

  Interestingly, this σH_6aa mutant has the highest activity with the artificial hybrid promoter PD35-rsdAH10-uvrD3.

  Taken together, the σH_6aa subunit and PD35-rsdAH10-uvrD3 promoter seem to be the most suitable candidates as a σ-promoter pair that could enable bio-orthogonal transcription.

  Prospectively, another designed mutation in the σH_6aa subunit, i.e., Y155A, could decrease the unwanted transcription from the σH promoter PuvrD3 and increase the transcription driven by the PD35-rsdAH10-uvrD3 hybrid promoter to the level that was observed with σD and the σD-dependent promoter PrsdA.


## Discussion and conclusions
  C. glutamicum has been applied in various biotechnological processes for the production of various amino acids, value-added chemicals, fuels, and polymers [3, 25]. To make these processes more effective, the production/transcription by bacteria should take place bio-orthogonally, to interfere as little as possible with their metabolism. For this, it is necessary to create pairs of artificial promoters and sigmas (or also anti-sigmas). This can be achieved in several different ways. Orthogonal pairs can be found in the genomes of various bacteria. Moreover, such regulatory units can be created artificially as chimeras or more subtly through amino acid point mutagenesis.

  For example, 86 ECF σs, their promoters, and 62 anti σs identified from the genomes of diverse bacteria were used to identify a subset of 20 σs and promoters that were found to be highly orthogonal to each other [26]. They were used to build synthetic genetic switches in Escherichia coli [26]. Further, it was proposed by Rhodius et al. that this set could be extended by combining the −35 and −10 binding domains to build chimeras.

  Indeed, a synthetic hybrid σ combining the −10 DNA binding domain of σ70 with the −35 DNA binding domain of σ32 was able to recognize a cognate hybrid promoter containing a consensus σ32 −35 motif and a consensus σ70 −10 motif [27].

  Recently, 91,552 potential promoters belonging to 41,665 unique ECF σs were studied in detail [28]. Motifs were aligned, and putative promoter sequences were associated with the respective ECF σ sequences. Only a few amino-acid + nucleotide pairs were identified as important, and these were consistent with specificity-determining interactions observed in the crystal structures of three divergent ECF σs bound to their cognate promoters [29–31]. It suggests that the mechanism of ECF σ-promoter interaction is conserved in a majority of ECF σs despite their extensive sequence divergence. Artificial σ subunits can be therefore tailored to be specific for the respective hybrid promoters through point mutations of a very small number of amino acids.

  Here we followed up on our previous study [13] and first looked at naturally occurring hybrid promoter Pcg0441, which has a sequence CTAACG close to the consensus of the σD-dependent promoters in the −35 region and GTT in the −10 region which conforms the σH-dependent promoters. We studied transcription driven from this promotor using a set of systematically mutated σ subunits based on σH. The mutations were proposed purely based on homology models constructed using the few available crystal structures of ECF σs, but it is clear that these mutations fall within a region recently identified as crucial in the study of tens of thousands of promoters and ECF sigma factors mentioned above see Fig. 1b in [28].

  The most extensively mutated σH subunit, σH_6aa_K, was the most potent one from this set as regards transcription from the natural hybrid Pcg0441 promoter. This finding confirmed our assumption that all proposed mutations are meaningful and bring the expected and synergistic effect. In other words, it means that σH with a few point mutations is undoubtedly able to interact effectively with the −35 element carrying the nucleotide sequence typical for σD-dependent promoters.

  On the other hand, our experimental results clearly showed that the naturally occurring hybrid promoter Pcg0441 is by no means suitable for bio-orthogonal transcription, as it is strongly recognized by the native σD factor (despite the GTT sequence in the −10 region which is typical for σH-dependent promoters and which should prevent σD binding).

  We believe that σD can recognize this naturally occurring hybrid promoter Pcg0441 partly due to the atypical base sequence in the −35 element region, specifically due to the base C−35 at the first position of the −35 element consensus sequence (CTAAC). MD clearly showed that this leads to a remarkably distorted binding of this atypical −35 element to σ subunits. We suppose, that this could ultimately affect the conformation of the whole spacer region of upstream DNA and even the binding of the distant −10 element of upstream DNA to the σ2 segment of sigma subunits.

  Indeed, although there are only a few structures of the entire RNAP in complex with the ECF σ subunit and promoter DNA, they show the remarkable conformational variability of the ECF σ subunits in the region recognizing the −35 element (compare PDBid: 6JBQ, 6CA0, 5ZX2 – [29–31]). Different ECF σ subunits use a distinct hydrophobic surface to bind the tip helix of RNAP-β flap domain that rotates by 90°. This is accompanied by different bending of the DNA in the spacer region and by changes in its interaction with the positively charged amino acids of RNAP. Some distortions are visible even in the parts of the complexes, where σs recognize the −10 element. Thanks to the flexibility of the σ4 segments of the sigma subunits, transcription can probably start from promoters with spacers of different lengths or with certain deviations from consensus sequences in the −35 element. Nevertheless, it should be taken into account that these observations are based on a comparison of structures gained by different experimental techniques, namely cryoEM (6JBQ) and X-ray (5ZX2). Therefore, more structures obtained through cryo-EM will have to be awaited before making conclusions. Alternatively, extensive MD simulations (on a time scale of at least us), during which the 5ZX2 structure would be allowed to relax, could clarify whether the spacer DNA and tip helix of RNAP-β flap domain undergoes conformational changes exclusively due to the contacts with different sigma subunits or if it is partly a consequence of the so-called crystal packing forces.

  The naturally occurring hybrid promoter Pcg0441 has four consecutive thymines in the spacer region. This TTTT sequence should allow a significant bending of the spacer duplex since the AT base pairs are bound together by only two hydrogen bonds (in contrast to GC base pairs bound with three hydrogen bonds). Gaballa et al. identified a similar −35 proximal homo-polymeric T-tract as a novel promoter element involved in promoter discrimination by ECF σ factors in B. subtilis, likely by altering the trajectory of promoter DNA during engagement with RNAP [32]. Based on its conservation in a significant subset of deduced consensus sequences for ECF σs factors, they surmised that this element likely plays a general role in modulating the extent and impact of overlapping promoter recognition among ECF σ factors. Similarly, extended −10 promoters, which contain a 5’-TG-3’ element, tend to have longer spacers containing short runs of T residues. These promoters also show fewer matches to the consensus −35 hexamer element [33].

  Considering both structural factors mentioned above (i.e. atypical C−35 and the TTTT sequence in the spacer region), we believe that they could jointly explain this rather unexpected and for us undesired recognition of the −10 region of Pcg0441 by σD (which undoubtedly has biological significance). Since, at this moment, we don’t see any simple way to modify the Pcg0441 sequence so that it was not recognized by σD but still was recognized by σH_6aa_K, we tried a different approach to gain a hybrid promotor capable of bio-orthogonal transcription.

  In subsequent experiments, we focused on two promoters, i.e. both σD-dependent (PrsdA) and σH-dependent (PuvrD3) that carry conventional −35 consensus sequences with G−35 in the first position (GGAAT and GTAAC). This G−35 is efficiently recognized by R175 in both σD and σH using two mutual hydrogen bonds that remarkably stabilize the positioning of the −35 element relative to σ subunits. As expected, σD stimulated transcription of σD-dependent PrsdA by far the most strongly (transcription stimulated by σH or by its mutants was negligible). On the other hand, the σH-dependent PuvrD3 was not recognized by σD at all. Therefore, we created an artificial hybrid promoter combining the −10 element from the PuvrD3 promoter and the −35 element from the PrsdA promoter which showed almost optimal properties in terms of bio-orthogonal transcription.

  For the future, we see some space for potential further improvements in two ways. First, a model of the complete RNAP with the entire σH_6aa_K and in complex with the PD35H10 hybrid promoter could allow the design of base mutations to improve the interaction between the PD35H10 hybrid promoter spacer and RNAP. Second, it could be interesting to make additional point mutations of σH_6aa_K so that it is not recognized by the anti-sigma factor RshA [34, 35]. Our earlier results show that this could yield a several-fold increase in transcription [36]. However, both would require MD simulations of significantly larger molecular systems and detailed calculations of binding free energy [37, 38].


## Supplementary Information
  Below is the link to the electronic supplementary material.Supplementary file 1 (DOCX 101 kb)Supplementary file 2 (DOCX 15 kb)


## Acknowledgements
  This work was supported by Grant from Charles University (Project GAUK 338321).