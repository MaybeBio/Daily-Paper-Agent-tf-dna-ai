## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, experimental section, and conclusions.
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the manuscript. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors report the synthesis of five decorated (2-([2,2'-bipyridin]-6-yl)phenyl)platinum(II) complexes and evaluate their binding to c-myc G-quadruplex and other DNA structures using UV-vis, fluorescence, CD melting, UVRR spectroscopy, and docking simulations. They claim selective binding to c-myc, significant stabilization, and structure-dependent optical responses.
- **Visible evidence base** Full text including all figures, tables, schemes, and experimental methods as provided.
- **Missing materials affecting confidence** Supporting Information (Figures S1–S65, Tables S1–S8) is referenced but not provided. This includes key data such as NMR spectra, CD spectra of DNA constructs, UVRR spectra for 22AG/K+, and detailed docking results. The absence of these materials limits full verification of several claims.

## Reviewer
- **Overall assessment** The manuscript presents a systematic synthetic effort and a multi-technique biophysical evaluation of a new class of neutral organoplatinum G-quadruplex binders. The synthetic chemistry is sound and well-described. The binding data are internally consistent and support the claim of c-myc selectivity. However, several important claims, particularly regarding the molecular basis of binding and enantioselectivity, rely on data not fully presented in the main text. The UVRR interpretation is partially speculative, and the docking results, while informative, are not experimentally validated. The work is of interest to the nucleic acid recognition and bioinorganic chemistry communities, but the current evidence does not fully establish the mechanistic conclusions.
- **Who would be interested in the results, and why** Researchers in nucleic acid chemistry, particularly those studying G-quadruplex ligands; bioinorganic and medicinal chemists interested in platinum-based anticancer agents; and groups developing optical probes for DNA structures. The synthetic methodology and the comparative biophysical dataset will be of practical value.
- **Major strengths** 1. The synthetic route is efficient and modular, allowing access to a diverse set of side-chain decorated complexes from a common intermediate. 2. The use of multiple orthogonal biophysical techniques (UV-vis, fluorescence, CD melting, UVRR) provides a comprehensive dataset. 3. The inclusion of enantiomeric proline derivatives to probe chiral effects is a novel and valuable contribution. 4. The observation of up to 200-fold emission enhancement with c-myc is a significant and potentially useful finding.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that UVRR spectroscopy provides "direct evidence" for end-stacking binding and side-chain interactions with loop residues.
  - **Evidence pointer** Section "UV resonance Raman (UVRR) investigation", Figures 5 and 6, Table 2.
  - **Concern** The UVRR data are presented as difference spectra and intensity changes, but the interpretation relies on band assignments that are partially ambiguous. The shift of the 1608 cm⁻¹ band to 1613 cm⁻¹ is attributed to N1H bending of guanine, but adenine also contributes in this region. The authors acknowledge this but do not provide a deconvolution that separates these contributions. Furthermore, the claim that intensity changes in the thymine band at 1661 cm⁻¹ indicate a change in the dihedral angle between base and sugar is speculative and not directly supported by the data presented. The absence of the raw UVRR spectra and the full deconvolution analysis in the main text or accessible Supporting Information prevents independent verification.
  - **Why it matters** The UVRR data are central to the claim of a specific binding mode (end-stacking with loop interactions). If the interpretation is not robust, the mechanistic conclusions are weakened.
  - **Resolution test** Provide the raw UVRR spectra, the full deconvolution fits, and a control experiment with a DNA sequence lacking the thymine loop to confirm the assignment of the 1661 cm⁻¹ band. Alternatively, use a site-specifically modified DNA (e.g., 2-aminopurine or 8-oxoguanine substitution) to probe stacking interactions more directly.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Claim strength vs. evidence
  - **Claim pointer** The claim that the D-enantiomer (22) has higher affinity for c-myc than the L-enantiomer (21), and that this correlates with different binding modes.
  - **Evidence pointer** Table 1, Figure 2, Section "Binding affinities", Section "Docking simulations".
  - **Concern** The difference in Ka between 21 and 22 is small (e.g., 3.1 vs. 3.6 × 10⁵ M⁻¹ for c-myc) and may be within experimental error. The authors state the difference is "statistically significant" but do not provide error bars or statistical analysis in the main text. The docking results suggest different binding modes for the two enantiomers, but these are computational predictions without experimental validation. The claim of enantioselectivity is interesting but not firmly established.
  - **Why it matters** Enantioselective recognition of G-quadruplexes is a potentially important finding for drug design. Overstating this result could mislead future work.
  - **Resolution test** Provide replicate measurements with standard deviations and a statistical test (e.g., t-test) for the Ka values. Validate the docking predictions with a mutation study (e.g., altering the loop residues predicted to interact with the side chain) or with a different biophysical method sensitive to binding mode (e.g., NMR or native mass spectrometry).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical validation
  - **Claim pointer** The claim that the CD melting experiment shows a bimodal curve indicating "combined stabilizing effects on the G-tetrad core and loop elements."
  - **Evidence pointer** Section "Stabilization induced to c-myc", Figure 4, Supporting Information Figure S52.
  - **Concern** The bimodal melting curve is interpreted as evidence for two distinct binding interactions. However, a bimodal curve can also arise from partial unfolding or from the presence of multiple DNA conformations in solution. The authors do not provide a control experiment to rule out these alternatives. The assignment of the two transitions to specific structural elements (core vs. loop) is not directly supported by the data.
  - **Why it matters** The claim of dual-mode stabilization is a key part of the proposed mechanism of action. If incorrect, the model of how these compounds work is flawed.
  - **Resolution test** Perform melting experiments with a c-myc mutant lacking the loops (e.g., a G-only sequence) to see if the second transition disappears. Alternatively, use a different technique such as differential scanning calorimetry (DSC) to confirm the presence of two thermal transitions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The phrase "decorated (2-([2,2'-bipyridin]-6-yl)phenyl)platinum compounds" is used in the title and abstract. The term "decorated" is vague. It would be clearer to specify the nature of the decoration (e.g., "side-chain functionalized").
  - **Required correction** Replace "decorated" with a more descriptive term such as "side-chain functionalized" or "peripherally modified."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Experimental section, UVRR methods
  - **Evidence pointer** Section "UV resonance Raman study"
  - **Issue** The UVRR experimental conditions are described, but the data processing steps (baseline correction, normalization, deconvolution) are not fully detailed. The equation for calculating percentage change is given, but the fitting parameters for the Voigt functions are not.
  - **Required correction** Provide a more detailed description of the UVRR data processing, including the number of Voigt functions used, initial guesses, and goodness-of-fit parameters.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Table 1
  - **Evidence pointer** Table 1
  - **Issue** The Ka values are presented without error estimates. Given that the authors claim statistical significance for the difference between 21 and 22, error bars or confidence intervals are essential.
  - **Required correction** Add standard deviations or confidence intervals to the Ka values in Table 1, and indicate the number of replicate measurements.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Docking section
  - **Evidence pointer** Section "Docking simulations"
  - **Issue** The docking study uses a single PDB structure (1XAV) with 20 NMR conformers. The authors acknowledge this but do not discuss the limitations of using a single G-quadruplex structure, given the known conformational heterogeneity of c-myc.
  - **Required correction** Add a sentence acknowledging that the docking results are dependent on the chosen PDB structure and that other c-myc conformations may yield different binding modes.
- **Technical failings that need to be addressed before the case is established** 1. Lack of error analysis and statistical testing for the key binding affinity measurements (R1-M2). 2. Insufficient detail in UVRR data processing and interpretation (R1-M1). 3. The bimodal CD melting curve interpretation requires additional control experiments (R1-M3). 4. The Supporting Information, which contains critical data, is not provided for review.
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The use of a neutral organoplatinum scaffold with peptide-mimetic side chains is a reasonable extension of existing work on platinum terpyridine complexes, but the concept of side-chain decoration for G-quadruplex targeting is not entirely new. The enantioselectivity aspect is a novel angle.  
  *Scientific importance*: Moderate. The findings are incremental. The compounds show good c-myc selectivity and stabilization, but the improvement over existing ligands is not dramatic. The mechanistic insights, if validated, would be useful but are not transformative.  
  *Interdisciplinary readership*: Limited. The work will primarily appeal to specialists in nucleic acid chemistry and bioinorganic chemistry. The broader cancer biology community is unlikely to be strongly engaged.  
  *Technical soundness*: The synthetic chemistry is rigorous. The biophysical methods are appropriate, but the interpretation of UVRR and CD melting data needs strengthening. The docking study is preliminary.  
  *Readability for nonspecialists*: The manuscript is clearly written, but the level of detail in the biophysical sections assumes significant prior knowledge. The abstract is accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The synthetic work and the initial biophysical characterization are valuable. However, the mechanistic claims regarding binding mode and enantioselectivity need to be substantiated with additional data and analysis. The manuscript would be suitable for publication in a specialized chemistry journal after major revision.

## Risk / unsupported claims
- The claim of "direct evidence" for end-stacking binding mode from UVRR is not fully supported by the data presented.
- The claim of enantioselective binding between 21 and 22 is not statistically substantiated.
- The interpretation of the bimodal CD melting curve as evidence for dual-site binding (core and loop) is speculative.
- The docking predictions of specific hydrogen bonds and side-chain interactions are not experimentally validated.
- The statement that the compounds are "cell-permeable" (in the conclusions) is not supported by any experimental data in the manuscript.