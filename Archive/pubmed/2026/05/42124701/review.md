## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, discussion, and supplementary figure/table references
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and interpretability of the ChIP-FRiP pipeline and its application to cohesin ChIP-seq meta-analysis
- **Shared manuscript claim summary** The authors present ChIP-FRiP, a standardized pipeline for computing fraction of reads in peaks (FRiP) across ChIP-seq datasets, apply it to 140 cohesin datasets from 13 studies, and use biophysical simulations coupled with a biochemical model of antibody background to explain observed FRiP variation and propose a background correction strategy
- **Visible evidence base** Abstract, full introduction, full results section, full methods section, discussion, code availability statements, figure references (Fig 1-4, S1-S8), table references (Table 1, S1-S2)
- **Missing materials affecting confidence** Actual figures and supplementary tables not provided; no raw data or intermediate pipeline outputs; no validation metrics for pipeline accuracy beyond correlation with existing tools; no detailed statistical outputs from beta regression models

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important problem in quantitative ChIP-seq analysis, specifically the confounding role of antibody background in interpreting cohesin positioning data. The development of a standardized pipeline for cross-study FRiP comparison is valuable, and the integration of biophysical simulations with a biochemical model of background is conceptually innovative. However, the central claim that background correction is "requisite" for interpreting cohesin cofactor roles rests on a model with several simplifying assumptions that are not fully validated against experimental ground truth. The meta-analysis reveals substantial heterogeneity but the attribution of this heterogeneity to technical versus biological factors remains incomplete. The proposed correction strategy, while logically derived, is not demonstrated to recover known biological signals in a prospective validation. Overall, the work is promising but the evidence as presented does not fully establish the case that background correction is both necessary and sufficient for reliable comparative cohesin ChIP-seq analysis.

- **Who would be interested in the results, and why** Researchers studying cohesin biology, chromatin architecture, and loop extrusion mechanisms would find the meta-analysis and simulation framework directly relevant. Methodologists and bioinformaticians developing ChIP-seq analysis pipelines would be interested in the ChIP-FRiP pipeline and the background correction strategy. The broader chromatin biology community would benefit from the cautionary insights regarding antibody specificity and quantitative interpretation of ChIP-seq data. The work also has relevance for anyone performing meta-analyses of public ChIP-seq datasets.

