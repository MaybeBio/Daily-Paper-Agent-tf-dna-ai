## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific claims, methodology, and evidence as presented in the provided manuscript text; no external data or code were accessed
- **Shared manuscript claim summary** The authors present an iterative deep learning-based design pipeline for synthetic human enhancers with cell type-specific activity. They train models on published MPRA and chromatin accessibility data, design and experimentally validate enhancer libraries across two design-build-test cycles, and report improved specificity in the second round. They further characterize sequence features (motif density, motif vocabulary), perform perturbation experiments, and use single-cell MPRA to link enhancer activity to transcription factor expression.
- **Visible evidence base** Main text figures (Fig. 1–5), supplementary figures (Fig. S1–S9), supplementary tables (Table S1–S7), methods section
- **Missing materials affecting confidence** Raw sequencing data, code, and processed data files are referenced but not accessible for verification; figure panels are not viewable in this text-only format; detailed model hyperparameters and architecture schematics are partially described but not fully specified

## Reviewer
- **Overall assessment** This manuscript presents a well-executed and thoughtfully analyzed study on deep learning-based design of cell type-specific enhancers. The iterative design-build-test approach is a valuable contribution, and the demonstration that small amounts of high-quality synthetic data can improve model performance is notable. The combination of bulk MPRA, single-cell MPRA, and perturbation experiments provides a multi-layered characterization of the designed enhancers. However, several technical concerns regarding model evaluation, statistical rigor, and the interpretation of motif analyses need to be addressed before the central claims are fully established.

- **Who would be interested in the results, and why** Researchers in synthetic biology, regulatory genomics, and computational biology would find this work of interest. The iterative design strategy and the finding that compact, high-density motif grammars can drive cell type-specificity have direct implications for gene therapy and cell engineering. The demonstration that models trained on chromatin accessibility alone can generate functional enhancers is also relevant to those working in systems where MPRA data are unavailable.

- **Major strengths**
  1. The iterative design-build-test cycle is a clear methodological advance over single-round design approaches.
  2. The use of multiple design algorithms (Simulated Annealing, Fast SeqProp, DENs) and two training data types (MPRA, DHS) strengthens the generalizability of the findings.
  3. The combination of bulk and single-cell MPRA provides complementary views of enhancer activity.
  4. The perturbation experiments (ablations) directly test causal contributions of identified motifs.
  5. The finding that 50 bp enhancers can maintain specificity has practical implications for vector design.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "Iterative retraining results in dramatic performance improvements" and "R2 enhancers outperformed those in all other libraries 92.6% (HepG2) or 81.1% (K562) of the time"
