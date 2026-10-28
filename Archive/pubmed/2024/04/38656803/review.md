## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure references.
- **Assessment boundary** Scientific content, experimental and computational methodology, data interpretation, and alignment with claims. No assessment of formatting, grammar, or editorial fit.
- **Shared manuscript claim summary** The authors propose that BRD4 condensation is modulated by its binding to acetylated chromatin, which enhances both kinetic (nucleation rate) and thermodynamic (critical valence) properties of phase separation, and that this dual mechanism explains selective targeting of BRD4 condensates to acetylated chromatin loci.
- **Visible evidence base** Live-cell imaging (immunofluorescence, Corelet optogenetic system, JQ1 washout), quantitative image analysis (puncta count, size, volume, nucleation rate, delay time, number density, Pearson correlation coefficients), coarse-grained molecular dynamics simulations (phase diagrams, nucleation trajectories), and pharmacological perturbations (JQ1, A485, TSA).
- **Missing materials affecting confidence** No raw data files, no detailed simulation parameter tables, no statistical test details (e.g., exact p-values, sample sizes per condition beyond "25 nuclei per well, 4 biological replicates"), no supplementary figures or movies referenced in the text, no code or input files for simulations, no detailed image analysis pipeline validation.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and well-integrated combination of live-cell experiments and coarse-grained simulations to address a significant question in the field of biomolecular condensates: how chromatin binding influences the formation and targeting of transcriptional condensates. The authors provide strong evidence that BRD4 chromatin binding enhances both thermodynamic stability and nucleation kinetics of condensates, and they propose a mechanistic model that reconciles these observations. The work is technically sound in its core approaches, though several aspects of the quantitative analysis and simulation methodology require clarification to fully establish the claims. The findings are likely to be of broad interest to researchers studying phase separation, chromatin biology, and transcriptional regulation.
- **Who would be interested in the results, and why** Researchers in the fields of biomolecular condensates and phase separation, chromatin biology and epigenetics, transcriptional regulation, and biophysics. The work provides a framework for understanding how substrate interactions can modulate condensate properties, which is relevant to many nuclear processes beyond BRD4. The combination of experimental and computational approaches will also appeal to those interested in quantitative cell biology.
- **Major strengths** 1) The study addresses a timely and important question about the interplay between condensation and chromatin binding, which is underexplored. 2) The use of multiple complementary experimental systems (endogenous, exogenous, Corelet) and perturbations (JQ1, A485, TSA) strengthens the conclusions. 3) The coarse-grained simulations provide mechanistic insight and are validated against experimental phase diagrams. 4) The quantitative metrics (nucleation rate, delay time, number density, PCC) are well-chosen to test the proposed model. 5) The writing is clear and accessible, with a logical progression from observation to mechanism.
- **Major Concerns** 
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: No)
  - **R1-M4** (Blocking: No)
- **Minor Comments** 
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking concerns that must be resolved. R1-M3 and R1-M4 are non-blocking but should be addressed to strengthen the manuscript.
- **Assessment against Nature-style criteria** 
  - **Originality** High. The study introduces a novel perspective on how substrate binding modulates condensate thermodynamics and kinetics, which is a relatively unexplored area.
  - **Scientific importance** High. The findings have implications for understanding transcriptional regulation and the role of epigenetic marks in organizing nuclear compartments.
  - **Interdisciplinary readership** Moderate to high. The work bridges cell biology, biophysics, and computational modeling, and should appeal to a broad audience.
  - **Technical soundness** Moderate. The experimental and computational approaches are generally appropriate, but several methodological details and potential artifacts need to be addressed to fully support the conclusions.
  - **Readability for nonspecialists** Good. The manuscript is well-written and explains concepts clearly, though some sections (e.g., simulation details) may be challenging for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are novel and potentially important, but the blocking concerns regarding quantitative rigor and simulation validation must be addressed before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The authors claim that "chromatin binding provides a thermodynamic enhancement of BRD4 condensation" based on a shift in critical valence from 5-6 (off-chromatin) to 2 (on-chromatin) in the Corelet system.
