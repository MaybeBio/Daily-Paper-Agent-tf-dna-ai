## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, conclusion) without figures, tables, or supporting information
- **Assessment boundary** Scientific claims, methodology description, and internal logic as presented in the text; structural biology and computational data cannot be independently verified without figures, tables, and supplementary materials
- **Shared manuscript claim summary** The authors propose that a network of water molecules in the BRD4(1) bromodomain binding site functions as a hydrophobic recognition motif. They support this with binding assays, X-ray crystallography, MD simulations, and FEP calculations, showing that apolar groups contacting the water network bind favorably while polar groups are disfavored, and that this arises from systemic stabilization of the protein-water assembly rather than local water-ligand interactions.
- **Visible evidence base** Text descriptions of TR-FRET binding data (Table 1), crystal structures of compounds 2 and 4 (Figure 1, Table S1), MD water density analysis (Figure S6, Table 2), GIST decomposition (Table 2, Table S2), FEP calculations (Figure 2), protein dynamics analysis (Figure 3, Figure S7), and literature precedents (PDE4, BACE1, antifreeze proteins)
- **Missing materials affecting confidence** All figures, tables, and supporting information; experimental methods section; crystallographic statistics; FEP protocol details; GIST implementation parameters; compound synthesis and characterization data; pKa prediction details for compound 5

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially significant idea: that water networks can act as hydrophobic recognition motifs. The combination of experimental and computational approaches is appropriate for the question. However, the central claim rests on a chain of inference that cannot be fully evaluated from the text alone. The experimental binding data show a relatively flat SAR, and the key quantitative evidence comes from FEP calculations whose protocol is not described in the visible text. The interpretation of the GIST results as supporting a "systemic" mechanism is plausible but requires careful scrutiny of the decomposition. The broader generalization to PDE4 and BACE1 is suggestive but presented at a level that is too cursory to establish generality. The manuscript is well written and the concept is likely to interest a broad readership, but the strength of the conclusions currently exceeds what can be verified from the provided material.

- **Who would be interested in the results, and why** Structural biologists and biophysicists studying protein hydration and molecular recognition; computational chemists developing and applying free energy methods; medicinal chemists and drug discovery researchers interested in bromodomains and in understanding how water networks influence ligand design; protein engineers interested in non-canonical recognition motifs. The concept of water networks as hydrophobic motifs could have broad implications for understanding binding specificity and for designing ligands that exploit or avoid such networks.

- **Major strengths**
  1. The central concept is novel and counterintuitive, challenging the standard view that hydrophobic sites are simply apolar surfaces.
  2. The study combines multiple complementary techniques (binding assays, crystallography, MD, FEP, GIST), which is appropriate for the complexity of the question.
  3. The authors address the apparent paradox directly and provide a mechanistic hypothesis (systemic stabilization) that is testable.
  4. The use of a matched series of compounds differing only in polarity is a sound experimental design.
  5. The manuscript is clearly written and the logic is easy to follow for a broad audience.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "The water network functions as a hydrophobic recognition motif that cannot accommodate polar groups without disruption."
