## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusions. No supplementary figures or tables were provided for assessment.
- **Assessment boundary** The review is limited to the content presented in the supplied manuscript text. Claims referring to supplementary materials, external datasets, or unpublished data are noted but not independently verifiable.
- **Shared manuscript claim summary** The authors propose that BRF2, a subunit of RNA polymerase III, is a viable therapeutic target in cancer. They report in silico screening of a drug library to identify inhibitors of the BRF2-TBP-DNA complex, with bexarotene selected as a candidate. They further present experimental data suggesting BRF2 is involved in the DNA damage response and that bexarotene reduces oxidative-stress-induced BRF2 levels and cancer cell proliferation.
- **Visible evidence base** TCGA pan-cancer expression and copy number analyses; correlation analyses with genomic instability features, signaling pathways, and immune infiltration; molecular docking and molecular dynamics simulations; cell viability, proliferation, ROS, and immunoblotting experiments in MCF10A, MCF7, MDA-MB-231, SUM159PT, and HeLa cells.
- **Missing materials affecting confidence** Supplementary figures and tables (referenced as S1–S7 and Table S1) were not provided. Details of the virtual screening protocol, including the complete list of screened compounds and scoring functions, are partially described. Raw data for Western blots, dose-response curves, and statistical analyses are not shown in the text. The identity and purity of bexarotene, and the specific conditions for ROS assays, are not fully detailed.

## Reviewer
- **Overall assessment** The manuscript addresses an important question, namely whether BRF2 can be targeted therapeutically using repurposed drugs. The bioinformatics analyses are broad and the identification of bexarotene as a potential inhibitor is of interest. However, the experimental validation is limited and does not convincingly demonstrate that bexarotene acts through BRF2 to exert its effects. The claim that BRF2 is a novel player in the DNA damage response is supported by correlative data but lacks mechanistic depth. The manuscript would benefit from more rigorous experimental evidence, including direct binding assays, genetic rescue experiments, and a clearer demonstration of on-target specificity.
- **Who would be interested in the results, and why** Researchers in cancer biology, particularly those studying RNA polymerase III transcription, oxidative stress responses, and drug repurposing. Clinicians interested in novel applications of FDA-approved drugs for cancers with elevated BRF2 expression may also find the work relevant.
- **Major strengths** The study addresses an underexplored target, BRF2, and leverages publicly available datasets to support its relevance across multiple cancer types. The combination of computational screening with experimental validation is a reasonable approach. The identification of bexarotene, an approved drug, as a potential BRF2 inhibitor has translational appeal.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The concept of targeting BRF2 is relatively novel, but the approach of using in silico screening and repurposed drugs is not new. The claim of a novel role for BRF2 in DNA damage response is interesting but not fully substantiated.  
  - **Scientific importance** Potentially high, if BRF2 proves to be a druggable target. However, the current evidence does not establish this convincingly.  
  - **Interdisciplinary readership** The work spans computational biology, cancer biology, and pharmacology, which could appeal to a broad audience. However, the limited experimental depth may reduce its impact.  
  - **Technical soundness** The computational methods are standard, but the experimental validation is incomplete. Key controls and mechanistic experiments are missing.  
  - **Readability for nonspecialists** The manuscript is generally well written, but some sections, particularly the methods, are dense and may be challenging for nonspecialists. The figures are not assessable from the text alone.

## Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Experimental validation  
- **Claim pointer** The authors claim that bexarotene inhibits BRF2 function and reduces cancer cell proliferation through BRF2-dependent mechanisms.  
- **Evidence pointer** Section 3.7, Figures 7G–7K  
- **Concern** The experimental data do not demonstrate that bexarotene's effects are mediated by BRF2. The authors show that bexarotene reduces proliferation and ROS levels, but they do not show that this is dependent on BRF2 expression. The lack of a rescue experiment, where BRF2 is overexpressed in the presence of bexarotene, or a direct binding assay, leaves the mechanism unresolved.  
- **Why it matters** Without evidence of on-target specificity, the conclusion that bexarotene is a BRF2 inhibitor is not supported. The observed effects could be due to off-target activities, which is particularly relevant given that bexarotene is a known RXR agonist.  
- **Resolution test** Provide direct evidence of bexarotene binding to BRF2, such as surface plasmon resonance or isothermal titration calorimetry. Additionally, perform rescue experiments where BRF2 is ectopically expressed in knockdown cells to see if bexarotene's effects are reversed.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Mechanistic insight  
- **Claim pointer** The authors claim that BRF2 is a novel player in the DNA damage response pathway.  
- **Evidence pointer** Section 3.2, Figures 2A–2J  
- **Concern** The evidence for BRF2's role in DNA damage response is largely correlative. The authors show that BRF2 is upregulated after DNA damage and that its knockdown leads to persistent DNA damage, but they do not explore the underlying mechanism. It is unclear whether BRF2 is directly involved in DNA repair or if the observed effects are secondary to other cellular changes.  
- **Why it matters** The claim of a novel function for BRF2 in DNA damage response is a key part of the manuscript's significance. Without mechanistic insight, the claim remains speculative.  
- **Resolution test** Investigate whether BRF2 interacts with known DNA repair proteins, and assess the kinetics of DNA repair in BRF2-depleted cells using more direct assays, such as comet assays or pulsed-field gel electrophoresis.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Data completeness  
- **Claim pointer** The authors claim that bexarotene reduces oxidative-stress-induced BRF2 levels.  
- **Evidence pointer** Section 3.7, Figure 7I  
- **Concern** The Western blot data are not quantified, and the representative blots are not shown in the text. It is unclear whether the observed reduction in BRF2 levels is statistically significant and reproducible across biological replicates.  
- **Why it matters** Quantification of Western blots is essential to support the claim. Without it, the conclusion is not robust.  
- **Resolution test** Provide densitometric analysis of at least three independent experiments, with statistical tests, and include representative blots in the main figures.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Specificity of drug effect  
- **Claim pointer** The authors suggest that bexarotene's anti-proliferative effect is due to BRF2 inhibition.  
- **Evidence pointer** Section 3.7, Figure 7G  
- **Concern** The authors note that bexarotene's anti-proliferative effect is non-selective for BRF2 expression, as both control and BRF2-knockdown cells show reduced viability. This undermines the claim that the drug acts through BRF2.  
- **Why it matters** If the effect is non-selective, the therapeutic rationale for targeting BRF2 with bexarotene is weakened.  
- **Resolution test** Use a more specific approach, such as a BRF2 inhibitor with a different scaffold, or perform a competition assay with excess BRF2 peptide to show specificity.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The authors claim that BRF2 expression correlates with poor survival in ER-positive tumors.  
- **Evidence pointer** Section 3.1, Supplementary Figure S1H  
- **Concern** The survival analysis is only presented in supplementary materials, which were not provided. The statistical methods and covariates used in the analysis are not described in the text.  
- **Why it matters** Survival analyses are prone to confounding and require careful statistical adjustment. Without details, the claim is not assessable.  
- **Resolution test** Provide the full survival analysis, including hazard ratios, confidence intervals, and adjustment for relevant covariates, in the main text or a clearly described supplementary file.

## Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 2.3  
- **Evidence pointer** "Eight thousand molecular dockings were performed"  
- **Issue** The number of dockings is inconsistent with the stated library size of 8,770 compounds. Clarify whether each compound was docked once or multiple times.  
- **Required correction** Specify the number of dockings per compound and the total number of unique compounds screened.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Section 2.4  
- **Evidence pointer** "The protonation state of the Gromacs package was used to calculate the total charge of the protein."  
- **Issue** The method for assigning protonation states is vague. It is unclear whether a specific tool (e.g., PROPKA) was used.  
- **Required correction** Provide details on the protonation state assignment method and the software version used.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Section 3.1  
- **Evidence pointer** "BRF2 is significantly overexpressed in many tumor types"  
- **Issue** The text does not specify which cancer types show the most significant overexpression, nor does it provide effect sizes.  
- **Required correction** Include a summary table or heatmap of BRF2 expression across cancer types, with statistical significance and fold changes.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Section 3.6  
- **Evidence pointer** "The binding free energy and its related components, acquired from the MM/PBSA calculation of the ligand-BRF2 complexes, are listed in Table 3."  
- **Issue** The text states that electrostatic energy contributed the most, but the table is not provided. It is unclear how the authors determined this.  
- **Required correction** Include Table 3 in the main text or provide a summary of the energy components in the text.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Language  
- **Affected element** Section 3.4  
- **Evidence pointer** "principle component analysis"  
- **Issue** The correct term is "principal component analysis."  
- **Required correction** Correct the terminology throughout the manuscript.

## Risk / unsupported claims
- The claim that bexarotene is a potential BRF2 inhibitor is not supported by direct binding or functional rescue experiments.
- The claim that BRF2 is a novel player in the DNA damage response is based on correlative data and lacks mechanistic evidence.
- The claim that bexarotene reduces oxidative-stress-induced BRF2 levels is not quantified and may not be reproducible.
- The survival analysis correlating BRF2 expression with poor prognosis is not assessable without the supplementary data and statistical details.
- The statement that "more than 3500 FDA-approved drugs" were screened is inconsistent with the stated library size of 8,770 compounds; the number of unique compounds screened is unclear.