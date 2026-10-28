## Abstract

Transcription factors (TFs) regulate gene expression by interacting with specific DNA sequences in various manners, yet the mechanisms by which they dissociate from high-affinity DNA sites under physiological conditions remain not completely understood. Here, we employ continuous wave electron paramagnetic resonance (CW-EPR) spectroscopy in native solution state to resolve, with domain-level precision, the dissociation dynamics of the MYC-associated factor X (MAX) from its cognate EBOX DNA motif. Site-directed spin labeling reveals that in the absence of DNA, MAX undergoes a stepwise dissociation process—beginning with melting of the N-terminal disordered region (NTD), followed by the helix-loop-helix (HLH) domain, and culminating in leucine zipper (LZ) dimer dissociation. DNA binding reorganizes this process into a cooperative all-or-none transition, wherein destabilization of the LZ triggers concerted collapse of the entire trimeric MAX:MAX–DNA complex. Strikingly, the addition of a disordered BRCA1 fragment (residues 219–504) disrupts this cooperativity by selectively destabilizing DNA contacts in the NTD and HLH regions, without perturbing the LZ. This results in facilitated dissociation via competitive DNA binding, observed here directly at domain-level resolution. Our findings establish EPR spectroscopy as a uniquely sensitive tool for dissecting TF–DNA dynamics under physiological conditions, offering mechanistic insight into regulated unbinding processes inaccessible to ensemble methods.


## Introduction

Transcription factors (TFs) play central roles in regulating gene expression by targeting specific DNA motifs within chromatin 1 – 4 . MAX, the MYC-associated factor X, is a bHLH-LZ transcription factor that forms a homodimer in solution and recognizes the canonical enhancer box (EBOX) DNA element (CACGTG) in gene promoters. 5 – 9 Max is a key player in regulating the transcriptional machinery, being involved in the control of a plethora of MYC-regulated genes. Indeed, disruption of MAX function has been linked to numerous oncogenic processes. 6 , 10 , 11 While the thermodynamics and structural biology of MAX:MAX and MAX:MAX-DNA binding have been characterized, the kinetic and mechanistic basis of MAX binding to and dissociating from its cognate DNA remains poorly understood. In particular, it remains an open question of how TFs can execute their functions despite typically having nanomolar affinities to their cognate DNAs. 12 , 13

Facilitated dissociation—a mechanism wherein competitor proteins or nucleic acids actively promote TF release—has emerged as a plausible model for such regulation. 14 – 17 Recently, it was shown that MAX undergoes large-scale dynamic fluctuations, 15 which might underlie facilitated dissociation from or diffusion along DNA strands. However, direct domain-resolved experimental observations and descriptions of such events under near-physiological conditions have not yet been reported. Addressing this gap requires methodologies capable of resolving structural transitions in specific regions of a protein immediately as it dissociates from a DNA strand.

Here, we propose temperature-dependent continuous wave electron paramagnetic resonance (CW EPR) spectroscopy 18 – 25 as a technique to track local conformational changes within individual domains of MAX upon DNA dissociation. By site-directed spin labeling at selected positions 26 – 28 in the N-terminal DNA-binding domain, the helix-loop-helix motif, and the C-terminal leucine zipper, we map the domain-specific temperature-induced unfolding pathway of MAX via the stability of its individual components. We find that (i) the leucine zipper acts as a main anchor between both MAX strands and as a key stabilizing moiety, (ii) binding of cognate DNA to the N-terminal MAX domain stabilizes the homodimer leading to a cooperative DNA-MAX:MAX dissociation process, wherein the DNA-MAX and MAX-MAX interaction are simultaneously disrupted, (iii) the presence of the disordered BRCA1 fragment, housing its DNA-binding domain, promotes facilitated dissociation by destabilizing the DNA-bound form of MAX without perturbing the dimeric scaffold.

The sensitivity of EPR to changes in local spin label dynamics, combined with its applicability at near-physiological temperatures and concentrations 29 , 30 , thus offered us a unique window into protein-DNA interactions that are difficult to access by conventional methods. Together with complementary NMR data, this work provides a mechanistic framework for transcription factor unbinding and highlights the utility of EPR for detecting complex biomolecular dissociation events with site specificity.


## Results

The bHLH-LZ transcription factor MAX forms a characteristic homodimer, in which each monomer comprises an N-terminal intrinsically disordered domain (NTD) that binds to DNA double-strands, a helix-loop-helix (HLH) motif, and a C-terminal coiled-coil leucine zipper (LZ) responsible for dimerization 7 – 9 , 31 ( Fig. 1., A .). The NTD folds upon binding to DNA into another pair of helices embracing the nucleic acid ligand. 32 The homodimer exists in a dynamic equilibrium with its monomeric forms whereas low concentrations and high temperatures promote dissociation of the dimer 26 , 27 , 33 , giving rise to a heterogeneous conformational ensemble.

