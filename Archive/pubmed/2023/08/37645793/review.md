## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends (as provided).
- **Assessment boundary** Scientific validity, technical soundness, interpretation of results, and alignment with the stated claims. Editorial and stylistic issues are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors combine live imaging of the Sox2 promoter and its enhancer (SCR) with molecular dynamics simulations to show that transcription and loop extrusion have antagonistic effects on local chromatin dynamics. They report that active elements are more constrained than control loci, that enhancer mobility decreases upon transcriptional activation, and that deletion of CTCF sites or transcription factor binding sites has opposing effects on mobility. Simulations require competition between loop extrusion and transcription-linked communication to recapitulate the data.
- **Visible evidence base** Live imaging of ANCHOR-tagged loci, inter-probe distance measurements, 4C-seq, ChIP-qPCR, single-molecule RNA FISH, western blotting, and molecular dynamics simulations. Figures referenced: 1, 2, 3, 4, 5, 6, 7, S1–S9 (as cited in text). Tables S1–S7.
- **Missing materials affecting confidence** Raw imaging data, full statistical reporting (e.g., effect sizes, confidence intervals for all comparisons), details of the GPTool fitting procedure as applied here, and complete simulation parameter sweeps. Some figure panels are referenced but not fully described in the text provided.

## Reviewer
- **Overall assessment** This is a technically ambitious study that combines state-of-the-art live imaging with modeling to address a fundamental question in gene regulation. The central observation, that transcription and loop extrusion have opposing effects on local chromatin dynamics, is potentially important and would be of broad interest. However, the manuscript as presented has several technical and interpretive gaps that need to be addressed before the case is fully established. The link between the experimental perturbations and the inferred mechanistic competition is not always direct, and the simulations, while instructive, are not sufficiently constrained to be confirmatory. The work is likely to be of interest to the chromatin and transcription fields, but the current evidence base does not fully support all the strong claims made.
- **Who would be interested in the results, and why** Researchers studying 3D genome organization, enhancer-promoter communication, transcription dynamics, and the biophysical properties of chromatin. The combination of imaging and simulation provides a framework that could be adapted by others. The finding that CTCF and transcription factor binding sites have opposing effects on mobility is a novel observation that could influence how the field thinks about the interplay between architectural and regulatory proteins.
- **Major strengths**
  1. The use of the ANCHOR system to tag the endogenous Sox2 promoter and enhancer with minimal perturbation is a significant technical advance.
  2. The combination of live imaging with molecular dynamics simulations is a powerful approach that allows for direct comparison between experiment and theory.
  3. The study addresses a long-standing controversy about the relationship between promoter-enhancer proximity and transcription, providing data that reconcile some conflicting results.
  4. The observation that enhancer mobility specifically decreases upon transcriptional activation, while promoter mobility is relatively insensitive, is a novel and potentially important finding.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "deleting either CTCF or transcription factor binding sites induced opposing effects on localized chromatin mobility" and that this reflects a competition between loop extrusion and transcription-linked communication.
  - **Evidence pointer** Figures 6 and 7; text in Results section "Opposing effects of loop extrusion and promoter-enhancer communication on local chromatin mobility".
  - **Concern** The interpretation of the CTCF deletion experiments is not fully supported. The authors show that deletion of the CTCF site at the SCR increases mobility, but they do not directly demonstrate that this is due to altered loop extrusion. The effect could be due to changes in local protein binding, chromatin state, or other indirect effects. Similarly, the claim that transcription factor binding site deletions increase constraint is based on a small number of loci and the mechanism is speculative. The simulations are used to support the interpretation, but the model parameters are not systematically varied or validated against independent data.
  - **Why it matters** The central mechanistic claim of the paper rests on the interpretation of these perturbation experiments. If the effects are not directly attributable to loop extrusion versus transcription-linked communication, the main conclusion is weakened.
  - **Resolution test** The authors should provide additional evidence that the mobility changes are specifically due to altered loop extrusion. This could include: (1) measuring loop extrusion rates or processivity directly, (2) performing similar deletions at additional loci to show generality, (3) using a more specific inhibitor of loop extrusion (e.g., auxin-inducible degron of cohesin) in combination with the CTCF deletion, or (4) showing that the simulation predictions are robust to parameter variation and match additional experimental observables (e.g., contact frequency changes).
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that "active elements display more constrained mobility, consistent with confinement within specialized nuclear sites."
  - **Evidence pointer** Figure 3; text in Results section "Promoters and enhancers have more constrained chromatin motion than control sequences".
  - **Concern** The comparison of mobility between active elements (promoter, enhancer) and control regions is potentially confounded by differences in local chromatin environment, nuclear position, or the presence of bound proteins. The control regions are described as "non-regulatory" but are not matched for sequence content, GC content, or other features. The authors do not show that the mobility differences are specific to the transcriptional activity of the Sox2 locus, rather than a general property of these genomic regions.
  - **Why it matters** The claim that active elements are specifically constrained is a key observation. If the effect is not specific to activity, the interpretation is less clear.
  - **Resolution test** The authors should include additional control loci that are matched for genomic features but are not active. They could also perform the same measurements in a cell type where Sox2 is not expressed, to show that the constraint is activity-dependent. Alternatively, they could use a reporter system where the same locus can be toggled between active and inactive states.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor
  - **Claim pointer** The authors report differences in the anomalous exponent, α, between conditions (e.g., transcribing vs. non-transcribing alleles, wild-type vs. mutant).
  - **Evidence pointer** Figures 3, 4, 5, 6; Tables S1, S2.
  - **Concern** The statistical analysis of the α distributions is not fully described. The authors use Wilcoxon rank-sum tests, but it is unclear how many cells/alleles were analyzed per condition, whether the data are independent (e.g., multiple measurements from the same cell), and whether multiple testing corrections were applied consistently. The effect sizes are not reported, and it is difficult to assess the biological significance of the observed differences.
  - **Why it matters** The conclusions rely heavily on the statistical significance of small differences in α. Without proper reporting, it is difficult to evaluate the robustness of the findings.
  - **Resolution test** The authors should provide a detailed description of the sample sizes, the number of independent biological replicates, and the statistical methods used. They should report effect sizes and confidence intervals for all key comparisons. They should also consider using mixed-effects models to account for potential correlations between measurements from the same cell or embryo.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The molecular dynamics simulations are used to support the experimental findings and to make predictions about the competition between loop extrusion and transcription.
  - **Evidence pointer** Methods section "Molecular dynamics simulations"; Figures 7 and S8.
  - **Concern** The simulation model is complex and has many parameters. The authors do not provide a systematic sensitivity analysis, and it is unclear how robust the conclusions are to parameter choices. The model is calibrated to reproduce the experimental results, but it is not clear that it would make correct predictions for other perturbations or loci.
  - **Why it matters** The simulations are a key part of the paper's argument. If the model is not well-validated, the conclusions drawn from it are less convincing.
  - **Resolution test** The authors should provide a more detailed description of the model parameters and their rationale. They should perform a sensitivity analysis to show that the main conclusions are robust to reasonable parameter variations. They should also test the model's predictions against independent experimental data (e.g., the effect of cohesin depletion on mobility).
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, last sentence.
  - **Issue** The phrase "This provides an experimental framework for the underappreciated role of chromatin dynamics in genome regulation" is vague. It is not clear what specific framework is being provided or how it advances the field beyond the specific findings.
  - **Required correction** Rephrase to be more specific about what the framework is and how it can be used by others.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods, GPTool fitting
  - **Evidence pointer** Methods section "GP-FMM measurement of diffusive parameters".
  - **Issue** The description of the GPTool fitting procedure is brief. It is not clear how the model parameters are estimated, what priors are used, or how the model is validated.
  - **Required correction** Provide more detail on the fitting procedure, including the likelihood function, optimization algorithm, and any model comparison or validation steps.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of Figure 5
  - **Evidence pointer** Results section "The SCR has reduced chromatin dynamics on transcriptional firing".
  - **Issue** The authors state that the enhancer becomes "more constrained" upon transcriptional activation, but the difference in α is small (0.148 vs. 0.191). It is not clear if this difference is biologically meaningful.
  - **Required correction** Provide a more quantitative interpretation of the effect size, perhaps by relating the change in α to a physical model of confinement.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Figure legends
  - **Evidence pointer** Figures 1–7.
  - **Issue** The figure legends are not fully self-contained. Some panels are not described in sufficient detail, and the statistical tests used are not always specified.
  - **Required correction** Expand the figure legends to include a description of all panels, the number of replicates, and the statistical tests used.

## Risk / unsupported claims
- The claim that transcription and loop extrusion are "antagonistic processes" is supported by the simulations but not directly by the experimental data. The experiments show that perturbations have opposing effects, but the mechanistic link to a specific competition is inferred.
- The claim that the Sox2 promoter and enhancer are "frequently in relatively close proximity" is based on median distances that are below the diffraction limit. The authors acknowledge this limitation but do not provide a quantitative model to account for the resolution limit.
- The claim that the ANCHOR system has "negligible functional impact" is supported by control experiments, but the sensitivity of these controls is not fully established.
- The generalizability of the findings beyond the Sox2 locus is not demonstrated. The authors speculate that the principles may apply broadly, but no data are presented to support this.