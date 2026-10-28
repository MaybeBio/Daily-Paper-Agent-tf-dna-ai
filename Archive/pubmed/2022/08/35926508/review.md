## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure legends
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors propose that FoxP3, a transcription factor essential for regulatory T cell function, can adopt two distinct dimerization states: a head-to-head dimer mediated by the Runx1-binding region (RBR) that represents the functional form, and a domain-swap dimer that is associated with impaired function. They support this with structural, biochemical, and cellular assays, including a disease-associated mutation (R337Q) that induces the swap conformation.
- **Visible evidence base** SEC-MALS, EMSA, crystallography (3.1–4.0 Å), pulldown assays, co-IP, thermal shift assays, restriction enzyme protection assays, ChIP-seq reanalysis, mouse models, and T cell functional assays
- **Missing materials affecting confidence** Electron density maps and refinement statistics (Table S1 referenced but not provided), full uncropped gel images, ChIP-seq peak lists, statistical details for mouse experiments, and supplementary figures S1–S7 referenced but not available for inspection

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially important revision of the current understanding of FoxP3 structure and function. The central claim that FoxP3 can adopt two distinct dimerization states with different functional consequences is well-supported by a multi-pronged experimental approach. The identification of the head-to-head dimer as the functional form, and the demonstration that a disease-associated mutation promotes the non-functional swap conformation, has significant implications for understanding IPEX syndrome and FoxP3 biology. However, several technical concerns, particularly regarding the resolution of the crystal structures and the interpretation of the ChIP-seq data, need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Immunologists studying regulatory T cell biology and immune tolerance; structural biologists interested in transcription factor dimerization and DNA recognition; clinical researchers investigating IPEX syndrome and other autoimmune disorders; and scientists studying the evolution of forkhead domain function.
- **Major strengths** The study combines structural biology, biochemistry, and cellular assays to address a fundamental question about FoxP3 function. The discovery that the RBR linker is critical for proper folding of the forkhead domain is novel and provides a mechanistic explanation for previous discrepancies in the literature. The use of a disease-associated mutation to validate the physiological relevance of the two conformations is elegant and clinically relevant. The demonstration that multiple IPEX mutations near the H2/H4 junction cause folding defects suggests a common pathogenic mechanism.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The crystal structures of FoxP3ΔN' and FoxP3ΔN" in complex with IR-FKHM4g DNA reveal a head-to-head dimer with the forkhead domain in a non-swap conformation.
  - **Evidence pointer** Results section "Overall architecture of FoxP3", Figure 1E, Table S1
  - **Concern** The crystal structures were solved at 3.1 Å and 4.0 Å resolution. At these resolutions, particularly 4.0 Å, the electron density maps may not be of sufficient quality to unambiguously assign side chain conformations and accurately model the protein-DNA interface. The authors state that the RBR loop was not well-defined in the electron density, which raises questions about the reliability of the proposed H-H dimer interface. Additionally, the structures contain deletions (residues 277–304 and 277–314) and mutations (C217S, C231S) that could potentially alter the protein's conformation.
  - **Why it matters** The structural model is the foundation for the central claim of the paper. If the H-H dimer interface is not accurately modeled, the subsequent functional interpretations, including the effects of interface mutations and the proposed mechanism of Runx1 recruitment, may be incorrect.
  - **Resolution test** Provide clear electron density maps (2Fo-Fc and Fo-Fc) for the H-H dimer interface and the RBR loop region. Report map-to-model correlation statistics (e.g., real-space R-factor) for the interface residues. If possible, validate the interface with an independent method such as crosslinking mass spectrometry or mutagenesis combined with analytical ultracentrifugation.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The R337Q mutation induces domain-swap dimerization, and this conformational change is the primary cause of functional impairment.
  - **Evidence pointer** Results section "IPEX mutation R337Q induces swap dimerization and impairs FoxP3 functions", Figure 7G–M
  - **Concern** The evidence that R337Q induces swap dimerization relies on SEC-MALS showing a dimer and the observation that A372S (a swap-suppressive mutation) reverts it to a monomer. However, the authors do not provide direct structural evidence (e.g., a crystal structure of R337Q) that the dimer is indeed a swap dimer. The functional rescue by A372S is partial, and the authors acknowledge that R337 also directly contacts DNA. It is therefore difficult to disentangle the effects of the conformational change from the direct loss of a DNA contact.
  - **Why it matters** The paper's conclusion that swap dimerization is the pathogenic mechanism for R337Q depends on this distinction. If the primary effect of R337Q is simply loss of a direct DNA contact, the role of swap dimerization in disease would be less clear.
  - **Resolution test** Provide direct structural or biophysical evidence that R337Q forms a swap dimer, such as a crystal structure or small-angle X-ray scattering (SAXS) analysis. Alternatively, generate a mutation that specifically disrupts the swap dimer interface without affecting the DNA contact and test whether it rescues R337Q function.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors state that "head-to-head dimerization was unique to FoxP3" among FoxP family members, and that this imparts distinct functions to FoxP3.
  - **Evidence pointer** Results section "Head-to-head (H-H) dimerization of forkhead is unique to FoxP3", Figure 3E–F
  - **Concern** The conclusion that H-H dimerization is unique to FoxP3 is based on EMSA showing that FoxP1/2/4 bind IR-FKHM4g and sFKHM equally. However, this is an indirect assay. The authors do not test whether FoxP1/2/4 can form H-H dimers under any conditions, nor do they examine whether the RBR sequences of FoxP1/2/4 could support H-H dimerization if appropriately positioned. The sequence alignment in Figure 3F shows differences, but the functional significance is not directly tested.
  - **Why it matters** The claim of uniqueness is important for understanding FoxP3's specialized function in Tregs. If other FoxP proteins can also form H-H dimers under certain conditions, the evolutionary and functional implications would be different.
  - **Resolution test** Perform a more direct test of H-H dimerization for FoxP1/2/4, such as a crosslinking assay in the presence of IR-FKHM4g DNA, or a chimeric construct where the FoxP3 RBR is replaced with the corresponding region from FoxP1/2/4 to test whether H-H dimerization is transferable.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors conclude that "H-H dimerization enables FoxP3 to recognize diverse DNA sequences" based on in vitro binding assays with a limited set of sequences.
  - **Evidence pointer** Results section "H-H dimerization enables FoxP3 to recognize diverse DNA sequences", Figure 5
  - **Concern** The ChIP-seq reanalysis is limited to 548 peaks containing an FKHM, and the authors do not find enrichment of IR-FKHM4g. They then test a small number of non-consensus sequences (seq1–4) and show that FoxP3 binds some of them when paired with FKHM. This is a very limited sampling of the potential sequence space. The conclusion that H-H dimerization "enables FoxP3 to recognize diverse DNA sequences" is an extrapolation from a small dataset.
  - **Why it matters** The physiological relevance of the in vitro DNA binding specificity is a key claim. If the diversity of sequences is not representative of genomic binding sites, the model may not accurately reflect FoxP3 function in cells.
  - **Resolution test** Perform a more comprehensive in vitro binding assay, such as SELEX or protein-binding microarray, to define the full range of sequences bound by the FoxP3 H-H dimer. Alternatively, use a more sophisticated bioinformatics approach on the ChIP-seq data to search for more complex patterns.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The abstract begins with "FoxP3 is an essential transcription factor (TF) for immunologic homeostasis" but does not explain what FoxP3 does or why it is important for a general audience.
  - **Required correction** Add a brief explanation of FoxP3's role in regulatory T cells and immune regulation in the first or second sentence.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Figure 2C
  - **Evidence pointer** Results section "FoxP3 forkhead exists in the non-swap monomeric conformation in the presence of RBR", Figure 2C
  - **Issue** The transcriptional activity assay in Figure 2C shows that A372P partially impairs FoxP3 function, but the authors do not discuss whether this is due to the mutation's effect on protein stability or folding, rather than specifically on swap dimerization.
  - **Required correction** Include a discussion of potential confounding factors, such as protein stability, and if possible, provide data on protein expression levels for the mutants.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Figure 6B
  - **Evidence pointer** Results section "H-H dimerization is important for Runx1 binding", Figure 6B
  - **Issue** The pulldown assay showing Runx1 binding to FoxP3 uses a truncated Runx1 construct (residues 371–451). It is not clear whether this fragment represents the full Runx1 interaction domain or if other regions of Runx1 contribute to the interaction.
  - **Required correction** Clarify the rationale for using this Runx1 fragment and discuss whether the full-length Runx1 might behave differently.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interdisciplinary readership
  - **Affected element** Discussion
  - **Evidence pointer** Discussion, first paragraph
  - **Issue** The discussion of "fuzzy" interactions and the potential implications for drug development is interesting but could be expanded for readers not familiar with this concept.
  - **Required correction** Briefly explain what "fuzzy" interactions are and why they might be relevant for therapeutic targeting.
