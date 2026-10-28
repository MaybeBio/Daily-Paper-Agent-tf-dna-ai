# Integrated In Silico Discovery of Thymoquinone Analogs Targeting the Keap1–Nrf2 Pathway for Amyotrophic Lateral Sclerosis Therapy


## Abstract
  Oxidative stress drives neuronal vulnerability in amyotrophic lateral sclerosis (ALS), making the Keap1–Nrf2 pathway a vital therapeutic target. While thymoquinone (TQ) modulates this axis, its efficacy is limited by low potency and poor drug‐likeness. We utilized an integrated in silico workflow—including validated QSAR modeling (R 2 = 0.68, Q 2 ext = 0.66), ADMET profiling, docking, 200 ns molecular dynamics, and MM–PBSA analysis—to identify improved TQ‐derived Keap1 inhibitors. Screening 64 analogs prioritized three leads (CHEMBL3416163, CHEMBL4636830, and CHEMBL221598) with favorable safety and blood–brain barrier permeability. Docking and dynamics confirmed these analogs form stable interactions with Kelch domain hotspots. MM–PBSA calculations revealed significantly enhanced binding free energies (−75.10 to −93.79 kJ mol−1) compared to parent TQ (−21.05 kJ mol−1), driven primarily by van der Waals and hydrophobic forces. This study identifies structurally tractable TQ analogs with improved predicted potency and establishes a robust computational framework for neuroprotective discovery. The prioritized leads are compelling candidates for in vitro and in vivo validation as redox‐modulating agents in ALS.


## Introduction
  Reactive species are inevitable by‐products of metabolic and environmental processes that continually challenge cellular macromolecules. They comprise both free radicals and nonradical intermediates capable of generating radicals under physiological conditions [1, 2]. Free radicals possess unpaired electrons, which make them highly unstable and prone to abstract electrons from nearby lipids, proteins, and nucleic acids, thereby disrupting cellular integrity and contributing to disease pathologies [2]. At low or regulated concentrations, these species play essential roles in signaling, immune defense, and redox homeostasis [3, 4]. However, when their production exceeds the capacity of antioxidant defenses, it damages vital biomolecules and ultimately drives oxidative stress [5]. Figure 1 illustrates the principal pathways of reactive oxygen and nitrogen species formation that contribute to cellular redox imbalance.

  Oxidative stress is implicated across chronic pathologies, including Alzheimer’s and Parkinson’s disease, cancer, cardiovascular disease, diabetes, and amyotrophic lateral sclerosis (ALS) [5, 6]. ALS is a progressive neurodegenerative disorder marked by motor neuron loss, resulting in muscle weakness, paralysis, and typically death from respiratory failure within 3–5 years of symptom onset [7, 8]. Although its etiology is multifactorial, convergent evidence places oxidative stress among the principal drivers of neuronal injury and disease progression [9]. The global burden is substantial and projected to rise with population aging [10, 11]; underrecognition in low‐ and middle‐income settings further underscores the need for effective, brain‐accessible therapies [12, 13].

  Approved ALS treatments offer only modest clinical benefit and do not substantially alter long‐term disease progression. Riluzole yields a small survival gain [9], tofersen benefits a genetically defined subgroup [14], and edaravone, while antioxidant‐oriented, shows limited impact on long‐term progression and carries tolerability concerns, including renal toxicity and hypersensitivity reactions [15, 16]. These limitations stem largely from the “antioxidant paradox,” where direct scavengers often fail to match the kinetic scale of reactive species production in the central nervous system. Collectively, this reinforces the rationale for strategies that restore redox homeostasis by re‐engaging endogenous cytoprotective pathways, offering a catalytic antioxidant response, rather than relying solely on direct radical scavenging [17, 18].

  The Keap1–Nrf2 pathway is a master regulator of cellular redox balance [19]. Under basal conditions, Keap1 targets Nrf2 for degradation; during stress, disrupting the Keap1–Nrf2 protein–protein interaction allows Nrf2 to accumulate, translocate to the nucleus, and activate antioxidant and detoxification genes via the antioxidant response element [20]. Importantly, oxidative stress and mitochondrial dysfunction are convergent pathogenic mechanisms across the major genetic forms of ALS, including those associated with SOD1, C9orf72, TARDBP, and FUS. Emerging evidence indicates that dysregulation of the Keap1–Nrf2 pathway contributes to this oxidative imbalance, whereas genetic or pharmacological activation of Nrf2 restores redox homeostasis, suppresses mitochondrial oxidative stress, and improves disease‐related phenotypes in experimental ALS models, particularly those associated with C9orf72 [21, 22]. Directly blocking Keap1 provides an upstream, structurally tractable entry point to strengthen intrinsic defenses before irreversible damage develops [17, 19]. Figure 2 outlines the pharmacological activation sequence of the Keap1–Nrf2 pathway.

  Natural products such as flavonoids, sulforaphane, and curcumin provide proof‐of‐concept for Nrf2 activation but commonly suffer from modest potency, off‐target electrophilicity, metabolic instability, and poor blood–brain barrier (BBB) penetration [19, 20, 23, 24]. Thymoquinone (TQ), the principal quinone of Nigella sativa, has attracted attention for its antioxidant and neuroprotective effects and can activate Nrf2 by interfering with Keap1 binding (Figure 3) [25, 26]. Importantly, its quinone scaffold offers a chemically tractable, nonelectrophilic framework amenable to rational modification [27]. However, TQ is constrained by poor solubility, rapid metabolism, and low oral bioavailability, necessitating the discovery of analogs that retain the pharmacophoric core while enhancing drug‐likeness and neural reach [28, 29, 30].

  To bridge these pharmacological gaps while leveraging the neuroprotective core of TQ, we developed a fully integrated in silico workflow designed to prioritize analogs with optimized Keap1 engagement and enhanced neural reach. By exploring the ChEMBL and DrugBank libraries, we ensured that the resulting candidates possess high translational value and structural tractability [31, 32]. This multistep strategy comprised: (i) scaffold‐aware similarity screening to expand chemical space [33, 34, 35]; (ii) quantitative structure–activity relationship (QSAR) modeling with rigorous internal and external validation [36, 37, 38]; (iii) orthogonal drug‐likeness and Absorption, Distribution, Metabolism, Excretion, and Toxicity (ADMET) triage focused on BBB penetration [39, 40, 41, 42, 43]; (iv) structure‐based docking into the Keap1 Kelch pocket [44, 45]; and (v) 200 ns molecular dynamics with MM–PBSA free‐energy analysis to decompose energetic drivers under dynamic conditions [46, 47].

  In summary, this study builds on the recognition that restoring redox balance through endogenous defense pathways offers greater therapeutic promise than direct radical scavenging alone. By focusing on TQ analogs as modulators of the Keap1–Nrf2 pathway, we provide a blueprint for accelerating the rational design of neuroprotective agents grounded in antioxidant biology.


