## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose a structural model, based on AlphaFold predictions and validated by in vitro assembly and mutagenesis, for a hexameric complex comprising TALE (PBX/PREP) homeodomain heterodimers, the NF-Y trimer, and Sp2 on a composite DECA-CCAAT DNA element. They claim that Sp2 potentiates cooperative DNA binding through two contact interfaces, an SP-box and a novel short linear motif (YA-SLiM), and that the model rationalises existing genomic and biochemical data with implications beyond this specific element.
- **Visible evidence base** Abstract text only; no experimental details, structural coordinates, validation metrics, or raw data are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, AlphaFold model confidence scores, experimental protocols, mutagenesis details, electrophoretic mobility shift assay (EMSA) or other binding data, and any statistical analyses

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting structural hypothesis for cooperative transcription factor binding at composite regulatory elements. The combination of AlphaFold-based modelling with in vitro validation is a reasonable approach, and the identification of a novel short linear motif is potentially valuable. However, the abstract alone provides insufficient evidence to assess the robustness of the structural models, the quality of the experimental validation, or the strength of the claim that this represents a novel mode of cooperative binding. The significance for broader eukaryotic contexts is asserted rather than demonstrated. The work may be of interest to specialists in transcription regulation, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, particularly those focused on cooperative DNA binding by transcription factor complexes, homeodomain proteins, the NF-Y family, and Sp/KLF factors. Developmental biologists working on gene regulatory networks in mammals and zebrafish may also find the DECA-CCAAT element context relevant. Structural biologists interested in protein-DNA complexes and the application of AlphaFold to multi-protein assemblies could find the modelling approach of interest.
- **Major strengths** The study addresses a mechanistically important question, namely how multiple transcription factors cooperate at composite regulatory elements. The use of AlphaFold to generate testable structural predictions is timely and appropriate. The identification of a specific novel motif (YA-SLiM) and its functional validation through mutagenesis provides a concrete mechanistic claim. The combination of computational prediction with in vitro biochemical validation is a sound overall strategy.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract claims that AlphaFold models "position TALE and NF-Y on the respective sites" and predict "the complex arrangement of the MEINOX/PBC heterodimerization module" and "sequence-specific DNA contacts of the HDs to DECA."
  - **Evidence pointer** Abstract only; no model confidence metrics, no comparison with experimental structures, no validation of predicted contacts
  - **Concern** The abstract provides no information on the confidence of the AlphaFold models, such as predicted local distance difference test (pLDDT) scores or predicted aligned error (PAE) values. Multi-protein complexes are notoriously challenging for AlphaFold, and the reliability of the predicted interfaces between TALE, NF-Y, and Sp2 is unknown. Without these metrics or independent structural validation, the accuracy of the proposed arrangement cannot be assessed.
  - **Why it matters** The central claim of the paper is a structural model. If the model is not reliable, the downstream interpretation of cooperativity mechanisms and the proposed novel motif lose their foundation. The absence of confidence metrics prevents readers from evaluating whether the predicted interfaces are credible or artefacts.
  - **Resolution test** Provide AlphaFold confidence scores for all predicted interfaces, show superposition with any available experimental structures of related complexes, and demonstrate that the key predicted contacts are supported by mutagenesis data that specifically disrupt predicted interfaces rather than merely reducing binding.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims that "the models are confirmed by assembly of the recombinant NF-Y/TALE/Sp2 in complex with DNA in vitro" and that "mutagenesis confirms the importance of the SP-box and YA-SLiM for cooperativity."
  - **Evidence pointer** Abstract only; no experimental data shown, no quantitative binding measurements, no controls described
  - **Concern** The abstract states that in vitro assembly and mutagenesis confirm the models, but provides no quantitative data, no description of the assays used, no information on the magnitude of effects, and no mention of controls. "Assembly" of a complex could range from a weak supershift to a high-affinity specific complex. The term "cooperativity" is used without defining how it was measured or what threshold was applied.
  - **Why it matters** The validation experiments are the primary evidence that the computational model has biological relevance. Without quantitative binding data, dose-response relationships, or competition experiments, the claim that Sp2 "potentiates" TALE and NF-Y association is not substantiated. The reader cannot determine whether the mutagenesis effects are specific to the proposed interfaces or reflect general protein destabilisation.
  - **Resolution test** Provide quantitative binding data, such as dissociation constants from EMSA or surface plasmon resonance, for wild-type and mutant complexes, including single and double mutants for each interface. Show that mutations in the SP-box and YA-SLiM specifically reduce cooperativity without affecting individual DNA-binding activities. Include appropriate controls for protein folding and stability.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Originality and significance
  - **Claim pointer** The abstract claims that the models "depict a novel mode of cooperative binding on DNA" and provide "important clues as to how TFs potentially function beyond DECA-CCAAT in different eukaryotic contexts."
  - **Evidence pointer** Abstract only; no comparative analysis with known cooperative binding mechanisms
  - **Concern** The claim of novelty is not contextualised against existing structural and biochemical data on cooperative transcription factor binding. Many cooperative complexes involving homeodomain proteins, NF-Y, and Sp/KLF factors have been described. The abstract does not explain what specifically is novel about this mode of cooperation compared to previously characterised complexes, nor does it provide evidence that the proposed mechanism extends beyond DECA-CCAAT elements.
  - **Why it matters** For a broad-readership journal, the significance of the work depends on the novelty and generalisability of the mechanism. Without explicit comparison to known structures or mechanisms, and without data showing that the same cooperative logic applies at other elements, the broader relevance claim is speculative.
  - **Resolution test** Include a comparative discussion of known cooperative transcription factor complexes, highlighting the specific structural features that distinguish this mode. Provide bioinformatic or experimental evidence that the YA-SLiM and SP-box contacts are conserved or functionally relevant at other genomic loci beyond DECA-CCAAT.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract terminology
  - **Evidence pointer** Abstract text
  - **Issue** The term "DECA-CCAAT composite element" is used without defining what DECA represents or providing the consensus sequence. Nonspecialist readers may not know the arrangement or spacing of these motifs.
  - **Required correction** Define DECA and provide the consensus sequences and spacing for both motifs in the abstract or a figure.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Model validation description
  - **Evidence pointer** Abstract text
  - **Issue** The abstract states that AlphaFold was "applied" but does not specify the version, the input construction (e.g., whether DNA was included, how the complex was assembled), or whether multiple conformations were sampled.
  - **Required correction** Specify the AlphaFold version, the modelling strategy, and whether DNA was included in the prediction or docked post hoc.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Abstract structure
  - **Evidence pointer** Abstract text
  - **Issue** The abstract moves rapidly from the biological question to the structural model to the validation without clearly separating hypothesis generation from hypothesis testing.
  - **Required correction** Consider restructuring the abstract to clearly delineate the computational prediction phase from the experimental validation phase.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The structural model lacks confidence metrics and independent validation, and the experimental confirmation is described without quantitative data. Both must be addressed before the central claims can be evaluated.
