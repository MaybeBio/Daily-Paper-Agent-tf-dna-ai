## Abstract

The phase separation model for transcription suggests that transcription factors (TFs), coactivators, and RNA polymerases form biomolecular condensates around active gene loci and regulate transcription. However, the structural details of condensates remain elusive. In this study, for Nanog, a master TF in mammalian embryonic stem cells known to form protein condensates in vitro , we examined protein structures in the condensates using residue-level coarse-grained molecular simulations. Human Nanog formed micelle-like clusters in the condensate. In the micelle-like cluster, the C-terminal disordered domains, including the tryptophan repeat (WR) regions, interacted with each other near the cluster center primarily via hydrophobic interaction. In contrast, hydrophilic disordered N-terminal and DNA-binding domains were exposed on the surface of the clusters. Electrostatic attractions of these surface residues were responsible for bridging multiple micelle-like structures in the condensate. The micelle-like structure and condensate were dynamic and liquid-like. Mutation of tryptophan residues in the WR region which was implicated to be important for a Nanog function resulted in dissolution of the Nanog condensate. Finally, to examine the impact of Nanog cluster to DNA, we added DNA fragments to the Nanog condensate. Nanog DNA-binding domains exposed to the surface of the micelle-like cluster could recruit more than one DNA fragments, making DNA-DNA distance shorter.

Author summary In eukaryotic transcription regulation, enhancer elements far from the promoter are known to modulate transcriptional activity, but the molecular mechanism remains elusive. One of these models, the phase separation model, suggests that transcription factors (TFs), coactivators, and transcription machinery form biomolecular condensates that include enhancer and promoter elements, making enhancer-promoter communication possible via the protein network in the condensate. Nanog, one of the core TFs involved in mammalian embryonic stem cells, has been reported to have the ability to form condensates. In this study, we addressed the structural details of Nanog condensates by performing residue-level coarse-grained molecular simulations. We found that Nanog formed micelle-like clusters via primarily hydrophobic interactions between tryptophan repeat regions in the C-terminal disordered domains within the condensate. On the other hand, highly charged N-terminal and DNA-binding domains were exposed to the surface of the micelle and were responsible for bridging many micelles into a condensate. The micelle-like clusters and condensate were dynamic and liquid-like. In addition, Nanog condensates could induce DNA-DNA attraction mediated by micelle-like structures.


## Introduction

Eukaryotic transcription factors (TFs) regulate gene expression by binding to cis-regulatory regions, especially enhancers, and by recruiting other factors, such as coactivators and RNA polymerases. In mammalian embryonic stem cells (ESCs), a small set of TFs called master TFs, including Nanog, Sox2, and Oct4, are known to regulate the expression of many other genes crucial in controlling the ESC state [ 1 ][ 2 ][ 3 ]. At some active gene loci in ESCs, molecular condensates or clusters are found near super-enhancer regions, where master TFs and coactivators, including mediator complexes, are enriched [ 4 ][ 5 ][ 6 ][ 7 ]. The levels of active histone markers H3K27ac and H3K4me1 are also higher in these regions [ 5 ]. The transcription of these genes is affected by the concentration of the construct [ 5 ]. Based on these observations, a phase-separation model for transcription has been proposed [ 8 ]. Transcription factors, coactivators, and RNA polymerases form condensed clusters through fuzzy and multivalent interactions. Many components of clusters contain intrinsically disordered regions, which can form condensates via liquid-liquid phase separation (LLPS) [ 9 ]. However, the molecular structures and underlying mechanisms of LLPS remain unclear.

Biomolecular LLPS is involved in several cellular functions. However, it is generally difficult to study the details of the molecular structures in condensates using experimental methods owing to the limitation of the temporal and spatial resolutions. Molecular dynamics (MD) simulations are a complementary approach for elucidating the molecular structure of these protein condensates. Molecular dynamics simulations can provide insights into the atomic interactions of individual residues and their roles in driving LLPS. Standard all-atom MD simulations are not feasible for such long-term behavior in large-scale systems. In such cases, coarse-grained (CG) models can effectively accelerate the simulation speed[ 10 ], and were applied to simulate LLPS[ 11 ][ 12 ][ 13 ][ 14 ]. In the commonly used residue-level CG model, each protein amino acid residue is represented by a mass particle. Globular domains are often treated with structure-based Go-type terms to maintain a native-like folded conformation[ 15 ][ 16 ]. In addition, sequence-dependent interactions, termed hydrophobicity scale (HPS) potential[ 11 ][ 17 ], are used to describe physicochemical interactions, such as electrostatic and hydrophobic interactions between disordered regions. The interaction parameters of amino acids have recently been refined towards the LLPS simulations[ 11 ] [ 12 ][ 17 ][ 18 ].

