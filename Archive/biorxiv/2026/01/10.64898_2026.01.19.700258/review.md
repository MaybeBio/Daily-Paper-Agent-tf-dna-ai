## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary references)
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive validity as presented in the supplied text
- **Shared manuscript claim summary** The authors report that Sirt1 binds exclusively to acetylated p53 in a 1:1 stoichiometry independent of p53 oligomeric state, that K382 is the predominant acetylation site and primary deacetylation target, and they present a first structural model of the full-length p53:Sirt1 complex derived from cross-linking mass spectrometry and data-driven docking
- **Visible evidence base** Native MS spectra (Figs 1, 2, S1–S5), CID-MS/MS dissociation data (Figs 2C, S4C, S5C), LC-MS/MS acetylation site mapping (Fig 3), deacetylation kinetics (Fig 4), SDS-PAGE cross-linking gels (Fig 5), XL-MS interaction maps (Fig 6, Supplementary Table I), docking results (Fig 7, Supplementary Table II)
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S7, Tables I–II) not provided; no raw MS data or annotated spectra; no statistical details for quantitative claims; no negative controls for acetylation specificity; no replicate information for native MS or kinetics experiments

## Reviewer
- **Overall assessment** This manuscript addresses a long-standing question in the p53 field, namely the structural basis of the p53:Sirt1 interaction. The integrated use of native MS, XL-MS, and docking is appropriate and potentially powerful for a system refractory to high-resolution structural methods. The central claim that Sirt1 binds exclusively to acetylated p53 with 1:1 stoichiometry is supported by the native MS data as described, and the identification of K382 as the primary deacetylation site is consistent with prior literature. However, several technical concerns, particularly around the interpretation of the K382 cross-link, the absence of quantitative rigor in the kinetics data, and the limited validation of the docking model, prevent full confidence in the conclusions as currently presented.
- **Who would be interested in the results, and why** Researchers studying p53 post-translational regulation, sirtuin biology, and the broader field of intrinsically disordered protein complexes. The methodological integration of XL-MS with docking for a highly flexible system will also interest structural biologists working on IDPs. The potential link between acetylation status and Sirt1 recruitment has implications for cancer biology and therapeutic targeting of the p53 pathway.
- **Major strengths** The study tackles a technically challenging system, full-length p53 with large disordered regions, using an appropriate suite of orthogonal methods. The observation that Sirt1 binds only acetylated p53 across all oligomeric states is clean and reproducible as presented. The identification of K382 as the dominant acetylation site and Sirt1 target is biologically significant and consistent with known p53 regulatory biology. The docking model, while necessarily low-resolution, provides a testable framework for future mutagenesis studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (K382 cross-link interpretation), R1-M2 (docking model validation), R1-M3 (kinetics quantification)
- **Assessment against Nature-style criteria** Originality is moderate to high, as no full-length p53:Sirt1 structural model has been reported, but the conceptual advance over prior peptide-based studies is incremental. Scientific importance is substantial given the central role of p53 acetylation in tumor suppression. Interdisciplinary readership is plausible, spanning structural biology, proteomics, and cancer biology. Technical soundness is mixed, with strong MS data but weaker computational validation. Readability for nonspecialists is adequate, though the methods sections assume significant MS expertise.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the K382 cross-link interpretation and docking validation

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of cross-linking data
- **Claim pointer** The authors state that the p53-K382:Sirt1-K427 cross-link is created immediately after deacetylation, when the two proteins are still in close proximity, and that this supports K382 acetylation as a prerequisite for complex formation.
- **Evidence pointer** Results section "Molecular details of p53:Sirt1 interaction", Fig 6, Supplementary Table I
- **Concern** The logic here is circular. The authors argue that because K382 is acetylated in the starting material, it cannot form a cross-link, and therefore its appearance as a cross-linked residue proves that deacetylation occurred during the cross-linking reaction. However, no time-resolved cross-linking experiment is presented to demonstrate that the K382-K427 cross-link appears only after deacetylation has occurred. An alternative explanation is that a subpopulation of p53 molecules is not acetylated at K382 in the starting material, and these unmodified molecules form the cross-link. The authors do not report the fractional occupancy of acetylation at K382 in their preparations, nor do they show that the cross-link abundance correlates with deacetylation kinetics. Without these controls, the claim that the cross-link reports on post-deacetylation proximity is not established.
- **Why it matters** This interpretation is central to the mechanistic model that acetylation at K382 is a prerequisite for Sirt1 binding. If the cross-link instead arises from a pre-existing unacetylated subpopulation, the model would need revision, and the conclusion that Sirt1 recognizes acetylated p53 specifically would be weakened.
- **Resolution test** The authors should quantify the acetylation occupancy at K382 in the starting p53 preparations. They should also perform a time-course experiment where cross-linking is quenched at different time points after Sirt1 addition, and show that the K382-K427 cross-link abundance increases with time in a manner that correlates with deacetylation. Alternatively, they could use a p53 variant with K382 mutated to arginine to demonstrate that the cross-link is lost, and a K382Q acetyl-mimetic to show that it is absent when acetylation is constitutive.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational model validation
- **Claim pointer** The authors present a structural model of the full-length p53:Sirt1 complex and state that clustering analysis indicates high confidence in the data-driven docking results.
- **Evidence pointer** Results section "Computational modeling to derive 3D-structural data of full-length p53:Sirt1 complex", Fig 7, Supplementary Table II
- **Concern** The docking model is derived from a small number of cross-links (ten unique inter-protein cross-links total, with only two recurrent across all variants). The manuscript reports a median pairwise backbone RMSD of 3.7 ± 1.3 Å across 188 retained models, but this metric only reflects internal consistency of the docking ensemble, not agreement with the experimental data. No information is provided on the fraction of cross-links satisfied by the final model, the HADDOCK scores, or whether the model was validated by any independent method such as SAXS or MD simulation. The removal of low-confidence regions from the input models is described but the specific residues removed are not listed, making it impossible to assess whether the docking was biased by the choice of input structures.
- **Why it matters** The structural model is a headline claim of the manuscript. Without clear metrics of how well the model satisfies the experimental restraints, and without any independent validation, the model remains a hypothesis rather than an established structure. Overstating confidence in the model could mislead the field.
- **Resolution test** The authors should report the fraction of cross-links satisfied by the final model, the HADDOCK Z-scores, and a comparison of the model to the input AlphaFold structures. They should also perform at least one independent validation, such as a short MD simulation to assess model stability, or SAXS analysis of the complex to compare with the model's radius of gyration. If such validation is not feasible, the claims of confidence should be tempered accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of kinetics data
- **Claim pointer** The authors report time-dependent deacetylation of K382 by Sirt1, with a minor decrease at K381, based on LC-MS/MS quantification.
- **Evidence pointer** Results section "Site-specific acetylation and deacetylation of p53", Fig 4
- **Concern** The deacetylation kinetics are described qualitatively ("time-dependent decrease", "minor decrease") without reporting the number of replicates, error bars, or statistical significance. The methods state that relative acetylation levels were normalized to all detected versions of each peptide, but no details are given on how many independent experiments were performed, whether the data points in Fig 4 represent means of replicates, or what the variability was. Without this information, it is not possible to assess whether the reported differences between K382 and K381 deacetylation are robust.
- **Why it matters** The claim that K382 is selectively deacetylated relative to K381 is a key part of the mechanistic model. If the difference is within experimental noise, the conclusion would be weakened.
- **Resolution test** The authors should provide replicate numbers, error bars, and statistical tests for the deacetylation time-course data. They should also report the limit of detection for the LC-MS/MS method to demonstrate that the "minor decrease" at K381 is not an artifact of poor sensitivity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Native MS stoichiometry determination
- **Evidence pointer** Methods section "Native MS of intact proteins", Figs 2, S4, S5
- **Issue** The manuscript states that complexes were observed with 1:1 stoichiometry but does not describe how the stoichiometry was assigned from the mass spectra. For a system with multiple oligomeric states, it is important to know whether the assignment was based on mass alone or on additional evidence such as dissociation behavior.
- **Required correction** Add a brief description of how stoichiometry was determined from the native MS data, including the expected and observed masses for each complex.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig 3 acetylation site quantification
- **Evidence pointer** Results section "Site-specific acetylation and deacetylation of p53", Fig 3
- **Issue** The manuscript reports acetylation at K370, K372, K373, K381, K382, and K386 but states that K370/K372/K373 were analyzed collectively due to ambiguity. It is unclear whether the collective analysis was due to peptide sequence redundancy or MS/MS fragmentation limitations, and whether this ambiguity affects the interpretation of the deacetylation kinetics.
- **Required correction** Clarify the reason for the collective analysis and state whether the ambiguity affects any of the conclusions drawn from the kinetics data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, paragraph 1
- **Issue** The authors note that previous structural insights were confined to short C-terminal p53 peptides, but they do not discuss the existing structural data on Sirt1 in complex with p53 peptides in any detail, nor do they explain how their full-length model compares to or extends these prior findings.
- **Required correction** Add a brief comparison of the new model to the previously reported peptide-bound Sirt1 structures, highlighting any novel features or discrepancies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion section
- **Issue** The term "exclusively" in the claim that Sirt1 binds exclusively to acetylated p53 is strong. The data show that non-acetylated p53 did not form detectable complexes under the conditions tested, but this does not rule out weak or transient interactions below the detection limit.
- **Required correction** Soften the language to "preferentially" or "detectably" to reflect the limits of the experimental approach.

## Risk / unsupported claims
- The claim that the p53-K382:Sirt1-K427 cross-link is formed immediately after deacetylation is not directly supported by the data presented, as no time-resolved cross-linking experiment is shown.
- The claim of "high confidence" in the docking results is not supported by the metrics reported, which only reflect internal consistency of the ensemble.
- The statement that Sirt1 binds "exclusively" to acetylated p53 is stronger than the data warrant, given the detection limits of native MS.
- The proposed model of sequential, processive deacetylation within the p53 tetramer is speculative and not directly tested by any experiment in the manuscript.
- The comparison to the S100β system, while interesting, is presented without sufficient mechanistic detail to establish a meaningful parallel.