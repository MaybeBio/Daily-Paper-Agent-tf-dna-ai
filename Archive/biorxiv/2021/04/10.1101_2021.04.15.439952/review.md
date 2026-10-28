## Review setup
- **Input scope** Full manuscript text and author summary as provided
- **Assessment boundary** Scientific claims, experimental logic, and evidence as presented in the supplied text only
- **Shared manuscript claim summary** The authors report that promoter selectivity between VqmA from *Vibrio cholerae* (VqmA^Vc^) and the VP882 phage homolog (VqmA^Phage^) is determined by the DNA-binding domain, with specific residues in the helix-turn-helix motif and C-terminal flanking region governing differential binding to the *vqmR* and *qtip* promoters. They propose that in VqmA^Vc^, the helix-turn-helix motif and C-terminal flanking residues together prevent binding to the *qtip* promoter.
- **Visible evidence base** Text describing findings from protein sequence-guided mutagenesis, a genetic screen for VqmA^Phage^ mutants, and a targeted genetic screen in VqmA^Vc^. No figures, tables, methods, or numerical data are provided.
- **Missing materials affecting confidence** Figures, tables, experimental methods, statistical analyses, sequence alignments, strain and plasmid details, and any quantitative binding or expression data. The manuscript appears to be a preprint with full text, but only the abstract and author summary are supplied here.

## Reviewer
- **Overall assessment** The manuscript addresses a compelling question in quorum sensing and phage biology, namely the molecular basis for asymmetric promoter recognition between a bacterial and a phage-encoded transcription factor. The proposed mechanism, involving distinct residues in the DNA-binding domain and flanking sequences, is plausible and potentially significant. However, the supplied material is insufficient to evaluate the rigor of the experimental support. Key claims rest on genetic screens and mutagenesis whose design, validation, and quantitative outcomes are not described. The conclusion that VqmA^Vc^ is actively prevented from binding the *qtip* promoter, rather than simply lacking the necessary contacts, is an interesting hypothesis but is not substantiated by the evidence presented here.
- **Who would be interested in the results, and why** Researchers in bacterial quorum sensing, phage-host interactions, transcription factor specificity, and gene regulation. The work also has relevance for understanding cross-domain chemical communication and the evolution of transcriptional regulatory networks. The mechanistic dissection of DNA-binding specificity could inform studies of other homologous regulators.
- **Major strengths** The question is well-framed and biologically important. The use of reciprocal promoter selectivity between two highly similar proteins is a powerful approach. The identification of specific residues and regions involved in specificity, including the surprising finding that conserved residues contribute to differential binding, is conceptually interesting. The author summary clearly articulates the broader significance.
- **Major Concerns** The supplied text lacks all experimental detail, making it impossible to assess the validity of the claims. The genetic screens are described only in narrative form, with no information on library size, selection criteria, mutation frequency, or validation. The claim that promoter selectivity is driven "exclusively" by the DNA-binding domain is a strong statement that requires domain-swap or chimeric experiments, which are not described. The proposal that VqmA^Vc^ is "prohibited" from binding the *qtip* promoter implies an active mechanism, but the evidence for a negative determinant is not presented in sufficient detail.
- **Minor Comments** The abstract and author summary are well-written and accessible. The use of "eavesdrops" in the author summary is informal but acceptable for a preprint. The manuscript would benefit from a clearer statement of the null hypothesis regarding how VqmA^Vc^ avoids *qtip* binding.
- **Technical failings that need to be addressed before the case is established** The absence of any experimental data, figures, or methods means that no technical claim can be verified. Specifically, the mutagenesis and screen results, the binding assays, and the promoter constructs are all unverifiable from the supplied material.
- **Assessment against Nature-style criteria**  
  *Originality*: The work addresses a novel question and the proposed mechanism appears original.  
  *Scientific importance*: High, given the relevance to quorum sensing, phage biology, and pathogenicity.  
  *Interdisciplinary readership*: Likely to appeal to microbiologists, molecular biologists, and those interested in phage-host interactions.  
  *Technical soundness*: Cannot be assessed from the supplied material.  
  *Readability for nonspecialists*: The abstract and author summary are clear, but the main text is not provided in full.
- **Recommendation posture** Currently not established from the provided evidence. The claims are interesting and potentially important, but the supplied material is insufficient to support them. A full manuscript with data would be required for a substantive evaluation.

### Major Concerns

