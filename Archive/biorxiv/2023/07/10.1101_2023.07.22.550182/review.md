## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, conclusions, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological soundness, interpretation of results, and clarity of claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors investigate how the position of an abasic site (AP site) within short DNA duplexes affects duplex stability and dynamics. They combine temperature-dependent FTIR and NMR spectroscopy, T-jump IR kinetics, and coarse-grained MD simulations to show that AP sites introduce an entropic nucleation barrier for base pairing on each side of the lesion. The position of the AP site determines whether the short segment remains frayed or becomes stably hybridized, with sequence context modulating the length scale of this transition. They also report evidence for out-of-register base pairing in certain sequences that can circumvent the nucleation penalty.
- **Visible evidence base** FTIR melting curves, ITC measurements, 2D IR spectra, T-jump IR kinetics, 1H NMR TOCSY/NOESY spectra, coarse-grained MD free-energy profiles, all-atom MD simulations, Markov state model relaxation profiles
- **Missing materials affecting confidence** Full methods details for NMR assignment procedures, specific fitting parameters for global lifetime analysis, convergence criteria for metadynamics simulations, force field validation details for AP site parameters, and raw data for all figures

## Reviewer

- **Overall assessment** This manuscript presents a systematic and multi-technique investigation of how AP site position and sequence context modulate DNA duplex stability and dynamics. The combination of experimental thermodynamics, kinetic measurements, and simulation provides a compelling and mechanistically detailed picture. The central concept of a position-dependent nucleation barrier is well supported by the helix-coil model and MD simulations, and the T-jump experiments provide direct kinetic evidence for metastable partially hybridized states. The work is technically sound in its core claims, though several aspects of the simulation methodology and interpretation of NMR data would benefit from additional clarification. The study is likely to be of interest to the nucleic acid biophysics and DNA damage communities.

- **Who would be interested in the results, and why** Researchers studying DNA lesion recognition and repair, nucleic acid thermodynamics and kinetics, and the biophysics of short oligonucleotide hybridization. The work is also relevant to those developing predictive models for DNA duplex stability, particularly in the context of modified bases and lesions. The methodological combination of experiment and simulation may interest biophysical chemists working on nucleic acid dynamics.

