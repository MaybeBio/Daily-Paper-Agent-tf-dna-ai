## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report a concentration-dependent binding mode of the antihistaminic drug oxatomide (OXT) with calf-thymus DNA (CT-DNA) in physiological buffer (pH 7.4). At low drug-to-DNA molar ratios (0.6-0.1), OXT intercalates into base pairs; at high ratios (13-6), it binds in the minor groove. Binding constants are reported in the range 10^3-10^5 M^-1, with groove binding showing a slightly higher constant. Thermodynamic analysis at three temperatures indicates hydrophobic driving forces (ΔH° > 0, ΔS° > 0). Voltammetric data suggest adsorption-controlled electro-reduction and shifts in reduction potentials consistent with concentration-dependent binding. Metadynamics simulations reveal two binding forces, partial intercalation and minor groove binding, corroborating experimental results.
- **Visible evidence base** Abstract text only; no experimental data, spectra, voltammograms, simulation parameters, or statistical analyses are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental methods, simulation setup and convergence criteria, raw binding constants, thermodynamic parameters, and error estimates

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting study of concentration-dependent DNA binding by a drug molecule, combining multiple experimental techniques with all-atom metadynamics simulations. The central claim, that the binding mode switches from intercalation to minor groove binding as the drug-to-DNA ratio increases, is mechanistically intriguing and could be of interest to the biophysical chemistry and drug-DNA interaction communities. However, the abstract alone provides insufficient evidence to evaluate the rigor of the experimental design, the quality of the data, or the validity of the interpretation. Several claims, particularly the mode-switching behavior and the thermodynamic interpretation, require detailed supporting data that are not visible here. The simulation results are mentioned but not described in sufficient detail to assess their reliability. Overall, the study has potential merit, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in biophysical chemistry, drug-DNA interaction studies, and computational molecular modeling would be interested. The concentration-dependent binding mode is relevant to understanding how drug dosage may influence DNA binding mechanisms, which has implications for drug design and toxicity assessment. The combination of spectroscopic, electrochemical, and simulation approaches may appeal to methodologically oriented readers.
- **Major strengths** The study employs a multi-technique approach, which is commendable for cross-validating binding modes. The use of metadynamics simulations to complement experimental findings is a modern and potentially powerful addition. The focus on concentration-dependent behavior is a nuanced angle that goes beyond typical single-mode binding studies.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  - Originality: The concentration-dependent mode-switching concept is not entirely novel, as similar phenomena have been reported for other DNA-binding ligands, but the specific application to oxatomide may offer a new data point. The originality is moderate.  
  - Scientific importance: The findings could contribute to understanding drug-DNA interactions, but the significance is limited by the lack of demonstrated biological or therapeutic implications. The importance is modest.  
  - Interdisciplinary readership: The topic bridges chemistry, biophysics, and computational biology, which could attract a cross-disciplinary audience, but the abstract does not clearly articulate broader relevance beyond the specific system.  
  - Technical soundness: Cannot be assessed from the abstract alone. The absence of error estimates, control experiments, and simulation validation details prevents evaluation of technical rigor.  
  - Readability for nonspecialists: The abstract is reasonably clear but uses technical jargon (e.g., "metadynamics," "adsorption controlled process") without sufficient context for a general scientific audience. The structure is logical, but the density of techniques may overwhelm nonspecialists.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially valid study, but the lack of visible data and methodological details means the core claims cannot be verified. A revised submission with full experimental and computational details would be needed to assess whether the case can be supported.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The claim that OXT binds to CT-DNA in a concentration-dependent manner, with intercalation at low molar ratios (0.6-0.1) and minor groove binding at high ratios (13-6), is central to the study.  
