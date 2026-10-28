## Short Peptide Tails Modulate DNA Association and Condensation by PAMAM Dendrimers Journal: xxx

Poly(amidoamine) (PAMAM) dendrimers are promising candidates for nucleic acid delivery; however, biocompatibility and transfection efficiency remain a challenge. Here, we investigated how the composition of short peptide tails conjugated to generation 2 PAMAM (G2) dendrimers influence DNA association and condensation across a range of pH values. Using a combination of potentiometric titrations, DNA precipitation assays, and coarse-grained molecular simulations with charge regulation, we show that the ionization of G2 dendrimers is strongly affected by both pH and proximity to DNA. Although charge regulation enhances dendrimer protonation and strengthens DNA association at low pH, DNA condensation by unmodified G2 remains largely insensitive to pH within the studied range.

In contrast, conjugation of a single peptide tail introduces a pronounced pH dependence to DNA condensation. Histidine-containing conjugates exhibit the strongest response, with condensation efficiency decreasing markedly as the pH increases. Simulations reveal that the interaction strength between conjugates and DNA depends on both peptide composition and pH and that histidine-containing peptide tails become nearly neutral at physiological pH, contributing little to DNA binding. While single-conjugate simulations explain the trends in DNA association, they do not fully account for the observed condensation behavior, highlighting the importance of collective effects involving multiple conjugates.

Overall, peptide conjugation transforms G2 PAMAM dendrimers from relatively pH-insensitive DNA-condensing agents into pH-responsive DNA-binding systems. These findings provide molecular-level insight into the interplay between charge regulation, peptide composition, and DNA condensation.


## 1 Introduction

The therapeutic strategy of modulating genetic expression through the intracellular delivery of polynucleotides has gained significant importance in modern medicine. A wide range of delivery approaches has been developed to facilitate the transport of nucleic acids into cells. These strategies must address several critical challenges: protecting nucleic acids from enzymatic degradation, 30 enabling their passage across the cellular membrane and ensuring successful endosomal escape to reach intracellular targets. 44 Successful delivery systems must therefore be capable of overcoming these biological barriers to achieve therapeutic efficiency.

Among non-viral delivery systems, cationic lipids and polymers are commonly used due to their ability to complex with and condense nucleic acids. Cationic poly(amidoamine) PAMAM dendrimers are an example of such non-viral vectors that have been explored for nucleic acid delivery. 20 , 8 , 9 , 54 , 42 , 49 , 57 Their water solubility and high charge density enables strong interactions with DNA, leading to DNA condensation and the formation of dendriplexes. 9 , 17 , 1 , 18 Additionaly, the presence of amine groups renders PAMAM dendrimers sensitive to pH variations, which is advantageous for intracellular delivery. They are also considered biocompatible at low concentrations and low generation. 21 To further enhance their biocompatibility, targeting ability, and transfection efficiency, PAMAM dendrimers can also be functionalized with peptides 54 , 42 , 52 , 2 , 16 . In a previous study, we showed that the net charge of peptides conjugated to generation 2 PAMAM (G2) dendrimers influence their DNA complexation capacity, with fewer conjugates being required to achieve DNA condensation compared to unmodified G2, for positive peptides. 14

Typically, dendriplexes enter cells via endocytosis. As mentioned, one of the main challenges of nucleic acid delivery is the release of DNA from the endosomes into the cytosol, a process known as endosomal escape. As the endosomes mature into late endosomes and lysosomes, the pH decreases from approximately 7.4 to 6.2 (late endosome) and eventually to 4.7 (lysosome). 43 , 34 This acidification leads to the increased protonation of weakly basic groups, which is believed to trigger endosomal escape either by increasing osmotic pressure and causing membrane rupture (the proton sponge effect), 3 , 56 , 32 , 41 or by destabilizing the endosomal membrane through the formation of pores by highly (positively) charged molecules or complexes. 7 , 53 , 40 Both mechanisms facilitate the release of DNA or dendriplexes into the cytosol.

Therefore, the ability to modulate the charge of the dendrimers and dendriplexes in response to pH changes offers a promising strategy to enhance endosomal escape.

In this work, we investigate how the composition of short peptides conjugated to G2 PAMAM dendrimers influence DNA condensation across varying pH conditions. By combining in vitro assays with Langevin dynamics simulations, we show that peptide conjugation amplifies the pH-dependence effects G2 dendrimers on DNA condensation.


## 2 Materials and Methods


## 2.1 Materials

PAMAM dendrimers generation 2.0 with ethylenediamine cores (supplied as 20 wt% in methanol), phosphate buffered saline (PBS) tablets, dithiothreitol (DTT), sulfo-LC-SPDP, sodium acetate, acetic acid, and Trizma®base were purchased from Sigma-Aldrich/Merck. Spectrum TM Spectra/Por TM Biotech Cellulose Ester dialysis membrane tubing with a MWCO of 0.5 k 0.5\text{\,}\mathrm{k} was purchased from Thermo Fisher Scientific. Ultrapure water (resistivity 18.2 M ​ Ω cm 18.2\text{\,}\mathrm{M\SIUnitSymbolOhm}\text{\,}\mathrm{cm} , Milli-Q plus, Merck Millipore) was employed in the experiments.

DNA (gwiz-Luc plasmid , 6732bp) was obtained from Aldevron (Fargo, ND).

Custom-designed peptides were purchased from Genscript. The sequences, listed in the right-hand column of Table 1 , include a cysteine residue to facilitate conjugation. Peptides were dissolved in MilliQ water.

