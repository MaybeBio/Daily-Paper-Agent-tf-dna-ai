## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Computational identification of natural product inhibitors against Oct4, including virtual screening, molecular docking, molecular dynamics simulations, and binding free energy calculations
- **Shared manuscript claim summary** The authors employed receptor-based virtual screening of natural product databases, followed by molecular docking, MM/GBSA binding free energy calculations, and molecular dynamics simulations to identify two compounds (ZINC02145000 and ZINC32124203) that stably bind to the POUHD domain of Oct4, potentially impeding glioma stem cell mechanisms.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results and Discussion, Conclusion, figure legends referenced in text
- **Missing materials affecting confidence** Figures and tables referenced but not provided; supporting information files not available; no experimental validation data; no compound structures or chemical details

## Reviewer
- **Overall assessment** This manuscript presents a computational workflow for identifying natural product inhibitors against the Oct4 POUHD domain, a potentially important target in glioma stem cell biology. The study combines multiple in silico approaches including homology modeling, virtual screening, induced fit docking, MM/GBSA calculations, and molecular dynamics simulations. While the methodological pipeline is comprehensive and the topic is of interest, the manuscript has several significant limitations. The most critical issue is the lack of experimental validation, which is acknowledged by the authors but limits the strength of the conclusions. Additionally, the reported simulation results show high structural instability of the free protein, which raises questions about the reliability of the model and the interpretation of ligand-induced stabilization. The manuscript would benefit from clearer presentation of results, more rigorous analysis of the simulation data, and a more cautious interpretation of the findings.

- **Who would be interested in the results, and why** Researchers in computational drug discovery, particularly those focused on cancer stem cell targets, would find this study relevant. The work also addresses the glioma stem cell field, where Oct4 is recognized as a key regulator. Scientists interested in natural product-based therapeutics for glioblastoma may find the identified compounds worth pursuing. However, the lack of experimental validation means the impact is limited to computational predictions that require further investigation.

