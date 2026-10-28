## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2025-09-26)
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the provided text; no external data or code were accessed
- **Shared manuscript claim summary** The authors present interpretable neural networks incorporating biophysical models of transcriptional activation domains (ADs) to predict activation domain strength and transcription factor abundance from 40-amino-acid sequences. They report that these biophysical NNs reveal sequence grammar signals, specifically position-dependent roles of acidic and hydrophobic residues, and that these signals help interpret post-hoc analyses of deeper NNs.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Methods sections; Figures 1–4 referenced; Supplementary Figures S1–S14 and Table S1 referenced but not provided
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S14, Table S1); actual parameter values from trained NNs; detailed architecture hyperparameters; code repository; full dataset statistics; FINCHES prediction details; DeepLIFT/PADDLE interpretation outputs

## Reviewer

### Overall assessment
This manuscript addresses a timely and important problem: interpretability of neural networks in biology, specifically for transcriptional activation domain prediction. The authors propose a pragmatic approach using simple and biophysical NNs, and report novel insights into sequence grammar, particularly the dual roles of acidic and hydrophobic residues in controlling both coactivator binding and protein abundance. The writing is clear and the motivation is well-articulated. However, the manuscript has several significant weaknesses that currently prevent full support. The central claims about "grammar" and the separation of abundance versus binding effects rest heavily on parameter interpretation, but the evidence provided in the main text is largely qualitative, with key quantitative validations relegated to supplementary materials that were not available for review. The biophysical model derivation is presented but not rigorously validated against independent experimental data. The comparison with deeper NNs is interesting but the interpretation of PADDLE results is speculative. The claim that the three-state model is "not learning the acidic exposure model" is based on parameter inspection, but the authors do not provide a clear statistical or quantitative framework for this conclusion. Overall, the work is promising and the approach is valuable, but the case is not fully established from the provided materials.

### Who would be interested in the results, and why
Computational biologists and machine learning researchers working on interpretable AI for genomics and protein function would find this work directly relevant. Researchers studying transcriptional activation domains, intrinsically disordered regions, and transcription factor biology would also be interested, as the findings propose specific residue-level grammar rules that could guide experimental validation. The broader community interested in hybrid physics-informed neural networks and the trade-off between accuracy and interpretability would also find value. The work is likely to be of interest to readers of Nature-level journals if the claims are rigorously supported, given the general importance of interpretable AI in biology.

