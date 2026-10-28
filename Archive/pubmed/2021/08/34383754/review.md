## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and interpretation of results as presented in the provided text
- **Shared manuscript claim summary** The authors present DeepG4, a convolutional neural network that predicts cell-type specific active G-quadruplex (G4) regions from DNA sequence and chromatin accessibility data. The model achieves high accuracy (AUROC > 0.98) across multiple cell lines, identifies predictive DNA motifs including known transcription factor binding sites, and provides genome-wide predictions in tissues and cancers as a community resource.
- **Visible evidence base** Figures referenced (Fig 1, 2, 3, 4, 5), supplementary figures (S1, S2), GEO accession numbers, GitHub repository links, JASPAR database, ICGC data portal
- **Missing materials affecting confidence** Actual figures and supplementary materials not provided; quantitative performance metrics beyond AUROC/AUPR values mentioned in text are not fully detailed; hyperparameter optimization details partially described; code repository not inspected; detailed statistical test descriptions for enrichment analyses not provided

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful deep learning tool for predicting active G4 regions in a cell-type specific manner. The core idea of integrating chromatin accessibility with sequence information is sensible and addresses a gap in existing G4 prediction methods. However, several methodological details and validation aspects require clarification and strengthening before the claims are fully supported. The biological interpretations, particularly regarding transcription factor motifs, are intriguing but would benefit from more rigorous validation.
- **Who would be interested in the results, and why** Researchers studying G-quadruplex biology, DNA structure and function, gene regulation, and genome instability. Computational biologists developing deep learning approaches for genomic feature prediction. The resource of genome-wide predictions across tissues and cancers would be valuable for the broader chromatin biology community.
- **Major strengths** 1) Addresses an important gap by predicting active G4 regions (in vivo) rather than just potential G4-forming sequences. 2) Integration of chromatin accessibility is a novel and biologically motivated feature. 3) High predictive performance across multiple cell lines suggests generalizability. 4) Identification of specific motifs, including TF binding sites, provides mechanistic insights. 5) Resource generation for multiple tissues and cancers increases utility.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: Moderate. While deep learning for G4 prediction exists, the focus on active G4 regions with chromatin accessibility integration is a novel contribution. Scientific importance: Moderate to high. G4 biology is an active field, and cell-type specific prediction tools are needed. Interdisciplinary readership: Moderate. Will appeal to computational biologists and G4 researchers, but may have limited broader appeal. Technical soundness: Needs improvement. Several methodological details require clarification and additional validation. Readability for nonspecialists: Generally clear, though some technical sections could be more accessible.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "DeepG4 is very accurate to predict active G4 regions in different cell types" and "DeepG4 achieves excellent accuracy at predicting cell-type specific active G4 regions (AUROC > 0.98)"
- **Evidence pointer** Results section, Fig 3; location not provided
- **Concern** The evaluation of DeepG4 appears to rely primarily on AUROC and AUPR metrics. However, the manuscript does not clearly describe how negative examples were selected for training and testing. The authors state that negative sequences were "randomly drawn from the human genome with sizes, GC content, and repeat content similar to those of positive DNA sequences," but the genomic context of these negatives (e.g., whether they overlap with any G4-seq or G4 ChIP-seq signals, their chromatin state) is not specified. This is critical because the choice of negatives dramatically affects performance metrics. If negatives are drawn from regions with low chromatin accessibility, the model may trivially learn to use accessibility rather than sequence features.
- **Why it matters** Without a clear description of negative set construction, the reported AUROC values may be inflated and not reflective of real-world performance. The model's ability to generalize to novel genomic regions depends on the representativeness of the training negatives.
- **Resolution test** Provide a detailed description of negative set construction, including genomic distribution, overlap with any G4-related signals, and chromatin accessibility profiles. Additionally, perform evaluation using alternative negative sets (e.g., random genomic regions, regions with matched accessibility but no G4 signal) to demonstrate robustness.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Removing chromatin accessibility significantly lowered cell-type specific prediction accuracy" and the model's ability to predict cell-type specific active G4 regions
- **Evidence pointer** Results section, Fig 3F-3J; location not provided
- **Concern** The comparison between DeepG4 (with accessibility) and DeepG4* (without accessibility) is presented as evidence that chromatin accessibility is important. However, the manuscript does not describe how the accessibility feature is incorporated into the model architecture. Specifically, it is unclear whether accessibility is treated as a single scalar feature per region, a vector of per-base values, or something else. The description of the model architecture in the Methods and Results sections is incomplete, lacking details on how the two input types (sequence and accessibility) are combined in the network.
- **Why it matters** The architectural details are essential for reproducibility and for understanding the relative contribution of sequence versus accessibility features. Without this information, the claim that accessibility is important cannot be properly evaluated, and other researchers cannot implement or build upon the method.
- **Resolution test** Provide a complete architectural description, including layer dimensions, how the accessibility input is processed, and where the concatenation occurs. Include a model diagram with tensor shapes. Additionally, report feature importance analyses (e.g., ablation studies) that quantify the contribution of accessibility relative to sequence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "DeepG4 identifies key DNA motifs that are predictive of G4 region activity" and "among those motifs, we identified known transcription factors (TFs) which could play important roles in G4 activity"
- **Evidence pointer** Results section, Fig 4; location not provided
- **Concern** The motif discovery and TF matching procedures are not described in sufficient detail. The authors state that motifs were extracted from the first convolutional layer and clustered using RSAT, and that TomTom was used to match against JASPAR. However, key parameters are missing: how many motifs were tested, what significance thresholds were used for TomTom matches, how the "variable importance" was computed using random forests, and how the enrichment analyses around active G4 regions and canonical G4 motifs were performed (e.g., what background model was used). The claim that cluster 3 matches FOS with q-value = 2 × 10⁻¹⁰ is presented, but the statistical framework for this and other matches is not fully explained.
- **Why it matters** The biological interpretations regarding TF involvement in G4 activity are a significant part of the manuscript's contribution. If the motif discovery and matching procedures are not rigorously described and statistically controlled, these claims may be overstated or irreproducible.
- **Resolution test** Provide complete details of the motif extraction, clustering, and matching procedures, including all parameters and thresholds. Describe the enrichment analysis methodology, including background models and multiple testing corrections. Consider validating a subset of TF motif predictions experimentally or through independent datasets.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We used DeepG4 to predict active G4 regions in a large number of tissues and cancers, thereby providing a comprehensive resource for researchers"
- **Evidence pointer** Results section, Fig 5; location not provided
- **Concern** The genome-wide predictions in tissues and cancers are presented as a resource, but the manuscript does not provide any validation of these predictions. The authors show examples (e.g., FUS gene with variable G4 activity across cancers), but there is no systematic assessment of whether the predicted cell-type specific differences are biologically meaningful. For instance, are there any experimental data (e.g., from other studies) that corroborate the predicted differences? How do the predictions compare to known G4 ChIP-seq data in any of the tissues or cancers where such data exist?
- **Why it matters** The resource claim is a major part of the manuscript's value proposition. Without any validation, users of the resource cannot assess its reliability. The identification of "variable" G4 regions is particularly important, as these are claimed to be cell-type specific, but this claim requires external validation.
- **Resolution test** Provide validation analyses, such as comparing predictions to available G4 ChIP-seq data in at least one or two tissues/cancers where such data exist. Alternatively, use orthogonal approaches (e.g., correlation with gene expression or chromatin state annotations) to support the biological relevance of predicted variable regions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, G4 data section
- **Evidence pointer** "We downloaded G4 ChIP-seq data for HaCaT, K562 and HEKnp cell lines from Gene Expression Omnibus (GEO) accession numbers GSE76688, GSE99205 and GSE107690"
- **Issue** The text states that G4 ChIP-seq data were downloaded from three GEO accessions for three cell lines, but it is unclear which accession corresponds to which cell line. Additionally, the authors mention "G4P ChIP-seq" for other cell lines, but the difference between G4 ChIP-seq and G4P ChIP-seq is not explained.
- **Required correction** Clarify the correspondence between GEO accessions and cell lines. Define G4P ChIP-seq and explain any differences in data processing.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, DeepG4 implementation
- **Evidence pointer** "DeepG4 was implemented using Keras R library" and "DeepG4 is available at https://github.com/morphos30/DeepG4"
- **Issue** The manuscript mentions that all fasta files used for training and predictions were deposited, but does not specify where. The GitHub repository link is provided, but it is not clear if the deposited data are accessible through the same repository or through a separate data repository.
- **Required correction** Specify the data repository (e.g., Zenodo, Figshare) and provide accession numbers or DOIs for the deposited training and prediction data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, Genome-wide predictions section
- **Evidence pointer** "we observed that 29% of stable G4 regions located within promoters, whereas only 16% of variable G4 regions colocalized with promoters" and "variable G4 regions were enriched at strong enhancers as compared to stable G4 regions (p = 0.011)"
- **Issue** The statistical test used for the enrichment comparison (p = 0.011) is not described. It is unclear whether this is a permutation test, a binomial test, or another approach. Additionally, the comparison of promoter proportions (29% vs 16%) is presented without any statistical assessment.
- **Required correction** Describe the statistical tests used for enrichment analyses, including the null model and multiple testing corrections if applicable. Provide confidence intervals or effect sizes for the reported proportions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, Identification of important motifs section
- **Evidence pointer** "It was very interesting to observe that such motif corresponding to one half of a canonical G4 motif also matched a known TFBS motif, which supported the complex interplay between G4s and TFBS protein binding"
- **Issue** The interpretation that a motif matching both a G4 half and a TFBS supports interplay between G4s and TF binding is speculative. The overlap could be coincidental, and the manuscript does not provide functional evidence for this claim.
- **Required correction** Soften the interpretation or provide additional evidence, such as experimental validation or analysis of TF binding data in G4 regions.

## Risk / unsupported claims
- The claim that DeepG4 provides "a comprehensive resource for researchers" is not fully supported without validation of the genome-wide predictions in tissues and cancers.
- The biological interpretation that specific TF motifs "could play important roles in G4 activity" is speculative and not experimentally validated.
- The statement that "active G4 regions are determined by numerous specific motifs" rather than a flexible consensus sequence is an interpretation that requires more rigorous statistical support.
- The claim that chromatin accessibility is important for cell-type specific predictions is supported by the DeepG4 vs DeepG4* comparison, but the magnitude of the effect and its consistency across cell types are not fully quantified.
- The performance metrics reported (AUROC values) are not accompanied by confidence intervals or cross-validation details, limiting the assessment of their reliability.