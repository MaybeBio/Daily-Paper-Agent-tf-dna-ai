## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, conclusion, key points) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text; figure and table contents are referenced but not directly inspectable
- **Shared manuscript claim summary** The authors propose a few-shot learning framework integrating AlphaFold2 subsampling, ensemble docking, and Siamese learning (STGNet) to predict relative protein-ligand binding affinity changes induced by mutations, validated on 31 ABL kinase variants and 6 tyrosine kinase inhibitors
- **Visible evidence base** Text descriptions of results, methodological details, and references to figures (Fig. 1-9), tables (Table S1-S6), and supplementary figures (Fig. S1-S11); no numerical data, error bars, or statistical test outputs are directly visible
- **Missing materials affecting confidence** All figures, tables, and supplementary materials; numerical performance metrics (RMSE, MAE, Pearson, Spearman values); details of the TKI dataset composition; FEP+ comparison methodology; hyperparameter choices; training/validation splits for the main model; ablation study details

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational drug discovery, namely predicting mutation-induced changes in protein-ligand binding affinity without requiring crystal structures of mutants. The integration of AlphaFold2 subsampling with ensemble docking and Siamese learning is conceptually interesting and the few-shot learning framing is appropriate for the small-data regime typical of mutation studies. However, the current text provides insufficient quantitative evidence to evaluate the central claims. Key performance metrics are referenced only through figures and tables that are not available for inspection, and several methodological details that would be essential for reproducibility are either missing or described at a level that prevents independent assessment. The comparison with FEP+ is mentioned but the basis for this comparison is not described. The claim of transferability to other drug-target systems is plausible but not demonstrated. The manuscript has potential but the evidence base as provided is insufficient to establish the case.

- **Who would be interested in the results, and why** Computational chemists and structural biologists working on binding affinity prediction, particularly those interested in mutation effects and drug resistance. Researchers developing few-shot or transfer learning approaches for molecular property prediction would also find the methodology relevant. The pharmaceutical industry community focused on resistance profiling for kinase inhibitors may find the application direction valuable, though the current validation on a single kinase family limits immediate practical utility.

- **Major strengths**
  1. The problem is well-motivated and practically important. Drug resistance through mutation is a major clinical challenge, and methods that can predict resistance without mutant crystal structures would be valuable.
  2. The conceptual integration of conformational sampling via AF2 subsampling with relative binding affinity prediction is a sensible and potentially novel direction. The use of Gaussian filtering to select representative conformations is a reasonable statistical approach.
  3. The few-shot learning framing is appropriate and the Siamese architecture is a natural fit for relative prediction tasks.
  4. The authors are transparent about limitations, acknowledging that computational accuracy does not match FEP+ while claiming superior ranking performance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that the proposed method achieves higher ranking accuracy than both molecular docking and FEP+ for five out of six TKI molecules, as evidenced by highest Spearman correlation coefficients
