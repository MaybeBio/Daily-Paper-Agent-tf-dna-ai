## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion) without figures or supplementary materials
- **Assessment boundary** Scientific claims, methodological soundness, and conceptual framework as presented in the text; figure content assessed only through textual descriptions
- **Shared manuscript claim summary** The manuscript integrates deep mutational scanning (DMS) data with atomistic simulations, machine learning, and statistical thermodynamic modeling to characterize allostery hotspots in the TetR transcription factor. The central claim is that allostery hotspots are broadly distributed across the protein structure because the induction function can be modulated through two distinct mechanisms: perturbing inter-domain coupling (γ) or intra-domain properties (ϵL, ϵD). This mechanistic degeneracy explains the DMS observations and provides a framework for hotspot identification and prediction.
- **Visible evidence base** Text descriptions of DMS data from prior publications, molecular dynamics simulation results, free energy surfaces, machine learning classification accuracies, Bayesian inference of thermodynamic parameters, and dose-response curve analyses
- **Missing materials affecting confidence** All figures, tables, and supplementary materials; detailed simulation protocols; specific numerical results for free energy calculations; machine learning feature lists and model performance metrics; Bayesian inference priors and posterior distributions; sequence alignment details for homolog comparisons

## Reviewer

- **Overall assessment** This manuscript presents a synthesis of the authors' prior computational studies on allostery in TetR, framed around a mechanistic degeneracy hypothesis that distinguishes between inter-domain coupling and intra-domain perturbations. The conceptual framework is thoughtful and the integration of diverse computational approaches is commendable. However, the manuscript reads more as a review of the authors' own work than as a primary research article, and the central claims are presented without sufficient quantitative evidence in the text. The thermodynamic model is elegant but its validation rests on figures and analyses that are not fully described. The machine learning results, while interesting, show variable accuracy across homologs and the practical utility for hotspot prediction remains unclear. The manuscript would benefit from a clearer articulation of what is new versus what is synthesized from prior publications, and from more rigorous quantitative support for the key claims.

- **Who would be interested in the results, and why** Researchers in protein allostery, computational biophysics, and protein engineering would find this manuscript relevant. The mechanistic degeneracy framework offers a conceptual advance that could inform experimental design in allosteric drug discovery and protein engineering. The integration of DMS data with computational analysis is timely and could interest the deep mutational scanning community. The discussion of machine learning for hotspot prediction, particularly the transfer learning results, may appeal to those working at the interface of computational biology and machine learning.