To probe the dissociation of the MAX:MAX-DNA complex, we conducted temperature-dependent CW EPR spectroscopy on MAX variants site-specifically labeled with MTSL at three mutated residues: R5C (NTD), G35C (loop of HLH), and R55C (LZ) ( Fig. 1., B .). These mutations do not perturb dimerization or ligand binding. 15 , 28

In the following, we will first describe our investigation of the neat MAX:MAX dimer to obtain reference data before moving on to the more complex MAX:MAX-DNA trimer. Finally, we will highlight how a competing BRCA1 ligand facilitates the dissociation process.


## Sequential unfolding of MAX

To probe the stability of the different motifs of the MAX:MAX dimer, we recorded temperature-dependent CW EPR data. The rationale behind this approach was to employ the dependence of MTSL CW EPR spectra on the rotational freedom of the spin label. Upon undergoing the well-documented temperature-induced transition of MAX from the rigid dimer to the dynamic intrinsically disordered state 13 , the MTSL labels were, thus, expected to lead to an abrupt change in EPR line shape.

At low temperatures (< 300 K), all EPR spectra of all three variants in the absence of DNA were well-described by a dominating single spectral component representing fast rotational motion with a rotational correlation time τ c of 0.89 ns, 1.82 ns, and 3.98 ns for R5C, G35C, and R55C, respectively. Additionally, small (<10%) contributions of an even faster species were found. These spectra are representative of the MAX:MAX dimer dominating the conformational space at low temperatures ( Fig. 1, C .).

Upon heating >300 K, a second, faster component suddenly emerged (as expected), increasing in population with temperature until it dominated the spectral signature ( Fig. 2, A and B .). This biphasic spectral evolution reflects a redistribution within the conformational ensemble toward states with greater local mobility. Spectral simulations confirmed that a two-component model with two distinct rotational correlation times provided a minimal and robust fit to the data. In contrast, single-component models failed to reproduce the observed features ( Fig. 2, C .).

To quantify the temperature-dependence, we fitted the weighted contributions of the two spectral components to sigmoidal functions ( Fig. 3 ) and extracted their inflection points. These correspond to the temperatures at which the fast and slow components become equally populated, i . e ., the cross-over point. The corresponding temperatures T c are shown in the bar chart in Fig. 4 and listed Table 1 .

We found that the NTD showed the lowest T c around 305 K, followed by the HLH domain at 310 K and the LZ at 322 K. These temperatures correspond to the stability of the different MAX domains. The unfolded NTD with the most significant conformational plasticity transitions first. This is followed by the HLH, recently shown to be involved in large-scale dynamic fluctuations 15 , albeit with a stable secondary structure; lastly, the rigid LZ transitions. Thus, intuitively, these temperatures were attributed to the unfolding/dissociation of the individual MAX domains.

However, it is important to note that the underlying molecular processes—monomer-dimer exchange and local temperature-dependent MTSL dynamics etc.—are more complex, and the EPR-detected population shifts should be interpreted as ensemble-averaged reporters of these composite motions.

Nonetheless, the ratio between the slower and the faster components changes upon the dissociation of the MAX:MAX dimer and the concomitant formation of an intrinsically disordered monomeric state. 27 Orthogonal NMR-based control experiments showed the same domain-specific destabilization patterns in the absence of spin labels, thereby ruling out label-induced artifacts or local probe dynamics as the primary cause of the observed temperature dependencies (Supporting Information Fig. S1).


## DNA Binding Shifts the Dissociation Profile of MAX Toward Cooperative Melting

We next compared these thermal profiles with data obtained in the presence of cognate DNA, the 5’-CACGTG-3’ enhancer box (EBOX) motif 6 , which has been known to bind the NTD of MAX efficiently. 15 ( Fig. 1., C . and Fig. 2, B .) Interestingly, for all three labeled positions, the equilibrium towards a faster motion was now found to be concerted at 322 K, corresponding to the cross-over point of the LZ label after DNA binding ( Fig. 3, B .). Thus, a delayed transition for the NTD and HLH labels was observed, consistent with enhanced structural stabilization by DNA binding. Notably, only above 320 K did the fast component dominate the spectra, suggesting a sharp, cooperative transition (Supporting Information Fig. S2 to S4). This behavior contrasts with the gradual domain-by-domain unfolding seen in DNA-free conditions.

