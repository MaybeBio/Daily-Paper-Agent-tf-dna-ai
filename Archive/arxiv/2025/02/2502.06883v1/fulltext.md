## QuantumDNA: A Python Package for Analyzing Quantum Charge Dynamics in DNA and Exploring Its Biological Relevance Journal: arXiv

The study of DNA charge dynamics is a highly interdisciplinary field that bridges physics, chemistry, biology, and medicine, and plays a critical role in processes such as DNA damage detection, protein-DNA interactions, and DNA-based nanotechnology. However, despite significant advances in each of these areas, knowledge often remains inaccessible to researchers in other scientific communities, limiting the broader impact of advances across disciplines. To bridge this gap, we present QuantumDNA, an open-source Python package for simulating DNA charge transfer (CT) and excited states using quantum physical methods. QuantumDNA combines an efficient Linear Combination of Atomic Orbitals (LCAO) approach with tight-binding (TB) models, incorporating open quantum systems techniques to account for environmental effects. This approach allows rapid yet accurate analysis of large DNA ensembles, enabling statistical studies of genetic and epigenetic phenomena. To ensure accessibility, the package features a graphical user interface (GUI), making it suitable for researchers across disciplines.


## 1 Introduction

DNA, the molecular blueprint of life, is not only known to encode most of the genetic information necessary to sustain life, but its complex molecular structure has long been studied as a platform for many physical phenomena. Among these, as early as sixty years ago, hypotheses were put forward for the possible relevance of quantum phenomena on the DNA molecule, both for engineering purposes and for a better understanding of the functioning of DNA in living cells [ 1 , 2 ] . For example, Löwdin’s pioneering work demonstrated that classically forbidden proton tunneling through energy barriers could lead to DNA point mutations, shedding light on a novel mechanism of genetics [ 3 ] and advancing our understanding of fundamental biological processes.

One area of research that has generated particular interest in the community is long-range CT [ 4 , 5 , 6 ] and long-lived excited states [ 7 , 8 , 9 ] on the DNA molecule. Understanding the charge dynamics in DNA is crucial for several scientific disciplines. From a physical and chemical perspective, these processes elucidate electron dynamics in complex macromolecular systems and inform the design of novel nature-inspired materials in molecular electronics [ 10 , 11 ] . Biologically, they are integral to genetic information processing and cellular functions, affecting DNA replication, repair, and transcription. In fact, characterization of the conducting properties of the DNA double helix has recently been explored as a novel approach to potentially uncover mechanisms of epigenetic regulation in living cells [ 12 ] . Medically, insights into these mechanisms may improve the diagnosis, treatment, and prevention of disease, particularly for conditions such as cancer [ 13 , 14 , 15 ] .

To provide a computational framework for studying these processes, we present QuantumDNA, an open-source Python package specifically designed to simulate DNA charge dynamics using quantum physics methods. QuantumDNA uses a zoom-in/zoom-out approach to seamlessly integrate atomistic precision with system-level modeling. At the atomic level, charge interaction parameters are calculated using a built-in LCAO method amd serve as the basis for a coarser-grained TB model. This dual-scale approach ensures computational efficiency while maintaining the accuracy required for statistical analysis of large ensembles of DNA sequences, making QuantumDNA particularly suitable for statistical studies of genetic and epigenetic phenomena. Recently, the package was used to estimate exciton lifetimes and average dipole moments for all 16,384 possible seven-base pair DNA sequences [ 16 ] , demonstrating its capability for high-throughput analysis of DNA electronic properties.

QuantumDNA integrates with publicly available biological databases such as the RCSB Protein Data Bank (PDB), allowing researchers to analyze a wide range of realistic DNA structures. Using molecular editing and visualization tools such as Biovia Discovery Studio and PyMol, users can introduce targeted mutations or modifications into DNA sequences and study their effects on CT and excited state properties. This functionality allows rapid screening of large DNA ensembles, facilitating the identification of sequences with significant electronic properties. These selected sequences can then be subjected to more detailed ab initio calculations or used to guide experimental research. By combining physical modeling, structural biology, and computational chemistry, the package can serve as an interdisciplinary tool for studying DNA charge dynamics at multiple scales.

The manuscript is organized as follows. Section 2 provides a brief overview of the field of DNA physics and sets the stage for the following discussions. In Section 3 , we introduce the QuantumDNA package and outline its architecture. Section 4 describes the theoretical framework and the computational methods used for the simulations. In Section 5 , we demonstrate the capabilities of QuantumDNA by replicating the results of published research and presenting a biological application. Finally, Section 6 presents concluding remarks and discusses the limitations and planned future improvements of the package.


## 2 Charge and Energy Diffusion along DNA


## 2.1 Charge Transfer

Following the seminal characterization of the double-helical structure of DNA by Watson, Crick [ 19 ] and Franklin, early hypotheses suggested that DNA might exhibit electrical conductivity, inspired by its structural similarity to the stacking patterns observed in one-dimensional molecular crystals [ 1 , 20 ] . Three decades ago, experiments confirmed that photoinduced CT can occur over long molecular distances between donor and acceptor molecules intercalated in DNA [ 21 ] . It is known that CT happens mainly through the pi-stacked DNA nucleobases and is very sensitive to changes in the stacking. Therefore, it has been proposed as a signaling and sensing mechanism that may allow DNA-binding proteins to detect and repair mutations and defects in the DNA sequence, as suggested by Barton et al. [ 22 , 23 ] .

