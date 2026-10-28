## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary figure legends as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors report that the C. elegans LEM-3/ANKLE1 nuclease cleaves a broad range of branched DNA substrates in vitro, that its catalytic mechanism is conserved with bacterial GIY-YIG nucleases, that the LEM-like domain is required for DNA binding and nuclease activity, and that preventing nuclear access of the nuclease is important to avoid toxicity. They propose LEM-3 acts as a "last chance catch-all" enzyme processing persistent DNA bridges before cytokinesis.
- **Visible evidence base** In vitro nuclease assays on synthetic DNA substrates (flaps, forks, nicked and intact Holliday junctions), electrophoretic mobility shift assays, AlphaFold structural predictions, CRISPR-generated C. elegans mutants, IR sensitivity assays, fluorescence microscopy of LEM-3 localization, western blot analysis, and RNAi-based MCM-7 depletion experiments.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S12) are referenced but not provided in full. Raw quantification data for binding curves, KD determination, and statistical analyses are not shown. Detailed plasmid construction and mutagenesis protocols are not fully described. Representative microscopy images and quantification methods for localization studies are not fully described.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive structure-function analysis of the LEM-3 nuclease, combining in vitro biochemistry with in vivo genetics in C. elegans. The work addresses an important question in genome stability: how persistent DNA bridges are processed at the final stages of cell division. The authors provide evidence for broad substrate specificity, a conserved catalytic mechanism, and a dual role for the LEM-like domain in DNA binding and localization. The finding that a GIY-YIG-only derivative is toxic when nuclear is intriguing and potentially important. However, several claims are not fully supported by the data as presented, particularly regarding dimer formation, the mechanistic basis of LEM-like domain function, and the interpretation of the toxicity phenotype. The manuscript would benefit from additional quantitative analyses and clearer presentation of key experiments.

- **Who would be interested in the results, and why** Researchers studying DNA repair, homologous recombination, genome stability, and cytokinesis would find this work relevant. The study also speaks to the broader community interested in structure-function relationships of nucleases and the evolutionary conservation of DNA processing enzymes. The C. elegans community and those studying ANKLE1 in human disease contexts (cancer, anemia) would also be interested.

- **Major strengths**
  1. The combination of in vitro biochemistry with in vivo genetics provides complementary evidence for LEM-3 function.
  2. The systematic dissection of LEM-3 domains (LEM-like, GIY-YIG, ankyrin) is well conceived.
  3. The use of "atomic" mutants (Y to F) to probe catalytic function is elegant.
  4. The observation that nuclear mislocalization of the GIY-YIG-only derivative causes toxicity is novel and potentially significant.
  5. The AlphaFold-based structural analysis provides testable hypotheses about the catalytic mechanism.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for dimer formation
