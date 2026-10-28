## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Technical and scientific evaluation of the Chronobot device, ice thickness quantification methods, and time-resolved cryo-EM structures of RecA homology search intermediates
- **Shared manuscript claim summary** The authors present Chronobot, a time-resolved cryo-EM sample preparation platform with deep learning-based ice thickness estimation, achieving an 11-fold improvement in sample quality. They apply this to capture RecA homology search intermediates at 250 ms, revealing dsDNA capture at site II and three-strand homology sampling states, and propose a model for early homology search.
- **Visible evidence base** Abstract, Introduction, Results (narrative), Discussion, Materials and Methods, figure legends referenced but figures not provided
- **Missing materials affecting confidence** Figures 1-4 and Extended Figures 1-8 not provided; Supplementary Tables not provided; no quantitative validation metrics for the deep learning model; no reconstruction validation statistics (FSC curves, local resolution maps); no particle counts or classification parameters for 3D classes

## Reviewer
- **Overall assessment** This manuscript describes a significant technical advance in time-resolved cryo-EM sample preparation, with a compelling biological application to RecA homology search. The Chronobot system integrates multiple engineering improvements and a novel deep learning-based ice thickness estimation approach. The biological findings, particularly the visualization of dsDNA capture at site II prior to homology sampling, are potentially important. However, the manuscript as presented has substantial gaps in validation and quantitative support that prevent full assessment of both the technical claims and the biological model. The absence of figures, validation metrics, and detailed reconstruction statistics makes it impossible to evaluate the core claims rigorously.
- **Who would be interested in the results, and why** Structural biologists developing time-resolved cryo-EM methods; researchers studying homologous recombination and RecA/Rad51 family mechanisms; cryo-EM methodologists interested in sample preparation optimization and machine learning applications; pharmaceutical researchers interested in structure-based drug discovery targeting recombination pathways.
- **Major strengths** The Chronobot platform addresses a critical bottleneck in time-resolved cryo-EM with a comprehensive engineering solution. The integration of deep learning for real-time ice thickness estimation is innovative and practically valuable. The application to RecA homology search is well-chosen, addressing a fundamental biological question with clear kinetic rationale. The proposed model of sequential dsDNA capture, homology sampling, and strand displacement provides a testable framework.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (deep learning model validation), R1-M2 (ice thickness metric definition), R1-M3 (reconstruction quality validation), R1-M4 (occupancy quantification), R1-M5 (model overinterpretation)
- **Assessment against Nature-style criteria** Originality: High. The Chronobot system represents a novel integration of engineering, machine learning, and cryo-EM. The biological application to capture millisecond-scale intermediates is innovative. Scientific importance: High if validated. Time-resolved cryo-EM is a rapidly advancing field, and robust sample preparation methods are urgently needed. The RecA findings could illuminate a fundamental process. Interdisciplinary readership: Strong. The work bridges engineering, machine learning, structural biology, and biochemistry. Technical soundness: Currently not fully assessable. The engineering and methods are described in detail, but key validation metrics and figures are missing. Readability for nonspecialists: Good. The manuscript is clearly written with appropriate context for each section, though some methods details are dense.
- **Recommendation posture** Supportive if technical concerns are resolved. The core concept and biological application are compelling, but the manuscript requires substantial additional validation data and clarification before the claims can be considered established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The deep learning model predicts ice thickness from high-speed camera videos, and this prediction is used for real-time sample quality assessment.
- **Evidence pointer** Results section "Rapid ice thickness estimation using deep learning"; Methods section "Deep learning methods for ice thickness estimation"; Extended Figure 3h-i
- **Concern** The manuscript claims the deep learning model provides accurate ice thickness estimates but does not report quantitative validation metrics. No correlation coefficients, mean absolute errors, or comparison against ground truth measurements are provided. The training dataset of 45,542 grid square pairs is described, but the distribution of ice thicknesses in this dataset, the accuracy on held-out test sets, and the generalizability across different grid types and sample conditions are not reported. The claim of "coarse estimate" in the Results is vague and does not establish the reliability needed for the claimed 11-fold improvement.
- **Why it matters** The deep learning model is a central component of the Chronobot workflow. Without quantitative validation, the reliability of the ice thickness predictions and the resulting optimization decisions cannot be assessed. This directly impacts the reproducibility and generalizability of the entire platform.
- **Resolution test** Provide quantitative validation of the deep learning model on held-out test data, including correlation with ground truth ice thickness measurements, error distributions, and performance across different ice thickness ranges. Report the accuracy of the model in classifying grid squares as usable or unusable for data collection.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The manuscript claims an 11-fold improvement in sample quality, defined as the number of holes with ice below 60 nm thickness.
- **Evidence pointer** Results section "Data-driven strategy for optimising time-resolved sample preparation"; Figure 3g-h
- **Concern** The primary metric for sample quality is the number of holes with ice below 60 nm. However, the manuscript does not provide the raw data or statistical analysis supporting the 11-fold improvement. The comparison is made to "our previously reported workflow" but the baseline numbers are not given. Additionally, the threshold of 60 nm is stated as empirical but no justification or sensitivity analysis is provided. The variability between grids and experiments is not reported, making it impossible to assess whether the improvement is statistically significant.
- **Why it matters** The 11-fold improvement is a headline claim of the manuscript. Without supporting data and statistical analysis, this claim cannot be evaluated. The choice of 60 nm as the threshold and the robustness of this metric need to be justified.
- **Resolution test** Provide the distribution of ice thickness measurements for the baseline and optimized conditions, including the number of holes, the mean and standard deviation of ice thickness, and the statistical significance of the improvement. Justify the 60 nm threshold with reference to achievable resolution or provide a sensitivity analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural validation
- **Claim pointer** The time-resolved cryo-EM reconstructions of RecA mini-filaments with dsDNA substrates achieve 3.2 and 3.1 Å resolution and reveal distinct conformational states.
- **Evidence pointer** Results section "Three-dimensional dynamics govern RecA homology search at millisecond timescales"; Figure 4b-i; Extended Figures 6-8
- **Concern** The manuscript reports high-resolution reconstructions but does not provide standard validation metrics. No FSC curves, local resolution maps, or particle numbers are given. The classification strategy is described only briefly, and the number of particles in each class is not reported. The claim of distinct conformational states relies on visual interpretation of density, but the resolution of the relevant regions (site II, L2 loops, CTD) is not assessed. The manuscript also does not state whether the reconstructions are from a single dataset or merged across multiple grids, which is critical for time-resolved experiments.
- **Why it matters** The biological conclusions depend entirely on the quality and interpretability of the cryo-EM reconstructions. Without standard validation metrics, the reliability of the observed conformational states cannot be assessed. The distinction between genuine intermediates and reconstruction artifacts is a central concern.
- **Resolution test** Provide FSC curves, local resolution maps, particle counts, and classification parameters for all reported reconstructions. Assess the local resolution in the regions where novel density is interpreted (site II, L2 loops, CTD). State whether reconstructions are from single or merged datasets and report the number of micrographs and particles used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative analysis
- **Claim pointer** The manuscript states that the 7-nt substrate exhibits approximately 50% occupancy at 250 ms, while the 8-nt substrate shows nearly 100% occupancy.
- **Evidence pointer** Results section "Three-dimensional dynamics govern RecA homology search at millisecond timescales"; Figure 4d-e
- **Concern** The occupancy values are stated without any description of how they were quantified. No error bars, number of particles, or statistical comparison between conditions are provided. The claim that 50% occupancy is "consistent with its reported half-life" is not quantitatively supported. The manuscript does not describe how occupancy was defined or measured, nor how the 250 ms time point was verified.
- **Why it matters** The differential occupancy between 7-nt and 8-nt substrates is a key biological finding that supports the model of homology length discrimination. Without quantitative rigor, this claim is not established.
- **Resolution test** Describe the method for quantifying occupancy, including the number of particles in each state, the criteria for assigning a particle to a state, and the statistical significance of the difference between 7-nt and 8-nt conditions. Provide error estimates and discuss potential biases in classification.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Model interpretation
- **Claim pointer** The manuscript proposes a model where dsDNA is first captured at site II, then transitions to three-strand homology sampling, and finally achieves stable homology binding with the complementary strand displaced to site II.
- **Evidence pointer** Discussion section "Visualising time-resolved RecA homology search initiation intermediates"; Figure 4j
- **Concern** The proposed model is based on a limited number of observed states at a single time point (250 ms). The manuscript does not provide evidence for the temporal ordering of these states, as only one time point was collected. The model is presented as a linear sequence, but the data cannot distinguish between sequential steps and parallel pathways. The manuscript acknowledges this limitation in the Discussion but does not address how future experiments would test the model.
- **Why it matters** The model is a significant interpretive claim that goes beyond the direct observations. Without additional time points or kinetic analysis, the proposed sequence of events remains speculative.
- **Resolution test** Collect additional time points to establish temporal ordering, or use biochemical assays to test the predicted intermediates. Alternatively, temper the model claims to reflect the uncertainty in temporal ordering.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Rapid ice thickness estimation using deep learning"
- **Evidence pointer** Figure 3a-c
- **Issue** The description of the deep learning model architecture is incomplete. The manuscript mentions DeepLabv3 with a custom decoder but does not specify the input resolution, the number of parameters, the training loss values, or the inference time. The claim of "real-time" inference is not quantified.
- **Required correction** Provide details on the model architecture, training procedure, and inference speed. Report the inference time per grid square and the computational resources required.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Analytical methods for ice thickness estimation"
- **Evidence pointer** Extended Figure 3a-f
- **Issue** The ALS coefficient at 150x magnification is stated as 133.9, but the calibration procedure is not fully described. The manuscript mentions a two-step calibration from 150,000x to 150x but does not report the uncertainty in this value or how it was validated across different microscopes or sessions.
- **Required correction** Describe the calibration procedure in detail, including the number of calibration datasets, the variability in the ALS coefficient, and any cross-validation performed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and Code Availability section
- **Evidence pointer** Not applicable
- **Issue** The manuscript states that data and code will be released upon publication, but no repository identifiers or accession numbers are provided. For a methods paper, this is a significant limitation for reproducibility.
- **Required correction** Provide repository links or accession numbers for the code, trained model weights, and representative datasets. If deposition is pending, state the expected timeline.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "Systematic improvements of ice quality for time-resolved cryo-EM"
- **Evidence pointer** Figure 3h
- **Concern** The improvements in sample quality are reported as percentages (e.g., 318% for gold grids), but the number of replicate grids and the variability between them are not reported. The manuscript does not state whether these improvements were consistent across multiple experiments.
- **Required correction** Report the number of replicate grids for each condition and provide measures of variability (e.g., standard deviation, range). State whether the improvements were reproducible across independent experiments.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Discussion section "Visualising time-resolved RecA homology search initiation intermediates"
- **Evidence pointer** Figure 4j
- **Concern** The manuscript discusses the role of the RecA CTD in homology search but does not compare the observed CTD interactions with those reported in previous structural studies of RecA or Rad51. A more detailed comparison with existing literature would strengthen the biological interpretation.
- **Required correction** Add a comparison of the observed CTD binding modes with those reported in previous RecA/Rad51 structures, highlighting similarities and differences.

## Risk / unsupported claims
- The 11-fold improvement in sample quality is not quantitatively supported without raw data and statistical analysis.
- The deep learning model accuracy is not validated with quantitative metrics.
- The occupancy values for 7-nt and 8-nt substrates are stated without error estimates or statistical comparison.
- The temporal ordering of the proposed homology search intermediates is not supported by the single time point data.
- The claim that the observed states represent "molecular choreography" implies a dynamic sequence that is not directly observed.
- The generalizability of the Chronobot platform to other biological systems is asserted but not demonstrated.
- The statement that the deep learning model provides "coarse" estimates is vague and does not establish the reliability needed for the claimed improvements.