- **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** "Promoter selectivity is driven exclusively by each VqmA DNA-binding domain"  
  - **Evidence pointer** Abstract, location not provided  
  - **Concern** The claim of exclusivity requires demonstration that the DNA-binding domain alone, when swapped or isolated, recapitulates promoter selectivity. No such experiment is described in the supplied text.  
  - **Why it matters** The central mechanistic claim of the paper rests on this exclusivity. Without direct evidence, alternative explanations, such as contributions from other protein regions or oligomerization states, remain plausible.  
  - **Resolution test** Provide domain-swap or chimeric protein experiments showing that the DNA-binding domain is sufficient to confer promoter specificity.

- **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** "A genetic screen to identify VqmA^Phage^ mutants that are incapable of binding the *qtip* promoter but maintain binding to the *vqmR* promoter delivered additional VqmA^Phage^ residues located immediately C-terminal to the helix-turn-helix motif as required for binding the *qtip* promoter"  
  - **Evidence pointer** Abstract, location not provided  
  - **Concern** The genetic screen is described only in narrative form. No information is given on the library construction, mutation rate, screening stringency, number of hits, or validation of the identified residues.  
  - **Why it matters** Genetic screens can produce false positives or miss key determinants. Without details on the screen design and validation, the identified residues cannot be considered robustly established.  
  - **Resolution test** Provide full methods for the screen, including library size, selection criteria, and independent validation of each identified residue via site-directed mutagenesis and binding assays.

- **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** "A second, targeted genetic screen revealed a region located in the VqmA^Vc^ DNA-binding domain as necessary to prevent VqmA^Vc^ from binding the *qtip* promoter"  
  - **Evidence pointer** Abstract, location not provided  
  - **Concern** The existence of a negative determinant that actively prevents binding is a strong claim. The supplied text does not describe how this region was identified, how it was tested, or whether the effect is due to direct protein-DNA contacts or indirect conformational effects.  
  - **Why it matters** The proposed mechanism of "prohibition" is mechanistically distinct from a simple lack of positive contacts. The distinction has implications for understanding how specificity evolves.  
  - **Resolution test** Provide detailed methods for the targeted screen and direct biochemical evidence, such as electrophoretic mobility shift assays or structural data, showing that the identified region prevents binding.

- **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** "The residue E194 of VqmA^Phage^ and A192, the equivalent residue in VqmA^Vc^, in the helix-turn-helix motifs contribute to promoter-binding specificity"  
  - **Evidence pointer** Abstract, location not provided  
  - **Concern** The contribution of these specific residues is stated, but no data are shown. It is unclear whether these residues were tested by alanine scanning, whether they are necessary or sufficient for specificity, and what the quantitative effects on binding are.  
  - **Why it matters** The identification of specific residues is a key finding, but without quantitative binding data, the magnitude and direction of the effect cannot be evaluated.  
  - **Resolution test** Provide site-directed mutagenesis data with quantitative binding or reporter assays for both VqmA^Phage^ and VqmA^Vc^ at these positions.

### Minor Comments

- **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Author summary  
  - **Evidence pointer** Author summary, location not provided  
  - **Issue** The phrase "eavesdrops" is informal and may be unclear to some readers.  
  - **Required correction** Replace with a more precise term such as "senses" or "monitors."

- **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Abstract  
  - **Evidence pointer** Abstract, location not provided  
  - **Issue** The abstract does not state the number of residues identified in the screens or the magnitude of the binding differences.  
  - **Required correction** Include quantitative summaries of the key findings, such as the number of mutations identified and the fold-differences in binding or expression.

- **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Interpretation  
  - **Affected element** Proposed mechanism  
  - **Evidence pointer** Abstract, location not provided  
  - **Issue** The proposal that the helix-turn-helix motif and C-terminal flanking residues "function together" is vague. It is unclear whether this means cooperative binding, steric occlusion, or an allosteric effect.  
  - **Required correction** Clarify the proposed mechanistic model with a more explicit description of how the two regions interact.

## Risk / unsupported claims
- The claim that promoter selectivity is driven "exclusively" by the DNA-binding domain is unsupported without domain-swap experiments.
- The identification of specific residues (E194, A192) as contributing to specificity is unverifiable without mutagenesis and binding data.
- The existence of a region in VqmA^Vc^ that "prevents" binding to the *qtip* promoter is an unsupported mechanistic claim without direct biochemical evidence.
- The statement that the identified residues are "required" for binding is not substantiated by the supplied text.
- The broader claim that VqmA transcriptional regulation is "crucial to the survival and persistence" of both the pathogen and the phage is not supported by any data in the supplied material.