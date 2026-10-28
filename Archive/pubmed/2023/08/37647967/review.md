## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report that TBBPA is acutely toxic to common carp (96 h LC50 4.2 mg/L, acute toxic level II), bioaccumulates in a tissue-specific manner (liver > gill > brain), and alters AHR pathway gene expression in a tissue-specific way. They further claim that TBBPA acts as a competitive antagonist of AHR transactivation based on in vitro inhibition of TCDD-induced activity, and that in silico docking and molecular dynamics simulations support form-specific binding and differential flexibility relative to TCDD.
- **Visible evidence base** Abstract text only; no experimental details, statistical analyses, or raw data are provided
- **Missing materials affecting confidence** Full methods, all figures and tables, statistical outputs, docking scores, simulation parameters, and any supplementary information

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable ecotoxicological study addressing an understudied non-model species and a widely used flame retardant. The combination of in vivo, in vitro, and in silico approaches is commendable. However, the abstract alone does not provide sufficient detail to evaluate the robustness of the methods, the validity of the statistical analyses, or the strength of the mechanistic conclusions. Several claims, particularly regarding antagonist mechanisms and form-specific interactions, require supporting data that are not visible in the abstract.
- **Who would be interested in the results, and why** Environmental toxicologists, regulatory scientists, and researchers studying endocrine or xenobiotic metabolism disruption in aquatic organisms. The work also has relevance for risk assessment of brominated flame retardants and for those interested in AHR pathway evolution and species-specific responses.
- **Major strengths** The study addresses a relevant environmental contaminant with limited ecotoxicity data. The use of a non-model fish species is a strength. The integration of in vivo, in vitro, and in silico approaches provides a multi-level perspective. The tissue-specific and time-dependent analyses add granularity to the findings.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The topic is not entirely novel, but the focus on common carp and the combined in vivo/in vitro/in silico approach adds some originality.
  - Scientific importance: Moderate. The findings are relevant to environmental risk assessment but do not represent a major conceptual advance.
  - Interdisciplinary readership: Limited. The work is primarily of interest to environmental toxicology and risk assessment communities.
  - Technical soundness: Not assessable from the abstract alone. Key methodological details and statistical validations are missing.
  - Readability for nonspecialists: The abstract is generally readable, though some jargon (e.g., RMSD, transactivation) may require background knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially sound study, but the absence of methodological and statistical detail prevents a definitive assessment. Supportive if technical concerns are resolved upon full manuscript review.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that TBBPA is a competitive antagonist of AHR transactivation based on inhibition of TCDD-induced activity.
- **Evidence pointer** Abstract text, in vitro AHR inhibition assay description
- **Concern** The abstract states that TBBPA inhibited TCDD-induced AHR transactivation and concludes it is a competitive antagonist. However, no data are provided on dose-response relationships, IC50 values, or whether the inhibition was surmountable with increasing TCDD concentrations, which is a key criterion for competitive antagonism. The distinction between competitive and non-competitive antagonism cannot be established from the information given.
- **Why it matters** The mechanistic conclusion is central to the paper's contribution. If the antagonism is not rigorously characterized, the claim of competitive antagonism is unsupported and could mislead subsequent research and risk assessment.
- **Resolution test** Provide full dose-response data for TCDD in the presence and absence of multiple TBBPA concentrations, including statistical analysis of whether the maximum response is depressed (non-competitive) or shifted rightward (competitive). Show IC50 values and confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that in silico analysis showed TBBPA can be docked into the binding cavity with similar poses but with AHR-form-specific interactions, and that molecular dynamics simulations showed greater flexibility for TBBPA compared to TCDD, particularly in ccaAHR1b.
- **Evidence pointer** Abstract text, in silico analysis and molecular dynamics simulation descriptions
- **Concern** The abstract provides no quantitative results from docking or simulations, such as binding energies, interaction residues, RMSD values (beyond a qualitative mention), or comparison metrics across AHR forms. The claim of "form-specific interactions" and "greater flexibility" is not supported by any numerical data or statistical comparison.
- **Why it matters** The in silico component is presented as a key part of the mechanistic argument. Without quantitative outputs and appropriate statistical treatment, the conclusions drawn from the simulations are not verifiable and may be overinterpreted.
- **Resolution test** Provide docking scores, interaction residue maps, and RMSD trajectories with standard deviations for all AHR forms tested. Include statistical comparisons (e.g., ANOVA or equivalent) between TBBPA and TCDD for flexibility metrics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and completeness
- **Claim pointer** The abstract reports bioaccumulation potential following the order liver > gill > brain and gene expression changes that are tissue-specific with minor differences between 3- and 14-day exposure.
- **Evidence pointer** Abstract text, bioaccumulation and gene expression descriptions
- **Concern** The abstract does not specify the number of biological replicates, the statistical tests used, or the magnitude of the reported differences. The claim that differences between 3- and 14-day exposure were "minor" is subjective without effect sizes or p-values. Additionally, the bioaccumulation order is stated without any concentration data or statistical support.
- **Why it matters** The tissue-specific bioaccumulation and gene expression patterns are core findings. Without statistical rigor, the reliability of these conclusions cannot be assessed, and the "minor" time-dependent differences may be an artifact of low statistical power.
- **Resolution test** Provide full statistical reporting, including sample sizes, test types, p-values, and effect sizes for all bioaccumulation and gene expression comparisons. Show that the tissue-specific order is statistically significant and that time-dependent differences are either significant or adequately powered to detect meaningful effects.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract text, first sentence
- **Issue** The phrase "high bioaccumulation potential and toxicity on both humans and wildlife" is vague. The term "high" is not quantified, and the basis for this claim is not referenced.
- **Required correction** Specify the bioaccumulation potential (e.g., log Kow, BCF values) and provide a reference or data supporting the toxicity claim.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Acute toxicity classification
- **Evidence pointer** Abstract text, 96 h LC50 statement
- **Issue** The abstract states the LC50 belongs to "acute toxic level II" but does not specify the classification system used (e.g., OECD, GHS, or Chinese national standard).
- **Required correction** Name the classification system and provide the corresponding category definition for clarity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Precision
- **Affected element** Gene expression description
- **Evidence pointer** Abstract text, AHR pathway gene expression statement
- **Issue** The abstract says "as expected" for cyp1a1 and cyp1b1 upregulation, which is informal and implies a prior hypothesis without stating it. Also, the term "upregulated" is used without specifying the magnitude or fold-change threshold.
- **Required correction** Remove "as expected" and state the hypothesis explicitly. Provide fold-change values or a defined threshold for upregulation.

## Risk / unsupported claims
- The claim that TBBPA is a competitive antagonist is unsupported without dose-response and surmountability data.
- The claim of AHR-form-specific interactions and greater flexibility from in silico analysis is unsupported without quantitative simulation outputs.
- The bioaccumulation order (liver > gill > brain) and tissue-specific gene expression patterns are not statistically verifiable from the abstract.
- The classification of TBBPA as "acute toxic level II" is not verifiable without specifying the classification system.
- The statement that TBBPA has "high bioaccumulation potential" is not supported by data in the abstract.