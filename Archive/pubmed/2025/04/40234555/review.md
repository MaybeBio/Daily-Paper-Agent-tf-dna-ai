## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) as provided
- **Assessment boundary** Scientific soundness, methodological rigor, and support of claims based solely on the supplied material
- **Shared manuscript claim summary** The authors report seven novel somatic missense variants in the VHL gene from 210 Eastern Indian (Bengali) ccRCC patients and use in silico tools to predict their pathogenicity, effects on protein stability, and impact on VHL-Elongin C binding.
- **Visible evidence base** Tables 1-4, Figures 1-4, Supplementary Tables 1-2, Supplementary Files S1-S2, Supplementary Figure 1
- **Missing materials affecting confidence** Raw sequencing data, detailed docking scores beyond summary statistics, full CABS-flex output, experimental validation data, and complete clinicopathological raw data

## Reviewer
- **Overall assessment** The manuscript addresses an important gap in population-specific VHL mutation data from India and applies a reasonable computational pipeline. However, the study is purely in silico and the central claim regarding effects on VHL-Elongin C binding is supported only by predictive tools without experimental validation. The presentation of results is at times unclear, and several methodological details are insufficiently described. The work is of interest to the ccRCC genetics community but does not currently establish a definitive case for the functional impact of these variants.
- **Who would be interested in the results, and why** Researchers in renal cancer genetics, particularly those studying population-specific mutation spectra in under-represented groups. Clinicians and genetic counsellors in India may also find the data useful for variant interpretation. The computational approach may interest methodologists working on protein-protein interaction prediction.
- **Major strengths** 1) Addresses a clear gap in representation of Indian populations in VHL mutation databases. 2) Identifies seven novel variants, expanding the known mutation spectrum. 3) Applies a multi-tool in silico pipeline for pathogenicity prediction. 4) Provides structural and dynamic analysis of variant effects on a key protein interaction.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of experimental validation), R1-M2 (inadequate docking methodology description), R1-M3 (overstated conclusions from RMSF data), R1-M4 (unclear statistical framework)
- **Assessment against Nature-style criteria** Originality: Moderate. The finding of novel variants is original but the approach is standard. Scientific importance: Moderate. Population-specific data are valuable but the lack of functional validation limits significance. Interdisciplinary readership: Limited. Primarily relevant to cancer genetics and computational biology specialists. Technical soundness: Partially adequate. The computational pipeline is reasonable but has methodological gaps. Readability for nonspecialists: Acceptable but could be improved with clearer figure descriptions and more explicit statements of limitations.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding methodological transparency and tempering of conclusions. Currently not fully established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The manuscript claims that the identified variants "predict to affect the interface interactions between VHL and Elongin C" and that this has implications for ccRCC pathogenesis.
- **Evidence pointer** Results sections on docking, interface residues, and MD simulation; Discussion
- **Concern** The entire functional inference rests on computational predictions. No experimental validation (e.g., co-immunoprecipitation, pull-down assays, cellular assays) is provided to confirm that the predicted changes in binding actually occur in biological systems. The authors acknowledge this in the limitations but still frame the findings as having pathogenic significance.
- **Why it matters** Computational predictions of protein-protein interaction changes are notoriously prone to false positives. Without experimental confirmation, the central claim that these variants affect VHL-Elongin C binding and thereby contribute to ccRCC remains speculative.
- **Resolution test** Provide experimental validation for at least the most strongly implicated variants, or substantially temper the conclusions to reflect the predictive nature of the findings.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The docking results are presented as evidence of differential binding affinity between wild-type and mutant VHL-Elongin C complexes.
- **Evidence pointer** Methods section on molecular docking; Table 3
- **Concern** The description of the docking methodology is insufficient. Key parameters are not reported, including the number of docking runs, the scoring function used for ranking, the criteria for selecting the best model, and how the HADDOCK score was interpreted. The active residues are stated but the rationale for their selection is not fully explained. Additionally, the HADDOCK score is a relative measure and cannot be directly interpreted as binding affinity without further analysis (e.g., free energy calculations).
- **Why it matters** Without a clear and reproducible docking protocol, the results cannot be independently verified. The interpretation of HADDOCK scores as direct indicators of binding strength is an oversimplification that may mislead readers.
- **Resolution test** Provide a detailed docking protocol, including all parameters, and use additional methods (e.g., MM-PBSA, free energy perturbation) to corroborate the binding affinity predictions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of results
- **Claim pointer** The RMSF analysis is used to conclude that "mutant VHL demonstrates somewhat less flexibility in its active site residues relative to the wild-type complex" and that this may affect binding.
- **Evidence pointer** Results section on MD simulation; Figure 4
- **Concern** The RMSF values are reported as averages over the active site region, but the significance of the differences is not assessed statistically. The biological relevance of the observed RMSF changes is not established. Reduced flexibility does not necessarily imply impaired binding; in some cases, reduced flexibility can enhance binding by reducing entropic penalties. The interpretation is therefore one-sided and not fully justified.
- **Why it matters** The conclusion that reduced flexibility leads to impaired function is an inference that requires additional support. Without statistical analysis and a more nuanced discussion, the claim is overstated.
- **Resolution test** Perform statistical comparison of RMSF distributions, and discuss alternative interpretations of the flexibility changes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The manuscript states that "no significant correlations between the presence of a specific mutation and patient clinicopathological parameters" were found.
- **Evidence pointer** Results section on clinicopathological characterization; Table 1
- **Concern** The statistical analysis is described only as a Pearson's chi-square test for Hardy-Weinberg equilibrium. No details are given on how the correlation between mutations and clinicopathological parameters was tested, what variables were included, or what statistical power the study had. Given the small number of novel mutations (seven across 210 patients), the study is likely underpowered to detect any meaningful associations.
- **Why it matters** The negative finding is presented without adequate statistical context, which could be misinterpreted as evidence of no association when the study may simply be underpowered.
- **Resolution test** Provide a detailed statistical analysis plan, including the tests used, variables tested, and a power analysis or clear statement of limitations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure is described as showing the distribution of novel missense mutations across the VHL protein, but the figure itself is not provided in the text. The description is insufficient to understand the domain structure and mutation positions.
- **Required correction** Provide a clear figure with domain annotations and mutation positions, or a more detailed description in the text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Table 2
- **Evidence pointer** Table 2
- **Issue** The table lists in silico prediction results but does not include the specific scores for each tool (e.g., SIFT score, PolyPhen-2 score) for all variants. The text mentions some scores but not systematically.
- **Required correction** Include all prediction scores for each variant in the table for full transparency.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions "heterozygous VHL mutations" but the manuscript does not clearly state whether all identified variants were heterozygous. This is an important detail for interpreting the results.
- **Required correction** Clarify the zygosity status of the identified variants in the results section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The phrase "impact on the formation and function of the VHL-Elongin C binding" is grammatically awkward. Similar phrasing issues appear elsewhere.
- **Required correction** Revise for clarity and grammatical correctness.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods section on MD simulation
- **Evidence pointer** Methods section
- **Issue** The description of the CABS-flex simulation is brief. The number of replicas, the temperature, and the force field parameters are not specified.
- **Required correction** Provide full simulation parameters for reproducibility.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary materials
- **Evidence pointer** Supplementary materials list
- **Issue** The supplementary materials are listed but their contents are not described in the text. It is unclear what each file contains.
- **Required correction** Add a brief description of each supplementary file in the main text.

## Risk / unsupported claims
- The claim that the identified variants "predict to affect the interface interactions between VHL and Elongin C" is unsupported by experimental evidence and relies entirely on computational predictions.
- The claim that reduced RMSF in mutants "may affect the specificity of Elongin C recognition and binding" is speculative and not directly supported by the data presented.
- The statement that "the best pose would interpret the binding affinity, binding free energy and the stability" is not a standard or well-defined criterion and is not supported by the methods described.
- The assertion that alcohol consumption "may be related to the development of this cancer" is based on a descriptive observation without statistical testing and is not supported by the data presented.
- The claim that the study "sheds focus on novel heterozygous VHL mutations" is not fully supported as zygosity is not explicitly reported for all variants.