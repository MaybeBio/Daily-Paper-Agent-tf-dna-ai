## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results and discussion, conclusions, and supplementary figure/table references
- **Assessment boundary** Scientific claims, methodological soundness, data interpretation, and conclusions as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors measure DNA twist at high alkaline ion concentrations (up to 8 M) using magnetic tweezers, observe a plateau in twist above 4-5 M, and use all-atom MD simulations to show that C-form DNA is not stable in solution, concluding that DNA remains in B-form even at very high salt concentrations
- **Visible evidence base** Magnetic tweezers rotation-extension curves, CD spectroscopy data, all-atom MD simulations with multiple force fields, Kirkwood-Buff activity analysis, supplementary figures and tables referenced but not fully visible
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S18), detailed numerical data for twist values, complete CD spectra, simulation convergence data, force field parameter details, and the Zenodo repository contents

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question in nucleic acid biophysics: whether DNA transitions to C-form at high salt concentrations. The combination of single-molecule experiments and MD simulations is appropriate and powerful. The experimental data appear carefully collected, and the conclusion that C-form DNA is not supported in solution is well argued. However, several technical concerns regarding data analysis, simulation methodology, and interpretation of CD spectra need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers in nucleic acid biophysics, DNA-ion interactions, single-molecule biophysics, and computational chemistry. The results are also relevant to those studying extremophiles and prebiotic chemistry, as well as developers of nucleic acid force fields who need experimental benchmarks at extreme ionic conditions.

- **Major strengths** The study extends twist measurements to much higher salt concentrations than previously explored, providing new data in an understudied regime. The combination of experimental and computational approaches is complementary and mutually reinforcing. The use of activity derivatives rather than concentrations to compare simulations and experiments is a thoughtful methodological advance. The manuscript is clearly written and the conclusions are appropriately cautious.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "twist initially increases approximately as ∼[salt]^1/2, but plateaus above 3 M" and that "the change in twist is well described by a square root dependence up to 2 M for all salts studied"
- **Evidence pointer** Figure 1G, Supplementary Figure S8, Table 1
- **Concern** The manuscript states that twist follows a square root dependence up to 2 M but does not provide the fitting procedure, error analysis, or statistical comparison between the square root model and alternative functional forms. The claim of a plateau above 3 M is based on visual inspection of Figure 1G, but no quantitative criterion for "plateau" is provided. Additionally, the transition from square root behavior to plateau is not characterized.
- **Why it matters** The functional form of the twist-salt concentration relationship is central to the manuscript's conclusions. Without rigorous fitting and model comparison, the reader cannot assess whether the proposed square root dependence is uniquely supported or whether other models (e.g., logarithmic, power law with different exponent) fit equally well. The plateau claim is critical for the argument against C-form DNA, so it must be quantitatively established.
- **Resolution test** Provide the full fitting procedure, including the functional form, fitting range, and parameter uncertainties. Perform model comparison (e.g., AIC or BIC) between the square root model and alternative models. Define a quantitative criterion for plateau (e.g., slope below a threshold) and apply it consistently across all salts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "simulations initiated in the C-form rapidly convert to B-form, while the B-form remains stable" and that "C-form DNA is not stable in the simulations for different force fields, even at LiCl concentrations up to 7.8 M"
- **Evidence pointer** Figure 4A-C, Supplementary Figures S14-S15
- **Concern** The manuscript does not provide sufficient detail on the simulation protocol for the C-form to B-form conversion. Key missing information includes: the timescale of conversion, the criteria used to define "conversion" (e.g., RMSD thresholds, twist values), the number of independent simulations performed, and whether the conversion was observed consistently across all force fields. The statement that "the twist decreases rapidly to the lower values characteristic of B-form DNA" is vague without quantitative convergence data. Additionally, the manuscript does not report whether the simulations reached equilibrium and how the final twist values compare to experimental values.
- **Why it matters** The instability of C-form in simulations is a key piece of evidence against C-form DNA in solution. If the conversion is not rigorously characterized, the reader cannot assess whether the simulations truly sample equilibrium behavior or whether the conversion is an artifact of the simulation protocol (e.g., insufficient sampling, force field artifacts, or starting structure preparation).
- **Resolution test** Provide detailed convergence analysis, including time series of twist and RMSD for both B- and C-form starting structures, the number of independent replicates, and the criteria for defining conversion. Report the equilibrium twist values and their uncertainties for each force field and compare them quantitatively to experimental values.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "comparing simulations and experiments using activity derivatives rather than concentrations significantly improves the agreement, capturing both the nonlinear twist increase and its saturation"
- **Evidence pointer** Figure 5A-B, Supplementary Figures S16-S17
- **Concern** The manuscript does not provide a quantitative measure of the improvement when using activity derivatives instead of concentrations. The claim of "significant improvement" is based on visual comparison of Figure 5A and 5B, but no statistical metric (e.g., RMSD between simulation and experiment, correlation coefficient) is provided. Additionally, the method for computing activity derivatives from simulations via Kirkwood-Buff theory is not described in sufficient detail, and the uncertainty in the computed activity derivatives is not reported.
- **Why it matters** The activity derivative comparison is presented as a methodological advance that reconciles simulation and experiment. Without quantitative assessment, the reader cannot determine whether the improvement is statistically meaningful or within the uncertainty of the calculations. The Kirkwood-Buff analysis requires careful treatment of finite-size effects and convergence, which are not discussed.
- **Resolution test** Provide quantitative metrics for the agreement between simulation and experiment for both concentration-based and activity-based comparisons. Report the uncertainty in the computed activity derivatives and discuss finite-size effects and convergence of the Kirkwood-Buff integrals.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "the fact that Δε at 280 nm undergoes further changes at salt concentrations where the twist has plateaued and remains constant implies that CD does not directly report on DNA helical twist"
- **Evidence pointer** Figure 2B-C, Supplementary Figure S13
- **Concern** The manuscript does not provide a mechanistic explanation for why CD at 280 nm continues to change while twist plateaus. The authors speculate that "continued changes in the ion binding pattern including the increasing number of Li+ ions bound to the nucleobases" may be responsible, but this is not tested or supported by additional data. The claim that "CD does not directly report on DNA helical twist" is potentially important but requires more rigorous support.
- **Why it matters** This claim challenges the interpretation of previous CD studies that attributed changes at 280 nm to C-form DNA. If the authors are making this argument, they need to provide a more detailed analysis of what structural features contribute to the CD signal at 280 nm and why these features continue to change after twist plateaus.
- **Resolution test** Provide additional analysis of the CD spectra, such as decomposition into contributions from different structural features, or perform additional experiments (e.g., CD measurements at different temperatures or with different DNA sequences) to test the proposed mechanism. Alternatively, use MD simulations to compute CD spectra and compare to experimental data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the change in twist correlates strongly with the number of specifically adsorbed Li+ ions" and that "high-affinity Li+ binding is limited by electrostatic repulsion between the cations, which in turn defines an upper bound for DNA twist"
- **Evidence pointer** Figure 6D-G, Supplementary Figure S18
- **Concern** The correlation analysis between twist and Li+ adsorption is not described in detail. The manuscript does not report the correlation coefficients, the statistical significance, or whether the correlation is independent of other variables (e.g., ionic strength, water activity). The proposed mechanism of electrostatic repulsion limiting Li+ binding is plausible but is not directly tested.
- **Why it matters** The mechanistic model presented in Figure 6 is a key contribution of the manuscript. Without rigorous correlation analysis and testing of alternative mechanisms, the model remains speculative.
- **Resolution test** Provide quantitative correlation analysis between twist and Li+ adsorption, including correlation coefficients and significance tests. Test alternative mechanisms (e.g., changes in water activity, ion dehydration) and discuss whether the data can distinguish between them.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, line "twist initially increases approximately as ∼[salt]^1/2"
- **Issue** The notation "∼[salt]^1/2" is ambiguous. It is unclear whether this means the square root of the salt concentration or the square root of the salt activity.
- **Required correction** Clarify the notation, e.g., "twist increases approximately as the square root of the salt concentration" or specify whether activity is used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** Results section, "Changes of the slope in the plectonemic regime"
- **Issue** The discussion of slope changes in the plectonemic regime is brief and does not clearly state whether these changes are statistically significant or what their physical origin might be.
- **Required correction** Provide statistical analysis of the slope changes and discuss possible physical origins (e.g., changes in bending stiffness, helix geometry).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Methods section, "Molecular dynamics simulations"
- **Issue** The manuscript states that "the reported volumes include the volume of the DNA, which is 2% of the total simulation volume" but does not explain how the DNA volume was calculated or why this correction is necessary.
- **Required correction** Provide details on how the DNA volume was estimated and justify the correction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section
- **Evidence pointer** Results section, "Circular dichroism spectra"
- **Issue** The CD measurements are described as being in agreement with previous work, but the manuscript does not provide a quantitative comparison (e.g., difference spectra, correlation coefficients).
- **Required correction** Provide a quantitative comparison with previous CD data, such as overlaying spectra or reporting correlation coefficients.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusions
- **Evidence pointer** Conclusions, "the ion binding pattern including the increasing number of Li+ ions bound to the nucleobases"
- **Issue** The statement about Li+ binding to nucleobases is not supported by data presented in the manuscript. It is unclear whether this is from the simulations or from literature.
- **Required correction** Clarify the source of this statement and provide supporting data or references.

- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative fitting of twist-salt relationship), R1-M2 (rigorous characterization of C-form to B-form conversion in simulations), R1-M3 (quantitative assessment of activity-based comparison)

- **Assessment against Nature-style criteria** 
  - Originality: The manuscript addresses a long-standing question about C-form DNA in solution with a combination of techniques not previously applied to this problem. The extension of twist measurements to very high salt concentrations is novel.
  - Scientific importance: The results have implications for understanding DNA behavior in extreme ionic conditions, relevant to extremophiles and prebiotic chemistry. The work also provides a benchmark for force field validation.
  - Interdisciplinary readership: The topic bridges biophysics, physical chemistry, and computational biology. The findings would interest researchers in these fields, though the technical nature may limit broader appeal.
  - Technical soundness: The experimental approach is sound, but the quantitative analysis needs strengthening (see Major Concerns). The simulation methodology is appropriate but requires more detailed convergence analysis.
  - Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections (e.g., Kirkwood-Buff analysis) may be challenging for non-experts.

- **Recommendation posture** Supportive if technical concerns are resolved. The core conclusion that C-form DNA is not supported in solution is likely correct, but the quantitative analysis needs strengthening to fully establish the case.

## Risk / unsupported claims
- The claim that "the change in twist is well described by a square root dependence up to 2 M" is not quantitatively supported without fitting details and model comparison
- The claim that "C-form DNA is not stable in the simulations" requires more rigorous convergence analysis and quantitative criteria for stability
- The claim that "comparing simulations and experiments using activity derivatives rather than concentrations significantly improves the agreement" lacks quantitative metrics
- The statement that "high-affinity Li+ binding is limited by electrostatic repulsion between the cations" is presented as a conclusion but is not directly tested
- The claim that "CD does not directly report on DNA helical twist" is based on indirect evidence and requires additional support
- The statement about "continued changes in the ion binding pattern including the increasing number of Li+ ions bound to the nucleobases" is not supported by data presented in the manuscript