Over short distances of 3-4 base pairs quantum mechanical tunneling (superexchange) is assumed to dominate CT [ 24 ] .

DNA nucleobases can undergo redox reactions resulting in the insertion of a hole (oxidation) or an electron (reduction) by external stimuli, represented by the green object in Fig. 1 (a). The specific mechanisms driving these events vary with experimental conditions [ 6 , 23 ] , but the focus here is on the resulting charge state of the nucleobase, which acts as the initial charge donor. Once initiated, the charge can propagate along the DNA chain and reach a distant acceptor.


## 2.2 Excited States

Photoexcited energy transfer is a fundamental process in nature and the basis for life on Earth. In DNA, the absorption of ultraviolet radiation (UVB) from sources such as sunlight or lasers has been extensively studied both experimentally and theoretically [ 7 , 8 , 9 ] . The remarkable photochemical stability of DNA is due to its ability to dissipate photoexcitation energy as thermal energy within picoseconds through non-radiative processes. This rapid energy conversion helps to prevent UV-induced mutations.

Nevertheless, transient absorption and pump-probe experiments by Kohler et al. [ 18 , 25 ] indicate that the excited state lifetime is increased in stacked DNA bases compared to DNA monomers. This could explain how photomutagenic damage to DNA occurs, for example, cyclobutane pyrimidine dimers (CPDs) linking neighboring T-bases, which are a major contributor to skin cancer.

A physical model of DNA photoexcitation is shown in Fig. 1 (b). Energy absorption promotes an electron from the highest occupied molecular orbital (HOMO) to the lowest unoccupied molecular orbital (LUMO). As shown on the left side of Fig. 1 (b), this creates an excited state in which the electron and the remaining hole are bound by a Coulomb attraction, forming a Frenkel exciton. The electron and hole can move along the DNA double strand by molecular orbital overlap between adjacent bases. On an ultrafast timescale, they can separate to form a charge-separated state, generating an electric dipole moment, as shown in the centre of Fig. 1 (b). Energy dissipation via an internal conversion mechanism relaxes the DNA molecule to its equilibrium state.


## 3 QuantumDNA Package Structure


## 3.1 Workflow Structure

The QuantumDNA package can be easily installed using the Python pip installer with the following command:

The study of DNA charge dynamics in a coarse-grained quantum framework requires addressing different challenges at different scales. To ensure clarity, modularity, and ease of future development, each class in QuantumDNA has been designed to handle a specific aspect of the simulation. Two particularly important classes, illustrated in Fig. 3 , focus on incorporating environmental interactions, which are essential because DNA in vivo is always embedded in a complex cellular environment. These core components include the isolated DNA system ( TB_Ham , blue) and its environmental interactions ( Lind_Diss , red), following the well-established Lindblad formalism for modeling open quantum systems. A complete overview of all QuantumDNA classes is given in Tab. A1 in the Appendix. Meanwhile, Fig. 3 presents a conceptual illustration of the overall structure of the package.

The QuantumDNA package aims to bridge the gap between experimental DNA measurements and tangible predictions about the consequences of charge dynamics along the DNA molecule. Therefore, the first step is to evaluate suitable parameters for the TB model from the measured distribution of atoms of the DNA sample of interest. The input parameters to define the DNA TB model can be provided in three different ways: (1) by direct calculation within the package using the state-of-the-art LCAO methods developed by Mantela et al. [ 26 ] (see Section 4 ) provided the geometric distribution of atoms in the DNA segment; (2) by using parameters from the literature, which are already included and available in the package and summarized in Table A3 ; (3) by providing a custom set of parameters as input by the user. These atomistic parameters form the basis for a coarser-grained TB framework, allowing users to model the physical properties of DNA at larger scales.

When calculating the parameters from the distribution of atoms in the system of interest, this distribution can be provided in XYZ or PDB format, the standard file format used by the Protein Data Bank (PDB) to represent DNA structures. The preparation of the molecular structure file includes the removal of the backbone atoms, as the influence of the backbone is taken into account indirectly in the parameterization of the environmental effects, as discussed below. Further developments currently underway will implement the ability to investigate possible CT phenomena directly mediated by the backbone to further refine the accuracy of the model, as recently investigated by Kordas et al. This pre-processing step can easily be done manually or by using freely available software such as Biovia Discovery Studio [ 27 ] or similar molecular editing tools.

Given a specific DNA segment, the preferred strategy for obtaining the required parameters includes the choice of the best TB model for the analysis to be performed. The choice of the TB model (to be selected from several built-in options as shown in Fig. A2 ) is crucial as it determines the trade-off between the required level of detail and computational efficiency. Fig. A3 shows an example of the scaling of computational times as a function of the chosen TB model and the length of the DNA sequence. Once the DNA sequence of interest and the specific TB model have been chosen, the isolated system is well-defined.

