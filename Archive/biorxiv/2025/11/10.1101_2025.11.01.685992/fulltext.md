## ABSTRACT

Vitronectin (Vn) is a multifunctional blood glycoprotein involved in cell adhesion and migration, blood coagulation, and inflammation. It is a component of the high-density lipoprotein (HDL) proteome, and often found associated with the calcified, lipid-rich, protein deposits that are a hallmark of age-related macular degeneration, Alzheimer’s disease, atherosclerosis and other aging-related diseases. Here we explored the molecular basis for lipid binding by Vn using isothermal titration calorimetry (ITC), nuclear magnetic resonance (NMR) and all-atom molecular dynamics (MD) simulations. The data reveal a hydrophobic groove on the surface of the hemopexin-like (HX) domain of Vn, that is capable of binding phosphatidylcholine (PC). Conformational landscape analyses of multiple, independent MD simulations identify key structural motifs and intermolecular contacts mediating the association of Vn with PC, and show that lipid binding is guided by interactions with positively charged and hydrophobic residues that organize the lipids in a tail-to-tail bilayer-like arrangement within the groove. Collectively, the data establish a comprehensive structural model for Vn association with HDL and provide mechanistic insight into its accumulation within lipid-rich deposits characteristic of age-related pathologies.


## INTRODUCTION

The high-density lipoprotein (HDL) complex encompasses a heterogeneous collection of lipid-protein particles assembled from more than 280 protein and 200 lipid species that endow it with a broad range of activities 1 . Structural studies have provided fundamental information for both spherical and discoidal particles formed by the major HDL scaffolding proteins, particularly ApoA1 2 , and structural data are emerging for lecithin-cholesterol acyltransferase (LCAT) bound to discoidal Apo-A1 HDL particles 3 , but little is known about the structural basis for the association of the many other protein components with HDL.

Here, we present a structural model for lipid-bound vitronectin (Vn), a multifunctional serum glycoprotein associated with the acute phase response activities of small, dense pre-β HDL particles 1a-c , 4 . Vn interacts with a broad range of ligands to regulate cell adhesion and migration, extracellular matrix deposition, immune response, angiogenesis, fibrinolysis, and more 5 . It has been reported to bind lipids and cholesterol 6 , and is found with the lipid-rich deposits that accumulate with diseases of aging, including atherosclerosis 7 , age-related macular degeneration 8 and Alzheimer’s disease 9 . Understanding its mechanism for lipid binding is important for gaining insights to these physiological and pathological processes.

Using nuclear magnetic resonance (NMR) and molecular dynamics (MD) simulations, we show that Vn uses an extensive surface-exposed groove in its hemopexin-like (HX) domain to bind phosphatidylcholine (PC) – one of the most abundant phospholipids of the HDL lipidome 1d , 4 . Lipid binding is guided by interactions with positively charged and hydrophobic residues that organize the bound lipids in a bilayer-like arrangement within the groove. The data expand the range of protein-lipid interactions observed within the structurally and functionally diverse collection of HDL particles. They suggest a model for the association of Vn with HDL and provide a clue to its association with the lipid-rich deposits that accumulate in age-related pathologies.


## RESULTS AND DISCUSSION


## Vn binds lipid

Vn circulates as a 75 kDa N-glycosylated polypeptide ( Fig. S1 ). Its C-terminal HX domain comprises ∼70% of the mature protein sequence harboring binding sites for various ligands, and we have shown that it adopts a four-bladed β propeller structure ( Fig. 1A , Fig. S2 ) with each blade formed by one of four HX homology sequences (HX1-HX4) 10 . The propeller channel occludes NaCl, and four Asp residues at the channel rim form a Ca 2+ binding site 11 . An elongated hydrophobic groove formed at the HX1-HX4 interface is an attractive candidate for lipid binding ( Fig. 1B, C ).

To estimate the lipid binding potential, we performed isothermal titration calorimetry (ITC) by titrating Vn-HX with 1,2-diheptanoyl-sn-glycero-3-phosphatidylcholine (diC7-PC), a soluble short-chain mimetic of native PC. The ITC data ( Fig. 1D ; Fig S3 ) reflect exothermic lipid binding, with the potential for up to ∼5 diC7-PC molecules to associate with a single protein and a dissociation constant (K d ) of ∼60 µM, although we note that the experimental binding parameters are complicated by micellar aggregation of short-chain diC7-PC, and therefore not likely to be a true reflection of the native state.


