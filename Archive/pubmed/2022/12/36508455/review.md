## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supporting information references.
- **Assessment boundary** Scientific claims, methodological soundness, statistical rigor, and interpretation of results as presented in the provided manuscript. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors propose that the number of regulating transcription factors (TFs) and the dynamics of TF binding, specifically cooperative and competitive binding, are the primary drivers of gene expression noise in yeast, surpassing the predictive power of previously implicated features such as TATA box presence and promoter nucleosome occupancy.
- **Visible evidence base** Analysis of two published datasets (mRNA noise from Nadal-Ribelles et al., protein noise from Newman et al.), a linear regression framework with 329 molecular features, and stochastic simulations of TF binding models.
- **Missing materials affecting confidence** The manuscript does not provide the full list of 329 features with sources, detailed correlation matrices, or the code for simulations and regression analyses. The specific statistical significance of differences between feature predictive powers is not fully reported. The MCMC sampling details are described but convergence diagnostics are not shown.

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in gene expression noise and presents a compelling, data-driven argument that TF binding dynamics, rather than static promoter features, are the primary noise determinants. The integration of a large feature set with predictive modeling is a strength. However, the central claim that TF binding "process" is the primary driver is inferred from correlative feature analysis and simplified simulations. The manuscript would be significantly strengthened by addressing the potential for confounding variables, providing more rigorous statistical comparisons between feature classes, and clarifying the biological interpretation of the simulation results.
- **Who would be interested in the results, and why** Researchers in gene regulation, systems biology, and synthetic biology would be interested. The work challenges existing paradigms about noise sources and offers a new predictive framework. It also has implications for understanding phenotypic heterogeneity in disease contexts, such as cancer and antibiotic persistence, making it relevant to a broader biomedical audience.
- **Major strengths**
  1.  The study uses a comprehensive, integrated approach with a large number of features, moving beyond single-feature analyses.
  2.  The finding that TF number and binding dynamics are better predictors than TATA box or nucleosome occupancy is a novel and important contribution.
  3.  The combination of statistical modeling with mechanistic stochastic simulations provides a strong framework for hypothesis generation.
  4.  The authors perform several robustness checks, including removal of duplicate genes and MCMC sampling of parameters.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor and causal inference
  - **Claim pointer** The claim that the "transcription factor binding process is the primary driver of noise" is presented as a causal mechanism, but the evidence is largely correlative.
  - **Evidence pointer** Results section "Molecular features associated with TF binding were the top predictors of noise", Figures 3 and 4.
  - **Concern** The analysis demonstrates that the number of TFs and related features are the best *predictors* of noise in a linear model. However, this does not establish that the TF binding *process* (i.e., the dynamic events of binding/unbinding) is the *driver*. Other features correlated with TF number, such as promoter complexity or regulatory network position, could be the underlying cause. The simulations are used to show that cooperative/competitive binding *can* generate noise, but this is a proof-of-principle, not a direct test of the model's predictions against the observed data. The manuscript does not show that the specific mechanisms modeled (cooperation/competition) are the ones operating in the high-noise genes identified in the analysis.
  - **Why it matters** The central thesis of the paper is a causal one. Without addressing the correlation-versus-causation gap, the conclusion overreaches the evidence. The paper would be more accurate if it claimed that TF binding-related features are the most predictive, and that simulations suggest a plausible mechanism.
  - **Resolution test** To resolve this, the authors could: (1) perform a mediation analysis to see if the effect of TF number on noise is mediated by the predicted dynamics (e.g., competition/cooperation scores); (2) use their model to make quantitative predictions about noise for specific genes and test these against experimental data (e.g., from a perturbation experiment where TF binding is altered); (3) explicitly test whether the relationship between TF number and noise holds after controlling for other correlated features like promoter length or number of cis-regulatory modules.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological transparency and validation
  - **Claim pointer** The claim that the integrated model can predict noise with a certain accuracy (R2 values).
  - **Evidence pointer** Results section "Molecular features associated with TF binding were the top predictors of noise", Figure 4.
  - **Concern** The manuscript reports R2 values for the full model and for individual features, but the methodology for model selection and validation is not fully described. It is unclear if the reported R2 values are from the training or test set. The process of feature selection using Ridge/Lasso followed by stepwise regression is prone to overfitting, and the manuscript does not describe how the final model was validated (e.g., cross-validation on the test set). The "predicted R2" is mentioned but its calculation is not detailed.
  - **Why it matters** The predictive power is a key selling point of the paper. If the reported values are optimistic due to overfitting or unclear validation, the conclusions about the relative importance of features are weakened.
  - **Resolution test** The authors should clearly describe the model building and validation process. They should report the R2 and predicted R2 for the final model on the held-out test set, and ideally show the results of a cross-validation procedure. They should also report the uncertainty (e.g., confidence intervals) around the R2 values for the top features.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological interpretation of simulations
  - **Claim pointer** The claim that "cooperative and competitive TF binding could generate high expression noise" and that this is the mechanism explaining the observed correlation.
  - **Evidence pointer** Results section "Cooperative and Competitive TF binding could generate high expression noise", Figures 6 and 7.
  - **Concern** The simulations are highly simplified. The model assumes a two-state promoter and uses Hill functions for cooperativity, but it does not incorporate other known sources of noise, such as chromatin remodeling dynamics, transcriptional interference, or cell cycle effects. The authors do not test whether the noise generated by their model quantitatively matches the noise distribution seen in the experimental data. The claim that the model explains the observed noise is therefore not directly validated.
  - **Why it matters** The simulations are used to provide a mechanistic explanation for the statistical findings. If the model is too simplistic or not validated against the data, the proposed mechanism remains speculative.
  - **Resolution test** The authors should attempt to fit their model to the noise data for specific genes, using the measured TF binding properties as parameters. They could also test the model's predictions by comparing the noise distribution of genes with predicted high competition/cooperation versus those with low. A more direct test would be to experimentally manipulate TF binding sites (e.g., create mutations that alter competition) and measure the effect on noise.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1A-1E
  - **Issue** The figure is dense and the relationship between the different panels (A-E) is not immediately clear from the legend. The description of how the "distance to median" (DM) measure is used and how it relates to the mRNA noise calculation could be clearer.
  - **Required correction** Consider splitting the figure or providing a more detailed legend that explicitly walks the reader through the workflow from raw data to the final noise measure.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results section "Molecular features associated with TF binding were the top predictors of noise"
  - **Evidence pointer** Figure 3C
  - **Issue** The manuscript states that the top 10 features are the same for mRNA and protein noise, but the rankings are different. The significance of the difference in ranking is not discussed.
  - **Required correction** A brief comment on the consistency of the feature set and the implications of the ranking differences would be helpful.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness of methods
  - **Affected element** Methods section "Analysis of transcription factor binding"
  - **Evidence pointer** Methods section
  - **Issue** The method for identifying overlapping TF binding sites is described, but the criteria for defining an "overlap" (e.g., minimum overlap length) are not specified.
  - **Required correction** Provide the specific parameters used for defining overlaps.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation of results
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section
  - **Issue** The discussion mentions that the model's performance is similar for mRNA and protein noise, but does not speculate on why this might be, given the different timescales and regulatory layers involved.
  - **Required correction** A brief discussion of this point would add depth to the interpretation.

## Technical failings that need to be addressed before the case is established
- R1-M1: The causal claim is not supported by the correlative analysis. The manuscript must either temper the conclusion or provide additional evidence for causality.
- R1-M2: The model validation process is not described with sufficient detail to assess the risk of overfitting and the reliability of the reported predictive power.

## Risk / unsupported claims
- The claim that the TF binding process is the "primary driver" of noise is not fully supported by the evidence, which is primarily correlative and based on simplified simulations.
- The claim that the model can predict noise with a certain accuracy is not verifiable without a detailed description of the validation methodology.
- The biological relevance of the simulation results to the observed data is not established, as the model is not quantitatively fitted to or tested against the experimental noise distributions.