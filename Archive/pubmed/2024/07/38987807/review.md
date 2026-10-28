## Review setup
- **Input scope** Full manuscript text (Introduction, Results, Discussion, Methods) with figure legends and supplementary figure references
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and significance of the TFscope framework as presented
- **Shared manuscript claim summary** The authors present TFscope, a machine learning approach that systematically identifies sequence features (core motif, nucleotide environment, co-factor binding sites) explaining transcription factor binding differences between two conditions (cell types, treatments, or paralogous TFs). They apply it to 272 cell-type pairs and 79 treatment pairs, reporting that co-factors and nucleotide environment dominate cell-type differences, while core motif differences dominate paralog comparisons.
- **Visible evidence base** Main text figures 1-7, supplementary figures S1-S8, supplementary tables, methods descriptions, and links to a public GitLab repository with results
- **Missing materials affecting confidence** Full supplementary figures and tables not provided in the submitted text; detailed parameter settings for LASSO regularization; complete description of the DExTER modification; exact definitions of "unique" peaks; details on the hierarchical clustering procedure for pair selection; code availability statement

## Reviewer
- **Overall assessment** This manuscript presents a well-motivated and potentially useful framework for dissecting sequence determinants of TF binding specificity. The three-module design is conceptually clear, and the application to a large number of ChIP-seq pairs is commendable. However, several methodological details and validation aspects require clarification and strengthening before the claims can be fully supported. The comparison to existing methods is incomplete, and the biological interpretations, while plausible, are not always rigorously tested against alternatives.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational genomics, and gene regulatory network inference would find this work relevant. The framework offers a transparent alternative to black-box deep learning models for explaining TF binding differences, which is of broad interest to those studying cell-type-specific gene regulation, paralog functional divergence, and the mechanistic basis of TF-DNA recognition.
- **Major strengths**
  1. The problem addressed is important and timely: moving beyond static PWM models to explain context-dependent TF binding.
  2. The three-module decomposition (core motif, nucleotide environment, co-factors) is intuitive and provides interpretable outputs.
  3. The default strategy of comparing condition-unique peaks avoids the difficult background definition problem.
  4. The scale of application (272 + 79 pairs) is substantial and provides a useful resource.
  5. The use of LASSO for feature selection and the "mirror-logo" visualization are practical and clear.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological rigor
  - **Claim pointer** The claim that TFscope "systematically investigates" the importance of three feature types and that the learned discriminative PWM is "the best PWM for our problem" (optimality claim).
  - **Evidence pointer** Methods sections "TFscope-DM", "TFscope-NE", "TFscope-CF"; Results section "TFscope overview"
  - **Concern** The optimality claim for the discriminative PWM rests on the convexity of the logistic regression likelihood, which is true, but the feature space is restricted to a single PWM of fixed length K. The comparison to DAMO and STREME is presented as a conceptual advantage, but no runtime or accuracy comparison on identical inputs is shown. More critically, the procedure for selecting the PWM length K and the number of LASSO iterations is not described. The "best" PWM is only optimal within the chosen model class and regularization path, which is not acknowledged.
  - **Why it matters** Overstating optimality could mislead users into believing no better discriminative motif model exists. The practical utility depends on robust parameter choices, which are not documented.
  - **Resolution test** Provide a formal statement of the optimization problem and the conditions under which the global optimum is reached. Report sensitivity analyses for K and the LASSO penalty parameter. Include a runtime comparison with DAMO and STREME on a common benchmark set.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validation and benchmarking
  - **Claim pointer** The claim that TFscope "outperforms" alternative models (original PWM, incomplete models) and that the identified features are biologically meaningful.
  - **Evidence pointer** Results sections "TFscope provides meaningful information about co-factors", "TFscope assesses the relative importance of each sequence feature"; Figures 2A, 3A, 4A
  - **Concern** The evaluation is primarily based on AUROC on held-out test sets. While this is standard, the manuscript lacks a comparison against a simple sequence-based baseline (e.g., k-mer frequencies without positional information) or against a state-of-the-art deep learning model (e.g., DeepBind, BPNet) to contextualize the performance. The biological validation (e.g., co-factor expression correlation in Figure 3B) is suggestive but limited to a small subset (19 experiments) and does not include a negative control (e.g., randomly selected motifs). The claim that co-factors are "the most common mechanism" is based on a clustering of importance scores, but the stability of this clustering is not assessed.
  - **Why it matters** Without appropriate baselines and negative controls, the reader cannot judge whether the identified features are truly informative or an artifact of the model architecture. The biological claims require stronger evidence to exclude alternative explanations.
  - **Resolution test** Add a baseline model using only k-mer frequencies (no positional information) and a deep learning model. Include negative controls where the class labels are permuted. Assess clustering stability via bootstrapping. Expand the co-factor expression analysis to include a larger set of experiments and a matched set of non-co-factor motifs.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility and data availability
  - **Claim pointer** The claim that all results are available at a public GitLab repository.
  - **Evidence pointer** Results sections; "Availability of data and materials" (implied)
  - **Concern** The manuscript states results are available at a GitLab URL, but the provided text does not include a full data availability statement, code availability statement, or a description of the computational environment (software versions, dependencies). The methods section mentions specific commands for BEDTools and FIMO but does not provide a complete pipeline description or a containerized environment. The supplementary figures and tables are referenced but not included in the submitted text, making it impossible to verify the claims about Figure S1-S8.
  - **Why it matters** Reproducibility is a core requirement for computational biology papers. Without complete code, data, and environment specifications, the work cannot be independently verified or extended.
  - **Resolution test** Provide a complete data availability statement with a persistent identifier (e.g., Zenodo DOI). Provide a code repository with a README, dependency list, and a container (e.g., Docker) or a conda environment file. Include all supplementary figures and tables in the submission.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor
  - **Claim pointer** The claim that "classification is very often accurate" and the use of AUROC as the primary metric.
  - **Evidence pointer** Results sections "TFscope assesses the relative importance of each sequence feature"; Figure 4A
  - **Concern** AUROC is reported, but no confidence intervals, statistical tests comparing models, or correction for multiple testing across 272 experiments are provided. The median AUROC is reported, but the variance across experiments is not characterized. The relationship between AUROC and the number of peaks per experiment is not examined, which could confound comparisons.
  - **Why it matters** Without measures of uncertainty, the reader cannot assess the reliability of the reported accuracies. The lack of multiple testing correction is particularly concerning given the large number of comparisons.
  - **Resolution test** Report AUROC with confidence intervals (e.g., via bootstrapping). Perform a statistical comparison of model performances (e.g., paired Wilcoxon test). Examine the correlation between AUROC and sample size. Apply multiple testing correction where appropriate.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1 legend
  - **Issue** The figure legend is dense and does not clearly explain the flow from input to output. The role of the "lattice structure" in the co-factor module is not visually evident.
  - **Required correction** Simplify the legend and add annotations to the figure to clarify the lattice structure and the flow of data.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "Discriminative PWM"
  - **Evidence pointer** Methods section "TFscope-DM"
  - **Issue** The term "discriminative PWM" is used, but it is not clearly distinguished from a standard PWM or a position weight matrix learned by other means. The relationship to the original PWM used for scanning is not fully explained.
  - **Required correction** Define "discriminative PWM" explicitly and explain how it differs from the original PWM and from a PPM-derived PWM.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Alternative analyses
  - **Evidence pointer** Results section "Indirect binding and alternative analyzes"
  - **Issue** The section on alternative analyses is brief and does not provide quantitative results for the DiffBind comparison or the analysis without re-centering. The reader cannot assess how these alternatives affect the conclusions.
  - **Required correction** Provide a summary table or figure with AUROC values for the alternative analyses and a brief discussion of the implications.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Co-factor expression analysis
  - **Evidence pointer** Results section "TFscope provides meaningful information about co-factors"; Figure 3B
  - **Issue** The analysis shows that co-factor expression is higher in the cell type where the co-factor motif is enriched. However, this could be confounded by the overall expression level of the co-factor across cell types. A normalization or a comparison to a random set of motifs would strengthen the claim.
  - **Required correction** Add a control analysis using random motifs or a permutation test to show that the observed expression difference is specific to the identified co-factors.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Results section "Analysis of binding differences of paralogous TFs"
  - **Evidence pointer** Figure 7
  - **Issue** The text states that TFscope "confirms" previous results for FOSL1/FOSL2 and NR3C1/AR, but the comparison to the previous studies is not detailed. The reader cannot assess the degree of agreement.
  - **Required correction** Provide a more detailed comparison, including specific positions and nucleotides that match or differ from the previous findings.
