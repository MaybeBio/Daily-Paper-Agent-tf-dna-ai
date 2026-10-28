## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary references)
- **Assessment boundary** Scientific and technical evaluation of the presented claims, methods, and results; no assessment of code functionality or reproducibility beyond what is described
- **Shared manuscript claim summary** The authors present Chiron3D, a DNA-only deep learning framework that predicts CTCF Hi-C/HiChIP contact maps at 524 kb windows with nucleotide-level interpretability. They claim competitive performance against C.Origami (including a CTCF ChIP-seq augmented variant), and use attribution and sparse edit simulations to derive mechanistic insights into loop asymmetry and stability, specifically that boundary CTCF motif strength/count governs anchorage and that intra-loop CTCF sites destabilize loops.
- **Visible evidence base** Main text figures referenced (Fig. 1, 2, 3, 4), supplemental figures S1-S9, supplemental tables S1-S2, methods descriptions, benchmark comparisons, edit simulation results
- **Missing materials affecting confidence** Actual figure images, supplemental methods details, hyperparameter settings, training/validation splits, full benchmark results, code repository contents, exact definitions of metrics (e.g., Asym, Stab equations not fully shown), and details of the Ledidi adaptation

## Reviewer

- **Overall assessment** This manuscript presents a potentially valuable contribution to the field of 3D genome prediction and interpretation. The core idea of a DNA-only model with nucleotide-level interpretability for CTCF-mediated looping is timely and relevant. The reported performance matching a ChIP-seq augmented model is encouraging. However, the manuscript as provided has several significant gaps in methodological detail and validation that prevent full assessment of the claims. The mechanistic insights, while interesting, are largely confirmatory of existing literature and the novelty of the specific findings needs clearer articulation. The single cell line focus and in silico-only validation limit the strength of the conclusions. The writing is generally clear but some technical details are missing.

- **Who would be interested in the results, and why** Researchers in computational genomics, 3D genome organization, gene regulation, and chromatin biology would be interested. Specifically, those developing or using deep learning models for genome structure prediction, those studying CTCF-mediated loop extrusion mechanisms, and those interested in interpreting non-coding variants in disease contexts would find the framework and insights relevant. The interpretability aspect would appeal to those seeking causal understanding from predictive models.

- **Major strengths**
  1. The DNA-only design with interpretability is a clear advance over models requiring additional epigenetic inputs, enabling direct sequence-to-structure analysis.
  2. The combination of attribution (TF-MoDISco) and sparse edit (Ledidi) frameworks provides a coherent pipeline for hypothesis generation and testing in silico.
  3. The benchmarking against C.Origami, including a ChIP-seq augmented variant, is appropriate and the reported performance parity is notable.
  4. The systematic analysis of loop asymmetry and stability with quantitative scores (Asym, Stab) provides a framework for future studies.
  5. The identification of known SNPs among proposed edits adds translational relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Chiron3D accurately predicts HiChIP contact maps from DNA sequence alone" and "competitive with baselines that take CTCF ChIP-seq as additional input"