For R5C, T c shifted from ~305 K (DNA-free) to ~323 K (DNA-bound) ( Fig. 4 ). G35C showed a more modest stabilization (312 K vs . 323 K), while R55C exhibited near-identical melting behavior in both conditions (~322 K), indicating that LZ stability is largely independent of DNA. These results align with the structural model in which DNA binding rigidifies the NTD and HLH but not the distal LZ domain. The simultaneous dissociation of all labels in the MAX:MAX–DNA trimer, thus, appears to be initiated by destabilization of the LZ, which causes the entire complex to disassemble.


## BRCA1 Facilitates Dissociation by Destabilizing the DNA-Bound Complex

To test whether MAX:MAX–DNA dissociation can be facilitated by a third partner, we introduced a BRCA1 fragment (residues 219–504), previously shown to bind the EBOX DNA motif. 34 Upon BRCA1 219–504 addition, we observed pronounced shifts in the EPR temperature profiles and T c , particularly for the R5C and G35C mutants ( Fig. 3, C ., and Fig. 4 ). The presence of BRCA1 reduced the DNA-induced stabilization effect: T c of R5C was elevated by ~8 K with EBOX DNA alone, but by only ~4 K when BRCA1 was also present. G35C exhibited a similar though less marked response. In contrast, R55C remained unaffected, suggesting that BRCA1 competes with MAX for DNA interaction rather than perturbing the LZ-mediated stability of the dimer.

These observations indicate that BRCA1 reduces the stabilizing influence of DNA on MAX, facilitating dissociation and allowing for earlier transitions into the dissociated states.


## Discussion

The T c values provide an avenue for a mechanistic understanding of the temperature- and ligand-dependent dissociation behavior of the MAX:MAX dimer, particularly within its trimeric DNA-bound complex. In the absence of DNA, dissociation follows a domain-specific and sequential pathway: the intrinsically disordered N-terminal domain (NTD) exhibits early melting, followed by unfolding of the helix-loop-helix (HLH) domain, and finally the leucine zipper (LZ), which anchors the dimer. This stepwise disengagement reveals a modular structural hierarchy, consistent with a model in which local conformational fluctuations initiate dissociation prior to complete complex breakdown.

Strikingly, when MAX is bound to its cognate EBOX DNA, this modular dissociation is no longer observed. Instead, all thermally induced conformational changes converge into a single cooperative transition temperature. Our data demonstrate that this unified ‘melting’ event is governed by destabilization of the LZ. Once this key dimerization interface begins to unfold, the entire MAX:MAX-DNA trimer collapses. The synchronicity of this transition underscores a highly cooperative unbinding mechanism in the DNA-bound state, in which destabilization of the LZ acts as the critical trigger for dissociation of the whole trimeric complex.

The introduction of BRCA1 219–504 destabilizes the MAX:MAX-DNA complex by competitively binding the DNA, effectively impairing the stabilizing influence of DNA on MAX dimer. As a result, domain-specific melting is present even in the presence of DNA, with early dissociation of the NTD and HLH domains preceding disruption of the LZ. This indicates that BRCA1 shifts the dissociation sequence such that DNA unbinding is facilitated before complete dissociation of the dimeric protein scaffold— evidence of facilitated dissociation.

The observed domain-resolved destabilization profile thereby provides direct evidence that BRCA1 facilitates transcription unbinding through a selective competition mechanism. Indeed, BRCA1 lowers the thermodynamic stability of DNA-bound MAX at the NTD and HLH regions, without perturbing the structural integrity of the LZ-mediated dimer. This implies that BRCA1 promotes MAX release from DNA by displacing it from the EBOX site, not by inducing dimer dissociation. Such domain-specific modulation is consistent with a facilitated dissociation mechanism and highlights the modularity of TF regulation.


## Conclusions

This study provides domain-resolved insights into the dissociation mechanism of the transcription factor MAX from its target DNA, revealing how the intrinsically disordered BRCA1 219–504 fragment facilitates unbinding via competitive destabilization. Using site-directed spin labeling and continuous wave EPR spectroscopy, we captured discrete thermal transitions in the N-terminal and HLH domains of MAX, while the leucine zipper remained stable—demonstrating a clear sequence of domain-specific dissociation steps.

Our findings show that DNA binding enforces a highly cooperative melting behavior in the MAX:MAX–DNA trimeric complex, where destabilization of the leucine zipper triggers simultaneous collapse of all domains. The addition of BRCA1 219–504 , however, disrupts this coupling: by binding to the EBOX motif, it selectively reduces DNA-induced stabilization of the N-terminal and HLH regions, thereby promoting MAX dissociation without dismantling the dimer. This is a hallmark of facilitated dissociation, directly observed here for the first time with domain-level precision.

Crucially, this mechanistic dissection would be inaccessible with conventional competition assays, circular dichroism, or ensemble-based thermodynamic methods, which report only averaged unfolding or binding behavior. EPR spectroscopy offers a suite of advantages: it is intrinsically local, highly sensitive to changes in molecular motion, and can be performed in native solution environments at temperatures close to physiological. This allows detection of subtle nanoscale changes in protein dynamics that precede or accompany macroscopic dissociation events—providing a level of spatial and kinetic resolution not achievable with other techniques.

