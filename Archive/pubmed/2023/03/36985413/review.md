## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and conclusions
- **Assessment boundary** Scientific content, methodological rigor, statistical validity, and support of claims by presented evidence
- **Shared manuscript claim summary** The authors report that USP37 expression correlates positively with c-MYC in the ABC subtype of DLBCL, that c-MYC and USP37 interact via specific regions identified by peptide array and docking, and that a designed peptidyl disruptor can block this interaction
- **Visible evidence base** Immunohistochemistry data from 84 DLBCL cases, peptide array and alanine scan results, computational modeling and docking predictions
- **Missing materials affecting confidence** Raw data files, representative immunohistochemistry images with quantification details, peptide array raw data, statistical analysis outputs, validation of antibodies, negative controls, and experimental validation of the proposed peptidyl inhibitor

## Reviewer
- **Overall assessment** The manuscript addresses a potentially interesting question regarding USP-mediated regulation of c-MYC in DLBCL subtypes and proposes a computational approach for therapeutic intervention. However, the study has substantial methodological limitations that undermine the strength of the conclusions. The correlation analysis is based on a small sample size with weak statistical power, the peptide array and docking studies lack experimental validation, and the proposed peptidyl inhibitor is purely computational without any in vitro or in vivo testing. The manuscript would benefit from significant additional work to establish the claims made.
- **Who would be interested in the results, and why** Researchers studying c-MYC regulation in B-cell lymphomas, investigators interested in deubiquitinase biology in cancer, and computational biologists working on protein-protein interaction inhibitors may find aspects of this work relevant. The potential therapeutic angle for DLBCL could interest translational researchers, though the lack of experimental validation limits immediate utility.
- **Major strengths** The study addresses a gap in understanding USP-mediated regulation of c-MYC in DLBCL subtypes. The use of in situ co-expression analysis in clinical samples is appropriate. The computational approach to identify interaction sites and design a peptidyl disruptor is systematic and follows a logical workflow.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The question of USP-mediated c-MYC regulation in DLBCL is relatively novel, though the approach is incremental. Scientific importance: Moderate, as the findings could inform therapeutic strategies, but the evidence is insufficient to establish clinical relevance. Interdisciplinary readership: The work spans oncology, protein biochemistry, and computational biology, which could attract broad interest if properly validated. Technical soundness: Currently inadequate due to statistical weaknesses, lack of experimental validation, and overinterpretation of computational predictions. Readability for nonspecialists: The manuscript is generally readable, though some sections assume familiarity with structural biology concepts.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial revisions and additional experimental work before the claims can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** The authors claim a statistically significant positive correlation between USP37 and c-MYC expression in the ABC subtype of DLBCL (p = 0.0184; r2 = 0.1616).
- **Evidence pointer** Section 2.3, Figure 4A
- **Concern** The reported correlation coefficient (r2 = 0.1616) indicates that USP37 expression explains only approximately 16% of the variance in c-MYC expression. The p-value of 0.0184 is marginally significant, and with a sample size of 34 ABC cases, the statistical power is limited. The authors do not report confidence intervals for the correlation coefficients, nor do they account for multiple comparisons when testing three USPs across two subtypes. Additionally, the choice of Spearman correlation is appropriate for non-parametric data, but the authors do not justify this choice or report whether the data met parametric assumptions.
- **Why it matters** The central claim of the paper rests on this correlation. A weak correlation with marginal significance does not robustly support the conclusion that USP37 specifically regulates c-MYC in the ABC subtype. Without proper multiple testing correction and confidence intervals, the finding may represent a false positive.
- **Resolution test** Provide confidence intervals for all correlation coefficients, apply multiple testing correction (e.g., Bonferroni or FDR), report the raw data distribution, and justify the statistical approach. If the correlation remains significant after correction, the claim would be strengthened.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that the N-terminal region of c-MYC interacts directly with residues within and in proximity of the catalytically active C19 domain of USP37, based on peptide array and docking simulations.
- **Evidence pointer** Sections 2.4, 2.5, 2.9, Figures 5, 9
- **Concern** The peptide array and alanine scan identify putative interaction regions, but these are in vitro binding assays using recombinant proteins and synthetic peptides. The docking simulations are purely computational predictions. No co-immunoprecipitation, pull-down assay, or cellular validation is provided to confirm that c-MYC and USP37 physically interact in DLBCL cells. The authors also do not demonstrate that the identified interaction is functionally relevant for c-MYC stabilization in a cellular context.
- **Why it matters** The proposed mechanism of USP37-mediated c-MYC stabilization in DLBCL requires demonstration of a physical interaction in the relevant cellular context. Computational predictions and peptide arrays alone cannot establish this. Without experimental validation, the mechanistic claim remains speculative.
- **Resolution test** Perform co-immunoprecipitation or proximity ligation assays in DLBCL cell lines to confirm endogenous c-MYC-USP37 interaction. Knockdown or overexpression experiments should demonstrate that USP37 modulates c-MYC protein stability in ABC-type DLBCL cells.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance
- **Claim pointer** The authors claim that the designed peptidyl disruptor could be used for therapeutic intervention against the ABC subtype of DLBCL.
- **Evidence pointer** Section 2.10, Figure 10
- **Concern** The peptidyl disruptor is designed based on computational predictions and docking simulations only. No experimental evidence is provided that the peptide actually disrupts the c-MYC-USP37 interaction in vitro or in cells. There is no data on peptide stability, cell permeability, toxicity, or efficacy in any biological system. The claim that this could be used for therapeutic intervention is therefore unsupported.
- **Why it matters** A therapeutic claim requires at minimum demonstration of target engagement and functional effect in a relevant biological model. The current evidence is entirely computational and does not establish that the peptide has any biological activity.
- **Resolution test** Synthesize the peptide and test its ability to disrupt c-MYC-USP37 interaction in vitro (e.g., by pull-down or surface plasmon resonance). Demonstrate cellular uptake and target engagement in DLBCL cell lines, and assess effects on c-MYC protein levels and cell viability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and reproducibility
- **Claim pointer** The authors claim that expression of c-MYC and USPs was estimated digitally from immunohistochemistry images using ImageJ with the IHC profiler plugin.
- **Evidence pointer** Sections 2.2, 4.4, Figures 2, 3
- **Concern** The methodology for immunohistochemistry quantification is described briefly but lacks critical details. The authors do not report the number of fields analyzed per case beyond "three representative fields," do not describe how fields were selected, and do not provide information on inter-observer variability or validation of the digital scoring against manual scoring. The optical density formula is referenced but not fully explained. No information is provided on antibody validation, including specificity controls or titration experiments.
- **Why it matters** Reproducible and reliable quantification of immunohistochemistry is essential for the correlation analysis. Without detailed methodology and validation, the expression data may not be reliable, which would undermine all downstream analyses.
- **Resolution test** Provide detailed methodology for image acquisition and analysis, including field selection criteria, number of cells analyzed, and validation of the digital scoring approach. Include representative images with corresponding scores and report antibody validation data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Model quality and interpretation
- **Claim pointer** The authors claim that the molecular models of c-MYC and USP37 are structurally plausible and that docking predictions are reliable.
- **Evidence pointer** Sections 2.7, 2.8, 2.9, Figures 6, 7, 8, 9
- **Concern** The manuscript reports that c-MYC and USP37 have large intrinsically disordered regions, which the authors acknowledge limits crystallization. However, the molecular models are built using I-TASSER, which relies on template-based modeling. For proteins with extensive disorder, such models are inherently unreliable. The authors report a ProSA Z-score of -6.99 for the c-MYC model but do not provide comparable quality metrics for the USP37 model. The docking results are presented without clear statistical measures of confidence, and the functional significance of the predicted interface is not experimentally tested.
- **Why it matters** The structural predictions form the basis for the proposed interaction interface and the design of the peptidyl inhibitor. If the models are unreliable, the interaction predictions and inhibitor design may be incorrect, leading to wasted effort in downstream applications.
- **Resolution test** Provide quality metrics for all models, including Ramachandran statistics, ProSA Z-scores, and template alignment details. Validate the predicted interaction interface through mutagenesis studies or hydrogen-deuterium exchange mass spectrometry. If possible, use experimental structures or cryo-EM to confirm the interaction.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of reporting
- **Affected element** Section 2.1, Figure 1
- **Evidence pointer** Section 2.1
- **Issue** The authors state that 84 samples were classified into GCB (50) and ABC (34) subtypes but do not provide a breakdown of how many cases were excluded and why. The figure legend for Figure 1 is not described in the text.
- **Required correction** Clarify the inclusion and exclusion criteria for samples and describe the contents of Figure 1 in the text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.3, Figure 4
- **Evidence pointer** Section 2.3
- **Issue** The authors report r2 values but do not report the actual correlation coefficients (r values) or confidence intervals. The p-value for the GCB subtype USP36 correlation is reported as 0.0414, but the direction of the correlation (negative) is only mentioned in the text, not in the figure.
- **Required correction** Report both r and r2 values with confidence intervals for all correlations. Ensure figure labels and legends clearly indicate the direction of significant correlations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 2.9
- **Evidence pointer** Section 2.9
- **Issue** The dissociation constant is reported as "1.9 × 10−8 Kda" which appears to be a typographical error. The unit should be M (molar) or nM, not Kda.
- **Required correction** Correct the unit for the dissociation constant and ensure all units are consistent throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Section 3
- **Issue** The discussion would benefit from a more thorough comparison with existing literature on USP-mediated regulation of c-MYC in other cancer types and any prior studies on USP37 in lymphoma.
- **Required correction** Expand the discussion to place the findings in the broader context of USP-c-MYC biology and DLBCL pathogenesis.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 2, 5, 9, 10
- **Evidence pointer** Figures 2, 5, 9, 10
- **Issue** The manuscript does not include figure legends in the provided text. Without legends, it is difficult to interpret the figures.
- **Required correction** Ensure all figures have complete legends that describe the experimental conditions, sample sizes, and statistical analyses.

## Risk / unsupported claims
- The claim that USP37 is specifically involved in regulating c-MYC turnover in the ABC subtype of DLBCL is unsupported due to the weak correlation and lack of functional validation.
- The claim that the N-terminal region of c-MYC interacts with the C19 domain of USP37 is based solely on computational predictions and in vitro peptide arrays, without cellular validation.
- The claim that the designed peptidyl disruptor could be used for therapeutic intervention is entirely speculative, as no experimental evidence of efficacy is provided.
- The claim that the molecular models are structurally plausible is not adequately supported by quality metrics for all models.
- The statement that "the findings could further be exploited to develop therapeutic interventions" is premature given the lack of experimental validation at any level.