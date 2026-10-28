## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and conclusions as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors use enhanced sampling and molecular dynamics simulations to map the pathway of cyclobutane pyrimidine dimer (CPD) recognition by Rad4/XPC, proposing a sequential order of events: 5′-dA flips out before 3′-dA, and both flips occur before BHD3 β-hairpin insertion into the DNA lesion site.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results and Discussion, Conclusion, Data Availability, Funding, Acknowledgements. Figures are referenced but not provided.
- **Missing materials affecting confidence** Figures 1–12, supplementary information, simulation parameter files, force field parameter details for the CPD lesion, and convergence analyses are not provided. These are essential for verifying the technical soundness of the simulations and the validity of the free energy profiles.

## Reviewer
- **Overall assessment** The manuscript addresses a significant and timely question in DNA repair: the dynamic pathway by which Rad4/XPC recognizes CPD lesions. The use of enhanced sampling simulations to explore multiple intermediate states is a reasonable approach. However, the current manuscript has several technical and presentational issues that prevent a full assessment of the claims. The lack of figures and detailed convergence data makes it impossible to verify the robustness of the free energy profiles. The interpretation of the PMFs, particularly the derivation of the deinsertion energy, requires more careful justification. The manuscript would benefit from a clearer articulation of the novelty relative to prior computational studies and a more rigorous discussion of the limitations of the chosen collective variables.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, genome stability, computational biophysics, and molecular dynamics simulation. The proposed sequential pathway and the energetic estimates could inform future experimental and computational studies on lesion recognition by XPC and related proteins.
- **Major strengths** The study addresses a mechanistically important and challenging problem. The use of multiple intermediate models and sequential umbrella sampling to probe the order of events is a thoughtful strategy. The authors explicitly consider alternative pathways and provide a clear summary of their proposed sequence of events.
- **Major Concerns** The concerns are detailed below.
- **Minor Comments** The concerns are detailed below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The question of the order of events in CPD recognition is important, but the approach of using umbrella sampling on a known complex is not entirely novel. Scientific importance: High, as understanding lesion recognition is central to NER. Interdisciplinary readership: The topic is of interest to structural biologists, biochemists, and computational chemists, but the presentation is heavily technical. Technical soundness: Cannot be fully assessed without figures and convergence data. Readability for nonspecialists: The manuscript is dense and assumes significant prior knowledge of simulation techniques and the Rad4 system.
- **Recommendation posture** Currently not established from the provided evidence. The core claims are plausible but not verifiable without the missing figures and technical details.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the free energy profiles for the deinsertion of the BHD3 β-hairpin and the flipping of partner bases are reliable and support the proposed order of events.
- **Evidence pointer** Results and Discussion, Figures 5–10 (figures not provided)
- **Concern** The manuscript does not provide any convergence analysis for the umbrella sampling simulations. It is not stated how many replicas were run, how long each window was simulated, or whether the PMFs were stable over time. Without this information, the reliability of the reported free energy barriers and minima cannot be assessed.
- **Why it matters** Umbrella sampling results are only meaningful if the simulations are converged. If the PMFs are not converged, the proposed energetics and the derived order of events are not supported.
- **Resolution test** Provide convergence plots (e.g., PMF as a function of simulation time), the number of windows, the total simulation time per window, and the overlap of the umbrella histograms.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that the deinsertion energy is estimated to be 4.96 kcal mol−1, derived from the difference between the downhill energy loss for Model A (41.81 kcal mol−1) and the uphill energy cost for Model F (46.77 kcal mol−1).
- **Evidence pointer** Results and Discussion, Figure 5 (figure not provided)
- **Concern** The derivation of the deinsertion energy from the difference of two large numbers is not clearly justified. The two PMFs are computed for different states (Model A with extrahelical partners and CPD, Model F with intrahelical partners and CPD), and the difference may not directly correspond to a physical deinsertion free energy. The manuscript does not explain why this subtraction is valid.
- **Why it matters** The deinsertion energy is a key quantitative result. If the derivation is flawed, the reported value is meaningless and could mislead future studies.
- **Resolution test** Provide a clear thermodynamic cycle or a detailed explanation of why the difference between the two PMFs corresponds to the deinsertion free energy. Alternatively, compute the deinsertion free energy directly using a single PMF that connects the inserted and deinserted states.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the flipping of 5′-dA occurs before that of 3′-dA, based on comparisons of free energy profiles from different models.
- **Evidence pointer** Results and Discussion, Figures 6–8 (figures not provided)
- **Concern** The comparison of free energy profiles from different models (Model B, C, D) to infer the order of events is not straightforward. The manuscript does not clearly explain how the differences in the PMFs translate into a kinetic or thermodynamic preference for one order over another. The free energy profiles are computed along different collective variables (γ, γ′, δ), and the barriers and minima are not directly comparable without a common reference state.
- **Why it matters** The proposed sequential order is a central claim of the manuscript. If the comparison is not rigorous, the conclusion is not supported.
- **Resolution test** Provide a clear framework for comparing the PMFs, such as computing the free energy of each intermediate state relative to a common reference, or performing simulations that directly sample the transition between the two possible orders.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that the CPD lesion was added to the open complex and that the partner thymines were replaced by adenines, but the force field parameters for the CPD lesion are not described in detail.
- **Evidence pointer** Materials and Methods, Models section
- **Concern** The manuscript states that the partial charges of the CPD lesion were assigned using Antechamber and the remaining parameters were adopted from GAFF. However, the specific parameters used for the cyclobutane ring and the modified base are not provided. The accuracy of the simulation results depends critically on the quality of these parameters.
- **Why it matters** If the CPD parameters are not validated or are inaccurate, the simulation results, particularly the energetics of flipping and hairpin insertion, could be significantly biased.
- **Resolution test** Provide the full parameter set for the CPD lesion, including partial charges, and cite or perform validation studies (e.g., comparison with QM calculations or experimental data).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript claims that the simulations were performed using AMBER 2018.10 with PLUMED 2.5, but the specific input files and simulation protocols are not provided.
- **Evidence pointer** Materials and Methods, Molecular dynamics simulation section
- **Concern** The manuscript does not provide the specific input files, topology files, or detailed simulation protocols (e.g., temperature coupling, pressure coupling, integration time step, equilibration procedure) needed to reproduce the simulations. The data availability statement provides a link to a Zenodo repository, but the contents of this repository are not described.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without the input files and protocols, other researchers cannot verify or build upon the results.
- **Resolution test** Provide a detailed description of the simulation protocols in the main text or supplementary information, and ensure that the Zenodo repository contains all necessary files (e.g., input files, topology files, parameter files, and analysis scripts).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "nine intermediate states" were considered, but the main text describes models A through I, which is nine states. The abstract should be consistent with the main text.
- **Required correction** Clarify the number of intermediate states in the abstract or main text to ensure consistency.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion
- **Evidence pointer** Results and Discussion, BHD3 β-hairpin deinsertion section
- **Issue** The manuscript states that the energy minimum for Model A is at η ∼ 3 Å, but the crystal structure value is not explicitly given. The text mentions a shift of 2 Å compared to the crystal structure, but the actual crystal structure value is not stated.
- **Required correction** Provide the crystal structure value of η for clarity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion
- **Evidence pointer** Results and Discussion, Flipping of CPD partner bases section
- **Issue** The manuscript uses the terms "flipped out" and "flipped in" without defining them clearly. It would be helpful to define these terms in the context of the collective variables used.
- **Required correction** Define "flipped out" and "flipped in" in terms of the collective variables γ, γ′, and δ.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Figures 5–11 (not provided)
- **Issue** The manuscript references multiple figures, but the figures are not provided in the manuscript text. This makes it impossible to evaluate the data.
- **Required correction** Ensure that all figures are included in the manuscript or supplementary information.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusion
- **Evidence pointer** Conclusion
- **Issue** The conclusion states that "the flipping of partner bases occurs before the insertion of the BHD3 β-hairpin," but this is based on simulations that started from the bound state and reversed the process. The authors should clarify that this is a proposed pathway based on reverse simulations.
- **Required correction** Clarify that the proposed order is inferred from reverse simulations and may not reflect the forward pathway.

## Risk / unsupported claims
- The claim that the deinsertion energy is 4.96 kcal mol−1 is not supported by the provided evidence, as the derivation is not clearly justified.
- The claim that 5′-dA flips before 3′-dA is not fully supported, as the comparison of PMFs from different models is not rigorously explained.
- The claim that the proposed pathway is the most likely sequence of events is not supported by kinetic or thermodynamic data that directly compare alternative pathways.
- The reliability of all free energy profiles is unassessable due to the lack of convergence data and figures.