# Protein-DNA Co-condensation is Prewetting to a Collapsed Polymer


## Abstract
  The three-dimensional organization of chromatin is thought to play an important role in controlling gene expression. Specificity in expression is achieved through the interaction of transcription factors and other nuclear proteins with particular sequences of DNA. At unphysiological concentrations many of these nuclear proteins can phase-separate in the absence of DNA. In-vivo the thermodynamic forces driving these phases lead the chromosome to co-condense with nuclear proteins. However it is unclear how DNA, itself a long polymer subject to configurational transitions, interacts with three-dimensional protein phases. Here we show that a long compressible polymer can be coupled to interacting protein mixtures, leading to a generalized prewetting transition where polymer collapse is coincident with a locally stabilized liquid droplet. We use lattice Monte-Carlo simulations and a mean-field theory to show that these phases can be stable even in regimes where both polymer collapse and coexisting liquid phases are unstable in isolation, and that these new transitions can be either abrupt or continuous. For polymers with internal linear structure we further show that changes in the concentration of bulk components can lead to changes in three-dimensional polymer structure. In the nucleus there are many distinct proteins that interact with many different regions of chromatin, potentially giving rise to many different Prewet phases. The simple systems we consider here highlight chromatin’s role as a lower-dimensional surface whose interactions with proteins are required for these novel phases.


## MONTE-CARLO SIMULATIONS

### Model:
  We model a single self-avoiding polymer on a 3-D cubic lattice of linear dimension L = 64. A spin variable at lattice site i, sip=1 for sites which the polymers passes through and is 0 otherwise. The energy of configurations of this system is given by the Hamiltonian Hpoly:  (1) HpolykBT=-μp+vp∑isip+vp∑<i,j>sipsjp

  Here both sums are over lattice sites, and < i, j > represents nearest neighbors. μp is a monomer chemical potential which multiplies Np=∑isip, the total number of monomers in the polymer. vp is a monomer-monomer interaction energy, and the subtraction in the first term avoids counting contacts between sequential monomers. All simulations take place on periodic lattices, and are constrained to polymer configurations with initial position (L/2, L/2, 0) and final position (L/2, L/2, L). We also enforce that the polymer have length shorter than Nmax, typically 1500 monomer units, so that the polymer obeys L ≤ Np < Nmax. In most of our simulations Np ≈ Nmax, so that we sample an effectively fixed length distribution, but allow small fluctuations for numerical convenience.

  We couple this single long polymer (yellow in Fig.1A) to a solution of two types of shorter polymers which we term bulk molecules (red and blue in Fig.1A). Bulk molecules are held at fixed chemical potential μb and fixed length Nb. Following our previous work [17], we model the bulk as a mixture of two types of molecules prone to condensing together. Molecules of the same type are self-avoiding while molecules of different types may occupy the same site, and have an on-site attractive interaction with energy Jbulk. Their occupancies at site i are defined analogously to the long polymer by two additional spin variables si1 and si2. All molecules interact with a weak nearest-neighbor energy Jnn. The bulk Hamiltonian thus reads:  (2) HbulkkBT=−μbNb∑i(si1+si2)−Jbulk∑isi1si2−Jnn∑<i,j>(si1sj1+si1sj2+si2sj2)

  The long polymer and one of the bulk molecules, red in the Figures, are coupled by interactions of strength Jint, giving an interaction energy:  (3) HintkBT=-Jint∑isi1sip

  We illustrate this model in Fig.1A.

  We use a Monte-Carlo procedure to sample equilibrium configurations of this system (see Methods). We sample the long polymer through three elementary moves that add, delete, or ‘kink’ a given bond. We exchange bulk molecules with a particle reservoir and update their configuration with moves that conserve length.


