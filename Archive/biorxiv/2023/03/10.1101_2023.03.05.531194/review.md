## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends, supplemental figure descriptions) as provided in the submission.
- **Assessment boundary** Scientific content, methodological soundness, logical coherence, and support of claims by the presented evidence. No assessment of formatting, grammar, or editorial style beyond readability for a general scientific audience.
- **Shared manuscript claim summary** The authors propose that the context-dependent activity of CRX binding sites in rod photoreceptors is explained by a balance between positive additive contributions of individual TFBSs, positive heterotypic interactions between different TFs, and negative homotypic interactions between sites for the same TF. They support this with neural network models (MAVE-NN) fitted to synthetic CRE MPRA data.
- **Visible evidence base** Main text figures 1-4 (described in text), supplemental figures S1-S3 (described in text), methods sections for model fitting, library design, cloning, electroporation, and data processing. No raw data, code, or supplementary tables were provided in the submission.
- **Missing materials affecting confidence** Raw MPRA data, model parameter tables, detailed figure panels, supplemental tables, and the actual code repository contents were not included. The manuscript references prior work [13, 18] for key datasets, but those data are not directly assessable here.

## Reviewer
- **Overall assessment** The manuscript presents a coherent and potentially important model for how CRX binding sites can act as either activators or silencers depending on sequence context. The use of MAVE-NN to deconvolve additive and interaction effects from synthetic CRE data is appropriate and well-motivated. The central claim, that negative homotypic interactions between CRX sites drive silencing while positive heterotypic interactions or additive contributions from diverse TFBSs can overcome this, is plausible and consistent with the described data. However, the evidence as presented is incomplete. The manuscript relies heavily on model fitting to previously published data, and the current submission does not provide sufficient detail on model parameters, validation statistics, or the raw data to fully assess the robustness of the conclusions. The link between the synthetic CRE models and genomic enhancer/silencer observations is correlative and would benefit from direct experimental validation.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, cis-regulatory element function, enhancer/silencer logic, and computational modeling of gene expression. The work is also relevant to those interested in retinal biology and photoreceptor gene regulation. The proposed framework of balancing additive and interaction effects may generalize to other TFs and cell types.
- **Major strengths** The study addresses a fundamental and unresolved question in gene regulation, namely how the same TF can activate or repress depending on context. The use of synthetic CRE libraries with systematic variation is a powerful approach. The MAVE-NN framework is well-suited to separate additive and interaction effects. The finding that homotypic interactions are negative and scale quadratically while additive effects scale linearly provides a simple and elegant explanation for non-monotonic activity. The model successfully recapitulates known patterns in genomic data.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of model fitting and validation
  - **Claim pointer** The claim that the pairwise interaction model accurately captures the cis-regulatory grammar of CRX and NRL sites, and that its parameters (additive and interaction terms) are reliable.
  - **Evidence pointer** Results section "Positive heterotypic and negative homotypic interactions explain the effects of CRX and NRL sites on expression", Figures 2A-D, Methods "Model fitting".
  - **Concern** The manuscript reports predictive information values and R² values for model performance, but does not provide sufficient detail on the uncertainty of the model parameters. The additive and interaction terms are presented as averages (Fig. 2D), but no confidence intervals or error bars are shown. Given that the central conclusion rests on the sign and magnitude of these terms, it is critical to know whether the negative homotypic interactions and positive heterotypic interactions are statistically distinguishable from zero. The manuscript also does not report how many model parameters were fitted, whether regularization was used, or how sensitive the conclusions are to the choice of hyperparameters (Table 1 is referenced but not provided).
  - **Why it matters** Without parameter uncertainty estimates, the reader cannot assess whether the proposed grammar is robustly supported by the data or could be an artifact of overfitting or model misspecification. The claim that negative homotypic interactions cause silencing is a strong claim that requires statistical support.
  - **Resolution test** Provide confidence intervals or posterior distributions for the additive and interaction parameters. Report the number of parameters, regularization scheme, and a sensitivity analysis showing that the qualitative conclusions (sign of interaction terms) are stable across reasonable hyperparameter choices. Show that the model predictions are significantly better than simpler alternatives (e.g., additive-only model) using a formal statistical test.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Support for the link between synthetic models and genomic observations
  - **Claim pointer** The claim that the model "explains observed patterns of activity among genomic CRX-bound enhancers and silencers" and that "enhancers may require diverse TFBSs to overcome negative homotypic interactions."
  - **Evidence pointer** Discussion section, Results section "Additional retinal TFs contribute independently to CRE activity", reference to prior work [18].
  - **Concern** The manuscript states that genomic CRX-bound enhancers have more diverse TFBSs than silencers, and that this is consistent with the model. However, no direct comparison between model predictions and genomic data is presented in this manuscript. The argument is qualitative and relies on previously published observations. The model predicts specific quantitative relationships (e.g., activity as a function of TFBS number and identity), but these are not tested against genomic enhancer/silencer activity data. The claim that the model "explains" the genomic patterns is therefore not fully supported by the evidence presented here.
  - **Why it matters** The broader significance of the work depends on whether the synthetic CRE model can predict or explain endogenous regulatory element behavior. Without a direct quantitative test, the relevance to genomic regulation remains speculative.
  - **Resolution test** Perform a direct comparison between model predictions and genomic MPRA data (e.g., from [18]). For example, predict the activity of genomic CRX-bound sequences based on their TFBS composition and compare to measured activity. Alternatively, use the model to make specific predictions about how mutating TFBSs in genomic enhancers/silencers would alter activity, and test these predictions experimentally.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of the model beyond the tested TF pairs
  - **Claim pointer** The claim that the balance between positive additive, positive heterotypic, and negative homotypic interactions is a general principle of cis-regulatory grammar, applicable to other TFs and cell types.
  - **Evidence pointer** Discussion section, final paragraph.
  - **Concern** The model is fitted to data from only two TFs (CRX and NRL) in one library, and five TFs (CRX, NRL, NEUROD1, RORB, MAZ) in a second library. The claim of generality is extrapolated from these limited cases. The manuscript does not test whether the same framework applies to other TF families or other cellular contexts. The negative homotypic interaction is proposed as a general phenomenon, but the mechanism (e.g., squelching, cooperative DNA binding, nucleosome competition) is not investigated.
  - **Why it matters** The significance of the work for a broad audience depends on whether the proposed grammar is a general feature of gene regulation or specific to photoreceptor TFs. Overgeneralization without evidence could mislead future studies.
  - **Resolution test** Discuss the limitations of the current scope explicitly. If possible, apply the same modeling framework to published MPRA datasets from other TFs or cell types to test whether similar patterns of homotypic and heterotypic interactions emerge. Alternatively, temper the claims of generality and frame the model as a hypothesis to be tested in other systems.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of model description
  - **Affected element** Methods "Model fitting"
  - **Evidence pointer** Methods section, Table 1 (not provided).
  - **Issue** The description of the model architecture is brief. The manuscript states that "additive models with or without interaction terms" were trained, but does not specify the exact functional form of the pairwise interaction model. For example, are interaction terms parameterized as a single coefficient per TF pair, or do they depend on position or orientation? The encoding of TFBSs as single letters and the use of dummy sites "O" is described, but the reader cannot fully reconstruct the model input.
  - **Required correction** Provide a complete mathematical description of the model, including the equation relating sequence to latent phenotype, the definition of all parameters, and the encoding scheme. Include the hyperparameter table (Table 1) in the main text or supplement.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Interpretation of the simplified model
  - **Affected element** Results section "Balance between positive and negative interactions can explain context-dependent effects of binding sites for transcriptional activators", Figure 4.
  - **Evidence pointer** Results section, Figure 4A-B.
  - **Issue** The simplified model in Figure 4 sets all weights (α, β, γ) equal to 1. This is acknowledged as a simplifying assumption, but the sensitivity of the conclusions to these weights is not explored. For example, if the negative homotypic interaction weight γ were much larger than the additive weight α, the model would predict silencing at lower TFBS numbers. The qualitative conclusions (e.g., non-monotonic activity) may hold for a range of weights, but this is not shown.
  - **Required correction** Show that the qualitative behavior of the simplified model (e.g., non-monotonic activity, conversion of silencer to enhancer by adding a heterotypic site) is robust to a range of weight values. A simple parameter sweep would suffice.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical treatment of replicates
  - **Affected element** Methods "MPRA data processing"
  - **Evidence pointer** Methods section.
  - **Issue** The manuscript states that three replicate electroporations were performed and that MPRA activity scores were averaged across replicates. However, no measure of inter-replicate variability is reported. It is unclear whether the observed differences in activity between CREs are large compared to the noise between replicates.
  - **Required correction** Report the standard deviation or coefficient of variation across replicates for a subset of CREs, or provide a scatter plot of replicate 1 vs replicate 2 to demonstrate reproducibility.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction, first paragraph
  - **Evidence pointer** Introduction.
  - **Issue** The introduction assumes familiarity with terms such as "enhanceosome model" and "billboard model" without defining them. A brief explanation of these competing models of cis-regulatory grammar would help nonspecialist readers understand the conceptual framework.
  - **Required correction** Add one or two sentences defining the enhanceosome and billboard models and their key differences.

