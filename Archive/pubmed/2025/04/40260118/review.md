## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided.
- **Assessment boundary** Scientific soundness, methodological clarity, validation strength, and alignment with the journal's stated scope. No assessment of code functionality or reproducibility beyond what is described.
- **Shared manuscript claim summary** The authors present NetREm, a network-regularized regression framework that integrates single-cell gene expression data with prior protein–protein interaction networks to infer cell-type-specific transcription factor–target gene regulatory links and transcription factor–transcription factor coordination. The method is validated through simulations, benchmarked against existing tools, and applied to Schwann cell subtypes and Alzheimer's disease contexts.
- **Visible evidence base** Simulation studies (Section 3.2), benchmarking against SOTA GRN tools (Section 3.3), application to Schwann cells (Section 3.4) and AD (Section 3.6), supplementary figures and tables referenced but not fully visible.
- **Missing materials affecting confidence** Supplementary File S5 (detailed methodology), supplementary tables and figures, code repository contents, and full validation datasets were not provided. These are essential for verifying methodological details and reproducibility.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting integration of network priors with regression-based GRN inference, addressing a real gap in the field. The core idea of using PPINs to regularize TF selection and infer coordination is timely. However, the current manuscript has several critical weaknesses: the methodological description is dense and at times unclear, the validation strategy is incomplete (particularly regarding statistical rigor and comparison fairness), and the biological claims in the applications are not sufficiently supported by the presented evidence. The work has potential but requires substantial revision and additional analysis before the claims are established.
- **Who would be interested in the results, and why** Computational biologists developing GRN inference methods; researchers studying transcriptional regulation in development and disease, particularly in the nervous system; and those interested in integrating prior knowledge with single-cell data. The method's ability to infer TF–TF coordination could be of broad interest to the gene regulation community.
- **Major strengths**
  1. Novel integration of PPIN priors into a regression framework for GRN inference, addressing a recognized limitation of expression-only methods.
  2. The method outputs both TF–TG regulatory links and TF–TF coordination scores, providing a more complete picture than many existing tools.
  3. The application to clinically relevant contexts (Schwann cells, AD) demonstrates potential utility.
  4. The authors provide an open-source implementation, which is commendable for reproducibility.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological clarity
  - **Claim pointer** The authors claim NetREm is a "novel computational framework" that "leverages network-constrained regularization" to reveal TF–TF coordination.
  - **Evidence pointer** Section 2.1, Equations (1)–(4)
  - **Concern** The mathematical formulation is presented with insufficient clarity. The transformation from the original objective function to the final Lasso problem (Equations 1–4) is not fully derived or explained. Key steps, such as the construction of the embedding matrices X̃ and ỹ, and the role of the truncated SVD, are described but not rigorously justified. The notation is inconsistent (e.g., N used for both number of candidate TFs and sample size in different contexts). A reader cannot easily reproduce the method from the description alone.
  - **Why it matters** Reproducibility is a core requirement for computational methods. Without a clear, step-by-step derivation and explanation of the algorithm, the scientific community cannot evaluate, implement, or build upon the method. This is a blocking issue for publication.
  - **Resolution test** The authors should provide a complete, self-contained derivation of the method, including all matrix dimensions, definitions of all variables, and a clear explanation of the SVD-based transformation. A pseudocode algorithm box would be highly beneficial. The notation should be standardized throughout.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validation rigor
  - **Claim pointer** The authors claim NetREm "achieves the highest precision in predicting signed-TF-TG links" and "outperforms" SOTA tools in various contexts.
  - **Evidence pointer** Section 3.3, Supplementary Figures S5–S7, Supplementary Tables S8–S14
  - **Concern** The benchmarking methodology is not described with sufficient detail to assess fairness. It is unclear how hyperparameters were selected for the comparison methods, whether the same train/test splits were used, and what statistical tests were performed to support claims of superiority. The statement "NetREm achieves the highest precision" appears to be based on a single metric or a limited set of metrics, and the variability across datasets is not reported. The comparison to SCENET is mentioned but not shown in the main text.
  - **Why it matters** Claims of improved performance over existing methods are central to the paper's contribution. Without rigorous, fair, and statistically sound benchmarking, these claims are not substantiated. The community needs to trust that the improvement is real and not an artifact of favorable parameter choices or data selection.
  - **Resolution test** The authors should provide a detailed benchmarking protocol, including hyperparameter tuning procedures for all methods, a description of cross-validation schemes, and results of statistical significance tests (e.g., paired tests across datasets). Performance should be reported with confidence intervals. The comparison to SCENET should be included in the main text.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Biological validation
  - **Claim pointer** The authors claim that NetREm "reveals cell-type transcription factor coordination" and that predictions are "validated with experimental data from rat, mouse, and human models."
  - **Evidence pointer** Sections 3.4–3.5, Figures 4–5, Supplementary Figures S15–S19
  - **Concern** The biological validation is presented in a fragmented manner. For the Schwann cell application, the authors mention validation with experimental data, but the specific nature of this validation is not clearly described. For example, what exactly was validated? Were the predicted TF–TF coordination links tested experimentally, or was the validation limited to comparing predicted target genes with existing ChIP-seq/knockout data? The AD section presents interesting correlations but lacks a clear causal or mechanistic validation. The statistical significance of the enrichment analyses is mentioned but not fully detailed.
  - **Why it matters** The biological applications are a key selling point of the paper. If the validation is not rigorous, the claims of biological discovery are weakened. The authors need to clearly distinguish between predictions, correlations, and experimentally validated findings.
  - **Resolution test** The authors should clearly describe the validation strategy for each application. For the Schwann cell data, specify which predictions were tested and how. For the AD data, provide a more focused analysis of a few key TF–TF coordination events, with supporting evidence from independent datasets or experiments.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparison to existing methods
  - **Claim pointer** The authors state that SOTA tools "often overlook the interdependent TF-TF PPI networks" and that NetREm addresses this gap.
  - **Evidence pointer** Section 1 (Introduction), Section 3.3
  - **Concern** The introduction does not adequately position NetREm relative to other network-regularized regression methods or GRN inference tools that incorporate prior information. The claim that existing tools "overlook" PPINs is too broad; some methods do use prior networks, albeit in different ways. A more nuanced comparison is needed.
  - **Why it matters** The novelty of the contribution depends on a clear understanding of the state of the art. Overstating the gap can undermine the credibility of the paper.
  - **Resolution test** The authors should revise the introduction to acknowledge existing methods that use network priors and clearly articulate the specific novelty of NetREm (e.g., the embedding approach, the focus on TF–TF coordination).

  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Parameter sensitivity
  - **Claim pointer** The authors claim NetREm's performance is "robust" to changes in the input PPIN.
  - **Evidence pointer** Section 3.3, Supplementary Figure S14
  - **Concern** The robustness analysis is described only briefly. It is unclear how the input PPIN was varied (e.g., which PPINs were used, how they differed) and what metric was used to assess robustness. The claim of robustness needs to be supported by a more systematic analysis.
  - **Why it matters** The method's utility depends on its performance with different input networks, as users may have access to different PPIN resources. A weak robustness analysis limits confidence in the method's general applicability.
  - **Resolution test** The authors should provide a more detailed robustness analysis, varying the input PPIN systematically (e.g., different databases, different confidence thresholds) and reporting the impact on both TF–TG and TF–TF predictions.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of writing
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract, Section 1
  - **Issue** The abstract is dense and uses jargon without clear definitions. The introduction could be more accessible to a broader audience.
  - **Required correction** Simplify the abstract, define key terms (e.g., "network regression embeddings") early, and provide more context for non-specialists.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Figure quality
  - **Affected element** Figures 1–6
  - **Evidence pointer** Figures 1–6
  - **Issue** The figures are complex and may be difficult to interpret without detailed legends. Some figure panels are referenced but not fully explained in the text.
  - **Required correction** Improve figure legends to be self-contained. Ensure all panels are described in the text.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data Availability section
  - **Evidence pointer** Data Availability section
  - **Issue** The data availability statement is vague. It is unclear what data and code are available and under what license.
  - **Required correction** Provide a clear statement on data and code availability, including a link to the repository and any relevant accession numbers.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Throughout
  - **Evidence pointer** Throughout
  - **Issue** The term "revolutionary" is used in the abstract, which is subjective and not appropriate for a scientific manuscript.
  - **Required correction** Replace subjective terms like "revolutionary" with more objective descriptors.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Section 3.5
  - **Evidence pointer** Section 3.5, Figure 5A
  - **Issue** The comparison of MSEs is mentioned, but the statistical significance of the differences is not reported.
  - **Required correction** Add statistical tests (e.g., paired t-tests) and report p-values for the MSE comparisons.

## Risk / unsupported claims
- The claim that NetREm "reveals cell-type transcription factor coordination" is not fully supported by the presented evidence, as the biological validation is incomplete.
- The claim of "unprecedented" performance or "revolutionary" capabilities is not supported by the data and should be tempered.
- The claim that NetREm can "help address the link prediction problem" is speculative and not directly tested.
- The generalizability of the method to other organisms and data types is claimed but not demonstrated beyond the presented applications.
- The robustness of the method to different PPIN inputs is claimed but not rigorously demonstrated.