### Major strengths
1. The problem is well-motivated and the approach is novel: building biophysical models into NN architecture for AD prediction is a creative and potentially impactful contribution.
2. The authors are transparent about limitations (e.g., random initialization effects, redundancy in NNs) and do not overstate accuracy improvements.
3. The parallel interpretation of multiple NNs (SimpleNN, BiophysicalNN, deep NNs) is a thoughtful strategy to cross-validate findings.
4. The identification of dual roles for acidic and hydrophobic residues, and the connection to protein abundance, is biologically interesting and could have broad implications.
5. The manuscript is generally well-written and accessible to a non-specialist audience, with clear explanations of NN components.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claims
- **Claim pointer** The authors claim that BiophysicalNNs reveal "two new ways that arrangement (i.e. the sequence grammar) of activation domain controlled function: 1) hydrophobic residues both increase activation domain strength and decrease protein abundance, and 2) acidic residues control both activation domain strength and protein abundance."
- **Evidence pointer** Results sections "Biophysical Neural Networks reveal activation domain grammar"; Figures 3E, 3F, 4E, 4F; Supplementary Figures S9, S13
- **Concern** The central claims about grammar are based on visual inspection of NN parameters (convolutional filter and dense layer weights). The authors state that "the BiophysicalNN learned that negative amino acids have two conflicting functions with position-specific dependence" and that "hydrophobic amino acids have conflicting C-terminal effects." However, the main text does not provide quantitative measures of these effects (e.g., effect sizes, confidence intervals, statistical tests comparing parameter values across random initializations). The supplementary figures are referenced but not provided, so the robustness of these patterns across the 1800 trained NNs cannot be assessed. Without a clear quantitative framework, the claim that these are "grammar" rules rather than noise or artifacts of a particular initialization is not established.
- **Why it matters** The primary scientific contribution of the manuscript is the identification of these grammar signals. If the evidence is only qualitative and not rigorously quantified, the conclusions are not reproducible or verifiable from the provided materials. This is a blocking issue for establishing the case.
- **Resolution test** Provide quantitative summaries of parameter values across all trained NNs (e.g., mean and standard deviation of filter weights for each residue at each position), statistical tests comparing positions (e.g., N-terminal vs. C-terminal effects), and effect sizes. Show that the patterns are consistent across random initializations and filter sizes. Include these data in the main text or clearly accessible supplementary materials.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of biophysical model
- **Claim pointer** The authors state that "we derived an equation relating the equilibrium constants between the states of the biophysical models to the experimental measures of activation domain strength and transcription factor abundance" and that the BiophysicalNNs "simultaneously predict transcription factor abundance and activation domain strength."
- **Evidence pointer** Methods section "Neural Network design"; Figures 3B, 4B, S7
- **Concern** The biophysical model derivation is presented in the Methods, but the assumptions are not critically examined. The authors assume that mCherry fluorescence equals total TF abundance and that GFP fluorescence is related to bound TF via a Hill function. These are strong assumptions. The manuscript does not provide evidence that these assumptions hold for the experimental system, nor does it compare the biophysical model predictions against independent experimental measurements of binding or abundance. The correlation with FINCHES predictions (Figure S10) is mentioned but not detailed in the main text, and the strength of this correlation is not reported. Without external validation, the "biophysical" interpretation of the NN parameters remains speculative.
- **Why it matters** The claim that the NNs are "biophysical" and that the intermediate values are meaningful equilibrium constants is central to the interpretability argument. If the model is not validated against independent biophysical data, the interpretation of parameters as reflecting true binding or abundance mechanisms is not justified.
- **Resolution test** Provide a detailed validation of the biophysical model, including: (1) comparison of predicted equilibrium constants against experimental binding measurements (e.g., from FINCHES or other assays) with correlation coefficients and significance; (2) sensitivity analysis of the assumptions (e.g., linear vs. Hill function); (3) demonstration that the model recovers known biophysical parameters where available. If such validation is not possible, temper the claims and clearly state the limitations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of deep NN post-hoc analyses
- **Claim pointer** The authors state that "the BiophysicalNNs helped us to understand the post-hoc interpretations of the deeper NNs, revealing that the deep NNs also learned bidirectional amino acid contributions" and that "the trends in our interpretation of ADhunter-ratio match the trends in the interpretation of ADhunter-ensemble."
- **Evidence pointer** Results section "Biophysical Neural Networks help to interpret more complicated NNs"; Figures 3G, 3H, S11
- **Concern** The comparison between BiophysicalNN and deep NN interpretations is qualitative. The authors state that patterns "match" but do not provide a quantitative comparison (e.g., correlation between DeepLIFT scores and BiophysicalNN parameters). The PADDLE interpretation is based on a different approach (mutational scanning) and the authors speculate that "there may have still been variability in TF abundance that contributed to reporter gene expression" in the PADDLE training data. This is a testable hypothesis, but no evidence is provided to support it. The claim that the BiophysicalNN "interprets the interpreters" is interesting but not rigorously demonstrated.
- **Why it matters** The manuscript's broader contribution is to show that simple biophysical NNs can aid in interpreting complex NNs. If this claim is not quantitatively supported, the practical utility of the approach is weakened.
- **Resolution test** Provide a quantitative comparison between BiophysicalNN parameters and DeepLIFT scores (e.g., correlation coefficients, overlap of important positions/residues). For the PADDLE analysis, test the hypothesis that abundance variation confounds the PADDLE training data, or clearly state that this is a hypothesis requiring further investigation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and dataset scope
- **Claim pointer** The authors state that "the biophysical neural networks revealed two new ways that arrangement of activation domain controlled function" and discuss implications for AD biology broadly.
- **Evidence pointer** Results sections; Discussion
- **Concern** The dataset is derived from Gcn4 homologs only. The authors do not test whether the identified grammar rules generalize to other AD families or transcription factors. The Discussion mentions this limitation only briefly. Given that the authors claim "new ways" of understanding AD function, the lack of cross-family validation is a significant gap.
- **Why it matters** The scientific impact of the findings depends on their generalizability. If the grammar rules are specific to Gcn4-like ADs, the claims should be appropriately scoped.
- **Resolution test** Validate the identified grammar rules on ADs from other families (e.g., using existing datasets or by training on additional AD families). If this is not feasible, clearly state the scope of the conclusions and avoid overgeneralization.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figures 1E, 1F, 3E, 3F, 4E, 4F
- **Evidence pointer** Results sections; Figures referenced
- **Issue** The parameter visualizations are described in the text but the figures are not provided in the manuscript text. The authors should ensure that the figures are self-explanatory, with clear labels for positions, residues, and the direction of effects (positive/negative).
- **Required correction** Provide detailed figure captions and ensure that the color scales and axes are clearly defined. Consider adding a schematic explaining how to read the parameter plots.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Performance comparisons (Figures 1C, 1D, 2B, 3D, 4D)
- **Evidence pointer** Results sections; Figures referenced
- **Issue** The manuscript reports Pearson correlations but does not provide confidence intervals or significance tests for differences between models. The statement that "all NN variations performed similarly, with individual differences likely coming from differences in random initialization" is not supported by statistical analysis.
- **Required correction** Report confidence intervals for correlations and perform statistical tests (e.g., paired tests across random seeds) to support claims of similarity or difference.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methods detail
- **Affected element** Training procedure
- **Evidence pointer** Methods section "Neural Network training"
- **Issue** The loss functions are described with equations, but the hyperparameters (e.g., learning rate schedule, batch size, early stopping criteria) are not fully specified. The penalty terms for negative weights and negative equilibrium constants are described but the weights (0.1) are only given for the second stage.
- **Required correction** Provide a complete list of hyperparameters and training details to ensure reproducibility.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Grammar" terminology
- **Evidence pointer** Throughout
- **Issue** The term "grammar" is used to describe position-dependent effects of residues. This is a useful metaphor, but it may be misinterpreted. The authors should define what they mean by "grammar" early in the manuscript and clarify that it refers to position-specific contributions, not a formal language model.
- **Required correction** Add a brief definition of "grammar" in the Introduction or Results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** External validation
- **Affected element** Generalization to human data
- **Evidence pointer** Results section "The simple neural network for predicting transcription factor abundance"; Figure S5
- **Issue** The analysis of human data (Figure S5) is mentioned but not described in the main text. The authors should provide more context on this analysis and its implications.
- **Required correction** Add a brief description of the human data analysis in the main text, including the source of the data and the key findings.

