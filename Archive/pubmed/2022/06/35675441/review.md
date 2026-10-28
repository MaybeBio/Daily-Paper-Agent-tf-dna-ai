## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive validity based solely on the provided text
- **Shared manuscript claim summary** The authors use extensive molecular dynamics simulations (up to 50 μs) and free energy computations to establish the molecular and energetic basis for the broad allostery hotspot distribution in the tetracycline repressor (TetR), proposing a conformational selection model and a thermodynamic framework that rationalizes distinct mechanistic contributions of hotspot residues.
- **Visible evidence base** Text descriptions of methods and results; no figures, tables, or supplementary data provided
- **Missing materials affecting confidence** All figures (Figs. 1–9), tables (Table 1, Table S1), and supplementary figures (Figs. S1–S23) are referenced but not provided; simulation parameters, force field validation details, and convergence criteria are only partially described

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive computational study aimed at explaining the broad distribution of allostery hotspots in TetR observed via deep mutational scanning. The authors employ extensive MD simulations across three ligation states, construct free energy landscapes, and integrate multiple analytical approaches to characterize residue-level contributions. The work is ambitious and addresses a significant question in allostery research. However, the absence of figures and quantitative data in the provided material severely limits the ability to evaluate the validity of the central claims. The conceptual framework, particularly the distinction between pathway-based and ensemble-based views of allostery, is thoughtful and potentially impactful. The thermodynamic model is presented at a qualitative level, which is appropriate given the scope, but the connection between simulation observables and model parameters requires clearer articulation. The manuscript would benefit from more explicit treatment of simulation convergence and statistical uncertainty, which are critical for the quantitative claims made.

- **Who would be interested in the results, and why** Researchers in computational biophysics, protein allostery, and protein engineering would find this work relevant. The study addresses a fundamental question about the molecular basis of allostery and provides a framework for interpreting deep mutational scanning data. The methodological approach, combining long-timescale simulations with multiple analysis techniques, will interest practitioners in the MD simulation community. The thermodynamic model and its implications for engineering allosteric proteins are relevant to synthetic biologists and protein designers. The work also speaks to the broader question of how to reconcile different conceptual frameworks for understanding allostery, which is of interest to the general biophysics community.

