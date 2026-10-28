## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text; no supplementary figures or tables were available for direct inspection
- **Shared manuscript claim summary** The authors combine molecular dynamics simulations and experimental biophysical measurements to show that eight directed-evolution mutations in the TadA-8e deaminase of the adenine base editor ABE8e enhance its DNA-binding affinity primarily through electrostatic interactions, and unexpectedly increase protein thermal stability by approximately 12°C, providing a mechanistic rationale for the higher editing activity of ABE8e compared to ABE7.10
- **Visible evidence base** MD simulation trajectories (~150 ns) of four full-length ABE models; MM/PBSA binding energy calculations; electrostatic surface potential analysis; microscale thermophoresis binding measurements; nanoDSF thermal shift assays
- **Missing materials affecting confidence** Supplementary figures (Fig. S1–S4), tables (Table S1–S2), and movies (S1–S2) referenced in the text were not provided; full MD trajectory data and convergence analyses not shown; raw MST binding curves and nanoDSF melting profiles not shown; no statistical analysis details for replicate measurements

## Reviewer
- **Overall assessment** This manuscript addresses a relevant question in base editor engineering: how directed-evolution mutations in TadA-8e enhance the editing activity of ABE8e. The authors combine computational and experimental approaches to propose that enhanced DNA-binding affinity, driven by electrostatic interactions, and improved protein stability underlie the activity gain. The topic is of interest to the genome editing community, and the combination of MD simulations with biophysical measurements is appropriate. However, several technical concerns limit the strength of the conclusions as currently presented. The MD simulation times are relatively short for drawing robust conclusions about binding affinity differences, the MM/PBSA calculations rely on a single trajectory per system without error estimates, the electrostatic surface analysis is qualitative, and the experimental validation is limited to two biophysical measurements without direct functional assays linking the proposed mechanisms to editing activity. The claim that DNA-binding affinity and protein stability are "closely related" to editing activity is not directly tested. The manuscript would benefit from additional replicates, convergence analyses, and functional experiments to establish causality.

- **Who would be interested in the results, and why** Researchers in genome editing, protein engineering, and base editor development would be interested. The findings could inform rational design of improved adenine base editors, which are widely used in research and therapeutic applications. The study also contributes to understanding how directed evolution optimizes enzyme function through combined effects on substrate binding and stability, which is relevant to the broader protein engineering community.

