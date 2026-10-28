## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, methods, figures, and supplementary figure legend.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality. Not assessed: editorial fit, formatting, or grammatical style.
- **Shared manuscript claim summary** The authors present a comprehensive deep mutational scanning study of the JUN bZIP domain, measuring the effects of nearly all single amino acid substitutions on binding to 52 of 54 human bZIP transcription factors. They fit a global thermodynamic model to decompose mutational effects into global (affinity-changing) and specific (specificity-changing) components, identify determinants of interaction specificity, and propose a "zig-zag model" for the evolution of specificity and affinity in coiled-coil interactions.
- **Visible evidence base** Abstract, Introduction, Results (partial), Methods, Figure legends (Fig. 1-7, Fig. S1), Data availability, Code availability, Author contributions, Acknowledgements.
- **Missing materials affecting confidence** Full Results section text (only partial content provided), all main figures (Fig. 1-7) and their legends, supplementary tables (Table S1-S3), detailed statistical methods, and the complete Discussion section. The absence of these materials limits the ability to fully evaluate the robustness of the data analysis and the strength of the conclusions.

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in protein evolution and biophysics: how interaction specificity is encoded in a large protein family. The experimental approach is ambitious and technically impressive, generating a large-scale dataset of mutational effects on binding across an entire protein family. The authors' use of a global thermodynamic model to decompose affinity and specificity effects is conceptually sound and provides a framework for interpreting complex mutational data. The finding that specificity-altering mutations are rare, pleiotropic, and distributed throughout the interface is potentially important. However, the manuscript as presented has significant gaps in the Results section and lacks key figures and tables, making it impossible to fully assess the validity of the claims. The authors should be commended for the scale of the experiment, but the current presentation does not yet establish the case for the "zig-zag model" of specificity and affinity optimization.
- **Who would be interested in the results, and why** This work will be of interest to researchers in protein biophysics, molecular evolution, and systems biology. Specifically, those studying protein-protein interaction networks, the determinants of binding specificity, and the evolutionary constraints on protein interaction interfaces will find the dataset and the proposed model valuable. The methodological approach of combining deep mutational scanning with thermodynamic modeling may also be of interest to method developers in these fields.
- **Major strengths**
  1. The experimental design is comprehensive, covering nearly all possible single amino acid substitutions in a protein domain against an entire family of interaction partners.
  2. The use of a global thermodynamic model to separate affinity and specificity effects is a sophisticated and appropriate analytical approach.
  3. The identification of both positive and negative determinants of specificity, including dual-function residues, provides a nuanced view of how specificity is encoded.
  4. The proposed "zig-zag model" is an interesting conceptual contribution that may stimulate further research.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data completeness and presentation
  - **Claim pointer** The manuscript claims to provide "the first global view of how mutations in a protein affect binding to all its potential interaction partners" and to reveal "the distributed encoding of specificity and affinity in an interaction interface."
  - **Evidence pointer** Results section (partial), Figures 1-7 (not provided), Figure S1 (legend only)
  - **Concern** The Results section is incomplete, and the main figures (Fig. 1-7) are not provided. This makes it impossible to evaluate the quality of the data, the validity of the model fits, and the strength of the evidence for the claims. For example, the claim that "most affinity changing mutations equally affect JUN's propensity to bind to all its interaction partners" is central to the paper, but the supporting data (likely in Fig. 2) cannot be assessed. Similarly, the identification of specificity-determining residues (Fig. 6) and the structural analysis (Fig. 7) are key results that cannot be verified.
  - **Why it matters** The core conclusions of the paper rest on the data and analyses presented in the missing figures and results. Without these, the claims are unsupported and the scientific contribution cannot be evaluated.
  - **Resolution test** Provide the complete Results section and all main figures with legends. The figures should clearly show the distribution of mutational effects, the model fits, the identification of specificity-determining residues, and the structural context.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Model validation and interpretation
  - **Claim pointer** The authors state that "fitting a global thermodynamic model to the data reveals that most affinity changing mutations equally affect JUN's propensity to bind to all its interaction partners" and that the model "predicts binding scores with high accuracy (R² = 0.91)."
  - **Evidence pointer** Methods (Thermodynamic model), Figure 3 (not provided)
  - **Concern** The thermodynamic model is central to the analysis, but the validation and interpretation are not fully described. The authors mention that for some partners the model did not provide a good fit and required a multiplicative term (Hill coefficient), but the rationale and implications of this modification are not fully explained. The claim that the model captures "global" effects assumes that the additive ΔΔG is truly partner-independent, but the need for a multiplicative term suggests otherwise. The authors should clarify the physical interpretation of this term and how it affects the decomposition of global and specific effects.
  - **Why it matters** The validity of the decomposition into global and specific effects depends on the correctness of the model. If the model is misspecified, the conclusions about the rarity and nature of specificity-altering mutations could be incorrect.
  - **Resolution test** Provide a more detailed description of the model, including the derivation of the multiplicative term, its physical interpretation, and a sensitivity analysis showing how the conclusions change with different model assumptions. Show the model fits for a representative set of partners, including those that required the multiplicative term.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor
  - **Claim pointer** The authors identify 97 variant-bZIP combinations with "strong changes in specificity (absolute specific effect > 0.5, FDR < 5%)" and classify residues as positive, negative, or dual determinants of specificity.
  - **Evidence pointer** Results section (partial), Figure 6 (not provided)
  - **Concern** The criteria for identifying specificity-altering mutations and classifying determinants of specificity are not fully described. The threshold of 0.5 for the specific effect is arbitrary and its biological significance is unclear. The FDR correction is mentioned, but the details of the statistical testing (e.g., how the null distribution was estimated) are not provided. The classification of residues as positive, negative, or dual determinants appears to be based on the direction of effects of individual mutations, but the criteria for this classification are not explicit.
  - **Why it matters** The identification of specificity determinants is a key result of the paper. Without clear and rigorous statistical criteria, the classification of residues may be unreliable, and the conclusions about the distribution and nature of specificity determinants may not be robust.
  - **Resolution test** Provide a detailed description of the statistical methods used to identify specificity-altering mutations and classify determinants. Include a justification for the threshold used and a sensitivity analysis showing how the results change with different thresholds. Show the distribution of specific effects and the criteria for classification in a clear figure.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evolutionary interpretation
  - **Claim pointer** The authors propose a "zig-zag model" of specificity and affinity optimization, suggesting that "specificity can therefore be optimised during evolution using combinations of pleiotropic specificity and affinity altering mutations in the interface coupled to compensatory affinity tuning mutations elsewhere in the zipper."
  - **Evidence pointer** Discussion section
  - **Concern** The evolutionary model is presented as a conclusion, but it is largely speculative and not directly tested by the data. The authors do not provide evidence that the proposed evolutionary pathway is feasible or that it has occurred in natural populations. The model is plausible, but it is one of several possible explanations for the observed data.
  - **Why it matters** The "zig-zag model" is a potentially important conceptual contribution, but it is presented as a firm conclusion rather than a hypothesis. Overstating the implications of the data could mislead readers.
  - **Resolution test** Soften the language used to describe the model, presenting it as a hypothesis or a framework for future work. Provide a more balanced discussion of alternative explanations for the observed data.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of writing
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract is dense and uses technical jargon (e.g., "global thermodynamic model," "specificity-altering mutations") without sufficient context for a general reader.
  - **Required correction** Consider revising the abstract to make the key findings and their significance more accessible to a broad audience.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Code availability
  - **Evidence pointer** Code availability section
  - **Issue** The statement "All custom scripts will be provided upon requests" is vague and does not meet modern standards for reproducibility.
  - **Required correction** Provide a link to a public repository (e.g., GitHub) where the scripts are deposited, or provide them as supplementary files.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Results section
  - **Evidence pointer** Results section (partial)
  - **Issue** The term "global binding energy" is used to describe the partner-independent effect of a mutation, but this term could be confused with the absolute binding free energy of a complex. The term "general binding energy" or "intrinsic binding propensity" might be clearer.
  - **Required correction** Consider using a more precise term to describe the partner-independent effect of a mutation.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Figure quality
  - **Affected element** Figure S1
  - **Evidence pointer** Figure S1 legend
  - **Issue** The legend for Figure S1 is brief and does not fully explain the visualization. It is unclear what the "three characters in the mutant name" refer to and how the coloring scheme works.
  - **Required correction** Expand the figure legend to provide a clear explanation of the visualization, including the naming convention and color scheme.

## Risk / unsupported claims
- The claim that the data provide "the first global view of how mutations in a protein affect binding to all its potential interaction partners" is not fully supported, as the data cover 52 of 54 bZIPs and exclude two partners (CEBPG and CREB1) for technical reasons.
- The claim that "about half of the specificity-defining residues in JUN have dual functions" is based on a classification that is not fully described and may be sensitive to the statistical thresholds used.
- The "zig-zag model" of specificity and affinity optimization is presented as a conclusion but is not directly tested by the data and should be considered a hypothesis.
- The physical interpretation of the multiplicative term (Hill coefficient) in the thermodynamic model is described as "speculative" by the authors, yet it is used in the decomposition of global and specific effects. The robustness of the conclusions to this model choice is not assessed.