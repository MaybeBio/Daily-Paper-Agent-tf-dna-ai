## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure/table legends
- **Assessment boundary** Scientific validity, technical soundness, and significance of the computational design method and experimental validation presented
- **Shared manuscript claim summary** The authors present a computational pipeline for designing small sequence-specific DNA-binding proteins (DBPs) using a custom scaffold library, RIFdock-based docking, and sequence design with Rosetta or LigandMPNN. They report binders for 5 distinct DNA targets with affinities as low as 30–100 nM, specificity consistent with design models, a co-crystal structure closely matching the design, and functional activity in both E. coli and mammalian cells.
- **Visible evidence base** Abstract, full main text, methods section, and references to supplementary figures (S1–S19) and tables (S1–S4)
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; raw data, sequence information, and structural coordinates not included; detailed computational parameters and code availability not fully described

## Reviewer
- **Overall assessment** This manuscript describes a significant advance in the computational design of sequence-specific DNA-binding proteins. The approach builds on prior work in protein binder design and extends it to DNA recognition, addressing key challenges of shape complementarity, base-specific hydrogen bonding, and sidechain preorganization. The experimental validation, including yeast display screening, in vitro binding assays, a co-crystal structure, and functional assays in bacterial and mammalian cells, is substantial. However, several technical concerns regarding the generality of the method, the specificity of the designed binders, and the robustness of the computational metrics need to be addressed before the claims are fully established.
- **Who would be interested in the results, and why** Researchers in protein design, synthetic biology, gene regulation, and genome editing would be interested. The method offers a potential route to custom DNA-binding proteins that could complement existing tools like zinc fingers, TALEs, and CRISPR-Cas, particularly for applications requiring small, modular, and readily deliverable DNA-binding domains.
- **Major strengths** 1) A clear and well-motivated design strategy addressing three specific challenges in DNA-binding protein design. 2) A large and diverse scaffold library derived from metagenomic sequences, providing broad structural sampling. 3) Integration of multiple computational tools (RIFdock, Rosetta, LigandMPNN, AlphaFold2) with experimental screening. 4) Comprehensive experimental validation including specificity assays, structural characterization, and functional assays in two organisms. 5) Demonstration of orthogonal regulation using designed dimers, which is important for synthetic biology applications.
- **Major Concerns** 
  - R1-M1: The claim of "arbitrary sequence" recognition is not fully supported by the data, as only 5 target sequences were tested and the sequence space covered is limited.
  - R1-M2: The success rate of the design pipeline is not clearly reported, making it difficult to assess the practical utility of the method.
  - R1-M3: The specificity of the designed binders, particularly for off-target sequences, is not comprehensively characterized.
  - R1-M4: The computational metrics used for design selection are not fully validated against experimental outcomes.
  - R1-M5: The co-crystal structure is only presented for one design, and the resolution and quality of the structure are not described in the main text.
- **Minor Comments** 
  - R1-m1: The manuscript would benefit from a clearer description of the "arbitrary" target sequence selection criteria.
  - R1-m2: The authors should clarify the relationship between the designed binders and native DBP scaffolds in terms of sequence identity and structural similarity.
  - R1-m3: The functional assays in E. coli and mammalian cells are described briefly; more details on the experimental design and controls would strengthen the claims.
  - R1-m4: The authors mention "water-mediated hydrogen bonds" in the co-crystal structure but do not discuss how these were accounted for in the design process.
  - R1-m5: The manuscript would benefit from a discussion of the limitations of the method, particularly regarding target sequence constraints and potential off-target effects.
- **Technical failings that need to be addressed before the case is established** 
  - R1-M1 (success rate and generality)
  - R1-M2 (specificity characterization)
  - R1-M4 (computational metric validation)
- **Assessment against Nature-style criteria** 
  - Originality: High. The work represents a novel approach to DNA-binding protein design, extending computational design to a challenging molecular recognition problem.
  - Scientific importance: High. The ability to design custom DNA-binding proteins has broad implications for biotechnology and medicine.
  - Interdisciplinary readership: Moderate to high. The work bridges computational biology, structural biology, and synthetic biology, and would appeal to a broad audience.
  - Technical soundness: Moderate. The computational pipeline is sophisticated, but several technical concerns (success rate, specificity, metric validation) need to be addressed.
  - Readability for nonspecialists: Good. The manuscript is generally well-written and accessible, though some sections (e.g., RIFdock details) may be challenging for non-experts.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Generality of the method
