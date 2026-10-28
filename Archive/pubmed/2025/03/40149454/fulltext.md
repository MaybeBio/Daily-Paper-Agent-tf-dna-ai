# Integrating Artificial Intelligence and Bioinformatics Methods to Identify Disruptive STAT1 Variants Impacting Protein Stability and Function


## Abstract
  Background: The Signal Transducer and Activator of Transcription 1 (STAT1) gene is an essential component of the JAK-STAT signaling pathway. This pathway plays a pivotal role in the regulation of different cellular processes, including immune responses, cell growth, and apoptosis. Mutations in the STAT1 gene contribute to a variety of immune system dysfunctions. Objectives: We aim to identify disease-susceptible single-nucleotide polymorphisms (SNPs) in STAT1 gene and predict structural changes associated with the mutations that disrupt normal protein–protein interactions using different computational algorithms. Methods: Several in silico tools, such as SIFT, Polyphen v2, PROVEAN, SNAP2, PhD-SNP, SNPs&GO, Pmut, and PANTHER, were used to determine the deleterious nsSNPs of the STAT1. Further, we evaluated the potentially deleterious SNPs for their effect on protein stability using I-Mutant, MUpro, and DDMUT. Additionally, we predicted the functional and structural effects of the nsSNPs using MutPred. We used Alpha-Missense to predict missense variant pathogenicity. Moreover, we predicted the 3D structure of STAT1 using an artificial intelligence system, alphafold, and the visualization of the 3D structures of the wild-type amino acids and the mutant residues was performed using ChimeraX 1.9 software. Furthermore, we analyzed the structural and conformational variations that have resulted from SNPs using Project Hope, while changes in the biological interactions between wild type, mutant amino acids, and neighborhood residues was studied using DDMUT. Conservational analysis and surface accessibility prediction of STAT1 was performed using ConSurf. We predicted the protein–protein interaction using STRING database. Results: In the current study, we identified six deleterious nsSNPs (R602W, I648T, V642D, L600P, I578N, and W504C) and their effect on protein structure, function, and stability. Conclusions: These findings highlight the potential of approaches to pinpoint pathogenic SNPs, providing a time- and cost-effective alternative to experimental approaches. To the best of our knowledge, this is the first comprehensive study in which we analyze STAT1 gene variants using both bioinformatics and artificial-intelligence-based model tools.


