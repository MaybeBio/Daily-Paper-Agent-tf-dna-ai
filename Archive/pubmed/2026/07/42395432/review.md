## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) and metadata. No supplementary figures, tables, or source data were provided.
- **Assessment boundary** Assessment is limited to the claims, methods, and results as described in the provided text. No independent verification of computational outputs or benchmarking data was possible.
- **Shared manuscript claim summary** The authors benchmark AlphaFold3 (AF3) on 115 nucleosome-containing structures deposited in the PDB after the AF3 training cutoff, finding that AF3 performs well on histone-driven interactions (PTM writers, readers, erasers) but poorly on DNA-driven interactions (transcription factors, chromatin remodelers). They introduce interactor-specific DockQ metrics and an ipSAE-based virtual screen to assess PTM recognition specificity.
- **Visible evidence base** Main text figures (Figures 1–6) are referenced but not provided. Methods section describes dataset curation, AF3/AF3X prediction parameters, DockQ scoring, and PTM screen protocols. Supplementary Table 1 and Supplementary Figures 1–5 are referenced but not provided.
- **Missing materials affecting confidence** All figures, supplementary tables, and supplementary figures are absent. The Zenodo data repository link is provided but was not accessed. This significantly limits the ability to verify quantitative claims, visual comparisons, and statistical analyses.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question: how well does AlphaFold3 perform on chromatin complexes? The authors identify a clear performance dichotomy between histone-driven and DNA-driven interactions, which is a useful and actionable finding. The introduction of interactor-specific DockQ metrics is a methodological contribution that could benefit the field. However, the manuscript as presented has several critical gaps. The absence of all figures and supplementary materials makes it impossible to evaluate the core evidence. The DockQoverall metric is shown to be misleading in some cases, yet the authors still rely on it for initial filtering. The ipSAE-based virtual screen is promising but the validation is incomplete, and the authors themselves note that AF3 cannot distinguish methylation states. The claim that AF3 "can faithfully recapitulate known post-translational modification recognition patterns" is only partially supported by the described results. The manuscript would benefit from a more rigorous statistical framework and a clearer discussion of the limitations of using DockQ for nucleic acid-containing complexes.
- **Who would be interested in the results, and why** Computational structural biologists using AF3 for complex prediction, chromatin biologists studying nucleosome recognition mechanisms, and developers of next-generation structure prediction tools. The interactor-specific metrics and the identified failure modes for DNA interactions will be directly useful for practitioners deciding when to trust AF3 predictions.
- **Major strengths** 1) Timely and relevant question with direct practical implications. 2) Systematic benchmark design with clear inclusion/exclusion criteria. 3) Introduction of interactor-specific DockQ metrics that address a known limitation of global scoring. 4) Demonstration of AF3's utility for PTM recognition prediction, with potential for virtual screening applications. 5) Clear and honest discussion of limitations, including the inability to model DNA unwrapping and dynamic nucleosome conformations.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence completeness
  - **Claim pointer** The manuscript claims systematic benchmarking of 115 nucleosome-containing structures with quantitative performance assessments (Figures 2, 3, 4).
  - **Evidence pointer** Figures 1–6, Supplementary Figures 1–5, Supplementary Table 1 (location not provided in the submitted text)
  - **Concern** All figures and supplementary materials are referenced but not provided. The core quantitative results, including ipTM distributions, DockQ score comparisons, structural overlays, and the ipSAE-based screen outcomes, are entirely inaccessible. Without these, the claims of performance differences between interaction types, the specific examples of correct and incorrect predictions, and the validation of the virtual screen cannot be assessed.
  - **Why it matters** The manuscript's conclusions rest entirely on the presented figures and supplementary data. A review cannot establish whether the benchmark was executed correctly, whether the performance dichotomy is statistically robust, or whether the visual comparisons support the stated interpretations.
  - **Resolution test** Provide all figures and supplementary materials, or a detailed summary of the quantitative data underlying each figure, in a revised submission.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validity
  - **Claim pointer** The authors state that DockQoverall "largely reflects the high accuracy of the predicted nucleosome structure rather than of the pose of the interactor on the nucleosome" and therefore introduce interactor-specific metrics.
  - **Evidence pointer** Results section "Interactor-Nucleosome DockQ score highlights AF3's strength in histone-driven interactions", Methods section "DockQ scoring, iRMSD, and Interactor-Nucleosome calculations"
  - **Concern** The authors identify a critical flaw in DockQoverall for nucleosome complexes, yet they still use DockQoverall as the primary filter for which models are analyzed (17 models excluded due to "severe prediction inaccuracies that prevented initial structural alignment"). This creates a selection bias: models that fail to align are excluded, potentially removing the most challenging cases. The manuscript does not describe how this exclusion affects the reported performance statistics.
  - **Why it matters** If the excluded models are disproportionately DNA-driven interactions, the reported performance gap between histone-driven and DNA-driven interactions could be artificially inflated. The manuscript needs to address this selection bias explicitly.
  - **Resolution test** Report the number and identity of excluded models by interaction class, and re-analyze the data with a more inclusive alignment strategy or a sensitivity analysis.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Claim support
  - **Claim pointer** The authors claim that "AF3 can accurately predict the binding orientation of histone PTM writers and readers" and that it "can faithfully recapitulate known post-translational modification recognition patterns, matching experimentally determined specificity profiles."
  - **Evidence pointer** Results sections "AF3 can accurately predict the binding orientation of histone PTM writers and readers" and "Histone methyl-lysine specificity can be predicted by AF3", Figure 5, Figure 6
  - **Concern** The evidence for accurate PTM recognition is based on a small number of examples (Eaf3, UbcH5C-RNF168, SUV420H1, DNMT3APWWP, BPTFPWWP). The virtual screen results show that AF3 can rank cognate modifications above non-cognate ones, but the authors acknowledge that AF3 cannot distinguish between methylation states (e.g., me1 vs me2 vs me3). This is a significant limitation for a tool intended to predict PTM specificity, as methylation state is often biologically critical. The claim of "faithfully recapitulating" specificity patterns is therefore overstated.
  - **Why it matters** The virtual screen is presented as a key application of AF3. If the method cannot distinguish methylation states, its practical utility for predicting PTM readout is substantially reduced. The manuscript should temper this claim and discuss the implications of this limitation.
  - **Resolution test** Provide a more nuanced discussion of the methylation state limitation, and ideally include additional examples or a statistical analysis of screen performance across a larger panel of readers and modifications.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors use ipSAE with a 10 Å distance cutoff and 10 Å PAE cutoff for scoring virtual screen predictions.
  - **Evidence pointer** Methods section "Post Translational Modification (PTM) screen"
  - **Concern** The choice of ipSAE cutoffs (10 Å distance, 10 Å PAE) is stated but not justified. The manuscript does not describe how sensitive the results are to these parameters, nor whether the cutoffs were optimized on the test set (which would introduce circularity). The ipSAE metric is relatively new, and its behavior on nucleosome complexes with flexible histone tails is not well characterized.
  - **Why it matters** If the cutoffs are not robust, the ranking of predictions in the virtual screen could be an artifact of parameter choice. The manuscript needs to demonstrate that the results are stable across reasonable parameter ranges.
  - **Resolution test** Provide a sensitivity analysis of ipSAE cutoffs, or justify the chosen values based on prior benchmarks with clear reasoning.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The abstract states that AF3 "now incorporates the capability to model complexes containing nucleic acids and chemically modified side chains." This is accurate but could be more specific about the types of modifications supported (e.g., which PTMs are natively supported vs. requiring workarounds).
  - **Required correction** Consider specifying which PTMs are natively supported by AF3, or noting that some modifications required substitution or deletion (as described in the Methods).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, "AlphaFold3 and AlphaFold3x prediction parameters"
  - **Evidence pointer** Methods section, paragraph on prediction parameters
  - **Issue** The manuscript states that predictions were performed with "random seed numbers" but does not specify how many seeds were used or whether results were averaged across seeds. AF3 can produce variable outputs depending on the random seed.
  - **Required correction** Specify the number of seeds used and whether the reported metrics are from a single seed or averaged. If a single seed was used, acknowledge this as a limitation.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, "Interactor-Nucleosome DockQ score highlights AF3's strength in histone-driven interactions"
  - **Evidence pointer** Results section, Figure 3C
  - **Issue** The manuscript reports percentages of models scoring in "Medium" or better ranges for different interaction classes (e.g., 61.9% for writers, 10.0% for remodelers, 16.7% for transcription factors) but does not report confidence intervals or statistical tests for these differences.
  - **Required correction** Add statistical comparisons (e.g., Fisher's exact test) or confidence intervals to support the claim of a performance dichotomy.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Discussion
  - **Evidence pointer** Discussion, final paragraph
  - **Issue** The discussion mentions that AF3's limitations in modeling DNA interactions "reflect a broader challenge in structure prediction" and cites a recent benchmark. However, the manuscript does not discuss whether alternative tools (e.g., RoseTTAFold All-Atom, or specialized DNA-protein docking methods) perform better on these specific cases.
  - **Required correction** Add a brief comparison to alternative methods, or explicitly state that such a comparison is outside the scope of this work.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data Availability statement
  - **Evidence pointer** Data Availability section
  - **Issue** The data availability statement provides a Zenodo link but does not specify the license or the exact contents of the deposit. It is also unclear whether the AF3/AF3X prediction files include all input parameters and intermediate outputs.
  - **Required correction** Clarify the contents of the Zenodo deposit and specify a license. Consider including a README file describing the directory structure and file formats.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing figures and supplementary data) and R1-M2 (selection bias in DockQ-based filtering) are the most critical. R1-M3 (overstated PTM specificity claims) and R1-M4 (unjustified ipSAE cutoffs) also need to be addressed. Without access to the figures and data, the core claims cannot be verified.
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The application of AF3 to chromatin complexes is novel, and the interactor-specific metrics are a useful contribution. However, the finding that protein-DNA interactions are poorly predicted is consistent with prior benchmarks and is not entirely unexpected.  
  *Scientific importance*: High for the chromatin biology and structural prediction communities. The identified performance dichotomy has direct practical implications for researchers using AF3 to model nucleosome complexes.  
  *Interdisciplinary readership*: Moderate. The manuscript will appeal to structural biologists, chromatin biologists, and computational biologists. The writing is accessible but assumes familiarity with AF3 and DockQ.  
  *Technical soundness*: Currently not fully assessable due to missing figures and data. The methodological concerns about selection bias and ipSAE cutoffs need to be resolved.  
  *Readability for nonspecialists*: Good. The manuscript is clearly written, and the key concepts are explained well. The equations are straightforward, and the figures (as described) would likely aid comprehension.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question and introduces useful metrics, but the missing evidence and methodological issues must be addressed before the claims can be fully evaluated. The authors should provide all figures and supplementary data, address the selection bias in DockQ-based filtering, temper the PTM specificity claims, and justify the ipSAE cutoffs.

## Risk / unsupported claims
- The claim that AF3 "can faithfully recapitulate known post-translational modification recognition patterns, matching experimentally determined specificity profiles" is only partially supported, as the authors acknowledge AF3 cannot distinguish methylation states.
- The claim that AF3 performs well on histone-driven interactions is based on a small number of examples and lacks statistical validation.
- The claim that DockQoverall is misleading for nucleosome complexes is plausible but not quantitatively demonstrated in the provided text.
- The performance of the ipSAE-based virtual screen is presented without a clear benchmark against alternative scoring methods or a null model.
- The exclusion of 17 models due to alignment failures is not analyzed for potential bias.
- The generalizability of the findings beyond the 115 curated structures is not discussed.