- **Major strengths** The study addresses a significant and timely question, namely the molecular basis for broad allostery hotspot distributions revealed by deep mutational scanning. The use of extensive simulations (up to 50 μs) represents a substantial computational investment that goes beyond typical practice. The multi-faceted analytical approach, integrating free energy landscapes, contact probabilities, dihedral angle analyses, and dynamical network analysis, is comprehensive and appropriate for the complexity of the problem. The development of a thermodynamic model that reconciles different mechanistic views of allostery is conceptually valuable and provides a framework for future studies. The authors are appropriately cautious in presenting the model at a qualitative level.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that computed free energy landscapes "clearly illustrate that allostery in TetR is well described by a conformational selection model" and that the apo state "samples a broad set of conformations, and specific ones are selectively stabilized by either ligand or DNA binding."
- **Evidence pointer** Results section, Fig. 4, Fig. S8, Fig. S10a
- **Concern** The central claim of conformational selection rests on the free energy landscapes shown in Fig. 4 and related supplementary figures, none of which are available in the provided material. The text describes the landscapes qualitatively but provides no quantitative measures such as free energy differences between basins, statistical uncertainties, or convergence assessments. Without these data, it is impossible to evaluate whether the simulations have adequately sampled the relevant conformational space, particularly for the highly flexible apo state. The claim that the apo state "samples a broad set of conformations" requires demonstration that the observed breadth is not an artifact of insufficient sampling or simulation artifacts.
- **Why it matters** The conformational selection mechanism is the foundational claim of the paper. If the free energy landscapes are not demonstrably converged or if the basin separations are within statistical noise, the entire interpretive framework is compromised. The distinction between conformational selection and induced fit has important implications for understanding allostery and for the thermodynamic model developed later.
- **Resolution test** Provide the free energy landscapes with error bars or bootstrap estimates, demonstrate convergence through block analysis or split-half comparisons, and report quantitative free energy differences between basins with associated uncertainties. Show that the apo state sampling is reproducible across independent trajectories.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support
- **Claim pointer** The authors state that "various analyses capture different subsets of experimentally identified hotspots" and that this supports the notion that residues modulate allostery in distinct ways.
- **Evidence pointer** Results section, Table 1, Fig. S22
- **Concern** The claim that different analyses capture different hotspot subsets is central to the paper's thesis, but Table 1 and Fig. S22 are not provided. The text does not report quantitative overlap statistics, enrichment factors, or statistical significance of the overlaps between computational predictions and experimental hotspots. Without these numbers, the claim of "different subsets" could reflect random chance rather than meaningful mechanistic distinctions. The authors mention that "less than ten" of 48 hotspots were not identified by any metric, but the distribution of overlaps across metrics is not quantified.
- **Why it matters** The paper's contribution to understanding hotspot diversity depends on demonstrating that different analytical approaches genuinely capture distinct mechanistic classes of residues. If the overlaps are not statistically significant, the conclusion that residues contribute via different mechanisms is not supported.
- **Resolution test** Provide a contingency table of hotspot identification across all analytical methods, compute enrichment statistics (e.g., hypergeometric tests) for overlaps between computational predictions and experimental hotspots, and report sensitivity and specificity for each method.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Model validation
- **Claim pointer** The authors develop a thermodynamic model with parameters ϵL, ϵD, and γ that "qualitatively explains the broad distribution of hotspot residues and their distinct features from molecular dynamics simulations."
- **Evidence pointer** Discussion section, Fig. 9, Fig. S23
- **Concern** The thermodynamic model is presented as a key outcome, but the connection between simulation results and model parameters is not quantitatively established. The text states that the model is "qualitative," which is appropriate, but it does not explain how the parameters would be estimated from simulation or experimental data, nor does it provide any fitting or validation against the deep mutational scanning results. The claim that the model "explains" the broad distribution requires at least a demonstration that reasonable parameter values can reproduce the observed hotspot patterns.
- **Why it matters** The model is presented as a framework for understanding hotspot distributions, but without any quantitative connection to data, it remains a conceptual proposal rather than a validated model. The paper's contribution to future engineering efforts depends on the model's ability to make testable predictions.
- **Resolution test** Provide a proof-of-concept demonstration that the model can reproduce qualitative features of the experimental hotspot distribution with reasonable parameter values, or outline a clear procedure for parameter estimation from future simulations or experiments.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor
- **Claim pointer** The authors use the CHARMM36m force field for protein simulations and the CHARMM General Force Field (CGENFF) for the ligand anhydrotetracycline (aTC), with Mg2+ treated using the standard CHARMM force field model.
- **Evidence pointer** Computational Methods section
- **Concern** The manuscript does not report validation of the ligand force field parameters against experimental data or quantum mechanical calculations. The conversion from minocycline in the crystal structure to aTC in the simulations is described but the structural basis for this conversion and its potential impact on the results is not discussed. The protonation state of the ligand and the treatment of Mg2+ coordination are critical for accurate simulation of the binding site, but no validation is presented.
- **Why it matters** The accuracy of the free energy landscapes and the derived mechanistic conclusions depends critically on the quality of the force field parameters, particularly for the ligand and metal ion. Inaccuracies in ligand parameters could lead to incorrect binding site conformations and erroneous conclusions about allostery.
- **Resolution test** Provide validation of ligand parameters against experimental data or high-level quantum mechanical calculations, and discuss the sensitivity of key results to the choice of ligand protonation state and Mg2+ coordination model.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors describe simulations conducted on local GPUs and on Anton 2, with total simulation times of 6 μs for ligand-bound and DNA-bound states and 53 μs for the apo state.
- **Evidence pointer** Computational Methods section
- **Concern** The manuscript does not report the number of independent simulations, the length of individual trajectories, or the criteria used to determine that the simulations were sufficiently converged for the analyses performed. The description of "3 independent trajectories of 15–20 μs each" for the apo state provides some information, but the convergence of the free energy landscapes and the statistical uncertainties of the reported quantities are not addressed.
- **Why it matters** The reliability of the conclusions depends on adequate sampling. Without convergence assessments, it is unclear whether the observed differences between ligation states reflect genuine physical differences or insufficient sampling.
- **Resolution test** Report the number and length of individual trajectories, provide convergence plots for key observables, and include statistical uncertainties for all reported quantities.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the study establishes "the molecular and energetic basis for the strong anti-cooperativity" but does not summarize the key quantitative findings or the specific contributions of the thermodynamic model.
- **Required correction** Include a brief summary of the main quantitative results, such as the free energy differences between states or the fraction of hotspots captured by the analyses.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Computational Methods
- **Evidence pointer** Computational Methods section
- **Issue** The description of the SAXS profile calculation mentions the FoXS method and MES reweighting but does not specify which experimental SAXS data were used for comparison or how the agreement was quantified.
- **Required correction** Provide details of the experimental SAXS data used and report quantitative measures of agreement between computed and experimental profiles.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The statement that "the two views are not in conflict" regarding pathway-based and ensemble-based models of allostery is presented as a conclusion, but the manuscript does not explicitly discuss how the results resolve potential tensions between these frameworks beyond the proposed model.
- **Required correction** Expand the discussion to address how the results specifically reconcile these perspectives and what evidence supports this reconciliation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction assumes familiarity with the TetR system and its allosteric mechanism, which may limit accessibility for readers outside the immediate field.
- **Required correction** Provide a brief description of the TetR structure and function, including the locations of the ligand and DNA binding sites, to orient non-specialist readers.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Results section, Fig. 2
- **Issue** The text notes that distributions of structural parameters "feature a finite overlap" between ligand-bound and DNA-bound states, but does not report quantitative measures of the overlap or its statistical significance.
- **Required correction** Report quantitative measures of distribution overlap (e.g., Bhattacharyya coefficient) and assess whether the observed overlaps are consistent with the proposed conformational selection model.

## Risk / unsupported claims
- The claim that allostery in TetR is "well described by a conformational selection model" is not fully supported without the free energy landscape figures and quantitative basin analysis
- The claim that different analyses capture different subsets of hotspots requires the missing Table 1 and Fig. S22 to verify the overlap statistics
- The thermodynamic model's ability to "explain" the broad hotspot distribution is presented qualitatively without quantitative validation
- The statement that the apo state "samples a broad set of conformations" requires convergence assessment to rule out sampling artifacts
- The claim that polar interactions "help propagate changes due to ligand binding" is based on contact probability analysis, but the statistical significance of these changes is not reported
- The assertion that the study has implications for engineering allosteric proteins is speculative without experimental validation of the predictions