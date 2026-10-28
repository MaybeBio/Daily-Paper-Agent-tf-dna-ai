## Review setup
- **Input scope** Full manuscript text including abstract, main text, results, discussion, methods, and supplementary information descriptions
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and significance of the reported findings
- **Shared manuscript claim summary** The authors present InstructNA, a framework that combines nucleic acid large language models (NA-LLMs) with high-throughput SELEX (HT-SELEX) data to enable de novo design of functional nucleic acids (FNAs), specifically transcription factor-binding DNA and protein-binding aptamers, without relying on structural information. The framework reportedly generates sequences with enhanced binding functionality and high sequence diversity compared to traditional HT-SELEX.
- **Visible evidence base** Main text figures (Fig. 1, Fig. 2), Extended Data Figures 1-3, Supplementary Figures 1-20, Supplementary Tables 1-6, and Supplementary Notes 1-11
- **Missing materials affecting confidence** Supplementary figures, tables, and notes are referenced but not provided in the submitted material. Source data files are mentioned but not accessible. This limits full verification of methodological details and statistical analyses.

## Reviewer

- **Overall assessment** The manuscript presents a potentially valuable contribution to the field of functional nucleic acid design by integrating NA-LLMs with HT-SELEX data. The core idea of using a domain-adapted language model with Bayesian optimization in latent space is conceptually interesting and timely. However, several technical concerns and gaps in the evidence base prevent full confidence in the claims as currently presented. The experimental validation is limited to two protein targets, and the comparison against existing methods is incomplete. The manuscript would benefit from clearer articulation of the novelty relative to existing generative approaches and stronger statistical evidence for the claimed improvements.

- **Who would be interested in the results, and why** Researchers in nucleic acid engineering, aptamer development, computational biology, and machine learning applied to biological sequence design would find this work relevant. The framework addresses a recognized bottleneck in aptamer discovery, and the integration of language models with experimental screening data could interest groups working on generative models for biomolecules. The potential clinical and diagnostic applications of aptamers broaden the appeal to translational research communities.

