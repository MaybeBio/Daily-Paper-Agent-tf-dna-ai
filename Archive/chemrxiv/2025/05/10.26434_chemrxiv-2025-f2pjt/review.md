## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract; no methods, figures, or supplementary material were provided for verification
- **Shared manuscript claim summary** The authors report molecular dynamics (MD) and dissociation parallel cascade selection molecular dynamics (dPaCS-MD) simulations of a single-stranded RNA bound to the FUS zinc finger (ZnF) and its flanking intrinsically disordered RGG2 domain. They propose two distinct binding modes, one involving specific GGU recognition by ZnF with non-specific RGG2 interaction and RNA backbone distortion, and another with ZnF-specific GGU recognition but minimal RGG2 involvement. They further generalize to two mechanisms for strong and specific nucleic acid binding in nucleic acid binding proteins, and claim expansion of disordered region-assisted ZnF binding from double-stranded DNAs to single-stranded RNAs.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or simulation parameters provided
- **Missing materials affecting confidence** Full manuscript, methods section, simulation parameters, force field details, convergence criteria, free energy estimates, structural figures, sequence analysis methodology, and any statistical validation

## Reviewer
- **Overall assessment** The abstract presents a plausible computational study addressing an important question in RNA binding by a disease-relevant protein. However, the evidence base available for review is limited to the abstract, which prevents verification of the central claims. The proposed dual binding modes and the generalized mechanisms for nucleic acid binding are interesting but require substantial methodological detail and quantitative support to be convincing. The claim of expanding the repertoire from double-stranded DNAs to single-stranded RNAs is intriguing but not substantiated in the abstract alone.
- **Who would be interested in the results, and why** Researchers studying RNA binding proteins, particularly those involved in neurodegeneration (FUS is linked to amyotrophic lateral sclerosis and frontotemporal dementia), computational biophysicists interested in protein-RNA interactions, and structural biologists studying intrinsically disordered regions in nucleic acid binding contexts. The proposed general mechanisms for nucleic acid binding could interest a broader community studying protein-nucleic acid recognition.
- **Major strengths** The study addresses a biologically and clinically relevant system with a sophisticated computational approach. The proposal of two distinct binding modes is a nuanced view that goes beyond simple binary descriptions. The attempt to generalize findings into broader mechanisms for nucleic acid binding proteins adds conceptual value. The connection to disordered region-assisted binding is timely given growing recognition of disordered regions in molecular recognition.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The concept of disordered region-assisted ZnF binding to single-stranded RNA is novel and extends prior work on double-stranded DNA. However, the abstract does not clearly differentiate this from existing literature on FUS-RNA interactions.  
  Scientific importance: The FUS protein is clinically significant, and understanding its RNA binding mechanism has implications for disease mechanisms. The proposed general mechanisms could be impactful if well supported.  
  Interdisciplinary readership: The topic bridges structural biology, computational biophysics, and RNA biology, which could attract a broad audience. However, the abstract is written in a way that assumes familiarity with simulation methods.  
  Technical soundness: Cannot be assessed from the abstract alone. The lack of methodological detail and quantitative results prevents evaluation of simulation quality, convergence, or statistical significance.  
  Readability for nonspecialists: The abstract is dense and uses specialized terminology without sufficient context. The distinction between the two binding modes is not clearly explained for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents interesting hypotheses but the evidence base is insufficient to assess the validity of the central claims. A full manuscript with detailed methods and results would be required for a meaningful evaluation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim to have "identified the molecular basis for the strong and specific binding of FUS ZnF to RNA at atomic resolution" and observed "dissociation of the complex" through MD and dPaCS-MD simulations.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract provides no quantitative results from the simulations. There are no free energy values, no binding affinity estimates, no comparison to experimental data, and no description of how "strong and specific binding" was quantified. The observation of dissociation is mentioned but without context regarding simulation timescales, number of replicates, or statistical significance.  
