# A new family of small ArdA proteins reveals antirestriction
activity


## IMPORTANCE
  Our current findings suggest that the binding specificity of DNA-mimicking proteins to their targets could also be achieved by very short proteins. The ability of these DNA-mimicking proteins to specifically inhibit different DNA-binding proteins makes them a promising tool for regulating a range of intracellular processes, including gene expression.


## INTRODUCTION
  Type I RM systems, consisting of specificity subunits, restriction endonucleases, and DNA methyltransferases, provide a critical defense mechanism in bacteria by recognizing and cleaving foreign DNA (1). ArdA proteins can counteract this defense by mimicking the structure and surface charge of DNA, thereby preventing the degradation of a mobile genetic element’s DNA (2). ardA genes are commonly found within conjugative plasmids, transposons, and bacteriophage DNA and are typically among the first genes to enter the cell during horizontal gene transfer (3).

  Recent evidence shows that chromosomally coded ArdA proteins from Bifidobacterium bifidum modulate bacterial gene expression in E. coli (4), raising intriguing questions about their cellular roles.

  Here, we identify two novel ArdA-like antirestriction proteins from L. cremoris (further named ArdA_1576) and C. pilbarense (further named ArdA_8247). These newly identified proteins are particularly intriguing due to their exceptionally small sizes, respectively (114 and 88 aa), making them among the smallest ArdA proteins discovered to date.


## MATERIALS AND METHODS

### Bacterial strains and plasmids
  E. coli strain TG1 (K-12 glnV44 thi-1 Δ(lac-proAB) Δ(mcrB-hsdSM)5(rK–mK–) F′ [traD36 proAB + lacIq lacZΔM15]) was used as the host strain for all experiments. Two novel, exceptionally small chromosomal ardA genes were cloned from the C. pilbarense B-8247 and L. cremoris B-1576 chromosomes. All strains were obtained from the All-Russian Collection of Industrial Microorganisms (VKPM).


### Construction of plasmids
  The two novel chromosomal ardA genes were amplified from C. pilbarense and L. cremoris genomes via PCR using primers incorporating NdeI and EcoRI restriction sites. The PCR products were purified and digested with NdeI and EcoRI restriction enzymes. The pIR-DPAl expression vector was also digested with the same restriction enzymes. The digested ardA gene fragments and the linearized pIR-DPAl vector were ligated using T4 DNA ligase (Thermo Fisher Scientific, USA). The ligation products were transformed into calcium-competent E. coli cells, and transformants were selected on LB agar plates containing kanamycin (50 µg/mL). Plasmids were isolated from positive colonies and confirmed by sequencing. The resulting plasmids (Table 1) contained the target ardA genes under the control of the pIR-DPAl expression vector promoter.


### Antirestriction activity assays
  To evaluate the antirestriction activity of ArdA_8247 and ArdA_1576 against the EcoKI (GenBank AAC77306.2, AAC77305.1, AAC77304.1) and EcoR124II (GenBank OAF89003.1, CAL6689313.1, OMI69276.1) restriction-modification (RM) systems, unmodified lambda phage (λ₀) was used. Three types of E. coli TG1 cultures were used: cells without plasmids, cells harboring plasmids containing the genes for the RM systems, and cells carrying plasmids with the RM system genes along with either ardA_8247 or ardA_1576 (as detailed in Table 1). The plasmid pIR-DPAl-ArdA-R64, containing a well-described ardA gene from the conjugative plasmid R64, served as a positive control. Phage plating and calculation of the efficiency of plating (EOP) were conducted following established procedures (6).

  The efficiency of plating (EOP) was estimated as

  where NX is the number of λ0 phage plaques on the Е. coli TG1 cells carrying genes “X” affecting plaque formation (RMI ± Ard), NTG1 is the number of λ₀ phage plaques on Е. coli TG1 (without any additional restriction or antirestriction genes).


### Phylogenetic studies
  The protein sequences from the NCBI database used to construct phylogenetic trees are presented in Table S1. We used ModelFinder (9) to select the best evolutionary model for our sequence alignments. The phylogenetic relationships between ArdA proteins were visualized using the Tree Of Life (iTOL) v5 online tool (10).


### AlphaFold structure predictions
  We performed structure predictions of the proteins ArdA_1576, ArdA_8247, and ArdA_916 as well as their interaction with the EcoKI (S1M2) protein complex using AlphaFold v.3 software (11). For comparison, the prediction of the interaction between the EcoKI (S1M2) protein complex and dsDNA (AAAACACGTGTGTGCAA) was performed.


