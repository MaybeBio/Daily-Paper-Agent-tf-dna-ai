## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, supplementary statements)
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and support of claims by presented evidence. Not assessed: editorial quality, formatting, or literature completeness beyond what affects interpretation.
- **Shared manuscript claim summary** The authors present an integrative structural biology study of the RAR/RXR heterodimer bound to four DNA response elements (DR0, DR1, DR5, IR0) in complex with corepressor NCoRNID or coactivator TIF-2NRID. Using SAXS, HDX-MS, and MD simulations, they report that DNA sequence and architecture modulate the conformational ensemble of the heterodimer, influence interdomain contacts, and affect coregulator binding affinity and dynamics. They propose that specific DNA response elements exert allosteric control over receptor function and coregulator recruitment.
- **Visible evidence base** Abstract, full introduction, complete methods section, results section with references to Figures 1-4 and Tables 1, supplementary figure and table references, discussion, data availability statement
- **Missing materials affecting confidence** Figures and tables referenced in the text are not provided. Supplementary figures (S1-S9), supplementary tables (S1-S3), and the crystallographic structure for IR0-bound RXR/RXR are referenced but not available. Specific numerical values for HDX-MS differences, MD contact probabilities, and SAXS fitting parameters are only partially reported in text. The deposited PDB and SASBDB accession codes are listed as "to be added."

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious and potentially valuable integrative analysis of RAR/RXR conformational dynamics on different DNA response elements. The combination of SAXS, HDX-MS, and MD simulations is appropriate and well-designed to address the question of DNA allosteric effects on nuclear receptor complexes. The authors have generated a substantial dataset that could meaningfully advance understanding of how DNA sequence modulates RAR/RXR function. However, the manuscript as presented has several significant issues that prevent full evaluation. The absence of all figures and tables makes it impossible to assess the quality of the data, the validity of the fitting procedures, or the strength of the conclusions drawn. Several claims appear to exceed what the described methods can support, particularly regarding the functional significance of observed conformational differences. The HDX-MS analysis, while comprehensive in scope, lacks sufficient quantitative detail in the text to evaluate the significance of reported differences. The MD simulation methodology, while state-of-the-art, is described with insufficient detail regarding system preparation, equilibration protocols, and convergence criteria. The manuscript would benefit from clearer articulation of which conclusions are firmly supported by direct experimental evidence versus which are inferred from computational modeling.

- **Who would be interested in the results, and why** Structural biologists studying nuclear receptor complexes, particularly those interested in allosteric regulation of transcription factors. Researchers in the retinoid signaling field would find the comparative analysis of different RARE elements valuable. The methodological approach combining multiple biophysical techniques with MD simulations will interest investigators studying other dynamic multi-domain protein-DNA complexes. The findings on coregulator interaction dynamics have potential relevance for drug discovery efforts targeting RAR/RXR, as they suggest DNA context may influence ligand-coregulator coupling.