- **Evidence pointer** Fig. 6, Table S2-S5; location not provided
- **Concern** The central performance claim is presented entirely through references to figures and tables that are not available in the provided material. No numerical values for Spearman coefficients, RMSE, or MAE are given in the text. Without access to these data, it is impossible to assess whether the claimed improvements are statistically meaningful, whether error bars or confidence intervals are reported, or whether the comparison with FEP+ is apples-to-apples. The claim that the method outperforms FEP+ in ranking is particularly consequential and requires scrutiny of the FEP+ protocol, the number of FEP+ calculations performed, and whether the same conformational ensembles were used.
- **Why it matters** The central contribution of the manuscript is the claimed improvement in ranking accuracy. If the underlying data do not support this claim, the manuscript has no substantive result. The absence of visible quantitative evidence prevents any assessment of effect sizes, variability, or statistical significance.
- **Resolution test** Provide the numerical values for all performance metrics in the main text or in a clearly readable table. Report confidence intervals or standard deviations across repeated runs. Describe the FEP+ protocol in sufficient detail to assess comparability, including the number of FEP+ calculations, the force field, and the simulation length.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The manuscript claims that the STGNet model with 50-fold data augmentation achieves the best performance, and that the top50 dataset reduces RMSE and MAE
- **Evidence pointer** Fig. 8, Fig. S10; location not provided
- **Concern** The choice of k = 50 as the optimal augmentation factor is presented as an empirical finding, but the text does not describe how this value was selected. Was it chosen by validation performance? If so, what was the validation protocol? The claim that top100 performs slightly worse than top50 due to "excessive conformational changes" is plausible but is presented without supporting analysis. The relationship between augmentation factor and model performance is a key methodological contribution, and the current description is insufficient to understand the trade-off.
- **Why it matters** The augmentation strategy is a core component of the proposed method. Without understanding how the optimal augmentation level was determined and whether this choice generalizes, the method cannot be applied by others. The risk of overfitting to the specific TKI dataset is not addressed.
- **Resolution test** Describe the model selection procedure, including how k was chosen and whether this was done on a held-out validation set. Provide learning curves or a table showing performance as a function of k. Discuss the risk of overfitting to the augmentation factor.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparison validity
- **Claim pointer** The manuscript claims that the proposed method outperforms both molecular docking and FEP+ in ranking accuracy for five out of six TKI molecules
- **Evidence pointer** Fig. 5, Fig. 6; location not provided
- **Concern** The comparison with FEP+ is mentioned but the methodology is not described. FEP+ is a physics-based approach that requires significant computational resources and careful setup. The text does not state whether the FEP+ results were taken from the original publication by Hauser et al. or whether new FEP+ calculations were performed. If taken from the literature, were the same experimental measurements used? If new calculations were performed, what was the protocol? The comparison with molecular docking is also unclear: the docking scores are used as inputs to the model, so comparing the model output to raw docking scores may not be a fair comparison.
- **Why it matters** The claim of superiority over FEP+ is the strongest claim in the manuscript. If the comparison is not properly controlled, the claim is not credible. The relationship between the docking scores used as model inputs and the docking baseline used for comparison needs to be clarified.
- **Resolution test** Clearly state the source of the FEP+ data and the comparison protocol. If FEP+ results are from the literature, confirm that the same experimental data and the same mutant set were used. If new FEP+ calculations were performed, provide full methodological details. Clarify whether the docking baseline uses the same docking protocol as the one used to generate model inputs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript claims that the method can be transferred and applied to other drug-target interaction predictions
- **Evidence pointer** Methods section; location not provided
- **Concern** The Methods section contains several incomplete descriptions. The mathematical formulation is presented with placeholder equations that are not fully specified. The description of the STGNet architecture mentions MPNN and GIGN components but does not provide sufficient detail on layer sizes, number of layers, activation functions, or training hyperparameters. The data preprocessing steps are described at a high level but lack specific parameters. The statement in the footnotes that the mathematical formula was revised suggests the current version may still contain errors.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publication. Without complete methodological details, other researchers cannot implement or evaluate the proposed method. The claim of transferability cannot be assessed without a complete method description.
- **Resolution test** Provide complete architectural details for STGNet, including all hyperparameters. Complete the mathematical formulation with all terms defined. Describe the training procedure, including loss function, optimizer, learning rate, batch size, and number of epochs. Provide the full data preprocessing pipeline with all parameters.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalization evidence
- **Claim pointer** The manuscript claims that the approach can be transferred to other drug-target interaction predictions when conformational flexibility needs to be considered
- **Evidence pointer** Conclusion section; location not provided
- **Concern** The validation is performed exclusively on ABL kinase with six TKI molecules. While the authors state that the method can be transferred, no evidence is provided to support this claim. The choice of ABL kinase is motivated by drug resistance, but the method's dependence on AF2 subsampling quality, docking accuracy, and the availability of experimental binding data for related mutants may limit generalizability. The manuscript does not discuss potential failure modes or conditions under which the method might not work.
- **Why it matters** The claim of transferability is used to justify the broader significance of the work. Without evidence or at least a reasoned analysis of generalizability, this claim is speculative.
- **Resolution test** Either provide preliminary results on a second protein system or temper the claim to reflect the current evidence base. Discuss the conditions under which the method is expected to work or fail.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that the method achieves an increased Spearman correlation coefficient for five out of six TKI molecules, but does not provide the actual values or the baseline for comparison. The phrase "increased" is vague without a reference point.
- **Required correction** Provide the actual Spearman correlation values for the proposed method and the comparators in the abstract, or state the baseline explicitly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section
- **Evidence pointer** Section "Conformation sampling for ABL kinase using subsampled AF2"; location not provided
- **Issue** The term "WILD" is used to denote wild-type. This is nonstandard and could be confused with other meanings. The standard abbreviation is "WT".
- **Required correction** Replace "WILD" with "WT" throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Section "Improved predictive performance over physics-based methods"; location not provided
- **Issue** The text mentions that FEP+ results are "reported by Hauser et al." but does not specify whether the comparison uses the same experimental measurements, the same mutant set, and the same evaluation protocol. The basis for the comparison should be explicit.
- **Required correction** Add a sentence specifying the source of the FEP+ data and confirming that the evaluation protocol is consistent across methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Notation consistency
- **Affected element** Methods section
- **Evidence pointer** Section "Mathematical formulation"; location not provided
- **Issue** The notation for the predicted energy difference appears as both ΔΔΔ G pred and ΔΔΔ G pertb in different places. This inconsistency is confusing.
- **Required correction** Use a single notation throughout the manuscript.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Results section
- **Evidence pointer** Fig. 4, Fig. 9; location not provided
- **Issue** The text describes clustering results in Fig. 9A and conformational distributions in Fig. 9C, but the clustering method, the number of clusters, and the validation of cluster assignments are not described in the text.
- **Required correction** Add a brief description of the clustering procedure in the Methods or Results section.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Data availability
- **Evidence pointer** Data availability section; location not provided
- **Issue** The data availability statement only mentions AlphaFold2 subsampling prediction data. It is unclear whether the docking results, the training data, and the model weights are also available.
- **Required correction** Clarify the availability of all data and code components, including docking results and trained model weights.

## Risk / unsupported claims
- The claim of superior ranking performance over FEP+ for five out of six TKI molecules is unsupported in the provided text because no numerical results are visible and the FEP+ comparison protocol is not described.
- The claim that the method can be transferred to other drug-target interaction predictions is unsupported by evidence presented in the text.
- The claim that the top50 augmentation factor achieves the best performance is presented without supporting data or model selection details.
- The claim that the method captures conformational flexibility effects is plausible but not directly demonstrated with conformational analysis or comparison to experimental conformational data.
- The statement that the proposed method achieves "experimental level" accuracy through the equation ΔΔ G exp = ΔΔ G dock + ΔΔΔ G pred is not substantiated with numerical evidence in the provided text.