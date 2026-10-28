## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the supplied text; no external verification of data or figures possible
- **Shared manuscript claim summary** The authors identify Arg105 in the α3 helix of ZmHsf17's DNA-binding domain as a critical residue for recognition of heat shock elements in the ZmPAH1 promoter, validate this finding in the paralog ZmHsf05 (Arg93), demonstrate that flanking sequences (but not the inter-GAA spacer) modulate binding specificity, and show that the α3 helix and an "RQLN" motif are evolutionarily conserved across diverse taxa
- **Visible evidence base** Text descriptions of results from AlphaFold 3 modeling, site-directed mutagenesis, EMSA experiments, sequence alignment, and phylogenetic reconstruction; references to Figures 1-6 and Table S1 (figures and supplementary materials not directly viewable)
- **Missing materials affecting confidence** Actual figures and supplementary data (Figure S1, Table S1), raw EMSA gel images, AlphaFold 3 confidence metrics, sequence alignment files, phylogenetic tree with bootstrap values, ChIP-seq data referenced but not shown, and experimental replicates/statistical analyses

## Reviewer
- **Overall assessment** This manuscript addresses a focused question in plant heat stress biology: identifying specific amino acid residues in maize HsfA2 transcription factors that mediate DNA binding to heat shock elements. The work combines computational prediction with targeted mutagenesis and EMSA validation, and extends findings to a paralog and across evolutionary scales. The core finding that a single conserved arginine in the α3 helix is indispensable for DNA binding is plausible and consistent with prior work in other systems. However, the manuscript as presented has several limitations that prevent full assessment: key figures are not viewable, the EMSA data appear qualitative without quantification or replicates described, the AlphaFold 3 methodology lacks critical validation details, and the evolutionary analysis conflates sequence conservation with functional significance without experimental support. The study is technically sound in its basic approach but would benefit from additional controls, quantitative analysis, and clearer presentation of the structural modeling evidence. The writing is generally clear but contains some overstatements relative to the evidence presented.

- **Who would be interested in the results, and why** Plant molecular biologists studying heat stress responses and transcription factor function would find this work relevant, particularly those working on Hsf family members in crops. Researchers interested in protein-DNA recognition mechanisms and the evolution of transcription factor DNA-binding domains would also find value. The potential application to engineering heat-tolerant crops through targeted modification of Hsf proteins could interest plant biotechnology and breeding communities. The evolutionary analysis spanning archaea to plants may attract comparative genomics researchers.