- **Evidence pointer** Fig. 1F, Fig. S4A, bootstrap analysis section
- **Concern** The bootstrap analysis used to compare library performance resamples from the same measured data. This does not account for systematic biases between libraries (e.g., different synthesis batches, different transfection efficiencies, different sequencing depths). The claim of "dramatic improvement" relies on this comparison, but the statistical framework does not appear to model batch effects or other technical confounders.
- **Why it matters** If the improvement in R2 is partly due to technical factors rather than improved model performance, the central claim of iterative improvement is weakened.
- **Resolution test** Provide an analysis that explicitly models batch effects (e.g., using a mixed-effects model with library as a fixed effect and replicate as a random effect), or demonstrate that the improvement persists when comparing only sequences synthesized and assayed in the same batch.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model evaluation
- **Claim pointer** "Prediction-measurement correlations from all models were on par with inter-replicate correlations"
- **Evidence pointer** Fig. S1C, Methods section "R1-MPRA model training"
- **Concern** The statement that model performance is "on par with inter-replicate correlations" is used to justify model quality, but the inter-replicate correlation is not reported numerically. Moreover, the correlation metric used (Pearson vs Spearman) is not consistently specified. The comparison between model prediction and measurement correlation versus inter-replicate correlation is only meaningful if both are computed on the same scale and with the same metric.
- **Why it matters** Without a clear benchmark, the reader cannot assess whether the models are genuinely predictive or merely capturing noise.
- **Resolution test** Report the exact correlation values (with confidence intervals) for both model predictions and inter-replicate comparisons, using the same metric. Additionally, report performance on held-out sequences that were not used in any stage of training or design.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of motif analyses
- **Claim pointer** "Motif density increased significantly over successive design rounds" and "TP53 was dramatically enriched in both R1-MPRA and R2"
- **Evidence pointer** Fig. 2A–E, motif calling methods
- **Concern** The motif analysis relies on scanning with JASPAR position weight matrices and a custom clustering algorithm. The authors do not report how sensitive the results are to the choice of motif database, the p-value/q-value thresholds, or the clustering parameters. The dramatic enrichment of TP53 in designed sequences could be an artifact of the model exploiting a simple, high-information-content motif that is easy to optimize, rather than a biologically meaningful driver of specificity.
- **Why it matters** The claim that the models "discover" important motifs is central to the paper's mechanistic interpretation. If the motif enrichment is an artifact of the optimization procedure, the biological conclusions are overstated.
- **Resolution test** Perform a control analysis where motifs are called using a different database (e.g., CIS-BP) and different thresholds, and show that the enrichment patterns are robust. Additionally, test whether random sequences with similar GC content and motif density (but different motif identities) show similar activity profiles.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Single-cell MPRA interpretation
- **Claim pointer** "Enhancer activity is correlated with transcription factor expression at the single cell level"
- **Evidence pointer** Fig. 5C–H, Fig. S9
- **Concern** The single-cell MPRA analysis correlates enhancer activity with TF expression across cells. However, the analysis appears to be correlational and does not establish causality. The authors acknowledge this in the Discussion, but the presentation in the Results section is somewhat stronger than the evidence supports. Additionally, the number of cells and the statistical model used for the correlation are not fully described.
- **Why it matters** The claim of a link between TF expression and enhancer activity is interesting but requires careful statistical treatment to rule out confounding factors (e.g., cell cycle, transfection efficiency).
- **Resolution test** Provide details on the number of cells, the statistical test used, and whether the correlation holds when controlling for cell cycle or other covariates. Consider a permutation-based null model to assess significance.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "Our design methods embed relevant TFBS motifs with higher frequencies than comparable endogenous enhancers while using a more selective motif vocabulary"
- **Evidence pointer** Fig. 2D–E, motif analysis
- **Concern** The claim of "more selective motif vocabulary" is based on comparison to endogenous enhancers from the training data. However, the designed sequences are shorter (50–145 bp) than typical endogenous enhancers, and the comparison may not be apples-to-apples. The authors do not control for sequence length or GC content in this comparison.
- **Why it matters** If the apparent selectivity is simply a consequence of shorter sequences having less room for spurious motif hits, the conclusion is misleading.
- **Resolution test** Compare motif vocabulary and density in designed sequences against length-matched and GC-matched endogenous enhancer fragments.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 1C–F
- **Evidence pointer** Fig. 1
- **Issue** The figure panels are described in the text but the actual data distributions (e.g., scatter plots, box plots) are not visible in this text-only format. The text refers to "median log2FCH2K" values but does not report the full distribution or variability.
- **Required correction** In the figure legends or main text, report the number of sequences per category and the interquartile ranges for the key metrics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "R1-DHS design and model training"
- **Evidence pointer** Methods section
- **Issue** The GAN training procedure is described at a high level, but key hyperparameters (e.g., learning rate, batch size, number of epochs, architecture details) are not provided. The classifier training also lacks specific details on the architecture and optimization.
- **Required correction** Provide a table of hyperparameters for all models (CNN, GAN, classifier) in the Methods or Supplementary Information.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Bootstrap analysis
- **Evidence pointer** Fig. 1F
- **Issue** The bootstrap analysis reports percentages (e.g., 92.6%) but does not report confidence intervals for these percentages.
- **Required correction** Report 95% confidence intervals for the bootstrap percentages.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Ablation analysis
- **Evidence pointer** Fig. 3B–H
- **Issue** The ablation scores are reported as fractions, but the text does not clarify whether these are relative to the original enhancer activity or to a control (e.g., scrambled sequence). The definition in the Methods is clear, but the presentation in the Results could be more explicit.
- **Required correction** In the Results, restate the definition of the ablation score and clarify what a score of 0 or 1 means in practical terms.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion mentions "future work" but does not address the limitation that only two cell lines were tested. The authors should explicitly discuss how the approach might generalize to other cell types and whether the motif grammar learned here is likely to be cell type-specific or general.
- **Required correction** Add a paragraph in the Discussion addressing the generalizability of the approach to other cell types and potential limitations of the two-cell-line system.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 5
- **Evidence pointer** Fig. 5A
- **Issue** The schematic in Fig. 5A is described in the text but the details of the scMPRA workflow are complex. A step-by-step description in the figure legend would improve readability.
- **Required correction** Expand the Fig. 5A legend to include a step-by-step description of the scMPRA workflow.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Data and code availability section
- **Issue** The code repository is referenced but not linked in the text provided. The authors should ensure the link is active and that all code needed to reproduce the analyses is included.
- **Required correction** Verify the repository link and include a statement about code availability in the main text.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Fig. 2G
- **Evidence pointer** Fig. 2G
- **Issue** The dose-response analysis for motif multiplicity shows saturation effects, but the text does not discuss whether this saturation is due to physical constraints (e.g., steric hindrance) or model limitations.
- **Required correction** Add a brief discussion of the potential mechanisms underlying the observed saturation in motif multiplicity effects.

## Risk / unsupported claims
1. The claim that "iterative retraining results in dramatic performance improvements" is not fully supported without a formal statistical comparison that accounts for batch effects and other technical confounders.
2. The claim that "enhancer activity is correlated with transcription factor expression at the single cell level" is presented as a key finding, but the analysis is correlational and the statistical framework is not fully described.
3. The claim that designed enhancers use a "more selective motif vocabulary" than endogenous enhancers is not adequately controlled for sequence length and GC content.
4. The generalizability of the design approach to other cell types is asserted but not tested; the authors only demonstrate results in two cell lines.
5. The performance of the GAN-based design approach (R1-DHS) is compared to MPRA-based design (R1-MPRA), but the comparison may be confounded by differences in training data size, quality, and design objectives.