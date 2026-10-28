## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, conclusion, contributions, competing interests, funding, data availability, acknowledgements)
- **Assessment boundary** Scientific and technical evaluation of the claims, methodology, and evidence presented in the preprint. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors report a nanofluidic device combined with camera-based single-molecule FRET (smFRET) to study interactions between plant auxin response factor DNA-binding domains (ARF-DBDs) and labelled DNA oligonucleotides. They report two readouts for binding: changes in FRET efficiency and changes in diffusion coefficient. They also report that fluorescently labelled ARF-DBDs are monomeric at nanomolar concentrations, contrasting with dimeric crystal structures.
- **Visible evidence base** Abstract, introduction, materials and methods (device fabrication, protein expression, labelling, accessible volume simulations, single-molecule detection, FRET/ALEX analysis, particle displacement analysis, theoretical diffusion calculations), results (three sections), conclusion (two versions), author contributions, competing interests, funding, data availability, acknowledgements. Figures are referenced but not provided.
- **Missing materials affecting confidence** Figures (all), supplementary information, raw data, experimental protocols for protein expression and purification (referenced to prior work), detailed buffer compositions for single-molecule experiments, calibration data for diffusion measurements, control experiments (e.g., specificity of binding, photobleaching controls), statistical analysis details, and information on replicate numbers.

## Reviewer
- **Overall assessment** The manuscript presents a technically interesting application of nanofluidic devices for single-molecule fluorescence studies of protein-DNA interactions. The concept of combining FRET and diffusion measurements as orthogonal readouts is appealing and potentially useful. However, the evidence as presented is incomplete, with key figures missing, limited quantitative analysis, and several claims that are not fully supported by the described data. The claim regarding ARF-DBD monomeric state at nanomolar concentrations is particularly under-supported given the indirect nature of the diffusion-based inference and the lack of rigorous error analysis. The manuscript would benefit from a more detailed presentation of methods, controls, and statistical treatment.
- **Who would be interested in the results, and why** Researchers in single-molecule biophysics, microfluidics/nanofluidics, and plant transcription factor biology. The methodological advance of combining smFRET with diffusion measurements in nanochannels could interest biophysicists developing high-throughput assays. Plant biologists studying auxin signalling and ARF function may be interested in the oligomerization state of ARF-DBDs in solution.
- **Major strengths** 1. The combination of two independent readouts (FRET efficiency and diffusion coefficient) for detecting protein-DNA interactions is a conceptually strong approach. 2. The use of parallel nanofluidic channels with stroboscopic illumination addresses real technical challenges in camera-based single-molecule detection. 3. The comparison of experimental diffusion coefficients with theoretical predictions from crystal structures provides a quantitative framework. 4. The work addresses a biologically relevant question about ARF-DBD oligomerization state in solution.
- **Major Concerns** 
  - R1-M1: The claim that ARF-DBDs are monomeric at nanomolar concentrations is not sufficiently supported by the evidence presented.
  - R1-M2: The accuracy and precision of diffusion coefficient measurements in nanochannels are not adequately characterized.
  - R1-M3: The FRET-based binding detection lacks quantitative analysis and control experiments.
  - R1-M4: The titration experiment is described as having poor data quality, yet is used to support feasibility claims.
  - R1-M5: The theoretical diffusion coefficient calculations may not account for the nanochannel environment.
- **Minor Comments** 
  - R1-m1: The manuscript contains two versions of the conclusion section.
  - R1-m2: The accessible volume simulations are described but results are not presented.
  - R1-m3: The effect of oxygen scavenging system on diffusion measurements is mentioned but not quantified.
  - R1-m4: The fraction of surface-adsorbed molecules is stated as less than 20% but no quantification method is described.
  - R1-m5: The statement about "high-throughput" capabilities is not supported by throughput data.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The combination of FRET and diffusion in nanochannels is not entirely novel, building on prior work by the same group (Fontana et al., 2019). The application to ARF-DBD oligomerization is new but the approach is incremental.
  - Scientific importance: Moderate. The biological question about ARF-DBD oligomerization is relevant, but the impact is limited by the preliminary nature of the data and the lack of strong quantitative conclusions.
  - Interdisciplinary readership: The work bridges biophysics, microfluidics, and plant biology, which could appeal to a broad audience. However, the presentation assumes significant expertise in single-molecule techniques, which may limit accessibility.
  - Technical soundness: The core methodology is sound in principle, but the presented evidence is incomplete. Key controls, error analysis, and calibration are missing. The diffusion-based oligomerization inference is indirect and requires more rigorous validation.
  - Readability for nonspecialists: The manuscript is reasonably well-written but includes technical jargon and assumes familiarity with smFRET, ALEX, and nanofluidics. The dual conclusion sections and missing figures detract from clarity.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript shows promise but requires substantial additional data, controls, and analysis to support the main claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** "our data on fluorescently labelled ARF-DBDs suggest that, at nanomolar concentrations, ARF-DBDs are exclusively present as monomers"