## 1. Introduction
  Signal Transducer and Activator of Transcription (STAT) proteins are a family of transcription factors latently present in the cytoplasm and participate in a variety of cellular events following cytokines and growth factors signaling [1,2]. STAT proteins are involved in intracellular signaling downstream of the type I and type II cytokine receptors. Upon activation, translocation to the nucleus, binding to their specific promoter regions of target genes and regulation of their transcription subsequently takes place [3,4]. Seven proteins have been identified (STAT1, -2, -3, -4, -5a, -5b, and -6) and share a common structure consisting of an SH2 domain that mediates STAT interactions through homo- or heterodimers, a coiled-coil domain, which is important for dimer nuclear localization, a DNA-binding domain, which leads to target gene transcription, and a transactivation domain [5,6].

  The Signal Transducer and Activator of Transcription 1 (STAT1) gene is composed of 25 exons and 7 domains, located on chromosome 2q32.2 [7,8,9]. STAT1 is an essential mediator of the JAK-STAT signaling pathway in response to interferons [8,10,11,12]. It plays a crucial role in the biological immune response against intracellular mycobacterial infection as well as viral infections [8,13,14]. Upon type I IFN-gamma (IFN-γ) binding to cell surface receptors, there is a signaling pathway through protein kinases then activation of Jak kinases (TYK2 and JAK1) with tyrosine phosphorylation of STAT1, dimerization of phosphorylated STAT1, and association with ISGF3G/IRF-9 forming ISGF3 transcription factor [15]. ISGF3 enters the nucleus and binds to the IFN-stimulated response element (ISRE) to activate the transcription of IFN-stimulated genes (ISG), which bring the cell into an antiviral state [16]. Moreover, in response to type II IFN, STAT1 is tyrosine- and serine-phosphorylated; it then forms a homodimer termed IFN-gamma-activated factor (GAF) [17] that migrates into the nucleus and binds to the IFN-gamma-activated sequence (GAS) to drive the expression of the target genes, inducing a cellular antiviral state [18].

  Genetic variants within STAT1 gene lead to loss-of-function (LOF) and gain-of-function (GOF) phenotypes, with a wide range of clinical presentations, including autoimmunity and life-threatening mycobacterial, severe viral, and bacterial infections [19,20,21]. STAT1 amorphic alleles cause severe viral and bacterial infections, while hypomorphic alleles cause mild disseminated mycobacterial disease [22]. Moreover, hypermorphic mutations are responsible for a variety of clinical presentations such as chronic mucocutaneous candidiasis (CMC), arterial aneurysms, autoimmunity, and squamous cell cancers [23]. STAT1 gain-of-function (GOF) mutation, mostly located at coiled-coil (CCD) and DNA-binding domains (DBD) causing hyper-phosphorylation of STAT1 protein, thus enhanced STAT1-dependent responses to interferons (IFNs) and IL-27, with sequential impairment of Th17 cell development [24,25,26]. GOF mutation is associated with chronic mucocutaneous candidiasis [10,27,28], while patients with LOF mutations display an increased susceptibility to intracellular bacteria, including a Mendelian susceptibility to mycobacterial disease (MSMD) [10,22].

  Single-nucleotide polymorphisms (SNPs) constitute a common form of genetic variation in humans [29]. The nonsynonymous SNPs (nsSNPs) cause alteration in the amino acid residues because of variation in the sequence of DNA at a single position of a nucleotide (A, T, C, or G), which contributes to the functional diversity of the related proteins [30,31,32].

  Recently, bioinformatics tools have played a significant role in the prediction of damaging SNPs and their relationship with diseases [33]. The influence of STAT1 nsSNPs on protein structure and function has not been thoroughly investigated, despite their potential importance; this indicates a substantial scientific gap. Nonetheless, limited published articles have systematically examined STAT1 SNPs by bioinformatics approaches.

  The objective of this study is to define the structural and functional characterization of the most pathogenic variations of the STAT1 gene. We performed a comprehensive STAT1-SNPs analysis using bioinformatics prediction tools combined with artificial intelligence models to identify the pathogenic and deleterious SNPs, providing novel insights into their involvement in immune dysregulation and establishing a foundation for subsequent functional and clinical research.


## 2. Materials and Method
  An overview of the complete methodological approach is shown in Figure 1.


