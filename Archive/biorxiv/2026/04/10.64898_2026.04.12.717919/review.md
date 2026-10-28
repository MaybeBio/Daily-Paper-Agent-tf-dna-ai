## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific claims, methodological soundness, experimental validation, and comparison with existing approaches as presented in the provided text
- **Shared manuscript claim summary** The authors present CLAIRE, a hybrid physics-deep learning framework for combinatorial de novo design of small-molecule binding proteins. The method combines motif-based interaction scaffolding with LUCS-generated alpha-beta scaffolds, followed by iterative refinement using Rosetta, ProteinMPNN, and AlphaFold2. The authors report experimental success rates of 4/26 designs binding their targets (progesterone and estriol), with NMR structures of two designs in good agreement with design models.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Methods sections; supplementary figure and table references cited but not provided
- **Missing materials affecting confidence** Figures 1-4, all supplementary figures and tables, NMR structural data, raw experimental data, code repository contents, and detailed protocol parameters

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable contribution to the field of de novo small-molecule binding protein design. The combinatorial approach combining motif scaffolding with alpha-beta architectures addresses a genuine limitation of existing methods. However, the evidence provided is insufficient to fully evaluate the claims. The experimental success rate of 4/26 is modest, and critical details regarding binding affinity, specificity, and structural validation are incomplete. The comparison with RFdiffusion is interesting but lacks sufficient methodological detail. The manuscript would benefit from clearer presentation of the workflow's generalizability and limitations.
- **Who would be interested in the results, and why** Computational protein designers, structural biologists, and synthetic biologists interested in generating small-molecule binders without high-throughput screening. The work is also relevant to researchers developing hybrid physics-ML approaches for biomolecular design, as it demonstrates a practical integration of these methods.
- **Major strengths** 1) The combinatorial approach to motif scaffolding into alpha-beta architectures is a novel extension of existing helical bundle methods. 2) The integration of physics-based and deep learning methods for iterative refinement is well-motivated and appears to improve in silico metrics. 3) The experimental validation, while limited, includes structural characterization by NMR, which is a rigorous standard. 4) The comparison with RFdiffusion provides useful context for the field.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (binding affinity not quantified), R1-M2 (limited experimental validation), R1-M3 (insufficient methodological detail for reproducibility), R1-M4 (comparison with RFdiffusion incomplete)
- **Assessment against Nature-style criteria** **Originality**: The combinatorial approach to scaffolding motifs into alpha-beta architectures is a meaningful advance over existing helical bundle methods, though the individual components (BSFF, LUCS, Rosetta, ProteinMPNN) are established. **Scientific importance**: The work addresses a significant challenge in de novo protein design, but the modest experimental success rate and lack of quantitative binding data limit the strength of the claims. **Interdisciplinary readership**: The work bridges computational design, structural biology, and biochemistry, and would appeal to a broad readership if the claims are fully supported. **Technical soundness**: The computational workflow is well-structured, but the manuscript lacks sufficient detail to fully assess reproducibility. The NMR validation is a strength, but the inability to quantify binding affinity is a significant gap. **Readability for nonspecialists**: The manuscript is generally well-written and accessible, though some sections assume familiarity with Rosetta and protein design terminology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding quantitative binding data and methodological detail.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim "a notable experimental success rate (4/26 designs bind their targets)" and that designs bind with "low micromolar range" affinity.
- **Evidence pointer** Results section, Figure 3, Supplementary Figure S14
- **Concern** The binding affinity is only estimated as "low micromolar range" from a single NMR titration experiment, and the authors explicitly state that the protein concentration was above the Kd, which compromises the accuracy of the estimate. No quantitative Kd values are provided for any of the four confirmed binders. The claim of "binding" is based on chemical shift perturbations, which indicate interaction but do not provide thermodynamic or kinetic characterization.
- **Why it matters** For a paper claiming to have designed small-molecule binding proteins, quantitative binding affinity is a core metric. Without reliable Kd values, the functional significance of the designs cannot be assessed, and the claim of "eliminating the need for high-throughput screening" is not supported by the data.
- **Resolution test** Provide quantitative Kd values (e.g., from ITC or NMR-based titration with appropriate protein concentrations below Kd) for at least the three designs selected for further characterization. If ITC is not feasible, provide a rigorous NMR-based binding analysis with appropriate controls and error estimates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that "NMR structures of two designs are in good agreement with design models" and that the designs are "extremely thermally stable."
- **Evidence pointer** Results section, Figure 4, Supplementary Figures S15-S18
- **Concern** Only two structures were solved by NMR, and for one of these (A1E), the ligand pose could not be determined due to lack of NOEs. The statement that structures are "in good agreement" is based on Ca RMSD values of 1.57 Å and 1.46 Å for non-loop regions, but the significance of these values is not discussed in the context of design accuracy. The thermal stability claim is based on CD melting curves showing no change at 95°C, but this is only reported for three designs and the CD data are not shown in the main text.
- **Why it matters** Structural validation is critical for demonstrating that the design method produces proteins with the intended fold and binding site geometry. The inability to determine the ligand pose in A1E is a significant limitation, as it leaves the most important aspect of the design unvalidated. The thermal stability data are presented without sufficient context or comparison to typical designed proteins.
- **Resolution test** Provide a more detailed analysis of the structural agreement, including per-residue RMSD analysis and discussion of the significance of the observed deviations. For A1E, either obtain additional NOE data to determine the ligand pose or clearly state the limitations of the structural model. Present the CD melting data with appropriate controls and discuss the thermal stability in the context of other designed proteins.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that the method "generalizes to alpha-beta architectures" and that the workflow is "generalizable."
- **Evidence pointer** Methods section, Figure 1
- **Concern** The manuscript lacks sufficient detail on several key parameters for reproducibility. The number of motifs generated (230 for estriol, 399 for progesterone) and the number of scaffolds (1,816) are stated, but the criteria for selecting which motifs to use, the specific parameters for the Rosetta Match application, and the details of the HBRefine algorithm are not fully described. The statement that the method "generalizes" is based on only two target molecules, both of which are steroids with similar physicochemical properties.
- **Why it matters** For a methods paper, reproducibility is essential. The lack of detail on key parameters and the limited demonstration of generalizability (only two chemically similar targets) weaken the claim that this is a general approach.
- **Resolution test** Provide complete parameter files and detailed descriptions of all algorithms in the supplementary materials. Demonstrate the method on at least one additional target with different physicochemical properties (e.g., a more polar or flexible molecule) to support the generalizability claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparative analysis
- **Claim pointer** The authors claim that their method achieves "considerably higher in silico success rates" compared to RFdiffusion all-atom.
- **Evidence pointer** Results section, Figure 2, Supplementary Tables S7-S8
- **Concern** The comparison with RFdiffusion is based on in silico metrics only, and the authors do not report experimental testing of the RFdiffusion designs. The statement that RFdiffusion designs "are almost exclusively helical bundle proteins" is presented as a limitation, but the significance of this difference is not discussed in terms of functional outcomes. The in silico success rates are not clearly defined, and the criteria for "success" may differ between methods.
- **Why it matters** A fair comparison between methods is essential for the field to assess the relative merits of different approaches. Without experimental validation of the RFdiffusion designs, the comparison is incomplete, and the claim of superiority is not fully supported.
- **Resolution test** Provide a more detailed description of the in silico success criteria and ensure they are applied consistently to both methods. If feasible, experimentally test a small number of RFdiffusion designs to provide a direct comparison of success rates.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the method "effectively eliminating the need for high-throughput screening," but the experimental success rate of 4/26 (15%) still requires screening of a moderate number of designs. The term "eliminating" is too strong.
- **Required correction** Rephrase to "reducing the need for high-throughput screening" or "enabling screening of small numbers of designs."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Results section, Figure 2
- **Issue** The comparison with RFdiffusion is presented in a single figure, but the specific metrics and criteria for "success" are not clearly defined in the main text. The reader is referred to supplementary tables, which are not provided.
- **Required correction** Define the in silico success criteria in the main text and provide a summary of the key metrics in the figure itself.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Results section
- **Evidence pointer** Results section, Figure 3
- **Issue** The experimental success rate of 4/26 is reported without confidence intervals or statistical analysis. Given the small sample size, the uncertainty in this estimate is substantial.
- **Required correction** Provide confidence intervals for the success rate and discuss the statistical power of the study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Specificity
- **Affected element** Results section
- **Evidence pointer** Results section, "We tested the specificity of these designs"
- **Issue** The specificity data are presented qualitatively ("showed binding to progesterone" for estriol binders), but no quantitative data are provided. The statement that "neither of the tested progesterone binders showed a clear binding signal with estriol" is based on visual inspection of spectra.
- **Required correction** Provide quantitative measures of specificity (e.g., binding affinity ratios or competition experiments) to support the claims.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract, Introduction
- **Issue** The term "combinatorial" is used to describe the approach, but the manuscript does not clearly explain what is being combined. The combinatorial aspect appears to refer to the enumeration of motif-scaffold combinations, but this is not explicitly stated.
- **Required correction** Clarify the meaning of "combinatorial" in the context of the method, either in the abstract or introduction.

## Risk / unsupported claims
- The claim that the method "effectively eliminating the need for high-throughput screening" is not supported by the data, as 26 designs were still screened to obtain 4 binders.
- The claim of "low micromolar range" binding affinity is based on a single experiment with protein concentration above Kd and should be considered an estimate rather than a measured value.
- The claim that the method "generalizes to alpha-beta architectures" is based on only two targets, both steroids, and may not extend to other molecule classes.
- The claim that the method achieves "considerably higher in silico success rates" compared to RFdiffusion is based on in silico metrics only and lacks experimental validation of the comparison method.
- The statement that "NMR structures of two designs are in good agreement with design models" is based on Ca RMSD values that are not contextualized, and for one structure the ligand pose could not be determined.
- The claim that the designs are "extremely thermally stable" is based on CD data for only three designs, with no comparison to typical designed proteins.