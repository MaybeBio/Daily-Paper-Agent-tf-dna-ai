## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors present LIPAC, a computational framework applying hierarchical Bayesian causal inference to molecular dynamics simulations, and claim it distinguishes causal from correlational lipid-protein relationships, with application to EphA2-GM3 and Notch-GM3 systems demonstrating sensitivity and specificity
- **Visible evidence base** Abstract text only; no numerical results, statistical outputs, or methodological details are available
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, simulation parameters, model specification, validation procedures, and code availability

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable methodological contribution to the analysis of molecular dynamics trajectories, addressing a genuine limitation of conventional correlation-based approaches. The conceptual framing is clear and the two-stage design is sensible. However, the evidence provided in the abstract is insufficient to evaluate the technical soundness of the causal inference framework, the validity of the claims regarding sensitivity and specificity, or the robustness of the biological conclusions. The central claim that LIPAC establishes causal relationships is not assessable from the supplied material without details on model specification, identifiability, and validation against ground truth.
- **Who would be interested in the results, and why** Computational biophysicists and method developers working on MD simulation analysis would be the primary audience, as the framework addresses a recognized gap in extracting mechanistic insight from trajectories. Researchers studying lipid-protein interactions, particularly membrane receptor signaling and lipid raft biology, would also be interested if the biological claims hold. Statisticians working on causal inference in complex physical systems may find the hierarchical Bayesian approach of interest.
- **Major strengths** The abstract identifies a real and important limitation in MD analysis, namely the inability of conventional methods to distinguish causation from correlation. The proposed two-stage design, separating between-system detection from within-system quantification, is conceptually sound and addresses a practical need. The application to two receptor systems with contrasting results suggests an attempt to demonstrate both sensitivity and specificity, which is commendable. The emphasis on uncertainty quantification at both individual and population levels is appropriate for the hierarchical nature of the data.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient information to assess whether the causal inference framework is technically valid. Specifically, the model specification, identifiability conditions, prior choices, and validation strategy are not described. Without these, the claim that LIPAC quantifies causal relationships cannot be evaluated.
- **Assessment against Nature-style criteria** Originality: the concept of applying hierarchical Bayesian causal inference to MD trajectories appears novel, though the abstract does not situate it against existing causal analysis methods in the field. Scientific importance: the potential to extract mechanistic insight from MD simulations is significant, but the importance is not yet established from the abstract alone. Interdisciplinary readership: the work bridges computational biology, statistics, and membrane biophysics, which could attract a broad audience if the methods are accessible. Technical soundness: not assessable from the abstract; critical details are missing. Readability for nonspecialists: the abstract is well written and accessible, with clear terminology and a logical flow from problem to solution to application.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual contribution is promising, but the technical validity of the causal inference framework and the robustness of the biological claims cannot be assessed from the abstract alone. A supportive posture would require the full manuscript to demonstrate model identifiability, validation against known ground truth, and sensitivity analyses.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** LIPAC quantifies causal, rather than merely correlational, relationships between lipid binding and membrane organization
- **Evidence pointer** Abstract, methods not provided
- **Concern** The abstract claims that LIPAC establishes causal relationships, but no information is provided about the causal inference model, its assumptions, identifiability conditions, or how confounding variables are addressed. Causal inference from observational MD trajectories is nontrivial and requires explicit modeling of the data-generating process, temporal ordering, and potential unobserved confounders. Without this information, the causal claim is unsupported.
- **Why it matters** The central contribution of the work is the distinction between causal and correlational relationships. If the causal inference framework is not rigorously specified and validated, the entire premise of the paper collapses. Readers cannot evaluate whether the method is sound or whether the biological conclusions are justified.
- **Resolution test** The full manuscript must provide a complete specification of the hierarchical Bayesian model, including likelihood, priors, and latent variable structure. The authors must demonstrate identifiability of the causal parameters, describe how confounding is handled, and provide validation against simulated data with known causal structure.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** LIPAC correctly distinguished strong, reproducible effects (EphA2) from weak, inconsistent effects (Notch), demonstrating both sensitivity and specificity
- **Evidence pointer** Abstract, no figures or tables provided
- **Concern** The claim of sensitivity and specificity is made without presenting any quantitative results. No effect sizes, credible intervals, or statistical comparisons are shown. The statement that EphA2 shows "consistent DIPC depletion with narrow credible intervals" and Notch shows "wide credible intervals, inconsistent directionality" is descriptive but not supported by any numerical evidence in the abstract.
- **Why it matters** The demonstration of sensitivity and specificity is a key selling point of the framework. Without quantitative results, readers cannot assess whether the distinction between the two systems is statistically meaningful or whether the conclusions are robust. The claim of correct distinction requires evidence that the method does not produce false positives or false negatives.
- **Resolution test** The full manuscript must present effect size estimates with credible intervals for both systems, ideally in forest plots or equivalent visualizations. The authors should also report the number of simulation replicates, the consistency of results across replicates, and any formal statistical comparisons between the two systems.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological conclusion validity
- **Claim pointer** For EphA2, GM3 binding causally induces local enrichment of cholesterol and sphingomyelin while depleting unsaturated phosphatidylcholine, consistent with lipid-raft formation
- **Evidence pointer** Abstract, no supporting data provided
- **Concern** The biological conclusion about lipid raft formation is presented as a definitive finding, but the abstract provides no quantitative support. The claim that GM3 binding "causally induces" specific lipid changes requires evidence that the effect is specific to GM3 binding and not an artifact of the simulation setup, the force field, or the analysis method. The connection to lipid raft formation is also an interpretation that requires careful justification.
- **Why it matters** If the biological conclusion is overstated or not robust to methodological choices, it could mislead researchers in the membrane biology community. The claim of causal induction is strong and requires correspondingly strong evidence.
- **Resolution test** The full manuscript must show the magnitude of the lipid enrichment and depletion effects, the uncertainty associated with these estimates, and sensitivity analyses demonstrating that the conclusions are robust to simulation parameters, force field choices, and analysis settings. The authors should also discuss alternative interpretations and justify the lipid raft interpretation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "causal" is used repeatedly but not defined in the context of MD simulations. Causal inference in physical systems can have different meanings depending on the framework (e.g., interventionist, mechanistic, or counterfactual).
- **Required correction** Provide a brief definition or operationalization of causality as used in this work, ideally in the introduction or methods section.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not mention whether the LIPAC framework is publicly available or whether simulation data and analysis scripts are deposited.
- **Required correction** Include a data and code availability statement in the full manuscript, and mention it in the abstract if space permits.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Scope of application
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract presents LIPAC as a general framework but only demonstrates it on two receptor-membrane systems. It is unclear whether the method scales to larger systems, longer timescales, or different types of lipid-protein interactions.
- **Required correction** Add a discussion of the method's computational cost, scalability, and potential limitations for other applications.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Comparison with existing methods
- **Affected element** Benchmarking
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not compare LIPAC with existing causal or advanced correlation analysis methods for MD trajectories, such as mutual information, transfer entropy, or dynamic network analysis.
- **Required correction** Include a benchmarking section in the full manuscript comparing LIPAC with at least one or two established methods on the same datasets.

## Risk / unsupported claims
- The claim that LIPAC "quantifies causal relationships" is unsupported without model specification and validation details
- The claim of "sensitivity and specificity" is unsupported without quantitative results
- The biological conclusion regarding lipid raft formation is unsupported without effect size estimates and sensitivity analyses
- The claim that the framework is "general" is not assessable from a two-system demonstration
- The statement that conventional methods "cannot distinguish causal relationships from correlations" is presented as fact without citation or discussion of existing causal analysis approaches in the field