To investigate pH-dependent behavior, experiments were conducted using 10 mM 10\text{\,}\mathrm{mM} sodium acetate buffers at pH 4.3, 5.0 and 5.7, and 10 mM 10\text{\,}\mathrm{mM} Tris-HCl buffers at pH 7.1 and 8.2. All buffers were adjusted to an ionic strength of 16.9 mM 16.9\text{\,}\mathrm{mM} , using NaCl.


## 2.2 PAMAM-Peptide Conjugation

The conjugation of peptides to G2 PAMAM dendrimers was performed following protocols adapted from Santos et al. 42 and Waite et al. . 54 First, G2 dendrimers were air-dried to remove the methanol and then dissolved in 10 mM 10\text{\,}\mathrm{mM} PBS buffer. Sulfo-LC-SPDP was added to the dendrimer solution at a molar ratio 6:1 (sulfo-LC-SPDP:G2), and the mixture was stirred for 2.5 hours at room temperature to functionalize the dendrimers. Unreacted SPDP was removed by overnight dialysis against MilliQ water. The samples were then freeze-dried and eluted in 10 mM 10\text{\,}\mathrm{mM} PBS buffer.

The degree of SPDP functionalization was assessed using a DTT assay (described below). Peptides were then conjugated to the G2-SPDP complexes by adding them at a 1:1 molar ratio relative to the attached SPDP groups. The reaction was allowed to proceed overnight at room temperature.

To evaluate conjugation efficiency, DTT assays were performed both before and after peptide addition. Briefly, 10 µ ​ L 10\text{\,}\mathrm{\SIUnitSymbolMicro L} of a 15 mg mL − 1 15\text{\,}\mathrm{mg}\text{\,}{\mathrm{mL}}^{-1} DTT stock solution in PBS was added to 1 mL 1\text{\,}\mathrm{mL} of 0.01 mM 0.01\text{\,}\mathrm{mM} G2-SPDP or G2-peptide conjugate solution and incubated for 15 minutes at room temperature. The absorbance at 343 nm 343\text{\,}\mathrm{nm} , corresponding to pyridine 2-thione (a byproduct of the reaction), was measured using an Agilent 8453 UV/Vis spectrophotometer. This absorbance was used to calculate the average number of SPDP linkers and peptides per dendrimer. On average approximately two SPDP linkers and one peptide were conjugated per dendrimer for all peptide variants. Fig. 14 in A shows the pyridine-2-thione absorbance after addition of the linker and after conjugation with the different peptides.


## 2.3 Precipitation Assay

DNA condensation by G2 PAMAM dendrimers and PAMAM-peptide conjugates was assessed via precipitation assays at varying molar ratios ( r molar r_{\rm molar} ) and pH values. In each assay, 10 µ ​ L 10\text{\,}\mathrm{\SIUnitSymbolMicro L} of dendrimer or conjugate solutions, at varying concentrations, was added to 4 µ ​ L 4\text{\,}\mathrm{\SIUnitSymbolMicro L} of 0.5 g 0.5\text{\,}\mathrm{g} gwiz-Luc DNA in 86 µ ​ L 86\text{\,}\mathrm{\SIUnitSymbolMicro L} of buffer, resulting in a final DNA concentration of 0.02 g 0.02\text{\,}\mathrm{g} . The solution was gently pipetted to mix and incubated for 30 min 30\text{\,}\mathrm{min} at room temperature. Following equilibration, the samples were centrifuged at 3600 g g for 30 min 30\text{\,}\mathrm{min} . The absorbance of the supernatant at 260 nm 260\text{\,}\mathrm{nm} was measured using a NanoDrop Spectrophotometer to quantify unbound DNA.


## 2.4 Potentiometric Titration

Prior to titration, G2 dendrimers and G2-peptide conjugates were dialyzed overnight against pure MilliQ water using dialysis tubing with a MWCO of 0.5 k 0.5\text{\,}\mathrm{k} and freeze-dried. Peptides were delivered freeze-dried by the manufacturer. Potentiometric titrations of G2, peptides and G2-peptide conjugates were performed in 0.1 M 0.1\text{\,}\mathrm{M} aqueous HCl by incremental addition of 0.1 M 0.1\text{\,}\mathrm{M} NaOH until a stable pH value of 12 was reached. A waiting period was included between additions to allow the pH to stabilize. Titration curves were recorded at 23 °C 23\text{\,}\mathrm{\SIUnitSymbolCelsius} using a Metrohm 888 Titrado Compact titrator equipped with a Pt1000 temperature sensor and a LL Biotrode 3.0 mm glass electrode. Before each titration, a blank titration was performed under identical conditions using only 0.1 M 0.1\text{\,}\mathrm{M} aqueous HCl titrated with 0.1 M 0.1\text{\,}\mathrm{M} NaOH.

Details on the analysis and processing of the potentiometric titration data are provided in B .


## 2.5 Molecular modeling

To assess how DNA affects the ionization of G2 dendrimers and conjugates, a coarse-grained model that faithfully describes the structure and charge distribution of the double helix was used. First, an all atomistic, helical DNA structure with an arbitrary sequence was generated using UCSF Chimera. 35 The structure was then coarse grained with the model DNA spanning the entire box length to avoid end effects. In this representation, each base pair consists of three backbone beads, two for the deoxyribose sugar and one for the phosphate group, which carries a charge of − 1 -1 and has a radius of r phos = 2.9 Å r_{\text{phos}}=$2.9\text{\,}\mathrm{\text{Å}}$ . Purine bases (adenine and guanine) are modeled with four beads, while pyrimidine bases (cytosine and thymine) use three beads, each with a radius of r base = 3.35 Å r_{\text{base}}=$3.35\text{\,}\mathrm{\text{Å}}$ , matching the radius of the deoxyribose beads. All radii are derived from the van der Waals radii of the respective chemical groups. A rigid model was used, fixing the DNA particles in place and thus neglecting DNA bending in the presence of dendrimers. This assumption is justified, as the length of the model DNA in our system is well below the persistence length of DNA, even at high ionic strength. 29

