## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report computational screening of Satureja hortensis phytochemicals against the AP-1 (FOS/JUN) transcription factor complex, with molecular docking identifying cedrelanol and allo-aromadendrene as top binders, followed by a 100-ns molecular dynamics simulation and MM/GBSA analysis supporting cedrelanol as a stable and energetically favorable AP-1 modulator with potential relevance to mitigating valproic acid teratogenicity
- **Visible evidence base** Abstract text only; specific numerical results for docking scores, RMSD values, and binding free energy are stated but no methodological details, statistical measures, or validation data are visible
- **Missing materials affecting confidence** Full manuscript text, methods section, docking protocols, force field parameters, simulation setup, convergence criteria, control experiments, structural validation, and any comparative or experimental data

## Reviewer

- **Overall assessment** The abstract presents a straightforward computational docking and simulation study with plausible methodology, but the evidence provided is insufficient to establish the central claims. The reported results are limited to predicted binding affinities and a single simulation trajectory, with no experimental validation, no comparison to known AP-1 inhibitors beyond a single reference, and no assessment of selectivity or functional relevance. The conclusion that cedrelanol is a "potent AP-1 modulator" is not supported by the visible evidence, which only demonstrates computational binding predictions. The manuscript may have merit as a preliminary in silico screening report, but the current abstract does not provide enough detail to assess technical rigor or biological significance.
- **Who would be interested in the results, and why** Researchers in computational drug discovery, teratology, and phytochemistry may find preliminary interest. Those studying valproic acid mechanisms or seeking natural product leads for transcription factor modulation could view this as a starting point, though the lack of experimental follow-up limits broader appeal.
- **Major strengths** The study addresses a clinically relevant problem, namely VPA teratogenicity, and applies a standard computational pipeline combining docking, molecular dynamics, and binding free energy calculations. The use of a reference inhibitor for comparison is appropriate. The focus on a specific transcription factor complex provides a clear mechanistic hypothesis.
- **Major Concerns** The concerns below identify that the core claims are not established from the provided evidence, primarily due to missing methodological detail, lack of validation, and overinterpretation of computational predictions.
- **Minor Comments** Several clarifications and additions are needed to improve reproducibility and interpretation.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is limited, as computational docking of phytochemicals against transcription factors is a common approach, and the specific target and compound class do not represent a conceptual advance. Scientific importance is moderate at best, given that no experimental evidence links the predicted binding to functional AP-1 inhibition or teratogenicity mitigation. Interdisciplinary readership is narrow, primarily computational chemists and teratologists, with limited appeal to a broad biological or clinical audience. Technical soundness cannot be fully assessed from the abstract, but the absence of key methodological details and validation raises concerns. Readability for nonspecialists is adequate, though the abstract uses technical terms without sufficient context for a general audience.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that molecular docking predicted cedrelanol and allo-aromadendrene bind the AP-1 complex with affinities of -7.7 kcal/mol, exceeding the reference inhibitor SR11302 at -7.3 kcal/mol
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The docking results are presented as single affinity values with no indication of docking protocol, scoring function, pose selection criteria, or reproducibility. No error estimates, replicate runs, or statistical comparisons are provided. The difference between -7.7 and -7.3 kcal/mol is small and may not be significant given typical docking score variability.
- **Why it matters** Without methodological detail and error assessment, the claimed superiority of the top ligands over the reference inhibitor cannot be evaluated. The conclusion that these compounds are better binders is not supported by the visible evidence.
- **Resolution test** Provide full docking methodology, including software, scoring function, grid parameters, and validation against known binders. Report multiple docking runs with standard deviations and statistical significance tests for the affinity differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that a 100-ns molecular dynamics simulation of the cedrelanol-1FOS complex confirmed stable binding, with protein backbone RMSD between 0.8-1.2 A and ligand RMSD below 1.3 A throughout the trajectory
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** A single 100-ns trajectory is insufficient to establish binding stability. No information is provided on force field parameters, water model, temperature and pressure coupling, equilibration protocol, or convergence assessment. RMSD ranges alone do not demonstrate stable binding, as they do not address ligand contacts, hydrogen bonding, or conformational changes in the binding site.
- **Why it matters** The claim of "stable binding" is central to the conclusion that cedrelanol is a viable modulator. Without evidence of simulation quality and convergence, the stability claim is unsubstantiated.
- **Resolution test** Provide full simulation setup details, include multiple independent replicates or extended simulation times, and report additional metrics such as ligand root mean square fluctuation, contact analysis, and binding site conformational dynamics. Show convergence plots and compare with a control simulation of an unbound or negative control system.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation
- **Claim pointer** The abstract claims that MM/GBSA binding free energy analysis indicated a highly favorable DeltaG_binding of -75.04 kcal/mol for the cedrelanol-1FOS complex
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The MM/GBSA value of -75.04 kcal/mol is presented as a single number with no indication of the calculation protocol, entropy contributions, or standard deviation. MM/GBSA values are known to be system-dependent and can vary widely based on the chosen parameters. The magnitude is unusually large for a small molecule binding to a protein, which raises questions about the calculation setup.
- **Why it matters** The binding free energy is used to support the claim of potent modulation. An unvalidated and potentially overestimated value does not provide reliable evidence for the conclusion.
- **Resolution test** Report the MM/GBSA calculation details, including the number of frames used, the energy components, and the standard deviation. Compare the value with those obtained for the reference inhibitor and a decoy compound. Discuss the limitations of MM/GBSA and provide experimental or literature-based context for the expected binding affinity range.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim scope
- **Claim pointer** The abstract concludes that cedrelanol is a "potent AP-1 modulator" and that S. hortensis phytochemicals are "plausible inhibitors of AP-1" with potential implications for mitigating VPA teratogenicity
- **Evidence pointer** Abstract, Conclusion section; location not provided
- **Concern** The conclusion extends beyond the computational evidence. Docking and simulation predictions do not establish functional modulation of AP-1 activity, and no experimental data on transcriptional activity, cell-based assays, or animal models are presented. The link to VPA teratogenicity mitigation is speculative.
- **Why it matters** The central claim of the manuscript is that these compounds can modulate AP-1 and potentially mitigate VPA teratogenicity. This claim is not supported by the visible evidence, which only shows in silico binding predictions.
- **Resolution test** Provide experimental validation, such as reporter gene assays, electrophoretic mobility shift assays, or cell-based studies demonstrating AP-1 inhibition. If experimental data are not available, revise the conclusion to clearly state that the findings are preliminary computational predictions requiring further validation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Background section
- **Evidence pointer** Abstract, Background; location not provided
- **Issue** The background states that VPA induces defects "in part via aberrant activation" of AP-1, but no citation or mechanistic detail is provided in the abstract.
- **Required correction** Add a citation or briefly describe the evidence linking VPA to AP-1 activation to contextualize the study.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract, Methods section
- **Evidence pointer** Abstract, Methods; location not provided
- **Issue** The methods section is a single sentence and does not specify the number of phytochemicals screened, the source of the compound library, or the criteria for selecting top ligands.
- **Required correction** Provide the number of compounds screened and the selection criteria for the top hits.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, Results; location not provided
- **Issue** The abstract reports docking scores for cedrelanol and allo-aromadendrene but does not state which compound was used for the molecular dynamics simulation, though the conclusion focuses on cedrelanol.
- **Required correction** Clarify whether both compounds were simulated or only cedrelanol, and justify the selection.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, Results; location not provided
- **Issue** The RMSD values are reported without units in the text, though the context implies angstroms.
- **Required correction** Ensure units are explicitly stated for all reported values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Abstract, Conclusion section
- **Evidence pointer** Abstract, Conclusion; location not provided
- **Issue** The conclusion contains redundant phrasing, with "potent AP-1 modulator" and "plausible inhibitors" used in close succession, which weakens the precision of the claims.
- **Required correction** Revise the conclusion to use consistent and precise language, distinguishing between computational predictions and established effects.

## Risk / unsupported claims

- The claim that cedrelanol and allo-aromadendrene bind AP-1 with higher affinity than SR11302 is unsupported due to lack of methodological detail and statistical analysis
- The claim that the molecular dynamics simulation confirmed stable binding is unsupported due to the absence of simulation setup details and convergence assessment
- The claim that the MM/GBSA binding free energy of -75.04 kcal/mol indicates a highly favorable interaction is unsupported without calculation details and validation
- The claim that cedrelanol is a "potent AP-1 modulator" is unsupported, as no functional or experimental evidence is provided
- The claim that S. hortensis phytochemicals have potential implications for mitigating VPA teratogenicity is speculative and not supported by the visible evidence
- The overall conclusion that these compounds are plausible inhibitors of AP-1 is not established from the provided computational predictions alone