Our work establishes EPR spectroscopy as a powerful platform for probing facilitated dissociation mechanisms in transcriptional regulators. These findings offer a model for BRCA1-mediated regulation in the MYC:MAX axis and highlight a broadly applicable strategy for studying competitive unbinding in disordered or conformationally heterogeneous systems.


## Materials and methods


## Protein expression and sample preparation

The his-tagged MAX, and BRCA1 DNA codifying sequences were inserted in the vector pET21(a)+ and employed for Rosetta 2 E. coli cells transformation. The transformed bacteria were grown at 37° C up to an absorbance of 0.6 at 600 nm, and then resuspended in M9 (with homogeneously 13 C labeled glucose 1 g/L and 15 N ammonium chloride 1 g/L). The protein expression was then triggered by the addition of IPTG and conducted overnight at 30° C. For the full protein purification of BRCA1 and MAX, we followed the procedures reported in 35 and 33 , respectively.

For the EPR experiments, we purchased three different pET21(a)+ vectors subcloned with the sequence codifying the three variants of MAX, R5C, G35C, and R55C. The expressed proteins were MTSL-tagged according to the reference 36 . MTSL-tagged MAX mutants were buffer exchanged against MES buffer. Labelling efficiency was always above 98% as probed by DTNB assays.

We purchased the CACGTG DNA filaments forming the EBOX double-strand from Eurofins Austria.


## EPR

The Continuous Wave (CW) X-Band measurements have been recorded using a Bruker ElexSys E500 instrument (9.34 GHz) equipped with a super-high Q resonator (ER4122SHQE-W1). Samples (20 μL) with a protein concentration of 100 μM were loaded into a microcapillary tube. All measurements were recorded with 100-kHz field modulation. The temperature-stabilized measurements were performed using a temperature controller (ER 4131 VT, Bruker). The spectra were recorded with 0.25 G modulation amplitude for measurements in the range 290 K – 335 K.

All the raw CW EPR spectra are reported in the Supporting information, from SI5 to SI13.

The home-written MATLAB routine (script) for fitting of the room temperature CW EPR spectra can be found in the Supporting Information as Script S1.


## Simulations and Data Fitting

The EPR spectra were simulated with a homemade MATLAB 2019a script implementing the “chili” function of the EasySpin 5.7.0 package.

At <300 K the EPR spectra were successfully simulated by a single spin system for all the three mutants. At temperatures > 300 K, a good description of the experimental profiles was obtained by overlapping two spin systems with different τ c , representing the slow-and fast-motion contributions. The weights and τ c obtained were varied during the fit of the spectra at different temperatures.

The weights of the slow and fast contributions over the temperature were then fitted in MATLAB with a sigmoidal function of equation: .


## NMR

The H N -CON experiments were performed on a 600 MHz Avance Neo Bruker spectrometer equipped with a Bruker Prodigy TCI cryo-probe.

All samples were prepared in 25 mM MES buffer at pH 5.5. 10% D 2 O was added as lock solvent.

For the H N -CON selective 1 H excitation and refocusing were achieved using PC9 37 (bandwidth 6.25 ppm, duration 2001 µs), and REBURP 38 (bandwidths 6.0-6.05 ppm, durations 1600-1614 µs) pulses, respectively. Selective proton pulses were centered at 8.3 ppm.

Selective 13 C excitation and refocusing were achieved using Q5 (bandwidth 136 ppm, duration 300 µs), and Q3 (bandwidth 115 ppm, duration 199 µs) pulses. 39 Selective 13 C pulses were centered at 173 and 54 ppm for CO and Cα, respectively. IPAP acquisition was used to suppress CO-Cα couplings during acquisition. Non-selective 15 N 90 ° pulse durations were 32 µs. the number of scans was 32, the recycle delay was increased to 1 s, and the number of t 1 increments collected was 256.

All the NMR analysis were performed using Topspin 4.0.7, CCPNMR and MATLAB R2019a. All data were apodized using 60° shifted sine bell functions before Fourier transform and baseline corrected using 5 th -order polynomials.


## Conflict of Interest

The authors declare no conflicts of interest.


## Acknowledgments

The authors acknowledge support from the NMR core facility of the Faculty of Chemistry, University Vienna. The project received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (Grant agreement 801936). For the EPR experiments financial support from the IR INFRANALYTICS FR2054 is gratefully acknowledged. The authors thanks H. Ahouari (Chevreul Institute, Villeneuve d’Ascq) for technical assistance in recording CW spectra and troubleshooting.


## Funder Information Declared