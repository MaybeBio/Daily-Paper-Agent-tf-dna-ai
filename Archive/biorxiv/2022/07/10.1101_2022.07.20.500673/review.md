## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplementary figure/table legends) as provided
- **Assessment boundary** Scientific content, technical soundness, structural biology claims, evolutionary inferences, and consistency with the presented evidence
- **Shared manuscript claim summary** The authors report an integrative structural and biophysical characterization of the archaeal Replication Protein A (RPA) from *Pyrococcus abyssi*, including three crystal structures and four cryo-EM structures in apo and ssDNA-bound states. They identify a trimeric core shared with eukaryotes, a novel archaeal-specific domain (ARCD), and a cooperativity module. They propose a mechanism of cooperative ssDNA binding involving self-association of RPA molecules into tetrameric supercomplexes that dissociate upon DNA binding, and infer evolutionary relationships between archaeal and eukaryotic RPA components.
- **Visible evidence base** Crystal structures (apo PabRPA, cooperativity module, Tri-C/dT20), cryo-EM structures (PabRPA/dT35, PabRPA/dT100, tetrameric supercomplex at 3.35 Å and 3.8 Å), SEC-SLS, SAXS, EMSA, SPR, BLI, MST, and structural comparisons with AlphaFold models
- **Missing materials affecting confidence** Electron density maps and validation statistics for cryo-EM reconstructions are not shown in the provided text; figure panels referenced (Figures 1-5, Supplementary Figures S1-S10) are not available for direct inspection; detailed refinement statistics for cryo-EM models are only referenced in Supplementary Tables S1-S2 without content; sequence alignments and structural comparison methodology for the evolutionary analysis are not described in detail