In the following example, we set up a model to simulate the dynamics of an exciton initially localized at the leftmost guanine (G) within the GCG sequence occupying the 2nd, 3rd, and 4th base pairs of the 1BNA dodecamer. The 1BNA structure is widely recognized as a benchmark in computational structural biology due to its historical significance as one of the first high-resolution B-DNA structures [ 28 ] . The corresponding PDB file can be obtained from rcsb.org .

For this simulation, we use the Extended Ladder Model (ELM) shown in Fig. 6 (b) and parameterize it using two different approaches: (1) computing parameters from a PDB file that provides atomic-level structural information, and (2) using a predefined parameter set from the literature.

To compute TB parameters for the 1BNA molecular structure, we select the PDB file and the desired TB model, and proceed with calculating and saving the parameters:

Once the set of parameters has been generated, the DNA model Hamiltonian can be easily constructed using the TB_Ham class. However, as mentioned above, QuantumDNA’s capabilities extend beyond the simulation of isolated TB models. To account for environmental effects, the Lindblad_Diss class allows the inclusion of various dissipative processes, allowing users to model system-bath interactions relevant to their specific research questions. This functionality makes it possible to introduce quantum decoherence and relaxation effects, or to simulate the escape of excitons into the environment - phenomena that have been experimentally investigated, for example, by Kohler et al. [ 18 ] .

In this example, we restrict the system-bath interactions to those governing electron-hole recombination and energy dissipation into the thermal environment:

In the following, we use the built-in set of parameters presented in Ref. [ 29 ] with the source identifier Hawke2010 :

Once the parameters are set, the following code creates the instances for the TB Hamiltonian of the isolated DNA double-strand ( TB_Ham class) and its interaction with the environment ( Lindblad_Diss class):

The system dynamics and various observables can now be analyzed using the ME_Solver class, which uses the QuTiP master equation solver [ 30 , 31 ] . This class allows the calculation of key properties, including the population dynamics and charge coherences within the modeled DNA segment. In addition, several built-in observables are available, such as the average excitonic lifetime and the dipole moment resulting from electron-hole separation. In the following, we demonstrate how to compute and visualize the time evolution of electrons, holes and excitons, as well as how to evaluate the aforementioned observables:

A complete list of the default settings used in the classes can be found in Tab. A2 , while a detailed description of all available classes and functions can be found in the official QuantumDNA documentation webpage .


## 3.2 GUI Setup and Usage

In addition to its Python-based implementation, the QuantumDNA package features an intuitive and user-friendly GUI designed to facilitate its use by researchers with limited experience in computational techniques. To demonstrate its functionality, we present an example workflow based on the previously introduced 1BNA dodecamer. A schematic representation of the 1BNA structure is shown in Fig. 4 (a).

Once the PDB file has been processed, the GUI can be started using the following command, either from a terminal or within a Jupyter notebook:

The main GUI interface, shown in fig. 4 (c), provides an intuitive environment for setting parameters and visualizing results efficiently. To generate a new set of TB parameters specific to the 1BNA dodecamer, select the "PDB Input" option (highlighted in orange). This action opens a separate window, as shown in Fig. 4 (b). Upload the edited PDB file, assign an identifier, and select a TB model. Once the TB parameters have been calculated, restart the GUI to ensure that they are correctly loaded into the main menu.

In the menu, specify the DNA segment to be simulated (in this example, GCG, highlighted in fig. 4 (a)) by entering it in the appropriate field (highlighted in blue in Fig. 4 (c)) and confirming with the first button (red 1). Additional simulation settings can then be adjusted, the default values are listed in the Tab. A2 . It is important to update the source field to 1BNA to ensure that the newly generated TB parameters are used instead of the default Hawke2010 settings. After configuring all options, press the second confirmation button (red 2), which will initialize an instance of the ME_Solver class in the background.

The right panel of the interface provides various calculation and visualization options. The excited state properties can be calculated (green frame), while the charge dynamics can be visualized using the heatmap option, which provides an intuitive representation of the charge dynamics similar to [ 32 ] . Finally, pressing the Submit button (red 3) generates the heatmap, which can be saved for further analysis, as shown in Fig. 4 (d).


## 4 Methodology


## 4.1 Linear Combination of Atomic Orbitals (LCAO)

Ab initio methods, such as Density Functional Theory (DFT) and post-Hartree-Fock (post-HF) techniques, provide accurate electronic structure calculations for small DNA fragments near equilibrium. More advanced approaches, such as Real-Time Time-Dependent DFT (RT-TDDFT), enable the study of dynamical, out-of-equilibrium phenomena. However, the computational cost of these methods scales rapidly, making them impractical for systems beyond 3–4 nucleotides, thereby limiting their applicability to long-range CT studies. To efficiently analyze large ensembles of DNA sequences, alternative methods with higher numerical efficiency are required.

A significant breakthrough came with the LCAO-based approach introduced by Endres, Cox, and Singh [ 33 ] , which calculates CT parameters by deriving molecular orbitals (MOs) from the overlap of atomic orbitals (AOs) using the semi-empirical Slater-Koster method. The open parameters in this model were optimized to reproduce results from high-accuracy ab initio calculations. Building on this foundation, Hawke et al. [ 29 ] refined the parameterization to generate a more comprehensive set of TB parameters at both the single-base and base-pair levels. More recently, Mantela et al. [ 26 ] further extended the LCAO approach by incorporating all valence orbitals, moving beyond Hückel-type LCAO. This improvement enhanced its applicability to DNA charge transfer and transport studies, including cases involving distorted or mutated DNA sequences [ 34 ] .

