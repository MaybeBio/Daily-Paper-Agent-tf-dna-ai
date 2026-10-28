## Review setup

- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, technical soundness, and internal consistency of the reported findings; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The authors report that the intrinsically disordered N-terminal domain (NTD) of p53, rather than the DNA-binding domain (DBD), is the major binding site for cyclophilin D (CypD), with a micromolar affinity, a broad and dynamic electrostatic interface overlapping the cyclosporin A (CsA) binding face, and two sub-regions (D1, residues 22-44; D2, residues 58-70) each contributing millimolar-affinity binding.
- **Visible evidence base** SPR binding data (Fig. 1), NMR chemical shift perturbation data (Figs. 2, 3, 6, 7), MD simulation results (Fig. 4, Figs. S4-S9), salt-dependent SPR experiments (Fig. 5), peptide binding data (Fig. 6, Figs. S2-S3)
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; no raw SPR sensorgrams; no NMR spectral overlays; no MD trajectory statistics or convergence metrics beyond textual description; no statistical error analysis for reported K D values; no experimental replicates described

## Reviewer

- **Overall assessment** The manuscript addresses a question of potential biological importance, namely the molecular basis of the p53-CypD interaction relevant to mPTP opening. The central claim that NTD, not DBD, is the major CypD binding site is supported by the SPR and NMR data as described, but the evidence base is incomplete in several respects. The reported micromolar affinity for NTD-CypD is plausible, and the identification of a broad electrostatic interface is consistent with the disordered nature of NTD. However, the manuscript has notable weaknesses in quantitative rigor, missing controls, and incomplete methodological detail that prevent full evaluation of the conclusions. The claim that NTD 20-70 is the minimal binding region is only partially supported, and the functional significance of the millimolar-affinity sub-fragments is unclear. The MD simulations are described in reasonable detail but their validation and convergence are not fully documented. Overall, the core finding is interesting and likely correct, but the manuscript requires substantial revision to establish the case convincingly.

- **Who would be interested in the results, and why** Researchers studying mitochondrial permeability transition, cell death pathways (necrosis, apoptosis), p53 biology, and intrinsically disordered protein interactions. The work may also interest those developing therapeutic strategies targeting p53-CypD interactions in ischemia-reperfusion injury, neurodegeneration, and cancer. The methodological approach combining SPR, NMR, and coarse-grained MD simulations could interest biophysicists studying disordered protein complexes.

