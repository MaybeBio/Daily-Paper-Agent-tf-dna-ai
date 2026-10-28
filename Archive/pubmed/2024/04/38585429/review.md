## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided text
- **Shared manuscript claim summary** The authors propose that the monomeric forkhead (FKH) domain of human FoxP1 is intrinsically disordered, that dimerization via 3D domain swapping stabilizes the folded state, and that DNA binding paradoxically promotes a disordered dimeric state, thereby negatively regulating dimer stability and suggesting a reversible, DNA-mediated control of FoxP1 transcriptional repression.
- **Visible evidence base** Single-molecule multiparameter fluorescence spectroscopy (smMFS) including FRET, fluorescence anisotropy, burst variance analysis (BVA), photon distribution analysis (PDA), filtered FCS (fFCS); replica exchange discrete molecular dynamics (DMD) simulations; ensemble biochemical dimerization assays; sequence analysis references.
- **Missing materials affecting confidence** Figures and supplementary tables referenced but not provided; detailed experimental protocols for mutagenesis, labeling efficiency, and sample preparation; raw data and fitting parameters; structural models used for DMD simulations; details of the dimerization assay including controls and replicates.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question in transcription factor biology, namely the active role of DNA in modulating the conformational landscape and oligomeric state of a DNA-binding domain. The combination of single-molecule spectroscopy and simulations is appropriate and potentially powerful. However, the central claim that DNA binding destabilizes the dimeric state and promotes disorder is not fully established from the evidence presented. Key quantitative details, control experiments, and a clear mechanistic model linking the observed conformational changes to the dimerization equilibrium are lacking. The manuscript would benefit from a more rigorous and quantitative treatment of the data, as well as a clearer articulation of how the proposed model differs from and advances existing frameworks.
- **Who would be interested in the results, and why** Researchers in the fields of transcription factor biology, protein dynamics, intrinsically disordered proteins, and single-molecule biophysics. The work is also relevant to those studying FoxP family proteins and their roles in development and disease, as it challenges the conventional view of DNA as a passive binding partner and suggests a regulatory feedback mechanism.
- **Major strengths** 1. The study tackles a significant and under-explored question: the reverse allosteric effect of DNA on a transcription factor's conformational state and oligomerization. 2. The use of multiple complementary single-molecule techniques (FRET, anisotropy, BVA, PDA, fFCS) is a methodological strength, providing a multi-parameter view of the system. 3. The integration of experimental data with molecular dynamics simulations is a powerful approach to interpret conformational ensembles. 4. The focus on the FoxP1 FKH domain, a clinically relevant protein, adds translational significance.
- **Major Concerns** 
  - **R1-M1** (Severity: Major, Blocking: Yes, Axis: Evidence sufficiency for central claim)
  - **R1-M2** (Severity: Major, Blocking: Yes, Axis: Quantitative rigor and data interpretation)
  - **R1-M3** (Severity: Major, Blocking: No, Axis: Mechanistic model clarity)
  - **R1-M4** (Severity: Major, Blocking: No, Axis: Generalizability and physiological relevance)
- **Minor Comments** 
  - **R1-m1** (Severity: Minor, Axis: Clarity and reproducibility)
  - **R1-m2** (Severity: Minor, Axis: Data presentation)
  - **R1-m3** (Severity: Minor, Axis: Literature context)
- **Technical failings that need to be addressed before the case is established** The central claim that DNA binding destabilizes the dimer is based on indirect measurements of conformational populations (FRET, anisotropy) and a single biochemical assay. The link between the observed increase in conformational disorder and a shift in the dimerization equilibrium is not quantitatively established. The dimerization assay, as described, lacks crucial controls and a clear demonstration that the observed changes in anisotropy directly report on the monomer-dimer equilibrium rather than on conformational changes within a stable dimer. The interpretation of the fFCS data, particularly the assignment of specific timescales to conformational transitions, requires more rigorous justification.
- **Assessment against Nature-style criteria** 
  - **Originality** High. The concept of DNA as a negative allosteric regulator of TF dimerization is novel and counterintuitive.
  - **Scientific importance** High. If substantiated, the findings would have broad implications for understanding gene regulation, the role of intrinsic disorder in TF function, and the evolution of TF-DNA interactions.
  - **Interdisciplinary readership** Moderate to high. The work bridges biophysics, structural biology, and molecular biology, and would appeal to a broad audience in these fields.
  - **Technical soundness** The experimental approach is sophisticated, but the current analysis and presentation of the data are insufficient to fully support the conclusions. The lack of quantitative rigor in linking conformational dynamics to the dimerization equilibrium is a significant weakness.
  - **Readability for nonspecialists** The manuscript is written in a technical style that may be challenging for non-specialists. The key concepts and the significance of the findings could be communicated more clearly.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the experimental toolkit is appropriate, but the evidence as presented does not yet fully establish the central claim. A major revision with more rigorous quantitative analysis, additional controls, and a clearer mechanistic model is required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** The manuscript claims that "DNA binding promotes a disordered FKH dimer bound to DNA, negatively controlling the stability of the dimeric FoxP1:DNA complex" and that this "shifts the dimerization equilibrium toward the monomeric state."
