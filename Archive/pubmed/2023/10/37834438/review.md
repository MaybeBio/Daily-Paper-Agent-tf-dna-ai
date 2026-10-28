## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to evidence presented, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors use homology modeling and rigid docking to predict that the extracellular matrix proteoglycan lumican binds CpG ODN_2395 via leucine-rich repeat (LRR) motifs 1–11, primarily through hydrogen bonds, salt bridges, and hydrophobic interactions, with a smaller buried surface area (1803 Å²) than TLR9-CpG ODN_2395 (2094 Å²), suggesting weaker binding and providing molecular insights into TLR9-mediated inflammation modulation.
- **Visible evidence base** Abstract; Introduction; Results sections 2.1–2.5; Discussion; Materials and Methods sections 4.1–4.6; Conclusions; references to Figures 1–5, Tables 1–5, and Supplementary Figures S1–S5 (figures/tables not provided in the submitted material)
- **Missing materials affecting confidence** Figures 1–5, Tables 1–5, Supplementary Figures S1–S5, and Supplementary Table S1 are referenced but not included. Experimental validation data (e.g., binding assays, mutagenesis) are not presented. The manuscript relies entirely on in silico predictions without independent experimental corroboration beyond prior published work.

## Reviewer
- **Overall assessment** The manuscript presents a computational study aimed at characterizing lumican-CpG DNA interactions at a molecular level. The work addresses a biologically relevant question, namely how an ECM proteoglycan may modulate TLR9 signaling by sequestering CpG DNA. However, the study is purely computational, and the central claims rest on homology modeling and rigid docking without experimental validation. Several methodological choices, particularly the use of a rigid B-form single-stranded DNA model and the reliance on a single docking pose, limit the robustness of the conclusions. The manuscript is clearly written and the rationale is sound, but the evidence base is insufficient to establish the proposed interaction model with confidence. The findings may be of interest to a specialized audience in matrix biology and innate immunity, but the novelty and broad significance are modest relative to Nature-style expectations.
- **Who would be interested in the results, and why** Researchers in extracellular matrix biology, proteoglycan function, and innate immune signaling, particularly those studying TLR9 regulation and DNA sensing. The study may also interest computational biologists working on protein-DNA docking and LRR protein interactions. The potential translational relevance to inflammation and autoimmunity could attract investigators seeking molecular targets for therapeutic modulation.
- **Major strengths** The manuscript addresses a gap in understanding lumican-CpG DNA interactions at a molecular level. The use of AlphaFold-predicted lumican structure is appropriate given the absence of an experimental structure. The comparison with TLR9-CpG DNA interactions provides a useful framework. The authors acknowledge key limitations, including the use of rigid DNA and the lack of experimental validation. The writing is clear and the methods are described in sufficient detail for reproducibility.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the docking analysis identified 32 amino acids in lumican LRR1–11 interacting with CpG ODN_2395, primarily through hydrogen bonding, salt bridges, and hydrophobic interactions.
  - **Evidence pointer** Results section 2.3, Table 3, Figure 3 (not provided)
  - **Concern** The interaction model is based on a single rigid docking pose from HDOCK, with no ensemble analysis, no molecular dynamics simulations, and no experimental validation. The authors themselves note that the flexible nature of single-stranded DNA could lead to different interaction conformations. The claim of specific interacting residues is therefore not robustly supported.
  - **Why it matters** The central conclusion of the paper, namely the identification of specific lumican residues involved in CpG DNA binding, depends entirely on the accuracy of the docking prediction. Without experimental corroboration (e.g., mutagenesis, binding assays) or at least multiple computational approaches, the specific residue-level claims are speculative.
  - **Resolution test** Provide experimental validation of key predicted interactions (e.g., site-directed mutagenesis of predicted hot-spot residues followed by binding assays) or perform molecular dynamics simulations to assess the stability of the predicted complex and demonstrate that the identified residues are consistently involved across multiple conformations.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the lumican-CpG ODN_2395 interaction has a smaller buried surface area (1803 Å²) than TLR9-CpG ODN_2395 (2094 Å²), implying a potentially lower binding strength for lumican.
  - **Evidence pointer** Results section 2.2, Figure 2 (not provided)
  - **Concern** The buried surface area values are derived from a single docking model for each complex. The comparison between lumican and TLR9 is made without accounting for differences in model quality, the presence of glycosaminoglycan modifications on lumican, or the fact that TLR9 was modeled in its unliganded form. The inference from BSA to binding strength is not straightforward and requires experimental binding affinity measurements.
  - **Why it matters** The claim of differential binding strength between lumican and TLR9 is used to support the proposed mechanism of sequestration. If the BSA comparison is not reliable, the mechanistic interpretation is weakened.
  - **Resolution test** Measure binding affinities experimentally (e.g., surface plasmon resonance, isothermal titration calorimetry) for lumican and TLR9 with CpG ODN_2395, and compare with the predicted BSA values. Alternatively, use multiple docking algorithms and demonstrate consistent BSA differences.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors state that the study provides molecular insights into lumican and CpG DNA interactions that may lead to molecular targets for modulating TLR9-mediated inflammation and autoimmunity.
  - **Evidence pointer** Abstract, Discussion
  - **Concern** The translational relevance is speculative. The study does not demonstrate that the predicted interactions are functionally relevant in a biological context. The claim that this may lead to molecular targets is not supported by any functional data.
  - **Why it matters** The broader significance of the work depends on the potential for therapeutic application. Without functional validation, the translational claim is premature.
  - **Resolution test** Provide experimental evidence that disrupting the predicted lumican-CpG DNA interaction alters TLR9 signaling in cellular assays, or temper the claims to reflect the purely computational nature of the study.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction, Discussion
  - **Evidence pointer** Section 1, Section 3
  - **Issue** The manuscript assumes familiarity with LRR protein structure and TLR9 biology. Some terms, such as "LRRCE motif" and "PAMP binding surface," are used without definition or context.
  - **Required correction** Briefly define LRR motif classes and the functional significance of the TLR9 C-terminal region for readers outside the immediate field.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods section 4.5
  - **Evidence pointer** Section 4.5, Table 5
  - **Issue** The choice of rigid docking is justified by the lack of suitable templates, but the authors do not discuss the limitations of this approach for single-stranded DNA, which is inherently flexible. The use of a single top-ranked pose without considering alternative conformations is a significant simplification.
  - **Required correction** Acknowledge the limitations of rigid docking for ssDNA more explicitly and discuss how this might affect the reliability of the predicted interactions.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Results section 2.5
  - **Evidence pointer** Section 2.5, Figure 5 (not provided)
  - **Issue** The prediction that collagen binding will interfere with CpG DNA binding is based on overlapping residue usage, but no direct competition assay or co-binding model is presented.
  - **Required correction** Clarify that this is a hypothesis derived from the model and suggest experimental approaches to test it.
