## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, supplementary figure legends referenced but not provided)
- **Assessment boundary** Scientific content, methodological soundness, interpretation of results, and alignment with Nature-style criteria. Editorial quality and language are considered only insofar as they affect scientific clarity.
- **Shared manuscript claim summary** The authors report that TMPyP, a cationic porphyrin, induces complex and tunable nanomechanical changes in DNA, including lengthening and softening of dsDNA, a non-monotonic effect on overstretch transition force with a transient stabilization at low concentrations, reduced cooperativity of the overstretch transition, and lengthening of ssDNA. They propose that these effects arise from multiple binding modes (intercalation, groove binding, ssDNA binding) and that NaCl differentially competes with these modes. They introduce an empirical mathematical model to extract nanomechanical parameters from force-extension curves.
- **Visible evidence base** Main text figures (Figures 1-8) are described but not directly viewable. Supplementary figures (S1-S4) are referenced. Methods section provides experimental details. No raw data or statistical analysis details are provided in the text.
- **Missing materials affecting confidence** The actual figures and supplementary materials are not available for direct inspection. Statistical details (error bars, number of independent measurements, statistical tests used) are not reported in the text. The mathematical model derivation and fitting procedures are described only qualitatively. Data availability statement indicates data are available upon request, not in a public repository.

## Reviewer

### Overall assessment
This manuscript addresses a relevant and timely question: how does TMPyP, a widely used porphyrin with therapeutic applications, affect the nanomechanical properties of DNA? The authors present a systematic single-molecule study using optical tweezers across a broad parameter space of TMPyP concentration, NaCl concentration, and pulling rate. The work is potentially of interest to the biophysics, nucleic acid chemistry, and photodynamic therapy communities. However, the manuscript in its current form has several significant issues that prevent a definitive assessment of the claims. The most critical concerns are: (1) the lack of direct visualization of the data and figures, which precludes verification of the fitting quality and the reported effects; (2) the absence of statistical analysis and error reporting; (3) the empirical nature of the mathematical model and the unclear relationship between fitting parameters and physical quantities; (4) the speculative interpretation of the two binding modes based on indirect evidence; and (5) the lack of a quantitative comparison with established polymer physics models. The core claims are plausible but not fully established from the provided evidence.

### Who would be interested in the results, and why
Researchers in single-molecule biophysics, DNA mechanics, nucleic acid-ligand interactions, and photodynamic therapy would find this work relevant. The demonstration that TMPyP can tune DNA nanomechanics in a concentration-dependent manner, with effects in the pharmacologically relevant nanomolar range, could inform the design of TMPyP-based therapeutic strategies. The empirical model for extracting nanomechanical parameters may also be of methodological interest to the single-molecule community.