### Thermodynamics of an Isolated Polymer —
  In the absence of the bulk system, the long polymer can access several thermodynamic phases. These phases correspond to distributions over the spatial configurations of the long polymer, {r→i}, where r→i is the position of the ith monomer. For idealized polymers in regions where boundary conditions can be neglected, these phases can be characterized by scaling relationships between Np and the radius of gyration Rg, defined by Rg2=1/Np∑iNp(r→i-r→cm)2 with r→cm the center of mass of the chain. We show sample configurations of these phases in Fig.1B

  When μp is negative and vp is positive or small and negative, the polymer is in the Short phase. Here Np is small, ≈ L. In our simulations we typically set μp = 0, and are not concerned with this Short phase.

  When vp is large and attractive, the polymer is in the Collapsed phase. Here Np fluctuates about Nmax, and typical configurations are space-filling, with a constant density as Nmax → ∞.

  When vp is large and repulsive, but μp is positive, the polymer is in the Extended phase. Here the length fluctuates about Nmax, but the polymer configuration is Extended and the average density of the polymer approaches 0 as Nmax approaches infinity.

  The Extended and Collapsed phase are separated by a line of continuous transitions at vp = 0. We show a typical Extended configuration in Fig.1B.


### Bulk Molecules Phase Separate and Modify the Polymer Phase Diagram —
  Our bulk system has phases and phase-transitions independent of its interactions with the long polymer. The bulk phases are dilute and dense corresponding to gas and liquid-like states. At certain chemical potentials, or densities, these bulk phases will coexist and the system phase-separates, drawn as the yellow region in Fig.2E, with typical configurations in each phase shown in Fig.1C.

  The polymer configurations in the Wet phase depend on Jint and Jbulk, which together determine solvent quality of the dense phase. A polymer that prefers to be Extended in an infinite bulk dense phase can be confined by a finite-size droplet separate from the collapse transition.

  Outside of the bulk coexistence region we find another phase where the polymer is Collapsed and also enriched with a dense-like phase of bulk molecules, shown in Fig.2B. This is reminiscent of prewetting where a thin bulk domain forms which is adhered to a particular surface phase [17, 19]; we call phases where polymer collapse coincides with polymer-only bulk de-mixing Generalized Prewet - Collapsed. Consistent with this view, the polymer phase-diagram effectively shifts and the collapse transition occurs at repulsive vp. Polymer collapse and bulk demixing couple because this minimizes the volume of an otherwise unfavorable bulk phase, while maintaining a high density of bulk-bulk and bulk-polymer interactions. Increasing μb, we transition discontinuously between the three phases shown in Fig.2A–C, which we draw schematically in the phase diagrams sketched in Fig.2E,F.


## MEAN-FIELD THEORY
  Here we develop a mean-field theory that couples a long, collapsible polymer to a bulk fluid with a propensity to phase-separate.


### Isolated polymer —
  We write the free energy of an isolated polymer chain, Fpoly0Rg, in terms of the order parameter Rg, and at fixed length Np:  (4) Fpoly0Rg=32Rg2Npa2-log⁡Rg2Npa2⏟Non-Interacting Polymer+vp2Np2a3Rg3+13!Np3a6Rg6⏟Interactions

  The first two terms labeled ‘Non-Interacting polymer’ are entropic contributions to the free-energy from gaussian statistics, and can be derived by replacing the radius of gyration with the end-to-end distance, with a the linear dimension of a single monomer. A free-energy written in terms of Rg has additional entropic costs due to confinement – but these, along with higher order interactions, are never relevant so we neglect them here (see Supplement). The final two terms capture mean-field interactions between monomers [21]. The parameter vp is the difference between monomer-monomer and monomer-solvent interactions. The point vp = 0 separates an Extended polymer phase, where the monomer density ρ = Na3/Rg3 approaches 0, from the Collapsed phase where ρ is finite, see the green line Fig.3B. This transition is continuous but sharp in the large Np limit [16, 22].


