## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, and methods
- **Assessment boundary** Scientific content, technical soundness, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors report a comparative biophysical study of all four human FOXO forkhead (FH) domains using NMR spectroscopy and molecular dynamics simulations, identifying differential backbone dynamics, conserved intramolecular FH-CR3 interactions, and novel intermolecular FH-CR3 interactions between different FOXO isoforms
- **Visible evidence base** NMR chemical shift assignments, relaxation data (R1, R2, heteronuclear NOE), chemical shift perturbation titrations, MD simulations, AlphaFold2 predictions, quantum chemistry calculations
- **Missing materials affecting confidence** Figures referenced but not fully visible in text; supplementary data not provided; specific numerical values for binding affinities not reported; statistical details of MD analyses limited

## Reviewer
- **Overall assessment** This manuscript presents a systematic and technically rigorous comparative analysis of FOXO family FH domain dynamics and interactions. The work addresses an important gap in understanding how highly conserved transcription factor domains achieve functional diversity. The combination of NMR relaxation measurements, MD simulations, and binding studies across all four family members under identical conditions is a strength. However, several claims regarding the functional implications of the observed differences and the proposed intermolecular interaction model require additional quantitative support and more cautious interpretation. The manuscript would benefit from clearer presentation of binding affinities and more explicit statistical treatment of the MD data.

- **Who would be interested in the results, and why** Researchers in the fields of transcription factor biology, structural biology, and biophysics would find this work valuable. Specifically, those studying FOXO family function, intrinsically disordered protein regions, autoinhibitory mechanisms in transcription factors, and protein-protein interaction networks involving disordered domains would benefit. The methodological approach of combining NMR and MD across a protein family under standardized conditions provides a template for similar comparative studies.

- **Major strengths** 
  1. Systematic comparison of all four FOXO FH domains under identical experimental conditions is a significant methodological advance
  2. Integration of multiple biophysical techniques (NMR relaxation, MD simulations, quantum chemistry) provides complementary perspectives
  3. Identification of conserved intramolecular FH-CR3 interactions across the family extends previous findings
  4. Discovery of intermolecular FH-CR3 interactions between different FOXO isoforms is novel and potentially important
  5. Clear identification of FOXO3 as having distinct dynamic properties and weaker autoinhibitory interactions

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that intermolecular FH-CR3 interactions between different FOXO isoforms "indicate a model in which FOXO transcription factors could modulate their activities by interacting mutually"
- **Evidence pointer** Figure 7, Results section "FH and CR3 of different FOXOs interact intermolecularly"
- **Concern** The intermolecular interactions are demonstrated only through qualitative NMR titration experiments showing CSPs and line broadening. No binding affinities, stoichiometries, or quantitative comparisons between homo- and heterotypic interactions are provided. The physiological relevance of these interactions is speculative without cellular validation or at minimum quantitative biophysical characterization.
- **Why it matters** The central novel claim of the manuscript is the potential for hetero-oligomeric FOXO complex formation. Without quantitative binding data or evidence that such interactions occur at physiologically relevant concentrations, this claim remains unsupported. The qualitative categorization into "weak," "strong," and "line broadening" is insufficient to establish the proposed functional model.
- **Resolution test** Provide dissociation constants (Kd values) for representative homo- and heterotypic FH-CR3 pairs, determine binding stoichiometry, and demonstrate that interactions occur at concentrations relevant to cellular FOXO levels. Alternatively, temper the functional claims to reflect that these are in vitro observations requiring further validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The authors state that FOXO3 shows "the highest degree of flexibility within the FH domain and the weakest binding to its TAD"
- **Evidence pointer** Figure 3, Figure 6, Results sections on NMR relaxation and binding studies
- **Concern** The comparison of binding strengths across different FOXO isoforms is based on qualitative CSP magnitudes. The claim that FOXO3 has the weakest binding is derived from "only weak chemical shift perturbations" but no quantitative analysis or statistical comparison is provided. Additionally, the relationship between observed flexibility differences and binding affinity is not rigorously established.
- **Why it matters** The differential behavior of FOXO3 is a key finding that could explain functional differences among family members. However, without quantitative binding measurements and statistical analysis, the conclusion that FOXO3 has weaker autoinhibition remains preliminary.
- **Resolution test** Perform quantitative binding assays (e.g., ITC or fluorescence anisotropy) for all four FH-CR3 pairs to obtain comparable Kd values with appropriate error analysis. Correlate these values with the observed dynamic differences using appropriate statistical methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors propose that the W-[2-5]-[S/T/C/Y] motifs represent a common structural feature with variable interaction strengths that may contribute to functional differences
- **Evidence pointer** Figure 5, Results section on molecular dynamics simulations
- **Concern** The functional significance of the W-[2-5]-[S/T/C/Y] motifs is inferred primarily from MD simulations and quantum chemistry calculations on isolated side chain pairs. The connection between these local interactions and the observed differences in FH domain dynamics or CR3 binding affinity is not clearly demonstrated. The evolutionary analysis is limited to sequence conservation without functional validation.
- **Why it matters** The identification of these motifs as functionally important determinants of FOXO behavior is a significant claim that extends beyond the direct experimental observations. Without experimental validation of the role of these specific interactions, the interpretation remains speculative.
- **Resolution test** Perform mutagenesis experiments targeting the identified W-[2-5]-[S/T/C/Y] motifs and test the effects on FH-CR3 binding affinity and FH domain dynamics. Alternatively, clearly frame these findings as computational predictions requiring experimental validation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, NMR relaxation measurements
- **Evidence pointer** Methods section "15N spin relaxation measurements and error analysis"
- **Issue** The description of the relaxation data analysis is somewhat brief. The authors mention using FuDA for lineshape fitting but do not provide sufficient detail on how R1ρ values were converted to R2 or how the off-resonance correction was validated.
- **Required correction** Expand the methods to include more detail on the R1ρ to R2 conversion, validation of the off-resonance correction, and the specific parameters used in the FuDA analysis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results section, MD simulations
- **Evidence pointer** Figure 4, Results section "Molecular dynamics simulations reveal variable dynamics in conserved regions"
- **Issue** The description of the MD simulation results is somewhat qualitative. The authors mention distance distributions and flexibility differences but do not provide quantitative measures of uncertainty or convergence criteria for the simulations.
- **Required correction** Include convergence analysis for the MD simulations, provide quantitative measures of the distance distributions (e.g., mean and standard deviation), and state the criteria used to determine that the simulations were sufficiently converged for analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, paragraph on functional implications
- **Issue** The discussion of potential functional consequences of the observed differences in dynamics and binding is somewhat speculative and could benefit from more concrete connections to known FOXO biology, such as specific post-translational modifications or interaction partners that might be affected.
- **Required correction** Add a more focused discussion of how the observed biophysical differences might relate to known FOXO functions, such as differential regulation by post-translational modifications or tissue-specific functions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section, Quantum chemistry calculations
- **Evidence pointer** Methods section "Molecular dynamics simulations"
- **Issue** The description of the quantum chemistry calculations for interaction energies is brief. The authors mention using the APFD functional but do not provide details on basis set superposition error correction beyond mentioning the counterpoise method.
- **Required correction** Provide more detail on the counterpoise correction procedure, the specific software settings used, and how the five geometries were selected for the interaction energy calculations.