## Materials and Methods

### Similarity‐Based Identification of Thymoquinone Analogs
  We utilized the SwissSimilarity web server [33] to perform a 2D scaffold‐based similarity search, using the SMILES representation of TQ as the query molecule. To maximize the translational value and biological relevance of our findings, we explored two distinct chemical spaces: the ChEMBL library [31] of bioactive compounds and the DrugBank library [32] of clinically approved drugs. The Scaffold similarity method was specifically selected to preserve the essential benzoquinone pharmacophore, the core responsible for redox modulation, while permitting rational peripheral diversification around the isopropyl substituent. This similarity search was conducted using the SwissSimilarity web server [33] (accessed October 26, 2025). Following the removal of duplicate entries, we generated a nonredundant dataset exported in SMILES format for subsequent QSAR modeling.


### Quantitative Structure–Activity Relationship (QSAR) Modeling
  A schematic overview of the QSAR workflow is provided in Figure 4. In summary, we conducted comprehensive QSAR modeling to predict Keap1 inhibition in strict accordance with the guidelines of the Organisation for Economic Co‐operation and Development (OECD) [48]. The modeling framework adhered to four foundational principles: (i) defining a clear biological endpoint; (ii) applying a transparent and reproducible learning algorithm; (iii) establishing a defined applicability domain (AD); and (iv) evaluating performance using robust measures of goodness‐of‐fit and external predictivity.


#### Data Collection and Preprocessing
  Bioactivity data for human Keap1 (ChEMBL target ID: CHEMBL2069156) were retrieved from the ChEMBL database (version 36) [49, 50]. The initial dataset comprised 1798 compounds across 21 assay endpoints. For modeling, we retained only compounds with experimentally determined half‐maximal inhibitory concentration (IC50) values in nanomolar units, yielding 382 entries. To ensure data integrity, we removed duplicates (identified by canonical SMILES), records with inequality qualifiers (“<” or “>”), and entries with missing IC50 values. The final curated dataset consisted of 268 unique compounds. To normalize activity values for consistent comparison, IC50 values were transformed to their negative logarithmic form (pIC50) using Equation (1)

  (1) pIC50=−log10(IC50×10−9)


#### Descriptor Calculation
  Prior to computation, all molecular structures were standardized by removing salts, assigning aromaticity, and normalizing tautomeric and nitro groups to ensure chemical consistency [51]. Using PaDEL‐Descriptor, we generated twelve classes of fingerprint‐based molecular descriptors (Table 1) to capture diverse topological, substructural, and electronic characteristics [59].


#### Data Preprocessing and Feature Selection
  Descriptor matrices were mean‐centered and scaled to unit variance. To minimize multicollinearity, we removed redundant descriptors with pairwise correlations greater than 0.95 or those with minimal variance (<0.01) [59].

  We employed a two‐stage hybrid feature selection protocol to identify an optimal subset of informative descriptors. In the first stage, a Random Forest model was used to rank descriptors by importance, retaining a reduced subset of the most informative features to preserve nonlinear relationships. In the second stage, recursive feature elimination with 10‐fold cross‐validation (RFECV), using a Random Forest base estimator, was applied to iteratively remove weakly informative variables. This procedure yielded final descriptor sets ranging from 29 to 50 features across the twelve fingerprints, which were subsequently used for consistent model training and prediction.


#### Model Development and Assessment
  The dataset was divided into 80% training and 20% external test subsets using stratified random sampling to ensure a balanced distribution of activity values [60]. We selected the Random Forest (RF) algorithm for its ability to capture complex nonlinear relationships and its resistance to overfitting in moderate‐sized datasets [61, 62, 63]. Model implementation used the scikit‐learn library [64] with systematically tuned hyperparameters.

  Predictive performance was examined through 10‐fold cross‐validation, external validation (n = 54), and Y‐randomization (100 iterations) to ensure the observed correlations were not due to chance. Statistically acceptable models required R2≥0.6, Q2≥0.5, and an R2−Q2 difference ≤0.2 [65, 66].