The peptides were modeled using a bead-and-spring approach, with two beads per amino acid, one representing the backbone and the other the side chain. 28 Ionizable side chain beads, along with terminal groups, were assigned p K a K_{\text{a}} values based on experimentally determined data (see Table 2 ).

In the quasi-atomistic model of the dendrimer, each methyl and amide group was represented by a single, neutrally charged bead. Beads corresponding to tertiary amines (at the branching nodes) and primary amines (at the terminal positions) were modeled with ionizable states that could switch on and off. Their assigned p K a K_{\text{a}} values are also listed in Table 2 . All dendrimer beads were assigned a radius of r den = r_{\text{den}}= 1.5 Å 1.5\text{\,}\mathrm{\text{Å}} . The linker was modeled similarly, using 11 beads with r link, Me = r_{\text{link, Me}}= 1.54 Å 1.54\text{\,}\mathrm{\text{Å}} for the methyl groups and r link, C = r_{\text{link, C}}= 1.5 Å 1.5\text{\,}\mathrm{\text{Å}} for the other groups, as shown in Fig. 1 . Following the chemistry of the reaction, one primary amine of the dendrimer and the sulfur group of the peptide were considered non-ionizable in the conjugates. Fig. 1 illustrates the models of the dendrimer, linker and peptides and Fig. 2 shows a simulation snapshot of the G2-H4S5 conjugate interacting with the fixed DNA double helix.

The systems were studied by combining Langevin Dynamics (LD) simulations to probe the conformational evolution of the dendrimers, peptide, and dendrimer-peptide conjugates and a constant-pH (cpH) Monte Carlo procedure to account for the acid-base equilibrium of the ionizable groups. Each simulation was run for 7.5 × 10 4 7.5\times 10^{4} cycles. One simulation cycle consisted of 4000 LD integration steps, with a time step Δ ​ t = 0.005 ​ τ \Delta t=0.005\tau , followed by approximately 100 cpH titration attempts. The first 20% of each simulation was discarded as equilibration. Statistical uncertainty of the computed averages was estimated using the block analysis method. 22

The degree of ionization, α \alpha , was calculated as the ensemble average over the ionization states throughout the simulation. Potential of mean force plots were calculated using a weighted average umbrella sampling.

Full details on the simulation protocol and data processing are provided in the C .

The systems and acid-base reactions were set up using the pyMBE molecule builder 6 and the simulations were carried using the ESPReSso v4.2.1 simulation package. 55 All computational work was performed on the IDUN computing cluster at NTNU. 45


## 3 Results and Discussion

The validity of the ionization behavior of the G2 PAMAM model has been established previously. 11 Here the ionization behavior of the peptides is examined, along with the effect of pH on the individual interactions of G2 and peptides with DNA. Next, we extend the study to the titration and DNA binding of PAMAM-peptide conjugates. Lastly, we explore the condensation of DNA mediated by PAMAM-peptide conjugates at varying pH.


## 3.1 G2 PAMAM Dendrimers Condense DNA Independently of pH

Fig. 3 shows the impact of a DNA molecule on the ionization behavior of PAMAM dendrimers, as determined through molecular modeling. We focus on the pH range 5-7, which is particularly relevant for endosomal escape. As expected, the overall charge of the dendrimers decreases with increasing pH. Further, at all pH values studied, the dendrimer charge increases as it approaches the DNA. This effect, known as charge regulation, is most pronounced at pH 5. Similar charge regulations behavior has been previously observed in other polyelectrolyte systems. 36 , 27 , 47 , 51 , 38 , 31 , 5

Precipitation assays were performed to evaluate the interaction between G2 PAMAM dendrimers and DNA under varying buffer pH conditions (see Fig. 4 ). The results indicate no significant differences in DNA precipitation efficiency across the tested pH range, although a slight trend towards reduced condensation efficiency at higher pH values is observed. Nevertheless, a molar ratio of r mol > 800 r_{\rm mol}>800 is generally sufficient to induce DNA condensation. In a previous study, gel electrophoresis showed complex formation between G2 PAMAM dendrimers and DNA at approximately r mol = 400 r_{\text{mol}}=400 , while dye exclusion experiments revealed a reduction in normalized fluorescence intensity to 0.55 at r mol = 1550 r_{\text{mol}}=1550 , indicating substantial inhibition of dye binding to DNA. 14 Both precipitation assays and gel electrophoresis assess global condensation effects, involving multiple DNA strands, whereas dye exclusion probes more localized interactions between individual dendrimers and DNA. Therefore, the similarity in results between precipitation and gel electrophoresis is expected. The apparent pH-independence of DNA condensation may be attributed to the relatively high net charge of the dendrimers, which remains substantial even at high pH. As shown in Fig. 3 , simulation results reveal that although the total charge of G2 dendrimers decreases with increasing pH, the minimum charge remains at + 14 ​ e +14e , sufficient to drive DNA condensation.


## 3.2 Short Peptides are not Sufficiently Charged to Condense DNA

Similarly to G2 dendrimers, the ionization of the coarse-grained peptide models, described using a two-bead approach per amino-acids, 28 is found to be in good agreement with the potentiometric titrations, as shown in Fig. 5 . The peptide E4S1H4 shows the largest deviation between experiments and simulations, in pH range 3-5. At pH > 10 \text{pH}>10 the experimental results become less reliable, due to absorption of CO 2 \text{CO}_{2} , which explains the deviations at high pH values.

