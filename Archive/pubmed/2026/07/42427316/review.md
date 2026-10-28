## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusions, methods, and data availability statements)
- **Assessment boundary** Scientific and technical evaluation of the AF-CALVADOS method, its validation, and its application to proteome-scale simulations
- **Shared manuscript claim summary** The authors present AF-CALVADOS, a coarse-grained simulation model that uses AlphaFold2-derived pLDDT and PAE scores to automatically define and restrain folded domains in multi-domain proteins (MDPs), enabling accurate and scalable simulations of proteins with mixed folded and disordered regions. The method is validated against experimental SAXS data for over 400 proteins and applied to 12,483 human intracellular proteins, with a detailed analysis of 1,487 transcription factors.
- **Visible evidence base** Main text figures (Figures 1-7), supplementary figures and tables referenced (Figures S1-S17, Tables S1-S3), methods section, and data availability statements
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S17, Tables S1-S3) were not provided; specific numerical values for validation metrics (e.g., χ2 values, correlation coefficients) are only partially reported in the text; details of the bootstrapping procedure are not fully described; the PeptoneBench comparison results for individual methods are not shown in the provided material

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially valuable extension of coarse-grained simulation methods to multi-domain proteins by leveraging AlphaFold2 confidence scores. The core idea of using pLDDT and PAE to automatically define folded regions is conceptually sound and addresses a clear limitation of prior approaches that required manual domain definitions. The validation against a large SAXS dataset is commendable in scope. However, the manuscript has several technical concerns that need to be addressed, particularly regarding the interpretation of the PAE-based validation, the treatment of edge cases in the force field, and the biological significance of the proteome-scale analysis. The writing is generally clear, but some methodological details require clarification.
- **Who would be interested in the results, and why** Computational biophysicists and structural biologists studying intrinsically disordered proteins and multi-domain proteins would be the primary audience. Researchers developing or using coarse-grained simulation methods, as well as those interested in proteome-scale conformational ensembles, would find the method and the large-scale dataset valuable. The work may also interest researchers using AlphaFold predictions beyond static structure determination, as it demonstrates a practical use of confidence metrics for dynamical modeling.
- **Major strengths** 1) The automated approach to defining folded domains using pLDDT and PAE scores removes a significant bottleneck in applying coarse-grained simulations to MDPs at scale. 2) The validation set is large and diverse, covering a wide range of disorder content. 3) The proteome-scale application demonstrates clear scalability and provides a publicly available resource. 4) The analysis of transcription factors provides a concrete biological example of the method's utility.
- **Major Concerns** 
  - R1-M1: The use of PAE as a validation target for simulated fluctuations is circular, since PAE is used to define the restraints.
  - R1-M2: The treatment of edge cases in the force field, particularly the interpolation between restrained and unrestrained states, may introduce artifacts that are not fully characterized.
  - R1-M3: The biological interpretation of the transcription factor analysis is somewhat speculative and not strongly supported by the presented data.
  - R1-M4: The comparison to other methods in the PeptoneBench benchmark may be confounded by differences in how the methods were applied or evaluated.
- **Minor Comments** 
  - R1-m1: The description of the switching functions and their parameters could be more explicit.
  - R1-m2: The choice of the ubiquitin test case for intra-domain dynamics is reasonable but limited; a more diverse set of folded domains would strengthen the conclusion.
  - R1-m3: The statement about the "excellent accuracy" of AF-CALVADOS in Figure 5 should be supported by a more quantitative comparison, such as the area under the LOWESS curve values for each method.
  - R1-m4: The manuscript would benefit from a more detailed discussion of the limitations of using a single bead per residue for capturing intra-domain dynamics.
