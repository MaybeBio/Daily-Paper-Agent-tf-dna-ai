## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and internal consistency of the reported findings
- **Shared manuscript claim summary** The authors propose that binding pathways of small molecules on disordered proteins are predominantly protein-defined rather than ligand-defined, based on MSM analysis of MD simulations of Aβ42 and α-synuclein C-terminal region, supported by ensemble docking and a prospective screening pipeline
- **Visible evidence base** Abstract, Introduction, Results (4 main sections), Discussion, Materials and Methods; Figures 1-6 referenced but not provided; Supplementary Figures S1-S2 referenced but not provided
- **Missing materials affecting confidence** All figures and supplementary materials; simulation trajectory data; specific numerical results for enrichment factor and AUC analyses beyond summary statistics; details of the prospective screening output; experimental validation data (stated as forthcoming)

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question in disordered protein drug discovery, namely whether binding pathways are intrinsic properties of the protein sequence or ligand-specific features. The conceptual framework is appealing and the methodological approach is sophisticated. However, the central claim of protein-defined binding pathways rests on evidence that is presented only in summary form, with key quantitative results and all figures unavailable for inspection. The prospective screening application is a valuable translational test but the results are not yet validated experimentally. The manuscript would benefit from clearer presentation of the statistical robustness of the pathway conservation claims and a more critical discussion of the limitations of the MSM construction on short peptide systems.
- **Who would be interested in the results, and why** Researchers in disordered protein biophysics, computational drug discovery, and molecular recognition. The work is also relevant to those studying fuzzy complexes and transient protein-ligand interactions, as well as developers of computational screening methods for challenging targets.
- **Major strengths** The conceptual framing is clear and addresses a fundamental question in the field. The combination of MSM analysis with ensemble docking provides complementary evidence. The inclusion of a urea control is a thoughtful experimental design element. The prospective screening pipeline represents a practical translational application of the framework.
- **Major Concerns** The core quantitative evidence for pathway conservation is not directly inspectable. The manuscript reports summary statistics but the underlying data, figures, and detailed analyses are not available. The claim of protein-defined pathways is strong and requires robust statistical support, particularly given the relatively small number of ligands tested per target. The relationship between the computed effective KD values and experimental affinities is not fully reconciled. The prospective screening results are presented as a validation but no experimental confirmation is provided.
- **Minor Comments** Several methodological details are incomplete, including the exact definition of the enrichment factor formula, the handling of the urea control in the comparison analyses, and the criteria for selecting the 40 microstates for the prospective screen. The discussion of limitations is honest but could be expanded on the potential force field dependence of the conclusions.
- **Technical failings that need to be addressed before the case is established** The absence of all figures and supplementary data prevents verification of the central claims. The enrichment factor and AUC analyses are described but the actual distributions, confidence intervals, and statistical tests are not shown. The comparison between computed and experimental KD values requires more careful treatment.
- **Assessment against Nature-style criteria** Originality: High. The question of whether binding pathways are protein- or ligand-defined is novel and important. Scientific importance: High if the claims are substantiated, as this would have implications for disordered protein drug discovery. Interdisciplinary readership: Moderate to high, appealing to biophysicists, computational chemists, and structural biologists. Technical soundness: Cannot be fully assessed without the figures and detailed results; the methodological framework is reasonable but the evidence base is incomplete. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some technical sections assume familiarity with MSM methodology.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising and the approach is sound, but the central claims cannot be verified without access to the figures, supplementary data, and detailed statistical results. The manuscript would be suitable for reconsideration if the full evidence base is made available and the technical concerns are addressed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims strong conservation of dominant binding pathways across chemically diverse ligands, with enrichment factors of 15-45 and AUC values typically ≥0.75
- **Evidence pointer** Figures 4a and 4b; location not provided for specific data points
- **Concern** The central quantitative claim of pathway conservation is presented only as summary statistics. The actual enrichment factor distributions, AUC curves, confidence intervals, and the underlying ranked lists of contact triplets are not shown. Without these data, it is impossible to assess whether the reported values are statistically robust, whether they are driven by a small number of highly conserved states, or whether the comparison methodology is appropriate.
- **Why it matters** The claim that binding pathways are protein-defined rather than ligand-defined is the central conclusion of the manuscript. If the statistical support is weak or the analysis methodology is flawed, the entire conceptual framework is undermined.
- **Resolution test** Provide the full enrichment factor and AUC analysis results, including distributions, confidence intervals, and the ranked lists of contact triplets for all pairwise comparisons. Show the actual data in the main figures or supplementary materials.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that ensemble docking recovers the dynamics-defined hotspot in 89% of cases, compared with 26% for Fpocket detection alone
- **Evidence pointer** Figure S2; location not provided
- **Concern** This is a striking quantitative claim that directly supports the protein-defined pathway hypothesis. However, the underlying data are not shown. The definition of "recovery" is not fully specified, and the comparison with Fpocket alone may not be a fair baseline if the docking procedure uses information from the same trajectories.
- **Why it matters** This result provides independent support for the MSM-based conclusions. If the recovery rate is inflated by methodological choices or the comparison is not appropriate, the convergence argument is weakened.
- **Resolution test** Show the full recovery analysis, including the definition of recovery, the distribution of docking scores across pockets, and the comparison with appropriate baselines. Provide the data in the main text or supplementary materials.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The manuscript states that the urea control shows reduced enrichment, indicating that ligands primarily modulate pathway weights rather than define the underlying network topology
- **Evidence pointer** Figure 4; location not provided
- **Concern** The urea control is a critical element of the experimental design, as it is intended to distinguish specific from non-specific binding. However, the quantitative results for the urea control are not presented. It is unclear whether the reduced enrichment is statistically significant, whether it is consistent across all comparison metrics, and whether the choice of urea as a control is appropriate given its known chaotropic properties.
- **Why it matters** The urea control is the primary evidence that the observed pathway conservation is specific to designed ligands rather than a general property of any molecule diffusing on the peptide surface. Without quantitative support, this key distinction is not established.
- **Resolution test** Provide the full enrichment and AUC results for the urea control, including statistical comparisons with the specific ligands. Discuss the choice of urea as a control and its potential limitations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The manuscript reports effective KD values for Aβ42 ligands spanning 4.32 × 10² to 1.08 × 10³ μM, and states these are consistent with low-μM affinities previously reported for G5
- **Evidence pointer** Results section, "A transition-based representation of binding to disordered peptides"; location not provided
- **Concern** The computed effective KD values are 2-3 orders of magnitude higher than the experimental low-μM affinity reported for G5. The manuscript states these are "in line" with experimental values, but this discrepancy is not adequately explained. The conversion from relative to absolute KD values depends on the simulation box concentration, and the relationship between the MSM-derived equilibrium populations and experimental binding affinities requires careful justification.
- **Why it matters** The quantitative agreement between computed and experimental affinities is important for validating the MSM approach. If the computed values are not consistent with experiment, the reliability of the pathway analysis is called into question.
- **Resolution test** Provide a detailed explanation of the KD calculation, including the conversion from relative to absolute values, and a quantitative comparison with experimental data. Discuss the sources of discrepancy and the limitations of the approach.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript describes a prospective screening pipeline that nominates 19 candidates for experimental evaluation
- **Evidence pointer** Results section, "Prospective Application to Aβ42"; Figure 6; location not provided
- **Concern** The prospective screening is presented as a translational validation of the framework, but no experimental results are provided. The manuscript states that experimental measurements "will provide" a test, indicating that the validation is incomplete. The choice of the 19 candidates, the criteria for their selection, and the predicted binding modes are not described in sufficient detail.
- **Why it matters** The prospective application is a key component of the manuscript's translational claim. Without experimental validation, the practical utility of the framework is not demonstrated.
- **Resolution test** Provide the full list of 19 candidates, their predicted affinities, and the selection criteria. If experimental data are available, include them; if not, clearly state that the validation is ongoing and discuss the limitations of the prospective claim.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** MSM construction
- **Evidence pointer** Materials and Methods, "MSM construction"
- **Issue** The choice of quintuplets as the microstate definition is stated to be based on a Chapman-Kolmogorov validation, but the details of this validation are not provided. It is unclear how the quintuplet size was selected and whether alternative definitions were tested.
- **Required correction** Provide the Chapman-Kolmogorov validation results and a brief description of how the quintuplet size was chosen.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Enrichment factor and AUC analyses
- **Evidence pointer** Materials and Methods, "Cross-system pathway comparison"
- **Issue** The enrichment factor formula is not fully specified. The text states "the enrichment factor at cutoff k was calculated as" but the equation is not provided. The statistical significance of the reported enrichment factors is not discussed.
- **Required correction** Provide the complete enrichment factor formula and describe the statistical tests used to assess significance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Ensemble docking
- **Evidence pointer** Materials and Methods, "Ensemble docking"
- **Issue** The selection of 100 frames for receptor templates and the top 5 pockets per frame is described, but the criteria for frame selection and the rationale for these specific numbers are not given.
- **Required correction** Describe the frame selection procedure and justify the choice of 100 frames and 5 pockets per frame.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Prospective screening
- **Evidence pointer** Results section, "Prospective Application to Aβ42"
- **Issue** The text states the TargetMol library contains approximately 2 × 10⁶ compounds, but the abstract and results mention 1.66 million compounds. This discrepancy should be resolved.
- **Required correction** Clarify the exact number of compounds in the TargetMol library and ensure consistency throughout the manuscript.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure references
- **Evidence pointer** Throughout the manuscript
- **Issue** All figures are referenced but not provided. This makes it impossible to assess the quality of the data presentation and the validity of the visual claims.
- **Required correction** Ensure all figures are included in the manuscript submission and are of sufficient quality for review.

## Risk / unsupported claims
- The claim that binding pathways are predominantly protein-defined rather than ligand-defined is not fully supported by the visible evidence, as the key quantitative results are not provided
- The claim that ensemble docking recovers MSM-defined hotspots in 89% of cases is not verifiable without the underlying data
- The claim that the urea control shows reduced enrichment is not quantitatively supported
- The claim that computed effective KD values are consistent with experimental affinities is not adequately justified given the 2-3 order of magnitude discrepancy
- The prospective screening results are presented as a validation but no experimental confirmation is provided
- The claim that the framework has translational value for drug discovery is premature without experimental validation of the nominated candidates