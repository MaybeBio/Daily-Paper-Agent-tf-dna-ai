## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary figure references
- **Assessment boundary** Scientific validity of the structural characterization claims, computational modelling quality, experimental validation adequacy, and consistency between computational and experimental results
- **Shared manuscript claim summary** The authors report the first computational model and experimental characterization of the DNA-binding Myb domain of mouse TTF1, claiming it is predominantly alpha-helical, stable in MD simulations, and sufficient for Sal box DNA binding
- **Visible evidence base** Sequence-based predictions (ProtParam, DisoPred), homology and ab-initio models (SWISS-MODEL, AlphaFold, Robetta, I-TASSER), model validation statistics (PROCHECK, SAVES, ProSA, VADAR), 200 ns MD simulations in triplicate, protein purification data, CD spectroscopy, Raman spectroscopy, and EMSA
- **Missing materials affecting confidence** Supplementary figures S1-S5 referenced but not provided; raw MD trajectory data not available; DLS data mentioned but not shown; EMSA gel image not shown in the provided text; no quantitative binding affinity data; no negative control for EMSA; no size-exclusion chromatography profile shown

## Reviewer
- **Overall assessment** The manuscript addresses an important gap in the structural biology of TTF1, a multifunctional protein with critical roles in transcription regulation. The authors combine computational prediction with experimental validation to characterize the Myb domain. The work is potentially valuable, but several technical issues weaken the current claims. The computational modelling is reasonable, though the template identity of 27% is low and the selection of the Robetta model over others requires stronger justification. The experimental validation is incomplete: the EMSA lacks quantitative analysis and controls, the DLS data are not shown, and the Raman spectroscopy interpretation is overly qualitative. The claim that this is the "first-ever study" is strong and needs careful verification. The manuscript would benefit from more rigorous quantitative analysis and clearer presentation of raw data.

- **Who would be interested in the results, and why** Researchers studying transcription termination mechanisms, particularly Pol I transcription and rDNA regulation, would find this work relevant. The structural characterization of the TTF1 DNA-binding domain could inform studies on transcription termination across species. Additionally, researchers interested in the application of computational modelling combined with biophysical validation for challenging protein targets would find the methodological approach useful. The work may also interest those studying proteins with intrinsically disordered regions, as the authors address the challenge of characterizing a domain from a protein that resists full-length purification.

