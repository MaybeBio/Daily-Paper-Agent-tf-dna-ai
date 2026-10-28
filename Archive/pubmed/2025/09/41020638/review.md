## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, conclusion, and data availability statement. Figures and tables are referenced but not provided in full detail.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to provided evidence, and suitability for a high-impact computational biology venue. No assessment of code functionality or reproducibility beyond what is described.
- **Shared manuscript claim summary** The authors present INAB, a computational framework integrating cross-modal protein language models (ESM-2, GearNet, SaProt) with a multiscale architecture combining Mamba (sequence-level) and EGNN (structure-level) modules, using a novel hierarchical distance-based labeling system for nucleic acid binding domain prediction. They claim state-of-the-art performance on independent test sets and public benchmarks, with contributions in multimodal fusion, regression-based labeling, and computational efficiency.
- **Visible evidence base** Abstract, full methods description, results narrative, tables referenced (Tables 1-5), figures referenced (Figs 1-4), supplementary materials referenced (Tables S1-S3, Fig. S1). Actual numerical results, figures, and supplementary content are not fully visible in the provided material.
- **Missing materials affecting confidence** Actual performance numbers, comparison tables, figure contents, ablation results, hyperparameter settings, dataset statistics, and benchmark details. The manuscript text describes results but the quantitative evidence is not directly assessable.

## Reviewer

- **Overall assessment** The manuscript addresses a relevant problem in computational biology with a technically sophisticated approach. The integration of multiple PLM modalities with geometric deep learning is timely and the hierarchical labeling scheme is conceptually interesting. However, the provided material does not include the actual experimental results, making it impossible to verify the central claims of state-of-the-art performance. The methods section is detailed but several critical experimental design choices require clarification. The work has potential but the case is not fully established from the supplied evidence.

- **Who would be interested in the results, and why** Researchers in computational biology, bioinformatics, and machine learning applied to protein function prediction. Specifically, those working on protein-nucleic acid interactions, protein language models, geometric deep learning, and functional annotation of proteins. The hierarchical labeling approach and multimodal fusion strategy may also interest method developers in the broader protein function prediction community.

- **Major strengths**
  1. The conceptual framing of nucleic acid binding as a continuous, hierarchical property rather than a binary classification is biologically motivated and potentially more informative.
  2. The systematic integration of three complementary PLM modalities (sequence, residue-level structure, structural token) with classical empirical features is a well-reasoned design.
  3. The multiscale architecture combining global sequence modeling (Mamba) with local geometric reasoning (EGNN) addresses complementary aspects of the binding prediction problem.
  4. The authors explicitly address the potential concern of PLM pretraining data overlap with benchmark datasets, providing a reasonable argument for why this does not constitute leakage.
  5. The inclusion of efficiency benchmarking against template-based methods is practically relevant.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims INAB achieves state-of-the-art performance across all metrics on both DNA and RNA independent test sets, and outperforms competing methods on public benchmarks.
