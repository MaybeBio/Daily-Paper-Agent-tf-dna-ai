## Review setup
- **Input scope** Full manuscript text (main text, Materials and Methods, figure legends referenced but not provided in full)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that arginine-rich dipeptide repeats (R-DPRs) poly-PR and poly-GR, linked to C9orf72 ALS/FTD, bind to the negatively charged IDR1 of G3BP1 and switch it from a closed, inactive state to an open, activated state, driving liquid-liquid phase separation (LLPS) more potently than RNA. They further propose that this interaction represents a general pathological mechanism targeting switch-like proteins in membrane-less organelles, with implications for therapeutic intervention.
- **Visible evidence base** Turbidity assays, fluorescence microscopy, dynamic light scattering, FRAP, biolayer interferometry, Thioflavin S assays, coarse-grained Monte Carlo simulations, bioinformatic interactome analyses, Western blot-based recruitment assays
- **Missing materials affecting confidence** Full figures and supplementary figures (Fig. 1A-H, Fig. 2A-G, Fig. 3A-G, Fig. 4A-F, SI Appendix figures and tables), detailed experimental protocols for several assays, statistical analysis details, raw data, and complete figure legends

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question in the ALS/FTD field: the molecular mechanism by which arginine-rich dipeptide repeats exert toxicity through perturbation of stress granule dynamics. The authors provide a compelling body of in vitro biochemical data suggesting that R-DPRs bind G3BP1 with much higher affinity than RNA and drive a more potent, qualitatively different form of phase separation. The combination of experimental and computational approaches is commendable. However, several concerns regarding the quantitative rigor of the binding data, the physiological relevance of the concentrations used, the interpretation of the cooperativity experiments, and the strength of the bioinformatic conclusions need to be addressed before the central claims can be fully established.

- **Who would be interested in the results, and why** Researchers in the fields of neurodegeneration (specifically ALS/FTD), RNA biology, phase separation and biomolecular condensates, and intrinsically disordered proteins. The work provides mechanistic insight into how a disease-linked toxic species (R-DPRs) can hijack a core stress granule protein, which is of direct relevance to understanding C9orf72 pathogenesis. The proposed general mechanism of targeting switch-like proteins may also interest a broader audience studying protein condensation in disease.