- **Claim pointer** The abstract states the method enables design of DBPs that "recognize arbitrary target sequences."
- **Evidence pointer** Results section, "Design generation and screening" (location not provided)
- **Concern** The claim of "arbitrary" sequence recognition is not supported by the data. Only 5 distinct target sequences were tested, and the sequence space covered is limited. The authors do not report the success rate of the design pipeline (i.e., the fraction of designs that bind their intended target), which is critical for assessing the generality of the method.
- **Why it matters** If the method only works for a small fraction of target sequences or has a low success rate, its practical utility is limited. The claim of "arbitrary" recognition is a strong one that requires broader demonstration.
- **Resolution test** The authors should report the success rate of the design pipeline across a larger and more diverse set of target sequences, and discuss any sequence-dependent limitations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity of designed binders
- **Claim pointer** The manuscript claims that designed binders exhibit "specificity closely matching the computational models."
- **Evidence pointer** Results section, "Design conformation and DNA-side footprinting" (location not provided)
- **Concern** The specificity of the designed binders is not comprehensively characterized. The all-by-all screen (Fig. S5) and competition assays (Fig. 2) provide some information, but the off-target binding landscape is not fully explored. For example, the authors do not report binding to sequences with single-nucleotide mismatches or to a diverse library of random sequences.
- **Why it matters** Specificity is a critical property for DNA-binding proteins, particularly for applications in gene regulation and editing where off-target effects can be detrimental. The current data are insufficient to support the claim of high specificity.
- **Resolution test** The authors should perform more comprehensive specificity assays, such as binding to a library of random sequences or systematic single-nucleotide mismatch analysis, to demonstrate the specificity of the designed binders.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Validation of computational metrics
- **Claim pointer** The authors state that designs were selected based on "the most favorable free energy of binding (Rosetta ΔΔG), contact molecular surface area, and interface hydrogen bonds."
- **Evidence pointer** Methods section, "Design Filtering" (location not provided)
- **Concern** The computational metrics used for design selection are not fully validated against experimental outcomes. The authors report correlations between some metrics and experimental binding (Fig. S17), but the predictive power of these metrics is not systematically assessed. For example, it is unclear how well Rosetta ΔΔG predicts experimental binding affinity or specificity.
- **Why it matters** If the computational metrics are not reliable predictors of experimental success, the design pipeline may not be robust or transferable to new targets.
- **Resolution test** The authors should provide a more detailed analysis of the relationship between computational metrics and experimental outcomes, including receiver operating characteristic (ROC) curves or similar analyses, to demonstrate the predictive power of their selection criteria.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Structural validation
- **Claim pointer** The co-crystal structure of DBP48 is described as being "in close agreement with the design model."
- **Evidence pointer** Results section, "Structural validation" (location not provided)
- **Concern** Only one co-crystal structure is presented, and the resolution and quality of the structure are not described in the main text. The authors note that some designed hydrogen bonds were not observed in the structure, but the implications of these discrepancies for the design method are not discussed.
- **Why it matters** Structural validation is important for confirming the accuracy of the design method. A single structure, especially one with discrepancies from the design model, is insufficient to establish the general accuracy of the approach.
- **Resolution test** The authors should provide more details on the structure quality (resolution, R-factors) and discuss the observed discrepancies in the context of the design method. Additional structures of other designed binders would strengthen the validation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Functional activity in cells
- **Claim pointer** The manuscript claims that designed DBPs "function in both Escherichia coli and mammalian cells to repress and activate transcription."
- **Evidence pointer** Results section, "Designed DBPs modulate transcription in living cells" (location not provided)
- **Concern** The functional assays demonstrate transcriptional repression in E. coli and activation in mammalian cells, but the magnitude of the effects and the specificity of the regulation are not fully described. For example, the authors do not report the dynamic range of the repression/activation or the extent of off-target effects on other genes.
- **Why it matters** Functional activity in cells is a key claim of the manuscript. The current data are promising but not sufficient to fully assess the utility of the designed DBPs for gene regulation applications.
- **Resolution test** The authors should provide more detailed functional data, including dose-response curves, dynamic range, and specificity controls, to support the claim of functional activity in cells.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract (location not provided)
- **Issue** The term "arbitrary target sequences" is used without qualification. It is unclear whether this means any sequence can be targeted or only sequences that meet certain structural criteria.
- **Required correction** Clarify the scope of the method, e.g., "sequences that can be accommodated by the scaffold library and design pipeline."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Scaffold Library Generation"
- **Evidence pointer** Methods section (location not provided)
- **Issue** The description of the scaffold library generation is brief. The criteria for selecting scaffolds and the diversity of the library are not fully described.
- **Required correction** Provide more details on the scaffold selection criteria, including the range of sizes, shapes, and sequence diversity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and materials availability
- **Evidence pointer** Data and materials availability section (location not provided)
- **Issue** The authors state that "underlying data and PDB files will be made available upon reasonable request." This is less transparent than depositing data in public repositories.
- **Required correction** Deposit the co-crystal structure and other key data in public databases (e.g., PDB, GEO) and provide access to computational scripts and parameters.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Results, "Design generation and screening"
- **Evidence pointer** Results section (location not provided)
- **Issue** The statistical significance of the enrichment and specificity data is not reported. For example, it is unclear whether the observed enrichment of specific binders is statistically significant compared to the naive library.
- **Required correction** Provide statistical analyses (e.g., p-values, confidence intervals) for the key experimental results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Conclusion
- **Evidence pointer** Conclusion section (location not provided)
- **Issue** The conclusion is largely forward-looking and does not discuss the limitations of the current method, such as the low success rate or the challenges in targeting certain sequences.
- **Required correction** Add a paragraph discussing the limitations of the method and potential strategies to overcome them.

## Risk / unsupported claims
- The claim of "arbitrary target sequence" recognition is not supported by the limited number of targets tested (5 sequences).
- The claim that designed binders exhibit "specificity closely matching the computational models" is not fully supported by the specificity data presented.
- The claim that the method is "a substantial step towards a general route" is speculative and not fully supported by the current data.
- The functional activity in cells is demonstrated, but the magnitude and specificity of the effects are not fully characterized.
- The co-crystal structure is presented as validation, but the resolution and quality of the structure are not described, and discrepancies with the design model are not fully discussed.