All titration curves show distinct regions of increased ionization from high to low pH, that align well with the known pK a {}_{\text{a}} values of the peptide residues. For example, H4S5 (orange circles in Fig. 5 ) shows a sharp increase in net charge around pH 6.3, corresponding to the pK a {}_{\text{a}} of histidine, followed by a more gradual increase near pH 8.35, which is consistent with the pK a {}_{\text{a}} of cysteine.

Fig. 5 also shows deviations between the analytical prediction based on the Henderson–Hasselbalch equation (Eq. 9 in B ) and the simulation and experimental data for peptides K4S5 and E4S1H4. These deviations occur due to the so-called polyelectrolyte effect, where ionization of individual monomers is suppressed due to electrostatic repulsion between the monomers. 39 , 50 , 10 This is especially evident in the simulation data of the E4S1H4 peptide (open yellow circles in Fig. 5 ) where the analytical prediction overestimates the (positive) charge at low pH values and overestimates the negative charge between pH 5 and 8, with the data crossing at pH 5, where the peptide is neutral.

The ability of the peptides to condense DNA was evaluated across the pH range 4-8, up to r mol = 1200 r_{\rm mol}=1200 . This corresponds to a charge ratio (N/P) of approximately 4, based on the peptides carrying a net charge of + 4 ​ e +4e , specifically H4S5 at pH 4 and K4S5 in the pH range 4-6.

Given the relatively low net charge and charge density of these peptides, even at acidic conditions, it is not surprising that no DNA condensation was observed up to r mol = 1200 r_{\rm mol}=1200 (Fig. 16 in D ). Higher concentrations of short polyelectrolytes are typically required to induce DNA condensation. 37 , 48 While the binding of short polyelectrolyte chains to DNA is thermodynamically favorable due to the counterion release, actual DNA condensation, driven by correlation effects and bridging interactions, 19 , 24 , 25 results in a reduction of the DNA’s conformational entropy and, to some extent, the translational entropy of the polycations along the DNA backbone. 15


## 3.3 G2 PAMAM-Peptide Conjugates Exhibit pH-Sensitive DNA Association

We now turn to the effect of pH on the interaction between G2 PAMAM-conjugates and DNA, beginning with an analysis of their ionization behavior. In Fig. 6 we compare the experimental titration data (full circles), simulation results (open circles), and analytical predictions. As observed for unmodified G2 PAMAM, the ionization of the amine groups in the conjugates is suppressed across most of the pH range when compared to the ideal behavior predicted by the Henderson-Hasselbalch equation. Interestingly, and in contrast to the behavior of the individual dendrimers and peptides, the potentiometric titration data show poor agreement with the simulation results.

Across all systems studied, the conjugates exhibit near-ideal ionization behavior under acidic conditions, with the simulations underestimating the net charge. However, in the pH range of 7 to 9.5, the experimental data reveal a pronounced suppression of charge relative to both simulations and analytical predictions.

The deviation observed between the experimental titration curves and simulations results may be attributed to the presence of multivalent phosphate ions originating from the phosphate buffer used during peptide conjugation. 31 P NMR analysis confirms that, despite extensive dialysis in pure water, the G2-peptide conjugate samples retained a non-negligible amount of phosphate ions, with P:conjugate molar ratios ranging from 12.7 12.7 to 44.5 44.5 depending on the conjugate (see Fig. 17 and Tables 4 and 5 in E ). Furthermore, experimental studies 23 and molecular modeling 11 have shown that phosphate ions accumulate around PAMAM dendrimers. Although the effect of phosphate binding on the ionization state of G2 is expected to be modest, it complicates the interpretation of the potentiometric titration data.

The presence of phosphates is also expected to affect the interactions of the conjugates with DNA. From an electrostatic perspective, the divalent phosphate ions are likely to be displaced from the G2-peptide conjugates upon association with DNA. However, the overall binding affinity may decrease because the pre-associated phosphate ions reduce the counterion-release entropy gain that normally accompanies complex formation. Since all the DNA binding experiments are conducted in a phosphate buffer, the influence of phosphate ions on the interaction with DNA does not contribute to the observed differences between the conjugates. While phosphate ions are not explicitly included in the simulations, the different observables investigated experimentally and computationally limit the comparison to qualitative trends.

Despite peptide modifications, all conjugates retain a substantial net charge in the pH range 5-7. At pH 7 it varies from approximately + 15 ​ e +15e for G2-K4S5 and G2-H4S5 (similar to unmodified G2) to around + 10 ​ e +10e for G2-E4S1H4.

As shown above for G2 PAMAM, the presence of DNA significantly affects the charge and ionization behavior of all titratable groups in the conjugates. The computed net charge of the conjugates as function of distance from the DNA center, across the pH range 5-7, is shown in Fig. 7 , alongside the corresponding data for G2. In all systems, the net charge increases as the conjugates approach the DNA. This effect is more pronounced at the lowest pH, where the difference in ionization between DNA-associated and free conjugates/dendrimers reaches approximately 10 ​ e 10e , or about 30% of the total charge.

The extension and nature of this charge modulation depend on the specific composition of each conjugate and can be rationalized by analyzing the ionization degrees of the various functional groups (Fig. 8 and Fig. 9 ). At pH 5 and 6, the increase in net charge of the conjugates upon DNA association is primarily driven by enhanced ionization ( α \alpha ) of the tertiary amine groups of G2, while the primary amines remain fully protonated regardless of their distance from DNA. At pH 7, DNA proximity induces only a modest increase in the ionization of tertiary amines, and guarantees full ionization of primary amines. Interestingly, in the G2-E4S1H4 conjugate, the primary amines are nearly fully ionized even at pH 7, and the tertiary amines exhibit slightly higher α \alpha even at greater distances from the DNA. This behavior is likely due to the glutamic acid residues in the peptides, which are fully deprotonated at pH 7 (Fig. 9 ), thereby enhancing the ionization of nearby (oppositely charged) amine groups.

