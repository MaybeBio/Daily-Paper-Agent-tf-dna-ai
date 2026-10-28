## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Methods, Supporting Information references)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and presentation as presented in the provided text
- **Shared manuscript claim summary** The authors present ECHO, a graph-based neural network that incorporates 200-bp resolution Micro-C chromatin contact maps to predict 2,583 chromatin features (TF binding, histone marks, DNase I hypersensitivity) and to characterize collaborative transcription regulation. ECHO reportedly outperforms sequence-based models (DeepCNN, DeepSEA, DanQ) and the graph-based ChromeGCN in prediction accuracy, and interpretability analyses via gradient-based attribution reveal distance-dependent contributions of chromatin contacts and recovery of TF motifs and collaborative binding events.
- **Visible evidence base** Main text figures (Fig 1a–c, Fig 2a–e, Fig 3, Fig 4a–c, Fig 5a–b, Fig 6a–c), Supporting figures (S1–S12), Supporting tables (S1–S3), Algorithm 1, Methods section
- **Missing materials affecting confidence** Actual figure images and supplementary data files were not provided; only figure captions and in-text descriptions were available. Exact hyperparameter values, model architecture dimensions, and full ablation details were not fully specified. Code availability and data accession details were not stated in the provided text.

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in computational genomics by integrating high-resolution 3D chromatin organization into deep learning-based prediction of chromatin features. The core idea of transforming graph-structured contact data into grid-structured representations amenable to convolution is technically sound and represents a meaningful advance over prior sequence-only models. The performance improvements reported are substantial and statistically well-supported. The interpretability analyses are thoughtful and provide biological insights that go beyond simple prediction. However, several technical details require clarification, particularly regarding the neighborhood sampling strategy, the handling of cell-type heterogeneity, and the statistical rigor of some comparisons. The claim of recovering collaborative TF binding is intriguing but would benefit from more direct validation. Overall, the work is potentially suitable for publication in a computational biology journal, but the case would be strengthened by addressing the concerns below.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, deep learning applications in genomics, and 3D genome organization would find this work directly relevant. Researchers developing interpretable deep learning models for biological sequence and structure data would also be interested in the attribution methodology. Additionally, experimental biologists studying transcriptional regulation, particularly those interested in TF cooperativity and long-range regulatory interactions, may find the biological insights valuable.

