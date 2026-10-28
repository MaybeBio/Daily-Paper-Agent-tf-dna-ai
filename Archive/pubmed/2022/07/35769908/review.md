## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, conclusion, and supplementary figure/table references
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to the evidence presented, and clarity of presentation. No assessment of editorial fit or journal-specific policy matters
- **Shared manuscript claim summary** The authors use 500 ns molecular dynamics simulations to show that phosphorylation of Ser44 in DNA polymerase β, in the presence of Mg²⁺ ions, induces conformational transitions from a closed to an open state, driven by disruption of a key hydrogen bond (S44-E335) and formation of new salt bridges, with the dianionic phosphoserine (SP2) patch producing an open state and the monoanionic (SP1) patch producing an extended state
- **Visible evidence base** Main text figures 1-9, supplementary figures S1-S9, supplementary tables S1-S2, methods section describing simulation protocols, and results sections 3.1-3.6
- **Missing materials affecting confidence** The supplementary information is referenced but not provided in the submitted material. This includes supplementary figures S1-S9, supplementary tables S1-S2, and details of the dynamic cross-correlation and network centrality methods. Without these, several quantitative claims cannot be independently verified. Additionally, no simulation trajectory data, force field parameter files, or input structures are provided. The authors state that raw data will be made available upon request, but this is not verifiable from the current submission.

## Reviewer
- **Overall assessment** This manuscript presents a computational study of phosphorylation-induced conformational changes in DNA polymerase β using molecular dynamics simulations. The work extends a previous study by the same group (Homouz et al., 2018) by including Mg²⁺ ions, using longer simulation times, and employing additional analysis methods. The central claim, that Ser44 phosphorylation induces a closed-to-open conformational transition, is plausible and consistent with prior experimental observations of activity loss. However, the manuscript has several significant weaknesses. The simulation methodology, while standard, has limitations that are not adequately discussed, including the use of a single trajectory per system, the removal of DNA from the crystal structure, and the absence of enhanced sampling methods. The analysis of salt bridges and hydrogen bonds is presented descriptively without statistical rigor. The network centrality analysis is used to make claims about information pathways, but the connection between these computational metrics and functional outcomes is speculative. The comparison between SP1 and SP2 patches is interesting but the biological relevance of the SP1 patch is unclear, as the authors themselves note that SP2 is the accurate model for the experimentally phosphorylated residue. The manuscript would benefit from clearer presentation of methods, additional validation, and more cautious interpretation of the results.

- **Who would be interested in the results, and why** Researchers studying DNA polymerase β structure-function relationships, particularly those interested in post-translational regulation of DNA repair enzymes. The work may also be of interest to computational biologists studying phosphorylation-induced conformational changes in proteins and to those developing methods for analyzing allosteric communication in enzymes. The findings could have implications for understanding how phosphorylation regulates base excision repair, which is relevant to cancer biology and chemotherapy resistance.

