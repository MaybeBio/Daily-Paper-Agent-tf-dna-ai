## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary figure legends
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided manuscript text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors report that in the atypical HigB-HigA toxin-antitoxin system from Proteus vulgaris, the antitoxin HigA alone robustly represses transcription at the hig promoter, while the toxin HigB does not act as a co-repressor. They present crystal structures of both trimeric HigB-HigA2 and tetrameric HigB2-HigA2 complexes bound to the O2 operator DNA, and show that an engineered trimeric complex represses transcription more than 26-fold more strongly than the tetrameric form. The authors propose that the oligomeric state of the TA complex determines the level of transcriptional repression and responsiveness to excess toxin.
- **Visible evidence base** X-ray crystal structures (PDB codes 9CHL and 9CHN), EMSA binding assays, beta-galactosidase reporter assays, size-exclusion chromatography, nano-DSF thermal stability measurements, and 1-microsecond molecular dynamics simulations with RMSF analysis
- **Missing materials affecting confidence** Supplementary Tables S1-S3 and Supplementary Figures S1-S9 are referenced but not provided in the submitted text. Raw data for beta-galactosidase assays, individual EMSA gel images, and MD simulation convergence metrics are not shown. The exact sequences of the engineered HigB(L5ext) construct and the scrambled operator DNA sequences are not fully described in the main text.