- **Major strengths** 1) The integration of high-resolution Micro-C data (200-bp) represents a methodological advance over prior work using lower-resolution Hi-C (1-kb), enabling more precise characterization of regulatory interactions. 2) The systematic comparison against multiple sequence-based baselines and the graph-based ChromeGCN provides a rigorous performance assessment. 3) The distance-stratified analysis of contact contributions reveals biologically interpretable patterns that align with known regulatory mechanisms. 4) The attribution framework extends interpretability beyond sequence-only models to include spatial interaction contributions, enabling discovery of collaborative TF binding. 5) The use of neighborhood sampling and mini-batch training addresses scalability concerns that limit prior graph-based approaches.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "ECHO predicted 2,583 chromatin features with significantly higher average AUROC and AUPR than the best sequence-based model"
- **Evidence pointer** Fig 1b, Fig 1c, S1 Fig, S2 Table
- **Concern** The performance comparison against sequence-based baselines may be confounded by the pre-training strategy. The authors state that ECHO uses DeepCNN (or DeepSEA/DanQ) as a pre-trained model for the sequence layers, with these pre-trained layers frozen. This means ECHO inherits representations from the baseline models. The reported improvement could partly reflect the additional graph layers and neighborhood information, but it is unclear how much of the improvement is attributable to the graph component versus the fine-tuning of the prediction layer. A cleaner ablation would compare ECHO against the same baseline model with an equivalent number of additional parameters but without graph information.
- **Why it matters** Without this ablation, the specific contribution of the graph-based neighborhood aggregation to the performance gain is not cleanly isolated. This is central to the paper's core claim that incorporating 3D chromatin organization improves prediction.
- **Resolution test** Provide an ablation where the baseline model is augmented with additional non-graph layers of comparable capacity to the graph layers, or where the graph layers are replaced with randomly connected neighbors to control for the effect of additional parameters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We observed that chromatin contacts of different distances affected different types of chromatin features' prediction in diverse ways, suggesting complex and divergent collaborative regulatory mechanisms"
- **Evidence pointer** Fig 2a–e, S7 Fig
- **Concern** The distance-stratified analysis separates contacts into four bins (0–1 kb, 1–5 kb, 5–20 kb, >20 kb) and evaluates model performance using only each bin. However, the statistical comparison between distance bins appears to rely on paired t-tests across features. It is unclear whether multiple testing corrections were applied given that 2,583 features are being compared. Additionally, the interpretation of "improvement" for a given distance bin is relative to the DeepCNN baseline, but the baseline itself does not use any spatial information. A more informative comparison would be against ECHO using all contacts, to understand which distance ranges are most informative relative to the full model.
- **Why it matters** The claim of distance-dependent regulatory mechanisms is a key biological finding. If the statistical comparisons are not properly controlled, the reported patterns may be overstated. The interpretation would also be strengthened by comparing against the full model rather than only the sequence-only baseline.
- **Resolution test** Report multiple-testing-corrected p-values (e.g., Benjamini-Hochberg FDR) for the distance-bin comparisons. Additionally, include a comparison of each distance bin against the full ECHO model with all contacts to assess the marginal contribution of each distance range.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality
- **Claim pointer** "The attributions on DNA sequences identify TF binding motifs and TF collaborative binding"
- **Evidence pointer** Fig 5a–b, Fig 6a–c, S10 Fig
- **Concern** The identification of TF collaborative binding relies on the co-occurrence of high-attribution motifs in central and neighbor sequences connected by high-attribution contacts. However, the validation of these predicted collaborative events appears to be limited to literature-based consistency checks. The authors mention that "some were consistent with existing biological knowledge," but no systematic enrichment analysis or comparison against known TF-TF interactions (e.g., from ChIP-seq co-occupancy or protein-protein interaction databases) is presented. The example of the ELF1 motif and ZBTF3 proximity to CTCF is suggestive but anecdotal.
- **Why it matters** The claim of recovering collaborative TF binding is a significant interpretability result. Without systematic validation, it is difficult to assess whether the identified events represent true biological cooperativity or statistical artifacts of the attribution method.
- **Resolution test** Perform a systematic enrichment analysis of predicted collaborative TF pairs against known TF-TF interactions from databases such as ENCODE ChIP-seq co-occupancy, STRING, or CORUM. Report odds ratios and significance levels for the enrichment.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "ECHO with Micro-C contact maps predicted chromatin features with a mean AUROC of 0.921, which was significantly higher than ECHO with 83M Hi-C contacts (AUROC 0.914, p-value 7.08E−6)"
- **Evidence pointer** Fig 3
- **Concern** The comparison between Micro-C and Hi-C resolution is confounded by the number of contacts used. The Micro-C map has 77M contacts, while the Hi-C-derived maps have 61M and 83M contacts. The authors state that Micro-C outperforms Hi-C even with fewer contacts, which supports the resolution argument. However, the sampling strategy for converting 1-kb Hi-C bins to 200-bp resolution is described as connecting the centered 200-bp bin with the original 200-bp central sequence. This creates artificial 200-bp contacts that may not reflect true chromatin interactions at that resolution. The comparison may therefore not be a fair test of resolution effects.
- **Why it matters** The claim that high-resolution Micro-C is critical for performance is a central methodological contribution. If the Hi-C downsampling strategy introduces artifacts, the comparison may be biased in favor of Micro-C.
- **Resolution test** Provide additional validation of the Hi-C to 200-bp conversion strategy, such as comparing against a native 200-bp Hi-C dataset if available, or demonstrating that the conversion does not introduce systematic biases. Alternatively, compare Micro-C and Hi-C at matched contact counts to isolate resolution effects.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "ECHO used neighborhood sampling and mini-batch training which made it applicable to large graphs"
- **Evidence pointer** Methods, Algorithm 1
- **Concern** The neighborhood sampling strategy is described conceptually, but key implementation details are missing. Specifically, the authors do not specify how the number of sampled neighbors (kc) is determined, how the threshold τ for contact filtering is chosen, or how the trade-off between sampling coverage and computational efficiency is managed. The choice of kc = 50 spatial neighbors and ks = 10 sequential neighbors appears arbitrary without sensitivity analysis.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without clear specification of hyperparameters and sensitivity analyses, other researchers cannot reliably implement or adapt the method.
- **Resolution test** Provide a sensitivity analysis for key hyperparameters (kc, ks, τ) and report the impact on model performance. Include the full hyperparameter configuration in the Methods or Supplementary Materials.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "ECHO predicted 2,583 chromatin features with significantly higher average AUROC and AUPR than the best sequence-based model" but does not specify which baseline was the "best" or how "best" was determined across the three baselines tested.
- **Required correction** Specify which baseline model achieved the best performance and clarify whether "best" was determined per feature or on average.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Fig 1b
- **Evidence pointer** Fig 1b
- **Issue** The p-values reported for AUROC and AUPR comparisons (e.g., 6.73E−97) are extremely small, which may reflect the large number of features tested rather than meaningful effect sizes. The effect sizes (differences in AUROC/AUPR) are not reported.
- **Required correction** Report effect sizes alongside p-values, and consider reporting median or interquartile ranges of AUROC/AUPR distributions rather than only means.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods, Model training
- **Issue** The authors state that "the rest of the genome was segmented into 200-bp bins" and that bins were labeled based on overlap with peaks, but the exact criteria for handling bins with partial overlap or ambiguous labels are not specified.
- **Required correction** Clarify the labeling criteria, including how bins with partial peak overlap are handled and whether any filtering of low-confidence bins was applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Fig 4c
- **Evidence pointer** Fig 4c
- **Issue** The description of Fig 4c mentions "all" as a baseline for CTCF interaction percentages, but it is unclear whether this baseline includes all contacts regardless of attribution score or all contacts with any attribution score above zero.
- **Required correction** Clarify the definition of the "all" baseline in the figure legend or main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Fig 6a
- **Evidence pointer** Fig 6a
- **Issue** The identification of a FOS:JUN related pattern and a CAGGTG pattern in the neighborhood of SMAD5 binding sites is presented as evidence of collaborative regulation. However, the statistical significance of these motif enrichments relative to background is not reported.
- **Required correction** Report enrichment statistics (e.g., hypergeometric test p-values) for the identified motifs against appropriate genomic background.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion mentions that "ECHO identifies collaborative bindings by discovering sequence patterns on both the central sequences and the neighborhood sequences," but the distinction between "collaborative binding" and simple co-occurrence of TF motifs in spatially proximal regions is not clearly defined.
- **Required correction** Provide a clear operational definition of "collaborative binding" as used in this work, and discuss the limitations of inferring cooperativity from motif co-occurrence alone.

## Risk / unsupported claims
- The claim that ECHO "characterize[s] collaborative transcription regulation" is partially supported by the interpretability analyses, but the functional validation of predicted collaborative events is limited to literature-based consistency. The claim is therefore only weakly supported.
- The claim that "high-resolution Micro-C contact maps provide more precise chromatin contact information" is supported by the performance comparison, but the potential artifacts in the Hi-C downsampling strategy (R1-M4) mean this claim is not fully established.
- The claim that ECHO "could identify collaborative bindings guided by chromatin contact maps, without a range limit" is not directly tested. The authors demonstrate motif recovery in neighbor sequences, but do not systematically compare the range of detected interactions against sequence-only models with large receptive fields.
- The statement that "ECHO with Micro-C contact maps using fewer contacts outperformed ECHO with Hi-C contact maps" is presented as evidence for resolution effects, but the difference in contact counts (77M vs 61M/83M) is not large, and the comparison may be confounded by the downsampling strategy.
- The generalizability of ECHO to other cell types and chromatin features beyond those tested is not assessed. The authors note that chromatin features are from multiple cell lines but only two Micro-C maps are used, and the potential cell-type mismatch is not discussed in detail.