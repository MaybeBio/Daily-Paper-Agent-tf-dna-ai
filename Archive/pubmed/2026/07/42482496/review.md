## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose a discrete-state stochastic model to study how transcription factor (TF) dimerization affects target search on DNA. They claim that dimerization alters effective association, dissociation, and sliding dynamics, leading to regime-dependent acceleration of target localization, and suggest that tuning protein-protein interactions may regulate genetic information transfer.
- **Visible evidence base** Abstract text only; no methodological details, equations, simulation parameters, or quantitative results are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, supplementary material, model derivation, simulation protocols, parameter values, and any comparison with experimental data

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting theoretical question regarding the role of protein-protein interactions in transcription factor target search. However, the provided material is insufficient to evaluate the technical soundness, the validity of the claims, or the significance of the findings. The abstract lacks quantitative details, model specifications, and any comparison with experimental observations, making it impossible to assess whether the conclusions are supported by the evidence.
- **Who would be interested in the results, and why** Researchers in biophysics, computational biology, and gene regulation would be interested in this work if the full manuscript provides a rigorous theoretical framework and testable predictions. The topic connects to broader questions of how molecular interactions shape gene expression kinetics, which is relevant to both fundamental biology and potential therapeutic applications.
- **Major strengths** The question addressed is timely and relevant, given recent experimental evidence of TF oligomerization and phase separation. The use of analytical calculations combined with kinetic Monte Carlo simulations is a standard and appropriate approach for this type of problem. The abstract clearly identifies parameter regimes where dimerization accelerates target search, which suggests the authors have explored the parameter space systematically.
- **Major Concerns**  
  - **Concern ID** R1-M1  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Technical soundness  
    **Claim pointer** The claim that dimerization alters effective association, dissociation, and sliding dynamics, leading to substantial changes in target search kinetics, is presented without any quantitative support.  
    **Evidence pointer** Abstract, location not provided  
    **Concern** The abstract states that analytical calculations and simulations demonstrate these effects, but no specific results, parameter values, or model details are given. Without seeing the model equations, the definitions of effective rates, or the simulation protocols, it is impossible to verify that the conclusions follow from the methods.  
    **Why it matters** The core scientific claim depends entirely on the correctness and appropriateness of the model and the simulations. If the model is oversimplified or the simulations are not properly validated, the conclusions may not hold.  
    **Resolution test** Provide the full model derivation, explicit definitions of all effective rates, simulation details, and a demonstration that the results are robust to parameter choices and model assumptions.  
  - **Concern ID** R1-M2  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Scientific importance  
    **Claim pointer** The claim that tuning protein-protein interactions of TFs might be an efficient tool for the regulation of genetic information transfer is presented as a general conclusion.  
    **Evidence pointer** Abstract, location not provided  
    **Concern** The abstract does not provide any quantitative measure of the acceleration effect, nor does it specify the biological relevance of the parameter regimes where acceleration occurs. Without knowing the magnitude of the effect or whether the relevant parameters are biologically plausible, the significance of the finding cannot be assessed.  
    **Why it matters** The broader claim about regulation of genetic information transfer requires that the predicted effects are large enough and occur in biologically accessible parameter ranges. If the acceleration is marginal or requires unrealistic parameter values, the claim is overstated.  
    **Resolution test** Provide quantitative results showing the magnitude of acceleration in biologically relevant parameter regimes, and discuss how these parameters compare with known experimental values.  
  - **Concern ID** R1-M3  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Interdisciplinary readership  
    **Claim pointer** The abstract claims that the findings are discussed in light of recent experimental observations.  
    **Evidence pointer** Abstract, location not provided  
    **Concern** No specific experimental observations are mentioned, and no comparison with experimental data is presented in the abstract. The claim that the theoretical findings explain experimental observations cannot be evaluated without knowing which observations are referenced and how the model relates to them.  
    **Why it matters** For a broad readership, the connection to experiments is crucial for establishing the relevance of the theoretical work. Without this connection, the work remains abstract and its impact is unclear.  
    **Resolution test** Clearly identify the experimental observations being referenced, and provide a detailed comparison between model predictions and experimental data in the full manuscript.  
- **Minor Comments**  
  - **Concern ID** R1-m1  
    **Severity** Minor  
    **Axis** Readability for nonspecialists  
    **Affected element** Abstract  
    **Evidence pointer** Abstract, location not provided  
    **Issue** The abstract uses terms such as "discrete-state stochastic model" and "effective association, dissociation, and sliding dynamics" without defining them for a general audience.  
    **Required correction** Provide brief definitions or intuitive explanations of these terms in the abstract to make the work accessible to a broader readership.  
  - **Concern ID** R1-m2  
    **Severity** Minor  
    **Axis** Technical soundness  
    **Affected element** Abstract  
    **Evidence pointer** Abstract, location not provided  
    **Issue** The abstract does not specify the number of TFs considered in the model or the dimensionality of the search space, which are important for understanding the scope of the results.  
    **Required correction** Include a brief statement about the model setup, such as the number of TFs and the nature of the DNA lattice, in the abstract or the full manuscript.  
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The abstract alone does not provide sufficient evidence to establish the core claims. The full manuscript must be reviewed to assess the model, simulations, and comparison with experiments.

## Risk / unsupported claims
- The claim that dimerization accelerates target search in specific parameter regimes is unsupported without quantitative results.
- The claim that the findings explain recent experimental observations is unsupported without specifying which observations are referenced.
- The claim that tuning protein-protein interactions can regulate genetic information transfer is speculative without evidence of biological relevance or magnitude of effect.
- All quantitative aspects of the model and simulations are unassessable from the provided material.