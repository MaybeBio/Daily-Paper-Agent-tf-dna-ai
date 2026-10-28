## Review setup
- **Input scope** Full manuscript text (main text, significance statement, materials and methods summary) without supplementary figures, tables, or appendices
- **Assessment boundary** Scientific claims, experimental design, theoretical modeling, and interpretation as presented in the provided text; supplementary materials referenced but not evaluated
- **Shared manuscript claim summary** The authors report that p53 protein (p534M ΔTAD) forms homogeneous condensates with low-affinity random dsDNA, and that subsequent addition of high-affinity p21 DNA triggers a transition to hollow condensates. They propose a mechanism involving p21 DNA-induced peripheral gelation, core depletion of protein and random DNA, and gelation-induced spinodal decomposition leading to hollow structure formation. A three-component continuum model is presented to support this mechanism.
- **Visible evidence base** Main text figures referenced (Figs. 1–6), supplementary figures referenced (Figs. S1–S8), movies referenced (Movies S1–S4), and methods summary; actual figure data not directly inspectable
- **Missing materials affecting confidence** Supplementary figures and methods details, movies, raw data, model equations and parameters, full methods protocols, statistical details

## Reviewer
- **Overall assessment** This manuscript addresses an interesting and timely question in biomolecular condensate biology: how multi-component condensates can adopt hollow morphologies. The experimental system is well-chosen, and the observation of a hollow condensate transition driven by a second DNA species is novel and potentially significant. The combination of experimental characterization (confocal, FRAP, AFM-FS, FCS) with a continuum model is commendable. However, several concerns limit the strength of the conclusions as currently presented. The mechanistic claim of "gelation-induced spinodal decomposition" rests heavily on the model, but the model omits key experimentally observed features (size increase, component escape, competitive binding), and the direct experimental evidence for spinodal decomposition is indirect. The relationship between the model's mean-field assumptions and the molecular reality of p53-DNA interactions requires clarification. The significance statement's implications for disease and therapy are speculative and not supported by data in the text. Overall, the work is promising but requires substantial revision and additional analysis to fully establish the proposed mechanism.

- **Who would be interested in the results, and why** Researchers in the fields of biomolecular condensates, phase separation, biophysics of DNA-protein interactions, and cellular organization would find this work relevant. The demonstration of a pathway-dependent transition to hollow condensates, and the proposed spinodal decomposition mechanism, could inform understanding of condensate architecture and function. The modeling framework may be of interest to theorists working on multi-component phase separation. The potential implications for drug delivery (hollow condensates as carriers) could attract applied researchers, though this remains speculative.

- **Major strengths** 
  1. The experimental system is clean and well-controlled, using a well-characterized p53 variant and defined DNA substrates.
  2. The observation of a hollow condensate transition is visually striking and clearly documented with confocal microscopy and fluorescence intensity profiles.
  3. The identification of three distinct kinetic stages with measurable time constants (τ1, τ2) provides a quantitative framework.
  4. The combination of multiple biophysical techniques (FRAP, AFM-FS, FCS) to characterize material properties is thorough.
  5. The continuum model successfully reproduces key qualitative features and provides a testable mechanistic hypothesis.
  6. The authors acknowledge limitations of the model and discuss discrepancies with experiments.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim
