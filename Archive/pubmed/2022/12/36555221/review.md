## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, materials and methods, conclusions) without figures, schemes, tables, or supplementary materials
- **Assessment boundary** Computational chemistry and molecular dynamics study of a Pt(IV)-salphen complex: reduction mechanism by DFT and G-quadruplex binding by classical MD
- **Shared manuscript claim summary** The authors claim that (1) the Pt(IV)-Sal prodrug can be reduced by ascorbate and cysteine via inner-sphere mechanisms with low barriers, (2) outer-sphere reduction is also feasible based on calculated redox potential, and (3) the released Pt(II)-Sal binds c-myc G-quadruplex primarily via π-stacking, with enhanced affinity when protonated due to electrostatic and H-bonding interactions
- **Visible evidence base** Text descriptions of DFT free energy profiles (Figure 1), MD simulation results (Figures 2-4), binding free energy values (Table S2), H-bond data (Table S1), and methodological details in Section 3
- **Missing materials affecting confidence** All figures, schemes, tables, and supplementary materials (Figures S1-S6, Tables S1-S2, Movie S1) are not provided; experimental validation data referenced from prior work [19,20] are not included; force field parameter details for the Pt center are only partially described

## Reviewer
- **Overall assessment** This manuscript presents a computational investigation of a Pt(IV)-salphen prodrug reduction mechanism and the G-quadruplex binding of its Pt(II) reduction product. The DFT analysis of inner-sphere reduction pathways is systematic and follows established protocols from the authors' prior work. The MD simulations address an important question regarding the role of protonation state in G-quadruplex recognition. However, the manuscript has several significant issues. The comparison of calculated redox potential with experimental data is indirect and the interpretation is somewhat speculative. The MD binding free energy results show variability between simulations (from -11.8 to -17.1 kcal/mol) that is not adequately discussed. The claim that the complex "stabilizes" G-quadruplex DNA is not directly supported by the simulations, which only show binding modes and energies, not stabilization effects such as increased melting temperature. The manuscript would benefit from clearer presentation of the biological relevance and a more critical discussion of the limitations of the computational approach.

- **Who would be interested in the results, and why** Researchers in the fields of bioinorganic chemistry, anticancer drug design, and G-quadruplex-targeting therapeutics would find this work relevant. The study provides mechanistic insight into Pt(IV) prodrug activation and the molecular basis for G-quadruplex recognition by a metal complex, which could inform the design of more selective anticancer agents. Computational chemists working on metallodrug-DNA interactions may also find the methodological approach of interest.

