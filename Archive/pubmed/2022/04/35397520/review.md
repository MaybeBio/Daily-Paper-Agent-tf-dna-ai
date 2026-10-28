## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, and figure/table captions as provided)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and support of claims based solely on the provided manuscript content
- **Shared manuscript claim summary** The manuscript proposes ProbC, a generative probabilistic model based on convex likelihood optimization, to decompose Hi-C and Micro-C interactions using chromatin marks (histone modifications and transcription factor binding sites). It claims that a small subset of marks (H3K27ac, H3K9me3, H3K4me3, H3K4me1, CTCF) is highly predictive of 3D genome interactions across cell types and species, and that ProbC outperforms existing methods in interaction prediction.
- **Visible evidence base** Methods section with mathematical formulation (Eqs. 1-19), Theorem 1 with proof, optimization details (ADMM, gradient descent), results section with figures (Figs. 1-13) and tables (Tables 1-3) referenced in captions, dataset descriptions, and performance metrics (AUC, Spearman correlation, NVI)
- **Missing materials affecting confidence** Actual figure images and table data are not provided; only captions are visible. No quantitative results (e.g., exact AUC values, confidence intervals, statistical significance tests) are given in the text. No comparison of computational runtime or scalability. No details on hyperparameter tuning ranges or convergence criteria. No access to code or datasets for independent verification.

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in 3D genomics by proposing a generative model that jointly considers epigenomic and transcriptomic marks to explain Hi-C and Micro-C interactions. The methodological framework is novel and mathematically rigorous, with a convex formulation and an efficient optimization scheme. However, the evidence presented in the text is largely qualitative, with figure and table captions that do not provide sufficient quantitative detail to fully assess the strength of the claims. The cross-species and cross-cell-type predictions are promising but require more robust statistical validation. The manuscript is well-written and accessible, but several technical aspects need clarification and additional experiments to establish the case convincingly.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on 3D genome organization, chromatin architecture, and integrative analysis of epigenomic data. Researchers developing predictive models for Hi-C interactions from 1D genomic features would find the generative approach and the identification of key marks valuable. The cross-species transferability results may interest evolutionary genomics researchers. The method's potential to predict 3D structure in species with limited Hi-C data is practically relevant.
- **Major strengths** 1) Novel formulation that jointly models mark interactions and Hi-C interactions with a convex objective, providing global optimality guarantees. 2) The method directly accounts for both interaction existence and non-existence, which is more informative than many existing approaches. 3) Identification of a sparse set of predictive marks (H3K27ac, H3K9me3, H3K4me3, H3K4me1, CTCF) with biological plausibility. 4) Demonstration of cross-species and cross-cell-type prediction, which has practical utility. 5) The manuscript is clearly written with a logical structure, making the methodology accessible to a broad audience.
- **Major Concerns** 1) The manuscript lacks quantitative results in the text; all performance metrics are only referenced in figure captions, making it impossible to assess the magnitude of improvements or statistical significance. 2) The claim of outperforming HiC-Reg and Rambutan is not substantiated with specific numbers or statistical tests. 3) The cross-species prediction results are presented without discussion of potential confounding factors or limitations. 4) The sensitivity analysis for λ1 and λ2 is described qualitatively; no quantitative thresholds or performance degradation curves are shown. 5) The manuscript does not address potential overfitting or the generalizability of the identified mark subset to other cell types or conditions beyond those tested.
- **Minor Comments** 1) The term "transcriptome effects" in the title is somewhat misleading, as the manuscript focuses on transcription factor binding sites rather than transcriptomic data (e.g., RNA-seq). 2) The related work section could benefit from a more explicit comparison of ProbC's generative approach versus discriminative methods in terms of interpretability. 3) The proof of Theorem 1 is brief; a more detailed derivation of the Hessian negative semidefiniteness would strengthen the methodological contribution. 4) The description of the Poisson approximation (Eq. 19) could clarify the conditions under which Le Cam's theorem is valid in this context. 5) The manuscript mentions "latent biases" in Hi-C but does not elaborate on how these could be used for noise filtering in practice.
- **Technical failings that need to be addressed before the case is established** 1) Lack of quantitative performance metrics in the text (e.g., exact AUC values, confidence intervals, p-values for comparisons). 2) No statistical significance testing for the claimed outperformance over baselines. 3) The cross-species prediction results are not accompanied by error bars or variability measures. 4) The manuscript does not report the number of marks used in the final model or the sparsity level achieved. 5) No discussion of computational complexity or runtime, which is important for practical adoption.
- **Assessment against Nature-style criteria** Originality: High. The generative probabilistic framework for joint modeling of marks and Hi-C interactions is novel, and the convex formulation with global optimality is a significant contribution. Scientific importance: Moderate to high. The problem of predicting 3D genome structure from 1D marks is relevant, and the identification of key predictive marks has biological implications. However, the impact would be stronger with more comprehensive validation. Interdisciplinary readership: Moderate. The manuscript is accessible to computational biologists, but the lack of detailed biological interpretation of the identified marks may limit appeal to experimentalists. Technical soundness: The mathematical formulation is sound, but the evidence base is incomplete due to missing quantitative results. Readability for nonspecialists: Good. The manuscript is well-structured and explains concepts clearly, though some sections (e.g., optimization details) may be challenging for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core methodology is promising and the problem is important, but the current manuscript does not provide sufficient quantitative evidence to fully establish the claims. The authors should add detailed results, statistical analyses, and robustness checks to strengthen the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "ProbC outperforms the existing methods in predicting interactions across almost all chromosomes" (Results section, paragraph on comparison with HiC-Reg and Rambutan)
- **Evidence pointer** Figure 7 caption; location not provided for specific numbers
- **Concern** The claim of outperformance is not supported by any quantitative data in the text. The figure caption only states that a comparison was made, but no AUC values, confidence intervals, or statistical tests are reported. Without these, it is impossible to assess whether the improvement is meaningful or statistically significant.
- **Why it matters** The central claim of the manuscript is that ProbC is superior to existing methods. If this is not rigorously demonstrated with appropriate statistical analysis, the contribution is weakened and the reader cannot evaluate the practical value of the method.
- **Resolution test** Provide a table or in-text summary of AUC values for ProbC, HiC-Reg, and Rambutan across all chromosomes, including mean and standard deviation, and perform a paired statistical test (e.g., Wilcoxon signed-rank test) to demonstrate significance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** "We can estimate interaction probabilities between marks in less than 15 minutes on human IMR90 cells even without binning" (Results section, Datasets and implementation)
- **Evidence pointer** Section "Datasets and implementation"; location not provided
- **Concern** The runtime claim is not accompanied by details on the computational environment (e.g., CPU, memory), the size of the dataset, or the convergence criteria used. Without these, the claim is not reproducible and may not generalize to other settings.
- **Why it matters** Reproducibility is a core requirement for computational methods. If the runtime is not properly contextualized, other researchers cannot assess whether the method is practical for their use cases.
- **Resolution test** Specify the hardware and software environment, report the number of marks and interactions in the dataset, and describe the convergence criteria (e.g., tolerance, maximum iterations). Provide runtime as a function of dataset size if possible.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** "PROBC can accurately predict cross-cell types and cross-species interactions" (Results section, subsection on cross-cell types and cross-species)
- **Evidence pointer** Figures 10 and 11 captions; location not provided
- **Concern** The cross-species and cross-cell-type predictions are presented as accurate, but no quantitative metrics are given in the text. The figures are only described in captions, and it is unclear how "accuracy" is defined (e.g., AUC, correlation, F1 score). Additionally, the manuscript does not discuss potential biases or limitations of transferring models across species, such as differences in mark distributions or genome organization.
- **Why it matters** Cross-species prediction is a strong claim with practical implications. If not rigorously validated, the results may be overinterpreted, and the limitations could undermine the generalizability of the method.
- **Resolution test** Report specific performance metrics (e.g., AUC, Spearman correlation) with confidence intervals for all cross-species and cross-cell-type comparisons. Discuss potential confounding factors, such as differences in data quality or mark availability, and perform sensitivity analyses.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Model assumptions
- **Claim pointer** "We assume these interaction probabilities between marks X to be same across all restriction sites which is a global characteristic of genome embedding rather than being a local feature" (Methods, PROBC model)
- **Evidence pointer** Methods section, "PROBC: generative probabilistic model"; location not provided
- **Concern** The assumption of global uniformity of mark interaction probabilities is strong and may not hold across different genomic regions, such as heterochromatin versus euchromatin, or across different chromosomes. The manuscript does not test this assumption or discuss its potential impact on the results.
- **Why it matters** If the assumption is violated, the model may produce biased estimates of interaction probabilities, leading to incorrect predictions or interpretations. The validity of the model depends on the reasonableness of this assumption.
- **Resolution test** Perform a sensitivity analysis by fitting the model separately for different genomic compartments (e.g., A/B compartments) or chromosome regions and compare the inferred interaction probabilities. Discuss whether the global assumption is justified or if a local model would be more appropriate.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Title
- **Evidence pointer** Title
- **Issue** The title mentions "transcriptome effects," but the manuscript focuses on transcription factor binding sites, not transcriptomic data (e.g., RNA-seq). This could mislead readers about the scope of the work.
- **Required correction** Consider revising the title to "ProbC: joint modeling of epigenome and transcription factor binding effects in 3D genome" or similar to accurately reflect the content.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Related work
- **Evidence pointer** Related work section
- **Issue** The comparison with existing methods is brief and does not explicitly discuss the advantages of a generative model over discriminative approaches in terms of interpretability and the ability to model non-interactions.
- **Required correction** Add a paragraph in the related work section that explicitly contrasts generative versus discriminative modeling for Hi-C prediction, highlighting the unique contributions of ProbC.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Theorem 1 proof
- **Evidence pointer** Methods, Theorem 1 proof
- **Issue** The proof of convexity is concise and relies on the Hessian being negative semidefinite, but the derivation is not fully detailed. This may be challenging for readers to verify.
- **Required correction** Expand the proof to show the explicit computation of the Hessian and the conditions under which it is negative semidefinite, or provide a reference for the convexity of the log-sum-exp type functions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Practical utility
- **Affected element** Discussion of latent biases
- **Evidence pointer** Results, paragraph on interaction probabilities
- **Issue** The manuscript mentions that inferred interaction probabilities can be interpreted as latent biases in Hi-C, but does not elaborate on how these could be used to filter noise or improve experimental design.
- **Required correction** Add a brief discussion on the practical implications of the inferred biases, such as potential applications in Hi-C data normalization or experimental validation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Cross-species results
- **Evidence pointer** Figures 10 and 11 captions
- **Issue** The cross-species results are presented without error bars or variability measures, making it difficult to assess the robustness of the predictions.
- **Required correction** Include error bars or confidence intervals in the figures, and report the number of replicates or cross-validation folds used.

## Risk / unsupported claims
- The claim that ProbC "outperforms the existing methods" is unsupported in the text because no quantitative results are provided.
- The claim of "accurate" cross-species and cross-cell-type prediction is not substantiated with specific metrics or statistical tests.
- The statement that "identified chromatin marks alone carry almost enough information to predict chromosomal structures" is an overgeneralization without supporting evidence.
- The assumption of global uniformity of mark interaction probabilities is stated but not tested or justified.
- The runtime claim of "less than 15 minutes" is not reproducible without details on the computational environment and dataset size.