- **Major Strengths**
  1. The study addresses a significant gap, as no structural information for TTF1 has been available despite its essential functions
  2. The combination of multiple computational approaches (homology, ab-initio, MD simulation) with experimental validation (CD, Raman, EMSA) is methodologically sound
  3. The MD simulation in triplicate over 200 ns provides reasonable evidence for structural stability
  4. The experimental validation of the computational model through CD spectroscopy showing alpha-helical content is a good example of computational-experimental integration
  5. The work has clear practical implications, as the purified Myb domain could enable future structural studies

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence sufficiency
- **Claim pointer** "The results confirmed that the Myb domain alone was sufficient to bind to the Sal box DNA sequence"
- **Evidence pointer** Results section, EMSA subsection, Figure 8
- **Concern** The EMSA is described qualitatively with no quantitative binding data, no negative control (e.g., a non-specific DNA sequence or a mutated Sal box), and no competition assay. The gel image is not shown in the provided text, making it impossible to assess the quality of the shift or whether the observed shift is specific. Additionally, the protein concentrations used are not specified in the text.
- **Why it matters** The claim that the Myb domain is sufficient for DNA binding is a central conclusion of the paper. Without quantitative binding affinity (e.g., Kd determination) or specificity controls, the conclusion is not rigorously supported. A non-specific DNA-binding protein could produce a similar shift.
- **Resolution test** Provide the EMSA gel image, include a negative control with a non-specific DNA sequence, perform a competition assay with unlabeled specific and non-specific DNA, and ideally determine a binding constant (e.g., Kd) using a quantitative method such as fluorescence anisotropy or ITC.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model selection justification
- **Claim pointer** "Considering all the above factors, we selected the Robetta generated de novo model of the Myb domain, to pursue for further computational analysis"
- **Evidence pointer** Results section, Molecular modelling subsection, Table 2, Figure 2
- **Concern** The selection of the Robetta model over the other three models (SWISS-MODEL, AlphaFold, I-TASSER) is not well justified. The Ramachandran plot statistics are similar for AlphaFold, SWISS-MODEL, and Robetta, and the authors do not provide a clear quantitative comparison (e.g., QMEAN, MolProbity scores, or other global quality metrics) that would justify the choice. The I-TASSER model is excluded due to poorer statistics, but the distinction among the other three is unclear.
- **Why it matters** The choice of model underpins all subsequent computational analyses (MD simulation, FEL, contact maps). If the model selection is arbitrary or not rigorously justified, the downstream conclusions about structural stability and dynamics are weakened.
- **Resolution test** Provide a comprehensive comparison of all four models using multiple quality metrics (e.g., QMEAN, MolProbity, z-scores from ProSA for all models, not just the selected one). Justify the Robetta selection based on these metrics and explain why AlphaFold, which is generally considered highly accurate, was not selected.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability and reproducibility
- **Claim pointer** "All the data generated from the study is available in the manuscript"
- **Evidence pointer** Data Availability section
- **Concern** The statement that all data are available in the manuscript is not accurate. Supplementary figures S1-S5 are referenced but not provided in the submitted text. The DLS data are mentioned but not shown. The size-exclusion chromatography profile is not shown. The EMSA gel is not shown. The MD simulation parameters and force field validation are not fully described.
- **Why it matters** Reproducibility is a core requirement for scientific publication. Without access to the raw data, supplementary figures, and detailed methods, other researchers cannot verify or build upon the findings.
- **Resolution test** Provide all supplementary figures and raw data. Show the DLS data and SEC profile. Include the EMSA gel image. Provide detailed MD simulation parameters, including the specific commands and force field settings used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Novelty claim verification
- **Claim pointer** "This is the first-ever study to report a complete in silico model of the Myb domain, which is physically characterized"
- **Evidence pointer** Abstract, Discussion
- **Concern** The claim of being the "first-ever" study is strong and requires careful verification. The authors do not provide a comprehensive literature search to support this claim. Given that TTF1 has been studied for decades and that AlphaFold has been used to predict structures of many proteins, it is possible that a model of the TTF1 Myb domain already exists in public databases or has been reported in other contexts.
- **Why it matters** Overclaiming novelty can undermine the credibility of the work. If a similar model or characterization has been reported, the claim would be inaccurate.
- **Resolution test** Conduct a thorough literature search and database check (e.g., AlphaFold DB, PDB) for existing TTF1 Myb domain structures or models. Revise the novelty claim to be more specific and accurate, or provide evidence that no prior model exists.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Raman spectroscopy interpretation
- **Claim pointer** "The wavenumbers for the amide I and III modes in α-helix and β-sheet structures are typically found to be within the ranges of 1662–1650 and 1272–1264 cm−1 (for α-helix) and 1674–1672 and 1242–1227 cm−1 (for β-sheet), respectively"
- **Evidence pointer** Results section, Raman spectra analysis subsection, Figure 10
- **Concern** The Raman spectroscopy section is largely descriptive and does not provide a clear quantitative analysis. The amide I band fitting is described, but the actual fitted parameters, the percentage of alpha-helix derived from the fit, and the comparison with CD data are not presented quantitatively. The figure is not shown in the provided text.
- **Why it matters** Raman spectroscopy can provide valuable secondary structure information, but the analysis must be quantitative to be meaningful. Without the fitted parameters and derived secondary structure percentages, the conclusion that the protein is predominantly alpha-helical based on Raman is not well supported.
- **Resolution test** Provide the Raman spectra figure, the fitted amide I band components with their positions and relative areas, and the derived secondary structure percentages. Compare these quantitatively with the CD results.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology accuracy
- **Affected element** Abstract, Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The manuscript uses "Mys domain" in the Introduction and "Myb domain" elsewhere. This inconsistency is confusing.
- **Required correction** Use "Myb domain" consistently throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and Methods, Molecular Dynamics simulation section
- **Evidence pointer** Materials and Methods section
- **Issue** The MD simulation section does not specify the force field version, water model details, or the specific GROMACS commands used. The number of ions and water molecules is given, but the simulation box size and the method for adding ions are not described.
- **Required correction** Provide complete MD simulation parameters, including the exact GROMACS version, force field version, water model, box dimensions, and ion placement method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Results, CD spectroscopy subsection
- **Evidence pointer** Results section, CD spectroscopy subsection
- **Issue** The CD spectroscopy results are described as an average of three runs, but no error bars or standard deviations are provided in the text. The deconvolution results are given as percentages, but the uncertainty in these values is not reported.
- **Required correction** Provide the standard deviation or standard error for the CD measurements and the deconvolution results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript states that TTF1 has "vital roles" in multiple processes, but some of the cited references are not specific to TTF1 or are outdated. For example, reference [6] for the ribomotor model may not be the most recent or comprehensive source.
- **Required correction** Review and update references to ensure they are specific to TTF1 and include recent work where applicable.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 7
- **Evidence pointer** Results section, Purification subsection
- **Issue** The purification figure is described but not shown. The text mentions a single band on SDS-PAGE, but the molecular weight marker positions and the expected size of the Myb domain are not stated.
- **Required correction** Provide the figure and include molecular weight markers and the expected molecular weight of the Myb domain in the figure legend.

## Risk / unsupported claims
1. The claim that the Myb domain is "sufficient to bind the Sal box DNA" is not quantitatively supported by the EMSA data presented, as no binding affinity or specificity controls are shown.
2. The claim of being the "first-ever study" to report a complete in silico model of the Myb domain is not verified with a comprehensive literature search.
3. The statement that the Robetta model is the best among the four generated models is not supported by a comprehensive quantitative comparison.
4. The claim that the protein is "predominantly alpha-helical" is supported by CD and Raman, but the Raman analysis is not quantitative, and the CD data lack error analysis.
5. The assertion that the model "stabilizes at 200ns" is based on MD simulation, but the specific convergence criteria and the analysis of the three replicates are not fully described.
6. The statement that the purified protein is "highly homogeneous and mono-dispersed" is based on DLS data that are not shown in the manuscript.
7. The claim that the study "will pave the way towards solving the atomic structure" is speculative and not directly supported by the data presented.