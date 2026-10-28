## Review setup
- **Input scope** Full manuscript text including main text and supplemental methods
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided material
- **Shared manuscript claim summary** The authors use coarse-grained polymer simulations to show that bridging-induced phase separation (BIPS) of transcription factor binding to transcription units generates intrinsic transcriptional noise through correlated clustering dynamics, while stochastic loop extrusion by cohesin-like factors contributes to extrinsic noise across cells. They propose that 3D chromatin organization provides a mechanistic basis for transcriptional heterogeneity.
- **Visible evidence base** Main text figures referenced (Figs. 1-3), supplemental figures (S1, S3, S5-S7), simulation methods, and parameter tables
- **Missing materials affecting confidence** Actual figure images and data values are not provided; only figure captions and in-text descriptions are available. Quantitative results (e.g., exact noise values, correlation times) are described qualitatively in the text. The supplemental material is referenced but not fully included.

## Reviewer
- **Overall assessment** This manuscript presents a computational study addressing an important and timely question: how 3D chromatin organization contributes to transcriptional noise. The authors employ a well-established coarse-grained polymer modeling framework and systematically investigate how two key biophysical mechanisms, BIPS and loop extrusion, influence transcriptional variability. The central claims, that BIPS drives intrinsic noise through correlated clustering dynamics and that stochastic loop extrusion contributes to extrinsic noise, are mechanistically plausible and potentially significant. However, the manuscript as presented has several limitations that prevent full evaluation: quantitative results are described qualitatively, key figures are not available for inspection, and the connection between simulation observables and experimental measurements of transcriptional noise requires further justification. The work is likely to interest researchers in chromatin biophysics, gene regulation, and stochastic gene expression, but the current evidence base is insufficient to fully establish the claims.

- **Who would be interested in the results, and why** Researchers studying chromatin organization and its functional consequences, particularly those interested in the biophysical mechanisms of gene regulation. The work connects polymer physics concepts (phase separation, loop extrusion) to transcriptional variability, which is relevant to understanding developmental decisions, cellular heterogeneity, and disease states such as cancer. Experimentalists using single-cell transcriptomics, imaging approaches (DNA/RNA FISH), and genome engineering (e.g., cohesin degradation) would find the predictions testable and relevant to interpreting their data. The modeling community working on chromatin structure and gene regulation would also be interested in the methodological framework.

