## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure references
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to presented evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors use multiscale molecular dynamics simulations (all-atom and coarse-grained) to characterize the conformational ensemble of monomeric TDP-43 and identify a network of transient, predominantly electrostatic interdomain interactions that modulate the protein's phase behavior
- **Visible evidence base** Simulation results presented in main figures (Figures 1-5), supplementary figures (Figures S1-S8), and methodological descriptions in the Methods section
- **Missing materials affecting confidence** Raw simulation trajectories, force field parameter files, convergence analyses, error estimates for contact maps, experimental validation data, and code availability statements are not provided

## Reviewer

- **Overall assessment** This manuscript presents a computational investigation of interdomain interactions in TDP-43 using a multiscale simulation approach. The work addresses an important question regarding the molecular determinants of TDP-43 phase separation, which is relevant to understanding ALS and FTD pathology. The authors identify a network of heterodomain interactions involving linkers, RRM domains, and the disordered C-terminal domain, and provide evidence that these interactions are predominantly electrostatic. While the study is potentially valuable, several technical concerns regarding simulation methodology, validation, and interpretation must be addressed before the conclusions can be considered fully established.

- **Who would be interested in the results, and why** Researchers studying liquid-liquid phase separation of RNA-binding proteins, computational biophysicists interested in multidomain protein conformational ensembles, and investigators focused on TDP-43 biology in the context of neurodegenerative disease. The findings may also be relevant to those studying the role of electrostatic interactions in biomolecular condensate formation.

