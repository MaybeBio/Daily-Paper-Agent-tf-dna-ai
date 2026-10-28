## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure legends.
- **Assessment boundary** Scientific content, technical soundness, data interpretation, and support for claims. Not an assessment of language editing or formatting.
- **Shared manuscript claim summary** The authors report the discovery of SH6, a small molecule that binds to the C2H2 zinc finger cluster 4 (ZFC4) of the transcription factor SALL4, leading to its degradation via the CUL4A/CRBN ubiquitin-proteasome pathway. This degradation is independent of the IMiD-binding zinc finger cluster 1 (ZFC1), thereby targeting both SALL4 isoforms. SH6 selectively inhibits SALL4-expressing cancer cell growth and shows significant tumor growth inhibition in xenograft and patient-derived xenograft (PDX) models.
- **Visible evidence base** Crystal structure of SALL4 ZFC4/DNA complex (PDB 8CUC); AlphaFold2 models; in silico docking; cell viability assays; Western blotting; dual-luciferase reporter assay; CETSA; SPR; mouse xenograft and PDX studies; mass spectrometry.
- **Missing materials affecting confidence** The full experimental details for the mass spectrometry analysis (e.g., replicates, statistical methods) are not fully described. The synthesis and characterization data for SH6 are incomplete (e.g., purity, yield for final step). The PDX study lacks detailed information on tumor take rates, passage number, and statistical analysis of tumor growth curves. The manuscript does not provide a direct binding assay (e.g., ITC or NMR) between SH6 and the isolated ZFC4 domain, relying instead on cellular and computational data.

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting approach to targeting the transcription factor SALL4 through a non-IMiD binding site. The combination of structural biology, computational screening, and cellular assays is logical. However, the evidence for the proposed mechanism of action, particularly the direct binding of SH6 to ZFC4 and the details of the degradation pathway, is incomplete. The in vivo efficacy data are promising but require more rigorous statistical and experimental detail. The manuscript is not yet suitable for publication in its current form.
- **Who would be interested in the results, and why** Researchers in the fields of targeted protein degradation, transcription factor drug discovery, and cancer biology, particularly those focused on SALL4-driven malignancies like hepatocellular carcinoma. The work may also be of interest to medicinal chemists developing small-molecule degraders.
- **Major strengths**
  - The study addresses a significant unmet need by targeting a transcription factor that is generally considered "undruggable" and is a known cancer driver.
  - The use of a crystallographic structure of the ZFC4-DNA complex to guide computational screening is a rational and potentially powerful approach.
  - The identification of a compound that degrades both SALL4 isoforms, unlike IMiDs, is a key conceptual advance.
  - The in vivo efficacy data, particularly the 87% tumor growth inhibition in a PDX model, are compelling.
- **Major Concerns**
  - **R1-M1** (Blocking): The manuscript lacks direct biochemical evidence for the binding of SH6 to the ZFC4 domain. The claim that SH6 "targets" ZFC4 is based on cellular assays (degradation requires ZFC4) and computational docking, but no direct binding data (e.g., ITC, NMR, or a robust pull-down with purified protein) are presented. The pull-down assay in Figure 4B is in a cellular context and could be indirect.
  - **R1-M2** (Blocking): The specificity of SH6 is not sufficiently established. The mass spectrometry experiment (Figure 4D) identifies SALL4, ZFP91, and ZFP653 as downregulated proteins. While this supports the idea of targeting C2H2 zinc finger proteins, it also raises the question of whether SH6 is a general zinc finger binder. The manuscript does not address the potential off-target effects on other zinc finger proteins, which is a major concern for a proposed therapeutic.
  - **R1-M3** (Blocking): The mechanism of degradation is not fully characterized. While the authors show that SH6-mediated degradation is rescued by MLN4924 and MG132, and that it involves CUL4A and CRBN (via CETSA), the exact molecular mechanism is unclear. Is SH6 acting as a molecular glue, similar to IMiDs, but with a different binding site? Or does it have a different mechanism? The manuscript does not provide a clear model for how SH6 binding to ZFC4 leads to recruitment of the CRL4CRBN E3 ligase.
  - **R1-M4** (Major): The in vivo efficacy data, while promising, are not fully presented. The xenograft study (Figure 5B) shows tumor weights at endpoint, but the tumor growth curves over time are not shown. The PDX study (Figure 5C) is described, but the statistical analysis of the tumor growth curves is not detailed. The manuscript states "tumor growth inhibition of 87%", but the basis for this calculation is not clear.
