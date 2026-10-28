## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure legends
- **Assessment boundary** Structural and functional characterization of the lysosomal mTORC1–TFEB–Rag–Ragulator megacomplex by cryo-EM, with supporting cellular validation
- **Shared manuscript claim summary** The authors report cryo-EM structures of TFEB bound to Rag–Ragulator complexes, with and without mTORC1, revealing a 2:1 Rag–Ragulator:Raptor stoichiometry. They identify a RagC GDP-dependent clamp that binds the TFEB N-terminus and a second RagC GDP-dependent interface bridging the two Rag–Ragulator complexes. Mutational analysis in cells supports the functional importance of these interfaces for TFEB phosphorylation and localization.
- **Visible evidence base** Main text figures 1–5, Extended Data figures 1–10, Extended Data table 1, Supplementary figures 1–2, Supplementary video 1
- **Missing materials affecting confidence** Atomic coordinates and cryo-EM maps are not provided in the manuscript text; validation statistics beyond resolution are not fully detailed; raw western blot images are only in supplementary; no structural statistics table for the megacomplex model is included in the visible text

## Reviewer
- **Overall assessment** This manuscript presents a significant structural advance in understanding how TFEB, a master regulator of lysosomal biogenesis, is selectively presented to mTORC1 for phosphorylation. The cryo-EM structures are of high quality, and the identification of a RagC GDP-dependent clamp mechanism provides a compelling molecular explanation for the unique dependence of TFEB phosphorylation on FLCN and the RagC nucleotide state. The cellular validation experiments are thoughtful and largely support the structural conclusions. The work will be of broad interest to the autophagy, lysosome, and mTOR signaling communities. However, several technical and interpretive concerns need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Cell biologists and biochemists studying mTORC1 signaling, autophagy, lysosomal biogenesis, and transcription factor regulation. Structural biologists interested in large multi-protein complexes. Clinicians and researchers focused on lysosomal storage disorders, neurodegenerative diseases, and Birt–Hogg–Dubé syndrome, where TFEB and FLCN are relevant therapeutic targets. The work provides a molecular framework for understanding substrate specificity in mTORC1 signaling that extends beyond TFEB.

- **Major strengths** 
  1. The structures are determined at high resolution (2.8–3.2 Å for key components) and reveal a previously unknown 2:1 stoichiometry of Rag–Ragulator to Raptor, which is unexpected and mechanistically important.
  2. The identification of a RagC GDP-dependent clamp that specifically engages the TFEB N-terminus provides a clear structural basis for the long-standing observation that TFEB phosphorylation requires FLCN and the RagC GDP state.
  3. The cellular validation is well-designed, using multiple complementary assays (localization, phosphorylation, co-immunoprecipitation) and appropriate mutant controls.
  4. The authors carefully address the relationship between their findings and prior work, including reconciling apparent discrepancies with a recent publication on RagC's role in TFEB recruitment.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the megacomplex structure was determined at 3.7 Å overall resolution, improved to 3.2 Å by symmetry expansion and local refinement, and that this allowed building an accurate atomic model of the entire complex containing 36 polypeptide chains.
