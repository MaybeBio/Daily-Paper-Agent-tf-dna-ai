## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, methods, and figure legends. Supplementary figures and methods are referenced but not fully provided.
- **Assessment boundary** Scientific validity, technical soundness, and support of claims based on the provided manuscript text. Statistical analysis details, raw data, and supplementary methods are not fully assessable.
- **Shared manuscript claim summary** The authors propose that the C-terminal domain of human Ku80 (Ku80-Ct) acts as an endogenous inhibitor of Endonuclease G (EndoG), protecting the MLL breakpoint cluster region (MLLbcr) from chemotherapy-induced, leukemogenic chromosomal rearrangements. They identify a 28-mer peptide (Ku3) derived from Ku80-Ct that mimics this protective effect, reducing MLLbcr breakage and rearrangements after doxorubicin treatment without affecting cytotoxicity or DNA repair pathways. The mechanism is proposed to involve disruption of Ku80-EndoG complex formation and modulation of EndoG chromatin binding.
- **Visible evidence base** Main text figures (Fig. 1-7), tables (Table 1), and referenced supplementary figures (Supplementary Fig. 1-13) and tables (Supplementary Table 2, 3). Methods section for molecular modeling, docking, and cell-based assays.
- **Missing materials affecting confidence** Supplementary Methods (including SMT details, SPR details, and stable cell line generation), uncropped Western blots, raw data files, and detailed statistical outputs. These are essential for fully evaluating the robustness of the experimental data.