#### Applicability Domain
  The applicability domain (AD) defines the chemical space within which a QSAR model is expected to make reliable predictions, as compounds lying outside this region are more likely to yield uncertain outcomes. In this study, we assessed the AD using a Williams plot, which integrates leverage values and standardized residuals to identify structurally influential compounds and potential prediction outliers [67, 68].

  Leverage values (hi) were calculated according to Equation (2)

  (2) hi=xiT(XTX)−1xi where xi is the descriptor row vector of the ith compound, X is the descriptor matrix, and X T is its transpose. The warning leverage threshold (h∗) was determined using Equation (3)

  (3) h∗=3(p+1)n where p is the number of model descriptors and n is the number of training compounds.

  Compounds with leverage values exceeding h∗ were considered structurally influential, whereas those with standardized residuals beyond ±3 standard deviations were classified as outliers. The Williams plot thus provides a visual and statistical means of defining the model’s AD, ensuring that only structurally relevant and statistically reliable predictions are interpreted within the model’s chemical space [37, 68].


### Drug‐Likeness and ADMET Properties
  We evaluated drug‐likeness and ADMET (absorption, distribution, metabolism, excretion, and toxicity) properties to determine the pharmacokinetic suitability and safety of the QSAR‐predicted TQ analogs. Canonical SMILES for the candidates were submitted to an orthogonal suite of predictive servers, including SwissADME [41], pkCSM [42], and ProTox‐3.0 [43].

  To ensure oral suitability, we first applied Lipinski’s “Rule of Five” using the following thresholds: molecular weight (MW) ≤500 Da, hydrogen bond donors (HBD) ≤5, hydrogen bond acceptors (HBA) ≤10, and partition coefficient (Log P) ≤5 [39]. We further refined this selection using Veber’s criteria, requiring rotatable bonds (RB) ≤10 and a topological polar surface area (TPSA) ≤140 Å2  [40]. Compounds were prioritized if they demonstrated a bioavailability score (BAS) ≥0.55, indicating acceptable oral absorption [69], and a synthetic accessibility (SA) score <5, ensuring they remain structurally tractable for future development [70].

  Comprehensive ADME profiling focused on gastrointestinal absorption, P‐glycoprotein (P‐gp) substrate status, and blood–brain barrier (BBB) permeability—a prerequisite for ALS‐directed therapies. We also utilized pkCSM to predict cytochrome P450 interactions and total systemic clearance to assess potential metabolic liabilities. Safety was rigorously assessed across five primary toxicological endpoints: hepatotoxicity, neurotoxicity, nephrotoxicity, carcinogenicity, and mutagenicity. Following a conservative triage strategy, we excluded any compound predicted to be toxic in a single endpoint or classified within Predicted Toxicity Class (PTC) I–III (LD50 < 300 mg kg−1) [43].


### Molecular Docking
  We conducted structure‐based molecular docking to evaluate the binding modes and relative affinities of TQ and its prioritized analogs within the Keap1 Kelch domain. TQ and the lead candidates identified through QSAR and ADMET screening were retrieved from PubChem in SDF format [71]. To ensure optimal starting geometries, we performed energy minimization using the MMFF94 force field in Open Babel 3.1.1 [72]. Ligands were subsequently converted to PDBQT format, incorporating polar hydrogens and Gasteiger charges for compatibility with the docking algorithm [72].

  The high‐resolution crystal structure of the human Keap1 Kelch domain (PDB ID: 4XMB) was obtained from the Protein Data Bank (PDB) [73]. Receptor preparation was performed using AutoDockTools 1.5.6, which involved removing crystallographic water molecules, adding polar hydrogens, and assigning Kollman charges before exporting the receptor as a PDBQT file [74].

  Docking simulations were executed using AutoDock Vina version 1.2.0 [45, 75]. The search grid was centered at the centroid of the native ligand‐binding pocket (x=4.266Å,y=0.692Å,z=−23.196Å) with dimensions of 40Å×40Å×40Å to ensure comprehensive coverage of the interaction region. We employed an exhaustiveness of 8 to generate nine poses per ligand, retaining the conformation with the most negative predicted binding affinity for further analysis [75].

  To ensure the reliability of the docking protocol, we performed a self‐docking validation by redocking the cocrystallized ligand into the receptor site [76]. The predicted pose was superimposed onto the experimentally resolved conformation to verify the reproduction of the native binding mode [76]. All ligand–receptor interactions were visualized and analyzed using UCSF Chimera and BIOVIA Discovery Studio [77, 78].