In this study, we focused on Nanog, a master TF, to study the molecular mechanism of protein condensates and their effect on DNA. In mouse ESCs, the cytokine leukemia inhibitory factor induces self-renewal [ 19 ][ 20 ]. Nanog drives the self-renewal of ESCs independently of leukemia inhibitory factor [ 21 ][ 22 ]. Nanog consists of three domains: the N-terminal domain (NTD), DNA-binding domain (DBD), and C-terminal domain (CTD) ( Fig. 1A ). The DBD is a globular domain consisting of three α-helices [ 23 ]. The NTD and CTD are intrinsically disordered and essential for transactivation [ 24 ]. The NTD is highly charged, similar to many transactivation domains of other TFs[ 22 ][ 21 ][ 24 ]. In contrast, the CTD has only a few charged residues ( Fig. 1B ). Interestingly, it was revealed that in mouse ESCs, the transactivation ability of Nanog CTD was approximately 7-fold higher than that of NTD [ 24 ]. The CTD consists of eight to ten tryptophan repeats (WRs), which are five-residue long and begin with tryptophan (Trp). The WR regions are crucial for the function of Nanog in forming homodimers or oligomers [ 25 ][ 26 ][ 27 ][ 28 ]. When Trp residues in WRs are mutated to Ala, Nanog cannot form complexes, and leukemia inhibitory factor-independent self-renewal ability is reduced [ 25 ][ 26 ][ 27 ][ 28 ]. However, the molecular mechanism of LLPS formation and the relationship between oligomerization and LLPS remain unclear.

In this study, we examined the molecular mechanism of droplet formation by human Nanog using CG MD simulations ( Fig. 1C, D ). We first verified our model and observed LLPS when the simulation started with condensed and uniformly distributed configurations. We found that Nanog formed condensed clusters primarily via its hydrophobic residues in the CTDs and that the condensate contained micelle-like clusters. These clusters were formed via interactions between WR regions. When we introduced the eight mutations from Trp to Ala, as was done in the previous experiment, the clusters broke, and molecules in the condensate diffused to the dilute phase. The CTD-only mutant formed a more compact condensate than the wild type (WT) did, suggesting that the NTD and DBD are essential for higher fluidity. Finally, we added DNA fragments to the Nanog condensates and observed that the DNA fragments bound to the surface of the clusters. DNA fragments were closer to each other when mediated by Nanog condensates.


## RESULTS AND DISCUSSIONS


## Phase separation of simulated human Nanog

Before investigating the detailed structure and dynamics of human Nanog, we first examined our simulation model to confirm whether it could reproduce the phase separation observed in the experimental results [ 9 ]. An in vitro experiment showed that Nanog formed droplets in a solution with an average concentration of 10 μM and 10 wt. % polyethylene glycol (PEG) as a crowder [ 9 ]. We performed MD simulations for a system containing 200 human Nanog proteins in a slab simulation box of 300Å × 300Å × 3000Å[ 11 ], starting from a completely phase-separated configuration (see Methods for the initial configuration setup). We repeated eight independent runs of 5 × 10 7 MD steps with different stochastic forces.

Figure 2A depicts the time courses of the center of mass of every Nanog molecule along the long axis (z-axis) in one trajectory, indicating that most molecules remain in the condensed phase, and a few molecules leave the condensate (Fig. S1 for the other trajectories, Movie S1). The time courses of the condensed phase size suggest that the trajectories reach near-equilibrium after 2∼4 × 10 6 MD steps (Fig. S2A, B). The final structure is shown in Fig. 2B . In all the eight trajectories, the phase-separated configurations were stable during the simulations. Once some molecules diffuse into the dilute phase, they diffuse and occasionally merge into the high-density phase. The density of the amino acids along the z-axis in Fig. 2C shows clear evidence of phase separation.

The Nanog concentration in the dilute phase of the phase-separated state corresponds to the critical concentration for phase separation. To quantify the concentration in the dilute phase, we counted the number of Nanog molecules in the dilute phase (Fig. S3). In each trajectory, one or two molecules were in the dilute phase at each step, and the average concentration of the dilute phase was 7.64 ± 0.046 μM. This value is consistent with the experimental result that human Nanog forms droplets at an average concentration of 10 μM, thus indicating that the critical concentration for phase separation is below 10 μM [ 9 ].

It should be noted that the in vitro experiments were performed with 10 wt.% PEG, which can change the phase separation behavior. Therefore, we briefly examined the effect of the crowder, including repulsive spheres, in the simulation box to represent ideal crowders (Fig. S5). The results showed that the condensate was stable during the simulation. Thus, this result does not contradict the experimental results. We note that adding the crowder markedly reduced the Nanog concentration in the dilute phase, thus decreasing the critical concentration for phase separation.

In addition to the above simulation that started from a phase-separated configuration, we also examined another initial configuration in which Nanog molecules were uniformly distributed in the slab simulation box. We performed one MD run with 1.4 × 10 8 MD steps for this system. Figure 2D shows the time courses of Nanog molecules along the z-axis, which indicates that Nanog quickly formed small clusters during the simulation, which occasionally merged into larger clusters. The final snapshot is shown in Fig. 2E . Clearly, this simulation did not reach equilibrium because of the limitation of simulation time. However, small- to medium-sized clusters were formed, which supports the view that Nanog can form small clusters or condensates, perhaps leading to a phase-separated form.

Previous experimental and theoretical studies demonstrated the effect of salt concentrations and thus roles of electrostatic interactions on LLPS[ 11 ][ 29 ]. Here, we examined the role of electrostatic interactions to the Nanog droplets by performing MD simulations with a higher and lower salt concentration than the above case of 125 mM. At 500 mM, from a completely-phase separated configuration, we saw gradual dissolution of the Nanog condensate: Many molecules diffused to the dilute phase ( Fig. 2F , Fig. S6D and S6E). Similar results were reported for other proteins including Sox2, FUS, and TDP43 in the previous experiments[ 29 ]. Interestingly, as shown in Fig. 2F , Nanog molecules did not fall apart to monomers, but remained forming small clusters. The high salt concentration weakened the electrostatic interactions, but did not change the hydrophobic interactions modeled as the HPS potential. Thus, we suggest that, while the condensate is stabilized by electrostatic interactions, small clusters are formed by non-electrostatic interactions. Next, at 50 mM ion concentration, the phase-separated state was stable during the simulations ( Fig. 2G , Fig. S6D, S6E). Figure 2G represents the snapshot at the end of one simulation at 50mM, which resembles that at 125mM conditions. However, the maximum density of amino acids was higher at 50 mM than that in 125mM ( Fig. 2H ). The condensate at 50mM salt was more compact than that at 125mM. The lower salt concentration strengthens the electrostatic interactions that led to higher density condensate.

