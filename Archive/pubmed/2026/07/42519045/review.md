## Review setup
- **Input scope** Full manuscript text (Summary, Introduction, Results, Discussion, Limitations, STAR Methods)
- **Assessment boundary** Scientific claims, experimental design, data analysis, and interpretation as presented; no independent replication or re-analysis of raw data performed
- **Shared manuscript claim summary** The authors propose a hierarchy of grammar rules governing the sequence-function relationship of transcriptional activation domains (ADs), identifying redundant aromatic residues and net negative charge as dominant features, and interpret these findings as consistent with an acidic-hydrophobic surfactant model of AD function.
- **Visible evidence base** In vivo high-throughput screen of ~7,327 designed AD sequences in yeast; regression coefficients for rule features; heatmaps and distribution plots of functionality scores; Lasso logistic regression AUC comparisons across three datasets; VIF and pairwise interaction analyses.
- **Missing materials affecting confidence** Raw sequencing data, full library composition details, individual sequence-level functionality scores, exact statistical outputs (confidence intervals, p-value distributions), and code for reproducibility were not fully inspectable from the provided text. Figures referenced but not fully legible in text (e.g., Figure 1B insets, Figure S1) limit verification of specific claims.

## Reviewer

- **Overall assessment** This study addresses a long-standing and important problem in eukaryotic gene regulation: the sequence grammar of transcriptional activation domains. The experimental design is thoughtful, leveraging a high-throughput in vivo screen with a continuous functionality readout, which is a methodological improvement over binary classification approaches. The identification of a rule hierarchy, with redundancy of aromatic residues and net negative charge as dominant features, is a potentially valuable contribution. However, the manuscript's central claims rest on the interpretation of regression coefficients and AUC values that are presented without full statistical context, and the generalizability of the findings beyond the restricted W/D/R/G sequence space remains uncertain. The surfactant model interpretation is intriguing but speculative, and the manuscript would benefit from a more cautious framing of this mechanistic proposal. Overall, the work is of interest to the gene regulation community, but several technical and interpretive issues need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, particularly those focused on activation domain function, intrinsically disordered proteins, and sequence-function relationships. The work is also relevant to computational biologists developing predictive models for protein function and to those interested in the biophysical principles underlying weak, multivalent interactions in gene regulation. The proposed surfactant model may attract interest from biophysicists and structural biologists.

- **Major strengths**
  1. The use of a continuous, quantitative in vivo functionality readout (growth slope) rather than a binary on/off classification is a significant strength, enabling more nuanced analysis of rule effects.
  2. The systematic combinatorial design of sequence libraries around defined grammar rules is rigorous and allows for clear attribution of functional effects to specific sequence features.
  3. The refinement of rules from binary to continuous definitions, with validation across multiple datasets (designed, random, natural), strengthens the generalizability of the conclusions.
  4. The pairwise interaction analysis provides insight into how rules combine, which is more biologically realistic than considering rules in isolation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and interpretability