- **Evidence pointer** Table 1, Figure 1, Figure 2, location not provided
- **Concern** The experimental binding data show only modest differences: compound 4 (hydroxyl) loses 2.5-fold and compound 5 (amine) loses 6-fold relative to compound 1. The authors argue that compound 4's reversed binding mode indicates repulsion from the water network, but the affinity loss is small. The large predicted penalties from FEP (2.5-3.3 kcal/mol for neutral polar groups, 10 kcal/mol for charged) are not reflected in the experimental data. This discrepancy between computation and experiment is not adequately discussed. If the FEP calculations were performed with restraints that force the original binding mode, they may not represent the experimentally accessible binding modes. The claim that the water network "cannot accommodate polar groups" is stronger than the experimental evidence supports.
- **Why it matters** The central conclusion of the manuscript depends on establishing that polar groups are strongly disfavored at this site. If the experimental affinity differences are small and the computational predictions are not validated by experiment, the case for a hydrophobic recognition motif is weakened.
- **Resolution test** Provide a quantitative comparison of experimental and computed binding free energies for all compounds. Discuss the discrepancy explicitly. If possible, obtain experimental structures of compound 5 or additional polar analogues to test whether binding mode reversal is general. Alternatively, perform FEP calculations without restraints to allow binding mode changes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "Free energy perturbation (FEP) calculations with MD simulations in explicit water solvation... provide high confidence in the predicted values."
- **Evidence pointer** Figure 2, Table 1, location not provided
- **Concern** The FEP methodology is described only in general terms. No details are provided on the force field, water model, simulation length, number of lambda windows, equilibration protocol, or treatment of electrostatic interactions. The claim of "very low uncertainties" and "minimal errors" in cycle closures cannot be evaluated without seeing the actual values and the protocol. The pKa prediction for compound 5 is mentioned but the method is not described. The decision to consider both microspecies (50 and 5+) in simulations is appropriate, but the relative populations and how they are weighted in the final result are not stated.
- **Why it matters** FEP calculations are the primary quantitative evidence for the hydrophobic nature of the water network. Without a complete description of the methodology, the reliability of these predictions cannot be assessed. The discrepancy with experimental data (R1-M1) further underscores the need for methodological transparency.
- **Resolution test** Provide a full description of the FEP protocol in the Methods section, including force field parameters, simulation details, convergence criteria, and uncertainty estimates. Report the pKa prediction method and the weighting of microstates. Show the cycle closure errors explicitly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretational rigor
- **Claim pointer** "Binding of hydrophobic ligands results in a global decrease of protein dynamics... The change in dynamics is directly linked to the robustness of the water network."
- **Evidence pointer** Figure 3, Figure S7, Figure S8, location not provided
- **Concern** The causal link between ligand hydrophobicity, water network stability, and global protein dynamics is asserted but not rigorously established. The authors show correlations (hydrophobic ligands reduce dynamics, polar ligands increase dynamics) but do not demonstrate that the water network is the mediating factor. Alternative explanations, such as direct ligand-protein contacts or ligand-induced conformational changes, are not excluded. The GIST analysis shows that water molecules intrinsically prefer polar environments, which seems to contradict the claim that the water network is stabilized by hydrophobic groups. The authors explain this as a "trade-off" but the logic is not fully developed.
- **Why it matters** The proposed mechanism is the most novel aspect of the manuscript. If the link between water network stability and protein dynamics is not convincingly established, the manuscript becomes a description of an interesting correlation rather than a mechanistic insight.
- **Resolution test** Perform additional analyses to test causality, such as mutation of residues involved in the water network, or simulations with modified water models that alter water network stability. Provide a more detailed energetic decomposition showing how the "trade-off" operates quantitatively.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generality of claims
- **Claim pointer** "A systematic re-examination of historical structural data is likely to reveal further examples, extending beyond protein-ligand complexes."
- **Evidence pointer** Figure S9, Figure S10, Supporting Information, location not provided
- **Concern** The generalization to PDE4 and BACE1 is presented as supporting evidence for the universality of the phenomenon, but the analysis is described as "cursory." For PDE4, a single ligand (3DE) is cited, and the affinity increase is attributed to contact with the water network, but alternative explanations are not considered. The BACE1 discussion is relegated to Supporting Information and cannot be evaluated. The claim that this is a "general, underappreciated recognition motif" is not supported by the evidence presented.
- **Why it matters** The broader significance of the work depends on the generality of the phenomenon. If the PDE4 and BACE1 examples are not rigorously analyzed, the claim of generality is speculative.
- **Resolution test** Provide a more systematic analysis of PDE4 and BACE1, including multiple ligands and quantitative structure-activity relationships. Alternatively, temper the claims of generality and present the PDE4 and BACE1 examples as preliminary observations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the water network "cannot accommodate polar groups without disruption" but the experimental data show only modest affinity losses. This overstates the findings.
- **Required correction** Soften the language to reflect the actual magnitude of the effects, e.g., "strongly disfavors" or "is incompatible with."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Introduction
- **Evidence pointer** Introduction, location not provided
- **Issue** The introduction does not discuss alternative interpretations of water networks in binding sites, such as water-mediated hydrogen bonding or water displacement as an entropic driving force. This would provide context for the novelty of the claim.
- **Required correction** Add a brief discussion of existing views on water in binding sites and how the proposed concept differs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results and Discussion
- **Evidence pointer** Results and Discussion, location not provided
- **Issue** The text states that compound 4's reversed binding mode "cannot be justified by a gain of interaction of the newly introduced hydroxyl" but does not provide a quantitative analysis of the energetic consequences of the reversal. The reader is left to accept this assertion.
- **Required correction** Provide a brief energetic or structural argument for why the reversed mode is not more favorable, or acknowledge that the reversal itself is evidence of the hydrophobic character of the site.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Precision
- **Affected element** Results and Discussion
- **Evidence pointer** Results and Discussion, location not provided
- **Issue** The term "hydrophobic recognition motif" is used throughout but is not precisely defined. It is unclear whether this refers to a structural motif, a thermodynamic property, or a functional role.
- **Required correction** Define the term explicitly at first use and use it consistently.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Conclusion
- **Evidence pointer** Conclusion, location not provided
- **Issue** The conclusion mentions implications for "drug discovery, protein engineering, and structural and chemical biology" but does not provide specific examples of how the concept could be applied.
- **Required correction** Add one or two concrete examples of how recognizing water networks as hydrophobic motifs could influence design strategies.

- **Technical failings that need to be addressed before the case is established**
  1. FEP methodology is not described in sufficient detail to assess reliability (R1-M2).
  2. Discrepancy between experimental and computational affinity predictions is not addressed (R1-M1).
  3. Causal link between water network stability and protein dynamics is asserted without rigorous demonstration (R1-M3).
  4. Generalization to other targets is based on cursory analysis (R1-M4).

## Risk / unsupported claims
- The claim that the water network "cannot accommodate polar groups without disruption" is not supported by the experimental data, which show only modest affinity losses.
- The claim that "the protein pre-organizes the water network" is not directly demonstrated; no evidence is presented for pre-organization in the apo state.
- The claim that hydrophobic groups "reinforce the surrounding hydrogen-bond network" is inferred from GIST analysis but the causal direction is not established.
- The generalization to PDE4 and BACE1 as evidence for a "general" phenomenon is not supported by the level of analysis presented.
- The statement that "a systematic re-examination of historical structural data is likely to reveal further examples" is speculative and not based on a systematic analysis.
- The claim that the water network "limits the mobility of the entire protein-water assembly" is based on MD simulations but the statistical significance and magnitude of the effect are not reported.