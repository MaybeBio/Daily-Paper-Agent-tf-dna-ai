## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, data availability, and supplementary figure/table references.
- **Assessment boundary** Scientific content, methodological rigor, validity of conclusions relative to the evidence presented, and clarity of presentation. Not assessed: editorial fit, formatting, or literature completeness beyond what is cited.
- **Shared manuscript claim summary** The authors use extensive all-atom molecular dynamics (MD) simulations (~3.5 μs) of human XPD helicase bound to single-stranded DNA, both undamaged and containing a 6−4 pyrimidine-pyrimidone photoproduct (6−4PP) near the pore entry, to propose an atomistic mechanism for lesion verification. They report that undamaged DNA undergoes a one-nucleotide 3′→5′ backbone translocation through the XPD pore, while the 6−4PP lesion is immobilized via extensive interactions with key residues (FeS residues R112, R196, H135, K128; Arch residues E377, R380; ATPase lobe 1 residues 215−221), leading to a closed, rigid pore that stalls the helicase.
- **Visible evidence base** Full text of the manuscript, including methods descriptions, results narrative, discussion, and references to supplementary figures, tables, and movies. No supplementary material files were provided for direct inspection.
- **Missing materials affecting confidence** Supplementary figures (S1–S14), supplementary tables (S1), supplementary movies (S1–S5), and the deposited MD trajectories on GitHub were not available for review. These are essential for verifying quantitative claims, convergence analyses, and the visual evidence for the proposed translocation and immobilization events.

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive and potentially valuable contribution to understanding how XPD verifies bulky DNA lesions during nucleotide excision repair. The central observation, that undamaged DNA can translocate by one nucleotide through the pore while the 6−4PP lesion is immobilized, is mechanistically interesting and aligns with existing biochemical and structural data. However, the strength of the conclusions rests heavily on the interpretation of a small number of MD trajectories, and the absence of the supplementary data limits the ability to fully assess convergence, sampling adequacy, and the robustness of the key findings. The manuscript is clearly written and the biological context is well presented, but several technical aspects require clarification and additional analysis before the proposed mechanism can be considered established.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, particularly nucleotide excision repair, and those studying helicase mechanisms and protein–DNA interactions. The work also speaks to the broader community interested in how molecular dynamics simulations can inform enzyme mechanism, especially in the context of damage recognition and verification. The identification of specific residues involved in lesion immobilization may guide future mutagenesis and single-molecule experiments.
- **Major strengths**
  1. The study addresses a significant and unresolved question: how XPD distinguishes damaged from undamaged DNA at the molecular level.
  2. The use of long-timescale all-atom MD simulations is appropriate and represents a substantial computational effort.
  3. The models are based on a relevant cryo-EM structure (PDB 6RO4), and the authors carefully describe the construction of the three systems.
  4. The proposed mechanism is concrete and testable, with specific residues and interactions identified.
  5. The discussion appropriately contextualizes the findings within existing experimental literature.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / sampling adequacy
  - **Claim pointer** The claim that undamaged DNA undergoes a one-nucleotide 3′→5′ backbone translocation through the XPD pore is based on a single 3.5 μs simulation in which this event was observed.
  - **Evidence pointer** Results section, Figure 2A, Figure 3, Supplementary Movie S1; location not provided for specific trajectory analysis details.
  - **Concern** The observation of a single translocation event in one trajectory, even over 3.5 μs, is a very limited basis for proposing a general mechanism. The authors state that this event occurred mainly during the 0–1 μs interval, prior to equilibration. This raises the question of whether the observed movement is a genuine representation of the translocation process or an artifact of the initial model setup and the system relaxing from a non-equilibrium starting state. The additional eight 2 μs simulations did not show this translocation, and the authors report that 67% of simulations showed blockage and 22% showed base flipping. The statistical basis for the proposed mechanism is therefore weak.
  - **Why it matters** The central mechanistic claim of the paper rests on this single event. Without evidence of reproducibility across multiple independent simulations, or a demonstration that the event is not a rare fluctuation, the conclusion that this represents the physiological translocation mechanism is not well supported.
  - **Resolution test** The authors should provide a more detailed analysis of the single translocation event, including the free energy landscape or a potential of mean force calculation for the translocation step. They should also discuss why the event was observed only in the pre-equilibration phase and whether this is consistent with a biologically relevant process. Additional independent simulations starting from different initial velocities or with different initial placements of the DNA might help establish reproducibility. If the event is truly rare, the authors should acknowledge this limitation and temper the strength of their claim.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / force field and model validation
  - **Claim pointer** The manuscript claims that the simulations provide a "molecular and dynamic characterization" of XPD activity, implying that the MD results are reliable and representative of the true system behavior.
  - **Evidence pointer** Materials and Methods, MD simulations section; Supplementary Methods (not provided).
  - **Concern** The manuscript does not provide sufficient detail on the force field parameters used for the 6−4PP lesion. The 6−4PP is a unique lesion with specific structural and electronic properties, and its accurate parameterization is critical for the validity of the simulations. The authors state that the 6−4PP structure is based on PDB 6CFI, but the process of deriving force field parameters (e.g., using GAFF, AMBER force fields, RESP charges) is not described in the main text. The Supplementary Methods are referenced but were not available for review.
  - **Why it matters** If the lesion parameters are inaccurate, the interactions between the lesion and the protein, which are central to the proposed immobilization mechanism, could be misrepresented. This would undermine the core conclusions of the study.
  - **Resolution test** The authors must provide a detailed description of the force field parameterization for the 6−4PP lesion, including the derivation of partial charges and any validation against experimental or quantum mechanical data. This information should be included in the main text or the Supplementary Methods, and the authors should confirm that the parameters have been used and validated in previous studies.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility / data availability
  - **Claim pointer** The authors state that the MD trajectories are deposited on GitHub, but the specific repository structure and analysis scripts are not described.
  - **Evidence pointer** Data Availability section.
  - **Concern** While depositing trajectories is commendable, the availability of raw trajectories alone is insufficient for full reproducibility. The authors do not mention whether the input files (e.g., parameter files, topology files, initial coordinates for all systems) and the analysis scripts used to generate the figures and quantitative results are also provided. Without these, other researchers cannot easily reproduce the simulations or the analyses.
  - **Why it matters** Reproducibility is a cornerstone of scientific validity. The inability of others to fully reproduce the work limits its impact and verifiability.
  - **Resolution test** The authors should confirm that all necessary input files, parameter files, and analysis scripts are deposited alongside the trajectories, and provide a clear description of the repository contents in the Data Availability statement.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation / overstatement of conclusions
  - **Claim pointer** The discussion states that the proposed mechanism "elucidates" how XPD verifies lesions and that the findings "demonstrate" the mechanism of discrimination.
  - **Evidence pointer** Discussion section, final paragraph.
  - **Concern** The language used in the discussion is somewhat stronger than the evidence supports. The study is based on a limited number of MD simulations and proposes a plausible mechanism, but it does not provide direct experimental validation. Terms like "elucidate" and "demonstrate" imply a level of certainty that is not warranted by the computational evidence alone. The authors do acknowledge this is a "model" and a "view," but the overall tone leans toward overstatement.
  - **Why it matters** Overstatement can mislead readers, especially those not deeply familiar with the limitations of MD simulations, into believing the mechanism is more firmly established than it is.
  - **Resolution test** The authors should soften the language in the discussion and conclusion to more accurately reflect that this is a proposed mechanism based on computational modeling, which is consistent with, but not proven by, existing experimental data. Phrases like "our simulations suggest" or "we propose" would be more appropriate.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1 and its legend.
  - **Issue** The figure legend is somewhat dense and it is not immediately clear how the three models (XPD-lesionOUT, XPD-lesionIN, XPD-unmod) differ in the schematic representation. The placement of the lesion relative to the pore is described in the text but could be more clearly annotated in the figure itself.
  - **Required correction** Consider adding explicit labels or a zoomed-in inset to Figure 1 that clearly shows the position of the 6−4PP lesion relative to the pore entry for both lesion-containing models, and the position of the dT1 nucleotide in the unmodified model.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods, MD simulations
  - **Evidence pointer** Materials and Methods, MD simulations section.
  - **Issue** The manuscript states that "AMBER18" was used but does not specify the exact force field (e.g., ff14SB, ff19SB) for the protein and the DNA. This is a key detail for reproducibility.
  - **Required correction** Specify the exact force field versions used for the protein, DNA, and ions in the main text or Supplementary Methods.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical analysis
  - **Affected element** Results, ensemble analyses
  - **Evidence pointer** Results section, "Overview" and subsequent subsections.
  - **Issue** The manuscript reports ensemble averages (e.g., RMSD values with standard deviations) but does not describe how many independent samples or frames were used for these calculations, nor whether block averaging or other methods were used to account for correlated data in a trajectory.
  - **Required correction** Provide details on the number of frames used for ensemble analysis and the method for estimating statistical uncertainties.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section, first paragraph.
  - **Issue** The discussion of the "plug" region and its potential role is brief. Given that the plug was excluded from the simulations, a more detailed discussion of the potential impact of this exclusion on the results would be helpful.
  - **Required correction** Add a sentence or two explicitly discussing the potential limitations of excluding the plug region and how its presence might affect the proposed mechanism.

## Risk / unsupported claims
- The claim that a one-nucleotide 3′→5′ backbone translocation is a general mechanism for undamaged DNA passage through the X pore is based on a single observed event in one trajectory and is therefore not robustly supported.
- The claim that the identified residues (R112, R196, H135, K128, E377, R380, and 215−221) are "key" for lesion verification is based on their observed interactions in the simulations, but no mutational or functional validation is provided. This is a plausible hypothesis, not an established finding.
- The statement that the proposed mechanism "elucidates" the lesion verification process is an overstatement given the computational nature of the study and the lack of direct experimental testing.
- The accuracy of the simulations, and therefore all conclusions, is contingent on the force field parameters for the 6−4PP lesion, which are not described in sufficient detail in the provided material.
- The generalizability of the findings to other lesions (e.g., CPD, bulky chemical adducts) is speculated upon but not tested, and should be presented as a hypothesis rather than a conclusion.