- **Major strengths** The study addresses a significant and under-explored question: how DNA response element identity influences the conformational landscape of a nuclear receptor heterodimer and its interactions with coregulators. The multi-technique approach is well-conceived, with SAXS providing global shape information, HDX-MS offering residue-level dynamics, and MD simulations enabling interpretation at atomic detail. The inclusion of four distinct DNA elements, including non-canonical and inverted repeat configurations, provides a useful comparative framework. The authors have been thoughtful in attempting to connect structural observations to functional outcomes, particularly regarding the repressive role of DR1 elements. The identification of a potential new interaction interface on NCoRNID (the IR region) is an interesting observation that could stimulate further investigation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim pointer** The manuscript claims to present an integrative structural analysis of RAR/RXR complexes on four DNA elements, with conclusions about conformational differences, interdomain contacts, and coregulator interaction dynamics.
- **Evidence pointer** Figures 1-4, Tables 1-2, Supplementary Figures S1-S9, Supplementary Tables S1-S3 (none provided)
- **Concern** All primary data figures and tables are absent from the submitted manuscript. The results section refers extensively to specific panels, fitting curves, difference maps, and statistical comparisons that cannot be evaluated. This includes the SAXS profiles and fits (Figure 1), MD-derived distance distributions and contact maps (Figures 2-3), HDX-MS difference maps (Figures 2-4), and all quantitative binding data (Table 1). Without access to these data, it is impossible to assess the quality of the experimental work, the validity of the fitting procedures, the statistical significance of reported differences, or whether the conclusions are supported by the evidence.
- **Why it matters** The central claims of the paper rest entirely on the interpretation of these data. The χ² values for SAXS fits, the magnitude and reproducibility of HDX-MS differences, the convergence of MD simulations, and the statistical treatment of binding affinities are all critical to evaluating whether the conclusions are justified. The absence of these materials makes the manuscript unassessable in its current form.
- **Resolution test** Provide all figures and tables with appropriate statistical annotations. Include representative raw data, fitting residuals, and quality metrics. For HDX-MS, provide confidence intervals or replicate information for all reported differences. For MD, provide convergence metrics and ensemble validation against experimental data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-data alignment
- **Claim pointer** The authors state that "each DNA differently drives the relative subunit domain positioning of RAR/RXR heterodimer" and that specific DNA elements induce distinct conformational states with functional consequences for coregulator recruitment.
- **Evidence pointer** Results section "DNA-Driven Structural Adaptations of the RAR/RXR Heterodimer"; Figures 1-2; Table 1
- **Concern** The text reports that SAXS-derived parameters (Rg, Dmax) are similar across all DNA conditions (approximately 4.0 ± 0.4 nm and 13.0 ± 0.9 nm, respectively), yet the authors conclude that the complexes adopt distinct conformations depending on the DNA element. The evidence for conformational differences appears to rest primarily on differences in P(r) and Kratky profile shapes, and on MD simulations. However, the text does not provide quantitative metrics for how these profile differences were assessed, whether they were statistically significant, or how they were validated against the MD ensembles. The MD simulations are used to interpret the SAXS data, but the text does not describe how the simulations were validated against the experimental data beyond reporting χ² values. This creates a circularity concern: the simulations are used to interpret the experimental data, and the experimental data are used to validate the simulations, without clear independent assessment of either.
- **Why it matters** The central conclusion that DNA sequence modulates the conformational ensemble of RAR/RXR depends on demonstrating that the observed differences are real and not artifacts of sample preparation, data processing, or simulation methodology. If the global parameters are similar, the evidence for distinct conformations must be robust and clearly presented.
- **Resolution test** Provide quantitative comparison of P(r) and Kratky profiles across conditions, including error estimates and statistical tests. Describe how MD ensembles were validated against SAXS data, including the fitting procedure, the number of frames used, and the sensitivity of the fits to ensemble composition. Provide independent evidence (e.g., from HDX-MS or other techniques) that corroborates the conformational differences predicted by MD.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The authors report binding affinities for NCoRNID to RAR/RXR-DNA complexes in the presence and absence of BMS493, and for TIF-2NRID to agonist-bound complexes, with differences attributed to DNA identity.
- **Evidence pointer** Table 1; Results sections on NCoRNID and TIF-2NRID interactions; Supplementary Figure S2
- **Concern** The text reports Kd values in the nanomolar range for TIF-2NRID and approximately 500 nM for NCoRNID, with some DNA-dependent variation. However, no error estimates, replicate numbers, or statistical comparisons are provided in the text. The MST experiments for NCoRNID are described as three independent measurements, but the variability is not reported. The fluorescence anisotropy experiments are described as averages of at least three independent experiments, but again without error metrics. The claim that DR5 and IR0 show enhanced NCoRNID affinity compared to DR0 and DR1 is not supported by any reported statistical analysis. Additionally, the authors note that NCoRNID affinity was "drastically reduced" in the presence of AM580 with Kd > 5 µM, but the upper limit of detection is not defined.
- **Why it matters** The functional significance of the study depends on demonstrating that DNA identity measurably affects coregulator binding. Without proper error analysis and statistical testing, the reported differences could be within experimental noise. The affinity measurements are also central to the claim that DNA exerts allosteric control over coregulator recruitment.
- **Resolution test** Provide Kd values with standard errors or confidence intervals for all conditions. Report the number of independent experiments and the statistical test used to compare conditions. Define the detection limits of the assays. If differences are not statistically significant, state this explicitly and adjust the conclusions accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive overreach
- **Claim pointer** The authors state that "DNA influences RAR/RXR function through direct interactions and long-range allosteric effects" and that these effects "may affect the heterodimer functions, including heterodimerization stability, ligand binding and coregulator interaction."
- **Evidence pointer** Discussion section; HDX-MS results (Figures 2-4)
- **Concern** The HDX-MS data show protection differences in the LBDs upon DNA binding, but the text does not clearly distinguish between direct effects (e.g., DNA contacting LBD regions through the hinge) and true allosteric effects transmitted through the protein. The authors acknowledge that the hinge is flexible and that DNA-induced protection in the LBD could result from direct contact between the DNA and LBD regions in some conformations. However, the discussion interprets these findings as evidence for allosteric communication without adequately considering alternative explanations. The claim that DNA stabilizes the RAR LBD while destabilizing the RXR LBD is interesting but the functional significance is speculative. The authors suggest this may relate to the "subordinate role" of RXR, but this interpretation goes beyond the data presented.
- **Why it matters** The distinction between direct and allosteric effects is mechanistically important. If the observed LBD protection results from direct DNA-LBD contacts in a subpopulation of conformations, this is different from a true allosteric pathway through the protein. The authors should be more careful in their language and acknowledge the limitations of their approach in distinguishing these possibilities.
- **Resolution test** Provide additional analysis or discussion that addresses alternative explanations for the observed HDX-MS protection patterns. If possible, use the MD simulations to determine whether DNA-LBD contacts occur in the simulated ensembles and whether these correlate with the HDX-MS protection. Consider performing additional experiments (e.g., with mutant proteins or modified DNA) to test the allosteric hypothesis.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The authors used AlphaFold3.0 to model the NCoRNID complex with RAR/RXR on DR1, and this model was used for MD simulations to assess the stability of the IR region.
- **Evidence pointer** Results section "Structural and Functional Characterization of NCoRNID Interactions"; Supplementary Figure S9
- **Concern** The description of the AlphaFold3.0 modeling is minimal. The text states that the complex was modeled and subjected to MD simulations, but does not provide details on the confidence of the model, the regions of the complex that were modeled (full-length vs. truncated), or how the model was validated. The IR region of NCoRNID is described as "predicted to adopt a helical structure," but the basis for this prediction is not clear. The MD simulations of the modeled complex are used to support conclusions about the IR region's interactions with RXR, but the text does not describe how the simulations were set up, how the system was equilibrated, or how convergence was assessed. Given that the IR region is a novel finding of this study, the modeling and simulation details need to be more thoroughly described.
- **Why it matters** The identification of the IR region as a new interaction interface is a potentially important contribution. However, if the modeling is not robust or the simulations are not well-converged, the conclusions about the IR region's role could be unreliable. The authors need to provide sufficient detail for readers to evaluate the quality of the modeling and simulation work.
- **Resolution test** Provide a more detailed description of the AlphaFold3.0 modeling, including confidence metrics (e.g., pLDDT scores, PAE values) and the specific regions of the complex that were modeled. Describe the MD simulation setup, including the force field parameters, solvation conditions, equilibration protocol, and simulation length. Provide convergence metrics (e.g., RMSD, radius of gyration as a function of time) and validation of the modeled complex against experimental data.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, final sentence
- **Issue** The abstract states that the study "provides new insights into the structural features of coregulator proteins," but the study primarily focuses on the RAR/RXR heterodimer and its conformational changes. The structural features of the coregulator proteins themselves are not a major focus.
- **Required correction** Revise the abstract to more accurately reflect the focus of the study, e.g., "provides new insights into the structural dynamics of RAR/RXR-coregulator complexes and the allosteric influence of DNA response elements."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results section "DNA-Driven Structural Adaptations"
- **Evidence pointer** Text describing Figure 1E-H
- **Issue** The text states that "a disparity in P(r) and Kratky profiles among the RR-DNA complexes was observed," but the description of the specific differences is vague. The text mentions "distinct asymmetric patterns" and "a prominent peak at 3 nm followed by a second peak at 7 nm" for IR0, but does not clearly describe the profiles for the other DNA elements.
- **Required correction** Provide a more detailed and systematic description of the P(r) and Kratky profiles for each DNA condition, highlighting the specific differences that support the conclusion of distinct conformations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section "DNA Conformational Signature Persists"
- **Evidence pointer** Text describing Figure 3A-D
- **Issue** The term "deck model" is used without definition. It appears to refer to a model in which NCoRNID binds to both RAR and RXR, but this is not explicitly stated.
- **Required correction** Define the term "deck model" when first used, or replace with a more descriptive term such as "dual-binding model."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Data Availability section
- **Evidence pointer** Data Availability section
- **Issue** The PDB and SASBDB accession codes are listed as "to be added." This is acceptable for a preprint, but the authors should ensure that the codes are provided before any formal publication.
- **Required correction** Provide the accession codes when available, or state that they will be provided upon publication.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph on IR region
- **Issue** The discussion of the IR region's potential role is speculative and could be more clearly framed as a hypothesis. The text states that the IR region "may participate in additional molecular interactions within a larger complex," but does not provide specific predictions or suggest experiments to test this hypothesis.
- **Required correction** Frame the IR region discussion as a hypothesis and suggest specific experiments or analyses that could test its role.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, HDX-MS section
- **Evidence pointer** Methods section on HDX-MS
- **Issue** The methods section describes the HDX-MS experimental setup but does not provide details on the data analysis pipeline, including how peptide-level data were combined to calculate region-level differences, how significance thresholds were determined, or how the data were normalized across conditions.
- **Required correction** Provide additional detail on the HDX-MS data analysis, including the software used, the criteria for identifying significant differences, and the handling of replicates.

## Risk / unsupported claims
- The claim that "each DNA differently drives the relative subunit domain positioning" is supported primarily by MD simulations with limited experimental validation. The SAXS data show similar global parameters across conditions, and the differences in P(r) profiles are not quantified or statistically assessed in the text.
- The claim that DNA binding "caused a substantial destabilization to RXR LBD's H2-H3 loop and H11" is based on HDX-MS data, but the magnitude of the effect and its statistical significance are not reported.
- The identification of the IR region of NCoRNID as a new interaction interface with RXR is based on AlphaFold3.0 modeling and MD simulations, but the confidence in the model and the convergence of the simulations are not described.
- The statement that "the DNA effects on RAR were maintained upon interaction with the ligand and coregulator" is based on HDX-MS comparisons, but the text does not provide quantitative comparisons across the different complex conditions.
- The functional significance of the observed conformational differences, particularly the claim that DR1 stabilizes the repressive complex, is inferred from structural data but not directly tested in functional assays.
- The claim that "TIF-2NRID physically interacted with the two agonist-bound receptors through NR boxes 1 and 3" is presented as a novel finding, but the evidence is based on HDX-MS protection patterns that could have alternative explanations (e.g., indirect effects through conformational changes).