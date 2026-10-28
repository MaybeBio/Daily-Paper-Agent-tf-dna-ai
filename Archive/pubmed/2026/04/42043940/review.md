## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, availability, data availability) as provided.
- **Assessment boundary** Scientific content, methodological soundness, validation evidence, and claims as presented in the provided text. No supplementary materials, figures, or tables were available for direct inspection.
- **Shared manuscript claim summary** The authors present BayesPI-FLY, a Bayesian neural network tool for de novo TF motif discovery that integrates DNA sequence and methylation data, claiming it recovers known methylation-associated TF-binding patterns and infers strand-specific associations.
- **Visible evidence base** Synthetic dataset validation (six datasets, 500-8000 sequences), real HTS data from K562 cell line (six TFs), performance comparisons with MEME, and parallel computation benchmarks. Specific figures and tables referenced but not provided.
- **Missing materials affecting confidence** All figures (Figs 1-4, Supplementary Figs S1-S5), Supplementary Methods, Supplementary Tables, and the actual software code/documentation. These are critical for verifying methodological details, validation results, and performance claims.

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful computational tool for integrating methylation data into TF motif discovery, building on a reasonable biophysical foundation. However, the current text lacks sufficient detail to fully evaluate the methodological novelty, validation rigor, and practical utility. The claims of recovering known patterns and inferring strand-specific associations are plausible but not fully substantiated without access to the referenced figures and supplementary materials. The writing is generally clear but contains some ambiguities in the methods section that need clarification.
- **Who would be interested in the results, and why** Researchers in computational biology, gene regulation, and epigenetics, particularly those studying TF-DNA binding in the context of DNA methylation. The tool could be useful for analyzing matched ChIP-seq and WGBS datasets to explore methylation-sensitive TF binding across conditions.
- **Major strengths** 1) Addresses a relevant gap by integrating methylation data into motif discovery within a biophysical framework. 2) The Bayesian neural network approach with two-level inference is a principled methodological choice. 3) Validation on both synthetic and real data, including multiple TFs with known methylation preferences, is a reasonable strategy. 4) The tool is implemented in C with Python parallelization, suggesting practical efficiency.
- **Major Concerns** 1) The manuscript lacks quantitative results and statistical measures in the text, making it impossible to assess the strength of the validation. 2) The novelty relative to existing methods (e.g., MethMotif, ProBound) is not clearly articulated. 3) The strand-specific findings are presented without sufficient mechanistic or statistical justification. 4) The methods section has some unclear notation and incomplete derivations that hinder reproducibility.
- **Minor Comments** 1) The abstract is somewhat vague about the specific outputs and performance metrics. 2) The introduction could better position the work against recent advances in methylation-aware motif discovery. 3) The discussion is largely speculative about applications without concrete examples or pilot results. 4) Some terminology (e.g., "feature weighted") is not clearly defined.
- **Technical failings that need to be addressed before the case is established** 1) Lack of quantitative validation results in the main text. 2) Incomplete methodological details for the Bayesian inference and neural network architecture. 3) No clear comparison of runtime or accuracy improvements over existing tools beyond a brief mention. 4) The strand-specific claims require statistical support and biological interpretation.
- **Assessment against Nature-style criteria** **Originality**: Moderate. The integration of methylation into a Bayesian neural network for motif discovery is a reasonable extension of prior work, but the core idea is not entirely novel given existing methylation-aware tools. **Scientific importance**: Moderate. The tool could be valuable for the epigenetics community, but the demonstrated impact is limited without broader applications or novel biological insights. **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to computational biologists and epigenetics specialists, with limited appeal to a broader scientific audience. **Technical soundness**: Partially assessable. The theoretical framework is plausible, but the lack of detailed validation and methodological clarity prevents full assessment. **Readability for nonspecialists**: Adequate but could be improved. The text is generally clear, but the methods section is dense and assumes significant background knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The tool addresses a relevant problem and the approach is promising, but the current manuscript does not provide sufficient evidence to fully establish the claims. Major revisions are needed to provide quantitative validation, clarify methods, and strengthen the novelty argument.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** The abstract and results claim that BayesPI-FLY "can recapitulate known methylation-associated TF-binding patterns" and achieve accuracy improvements with increasing data size.
- **Evidence pointer** Results section, Figures 2-4, Supplementary Figures S1-S5 (not provided)
- **Concern** The main text provides no quantitative results, statistical measures, or error bars for the validation experiments. The accuracy percentages mentioned (e.g., 60%, 70%, 80%) are presented without confidence intervals, statistical tests, or comparison to baseline methods. The figures are referenced but not available for inspection, making it impossible to verify the claims.
- **Why it matters** Without quantitative evidence, the reader cannot assess whether the tool performs adequately or outperforms existing methods. The claim of "recapitulating known patterns" requires statistical support to be convincing.
- **Resolution test** Provide detailed quantitative results in the main text or supplementary materials, including accuracy metrics with confidence intervals, statistical comparisons to existing tools (e.g., MEME, ProBound), and clear figure legends that can be evaluated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The methods describe a "two-level inference" process and a "Bayesian neural network" approach, but the details are incomplete.
- **Evidence pointer** Methods section, equations (7) to (39), Supplementary Methods (referenced but not provided)
- **Concern** The derivation of the Bayesian framework is presented in a condensed form with several equations that are not fully explained. The neural network architecture, activation functions, initialization, and training procedure are not described in sufficient detail. The role of the hyperparameters α and β and their update rules are mentioned but the underlying assumptions and derivations are not fully transparent. The notation is sometimes ambiguous (e.g., the use of W1, W2, b1, b2 is not consistently defined).
- **Why it matters** Reproducibility is a core requirement for computational tools. Without a clear description of the model and training procedure, other researchers cannot implement or adapt the method.
- **Resolution test** Provide a complete and self-contained description of the model, including all equations, definitions, and algorithmic steps. Include pseudocode or a detailed algorithm box. Ensure that all symbols are defined and that the derivation is logically complete.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and comparison
- **Claim pointer** The introduction states that "few methods integrate both sequence information and methylation profiles into a unified framework," implying novelty.
- **Evidence pointer** Introduction section, references [14-18]
- **Concern** The manuscript does not clearly differentiate BayesPI-FLY from existing methylation-aware motif discovery tools such as MethMotif, ProBound, or MeDeMo. The authors mention these tools but do not provide a systematic comparison of features, assumptions, or performance. The claimed novelty of "feature weighted" TF-DNA interaction is not clearly defined or contrasted with existing approaches.
- **Why it matters** For a new tool to be publishable, its unique contributions must be clearly articulated. Without a clear comparison, the reader cannot judge whether the tool offers significant advantages over existing methods.
- **Resolution test** Add a dedicated section comparing BayesPI-FLY with existing methods, highlighting specific differences in methodology, input data requirements, and output. Include benchmark comparisons on the same datasets where possible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Strand-specific claims
- **Claim pointer** The results claim to find "strand-dependent differences in the inferred methylation-binding associations" for CEBPG and ZBTB33.
- **Evidence pointer** Results section, Figures 3 and 4
- **Concern** The observation of strand-specific differences is presented as a finding, but the statistical significance and biological relevance are not discussed. The text notes that "BayesPI-FLY does not directly establish mechanistic strand-specific recognition," which is appropriate, but the finding is not contextualized with respect to known biology or potential artifacts.
- **Why it matters** Strand-specific effects could be biologically meaningful or could be an artifact of the model or data processing. Without further analysis or discussion, the claim is not well-supported.
- **Resolution test** Provide statistical tests for the strand differences, discuss potential sources of bias (e.g., read mapping, methylation calling), and relate the findings to known TF biology or propose follow-up experiments.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states the tool "quantitatively characterizes methylation effects at both single-nucleotide and motif levels," but the specific outputs (e.g., effect sizes, confidence intervals) are not described.
- **Required correction** Clarify what quantitative outputs the tool produces and how they are interpreted.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction and Methods
- **Evidence pointer** Introduction, Methods section
- **Issue** The term "feature weighted" is used but not explicitly defined. It is unclear whether this refers to a weighting of sequence features, methylation features, or both.
- **Required correction** Define "feature weighted" explicitly in the introduction or methods, and explain how it relates to the model equations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The data availability section lists accession numbers for ChIP-seq and WGBS data but does not specify the exact versions or processing pipelines used.
- **Required correction** Provide detailed data processing steps, including software versions and parameters, in the supplementary materials.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Performance claims
- **Affected element** Results, parallel computation
- **Evidence pointer** Results section, Supplementary Table S1
- **Issue** The claim that parallel computation reduces runtime by "more than 50%" is vague and lacks context (e.g., number of cores, dataset size).
- **Required correction** Provide specific runtime measurements for different numbers of processes and dataset sizes, and clarify the baseline for the 50% reduction.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section
- **Evidence pointer** Methods section, equations
- **Issue** The equations are presented without clear numbering or cross-referencing in the text, making it difficult to follow the derivation.
- **Required correction** Number all equations and refer to them explicitly in the text. Provide a table of symbols and definitions.

## Risk / unsupported claims
- The claim that BayesPI-FLY "can recapitulate known methylation-associated TF-binding patterns" is not quantitatively supported in the provided text.
- The claim of "strand-specific associations" is presented without statistical evidence or biological validation.
- The performance comparison with MEME is mentioned but not detailed, making it impossible to evaluate the claim of "higher prediction accuracy."
- The runtime reduction claim of "more than 50%" is not substantiated with specific data.
- The general applicability of the tool to "other omics data" is speculative and not demonstrated.
- The discussion of potential applications in cancer and disease contexts is entirely hypothetical and not supported by any results.