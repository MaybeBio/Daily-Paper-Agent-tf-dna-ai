## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, conclusion, and supplementary material references
- **Assessment boundary** Scientific claims, methodological soundness, experimental design, statistical analysis, and interpretation of results as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose a hybrid approach combining protein language model (pLM) embeddings with graph neural networks (GNNs) for protein-ligand binding residue prediction. They report that structure information consistently improves predictive performance in absolute terms, but the relative contribution of structure diminishes with increasing pLM complexity, suggesting that complex pLMs already encode substantial structural information.
- **Visible evidence base** Tables 1-6, Figures 1-4, supplementary tables 1-8, statistical significance tests (t-tests), comparisons with existing methods (TargetS, EC-RUS, SXG-Bsite, GraphBind, GraphSite, GeoBind, EquiPNAS)
- **Missing materials affecting confidence** Full supplementary tables and figures not provided in the submitted material; exact hyperparameter ranges for manual tuning not fully specified; details of the random graph perturbation procedure partially described; complete dataset statistics for the DNA/RNA benchmark not visible

## Reviewer

### Overall assessment
The manuscript addresses a timely and relevant question in computational structural biology: whether and to what extent structural information contributes to binding residue prediction when powerful protein language model embeddings are used. The experimental design is thoughtful, comparing multiple pLM embeddings of varying complexity against a structure-free baseline and a structure-based GNN architecture. The central finding, that structure improves performance in absolute terms but with diminishing relative contribution as pLM complexity increases, is interesting and potentially useful for the field. However, several methodological details require clarification, and the statistical framework for comparing improvements across conditions could be strengthened. The claim that complex pLMs "contain structural information" is plausible but the evidence presented is indirect and would benefit from more direct probing. Overall, the work is a solid contribution to the ongoing discussion about the role of structure in deep learning-based protein function prediction, but the strength of the conclusions should be tempered given the limitations in experimental design and analysis.

### Who would be interested in the results, and why
Computational biologists and bioinformaticians working on protein function prediction, binding site annotation, and the application of protein language models to structural biology tasks would find this work relevant. The manuscript speaks directly to practitioners deciding whether to invest in structure-based pipelines or rely on sequence-only approaches. The finding that complex pLMs reduce the marginal value of explicit structure information has practical implications for tool development and resource allocation. Researchers developing hybrid sequence-structure models, as well as those interested in interpretability of pLM representations, would also benefit from the analysis. The work may also be of interest to the broader machine learning for biology community studying what information is captured by large pre-trained models.