- **Assessment against Nature-style criteria**  
  Originality: The identification of a novel short linear motif and a specific tripartite cooperative mechanism has potential originality, but the abstract does not sufficiently differentiate this from previously described cooperative transcription factor complexes.  
  Scientific importance: The question of how transcription factors cooperate at composite elements is important for understanding gene regulation. The specific relevance of DECA-CCAAT in development is well established, but the broader importance of the proposed mechanism is asserted rather than demonstrated.  
  Interdisciplinary readership: The work sits at the interface of structural biology, biochemistry, and gene regulation. It could appeal to a broad audience if the structural novelty and generalisability are clearly established, but the abstract currently reads as specialised.  
  Technical soundness: The combination of AlphaFold with in vitro validation is appropriate, but the lack of confidence metrics and quantitative binding data is a significant weakness.  
  Readability for nonspecialists: The abstract uses field-specific terminology without sufficient definition, and the logical flow from prediction to validation is compressed. It is not fully accessible to nonspecialists.
- **Recommendation posture** Currently not established from the provided evidence. The work has potential interest, and the approach is reasonable, but the abstract alone does not provide sufficient evidence to support the structural and mechanistic claims. A supportive recommendation would require access to the full manuscript with quantitative validation data and model confidence metrics.

## Risk / unsupported claims

- The claim that the AlphaFold models accurately predict the arrangement of the TALE/NF-Y/Sp2 complex is unsupported without confidence metrics or independent structural validation.
- The claim that in vitro assembly "confirms" the models is unsupported without quantitative binding data or appropriate controls.
- The claim that mutagenesis confirms the importance of SP-box and YA-SLiM for cooperativity is unsupported without details on the mutagenesis strategy, the magnitude of effects, and controls for protein stability.
- The claim that the models depict a "novel mode of cooperative binding" is not assessable without comparison to existing structural data on cooperative transcription factor complexes.
- The claim that the findings provide clues for transcription factor function "beyond DECA-CCAAT in different eukaryotic contexts" is speculative and not supported by data presented in the abstract.