### Major Strengths
1. The study covers a wide and systematic parameter space (TMPyP concentration, NaCl concentration, pulling rate), which is commendable for a single-molecule study.
2. The use of a microfluidic system to deliver TMPyP and the control for non-specific adsorption are thoughtful experimental design choices.
3. The development of an empirical model to decompose the complex FEC into distinct regimes is a useful analytical approach.
4. The observation of a non-monotonic effect on overstretch force (transient stabilization at low TMPyP) is potentially novel and interesting.
5. The discussion of the differential effects of NaCl on different binding modes is conceptually interesting.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality and reproducibility
- **Claim pointer** The manuscript claims that TMPyP binding leads to lengthening and softening of dsDNA, reduced cooperativity of the overstretch transition, and increased ssDNA contour length, with specific quantitative values (e.g., up to 37% lengthening, >3% ssDNA lengthening).
- **Evidence pointer** Figures 2, 4, 5, 7, 8; location not provided for specific data points
- **Concern** The figures are not available for direct inspection, and the text does not provide quantitative values with error bars or statistical significance for the key claims. For example, the claim of "up to 37% increase in contour length" is stated in the Discussion but the corresponding figure and analysis are not shown in the text. The number of independent measurements (n) for each condition is not reported. Without this information, the robustness of the reported effects cannot be assessed.
- **Why it matters** Reproducibility and statistical rigor are fundamental to the validity of the conclusions. The lack of error reporting and statistical tests makes it impossible to determine whether the observed effects are significant or within experimental noise.
- **Resolution test** Provide the actual figures with error bars, report the number of independent measurements (n) for each condition, and perform appropriate statistical tests (e.g., ANOVA or t-tests with multiple comparison corrections) to support the claims of significant differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity and interpretation
- **Claim pointer** The authors state that the empirical model (equations 1-4) provides insight into the molecular mechanisms of the effects, and that parameters P1-P6 scale with specific physical quantities (e.g., P1 with contour length, P3 inversely with cooperativity, P4 with stability).
- **Evidence pointer** Materials and Methods, Figure 3; location not provided
- **Concern** The relationship between the empirical fitting parameters and the claimed physical quantities is asserted but not rigorously justified. For example, P1 is stated to "scale with the contour length of dsDNA," but the exact relationship is not defined. The model is described as "empirical," which raises questions about its ability to provide mechanistic insight. Furthermore, the model's ability to uniquely fit the complex FEC with six parameters is not demonstrated, and the potential for parameter correlation or overfitting is not addressed.
- **Why it matters** The interpretation of the results hinges on the validity of the model and the physical meaning of its parameters. If the parameters do not uniquely or accurately reflect the claimed physical quantities, the mechanistic conclusions drawn from them are not reliable.
- **Resolution test** Provide a more rigorous justification for the model, including a demonstration of parameter identifiability (e.g., through fitting to simulated data with known parameters). Validate the model against an established polymer physics model (e.g., extensible worm-like chain) and show that the extracted parameters (e.g., contour length, stretch modulus) are consistent with known values for DNA.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of binding modes
- **Claim pointer** The authors conclude that TMPyP binds to dsDNA by two modes (intercalation and groove binding) with different kinetics, and that the non-monotonic effect on overstretch force reflects a shift between stabilizing and destabilizing binding modes.
- **Evidence pointer** Figures 4, 7, Discussion; location not provided
- **Concern** The assignment of the two binding modes (intercalation vs. groove binding) to the two kinetic phases (fast and slow) is speculative and not directly supported by the data presented. The manuscript does not include any independent measurements of TMPyP binding mode (e.g., circular dichroism, fluorescence, or molecular dynamics simulations) to corroborate this assignment. The claim that "force enhances TMPyP binding" is also not quantitatively supported by a binding model.
- **Why it matters** The mechanistic interpretation is a central claim of the paper. Without direct evidence for the binding modes and their kinetics, the proposed mechanism remains a hypothesis rather than a conclusion.
- **Resolution test** Include independent biophysical measurements (e.g., CD spectroscopy, isothermal titration calorimetry, or stopped-flow kinetics) to directly characterize TMPyP binding modes and kinetics. Alternatively, perform experiments with DNA sequences or conditions that selectively favor one binding mode to test the assignment.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with existing literature
- **Claim pointer** The authors state that "the effect of TMPyP on DNA nanomechanics is unknown" and that their work is the first comprehensive analysis of this kind.
- **Evidence pointer** Introduction, Discussion; location not provided
- **Concern** The introduction and discussion do not adequately review prior single-molecule studies of porphyrin-DNA interactions or related intercalator-DNA nanomechanics. For example, studies on other intercalators (e.g., ethidium bromide, YOYO-1) have shown similar effects on DNA contour length and stiffness. The novelty of the present work relative to these prior studies is not clearly articulated.
- **Why it matters** The claim of novelty is important for the significance of the work. Without a clear comparison to prior art, the reader cannot assess what is genuinely new about this study.
- **Resolution test** Expand the introduction and discussion to include a more thorough review of prior single-molecule studies of DNA-ligand interactions, particularly with intercalators and groove binders. Clearly state what is novel about the present findings (e.g., the specific effects of TMPyP, the wide parameter space, the empirical model).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** AFM control experiments
- **Claim pointer** The authors use AFM imaging to substantiate the TMPyP-induced DNA lengthening effect, reporting a 9% increase in contour length.
- **Evidence pointer** Figure S3, Results; location not provided
- **Concern** The AFM measurements are performed on surface-immobilized DNA, which may not reflect the solution behavior measured by optical tweezers. The manuscript does not discuss potential artifacts of AFM imaging (e.g., tip-sample interactions, dehydration, surface charge effects) that could affect the measured contour length. The discrepancy between the AFM (9%) and optical tweezers (16% at zero force) is attributed to "constraints imposed by binding of DNA to the substrate surface," but this is not tested.
- **Why it matters** The AFM data are used as supporting evidence for a key claim. If the AFM measurements are not reliable or are not directly comparable to the solution measurements, the support is weakened.
- **Resolution test** Provide more details on the AFM imaging conditions and analysis. Discuss potential artifacts and how they were controlled. Consider performing AFM on DNA in solution or using a different surface chemistry to minimize constraints.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract, Results
- **Evidence pointer** Abstract, Figure 2; location not provided
- **Issue** The abstract states that "TMPyP binding leads to the lengthening and softening of dsDNA" but does not mention the non-monotonic effect on overstretch force, which is a notable finding. The Results section describes the effects in a qualitative manner without providing specific numbers or statistical context.
- **Required correction** Include the key quantitative findings and the non-monotonic effect in the abstract. In the Results, provide specific values with error bars and statistical significance for the main effects.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Model presentation
- **Affected element** Materials and Methods, Figure 3
- **Evidence pointer** Materials and Methods, Figure 3; location not provided
- **Issue** The equations for the empirical model are not fully written out in the text. The description of the parameters is brief and does not explain how the model was validated or how the initial guesses for fitting were chosen.
- **Required correction** Provide the full equations in the text or supplement. Describe the fitting procedure in more detail, including the choice of initial parameters, the fitting algorithm, and the criteria for convergence.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability Statement
- **Evidence pointer** Data Availability Statement; location not provided
- **Issue** The data availability statement says "All experimental data are available upon request by writing to the corresponding author." This is not in line with current best practices for data sharing, especially for a Nature-style journal.
- **Required correction** Deposit the raw data in a public repository (e.g., Zenodo, Figshare) and provide a DOI or accession number.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion
- **Evidence pointer** Discussion; location not provided
- **Issue** The term "apparent compliance" and "apparent stiffness" are used but not clearly defined. The relationship between these terms and the standard mechanical properties of DNA (e.g., stretch modulus, persistence length) is not explicitly stated.
- **Required correction** Define these terms clearly and relate them to the standard mechanical parameters used in the field.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 2, 4, 5, 7, 8
- **Evidence pointer** Figures 2, 4, 5, 7, 8; location not provided
- **Issue** The figures are not available for inspection, but based on the text, it is unclear whether the figures include error bars, individual data points, or statistical annotations. The figure legends are not provided in the text.
- **Required correction** Ensure all figures include error bars and statistical annotations. Provide detailed figure legends that explain the experimental conditions and the number of replicates.

