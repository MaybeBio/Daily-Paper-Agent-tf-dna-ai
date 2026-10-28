## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, experimental section, and supplementary figure references
- **Assessment boundary** Scientific claims, model validity, experimental validation, and consistency between modeling and experimental data as presented in the provided text
- **Shared manuscript claim summary** The authors present a computational model integrating plasma membrane curvature-dependent endocytosis, curvature-sensitive actin assembly, and stretch-induced nuclear pore complex opening to explain how nanoscale substrate topography regulates YAP/TAZ nuclear localization. The model predicts that nanotopography globally inhibits cytoskeletal assembly via integrin endocytosis while locally enhancing actin assembly, and that nuclear deformation and rupture on nanopillar substrates can enhance YAP/TAZ nuclear accumulation.
- **Visible evidence base** Model equations (1-10), simulation results described in Figures 1-4, experimental measurements of nuclear indentation and curvature (Figure 3), YAP/TAZ and Ku-80 immunostaining data (Figure 5), and statistical analyses as described in the text
- **Missing materials affecting confidence** Actual figure images, supplementary figures S1-S4, supplementary tables S1-S4, movies, detailed parameter values, experimental raw data, and full model equations in the supplementary information were not provided for direct verification

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question in mechanobiology: how nanoscale substrate curvature integrates multiple mechanical signals to regulate YAP/TAZ nuclear localization. The authors develop a sophisticated spatial computational model using their SMART software package and validate key predictions with experiments. The work is ambitious and the integration of multiple mechanotransduction pathways is commendable. However, several technical concerns regarding model parameterization, the treatment of nuclear rupture, and the strength of experimental validation need to be addressed before the conclusions are fully established.

- **Who would be interested in the results, and why** Researchers in mechanobiology, cellular biophysics, and nuclear mechanics would find this work of significant interest. The study addresses fundamental questions about how cells integrate mechanical cues across length scales, which is relevant to understanding tissue development, cancer metastasis, and cell migration through complex environments. The computational framework presented could also be valuable to the broader computational biology community studying spatial signaling models.

