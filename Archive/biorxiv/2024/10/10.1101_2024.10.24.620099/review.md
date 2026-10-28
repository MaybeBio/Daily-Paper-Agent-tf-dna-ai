## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, funding, conflict of interest, acknowledgements). Supplementary materials referenced but not provided.
- **Assessment boundary** Technical soundness, methodological clarity, validity of conclusions relative to presented data, and suitability for a high-impact general audience. No assessment of formatting or editorial policy.
- **Shared manuscript claim summary** The authors present a high-throughput single-molecule FRET platform using site-specifically labeled, enzymatically supercoiled plasmid DNA to study how DNA supercoiling affects protein-DNA interactions. They report that negative supercoiling enhances dCas9-gRNA unwinding of mismatched targets, and that both negative and positive supercoiling stabilize MutS binding to a GT mismatch without altering ATP-induced sliding clamp formation kinetics.
- **Visible evidence base** Results sections for CRISPR-Cas9 and MutS experiments, methods descriptions, figure legends (figures not directly viewable), and referenced supplementary tables and figures (not provided).
- **Missing materials affecting confidence** Figures and supplementary information (Tables S1-S4, Figures S1-S2) are not included in the provided text. Raw data, fitting parameters, and statistical details are not fully accessible. This limits independent verification of quantitative claims.

