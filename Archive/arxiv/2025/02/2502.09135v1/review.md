## Review setup
- **Input scope** Full manuscript text including main text, references, and appendix
- **Assessment boundary** Scientific claims, methodology, results interpretation, and reproducibility as presented in the provided manuscript
- **Shared manuscript claim summary** The authors train a sparse autoencoder on ESM-2 8M activations, interpret latent components against protein annotations, and demonstrate steering of sequence generation toward zinc finger features
- **Visible evidence base** Main text sections 1-5, Appendix A sections A.1-A.3, Figures 1, 2, 4, 5 (referenced), Table 1 (referenced), equations 1-8 (partially rendered)
- **Missing materials affecting confidence** Actual figure images, table contents, supplementary data, training curves, detailed hyperparameter results, and code implementation details are not visible in the provided text

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially valuable application of sparse autoencoders to protein language model interpretability. The core idea of linking SAE latents to biological annotations and using them for steering is conceptually sound and relevant to the growing field of mechanistic interpretability in biology. However, the current evidence base is insufficient to fully establish the claims. The interpretability analysis relies on correlational statistics without clear baselines or significance testing, and the steering results, while promising, show low success rates that raise questions about practical utility. The layer selection heuristic based on intrinsic dimension is interesting but its validation is incomplete. The manuscript would benefit from stronger quantitative evaluation, comparison against alternative interpretability methods, and more rigorous statistical treatment of the association analysis.
- **Who would be interested in the results, and why** Researchers in mechanistic interpretability of biological sequence models, protein language model developers, and computational biologists working on protein design would find this work relevant. The demonstration of steering toward zinc finger domains could interest protein engineers seeking controllable generation. The layer selection methodology may also appeal to those applying SAEs to other biological sequence models.
- **Major strengths** The work addresses an underexplored area by applying SAEs to protein language models, moving beyond natural language applications. The layer selection heuristic using intrinsic dimension is a thoughtful addition that could generalize. The authors provide open resources including model weights, code, and supplementary data, supporting reproducibility. The focus on actionable features for steering, rather than purely descriptive interpretability, is a practical strength.
- **Major Concerns** The interpretability analysis lacks statistical rigor, with no significance testing or baselines to distinguish genuine feature associations from chance. The steering results show low success rates (24 out of 180 sequences), and the comparison conditions are not fully described. The layer selection method is presented as principled but its advantage over simpler heuristics is not demonstrated. The manuscript does not compare against existing interpretability approaches for protein models, limiting the assessment of novelty and relative performance.
- **Minor Comments** The writing is generally clear but some technical details are underspecified. The appendix provides useful information but the hyperparameter sweep results are not fully presented. The choice of ESM-2 8M as the smallest model in the family is reasonable for initial exploration but limits generalizability claims. The discussion of limitations is brief and could be expanded.
- **Technical failings that need to be addressed before the case is established** The lack of statistical significance testing for latent-feature associations, the absence of baseline comparisons for the steering experiments, and the incomplete validation of the layer selection heuristic are the primary technical gaps that prevent the core claims from being fully supported.
- **Assessment against Nature-style criteria** Originality: Moderate to high, as SAE application to protein language models is relatively novel, though building on established SAE methods. Scientific importance: Moderate, with potential implications for protein design and model interpretability, but the demonstrated results are preliminary. Interdisciplinary readership: The work bridges machine learning and biology, but the presentation assumes familiarity with both fields, potentially limiting accessibility. Technical soundness: The methods are reasonable but the evaluation is incomplete, with insufficient statistical treatment and missing comparisons. Readability for nonspecialists: The manuscript is accessible to those with background in either field, but some concepts such as superposition and intrinsic dimension may require additional explanation for broader audiences.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical rigor and baseline comparisons. The core concept is promising but the current evidence does not fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim to identify 395 putative latent-feature associations with precision or recall exceeding 0.80
- **Evidence pointer** Section 3.3, Section 4.1, Table 1
- **Concern** The association analysis computes precision and recall for each latent-feature pair but does not include any statistical significance testing, multiple comparison correction, or comparison against null distributions. With a large number of latent components and annotation types, many associations could arise by chance. The threshold of 0.80 for precision or recall is arbitrary and its justification is not provided. The authors also do not assess how these associations compare to those obtained from a randomly initialized or untrained model, which would be a critical baseline.
- **Why it matters** Without statistical validation, the identified associations cannot be distinguished from spurious correlations. This undermines the reliability of the interpretability claims and the subsequent selection of latents for steering. The scientific community requires confidence that reported feature associations are genuine and reproducible.
- **Resolution test** The authors should provide a null distribution of precision and recall values, either through permutation testing or by analyzing a randomly initialized model, and report adjusted significance levels. They should also justify the threshold choice and demonstrate that the number of associations significantly exceeds what would be expected by chance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim successful steering toward zinc finger domains, with 24 matches out of 180 sequences when intervening on two latents
- **Evidence pointer** Section 3.4, Section 4.2
- **Concern** The steering experiment reports a success rate of approximately 13 percent for the best condition, which is low. The comparison conditions are not fully described: the baseline model and random latent interventions are mentioned but the details of these conditions, such as the number of runs, the specific random latents used, and the statistical variability across runs, are not provided. The manuscript does not report whether the 24 matches are statistically significant compared to what might be expected by chance, nor does it assess the quality of the matched sequences beyond similarity scores. The choice of zinc finger annotations as the target and the selection of the two most prominent latents are not justified in detail.
- **Why it matters** The steering claim is a central contribution of the paper. If the success rate is not significantly above chance or if the comparison conditions are not rigorous, the practical utility of the method is questionable. The scientific claim of successful steering requires robust evidence that the intervention specifically causes the observed outcome.
- **Resolution test** The authors should provide a more detailed experimental protocol, including the number of independent runs, the distribution of outcomes across runs, and a statistical test comparing the intervention condition against baselines. They should also report the expected number of matches by chance and demonstrate that the observed matches are significantly higher. Additionally, they should assess the functional relevance of the generated sequences beyond simple motif matching.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological validation
- **Claim pointer** The authors propose a heuristic for layer selection based on intrinsic dimension, claiming it identifies where abstract information is most clearly encoded
- **Evidence pointer** Section 3.2, Appendix A.3, Figure 4
- **Concern** The layer selection method is presented as principled, but the manuscript does not demonstrate that this approach outperforms simpler heuristics, such as choosing a fixed mid-layer or the last layer. The intrinsic dimension estimation is applied to a single model size, and the claim that larger models exhibit similar profiles is not supported by data shown in the manuscript. The relationship between intrinsic dimension plateaus and the quality of SAE features is asserted but not empirically validated. The authors do not compare the interpretability or steering outcomes when using layers selected by different methods.
- **Why it matters** The layer selection heuristic is presented as a contribution, but without validation, its utility is unclear. If the method does not provide a meaningful advantage over existing practices, its inclusion as a contribution is weakened. The scientific community needs evidence that the proposed method improves outcomes in a measurable way.
- **Resolution test** The authors should compare the quality of SAE features and steering outcomes when using layers selected by their heuristic versus alternative methods, such as random mid-layers or the final layer. They should also provide data supporting the claim that intrinsic dimension profiles are consistent across model sizes, or temper this claim accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that training details, hyperparameter selection, and additional results are in the appendix
- **Evidence pointer** Section 3.1, Appendix A.1, A.3
- **Concern** While the appendix provides some details, the hyperparameter sweep results are not fully presented. The manuscript mentions an elbow in the CE increase versus L0 plot but does not show the full Pareto frontier or the specific values for all hyperparameter combinations. The number of dead latents is reported for the selected model but not for other configurations. The training procedure lacks specifics such as the number of training steps, batch size, learning rate schedule, and computational resources used. The data preprocessing steps for the SCOPe dataset are not fully described.
- **Why it matters** Reproducibility is a core requirement for scientific contributions. Without complete training and evaluation details, other researchers cannot replicate the work or build upon it. The lack of full hyperparameter results also prevents assessment of the robustness of the model selection.
- **Resolution test** The authors should provide a complete description of the training procedure, including all hyperparameters, the full results of the hyperparameter sweep, and the criteria for model selection. They should also describe the data preprocessing steps in sufficient detail to allow replication.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, equation 1
- **Evidence pointer** Section 2.1
- **Issue** The loss function for masked language modeling is referenced but the equation is not rendered in the provided text. The notation for the probability term is unclear.
- **Required correction** Provide the full equation with clear notation and define all variables.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.3, threshold selection
- **Evidence pointer** Section 3.3
- **Issue** The threshold of 0.80 for precision or recall is stated without justification. The authors do not discuss how this threshold was chosen or its implications for the number of associations found.
- **Required correction** Provide a rationale for the threshold choice and discuss its sensitivity, possibly by showing results for different thresholds.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 4.2, sequence similarity
- **Evidence pointer** Section 4.2
- **Issue** The authors report an average sequence similarity of 31 percent among matched sequences but do not specify the similarity measure used or the comparison set.
- **Required correction** Specify the similarity metric and the reference set used for comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.4, steering procedure
- **Evidence pointer** Section 3.4, equations 7 and 8
- **Issue** The equations for the steering procedure are referenced but not rendered. The description of scaling and shifting the latent value is brief and lacks detail on how the parameters are chosen.
- **Required correction** Provide the full equations and describe the parameter selection process for the scaling and shifting factors.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Appendix A.1, dead latent reinitialization
- **Evidence pointer** Appendix A.1
- **Issue** The reinitialization procedure for dead latents is described but the specific method for reinitialization is not detailed.
- **Required correction** Describe the reinitialization procedure in more detail, including how the new weights are initialized.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 5, discussion
- **Evidence pointer** Section 5
- **Issue** The discussion is brief and does not address limitations of the approach, such as the low steering success rate or the potential for spurious associations.
- **Required correction** Expand the discussion to include a more thorough treatment of limitations and potential improvements.

## Risk / unsupported claims
- The claim of 395 putative latent-feature associations is unsupported without statistical significance testing or null distribution comparison
- The claim of successful steering toward zinc finger domains is weakly supported given the low success rate and incomplete baseline descriptions
- The claim that intrinsic dimension plateaus indicate where abstract information is most clearly encoded is asserted without direct empirical validation
- The claim that larger ESM-2 models exhibit similar intrinsic dimension profiles is not supported by data shown in the manuscript
- The statement that this is the first application of steering with sparse autoencoder features to generate complex protein sequences is not verifiable from the provided references
- The effectiveness of the steering procedure beyond the specific zinc finger case is not demonstrated
- The generalizability of the interpretability findings beyond the ESM-2 8M model is not established