- **Evidence pointer** Main text, "Cryo-EM structure of the megacomplex" section; Extended Data Fig. 8; Extended Data Table 1
- **Concern** The manuscript does not provide a complete set of cryo-EM validation statistics for the megacomplex model. While resolutions are quoted, key metrics such as map-model FSC, MolProbity scores, Ramachandran statistics, and per-residue model confidence are not presented in the visible text. For a complex of this size (36 chains), model building is challenging, and the absence of these statistics makes it difficult to assess the reliability of the atomic model, particularly for the TFEB regions and the interfaces that are central to the conclusions.
- **Why it matters** The structural claims are the foundation of the paper. Without robust validation statistics, readers cannot evaluate whether the reported interactions, particularly the RagC GDP-dependent clamp and the TFEB–Raptor interface, are reliably modeled. This is especially important given that the TFEB density was not observed in the absence of Raptor, suggesting conformational heterogeneity.
- **Resolution test** Provide a complete cryo-EM validation table for all reported maps and models, including FSC curves, map-model correlation, and geometry statistics. Deposit and reference the PDB and EMDB accession codes. If the megacomplex model has regions of lower confidence, these should be explicitly indicated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors propose that the TPAI motif of TFEB binds to the Raptor N-terminal conserved (RNC) domain at a site overlapping the 4E-BP1 RAIP binding site, but they report that mutation of this motif has no effect on TFEB phosphorylation or localization.
- **Evidence pointer** Main text, "Bridging Rag–Ragulator complexes" section; Extended Data Fig. 7d,e
- **Concern** The authors identify a direct TFEB–Raptor interaction involving the TPAI motif, yet their own mutational data show that disrupting this interaction has no functional consequence. This is presented as evidence that the interaction is "secondary" or "auxiliary," but the logic is somewhat circular. If the TPAI–Raptor interaction is dispensable for TFEB phosphorylation, what is its actual role? The authors speculate it may stabilize the complex, but they do not test this directly. The structural prominence of this interface, contrasted with its apparent functional irrelevance, is confusing and needs more explicit discussion.
- **Why it matters** The paper claims to reveal a "megacomplex" with multiple new interfaces. If one of the major new interfaces (TFEB–Raptor) has no demonstrated function, the significance of the overall architecture is weakened. The authors should either provide evidence for a functional role of this interaction or more clearly frame it as a structural observation whose functional significance remains unknown.
- **Resolution test** Provide additional experiments to test the role of the TPAI–Raptor interaction, such as measuring binding affinity of TFEB mutants to Raptor in vitro, or assessing the stability of the megacomplex with TPAI mutants. Alternatively, clearly state in the discussion that the functional role of this interface is not yet established and discuss why it may be dispensable.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the double use of RagC GDP contacts in both Rag dimers explains the strong dependence of TFEB phosphorylation on FLCN and the RagC GDP state."
- **Evidence pointer** Main text, Abstract and Discussion
- **Concern** While the structural data clearly show two RagC GDP-dependent interfaces, the causal link to FLCN dependence is inferred rather than directly demonstrated. The authors do not experimentally manipulate FLCN activity in the context of their mutants to show that the structural interfaces they identify are the ones through which FLCN exerts its effect. The logic is plausible, but the claim as stated is stronger than the evidence supports.
- **Why it matters** The paper's central thesis is that this structure explains the unique FLCN dependence of TFEB phosphorylation. If this link is not directly tested, the conclusion remains a hypothesis, albeit a well-supported one. Directly testing this would substantially strengthen the paper.
- **Resolution test** Perform experiments where FLCN is knocked down or inhibited in the context of the RagC clamp mutants, to determine whether the mutants bypass the FLCN requirement. Alternatively, test whether the RagC GDP state is required for TFEB binding in vitro using purified components with defined nucleotide states.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "TFEB phosphorylation by mTORC1 is independent of Rheb" and that their structure reveals "the alternative structural mechanism of Rheb-independent TFEB phosphorylation by mTORC1."
- **Evidence pointer** Main text, "Cryo-EM structure of the megacomplex" section; Extended Data Fig. 10
- **Concern** The claim of a "Rheb-independent mechanism" is based on prior work (ref. 7) and the structural observation that TFEB is positioned near the active site without the conformational changes associated with Rheb binding. However, the structure does not include Rheb, and the authors do not directly compare the megacomplex structure with a Rheb-bound mTORC1 structure in the same study. The mechanistic distinction between Rheb-dependent and Rheb-independent substrate phosphorylation is interesting but is not fully developed.
- **Why it matters** This is a potentially important conceptual advance, but as presented it is somewhat speculative. The authors should more carefully delineate what is directly shown by their data versus what is inferred from comparison with prior structures.
- **Resolution test** Provide a direct structural comparison between the megacomplex and a Rheb-bound mTORC1 structure, or perform experiments that test the Rheb independence of TFEB phosphorylation in their system. At minimum, temper the language to reflect the inferential nature of this claim.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and assumes significant background knowledge. Terms such as "TOR signalling motif," "RagC GTPase activating protein FLCN," and "megacomplex" are introduced without brief context. The significance of the work for broader biological understanding could be stated more clearly.
- **Required correction** Consider adding one sentence of context on why TFEB phosphorylation by mTORC1 is important (e.g., its role in coordinating cellular clearance with nutrient status) and what is conceptually novel about the "megacomplex" architecture.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Protein expression and purification"
- **Evidence pointer** Methods section
- **Issue** The methods state that wild-type TFEB-GFP did not co-elute with the Rags (Supplementary Fig. 2), but the conditions for this control experiment are not described in detail. It is unclear whether the same expression and purification conditions were used as for the mutant TFEB.
- **Required correction** Provide a brief description of the control experiment conditions, or reference a supplementary methods section where this is detailed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of Birt–Hogg–Dubé syndrome and therapeutic implications is brief. Given the potential clinical relevance, a slightly more detailed discussion of how these structural insights might inform therapeutic strategies would broaden the appeal.
- **Required correction** Expand slightly on the therapeutic implications, perhaps by discussing how the specific interfaces identified could be targeted and what the potential challenges might be.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Figure 3
- **Evidence pointer** Figure 3 and legend
- **Issue** The statistical details for the quantification in Figure 3a,d,i–n are not fully described in the figure legend. It is stated that n represents independent fields, but the number of independent experiments is not clear.
- **Required correction** Clarify in the figure legend whether the n values represent fields from a single experiment or pooled from multiple independent experiments, and state the number of independent replicates.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Main text, "Bridging Rag–Ragulator complexes" section
- **Evidence pointer** Main text
- **Issue** The description of the structural arrangement, particularly the "closed triangle" and the relationship between the two Rag–Ragulator complexes, is difficult to follow without a schematic. The text refers to Extended Data Fig. 4, but a simplified schematic in the main figure would aid comprehension.
- **Required correction** Consider adding a schematic diagram to Figure 1 or 2 that illustrates the overall architecture and the two Rag–Ragulator complexes in a simplified manner.

## Risk / unsupported claims
- The claim that the structure "explains the strong dependence of TFEB phosphorylation on FLCN" is inferred from structural data and prior functional studies, but not directly tested in this manuscript (R1-M3).
- The claim of a "Rheb-independent mechanism" for TFEB phosphorylation is based on indirect evidence and comparison with prior structures, not directly demonstrated here (R1-M4).
- The functional significance of the TFEB–Raptor TPAI interaction is unclear, as the authors' own mutational data show it is dispensable for TFEB phosphorylation (R1-M2).
- The statement that the TFEB N-terminus is "both necessary and sufficient" for complex formation is supported by the structure and the in vitro binding of residues 1–109, but the "sufficiency" claim is only tested with a slightly longer construct, not the minimal 2–105 region observed in the structure.
- The physiological relevance of the 2:1 Rag–Ragulator:Raptor stoichiometry is not directly tested; the authors do not show that this stoichiometry exists in cells.