### Coupling Polymer to 3D Bulk —
  We employ a simple mean field theory for an order parameter ϕ which roughly describes the density of bulk phase separating components [23, 24]:  (5) fbulk=tb2ϕ2+u4!ϕ4-μbϕ

  Here tb corresponds to the reduced temperature, a measure of interaction strength between bulk molecules, μb is the chemical potential, and u captures higher order interactions and is required for stability.

  In a standard mean field approximation without a polymer, the order parameter is assumed to take the value ϕ∞ which globally minimizes the free energy density fbulk. In the presence of a long polymer, we further assume that a sphere of volume Rg3 has a polymer density ρ=Npa3Rg3 and a potentially different value of the order parameter ϕ. Here we assume that both order parameters, Rg (or equivalently ρ) and ϕ together minimize the free energy of the coupled system.

  We describe interactions between the bulk and the long polymer via an energy density fint and corresponding interaction energy Fint=fintRg3:  (6) Fint=-hϕNp

  The parameter h is analogous to Jint, and can be interpreted as a per monomer binding interaction between bulk and long polymer. To compactly write the coupled free energy of the polymer and its order parameter environment we define Δfbulk=fbulk(ϕ)-fbulkϕ∞ and write the free energy of the coupled system as:  (7) FsysRg,ϕ=Fpoly0Rg+FintRg,ϕ+Rg3Δfbulk(ϕ)

  where we have subtracted off a contribution from the polymer-free bulk.


### A super-critical bulk system modifies the polymer collapse transition —
  To see how the bulk modifies the thermodynamics of the long polymer, we examine the behavior of a weakly interacting bulk by approximating the free energy as quadratic, Δfbulk=tb2ϕ-ϕ∞2. In this approximation ϕ can be minimized analytically, leaving just one additional Rg dependent contribution to the effective free energy of an isolated polymer, so that FpolyeffRg=Fpoly0Rg-h2tbNpρ, and a constant term -hϕ∞Np. This additional term has exactly the same form as the monomer-monomer coupling, defining a new veff≡vp-h2tb. Thus, the effect of the bulk in this regime is precisely to shift the parameter regime of the collapse transition, see purple line in Fig.3A. The value of the bulk order parameter tracks with the density of the polymer and sees a sharp, continuous increase through the collapse transition, see Fig.3B, purple line.


### Strongly interacting bulk drives a first-order transition —
  In the limit where the bulk system is instead near to phase coexistence, when tb < 0 the bulk free energy density (equation 5) is not well described by a single quadratic minimum. Still, the order parameters Rg and ϕ take values which minimize the combined free energy Fsys (equation 7). Contour plots of Fsys are shown in Fig.3D,E (with ρ rather than Rg on the x axis), where there are two distinct minima. When the long polymer interacts more strongly with itself, (lower vp) there is an abrupt transition as one minimum becomes lower in free energy than the other. This leads to discontinuities in the polymer density (blue curve in Fig.3B) and in the bulk order parameter (blue curve in Fig.3C).

  To gain additional insight into the nature of this abrupt transition, we can also approximate the free energy as quadratic around both dense and dilute phase minima, treating each with the same approximation as above (orange and purple lines in Fig 3D,E left). This predicts that local minima will lie near the corresponding orange and purple lines in Fig 3D,E. In this approximation, the system takes the position of either the purple or orange dot, and a first order transition occurs when they have the same value of Fsys. Our simulations and theory show that ρ → 0 as μb → 0, corresponding to an Extended polymer wet by the bulk dense phase.

  Polymer collapse can only be accessed from the extended phase through a phase transition, either continuous or abrupt. Our simulations are in the abrupt regime, but the presence of a continuous transition above Tc, suggests that a generic phase diagram has the features plotted in figure 2E; a line of abrupt transitions in the dilute bulk phase but just outside of bulk coexistence, a line of continuous transitions at hight Tb and near the bulk dense phase, and a tricritical point where they meet. Near the bulk critical point but in the dense phase, a narrow region of prewetting can be accessed through a continuous transition by decreasing bulk density, and thereby increasing effective interactions. This is related to the phenomenon of polymer co-nonsolvency [25], in which a mixture of a good and bad solvent can induce polymer collapse more effectively than the bad solvent in isolation.