### Antimethylation activity assay
  To test the antimethylation activity of newly described sArdA proteins, we used E. coli AB1157 [thr-J leu-6 proA2 his4 thi-J argE3 lacY galK2 ara-14 xyl-5 mtl-l tsx-33 rpsL31 supE44] strain, which contains the EcoKI RMI system. We collected λk from the AB1157 strain and λk1576 and λk8247 from AB1157 pIR-DPAl-ArdA-1576 and AB1157 pIR-DPAl-ArdA-8247, respectively. After that, the EOP was estimated.


### Site-directed mutagenesis
  To verify our predictions of the EcoKI (S1M2) protein complex interactions, we tested the effect of point mutations in sArdA proteins on their antirestriction activity against the EcoKI RMI system. We selected D8 and D40 amino acids in ArdA_1576, as well as D7, E75, and E78 in ArdA_8247, and replaced them with uncharged leucines. The oligos used for mutagenesis are listed below:

  8247_D7L_F  GAACAACCTGCTCAGCACGCCCCGCGTGT

  8247_D7L_R  CGTGCTGAGCAGGTTGTTCGTGTCCATATG

  8247_E7578L_F GATGGGCCCGAACTTGGCTGCTTTGTGAGGCCGGAATTCAA

  8247_E7578L_R GGCCTCACAAAGCAGCCAAGTTCGGGCCCATCTCGCCGCGTACGGGC

  1576_D8L_F   GCAGAAAATGATGAACTTTTAGCACAGGAATTAATTGAAC

  1576_D8L_R   GTGCTAAAAGTTCATCATTTTCTGCTTCCATATGA

  1576_D40L_D  GCTTATGGTCGACTTTTAGCGATTGGTGATT

  1576_D40L_R  CGCTAAAAGTCGACCATAAGCACTAAAGTTAAAAT

  We constructed four more pIR-DPAl-based plasmids with mutated sArdA proteins. We also confirmed protein expression using SDS-PAGE (not presented). All mutations were verified using Sanger sequencing.

  Antirestriction was measured against the AB1157 strain, which contains the full EcoKI RMI system as described above.


