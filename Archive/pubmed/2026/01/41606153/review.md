## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods summary, figure legends, supplementary information description)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and presentation as presented in the provided text. No access to supplementary figures, tables, or extended data.
- **Shared manuscript claim summary** The authors present AlphaGenome, a deep learning model that takes 1 Mb of DNA sequence as input and predicts thousands of functional genomic tracks at up to single-base-pair resolution across 11 modalities (gene expression, splicing, chromatin accessibility, histone modifications, transcription factor binding, chromatin contacts). The model is trained on human and mouse genomes and is claimed to match or exceed the strongest available external models in 25 of 26 variant effect prediction evaluations. The authors further claim that AlphaGenome accurately recapitulates mechanisms of clinically relevant variants near the TAL1 oncogene and provide tools for genome track and variant effect prediction.
- **Visible evidence base** Main text descriptions of model architecture, training procedure, performance metrics (Pearson r, Spearman ρ, auROC, auPRC), ablation study results, and qualitative example predictions. Figure legends for Figures 1–7. No access to actual data values, supplementary tables, or extended data figures.

## Reviewer
- **Overall assessment** This manuscript describes a technically ambitious and potentially impactful model that aims to unify long-range context, base-pair resolution, and multimodal prediction in a single framework. The core idea of combining a U-Net architecture with sequence parallelism to achieve 1 Mb input at 1 bp resolution is novel and addresses a real limitation in the field. The reported performance improvements over existing models, particularly in splicing and eQTL prediction, are notable. However, the manuscript as provided has significant limitations in the evidence presented. The Methods section is almost entirely deferred to supplementary information, making it impossible to assess key technical details such as data preprocessing, model hyperparameters, training stability, and evaluation protocols. Several claims, particularly regarding clinical relevance and mechanistic interpretation, are supported by qualitative examples rather than quantitative benchmarks. The ablation studies are described only at a high level without numerical results. The lack of access to the actual performance numbers, confidence intervals, and statistical significance testing prevents a full assessment of the robustness of the reported improvements. The manuscript would benefit from a more detailed presentation of the evaluation methodology and results in the main text.

- **Who would be interested in the results, and why** Computational biologists and geneticists working on regulatory genomics, variant effect prediction, and non-coding disease variant interpretation would be the primary audience. The model's ability to predict multiple modalities simultaneously at base-pair resolution from long-range context could be of broad interest to researchers studying gene regulation, splicing mechanisms, and chromatin architecture. The potential clinical applications in rare disease diagnostics and variant prioritization would also interest translational researchers. The technical approach of combining sequence parallelism with a U-Net architecture may interest machine learning researchers working on genomic sequence models.

- **Major Strengths**
  1. The model architecture addresses a genuine and important limitation in the field: the trade-off between input sequence length and prediction resolution. The 1 Mb input at 1 bp resolution is a significant technical achievement.
  2. The breadth of modalities covered (11 modalities, including novel splicing junction prediction) is impressive and could provide a unified framework for regulatory variant interpretation.
  3. The two-stage training approach (pretraining with cross-validation, followed by distillation) is well-motivated and the reported efficiency gains (single model, <1 s per variant on H100) are practically valuable.
  4. The ablation studies, even at a high level, address important design questions (resolution, sequence length, ensembling, distillation, multimodality) that would inform future model development.
  5. The TAL1 case study provides a compelling demonstration of the model's potential for mechanistic interpretation of clinically relevant variants.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "AlphaGenome achieved SOTA performance on 22 of 24 genome track prediction tasks and 25 of 26 variant effect prediction tasks."