- **Major Strengths**
  1. The study addresses a biologically important question: how phosphorylation regulates DNA polymerase β activity, which is relevant to DNA repair and cancer biology
  2. The inclusion of Mg²⁺ ions represents an improvement over the previous study and addresses a known gap in the modeling
  3. The use of multiple analysis methods (RMSD, Rg, RMSF, hydrogen bonding, salt bridge analysis, PCA, network centrality) provides a comprehensive characterization of the simulated systems
  4. The comparison between SP1 and SP2 phosphorylation patches provides insight into the role of charge in driving conformational changes
  5. The manuscript is generally well-written and the main text figures are clear and informative

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the simulations reveal the mechanism of phosphorylation-induced conformational transitions in DNA polymerase β, specifically that salt bridge formation and hydrogen bond disruption drive the closed-to-open transition
- **Evidence pointer** Section 3.1, Section 3.2, Figures 2-5, Supplementary Tables S1-S2, Supplementary Figures S1-S5
- **Concern** The study relies on a single 500 ns trajectory per system (WT, pS44 with SP2, pS44 with SP1). This is a fundamental limitation. Protein conformational transitions, particularly domain-scale movements such as those described here, typically occur on timescales of microseconds to milliseconds. A single 500 ns trajectory is unlikely to provide statistically converged sampling of the conformational ensemble. The authors do not provide any assessment of convergence, such as block averaging, multiple independent replicates, or comparison of structural properties across different time windows. The claim that the system "transits" from closed to open states based on a single trajectory is not statistically supported. The authors should either provide multiple independent simulations with demonstrated convergence, use enhanced sampling methods, or substantially temper their claims about the mechanism.
- **Why it matters** The central conclusion of the paper, that phosphorylation induces a specific conformational transition through specific molecular interactions, depends entirely on the statistical validity of the simulation sampling. Without evidence of convergence or replicate simulations, the observed differences between WT and pS44 could be due to insufficient sampling rather than genuine phosphorylation-induced effects.
- **Resolution test** Provide at least 3 independent replicate simulations per system and show that the key observables (RMSD distributions, salt bridge occupancies, hydrogen bond occupancies) are consistent across replicates. Alternatively, use enhanced sampling methods (e.g., metadynamics, umbrella sampling) to compute free energy surfaces along relevant reaction coordinates. Show that the free energy difference between closed and open states is statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the hydrogen bond between S44 and E335 is disrupted upon phosphorylation, with occupancy remaining 0.0 throughout the trajectory, and that this disruption is a key driver of conformational change
- **Evidence pointer** Section 3.1, Supplementary Table S1
- **Concern** The hydrogen bond analysis is presented in a binary manner: the S44-E335 hydrogen bond is either present (WT) or absent (pS44). However, the authors do not provide the distance and angle distributions for the S44-E335 interaction in either system. It is possible that in the WT system, the hydrogen bond is only transiently formed, or that in the pS44 system, the residues remain in close proximity but the geometric criteria for hydrogen bonding are not met due to the added phosphate group. The authors also do not report the occupancy of this hydrogen bond in the WT system, only stating that it is 0.0 for pS44. A more detailed analysis of the distance and angle distributions would strengthen the claim. Additionally, the authors state that the hydrogen bond is "responsible for stabilizing the enzyme in the closed state" based on crystal structures, but this is an inference from static structures and should be verified in the simulations.
- **Why it matters** The disruption of the S44-E335 hydrogen bond is presented as a primary mechanism for the conformational transition. If this hydrogen bond is not stably formed in the WT simulation, or if the disruption is not clearly associated with the conformational change, the mechanistic claim is weakened.
- **Resolution test** Provide distance and angle distributions for the S44-E335 interaction in both WT and pS44 systems. Report the hydrogen bond occupancy for the WT system. Show a time series of the S44-E335 distance alongside the RMSD or a relevant conformational coordinate to demonstrate temporal correlation between hydrogen bond disruption and conformational change.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the presence of Mg²⁺ ions plays a major role in facilitating the formation of new salt bridges (with K280 and R299) that drive the conformational transition, and that this represents a novel finding compared to their previous study without Mg²⁺
- **Evidence pointer** Section 3.2, Figure 5, Supplementary Tables S1-S2, Supplementary Figures S4-S5
- **Concern** The claim that Mg²⁺ ions play a major role in facilitating the new salt bridges is not directly supported by the data presented. The authors show that in the presence of Mg²⁺, salt bridges with K280 and R299 form, and that in the absence of Mg²⁺, a different set of salt bridges forms. However, they do not provide a mechanistic explanation for how Mg²⁺ facilitates the new salt bridges. The statement that Mg²⁺ "screens" the positive charge and thereby disrupts existing salt bridges is plausible but is not demonstrated with specific interaction analysis. The authors also do not compare the pS44 system without Mg²⁺ to the pS44 system with Mg²⁺ in terms of the conformational ensembles visited, so it is unclear whether the Mg²⁺-dependent salt bridges are actually associated with different conformational outcomes. The comparison to the previous study (Homouz et al., 2018) is mentioned but not systematically presented.
- **Why it matters** The role of Mg²⁺ is presented as a key advance of this study. If the specific mechanism by which Mg²⁺ influences the conformational transition is not clearly established, the novelty and importance of the work are diminished.
- **Resolution test** Provide a direct comparison of the pS44 system with and without Mg²⁺ using the same analysis methods. Show the time series of Mg²⁺-residue distances and correlate these with the formation of the new salt bridges. Provide a quantitative analysis of the electrostatic interactions involving Mg²⁺ and the relevant residues.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that network centrality analysis reveals that phosphorylation modulates the information pathway between the Lyase domain and base pair binding domain, and that residues with high betweenness centrality are functionally important
- **Evidence pointer** Section 3.5, Figure 9, Supplementary Figure S8
- **Concern** The network centrality analysis is presented with insufficient methodological detail. The authors state that the dynamic cross-correlation matrix is used to compute edge weights, but the specific criteria for edge inclusion, the threshold for the correlation coefficient, and the construction of the network are not described in the main text. The claim that residues with high betweenness centrality "could be assumed crucial for modulating the signal flow" is speculative. Betweenness centrality in correlation-based networks does not necessarily correspond to allosteric communication or functional importance. The authors do not validate their network analysis with any independent method, such as perturbation analysis or mutational studies. The threshold of C_B ≥ 0.15 appears arbitrary and is not justified.
- **Why it matters** The network analysis is used to support the claim that phosphorylation affects communication pathways in the enzyme. If the methodology is not transparent and the interpretation is not validated, this claim is not well-supported.
- **Resolution test** Provide a detailed description of the network construction, including the criteria for edge inclusion and the choice of thresholds. Validate the network analysis by comparing the identified residues with known functional residues from experimental studies. Use an independent method, such as community analysis or perturbation response scanning, to confirm the identified communication pathways.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the SP1 patch produces an extended state, in contrast to the open state produced by the SP2 patch, and that this difference provides insight into the role of charge in the conformational transition
- **Evidence pointer** Section 3.6, Supplementary Figure S9
- **Concern** The biological relevance of the SP1 patch is questionable. The authors state that SP2 is the accurate model for the experimentally phosphorylated residue, yet they devote a significant portion of the results to the SP1 patch. The claim that the SP1 patch produces an "extended state" is based on a single trajectory, and the structural characterization of this state is limited. The authors do not provide a clear explanation for why the SP1 patch produces a different outcome, beyond the difference in charge. The connection between the SP1 results and the biological function of DNA polymerase β is not established.
- **Why it matters** The SP1 results are presented as a significant finding, but if the SP1 patch is not biologically relevant, the extended state observation is of limited interest. The manuscript would be strengthened by a clearer justification for including the SP1 simulations and a more careful interpretation of their significance.
- **Resolution test** Provide a clear justification for the biological relevance of the SP1 patch. If the SP1 patch is not biologically relevant, present the SP1 results as a computational control or sensitivity analysis rather than a major finding. Provide a more detailed structural characterization of the extended state, including the specific domain rearrangements and the interactions that stabilize this state.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, Section 1
- **Evidence pointer** Section 1, paragraph 2
- **Issue** The introduction states that "DNA polymerase β′s 335 residue has two domains" which is confusingly worded. It should be "DNA polymerase β has 335 residues and two domains" or similar. The sentence structure is awkward and may confuse readers.
- **Required correction** Rewrite the sentence to clearly state the number of residues and the domain organization of DNA polymerase β.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The methods state that the Berendsen thermostat was used for temperature coupling and the Parrinello-Rahman barostat for pressure coupling. The Berendsen thermostat is known to not produce a correct canonical ensemble and is generally recommended only for equilibration. The Parrinello-Rahman barostat is appropriate for production runs. The authors should clarify whether the Berendsen thermostat was used during production or only during equilibration.
- **Required correction** Clarify which thermostat and barostat were used during the production phase. If the Berendsen thermostat was used during production, justify this choice or switch to a thermostat that produces the correct ensemble (e.g., Nosé-Hoover).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The methods state that the DNA was removed from the crystal structure, leaving only the protein. This is a significant modification of the biological system, as DNA polymerase β functions in complex with DNA. The authors should discuss the potential implications of removing DNA for the conformational behavior of the enzyme.
- **Required correction** Add a discussion of the limitations of simulating the apo protein and how this may affect the interpretation of the results in the context of the DNA-bound enzyme.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Section 2.2
- **Evidence pointer** Section 2.2
- **Issue** The hydrogen bond criteria are stated as a distance cutoff of 3.5 Å and an angle cutoff of 30 degrees. The angle definition is not specified (e.g., donor-H-acceptor angle vs. H-acceptor-acceptor-base angle). This should be clarified for reproducibility.
- **Required correction** Specify the exact geometric criteria used for hydrogen bond detection, including the definition of the angle.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, Section 3.1
- **Evidence pointer** Section 3.1, Figure 2
- **Issue** The RMSD distribution for pS44 shows two peaks, which the authors interpret as evidence of two conformational states. However, the authors do not provide the time series of RMSD to show whether the system transitions between these states or whether the two peaks correspond to different phases of the trajectory. This distinction is important for interpreting the dynamics.
- **Required correction** Provide the RMSD time series for both WT and pS44 to show the temporal behavior of the system and whether the two peaks in the pS44 distribution correspond to distinct conformational states visited at different times.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, Section 3.2
- **Evidence pointer** Section 3.2, Figure 5
- **Issue** The description of the correlation between the pS44-K280 distance and the pS44-E335 distance is unclear. The authors state that the pS44-K280 distance "correlates" with the pS44-E335 distance, but it is not clear whether this is a positive or negative correlation, and what the magnitude of the correlation is. The figure appears to show scatter plots, but the correlation coefficients are not reported.
- **Required correction** Report the correlation coefficients for the relationships shown in Figure 5 and clarify the direction of the correlations in the text.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, Section 3.5
- **Evidence pointer** Section 3.5, Figure 9
- **Issue** The authors state that residues with C_B values ≥ 0.15 were mapped onto the structure, and 14 residues were identified. However, the specific residues are not listed in the main text, and the figure may not clearly show all 14 residues. The authors should provide a list of these residues and their locations in the structure.
- **Required correction** Provide a list of the 14 residues identified by the betweenness centrality analysis, along with their domain locations and their potential functional significance.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract, last sentence
- **Issue** The abstract states that the phase space of structural transitions is "much richer" in the presence of Mg ions. This phrase is vague and not quantified. It would be more informative to state the specific differences observed in the presence versus absence of Mg ions.
- **Required correction** Replace the vague phrase with a specific description of the differences observed in the presence of Mg ions, such as the number of conformational states visited or the magnitude of structural changes.

