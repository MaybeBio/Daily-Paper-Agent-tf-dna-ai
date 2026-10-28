## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and supplementary information descriptions.
- **Assessment boundary** In silico structural analysis of the (pro)renin receptor using AlphaFold2 and RoseTTAFold predictions, evolutionary conservation analysis, and interpretation of functional implications. No experimental validation data are included.
- **Shared manuscript claim summary** The authors propose that two previously identified antibody-targeted regions (residues 47–60 and 200–213) of the (P)RR extracellular domain, together with an intrinsically disordered region (residues 270–296), form a conserved hydrophobic "hand-shaped" groove that serves as a multifunctional protein binding site, potentially explaining the receptor's one-to-many binding capacity and its role in Wnt signaling.
- **Visible evidence base** Predicted structural models from AlphaFold2 and RoseTTAFold, pLDDT scores, PAE plots, ProSA Z scores, Ramachandran plots, Dali structural similarity searches, ConSurf conservation scores, and PISA interface analysis.
- **Missing materials affecting confidence** No experimental validation of predicted interactions, no co-crystal structures or cross-linking data, no mutagenesis studies, no functional assays testing the proposed binding mechanism, and no direct evidence linking the identified groove to Wnt signaling components.

## Reviewer
- **Overall assessment** This manuscript presents a purely computational analysis of the (P)RR structure using state-of-the-art prediction tools. The work is logically organized and the authors make a reasonable attempt to connect their structural findings to previously published functional data. However, the central claims regarding the functional significance of the identified groove and the proposed "catch and tether" mechanism remain speculative, as no experimental evidence is provided to support these interpretations. The study is descriptive rather than hypothesis-testing, and the conclusions extend considerably beyond what the in silico data can support.
- **Who would be interested in the results, and why** Researchers studying the (pro)renin receptor, Wnt signaling pathways, pancreatic cancer biology, and protein-protein interaction mechanisms. The structural predictions may also be of interest to computational biologists working on AlphaFold2 applications to membrane proteins and intrinsically disordered regions. The potential link to hypertension and cancer therapeutics could attract translational researchers, though the speculative nature of the conclusions limits immediate applicability.
- **Major strengths** The manuscript is clearly written and the use of multiple complementary computational tools (AlphaFold2, RoseTTAFold, ConSurf, Dali, PISA) strengthens the structural analysis. The comparison between two independent prediction methods provides some confidence in the overall fold. The identification of a conserved surface patch combining the two antibody-targeted regions is an interesting observation that could guide future experimental work. The authors appropriately acknowledge the limitations of low-confidence predictions in disordered regions.
- **Major Concerns** The manuscript's central claims about the functional role of the identified groove and the "catch and tether" mechanism are not supported by direct experimental evidence. The leap from structural prediction to biological function is substantial and requires validation. Additionally, the analysis of the intrinsically disordered region is based on low-confidence predictions, which the authors acknowledge but then proceed to build their main hypothesis upon. The evolutionary conservation analysis, while useful, does not establish functional significance.
- **Minor Comments** Several statements in the discussion go beyond what the data can support, particularly regarding disease mechanisms and therapeutic implications. The relationship between the predicted dimer and the previously published experimental dimerization data could be explored more thoroughly. The manuscript would benefit from a more explicit statement of the limitations of computational predictions for functional inference.
- **Technical failings that need to be addressed before the case is established** The absence of any experimental validation for the predicted dimer interface, the proposed binding groove, or the functional significance of the conserved residues is a critical gap. The manuscript cannot establish its central claims without such validation.
- **Assessment against Nature-style criteria** Originality: Moderate. The application of AlphaFold2 to this specific receptor is novel, but the general approach of predicting protein binding sites from structural models is well established. Scientific importance: Limited at present. The findings are potentially interesting but remain speculative without experimental support. Interdisciplinary readership: The topic bridges structural biology, cancer biology, and hypertension research, but the purely computational nature may limit broader appeal. Technical soundness: Generally sound in terms of computational methodology, but the interpretation overreaches the data. Readability for nonspecialists: The manuscript is accessible, though some familiarity with structural biology concepts is assumed.
- **Recommendation posture** Currently not established from the provided evidence. The computational analysis is competently executed, but the central functional claims require experimental validation before the conclusions can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence mismatch
- **Claim pointer** The authors claim that the identified "hand-shaped" groove with the IDR acts as a protein binding site that performs multiple functions, including Wnt signaling activation.
- **Evidence pointer** Results sections "Mapping of (P)RR regions involved in PDAC antiproliferative effects" and "Conservation profile evaluated with respect to the local structural environment"; Figures 4, 5, and 6
- **Concern** The central functional claim is based entirely on structural prediction and conservation analysis. No experimental data demonstrate that this groove actually binds any protein partner, that the identified residues are required for binding, or that disruption of this region affects Wnt signaling. The connection between the antibody epitopes and the proposed binding site is circumstantial.
- **Why it matters** The manuscript's primary contribution is the proposal of a functional binding site. Without experimental validation, this remains speculation. The claim that this site mediates Wnt signaling activation is particularly unsupported, as no interaction with Wnt pathway components is demonstrated.
- **Resolution test** Provide experimental evidence such as mutagenesis of the identified residues showing loss of function, co-immunoprecipitation of predicted binding partners, or cellular assays demonstrating that disruption of the groove affects Wnt signaling.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Overinterpretation of low-confidence predictions
- **Claim pointer** The authors propose that residues 270–296 form an intrinsically disordered region that acts as "fingers" in the hand-shaped binding site, contributing to the proposed "catch and tether" mechanism.
- **Evidence pointer** Results section "Quality of the predicted human (P)RR model"; Figure 1A and 1C
- **Concern** The IDR is identified based on low pLDDT scores in the AlphaFold2 prediction. The authors acknowledge that low-confidence regions may represent disorder, but they then build a central mechanistic hypothesis on this uncertain foundation. The RoseTTAFold model also shows low confidence in this region, but this could indicate prediction failure rather than true disorder. No experimental validation of disorder (e.g., circular dichroism, NMR, or protease sensitivity) is provided.
- **Why it matters** The "catch and tether" mechanism depends critically on the IDR being genuinely disordered and functionally important. If this region is simply poorly predicted, the entire proposed mechanism collapses.
- **Resolution test** Experimentally characterize the disorder of residues 270–296 using biochemical methods, or provide additional computational evidence (e.g., multiple disorder prediction algorithms) that this region is intrinsically disordered.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Unsupported generalization from in silico to in vivo function
- **Claim pointer** The authors state that the study "provides the first 3D structural insight into receptor binding and one-to-many interactions, underpinning the functional versatility of this receptor" and suggest implications for disease treatment.
- **Evidence pointer** Discussion section
- **Concern** The conclusions extrapolate from computational predictions to broad statements about disease mechanisms and therapeutic potential. The leap from a predicted structure to statements about hypertension pathogenesis and cancer treatment is not justified by the data presented. The "one-to-many interactions" claim is inferred from the presence of an IDR and hydrophobic groove, but no binding partners are identified or tested.
- **Why it matters** Overstated conclusions can mislead readers and potentially influence future research directions. The manuscript should clearly distinguish between structural predictions and experimentally established facts.
- **Resolution test** Either temper the conclusions to match the evidence level, or provide experimental data supporting the proposed functional roles and disease implications.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "Structural similarity analysis of human (P)RR"
- **Evidence pointer** Methods section; Supplementary Table 1
- **Issue** The Dali search results are only briefly mentioned, and the significance of the structural similarity to alkaline phosphatase is not discussed in depth. The authors note that (P)RR appears to be a "pseudo-ALP" but do not explore the functional implications of this finding.
- **Required correction** Expand the discussion of the Dali results, explaining what the structural similarity to ALP family proteins might mean for (P)RR function and whether this similarity has any bearing on the proposed binding mechanism.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 6D and the "catch and tether" model
- **Evidence pointer** Figure 6D; Discussion section
- **Issue** The proposed "catch and tether" mechanism is presented as a schematic without clear explanation of how it would work at a molecular level. The figure is not accompanied by sufficient detail about what interactions are proposed and with which partners.
- **Required correction** Provide a more detailed description of the proposed mechanism, including which specific residues are involved in each step and what conformational changes are envisioned.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion of the relationship between the predicted dimer and experimental data
- **Evidence pointer** Results section "Structural basis for the homodimerization of (P)RR"; References 8, 44, 45
- **Issue** The authors mention that dimerization has been experimentally demonstrated, but do not compare their predicted dimer interface with any experimental constraints (e.g., mutagenesis data, cross-linking results, or binding assays that might localize the interface).
- **Required correction** Discuss how the predicted dimer interface relates to any available experimental data on (P)RR dimerization, or explicitly state that no such data exist.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract; Discussion section
- **Issue** The abstract repeats the same summary sentence twice, which appears to be an editorial error. Additionally, the discussion contains some redundancy in stating the novelty of the findings.
- **Required correction** Remove the duplicated sentence in the abstract and streamline the discussion to avoid repetition.

## Risk / unsupported claims
- The claim that the identified groove "acts as a protein binding site" is unsupported by direct binding data.
- The proposal that the "catch and tether" mechanism explains (P)RR's one-to-many binding is speculative and not tested.
- The assertion that the study provides insight into disease pathogenesis and therapeutic opportunities is overstated given the purely computational nature of the work.
- The functional significance of the conserved residues in the 47–60 and 200–213 regions is inferred from conservation alone, which does not establish function.
- The identification of residues 270–296 as an IDR is based solely on low prediction confidence and is not experimentally validated.
- The claim that the dimer model explains experimentally observed homodimerization is plausible but not directly verified against experimental constraints.
- The suggestion that the "hand" may facilitate V-ATPase assembly is entirely speculative with no supporting evidence.