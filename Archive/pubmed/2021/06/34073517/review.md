## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, conclusions) and bibliographic metadata
- **Assessment boundary** Computational methodology, simulation design, data analysis, and interpretation as presented; no experimental validation data are included
- **Shared manuscript claim summary** The authors describe a computational workflow combining molecular dynamics simulations, MM-GBSA free energy calculations, and residue scanning with a non-natural amino acid database to design twelve combinatorial peptides targeting the HOX-PBX1 protein-protein interaction. They report that eleven of these peptides show promising predicted binding free energies compared to reference peptides HOXA9 hexapeptide and HTX001 core peptide.
- **Visible evidence base** Tables 1-6, Figures 4-6, Supplementary Figures S1-S3, Supplementary Tables S1-S5, methods descriptions
- **Missing materials affecting confidence** PDB structure preparation details, force field parameterization specifics for non-standard residues, convergence criteria for MD simulations, raw trajectory data, error estimates for MM-GBSA values, statistical analysis of replicate simulations, and any experimental validation data

## Reviewer
- **Overall assessment** The manuscript presents a systematic computational approach to peptide design targeting a clinically relevant protein-protein interaction. The workflow is logical and builds on established methods, but several technical aspects require clarification and additional analysis before the conclusions can be considered robust. The central claim that eleven peptides show "promising" binding properties rests entirely on MM-GBSA predictions without experimental validation or adequate error analysis. The study is potentially useful as a computational screening methodology, but the current evidence does not establish that these peptides will function as intended in biological systems.
- **Who would be interested in the results, and why** Researchers in computational drug design, peptide therapeutics, and cancer biology would find this methodology relevant. Those working on protein-protein interaction inhibitors and non-standard amino acid incorporation into bioactive peptides would be the primary audience. The HOX-PBX interaction is a validated oncology target, so groups focused on transcriptional regulation in cancer may also be interested.
- **Major strengths** The study addresses a clinically relevant target with a rational computational design strategy. The use of non-natural amino acids expands the chemical space beyond standard peptide design. The workflow integrates multiple established computational tools in a coherent pipeline. The authors appropriately reference experimental context, including the clinical-stage peptide HTL001, providing a benchmark for their predictions.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: moderate. The combination of non-standard amino acid scanning with MD and MM-GBSA for this specific target is somewhat novel, but each individual method is well established. Scientific importance: potentially relevant to cancer therapeutics, but the lack of experimental validation limits current impact. Interdisciplinary readership: would appeal to computational chemists and structural biologists, with limited accessibility to broader cancer biology audience. Technical soundness: several concerns identified below undermine confidence in the quantitative conclusions. Readability for nonspecialists: the manuscript is generally clear but assumes familiarity with computational chemistry terminology without sufficient explanation for a broad readership.
- **Recommendation posture** Currently not established from the provided evidence. The computational workflow is reasonable, but the central claims require additional technical validation and error analysis before the conclusions can be accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MM-GBSA calculations provide ΔGbinding average values that can be used to compare and select promising peptide candidates.
- **Evidence pointer** Tables 2, 3, 4, 5; Section 2.2, 2.3, 2.4; Section 3.4
- **Concern** The manuscript reports single MM-GBSA values for each peptide without any measure of statistical uncertainty. MM-GBSA calculations are known to be sensitive to trajectory length, frame sampling, and the choice of dielectric constant and solvation model. No standard deviation, standard error, or confidence interval is provided for any ΔGbinding value. Additionally, the number of frames used for averaging is not specified. Without error estimates, it is impossible to determine whether the differences between peptides are statistically meaningful or within the noise of the method.
- **Why it matters** The entire peptide selection process depends on comparing ΔGbinding values. If the differences between candidates are smaller than the typical MM-GBSA error (often 1-3 kcal/mol or more), the ranking of peptides and the conclusion that eleven are "promising" are not justified.
- **Resolution test** Provide standard deviations or standard errors for all reported ΔGbinding values, specify the number of frames used in averaging, and perform statistical significance testing (e.g., bootstrap or t-test) to demonstrate that the selected peptides are significantly better than the reference peptides.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the residue scanning was performed using the SwissSidechain database and that mutations were selected based on ΔΔGaffinity and ΔΔGstability values with a cutoff of −3.0 kcal/mol for affinity.
- **Evidence pointer** Section 2.3; Section 3.2; Table 3
- **Concern** The manuscript does not report the actual ΔΔGaffinity and ΔΔGstability values for the selected mutations. Only the final MM-GBSA values are shown. It is unclear how many mutations passed the −3.0 kcal/mol cutoff at each position, how the "first four most promising" were ranked, and whether the cutoff was applied to affinity, stability, or both. The relationship between the residue scanning predictions and the subsequent MD/MM-GBSA results is not explicitly discussed. Furthermore, the authors state that 119, 10, 52, 35, and 5 acceptable mutations were found for positions X1-X5 respectively, but the criteria for "acceptable" are not fully defined.
- **Why it matters** The residue scanning step is a critical filter in the design pipeline. Without transparency in the selection criteria and the intermediate data, the reader cannot evaluate whether the chosen mutations are justified or whether the process introduced bias.
- **Resolution test** Provide a supplementary table listing all mutations that passed the cutoff at each position, with their ΔΔGaffinity and ΔΔGstability values. Clearly state the ranking criteria and explain how the final four per position were selected.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the designed peptides maintain key interactions with PBX1, particularly the tryptophan residue remaining "stuck within the hydrophobic pocket of PBX1 during all the twelve MD simulations."
- **Evidence pointer** Section 2.4; Figures 4-6; Supplementary Tables S2, S3
- **Concern** The manuscript does not provide quantitative measures of interaction stability. The statement about tryptophan remaining in the hydrophobic pocket is qualitative. No distance time series, contact maps, or occupancy calculations are shown. The interaction analysis appears to be based on visual inspection of representative frames rather than systematic trajectory analysis. Additionally, the authors do not report root-mean-square fluctuation (RMSF) values for the peptides or the protein binding site, which would be standard metrics for assessing binding stability.
- **Why it matters** The conclusion that the peptides form stable complexes relies on the assumption that key interactions are maintained throughout the simulation. Without quantitative evidence, this claim is not supported.
- **Resolution test** Provide time series of key distances (e.g., tryptophan indole to PBX1 pocket residues), hydrogen bond occupancy percentages, and RMSF plots for peptide and protein residues. Report the fraction of simulation time during which key contacts are maintained.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the designed peptides have potential to prevent HOX-PBX1-associated cancers and that the most promising peptides "will be soon synthesized" for testing.
- **Evidence pointer** Abstract; Section 4
- **Concern** The manuscript provides no experimental validation whatsoever. All conclusions are based on computational predictions. While the authors acknowledge that synthesis and testing are planned, the title and abstract imply a stronger claim than the evidence supports. The phrase "potentially able to prevent" is appropriately hedged, but the overall framing suggests that the computational results are sufficient to establish therapeutic potential. No discussion of potential off-target effects, cell permeability (beyond PSA and logP calculations), metabolic stability, or toxicity is provided.
- **Why it matters** Computational predictions of binding affinity do not translate directly to biological activity. Without experimental data, the clinical relevance of these peptides remains entirely speculative.
- **Resolution test** Either temper the conclusions to clearly state that these are computational predictions requiring experimental validation, or include preliminary experimental data (e.g., binding assays, cell viability studies) to support the claims.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Section 3.1
- **Issue** The protein preparation section mentions "eventual bonds to metals were broken" and "formal charges to metals and neighbouring atoms were corrected" but does not specify which metals are present in the PDB structure 1PUF or how their protonation states were determined.
- **Required correction** Specify the metal ions present in the structure and the criteria used for assigning their charge states.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Section 3.3
- **Issue** The MD simulation parameters are described but key details are missing, including the specific version of Desmond, the equilibration protocol, the number of steps for each relaxation phase, and the criteria for determining system equilibration.
- **Required correction** Provide a complete description of the simulation protocol, including all relaxation steps and equilibration criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Tables 2-5
- **Evidence pointer** Tables 2, 3, 4, 5
- **Issue** The ΔGbinding values are reported with four decimal places, which implies a precision that is not supported by the MM-GBSA method. Typical MM-GBSA errors are on the order of 1-2 kcal/mol.
- **Required correction** Report values with appropriate significant figures (e.g., one decimal place) and include error estimates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4, Table 5
- **Issue** The text states that the sixth peptide was excluded because it showed a higher ΔGbinding value, but the threshold for exclusion is not defined. It is unclear whether the exclusion was based on a specific cutoff or a relative comparison.
- **Required correction** State the explicit criterion used to exclude the sixth peptide.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.4, Table 6
- **Evidence pointer** Table 6
- **Issue** The PSA and logP values are presented as indicators of cell permeability, but no comparison to known cell-penetrating peptides or established permeability thresholds is provided.
- **Required correction** Add context for interpreting these values, such as reference ranges for cell-permeable peptides.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Section 1
- **Issue** The introduction mentions the clinical-stage peptide HTL001 but does not provide details on its development, current trial phase, or reported efficacy data. This context would help readers assess the significance of the present work.
- **Required correction** Add a brief summary of HTL001's development status and any published clinical results.

## Risk / unsupported claims
- The claim that eleven combinatorial peptides are "promising" is unsupported without statistical error analysis and significance testing of the MM-GBSA values.
- The claim that the designed peptides "potentially" prevent HOX-PBX1-associated cancers is not supported by any experimental evidence and should be framed strictly as a computational hypothesis.
- The statement that tryptophan remains "stuck within the hydrophobic pocket" during all simulations is not quantitatively demonstrated.
- The assertion that the designed peptides maintain key interactions with PBX1 is based on qualitative analysis and requires quantitative trajectory analysis.
- The relevance of the PSA and logP values to actual cell permeability is asserted without experimental validation or comparison to established benchmarks.
- The selection of the "first four most promising" non-standard amino acids per position is not transparently justified, as the underlying ΔΔG values are not reported.