- **Major strengths** The study addresses a specific, mechanistically important question that has been underexplored in plants. The combination of computational prediction (AlphaFold 3) with experimental validation (mutagenesis plus EMSA) provides complementary evidence. The inclusion of a paralog (ZmHsf05) strengthens the generalizability of the finding. The chimeric promoter analysis systematically dissects the contribution of flanking sequences versus core elements. The evolutionary analysis across 25 species provides a broad comparative perspective.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of structural modeling
- **Claim pointer** "Modeling in AlphaFold 3 predicted specific interactions between ZmHsf17-DBD-OD homodimer and the double-stranded canonical HSE motif in the ZmPAH1 promoter" and "Structural modeling predicts that five residues (N99, S102, R105, N108, and Y110) within the α3 helix of the DBD potentially form hydrogen bonds with the DNA backbone"
- **Evidence pointer** Section 2.1, Figure 1c; Methods 4.2
- **Concern** The AlphaFold 3 modeling is presented as the basis for identifying candidate interacting residues, but critical validation details are missing. The manuscript does not report confidence scores, model quality metrics, or whether the predicted complex was validated against known Hsf-DNA structures. AlphaFold 3 is a powerful tool but its predictions for protein-DNA complexes require careful benchmarking. The hydrogen bond analysis relies on PyMOL's built-in detection algorithm with stated geometric criteria, but no information is provided about how many alternative conformations were sampled, whether the prediction was reproducible, or how the specific DNA sequence was selected for modeling. The claim that specific residues "potentially form hydrogen bonds" is appropriately hedged, but the subsequent experimental design depends entirely on this prediction being correct.
- **Why it matters** The entire experimental strategy hinges on the accuracy of the AlphaFold 3 prediction. If the predicted interface is incorrect, the mutagenesis experiments may be testing irrelevant residues. Without confidence metrics or validation against experimental structures, the computational foundation of the study cannot be properly evaluated.
- **Resolution test** Provide AlphaFold 3 confidence scores (ipTM, pTM), show superposition of predicted complex with known Hsf-DNA structures (e.g., yeast or human Hsf1), and include a control experiment testing a residue predicted to be outside the interface.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence quality
- **Claim pointer** "The EMSA demonstrated that ZmHsf17 bound the ZmPAH1 HSE probes, forming distinct retarded complexes. Notably, the R105A mutation abolished HSE binding, whereas the T109A and K142A mutants retained DNA-binding capacity" and "The EMSA demonstrated that ZmHsf05 bound the ZmPAH1 HSE probes, while the R93A mutation completely abolished DNA binding"
- **Evidence pointer** Sections 2.2 and 2.3, Figures 2d and 4c; Methods 4.5
- **Concern** The EMSA results are described qualitatively without quantification, replicates, or statistical analysis. The manuscript states that R105A "abolished" binding and T109A/K142A "retained" binding, but no band intensity measurements, dilution series, or competition experiments are shown. The methods describe a single binding condition (25 °C, 30 min) without titration of protein concentrations. For a study whose central claim is that a single residue is critical for DNA binding, the evidence should include quantitative binding affinity measurements (e.g., Kd determination) or at minimum multiple protein concentrations demonstrating a clear difference. Additionally, the EMSA appears to have been performed only once per construct based on the description.
- **Why it matters** The central conclusion that Arg105 is indispensable for DNA binding rests entirely on the EMSA results. Without quantitative data, replicates, or proper controls (e.g., competition with unlabeled probe, mutant probe controls), the possibility of experimental artifact or non-specific effects cannot be excluded. The difference between "abolished" and "retained" binding needs statistical support.
- **Resolution test** Provide quantitative EMSA data with at least three independent replicates, protein concentration titrations, calculated apparent Kd values for wild-type and mutant proteins, and appropriate controls including competition assays and binding to mutant probes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of evolutionary analysis
- **Claim pointer** "Comparative evolutionary analysis of DNA-binding domain sequences from 25 phylogenetically diverse species reveals that the α3 helix constitutes the most conserved structural element" and "a conserved tetrapeptide motif 'RQLN' was identified in the α3 helix across all analyzed species"
- **Evidence pointer** Section 2.5, Figure 6a; Methods 4.6
- **Concern** The evolutionary analysis identifies the "RQLN" motif as conserved across all 25 species, but the functional significance of this conservation is inferred rather than demonstrated. The manuscript states that "the arginine residue (R) within the 'RQLN' tetrapeptide was identified as a critical determinant of HSE binding" based on the mutagenesis data, but this is a post-hoc interpretation. The analysis does not include any positive selection detection, evolutionary rate analysis, or comparison of the α3 helix conservation against other regions of the protein to establish that this region is under stronger purifying selection. The inclusion of a thermophilic archaeon in the analysis is interesting but raises questions about whether the "RQLN" motif in archaea actually functions in HSE binding, given that canonical HSEs are eukaryotic regulatory elements.
- **Why it matters** The claim that the α3 helix is "the most conserved structural element" requires quantitative comparison of conservation across all structural elements, not just visual inspection. The functional interpretation of the conserved arginine in species that do not have canonical HSEs (e.g., archaea) needs discussion. Without these analyses, the evolutionary claims are descriptive rather than functionally informative.
- **Resolution test** Provide quantitative conservation scores (e.g., ConSurf or Rate4Site analysis) for all structural elements of the DBD, test whether the "RQLN" motif in non-plant species can bind HSE-like sequences, and discuss the functional relevance of the motif in organisms without canonical HSEs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Specificity of flanking sequence effects
- **Claim pointer** "Sequence substitution experiments among distinct HSEs demonstrated that flanking sequences upstream and downstream of the HSE core synergistically contribute to the specificity of DNA-binding domain recognition" and "flanking sequences at both termini but not the inter-GAA spacer critically determine recognition specificity"
- **Evidence pointer** Section 2.4, Figure 5b-d; Methods 4.5
- **Concern** The chimeric HSE experiments are described as showing that flanking sequences determine binding specificity, but the manuscript does not provide the actual sequences of the chimeric constructs or the EMSA results in sufficient detail. The claim that "flanking sequences at both termini" are important is based on constructs where either the upstream 16 bp, the downstream 16 bp, or the 2 bp spacer was swapped. However, the manuscript does not show whether the effect is additive, synergistic, or dependent on specific sequence features (e.g., GC content, specific nucleotides). The conclusion that the inter-GAA spacer plays a "negligible role" is based on a single construct where only 2 bp were changed, which may not be sufficient to detect an effect.
- **Why it matters** The specificity of Hsf binding to different HSEs is a key mechanistic question. The current analysis is too coarse to determine whether the flanking sequence effects are due to specific base contacts, DNA shape, or indirect readout. A more systematic mutagenesis approach would be needed to establish the sequence determinants of binding specificity.
- **Resolution test** Provide complete sequences of all chimeric constructs, perform systematic mutagenesis of flanking regions (e.g., scanning mutations, base substitutions), and include quantitative binding data for each construct to establish the sequence determinants of specificity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness of methods
- **Affected element** EMSA methodology
- **Evidence pointer** Section 4.5
- **Issue** The EMSA methods section is incomplete. It does not specify the protein concentrations used, the amount of DNA probe per reaction, the specific activity of the labeled probe, or the exposure times for detection. The description of the binding reaction is vague ("biotinylated an HSE probe, a mutation HSE probe, a purified recombinant protein, an EMSA/Gel-Shift buffer, a competitive probe, a competitive mutation HSE probe, and nuclease-free water").
- **Required correction** Provide a complete EMSA protocol with all reagent concentrations, volumes, incubation conditions, and detection parameters. Clarify the composition of the binding reaction and the concentrations of each component.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** All quantitative claims
- **Evidence pointer** Sections 2.2-2.5
- **Issue** No statistical analyses are reported anywhere in the manuscript. The EMSA results, sequence conservation claims, and phylogenetic inferences are all presented without measures of variability or significance testing.
- **Required correction** Add appropriate statistical analyses for all quantitative comparisons, including replicates for EMSA experiments and statistical tests for conservation differences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 1-6
- **Evidence pointer** Sections 2.1-2.5
- **Issue** The figures are referenced but not viewable in the provided text. Based on the descriptions, Figure 1 appears to contain multiple panels (a-c) with structural models, but the resolution and clarity of the predicted interactions cannot be assessed. Figure 6 includes a phylogenetic tree and sequence logo, but the readability of these figures is unknown.
- **Required correction** Ensure all figures are high-resolution, clearly labeled, and accessible to readers. Consider providing structural models as supplementary PDB files for independent verification.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Sections 1 and 3
- **Issue** The introduction and discussion cite relevant literature but do not adequately contextualize the findings within the broader field of plant Hsf-DNA interactions. The discussion of conserved arginine residues in other systems (yeast, Drosophila, human) is brief and does not fully explore the structural basis for arginine-mediated DNA recognition.
- **Required correction** Expand the discussion to include more detailed comparison with structural studies of Hsf-DNA complexes in other organisms and discuss the implications of the findings for understanding Hsf functional diversity.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Abstract, Sections 1-3
- **Issue** The manuscript uses "ZmHsf17" and "ZmHsfA2" somewhat interchangeably. The title refers to "ZmHsfA2'S DNA-Binding Domain" while the text primarily uses "ZmHsf17." The relationship between these designations should be clarified early in the manuscript.
- **Required correction** Define the relationship between ZmHsf17 and ZmHsfA2 in the introduction and use consistent terminology throughout.