## The lipid binding site maps to an elongated surface groove

To identify the lipid binding site we performed NMR experiments in the presence of diC7-PC. Vn-HX adopts the same structure in solution as in crystals 11a and the NMR spectra obtained with or without diC7-PC are very similar indicating that the same overall protein conformation is also maintained in the lipid-bound state ( Fig. 1E ; Fig. S4 ). Nevertheless, addition of diC7-PC induces distinct NMR perturbations, including 1 H and 15 N chemical shift changes, appreciable line narrowing and the appearance of 37 previously undetectable 1 H/ 15 N signals representing nearly 20% of the total assignable backbone ( Fig. 2A ). This NMR line-narrowing effect of diC7-PC is consistent with an overall increase of conformational order, indicating that lipid binding stabilizes a specific protein conformation. The largest perturbations map to the HX1-HX4 hydrophobic groove ( Fig. 2A, B ). By contrast, the 1 H/ 15 N signals of four Gly (G177, G224, G276, G441) peripheral to the Ca 2+ binding site are not significantly perturbed from the characteristic values of the Ca 2+ bound protein 11 indicating that lipid-bound Vn-HX remains Ca 2+ bound, and the binding sites for lipid and Ca 2+ are distinct.


## Structural basis for lipid association

To gain deeper structural insights, we performed five independent 6 µs MD simulations, starting from the coordinates of Ca 2+ bound Vn-HX 11b and 20 molecules of diC7-PC dispersed in water ( Table S1 ). Consistent with the NMR observation that diC7-PC does not induce a major structural rearrangement of the β-propeller, the protein coordinates equilibrate within a few nanoseconds and the structure remains folded over the course of simulation ( Fig. S5 ).

All simulations resulted in both rapid association of individual lipid molecules with the protein, and micellar self aggregation of the unbound lipids ( Fig. 3A ; Fig. S6 ). Volumetric map analysis ( Fig. S7 ) reveals the formation of a spherical ∼40 Å diameter micellar structure, with an average aggregation number of 16 lipids, that can be visualized as an inner volume of lipid acyl chains enclosed by an outer shell of polar headgroups, as expected for diC7-PC in water. The analysis also identifies two types of lipid-protein interactions: specific binding of individual lipid molecules to the HX1-HX4 groove, and a more dynamic association of the micelle with Arg-rich surface sites near the ends of the groove and at the β1-β2 loop of HX3.

The pattern of protein-lipid atomic interactions observed by MD ( Fig. 2C, D ) mirrors that of the experimental chemical shift perturbations, identifying the HX1-HX4 groove as the primary lipid binding site. Arg residues (R176, R189, R353, R446 and R450) situated at each end of the groove make frequent contacts with lipid headgroup phosphates, while aromatic and hydrophobic residues within the groove contact the lipid acyl chains.

In most replicas, individual lipids bind the groove very rapidly, within the first 200 ns of simulation, as evidenced by a sharp reduction in the lipid-to-groove distances, after which the groove remains lipid-bound for the duration of MD ( Fig. 3A ). In all five replicas, initial lipid binding occurs at the HX4 end of the groove (designated site 1), guided by interactions of the lipid acyl chains with aromatic and aliphatic residues in the groove core, and polar interactions of the lipid phosphate group with three Arg (R353, R446, R463) that form a positively charged gate at the groove entrance ( Fig. 3A, C , pink ). This first lipid binding event is rapidly followed by a second at the HX1 end of the groove (designated site 2) guided by interactions of the lipid acyl chains with aromatic and aliphatic residues in the groove core, and polar interactions of the lipid phosphate group with R176 at the HX1 groove entrance ( Fig. 3A, D , blue ). The sequence of events suggests that binding at site 1 may prime site 2 for binding a second lipid molecule.

