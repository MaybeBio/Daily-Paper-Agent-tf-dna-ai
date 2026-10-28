## Review setup
- **Input scope** Full manuscript text (abstract, introduction, models and theory, results, discussion, supplementary material description)
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided text; no external data or code were accessed
- **Shared manuscript claim summary** The authors present a theoretical and computational framework combining mass-action kinetics, analytical theory, and spatial stochastic simulations to show that protein dimerization can either enhance or impair DNA target selectivity, dwell time, and occupancy depending on target spacing, protein-protein binding kinetics, and dimensional reduction via nonspecific DNA binding. They apply the model to explain GAF ChIP-seq data showing selectivity for clustered targets.
- **Visible evidence base** Main text equations (1)-(14), Figures 1-6 referenced, Figures S1-S10 and Tables S1-S7 referenced in supplementary, ChIP-seq data comparison described qualitatively, NERDSS simulation method referenced
- **Missing materials affecting confidence** Supplementary Information (SI text, figures, tables) not provided; Dataset S1 not provided; code repository not accessed; specific parameter values for GAF simulations not fully detailed in main text; ChIP-seq data processing details not described

## Reviewer
- **Overall assessment** This manuscript presents a timely and potentially valuable theoretical framework for understanding how protein dimerization modulates DNA binding kinetics and target selectivity. The central insight, that dimerization can either enhance or impair measured dwell times and occupancy depending on kinetic regimes and target spatial organization, is conceptually important and counterintuitive. The combination of mass-action models, analytical theory, and particle-based simulations is appropriate and rigorous in principle. However, the main text alone does not provide sufficient detail to fully evaluate the derivations, parameter choices, or the robustness of the conclusions. The comparison to GAF ChIP-seq data is intriguing but presented at a level that prevents quantitative assessment. The manuscript would benefit from clearer presentation of the model assumptions, validation of the analytical approximations, and a more detailed account of how the ChIP-seq comparison was performed.

- **Who would be interested in the results, and why** Researchers studying transcription factor dynamics, DNA target search mechanisms, protein-protein interactions in gene regulation, and quantitative modeling of chromatin-associated processes. The framework could also interest experimentalists using single-particle tracking or ChIP-seq who need better interpretive models for how oligomerization affects binding metrics. The general principle that weak protein-protein interactions can dramatically reshape genomic binding distributions has broad relevance to gene regulation.

- **Major strengths**
  1. The conceptual framing is novel and important: most prior models treat protein-DNA interactions in isolation, whereas this work systematically incorporates protein-protein interactions as a competing and cooperating factor.
  2. The three microenvironment models (DNA, DNA+targ, DNA+clusTarg) provide a clean decomposition of effects.
  3. The finding that dimerization can impair dwell time via transient co-localization (Eq. 9) is a non-obvious and mechanistically insightful result.
  4. The application to GAF, a biologically important generalist transcription factor, grounds the theory in a real system.
  5. The use of both analytical theory and spatial stochastic simulations (NERDSS) provides complementary validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their mass-action kinetic models with diffusing nonspecific sites accurately describe protein sliding along DNA and that the approximation is valid in the rate regimes studied.