- **Claim pointer** "We present evidence that LEM-3 may form a homodimeric complex on the Holliday junction DNA."
- **Evidence pointer** Results section "Cleavage of HJ substrates and evidence for LEM-3 acting as a dimer"; Figure 3B; Supplementary Fig. S9
- **Concern** The claim of homodimer formation is based on indirect evidence: the observation of two shifted species in EMSA and the conversion of plasmid to linear DNA. The authors themselves acknowledge that "our results do not formally prove LEM-3 dimer formation." However, the claim is presented prominently in the abstract and results. The EMSA data showing two shifted species could be explained by other models, such as sequential binding of monomers to different sites on the HJ, or conformational changes. The plasmid cleavage assay showing linear products is consistent with dual incision but does not demonstrate that both incisions occur within a single dimer complex. No direct biophysical evidence (e.g., analytical ultracentrifugation, size exclusion chromatography coupled with multi-angle light scattering, or cross-linking) is provided.
- **Why it matters** The proposed dimerization mechanism is central to the model of how LEM-3 processes HJs. If the dimer model is incorrect, the mechanistic interpretation of the cleavage pattern changes substantially. This claim goes beyond what the data can support and may mislead readers.
- **Resolution test** Provide direct evidence for dimer formation, such as: (1) size exclusion chromatography or native mass spectrometry showing a dimeric LEM-3 species in solution; (2) chemical cross-linking followed by SDS-PAGE showing a dimer band; (3) a dominant-negative experiment where a catalytically dead mutant mixed with wild-type reduces cleavage in a manner consistent with dimer interference; or (4) single-molecule FRET or similar approaches showing two LEM-3 molecules bound to a single HJ. Alternatively, soften the claim to state that the data are "consistent with, but do not prove, dimer formation."

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic basis of LEM-like domain function
- **Claim pointer** "The LEM-3 LEM-like and GIY-YIG nuclease domains are essential for LEM-3 recruitment to the midbody and its nuclease activity, while its LEM-like domain is sufficient for DNA binding."
- **Evidence pointer** Results sections "Role of LEM-domain for catalytic activity" and "Role of LEM-domain in DNA binding"; Figures 4 and 5
- **Concern** The manuscript shows that the LEM-like domain is required for DNA binding and nuclease activity, and that it contributes to midbody localization. However, the mechanistic distinction between the LEM-like domain's role in DNA binding versus its role in protein localization is not clearly resolved. The authors show that LEM-3(241-484) binds HJ DNA, but they do not demonstrate that this DNA binding is what mediates midbody localization. The midbody localization could be mediated by protein-protein interactions with midbody components, with the DNA binding being a separate function. The K441A-R456A mutant shows reduced DNA binding and reduced midbody localization, but the authors do not test whether this mutant still interacts with potential protein partners at the midbody. The claim that the LEM-like domain is "sufficient for DNA binding" is based on a single EMSA experiment with a truncated protein, and the affinity and specificity of this binding are not quantified.
- **Why it matters** Understanding whether the LEM-like domain mediates localization through DNA binding or protein-protein interactions is important for the model of how LEM-3 is recruited to the midbody. This distinction has implications for how LEM-3 recognizes its substrates in vivo and how its activity is regulated.
- **Resolution test** Perform additional experiments to separate DNA binding from protein-protein interaction functions: (1) test whether the K441A-R456A mutant can still interact with known midbody proteins (e.g., via co-immunoprecipitation); (2) generate a mutant that specifically disrupts DNA binding but not protein interactions, or vice versa; (3) quantify the DNA binding affinity of the LEM-like domain and test whether mutations that reduce affinity correlate with reduced midbody localization in a dose-dependent manner; (4) perform localization studies with a LEM-like domain that is fused to a heterologous DNA binding domain to test whether DNA binding alone can drive midbody localization.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of toxicity phenotype
- **Claim pointer** "Preventing LEM-3 nuclear access is important to avoid toxicity, likely caused by branched DNAs cleavage during normal DNA metabolism."
- **Evidence pointer** Results section "In vivo toxicity of GFP::lem-3(485-704)"; Figure 4C,D; Supplementary Fig. S10
- **Concern** The interpretation that the toxicity of GFP::LEM-3(485-704) is due to nuclear access and cleavage of genomic DNA is plausible but not directly tested. The authors show that this derivative is not excluded from the nucleus and is toxic, and that the catalytically dead version (Y530F) is not toxic. However, they do not directly demonstrate that the toxicity is due to DNA cleavage in the nucleus. Alternative explanations include: (1) the truncated protein may misfold and cause aggregation or proteotoxic stress; (2) the protein may sequester important nuclear factors; (3) the toxicity may be due to aberrant protein-protein interactions rather than nuclease activity. The authors also note that the GIY-YIG-only derivative has residual activity in vitro, so the toxicity could be due to this residual activity acting on nuclear substrates. The claim that this is "likely caused by branched DNAs cleavage" is presented as a conclusion rather than a hypothesis.
- **Why it matters** The toxicity phenotype is used to support the model that LEM-3 must be excluded from the nucleus to prevent inappropriate cleavage of DNA. If the toxicity is due to other mechanisms, the model of LEM-3 regulation would need to be revised. This is also relevant to understanding how ANKLE1 is regulated in human cells.
- **Resolution test** Perform additional experiments to test the mechanism of toxicity: (1) examine whether the toxic phenotype is associated with DNA damage markers (e.g., γH2AX, RAD-51 foci) in the nucleus; (2) test whether the toxicity is suppressed by mutations that disrupt DNA binding (e.g., K441A-R456A) in the context of the GIY-YIG-only derivative; (3) perform RNA-seq or proteomics to look for broader cellular responses; (4) test whether the toxicity is dependent on the cell cycle stage or specific DNA structures.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative analysis of substrate specificity
- **Claim pointer** "LEM-3 can cleave a wide range of branched DNA substrates, including flaps, forks, nicked, and intact Holliday junctions."
- **Evidence pointer** Results section "Specificity of LEM-3"; Figure 3A; Supplementary Fig. S8
- **Concern** The substrate specificity is presented qualitatively. The authors show that LEM-3 cleaves various substrates, but the relative efficiencies are not quantified. The time course experiments (Supplementary Fig. S8D) suggest differences in cleavage efficiency among substrates, but these are not analyzed statistically or presented with kinetic parameters. The statement that LEM-3 displays "the highest activity against 5'-flaps, 3'-flaps, and replication fork" is based on visual inspection of gels. Without quantification, it is difficult to assess the significance of these differences or to compare with other nucleases.
- **Why it matters** The substrate specificity of LEM-3 is central to understanding its biological function. If LEM-3 is a "catch-all" enzyme, it should cleave diverse substrates with reasonable efficiency. Quantitative data would allow comparison with other HJ resolvases and structure-specific nucleases, and would strengthen the model.
- **Resolution test** Provide quantitative analysis of cleavage efficiencies for each substrate, including: (1) time courses with multiple time points; (2) determination of initial rates or kcat/KM values where feasible; (3) statistical analysis comparing cleavage of different substrates; (4) dose-response curves with varying enzyme concentrations. Present these data graphically with appropriate error bars and statistical tests.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** In vivo relevance of in vitro findings
- **Claim pointer** "Our data suggest that LEM-3 acts as a 'last chance catch-all' enzyme that processes DNA bridges caused by various perturbations of DNA metabolism just before cells divide."
- **Evidence pointer** Discussion section; Figures 1, 2, 4, 5, 6
- **Concern** The in vitro data demonstrate that LEM-3 can cleave various branched DNA substrates, and the in vivo data show that catalytic activity is required for IR resistance and DNA bridge processing. However, the direct link between the specific in vitro substrate preferences and the in vivo function is not established. For example, the authors do not show that the DNA bridges that accumulate in lem-3 mutants are specifically the types of substrates that LEM-3 cleaves most efficiently in vitro. The "catch-all" model is reasonable but remains speculative.
- **Why it matters** The "catch-all" model has implications for how LEM-3 functions in genome stability and how it might be targeted therapeutically. If the model is incorrect, the function of LEM-3 might be more specific than proposed.
- **Resolution test** Provide evidence linking in vitro substrate specificity to in vivo function: (1) identify the types of DNA bridges that accumulate in lem-3 mutants (e.g., by staining for specific DNA structures); (2) test whether LEM-3 mutants with altered substrate specificity in vitro show corresponding changes in the types of bridges processed in vivo; (3) examine whether the in vitro substrate preferences correlate with the types of DNA damage that cause synthetic lethality with lem-3 mutations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1A
- **Evidence pointer** Figure 1A; Results section "Purification of LEM-3(241–704) and genetic characterization"
- **Issue** The domain structure schematic in Figure 1A is described in the text but the figure itself is not provided. The description of the Y530F mutation as a "catalytic site mutation" is introduced before the structural analysis that identifies Y530 as catalytic is presented.
- **Required correction** Ensure the figure clearly labels all domains (ankyrin, LEM-like, GIY-YIG) with amino acid boundaries. Consider reordering the text so that the structural analysis identifying catalytic residues precedes the description of the Y530F mutant.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** IR sensitivity assays
- **Evidence pointer** Figure 1C, 4C,D, 5G,H; Results sections
- **Issue** The IR sensitivity assays are described as showing differences between strains, but the statistical methods and number of biological replicates are not stated in the text provided. The methods section mentions a one-way ANOVA with Tukey's test, but it is not clear which experiments were analyzed this way.
- **Required correction** Clearly state the number of biological replicates for each experiment, the statistical test used, and the p-values for each comparison. Consider adding a statistical analysis subsection to the methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Protein purification details
- **Affected element** Recombinant protein production
- **Evidence pointer** Methods section "Protein expression and purification"; Supplementary Fig. S1
- **Issue** The methods describe two different purification protocols (one for LEM-3(241-704) and related proteins, one for LEM-3(241-484)), but the details of the second protocol are incomplete. The text states "The purification was performed as indicated above with the following modifications" but does not specify the modifications beyond the addition of PMSF.
- **Required correction** Provide complete details of the purification protocol for LEM-3(241-484), including the lysis buffer composition, the type of affinity resin used, the wash and elution conditions, and any additional chromatography steps.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** AlphaFold model validation
- **Affected element** Structural predictions
- **Evidence pointer** Figure 2A-C; Methods section "AlphaFold model prediction and structure analysis"
- **Issue** The AlphaFold models are used to make mechanistic claims about catalysis and DNA binding, but the confidence of the predictions is not discussed in the text. The pLDDT scores or predicted aligned error are not mentioned.
- **Required correction** Report the confidence metrics for the AlphaFold predictions, particularly for the regions involved in catalysis and DNA binding. If the confidence is low in these regions, this should be acknowledged and the claims tempered accordingly.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Domain nomenclature
- **Evidence pointer** Throughout the manuscript
- **Issue** The manuscript uses "LEM domain" and "LEM-like domain" somewhat interchangeably. The authors state that the LEM-3 domain is structurally similar to LEM domains but has distinct features, and they propose calling it "LEM-like." However, the text sometimes refers to it simply as "LEM domain."
- **Required correction** Use "LEM-like domain" consistently throughout the manuscript once the term is introduced, to avoid confusion.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion does not explicitly address the limitations of the study, such as the lack of direct evidence for dimer formation, the indirect nature of the toxicity mechanism, and the potential differences between in vitro and in vivo conditions.
- **Required correction** Add a paragraph discussing the limitations of the current study and what additional experiments would be needed to address them.

## Risk / unsupported claims
1. The claim that LEM-3 "may form a homodimeric complex on the Holliday junction DNA" is not directly supported by the data presented. The evidence is indirect and the authors themselves acknowledge this limitation.
2. The claim that the toxicity of GFP::LEM-3(485-704) is "likely caused by branched DNAs cleavage during normal DNA metabolism" is presented as a conclusion but is not directly tested. The mechanism of toxicity remains speculative.
3. The statement that the LEM-like domain is "sufficient for DNA binding" is based on a single EMSA experiment with a truncated protein. The affinity, specificity, and stoichiometry of this binding are not characterized.
4. The claim that the catalytic mechanism of LEM-3 is conserved with bacterial GIY-YIG nucleases is based on AlphaFold structural predictions and sequence alignments, but no direct biochemical evidence (e.g., metal ion dependence, specific base catalysis) is provided.
5. The statement that "preventing LEM-3 nuclear access is important to avoid toxicity" implies a regulatory mechanism, but the authors do not identify how LEM-3 is normally excluded from the nucleus or how this exclusion is regulated.
6. The "last chance catch-all" model is presented as a conclusion but is not directly tested. The authors do not demonstrate that LEM-3 processes all types of DNA bridges that arise from the various perturbations they list.