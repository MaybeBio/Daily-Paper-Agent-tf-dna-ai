## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided
- **Assessment boundary** Scientific content, technical soundness, claims versus evidence, and suitability for a high-impact general journal. No assessment of formatting, grammar, or editorial style beyond readability.
- **Shared manuscript claim summary** The authors report that fusing the hyperthermophilic DNA-binding protein Sso7d to the N terminus of LbaCas12a enhances trans-cleavage activity, catalytic turnover (kcat), detection sensitivity, and thermal robustness, enabling robust detection of antibiotic resistance genes from clinical Acinetobacter baumannii isolates where wild-type Cas12a produces little or no signal.
- **Visible evidence base** Results sections describing engineering and screening of fusion variants, kinetic analyses at 37 and 60 °C, guide RNA dependence, substrate independence, specificity and mismatch profiling, limit-of-detection measurements, and application to AMR detection. Supplementary figures and tables are referenced but not provided.
- **Missing materials affecting confidence** All supplementary figures and tables (Supplementary Figs 1–8, Supplementary Tables 1–3), raw kinetic data, calibration curves, statistical outputs, and the full amino acid sequences of fusion constructs. The manuscript states that DNA and amino acid sequences are available in the supplementary information file, which was not provided. No figure panels are visible in the supplied text.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially useful protein-engineering strategy to improve Cas12a trans-cleavage activity. The central claim, that fusing Sso7d to the N terminus of LbaCas12a enhances catalytic turnover and detection sensitivity, is supported by the reported kinetic parameters and the differential performance between fusion and wild-type enzymes in the AMR detection assay. However, the evidence base as provided is incomplete. The absence of all supplementary data, including the actual figures, raw traces, and sequence information, prevents full verification of several key claims. The mechanistic interpretation, while plausible, is inferred rather than directly demonstrated. The claim of improved thermal robustness is not quantitatively supported by the data described. The diagnostic application is compelling but relies on a single assay format with a limited number of clinical isolates. Overall, the work is of interest to the CRISPR diagnostics community and potentially beyond, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers in molecular diagnostics, CRISPR biology, and protein engineering. The work is directly relevant to those developing Cas12a-based detection platforms, as it offers a simple modular strategy to improve sensitivity and speed. The mechanistic insight into how accessory DNA-binding domains can modulate Cas12a activation may also interest structural biologists and enzymologists studying CRISPR effector complexes. The potential extension to other Cas orthologs and DNA-binding domains broadens the appeal to synthetic biologists.
- **Major strengths**
  1. The engineering strategy is modular and conceptually simple, with a clear rationale for choosing Sso7d based on its hyperthermophilic stability and non-specific DNA-binding properties.
  2. The kinetic characterization is thorough, reporting kcat, Km, and time-to-saturation under multiple conditions.
  3. The demonstration that the fusion improves detection of clinically relevant AMR genes from real isolates, where wild-type Cas12a fails, is a strong practical validation.
  4. The observation that specificity is not compromised, and may be improved, addresses a common concern with enhanced-activity enzyme variants.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence completeness
  - **Claim pointer** The manuscript claims a 4.6-fold increase in kcat and a 2-fold improvement in detection sensitivity for the Sso7d–Cas12a fusion relative to wild-type Cas12a.
  - **Evidence pointer** Results section "Sso7d fusion enhances catalytic turnover and thermal robustness", Table 1, Figure 3
  - **Concern** The kinetic parameters and the associated improvements are presented in Table 1 and Figure 3, but neither the table nor the figure panels are visible in the supplied text. The methods for kinetic analysis are described, but the actual data, including the calibration curve used to convert fluorescence to molar cleavage rates, are not available for inspection. Without these data, the magnitude of the reported kcat increase and the quality of the Michaelis–Menten fits cannot be independently assessed.
  - **Why it matters** The 4.6-fold kcat increase is a central quantitative claim that underpins the entire manuscript. If the kinetic analysis is flawed, or if the reported parameters are not robust across replicates, the core conclusion is weakened. The calibration curve is essential to verify that the fluorescence-based assay is properly quantitative.
  - **Resolution test** Provide the full kinetic data, including raw fluorescence traces, fitted curves, the calibration curve, and the derived Michaelis–Menten parameters with confidence intervals and replicate information. The table and figure must be visible and legible.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim versus evidence
  - **Claim pointer** The manuscript claims "substantially accelerated trans-cleavage kinetics" and "improved thermal robustness" for the fusion enzyme.
  - **Evidence pointer** Results section "Sso7d fusion enhances catalytic turnover and thermal robustness", Figure 3
  - **Concern** The text states that the fusion enzyme shows accelerated kinetics and retained activity at elevated temperatures, but the data supporting the thermal robustness claim are not described in sufficient detail. The kinetic analysis is reported at 37 and 60 °C, but it is unclear whether the comparison between fusion and wild-type at 60 °C is statistically powered, how many replicates were performed, and whether the wild-type enzyme was fully inactive or merely reduced in activity. The claim of "thermal robustness" implies a specific advantage at high temperature, but the data as described do not clearly establish this.
  - **Why it matters** The ability to function at elevated temperatures is a stated motivation for the work, as it would enable compatibility with high-temperature amplification methods. If the fusion enzyme does not actually provide a meaningful advantage at 60 °C, this aspect of the claim is overstated.
  - **Resolution test** Provide the full dataset for the 60 °C experiments, including replicate numbers, statistical analysis, and a direct comparison of fusion versus wild-type activity at multiple time points. Clarify whether the improvement at 60 °C is statistically significant and whether it is of practical magnitude.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim versus evidence
  - **Claim pointer** The manuscript claims that Sso7d–Cas12a enables detection of blaOXA-51 and blaOXA-24 from clinical A. baumannii isolates with up to a 30-fold increase in signal, whereas wild-type Cas12a produces little or no detectable signal.
  - **Evidence pointer** Results section "Improved analytical performance in antimicrobial resistance detection", Figure 8
  - **Concern** The AMR detection results are presented as a key validation of the fusion enzyme's practical utility. However, the figure is not visible, and the number of isolates tested, the replicate structure, and the statistical analysis are not described in the text. The claim that wild-type Cas12a "failed to produce a significant fluorescence signal above background" is strong, but the data supporting it are not available. Additionally, the LAMP results for blaOXA-23 are mentioned as negative but are only shown in supplementary figures that were not provided.
  - **Why it matters** The diagnostic application is the most compelling aspect of the manuscript. If the differential between fusion and wild-type is not robust across isolates and replicates, or if the wild-type failure is due to a trivial reason such as suboptimal guide selection, the practical significance is diminished.
  - **Resolution test** Provide the full dataset for the AMR detection experiments, including the number of isolates, replicates, raw fluorescence traces, endpoint values, and statistical comparisons. The figure must be visible. Clarify the guide RNA selection process for the AMR targets and whether the same guides were used for both fusion and wild-type enzymes.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Mechanistic interpretation
  - **Claim pointer** The manuscript proposes that Sso7d stabilises partially formed R-loop intermediates and accelerates the conformational activation step after target binding.
  - **Evidence pointer** Results section "Catalytic enhancement varies with guide RNA and is substrate-independent", Discussion
  - **Concern** The mechanistic model is inferred from the kinetic data and the observation that improvements are larger for guides with lower baseline activity. However, no direct biophysical or structural evidence is provided to support the proposed mechanism. The claim that Sso7d acts on the conformational activation step rather than on initial binding is based on the observation that Km is only modestly affected, but this is an indirect inference. Alternative explanations, such as Sso7d increasing the local concentration of the reporter substrate or altering the enzyme's processivity, are not excluded.
  - **Why it matters** The mechanistic interpretation is a significant part of the manuscript's intellectual contribution. If the proposed mechanism is incorrect or incomplete, the generalizability of the approach to other Cas enzymes or DNA-binding domains may be limited.
  - **Resolution test** Provide additional experimental evidence, such as stopped-flow kinetics, single-molecule FRET, or hydrogen-deuterium exchange mass spectrometry, to directly test the proposed conformational activation step. Alternatively, the authors could soften the mechanistic claims and present the work primarily as an empirical demonstration of enhanced activity.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract states "a twofold improvement in detection sensitivity" and "a 4.6-fold increase in kcat" but does not specify the assay conditions or the comparator. It is unclear whether the twofold improvement refers to the LOD in terms of DNA concentration or to the signal-to-noise ratio.
  - **Required correction** Specify the metric used for detection sensitivity and the conditions under which the comparison was made.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Materials and Methods, CRISPR assay
  - **Evidence pointer** Materials and Methods, CRISPR assay
  - **Issue** The buffer composition for the CRISPR assay is described as "10 mM Tris-HCl, 100 mM NaCl, 10 mM MgCl2, 100 µg/ml BSA pH 9 (for Sso7d-Cas12a)". It is unclear whether a different buffer was used for wild-type Cas12a or whether the same buffer was used for both. The pH of 9 is unusual for Cas12a assays, which typically use near-neutral pH.
  - **Required correction** Clarify the buffer conditions for both enzymes and justify the choice of pH 9.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results, LOD measurements
  - **Evidence pointer** Results section "Catalytic enhancement varies with guide RNA and is substrate-independent"
  - **Issue** The LOD measurements are described as being performed with serial dilutions, and the statistical test is stated as two-way ANOVA. However, the number of replicates, the definition of "reliable discrimination," and the criteria for calling a positive signal are not specified.
  - **Required correction** Provide the replicate number, the threshold for a positive call, and the statistical details of the ANOVA.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Generalizability
  - **Affected element** Discussion
  - **Evidence pointer** Discussion
  - **Issue** The authors state that the approach "could in principle be extended to other Cas orthologs or other small DNA-binding proteins," but no data are presented to support this speculation.
  - **Required correction** Either provide preliminary data on other Cas orthologs or DNA-binding domains, or clearly label this as speculation.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data Availability statement
  - **Evidence pointer** Data Availability section
  - **Issue** The data availability statement says that datasets are available from the corresponding author on reasonable request. For a manuscript with a strong methodological focus, this is insufficient. The authors should deposit raw kinetic data, calibration curves, and sequence information in a public repository.
  - **Required correction** Deposit all raw data and sequences in a public repository and provide accession numbers.
