## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary text sections
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and reporting completeness
- **Shared manuscript claim summary** The authors propose EiRA, a multimodal protein language model built on ESM3-small, with two-stage post-training (domain-adaptive masking and binding site-informed preference optimization) to design biomolecule-binding proteins. They claim state-of-the-art performance across 8 test sets covering 6 biomolecule types, improved representation learning for downstream tasks, mitigation of repetitive generation, DNA-conditioned binder design, and experimental validation including expression, purification, and SPR-confirmed binding.
- **Visible evidence base** Abstract, main text results sections, methods descriptions, supplementary text S1-S4, figure references (Fig. 1-7, Fig. S1-S12), tables referenced (Tables 1-3, S1-S6)
- **Missing materials affecting confidence** Figures and tables themselves are not provided, only referenced. No supplementary figures or tables content is visible. No code or data repository contents are accessible. No detailed statistical analysis or error bars are shown. No sequence-level examples of designed proteins are provided.

## Reviewer
- **Overall assessment** This manuscript presents a potentially valuable contribution to the field of protein design by adapting a multimodal protein language model for biomolecule-binding protein generation. The two-stage post-training strategy is conceptually sound and the breadth of evaluation is commendable. However, the current manuscript has several critical gaps that prevent full assessment of the claims. The most significant issues are the lack of visible figures and tables, incomplete methodological details for the preference optimization, unclear baseline comparisons, and insufficient experimental validation to support the strong claims of functional utility. The "one-shot" Glucagon binder result is promising but requires more rigorous characterization and comparison to existing methods. The manuscript would benefit from clearer presentation of the evaluation metrics, more detailed ablation studies, and a more critical discussion of limitations.

- **Who would be interested in the results, and why** Computational protein designers and engineers would be the primary audience, particularly those working on binder design and generative models. Researchers in the broader protein language model community would be interested in the post-training strategies and the finding that domain-adaptive training can improve both generation and representation. Experimental biologists working on peptide binders or DNA-binding proteins may find the validated examples useful. The work also has relevance for gene therapy and therapeutic protein development communities given the demonstrated Glucagon binder.