## Reviewer
- **Overall assessment** The manuscript describes a technically ambitious and potentially valuable method for studying DNA supercoiling effects on protein-DNA interactions at the single-molecule level. The core innovation, site-specific internal labeling of plasmid DNA combined with enzymatic supercoiling and smFRET, is well conceived and could be broadly useful. The two biological applications, dCas9 and MutS, are appropriate proof-of-principle demonstrations. However, the current manuscript has several technical gaps that need to be addressed, particularly regarding the characterization of supercoiling density, the specificity of the observed effects, and the quantitative rigor of the kinetic analyses. The conclusions are plausible but not fully established from the evidence presented.
- **Who would be interested in the results, and why** Researchers in single-molecule biophysics, DNA repair, CRISPR biology, and DNA topology. The methodological advance will appeal to those studying DNA-protein interactions under torsional stress. The MutS findings are relevant to the DNA mismatch repair field, and the dCas9 results have implications for genome editing applications where DNA topology may affect off-target activity.
- **Major strengths** 1) The method addresses a real need for high-throughput single-molecule assays that can probe DNA supercoiling effects. 2) The use of enzymatic supercoiling (gyrase and reverse gyrase) is elegant and avoids the need for specialized instrumentation. 3) The two proof-of-principle applications are well chosen and demonstrate the versatility of the platform. 4) The kinetic analyses, particularly for MutS, are thoughtful and attempt to dissect multiple steps in the interaction pathway.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (supercoiling density characterization), R1-M2 (specificity of dCas9 off-target effects), R1-M3 (MutS binding specificity), R1-M4 (kinetic model assumptions), R1-M5 (statistical rigor).
- **Assessment against Nature-style criteria** **Originality**: High. The combination of site-specific internal plasmid labeling with enzymatic supercoiling and smFRET is novel and distinct from existing approaches such as magnetic tweezers or rotor bead tracking. **Scientific importance**: Moderate to high. The method has clear utility, and the biological findings, if confirmed, would be of interest. However, the conceptual advance is primarily methodological rather than biological. **Interdisciplinary readership**: Moderate. The work bridges biophysics, DNA repair, and CRISPR biology, but the technical nature may limit appeal to a broad audience. **Technical soundness**: Currently not fully established. Several technical details and controls are missing or underdescribed. **Readability for nonspecialists**: The manuscript is generally well written, but the methods and results sections assume significant familiarity with single-molecule FRET and DNA topology concepts. A brief primer on supercoiling density and its biological relevance would improve accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The methodological advance is promising, and the biological findings are potentially interesting, but the current evidence does not fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to generate negatively and positively supercoiled plasmid DNA using gyrase and reverse gyrase, respectively, and use these to assess supercoiling effects on protein-DNA interactions.
- **Evidence pointer** Materials and Methods, "Plasmid DNA preparation with different DNA supercoiling status"; Results, "Site-specific labeled plasmid DNA is an optimal sample for smFRET experiment"
- **Concern** The manuscript does not provide any direct measurement of the supercoiling density (σ) of the prepared DNA substrates. The authors state that gyrase and reverse gyrase generate negative and positive supercoiling, respectively, but no data (e.g., agarose gel electrophoresis with chloroquine, two-dimensional gel analysis, or topoisomer distribution analysis) are shown to confirm the extent or distribution of supercoiling. This is critical because the magnitude of supercoiling will strongly influence the observed effects on protein-DNA interactions. Without this characterization, it is impossible to know whether the observed differences between supercoiled and relaxed DNA are due to physiologically relevant levels of supercoiling or to extreme, non-physiological states.
- **Why it matters** The central claim of the manuscript is that supercoiling affects protein-DNA interactions. If the supercoiling density is not quantified, the results cannot be interpreted quantitatively or compared to in vivo conditions. The authors themselves note that in vivo supercoiling density is approximately -0.06, but they do not demonstrate that their preparations achieve this level.
- **Resolution test** Provide gel electrophoresis data (e.g., agarose gels with and without chloroquine) showing the topoisomer distributions of the negatively supercoiled, positively supercoiled, and relaxed DNA preparations. Quantify the average supercoiling density (σ) for each preparation. If possible, show that the preparations are stable over the time course of the single-molecule experiments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that negative DNA supercoiling enhances DNA unwinding by dCas9-gRNA in the presence of mismatches, based on FRET-based measurements of unwound fraction over time.
- **Evidence pointer** Results, "CRISPR-Cas9: Negative DNA supercoiling enhances R-loop formation in the presence of mismatch"; Figure 2C-D
- **Concern** The manuscript reports that negative supercoiling enhances unwinding for dCas9-gRNA with a PAM-proximal mismatch, and also presents data for a PAM-distal triple mismatch. However, the specificity of this effect is not fully established. The authors do not show data for a perfectly matched target under the same conditions. Without this control, it is unclear whether the enhanced unwinding on negatively supercoiled DNA is specific to mismatched targets or is a general property of dCas9-gRNA on supercoiled DNA. Additionally, the manuscript does not report the number of independent experiments, the variability between experiments, or the number of molecules analyzed for each condition.
- **Why it matters** The conclusion that negative supercoiling "exacerbates off-target effects" is a strong claim with implications for genome editing. If the effect is not specific to mismatched targets, the interpretation would be different. The lack of a matched-target control and the absence of statistical details prevent the reader from assessing the robustness of the finding.
- **Resolution test** Include experiments with a perfectly matched target under identical conditions (negative, positive, and relaxed DNA). Report the number of independent experiments, the number of molecules analyzed, and the statistical significance of the differences in unwound fraction and rate constants between conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that both negative and positive supercoiling enhance the binding interaction between MutS and a mismatched base pair, based on dwell time analysis of MutS binding events.
- **Evidence pointer** Results, "MutS: DNA supercoiling stabilizes the interaction between MutS and a mismatched base pair"; Figure 3C-D
- **Concern** The MutS binding experiments rely on FRET between a Cy3-labeled MutS and a Cy5-labeled plasmid. The manuscript does not provide sufficient detail on how specific binding to the mismatch is distinguished from non-specific binding elsewhere on the plasmid. The authors state that high FRET corresponds to specific binding at the mismatch, but no control experiments are shown (e.g., MutS binding to a plasmid without a mismatch, or competition with unlabeled mismatch-containing DNA). Additionally, the dwell time analysis is described as "manual" using custom MATLAB scripts, which raises concerns about potential bias and reproducibility.
- **Why it matters** The conclusion that supercoiling stabilizes MutS-mismatch interactions depends entirely on the ability to identify and quantify specific binding events. If non-specific binding contributes to the observed dwell times, the conclusions would be compromised. The manual analysis approach is also a concern for reproducibility.
- **Resolution test** Include control experiments showing that the high-FRET state is dependent on the presence of a mismatch. Provide a detailed description of the automated or semi-automated analysis pipeline, including criteria for event selection and how potential biases were avoided. Report inter-observer variability if manual analysis is retained.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors derive rate constants for MutS binding, dissociation, and sliding clamp formation using a kinetic model that assumes a simple sequential scheme.
- **Evidence pointer** Materials and Methods, "MutS"; Results, "MutS: DNA supercoiling stabilizes the interaction between MutS and a mismatched base pair"; Figure 3E-F
- **Concern** The kinetic model used to extract k1, k-1, and k2 assumes a specific reaction scheme (binding, then either dissociation or conformational change to sliding clamp). The manuscript does not discuss whether alternative models were considered or whether the data are sufficient to distinguish between different kinetic schemes. For example, the sliding clamp could form directly from a non-specifically bound state, or the conformational change could be reversible. The authors also do not report confidence intervals for the fitted parameters or the results of model comparison tests.
- **Why it matters** The conclusion that supercoiling affects binding but not sliding clamp formation depends on the accuracy of the kinetic model. If the model is misspecified, the derived rate constants could be biased, and the conclusions could be incorrect.
- **Resolution test** Perform model comparison using, for example, Akaike information criterion or Bayesian information criterion, to justify the chosen kinetic scheme. Report confidence intervals for all fitted parameters. Discuss whether the data are sufficient to constrain all parameters in the model.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports quantitative differences in rate constants and fractions between different supercoiling conditions.
- **Evidence pointer** Results, "CRISPR-Cas9" and "MutS" sections; Figure 2C-F and Figure 3C-F
- **Concern** The manuscript does not report the number of independent biological replicates, the number of molecules analyzed per condition, or the statistical tests used to compare conditions. Error bars are described as standard error, but the number of measurements is not stated. Without this information, it is not possible to assess whether the reported differences are statistically significant.
- **Why it matters** The conclusions rely on quantitative comparisons between conditions. Without proper statistical reporting, the reader cannot evaluate the reliability of the findings.
- **Resolution test** Report the number of independent experiments, the number of molecules analyzed, and the statistical tests used for each comparison. Provide effect sizes and confidence intervals for the key findings.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that negative supercoiling "exacerbates off-target effects" for Cas9, but the data shown are for dCas9 (catalytically dead) unwinding, not for cleavage or editing outcomes. The term "off-target effects" is potentially misleading.
- **Required correction** Clarify that the observed effect is on DNA unwinding by dCas9-gRNA, and discuss the implications for off-target effects as a inference rather than a direct measurement.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and Methods, "Plasmid DNA preparation with different DNA supercoiling status"
- **Evidence pointer** Materials and Methods
- **Issue** The method for generating positively supercoiled DNA using reverse gyrase is described, but the incubation temperature (80 °C) is noted. It is unclear whether the labeled plasmid DNA, particularly the fluorescent dyes, is stable at this temperature for 30 minutes.
- **Required correction** Address the thermal stability of the fluorescent labels under the reverse gyrase reaction conditions, or provide data showing that the labels remain functional after the supercoiling reaction.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "CRISPR-Cas9" section
- **Evidence pointer** Results
- **Issue** The manuscript describes fitting the unwound fraction over time to a one-phase association model, but the equation is not shown in the main text. The reader is referred to the Materials and Methods, but the equation number is not given.
- **Required correction** Include the equation in the Results section or provide a clear cross-reference to the equation in the Materials and Methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods, "MutS"
- **Evidence pointer** Materials and Methods
- **Issue** The dwell time analysis is described as "manual" using custom MATLAB scripts. This is a potential source of bias and makes the analysis difficult to reproduce.
- **Required correction** Provide the custom MATLAB scripts as supplementary material or describe the analysis pipeline in sufficient detail to allow independent implementation. Consider using an automated or semi-automated approach.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "MutS" section
- **Evidence pointer** Results
- **Issue** The manuscript states that the sliding clamp formation rate (k2) did not change significantly with supercoiling, but the data are not shown in the main text. The reader is referred to Figure 3F, but the figure is not viewable in the provided text.
- **Required correction** Ensure that the figure clearly shows the k2 values for all conditions and that the statistical comparison is described in the text or figure legend.

## Risk / unsupported claims
- The claim that negative supercoiling "exacerbates off-target effects" for Cas9 is not directly supported by the data, which measure dCas9 unwinding rather than editing outcomes.
- The claim that supercoiling enhances MutS binding to a mismatch is based on FRET measurements that may not distinguish specific from non-specific binding without additional controls.
- The quantitative rate constants (k1, k-1, k2) for MutS are derived from a kinetic model that is not validated against alternative models.
- The supercoiling density of the DNA substrates is not measured, so the physiological relevance of the observed effects is unclear.
- The stability of fluorescent labels under reverse gyrase reaction conditions (80 °C) is not addressed.
- The number of independent experiments and molecules analyzed is not reported, limiting the assessment of statistical significance.