### 2.1. Data Retrieval
  We gathered the data for the human STAT1 gene from the National Center for Biological Information (NCBI) website (https://www.ncbi.nlm.nih.gov/) (accessed on 20 April 2024). While the SNP information (SNP ID) of the STAT1 gene was obtained from the NCBI dbSNP (https://www.ncbi.nlm.nih.gov/gene/?term=STAT1, accessed on 20 April 2024), the protein ID and its sequence were extracted from UniProtKB in Swiss-Prot databases with the accession number P42224 (https://www.expasy.org/search/uniprot, accessed on 20 April 2024) [34].


### 2.2. Phenotype Prediction of Deleterious ns SNPs
  We predicted the deleterious nsSNPs by using eight different tools. Sorting Intolerant from Tolerant (SIFT) (http://sift.bii.a-star.edu.sg/, accessed on 20 April 2024) predicts whether the replacement of an amino acid alters protein function. We downloaded nsSNP IDs from the online databases of NCBI and then uploaded them to SIFT. Results were documented as damaging (deleterious) or benign (tolerated), depending on the cutoff value of 0.05, as values less than or equal to (0.0–0.04) were predicted to be damaging or intolerant, while (0.05_1) is benign or tolerated [35].

  Polyphen-2 (http://genetics.bwh.harvard.edu/pph2/, accessed on 20 April 2024) analyzes multiple sequence alignments and the protein’s three-dimensional structure, then predicts the possible impact of amino acid substitutions on the stability and function of human proteins using structural and comparative evolutionary considerations. The prediction outcomes are classified as probably damaging, possibly damaging, or benign based on the position-specific independent counts value (PSIC), which ranges from 0 to 1. Values near zero are regarded as benign, while values near one are considered probably damaging [36].

  Provean (https://www.jcvi.org/research/provean/, accessed on 20 April 2024) is a software tool that predicts whether an amino acid substitution or indel has an impact on the biological function of a protein. Variants with a score equal to or below −2.5 are considered deleterious, while variants with a score above −2.5 are neutral [37].

  SNAP2 (https://rostlab.org/services/snap2web/, accessed on 20 April 2024) is a trained classifier that uses the “neural network” machine learning tool to predict the functional effects of mutations by utilizing several sequence and variant properties to discriminate between effect and neutral variants/nonsynonymous SNPs [38].

  PHD-SNP (https://snps.biofold.org/phd-snp/phd-snp.html, accessed on 20 April 2024) uses a support vector machine (SVM)-based method trained to determine disease-associated nsSNPs using sequence information. PHD-SNP classifies mutations either to be disease-related (disease) or a neutral polymorphism [39].

  SNP and GO (https://snps-and-go.biocomp.unibo.it/snps-and-go/, accessed on 20 April 2024) is a server for the prediction of single-point protein mutations likely to be involved in the development of diseases in humans [40].

  P-Mut is a web-based tool for the annotation of pathological variants on proteins. It allows fast and accurate prediction of the pathological properties of single-point amino acid mutations based on the use of a neural network. It is available at (http://mmb.irbbarcelona.org/PMut, accessed on 20 April 2024) [41].

  Protein Analysis through Evolutionary Relationships (PANTHER) (http://pantherdb.org/, accessed on 20 April 2024) uses a position-specific evolutionary preservation (PSEP) score to measure the length of time (in millions of years), with <200 my “probably benign”, <450 my “possibly damaging”, and 450 my “probably damaging” [42].


### 2.3. Predicting Functional and Structural Effects of the nsSNP
  MutPred v1.2 (http://mutpred.mutdb.org/, accessed on 20 April 2024) is used for sorting disease-associated or neutral amino acid substitutions in humans. MutPred is an efficient web-based application tool that screens amino acid substitutions and predicts the molecular base of the disease [43].


### 2.4. Protein Stability Analysis of Predicted STAT1 nsSNPs
  I-Mutant 3.0 is available at (https://gpcr2.biocomp.unibo.it/cgi/predictors/I-Mutant3.0/I-Mutant3.0.cgi, accessed on 20 April 2024); it is a neural-network-based tool for routinely analyzing protein stability and change while taking single-site mutations into consideration [44]. The FASTA sequence of proteins retrieved from UniProt is used as an input to predict the mutational effect on protein stability.

  MUpro, a group of machine learning methods, predicts the effects of single amino acid substitutions on protein stability [45]. It uses both support vector machines and neural networks; the output is either increased or decreased stability [45]. MUpro also interprets the result based on Gibbs free energy (ΔΔG), with a confidence score between −1 and 11. It is available at http://mupro.proteomics.ics.uci.edu, accessed on 20 April 2024.

  DDMUT (https://biosig.lab.uq.edu.au/ddmut/, accessed on 20 April 2024) is a fast and accurate network using deep learning models to predict changes in Gibbs free energy (ΔΔG) upon single- and multiple-point mutations [46]. DDMut achieved a Pearson’s correlation of up to 0.70 (RMSE: 1.37 kcal/mol) on predicting single-point mutations on cross-validation and 0.74 (RMSE: 1.67 kcal/mol) on multiple mutations.


### 2.5. Prediction of Missense Variant Pathogenicity
  Alpha Missense is an adaptation of alphafold fine-tuned on human and primate variant population frequency databases to predict missense variant pathogenicity. It works by combining structural context and evolutionary conservation. This model achieves state-of-the-art results across a wide range of genetic and experimental benchmarks, all without explicitly training on such data [47].


### 2.6. Three-Dimensional Structure Prediction and Visualization
  We predicted the 3D structure using an artificial intelligence system, AlphaFold (https://alphafold.ebi.ac.uk, accessed on 20 April 2024). Alphafold is an artificial intelligence system developed by google DeepMind. It predicts a protein’s 3D structure from its amino acid sequence. It can predict protein structures computationally with high accuracy [48]. We used the UniProt sequence of the STAT1 protein as an input to obtain the alphafold model.

  UCSF ChimeraX 1.9 is a robust application that enables interactive viewing and analysis of various molecular structures and related data, including density maps, sequence alignments, and supramolecular assemblies [49]. It allows the mapping and visualization of amino acid substitutions. Chimera X is available at https://www.rbvi.ucsf.edu/chimerax/, accessed on 20 April 2024.


### 2.7. Phenotypic Effects Prediction
  Project Hope (version 1.0) is an online web server used to analyze the structural and conformational variations that have resulted from single amino acid substitutions [50]. We uploaded STAT1 protein sequence, wild-type amino acids, and mutants. The results provided describe the change in the physiochemical properties of the amino acid in the given SNPs. It is available at (https://www3.cmbi.umcn.nl/hope/method/, accessed on 20 April 2024).

  DDMUT can also detect changes in the biological interactions between wild-type amino acids and neighborhood residues in comparison with mutant residues [46].


### 2.8. Conservational Analysis and Surface Accessibility Prediction of STAT1
  The ConSurf bioinformatics tool (https://consurf.tau.ac.il, accessed on 20 April 2024) was used to study the evolutionary conservation of nsSNP positions in a protein sequence [51]. We submitted the FASTA sequence of the STAT1 protein to the server, and we screened out the highly conserved residues, exposed and buried residues.


### 2.9. Identification of nsSNPs in STAT1 Protein Domains
  We submitted the FASTA sequence of the STAT1 protein to the InterPro server (https://www.ebi.ac.uk/interpro, accessed on 20 April 2024). It predicts protein families and conserved domains, and then we manually pinpointed the positions of nsSNPs within these domains [52].


### 2.10. Prediction of Protein–Protein Interactions
  A precomputed database, STRING (https://string-db.org/, accessed on 20 April 2024), is used to determine protein–protein interactions to understand the function, structure, molecular action, and regulation of the protein [53]. We submitted the protein sequence as an input query.


## 3. Results

### 3.1. Distribution of STAT1 Gene SNP Datasets
  The total number of SNPs was 10,989. There were 888 frame shift mutations; 480 SNPs located in the coding region, of which 247 were nsSNPs and 233 were synonymous SNPs (sSNPs), while 9.621 SNPs were in noncoding regions, of which 375 occurred in the 3′UTR, 131 in the 5′UTR region, and the rest (9115) were in the intronic region, as shown in Figure 2. We chose nonsynonymous coding SNPs for our investigation.


### 3.2. Identification of Deleterious Missense Mutation
  All 247 nsSNPs were retrieved and subjected to pathogenicity prediction web servers. Sixty-four nsSNPs were found to be deleterious by SIFT and were further subjected to crosschecking by using three different tools (Poly-Phen-2, PROVEAN, and SNAP2).

  The shortlisted 33 nsSNPs passed the first four tools, presented in Table 1, then were submitted to another set of four tools: P Mut, PhD-SNP, SNPs and GO, and PANTHER. In total, 29 SNPs out of the 33 predicted by the first set of tools are disease-causing by P mut, 21 out of 33 are disease-causing by Panther, 20 are disease-causing by PhD-SNP, and 14 out of 33 by SNP and GO. A final nine nsSNPs passed all eight tools shown in Table 2. We further analyzed the final set of SNPs for the functional and structural modifications.


### 3.3. MutPred Prediction for Functional and Structural Modifications
  We submitted the shortlisted nine nsSNPs to the MutPred server, along with the resultant probability scores and their p values in Table 3. The structural and functional alterations predicted include loss of disorder, catalytic residue, glycosylation, gain of phosphorylation, solvent accessibility, ubiquitination, and molecular recognition features (MoRF) binding. According to these predictions, several nsSNPs might be the reason behind any possible structural and functional modifications of STAT1 protein.


### 3.4. Prediction of Change in STAT1 Stability Due to Mutation
  We used I mutant, MUpro, and DDMUT servers to predict the effect of the nsSNPs on protein stability. The result revealed that six variants destabilized the STAT 1 protein, namely (I648T) rs759271255, (V642D) rs752542806, (R602W) rs 1209841496, (L600P) rs137852678, (I578N) rs767475430, and (W504C) rs916580554. The results are presented in Table 4.


### 3.5. Pathogenicity Prediction Results
  We analyzed STAT1 nsSNP by Alpha-Missense, and we found that all the pathogenic nsSNPs that were predicted by the previous tools were also classified as pathogenic in Alpha-Missense, presented in Table 5. The heat map represented the mutations in STAT1, as shown in Figure 3.


### 3.6. The Conservational Status and Surface Accessibility Analysis of STAT1 Protein
  Highly conserved residues are most likely to be involved in proteins’ structural integrity and functions. We evaluated the conservational profile for the STAT1 protein. The ConSurf algorithm represented the structural and functional conservation levels of all the amino acid residues of the STAT1 protein. Four SNPs (I648T, L600P, W504C, and I578N) are predicted to be located in a conserved region. L600P and I578N are predicted to be structural residues (highly conserved and buried). V642D is predicted as buried, and R602W is predicted as a functional residue (highly conserved and exposed), presented in Table 6.


### 3.7. Three-Dimensional Structure Prediction by AlphaFold and SNP Visualization by ChimeraX
  An individual residue confidence score (pLDDT) between 0 and 100 is generated by the AlphaFold algorithm. Alphafold produces a per residue confidence score (pLDDT) 1–100. Regions with low pLDDT may be unstructured in isolation. The majority of the 3D structural region corresponds to alpha-helical domains and has extremely high confidence (pLDDT > 90). The remaining components of the model are depicted as unresolved loops with low (70 > pLDDT > 50) and extremely low (pLDDT > 50) scores, as in Figure 4.

  We used ChimeraX to visualize the 3D structures of the wild-type amino acids in blue and the mutant residues in red, as shown in Figure 5.


### 3.8. The Physical Outcome of Predicted SNPs
  We examined the impact of the generated damaging SNPs on the three-dimensional structure of STAT1 using the HOPE server. The server predicted that all the mutated amino acids were different in size; one had a different charge, and six had different hydrophobicity. The results are in Table 7.

  Loss of the interactions between the wild-type amino acid and other amino acids in the protein and/or development of new interactions or bonds between the mutant residue of the protein and the other amino acids in the protein were predicted by DDMUT, as presented in Figure 6.


### 3.9. Domain Identification of the STAT1 Protein by the InterPro Server
  The InterPro tool predicted the domain regions of the STAT1 protein. The STAT1, SH2 domain (a phosphotyrosine binding pocket) at position (557–707), STAT transcription factor, DNA binding domain at (323–458), and STAT1_TAZ2-binding domain (715–739) are conserved sites. Src homology 2 (SH2) domain profile (573–670), SH2 domain (578–638), STAT1 transcription factor, all alpha domain (144–305), and STAT transcription factor protein interaction (2–12) are as in Table 8.


### 3.10. STAT1–Protein Interaction
  Analysis of protein–protein interaction using the STRING network revealed that STAT1 interacts with 10 proteins, which include other proteins of the same STAT family (STAT2 and STAT3), proteins of the JAK family (JAK1 and JAK2), IFR1, IFR9, IFNGR1, CREBBP, KBNA1, and PIAS1, as presented in Figure 7.


## 4. Discussion
  We evaluated the functional and pathogenic sequences of missense SNPs of the human STAT1 gene, utilizing 12 diverse in silico prediction tools (SIFT, PolyPhen2, PROVEAN, PANTHER, P MUT, PhD-SNP, SNPs&GO, SNAP2, and MutPred2). In silico prediction analysis identified six variants (I648T, V642D, R602W, L600P, I578N, and W504C) considered pathogenic and deleterious. These mutations have a major impact on the protein’s physicochemical characteristics, such as its size and charge hydrophobicity, which ultimately affect the protein’s stability and function and may have an impact on disease. Furthermore, we assessed the effect of missense SNPs on the stability of the STAT1 structure utilizing three stability prediction algorithms: I-Mutant3, MUpro, and DDMUT. All the variants revealed a reduction in stability by the three stability prediction tools (I-Mutant3, MUpro, and DDMUT). In general, we assumed that all missense SNPs in the STAT1 gene were highly unstable in their protein structures, so they were selected for further structural bioinformatics analysis utilizing various tools to explore the consequences of tentatively destructive missense SNPs on STAT1 protein function. To evaluate the conservation profile, we used the ConSurf algorithm to represent the structural and functional conservation levels of all the amino acid residues of STAT1 protein. The ConSurf analysis revealed that the variant in position 602 is a functional residue in a highly conserved and exposed position. Structural residues in highly conserved and buried positions were identified in positions 600 and 578. The identified variants were found in a highly conserved region; this finding suggests that they might be involved in modifications of molecular mechanisms such as bond gain or loss.

  STAT1 GOF mutations with CMC were first described in 2001 and 2011, respectively; later, studies confirmed that STAT1-GOF mutations cause immunodeficiency and immune dysregulation, with a wide clinical spectrum [54].

  Among the six SNPs identified linked to STAT1 gene mutations in this study, some of these SNPs have been associated with diseases in previous studies, while others were projected to be so in this study using various computational tools. Population genetics and clinical studies are crucial to verifying the results of such research, even though utilizing computational techniques to analyze the impact of the SNPs may aid in identifying disease-related SNPs.

  One mutation, namely L600P, has already been previously reported as a mutation in the STAT1 gene in an infant who died of a viral-like illness associated with complete STAT1 deficiency and carried a homozygous nucleotide substitution (T→C) in exon 20, resulting in the substitution of a proline for a leucine at amino acid position 600 [55]. This mutation was found to be pathogenic using all the bioinformatics tools. I648T, V642D, R602W, I578N, and W504C were not reported previously.

  Three mutations, namely L706S (rsRCV000009610), Q463H (VAR_065817), and E320Q (VAR_065816), have been reported as mutations in the STAT1 gene. The two previously reported types of autosomal-dominant (AD) Mendelian susceptibility to mycobacterial disease (AD-MSMD) causing STAT1 mutations are located in the tail segment domain (p.L706S) or in the DNA-binding domain (p.E320Q and p.Q463H) [56]. These mutations were not available in the dbSNP database. Two other SNPs (K637E) and (K673R) affecting the SH2 domain, which has been previously reported in two cases with AD-STAT1 deficiency in two unrelated patients from Japan and Saudi Arabia, were also not available in the dbSNPs database at the time of the analysis [56].

  Two mutations linked to chronic mucocutaneous candidiasis are (T437I) and (Q271P). Q271P occurred within a specific pocket of the STAT1 coiled-coil domain, near residues essential for dephosphorylation, and was identified in a German patient who presented at 1 year of age with autosomal dominant chronic mucocutaneous candidiasis, showed signs of thyroid autoimmunity, and died at age 41 from squamous cell carcinoma [57,58]. These mutations were not available in the dbSNPs database.

  The A267V variant in STAT1 has been reported in >10 individuals with chronic mucocutaneous candidiasis (CMC) and segregated with disease in 16 individuals from nine families [59]. This mutation was not present in the dbSNP database.

  Interestingly, nsSNPs in the STAT1 gene will ultimately affect and may disturb the normal function of other interacting genes. As our study was in detail, it provides all the information and analysis needed for the identification of the most damaging nsSNPs. Like ours, there are certain limitations in every study. Utilizing in silico technologies is now a crucial method for identifying disease-related SNPs. In this study, the STAT1 gene underwent a thorough analysis utilizing 18 genetics analysis tools (10 computational tools and 8 AI-based methods) to determine the impact of nsSNPs on the protein’s structure and function.

  Our study is based on computer tools and web servers, which are based on mathematical and statistical algorithms. Therefore, to confirm these results, experimental investigation is necessary.


## 5. Conclusions
  Our study provides an insight about nsSNPs of the STAT1 gene, its protein 3D structure, and its interactions with other genes, which might be helpful in future studies of STAT1 in order to better understand its role in immunity and all related diseases.