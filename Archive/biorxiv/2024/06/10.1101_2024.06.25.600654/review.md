## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, conclusion, materials and methods, and supplementary materials description
- **Assessment boundary** Scientific validity, methodological rigor, interpretation of results, and support for claims based on the provided text
- **Shared manuscript claim summary** The authors combine SEC-SAXS with AlphaFold-predicted structures to model conformational states of full-length ParB1 from Vibrio cholerae, showing that parS1 DNA loading brings CTPase domains closer to facilitate clamping, and that an intrinsically disordered linker regulates self-association for partition assembly formation
- **Visible evidence base** SEC-SAXS profiles, REGALS and SVD analyses, pair distribution functions, Kratky plots, AlphaFold models, CORAL-based integrative modeling, AUC, DLS, SEC, CTPase assays, biolayer interferometry
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; detailed CORAL modeling parameters and validation metrics; raw SAXS data and fit statistics; experimental replicates for key measurements; linker mutant characterization details; condensate formation data referenced as unpublished

## Reviewer
- **Overall assessment** This manuscript presents a potentially valuable approach for combining SEC-SAXS with AI-predicted structures to study conformational changes in ParB1, a protein involved in bacterial chromosome segregation. The authors provide evidence for parS1-induced conformational changes and identify a linker region that modulates self-association. However, the study has significant limitations in the validation of structural models, the interpretation of SAXS data from heterogeneous samples, and the strength of conclusions drawn from indirect measurements. The claim that the linker restricts self-association is based on a single triple mutant with limited characterization. The manuscript would benefit from more rigorous validation of the integrative models and additional functional experiments to support the mechanistic conclusions.
- **Who would be interested in the results, and why** Researchers studying bacterial chromosome segregation, ParB/parS systems, CTP-dependent protein switches, and those interested in hybrid approaches combining SAXS with AI-predicted structures. The methodological approach may also interest structural biologists working on intrinsically disordered proteins and protein self-association.
- **Major strengths** The combination of SEC-SAXS with AlphaFold predictions is timely and relevant. The use of REGALS for decomposing overlapping elution profiles is appropriate. The identification of a linker region that modulates self-association provides a testable hypothesis. The authors are transparent about limitations of their models.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: moderate. While the combination of SAXS and AlphaFold is not entirely new, its application to ParB1 provides some novel insights. Scientific importance: moderate. The findings advance understanding of ParB1 conformational changes but do not fundamentally alter current models. Interdisciplinary readership: limited. The work will primarily interest specialists in bacterial chromosome segregation and structural biology. Technical soundness: questionable. Several methodological concerns need addressing. Readability for nonspecialists: adequate but could be improved with clearer explanations of SAXS concepts.
- **Recommendation posture** Currently not established from the provided evidence. The core claims require additional validation and clarification.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that integrative models built from SAXS data and AlphaFold-predicted rigid domains reveal conformational changes in ParB1 upon parS1 binding, specifically that CTPase domains move closer and a lumen forms below the parS1 binding site
- **Evidence pointer** Results section "Structural modeling of vcParB1 conformational states", Figures 2A-E, S7, S8
- **Concern** The integrative modeling approach using CORAL with rigid domains from AlphaFold predictions requires careful validation. The authors report good chi-square values but do not provide sufficient details on the modeling procedure, including the number of independent runs, convergence criteria, and the variability of solutions. More critically, the use of synthetic SAXS data based on known domain interfaces as additional constraints may bias the models toward expected conformations. The authors should provide a more thorough validation of their models, including cross-validation with independent data, assessment of model uniqueness, and comparison with alternative conformations. The claim that the lumen region forms below the parS1 binding site is based on models that may not be unique given the sparse data.
- **Why it matters** The central conclusion about parS1-induced conformational changes and the formation of a lumen for DNA capture depends entirely on the reliability of the integrative models. If the models are not unique or are biased by the constraints used, the mechanistic conclusions may be incorrect.
- **Resolution test** Provide detailed modeling parameters, show the distribution of solutions from multiple independent runs, demonstrate that the models are not overly constrained by the synthetic data, and validate the models using independent experimental data such as cross-linking or FRET.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that a truncated form of ParB1 (vcParB1trunc) lacking the IDR and CTDD shows concentration-dependent oligomerization, and that the linker region joining the HTHD and CTDD curbs self-association of full-length ParB1
- **Evidence pointer** Results section "A truncated form of vcParB1 devoid of the intrinsically unstructured regions is highly heterogeneous", Figures 3A-F, 4A-C
- **Concern** The evidence for concentration-dependent oligomerization of vcParB1trunc is based on SEC-SAXS elution profiles showing heterogeneity and Rg variation across the peak. However, the authors do not provide quantitative analysis of the oligomeric states, such as molecular weight estimates from SAXS or AUC at multiple concentrations. The AUC data are only presented for a single concentration and show the protein is a monomer at 70 micromolar. The claim that the linker curbs self-association is based on a single triple mutant (P235G, D237G, K239A) with elevated flexibility, but the authors do not provide direct evidence that this mutant actually has increased flexibility or that the observed increase in self-association is specifically due to the linker flexibility rather than other effects of the mutations. The B22 values are presented but the difference between wild-type and linker mutant is not statistically validated.
- **Why it matters** The conclusion that the linker regulates self-association is a key finding of the paper. If the evidence is not robust, this conclusion is not supported. The interpretation of SAXS data from heterogeneous samples is challenging and requires careful quantitative analysis.
- **Resolution test** Provide quantitative analysis of oligomeric states from SAXS and AUC at multiple concentrations, characterize the linker mutant more thoroughly (e.g., circular dichroism, size-exclusion chromatography with multi-angle light scattering), and perform statistical analysis on the B22 values.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that CTP induces a small reduction in the size of ParB1, suggesting a conformational change, but state that models of the CTP-bound state were not obtained due to variability
- **Evidence pointer** Results section "DNA binding induces conformational change in ParB1", Table 1, Figure 1B-C, Figure S7E-F
- **Concern** The SEC-SAXS experiments with CTP were performed with CTP in the mobile buffer, but the authors do not provide details on CTP concentration stability, potential hydrolysis during the experiment, or whether the protein was saturated with CTP. The claim of a small size reduction is based on Rg values, but the difference may not be statistically significant given the error bars. More importantly, the authors state that models of the CTP-bound state could not be obtained due to variability, which limits the interpretation of this result. The authors should either provide more robust evidence for the CTP-induced conformational change or temper their conclusions.
- **Why it matters** The CTP-induced conformational change is part of the proposed mechanism, but the evidence is weak and the models are not presented. Without reliable models, the structural interpretation of the CTP effect is speculative.
- **Resolution test** Provide statistical analysis of Rg differences, ensure CTP saturation, and either obtain reliable models or clearly state the limitations of the CTP experiments.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the combination of SAXS and AlphaFold predictions provides unique insights into ParB1 conformational changes and self-association that are relevant for understanding partition assembly formation
- **Evidence pointer** Throughout the manuscript, particularly Discussion and Conclusion
- **Concern** The authors state that ParB1 forms condensates but reference unpublished results. This is a significant claim that is central to the relevance of the study for partition assembly formation. Without presenting the condensate data, the connection between the observed self-association and biological function is not established. Additionally, the authors do not discuss alternative interpretations of their SAXS data, such as the possibility that the observed changes in Rg are due to changes in hydration or flexibility rather than large-scale conformational changes.
- **Why it matters** The biological relevance of the findings depends on the connection to condensate formation and partition assembly. Without presenting the condensate data, the significance of the self-association observations is unclear.
- **Resolution test** Include the condensate formation data or clearly state that this is a topic for future work. Discuss alternative interpretations of the SAXS data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and uses technical terms without sufficient context. The phrase "chromatography-coupled SAXS" is used without explaining what this means for a general reader.
- **Required correction** Briefly explain what chromatography-coupled SAXS is and why it is advantageous for studying protein conformational changes.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods
- **Evidence pointer** Materials and Methods section "SAXS and SEC-SAXS experiments"
- **Issue** The methods section does not provide sufficient details on the SAXS data collection parameters, such as exposure time, number of frames, and data reduction procedures. The buffer composition for SAXS experiments is not fully specified.
- **Required correction** Provide complete details on SAXS data collection and processing, including buffer composition, temperature, and data reduction steps.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Results section "DNA binding induces conformational change in ParB1", Table 1
- **Issue** The Rg values are presented without error estimates or statistical comparison between conditions. It is unclear if the differences are significant.
- **Required correction** Provide error estimates for Rg values and perform statistical tests to compare conditions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results
- **Evidence pointer** Results section "A truncated form of vcParB1 devoid of the intrinsically unstructured regions is highly heterogeneous"
- **Issue** The authors mention that a repeat AUC run in the presence of CTP rendered the data not analyzable due to aggregation, but do not provide any details on this observation or its implications.
- **Required correction** Provide more details on the CTP-induced aggregation and discuss its potential relevance to the mechanism.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The authors discuss the relevance of their findings for partition assembly formation but do not fully address how the observed self-association relates to the known biology of ParB condensates.
- **Required correction** Expand the discussion to connect the biophysical observations to the biological context of partition assembly formation.

## Risk / unsupported claims
- The claim that ParB1 forms condensates is based on unpublished results and cannot be evaluated from the provided material
- The claim that the linker region curbs self-association is based on a single mutant with limited characterization
- The structural models of the ParB1-parS1 complex are not validated against independent experimental data
- The CTP-induced conformational change is not supported by reliable structural models
- The claim that the lumen region forms below the parS1 binding site for capturing sliding DNA is speculative and based on models that may not be unique