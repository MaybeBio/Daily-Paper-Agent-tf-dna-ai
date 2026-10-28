## Review setup
- **Input scope** Full manuscript text (main text, methods, figure legends, supplemental information descriptions)
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and alignment with Nature-style criteria based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present a coarse-grained (CG) computational model of the E. coli single-stranded DNA-binding protein (SSB) and its interaction with single-stranded DNA (ssDNA), parameterized using all-atom molecular dynamics (MD) simulations via iterative Boltzmann inversion (IBI). They demonstrate that the model reproduces experimentally measured force-extension behavior of SSB-ssDNA complexes, captures strand replacement and exchange kinetics, and can be extended to simulate a T7 bacteriophage replication fork trombone loop with multiple SSB proteins. The authors argue this represents a step toward replacing single-molecule biophysics experiments with in silico simulations.
- **Visible evidence base** Main text (Summary, Introduction, Results, Discussion, Limitations), STAR Methods, figure legends (Figures 1-7), supplemental video descriptions (Videos S1-S9), supplemental figure descriptions (Figures S1-S3)
- **Missing materials affecting confidence** Actual figure images, supplemental figures S1-S3, supplemental videos S1-S9, quantitative error bars or statistical analysis details, simulation parameter files, force-extension experimental data (referenced as provided by Chem lab but not shown), convergence metrics for IBI iterations, and detailed analysis of the 48 replicate simulations beyond summary statistics

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious and largely successful effort to develop a CG model of SSB-ssDNA interactions that bridges atomistic simulation and single-molecule experimental observables. The methodological framework, combining bottom-up parameterization from all-atom MD with top-down adjustments, is sound and the validation against experimental force-extension data is compelling. The extension to multi-protein systems and the trombone loop model demonstrates the potential of the approach. However, several concerns limit the strength of the claims as presented. The kinetic interpretation is complicated by the acknowledged, process-dependent acceleration of dynamics, and the authors appropriately caution against over-interpreting absolute rates. The neglect of SSB's intrinsically disordered C-terminal tails, while justified, may have more significant consequences for the multi-protein and trombone loop simulations than the authors acknowledge. The statistical treatment of the 48 replicate simulations is not fully described, and the comparison to experimental data, while visually impressive, lacks quantitative error analysis. The trombone loop model, while novel, is presented as a proof-of-concept with limited validation. Overall, this is a valuable contribution to the field of computational biophysics, but the claims of "replacing experiments" are premature and the current evidence does not fully establish the model's predictive power beyond the specific systems tested.
- **Who would be interested in the results, and why** Researchers in computational biophysics and molecular dynamics simulation, particularly those developing CG models of protein-nucleic acid interactions. Single-molecule experimentalists studying DNA replication, repair, and SSB function would be interested in the model as a tool for interpreting their data and generating mechanistic hypotheses. The broader community studying DNA replication machinery, including the replisome, would find the trombone loop model of interest. The methodological approach to bridging atomistic and CG scales is relevant to a wide range of biomolecular simulation problems.
- **Major strengths** The manuscript presents a clear and well-structured methodological framework for developing CG models of protein-DNA interactions. The validation against experimental force-extension data is a significant strength, demonstrating quantitative agreement without parameterization against that specific observable. The extension to multi-protein systems and the trombone loop represents a novel and ambitious application. The authors are appropriately cautious about the limitations of their model, particularly regarding kinetics and the neglect of C-terminal tails. The writing is clear and accessible, with good use of figures to illustrate the model and results.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (kinetic rate claims), R1-M2 (statistical analysis of replicates), R1-M3 (trombone loop validation)
- **Assessment against Nature-style criteria** 
  - **Originality** The work is original in its specific combination of bottom-up CG parameterization for a full protein-DNA complex, validation against single-molecule force spectroscopy, and application to a multi-protein replication fork structure. The concept of "in silico single-molecule experiments" is not entirely new, but the specific implementation and the trombone loop model are novel contributions.
  - **Scientific importance** The work addresses an important gap between atomistic simulation and single-molecule experiments, providing a framework that could be broadly applicable. The trombone loop model, if validated, could provide significant insights into DNA replication mechanisms. However, the importance is somewhat limited by the acknowledged limitations and the proof-of-concept nature of the most ambitious application.
  - **Interdisciplinary readership** The work bridges computational biophysics, single-molecule biophysics, and DNA replication biochemistry. The writing is generally accessible to nonspecialists, though some familiarity with simulation methods and single-molecule techniques is assumed. The potential readership extends across these fields.
  - **Technical soundness** The methodological approach is technically sound, with appropriate use of established techniques (IBI, CG MD, rigid body dynamics). The validation against experimental data is appropriate, though the lack of quantitative error analysis is a weakness. The statistical treatment of replicate simulations needs more detail.
  - **Readability for nonspecialists** The manuscript is generally well-written and the figures are informative. The Summary and Introduction provide good context. However, some sections, particularly the methods, assume significant background knowledge. The Discussion could more clearly articulate the broader implications for nonspecialist readers.
