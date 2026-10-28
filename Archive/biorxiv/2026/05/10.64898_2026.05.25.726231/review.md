## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no figures, methods, or supplementary data were provided for evaluation
- **Shared manuscript claim summary** The authors report a cryo-EM structure at 3.1 Å resolution of a Streptococcal C5a peptidase-like (ScpH) protein from *Streptococcus sanguinis* that oligomerizes into a double-rowed filament scaffolded on extracellular DNA (eDNA). The structure reveals interlocked dimers formed via reciprocal Ig and protease-Fn domain contacts, propagation into filaments via three additional interfaces, and eDNA engagement through an electropositive cleft involving the C-terminal FIVAR3 domain and a DNA-binding tail that replaces the LPXTG anchor. AlphaFold 3 predictions suggest conservation of dimerization and eDNA binding across a subfamily of streptococcal oral colonizers. The catalytic triad is intact and a co-purified peptide occupies the active site, but proteolytic activity is not demonstrated.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials were supplied
- **Missing materials affecting confidence** Full manuscript, cryo-EM density maps, model validation statistics, AlphaFold 3 prediction details, experimental methods, and any functional assays

## Reviewer
- **Overall assessment** The abstract describes a structurally striking and potentially significant finding: a C5a peptidase-like protease assembled into a filament on eDNA, which would represent a novel mechanism of biofilm functionalization. The structural claims are specific and internally consistent, and the proposed biological implication is thought-provoking. However, the evidence base available for this review is limited to the abstract, and several key claims, particularly regarding conservation, active site occupancy, and functional relevance, cannot be independently assessed. The work is likely to interest structural biologists and microbiologists studying biofilm biology and streptococcal pathogenesis, but the case for a "catalytic platform" remains speculative without functional validation.
- **Who would be interested in the results, and why** Structural biologists studying supramolecular protein assemblies and cryo-EM will find the filament architecture and the eDNA-scaffolding mechanism of interest. Microbiologists and immunologists working on streptococcal pathogenesis, immune evasion, and biofilm formation will be attracted by the potential link between a protease and the extracellular matrix. The proposed repurposing of eDNA from a passive structural component to a catalytic scaffold could also engage researchers in the broader biofilm community.
- **Major strengths** The discovery of an unprecedented supramolecular assembly for a C5a peptidase, which has only been characterized as a monomer, is a clear conceptual advance. The structural resolution of 3.1 Å is appropriate for the claims made about domain organization and interfaces. The identification of a specific eDNA-binding cleft that replaces the canonical LPXTG anchor provides a plausible structural rationale for the new mode of surface association. The use of AlphaFold 3 to extend the finding across a subfamily adds predictive value, though it is not experimental confirmation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract states that the cryo-EM structure at 3.1 Å resolution reveals the filament architecture and eDNA engagement, and that a co-purified peptide occupies the active site.
  - **Evidence pointer** Abstract only; no figures or methods provided
  - **Concern** The abstract provides no information on how the structure was validated, including map quality, model refinement statistics, or local resolution estimates. The claim that a co-purified peptide occupies the active site is presented without any density map evidence or identification of the peptide species. Without these details, the structural interpretation cannot be verified.
  - **Why it matters** The central conclusion, that ScpH forms an eDNA-scaffolded filament with an occupied active site, rests entirely on the reliability of the cryo-EM reconstruction and model building. If the map quality is insufficient in the active site region or at the proposed interfaces, the biological interpretation could be compromised.
  - **Resolution test** Provide the cryo-EM density maps, FSC curves, model-to-map fit statistics, and a clear description of the peptide density in the active site, including its identity or source. The structure should be deposited in the EMDB and PDB with validation reports.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The abstract claims that this structure reveals "a previously unknown mechanism of biofilm functionalization" and transforms eDNA into "a potential catalytic platform."
  - **Evidence pointer** Abstract only; no functional data provided
  - **Concern** The functional significance is inferred from the structure alone. The abstract explicitly states that "proteolytic activity remains to be demonstrated," yet the concluding claim of a "catalytic platform" implies a functional role that is not supported by any experimental evidence. The presence of an intact catalytic triad and a bound peptide does not establish that the filament is catalytically active in the biofilm context.
  - **Why it matters** The broader significance of the work, and its appeal to a wide readership, depends on the functional relevance of the assembly. Without evidence of proteolytic activity, the claim that eDNA is transformed into a catalytic platform is speculative and may overstate the findings.
  - **Resolution test** Provide experimental evidence of proteolytic activity for the ScpH filament, such as cleavage assays with a known C5a substrate or a generic protease substrate, and ideally demonstrate that the filament form retains activity. If activity cannot be shown, temper the conclusions accordingly.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The abstract states that "AlphaFold 3 predictions indicate that both dimerization and eDNA binding are conserved across a subfamily of streptococcal species."
  - **Evidence pointer** Abstract only; no details on the prediction methods or species list provided
  - **Concern** AlphaFold 3 predictions are computational and not experimental validation. The abstract does not specify which species were analyzed, how conservation was scored, or whether the predictions were benchmarked against the experimental structure. The claim of conservation is therefore not verifiable from the provided material.
  - **Why it matters** The extension of the finding to other species is a key part of the biological significance, suggesting broad relevance. If the predictions are based on limited or poorly defined criteria, the claim of conservation may be overstated.
  - **Resolution test** Provide the list of species analyzed, the AlphaFold 3 confidence metrics, and a comparison of predicted interfaces with the experimental structure. Ideally, include experimental validation for at least one additional species.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The term "C5a peptidases" is used without a brief explanation of what C5a is, which may be unclear to readers outside immunology.
  - **Required correction** Add a brief parenthetical explanation, such as "C5a, a complement-derived neutrophil chemoattractant," to improve accessibility.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Clarity of claims
  - **Affected element** Abstract, final sentence
  - **Evidence pointer** Abstract, last sentence
  - **Issue** The phrase "transforming a passive structural component of the biofilm matrix into a potential catalytic platform" is evocative but ambiguous, as it is unclear whether the "transformation" is a physical process or a conceptual reinterpretation.
  - **Required correction** Clarify whether the authors propose that eDNA is actively modified by the protease or that the assembly simply provides a scaffold for the enzyme. Rephrase to avoid overinterpretation.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Abstract, description of domain interactions
  - **Evidence pointer** Abstract, third sentence
  - **Issue** The abstract mentions "reciprocal contacts between the Ig and protease-Fn domains" and "three additional inter-protomer interfaces" but does not specify which domains are involved in the latter, leaving the description incomplete.
  - **Required correction** Briefly identify the domains contributing to the additional interfaces, or refer to a figure where this is shown, to aid comprehension.