### Molecular Dynamics Simulations
  The docked Keap1–ligand complexes served as the initial configurations for molecular dynamics (MD) simulations to evaluate their structural stability under simulated physiological conditions. Protein topologies were prepared in GROMACS 2024.3 [79] using the pdb2gmx module with the OPLS‐AA force field [80] and the TIP4P water model [81]. Ligand structures were extracted from the top‐ranked docking poses, hydrogenated, and assigned Gasteiger charges using UCSF ChimeraX [82]. We performed ligand parameterization via the LigParGen web server to generate OPLS‐AA‐compatible coordinates and topology files [83].

  The resulting protein–ligand systems were solvated in a dodecahedral TIP4P water box and neutralized with counterions. Energy minimization was conducted using the steepest‐descent algorithm until the maximum force reached 1000 kJ mol−1 nm−1 [84].

  System equilibration was performed in two restrained phases: an NVT phase at 300 K using the stochastic velocity rescaling (v‐rescale) thermostat [85], followed by an NPT phase at 1 bar using the v‐rescale thermostat and the Berendsen barostat [86]. The solvated systems were electrically neutralized by the addition of six Na+ counterions prior to energy minimization. Long‐range electrostatics were treated with the Particle‐mesh Ewald (PME) method [87], and all covalent bonds involving hydrogen atoms were constrained using the LINCS algorithm [88], allowing for a 2 fs timestep.

  Production simulations were executed for 200 ns under periodic boundary conditions using the leap‐frog integrator [89], with coordinates recorded at 10 ps intervals. To characterize the conformational stability and local flexibility of the complexes, we analyzed the trajectories for root‐mean‐square deviation (RMSD), root–mean‐square fluctuation (RMSF), radius of gyration (R g), and solvent‐accessible surface area (SASA).


### MM–PBSA Binding Free Energy Calculations
  MM–PBSA binding free energy calculations were performed using gmx_MMPBSA [90] interfaced with GROMACS 2024.3 [79], employing the Poisson–Boltzmann model for polar solvation energy estimation. Binding free energies were calculated according to Equation (4)

  (4) ΔGbind=Gcomplex−(Gprotein+Gligand) where G complex, G protein, and G ligand represent the free energies of the protein–ligand complex, isolated protein, and isolated ligand, respectively [91]. The free energy of each species was estimated according to

  (5) G=EMM+Gsolv−TΔS where E MM is the molecular mechanics energy, G solv is the solvation free energy, and TΔS is the entropic contribution [92]. In the present study, the entropic term was omitted to facilitate the comparative ranking of structurally related ligands, consistent with common MM–PBSA practice [46, 91].

  The equilibrated portion of each MD trajectory (180–200 ns) was selected based on RMSD stabilization. Snapshots were extracted every 200 ps after removing periodic boundary conditions, recentering the complexes, and stripping solvent molecules and ions prior to MM–PBSA calculations. Per‐residue energy decomposition was subsequently performed following the approach of Homeyer and Gohlke [91] to identify the residues contributing most significantly to ligand binding within the Keap1 Kelch domain.


## Results and Discussion

### Model Performance and Validation
  Twelve Random Forest‐based QSAR models were developed using distinct molecular fingerprints to identify the structural determinants required for Keap1 inhibition (Table 2). Among these, the AtomPairs2DCount model provided the optimal balance between internal robustness and external predictivity, yielding Rtrain2=0.68, QCV2=0.61, and QExt2=0.66 with a streamlined set of 32 descriptors [59]. These statistical metrics exceed the established reliability thresholds of R2≥0.6 and Q2≥0.5 for valid QSAR models [65]. Furthermore, the minimal difference between R 2 and Q 2 (Δ ≤ 0.1) confirms that the model is statistically sound and possesses a low risk of overfitting [66].

  The SubstructureCount model also demonstrated acceptable predictive power with an Rtrain2 of 0.61 and a QExt2 of 0.59, suggesting its potential utility for consensus‐based modeling frameworks. Assessment of the experimental versus predicted pIC50 values for the AtomPairs2DCount model showed that most compounds for both the internal and external sets remained within a ±1.0 error window of the ideal regression line (Figure 5a). This alignment illustrates the model’s capacity to generalize its predictive accuracy across diverse chemical scaffolds.

  To ensure the results were not artifacts of random association, Y‐randomization was performed across 100 iterations. The resulting scrambled models produced markedly lower R2 and Q2 values (<0.2), whereas the actual AtomPairs2DCount model maintained its superior performance, confirming the statistical significance of the observed structure–activity correlations (Figure 5b).


### Applicability Domain Analysis
  We evaluated the applicability domain (AD) of the AtomPairs2DCount model using a Williams plot to ensure that the structural space of the training data was representative of the target chemical space (Figure 6) [68]. A warning leverage threshold (h∗=0.579) and a standardized residual range of ±3 were established as the definitive cut‐off criteria for reliability [37].

  Analysis of the training set identified seven compounds (e.g., CHEMBL4436743, CHEMBL4747827) that exceeded the leverage threshold, while two (e.g., CHEMBL4794829) were identified as residual outliers; notably, no compounds were found to be simultaneously influential and outlying [68]. In the external set, five compounds were identified as structurally influential, but no residual outliers were detected.

  The majority of compounds in both the training and test sets resided within the defined chemical space, confirming that the structure–activity relationships are statistically robust and chemically meaningful. This rigorous AD definition ensures that subsequent predictions for TQ analogs remain within the model’s learning domain, thereby strengthening the reliability of the identified leads.