## Reviewer
- **Overall assessment** This manuscript presents a substantial body of structural work on an archaeal RPA, filling a clear gap in the field. The identification of a cooperativity module and the proposed hand-off mechanism for ssDNA between adjacent RPA molecules are potentially significant contributions. However, the manuscript as provided has several technical concerns that need to be addressed, particularly regarding the resolution limits of the cryo-EM maps, the confidence in the AlphaFold-guided modeling, and the strength of the evolutionary conclusions drawn from structural comparisons. The claim of a "newly identified archaeal-specific domain" and its functional role requires more direct experimental validation than is currently presented. The evolutionary narrative, while plausible, is built on structural similarity arguments that need more rigorous quantitative support.
- **Who would be interested in the results, and why** Researchers in DNA replication and repair, particularly those studying SSB/RPA biology across domains of life. Structural biologists interested in protein-nucleic acid complexes and oligomeric assemblies. Evolutionary biologists studying the origin and diversification of replication machinery. The work provides a first full-length archaeal RPA structure and proposes a cooperative binding mechanism that may be generalizable, making it relevant to a broad readership in molecular biology and biochemistry.
- **Major strengths** The study addresses a significant gap by providing the first full-length archaeal RPA structures. The integrative approach combining multiple structural techniques with biophysical assays is commendable. The identification of a potential cooperativity module and the proposed hand-off mechanism are novel and interesting. The evolutionary analysis, while needing refinement, addresses an important question about the ancestry of eukaryotic RPA.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (cryo-EM resolution and model confidence), R1-M2 (AlphaFold-guided modeling validation), R1-M3 (evolutionary inference robustness), R1-M4 (functional validation of ARCD)
- **Assessment against Nature-style criteria** **Originality**: High. The first full-length archaeal RPA structures and the proposed cooperativity mechanism are novel. **Scientific importance**: High. RPA is essential across eukaryotes and archaea, and understanding its mechanism and evolution has broad implications. **Interdisciplinary readership**: Moderate to high. The work bridges structural biology, biochemistry, and evolutionary biology, and should appeal to readers across these fields. **Technical soundness**: Currently moderate. The structural determinations appear carefully executed, but the resolution limits of several cryo-EM maps and the reliance on AlphaFold for key interaction interfaces raise concerns that need to be addressed. **Readability for nonspecialists**: Moderate. The manuscript is generally well-written but assumes familiarity with structural biology terminology and RPA biology. The abstract is accessible, but the results section would benefit from clearer explanations of the significance of specific structural features for a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core structural findings are likely to be valuable, but the current evidence does not fully establish the proposed cooperative binding mechanism or the evolutionary scenario with the confidence required for a high-impact journal.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The cryo-EM structures of PabRPA/dT35 (6.3 Å) and PabRPA/dT100 (8.2 Å) are used to support the proposed mechanism of ssDNA hand-off between adjacent RPA molecules and the conformational changes in the cooperativity module.
- **Evidence pointer** Results section "Cryo-EM structure of the full-length PabRPA bound to short ssDNA" and "Structural basis for the assembly of multiple PabRPA molecules on ssDNA"; Supplementary Table S2
- **Concern** The global resolutions of 6.3 Å and 8.2 Å for the two key cryo-EM reconstructions are very low. At these resolutions, it is not possible to reliably assign secondary structure elements, let alone identify specific side-chain interactions or accurately model the path of ssDNA. The manuscript states that rigid-body fitting of known crystal structures was used, but this approach cannot validate the proposed domain rearrangements or the specific protein-protein and protein-DNA contacts that are central to the proposed hand-off mechanism. The local resolution of the maps, particularly at the interfaces between RPA molecules and at the DNA-binding sites, is not reported. Without this information, the structural basis for the cooperative binding mechanism is not established.
- **Why it matters** The central claim of the manuscript is a novel mechanism of cooperative ssDNA binding involving specific intermolecular interactions. If the key structural evidence is derived from maps at resolutions where such interactions cannot be visualized, the mechanism remains speculative. The authors need to demonstrate that the features they interpret are actually resolved in their maps.
- **Resolution test** Provide local resolution estimates for the cryo-EM maps, particularly at the interfaces between RPA protomers and at the DNA-binding sites. Show representative density for the key interaction interfaces with the fitted models. If the resolution is insufficient to resolve side chains, clearly state the limitations and provide alternative biochemical or biophysical evidence (e.g., crosslinking, mutagenesis) that supports the proposed contacts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript uses AlphaFold predictions to model the protein-protein interactions between adjacent RPA molecules in the dT100 complex and to interpret the cryo-EM density at 8.2 Å resolution.
- **Evidence pointer** Results section "Structural basis for the assembly of multiple PabRPA molecules on ssDNA"; Methods section "AlphaFold model predictions"; Supplementary Figure S8
- **Concern** The manuscript states that an AlphaFold prediction of the interaction between two RPA molecules was used to model the dT100 cryo-EM map. While AlphaFold is a powerful tool, its predictions of protein-protein interfaces, especially for large multi-domain complexes, are not always accurate and need experimental validation. The manuscript does not provide a confidence score (e.g., ipTM or PAE) for the predicted complex, nor does it describe how the AlphaFold model was fitted into the 8.2 Å map. At this resolution, the fit could be ambiguous, and the model could be biased by the prediction. The claim that the AlphaFold model "can be nicely fitted" is not a substitute for experimental validation of the interface.
- **Why it matters** The proposed hand-off mechanism relies on a specific interaction between the OB-1 domain of one RPA molecule and the trimerization core of the adjacent molecule. If this interaction is only supported by an unvalidated AlphaFold model fitted into a low-resolution map, the mechanism is not convincingly established.
- **Resolution test** Provide the AlphaFold confidence metrics (ipTM, PAE) for the predicted complex. Describe the fitting procedure in detail, including how the model was placed into the map and how the fit was assessed. Ideally, validate the predicted interface with site-directed mutagenesis coupled with a biochemical assay (e.g., crosslinking, analytical ultracentrifugation, or a functional DNA-binding assay).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Evolutionary inference
- **Claim pointer** The manuscript claims that structural comparisons suggest RPA evolved in Archaea from a bacterial-like SSB ancestor, and that eukaryotic RPA was inherited from an archaeal RPA ancestor.
- **Evidence pointer** Results section "Evolution of RPA in Archaea and Eukarya"; Figure 5
- **Concern** The evolutionary conclusions are based on a structural comparison of OB domains from a limited set of representative proteins, supplemented with AlphaFold models. The manuscript does not describe the methodology for the all-against-all structural comparison (e.g., which algorithm was used, how the tree was constructed, what the statistical support for the branches is). The statement that "structural comparisons clearly distinguish the two sets of proteins" is not supported by any quantitative data. The evolutionary scenario is plausible but is presented as a narrative without rigorous phylogenetic or phylogenomic analysis.
- **Why it matters** The evolutionary claims are a significant part of the manuscript's broader impact. If they are not supported by a robust analysis, they weaken the paper's conclusions and could be misleading to readers.
- **Resolution test** Provide a detailed description of the structural comparison methodology, including the algorithm used, the dataset, and the statistical support for the tree. Consider performing a more formal phylogenetic analysis using structural or sequence data. Alternatively, soften the evolutionary claims to be more clearly speculative and hypothesis-generating.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Functional validation
- **Claim pointer** The manuscript proposes that the ARCD domain contributes to cooperative binding by pre-connecting RPA molecules before they bind to DNA.
- **Evidence pointer** Results section "Architecture of the archaeal RPA heterotrimeric complex" and "DNA-binding properties of PabRPA trimerization core and cooperativity module"; Figure 3d; Supplementary Figure S8
- **Concern** The functional role of the ARCD domain is inferred primarily from structural observations and a single MST experiment with a deletion construct. The MST data show a partial reduction in cooperativity (Hill coefficient from 2.0 to 1.8) upon ARCD deletion, which is a modest effect. The manuscript does not provide a direct demonstration that ARCD mediates the proposed pre-connection between RPA molecules. The structural evidence for the ARCD/OB-4 interaction comes from a crystal lattice contact and a low-resolution cryo-EM map, which may not reflect the solution state.
- **Why it matters** The ARCD domain is presented as a novel and functionally important feature. If its role is not convincingly demonstrated, the significance of this finding is diminished.
- **Resolution test** Provide additional biochemical evidence for the role of ARCD in pre-connecting RPA molecules. This could include crosslinking experiments, analytical ultracentrifugation, or size-exclusion chromatography coupled with multi-angle light scattering (SEC-MALS) to show that ARCD mediates oligomerization in solution. A more complete mutagenesis study, targeting residues at the predicted ARCD/OB-4 interface, would also strengthen the claim.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction
- **Issue** The abstract and introduction use the term "cooperativity module" without a clear definition of what constitutes this module at the domain level. The reader is left to infer that it refers to the OB-1 domain and the ARCD, but this is not explicitly stated until later in the results.
- **Required correction** Define the "cooperativity module" clearly in the introduction, specifying which domains it comprises and how it was identified.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Cryo-EM data acquisition and image processing"
- **Evidence pointer** Methods section; Supplementary Table S2
- **Concern** The methods state that the dT35 dataset was collected on a 200 kV Glacios microscope and the dT100 dataset on the same microscope, but the dT100 dataset was collected in "integration mode" while the dT35 was in "electron counting mode." The implications of this difference for data quality are not discussed.
- **Required correction** Briefly explain the choice of different acquisition modes and any potential impact on the resolution or interpretability of the resulting maps.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Results section "Crystal structure of the PabRPA trimerization core bound to ssDNA"
- **Evidence pointer** Results section; Figure 2b
- **Concern** The description of the DNA-binding site mentions that "Rpa3 does not contact ssDNA in the structure of PabRPA." This is an interesting observation, but the manuscript does not discuss the potential functional implications of this difference compared to eukaryotic RPA, where the corresponding subunit also plays a structural role.
- **Required correction** Add a brief discussion of the functional significance of Rpa3 not contacting DNA, comparing it to the eukaryotic system.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion of the comparison with the eukaryotic RPA is somewhat brief. The manuscript mentions similarities and differences but does not fully explore the implications of the proposed hand-off mechanism for understanding eukaryotic RPA function.
- **Required correction** Expand the discussion to more thoroughly compare the proposed archaeal mechanism with the current understanding of eukaryotic RPA dynamics and function, and discuss the potential implications for DNA replication and repair in eukaryotes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5
- **Evidence pointer** Figure 5
- **Concern** The structural tree in Figure 5 is described in the text but the figure itself is not available for review. The legend is not provided in the manuscript text.
- **Required correction** Ensure the figure legend clearly describes the methods used to generate the tree, the color coding, and the statistical support for the branches.

## Risk / unsupported claims
- The claim that the cryo-EM structures reveal "for the first time how ssDNA is handed over from one RPA molecule to the other" is not fully supported by the evidence presented, given the low resolution of the key maps (6.3 Å and 8.2 Å) and the reliance on AlphaFold for modeling the interaction interface.
- The claim that the ARCD domain "contributes to cooperative binding, by pre-connecting together RPA molecules before they bind to DNA" is not directly demonstrated. The structural evidence is based on a crystal lattice contact and a low-resolution cryo-EM map, and the functional evidence is limited to a single MST experiment with a modest effect.
- The evolutionary scenario proposing that RPA evolved from a bacterial-like SSB ancestor and that eukaryotic RPA was inherited from an archaeal ancestor is presented without a detailed description of the methodology or statistical support for the structural tree.
- The statement that the "cooperativity module" is a "newly identified" feature is not fully contextualized. The manuscript does not discuss whether similar modules have been proposed or observed in other archaeal or eukaryotic RPA homologs.