- **Evidence pointer** Figure 1d,e; Supplementary Tables 3 and 4 (not accessible)
- **Concern** The central performance claims are presented as aggregate counts (22/24, 25/26) without any numerical details in the main text. The reader cannot assess the magnitude of improvements, whether they are statistically significant, or whether they are consistent across tasks. The comparison methodology against "the strongest available external model" is not described. It is unclear whether the same external model is used for all tasks in a modality, how hyperparameters were selected for baselines, and whether the comparisons are fair (e.g., same training data, same evaluation metrics).
- **Why it matters** The primary contribution of this work is the claimed performance improvement over existing methods. Without quantitative details and a clear description of the evaluation protocol, the central claims cannot be verified. This is particularly important given the field's history of subtle evaluation differences leading to inflated performance claims.
- **Resolution test** Provide a table in the main text with the actual performance values for AlphaGenome and each baseline for all 24 track prediction and 26 variant effect prediction tasks, including confidence intervals and statistical significance tests. Describe the baseline selection criteria and evaluation protocol in sufficient detail to be reproducible.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The model takes 1 Mb of DNA sequence as input and predicts 5,930 human or 1,128 mouse genome tracks across diverse cell types and 11 output types at specific resolutions."
- **Evidence pointer** Figure 1a; Extended Data Fig. 1 (not accessible); Methods (deferred to Supplementary Information)
- **Concern** The Methods section in the main text is a single sentence referring to supplementary information. Critical technical details are entirely absent: data sources and preprocessing (e.g., how RNA-seq, ChIP-seq, ATAC-seq, Hi-C data were processed and normalized), the exact architecture (number of layers, attention heads, hidden dimensions), training hyperparameters (learning rate, batch size, optimization algorithm, training duration), and the cross-validation scheme. The description of the distillation process is also high-level; the student model's architecture, the nature of "mutationally perturbed input sequences," and the loss function for distillation are not specified.
- **Why it matters** For a model of this complexity, the technical details are essential for reproducibility and for the community to build upon the work. The lack of detail also prevents assessment of potential data leakage issues (e.g., whether the cross-validation folds properly separate chromosomes or genomic regions) and whether the model is genuinely learning generalizable regulatory principles versus memorizing training data.
- **Resolution test** Provide a comprehensive Methods section in the main text or ensure the supplementary information contains all necessary details for reproduction, including data accession numbers, preprocessing pipelines, architecture specifications, hyperparameters, and training procedures. Describe the cross-validation scheme in detail, including how genomic regions were partitioned.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "The ability of AlphaGenome to simultaneously score variant effects across all modalities accurately recapitulates the mechanisms of clinically relevant variants near the TAL1 oncogene."
- **Evidence pointer** Figure 6; reference 6
- **Concern** The TAL1 case study is presented as a key demonstration of the model's utility, but the evidence is entirely qualitative. The text describes predicted changes in histone marks, accessibility, and expression, but no quantitative comparison to experimental validation is provided. It is unclear whether the predictions for the oncogenic mutations are statistically distinguishable from the control mutations, what the effect sizes are, and whether the model's predictions were validated experimentally or only compared to previously published observations. The claim of "accurately recapitulates" is not supported by quantitative metrics.
- **Why it matters** The clinical relevance and mechanistic interpretability of the model are major selling points. A qualitative case study, while illustrative, does not provide rigorous evidence that the model can reliably identify and interpret disease-relevant variants. Overclaiming based on anecdotal examples could mislead potential users.
- **Resolution test** Provide quantitative metrics for the TAL1 analysis, such as the distribution of predicted effect sizes for oncogenic versus control mutations, with statistical significance testing. If experimental validation was performed, describe the experiments and results. If the analysis is purely computational, state this clearly and temper the claims accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "AlphaGenome outperformed these external models on 22 of 24 evaluations... This included strong performance in quantitative trait locus (QTL) evaluations, such as sign prediction for expression QTLs (eQTLs; +25.5% versus Borzer) and accessibility QTL (+8.0% versus ChromBPNet, averaged across five datasets)."
- **Evidence pointer** Figure 1d,e; Extended Data Figs. 3–5 (not accessible); Supplementary Tables 3 and 4 (not accessible)
- **Concern** The reported improvements are presented as percentages (e.g., +25.5%, +8.0%), but the baseline values are not given. A +25.5% improvement from 0.40 to 0.50 is very different from an improvement from 0.80 to 0.90 in terms of practical significance. The text also mentions "averaged across several similar datasets" without specifying which datasets, how many, or the variance across them. The stratification analyses (e.g., by distance to TSS, by functional annotation) are mentioned but not shown.
- **Why it matters** The practical significance of the improvements cannot be assessed without knowing the absolute values. The averaging across datasets could mask important heterogeneity in performance. The lack of stratified results prevents understanding of where the model excels and where it struggles.
- **Resolution test** Report absolute performance values alongside the relative improvements. Show the distribution of performance across individual datasets rather than just the average. Include the stratified analyses in the main text or ensure they are clearly presented in the supplementary material.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "AlphaGenome more accurately models both genome tracks and variant effects" and "AlphaGenome achieves SOTA variant splicing effect prediction on six of seven benchmarks."
- **Evidence pointer** Figures 2–5; Extended Data Figs. 2–8 (not accessible); Supplementary Tables 3–5 (not accessible)
- **Concern** The manuscript reports performance on a wide range of benchmarks, but the selection of benchmarks and the criteria for "SOTA" are not justified. For example, for splicing, the authors compare against SpliceAI, Pangolin, and others, but it is unclear whether these are the most recent versions, whether the training data are comparable, and whether the evaluation metrics are the most appropriate. The claim of "SOTA" requires a comprehensive and fair comparison against all relevant existing methods, not just a selected subset.
- **Why it matters** The field of regulatory variant effect prediction is rapidly evolving, and claims of SOTA performance need to be carefully contextualized. An incomplete or unfair comparison could misrepresent the model's true standing relative to the state of the art.
- **Resolution test** Justify the selection of baseline methods and benchmarks. Ensure that all comparisons use the most recent versions of baseline models and that evaluation protocols are consistent. Consider including a broader range of baselines, including non-deep-learning methods.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "AlphaGenome can complement the capabilities of generative models trained on DNA sequences by predicting functional properties of newly generated sequences."
- **Evidence pointer** Discussion section
- **Concern** This claim is made in the discussion without any supporting evidence or demonstration. While it is plausible that AlphaGenome could be used in this way, the manuscript does not provide any examples or benchmarks showing that the model's predictions are useful for evaluating sequences generated by other models. This is a speculative claim presented as a potential application.
- **Why it matters** The discussion should distinguish between demonstrated capabilities and potential future applications. Overstating the model's utility in areas where no evidence is provided could mislead readers about its current capabilities.
- **Resolution test** Either remove or clearly label this claim as speculative, or provide a proof-of-concept demonstration showing AlphaGenome's utility in evaluating generated sequences.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 1a
- **Evidence pointer** Figure 1a
- **Issue** The description of the model architecture in the figure legend is dense and difficult to follow. The relationship between the encoder, transformer, and decoder components, and how they produce the different output types at different resolutions, is not clear from the text alone.
- **Required correction** Consider simplifying the figure legend and adding a more detailed architectural diagram in the supplementary material. A clear schematic of the data flow from input sequence to output tracks would greatly aid comprehension.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "AlphaGenome matches or exceeds the strongest available external models in 25 of 26 evaluations of variant effect prediction" but does not mention the track prediction results (22 of 24). This is an important omission as track prediction is a core capability of the model.
- **Required correction** Consider including both track prediction and variant effect prediction results in the abstract to provide a more complete summary of the model's performance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Ablation studies
- **Evidence pointer** Figure 7
- **Issue** The ablation studies are described at a high level, but the specific metrics and datasets used for each ablation are not specified. For example, in Figure 7a, it is unclear which tasks were used to evaluate the impact of target resolution.
- **Required correction** Specify the evaluation tasks and metrics for each ablation panel in the figure legend or main text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion is quite long and covers many topics, including limitations, future directions, and potential applications. Some of this material could be streamlined to improve focus.
- **Required correction** Consider condensing the discussion and moving some of the more speculative content to a "Future Directions" subsection or removing it entirely.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Benchmarking
- **Evidence pointer** Figure 3f–i, Figure 4c–i, Figure 5b,c
- **Issue** The text mentions "tissue-specific auPRCs were averaged and weighted by variant count per tissue" for the sQTL classification, but the details of this weighting scheme are not provided. Similar methodological details for other benchmarks are also lacking.
- **Required correction** Provide a clear description of the evaluation methodology for each benchmark, including any weighting or aggregation schemes, in the Methods section.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Terminology
- **Evidence pointer** Throughout
- **Issue** The term "SOTA" is used frequently without always specifying the comparison set. It would be clearer to say "SOTA among the methods compared" or similar.
- **Required correction** Use more precise language when claiming SOTA performance.

## Risk / unsupported claims
- The claim that AlphaGenome "accurately recapitulates the mechanisms of clinically relevant variants near the TAL1 oncogene" is not quantitatively supported in the provided text. The evidence is qualitative and lacks statistical validation.
- The claim that AlphaGenome "could be used 'in the loop' to accelerate sequence design applications" is speculative and not demonstrated.
- The claim that AlphaGenome "can complement the capabilities of generative models" is speculative and not demonstrated.
- The overall performance claims (22/24 and 25/26) are unverifiable without access to the actual numerical results and comparison methodology.
- The claim that AlphaGenome "more accurately models both genome tracks and variant effects" is a general statement that needs to be qualified by the specific benchmarks and comparison methods used.
- The ablation study conclusions are not fully supported by the data presented in the main text, as the specific metrics and datasets are not described.