## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors combine all-atom molecular dynamics simulations with yeast-based transactivation assays to show that pathogenic mutations in the p53 tetramerization domain, particularly at residues 337 and 352, destabilize the tetramer and alter transactivation capacity and specificity, with mutant proteins better tolerating weak DNA binding sites.
- **Visible evidence base** Abstract text only; no methodological details, quantitative results, or statistical analyses provided
- **Missing materials affecting confidence** Full manuscript, simulation parameters and convergence criteria, experimental protocols, strain details, quantitative transactivation data, statistical analyses, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting hypothesis linking tetramerization domain stability to p53 transactivation specificity, supported by a dual computational and experimental approach. However, the abstract alone provides insufficient detail to evaluate the rigor of the simulations, the robustness of the functional assays, or the strength of the claimed causal relationship. The central claim that mutations alter transactivation specificity by better tolerating weak DNA binding sites is intriguing but not substantiated with quantitative evidence in the provided material.
- **Who would be interested in the results, and why** Cancer biologists and clinicians studying p53 mutations and their functional consequences, structural biologists interested in protein tetramerization dynamics, and computational biologists developing predictive models for mutation effects on protein stability and function. The R337H founder mutation is of particular relevance to populations in southern Brazil, so clinical genetics audiences may also find the work useful.
- **Major strengths** The combination of extended all-atom molecular dynamics with functional assays in a defined genetic system is a strong integrative approach. The inclusion of rationally designed mutations targeting a specific salt bridge provides a clear mechanistic hypothesis. The focus on transactivation specificity, rather than only overall activity, adds a nuanced dimension that is often overlooked.
- **Major Concerns** The abstract does not report any quantitative simulation outcomes, such as free energy differences, root-mean-square deviation trajectories, or convergence metrics, making it impossible to assess the reliability of the destabilization claim. The transactivation assay results are described qualitatively, with no effect sizes, replicate numbers, or statistical tests, so the claim of altered specificity is not verifiable from the provided material. The mechanistic link between tetramer destabilization and altered specificity for weak DNA binding sites is asserted but not explained mechanistically, leaving a gap in the logical chain.
- **Minor Comments** The abstract would benefit from stating the simulation timescale and number of replicas. The yeast-based system is mentioned as genetically defined, but the specific p53-null background or reporter constructs are not described. The phrase "better tolerating the negative features in weak DNA binding sites" is vague and should be defined operationally.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: moderate, as the salt bridge at residues 337 and 352 has been studied before, but the focus on transactivation specificity is a fresh angle. Scientific importance: potentially high given the clinical relevance of R337H, but the abstract does not yet demonstrate a definitive advance. Interdisciplinary readership: the work bridges structural biology, computational biophysics, and functional genomics, which could appeal to a broad audience if the evidence is robust. Technical soundness: cannot be assessed from the abstract alone, as no quantitative details are provided. Readability for nonspecialists: the abstract is generally clear, though terms like "transactivation specificity" and "weak DNA binding sites" could be explained more explicitly for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract outlines a promising study, but the absence of quantitative results and methodological detail prevents any assessment of whether the claims are supported. A full manuscript with rigorous data would be needed to evaluate the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Simulations revealed a destabilizing effect of pathogenic mutations within the p53 tetramerization domain"
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that simulations revealed destabilization but provides no quantitative metrics, such as free energy changes, structural deviations, or stability scores. No simulation timescale, force field, or convergence assessment is mentioned.
- **Why it matters** Without quantitative output and methodological context, the claim of destabilization is not verifiable. Molecular dynamics results are highly sensitive to simulation length and force field choice, and a qualitative statement of "destabilizing effect" is insufficient to support a mechanistic conclusion.
- **Resolution test** Provide specific stability metrics (e.g., free energy differences, contact maps, or RMSD trajectories) with error estimates, and demonstrate convergence through replicate simulations or block analysis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "p53 tetramerization mutations could decrease transactivation potential and alter transactivation specificity, in particular, by better tolerating the negative features in weak DNA binding sites"
- **Evidence pointer** Abstract, location not provided
- **Concern** The transactivation assay results are described only qualitatively. No data are shown for the magnitude of decrease in transactivation potential, the number of replicates, the statistical significance of specificity changes, or the definition of "weak DNA binding sites" and "negative features."
- **Why it matters** The claim of altered specificity is the most novel aspect of the work, but it requires quantitative demonstration that the effect is reproducible and statistically robust. Without such data, the claim could be based on a single experiment or a small effect that is not biologically meaningful.
- **Resolution test** Present transactivation data as quantitative values (e.g., reporter activity normalized to wild-type) with error bars and statistical tests, and define the criteria for classifying binding sites as weak or strong.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Logical coherence
- **Claim pointer** "These results establish the effect of naturally occurring variations at positions 337 and 352 on p53 conformational stability and function"
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not explain how tetramer destabilization mechanistically leads to altered transactivation specificity. The link between reduced tetramer stability and a preference for weak DNA binding sites is asserted but not rationalized.
- **Why it matters** Without a mechanistic explanation, the correlation between simulation and functional data could be coincidental. The claim of "establishing" an effect requires a coherent model that connects the structural and functional observations.
- **Resolution test** Provide a mechanistic model, supported by data, that explains how destabilized tetramers alter DNA binding specificity, for example through changes in cooperativity or DNA binding domain dynamics.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, methods description
- **Evidence pointer** Abstract, location not provided
- **Issue** The simulation timescale and number of replicas are not stated, which is standard information for molecular dynamics studies.
- **Required correction** Add the total simulation time per system and the number of independent replicates to the abstract or methods summary.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "better tolerating the negative features in weak DNA binding sites" is ambiguous and not operationally defined.
- **Required correction** Define what constitutes a "negative feature" and how tolerance is measured, or rephrase to describe the specific experimental observation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Abstract, experimental system
- **Evidence pointer** Abstract, location not provided
- **Issue** The yeast-based system is described as "genetically defined," but the specific genetic background and reporter constructs are not mentioned.
- **Required correction** Briefly state the yeast strain and reporter system used, or refer to a methods section where these details are provided.

## Risk / unsupported claims
- The claim that simulations revealed destabilization is unsupported without quantitative data.
- The claim that mutations alter transactivation specificity is unsupported without statistical evidence.
- The claim that the results "establish" an effect on conformational stability and function is overreaching given the qualitative nature of the reported findings.
- The mechanistic link between tetramer destabilization and altered specificity for weak DNA binding sites is not established.