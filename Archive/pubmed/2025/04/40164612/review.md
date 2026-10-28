## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific claims, methodology, data interpretation, and presentation quality
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics simulations to study phase separation of six transcription factor (TF) low-complexity domains (LCDs) from three families (FET, SP/KLF, HNF). They identify four "sticker motifs" and two "orthogonal molecular grammar" types (hydrophobic and cation-π/electrostatic) that drive selective phase separation, and propose this as a generic mechanism for transcriptional regulation.
- **Visible evidence base** Main text figures (Figs 1-9), supplementary figures and tables referenced but not fully visible, methods section
- **Missing materials affecting confidence** Supplementary figures and tables (referenced extensively but not provided in the submitted text), source data files, reporting summary

## Reviewer

- **Overall assessment** This manuscript presents a systematic computational study of TF LCD phase separation using a coarse-grained model. The work is technically competent and addresses an important question in transcriptional regulation. However, the central claim of "orthogonal molecular grammar" as a generic mechanism is only partially supported by the evidence presented. The study is largely descriptive, cataloging interaction types and resulting morphologies, but lacks predictive validation or experimental corroboration. The connection to biological function remains speculative.

- **Who would be interested in the results, and why** Researchers in the fields of phase separation, transcriptional regulation, and intrinsically disordered proteins would find this work relevant. The systematic mapping of interaction types to condensate morphologies could inform future experimental designs. The methodological developments to the 1BPA model may also interest computational biologists working on coarse-grained simulations of biomolecular condensates.

