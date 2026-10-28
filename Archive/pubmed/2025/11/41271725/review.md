## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information descriptions
- **Assessment boundary** Scientific validity, methodological rigor, mechanistic claims, and consistency with provided evidence; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics simulations with ATP-driven conformational switching to propose an asymmetric hand-over-hand mechanism for CMG helicase translocation along ssDNA, demonstrate dsDNA unwinding coupled to translocation, characterize distinct roles for RPA and Csm3/Tof1 in promoting processivity, and show that FACT facilitates nucleosome traversal while suppressing inappropriate histone transfer to the lagging strand
- **Visible evidence base** Main text figures 1-7, supplementary figures 1-7, supplementary movies 1-13, methods section, source data file
- **Missing materials affecting confidence** Source data file not provided; supplementary figures and movies not accessible; specific simulation parameters and validation metrics partially described but not fully quantified; no force field validation benchmarks shown; no error analysis for coarse-grained model limitations

## Reviewer
- **Overall assessment** This manuscript presents a substantial computational study addressing a fundamental question in eukaryotic DNA replication: how the CMG helicase achieves directional translocation and navigates nucleosomal barriers. The authors employ coarse-grained molecular dynamics simulations with a novel potential-switching scheme to model ATP-driven conformational changes, identifying four distinct DNA-binding states that enable asymmetric hand-over-hand translocation. The work integrates multiple replication factors (RPA, FPC, Ctf4, FACT) and provides mechanistic predictions that are experimentally testable. The study is ambitious in scope and addresses important gaps in our understanding of replisome function. However, several technical concerns regarding model validation, statistical robustness, and the interpretation of coarse-grained simulation results need to be addressed before the mechanistic claims can be fully established.

- **Who would be interested in the results, and why** Researchers in DNA replication, helicase mechanisms, chromatin biology, and computational biophysics would find this work relevant. The asymmetric hand-over-hand model provides a new framework for understanding CMG translocation that challenges the symmetric model derived from homo-hexameric helicases. The predictions regarding heterogeneous step sizes and the distinct roles of RPA versus Csm3/Tof1 are directly testable with single-molecule approaches. The nucleosome traversal mechanism and the proposed role of FACT in suppressing histone transfer to the lagging strand have implications for epigenetic inheritance. Computational biophysicists interested in coarse-grained modeling of large macromolecular complexes would also find the methodological approach of interest.

