## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, or supplementary data were available for evaluation
- **Shared manuscript claim summary** The authors report identification and characterization of a Ku-binding motif (KBM) in the C-terminal region of RAG2 (R2CT), based on interactome analysis, proximity ligation assay, calorimetry, mutagenesis, and computational modeling. They propose that this interaction couples DNA breakage and repair during V(D)J recombination.
- **Visible evidence base** Abstract text only; no experimental details, numerical data, figures, or statistical analyses provided
- **Missing materials affecting confidence** Full methods, all figures and tables, mass spectrometry datasets, calorimetry data, PLA quantification, AlphaFold2 confidence metrics, molecular dynamics simulation parameters, and any statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting finding that a KBM in RAG2 C-terminus mediates interaction with Ku70/80, which could have implications for understanding V(D)J recombination. However, the evidence as presented is insufficient to evaluate the robustness of the claims. Several internal inconsistencies and ambiguities in the abstract undermine confidence. The computational predictions are presented with strong causal language despite being in silico. The biological significance claim regarding coupling of breakage and repair is not directly supported by the data described.
- **Who would be interested in the results, and why** Researchers studying V(D)J recombination, non-homologous end joining (NHEJ) repair mechanisms, Ku protein interactions, and DNA damage response pathways. The finding could also interest structural biologists studying protein-DNA complexes and computational biologists using AlphaFold2 for interaction prediction.
- **Major strengths** The study addresses a relevant question about how RAG2 may participate in repair processes beyond cleavage. The combination of experimental approaches (interactome, PLA, calorimetry, mutagenesis) with computational methods (AlphaFold2, molecular dynamics) is commendable. The identification of a specific residue (K503) with functional validation through a mutant is a positive feature.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. KBM-mediated Ku recruitment is an established concept; the novelty lies in applying this to RAG2, which is incremental rather than paradigm-shifting.  
  *Scientific importance*: Potentially relevant to V(D)J recombination field, but the broader significance is not convincingly established from the abstract.  
  *Interdisciplinary readership*: Limited. The work is primarily of interest to immunology and DNA repair specialists.  
  *Technical soundness*: Cannot be adequately assessed from the abstract alone. Internal inconsistencies and missing methodological details prevent evaluation.  
  *Readability for nonspecialists*: The abstract is reasonably accessible but contains technical jargon and an apparent typographical error that affects comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The abstract contains inconsistencies and insufficient detail to support the strong claims made. A revised and complete manuscript would be required for proper evaluation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Internal consistency  
- **Claim pointer** The abstract states the KBM spans "amino acids 589-527"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The amino acid range is given as 589-527, which is numerically inverted. This is either a typographical error or a substantive error in the reported sequence coordinates.  
- **Why it matters** Accurate sequence coordinates are essential for reproducibility and for readers to interpret which region of RAG2 is being studied. An inverted range suggests possible carelessness in data reporting.  
- **Resolution test** Provide the correct amino acid coordinates for the identified KBM and confirm the numbering system used.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The abstract claims "a specific micromolar interaction between this RAG2 region and Ku70/80/DNA complex" was confirmed by calorimetry  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No numerical values for the dissociation constant (Kd), stoichiometry, or thermodynamic parameters are provided. A "micromolar" affinity is relatively weak and may be of questionable biological relevance, yet no context is given for how this affinity compares to other known KBM-Ku interactions.  
- **Why it matters** Without quantitative data, the reader cannot assess whether the interaction is specific, physiologically relevant, or comparable to established KBM interactions. The claim of "specific" interaction requires appropriate controls and quantitative support.  
- **Resolution test** Provide the measured Kd with error estimates, the stoichiometry of binding, and comparison to control peptides or known KBM affinities.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim overreach  
- **Claim pointer** The abstract states "AlphaFold2 prediction coupled with molecular dynamic simulations indicate that the C-terminal part of the RAG2 motif interacts with Ku80 on the same site than the NHEJ factor XLF"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The claim that the RAG2 motif interacts with Ku80 "on the same site" as XLF is based solely on computational prediction. No experimental validation (e.g., competition assays, mutagenesis of the XLF-binding site on Ku80) is described. The phrase "indicate" is used, but the subsequent text treats this as established fact.  
- **Why it matters** Computational predictions, even from AlphaFold2, require experimental validation before making claims about shared binding sites. Overstating computational findings as definitive can mislead readers and may not withstand scrutiny.  
- **Resolution test** Provide experimental evidence such as competition binding assays between RAG2 peptide and XLF for Ku80, or mutagenesis of the predicted XLF-binding site on Ku80 and testing RAG2 binding.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The abstract claims "disruption of the interaction observed with the K503E mutant" supports the role of K503 in DNA interaction  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract states that the N-terminal part of the RAG2 motif interacts with DNA "with a major role of the K503 residue in agreement with disruption of the interaction observed with the K503E mutant." However, it is unclear whether this disruption was observed in the calorimetry experiments, in the PLA experiments, or in a different assay. The type of interaction disrupted (RAG2-Ku vs RAG2-DNA) is ambiguous.  
- **Why it matters** The interpretation of the K503E mutant data depends critically on which interaction was measured and in which assay. Without this context, the claim cannot be properly evaluated.  
- **Resolution test** Specify which assay was used for the K503E mutant, what exactly was disrupted (binding to Ku, binding to DNA, or both), and provide the quantitative data.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "the RAG2 motif KBM can be subdivided in two conserved parts that have no interaction individually" is ambiguous. It is unclear whether "no interaction" refers to no interaction with Ku, no interaction with DNA, or no interaction between the two parts themselves.  
- **Required correction** Clarify what interaction is being referred to and specify the assay used to demonstrate the lack of individual interaction.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "unsupervised interactome analysis" is used without explanation. It is unclear what "unsupervised" means in this context and how it differs from standard interactome approaches.  
- **Required correction** Define the term or use more standard terminology such as "unbiased interactome analysis" with appropriate methodological description.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract content  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract mentions that Ku70 and Ku80 were "among the top 10 hits" in mass spectrometry, but does not provide the full list of hits or any statistical measures of significance.  
- **Required correction** Provide the full list of top hits with enrichment scores or significance thresholds in the full manuscript, and state these in the abstract if space permits.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Biological relevance  
- **Affected element** Abstract interpretation  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract concludes that the Ku-RAG2 interaction "substantiates the model of a tight coupling between DNA breakage and repair during V(D)J recombination." However, the data presented only show that RAG2 can interact with Ku; they do not demonstrate that this interaction is required for or functionally relevant to the coupling of breakage and repair.  
- **Required correction** Soften the conclusion or provide functional data (e.g., effects of KBM mutation on V(D)J recombination efficiency or repair outcomes) to support the coupling model.

## Risk / unsupported claims
- The claim that the RAG2 KBM interacts with Ku80 "on the same site" as XLF is unsupported by experimental evidence and relies solely on computational prediction.
- The claim of "tight coupling between DNA breakage and repair" mediated by the Ku-RAG2 interaction is not supported by any functional data presented in the abstract.
- The biological relevance of the "micromolar" interaction affinity is not established without comparison to known KBM-Ku affinities or demonstration of functional consequences.
- The claim that the KBM "can be subdivided in two conserved parts" implies evolutionary conservation analysis, but no such analysis is described in the abstract.
- The statement that the K503E mutant disrupts "the interaction" is ambiguous and cannot be evaluated without specifying which interaction and assay were used.