- **Major strengths** The manuscript addresses a fundamental question about the mechanistic origins of transcriptional noise, which has broad biological relevance. The modeling framework is physically motivated and builds on prior work by the same group, providing continuity with established approaches. The systematic exploration of parameters (TU spacing, TF valency, loop extrusion parameters) is thorough. The distinction between intrinsic and extrinsic noise mechanisms is conceptually valuable. The connection to experimental observations, particularly the finding that cohesin degradation has subtle effects on mean expression but potentially larger effects on variability, is an important insight.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that BIPS-driven clustering is the primary mechanism for intrinsic transcriptional noise, and that loop extrusion contributes to extrinsic noise.
- **Evidence pointer** Figures 2 and 3, described in text; supplemental figures S3, S5-S7
- **Concern** The quantitative evidence supporting the central claims is not presented in the provided material. The text describes trends (e.g., "noise increases with d_TU up to ~100 kbp", "noise decreases rather than increases" with fixed loops) but does not provide numerical values, error bars, or statistical comparisons. Without access to the actual data, it is impossible to assess the magnitude of the reported effects, whether they are statistically robust, or whether they are biologically meaningful. The boomerang plots are described but not shown with quantitative axes.
- **Why it matters** The central claims rest on quantitative comparisons between simulation conditions and against the binomial baseline. If the deviations from the binomial model are small or within simulation noise, the conclusions would be substantially weakened. The reader cannot evaluate the strength of the evidence without the actual data.
- **Resolution test** Provide the actual figure data with numerical values, error bars, and statistical tests comparing conditions. Show the magnitude of overdispersion relative to the binomial baseline and demonstrate that the reported effects are robust across simulation repeats.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The manuscript claims that the simulation model captures biologically relevant features of transcriptional noise, and that predictions can be tested experimentally.
- **Evidence pointer** Section I (Simulation Methods), Section II (Measuring Transcriptional Activity)
- **Concern** The model uses a simplified representation where transcriptional activity is equated with TF binding to TUs. The authors state that this quantity "was shown to have a significant positive correlation with experimental data on nascent transcription" (citing Brackley et al. 2021), but the nature and strength of this correlation is not described. The mapping from simulation time to real time is acknowledged to be approximate (with gamma/m set to 1 for computational convenience), and the implications of this for the interpretation of correlation times are not discussed. The model also assumes fixed loops for loop extrusion, which is a simplification of the dynamic process.
- **Why it matters** The biological relevance of the findings depends on whether the simulation observable (fraction of time TF is bound) is a faithful proxy for transcriptional activity. If the correlation with experimental data is weak or condition-dependent, the conclusions may not transfer to real biological systems. The time mapping issue affects the interpretation of correlation times and whether the predicted noise timescales are experimentally accessible.
- **Resolution test** Provide the quantitative correlation between simulation observables and experimental data from the cited work. Discuss the sensitivity of the results to the time mapping and the fixed-loop approximation. Consider whether dynamic loop extrusion would alter the conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Conceptual framing
- **Claim pointer** The manuscript distinguishes intrinsic noise (within a single cell over time) from extrinsic noise (across cells), attributing the former to BIPS and the latter to loop extrusion.
- **Evidence pointer** Main text, Figures 2 and 3
- **Concern** The distinction between intrinsic and extrinsic noise in the simulation context is not fully clarified. In the simulations, "different cells" are represented by different simulation runs with different random seeds. The intrinsic noise is measured as temporal fluctuations within a single run, while extrinsic noise is the variability across runs. However, the manuscript does not clearly explain how the simulation setup maps to the biological distinction, particularly given that the same physical processes (TF binding, clustering) operate in both cases. The claim that loop extrusion contributes "more significantly" to extrinsic than intrinsic noise is presented without a quantitative comparison.
- **Why it matters** The conceptual framework of intrinsic versus extrinsic noise is central to the manuscript's interpretation. If the mapping between simulation observables and these biological concepts is not rigorous, the conclusions may be overstated or misinterpreted.
- **Resolution test** Provide a clear operational definition of intrinsic and extrinsic noise in the simulation context. Quantitatively decompose the total noise into intrinsic and extrinsic components and show how each mechanism (BIPS, loop extrusion) contributes to each component.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Parameter sensitivity
- **Claim pointer** The manuscript claims that the dependence of noise on TU spacing (d_TU) is non-monotonic, with a maximum near ~100 kbp, and that this reflects the transition where BIPS becomes effective.
- **Evidence pointer** Figure 2(a), described in text
- **Concern** The non-monotonic dependence on d_TU is a key finding, but the manuscript does not provide a mechanistic explanation for why the maximum occurs at ~100 kbp specifically. The relationship between d_TU, the interaction range of TF-mediated bridging, and the polymer physics of the system is not analyzed in detail. It is unclear whether this length scale is robust to changes in other parameters (e.g., TF concentration, binding strength, polymer stiffness).
- **Why it matters** The claim that the noise maximum at ~100 kbp is biologically meaningful (e.g., related to typical gene spacing or TAD sizes) requires demonstrating that this is a robust feature of the model rather than a consequence of specific parameter choices.
- **Resolution test** Perform a parameter sweep to show that the non-monotonic dependence on d_TU persists across a range of TF concentrations, binding energies, and polymer stiffness values. Provide a theoretical or scaling argument for why the maximum occurs at the observed length scale.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Experimental testability
- **Claim pointer** The manuscript states that predictions "could be tested with single-cell experiments" and suggests specific experimental approaches.
- **Evidence pointer** Main text, final paragraph
- **Concern** The experimental predictions are stated at a general level without specific, falsifiable predictions. For example, the manuscript does not specify how the predicted relationship between TU spacing and noise would manifest in experimental measurements, or how the predicted contribution of loop extrusion to extrinsic noise could be distinguished from other sources of variability. The connection between the simulation timescales and experimentally accessible timescales is not addressed.
- **Why it matters** For the work to have impact beyond the modeling community, it needs to generate concrete, testable predictions that experimentalists can evaluate. Vague suggestions for experimental testing are insufficient.
- **Resolution test** Provide specific, quantitative predictions (e.g., expected fold-changes in noise under specific perturbations, expected correlation lengths, expected differences between conditions) that could be directly tested in single-cell experiments.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of transcriptional noise
- **Evidence pointer** Main text, first paragraph
- **Issue** The term "transcriptional noise" is defined as "variable gene expression" but the relationship between this definition and the specific simulation observable (standard deviation of phi) is not explicitly stated in the main text.
- **Required correction** Clearly define the simulation observable for noise (sigma(phi)) and explain how it relates to the biological concept of transcriptional noise.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Simulation parameters
- **Evidence pointer** Section IV (Simulation Parameters)
- **Issue** The parameter values for TF concentration and valency are listed in tables, but the rationale for choosing these specific values is not provided. It is unclear whether they are based on experimental estimates or are arbitrary.
- **Required correction** Provide justification for the parameter choices, citing experimental measurements where available, and discuss the sensitivity of the results to these choices.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure descriptions
- **Evidence pointer** Figures 1-3
- **Issue** The figure descriptions in the text are qualitative. Without seeing the actual figures, it is difficult to assess the visual evidence for the claims.
- **Required correction** Ensure that the figures clearly show the quantitative data with appropriate axes, error bars, and statistical annotations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of related work
- **Evidence pointer** Main text, introduction and discussion
- **Issue** The manuscript does not discuss alternative models of transcriptional noise (e.g., stochastic promoter switching, transcriptional bursting models) and how the proposed mechanism relates to or differs from these.
- **Required correction** Add a brief discussion of how the proposed mechanism complements or challenges existing models of transcriptional noise.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "noise" versus "heterogeneity"
- **Evidence pointer** Main text, throughout
- **Issue** The terms "noise" and "heterogeneity" are used somewhat interchangeably. In the field, "noise" often refers to stochastic fluctuations within a population, while "heterogeneity" can encompass deterministic differences. Clarifying the usage would improve precision.
- **Required correction** Define the terms clearly and use them consistently throughout.

## Risk / unsupported claims
- The claim that BIPS is the primary mechanism for intrinsic noise is supported by simulation results but the quantitative evidence is not visible in the provided material.
- The claim that loop extrusion contributes to extrinsic noise is supported by the comparison between fixed-loop and variable-loop conditions, but the magnitude of the effect is not quantified.
- The claim that the noise maximum at d_TU ~ 100 kbp is related to the BIPS transition is plausible but not rigorously demonstrated.
- The speculation that loop extrusion enhancing noise may explain why evolutionarily young genes are noisier is presented without supporting evidence or a detailed mechanistic argument.
- The statement that the simulation observable (phi) correlates with experimental nascent transcription data is referenced but the correlation strength and conditions are not described.
- The mapping between simulation time and real time is acknowledged to be approximate, but the implications for the interpretation of correlation times and noise timescales are not discussed.