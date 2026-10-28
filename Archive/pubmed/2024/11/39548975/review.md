## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use multiscale simulations to characterize the monomeric and dimeric conformational landscapes of full-length TDP-43, identifying state-independent and dimerization-modulated features, with the C-terminal domain emerging as a key structure-dictating element. They report validation of simulated observables by complementary spectroscopy.
- **Visible evidence base** Abstract text only; no methodological details, quantitative results, or experimental data are provided
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, convergence criteria, spectroscopic validation details, and all figures/tables

## Reviewer
- **Overall assessment** The abstract presents a broad qualitative description of a computationally intensive study on a biologically important target. The topic is timely and the multiscale approach is appropriate in principle. However, the abstract lacks quantitative detail, specific methodological transparency, and a clear articulation of how the spectroscopic validation was performed. The claims are numerous and sweeping, but the evidence base visible here is insufficient to assess their robustness. The work may be of interest to the neurodegeneration and protein aggregation communities, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying TDP-43 biology, protein aggregation mechanisms in amyotrophic lateral sclerosis and frontotemporal dementia, and computational biophysicists interested in intrinsically disordered proteins and multiscale simulation approaches. The proposed transition between dimeric and monomeric states is directly relevant to therapeutic strategy development.
- **Major strengths** The study addresses a significant knowledge gap regarding full-length TDP-43 structure. The multiscale simulation approach is well suited to explore conformational landscapes. The explicit comparison between state-independent and dimerization-modulated features provides a useful conceptual framework. The attempt to validate computational predictions with spectroscopy is commendable.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is moderate to high, as full-length TDP-43 conformational detail is lacking. Scientific importance is high given the disease relevance. Interdisciplinary readership is plausible, spanning computational chemistry, biophysics, and neuroscience. Technical soundness cannot be evaluated from the abstract alone, as no methodological specifics are provided. Readability for nonspecialists is acceptable, though the abstract is dense with qualitative descriptors that lack quantitative anchoring.
- **Recommendation posture** Currently not established from the provided evidence. The abstract promises substantial findings, but the visible material does not permit verification of the core claims. A full manuscript review would be required to assess whether the technical concerns are resolvable.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that a multiscale simulation approach "unearths numerous crucial features" of the TDP-43 conformational landscape, including specific structural determinants such as beta-sheet propensity and hydrogen bonding patterns.
- **Evidence pointer** Abstract, methods not described; location not provided
- **Concern** The abstract provides no information on the simulation methods used, including force fields, sampling algorithms, simulation lengths, system construction, or convergence criteria. Without this information, the reliability of the predicted conformational features cannot be assessed. Multiscale approaches vary widely in their accuracy for disordered proteins, and the choice of methods critically affects the validity of the reported landscape features.
- **Why it matters** The central claims of the paper rest entirely on the quality and appropriateness of the simulations. If the methods are not described or are inadequate, the entire set of structural predictions is called into question. The absence of any methodological detail in the abstract is particularly problematic for a computational study.
- **Resolution test** The full manuscript must provide a detailed methods section with force field parameters, simulation protocols, validation of sampling convergence, and justification for the multiscale approach. The authors should demonstrate that the observed features are robust across independent simulations or alternative methods.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that "validation of our simulated observables by a complementary spectroscopic approach on multiple counts ensures the robustness of the computationally predicted features."
- **Evidence pointer** Abstract, validation described only in general terms; location not provided
- **Concern** The abstract states that spectroscopic validation was performed but provides no details on which spectroscopic technique was used, which observables were compared, how the comparison was quantified, or the level of agreement achieved. The phrase "on multiple counts" is vague and does not allow the reader to judge the strength of the validation.
- **Why it matters** Validation is the key evidence that the simulations are physically meaningful. Without specifics, the claim of robustness is unsupported. If the validation is weak or indirect, the computational predictions remain unverified.
- **Resolution test** The full manuscript must describe the spectroscopic experiments, the specific simulated observables that were compared, the quantitative agreement between experiment and simulation, and any limitations of the comparison.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim that the C-terminal domain "appears as the most crucial structure-dictating domain" and that it "preferably populates a compact conformation with a high beta-sheet propensity in its isolated state stabilized by intrabackbone hydrogen bonds."
- **Evidence pointer** Abstract, no quantitative data provided; location not provided
- **Concern** The abstract presents this as a central finding, but no quantitative measures are given, such as radius of gyration values, beta-sheet content percentages, or hydrogen bond occupancies. The comparison between the isolated and integrated forms of the C-terminal domain is described only qualitatively ("comparatively faded"), without numerical support.
- **Why it matters** The prominence of the C-terminal domain is a key conclusion with potential therapeutic implications. Without quantitative evidence, the claim is not verifiable and could be an artifact of the simulation setup or analysis choices.
- **Resolution test** The full manuscript must provide quantitative comparisons of conformational properties between the isolated and integrated C-terminal domain, with appropriate statistical analysis and error estimates.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors describe a "multiscale simulation approach" and report "slower collapsing dynamics" and "restricted polymorphic landscape" for the dimer, among other dynamic features.
- **Evidence pointer** Abstract, no kinetic or dynamic data provided; location not provided
- **Concern** The abstract reports dynamic properties such as collapsing dynamics and landscape restrictions, but no timescales, rates, or free energy estimates are given. The term "multiscale" implies multiple levels of resolution, but the abstract does not explain how these scales were integrated or which properties were computed at which scale.
- **Why it matters** Dynamic claims require appropriate sampling and analysis to be meaningful. Without quantitative dynamic data or a description of how the multiscale approach was implemented, the reported features cannot be reproduced or evaluated by other researchers.
- **Resolution test** The full manuscript must provide detailed descriptions of the multiscale methodology, including how different resolution levels were coupled, and quantitative dynamic observables with appropriate uncertainty estimates.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract structure
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract is a single dense paragraph that mixes state-independent and dimerization-modulated features without clear sub-structuring, making it difficult for readers to follow the logical organization of the findings.
- **Required correction** Consider restructuring the abstract with explicit subheadings or clearer transitions between the two categories of features.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Multiscale simulation approach"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "multiscale" is used without specifying which scales are involved (e.g., atomistic, coarse-grained, mesoscopic) or how they are connected. This is a significant omission for a computational methods paper.
- **Required correction** Specify the resolution levels used and the coupling scheme in the abstract or clearly indicate that full details are in the methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Precision
- **Affected element** "High beta-sheet propensity"
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "high beta-sheet propensity" is used without a quantitative threshold or comparison to a reference state. It is unclear what constitutes "high" in this context.
- **Required correction** Provide a quantitative definition or comparison, such as beta-sheet content relative to known disordered proteins or a specific secondary structure prediction score.

## Risk / unsupported claims
- The claim that the C-terminal domain is "the most crucial structure-dictating domain" is unsupported without quantitative comparisons across all domains.
- The claim that validation "ensures the robustness" of predictions is unsupported given the lack of detail on the validation method and agreement level.
- All dynamic claims (slower collapsing, restricted landscape) are unsupported without quantitative kinetic or thermodynamic data.
- The claim of a "rugged polymorphic landscape" is not verifiable without free energy or conformational sampling metrics.
- The relative importance of hydrophobic versus hydrophilic residues in interfaces is stated without quantitative interface analysis data.