## Review setup
- **Input scope** Full manuscript text, including Summary, Introduction, Results, Discussion, Resource Availability, and STAR Methods sections. Figures, tables, and supplementary materials are referenced but not provided.
- **Assessment boundary** Assessment is limited to the claims, methods, and interpretations presented in the provided text. Experimental data, figures, and supplementary information are not available for independent verification.
- **Shared manuscript claim summary** The authors propose three chromatin folding principles underlying V(D)J recombination at the mouse Igh locus: (1) cohesin loading throughout the locus, not just at the recombination center, is required for long-range chromatin structure and distal VH gene utilization; (2) the Eμ enhancer, which lacks CTCF binding, functions as a bidirectional loop extrusion blocker; (3) interactions between H3K27ac-marked regions and Eμ are necessary to fully recapitulate VH gene usage across the 2.8 Mb locus. The model is validated by comparing simulated contact maps and VH recombination frequencies against published experimental data, including wild-type and mutant alleles.
- **Visible evidence base** The manuscript text describes simulations using the polychrom software, comparisons to published capture Hi-C, Hi-ChIP, ChIP-seq, and VH usage datasets, and qualitative agreement between simulated and experimental results. No primary experimental data, figures, or quantitative statistical analyses are included in the provided material.
- **Missing materials affecting confidence** All figures, tables, supplementary figures, and detailed statistical outputs are absent. The manuscript references specific datasets (GSE214438, GSE241661, GSE151910, GSE140975, GSE113023) but these are not accessible for review. Quantitative metrics of model fit, such as correlation coefficients or error bars, are not provided in the text.

## Reviewer
- **Overall assessment** The manuscript addresses a fundamental question in immunology and genome biology: how do distal VH gene segments achieve comparable recombination frequencies across a 2.5 Mb locus? The authors combine polymer simulations with published experimental data to propose a mechanistic model with three distinct principles. The work is conceptually interesting and timely, given the ongoing debate about loop extrusion and RAG scanning. However, the current manuscript, as presented, does not provide sufficient quantitative evidence to fully support the claims. The absence of figures, detailed model validation statistics, and sensitivity analyses limits the ability to assess the robustness of the conclusions. The model's predictive power is demonstrated qualitatively, but the lack of formal statistical comparison between simulated and experimental data weakens the central claims.
- **Who would be interested in the results, and why** Immunologists studying V(D)J recombination and antibody repertoire generation would be directly interested. Additionally, researchers in chromatin biology, particularly those focused on loop extrusion, cohesin dynamics, and enhancer-promoter interactions, would find the proposed principles relevant. The work may also appeal to computational biologists developing polymer models of genome organization. The broader implications for enhancer function and long-range gene regulation extend the potential readership to those interested in transcriptional control and 3D genome architecture.
- **Major strengths** The manuscript tackles a complex, multi-scale problem with a combination of biophysical simulation and experimental data. The authors explicitly test prevailing models and identify their limitations, particularly the failure of unidirectional extrusion from the recombination center to explain distal VH usage. The proposal that Eμ acts as a bidirectional blocker is novel and testable. The inclusion of H3K27ac-mediated interactions adds a layer of biological realism that goes beyond purely structural models. The model's ability to predict recombination patterns of large genomic inversions is a strong point, as it provides an independent test of the underlying principles.
- **Major Concerns** The major concerns are detailed below. The most significant issues are the lack of quantitative validation, the absence of sensitivity analyses, and the reliance on unpublished or inaccessible data for key model parameters.
- **Minor Comments** Several minor issues are listed below, primarily related to clarity, terminology, and the need for additional methodological detail.
- **Technical failings that need to be addressed before the case is established** The primary technical failing is the absence of a rigorous, quantitative comparison between simulated and experimental data. The manuscript states qualitative agreement but does not provide statistical measures (e.g., correlation coefficients, root-mean-square deviations) for contact maps or VH usage profiles. Additionally, the model's sensitivity to key parameters, such as cohesin processivity, loading rate, and the strength of H3K27ac interactions, is not explored. Without this, it is unclear whether the proposed principles are uniquely sufficient or merely one of many possible explanations.
- **Assessment against Nature-style criteria**  
  - **Originality** High. The combination of cohesin loading throughout the locus, bidirectional Eμ blocking, and H3K27ac-mediated interactions is a novel synthesis that challenges simpler unidirectional scanning models.  
  - **Scientific importance** High. Understanding how chromatin architecture enables diverse antigen receptor generation is a central question in adaptive immunity. The principles proposed may apply to other antigen receptor loci and to long-range enhancer-promoter communication generally.  
  - **Interdisciplinary readership** Moderate to high. The topic bridges immunology, chromatin biology, and computational biophysics. The conceptual framework should be accessible to a broad audience, but the technical details of the simulations may be challenging for non-specialists.  
  - **Technical soundness** Currently not fully established. The simulation approach is based on a published framework, but the specific implementation, parameter choices, and validation metrics are not fully described or quantified in the provided text.  
  - **Readability for nonspecialists** The Introduction and Discussion are well-written and accessible. The Results section, however, relies heavily on terminology and concepts from polymer physics and Hi-C analysis that may be difficult for readers without a computational background. A more explicit explanation of key terms and metrics would improve accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework is compelling and the work addresses an important problem. However, the current manuscript does not provide sufficient quantitative evidence to fully establish the proposed principles. A revised version with detailed model validation, sensitivity analyses, and accessible presentation of key results would be necessary to support publication in a high-impact journal.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the model "correctly predicted rearrangement patterns of wild type and mutated Igh alleles, including large-scale genomic inversions."