- **Claim pointer** The claim that "the two dominant rules are the redundant representation of aromatic and acidic residues and the absence of positively charged residues, with coefficients of 3.51 and 2.85, respectively" (Figure 1A), and the subsequent ranking of rule importance throughout the manuscript.
- **Evidence pointer** Figure 1A, Figure 7A, Results section "Importance of grammar rules relative to each other"
- **Concern** The regression coefficients are presented as point estimates without confidence intervals, standard errors, or formal statistical comparisons between coefficients. The claim of "dominance" of two rules over others requires evidence that the coefficients are significantly different from each other, not merely that they are numerically larger. Additionally, the coefficients are derived from a single dataset (the designed library), and it is unclear whether the ranking is stable across the random and natural datasets. The manuscript would be substantially strengthened by reporting uncertainty measures and formal hypothesis tests for coefficient differences.
- **Why it matters** The central claim of the paper is the existence of a rule hierarchy. Without statistical evidence that the hierarchy is robust and not due to sampling variation, the primary conclusion is not fully supported.
- **Resolution test** Provide confidence intervals for all regression coefficients and perform formal tests (e.g., Wald tests or likelihood ratio tests) comparing the coefficients of the top-ranked rules against the others. Additionally, report whether the coefficient ranking is consistent when the model is fit separately to the random and natural sequence datasets.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability and external validity
- **Claim pointer** The claim that the refined rules "better reflect the AD functionality in vivo" based on improved prediction accuracy across three datasets (Figure 7B), and the broader implication that these rules describe AD grammar generally.
- **Evidence pointer** Figure 7B, Results section "Refined grammar rules for ADs"
- **Concern** The prediction accuracy for the natural sequences dataset is acknowledged to be poor, and the authors attribute this to small dataset size. However, this limitation undermines the claim of generalizability. The designed library is restricted to W, D, R, and G, which is a narrow subset of the amino acid alphabet. Natural ADs contain a much wider variety of residues, including other aromatics (F, Y), other acidics (E), and hydrophobic residues (L, I, V). The poor performance on natural sequences may indicate that the refined rules are overfit to the W/D/R/G space and do not capture the full complexity of natural AD grammar. The authors should either demonstrate that the rules generalize to a more diverse sequence space or temper their claims about universal applicability.
- **Why it matters** The stated goal is to understand the "language" of ADs, which implies a general grammar. If the rules only apply to a narrow sequence space, the significance of the work is substantially reduced.
- **Resolution test** Validate the refined rules on a larger, more chemically diverse set of natural AD sequences, or on a designed library that includes a broader range of amino acids (e.g., E, F, Y, L, I, V). If such validation is not feasible, the manuscript should explicitly state that the rules are specific to the W/D-rich class of ADs and discuss the implications of this limitation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The statement in the Discussion that the findings "fit well with the recently introduced amphiphilic acidic-hydrophobic model of AD function" and the interpretation of ADs as "acidic-hydrophobic surfactants."
- **Evidence pointer** Discussion section, Summary
- **Concern** The surfactant model is presented as a unifying explanation, but the evidence provided is indirect. The data show that certain sequence features correlate with function, but no direct biophysical measurements (e.g., surface activity, interfacial behavior, or interaction thermodynamics) are presented to support the surfactant mechanism. The model is plausible, but it is one of several possible interpretations of the data. The manuscript would be strengthened by a more balanced discussion of alternative models (e.g., specific coactivator binding, charge-charge interactions) and by explicitly stating that the surfactant model is a hypothesis that requires direct testing.
- **Why it matters** The mechanistic interpretation is a key part of the paper's significance. Overstating the support for a specific model could mislead readers and the field.
- **Resolution test** Add a paragraph in the Discussion that explicitly acknowledges the speculative nature of the surfactant model, discusses alternative interpretations, and outlines specific experimental tests (e.g., in vitro biophysical assays) that could distinguish between models.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** STAR Methods, "Estimation of sequence growth rates"
- **Evidence pointer** STAR Methods, "Estimation of sequence growth rates"
- **Issue** The description of the growth rate estimation is somewhat terse. It is stated that "robust linear regression" was used, but the specific implementation (e.g., which robust method, how outliers were handled) is not detailed. Additionally, the rationale for using the 200 μg/mL aureomycin treatment group for further analysis is not explained.
- **Required correction** Provide more detail on the robust regression method used and justify the choice of the 200 μg/mL treatment group for downstream analyses.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1B
- **Evidence pointer** Figure 1B
- **Issue** The figure legend mentions "Roman numerals indicate selected individual sequences," but the significance of these selected sequences is not explained in the text. It is unclear whether these are examples of specific functional or non-functional sequences, and what the reader should take away from them.
- **Required correction** Either remove the Roman numerals or add a brief explanation in the text or legend describing what these selected sequences illustrate.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of interaction analysis
- **Affected element** Results section "Refined grammar rules for ADs", Table S3
- **Evidence pointer** Table S3, Results section "Refined grammar rules for ADs"
- **Issue** The pairwise interaction analysis is mentioned, and some interactions are described in the text (e.g., balance with charge and redundancy). However, the magnitude and direction of these interaction effects are not quantified in the main text. It is difficult to assess the biological importance of these interactions without more detail.
- **Required correction** Provide a brief summary of the key interaction effects, including their direction (positive or negative) and approximate magnitude, in the main text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The term "grammar rules" is used throughout, which is evocative but potentially imprecise. The rules are essentially statistical correlations between sequence features and function. The term "grammar" might imply a more deterministic or generative framework than is supported by the data.
- **Required correction** Consider using a more neutral term such as "sequence determinants" or "compositional rules" in some places, or explicitly define what is meant by "grammar" in this context.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of statistical inference on regression coefficients (no CIs, no formal comparisons).
  - R1-M2: Poor generalizability to natural sequences, with the primary validation dataset being a narrow W/D/R/G space.

- **Assessment against Nature-style criteria**
  - **Originality**: The work is original in its systematic, quantitative approach to dissecting AD grammar and in proposing a hierarchy of rules. The surfactant model, while speculative, is a novel conceptual framework.
  - **Scientific importance**: The question of AD sequence-function relationships is of fundamental importance to gene regulation. A robust, quantitative understanding of AD grammar would have broad implications. However, the importance is currently tempered by the generalizability concerns.
  - **Interdisciplinary readership**: The work bridges molecular biology, computational biology, and biophysics. The findings are likely to be of interest to researchers in all three areas, though the biophysical interpretation is currently underdeveloped.
  - **Technical soundness**: The experimental design is sound, and the high-throughput screen is well-executed. However, the statistical analysis is incomplete, and the lack of uncertainty measures on the key quantitative claims is a significant technical weakness.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible. The concepts are introduced clearly, and the figures are helpful. However, the statistical methods and the interaction analysis may be challenging for non-specialists without additional context.

- **Recommendation posture** Supportive if technical concerns are resolved. The core experimental approach and the identification of a rule hierarchy are valuable contributions. However, the manuscript cannot be accepted in its current form. The authors must address the statistical rigor of the regression analysis (R1-M1) and provide a more thorough discussion of the generalizability of their findings (R1-M2). If these issues are resolved, the paper would be a strong contribution to the field.

## Risk / unsupported claims
- The claim that the two rules (redundancy and charge) are "dominant" is not statistically supported without confidence intervals or formal comparisons.
- The claim that the refined rules "better reflect AD functionality in vivo" is weakened by the poor performance on the natural sequences dataset, which is acknowledged but not adequately addressed.
- The interpretation of ADs as "acidic-hydrophobic surfactants" is presented as a strong conclusion, but the evidence is indirect and does not exclude alternative models. This should be framed as a hypothesis.
- The claim that "the 'acidic exposure' model is incomplete" based on the proline substitution experiments (Figure 4) is reasonable, but the conclusion is based on a limited set of sequence contexts and may not be universally applicable.