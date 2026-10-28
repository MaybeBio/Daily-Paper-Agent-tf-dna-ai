## ABSTRACT

Selecting suitable glucose-binding proteins (GBPs) is vital for biosensor development for medical diagnostics and quality control in the food industry. Biosensors offer advantages such as high specificity, selectivity, fast response time, continuous measurement, and cost-effectiveness. The current work utilized a combination of molecular docking, molecular dynamics (MD) simulations, and free energy calculations to develop a high-throughput bioinformatics pipeline to select GBP candidates from an extensive protein database (37,325 proteins). Using molecular docking, GBPs with good binding affinity to glucose (1,447 candidates) were virtually screened from the Protein Data Bank. MD simulations ascertained the binding dynamics of a few selected candidates. Further, steered MD (Brownian dynamics fluctuation-dissipation-theorem) was used to estimate binding free energies of the ligand-protein complex. Correlations between ligand-binding parameters obtained from longer MD simulations and binding parameters interpreted from significantly faster docking simulations were investigated. The correlation plots suggested that a combination of threshold values of the following three docking parameters: docking binding energy, binding cavity depth, and the number of hydrogen bonds between the ligand and binding site residues can be used to predict candidate GBPs reliably. Thus, a high-throughput and accurate protein selection process based on relatively faster docking simulations was proposed to screen GBPs for glucose biosensing.


## 1. Introduction

Biosensors have revolutionized a wide range of fields, from medical diagnostics to environmental monitoring, by combining the specificity of biomolecular recognition with the sensitivity of modern sensing technologies[ 1 ]. These powerful devices enable real-time and accurate detection of analytes in complex biological or environmental samples. Proteins are versatile candidates for recognition elements in biosensors, offering unique binding capabilities and adaptability[ 2 – 5 ]. Glucose biosensing is crucial in medical diagnostics and blood glucose monitoring. In numerous applications, such as diabetes management, food industry quality control, and fermentation processes, the precise measurement of glucose is of paramount importance due to its role as an essential energy source[ 4 , 6 ]. Glucose biosensors employ specific enzymes for accurate glucose measurement. Continuous glucose monitoring systems provide real-time data wirelessly for monitoring or smartphones [ 7 – 9 ]. Non-invasive glucose biosensors offer less invasive monitoring through optical and electrochemical methods. These advancements enhance diabetes management, promising ongoing improvements in accuracy and convenience[ 10 – 15 ].

To achieve high selectivity and sensitivity in glucose sensing, selecting an appropriate recognition element becomes critical. In this context, GBPs are promising candidates owing to their innate ability to bind glucose molecules selectively. GBPs encompass a diverse group of proteins with distinct binding pockets or domains that exhibit an affinity for glucose. As recognition elements in biosensors, GBPs offer advantages of high binding affinity, specificity, and stability. Moreover, their potential for genetic and protein engineering allows for performance enhancement and customization to specific applications. The screening and selection of suitable GBPs for biosensor development constitute crucial steps in harnessing their potential. To this end, advanced screening techniques, including combinatorial libraries, phage display, and high-throughput screening methods[ 16 – 18 ], have facilitated the identification of novel GBPs with enhanced binding properties. These techniques enable the exploration of vast protein libraries and the identification of GBPs with desired attributes, such as high affinity, selectivity, and resistance to interfering substances.

Molecular docking enables the analysis of protein-substrate interactions, the assessment of substrate specificity, the evaluation of docking scores, and the optimization of enzyme structures. By predicting binding affinities and stability, molecular docking aids in identifying enzymes with strong substrate binding and high selectivity [ 19 – 22 ]. This computational approach significantly enhances the efficiency of enzyme selection, enabling the development of sensitive and specific biosensors for diverse applications. Additionally, MD simulation of docked complexes provides insights into the dynamic behavior of enzyme-substrate interactions, further elucidating the stability and conformational changes crucial for biosensor design and optimization. In the current work, a bioinformatics pipeline was used to screen glucose-specific GBPs from large datasets of proteins acquired from a protein database. Sequence-based analysis was done to filter out unique GBPs, and molecular docking and MD simulation were employed to screen specific GBPs. A unique set of GBPs with high binding affinity to the glucose molecule were identified.