## Risk / unsupported claims
1. The claim that the system "transits" from a closed to an open state is based on a single 500 ns trajectory per system and is not supported by evidence of convergence or statistical sampling. This is a central claim of the paper and is currently not well-established.
2. The claim that Mg²⁺ ions play a "major role" in facilitating the formation of new salt bridges is not directly demonstrated. The authors show correlations but do not provide a mechanistic explanation or direct evidence of Mg²⁺ involvement.
3. The claim that network centrality analysis reveals modulation of "information pathways" is speculative. The connection between betweenness centrality in correlation-based networks and functional communication pathways is not established.
4. The claim that the SP1 patch produces an "extended state" is based on a single trajectory and the biological relevance of this state is unclear.
5. The claim that the S44-E335 hydrogen bond is "responsible for stabilizing the enzyme in the closed state" is inferred from crystal structures and is not directly tested in the simulations.
6. The claim that the results "confirm" that phosphorylated serine 44 leads to significant conformational changes is overstated given the limitations of the simulation methodology.
7. The authors state that the results "agree with our previous study" but do not provide a systematic comparison of the two studies, making this claim difficult to evaluate.
8. The authors state that the hydrogen bond analysis "signifies the role of hydrogen bonds in opening up the structure" but do not provide a quantitative analysis of how hydrogen bond changes correlate with conformational changes over time.