- **Major strengths** The conceptual integration of NA-LLMs with HT-SELEX data is a timely and potentially impactful approach. The demonstration of generating aptamers with improved binding affinity over traditional HT-SELEX candidates, particularly the identification of G1L with a KD of 12.9 nM compared to the best HT-SELEX candidate at 23.1 nM, is encouraging. The framework's flexibility in accommodating different NA-LLMs (DNABERT, Evo1, Nucleotide Transformer) is a practical advantage. The inclusion of structural analysis and molecular dynamics simulations adds depth to the validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that InstructNA generates "100% and 200% more strong aptamer binders for two protein targets" compared to traditional HT-SELEX.
- **Evidence pointer** Fig. 2b,c; Supplementary Tables 3-6
- **Concern** The claim of generating more strong binders is based on only two protein targets (LOX1 and CXCL5). For LOX1, 4 out of 10 generated aptamers are strong binders versus 2 out of 10 from HT-SELEX. For CXCL5, 3 out of 10 versus 1 out of 10. While these results are positive, the sample size is very small, and the statistical significance of these differences is not established. The manuscript does not report confidence intervals or statistical tests for these comparisons. Additionally, the selection of only the top 10 HT-SELEX candidates for comparison may not represent the full distribution of HT-SELEX performance.
- **Why it matters** The central claim of improved performance over existing methods rests on this comparison. Without statistical rigor and broader validation across more targets, the generalizability of the claimed improvement cannot be assessed.
- **Resolution test** Provide statistical analysis (e.g., Fisher's exact test or confidence intervals) for the proportion of strong binders. Validate on additional protein targets (at least 3-5 more) with diverse structural and biochemical properties. Report the full distribution of KD values for all tested aptamers, not just the top performers.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The manuscript claims that InstructNA enables "de novo design of FNAs without relying on structural information" and that the HC-HEDO algorithm enables "directed evolution of FNAs in a continuous latent space."
- **Evidence pointer** Methods section "HC-HEDO in InstructNA"; Supplementary Note 6
- **Concern** The description of the HC-HEDO algorithm is incomplete. The manuscript states that HEDO performs global optimization and that HC restricts the search space, but the specific implementation details are insufficient. Key parameters such as the number of iterations, the acquisition function used, the kernel choice for the Gaussian process surrogate, and the handling of heteroscedastic noise are not fully specified. The stopping criteria and convergence properties are not discussed. The comparison with HEDO alone (without HC) is mentioned but the results are only shown in Extended Data Fig. 2b and Supplementary Fig. 8, which are not accessible in the provided material.
- **Why it matters** Reproducibility is a fundamental requirement for computational methods. The HC-HEDO algorithm is a core contribution of the paper, and without complete methodological details, other researchers cannot implement or build upon the approach.
- **Resolution test** Provide complete pseudocode for HC-HEDO, including all hyperparameters, acquisition function details, and convergence criteria. Include ablation studies showing the contribution of each component (HC, heteroscedastic noise handling, evolutionary strategy). Make the code publicly available with documentation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Comparative evaluation
- **Claim pointer** The manuscript claims that InstructNA outperforms "the existing state-of-the-art model" (RaptGen) in generating TF-binding DNA with higher binding specificity.
- **Evidence pointer** Fig. 1b,c; Extended Data Fig. 1; Supplementary Fig. 10
- **Concern** The comparison with RaptGen is limited to binding specificity scores computed using the 8mer_sum algorithm, which is a computational prediction rather than an experimental measurement. While this is a reasonable first-pass evaluation, the manuscript does not experimentally validate the TF-binding DNA sequences generated by InstructNA. The claim of "higher binding specificity" is therefore only demonstrated in silico. Additionally, the comparison with other generative approaches (e.g., AptaDiff, or generative adversarial networks for aptamers) is not included.
- **Why it matters** The field of generative models for nucleic acids is rapidly evolving, and claims of state-of-the-art performance require comprehensive benchmarking against multiple existing methods. Experimental validation of predicted binding specificity would substantially strengthen the claims.
- **Resolution test** Include experimental validation (e.g., electrophoretic mobility shift assays or high-throughput binding assays) for a subset of the generated TF-binding DNA sequences. Expand the comparison to include other generative models. Report performance metrics beyond binding specificity, such as sequence diversity, structural plausibility, and synthesis success rate.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports KD values for aptamers with "mean ± s.d. (n = 3 independent experiments)" and claims that G1L and G2L exhibit "higher binding affinity than the original T1L and T2L."
- **Evidence pointer** Fig. 2b-e; Supplementary Figs. 11-14
- **Concern** The statistical comparison of KD values between generated and HT-SELEX aptamers is not described. With n = 3, the manuscript should report whether the differences in KD values are statistically significant. The overlap in error bars between G1L (12.9 ± ? nM) and T1L (23.1 ± ? nM) is not shown with actual values. Additionally, the manuscript does not report the variability across different batches of experiments or the reproducibility of the SPR measurements.
- **Why it matters** The claim of improved binding affinity is a key result. Without proper statistical testing, the reader cannot determine whether the observed differences are meaningful or within experimental noise.
- **Resolution test** Report the full statistical analysis including p-values or confidence intervals for all KD comparisons. Include the raw SPR data or representative sensorgrams for all tested aptamers. Describe the error model and how variability was assessed.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The manuscript claims that InstructNA is "applicable for generating any type of FNA, provided that its HT-SELEX data are available and its functionality can be measured."
- **Evidence pointer** Discussion section; Results section
- **Concern** The demonstration is limited to TF-binding DNA and two protein-binding aptamers. The claim of general applicability to "any type of FNA" is not supported by the evidence presented. The manuscript does not discuss potential limitations for RNA aptamers, ribozymes, or DNAzymes, which may have different sequence constraints and structural requirements. The framework's dependence on HT-SELEX data availability is acknowledged but not critically examined.
- **Why it matters** Overgeneralization of the framework's applicability could mislead readers about its practical utility. A more measured claim with explicit discussion of limitations would be more scientifically accurate.
- **Resolution test** Either provide additional demonstrations on diverse FNA types or temper the claim to reflect the demonstrated scope. Discuss specific challenges for different FNA classes and how the framework might be adapted.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "100% and 200% more strong aptamer binders" which is an unusual way to express the improvement. This phrasing could be misinterpreted as a 100% and 200% increase in binding affinity rather than in the number of strong binders.
- **Required correction** Rephrase to "two-fold and three-fold more strong aptamer binders" or "100% and 200% more strong aptamer binders compared to HT-SEASON" with explicit clarification that this refers to the count of strong binders.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods section "Tokenization in DNABERT (3-mers)"
- **Issue** The description of tokenization is overly verbose and includes general background on language modeling that is not necessary for the methods section. The specific details of how the 3-mer tokenization is applied to the aptamer sequences (e.g., handling of sequence length variability, padding strategy) are not described.
- **Required correction** Condense the general background and provide specific implementation details for the tokenization as applied to the aptamer sequences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "SPR experiments"
- **Issue** The SPR experimental details are incomplete. The manuscript does not specify the concentration range of aptamers tested, the number of concentration points, the fitting model details beyond "1:1 binding model," or the quality metrics for the fits (e.g., chi-square values).
- **Required correction** Provide complete SPR experimental parameters including concentration ranges, number of replicates, and fit quality metrics.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results
- **Evidence pointer** Fig. 1c
- **Issue** The scatter plot in Fig. 1c shows relative binding specificity versus maximum sequence similarity, but the interpretation of the "dashed line" indicating the highest relative binding specificity among the top ten HT-SEASON sequences is not clearly explained in the text. The reader is left to infer the significance of this threshold.
- **Required correction** Add explicit text explaining the significance of the dashed line and what it represents for the comparison between InstructNA and RaptGen.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Fig. 2
- **Evidence pointer** Fig. 2b,c
- **Issue** The figure uses symbols (# and *) to denote weaker binders and no measurable binding, but the exact KD thresholds for these categories are not defined in the text or figure legend.
- **Required correction** Define the KD thresholds for "strong," "weak," and "no measurable binding" in the figure legend or methods.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address potential failure modes or limitations of the approach. For example, what happens when the HT-SEASON data quality is poor, or when the target protein has no known aptamers? How does the framework handle sequences with modified nucleotides?
- **Required correction** Add a paragraph discussing limitations, failure modes, and potential mitigation strategies.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "Docking and unrestrained MD simulations"
- **Issue** The MD simulation parameters are described but the equilibration protocol is not fully specified. The manuscript states "heated to 300 K under constant volume" and "50-ps constant-pressure relaxation" but does not describe the heating schedule, the thermostat coupling parameters, or the barostat parameters.
- **Required correction** Provide complete MD simulation parameters including heating schedule, thermostat and barostat settings, and the number of steps for each phase.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results
- **Evidence pointer** Results section "Architecture of InstructNA"
- **Issue** The description of the five-step framework is clear, but the relationship between the "domain-adapted FNA-LLM" and the "lightweight decoder" is not fully explained. Specifically, how the decoder is trained on top of the frozen encoder and how the two components interact during generation could be clarified.
- **Required correction** Add a brief explanation of how the encoder and decoder interact during the generation and optimization process.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods section "Preparation of HT-SEASON data of TF-binding DNA for model training"
- **Issue** The data preprocessing steps are described but the quality control criteria for the HT-SEASON data are not specified. For example, what was the minimum read count threshold for including a sequence? How were sequencing errors handled?
- **Required correction** Provide detailed quality control criteria for the HT-SEASON data preprocessing.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract does not mention the limitations of the study or the need for further validation. Given the small number of targets tested, a brief caveat would be appropriate.
- **Required correction** Add a sentence acknowledging the limited number of targets tested and the need for broader validation.

## Risk / unsupported claims
- The claim that InstructNA is "applicable for generating any type of FNA" is not supported by the evidence, which only demonstrates TF-binding DNA and two protein-binding aptamers.
- The claim of "100% and 200% more strong aptamer binders" is based on a very small sample size (2 targets) without statistical testing.
- The claim that InstructNA generates sequences with "higher binding specificity" for TF-binding DNA is only supported by in silico predictions (8mer_sum scores), not experimental validation.
- The claim of "high sequence diversity" is not quantified with specific diversity metrics or compared against a baseline in the main text.
- The superiority of HC-HEDO over standard HEDO is claimed but the supporting data are only in supplementary materials not accessible for review.
- The manuscript claims "robustness" of InstructNA towards representation perturbations, but this is only tested through KDE-based perturbations, which may not capture all relevant perturbation types.
- The structural analysis of G1L and the claim of "a more intricate fold at the apical loop" is based on computational predictions (AlphaFold3 and MD simulations) without experimental structural validation.
- The claim that InstructNA "learns semantically rich, functionally relevant and robust representations" is partially supported by the correlation and classification analyses, but the functional relevance is only demonstrated for binding specificity, not for other functional properties of FNAs.

## Assessment against Nature-style criteria
- **Originality** The integration of NA-LLMs with HT-SEASON data for de novo FNA design is a novel contribution. While individual components (language models, Bayesian optimization, SEASON) are established, their combination in this framework is original. The HC-HEDO algorithm represents a methodological innovation, though its novelty relative to existing constrained optimization approaches needs clearer articulation.
- **Scientific importance** Functional nucleic acid design is a significant challenge with broad applications in diagnostics, therapeutics, and synthetic biology. If the framework's performance is robustly validated, it could substantially accelerate aptamer discovery and reduce the cost and time associated with experimental screening. The potential impact is high, but the current evidence base is too limited to fully establish this impact.
- **Interdisciplinary readership** The work bridges machine learning, nucleic acid chemistry, and molecular biology, and would appeal to researchers across these disciplines. The writing is generally accessible, though the methods section assumes familiarity with both language model architectures and SEASON protocols. The clinical and diagnostic applications of aptamers broaden the potential readership.
- **Technical soundness** The technical approach is sound in principle, but several concerns remain: the limited number of experimental targets, the lack of statistical testing for key comparisons, incomplete methodological details for HC-HEDO, and the absence of experimental validation for TF-binding DNA predictions. The computational analyses appear reasonable but cannot be fully verified without access to the supplementary materials.
- **Readability for nonspecialists** The abstract and introduction are accessible to a broad scientific audience. The results section is reasonably clear, though some figures require careful study. The methods section is dense and assumes significant background knowledge. The discussion could be improved by more explicitly addressing limitations and potential applications.

## Recommendation posture
**Supportive if technical concerns are resolved.** The core concept is promising and the preliminary results are encouraging, but the current evidence base is insufficient to fully establish the claims. The manuscript requires additional experimental validation, statistical rigor, and methodological detail before the case is fully established. I recommend major revision with the specific concerns outlined above addressed.