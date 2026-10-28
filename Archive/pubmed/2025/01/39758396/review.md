## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, conclusion, and supplementary figure/table legends as referenced.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No external data or unpublished references were consulted.
- **Shared manuscript claim summary** The authors report the identification of three proteins (ACBD6, DCA, and a DNA-binding transcription factor) that interact with the transcription factor DpWRI1-like in the microalga *Dunaliella parva*, using yeast two-hybrid (Y2H) screening and bimolecular fluorescence complementation (BiFC) validation, followed by in silico bioinformatics analyses including protein-protein docking.
- **Visible evidence base** Y2H screening results (Fig. 2), BiFC fluorescence images (Fig. 3), bioinformatics predictions (Fig. 4, Supplementary Fig. S4), primer sequences (Table 1), and protein annotations (Table 2). Supplementary figures S1-S3 are referenced but not fully described in the text.
- **Missing materials affecting confidence** Full Y2H vector maps, detailed BiFC construct schematics, negative control data for BiFC, raw sequencing data for positive clones, statistical analysis of docking scores, and full supplementary figures (S1-S3) are not provided in the manuscript text. The manuscript does not include quantitative data for BiFC fluorescence intensity or Y2H colony counts beyond the initial screening.

## Reviewer
- **Overall assessment** The manuscript presents a straightforward application of established techniques (Y2H and BiFC) to identify candidate interacting partners of a transcription factor of interest. The experimental work is largely descriptive and preliminary. The main claims of interaction are supported by the Y2H and BiFC data, but the functional significance of these interactions for lipid biosynthesis is speculative and not experimentally tested. The bioinformatics analyses are routine and add limited insight. The manuscript is technically sound in its core methods but lacks depth in functional validation and mechanistic exploration.
- **Who would be interested in the results, and why** Researchers working on transcriptional regulation of lipid metabolism in microalgae, particularly those studying WRINKLED1-like transcription factors and their regulatory networks. The identification of ACBD6 and DCA as interaction partners may be of interest to those investigating lipid biosynthesis pathways in oleaginous microalgae for biofuel applications. The study also provides a methodological template for Y2H-based interactome studies in non-model microalgae.
- **Major strengths** 1. Clear and logical experimental design, starting from a previously characterized transcription factor. 2. Use of two orthogonal methods (Y2H and BiFC) to validate protein-protein interactions. 3. The study addresses a genuine gap in knowledge regarding DpWRI1-like interacting partners. 4. The manuscript is clearly written and the methods are described in sufficient detail for replication.
- **Major Concerns** 1. The functional relevance of the identified interactions to lipid biosynthesis is not experimentally demonstrated. 2. The bioinformatics analyses are superficial and do not provide mechanistic insights. 3. The BiFC assay lacks quantitative analysis and negative controls are not described. 4. The manuscript relies heavily on unpublished data and previous studies, making some claims difficult to verify.
- **Minor Comments** 1. The introduction could be more focused on the specific gap in knowledge regarding DpWRI1-like interacting proteins. 2. The discussion of ACBD6 and DCA functions in other organisms is relevant but not well integrated with the current findings. 3. The conclusion is somewhat repetitive of the abstract. 4. The manuscript would benefit from a figure summarizing the proposed model of DpWRI1-like regulation.
- **Technical failings that need to be addressed before the case is established** 1. Lack of negative controls for BiFC (e.g., empty vector controls, non-interacting protein pairs). 2. No quantitative assessment of Y2H interaction strength (e.g., β-galactosidase assays or dilution series). 3. The protein-protein docking scores are presented without statistical context or comparison to known non-interacting pairs. 4. The manuscript does not provide evidence that the identified interactions occur in vivo in *D. parva*.
- **Assessment against Nature-style criteria** **Originality:** Moderate. The identification of novel interacting partners for a microalgal WRI1-like transcription factor is a new contribution, but the approach is standard and the findings are incremental. **Scientific importance:** Limited. The study identifies candidate interactors but does not establish their functional role in lipid biosynthesis, which limits the significance of the findings. **Interdisciplinary readership:** Narrow. The study is primarily of interest to microalgal lipid researchers and transcription factor biologists. **Technical soundness:** Adequate for the core interaction assays, but the lack of negative controls and quantitative data weakens the evidence. **Readability for nonspecialists:** The manuscript is generally readable, but the bioinformatics sections may be challenging for non-experts. The significance of the findings for broader audiences is not clearly articulated.
- **Recommendation posture** Supportive if technical concerns are resolved. The core interaction data are promising, but the manuscript requires additional controls, quantitative analyses, and a clearer demonstration of functional relevance to fully support the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that BiFC assay "further validated the interaction between DpWRI1-like and interacting proteins ACBD6 and DCA."
- **Evidence pointer** Fig. 3, Results section "Results of BiFC assay"
- **Concern** The BiFC assay is presented as validation of the Y2H results, but the manuscript does not describe any negative controls. Without controls such as empty vectors, non-interacting protein pairs, or single-construct infiltrations, the specificity of the observed YFP signals cannot be confirmed. Additionally, the fluorescence images are qualitative, and no quantification of signal intensity or percentage of positive cells is provided.
- **Why it matters** BiFC is prone to false positives due to spontaneous complementation or overexpression artifacts. The absence of negative controls and quantitative data significantly weakens the claim that the observed interactions are specific and biologically relevant.
- **Resolution test** The authors should include BiFC experiments with negative controls (e.g., DpWRI1-like-YFPN with unfused YFPC, or a known non-interacting protein fused to YFPC) and provide quantitative data such as fluorescence intensity measurements or the percentage of cells showing positive signals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance
- **Claim pointer** The authors state that "this study contributes to a deeper understanding of the role of DpWRI1-like in lipid synthesis" and that the interacting proteins "have been found to be related to lipid biosynthesis in other organisms."
- **Evidence pointer** Abstract, Discussion section
- **Concern** The manuscript identifies three interacting proteins but provides no experimental evidence that these interactions are functionally relevant to lipid biosynthesis in *D. parva*. The discussion speculates about potential roles based on literature from other organisms, but no experiments are performed to test whether disruption or overexpression of these interactions affects lipid content or fatty acid composition.
- **Why it matters** The central claim of the manuscript is that these interactions are related to lipid biosynthesis. Without functional validation, the study remains descriptive and the significance of the findings is not established.
- **Resolution test** The authors should perform functional experiments, such as knockdown or overexpression of the interacting proteins in *D. parva*, and measure lipid content, fatty acid profiles, or expression of lipid biosynthesis genes. Alternatively, they could demonstrate that the interaction is required for DpWRI1-like-mediated transcriptional activation of target genes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Data completeness
- **Claim pointer** The authors report that "protein-protein docking indicated the strong affinity between DpWRI1-like and three interacting proteins."
- **Evidence pointer** Fig. 4C, Results section "Bioinformatics analysis of interacting proteins"
- **Concern** The docking scores are presented as evidence of strong affinity, but no statistical analysis or comparison to negative controls (e.g., docking of DpWRI1-like with a random or known non-interacting protein) is provided. The scores are also not contextualized with respect to what constitutes a "strong" interaction in the docking software used.
- **Why it matters** Docking scores are computational predictions and can be misleading without proper controls and statistical validation. Overinterpreting these scores as evidence of biological affinity is not justified.
- **Resolution test** The authors should provide docking scores for negative control protein pairs and perform statistical analysis to show that the scores for the three interacting proteins are significantly different from controls. Alternatively, they could validate the predicted binding interfaces through mutagenesis experiments.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "the cDNA library of *D. parva* (cell density > 2 × 10^7/mL) has been obtained in our previous work [17]."
- **Evidence pointer** Materials and methods, section "Preparation of cDNA library and yeast bait strain"
- **Concern** The manuscript relies on a previously described cDNA library and Y2H protocol, but the details of the library construction (e.g., vector, insert size, complexity) are not provided. This makes it difficult to assess the quality and coverage of the library, which is critical for the reliability of the Y2H screening results.
- **Why it matters** A low-complexity or poorly constructed library could lead to false negatives or biased results. The reproducibility of the screening depends on the quality of the library.
- **Resolution test** The authors should provide details of the cDNA library construction, including the number of independent clones, average insert size, and the vector used. If this information is available in the previous publication, it should be clearly referenced and summarized.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states that "DpWRI1-like was a key regulatory factor of lipid biosynthesis" but does not provide the context of how this was established in previous work.
- **Required correction** Briefly mention the previous findings (e.g., correlation with lipid content under nitrogen limitation) to provide context for readers unfamiliar with the prior studies.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 2
- **Evidence pointer** Fig. 2, Results section "Identification of interacting proteins"
- **Issue** The figure shows plasmid PCR results for only 10 of the 27 positive clones. It is unclear whether all 27 clones were analyzed and whether the three identified proteins were found in multiple independent clones.
- **Required correction** Provide a summary table or description of all 27 clones, including the number of times each protein was identified, to demonstrate the reproducibility of the screening.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph on DCA
- **Issue** The discussion mentions unpublished data on DCA overexpression in *D. parva* but does not provide any details or data. This makes it difficult to evaluate the relevance of this information.
- **Required correction** Either remove the reference to unpublished data or provide a brief summary of the key findings and how they relate to the current study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The manuscript contains several grammatical errors and awkward phrasings (e.g., "the size and quantity of colonies were similar" in the Results section).
- **Required correction** The manuscript should be carefully edited for language and grammar to improve readability.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and methods
- **Evidence pointer** Materials and methods, section "Bioinformatics analysis"
- **Issue** The bioinformatics methods are described only by listing software names. No parameters, versions, or analysis details are provided.
- **Required correction** Provide a brief description of the parameters used for each software tool and the version numbers to ensure reproducibility.

## Risk / unsupported claims
- The claim that the identified interactions are "related to lipid biosynthesis" is unsupported by direct experimental evidence in this manuscript.
- The claim of "strong affinity" based on docking scores is unsupported without statistical comparison to negative controls.
- The functional significance of the interaction between DpWRI1-like and the DNA-binding transcription factor (TF) is entirely speculative and not addressed experimentally.
- The statement that "this study firstly reported three interacting proteins" is difficult to verify and should be softened or supported with a more thorough literature search.
- The relevance of the unpublished studies mentioned in the Discussion to the current findings cannot be assessed.