- **Claim pointer** "These findings reveal fundamental principles of three-component hollow condensate formation" and "p21 DNA induces localized gelation at the condensate periphery, leading to a progressive depletion of protein and Random DNA in the core. This compositional shift drives spinodal decomposition inside the condensate, ultimately giving rise to hollow condensates."
- **Evidence pointer** Figures 4–6; Discussion
- **Concern** The central mechanistic claim is that gelation-induced spinodal decomposition drives hollow condensate formation. However, the direct experimental evidence for spinodal decomposition is indirect. The authors infer spinodal decomposition from the Min Eigenvalue crossing below zero in the model (Fig. 6A), but the experimental data (Fig. 2B) only show intensity changes, not direct evidence of spinodal decomposition kinetics (e.g., characteristic length scale selection, bicontinuous structures). The model's prediction of spinodal decomposition is not experimentally validated with structural measurements at the relevant length scales. Additionally, the model omits experimentally observed features (size increase, component escape, competitive binding), which the authors acknowledge. The claim that the mechanism is "gelation-induced" spinodal decomposition requires direct experimental manipulation of gelation (e.g., altering p21 DNA binding affinity, crosslinking) to demonstrate causality.
- **Why it matters** The proposed mechanism is the central novel contribution of the paper. If the evidence for spinodal decomposition is only model-based and not experimentally validated, the mechanistic claim is not fully established. The distinction between spinodal decomposition and other possible mechanisms (e.g., nucleation and growth, Ostwald ripening, active transport) is important for understanding the physics of hollow condensate formation.
- **Resolution test** Provide direct experimental evidence for spinodal decomposition, such as time-resolved small-angle X-ray scattering or super-resolution microscopy showing characteristic length scale evolution. Alternatively, perform experiments that manipulate gelation (e.g., using p21 DNA mutants with different binding affinities, or varying crosslink density) and show that hollow formation is correspondingly affected. If direct experimental evidence is not feasible, the authors should temper the mechanistic claim and clearly state that spinodal decomposition is a model-predicted mechanism requiring further validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** "We formulated a three-component continuum model... We assumed that the system follows Cahn-Hilliard dynamics, governed by a free energy driving the condensate formation between p534M ΔTAD and Random DNA or p21 DNA."
- **Evidence pointer** Figure 5; SI Appendix (model details not provided in main text)
- **Concern** The model is described only in general terms in the main text. The free energy functional, interaction parameters, and model equations are not presented in the main text, and the SI Appendix is not available for review. The model's assumptions (e.g., mean-field interactions, the form of the gelation field, the critical threshold for gelation) cannot be evaluated. The authors state that the model "quantitatively recapitulates the key experimental observations" (Figs. 1–3), but the quantitative comparison is not shown in the main text. The model's predictive power and robustness to parameter variations are not discussed.
- **Why it matters** The model is a key component of the mechanistic argument. Without access to the model details and quantitative comparison to experiments, the validity of the model and its support for the proposed mechanism cannot be assessed. The claim of "quantitative recapitulation" is unverifiable from the provided text.
- **Resolution test** Provide the full model equations, parameters, and free energy functional in the main text or SI. Show quantitative comparisons between model predictions and experimental data (e.g., intensity profiles, time constants) with appropriate error analysis. Discuss parameter sensitivity and model robustness. If the model cannot quantitatively reproduce all experimental observations, clearly state which features are and are not captured.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Experimental controls
- **Claim pointer** "Hollow condensates formed only when protein and Random DNA were combined first, followed by the addition of p21 DNA. Conversely, no hollow structures were observed when protein was initially mixed with p21 DNA before adding Random DNA or when all three components were combined simultaneously."
- **Evidence pointer** Figure S7 (referenced); Results section
- **Concern** The order-of-addition experiments are critical for establishing the kinetic origin of hollow formation. However, the text does not provide details on the concentrations used in these experiments, the time scales over which observations were made, or whether the final equilibrium state was reached. It is unclear whether the lack of hollow structures in the alternative orders reflects a kinetic trap or a different equilibrium state. Additionally, the text does not report whether the alternative orders produce homogeneous condensates, phase-separated mixtures, or no condensates at all.
- **Why it matters** The order-of-addition dependence is a key piece of evidence for the kinetic mechanism. Without proper controls and characterization of the alternative pathways, the conclusion that hollow formation is pathway-dependent is not fully supported.
- **Resolution test** Provide detailed experimental conditions for the order-of-addition experiments, including concentrations, time courses, and final states. Characterize the structures formed in the alternative orders (e.g., homogeneous, multilayered, no condensate). If possible, show that the alternative orders eventually reach the same final state given sufficient time, or demonstrate that they are kinetically trapped.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative analysis
- **Claim pointer** "τ1 displays a strong dependence on p21 DNA concentration (Fig. 3 B, i), whereas τ2 remains relatively stable across the tested concentration range (Fig. 3 B, ii)."
- **Evidence pointer** Figure 3B; Results section
- **Concern** The time constants τ1 and τ2 are defined in the SI Appendix, which is not available. The text does not explain how these time constants are extracted from the data, what functional forms are used for fitting, or how many independent replicates were performed. The claim that τ1 depends strongly on concentration while τ2 is stable is not supported by statistical analysis in the main text. Error bars and significance tests are not shown in the referenced figure.
- **Why it matters** The concentration dependence of τ1 and τ2 is used to support the mechanistic model. Without proper statistical analysis and clear definitions, the quantitative claims are not verifiable.
- **Resolution test** Provide clear definitions of τ1 and τ2, the fitting procedures, and the number of replicates. Show statistical analysis (e.g., error bars, significance tests) for the concentration dependence. If the claims are based on limited replicates, state this and discuss the implications.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Throughout
- **Issue** The term "hollow condensates" is used throughout, but the text does not clearly define the structural criteria for "hollow" (e.g., shell thickness, lumen size relative to condensate size, volume fraction of the lumen). The distinction between a hollow condensate and a core-shell structure with a thin shell is not clarified.
- **Required correction** Provide a clear operational definition of "hollow" with quantitative criteria, and discuss how the observed structures meet these criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Model limitations
- **Evidence pointer** Discussion
- **Issue** The authors acknowledge that the model does not capture size increase, component escape, or competitive binding, but the discussion of these limitations is brief. The implications of these omissions for the validity of the mechanistic conclusion are not fully explored.
- **Required correction** Expand the discussion of model limitations, including how the omitted features might affect the predicted mechanism and what additional physics would be needed to capture them.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Materials and Methods
- **Issue** The methods section states that "detailed protocols... are shown in SI Appendix" but does not provide key parameters in the main text (e.g., protein and DNA concentrations, buffer conditions, imaging parameters). This limits the reproducibility of the experiments from the main text alone.
- **Required correction** Provide key experimental parameters in the main text or ensure that the SI Appendix contains all necessary details for reproduction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Significance statement
- **Evidence pointer** Significance
- **Issue** The significance statement claims "broader implications for disease mechanisms and therapeutic strategies," but no disease or therapeutic context is discussed in the main text. This claim is unsupported.
- **Required correction** Either remove the claim or add a brief discussion of potential disease/therapeutic implications in the Discussion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 4
- **Evidence pointer** Figure 4 (referenced)
- **Issue** The FRAP and AFM-FS data are described qualitatively ("markedly lower and slower recovery," "significantly higher Young's modulus values"), but statistical details (n, p-values, error bars) are not provided in the main text.
- **Required correction** Provide statistical details for the FRAP and AFM-FS measurements, including the number of independent measurements and appropriate statistical tests.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Model-experiment comparison
- **Affected element** Figure 5C
- **Evidence pointer** Figure 5C (referenced)
- **Issue** The claim that simulated τ1 and τ2 "closely matched experimental results" is not quantified. The figure is not shown in the main text, and no numerical comparison or goodness-of-fit measure is provided.
- **Required correction** Provide a quantitative comparison between simulated and experimental τ1 and τ2 values, including appropriate metrics (e.g., R², RMSD) and discussion of discrepancies.

## Risk / unsupported claims
- The claim that "gelation-induced spinodal decomposition" is the mechanism for hollow condensate formation is not fully supported by direct experimental evidence; the spinodal decomposition inference is primarily model-based.
- The claim of "quantitative recapitulation" of experimental observations by the model is unverifiable without access to the model details and quantitative comparisons.
- The significance statement's implications for "disease mechanisms and therapeutic strategies" are not supported by data or discussion in the main text.
- The claim that τ1 and τ2 "closely matched" between simulation and experiment is not quantified.
- The claim that the model "successfully reproduced the key experimental observations" (Figs. 1–3) is not demonstrated with quantitative comparisons in the main text.
- The statement that "the lumen and the surrounding dilute phase share similar molecular composition and mobility" is based on FCS measurements, but the FCS data are not shown in the main text and the statistical significance of the comparison is not provided.
- The claim that "p21 DNA on the surface can displace Random DNA by competing for binding to the protein" is inferred from fluorescence intensity profiles but is not directly tested (e.g., with binding assays or competition experiments).