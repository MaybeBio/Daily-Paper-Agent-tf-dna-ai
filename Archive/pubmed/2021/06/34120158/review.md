## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological soundness, interpretation of results, and alignment with stated claims; no assessment of formatting or editorial style beyond Nature-style criteria
- **Shared manuscript claim summary** The authors compare salt-dependent DNA binding by two ETS-family transcription factors, Elk1 and ETV6, and use molecular dynamics simulations to propose that differences in extra-interfacial salt-bridge dynamics, driven by non-conserved acidic residues, underlie divergent nonspecific binding modes and contribute to target selectivity
- **Visible evidence base** Experimental binding data (SPR, fluorescence), MD simulations, DFT calculations, bioinformatic analysis, and structural comparisons
- **Missing materials affecting confidence** Supplementary figures and tables (Fig. S1–S7, Tables S1–S2) referenced but not provided; simulation input files, force field parameters, and convergence metrics not fully detailed; no experimental structures of nonspecific complexes

## Reviewer
- **Overall assessment** This manuscript addresses an important and under-explored question in protein/DNA recognition, namely the role of extra-interfacial salt bridges in modulating nonspecific binding and specificity. The comparative approach using two ETS homologs is well conceived, and the combination of experimental binding thermodynamics with MD simulations is appropriate. The central claim, that non-conserved acidic residues in Elk1 dynamically disengage from salt bridges upon nonspecific binding and are replaced by interactions with mobile Na+ ions, is plausible and potentially significant. However, the evidence base is incomplete in several respects. The MD simulations are used to support a mechanistic model, but the analysis relies on a single distance cutoff for salt-bridge identification, and the connection between simulated ionic distributions and the experimentally measured ion numbers is indirect. The DFT calculations are presented as supporting energetics but are simplified and may not capture the full free energy balance. The manuscript would be strengthened by a more rigorous treatment of uncertainties, additional validation of the simulation results, and a clearer quantitative link between the proposed mechanism and the observed binding free energy differences. The writing is generally clear, though some sections are dense and could benefit from more explicit signposting for a general readership.

- **Who would be interested in the results, and why** Researchers in the fields of protein/DNA recognition, transcription factor biology, and biophysical chemistry would find this work of interest. The study provides a comparative framework for understanding how sequence variation in conserved DNA-binding domains can lead to divergent specificity mechanisms. The methodological combination of binding thermodynamics, MD simulation, and quantum chemical calculations offers a template for similar analyses in other systems. The evolutionary implications for ETS-family transcription factors may also appeal to those studying gene regulation and protein evolution.

- **Major strengths**
  1. The comparative design using two structurally similar but compositionally divergent ETS domains is a powerful approach to isolate the role of ionic interactions in specificity.
  2. The experimental binding data are collected over a wide salt range, allowing robust extraction of ion numbers and comparison between cognate and nonspecific complexes.
  3. The integration of multiple computational methods (MD, DFT) with experimental data is ambitious and, in principle, well suited to the question.
  4. The identification of specific non-conserved residues (Asp2, Glu40) that behave differently between cognate and nonspecific complexes provides a concrete and testable hypothesis.
  5. The evolutionary discussion, while speculative, is thought-provoking and appropriately framed.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MD simulations "generated ionic interactions in agreement with the experimental binding data" and that the simulations reveal distinct salt-bridge dynamics that explain the experimental differences in ion numbers between Elk1 and ETV6.