We conclude that the current simulation model can reproduce the phase-separated form of Nanog observed in an in vitro experiment [ 9 ]. We suggest that the electrostatic interaction is important to form the Nanog condensate, or droplet, whereas hydrophobic interactions are responsible for forming small clusters.


## Micelle-like clusters in the Nanog condensate

The above observation in our simulations suggests that the condensed structures were not homogenous and were made of many clusters that are bridged to form the condensate. Especially in the simulation starting from a random and uniform distribution, Nanog formed distinctive small and near-spherical complexes ( Fig. 2E ). Similar structures were observed in the condensate in the simulation of the phase-separated form ( Fig. 2B ) and in the configurations with higher and lower salt concentrations ( Fig. 2F, G ). To study the structural features of the condensate, we calculated the inter-molecule residue-residue contact map using a cutoff distance of 6.5 Å ( Fig. 3A ). As shown in Fig. 3A , we found high frequencies of contact between the hydrophobic regions (155– 240 residues) in the CTD, especially between WR regions. We suspected that a fraction of Nanog molecules in the condensate might form clusters via direct interactions between the WR regions.

To quantify this possibility, we performed cluster analysis based on the contact between WR regions (see MATERIALS AND METHODS for details). The cluster size was distributed broadly from four to 70 molecules ( Fig. 3B ). The cluster size distribution converged well in the early stages of the simulations (∼5 × 10 6 MD steps). For each cluster, we calculated the distances of the three domains (NTD, DBD, and CTD) from the center of the cluster ( Fig. 3C ). The distributions indicate that in the clusters, CTDs are distributed near the center of the cluster, DBDs in the middle, and NTDs near the surface of the cluster. This bias suggests the presence of micelle-like structures. The CTD contains WR regions that attract each other. There were many charged residues in the NTD and DBD, but fewer residues in the CTD. These results are consistent with the typical physicochemical nature of the micelles. Similar to other surfactant molecules[ 30 ], we found that when the number of Nanog molecules in a cluster was small, spherical micelles were formed ( Fig.3D ). Cylindrical micelles were formed when the number of Nanog molecules increased ( Fig. 3E ).

In the current simulation setup, we included the HPS potential between the disordered regions, but not the DBD, because the HPS potential was developed for the disordered regions. However, we were concerned that this setup might artificially have induced micelle-like structures in our simulations. To test this possibility, two control simulations were performed. First, the HPS potential was applied to all amino acids, asking if this setup also exhibits the micelle-like structure of Nanog in the condensate (Fig. S7). For the second test, we simulated a mutant Nanog that lacked DBD (Note that there is no corresponding experiment at the moment and thus this is merely to test robustness of the micelle-like structure). The results showed micelle-like structures similar to those of the WT (Fig. S8). Therefore, we conclude that the micelle-like structures were not artifacts of the setup.

As mentioned above, we found similar clusters in the configurations with higher and lower salt concentrations. To check if these clusters were micelle-like or not, we did similar analyses for these results (Fig. S6 C, F). In each simulation Nanog formed micelle-like clusters. Interestingly, the micelle-like clusters were stable even in the higher salt concentrations (Fig. S6F). Comparing the contact maps of the medium (125mM) and higher (500mM) salt concentrations, we found that the contacts between NTDs and DBDs were lost in the higher salt concentrations. This result is expected because the NTD has some negatively charged residues and the DBD has many positively charged residues ( Fig. 1B ).

In summary, we suggest that Nanog forms droplets by two different interactions. First, Nanog forms micelle-like clusters primarily by the hydrophobic interactions between its WR regions. Next, clusters bind each other via electrostatic interactions between the NTD and the DBD.


## Fluidity in the Nanog condensate

To study dynamics of the Nanog condensates, we computed the mean square deviation of each Nanog molecule as a function of the time difference in the condensate as well as in the dilute phase as a control (Fig. S4). Each mean square deviation, as a function of the time difference, was well fitted by a linear line for both the dilute and condensed phases, indicating the normal diffusion. Thus, both the dilute and condensed phases can be regarded as fluids. In our simulations, the diffusion coefficient in the condensed phase was approximately 1/10 of that in the dilute phase.

Next, we tracked selected Nanog molecules in the condensate to examine protein fluidity in micelle-like clusters as well as in the condensate ( Fig. 4 ). Figure 4A and 4C represent movements of Nanog molecules that were in a selected region along z-axis at a time point 2.0 × 10 7 , as a proxy to the fluorescence recover after photobreaching (FRAP) experiment. Note that all the selected molecules were not in one micelle. The molecules diffused nearly everywhere within the condensate in approximately 10 7 MD steps. Next, Fig. 4B and 4D represent tracking of 11 Nanog molecules involved in a micelle-like cluster at a time point of 2.3 × 10 7 MD steps. We observed a dynamic rearrangement within the condensed phase. The number of Nanog molecules remained in the same cluster slowly decreased; six and three molecules after 0.4 × 10 7 and 0.8 × 10 7 MD steps, respectively from the reference time point. Within the cluster, the relative diffusion was restrained, by definition. Once ejected from the cluster, molecules started diffusing freely from the cluster.