- **Evidence pointer** Figure 2E, 2F; Results section "Chromatin binding thermodynamically enhances BRD4 condensation"
- **Concern** The phase diagrams in Figure 2E and 2F are based on a limited number of data points and rely on qualitative classification of "Yes PS" vs "No PS" by two observers. The logistic regression fit is used to determine critical valence, but the manuscript does not provide confidence intervals for these estimates, nor does it report the number of cells at each concentration/valence point. The shift from valence 2 to 5-6 upon JQ1 treatment is a key quantitative claim, but without error bars or statistical comparison, it is difficult to assess the robustness of this difference. Additionally, the authors note that "extremely low Core concentration is sufficient to initiate BRD4FL condensate formation" and that the left-hand boundary is absent, which complicates the interpretation of the phase diagram. The lack of a clear saturation concentration in the control condition makes the thermodynamic interpretation ambiguous.
- **Why it matters** The quantitative difference in critical valence is central to the claim that chromatin binding thermodynamically enhances condensation. If this difference is not statistically robust, the thermodynamic argument is weakened.
- **Resolution test** Provide confidence intervals for the critical valence estimates from the logistic regression, report the number of cells and replicates for each data point, and perform a statistical test (e.g., likelihood ratio test) comparing the fits with and without JQ1. Additionally, clarify how the absence of a left-hand boundary in the control phase diagram is handled in the analysis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation validation
- **Claim pointer** The authors claim that "the critical valence for phase separation in the absence of chromatin is between 5 and 6 BRD4 molecules per Core oligomerization platform" from simulations, and that this matches the experimental value of 5-6.
- **Evidence pointer** Figure 3B; Results section "Coarse-grained simulations characterize valence dependence of BRD4 condensation"
- **Concern** The simulation model is described qualitatively, but key parameters (e.g., interaction strengths, Flory-Krigbaum parameters, radii of gyration) are not provided in the main text or methods. The authors state that "interaction strengths are chosen to reproduce the experimental phase diagram," which raises concerns about circularity: if the simulations are parameterized to match the experimental phase diagram, then the agreement between simulation and experiment is not an independent validation. The manuscript does not specify how the interaction strengths were tuned, nor does it show a sensitivity analysis. Furthermore, the simulation phase diagram in Figure 3B appears to be based on a single set of conditions, and it is unclear how the critical valence was determined from the simulation data.
- **Why it matters** The agreement between simulation and experiment is a key pillar of the manuscript's argument. If the simulations are not independently validated or if the parameterization is circular, the mechanistic conclusions drawn from the simulations are not well-supported.
- **Resolution test** Provide a table of all simulation parameters, describe the parameterization procedure in detail, and show that the model can reproduce experimental results without fine-tuning to the specific phase diagram. Perform a sensitivity analysis to show that the predicted critical valence is robust to reasonable variations in interaction strengths. Additionally, describe how the critical valence was extracted from the simulation data (e.g., from coexistence densities or nucleation trajectories).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The authors claim that "acetylated chromatin regions act as heterogeneous seeds for BRD4 condensate nucleation" based on the observation that condensates reform at similar positions after JQ1 washout.
- **Evidence pointer** Figure 4I-4K; Results section "Chromatin acts as a heterogeneous seed for BRD4 condensate nucleation in cells"
- **Concern** The JQ1 washout experiment shows that condensates reform at correlated positions, but the correlation is measured over a short time window (2 min of JQ1 treatment). It is unclear whether this correlation reflects stable chromatin binding sites or simply the persistence of local nuclear architecture (e.g., pre-existing clusters of BRD4 that were not fully dispersed). The authors do not report the time scale of BRD4 diffusion or the stability of the correlation over longer timescales. Additionally, the PCC values are reported without error bars or statistical comparison to a null model (e.g., random positions).
- **Why it matters** The claim of heterogeneous nucleation at specific chromatin sites is a central mechanistic conclusion. If the correlation is not robust or is confounded by other factors, the interpretation is weakened.
- **Resolution test** Report PCC values with error bars and compare to a null model (e.g., random placement of condensates). Extend the observation time after washout to show that the correlation persists. Consider using a more specific marker of acetylated chromatin to directly demonstrate co-localization with nucleation sites.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors propose that "epigenetic modification of chromatin allows for rapid condensation of transcriptional activators like BRD4 at specific chromatin sites" and suggest this may be a general mechanism.
- **Evidence pointer** Discussion section
- **Concern** The study focuses exclusively on BRD4 and uses a limited set of perturbations (JQ1, A485, TSA) that affect global acetylation levels. The authors do not test whether the proposed mechanism applies to other transcriptional activators or to specific genomic loci. The claim of generalizability is speculative and not directly supported by the data.
- **Why it matters** The broader significance of the work depends on whether the mechanism is generalizable. Without evidence from other systems, the conclusions are limited to BRD4.
- **Resolution test** Discuss the limitations of the study more explicitly and avoid overgeneralizing. If possible, provide preliminary data from another transcriptional activator or a specific locus to support the generalizability claim.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 4C-4E
- **Evidence pointer** Results section "Chromatin acts as a heterogeneous seed for BRD4 condensate nucleation in cells"
- **Issue** The manuscript reports significant differences in nucleation rate, delay time, and number density between control and JQ1-treated cells, but does not provide specific p-values or effect sizes.
- **Required correction** Report exact p-values and effect sizes for all statistical comparisons, or state that these are not available.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Image analysis
- **Evidence pointer** Methods section "Image analysis for count, size, total area, and volume of puncta per nucleus"
- **Issue** The thresholding methods (Otsu, IsoData) are mentioned, but the criteria for distinguishing puncta from background are not fully described. It is unclear how the authors handled cells with high background fluorescence or overlapping puncta.
- **Required correction** Provide a more detailed description of the image analysis pipeline, including any manual curation steps and quality control measures.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Simulation details
- **Affected element** Methods section "Coarse-grained model"
- **Evidence pointer** Methods section "Coarse-grained model"
- **Issue** The simulation model is described qualitatively, and the mapping between simulation units and physical units is not specified.
- **Required correction** Provide a table of all simulation parameters, including units, and describe how the model was mapped to the experimental system.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods section "Request a protocol through Bio-protocol"
- **Evidence pointer** Methods section "Request a protocol through Bio-protocol"
- **Issue** The methods section refers to a protocol through Bio-protocol, but no protocol ID or link is provided.
- **Required correction** Provide the protocol ID or link, or include the full protocol in the supplementary materials.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Figure 5
- **Evidence pointer** Results section "Coarse-grained simulations characterize BRD4 chromatin-seeded nucleation behavior"
- **Issue** The simulation snapshots in Figure 5 are described but not shown in the main text. It is unclear how the reader can visualize the nucleation events described.
- **Required correction** Include representative simulation snapshots in the main text or supplementary figures, or provide a more detailed description of the simulation trajectories.

## Risk / unsupported claims
- The claim that "epigenetic modification of chromatin allows for rapid condensation of transcriptional activators like BRD4 at specific chromatin sites" is presented as a general mechanism but is only demonstrated for BRD4 under global acetylation changes. This is an extrapolation beyond the data.
- The claim that "chromatin binding provides a thermodynamic enhancement of BRD4 condensation" is supported by the critical valence shift, but the statistical robustness of this shift is not established (see R1-M1).
- The claim that "acetylated chromatin regions act as heterogeneous seeds" is supported by the washout experiments, but the correlation could be confounded by other factors (see R1-M3).
- The simulation results are presented as validating the experimental findings, but the parameterization procedure may be circular (see R1-M2).