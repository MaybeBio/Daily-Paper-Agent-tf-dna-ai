## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, and supplementary declarations) as provided.
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by the presented evidence. No assessment of formatting, grammar, or editorial style beyond readability for nonspecialists.
- **Shared manuscript claim summary** The authors use multiscale simulations (coarse-grained Brownian dynamics and all-atom molecular dynamics) combined with mutational scanning and network-based community analysis to characterize stability, ACE2 binding, and epistatic interactions in Omicron BA.2, BA.2.75, XBB.1, and XBB.1.5 RBD-ACE2 complexes. They propose that R498 and Y501 act as epistatic hubs mediating compensatory effects, and that F486P in XBB.1.5 restores stability and binding affinity lost by F486S in XBB.1.
- **Visible evidence base** Methods descriptions for structural modeling, CG-BD and MD simulations, mutational scanning (BeAtMuSiC, SWOTein), and network analysis (RING, NetworkX, CFinder). Results sections with figures referenced (Figures 1-11) and tables (Tables 1-3, S1-S4). No raw data, trajectory files, or numerical outputs are provided in the text.
- **Missing materials affecting confidence** No quantitative results (e.g., ΔΔG values, RMSF numbers, community metrics) are reported in the text; all results are described qualitatively with reference to figures that are not included in the provided material. No statistical analysis or error estimates are presented. No comparison to experimental binding data beyond literature citations. No code or parameter files for reproducibility.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question: how Omicron subvariants balance stability, ACE2 binding, and immune escape through epistatic interactions. The methodological framework is ambitious and potentially valuable. However, the presented evidence is almost entirely qualitative, with no numerical data, statistical validation, or direct comparison to experimental measurements. The central claims about epistatic hubs and compensatory mechanisms rest on network metrics that are not quantitatively reported. As provided, the case is not established.
- **Who would be interested in the results, and why** Researchers studying SARS-CoV-2 evolution, viral entry mechanisms, and protein-protein interaction dynamics. Computational biophysicists interested in network-based approaches to allostery and epistasis. Structural biologists studying spike-ACE2 complexes. The topic has broad relevance to pandemic surveillance and variant forecasting.
- **Major strengths** The manuscript tackles a biologically important and current problem. The combination of multiple computational methods (CG-BD, MD, mutational scanning, network analysis) is comprehensive. The focus on epistatic effects and compensatory dynamics is conceptually novel and goes beyond simple binding affinity calculations. The discussion connects computational findings to experimental literature in a thoughtful manner.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no quantitative results), R1-M2 (no validation against experimental data), R1-M3 (network model assumptions unvalidated), R1-M4 (simulation convergence and sampling not demonstrated).
- **Assessment against Nature-style criteria** Originality: moderate to high; the network-based epistasis model is a novel angle. Scientific importance: high, given the public health relevance. Interdisciplinary readership: potentially broad, but the presentation is too specialized and lacks accessible summaries. Technical soundness: not assessable from the provided material due to absence of quantitative data. Readability for nonspecialists: poor; the text is dense and assumes deep familiarity with the methods.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if the technical concerns are resolved with quantitative data, validation, and clearer presentation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims to "systematically characterize conformational dynamics, protein stability and binding affinities" and to identify "epistatic effects modulating compensatory dynamic and energetic changes."
- **Evidence pointer** Results sections, Figures 1-11, Tables 1-3 (location not provided for numerical values)
- **Concern** No quantitative results are reported in the text. All findings are described qualitatively (e.g., "larger stability," "increased density," "appreciable destabilizing change"). No ΔΔG values, RMSF numbers, community sizes, or network metrics are given. The single numerical value mentioned, ΔΔG = 0.78 kcal/mol for P486S, appears to contain a typo ("kal/mol") and is not placed in context with error estimates or comparison to other variants.
- **Why it matters** Without quantitative data, the claims cannot be evaluated, reproduced, or compared to experimental measurements. The reader cannot assess the magnitude of effects or the significance of differences between variants.
- **Resolution test** Provide all key numerical results in tables or text, including mean values, standard deviations, and statistical tests where applicable. Report ΔΔG values for all mutations, RMSF profiles, community metrics, and network parameters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The manuscript states that results "are consistent with a broad range of functional studies" and that predictions "may explain the growth advantages" of XBB.1.5.
- **Evidence pointer** Results sections, Discussion (location not provided)
- **Concern** No direct quantitative comparison is made between computational predictions and experimental measurements. The manuscript cites experimental studies but does not show side-by-side comparisons of predicted vs. measured binding affinities, stabilities, or epistatic effects. The claim of consistency is asserted, not demonstrated.
- **Why it matters** Computational predictions without experimental validation are speculative. The manuscript's central claims about compensatory epistasis and the role of F486P require quantitative agreement with experimental data to be convincing.
- **Resolution test** Add a section comparing predicted ΔΔG values, stability changes, and epistatic interactions to published experimental data (e.g., DMS, SPR, thermal stability). Provide correlation coefficients or other quantitative agreement metrics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The manuscript proposes a "clique-based network model for the analysis of non-additive contributions" and claims that "3-clique community distributions" can identify epistatic effects.
- **Evidence pointer** Methods, Results (network analysis section), Figures 9-11 (location not provided)
- **Concern** The network model's assumptions are not justified. The manuscript asserts that co-membership in 3-cliques indicates epistasis, but no theoretical or empirical basis is provided for this equivalence. The choice of network construction parameters (e.g., correlation thresholds, edge weights) is not described in sufficient detail, and no sensitivity analysis is presented.
- **Why it matters** If the network model does not reliably capture epistatic interactions, the central conclusions about R498 and Y501 as epistatic hubs are unfounded. The method must be validated against known epistatic pairs or benchmarked on systems with established epistasis.
- **Resolution test** Provide a detailed description of network construction and parameter choices. Validate the model by showing it recovers known epistatic interactions from experimental data or from a benchmark system. Perform sensitivity analysis on key parameters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims to use "multiscale molecular simulations" including 500 ns all-atom MD simulations to draw conclusions about stability and dynamics.
- **Evidence pointer** Methods (MD simulation section), Results (dynamics analysis) (location not provided)
- **Concern** No evidence of simulation convergence is provided. For protein-protein complexes of this size, 500 ns may be insufficient to sample relevant conformational states, especially for detecting subtle differences between closely related variants. No RMSD time series, block averaging, or replica analysis is shown. The number of independent simulations and the reproducibility of results across runs are not reported.
- **Why it matters** If simulations are not converged, the observed differences in dynamics and stability between variants may be artifacts of insufficient sampling. The conclusions about "progressive rigidification" and "compensatory dynamics" require demonstrated convergence.
- **Resolution test** Provide convergence metrics (e.g., RMSD vs. time, RMSF convergence plots, multiple independent runs with error bars). Justify the simulation length based on system size and the timescales of relevant motions. Consider longer simulations or enhanced sampling methods if convergence is not achieved.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction (location not provided)
- **Issue** The abstract and introduction are dense and use jargon without definition (e.g., "epistatic effects," "allosteric modulation," "fitness trade-offs"). Nonspecialist readers will struggle to understand the core message.
- **Required correction** Add brief definitions or plain-language explanations of key terms. Consider a schematic figure summarizing the workflow and main findings.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods (location not provided)
- **Issue** The methods section lacks specific parameters for several key steps. For example, the CG-BD simulation parameters (e.g., friction coefficients, time steps) are not fully specified, and the network construction thresholds (e.g., correlation cutoff for edge inclusion) are not given.
- **Required correction** Provide complete parameter lists for all simulations and analyses. Include software versions and any custom scripts or settings.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results, Discussion
- **Evidence pointer** Results (mutational scanning section), Discussion (location not provided)
- **Issue** The manuscript states that "most mutations being largely neutral for binding" but also claims that "the improved RBD stability in BA.2.75 and XBB.1.5 may be an important driving force." The relationship between neutrality of individual mutations and overall stability improvement is not clearly explained.
- **Required correction** Clarify how individual neutral mutations collectively contribute to the observed stability and binding differences. Provide a mechanistic explanation or additional analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Figures 1-11 (location not provided)
- **Issue** The figures are referenced but not included in the provided material. Based on the text, it is unclear whether the figures contain quantitative data or are purely illustrative.
- **Required correction** Ensure all figures include clear labels, error bars where applicable, and captions that explain the key findings. Consider adding a figure with quantitative comparisons between variants.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion (location not provided)
- **Issue** The manuscript cites many studies but does not clearly differentiate between established experimental facts and computational predictions. Some statements in the Discussion appear to overstate the certainty of the computational findings.
- **Required correction** Use cautious language when describing computational predictions and clearly distinguish them from experimentally established results.

## Risk / unsupported claims
- The claim that R498 and Y501 act as "epistatic hubs" is unsupported without quantitative network analysis results and validation against experimental epistasis data.
- The claim that F486P in XBB.1.5 "restores both the stability and binding affinity" is not quantitatively demonstrated; no ΔΔG values or experimental comparisons are provided.
- The claim of "progressive rigidification" of the RBD in BA.2.75 and XBB.1.5 is based on qualitative RMSF descriptions without numerical data or statistical significance testing.
- The assertion that the network model can "identify highly inter-dependent mutational sites" is unvalidated and lacks a clear theoretical basis.
- The statement that results "are consistent with a broad range of functional studies" is an assertion without direct quantitative comparison.
- The proposed mechanism of "compensatory dynamics and energetic changes" is speculative and not supported by direct evidence of causality.