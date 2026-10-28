## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv 2023.04.25.538222)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No external data or supplementary files were assessed beyond what is described.
- **Shared manuscript claim summary** The authors combine live imaging of the Sox2 promoter and its enhancer (SCR) with molecular dynamics simulations to show that (1) promoter-enhancer proximity is maintained independent of transcription, (2) active elements are more constrained in mobility than neutral loci, (3) transcriptional inhibition reduces promoter mobility, (4) the enhancer becomes more constrained upon transcriptional activation, and (5) CTCF-mediated loop extrusion and transcription-factor-mediated clustering have opposing effects on local chromatin dynamics.
- **Visible evidence base** Live imaging of parS/ANCHOR-tagged loci, 3D DNA FISH, allele-specific 4C-seq, ChIP-qPCR (CTCF, Rad21), qRT-PCR, single-molecule RNA FISH, western blotting, molecular dynamics simulations (EspressoMD), GPTool-based diffusion analysis, MSD analysis.
- **Missing materials affecting confidence** Supplementary figures and tables (Fig S1–S9, Tables S1–S7) are referenced but not provided. Detailed statistical outputs, exact sample sizes per condition, and full simulation parameter sweeps are not fully described in the main text. Raw imaging data and code availability are not stated.

## Reviewer
- **Overall assessment** This is a technically ambitious and largely well-executed study that addresses a fundamental question in gene regulation: how transcription and loop extrusion jointly shape the dynamics of promoters and enhancers. The combination of high-resolution live imaging with perturbation experiments and simulations is commendable and provides a valuable resource for the field. The key claims are generally supported by the data presented, though several important technical details and potential confounders require clarification. The finding that loop extrusion and transcription-factor-mediated clustering have opposing effects on chromatin mobility is novel and conceptually important, but the mechanistic interpretation would benefit from stronger direct evidence. Overall, this is a strong manuscript that could be suitable for a high-impact journal after revision.

- **Who would be interested in the results, and why** Researchers in the fields of 3D genome organization, transcriptional regulation, chromatin dynamics, and biophysics of gene expression. The study is also relevant to those interested in the mechanisms of enhancer-promoter communication and the role of phase-separated condensates in transcription. The methodological framework (ANCHOR/parS labeling, GPTool analysis, simulations) will be of interest to specialists in live-cell imaging and polymer modeling.

- **Major strengths**
  1. The use of the ANCHOR/parS system to label endogenous loci with minimal perturbation is a significant technical advance, allowing direct visualization of promoter and enhancer dynamics in living cells.
  2. The combination of experimental perturbations (genetic deletions, pharmacological inhibition, differentiation) with molecular dynamics simulations provides a multi-pronged approach to dissect the contributions of transcription and loop extrusion.
  3. The finding that promoter-enhancer proximity is maintained independent of transcription, and that the enhancer specifically becomes more constrained upon transcriptional activation, is a novel and important observation.
  4. The demonstration of opposing effects of CTCF-mediated loop extrusion and transcription-factor-mediated clustering on local chromatin mobility is conceptually interesting and challenges simple models of enhancer-promoter communication.
  5. The careful attention to substrate motion correction and the use of GPTool for single-trajectory analysis is methodologically rigorous.

- **Major Concerns**
  - **R1-M1** (Severity: Major, Blocking: No, Axis: Technical soundness)
  - **R1-M2** (Severity: Major, Blocking: No, Axis: Technical soundness)
  - **R1-M3** (Severity: Major, Blocking: No, Axis: Interpretation / claim support)
  - **R1-M4** (Severity: Major, Blocking: No, Axis: Technical soundness)
  - **R1-M5** (Severity: Major, Blocking: No, Axis: Interpretation / claim support)

- **Minor Comments**
  - **R1-m1** (Severity: Minor, Axis: Clarity, Affected element: Abstract/Summary)
  - **R1-m2** (Severity: Minor, Axis: Statistical reporting, Affected element: Figure legends)
  - **R1-m3** (Severity: Minor, Axis: Reproducibility, Affected element: Methods)
  - **R1-m4** (Severity: Minor, Axis: Interpretation, Affected element: Discussion)
  - **R1-m5** (Severity: Minor, Axis: Clarity, Affected element: Introduction)

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M4

- **Assessment against Nature-style criteria**
  - **Originality**: High. The study introduces a novel experimental system and provides new insights into the relationship between transcription, loop extrusion, and chromatin dynamics. The finding of opposing effects of these processes is original.
  - **Scientific importance**: High. The question of how enhancers and promoters communicate in space and time is central to gene regulation. The results have implications for understanding transcriptional control in development and disease.
  - **Interdisciplinary readership**: Moderate to high. The study bridges cell biology, biophysics, and computational modeling. The findings will be of interest to a broad audience, though the technical complexity may limit accessibility to non-specialists.
  - **Technical soundness**: Generally sound, but several concerns (see R1-M1, R1-M2, R1-M4) need to be addressed to fully establish the claims. The imaging and analysis methods are state-of-the-art, but the interpretation of some results relies on assumptions that need clarification.
  - **Readability for nonspecialists**: The manuscript is well-written and the logic is clear, but the Methods section is dense and may be challenging for readers without a background in biophysics or imaging. The main text does a good job of explaining the concepts.

