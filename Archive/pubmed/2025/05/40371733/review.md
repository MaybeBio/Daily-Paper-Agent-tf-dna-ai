## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, and methods
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and conclusions as presented in the provided text
- **Shared manuscript claim summary** The authors map short linear motifs (SLiMs) and activation domains (ADs) in an Arabidopsis NAC transcription factor clade, characterize the intrinsically disordered region (IDR) of ANAC046, and demonstrate that two distant AD/SLiM regions bind six regulator domains promiscuously with a hierarchy of affinities, proposing a rheostatic regulatory mechanism.
- **Visible evidence base** NMR spectroscopy (chemical shifts, relaxation, PREs), ITC binding data, SAXS with ensemble reweighting, coarse-grained simulations, bioinformatic SLiM identification
- **Missing materials affecting confidence** Figures and supplementary tables referenced but not provided; specific NMR assignment details; raw ITC thermograms; AlphaFold 3 model confidence metrics; statistical details for ensemble comparisons

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive biophysical characterization of the ANAC046 IDR and its interactions with multiple regulator domains. The work addresses an important question in transcriptional regulation, namely how multiple ADs in long IDRs coordinate regulator binding. The combination of NMR, ITC, SAXS, and simulations is rigorous and appropriate. However, several claims regarding the rheostatic model and the functional significance of the observed hierarchy require stronger direct evidence. The link between in vitro binding affinities and in vivo regulatory outcomes is inferred rather than demonstrated. The manuscript would benefit from clearer presentation of the SLiM-AD relationship and a more critical discussion of alternative interpretations.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, intrinsically disordered proteins, and plant stress/senescence signaling would find this work relevant. The methodological approach combining multiple biophysical techniques on a plant transcription factor IDR is of broad interest to the IDP community. The proposed rheostatic model could inform studies of other transcription factors with multiple ADs.
- **Major strengths** 1) Comprehensive biophysical characterization using complementary techniques (NMR, ITC, SAXS, simulations). 2) The use of a plant transcription factor family adds diversity to the predominantly mammalian-focused AD literature. 3) The identification of a binding hierarchy between two ADs and multiple regulators is novel. 4) The integration of experimental data with coarse-grained simulations provides mechanistic insight into IDR behavior.
- **Major Concerns** 1) The rheostatic model is inferred from in vitro binding data without direct functional validation. 2) The claim that SLiMs and ADs do not systematically overlap is based on a limited dataset. 3) The physiological relevance of the selected regulator domains is not fully justified. 4) The interpretation of PRE data in the context of RCD1-RST binding may be confounded by aggregation effects.
- **Minor Comments** 1) The abstract could more clearly state the novelty of the findings. 2) Some figure references are unclear without seeing the actual figures. 3) The discussion of phase separation propensity is speculative and not directly tested. 4) The methods section for ITC lacks some experimental details.
- **Technical failings that need to be addressed before the case is established** The functional significance of the binding hierarchy is not demonstrated. The manuscript shows that two ADs bind regulators with different affinities, but does not show how this translates to rheostatic transcriptional regulation in cells. Without this link, the central claim remains speculative.
- **Assessment against Nature-style criteria** Originality: Moderate to high. While individual techniques are established, the combination and the specific biological system are novel. Scientific importance: Moderate. The findings advance understanding of plant transcription factor regulation but the generalizability to other systems is not established. Interdisciplinary readership: The work bridges structural biology, biophysics, and plant biology, potentially appealing to a broad audience. Technical soundness: Generally high, with appropriate controls and rigorous data analysis. Readability for nonspecialists: The manuscript is dense and assumes significant background knowledge in NMR and IDP biology, which may limit accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the functional validation of the rheostatic model and clarification of the SLiM-AD relationship.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance
- **Claim pointer** The authors claim that the hierarchy in regulator binding to two distant ADs "empowers rheostatic regulation" and that this mechanism is "likely mirrored in other transcription factors."
- **Evidence pointer** Discussion section, Figure 5 (referenced but not provided)
- **Concern** The central claim of rheostatic regulation is inferred from in vitro binding affinities without any functional validation. The manuscript does not demonstrate that the observed binding hierarchy translates to graded transcriptional responses in cells. The proposed model of concentration-dependent competition between regulators is plausible but remains speculative without experiments showing, for example, that varying regulator concentrations produces graded transcriptional outputs in a cellular context.
- **Why it matters** The rheostatic model is the main conceptual advance of the paper. Without functional evidence, the physiological relevance of the observed binding hierarchy is unclear. The claim that this mechanism is "likely mirrored" in other transcription factors is an extrapolation that requires at least some comparative or functional support.
- **Resolution test** Provide experimental evidence linking the binding hierarchy to transcriptional outcomes, such as reporter assays with varying regulator concentrations, or mutagenesis of the ADs to disrupt the hierarchy and show altered transcriptional responses. Alternatively, clearly reframe the claims as a testable model rather than an established mechanism.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** SLiM-AD relationship
- **Claim pointer** The authors state that "although sequence motifs and activation domains often coincide, no systematic overlap exists" based on their analysis of the NAC clade II-3 transcription factors.
- **Evidence pointer** Results section "SLiM identification in the long IDRs of ANAC clade II-3 transcription factors" and "SLiMs are not directly linked to AD activity", Figure 1
- **Concern** The conclusion that SLiMs and ADs do not systematically overlap is based on a small dataset of 13 transcription factors from a single clade. The analysis relies on AD predictions from a high-throughput yeast assay (Morffy et al., 2024) that may not capture all functional ADs, as the authors acknowledge. The criteria for defining "overlap" are not clearly stated, and the statistical power to detect systematic patterns is limited.
- **Why it matters** The relationship between SLiMs and ADs is a key conceptual point of the paper. If the conclusion is based on insufficient data or ambiguous criteria, it weakens the foundation for the subsequent focus on ANAC046.
- **Resolution test** Expand the analysis to include more transcription factor families or provide a more rigorous statistical framework for assessing overlap. Clearly define the spatial criteria for overlap and consider whether the AD assay captures all relevant ADs. Alternatively, soften the claim to reflect the preliminary nature of the observation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Binding site specificity
- **Claim pointer** The authors conclude that both AD1/M1-2 and AD2/M5 bind all six regulator domains promiscuously, with different binding modes and affinities.
- **Evidence pointer** Results section "The ANAC046 IDR binds regulators promiscuously at overlapping sites", Figures 3, S6-S11, Table 2
- **Concern** The evidence for promiscuous binding relies primarily on NMR peak intensity changes and chemical shift perturbations. For several regulator domains, aggregation or precipitation was observed, complicating the interpretation. The AlphaFold 3 models are used to support binding mode differences, but these predictions lack experimental validation. The claim that the two ADs are "uncoupled in binding" is based on the absence of avidity effects, but the linker length argument may not fully exclude allosteric or conformational coupling.
- **Why it matters** The promiscuous binding and independence of the two ADs are central to the proposed rheostatic mechanism. If the binding is not truly promiscuous or if the ADs are coupled in some way, the model would need revision.
- **Resolution test** Provide more detailed binding data for each regulator-AD pair, including quantitative affinity measurements where possible. Validate AlphaFold 3 predictions with mutagenesis or cross-linking experiments. Address the aggregation issue more thoroughly, perhaps by using alternative buffer conditions or techniques less sensitive to precipitation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Ensemble representation
- **Claim pointer** The authors state that the ANAC046 IDR is "devoid of residual structure" and that the ensemble is "slightly expanded" based on SAXS and NMR data.
- **Evidence pointer** Results section "The ANAC046 IDR: Lack of residual structure, with propensity to phase separate", Figures 2, S4
- **Concern** The conclusion that the IDR lacks residual structure is based on secondary chemical shifts and relaxation data, which are consistent with a disordered state. However, the SAXS-derived scaling exponent of 0.56 suggests a slightly expanded chain, which is interpreted as such. The reweighted ensemble is used to explain PRE data, but the agreement between experimental and calculated PREs is only described qualitatively. The choice of the CALVADOS 2 model and the reweighting procedure may introduce biases that are not fully discussed.
- **Why it matters** The structural characterization of the IDR is foundational to the binding studies. If the ensemble representation is inaccurate, the interpretation of binding-induced changes and the proposed mechanism could be affected.
- **Resolution test** Provide quantitative measures of the agreement between experimental and calculated PREs (e.g., R² values). Discuss potential limitations of the coarse-grained model and reweighting approach. Consider validating the ensemble with additional experimental data, such as FRET or single-molecule measurements.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the results "imply rheostatic regulation" but does not clearly define what is meant by "rheostatic" in this context. The term may be unfamiliar to some readers.
- **Required correction** Briefly define or contextualize "rheostatic regulation" in the abstract, or use more accessible language such as "graded" or "tunable" regulation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** ITC methods
- **Evidence pointer** Materials and Methods, "Isothermal titration calorimetry"
- **Issue** The ITC methods section does not specify the buffer conditions, temperature, or the concentration ranges for all experiments. Some details are mentioned in the results but not systematically.
- **Required correction** Provide a complete description of ITC experimental conditions, including buffer composition, pH, temperature, and concentration ranges for both titrant and titrand.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of phase separation
- **Evidence pointer** Results section "The ANAC046 IDR: Lack of residual structure, with propensity to phase separate", Figure 2d
- **Issue** The prediction of phase separation propensity is mentioned but not experimentally tested. The relevance of this prediction to the binding studies is unclear.
- **Required correction** Either remove the phase separation prediction or explicitly state that it is speculative and not directly tested, and clarify its potential relevance to the proposed mechanism.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure references
- **Evidence pointer** Throughout the text
- **Issue** Several figures are referenced but not provided in the manuscript text, making it difficult to fully evaluate the data. This is likely due to the format of the submission, but it limits the review.
- **Required correction** Ensure all figures and supplementary materials are accessible to the reviewers, or provide a summary of key data points in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The authors suggest that the rheostatic mechanism is "likely mirrored in other transcription factors" but do not provide specific examples or a systematic analysis to support this claim.
- **Required correction** Either provide examples of other transcription factors with similar features or temper the claim to acknowledge that this is a hypothesis requiring further testing.

## Risk / unsupported claims
- The rheostatic regulatory model is not directly supported by functional experiments; it is inferred from in vitro binding data.
- The claim that SLiMs and ADs do not systematically overlap is based on a limited dataset and may not be generalizable.
- The prediction of phase separation propensity is not experimentally validated and its relevance to the proposed mechanism is unclear.
- The assertion that the two ADs are "uncoupled in binding" is based on the absence of avidity effects, which may not fully exclude other forms of coupling.
- The AlphaFold 3 models of the complexes are not experimentally validated and should be treated as predictions.
- The physiological relevance of the selected regulator domains (RCD1, TAF4, HAC1, MED25) to ANAC046 function in planta is not experimentally demonstrated.