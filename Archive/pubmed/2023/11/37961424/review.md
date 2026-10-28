## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv 2023.11.14, DOI 10.1101/2023.10.27.564484)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No line numbers were available; section and figure references are used as provided.
- **Shared manuscript claim summary** The authors investigate the N-terminal low-complexity domain of EWS (EWSLCD), a FET family protein, to characterize its conformational ensemble, self-association, and phase separation behavior. They combine NMR (relaxation, PRE), analytical ultracentrifugation, SEC, turbidity/microscopy, and all-atom and coarse-grained simulations to propose that tyrosine residues, particularly in the N- and C-terminal regions, drive intramolecular contacts in the dilute phase that are recapitulated as intermolecular contacts in the condensed phase, and that this mechanism distinguishes EWS from FUS.
- **Visible evidence base** Abstract; Introduction; Materials and Methods (protein purification, fluorescent labeling, microscopy/turbidity, temperature sensitivity, pelleting, AUC, SEC, NMR relaxation, diffusion, PRE, CG and AA simulations, condensed phase simulations, relaxation calculation); Results sections (EWS domain architecture, physicochemical properties, chain dynamics/self-association, tyrosine-mediated phase separation, tyrosine effects on dynamics, condensed phase contacts); Discussion; Supplementary figure/table references (Supp. Figs. 1–7, Supp. Tables 1–2); Figure references (Figs. 1–6, Fig. 7 mentioned in Discussion).
- **Missing materials affecting confidence** Main-text figures and supplementary figures/tables were not provided. Specific numerical values for key results (e.g., Csat values, sedimentation coefficients, PRE magnitudes, R2 differences) are not fully reported in the text. No statistical analysis details or error bar definitions are given. The manuscript is a preprint and has not undergone peer review.

