## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supporting information references)
- **Assessment boundary** Scientific content, methodological rigor, claims versus evidence, and presentation quality as presented in the provided text
- **Shared manuscript claim summary** The authors benchmark six residue-resolution coarse-grained models (HPS, HPS-cation–π, HPS-Urry, CALVADOS2, Mpipi, Mpipi-Recharged) against experimental data for phase behaviour and viscosity of seven A1-LCD variants, concluding that Mpipi, Mpipi-Recharged, and CALVADOS2 perform best, with Mpipi-Recharged most accurate overall.
- **Visible evidence base** Main text figures (Figs 1–8), supplementary figures (S1–S4), tables (Table 1, S1 Table), methods section, and referenced experimental data from Refs [77, 78]
- **Missing materials affecting confidence** Full figure data (numerical values, error bars), simulation convergence criteria, force field parameter tables, experimental fitting procedures, and details of the Green-Kubo integration cutoffs are not fully provided in the text

## Reviewer
- **Overall assessment** This manuscript presents a systematic and timely benchmark of six residue-resolution coarse-grained models for simulating biomolecular condensates, using a well-chosen protein system (A1-LCD and variants) with available experimental data. The study is carefully designed, and the conclusions are largely supported by the presented comparisons. The work will be of interest to the biomolecular simulation and phase separation communities. However, several technical aspects require clarification and strengthening before the case is fully established, particularly regarding simulation convergence, error estimation, and the interpretation of viscosity predictions.

- **Who would be interested in the results, and why** Researchers in computational biophysics, specifically those developing or using coarse-grained models for intrinsically disordered proteins and phase-separating systems. The benchmark provides practical guidance on model selection for condensate simulations, which is directly relevant to the growing community studying biomolecular condensates in health and disease. Experimentalists studying phase separation may also find the model assessment useful for interpreting their data.

- **Major strengths**
  - Systematic comparison of six models on the same protein system with consistent simulation protocols
  - Direct benchmarking against experimental phase behaviour and viscosity data
  - Clear identification of model strengths and weaknesses, with actionable conclusions
  - Inclusion of contact map analysis to provide mechanistic insight into model differences
  - Open sharing of simulation scripts and data via GitHub

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the Mpipi-Recharged model provides the most accurate predictions of condensate viscosity among the tested models (Section 2.3, Fig 6).
- **Evidence pointer** Section 2.3, Fig 6D–6F, Section 4.5
- **Concern** The viscosity values are compared only in a normalised form (relative to WT+NLS), and the absolute deviations from experimental values are not reported. The normalisation procedure may mask systematic errors in absolute viscosity prediction. Furthermore, the Green-Kubo integration method relies on fitting G(t) to Maxwell modes at long times, and the choice of fitting range and number of modes can significantly affect the final viscosity value. The manuscript does not provide details on the sensitivity of the results to these fitting parameters, nor does it report statistical uncertainties (e.g., standard errors) for the viscosity estimates.
- **Why it matters** Viscosity is a key material property of condensates, and the claim that Mpipi-Recharged is most accurate hinges on the reliability of the viscosity calculation. Without error bars and sensitivity analysis, the ranking of models could be affected by numerical artifacts rather than genuine model performance.
- **Resolution test** Provide absolute viscosity values with statistical uncertainties (e.g., block averaging or multiple independent runs). Perform a sensitivity analysis of the Maxwell mode fitting procedure (e.g., vary the number of modes, fitting range) and demonstrate that the model ranking is robust to these choices.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the HPS and HPS-cation–π models "failed to recapitulate the relative phase-separation propensity of the A1-LCD variants" (Section 2.3) and that HPS and HPS-Urry "do not phase-separate at 298 K" (Section 2.3).
- **Evidence pointer** Section 2.3, Fig 4A–4B, Fig 2B–2D
- **Concern** The criteria for "failing" are not explicitly defined. For HPS and HPS-cation–π, the correlation between predicted Tc and experimental Csat is low, but the absolute Tc values are not compared to experimental critical temperatures. For HPS and HPS-Urry, the statement that they do not phase separate at 298 K is made without showing the full phase diagrams or the temperature range over which they do phase separate. It is unclear whether these models would phase separate at lower temperatures, and whether the failure at 298 K is a quantitative or qualitative issue.
- **Why it matters** The exclusion of HPS and HPS-Urry from the viscosity analysis is justified by these claims. If the criteria for failure are not transparent, the reader cannot assess whether the exclusion is warranted or whether these models might still be useful for other conditions or observables.
- **Resolution test** Define explicit quantitative criteria for "failing" (e.g., correlation coefficient threshold, deviation from experimental Tc). Show the full phase diagrams for HPS and HPS-Urry, including the temperature range where phase separation occurs, and discuss whether the failure at 298 K is a fundamental limitation or a temperature-dependent issue.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that "models considering both cation–π and π–π interactions as primary contributors to the stability of A1-LCD condensates align most closely with experimental observations" (Section 2.4).
- **Evidence pointer** Section 2.4, Fig 8, S3 Fig, S4 Fig
- **Concern** The contact map analysis is performed at 0.95 Tc for each model, which means the comparison is made at different absolute temperatures for different models. This could bias the contact analysis, as the relative importance of different interaction types may be temperature-dependent. Additionally, the contact maps are only shown for the WT+NLS sequence (S3 Fig) and for the Mpipi-Recharged model across variants (Fig 8); a systematic comparison of contact maps across all models and all variants is not presented.
- **Why it matters** The mechanistic conclusion about which interaction types are most important relies on the contact map analysis. If the comparison is not performed under equivalent thermodynamic conditions, the conclusions may not be robust.
- **Resolution test** Perform the contact map analysis at the same absolute temperature (e.g., 298 K) for all models, or justify why 0.95 Tc is the appropriate comparison point. Present contact maps for all models and all variants, or at least for a representative subset that supports the general conclusions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section 2.1, Fig 1
- **Evidence pointer** Fig 1A
- **Issue** The description of the Direct Coexistence method in the main text is brief, and the reader is referred to Section 4.3 for details. A schematic of the simulation setup (Fig 1A) is helpful, but the caption could more clearly explain what is shown in the top and bottom panels.
- **Required correction** Expand the Fig 1A caption to explicitly state that the top panel shows a two-phase coexistence below Tc and the bottom panel shows a single phase above Tc, and briefly define the density profile.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.1, Table 1
- **Evidence pointer** Table 1
- **Issue** Table 1 summarises the potentials used by each model, but the specific parameter values (e.g., λi values, εij values) are not provided in the main text or table. The reader is referred to the original model papers, but a summary of key parameters would improve the self-containedness of the manuscript.
- **Required correction** Add a supplementary table listing the key parameters for each model, or at least provide the parameter values for the interaction strengths of the aromatic residues (F, Y, W) that are central to the study.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Section 2.2, Fig 5
- **Evidence pointer** Fig 5
- **Issue** The definition of the deviation metric D (Eq 18) is given in Section 4.6, but the interpretation of D values (e.g., what constitutes a "good" or "poor" agreement) is not discussed in the main text.
- **Required correction** Briefly state in Section 2.2 what range of D values would be considered acceptable, or compare the D values obtained here to those from previous benchmark studies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section 2.3, Fig 6
- **Evidence pointer** Fig 6B
- **Issue** The shear stress relaxation function G(t) is shown for the WT+NLS sequence, but the differences between models at short timescales are described as "rather similar" without quantitative support.
- **Required correction** Provide a quantitative measure of similarity (e.g., root mean square deviation between G(t) curves at short times) or state that the differences are within statistical uncertainty.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.2
- **Evidence pointer** Section 4.2
- **Issue** The simulation time for viscosity calculations is stated as "around 3–5 μs", but the equilibration time is not specified. The equilibration protocol (e.g., how the system was compressed to the desired density) is also not described.
- **Required correction** Specify the equilibration time and protocol, and state how the system density was set for the viscosity simulations.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of statistical uncertainties and sensitivity analysis for viscosity predictions
  - R1-M2: Unclear criteria for model failure and exclusion from viscosity analysis
  - R1-M3: Contact map comparison at different absolute temperatures across models

