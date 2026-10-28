## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, conclusions, supplementary data references) as provided.
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and results as presented in the provided text. No assessment of code functionality, dataset availability beyond stated URLs, or reproducibility beyond what is described.
- **Shared manuscript claim summary** The authors present SATORI 2.0, an extension of the SATORI framework, which adds an entropy penalty term to self-attention maps and supports attention-attribution scoring. They claim that entropy-enhanced attention yields high-precision sparse attention maps, that their framework accurately infers transcription factor (TF) interactions across simulated and real datasets, and that pre-loaded CNN filters improve interaction inference. They also provide a comparative evaluation of raw attention, attention attribution, and DFIM.
- **Visible evidence base** Simulated datasets with implanted interactions (three levels of complexity, plus a second set for pre-loaded filters); real datasets: human promoter DHSs (164 cell lines), Arabidopsis whole-genome accessible chromatin (36 samples), Arabidopsis enhancers (STARR-seq). Metrics: AUC, precision, recall, F1-score. Figures referenced: Figs 1–6, Supplementary Figs S1–S6, Supplementary Tables S1–S16.
- **Missing materials affecting confidence** Figures and supplementary materials (Figs 1–6, S1–S6, Tables S1–S16) are referenced but not provided. Exact hyperparameter values, model architecture details (layer sizes, number of heads, etc.) are only partially described. Statistical significance testing for differences between methods is not described. Details on the Mann–Whitney U test implementation (e.g., multiple testing correction) are absent. The Arabidopsis enhancer dataset construction is described but no validation of negative set quality is provided.

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in interpretable deep learning for genomics: how to reliably infer TF cooperativity from self-attention. The addition of an entropy penalty is a simple and potentially effective idea, and the authors are to be commended for attempting a systematic evaluation across multiple datasets and architectures. However, the manuscript as presented has several significant gaps. The core claims are plausible but not fully established from the provided text alone, primarily because the key results (figures, supplementary tables) are not visible. The evaluation methodology, while thoughtful, lacks statistical rigor in places, and some claims (e.g., "comprehensive evaluation") are overstated given the limited set of baselines and the absence of ablation studies for the entropy term's interaction with other components. The real-data validation is weak: the use of HIPPIE database matches is a reasonable sanity check, but the authors do not report precision or recall against a gold standard of known interactions, which limits the strength of the claims. Overall, the work is of interest to the computational genomics community, but the evidence as presented is insufficient to fully support the conclusions.
- **Who would be interested in the results, and why** Researchers working on interpretable deep learning for regulatory genomics, specifically those developing or using attention-based models for TF binding and cooperativity prediction. The paper would also be of interest to method developers in the broader deep learning interpretability community, as the entropy penalty is a generalizable idea. Practitioners seeking guidance on choosing between raw attention, attention attribution, or DFIM for interaction discovery would find the comparative evaluation useful, provided the full results are made available.
- **Major strengths**
  1. The problem is well-motivated and important: extracting biological insights from deep learning models is a key bottleneck.
  2. The entropy penalty is a novel and simple contribution that is well-justified by the goal of inducing sparsity in attention maps.
  3. The evaluation spans multiple datasets (simulated and real) and architectures (basic vs. deep), which is more comprehensive than most prior work.
  4. The inclusion of pre-loaded CNN filters as a comparison point is valuable, as it addresses a practical concern about filter-to-motif mapping.
  5. The authors are transparent about limitations (e.g., inability to run DFIM on deep models) and provide code and data.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Our findings demonstrate the benefit of the entropy-enhanced attention models" (Abstract); "the addition of an entropy term yields high-precision sparse attention maps that are easy to interpret" (Abstract).