- **Major strengths** The study addresses a significant gap in understanding TDP-43 phase behavior by examining heterodomain interactions beyond the well-characterized homodomain interactions. The multiscale approach combining all-atom and coarse-grained simulations is appropriate for spanning the relevant length and time scales. The comparison of monomeric and condensed phase behavior provides a coherent framework for linking single-chain properties to phase separation. The salt sensitivity analysis provides a testable prediction that connects to experimental observations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the all-atom simulations provide a reliable conformational ensemble of monomeric TDP-43, with a mean Rg of 3.56 ± 0.40 nm, and that this ensemble is representative of the protein's behavior under physiological conditions
- **Evidence pointer** Results section "TDP-43 populates a diverse conformational ensemble in the monomeric state", Figure 2a,b, Figure S1
- **Concern** The all-atom simulations were performed for 3 replicates of 5 microseconds each. For a 414-residue multidomain protein with large disordered regions, this timescale may be insufficient to achieve conformational convergence. The authors do not provide convergence analyses such as block averaging, autocorrelation times, or comparison of independent replicate distributions. The wide Rg distribution (3.56 ± 0.40 nm) suggests significant conformational heterogeneity, but it is unclear whether this reflects true equilibrium sampling or incomplete exploration of conformational space. Additionally, the use of a single force field (AMBER99SBws-STQ) without cross-validation against alternative force fields or experimental data limits confidence in the ensemble.
- **Why it matters** The entire analysis of interdomain interactions depends on the reliability of the conformational ensemble. If the simulations have not converged, the identified interaction network may be biased by the initial conditions or insufficient sampling, leading to incorrect conclusions about which interactions are biologically relevant.
- **Resolution test** Provide convergence metrics (e.g., time evolution of Rg, contact maps from independent halves of trajectories, autocorrelation analysis). Compare ensembles from different starting structures or force fields. Validate against available experimental data such as SAXS profiles, FRET measurements, or NMR chemical shifts if available.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the CG simulations at 325 K reproduce experimental saturation concentrations (csat) for TDP-43 phase separation, with simulated csat of 2-3 μM compared to experimental values of 0.5-2.5 μM
- **Evidence pointer** Methods section "Parameterization of phase-coexistence simulations against in vitro experiments", Figure S7d
- **Concern** The agreement between simulated and experimental csat is presented as validation of the CG model, but the comparison involves several assumptions. The experimental csat values are cited from studies using different buffer conditions, protein constructs, and measurement methods. The CG model uses a Debye-Hückel electrostatic potential with a screening length corresponding to approximately 100 mM ionic strength, but the experimental values cited include measurements at 150 mM NaCl. The temperature correction (simulating at 325 K to match 300 K all-atom behavior) introduces an additional empirical adjustment that may affect the transferability of the model. Furthermore, the authors state that the CG model does not capture binding affinity and specificity of NTD dimerization and CR oligomerization, yet these interactions are known to be important drivers of TDP-43 phase separation.
- **Why it matters** The validity of the condensed phase analysis depends on the reliability of the CG model. If the model is not accurately capturing the physics of phase separation, the conclusions about which interdomain interactions are prevalent in the condensed phase may be incorrect.
- **Resolution test** Provide a more detailed comparison of simulation conditions with experimental conditions. Test the sensitivity of csat predictions to model parameters (e.g., screening length, temperature). Validate the CG model against additional experimental observables such as cluster size distributions, diffusion coefficients, or domain-specific contact frequencies if available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the heterodomain interactions identified in their simulations "modulate the conformational landscape of TDP-43 monomer (dilute phase) and occur within the condensed phase alongside homodomain interactions" and that these interactions "collectively dictate the phase behavior of TDP-43 under physiological conditions"
- **Evidence pointer** Results sections "A diverse network of inter-domain interactions underlies the conformational ensemble of monomeric TDP-43" and "CG simulations of TDP-43 condensates reveal a complex network of homo- and heterodomain intermolecular interactions", Figures 2c, 3, 5
- **Concern** While the simulations identify a network of interdomain interactions, the functional significance of these interactions for phase behavior is not directly demonstrated. The authors show that interactions exist and are electrostatic, but they do not perform perturbation analyses (e.g., mutating key charged residues, altering linker sequences) to test whether disrupting these interactions changes phase behavior in a predictable manner. The claim that these interactions "dictate" phase behavior is therefore an inference rather than a demonstrated conclusion. Additionally, the physiological relevance of the monomeric ensemble is unclear, as TDP-43 is known to oligomerize and bind RNA in cells.
- **Why it matters** The central claim of the paper is that a network of interdomain interactions modulates phase behavior. Without direct perturbation experiments or additional validation, the causal relationship between the identified interactions and phase separation remains correlative.
- **Resolution test** Perform additional simulations with charge-neutralizing mutations in key interacting regions and show that phase behavior changes accordingly. Alternatively, compare the interaction network in the monomeric ensemble to that in the condensed phase more quantitatively, identifying which interactions are specifically enriched or depleted upon condensation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the increase in salt concentration from 100 mM to 300 mM NaCl leads to a "substantial loss of heterodomain interactions" and conformational expansion of TDP-43
- **Evidence pointer** Results section "Heterodomain interactions are predominantly electrostatic in nature and sensitive to salt", Figure 4
- **Concern** The salt dependence is tested using only two salt concentrations (100 mM and 300 mM). This limited sampling does not establish a dose-response relationship or rule out non-electrostatic effects. Additionally, the all-atom simulations at 300 mM NaCl were performed for the same duration as the 100 mM simulations, but no convergence analysis is provided for the high-salt condition. The interpretation that the observed expansion is due specifically to loss of electrostatic interactions assumes that other salt-dependent effects (e.g., changes in hydrophobic interactions, hydrogen bonding) are negligible, which is not demonstrated.
- **Why it matters** The conclusion that interdomain interactions are "predominantly electrostatic" rests on the salt dependence data. If the salt effect is not cleanly attributable to electrostatics, the mechanistic interpretation may be incomplete or incorrect.
- **Resolution test** Perform simulations at intermediate salt concentrations (e.g., 150, 200, 250 mM) to establish a dose-response relationship. Analyze the specific interaction types that change with salt concentration to confirm that electrostatic interactions are the primary affected species.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The authors state that their findings "lead to a greater appreciation of the complex interaction network underlying the structural landscape and phase separation of TDP-43" and suggest the approach has "great potential in unraveling the complex interaction network underlying biologically-relevant, multi-component condensates"
- **Evidence pointer** Discussion section
- **Concern** The broader implications of this work for understanding TDP-43 biology are not fully developed. The authors do not discuss how their findings relate to specific disease-associated mutations beyond the A90V site mentioned in passing, nor do they connect their results to the growing experimental literature on TDP-43 phase separation and aggregation. The potential therapeutic implications of targeting electrostatic interdomain interactions are not explored.
- **Why it matters** For a broad readership, the significance of the findings needs to be contextualized within the larger framework of TDP-43 biology and neurodegeneration. Without this context, the work may appear as a purely computational exercise with limited translational relevance.
- **Resolution test** Expand the discussion to address how specific disease mutations might affect the identified interaction network, and discuss how the findings could inform experimental studies or therapeutic strategies.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction
- **Evidence pointer** Introduction section
- **Issue** The introduction assumes significant familiarity with phase separation concepts and TDP-43 biology. Terms such as "valency," "scaffolds," and "condensates" are used without sufficient explanation for readers outside the immediate field.
- **Required correction** Provide brief definitions or explanations of key terms when first introduced, and consider adding a short paragraph on the biological context of TDP-43 phase separation for nonspecialist readers.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section
- **Evidence pointer** Methods section "All-atom MD simulations"
- **Issue** The description of the simulation protocol contains some ambiguities. The sentence "5 μs production simulations were performed for 5 μs in the NVT ensemble was performed using the Langevin Middle Integrator" contains a grammatical error and redundancy. Additionally, the rationale for using the NVT ensemble for production runs after NPT equilibration is not explained.
- **Required correction** Rewrite the sentence for clarity and provide justification for the ensemble choice.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section
- **Evidence pointer** Methods section "Coarse-grained (CG) MD simulations"
- **Issue** The description of the CG model parameters is incomplete. The authors mention the HPS model based on the Urry hydrophobicity scale but do not provide specific parameter values, the version of the model used, or details on how the electrostatic interactions are implemented in the CG framework.
- **Required correction** Provide complete parameterization details or reference the specific model implementation used, including any modifications made for this study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section
- **Evidence pointer** Results section "TDP-43 populates a diverse conformational ensemble in the monomeric state"
- **Issue** The classification of conformations into compact, intermediate, and extended based on Rg thresholds appears arbitrary. The authors do not justify the specific cutoffs (3.0 nm and 4.0 nm) or demonstrate that these categories represent distinct conformational states rather than a continuum.
- **Required correction** Provide justification for the chosen cutoffs or use a more objective classification method such as clustering based on structural similarity.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Methods section
- **Issue** The manuscript does not include a data availability statement or code availability statement. Given the computational nature of the work, this is a significant omission for reproducibility.
- **Required correction** Add statements regarding availability of simulation input files, analysis scripts, and any custom code used in the study.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors mention that their findings are "broadly supported" by a previous NMR study (Wei et al., 2016), but do not provide a detailed comparison of their interaction network with the experimental data. A more quantitative comparison would strengthen the validation of the simulation results.
- **Required correction** Provide a more detailed comparison with experimental data, including specific interaction sites or regions that are consistent or inconsistent between simulation and experiment.

## Risk / unsupported claims
- The claim that heterodomain interactions "collectively dictate the phase behavior of TDP-43 under physiological conditions" is not directly supported by the presented evidence, as no perturbation experiments were performed to establish causality
- The claim that the CG model at 325 K reproduces experimental csat values relies on comparisons with experiments conducted under different conditions and involves empirical temperature adjustments, making the validation indirect
- The assertion that the identified interdomain interactions are "predominantly electrostatic" is based on only two salt concentrations and does not exclude contributions from other interaction types
- The physiological relevance of the monomeric TDP-43 ensemble is not established, as the protein is known to oligomerize and interact with RNA in cellular contexts
- The statement that the approach has "great potential" for studying multi-component condensates is speculative and not demonstrated in this work