- **Major strengths** The manuscript addresses a genuine and underappreciated problem in the field, namely that quantitative interpretation of ChIP-seq data is confounded by antibody background. The development of a standardized, reproducible pipeline for cross-study comparison is a practical contribution. The coupling of biophysical simulations with a biochemical model of background is conceptually elegant and provides mechanistic insight into how background can invert expected FRiP trends. The meta-analysis of 140 datasets from 13 studies is comprehensive and the observation of substantial cross-study heterogeneity is an important cautionary finding. The proposed background correction strategy, derived from the model, is logically sound and practically implementable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** "Our results establish a framework for reliable comparative analysis, demonstrating that accurate background correction is requisite for interpreting the roles of cohesin cofactors in cohesin positioning."
- **Evidence pointer** Results section "Correcting for ChIP-seq background reads"; Methods section "Estimating background fraction in ChIP-seq data"
- **Concern** The central claim that background correction is "requisite" is supported by a theoretical model and a derivation, but no experimental validation is provided demonstrating that the correction actually recovers known biological signals. The authors derive a formula for estimating background fraction from paired spike-in data (Equation 17) and a denoising formula (Equation 19), but these are not applied to any real dataset to show that corrected FRiP values align with independent biological measurements or expectations. The claim of "reliable comparative analysis" is therefore not empirically established.
- **Why it matters** The manuscript's primary contribution is the assertion that background correction is necessary for correct biological interpretation. Without a demonstration that the correction works on real data, the claim remains theoretical. A skeptical reader cannot distinguish whether the correction improves accuracy or introduces new biases.
- **Resolution test** Apply the background estimation and denoising procedure to at least one dataset where an independent ground truth exists, such as a dataset with known cohesin binding levels from orthogonal methods (e.g., quantitative mass spectrometry or calibrated ChIP with recombinant standards). Show that corrected FRiP values correlate with the independent measurement better than uncorrected values. Alternatively, demonstrate that the correction resolves a known biological discrepancy between studies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model assumption validity
- **Claim pointer** "Leveraging a simple biochemical model for background ChIP-seq signal, we derived a strategy to estimate and correct for the background using paired spike-in ChIP-seq data from wild-type and depletion conditions."
- **Evidence pointer** Methods section "Biochemical model of background noise in cohesin ChIP-seq"
- **Concern** The biochemical model relies on four explicit assumptions: equilibrium binding kinetics, sufficient antibody abundance, background signal weaker than cohesin signal, and uniform background distribution. The assumption of sufficient antibody abundance to capture all available cohesin is particularly problematic, as antibody saturation is not guaranteed in typical ChIP experiments and could vary with chromatin accessibility and crosslinking efficiency. The assumption that background is uniformly distributed across the genome is also questionable, as non-specific antibody binding may have sequence or chromatin-state preferences. These assumptions are acknowledged in the Discussion but their potential impact on the derived correction strategy is not quantitatively assessed.
- **Why it matters** If the assumptions are violated, the derived correction formula could systematically bias results. For example, if antibody is not saturating, the relationship between ChIP signal and cohesin abundance becomes nonlinear in a way not captured by the model. If background is non-uniform, the correction could over- or under-correct in specific genomic regions, potentially creating spurious peaks or masking real ones.
- **Resolution test** Perform sensitivity analyses varying each assumption within plausible ranges and show that the qualitative conclusions (i.e., that background correction is necessary) hold. Alternatively, validate the model against experimental data where antibody concentration and background distribution are directly measured, such as titration experiments with varying antibody amounts.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Meta-analysis interpretation
- **Claim pointer** "We found substantial variation attributable to technical effects, obscuring biological interpretability."
- **Evidence pointer** Results section "Meta-analysis of how cohesin perturbations impact experimental FRiP"; Figure 2
- **Concern** The meta-analysis identifies substantial FRiP variation across studies, but the attribution of this variation to "technical effects" is not rigorously demonstrated. The beta regression analysis considers covariates such as cell type, antibody type, read count, and spike-in presence, but the relative contribution of each is not clearly quantified. The statement that technical effects "obscure biological interpretability" is plausible but the analysis does not formally partition variance into technical versus biological components. Furthermore, the observation that WAPL depletion shows variable FRiP changes across studies could reflect genuine biological differences (e.g., cell-type-specific effects) rather than technical artifacts.
- **Why it matters** The manuscript's motivation is that cross-study comparison is confounded by technical variation. If the variation is actually biological, the proposed solution (background correction) would not address the root cause. The distinction is critical for the field to know whether the problem is technical or biological.
- **Resolution test** Perform a formal variance decomposition analysis, such as mixed-effects modeling with study as a random effect, to quantify the proportion of variance attributable to technical versus biological factors. Alternatively, compare FRiP variation within studies (across replicates) to between studies for the same perturbation to estimate technical reproducibility.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Simulation parameter justification
- **Claim pointer** "We used simulations of cohesin loop extrusion with dynamic CTCF barriers and extrusion parameters chosen based on measurements in mouse embryonic stem cells."
- **Evidence pointer** Methods section "Loop extrusion simulations for modeling cohesin number effects on FRiP"
- **Concern** The simulation parameters are stated to be based on mESC measurements, but the specific values and their sources are not provided in the visible text. The baseline LEF separation of 250 kb, CTCF lifetime of 780 sec, and other parameters are given, but no justification or citation is provided for these choices. The sensitivity of the qualitative conclusions to parameter variation is not explored.
- **Why it matters** The simulation results showing that FRiP decreases with increasing cohesin number are central to the manuscript's argument that background can invert this relationship. If the simulation parameters are not representative of actual cellular conditions, the predicted relationship may not hold, undermining the motivation for the background correction.
- **Resolution test** Provide parameter values with citations or justify them from experimental measurements. Perform a parameter sweep (e.g., varying LEF separation, CTCF occupancy, cohesin processivity) and show that the qualitative relationship between cohesin number and FRiP is robust.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of pipeline validation
- **Affected element** Results section "ChIP-FRiP pipeline from FASTA to FRiP"
- **Evidence pointer** Figure S1
- **Issue** The validation of the pipeline against SpikeFlow and chipseq is described as showing "correlations near 1," but the specific correlation values, the number of samples compared, and the genomic regions used for comparison are not stated. Correlation alone may not capture systematic biases.
- **Required correction** Provide the actual correlation coefficients, the number of datasets compared, and a description of the comparison metrics. Consider reporting additional metrics such as mean absolute difference or concordance correlation coefficient.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Meta-analysis of how cohesin perturbations impact experimental FRiP"
- **Evidence pointer** Table 1
- **Issue** The beta regression results are summarized in Table 1, but the table is not visible in the provided text. The BIC values are mentioned but no confidence intervals or significance tests are reported for the covariate effects.
- **Required correction** Include the full beta regression output in the table, including coefficient estimates, standard errors, and p-values or confidence intervals. State the number of observations used in the model.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Throughout
- **Evidence pointer** Abstract, Results
- **Issue** The term "FRiP" is used both as a quality metric and as a quantitative measure of cohesin positioning. While the authors define FRiP as fraction of reads in peaks, the interpretation of FRiP as a direct proxy for cohesin occupancy at CTCF sites assumes that all reads in peaks represent specific binding, which is precisely the assumption the manuscript challenges.
- **Required correction** Clarify the distinction between raw FRiP and background-corrected FRiP throughout the text. Consider introducing a term for the corrected metric to avoid confusion.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility of meta-analysis
- **Affected element** Methods section "Cohesin positioning meta-analysis"
- **Evidence pointer** Table S2
- **Issue** The meta-analysis includes 140 datasets from 13 studies, but the criteria for including or excluding datasets are not described. The handling of datasets with different antibody specificities, cell types, and perturbation methods is not detailed.
- **Required correction** Provide a PRISMA-style flow diagram or a detailed inclusion/exclusion criteria table. Describe how datasets with multiple replicates were handled and whether any datasets were excluded and why.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The Discussion acknowledges limitations but does not address the potential impact of the assumption that CTCF peak positions are unchanged by cohesin perturbations. If cohesin loss alters CTCF binding or chromatin accessibility, the fixed peak definition could bias FRiP calculations.
- **Required correction** Add a paragraph discussing the potential impact of CTCF peak stability on the analysis and suggest how future studies could address this, such as by re-calling peaks in perturbed conditions.

## Risk / unsupported claims
- The claim that background correction is "requisite" for interpreting cohesin cofactor roles is not empirically validated; it is supported only by theoretical modeling.
- The attribution of FRiP variation to "technical effects" is not formally demonstrated through variance decomposition.
- The simulation parameters are stated to be based on mESC measurements but specific sources are not provided, making the parameter choices unverifiable.
- The pipeline validation is described only as "correlations near 1" without specific values or metrics, making the validation claim unverifiable.
- The beta regression results are referenced but not visible, making the statistical claims unverifiable.
- The claim that WIZ depletion has the most substantial increase in FRiP ratio is presented without statistical significance testing or confidence intervals.
- The statement that "accurate background correction is requisite" implies a universal necessity that is not demonstrated across all experimental contexts.