To compare the diffusive spreading from one micelle and from one region not restricted to the micelle for the same pair of trajectories, we plotted in Fig. 4E the variance of the z-coordinates in the tracking molecules as a function of the time duration from the reference time points. Clearly, the variance increased faster for the sample from one region (termed FRAP) than that from one micelle (denoted as micelle). For the latter, the variance stayed nearly constant for a short period at the beginning, ∼0.3× 10 7 MD step, during which all the molecules remained in the same micelle. Next, we obtained the averaged variance as a function of the time duration over all the trajectories in Fig. 4F . We found that the diffusive spreading from one micelle is clearly slower than that from one region (FRAP). The spreading rate is not markedly different for different sizes of micelles; micelles containing 9-11 molecules and those containing 20-30 molecules showed very similar spreading rates. In summary, while we observed translocations of Nanog molecules from one cluster to another, the inter-cluster transition is markedly slow, relative to normal diffusion in the condensate.

In summary, micelle-like structures are not fixed, but dynamically change their component molecules. We suggest that although the condensates are not uniform and have micelle-like substructures, these underlying substructures are transient and dynamic. Within a micelle-like condensate, the molecular motion can differ from normal diffusion. Molecules involved in one micelle can be restricted to the micelle-like structures on a short time scale. Although molecules can depart from one micelle to reach another in the long term, it would involve an escape process with some free energy barrier.


## Tryptophan in the WR region is essential for the LLPS

The importance of Trp residues in the WR region has been demonstrated [ 27 ][ 28 ]. To examine the effect of Trp residues in the WR region on LLPS ability, we constructed a mutant model in which all eight Trp residues in the WR region were mutated to Ala (W8A) and performed the same simulation as above, starting from a totally phase-separated configuration. As shown in Figure 5A , the condensed phase dissolved quickly during the simulation of the W8A system. The W8A molecules diffused throughout the slab simulation box ( Fig. 5B, C ). We did not find any stable clusters or oligomers. Although the simulation was not long enough to reach a completely uniform state, a sufficiently long simulation would lead to a uniform distribution in the simulation box. The simulation clearly showed that Trp residues in the WR regions are essential for the formation of LLPS.


## Phosphorylation of Nanog slightly weakens the condensate

Nanog contains several serine residues that are known to be phosphorylated in human ESCs[ 31 ][ 32 ]. While the phosphorylation at the residues in the DBDs were well-studied, the effect of the phosphorylation in the NTDs remains unclear[ 32 ]. Previous studies about FUS showed that the phosphorylation destabilized the droplets[ 33 ]. To examine the effect of phosphorylation in the N-terminal domain on the droplet we constructed the mutant that changed the charge of Ser52, Ser56, Ser57, and Ser65 to -1.0 (Fig. S9A). These serine residues are well conserved and known to be phosphorylated[ 34 ][ 31 ]. The condensate of the phosphorylated Nanog was stable during the simulations (Fig. S9B, C). We found that the condensed configurations in the final frame have slightly more cavities than that of the unphosphorylated Nanog, and the density of amino acids also shows similar extension of the condensates (Fig. S9D, E). As mentioned above, the NTD has some negatively charged residues and the interaction between the NTD and DBD was important for the formation of droplets. The net charge of human Nanog in its unphosphorylated form is -1, and thus the phosphorylation changes the net charge to more negative (-5 in the current setup). We found that the phosphorylation decreased the contacts between the NTD and DBD (Fig. S9F). The phosphorylation in the NTD changes the charge balance between the NTD and the DBD and strengthens the repulsion between the NTDs. Previous studies showed that the mutation of the phosphorylation sites upregulated the reprogramming function of Nanog[ 31 ]. We suggest that the phosphorylation in the N-terminal domain destabilizes the droplets of Nanog, which should reduce the transcription of the target genes. We note that, given that the pKa value of the secondary ionization of the phosphate group is close to 7, the phosphate group can have -1.0 or -2.0 charges depending on its local environment. In our simulation, we used -1.0 to represent modest effects of phosphorylation. With the charge of -2 in the phosphorylated serine, we would expect even stronger effects than the current case.


## NTD and DBD form the cavity in the condensed configuration

The NTD and DBD were located on the surface of the micelle-like clusters of Nanog. These surface-exposed regions contain many hydrophilic and charged residues. This implies that repulsive forces can exist between the clusters. We presumed that these repulsive forces might create void spaces in the condensates, thereby enhancing fluidity. To test these propositions, we constructed a mutant that lacked the NTD and DBD (Only-CTD), and performed the same simulation as above. During the simulations of this mutant, the condensate was stable, as was the case for the WT-Nanog ( Fig. 5D ). However, the internal structure was distinct from that of WT-Nanog; As shown in Figure 5E , which is a snapshot of the final frame, we found a highly compact condensate without any significant cavity. Quantitatively, we calculated the density of amino acids along the long axis of the slab ( Fig. 5F ) and found that the density of amino acids in Only-CTD was much higher than that of amino acids in WT-Nanog. By deleting the NTD and DBD, which contain many hydrophilic and charged residues, the mutant became highly compact. In the case of WT-Nanog, small micelle-like clusters packed loosely to form a large condensate because of the relatively hydrophilic and charged NTD and DBD.