Among the conjugates, G2-K4S5 shows the highest net charge across the studied pH range and distances from the DNA (red triangles in Fig. 7 ), as all lysine residues are fully protonated under these conditions. In contrast, G2-H4S5 shows a similar charge to G2-K4S5 at the lower pH values, but its net charge decreases at pH 7, due to the reduced ionization of the histidine residues (Fig. 9 ). Consequently, at pH 7, the overall charge of the G2-H4S5 resembles that of the unmodified G2 dendrimer.

The net charge of the G2-E4S1H4 conjugate is comparable to that of G2 at pH 5 (Fig. 7 ), due to a slight increase in amine group ionization (Fig. 8 ), combined with histidine ionization and reduced ionization of the glutamic acid residues (Fig. 9 ). As pH increases, the full ionization of glutamic acid residues and the decreasing ionization of histidines, result in a net charge that progressively falls below that of G2. Notably, the presence of the glutamic acid residues in G2-E4S1H4 appears to suppress histidine ionization, particularly near the DNA at higher pH. This is likely due to electrostatic repulsion between the negatively charged DNA and glutamic acid residues, which causes the peptide to extend away from the DNA, as illustrated in the representative snapshots in Fig. 10 . While at pH 5, the peptide occasionally interacts with the DNA, at pH 7 it is almost entirely protruding away from the DNA, reducing the influence of DNA-mediated charge regulation on the histidine residues.

Using computational modeling, we evaluated the potential of mean force (PMF) for the adsorption of G2 dendrimers and their peptide conjugates onto the DNA model.

As shown in Fig. 11 , both the net charge – modulated by pH and proximity to DNA – and the spatial distribution of charge within the condensing agents influence their association with DNA.

Focusing first on the unmodified G2 dendrimers (blue symbols), we observe that the depth of the PMF well decreases from − 64 ​ k B ​ T -64k_{\text{B}}T at pH 5 to − 39 ​ k B ​ T -39k_{\text{B}}T at pH 7, reflecting the reduced electrostatic attraction as the dendrimer becomes less charged. The G2-K4S5 conjugates (red symbols), which carry fully ionized lysine residues across the studied pH range, exhibit the strongest interaction with DNA. These conjugates display both deeper and broader potential wells, the latter attributed to the extended reach of the peptide chains, which enhance interactions even at relatively long distances.

Interestingly, both histidine-containing conjugates, G2-H4S5 and G2-E4S1H4, show similar PMF profiles near the DNA. At pH 5 and 6, their PMF curve falls between those of G2 and G2-K4S5, despite G2-E4S1H4 having a net charge similar to or lower than G2, and G2-H4S5 having a charge comparable to G2-K4S5. At pH 7, the PMFs of G2-H4S5 and G2-E4S1H4 converge with that of G2, even though G2-E4S1H4 has a lower net charge than both G2-H4S5 and G2. This suggests that at this pH, the peptides – being nearly neutral or negatively charged – do not significantly contribute to the association with DNA.

These findings are consistent with previous Monte Carlo simulations, which showed that neutral peptides do not significantly affect the binding of PAMAM-peptides conjugates to DNA. 14


## 3.4 G2 PAMAM-Peptide Conjugates Exhibit pH-Sensitive DNA Condensation

Unlike unmodified G2 PAMAM dendrimers, DNA condensation induced by G2-peptide conjugates exhibits a strong dependence on the pH of the buffer solution, as measured using a precipitation assay (Fig. 12 ).

Starting with G2-K4S5 (top panel in Fig. 12 ), it can be seen that the precipitation curve at pH 4 closely resembles that of G2 (Fig. 4 ), despite G2 having a lower net charge by approximately 4 ​ e 4e (Fig. 7 ), and a weaker interaction with DNA (Fig. 11 ). As the pH increases, the absorption of the supernatant at λ \lambda = 260 nm also increases, indicating a larger number of DNA molecules in solution after centrifugation. This trend is somewhat unexpected, given that G2-K4S5 maintains a relatively high net charge even at pH 7 – higher than G2, whose precipitation behavior remains largely unaffected by pH.

These findings can be compared to our previous work, where conjugation of peptides containing up to 12 lysine residues to G2, resulted in a reduced r mol r_{\rm mol} needed for DNA condensation at pH 7. 14 In that study, the peptides were shown to stretch along the DNA, occupying the space between the dendrimers. We speculate that while a single G2-K4S5 conjugate may enhance interaction due to its + 4 ​ e +4e charge, this effect diminishes when multiple conjugates are present. Electrostatic repulsion between dendrimers adsorbed onto the DNA, combined with the low charge of the peptides, may suppress lysine ionization and promote peptide desorption. The conjugation of neutral peptides to G2 has been shown to hinder DNA condensation. 14

Charge regulation is strongest near the pK a {}_{\text{a}} of the ionizable groups. Since lysine has a high pK a {}_{\text{a}} (10.4), the observed strong pH-dependence of G2-K4S5 precipitation in the pH 4-8 range may seem counterintuitive. However, this behavior is consistent with the idea that even small changes in local environment or conformation can significantly affect ionization and complex formation

The observed pH-dependent behavior is also very pronounced in the DNA–G2-H4S5 system, but shifted to higher r mol r_{\text{mol}} . Significant DNA condensation is observed at pH 5 and below, provided that the r mol r_{\text{mol}} is sufficiently high. However, condensation efficiency drops sharply at pH values near or above the pK a {}_{\text{a}} of histidine. An even stronger effect is observed for the G2-E4S1H4 system, fueled by the neutralized peptide at high pH values. It is however unclear why it shows a precipitation profile similar to G2-K4S5 at pH 4.