- **Major strengths**
  1. Systematic exploration of a relevant parameter space (three TF families, multiple binary and ternary combinations)
  2. Clear presentation of interaction types and their relative contributions
  3. The identification of four distinct condensate morphologies based on relative homotypic/heterotypic interaction strengths is conceptually useful
  4. The inclusion of POL II as a "promiscuous" interactor provides an interesting contrast to the selective TF interactions
  5. Methodological transparency in describing the simulation protocol and analysis tools

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "selective phase separation of transcription factors is driven by orthogonal molecular grammar" and that this represents "a generic molecular mechanism that drives selective transcriptional condensation in gene expression."
- **Evidence pointer** Abstract, Discussion, Figs 2, 6-8
- **Concern** The central claim of "orthogonal molecular grammar" as a generic mechanism is not sufficiently established. The study examines only six TFs from three families, which is a limited sample. The claim of "generality" requires either a broader survey of TF sequences or a clear demonstration that the identified interaction types are both necessary and sufficient to predict phase separation behavior. The current evidence is largely correlative, showing that certain interaction types are present in certain systems, but not demonstrating that these are the causal determinants of selectivity.
- **Why it matters** The title and abstract make a strong claim about a "generic molecular mechanism." If the evidence only supports a description of interaction patterns in a small set of systems, the claim is overstated. This affects the scientific impact and accuracy of the work.
- **Resolution test** The authors should either (a) expand the analysis to a larger, more diverse set of TF LCDs to demonstrate predictive power, (b) perform mutational or sequence-perturbation simulations that test the causal role of the identified interaction types, or (c) temper the claims to be specific to the systems studied rather than "generic."

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors state that "PS is observed across all compositions of the TFs and POLII studied" and that the identified morphologies (marbled, coated, bimodal, separated) are robust features of the systems.
- **Evidence pointer** Results, Figs 2, 6-8, Supplementary Figs 11-17
- **Concern** The simulations are performed with a coarse-grained model (1BPA-2.1) that has been reparameterized, but no direct validation of the model's predictions for these specific TF systems is provided. The authors reference previous work on nucleoporins, but the transferability to TF LCDs is not demonstrated. Experimental data on phase separation of these specific TFs (e.g., FUS, EWS, TAF15, SP1, SP2, HNF1A) exist in the literature, and a comparison with these data would strengthen the claims. Without such validation, the reader cannot assess whether the observed morphologies are artifacts of the model or genuine predictions.
- **Why it matters** The scientific value of the work depends on the reliability of the simulation predictions. If the model has not been validated for these systems, the conclusions about selectivity and morphology may not be trustworthy.
- **Resolution test** The authors should compare their simulation results (e.g., phase separation propensity, condensate morphology, interaction types) with available experimental data on these TFs. If discrepancies exist, they should be discussed and explained. Alternatively, the authors could perform additional simulations with a different model (e.g., all-atom or a different coarse-grained approach) to confirm the robustness of their findings.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance
- **Claim pointer** The authors propose that "the local TF condensate environment formed in the nucleus plays a crucial role in orchestrating POL II localisation to the correct genes for transcription" and that their findings "provide a universal mechanistic basis for selective gene transcription."
- **Evidence pointer** Discussion, Fig 9
- **Concern** The connection between the simulation results and biological function is speculative. The simulations are performed in simplified conditions (no DNA, no chromatin, no other nuclear proteins, no post-translational modifications except for the POL II charge mutant). The extrapolation to in vivo transcriptional regulation requires many assumptions that are not discussed. For example, the concentrations used (80,000 μM total residue concentration) may not reflect physiological conditions in the nucleus. The role of DNA binding domains, which are excluded from the simulations, is acknowledged but not addressed.
- **Why it matters** The broader significance of the work for understanding transcriptional regulation depends on the biological relevance of the simulation conditions. If the conditions are not representative, the conclusions may not apply to real biological systems.
- **Resolution test** The authors should either (a) perform simulations under more physiologically relevant conditions (e.g., with DNA, at lower concentrations), (b) explicitly discuss the limitations of their simplified conditions and how they might affect the conclusions, or (c) soften the claims about biological relevance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative analysis
- **Claim pointer** The authors state that "the relative homotypic and heterotypic interaction strengths" determine the four condensate morphologies, and they provide a ranking of interaction types (cation-π > aliphatic > aromatic > aliphatic-aromatic/electrostatic).
- **Evidence pointer** Results, Figs 4-5, Supplementary Figs 3-8
- **Concern** The quantitative analysis of interaction strengths is not fully described. The authors mention "mean interaction propensity" and "fraction of interactions" but do not provide a clear statistical framework for comparing these quantities across systems. It is unclear whether the differences in interaction strengths between systems are statistically significant. The ranking of interaction types appears to be based on mean values, but the variability across systems and over time is not reported. This limits the reader's ability to assess the robustness of the conclusions.
- **Why it matters** The central mechanistic claim depends on the relative strengths of different interaction types. If these are not rigorously quantified, the conclusions may be based on noise rather than genuine differences.
- **Resolution test** The authors should provide error bars or confidence intervals for their interaction strength measurements, and perform statistical tests to support the ranking of interaction types. They should also report the variability across independent simulation runs.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig 1
- **Evidence pointer** Fig 1
- **Issue** The color scheme in Fig 1 is not colorblind-friendly. The authors use red for cations, blue for anions, green for aromatics, black for aliphatics, and white for hydrophilics. Red-green color blindness is common, and the distinction between red (cations) and green (aromatics) may be difficult for some readers.
- **Required correction** Consider using a colorblind-safe palette, or add patterns/textures to distinguish the residue types.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract, Introduction, Discussion
- **Issue** The term "orthogonal molecular grammar" is used repeatedly but is not clearly defined. The authors describe two "orthogonal driving forces" (hydrophobic and cation-π/electrostatic), but the term "grammar" implies a combinatorial system that is not fully explained. It is unclear what the "rules" of this grammar are and how they would be applied to predict behavior in new systems.
- **Required correction** Provide a clear definition of "molecular grammar" in this context, and explain how the identified interaction types constitute a "grammar" rather than simply a set of interaction preferences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The methods section describes the simulation protocol but lacks some details that would be needed for reproducibility. For example, the number of independent simulation runs, the criteria for determining convergence, and the specific parameters for the 1BPA-2.1 model are not fully specified. The authors refer to the ESI for details, but this is not accessible to the reader.
- **Required correction** Provide a more complete description of the simulation parameters and analysis methods in the main text, or ensure that the ESI is accessible and clearly referenced.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the POL II phosphorylation mutant (POLIIcharged) is brief. The authors state that the increase in negative charge leads to loss of phase separation, but do not discuss the implications of this finding in detail. For example, how does this relate to the known role of phosphorylation in regulating POL II function during transcription?
- **Required correction** Expand the discussion of the POL II phosphorylation results and their biological implications.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript does not adequately situate the work within the broader literature on TF phase separation. Several key experimental studies on TF condensates (e.g., on OCT4, GCN4, and other TFs) are not cited or discussed. The claim of novelty would be strengthened by a clearer comparison with existing work.
- **Required correction** Add a more comprehensive literature review and explicitly state how this work advances beyond previous studies.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The claim of "generic molecular mechanism" is not supported by the limited number of systems studied
  - R1-M2: Lack of validation of the coarse-grained model for the specific TF systems studied
  - R1-M3: The biological relevance of the simulation conditions is not established

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The application of coarse-grained simulations to study TF phase separation selectivity is not entirely new, but the systematic comparison of three TF families and the identification of four distinct morphologies provides some novelty.
  - **Scientific importance**: Moderate. The work addresses an important question (how TFs achieve selectivity in transcriptional regulation), but the conclusions are largely descriptive and lack predictive power or experimental validation.
  - **Interdisciplinary readership**: Moderate. The work will appeal to researchers in biophysics, computational biology, and gene regulation, but the technical nature of the simulations may limit broader appeal.
  - **Technical soundness**: The simulation methodology appears sound, but the lack of validation and incomplete quantitative analysis are concerns.
  - **Readability for nonspecialists**: The manuscript is generally well-written, but the heavy use of specialized terminology (e.g., "sticker-spacer model," "percolation") may be challenging for readers outside the field.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an interesting computational study, but the central claims of "orthogonal molecular grammar" as a generic mechanism and the biological relevance of the findings are not sufficiently supported. The authors should address the major concerns, particularly the need for validation and a more rigorous quantitative analysis, before the case is established.

## Risk / unsupported claims
- The claim that "orthogonal molecular grammar" is a "generic molecular mechanism" for selective transcriptional condensation is not supported by the limited number of systems studied (six TFs from three families).
- The claim that the identified interaction types are the causal determinants of phase separation selectivity is not established; the evidence is correlative.
- The extrapolation from simplified simulation conditions to in vivo transcriptional regulation is speculative and not adequately justified.
- The statement that "PS is observed across all compositions of the TFs and POLII studied" is presented without quantitative evidence of phase separation (e.g., critical concentrations, binodals).
- The claim that POL II "can interact with any TF to enable co-condensation" is based on simulations with only six TFs and may not generalize to all ~1600 human TFs.