## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report that Huangkui capsule (HKC), an ethanol extract of *Abelmoschus manihot* (L.), ameliorates diabetic kidney disease (DKD) in db/db mice, and that single-cell RNA sequencing combined with cell communication analysis, transcription factor regulatory network prediction, and molecular docking identifies 11 key receptors in 4 renal cell types that directly interact with seven HKC flavonoids, regulating downstream regulons linked to T cell function and renal injury.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or statistical outputs provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, statistical analyses, and any validation experiments

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting application of single-cell transcriptomics to explore the mechanism of a botanical extract in a mouse model of DKD. However, the current evidence base is insufficient to evaluate the validity of the central claims. The abstract reports a complex analytical pipeline but provides no quantitative results, no validation of key findings, and no clarity on how the single-cell data support the specific receptor and regulon conclusions. The causal language used in the conclusion exceeds what the described analyses can establish.
- **Who would be interested in the results, and why** Researchers in nephrology, particularly those studying diabetic kidney disease mechanisms and potential botanical therapeutics; investigators using single-cell RNA sequencing to dissect cell type specific drug responses; and scientists interested in computational approaches such as cell communication inference and molecular docking for natural product target identification.
- **Major strengths** The study addresses a clinically relevant question using a clinically used botanical extract. The combination of single-cell transcriptomics with cell communication and transcription factor network analyses is a modern and potentially powerful approach. The focus on cell type specific mechanisms is appropriate for a disease with heterogeneous renal pathology.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence sufficiency
    - **Claim pointer** The abstract claims that 11 key receptors in 4 cell types were found to directly interact with HKC flavonoids and that these interactions regulated 8 downstream regulons.
    - **Evidence pointer** Abstract results section; location not provided
    - **Concern** The abstract provides no quantitative data, no statistical measures, and no details on how the 11 receptors and 8 regulons were selected. No thresholds, significance criteria, or validation steps are described. The claim of "direct interaction" is based on molecular docking, which is a computational prediction and not experimental evidence of binding.
    - **Why it matters** Without quantitative support and clear selection criteria, the reader cannot assess whether the identified receptors and regulons are robust findings or artifacts of the analytical pipeline. The term "directly interacted" overstates what docking can establish.
    - **Resolution test** Provide the full results with effect sizes, confidence intervals or p values, the criteria for receptor and regulon selection, and experimental validation such as binding assays, knockdown or overexpression studies, or at minimum orthogonal transcriptomic validation.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Causal inference
    - **Claim pointer** The conclusion states that the identified receptors and regulons provide a better understanding of the cell type specific molecular mechanisms of *A. manihot* in treatment of DKD, and the results section implies that receptor ligand interactions "led to" transcriptional event differences and "consequently affected" T cell activation, differentiation, and infiltration.
    - **Evidence pointer** Abstract results and conclusion sections; location not provided
    - **Concern** The abstract uses causal language such as "led to" and "consequently affected" based on correlational single-cell data and computational predictions. No perturbation experiments, time course analyses, or functional assays are described that would support causal relationships between flavonoid receptor binding, regulon activity, and cellular phenotypes.
    - **Why it matters** Causal claims about drug mechanism require experimental intervention. The current evidence supports only association or prediction, not causation. Overstating causal relationships misleads readers about the strength of the findings.
    - **Resolution test** Either temper the language to describe associations and predictions, or add functional validation experiments such as receptor inhibition, regulon modulation, or adoptive transfer studies that directly test the proposed mechanism.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Reproducibility and transparency
    - **Claim pointer** The abstract describes a single-cell RNA sequencing analysis of kidneys in db/db mice with and without HKC administration, and a urinary biochemical and histopathological examination.
    - **Evidence pointer** Abstract methods section; location not provided
    - **Concern** No details are provided on the number of mice per group, the number of cells sequenced, the sequencing depth, the quality control metrics, the bioinformatics pipeline, or the statistical methods. The histopathological and biochemical results are mentioned but no data are shown.
    - **Why it matters** Reproducibility is a core requirement for scientific claims. Without these details, the study cannot be evaluated or replicated. The absence of any reported phenotypic data also leaves unclear whether HKC actually improved DKD outcomes in this experiment.
    - **Resolution test** Provide the full methods with all parameters, the number of biological and technical replicates, and the phenotypic results with appropriate statistical analysis.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Study design description
    - **Evidence pointer** Abstract study design section; location not provided
    - **Issue** The abstract states "C57BL/6 and db/db mice of DKD and HKC groups" but does not clarify whether C57BL/6 mice served as non diabetic controls and how many groups were used in total.
    - **Required correction** Clarify the experimental groups, including the number of mice per group and the role of each strain.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** Title
    - **Evidence pointer** Title; location not provided
    - **Issue** The title states "transcriptional regulation responded for" which is grammatically awkward and unclear. The intended meaning appears to be "transcriptional regulation underlying" or "mediating" the treatment effect.
    - **Required correction** Revise the title for grammatical clarity and precision.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Results summary
    - **Evidence pointer** Abstract results section; location not provided
    - **Issue** The abstract mentions "75 receptors with different activities" but does not explain what "different activities" means or how this set was defined.
    - **Required correction** Define the criteria for receptor inclusion and the meaning of "different activities."
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Interpretation
    - **Affected element** T cell findings
    - **Evidence pointer** Abstract results section; location not provided
    - **Issue** The abstract states that receptor docking in T cells affected activation, differentiation, and infiltration, but no data on T cell phenotypes or infiltration are presented in the abstract.
    - **Required correction** Either present supporting data or describe these as predicted effects based on regulon analysis.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative results, experimental validation, and methodological transparency means the central claims are not currently supported by the provided evidence.
- **Assessment against Nature-style criteria**  
  *Originality*: The combination of single cell RNA sequencing with docking and regulon analysis for a botanical extract in DKD is moderately novel, though each individual technique is established.  
  *Scientific importance*: The clinical relevance of HKC for DKD is real, but the abstract does not demonstrate that the mechanistic findings are generalizable or actionable beyond this specific model and extract.  
  *Interdisciplinary readership*: The work bridges nephrology, transcriptomics, and computational pharmacology, which could interest a broad audience if the findings are robust.  
  *Technical soundness*: Cannot be assessed from the abstract. The described pipeline is complex and error prone, and no quality metrics or validations are provided.  
  *Readability for nonspecialists*: The abstract is dense and uses specialized terms without sufficient context, making it difficult for a general scientific audience to follow.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a potentially valuable study, but the absence of quantitative results, validation, and methodological detail prevents any assessment of the validity of the claims. A full manuscript with complete data and appropriate experimental validation would be required to evaluate the case.

## Risk / unsupported claims
- The claim that 11 receptors "directly interacted" with HKC flavonoids is unsupported because molecular docking is predictive, not experimental.
- The causal statements that receptor ligand interactions "led to" transcriptional differences and "consequently affected" T cell function are unsupported by the described analyses.
- The claim that the study "provides novel information" for understanding mechanisms of *A. manihot* in DKD is not evaluable without comparison to existing literature and without validation of the findings.
- Any statement about the efficacy of HKC in the mouse model is unsupported because no biochemical or histopathological data are presented in the abstract.