### QSAR‐Based Activity Prediction of TQ Analogs
  The validated QSAR model built using AtomPairs2DCount fingerprints was applied to predict the inhibitory activity (pIC50) of TQ (CHEMBL1672002) alongside 64 structurally related TQ analogs retrieved via SwissSimilarity [33, 34, 35]. Predicted activities were categorized as active (pIC50 ≥ 6), intermediate (5 ≤ pIC50 < 6), or inactive (pIC50 < 5) [93]. The screening identified 49 intermediate and 16 inactive compounds, with no candidates reaching the active threshold (Figure 7).

  Applicability domain analysis confirmed that 64 of the compounds resided within the model’s chemical space, while one fell outside, emphasizing the necessity of domain validation for reliable predictions [65, 68]. From this pool, 48 intermediate compounds were prioritized for further analysis. Although TQ was predicted to be inactive (pIC50 = 4.01), it remained within the AD and was retained as the reference scaffold for all subsequent comparisons.

  The predicted activities and key drug‐likeness descriptors for the top‐performing candidates are summarized in Table 3, while full results for the entire library are provided as a separate CSV file in the Supplementary Material. This methodology follows established integrative frameworks that combine QSAR potency prediction with pharmacokinetic profiling to identify Keap1–Nrf2 inhibitors [94].


### Drug‐Likeness and Oral Bioavailability Profiling
  Physicochemical screening of the 48 prioritized analogs using Lipinski’s and Veber’s criteria identified ten compounds, along with TQ, that met all thresholds for drug‐likeness (Table 3) [39, 40]. Their molecular parameters, including molecular weight (MW), partition coefficient (log P), hydrogen‐bond donors (HBD) and acceptors (HBA), and polar surface area (TPSA), fell within established ranges for favorable permeability and absorption [41]. Notably, the selected analogs exhibited higher predicted activity than TQ, suggesting that scaffold optimization enhances both potency and pharmacokinetic potential, which is consistent with previous reports that structural modification can improve the biological activity of the TQ core [27].

  Molecular weights for the shortlisted candidates ranged from 164.20 to 330.46 Da, well within the optimal window (≤500 Da) for passive membrane diffusion [39]. Calculated log P values (1.85–4.79) reflected a balanced hydrophilic–lipophilic profile conducive to both aqueous solubility and membrane permeability. Hydrogen‐bond donors (0–2) and acceptors (2–5) were significantly below the recommended limits of 5 and 10, respectively, which favors efficient desolvation and target binding. Furthermore, the number of rotatable bonds (1–10) and the TPSA values (34.14–74.60 Å2) satisfied Veber’s thresholds for high intestinal absorption and oral bioavailability [40].

  Most analogs achieved a bioavailability score (BAS) of 0.85, compared to 0.55 for TQ, indicating superior oral absorption potential [69]. Synthetic accessibility (SA) scores ranged from 2.83 to 4.04, suggesting that these compounds possess moderate synthetic complexity and are amenable to further chemical optimization [70]. Because all eleven compounds complied with Lipinski’s and Veber’s rules, they were advanced to toxicological evaluation to establish their safety profiles.


### Toxicological Evaluation
  Toxicity profiling of the eleven drug‐like compounds identified by Lipinski’s and Veber’s filters was performed across several endpoints, including hepatotoxicity (dili), neurotoxicity (neuro), nephrotoxicity (nephro), carcinogenicity (carcino), mutagenicity (mutagen), and predicted toxicity class (PTC) [43]. Three analogs (CHEMBL3416172, CHEMBL4096012, and CHEMBL3416171) exhibited predicted toxicity in at least one category—specifically nephrotoxicity—and were subsequently excluded from the pipeline [43].

  The remaining eight analogs, along with TQ, were predicted to be inactive across all evaluated endpoints and were classified within PTC classes 4–5, indicating low acute toxicity (LD50 > 300 mg kg−1) [43]. The complete toxicity profiles are presented in Table 4. This early‐stage safety filtering is a critical step in identifying and eliminating potentially reactive or organ‐specific toxicants before advancing to expensive structural simulations [95].


### ADME Profiling
  ADME evaluation of the eight nontoxic, drug‐like analogs revealed uniformly favorable pharmacokinetic characteristics (Table 5). All compounds exhibited high predicted gastrointestinal absorption and blood–brain barrier (BBB) permeability, with no P‐glycoprotein efflux liability. The consistent BBB penetration across the subset is particularly significant for ALS therapy, as it ensures that the candidates can reach the target Keap1–Nrf2 proteins within the central nervous system.

  Regarding metabolic stability, none of the analogs showed inhibitory activity toward the major cytochrome P450 isoforms CYP1A2 or CYP3A4, reducing the risk of clinically relevant drug–drug interactions. However, substrate status varied among the candidates. CHEMBL221598 and CHEMBL3416163 emerged as the most favorable leads because they combined CYP3A4 nonsubstrate behavior with suitable predicted pharmacokinetic characteristics, whereas the remaining analogs were predicted to be CYP3A4 substrates with varying metabolic turnover potentials. Despite these metabolic differences, candidate prioritization was based on an integrated assessment of absorption, BBB permeability, CYP interaction profile, predicted clearance, and subsequent target engagement, rather than on any single ADME parameter. Although SwissADME [41] and pkCSM [42] predicted TQ to be soluble, this reflects a structure‐based computational estimate rather than experimentally determined aqueous solubility. Previous experimental studies [28, 29, 30] have consistently demonstrated that TQ exhibits poor aqueous solubility, rapid metabolism, and limited oral bioavailability, all of which contribute to its suboptimal pharmacokinetic performance. Consequently, analogs such as CHEMBL3416163 were prioritized despite their moderate predicted solubility because they achieved a more favorable overall balance between pharmacokinetic properties and predicted target engagement. Although their predicted clearance exceeded that of TQ, this was not considered prohibitive, as they simultaneously exhibited favorable BBB permeability, lack of CYP3A4 substrate liability, and substantially stronger predicted binding to Keap1, collectively supporting their selection for further investigation. This integrated ADME–docking framework enabled the prioritization of candidates with favorable pharmacokinetic characteristics while maintaining strong potential for Keap1 target engagement.