To achieve the required accuracy for charge dynamics simulations while maintaining computational efficiency, QuantumDNA employs an LCAO method to compute CT parameters between neighboring bases in the TB model (DNA bases/base pairs). Each MO is expressed as a linear combination of AOs:

where i ∈ I i\in I runs over all the AOs of a given atom, and α ∈ N \alpha\in N runs over all atoms in the molecule.

Following the current state-of-the-art, we include in our calculations all valence orbitals of the atoms constituting each DNA base, including the 2s, 2p x , 2p y , and 2p z orbitals for the carbon (C), nitrogen (N), and oxygen (O) atoms, and the 1s orbital for the hydrogen (H) atoms. The AOs are assumed to be orthogonal to each other, i.e. ⟨ ϕ i ​ α | ϕ j ​ β ⟩ = δ i ​ j ​ δ α ​ β \braket{\phi_{i\alpha}|\phi_{j\beta}}=\delta_{ij}\delta_{\alpha\beta} .

The MOs are obtained as eigenstates of the molecular Hamiltonian with the their energies being the corresponding eigenenergies. Therefore, we determine the coefficients c i ​ α c_{i\alpha} by diagonalizing the molecular Hamiltonian that is constructed from the constituent AOs. To quantify the AO overlap J χ J_{\chi} , we employ Slater-Koster two-center transfer integrals, where χ ∈ { s ​ s , s ​ x , x ​ x , x ​ y } \chi\in\{ss,sx,xx,xy\} represents the overlapping orbitals [ 35 ] .

The overlap of AOs depends on both the distance d d between the atoms and the angles integrated into the directional cosines ξ \xi derived from the vector connecting the atoms as shown in Fig. 5 .

To calculate each interaction value V χ V_{\chi} we use the quadratic decay in Eq. ( 2 ) as proposed by Harrison [ 36 , 37 ] , which is valid for the typical interatomic distances within a DNA base. However, since these expressions are limited to intrabase interactions, we include an exponentially decaying term in Eq. ( 3 ) to account for the overlap between AOs of neighboring DNA bases [ 29 , 26 ] .

where d 0 = 1.35 ​ Å d_{0}=1.35~\text{\AA} represents the typical bonding distance within a DNA base.

The constants C χ C_{\chi} are determined by fitting the method to experimental and ab initio results. QuantumDNA includes several parameterizations for these constants, with the default setting based on the latest MSF LCAO parameterization [ 26 ] .

To identify the HOMO and LUMO of each DNA base, we assume that all MOs below the Fermi level are occupied according to the Pauli exclusion principle, with each energy level accommodating two electrons due to spin degeneracy. Oxidation of a DNA base removes an electron from the HOMO, leaving a positively charged hole. Conversely, reduction adds an electron to the LUMO. Photoexcitation produces both an excited electron in the LUMO and a hole in the HOMO.

To estimate the CT parameters for both electrons and holes between neighboring DNA bases or base pairs, we compute the overlap of their MOs at the HOMO and LUMO levels. Fig. 6 (a) shows the overlapping MOs as shaded regions, representing molecular states that facilitate CT. The CT parameter between two adjacent molecules A A and B B is determined from this overlap as follows:

where H int H_{\text{int}} is the molecular interaction Hamiltonian describing the coupling between molecules A A and B B .

The following code demonstrates how to display the computed energies and CT parameters for two neighboring DNA bases, Adenine (A) and Thymine (T), derived from a given DNA geometry. In this example, the molecular geometry files are saved as A.xyz and T.xyz in the same directory. These files can be obtained from PubChem: Adenine (CID 190) and Thymine (CID 1135).

Once the parameters for all the neighboring bases of the DNA segment under analysis have been evaluated, both for the HOMO and LUMO orbitals, they can be used as parameters in a coarser TB model (see Fig. 6 (b)) to model the dynamics of a charge along its double-strand.


## 4.2 Tight-Binding (TB) Models

The DNA molecule is a very complex system with many degrees of freedom, making a complete theoretical quantum description of it neither feasible nor practical. In order to reduce the complexity of such an analysis, the use of TB models, which have been developed to capture the most relevant features of a complex system while discarding less important ones, is well established. In DNA CT simulation, TB models have been used in many different studies, see Refs. [ 38 , 39 , 17 , 16 , 40 ] and references therein.

TB models simplify the complex quantum mechanical problem at hand by introducing a coarse-grained approach that reduces each DNA base or base pair to a single degree of freedom, i.e., a site in the TB model. The couplings between neighboring sites are evaluated by considering the MO overlap between neighboring DNA bases, thus generating an effective model that captures the dynamics of a charge along different sites of the DNA strand, neglecting the charge dynamics within the atoms of each site. Since each nucleobase contains 13 to 16 atoms with multiple AOs, this approach reduces complexity by several orders of magnitude and thus significantly reduces the computational time needed to study larger DNA segments that are inaccessible by the ab initio methods mentioned above. TB models combine computational efficiency with physical accuracy, paving the way for the systematic analysis of large ensembles of DNA sequences.