## Reviewer
- **Overall assessment** This manuscript presents a structurally and biochemically detailed characterization of an atypical toxin-antitoxin system, with the surprising finding that the trimeric HigB-HigA2 complex is a more potent transcriptional repressor than the tetrameric HigB2-HigA2 form. The crystallographic work is of high quality, and the combination of structural, biophysical, and in vivo functional data is commendable. However, several technical concerns regarding the interpretation of the repression data, the basis for the engineered trimer, and the physiological relevance of the observed oligomeric states need to be addressed before the central claims are fully established.
- **Who would be interested in the results, and why** Researchers studying bacterial toxin-antitoxin systems, transcriptional regulation, and protein-DNA interactions would find this work of interest. The demonstration of an atypical regulatory mechanism within the HigB-HigA family, where the toxin acts as a derepressor rather than a co-repressor, challenges existing models of conditional cooperativity and may have implications for understanding TA system diversity across bacterial species. The structural data on TA-DNA complexes are also valuable for the broader structural biology community.
- **Major strengths** The manuscript combines multiple complementary techniques, including X-ray crystallography, MD simulations, EMSA, and in vivo reporter assays, to address a focused question. The serendipitous capture of two different oligomeric states in the same crystallization condition is elegant and provides direct structural evidence for the coexistence of trimeric and tetrameric complexes. The engineered trimeric construct is a clever approach to test the functional consequences of the oligomeric state. The writing is clear and the figures are well-referenced throughout the text.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of functional claims
  - **Claim pointer** The authors claim that the engineered trimeric HigB(L5ext)-HigA2 complex represses transcription more than 26-fold more than the tetrameric HigB2-HigA2 complex, and that this difference reflects the intrinsic regulatory properties of the two oligomeric states.
  - **Evidence pointer** Results section "Trimeric HigB-HigA2 represses Phig to a greater extent than HigB2-HigA2", Figures 4A and 6D, Supplementary Figure S8
  - **Concern** The comparison between the engineered trimer and the presumed tetramer is confounded by the fact that the engineered construct is not the naturally occurring trimer. The loop extension (L5ext) may alter the DNA-binding properties of the complex in ways unrelated to the oligomeric state per se. The authors do not provide direct evidence that the engineered trimer adopts the same conformation as the naturally occurring trimeric complex observed in the crystal structure. Additionally, the beta-galactosidase assays compare different constructs (wild-type HigB-HigA vs. HigB(L5ext)-HigA) that may have different expression levels, protein stabilities, or DNA-binding affinities, making the 26-fold difference difficult to attribute solely to the oligomeric state.
  - **Why it matters** The central conclusion of the manuscript, that the trimeric state is a more potent repressor, rests on this comparison. If the engineered trimer behaves differently for reasons unrelated to its oligomeric state, the interpretation of the results would be substantially weakened.
  - **Resolution test** The authors should provide direct binding affinity measurements (e.g., by ITC or SPR) for the engineered trimer versus the wild-type tetramer binding to the O2 operator. They should also demonstrate that the engineered trimer retains the same DNA-binding mode as the naturally occurring trimer, for example by showing that the L5ext mutation does not alter the conformation of the HTH domains. Additionally, the authors should consider testing whether the wild-type tetramer can be converted to a trimer under physiological conditions, or whether the trimer is actually the predominant species in vivo.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence for the physiological relevance of the trimeric state
  - **Claim pointer** The authors propose that "a mixture of both trimeric and tetrameric HigB-HigA complexes bound to DNA repressor sites" exists and that this mixture contributes to the regulatory behavior of the system.
  - **Evidence pointer** Results section "Structure of HigB-HigA2-hig O2 DNA", Discussion section
  - **Concern** The evidence for the existence of the trimeric complex in solution or in vivo is indirect. The trimeric crystal form was obtained in the same crystallization condition as the tetrameric form, but the authors do not provide solution-state evidence (e.g., SEC-MALS, AUC, or native mass spectrometry) that the trimeric complex exists in the absence of crystal packing forces. The authors argue that crystal packing is unlikely to cause the trimer formation, but this is not a definitive test. Furthermore, the in vivo relevance of the trimeric state is not demonstrated; the authors do not show that the trimer forms under physiological conditions or that it is functionally significant in the bacterial cell.
  - **Why it matters** The claim that the trimeric state is functionally relevant is central to the proposed model of regulation. Without evidence that the trimer exists in solution or in vivo, the model remains speculative.
  - **Resolution test** The authors should perform SEC-MALS or AUC on the purified HigB-HigA complex in the presence of O2 DNA to determine the oligomeric state in solution. They could also use cross-linking mass spectrometry or native PAGE to assess the oligomeric state. To establish in vivo relevance, they could perform site-directed cross-linking in cells or use a reporter system that distinguishes between trimer- and tetramer-mediated repression.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of MD simulation results
  - **Claim pointer** The authors state that MD simulations reveal "similar dynamics" for the trimeric and tetrameric complexes and use this to support the idea that both are stable DNA-bound complexes.
  - **Evidence pointer** Results section "HigB2-HigA2-hig O2 and HigB-HigA2-hig O2 complexes exhibit similar dynamics", Figure 7
  - **Concern** The RMSF analysis is presented as a qualitative comparison, but no quantitative metrics are provided to support the claim of "similar dynamics." The authors do not report the convergence of the simulations, the number of independent replicates, or statistical comparisons between the two complexes. The observation that the C-terminus of one HigA is disordered in the trimeric complex and not modeled is a significant caveat, as this could affect the dynamics of the remaining residues.
  - **Why it matters** The MD simulations are used to support the structural stability of the trimeric complex. If the simulations are not converged or the analysis is not statistically robust, this support is weakened.
  - **Resolution test** The authors should provide convergence metrics (e.g., RMSD over time, block averaging) and perform multiple independent simulations to assess the reproducibility of the results. They should also consider using principal component analysis or other methods to compare the conformational ensembles of the two complexes more rigorously.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of reporting
  - **Affected element** Methods section "Electrophoretic mobility shift assays"
  - **Evidence pointer** Methods section, Supplementary Table S1
  - **Issue** The description of the scrambled operator DNA constructs is incomplete. The authors state that "all 21 nucleotides in each operator were randomized individually" but do not specify whether the scrambled sequences were verified to lack any unintended binding sites or whether the scrambling preserved the overall GC content.
  - **Required correction** Provide the full sequences of the scrambled operators in the supplementary material and state whether the scrambled sequences were tested for non-specific protein binding.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Reporter assays, Figures 4A and 6D
  - **Evidence pointer** Results section, Supplementary Figure S8
  - **Issue** The beta-galactosidase assay data are presented as mean +/- SD, but the number of independent biological replicates is not stated in the main text. The statistical test used to compare conditions is not described.
  - **Required correction** State the number of biological replicates and the statistical test used in the figure legends or methods.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness of structural reporting
  - **Affected element** Crystallographic data, Supplementary Table S3
  - **Evidence pointer** Methods section "Crystallization, data collection, and structure determination"
  - **Issue** The authors report Rwork/Rfree values but do not provide a full crystallographic data table in the main text. The completeness, multiplicity, and B-factor information are not described.
  - **Required correction** Include a complete crystallographic data table in the supplementary material, including resolution, completeness, I/sigma, multiplicity, and Ramachandran statistics.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation of sequence conservation
  - **Affected element** Discussion section, Figure 8
  - **Evidence pointer** Discussion section
  - **Issue** The authors state that HigB-HigA shares 29% sequence identity with GraT-GraA and use this to discuss functional differences. However, the sequence alignment is not shown, and the significance of the 29% identity is not discussed in the context of the structural comparison.
  - **Required correction** Provide the sequence alignment in the supplementary material and discuss which residues are conserved and which differ between the two systems, particularly in the regions involved in DNA binding and toxin-antitoxin interactions.

