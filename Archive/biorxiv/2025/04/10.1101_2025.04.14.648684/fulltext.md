## Abstract

This study investigates the critical role of the dimeric GrpE protein as a thermosensor within bacterial DnaK complexes, with a specific focus on All4144, a GrpE homolog found in Anabaena sp. PCC7120. In the present work, we characterized All4144, which possesses both the GrpE domain and a helix-turn-helix (HTH) domain. Our aim was to elucidate the functional significance of the HTH domain by selectively deleting the region encompassing residues 1-67 from the full-length All4144. Our findings reveal that both All4144 and its deletion mutant function as homo-dimeric nucleotide exchange factors for DnaK, enhancing the ATPase and refolding activities of DnaK. Additionally, All4144 plays a role in DNA binding. On the contrary, the deletion mutant lacking the HTH motif exhibits impaired DNA-binding ability, underscoring the importance of the HTH domain. Moreover, All4144 superior cell survival and thermal stability profiles, compared to the deletion mutant. Taken together, our study sheds light on the multifunctional nature of All4144, highlighting its pivotal role in modulating thermal tolerance through interactions with DnaK and DNA.


## 1. Introduction

Cyanobacteria are a specialized group of nitrogen-fixing, photosynthetic prokaryotes widely distributed in aquatic and terrestrial habitats ( 1 ). Their evolutionary significance relies on their ability to cope with challenging environmental conditions, such as high light intensity, fluctuating temperature, UV-B, and nutrient deprivation ( 2 ). Proteomic investigations have unveiled that cyanobacteria respond to such stresses by upregulating the expression of various stress-responsive proteins, particularly heat shock proteins (Hsps) ( 2 ). Heat shock proteins, acting as molecular chaperones, play a crucial role in maintaining protein homeostasis by mediating conformational changes and preventing protein aggregation and degradation under abiotic stresses ( 3 ). The DnaK (bacterial Hsp70) system is the most studied molecular chaperone, ubiquitously found across all domains of life, and its activity is dependent on two co-chaperones: DnaJ and GrpE ( 4 ). Co-occurrence analysis in Nostoc punctiforme has revealed the conserved presence of the DnaK-DnaJ-GrpE chaperone system in cyanobacteria ( 5 ). DnaJ, an Hsp40 homolog, stimulates ATP hydrolysis and targets substrate protein to ADP-bound DnaK/Hsp70 ( 6 ), while GrpE acts as a nucleotide exchange factor (NEF), facilitating ADP/ATP exchange and influencing the longevity of the DnaK-substrate complex ( 7 ).

The expression of GrpE in bacteria is a responsive measure triggered by various stressors, including heat shock, nutrient deprivation at low temperatures, and oxidative stresses, underscoring its pivotal role in the intricate web of stress responses ( 8 ). This responsiveness emphasizes GrpE’s adaptive nature, aligning with the dynamic needs of the cellular environment under challenging conditions.

In contrast to prokaryotes, eukaryotic homologs of GrpE exhibit noteworthy divergence in sequence identity. Instances include the identification of Mgelp in yeast ( 9 ) and GrpEL1 and GrpEL2 in mammalian mitochondria ( 10 ). Notably, BAG1 emerges as a functional homolog of GrpE specifically for cytosolic Hsp70s in mammals, further highlighting the versatility and conservation of this essential chaperone system across evolutionary boundaries ( 11 ). Structurally, GrpE proteins comprised of three domains: a long paired α-helix, a four-helix bundle-forming domain, and a C-terminus β-sheet domain ( 12 ). The long paired α-helices act as a thermosensing domain, undergoing helix-to-coil transitions to prevent thermal denaturation of substrate proteins during heat shock ( 13 ). Further, crystal structure analysis of GrpE from Thermus thermophilus HB8 revealed that thermosensing action of the GrpE is related to its structural characteristics ( 14 ) and mediated by different protein domains i.e. either N-terminus or C-terminus. Despite the well-characterized thermosensing action and function of GrpE as a nucleotide exchange factor, there is no concrete evidence of the diversified biological function of GrpE in prokaryotes. Only fragmentary information is available regarding cyanobacteria e.g. upregulation of a heat shock GrpE protein (Sll0057) in Synechocystis sp. when exposed to hexane ( 8 ).