Lipid binding at these primary sites is long-lived on the 6 µs time scale of MD. The two lipids occupy the groove in a tail-to-tail bilayer-like conformation, with polar heads stabilized by phosphate-Arg contacts and acyl chains stabilized by an aromatic cage (F161, F164, Y181, F437, F439, Y444, W469) that lines the length of the groove. Additional lipid molecules are seen to associate with the groove-bound lipids in what appears to be a cooperative interaction highly reminiscent of lipid bilayer formation ( Fig. 3A, E , yellow ). The groove-bound lipids are appreciably more conformationally restrained than either the additional cooperatively bound lipids or the micellar lipids, as evidenced by the narrow distribution of lipid-protein inter-atomic distances that they maintain over the course of simulation.

To identify the dominant lipid-binding poses at the primary groove sites, we defined a minimal, non-redundant set of structural descriptors that encapsulate key conformational rearrangements of both lipid and protein upon initial recognition ( Fig. 4 ). These are measured as the minimum distances between lipid tail atoms and the hydrophobic cores of sites 1 and 2 (see experimental section). The time evolution of the minimum distance between the lipid tail and the groove core reflects a stable lipid binding interaction across all five replicas, and the most probable occupancy of the groove corresponds to two bound lipids, with an average occupancy of 1.85 ± 0.5 ( Fig. S8) .

The conformational population landscape, mapped as a function of these descriptors, revealed distinct population density peaks corresponding to different groove-bound lipid poses ( Fig. 4A-C ): A surface-bound pose with the lipid acyl chains resting above the groove’s aromatic cage ( Fig. 3D , 4H ), and a groove-occluded pose with one or both acyl chains inserted deep in the groove core, under the rings of the aromatic cage residues ( Fig. 3E , 4I ). The transition from groove-surface to groove-occluded poses at site 1 is mediated by W469, whereas Y181 plays a similar role at site 2. Each pose correlates strongly with contacts of the lipid phosphate to the Arg gates for either site 1 or 2 ( Fig. 4D-F ) .

For each of these poses, the time evolution of their population reveals their life time within the groove ( Fig. 4D-F ). The most probable states are those where one lipid binds site 1 and another site 2. For Site 1, occluded and surface bound poses form distinct peaks separated by a low-probability transition region, underscoring long µs scale residence times in each state, with rare transitions between them ( Fig. S8 ). These states are correctly distinguished as separate structural groups by density-based clustering. For site 2, the separation between surface and occluded binding modes (see heatmap) is less distinct than for site 1, with transitions occurring on the sub-μs scale ( Fig. S8 ).

Notably, the evolution of bound state populations across 2-µs time blocks of simulation, averaged over all replicas, shows that initial binding occurs predominantly in both a loosely bound and a surface mode ( Fig. 4A, D ), and gradually transitions to the occluded mode as the simulation progresses. In the final 2 µs, the occluded mode dominates ( Fig. 4C, F ), suggesting that it drives binding affinity, whereas the surface mode likely serves as a kinetic intermediate. Moreover, the probability of simultaneously binding two lipids, each at sites 1 and 2, rises from the starting average value of 60%, to 70% in the last 2 µs, in line with the bilayer-like lipid binding organization observed in the MD structural models.


## CONCLUSIONS

Recent studies indicate that the function of HDL transcends the traditional correlation of its cholesterol level with risk of atherosclerotic cardiovascular disease. While HDL is well known for its central role in removing excess cholesterol from cells and transporting it to the liver for excretion, it is also associated with other fundamental physiological processes, and HDL particles have diverse compositions, structures and sizes, tailored for specialized physiological functions 1e-g . Proteomic studies 1a-d have identified more than 280 HDL proteins that confer specialization, highlighting the need to understand the molecular basis for their association with HDL. Our work sheds light on the mechanism for HDL association by Vn.

Here we have shown that the HX domain of Vn binds lipid molecules through an elongated surface-exposed hydrophobic groove. Positively charged Arg gates at the ends of the groove, and an aromatic cage within the groove core, provide a template for lipid binding in a tail-to-tail arrangement reminiscent of a lipid bilayer. Two lipid molecules remain associated with the groove over extended periods on the µs timescale of the MD simulations. Each bound lipid also engages in interactions with neighboring lipid molecules, as supported by the non-negligible probability of higher-order lipid occupancies within the Vn groove.

