## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors report that Borrelia burgdorferi PlzA, a c-di-GMP binding protein, binds DNA and RNA in a c-di-GMP-dependent manner, with the N-terminal domain mediating nucleic acid interactions and c-di-GMP binding stabilizing the protein structure to facilitate binding
- **Visible evidence base** EMSA data (Figures 2, 4, 5, 6, 7, 8, 10), LC-MS/MS analysis (Figures 3, 11A), circular dichroism (Figure 11B), computational docking (Figure 12), statistical analyses (Figure 4D, 9), and a proposed model (Figure 13)
- **Missing materials affecting confidence** Original gel images, raw densitometry data, full statistical outputs, supplementary figures (Figure S1 referenced but not provided), protein purity assessments, and detailed docking parameters

## Reviewer
- **Overall assessment** This manuscript presents a systematic biochemical characterization of PlzA as a c-di-GMP-dependent nucleic acid binding protein. The work addresses an important gap in understanding how c-di-GMP signaling is transduced in Borrelia burgdorferi. The experimental approach is logical and the data largely support the major conclusions. However, several technical concerns regarding binding affinity calculations, the physiological relevance of the micromolar binding constants, and the interpretation of the groove binding and docking experiments need to be addressed before the case is fully established. The study is of interest to the bacterial signaling and gene regulation communities, though the mechanistic depth is currently limited by the absence of in vivo validation and identification of specific binding motifs.
- **Who would be interested in the results, and why** Researchers studying c-di-GMP signaling in bacteria, particularly those focused on PilZ domain proteins and their effector mechanisms. The work also has relevance for the Borrelia research community, as PlzA is the sole c-di-GMP binding protein in Lyme disease spirochetes and is implicated in the enzootic life cycle. Additionally, those interested in novel nucleic acid binding domains and the intersection of second messenger signaling with transcriptional regulation would find this study valuable.
- **Major strengths** The study fills a significant knowledge gap by identifying a biochemical function for PlzA, which was previously unknown. The use of multiple complementary approaches (EMSAs, mutant proteins, LC-MS/MS, CD spectroscopy, computational docking) strengthens the conclusions. The demonstration that c-di-GMP binding is required for nucleic acid binding provides a clear mechanistic link between second messenger levels and gene regulation. The identification of the N-terminal domain as the nucleic acid binding domain is a useful advance.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (binding affinity calculations), R1-M2 (physiological relevance of binding constants), R1-M3 (interpretation of groove binding data), R1-M4 (docking analysis limitations)
- **Assessment against Nature-style criteria** Originality: The finding that a PilZ domain protein binds both DNA and RNA in a c-di-GMP-dependent manner is novel and extends the known functional repertoire of c-di-GMP binding proteins. Scientific importance: The work provides a mechanistic basis for PlzA function in B. burgdorferi, which is important for understanding the enzootic life cycle of this pathogen. However, the broader significance beyond Borrelia may be limited, as PlzA is not widely conserved. Interdisciplinary readership: The work will appeal primarily to microbiologists and those studying bacterial signal transduction; the broader readership interest is moderate. Technical soundness: The experimental design is generally sound, but concerns about binding affinity calculations, the lack of in vivo validation, and the interpretive limitations of the docking and groove binding experiments temper confidence. Readability for nonspecialists: The manuscript is clearly written and the logic is easy to follow, though some sections (e.g., docking analysis) assume familiarity with structural biology concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core finding that PlzA is a c-di-GMP-dependent nucleic acid binding protein is likely correct and important, but the quantitative aspects of the binding data and the physiological relevance need to be strengthened.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of binding affinity calculations
- **Claim pointer** The authors report apparent KD values for PlzA binding to DNA, RNA, and ssDNA (e.g., KD(app) of 1.09 ± 0.06 μM for dsDNA at 100 μM c-di-GMP, 0.95 ± 0.11 μM for RNA, 4.42 ± 0.90 μM for ssDNA).
- **Evidence pointer** Figures 4C, 4D, 8, 9, Table 1
- **Concern** The KD(app) values are calculated from EMSA data using densitometry and a one-site specific binding model. However, the manuscript does not describe how the fraction of bound DNA was determined, whether the free and bound species were in equilibrium during electrophoresis, or how the super-shifted species (which the authors acknowledge may represent non-1:1 stoichiometry) were included in the analysis. The progressive super-shifting and smearing at higher protein concentrations suggest complex dissociation during electrophoresis, which would compromise the accuracy of the calculated KD values. Additionally, the assumption of a 1:1 binding stoichiometry is stated to be uncertain, yet the calculations rely on this assumption.
- **Why it matters** The quantitative binding affinities are a central part of the manuscript's conclusions, particularly the comparison between different nucleic acid substrates and the effect of c-di-GMP. If the KD values are inaccurate due to methodological issues, the conclusions about relative affinities and the magnitude of the c-di-GMP effect may be unreliable.
- **Resolution test** The authors should provide a detailed description of how the bound fraction was quantified, including whether the super-shifted species were included as bound, and how the potential dissociation during electrophoresis was accounted for. Alternative methods such as fluorescence anisotropy or surface plasmon resonance should be considered to validate the KD values. If the 1:1 stoichiometry assumption cannot be justified, the KD values should be described as apparent and the limitations clearly stated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Physiological relevance
- **Claim pointer** The authors propose that c-di-GMP levels during the enzootic life cycle direct PlzA binding to regulatory targets, implying that the binding affinities measured are physiologically relevant.
- **Evidence pointer** Discussion, Figure 13
- **Concern** The measured KD values for PlzA-nucleic acid interactions are in the low micromolar range (approximately 1-9 μM). The manuscript does not discuss whether these affinities are consistent with the intracellular concentrations of PlzA and its target nucleic acids in B. burgdorferi. If the cellular concentrations of PlzA and target sites are significantly lower than the KD, the interaction would be inefficient. Additionally, the concentration of c-di-GMP required to activate binding (approximately 25-100 μM for maximal effect) may not reflect the physiological range in B. burgdorferi, which has not been measured in this study.
- **Why it matters** The proposed model in Figure 13 depends on the assumption that the binding affinities measured in vitro are relevant in vivo. Without addressing this, the physiological significance of the findings remains uncertain.
- **Resolution test** The authors should discuss the estimated intracellular concentrations of PlzA, c-di-GMP, and target nucleic acids in B. burgdorferi, and whether the measured KD values are consistent with a functional interaction. If possible, experiments using cellular lysates or in vivo crosslinking could provide evidence for the relevance of the measured affinities.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of groove binding data
- **Claim pointer** The authors conclude that PlzA interacts predominantly with the major groove of DNA based on competition experiments with methyl green and actinomycin D.
- **Evidence pointer** Figure 5
- **Concern** The competition experiments with methyl green and actinomycin D are indirect and can be difficult to interpret. Methyl green is a large molecule that may not specifically occupy the major groove, and actinomycin D intercalates into DNA rather than binding exclusively to the minor groove. The concentrations used (0.25-250 μM) are high, and the specificity of these drugs for their respective grooves is not absolute. The authors do not provide a quantitative analysis of the competition data, and the conclusion that PlzA binds predominantly to the major groove is based on visual inspection of the EMSA gels.
- **Why it matters** The groove preference is used to support the docking model and the proposed mode of DNA recognition. If the interpretation is incorrect, the mechanistic model may be flawed.
- **Resolution test** The authors should provide quantitative analysis of the competition data, including the concentrations at which each drug effectively competes with PlzA binding. Additional experiments using minor groove binders with higher specificity, or footprinting assays, would strengthen the conclusion.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Computational docking limitations
- **Claim pointer** The computational docking analysis predicts that c-di-GMP binding stabilizes the overall protein structure and facilitates PlzA-DNA interactions via residues in the N-terminal domain.
- **Evidence pointer** Figure 12
- **Concern** The docking analysis was performed using the HDOCK server with default parameters, and the manuscript does not provide details on the validation of the docking results, the number of models generated, or the criteria used to select the top model. The docking scores and confidence scores are mentioned in the figure legends, but the specific values are not reported in the text. The prediction that c-di-GMP binding stabilizes the protein structure is not directly tested experimentally, and the docking model is not validated by mutagenesis of the predicted interacting residues.
- **Why it matters** The docking analysis is used to support the mechanistic model, but without experimental validation, the predictions remain speculative.
- **Resolution test** The authors should provide the docking scores and confidence values in the text, describe the model selection criteria, and ideally validate the predicted interacting residues through site-directed mutagenesis experiments.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2
- **Issue** The EMSA data in Figure 2 show that PlzA binding to the glpFKD(−219) probe occurs at micromolar concentrations, but the authors do not show a no-protein control lane for each condition. Additionally, the figure legend does not specify the concentration range of PlzA used in each panel.
- **Required correction** Include no-protein controls in all panels and specify the protein concentration range in the figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Figure 4D
- **Evidence pointer** Figure 4D
- **Issue** The statistical analysis compares KD(app) values across different c-di-GMP concentrations, but the number of independent replicates and the exact p-values are not reported in the text or figure legend.
- **Required correction** Report the number of replicates and exact p-values for all statistical comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Protein characterization
- **Affected element** Methods, Recombinant protein overexpression and purification
- **Evidence pointer** Methods section
- **Issue** The manuscript does not report the purity of the recombinant proteins used in the binding assays. While SDS-PAGE and Coomassie staining are mentioned, no gel images or purity estimates are provided.
- **Required correction** Include representative SDS-PAGE gels showing protein purity for all recombinant proteins used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** RNA binding specificity
- **Affected element** Figure 8
- **Evidence pointer** Figure 8
- **Issue** The RNA binding experiments use a single RNA probe derived from the glpFKD 5' UTR. It is unclear whether PlzA binds RNA non-specifically or with sequence specificity. A control RNA of unrelated sequence would help address this.
- **Required correction** Include a control RNA of unrelated sequence to demonstrate binding specificity.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of conflicting data
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The authors reference a prior study (Zhang et al., 2018) that concluded PlzA does not bind DNA, but the discussion of this discrepancy is brief. A more detailed comparison of the experimental conditions that might explain the different results would be valuable.
- **Required correction** Expand the discussion of the discrepancy with Zhang et al., including potential differences in protein preparation, DNA substrates, or assay conditions.

## Risk / unsupported claims
- The claim that PlzA binding to nucleic acids is "c-di-GMP dependent" is supported by the data, but the quantitative relationship between c-di-GMP concentration and binding affinity is not fully characterized.
- The proposal that c-di-GMP levels during the enzootic life cycle direct PlzA binding to regulatory targets (Figure 13) is speculative and not directly tested.
- The conclusion that PlzA interacts predominantly with the major groove of DNA is based on indirect competition experiments and requires additional validation.
- The computational docking predictions regarding the stabilizing effect of c-di-GMP and the specific residues involved in nucleic acid binding are not experimentally validated.
- The claim that PlzA is the first c-di-GMP binding protein demonstrated to also bind RNA is presented without a comprehensive literature search to support this assertion.