In a previous study, the CTD of Nanog alone was insoluble in water[ 28 ]. Our results indicated that WT-Nanog could dissolve in water owing to the formation of micelle-like structures.


## Condensates induce DNA-DNA attraction

Transcription factors form droplets along with chromatin, transcription machinery, and coactivators in a model of transcription condensates. To study the effects of the Nanog LLPS condensates on DNA, we added four 50 bp DNA fragments of the poly CG sequence to the neighbors of the condensate that contained ∼200 Nanog molecules. We note that the Nanog consensus sequence is far from the poly CG sequence. Here we used the poly CG sequence only to examine non-specific binding of Nanog via electrostatic interactions. During the simulation, the DNA fragments were incorporated into the Nanog condensate ( Fig. 6A ). Figure 6B , a snapshot of the final time, shows that DNAs are not located in the center of the condensate but are bound to the surface of the condensate. Figure 6C shows a close-up view of the micelle-like cluster in which one DNA fragment is bound to the surface. In the micelle-like clusters of Nanog, DBDs are exposed on the surface of the clusters so that DNA segments can access the DNA-binding domains of many Nanog molecules. We suggest that the micelle-like structure makes a DNA segment to easily bind to multiple Nanog molecules and to co-stabilize the complex.

In the simulations, multiple DNA segments were bound to the Nanog condensate, making the distance between the two DNA segments relatively close ( Fig. 6A ). To quantify this, we compared the DNA-DNA distance distribution in the Nanog condensate with that in a DNA-only system, where only four 50 bp DNA segments were simulated in the same slab simulation box ( Fig. 6D ). With the Nanog condensate, we found a prevalence of DNA-DNA centroid distances in the range of 100–200 Å. However, we did not observe this in the DNA-only system. In the micelle-like structure, the DBDs tended to be located at ∼80 Å from the center of the micelles ( Fig. 3C ). Thus, two DNA segments bound to the opposite end of the spherical micelle-like cluster had a distance of ∼160 Å. Micelle-like clusters can bind multiple DNA segments at once; therefore, the cluster makes the DNA fragments closer than in the DNA-only system. This is in agreement with recent experiments and with the transcriptional condensate model, which states that transcription factor condensates bring super-enhancers and promoters into proximity [ 35 ]. The DNA-DNA distance distribution has the second peak near 450 Å, which corresponds to the breadth of the Nanog condensate in the z-direction of the slab. DNA weakly favored the interface of the condensate, which resulted in the peak of the distribution corresponding to the breadth of the condensate.

We compared the density of atoms calculated from each type of the CG particles containing Nanog and DNA along the z-axis for simulations with and without DNA as shown in Figure 6E . The Nanog condensate containing DNA was slightly more extended than that without the DNA. Some Nanog DBDs that are bound to DNA cannot have the same attractive interactions to Nanog NTDs as in the case without DNA, which weakens the interactions between micelle-like clusters. The net negative charges of the condensate may also weaken the condensate.

To examine the saturation effect of DNA fragments, we added four more DNA fragments to the final configurations of the above simulation and extended MD simulations for 5.0 × 10 7 MD steps. During the simulations few DNA fragments entered the droplets; two of the four added DNA were completely dissociated, the other two resided near the interface of loose condensate (Fig. S10A, B). The snapshot at the end of the simulation showed large cavities in the droplet (Fig. S10C). The net charge of the condensate was highly negatively charged, and thus have overall electrostatic repulsions, which tends to break the droplet. The atomic densities along z-axis showed no significant difference between the cases containing four and eight DNA fragments (Fig. S10D). A previous experiment showed that a condensate of positively charged proteins is enhanced with a low density of RNA, but is dissolved with a high-density of RNA[ 36 ]. The current result may qualitatively correspond to the high-density case since Nanog has the net charge of -1.


## Biological significance

Nanog is one of the master transcription factors and regulates many genes cooperatively with other transcription factors such as Oct4 or Sox2 in mammalian ESC. Recent experiments showed that human Nanog forms condensate, or droplet, at the concentration 20μM[ 9 ]. Below the critical concentration to form the condensate, previous experiments identified formation of dimer as well as broad range of oligomers[ 26 ]. Our simulation study characterized structural feature in the Nanog condensate; human Nanog forms ∼100Å scale micelle-like structures, which are weakly bridged together to form larger-scale condensate. Hydrophobic interactions of the WR region, especially tryptophan, in the C-terminal domain are responsible for the micelle formation, whereas assembly of micelles into condensate is driven by electrostatic interactions in the N-terminal and DNA-binding domains. This micelle-like structure can have advantages for Nanog functions and explain some results obtained in previous studies.

First, we discuss possible states of Nanog in the cell. We estimated the critical concentration for the condensate formation as 7.6μM. While this is a rough estimate given the simplicity of the simulated model and the small number, i.e., 200, of Nanog molecules in the simulation system, we guess the real critical concentration would be between 1 and 10μM. Although the concentration of Nanog in ESC has not been characterized to our knowledge, the concentrations of other master TFs, Sox2 and Oct4, are known to be on the order of 1μM[ 37 ][ 38 ][ 39 ]. Therefore, Nanog alone unlikely to form the condensate in ESC. Yet, given the dimer or oligomer formation reported previously, we consider that the micelle-like cluster remains stable somewhat under the critical concentration for the condensate formation. Our simulation started from a random and uniformly distributed configuration showed prompt formation of micelle-like clusters of Nanog in the early stages ( Fig. 2D ), which would support formation of clusters even at lower concentration than the critical one. We are not sure if Nanog alone forms clusters or not in the ESC. Importantly, the critical concentration for the Nanog condensate is only modestly higher than the Nanog concentration in ESC. Enhancer regions of Nanog-target genes have multiple Nanog-binding sites in the super-enhancers, which would induce formation of either cluster or condensate.