## Reviewer
- **Overall assessment** This manuscript presents a novel and potentially significant finding: the identification of a Ku80-derived peptide that inhibits EndoG-mediated MLLbcr cleavage and rearrangements. The hypothesis is well-motivated by structural similarities between Drosophila EndoGI and human Ku80-Ct. The combination of computational modeling, biochemical assays, and cell-based reporter systems is a strength. However, the current evidence has several gaps that prevent full support of the central claims. The mechanistic link between Ku3 binding, disruption of Ku80-EndoG complexes, and the observed reduction in rearrangements is correlative rather than definitive. The specificity of the peptide's effect on EndoG versus other nucleases or DNA repair factors is not fully established. The in vivo relevance and therapeutic potential are speculative at this stage. The manuscript would be strengthened by direct evidence of EndoG nuclease inhibition by Ku3, a clearer demonstration of the on-target effect, and a more thorough quantitative analysis of the SMT data.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, genomic instability, cancer biology, and leukemia research would be interested. Specifically, those studying the mechanisms of therapy-related leukemias, the regulation of EndoG, and the development of peptide-based inhibitors to prevent secondary malignancies would find this work relevant. The potential clinical application of preventing secondary leukemia in patients undergoing chemotherapy is a broad and compelling interest.
- **Major strengths**
    1.  The central hypothesis is novel and well-articulated, proposing a new endogenous regulatory mechanism for EndoG via Ku80.
    2.  The study integrates a robust multi-disciplinary approach, combining structural bioinformatics, molecular dynamics simulations, biochemical binding assays (SPR, IP), and functional cellular assays (recombination reporters, ChIP, PLA, SMT).
    3.  The identification of a specific peptide (Ku3) with a defined sequence and predicted binding mode provides a clear and testable tool for further investigation.
    4.  The demonstration that Ku3's protective effect is independent of canonical DNA-PK activity and general DSB repair is an important control, suggesting a specific mechanism.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Mechanistic Evidence
    - **Claim pointer** The manuscript claims that Ku3 acts as an EndoG inhibitor, reducing MLLbcr breakage and rearrangements by disrupting Ku80-EndoG complex formation.
    - **Evidence pointer** Results sections "Ku80-Ct mitigates MLLbcr rearrangements but not the repair component", "Structure-based discovery of peptide inhibitors of human EndoG", "Peptide Ku3 sequence-specifically interferes with Ku80 and EndoG complex formation in the nucleus", Figures 1, 4, 5, 6.
    - **Concern** The central claim is that Ku3 inhibits EndoG's nuclease activity. However, the manuscript does not provide direct biochemical evidence that Ku3 inhibits EndoG's endonuclease activity on DNA substrates. The data show reduced MLLbcr breakage (Fig. 5) and rearrangements (Fig. 4), and reduced Ku80-EndoG complex formation (Fig. 6), but these are indirect readouts. The reduction in breakage could be due to altered chromatin accessibility, changes in DNA structure, or effects on other nucleases. Direct evidence, such as an in vitro nuclease assay with purified EndoG and Ku3, is essential to support the claim of direct inhibition.
    - **Why it matters** Without direct evidence of nuclease inhibition, the proposed mechanism remains speculative. The observed cellular effects could be due to off-target effects of the peptide or indirect consequences of disrupting Ku80 interactions. This is a critical gap that undermines the fundamental premise of the paper.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Specificity and On-Target Effects
    - **Claim pointer** The manuscript claims that Ku3's protective effect is specific to EndoG-mediated cleavage at the MLLbcr and does not affect general DNA repair.
    - **Evidence pointer** Results sections "Ku80-Ct mitigates MLLbcr rearrangements but not the repair component", "Peptide Ku3 sequence-specifically interferes with Ku80 and EndoG complex formation in the nucleus", Figures 1, 4, 6, Supplementary Figures 2, 5.
    - **Concern** The specificity of Ku3 for EndoG is not sufficiently demonstrated. While the authors show that Ku3 does not affect NHEJ or homologous recombination in reporter assays, this does not rule out effects on other DNA repair pathways, transcription, or chromatin remodeling. The observation that Mut1 and Mut2, which have single point mutations, not only lose inhibitory activity but also *increase* Ku80-EndoG complex formation (Fig. 6c) is intriguing but also raises questions about the specificity of the peptide's interaction. The manuscript would be strengthened by showing that Ku3 does not affect the activity of other nucleases or DNA-binding proteins, and by demonstrating that the effect is dependent on EndoG expression (e.g., using EndoG knockout cells).
    - **Why it matters** A key selling point of the peptide is its potential as a specific therapeutic agent. If its effects are not specific to EndoG, its utility and the validity of the mechanistic model are significantly compromised. The lack of on-target validation makes it difficult to attribute the observed phenotype to the proposed mechanism.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Quantitative Data Analysis and Rigor
    - **Claim pointer** The manuscript claims that Ku3 reduces MLLbcr rearrangements and breakage, and that SMT analysis shows reduced chromatin binding of EndoG.
    - **Evidence pointer** Results sections "Ku80-Ct mitigates MLLbcr rearrangements but not the repair component", "Peptide Ku3 sequence-specifically interferes with Ku80 and EndoG complex formation in the nucleus", Figures 4, 5, 7, Supplementary Figures 4, 5, 11, 12.
    - **Concern** The quantitative rigor of several key experiments is insufficient. For example, the recombination data in Figure 4b and 4c show a reduction of ~35%, but the statistical analysis and effect sizes are not fully described. The SMT data in Figure 7 are complex, and the analysis of bound fractions and residence times relies on fitting models (e.g., three-component Brownian diffusion) that are not fully detailed in the main text. The authors state that error bars are smaller than data markers in Figure 7h, which is unusual and requires explanation. The number of cells, tracks, and independent experiments for the SMT analysis are not clearly stated in the main text.
    - **Why it matters** The conclusions are based on quantitative measurements. Without a clear and rigorous presentation of the statistical methods, effect sizes, and variability, it is difficult to assess the reliability and biological significance of the findings. This is particularly important for the SMT data, which is a specialized technique that requires careful controls and analysis.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Translational Relevance and In Vivo Significance
    - **Claim pointer** The manuscript suggests that Ku3 could be a lead compound for preventing secondary leukemia during cancer therapy.
    - **Evidence pointer** Abstract, Discussion.
    - **Concern** The therapeutic potential is a major part of the paper's significance, but there is no in vivo data or even ex vivo data in primary human cells. All experiments are performed in immortalized cell lines (K562, HeLa). The discussion speculates on the clinical relevance, but this is not supported by any experimental evidence. The authors do not address potential challenges such as peptide stability, delivery, bioavailability, or efficacy in a relevant animal model.
    - **Why it matters** While the study is primarily basic science, the stated goal of developing a therapeutic peptide makes the lack of translational evidence a significant weakness. The claims about preventing secondary leukemia are premature and not supported by the data presented.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and Presentation
    - **Affected element** Figure 1f, g
    - **Evidence pointer** Figure 1f, g
    - **Issue** The description of the recombination assay in Figure 1f and 1g is complex and difficult to follow. The normalization procedure and the exact meaning of "relative rec. frequencies" could be explained more clearly.
    - **Required correction** Please provide a more detailed and structured explanation of the recombination assay, including a clear step-by-step description of the normalization process and the statistical tests used.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data Presentation
    - **Affected element** Figure 7h
    - **Evidence pointer** Figure 7h
    - **Issue** The statement that error bars are smaller than the data markers and therefore not visible is concerning. It is unusual for biological data to have such small variability.
    - **Required correction** Please provide the actual values for the long-bound fractions and their standard deviations in a table or in the text. Also, clarify the number of independent experiments and cells analyzed.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical Details
    - **Affected element** Methods: Molecular Dynamics
    - **Evidence pointer** Methods section "Molecular dynamics simulations"
    - **Issue** The description of the molecular dynamics simulations is brief. Details on the force field parameters, water model, simulation time, and analysis of convergence are missing.
    - **Required correction** Please provide more details on the simulation setup and analysis to allow for reproducibility.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Literature Context
    - **Affected element** Introduction
    - **Evidence pointer** Introduction
    - **Issue** The introduction could better contextualize the role of Ku80 in DNA repair beyond its canonical NHEJ function, particularly its potential roles in replication stress and chromatin dynamics, which are relevant to the proposed mechanism.
    - **Required correction** Consider adding a brief discussion of non-canonical Ku80 functions to strengthen the rationale for the study.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of direct biochemical evidence for EndoG nuclease inhibition by Ku3.
    - R1-M2: Insufficient demonstration of on-target specificity for EndoG.
    - R1-M3: Incomplete quantitative analysis and reporting of key experiments, particularly SMT.

