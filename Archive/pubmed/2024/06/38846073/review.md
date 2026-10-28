## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, conclusion, methods, and experimental methods sections.
- **Assessment boundary** Scientific claims, methodological soundness, data interpretation, and alignment with stated conclusions. Editorial and formatting issues are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors use molecular dynamics simulations of 33 steroidal ligands bound to the progesterone receptor ligand-binding domain to propose that ligand potency is governed by competition between an ancestral, Asn719-dependent activation mechanism and a modern, Asn719-independent mechanism. They classify ligands into four potency classes and support their simulation findings with luciferase reporter assays on PR mutants.
- **Visible evidence base** MD simulation trajectories (triplicate 500 ns per complex), MM-PBSA/MM-GBSA binding energies, SASA calculations, hydrogen bond occupancy analysis, Cα–Cα distance analysis, network analysis, and in vitro transactivation assays with PR mutants. Figures cited include Fig. 1, 2, 3, and 4; supplementary figures and tables are referenced but not provided.
- **Missing materials affecting confidence** Supplementary figures and tables (Fig. S1–S8, Tables S1–S4) are referenced but not available for review. Full EC50 data for all 33 ligands are not in the main text. Statistical details for transactivation assays (number of replicates, error bars, statistical tests) are not fully described. The manuscript text appears truncated in the Conclusion section, with an incomplete sentence and an embedded SVG element.

## Reviewer
- **Overall assessment** This manuscript presents an interesting and potentially valuable hypothesis regarding the evolutionary basis of ligand-dependent activation of the progesterone receptor. The combination of extensive MD simulations with in vitro mutagenesis is commendable. However, the central claims rest heavily on simulation-derived metrics whose relationship to functional potency is correlative rather than mechanistic. The in vitro data, while supportive of some trends, do not strongly discriminate between the proposed mechanisms. The manuscript would benefit from clearer presentation of the classification scheme, more robust statistical treatment of simulation data, and a more cautious interpretation of the evolutionary narrative. The work is likely of interest to the nuclear receptor and steroid hormone signaling communities, but the current evidence does not fully establish the proposed mechanistic competition.
- **Who would be interested in the results, and why** Researchers in nuclear receptor biology, steroid hormone signaling, structural biology, and computational chemistry would find this work relevant. Those interested in the evolutionary history of steroid receptors and the molecular basis of ligand selectivity and potency would be particularly engaged. The findings may also inform drug discovery efforts targeting PR, especially in the context of designing ligands that exploit or avoid specific activation mechanisms.
- **Major strengths**
  - The study addresses a significant and underexplored question: how evolutionary history shapes the response of a nuclear receptor to diverse ligands.
  - The use of a large ligand library (33 compounds) spanning a wide potency range is a notable strength.
  - The combination of multiple simulation-based analyses (dynamics, energetics, SASA, hydrogen bonding, network analysis) provides a comprehensive view of ligand-induced conformational changes.
  - The inclusion of in vitro transactivation assays with PR mutants provides an experimental anchor for the simulation predictions.
  - The identification of four ligand classes based on dynamic signatures is a potentially useful framework for future studies.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The manuscript claims that "potent ligands utilize the modern PR mechanism while weaker ligands coopt the defunct ancestral mechanism by forming hydrogen bonds with Asn719."