- **Evidence pointer** Section 3.1, Figure 2B-C
- **Concern** The performance comparison is presented with only summary metrics (SSIM, MSE, Pearson, Spearman) and a single figure panel. Critical details are missing: the exact train/validation/test split (are test chromosomes held out?), the number of training windows, the training time, the variance across seeds, and whether the C.Origami models were retrained or used from prior work with the same data. Without these details, the claim of "competitive" performance cannot be fully evaluated. Additionally, the comparison to C.Origami with ChIP-seq input is only shown for one cell line, limiting generalizability.
- **Why it matters** The central claim of the paper is that a DNA-only model can match or exceed models with additional epigenetic input. If the comparison is not rigorously controlled, the claim is weakened. Reproducibility and fair benchmarking are essential for the community to trust and build upon these results.
- **Resolution test** Provide full experimental setup: data splits, hyperparameters, training details, number of seeds, and statistical significance tests for metric differences. Ideally, show performance on multiple cell lines and include a comparison to a DNA-only C.Origami variant trained under identical conditions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Using targeted, single-nucleotide edit simulations with Chiron3D, we show that both loop strength and stability can be precisely controlled."
- **Evidence pointer** Section 3.2, 3.3, Figures 3D-I, 4C-H
- **Concern** The edit simulation results are presented for a small number of examples (one detailed example for asymmetry, one for stability) and aggregate statistics. The claim of "precise control" is strong and requires more systematic validation. Specifically: (1) How many edit simulations were performed in total? (2) What is the success rate of edits achieving the desired direction of change? (3) Are there negative controls (e.g., edits at random positions, or edits that should have no effect)? (4) How robust are the predictions to model uncertainty? (5) The relationship between predicted changes and actual experimental outcomes is not tested, which is a major limitation for the "control" claim.
- **Why it matters** The mechanistic insights and the utility of the framework for predicting variant effects depend on the reliability of the edit simulations. If the model's predictions are not validated against experimental data, the claims of "control" and "precise" are overstated. The paper would be significantly strengthened by experimental validation of at least a few predicted edits.
- **Resolution test** Provide a systematic evaluation of edit simulations: number of edits, success rates, negative controls, and ideally experimental validation (e.g., CRISPR editing or reporter assays) for a subset of predictions. If experimental validation is not possible, temper the language from "control" to "predicted modulation" and clearly state the in silico-only nature of the validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Originality / Scientific importance
- **Claim pointer** "we provide likely mechanistic insights into the physical control of loop dynamics. Specifically, we find that the strength of the loop extrusion anchorage site is largely governed by the amount and binding affinity of CTCF sites at the boundaries. Furthermore, we reveal that loop stability is regulated by the amount of intra-loop CTCF binding sites, where fewer intra-loop sites are associated with greater loop stability."
- **Evidence pointer** Section 3.2, 3.3, Figures 3, 4
- **Concern** The finding that boundary CTCF motif strength/count governs anchorage is consistent with established literature (e.g., Vian et al. 2018, and many others). The finding regarding intra-loop CTCF sites and stability, while interesting, needs to be positioned more clearly against existing knowledge. Is this a novel observation, or a confirmation of prior hypotheses? The authors should explicitly state what is new here beyond what is already known. The mechanistic insights are presented as "likely" and "reveal," but the evidence is correlative (from model attributions) and in silico, not causal.
- **Why it matters** For a Nature-style audience, the novelty and significance of the biological insights are critical. If the findings are largely confirmatory, the paper's impact is reduced. The authors need to clearly articulate the new knowledge gained from their approach.
- **Resolution test** Add a dedicated section in the Discussion that explicitly compares the findings to prior literature, highlighting what is novel and what is confirmatory. Consider whether the intra-loop CTCF finding can be tested against existing Hi-C or HiChIP datasets across multiple cell types to strengthen the claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** "Chiron3D approximates cell-type-specific HiChIP structures and enables mechanistic manipulation of sequence features governing stripe formation and loop stability"
- **Evidence pointer** Section 4 (Discussion)
- **Concern** The manuscript is written primarily for a computational biology audience. The biological implications and the significance of the findings for understanding gene regulation, development, or disease are not fully developed. The discussion of disease relevance is brief and speculative. For a broader readership, the authors should more clearly explain why understanding loop stability and asymmetry matters for biology and medicine.
- **Why it matters** The potential impact of the work extends beyond computational genomics. If the biological significance is not clearly articulated, the paper may not appeal to a wider audience, limiting its influence.
- **Resolution test** Expand the Discussion to include a more accessible explanation of the biological importance of loop dynamics, with concrete examples of how this framework could be applied to study disease-associated variants or developmental processes.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction and Methods
- **Evidence pointer** Section 1, Section 2
- **Issue** The introduction assumes significant prior knowledge of 3D genome terminology (e.g., "stripes," "corner interactions," "loop extrusion") without sufficient explanation for a general reader. The Methods section is dense and some equations (Asym, Stab) are not fully defined in the main text.
- **Required correction** Provide brief definitions or a glossary for key terms in the introduction. Ensure all equations are fully defined in the main text or clearly referenced to the supplement.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Data and code availability
- **Evidence pointer** Data availability section
- **Issue** The code repository link is provided, but it is not stated whether the code is versioned, documented, and includes the trained model weights. The processed data are on Zenodo, but the exact contents are not described.
- **Required correction** Clarify the contents of the repository and Zenodo record, including model weights, training scripts, and a minimal example to reproduce the main results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Section 4
- **Issue** The discussion of limitations is brief. The authors acknowledge the single cell line focus and in silico validation, but do not discuss potential biases in the training data, the resolution limits of the model, or the generalizability to other species or assay types.
- **Required correction** Expand the limitations paragraph to address these points and suggest concrete future directions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The description of the data processing is incomplete. It is not clear how the HiChIP contact maps were normalized, what the effective sequencing depth was, or how the 5 kb resolution was chosen. The filtering of stable loops with FitHiChIP is mentioned but the parameters are not given.
- **Required correction** Provide more detail on data preprocessing, including normalization methods and parameters for FitHiChIP.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Results, Section 3.2
- **Evidence pointer** Section 3.2, Figure 3
- **Issue** The example of a single edit at a specific locus (chr2: 241.17-241.38 Mb) is informative but the choice of this example and its representativeness is not discussed. The figure legend is not provided, making it difficult to interpret the panels.
- **Required correction** Provide figure legends and explain why this example was chosen. Discuss whether the observed effect is typical across all tested loci.

## Risk / unsupported claims
- The claim of "precise control" of loop strength and stability via single-nucleotide edits is not supported by experimental validation; the evidence is entirely in silico.
- The claim that Chiron3D "matches" the performance of ChIP-seq augmented C.Origami is based on a single cell line and limited metrics; statistical significance is not reported.
- The mechanistic insight that "loop stability is regulated by the amount of intra-loop CTCF binding sites" is presented as a novel finding, but the comparison to prior literature is insufficient to establish novelty.
- The generalizability of the model to other cell types, species, or assay types is not demonstrated and is stated as a limitation, but the claim of "cell-type specific manner" training suggests this is a key feature that needs more validation.
- The statement that the framework "can identify naturally occurring variants that may influence chromatin architecture" is based on overlap with dbSNP, but the functional impact of these variants is not tested.