### Monte-Carlo simulations support theoretical predictions —
  Some predictions from our mean-field theory are testable in our Monte-Carlo simulations : (i) Is there a regime of continuous transitions at weak Jbulk? and a regime of discontinuous transitions at large Jbulk? (ii) Do interactions from the bulk solvent shift the collapse transition of the long polymer. We tested these predictions in a minimal Lattice Monte-Carlo Simulation (see Methods). Figure 4A demonstrates a regime where polymer and bulk density increase abruptly as μb increases for Jbulk >> 0 (blue line), and a regime where the densities continuously change for weaker Jbulk. (purple line). Likewise Figure 4B supports the ’shifting’ of the polymer collapse transition with solvent-mediated interactions. This shift can be continuous for weak coupling strengths (purple line) or discontinuous for stronger couplings (blue line).

  The discontinuities we predict will be blunted in finite-size systems. The sharpness of the prewetting-collapse transition is set by the contour length of the long polymer Np. While biological polymers are larger than most synthetic polymers, a direct mapping between our Np and monomer units in biological systems is unclear. Finite size bulk systems can also blunt these discontinuities but only through material depletion, an effect which we do not consider.


## MULTI-COMPONENT POLYMERS
  In many biological scenarios bulk proteins interact strongly with certain regions of the chromosome, and weakly or not at all with others. We modified our simulations by partitioning the long polymer into discrete segments that either interact with the bulk (yellow in Fig 5A) or do not (green in Fig 5A).

  Since the bulk interacts differently with the two monomer types, there are situations where strongly interacting segments collapse but non-interacting segments remain Extended. At low μb the polymer is Extended (Fig 5C) while at high μb all interacting segments form a globally Collapsed phase (Fig 5E). These phases differ in their occupation of bulk molecules and their polymer-polymer contacts. The Extended phase sees low occupancy of directly binding bulk molecules (red) at the yellow segments (Fig 5C, bottom) while both direct and indirect (blue) bulk molecules are enriched in the globally Collapsed phase (Fig 5E, bottom). The occupancy of yellow monomers increases discontinuously with μb while the green monomers remain mostly unoccupied (Fig 5B). When bulk molecules do not interact with each other, Jbulk = 0, the occupancy of yellow regions increases smoothly with μb (Fig 5B, diamonds), and there is no accompanying occupancy in indirect binders (Fig 5D, lower). Polymer-polymer contacts in the Extended phase are homogeneous, while the globally Collapsed phase sees long-range contacts between monomers of the same type, even those separated by an intervening sequence (Fig 5E,middle).


## DISCUSSION
  Here we have presented a model where a long polymer near a collapse transition couples to a bulk solvent near a de-mixing transition. We find that this coupling allows both polymer collapse and bulk demixing to occur well outside of their uncoupled phase boundaries. This is reminiscent of prewetting phase-transitions, where a boundary condensed phase is stabilized via interactions with a surface, sometimes undergoing its own transition [17, 19]. Here we discuss the ways biology could use these transitions, and further questions on their physics.


### Transcriptional activation through a prewetting transition —
  Transcription factors interact directly with enhancers, and many feature ‘activation domains’ that phase-separate with transcriptional machinery such as the co-activator Mediator [7, 26, 27], playing roles roughly analogous to the red and blue polymers in our simulations. These Prewet phases could naturally integrate information from transcription factor concentrations into transcriptional regulation by controlling where along the chromosome Prewet domains occur (Fig 5B). Transcription factor concentration could also modify how enhancers, promoters, and distant genomic regions interact in three dimensions, as in Fig 5E,F. The prewetting phase transition naturally integrates over a long stretch of chromosome, yielding an effective cooperativity in when and where domains appear, as may be relevant for transcription initiation [2, 3, 28, 29]. It is possible that heterochromatin is best thought of as a separate generalized Prewet phase, which excludes transcriptional machinery, and is rich in DNA and certain proteins. [8, 10, 30–32]


### The composition and genomic localization of Prewet domains can encode cellular identity —
  Cellular identity is thought to be encoded by core regulatory complexes (CoRCs) composed of a small number of transcription factors which regulate downstream cell-type specific genes [33, 34]. Evidence for these complexes comes, in part, from Chromatin Immuno-precipitation (ChIP-seq) studies [35]. Long stretches enriched in cell-type specific groups of a few transcription factors are often interpreted as arising from large, macromolecular complexes. But a generalized Prewet phase localized to certain genomic regions has a similar experimental signature, as Fig.5E (occupancy) illustrates. Molecules that do not bind directly to the polymer (blue) localize to the same region as molecules that interact directly (red) so long as both of these molecules phase-separate with each other. Many transcription factors that inspired this model for CoRCs phase-separate at high concentrations (OCT4, NANOG [26]), and are found as large, localized assemblies in some cell types. Prewet phases which depend on cellular identity may also explain cell type specific differences in the three-dimensional structure of chromatin (Fig.5E, polymer contacts).