- **Evidence pointer** Results and discussion, Fig. 3F and 3G; Table S4 (not provided)
- **Concern** The central mechanistic claim rests on hydrogen bond occupancy differences between ligand classes. However, the manuscript does not provide a quantitative comparison of these occupancies across all 33 ligands, nor does it show that the observed differences are statistically significant. The representative ligands shown in Fig. 3G (ZK5, DHT, BUD, P0M) are illustrative but do not establish a class-wide pattern. Furthermore, the correlation between hydrogen bond occupancy and functional potency is not quantified. The claim that weak ligands "coopt" an ancestral mechanism implies causality, but the simulations only show correlation.
- **Why it matters** The evolutionary narrative is the central thesis of the manuscript. If the hydrogen bonding patterns are not robustly and quantitatively linked to potency across the full ligand set, the claim is not established.
- **Resolution test** Provide a quantitative analysis of hydrogen bond occupancy for all 33 ligands, grouped by class, with appropriate statistical tests (e.g., ANOVA or Kruskal-Wallis). Show a scatter plot or correlation analysis between Asn719 hydrogen bond occupancy and EC50. Demonstrate that the pattern holds when ligands are analyzed individually, not just as class averages.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "moderate potency agonists display significantly stronger coupling (i.e., lower shortest distance) with AF-2" and that "moderate potency agonists show significantly weaker communication (higher shortest distance) with H5 residues compared to high potency agonists."
- **Evidence pointer** Results and discussion, Fig. 1E and 1G
- **Concern** The "shortest distance" metric is a non-standard, unitless quantity derived from network analysis. The manuscript does not provide sufficient validation of this metric as a meaningful measure of allosteric communication. The statistical comparison between classes is not described in detail; it is unclear what test was used, whether multiple testing was corrected for, and what the effect sizes are. The biological interpretation of "stronger coupling" or "weaker communication" is not grounded in any experimental validation.
- **Why it matters** The classification of ligands into four classes is based on this metric. If the metric is not robust or its biological meaning is unclear, the classification scheme is on shaky ground.
- **Resolution test** Provide a detailed description of the statistical methods used to compare shortest distances between classes. Include effect sizes and confidence intervals. Validate the metric by showing that it correlates with an independent measure of allosteric communication (e.g., dynamic network analysis using a different algorithm, or perturbation response scanning). Consider showing that the classification is robust to the choice of network parameters.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The manuscript claims that "weak ligands coopt the ancestral steroid receptor mechanism to achieve weak activity in PR" and that "moderate ligands... display weaker activity than high potency ligands because of the C11–OH, which introduces evolutionary pressure on ligands to revert to the ancient Asn719-dependent activation."
- **Evidence pointer** Results and discussion, Fig. 3H and 3I; Fig. S6 and S7 (not provided)
- **Concern** The in vitro transactivation assays with PR mutants are presented as supporting evidence for the simulation-based mechanisms. However, the manuscript states that "ligands tended to display the same effects across all mutations," which undermines the claim that specific residues mediate class-specific mechanisms. The data appear to show a general sensitivity to mutations rather than a differential effect by ligand class. The manuscript acknowledges this but does not reconcile it with the proposed mechanism. The number of replicates, error bars, and statistical analysis for these assays are not described.
- **Why it matters** The in vitro data are the only experimental validation of the simulation predictions. If they do not show class-specific effects, the mechanistic claims are not experimentally supported.
- **Resolution test** Provide a full statistical analysis of the transactivation data, including replicates, error bars, and tests for interaction effects between ligand class and mutation. Show whether the pattern of responses to mutations is significantly different between ligand classes. If not, revise the mechanistic claims to be more cautious.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "we have not accounted for full versus partial agonistic activity of the ligands here, as we have focused solely on EC50 values."
- **Evidence pointer** Methods, ligand selection; Table S1 (not provided)
- **Concern** The use of EC50 as the sole measure of ligand activity is a simplification. Partial agonists may have similar EC50 values to full agonists but different mechanisms of action. The classification of ligands into potency classes based on EC50 alone may conflate efficacy with potency. This is acknowledged in the Conclusion, but the implications for the mechanistic claims are not discussed.
- **Why it matters** If some ligands in the "high potency" class are partial agonists, their dynamic signatures may reflect a different mechanism than full agonists, confounding the classification.
- **Resolution test** Discuss the potential impact of partial agonism on the interpretation of the results. If possible, include efficacy data (e.g., Emax) in the analysis or at least acknowledge the limitation more prominently.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes the use of 33 ligands, but the Methods section states that "a library of sixty-six complexes" was prepared, with 32 ligands inserted into the PR pocket.
- **Evidence pointer** Methods, Model preparation
- **Concern** There is a numerical discrepancy: the abstract and results mention 33 ligands, while the Methods section states 32 ligands were inserted. Additionally, the unliganded complex is mentioned, but it is unclear if this is included in the 66 complexes. This inconsistency affects the reproducibility of the study.
- **Why it matters** Reproducibility is a core requirement for computational studies. A discrepancy in the number of systems studied undermines confidence in the results.
- **Resolution test** Clarify the exact number of ligand-bound complexes and the total number of simulations performed. Ensure consistency between the abstract, results, and methods.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "Ancient and modern mechanisms compete" is evocative but not defined in the abstract. The reader is left to infer what these mechanisms are.
- **Required correction** Briefly define the two mechanisms in the abstract, e.g., "an ancestral Asn719-dependent hydrogen bonding mechanism and a modern Asn719-independent hydrophobic mechanism."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results and discussion, Fig. 1
- **Evidence pointer** Fig. 1A and 1B
- **Issue** The structural features of the ligands used for the SAR classification are described in the text, but the figure itself is not self-explanatory. The reader must refer to the text to understand the labeling scheme.
- **Required correction** Add a legend to Fig. 1 that explains the labeling of substituents (e.g., 'b' for bulky, 'c' for corticosteroid-like, 'e' for esterified, 'm' for methyl).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results and discussion, Fig. 2
- **Evidence pointer** Fig. 2C–H
- **Issue** The manuscript mentions p < 0.05 for one comparison but does not provide statistical details for other comparisons. It is unclear whether all pairwise comparisons were performed and what the significance levels are.
- **Required correction** Provide a full description of the statistical tests used for SASA and binding energy comparisons, including correction for multiple testing.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusion
- **Evidence pointer** Conclusion, final paragraph
- **Issue** The text is truncated mid-sentence, and an SVG element is embedded. This appears to be a formatting error.
- **Required correction** Complete the sentence and remove the SVG element.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Experimental methods
- **Evidence pointer** Methods, Experimental methods
- **Issue** The primer sequences for site-directed mutagenesis are mentioned but not listed. The statement "The following primers used for the mutagenesis reactions:" is followed by no content.
- **Required correction** Provide the full list of primer sequences or a reference to where they can be found.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results and discussion, Fig. 3
- **Evidence pointer** Fig. 3H and 3I
- **Issue** The transactivation assay results are described qualitatively. The manuscript states that "ligands tended to display the same effects across all mutations," but the figure is not shown in the main text.
- **Required correction** Show the data in the main text or provide a clear summary of the results in the text, including effect sizes and variability.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative, statistically robust evidence linking hydrogen bond occupancy to potency across the full ligand set.
  - R1-M2: The "shortest distance" metric is not validated and its statistical treatment is incomplete.
  - R1-M3: The in vitro data do not show class-specific effects, undermining the mechanistic claims.
  - R1-M5: Numerical inconsistency in the number of ligands studied.
  - Missing primer sequences in the Methods section.
  - Truncated text and embedded SVG in the Conclusion.