- **Evidence pointer** Results section "ARF-DBDs at nanomolar concentration are monomeric", Figure 4 (not provided)
- **Concern** The claim of exclusive monomeric presence is based on comparing measured diffusion coefficients (78, 65, 69 µm²/s for three labelled constructs) with theoretical values for monomer (73 µm²/s) and dimer (55 µm²/s). The measured values are 6-13% higher than the monomer prediction, which the authors attribute to localization error. However, the analysis does not account for the uncertainty in the theoretical calculations, the effect of the fluorescent label on hydrodynamic radius, or the polydispersity of the sample. The two-Gaussian fitting procedure is described but no fit parameters, errors, or goodness-of-fit metrics are provided. The conclusion of "exclusively monomers" is too strong given the indirect nature of the measurement and the lack of error analysis.
- **Why it matters** The oligomerization state of ARF-DBDs is a key biological claim of the manuscript. If the diffusion measurements cannot distinguish between monomer and dimer with statistical confidence, the claim is unsupported. The contrast with crystal structures is a central narrative point, so this claim needs to be rigorously established.
- **Resolution test** Provide a full error analysis of the diffusion coefficient measurements, including the uncertainty in the theoretical predictions. Show that the measured values are statistically distinguishable from the dimer prediction. Include replicate measurements and a discussion of systematic errors (e.g., label effects, channel geometry, localization error). If possible, validate with an independent method (e.g., fluorescence correlation spectroscopy).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The analysis of the diffusion coefficients in presence of an OSS shows decreased diffusion coefficients for both free DNA and bound DNA. This effect is likely to be caused by (I) the reduced photobleaching which in turn reduces the average localization error and (II) the increased viscosity of the sample"
- **Evidence pointer** Results section "Changes in the diffusion coefficient of labelled DNA can be used to monitor ARF-DNA interaction", Figure 3 (not provided)
- **Concern** The diffusion coefficient measurements are central to two of the three main results. However, the accuracy of these measurements is not well characterized. The authors acknowledge that localization error inflates the measured diffusion coefficient but do not provide a quantitative correction. The effect of the nanochannel confinement (200 nm height) on the diffusion of a DNA molecule with a hydrodynamic radius potentially comparable to the channel dimension is not discussed. The viscosity correction for OSS is mentioned but not quantified. The precision of the measurements (e.g., standard deviation across replicates) is not reported.
- **Why it matters** Diffusion coefficients are used both as a binding readout and to infer oligomerization state. If the measurements have large systematic errors or poor precision, both conclusions are compromised. The comparison with theoretical values requires confidence in the experimental accuracy.
- **Resolution test** Provide a detailed characterization of the diffusion measurement accuracy, including calibration with a known standard, a correction for localization error, and a discussion of confinement effects. Report the precision of the measurements (e.g., standard error across multiple experiments). Quantify the viscosity effect of OSS and correct for it.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** "Measuring the DNA construct alone (2.5 nM in PBS buffer containing oxygen scavenger system) in the fluidic devices led to a single population centered at E* = 0.39; a second sample containing saturating concentration (256 nM) of MpARF2-DBD showed the characteristic shift toward a lower FRET efficiency (E* = 0.31)"
- **Evidence pointer** Results section "The interaction between ARF and labelled DNA can be visualized using smFRET in nanochannels", Figure 2c (not provided)
- **Concern** The FRET-based detection of binding is presented as a single experiment with one concentration of protein. No titration curve, binding affinity, or specificity control (e.g., with a non-specific DNA sequence) is shown. The shift from E* = 0.39 to 0.31 is reported but the width of the distributions, the fraction of bound molecules, and the reproducibility are not described. The statement that this confirms binding "rather than surface-induced artifacts" is not supported by any control experiment.
- **Why it matters** The FRET readout is the primary evidence for the interaction between ARF-DBD and DNA. Without quantitative analysis, controls, and replicates, the reader cannot assess the reliability of this result. The claim that this rules out surface artifacts is particularly important given the known challenges of surface interactions in nanochannels.
- **Resolution test** Provide a full titration curve with multiple protein concentrations, a specificity control with a mutated or non-specific DNA sequence, and replicate measurements. Report the fraction of bound DNA as a function of protein concentration and, if possible, an apparent binding affinity. Include a control with a surface-passivated channel and no protein to demonstrate the absence of surface-induced FRET changes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim support
- **Claim pointer** "We asked to which extent the use of parallel nanochannels allows performing titration experiments without the supervision of an operator... The ARF containing samples showed the characteristic shift towards lower FRET efficiencies when compared to the one without ARF; however, the noise present on the E*S histogram makes the evaluation of the DNA bound fraction inaccurate."
- **Evidence pointer** Results section "The interaction between ARF and labelled DNA can be visualized using smFRET in nanochannels", Figure 2d-e (not provided)
- **Concern** The authors acknowledge that the data quality in the titration experiment is poor, yet they use this to claim feasibility of automated titrations. The statement that the "characteristic shift" is observed is qualitative and the noise is described as making analysis "inaccurate." This is a weak basis for a feasibility claim.
- **Why it matters** The claim of automated titration capability is a potential advantage of the platform. If the data quality is insufficient for quantitative analysis, the practical utility of this feature is questionable. The authors suggest that the issue is due to photobleaching in the absence of OSS, but this is speculative.
- **Resolution test** Provide a revised titration experiment with improved data quality (e.g., using an inert atmosphere or a more stable fluorophore). Show that the bound fraction can be quantified with acceptable accuracy. Alternatively, temper the claim to reflect the current limitations.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "The predicted diffusion coefficients presented in this chapter were calculated using HYDROPRO... The calculations were performed loading the pdb file of the protein or complex of interest, setting the temperature to 20 °C and the viscosity of the solution to 1 cP"
- **Evidence pointer** Materials and methods section "Calculation of theoretical diffusion coefficients"
- **Concern** The theoretical diffusion coefficients are calculated for the protein or complex in bulk solution. However, the experimental measurements are performed in 200 nm high nanochannels. The confinement is likely to reduce the measured diffusion coefficient compared to bulk, yet the comparison is made directly. Additionally, the calculations are for the unlabelled protein, while the experiments use fluorescently labelled proteins, which will have a larger hydrodynamic radius.
- **Why it matters** The comparison between experimental and theoretical diffusion coefficients is used to infer the oligomerization state. If the theoretical values do not account for the experimental conditions (confinement, labelling), the inference is unreliable.
- **Resolution test** Either correct the theoretical values for confinement effects and label size, or perform control experiments with a well-characterized protein of known oligomerization state to validate the comparison. Discuss the expected magnitude of these effects.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Manuscript structure
- **Evidence pointer** Conclusion section
- **Issue** The manuscript contains two distinct conclusion sections with overlapping content. This is likely a drafting error.
- **Required correction** Merge the two conclusion sections into a single, coherent conclusion.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results
- **Evidence pointer** Materials and methods section "Accessible Volume simulations"
- **Issue** The accessible volume simulations are described in the methods but no results from these simulations are presented in the results section. The expected FRET efficiencies based on the simulations are not compared with the experimental values.
- **Required correction** Either present the simulation results and compare them with experimental data, or remove the methods description if the simulations are not used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Quantification
- **Affected element** Results
- **Evidence pointer** Results section "Changes in the diffusion coefficient of labelled DNA can be used to monitor ARF-DNA interaction"
- **Issue** The effect of OSS on diffusion coefficients is described qualitatively. The viscosity increase from 1% glucose is mentioned as approximately 2%, but the expected effect on the diffusion coefficient is not calculated or compared with the observed decrease.
- **Required correction** Quantify the expected viscosity effect and compare it with the observed change in diffusion coefficient to support the interpretation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Quantification
- **Affected element** Results
- **Evidence pointer** Results section "ARF-DBDs at nanomolar concentration are monomeric"
- **Issue** The fraction of adsorbed molecules is stated as less than 20%, but the method for determining this fraction is not described. The two-Gaussian fit is mentioned but no fit parameters or uncertainties are provided.
- **Required correction** Describe how the fraction of adsorbed molecules was determined and provide the fit parameters and uncertainties.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Claim support
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The manuscript claims "high-throughput measurements" as a general feature of the platform. However, no throughput data (e.g., number of molecules detected per unit time, number of conditions per experiment) are presented.
- **Required correction** Either provide throughput metrics or temper the claim to reflect the demonstrated capabilities.

## Risk / unsupported claims
- The claim that ARF-DBDs are "exclusively present as monomers" at nanomolar concentrations is not supported by the presented data, as the diffusion-based inference lacks error analysis and validation.
- The claim that the FRET shift confirms specific binding "rather than surface-induced artifacts" is unsupported, as no control experiments are described.
- The claim of "high-throughput measurements" is not supported by any quantitative throughput data.
- The feasibility of automated titrations is claimed despite acknowledged poor data quality in the presented experiment.
- The comparison of experimental diffusion coefficients with theoretical values does not account for nanochannel confinement or fluorescent labelling, making the quantitative comparison unreliable.
- The effect of OSS on diffusion coefficients is attributed to two factors, but only one is quantified and the expected magnitude is not compared with observations.