## Review setup
- **Input scope** Full manuscript text, including abstract, results, methods, and supplementary figure references
- **Assessment boundary** Scientific validity, methodological rigor, and claims as supported by the provided evidence; no assessment of code availability or data accessibility beyond what is stated
- **Shared manuscript claim summary** The authors present Shorkie, a masked DNA language model pretrained on fungal genomes, which when fine-tuned on yeast RNA-seq and chromatin data substantially improves expression prediction over random initialization, recovers known TF motifs, tracks dynamic motif usage across TF induction time courses, and outperforms leading models in cis-eQTL classification and MPRA concordance
- **Visible evidence base** Main text figures (Figure 1-7), supplementary figure references (S1-S25), detailed methods for model architecture, training, and evaluation
- **Missing materials affecting confidence** Actual figure images, quantitative performance values in main text, baseline model details, hyperparameter search details, statistical significance tests, and complete evaluation metrics

## Reviewer
- **Overall assessment** This manuscript presents a compelling application of self-supervised pretraining to yeast gene expression prediction, with a thoughtful focus on evolutionary scale selection. The core finding that pretraining on 165 Saccharomycetales genomes outperforms both single-genome and pan-fungal pretraining is well-motivated and potentially impactful. However, the manuscript as provided lacks quantitative details in the main text that are essential for evaluating the magnitude of improvements, and several methodological choices require clarification. The claims about dynamic motif tracking and variant effect prediction are intriguing but need stronger statistical support and clearer baselines. The work is likely of interest to the regulatory genomics and deep learning communities, but the current evidence base is insufficient to fully establish the superiority claims over existing methods.

- **Who would be interested in the results, and why** Computational biologists working on regulatory genomics, particularly those developing sequence-to-expression models; yeast geneticists interested in cis-regulatory code and TF dynamics; machine learning researchers studying transfer learning and pretraining strategies for genomic data. The demonstration that evolutionary-scale pretraining matters for downstream task performance has implications beyond yeast, potentially informing pretraining strategies for other organisms with limited labeled data.