The package includes several TB models for different levels of accuracy in DNA simulations, which are visualized in Fig. A2 and described below:

The Wire Model (WM) simplifies DNA by representing each base pair as a single TB site, providing a description at the base pair level. This model is useful for studying general DNA transport and conductance properties, but does not account for strand-specific dynamics.

The Ladder Model (LM) provides higher resolution by treating each DNA base as an individual TB site, thus capturing details at the single base level. It includes vertical hopping interactions within base pairs, but simplifies the DNA structure by representing it as a linear molecule, ignoring its helical symmetry.

The Extended Ladder Model (ELM) builds on the LM by incorporating the helical symmetry of DNA. This is achieved by including diagonal interstrand CT, resulting in a more accurate structural representation of DNA. As it is a popular TB model for DNA, QuantumDNA uses it by default, as shown in Fig. 6 (b).

Fishbone models (FWM / FLM / FELM) take complexity a step further by adding explicit modeling of the sugar-phosphate backbone, shown as brown rectangles above and below the strands in Fig. A2 . This improved representation captures the influence of the backbone on DNA dynamics, improving accuracy at the cost of increased computational complexity.

As shown in Fig. A4 in the appendix, the complexity and computational time required by each TB model increases, from top left to bottom right (in the legend). This is due to the different number of TB sites and number of CT parameters required to build each of those models.

QuantumDNA assigns a tuple ( i , j ) (i,j) to each TB site, where i i is the strand index and j ∈ { 1 , … , N } j\in\{1,...,N\} is the TB site index within the strand, given a strand length of N N . These tuples form a set Λ \Lambda , which represents the collection of the TB lattice sites. The local state | p i , j ⟩ \ket{p_{i,j}} describes the presence of the particle p p (electron, hole or exciton) at the TB site indicated by the tuple ( i , j ) (i,j) . Each TB Hamiltonian consists of two parts: a localization part containing the energies of the bases (HOMO and LUMO estimated energies) and a tunneling part containing the CT parameters (from the overlapping MOs of neighboring bases):

The equations for the different TB models in Fig. A2 are explicitly given Eqs. ( 15 ) in the appendix.

When UV light photoexcites an electron from a lower-energy orbital to a higher-energy orbital in a DNA base, it leaves behind a positively charged hole that binds with the electron and forms a paired system often referred to as exciton . Such state is described by the electron-hole configuration state | e α 1 ​ h α 2 ⟩ \ket{\text{e}_{\alpha_{1}}\text{h}_{\alpha_{2}}} , where α k = ( i k , j k ) \alpha_{k}=(i_{k},j_{k}) . The package includes two different types of two-body interactions, as described by Bittner [ 17 , 32 ] , between the electron and the hole: the Coulomb interaction J ⁡ ( r ) J(r) , representing the electron-hole attraction, and the exchange integrals K ⁡ ( r ) K(r) , which account for spin-exchange coupling. Assuming that the Coulomb interaction decays algebraically and the exchange interaction decays exponentially with the distance r r between the charges, we implement these energy terms as [ 17 , 32 , 16 ] :

where it is assumed the value r 0 = 1.0 ​ Å r_{0}=1.0\,\text{\AA} for the e-h separation within the same base [ 17 , 32 ] . The distance among different bases is then evaluated considering that two adjacent DNA bases are separated by about D = 3.4 ​ Å D=3.4\,\text{\AA} , both intrastrand and interstrand.

In addition to single CT, the exciton can be transferred along the DNA strand because of dipolar couplings between separated sites as described in [ 17 ] . Including the above introduced terms, the excited state Hamiltonian yields:

As a default choice, the QuantumDNA package implements a cut-off in the evaluation of the Coulomb interaction to the nearest neighbouring bases. This is justified because the thermal energy at physiological temperatures of 300 ​ K 300~\text{K} is about 0.3 ​ eV 0.3~\text{eV} , which is equal to the Coulomb energy at the base-stacking distance D D .

Normally, to account for such many-body interaction terms, it is necessary to explore an exponentially large Hilbert space with respect to the dimension of the system (number of DNA bases). However, the QuantumDNA package enforces the constraint that there is always either one exciton or no exciton in the system, allowing us to explore only a Hilbert space scaling quadratically in the length of the chain, i.e. | ℋ | = | Λ | 2 |\mathcal{H}|=|\Lambda|^{2} .

The code below gives an example of how to retrieve the full excited state Hamiltonian of a GC/CG dimer once its parameters have been set:

QuantumDNA provides useful tools for investigating the CT properties of isolated DNA chains, based on the evaluation of the dominant frequencies of charge oscillations along the chain. As the experimental study and manipulation of isolated DNA chains has become more relevant, as in the case of DNA origami [ 41 ] , such theoretical tools can be extremely useful to analyze the intrinsic properties of DNA, free from the complex environmental interactions present in living cells, and provide insights into the timescales of charge dynamics and average charge distributions, as investigated by Lambropoulos et al. [ 42 , 43 ] .