- **Technical failings that need to be addressed before the case is established** The absence of experimental validation for the predicted interactions is the primary technical failing. The reliance on a single rigid docking model without ensemble analysis or molecular dynamics simulations undermines the robustness of the residue-level claims. The comparison of BSA values between lumican and TLR9 is not adequately controlled for model quality differences. The manuscript would benefit from either experimental corroboration or a more cautious interpretation of the computational results.
- **Assessment against Nature-style criteria**  
  **Originality:** The study is original in applying computational modeling to lumican-CpG DNA interactions, which has not been previously reported. However, the approach is standard and the novelty is incremental.  
  **Scientific importance:** The question of how ECM proteins modulate TLR9 signaling is relevant, but the study does not provide functional data to establish biological significance. The importance is moderate and largely dependent on future validation.  
  **Interdisciplinary readership:** The work bridges matrix biology, innate immunity, and computational biology, but the technical depth in docking may limit accessibility. The potential interest across disciplines is moderate.  
  **Technical soundness:** The methods are described adequately, but the lack of experimental validation and the limitations of rigid docking for ssDNA are significant weaknesses. The technical soundness is insufficient to support the central claims.  
  **Readability for nonspecialists:** The manuscript is generally clear, but some field-specific terms and concepts are not fully explained. The readability is acceptable for a specialized audience but could be improved for broader readership.
- **Recommendation posture** Currently not established from the provided evidence. The computational predictions are interesting and hypothesis-generating, but the central claims of specific residue-level interactions and differential binding strength require experimental validation or substantially more robust computational analysis. The manuscript would be more suitable for a specialized computational biology or matrix biology journal after addressing the major concerns.

## Risk / unsupported claims
- The specific identification of 32 lumican residues interacting with CpG ODN_2395 is unsupported without experimental validation or multiple independent computational methods.
- The claim that lumican has lower binding strength than TLR9 for CpG ODN_2395, based solely on BSA comparison from single docking models, is unsupported.
- The prediction that collagen binding will interfere with CpG DNA binding to lumican is speculative and not directly tested.
- The translational claim that the findings may lead to molecular targets for modulating TLR9-mediated inflammation is unsupported by functional data.
- The statement that the lumican model shares strongest similarity with TLR9 LRR1–13 is based on a single pairwise alignment and structural superposition with high RMSD (6.4 Å), which limits confidence in this comparison.