## Risk / unsupported claims
- The claim that the engineered trimeric HigB(L5ext)-HigA2 complex represses transcription 26-fold more than the tetrameric complex is not fully supported because the comparison is between a wild-type and an engineered construct that may differ in properties unrelated to oligomeric state.
- The claim that "there is likely a mixture of both trimeric and tetrameric HigB-HigA complexes bound to DNA repressor sites" is not supported by direct solution-state or in vivo evidence.
- The claim that the trimeric complex is "more stable" or "higher affinity" than the tetrameric complex is not directly measured; the authors infer this from the repression data, but no binding affinity measurements are provided.
- The MD simulation results are presented as supporting evidence for the stability of both complexes, but the lack of convergence metrics and statistical comparisons makes this support weak.
- The statement that "HigB toxin can disrupt interactions between HigB-HigA and hig and thus is a transcriptional derepressor" is based on the in vivo assay with overexpressed HigB(H54A), but the mechanism of this disruption is not characterized at the molecular level.

## Assessment against Nature-style criteria
- **Originality** The finding that the trimeric HigB-HigA2 complex is a more potent repressor than the tetrameric form is novel and challenges the prevailing model of conditional cooperativity in TA systems. The structural capture of both oligomeric states in the same crystallization condition is also original. However, the broader concept that TA systems exhibit diverse regulatory mechanisms is already established, and the manuscript builds on prior work from the same group.
- **Scientific importance** The results have implications for understanding the diversity of regulatory mechanisms in TA systems, which are widespread in bacteria and increasingly recognized as important in phage resistance and bacterial physiology. The structural data are a valuable contribution. However, the physiological relevance of the trimeric state is not established, which limits the immediate impact of the findings.
- **Interdisciplinary readership** The work is primarily of interest to structural biologists, microbiologists, and researchers studying gene regulation. The use of MD simulations may also appeal to computational biologists. The broader significance to non-specialists is limited by the specialized nature of the topic.
- **Technical soundness** The crystallographic work appears technically sound, with reasonable resolutions and R-factors. The EMSA and reporter assays are standard and well-executed. However, the lack of solution-state evidence for the trimeric complex and the confounding factors in the engineered trimer comparison are significant technical weaknesses.
- **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear. The introduction provides sufficient background for readers unfamiliar with TA systems. However, some sections, particularly the structural comparisons and MD simulation descriptions, may be challenging for non-specialists. The figures are well-referenced and should aid comprehension.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a potentially important finding with high-quality structural data, but the central functional claim regarding the trimeric complex requires additional experimental support. Specifically, the authors should provide solution-state evidence for the trimeric complex, direct binding affinity measurements for the engineered trimer versus the wild-type tetramer, and a more rigorous analysis of the MD simulations. If these concerns are addressed, the manuscript would be suitable for publication in a high-impact journal.