In this context, the unitary dynamics of the system is governed by the TB Hamiltonian H T ​ B H_{TB} via the von Neumann equation. For simplicity of notation, we use | α ⟩ \ket{\alpha} to represent both one-particle (1P) and two-particle (2P) states. The evolution of the system can be solved analytically and represented in terms of the eigenstates of the system | Ψ i ⟩ = ∑ α ∈ Λ c α , i ​ | α ⟩ \ket{\Psi_{i}}=\sum_{\alpha\in\Lambda}c_{\alpha,i}\ket{\alpha} and the corresponding eigenenergies E i E_{i} . The time-dependent population P α ​ ( t ) P_{\alpha}(t) of a state | α ⟩ \ket{\alpha} is then given by:

where ω i ​ j = ( E i − E j ) / ℏ \omega_{ij}=(E_{i}-E_{j})/\hbar represents the frequency associated with the energy difference between eigenstates E i E_{i} and E j E_{j} . The first term represents the time-averaged population for non-degenerate eigenenergies, while the second term accounts for the oscillations between different eigenstates and their corresponding amplitudes.

A detailed knowledge of the expected dynamics of a charge along the DNA chain, both in terms of long-term behavior and fast scale oscillations, can be particularly useful in interpreting experimental measurements that are averaged over time, especially when ultrashort timescales are not directly resolvable.

The code below provides an example of how to perform the analysis described above for the GC/CG double-stranded segment:


## 4.3 DNA Environment

CT within DNA in the cell under physiological conditions is influenced by the cellular environment. Interactions with the solvent, especially water molecules, and counterions can induce fluctuations in the energies of the nucleobases, alter the conformation of the MOs of each DNA base, and inhibit the quantum nature of charge transport due to decoherence and relaxation phenomena. Thus, a thorough analysis of the complex interplay between the DNA structure, its dynamical fluctuations and the surrounding environment is crucial for the development of realistic models of DNA electronic properties and their implications in living biological processes.

Several quantum physical models have been proposed to account for this effect [ 44 , 45 , 46 , 40 ] . Often the environment is modeled as an infinite set of bosonic harmonic oscillators interacting with electronic transitions (excitons) within the DNA molecule [ 47 ] . To describe the time evolution of a charge on the DNA strand without explicitly describing all the degrees of freedom of the bath, the influence of the bath on the particle has to be considered indirectly by solving an appropriate quantum master equation. This approach allows the effects of the environment on the charge dynamics along the DNA to be effectively represented, enabling the study of CT and excited state dynamics in biologically relevant systems.

To implement the above description in our modeling, the QuantumDNA package implements a set of Lindblad operators. Lindblad models are an efficient choice for simulating long DNA sequences due to their computational efficiency, ease of implementation, and analytical solvability for some specific systems. The Lindblad form of a quantum master equation for the time evolution of the density matrix ρ ⁡ ( t ) \rho(t) describing the charge dynamics is defined as:

where the first term describes the coherent unitary evolution of the TB Hamiltonian of the isolated DNA described in the previous subsection, and the Lindblad operators L k L_{k} capture the dissipative dynamics induced by environmental interactions. The relationship between the number of Lindblad operators and the number of TB sites (DNA sequence length) for each Lindblad model in the 2P description is illustrated in Fig. A3 in the appendix.

The package implements four distinct methods for incorporating environmental effects, summarized in Tab. 1 : (1) local dephasing, (2) global dephasing, (3) local thermalization, and (4) global thermalization. Dephasing models describe the loss of quantum coherence (decoherence) due to entanglement with the surrounding environment. However, unlike thermalization models, they do not drive the system toward a canonical thermal equilibrium state. In local models, each site interacts with an independent environment (bath), whereas global models assume a shared environment for all sites. For more details and benchmarking against more advanced beyond-Lindblad approaches, we refer to [ 48 ] .


## 4.4 Excitation Relaxation Channel

The DNA molecule is inherently photostable due to the rapid decay of its electronic excitations. To model this relaxation process, we adopt a minimalist approach inspired by pump-probe experiments as in [ 7 ] and theoretically introduced in [ 16 ] . To account for the possibility that the DNA molecule relaxes to its ground state after excitation (creation of an e-h pair), the Hilbert space of the system is extended to include the ground state of DNA, labeled | 0 ⟩ \ket{0} . In addition, intrinsic loss mechanisms are incorporated using Lindblad operators that describe the possibility of exciton recombination occurring at each site of the TB model with a tunable decay rate γ α \gamma_{\alpha} :

We identify the exciton lifetime as the time taken for the excitation to decay by ϵ = 1 / e \epsilon=1/\text{e} of its initial value, following [ 16 ] . Specifically, we define the exciton lifetime T T as the shortest time for which the population satisfies the condition:

In addition to describing the lifetime of the e-h pair, it is possible to quantify the separation between the electron and the hole (charge separation) occurring due to the dynamics of each particle using the charge separation operator d ^ \hat{d} , defined in our package as:

