## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methodology, results, discussion, and conclusions. Supplementary materials referenced but not provided.
- **Assessment boundary** Scientific soundness, technical validity, and interpretation of the presented data. Claims are assessed strictly against the evidence provided in the manuscript text.
- **Shared manuscript claim summary** The authors report the first identification of small molecules that bind to human single-stranded DNA binding protein 1 (hSSB1) and disrupt its interaction with single-stranded DNA (ssDNA). They employed a dual approach: (1) structure-based virtual screening and rational design of compounds based on the RPA inhibitor TDRL-551, and (2) screening of an 80-compound physical library using AlphaLISA. Three compounds (MS-ML24, MS-ML25, MS-ML26) were identified with nanomolar affinity, and their binding was characterized via cosolvent molecular dynamics (MD) simulations and MM/GBSA free energy calculations. Cytotoxicity was observed in U2OS osteosarcoma cells at concentrations above 2 μM.
- **Visible evidence base** Main text figures (Figures 1–5), tables (Tables 1–3), and referenced supplementary figures/tables (Figures S1–S16, Tables S1–S2). No supplementary material was provided for independent verification.
- **Missing materials affecting confidence** Supplementary Information (detailed AlphaLISA protocol, MD simulation parameters, additional figures and tables) is referenced but not available. Raw data, statistical analysis details, and full compound characterization spectra are not accessible. This limits verification of methodological rigor and reproducibility.