- **Major strengths** The systematic exploration of multiple reduction pathways (inner-sphere mechanisms A, B, C and outer-sphere) is thorough. The use of a biologically relevant reductant (ascorbate) and a model sulfur-containing reductant (cysteine) is appropriate. The MD study comparing protonated and deprotonated forms of the Pt(II) complex provides useful insight into the role of charge in DNA binding. The long 1.5 μs unbiased MD simulation for binding site recognition is a notable effort that goes beyond typical docking-based approaches.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors state that the Pt(II)-Sal complex "stabilizes the G-quadruplex DNA" based on MD simulations showing binding modes and MM-GBSA binding free energies.
- **Evidence pointer** Section 2.2.1, Figures 2-3, Table S2
- **Concern** The simulations demonstrate that the Pt(II) complex binds to the G-quadruplex and provide binding free energy estimates, but they do not directly measure or compute stabilization of the G-quadruplex structure itself. Stabilization typically refers to an increase in thermal stability (e.g., elevated melting temperature) or a shift in the equilibrium toward the folded state. The MM-GBSA binding energy is a proxy for binding affinity, not for G-quadruplex stabilization. The authors use the term "stabilizes" in the abstract and conclusions without providing direct evidence for this specific claim.
- **Why it matters** The therapeutic relevance of G-quadruplex-binding ligands is predicated on their ability to stabilize these structures in cells, thereby disrupting telomere maintenance or oncogene expression. Overstating what the simulations show could mislead readers about the biological significance of the findings.
- **Resolution test** The authors should either (a) rephrase claims to state that the complex "binds to" or "associates with" the G-quadruplex with favorable computed free energies, or (b) provide additional computational evidence for stabilization, such as free energy calculations comparing folded versus unfolded states in the presence and absence of the ligand, or cite experimental data from prior work demonstrating stabilization.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The calculated redox potential of 0.162 eV for Pt(IV)-Sal is compared with the calculated value of 0.374 eV for cis-[PtCl4(NH3)2] and the experimental peak potential of -0.204 eV for the latter, leading the authors to conclude that Pt(IV)-Sal "may also be reduced following an outer-sphere mechanism."
- **Evidence pointer** Section 2.1.2, Scheme 3
- **Concern** The comparison between calculated standard reduction potentials and experimental peak potentials is problematic. Peak potentials from cyclic voltammetry are not directly comparable to standard reduction potentials, as they include kinetic contributions and are scan-rate dependent. The authors acknowledge this indirectly by noting that "peak potentials are significantly more negative than the normal potentials," but the argument that the calculated value of 0.162 eV "favorably compares" with the calculated value for the cisplatin derivative is not a validation of the method. The difference between the two calculated values (0.212 eV) is substantial, and the relationship between this difference and the experimental peak potential difference is not established. The conclusion that outer-sphere reduction is feasible is therefore weakly supported.
- **Why it matters** The claim that the prodrug can be reduced by both inner- and outer-sphere mechanisms is a central finding of the paper. If the outer-sphere pathway is not convincingly established, the mechanistic picture is incomplete and the relative importance of the two pathways cannot be assessed.
- **Resolution test** The authors should either (a) provide a more rigorous calibration of their computational protocol against a series of Pt(IV) complexes with known experimental reduction potentials, (b) compute the reduction potential using a more direct approach that accounts for the irreversibility of the process, or (c) temper the claim to state that outer-sphere reduction "may be possible" based on the calculated potential being within a reasonable range, without overinterpreting the comparison.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and methodological transparency
- **Claim pointer** The authors state that "the platinum metal center was parametrized (detailed information is reported in the SM)" and that MM-GBSA calculations were performed "evaluating the whole production trajectory over the last 150 ns of each dynamic."
- **Evidence pointer** Section 3, Materials and Methods
- **Concern** The description of the metal center parametrization is incomplete in the main text and the supplementary materials are not available for review. Critical details such as the choice of spin state, the treatment of the Pt(II) coordination geometry, the specific RESP charge fitting procedure, and the validation of the parameters against known structural or energetic data are not provided. Additionally, the MM-GBSA calculations are described as using "the whole production trajectory over the last 150 ns," but it is unclear whether this means a single trajectory or multiple snapshots, and whether entropic contributions were considered. The variability in binding free energies between MD1 (-11.8 kcal/mol) and MD1_rep (-13.2 kcal/mol) for the same protonation state suggests that the results may be sensitive to the initial conditions, and this is not discussed.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without complete parametrization details and a clear description of the analysis protocol, other researchers cannot reproduce or build upon these results. The observed variability between simulations also raises questions about the robustness of the conclusions.
- **Resolution test** The authors should provide complete details of the metal center parametrization in the main text or supplementary materials, including the RESP fitting procedure, the atom types and charges assigned, and any validation performed. They should also clarify the MM-GBSA protocol, including the number of snapshots used, whether entropic terms were included, and how the reported values were averaged. A discussion of the variability between MD1 and MD1_rep and its implications for the conclusions should be added.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance and context
- **Claim pointer** The authors state that "compounds capable of binding and stabilizing this type of DNA structure would be greatly beneficial in anticancer therapy" and imply that the studied Pt(II)-Sal complex is such a compound.
- **Evidence pointer** Introduction, Section 2.2
- **Concern** The manuscript does not provide any comparison with known G-quadruplex-binding metal complexes or organic ligands in terms of binding affinity or selectivity. The binding free energy of -11.8 to -17.1 kcal/mol is presented without context. How does this compare with established G-quadruplex ligands such as BRACO-19, TMPyP4, or other metal complexes? Is the binding selective for G-quadruplex over duplex DNA? These questions are not addressed, and without this context, the significance of the findings is difficult to assess.
- **Why it matters** The therapeutic potential of a G-quadruplex binder depends not only on its ability to bind but also on its selectivity and affinity relative to known compounds. Without comparative data or discussion, the novelty and potential utility of this specific complex remain unclear.
- **Resolution test** The authors should add a discussion comparing their computed binding affinities with experimental or computational values for known G-quadruplex ligands. If such data are not available, they should at least acknowledge this limitation and discuss the implications for the potential utility of the complex.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract and Conclusions
- **Evidence pointer** Abstract, Section 4
- **Issue** The abstract states that the Pt(II) complex "stabilizes the G-quadruplex DNA prevalently, either establishing π-stacking interactions with the terminal G-tetrad or through electrostatic interactions along with H-bonds formation." The word "prevalently" is awkward and the sentence structure is confusing. It is unclear whether the authors mean that the complex stabilizes the G-quadruplex predominantly through one of two alternative mechanisms depending on protonation state, or that both mechanisms contribute simultaneously.
- **Required correction** Rewrite the sentence for clarity, for example: "The results show that the Pt(IV) prodrug may be reduced by both inner- and outer-sphere mechanisms, and the active Pt(II) complex stabilizes the G-quadruplex DNA through π-stacking interactions with the terminal G-tetrad, with additional electrostatic interactions and H-bond formation when the complex is in its protonated state."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Section 2.1.2
- **Evidence pointer** Section 2.1.2, Scheme 3
- **Issue** The description of the outer-sphere reduction potential calculation is brief. The formula E° = -ΔG(sol) - Eref is given, but the solvation model, the treatment of the electron in solution, and the reference electrode details are not fully described. The value of 4.43 V for the absolute potential of SHE is stated, but the source of this value and its applicability to the computational protocol are not discussed.
- **Required correction** Provide additional details on the calculation of ΔG(sol), including the solvation model used, the treatment of the electron, and any corrections applied. Cite the source for the 4.43 V value and discuss its appropriateness for the computational method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** Section 2.2.1
- **Evidence pointer** Section 2.2.1, Figure 3
- **Issue** The authors state that "the distance between the Pt atom and the O6 carbonyl atoms of the four guanines of the terminal G-tetrad along the trajectories has been plotted in Figure 3." However, the figure is not available for review, and the text does not describe the key features of these distance plots. It is unclear whether the Pt atom remains consistently positioned over the center of the G-tetrad or whether it samples multiple positions.
- **Required correction** Add a brief description of the distance plots in the text, including the average distances and their fluctuations, to allow readers to assess the stability of the binding pose without needing to consult the figure.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 2.2.2
- **Evidence pointer** Section 2.2.2, Figure 4
- **Issue** The authors describe the 1.5 μs unbiased MD simulation as showing that the Pt(II)-SalH22+ complex "correctly recognize[s] and interact[s] with the binding site." However, the text notes that the initial interaction occurs with an adenine (DA12) and that the complex only reaches the terminal G-tetrad at approximately 1300 ns. This suggests a relatively slow recognition process, and it is unclear whether the complex would have remained bound if the simulation had been extended or whether the binding is kinetically accessible on biologically relevant timescales.
- **Required correction** Discuss the timescale of the recognition process and its biological relevance. If the complex requires over 1 μs to reach the binding site, this may have implications for its efficacy in a cellular context, where competing interactions and diffusion may limit the effective concentration at the target.