- **Major strengths** The manuscript provides a coherent conceptual framework for understanding allostery hotspots that reconciles the broad distribution of hotspots with the functional requirements of allosteric regulation. The integration of multiple computational approaches, from atomistic simulations to statistical thermodynamics, is comprehensive and demonstrates methodological breadth. The mechanistic degeneracy hypothesis is testable and provides clear predictions for experimental validation. The discussion of challenges and future directions is thoughtful and identifies important open questions in the field.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that the thermodynamic model, with parameters (ϵL, ϵD, γ), quantitatively describes the induction activity of TetR and its mutants, and that Bayesian inference extracts these parameters with "generally small uncertainties."
- **Evidence pointer** Section "Distinct Contributions from Allostery Hotspots: Atomistic Simulations and Statistical Thermodynamics Modeling", Figure 6
- **Concern** The quantitative validation of the thermodynamic model is not presented in sufficient detail. The text states that Bayesian inference was used to extract parameters from experimental induction data, but does not provide the number of mutants analyzed, the quality of fits, the uncertainty ranges, or the model comparison against alternative formulations. The claim that parameters are extracted with "generally small uncertainties" is not supported by any numerical evidence in the text. Furthermore, the model assumes that R* and K are constants not perturbed by mutations, which is a strong assumption that is not justified or tested.
- **Why it matters** The thermodynamic model is central to the manuscript's conceptual framework. Without clear evidence that the model quantitatively captures the experimental data and that the extracted parameters are reliable, the mechanistic degeneracy hypothesis rests on qualitative rather than quantitative support. This weakens the manuscript's primary contribution.
- **Resolution test** Provide the number of mutants analyzed, the posterior distributions or credible intervals for the extracted parameters, goodness-of-fit metrics, and a comparison of model predictions against experimental dose-response curves. Ideally, include a cross-validation or holdout analysis to demonstrate predictive power.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and contribution
- **Claim pointer** The manuscript presents the integration of DMS data with computational analyses as providing "new insights" and a "mechanistic framework" for understanding allostery hotspots.
- **Evidence pointer** Throughout the manuscript, particularly the Introduction and Concluding Discussions
- **Concern** The manuscript synthesizes results from prior publications by the same author (references 49, 50, 57, 58, 59) but does not clearly delineate what constitutes new analysis or new conceptual synthesis presented here for the first time. The mechanistic degeneracy idea is introduced as a framework, but it is unclear whether this is a novel contribution of this manuscript or a synthesis of conclusions already published in the cited works. The manuscript would benefit from an explicit statement of what is new.
- **Why it matters** For a journal like Journal of Molecular Biology, the expectation is that the manuscript provides a distinct contribution beyond the authors' prior publications. If the framework is already implicit in the cited works, the manuscript's value as a standalone contribution is diminished.
- **Resolution test** Add a section or paragraph explicitly stating which aspects of the framework are new to this manuscript, which are synthesized from prior work, and what new analyses (if any) were performed for this manuscript. If no new analyses were performed, the manuscript should be reframed as a review or perspective.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor
- **Claim pointer** The manuscript claims that machine learning analysis identified a "modest (~5–6) set of features" that classify allostery hotspots with accuracy ranging from "~50–60% for TtgR and RolR to ~80% for TetR and MphR."
- **Evidence pointer** Section "Properties that Distinguish Allostery Hotspots: Insights from Machine Learning Analysis of DMS data and Atomistic Simulations", Figure 3A
- **Concern** The classification accuracy of 50–60% for two of the four homologs is barely above chance for a binary classification problem. The manuscript does not discuss what this means for the practical utility of the machine learning approach. Additionally, the feature selection method (genetic algorithm-neural network) is described only briefly, and the stability of feature selection across cross-validation folds is not discussed. The manuscript also does not address potential overfitting given the relatively small number of hotspots compared to the feature space.
- **Why it matters** The machine learning results are presented as supporting the mechanistic framework, but the variable and sometimes near-chance accuracy raises questions about the reliability of the approach for hotspot prediction. This is particularly important given the manuscript's later claim that machine learning can be leveraged for hotspot prediction.
- **Resolution test** Provide a more detailed description of the machine learning methodology, including cross-validation strategy, feature selection stability, and a comparison against simpler baseline models. Discuss the implications of the variable accuracy across homologs and whether the approach is suitable for prospective prediction.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes extensive atomistic simulations, including "long (~50 μs) MD simulations" and free energy calculations using metadynamics, and claims these provide insights into the structural and energetic basis of allostery.
- **Evidence pointer** Sections "Properties that Distinguish Allostery Hotspots" and "Distinct Contributions from Allostery Hotspots"
- **Concern** The simulation details are not provided. The manuscript does not specify the force field, water model, simulation temperature, pressure coupling, or the specific systems simulated (e.g., which mutants, which functional states). The free energy calculations are described only qualitatively, with no information on the collective variables used, the convergence criteria, or the estimated errors. This level of detail is insufficient for reproducibility.
- **Why it matters** The simulation results are used to support key claims about the distinct contributions of hotspot residues. Without adequate methodological detail, these results cannot be evaluated or reproduced by other researchers, which is a fundamental expectation for computational studies.
- **Resolution test** Provide a detailed methods section or supplementary material describing the simulation protocols, including software, force field parameters, system setup, equilibration procedures, production run lengths, and analysis methods. For free energy calculations, specify the collective variables, bias parameters, and convergence assessment.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scope and generalizability
- **Claim pointer** The manuscript claims that the "mechanistic framework and the multi-faceted computational approaches are expected to be applicable to the analysis of other allostery systems, especially those sharing the similar two-domain structural topology."
- **Evidence pointer** Abstract and Concluding Discussions
- **Concern** The generalizability claim is made without any supporting evidence from other systems. The manuscript analyzes only TetR and its homologs, and the thermodynamic model is specifically tailored to a two-domain architecture with anti-cooperative binding. It is not clear how the framework would apply to allosteric systems with different architectures, such as monomeric enzymes with a single active site or multi-subunit complexes with cooperative interactions.
- **Why it matters** The claim of general applicability is a significant part of the manuscript's stated significance. Without evidence or a clear argument for why the framework should generalize, this claim is speculative and may overstate the manuscript's contribution.
- **Resolution test** Either temper the generalizability claim to be more modest, or provide a more detailed argument for why the framework should apply to other two-domain systems, including specific predictions that could be tested in future work.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Equation 1
- **Evidence pointer** Section "Distinct Contributions from Allostery Hotspots"
- **Issue** The equation for fold change (FC) is presented without derivation or definition of all terms. The parameter c is defined as inducer concentration, but the relationship between c and the binding constant K is not clear from the equation as written. The term R* is described as "rescaled transcription factor copy number" but the rescaling is not explained.
- **Required correction** Provide a brief derivation or explanation of the equation, including the definition of each term and the assumptions made. Clarify the relationship between c, K, and the binding probability.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Figure descriptions
- **Evidence pointer** Figures 1, 2, 3, 5, 6, 7, 8, 9, 10
- **Issue** The manuscript refers to many figures but the text descriptions are often insufficient to understand what is shown. For example, Figure 5C is described as showing free energy surfaces projected onto two collective variables, but the specific systems and conditions for each panel are not described in the text.
- **Required correction** Ensure that each figure is described in sufficient detail in the text so that the reader can understand the key findings without needing to see the figure. Consider adding a figure legend that is more comprehensive.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Allostery hotspot" definition
- **Evidence pointer** Introduction and Key Observations from DMS Analysis
- **Issue** The term "allostery hotspot" is used throughout but the operational definition is not precise. The manuscript states that hotspots are sites where a significant fraction of mutations abolish induction, with a threshold of ~25%, but it is not clear how this threshold was chosen or whether it was applied consistently across the four homologs.
- **Required correction** Provide a clear operational definition of "allostery hotspot" and justify the threshold used. Discuss whether the results are sensitive to the choice of threshold.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of machine learning for hotspot prediction
- **Evidence pointer** Section "Prediction of Allostery Hotspots"
- **Issue** The manuscript discusses machine learning for hotspot prediction but does not compare the approach to existing methods in the literature, such as those based on evolutionary conservation, coevolutionary analysis, or structure-based energy calculations.
- **Required correction** Add a brief comparison to existing hotspot prediction methods and discuss the advantages and limitations of the proposed approach relative to these methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Bayesian inference analysis
- **Evidence pointer** Section "Distinct Contributions from Allostery Hotspots"
- **Issue** The manuscript states that Bayesian inference was used but does not describe the priors used for the parameters, the sampling method, or the number of samples. This makes it difficult to assess the reliability of the parameter estimates.
- **Required correction** Provide details on the Bayesian inference procedure, including the priors, sampling method, and convergence diagnostics.

## Risk / unsupported claims
- The claim that the thermodynamic model quantitatively describes induction activity with "generally small uncertainties" in parameter estimates is not supported by numerical evidence in the text.
- The claim that the mechanistic framework is "expected to be applicable to other allostery systems" is speculative and not supported by evidence from other systems.
- The claim that free energy calculations can be used to rank the rescuability of hotspot mutations is based on a qualitative comparison and lacks quantitative correlation analysis.
- The claim that transfer learning with 10% of target data achieves near-equivalent accuracy to full training is not supported by specific accuracy numbers or statistical comparisons.
- The claim that the "diagonal shape" of the free energy surface in the apo state encodes anti-cooperativity is presented without quantitative analysis of the free energy surface.
- The claim that hotspot mutations can be classified as primarily affecting inter-domain coupling versus intra-domain properties is presented as a dichotomy, but the manuscript acknowledges that most mutations affect both to varying degrees, making the classification less clear-cut than implied.