- **Minor Comments**
  - **R1-m1**: The manuscript would benefit from a more detailed description of the mass spectrometry experiment, including the number of replicates, the statistical test used, and the criteria for identifying significantly changed proteins.
  - **R1-m2**: The synthesis of SH6 is described, but the final yield and purity of the compound are not reported. This is important for reproducibility.
  - **R1-m3**: The authors state that "IMiDs do not inhibit the growth of SALL4-expressing cancer cells" but do not provide data to support this claim in the context of the cell lines used in this study. It would be helpful to show the effect of a known IMiD (e.g., lenalidomide) on the viability of SNU398 cells in the same assay.
  - **R1-m4**: The rationale for using the AlphaFold2 models over the crystal structure for docking is not entirely clear. The authors mention that the crystal structure only covers a small region, but a more direct comparison of the binding site in both models would be useful.
  - **R1-m5**: The manuscript would be strengthened by a discussion of the potential limitations of the CETSA assay, such as the possibility of false positives or the effect of protein expression levels on the thermal shift.
- **Technical failings that need to be addressed before the case is established**
  - Lack of direct binding data for SH6-ZFC4 interaction.
  - Insufficient characterization of SH6 selectivity across the broader zinc finger proteome.
  - Incomplete mechanistic model for how SH6 binding leads to CRL4CRBN recruitment and degradation.
  - Incomplete presentation and statistical analysis of in vivo efficacy data.
- **Assessment against Nature-style criteria**
  - **Originality**: The concept of targeting a non-IMiD zinc finger domain to degrade a transcription factor is novel and represents a potential new avenue for drug discovery. This is a significant conceptual advance over existing approaches.
  - **Scientific importance**: SALL4 is a high-value target in oncology, and a small molecule that can degrade it has substantial therapeutic potential. The work addresses a critical gap in the field.
  - **Interdisciplinary readership**: The work bridges structural biology, computational chemistry, and cancer biology. The findings would be of interest to a broad audience, but the technical details may be more accessible to specialists.
  - **Technical soundness**: The experimental design is generally sound, but the lack of direct binding data and the incomplete mechanistic characterization are significant weaknesses that undermine the central claims.
  - **Readability for nonspecialists**: The manuscript is clearly written and the logic is easy to follow. The figures are informative, though some (e.g., Figure 4D) could be better annotated.
