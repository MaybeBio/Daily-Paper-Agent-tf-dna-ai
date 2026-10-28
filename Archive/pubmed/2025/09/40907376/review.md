## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific validity, methodological soundness, evidence quality, and clarity of claims as presented in the supplied material
- **Shared manuscript claim summary** The authors report a computational pipeline combining QSAR-based artificial neural network classification, molecular docking, and molecular dynamics simulation to identify phlorethopentafuhalol-A from brown algae as a potential inhibitor of RelA in oral squamous cell carcinoma, with predicted binding affinity superior to known RelA inhibitors.
- **Visible evidence base** Text descriptions of methods and results; Tables 1, 2, and 3; Figures 1 through 10 (figures referenced but not visually available to this reviewer)
- **Missing materials affecting confidence** Figure images (1-10) not provided; no supplementary data files; no dataset or code availability statement; no SMILES strings or descriptor values; no docking pose coordinates; no MD simulation parameter files or trajectory data; no validation of the ChEMBL dataset curation process

## Reviewer
- **Overall assessment** This manuscript presents a purely computational study with a linear pipeline from QSAR model development to virtual screening to docking and MD simulation. The core scientific claim, that phlorethopentafuhalol-A is a potential RelA inhibitor, rests entirely on in silico predictions without any experimental validation. While the workflow is coherent and the topic is of interest to the oral cancer and drug discovery communities, several technical issues undermine confidence in the results. The most significant problems are the lack of a clear benchmark for the docking protocol, the absence of a positive control in the MD simulations, the unexplained discrepancy between the number of compounds collected (1221 in the abstract, 1212 in the methods/results), and the lack of any experimental corroboration. The manuscript is not suitable for publication in its current form.
- **Who would be interested in the results, and why** Computational chemists and structural biologists working on NF-κB pathway inhibition, researchers in marine natural product drug discovery, and oral cancer researchers interested in RelA as a therapeutic target. The methodological pipeline may be of interest to those developing QSAR-based screening approaches for natural product libraries.
- **Major strengths** The study addresses a clinically relevant target (RelA in OSCC) with a well-established role in tumour progression. The computational workflow is comprehensive, integrating multiple complementary techniques from QSAR modelling through to MD simulation. The authors provide performance metrics for their classifier and compare it against a logistic regression benchmark. The discussion of descriptor classes and their physicochemical relevance is informative. The authors acknowledge the lack of experimental validation as a limitation.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that phlorethopentafuhalol-A has a higher binding affinity for RelA (docking score of −8.45 kcal/mol) than known RelA inhibitors (range −5.30 to −1.31 kcal/mol).
- **Evidence pointer** Results section, Molecular docking and free energy calculations; Table 2
- **Concern** The docking comparison is not a valid head-to-head comparison. The known RelA inhibitors from ChEMBL were docked to the same receptor, but the authors do not report whether the docking protocol was validated by redocking a co-crystallised ligand to reproduce its native pose. Without this validation, the absolute docking scores are not reliable indicators of binding affinity. Furthermore, the known inhibitors span a wide range of IC50 values (all <10 µM), yet the authors do not show whether their docking scores correlate with the experimental potencies. A compound with a more negative docking score than a set of weak inhibitors does not establish that it is a better inhibitor, particularly when the reference compounds are not potent binders.
- **Why it matters** The central claim of the paper, that phlorethopentafuhalol-A is a potential RelA inhibitor, depends on the reliability of the docking scores. If the docking protocol is not validated, the comparison is meaningless and the conclusion is unsupported.
- **Resolution test** The authors should validate the docking protocol by redocking a known co-crystallised ligand of RelA (or a closely related NF-κB family member) and reporting the RMSD between the docked pose and the crystal structure. They should also report docking scores for a set of known inactive compounds as a negative control, and ideally demonstrate a correlation between docking scores and experimental IC50 values for the known inhibitors.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the MD simulation confirmed that phlorethopentafuhalol-A formed a stable conformation with RelA based on trajectory analysis.
- **Evidence pointer** Results section, Molecular dynamics of RelA-phlorethopentafuhalol-A; Table 3; Figures 6-10
- **Concern** The MD simulation analysis is incomplete and the interpretation is problematic. The authors report that the RelA-phlorethopentafuhalol-A complex "began stabilising" after 40 ns, but they do not report the RMSD values for the ligand itself, only for the protein. The average RMSD for the complex (0.874 nm) is substantially higher than for the apo protein (0.374 nm), which the authors do not explain. The claim that the complex is stable is not supported by the data presented. Additionally, the authors state that the RelA-CHEMBL218434 complex "failed to achieve stable equilibrium," but the RMSD plot for this complex is not shown in the main text (only referenced as Figure 7A). The hydrogen bond analysis shows a maximum of 11 protein-ligand hydrogen bonds for phlorethopentafuhalol-A, but the average number of protein-ligand hydrogen bonds is not reported, which would be a more meaningful measure of stability. Finally, the authors do not report any free energy calculations from the MD trajectory (e.g., MM-PBSA or MM-GBSA over the trajectory), which would be a more robust measure of binding stability than visual inspection of RMSD plots.
- **Why it matters** The MD simulation is presented as confirmation of stable binding, but the analysis is insufficient to support this claim. Without proper convergence analysis, ligand RMSD, and free energy calculations, the stability conclusion is not established.
- **Resolution test** The authors should report ligand RMSD over the simulation time, the average and standard deviation of protein-ligand hydrogen bonds, and a convergence analysis (e.g., block averaging of RMSD). They should also perform MM-PBSA or MM-GBSA calculations on the MD trajectory to estimate binding free energies, and compare the stability of the phlorethopentafuhalol-A complex against the known inhibitor complex under identical simulation conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors describe the development of a QSAR-based ANN model using 25 molecular descriptors selected by chi-square testing, and report model performance metrics.
- **Evidence pointer** Methods section, Dataset selection and descriptor generation; Neural network model and evaluation; Results section, Classification model
- **Concern** The description of the model development is insufficient for reproducibility. The authors do not specify the architecture of the MLP (number of hidden layers, number of neurons per layer, activation functions), the training algorithm, the learning rate, the number of epochs, or the criteria for early stopping. The statement that "a maximum of 1000 ANNs were generated" is vague; it is unclear whether this refers to random restarts, ensemble members, or something else. The authors also do not report the hyperparameter tuning procedure. Furthermore, the dataset of 156 compounds is small for training a neural network with 25 input features, and the risk of overfitting is substantial. The authors report accuracy, sensitivity, specificity, F1 score, and MCC for the training set, but do not report these metrics for the test or validation sets, which would be more informative. The external validation using brown algae compounds is not a true external validation because there are no experimental labels for these compounds to compare against.
- **Why it matters** The QSAR model is the foundation of the entire screening pipeline. If the model cannot be reproduced or its performance is not properly evaluated, the subsequent screening results are not trustworthy.
- **Resolution test** The authors should provide full architectural and training details for the MLP, report performance metrics for the test and validation sets, and describe the hyperparameter selection procedure. They should also consider using cross-validation to assess model generalisation. If possible, the model and data should be made publicly available.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that phlorethopentafuhalol-A "could be a potential RelA inhibitor that may be useful in the treatment of OSCC on further investigation."
- **Evidence pointer** Conclusions section
- **Concern** The study is entirely computational and the authors acknowledge the lack of experimental validation. However, the claim of therapeutic potential is speculative. The docking score of −8.45 kcal/mol is modest and does not necessarily indicate a potent inhibitor. The authors do not assess drug-likeness properties (e.g., Lipinski's rule of five, ADMET predictions) for phlorethopentafuhalol-A, which would be a standard part of a computational drug discovery pipeline. The compound is a large polyphenolic molecule (phlorethopentafuhalol), and its bioavailability and cell permeability are questionable. The authors mention anti-viral, anti-diabetic, and anti-oxidant properties of this compound, but do not discuss whether these properties would be relevant or problematic for the intended use.
- **Why it matters** The translational significance of the findings is overstated relative to the evidence. A computational prediction without experimental validation, drug-likeness assessment, or consideration of the compound's physicochemical properties does not support a claim of therapeutic potential.
- **Resolution test** The authors should either temper their conclusions to reflect the purely computational nature of the study, or add in silico ADMET and drug-likeness predictions for phlorethopentafuhalol-A. Ideally, they should also discuss the feasibility of synthesising or isolating this compound for experimental testing.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that the top 25 molecular descriptors were selected based on chi-square test scores with significant P-values (P < .001 in the methods, P < .05 in the results).
- **Evidence pointer** Methods section, Neural network model and evaluation; Results section, Classification model with the crucial descriptors
- **Concern** There is an inconsistency in the reported significance threshold. The methods state P < .001, while the results state P < .05. This discrepancy needs to be resolved. Additionally, the authors report that the chosen descriptors had correlations ranging from −0.98 to 0.99. A correlation of 0.99 between two descriptors indicates near-perfect collinearity, which is problematic for model interpretation and can lead to unstable coefficient estimates. The authors do not discuss how they handled multicollinearity among the selected descriptors.
- **Why it matters** The descriptor selection procedure is a key step in the model development. Inconsistencies in the reported thresholds and unaddressed multicollinearity undermine confidence in the model's validity.
- **Resolution test** The authors should clarify the significance threshold used and justify their choice. They should also report the correlation matrix for the selected descriptors and discuss how multicollinearity was addressed (e.g., through variance inflation factor analysis or correlation-based feature elimination).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Results section
- **Evidence pointer** Abstract; Results section, Classification model
- **Issue** The abstract states that 1221 brown algae-derived compounds were assessed, while the methods and results sections state 1212 compounds were collected from the CMNDB. This numerical discrepancy is confusing.
- **Required correction** The authors should verify the correct number of compounds and ensure consistency across the abstract, methods, and results.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, Molecular dynamics simulation
- **Evidence pointer** Methods section, Molecular dynamics simulation of the RelA complex
- **Issue** The authors state that the system was placed in an orthorhombic periodic boundary box with dimensions of 1 Å. This is physically unrealistic; a box of 1 Å would be smaller than the protein itself. This is likely a typographical error.
- **Required correction** The authors should correct the box dimensions to a realistic value (e.g., 1 nm or 10 Å) and specify the distance between the protein and the box edges.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section, Molecular dynamics
- **Evidence pointer** Table 3
- **Issue** The table reports "Avg. protein H-bonds" for the apo protein and complexes, but the meaning of this metric is unclear. It is not standard practice to report the total number of intramolecular hydrogen bonds in a protein as a measure of complex stability.
- **Required correction** The authors should clarify what this metric represents and why it is relevant, or remove it and focus on protein-ligand hydrogen bonds.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section, Molecular docking
- **Evidence pointer** Results section, Molecular docking and free energy calculations
- **Issue** The sentence "The least negative glide score indicates stronger interactions" is incorrect. A more negative glide score indicates stronger binding. The authors likely meant "more negative" rather than "least negative."
- **Required correction** The authors should correct this statement to "A more negative glide score indicates stronger interactions."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, Dataset selection
- **Evidence pointer** Methods section, Dataset selection and descriptor generation
- **Issue** The authors do not specify the version of the ChEMBL database used, the date of access, or the exact search criteria for retrieving RelA inhibitors. This information is necessary for reproducibility.
- **Required correction** The authors should provide the database version, access date, and search strategy.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section, Molecular dynamics
- **Evidence pointer** Results section, Molecular dynamics of RelA-phlorethopentafuhalol-A
- **Issue** The authors state that the RelA-phlorethopentafuhalol-A complex "began stabilising" after 40 ns, but they do not report the RMSD values at specific time points or the final RMSD value. The statement is vague.
- **Required correction** The authors should report the average RMSD and standard deviation for the last 50 ns of the simulation to demonstrate convergence.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, MM-GBSA calculations
- **Evidence pointer** Methods section, MM-GBSA calculations
- **Issue** The authors state that MM-GBSA was used to calculate the free energy of binding but do not specify the dielectric constant used for the solvent or the solute, which are critical parameters for MM-GBSA calculations.
- **Required correction** The authors should specify the dielectric constants and any other relevant parameters used in the MM-GBSA calculation.

- **Technical failings that need to be addressed before the case is established** R1-M1 (docking validation), R1-M2 (MD simulation analysis), R1-M3 (model reproducibility), R1-M5 (descriptor selection inconsistency and multicollinearity)
- **Assessment against Nature-style criteria** Originality: The application of a QSAR-ANN pipeline to screen brown algae compounds against RelA is somewhat novel, but the individual components are well-established. The claim of being the "first evidence" for phlorethopentafuhalol-A as a RelA inhibitor is not verifiable from the provided material. Scientific importance: The study addresses a relevant target, but the purely computational nature and lack of experimental validation limit the immediate impact. The findings are hypothesis-generating rather than conclusive. Interdisciplinary readership: The work sits at the intersection of computational chemistry, marine natural products, and cancer biology, which could attract a broad readership, but the technical depth in each area is limited. Technical soundness: Several technical issues, as detailed above, undermine confidence in the results. The docking protocol is not validated, the MD analysis is incomplete, and the model development lacks sufficient detail for reproducibility. Readability for nonspecialists: The manuscript is generally readable, but some sections, particularly the descriptor analysis, assume familiarity with cheminformatics terminology. The figures are referenced but not available for assessment.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a plausible computational workflow, but the technical issues identified above must be resolved before the claims can be considered supported. The authors should validate their docking protocol, provide a more rigorous MD analysis, and clarify the model development details. Even after these revisions, the lack of experimental validation will limit the strength of the conclusions, and the authors should temper their claims accordingly.