Fig. 13 summarizes the precipitation assay results for all systems at r m ​ o ​ l = 1200 r_{mol}=1200 . For reference, G2 at pH 7.0 has an average net charge of + 18 ​ e +18e (when adsorbed to DNA), corresponding to a N/P charge ratio of 1.6. As previously discussed, G2-induced DNA condensation is largely unaffected by pH at this concentration. In contrast, G2-K4S5 shows a gradual decrease in DNA condensation with increasing pH, with only ∼ \sim 50% of DNA excluded from solution at pH 8. The most pronounced pH dependence is observed for the histidine-containing conjugates, G2-H4S5 and G2-E4S1H4. At pH 4, nearly all DNA is condensed, while at pH 8, DNA remains fully in solution. This behavior aligns with the steep increase in net charge per conjugate as pH decreases from 8 to 4. In comparison, the charge increase for G2-K4S5 over the same pH range is much smaller, explaining the more moderate pH response.

To summarize, our previous work showed that conjugation of long, highly positively charged peptides to G2 PAMAM dendrimers reduces the amount of dendrimers required to induce DNA condensation. 14 In contrast, the present study shows that short peptides with relatively low net charge reduce the condensation efficiency. These findings indicate that peptide conjugation influences DNA condensation through mechanisms beyond a simple increase in the total positive charge of the carrier.

At the level of individual conjugates, the simulations reveal a strong dependence of DNA–conjugate association on both peptide composition and pH. However, these trends do not directly translate into the experimentally observed condensation behavior, highlighting the importance of collective many-body effects during DNA condensation, including interactions between multiple DNA-bound conjugates, charge regulation, and peptide conformational entropy.

Together, these results suggest that short peptide tails primarily regulate the interaction between PAMAM dendrimers and DNA, rather than merely contributing additional charge. Depending on their amino acid composition, the peptides modify the pH responsiveness of the conjugates, alter the spatial distribution of charge, and influence how neighboring conjugates can pack along the DNA molecule.

From a gene-delivery perspective, histidine-containing conjugates are of particular interest because their ionization changes substantially within the pH range encountered during endosomal maturation. The resulting increase in the charge of the DNA-conjugate complexes may enhance their interactions with negatively charged endosomal membranes, a mechanism that has been proposed to contribute to endosomal escape in polycation-based delivery systems. 12 At the same time, these conjugates were the least efficient DNA-condensing agents at neutral pH, highlighting a trade-off between endosomal responsiveness and nucleic-acid packaging efficiency. Interestingly, lysine-containing conjugates exhibited quantitatively similar pH-dependent changes in DNA condensation at low conjugate concentrations despite the much weaker pH dependence expected from the ionization state of the lysine residues.


## 4 Conclusions

We combined potentiometric titrations, DNA precipitation assays, and molecular simulations to investigate how the conjugation of short peptides affects the interaction of G2 PAMAM dendrimers with DNA.

The simulations show that the ionization state of G2 PAMAM dendrimers is strongly influenced by both pH and proximity to DNA. Charge regulation enhances dendrimer protonation near DNA, primarily through the tertiary amine groups, leading to stronger dendrimer–DNA interactions at lower pH. Despite these changes in interaction strength, DNA condensation induced by unmodified G2 PAMAM dendrimers was largely insensitive to pH within the investigated range, consistent with the dendrimers retaining a sufficiently high positive charge under all conditions studied.

The free peptides were found to be insufficiently charged to induce DNA condensation. In contrast, conjugation of a single peptide to G2 substantially altered the behavior of the dendrimers. All peptide-conjugated systems exhibited a pronounced pH dependence of DNA condensation, with condensation efficiency decreasing as the pH increased. This effect was strongest for the histidine-containing conjugates, whose net charge changes markedly within the physiologically relevant pH range.

Molecular simulations further revealed that the interaction strength between the conjugates and DNA depends strongly on both pH and peptide composition. At acidic pH, peptide-containing conjugates generally displayed stronger DNA association than unmodified G2. At neutral pH, however, conjugates containing histidine residues exhibited binding free-energy profiles similar to those of G2, indicating that the peptide tails become nearly neutral and contribute little to the interaction with DNA. Instead, the tails tend to extend away from the DNA surface and remain only weakly involved in binding.

The differences between the single-conjugate PMF calculations and the experimentally observed condensation behavior highlight the importance of collective many-body effects, including conjugate–conjugate repulsion, charge regulation, and peptide conformational entropy, during DNA condensation. Elucidating the role of these collective effects through simulations containing multiple conjugates is the focus of ongoing work.

In summary, conjugation of short peptide tails transforms G2 PAMAM dendrimers from relatively pH-insensitive DNA condensing agents into pH-responsive DNA-binding systems. These modifications increase the pH responsiveness of the conjugates and can lead to a substantial increase in complex charge within the pH range encountered during endosomal maturation, which may enhance interactions between DNA-conjugate complexes and negatively charged endosomal membranes. However, this gain is accompanied by a reduction in DNA condensation efficiency, highlighting a trade-off between endosomal responsiveness and nucleic-acid packaging when designing PAMAM-based gene delivery vectors.


## Acknowledgments

We would like to thank Marius Aarsten, Astrid Gaarder Harsheim and Tommy Duy Tran for their contribution to this work during their studies at NTNU. P.K. and R.S.D thank EEA and Norway grants (EHP11BFNU-OVNKM-4-215-01-2022). The authors acknowledge the computational resources from the High Performance Computing center IDUN at NTNU.


## References


## Appendix A Conjugation of PAMAM G2 and peptides

