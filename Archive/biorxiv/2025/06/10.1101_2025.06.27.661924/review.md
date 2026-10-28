## Review setup

- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and code availability statement
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and presentation quality. No assessment of formatting or editorial style beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors propose active learning as a strategy for optimizing regulatory DNA sequences to improve protein expression. They test this on synthetic NK fitness landscapes and on a large experimentally characterized yeast promoter dataset, using a pretrained transformer model as a surrogate. They report that active learning outperforms one-shot optimization methods, particularly in rugged landscapes with epistasis, and that it can leverage data from different experimental conditions.
- **Visible evidence base** Figures 1-4 (described in text), Supplementary Figures S1-S10 (referenced), Methods section with model details, pseudocode description, and parameter choices. No raw data or code were provided.
- **Missing materials affecting confidence** Code repository not yet available. Raw data files not provided. Supplementary figures not accessible in the submitted material. Exact hyperparameters for the MLP ensemble and training details are only partially specified. The pseudocode is described but not shown in full.

## Reviewer

- **Overall assessment** This manuscript addresses a relevant problem in biotechnology: how to efficiently optimize regulatory DNA sequences for maximal protein expression. The authors propose active learning as an alternative to one-shot optimization and provide evidence from both synthetic and experimental landscapes. The work is timely and the approach is sensible. However, the manuscript has several technical weaknesses that need to be addressed before the case is fully established. The comparison with one-shot methods is not entirely fair in some places, the surrogate model usage raises questions about circularity, and the statistical treatment of results is incomplete. The biological insights from motif analysis are interesting but underdeveloped. Overall, the core idea has merit, but the evidence as presented does not yet fully support all claims.

- **Who would be interested in the results, and why** Researchers in synthetic biology, metabolic engineering, and protein engineering would be interested, as the method offers a potential framework for reducing experimental cycles in sequence optimization. Computational biologists working on sequence-to-expression models and active learning would also find the methodological comparisons relevant. The demonstration of cross-condition data transfer could be of interest to those building shared datasets across laboratories.