## Reviewer
- **Overall assessment** This manuscript presents a potentially significant first step toward small-molecule inhibitors of hSSB1, a protein implicated in DNA damage repair and cancer therapy resistance. The combination of virtual screening, biochemical assays, and MD simulations is appropriate and the identification of nanomolar-affinity binders is encouraging. However, several technical concerns undermine the strength of the conclusions. The discrepancy between AlphaLISA and EMSA results for DAZLN-56, the lack of direct binding validation (e.g., ITC, SPR, NMR), and the absence of cellular mechanistic data linking hSSB1 inhibition to cytotoxicity leave the central claim of "disrupting hSSB1–ssDNA interaction" only partially supported. The MD simulations are suggestive but not conclusive without experimental structural validation. The manuscript would benefit from additional experiments and clearer presentation of quantitative data.
- **Who would be interested in the results, and why** Researchers in DNA damage repair, cancer biology, and drug discovery would find these results of interest. The identification of first-in-class small-molecule binders to hSSB1 opens a new avenue for targeting the DNA damage response in cancer therapy. The methodological combination of virtual screening, biochemical assays, and MD simulations may also appeal to computational chemists and structural biologists. The potential clinical relevance for sensitizing cancer cells to radio- or chemotherapy broadens the appeal to translational researchers.
- **Major strengths** (1) First reported exploration of small molecules targeting hSSB1, addressing a clear gap in the field. (2) Complementary use of computational and experimental methods strengthens the overall approach. (3) Identification of compounds with nanomolar affinity is a meaningful result. (4) The study provides a framework for future inhibitor development, including structural hypotheses from MD simulations.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "Three compounds with nanomolar affinity for hSSB1 were identified" (Abstract) and "MS-ML24 (143 nM) and MS-ML26 (198 nM)" (Discussion).
  - **Evidence pointer** Section 3.4, Figure 3, Table 2; Section 3.6, Figure 5, Table 3.
  - **Concern** The affinity values are derived solely from AlphaLISA competition assays. No orthogonal biophysical method (e.g., ITC, SPR, MST, NMR) is used to confirm direct binding. The AlphaLISA format is indirect and susceptible to assay artifacts, as acknowledged by the authors for DAZNL-51. The discrepancy between AlphaLISA and EMSA results for DAZLN-56 (binding in AlphaLISA but no inhibition in EMSA) raises questions about the specificity of the assay readout.
  - **Why it matters** The central claim of the manuscript is the identification of small molecules that bind hSSB1. Without independent confirmation of direct binding, the reported affinities could be artifacts of the assay system. This undermines the foundation for all subsequent conclusions.
  - **Resolution test** Provide direct binding data using a label-free method (ITC, SPR, or MST) for at least the three MS-ML compounds. Alternatively, a competitive binding assay with a known ssDNA ligand using a different detection principle would strengthen the case.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "Cellular studies indicate that the molecules may interfere with the cell's ability to repair DNA at certain concentrations" (Simple Summary) and "The MS-ML compounds demonstrated cytotoxicity at concentrations above 2 μM" (Section 3.7).
  - **Evidence pointer** Section 3.7, Figure 5C.
  - **Concern** The cytotoxicity data are presented as a single dose-response curve with no mechanistic link to hSSB1 inhibition. No experiments demonstrate that the observed cytotoxicity is due to on-target hSSB1 engagement rather than off-target effects. The authors do not assess DNA damage repair capacity, cell cycle effects, or apoptosis pathways. The statement in the Simple Summary that compounds "may interfere with the cell's ability to repair DNA" is speculative and not directly supported by the presented data.
  - **Why it matters** The therapeutic rationale for hSSB1 inhibition is to sensitize cancer cells to DNA-damaging agents. Without evidence that the compounds affect DNA repair through hSSB1, the translational significance of the findings remains unsubstantiated.
  - **Resolution test** Perform experiments linking compound treatment to hSSB1 function: e.g., measure hSSB1-ssDNA binding in cells (via ChIP or proximity ligation), assess DNA repair efficiency (e.g., γH2AX foci, comet assay), or use hSSB1 knockdown/rescue experiments to demonstrate on-target effects.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** "Molecular dynamics simulations indicated that three of the compounds that were tested bound to the ssDNA-binding site of hSSB1" (Abstract) and "Cosolvent MD simulations were used to develop a stronger hypothesis regarding where the compounds bind" (Discussion).
  - **Evidence pointer** Section 3.8, Figure 6, Figures S12–S15, Table S2.
  - **Concern** The MD simulation methodology is not described in the main text and the supplementary details are not available. Key parameters such as force field, water model, simulation length, convergence criteria, and analysis methods are not stated. The clustering analysis and definition of binding sites are not fully explained. The simulations are performed on a monomer, which may not represent the physiologically relevant oligomeric state of hSSB1.
  - **Why it matters** The structural predictions from MD simulations are used to support the experimental findings and provide a mechanistic framework. Without transparent methodology and validation, these predictions cannot be properly evaluated.
  - **Resolution test** Provide full simulation details in the main text or supplementary material. Validate the predicted binding modes with experimental structural data (e.g., NMR chemical shift perturbations, X-ray co-crystallography, or HDX-MS). At minimum, include a convergence analysis and error estimates for the free energy calculations.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** "To our knowledge, this is the first study to identify small molecules that modulate hSSB1 activity" (Abstract).
  - **Evidence pointer** Section 1 (Introduction), Section 4 (Discussion).
  - **Concern** The claim of novelty is plausible but the literature search is not comprehensive. The authors do not discuss potential off-target effects on other OB-fold proteins, particularly hSSB2, which shares functional redundancy. The selectivity of the identified compounds for hSSB1 over hSSB2 or other OB-fold proteins is not addressed experimentally.
  - **Why it matters** The therapeutic utility of hSSB1 inhibitors depends on selectivity. If the compounds also inhibit hSSB2 or other essential OB-fold proteins, the observed effects may not be attributable to hSSB1 specifically.
  - **Resolution test** Test the identified compounds against hSSB2 and other OB-fold proteins (e.g., RPA, POT1) in binding assays. Include a discussion of potential selectivity challenges in the context of the OB-fold family.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Figure 3
  - **Evidence pointer** Section 3.4, Figure 3
  - **Issue** The figure legend does not clearly state the number of replicates, error bar definition, or statistical test used. The difference between "binding" in AlphaLISA and "inhibition" in EMSA is not clearly explained for a non-specialist reader.
  - **Required correction** Clarify the figure legend with n numbers, error bar definition, and statistical methods. Add a brief explanation of the difference between the two assay formats and what each measures.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Table 2 and Table 3
  - **Evidence pointer** Section 3.4, Table 2; Section 3.6, Table 3
  - **Issue** The tables report IC50/Kd values with confidence intervals, but the number of independent experiments and the fitting method are not stated. The units are not consistently reported.
  - **Required correction** Add experimental details (n, fitting model, software) to the table footnotes. Ensure all values include appropriate units.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 2.4
  - **Evidence pointer** Section 2.4
  - **Issue** The AlphaLISA assay design is described as "described in the Supplementary Information," but the key principle of the competition format is not explained in the main text. A non-specialist reader cannot understand how the assay works.
  - **Required correction** Provide a brief description of the AlphaLISA competition format in the main text, including what is being measured and how the signal relates to binding.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Section 2.9
  - **Evidence pointer** Section 2.9
  - **Issue** The concentration range for the cytotoxicity assay is stated as "30 to 0492 μM," which appears to be a typo. The intended range is likely 30 to 0.0492 μM.
  - **Required correction** Correct the typo and verify the concentration range.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 3.8
  - **Evidence pointer** Section 3.8
  - **Issue** The text states "Iin this case the interaction occurs with the Phe-98" with a typo ("Iin").
  - **Required correction** Correct the typo.