- **Assessment against Nature-style criteria**
  - **Originality** The evolutionary framing of PR activation mechanisms is a fresh perspective. The idea that a receptor retains a vestigial activation mechanism that can be coopted by specific ligands is conceptually interesting. However, similar evolutionary analyses have been applied to other nuclear receptors, and the novelty here is incremental rather than paradigm-shifting.
  - **Scientific importance** The work has implications for understanding PR pharmacology and potentially for drug design. However, the importance is limited by the lack of strong experimental validation of the central mechanism. The findings are more likely to be of interest to specialists than to a broad scientific audience.
  - **Interdisciplinary readership** The work bridges computational chemistry, structural biology, and endocrinology. However, the heavy reliance on simulation-derived metrics may limit accessibility to experimentalists. The evolutionary narrative could attract a broader readership if it were more convincingly supported.
  - **Technical soundness** The simulation methodology is standard and appears to be executed competently. However, the analysis and interpretation of the "shortest distance" metric and the hydrogen bond occupancy data are not sufficiently rigorous. The statistical treatment is incomplete. The in vitro assays are underpowered to support the claims.
  - **Readability for nonspecialists** The manuscript is generally well-written and the concepts are explained clearly. However, the Methods section is dense and the "shortest distance" metric is not intuitively explained. The evolutionary narrative is engaging and helps readability.

- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the computational approach is appropriate, but the evidence presented does not currently establish the proposed mechanistic competition. The authors need to provide a more rigorous quantitative analysis of their simulation data, strengthen the statistical treatment, and either provide stronger experimental support or temper their mechanistic claims. The manuscript has potential but requires substantial revision before it can be considered for publication.