Furthermore, the critical concentration should be further modulated by chemical modification such as phosphorylation. Our quick examination suggested that the phosphorylation of Nanog NTD sites slightly increases the critical concentration of the condensate formation. Thus, the phosphorylation would reduce the condensate formation for a given concentration and thus would down-regulate the target transcription. This result is, at least qualitatively, consistent with the experiment which showed that the phosphorylation-deletion mutant enhanced the Nanog activity[ 31 ]. Notably, our simulation showed that the cluster formation mediated by the CTD domain is not affected by the phosphorylation in the NTD.

The micelle-like structure can be efficient for Nanog function. In our model the CTDs interact with each other by hydrophobic interactions, and NTDs and DBDs are exposed to the surface of the cluster. Thus, DNA can easily be accessible to the DBD of Nanog. In addition, one DNA segments can bind multiple Nanog molecules, at least via sequence non-specific electrostatic interactions. The Nanog-DNA complex in the Nanog cluster can bring different DNA regions closer as shown in Fig. 6C and 6D . Previous studies using fluorescence resonance energy transfer experiments showed that Nanog complex could bring DNA fragments closer and the ability was lost by the mutation of tryptophan residues to alanine[ 28 ]. Nanog micelle-like cluster can bring enhancer and promoter regions closer in space.

Previous studies revealed that the mutant containing only CTDs is insoluble in aqueous solution[ 28 ]. As shown in Fig. 5E , the mutants containing only CTDs formed markedly more compact structures than the full-length Nanog. We suggest that the charged NTDs and DBDs exposed to the solution in the micelle-like structure prevents CTDs from forming insoluble aggregates.

A recent study proposed that the CTDs of Nanog can form cross-β structures with the same domains in different Nanog molecules and finally form fiber-like structures[ 28 ]. In the micelle-like structures, CTDs of several molecules are assembled at the center with high density. We speculate that within such a high-density mixture of CTDs, the WR region could form cross-β structure after some latent time. Our simulation that used residue-revel coarse-grained models cannot faithfully represent hydrogen-bonds interactions, making simulation of β-sheet formations intractable. Fully atomistic models are required to examine the roles of cross-β structures, which is left for future study.


## CONCLUSIONS

In this study, we investigated the molecular structures of condensates formed by human Nanog using CG MD simulations. We first verified the model and observed the LLPS when the simulation started from condensed and uniformly distributed configurations. We observed that Nanog formed condensates primarily via hydrophobic residues in the CTDs. We found that the condensate contained micelle-like clusters formed via interactions between the WR regions. When we added DNA fragments to the Nanog condensates, we found that the DNA fragments bound to the surfaces of the clusters could become closer to each other. At the same time, the Nanog condensate became less packed in the system with DNA.

The current study focused on the protein condensate formed by Nanog alone; however, chromatin should contain many types of TFs, coactivators, RNA, and RNA polymerases. How mixtures of TFs and other elements alter the nature of condensates is of interest for future studies.


## MATERIALS AND METHODS


## Molecules

We used full-length human Nanog protein, which contains 305 residues. For double-stranded DNA, we used a 50 bp poly-CG sequence.


## Coarse-Grained Model for Nanog and DNA

We used residue-level CG models for large-scale MD simulations of Nanog condensates, with and without DNA [ 40 ]. For Nanog, each amino acid was represented by one bead located at the Cα atom position, whereas each nucleotide in the DNA was represented by three beads, each representing a phosphate, sugar, and base.

The potential energy functions for Nanog consist of the AICG2+ potential [ 41 ], HPS potential[ 11 ][ 17 ], excluded volume interactions, and Debye–Huckel electrostatic interactions. For the DBD of Nanog, we used structure-based potentials from the AICG2+ model to maintain the folded structure [ 42 ]. For the disordered regions of Nanog, we used the flexible-local potential. For nonlocal interactions between disordered regions of both intra- and intermolecular interactions, we used the HPS potential. The HPS model has been used previously with progressively refined parameters for the simulations of LLPS of disordered proteins [ 43 ][ 44 ][ 45 ][ 29 ]. In the present study, we selected the parameter set obtained by Tesei et al. [ 17 ].

For DNA, we used the 3SPN.2C model developed by de Pablo et al. [ 46 ], which has been used together with the AICG2+ model in previous studies [ 47 ][ 48 ][ 49 ]. The excluded volume and Debye–Huckel electrostatic interactions were considered for Nanog-DNA interactions.


## Molecular Dynamics Simulation

As in previous simulation studies of LLPS, we used a slab simulation box (small x and y side lengths and a large z side length) with the periodic boundary condition. The slab box is superior to the more standard cubic box in that the slab box reduces the finite-size artifact. With a standard cubic box, the droplet, once formed, has spherical surface. For limited size of systems, significant fraction of molecules is involved to the interface of the two phases. Since the interface molecules have frustrated interactions, they lead to energy cost, or the surface tension. This gives rise large finite-size effect. On the other hand, with small x and y side lengths, molecules can form condensate spanning all x and y ranges. With the periodic boundary condition, the interface disappears in x and y directions. To represent the inhomogeneous two phases, we do need long z side length with the interface. The area of one interface is only the product of the side lengths of x and y, which is relatively small in the slab box.