### Major strengths
1. The research question is clearly formulated and practically relevant.
2. The experimental design systematically varies both the embedding complexity and the graph construction parameters, allowing for a nuanced analysis.
3. The comparison against a random graph baseline is a clever control that helps isolate the effect of genuine structural information from mere graph propagation.
4. The inclusion of multiple pLMs of varying complexity strengthens the generalizability of the conclusions.
5. The statistical significance testing adds rigor to the claim that structure improves performance.
6. The comparison with existing methods on a benchmark dataset situates the work in the broader literature.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** The authors claim that "using the structure information consistently enhances the predictive power of baselines in absolute terms" and that "the relative impact of the structure information represented by the GNN architecture diminishes" with more complex pLMs.
- **Evidence pointer** Tables 4 and 5, Section 3.6
- **Concern** The statistical significance testing is performed on the improvement of the GNN over the sequence baseline within each embedding condition, but no statistical comparison is made between the improvement magnitudes across different embedding conditions. The claim that the relative improvement diminishes with pLM complexity is based on visual inspection of average values rather than a formal statistical test comparing the improvement distributions across conditions. Without such a test, the conclusion that complex pLMs reduce the value of structure information is not rigorously established.
- **Why it matters** The central conclusion of the manuscript rests on the differential effect of structure across embedding types. If the differences in improvement across conditions are not statistically significant, the main claim is weakened.
- **Resolution test** Perform a formal statistical comparison of the improvement values across embedding conditions, for example using a paired test or ANOVA across the ligand datasets, and report the results. Alternatively, provide confidence intervals for the improvement values that allow direct comparison.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The authors state that "the hyperparameters of the GNN models were chosen after manual tuning on a random validation split from the training set."
- **Evidence pointer** Section 2.5, Supplementary table 6
- **Concern** The hyperparameter tuning procedure is described as manual and performed on a single random validation split. This raises concerns about potential overfitting to the validation set and lack of robustness in the reported results. The range of hyperparameters tried is only referenced in supplementary material that was not provided. Without a more systematic tuning procedure or at least multiple random splits, the reported performance may be optimistically biased.
- **Why it matters** If the hyperparameters are overfit to a particular validation split, the reported improvements of the GNN over the baseline may not generalize to new data, undermining the reliability of the conclusions.
- **Resolution test** Provide details of the hyperparameter search space and either use a more systematic approach such as cross-validated hyperparameter selection or demonstrate that the results are stable across multiple random validation splits.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence strength
- **Claim pointer** The authors conclude that "complex pLMs still contain structural information that lead to good predictive performance even without using 3D structure."
- **Evidence pointer** Section 3.6, Tables 4 and 6
- **Concern** The evidence for this claim is indirect. The authors show that the relative improvement from structure decreases with pLM complexity, which is consistent with pLMs encoding structural information, but this is not a direct demonstration. Alternative explanations include the possibility that complex pLMs simply provide better sequence-based features that are less complementary to structure, or that the GNN architecture is less able to exploit structure when features are already rich. The random graph experiment partially addresses this, but the interpretation remains speculative.
- **Why it matters** The conclusion is framed as a substantive finding about pLM representations, but the experimental design does not directly probe what information is encoded in the embeddings. Overstating this claim could mislead readers about the interpretability of pLM representations.
- **Resolution test** Consider additional analyses that more directly probe structural information in pLM embeddings, such as probing tasks or analysis of embedding geometry, or temper the conclusion to reflect the indirect nature of the evidence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors claim that their approach is "comparable with recently published methods that predict nucleic acid binding using GNNs" based on the DNA/RNA benchmark results.
- **Evidence pointer** Section 3.5, Supplementary table 8
- **Concern** The comparison with GraphBind, GraphSite, GeoBind, and EquiPNAS is only briefly described, and the full results are in supplementary material that was not provided. The authors state that they report scores "directly from the original published results" which raises concerns about comparability of evaluation protocols, data splits, and metrics across methods. Without a careful re-implementation or at least a detailed description of how the comparison was made consistent, the claim of comparability is difficult to assess.
- **Why it matters** The claim that the proposed method is competitive with state-of-the-art structure-based methods is important for the perceived impact of the work. If the comparison is not rigorous, this claim is not substantiated.
- **Resolution test** Provide the full comparison table and a detailed description of how the comparison was conducted, including any efforts to ensure consistent evaluation protocols. If direct comparison is not possible, temper the claim accordingly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, protein graph construction
- **Evidence pointer** Section 2.1
- **Issue** The description of the graph construction states that edges are added when the distance between alpha-carbon atoms is below a threshold, but it is not clear whether this is the only criterion or if other factors such as sequence separation are considered. Additionally, the use of the degree symbol in "4, 6, 8, and 10 ° A" is unusual and may be a typographical error.
- **Required correction** Clarify the graph construction criteria, including whether sequence-adjacent residues are always connected regardless of distance. Correct the unit notation to "Å" or "Angstrom".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.5, model training
- **Evidence pointer** Section 2.5
- **Issue** The training procedure is described as stopping at the epoch with the best validation MCC, but it is not specified whether early stopping is based on the validation set from the random split or a separate validation set. The relationship between the validation split used for early stopping and the validation split used for hyperparameter tuning is unclear.
- **Required correction** Clarify the data splitting procedure, including how the validation set for early stopping relates to the validation set for hyperparameter tuning and the independent test set.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3.4, attention analysis
- **Evidence pointer** Section 3.4, Figure 4
- **Issue** The attention analysis is described qualitatively, and the figure is referenced but not described in detail. The authors note that "in many cases, the residues with the highest attention were the other ligand-binding residues," but no quantitative summary is provided.
- **Required correction** Provide a more quantitative description of the attention analysis, such as the fraction of cases where high-attention residues were binding residues, or a statistical comparison against a random baseline.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.5, comparison with existing methods
- **Evidence pointer** Section 3.5
- **Issue** The comparison with TargetS, EC-RUS, and SXG-Bsite is presented in Table 3, but the table is not visible in the provided material. The authors state that their method outperforms these methods on MCC for all ligands, but without seeing the table, this claim cannot be evaluated.
- **Required correction** Ensure that the table is included in the final submission and that the comparison is described in sufficient detail in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Location not provided
- **Issue** The manuscript contains several instances of informal or imprecise language, such as "we were further wondering" and "it was not clear how could the residues." These reduce the professional tone of the manuscript.
- **Required correction** Revise the language throughout for a more formal academic style.