- **Technical failings that need to be addressed before the case is established** (1) Lack of orthogonal binding validation (R1-M1). (2) No mechanistic link between compound treatment and hSSB1 function in cells (R1-M2). (3) Incomplete MD simulation methodology and lack of experimental structural validation (R1-M3). (4) No selectivity assessment against hSSB2 or other OB-fold proteins (R1-M4).
- **Assessment against Nature-style criteria**  
  *Originality*: The work addresses a novel target (hSSB1) for small-molecule inhibition, which has not been previously explored. This is a genuine gap in the field. However, the approach (virtual screening, biochemical assays, MD) is not methodologically novel.  
  *Scientific importance*: hSSB1 is a promising therapeutic target in cancer, and the identification of first-in-class binders is potentially important. However, the lack of mechanistic cellular data and selectivity assessment limits the immediate impact. The findings are preliminary and require substantial follow-up.  
  *Interdisciplinary readership*: The topic bridges cancer biology, DNA repair, and drug discovery, which could attract a broad audience. However, the manuscript is written in a way that assumes familiarity with both computational and experimental techniques, which may limit accessibility.  
  *Technical soundness*: The experimental design is generally reasonable, but the lack of orthogonal validation, incomplete methodological details, and unresolved discrepancies between assays are significant weaknesses. The MD simulations are not sufficiently validated.  
  *Readability for nonspecialists*: The abstract and simple summary are accessible, but the main text contains technical jargon and assumes prior knowledge. The structure is logical, but some sections (e.g., MD simulations) are difficult to follow without supplementary material.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the identification of nanomolar binders is a meaningful contribution. However, the current evidence does not fully establish that these compounds specifically disrupt the hSSB1–ssDNA interaction or that the observed cytotoxicity is due to on-target effects. Additional experiments are required to strengthen the case.

## Risk / unsupported claims
- "Three compounds with nanomolar affinity for hSSB1 were identified" — Affinity values are based solely on AlphaLISA; not confirmed by orthogonal methods.
- "Cellular studies indicate that the molecules may interfere with the cell's ability to repair DNA" — No direct evidence of DNA repair impairment is presented.
- "Molecular dynamics simulations indicated that three of the compounds that were tested bound to the ssDNA-binding site of hSSB1" — Simulation methodology is incomplete and not experimentally validated.
- "These are the first small molecules that have been demonstrated to have an affinity to hSSB1" — The claim of "demonstrated" is overstated given the lack of direct binding validation.
- "The compounds identified in this study that demonstrated the highest affinity to hSSB1 present some problems for further development" — The statement about "problems" is based on known off-target effects of the compounds in other contexts, but this is not directly tested here.