- **Major strengths**
  1. The study addresses a significant and timely question in eukaryotic DNA replication with a computationally ambitious approach
  2. The potential-switching scheme to mimic ATP-driven conformational changes is creative and represents a methodological advance
  3. The integration of multiple replication factors (RPA, FPC, Ctf4, FACT) into a single simulation framework is impressive
  4. The predictions regarding heterogeneous step sizes and distinct factor roles are experimentally testable
  5. The identification of a potential additional conformational state (State 4) based on cross-species structural data is thoughtful
  6. The nucleosome traversal simulations provide novel mechanistic insights into a poorly understood process

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the four-state switching scheme enables directional translocation and dsDNA unwinding, with 18/20 trajectories achieving approximately 12 nucleotides per cycle
- **Evidence pointer** Figure 2C-E, Supplementary Figure 1
- **Concern** The success rate of 18/20 trajectories achieving the expected 12-nt translocation is reported, but the criteria for defining "successful" translocation are not clearly specified. The manuscript does not report the distribution of translocation distances across all trajectories, nor does it provide statistical measures of variability beyond mean and standard deviation. More critically, the authors do not demonstrate that the observed translocation is robust to reasonable variations in simulation parameters, such as the switching interval, the strength of the potential-switching perturbation, or the specific choice of coarse-grained force field parameters. Without systematic parameter sensitivity analysis, it is difficult to assess whether the observed translocation is a robust property of the model or an artifact of specific parameter choices.
- **Why it matters** The central claim of the paper rests on the reliability of the simulation results. If the translocation behavior is highly sensitive to parameter choices, the mechanistic conclusions drawn from the simulations would not be robust. The lack of parameter sensitivity analysis undermines confidence in the predictive power of the model.
- **Resolution test** Provide systematic parameter sensitivity analysis showing that translocation efficiency and step-size distributions are robust to variations in switching intervals, potential strengths, and force field parameters. Report full distributions of translocation distances, not just means and standard deviations, and clearly define success criteria for translocation trajectories.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the coarse-grained model captures the essential physics of CMG translocation, including the asymmetric hand-over-hand mechanism
- **Evidence pointer** Methods section, Figure 1
- **Concern** The coarse-grained model uses a single bead per amino acid (AICG2+ model) and three beads per nucleotide (3SPN.2C model). While these models have been validated in previous studies for nucleosome dynamics, their applicability to a complex multi-subunit helicase with ATP-driven conformational changes is not well established. The manuscript does not provide validation of the model's ability to reproduce known biochemical or biophysical properties of CMG, such as translocation rates, processivity, or the effects of specific mutations. The potential-switching scheme introduces energy into the system in a way that may not accurately represent the free energy landscape of ATP hydrolysis. The authors address this concern with a control simulation, but the control only tests the effect of switching without hydrogen-bonding potential changes, not the broader question of whether the model accurately represents the energetics of the real system.
- **Why it matters** The mechanistic conclusions drawn from the simulations depend on the fidelity of the coarse-grained model. If the model does not accurately capture the energetics of CMG translocation, the proposed asymmetric hand-over-hand mechanism may not reflect the actual biological mechanism. The lack of validation against experimental data weakens the claim that the simulations provide mechanistic insights.
- **Resolution test** Provide additional validation of the coarse-grained model against experimental data, such as comparing simulated translocation rates or processivity with single-molecule measurements, or reproducing the effects of known mutations on CMG function. Alternatively, demonstrate that the model reproduces known structural or thermodynamic properties of CMG-DNA interactions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that Csm3/Tof1 grips the parental duplex to suppress backtracking, while RPA alleviates lagging-strand clogging, and that these distinct mechanisms are critical for processive unwinding
- **Evidence pointer** Figure 4, Supplementary Figures 4-5
- **Concern** The simulations show that RPA and Csm3/Tof1 improve translocation efficiency on different DNA sequences, but the mechanistic interpretation relies on indirect measures such as contact probabilities and minimum distances. The manuscript does not provide direct evidence for the proposed mechanisms, such as free energy calculations showing that Csm3/Tof1 binding to the parental duplex reduces the probability of backward steps, or that RPA binding prevents lagging-strand entry into the CMG pore. The claim that these factors act through "distinct mechanisms" is inferred from the observation that they have different effects on different sequences, but alternative explanations, such as non-specific stabilization of the fork structure, are not ruled out.
- **Why it matters** The proposed distinct mechanisms for RPA and Csm3/Tof1 are a key finding of the paper. If the mechanistic interpretation is not well-supported, the significance of the finding is diminished. The distinction between specific and non-specific effects is important for understanding how these factors actually function in the replisome.
- **Resolution test** Provide more direct evidence for the proposed mechanisms, such as free energy calculations, mutation analysis, or additional simulations that specifically test the proposed mechanisms. Rule out alternative explanations, such as non-specific stabilization of the fork structure, through appropriate control simulations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that nucleosomes positioned ≥22 bp downstream of the fork junction do not impede CMG translocation, but that progression becomes increasingly restricted as CMG approaches the dyad
- **Evidence pointer** Figures 5-6, Supplementary Figures 6-7
- **Concern** The nucleosome simulations are performed with CMG positioned at different initial locations relative to the nucleosome (SHL-7, SHL-5, SHL-4, SHL-3). However, the manuscript does not describe how these initial configurations were generated or whether they represent physiologically relevant encounter geometries. The observation that translocation efficiency decreases as CMG approaches the dyad is interpreted as evidence for a positional energy barrier, but the simulations do not directly measure the free energy barrier. The claim that Csm3/Tof1 promotes unwrapping via electrostatic interactions is based on simulations where these interactions were disabled, but the manuscript does not report whether this manipulation affects other aspects of the simulation, such as protein stability or DNA binding.
- **Why it matters** The nucleosome traversal mechanism is a significant contribution of the paper. If the initial configurations are not physiologically relevant or the interpretation of the energy barrier is not well-supported, the conclusions about nucleosome navigation may not be reliable. The role of Csm3/Tof1 in promoting unwrapping is a specific mechanistic claim that requires stronger evidence.
- **Resolution test** Provide more detail on how initial configurations were generated and justify their physiological relevance. Use free energy calculations or umbrella sampling to directly measure the energy barrier to CMG progression at different positions within the nucleosome. Provide additional controls to ensure that disabling electrostatic interactions does not have unintended effects on the simulation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that their findings support an asymmetric hand-over-hand mechanism and that this is consistent with biochemical evidence that not all Mcm subunits require ATPase activity
- **Evidence pointer** Discussion section, Figure 2
- **Concern** The manuscript discusses the asymmetric hand-over-hand model as an alternative to the symmetric model, but the relationship between the simulation results and the biochemical evidence is not fully developed. The authors state that "previous biochemical evidence demonstrating that not all Mcm2-7 ATPase subunits are essential for translocation supports the plausibility of an asymmetric hand-over-hand model," but this connection is not explained in detail. The simulations do not directly test the ATPase requirements of individual subunits, and the relationship between the four conformational states and the ATP hydrolysis cycle is not explicitly mapped.
- **Why it matters** The connection between the simulation results and experimental observations is important for establishing the biological relevance of the model. If the relationship between the simulated conformational states and the actual ATP hydrolysis cycle is not clear, the claim that the simulations support an asymmetric hand-over-hand mechanism is weakened.
- **Resolution test** Provide a more detailed discussion of how the four conformational states relate to the ATP hydrolysis cycle, and how the simulation results connect to the biochemical evidence regarding subunit-specific ATPase requirements. Consider performing simulations with specific ATPase-deficient mutants to directly test the model's predictions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section
- **Evidence pointer** Methods, "Molecular dynamics simulations with potential switching"
- **Issue** The description of the potential-switching scheme is somewhat brief. The manuscript states that "conformational changes of S. cerevisiae CMG associated with ATP hydrolysis and ADP-ATP exchange were modeled by sequentially switching the underlying energy potentials" but does not provide sufficient detail on how the switching is implemented, how the timing of switches is determined, or how the system responds to the switching events.
- **Required correction** Expand the methods description to provide more detail on the implementation of the potential-switching scheme, including how switching times are determined, how the system is equilibrated after each switch, and how the results depend on the switching protocol.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Figure 3
- **Evidence pointer** Figure 3D
- **Issue** The classification of trajectories into "forward," "backward," and "idling" categories is based on final displacement thresholds of ±3 nt. The choice of this threshold is not justified, and it is unclear how sensitive the results are to this choice.
- **Required correction** Justify the choice of threshold for trajectory classification and show that the main conclusions are robust to reasonable variations in this threshold.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph 4
- **Issue** The discussion of limitations contains a duplicated sentence: "the coarse-grained model simplifies ATP hydrolysis dynamics and protein-DNA interactions, potentially overlooking transient intermediates" appears twice in the same paragraph.
- **Required correction** Remove the duplicated sentence and ensure the limitations are discussed in a clear, organized manner.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section
- **Evidence pointer** Methods, "Coarse-grained molecular models"
- **Issue** The manuscript states that simulations were performed at 300 mM monovalent salt concentration, which is higher than physiological conditions. The justification for this choice is provided, but the manuscript does not discuss whether the results are sensitive to salt concentration.
- **Required correction** Discuss the potential sensitivity of the results to salt concentration and, if possible, perform simulations at lower salt concentrations to test the robustness of the findings.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 5
- **Evidence pointer** Figure 5C
- **Issue** The description of the nucleosome unwrapping dynamics in Figure 5C is somewhat difficult to follow. The figure shows time trajectories of unwrapping extent, but the relationship between the different panels and the main text description is not always clear.
- **Required correction** Improve the figure labeling and legend to make the relationship between the different panels and the main text description clearer.

## Risk / unsupported claims
- The claim that the four-state switching scheme represents the minimal set of conformational states required for efficient translocation is not directly tested; the authors did not systematically explore whether fewer states could also support translocation
- The claim that Csm3/Tof1 "grips" the parental duplex to suppress backtracking is inferred from contact probabilities and is not directly demonstrated through free energy calculations or perturbation analysis
- The claim that FACT "prevents inappropriate histone transfer to the lagging strand" is based on simulations where FACT was present or absent, but the manuscript does not provide a quantitative measure of histone transfer probability
- The claim that the simulations support an asymmetric hand-over-hand mechanism "consistent with biochemical observations" is not fully developed; the connection between the simulated conformational states and the ATP hydrolysis cycle is not explicitly mapped
- The physiological relevance of the initial simulation configurations for nucleosome encounter (SHL-7, SHL-5, SHL-4, SHL-3) is not fully justified
- The manuscript does not provide quantitative comparison between simulated translocation rates or processivity and experimental measurements, limiting the ability to assess the quantitative accuracy of the model