- **Major strengths** The manuscript addresses a significant gap in the field by providing a mechanistic computational framework that integrates multiple, sometimes opposing, mechanotransduction pathways. The use of realistic cell geometries informed by experimental measurements is a notable advance over previous well-mixed models. The combination of modeling with experimental validation, particularly the prediction and validation of nuclear rupture effects on YAP/TAZ localization, strengthens the overall conclusions. The authors are transparent about model assumptions and provide open access to code and data.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of model parameterization
- **Claim pointer** The model claims to recapitulate lower levels of global cytoskeletal assembly on nanopillar substrates and predict YAP/TAZ nuclear localization as a function of nanotopography.
- **Evidence pointer** Results section "Regulation of Enzyme Activation and Actin Polymerization by Plasma Membrane Curvature"; Equations (1-3); Table S4
- **Concern** The model introduces two free parameters, k_N-WASP and H_0, which are fit to experimental data. However, the manuscript does not provide sufficient detail on how these parameters were estimated, the sensitivity of model predictions to these parameters, or whether the fitted values are unique. The best-fit value for H_0 is justified by comparison to clathrin-mediated endocytosis data, but the relationship between this parameter and the actual physical process is not rigorously established. Furthermore, the model relies on previously estimated parameters from earlier work, but the propagation of uncertainty from those estimates into the current predictions is not addressed.
- **Why it matters** The central claim that the model can predict YAP/TAZ nuclear localization depends critically on the parameter values used. Without a rigorous parameter estimation and sensitivity analysis, it is unclear whether the model's predictions are robust or simply a consequence of parameter tuning. This affects the reliability of the model as a predictive tool for understanding mechanotransduction.
- **Resolution test** The authors should provide a detailed parameter estimation procedure, including the objective function used, the optimization algorithm, and the uncertainty in parameter estimates. A sensitivity analysis showing how model predictions vary with reasonable perturbations of the free parameters should be included. Ideally, the model should be validated against independent experimental data not used for parameter fitting.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation of nuclear rupture model
- **Claim pointer** The manuscript claims that nuclear rupture enhances YAP/TAX nuclear accumulation and validates this with experiments showing increased YAP N/C in cells with Ku-80 cytosolic mislocalization.
- **Evidence pointer** Results section "Nuclear Rupture Leads to High Levels of YAP/TAZ in Select Cells on Nanopillar Substrates"; Figure 5D-F
- **Concern** The experimental validation of the nuclear rupture model is based on correlative immunofluorescence data. The authors show that cells with Ku-80 cytosolic mislocalization (indicative of rupture) have higher YAP N/C, but the causal relationship is not directly tested. The model assumes a specific mechanism for how rupture enhances YAP/TAZ nuclear accumulation, but alternative explanations (e.g., rupture simply allows more YAP to enter before repair, or the correlation reflects a third factor) are not excluded. The manuscript does not report the frequency of rupture events, the timing of rupture relative to YAP accumulation, or whether the effect is specific to YAP/TAZ or applies to other nuclear proteins.
- **Why it matters** The nuclear rupture mechanism is a novel and potentially important contribution of this work. However, the current experimental evidence is correlative and does not definitively establish the proposed mechanism. Without stronger causal evidence, the claim that rupture enhances YAP/TAZ nuclear accumulation remains speculative.
- **Resolution test** The authors should provide additional experimental evidence supporting the causal role of nuclear rupture in YAP/TAZ accumulation. This could include time-lapse imaging showing YAP accumulation following rupture, experiments with manipulated rupture frequency (e.g., using different nanopillar geometries or pharmacological agents), or loss-of-function experiments targeting rupture repair machinery. Quantification of rupture frequency and the fraction of YAP accumulation attributable to rupture would strengthen the claim.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Model simplification of nuclear envelope mechanics
- **Claim pointer** The model treats nuclear deformation as a prescribed displacement field and calculates stretch ratios analytically, without considering the mechanical properties of the nuclear envelope or the forces required for deformation.
- **Evidence pointer** Results section "Nanopillar-Induced Nuclear Deformation Leads to Increases in the Stretch and Curvature of the Nuclear Envelope"; Section S5
- **Concern** The model prescribes the nuclear deformation field rather than computing it from mechanical principles. This means the model cannot predict the extent of nuclear deformation for a given nanopillar geometry, but rather requires this as an input. The relationship between nanopillar properties (height, spacing, stiffness) and the resulting nuclear deformation is not modeled mechanistically. This limits the predictive power of the model and its applicability to different experimental conditions.
- **Why it matters** A key claim of the paper is that the model can predict YAP/TAZ nuclear localization as a function of nanotopography. However, if the nuclear deformation must be prescribed, the model's predictive capacity is limited to the specific deformation states that are input. A more complete model would couple the mechanics of nuclear deformation to the nanopillar geometry and cellular forces.
- **Resolution test** The authors should either incorporate a mechanical model of nuclear deformation that predicts the deformation field from nanopillar geometry and cellular forces, or clearly state the limitations of the prescribed deformation approach. If the latter, the model should be tested against a range of deformation states to demonstrate its robustness.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The manuscript implies that the findings are general to cells on nanotopographic substrates, but the experimental validation is limited to a single cell type (U2OS) and a single nanopillar geometry.
- **Evidence pointer** Experimental Section "U2OS Cell Experiments"; Figure 3
- **Concern** The experimental validation of the model is performed exclusively with U2OS osteosarcoma cells on one specific nanopillar geometry. While the model is calibrated to data from a previous study using different nanopillar geometries, the direct experimental validation in this work uses only one condition. It is unclear whether the model predictions hold for other cell types, which may have different nuclear mechanics, cytoskeletal properties, or YAP/TAZ expression levels, or for other nanopillar geometries.
- **Why it matters** The conclusions about how nanotopography regulates YAP/TAZ nuclear localization are presented as general principles. However, without testing across multiple cell types and nanopillar geometries, the generalizability of these findings is uncertain. This is particularly important given that the balance between positive and negative regulation may differ depending on cell type and substrate geometry.
- **Resolution test** The authors should validate the model predictions in at least one additional cell type and with varying nanopillar geometries (e.g., different heights, spacings, or diameters). This would demonstrate that the model captures general principles rather than being specific to one experimental system.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of model description
- **Affected element** Model equations and parameter definitions
- **Evidence pointer** Results section "Model Summary"; Equations (1-10)
- **Issue** The model description is dense and some terms are not fully defined in the main text. For example, the relationship between the nuclear pore complex opening rate and the stretch ratio is described qualitatively but the functional form is not fully justified. The distinction between "activated" and "free" YAP/TAZ pools could be clarified.
- **Required correction** Provide a more detailed description of the model equations in the main text or refer readers to specific equations in the supplementary information. Define all variables and parameters at first use and provide a brief justification for the chosen functional forms.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis reporting
- **Affected element** Figure 5E-F statistical comparisons
- **Evidence pointer** Experimental Section "Statistical Analysis"
- **Issue** The statistical methods are described briefly. It is unclear how many cells were analyzed per condition, whether the data met assumptions for parametric testing, and how the threshold for Ku-80 cytosolic-to-nuclear ratio (0.16) was determined.
- **Required correction** Provide more detailed statistical reporting, including sample sizes, tests used, and justification for the Ku-80 ratio threshold. Consider showing individual data points alongside summary statistics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of model limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion does not adequately address the limitations of the model, particularly the prescribed nuclear deformation and the simplified treatment of nuclear rupture as a single pore with uniform permeability.
- **Required correction** Add a paragraph discussing model limitations and potential avenues for improvement, such as coupling to mechanical models of nuclear deformation or incorporating more detailed descriptions of rupture dynamics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility of experimental methods
- **Affected element** Nanopillar fabrication and cell experiments
- **Evidence pointer** Experimental Section "Nanopillar Substrate Fabrication and Preparation"
- **Issue** The nanopillar fabrication protocol is described but some parameters (e.g., gelatin concentration, coating time) are not specified. The cell seeding density and time points for analysis are not fully detailed.
- **Required correction** Provide complete details of all experimental protocols to ensure reproducibility, including concentrations, incubation times, and cell densities.