## Reviewer
- **Overall assessment** This manuscript presents a multi-technique study of the EWS low-complexity domain, addressing an important gap in the FET protein field where FUS has been the primary model. The combination of solution NMR, hydrodynamic methods, and simulations is appropriate and potentially powerful. The central claim that tyrosine-driven contacts in the dilute phase inform condensed-phase interactions is plausible and of interest. However, the evidence as presented is incomplete: key quantitative results are not reported in the text, the connection between dilute-phase PRE data and phase separation behavior is inferred rather than directly demonstrated, and the comparison to FUS is largely qualitative. The manuscript would benefit from clearer presentation of quantitative data and a more rigorous treatment of the relationship between intramolecular contacts and phase separation propensity.
- **Who would be interested in the results, and why** Researchers studying biomolecular condensates and liquid-liquid phase separation, particularly those focused on FET family proteins (FUS, EWS, TAF15) and their roles in neurodegeneration and cancer. The work is also relevant to those interested in the sequence determinants of phase separation in intrinsically disordered proteins and to computational biologists developing and testing models for IDP conformational ensembles and condensed phases.
- **Major strengths** 1) Addresses a significant knowledge gap by studying EWS, which is under-characterized relative to FUS. 2) Integrates multiple complementary experimental and computational techniques. 3) The finding that EWS and FUS LCDs differ in their conformational preferences and interaction patterns is potentially important for understanding functional divergence within the FET family. 4) The use of atomistic simulations in both dilute and condensed phases is ambitious and provides a framework for interpreting experimental data.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that "tyrosine residues primarily drive the interactions vital for EWSLCD phase separation" and that mutating tyrosines increases solubility and shifts the phase boundary.
  - **Evidence pointer** Results sections "Tyrosine Residues Mediate Phase Separation of the EWSLCD" and "Tyrosine Residues Affect the Dynamics of EWSLCD"; Figures 4 and 5; location not provided for specific data points.
  - **Concern** The phase diagrams and pelleting assays are described qualitatively. No numerical Csat values, error bars, or statistical comparisons are provided in the text. The claim that specific tyrosine mutations (Y170S/Y172S, 7YS) increase solubility is not supported by quantitative data. The relationship between the number of tyrosines mutated and the observed effect is not systematically presented.
  - **Why it matters** The central conclusion of the paper rests on the quantitative effect of tyrosine mutations on phase separation propensity. Without these data, the claim cannot be evaluated.
  - **Resolution test** Provide quantitative phase boundary data (e.g., Csat values with errors) for WT and all mutants, with statistical tests. Show representative images and turbidity curves. Report the fraction of soluble protein in pelleting assays with replicates.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim-data alignment
  - **Claim pointer** The authors state that "interactions observed in the dilute phase inform on atomic interactions driving phase separation" and that condensed-phase simulations show "a strong correlation" between pairwise residue type contacts in condensed and dilute phases.
  - **Evidence pointer** Results section "Condensed Phase Intermolecular Contacts Mimic Intramolecular Interactions in the Dilute Phase"; Figure 6; location not provided for correlation coefficients.
  - **Concern** The correlation between dilute and condensed phase contacts is stated but the correlation coefficient and its statistical significance are not reported. The claim that dilute-phase interactions "inform" phase separation is an inference; the data show correlation, not causation. The authors note that experimental condensed-phase NMR was challenging and did not succeed, so the simulation results are not validated against experimental condensed-phase data.
  - **Why it matters** The transferability of dilute-phase information to the condensed phase is a key conceptual claim of the paper. Without quantitative correlation metrics and experimental validation, this remains speculative.
  - **Resolution test** Report the correlation coefficient (e.g., Pearson or Spearman) with confidence intervals for the contact map comparison. Discuss the limitations of inferring phase separation mechanisms from dilute-phase data. If possible, provide experimental validation of condensed-phase contacts (e.g., solid-state NMR, cryo-EM, or other approaches).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors use PRE NMR to infer intramolecular contacts and state that "tyrosine residues primarily drive the interactions vital for EWSLCD phase separation" based on PRE data.
  - **Evidence pointer** Results section "Peptide Chain Dynamics and Self-Association of the EWSLCD"; Figure 3; Supp. Fig. 4; location not provided for PRE data.
  - **Concern** The PRE data are presented qualitatively. The magnitude of PRE effects, the specific residues affected, and the comparison between WT and mutants are not quantified. The authors note that intermolecular PREs were not significant, but the interpretation of intramolecular PREs in terms of "contacts" requires a quantitative framework (e.g., ensemble refinement against PRE data). The comparison of simulated <r−6> to experimental PRE data is described as "qualitatively similar" without quantitative metrics.
  - **Why it matters** PRE is a powerful technique, but its interpretation requires careful quantitative analysis. Without reporting the actual PRE rates, the strength of the contacts, and the goodness-of-fit between experiment and simulation, the conclusions about specific interactions are not well supported.
  - **Resolution test** Report PRE rates (Γ2) as a function of residue number for WT and mutants, with errors. Provide a quantitative comparison between experimental PRE and simulated <r−6> values (e.g., R² or χ²). Show that the observed PREs are specific to intramolecular interactions and not artifacts of aggregation or transient oligomerization.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparative analysis
  - **Claim pointer** The authors emphasize differences between EWS and FUS, stating that EWS has "distinct differences in both amino acid composition and distribution" and that the conformational ensemble of EWSLCD contrasts with FUS.
  - **Evidence pointer** Results section "EWS Domain Architecture and Differences between FUS and EWS"; Figure 1; Supp. Fig. 1; location not provided.
  - **Concern** The comparison to FUS is largely based on sequence composition and qualitative descriptions of conformational preferences. No direct comparative experiments (e.g., FUS LCD under identical conditions) are presented. The claim that EWS is "more prone to phase separate" than FUS is stated but not supported by direct comparative measurements.
  - **Why it matters** The paper's framing emphasizes molecular diversity within the FET family. A direct quantitative comparison with FUS under matched conditions would strengthen this claim.
  - **Resolution test** Perform side-by-side phase separation assays and hydrodynamic measurements with FUS LCD under identical buffer conditions. Report quantitative Csat values for both proteins. If direct comparison is not feasible, clearly state the limitations of the comparison.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results section "Physiochemical Properties of EWSLCD"
  - **Evidence pointer** Figure 2; location not provided.
  - **Issue** The term "physiochemical" should be "physicochemical." The section describes turbidity, pelleting, and microscopy but the organization is somewhat scattered.
  - **Required correction** Correct the typo. Consider reorganizing the section to separate solution-state characterization (SEC, AUC, NMR) from phase separation assays (turbidity, microscopy, pelleting).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods section "Nuclear Magnetic Resonance"
  - **Evidence pointer** Location not provided.
  - **Issue** The NMR relaxation experiments are described, but key acquisition parameters (e.g., relaxation delays, number of scans, temperature calibration) are not fully specified. The T1ρ spin-lock field strength is not given.
  - **Required correction** Provide complete acquisition parameters for all NMR experiments, including T1, T1ρ, heteronuclear NOE, and PRE experiments.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results section "Condensed Phase Intermolecular Contacts Mimic Intramolecular Interactions in the Dilute Phase"
  - **Evidence pointer** Figure 6; location not provided.
  - **Issue** The correlation between condensed and dilute phase contacts is stated but the figure is not available for review. The authors should ensure the figure clearly shows the correlation and includes the correlation coefficient.
  - **Required correction** Ensure Figure 6 includes a scatter plot with correlation coefficient and confidence interval. Add a supplementary figure with the full contact maps for both phases.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion
  - **Evidence pointer** Location not provided.
  - **Issue** The discussion of the yin-yang hypothesis and the role of phase separation in EWS::FLI1 function is brief. The authors could more thoroughly contextualize their findings within the existing literature on FET protein phase separation and oncogenic fusion proteins.
  - **Required correction** Expand the discussion to more thoroughly address how the findings relate to previous studies on FUS and other FET proteins, and the implications for understanding EWS::FLI1 oncogenicity.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative phase separation data), R1-M2 (quantitative correlation between dilute and condensed phase contacts), R1-M3 (quantitative PRE analysis and validation).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The study addresses an under-characterized protein (EWS) and provides a multi-technique approach, but the general concept that tyrosine residues drive phase separation in FET proteins is not new. The specific finding of domain-like conformational behavior in EWSLCD is potentially novel.  
  *Scientific importance*: Moderate. The work contributes to understanding FET protein diversity and the molecular basis of EWS::FLI1 oncogenicity, but the direct implications for disease mechanisms are not fully developed.  
  *Interdisciplinary readership*: Moderate. The work will appeal to biophysicists, structural biologists, and cell biologists interested in phase separation, but the presentation is heavily technical and may not be accessible to a broad audience.  
  *Technical soundness*: The combination of techniques is appropriate, but the lack of quantitative data presentation and the absence of experimental validation for condensed-phase simulations are significant weaknesses.  
  *Readability for nonspecialists*: The manuscript is written for a specialist audience. The abstract is accessible, but the results and methods sections assume significant background knowledge. The authors should consider adding a brief explanation of key concepts (e.g., PRE, Csat) for a broader readership.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question and uses appropriate techniques, but the current presentation lacks the quantitative rigor needed to support the central claims. If the authors provide quantitative phase separation data, statistical analysis, and a more rigorous treatment of the dilute-condensed phase relationship, the manuscript could make a valuable contribution.

## Risk / unsupported claims
- The claim that "tyrosine residues primarily drive the interactions vital for EWSLCD phase separation" is not quantitatively supported by the data presented in the text.
- The claim that "interactions observed in the dilute phase inform on atomic interactions driving phase separation" is an inference not directly demonstrated.
- The statement that EWSLCD is "more prone to phase separate" than FUS is not supported by direct comparative measurements.
- The claim that condensed-phase simulations show "a strong correlation" with dilute-phase contacts is not supported by reported correlation coefficients or statistical tests.
- The statement that "the C-terminal region forms the highest total number of contacts" is based on simulation data that are not quantitatively presented in the text.
- The claim that "aging" of droplets leads to a less liquid-like state is based on FRAP data that are described qualitatively without quantitative recovery percentages or time constants.