- **Major strengths** The use of both synthetic and experimental landscapes is a good approach for testing the method under controlled and realistic conditions. The NK model provides a tunable testbed for understanding how landscape ruggedness affects performance. The yeast promoter dataset is large and experimentally grounded, and the use of a high-accuracy transformer surrogate is pragmatic. The exploration of different sampling strategies (directed evolution, genetic drift, recombination) and the inclusion of motif-based reward modification show thoughtful consideration of biological priors. The data transfer experiment is a useful practical contribution.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that active learning "can outperform one-shot optimization approaches in complex landscapes with a high degree of epistasis" (Abstract and Section 2.1).
- **Evidence pointer** Figure 2D, Section 2.1, Supplementary Figures S2-S4
- **Concern** The comparison between active learning and one-shot methods is not controlled for computational budget. The one-shot methods are trained once on a fixed dataset, while active learning receives additional data at each loop. The total number of labeled examples seen by active learning across all loops is larger than that used for one-shot training. This makes it unclear whether the improvement is due to active learning per se or simply to having more data. The authors state that one-shot methods use "the same number of sequences as in each active learning loop" (Section 4.3), but this is ambiguous. If one-shot methods are trained on the initial batch only, the comparison is unfair. If they are trained on the total accumulated data, the comparison is more meaningful but the text does not clarify this.
- **Why it matters** The central claim of the paper is that active learning provides a benefit over one-shot approaches. If the comparison is confounded by data quantity, the conclusion is not supported. This is a fundamental issue that affects the interpretation of all subsequent results.
- **Resolution test** Clarify the experimental setup. Specify exactly how many labeled examples each one-shot method receives versus the total number used in active learning. If one-shot methods are trained on the initial batch only, rerun the comparison with one-shot methods trained on the full accumulated dataset. Report results for both settings to disentangle the effect of active learning from the effect of additional data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The authors use a pretrained transformer model as a surrogate for experimental measurements in the yeast promoter landscape (Section 2.2, Section 4.1).
- **Evidence pointer** Section 2.2, Section 4.1, Figure 3
- **Concern** The active learning loop relies on a surrogate model to evaluate the selected sequences. The surrogate is described as highly accurate (Pearson r > 95%), but the authors do not report how this accuracy was measured or on which test set. More importantly, the MLP ensemble used in the active learning loop is trained on data generated by the surrogate, not on experimental data. This creates a potential circularity: the MLP learns to approximate the surrogate, and the surrogate is used to evaluate the MLP's selections. The reported improvements in expression are therefore improvements relative to the surrogate's predictions, not necessarily relative to true experimental measurements. The authors do not validate the final selected sequences experimentally.
- **Why it matters** The practical value of the method depends on whether the sequences identified by active learning actually perform well in the lab. Without experimental validation, the claim that active learning "can effectively optimize sequences" is not fully supported. The surrogate may have systematic biases that the active learning loop exploits, leading to overoptimistic results.
- **Resolution test** Provide details on the surrogate's test set and accuracy metrics. If possible, validate a subset of the final selected sequences experimentally. Alternatively, clearly state that the results are computational and that experimental validation is a future step. If experimental validation is not feasible, temper the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report that active learning "can outperform one-shot optimization approaches" and that certain sampling strategies (e.g., recombination) outperform others (Section 2.3).
- **Evidence pointer** Figures 2A, 2D, 3B, 4B, 4D
- **Concern** The results are presented as mean values or single trajectories, but no error bars, confidence intervals, or statistical tests are reported. The NK landscape experiments appear to be run once per condition, and the yeast promoter experiments also lack replication. Given the stochastic nature of neural network training and sequence sampling, it is unclear whether the observed differences are significant or within the range of random variation.
- **Why it matters** Without measures of variability, the reader cannot assess the reliability of the reported improvements. The claim that one sampling strategy outperforms another, or that active learning beats one-shot methods, may be based on a single favorable run.
- **Resolution test** Run multiple independent replicates of the active learning loop and the one-shot baselines. Report means with standard deviations or confidence intervals. Perform appropriate statistical tests (e.g., t-tests or nonparametric tests) for the key comparisons. If multiple replicates are computationally prohibitive, state this limitation explicitly and provide at least a sensitivity analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors state that "active learning can effectively leverage datasets from different conditions" based on the data transfer experiment (Section 2.2, Figure 3D).
- **Evidence pointer** Figure 3D, Section 4.5
- **Concern** The data transfer experiment shows that initializing with data from medium B and optimizing for medium A achieves similar results to starting with medium A data. However, the authors also report a 7.4% improvement when initializing with pre-optimized sequences from medium B. The text does not explain why pre-optimization in a different condition would help, and the result is presented without discussion of potential mechanisms. Additionally, the comparison is only made against one baseline (random initialization with medium A data). It is unclear whether the improvement is specific to the pre-optimization procedure or would also occur with any good initialization.
- **Why it matters** The claim about leveraging cross-condition data is interesting but the evidence is thin. The result could be a artifact of the specific dataset or the pre-optimization procedure. Without a deeper analysis, the generalizability of this finding is uncertain.
- **Resolution test** Provide a more detailed analysis of the data transfer experiment. Compare against additional baselines, such as random initialization with the same number of sequences, or initialization with pre-optimized sequences from the same condition. Discuss possible reasons for the observed improvement. If the effect is robust, consider a follow-up experiment with a different pair of conditions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "Python code for model training and evaluation will be made available in an open repository" (Code availability).
- **Evidence pointer** Code availability section
- **Concern** The code is not yet available, and the methods section does not provide sufficient detail to reproduce the results independently. The MLP ensemble architecture is described in a table (Table S1) that is not included in the submitted material. The pseudocode for the active learning loop is mentioned but not shown. The exact procedure for the NK model implementation is referenced to an external repository, but the adaptation to nucleotide sequences is not fully described.
- **Why it matters** Reproducibility is a core requirement for scientific claims. Without access to the code and full methodological details, other researchers cannot verify the results or build on the method. This is particularly important given the complexity of the active learning loop and the number of design choices involved.
- **Resolution test** Make the code available at the time of submission or provide a detailed algorithmic description in the methods. Include the full architecture table and hyperparameter settings. Describe the NK model adaptation in sufficient detail to be implemented independently.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Equation (1) and the description of the reward function
- **Evidence pointer** Section 2.1, Section 4.2
- **Issue** The parameter ff is described as controlling the balance between exploration and exploitation, but the text says "exploration and exploration" in one place (Section 4.2). The scaling of ff for the promoter datasets is mentioned but not specified precisely.
- **Required correction** Fix the typo. Provide the exact formula for scaling ff based on sequence length difference.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1C description
- **Evidence pointer** Section 2.1
- **Issue** The t-SNE visualization is mentioned but the figure is not described in detail. It is unclear what the colors or labels represent.
- **Required correction** Add a brief description of the t-SNE plot in the text or figure legend.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Supplementary figures
- **Evidence pointer** Multiple references to Supplementary Figures S1-S10
- **Issue** The supplementary figures are referenced but not provided in the submitted material. This makes it impossible to assess the supporting evidence.
- **Required correction** Include the supplementary figures in the submission or provide a summary of their content in the main text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 4.5
- **Evidence pointer** Section 4.5
- **Issue** The term "surrogetes" is used instead of "surrogates".
- **Required correction** Fix the typo.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Figure 3B
- **Evidence pointer** Section 2.2
- **Issue** The two data scenarios (broad range vs. low expression) are described, but it is not clear how the initial batches were selected. Were they randomly sampled from the full dataset, or were they specifically chosen to represent these scenarios?
- **Required correction** Clarify the selection procedure for the initial batches.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Section 3
- **Issue** The discussion mentions that active learning has been applied to protein engineering and other tasks, but does not compare the present approach to those prior works in detail. The novelty of the contribution is not clearly positioned.
- **Required correction** Add a brief comparison with prior active learning applications in biological sequence design, highlighting what is new in this work.

## Risk / unsupported claims

- The claim that active learning "can outperform one-shot optimization approaches" is not fully supported due to the potential confound of data quantity (R1-M1).
- The claim that active learning "can effectively optimize sequences" in the yeast promoter landscape is not supported by experimental validation, as all evaluations are done via a surrogate model (R1-M2).
- The claim that "active learning can effectively leverage datasets from different conditions" is based on a single experiment with limited baselines and no mechanistic explanation (R1-M4).
- The claim that recombination sampling outperforms directed evolution and genetic drift is not supported by statistical analysis (R1-M3).
- The claim that motif-based reward modification improves performance is presented without statistical support or analysis of which motifs drive the improvement.
- The generalizability of the findings to other regulatory elements (e.g., enhancers, terminators) or other organisms is not demonstrated and should not be inferred.