- **Evidence pointer** Results sections "DNA binding differentially perturbs the monomeric and dimeric states of the FKH domain" and "DNA binding controls the dimerization of the FKH domain"; Figures 3 and 4 (location not provided).
- **Concern** The central conclusion that DNA destabilizes the dimer is inferred primarily from changes in FRET efficiency and fluorescence anisotropy populations. These observables report on the conformational state of the labeled domain, not directly on the oligomeric state. The increase in the low-FRET (disordered) population in the dimer sample upon DNA binding could be interpreted as a conformational change within a stable dimer, rather than a shift in the monomer-dimer equilibrium. The dimerization assay using BODIPY-labeled C57 variant and unlabeled R53H variant is the only direct test of the equilibrium shift, but the description is insufficient. It is unclear whether the assay measures the association of two labeled monomers, the exchange of labeled and unlabeled monomers, or a change in the conformational state of a pre-formed dimer. The authors must provide a more direct and quantitative demonstration that DNA binding increases the population of monomeric species or decreases the dimer dissociation constant.
- **Why it matters** The entire premise of the paper, that DNA acts as a negative regulator of dimerization, rests on this specific claim. If the evidence only supports a DNA-induced conformational change within the dimer, the conclusions are significantly weakened and the proposed mechanism of "negative allosteric control" is not supported.
- **Resolution test** The authors should perform a quantitative titration of the dimerization equilibrium in the presence and absence of DNA, using a method that directly reports on the oligomeric state, such as sedimentation equilibrium analytical ultracentrifugation, mass photometry, or a well-validated Förster resonance energy transfer (FRET) assay between two distinctly labeled monomers. The data should be fit to a thermodynamic model to extract the dimer dissociation constant (Kd) under both conditions. Alternatively, they could use a kinetic assay to show that DNA increases the dissociation rate of a pre-formed dimer.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor and data interpretation
- **Claim pointer** The manuscript states that "the monomeric form of the forkhead (FKH) domain of the human FoxP1 behaves as a disordered protein and increases its folded population when it dimerizes" and that "DNA binding promotes a disordered FKH dimer bound to DNA."
- **Evidence pointer** Results sections "The monomeric state of FoxP1's FKH domain exchanges between folded and disordered states" and "DNA binding differentially perturbs the monomeric and dimeric states of the FKH domain"; Figures 2 and 3 (location not provided).
- **Concern** The interpretation of the FRET and anisotropy data relies heavily on the assignment of specific populations to "folded" and "disordered" states. The static and dynamic lines used to interpret the data are model-dependent. The authors do not provide a clear quantitative measure of the "folded population" or the "disorder" in each condition. For example, what is the fraction of molecules in the high-FRET state in the monomer vs. the dimer, and how does this change upon DNA binding? The BVA and PDA analyses are mentioned, but the results are not presented in a way that allows the reader to assess the magnitude of the effects. The fFCS data are used to infer timescales of conformational transitions, but the assignment of specific correlation times to specific molecular processes (e.g., "conformational sampling of the disordered state") is speculative without additional validation.
- **Why it matters** The paper's conclusions are based on a semi-quantitative interpretation of complex single-molecule data. Without clear quantitative metrics (e.g., population fractions, rate constants, and their uncertainties), it is difficult to evaluate the strength of the evidence or to compare the effects of different conditions (e.g., monomer vs. dimer, absence vs. presence of DNA).
- **Resolution test** The authors should provide a table summarizing the key quantitative parameters extracted from their analyses. This should include the fractions of folded and disordered populations for each condition (monomer, dimer, with/without DNA), the associated rate constants for interconversion (from fFCS or PDA), and the uncertainties in these values. They should also show the fits of their models to the data, with residuals, to demonstrate the quality of the fits.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic model clarity
- **Claim pointer** The manuscript proposes a "DNA-mediated allostery that provides a DNA-mediated reversible (TF:DNA ⇌ TF:TF:DNA ⇌ function) gene regulatory function."
- **Evidence pointer** Discussion section; Figure 4D (location not provided).
- **Concern** The proposed mechanistic model is vague. The authors suggest that DNA binding "promotes a disordered FKH dimer" and that this "negatively controls the stability of the dimeric FoxP1:DNA complex." However, it is unclear how a disordered dimer would be less stable. Does DNA binding induce a conformational change in the dimer that weakens the protein-protein interface? Or does it promote the dissociation of the dimer into monomers that are then bound to DNA? The model in Figure 4D is not described in detail. The authors should provide a more explicit and testable model that connects the observed conformational changes to the thermodynamics and kinetics of the dimerization equilibrium.
- **Why it matters** A clear mechanistic model is essential for the paper to have a lasting impact. The current model is too general to be useful for designing future experiments or for making predictions about the behavior of other FoxP proteins or other TFs.
- **Resolution test** The authors should revise the model to explicitly state the order of events (e.g., DNA binding to monomer → conformational change → altered dimerization affinity) and the nature of the proposed allosteric pathway. They should also discuss how this model could be tested experimentally, for example, by using mutants that specifically disrupt the DNA-induced conformational change or the dimer interface.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and physiological relevance
- **Claim pointer** The manuscript states that "the DNA-mediated reversible regulation on FKH dimers suggests that FoxP1-dependent gene suppression is unstable, and it must require the presence of other dimerization domains or cofactors to revert the negative impact exerted by the DNA."
- **Evidence pointer** Summary and Discussion sections.
- **Concern** The study is performed on the isolated FKH domain in vitro. The authors speculate about the implications for full-length FoxP1 in a cellular context, but they do not provide any experimental evidence to support these claims. The FKH domain is only one part of the full-length protein, which also contains a leucine zipper domain and other regions. The behavior of the isolated domain may not reflect the behavior of the full-length protein, especially in the context of chromatin. The claim that "FoxP1-dependent gene suppression is unstable" is a significant extrapolation from the in vitro data.
- **Why it matters** The physiological relevance of the findings is a key part of the paper's significance. Without any cellular or in vivo data, the authors should be more cautious in their claims about the implications for gene regulation.
- **Resolution test** The authors should either (a) temper their claims about the physiological implications, clearly stating that these are speculative, or (b) provide additional experimental evidence, such as experiments with full-length FoxP1 or in a cellular context, to support their claims.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Experimental procedures
- **Evidence pointer** "Experimental procedures" section, "smMFS" and "Anisotropy measurements" subsections.
- **Issue** The description of the dimerization assay is not sufficiently detailed to be reproduced. The authors state that "we developed a dimerization assay using a BODIPY FL-labeled single-cysteine variant of FoxP1 to track the kinetics of the dimer formation by measuring steady-state anisotropy," but do not provide details on the concentrations of the labeled and unlabeled proteins, the buffer conditions, the temperature, or the method for calculating the association and dissociation rate constants from the anisotropy data.
- **Required correction** Provide a detailed step-by-step protocol for the dimerization assay, including all concentrations, buffer compositions, and the exact equations and fitting procedures used to extract the kinetic parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figures and tables
- **Evidence pointer** Figures 2, 3, and 4 (location not provided).
- **Issue** The figures are not provided in the manuscript text, making it impossible to assess the quality of the data and the fits. The text refers to "Figure 2B," "Figure 3C," etc., but the figures themselves are not included.
- **Required correction** Ensure that all figures and supplementary figures are included in the submission and that they are of high quality, with clear labels, error bars, and statistical annotations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction and Discussion sections.
- **Issue** The authors state that "there is little knowledge about the molecular effect DNA has on TFs" and that the reverse reaction (function → TF:TF:DNA → TF:DNA → TF + DNA) "has not been extensively explored." While this may be true, the authors should more thoroughly discuss the existing literature on allosteric effects of DNA on protein conformation and oligomerization, including examples from other transcription factor families.
- **Required correction** Add a more comprehensive discussion of related work, including studies on DNA-induced conformational changes in other TFs, to better contextualize the novelty of the current findings.

## Risk / unsupported claims
- The claim that "DNA binding promotes a disordered FKH dimer bound to DNA, negatively controlling the stability of the dimeric FoxP1:DNA complex" is not fully supported by the evidence presented, as the link between conformational disorder and dimer stability is not directly demonstrated.
- The claim that "the DNA-mediated reversible regulation on FKH dimers suggests that FoxP1-dependent gene suppression is unstable" is an extrapolation from in vitro data on an isolated domain to a complex cellular process, and is not supported by any direct experimental evidence.
- The claim that the monomeric FKH domain "behaves as a disordered protein" is based on FRET and simulation data, but the quantitative extent of this disorder and its functional significance are not fully characterized.
- The specific timescales assigned to conformational transitions from fFCS data (e.g., "conformational sampling of the disordered state") are speculative and not rigorously validated.