- **Technical failings that need to be addressed before the case is established** R1-M1 (circular validation) and R1-M2 (edge case treatment) are the most critical. R1-M4 (benchmark comparison) also needs clarification.
- **Assessment against Nature-style criteria** 
  - Originality: The approach of using AlphaFold confidence scores to guide coarse-grained simulations is not entirely new, but the specific implementation and the scale of application are novel. The work builds on prior CALVADOS developments and similar efforts by other groups, but the automated, proteome-scale application is a distinct contribution.
  - Scientific importance: The method addresses a real gap in the field and has the potential to enable new types of analysis. The public availability of the large dataset is a significant resource. However, the biological insights derived from the transcription factor analysis are preliminary.
  - Interdisciplinary readership: The work is primarily of interest to computational biophysicists and structural biologists. The methods and results are presented in a way that is accessible to this audience, but the broader biological impact is not yet demonstrated.
  - Technical soundness: The core methodology is sound, but the validation approach has a potential circularity issue (R1-M1) and the edge case treatment needs more careful characterization (R1-M2). The benchmark comparison needs more detail (R1-M4).
  - Readability for nonspecialists: The manuscript is generally well-written and the concepts are explained clearly. The abstract and introduction are accessible. The methods section is technical but appropriate for the target audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the scale of validation is impressive, but the circular validation issue and the edge case treatment need to be addressed before the method can be fully endorsed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation methodology
