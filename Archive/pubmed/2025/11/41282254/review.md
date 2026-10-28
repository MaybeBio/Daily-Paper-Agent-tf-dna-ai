## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) and supplementary file list. No figures, tables, or supplementary PDFs were provided for inspection.
- **Assessment boundary** Structural and biochemical claims regarding the EBNA1-TRF2-RAP1 complex on the ½DS origin, as presented in the text. Functional replication assays are assessed only as described in the text.
- **Shared manuscript claim summary** The authors propose that EBNA1 recruits TRF2-RAP1 to the EBV oriP ½DS element through a previously uncharacterized acidic patch on the EBNA1 DNA-binding domain, and that this interaction is essential for oriP-dependent replication.
- **Visible evidence base** Text descriptions of EMSA, cryo-EM (7.1 Å reconstruction), XL-MS (402 interprotein cross-links), AlphaFold3 modeling, site-directed mutagenesis, replication assays, and cycloheximide chase experiments. Supplementary file names are listed but contents were not accessible.
- **Missing materials affecting confidence** All figures, supplementary figures, cryo-EM data processing statistics, XL-MS spectra and validation, AlphaFold3 confidence metrics, and raw replication assay data. Without these, several key claims cannot be independently verified.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question: how EBNA1 coordinates host telomere-binding factors at the EBV origin of replication. The integration of multiple structural and biochemical approaches is commendable, and the identification of a specific acidic patch on EBNA1 that engages TRF2 is potentially significant. However, the central structural claim rests on a low-resolution (7.1 Å) cryo-EM map with heterogeneous density, and the functional data, while suggestive, do not fully establish that the acidic patch is the sole or primary determinant of TRF2 recruitment in cells. The manuscript is well-written and the logic is clear, but several technical concerns must be addressed before the conclusions are fully supported.
- **Who would be interested in the results, and why** Virologists studying EBV latency and episome maintenance; structural biologists interested in protein-DNA complexes and host-pathogen interactions; telomere biologists studying shelterin complex functions beyond telomeres; and researchers in the DNA replication field interested in origin licensing mechanisms.
- **Major strengths** 1) The study addresses a significant gap in understanding how EBNA1 coordinates host factors at oriP. 2) The multi-technique approach (cryo-EM, XL-MS, AlphaFold3, biochemistry) provides orthogonal evidence for the proposed interaction. 3) The identification of a specific acidic patch with functional consequences is a concrete, testable finding. 4) The discussion of evolutionary divergence among herpesviruses is thoughtful and adds broader context.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (cryo-EM resolution and model fitting), R1-M2 (XL-MS validation and specificity), R1-M3 (AlphaFold3 overinterpretation), R1-M4 (functional replication assay controls).
- **Assessment against Nature-style criteria**  
  *Originality*: The finding of a specific acidic patch on EBNA1 mediating TRF2 recruitment is novel and not previously reported. The integration of cryo-EM with XL-MS and AlphaFold3 for this system is also original.  
  *Scientific importance*: The work has the potential to mechanistically link EBV episome maintenance to telomere biology, which would be of broad interest. However, the importance is somewhat tempered by the low-resolution structural data and the incomplete functional validation.  
  *Interdisciplinary readership*: The topic bridges virology, structural biology, and telomere biology, and would appeal to a broad audience if the claims are fully substantiated.  
  *Technical soundness*: The experimental design is generally sound, but the cryo-EM resolution is insufficient to define specific side-chain interactions, and the XL-MS data require more rigorous validation. The AlphaFold3 predictions are used in a somewhat uncritical manner.  
  *Readability for nonspecialists*: The manuscript is clearly written and the logic is easy to follow. Technical terms are used appropriately, and the figures (as described) would likely aid comprehension. However, the abstract could better highlight the broader significance for nonspecialists.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the data are suggestive, but the current evidence does not fully establish the structural model or the functional necessity of the acidic patch.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Structural evidence  