- **Recommendation posture** Currently not established from the provided evidence. The central claims of direct ZFC4 targeting and the specific mechanism of degradation are not sufficiently supported. The manuscript is promising but requires substantial additional experimentation to address the major concerns.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for direct target engagement
- **Claim pointer** The manuscript claims that SH6 "targets" the ZFC4 domain of SALL4, and that this binding is responsible for its degradation.
- **Evidence pointer** Figure 4B (pull-down), Figure 4C (CETSA), Figure 1F (docking)
- **Concern** The evidence for direct binding of SH6 to ZFC4 is indirect. The pull-down assay in Figure 4B is performed in a cellular context and could be mediated by other proteins. The CETSA data show that SH6 stabilizes SALL4, but this could be an indirect effect. The docking studies are computational predictions and require experimental validation. A direct binding assay, such as ITC, MST, or NMR with the purified ZFC4 domain, is essential to support the claim that SH6 directly binds to this domain.
- **Why it matters** The entire premise of the study is that SH6 is a specific binder of ZFC4. Without direct evidence, the mechanism of action remains speculative, and the compound could be acting through a different, non-specific mechanism.
- **Resolution test** Provide a direct binding assay (e.g., ITC, MST, or NMR) showing that SH6 binds to the purified ZFC4 domain with a measurable affinity. A negative control with a mutant ZFC4 domain or a different zinc finger domain would further strengthen the claim.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Selectivity and off-target effects
- **Claim pointer** The manuscript claims that SH6 selectively targets SALL4-expressing cancer cells.
- **Evidence pointer** Figure 4D (mass spectrometry)
- **Concern** The mass spectrometry data show that SH6 downregulates SALL4, ZFP91, and ZFP653, all of which are C2H2 zinc finger proteins. This suggests that SH6 may be a general binder of a subset of zinc finger domains, not specific to SALL4. The manuscript does not address the potential consequences of degrading these other proteins, nor does it assess the selectivity of SH6 across a broader panel of zinc finger proteins. This is a major concern for a proposed therapeutic, as off-target degradation could lead to significant toxicity.
- **Why it matters** A lack of selectivity would undermine the therapeutic potential of SH6 and could explain its effects on cell viability. The manuscript needs to demonstrate that the observed effects are due to SALL4 degradation and not to the degradation of other proteins.
- **Resolution test** Perform a broader selectivity profiling, such as a proteome-wide analysis or a panel of known zinc finger proteins, to determine the extent of SH6's off-target effects. Rescue experiments with a SALL4 mutant that cannot bind SH6 would also help to establish on-target specificity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic understanding of degradation
- **Claim pointer** The manuscript claims that SH6 degrades SALL4 through the CUL4A/CRBN pathway.
- **Evidence pointer** Figure 3A, 3D, 3E, 3F
- **Concern** While the data show that SH6-mediated degradation is rescued by MLN4924 and MG132, and that SH6 stabilizes CUL4A, CRBN, and SALL4 in CETSA, the exact molecular mechanism is not clear. The manuscript does not explain how SH6 binding to ZFC4 leads to the recruitment of the CRL4CRBN E3 ligase. Is SH6 acting as a molecular glue, creating a new protein-protein interaction surface? Or does it induce a conformational change in SALL4 that exposes a degron? The proposed model in the synopsis is speculative and not directly supported by the data.
- **Why it matters** A clear mechanistic understanding is crucial for the rational development of SH6 and for understanding its potential resistance mechanisms. Without this, it is difficult to assess the broader applicability of this approach.
- **Resolution test** Provide direct evidence for the formation of a ternary complex between SH6, SALL4, and CRBN, for example, using pull-down assays with purified components or a proximity ligation assay. Mutational analysis of the ZFC4 domain to identify the SH6 binding site and its role in CRBN recruitment would also be informative.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** In vivo efficacy data
- **Claim pointer** The manuscript claims that SH6 leads to significant tumor growth inhibition in xenograft and PDX models.
- **Evidence pointer** Figure 5B, 5C
- **Concern** The in vivo data are presented in a limited fashion. The xenograft study shows only endpoint tumor weights, not the growth curves over time. The PDX study is described, but the statistical analysis of the tumor growth curves is not detailed. The manuscript states "tumor growth inhibition of 87%", but the basis for this calculation is not clear. More detailed information on the experimental design, including the number of animals, the duration of the study, and the statistical methods used, is needed.
- **Why it matters** The in vivo efficacy is a key selling point of the manuscript. A more rigorous presentation of the data is necessary to support the claims of therapeutic potential.
- **Resolution test** Provide tumor growth curves over time for both the xenograft and PDX studies, with appropriate statistical analysis (e.g., repeated measures ANOVA). Clearly state the method used to calculate tumor growth inhibition.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Mass spectrometry methods
- **Evidence pointer** Methods section, "Mass spec analysis"
- **Issue** The description of the mass spectrometry experiment is brief and lacks critical details, such as the number of biological replicates, the statistical test used to identify significantly changed proteins, and the criteria for hit selection.
- **Required correction** Provide a more detailed description of the mass spectrometry methods, including the number of replicates, the statistical analysis, and the criteria for identifying differentially expressed proteins.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Compound characterization
- **Affected element** SH6 synthesis
- **Evidence pointer** Methods section, "Synthesis of SH6"
- **Issue** The final yield and purity of SH6 are not reported. This is important for reproducibility and for assessing the quality of the compound used in the biological assays.
- **Required correction** Report the final yield and purity (e.g., HPLC purity) of SH6.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Control experiments
- **Affected element** Cell viability assays
- **Evidence pointer** Figure 2A, 2B
- **Issue** The manuscript does not show the effect of a known IMiD (e.g., lenalidomide) on the viability of the SALL4-expressing cell lines used in this study. This would provide a useful benchmark for the activity of SH6 and would support the claim that IMiDs are ineffective in these cells.
- **Required correction** Include a control experiment showing the effect of a known IMiD on the viability of the cell lines used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 4D
- **Evidence pointer** Figure 4D
- **Issue** The volcano plot in Figure 4D is not clearly annotated. It is difficult to identify which proteins are significantly downregulated and by what magnitude.
- **Required correction** Improve the annotation of the volcano plot, clearly labeling the significantly changed proteins and the thresholds used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address the potential limitations of the CETSA assay, such as the possibility of false positives or the effect of protein expression levels on the thermal shift.
- **Required correction** Add a brief discussion of the limitations of the CETSA assay and how they might affect the interpretation of the results.

## Risk / unsupported claims
- The claim that SH6 directly binds to the ZFC4 domain is unsupported by direct biochemical evidence.
- The claim that SH6 is a selective SALL4 degrader is weakened by the observation that it also downregulates other C2H2 zinc finger proteins (ZFP91, ZFP653).
- The proposed mechanistic model of SH6-mediated degradation (as depicted in the synopsis) is speculative and not directly supported by the presented data.
- The claim of "good bioavailability" is based on a single pharmacokinetic study with limited detail.
- The claim of "no significant change" in body weight in the xenograft study is based on endpoint measurements only, which may not capture transient changes during the study.