- **Major strengths** The study addresses a previously unclear aspect of p53-CypD interaction, challenging the prevailing view that DBD is the primary binding site. The combination of SPR, NMR, and MD simulation provides complementary evidence. The identification of a dynamic, electrostatic interface is consistent with the known properties of NTD and provides a plausible mechanistic model. The use of multiple p53 constructs and the narrowing to NTD 20-70 as the minimal region is a logical experimental progression.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that NTD is the major CypD binding site on p53, with K D of ~10 μM for NTD and NTD-DBD, compared to ~1 μM for FLp53.
- **Evidence pointer** Fig. 1B-1E; location not provided
- **Concern** The SPR data are described only in text with K D values, but no sensorgrams, fitting curves, or statistical measures (e.g., standard errors, number of replicates) are shown. The claim that NTD is the major binding site relies on comparing K D values across constructs, but the difference between FLp53 (~1 μM) and NTD (~10 μM) is only 10-fold, and the authors do not discuss whether this difference is within experimental variability. Additionally, no data are shown for DBD alone binding to CypD, which is essential to support the claim that DBD is not a major binding site.
- **Why it matters** The central conclusion of the manuscript depends on the relative affinities of different p53 domains. Without raw data, replicates, and error estimates, the reader cannot assess whether the reported differences are significant. The absence of a DBD-only binding experiment leaves the comparison incomplete.
- **Resolution test** Provide SPR sensorgrams and fitting curves for all constructs, including DBD alone, with at least three independent replicates and reported K D values with standard deviations. Show that the K D difference between FLp53 and NTD is reproducible and that DBD binding is negligible or much weaker.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that NTD binds CypD with a broad and dynamic interface dominated by electrostatic interactions, and that the interface overlaps the CsA binding face.
- **Evidence pointer** Figs. 2, 3, 4; Figs. S1, S4-S9; location not provided
- **Concern** The NMR CSP data are described qualitatively, but no quantitative CSP values, significance thresholds, or mapped residue lists are provided. The claim that the interface is "broad" and "dynamic" is not supported by quantitative metrics. The MD simulations are described as predicting the same interface, but the convergence of the six independent simulations is only stated, not demonstrated with quantitative measures (e.g., RMSD, contact map convergence). The statement "This is consistent with NMR experiments showing [we should show CSP results at 1:1 or high ratio]" contains an incomplete placeholder, indicating the manuscript is not finalized.
- **Why it matters** The dynamic and electrostatic nature of the interface is a key finding. Without quantitative CSP data and MD convergence metrics, the reader cannot evaluate whether the interface is genuinely broad or whether the simulations have adequately sampled the binding landscape. The placeholder text suggests missing data.
- **Resolution test** Provide a complete CSP analysis with a significance threshold, a list of significantly perturbed residues, and a mapped surface representation. Show MD convergence metrics (e.g., contact probability error bars, block averaging) and a quantitative comparison between simulated and NMR-derived interface residues.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that NTD 20-70 is the minimal binding region for CypD interaction, maintaining micromolar affinity.
- **Evidence pointer** Fig. 7; location not provided
- **Concern** The data for NTD 20-70 are described in a single sentence with a K D of 9.4 μM, but no comparison is made to the full-length NTD (8.4 μM) in terms of statistical significance. The claim that NTD 20-70 is the "minimal" region requires testing of additional truncation constructs (e.g., NTD 1-20, NTD 70-100) to demonstrate that shorter fragments lose binding. The two sub-fragments D1 and D2 bind with only millimolar affinity, which is 100-fold weaker than NTD 20-70, and the authors do not explain how two millimolar-affinity fragments combine to yield micromolar affinity in the full NTD.
- **Why it matters** The identification of a minimal binding region is a specific and potentially useful finding for drug discovery. Without truncation analysis and a mechanistic explanation for the affinity difference between fragments and the full NTD, the claim is not established.
- **Resolution test** Test additional NTD truncation constructs to map the minimal region. Provide a quantitative comparison of K D values for NTD, NTD 20-70, D1, D2, and any additional fragments, with statistical analysis. Discuss the avidity or cooperativity effects that could explain the affinity difference.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the p53-CypD interaction is mainly driven by electrostatic interactions, based on salt-dependent SPR experiments.
- **Evidence pointer** Fig. 5; location not provided
- **Concern** The salt dependence experiment is described qualitatively ("moderate salt concentration inhibited more than 50% of the binding"), but no quantitative binding data (K D values at each salt concentration) or statistical analysis are provided. The interpretation that the interaction is "mainly driven by electrostatic interactions" is plausible but not quantitatively supported. The authors do not discuss whether the observed salt sensitivity could be due to changes in protein conformation or aggregation rather than direct electrostatic effects.
- **Why it matters** The electrostatic nature of the interaction is a central mechanistic claim. A quantitative salt dependence analysis (e.g., log K D vs. log [NaCl] plot) would provide a rigorous test. Without this, the claim remains qualitative.
- **Resolution test** Provide K D values at multiple salt concentrations with error bars, and a plot of log K D vs. log [NaCl] to derive the number of ion pairs involved. Include controls for protein stability and aggregation at high salt concentrations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states "NTD 20-70 was further identified as the minimal binding region" but does not mention the millimolar affinity of the D1 and D2 fragments, which is an important caveat.
- **Required correction** Add a sentence noting that D1 and D2 individually bind with millimolar affinity and that both are required for micromolar binding.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results section, "p53 binds to CypD through N-terminal domain (NTD)"
- **Evidence pointer** Location not provided
- **Issue** The text states "This has also been seen in other protein-protein binding interactions of p53, such as with the coactivator binding domain of the CREB binding protein 24" but does not explain the relevance of this comparison to the NTD-CypD interaction.
- **Required correction** Either expand on the relevance of the CREB binding protein comparison or remove it.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "2D NMR on 15 N CypD"
- **Evidence pointer** Location not provided
- **Issue** The equation for CSP calculation is referenced but not shown ("calculated using the equation"). The equation for residue-based binding affinity is also incomplete, with a missing term in the denominator.
- **Required correction** Provide the full CSP equation and correct the binding affinity equation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section, "NTD binds to the CsA-binding face of CypD"
- **Evidence pointer** Location not provided
- **Issue** The sentence "This is consistent with NMR experiments showing [we should show CSP results at 1:1 or high ratio]" contains an incomplete placeholder, indicating the manuscript is not finalized.
- **Required correction** Complete the sentence with the actual CSP data or remove the placeholder.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Molecular modeling of NTD and its interaction with CypD"
- **Evidence pointer** Location not provided
- **Issue** The description of the MD simulation validation states "The HyR model was first verified to provide a realistic description of the conformational properties of unbound p53-NTD compared to previous atomistic simulations and NMR studies (Fig. S4)" but no quantitative comparison metrics are provided.
- **Required correction** Provide quantitative measures of agreement (e.g., RMSD of secondary structure propensities, radius of gyration comparison) between the HyR simulation and reference data.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Location not provided
- **Issue** The discussion states "Our data clearly demonstrated that NTD plays a critical role for CypD binding, rather than DBD" but the data show that FLp53 binds with ~1 μM affinity while NTD binds with ~10 μM, which is a 10-fold difference. The word "clearly" overstates the strength of the evidence.
- **Required correction** Soften the language to reflect the quantitative difference, e.g., "Our data suggest that NTD plays a more important role than DBD in CypD binding."

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section, "Two NTD fragments bind CypD with mM affinity"
- **Evidence pointer** Fig. 6C; location not provided
- **Issue** The millimolar affinities for D1 and D2 are reported but no error estimates or replicate numbers are given.
- **Required correction** Report K D values with standard deviations and the number of independent measurements.