## RESULTS
  Recently, we showed that ardA genes can be found on bacterial chromosomes (4, 12). We searched for ardA-like genes across various bacterial species and identified a new group of chromosomal ardA genes, which are half the size of classic ardA genes such as the one from Tn_916 transposon (13). These small coding sequences are not surrounded by the ardA gene fragments but seem to be evolving independently. We named this group of ArdA proteins “small ArdA” (sArdA) and performed a protein alignment using the T-coffee service (14). The alignment results were visualized via the MView web service at the EMBL-EBI site (15) (Fig. 1).

  Figure 1 illustrates that although the percentage of amino acid identity is rather low, a distinctive negative charge (indicated by negatively charged amino acids colored in blue), mimicking the DNA structure, is preserved throughout all aligned protein sequences. Subsequently, we generated structural models of the selected proteins, ArdA_1576 and ArdA_8247, using the AlphaFold3 service (11). These modeled structures were subsequently aligned with the canonical ArdA_Tn916 structure (13).

  From Fig. 2, it is evident that despite the low percentage of identical amino acids (19%), there exists a structural similarity between ArdA_8247 and the N-terminal region of the classical full-length ArdA from Tn916, as well as with the C-terminal segment of ArdA, which aligns to the studied protein ArdA_1576. Moreover, ArdA_1576 aligns not just to the C-terminal region but specifically with the dimerization interface of the full-length ArdA_Tn916, thereby overlapping the dimerization site of its subunits.

  Then, we searched for small sardA genes that are homologous to the N- and C-terminal regions of the full-length ardA gene across various microorganisms. The results of phylogenetic analysis with the identified representatives of sArdA proteins are presented in Fig. 3. Homologs to the N-terminus are henceforth referred to as sArdN, and those to the C-terminus as sArdC. We also performed a Foldseek (18) structure alignment to confirm N and C division (Fig. S1).

  From the data shown in Fig. 3, it is clear that small representatives of the ardA gene family are widely distributed among various bacterial species. Specifically, within the phylum Actinomycetota, sArdA proteins cluster into two distinct subgroups, or subfamilies. We have provisionally named these subfamilies sArdN (homologs of the N-terminal region) and sArdC (homologs of the C-terminal region of the classical ArdA protein), as depicted in Fig. 3A and B, respectively. The clustering of sArdA across diverse bacterial species shows that once established through evolutionary processes, these genes continue to be preserved, forming clusters of conserved sequences. Hence, here, we demonstrated a convergent evolutionary path of genes sardN and sardC across at least two bacterial genera.

  We note that both sArdN and sArdC from the genus Lactococcus cluster with the full-length ArdA protein also present in these bacteria, rather than with their respective subfamilies from other taxa belonging to Actinomycetes. This suggests that the small ardA genes likely arose multiple times during evolution. Note that sArdN is nearly identical to a large ArdA variant found in L. cremoris. This suggests that the protein sArdN likely underwent recent separation or duplication from its ancestral form.

  To validate our results, we performed structure predictions of EcoKI (S1M2, one S-subunit, two M subunits) interacting with sArdC and sArdN using Alphafold v.3 (Fig. 4). Interestingly, we revealed four different states of the S1M2 complex, which feature different angles between M-S-M subunits (Fig. 4A). The intermediate state O2 was predicted only in the case of one protein for which sArdN interacts with the S-subunit (Fig. 4B). Interestingly, the state C1 was predicted in two cases: 2× sArdC and 2× sArdN interacting with the S-subunit. The structural alignment of the protein complex in the C1 state shows highly similar structures and angles between M-S-M subunits (Fig. 4C). A detailed view of the interactions of Ards with the S-subunit reveals that sArdC forms dimers (Fig. 4D), whereas sArdN interacts as two separate monomers (Fig. 4E). This is remarkable because two different agents, sArdC and sArdN, with different interaction pathways nevertheless showed the same conformational changes of the protein complex S1M2. This fact significantly increases the possibility that the EcoKI-ArdA forms complexes in the predicted C1 state in nature. For comparison, other interactions (with DNA and single Ards, etc) were also predicted (Fig. S1) and showed that a single sArdC interacts with EcoKI in an open O1 state, whereas a single sArdN interacts with EcoKI in an open O2 state. Thus, the addition of the second short ArdA might trigger the transition of EcoKI from O2 to C1 in the case of sArdN and from O1 to C1 in the case of sArdC, implying that two M-subunits of EcoKI rotate at different angles and skip the O2 intermediate open state in the case of EcoKI interacting with a single or two sArdC. The reference predictions with DNA and ArdA_916 triggered the EcoKI closed state C2 without any intermediate closed states.

  An investigation was performed on the effect of point mutations in sArdA protein models on the state of the EcoKI-ArdA complex (Table S4). For modeling, negatively charged amino acids were selected, which were replaced with uncharged leucines. It turned out that the predicted structural states of S1M2 complexes with sArdC changed the conformation from the C1 state (wild-type sArdC) to state O1 or O2 in several cases. For the sArdN protein, similar amino acid substitutions led to a change in the complex state from C1 (wild-type sArdN) to O1 or O2, and often, there was a complete loss of ability to form a complex with S1M2 EcoKI. Although these are not experimental results (indirect evidence), they may suggest that sArdN forms a less stable complex with S1M2 EcoKI.

  AlphaFold predictions allowed us to hypothesize that sArdN and sArdC proteins could work as an antirestriction agent. We confirmed this with lambda phage experiments (Fig. 5). The sArdN and sArdC proteins both exhibit almost «full-sized» antirestriction activity, similar to that of ArdA_R64.

  As we can see from Fig. 5, the genes sardN and sardC have a certain amount of specificity for different RMI systems. Thus, sArdC is more effective against EcoR124II, whereas sArdN is more effective against EcoKI. These findings were confirmed by statistical testing using a one-tailed paired t-test (Table S3).

  Then, we chose D8 and D40 amino acids in sArdC, as well as D7, E75, and E78 in sArdN, and replaced them with uncharged leucines. According to our AlphaFold predictions (Table S4), these mutations should lead to an O1 state of the EcoKI complex (or do not form a complex at all), and therefore, the antirestriction effect should decrease against the EcoKI system. Figure 6 shows the results of an EOP test against the lambda phage λ0.

  Figure 6 demonstrates a decrease in antirestriction activity for both sets of mutations, but it should also be noted that sArdN might be more sensitive to point mutations in negatively charged amino acids (some statistical information is presented in Table S5). Hence, we confirmed more directly that sArdN might form a less stable complex with S1M2 EcoKI.

  Additionally, we demonstrated that both studied sard-genes inhibit methylation of λ0 phage (Table 2). We collected modified λk phage from three strains: E. coli AB1157, which contains the full EcoKI RMI system; E. coli AB1157 pIR-DPAl-ArdA-1576; and E. coli AB1157 pIR-DPAl-ArdA-8247. Then, we compared the plaquing efficiency of λk phage from different sources on AB1157 (full EcoKI RMI system) and TG1 (no RMI systems) strains.

  One of the smallest DNA-mimicking proteins is Ocr from bacteriophage T7, and its DNA mimicry is well-described (19). It is known that DNA mimetic proteins are able to specifically inhibit various DNA-binding proteins. For example, Ugi (from Bacillus subtilis) is an inhibitor of the uracil DNA glycosylase (20). Overall, the ability of these DNA-mimicking proteins to specifically inhibit different DNA-binding proteins makes them a promising tool for regulating a range of intracellular processes, including gene expression.

  Here, we described two totally new DNA-mimicking proteins that are twice smaller than classic ArdA proteins.