- **Claim pointer** The authors claim that AF-CALVADOS simulations "capture the structural features defined by the PAE matrices" (Results, section 2.4) and use the agreement between simulated fluctuations (σr) and PAE as a validation metric.
- **Evidence pointer** Results section 2.4, Figures 3, S4, S7-S9
- **Concern** The PAE matrix is used both to define the restraints in the simulation and as a target for validation. This creates a circular argument: the simulation is constrained to reproduce PAE-derived features, so agreement between σr and PAE is expected and does not independently validate the model. The authors acknowledge that PAE is "only indirectly a probe of residue-residue interactions and fluctuations," but the validation approach still relies heavily on this metric. A more independent validation, such as comparison to experimental data that were not used in the parameterization (e.g., FRET, NMR, or SAXS for a held-out set), would be more convincing.
- **Why it matters** The validity of the method rests on its ability to reproduce experimental observations. If the primary validation metric is derived from the same source as the restraints, the evidence for the method's accuracy is weakened. The SAXS validation (Figure 5) is more independent, but the PAE-based validation is presented as a key result and needs to be interpreted with this circularity in mind.
- **Resolution test** The authors should either (a) provide a more independent validation, such as comparison to experimental data not used in the parameterization, or (b) clearly reframe the PAE-based comparison as a consistency check rather than a validation, and discuss its limitations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Force field robustness
- **Claim pointer** The authors state that "edge cases (very low restraining potential) are accounted for by mixing the restraining potential and the CALVADOS nonbonded potentials" (Methods, section 4.1).
- **Evidence pointer** Methods section 4.1, Equations 10-12
- **Concern** The treatment of edge cases, where the restraining potential is weak, involves a complex interpolation scheme between restrained and unrestrained states. The manuscript does not provide a detailed characterization of how this interpolation affects the behavior of the system. For example, it is unclear how the switching function behaves for intermediate values of the restraining prefactor, and whether this could lead to artifacts such as non-physical energy barriers or discontinuities in the potential energy surface. The authors note that ϵ values below 10 kJ/mol should be avoided, but the practical implications of this limitation are not fully discussed.
- **Why it matters** The robustness of the method depends on the reliability of the force field across the entire range of possible restraint strengths. If the edge case treatment introduces artifacts, this could affect the accuracy of simulations for proteins with borderline pLDDT/PAE scores, which are likely to be common in proteome-scale applications.
- **Resolution test** The authors should provide a more detailed analysis of the edge case behavior, such as a systematic study of the potential energy surface for a range of restraint strengths, or a demonstration that the interpolation scheme does not introduce artifacts in test cases.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The authors state that the analysis of disordered regions in 1,487 human transcription factors "can shed light on the interplay between folded and disordered regions" (Abstract) and that the observed compaction of some IDRs in the full-length context is "driven by the correlated motion of the flanking folded residues" (Results, section 2.5).
- **Evidence pointer** Results section 2.5, Figures 6-7, S12-S15
- **Concern** The biological interpretation of the transcription factor analysis is somewhat speculative. The authors identify correlations between sequence features and context-dependent changes in IDR compaction, but the functional significance of these observations is not established. For example, the claim that negatively charged IDRs may "transiently fold back onto the folded domain" is presented as a speculation without direct experimental evidence. The analysis is descriptive and does not yet provide a clear biological insight.
- **Why it matters** The proteome-scale application is a key selling point of the manuscript. If the biological insights are not compelling, the value of the large-scale dataset is reduced. The authors should either strengthen the biological analysis or temper the claims about its significance.
- **Resolution test** The authors should either (a) provide additional analysis that links the observed conformational changes to specific functional outcomes, or (b) reframe the transcription factor analysis as a demonstration of the method's capabilities rather than a biological discovery.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Benchmark comparison
- **Claim pointer** The authors claim that AF-CALVADOS "provides excellent accuracy across the entire order-disorder scale" in the PeptoneBench SAXS benchmark (Results, section 2.4, Figure 5).
- **Evidence pointer** Results section 2.4, Figure 5, S5-S6
- **Concern** The comparison to other methods in the PeptoneBench benchmark may be confounded by differences in how the methods were applied. For example, the authors note that they used 100 conformations for the main comparison, while other methods may have been evaluated with different numbers of conformations or different post-processing steps. The manuscript does not provide a detailed description of how the other methods were run, and the comparison may not be entirely fair. Additionally, the removal of eight proteins measured in urea and the handling of proteins with high similarity to the training data are not fully described.
- **Why it matters** The benchmark comparison is a key piece of evidence for the method's accuracy. If the comparison is not fair or is not well-described, the conclusions drawn from it are weakened.
- **Resolution test** The authors should provide a more detailed description of how the benchmark was run, including the exact settings for each method, and should discuss any potential biases in the comparison.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section 4.1
- **Evidence pointer** Methods section 4.1, Equations 8-10
- **Issue** The description of the switching functions for pLDDT and PAE is somewhat terse. The parameters αpLDDT, βpLDDT, αPAE, and βPAE are defined, but the rationale for the specific functional forms and the choice of parameters is not fully explained.
- **Required correction** Provide a more detailed explanation of the switching functions, including the rationale for the chosen functional forms and parameters, and a discussion of their sensitivity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Validation scope
- **Affected element** Results section 2.4
- **Evidence pointer** Results section 2.4, Figure S10
- **Issue** The ubiquitin test case is used to assess intra-domain dynamics, but this is a single, small, and highly stable protein. It is not clear how representative this is of the broader range of folded domains in the proteome.
- **Required correction** Consider adding additional test cases with different types of folded domains (e.g., larger, more flexible, or with different secondary structure content) to strengthen the conclusion about intra-domain dynamics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Quantitative reporting
- **Affected element** Results section 2.4, Figure 5
- **Evidence pointer** Results section 2.4, Figure 5
- **Issue** The claim of "excellent accuracy" in the benchmark comparison is not supported by specific numerical values. The area under the LOWESS curve is mentioned, but the actual values for each method are not reported in the text.
- **Required correction** Report the numerical values for the area under the LOWESS curve for each method, along with appropriate error estimates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Limitations
- **Affected element** Conclusions
- **Evidence pointer** Conclusions
- **Issue** The limitations of the single-bead-per-residue representation for capturing intra-domain dynamics are mentioned briefly, but the implications for the interpretation of the results are not fully discussed.
- **Required correction** Expand the discussion of limitations to include a more detailed assessment of what the coarse-grained model can and cannot capture, and how this affects the interpretation of the results.

## Risk / unsupported claims
- The claim that AF-CALVADOS "performs well across proteins with varying amounts of ordered and disordered regions" is supported by the SAXS validation, but the strength of this claim depends on the fairness of the benchmark comparison, which is not fully described.
- The claim that the transcription factor analysis "can shed light on the interplay between folded and disordered regions" is not fully supported by the presented data, which are largely descriptive.
- The claim that AF-CALVADOS "captures the structural features defined by the PAE matrices" is weakened by the circularity of using PAE for both restraint definition and validation.
- The statement that "several other parameter sets perform comparably to the chosen parameter set, indicating robustness of the model" is not fully supported by the data shown, as the full parameter scan is only presented in the supplementary material, which was not provided.