## Risk / unsupported claims
- The claim that intermolecular FH-CR3 interactions between different FOXO isoforms have functional relevance in cells is unsupported by the in vitro data presented
- The assertion that FOXO3 has the weakest FH-CR3 interaction among family members is based on qualitative CSP comparisons without quantitative binding measurements
- The functional significance of the W-[2-5]-[S/T/C/Y] motifs in determining FOXO-specific behavior is inferred from computational analyses without experimental validation
- The statement that differential dynamics "might be relevant for differential DNA binding and recruitment" is speculative and not directly tested
- The proposed model of FOXO hetero-oligomerization as a regulatory mechanism is presented as a conclusion rather than a hypothesis requiring further testing

## Assessment against Nature-style criteria
- **Originality** The comparative approach across all four FOXO family members under standardized conditions is novel. The identification of intermolecular FH-CR3 interactions between different isoforms is a new finding. However, the individual techniques and the concept of autoinhibitory CR3-FH interactions have been previously described.
- **Scientific importance** The work addresses a fundamental question in transcription factor biology: how highly conserved DNA-binding domains achieve functional diversity. The findings have implications for understanding FOXO regulation in development, metabolism, and cancer. The potential for hetero-oligomeric complex formation could open new avenues for therapeutic targeting.
- **Interdisciplinary readership** The work bridges structural biology, biophysics, and transcription factor biology. The NMR and MD approaches will appeal to biophysicists, while the FOXO biology context will attract cell and molecular biologists. However, the specialized nature of the methods may limit broader appeal.
- **Technical soundness** The experimental design is generally sound with appropriate controls and complementary techniques. The use of identical conditions for all family members is a strength. However, the lack of quantitative binding data and limited statistical treatment of some analyses weaken the technical rigor.
- **Readability for nonspecialists** The manuscript is generally well-written and accessible, with clear figures and logical flow. However, some sections, particularly the MD simulation and quantum chemistry descriptions, may be challenging for readers without computational biophysics background. The abstract effectively summarizes the key findings.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a valuable comparative analysis with novel findings regarding intermolecular FOXO interactions. However, the central claims regarding functional implications require quantitative binding data and more cautious interpretation. The work would be strengthened by addressing the major concerns regarding binding affinity measurements and tempering the speculative functional conclusions.