## 2. Methodology

The overall methodology employed in this study is illustrated in Figure 1 . A combination of computational tools was utilized to screen for GBPs.


## 2.1 Virtual screening of glucose-binding proteins (GBPs)

The 3D structure of glucose (PubChem ID 5793) was retrieved from the PubChem database and subsequently prepared by AutoDock 4 for docking against filtered GBPs. In the study, glucose-binding proteins were downloaded from the PDB database [ 23 ] using the keyword “glucose” and then filtered out by using two filters (Glucose & Homology filter). Again, AutoDock 4 was employed for protein preparation for molecular docking. AutoDock Vina [ 24 ] was employed for protein-ligand docking. The Parallelized Open Babel & AutoDock Suite Pipeline (POAP) [ 25 ] facilitated the automation of docking for multiple proteins and ligands. Discovery Studio Visualizer was used to visualize protein-ligand interactions [ 26 ].


## 2.2 Filtering and elimination of redundant GBPs

Several filters were implemented to optimize computational time and cost to eliminate redundant proteins. Redundancy criteria encompassed proteins unrelated to glucose, mutations within the same proteins, and homologous proteins. The integration of these filters facilitated the refinement of our dataset, concentrating exclusively on the most pertinent proteins for our molecular docking experiments.

The filters applied were as follows:

Keyword Filter (Filter 1): Search terms such as “glucose” were used to identify relevant proteins in the databases.

Glucose Filter (Filter 2): The chemical formula “ C 6 H 12 O 6 ” was again employed to identify unique proteins.

Homology filter (Filter 3): Proteins with more than 30% amino acid sequence similarity, indicating homology, were identified through a BLAST search and subsequently removed from the dataset [ 27 , 28 ].


## 2.3 Molecular dynamics simulation studies of docked complexes

The simulation setup of docked complexes was prepared by the CHARMM-GUI solution builder [ 29 ]. Details of the simulation setup are given in Table S1. Equilibration and production were conducted under constant volume, pressure, and temperature (1 atm and 310 K) conditions using NAMD 2.14 with CHARMM36m force field[ 30 ] for the 100ns. Structural changes during the simulation were measured using root mean square deviation (RMSD), with large RMSD values indicating significant motion and low RMSD values indicating a stable system. Analysis and visualization were performed using VMD [ 31 ].


## 2.4 SMD-BD-FDT analysis of docked complexes

Steered molecular dynamics (SMD) simulations were conducted using the Brownian dynamics fluctuation-dissipation theorem (BD-FDT) method [ 32 ] to accurately determine the free-energy profiles for glucose unbinding from protein-ligand complexes. The most stable structures of protein-ligand complexes were selected from MD simulations. CHARMM36m was utilized as the preferred force field, with a damping coefficient maintained at 5/ps. The vector connecting the center of mass of the glucose molecule to the center of mass of the alpha carbon atoms (within the binding site residues) was chosen as the pulling direction. The pulling speed was set at 0.002 Å/ps, while the rotational and translational motion of the protein-ligand complexes were fixed during the simulation. The distance between the bound and unbound states was divided into equal segments of 1 Angstrom. Ten forward and reverse paths were sampled for each segment as follows: the system was equilibrated for 0.5 ns with glucose held at the segment’s starting point, then glucose was steered 1 Å away from the binding site to sample a forward path. Subsequently, the system was equilibrated for 0.5 ns with glucose held at the segment’s end point. After equilibration, glucose was steered 1 Å towards the binding site to sample a reverse path. This process was repeated ten times for each segment from the bound state to the dissociated state. The potential of mean force (PMF) was then calculated using these paths from equation (1) , Where the BD-FDT relates the equilibrium free energy to the no equilibrium work according to the equation, here, 𝑊 𝐴→𝐵 is the force-displacement integral along a forward path from State A to State B, 𝑊 𝐵→𝐴 is a similarly defined force-displacement integral along a reverse path from State B to State A.


