## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods, extended data descriptions)
- **Assessment boundary** Scientific claims, experimental evidence, methodological rigor, and interpretive consistency as presented in the provided text
- **Shared manuscript claim summary** The authors propose that BRD2, a BET family scaffold protein, promotes spatial mixing and compartmentalization of active chromatin domains (ACDs) upon Cohesin loss, acting through its double bromodomain and low-complexity domain, and that this activity is antagonized by Cohesin and BRD4, with polymer simulations supporting a competition model between loop extrusion and chromatin state-specific affinity interactions.
- **Visible evidence base** Descriptions of 3D ATAC-PALM imaging, live-cell SOX2 imaging, Hi-C, Micro-C, ChIP-seq, CUT&Tag, single-particle tracking, biochemical fractionation, and polymer simulations; specific figure references (Fig. 1-5, Extended Data Fig. 1-12) are cited but not directly viewable
- **Missing materials affecting confidence** Actual figures, supplementary tables, statistical details, and raw data are not provided; only textual descriptions of results and methods are available

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially significant model for BRD2-mediated compartmentalization of accessible chromatin, supported by a multi-pronged experimental approach. The combination of super-resolution imaging, genomic assays, and polymer modeling is impressive and generally well-integrated. However, the absence of the actual figures and quantitative data prevents full verification of the claims. Several interpretive leaps, particularly regarding the causal role of BRD2 and the mechanistic distinction from BRD4, require stronger direct evidence. The study is likely to be of high interest to the chromatin and genome architecture community, but the current evidence base, as textually described, does not fully establish all conclusions.

- **Who would be interested in the results, and why** Chromatin biologists, genome architects, and researchers studying transcriptional regulation would find this work highly relevant. The identification of BRD2 as a specific mediator of active chromatin compartmentalization, distinct from BRD4, offers a new mechanistic layer to the understanding of 3D genome organization. The proposed competition between Cohesin-mediated loop extrusion and BRD2-mediated affinity interactions provides a testable framework that could influence future studies on nuclear organization in development and disease, particularly given the pharmacological targetability of BET proteins.

- **Major strengths**
  1. The study employs a sophisticated and complementary array of techniques, including 3D ATAC-PALM, live-cell imaging, Hi-C/Micro-C, and targeted protein degradation, to address a fundamental question in genome biology.
  2. The identification of BRD2, rather than the more commonly studied BRD4, as the key BET family member for ACD mixing is a novel and unexpected finding that challenges existing assumptions.
  3. The integration of experimental data with polymer simulations provides a quantitative framework that strengthens the proposed mechanistic model.
  4. The careful use of acute degradation systems (AID and PROTAC) minimizes compensatory effects and strengthens causal inferences.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that BRD2 "promotes spatial mixing and compartmentalization of active chromatin after Cohesin loss" is central to the paper.
