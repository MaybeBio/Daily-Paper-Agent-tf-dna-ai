## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract, without access to the full manuscript, figures, tables, or methods
- **Shared manuscript claim summary** The authors use molecular dynamics simulations to compare the interactions of highly positively charged substitution-inert platinum polynuclear complexes (SI-PPCs) with DNA and heparin. They report that electrostatic and hydrogen bonding interactions dominate, that both biomolecules respond similarly in terms of RMS deviation, solvent accessible surface area, RMS fluctuation, and interaction analysis, and that the observed structural changes suggest condensation and reduced surface area that may inhibit protein recognition and biological mechanisms related to apoptosis (DNA) or vascularization (heparin). Thermodynamic analyses are stated to support favourable interaction energies. The authors conclude that the results confirm an intrinsic dual-nature function of this chemotype and underline the importance of glycosaminoglycan (GAG)-small molecule interactions in drug pharmacology.
- **Visible evidence base** Abstract text only. No methods, simulation parameters, force fields, system setup, convergence criteria, error estimates, or quantitative results are provided.
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation methodology, force field parameters, system construction details, statistical analyses, convergence assessments, and any comparison with experimental data. Without these, the quantitative and mechanistic claims cannot be independently evaluated.

## Reviewer

- **Overall assessment** The abstract presents a plausible and potentially interesting computational study on the dual interactions of SI-PPCs with DNA and heparin. The topic is relevant to the fields of bioinorganic chemistry and drug design, particularly for platinum-based anticancer agents. However, the abstract alone provides insufficient detail to assess the technical soundness of the simulations, the robustness of the conclusions, or the novelty relative to prior work. Several claims are stated without quantitative support, and the mechanistic interpretation extends beyond what can be inferred from the limited information provided. The work may be of interest to specialists in computational chemistry and platinum drug development, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in bioinorganic chemistry, computational drug design, and platinum-based anticancer therapy would be interested. The comparison between DNA and heparin interactions addresses a growing interest in off-target glycosaminoglycan binding and its pharmacological consequences. The study could also appeal to those studying polyamine analogues and polynuclear platinum complexes as therapeutic agents.
- **Major strengths** The abstract addresses a relevant and underexplored question, namely the dual DNA and heparin binding behaviour of a single chemotype. The use of multiple complementary analyses (RMS deviation, solvent accessible surface area, RMS fluctuation, interaction analysis, thermodynamics) suggests a systematic approach. The framing around the extracellular versus intracellular balance of binding is conceptually useful and could inform future experimental work.
- **Major Concerns** The concerns below are based solely on the abstract. Without the full manuscript, several issues cannot be resolved.
- **Minor Comments** The comments below are based solely on the abstract. Without the full manuscript, several issues cannot be resolved.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5. The abstract does not provide sufficient methodological or quantitative detail to establish the technical validity of the simulations or the strength of the conclusions.
- **Assessment against Nature-style criteria** Originality: The concept of comparing DNA and heparin interactions for SI-PPCs is not entirely new, but the specific focus on this chemotype and the dual-nature framing may offer a fresh angle. However, the abstract does not clearly state what is novel relative to prior computational studies of platinum complexes with biomolecules. Scientific importance: The potential pharmacological relevance of GAG binding is real, but the abstract does not provide evidence that the findings have broad implications beyond the specific system studied. Interdisciplinary readership: The topic bridges chemistry, biology, and pharmacology, but the abstract is written in a way that assumes familiarity with simulation metrics and platinum chemistry, which may limit accessibility. Technical soundness: Cannot be assessed from the abstract. No simulation details, validation, or error analysis are provided. Readability for nonspecialists: The abstract is dense and uses field-specific terminology without sufficient context. The logical flow from methods to conclusions is not fully transparent.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that RMS deviation, solvent accessible surface area, RMS fluctuation, and interaction analysis confirm similar effects on both biomolecules, dictated predominantly by the total positive charge and total number of hydrogen bonds formed.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract provides no quantitative data, no statistical measures, and no description of how these analyses were performed or compared. It is unclear whether the similarity between DNA and heparin responses is based on absolute values, normalized values, or qualitative inspection. The claim that effects are "dictated predominantly" by charge and hydrogen bonding is an attribution of causality that cannot be supported without controlled variation of these parameters.
- **Why it matters** The central conclusion of the paper rests on this comparative claim. Without quantitative support and a clear analytical framework, the reader cannot judge whether the similarity is meaningful or an artefact of the simulation setup.
- **Resolution test** Provide quantitative values for each metric for both biomolecules, with error bars or standard deviations, and a statistical test or clear criterion for similarity. Demonstrate causality by showing that variations in charge or hydrogen bonding capacity lead to corresponding changes in the observed metrics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that changes in structural parameters suggest condensation and reduction of available surface area, which will reduce or prevent normal protein recognition and may thus potentially inhibit biological mechanisms related to apoptosis (DNA) or reduced vascularization viability (HEP).
- **Evidence pointer** Abstract, location not provided
- **Concern** The link between simulated structural changes and biological outcomes such as apoptosis inhibition or reduced vascularization viability is speculative. The abstract does not provide any experimental validation, nor does it explain the mechanistic pathway from reduced surface area to inhibition of protein recognition to specific biological effects. The use of "may thus potentially" indicates uncertainty, but the biological significance is presented as a likely consequence without supporting evidence.
- **Why it matters** This claim extends the computational findings to biological relevance, which is a key motivation for the study. If this link is not justified, the broader significance of the work is weakened.
- **Resolution test** Provide a clear mechanistic argument, supported by literature or additional simulations, that connects the observed structural changes to specific protein binding events and downstream biological effects. Alternatively, present experimental data that corroborates the predicted biological consequences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that thermodynamic analyses supported these findings with favourable interaction energies.
- **Evidence pointer** Abstract, location not provided
- **Concern** No thermodynamic quantities are reported. It is unclear what was calculated (binding free energy, enthalpy, entropy, interaction energy), by which method (MM-PBSA, MM-GBSA, free energy perturbation, etc.), and with what level of precision or convergence. "Favourable" is a qualitative term that does not convey the magnitude or reliability of the results.
- **Why it matters** Thermodynamic support is cited as a key piece of evidence. Without specific values and methodological details, this claim cannot be evaluated or reproduced.
- **Resolution test** Report the calculated thermodynamic quantities with units, standard errors, and the method used. Include a convergence assessment and, if possible, a comparison with experimental binding affinities.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the comparison of DNA and heparin confirms the general intersectionality between the two biomolecules and confirms the intrinsic dual-nature function of this chemotype.
- **Evidence pointer** Abstract, location not provided
- **Concern** The term "confirms" is too strong given the evidence presented. The abstract describes a computational comparison of two systems, but "intersectionality" and "dual-nature function" are broad conceptual claims that require more than a single simulation study to establish. The abstract does not define what is meant by these terms in a testable way.
- **Why it matters** Overstatement of conclusions can mislead readers and overstate the significance of the findings. The conceptual framing is interesting but should be presented as a hypothesis or interpretation, not a confirmed fact.
- **Resolution test** Rephrase the claim to reflect the level of evidence, such as "suggests" or "is consistent with." Provide a clear definition of "intersectionality" and "dual-nature function" and specify what evidence would be needed to confirm these concepts.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The entire study is based on molecular dynamics simulations, but no methodological details are provided.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not mention the force field, water model, simulation length, temperature, pressure, salt concentration, system size, or any validation of the simulation protocol. Without these details, the results cannot be reproduced or assessed for reliability.
- **Why it matters** Reproducibility is a core requirement for computational studies. The absence of methodological information prevents any meaningful evaluation of the technical soundness of the work.
- **Resolution test** Provide full methodological details in the manuscript, including all simulation parameters, software versions, and validation steps. If the abstract is the only document under review, these details must be made available for assessment.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "SI-PPCs" is used without definition in the abstract. While the full manuscript may define it, the abstract should be self-contained for readers encountering the term for the first time.
- **Required correction** Spell out "substitution-inert platinum polynuclear complexes" at first mention in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "two-limiting mode of actions" is awkward and unclear. It is not obvious what "two-limiting" means in this context.
- **Required correction** Rephrase to something like "the two proposed modes of action" or "the distinction between the two modes of action."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract structure
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract moves from methods to results to interpretation in a compressed manner, making it difficult to follow the logical progression. The sentence about "changes in structural parameters suggesting condensation" is particularly dense.
- **Required correction** Consider restructuring the abstract to clearly separate methods, results, and interpretation, and break long sentences into shorter, clearer statements.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract content
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not state the specific SI-PPC complexes studied, the number of systems simulated, or the length of the simulations. This information would help the reader gauge the scope of the study.
- **Required correction** Add a brief statement specifying the complexes studied and the simulation timescale.

## Risk / unsupported claims

- The claim that structural changes "will reduce or prevent normal protein recognition" and "may thus potentially inhibit biological mechanisms related to apoptosis (DNA) or reduced vascularization viability (HEP)" is unsupported by the abstract. No experimental or literature-based evidence is provided to substantiate this biological extrapolation.
- The claim that the results "confirm the general intersectionality between the two biomolecules" is unsupported. The abstract provides no definition of "intersectionality" and no comparative framework that would allow such a confirmation.
- The claim that thermodynamic analyses "supported these findings" is unverifiable because no thermodynamic data or methods are reported.
- The claim that effects are "dictated predominantly by the total positive charge and total number of hydrogen bonds formed" is an unsupported causal attribution without controlled variation or quantitative correlation analysis.
- The overall conclusion that the study "contributes to that understanding" of GAG-small molecule interactions is reasonable as a general statement, but the specific mechanistic and biological claims in the abstract are not established from the supplied material.