- **Major strengths** The systematic comparison of pretraining across four evolutionary scales is a well-designed ablation that directly addresses the question of optimal training data composition. The integration of diverse data types (RNA-seq, ChIP-exo, MNase) into a unified framework is ambitious and appropriate for the goal of comprehensive expression prediction. The use of interpretability analyses (ISM, attention visualization) to connect model predictions to biological mechanisms strengthens the biological relevance of the approach. The inclusion of newly generated high-resolution induction time-course data is a valuable community resource.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Shorkie achieved median bin-level Pearson's R of 0.78 versus 0.67 for Shorkie_Random_Init" and "gene-level Pearson's R of 0.88 versus 0.74"
- **Evidence pointer** Results section "Shorkie: LM transfer learning enables improved gene expression prediction"; Figure 3C-E
- **Concern** The main text reports only median correlation values without confidence intervals, per-fold variability, or statistical significance testing. The improvement from 0.67 to 0.78 in bin-level correlation is presented as substantial, but without error bars or significance tests, it is impossible to assess whether this improvement is robust across folds or driven by specific chromosomes or gene sets. Additionally, the gene-level comparison (0.88 vs 0.74) lacks information on the distribution of per-gene correlations, which could reveal whether improvements are concentrated in particular gene categories.
- **Why it matters** The central claim of the manuscript is that pretraining improves expression prediction. Without proper uncertainty quantification and significance testing, the magnitude and reliability of this improvement cannot be evaluated. This is the foundation upon which all subsequent claims rest.
- **Resolution test** Provide per-fold performance values, confidence intervals for median correlations, and statistical tests (e.g., paired tests across genes or folds) comparing Shorkie to Shorkie_Random_Init. Report the distribution of per-gene correlations, not just the median.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** "Shorkie accurately predicted variant effects, outperforming leading sequence-to-expression models in cis-eQTL classification"
- **Evidence pointer** Results section "Shorkie predicts cis-eQTL regulatory impacts"; Figure 7E-H
- **Concern** The cis-eQTL evaluation compares Shorkie to DREAM challenge models, but the DREAM models were trained on MPRA data, not endogenous expression data. This is a fundamental distribution shift that disadvantages the DREAM models. The manuscript acknowledges this for MPRA evaluation but not for eQTL evaluation. Additionally, the negative control sampling procedure is described but the matching quality (distance distribution, allele frequency distribution) between positive and negative sets is not reported. The classification metrics (AUROC, AUPRC) are reported without confidence intervals or significance tests.
- **Why it matters** The claim of outperforming leading models in eQTL classification is central to the variant effect prediction contribution. If the comparison is unfair due to training distribution mismatch, the conclusion may not hold. The negative control quality directly affects the validity of the classification evaluation.
- **Resolution test** Either train DREAM models on endogenous data or clearly state and justify the comparison as zero-shot transfer. Report matching quality statistics for negative controls. Provide confidence intervals for AUROC/AUPRC and significance tests comparing models.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability validation
- **Claim pointer** "Shorkie LM identified canonical motifs including Poly(dA:dT), Cbf1, Tye7, and Reb1" and "Shorkie recapitulated RRPE and PAC motifs"
- **Evidence pointer** Results section "Shorkie LM captures regulatory conservation"; Figure 2B-D, Figure 4A-C
- **Concern** The motif discovery results are presented qualitatively with example logos, but there is no quantitative comparison to known motif databases or assessment of motif discovery accuracy. The claim that Shorkie "recapitulated" motifs is based on visual inspection of logos. For the dynamic motif analysis, the temporal changes are described but not quantified or tested for statistical significance. The relationship between ISM importance and actual TF binding affinity is assumed but not validated.
- **Why it matters** The interpretability analyses are presented as evidence that the model has learned biologically meaningful representations. Without quantitative validation, these claims remain anecdotal. The dynamic motif tracking is a novel contribution that requires rigorous statistical support.
- **Resolution test** Provide quantitative motif matching scores (e.g., Tomtom q-values) for discovered motifs against known databases. For dynamic analyses, report effect sizes and significance tests for temporal changes in motif importance. Validate ISM importance against independent TF binding data where available.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Baseline adequacy
- **Claim pointer** "Shorkie substantially improves gene expression prediction compared to baselines trained without self-supervision"
- **Evidence pointer** Results section "Shorkie: LM transfer learning enables improved gene expression prediction"; Figure 3C-E
- **Concern** The only baseline presented is Shorkie_Random_Init, which uses identical architecture but random initialization. While this isolates the contribution of pretraining, it does not compare against existing state-of-the-art expression prediction models for yeast, such as those based on convolutional architectures trained from scratch on yeast data, or simpler sequence-based features. The manuscript mentions DREAM models for eQTL but not for expression prediction.
- **Why it matters** The claim of "substantial improvement" needs context. If simpler models achieve comparable performance, the value of the pretraining approach is diminished. The comparison to random initialization shows pretraining helps, but not whether this approach is competitive with or superior to existing methods.
- **Resolution test** Include at least one additional baseline: a state-of-the-art supervised model trained from scratch on yeast data, and potentially a simpler feature-based model. Report performance across all models on identical evaluation metrics.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalization evidence
- **Claim pointer** "Shorkie LM captures conserved regulatory grammar" and "generalizes across substantial evolutionary distances"
- **Evidence pointer** Results section "Shorkie LM captures regulatory conservation"; Figure 2C
- **Concern** The generalization claims are based on motif discovery across six fungal datasets, but the quantitative results are not presented in the main text. The statement that motif conservation declined beyond Saccharomycetales is qualitative. The relationship between pretraining diversity and downstream task performance is only shown for the four pretraining datasets, not for the six evaluation datasets.
- **Why it matters** The evolutionary-scale pretraining is a key contribution. The claim that the model captures conserved regulatory grammar across diverse fungi needs quantitative support to be convincing.
- **Resolution test** Provide quantitative motif conservation scores across the six fungal datasets. Show that the 165_Saccharomycetales model generalizes better than alternatives on held-out fungal genomes at varying evolutionary distances.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1B
- **Evidence pointer** Results section "Yeast language model design and training across evolutionary divergences"
- **Issue** The phylogenetic tree visualization is referenced but the selection criteria for the four pretraining datasets (R64, 80_strains, 165_Saccharomycetales, 1341_Fungus) are not clearly justified. Why these specific groupings?
- **Required correction** Add a brief justification for the chosen evolutionary groupings, perhaps referencing known phylogenetic relationships or practical considerations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model training details
- **Evidence pointer** Methods section "Shorkie LM training"
- **Issue** The training procedure mentions early stopping with patience of 1000 epochs, but the maximum number of epochs (10,000) with 150 steps per epoch seems computationally intensive. The total training time and computational resources required are not reported.
- **Required correction** Report total training time, hardware used, and approximate computational cost to help readers assess feasibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** MPRA evaluation
- **Evidence pointer** Results section "Shorkie predicts promoter variant effects validated by MPRAs"; Figure 6
- **Issue** The MPRA evaluation samples 1,000 sequences per category, but the sampling procedure and representativeness of the sample are not described. The correlation values are reported without confidence intervals.
- **Required correction** Describe the sampling procedure and report confidence intervals for correlation coefficients.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Discussion of dynamic motif analysis
- **Evidence pointer** Results section "Shorkie captures dynamic cis-regulatory motif changes across time-course TF inductions"
- **Issue** The biological interpretation of dynamic motif changes is limited. For example, what does progressive STRE sharpening mean mechanistically? The authors could connect these observations to known biology of MSN2/MSN4 stress responses.
- **Required correction** Expand the discussion to place the dynamic motif observations in the context of known regulatory mechanisms.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Loss weighting scheme
- **Evidence pointer** Methods section "Shorkie LM training"
- **Issue** The loss weighting scheme down-weights exonic and repeat regions by 0.1, but the rationale for this specific value and the sensitivity of results to this choice are not discussed.
- **Required correction** Provide justification for the weighting factor or report sensitivity analysis.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Comparison to SpeciesLM
- **Evidence pointer** Results section "Yeast language model design and training across evolutionary divergences"
- **Issue** The manuscript references SpeciesLM as using the same training data, but does not directly compare Shorkie LM to SpeciesLM in terms of pretraining performance or downstream task performance.
- **Required correction** Add a direct comparison to SpeciesLM to contextualize the contribution of the architectural modifications.

## Risk / unsupported claims
- The claim that Shorkie "substantially improves" expression prediction is not quantitatively supported in the provided text without confidence intervals and significance tests
- The claim of "outperforming leading sequence-to-expression models" in eQTL classification is potentially confounded by training distribution mismatch between DREAM models and Shorkie
- The generalization claims across fungal species are qualitative and lack quantitative support in the main text
- The biological interpretation of dynamic motif changes (e.g., "progressive STRE sharpening") is presented without statistical validation
- The claim that the 165_Saccharomycetales pretraining scale is "optimal" is based on validation loss, but the relationship between pretraining loss and downstream task performance is not fully established
- The MPRA concordance results are reported without confidence intervals, making the strength of the correlation unclear
- The attention visualization analysis (Figure 2E, S9) is described qualitatively without quantitative metrics for what the attention patterns represent