Fig. 14 shows the pyridine-2-thione absorbance at 343 nm measured before and after treatment with DTT. G2 refers to the G2 PAMAM dendrimers modified with a Sulfo-LC-SPDP linker.


## Appendix B Potentiometric titration


## B.1 Treatment of titration data

Potentiometric titration experiments evaluate the solution pH as a function of volume of the titrant (NaOH). To compare the titration data with the simulations and analytical predictions, the charge of the peptides and conjugates must be assessed as a function of pH.

First, the total charge of all molecules present in the solution Z tot Z_{\rm tot} needs to be estimated, with

where z OH − z^{\text{OH}^{-}} , z H + z^{\text{H}^{+}} , z Cl − z^{\text{Cl}^{-}} and z Na + z^{\text{Na}^{+}} are the total amount of charge due to protons, hydroxide, chloride anions and sodium cations, respectively.

The amount of charge due to protons and hydroxide can be calculated from the measured pH using

and

where c c is the reference concentration of 1 mol 1\text{\,}\mathrm{mol} , V tot V_{\rm tot} is the total volume of the solution (including the added titrant), and p ​ K w = log 10 ⁡ K w {\rm p}K_{w}=\log_{10}K_{w} is the self-ionization equilibrium constant of water. The number of charges due to the titrant NaOH and HCl stock are given by

and

where c NaOH c_{\text{NaOH}} and c HCl c_{\text{HCl}} are the concentration of the NaOH and HCl stock solutions respectively. V NaOH V_{\text{NaOH}} is the added volume of the titrant NaOH solution and V 0 V_{0} is the initial volume of HCl stock solution.

Since our samples are polydisperse and contain multiple polymeric units with different monomers (dendrimers with peptides attached), it is challenging to directly assess the charge of each molecule, or find reasonable monomeric units to calculate the charge per monomer, as has been shown to be efficient previously. 36

Due to the uncertainty of the size of each sample molecule and possible unaccounted charge Z extra Z_{\text{extra}} , the titration curves were anchored to the simulation data. The anchoring points were chosen to be the charge at pH 3 ( OPEN z sim , 3 ) z_{\text{sim},3}) and pH 10 ( OPEN z sim , 10 ) z_{\text{sim},10}) . The scaling factor was then calculated using

where z exp , 3 z_{\text{exp},3} and z exp , 10 z_{\text{exp},10} are the experimental charge at pH 3 and pH 10, respectively. The shift was then calculated by

The experimental charge values were then scaled and shifted using

where z z is the processed charge and z 0 z_{0} is the unshifted, measured charge at a given pH.

The potentiometric titration data was compared to the analytical solution calculated with the Hendersson-Hasselbach equation


## Appendix C Additional details on molecular simulations


## C.1 Potential energy of the system

The coarse-grained model includes bounded, steric, and electrostatic interactions. The total potential energy is expressed as

The monomers were bonded using a harmonic potential given by

with the stiffness constant k = 560 ​ k B ​ T / σ 2 k=560\,k_{\text{B}}T/\sigma^{2} and σ = 1.5 \sigma=1.5 Å. r 0 r_{0} refers to the equilibrium length, whose values for the different bonds in the models are shown in Table 3 , together with the bead diameters.

The DNA was represented as a stationary double helix with 6 turns. In addition, counter-ions were added to the system to ensure electroneutrality.

Steric non-bonded interactions between all beads (except between the fixed DNA beads) are modeled using a pairwise augmented Lennard–Jones (LJ) potential, 5

where r r is the center-to-center distance between particles i i and j j , σ \sigma defines the interaction range, ϵ \epsilon sets the energy scale, r c r_{\mathrm{c}} is the cutoff distance, and r off r_{\mathrm{off}} is a size-dependent offset. The constant

ensures continuity of the potential at the cutoff, with r cut = r c − r off r_{\mathrm{cut}}=r_{\mathrm{c}}-r_{\mathrm{off}} .

We set σ = 1 \sigma=1 for all particle pairs, such that the shape of the LJ interaction is independent of particle size. Differences in particle diameter are instead incorporated through the offset

where d i d_{i} and d j d_{j} are the diameters of the interacting particles. This construction ensures that the steric contact distance reflects the physical particle sizes. We further set r c = 2 1 / 6 ​ σ + r off r_{\mathrm{c}}=2^{1/6}\sigma+r_{\mathrm{off}} and ϵ = k B ​ T = 1 \epsilon=k_{\mathrm{B}}T=1 , which defines the unit of energy in the reduced-unit system. With this choice of parameters, Eq. 12 reduces to a purely repulsive Weeks–Chandler–Andersen (WCA) potential irrespective of particle size.

Electrostatic interactions were described using a screened Coulomb potential using a Debye-Hückel approximation,

where q i q_{i} is the charge of particle i i , ϵ 0 \epsilon_{0} and ϵ r \epsilon_{r} are the vacuum permittivity and relative permittivity respectively. The solvent is treated implicitly through the dielectric constant of water, ϵ r = 78.5 \epsilon_{\mathrm{r}}=78.5 , at T = 298.15 K T=$298.15\text{\,}\mathrm{K}$ . The cutoff was set to be half of the height of the box. The Debye length is given by

where I I is the ionic strength of the solution.

The ionic strength of the system was set to 17 mM 17\text{\,}\mathrm{mM} . The simulation box was setup with periodic boundary conditions in a square prism. The system’s energy was relaxed with 5000 steepest descent integrator steps to eliminate any overlap between particles.


## C.2 Langevin Dynamics

Configurational sampling was performed by integrating the Langevin equation of motion,