## 3. Results and discussion


## 3.1 Filtering of glucose-binding proteins (GBPs)

A total of 37,325 hits were identified, indicating a potential association with glucose-binding proteins, using Filter 1. Filter 2, which employed the molecular formula of glucose (C 6 H 12 O 6 ), narrowed down the protein candidates to 7,919 entries. Subsequently, Filter 3 utilized the CD-HIT algorithm to cluster proteins exhibiting high sequence similarity. This process resulted in a refined set of 1,447 proteins, as detailed in Table S2. Follow the link ( https://aciitb23.github.io/GBPS.com/ ) for more information about GBPs.


## 3.2 Virtual screening of glucose-binding proteins (GBPs)

Virtual screening of the selected 1,450 GBPs showed significant variations in their binding affinity with glucose (Table S3). Follow the link ( https://aciitb23.github.io/GBPS.com/ ) for more information about GBPs. The GBPs were arranged in decreasing order of their docking scores, Δ𝐸 𝐴𝐷 , reflecting their potential binding affinity. Table 1 lists the docking scores for the top five GPB candidate compounds, along with their respective interacting residues and types of interacting bonds. Whereas Figure 2 shows the three-dimensional structures of these GBPs, Figure 3 shows respective glucose-protein interactions at predicted binding sites. The binding site interactions are shown in greater detail in Figure S1. Among the proteins, 5TA0 exhibited the highest docking score (−7.70 kcal/mol), suggesting a strong binding affinity. For comparison, the commonly used GBP, glucose oxidase (1GAL) was also included in the list. In addition, a GBP with a very low binding affinity (−4.9 kcal/mol), human glycolipid transfer protein (2EVL), was included as a negative control.


## 3.3 Simulation of docked complexes

The stability of the docked complexes (candidate protein + glucose) and associated structural changes were monitored with 100 ns long MD simulations ( Figure 4a ). RMSD values for all docked complexes were found to vary between 1 – 6 (Å). RMSD values for the 4D52 complex were the most stable among the seven GBPs ( Figures 4b, c ). In addition, 4V20 and 3BXD complexes also demonstrated higher stability compared to the rest of the complexes. The 2O7I complex exhibited relatively higher RMSD values compared to the other docked complexes. Hydrogen bond occupancy was calculated for all protein-ligand complexes, revealing varying degrees of hydrogen bond occupancy for each complex (Figure S2). These results suggested that RMSD values alone may not be the primary determinant of GBP complex stability.

However, not all complexes remained stable during the simulations. The distance of the glucose molecule from the binding sites (CA atom) of GBPs, 𝑑 𝐺 , was used as a measure of the integrity of the GBP-glucose complex. Plots of variation of 𝑑 𝐺 with time are shown in Figures 5a and b . A residence time, 𝜏 𝑏 , for a specific GBP was defined as the time after which the corresponding 𝑑 𝐺 value started diverging significantly from its initial value. Based on 𝜏 𝑏 values (estimated from the 𝑑 𝐺 versus time plots), the seven GBPs were characterized as candidates with either strong ( Figure 5a ) or weak ( Figure 5b ) binding affinities. Whereas 4D52 and 1GAL demonstrated strong binding affinities, 4V20, 2O7I, and 2EVL showed the lowest binding with glucose. Complexes of 3BXD and 5TA0 remained bound to glucose for approximately 35 ns and 70 ns, respectively. Since these complexes remained stable for much longer when compared to the weakly-binding GBPs, they were also classified as strongly-binding GBPs. The residence time, estimated from these calculations, was used as a parameter in the selection process because it describes the dynamics of ligand binding to the GBP. Glucose binding/unbinding times of a strongly-binding (5TA0) and a weakly-binding (2EVL) GBPs are shown in Figures 5c and d , respectively.


## 3.4 Potential of mean force from SMD-BD-FDT

Using the SMD-BD-FDT simulations, the potential of mean force (PMF) curves for the seven GBPs, were estimated as a function of the distance of the ligand from the binding site, 𝜉 ( Figure 6 ). The binding free energy of a ligand-protein complex was inferred from the PMF curve as the depth of the potential well. Most of the BD-FDT binding energy values, Δ𝐺 𝑏 , were different from the binding energies estimated from the AutoDock values ( Figure 7 ). For instance, BD-FDT predicted a binding energy of −16.7 kcal/mol for 5TAO, which was significantly higher than the value estimated by AutoDock at −7.7 kcal/mol. Interestingly, 2EVL, which was selected for its low binding score, displayed a low binding energy value of −2.6 kcal/mol in the BD-FDT simulations as well. Moreover, 2O7I demonstrated a binding free energy of −11.5 kcal/mol, higher than the docking prediction of −7.13 kcal/mol. However, the PMF curve showed a negative curvature, indicating weak binding of glucose with the protein. This inference is consistent with the extremely short 𝜏 𝑏 for 2O7I ( Figure 5c ) and in conflict with the prediction of a stable glucose-2O7I complex from AutoDock. It shows that AutoDock scores for binding energies may not capture all dynamical aspects of ligand binding to the GBP. Hence, AutoDock predictions need to be guided by more rigorous physics-based simulations to generate rules for protein selection. Representative paths corresponding to glucose unbinding for each GBP are shown in Figure S3.

The examination of individual cases further emphasized the diverse characteristics of the complexes. The analysis of the potential of 4V20 elucidated its limited binding capacity, supported by a shallow well and subsequent dissociation, confirmed by a low PMF value. Similarly, 2EVL showed weakened bonding, as evidenced by the shallow well and subsequent unbinding of glucose beyond a certain threshold. On the other hand, the unbinding pathways of 2O7I and 1GAL revealed distinct patterns, reflecting the complexities of their interactions. While 2O7I demonstrated a relatively abrupt dissociation, 1GAL displayed an intermediate state during the process, ultimately leading to complete detachment. Notably, 5TA0 exhibited unique unbinding patterns characterized by distinct potential wells and intermediate states, underscoring the intricate nature of their binding mechanisms. Figure 7 compares binding energy predictions from docking, Δ𝐸 𝐴𝐷 , with those from SMD simulations, Δ𝐺 𝑏 . Both Δ𝐸 𝐴𝐷 and Δ𝐺 𝑏 values were the highest for 5TA0. Other proteins with high Δ𝐸 𝐴𝐷 scores (3BXD, 4D52, and 1GAL) also demonstrated high Δ𝐺 𝑏 values. For 2EVL, a weakly-binding GBP, both Δ𝐸 𝐴𝐷 and Δ𝐺 𝑏 values were low. These observations indicated a relatively strong correlation between Δ𝐸 𝐴𝐷 and Δ𝐺 𝑏 values. They also set the stage for finding other correlations between energy-minimization-based AutoDock predictions and more detailed atomistic MD simulations. Such correlations can assist in developing a rational GBP selection framework based on relatively quicker, albeit approximate, docking simulations.


## 3.5 Correlating docking predictions with MD simulations

A comprehensive analysis was carried out to correlate results from docking with those from MD simulations. It should be noted that absolute values of the binding energies, |Δ𝐺 𝑏 | and |Δ𝐸 𝐴𝐷, | are represented in these plots. Key parameters derived from MD simulations, including glucose residence time (𝜏 𝑏 ), glucose binding free energy (|Δ𝐺 𝑏 |), and the hydrogen bond occupancy (𝑛 𝐻𝐵𝐷 ), were selected as the first set of parameters. The second set of parameters, derived from docking simulations, included the docking energy (|Δ𝐸 𝐴𝐷 |), cavity depth of the binding site from the GBP surface (𝑑 𝑐 ), and the number of hydrogen bonds between glucose and GBP residues (𝑛 𝐴𝐷 ). Correlations were sought between parameters in the first set with those in the second set. Figures 8a – c plot 𝜏 𝑏 as a function of the docking parameters from the second set. Similarly, Figures 8d – f plot |Δ𝐺 𝑏 | as a function of the second set docking parameters.

Whereas 𝜏 𝑏 did not show any correlation with either |Δ𝐸 𝐴𝐷 | or 𝑛 𝐴𝐷 ( Figures 8a,c ), it showed a strong linear correlation with 𝑑 𝑐 ( Figure 8b ). The correlation plot of 𝜏 𝑏 vs 𝑑 𝑐 showed that a large cavity depth resulted in a strongly-bound and stable glucose-GBP complexes. A comparison with MD results from Figures 5a and b indicated that weakly-bound GBPs (2EVL, 4V20, and 2O7I) had 𝑑 𝑐 < 10Å. Interestingly, both 4V20 and 2O7I had high |Δ𝐸 𝐴𝐷 | values, implying that a high docking score may not necessarily lead to stable glucose-GBP complexes.

The binding free energy, |Δ𝐺 𝑏 |, showed stronger correlations with the three docking parameters ( Figures 8d – f ). It increased almost linearly with increasing value of both |Δ𝐸 𝐴𝐷 | ( Figure 8d ), but there were a couple of anomalies. As stated above, 4V20 had a high |Δ𝐸 𝐴𝐷 | but did not form a stable complex ( Figure 5b ) because of which it had a low |Δ𝐺 𝑏 | value. Similarly, 2O7I also formed an unstable complex (though it had a high |Δ𝐸 𝐴𝐷 |, but a high |Δ𝐺 𝑏 | value was interpreted from its anomalous PMF curve in Figure 6e . Again, |Δ𝐺 𝑏 | showed a linear correlation with 𝑑 𝑐 ( Figure 8e ). In general, GBPs with deeper cavities resulted in higher |Δ𝐺 𝑏 | values. Thus, cavity depth emerged as a reliable indicator of glucose binding with a GBP. The correlation plots in Figures 8b,e suggested that stable glucose-GBP complexes emerged for 𝑑 𝑐 > 12Å. Plotting the variation of |Δ𝐺 𝑏 | with respect to 𝑛 𝐴𝐷 provided insight into the effect of the bonding environment at the ligand binding site on the stability of the glucose-GBP complex. A sigmoidal dependence of |Δ𝐺 𝑏 | with respect to 𝑛 𝐴𝐷 was inferred from Figure 8f . Whereas GBPs with 𝑛𝐴𝐷≤3 corresponded to low Δ𝐺𝑏 values (weakly binding), GBPs with 𝑛 𝐴𝐷 > 3 corresponded to stable complexes with Δ𝐺 𝑏 values close to 10 kcal/mol. Thus, |Δ𝐺 𝑏 | versus 𝑛 𝐴𝐷 plot indicated a threshold value of 𝑛 𝐴𝐷 = 3, above which stable complexes could be found.

To validate these correlations interpreted from Figure 8 , |Δ𝐺 𝑏 | was plotted with respect to two other parameters also obtained from MD data, namely, 𝑛 𝐻𝐵𝐷 and 𝜏 𝑏 ( Figure 9 ). The plot of |Δ𝐺 𝑏 | with respect to 𝑛 𝐻𝐵𝐷 showed a sigmoidal behavior similar to the plot in Figure 8f , indicating that a certain minimum number of hydrogen bonds (at the binding site) are required for stable glucose-GBP complexes. Similarly, low 𝜏 𝑏 values corresponded to low |Δ𝐺 𝑏 | values and, by extension, a weakly-bound glucose molecule ( Figure 9b ).

Thus, the correlation plots in Figure 8 helped in arriving at a set of docking parameters that would reliably predict GBPs that bound strongly to glucose. Using these parameters would make the protein selection process more efficient since these parameters would be obtained from relatively faster docking simulations. Based on the above discussion, a combination of threshold values of Δ𝐸𝐴𝐷, 𝑑𝑐, and 𝑛 𝐴𝐷 can be used to predict candidate GBPs reliably. Specifically, a GBP with docking parameters corresponding to |Δ𝐸 𝐴𝐷 | > 7.0, 𝑑 𝑐 > 12Å, and 𝑛 𝐴𝐷 > 3 should result in the formation of a stable glucose-protein complex.

Figure 10 is a flowchart that outlines a “GBP selection pipeline” that incorporates the above-mentioned selection rules (based only on docking data) and a few test MD simulations. It comprises the following steps,

Use Filters 1, 2, and 3 to select candidates from the database

Apply threshold values of |Δ𝐸 𝐴𝐷 | > 7.0 kcal/mol, 𝑑 𝑐 > 12Å and 𝑛 𝐴𝐷 > 3 to arrive at potentially strongly-binding GBPs

Computational validation of selection process: Conduct short (100 ns) MD simulations on a small sample of proteins (≈10 proteins) to test the stability of the glucose-protein complex (along the lines of Figure 5 )

Experimental validation: Use top candidates for further experimental binding studies


## 4. Conclusion

Biosensors are valuable tools for monitoring the quality of fruit juices due to their fast response time, portability, and cost-effectiveness. Enzymatic biosensors have proven successful due to their high specificity and low manufacturing cost. In the current work, unique glucose-binding proteins were identified using a high-throughput bioinformatics pipeline, which included sequence-based analysis, molecular docking, and MD simulations. A total of 37,325 GBP hits were identified from the PDB database, and subsequently, a total of 1,447 unique GBPs were found suitable. Molecular docking data provided approximate values for binding (docking) energies, binding cavity depths, and state of hydrogen bonding at the binding site ( Figures 3 and 8 ). Detailed binding dynamics of a smaller subset of seven GBPs were exhaustively investigated using MD simulations. MD simulations provided estimates of glucose binding times to corresponding GBPs ( Figure 5 ). BD-FDT SMD simulations were used to estimate the binding free energies of the ligand-protein complex ( Figure 6 ).

Several parameters belonging to two different sets, (a) ligand-binding (from MD simulations) and (b) binding parameters (from docking simulations), were compared to extract correlations between them ( Figures 7 and 8 ). The objective was to propose parameter values based only on faster docking simulations that could be used reliably to select GBPs. The correlation plots suggested that the following threshold values of three docking parameters: Δ𝐸𝐴𝐷>7.0 kcal/mol, 𝑑𝑐>12Å, and 𝑛 𝐴𝐷 > 3 can be used to predict candidate GBPs reliably. All selection criteria were based only on data generated from quick docking simulations. A high-throughput and accurate protein selection process based on quick docking simulations was proposed to screen GBPs for glucose biosensing ( Figure 10 ).

Top candidates from the screening process can be tested in laboratory experiments to study glucose binding. This would constitute a test for the validity of the proposed scheme. Experimental validation was not in the scope of the current work. However, 1GAL (a widely used GBP) met all three proposed selection criteria. The current scheme can also be extended to other ligand-binding proteins for different analytes present in food processing, including fruit juices.


## Disclosure statement

The authors declare no competing interests.


## Funding

There are no funding sources to declare.


## Author’s Contributions

A.C., P.D., and A.S.P. designed the research. A.C. developed a high throughput screening pipeline for screening GBP candidates. A.C. and A.M. prepared the initial manuscript draft.

A.M. performed SMD simulations, analyzed data, and created figures. P.D. and D.D. provided inputs on glucose sensing and analysis. A.C. and A.S.P. contributed to the writing and editing of the final manuscript.


## Data availability

Follow the link ( https://aciitb23.github.io/GBPS.com/ ) for more information about screened GBPs.


## Acknowledgments

The authors acknowledge support in the form of access to the Spacetime High-Performance Computing (HPC) resource at IIT Bombay.


## Footnotes

Manuscript title updated; author affiliations updated; Figure 1 revised; Figures caption updated Supplemental table and figures caption modified; conclusion updated.

https://aciitb23.github.io/GBPS.com/