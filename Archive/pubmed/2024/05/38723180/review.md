## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report a cryo-EM structure of a transcription activation complex containing Escherichia coli RNA polymerase, the LysR-type transcriptional regulator GcvA, and promoter DNA. They propose that two GcvA DNA-binding domains dimerize and engage activation binding sites, presenting the -35 element for recognition by sigma70 region 4. They further claim that the RNAP alpha subunit C-terminal domain interconnects GcvA_DBD, sigma70R4, and promoter DNA, that molecular docking supports glycine as a potential inducer, and that single-molecule photobleaching experiments visualize a tetrameric GcvA-engaged complex. A general model for tetrameric LTTR-dependent transcription activation is proposed.
- **Visible evidence base** Abstract text only; no structural coordinates, maps, docking scores, photobleaching traces, or statistical analyses are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, cryo-EM data and validation statistics, molecular docking parameters and scores, single-molecule experimental details and replicates, methods section, and any supplementary information

## Reviewer
- **Overall assessment** The abstract describes a potentially significant structural study addressing a long-standing question in bacterial transcription regulation. The cryo-EM structure of an LTTR-dependent activation complex would be of considerable interest to the transcription and gene regulation communities. However, the abstract alone provides insufficient detail to evaluate the technical quality of the structural determination, the robustness of the docking and photobleaching experiments, or the strength of the proposed general model. Several claims are presented without quantitative support or methodological context, and the relationship between the observed complex and the proposed tetrameric model is not clearly established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying bacterial transcription regulation, particularly those focused on LysR-type regulators, RNA polymerase promoter recognition, and activator mechanisms. Structural biologists interested in multi-subunit transcription complexes and cryo-EM methodology would also find the work relevant. Given the essential roles of LTTRs in metabolism, virulence, and stress responses, investigators in bacterial pathogenesis and antimicrobial development may have applied interest.
- **Major strengths** The study addresses a fundamental and unresolved question in bacterial transcription activation. The use of cryo-EM to capture a complete LTTR-dependent activation complex is a technically ambitious and potentially field-advancing approach. The proposed integration of structural, biochemical, and single-molecule data toward a general model is conceptually valuable.
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
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The work appears conceptually original in providing a structural view of an LTTR-dependent activation complex, though the abstract does not clarify how this differs from prior LTTR structures or existing activation models.  
  Scientific importance: The topic is important, and a validated structural model would be a meaningful advance. However, the abstract does not demonstrate that the proposed model is generalizable beyond GcvA.  
  Interdisciplinary readership: The findings would appeal to structural biologists, microbiologists, and biochemists, but the abstract does not articulate broader implications for fields such as systems biology or drug discovery.  
  Technical soundness: Cannot be assessed from the abstract. No resolution, map quality, model validation, or experimental controls are reported.  
  Readability for nonspecialists: The abstract is dense and assumes familiarity with LTTR biology, sigma70 domains, and cryo-EM terminology. A nonspecialist would struggle to extract the key advance.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible and interesting study, but the absence of quantitative data, methodological detail, and validation metrics prevents assessment of whether the core claims are supported. A supportive posture would require full manuscript review.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness of structural determination  