- **Evidence pointer** Models and Theory, Model Description; Figure S2 referenced
- **Concern** The treatment of nonspecific sites as diffusing particles in a mass-action framework is a significant abstraction. While the authors state that particle-based simulations validate this approximation, the main text does not describe the parameter regimes where this holds or where it breaks down. The claim that "diffusion is not limiting" is stated but not justified with quantitative comparisons between the mass-action and spatial simulation results. Without seeing the validation data (Figure S2), it is impossible to assess whether the analytical results are reliable across the parameter ranges explored.
- **Why it matters** The entire theoretical framework rests on this approximation. If the mass-action model deviates from the spatial simulations in relevant regimes, all subsequent conclusions about dwell times, occupancy, and selectivity could be quantitatively incorrect.
- **Resolution test** Provide in the main text or accessible SI a quantitative comparison between mass-action predictions and NERDSS simulation results across the parameter ranges used, including a clear statement of the maximum deviation and the conditions under which the approximation fails.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that their model "explains how the distribution of the essential GAF protein throughout the genome is highly selective for clustered targets due to protein interactions" and that the ChIP-seq comparison supports this.
- **Evidence pointer** Results, Simulation results reproduce ChIP-seq data; Figure 5d-g; Figure S10
- **Concern** The ChIP-seq comparison is described only qualitatively. The authors state that GAF occupancy is higher at clustered targets and that their model reproduces this, but no quantitative metrics are provided: no correlation coefficients, no goodness-of-fit measures, no description of how the model was parameterized for the genomic comparison, and no account of how ChIP-seq data were processed or normalized. The claim that the model "explains" the data is therefore not supported by the evidence presented in the main text.
- **Why it matters** This is the only direct experimental validation in the manuscript. Without quantitative comparison, the relevance of the theoretical framework to real biological systems remains unestablished.
- **Resolution test** Provide a quantitative comparison between model predictions and ChIP-seq data, including the fitting procedure, parameter values used, statistical measures of agreement, and a discussion of potential confounding factors (e.g., chromatin accessibility, cooperative binding with other factors).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors derive closed-form expressions for dwell times and occupancy under various approximations, including Eq. (8) for reversible dimers and Eq. (13) for the critical koffP threshold.
- **Evidence pointer** Models and Theory, Two-state model; Results sections; SI SVI, SVII referenced
- **Concern** The main text presents several approximate analytical results without showing the derivation or stating the assumptions clearly. For example, Eq. (8) is presented as a general result for reversible dimers, but the conditions under which this approximation holds (e.g., timescale separation, excess nonspecific sites) are not stated. Similarly, Eq. (13) is derived under the assumption χS≫χN, but the sensitivity of the conclusions to this assumption is not discussed.
- **Why it matters** Readers cannot assess the validity or generality of the analytical results without understanding the approximations. This limits the utility of the framework for other researchers who might want to apply it to different systems.
- **Resolution test** Provide derivations in the SI with explicit statement of all assumptions, and include a sensitivity analysis showing how the main conclusions change when these assumptions are relaxed.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "dimerization enhances selectivity for locally clustered targets and often impairs binding to widely-spaced targets by sequestration" and that this "predicts when even weak dimerization can redistribute and stabilize proteins on DNA as a necessary part of transcription."
- **Evidence pointer** Abstract; Results; Discussion
- **Concern** The biological significance of the predicted effects is not fully developed. The authors do not discuss what the physiological consequences of enhanced selectivity for clustered targets might be, nor do they address whether the predicted impairments for widely-spaced targets have known biological correlates. The connection to transcription regulation is asserted but not elaborated.
- **Why it matters** For a Nature-style audience, the broader biological implications are crucial. Without a clear statement of what these predictions mean for gene regulation, development, or disease, the work risks being seen as purely theoretical.
- **Resolution test** Add a discussion section that explicitly connects the model predictions to known biological phenomena (e.g., how GAF clustering relates to gene expression, whether mutations affecting dimerization have known phenotypes) and propose testable experimental predictions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Model Description
- **Evidence pointer** Models and Theory, Model Description
- **Issue** The description of the three microenvironment models (DNA, DNA+targ, DNA+clusTarg) is brief, and the distinction between "DNA + targ" and "DNA + clusTarg" is not immediately clear from the text alone. The statement that in "DNA + targ" the sites are "not adjacent" and in "DNA + clusTarg" they are "clustered" needs a more precise definition of "adjacent" and "clustered" in terms of the model geometry.
- **Required correction** Provide a clear definition of the spatial arrangement of sites in each model, possibly with a schematic in the main text or a more detailed description in the SI.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Parameter values
- **Evidence pointer** Models and Theory; Results; Dataset S1 referenced
- **Issue** The main text does not provide a table of the parameter values used for the simulations and analytical calculations. While Dataset S1 is mentioned, the main text should include at least the key parameter ranges to allow readers to understand the scope of the results.
- **Required correction** Add a table in the main text or SI listing all parameters, their definitions, and the values or ranges used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of "trials" of binding and the analogy to neural networks is interesting but somewhat speculative and not clearly connected to the model results. The statement that "stoichiometry then provides further nonlinear tunability" is not directly supported by the results presented.
- **Required correction** Either remove or clearly mark speculative statements, or provide specific model results that support these claims.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Eq. (3)
- **Evidence pointer** Models and Theory, Two-state model
- **Issue** The expression for mean dwell time in Eq. (3) is presented without derivation or explanation of the notation. The term "stoichiometry" in the numerator is not defined, and the relationship to the two-state model is not immediately obvious.
- **Required correction** Provide a brief derivation or explanation of Eq. (3) in the main text or SI, and define all symbols.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure references
- **Evidence pointer** Throughout
- **Issue** Several figures are referenced (e.g., Figure 2d, Figure 3a, Figure 4e) but the main text does not describe what is shown in each panel. This makes it difficult to follow the results without constantly referring to the figures.
- **Required correction** Add brief descriptions of each figure panel in the text when first referenced.

## Risk / unsupported claims
- The claim that the model "explains" GAF ChIP-seq data is not quantitatively supported in the main text; the comparison is described only qualitatively.
- The statement that "dimensional reduction achieved through nonspecific binding and subsequent 1D diffusion controls the order-of-magnitude of enhancements despite nucleosome barriers" is presented as a result but the role of nucleosome barriers is not explicitly modeled or discussed in the main text.
- The claim that "even weak dimerization can redistribute and stabilize proteins on DNA as a necessary part of transcription" is a strong statement that goes beyond the model results, which are limited to equilibrium binding and do not include active processes or transcription itself.
- The assertion that the model "provides a way to improve interpretation of single-particle tracking measurements" is plausible but not demonstrated; no specific experimental data or analysis is shown.
- The statement that "allosteric effects could make assembly much more (or less) favorable in 1D vs 3D" is speculative and not supported by any data or analysis in the manuscript.