- **Evidence pointer** Results and discussion, section "The electrostatic basis of target selectivity"; Fig. 5 and 6
- **Concern** The agreement between simulation and experiment is asserted but not quantitatively demonstrated. The experimental ion numbers (Δmobs) are derived from the salt dependence of binding, while the simulation analysis counts salt-bridge contacts and computes ionic densities. These are related but not equivalent quantities. The manuscript does not provide a direct comparison, such as a calculated Δmobs from the simulations, nor does it account for the contributions of mobile ions beyond the protein surface. The claim of agreement is therefore not substantiated by the data presented.
- **Why it matters** The central mechanistic conclusion rests on the validity of the simulations as a faithful representation of the experimental system. Without a quantitative link between simulated ionic distributions and measured thermodynamic quantities, the interpretation remains speculative.
- **Resolution test** Provide a quantitative comparison, e.g., compute the number of phosphate contacts from simulations and compare to the experimental Δmobs values, or calculate the free energy contribution from ionic distributions using a rigorous method (e.g., Poisson-Boltzmann or thermodynamic integration). Alternatively, present a clear argument for why the observed salt-bridge dynamics are sufficient to explain the experimental differences, with error estimates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "two non-conserved residues (Asp2 and Glu40) in Elk1 exhibited persistent differences between the cognate and nonspecific complexes" and that these residues are "material targets for analyzing the ionic disposition in nonspecific Elk1 binding."
- **Evidence pointer** Results and discussion, section "The electrostatic basis of target selectivity"; Fig. 7
- **Concern** The identification of Asp2 and Glu40 as key residues is based on a single MD analysis with a 4.5 Å cutoff for salt-bridge detection. The manuscript does not report the sensitivity of this result to the choice of cutoff, nor does it provide statistical measures of convergence across the three replicate simulations beyond median and MAD. The claim of "persistent differences" requires a more robust analysis, such as bootstrapping or block averaging, to ensure that the observed differences are not artifacts of limited sampling.
- **Why it matters** The proposed mechanism hinges on the specific behavior of these two residues. If the result is not robust to analysis parameters or sampling, the conclusion is weakened.
- **Resolution test** Perform a sensitivity analysis of the salt-bridge detection cutoff (e.g., 3.5, 4.0, 4.5, 5.0 Å) and report whether the differences for Asp2 and Glu40 persist. Provide convergence plots or block-averaged estimates with confidence intervals. If possible, validate with additional independent simulations or enhanced sampling.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that "primary structure variation in ionic residues can encode highly differentiated specificity mechanisms in a highly conserved DNA-binding motif" and that this has implications for the evolution of ETS transcription factors.
- **Evidence pointer** Results and discussion, section "Implications of divergent nonspecific binding modes in the evolution of ETS transcription factors"; Fig. 8
- **Concern** The evolutionary discussion is largely speculative and goes beyond the data presented. The correlation between isoelectric point and evolutionary distance (Fig. 8) is interesting but is not directly linked to the functional differences observed in this study. The claim that "increasing density of basic residues in more recent ETS relatives renders the canonical binding mode less tolerant to nonspecific DNA" is not tested experimentally or computationally. The connection between the specific findings for Elk1 and ETV6 and broader evolutionary trends is asserted rather than demonstrated.
- **Why it matters** While speculation can be valuable in a discussion section, the authors present this as a conclusion, which overstates the evidence. This may mislead readers into overinterpreting the evolutionary significance of the findings.
- **Resolution test** Either temper the language to clearly mark this as a hypothesis, or provide additional analysis, such as a phylogenetic comparison of salt-bridge dynamics across a broader set of ETS domains, to support the claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The DFT calculations are used to argue that "the electrostatic attraction for Na+ was more than twice stronger than Cl− at their corresponding contact minima," supporting the preferential association of Na+ with acidic residues.
- **Evidence pointer** Results and discussion, section "The electrostatic basis of target selectivity"; Fig. 6B
- **Concern** The DFT calculations are performed on simplified model systems (isolated amino acid side chains) in a continuum solvent. The transferability of these gas-phase or implicit-solvent interaction energies to the full protein/DNA complex in explicit solvent is not established. The manuscript does not discuss the limitations of this approach, such as the neglect of many-body effects, polarization, or the influence of the protein environment on the effective dielectric constant. The conclusion that Na+ is preferentially attracted over Cl− is qualitatively plausible but quantitatively uncertain.
- **Why it matters** The DFT results are used to rationalize the MD findings, but if the model systems are not representative, the support is weak. This affects the overall confidence in the mechanistic interpretation.
- **Resolution test** Provide a more detailed justification for the model systems, or perform calculations on larger fragments that better represent the local protein environment. Alternatively, use a more rigorous method, such as free energy perturbation or umbrella sampling, to estimate the relative affinities of Na+ and Cl− for the relevant sites.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, first paragraph
- **Evidence pointer** Location not provided
- **Issue** The introduction assumes familiarity with polyelectrolyte theory and the concept of ion release without sufficient context. A brief explanation of why salt dependence of binding is informative would help nonspecialist readers.
- **Required correction** Add one or two sentences explaining that the salt dependence of binding affinity reflects the release of ions from the DNA and protein surfaces, and that this can be used to infer the number of ionic contacts.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, MD simulations
- **Evidence pointer** Location not provided
- **Issue** The manuscript states that simulations were run "for at least 600 μs," which is likely a typo for 600 ns. This should be corrected to avoid confusion.
- **Required correction** Correct the unit to ns, or verify the actual simulation length and report it accurately.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, section "The electrostatic basis of target selectivity"
- **Evidence pointer** Fig. 5A
- **Issue** The scaling of the contact cutoff to match experimental ion numbers is described, but the rationale for this scaling is not fully explained. It is unclear whether this is a fitting procedure or a physically motivated choice.
- **Required correction** Clarify whether the cutoff was chosen a priori or adjusted to match experiment, and discuss the implications of this choice for the interpretation of the simulation results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, section "Energetic contributions of salt-bridge perturbations to DNA affinity"
- **Evidence pointer** Location not provided
- **Issue** The discussion of entropic contributions, including adsorption entropy, is dense and may be difficult to follow for readers without a thermodynamics background. The key point, that entropic penalties could offset favorable enthalpic contributions, is important but could be stated more clearly.
- **Required correction** Provide a brief, plain-language summary of the entropic argument before presenting the quantitative estimates.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative link between MD simulations and experimental ion numbers.
  - R1-M2: Insufficient robustness analysis of salt-bridge identification.
  - R1-M4: DFT model systems may not be representative of the protein environment.