### Phase diagrams for generalized Prewet phases —
  Past work has investigated how binary bulk mixtures can lead to polymer collapse even when either component on its own does not, a phenomena known as polymer-co-nonsolvency [25]. As in that work, far above the critical point in our more complicated bulk mixture, the transition from an Extended to a Collapsed state is continuous, though steep. Near the two phase coexistence region this transition becomes abrupt, as we see in simulations and mean-field theory 3A, compare blue and purple lines. This implies a tri-critical point which we have not thoroughly explored, near but outside of bulk coexistence, where the line of first-order prewetting transitions meets the line of second-order transitions. We also anticipate that the line of prewetting transitions meets bulk coexistence at another tricritical point, where Dry, Wet, and Prewet phases coexist. At these tricritical points the polymer likely sees non-trivial scaling behavior. We also expect interesting finite-size effects in the wetting regime when the length of the polymer is such that its Collapsed size is of order the size of the bulk domain. And finally, we anticipate coupling many-component bulk systems to a multi-component polymer will yield very rich physics [36].


### Our model differs from past models of phase separation and chromosomes —
  Recent work has investigated the role of polymer ‘scaffolds’ on the phase-separation of 3D proteins [11, 15, 37–40], and how 3D proteins mediate communication between distal genomic regions [9, 41, 42]. Others have observed that long polymers can widen regimes in which bulk proteins phase separate; here we expand on these observations by studying the thermodynamics of these transitions Our results are also related to a body of work investigating how demixing transitions interact with polymer meshes [43, 44], though most of that literature has focused on cytoskeletal meshes, which interact elastically, but do not contribute a transition of their own. There are regimes where demixing transitions can be enhanced or inhibited, and are generically accompanied by distortions of the polymer mesh. Here we innovate by jointly considering the polymer collapse transition and bulk condensation. Our work is also related to models of the ParABS system for chromosome segregation in bacteria, which explicitly describe the interactions of a dynamic polymer with interacting proteins, but do not focus on the phase behavior of their bulk system [45].


### Distinguishing prewetting from wetting —
  Although we focus on a region of prewetting phase transitions, our model features other transitions that resemble wetting, where a bulk phase prefers to localize to a surface [18]. Wet phases are stable even without a long polymer; while polymers can partition into them, the presence of a Wet phase does not imply presence of a specific polymer. As such, Wet phases are less suitable for regulation by controlling DNA’s interaction with specific components or its three dimensional structure. Overexpression of transcriptional activators quite generally inhibits transcription through a phenomenon dubbed ‘squelching’ [46]. It is possible that squelching marks a transition into bulk coexistence where macroscopic droplets compete with the DNA for transcriptional machinery. A complementary view is that chromatin-localized condensates serve as heterogeneous nucleation seeds for specific bulk phases [15]. We interpret these ’seeds’ as bona-fide prewet phases that may interplay with wet phases in genetic regulation.

  Eukaryotic cells have many surfaces with phase-transitions that do not occur in bulk, and biology often needs to localize processes to specific locations. We speculate that biology uses a variety of these generalized-prewetting transitions to accomplish specific localization, and to imbue a bulk fluid with properties such as a diverging susceptibility. Work by ourselves and others [11, 44, 47, 48] will continue to uncover the rich physics allowed by surface phase-transitions.


## MATERIALS & METHODS

