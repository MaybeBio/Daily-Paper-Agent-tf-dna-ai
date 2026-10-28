## Review setup
- **Input scope** Abstract and author summary only
- **Assessment boundary** Claims and methods as described in the supplied abstract and author summary
- **Shared manuscript claim summary** The authors state that they coupled transcriptome sequencing and deep learning to identify differentially expressed genes (DEGs) in soybean during compatible and incompatible interactions with *Phytophthora sojae*, selected two defense-related transcription factors (WRKY and RAV), obtained DAP-seq data for these TFs, trained deep neural networks with convolutional and recurrent layers to predict new TF binding sites in the DEG set, leveraged Arabidopsis DAP-seq data for five TF families to train cross-species models, and constructed a gene regulatory network of TF-target gene interactions orchestrating the immune response.
- **Visible evidence base** Abstract text and author summary only. No figures, tables, methods details, or supplementary materials were provided.
- **Missing materials affecting confidence** Full manuscript text, all figures and tables, methods section, DAP-seq data processing details, model architecture and training parameters, cross-species model validation procedures, network construction algorithm, and any statistical analyses. These omissions substantially limit the ability to evaluate technical soundness and reproducibility.

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting integration of transcriptomics, DAP-seq, and deep learning to infer gene regulatory networks in a crop pathosystem of agricultural importance. The conceptual framing is reasonable and the potential translational value for soybean breeding is clear. However, the supplied material is insufficient to assess the technical validity of the core claims. Key methodological details, validation strategies, and quantitative results are absent. The cross-species transfer step is particularly concerning because no evidence is provided that Arabidopsis-trained models perform adequately on soybean sequences. The claim of constructing a gene regulatory network with "prioritized components" is not supported by any network metrics or validation data in the visible material. Overall, the idea is promising but the case is not established from the provided evidence.
- **Who would be interested in the results, and why** Plant pathologists studying oomycete diseases, soybean geneticists and breeders seeking durable resistance, computational biologists working on TF binding site prediction and gene regulatory network inference, and researchers interested in cross-species transfer of deep learning models in genomics. The potential to identify novel regulatory hubs in the soybean defense response would be of broad interest to the plant immunity community.
- **Major strengths** The study addresses a relevant agricultural problem with a clear translational motivation. The combination of experimental DAP-seq data with deep learning for TF target prediction is a contemporary and potentially powerful approach. The inclusion of both compatible and incompatible interactions allows for comparative analysis of defense responses. The use of publicly available Arabidopsis data for cross-species model training is an ambitious and potentially generalizable strategy.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4  
  - R1-M5
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria**  
  Originality: The combination of DAP-seq with deep learning for cross-species TF binding site prediction in a crop pathosystem is moderately original, though similar approaches have been reported in other systems. The specific application to soybean-P. sojae is novel.  
  Scientific importance: The potential to identify novel regulatory hubs in soybean defense is scientifically important for plant immunity and breeding. However, the importance is contingent on the validity of the predictions, which cannot be assessed from the supplied material.  
  Interdisciplinary readership: The work bridges plant pathology, genomics, and machine learning, which could attract a broad readership if the methods are rigorously validated and clearly presented.  
  Technical soundness: Not assessable from the abstract alone. Critical details on model training, validation, and network construction are missing.  
  Readability for nonspecialists: The abstract is reasonably clear for a technical audience, but the author summary improves accessibility. The deep learning and DAP-seq concepts may require additional explanation for a general readership.
