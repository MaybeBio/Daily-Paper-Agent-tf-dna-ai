## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure legends as provided.
- **Assessment boundary** Scientific content, methodological rigor, logical consistency, and support of claims by presented evidence. Editorial and stylistic issues are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors propose that in vitro measurements of transcription factor (TF) binding kinetics and affinities, combined with thermodynamic modeling, can quantitatively predict in vivo TF occupancy and chromatin states at single-molecule resolution. They report that motif recognition probability, rather than bound-state residence time, drives affinity differences; that flanking sequence effects are captured by a linear energy model; and that in vitro biophysical parameters predict in vivo chromatin states for unseen motif configurations.
- **Visible evidence base** High-throughput in vitro binding measurements (HiTS-FLIP), biolayer interferometry, single-molecule footprinting in K562 cells, thermodynamic partition function modeling, stochastic simulations of TF search, and deep learning model comparisons (BPNet, ChromBPNet).
- **Missing materials affecting confidence** Full figure panels and supplementary figures referenced but not fully described in text; exact numerical values for some correlations and fits; details on the SMF state-calling model validation; complete description of the deep learning model architecture and training hyperparameters; raw data for some statistical comparisons.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and technically impressive effort to bridge in vitro biophysical measurements with in vivo chromatin states. The combination of high-throughput binding assays, single-molecule footprinting, and thermodynamic modeling is ambitious and largely successful. The central finding that motif recognition probability, rather than residence time, governs affinity is an important conceptual contribution. However, several concerns regarding the interpretation of the in vivo residence time measurements, the generalizability of the flanking sequence model, and the statistical treatment of some comparisons need to be addressed before the conclusions are fully established.

- **Who would be interested in the results, and why** Researchers in gene regulation, transcription factor biology, chromatin structure, and biophysics will find this work of high interest. The study provides a rare quantitative link between in vitro biochemistry and in vivo chromatin behavior, which is a central goal in the field. The methodological framework combining HiTS-FLIP, SMF, and thermodynamic modeling will be of practical value to labs studying TF-DNA interactions. The findings on flanking sequence effects and nucleosome competition have implications for understanding enhancer function and TF binding site evolution.

- **Major strengths**
  1. The study uses a powerful combination of complementary techniques (HiTS-FLIP, Octet, SMF, modeling) to address a fundamental question in gene regulation.
  2. The finding that motif recognition probability, not residence time, drives affinity is conceptually novel and has broad implications for how TF binding is understood.
  3. The quantitative agreement between in vitro and in vivo measurements, particularly the residence time comparison, is compelling.
  4. The thermodynamic model with few interpretable parameters successfully predicts chromatin states for unseen sequences, demonstrating practical utility.
  5. The careful control experiments (e.g., dead motif, negative controls, density-matched libraries) strengthen the conclusions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the in vivo residence time of KLF at cognate motifs is approximately 1.8 minutes, consistent with in vitro measurements of 1.4 minutes.
