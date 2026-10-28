## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure references
- **Assessment boundary** Scientific validity, technical soundness, conceptual framing, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors measure DNA binding kinetics of RBPJ and mutants via live-cell single-molecule tracking, combine with ChIP-Seq and reporter assays, and propose an "effective in vivo binding energy landscape" to illustrate that TF-DNA binding is kinetically rather than thermodynamically stable
- **Visible evidence base** Abstract, full results narrative, methods descriptions, figure references (Figures 1-4), supplementary figure references, supplementary tables referenced
- **Missing materials affecting confidence** Actual figure panels, numerical data tables, supplementary figures, ChIP-Seq quality metrics, single-molecule tracking raw statistics, and statistical analysis details are not provided in the supplied text

## Reviewer
- **Overall assessment** The manuscript addresses a significant question in transcription factor biology: how binding kinetics and cofactor interactions determine target site specificity and stability in vivo. The combination of single-molecule tracking, ChIP-Seq, and reporter assays is powerful and appropriate. The central claim that RBPJ-DNA binding is kinetically rather than thermodynamically stable is interesting and potentially important. However, the manuscript as presented has several technical and conceptual issues that need to be resolved. The "effective in vivo binding energy landscape" is a useful visualization concept, but its derivation relies on several assumptions and unmeasured parameters that are not fully justified. The claim of generality across TFs is based on reanalysis of published data with limited detail. The K195E disease-related findings are clinically relevant but the mechanistic interpretation requires stronger support. Overall, the work is promising but the case is not fully established from the provided material.
- **Who would be interested in the results, and why** Researchers in transcription regulation, Notch signaling, single-molecule biophysics, and quantitative cell biology would be interested. The conceptual framework of kinetic versus thermodynamic stability of TF-DNA binding could influence how the field thinks about TF target search and occupancy. The disease relevance to Adams-Oliver Syndrome adds translational interest for clinical geneticists.
- **Major strengths** 1) The combination of complementary methods (single-molecule tracking, ChIP-Seq, reporter assays) to address a single question is rigorous. 2) The focus on in vivo kinetics rather than in vitro biochemistry is timely and relevant. 3) The inclusion of disease-relevant mutations (K195E) provides practical significance. 4) The proposal of an "effective in vivo binding energy landscape" is a novel conceptual contribution that could be widely adopted. 5) The reanalysis of other TFs (TALE, SOX2, GAF) suggests generality, which strengthens the impact.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The derivation of the binding energy landscape depends on unmeasured parameters (k* on,s, k off,s, k u-s, k s-u) that are fixed by assumption rather than experiment. The claim that "kinetic rather than thermodynamic stability might be a general feature" is extrapolated from a small number of TFs with limited methodological detail. The ChIP-Seq analysis lacks quality metrics and the threshold for "binding site loss" is not defined. The single-molecule tracking analysis relies on a three-component diffusion model whose justification is not fully presented. The relationship between the proposed energy landscape and traditional thermodynamic measurements is not clarified.
- **Assessment against Nature-style criteria** Originality: High. The concept of an effective in vivo binding energy landscape and the kinetic stability argument are novel. Scientific importance: High. Understanding TF binding kinetics in vivo is fundamental to gene regulation. Interdisciplinary readership: Moderate to high. The work bridges biophysics, cell biology, and disease genetics. Technical soundness: Moderate. The methods are appropriate but several key parameters are assumed rather than measured, and the statistical treatment is not fully described. Readability for nonspecialists: Moderate. The concepts are clearly explained but the methods section assumes significant expertise in single-molecule tracking and modeling.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially important, but the current evidence does not fully establish the claims, particularly regarding the energy landscape derivation and the generality of kinetic stability.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of energy landscape derivation
- **Claim pointer** The authors claim to construct an "effective in vivo binding energy landscape" of RBPJ-DNA binding from experimentally accessible kinetic rates and fractions.
- **Evidence pointer** Results section "The target site search time anticorrelates with transcriptional activity", Methods section "Calculation of the target site search time" and "Construction of the binding energy landscape", Figure 4
- **Concern** The energy landscape is derived using several parameters that are not experimentally measured. Specifically, the direct association rate k* on,s, direct dissociation rate k off,s, and microscopic transition rates k u-s and k s-u are not directly measured. The authors fix the ratio k off,s/k d to 0.0705 for all variants, which corresponds to an assumption that the target site search time is ten times faster than direct specific association. This assumption is not justified experimentally and could significantly affect the calculated energy barriers. Additionally, the frequency factor k A is assumed to be similar for all transitions, which is a strong assumption given that different conformational transitions may have different prefactors. The sensitivity of the conclusions to these assumptions is not tested.
- **Why it matters** The central conceptual contribution of the manuscript is the energy landscape visualization. If the landscape is heavily dependent on unmeasured and unjustified parameters, the conclusions about kinetic stability and mutation effects may not be robust. The claim that the approach is "model-free" is misleading because the energy landscape construction requires a specific kinetic model with several free parameters.
- **Resolution test** The authors should either measure or constrain the unmeasured parameters experimentally, or perform a thorough sensitivity analysis showing that the qualitative conclusions (e.g., kinetic stability, mutation effects on barriers) are robust to reasonable variations in these parameters. They should also clarify what "model-free" means in this context and acknowledge the assumptions made.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for generality claim
- **Claim pointer** The authors claim that "kinetic rather than thermodynamic stability of DNA binding might be a general feature of TFs in vivo" based on reanalysis of TALE-TFs, SOX2, and GAF.
- **Evidence pointer** Results section "RBPJ function is governed by association and dissociation rates", Figure 4e-g, Supplementary Tables 9-10
- **Concern** The generality claim is based on reanalysis of previously published data for TALE-TFs, SOX2, and GAF. However, the details of this reanalysis are not provided in the manuscript. It is unclear whether the same methods for determining bound fractions and kinetic rates were used, whether the same assumptions about unmeasured parameters were applied, and whether the data quality is comparable. The number of TFs analyzed is small (three additional factors), and they may not be representative of the diversity of TF families. The claim of generality is therefore not strongly supported.
- **Why it matters** The generality claim significantly increases the impact of the work. If the conclusion is based on limited or methodologically inconsistent reanalysis, it could be overstated. The field would benefit from a clearer understanding of which TFs exhibit kinetic stability and under what conditions.
- **Resolution test** The authors should provide a detailed description of the reanalysis methods for each TF, including how bound fractions and kinetic rates were extracted from the published data, what assumptions were made, and how the energy landscapes were constructed. They should also discuss potential limitations of comparing across different experimental systems and consider whether additional TFs with diverse DNA-binding domains should be analyzed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of ChIP-Seq data
- **Claim pointer** The authors state that cofactor binding mutations (FL/AA) reduce the number of RBPJ binding sites by ~74% and that in the absence of SHARP the number of sites is also reduced, concluding that cofactors contribute to target site specificity.
- **Evidence pointer** Results section "Both DNA and cofactor binding contribute to the chromatin binding specificity of RBPJ", Figure 1d-g
- **Concern** The ChIP-Seq analysis is presented without key quality metrics. It is unclear how peaks were called, what thresholds were used, how reproducibility between replicates was assessed, and whether the reduction in binding sites reflects true loss of occupancy or changes in peak height that fall below the detection threshold. The statement that "less than ~15% de novo binding to off-target sites" is made without defining what constitutes an off-target site or how this was determined. Additionally, the relationship between ChIP-Seq peak intensity and the single-molecule binding kinetics is not quantitatively compared.
- **Why it matters** The ChIP-Seq data are used to support the claim that cofactors are required for target site specificity. If the analysis is not rigorous, this conclusion could be weakened. A quantitative comparison between ChIP-Seq occupancy and kinetic parameters would strengthen the link between binding kinetics and genome-wide occupancy.
- **Resolution test** The authors should provide detailed ChIP-Seq analysis parameters, including peak calling thresholds, reproducibility metrics, and a definition of off-target sites. They should also consider performing a quantitative comparison between ChIP-Seq peak intensities and the kinetic parameters (e.g., residence times, bound fractions) to directly link the two datasets.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical treatment and error propagation
- **Claim pointer** The authors report residence times, bound fractions, and energy barriers with uncertainties (e.g., τs = 277 ± 108 s for WT), but the statistical methods are not fully described.
- **Evidence pointer** Results sections on residence times and binding fractions, Supplementary Tables 1-5
- **Concern** The manuscript does not describe how uncertainties were calculated for the reported kinetic parameters. It is unclear whether these are standard errors, confidence intervals, or something else. The error propagation from the single-molecule tracking data through the GRAM analysis to the final energy barrier calculations is not described. The number of cells, number of tracks, and biological replicates are not stated. Without this information, it is difficult to assess the precision of the reported values and whether differences between variants are statistically significant.
- **Why it matters** The conclusions about mutation effects (e.g., K195E reducing residence time) depend on the statistical significance of the differences. If the uncertainties are underestimated or the statistical tests are inappropriate, the conclusions could be incorrect.
- **Resolution test** The authors should provide a detailed description of the statistical methods, including how uncertainties are calculated, how many cells and tracks were analyzed per condition, and what statistical tests were used to compare variants. They should also report effect sizes and confidence intervals for key comparisons.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Figure 1b-c
- **Evidence pointer** Results section "Both DNA and cofactor binding contribute to the chromatin binding specificity of RBPJ"
- **Issue** The text states "As expected, the mutations in the DNA binding interface reduced the luciferase signal to either low (R/H, K/E and RFL/HAA) or very low (KRS/EHD) values above the background." However, the figure panels are not shown in the supplied text, and it is unclear whether the differences between "low" and "very low" are statistically significant or biologically meaningful.
- **Required correction** Clarify the statistical significance of the differences between variants and provide the actual values in the text or figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** "effective in vivo binding energy landscape"
- **Evidence pointer** Throughout the manuscript
- **Issue** The term "effective in vivo binding energy landscape" is used but not formally defined. It is unclear whether this represents a free energy surface, a kinetic barrier profile, or a combination of both. The relationship to traditional thermodynamic binding energy (ΔG) is not explicitly stated.
- **Required correction** Provide a formal definition of the "effective in vivo binding energy landscape" and clarify how it relates to standard thermodynamic and kinetic concepts.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail for single-molecule tracking
- **Affected element** Methods section "Single-molecule imaging"
- **Evidence pointer** Methods section
- **Issue** The methods describe time-lapse imaging with cycle times of 0.1 s to 6.4 s and continuous imaging with 10 ms exposure. However, the rationale for choosing these specific time scales and how they relate to the expected residence times of RBPJ is not explained. The photobleaching correction is mentioned but not described in detail.
- **Required correction** Provide a brief justification for the time scales used and a more detailed description of the photobleaching correction procedure.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The authors interpret their data within the framework of facilitated diffusion with three states. However, alternative models of TF search, such as hopping, intersegmental transfer, or direct targeting, are not discussed. The choice of the three-state model is justified but alternative interpretations are not considered.
- **Required correction** Briefly discuss alternative models and explain why the three-state model is most appropriate for the data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility of data
- **Affected element** Data availability section
- **Evidence pointer** Data availability
- **Issue** The single-particle tracking data are deposited in Dryad, but the link is provided as a share link for review purposes. It is unclear whether the data will be permanently archived and whether the source data for all figures are included in the "Source Data.xlsx" file.
- **Required correction** Confirm that the Dryad deposition will be permanent and that all source data are included.

## Risk / unsupported claims
- The claim that "kinetic rather than thermodynamic stability of DNA binding might be a general feature of TFs in vivo" is not fully supported by the data presented, as it is based on reanalysis of a small number of TFs with limited methodological detail.
- The "effective in vivo binding energy landscape" is presented as a model-free visualization, but its construction relies on several unmeasured parameters and assumptions that are not fully justified.
- The statement that cofactor binding mutations "reduced the number of identified binding sites of HT-RBPJ-WT by ~74%" is presented without defining the threshold for binding site identification or providing quality metrics for the ChIP-Seq data.
- The claim that "impaired DNA binding modulated not only dissociation, but also association to target sites" is based on the three-state model, but the direct association rate k* on,s is not experimentally measured and is inferred from the model.
- The relationship between the proposed "effective in vivo binding energy landscape" and traditional thermodynamic measurements of binding affinity is not clarified, making it difficult to compare with existing literature.