## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, and conceptual novelty of the claim that GSTP alleviates acute lung injury via S-glutathionylation of KEAP1 at C434 and subsequent NRF2 pathway activation
- **Shared manuscript claim summary** The authors propose that GSTP protects against LPS-induced acute lung injury by catalyzing S-glutathionylation of KEAP1 at cysteine 434, which disrupts KEAP1-NRF2 binding, promotes NRF2 nuclear translocation, and activates antioxidant gene expression, thereby reducing oxidative stress and inflammation
- **Visible evidence base** In vitro cell culture experiments (HPAEpiCs, BEAS-2B, A549, HEK293), Gstp1/2/3 knockout mouse model, AAV-mediated GSTP overexpression mouse model, co-immunoprecipitation, western blotting, immunofluorescence, LC-MS/MS, molecular docking, molecular dynamics simulations, site-directed mutagenesis, luciferase reporter assays, histopathology
- **Missing materials affecting confidence** Supplementary figures (Fig. S1, S2, S3) referenced but not provided; raw mass spectrometry data not shown; detailed statistical outputs not provided; no information on antibody validation for S-glutathionylation detection; no data on NRF2 target gene expression at mRNA level

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting mechanism linking GSTP-mediated S-glutathionylation of KEAP1 to NRF2 activation in acute lung injury. The combination of in vitro, in vivo, and computational approaches is commendable. However, several technical concerns regarding the specificity of the S-glutathionylation detection, the causal relationship between C434 modification and NRF2 activation, and the physiological relevance of the findings require careful consideration. The study is a solid contribution to the field of redox biology and ALI research, but the novelty is incremental given prior reports of KEAP1 S-glutathionylation in other contexts.
- **Who would be interested in the results, and why** Researchers in the fields of redox biology, pulmonary medicine, and inflammatory disease would find these results relevant. The identification of a specific cysteine residue in KEAP1 targeted by GSTP-mediated S-glutathionylation could inform therapeutic strategies for ALI and other oxidative stress-related conditions. The study also contributes to the broader understanding of how protein S-glutathionylation regulates signaling pathways.
- **Major strengths**
  1. Comprehensive approach combining in vitro, in vivo, and computational methods
  2. Identification of a specific cysteine residue (C434) as the functional S-glutathionylation site
  3. Use of both loss-of-function (Gstp knockout) and gain-of-function (AAV-GSTP) mouse models
  4. Molecular dynamics simulations provide mechanistic insight into how C434 modification affects KEAP1-NRF2 binding
  5. Clinical relevance to ALI, a condition with high mortality and limited therapeutic options
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of S-glutathionylation detection
  - **Claim pointer** The authors claim that GSTP catalyzes S-glutathionylation of KEAP1 at C434 and that this modification is functionally significant
  - **Evidence pointer** Figure 4A-D, Figure 5A-B, Methods section "Detection of KEAP1 S-glutathionylation"
  - **Concern** The detection of S-glutathionylation relies on immunoprecipitation with an anti-glutathione antibody followed by western blotting. This approach has well-documented limitations including potential cross-reactivity, difficulty in distinguishing true S-glutathionylation from other thiol modifications, and the possibility of artifactual oxidation during sample preparation. The authors do not provide validation of the anti-glutathione antibody specificity, nor do they include controls such as competition experiments with free glutathione or mass spectrometry confirmation of the modified peptides in cellular contexts. The LC-MS/MS identification of C368, C434, and C613 as S-glutathionylation sites was performed on recombinant protein, which may not reflect the cellular context.
  - **Why it matters** The central mechanistic claim of the paper rests on the specificity and reliability of S-glutathionylation detection. If the detection method is not rigorously validated, the conclusion that GSTP specifically catalyzes KEAP1 S-glutathionylation at C434 is not firmly established.
  - **Resolution test** Provide validation of the anti-glutathione antibody including peptide competition assays, include negative controls with thiol-blocking agents (e.g., NEM pretreatment), confirm S-glutathionylation by mass spectrometry on endogenous KEAP1 from cells, and show that the signal is sensitive to reducing agents in a controlled manner.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Causal relationship between C434 S-glutathionylation and NRF2 activation
  - **Claim pointer** The authors claim that S-glutathionylation at C434 is the key modification that promotes KEAP1-NRF2 dissociation and NRF2 nuclear translocation
  - **Evidence pointer** Figure 5A-D, Figure 6D-K
  - **Concern** The site-directed mutagenesis experiments replace C434 with serine (C434S), which eliminates the thiol group but does not specifically test the effect of S-glutathionylation. The C434S mutation could affect KEAP1 structure or function independent of S-glutathionylation. Furthermore, the authors do not demonstrate that the C434S mutant is resistant to GSTP-mediated S-glutathionylation while other mutants are not, which would be a more direct test. The molecular dynamics simulations show conformational changes but do not establish causality.
  - **Why it matters** The paper's central claim is that S-glutathionylation at C434 specifically drives NRF2 activation. Without demonstrating that the effect is specifically due to S-glutathionylation at this residue, alternative explanations (e.g., general thiol reactivity, structural effects of the mutation) cannot be excluded.
  - **Resolution test** Perform rescue experiments where C434S mutant is tested for its ability to restore NRF2 activation in GSTP-overexpressing cells; use a C434A mutant as an additional control; demonstrate that GSTP-mediated S-glutathionylation is specifically lost at C434 in the C434S mutant; consider using a glutathionylation-mimetic mutation (e.g., C434D) to test for constitutive activation.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Physiological relevance of in vitro findings
  - **Claim pointer** The authors claim that GSTP-mediated KEAP1 S-glutathionylation and NRF2 activation protect against LPS-induced ALI in vivo
  - **Evidence pointer** Figure 2A-K, Figure 7A-M
  - **Concern** The in vivo experiments demonstrate correlations between GSTP expression and markers of inflammation and oxidative stress, but do not directly establish that the protective effect is mediated through KEAP1 S-glutathionylation at C434. The AAV-GSTP overexpression model shows increased KEAP1 S-glutathionylation and NRF2 activation, but the authors do not test whether this effect is dependent on C434 in vivo. Additionally, the Gstp knockout mice may have developmental or compensatory changes that confound interpretation.
  - **Why it matters** The translational relevance of the proposed mechanism depends on demonstrating that the in vitro-identified C434 modification is functionally important in the intact organism.
  - **Resolution test** Generate or use knock-in mice with C434S mutation in KEAP1 to test whether GSTP-mediated protection is lost; alternatively, use a KEAP1 C434S overexpression approach in vivo to compete with endogenous KEAP1.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Quantitative analysis and statistical rigor
  - **Claim pointer** The authors claim significant differences between groups based on stated p-values
  - **Evidence pointer** All figures with quantitative data
  - **Concern** The manuscript does not provide details on the number of independent biological replicates for each experiment, whether the data meet assumptions for parametric testing, or how multiple comparisons were handled. The figure legends state "n = 3" or "n = 8 or 9 mice/group" but do not specify whether these represent biological or technical replicates. No information is provided on the statistical tests used for each comparison beyond the general statement in Methods.
  - **Why it matters** Rigorous statistical analysis is essential for the validity of the conclusions, particularly for the in vivo studies where inter-animal variability can be substantial.
  - **Resolution test** Provide complete statistical details including exact n values for each experiment, tests used, and how assumptions were verified; consider showing individual data points in figures.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 6
  - **Evidence pointer** Figure 6A-K
  - **Issue** The computational results are presented in a complex manner that is difficult to follow. The relationship between the docking results, MD simulations, and the functional conclusions is not clearly explained.
  - **Required correction** Simplify the presentation of computational results, provide a clearer schematic summary of the key findings, and ensure the figure legend explains all panels adequately.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness of methods
  - **Affected element** Methods section
  - **Evidence pointer** Methods section "Computational modeling"
  - **Issue** The methods for molecular docking and MD simulations lack sufficient detail for reproducibility. No information is provided on software versions, force field parameters, simulation time, or convergence criteria.
  - **Required correction** Provide complete details of the computational methods including software versions, parameters, and analysis protocols.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section
  - **Issue** The authors do not discuss potential limitations of their study, such as the specificity of the anti-glutathione antibody, the possibility of off-target effects of GSTP, or the relevance of the LPS model to human ALI.
  - **Required correction** Add a limitations paragraph acknowledging these issues and discussing how they might affect interpretation of the results.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data availability statement
  - **Evidence pointer** Data availability section
  - **Issue** The statement "Data will be made available on request" is vague and does not specify what data will be shared or under what conditions.
  - **Required correction** Provide a more detailed data availability statement, including raw mass spectrometry data deposition in a public repository.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Validation of S-glutathionylation detection method
  - R1-M2: Direct evidence that C434 S-glutathionylation is the causal modification driving NRF2 activation
