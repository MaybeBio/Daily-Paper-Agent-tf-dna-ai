## Review setup

- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, author contributions, data availability, acknowledgements)
- **Assessment boundary** Theoretical modeling and fitting to previously published experimental data; no new experimental data are presented
- **Shared manuscript claim summary** The authors develop a kinetic extension of the Tonks-McGhee-von Hippel lattice model that incorporates ligand crowding and transitions between two SSB binding modes. They claim this model quantitatively reproduces experimental binding kinetics and coverage-dependent behaviors for HmtSSB and EcoSSB, including bimodal kinetics and the transient shortening observed upon SSB removal from solution.
- **Visible evidence base** Figures 1-4 (described in text), Table 1 and Table 3 (referenced), Methods section, Supplementary Information (referenced but not provided)
- **Missing materials affecting confidence** Supplementary Information (detailed derivations, fitting procedures, parameter values), experimental datasets from Refs. (Morin et al. 2017; Naufer et al. 2021) not included, figure files not viewable, Table 2 not referenced or provided

## Reviewer

- **Overall assessment** The manuscript presents a theoretically motivated kinetic model that extends the Tonks-McGhee-von Hippel framework to include mode transformations and crowding effects. The core idea, that ligand crowding on ssDNA can explain observed SSB binding kinetics including the counterintuitive shortening upon protein removal, is interesting and potentially valuable. However, the manuscript as provided has significant gaps in presentation: the Methods section is incomplete, the Supplementary Information containing essential derivations is not available, and the figures and tables are not viewable. The claims of quantitative reproduction of experimental data cannot be fully assessed without these materials. The conceptual framework is sound and the work addresses a genuine gap in understanding SSB binding kinetics, but the current evidence base is insufficient to establish the case.

- **Who would be interested in the results, and why** Researchers studying single-stranded DNA binding proteins, DNA replication and repair mechanisms, and biophysicists working on ligand-polymer binding kinetics. The generalizable framework for multimode ligand binding to polymers could also interest theorists working on lattice models of protein-DNA interactions and experimentalists using optical tweezers to study protein-nucleic acid interactions.