Furthermore, GrpE protein has been characterized as a thermosensor in the thermophilic cyanobacterium Thermosynechococcus elongatus BP1 and mesophilic Synechocystis sp. PCC 6803 ( 12 ). Recently, we have observed that DnaJ III of Anabaena sp. PCC7120 imparts heat stress tolerance in E. coli and stimulates DnaK’s ATPase activity. However, it was not established how activity of the DnaK-DnaJIII chaperone/co-chaperone complex is associated with the co-chaperone GrpE in Anabaena sp. PCC7120 ( 15 ). This study investigates the functional characteristics of the GrpE homolog, All4144, in Anabaena sp. PCC7120. Notably, All4144 exhibits a helix-turn-helix (HTH) domain alongside the conventional GrpE domain. To elucidate the specific function of the HTH domain within GrpE and its implication in DNA binding, we deliberately generated a deletion mutant, All4144(68–214), which lacks the HTH domain. Through a comparative analysis of the full-length All4144 and the deletion mutant using biophysical and biochemical assays, we aim to assess the role of the intact additional HTH domain in conferring multi-functionality, such as thermal tolerance, co-chaperone activity, and DNA binding capability.


## Material and methods


## Cyanobacterial and bacterial strains and plasmids

Anabaena sp. PCC7120 (hereafter Anabaena sp. ) was cultivated photoautotrophically in BG-11 medium at 24 ± 2°C, pH 7.4, under daylight fluorescent illumination providing 72 μmol m⁻² s⁻¹ of photosynthetically active radiation (PAR) with a 14 h light/10 h dark cycle. The cultures were stirred three times per day. For cloning and protein overexpression, Escherichia coli strains DH5α and BL21(DE3) (Novagen) were used as hosts. Recombinant E. coli cultures were maintained in LB medium supplemented with 50 μg/mL kanamycin ( 16 ). The pET-28a(+) plasmid (Novagen) was employed for cloning and expression of the target proteins.


## In-silico analysis

