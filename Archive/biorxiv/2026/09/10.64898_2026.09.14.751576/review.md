## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, acknowledgments) as provided. Figures, tables, and supplementary materials referenced but not included.
- **Assessment boundary** Scientific content, methodological soundness, and claims as presented in the provided text. No assessment of formatting, grammar, or editorial style beyond readability for nonspecialists.
- **Shared manuscript claim summary** The authors present a new coarse-grained (CG) model of DNA parameterized for the Martini 3 force field, developed via Bayesian optimization against all-atom (AA) reference simulations. They claim the model captures key structural and mechanical properties of single- and double-stranded DNA across varying lengths and ionic conditions, and demonstrate compatibility with proteins, lipids, nanomaterials, and DNA nanostructures.
- **Visible evidence base** Text descriptions of methods and results, including quantitative values for persistence length, helical repeat, and Wasserstein loss scores. No actual figures, tables, or supplementary data were provided for inspection.
- **Missing materials affecting confidence** All figures (Figures 1-7, S1-S5), tables (Tables 1, S1-S3), and supplementary information. These are essential for evaluating the validity of the parameterization, the quality of the structural comparisons, and the robustness of the application simulations.

## Reviewer
- **Overall assessment** The manuscript addresses a clear and timely gap in the Martini 3 ecosystem by providing a DNA model compatible with the broader force field. The Bayesian optimization approach is methodologically sound and well described. However, the evidence base provided is insufficient to fully assess the validity of the model and the strength of the claims. The reported quantitative results are promising but incomplete, and several claims regarding transferability and accuracy require closer scrutiny. The manuscript is potentially suitable for publication in a high-impact venue, but substantial additional evidence and clarification are needed.
- **Who would be interested in the results, and why** Researchers in computational biophysics, molecular simulation, and DNA nanotechnology. The model would be of direct use to those studying DNA interactions with proteins, lipids, and nanomaterials within the Martini 3 framework. The Bayesian optimization workflow may also interest method developers in the coarse-graining community.
- **Major strengths** 1. The model addresses a well-defined need in the Martini 3 community, as no standard DNA model currently exists. 2. The Bayesian optimization approach is a modern and rigorous method for parameterizing CG models against AA references. 3. The validation across multiple application systems (protein, lipid, nanomaterial, nanostructure) is a strong demonstration of transferability. 4. The authors are transparent about limitations, including the fixed elastic network and salt-dependent behavior.
- **Major Concerns** 1. The persistence length results show no clear salt dependence and the value at 500 mM is above the expected experimental range, yet the authors state the model "captures" mechanical properties. This claim is not fully supported by the reported data. 2. The ssDNA radius of gyration is more compact than experimental measurements, which is acknowledged but not fully addressed. The implications for the model's utility in ssDNA applications are unclear. 3. The application simulations are described only qualitatively. Without quantitative metrics (e.g., binding free energies, contact maps, density profiles), the claim of "stable" interactions is difficult to evaluate. 4. The comparison with Martini 2 is limited to a single overall loss score. A more detailed comparison of specific structural properties would strengthen the claim of improvement.
- **Minor Comments** 1. The description of the Bayesian optimization workflow lacks some technical details, such as the choice of prior distributions and the convergence criteria for the optimization. 2. The manuscript would benefit from a clearer statement of the limitations of the fixed elastic network, particularly regarding the inability to model hybridization or melting. 3. The use of "heterogeneous" in the title and throughout is somewhat broad; the demonstrated systems are heterogeneous but limited in scope.
- **Technical failings that need to be addressed before the case is established** 1. The lack of quantitative data for the application simulations (protein binding, membrane insertion, graphene adsorption, nanostructure stability) prevents a rigorous assessment of the model's performance in these contexts. 2. The persistence length results, particularly the lack of salt dependence and the high value at 500 mM, need to be reconciled with experimental expectations or explicitly discussed as a limitation. 3. The comparison with Martini 2 should be expanded beyond a single aggregate score to demonstrate specific improvements.
- **Assessment against Nature-style criteria** Originality: High. The work fills a clear gap in the Martini 3 framework and introduces a novel application of Bayesian optimization to DNA CG model development. Scientific importance: High. A Martini 3 DNA model would enable a wide range of simulations in heterogeneous systems, with potential impact in biophysics, nanotechnology, and materials science. Interdisciplinary readership: Moderate to high. The work is relevant to computational biologists, soft matter physicists, and nanotechnologists, though the technical nature of the methods may limit accessibility. Technical soundness: Moderate. The optimization approach is sound, but the evidence provided is insufficient to fully validate the model's performance. Readability for nonspecialists: Moderate. The manuscript is generally well written, but the methods section assumes familiarity with CG modeling and Bayesian optimization.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea and approach are strong, but the evidence base must be expanded and the identified issues addressed before the claims can be fully supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The model "captures key structural and mechanical properties of single- and double-stranded DNA across varying lengths and ionic conditions."
- **Evidence pointer** Results section, "Validation of DNA Model" subsection; location not provided
- **Concern** The persistence length results show no clear salt-dependent trend, and the value at 500 mM (78.8 ± 16.8 nm) is substantially above the expected experimental range of approximately 45-50 nm. The authors acknowledge this but still claim the model captures mechanical properties. The lack of salt dependence and the deviation at high salt concentration suggest the model may not accurately represent ionic effects on DNA mechanics.
- **Why it matters** The claim of capturing mechanical properties across ionic conditions is central to the model's utility. If the model does not reproduce salt-dependent behavior, its applicability to physiological and experimental conditions is limited.
- **Resolution test** Provide a more detailed analysis of persistence length as a function of salt concentration, including comparisons with experimental data and a discussion of the expected trend. If the model cannot reproduce salt dependence, this should be explicitly stated as a limitation and the claim should be revised accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The application simulations demonstrate "stable protein binding, cholesterol-mediated membrane association, spontaneous ssDNA adsorption to graphene, and preservation of the crossover-containing nanostructure."
- **Evidence pointer** Results section, "Applications in Multicomponent Systems" subsection; location not provided
- **Concern** The application simulations are described only qualitatively. No quantitative metrics are provided, such as binding free energies, contact probabilities, density profiles, or RMSD values for the nanostructure. The claim of "stable" interactions is therefore not rigorously supported.
- **Why it matters** The transferability of the model to heterogeneous systems is a key selling point. Without quantitative evidence, it is impossible to assess whether the model performs adequately in these contexts or whether the observed behavior is an artifact of the simulation setup.
- **Resolution test** Provide quantitative analyses for each application system, such as binding free energies or contact maps for the protein-DNA complex, density profiles for the membrane system, adsorption energies or contact angles for the graphene system, and RMSD or structural stability metrics for the nanostructure.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The Bayesian optimization workflow "progressively identified parameter sets with improved AA-CG agreement."
- **Evidence pointer** Results section, "Parameter Optimization" subsection; location not provided
- **Concern** The description of the optimization workflow lacks details on the convergence criteria and the sensitivity of the results to the choice of acquisition function and mutation strategy. The authors state that no lower W_tot was identified after batch 11, but it is unclear whether this indicates convergence or a limitation of the optimization strategy.
- **Why it matters** The robustness of the optimization procedure is important for the reproducibility and generalizability of the approach. If the optimization is not well characterized, it is difficult to assess whether the final parameter set is truly optimal or merely a local minimum.
- **Resolution test** Provide additional details on the optimization procedure, including convergence diagnostics, sensitivity analyses, and a discussion of the choice of acquisition function and mutation strategy.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, "Bayesian Optimization of Backbone Parameters" subsection
- **Evidence pointer** Location not provided
- **Issue** The description of the acquisition function is incomplete. The text mentions a "stochastic mean-uncertainty acquisition function" but does not provide the full equation or a clear explanation of how the stochasticity is implemented.
- **Required correction** Provide the full equation for the acquisition function and a brief explanation of the stochastic element.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, "Validation of DNA Model" subsection
- **Evidence pointer** Location not provided
- **Issue** The comparison with Martini 2 is limited to a single aggregate W_tot score. A more detailed comparison of individual structural properties would be more informative.
- **Required correction** Provide a per-observable comparison of W_s values between Martini 3 and Martini 2, or a figure showing the distributions of key structural properties for both models.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion section
- **Evidence pointer** Location not provided
- **Issue** The discussion of the model's limitations is brief and does not fully address the implications of the fixed elastic network for the model's applicability to dynamic processes.
- **Required correction** Expand the discussion of the fixed elastic network, including a more detailed explanation of why it prevents modeling of hybridization or melting and what future work could address this.

## Risk / unsupported claims
- The claim that the model "captures key structural and mechanical properties" is not fully supported by the reported persistence length data, which show no clear salt dependence and a value at 500 mM above the expected range.
- The claim of "stable" interactions in the application simulations is unsupported by quantitative evidence, as only qualitative descriptions are provided.
- The claim that the model is "transferable" to heterogeneous systems is based on a limited set of four application systems, each simulated for 500 ns. Longer timescales and more diverse systems would be needed to fully establish transferability.
- The comparison with experimental ssDNA radius of gyration data is acknowledged as showing more compact conformations, but the implications for the model's utility in ssDNA applications are not discussed in detail.