- **Evidence pointer** Figures 3, 4, 5, 6; Supplementary Figs S1–S6; location not provided for specific data points.
- **Concern** The central claim that entropy enhancement improves precision and interpretability is not verifiable from the provided text alone. The figures and supplementary materials that contain the quantitative results are not included in the manuscript text provided. The authors state that entropy "maintains classification accuracy while enhancing precision" (Fig. 3) and that it "increased the number of interactions detected" (Fig. 6), but without seeing the actual numbers, error bars, or statistical tests, the magnitude and significance of these improvements cannot be assessed. Furthermore, the claim of "high-precision" is qualitative; no precision values are given in the text.
- **Why it matters** The entire contribution hinges on the demonstrated benefit of the entropy term. If the improvement is marginal or inconsistent across datasets, the paper's main selling point is weakened. The authors need to provide the actual data and statistical analysis to support this claim.
- **Resolution test** Provide the figures and supplementary tables with clear numerical values, error bars (or confidence intervals), and statistical significance tests (e.g., paired tests across dataset instances) comparing entropy vs. no-entropy models for precision, recall, F1, and AUC. The claim of "high-precision" should be quantified.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** "we performed a comprehensive evaluation of the relative performance of different flavors of attention-based transcription factor cooperativity discovery" (Abstract); "provide additional insights that would enable practitioners to make effective use of this valuable tool" (Abstract).
- **Evidence pointer** Methods section "Model selection and training"; Results sections for simulated and real data; location not provided for specific comparisons.
- **Concern** The evaluation, while broad, is not "comprehensive" in the sense of being systematic and controlled. The authors compare raw attention, attention attribution, and DFIM, but the comparison is confounded by several factors. First, the hyperparameter search is performed on a single simulated dataset instance, and it is unclear whether the selected hyperparameters are optimal for all datasets and architectures. Second, the comparison between raw attention and attention attribution is not an ablation: the attribution method is applied on top of the same attention mechanism, but the authors do not report whether the attribution method changes the ranking of interactions in a statistically significant way. Third, the DFIM comparison is limited to cases where it is computationally feasible, which may bias the comparison. Finally, the authors do not report any variance across the three dataset instances beyond "averaging," which is insufficient to assess stability.
- **Why it matters** The paper's stated goal is to guide practitioners. If the evaluation is not controlled and the variance is not reported, practitioners cannot make informed decisions about which method to use. The claim of "comprehensive" is an overstatement given these limitations.
- **Resolution test** Clarify the hyperparameter selection process and whether it was fixed across all experiments. Report standard deviations or confidence intervals for all metrics across the three dataset instances. Perform a formal statistical comparison (e.g., paired Wilcoxon test) between raw attention and attention attribution. Discuss the computational constraints that limited DFIM comparisons and whether this introduces bias.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** External validity
- **Claim pointer** "To test the ability of SATORI to detect cooperation of TFs in real data, we explored the regulatory cooperation among TFs within human promoter regions" (Results); "we searched these interactions against the HIPPIE protein–protein interaction database" (Results).
- **Evidence pointer** Results sections "TF interactions in accessible chromatin in human promoters" and "TF interactions in accessible chromatin in Arabidopsis"; Supplementary Tables S4–S16; location not provided.
- **Concern** The real-data validation is weak. The authors use the HIPPIE database to check whether predicted TF interactions are known protein-protein interactions. However, this is a very loose validation: many TF cooperativity events are not mediated by direct physical protein-protein interaction, and the absence of a HIPPIE match does not imply a false positive. The authors report "the interaction between SP7 and KDM2B discovered by all of the methods" but do not provide a systematic evaluation of precision or recall against a gold standard. The number of HIPPIE matches (Supplementary Table S4) is reported, but the total number of predicted interactions is not given in the text, making it impossible to assess the hit rate.
- **Why it matters** The real-data experiments are meant to demonstrate practical utility. Without a more rigorous validation (e.g., comparison to known TF cooperativity databases, or experimental validation), the biological relevance of the findings remains uncertain. The current validation is suggestive but not conclusive.
- **Resolution test** Provide the total number of predicted interactions for each method and dataset, and report the fraction that match HIPPIE. Consider additional validation strategies, such as comparison to known regulatory interactions from databases like ENCODE or STRING, or enrichment analysis for known co-binding motifs. Discuss the limitations of using HIPPIE as a gold standard.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical completeness
- **Claim pointer** "The use of pre-loaded CNN filters based on known motifs offers the potential advantage of not requiring computing matches to the trained filters" (Results); "using pre-loaded filters leads to improved interpretation accuracy" (Results).
- **Evidence pointer** Results section "Using pre-loaded filters"; Supplementary Figs S4 and S5; location not provided.
- **Concern** The pre-loaded filter experiments are described briefly, but several technical details are missing. The authors state that filters were pre-loaded with "clustered motifs from the Jaspar database" but do not describe the clustering method, the number of clusters, or how the filters were initialized (e.g., as position-specific scoring matrices converted to convolutional weights). The drop in classification accuracy is mentioned but not quantified. The interaction inference procedure for pre-loaded filters is also unclear: does the same filter-to-motif mapping procedure apply, or is it assumed that each filter corresponds to a known motif?
- **Why it matters** The pre-loaded filter approach is presented as a practical improvement, but without sufficient technical detail, it cannot be reproduced or fully evaluated. The trade-off between interpretation accuracy and classification accuracy is a key consideration for practitioners.
- **Resolution test** Provide a detailed description of the clustering and filter initialization procedure. Report the classification accuracy drop quantitatively. Clarify how interactions are inferred when using pre-loaded filters, and whether the same statistical testing procedure is applied.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "All the experiments were conducted on a Linux workstation with a 12 GB TITAN V GPU" (Methods); "The source code and datasets are available at https://github.com/sairajab/satoriv2" (Data availability).
- **Evidence pointer** Methods section "Model selection and training"; Data availability section; location not provided.
- **Concern** While the authors state that code and data are available, the manuscript does not provide sufficient detail for reproduction. The hyperparameter search space is in Supplementary Table S1, but the final selected hyperparameters are not listed in the text. The number of training epochs, batch size, learning rate schedule, and early stopping criteria are not described. The random seed handling is mentioned (three seeds) but not detailed. The exact architecture of the "deep" model is only partially described (inspired by SEI, with residual connections and dilated convolutions), but the number of layers, filter sizes, and dilation rates are not specified.
- **Why it matters** Reproducibility is a core requirement for computational biology papers. Without these details, other groups cannot replicate the experiments or build on the work.
- **Resolution test** Provide the final hyperparameters for all models, training details (epochs, batch size, optimizer settings), and a complete architecture specification. Ensure the code repository includes configuration files that reproduce the reported results.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided.
- **Issue** The abstract states "we extend this earlier work" but does not clearly specify what the "earlier work" is beyond referencing SATORI. The novelty of the entropy term is mentioned, but the abstract would benefit from a more explicit statement of the specific contributions (e.g., "we introduce an entropy penalty to the attention loss").
- **Required correction** Revise the abstract to explicitly state the two main contributions: (1) the entropy penalty term, and (2) the systematic comparison of raw attention vs. attention attribution vs. DFIM.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections
- **Evidence pointer** Results sections for simulated and real data; location not provided.
- **Issue** The text reports averages over three dataset instances but does not report standard deviations or confidence intervals. For example, "the entropy term increased the number of interactions detected" is stated without quantifying the variability across instances.
- **Required correction** Report standard deviations or confidence intervals for all key metrics (AUC, precision, recall, F1) across the three dataset instances.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Methods section "Attention attribution scores"
- **Evidence pointer** Methods section "Attention attribution scores"; location not provided.
- **Issue** The term "attention attribution scores" is used, but the relationship to integrated gradients is described only briefly. The authors should clarify whether this is the same as the "attention attribution" method in ISANREG [20] or a different implementation.
- **Required correction** Clarify the relationship to the method in [20] and provide a more precise definition of the attribution score computation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "TF interactions in Arabidopsis enhancers"
- **Evidence pointer** Results section "TF interactions in Arabidopsis enhancers"; location not provided.
- **Issue** The authors report AUPR values between 0.80 and 0.83 but do not report the corresponding precision and recall for interaction inference on this dataset. The number of interactions detected is not given in the text.
- **Required correction** Report the number of interactions detected and the precision/recall for this dataset, or explain why these are not reported.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Figures 3–6; location not provided.
- **Issue** The figures are referenced but not described in sufficient detail in the text. For example, Figure 3 is described as showing "impact of the entropy loss" but the axes, panels, and statistical comparisons are not explained.
- **Required correction** Add a brief description of each figure in the text, including what is plotted and what the key takeaways are.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Related work
- **Evidence pointer** Introduction and Related work; location not provided.
- **Issue** The related work section is brief and does not discuss recent advances in attention interpretability for genomics beyond the cited works. For example, the authors do not mention other methods that use attention for TF interaction discovery, such as DeepATT or other transformer-based approaches.
- **Required correction** Expand the related work to include a broader discussion of recent methods and how SATORI 2.0 compares.

## Risk / unsupported claims
- The claim that entropy-enhanced attention yields "high-precision sparse attention maps that are easy to interpret" is not supported by quantitative data in the provided text; the figures are not visible.
- The claim of a "comprehensive evaluation" is overstated given the limited number of baselines (only DFIM and attention attribution) and the lack of statistical comparisons.
- The claim that pre-loaded CNN filters "provide a further big increase in the number of detected interactions" is not quantified in the text.
- The real-data validation using HIPPIE is suggestive but not conclusive; the authors do not report precision or recall against a gold standard.
- The statement that "the interaction between SP7 and KDM2B discovered by all of the methods" is presented as a key result, but its biological significance is not discussed.
- The claim that "the entropy term was crucial for detecting interactions" in the human promoter dataset is not supported by a comparison to a no-entropy baseline in the text.
- The authors state that "attention attribution scores and raw attention scores give comparable results" but do not provide the data or a statistical test to support this.
- The claim that "the deeper model had somewhat lower interpretation accuracy" is made without reporting the magnitude of the difference or its significance.