- **Technical failings that need to be addressed before the case is established** R1-M1 (stabilization claim not supported by the evidence), R1-M2 (weak comparison between calculated and experimental redox potentials), R1-M3 (incomplete methodological details for reproducibility)

- **Assessment against Nature-style criteria**
  - Originality: Moderate. The application of DFT to Pt(IV) reduction mechanisms is not new, and the authors have published similar analyses previously [27]. The MD study of G-quadruplex binding by a Pt(II)-salphen complex is a useful extension but does not represent a fundamentally new approach or concept.
  - Scientific importance: Moderate. The work addresses a relevant question in anticancer drug design, namely the mechanism of activation of Pt(IV) prodrugs and their interaction with non-canonical DNA structures. However, the findings are largely confirmatory of existing hypotheses and do not provide a major conceptual advance.
  - Interdisciplinary readership: Limited. The manuscript is written for a specialized audience of computational chemists and bioinorganic chemists. The biological implications are discussed only superficially, and the potential therapeutic relevance is not developed in a way that would engage a broader biomedical readership.
  - Technical soundness: The DFT calculations appear to follow established protocols, but the incomplete description of the metal center parametrization and the questionable comparison between calculated and experimental redox potentials are concerns. The MD simulations are described in reasonable detail, but the variability between simulations and the lack of convergence analysis are not addressed.
  - Readability for nonspecialists: The manuscript is written in a technical style that assumes familiarity with DFT, MD, and G-quadruplex biology. The introduction provides some context, but the results section is dense and would be challenging for readers outside the immediate field.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant topic and the computational approach is generally sound, but the claims regarding G-quadruplex stabilization and the outer-sphere reduction mechanism need to be either better supported or appropriately tempered. The methodological details must be completed to ensure reproducibility. If these issues are addressed, the manuscript could make a useful contribution to the field.

## Risk / unsupported claims
- The claim that the Pt(II)-Sal complex "stabilizes" G-quadruplex DNA is not directly supported by the MD simulations, which only demonstrate binding modes and computed binding free energies. Stabilization requires additional evidence, such as free energy calculations of the folded versus unfolded states or experimental thermal stability data.
- The conclusion that the Pt(IV)-Sal complex "may also be reduced following an outer-sphere mechanism" is based on a comparison between a calculated standard reduction potential and an experimental peak potential, which are not directly comparable. The argument is suggestive but not conclusive.
- The statement that the Pt(II)-SalH22+ complex "correctly recognize[s]" the binding site based on the 1.5 μs simulation implies a level of biological relevance that is not established, as the simulation represents a single trajectory under idealized conditions.
- The claim that the protonated form of the complex has higher affinity due to electrostatic interactions and H-bond formation is based on a comparison of MM-GBSA values from different simulations, but the variability between simulations (e.g., -11.8 vs. -13.2 kcal/mol for the same protonation state) is not discussed, and the statistical significance of the difference is not assessed.