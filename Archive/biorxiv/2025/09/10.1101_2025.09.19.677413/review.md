## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific claims, methodological soundness, interpretability of reported results, and alignment with stated conclusions based on text alone
- **Shared manuscript claim summary** The authors present simple and biophysical neural networks that predict transcriptional activation domain strength and transcription factor abundance from 40-amino-acid sequences. They report that these interpretable networks recover known activation domain features, reveal position-dependent grammar signals for acidic and hydrophobic residues, and help interpret post-hoc analyses of deeper networks.
- **Visible evidence base** Text descriptions of results, architecture details, dataset composition, training procedures, and comparisons to published predictors. No figures, tables, or supplementary data were provided.
- **Missing materials affecting confidence** All figures (including Figure 1-4 and S1-S14), tables, and supplementary tables are absent. Quantitative performance metrics are referenced but not shown. Statistical details, hyperparameter settings, and code outputs are not verifiable from the supplied text.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important problem in computational biology, namely the interpretability of neural networks applied to transcriptional activation domain prediction. The authors propose a pragmatic approach combining simple architectures with biophysical models, and they report biologically plausible findings. However, the absence of all figures, tables, and quantitative results makes it impossible to evaluate the strength of the evidence. The claims about grammar signals and the utility of biophysical networks for interpreting deeper models rest on visual and numerical data that are not accessible in this submission. The conceptual framework is sound and the writing is clear, but the manuscript cannot be assessed for technical soundness without the missing materials.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, intrinsically disordered proteins, and machine learning interpretability would find this work relevant. The separation of protein abundance and coactivator binding contributions to activation domain function is a conceptual advance that could inform both mechanistic studies of transcription factors and the design of synthetic activation domains. The methodological comparison between simple, biophysical, and deep networks also speaks to a broader audience interested in interpretable AI for biology.
- **Major strengths** The authors address a genuine gap in the field by prioritizing interpretability without sacrificing predictive accuracy. The design of biophysical networks that explicitly model equilibrium states is conceptually elegant and grounded in established models of activation domain function. The use of multiple network architectures trained in parallel to distinguish robust trends from noise is a rigorous approach. The authors also demonstrate intellectual honesty by reporting that the three-state model did not learn the expected acidic exposure model, which strengthens the credibility of their interpretations.
- **Major Concerns** The absence of all figures and tables is a critical limitation. The manuscript repeatedly references specific results, such as parameter visualizations, performance comparisons, and correlation analyses, that cannot be evaluated. The claim that biophysical networks reveal position-dependent grammar signals is central to the paper, but the supporting evidence is not visible. Additionally, the comparison to existing predictors is described qualitatively, and the reported Pearson correlations are not contextualized with confidence intervals or statistical tests. The generalizability claims based on new datasets are mentioned but not substantiated with data.
- **Minor Comments** The writing is generally clear and accessible, though some sections, particularly the description of how network parameters function, may be dense for non-specialist readers. The authors could benefit from a brief primer on how convolutional filters and dense layer weights are interpreted in this context. The discussion of alternative explanations for the three-state model results is thoughtful, but the speculative nature of these explanations should be more clearly flagged. The manuscript would also benefit from a more explicit statement of the limitations of the biophysical assumptions, particularly the equilibrium assumption and the linear relationship between bound state and GFP expression.
- **Technical failings that need to be addressed before the case is established** The core technical evidence, including all figures, tables, and quantitative comparisons, is missing. Without these, the claims about grammar signals, performance parity with deep networks, and the utility of biophysical networks for interpreting deeper models cannot be verified. The statistical treatment of performance differences, the robustness of findings across random initializations, and the validation on external datasets are all referenced but not demonstrated.
- **Assessment against Nature-style criteria** Originality: The combination of simple and biophysical neural networks for activation domain prediction is a novel contribution, though the individual components are established. Scientific importance: The separation of abundance and coactivator binding effects on activation domain function is conceptually important and could influence both basic and applied research. Interdisciplinary readership: The work bridges machine learning, biophysics, and molecular biology, and the writing is largely accessible to all three communities. Technical soundness: Cannot be assessed from the provided text alone; the missing figures and tables are essential. Readability for nonspecialists: The manuscript is well written, but the methods section assumes familiarity with neural network architectures and biophysical modeling.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework and methodological approach are promising, and the authors have clearly invested in rigorous training and interpretation strategies. However, the current submission does not provide sufficient evidence to establish the central claims. Provision of all figures, tables, and quantitative results is essential for a fair evaluation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that biophysical neural networks reveal position-dependent grammar signals for acidic and hydrophobic residues, including that negative amino acids have position-specific effects on TF abundance and coactivator binding, and that hydrophobic amino acids have conflicting C-terminal effects.
- **Evidence pointer** Figures 3E, 3F, 4E, 4F, S9, S13; location not provided
- **Concern** The central findings of this manuscript are presented as visual interpretations of network parameters and averaged trends across random initializations. None of these figures are available in the submitted material. Without seeing the parameter visualizations, the averaged trends, and the statistical support for these trends, the claims about grammar signals cannot be evaluated. The text describes patterns, but the reader cannot verify the magnitude, consistency, or significance of these effects.
- **Why it matters** The identification of position-dependent grammar is the primary novel biological insight of the paper. If the supporting evidence is weak or ambiguous, the conclusions would be substantially weakened. The absence of this evidence prevents any assessment of whether the claims are justified.
- **Resolution test** Provide all figures and supplementary figures with clear annotations. Include statistical summaries of parameter trends across random initializations, such as confidence intervals or effect sizes, to demonstrate that the reported patterns are robust.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative validation
- **Claim pointer** The authors state that their simple and biophysical neural networks achieve similar accuracy to deeper networks, with the simple network performing slightly worse than ADhunter-GFP and PADDLE on regression and classification tasks.
- **Evidence pointer** Figures 1C, 1D, 2B, S8, Table S1; location not provided
- **Concern** The manuscript reports Pearson correlations and qualitative comparisons to existing predictors, but the actual performance values, error bars, and statistical tests are not shown. The claim that performance is "similar" or "slightly worse" is not quantified. Additionally, the comparison to TADA and ADPred as classifiers versus regressors is described, but the classification metrics are not provided.
- **Why it matters** The authors explicitly state that their goal is not to outperform existing predictors but to achieve similar accuracy with greater interpretability. This claim requires quantitative evidence. Without performance numbers and appropriate statistical comparisons, the reader cannot determine whether the interpretability gains come at an acceptable cost in accuracy.
- **Resolution test** Include all performance metrics in figures and tables, with error bars or confidence intervals. Report the results of statistical tests comparing the simple and biophysical networks to the deep networks on both regression and classification tasks. Clarify the metric used for classification comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation and biological interpretation
- **Claim pointer** The authors claim that the biophysical networks help interpret post-hoc analyses of deeper networks, specifically that negative amino acids have bifunctional roles and that hydrophobic residues at the C-terminus decrease abundance while increasing coactivator binding.
- **Evidence pointer** Figures 3G, 3H, S10, S11; location not provided
- **Concern** The manuscript describes correlations between biophysical network parameters and DeepLIFT scores from ADhunter-ratio, as well as PADDLE mutation analyses. These comparisons are central to the claim that biophysical networks aid in interpreting deeper models. However, the actual correlation values, the mutation analysis results, and the FINCHES correlation are not shown. The text mentions that the equilibrium constant correlates with FINCHES-predicted interaction strength, but the strength and significance of this correlation are not reported.
- **Why it matters** The claim that biophysical networks can serve as a bridge to interpret deeper networks is a key methodological contribution. Without the supporting data, this claim is unsubstantiated. The biological interpretation of the grammar signals also depends on the FINCHES correlation, which is not visible.
- **Resolution test** Provide the correlation plots and statistics for the equilibrium constant versus FINCHES scores. Show the DeepLIFT and PADDLE mutation results with appropriate visualizations and statistical summaries. Clearly state the number of sequences analyzed and the significance thresholds used.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Neural network training and architecture details
- **Evidence pointer** Methods section, Neural Network design and Neural Network training; location not provided
- **Issue** The description of the two-stage training procedure for the biophysical networks is somewhat unclear. The text states that the abundance predictor is trained first, then the activation domain strength module is trained with frozen abundance weights, but the exact loss functions and the role of the hill function are described only briefly.
- **Required correction** Provide a more detailed description of the training procedure, including the exact loss functions, the hill function parameters, and how the equilibrium constants are constrained to be positive. A pseudocode or schematic would be helpful.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Performance comparisons and parameter interpretations
- **Evidence pointer** Results sections, Figures 1C, 1D, 2B, S8; location not provided
- **Issue** The manuscript reports performance differences between networks but does not indicate whether these differences are statistically significant. The text states that "most convolutional filter sizes fell within the noise caused by random initialization," but the noise level is not quantified.
- **Required correction** Report the variance across random initializations for each network configuration and include statistical tests, such as paired t-tests or confidence intervals, for performance comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Generalizability claims
- **Affected element** Discussion of external validation
- **Evidence pointer** Discussion section, Table S1; location not provided
- **Issue** The authors state that their networks generalize to new datasets, but the details of these datasets and the performance metrics are not provided in the text.
- **Required correction** Describe the external datasets used for validation, the performance metrics, and the results in the main text or a clearly referenced table.

## Risk / unsupported claims
- The claim that biophysical networks reveal position-dependent grammar signals for acidic and hydrophobic residues is unsupported without the referenced figures and statistical analyses.
- The claim that the equilibrium constant correlates with FINCHES-predicted interaction strength is unsupported without the correlation value and plot.
- The claim that the simple and biophysical networks achieve similar accuracy to deeper networks is unsupported without quantitative performance metrics and statistical comparisons.
- The claim that the three-state biophysical network is not learning the acidic exposure model is based on parameter interpretations that are not visible.
- The claim that the networks generalize to new datasets is unsupported without details of the external validation.
- The claim that the biophysical networks help interpret post-hoc analyses of deeper networks is unsupported without the DeepLIFT and PADDLE mutation results.