where m m and 𝐯 \mathbf{v} are the particle mass and velocity, respectively, γ \gamma is the damping (Stokes) coefficient, and 𝐔 ⁡ ( 𝐱 ) \mathbf{U}(\mathbf{x}) is the total potential energy arising from the molecular interactions described in Sec. C.1 . The thermal energy is given by k B ​ T k_{\mathrm{B}}T , where k B ​ T k_{\mathrm{B}}T is the Boltzmann constant and T T is the temperature.

The stochastic term 𝝃 \boldsymbol{\xi} represents Gaussian white noise originating from collisions with the implicit solvent and satisfies

where d = 3 d=3 is the dimensionality of the system, δ \delta is the Dirac delta function, and ⟨ ⋯ ⟩ \left<\cdots\right> denotes an ensemble average. Together, the dissipative and stochastic terms reproduce the Brownian motion of particles in an implicit solvent and ensure canonical sampling at equilibrium.

Simulations were performed in reduced units with thermal energy k B ​ T = ϵ = 1 k_{\mathrm{B}}T=\epsilon=1 , where ϵ \epsilon defines the unit of energy. The equations of motion were integrated using a Velocity–Verlet scheme with time step Δ ​ t = 0.005 ​ τ \Delta t=0.005\tau and damping coefficient γ = 10 ​ τ − 1 \gamma=10\,\tau^{-1} , where τ = σ ​ m / ϵ \tau=\sigma\sqrt{m/\epsilon} is the unit of time. These parameters were chosen to ensure stable and efficient sampling of configurational space. The particle mass was set to m = 1 m=1 , as it does not affect equilibrium thermodynamic properties.


## C.3 Constant pH Monte Carlo

Titration Monte Carlo moves in the constant-pH ensemble were used to simulate the dissociation reactions of weak acid and base groups, represented as

and

The MC steps involved the protonation or deprotonation of ionizable beads, while simultaneously inserting or deleting a counterion in order to assure electroneutrality. The probability of accepting such a MC trial move is given by 39

where Δ ​ U \Delta U is the change in potential energy, ζ = ± 1 \zeta=\pm 1 for the forward or reverse direction of the reaction, and p ​ K a = − log ⁡ K a {\rm p}K_{\rm a}=-\log K_{\rm a} .

Following the Addition of a Cation Procedure (ACP) 26 , protonation and deprotonation moves are coupled to the creation or deletion of a cation in order to preserve electroneutrality. The activity coefficient of the cation, γ Na + \gamma_{\mathrm{Na}^{+}} , is accounted for a posteriori by shifting the pH scale, according to 4

where p ​ γ Na + = − log ⁡ γ Na + {\rm p}\gamma_{\mathrm{Na}^{+}}=-\log\gamma_{\mathrm{Na}^{+}} . The activity coefficient is estimated using the semi-empirical Davies equation:

where A ≈ 0.509 A\approx 0.509 and C = 0.3 C=0.3 are empirical parameters for water at 298 K, I I is the ionic strength, and c ⊖ = 1 ​ mol ​ kg − 1 c^{\ominus}=1~\mathrm{mol\,kg^{-1}} is the standard concentration.


## C.4 Radial distribution function

Fig. 15 shows the radial distribution function of the central beads of the dendrimers in G2-H4S5 conjugates at pH 7 as a function of the distance from the DNA. After a larger peak, there is a depletion zone starting at approximately 5 nm 5\text{\,}\mathrm{nm} from the center of the DNA. The bulk concentration is reached at approximately 37 nm 37\text{\,}\mathrm{nm} . This simulation was used to verify that the simulation box was sufficiently large. In order to reduce computational costs, all other umbrella sampling was restricted to 6 nm 6\text{\,}\mathrm{nm} .


## C.5 Umbrella sampling

Umbrella sampling was used to calculate free energy profiles of the dendrimer and conjugates as a function of distance from the DNA.The core of the dendrimer was anchored to a phantom particle in the middle of the DNA using a harmonic potential

where η \eta is the reaction coordinate, η 0 \eta_{0} is the reference point, and k k is the strength of the potential that was set to k = 1 ​ k B ​ T / σ 2 k=1\,k_{\text{B}}T/\sigma^{2} . The movement of the anchored bead was constrained along the z z -direction to ensure that the calculated distance from the DNA remained perpendicular to its helical axis.

The weighted histogram analysis method (WHAM) 46 was used to calculate the radial distribution function and potential of mean force.


## Appendix D Precipitation Assay Peptides

Fig. 16 shows the results of the precipitation assay using K4S5 peptides at varying r mol r_{\text{mol}} and pH. No decrease in UV absorbance of free DNA is visible, independent of pH and r mol r_{\text{mol}} in the investigated range.


## Appendix E Phosphorus-31 NMR spectra


## E.1 NMR spectra

31 P NMR spectra confirming the presence of phosphorus in the three G2-peptide conjugate samples, and the 10 mM 10\text{\,}\mathrm{mM} PBS reference are shown in Fig. 17 .


## E.2 Quantification of phosphorus by 31 P NMR

The phosphorus concentration in each sample was determined by comparingthe 31 P NMR peak area to that of a 10 mM 10\text{\,}\mathrm{mM} PBS reference solution. Assuming a linear relationship between peak area and concentration, the phosphorus concentration in each sample was calculated as:

where C PBS = 10 mM C_{\mathrm{PBS}}=$10\text{\,}\mathrm{mM}$ , and A sample A_{\mathrm{sample}} and A PBS A_{\mathrm{PBS}} are the integrated peak areas of the sample and reference, respectively. The number of moles of phosphorus was obtained from the calculated concentration and the sample volume of approximately 0.6 mL 0.6\text{\,}\mathrm{mL} , according to

The integrated peak areas, calculated phosphorus concentrations, and molar amounts are summarized in Table 4 . The molar ratio between phosphorus and each G2-peptide conjugate is reported in Table 5 .