- **Technical failings that need to be addressed before the case is established**
  1. The kinetic parameters (kcat, Km) are reported without visible data or statistical confidence intervals. The calibration curve used to convert fluorescence to molar rates is not shown.
  2. The thermal robustness claim is not quantitatively supported. The data at 60 °C are described only qualitatively.
  3. The AMR detection results are presented without visible data, replicate numbers, or statistical analysis.
  4. The specificity data (off-target with KanR) are described but the figure is not visible.
  5. The LOD determination lacks a clear definition of the positive call threshold and the number of replicates.
- **Assessment against Nature-style criteria**
  - **Originality** The concept of fusing a non-specific DNA-binding domain to a CRISPR effector to enhance trans-cleavage is novel. While accessory domains have been used in other enzyme engineering contexts, this specific application to Cas12a diagnostics is not previously described. The work is original in its specific combination of elements.
  - **Scientific importance** The work addresses a real limitation of Cas12a-based diagnostics, namely modest catalytic turnover and reduced activity at elevated temperatures. If the claims are robust, the strategy could be broadly applicable. However, the importance is incremental rather than transformative, as it is an optimization of an existing platform rather than a fundamentally new capability.
  - **Interdisciplinary readership** The work will appeal to researchers in molecular diagnostics, CRISPR biology, and protein engineering. The potential for clinical application in AMR detection broadens the appeal to infectious disease researchers. However, the mechanistic depth is limited, which may reduce interest from structural biologists or enzymologists.
  - **Technical soundness** The experimental design is generally sound, with appropriate controls and a logical progression from enzyme engineering to kinetic characterization to application. However, the lack of visible data for key figures and the absence of statistical detail for several claims prevent full assessment. The mechanistic interpretation is plausible but not directly tested.
  - **Readability for nonspecialists** The manuscript is clearly written and the logic is easy to follow. The abstract and introduction provide sufficient context for a general reader. The methods section is appropriately detailed. The discussion is balanced and acknowledges limitations.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the practical demonstration in AMR detection is compelling. However, the case is not fully established from the supplied material. The authors must provide the missing data, particularly the kinetic parameters, the thermal stability data, and the AMR detection results, with full statistical analysis. The mechanistic claims should be either supported by direct evidence or softened. Once these issues are addressed, the manuscript could be suitable for publication in a high-impact journal.

## Risk / unsupported claims
- The claim of "improved thermal robustness" is not quantitatively supported by the data described in the text.
- The claim that Sso7d stabilises partially formed R-loop intermediates is speculative and not directly tested.
- The claim of a "2-fold improvement in detection sensitivity" is not defined with respect to the metric used or the statistical basis.
- The claim that wild-type Cas12a "failed to produce a significant fluorescence signal above background" in the AMR detection assay is not supported by visible data or statistical analysis.
- The statement that the approach "could in principle be extended to other Cas orthologs" is speculative and not supported by data.
- The claim of "substantially accelerated trans-cleavage kinetics" is not quantified in the text beyond the kcat value, which is not visible in the provided material.