### Molecular Docking

#### Docking Protocol Validation
  Prior to the docking experiments, the protocol was validated to ascertain its reliability and accuracy. The cocrystallized ligand was redocked into the Keap1 active site (PDB ID: 4XMB), and the resulting pose was superimposed onto the experimentally resolved conformation, yielding an RMSD of 0.46 Å (Figure 8). This value, being significantly below the generally accepted 2.0 Å threshold, confirms that the docking procedure robustly reproduces the native binding mode and is therefore suitable for subsequent evaluation of the TQ analogs.


#### Docking Affinity Analysis
  Docking simulations against the Keap1 Kelch domain revealed that all eight analyzed analogs exhibited significantly stronger binding affinities than the parent TQ scaffold (−6.1 kcal/mol), as summarized in Table 6. To ensure the selection of leads with the highest translational potential, we integrated these structure‐based results with the previously determined ADME profiles. CHEMBL4636830 was identified as the most potent binder with an affinity of −8.0 kcal/mol. Despite its predicted status as a CYP3A4 substrate, it was prioritized due to this superior binding strength.

  CHEMBL3416163 and CHEMBL221598, both −7.2 kcal/mol, were advanced as high‐priority leads because they combined favorable binding affinities with optimal CYP3A4 nonsubstrate behavior, reducing the risk of metabolic liability. In contrast, the remaining analogs, including CHEMBL3416180, DB08690, CHEMBL221137, and CHEMBL3416352, were deprioritized because their predicted CYP3A4 substrate status outweighed their docking performance. This integrated ADME–docking framework yielded three high‐quality TQ analogs, which, along with the TQ reference, were advanced to dynamic simulation and free‐energy analysis to verify the stability of their binding modes.


#### Binding Interaction Analysis
  The four prioritized ligands exhibited consistent and residue‐dense binding within the Keap1 Kelch pocket, as illustrated in the interaction panels (Figure 9). CHEMBL4636830, the most potent binder, formed hydrogen bonds with Gly367, Val418, and Val465, reinforced by extensive van der Waals contacts centered on Gly603, Val604, and Gly511.

  Analogs CHEMBL3416163 and CHEMBL221598 displayed highly consistent binding patterns, characterized by recurrent hydrogen bonds involving Val418, Gly367, and Val606, carbon–hydrogen stabilization at Gly417, and a broad van der Waals network spanning Gly364, Gly603, and Gly511. In contrast, TQ (CHEMBL1672002) showed a comparatively narrow interaction profile dominated by polar contacts with Ser602 and Arg380, accompanied by limited aromatic interactions such as a single π–π stacking contact with Tyr334. Collectively, the prioritized analogs exploited a broader and more coherent hotspot network, particularly involving Gly364, Val604, and Gly603, providing a structural rationale for their superior affinity compared to the parent scaffold.


### Molecular Dynamics Trajectory Analyses

#### RMSD Analysis
  RMSD was used to evaluate the structural stability of Keap1 in its apo form and in complex with TQ and its analogs. As shown in Figure 10a, all systems equilibrated rapidly and remained stable over the 200 ns production run, with RMSD values consistently well below the 0.30 nm threshold. Apo‐Keap1 exhibited the highest mean RMSD (0.186 ± 0.018 nm), whereas ligand binding consistently reduced backbone fluctuations, indicating that the candidates enhance the structural rigidity of the Kelch domain. TQ (CHEMBL1672002) produced the lowest mean RMSD (0.134 ± 0.011 nm), while CHEMBL3416163 showed the closest stability profile (0.152 ± 0.016 nm), identifying it as the analog most capable of reproducing the reference scaffold’s stabilizing effect. Although CHEMBL4636830 and CHEMBL221598 stabilized at slightly higher values (0.159–0.167 nm), they maintained structural integrity without evidence of global unfolding or ligand dissociation.

  The RMSD probability density distributions (Figure 10b) reinforce these stability trends. While apo‐Keap1 sampled a broader conformational ensemble, the ligand‐bound systems exhibited narrower, left‐shifted unimodal peaks, which are characteristic of restrained backbone motion and restricted conformational space. TQ displayed the most compact distribution (∼0.136 nm), and CHEMBL3416163 exhibited the tightest distribution among the analogs, further confirming its role as a robust stabilizer. These results highlight CHEMBL3416163 as the most promising TQ‐like stabilizer in the set.