We used a slab box with x, y, and z side lengths of 300, 300, and 3000 Å, respectively. From a preparatory simulation of one Nanog molecule, we estimated the largest residue-residue distance within one Nanog molecular was around 150Å. Thus, we used 300 Å as the x and y side lengths to prevent the molecules from interacting with their periodic images. As for the z side length, too large side length makes reaching equilibrium intractable. We checked the Nanog single molecule can diffuse ∼ 3000 Å within the possible simulation time. In the slab box, we included 200 molecules of human Nanog, with or without four DNA fragments, which corresponds to an average Nanog concentration of 1.23 mM. This average concentration is in between those of the low- and high-density phases of Nanog, which ensures the phase separation.

We used the MD simulation software GENESIS, which contains all models described above[ 50 ][ 51 ] [ 52 ]. All simulations in this study used Langevin dynamics at a temperature of 300 K. We used the GENESIS-CG-TOOL software to create the initial DNA structures [ 52 ].

In most simulations, we used completely phase-separated configurations as starting configurations for efficient sampling. To create the configurations, we first performed short MD simulations for the system that contained one Nanog molecule and took an ensemble of conformations. We chose highly compact structures from the ensemble and placed 200 copies into a sufficiently large simulation box with the same length in the x and y axes and with no overlap between amino acids. Subsequently, the box size was gradually decreased by 0.1 Å every 100 MD steps along the z axis to the size which was small enough for all molecules to be in the condensed phase. In the shrinking simulation we used the same force field as used in the sampling and decreased the box size slowly, so that interactions are locally well relaxed. For the simulation, starting from a homogeneous and random configuration, we placed 200 copies in the simulation box to avoid molecule overlap.

As product MD simulations, we performed eight, two, and two independent MD runs for monovalent salt concentrations of 125, 50, and 500mM, respectively, for WT Nanog from a completely-phase separated configuration. The system that contains four DNA fragments was conducted five times, whereas that containing eight DNA fragments was run two times. For the simulation with phosphorylated Nanog, we conducted two MD runs. For the rest of simulations, such as that from a random configuration of WT and the W8A mutant, we performed one MD run each.


## Analysis of Simulation Results

To calculate the concentration in the dilute phase, we performed clustering based on the distance between molecules. In each frame, we first defined the distance between the molecules by the minimum distance between the amino acids in the molecules and calculated the contact map. We assumed that there were no interaction energies between the molecules in the dilute and condensed phases; therefore, we defined the cutoff distance of the contact map as the cutoff distance of the HPS model (50 Å). Based on the clustering results, a molecule in the dilute phase was defined as one that was not in the clusters of five or more molecules.

We used a similar method to study the micelle-like clusters formed by interactions between WR regions. In this case, the cutoff distance to define the contact between the WR regions was 6.5 Å.

In most analysis, we used the Python library MDAnalysis to read and analyze the DCD files[ 53 ][ 54 ].


## Effect of Crowders

In a previous experiment, PEG8000 was used as a crowder to increase the concentration of the macromolecules. To mimic the effect of the crowder, we performed simulations in the system that contained crowders at a concentration equal to the experimental conditions and compared it with the experimental results. The concentration of PEG8000 in the experiment was 10% (weight percent) [ 9 ], corresponding to 2030 repulsive spheres in our simulation box.

To briefly examine the effect of PEG8000, we employed a simple model of PEG8000, with a sphere of radius R =19 Å, estimated from the radius of gyration Rg of PEG8000 ∼15 Å [ 55 ] as [ 56 ]. Repulsive spheres representing PEG8000 were included in the solution as crowders. The interactions between the PEG spheres and proteins were the only excluded volume terms.

We performed simulations under these conditions and found that Nanog formed a condensate with similar fluidity and residue-level contacts to the case without the crowders (Fig. S3D). We suggest that the crowders have minor effects on the structure of the phase-separated Nanog condensate. In contrast, the Nanog concentration in the dilute phase was markedly reduced by the inclusion of the crowders (Fig. S3B). However, the repulsive sphere is an ideal crowder model, which is too simplistic for the PEG model [ 57 ]. A more realistic modeling of the PEG in our system is left for future work.


## Author Contributions


## Conceptualization

Azuki Mizutani, Shoji Takada


## Data Curation

Azuki Mizutani


## Formal Analysis

Azuki Mizutani


## Funding Acquisition

Yuji Sugita, Shoji Takada


## Investigation

Azuki Mizutani


## Methodology

Azuki Mizutani, Cheng Tan


## Project Administration

Shoji Takada


## Resources

Yuji Sugita, Shoji Takada.


## Software

Azuki Mizutani, Cheng Tan


## Supervision

Shoji Takada.


## Validation

Azuki Mizutani


## Visualization

Azuki Mizutani


## Writing – Original Draft preparation

Azuki Mizutani


## Writing – Review & Editing

Cheng Tan, Yuji Sugita, Shoji Takada


## Competing interest

The authors have declared that no competing interests exist.


## Supporting information captions


## S1. Appendix. The detail about the analysis

S1. Figure. Other trajectories of WT human Nanog simulations

