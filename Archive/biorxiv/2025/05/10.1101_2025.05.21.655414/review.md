## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided by the user
- **Assessment boundary** Scientific and technical evaluation of the manuscript's claims, methods, results, and presentation, based solely on the supplied text
- **Shared manuscript claim summary** The authors propose MORALE, a moment-alignment-based domain adaptation framework for cross-species transcription factor binding prediction. They claim it outperforms adversarial (gradient reversal) approaches in a two-species setting, improves human prediction accuracy beyond human-only training in a five-species transfer setting, preserves model interpretability, and is architecture-agnostic.
- **Visible evidence base** Abstract, Introduction, Methods (Sections 2.1–2.8), Results (Sections 3.1–3.3), Discussion, Conclusion, Data availability, Funding, Competing interests
- **Missing materials affecting confidence** Figures 1–6, Tables 1–2, Supplementary Tables 7–8, and all equations (including Equation 1 and 2) are referenced but not provided. Code repository is mentioned but not reviewed. No quantitative results (e.g., auPRC values, confidence intervals, statistical tests) are visible in the supplied text.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in regulatory genomics, namely cross-species generalization of TF binding prediction models. The proposed method, MORALE, is conceptually simple and builds on established moment alignment techniques. However, the provided text lacks all quantitative results, figures, and tables, making it impossible to evaluate the central claims of performance improvement, interpretability, or biological discovery. The methods section contains inconsistencies (e.g., two different deep learning frameworks, TensorFlow and PyTorch, are described for training) and some unclear passages. The claim of "frustratingly easy" domain adaptation is appealing but not substantiated without the missing evidence.
- **Who would be interested in the results, and why** Computational biologists and machine learning researchers working on sequence-to-function models, regulatory genomics, and cross-species prediction. The potential for a simple, architecture-agnostic domain adaptation method that improves cross-species TF binding prediction would be of interest to those developing deep learning models for genomics and those studying conserved regulatory grammar.
- **Major strengths** The problem is well-motivated and relevant. The proposed method is simple and does not require additional parameters or complex adversarial training, which is a practical advantage. The comparison against a gradient reversal layer baseline is appropriate. The multi-species setting is a valuable extension beyond typical two-species analyses.
- **Major Concerns** The absence of all figures, tables, and quantitative results is a critical limitation. The methods section contains inconsistencies and unclear descriptions. The claim of state-of-the-art performance is not verifiable from the supplied material. The interpretability claim is not supported by any visible analysis.
- **Minor Comments** The manuscript would benefit from clearer definitions of the moment alignment loss and its hyperparameter. The description of the multi-species data processing could be more detailed. The discussion of evolutionary conservation could be more nuanced given the observed deviations from phylogenetic expectations.
- **Technical failings that need to be addressed before the case is established** The lack of all quantitative results, figures, and tables. The inconsistency in deep learning frameworks (TensorFlow vs. PyTorch) in the methods. The unclear description of the moment alignment loss and its implementation.
- **Assessment against Nature-style criteria** Originality: The application of moment alignment to cross-species TF binding prediction is a reasonable extension of existing work, but the core idea is not novel. Scientific importance: The problem is important, and a simple, effective solution would be valuable, but the current evidence does not establish this. Interdisciplinary readership: The topic is of interest to both genomics and machine learning communities, but the presentation is too technical and lacks accessible summaries of the key findings. Technical soundness: The methods are not fully described, and the missing results prevent assessment of technical correctness. Readability for nonspecialists: The manuscript is written for a specialized audience and would benefit from clearer explanations of the domain adaptation concept and its significance.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript cannot be evaluated without the missing figures, tables, and quantitative results. The authors should be invited to resubmit a complete version.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim state-of-the-art performance, outperforming baseline and adversarial approaches across all TFs, and improved human prediction accuracy in the five-species setting.
- **Evidence pointer** Figures 2 and 5, Tables 1 and 2, location not provided
- **Concern** All quantitative results, including auPRC values, comparisons, and statistical assessments, are contained in figures and tables that are not provided in the supplied text. Without these, the central performance claims cannot be evaluated.
- **Why it matters** The core contribution of the manuscript is the claimed improvement in prediction performance. Without the actual numbers and visualizations, there is no evidence to support these claims.
- **Resolution test** Provide all figures and tables with clear axis labels, legends, and statistical annotations. Include exact auPRC values, confidence intervals, and significance tests where applicable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The methods section describes model training using both TensorFlow 2.18 and PyTorch 2.5.1, which is inconsistent.
- **Evidence pointer** Section 2.3, location not provided
- **Concern** The text states "All models were trained using TensorFlow 2.18" and then later "We train all models with PyTorch 2.5.1". This is contradictory and unclear which framework was actually used for which models.
- **Why it matters** Reproducibility is a fundamental requirement. The inconsistency in the described training framework undermines confidence in the methods and results.
- **Resolution test** Clarify which deep learning framework was used for each model and experiment. Ensure the methods section is internally consistent.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The MORALE loss is described as aligning first and second moments of sequence embeddings across domains, but the exact formulation is not fully specified.
- **Evidence pointer** Section 3.1, Equation 1, location not provided
- **Concern** The description of the moment alignment loss is incomplete. The equation is not provided, and the hyperparameter tuning is described without a clear definition of the loss function or its components.
- **Why it matters** The method is the central contribution. Without a precise mathematical definition, the method cannot be reproduced or fully understood.
- **Resolution test** Provide the full equation for the MORALE loss, define all variables, and explain how the hyperparameter is incorporated. Include a clear description of how the loss is computed in practice.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that MORALE preserves model interpretability and recovers canonical motifs with greater precision.
- **Evidence pointer** Figure 4, location not provided
- **Concern** The interpretability analysis, including motif discovery and comparison, is entirely contained in Figure 4, which is not provided. The text mentions "canonical motifs" and "greater precision" but no quantitative or qualitative evidence is visible.
- **Why it matters** Interpretability is a key claimed advantage. Without the motif analysis results, this claim is unsupported.
- **Resolution test** Provide Figure 4 with clear annotations, including motif logos, enrichment scores, and comparisons between models. Include quantitative measures of motif recovery precision.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that in the five-species transfer setting, MORALE improves human prediction accuracy beyond human-only training.
- **Evidence pointer** Figure 5, location not provided
- **Concern** The results of the five-species experiment are only summarized in text. The actual performance numbers, comparisons, and statistical significance are not visible.
- **Why it matters** This is a key result demonstrating the value of multi-species training with domain adaptation. Without the data, the claim cannot be assessed.
- **Resolution test** Provide Figure 5 with clear performance curves or bar plots, including error bars and statistical tests comparing MORALE to baselines.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1.2
- **Evidence pointer** Section 2.1.2, location not provided
- **Issue** The description of the automatic chromosome selection for validation and test sets is incomplete. The optimization problem is mentioned but not fully described.
- **Required correction** Provide the full optimization problem formulation and explain the constraints and objective clearly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5, location not provided
- **Issue** The definition of "differentially predicted site" is clear, but the threshold of 0.5 for the difference in outputs is arbitrary and not justified.
- **Required correction** Provide a rationale for the 0.5 threshold or perform a sensitivity analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.2
- **Evidence pointer** Section 3.2, location not provided
- **Issue** The text states "we exclude the target model as none of the source or source-adapted models come close to its performance." This is an important observation but is not quantified.
- **Required correction** Provide the actual performance gap between target and source/adapted models to support this statement.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.1.1
- **Evidence pointer** Section 2.1.1, location not provided
- **Issue** The data processing for the five-species dataset is described briefly, but details on alignment, peak calling, and filtering are not fully specified.
- **Required correction** Provide more details on the bioinformatics pipeline, including software versions and parameters.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1, location not provided
- **Issue** The notation for the moment alignment loss is introduced but not fully explained. The use of "b" for batch size and the estimation of moments is unclear.
- **Required correction** Define all notation clearly and explain how the moments are estimated from the background set.

## Risk / unsupported claims
- The claim of state-of-the-art performance is unsupported without the provided figures and tables.
- The claim of improved interpretability and motif recovery is unsupported without Figure 4.
- The claim that MORALE improves human prediction accuracy beyond human-only training in the five-species setting is unsupported without Figure 5.
- The claim that MORALE is "frustratingly easy" and architecture-agnostic is plausible but not fully demonstrated without a broader set of experiments.
- The statement that MORALE "reveals regulatory features conserved across mammals" is not supported by any visible analysis.
- The performance comparison between MORALE and GRL on repetitive elements (Table 2) is not assessable without the table.