#### RMSF Analysis
  RMSF was used to assess residue‐level flexibility across the Keap1 Kelch domain (residues 327–610) and to determine how TQ and its analogs influence local dynamics (Figure 11). Apo‐Keap1 showed the highest overall fluctuations (mean RMSF = 0.081 nm), with pronounced peaks in the intrinsically mobile loop segments around residues 333–340, 380–388, and 430–437. Ligand binding reduced these motions to varying extents, indicating a general stabilizing effect on the protein structure.

  TQ (CHEMBL1672002) exhibited the lowest mean RMSF (0.070 nm) and effectively suppressed mobility in key loops, including 381–388, 397–404, and 429–436. Among the analogs, CHEMBL221598 demonstrated a comparable stabilizing effect (mean RMSF = 0.074 nm), specifically dampening motion across residues 382–388, 397–402, and 478–483. This identifies CHEMBL221598 as the analog most consistent with the parent TQ in reducing local residue flexibility.

  In contrast, CHEMBL3416163 and CHEMBL4636830 displayed moderately higher flexibility (0.084 and 0.083 nm, respectively), with elevated peaks at residues 324, 384, and 433. While these peaks occur in regions known to be inherently dynamic and do not indicate global destabilization, they reflect a weaker local stabilization relative to TQ and CHEMBL221598. Overall, the RMSF profiles confirm CHEMBL221598 as the analog that best approximates TQ’s flexibility‐dampening behavior.


#### SASA Analysis
  SASA was analyzed to assess how ligand binding influences the compactness and solvent exposure of the Keap1 Kelch domain (Figure 12a). Apo‐Keap1 exhibited a mean SASA of 130.15 nm2, reflecting a higher degree of surface exposure compared to most ligand‐bound systems. TQ (CHEMBL1672002) produced the lowest mean SASA (127.75 ± 2.07 nm2), indicating that the reference scaffold promotes a more compact protein conformation with reduced solvent accessibility. Among the analogs, CHEMBL221598 closely approximated this effect with a mean SASA of 128.80 ± 2.05 nm2, identifying it as the most effective analog for reproducing TQ‐like structural compaction.

  In contrast, CHEMBL3416163 and CHEMBL4636830 displayed higher SASA values (131.47–131.69 nm2), which are consistent with modestly expanded surface regions and increased conformational breathing. These trends are further supported by the SASA probability distributions (Figure 12b), where TQ and CHEMBL221598 exhibited sharp, left‐shifted peaks indicative of highly compact states. Conversely, the distributions for CHEMBL3416163 and CHEMBL4636830 were broader and right‐shifted, reflecting increased solvent exposure and higher conformational variability. Collectively, the SASA results reinforce the selection of CHEMBL221598 as the analog that best mirrors the favorable compacting behavior of the parent TQ scaffold.


#### R
g Analysis
  The radius of gyration (R g) was evaluated to assess the global compactness of Keap1 in its apo state and upon ligand binding (Figure 13a). Apo‐Keap1 exhibited a mean R g of 1.827 nm, indicating a greater overall expansion compared with the ligand‐bound systems. TQ (CHEMBL1672002) yielded the lowest mean R g (1.808 ± 0.005 nm), confirming its ability to promote a more compact and tightly packed protein conformation. Among the candidates, CHEMBL221598 followed with the second‐lowest mean R g (1.817 ± 0.009 nm), demonstrating a similarly strong compacting effect.

  In contrast, CHEMBL3416163 and CHEMBL4636830 showed modestly elevated R g values (1.824–1.830 nm), consistent with slight structural expansion and increased breathing motions of the Kelch domain. These differences were corroborated by the R g probability density distributions (Figure 13b), where TQ displayed a narrow, left‐shifted peak characteristic of a highly compact structure, whereas the distributions for CHEMBL3416163 and CHEMBL4636830 were broader and right‐shifted. Overall, the R g findings complement the RMSD, RMSF, and SASA trends, identifying CHEMBL221598 as the analog that most closely approximates the compactness induced by the parent TQ scaffold.


### MM–PBSA Binding Free Energy Analysis

#### Total Binding Free Energies
  Molecular mechanics Poisson–Boltzmann surface area (MM–PBSA) calculations were employed to quantify the thermodynamic strength of Keap1–ligand interactions, providing a more rigorous validation of the docking‐predicted affinities and the stability profiles obtained from MD simulations. All ligand‐bound systems remained stable over the 200 ns trajectories, providing reliable ensembles for energy estimation. The reference ligand TQ (CHEMBL1672002) exhibited the weakest affinity with a total binding free energy of ΔGbind=−21.05kJ/mol, whereas the three prioritized analogs demonstrated markedly stronger binding: CHEMBL3416163 (−93.79 kJ/mol), CHEMBL4636830 (−88.68 kJ/mol), and CHEMBL221598 (−75.10 kJ/mol). This energy ranking mirrors the docking results, confirming that the superior binding strengths of these analogs persist under dynamic sampling conditions.

  Analysis of the individual energy components (Table 7) revealed that van der Waals interactions were the dominant stabilizing factors across all complexes, supported by moderate electrostatic contributions. Conversely, polar solvation energies opposed binding in every system, reflecting the significant desolvation penalty required to bury polar functional groups within the predominantly hydrophobic Kelch pocket [96]. The nonpolar solvation term provided modest stabilization, aligning with the structural compaction trends and the expected hydrophobic character of the Kelch‐domain interactions [97]. These energetic drivers are consistent with previous studies of Keap1 inhibitors, where van der Waals forces were identified as the primary determinants of affinity [47, 98].


