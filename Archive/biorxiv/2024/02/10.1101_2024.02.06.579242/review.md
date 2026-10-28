## Review setup
- **Input scope** Full manuscript text including abstract, background, results, discussion, conclusions, methods, and availability statements.
- **Assessment boundary** Scientific claims, methodological soundness, experimental design, and evidence quality as presented in the provided text. No external data or code verification performed.
- **Shared manuscript claim summary** The authors propose a nucleotide-level deep neural network (NLDNN) for transcription factor binding prediction within and across species, and introduce a dual-path adversarial training framework (NLDNN-AT) to improve cross-species performance by aligning domain spaces between human and mouse.
- **Visible evidence base** Results sections describe comparisons with competing methods across 18 TF binding datasets, variant effect prediction tasks, localization ability assessments, and adversarial training experiments. Figures referenced include Fig.1, Fig.2, Fig.3, Fig.4, Fig.5, Fig.6, and Supplementary Figures 1-12.
- **Missing materials affecting confidence** Figure panels and actual numerical results are not provided in the text. Supplementary figures and tables referenced but not included. No quantitative performance values, statistical significance tests, or error bars are visible. Code repository and data accession list mentioned but not verifiable from the manuscript text alone.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational genomics, namely cross-species prediction of TF binding, and proposes a reasonable architectural contribution in NLDNN plus an adversarial training strategy. The motivation is clear and the methodological framing is sensible. However, the evidence presented in the text is largely qualitative, with key quantitative results relegated to figures that are not available for inspection. Several claims about performance superiority and mechanism are made without sufficient visible support. The adversarial training framework is described but its novelty relative to existing domain adaptation approaches, particularly the GRL method cited, is not clearly delineated. The manuscript has potential but the current evidence base is insufficient to fully establish the central claims.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, TF binding prediction, and cross-species model transfer would be the primary audience. Researchers developing deep learning architectures for nucleotide-resolution genomic tasks would also find the NLDNN architecture of interest. The adversarial training framework for domain adaptation in genomics could attract those working on transfer learning across species or cell types.
- **Major strengths** The problem is well-motivated and practically important. The proposed NLDNN architecture is clearly described with architectural details. The use of multiple evaluation criteria beyond predictive performance, including variant effect prediction and localization ability, is commendable. The adversarial training framework is a sensible extension of existing domain adaptation ideas. The discussion of limitations, particularly regarding chromatin accessibility prediction and negative sample selection, shows scientific honesty.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality: moderate. The nucleotide-level architecture is not entirely novel given existing models like BPNet and FCNsignal, and the adversarial training approach borrows from GAN literature. The specific combination and application to cross-species TF binding has some novelty. Scientific importance: potentially high if the claims hold, as cross-species regulatory prediction is an open problem. However, the importance is not fully demonstrated without quantitative evidence. Interdisciplinary readership: the work sits at the intersection of deep learning and genomics, which has broad appeal, but the presentation assumes significant domain expertise. Technical soundness: the architecture descriptions are plausible, but the lack of visible quantitative results and statistical rigor undermines confidence. Readability for nonspecialists: the manuscript is dense and assumes familiarity with TF binding assays, deep learning architectures, and domain adaptation concepts. The abstract is accessible but the body would be challenging for nonspecialists.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that NLDNN performs better than competing methods in multiple prediction tasks, and that adversarial training improves cross-species prediction performance.
- **Evidence pointer** Results sections "The overall performance of NLDNN" and "Adversarial training can improve the performance of cross-species TF binding prediction", Figures 2, 6, Supplementary Figures 2, 10
- **Concern** The central performance claims are made without any visible quantitative results in the text. No numerical values for PR-AUC, Pearson correlation, or other metrics are provided. The figures that presumably contain these results are not available for inspection. Without actual numbers, statistical significance tests, or confidence intervals, the claims of superiority over competing methods cannot be evaluated.
- **Why it matters** The primary contribution of the manuscript is the claimed performance improvement. If the quantitative evidence is not presented or is weak, the core scientific contribution is not established.
- **Resolution test** Provide explicit numerical results in the text or tables, including performance metrics for all methods across all datasets, with measures of variance and statistical significance where appropriate.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological novelty
- **Claim pointer** The manuscript claims to design a "novel" Nucleotide-Level Deep Neural Network and a "dual-path framework for adversarial training" that improves cross-species prediction.
- **Evidence pointer** Methods sections "NLDNN" and "The framework of adversarial training", Background section
- **Concern** The novelty of NLDNN relative to existing nucleotide-level models such as BPNet and FCNsignal is not clearly articulated. The differences appear to be incremental, involving the specific combination of components like SPPM and RRB, but the text does not explain what specific advantages these bring. Similarly, the adversarial training framework is described as resembling GAN, but the distinction from the cited GRL method is not made explicit. The claim that adversarial training "pulls the domain space closer" is stated but the mechanism and its advantage over GRL are not demonstrated.
- **Why it matters** For a methods-focused manuscript, the novelty of the proposed approach is a key criterion for publication. If the contributions are incremental or not clearly differentiated from existing work, the significance is diminished.
- **Resolution test** Clearly articulate the specific architectural and methodological innovations, and provide comparative experiments or analyses that isolate the contribution of each novel component.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental rigor
- **Claim pointer** The manuscript claims that cross-species prediction performance is improved by adversarial training, and that this improvement is due to pulling domain spaces closer.
- **Evidence pointer** Results section "Adversarial training can improve the performance of cross-species TF binding prediction", Figures 5, 6, Supplementary Figure 10
- **Concern** The experimental design for evaluating adversarial training is not fully described. The manuscript mentions varying proportions of binding sequences added to the target data, but the rationale and the full range of conditions are not explained. The claim that "models with low proportions are generally better than those with high proportions" is presented without supporting numbers or statistical analysis. The visualization in Fig.6g is described qualitatively but the actual figure is not available. The mechanism by which adversarial training improves performance is inferred from the visualization but not rigorously tested.
- **Why it matters** The effectiveness of the proposed adversarial training is a central claim. Without rigorous experimental design and quantitative analysis, the claim is not convincing.
- **Resolution test** Provide a complete description of experimental conditions, present quantitative results for all conditions, and include statistical tests to support claims of improvement.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evaluation methodology
- **Claim pointer** The manuscript claims to make a direct comparison of sequence-level and nucleotide-level models using the maximums of coverage values as a bridge.
- **Evidence pointer** Methods section "Maximums of coverage values", Results section "The overall performance of NLDNN", Figure 2
- **Concern** The proposed evaluation methodology using maximums of coverage values is interesting but its validity is not fully established. The manuscript states that the maximums are closely related to binding strength based on a Pearson correlation of 0.9 (human) and 0.818 (mouse), but the details of this validation are not provided. The comparison of models with different output types using this metric may introduce biases that are not discussed. For example, nucleotide-level models are trained to predict coverage values directly, while sequence-level models are trained for classification or regression on the maximum, which may advantage one type.
- **Why it matters** The evaluation methodology is the foundation for all performance comparisons. If the methodology is flawed or biased, all subsequent claims are undermined.
- **Resolution test** Provide a thorough validation of the maximums-based evaluation approach, including comparisons with alternative evaluation strategies and a discussion of potential biases.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript claims that the source code is available at a GitHub repository and that data accession lists are provided in Supplementary Table 1.
- **Evidence pointer** Availability of data and materials section
- **Concern** The manuscript states that the code is available at a URL, but the repository is not described in terms of its contents, dependencies, or documentation. The data accession list is referenced but not provided in the text. For a computational methods paper, reproducibility is essential. Without clear documentation of code and data, other researchers cannot verify or build upon the results.
- **Why it matters** Reproducibility is a core requirement for scientific publication, particularly for methods papers. Lack of accessible code and data prevents verification and limits the impact of the work.
- **Resolution test** Provide a detailed description of the code repository, including dependencies, usage instructions, and example data. Ensure that all data accession numbers are listed and accessible.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract mentions "adversarial training" and "dual-path framework" but does not explain what these terms mean in this context. A brief clarification would help readers understand the contribution.
- **Required correction** Add a sentence in the abstract briefly explaining the adversarial training concept and its purpose.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Overview"
- **Evidence pointer** Results section "Overview"
- **Issue** The overview states that the maximums of coverage values are used to represent binding strength, but the rationale for this choice is only briefly mentioned. A more detailed justification would strengthen the presentation.
- **Required correction** Expand the explanation of why maximums are appropriate, possibly with a brief example or reference to the supplementary figure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Conclusions section
- **Evidence pointer** Conclusions section
- **Issue** The conclusions section mentions "PR-UAC" which appears to be a typo for "PR-AUC". This inconsistency could confuse readers.
- **Required correction** Correct the typo to "PR-AUC".

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Data processing"
- **Evidence pointer** Methods section "Data processing"
- **Issue** The description of how p-value coverage tracks were selected over fold-change tracks is brief. The statement that p-value tracks are "better suitable" is not supported with evidence or explanation.
- **Required correction** Provide a brief explanation or reference supporting the choice of p-value tracks.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Model training"
- **Evidence pointer** Methods section "Model training"
- **Issue** The training procedure mentions a "random sampling without replacement" strategy for negative sequences, but the details of this strategy and its impact on training are not discussed.
- **Required correction** Briefly describe the sampling strategy and its rationale.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Model interpretation"
- **Evidence pointer** Results section "Model interpretation"
- **Issue** The description of the motif discovery results is qualitative. Specific examples or quantitative measures of motif quality would strengthen the claims.
- **Required correction** Provide specific examples or quantitative metrics for motif discovery performance.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Reduced cross-species predictive performance"
- **Evidence pointer** Results section "Reduced cross-species predictive performance"
- **Issue** The analysis of factors contributing to reduced cross-species performance is interesting but the conclusions are drawn from limited evidence. The role of repeat elements is discussed but not systematically quantified.
- **Required correction** Provide quantitative analysis of the contribution of repeat elements and other factors to cross-species performance degradation.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "The framework of adversarial training"
- **Evidence pointer** Methods section "The framework of adversarial training"
- **Issue** The description of the adversarial training procedure is somewhat abstract. A step-by-step algorithm or pseudocode would improve clarity.
- **Required correction** Provide a pseudocode or algorithmic description of the training procedure.

## Risk / unsupported claims
- The claim that NLDNN performs better than competing methods in multiple prediction tasks is unsupported without visible quantitative results.
- The claim that adversarial training improves cross-species prediction performance is unsupported without numerical evidence and statistical analysis.
- The claim that the maximums of coverage values are closely related to binding strength is only supported by a correlation value without details of the validation.
- The claim that repeat elements contribute to reduced cross-species performance is plausible but not quantitatively demonstrated.
- The claim that the adversarial training framework pulls domain spaces closer is inferred from a qualitative visualization and not rigorously tested.
- The claim that NLDNN has better localization ability than other nucleotide-level models is not supported with specific numbers.
- The claim that nucleotide-level models are better suited for TF binding prediction while sequence-level models are better for chromatin accessibility is an interesting observation but not systematically tested.
- The claim that the proposed evaluation methodology enables direct comparison of sequence-level and nucleotide-level models is not fully validated.