## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, tables, or supporting data were provided
- **Shared manuscript claim summary** The authors propose a rational basis for designing ligands selective for individual TEAD isoforms by analyzing topographic homology of the TEAD C-terminal domain, both on the external surface and within the internal pocket. They report identification of a novel TEAD2-specific pocket and its first ligand. They further use AlphaFold2 models of full-length TEADs to suggest autoregulation of TEADs and to emphasize the importance of interface 2.
- **Visible evidence base** Abstract text only; no experimental details, compound structures, assay data, structural coordinates, or model validation are available
- **Missing materials affecting confidence** Full manuscript, methods, figures, tables, compound characterization data, binding assay protocols, structural analysis details, AlphaFold2 model parameters, and any statistical or validation information

## Reviewer
- **Overall assessment** The abstract presents an interesting and potentially valuable direction in the design of isoform-selective TEAD ligands, a topic of relevance to medicinal chemistry and cancer biology. The claim of a novel TEAD2-specific pocket and its first ligand is potentially significant, but the abstract alone provides insufficient evidence to evaluate the validity, robustness, or generalizability of this finding. The AlphaFold2-based suggestion of TEAD autoregulation is intriguing but is presented without supporting detail. The work may be of interest to specialists in Hippo pathway biology and drug discovery, but the current evidence base is too limited to establish the central claims.
- **Who would be interested in the results, and why** Researchers in medicinal chemistry and drug discovery targeting the Hippo pathway, structural biologists studying TEAD transcription factors, and cancer biologists interested in TEAD isoform-specific functions. The potential for isoform-selective TEAD inhibitors has therapeutic relevance, and the proposed rational design strategy could inform future ligand development.
- **Major strengths** The focus on isoform selectivity is a timely and important gap in the TEAD ligand field. The combination of topographic homology analysis with AlphaFold2 modeling is a modern and potentially powerful approach. The identification of a TEAD2-specific pocket, if validated, would be a novel contribution.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is potentially high, as isoform-selective TEAD ligands are an emerging area and the TEAD2-specific pocket appears novel. Scientific importance is moderate to high given the role of TEADs in cancer and development. Interdisciplinary readership is plausible, spanning chemistry, structural biology, and cancer biology. Technical soundness cannot be assessed from the abstract alone, as no experimental or computational validation is presented. Readability for nonspecialists is adequate, though the abstract assumes familiarity with TEAD biology and ligand design concepts.
- **Recommendation posture** Currently not established from the provided evidence. The claims are interesting and potentially significant, but the abstract does not provide sufficient data to support the identification of a novel TEAD2-specific pocket, the selectivity of the reported ligand, or the AlphaFold2-based autoregulation hypothesis. A full manuscript with experimental and computational details would be required to assess these claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim identification of a novel TEAD2-specific pocket and report its first ligand.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract states that a novel TEAD2-specific pocket was identified and that a first ligand for this pocket was reported, but no structural, biophysical, or functional data are presented to support this claim. No details are given on how the pocket was defined, how specificity was established, or how the ligand was characterized.
- **Why it matters** The central novelty of the work rests on this claim. Without evidence of pocket identification and ligand binding, the claim cannot be evaluated or accepted. If the pocket is not truly TEAD2-specific or the ligand is not validated, the main contribution of the paper is undermined.
- **Resolution test** Provide structural data (e.g., co-crystal structures, mutagenesis, or computational mapping) demonstrating the pocket is unique to TEAD2, and provide binding data (e.g., ITC, SPR, or cellular assays) for the ligand with selectivity controls against TEAD1, TEAD3, and TEAD4.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that topographic homology analysis of the TEAD C-terminal domain highlights the possibility of rationally designing ligands selective for one TEAD family member.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract describes a homology analysis but provides no details on the methods, the degree of homology, the specific residues or regions compared, or how this analysis translates into a design strategy. The claim of rational design is not supported by any demonstrated example beyond the TEAD2 ligand, and even that example lacks validation data.
- **Why it matters** The rational design strategy is a key conceptual contribution. Without a clear description of the analysis and its predictive power, the claim remains speculative. The field would benefit from a concrete demonstration that the homology-based approach can guide selective ligand design, not just a post hoc rationalization.
- **Resolution test** Present a detailed comparison of TEAD1-4 C-terminal domain structures, highlight the residues that differ and how they create selectivity determinants, and show that the TEAD2 ligand was designed based on these differences with prospective validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that AlphaFold2 models of full-length TEADs suggest TEAD autoregulation and emphasize the importance of interface 2.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract mentions AlphaFold2 models and a suggestion of autoregulation, but no details are provided on the models, the predicted interactions, the definition of interface 2, or any experimental validation. The claim is presented as a suggestion, which is appropriately cautious, but the basis for this suggestion is entirely absent.
- **Why it matters** The autoregulation hypothesis could have significant implications for understanding TEAD function and drug design. However, without model details or supporting experiments, this claim is not assessable. If the models are not validated or the interpretation is speculative, the claim could mislead readers.
- **Resolution test** Provide the AlphaFold2 model details, show the predicted intramolecular interactions, define interface 2 clearly, and include experimental evidence (e.g., mutations, biophysical assays) that supports the autoregulation hypothesis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "topographic homology" is used without definition. It is unclear whether this refers to surface shape similarity, sequence homology, or a combination of both.
- **Required correction** Define the term explicitly and describe the computational or experimental approach used to assess it.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Context
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract mentions that "the first ligands selective for TEAD1 and TEAD3 have been recently reported" but does not cite these reports or explain how the current work differs from or builds on them.
- **Required correction** Add citations and a brief statement of how the present work extends beyond these prior selective ligands.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Precision
- **Affected element** Claim wording
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "suggest TEAD autoregulation" is vague. It is unclear what type of autoregulation is meant, for example autoinhibition, intramolecular allostery, or feedback regulation.
- **Required correction** Specify the proposed mechanism of autoregulation and the evidence supporting it.

## Risk / unsupported claims
- The identification of a novel TEAD2-specific pocket is unsupported by the abstract alone.
- The report of the first ligand for the TEAD2-specific pocket is unsupported without binding or functional data.
- The claim that topographic homology analysis enables rational design of isoform-selective ligands is not substantiated.
- The AlphaFold2-based suggestion of TEAD autoregulation is not assessable without model details or experimental validation.
- The importance of interface 2 is stated but not defined or supported.