- **Assessment against Nature-style criteria**
    - **Originality** High. The concept of a Ku80-derived peptide acting as an EndoG inhibitor to protect against MLL rearrangements is novel and not previously described.
    - **Scientific importance** Potentially high. If the mechanism is fully validated, it could provide a new strategy to prevent therapy-related leukemias and offer insights into the regulation of EndoG. However, the current evidence is not yet sufficient to establish this importance.
    - **Interdisciplinary readership** Moderate. The topic is of interest to cancer biologists, DNA repair specialists, and hematologists. The computational aspects may appeal to a broader audience, but the specialized nature of the assays may limit its accessibility.
    - **Technical soundness** The experimental design is generally sound, but the lack of direct mechanistic evidence and incomplete quantitative analysis are significant weaknesses. The computational predictions are not fully validated experimentally.
    - **Readability for nonspecialists** The manuscript is written in a technical style that is appropriate for a specialist audience. The abstract is clear, but the results section is dense and may be challenging for nonspecialists to follow.

- **Recommendation posture** Not currently established from the provided evidence. The manuscript presents an interesting hypothesis and a promising lead peptide, but the central claim of direct EndoG inhibition is not supported by direct evidence. The specificity of the peptide's effects is not adequately demonstrated. Major revisions are required to provide direct biochemical evidence for the mechanism, strengthen the on-target validation, and improve the quantitative rigor of the data analysis. If these concerns are addressed, the manuscript could become a significant contribution to the field.