where α 1 = ( i 1 , j 1 ) \alpha_{1}=(i_{1},j_{1}) , α 2 = ( i 2 , j 2 ) \alpha_{2}=(i_{2},j_{2}) , and D = 3.4 ​ Å D=3.4~\text{\AA} corresponds to the average distance between adjacent DNA base pairs. The time-averaged charge separation, d ¯ \bar{d} , provides an estimate of the amount of charge separation over the exciton lifetime, T T :

The amount of separation between the electron and the hole can affect the electronic properties of DNA, as the two charges generate an electric dipole characterized by an effective dipole moment. This dipole moment can influence interactions with other molecules, such as proteins, which may be critical to the biological function of DNA.


## 5 Application and Benchmarking Examples

The development of QuantumDNA was driven by the observation that many research studies employ similar methodologies, such as TB models, to explore the quantum physical properties of DNA. This motivated the need for a unified platform to standardize and streamline these approaches. QuantumDNA therefore integrates methods from different research groups and has been benchmarked against published results.

In this section, we will use several examples to demonstrate the variety of different analyses that can be performed with the QuantumDNA package using just a few lines of code and only built-in functions. In particular, we will show how this package succeeds in converging the efforts of different research groups already working on this topic, but often pursuing independent research strategies. We then go on to show how this package paves the way for novel investigative strategies that can be integrated with those already existing in the field, thus setting the stage for more biologically oriented investigations.


## 5.1 Reproduction of Ultrafast Excitonic Dynamics along the DNA

In 2006 Eric Bittner presented one of the first theoretical investigations of the ultrafast dynamics of an exciton along the DNA chain [ 17 , 32 ] , using a TB model parameterized with ab initio calculations from Mehrez and Anantram [ 51 ] , also available in this package (source identifier Bittner2007 ). In his model, in contrast to several investigations carried out later by the community, he already includes a strategy to take into account the effects of the Coulomb and spin-exchange interactions that occur between the electron and the hole when both are present on the chain.

With the QuantumDNA package it is possible to reproduce the results developed by such modeling and to study the dynamics of electrons and holes along the chain under the influence of the same effects. In addition to the excitonic dynamics, it is possible to visualize independently the dynamics of the individual charges.

The example in Fig. 7 shows the results produced by the QuantumDNA package for a similar scenario considered in [ 17 ] , with an exciton initially placed over the fifth adenine of a double-stranded model consisting of 10 adenines (A) and 10 opposite thymines (T). The plot shows the dynamics for the electron, the hole, and the exciton. This plot can be easily obtained by running the code below:

The extent of these results can be generalized by modifying the input DNA sequence and system parametrization as explained in Section 3 . For example, by allowing the exciton to annihilate and thus escape the DNA strand, it is possible to model experimental results from Kohler et al. [ 18 ] to investigate the underlying mechanisms for the long-lived excitations measured in their pump-probe experiments on different DNA segments. This approach is described in more detail in [ 16 ] .


## 5.2 Modeling the Transition between Superexchange and Classical Hopping CT Regimes

Another example of the breadth of analysis provided by QuantumDNA is shown in Fig. 8 . Pioneering experiments by Giese et al. [ 52 , 24 ] observed a transition from quantum mechanical tunneling to classical thermal hopping in hole transport under varying conditions. They studied the sequence dependence of the transfer rates of a hole from its initial position on a donor base (G23) to an acceptor complex (triplet GGG) across a bridge of varying length, and deduced from the distribution of results that different CT mechanisms must take place depending on the bridge length. This phenomenon was later modeled theoretically by Simserides et al. [ 53 ] , whose simulations qualitatively reproduced the crossover found in Giese’s experiments. QuantumDNA incorporates this modeling strategy, allowing these theoretical results to be reproduced using the code below, and extended to more complex or biologically relevant systems.


## 5.3 Quantum Charge Dynamics over an Isolated or Open DNA Chain

The quantum dynamics of a charge on a DNA strand can be strongly influenced by the presence of an environment. In particular, the interaction of a quantum system with its environment is known to lead to a loss of coherence of the system, i.e. the tendency of the system to switch from quantum to classical behavior. Therefore, in order to understand the possible impact of quantum effects on biologically relevant systems, it is of utmost importance to carefully study the effects of the environment on the dynamics of a quantum system. Such an analysis, introduced by the work of Rossini et al. [ 40 ] , can be easily performed using the QuantumDNA package, as introduced in section 3 and illustrated in Fig. 9 . The system studied in the example is a double-stranded GCACG segment in which an electron or hole is initially placed on the LUMO or HOMO of the upper left guanine base. The top plots show the population of particles on this guanine over time for three different scenarios: (1) unitary system – the DNA is isolated; (2) local coupling with the environment – each site of the DNA strand interacts independently with the surrounding environment; (3) global coupling with the environment – the environment interacts with global modes (or eigenstates) of the DNA system.

The dynamics of the particles along the DNA chain varies depending on the scenario. Particles on isolated DNA oscillate continuously, while particles on interacting DNA gradually damp as they interact with the environment, reflecting the loss of quantum properties. The lower plots in Fig. 9 show a measure of the coherence, i.e. "quantumness", of the system, the sum of the absolute values of the off-diagonal terms of the particle density matrix. We emphasize that there are many ways to investigate how quantum a state is [ 54 ] , and that the QuantumDNA package is structured so that any preferred measure can be implemented to replace the built-in ones. The coherence measure of the unitary dynamics oscillates, maintaining the same recurring peak level, showing how the quantumness of the system is preserved over time. The plots for the interacting scenarios instead show a gradual loss of coherence to a final plateau, corresponding to the final equilibrium of the system. Further details can be found in [ 40 ] , while the code for the plot in Fig. 9 is given below:

