## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, tables, and supplementary figure legends as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and internal consistency of the provided manuscript. No external literature verification or replication of experiments performed.
- **Shared manuscript claim summary** The authors propose that the human CST complex inhibits telomerase primarily by sequestering the telomeric ssDNA primer, thereby preventing initiation of extension, and that CST does not actively terminate ongoing processive telomerase extension. They support this with DNA-binding mutant studies, quantitative binding assays, and competitive binding modeling.
- **Visible evidence base** Abstract, full introduction, materials and methods, results sections, discussion, Table 1, and references to Supplementary Figures S1–S8. No raw data files, uncropped gels, or original imaging data were provided.
- **Missing materials affecting confidence** Raw gel images, uncropped blots, raw counts for telomerase activity quantification, full details of the competitive binding script validation, and complete supplementary figures were not available for direct inspection.

## Reviewer

- **Overall assessment** This manuscript presents a focused and well-designed study addressing the mechanism by which CST inhibits telomerase. The use of DNA-binding mutants combined with quantitative binding assays and an exact competitive binding model is a rigorous approach. The conclusion that CST acts via primer sequestration rather than active eviction is clearly supported by the pulse-chase experiments. The work is technically sound and the conclusions are appropriately tempered. The manuscript is suitable for publication in a specialized journal, though its broad significance for a general readership is moderate.

- **Who would be interested in the results, and why** Researchers studying telomere biology, telomerase regulation, DNA replication, and the CST complex. The mechanistic distinction between initiation inhibition and processive extension termination is of direct relevance to understanding telomere length homeostasis and the coordination of G-strand and C-strand synthesis. The quantitative modeling approach may also interest biochemists working on protein-nucleic acid competition.

- **Major strengths**
  1. The use of multiple DNA-binding mutants with quantitative binding measurements provides strong genetic evidence linking DNA binding to telomerase inhibition.
  2. The application of an exact competitive binding model, rather than simplifying assumptions, strengthens the mechanistic interpretation.
  3. The pulse-chase experimental design directly tests the question of whether CST can terminate ongoing extension, and the negative result is convincing.
  4. The inclusion of a control mutant (g4.1) and the comparison with a DNA-binding mutant (g2.1) in the pulse-chase experiments effectively rules out nonspecific protein effects.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Experimental evidence