- **Technical failings that need to be addressed before the case is established** R1-M1 (crystal structure quality) and R1-M2 (direct evidence for swap dimerization of R337Q) are the primary technical concerns that need to be resolved. The lack of direct structural evidence for the R337Q swap dimer is particularly important, as this is the key link between the structural model and the disease mechanism.

## Risk / unsupported claims
- The claim that H-H dimerization is "unique to FoxP3" among FoxP family members is not fully supported by the data, as only indirect EMSA evidence is provided.
- The conclusion that H-H dimerization "enables FoxP3 to recognize diverse DNA sequences" is extrapolated from a limited set of in vitro binding assays and a small ChIP-seq analysis.
- The statement that "small molecules that either promote or destabilize the canonical monomeric forkhead structure or its H-H dimerization could be used to modulate Tregs" is speculative and not directly supported by any data in the manuscript.
- The claim that the R337Q mutation's functional impairment is "largely mediated by its induction of the domain-swap conformation" is not fully supported, as the direct DNA contact role of R337 is also impaired.
- The physiological relevance of the H-H dimer for FoxP3 function in vivo is inferred from in vitro and cell-based assays but not directly demonstrated in a relevant animal model.

## Assessment against Nature-style criteria
- **Originality** High. The study challenges the prevailing view of FoxP3 structure and provides a new model for understanding its function. The concept of two distinct dimerization states with opposing functional outcomes is novel.
- **Scientific importance** High. FoxP3 is a critical regulator of immune tolerance, and understanding its molecular function has direct implications for autoimmune disease and cancer immunotherapy. The identification of a potential common mechanism for IPEX mutations is clinically significant.
- **Interdisciplinary readership** Moderate to high. The study bridges structural biology, immunology, and clinical genetics. The findings should be of interest to a broad audience, though the technical details may be challenging for non-specialists.
- **Technical soundness** Moderate. The multi-pronged approach is commendable, but the crystal structure resolution and the lack of direct structural evidence for the R337Q swap dimer are significant weaknesses. The functional assays are generally well-designed but some conclusions are extrapolated beyond the data.
- **Readability for nonspecialists** Moderate. The manuscript is generally well-written, but the abstract and some sections assume familiarity with transcription factor biology and structural biology concepts. The figures are likely to be complex for non-experts.

## Recommendation posture
Supportive if technical concerns are resolved. The central hypothesis is interesting and potentially important, but the current evidence does not fully establish the case. Specifically, the authors need to provide stronger structural evidence for the H-H dimer interface and direct evidence that R337Q forms a swap dimer in the context of the full-length protein. If these concerns are addressed, this could be a significant contribution to the field.