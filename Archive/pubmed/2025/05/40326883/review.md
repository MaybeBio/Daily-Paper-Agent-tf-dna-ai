## Review setup
- **Input scope** Full manuscript text (abstract, introduction, theory, results, discussion, conclusions, methods) as provided
- **Assessment boundary** Scientific and technical evaluation of the computational methodology, validation approach, and claims as presented; no assessment of editorial fit or publication venue suitability
- **Shared manuscript claim summary** The authors present a computational protocol combining interaction energy analysis, MM/GBSA, and FEP+ calculations to quantify cooperativity in molecular glue-mediated ternary complex formation, benchmarked against experimental CRBN–IKZF2 recruitment data, and applied to virtual screening of large chemical libraries to identify novel putative IKZF2 degraders
- **Visible evidence base** Abstract, full text narrative, methods descriptions, references to Figures 1–5 (not provided), Figures S1–S10 (not provided), Table 1 (not provided), Table S1 (not provided)
- **Missing materials affecting confidence** All figures, tables, and supplementary materials referenced in the text are not provided; experimental data from Bonazzi et al. is cited but not reproduced; PDB structure 8DEY is referenced but not independently assessed; no raw numerical data or statistical details for the reported energy values are available

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach to quantifying cooperativity in molecular glue-mediated ternary complex formation using pathway-independent free energy calculations. The theoretical framework connecting cooperativity to binding free energies is clearly articulated and represents a useful formalization. However, the central claims of predictive accuracy and screening utility cannot be fully evaluated from the provided text alone, as all quantitative results are contained in figures and tables that were not supplied. The methodological choices, particularly the use of interaction energies as a proxy for cooperativity and the treatment of entropic contributions, require careful scrutiny. The validation against experimental data is described but the degree of agreement and its statistical significance cannot be assessed. The virtual screening results are presented as promising but the false positive rate and experimental validation status are unclear. The manuscript would benefit from clearer articulation of the limitations of the computational approximations and a more critical discussion of potential sources of error.

- **Who would be interested in the results, and why** Computational chemists and drug discovery researchers working on targeted protein degradation, particularly those developing methods for predicting molecular glue activity and ternary complex formation. The theoretical framework for quantifying cooperativity may also interest biophysicists studying protein-protein interactions and allostery. Pharmaceutical scientists involved in CRBN modulator programs would find the screening protocol and identified candidates relevant.