### Simulation model
  We sample polymer configurations using a Monte-Carlo procedure [49] composed of three elementary moves that correspond to Addition, Deletion, and Kink of a given bond, where a bond is a link between successive monomers in the polymer, red in Fig 6 .Any move may be viewed as the translation of a bond in a direction orthogonal to the direction of the bond (arrows in 6). The type of move proposals available is completely determined by the vertices of two monomers neighboring the monomers participating in the bond. If translation of the bond gives no intersection with neighboring monomers, the move is Bond Addition and corresponds to adding two monomers to the chain. If the translated bond intersects with both monomers in the chain the corresponding move is Bond Removal and the polymer loses two monomers. If one of the neighboring monomers is intersected by the translated bond, the move is a Kink that does not change the length of the polymer, but alters the configuration. These moves are illustrated in Fig 6B.

  We simulate the polymer as follows: we randomly select a monomer, at position s, and define its bond as the vector between the monomer and the s + 1 monomer. We then calculate all bond translations and whether they correspond to addition, removal, or kink moves. We then randomly propose one of the three possible moves, with probabilities:  Padd(p)=Np+22*1+Np1-PkinkPrem(p)=Np2*1+Np1-PkinkPkink(p)=Pkink

  These are set to satisfy the detailed balance condition, that PaddNp=PremNp+2 and PremNp=PaddNp-2; since Pkink does not change the length of the polymer it can be held constant. After proposing a move we check for self-avoidance, and that the polymer meets the length constraint Np<Nmax, if either of these are not satisfied we reject the move. If the move is not rejected, we compute the total energy from Hpoly and accept with the Metropolis criteria Paccept=max1,e-βHpoly.


### Simulation of bulk system:
  Simulation of our bulk system closely follows the bulk system used in [17]. We simulate a two-component fluid of short polymers whose length Nb = 20 monomer units in all simulations. We update the position of a single bulk molecule via kink moves, which are analogous to those we propose in the long polymer. Bulk molecules also perform reptation moves where a monomer is removed from one end of the molecule and placed in a position adjacent to the monomer at the other end. These moves conserve length and are proposed randomly with uniform probability. Our bulk is typically held at fixed chemical potential. To this end we separately simulate a reservoir of non-interacting molecules and exchange particles with this reservoir with rate λ+=NrNr+Ns+1 and λ-=Ns+1Nr+Ns+1 to ensure detailed balance. Particle exchanges and moves are accepted with the Metropolis probability given by the bulk Hamiltonian.


### Multi-component polymers:
  Our simulations of polymers with multiple monomer types use the same move-set as the single-monomer simulations. We first equilibrate a single-monomer polymer for several million MCS, then impose monomer sequence on the polymer. We track the number of monomers per ‘segment’, and moves are allowed to change the monomers-per-segment up to ±Δ: i.e if we set a segment of 50 monomers of the same type, and Δ = 10, this segment must have 40– –60 monomers. We set Δ = 12 in all simulations displayed in Fig 5. Any move that brings the segment outside of this window is rejected. Otherwise the simulations are identical up the Hamiltonian, which now reflects the differences in binding to the bulk  (8) HintkBT=-Jint,1∑isi1sip1+Jint,2∑isi1sip2

  where, for example, Jint,1 denotes interactions of the first monomer type with the bulk, and sip,1 denotes the occupancy of the ith lattice site for monomers of type 1.

  textbfMinimal Monte-Carlo Simulation: To validate our mean-field theory, we simulated a simpler bulk system consisting of a single monomeric bulk species and long polymer. The long polymer’s Hamiltonian Hpoly and its interactions with the bulk Hint are unchanged, and we use a lattice-gas Hamiltonian for the bulk:  (9) HbulkkBT=-μb∑isi-Jbulk∑<i,j>sisj

  Here si spin variable represents the occupancy of the lattice at site ith for a bulk molecule, and Jbulk parameterizes a nearest neighbor interaction. Monte Carlo steps for the polymer are unchanged. We propose random flips of bulk spin variables, accepting or rejecting the move with the Metropolis probability.


### Code Availability:
  Source code for the Monte-Carlo Simulations is available on Github: https://github.com/SimludDalhec/PolymerCollapsePrewetting


## Acknowledgements —
  We thank Asheesh Momi, Yu Fu, Isabella Graf, and Simon Mochrie for feedback on the manuscript, and Pranav Kantroo, Martin Girard, Sarah Veatch, and Simon Mochrie for helpful discussions. This work was supported by NIH R35 GM138341 and NSF 1808551.