- **Major strengths** The two-stage post-training strategy is well-motivated and addresses a clear gap in adapting general protein language models to specific functional tasks. The evaluation is comprehensive, covering multiple biomolecule types and using multiple structural predictors to avoid model-specific bias. The identification and mitigation of repetitive generation in larger ESM3 models is an important practical finding. The integration of DNA sequence information via cross-attention extends the design paradigm beyond protein-only conditioning. The experimental validation, including expression, purification, and SPR, provides real-world evidence of manufacturability and function.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim "SOTA performance of EiRA, including structural confidence, diversity, novelty, and designability on 8 test sets across 6 biomolecule types"
- **Evidence pointer** Results section "EiRA generates biomolecular binder with higher fold confidence", Figures 2-3, Tables 1-2
- **Concern** The core performance claims are made without visible figures or tables. The manuscript references Figures 2 and 3 and Tables 1 and 2, but none of these are provided in the submitted material. Without seeing the actual data, it is impossible to verify the claimed performance improvements, the statistical significance of differences, or the comparability of evaluation conditions across methods. The claim of "SOTA" requires direct comparison to a comprehensive set of baselines, which cannot be assessed.
- **Why it matters** The central contribution of this work is the claimed performance improvement. Without visible evidence, the scientific case is not established. Reviewers and readers cannot evaluate whether the improvements are meaningful, whether they hold across all test sets, or whether the evaluation methodology is fair and consistent.
- **Resolution test** Provide all figures and tables with full data. Include error bars or confidence intervals for all metrics. Show direct head-to-head comparisons with all baselines under identical evaluation conditions. Report the number of independent generations, statistical tests used, and effect sizes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The authors propose a "binding site-informed preference optimization" combining DPO with SFT loss
- **Evidence pointer** Methods section "Binding site-informed preference optimization", Equations 1-3
- **Concern** The preference optimization methodology is described at a high level but lacks critical details. The equations are referenced but not shown. The construction of preference pairs uses a "multi-stage filtering protocol" with dynamic pTH thresholds, but the rationale for specific parameter choices (p, M, q values) is not explained. The selection of "preferred" and "dispreferred" sequences based on pTM scores alone may not capture functional binding ability. The interaction between the DPO loss and SFT loss, and how the weight parameter a was chosen, is not discussed. The computational cost of generating 30 variants per prompt across the full training set is not reported.
- **Why it matters** The preference optimization is a key novel contribution. Without full methodological details, the approach cannot be reproduced or compared to alternative strategies. The choice of pTM as the sole reward signal is particularly concerning, as pTM measures global structural confidence rather than binding interface quality.
- **Resolution test** Provide the full equations with all terms defined. Justify the choice of pTM as reward signal and discuss alternatives. Report sensitivity analysis for key hyperparameters (a, b, thresholds). Provide computational cost estimates. Discuss potential failure modes of the preference optimization.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim "one-shot design of a Glucagon peptide binder with SPR-confirmed micromolar affinity" and "100% success rate in expression (20/20) and purification (10/10)"
- **Evidence pointer** Results sections "EiRA generates highly divergent mutants" and "EiRA generates new Glucagon binder", Figures 7, S12
- **Concern** The experimental validation is presented with very limited detail. For the TnpB and DNA-binding protein variants, only expression and purification are shown, with no functional assays. The claim of "100% success rate" is based on a small sample and lacks statistical power. For the Glucagon binder, only one binder is reported with a single Kd value. No negative controls, no comparison to binders designed by other methods, no binding kinetics analysis beyond the Kd, and no specificity testing against unrelated peptides are shown. The SPR methodology is described in only one sentence in Supplementary Text S3.
- **Why it matters** The experimental validation is the strongest evidence for real-world utility. The current level of detail is insufficient to assess whether the designed proteins are truly functional or whether the results are reproducible. The lack of functional assays for the DNA-binding proteins is particularly concerning given the claims of DNA-binding ability.
- **Resolution test** Provide full experimental details including protein sequences, expression conditions, purification yields, and quality control. For the Glucagon binder, show full SPR sensorgrams, kinetic analysis (ka, kd), specificity controls, and comparison to known Glucagon binders. For DNA-binding proteins, include functional assays such as electrophoretic mobility shift assays or binding affinity measurements. Report replicate measurements and statistical analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Baseline comparisons
- **Claim pointer** The authors claim EiRA outperforms "ESM3 (including small/medium/large versions) and RFdiffusion+ProteinMPNN"
- **Evidence pointer** Results section "EiRA generates biomolecular binder with higher fold confidence", Figure 3
- **Concern** The comparison to RFdiffusion+ProteinMPNN is mentioned but the evaluation conditions are not described. It is unclear whether the same prompts were used, whether the same number of sequences were generated, whether the same structural predictors were applied, and whether the comparison is apples-to-apples. The authors note EiRA is inferior to RFdiffusion on PPI and MDBP test sets but do not discuss why or what this means for the overall claims. The comparison to ESM3l and ESM3m is complicated by the repetitive generation issue, which may unfairly penalize these models.
- **Why it matters** The claim of superiority over existing methods is a key selling point. If the comparison conditions are not fair or are not described, the claim cannot be verified. The acknowledged inferiority on some test sets needs more discussion.
- **Resolution test** Describe the exact evaluation protocol for all baselines. Ensure identical prompts, generation counts, and evaluation pipelines. Discuss the implications of the test sets where EiRA underperforms. Consider whether the repetitive generation issue in ESM3l/m can be addressed through post-processing rather than penalizing the model.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Representation learning claims
- **Claim pointer** The authors claim "EiRA provides a better characterization for biomolecular-binding proteins than generic model, thereby improving the predictive performance of various downstream tasks"
- **Evidence pointer** Results section "Representation learning for downstream prediction task", Figure 5, Table 3
- **Concern** The downstream task evaluation is described but the specific datasets, evaluation protocols, and baselines are not fully detailed. The improvements reported are modest (1.39-6.33% AUPR improvements) and it is unclear if these are statistically significant. The choice of downstream tasks (DNA-binding, RNA-binding, ATP-binding prediction) is reasonable but the relationship between improved representation and improved generation is not established. The authors do not discuss whether the improved representations come at a cost to general protein representation quality.
- **Why it matters** The dual benefit claim (generation and representation) is interesting but requires more rigorous validation. If the representation improvements are marginal or not statistically significant, the claim should be moderated.
- **Resolution test** Provide full details of downstream task datasets, train/test splits, and baselines. Report statistical significance tests. Show that improvements are consistent across multiple random seeds. Discuss potential trade-offs between generation and representation quality.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "systemic evaluation" which should be "systematic evaluation". The abstract also uses "EiRAD" without defining it as the DPO-enhanced version of EiRA.
- **Required correction** Fix the typo and define EiRAD in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Data availability
- **Evidence pointer** Data Availability section
- **Issue** The authors state data and code are available at GitHub and HuggingFace, but the specific repository structure, model checkpoint sizes, and hardware requirements for inference are not described. The training configuration files are not visible.
- **Required correction** Provide a detailed README with model card information, inference examples, and hardware requirements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, all evaluation sections
- **Evidence pointer** Results sections
- **Issue** No confidence intervals, standard deviations, or statistical tests are reported for any of the computational evaluations. The number of independent generation runs is not stated.
- **Required correction** Report mean and standard deviation across at least 3 independent generation runs. Apply appropriate statistical tests for comparing methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The introduction cites several protein design methods but does not discuss recent advances in protein language models for design (e.g., ESM3 variants, ProGen2, etc.) in sufficient depth. The discussion of challenges in protein design is somewhat generic.
- **Required correction** Expand the literature review to include recent protein language model-based design methods and discuss how EiRA differs from and improves upon these approaches.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** All figures
- **Evidence pointer** Figure references throughout
- **Issue** Figures are referenced but not visible. Based on the text descriptions, it is unclear whether the figures include appropriate labels, legends, and statistical annotations.
- **Required correction** Ensure all figures are self-contained with clear labels, legends, and statistical annotations.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The term "universal biomolecules-binding protein design" is used throughout but is not clearly defined. Does "universal" mean the model can handle all biomolecule types, or that it is a general-purpose design tool?
- **Required correction** Define "universal" in the context of this work and clarify the scope of biomolecule types covered.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Experimental details
- **Affected element** Supplementary Text S2-S4
- **Evidence pointer** Supplementary Text S2-S4
- **Issue** The western blot, SPR, and MD simulation protocols are described briefly. Key parameters such as temperature, buffer composition, and analysis software versions are missing or incomplete.
- **Required correction** Provide complete experimental protocols with all relevant parameters.

## Risk / unsupported claims
- The claim of "SOTA performance" cannot be evaluated without visible figures and tables showing comparisons to baselines
- The "one-shot" Glucagon binder claim is based on a single example with no comparison to existing Glucagon binders or other design methods
- The "100% success rate" for expression and purification is based on a small sample size and lacks statistical power
- The claim that EiRA "provides a better characterization for biomolecular-binding proteins" is supported by modest improvements in downstream tasks that may not be statistically significant
- The claim that EiRA "decouples structural integrity from sequence homology" is based on limited examples and requires more systematic validation
- The DNA-binding ability of designed proteins is claimed based on MD simulations and AF3 predictions, but no experimental binding assays are shown for these proteins
- The mitigation of repetitive generation is described qualitatively without quantitative metrics comparing repetition rates before and after the proposed interventions