- **Technical failings that need to be addressed before the case is established** R1-M1 (missing SPR raw data and DBD control), R1-M2 (incomplete NMR and MD quantitative analysis, placeholder text), R1-M3 (incomplete truncation analysis and affinity discrepancy explanation)

- **Assessment against Nature-style criteria** Originality: The finding that NTD, not DBD, is the major CypD binding site challenges prior reports and is potentially original. However, the manuscript does not fully reconcile the discrepancy with previous work, and the originality is somewhat diminished by the preliminary nature of the data. Scientific importance: The p53-CypD interaction is relevant to cell death and disease, and a revised understanding of the binding interface could have therapeutic implications. The importance is moderate but not transformative. Interdisciplinary readership: The work bridges p53 biology, mitochondrial biology, and biophysical methods, which could appeal to a broad audience. However, the technical presentation is not sufficiently accessible to nonspecialists, particularly in the NMR and MD sections. Technical soundness: The combination of methods is appropriate, but the lack of quantitative rigor (missing error bars, replicates, and controls) undermines confidence. Readability for nonspecialists: The manuscript is generally readable but contains technical jargon and incomplete methodological details that would hinder a nonspecialist. Overall, the manuscript does not currently meet the standard for a high-impact general journal.

- **Recommendation posture** Supportive if technical concerns are resolved. The core finding is plausible and potentially interesting, but the manuscript requires substantial revision to provide complete quantitative data, appropriate controls, and a rigorous analysis of the binding interface. The placeholder text and missing figures must be addressed. If the authors can provide the missing evidence and strengthen the quantitative analysis, the manuscript could become a valuable contribution.

## Risk / unsupported claims

- The claim that NTD is the major CypD binding site is not fully supported without a DBD-only binding experiment and statistical comparison of K D values.
- The claim that the interface is "broad" and "dynamic" is not quantitatively supported by the NMR or MD data as presented.
- The claim that NTD 20-70 is the minimal binding region is not supported without additional truncation constructs.
- The claim that the interaction is "mainly driven by electrostatic interactions" is not quantitatively supported by the salt-dependent SPR data.
- The functional significance of the millimolar-affinity D1 and D2 fragments is not discussed or supported.
- The MD simulation results are described as consistent with NMR, but no quantitative comparison is provided.
- The statement in the Discussion that "Our data clearly demonstrated that NTD plays a critical role for CypD binding, rather than DBD" is an overstatement given the 10-fold affinity difference between FLp53 and NTD.