(A∼G) The results of the MD simulation for 200 Nanog with the same setup as Fig. 2 but with different random numbers. Cyan lines in each figure represent the trajectory of z-axis of centroids for each molecule during the simulation.

S2. Figure. Estimate of the convergence

(A)The time course of the size of the condensed phase. (B)The time course of the number of molecules in the condensed phase. In (A) and (B), the blue curve represents the average of all the eight trajectories, and the cyan represents the standard error.

S3. Figure. Estimate of the Nanog concentration in the dilute phase

The distribution of the concentration of molecules in the dilute phase. The horizontal axis represents the concentration of the molecules in the dilute phase, calculated from the volume of the dilute phase and the number of molecules in the dilute phase. The distribution was calculated for each trajectory, which was then averaged. Each error bar represents the standard deviation in eight trajectories. The vertical dashed line represents the experimental upper limit of the critical concentration (10μM)[ 9 ].

S4. Figure. The MSD of Nanog molecules

The mean square deviation (MSD) of a Nanog molecule as a function of the time difference. Comparison of the simulation results for a single Nanog molecule (orange) and the condensed state (cyan). Filled regions represent the standard deviation in all the eight trajectories. The dashed lines are obtained by the liner regression.

S5. Figure. Simulations with a PEG model

(A) The model of human Nanog and the PEG8000. The model of Nanog is the same as that in Fig. 1C . NTD, DBD, CTD, WR are colored with palecyan, green, teal, forest. The gray sphere represents a model for one molecule of PEG8000. (B) The result of one trajectory. Cyan curves represent the trajectories of z-axis of the centroids of 200 Nanog molecules. (C) The snapshot at the last frame of the same trajectory. We drew PEG8000 spheres with the radius smaller than the actual one. (D) The inter-molecule contact map. We used the cutoff distance 6.5Å between the two residues. The color represents the average number of contacts over all the frames and all trajectories. (E) The MSD as a function of the time difference. The yellow line represents the MSD of Nanog in the condensed phase with PEG. The blue line is the same result as in Fig. S4.

S6. Figure. Simulations of 200 Nanog in the slab box with 50mM NaCl or 500mM monovalent ion concentrations

(A, B) Time courses of 200 Nanog molecules along the z-axis (long axis of the slab) in the simulations with 50 mM condition. Figures A and B are results of the same setup with different random number seeds. (C) The residue contact map between two Nanog molecules in the simulation with 50 mM conditions. (D, E) Time courses of 200 Nanog molecules along the z-axis (long axis of the slab) in the simulations with 500 mM condition. Figures C and D are results of the same setup with different random number seeds. (F) The residue contact map between two Nanog molecules in the simulation with 500 mM NaCl conditions. Residue pairs of different molecules within 6.5Å are considered as the contact in (C) and (F).

S7. Figure. Simulations of 200 Nanog in the slab box in which the HPS potential was applied to all the amino acids including DBD

(A) Time courses of 200 Nanog molecules along the z-axis (long axis) of the slab. (B) The snapshot at the end of the same simulation as in A. (C) The residue contact map between two Nanog molecules. Residue pairs of different molecules within 6.5 Å are considered as the contact. The averaged numbers of contacts in all frames and trajectories are depicted. (D) The distributions of the distances of each domain from the center of mass of the cluster. Cyan, NTD; green, DBD; teal, CTD.

S8. Figure. Simulations of 200 Nanog mutant that lacks DNA binding domain

(A) Time courses of 200 mutant molecules along the z-axis of the slab. (B) The snapshot at the end of the same simulation in A. (C) The residue contact map between two Nanog molecules. Residue pairs of different molecules within 6.5 Å are considered as the contact. The averaged numbers of contacts in all frames and trajectories are depicted.

S9. Figure. Simulations of 200 Nanog phosphorylated at four serine residues in the N-terminal domains. (A)The mutated residues in the N-terminal domain of Nanog. The red colored serine were phosphorylated to have the charges -1.0. (B, C) Time courses of 200 Nanog mutants along the Z-axis (long axis) of the slab. Figure B and C represent results of the same setup with different random number seeds. (D) Snapshot of the end of the same simulations as shown in Figure A. (E) Density of amino acids along the z-axis. yellow, phosphorylated; blue, WT. (F) The residue contact map between two phosphorylated Nanog molecules in the simulation. Residue pairs of different molecules within 6.5Å are considered as the contact.

S10. Figure. Simulation of 200 Nanog with eight poly-CG DNA fragments.

(A, B) Time courses of 200 Nanog molecules (cyan) and eight DNA (red) along the z-axis (long axis) of the slab. (C) Snapshot at the end of the same simulation as (A). (D) Atomic density calculated from each type of CG particles including Nanog and DNA along the z-axis in the simulations of 200 Nanog without DNA and with four or eight DNA fragments. (Blue, with four DNA; Green, with eight DNA; Orange, without DNA)

S1. Movie. Trajectory of the simulation of 200 molecules of human Nanog in the slab box.


## Acknowledgements

The authors thank Soundhararajan Gopi and Giovanni B Brandani for helpful discussions. This research used computational resources of supercomputer Fugaku provided by the RIKEN Center for Computational Science through the HPCI System Research project (Project ID: JPMXP1020200101). The computer resources are provided by the HPCI system research project (project ID: hp200135, hp210177, and hp220170).


## Footnotes

Figure 4 revised

https://bsma.pdbj.org/entry/40