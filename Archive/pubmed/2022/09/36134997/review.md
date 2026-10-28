## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific validity of the subtractive genomics pipeline, target prioritization logic, structural modeling quality, docking and MD simulation interpretations, and the strength of the conclusions drawn from the provided evidence
- **Shared manuscript claim summary** The authors report identification of a DNA-binding response-regulator protein as a novel essential, human non-homologous, non-gut flora drug target in Staphylococcus lugdunensis strain N920143 via subtractive genomics, and propose two ZINC compounds as potential inhibitors based on molecular docking and 100 ns MD simulations
- **Visible evidence base** Abstract, full methods, results and discussion sections, tables 1-5, figures 1-9 (referenced but not shown)
- **Missing materials affecting confidence** Figures 1-9 and Tables 1-5 are referenced but not provided in the supplied text. Raw data, sequence accession numbers, docking poses, MD trajectory details, and validation metrics beyond those stated in text are not available. The exact criteria for pathway uniqueness and the full list of proteins at each filtering step are not fully described.

## Reviewer
- **Overall assessment** The manuscript presents a standard subtractive genomics workflow applied to S. lugdunensis, with a clear stepwise filtering strategy. The identification of a DNA-binding response-regulator protein as a candidate target is plausible, and the docking and MD analyses are appropriate in principle. However, several technical details are missing or ambiguous, particularly regarding the homology modeling template, the definition of "druggability," the docking scoring interpretation, and the MD simulation setup. The conclusions are somewhat overstated relative to the evidence presented, especially given that the figures and tables are not available for verification. The work is of interest to the antimicrobial drug discovery community but does not yet establish a robust case for the proposed target and inhibitors.
- **Who would be interested in the results, and why** Researchers in computational drug discovery, antimicrobial resistance, and staphylococcal pathogenesis would find this work relevant. The subtractive genomics approach is widely used for target identification in neglected pathogens, and the specific focus on S. lugdunensis, a pathogen with rising clinical relevance, adds value. The proposed pipeline could serve as a template for similar studies on other pathogens.
- **Major strengths** The study addresses a clinically relevant pathogen with limited therapeutic options. The subtractive genomics workflow is systematic and uses established databases (DEG, KEGG, CELLO, DrugBank, PAIDB, HMP). The inclusion of gut flora screening is a thoughtful step to reduce off-target effects. The use of both docking and MD simulation to assess binding stability is appropriate. The manuscript is generally readable and logically structured.
- **Major Concerns** The concerns below identify gaps in evidence and interpretation that currently limit the strength of the claims.
- **Minor Comments** Several minor issues relate to clarity, missing details, and presentation that should be corrected.
- **Technical failings that need to be addressed before the case is established** R1-M1 (homology modeling validation), R1-M2 (druggability criteria), R1-M3 (docking score interpretation), R1-M4 (MD simulation temperature inconsistency), R1-M5 (conclusion overreach)
- **Assessment against Nature-style criteria** Originality: moderate. The subtractive genomics approach is well-established, and the application to S. lugdunensis is novel but not methodologically innovative. Scientific importance: moderate. The pathogen is clinically relevant, but the study is computational and lacks experimental validation, limiting immediate impact. Interdisciplinary readership: limited. The work is primarily of interest to computational biologists and antimicrobial drug developers, with less appeal to a broad biological audience. Technical soundness: mixed. The pipeline is reasonable, but several technical details are underreported or ambiguous, and the absence of figures and tables prevents full verification. Readability for nonspecialists: acceptable. The text is generally clear, though some sections assume familiarity with bioinformatics tools and molecular dynamics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is sound, but the manuscript requires substantial revision to clarify methods, provide missing validation details, and temper conclusions to match the evidence level.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of homology modeling
- **Claim pointer** The authors state that the 3D structure of the drug target was modeled and validated, with a Z-score of -3.63 and 94.7% of residues in the most favored region of the Ramachandran plot.
- **Evidence pointer** Section 2.10, Section 2.11, Section 3.7, Figures 3 and 4 (not provided)
- **Concern** The manuscript does not specify the template used for homology modeling, the sequence identity between the target and template, or the modeling method (e.g., threading, comparative modeling). The Phyre2 server can generate models, but the quality of the model depends critically on the availability of a suitable template. The Z-score of -3.63 is reported, but the ProSA Z-score range for a reliable model depends on the protein size and fold; this value alone is not sufficient to establish model quality. The Ramachandran plot statistics are provided, but the percentage of residues in the favored region (94.7%) is acceptable, yet the manuscript does not report the number of residues modeled or the coverage of the target sequence.
- **Why it matters** The reliability of the docking results depends on the accuracy of the 3D model. If the model is poorly built, the predicted binding poses and docking scores are not meaningful. Without template information and model coverage, the reader cannot assess whether the model is suitable for docking studies.
- **Resolution test** Provide the template PDB ID, sequence identity, and the modeling method. Report the model coverage (number of residues modeled vs. total length). Include the ProSA Z-score plot and a comparison with the expected Z-score range for a protein of this size. If possible, show a superposition of the model with the template to demonstrate structural conservation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Druggability assessment
- **Claim pointer** The authors state that five proteins revealed similarities with FDA-approved drugs in the DrugBank database, and that these proteins possess druggable potential.
- **Evidence pointer** Section 2.8, Section 3.5, Table 4 (not provided)
- **Concern** The manuscript does not describe the criteria used to define "druggability" based on the DrugBank search. It is unclear whether the similarity was based on sequence homology to known drug targets, or on the presence of specific domains or folds. The DrugBank database contains drug targets, but a sequence match to a drug target does not necessarily mean the protein is druggable, as druggability also depends on the presence of a suitable binding pocket. The authors do not report the E-value threshold or the percentage identity used for this search.
- **Why it matters** The selection of the DNA-binding response-regulator protein as the final target depends on the druggability filter. If the criteria are not clearly defined, the prioritization is not reproducible, and the claim that this protein is a valid drug target is weakened.
- **Resolution test** Specify the search parameters (E-value, identity cutoff) used for the DrugBank comparison. Describe how druggability was assessed beyond sequence similarity, e.g., by checking for the presence of a binding pocket or known druggable domains. Provide the list of the five proteins and their corresponding DrugBank hits in Table 4.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Docking score interpretation
- **Claim pointer** The authors report docking scores of -16.231 and -14.187 for ZINC000020192004 and ZINC000020530348, respectively, and describe these as favorable interactions.
- **Evidence pointer** Section 3.8, Table 5 (not provided)
- **Concern** The docking scores are reported without context. It is unclear what scoring function was used in MOE, what the range of scores is for known active compounds against similar targets, and whether these scores are significantly better than those of decoy compounds. The authors do not report the docking scores of the other top 100 compounds, so it is not possible to assess whether these two compounds are outliers or within a normal distribution. Additionally, the manuscript does not describe the preparation of the receptor and ligands, such as protonation states, energy minimization, or the selection of the active site.
- **Why it matters** Docking scores are only meaningful when compared to a baseline or known inhibitors. Without this context, the claim that these compounds are "most favorable" is not supported. The lack of methodological detail also prevents reproducibility.
- **Resolution test** Report the scoring function used in MOE and the range of docking scores for all 10,000 compounds. Provide the scores for the top 100 compounds to show the distribution. Describe the receptor and ligand preparation steps, including protonation, energy minimization, and active site definition. If possible, dock known inhibitors of similar response regulators as a positive control.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** MD simulation setup and interpretation
- **Claim pointer** The authors state that the two compounds showed more stable behavior when bound to the drug target than the apo state, based on RMSD, RMSF, and RoG analyses over 100 ns simulations.
- **Evidence pointer** Section 2.13, Section 3.9, Figures 6-9 (not provided)
- **Concern** The MD simulation temperature is stated as 325 K in Section 2.13, but the physiological temperature is typically 310 K. The authors also state in Section 2.13 that the systems were heated from 0 to 325 K, and the Langevin dynamics approach was used at 310 K, which is inconsistent. The manuscript does not report the number of water molecules, the box size, the salt concentration, or the equilibration protocol. The RMSD values are reported as 1.6 and 1.5 for the complexes and 1.6 for the apo-enzyme, but the units are not specified (likely angstroms). The RMSF analysis is described qualitatively, but the specific residues with high fluctuations are not quantified. The RoG values are reported as 16.2, 16.1, and 16.01, but again without units or error bars.
- **Why it matters** The MD simulation is a key part of the study, and the results are used to support the stability claims. Inconsistent temperature reporting and missing simulation details undermine the credibility of the results. Without proper reporting, the reader cannot assess whether the simulations were performed correctly or whether the conclusions are justified.
- **Resolution test** Clarify the simulation temperature and ensure consistency between the heating and production phases. Report the full simulation setup, including box dimensions, water model, salt concentration, and equilibration steps. Provide RMSD, RMSF, and RoG plots with error bars or standard deviations. Specify the units for all reported values.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Conclusion overreach
- **Claim pointer** The authors conclude that the identified compounds are "lead compounds" and that the drug target is "promising" based solely on computational analyses.
- **Evidence pointer** Section 4
- **Concern** The conclusions state that the compounds are lead candidates and that the target is promising, but no experimental validation is provided. The manuscript does not include any in vitro or in vivo data to support the efficacy or safety of the proposed compounds. The term "lead compound" typically implies some level of experimental validation, which is absent here. The conclusion also mentions four targets (4-hydroxtetrahydrodipicolinate reductase, signal peptidase, DNA-binding response regulator, and genome polyprotein) but the results section only describes the DNA-binding response regulator in detail.
- **Why it matters** Overstating conclusions based on computational predictions alone can mislead readers and is not consistent with the standards of evidence in drug discovery. The manuscript should clearly distinguish between computational predictions and experimentally validated findings.
- **Resolution test** Revise the conclusions to clearly state that these are computational predictions requiring experimental validation. Remove the term "lead compounds" or qualify it as "potential lead compounds." Clarify the status of the other three targets mentioned in the conclusion, as they are not described in the results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The strain name is inconsistently reported. In Section 2.1, the strain is referred to as "N920143," but in Section 3.1, it is written as "N90143." This is likely a typographical error.
- **Required correction** Correct the strain name to "N920143" throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.12
- **Evidence pointer** Section 2.12
- **Issue** The docking protocol in MOE is described with several parameters, but the specific version of MOE and the exact settings for each parameter are not provided. The phrase "different parameters like Refinement, Rigid Receptor, Rescoring, London dG, Placement, and Triangle Matcher functions" is vague.
- **Required correction** Provide the exact MOE version and the specific values for each parameter used in the docking run.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Section 3.9
- **Evidence pointer** Section 3.9
- **Issue** The RMSD, RMSF, and RoG values are reported as single numbers without error bars or standard deviations. This makes it difficult to assess the variability of the simulations.
- **Required correction** Report the average values with standard deviations or show the time series plots with error bars.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.13
- **Evidence pointer** Section 2.13
- **Issue** The MD simulation section does not mention the number of replicates. Single simulations are generally not sufficient to draw robust conclusions about stability.
- **Required correction** State whether the simulations were performed in triplicate or more, and if not, acknowledge this as a limitation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 2.13
- **Evidence pointer** Section 2.13
- **Issue** The AMBER force field is stated as "AMBER14," but the correct name is "ff14SB" for proteins. The force field name should be specified accurately.
- **Required correction** Correct the force field name to "ff14SB" or the specific variant used.

## Risk / unsupported claims
- The claim that the DNA-binding response-regulator protein is a "novel drug target" is not fully supported, as the manuscript does not demonstrate that this protein has not been previously proposed as a target in other organisms.
- The claim that ZINC000020192004 and ZINC000020348 are "potent inhibitors" is unsupported, as no experimental inhibition data are provided. The term "potent" is not justified by docking scores alone.
- The claim that the identified compounds "revealed more stable behavior" than the apo state is based on single simulations and lacks statistical rigor.
- The conclusion mentions four targets, but only one is described in detail in the results, leaving the status of the other three unclear.
- The manuscript does not provide the actual figures and tables, so the results presented in the text cannot be independently verified.