## DISCUSSION
  The classical mechanism of new gene acquisition during evolution is considered to be duplication, followed by further mutagenesis of one of the copies (21). In our work, we demonstrated that deletions of different parts of the ardA gene lead to the formation of two active gene variants encoding either the C-terminal or N-terminal regions of the full-length protein (Fig. 1 and 2). Phylogenetic studies show that both the C-terminal and N-terminal small ArdA proteins (which we named sArdC and sArdN) are conserved throughout evolution and form homologous genes within certain bacterial taxa (Fig. 3). As seen in Fig. 3A and B, sardC genes cluster within taxa such as the genus Lactococcus and the phylum Actinomycetes. The fact that above the taxon level of Actinomycetota, sArdC and sArdN begin to cluster with their respective full-length ArdA genes strongly suggests repeated formation of small ardA genes in bacteria during evolution.

  Notably, pairs of sArdA proteins derived from different sources exhibit partial specificity for different restriction-modification systems. For instance, sArdC is more effective against EcoR124II, whereas sArdN is effective against EcoKI. It has been suggested in previous work that the specificity of ArdA proteins to DNA-binding proteins may depend on an additional domain, as observed in B. bifidum (4). Structure alignment (Fig. 2) shows that both small antirestriction enzymes are apparently capable of exhibiting the DNA mimicry effect through surface negatively charged amino acids. However, our current findings support the idea that the binding specificity of DNA-mimicking proteins to their targets could also be achieved by very short proteins. This effect opens up prospects for creating agents to specifically inhibit DNA-binding regulators.

  AlphaFold structure prediction allowed us to reveal the dynamics of the EcoKI-Ard protein complexes with four different states (two open, O1 and O2, and two closed, C1 and C2). Interestingly, that interaction with different agents (2× sArdC and 2× sArdN) provided similar predictions of the EcoKI conformation (C1 state). This state, on one hand, is intermediate between open O1 and closed C2 states (is the angle between M-S-M subunits approximately 120 degrees, Fig. 4A). On the other hand, the EcoKI complex is inhibited during this interaction as shown by the λ0 phage plaquing (EOP) on a lawn of E. coli cells containing genes of various RMI systems of gram-negative bacteria (Fig. 5); therefore, we inferred that it is in a closed state C1. Thus, the possible presence of two distinct closed states of the EcoKI protein complex might indicate totally different molecular mechanisms of inhibiting RM systems, although additional structural studies must be performed to directly test our hypothesis. Notably, amino acid substitution modeling revealed that sArdN is more sensitive to complex formation than sArdC (Table S4). This may be because sArdN does not appear to form a dimer and consequently has fewer protein-protein interactions, leading to less stable binding with S1M2 EcoKI. We also indirectly validated this hypothesis using site-directed mutagenesis: mutations in the negatively charged amino acids of sArdN result in a significantly greater reduction in antirestriction activity.

  Structural modeling revealed that sArdC from L. cremoris B-1576 is structurally homologous to the interface between subunits of the full-length ArdA dimer. Previous research by Zavilgel’skii and Rastorguev demonstrated that mutagenesis of this interface sequence reduces the anti-restriction activity of ArdA and completely eliminates its antimethylation capability (16, 17). Evidently, sArdC retains the activity of this part of the antirestrictase structure, which appears to have an antimethylase activity. This hypothesis is supported by data presented in Table 2, showing that only about 15% of phage particles grown on r + m + cells containing sArdC are methylated. Surprisingly, sArdN from C. pilbarense B-8247, which is homologous to the N-terminus of ArdA and theoretically cannot mimic the subunit interaction interface, is also efficient at antimethylation. This paradox awaits further investigation.

  Finally, antimethylation activity combined with relatively weak antirestriction could be beneficial for chromosomal genes during bacteriophage infection or plasmid conjugation.


## SUPPLEMENTAL MATERIAL
  The following material is available online at https://doi.org/10.1128/jb.00318-25.

  ASM does not own the copyrights to Supplemental Material that may be linked to, or accessed through, an article. The authors have granted ASM a non-exclusive, world-wide license to publish the Supplemental Material files. Please contact the corresponding author directly for reuse.


## ACKNOWLEDGMENTS
  The work on searching and cloning antirestriction genes, antirestriction assay, and phylogenetic studies was supported by R.S.F. (project 24-74-00024).

  The work on structural modeling and research was supported by the Ministry of Science and Higher Education of the Russian Federation (agreement 075-03-2025-662, project FSMG-2025-0003).

  The work on antimethylation measurements was carried out as part of a State Assignment for the Research Center Kurchatov Institute.