- **Evidence pointer** Abstract text; no specific figures or tables referenced  
- **Concern** The abstract states the mode-switching behavior but provides no quantitative data, such as binding isotherms, spectral titration curves, or representative spectra, to support the assignment of each binding mode at the specified ratios. The molar ratio ranges are oddly defined (0.6-0.1 and 13-6), and it is unclear why these ranges are discontinuous or how they were selected.  
- **Why it matters** The concentration-dependent mode switch is the primary novel claim. Without direct evidence, such as changes in absorption or fluorescence patterns, circular dichroism signatures, or viscosity trends that are diagnostic of intercalation versus groove binding, the claim is unsupported. The discontinuous ratio ranges also raise questions about the experimental design and whether intermediate ratios were examined.  
- **Resolution test** Provide titration data across a continuous range of drug-to-DNA ratios, with clear spectral or hydrodynamic markers for each binding mode. Show representative spectra or plots and statistical fits that justify the assignment of intercalation at low ratios and groove binding at high ratios.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Quantitative rigor  
- **Claim pointer** The binding constants are reported in the order of 10^3-10^5 M^-1, with groove binding exhibiting a slightly higher constant than intercalation.  
- **Evidence pointer** Abstract text; no data or methods provided  
- **Concern** The binding constants are given as a broad range without specific values, error margins, or the method used to calculate them (e.g., Benesi-Hildebrand, Scatchard, or other models). The claim that groove binding has a slightly higher constant is not quantified, and it is unclear whether the difference is statistically significant.  
- **Why it matters** Binding constants are a key quantitative output. Without precise values and uncertainties, the comparison between binding modes is not meaningful. The thermodynamic analysis (ΔH° > 0, ΔS° > 0) is also presented without the actual values or the temperature range, making it impossible to assess the reliability of the hydrophobic interaction claim.  
- **Resolution test** Report specific binding constants with standard deviations for each mode, the fitting model used, and the number of replicates. Provide van't Hoff plots or equivalent data showing ΔH° and ΔS° values with errors, and state the temperature range and number of temperatures used.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Simulation validity  
- **Claim pointer** The metadynamics simulations revealed two major binding forces, partial intercalation and minor groove binding, which corroborate the experimental results.  
- **Evidence pointer** Abstract text; no simulation details provided  
- **Concern** The abstract mentions all-atom metadynamics simulations but provides no information on the simulation protocol, such as the force field, water model, simulation time, collective variables used, or convergence criteria. The free energy landscape is mentioned but not shown or described quantitatively.  
- **Why it matters** Metadynamics results are only meaningful if the simulations are well-converged and the collective variables are appropriately chosen. Without these details, the claim of corroboration is unverifiable. The abstract also does not specify whether the simulations were performed at concentrations corresponding to the experimental ratios, which is critical for the concentration-dependent claim.  
- **Resolution test** Describe the simulation setup in detail, including software, force field, system size, simulation length, collective variables, and convergence checks. Show the free energy landscape and indicate the minima corresponding to partial intercalation and minor groove binding, with error estimates if possible.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological integration  
- **Claim pointer** The voltammetric investigations indicate that the electro-reduction of OXT is an adsorption-controlled process and that shifts in reduction peak potentials reiterate the concentration-dependent binding mode.  
- **Evidence pointer** Abstract text; no voltammetric data provided  
- **Concern** The abstract states that voltammetric shifts support the concentration-dependent binding, but no specific peak potentials, scan rate studies, or concentration-dependent voltammograms are shown. The link between adsorption-controlled electro-reduction and the binding mode is not explained mechanistically.  
- **Why it matters** Voltammetry is used as a corroborating technique, but the abstract does not demonstrate how the electrochemical data independently support the mode switch. Without data, the claim is merely an assertion. The connection between adsorption control and DNA binding mode is not obvious and requires explanation.  
- **Resolution test** Provide voltammograms at multiple drug-to-DNA ratios, with peak potential shifts and current changes quantified. Show scan rate dependence to support the adsorption-controlled mechanism and explain how these observations are consistent with intercalation versus groove binding.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Molar ratio ranges  
- **Evidence pointer** Abstract text  
- **Issue** The molar ratio ranges (0.6-0.1 and 13-6) are presented in descending order, which is unconventional and confusing. It is unclear whether these are drug-to-DNA or DNA-to-drug ratios.  
- **Required correction** Define the ratio explicitly (e.g., [OXT]/[CT-DNA]) and present the ranges in ascending order for clarity.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Thermodynamic analysis  
- **Evidence pointer** Abstract text  
- **Issue** The thermodynamic parameters are mentioned only qualitatively (ΔH° > 0, ΔS° > 0). The abstract does not state the number of temperatures used or the range, which is important for assessing the reliability of the van't Hoff analysis.  
- **Required correction** Specify the temperature range and the number of temperatures at which binding constants were measured.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "Partial intercalation"  
- **Evidence pointer** Abstract text  
- **Issue** The term "partial intercalation" is used in the simulation results but is not defined or distinguished from full intercalation in the experimental context. This could cause confusion about whether the experimental low-ratio mode is full or partial intercalation.  
- **Required correction** Clarify whether the experimental intercalation mode is full or partial and define "partial intercalation" in the context of the simulations.

## Risk / unsupported claims
- The concentration-dependent mode switch from intercalation to minor groove binding is unsupported without titration data across a continuous ratio range.
- The binding constant values and their comparison between modes are unverifiable without specific numbers and errors.
- The thermodynamic claim of hydrophobic driving forces is unsupported without actual ΔH° and ΔS° values.
- The voltammetric claim of adsorption-controlled electro-reduction and its link to binding mode is unsupported without data.
- The metadynamics simulation results are unverifiable without protocol details and convergence evidence.
- The claim of corroboration between simulations and experiments is not assessable from the abstract alone.