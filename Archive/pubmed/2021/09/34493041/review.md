## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that Trp146 in the p53 DNA-binding domain (DBD) exhibits temperature-dependent fluorescence behavior, with static emission intensity maximal at 30 degrees C, time-resolved decays described by a stretched exponential at all temperatures, and an increase in the stretched exponential parameter at 37 degrees C. Molecular dynamics simulations reveal distance jumps between Trp146 and specific quenching residues, and essential dynamics analysis indicates restricted global protein motions above 37 degrees C. The authors interpret these findings as evidence for reduced structural heterogeneity of DBD with increasing temperature and discuss implications for temperature modulation of p53 binding to partners including DNA.
- **Visible evidence base** Abstract text only; no numerical data, spectra, simulation parameters, or statistical analyses provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental methods, MD simulation setup and force field details, fluorescence decay fitting procedures, error estimates, and any statistical tests

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting biophysical study linking temperature-dependent fluorescence of a single tryptophan residue to protein dynamics via MD simulations. However, the evidence as presented is insufficient to establish the central claims. The relationship between the stretched exponential parameter and structural heterogeneity is asserted rather than demonstrated, and the connection between MD-derived distance jumps and the observed static fluorescence behavior is speculative. The abstract lacks quantitative details, error analysis, and a clear mechanistic model. The final claim regarding p53 binding to partners is not supported by any direct evidence in the abstract.
- **Who would be interested in the results, and why** Researchers in protein biophysics, particularly those studying intrinsically dynamic proteins and conformational ensembles, would find the temperature-dependent fluorescence and MD approach of interest. Investigators working on p53 structure and function, especially in the context of temperature-sensitive mutations or thermal regulation of tumor suppressor activity, may also be interested. Methodologically, those using time-resolved fluorescence to probe protein disorder could find the stretched exponential analysis relevant.
- **Major strengths** The combination of static and time-resolved fluorescence with MD simulations provides a multi-scale approach to studying protein dynamics. The use of a single tryptophan residue as an intrinsic probe is a well-established strategy. The temperature range chosen (25 to 45 degrees C) is physiologically relevant and may have implications for understanding p53 behavior under febrile conditions.
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
- **Assessment against Nature-style criteria** Originality: The approach is not novel in its individual components, though the specific application to p53 DBD at multiple temperatures may offer some new insight. Scientific importance: The potential link between temperature, protein dynamics, and p53 function is of interest, but the abstract does not establish a clear functional consequence. Interdisciplinary readership: The work bridges fluorescence spectroscopy and computational simulation, which could appeal to a broad biophysical audience, but the abstract is too technical and lacks context for nonspecialists. Technical soundness: Cannot be fully assessed from the abstract alone; the lack of quantitative details and error analysis is a concern. Readability for nonspecialists: The abstract assumes familiarity with stretched exponential decays and essential dynamics analysis, and the logical flow from fluorescence data to MD interpretation to biological implications is not clearly articulated.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents interesting observations but does not provide sufficient quantitative support or a coherent mechanistic framework to validate the central claims. A revised manuscript with full data, error analysis, and a clearer connection between simulation and experiment would be needed to assess the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that the stretched exponential parameter "was found to increase at 37 degrees C" and interpret this as indicative of structural disorder.
- **Evidence pointer** Abstract text, location not provided
- **Concern** The abstract states that the stretched exponential decay is observed at all temperatures and that the parameter increases at 37 degrees C, but no numerical values, uncertainties, or statistical significance are provided. It is unclear whether this increase is reproducible, what the magnitude of the change is, and whether it is statistically distinguishable from the values at other temperatures. Furthermore, the interpretation of the stretched exponential parameter as a direct measure of structural disorder is not justified. Stretched exponential decays can arise from multiple photophysical mechanisms, including solvent relaxation, excited-state reactions, or distributed quenching rates, and the assignment to structural disorder requires additional evidence.
- **Why it matters** The central claim of temperature-dependent structural heterogeneity rests on this parameter. Without quantitative data and a validated interpretation, the conclusion is not supported.
- **Resolution test** Provide the fitted stretched exponential parameters with standard errors for each temperature, report the number of independent measurements, and include a statistical test comparing values across temperatures. Additionally, justify the assignment of the stretched exponential to structural disorder, for example by correlating it with MD-derived conformational distributions or by ruling out alternative photophysical explanations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that "the times that these quenchers spend close to or far from Trp146 can provide an explanation for the static fluorescence behavior."
- **Evidence pointer** Abstract text, location not provided
- **Concern** The abstract reports distance jumps in MD trajectories between Trp146 and residues Arg110, Asp228, Cys229, and Gln144, but no quantitative relationship is established between the occupancy times of these quenchers and the measured static fluorescence intensity. The static emission maximum at 30 degrees C is not explained by any specific MD-derived metric. The claim that quencher proximity times "can provide an explanation" is speculative and lacks a direct correlation analysis or a kinetic model linking MD timescales to fluorescence observables.
- **Why it matters** The connection between simulation and experiment is the core of the paper's argument. Without a quantitative link, the MD results remain descriptive and do not validate the fluorescence interpretation.
- **Resolution test** Perform a quantitative correlation between the fraction of simulation time each quencher resides within a quenching distance of Trp146 and the static fluorescence intensity at each temperature. Alternatively, compute a predicted fluorescence intensity from MD-derived quenching rates and compare directly with experimental values. Report correlation coefficients and confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that "essential dynamics analysis of the MD trajectories indicates a significant restriction of protein global motions above 37 degrees C" and that this is "consistent with a decrease in the structural heterogeneity of DBD as the temperature increases."
- **Evidence pointer** Abstract text, location not provided
- **Concern** The essential dynamics analysis is mentioned without any quantitative output, such as eigenvalues, eigenvector projections, or measures of conformational space sampled. The claim of "significant restriction" is not supported by any numerical threshold or statistical comparison. Moreover, the inference from restricted global motions to decreased structural heterogeneity is not straightforward, as local fluctuations could still be large even if global motions are constrained. The consistency argument is circular unless an independent measure of heterogeneity is provided.
- **Why it matters** The conclusion about temperature-dependent structural heterogeneity is a key finding. Without quantitative support from the MD analysis, the claim is unsubstantiated.
- **Resolution test** Report the essential dynamics results, such as the cumulative variance explained by the first few eigenvectors, the trace of the covariance matrix, or the radius of gyration distribution, at each temperature. Provide a statistical comparison of these metrics across temperatures and demonstrate that the reduction in global motion correlates with a reduction in conformational heterogeneity as measured by an independent metric, such as root-mean-square fluctuation of backbone atoms or cluster analysis of conformations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors state that "the results are also discussed in view of understanding how temperature can modulate the p53 capability to binding partners, including DNA."
- **Evidence pointer** Abstract text, location not provided
- **Concern** No direct evidence of p53 binding to any partner is presented in the abstract. The connection between the observed fluorescence and MD results and the functional capability of p53 to bind DNA or other proteins is entirely speculative. The abstract does not include any binding assays, mutagenesis studies, or even a qualitative correlation with known binding data.
- **Why it matters** The broader biological relevance of the study is claimed but not demonstrated. This weakens the significance of the work for a general readership and overstates the implications.
- **Resolution test** Either remove the claim about binding capability from the abstract or provide direct experimental evidence, such as binding affinity measurements at the same temperatures, or a well-supported discussion that explicitly links the observed conformational changes to known binding interfaces with structural rationale.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Static fluorescence data
- **Evidence pointer** Abstract text, location not provided
- **Issue** The abstract states that static emission spectra exhibit an intensity maximum at 30 degrees C "without any substantial peak shift," but no information is given about the magnitude of the intensity change, the spectral range, or the reproducibility across replicates.
- **Required correction** Provide the relative intensity values at each temperature, the standard deviation, and the spectral range monitored. Clarify what constitutes a "substantial" peak shift.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** MD simulation details
- **Evidence pointer** Abstract text, location not provided
- **Issue** No information is provided about the MD simulation length, force field, water model, temperature coupling scheme, or equilibration protocol. These details are essential for assessing the reliability of the distance jump analysis and essential dynamics results.
- **Required correction** Include a brief description of the simulation parameters in the abstract or refer to a methods section where these details are fully described.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Temperature dependence of stretched exponential parameter
- **Evidence pointer** Abstract text, location not provided
- **Issue** The abstract reports that the stretched exponential parameter increases at 37 degrees C but does not state whether it decreases at 45 degrees C or remains elevated. The interpretation of a monotonic decrease in structural heterogeneity with temperature is not consistent with a non-monotonic parameter trend.
- **Required correction** Report the parameter values at all four temperatures and discuss the trend explicitly, including any non-monotonic behavior.

## Risk / unsupported claims
- The claim that the stretched exponential parameter increase at 37 degrees C indicates reduced structural heterogeneity is unsupported without quantitative data and a validated interpretation of the stretched exponential.
- The claim that MD-derived quencher proximity times explain the static fluorescence behavior is unsupported without a quantitative correlation or kinetic model.
- The claim that essential dynamics analysis shows significant restriction of global motions above 37 degrees C is unsupported without numerical results and statistical comparison.
- The claim that the results inform understanding of temperature modulation of p53 binding to partners is unsupported by any direct evidence in the abstract.
- The overall conclusion that structural heterogeneity decreases with increasing temperature is not established from the provided evidence.