- **Evidence pointer** Tables 2, 3, S3; location not provided for actual values
- **Concern** The central performance claims are made without presenting the actual numerical results in the provided material. The text states INAB achieved superior performance but the comparison tables are not visible. Without the quantitative evidence, the state-of-the-art claim cannot be evaluated.
- **Why it matters** The primary contribution of the paper rests on demonstrating improved predictive performance. If the numerical results do not support the claims, the entire case for the method collapses. The reader cannot assess effect sizes, statistical significance, or practical relevance of improvements.
- **Resolution test** Provide the full comparison tables with all metrics, standard deviations, and statistical significance tests. Show that improvements over baselines are meaningful and consistent across datasets.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The hierarchical labeling system quantifies binding likelihood based on minimum heavy-atom distance, with the label computed as a continuous score.
- **Evidence pointer** Materials and method, Dataset construction and annotation; location not provided
- **Concern** The exact formula for the hierarchical label is not fully specified. The text shows the label is computed from the minimum heavy-atom distance but the actual functional form is truncated. It is unclear whether this is a continuous distance value, a transformed score, or a discretized multi-level label. The relationship between distance and binding likelihood needs explicit definition.
- **Why it matters** The labeling scheme is a claimed contribution and directly affects what the model learns. Without a precise definition, the method cannot be reproduced and the biological interpretation of the predicted scores is ambiguous.
- **Resolution test** Provide the complete mathematical formulation of the labeling function, including any normalization, scaling, or thresholding steps. Clarify whether the output is interpretable as a probability, a distance, or a unitless score.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline fairness
- **Claim pointer** INAB is benchmarked against five state-of-the-art methods using their official pretrained models and codes.
- **Evidence pointer** Results and discussion, Comparison with state-of-the-art methods; location not provided
- **Concern** The five comparison methods are listed but not named in the provided text. The criteria for method selection are described but the actual baselines are not identified. It is impossible to assess whether these are appropriate and competitive baselines, whether they were used in their optimal configuration, or whether any of them were designed for the same task formulation.
- **Why it matters** Benchmarking against appropriate baselines is essential for establishing state-of-the-art claims. If the baselines are weak, outdated, or misconfigured, the reported improvements are not meaningful. The reader cannot judge the competitiveness of the comparison.
- **Resolution test** Name all baseline methods, describe their original task formulations, and clarify any adaptations made for this comparison. Justify why these represent the current state of the art.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Experimental design
- **Claim pointer** The hierarchical labeling approach outperforms binary classification in both regression and classification metrics.
- **Evidence pointer** Results and discussion, Comparison of binary and hierarchical labelling schemas; Tables 4, 5
- **Concern** The comparison between INAB (regression with hierarchical labels) and INAB-Cls (classification with binary labels) is described but the actual results are not visible. The claim that regression outperforms classification even on classification metrics is interesting but requires scrutiny. The binary labeling threshold of 5 Å is a single choice, and the sensitivity of results to this threshold is not discussed.
- **Why it matters** This comparison is central to justifying the hierarchical labeling contribution. If the improvement is marginal or threshold-dependent, the claimed advantage may not be robust. The choice of 5 Å as the binary threshold needs justification.
- **Resolution test** Show the full comparison results, include sensitivity analysis for the binary threshold, and discuss whether the advantage of hierarchical labeling holds across different threshold choices.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** INAB is applicable for predicting both DNA- and RNA-binding domains, and the authors suggest it can complement complex structure prediction methods.
- **Evidence pointer** Conclusion; location not provided
- **Concern** The manuscript reports separate training sets for DNA and RNA (DNA-2061_Train and RNA-2829_Train), suggesting separate models. The claim of general applicability to both nucleic acid types is made but the relationship between the DNA and RNA models is unclear. Additionally, the discussion of complementarity with AlphaFold 3 is speculative without concrete evidence.
- **Why it matters** The practical utility of the method depends on its applicability across nucleic acid types and its integration with other tools. If separate models are needed, the generalizability claim is weaker. The speculative discussion of integration with structure prediction methods should be clearly framed as future work.
- **Resolution test** Clarify whether a single model handles both DNA and RNA or whether separate models are trained. Provide evidence for cross-type generalization if claimed. Reframe the AlphaFold 3 discussion as explicitly speculative.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states the method achieves state-of-the-art performance but does not provide any quantitative context or comparison to existing methods.
- **Required correction** Include representative performance numbers or a clear statement of the improvement magnitude in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Dataset construction
- **Evidence pointer** Materials and method, Dataset construction and annotation; location not provided
- **Issue** The description of the dataset filtering process mentions CD-HIT at 90% identity and removal of truncated and excessively long sequences, but the final dataset composition (number of DNA vs. RNA binding proteins, sequence length distribution) is not described in the text.
- **Required correction** Add a brief description of the final dataset composition, including the number of DNA and RNA binding chains and key statistics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Model architecture
- **Evidence pointer** Materials and method, Multiscale computation framework; location not provided
- **Issue** The description of the Mamba and EGNN modules states that only key hyperparameters were customized, but the specific architectural choices (number of layers, hidden dimensions, etc.) are only in supplementary tables.
- **Required correction** Include the key architectural parameters in the main text or provide a summary table in the main text for accessibility.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Performance comparison
- **Evidence pointer** Results and discussion, Comparison with state-of-the-art methods; location not provided
- **Issue** The text does not mention whether performance differences were assessed for statistical significance or whether multiple runs were performed to estimate variance.
- **Required correction** Report standard deviations or confidence intervals for the main results, and state whether significance testing was performed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Case study
- **Evidence pointer** Results and discussion, Case study; location not provided
- **Issue** The case study uses a single protein (PDB id 8w2s_A) released after the training data cutoff, which is a good validation choice, but the text does not describe how the prediction quality was assessed beyond visual comparison.
- **Required correction** Provide quantitative metrics for the case study prediction or describe the visual assessment criteria more explicitly.

## Risk / unsupported claims
- State-of-the-art performance claim is unsupported in the provided material because actual comparison results are not visible.
- The claim that hierarchical labeling outperforms binary classification is unsupported without the numerical results.
- The claim that cross-modal PLM integration enhances prediction robustness is asserted but not demonstrated with visible evidence.
- The claim that INAB achieves substantially greater computational efficiency than NABind is described but the efficiency data are only in supplementary figures.
- The claim that INAB addresses the challenge of identifying binding domains from protein information alone, without requiring knowledge of the nucleic acid partner, is a reasonable framing but the comparative advantage over methods that also use protein-only input is not quantified.
- The statement that the use of PLMs pretrained on large corpora does not constitute information leakage is an argument, not a demonstrated fact, and requires careful consideration of what the PLMs may have learned about binding sites.