- **Major strengths** The study employs a multi-step computational screening pipeline that is methodologically sound and follows established protocols in structure-based drug discovery. The authors appropriately use multiple validation approaches including induced fit docking, MM/GBSA binding free energy calculations, and molecular dynamics simulations to cross-verify their findings. The focus on natural product databases is relevant for drug discovery. The identification of compounds that interact with both POU subdomains is an interesting observation that could have functional implications.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence strength
  - **Claim pointer** The manuscript claims that ZINC02145000 and ZINC32124203 "can impede the Oct4 function" and "may help to improve overall survival, diminish tumor relapse, and achieve a cure not only in deadly disease GBM but also in other cancers with minimal side effects."
  - **Evidence pointer** Conclusion section
  - **Concern** The central claim that these compounds can impede Oct4 function and have therapeutic potential is based entirely on computational predictions. No experimental validation is provided, such as cell-based assays, binding experiments, or functional studies. The conclusion overstates the significance of in silico findings without acknowledging the substantial gap between computational predictions and biological activity.
  - **Why it matters** Computational docking and simulation studies can identify potential binders, but they cannot establish functional inhibition, cellular activity, or therapeutic efficacy. The claim that these compounds could "achieve a cure" for GBM and other cancers is not supported by the evidence presented and could be misleading to readers.
  - **Resolution test** The authors should either provide experimental validation (e.g., Oct4 reporter assays, proliferation studies in glioma stem cells, binding affinity measurements) or substantially temper the conclusions to reflect that these are preliminary computational predictions requiring experimental verification.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript states that the modeled Oct4 protein was "quite unstable throughout the simulation with an RMSD value from 6Å to 17Å" and that the free protein showed high fluctuation.
  - **Evidence pointer** Results and discussion, "Protein structure prediction and stability evolution" and "Interaction and stability validation of selected leads through molecular dynamics simulation" sections
  - **Concern** The reported RMSD values of 6-17 Å for the free protein are extremely high and indicate that the modeled structure is not stable under simulation conditions. This raises serious questions about the quality of the homology model and whether it represents a physiologically relevant conformation. The authors attribute this instability to the presence of disordered regions, but such large deviations suggest potential problems with the modeling approach or simulation setup.
  - **Why it matters** If the free protein is highly unstable, the binding modes and interactions observed in ligand-bound simulations may be artifacts of the unstable starting structure rather than genuine binding characteristics. The comparison between free and bound states becomes unreliable when the free state itself is not well-defined.
  - **Resolution test** The authors should provide additional analysis of the model quality, including validation of the simulation setup, assessment of whether the system reached equilibrium, and comparison with experimentally determined structures of Oct4 or closely related POU domain proteins. They should also consider whether the high RMSD reflects genuine conformational flexibility or technical issues.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The manuscript describes a virtual screening workflow that identified 13 compounds from databases containing 155,819, 55,958, and 8,395 compounds respectively.
  - **Evidence pointer** Materials and methods, "High throughput virtual screening" section; Results, "Druggable pocket prediction, ligand filtration, and identification of potent inhibitors through virtual screening" section
  - **Concern** The manuscript does not provide sufficient details on the specific parameters used for ADME filtering, the criteria for selecting the 13 compounds from the 30 top hits, or the complete list of compounds tested. The compound identifiers are mentioned but the chemical structures and properties are not presented in the main text.
  - **Why it matters** Reproducibility is a fundamental requirement for computational studies. Without complete details on the screening parameters, selection criteria, and compound information, other researchers cannot replicate the study or fully evaluate the validity of the findings.
  - **Resolution test** The authors should provide a complete list of the 13 selected compounds with their structures, the ADME filtering criteria with specific cutoff values, and a clear description of the selection process from the initial hits to the final candidates.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript claims that ZINC02145000 and ZINC32124203 "established communication not only with the POUHD domain but also with the POUS domain" based on MD simulation analysis.
  - **Evidence pointer** Results, "Interaction and stability validation of selected leads through molecular dynamics simulation" section
  - **Concern** The evidence for inter-domain communication is based on visual inspection of simulation trajectories and hydrogen bond analysis. The manuscript does not provide quantitative measures of allosteric communication or domain-domain interactions. The claim that these compounds can "block both domain functions" is not supported by functional data.
  - **Why it matters** The proposed mechanism of action involving simultaneous targeting of both POU subdomains is a key finding of the study. Without robust evidence for this interaction and its functional consequences, this conclusion remains speculative.
  - **Resolution test** The authors should provide quantitative analysis of domain-domain interactions, such as distance measurements between the compound and residues in both domains over the simulation trajectory, free energy decomposition analysis, or mutational studies to confirm the importance of specific interactions.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract section
  - **Issue** The abstract is dense and contains multiple technical terms without sufficient context. The phrase "incredible potency" is subjective and not supported by quantitative data.
  - **Required correction** Revise the abstract to be more accessible to a broader readership, and replace subjective descriptors with quantitative measures where possible.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods
  - **Evidence pointer** Materials and methods, "Protein structure prediction and preparation" section
  - **Issue** The manuscript states that 50 models were generated but does not explain why this specific number was chosen or how the best model was selected beyond the DOPE score. Additional validation metrics (e.g., PROCHECK, ERRAT) are mentioned but the specific values for the selected model are not clearly presented.
  - **Required correction** Provide the complete validation results for the selected model, including the specific PROCHECK, ERRAT, and ProSA values, and explain the model selection criteria more clearly.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results
  - **Evidence pointer** Results, "Druggable pocket prediction, ligand filtration, and identification of potent inhibitors through virtual screening" section
  - **Issue** The manuscript mentions that 30 compounds were obtained from virtual screening but only 13 were selected for further analysis. The criteria for this selection are described as "visual examination" but the specific structural or interaction features that led to exclusion of the other 17 compounds are not detailed.
  - **Required correction** Provide a clear description of the visual inspection criteria and the specific reasons for excluding the other compounds.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Discussion
  - **Evidence pointer** Results, "Interaction and stability validation of selected leads through molecular dynamics simulation" section
  - **Issue** The discussion of why some compounds with higher docking scores showed less stable MD simulations is superficial. The authors note the discrepancy but do not provide a mechanistic explanation.
  - **Required correction** Expand the discussion to address the relationship between docking scores, binding free energies, and simulation stability, and consider factors such as solvation effects, entropic contributions, or conformational selection.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods
  - **Evidence pointer** Materials and methods, "Molecular dynamics simulation" section
  - **Issue** The manuscript does not specify the force field parameters used for the ligands in the MD simulations, which is critical for reproducibility.
  - **Required correction** Provide details on how ligand parameters were generated (e.g., using which tool and force field).

  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results
  - **Evidence pointer** Results, "Interaction and stability validation of selected leads through molecular dynamics simulation" section
  - **Issue** The manuscript mentions water-mediated interactions but does not provide details on the water molecules involved or the persistence of these interactions.
  - **Required correction** Provide additional analysis of water-mediated interactions, including occupancy and residence times.

## Risk / unsupported claims
- The claim that the identified compounds "can impede the Oct4 function" and "may help to improve overall survival, diminish tumor relapse, and achieve a cure" for GBM and other cancers is unsupported by the computational evidence presented. No experimental validation is provided.
- The claim that ZINC02145000 and ZINC32124203 can "block both domain functions" is not supported by functional data.
- The statement that the compounds have "incredible potency" is subjective and not quantified.
- The biological significance of the identified compounds for glioma stem cell mechanisms is inferred from computational predictions without experimental correlation.
- The manuscript does not provide evidence that the identified compounds would have minimal side effects, as claimed in the conclusion.
- The stability of the homology model is questionable given the very high RMSD values reported for the free protein, which undermines confidence in the simulation results.