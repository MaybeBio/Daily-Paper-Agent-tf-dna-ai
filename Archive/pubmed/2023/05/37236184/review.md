## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure legends as provided.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors use AlphaFold2-predicted structures and DALI structural homology searches to identify novel BEN DNA-binding domains across diverse species, including C. elegans, Drosophila, zebrafish, and plants. They report that the previously uncharacterized DUF4806 motif is a BEN domain subtype, that BEN domains share structural similarity with homeodomains, and that this approach can be generalized to annotate other protein domains such as DUF3504.
- **Visible evidence base** Main text figures 1–7 (described in text), supplementary figures S1–S4 (described in text), supplementary data S1–S3 (referenced), methods section, and references cited within the text.
- **Missing materials affecting confidence** Actual figure images, supplementary data files (Data S1A–D, S2A–B, S3A–C), detailed DALI search parameters and full hit lists, pLDDT score distributions for all novel domains, and complete multiple sequence alignment data. These are referenced but not provided in the manuscript text.

## Reviewer
- **Overall assessment** This manuscript presents a timely and potentially valuable application of AlphaFold2 structural predictions to expand the known repertoire of BEN DNA-binding domains. The finding that C. elegans, previously thought to lack BEN factors, encodes multiple such proteins including the well-studied LIN-14 and SEL-7, is significant and will be of broad interest to developmental biologists. The structural similarity between BEN domains and homeodomains is an intriguing observation with evolutionary implications. However, several technical concerns must be addressed, particularly regarding the stringency of structural hit validation, the functional evidence for DNA binding, and the phylogenetic interpretation. The manuscript would be strengthened by clearer presentation of the structural alignments and more rigorous statistical support for the evolutionary claims.
- **Who would be interested in the results, and why** Developmental biologists studying temporal patterning and cell fate decisions, particularly those working on C. elegans lin-14/lin-4 biology. Researchers interested in transcription factor evolution and the origins of DNA-binding domains. Computational biologists developing methods for structure-based protein annotation. The broader genomics community interested in functional annotation of uncharacterized protein domains.
- **Major strengths** The application of AlphaFold2 structural predictions to discover remote homologs is innovative and timely. The identification of BEN domains in C. elegans, including in the well-characterized LIN-14 protein, provides immediate functional context and validates the approach. The structural comparison between BEN and homeodomains is conceptually interesting and opens new evolutionary questions. The authors demonstrate the generalizability of their approach by applying it to DUF3504. The manuscript is generally well-written and accessible to a broad audience.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (hit validation stringency), R1-M2 (functional evidence for DNA binding), R1-M3 (phylogenetic interpretation), R1-M4 (generalizability claim for DUF3504).
- **Assessment against Nature-style criteria** **Originality**: High. The use of AlphaFold2 for domain discovery is novel and the findings substantially expand the BEN domain family. **Scientific importance**: High. The identification of BEN domains in C. elegans, particularly in LIN-14, provides new avenues for understanding conserved mechanisms of temporal regulation. The BEN-homeodomain connection has evolutionary significance. **Interdisciplinary readership**: Moderate to high. Will appeal to developmental biologists, evolutionary biologists, and computational biologists. **Technical soundness**: Moderate. The core structural comparison approach is sound, but several validation steps and statistical analyses need strengthening. **Readability for nonspecialists**: Good. The manuscript is clearly written with appropriate context for each finding, though some structural biology details may be challenging for non-specialists.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially important, but the current evidence does not fully establish all claims, particularly regarding the functional significance of the novel BEN domains and the evolutionary relationships proposed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of hit validation
- **Claim pointer** The authors claim that DALI structural searches with Z-score ≥ 3 and manual inspection identify bona fide BEN domains, including 12 novel C. elegans proteins.
- **Evidence pointer** Results section "C. elegans harbors numerous unannotated BEN domain factors", Figure 2A, Data S1C
- **Concern** The threshold for identifying BEN domains relies on DALI Z-scores and manual inspection, but the criteria for manual inspection are not fully described. The authors state they checked for "five α helices and a middle loop connecting helix 3 and 4," but it is unclear how objectively this was applied. For example, the authors exclude CELE_Y61A9LA.4 from the top 13 hits but include it in the final list of 12 BEN-like proteins, yet the basis for this inclusion is not clear. Additionally, the DALI Z-score threshold of 3.0 is relatively permissive, and the authors do not report false discovery rates or provide a statistical framework for distinguishing true homologs from chance structural similarities. The authors should provide a more rigorous and reproducible validation pipeline, including explicit structural criteria, alignment quality metrics, and ideally a comparison against a negative control set of non-BEN proteins.
- **Why it matters** The central claim of the manuscript is that structural searches reveal novel BEN domains. If the hit validation is not rigorous, the entire set of novel domains, including the C. elegans findings, may be called into question. The reproducibility of the method is also essential for others to apply it.
- **Resolution test** Provide a detailed, step-by-step description of the manual inspection criteria, including specific structural features (e.g., helix lengths, loop length ranges, RMSD values for core helix superposition). Include a validation set of known non-BEN proteins with similar folds (e.g., other HTH proteins) to demonstrate that the method does not produce false positives. Report the distribution of DALI Z-scores for all hits and justify the chosen threshold with statistical analysis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional evidence for DNA binding
- **Claim pointer** The authors state that the novel C. elegans BEN domains "recognize specific DNA sequences" and that LIN-14 333–456 comprises a "novel sequence-specific DNA binding BEN domain."
- **Evidence pointer** Results section "The novel C. elegans BEN domain proteins recognize specific DNA sequences", Figure 2J, Figure 2I
- **Concern** The functional claim is based solely on re-analysis of existing LIN-14 ChIP-seq data. The authors identify GADRAAG and GAGACGS motifs from this data, but they do not provide direct biochemical evidence that the LIN-14 BEN domain binds these sequences. The ChIP-seq data reflects the binding of the full-length LIN-14 protein, which may involve other domains or protein partners. Furthermore, the authors do not test whether the other novel C. elegans BEN domains bind DNA at all, nor do they demonstrate sequence-specific binding for any of the novel domains. The electrostatic surface analysis is suggestive but not sufficient to establish DNA binding. Direct evidence, such as electrophoretic mobility shift assays (EMSAs) or binding assays with purified domains, is needed.
- **Why it matters** The claim that these are DNA-binding domains is central to the functional interpretation of the findings. Without direct evidence, the domains could have other functions, such as protein-protein interactions, which would change the significance of the results.
- **Resolution test** Perform in vitro DNA binding assays (e.g., EMSA or fluorescence polarization) with purified LIN-14 BEN domain and the identified motifs, including mutant controls. For at least a subset of the other novel C. elegans BEN domains, test for DNA binding activity using a generic DNA substrate. If DNA binding is not detected, revise the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Phylogenetic interpretation
- **Claim pointer** The authors propose that BEN domains and homeodomains are evolutionarily related, and that plant BEN-like regions independently derived from homeodomains.
- **Evidence pointer** Results section "Structure comparison reveals similarities between the BEN domain and homeodomain", "Identification of BEN-like structures in plants", "The relationship between BEN domains, homeodomains and plant BEN-like regions", Figure 5
- **Concern** The evolutionary claims are based on structural similarity and limited sequence conservation. While the structural resemblance is noted, the authors do not provide a rigorous phylogenetic analysis. The statement that BEN domains "likely derived from homeodomain-containing transcriptional regulators at an early evolutionary stage" is speculative. The structural similarity could arise from convergent evolution or from a common ancestor that predates the divergence of these domains. The authors also claim that plant BEN-like regions "independently derived from a homeodomain," but the evidence for this is not presented in a phylogenetic framework. A formal phylogenetic analysis using structural alignments or profile-based methods is needed to support these claims.
- **Why it matters** The evolutionary narrative is a major part of the discussion and the title. If the evolutionary relationship is not well-supported, the significance of the findings is diminished.
- **Resolution test** Perform a formal phylogenetic analysis using structural alignments of BEN domains, homeodomains, and plant BEN-like regions. Include a diverse set of sequences and use appropriate outgroups. Report support values for key nodes. Alternatively, use structure-based phylogenetic methods. If the analysis does not support a close evolutionary relationship, temper the claims accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the approach
- **Claim pointer** The authors state that their approach can be applied to other protein domains, using DUF3504 as an example, and that they identified novel human members of DUF3504.
- **Evidence pointer** Results section "3D comparisons identify novel DUF3504-containing proteins", Figure 6D
- **Concern** The DUF3504 analysis is presented as a proof-of-principle, but the functional significance of the novel DUF3504-containing proteins is not explored. The authors identify TOP1 and TOP1MT as having DUF3504-like structures, but they do not discuss what this means for the function of these proteins. The claim that DUF3504 is a "potential transcriptional regulator domain" is not supported by any functional data. The analysis is descriptive and does not add substantial insight beyond the identification of structural similarity.
- **Why it matters** The generalizability claim is important for the broader impact of the method. However, if the DUF3504 example does not provide functional insight, it weakens the case that this approach is broadly useful for functional annotation.
- **Resolution test** Provide additional functional context for the DUF3504 findings. For example, discuss the known functions of TOP1 and TOP1MT and how the DUF3504-like region might contribute. Alternatively, present the DUF3504 analysis as a purely structural observation and avoid over-interpreting its functional significance.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1A–D
- **Issue** The description of the BEN domain structural types in Figure 1A–D is brief. The differences between type I and type II BEN domains are described in the text, but the figure itself is not referenced in sufficient detail to guide the reader.
- **Required correction** Expand the figure legend to clearly label the key structural features of type I and type II BEN domains, including the helix numbering and the middle loop. Consider adding a schematic diagram to complement the structural representations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Motif discovery
- **Evidence pointer** Figure 2J
- **Issue** The motif discovery analysis reports E-values for the identified motifs, but the number of motifs tested and the multiple testing correction are not described. The authors report 31 significant motifs from 11,329 peaks, but it is unclear how many were tested.
- **Required correction** Provide details on the motif discovery parameters, including the number of motifs requested, the background model used, and how statistical significance was assessed. Report the E-value threshold used and consider multiple testing corrections.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** DALI searches
- **Evidence pointer** Methods section "Proteome-wide homologous structure searching and structural analysis"
- **Issue** The description of the DALI searches is incomplete. The authors do not specify which DALI database was searched (e.g., the AlphaFold DB subset), how the queries were prepared, or whether the searches were performed against full proteomes or pre-filtered sets.
- **Required correction** Provide a complete description of the DALI search protocol, including the database version, query structures used, and any filtering steps. This is essential for reproducibility.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary data
- **Evidence pointer** Data S1–S3
- **Issue** The supplementary data files are referenced but not described in detail. It is unclear what information they contain and how they support the main findings.
- **Required correction** Provide a brief description of each supplementary data file in the main text or in a supplementary file legend. Ensure that the data are accessible and clearly formatted.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation of structural similarity
- **Affected element** Figure 5
- **Evidence pointer** Figure 5A–E
- **Issue** The structural superposition of BEN domains and homeodomains is shown, but the RMSD values and the number of aligned residues are not reported. This makes it difficult to assess the quality of the structural alignment.
- **Required correction** Report RMSD values and the number of aligned residues for the superpositions shown in Figure 5. This will allow readers to evaluate the significance of the structural similarity.

## Risk / unsupported claims
- The claim that LIN-14 333–456 is a "novel sequence-specific DNA binding BEN domain" is not fully supported by direct biochemical evidence; the ChIP-seq analysis is suggestive but not conclusive.
- The claim that plant BEN-like regions "independently derived from a homeodomain" is not supported by a formal phylogenetic analysis.
- The claim that DUF3504 is a "potential transcriptional regulator domain" is speculative and not supported by functional data.
- The claim that the novel C. elegans BEN proteins "recognize specific DNA sequences" is based on a single ChIP-seq dataset and has not been experimentally validated for most of the identified proteins.
- The evolutionary relationship between BEN domains and homeodomains is presented as likely, but the evidence is primarily structural and lacks a rigorous phylogenetic framework.