- **Claim pointer** The authors claim that cryo-EM and AlphaFold3 modeling "converge on a model in which the TRF2 homodimerization domain (TRFH) flexibly interacts with EBNA1 on the surface opposite the DNA-binding region."  
- **Evidence pointer** Results section "TRF2, Rap1, and the EBNA1 DBD form a stable but highly flexible complex with ½ DS"; Figure 2 (not provided)  
- **Concern** The cryo-EM reconstruction is at 7.1 Å resolution, which is insufficient to define specific protein-protein contacts or to validate the placement of the TRFH domain. The authors acknowledge heterogeneity and that the density "did not map cleanly to published structures." The claim of convergence with AlphaFold3 is problematic because AlphaFold3 predictions are not experimental evidence and may be biased by the input stoichiometry. The authors state that AlphaFold3 models "assumed perfect C2 symmetry, which our cryo-EM data did not support," yet they still use these models to interpret the density. This circular reasoning weakens the structural conclusion.  
- **Why it matters** The central structural claim of the paper, that TRFH engages a specific acidic patch on EBNA1, depends on the reliability of the model placement. At 7.1 Å, the density cannot distinguish between alternative orientations or confirm specific side-chain interactions. Without higher-resolution data or independent validation (e.g., mutagenesis coupled with cross-linking), the structural model remains speculative.  
- **Resolution test** Provide a higher-resolution reconstruction (ideally better than 4 Å) or use focused classification to improve the TRFH density. Alternatively, validate the model with site-directed cross-linking (e.g., introducing cysteine pairs or photo-cross-linkers) that can be tested biochemically. Show that the AlphaFold3 predictions are robust to different input stoichiometries and that the chosen model is not arbitrarily selected.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Cross-linking mass spectrometry validation  
- **Claim pointer** The authors state that "XLMS reveals a concentrated EBNA1 acidic patch that contacts TRF2-Rap1" based on 402 interprotein cross-links, with 107 between EBNA1 and TRF2 and 49 between EBNA1 and Rap1.  
- **Evidence pointer** Results section "XLMS reveals a concentrated EBNA1 acidic patch that contacts TRF2-Rap1"; Figure 3 (not provided)  
- **Concern** The XL-MS data are presented as counts of cross-links but no details are given on the false discovery rate (FDR), the number of replicates, or the criteria for accepting cross-link identifications. Zero-length EDC cross-linking requires proximity (typically <10 Å), but the authors do not report whether the identified cross-links are consistent with the AlphaFold3 model or whether they can discriminate between the proposed model and alternative arrangements. The high number of cross-links (402) is surprising for a complex with this level of flexibility and may indicate non-specific cross-linking or over-identification.  
- **Why it matters** The XL-MS data are a key piece of evidence supporting the acidic patch interaction. If the cross-link identifications are not rigorously validated, the conclusion that the acidic patch is the primary contact site is not supported. Over-identified cross-links could lead to false conclusions about the interface.  
- **Resolution test** Provide detailed XL-MS statistics, including FDR thresholds, number of replicates, and a table of all identified cross-links with their scores. Show that the cross-links are consistent with the proposed model and that they are not observed in control samples (e.g., EBNA1 alone or TRF2-RAP1 alone). Ideally, validate key cross-links by targeted mutagenesis of the involved residues.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** AlphaFold3 usage  
- **Claim pointer** The authors use AlphaFold3 to model the EBNA1-TRF2-RAP1 complex and state that "AlphaFold3 models consistently placed TRFH in the dorsal region."  
- **Evidence pointer** Results section "TRF2, Rap1, and the EBNA1 DBD form a stable but highly flexible complex with ½ DS"; Figure 2d-e (not provided)  
- **Concern** AlphaFold3 is a powerful tool, but its predictions for multi-protein complexes, especially those involving flexible or disordered regions, can be unreliable. The authors do not report confidence metrics (e.g., pLDDT, PAE) or whether the predictions were validated against the experimental data. The statement that the models "assumed perfect C2 symmetry" is concerning because it suggests the input constraints may have biased the output. The authors should demonstrate that the AlphaFold3 predictions are robust to different input configurations and that the chosen model is the most plausible.  
- **Why it matters** The structural model is a central claim of the paper. If the AlphaFold3 predictions are not critically evaluated, the model may be over-interpreted, leading to incorrect conclusions about the interaction interface.  
- **Resolution test** Provide AlphaFold3 confidence metrics and show that the predictions are consistent across multiple runs with different input stoichiometries. Compare the AlphaFold3 model with the cryo-EM density to demonstrate that the model fits the data. If possible, validate the model with additional experimental data (e.g., hydrogen-deuterium exchange or limited proteolysis).

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Functional replication assay  
- **Claim pointer** The authors claim that the 8x acidic patch mutant "showed severe impairment of oriP replication relative to WT" and that this is due to loss of TRF2-RAP1 recruitment.  
- **Evidence pointer** Results section "The acidic patch on EBNA1 is required for TRF2 and Rap1 recruitment and for replication at oriP"; Figure 5 (not provided)  
- **Concern** The replication assay is performed in HEK293 cells, but the text does not specify whether the cells are latently infected with EBV or whether the assay measures replication of a plasmid containing oriP. The authors state that the 8x mutant shows reduced replication at 72 hours, but the magnitude of the effect and the statistical significance are not reported. Additionally, the authors do not show that the 8x mutant is properly localized to the nucleus or that it retains DNA-binding activity. The cycloheximide chase experiment shows comparable protein stability, but this does not rule out other defects (e.g., altered subcellular localization or impaired DNA binding).  
- **Why it matters** The functional data are essential to establish the biological relevance of the acidic patch. If the replication defect is not specifically due to loss of TRF2-RAP1 recruitment, the conclusion is weakened. The lack of controls for DNA-binding activity and nuclear localization leaves alternative explanations open.  
- **Resolution test** Provide a detailed description of the replication assay, including the cell line, the plasmid used, and the statistical analysis. Show that the 8x mutant retains DNA-binding activity (e.g., by EMSA or ChIP) and is properly localized to the nucleus. If possible, perform a rescue experiment by tethering TRF2 to the 8x mutant to see if replication is restored.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The abstract states that EBNA1 is "essential for the episomal maintenance and DNA replication of Epstein-Barr virus (EBV) in latently infected cells," but this is a well-established fact and could be stated more concisely to make room for the novel findings.  
- **Required correction** Consider shortening the background and emphasizing the new findings more prominently.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Results section "TRF2, Rap1, and the EBNA1 DBD form a stable but highly flexible complex with ½ DS"  
- **Evidence pointer** Figure 1c description  
- **Issue** The term "unstable supershift" is vague. It is unclear whether this refers to a smeared band, a low-intensity band, or a band that disappears over time.  
- **Required correction** Provide a more precise description of the EMSA results, including the appearance of the bands and the conditions under which the supershift is observed.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Results section "XLMS reveals a concentrated EBNA1 acidic patch that contacts TRF2-Rap1"  
- **Evidence pointer** Figure 3 (not provided)  
- **Issue** The text states that cross-links are "highly concentrated on four acidic EBNA1 residues," but it is unclear how many of the 107 EBNA1-TRF2 cross-links involve these residues.  
- **Required correction** Provide a quantitative breakdown of the cross-links, including the number of unique cross-linked residues and the frequency of each residue in the identified cross-links.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Experimental detail  
- **Affected element** Methods section "Cyclohexamide chase experiments"  
- **Evidence pointer** Methods, "Cyclohexamide chase experiments"  
- **Issue** The text mentions "cyclohexamide" but the correct spelling is "cycloheximide." Additionally, the time points for the chase are not specified.  
- **Required correction** Correct the spelling and specify the time points used in the chase experiment.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Discussion  
- **Affected element** Discussion, paragraph 3  
- **Evidence pointer** Discussion, "There are limitations and clear next steps"  
- **Issue** The discussion of future directions is somewhat generic and could be more specific. For example, the authors mention "engineered cross-links" but do not specify what type of cross-linking would be most informative.  
- **Required correction** Provide more concrete suggestions for future experiments, such as specific cross-linking strategies or alternative structural methods (e.g., cryo-ET on intact cells).

## Risk / unsupported claims
- The claim that the cryo-EM and AlphaFold3 models "converge" on a specific TRFH placement is not fully supported, given the low resolution of the cryo-EM map and the acknowledged flexibility of the complex.
- The claim that the acidic patch is "unique amongst the herpesvirus episome maintenance proteins" is based on a limited comparison (only KSHV LANA and HPV E2 are mentioned) and is not systematically demonstrated.
- The functional significance of the acidic patch for oriP replication is suggested by the 8x mutant data, but the text does not provide sufficient detail to rule out off-target effects or other defects in the mutant protein.
- The statement that the 8x mutant "abolishes" oriP-dependent replication is strong, but the data are not shown in the text, and the magnitude of the effect is not quantified.
- The claim that TRF2-RAP1 recruitment is "essential" for oriP replication is not fully established, as the authors do not show that TRF2-RAP1 binding is required for replication in the absence of the acidic patch mutation.