HX domains are found in other protein families, most notably hemopexin (Hpx) and the matrix metalloproteases (Mmps). The latter have been reported to associate with membrane surfaces, including via their HX domains 12 , and the zymogen of Mmp2 was recently reported to associate with ApoA1 through its HX and catalytic domains 13 . In all these cases, the protein interactions are membrane-peripheral and individual lipid binding has not been reported. Hydrophobic residues at the HX1-HX4 interface are conserved across the sequence of Vn, Hpx and Mmps but neither the Arg gates nor the aromatic cage are highly conserved, suggesting that the HX1-HX4 groove of Vn may be unique in its ability to bind lipid.

As our studies were performed with short-chain diC7-PC the question arises how might Vn bind longer-chain native lipids and associate with HDL. The combined NMR and MD data suggest possible models for HDL particle association. Vn is found in the fraction of small, largely discoidal pre-β HDL particles 4 . These nanometer sized patches of lipid bilayer are stabilized by two antiparallel copies of the major structural protein ApoA1 which form a protective belt around the hydrophobic edges of the particle 2 . The ten amphipathic helices of ApoA1 encircle the bilayer and maintain the particle in solution, but recent work has shown that ApoA1 is dynamic, especially when bound to small discoidal HDL particles, and the C-terminus of one or both ApoA1 molecules can loop back on itself exposing the lipid bilayer edge of the disc 14 . Vn may be expected to bind the exposed edge of such a partially de-scaffolded particle.

Our data show that the groove can accommodate two short-chain lipids ( Fig. 5A ) , but two long-chain lipids could also bind, potentially in an intercalated tail bilayer arrangement that is compatible with the edge of discoidal particles ( Fig. 5B, C ). The Arg gates of the groove set the phosphate P-P atomic distance of bound diC7-PC in the range of 25 Å, approximately 10 Å shorter than the thickness of a physiological lipid bilayer and discoidal lipoparticle. The Vn-disc interaction may thus be predicted to thin the Vn-bound edge of an HDL disc relative to the rest of the bilayered disc structure, and induce some degree of edge remodeling ( Fig. 5C ) .

Alternatively, we cannot exclude the possibility that Vn binds only one long-chain lipid molecule biasing its association with one leaflet of an HDL discoidal particle, or even that it circulates as a lipid bound protein able to transport just one, two or a few more lipid molecules free from larger discoidal lipid assemblies ( Fig. 5B ) . Chemical composition analysis of HDL-associated Vn and structure determination will be needed to answer this question.

Ultimately, lipid binding, including the proposed affinity for cholesterol, and the surface accessibility of the groove will need to be validated in the context of full-length Vn. The AlphaFold structural model of full-length Vn 15 predicts that the groove is accessible for lipid binding, unobstructed by other protein segments or N-glycosylation at N169 and N242 ( Fig. S10 ). Whether additional regions of the protein contribute to lipid binding will have to be determined experimentally. Moreover, the Vn-HX groove is stabilized by a C156-C472 intramolecular disulfide bond, and disulfide bond reduction could alter the groove’s lipid affinity and specificity. Vn is a substrate of protein disulfide isomerase, and disulfide bond reshuffling affects its interactions with integrin receptors 16 , thus, redox-dependent conformational changes in Vn may also govern HDL association.

Finally, the affinity of Vn for both lipids and Ca 2+ is relevant in the context of pathologies characterized by the accumulation of calcified protein-lipid deposits. For example, the deposition of Vn-coated µm size spherules, with a lipid-rich core and a shell of hydroxyapatite, is a hallmark of age-related macular degeneration. Phospholipids also have inherent affinity for Ca 2+ ions 17 and can nucleate calcium-phosphate clusters to initiate mineralization 18 . Thus, by simultaneously recruiting both lipids and Ca 2+ , Vn may play a role in mediating calcium-phosphate mineralization, as proposed previously 11a . Overall, the present data provide a framework for exploring the role of Vn in HDL function and models of HDL protein association.


## EXPERIMENTAL SECTION


## Protein preparation

Vn-HX was prepared from E. coli as described previously 10 . Uniformly 15 N/ 13 C labeled protein for NMR studies was obtained by growing bacteria on minimal M9 media containing ( 15 NH 4 ) 2 SO 4 and 13 C-glucose (Cambridge Isotopes). Samples for NMR contained 100-164 µM Vn-HX in 160 μL of buffer (20 mM MES, pH 6.5, 300 mM NaCl, 2 mM CaCl 2 ) supplemented with 5% D 2 O. Lipid containing samples were supplemented with 1,2-diheptanoyl-sn-glycero-3-phosphocholine (diC7-PC) to obtain a protein/lipid ratio of 1/50.