- **Assessment against Nature-style criteria**
  - **Originality** Moderate. While the specific combination of GSTP-mediated KEAP1 S-glutathionylation at C434 in ALI has not been previously reported, S-glutathionylation of KEAP1 and its role in NRF2 regulation has been described in other contexts. The identification of a specific residue adds some novelty but is not transformative.
  - **Scientific importance** Moderate. The findings could have implications for understanding ALI pathogenesis and potentially for therapeutic development, but the clinical relevance remains speculative. The mechanism is an extension of known redox regulation of KEAP1-NRF2 rather than a fundamentally new pathway.
  - **Interdisciplinary readership** Limited. The work is primarily of interest to redox biologists and pulmonary researchers. The computational component is supportive rather than central and is unlikely to attract a broad computational audience.
  - **Technical soundness** The experimental design is generally sound, but the S-glutathionylation detection methodology requires additional validation. The computational analyses are appropriate but not deeply integrated with the experimental findings.
  - **Readability for nonspecialists** The manuscript is clearly written and the logic is easy to follow. However, the computational results section is dense and may be challenging for readers without a computational background.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a plausible and potentially important mechanism, but the central claim regarding C434-specific S-glutathionylation requires stronger experimental support. The authors should address the concerns regarding detection methodology and provide more direct evidence for the causal role of C434 modification.

## Risk / unsupported claims
- The claim that C434 is the "key" S-glutathionylation site is not fully supported, as the authors identified three sites (C368, C434, C613) but only tested C434 functionally
- The claim that GSTP directly catalyzes S-glutathionylation of KEAP1 in vivo is inferred from correlation in knockout/overexpression models but not directly demonstrated
- The molecular dynamics simulation conclusions about "unstable binding" are based on computational predictions that are not experimentally validated
- The therapeutic potential of targeting GSTP for ALI treatment is speculative and not supported by direct evidence
- The statement that "GSTP inhibited KEAP1-NRF2 interaction by promoting PSSG process of KEAP1" is presented as established fact but the evidence is correlative