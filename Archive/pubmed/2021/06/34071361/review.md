## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided manuscript
- **Shared manuscript claim summary** The authors use molecular docking, molecular dynamics (MD) simulations, and MM/PBSA calculations to compare the binding of iron protoporphyrin IX (Heme, agonist) and cobalt protoporphyrin IX (CoPP, antagonist) to the nuclear receptor REV-ERBβ. They report that Heme binds more strongly than CoPP, that CoPP induces conformational changes in the ligand-binding domain (LBD), particularly in Helix-11, and that these changes disrupt NCoR corepressor recruitment, providing a mechanistic explanation for the antagonistic activity of CoPP.
- **Visible evidence base** Full text including abstract, introduction, results (Sections 2.1–2.6), discussion, conclusions, and methods (Sections 4.1–4.6). Figures and tables are referenced but not provided in the submitted material.
- **Missing materials affecting confidence** Figures 1–14 and Tables 1–4 are referenced but not included. This limits the ability to independently verify the reported structural data, docking poses, RMSD plots, binding-pocket volume calculations, and interaction diagrams.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and interesting question: how a subtle change in the metal center of protoporphyrin IX (Fe to Co) switches the ligand from an agonist to an antagonist of REV-ERBβ. The computational approach is appropriate in principle, and the finding that CoPP disrupts the NCoR-binding surface via conformational changes in Helix-11 is mechanistically plausible. However, the evidence as presented is incomplete and in places internally inconsistent. Several key claims are not supported by the data shown, and the manuscript would require substantial revision and additional analysis before the conclusions can be considered established.
- **Who would be interested in the results, and why** Researchers in computational chemistry, structural biology, and cancer biology, particularly those studying nuclear receptors, porphyrin-based therapeutics, and the molecular basis of agonist/antagonist discrimination. The work may also be of interest to medicinal chemists designing metalloporphyrin derivatives for cancer therapy or imaging.
- **Major strengths** The study addresses a clinically relevant problem with a clear hypothesis. The use of multiple computational methods (docking, MD, MM/PBSA, protein-peptide docking) is appropriate. The comparison between Heme and CoPP in both agonist and antagonist receptor conformations is a sensible design. The focus on Helix-11 and corepressor recruitment provides a concrete mechanistic link between ligand identity and functional outcome.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (force field parameterization), R1-M2 (inconsistent binding energy reporting), R1-M3 (unsubstantiated Helix-11 claim), R1-M4 (missing validation of protein-peptide docking), R1-M5 (incomplete statistical reporting).
- **Assessment against Nature-style criteria** Originality: moderate. The question is interesting but the approach is largely standard. Scientific importance: potentially high if the mechanism is correct, but the current evidence is insufficient. Interdisciplinary readership: the topic bridges chemistry, biology, and medicine, but the presentation is too specialized and lacks context for a broad audience. Technical soundness: several methodological issues and missing validations undermine confidence. Readability for nonspecialists: the manuscript is written in a technical style that assumes familiarity with MD simulations and nuclear receptor biology; key concepts are not explained for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential but requires major revisions, additional analyses, and clarification of inconsistencies before the claims can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the AMBER99SB-ILDN force field was used for the protein and that the ligand was parameterized using ACPYPE for protoporphyrin IX and ForceGen for the metal centers.
- **Evidence pointer** Section 4.4
- **Concern** The parameterization of metalloporphyrins is notoriously challenging. The use of ACPYPE for the porphyrin ring and ForceGen for the metal center implies a split parameterization, but the manuscript does not describe how the metal-ligand bonds, angles, and electrostatic interactions were treated. No validation of the ligand parameters (e.g., comparison with quantum mechanical calculations or experimental data) is provided.
- **Why it matters** The central claim of the paper is that the metal center (Fe vs Co) determines agonist versus antagonist behavior. If the metal parameters are not accurately modeled, the entire simulation may be biased, and the observed differences could be artifacts of the parameterization rather than genuine physical effects.
- **Resolution test** Provide a detailed description of the ligand parameterization, including charges, bond terms, and any restraints used. Include validation of the parameters, such as comparison of simulated geometries or binding energies with experimental or high-level QM data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report docking binding energies in Table 1 and MM/PBSA binding energies in Table 2, and state that the computed binding affinity of Heme to REV-ERBβ was stronger than that of CoPP, in agreement with experimental results.
- **Evidence pointer** Section 2.1, Section 2.2, Tables 1 and 2
- **Concern** The manuscript reports docking binding energies of −65.91 and −71.10 kJ/mol for Heme and CoPP, respectively, in the antagonist and agonist receptor forms. However, the text states that Heme has a greater negative binding energy, which is inconsistent with the reported values if CoPP has the more negative value. The MM/PBSA results are not presented numerically in the text, and the relationship between docking scores and MM/PBSA energies is not discussed. The experimental KD values cited (353 nM for Heme, 2.56 µM for CoPP) correspond to a difference of approximately 5 kJ/mol, but the reported docking energies differ by about 5 kJ/mol in the opposite direction.
- **Why it matters** The agreement with experimental data is a key claim of the paper. If the reported numbers are inconsistent or misinterpreted, the central conclusion that the simulations reproduce experimental binding affinities is not supported.
- **Resolution test** Clarify the direction of the binding energy values and ensure that the text, tables, and figures are consistent. Provide the numerical MM/PBSA values and discuss how they compare with the docking results and experimental data. If the docking energies are not in agreement with experiment, state this explicitly and explain the discrepancy.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim that CoPP alters the conformation of the ligand-binding site of REV-ERBβ, disrupting the binding site for nuclear receptor corepressor, and that this is the mechanism of antagonism.
- **Evidence pointer** Sections 2.4–2.6, Figures 7–13
- **Concern** The claim that CoPP disrupts the NCoR-binding site is based on MD simulations showing increased RMSD, expansion of the binding pocket, and changes in Helix-11 conformation. However, the figures are not provided, and the text does not quantify the conformational changes beyond average RMSD values. The protein-peptide docking results (Table 4) show a large difference in binding energy between Heme and CoPP complexes, but the text does not explain how the docking scores translate to a functional outcome. The claim that the "end of Helix-11" is disrupted is not supported by a clear structural analysis.
- **Why it matters** The mechanistic conclusion of the paper rests on this claim. Without a clear and quantitative demonstration that CoPP specifically disrupts the NCoR-binding surface, the conclusion is not established.
- **Resolution test** Provide the missing figures and a quantitative analysis of the conformational changes, such as per-residue RMSD, secondary structure analysis, or principal component analysis. Show that the changes in Helix-11 are specific to CoPP and not simply due to general protein flexibility. Discuss how the protein-peptide docking results relate to the MD observations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors use protein-peptide docking with PATCH Dock to evaluate NCoR binding to the Heme and CoPP complexes, and report a validation step using re-docking with an RMSD of 1.3757 Å.
- **Evidence pointer** Section 2.6, Section 4.5, Table 3
- **Concern** The validation of the protein-peptide docking method is described only briefly. The RMSD of 1.3757 Å is reported, but it is not clear what this value refers to (e.g., the peptide backbone, the full complex, or the binding interface). The manuscript does not state how the NCoR peptide was extracted from the REV-ERBα crystal structure, how the peptide was modeled, or whether the docking was performed on the full-length NCoR or a fragment. The choice of PATCH Dock for protein-peptide docking is unusual, as this tool is primarily designed for protein-protein docking.
- **Why it matters** The protein-peptide docking results are used to support the claim that Heme promotes NCoR recruitment while CoPP does not. If the docking method is not validated or is inappropriate for this system, the results may not be reliable.
- **Resolution test** Provide a detailed description of the protein-peptide docking setup, including the source and preparation of the NCoR peptide, the docking protocol, and the validation criteria. Justify the choice of PATCH Dock for this application. If possible, compare the docking results with experimental data on NCoR binding to REV-ERBβ.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that the binding-pocket volume was calculated using POVME 3.0 and report average values of 566.29 A3 and 777.39 A3 for Heme and CoPP, respectively.
- **Evidence pointer** Section 2.5, Figure 9
- **Concern** The manuscript reports average binding-pocket volumes but does not provide any measure of variability, such as standard deviation or standard error. It is not clear how many frames were analyzed, whether the volumes were calculated over the entire trajectory or a subset, or whether the difference between Heme and CoPP is statistically significant.
- **Why it matters** The claim that CoPP enlarges the binding pocket is based on this analysis. Without statistical support, the difference could be within the noise of the calculation.
- **Resolution test** Provide the standard deviation or confidence intervals for the pocket volume calculations, and state the number of frames analyzed. Perform a statistical test to determine whether the difference between Heme and CoPP is significant.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that REV-ERBβ is an "overexpressed oncoprotein" but the introduction describes it as a "cancer suppressor." This is contradictory and confusing.
- **Required correction** Clarify the role of REV-ERBβ in cancer. If it is overexpressed in certain cancers but functions as a suppressor in others, state this explicitly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1, Table 1
- **Issue** The text states that Heme had the greatest negative binding energy, but the reported values in Table 1 appear to show CoPP with a more negative value in the antagonist form. This is confusing.
- **Required correction** Recheck the values in Table 1 and ensure the text accurately reflects the data. If the values are correct, explain the discrepancy.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2, Table 2
- **Issue** The MM/PBSA results are presented in Table 2 but not described in the text. The reader cannot assess the significance of these results.
- **Required correction** Add a description of the MM/PBSA results in the text, including the numerical values and their interpretation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5, Figure 8
- **Issue** The text states that CoPP rotated about 90 degrees by the end of the simulation, but it is not clear what this rotation refers to or how it was measured.
- **Required correction** Clarify the rotation measurement and provide a reference to the figure that shows this.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.3
- **Evidence pointer** Section 4.3
- **Issue** The docking protocol states that the grid spacing was changed from 0.375 nM, but the unit should be Å, not nM. This appears to be a typographical error.
- **Required correction** Correct the unit to Å.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.4
- **Evidence pointer** Section 4.4
- **Issue** The simulation temperature is stated as 310 K, which is above physiological temperature (310 K is approximately 37 degrees Celsius, which is correct for human body temperature). However, the text does not state why this temperature was chosen.
- **Required correction** Briefly justify the choice of simulation temperature.

## Risk / unsupported claims
- The claim that the computed binding affinity of Heme is stronger than that of CoPP is not supported by the reported docking energies, which appear to show the opposite for the antagonist form.
- The claim that CoPP disrupts the NCoR-binding site via Helix-11 conformational changes is not quantitatively supported by the data presented.
- The claim that the MD simulations explain the agonist/antagonist behavior of Heme and CoPP is not fully established due to the lack of validation of the ligand parameters and the protein-peptide docking method.
- The statement that "the results suggest that a subtle change in the metal center of porphyrin can change the behavior of porphyrin in cancer cell signaling" is a reasonable hypothesis but is not directly tested in this study, as no cellular or experimental validation is provided.
- The claim that "in silico studies are very important in designing and developing porphyrin derivatives" is a general statement and not a finding of this study.