- **Claim pointer** The authors claim to have determined a cryo-EM structure of a transcription activation complex comprising RNAP, GcvA, and promoter DNA.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract provides no information on the resolution of the cryo-EM map, the number of particles, the quality of the local map for the GcvA and DNA regions, or the validation statistics for the atomic model. Without these data, the reliability of the structural interpretation cannot be evaluated.  
- **Why it matters** The central claim of the paper rests on the accuracy of the structural model. If the map resolution is insufficient in the regions where GcvA_DBD contacts DNA or where the alpha CTD interconnects with other components, the proposed interactions may be artifacts of model building.  
- **Resolution test** Provide the nominal and local resolutions, Fourier shell correlation curves, model-to-map fit statistics, and validation metrics such as MolProbity scores and Ramachandran outliers. Show that the key interfaces are resolved at sufficient resolution to support the described contacts.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Support for the proposed activation mechanism  
- **Claim pointer** The authors state that two GcvA_DBDs dimerize and engage activation binding sites, presenting the -35 element for recognition by sigma70R4.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not describe how the activation binding sites were identified or whether the proposed presentation mechanism is supported by functional assays, such as promoter mutations or footprinting. It is unclear whether the observed complex represents a pre-activation state, an activated state, or a non-productive binding mode.  
- **Why it matters** The proposed mechanism is the core functional insight of the study. Without experimental validation that the observed DNA engagement is required for transcription activation, the structural observation may not reflect the functional mechanism.  
- **Resolution test** Include functional data, such as transcription assays with wild-type and mutant activation binding sites, or DNA binding assays that correlate the structural contacts with activity. Clarify the functional state of the complex.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence for the tetrameric model  
- **Claim pointer** The authors claim that single-molecule photobleaching experiments kinetically visualize the occurrence of tetrameric GcvA-engaged transcription activation complex, and that a general model for tetrameric LTTR-dependent transcription activation is proposed.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract provides no details on the photobleaching experimental design, the number of molecules observed, the stoichiometry determination method, or the statistical confidence in assigning tetrameric states. The leap from a single-molecule observation to a general model for all LTTRs is not justified without comparative data on other family members.  
- **Why it matters** The general model is a major claim of the paper. If the photobleaching data are limited or ambiguous, or if the tetrameric state is not consistently observed, the proposed model may be overgeneralized.  
- **Resolution test** Provide photobleaching step distributions, control experiments, and statistical analysis supporting the tetramer assignment. Include evidence that the tetrameric complex is functionally relevant, and discuss how the model applies to other LTTRs with supporting data or clear rationale.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Support for glycine as an inducer  
- **Claim pointer** The authors state that molecular docking supports glycine as one potential inducer of GcvA.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract does not report docking scores, the docking method, the binding site used, or any comparison with known GcvA ligands. The phrase "one potential inducer" is vague and does not establish whether glycine binding is biochemically validated.  
- **Why it matters** The inducer identity is relevant to the regulatory context of GcvA. If the docking is not validated by binding or activity assays, the claim is speculative and may mislead readers about the physiological relevance.  
- **Resolution test** Provide docking scores and ranks, describe the docking protocol and binding site, and include biochemical validation such as isothermal titration calorimetry, surface plasmon resonance, or transcription assays with glycine.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of terminology  
- **Affected element** Abstract, first sentence  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The phrase "enormous LysR-type transcriptional regulators" is imprecise. It is unclear whether "enormous" refers to the number of family members, the size of the proteins, or the breadth of their regulatory roles.  
- **Required correction** Replace with a precise descriptor, such as "the large family of LysR-type transcriptional regulators" or "the widely distributed LysR-type transcriptional regulators."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness of structural description  
- **Affected element** Abstract, structural findings  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not mention the overall architecture of the complex, such as the arrangement of RNAP core subunits or the path of promoter DNA. This limits the reader's ability to appreciate the structural context of the described interactions.  
- **Required correction** Add a brief description of the overall complex architecture, including the positions of key RNAP domains relative to GcvA and DNA.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Generalizability of the model  
- **Affected element** Abstract, final claim  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The proposed general model for tetrameric LTTR-dependent transcription activation is stated without specifying which features are conserved across LTTRs and which are GcvA-specific.  
- **Required correction** Clarify the basis for generalizability, such as sequence conservation of the DBD dimer interface or the alpha CTD interaction surface, and note any limitations.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Readability for nonspecialists  
- **Affected element** Abstract, overall  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract uses domain abbreviations such as GcvA_DBD, sigma70R4, and alpha CTD without defining them. A reader outside the transcription field may struggle to follow the mechanistic description.  
- **Required correction** Define abbreviations at first use, or use more descriptive terms such as "the DNA-binding domain of GcvA" and "region 4 of the sigma70 subunit."

## Risk / unsupported claims
- The claim that the cryo-EM structure reveals a specific activation mechanism is unsupported without resolution and validation data.
- The claim that the alpha CTD "directly interconnects" with GcvA_DBD, sigma70R4, and promoter DNA is unverifiable from the abstract alone.
- The claim that glycine is a potential inducer is speculative without docking scores or biochemical validation.
- The claim that a general model for tetrameric LTTR-dependent transcription activation is proposed is not supported by comparative evidence across LTTR family members.
- The functional relevance of the observed complex to transcription activation is not established from the abstract.