- **Technical failings that need to be addressed before the case is established** R1-M1 (parameter estimation and sensitivity), R1-M2 (causal evidence for rupture mechanism), R1-M3 (prescribed deformation limits predictive power)

- **Assessment against Nature-style criteria** 
  - Originality: The work is original in its integration of multiple mechanotransduction pathways into a spatial computational model of YAP/TAZ signaling. The focus on nuclear deformation and rupture as a mechanism for YAP/TAZ regulation is a novel contribution.
  - Scientific importance: The question of how cells integrate mechanical cues across length scales is of fundamental importance in mechanobiology. The findings have potential implications for understanding cancer cell behavior and tissue development.
  - Interdisciplinary readership: The work bridges cell biology, biophysics, and computational modeling, making it relevant to a broad interdisciplinary audience. However, the technical complexity of the model may limit accessibility to some readers.
  - Technical soundness: The computational framework is sophisticated and the use of realistic geometries is a strength. However, concerns about parameter estimation, model sensitivity, and the prescribed deformation field need to be addressed to fully establish technical soundness.
  - Readability for nonspecialists: The manuscript is generally well-written but the model description is dense. The main findings are clearly stated, but nonspecialists may struggle with the technical details of the model. The figures and experimental validation help to make the work accessible.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question with a sophisticated modeling approach and provides experimental validation for key predictions. However, the concerns about parameter estimation, the causal evidence for the rupture mechanism, and the limitations of the prescribed deformation approach need to be addressed before the conclusions are fully established. With appropriate revisions, this work could make a significant contribution to the field.

## Risk / unsupported claims
- The claim that nuclear rupture enhances YAP/TAZ nuclear accumulation is supported only by correlative immunofluorescence data; causal evidence is lacking.
- The model's prediction of YAP/TAZ nuclear localization as a function of nanotopography is dependent on fitted parameters whose uncertainty and sensitivity are not fully characterized.
- The generalizability of the findings to other cell types and nanopillar geometries is not established, as experimental validation is limited to U2OS cells on a single nanopillar geometry.
- The claim that the model is the "first to incorporate" these effects into a predictive computational model is difficult to verify without a comprehensive literature review.
- The relationship between the model's prescribed nuclear deformation and the actual mechanical forces involved is not addressed, limiting the physical interpretability of the results.