- **Why it matters** The central claim of identifying the molecular basis of binding at atomic resolution requires robust quantitative support. Without free energy calculations, convergence analysis, or experimental validation, the claim cannot be evaluated. The term "strong and specific" implies quantitative comparison that is not presented.  
- **Resolution test** Provide binding free energy estimates with error bars, convergence metrics for the simulations, and ideally comparison with experimental binding data or mutational validation.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors propose "two distinct binding modes" of the FUS ZnF-RNA complex, distinguished by the degree of RGG2 domain involvement.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not describe how these two binding modes were identified or distinguished. There is no mention of clustering analysis, free energy landscapes, or population distributions. The criteria for classifying a trajectory into one mode versus the other are not stated. The claim that one mode results in "weaker binding" is not supported by any quantitative comparison.  
- **Why it matters** The two-mode proposal is a central finding of the study. Without clear methodological criteria for defining and distinguishing these modes, and without quantitative support for the differential binding strength, the claim is not verifiable.  
- **Resolution test** Describe the analytical approach used to identify the two modes, provide population statistics or free energy differences between modes, and quantify the binding strength difference with appropriate error analysis.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The authors claim "two possible mechanisms for ensuring strong and specific nucleic acid binding in nucleic acid binding proteins" based on "further comprehensive analysis of nucleic acid binding site sequences."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not describe the nature of this "comprehensive analysis," the dataset used, the criteria for classification, or how the conclusions were derived. The generalization from a single system (FUS ZnF) to broad mechanisms for all nucleic acid binding proteins is a significant leap that requires substantial comparative evidence.  
- **Why it matters** This generalization elevates the study from a case report to a conceptual contribution. Without details on the sequence analysis methodology and the breadth of the dataset, the claim is unsupported and potentially overreaching.  
- **Resolution test** Provide details of the sequence analysis, including dataset composition, statistical methods, and how the two mechanisms were derived. Demonstrate that the conclusions are robust across diverse protein families.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Originality  
- **Claim pointer** The authors claim their findings "allow us to expand the repertoire of disordered region-assisted nucleic acid binding by ZnF from double-stranded DNAs to single-stranded RNAs."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not cite or discuss prior work on ZnF binding to single-stranded RNA or disordered region-assisted RNA binding. Without situating this claim in the existing literature, it is unclear whether this is truly an expansion or a confirmation of known behavior.  
- **Why it matters** The novelty claim is central to the paper's contribution. If prior work has already demonstrated disordered region-assisted ZnF binding to RNA, this claim would be overstated.  
- **Resolution test** Provide a clear literature context in the full manuscript, explicitly comparing to prior studies on ZnF-RNA interactions and disordered region-assisted binding.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract uses specialized terminology (e.g., "dissociation parallel cascade selection molecular dynamics") without explaining the method or its significance for a general audience.  
- **Required correction** Briefly describe the method in accessible terms or provide context for why this approach is particularly suited to the problem.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Scientific importance  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not mention the disease relevance of FUS, which is a key motivator for studying this protein.  
- **Required correction** Add a sentence connecting FUS to its clinical significance (e.g., ALS and FTD) to frame the importance of the study.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Technical soundness  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract states that the RGG2 domain "non-specifically interacts with RNA and distorts the RNA backbone structure" but does not explain why this distortion is functionally relevant.  
- **Required correction** Clarify the functional consequence of RNA backbone distortion, such as effects on binding affinity or specificity.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The distinction between the two binding modes is described in a way that is difficult to follow, particularly the difference in RGG2 involvement and its consequences.  
- **Required correction** Rewrite the description of the two modes to make the contrast clearer, possibly using a comparative structure.

## Risk / unsupported claims
- The claim of "strong and specific binding" is unsupported without quantitative binding data or experimental validation.
- The identification of "two distinct binding modes" is unverifiable without methodological details on mode classification.
- The generalization to "two possible mechanisms for ensuring strong and specific nucleic acid binding" is unsupported without details of the comparative sequence analysis.
- The claim of expanding the repertoire from double-stranded DNAs to single-stranded RNAs is unverifiable without literature context and comparative evidence.
- The functional relevance of RNA backbone distortion by RGG2 is asserted but not explained or supported.