### Technical failings that need to be addressed before the case is established
1. Lack of formal statistical comparison of improvement magnitudes across embedding conditions (R1-M1).
2. Insufficient detail on hyperparameter tuning procedure and potential overfitting (R1-M2).
3. Indirect evidence for the claim that pLMs encode structural information (R1-M3).
4. Incomplete description of the comparison with nucleic acid binding methods (R1-M4).

### Assessment against Nature-style criteria
- **Originality** The question of whether structure matters when pLMs are used for binding residue prediction is timely and somewhat novel, as most prior work has focused on either sequence-based or structure-based approaches in isolation. The systematic comparison across pLM complexities adds a useful dimension. However, the overall approach of combining pLMs with GNNs is not entirely new, and the novelty lies primarily in the specific question asked rather than in methodological innovation.
- **Scientific importance** The findings have practical implications for the design of binding site prediction tools and contribute to the ongoing discussion about the value of experimental structures versus predicted structures in the era of deep learning. The work is relevant to a moderate-sized community of computational biologists and bioinformaticians. The importance is solid but not exceptional.
- **Interdisciplinary readership** The manuscript is primarily of interest to computational biologists and bioinformaticians. The concepts are accessible to those with a background in machine learning and protein structure, but the work is unlikely to attract a broad interdisciplinary audience beyond this niche.
- **Technical soundness** The experimental design is generally sound, with appropriate baselines and controls such as the random graph perturbation. However, the statistical analysis is incomplete, as noted in R1-M1, and the hyperparameter tuning procedure raises concerns about robustness. The technical execution appears competent but would benefit from additional rigor.
- **Readability for nonspecialists** The manuscript is reasonably well-written and the main ideas are explained clearly. However, some sections, particularly the description of the attention analysis, could be more accessible. The use of technical jargon is appropriate for the target audience but may limit readability for a broader scientific audience.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses a relevant question with a thoughtful experimental design, and the main findings are potentially useful. However, the statistical analysis needs to be strengthened to support the central claim about diminishing returns of structure with pLM complexity, and the hyperparameter tuning procedure should be clarified. The comparison with existing methods should also be more rigorously described. If these concerns are addressed, the work would be a solid contribution to the field.

## Risk / unsupported claims
- The claim that "complex pLMs still contain structural information" is not directly supported by the experimental design and should be tempered or supplemented with additional analyses.
- The claim that the proposed approach is "comparable with recently published methods" for nucleic acid binding prediction is not fully verifiable from the provided material, as the full comparison table and methodological details are in supplementary material not provided.
- The statement that "the model's performance varies with the cutoff distance" is supported by the data, but the lack of a consistent trend across ligands makes it difficult to draw general conclusions.
- The claim that the ensemble model "removes the bias of choosing a predefined cutoff distance" is plausible but not directly tested against a systematic selection of cutoff distance.
- The assertion that "the graph attention mechanism significantly enhances predictive performance for densely connected graphs" is based on the comparison between GCN and GAT, but the statistical significance of this difference is not formally tested.