- **Claim pointer** The authors state that "CST has no detectable ability to terminate ongoing telomerase extension in vitro" based on pulse-chase experiments.
- **Evidence pointer** Results section, Figure 5D–H, Figure 6C
- **Concern** The pulse-chase experiments demonstrate that pre-initiated products continue to elongate after CST addition. However, the interpretation that CST does not affect ongoing extension relies on the assumption that the continued elongation is processive and not due to re-initiation by telomerase on the same primer. The authors argue that excess unextended primer acts as an internal chase, but this argument is not directly tested. A control experiment using a 3'-blocked primer as a chase would strengthen the conclusion.
- **Why it matters** If re-initiation were occurring, the observed continued elongation could be misinterpreted as processive extension, which would undermine the central claim that CST does not evict elongating telomerase.
- **Resolution test** Perform a pulse-chase experiment where a 3'-end-blocked primer is added along with CST to prevent any re-initiation. If elongation of pre-initiated products continues under these conditions, the conclusion that CST does not terminate ongoing extension would be firmly established.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Modeling assumptions
- **Claim pointer** The authors claim that the competitive binding model "provides strong support for the primer sequestration model" and that the fitted telomerase-DNA Kd matches independently measured values.
- **Evidence pointer** Results section, Figure 4B–C, Table 1
- **Concern** The model assumes a simple 1:1 competitive binding equilibrium between CST and telomerase for the DNA primer. However, telomerase is a ribonucleoprotein with a template RNA that must anneal to the primer, and its binding may involve multiple steps or conformational changes. The model also assumes that all CST is active and that the gamma factor (active fraction) is constant across conditions. The authors acknowledge the gamma factor but do not discuss whether the fitted value is biologically plausible or whether the model is sensitive to this assumption.
- **Why it matters** If the model is an oversimplification, the agreement between fitted and measured Kd values could be coincidental, and the conclusion that competitive binding fully explains inhibition would be weakened.
- **Resolution test** Test the model's robustness by varying the gamma factor and Kd values within experimental error and assessing whether the fit remains acceptable. Additionally, perform experiments at higher DNA concentrations where the model predicts a plateau in inhibition to verify the predicted behavior.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Data interpretation
- **Claim pointer** The authors state that "the switch from G-strand to C-strand synthesis may be passive rather than active" based on the lack of observed eviction.
- **Evidence pointer** Discussion section
- **Concern** The conclusion that the switch is passive is an extrapolation from in vitro data. The authors do not consider the possibility that other factors, such as post-translational modifications of CST or telomerase, or the presence of shelterin components, could actively promote termination in vivo. The discussion acknowledges this limitation but does not propose any testable predictions to distinguish passive from active switching.
- **Why it matters** The physiological relevance of the proposed passive mechanism is uncertain. If the switch is active in vivo, the in vitro findings would be incomplete and potentially misleading.
- **Resolution test** Propose and test a specific prediction of the passive model, such as the absence of a physical interaction between CST and telomerase during extension, or the lack of a CST-induced conformational change in telomerase. Alternatively, test whether a known telomere-binding factor can promote termination in the presence of CST.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Materials and Methods, "Direct telomerase assay"
- **Evidence pointer** Location not provided
- **Issue** The description of the pulse-chase experiment is brief. It is unclear how the "excess of unlabeled dGTP" was added and whether the addition of CST and cold dGTP were simultaneous or sequential.
- **Required correction** Provide a more detailed step-by-step description of the pulse-chase protocol, including the timing of additions and the concentrations used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table reports Kd values with standard deviations but does not specify the number of replicates for each mutant. The text mentions n values for WT and mutants in the EMSA section, but this is not consistently reported for all FP measurements.
- **Required correction** Add a column or footnote indicating the number of independent experiments (n) for each Kd value in Table 1.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, "CST inhibits telomerase extension independent of bound pol α-primase"
- **Evidence pointer** Figure 6A–E
- **Concern** The conclusion that pol α-primase is not involved in inhibition is based on the comparison of CST purified at 150 mM vs 300 mM KCl. However, the authors do not show that the 300 mM KCl preparation is fully active for pol α-primase stimulation, which would confirm that the removal was effective without damaging CST.
- **Required correction** Include a control experiment demonstrating that the 300 mM KCl CST preparation retains the ability to stimulate pol α-primase activity when pol α-primase is added back.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The pulse-chase experiment lacks a control to rule out re-initiation, which is essential to support the claim that CST does not terminate ongoing extension.
  - R1-M2: The competitive binding model's assumptions and sensitivity are not fully explored, which is necessary to validate the mechanistic conclusion.

- **Assessment against Nature-style criteria**
  - **Originality** The study provides a clear and quantitative test of a previously proposed model, but the concept of primer sequestration is not novel. The originality lies in the detailed quantitative analysis and the direct test of eviction, which adds new information to the field.
  - **Scientific importance** The findings are important for understanding telomere length regulation and the coordination of leading and lagging strand synthesis. The distinction between initiation inhibition and processive extension termination has implications for how telomere homeostasis is achieved.
  - **Interdisciplinary readership** The topic is of interest primarily to molecular biologists and biochemists specializing in telomeres and DNA replication. The quantitative modeling may appeal to computational biologists, but the overall scope is narrow.
  - **Technical soundness** The experimental methods are appropriate and well-executed. The use of multiple assays (EMSA, FP, telomerase activity) and the exact competitive binding model strengthen the technical rigor. However, the concerns raised above need to be addressed to fully establish the case.
  - **Readability for nonspecialists** The manuscript is clearly written and the logic is easy to follow. The use of figures and supplementary data aids comprehension. The discussion is accessible, though some familiarity with telomere biology is assumed.

- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are likely correct and the study is well-executed, but the concerns regarding the pulse-chase control and model validation should be addressed before the conclusions can be fully accepted.

## Risk / unsupported claims
- The claim that "the switch from G-strand to C-strand synthesis may be passive rather than active" is an extrapolation from in vitro data and is not directly supported by the experiments presented. This is appropriately framed as a suggestion in the discussion, but it should not be overstated.
- The statement that "the same lack of inhibition was observed with or without pol α-primase bound to CST" is supported by the data, but the authors do not demonstrate that the pol α-primase in the 300 mM KCl preparation is fully removed or inactive, which could affect interpretation.
- The fitted gamma factor (0.465) representing the active fraction of CST is not independently validated, and the model's predictions are not tested at extreme conditions, leaving some uncertainty in the quantitative conclusions.