- **Technical failings that need to be addressed before the case is established** R1-M1 (AlphaFold 3 validation), R1-M2 (quantitative EMSA with replicates and controls). These are the two concerns that directly affect whether the central claim of the manuscript (Arg105 as a critical DNA-binding residue) is supported by the evidence.

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The identification of specific residues in plant Hsf DBDs involved in DNA binding is a useful contribution, but the finding that a conserved arginine in the recognition helix is critical for DNA binding is not conceptually novel, as similar findings exist in yeast, Drosophila, and human systems. The extension to maize and the paralog comparison adds some originality.
  - Scientific importance: Moderate. The work provides mechanistic insight into plant Hsf-DNA interactions, which could inform crop engineering strategies. However, the significance is limited by the narrow scope (one residue in one transcription factor family) and the lack of in vivo validation.
  - Interdisciplinary readership: Limited. The manuscript is primarily of interest to plant molecular biologists and stress physiologists. The structural and evolutionary analyses are not sufficiently developed to attract a broader readership.
  - Technical soundness: The basic approach is sound, but the lack of quantitative data, replicates, and validation of the computational predictions weakens the technical foundation. The AlphaFold 3 predictions need benchmarking, and the EMSA data need quantification.
  - Readability for nonspecialists: The manuscript is generally well-written and accessible to readers with a background in molecular biology. The introduction provides adequate context, and the results are presented logically. However, some sections (particularly the evolutionary analysis) could be clearer for nonspecialists.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant question and the overall approach is reasonable, but the current evidence is insufficient to fully support the central claims. The authors should provide quantitative EMSA data with replicates, validate the AlphaFold 3 predictions, and strengthen the evolutionary analysis before the case is fully established.

## Risk / unsupported claims
- The claim that "the α3 helix constitutes the most conserved structural element" is not quantitatively supported; no conservation scoring is provided.
- The claim that flanking sequences "synergistically contribute" to binding specificity is based on a limited set of chimeric constructs without systematic analysis.
- The functional significance of the "RQLN" motif in organisms without canonical HSEs (e.g., archaea) is asserted without experimental support.
- The statement that "thirteen residues localize to the protein-DNA interaction surface" is based solely on the AlphaFold 3 model without experimental validation.
- The claim that "interference with three DBD residues (Arg105, Thr109, and Lys142) by alternative splicing-derived peptides attenuates ZmHsf17's DNA-binding capacity" is referenced from prior work but not directly demonstrated in this study.
- The ChIP-seq data referenced in Section 2.4 are not shown or described in sufficient detail to evaluate the claim that ZmHsf17 "exclusively bound HSE2."
- The phylogenetic tree topology and bootstrap support values are not presented, making the evolutionary claims unverifiable from the provided text.