- **Technical failings that need to be addressed before the case is established**
  1. R1-M1: Optimality claim requires formal qualification and sensitivity analysis.
  2. R1-M2: Lack of baseline comparisons and negative controls weakens the validation.
  3. R1-M3: Incomplete data and code availability prevents reproducibility.
  4. R1-M4: Missing statistical rigor in performance reporting.
- **Assessment against Nature-style criteria**
  - **Originality** The work is original in its specific combination of three interpretable feature types within a single framework and its application at scale. However, the individual components (discriminative motif learning, k-mer enrichment, co-factor motif scanning) are not novel in isolation. The originality lies in the integration and systematic application.
  - **Scientific importance** The question of what determines TF binding specificity beyond the core motif is of high importance. The framework has the potential to generate testable hypotheses about co-factor dependencies and nucleotide context effects. The scale of the analysis adds value. However, the importance is somewhat tempered by the lack of deep biological validation and the absence of clear new biological insights beyond what was already known for the specific cases examined.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and genomics researchers. The methods are described in sufficient detail for this audience, but the biological interpretation sections are accessible to a broader readership. The manuscript does not currently bridge into other disciplines (e.g., structural biology, biophysics) in a way that would broaden its appeal.
  - **Technical soundness** The core methodology is sound in principle, but the technical execution has gaps. The lack of baseline comparisons, negative controls, and statistical rigor are significant weaknesses. The reliance on AUROC as the sole metric is limiting. The methods for feature selection and model evaluation need more detail and robustness checks.
  - **Readability for nonspecialists** The manuscript is clearly written but assumes familiarity with ChIP-seq, PWMs, and machine learning concepts. The introduction provides good context, but the results and methods sections are dense. The figures are informative but some (e.g., Figure 1) are complex. The abstract is accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The framework is potentially valuable, but the current manuscript does not fully establish its validity and utility due to the methodological and validation gaps identified above. A revised version addressing these concerns could be a solid contribution to the field.

## Risk / unsupported claims
- The claim that the discriminative PWM is "the best PWM for our problem" is unsupported without a formal proof of global optimality within the specified model class and a demonstration that the LASSO path converges to this optimum.
- The claim that co-factors are "the most common mechanism" for cell-type binding differences is based on a clustering analysis whose stability is not assessed and which does not account for potential confounding factors (e.g., motif similarity, peak quality).
- The biological interpretation of the FOSL1/FOSL2 and NR3C1/AR comparisons is presented as "confirming" previous work, but the quantitative agreement is not shown.
- The statement that "in a majority of cases (58%), co-factors are the most influential feature" is presented without confidence intervals or a statistical test against the null hypothesis of equal importance.
- The analysis of repeat elements is limited to a single case study (NR3C1) and does not systematically evaluate the contribution of repeats across the full dataset.
- The alternative analyses (DiffBind, without re-centering) are described but not quantitatively reported, making their conclusions unverifiable.