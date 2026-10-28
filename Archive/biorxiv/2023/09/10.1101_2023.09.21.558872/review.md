## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without figures or supplementary materials
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive logic as presented in the text; figure content assessed only through textual descriptions
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics simulations of a bacterial chromosome model with homodimeric transcription factors to show that residence time distributions of TFs on DNA follow multi-exponential patterns even when a single or binary affinity model is used. They attribute this emergent behavior to the formation of protein-DNA clusters of various sizes, where larger clusters have longer dissipation lifetimes. They further show that distributed affinity models with discrete levels do not produce power-law behavior, suggesting that additional complexity is needed to explain experimentally observed power-law residence time distributions.
- **Visible evidence base** Textual descriptions of Figures 1-6 and Figure S1, methods section, and discussion; no actual figure panels, numerical values, or statistical outputs are visible
- **Missing materials affecting confidence** All figures and supplementary figures; quantitative fitting parameters; statistical test outputs; simulation parameter tables; cluster analysis numerical results; code outputs

## Reviewer
- **Overall assessment** The manuscript addresses an important question in transcription factor dynamics, namely the mechanistic origin of non-exponential residence time distributions. The central claim, that protein-DNA cluster formation can generate multi-exponential residence time patterns even with simple affinity models, is plausible and potentially significant. However, the evidence as presented in the text is insufficient to fully evaluate the strength of this claim. The manuscript would benefit from clearer presentation of quantitative results, more rigorous statistical comparisons, and a more direct connection between cluster properties and the observed residence time distributions.
- **Who would be interested in the results, and why** Researchers studying transcription factor kinetics, single-molecule tracking of DNA-binding proteins, gene regulation mechanisms, and coarse-grained simulations of chromosome organization would find these results relevant. The work bridges a gap between structural observations of protein-DNA clustering and kinetic measurements of TF residence times, which is of interest to both experimental and computational groups in these areas.
- **Major strengths** The manuscript addresses a timely and important discrepancy between simple bi-exponential models and observed power-law residence time distributions. The use of a coarse-grained model that captures both specific and nonspecific interactions is appropriate. The systematic variation of affinity and concentration parameters is a reasonable approach. The connection between cluster size and dissipation lifetimes provides a mechanistic hypothesis that is testable in principle.
- **Major Concerns** The major concerns are detailed below. The most significant issues are the lack of quantitative evidence visible in the text, the unclear causal logic connecting cluster formation to multi-exponential residence time distributions, and the insufficient treatment of alternative explanations.
- **Minor Comments** The minor comments are detailed below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate to high, as the cluster-mediated explanation for multi-exponential residence times is a novel contribution. Scientific importance is potentially high given the widespread interest in TF dynamics and gene regulation. Interdisciplinary readership is plausible, spanning biophysics, molecular biology, and computational biology. Technical soundness cannot be fully assessed from the text alone, but the methodological approach is reasonable. Readability for nonspecialists is adequate, though some sections assume familiarity with polymer physics and simulation methods.
- **Recommendation posture** Supportive if technical concerns are resolved, but currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "residence time distributions of dimeric proteins follow a multi-exponential pattern even when a single interaction describes the affinity between DNA and protein."
- **Evidence pointer** Figure 2, Figure S1, "location not provided"
- **Concern** The claim that residence time distributions are multi-exponential is central to the manuscript, but the text provides no quantitative information about the fitting procedure, the number of exponentials required, the goodness of fit, or the statistical comparison between models with different numbers of exponentials. The text states that "the increase from single to double as well as from double to triple exponential decay resulted in the order of magnitudes lower RSS," but no RSS values are reported. Without these quantitative details, the reader cannot assess whether the multi-exponential description is genuinely superior or whether the improvement is marginal.
- **Why it matters** The entire premise of the manuscript rests on the demonstration that residence time distributions are multi-exponential rather than bi-exponential. If the evidence for this is not clearly presented, the subsequent analysis of cluster formation as the cause loses its foundation.
- **Resolution test** Provide the RSS values for fits with 1, 2, 3, 4, and 5 exponentials for representative conditions, along with the number of parameters and a model selection criterion such as AIC or BIC. Show representative fits overlaid on the residence time distributions in the main text.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that "cluster formations drive multi-exponential residence time patterns" and that "concentration and affinity-dependent cluster formations could be the driving factors of the observed multi-exponential patterns."
- **Evidence pointer** Figures 3, 4, 5, "location not provided"
- **Concern** The text establishes correlations between cluster size and dissipation lifetimes, and between TF position within clusters and residence times, but the causal direction is not clearly established. It is possible that the multi-exponential residence time distributions arise from other sources of heterogeneity in the system, such as local DNA conformational variability, stochastic fluctuations in TF binding geometry, or finite-size effects of the simulation box. The authors do not present control simulations or perturbation analyses that would isolate cluster formation as the causal factor.
- **Why it matters** The manuscript proposes a mechanistic explanation for a biological observation. If the causal link is not established, the conclusion is weakened and alternative explanations remain viable.
- **Resolution test** Perform simulations where cluster formation is suppressed (e.g., by reducing TF-TF interactions or altering the binding site spacing) and show that the multi-exponential behavior is correspondingly reduced. Alternatively, show that the number of exponentials required to fit the residence time distributions correlates with the distribution of cluster sizes across conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The authors claim that "larger clusters had longer mean lifetimes" based on correlation analysis with "a coefficient of r ≥ 0.5."
- **Evidence pointer** Figure 4, "location not provided"
- **Concern** The correlation coefficient threshold of r ≥ 0.5 is reported, but no p-values, confidence intervals, or sample sizes are provided. A correlation of 0.5 can be statistically significant or not depending on the number of clusters analyzed. Additionally, the text does not specify whether the correlation is computed across all clusters within a single simulation or across multiple simulation conditions. The relationship between cluster size and lifetime may be confounded by other variables such as cluster density or local protein concentration.
- **Why it matters** The correlation between cluster size and dissipation lifetime is a key piece of evidence supporting the cluster-driven mechanism. Without proper statistical reporting, the strength of this evidence cannot be evaluated.
- **Resolution test** Report the number of clusters analyzed, the correlation coefficient with confidence intervals, and p-values for each condition. Consider partial correlations that control for potential confounders.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Alternative explanations
- **Claim pointer** The authors state that "the power-law interpretation of residence times distributions in experimental studies might well be due to such biases introduced by corrections rather than the actual underlying TF residence behavior."
- **Evidence pointer** Discussion, "location not provided"
- **Concern** This is a strong claim that challenges the interpretation of experimental single-molecule tracking data. However, the manuscript does not provide a detailed analysis of how experimental correction procedures could produce apparent power-law behavior from underlying multi-exponential distributions. The claim is speculative and not supported by any simulation or analytical demonstration within the manuscript.
- **Why it matters** If the authors wish to challenge the power-law interpretation of experimental data, they need to provide a concrete demonstration that plausible experimental artifacts can transform multi-exponential distributions into apparent power laws. Without this, the claim remains unsupported speculation.
- **Resolution test** Simulate the effect of typical experimental correction procedures (e.g., localization error, motion blur, finite observation window) on known multi-exponential distributions and show that these can produce apparent power-law behavior. Alternatively, temper the claim to a more modest suggestion that experimental artifacts may contribute to observed power-law behavior.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Retrieving the residence durations and generating the distributions"
- **Evidence pointer** Methods section, "location not provided"
- **Issue** The description of how residence times are extracted from the simulations is brief. It is unclear how the "uninterrupted bound state" is defined precisely, particularly regarding the threshold for what constitutes a binding event versus a transient contact.
- **Required correction** Provide a more detailed description of the binding detection criteria, including the distance threshold and the minimum duration for a binding event to be counted.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "Residence time behaviors are multi-factorial"
- **Evidence pointer** Figure 1, "location not provided"
- **Concern** The text mentions that "the projection of RT patterns in the log-log scale exhibited an apparent arching pattern, eliminating the possibility of a good power-law fit," but no quantitative measure of the deviation from a power law is provided.
- **Required correction** Report the goodness of fit for a power-law model compared to multi-exponential models, or provide a statistical test that quantifies the deviation from power-law behavior.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, paragraph on gene expression noise
- **Evidence pointer** Discussion, "location not provided"
- **Issue** The connection between multi-exponential residence time distributions and gene expression noise is speculative and not developed in detail. The authors mention transcriptional bursts and cellular heterogeneity but do not provide a quantitative link between their simulation results and these biological phenomena.
- **Required correction** Either develop this connection more explicitly with quantitative arguments or clearly label it as speculation beyond the scope of the current study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Fitting equations to the residence time distributions"
- **Evidence pointer** Methods section, "location not provided"
- **Issue** The fitting procedure is described, but the initial parameter guesses, fitting bounds, and convergence criteria are not specified. This makes it difficult to reproduce the fits.
- **Required correction** Provide the full fitting details, including the optimization algorithm, initial conditions, and any constraints on the fit parameters.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results, "Distributed affinity models do not lead to power-law behavior"
- **Evidence pointer** Figure 6, "location not provided"
- **Concern** The text states that distributed affinity models "did not produce power-law behavior" and that "triple-exponential fit, an example of multi-exponential fit, better described the behaviors," but the comparison between the distributed affinity model results and the single/binary affinity model results is not clearly presented.
- **Required correction** Clarify whether the distributed affinity models produce qualitatively different residence time distributions compared to the single and binary affinity models, and if so, how.

## Risk / unsupported claims
- The claim that experimental power-law residence time distributions may be due to correction biases is unsupported by any demonstration within the manuscript.
- The claim that cluster formation is the driving factor of multi-exponential residence time patterns is supported only by correlational evidence, not causal evidence.
- The claim that "larger clusters had longer mean lifetimes" is not quantitatively supported in the text due to missing statistical details.
- The claim that distributed affinity models do not produce power-law behavior is stated but not quantitatively supported with fit statistics or comparisons.
- The biological implications regarding gene expression noise and transcriptional bursts are speculative and not directly supported by the simulation results.