- **Assessment against Nature-style criteria**
  - **Originality** The work is original in its comparative approach to studying extra-interfacial salt-bridge dynamics in ETS domains. While individual techniques are established, their combination to address this specific question is novel.
  - **Scientific importance** The question of how nonspecific binding is modulated by ionic interactions is of broad significance for understanding protein/DNA recognition. The findings could have implications for other DNA-binding protein families. However, the importance is somewhat limited by the narrow focus on two homologs and the lack of direct experimental validation of the proposed mechanism.
  - **Interdisciplinary readership** The work bridges biophysical chemistry, structural biology, and molecular biology. It would appeal to researchers in these fields, but the technical density may limit accessibility to a broader readership.
  - **Technical soundness** The experimental methods are sound, but the computational analysis has weaknesses as noted above. The conclusions are not fully supported by the evidence presented.
  - **Readability for nonspecialists** The manuscript is generally well written, but some sections assume significant background knowledge. The abstract and introduction are accessible, but the results and discussion sections are dense.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the experimental data are valuable, but the computational analysis needs to be strengthened to fully support the mechanistic claims. Specifically, the authors should provide a quantitative link between simulations and experiment, demonstrate the robustness of their salt-bridge analysis, and temper or better support the evolutionary implications.

## Risk / unsupported claims
- The claim that MD simulations "generated ionic interactions in agreement with the experimental binding data" is not quantitatively demonstrated.
- The assertion that Asp2 and Glu40 are the key residues driving differences in nonspecific binding is based on a single analysis without robustness checks.
- The evolutionary hypothesis that "increasing density of basic residues in more recent ETS relatives renders the canonical binding mode less tolerant to nonspecific DNA" is speculative and not directly supported by the data.
- The DFT calculations are used to support qualitative conclusions, but their quantitative relevance to the full complex is not established.