- **Major strengths** The manuscript addresses a real and important gap: the kinetic consequences of crowding on SSB binding mode transitions have not been systematically modeled. The extension of the TGH framework to include mode transformations is a natural and potentially powerful theoretical advance. The model successfully explains a counterintuitive experimental observation (further contraction upon SSB removal) through a mechanistically plausible crowding effect. The authors are appropriately cautious in their claims and acknowledge limitations regarding cooperativity, condensate formation, and non-nearest-neighbor interactions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model "quantitatively reproduces experimental binding kinetics and coverage-dependent behaviors observed for HmtSSB and EcoSSB"
- **Evidence pointer** Figures 2-4, Tables 1 and 3, Supplementary Information (location not provided)
- **Concern** The quantitative claims of reproduction of experimental data cannot be verified from the provided material. The figures are not viewable, the fitting procedures and parameter values are only partially described in the main text, and the Supplementary Information containing the detailed derivations and fitting methodology is not available. Without these materials, it is impossible to assess whether the fits are statistically adequate, whether the parameter values are physically reasonable, or whether the model has sufficient flexibility that good fits are guaranteed regardless of the underlying physics.
- **Why it matters** The central claim of the manuscript is that the model quantitatively reproduces experimental data. If this cannot be verified, the core contribution of the work is unsubstantiated. The distinction between a model that genuinely captures the relevant physics and one that merely has enough free parameters to fit the data is critical for the scientific value of the contribution.
- **Resolution test** Provide the Supplementary Information with full derivations, fitting procedures, parameter uncertainties, and goodness-of-fit statistics. Ensure figures are viewable with clear presentation of model predictions versus experimental data points, including error bars and residuals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The model explains the bimodal kinetics as "a fast binding in the EcoSSB 8 mode, simultaneous with a fast conversion to the EcoSSB 17 mode (wrapping)" followed by "a slow phase combining slow binding in the lower mode, EcoSSB8, and a slow conversion from the higher to the lower mode"
- **Evidence pointer** Figure 4, Table 3, Methods section (location not provided)
- **Concern** The kinetic equations are presented in the Methods section but the derivation is incomplete in the main text. The rate equations in Eq. (5) are stated but the derivation of the crowding corrections, particularly the probability factors p_alpha and the correction to K_alpha_to_beta, is relegated to the Supplementary Information. The model assumes a specific reaction scheme (binding in mode alpha followed by conversion to mode beta) but the justification for this scheme over alternatives is not provided. Additionally, the model uses only two modes for EcoSSB (8 and 17 nucleotides) while the experimental system is known to exhibit additional modes; the justification for neglecting these is not fully developed.
- **Why it matters** The kinetic scheme is the foundation of the model. If the derivation is not transparent or the scheme is not adequately justified, the explanatory power attributed to crowding effects may be an artifact of the chosen framework rather than a robust conclusion.
- **Resolution test** Present the full derivation of the kinetic equations in the main text or ensure the Supplementary Information is available. Justify the two-mode approximation for EcoSSB with reference to the experimental conditions. Provide sensitivity analysis showing that the qualitative conclusions do not depend on the specific reaction scheme chosen.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "These results imply that the observed binding kinetics is compatible with crowding-induced inhibition of binding and mode transformation"
- **Evidence pointer** Discussion section, Figures 3-4 (location not provided)
- **Concern** The manuscript demonstrates that the crowding model can reproduce the experimental data, but the claim of compatibility is weaker than a claim of uniqueness. The authors do not systematically compare their model against alternative explanations for the observed kinetics, such as conformational changes in the SSB protein itself, ssDNA structural rearrangements, or cooperative effects. Without such comparison, the conclusion that crowding is the operative mechanism is not strongly established.
- **Why it matters** The scientific importance of the work depends on whether crowding is genuinely the dominant mechanism or merely one of several possible explanations. If alternative models can equally well reproduce the data, the contribution is more limited in scope.
- **Resolution test** Discuss alternative mechanistic explanations and explain why the crowding model is preferred. If possible, design discriminating predictions that could distinguish the crowding model from alternatives.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** The model is presented as "a generalizable framework for studying multimode ligand binding to polymers"
- **Evidence pointer** Discussion section (location not provided)
- **Concern** The generalizability claim is made but not demonstrated. The manuscript applies the model to two specific systems (HmtSSB and EcoSSB) but does not show how the framework would be adapted to other multimode ligand systems, what new predictions it makes beyond the specific systems studied, or what experimental designs would test the framework in other contexts.
- **Why it matters** The broader impact of the work depends on its applicability beyond the specific systems studied. Without a clear articulation of the generalizable aspects and how they would be applied, the claim of generalizability is not substantiated.
- **Resolution test** Add a section or paragraph explicitly discussing how the framework would be applied to other systems, what parameters would need to be measured, and what qualitative predictions the model makes that could be tested in other contexts.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction and Methods
- **Evidence pointer** Introduction, Methods section (location not provided)
- **Issue** The manuscript assumes familiarity with the Tonks-McGhee-von Hippel framework and lattice models without providing sufficient background for readers who are not specialists in this area. The biological motivation is clear, but the theoretical framework is introduced abruptly.
- **Required correction** Add a brief conceptual explanation of the TGH framework and why it is appropriate for modeling SSB-ssDNA interactions, perhaps with a simple illustrative example.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, parameter fitting
- **Evidence pointer** Table 1, Table 3, Methods section (location not provided)
- **Issue** The manuscript states that parameters are "determined simultaneously fitting" the data but does not describe the fitting procedure, the uncertainty in the fitted parameters, or the sensitivity of the results to parameter choices. Table 2 is referenced in the text but not provided.
- **Required correction** Describe the fitting procedure, provide parameter uncertainties, and include a sensitivity analysis. Ensure all referenced tables are present.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section, EcoSSB analysis
- **Evidence pointer** Figure 4, Table 3 (location not provided)
- **Issue** The manuscript states that the model can explain the experimental data for EcoSSB using modes of 8 and 17 nucleotides, but the text does not clearly describe how these mode sizes were determined or whether they are consistent with independent measurements.
- **Required correction** Clarify the source of the mode size values and discuss consistency with the literature.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results section
- **Evidence pointer** Section "Crowding-induced changes in effective rate constants explain bimodal kinetics" (location not provided)
- **Issue** The description of the bimodal kinetics and the model explanation is dense and would benefit from a clearer step-by-step explanation of the mechanism, perhaps with a schematic figure.
- **Required correction** Add a schematic figure or a more detailed textual explanation of the mechanism by which crowding produces the observed bimodal kinetics.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Discussion and Conclusions (location not provided)
- **Issue** The discussion of implications for genome maintenance mechanisms is brief and generic. The authors mention that the framework has "implications for understanding genome maintenance mechanisms" but do not elaborate on what these implications are.
- **Required correction** Expand the discussion of biological implications, perhaps by connecting the crowding effects to specific genome maintenance processes where SSB binding kinetics are relevant.

## Risk / unsupported claims

- The claim of "quantitative reproduction" of experimental data is unverifiable from the provided material because figures, tables, and Supplementary Information are not available.
- The claim that the model "explains" the bimodal kinetics and the transient shortening upon SSB removal is supported only by the model's ability to fit the data, not by independent validation or comparison with alternative models.
- The claim of generalizability to other multimode ligand systems is not demonstrated.
- The statement that "the observed binding kinetics is compatible with crowding-induced inhibition" is appropriately cautious but is not distinguished from other possible mechanisms.
- The model's assumption of two modes for EcoSSB (8 and 17 nucleotides) is stated but not justified in the provided text.
- The claim that non-nearest-neighbor interactions are "energetically disfavored" under tension is asserted without quantitative support.
- The potential effect of SSB condensates on effective free SSB concentration is mentioned but not incorporated into the model, and the magnitude of this effect is not estimated.