- **Major strengths** The study combines multiple orthogonal techniques to build a consistent mechanistic picture. The helix-coil model provides a simple and interpretable framework for understanding position-dependent destabilization. The T-jump IR experiments directly resolve metastable partially hybridized states, which is a significant advance. The use of sequence variants with different G:C content and placement is well designed to probe sequence effects. The identification of out-of-register base pairing as a potential mechanism to circumvent nucleation penalties is an interesting and novel observation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of simulation methodology
- **Claim pointer** The authors claim that 3SPN.2 coarse-grained MD simulations accurately capture the sequence-dependent free-energy penalties from AP sites, and that the model predicts metastable partially hybridized states consistent with experiment.
- **Evidence pointer** Methods section, coarse-grained MD simulations; Figures 3c-d, 4, 5d-f
- **Concern** The 3SPN.2 model is not parameterized for AP sites, and the authors state that AP sites are incorporated by removing a nucleoside bead. However, the manuscript does not describe how the local interaction parameters around the AP site are adjusted, if at all. The absence of any reparameterization or validation of the AP site representation in 3SPN.2 raises questions about whether the simulation results are quantitatively reliable. The authors acknowledge that 3SPN.2 overestimates the stability of out-of-register configurations, but the extent to which this bias affects the reported free-energy barriers and metastable state populations is not quantified.
- **Why it matters** The simulation results are central to the mechanistic interpretation. If the AP site representation in 3SPN.2 is not validated, the quantitative free-energy barriers and the predicted threshold lengths for stable segment hybridization may be artifacts of the model rather than physical properties.
- **Resolution test** The authors should provide a detailed description of how AP sites are represented in 3SPN.2, including any modifications to interaction parameters. They should also compare simulation predictions against experimental melting temperatures and free energies for at least a subset of sequences to establish quantitative reliability. If reparameterization is not feasible, the authors should clearly state the limitations and avoid overinterpreting quantitative barrier heights.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of NMR data
- **Claim pointer** The authors use 1H NMR TOCSY temperature series to extract melting profiles for individual G:C base pairs and conclude that the terminal G:C base pair in CGCcap-AP2 partially dehybridizes at temperatures well below the main melting transition.
- **Evidence pointer** Results section, NMR spectroscopy; Figures 6b, S38-S45
- **Concern** The assignment of cytosine H5 resonances and the interpretation of temperature-dependent chemical shift changes as direct reporters of base-pair opening is not fully justified. Chemical shifts are sensitive to multiple factors including ring current effects from neighboring bases, stacking interactions, and local conformational changes. The authors do not demonstrate that the observed chemical shift changes are specifically due to base-pair disruption rather than other structural rearrangements. Additionally, the presence of multiple slowly interconverting conformations in CGCcap-AP2 complicates the interpretation of the TOCSY data.
- **Why it matters** The NMR data are used to support the claim that the terminal G:C base pair in CGCcap-AP2 is frayed at equilibrium, which is an important piece of evidence for the position-dependent fraying mechanism. If the NMR interpretation is ambiguous, this claim is weakened.
- **Resolution test** The authors should provide additional evidence that the chemical shift changes track base-pair opening, such as comparison with imino proton exchange measurements or hydrogen-deuterium exchange data. They should also discuss how the presence of multiple conformations affects the interpretation of the TOCSY temperature series.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of conclusions
- **Claim pointer** The authors conclude that the position-dependent destabilization from an AP site is a general phenomenon that depends on the nucleation barrier and the binding stability of the short segment, and that this behavior may extend to other destabilizing modifications.
- **Evidence pointer** Conclusions section
- **Concern** The study is limited to 11-mer duplexes with a limited set of sequence contexts. The claim that the observed behavior is general for other destabilizing modifications is speculative and not directly tested. The authors do not provide a quantitative framework for predicting when position-dependent effects will be significant for other lesions or modifications, which limits the practical utility of the findings.
- **Why it matters** The broader significance of the work depends on whether the mechanism identified here applies beyond the specific sequences and lesion studied. Without a predictive framework or additional test cases, the generalizability claim is not established.
- **Resolution test** The authors should either provide additional experimental or simulation data for other lesion types or modifications, or temper the generalizability claim and clearly state the conditions under which the mechanism is expected to apply.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 2c description
- **Evidence pointer** Results section, helix-coil model
- **Issue** The description of the free-energy profiles in Figure 2c is somewhat unclear. The text refers to "the barrier" and "the short segment" without clearly defining which curve corresponds to which sequence or condition.
- **Required correction** The authors should clarify in the figure caption and text which curves correspond to which AP site positions and explicitly define the barrier and segment being discussed.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** ITC measurements
- **Evidence pointer** Methods section, isothermal titration calorimetry
- **Issue** The ITC measurements are mentioned as providing validation for the FTIR-derived thermodynamics, but the details of the ITC fitting procedure and how the values were compared are not described.
- **Required correction** The authors should provide a brief description of the ITC data analysis and how the results were used to validate the FTIR measurements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of simulation results
- **Affected element** Out-of-register base pairing in T11 sequences
- **Evidence pointer** Results section, Figure 7
- **Issue** The authors state that 3SPN.2 simulations predict out-of-register base pairing in T11 sequences but acknowledge that experimental data cannot directly confirm this. The discussion of this discrepancy is brief and does not fully address the implications for the interpretation of the T11 experimental results.
- **Required correction** The authors should expand the discussion of the limitations of the 3SPN.2 model for repetitive sequences and clarify how the potential presence of out-of-register conformations affects the interpretation of the experimental melting curves for T11.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Introduction
- **Evidence pointer** Introduction section
- **Issue** The introduction is dense and covers a wide range of topics, from DNA nanotechnology to lesion biology, without a clear narrative thread. The connection between the different applications and the specific question of AP site position effects could be made more explicit.
- **Required correction** The authors should streamline the introduction to more directly motivate the specific question of position-dependent effects and how the study addresses a gap in current understanding.

## Risk / unsupported claims
- The claim that the position-dependent destabilization mechanism identified for AP sites may extend to other destabilizing modifications is speculative and not directly tested in this work.
- The quantitative accuracy of the 3SPN.2 free-energy barriers for AP site-containing duplexes is not established, given the lack of reparameterization for the AP site.
- The interpretation of NMR chemical shift changes as direct reporters of base-pair opening is not fully validated.
- The claim that out-of-register base pairing can circumvent the nucleation penalty is based primarily on simulation predictions and lacks direct experimental confirmation.
- The generalizability of the threshold lengths for stable segment hybridization (2-3 base pairs for G:C-rich, 4-7 for A:T-rich) to other sequence contexts and duplex lengths is not established.