- **Recommendation posture** Supportive if technical concerns are resolved. The study is potentially important and the data are largely convincing, but the identified technical issues and interpretive ambiguities must be addressed before the claims can be fully accepted.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the ANCHOR/parS system has "negligible functional impact" on the loci being visualized, based on allele-specific qRT-PCR, 4C-seq, and imaging controls.
- **Evidence pointer** Results section "Enhancer-promoter proximity is frequently maintained at the Sox2 locus independent of transcription", Figure 1c,d; Methods section "Cell lines and culture"
- **Concern** The validation of the ANCHOR/parS system relies on a limited set of assays (qRT-PCR, 4C-seq, cell cycle analysis). It is not clear whether the binding of ParB proteins to the parS sites could affect local chromatin structure or dynamics in ways not captured by these assays. For instance, the authors do not show that ParB binding does not alter nucleosome positioning or local histone modifications. Additionally, the comparison of Sox2 expression between the tagged and untagged alleles is only shown for the population average, not at the single-cell level, which could mask allele-specific effects.
- **Why it matters** The entire study relies on the assumption that the labeling system does not perturb the very processes being measured. If the ANCHOR/parS system subtly alters chromatin dynamics or transcription, the conclusions could be compromised.
- **Resolution test** Provide additional validation, such as comparing chromatin dynamics at the tagged locus to an untagged locus using an independent method (e.g., a different labeling system or FISH-based tracking). Show single-cell, allele-specific expression data to rule out cis-effects of the tags. Demonstrate that ParB binding does not affect local chromatin compaction or histone modifications.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors use GPTool to extract diffusion parameters (Dα, α) from single trajectories and compare these across conditions. They claim that the substrate-corrected apparent anomalous exponent (αapp) is a reliable measure of chromatin constraint.
- **Evidence pointer** Methods section "GP-FBM measurement of diffusive parameters"; Results section "Promoters and enhancers have more constrained chromatin motion than control sequences", Figure 3c
- **Concern** The GPTool analysis assumes a fractional Brownian motion (FBM) model, but the authors acknowledge that the experimental MSD curves are non-linear on log-log scales, suggesting multiple regimes. The correction for substrate motion relies on cross-correlations of co-measured trajectories, which may not fully account for complex nuclear movements. The authors do not provide a detailed validation of GPTool's performance on their specific data, such as the accuracy of parameter recovery from simulated trajectories with known parameters, or the sensitivity of the results to the choice of fitting window.
- **Why it matters** The central conclusions about differential mobility between active and neutral loci, and changes upon perturbation, depend on the accuracy and robustness of the GPTool parameter estimates. If the model is misspecified or the fitting is sensitive to noise, the reported differences could be artifacts.
- **Resolution test** Provide a detailed validation of GPTool on simulated trajectories that mimic the experimental conditions (including substrate motion, noise, and finite trajectory length). Show that the inferred parameters are unbiased and that the reported differences between conditions are robust to variations in the fitting procedure (e.g., different time windows, different priors).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation / claim support
- **Claim pointer** The authors conclude that "alterations in chromatin mobility, not promoter-enhancer distance, is more informative about transcriptional status" and that "active elements display more constrained mobility, consistent with confinement within specialized nuclear sites."
- **Evidence pointer** Results section "Enhancer-promoter proximity is frequently maintained at the Sox2 locus independent of transcription", Figure 2; Results section "Promoters and enhancers have more constrained chromatin motion than control sequences", Figure 3
- **Concern** The claim that mobility is "more informative" than distance is based on a comparison of median distances and αapp values across conditions. However, the statistical power of these comparisons is not fully reported. The authors do not provide effect sizes or confidence intervals for the key comparisons. Moreover, the interpretation of reduced mobility as "confinement within specialized nuclear sites" is speculative and not directly tested. The authors do not measure the size or nature of these putative sites, nor do they rule out other explanations for reduced mobility, such as increased chromatin compaction or tethering to the nuclear periphery.
- **Why it matters** The central thesis of the paper is that mobility, not distance, is the key parameter. This claim needs to be supported by robust statistical evidence and a more direct test of the "confinement" hypothesis.
- **Resolution test** Provide a more detailed statistical analysis, including effect sizes and confidence intervals for all key comparisons. Consider alternative explanations for reduced mobility and design experiments to distinguish them (e.g., measuring the volume of the confinement zone, or testing whether the reduced mobility is dependent on the nuclear lamina or other structural elements).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors use molecular dynamics simulations to model the Sox2 locus and claim that the simulations "recapitulate these experimental findings only when competition between loop extrusion and transcription-linked enhancer-promoter communication was reinforced."
- **Evidence pointer** Results section "Opposing effects of loop extrusion and promoter-enhancer communication on local chromatin mobility", Figure 7a,b; Methods section "Molecular dynamics simulations"
- **Concern** The simulation model is complex and involves many parameters (e.g., binding affinities, extrusion speeds, transcription rates, competition strengths). The authors state that they explored different rates of PolII-enhancer bond dissociation, but they do not provide a systematic parameter sweep or sensitivity analysis. It is unclear how robust the simulation results are to parameter choices, and whether the "competition" mechanism is uniquely identified or if other parameter combinations could also fit the data.
- **Why it matters** The simulations are used to support the mechanistic interpretation of the experimental results. If the model is overparameterized or the conclusions are sensitive to specific parameter choices, the interpretive value is limited.
- **Resolution test** Provide a more thorough parameter sensitivity analysis, showing how the simulation outcomes (e.g., mobility, contact frequency) depend on key parameters. Test alternative models (e.g., without competition, or with different interaction mechanisms) and show that they do not recapitulate the experimental findings.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation / claim support
- **Claim pointer** The authors state that "deleting either CTCF or transcription factor binding sites induced opposing effects on localized chromatin mobility" and interpret this as evidence for antagonism between loop extrusion and transcription-factor-mediated clustering.
- **Evidence pointer** Results section "Opposing effects of loop extrusion and promoter-enhancer communication on local chromatin mobility", Figure 6b–e
- **Concern** The interpretation of opposing effects is based on comparing αapp at the promoter and enhancer in different deletion lines. However, the deletions are not directly comparable: deleting CTCF sites removes a structural element, while deleting transcription factor binding sites removes regulatory elements. These perturbations may have different indirect effects (e.g., on gene expression, chromatin state, or nuclear positioning) that could confound the interpretation. The authors do not fully control for these potential confounders.
- **Why it matters** The claim of antagonism is a key conceptual advance. If the opposing effects are due to indirect or confounding factors, the conclusion would be weakened.
- **Resolution test** Perform additional control experiments, such as deleting a neutral region of similar size, or measuring other parameters (e.g., histone modifications, nuclear positioning) to rule out indirect effects. Consider using a more targeted perturbation, such as acute degradation of CTCF or transcription factors, to minimize compensatory changes.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract/Summary
- **Evidence pointer** Summary section
- **Issue** The summary states that "alterations in chromatin mobility, not promoter-enhancer distance, is more informative about transcriptional status." This is a strong claim that is not fully supported by the data, as the authors themselves note that distance and mobility are correlated. The phrasing could be softened to "more informative" to "differentially informative" or "provides complementary information."
- **Required correction** Revise the summary to more accurately reflect the findings, e.g., "alterations in chromatin mobility provide additional information about transcriptional status beyond promoter-enhancer distance."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure legends
- **Evidence pointer** Figures 3, 4, 6
- **Issue** The figure legends do not consistently report the number of biological replicates, the number of cells/trajectories analyzed, or the statistical tests used for each comparison. This makes it difficult to assess the robustness of the findings.
- **Required correction** Add detailed statistical information to each figure legend, including sample sizes, statistical tests, and p-values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "Molecular dynamics simulations"
- **Issue** The simulation parameters are described in the text, but the specific values for many parameters (e.g., binding energies, extrusion speeds, PolII processivity) are not given in a table or a dedicated section. This makes it difficult for others to reproduce the simulations.
- **Required correction** Provide a table of all simulation parameters and their values, and consider depositing the simulation code in a public repository.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the "hierarchy" of nucleating transcription-competent microenvironments is interesting but speculative. The authors do not provide direct evidence for such a hierarchy, and the concept is not well-defined.
- **Required correction** Either provide more concrete predictions or experimental tests for the hierarchy concept, or temper the speculation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction section
- **Issue** The introduction is dense and covers a lot of ground, but the transition from the general question of enhancer-promoter communication to the specific focus on Sox2 could be smoother. The rationale for choosing Sox2 as a model system is not explicitly stated.
- **Required correction** Add a sentence or two explaining why Sox2 is a good model system for this study (e.g., well-characterized enhancer, importance in pluripotency, previous conflicting data).

## Risk / unsupported claims
- The claim that "alterations in chromatin mobility, not promoter-enhancer distance, is more informative about transcriptional status" is not fully supported by the statistical analysis presented.
- The interpretation of reduced mobility as "confinement within specialized nuclear sites" is speculative and not directly tested.
- The claim that simulations "recapitulate these experimental findings only when competition between loop extrusion and transcription-linked enhancer-promoter communication was reinforced" is not supported by a systematic parameter sensitivity analysis.
- The conclusion that CTCF and transcription factor binding sites have "opposing effects" on chromatin mobility is based on comparisons that may be confounded by indirect effects of the deletions.
- The statement that the ANCHOR/parS system has "negligible functional impact" is not fully validated, as the assays used may not capture all potential perturbations.