- **Major strengths** 1) The study addresses a significant and unresolved question in the field: the precise molecular target and mechanism of R-DPR toxicity in stress granules. 2) The combination of multiple orthogonal techniques (turbidity, microscopy, DLS, FRAP, BLI, simulations) provides a multi-faceted view of the phenomenon. 3) The comparative analysis of R-DPR versus RNA effects on G3BP1 phase separation is informative and highlights a potentially important distinction between physiological and pathological condensation. 4) The bioinformatic analysis extends the findings beyond G3BP1 to propose a broader mechanism, which is thought-provoking. 5) The distinction made between poly-GR and poly-PR behaviors is a valuable contribution, as these are often treated interchangeably.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative binding analysis
- **Claim pointer** The authors claim that R-DPRs bind G3BP1 with approximately 1000-fold higher affinity than RNA, based on BLI experiments (Fig. 2C, SI Appendix Table S3).
- **Evidence pointer** Fig. 2C, SI Appendix Fig. S6, SI Appendix Table S3
- **Concern** The BLI experiments are described as measuring binding of G3BP1 to immobilized R-DPRs or RNA. However, the manuscript does not provide sufficient detail on the experimental design, including the concentration range of G3BP1 used, the fitting model applied, and whether the data were globally or locally fitted. The reported Kd values (sub-nanomolar for R-DPRs) are unusually tight for a protein-disordered peptide interaction and may be influenced by avidity effects if G3BP1 is a dimer or if the immobilized ligand is multivalent. Furthermore, the comparison with polyU is complicated by the undefined length distribution of polyU, which the authors acknowledge but do not fully address in the interpretation. The claim of "absolute" Kd values for polyU is questionable given the polydisperse nature of the ligand.
- **Why it matters** The quantitative difference in binding affinity between R-DPRs and RNA is a cornerstone of the paper's central claim that R-DPRs are more potent drivers of G3BP1 phase separation. If the Kd values are inaccurate due to experimental artifacts or inappropriate fitting, the entire quantitative framework of the paper is weakened.
- **Resolution test** Provide full experimental details for BLI, including sensor loading levels, analyte concentration ranges, fitting models, and a representative sensorgram with the fit overlaid. Address the potential for avidity effects. For polyU, either use a defined-length RNA or provide a rigorous justification for the use of polydisperse polyU and discuss how the Kd should be interpreted in this context.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Physiological relevance of concentrations
- **Claim pointer** The authors conclude that R-DPRs drive G3BP1 phase separation more effectively than RNA and that this represents a pathological mechanism.
- **Evidence pointer** Fig. 1C-H, Fig. 2A-B, Materials and Methods
- **Concern** The concentrations of G3BP1, R-DPRs, and RNA used in the in vitro phase separation assays are not clearly stated in the main text. The authors mention "high protein and RNA concentrations" in the context of RNA-only experiments, but the specific concentrations for the R-DPR experiments are not provided. Given that R-DPRs are present at very low concentrations in patient cells, it is critical to know whether the concentrations used in this study are physiologically relevant. If the R-DPR concentrations required to drive G3BP1 phase separation are orders of magnitude higher than those found in vivo, the pathological relevance of the proposed mechanism is questionable.
- **Why it matters** The translational relevance of the findings depends on whether the observed effects occur at concentrations that are relevant to the disease state. Without this information, the reader cannot assess whether the proposed mechanism is likely to operate in patient cells.
- **Resolution test** Clearly state the concentrations of all components used in each phase separation assay. Provide a discussion of how these concentrations relate to estimated cellular concentrations of G3BP1 and R-DPRs in disease. If possible, perform experiments at lower, more physiologically relevant concentrations to demonstrate that the effect is not merely a high-concentration artifact.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of cooperativity
- **Claim pointer** The authors claim that R-DPRs and RNA show positive cooperativity in driving G3BP1 phase separation, based on the observation that the effect of both together is more than additive (Fig. 3B-C).
- **Evidence pointer** Fig. 3B-C, SI Appendix Fig. S9
- **Concern** The conclusion of cooperativity is based on comparing the effect of R-DPRs and RNA together versus the sum of their individual effects. However, this analysis is complicated by the fact that both R-DPRs and RNA can bind to G3BP1 and may compete for binding sites. The observation of a more-than-additive effect could also be explained by a simple increase in total multivalent cargo (both R-DPRs and RNA) that promotes phase separation through a mass-action effect, rather than by a specific allosteric cooperativity between the two ligands. The authors' simulation data (Fig. 3E-F) are suggestive but not definitive.
- **Why it matters** The claim of positive cooperativity is used to support the model of allosteric coupling between IDR1 and IDR3. If the effect is simply due to increased multivalency, the mechanistic model would need to be revised.
- **Resolution test** Perform experiments where the total concentration of multivalent cargo is held constant while varying the ratio of R-DPR to RNA. If the effect is truly cooperative, the phase separation should be enhanced at intermediate ratios compared to either component alone at the same total cargo concentration. Alternatively, use a non-binding RNA or a non-binding R-DPR mutant as a control to rule out mass-action effects.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the proposed mechanism
- **Claim pointer** The authors propose that R-DPRs target a broad set of "switch-like" proteins with acidic and basic IDR tracts and an RNA-binding domain, and that this represents a general pathological mechanism.
- **Evidence pointer** Fig. 4E, SI Appendix Tables S5-S7
- **Concern** The bioinformatic analysis identifies 23 R-DPR interactors and 7 toxicity effectors that share the "switch-like" features. However, the functional validation of this general mechanism is limited to G3BP1 and NPM1. It is not clear whether the other identified proteins are actually targeted by R-DPRs in a manner that affects their phase separation or function. The claim of generality is therefore not fully supported by the data presented.
- **Why it matters** The broader significance of the work depends on whether the mechanism proposed for G3BP1 and NPM1 applies to other proteins. Without functional validation of at least a few additional candidates, the claim of a general mechanism remains speculative.
- **Resolution test** Select 2-3 additional candidate proteins from the list of R-DPR interactors with switch-like features and test whether R-DPRs affect their phase separation in vitro and/or their localization in cells. This would provide direct evidence for the generality of the proposed mechanism.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Pathological relevance of ThS-positive state
- **Claim pointer** The authors show that R-DPR-induced G3BP1 droplets transition to a ThS-positive state, suggesting the formation of amyloid-like aggregates, and imply that this is relevant to pathology.
- **Evidence pointer** Fig. 4A-B
- **Concern** The ThS assay is used as a proxy for amyloid formation, but ThS can also bind to other structures, and the authors do not provide additional evidence (e.g., electron microscopy, X-ray diffraction, or seeding assays) to confirm that the ThS-positive state represents bona fide amyloid fibrils. Furthermore, the relationship between this in vitro state and the pathology observed in patient tissues is not established. The authors do not show that the ThS-positive G3BP1 aggregates are present in patient samples or that they share structural features with pathological inclusions.
- **Why it matters** The claim that R-DPRs drive G3BP1 toward a pathological amyloid-like state is a key part of the paper's significance. If the ThS signal is not specific or if the in vitro state is not representative of the in vivo pathology, this claim is weakened.
- **Resolution test** Provide additional characterization of the ThS-positive state, such as transmission electron microscopy to visualize fibrillar structures, or a seeding assay to demonstrate that the ThS-positive material can nucleate aggregation. If possible, use antibodies that specifically recognize pathological G3BP1 conformations to test for the presence of such states in patient tissue or in cellular models of R-DPR toxicity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Fig. 1C
- **Evidence pointer** Fig. 1C
- **Issue** The inset in Fig. 1C is mentioned in the text but its content is not described. It is unclear what "maximal OD values" refers to and how the inset relates to the main figure.
- **Required correction** Provide a clear description of the inset in the figure legend and in the text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The term "pathological phase separation" is used in the title and throughout the manuscript, but it is not clearly defined. What distinguishes "pathological" from "physiological" phase separation in this context?
- **Required correction** Provide a clear definition of "pathological phase separation" in the introduction or discussion, and use the term consistently throughout.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Materials and Methods
- **Evidence pointer** Materials and Methods
- **Issue** The Materials and Methods section is incomplete. Several assays are described in the Results but the corresponding methods are either missing or only briefly mentioned. For example, the ThS assay, the FRAP experiments, and the microfluidic setup are not described in sufficient detail.
- **Required correction** Provide complete descriptions of all experimental methods, including specific parameters, buffers, and data analysis procedures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The manuscript does not include any statistical analysis of the quantitative data (e.g., turbidity measurements, DLS, FRAP). It is unclear whether the observed differences are statistically significant.
- **Required correction** Add appropriate statistical tests to all quantitative comparisons and report the results (e.g., p-values, confidence intervals) in the figures and text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion does not address the limitations of the study, such as the use of in vitro systems, the potential for non-specific effects of R-DPRs, and the lack of direct evidence for the proposed mechanism in patient samples.
- **Required correction** Add a paragraph discussing the limitations of the study and how they might affect the interpretation of the results.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reference to previous work
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction and Discussion
- **Issue** The manuscript cites several previous studies on R-DPRs and G3BP1 but does not clearly distinguish the novel findings of this work from what was already known. For example, the authors state that a similar mechanism was "recently suggested" (ref 38) but do not explain what this study adds beyond that suggestion.
- **Required correction** Clearly articulate the novel contributions of this study relative to previous work, particularly ref 38.

## Risk / unsupported claims
- The claim that R-DPRs bind G3BP1 with sub-nanomolar affinity (Kd = 0.01 nM in the presence of RNA) is not fully supported by the data presented, given the lack of experimental detail and potential for avidity effects.
- The claim of positive cooperativity between R-DPR and RNA binding is not definitively established, as the more-than-additive effect could be explained by mass-action effects.
- The claim that the proposed mechanism is general and applies to a broad set of switch-like proteins is not supported by functional validation of additional candidates.
- The claim that R-DPR-induced G3BP1 droplets transition to a "pathological" amyloid-like state is not fully supported, as the ThS assay alone is not sufficient to establish amyloid formation.
- The physiological relevance of the concentrations used in the in vitro experiments is not established, and the authors do not demonstrate that the observed effects occur at concentrations relevant to disease.