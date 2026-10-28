## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends as provided.
- **Assessment boundary** Scientific content, methodological rigor, interpretation of results, and alignment with claims. Editorial and formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations of an 8-chain system of the low-complexity domain of hnRNPA1 (A1-LCD) at NaCl concentrations from 50 to 1000 mM to explain the atypical salt dependence of its phase separation. They propose two direct salt effects (charge neutralization and ion bridging between chains) and one indirect effect (strengthening of π-type interactions via water withdrawal), and they propose a classification of salt dependence of intrinsically disordered protein phase separation into four classes predictable from amino acid composition.
- **Visible evidence base** Simulation trajectories (four replicates of 1.5 μs per salt concentration), analyses of Dmax, radius of gyration, inter- and intrachain contacts, ion binding via radial distribution functions, bridging ion counts, and water radial distribution functions around tyrosine residues. Figure supplements and a table of protein properties are referenced.
- **Missing materials affecting confidence** No experimental validation data are included. The manuscript states that phase separation was "readily observed" in prior work (Martin et al., 2021) but does not include new experimental data. The classification scheme in Table 1 is described but the full table is not visible in the provided text. The GitHub repository for analysis scripts is mentioned but not assessed.

## Reviewer
- **Overall assessment** This manuscript presents a detailed all-atom simulation study of salt effects on A1-LCD phase separation. The work is technically ambitious and provides a plausible molecular mechanism for the atypical salt dependence. The distinction between direct and indirect salt effects is conceptually useful. However, the evidence for the indirect effect (water withdrawal strengthening π-interactions) is indirect and based on correlation rather than causation. The generalization to a four-class classification of salt dependence, while interesting, is supported by limited data and the predictive power is not rigorously tested. The manuscript would benefit from clearer presentation of the classification scheme and a more critical discussion of the limitations of the simulation approach.
- **Who would be interested in the results, and why** Researchers studying biomolecular condensates, liquid-liquid phase separation, intrinsically disordered proteins, and the molecular mechanisms of ion effects on protein interactions. The work is also relevant to those developing coarse-grained models of phase separation, as it provides atomic-level detail that can inform parameterization. The proposed classification of salt dependence may be of interest to a broader community studying IDP phase behavior.
- **Major strengths** The use of multi-chain all-atom simulations with explicit solvent and ions is a significant technical effort. The identification of two distinct direct effects (charge neutralization and bridging) is well supported by the simulation data. The analysis of water withdrawal around π-interaction partners is a novel and interesting observation. The authors connect their findings to a broader classification scheme, which adds conceptual value.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (simulation length and equilibration), R1-M2 (causality of indirect effect), R1-M3 (classification scheme validation).
- **Assessment against Nature-style criteria** **Originality**: The work is original in its atomic-level description of salt effects on a specific IDP system and in its proposal of a classification scheme. However, the conceptual framework (direct vs. indirect salt effects) is not entirely new. **Scientific importance**: The work addresses an important and unresolved question about the molecular mechanisms of salt effects on phase separation. The findings are likely to be of interest to the field. **Interdisciplinary readership**: The topic is relevant to biophysics, biochemistry, and cell biology. The writing is generally accessible, though some simulation details may be heavy for non-specialists. **Technical soundness**: The simulation methodology is appropriate, but concerns about simulation length and the indirect nature of the water-withdrawal evidence need to be addressed. **Readability for nonspecialists**: The abstract and introduction are clear, but the results section is dense and may be challenging for readers not familiar with simulation analysis techniques.
- **Recommendation posture** Supportive if technical concerns are resolved. The core simulation results are valuable, but the causal link for the indirect effect and the robustness of the classification scheme need strengthening.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the simulations show a lack of condensation at 50 mM NaCl and growing condensation at higher salt concentrations, and that the systems are equilibrated based on analysis of the last 500 ns of 1.5 μs trajectories.
- **Evidence pointer** Methods, "MD simulations"; Results, "Salt condenses A1-LCD and increases inter-chain interactions"; Figure 2.
- **Concern** The simulation time of 1.5 μs may be insufficient for a multi-chain system of this size (~500,000 atoms) to reach equilibrium, particularly at low salt where the system is described as maintaining a "loose configuration" with chains occasionally spanning the simulation box. The authors state that the last 500 ns was used for analysis, but no convergence tests (e.g., block averaging, comparison of early vs. late trajectory segments) are presented. The Dmax values at 50 mM remain close to the initial value, which could indicate a trapped, non-equilibrated state rather than a thermodynamically stable dispersed phase.
- **Why it matters** The central claim of the paper is that salt promotes condensation. If the low-salt simulation is not equilibrated, the observed difference between low and high salt could be a kinetic artifact rather than a thermodynamic effect. This would undermine the mechanistic conclusions.
- **Resolution test** Provide convergence analysis, such as time evolution of Dmax, Rg, and inter-chain contacts for each replicate, and demonstrate that these properties have plateaued. Consider longer simulations or replica exchange methods to enhance sampling. If the low-salt system is genuinely slow to equilibrate, this should be acknowledged and discussed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of results
- **Claim pointer** The authors claim that high salt strengthens π-type interactions by drawing water away from the interaction partners, and that this is an indirect mechanism contributing to condensation.
- **Evidence pointer** Results, "Salt also contributes to condensation indirectly by strengthening π-type interactions"; Figure 5.
- **Concern** The evidence for the water-withdrawal mechanism is correlative. The authors show that (i) the number of π-type inter-chain interactions increases with salt, and (ii) water density around tyrosine residues involved in π-interactions decreases with salt. However, they do not demonstrate a causal link. The decrease in water density could be a consequence of the increased number of π-interactions (i.e., water is excluded because the residues are now in contact) rather than the cause of their strengthening. The authors also do not quantify the free energy contribution of water withdrawal versus the direct ion effects.
- **Why it matters** The claim of an indirect salt effect is a key novel contribution of the paper. If the causal direction is not established, the mechanistic model is incomplete and potentially misleading.
- **Resolution test** Perform additional analyses to support causality. For example, calculate the potential of mean force between π-interaction partners as a function of salt concentration and decompose the contributions from ions and water. Alternatively, perform simulations with a modified water model or with ions that are less effective at withdrawing water to test the predicted effect. At minimum, the authors should discuss the alternative interpretation that water withdrawal is a consequence, not a cause, of increased π-interactions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability / claims
- **Claim pointer** The authors propose a four-class classification of salt dependence of IDP phase separation and state that these classes can be predicted from amino acid composition.
- **Evidence pointer** Discussion, Figure 6, Table 1.
- **Concern** The classification scheme is presented as a general framework, but it is derived from a limited set of examples (Table 1). The predictive criteria (total charged residues, net charge, aromatic content) are described qualitatively, and the thresholds (e.g., 8% aromatic content, 6% net charge) appear to be chosen post hoc. No statistical validation is provided, and the classification of some proteins (e.g., Caprin1 vs. pY-Caprin1) is based on data from other studies with different experimental conditions. The claim that the classification is "predictable" is therefore not well supported.
- **Why it matters** The classification scheme is a major conceptual output of the paper. If it is not robustly validated, its utility to the field is limited, and the claim of predictability is overstated.
- **Resolution test** Provide a more rigorous test of the classification scheme. This could include: (i) a larger dataset of IDPs with known salt dependence; (ii) a quantitative decision tree or logistic regression model with defined thresholds; (iii) prospective predictions for proteins not in the training set, followed by experimental or literature-based validation. At minimum, the authors should clearly state the limitations of the current dataset and the tentative nature of the thresholds.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 3
- **Evidence pointer** Results, "Ions selectively bind to backbone and sidechain sites to neutralize the net charge of A1-LCD"
- **Issue** The left panel of Figure 3A shows ion counts per residue for Cl- and Na+ around different sidechain types. The normalization is described as "per residue," but it is unclear whether this is per residue of that type in the system, or per residue that is in contact with an ion. The text states "On a per-residue basis, Arg and Lys sidechains coordinate the most 1st-shell Cl- ions, reaching ~0.25 ions per residue." This is ambiguous.
- **Required correction** Clarify the normalization procedure in the figure legend and methods. Specify whether the count is averaged over all residues of that type, or only over those that have at least one ion in their coordination shell.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "MD simulations"
- **Evidence pointer** Methods, "MD simulations"
- **Issue** The manuscript states that the initial configuration was built from conformations from previous single-copy simulations, with 4 copies placed in a box and then duplicated to form the 8-chain system. It is not clear whether the 4 copies were distinct conformations or whether the duplication creates a symmetric, potentially biased, initial arrangement. The choice of initial configuration can influence the kinetics of condensation.
- **Required correction** Provide more detail on the selection of initial conformations and the construction of the 8-chain system. Discuss whether the duplication could introduce artifacts and whether the results are robust to different initial arrangements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Discussion, classification scheme
- **Evidence pointer** Discussion, Figure 6
- **Issue** The four classes of salt dependence are described in the text and Figure 6, but the description is dense and the figure is not available in the provided text. The distinction between the "reentrant" and "high net charge" classes may be confusing, as both involve high salt promoting phase separation.
- **Required correction** Consider adding a clear, concise summary of the four classes in the main text, perhaps in a table format, with a one-sentence description of each class and a representative example. Ensure the figure is self-explanatory.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The data availability statement says all data are included in the manuscript and supplementary files, and a GitHub link is provided for analysis scripts. However, the specific simulation input files, force field parameters, and initial coordinates are not mentioned. For reproducibility, these should be made available.
- **Required correction** Provide a more detailed data availability statement, including deposition of simulation input files and trajectories in a public repository, or clearly state why these cannot be shared.

## Risk / unsupported claims
- The claim that the four-class classification of salt dependence is "predictable from amino acid composition" is not fully supported by the data presented. The thresholds are post hoc and no prospective validation is provided.
- The claim that water withdrawal is a causal mechanism for strengthening π-interactions is not established; the data are correlative.
- The statement that the simulation at 50 mM NaCl "mimics a homogenous solution" is an interpretation, not a demonstrated fact, given the potential for incomplete equilibration.
- The generalization of findings from A1-LCD to other IDPs (e.g., in the discussion of Caprin1) relies on literature data and is not directly tested here.