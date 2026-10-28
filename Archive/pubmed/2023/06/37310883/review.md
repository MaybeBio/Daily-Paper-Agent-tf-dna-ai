## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose an analytical framework, based on a discrete-state stochastic model, to study how nucleosome breathing and sliding dynamics affect the target search time of transcription factors on DNA. Using experimentally determined kinetic rates as inputs, they compute first-passage times separately for breathing and sliding, report substantial mechanistic differences between the two modes, identify molecular factors influencing search efficiency, and validate their analytical results with Monte Carlo simulations.
- **Visible evidence base** Abstract text only; no equations, parameter values, simulation details, or quantitative results are visible
- **Missing materials affecting confidence** Full manuscript, model derivation, parameter tables, simulation protocols, all figures and tables, and any quantitative comparisons between theory and simulation

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting question, namely how nucleosome dynamics modulate transcription factor target search, and proposes a tractable stochastic modeling approach. The distinction between breathing and sliding dynamics as separate regulatory mechanisms is a potentially valuable contribution. However, the abstract provides no quantitative results, no model specification, and no validation details, making it impossible to assess the technical soundness or the strength of the central claims. The work may be of interest to biophysicists and computational biologists, but the evidence base is too thin to establish the case.
- **Who would be interested in the results, and why** Biophysicists and computational biologists studying protein-DNA interactions, gene regulation, and stochastic search processes would be interested. The work also speaks to experimentalists investigating nucleosome dynamics, as it offers a theoretical framework to interpret kinetic data. The claim that breathing and sliding produce distinct search mechanisms could inform future experimental designs.
- **Major strengths** The question is timely and biologically relevant, given the prevalence of nucleosomes in eukaryotic genomes. The use of experimentally determined kinetic rates as model inputs is a strength, as it grounds the theory in measurable quantities. The separate treatment of breathing and sliding dynamics is a clear conceptual advance over models that treat nucleosomes as static barriers. The stated validation via Monte Carlo simulations is appropriate for this type of model.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not report any quantitative outcomes, such as search time values, scaling relationships, or comparison metrics between theory and simulation. Without these, the central claim of substantial differences between breathing and sliding cannot be evaluated. The model structure is not described, so the assumptions underlying the discrete-state stochastic description are unknown. The validation claim is unverifiable without simulation details or error metrics.
- **Assessment against Nature-style criteria** Originality is moderate, as stochastic models of protein search are established, but the explicit comparison of breathing versus sliding dynamics is a novel angle. Scientific importance is potentially high for the gene regulation community, but the abstract does not demonstrate broad significance beyond a specific modeling exercise. Interdisciplinary readership is plausible, but the abstract is written for a specialist audience and does not frame the findings for nonspecialists. Technical soundness cannot be assessed from the abstract alone. Readability for nonspecialists is limited, as key terms and the modeling approach are not explained in accessible language.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a promising framework, but the absence of quantitative results and model details prevents a supportive recommendation. A full manuscript with derivations, parameter values, and simulation comparisons would be required to assess the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their analytical framework estimates target search time via first-passage probability calculations separately for nucleosome breathing and sliding dynamics.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe the model equations, the state space, the transition rates, or the boundary conditions used in the first-passage calculations. Without this information, the analytical framework cannot be evaluated for correctness or applicability.
- **Why it matters** The core contribution is the analytical model. If the model is not specified, reviewers and readers cannot verify the derivation, reproduce the results, or assess whether the assumptions are biologically reasonable.
- **Resolution test** Provide the full model derivation in the manuscript, including the master equations, the definition of states, the rate constants, and the method for solving the first-passage problem. Show that the model reduces to known limits where applicable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that their results suggest substantial differences between the protein search mechanism on a nucleosome performing breathing versus sliding dynamics.
- **Evidence pointer** Abstract, location not provided
- **Concern** No quantitative results are presented to support this claim. The abstract does not report search times, differences in scaling, or any metric that would demonstrate the magnitude or nature of the differences.
- **Why it matters** The claim of substantial differences is the central scientific finding. Without quantitative support, the claim is unsupported and cannot be evaluated for significance or robustness.
- **Resolution test** Report specific search time values or distributions for both breathing and sliding cases, with appropriate error bars or confidence intervals. Show that the differences are statistically significant and biologically meaningful.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors claim that their analytical results are validated using extensive Monte Carlo simulations.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract provides no details on the simulation protocol, the number of runs, the parameter ranges tested, or the agreement metrics between theory and simulation. The term extensive is not quantified.
- **Why it matters** Validation is essential to establish that the analytical approximations are accurate. Without details, the validation claim is unverifiable and the reliability of the model is unknown.
- **Resolution test** Describe the simulation algorithm, the parameter sets used, the number of independent runs, and the quantitative agreement between analytical and simulation results, such as relative errors or correlation coefficients.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term nucleosome dynamics is used broadly, but the abstract only specifies breathing and sliding. It is unclear whether other dynamic modes, such as unwrapping or histone exchange, are considered or excluded.
- **Required correction** Define the scope of nucleosome dynamics explicitly and state which modes are included in the model.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract structure
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract moves from a general biological motivation to a specific modeling claim without a clear statement of the model inputs or outputs. Nonspecialist readers may struggle to follow the logic.
- **Required correction** Add a sentence that explicitly states the model inputs, the key output, and the main finding in plain terms.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Molecular factors
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that molecular factors influencing search efficiency are identified, but none are named. This claim is vague and unverifiable.
- **Required correction** List the specific molecular factors in the abstract or indicate that they are detailed in the full manuscript.

## Risk / unsupported claims
- The claim of substantial differences between breathing and sliding dynamics is unsupported, as no quantitative results are provided.
- The claim of validation via Monte Carlo simulations is unverifiable, as no simulation details or agreement metrics are given.
- The claim that molecular factors influencing search efficiency are identified is unverifiable, as no factors are named.
- The general statement that the framework portrays a highly dynamic landscape of gene regulation is speculative and not supported by specific evidence in the abstract.