- **Assessment against Nature-style criteria**
  - **Originality** The manuscript is not the first to benchmark coarse-grained models for phase separation, but the systematic comparison of six models on the same protein system with multiple experimental observables (phase behaviour, viscosity, contact maps) is a valuable and relatively unique contribution. The focus on viscosity as a benchmark observable is particularly noteworthy.
  - **Scientific importance** The results provide practical guidance for model selection in condensate simulations, which is of direct relevance to a growing community. The identification of Mpipi-Recharged as the most accurate model for this system is a useful finding. However, the generalizability of the conclusions to other protein systems remains to be established.
  - **Interdisciplinary readership** The topic is of interest to computational biophysicists, soft matter physicists, and cell biologists studying phase separation. The manuscript is generally accessible, though some sections (e.g., the potential energy functions) may be challenging for non-specialists.
  - **Technical soundness** The simulation methodology is largely sound, but the lack of error bars on viscosity predictions and the unclear criteria for model failure are significant gaps. The contact map analysis at different temperatures is a potential confound.
  - **Readability for nonspecialists** The manuscript is well-structured and the figures are informative. However, the methods section is dense, and some terms (e.g., "rectilinear diameters", "Maxwell modes") are not explained for a general audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant question and provides a useful benchmark, but the viscosity analysis needs statistical rigor, and the criteria for model exclusion need to be clarified. The contact map analysis should be performed under equivalent thermodynamic conditions or the choice of 0.95 Tc should be justified.

## Risk / unsupported claims
- The claim that Mpipi-Recharged is the "most reliable" model for viscosity prediction is not fully supported without statistical uncertainties and sensitivity analysis.
- The statement that HPS and HPS-Urry "do not phase separate at 298 K" is made without showing the full phase diagrams or the temperature range of phase separation for these models.
- The conclusion that models ranking cation–π interactions as stronger than π–π interactions perform best is based on contact maps at 0.95 Tc, which may not be directly comparable across models.
- The generalizability of the benchmark conclusions to other protein systems beyond A1-LCD is not established and should be stated as a limitation.