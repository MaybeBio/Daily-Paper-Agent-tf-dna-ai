## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract, without access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report atomistic and free energy simulations of TAR RNA binding to TAT protein in BIV and HIV systems. They claim enthalpically driven binding in BIV, entropically favored binding in HIV, a broader global basin in HIV attributed to binding-induced loop fluctuation, consistency with NMR data indicating classical entropic allostery, and a binding-competent conformation that facilitates subsequent cyclin-T1 binding.
- **Visible evidence base** Abstract text only. No simulation details, thermodynamic quantities, error estimates, NMR comparisons, or methodological parameters are provided.
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, convergence criteria, free energy calculation methods, NMR data and fitting procedures, structural figures, and any statistical or error analysis.

## Reviewer
- **Overall assessment** The abstract presents an interesting hypothesis regarding distinct allosteric mechanisms in two homologous RNA systems. However, the evidence base available for review is limited to the abstract, which precludes verification of the central claims. The thermodynamic distinction between BIV and HIV binding is stated without quantitative support, and the link between loop fluctuation and entropic allostery is asserted rather than demonstrated. The claim of consistency with NMR is plausible but cannot be assessed without the comparative data.
- **Who would be interested in the results, and why** Researchers in RNA biophysics, allostery, and molecular simulation would find the comparative thermodynamic analysis of interest. The proposed distinction between enthalpic and entropic allostery in structurally similar RNA scaffolds could inform studies of RNA-protein recognition and viral replication mechanisms. The potential connection to the TAT-TAR interaction as a drug target may also attract virologists and medicinal chemists.
- **Major strengths** The comparative design using two viral systems is a clear strength, as it allows mechanistic differences to be isolated. The integration of simulation with NMR-derived observations, if properly executed, would strengthen the biological relevance of the findings. The conceptual framing around conformational selection and entropic allostery is timely and potentially impactful.
- **Major Concerns** The abstract does not provide quantitative thermodynamic data, error estimates, or convergence metrics. The claim that loop fluctuation generates a binding-competent conformation for cyclin-T1 is speculative without structural or functional evidence. The NMR corroboration is mentioned but not substantiated with specific data or fitting details. The mechanistic distinction between the two systems is presented as categorical, but the statistical robustness of this distinction is not assessable.
- **Minor Comments** The abstract would benefit from stating the simulation timescales and the number of replicas. The phrase "classical entropic allostery onset" is vague and should be defined more precisely. The relationship between the broader global basin and the binding-competent conformation is not clearly articulated.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is moderate to high, as the comparative enthalpic versus entropic allostery framework in RNA is not common. Scientific importance is potentially significant for the RNA biophysics community, but the broader impact beyond this niche is unclear. Interdisciplinary readership is limited, as the work is primarily of interest to biophysicists and computational chemists. Technical soundness cannot be evaluated from the abstract alone, and the lack of quantitative evidence is a concern. Readability for nonspecialists is acceptable, though some terms such as "entropic allostery" and "global basin" may require more context.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Thermodynamic analysis reveals enthalpically driven binding in BIV and entropically favored binding in HIV."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states a categorical thermodynamic distinction between BIV and HIV binding without reporting any numerical values, such as changes in enthalpy, entropy, or free energy, nor any associated uncertainties or statistical significance.
- **Why it matters** Without quantitative thermodynamic data and error analysis, the reader cannot assess whether the observed difference is robust or within simulation noise. This is the central claim of the paper, and its verification is essential.
- **Resolution test** Provide the computed thermodynamic quantities for both systems, including standard errors or confidence intervals, and demonstrate that the difference between BIV and HIV is statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** "The broader global basin in HIV is attributed to binding-induced loop fluctuation, corroborated by nuclear magnetic resonance (NMR), indicating classical entropic allostery onset."
- **Evidence pointer** Abstract, location not provided
- **Concern** The attribution of the broader global basin to loop fluctuation is presented as a causal interpretation, but the abstract does not describe how this attribution was derived from the simulations. The NMR corroboration is mentioned without specifying which NMR observables were compared or how the comparison was performed.
- **Why it matters** The mechanistic interpretation is a key contribution of the work. If the causal link between loop fluctuation and the global basin is not rigorously established, and if the NMR comparison is not quantitative, the claim of entropic allostery remains unsupported.
- **Resolution test** Describe the analysis that links loop fluctuations to the global basin, and provide a quantitative comparison between simulation-derived observables and NMR data, including any fitting parameters and residuals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Speculative extension
- **Claim pointer** "While this loop fluctuation affects the TAT binding affinity, it generates a binding-competent conformation that aids subsequent effector (cyclin-T1) binding."
- **Evidence pointer** Abstract, location not provided
- **Concern** The claim that loop fluctuation generates a binding-competent conformation for cyclin-T1 is presented as a functional consequence, but no evidence is provided in the abstract that cyclin-T1 binding was simulated or experimentally tested.
- **Why it matters** This extends the findings beyond the TAT-TAR interaction to a downstream signaling event. Without direct evidence, this statement is speculative and could overstate the biological implications of the study.
- **Resolution test** Provide simulation or experimental data on cyclin-T1 binding to the TAR-TAT complex, or clearly reframe this statement as a hypothesis rather than a finding.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methodology description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not specify the simulation timescales, number of replicas, or force field used, which are essential for assessing the reliability of the free energy results.
- **Required correction** Add a brief statement of simulation length and force field in the abstract, or refer to the methods section for these details.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "classical entropic allostery onset"
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "classical entropic allostery onset" is not standard and is ambiguous. It is unclear what distinguishes "classical" from other forms of entropic allostery.
- **Required correction** Define the term or replace it with a more standard description, such as "entropically driven allosteric regulation."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Logical flow
- **Affected element** Relationship between basin and conformation
- **Evidence pointer** Abstract, location not provided
- **Issue** The connection between the "broader global basin" and the "binding-competent conformation" is not clearly explained. It is unclear whether these are the same feature or distinct aspects of the free energy landscape.
- **Required correction** Clarify the relationship between the global basin and the binding-competent conformation, and specify how each is defined in the analysis.

## Risk / unsupported claims
- The claim of enthalpically driven binding in BIV and entropically favored binding in HIV is unsupported without quantitative thermodynamic data.
- The attribution of the broader global basin to loop fluctuation is not verifiable from the abstract.
- The NMR corroboration is mentioned but not substantiated with specific data.
- The claim that loop fluctuation generates a binding-competent conformation for cyclin-T1 is speculative and not supported by evidence in the abstract.
- The overall mechanistic distinction between the two systems is presented as categorical, but statistical robustness is not assessable.