- **Evidence pointer** Results sections "Spatial mixing of ACDs is independent of transcription but involves BET family proteins" and "The interplay between BRD2 and Cohesin regulates genome topology"; Figures 2, 3, 4
- **Concern** The causal role of BRD2 is primarily inferred from loss-of-function experiments (BRD2 depletion reversing Cohesin-loss phenotypes). The text does not describe gain-of-function experiments (e.g., BRD2 overexpression in the presence of Cohesin) that would more directly demonstrate sufficiency. Furthermore, the specificity of BRD2 over BRD3/BRD4 is based on depletion phenotypes, but the text does not provide quantitative comparisons of the magnitude of effects or rule out redundant functions. The claim that BRD2 is the "effector" requires direct demonstration that BRD2 binding to chromatin is necessary and sufficient for the observed compartmentalization, which is not fully established from the described experiments.
- **Why it matters** Without direct evidence for sufficiency and a clear quantitative distinction from other BET proteins, the central claim that BRD2 is the primary driver of ACD mixing remains correlative. This weakens the mechanistic model and the proposed division of labor between BRD2 and BRD4.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretive consistency
- **Claim pointer** The claim that BRD2-mediated compartmentalization is "independent of transcription" is used to argue for a direct structural role.
- **Evidence pointer** Results section "Spatial mixing of ACDs is independent of transcription but involves BET family proteins"; Figure 4d-e; Extended Data Fig. 4a-c
- **Concern** The text states that alpha-amanitin treatment and subsequent Rbp1 degradation did not affect clustering or compaction. However, the duration of transcriptional inhibition and the completeness of RNA Pol II depletion are not described in the provided text. It is unclear whether the 5-hour treatment is sufficient to eliminate all transcription-dependent effects on chromatin architecture, given that some structural changes may have longer timescales. Additionally, the text does not report on the transcriptional status of the specific ACDs being imaged, leaving open the possibility that local transcription at these loci is unaffected by global inhibition.
- **Why it matters** The claim of transcription-independence is critical for distinguishing BRD2's structural role from indirect effects via gene expression changes. If transcriptional inhibition is incomplete or not verified at the loci of interest, the conclusion that BRD2 acts directly on chromatin architecture is not fully supported.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor
- **Claim pointer** The claim that polymer simulations "qualitatively reproduce" experimental observations is used to support the model.
- **Evidence pointer** Results section "Polymer modeling incorporating loop extrusion and chromatin state-specific affinity interactions"; Figure 5; Extended Data Fig. 12
- **Concern** The text describes qualitative agreement between simulations and experiments but does not provide quantitative metrics for comparison. It is unclear how the simulation parameters (e.g., protein concentration, interaction strengths) were calibrated to experimental data, and whether the model's predictions are unique to the proposed mechanism. The robustness tests described (Extended Data Fig. 12) address parameter sensitivity but do not provide a statistical framework for comparing model output to experimental measurements.
- **Why it matters** A qualitative match is insufficient to validate a mechanistic model, especially when multiple parameters could be tuned to achieve similar results. Quantitative comparison (e.g., goodness-of-fit metrics, model selection against alternative mechanisms) is needed to establish that the BRD2-Cohesin competition model is the most parsimonious explanation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Polymer modeling"
- **Evidence pointer** Methods, "Polymer modeling" subsection
- **Issue** The description of the polymer model is dense and lacks a clear schematic or step-by-step explanation of how the simulation parameters map to biological quantities. The distinction between "active" and "inactive" protein states and the rationale for the specific protein concentration changes upon Cohesin depletion are not fully explained.
- **Required correction** Provide a clearer conceptual outline of the model, including a table of parameters and their biological equivalents, and explicitly justify the choice of protein concentration changes based on experimental measurements (e.g., from single-particle tracking).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "ChIP-seq and CUT&Tag"
- **Evidence pointer** Methods, "ChIP-seq and CUT&Tag" subsection
- **Issue** The text mentions that BRD2 CUT&Tag was performed with two different antibodies but does not specify how data from the two antibodies were combined or whether they yielded consistent results. Details on peak calling thresholds and reproducibility between replicates are not provided.
- **Required correction** Specify the analysis pipeline for combining data from multiple antibodies, including any concordance metrics, and report the number of replicates and peak-calling parameters used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Cohesin loss triggers spatial mixing of ACDs without affecting their compaction"
- **Evidence pointer** Results, first subsection; Extended Data Fig. 1-3
- **Issue** The text states that "acute loss of Cohesin triggered prominent organizational changes" and that "the increase in accessible chromatin clustering was reversed," but does not report effect sizes, confidence intervals, or the number of biological replicates for the imaging experiments.
- **Required correction** Include quantitative summaries (e.g., mean ± SEM, n, p-values) for the key imaging metrics in the main text or figure legends.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "BRD4 competes with BRD2 and blocks its activities in genome organization"
- **Evidence pointer** Results, fourth subsection; Figure 4
- **Concern** The text describes that BRD4 depletion increases BRD2 binding and enhances compartmentalization, but does not address whether BRD4 overexpression (in the absence of Cohesin) would suppress BRD2-mediated effects. This would strengthen the competition model.
- **Required correction** Consider adding a discussion of whether such experiments are feasible or planned, or acknowledge this as a limitation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "compartmentalizes" is used to describe BRD2's function, but the text does not clearly define what constitutes a "compartment" at the scale being studied (e.g., vs. TADs or A/B compartments). This could lead to ambiguity in interpretation.
- **Required correction** Provide a clear operational definition of "compartmentalization" as used in this study, and clarify how it relates to existing nomenclature.

## Risk / unsupported claims
- The claim that BRD2 is the "only" BET family protein responding to Cohesin loss is not fully supported, as BRD3 depletion showed no effect but the text does not rule out partial redundancy.
- The statement that "BRD2 has the highest enrichment at CTCF binding sites among BET family proteins" is presented without quantitative comparison in the text.
- The claim that the polymer model "recapitulated existing experimental observations" is based on qualitative agreement; quantitative validation is not described.
- The assertion that "histone acetylation and bromodomain protein interactions may have a conserved role" in pathology is speculative and extends beyond the data presented.
- The text mentions "enhanced checkerboard pattern" in Micro-C but does not provide a clear definition or quantitative measure of this pattern.