## Technical failings that need to be addressed before the case is established
- R1-M1: Lack of parameter uncertainty estimates and model validation details.
- R1-M2: No direct quantitative link between the synthetic model and genomic enhancer/silencer data.
- R1-M3: Overgeneralization of the model beyond the tested TF pairs without supporting evidence.

## Risk / unsupported claims
- The claim that the model "explains" genomic enhancer/silencer patterns is not directly supported by evidence in this manuscript; it is inferred from prior correlative observations.
- The claim that negative homotypic interactions are a general feature of transcriptional activators is extrapolated from a limited set of TFs and is not mechanistically investigated.
- The statement that "the pairwise model captured a substantial fraction of the variation in reporter activity (R² = 0.889)" is presented without error bars or a comparison to the null model, making it difficult to judge the practical significance of the unexplained variance.
- The claim that "the effects are likely due to multivalent interactions that involve co-factors" is speculative and not tested.

## Assessment against Nature-style criteria
- **Originality** The work addresses a long-standing question in gene regulation with a novel combination of synthetic library design and interpretable neural network modeling. The specific finding of negative homotypic interactions as a driver of silencing is a new contribution. However, the general concept of context-dependent TF activity is well established, and the novelty lies in the specific quantitative framework.
- **Scientific importance** The question of how TF binding sites function in context is of broad importance to understanding gene regulation, disease variants, and synthetic biology. The proposed framework could have implications for predicting the effects of regulatory variants. The importance is high if the model generalizes beyond the tested TFs.
- **Interdisciplinary readership** The work is primarily of interest to molecular biologists, computational biologists, and researchers in gene regulation. The use of neural networks may attract computational readers, but the biological focus may limit appeal to a broader physical or chemical science audience. The topic is not of immediate interest to researchers outside the life sciences.
- **Technical soundness** The experimental design (synthetic libraries, MPRA) is sound. The modeling approach is appropriate, but the lack of statistical detail on parameter estimates and model validation is a significant weakness. The simplified model in Figure 4 is illustrative but not rigorously tested. The link to genomic data is qualitative.
- **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear. However, the introduction assumes familiarity with specific models of cis-regulatory grammar, and the methods section is dense. The abstract is accessible. The main text would benefit from a brief explanation of the competing models and a more explicit statement of the model equation.

## Recommendation posture
**Supportive if technical concerns are resolved.** The core idea is interesting and the experimental approach is appropriate. However, the manuscript as presented does not fully establish the case due to the lack of statistical rigor in the model fitting and the absence of a direct quantitative link to genomic data. Addressing R1-M1 and R1-M2 would substantially strengthen the claims. The overgeneralization in R1-M3 should be tempered or supported with additional data.