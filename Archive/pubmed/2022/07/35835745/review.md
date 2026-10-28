## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and supplementary figure/table legends
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report the X-ray crystal structure of a monomeric mycobacteriophage immunity repressor (from cluster A bacteriophage TipsytheTRex) bound to an asymmetric DNA sequence, revealing two independent DNA-binding domains within a single polypeptide. The structure is supported by SEC-SAXS-MALS, DNA-binding assays, in vivo immunity assays, and molecular dynamics simulations. The authors propose a model for how dual DNA-binding domains enable regulation of both transcription initiation and elongation, and how sequence diversity in the Stoperator domain may facilitate evolution of new immunity specificities.
- **Visible evidence base** Crystal structure (native and selenomethionine datasets), SEC-SAXS-MALS data, EMSA binding data, in vivo immunity assays, molecular dynamics simulations, sequence alignments (referenced as Supplementary Fig. 1)
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided in the submitted text; source data files not available; PDB validation reports not provided; details of AlphaFold model generation and quality metrics beyond average pLDDT not fully described

## Reviewer
- **Overall assessment** This manuscript presents a novel and structurally significant finding: a monomeric repressor that uses two separate domains to engage an asymmetric DNA target, a mechanism distinct from the dimeric lambda cI paradigm. The crystallographic work appears technically sound, and the supporting biophysical and functional data are appropriate. However, several concerns regarding data interpretation, methodological rigor, and the strength of the proposed model need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers studying bacteriophage biology, particularly mycobacteriophage gene regulation and immunity; structural biologists interested in novel DNA-binding domain architectures; those working on transcription regulation mechanisms in bacteria; and the phage therapy community, given the therapeutic potential of mycobacteriophages.
- **Major strengths** 1) The crystal structure provides a clear and unexpected mechanistic insight: a monomeric repressor engaging DNA with two domains, which is distinct from the dimeric repressor paradigm. 2) The combination of structural, biophysical, and in vivo functional data strengthens the biological relevance of the findings. 3) The identification and naming of a "Stoperator domain" with a variant HTH fold adds to the diversity of known DNA-binding motifs. 4) The proposed model for transcriptional silencing and immunity evolution is thought-provoking and testable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (crystallographic data quality), R1-M2 (SAXS mass discrepancy), R1-M3 (EMSA quantification), R1-M4 (molecular dynamics methodology)
- **Assessment against Nature-style criteria** **Originality:** High. The finding of a monomeric repressor with two DNA-binding domains is novel and challenges the prevailing dimeric paradigm for phage repressors. **Scientific importance:** High for the bacteriophage and transcription regulation communities; moderate for the broader structural biology field. **Interdisciplinary readership:** Moderate. The work will appeal primarily to phage biologists, structural biologists, and microbiologists, but the mechanistic insights may have broader relevance. **Technical soundness:** Generally sound, but several methodological details and data interpretations require clarification and strengthening (see Major Concerns). **Readability for nonspecialists:** The manuscript is clearly written and the figures are well-designed, making the main findings accessible. However, some sections (e.g., MD analysis) may be dense for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core structural finding is likely to be of significant interest, but the current manuscript has several issues that need to be addressed to fully support the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The crystal structure of the repressor-DNA complex is presented as the central finding, with the final models having Rwork/Rfree of 20.9/24.8% (native) and 19.9/24.5% (selenomethionine).
- **Evidence pointer** Table 1, Methods section "X-ray structure determination and refinement"
- **Concern** The crystallographic statistics, particularly the completeness of the selenomethionine dataset (85.37% overall, 41.40% in the highest resolution shell) and the high Rfree values relative to Rwork, raise concerns about the overall quality of the electron density maps and the reliability of the structural model. The high Wilson B-factors (65.9 and 92.15 Å²) suggest significant disorder, which may affect the accuracy of side-chain placements and the interpretation of specific DNA contacts. The authors should provide more detailed validation metrics, such as MolProbity scores, Ramachandran statistics, and a clear description of the quality of the electron density for the key interface residues.
- **Why it matters** The structural model is the foundation of the paper's central claim. If the map quality is insufficient, the specific protein-DNA contacts and the domain architecture may be misinterpreted, undermining the main conclusions.
- **Resolution test** Provide a complete validation report (e.g., MolProbity, clash score, Ramachandran outliers) and show representative electron density for the protein-DNA interface and the two domains. Address the low completeness of the selenomethionine data and explain how this was handled. If possible, improve the resolution or provide additional experimental evidence (e.g., mutagenesis of interface residues) to support the structural interpretation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The SEC-SAXS-MALS data are used to support the monomeric state of the repressor in solution and the formation of a 1:1 protein-DNA complex. The MALS-derived mass for the repressor alone is reported as 17 kDa, while the predicted monomeric mass is 23.6 kDa.
- **Evidence pointer** Figure 2a, Supplementary Table 1, Methods section "Small-angle X-ray scattering coupled with multi-angle light scattering in line with size-exclusion chromatography (SEC-SAXS-MALS)"
- **Concern** The MALS-derived mass of 17 kDa for the repressor alone is significantly lower than the predicted mass of 23.6 kDa. This discrepancy is not discussed. Similarly, the mass of the protein-DNA complex (27 kDa) is lower than the predicted 38.5 kDa. These discrepancies could indicate partial proteolysis, concentration-dependent oligomerization, or inaccuracies in the MALS analysis. The authors should address this discrepancy and explain why the mass is underestimated.
- **Why it matters** The monomeric state of the repressor is a key claim of the paper. If the MALS data are unreliable, the solution-state oligomerization state is not firmly established, which could affect the interpretation of the DNA-binding mechanism.
- **Resolution test** Provide a detailed explanation for the mass discrepancy, including a discussion of potential sources of error (e.g., protein concentration, column interactions, dn/dc values). If possible, include an additional method (e.g., analytical ultracentrifugation or native mass spectrometry) to confirm the monomeric state.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The EMSA data are used to identify residues critical for DNA binding, with mutants R45A, W50A, K81A, R108A, and R108Q showing loss of function.
- **Evidence pointer** Figure 4b, Supplementary Fig. 6, Methods section "DNA-binding assays"
- **Concern** The EMSA data are presented qualitatively, with representative gels shown. No quantitative binding data (e.g., KD values) are provided for the mutants that show loss of function. The authors state that these mutants are "defective in DNA binding" but do not provide a quantitative measure of the defect. Additionally, the D104A mutant shows a ~3.5-fold weaker binding affinity (KD = 207 ± 65 nM) compared to wild-type (KD = 59 ± 13 nM), but the significance of this difference is not discussed in the context of the in vivo immunity assay, where D104A shows a loss of function.
- **Why it matters** The functional data are used to support the structural observations and to identify key residues. Without quantitative binding data, it is difficult to assess the severity of the binding defects and to correlate them with the in vivo phenotypes.
- **Resolution test** Provide quantitative binding data (e.g., KD values) for the key mutants, or at least a more detailed qualitative assessment (e.g., percentage of bound DNA at a fixed protein concentration). Discuss the relationship between the in vitro binding affinities and the in vivo immunity phenotypes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The molecular dynamics simulations are used to investigate conformational flexibility of the repressor on and off DNA, and to support the model of domain communication.
- **Evidence pointer** Figure 5, Methods section "Principal component and cross-correlation analyses" and "Center-of-mass (COM) pulling and umbrella sampling"
- **Concern** The MD simulation methodology is described briefly, and several key details are missing. For example, the force field parameters for the DNA, the length of equilibration, the number of replicates, and the convergence criteria are not fully described. The COM pulling and umbrella sampling methods are described, but the results are only presented as a single PMF curve (Fig. 6b) with no error bars or discussion of sampling convergence. The interpretation of the PMF curve, particularly the assignment of the two energy barriers to individual domain dissociation events, appears speculative and should be supported by more rigorous analysis.
- **Why it matters** The MD simulations are used to support the proposed model of stepwise domain dissociation and to provide a dynamic view of the repressor. If the simulations are not well-converged or the analysis is not rigorous, the conclusions drawn from them are weakened.
- **Resolution test** Provide more details on the MD simulation setup, including force field parameters, equilibration protocol, and convergence checks. Show error bars or replicate runs for the PMF calculation. Provide a more detailed analysis of the dissociation pathway to support the assignment of energy barriers to specific domain dissociation events.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1 and legend
- **Issue** The color coding of the protein domains in Figure 1 is not consistent across all panels. For example, the HTH domain is colored slate blue in panel a, but in panel d, the HTH domain is shown in a different orientation and the color appears different. This makes it difficult to follow the domain architecture across panels.
- **Required correction** Ensure consistent color coding for the HTH, helix bridge, and Stoperator domains across all panels of Figure 1, and clearly label each domain in each panel.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the repressor "utilizes two domains to recognize an asymmetric DNA sequence," but it does not mention the proposed model for how this dual-domain recognition facilitates regulation of both transcription initiation and elongation. Including a brief mention of the proposed mechanism would make the abstract more informative.
- **Required correction** Add a sentence to the abstract summarizing the proposed model for how the two domains enable regulation of both transcription initiation and elongation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "X-ray structure determination and refinement"
- **Evidence pointer** Methods section
- **Issue** The description of the use of the AlphaFold model in structure solution is somewhat vague. The authors state that the model was "included during building and refinement," but it is not clear whether the AlphaFold model was used as a search model for molecular replacement, or whether it was used as a guide for manual building. This distinction is important for assessing the potential for model bias.
- **Required correction** Clarify the exact role of the AlphaFold model in the structure solution process, and describe any steps taken to minimize model bias.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Figure 6
- **Evidence pointer** Figure 6 and legend
- **Issue** The PMF curve in Figure 6b is difficult to interpret without more context. The x-axis is labeled "COM distance" but the units are not specified. Additionally, the two energy barriers are not clearly marked or labeled.
- **Required correction** Specify the units on the x-axis, and clearly mark and label the two energy barriers corresponding to the proposed stepwise domain dissociation events.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Discussion of the Stoperator domain
- **Evidence pointer** Results section "TipsytheTRex immunity repressor structure"
- **Issue** The authors name the second DNA-binding domain the "Stoperator domain" but do not provide a clear justification for this name. It is implied that it is named for its role in binding at stoperator sites, but this is not explicitly stated.
- **Required correction** Explicitly state the rationale for naming the domain "Stoperator" and discuss whether this domain is unique to mycobacteriophages or found in other contexts.

## Risk / unsupported claims
- The claim that the Stoperator domain is a "variation of the HTH motif" is based on structural comparison, but the functional significance of this variation is not fully explored. The authors should be cautious in overinterpreting the evolutionary implications of this structural similarity.
- The proposed model for how the repressor halts transcription elongation via protein-protein interactions with RNA polymerase is speculative and not directly tested. The authors should clearly label this as a hypothesis.
- The claim that "variations observed in the Stoperator domain allow mycobacteriophages to evolve to escape superinfection immune mechanisms" is based on sequence diversity analysis but is not directly tested. This should be presented as a hypothesis.
- The in vivo immunity assay data are presented as qualitative spot titers. While this is appropriate for the assay, the authors should be careful not to overstate the quantitative differences between mutants.
- The statement that "the consensus sequence alone is too small for the repressor to stably bind" is based on SEC-SAXS-MALS and EMSA data, but the authors do not provide a detailed thermodynamic analysis to support this claim.