### Technical failings that need to be addressed before the case is established
1. Lack of quantitative evidence for the central grammar claims (R1-M1).
2. Insufficient validation of the biophysical model against independent experimental data (R1-M2).
3. Qualitative rather than quantitative comparison between BiophysicalNN and deep NN interpretations (R1-M3).
4. Incomplete reporting of training details and hyperparameters (R1-m3).
5. Missing statistical reporting for performance comparisons (R1-m2).

### Assessment against Nature-style criteria
- **Originality** The approach of embedding biophysical models into NN architecture for AD prediction is novel and distinct from prior work. The identification of dual roles for residues is potentially original, but the evidence is not yet sufficient to confirm novelty of the biological findings.
- **Scientific importance** The problem of interpretable AI in biology is of high importance. The specific findings on AD grammar, if validated, could have significant implications for understanding transcriptional regulation and for engineering synthetic transcription factors. However, the current evidence does not fully establish the importance of the specific claims.
- **Interdisciplinary readership** The work bridges machine learning, biophysics, and molecular biology. The writing is accessible, and the topic is likely to appeal to a broad readership. However, the lack of quantitative detail may limit appeal to more rigorous computational audiences.
- **Technical soundness** The NN architecture is reasonable and the training procedure is described, but the lack of validation of the biophysical model and the qualitative nature of the grammar analysis undermine technical soundness. The statistical reporting is insufficient.
- **Readability for nonspecialists** The manuscript is well-written and the concepts are explained clearly. The use of figures and schematics (if provided) would further aid readability. The Methods section is detailed but may be dense for non-experts.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an important problem and presents a promising approach, but the central claims are not quantitatively supported in the provided text. The authors should address the blocking concerns, particularly the quantitative validation of the grammar signals and the biophysical model, before the case can be considered established. If the supplementary materials provide the missing evidence, the manuscript could become supportive, but this cannot be assessed from the current submission.

## Risk / unsupported claims
- The claim that BiophysicalNNs reveal "two new ways" of grammar control is not quantitatively supported in the main text.
- The claim that the three-state BiophysicalNN is "not learning the acidic exposure model" is based on parameter inspection without a formal test.
- The claim that deep NNs "also learned bidirectional amino acid contributions" is based on qualitative comparison.
- The hypothesis that PADDLE training data had variability in TF abundance is speculative and not tested.
- The correlation between predicted equilibrium constants and FINCHES interaction strengths is mentioned but not quantified in the main text.
- The generalization of findings to human data (Figure S5) is not described in the main text and cannot be assessed.