- **Major strengths** The study addresses a mechanistically important question with practical implications for base editor optimization. The combination of computational predictions with experimental biophysical validation is a sound overall strategy. The identification of R111 as a key residue for DNA binding provides a testable and mechanistically plausible explanation for previously observed experimental results. The unexpected finding of improved thermal stability adds a new dimension to understanding the effects of directed-evolution mutations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of computational methods
- **Claim pointer** The authors claim that MD simulations show TadA-8e has higher DNA-binding affinity than TadA-7.10, and that electrostatic interactions are the main driving force.
- **Evidence pointer** Results section "TadA-8e has higher DNA-binding affinity"; Table 1; Methods section "MD simulations"
- **Concern** The MD simulations are only ~150 ns per system, with equilibration assessed by RMSD stabilization after ~110 ns. This leaves only ~40 ns of production data for analysis. For protein-DNA binding affinity calculations using MM/PBSA, this is a very short timescale. The MM/PBSA calculations use only 41 snapshots from a 40 ns window, which is unlikely to provide converged or statistically robust binding energy estimates. No error bars, standard deviations, or block averaging are reported for the binding energies. Additionally, only a single trajectory per system was analyzed, making it impossible to assess run-to-run variability. The use of a single dielectric constant value (6) for the detailed per-residue analysis, while four values are shown in Table 1, raises questions about the sensitivity of the conclusions to this parameter.
- **Why it matters** The central claim that TadA-8e has higher DNA-binding affinity than TadA-7.10 rests on these MM/PBSA calculations. If the calculations are not converged or are highly sensitive to simulation length or dielectric constant, the conclusion may not be robust. The lack of error estimates prevents assessment of whether the reported differences are statistically meaningful.
- **Resolution test** Provide multiple independent MD trajectories (at least 3 per system) with longer simulation times (500 ns or more), show convergence of binding energy estimates over time, report standard errors or confidence intervals for MM/PBSA energies, and demonstrate that the relative ordering of binding affinities is consistent across different dielectric constants and analysis windows.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation and causal link
- **Claim pointer** The authors claim that "the editing activities of ABEs are closely related to their DNA-binding affinity and protein stability," implying a causal or mechanistic relationship.
- **Evidence pointer** Abstract; Discussion section
- **Concern** The experimental data consist of MST binding measurements and nanoDSF thermal stability measurements on isolated TadA proteins. No functional editing activity assays are performed in this study. The connection between the measured biophysical properties (binding affinity, thermal stability) and the actual base editing activity of ABE8e versus ABE7.10 is inferred from prior literature, not demonstrated here. The authors do not test whether mutations that alter binding affinity or stability in predictable ways correspondingly alter editing activity. The statement that editing activity is "closely related" to these properties is therefore an extrapolation beyond the data presented.
- **Why it matters** The title and abstract imply that the identified biophysical changes explain the enhanced editing activity of ABE8e. Without direct functional data linking the proposed mechanisms to editing outcomes, the causal claim is not established. The manuscript would be substantially strengthened by including editing activity measurements for ABE8e, ABE7.10, and relevant mutants.
- **Resolution test** Include cellular or biochemical base editing activity assays comparing ABE8e, ABE7.10, and mutants with altered binding or stability (e.g., R111 back-mutant, D119N/D167N variants) to demonstrate that changes in binding affinity and stability correlate with changes in editing activity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural model construction and validation
- **Claim pointer** The authors constructed full-length models of ABE8e and ABE7.10 based on the cryo-EM structure 6VPC, including homology modeling of missing loops and the 32-aa linker.
- **Evidence pointer** Methods section "Structure construction"; Results section "MD simulations of full-length ABEs"
- **Concern** The cryo-EM structure 6VPC has missing regions that were modeled using SWISS-MODEL. The accuracy of these modeled regions, particularly the 32-aa linker between Cas9n and TadA-8e, could significantly affect the simulation results. No validation of the modeled structures is provided (e.g., Ramachandran plots, comparison with known structures, or assessment of model confidence). The TadA-7.10 structure was generated by introducing point mutations into the TadA-8e structure, which assumes that the backbone conformation is identical between the two variants. This may not be valid if the mutations induce conformational changes.
- **Why it matters** The conclusions about binding affinity differences between TadA-8e and TadA-7.10 depend on the accuracy of the structural models. If the modeled regions are incorrect or the TadA-7.10 structure is not representative, the calculated binding energy differences could be artifacts of the model rather than real biophysical differences.
- **Resolution test** Provide validation of the modeled structures, such as comparison with available crystal structures of TadA variants, assessment of model quality metrics, or additional simulations starting from alternative model constructions to test robustness of conclusions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of electrostatic surface analysis
- **Claim pointer** The authors claim that the positive charge density and area on the surface of TadA-8e are higher and larger than those in TadA-7.10, and that this explains the enhanced DNA binding.
- **Evidence pointer** Results section "Electrostatic attractions improve DNA-binding ability of TadA-8e"; Figure 4
- **Concern** The electrostatic surface potential analysis is qualitative and descriptive. The authors state that the positive charge density is "higher and larger" but provide no quantitative measure of surface charge distribution or statistical comparison. The claim that the "negatively charged area of the active site is over-exposed" in TadA-7.10 is not quantified. The relationship between the observed surface potential differences and the calculated binding energy differences is not systematically established.
- **Why it matters** The electrostatic mechanism is a central part of the proposed explanation. Without quantitative analysis, the visual interpretation of surface potentials could be subjective and may not reliably support the mechanistic conclusion.
- **Resolution test** Provide quantitative measures of surface electrostatic potential, such as integrated positive potential over the DNA-binding region, comparison of charge distributions between the two variants, and correlation analysis between per-residue electrostatic contributions and binding energy differences.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** MST binding measurements
- **Evidence pointer** Results section "Electrostatic attractions improve DNA-binding ability of TadA-8e"; Figure 5C
- **Issue** The MST measurements report Kd values with standard deviations (113.40 ± 0.57 nM and 62.10 ± 0.13 nM), but the number of independent replicates is not stated. The very small standard deviations relative to the Kd values suggest high precision, but it is unclear whether these represent technical replicates from a single experiment or biological replicates from independent protein preparations.
- **Required correction** State the number of independent experiments and whether the reported errors represent technical or biological variation. Provide details on how the Kd values were calculated and fitted.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental conditions
- **Affected element** MST binding buffer
- **Evidence pointer** Methods section "Microscale thermophoresis (MST)"
- **Issue** The binding buffer contains 150 mM KCl and 10 mM MgCl2. The ionic conditions can significantly affect electrostatic interactions between proteins and DNA. It is unclear whether the binding affinity differences observed between TadA-7.10 and TadA-8e are specific to these conditions or would be observed under other physiologically relevant conditions.
- **Required correction** Discuss the choice of buffer conditions and whether the conclusions are expected to hold under different ionic strengths or in the context of the full ABE complex.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Use of "TasA-7.10" vs "TadA-7.10"
- **Evidence pointer** Results section "Directed-evolution mutations also improve protein stability of TadA-8e"
- **Issue** In the text, "TasA-7.10" appears once where "TadA-7.10" is clearly intended. This typographical error could cause confusion.
- **Required correction** Correct the typographical error to "TadA-7.10".

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figure 4 and Figure 5B
- **Evidence pointer** Results sections on electrostatic analysis
- **Issue** The electrostatic surface potential figures are described in the text but the color scales and orientation of the structures are not described. For readers unfamiliar with electrostatic potential visualization, it may be difficult to interpret the figures without additional guidance.
- **Required correction** Add figure legends that explain the color scale (e.g., red for negative, blue for positive) and the orientation of the structures, and consider adding labels for key residues such as R111.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion cites prior work on ABE mechanisms and directed evolution, but does not fully contextualize the findings within the broader literature on TadA structure-function relationships and base editor engineering. For example, the relationship between the identified mutations and previously reported biochemical characterizations of TadA variants could be discussed more thoroughly.
- **Required correction** Expand the discussion to more comprehensively compare the findings with existing structural and biochemical studies of TadA variants and other base editors.

## Risk / unsupported claims
- The claim that "the editing activities of ABEs are closely related to their DNA-binding affinity and protein stability" is not directly supported by the experimental data presented, as no functional editing assays were performed.
- The claim that R111 is "the key mutation" for enhanced DNA binding is based on computational analysis and one literature reference, but no experimental validation of the R111 contribution (e.g., mutagenesis and binding measurements) is provided in this study.
- The claim that the directed-evolution mutations "improve the thermal stability of TadA-8e by ~12°C" is supported by nanoDSF measurements, but the mechanistic link between the identified electrostatic and hydrogen bonding changes and the increased Tm is inferred from computational analysis rather than directly demonstrated.
- The order of binding affinities (TadA-8e > wtTadA–TadA-8e > wtTadA–TadA-7.10 > TadA-7.10) is based on MM/PBSA calculations from single short trajectories without error estimates, making the robustness of this ordering uncertain.
- The statement that "the main driving force is electrostatic interactions" is supported by energy decomposition, but the relative contribution of electrostatic versus other interactions (e.g., van der Waals, hydrophobic) is not quantitatively compared across systems.