- **Evidence pointer** Results section, "Structure and rearrangements of genomic inversions"; Figures 5A–5E (not provided)
- **Concern** The manuscript states that simulated VH usage profiles "closely mimicking experimental results" and "closely recapitulating experimental observations," but no quantitative comparison is shown. The text does not provide correlation coefficients, error metrics, or statistical tests comparing simulated and experimental VH usage frequencies. Without these, the claim of "correctly predicted" is not substantiated. The figures that would show this comparison are not available for review.
- **Why it matters** The central claim of the paper is that the model accurately recapitulates and predicts experimental recombination patterns. If the agreement is only qualitative, the model's predictive power is not established. A quantitative comparison is essential to demonstrate that the model captures the key features of VH usage and to rule out the possibility that the agreement is coincidental or driven by overfitting.
- **Resolution test** Provide quantitative metrics of model fit for all comparisons between simulated and experimental data. This should include, at minimum, correlation coefficients and confidence intervals for VH usage profiles, and a comparison of contact map similarity (e.g., using the stratum-adjusted correlation coefficient or similar metric). For the inversion predictions, provide a statistical test of whether the simulated usage patterns match the experimental data within expected noise.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors propose that "Eμ enhancer was best modeled as a bi-directional loop extrusion blocker though it does not bind CTCF."
- **Evidence pointer** Results section, "Eμ is a bidirectional blocker of cohesin extrusion"; Figures 2A–2I and S2 (not provided)
- **Concern** The conclusion that Eμ is a bidirectional blocker is based on the model's ability to recapitulate the fine structure of the 3' Igh domain. However, the manuscript does not describe how alternative models (e.g., Eμ as a unidirectional blocker, a pause site, or a barrier with variable strength) were tested and ruled out. The text mentions that modeling Eμ as a unidirectional blocker or non-blocking element "failed to recapitulate WT structure," but the criteria for "failure" are not defined. No quantitative comparison of model variants is provided.
- **Why it matters** The bidirectional blocking property of Eμ is a novel and important claim. If the evidence is only that one model variant fails qualitatively, the conclusion is not robust. A systematic exploration of alternative models, with quantitative comparison to experimental data, is necessary to support this claim.
- **Resolution test** Perform a systematic parameter sweep and model comparison, testing Eμ as a unidirectional blocker, bidirectional blocker, and non-blocking element. Provide quantitative metrics (e.g., contact map correlation) for each model variant and demonstrate that the bidirectional blocker is significantly better than the alternatives. Describe the criteria used to define "failure" of a model.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "utilization of VH genes to obtain maximum diversity required both widespread cohesin loading as well as long-range associations between H3K27ac-marked regions."
- **Evidence pointer** Results section, "Distal VH utilization"; Figures 4A–4D and S4C–S4D (not provided)
- **Concern** The model incorporates H3K27ac-mediated interactions as an additional constraint, but the manuscript does not describe how these interactions are parameterized. The text states that "we added an additional constraint that directs any two regions with H3K27ac to associate with each other if they are brought into proximity by cohesin-mediated extrusion." The strength, range, and specificity of these interactions are not defined. It is unclear whether the model's success depends on fine-tuning these parameters or whether the conclusions are robust to reasonable variations.
- **Why it matters** The claim that H3K27ac interactions are essential for distal VH usage is a key finding. If the model's behavior is highly sensitive to the choice of interaction parameters, the conclusion may not be generalizable. A sensitivity analysis is needed to demonstrate that the model's predictions are robust.
- **Resolution test** Provide a detailed description of the H3K27ac interaction parameters and perform a sensitivity analysis, varying the interaction strength and range. Show that the model's predictions for VH usage remain consistent with experimental data across a reasonable parameter range. If the model is sensitive to these parameters, discuss the implications and justify the chosen values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "Simulations that best recapitulated experimental data on locus structure and recombination of Igh alleles identified three novel chromatin folding principles."
- **Evidence pointer** STAR Methods, "Igh locus simulations"
- **Concern** The methods section describes the simulation framework but lacks critical details for reproducibility. The number of cohesins is fixed at six, but the loading positions, initial conditions, and the criteria for determining "best recapitulated" are not fully specified. The process by which the authors arrived at the final model parameters is not described. The code is available on GitHub, but the specific version and input files are not referenced.
- **Why it matters** For a computational study, reproducibility is essential. Without a complete description of the model parameters, initialization, and fitting procedure, other researchers cannot replicate the results or test alternative hypotheses.
- **Resolution test** Provide a complete description of the simulation protocol, including all parameters, initialization procedures, and the fitting/optimization process. Reference the specific version of the polychrom code and provide input files or a configuration script that would allow others to reproduce the simulations.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "Our findings provide a conceptual framework to understand chromatin folding principles that enable antibody diversity and reveal mechanisms of long-range genome communication."
- **Evidence pointer** Discussion section
- **Concern** The broader implications for "long-range genome communication" are stated but not developed. The manuscript does not discuss how the proposed principles might apply to other genomic contexts, such as enhancer-promoter interactions at other loci, or how they might be tested experimentally. The discussion of the three principles is focused on the Igh locus, and the generalizability is asserted rather than argued.
- **Why it matters** The claim of broader relevance is part of the paper's significance. If the principles are truly general, the authors should provide a more detailed argument for why they expect them to apply elsewhere and suggest specific experimental tests. Without this, the broader significance is overstated.
- **Resolution test** Expand the Discussion to address the generalizability of the three principles. Provide specific predictions that could be tested at other loci or in other cell types. Discuss potential exceptions or limitations to the proposed principles.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Results section, "Cohesin loading throughout the Igh locus recapitulates long-range chromatin structure"
- **Issue** The term "stripe" is used to describe features in Hi-C contact maps, but it is not defined for readers who may not be familiar with Hi-C data analysis. A brief explanation of what a "stripe" represents in a contact map would improve accessibility.
- **Required correction** Add a brief definition or explanation of "stripe" in the context of Hi-C contact maps, either in the Introduction or when the term is first used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods
- **Evidence pointer** STAR Methods, "Igh locus simulations"
- **Issue** The description of the simulation steps is brief. The text states that simulations were performed for 20,000 time steps, but it is unclear how the system was equilibrated and whether the first 10,000 steps were discarded as burn-in. The contact map was generated from time step 10,000, but the VH usage was calculated between steps 10,000 and 20,000. This distinction is not explained.
- **Required correction** Clarify the simulation protocol, including any equilibration period, and explain why contact maps were generated from a single time point while VH usage was averaged over a time window.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Resource Availability and Data and code availability sections
- **Issue** The Data and code availability section is listed but not described in the provided text. The manuscript states that code is available on GitHub, but the specific repository and version are not mentioned in the text.
- **Required correction** Provide the specific GitHub repository URL and version information for the polychrom code and any custom scripts used in the analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Model validation
- **Evidence pointer** Results section, "Proximal VH utilization in rearrangements"
- **Issue** The manuscript states that the model "reproduced recombination frequencies of only the five closest VH gene segments," but no statistical measure of agreement is provided. It is unclear how "reproduced" is defined and whether the agreement is within experimental error.
- **Required correction** Provide a quantitative measure of agreement between simulated and experimental VH usage for the proximal gene segments, such as a correlation coefficient or a chi-squared statistic.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure references
- **Evidence pointer** Results section, "Eμ is a bidirectional blocker of cohesin extrusion"
- **Issue** The text refers to Figures 2G, 2H, and 2I to illustrate the proposed loop extrusion events, but the figures are not provided. The text should briefly describe what is shown in these panels to help the reader understand the model.
- **Required correction** Add a brief description of the model schematics in Figures 2G–2I in the text.

## Risk / unsupported claims
- The claim that the model "correctly predicted rearrangement patterns of wild type and mutated Igh alleles" is unsupported by quantitative evidence in the provided text.
- The claim that Eμ is a bidirectional blocker is not fully supported, as alternative models were not systematically tested and compared.
- The claim that H3K27ac interactions are essential for distal VH usage is not supported by a sensitivity analysis.
- The statement that "a 4-fold increase in cohesin residence time was sufficient to generate both a contracted Igh locus and an extended 3'CBE stripe" is presented without quantitative comparison to experimental data.
- The broader implications for "long-range genome communication" are asserted but not developed or supported with specific predictions or examples.
- The manuscript's reliance on unpublished data (e.g., "unpublished observation" regarding Brd4 colocalization) makes certain claims unverifiable from the provided material.