- **Technical failings that need to be addressed before the case is established** R1-M1 (structural validation and active site peptide evidence) and R1-M2 (functional demonstration of proteolytic activity) are the primary technical failings. R1-M3 (AlphaFold 3 conservation claims) requires additional detail but is not blocking if the experimental structure is sound.
- **Assessment against Nature-style criteria**  
  *Originality*: The finding of an eDNA-scaffolded filament for a C5a peptidase is novel and unexpected, as these enzymes have only been characterized as monomers. This represents a clear conceptual advance.  
  *Scientific importance*: The potential link between a protease and eDNA in biofilms is significant for understanding streptococcal pathogenesis and biofilm biology, but the importance is currently limited by the lack of functional validation.  
  *Interdisciplinary readership*: The work bridges structural biology, microbiology, and immunology, and the concept of a catalytic scaffold on eDNA could attract interest from the broader biofilm community.  
  *Technical soundness*: The structural claims are plausible but cannot be assessed without the full methods and validation data. The absence of functional data weakens the overall case.  
  *Readability for nonspecialists*: The abstract is generally clear but uses domain-specific terms without explanation, and the final claim is somewhat overstated relative to the evidence.
- **Recommendation posture** Supportive if technical concerns are resolved. The structural discovery is potentially important, but the case is not fully established from the abstract alone. The authors must provide the cryo-EM validation data and demonstrate or temper the claims of proteolytic activity and conservation.

## Risk / unsupported claims
- The claim that the filament represents a "catalytic platform" is unsupported, as proteolytic activity is not demonstrated.
- The claim of conservation across a subfamily of streptococcal species is unsupported, as the AlphaFold 3 predictions are not detailed or experimentally validated.
- The presence of a "co-purified peptide" in the active site is unverifiable without density map evidence or peptide identification.
- The functional relevance of the assembly in biofilm contexts is inferred but not tested.