Functional domains of All4144 were analyzed using InterPro-Scan ( http://www.ebi.ac.uk/interpro ) ( 17 ) and the Conserved Domain Database (CDD) ( http://www.ncbi.nlm.nih.gov ) ( 18 ). Homology searches were performed using BLASTp from the NCBI database. Multiple sequence alignments were generated using PROMALS-3D (prodata.swmed.edu/promals3d/) ( 19 ). The I-TASSER server ( 20 ) was employed to generate a three-dimensional homology model of All4144.


## Model Validation and docking

To validate the structural integrity of the generated models, we utilized PROTEK and RAMPAGE as quality assessment tools ( 21 ). PROTEK was employed to evaluate the overall structural geometry, ensuring that the model maintained proper folding and stability. Additionally, RAMPAGE was used to generate a Ramachandran plot , which classified the backbone dihedral angles (ϕ and ψ) of amino acid residues into favored , allowed , and outlier regions. The majority of the residues were located in the favored and allowed regions, confirming that the stereochemistry of the model was within acceptable ranges for high-quality protein structures. Further we have used H-DOCK for protein-receptor docking which uses surface and electrostatic scoring function for protein-protein interactions ( 22 ). Best docked pose was selected using the in-built scoring function of H-DOCK.


## Transcript analysis of all4144

Total RNA was isolated from a 100 mL culture of Anabaena sp. (OD750 = 0.6) after exposure to arsenic (40 mM, 24 h) ( 23 ), heat (42°C, 1 h) ( 24 ), NaCl (100 mM, 24 h) ( 25 ), UV-B (12.9 mW/cm², 30 min) ( 26 ), and cadmium (10 µM, 24 h) ( 27 ). cDNA was synthesized from the isolated RNA using the iScript cDNA Synthesis Kit (BioRad). Gene-specific primers were designed using Primer3 (version 4.0, https://primer3.org ). Quantitative real-time PCR (qRT-PCR) was performed using 12 ng of cDNA from each sample in triplicate reactions, on a 96-well plate with a total volume of 20 µL, including 10 pmol of forward and reverse primers, and 1× SsoFast EvaGreen qPCR supermix (BioRad). Relative expression of the all4144 gene was calculated using the ΔCq method ( 28 ), normalized to rnpB transcript levels. Specificity of the PCR products was confirmed by melting curve analysis.


## Rationale and design of the deletion mutant of All4144

Conserved domain analysis ( Fig.1a ) identified All4144 as a member of the GrpE family, containing a helix-turn-helix (HTH) domain at the N-terminus (residues 1–67) and a GrpE domain at the C-terminus (residues 68–214). To evaluate the potential role of the HTH domain in GrpE function, an N-terminal deletion mutant, All4144(68–214), was generated by removing amino acids 1–67, as shown in ( Fig. 1b-c ).


## Cloning, expression and purification of All4144 and All4144(68–214)

Genomic DNA from Anabaena sp. was isolated and used for PCR amplification of all4144 and all4144 (68–214), which were cloned into the pET28a(+) plasmid at the NdeI and XhoI restriction sites. The recombinant plasmids were transformed into E. coli BL21, and protein expression was induced with 0.2 mM IPTG. Recombinant cells carrying all4144 and all4144 (68–214) were grown in LB broth containing 25 µg/mL kanamycin at 37°C with shaking at 160 rpm until the optical density at 600 nm reached 0.3. Protein expression was induced by adding 0.2 mM IPTG, followed by growth at 18°C for 14 h at 160 rpm. Cells were harvested by centrifugation at 15,000×g for 15 min at 4°C, and resuspended in 8 mL of cold lysis buffer (20 mM Tris-HCl, 500 mM NaCl, 40 mM imidazole, pH 7.8). Cell lysis was performed using ultrasonic treatment, and the lysate was clarified by centrifugation at 13,000×g for 50 min at 4°C. His-tagged proteins were purified from the supernatant using a His-Trap Nickel-NTA column (Bio-Rad). Eluted protein fractions were analyzed by SDS-PAGE (12%), and fractions with >95% purity were pooled and concentrated using a 10 kDa Amicon concentrator (Millipore). Protein concentrations were determined by absorbance at 280 nm.


## Cell survival study

The impact of heat stress was assessed using a spot assay, as described previously ( 29 ). In brief, recombinant cells and empty vector control (pET28a) were cultured in LB medium containing 50 µg/mL kanamycin at 37°C. Once the cultures reached an OD 600 of 0.6, they were induced with 0.2 mM isopropyl β-D-1-thiogalactopyranoside (IPTG) and incubated for an additional 5–6 h at 16°C. The IPTG-induced E. coli cells were then heat-treated at 50°C for 30, 60, and 90 min. Cultures were serially diluted (10⁻¹, 10⁻³, and 10⁻⁵), and 5 µL of each dilution was spotted onto LB-agar plates containing kanamycin. The spot assay results were further validated by SDS-PAGE analysis, where cells grown at 37°C and 50°C were harvested, proteins were isolated, and the expression was evaluated by SDS-PAGE. To ensure accurate comparisons, we used the housekeeping gene β-actin as a reference control.

Quantitative analysis of the impact of heat stress on genetically modified E. coli BL21 (DE3) strains was conducted using the colony-forming unit (CFU) count method. Following the same growth and induction protocol as the spot assay, a 50 μl aliquot of a culture diluted to 10 −3 was evenly spread onto LB-kanamycin plates. Bacterial colonies were counted, and CFU was calculated using the formula: CFU = (number of colonies × dilution factor) / volume of culture plated.


## Intracellular reactive oxygen species (ROS) measurement

Intracellular reactive oxygen species (ROS) generation under heat stress conditions was measured using 2,4-dichlorofluorescein diacetate (H₂DCFDA) following the protocol by Jakubowski and Bartosz ( 30 ). Overnight cultures of E. coli BL21 (DE3) cells harboring either an empty vector (pET-28a) or recombinant plasmids, pET-28a-all4144 and pET-28a-all4144(68–214), were grown in LB medium containing 50 µg/mL kanamycin. A 100 µL aliquot of these cultures, at OD600 = 0.6, was inoculated into 50 mL of LB medium supplemented with 0.2 mM IPTG. Cultures were subjected to heat stress at 50°C or maintained at 37°C as a control, shaking at 200×g for 60 min. After incubation, cells were harvested by centrifugation, washed, and resuspended in PBS buffer (pH 7.4). ROS generation was assessed by adding 10 µM H₂DCFDA (dissolved in ethanol) to the cell suspension, followed by incubation at 37°C for 30 min. ROS production was quantified using a Cary Eclipse LS-5B spectrofluorimeter with excitation at 490 nm and emission at 520 nm.


## Circular dichroism (CD) and DSC analysis

Circular dichroism (CD) spectra for full-length All4144 and its deletion mutant, All4144(68–214), were recorded in the far-UV region (190–250 nm) at a concentration of 5 µM in 25 mM phosphate buffer (Buffer A). CD measurements were conducted on a Jasco J-810 spectropolarimeter, using a 2-mm path length quartz cell. Temperature was incrementally varied from 20°C to 80°C, with a response time set at 50 nm/s. Prior to each sample measurement, a baseline spectrum of Buffer A was obtained and subtracted. Additional thermal scans were performed at 222 nm to monitor changes in α-helical content. For each sample, three scans were collected and averaged to improve data reliability. Melting temperatures (T_m) were determined from spectral data at specific wavelengths indicative of secondary structural elements and were fit to a sigmoidal curve (Boltzmann distribution), indicating cooperative unfolding behavior consistent with a two-state mechanism, where structural transitions occur concertedly across the molecule.

Differential scanning calorimetry (DSC) was performed according to a previously described method ( 31 ), with modifications. In brief, purified proteins in buffer C were analyzed using a DSC instrument (Mettler Toledo 822E, India). Samples (5 µM) were weighed into sealed aluminum crucibles, and thermal analysis was conducted in a nitrogen-depleted atmosphere over a temperature range of 0–200°C at a heating rate of 10°C/min. This method was employed to measure the excess heat capacity as a function of temperature and to calculate the calorimetric enthalpy of thermal unfolding (ΔH_cal) for both proteins ( 32 ).


## Cross-linking by glutaraldehyde

Glutaraldehyde crosslinking of proteins in their native state was conducted as previously described ( 33 ). Briefly, 5 µM of All4144 and its deletion mutant proteins were diluted in buffer A to a final reaction volume of 25 µL. Protein solutions were incubated at 37°C for 8 min, either in the absence or presence of 1.5 µL freshly prepared 0.025% glutaraldehyde solution. Following incubation, an equal volume of 2X Laemmli sample buffer was added, and the mixtures were heated at 90°C for 3 min. The crosslinked proteins were separated by 12% SDS-PAGE and visualized with Coomassie brilliant blue staining.


## Refolding assay

Malate dehydrogenase (MDH) was chemically denatured by incubating it for 24 h in a buffer containing 6 M guanidine hydrochloride (GdnHCl), 50 mM Tris-HCl (pH 7.5), 5 mM MgCl₂, and 2 mM dithiothreitol (DTT). Refolding of denatured MDH (5 nM) was performed using a previously described method ( 34 ). The denatured MDH was diluted in a buffer consisting of 100 mM Tris-HCl (pH 7.5), 3 mM glucose 6-phosphate, 5 µM ATP, and 150 mM NAD. The refolding reaction included DnaK (1 µM), DnaJ (1 µM), and either All4144 or the deletion mutant protein (2 µM), and was incubated for varying durations. Kinetics of MDH refolding were monitored using a spectrophotometer at a wavelength of 340 nm.


## ATPase activity assay

DnaK ATPase activity was measured with modifications based on the method described by Lanzetta et al. ( 35 ). Briefly, a reaction mixture containing 1 µM recombinant DnaK, 1 µM DnaJ, and 2 µM of either full-length All4144 or All4144(68–214) proteins was incubated in ATPase assay buffer C, which comprised 30 mM Tris, 50 mM KCl, 0.6 mM dithiothreitol (DTT), 2 mM MgCl₂, 1 mM ATP, and 10% (v/v) glycerol. A control reaction was established that excluded DnaJ, All4144, and the deletion mutant proteins, including only DnaK in the buffer. Reactions were initiated by the addition of 1 mM ATP and incubated at 25 °C. At various time intervals, reactions were quenched by adding 4 M formic acid. Values were monitored using a spectrophotometer at a wavelength of 650 nm.


## Tryptophan quenching analysis DnaK

The intrinsic tryptophan fluorescence of DnaK was measured using a Perkin-Elmer LS-5B Cary Eclipse spectrophotometer. Nucleotide-free DnaK, at a concentration of 1 µM, was analyzed at 25 °C in a buffer composed of 50 µM Tris-HCl (pH 7.5), 100 mM KCl, 5 µM MgCl₂, 2 mM EDTA, and 2 mM dithiothreitol (DTT). Emission spectra were recorded with a fixed excitation wavelength of 290 nm. For the experiments involving ADP, ATP, All4144, and the deletion mutant protein, 2 µM of each component was added to the DnaK sample. ATP or ADP was introduced from a stock solution (100 µM), and the mixture was incubated for 5 min in the cuvette at room temperature. Emission spectra were then recorded over a wavelength range from 300 nm to 400 nm ( 36 ).


## Electrophoretic mobility shift assay

Electrophoretic mobility shifts assays (EMSAs) were conducted with minor modifications based on previously described methods ( 37 ). Briefly, 1 µM protein samples were incubated with double-stranded DNA (dsDNA) (501 bp) and single-stranded DNA (ssDNA) (60 bp) in a total volume of 12 µL of binding buffer (50 mM Tris, pH 7.45; 750 mM KCl; and 0.5 mM dithiothreitol [DTT]), in the absence and presence of 1 mM ATP and ADP. The samples were incubated for 15 min at 25 °C before being loaded onto 1% agarose gels for electrophoresis in 1X TBE buffer for 90 min. Following electrophoresis, the gels were stained with ethidium bromide and imaged using a gel documentation system to visualize the DNA-protein complexes.


## Statistical analysis

All experiments were performed in triplicate, and statistical significance was assessed using analysis of variance (ANOVA) with SPSS software (SPSS Inc., Chicago, IL, USA). Graphical representations of the data were created using GraphPad Prism 8 and Origin 9 (Origin Lab, USA), with values expressed as mean ± standard error of the mean (SEM).


## 3. Result


## Transcript analysis of all4144 under multiple abiotic stresses using quantitative RT-PCR

Transcript profiling of all4144 was conducted under various abiotic stresses, including heat, UV-B, cadmium, arsenic, and salt. The expression of all4144 was significantly upregulated under heat, cadmium, and UV-B stress, showing increases of approximately 13.4 ± 1.9, 7.2 ± 0.9, and 4.1 ± 0.8 folds, respectively, compared to the control ( Fig. 1d ). In contrast, the fold changes in response to arsenic and salt stress were only 0.8 ± 0.2 and 2.0 ± 0.59, respectively.


## Purification and Secondary Structure of All4144 and All4144(68–214)

The open reading frames of all4144 and its deletion mutant all4144 ( 68–214 ) were amplified to investigate the products of the heat-inducible gene. Transformants of E. coli BL21(DE3) were generated, resulting in substantial production of soluble proteins with molecular weights of 24 kDa and 16 kDa, respectively ( Fig. 1f ). Western blot analysis using an anti-His antibody confirmed successful protein expression ( Fig. 1g ). Additionally, Far-UV circular dichroism (CD) analysis indicated that both All4144 and All4144(68–214) exhibit a significant α-helical content and an approximate β-pleated component, confirming that both proteins are well-folded ( Fig. 1e ).


## Cell survival study

Cell survival analysis of recombinant E. coli strains and the control (pET28a) was assessed using a spot assay and colony-forming unit (CFU) count. Spot assays were performed at 37°C and 50°C for 30, 60, and 90 minhou. The results indicated that both recombinant strains, BL21/pET-28a-all4144 and BL21/pET-28a-all4144(68–214), exhibited increased heat resistance compared to the vector control (BL21/pET-28a). Notably, the wild-type all4144 strain demonstrated superior growth under heat stress conditions compared to the deletion mutant BL21/pET-28a-all4144(68–214) ( Fig. 2a-b ).

Quantitative validation of these observations was obtained through CFU count analysis ( Fig. 2d ). CFU results showed comparable spot densities for BL21/pET-28a and the recombinant cells at 37°C. However, at 50°C, BL21/pET-28a-all4144 exhibited a substantial increase in spot density relative to the control, with fold changes of approximately 1.4, 2.8, and 5 at 30, 60, and 90 min, respectively. In contrast, BL21/pET-28a-all4144(68–214) cells showed fold changes of 1, 1.6, and 1.2, indicating a less pronounced response to heat stress than BL21/pET-28a-all4144.

SDS-PAGE analysis of protein expression under heat stress revealed higher protein expression levels at 50°C compared to 37°C and the control ( Fig. 2c ), indicating that both proteins (All4144 and the deletion mutant) upregulate in response to heat stress.

To further evaluate the reactive oxygen species (ROS) generation following the spot assay and CFU count. We found that both BL21/pET-28a-all4144 and BL21/pET-28a-all4144(68–214) exhibited decreased H 2 DCFDA dye intensity compared to the control (BL21/pET-28a), indicating reduced ROS production ( Fig. 2e ). However, BL21/pET-28a-all4144 demonstrated better heat tolerance than the deletion mutant, suggesting that the HTH domain impacts on cell survival under heat stress conditions.


## Thermal stability of All4144 and All4144(68–214)

The thermal stability of the full-length protein All4144 and its deletion mutant, All4144(68–214), was examined using circular dichroism (CD) spectroscopy and differential scanning calorimetry (DSC). CD spectroscopy revealed that both proteins maintained their secondary structure up to approximately 60 °C, with All4144 showing a higher α-helical content compared to the deletion mutant ( Fig. 3a-b ). The thermal unfolding profile was tracked by the decline in ellipticity at 222 nm, a wavelength sensitive to helical content, with All4144 exhibiting a main thermal transition at ∼65.24 °C, whereas All4144(68–214) displayed a lower thermal transition midpoint at ∼60.78 °C. Additionally, an early thermal transition observed between 30-40 °C in both proteins may indicate a potential physiological role at this temperature range ( Fig. 3c-d ). DSC analysis provided further insights, revealing two distinct thermal transitions in both proteins. For the full-length All4144, transitions were observed at 37.50 ± 0.07 °C and 101.17 ± 0.08 °C, suggesting significant structural stability across a wide temperature range. In contrast, All4144(68–214) displayed transitions at 39.91 ± 0.03 °C and 76.30 ± 0.05 °C, indicating a reduced thermal stability in the deletion mutant. Together, these findings from CD and DSC analyses suggest that All4144 has enhanced thermal stability compared to All4144(68–214), with implications for its structural integrity and function under varying thermal conditions ( Fig. 3e-f ).


## All4144 and All4144(68–214) are dimeric proteins

To examine the dimerization of purified proteins All4144 and All4144(68–214), were incubated without a cross-linking reagent. Both proteins were identified as monomers, with molecular weights of approximately 24 kDa and 16 kDa, respectively. Following the addition of glutaraldehyde, both All4144 and All4144(68–214) formed homodimers, resulting in molecular weights of ∼50 kDa and ∼32 kDa, respectively ( Fig. 4a ). These results indicate that the deletion of the HTH domain in All4144(68–214) does not disrupt the dimerization capability of All4144. The consistent formation of stable homodimers in both proteins underscores the importance of dimeric structures in elucidating their functional characteristics.


## All4144 and All4144(68–214) form intermediate structure between ATP-DnaK and ADP-DnaK

The fluorescence emitted by tryptophan residues within DnaK was utilized to assess the impact of All4144 and All4144(68–214) on the structural arrangement of DnaK, both in the presence and absence of ADP/ATP. Our study revealed that ATP caused a reduction in DnaK fluorescence, whereas ADP alone did not produce the same effect. Moreover, the addition of both All4144 and All4144(68–214) to the DnaK.ADP mixture led to a decrease in the intrinsic fluorescence of DnaK. Consequently, based on the intrinsic fluorescence spectra, both All4144 and All4144(68–214) induced an intermediate structural state between DnaK bound to ATP and DnaK bound to ADP. However, All4144 resulted in a greater quenching of DnaK fluorescence spectra compared to its All4144(68–214), indicating its higher affinity for DnaK. These findings extend our comprehension of the molecular interactions and conformational alterations that occur upon the binding of All4144 and its deletion mutant to DnaK ( Fig. 4b ).


## All4144 and All4144(68–214) function as true co-chaperons

In this study, we investigate the role of All4144 and All4144(68–214) in enhancing the refolding efficiency of denatured malate dehydrogenase (MDH) mediated by DnaK. Our findings reveal the physiological significance of All4144 in modulating DnaK’s chaperone function, particularly concerning protein refolding. In the absence of chaperones, less than 25% of MDH was reactivated, which served as a control. The addition of DnaK alone increased this to only 29%. However, the presence of both All4144(68–214) and All4144 markedly enhanced refolding efficiency, achieving 53.79% and 56.53%, respectively ( Fig. 4c ). These results indicate that the deletion mutant still significantly enhances the refolding of MDH mediated by DnaK. Notably, the deletion of the N-terminal region does not impair MDH’s refolding activity, allowing it to function effectively as a genuine co-chaperone.


## All4144 and All4144(68–214) stimulate the ATPase activity of DnaK

We assessed the rates of DnaK-catalyzed ATP hydrolysis in the presence or absence of DnaJ, All4144, and All4144(68–214). DnaK exhibited a low hydrolysis rate of 0.009 nMol/µg protein/min ATP hydrolyzed ( Fig. 4d ). The addition of DnaJ enhanced the rate roughly by 8-fold. Interestingly, when DnaJ was combined with All4144 or All4144(68–214), the rates of ATP hydrolysis by DnaK increased by 11-fold and 9-fold, respectively ( Fig. 4d ). Furthermore, the fact that the deletion mutant still stimulates the ATPase activity of DnaK indicates that the N-terminal HTH domain does not completely affect its function, leading it to work as a nucleotide exchange factor.


## All4144 is a DNA binding protein

The DNA-binding capabilities of All4144 and its deletion mutant All4144(68–214), were examined using an electrophoretic mobility shift assay (EMSA). The results revealed that full-length All4144 formed nucleoprotein complexes, as indicated by a retardation in DNA mobility in the gel. Notably, full-length All4144 exhibited nonspecific binding with non-specific dsDNA significantly. In the presence of ATP and ADP, DNA demonstrated substantial stimulation compared to the protein alone ( Fig. 5a-c ). The affinity of All4144 for dsDNA was found to be Kd = 14.17 ± 0.47 nM. Additionally, the binding of All4144 to dsDNA increased nearly 12.6-fold in the presence of ATP (Kd = 1.12 ± 0.05 nM) and 31-fold in the presence of ADP (Kd = 0.45 ± 0.21 nM) ( Fig. 5e ). These findings suggest that All4144 non-specifically binds with dsDNA. Additionally, All4144 did not bind to ssDNA, even at higher concentrations of the protein used ( Fig. 5f-h ), confirming a preference for dsDNA over ssDNA in both the presence and absence of ADP/ATP. In contrast, the deletion mutant All4144(68–214) exhibited a complete loss of binding ability to both dsDNA and ssDNA ( Fig. 5d ). This was evident from the inability of All4144(68–214) to form nucleoprotein complexes with dsDNA, even at high protein concentrations up to 500 nM ( Fig. 5d ). These results demonstrate that the helix-turn-helix (HTH) domain at the N-terminus of All4144 is essential for binding to dsDNA. The removal of the HTH domain leads to the complete loss of the DNA-binding ability of the protein, emphasizing the critical role of the HTH domain in mediating the interaction between All4144 and dsDNA.


## All4144 has Unique Sequence Feature

Our study involved a comprehensive examination of sequence alignment, focusing on GrpE family proteins sourced from various organisms, including E. coli , Arabidopsis , human, rat, and several cyanobacterial strains. Our study encompassed a diverse range of cyanobacterial strains, such as Roholtiella sp., Atlanticothrix silvestris , Nostoc punctiform , Trichormus variabilis , Fischerella thermalis , Calothrix sp., and Scytonema sp. Additionally, we compared All4144 with its paralogs All4473 and Alr2445 from Anabaena sp., unveiling sequence identities of 14% and 18%, respectively. The proteins selected for multiple sequence alignment are detailed in Table 1 , facilitating a comprehensive analysis of sequence conservation and divergence. Through a detailed examination of the alignment, we observed conserved features predominantly in the C-terminal region across all explored species, signified by a dark red star (box 2) in ( Fig. 6a ). Conversely, numerous notable sequence gaps were identified in the N-terminal region, highlighted by black stars (box 1) in ( Fig. 6a ). Our multiple sequence alignment (MSA) analysis highlights distinctive sequence features of All4144 compared to its paralogs (All4473 and Alr2445), providing valuable insights into the functional characteristics and evolutionary divergence within the GrpE family.


## Protein modeling and interaction with DNA

To elucidate the molecular characteristics of All4144, three-dimensional (3D) structure predictions of the full-length protein All4144 and its deletion mutant All4144(68–214) have been obtained from All4144 AlphaFold entry Q8YPP8. The structural integrity of the models was confirmed, and their quality was evaluated using RMSD (root-mean-square deviation), RAMPAGE and TM score. Subsequently, the HDOCK web server’s intuitive interface was employed to explore the interactions between the protein and DNA. The three-dimensional model of All4144 revealed that the N-terminal region of the protein is predicted to be involved in interactions with DNA ( Fig. 6b ). Notably, the deletion of the helix-turn-helix (HTH) domain from All4144 resulted in the loss of its ability to interact with DNA ( Fig. 6c ). This observation corroborates the results obtained from the electrophoretic mobility shift assay (EMSA), where the deletion of the N-terminal region completely abolished the protein’s DNA binding activity.

These findings collectively underscore the critical role of the N-terminal HTH domain in facilitating the interactions between All4144 and DNA. The integrated approach of structural modeling and experimental validation enhances our comprehension of the molecular mechanisms governing the DNA binding activity of All4144.


## 4. Discussion

The intricate regulation of chaperone systems across diverse organisms, encompassing the eukaryotic Hsc70/Bag1 and the prokaryotic DnaK/GrpE systems, has been extensively studied ( 38 , 39 , 40 ). The regulatory mechanisms within the DnaK chaperone system are complex, involving the interplay between ATP and ADP states, along with substrate release mediated by GrpE ( 41 ). GrpE plays a critical role in maintaining the nucleotide-binding domain (NBD) in the Hsp70/DnaK chaperone system, acting as an essential component for nucleotide exchange in DnaK ( 42 ).

Our previous findings ( 15 ) highlighted the ability of bacterial DnaJ-III to enhance ATP hydrolysis even in the absence of GrpE, prompting us to further investigate the influence of GrpE on the DnaK-DnaJ chaperone system and stress resilience. The current study focuses on All4144, an unconventional GrpE protein containing both HTH and GrpE domains, and its co-chaperone activity. We aim to understand how All4144 modulates protein folding and cellular stress responses. By exploring its influence on DnaK-DnaJ interactions, we seek novel insights into the regulatory mechanisms governing protein quality control and cellular homeostasis.

Our computational study revealed the presence of an N-terminal helix-turn-helix (HTH) domain in All4144, suggesting its potential role in DNA binding. This finding indicates that All4144 may possess additional functions beyond its conventional role as a co-chaperone for DnaK. Comparative sequence analysis highlighted significant conservation between All4144 and its mammalian counterparts. Additionally, previous findings ( 43 ) suggest that All4144, akin to Hap46, has dual functionalities: it binds DNA via its N terminus while acting as a nucleotide exchange factor for DnaK through its C terminus. This dual role implies that All4144 likely contributes to various metabolic processes in cyanobacteria. Moreover, the resemblance between All4144 and mammalian GrpE proteins indicates evolutionary convergence, hinting at similar functional roles across different organisms despite their evolutionary distance.

Transcript expression profiling revealed a significant increase in All4144 expression in response to heat stress, underscoring its role as a gene responsive to elevated temperatures. This suggests that All4144 is important for cellular responses to heat. Furthermore, cell survival and thermal assays demonstrated that All4144 significantly enhances heat stress tolerance.

GrpE’s function as a nucleotide exchange factor for DnaK is heat-inducible; it has been suggested that All4144 acts as a thermometer in response to elevated temperatures, as supported by previous findings ( 12 , 44 , 45 ).

Moreover, the dimerization properties of All4144, akin to other GrpE proteins further emphasize its role as a bona fide member of the GrpE family ( 46 , 47 ). The observed structural features, coupled with the thermal transition profiles observed, suggest that All4144 and deletion mutant function as a true GrpE protein by modulating the kinetics of DnaK’s ADP/ATP conversion in response to temperature fluctuations. Additionally, the functional assays provided valuable insights into the interaction between All4144 and All4144(68–214) with DnaK, emphasizing its significance in modulating DnaK’s activity. This increased affinity likely enhances DnaK’s efficiency in ATP to ADP exchange, a crucial step in its chaperone cycle, and facilitates the refolding of thermally labile proteins such as malate dehydrogenase (MDH). Specifically, the deletion mutant alone acts as a complete GrpE protein, analogous to those found in other organisms like E. coli GrpE ( 46 ). However, All4144 exhibits a higher affinity for DnaK compared to its deletion mutant counterpart, possibly due to an additional domain HTH or alterations in the conformational properties of the full-length All4144 protein. This was confirmed by tryptophan fluorescence studies, which also suggested that the All4144 and DnaK-ADP complex more effectively quenched DnaK compared to its deletion mutant. This underscores the significance of both All4144 and its deletion mutant in the cellular stress response and chaperone machinery, contributing to the understanding of GrpE-mediated protein folding and stress adaptation mechanisms ( 48 , 49 ).

It is noteworthy that despite the deletion of the N-terminal region, the interaction between All4144 and DnaK remained intact, and its nucleotide exchange factor activity was preserved. This observation is consistent with previous findings regarding other GrpE proteins, suggesting that the N-terminal region may not be essential for the GrpE-DnaK interaction or its nucleotide exchange factor activity ( 50 ).

Furthermore, the predictions regarding protein-DNA interactions, along with the results of electrophoretic mobility shift assays (EMSAs), strongly indicate the involvement of the N-terminal region of All4144 in DNA interaction. This observation suggests a potentially novel role for All4144 protein in mediating DNA interactions, particularly through their N-terminal domains. The preference of All4144 for binding to double-stranded (dsDNA) and not bind with ssDNA, especially higher in the presence of ADP, further underscores the possibility of GrpE acting as a nucleotide exchange factor in DNA interactions. This implies a multifaceted role for All4144 in cellular processes beyond conventional chaperone functions, expanding our understanding of the diverse functions of GrpE proteins in cellular physiology and stress response pathways. Further exploration of these interactions will provide valuable insights into the intricate molecular mechanisms underlying DNA-protein interactions mediated by GrpE proteins.


## Conclusion

All4144 emerges as a novel GrpE protein with distinct characteristics, deviating from its counterparts. The inclusion of the HTH domain enhances its functionality and augments thermal tolerance, shedding light on its multifaceted roles in modulating the DnaK chaperone cycle and interacting with DNA. Future investigations will elucidate the specific contributions of these domains to cyanobacterial physiology.


## CRediT authorship contribution statement

SS and LCR designed the experiments. SS conducted the experiment. SS and RR have written the manuscript. SS and LCR analyzed the data. LCR critically reviewed the paper.


## Conflict of interest

“No conflicts, informed consent, human or animal rights applicable.


## Acknowledgments

L.C. Rai thanks National Academy of Science, India for the NASI Senior Scientist Platinum Jubilee Fellowship and the Indian Council of Agricultural Research-National Bureau of Agriculturally Important Microorganisms (ICAR-NBAIM) for financial support. Sonam Sriwastaw is thankful to the Department of Science and Technology (DST) for the Senior Research Fellowship (SRF).