Modeling the nature of quantum CT dynamics on DNA in the presence of an environment is crucial for any biologically relevant investigation, and finding the best modeling strategy for this task is still an open question, which the QuantumDNA package allows to address efficiently.


## 5.4 Effects of Mutations of the TERT DNA Sequence on Charge Dynamics

Finally, we present an example of novel investigations that can be carried out using the QuantumDNA package. Here, we investigate a specific sequence within the human genome, the so-called hTERT sequence, for human Telomerase Reverse Transcriptase . In 2013 two studies [ 55 , 56 ] were published describing how two specific non-coding mutations of hTERT, located at the 1.295.228 th and 1.295.250 th base pair of the fifth chromosome, were recurrent in the appearance of melanomas. In both cases, a GC base pair mutates to a AT base pair [ 57 ] . They are usually referred to as C228T and C250T hTERT mutations.

The QuantumDNA package allows us to investigate the effect of such mutations on the quantum CT properties of DNA segments containing them. In particular, we investigate their effect on the expected lifetime of excitons initially excited by external UV radiation, as melanoma is a well-known skin cancer. For both mutations, we modeled a double-stranded ELM-TB model containing three base pairs before and after the mutating one, for a total of 14 DNA bases. We then evaluated the average lifetime of an exciton initially located at each one of the available sites, in both the natural and mutant cases. Finally, in Fig. 10 we visualize the differences between the lifetimes evaluated in the natural and mutated cases for each site of the double strand using a heatmap. It appears clear how the mutations affect the lifetime of excitons along the DNA chain, with particularly strong effects for excitations originating at or near the site of the mutation.

The results presented at this stage are not intended to validate an effective quantum influence on the mechanisms linking hTERT mutations to melanoma, but rather to provide an example (currently under investigation) of how the QuantumDNA package can drive research on quantum CT transfer along DNA towards more impactful avenues for the fields of epigenetics and medicine.


## 6 Conclusion

In this paper, we present QuantumDNA, an open-source Python package for the numerical simulation and analysis of open quantum charge dynamics in DNA, which aims to bridge the gap between quantum physics, biology and medicine. This framework provides a versatile computational toolkit that integrates LCAO and TB models with quantum master equations, enabling researchers to explore charge transport, excitonic behavior and environmental effects in DNA. Through its modular architecture and easy-to-use GUI, QuantumDNA makes quantum simulations of DNA accessible to researchers from different disciplines, fostering interdisciplinary collaboration across multiple fields.

We have outlined the theoretical foundation of QuantumDNA, detailing its implementation of quantum CT models and its ability to reproduce known experimental and theoretical results. Furthermore, we have demonstrated its applicability by presenting benchmark simulations and biological case studies, including the implementation of known models from the literature and the investigation of possible effects of sequence mutations on exciton lifetimes. These examples illustrate the potential of QuantumDNA to provide new insights into genetic and epigenetic phenomena through quantum physical analysis.

While this first release lays a solid foundation, future developments will focus on extending the capabilities of the package, including the incorporation of Green’s function methods for improved transport calculations and more advanced LCAO parameterizations that explicitly include backbone-mediated CT, an area of growing interest in the community [ 58 ] . In addition, further refinement of environmental interactions will increase the biological relevance of QuantumDNA simulations.

As an evolving open-source platform, QuantumDNA encourages community contributions to refine and extend its functionalities. By bridging quantum physics and computational biology, QuantumDNA paves the way for novel investigations of the electronic properties of DNA, offering new perspectives on its role in DNA repair, gene expression and regulation, and potential medical applications.


## Acknowledgements

The authors would like to thank Reiner Siebert and Ole Ammerpohl for fruitful discussions, especially regarding the medical and epigenetic applications of this package. We thank Paul Raschke for his contributions to the technical development of the TERT results.

This work has been supported by the Center for Integrated Quantum Science and Technology (IQST) and the BMBF through the QCOMP project in Cluster4Future QSens.


## Data Availability

The source code of the package is freely available under the BSD 3-Clause License and can be accessed on GitHub at github.com/dehe1011/QuantumDNA . The documentation webpage including the API and a user guide with tutorial Jupyter notebooks is available at quantumdna.readthedocs.io/en/latest/ . Tutorial Notebooks are also available at github.com/dehe1011/QuantumDNA-notebooks . Contributions to the code are welcome, especially for integrating interfaces with other tools.


## References


## Appendix A Appendix

In the above expressions, TB parameters that describe transfer to TB sites not included in the set Λ \Lambda are set to zero. Specifically, we have t i , j = h i , j = r i , j + = r i , j − = 0 ​ if ​ ( i , j ) ∉ Λ t_{i,j}=h_{i,j}=r^{+}_{i,j}=r^{-}_{i,j}=0\,\text{if}\,(i,j)\notin\Lambda .