#### Per‐Residue Binding Energy Contributions
  Residue‐level energy decomposition was performed to identify the specific amino acids responsible for stabilizing the complexes within the Keap1 Kelch domain (Figure 14). TQ exhibited only weak interactions, primarily with Pro549 and Phe546, consistent with its limited interaction network and poor binding free energy. In contrast, the prioritized analogs established a much broader and more persistent contact network. CHEMBL3416163 was stabilized most strongly by Arg380 and Asn414, CHEMBL4636830 by Ile559 and Val420, and CHEMBL221598 by Ala366 and Val418. These residues significantly overlap with the structural hotspots identified during docking, confirming that the stabilizing interactions observed in static poses are maintained under dynamic conditions.

  Many of the most significant contributors are located within flexible loop regions. The binding of these analogs effectively dampens local fluctuations in these loops, thereby enhancing the global conformational stability of the protein–ligand complex [98]. This stabilization mechanism, combining extensive hydrophobic anchoring with selective polar recognition, provides a coherent structural rationale for why the analogs achieve markedly superior ΔGbind values compared to TQ. These findings further support the selection of CHEMBL3416163 and CHEMBL4636830 as the most promising candidates for future lead optimization.

  The consistent agreement across QSAR prediction, ADMET profiling, molecular docking, molecular dynamics simulations, and MM–PBSA free‐energy calculations provides convergent computational evidence supporting the prioritization of these TQ analogs as promising Keap1 inhibitors. Nevertheless, these findings remain predictive in nature and should be interpreted within the scope of an in silico investigation. While the integrated computational workflow offers a robust framework for rational lead prioritization, it cannot by itself establish biological activity or therapeutic efficacy. Consequently, experimental studies, including in vitro validation of Keap1–Nrf2 modulation followed by pharmacokinetic and efficacy evaluation in appropriate ALS models, are required to confirm the translational potential of the prioritized analogs.


#### Biological Implications for ALS and Medicinal Relevance of the Prioritized Analogs
  The superior binding stability and favorable binding free energies exhibited by the prioritized analogs are consistent with an enhanced capacity to disrupt the Keap1–Nrf2 protein–protein interaction relative to the parent TQ scaffold. Given the central role of the Keap1–Nrf2 pathway in regulating cellular redox homeostasis, stable occupation of the Kelch binding pocket is expected to promote Nrf2 activation and the expression of cytoprotective genes, a mechanism that has been shown to alleviate oxidative stress, preserve mitochondrial function, and attenuate motor neuron degeneration in experimental ALS models [21, 22, 99].

  The identified leads also possess encouraging medicinal relevance. CHEMBL4636830 corresponds to cannabigeroquinone, a member of the cannabinoquinone family whose analogs have progressed into clinical development for inflammatory and neurodegenerative disorders [100]. CHEMBL221598 is structurally related to embelin, a bioactive benzoquinone with established antioxidant and anti‐inflammatory properties that has recently been investigated in experimental ALS research [101]. Meanwhile, CHEMBL3416163 represents a comparatively underexplored alkyl‐substituted 2,5‐dihydroxy‐1,4‐benzoquinone scaffold, a class recognized for its chemical tractability and diverse pharmacological activities [102, 103, 104]. Collectively, the established medicinal relevance of these scaffolds complements the computational findings presented here and further supports their prioritization as promising noncovalent Keap1 inhibitor scaffolds for future investigation.


## Conclusion
  This study identifies thymoquinone (TQ) analogs with substantially enhanced Keap1 affinity and drug‐like features through a rigorously integrated computational workflow. By combining a validated QSAR model (R2=0.68,Qext2=0.66) with ADMET triage, molecular docking, and 200 ns molecular dynamics simulations, three prioritized analogs (CHEMBL3416163, CHEMBL4636830, and CHEMBL221598) emerged as consistently superior to the parent TQ scaffold. These leads exhibited markedly stronger binding free energies, ranging from −75 to  −94 kJ/mol compared to −21.05 kJ/mol for TQ, characterized by broader hotspot engagement within the Kelch pocket and stable dynamic behavior supported by restrained backbone flexibility. Per‐residue energy decomposition confirmed that binding is primarily driven by van der Waals and hydrophobic interactions, providing a structural rationale for the superior potency of these analogs.

  Beyond identifying high‐quality candidates, this work establishes a coherent in silico framework for the rational discovery of Keap1 inhibitors relevant to ALS and other redox‐driven neurodegenerative conditions. The prioritized analogs combine improved binding affinity with predicted oral bioavailability and blood–brain barrier permeability, positioning them as credible starting points for experimental validation. Immediate future efforts should focus on confirming Keap1–Nrf2 modulation in vitro, followed by pharmacokinetic and efficacy assessments in ALS models and iterative structure–activity refinement. Overall, these findings demonstrate that rational modification of the TQ scaffold can yield tractable Keap1 inhibitors with significant translational potential for redox‐centered neuroprotection.


## Author Contributions
  Jabir C. Nalicho: conceptualization, data curation, formal analysis, investigation, methodology, validation, visualization, writing – original draft, writing – review & editing. Petro E. Mabeyo: supervision, validation, writing – review & editing. Andrew S. Paluch: resources, supervision, software, writing – review & editing. Lucas Paul: project administration, resources, supervision, validation, writing – review & editing.


## Conflicts of Interest
  The authors declare no conflicts of interest.


## Supporting information

## Data Availability Statement
  The data that support the findings of this study are openly available in Zenodo at https://doi.org/10.5281/zenodo.18483747.


## Acknowledgments
  The authors acknowledge the Ohio Supercomputer Center for providing the high‐performance computing resources used in this work, with all simulations performed on the Pitzer cluster [105].