- **Recommendation posture** Currently not established from the provided evidence. The authors should be encouraged to resubmit with full methodological details, validation results, and network metrics. If the technical concerns are resolved, the work could be supportive.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that deep neural networks with convolutional and recurrent layers were trained on DAP-seq data to predict new target sites of WRKY and RAV family members in the DEG set.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No details are provided on the DAP-seq data processing, peak calling, model architecture, training and test set construction, hyperparameter selection, or performance metrics. Without these, the claim that the models successfully predict new target sites cannot be evaluated.  
- **Why it matters** The core of the study rests on the validity of the deep learning predictions. If the models are poorly trained or overfit, the predicted TF-target interactions and the resulting network would be unreliable.  
- **Resolution test** Provide a detailed methods section including data preprocessing, model architecture, training and validation splits, performance metrics (e.g., AUC, precision-recall), and comparison to baseline methods. Show that the models generalize to held-out DAP-seq peaks.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that Arabidopsis DAP-seq data for five TF families were used to train similar models for cross-species TF binding site prediction on soybean.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** Cross-species prediction of TF binding sites is notoriously challenging due to differences in genome sequence, chromatin context, and regulatory grammar. The abstract provides no evidence that the Arabidopsis-trained models perform adequately on soybean sequences, nor any validation of the cross-species predictions.  
- **Why it matters** If the cross-species models are not validated, the predicted soybean binding sites may be largely false positives, undermining the gene regulatory network and any biological conclusions drawn from it.  
- **Resolution test** Provide validation results for cross-species predictions, such as comparison to soybean DAP-seq data for the same TF families, motif enrichment analysis, or experimental validation of a subset of predicted binding sites. Show that the cross-species models outperform sequence-only motif scanning.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality  
- **Claim pointer** The authors claim that a gene regulatory network depicting TF-target gene interactions that orchestrate an immune response against P. sojae was created.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract provides no information on how the network was constructed, what criteria were used to prioritize interactions, how network confidence was assessed, or whether the network was validated against known interactions or experimental data. The claim of "prioritized components" is unsupported.  
- **Why it matters** A gene regulatory network is only useful if its edges are reliable and its structure is biologically meaningful. Without validation, the network may contain many false interactions, leading to incorrect biological inferences.  
- **Resolution test** Provide a detailed description of the network inference method, edge confidence scores, network topology statistics, and validation against known TF-target interactions or independent experimental data (e.g., ChIP-seq, expression QTL, or mutant phenotypes).

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The authors claim that transcriptomes were generated to identify DEGs during compatible and incompatible interactions with P. sojae and a mock inoculation.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No details are provided on the experimental design, number of biological replicates, sequencing depth, read processing, differential expression analysis method, or significance thresholds. The selection of the two defense-related TFs (WRKY and RAV) is not justified with any data.  
- **Why it matters** Reproducibility is a fundamental requirement for any study. Without these details, the DEG list and the subsequent TF selection cannot be assessed or reproduced.  
- **Resolution test** Provide a complete description of the experimental design, bioinformatics pipeline, and statistical criteria for DEG identification. Justify the selection of the two TFs with expression data or enrichment analysis.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality  
- **Claim pointer** The authors claim that the findings "provide novel insight into molecular plant-pathogen interaction and may prove useful in developing soybean cultivars with more durable resistance."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not present any functional validation of the predicted TF-target interactions, such as mutant phenotypes, overexpression studies, or gene expression correlation analyses. The claim of novel insight and breeding utility is therefore speculative.  
- **Why it matters** Without functional validation, the biological relevance of the predicted network remains uncertain. The translational claim for durable resistance is not supported by any experimental evidence.  
- **Resolution test** Provide functional validation of at least a subset of predicted TF-target interactions, such as gene expression analysis in TF mutants or overexpression lines, or phenotypic data linking network components to resistance.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not specify the number of DEGs identified, the number of TF families enriched, or the number of predicted binding sites and network edges. Quantitative results would strengthen the summary.  
- **Required correction** Include key quantitative results in the abstract, such as the number of DEGs, the number of TF families analyzed, and the size of the predicted network.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Author summary  
- **Evidence pointer** Author summary, location not provided  
- **Issue** The author summary states that "we generated/acquired DNA-protein interactome data" but does not clarify which data were generated in-house and which were acquired from public sources.  
- **Required correction** Clarify the origin of each DAP-seq dataset in the abstract or author summary.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "prioritized components" in the author summary is vague and not defined.  
- **Required correction** Define what "prioritized" means in the context of the network, such as hub TFs identified by degree or centrality metrics.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interdisciplinary accessibility  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract assumes familiarity with DAP-seq and deep learning architectures. A brief explanation of these methods would improve accessibility for nonspecialist readers.  
- **Required correction** Add one or two sentences explaining DAP-seq and the rationale for using deep learning in this context.

## Risk / unsupported claims
- The claim that deep learning models successfully predict new TF binding sites is unsupported without performance metrics and validation.
- The claim that cross-species prediction from Arabidopsis to soybean is valid is unsupported without any validation data.
- The claim that a gene regulatory network with prioritized components was constructed is unsupported without network construction details and validation.
- The claim of "novel insight" into molecular plant-pathogen interaction is not assessable without comparison to existing knowledge.
- The claim that the findings "may prove useful in developing soybean cultivars with more durable resistance" is speculative and unsupported by functional data.