- **Recommendation posture** Supportive if technical concerns are resolved. The core methodological contribution and the validation against experimental data are strong. However, the claims regarding kinetics and the trombone loop model need to be tempered or better supported. The statistical analysis needs to be more rigorous. If these concerns are addressed, this could be a valuable contribution to the field.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The manuscript states that the model can be used to study the kinetics of SSB-ssDNA interactions, including strand exchange and replacement, and presents rates such as the exchange rate of approximately 0.28 μs⁻¹. The authors acknowledge that dynamics are accelerated but do not provide a quantitative framework for interpreting these rates.
- **Evidence pointer** Results section "Kinetics of SSB-ssDNA interactions", Figure 5, Figure 6D, Discussion
- **Concern** The authors acknowledge that CG dynamics are accelerated in a process-dependent manner but do not provide any quantitative correction or even a qualitative framework for relating simulated timescales to experimental timescales. The claim that the model can be used to study kinetics is therefore not well supported. The exchange rate of 0.28 μs⁻¹ is presented without any indication of how this relates to the true experimental rate. Without a method to calibrate or correct for the acceleration, the kinetic information from the model is of limited quantitative value. The authors should either provide a calibration against known experimental rates or temper their claims about the model's utility for kinetic studies.
- **Why it matters** The stated goal of the work is to enable in silico single-molecule experiments. If the kinetics cannot be quantitatively interpreted, this goal is only partially achieved. The process-dependent acceleration is a fundamental limitation of CG models, and the manuscript should address this more directly.
- **Resolution test** The authors should either (1) provide a quantitative comparison of simulated and experimental rates for at least one process, with a clear statement of the acceleration factor, or (2) explicitly state that the model is only suitable for studying thermodynamic properties and qualitative mechanistic pathways, not quantitative kinetics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript states that 48 replicate simulations were performed for the SSB exchange study and that the likelihood of successful transfer was determined. The probability of exchange versus time is shown in Figure 6D with an exponential fit.
- **Evidence pointer** Results section "Exchange of SSB proteins bound to ssDNA", Figure 6D, STAR Methods
- **Concern** The statistical analysis of the 48 replicate simulations is not described in sufficient detail. It is unclear how the exchange events were identified algorithmically, what the criteria were for defining a successful exchange, and how the uncertainty in the exchange probability was estimated. The exponential fit to the exchange probability versus time is shown, but the goodness of fit and the uncertainty in the fitted rate are not reported. Additionally, the authors state that "multiple transfer events within a continuous simulation trajectory were considered as independent events," which raises questions about the statistical independence of the observations.
- **Why it matters** The quantitative claims about exchange rates and probabilities depend on the statistical rigor of the analysis. Without proper error analysis, it is impossible to assess the significance of the reported differences in exchange probability between different strand lengths (e.g., 60% for dT70 displacing dT65 vs. 90% for dT60 displacing dT55).
- **Resolution test** The authors should provide a detailed description of the algorithmic detection of exchange events, the criteria for success/failure, and a proper statistical analysis including confidence intervals or error bars on the reported probabilities and rates. The independence assumption for multiple events within a single trajectory should be justified or addressed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of the trombone loop model
- **Claim pointer** The manuscript claims to present "the first structurally correct physical model of a trombone loop" and uses this model to investigate the possible structure of the loop within a DNA replication fork.
- **Evidence pointer** Results section "Model of the T7 bacteriophage trombone loop saturated with bacterial SSB", Figure 7, Discussion
- **Concern** The trombone loop model is presented as a significant achievement, but the validation is limited. The model is constructed by manually docking proteins into a cryo-EM map and using potential maps derived from the SSB-SSB interaction protocol. However, there is no quantitative comparison to any experimental data for the trombone loop structure or dynamics. The claim that this is "structurally correct" is not supported by direct evidence. The simulation shows that the loop becomes more compact and that SSB proteins can share the ssDNA strand, but these observations are not validated against any experimental measurements. The prediction that a single SSB protein can stably bind to both ends of the loop is interesting but untested.
- **Why it matters** The trombone loop model is presented as a key outcome of the work, demonstrating the power of the approach. If the model is not validated, the claim of providing a "structurally correct" model is overstated. The lack of validation limits the confidence in the biological conclusions drawn from the simulation.
- **Resolution test** The authors should either (1) provide quantitative validation of the trombone loop model against experimental data (e.g., FRET measurements, hydrodynamic data, or other structural information), or (2) clearly state that the model is a proof-of-concept and that the structural predictions are hypotheses to be tested experimentally.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** STAR Methods, "Refinement of CG SSB potentials"
- **Evidence pointer** STAR Methods, "Refinement of CG SSB potentials"
- **Issue** The description of the IBI procedure is somewhat terse. The authors mention that the initial potential was divided by a factor of ten and that a mask was applied, but the rationale for these choices and the sensitivity of the final results to these parameters are not discussed.
- **Required correction** Provide additional detail on the IBI procedure, including the rationale for the scaling factor and mask, and ideally a sensitivity analysis showing that the final results are robust to reasonable variations in these parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of model description
- **Affected element** Model of SSB-SSB interactions
- **Evidence pointer** Results section "Exchange of SSB proteins bound to ssDNA", STAR Methods
- **Issue** The SSB-SSB interaction potential is described as being derived from a previously published protocol, but the specific parameters and their validation are not described in detail. Given that the trombone loop model relies on these interactions, more detail would be helpful.
- **Required correction** Provide a more detailed description of the SSB-SSB interaction potential, including the specific parameters used and any validation performed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion, "Limitations of the study"
- **Evidence pointer** Discussion, "Limitations of the study"
- **Issue** The limitations section is brief and does not fully address the potential impact of the neglected C-terminal tails on the multi-protein simulations. The authors argue that the tails would have negligible influence on DNA binding, but the tails are known to be involved in protein-protein interactions, which could be relevant for the SSB-SSB and trombone loop simulations.
- **Required correction** Expand the discussion of the potential impact of neglecting the C-terminal tails, particularly for the multi-protein simulations, and consider whether this limitation could affect the conclusions drawn from the trombone loop model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1-7
- **Evidence pointer** Figures 1-7
- **Issue** The figure legends are informative, but the actual figures are not available for review. It is difficult to assess the quality of the visualizations and the clarity of the data presentation without seeing the figures.
- **Required correction** Ensure that the figures are of high quality and clearly present the data. In particular, Figure 3D (comparison of simulated and experimental force-extension curves) and Figure 6D (exchange probability versus time) should be clearly legible and include appropriate error bars or confidence intervals.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility of data
- **Affected element** Data and code availability
- **Evidence pointer** Data and code availability
- **Issue** The authors state that all data will be shared upon request and that code is deposited on GitLab. However, the specific data files (e.g., simulation trajectories, analysis scripts) are not listed in the key resources table.
- **Required correction** Provide a more detailed list of the data and code files that are available, including the specific trajectories and analysis scripts used to generate the main results.

## Risk / unsupported claims
- The claim that the model provides "the first structurally correct physical model of a trombone loop" is not supported by direct validation against experimental data for the trombone loop structure.
- The claim that the model can be used to study the kinetics of SSB-ssDNA interactions is not quantitatively supported due to the acknowledged process-dependent acceleration of CG dynamics.
- The prediction that a single SSB protein can stably bind to both ends of the trombone loop is presented without experimental validation or comparison to known biochemical data.
- The statement that the model "recapitulates" experimental force-extension data is supported, but the quantitative agreement is not assessed with error analysis or statistical measures.
- The claim that the model could be used to "replace some experiments outright" is speculative and not supported by the current evidence, given the acknowledged limitations.