- **Evidence pointer** Results section "In vitro and SMF-inferred in nuclei KLF residence times agree"; Figures 4D, 4J, 4K
- **Concern** The inference of in vivo residence time from methylation erosion kinetics relies on several assumptions that are not fully validated. First, the model assumes that methylation is irreversible and that TF rebinding does not occur during the methylation time course. Second, the authors assume that the methylation rate (km) measured at accessible CTCF-flanking bases is identical to the rate at KLF motifs, which may not hold if local chromatin context differs. Third, the model assumes that TF dissociation is the rate-limiting step for methylation, but if methylation itself is slow relative to TF rebinding, the inferred residence time would be an overestimate. The authors should provide additional validation, such as comparing inferred residence times with independent measurements (e.g., FRAP or single-molecule tracking) or demonstrating that the inferred residence time is insensitive to the assumed methylation rate.
- **Why it matters** The agreement between in vitro and in vivo residence times is a central claim of the paper. If the inference method is biased, the conclusion that in vitro kinetics recapitulate in vivo behavior would be weakened.
- **Resolution test** Provide sensitivity analysis showing that inferred residence time is robust to variations in km. Ideally, validate the approach using a TF with a known, independently measured residence time. Alternatively, use a competitor or mutation that alters residence time in a predictable way and show the method captures this change.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that flanking sequence effects on affinity are captured by a linear energy model (extended PWM) with r² = 0.92, and that distal flank effects are due to modulation of hopping probability during TF search.
- **Evidence pointer** Results section "An extended PWM captures flanking sequence effects" and "Distal flanks tuning hopping probabilities during TF search"; Figures 2E, 3I–3K
- **Concern** The extended PWM model is fit to the same data used to evaluate its predictive performance, which may lead to overfitting. The authors report r² values for training and validation, but it is unclear whether the validation set was truly independent (e.g., held out from model fitting). Additionally, the claim that distal flank effects are due to hopping probability is supported primarily by simulation, but the model has several free parameters (khop, xhop, pflip, D1helix, koff,NS) that are not directly constrained by experiment. The authors should demonstrate that the hopping model is uniquely identified by the data, or at least that alternative models (e.g., DNA shape or allostery) cannot reproduce the observed periodicity.
- **Why it matters** The mechanistic interpretation of distal flank effects is a key novel claim. If the model is overparameterized or not uniquely constrained, the conclusion that hopping probability drives these effects is not established.
- **Resolution test** Perform cross-validation where the PWM is fit on a training subset and evaluated on a held-out test set. For the hopping model, perform parameter identifiability analysis (e.g., profile likelihood) and show that the observed periodicity in affinity is robust across a range of physically plausible parameter values. Compare the hopping model's predictions to those of a DNA shape-based model using the same data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that their thermodynamic model, combining in vitro affinities with nucleosome competition, can predict in vivo chromatin states for unseen motif configurations.
- **Evidence pointer** Results section "Thermodynamic model explains in vivo KLF binding across motif number" and "Combined extended PWM and thermodynamic models predict in vivo flanking sequence effects"; Figures 5B, 5C, 6G
- **Concern** The predictive power of the combined model is demonstrated on a library of synthetic constructs integrated at a single genomic locus (AAVS1). It is unclear whether the model would perform as well at endogenous genomic loci, where chromatin context, DNA methylation, and other TFs may influence binding. The authors should discuss the limitations of their model in predicting binding at endogenous loci and ideally test the model on a set of endogenous KLF binding sites.
- **Why it matters** The claim that the model can predict in vivo chromatin states has implications for understanding gene regulation across the genome. If the model only works for synthetic constructs, its general utility is limited.
- **Resolution test** Apply the model to predict KLF occupancy at endogenous loci (e.g., from existing ChIP-seq data) and compare predictions to observed occupancy. If this is not feasible, clearly state the limitations and provide a roadmap for how the model could be extended to endogenous contexts.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction
- **Evidence pointer** Introduction, first paragraph
- **Issue** The introduction assumes familiarity with the "speed-specificity paradox" and "testing state" concepts without sufficient background. Nonspecialist readers may struggle to understand the key conceptual framework.
- **Required correction** Provide a brief explanation of the speed-specificity paradox and the testing state model in accessible language, perhaps with a simple analogy.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, SMF state-calling model
- **Evidence pointer** Methods section "Single-molecule state calling model"
- **Issue** The description of the state-calling model is brief and lacks details on how the model was validated (e.g., against simulated data or known ground truth). The choice of priors and the sensitivity of results to these choices are not discussed.
- **Required correction** Expand the methods to include validation of the state-calling model, such as performance on simulated data with known states, and discuss the sensitivity of results to prior choices.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, Figure 6I
- **Evidence pointer** Results section "Combined extended PWM and thermodynamic models predict in vivo flanking sequence effects"; Figure 6I
- **Issue** The statistical significance of the comparison between high and low GC content flanks is reported with p-values, but the effect size and the number of replicates are not clearly stated. It is unclear whether the observed differences are biologically meaningful.
- **Required correction** Report effect sizes (e.g., mean difference with confidence intervals) and the number of biological replicates for the comparison in Figure 6I.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion focuses heavily on the specific findings for KLF1 and does not sufficiently address the broader implications for other TF families and for understanding gene regulation in general.
- **Required correction** Add a paragraph discussing how the findings might generalize to other TFs, particularly those with different DNA-binding domains, and what this means for the field of gene regulation.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Validation of in vivo residence time inference
  - R1-M2: Model overfitting and parameter identifiability for the extended PWM and hopping model

- **Assessment against Nature-style criteria**
  - **Originality** High. The study presents a novel conceptual framework linking in vitro biophysics to in vivo chromatin states, with the finding on motif recognition probability being particularly original.
  - **Scientific importance** High. The work addresses a fundamental question in gene regulation and provides a quantitative framework that could be broadly applicable. The demonstration that in vitro measurements can predict in vivo behavior is a significant advance.
  - **Interdisciplinary readership** Moderate to high. The work bridges biophysics, molecular biology, and computational biology. The methods and concepts will be of interest to researchers in multiple fields, though some sections may be challenging for nonspecialists.
  - **Technical soundness** Generally strong, but with concerns about the validation of the in vivo residence time inference and the identifiability of the hopping model. These need to be addressed to fully support the conclusions.
  - **Readability for nonspecialists** Moderate. The manuscript is well-written but assumes familiarity with advanced concepts in TF binding kinetics and chromatin biology. The introduction and discussion could be improved to make the work more accessible.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a significant and potentially transformative contribution to the field. The major concerns regarding the validation of the in vivo residence time inference and the identifiability of the hopping model need to be addressed through additional analyses or experiments. If these are satisfactorily resolved, the paper would be suitable for publication in a high-impact journal.

## Risk / unsupported claims
- The claim that in vivo residence time is approximately 1.8 minutes is not fully supported due to potential biases in the inference method (R1-M1).
- The claim that distal flank effects are due to hopping probability is not uniquely established, as the model may be overparameterized (R1-M2).
- The claim that the combined model can predict in vivo chromatin states is only demonstrated for synthetic constructs at a single locus, and its generalizability to endogenous loci is not established (R1-M3).
- The statement that "in vitro and in nuclei measurements exhibit consistent, minutes-long TF residence times" is based on a single comparison and may not be generalizable.
- The claim that the extended PWM captures flanking sequence effects with r² = 0.92 may be optimistic if the validation set is not truly independent.