### Technical failings that need to be addressed before the case is established
1. Lack of statistical analysis and error reporting (R1-M1).
2. Insufficient justification of the empirical model and its parameters (R1-M2).
3. Speculative assignment of binding modes without direct evidence (R1-M3).
4. Incomplete comparison with prior literature (R1-M4).
5. Potential artifacts in AFM measurements not addressed (R1-M5).

### Assessment against Nature-style criteria
- **Originality**: The work addresses a gap in the literature (TMPyP effects on DNA nanomechanics), but the general phenomenon of ligand-induced changes in DNA mechanics is well established. The specific findings on TMPyP, particularly the non-monotonic effect on overstretch force, have potential originality, but this is not clearly differentiated from prior work on other intercalators.
- **Scientific importance**: The findings could be relevant for understanding how TMPyP exerts its therapeutic effects and for designing DNA-targeting drugs. However, the importance is not fully established without a clearer link to biological or therapeutic outcomes.
- **Interdisciplinary readership**: The topic is of interest to biophysicists, chemists, and biologists. The manuscript is written in a way that is largely accessible, but the lack of clear definitions and the speculative mechanistic model may limit accessibility for non-specialists.
- **Technical soundness**: The experimental approach (optical tweezers with microfluidics) is sound, but the analysis and interpretation have significant gaps, as detailed in the major concerns. The empirical model is not rigorously validated.
- **Readability for nonspecialists**: The manuscript is generally readable, but the abstract and results could be improved by including specific quantitative findings and clearer explanations of the model and its implications.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a relevant question and presents a systematic dataset, but the lack of statistical rigor, the speculative interpretation of binding modes, and the insufficient validation of the empirical model prevent a definitive assessment of the claims. The authors should address the major concerns, particularly the statistical analysis and the justification of the model, before the case is established. If the authors can provide the missing data and analyses, the work could become a valuable contribution to the field.