## NMR Spectroscopy

Solution NMR experiments were performed at 30°C on a Bruker Avance 600 MHz spectrometer, equipped with a 1 H/ 13 C/ 15 N triple-resonance cryoprobe. The NMR data were processed with TopSpin (Bruker) and analyzed using CCPN 2.4.2 19 . The HN, N, and CA chemical shifts were assigned using two-dimensional 1 H/ 15 N heteronuclear single quantum coherence (HSQC) experiments, and three-dimensional 1 H/ 15 N/ 13 C HNCA experiments 20 . The assigned chemical shifts are deposited in the BMRB database (IDs: 50241, 50261, 53399).


## Isothermal titration calorimetry (ITC)

Experiments were performed using the iTC200 instrument (Microcal) at 23 °C with 50-90 μM Vn-HX in the ITC cell and 3-6 mM diC7-PC in the injection syringe in 20 mM MES, pH 6.5, 300 mM NaCl. The data was processed and analyzed using ORIGIN software (Microcal) and fitted to a binding model corresponding to a single binding site for the extraction of dissociation constants (Kd). For control, titrants were added to the buffer.


## Molecular dynamics (MD) simulations

All-atom MD simulations were performed as described 11b , using the CHARMM36 force fields 21 with the TIP3P water model 22 . The temperature was set to 303.15K for simulations at 30°C, and the pressure was maintained at 1 bar.

The systems for MD ( Table S1 ), each containing one protein and twenty diC7-PC molecules, were prepared and equilibrated using the CHARMM-GUI Membrane Builder 23 . The initial models were generated from the crystal structure of Ca 2+ bound Vn-HX (PDB code 7rj9, molecule A) 10 , after removing all ligands and water molecules, and modeling residues with missing electron density using GalaxyFill 24 .

Five independent MD production simulations were conducted with OpenMM 25 using a time step interval of 4 fs with mass repartitioning. Trajectories were generated every 1 ns for 6 µs, and the last 5.8 µs were used for statistical analysis with home-made Python scripts in MDAnalysis 26 , PyLipid 27 and JupyterNotebook.


## Conformational landscape analysis

To identify the most probable lipid binding poses within the Vn groove, we evaluated a set of structural descriptors capturing key electrostatic and hydrophobic protein–lipid contacts. The ability of these descriptors to distinguish distinct binding poses was assessed using the Density-Based Spatial Clustering of Applications with Noise (DBSCAN) algorithm 28 , as implemented in the Scikit-Learn package 29 , across a range of neighborhood distance (ε) and minimum sample (min) parameters. Irrelevant or redundant descriptors were systematically filtered out, yielding two key non-redundant descriptors for lipid binding at sites 1 and 2, respectively. For site 1, this descriptor corresponds to the minimum distance between lipid tail carbon atoms and the center of mass of the F164 CZ and M350 CE atoms; For site 2, it corresponds to the minimum distance between lipid tail carbon atoms and the center of mass of the F164 and F161 CZ atoms. These two descriptors were then used to map the conformational landscape sampled by the MD simulations, clearly delineating the major binding states.


## ASSOCIATED CONTENT

This article contains supplementary information (Table S1; Figures S1-S8).


## AUTHOR INFORMATION

Notes: The authors declare no competing financial interests.


## AUTHOR CONTRIBUTIONS

KS, FM, FMM: writing, reviewing and editing

KS: protein preparation, NMR experiments

KS, AAB: ITC experiments

KS, WB, YT, GT, FM, FMM: MD simulations and analysis


## ACKNOWLEDGMENTS

We thank Marassi lab members for useful discussion. This research was supported by grants from the National Institutes of Health (P01 AG081167, R35 GM118186, P30 CA030199), the Canadian Institutes of Health Research (201711MFE-395794-210656), and the Fishman Fund Postdoctoral Fellowship. Computing resources were provided and supported by the Research Computing Center at MCW.


## Funder Information Declared


## ABBREVIATIONS