- **Major strengths**
  1. The theoretical formalization of cooperativity in terms of binding free energies is clear and provides a rigorous thermodynamic basis for comparing different ligands
  2. The pathway-independent approach avoids assumptions about dominant binding mechanisms, which is a genuine advantage for systems where multiple assembly routes may contribute
  3. The combination of multiple computational methods (interaction energies, MM/GBSA, FEP+) provides complementary perspectives on the binding problem
  4. The benchmarking against experimental recruitment data for a panel of known ligands provides a practical validation framework
  5. The virtual screening application demonstrates a realistic use case and identifies specific candidate molecules for further study

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that the computational protocol "demonstrates high accuracy in identifying superior molecular glues" based on benchmarking against experimental data
- **Evidence pointer** Results section "Binding Affinities in the Ternary Complex"; Figures 1–3 (not provided)
- **Concern** The central validation claim cannot be assessed because all quantitative comparisons between computational predictions and experimental recruitment data are presented only in figures that were not provided. The text states that "all methods managed to rank L4 and L5 in front of the rest" but provides no numerical values, statistical measures, or error estimates. The claim of "high accuracy" requires quantitative evidence of correlation or concordance between predicted and experimental rankings.
- **Why it matters** The predictive validity of the protocol is the core contribution of the manuscript. Without access to the actual comparison data, the strength of the agreement between computation and experiment cannot be evaluated, and the claim of high accuracy remains unsubstantiated.
- **Resolution test** Provide the numerical data underlying Figures 1–3, including correlation coefficients, ranking concordance measures, and uncertainty estimates for the computational predictions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The manuscript defines a computationally efficient approximation of cooperativity as the sum of pairwise interaction energy differences between ternary and dual complexes (Equation 15)
- **Evidence pointer** Theory section, Equation 15; Results section "Binding Affinities in the Ternary Complex"
- **Concern** The approximation in Equation 15 equates cooperativity with changes in pairwise interaction energies, which is a purely enthalpic measure. The authors acknowledge that entropic contributions are not included in this approximation, but the magnitude of the resulting error is not discussed. For molecular glue binding, desolvation and configurational entropy changes can be substantial and may differ significantly between ligands. The manuscript does not provide any calibration of this approximation against the more rigorous FEP+ results for the same ligands.
- **Why it matters** If the interaction energy approximation systematically misranks ligands due to neglected entropic effects, the screening protocol could produce false positives or false negatives. The utility of the approach depends on the approximation being sufficiently accurate for ranking purposes, which is not demonstrated.
- **Resolution test** Provide a direct comparison between the interaction energy approximation and the FEP+ calculated cooperativity for the same set of ligands, including a discussion of cases where the two methods disagree and the likely sources of discrepancy.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that FEP+ calculations identified 17 candidate molecules with more favorable binding free energies and cooperativity than the reference compound L0
- **Evidence pointer** Results section "FEP Analysis of the Top Hits"; Figure 5 (not provided); Table S1 (not provided)
- **Concern** The FEP+ results are presented as the most accurate validation of the screening hits, but the convergence and statistical uncertainty of these calculations are not reported. FEP calculations for protein-ligand systems are notoriously sensitive to force field parameters, sampling length, and the choice of perturbation pathway. The manuscript does not provide information on the number of independent runs, the statistical error bars on the reported ΔΔG values, or the hysteresis between forward and reverse perturbations.
- **Why it matters** Without uncertainty estimates, the ranking of candidate molecules cannot be distinguished from noise. The claim that specific molecules outperform L0 requires that the differences exceed the statistical error of the calculations.
- **Resolution test** Report the statistical uncertainty for each FEP+ calculated ΔΔG and ΔCE value, including the number of independent simulations performed and the convergence criteria used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of validation
- **Claim pointer** The manuscript claims that the protocol "can identify candidates that after further optimization could achieve potency comparable to L5 in targeting IKZF2"
- **Evidence pointer** Results section "FEP Analysis of the Top Hits"; Conclusions
- **Concern** The virtual screening hits are not experimentally validated. The claim that they could achieve potency comparable to L5 is speculative and not supported by any experimental data. The manuscript acknowledges that experimental validation was beyond the scope of the study, but the language in the conclusions overstates the confidence in the predictions.
- **Why it matters** The practical utility of the screening protocol depends on its ability to identify genuine hits, not just computationally favorable candidates. Without experimental validation, the false positive rate of the protocol is unknown.
- **Resolution test** Either temper the language to clearly state that the candidates are computational predictions requiring experimental validation, or provide any available experimental data on the identified hits.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretational clarity
- **Claim pointer** The manuscript discusses the molecular basis of differences between IKZF degraders, specifically the interaction between charged ligands and E377CRBN, and the salt bridge between E137IKZF2 and R373CRBN
- **Evidence pointer** Results section "Molecular Basis of Differences between IKZF Degraders"; Figure 4 (not provided)
- **Concern** The interpretation of the residue-level interaction analysis is presented as providing mechanistic insight, but the text notes that the E137IKZF2-R373CRBN salt bridge is absent for L4 and that this "might lead to the overestimation of the molecular glue performance of L4." This is a significant caveat that undermines the reliability of the ranking for L4, yet the manuscript does not discuss how this affects the overall conclusions about L4 being a top performer.
- **Why it matters** If the computational model produces an artifact for L4 due to a missing salt bridge that would be present in the full-length protein, then the predicted superiority of L4 may be incorrect. This directly affects the interpretation of the benchmarking results and the screening outcomes.
- **Resolution test** Provide a more detailed discussion of the potential impact of the missing salt bridge on the predicted cooperativity of L4, and consider whether additional simulations with the full-length protein or with restraints would be needed to confirm the prediction.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Theory section, Equation 15
- **Evidence pointer** Theory section
- **Issue** The definition of the interaction energy approximation in Equation 15 is introduced without a clear derivation or justification for why the sum of pairwise interaction energy differences should approximate the free energy of cooperativity. The relationship between this approximation and the rigorous thermodynamic definition in Equation 11 is not explicitly stated.
- **Required correction** Add a brief derivation or explanation of how Equation 15 relates to Equation 11, and clarify the assumptions underlying the approximation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Methods section "Virtual Screening Campaign"
- **Evidence pointer** Methods section
- **Issue** The substructure search identified 1327 compounds, but the manuscript does not state how many of these were successfully prepared and docked, how many passed the docking filter, and how many were selected for MD simulations and FEP analysis. The attrition rate at each stage of the screening funnel is not reported.
- **Required correction** Provide a clear description of the number of compounds at each stage of the screening pipeline, from initial hit identification to final FEP analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Binding Affinities in the Ternary Complex"
- **Evidence pointer** Results section
- **Issue** The manuscript states that interaction energy values have "a considerable standard deviation" for the ΔIntEAB term but does not report the actual values or the number of independent simulations used to estimate this uncertainty.
- **Required correction** Report the standard deviations for the key energy values and specify the number of independent MD simulations performed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Force field consistency
- **Affected element** Methods section "System Building" and "Free Energy Perturbation (FEP) Calculations"
- **Evidence pointer** Methods section
- **Issue** The MD simulations for interaction energy and MM/GBSA calculations use the CHARMM C36m force field, while the FEP+ calculations use the OPLS4 force field. The manuscript does not discuss the potential impact of using different force fields for different stages of the analysis.
- **Required correction** Add a brief comment on the choice of force fields and any potential inconsistencies introduced by using different force fields for different calculations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction
- **Issue** The term "pathway-independent" is used to describe the free energy calculation method, but the manuscript does not explicitly define what pathways are being referred to or how the method achieves pathway independence. The distinction between this approach and other free energy methods that may be pathway-dependent is not clearly articulated.
- **Required correction** Clarify the meaning of "pathway-independent" in the context of the method and explain how it differs from alternative approaches.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Virtual Screening Campaign"
- **Evidence pointer** Methods section
- **Issue** The manuscript states that a substructure search was performed using the MaaS web service and SciFinder, but does not provide the specific search queries, the version of the databases used, or the date of the search. This limits the reproducibility of the screening results.
- **Required correction** Provide the specific substructure queries and database versions used for the search.

## Risk / unsupported claims
- The claim of "high accuracy in identifying superior molecular glues" is unsupported without access to the quantitative benchmarking data
- The claim that the virtual screening hits "could achieve potency comparable to L5" is speculative and not supported by experimental data
- The statement that the protocol "effectively predicts ligand-induced PPIs and their degradation potential" is not fully supported, as the relationship between ternary complex stability and degradation efficiency is not established in the manuscript
- The assertion that the method is "readily transferable to other PPIs" is plausible but not demonstrated
- The claim that the approach "does not require the estimation of the most dominant pathway" is supported by the theoretical framework but the practical advantages over pathway-dependent methods are not quantified
- The discussion of the E137IKZF2-R373CRBN salt bridge and its implications for L4 performance is presented as a hypothesis but the text does not clearly distinguish between established findings and speculation