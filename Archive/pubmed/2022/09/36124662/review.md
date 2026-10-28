## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, technical soundness, and support of claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report that HMG20A, a high mobility group protein, forms a complex with the histone reader PHF14 through coiled-coil domain interactions, and that this complex modulates TGFβ and Hippo signaling pathways, thereby influencing epithelial-mesenchymal plasticity in breast cancer cells.
- **Visible evidence base** Full text including abstract, introduction, materials and methods, results, discussion, data availability, and supplementary figure/table references
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; raw mass spectrometry data not available; ChIP-seq or genome-wide binding data not provided; no structural validation beyond AlphaFold2 predictions

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive characterization of a novel protein-protein interaction between HMG20A and PHF14, with functional implications for epithelial-mesenchymal plasticity. The work combines structural prediction, biochemical validation, transcriptomic analysis, and functional assays across multiple cell lines. The identification of a new HMG20A interaction partner and its connection to Hippo and TGFβ pathways is potentially significant. However, several technical concerns regarding the strength of the interaction data, the specificity of the transcriptomic findings, and the mechanistic depth of the pathway connections need to be addressed before the conclusions are fully supported.
- **Who would be interested in the results, and why** Researchers studying chromatin regulation, histone readers, epithelial-mesenchymal transition, breast cancer biology, and Hippo/TGFβ signaling pathways would find this work relevant. The identification of a new HMG20A-PHF14 complex and its role in modulating key developmental and cancer-related pathways could inform future studies on transcriptional regulation and therapeutic targeting.
- **Major strengths** 
  1. The study identifies a novel interaction between HMG20A and PHF14, expanding the known interaction network of HMG proteins.
  2. The use of AlphaFold2 for structural prediction combined with experimental validation is a modern and rigorous approach.
  3. The phenotypic assays (migration, invasion, adhesion) are well-designed and complement the molecular findings.
  4. The transcriptomic analysis provides a genome-wide view of the effects of HMG20A and PHF14 depletion.
  5. The connection to Hippo and TGFβ pathways is biologically plausible and clinically relevant given the role of these pathways in cancer.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of interaction data
  - **Claim pointer** The authors claim that HMG20A and PHF14 form a stable nuclear complex through their coiled-coil domains.
  - **Evidence pointer** Figure 2D, E; Supplementary Figure S2A, B
  - **Concern** The co-immunoprecipitation experiments demonstrating the HMG20A-PHF14 interaction rely on overexpressed tagged proteins. No endogenous co-immunoprecipitation is shown. Additionally, the AlphaFold2 model is predictive and not experimentally validated by mutagenesis or structural biology.
  - **Why it matters** The central claim of the paper is the existence of a functional HMG20A-PHF14 complex. Without endogenous interaction data or mutational validation of the predicted interface, the physiological relevance of this interaction remains uncertain.
  - **Resolution test** Provide endogenous co-immunoprecipitation data in a relevant cell line. Alternatively, perform mutagenesis of the predicted coiled-coil interface and demonstrate loss of interaction and function.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Support for pathway-specific claims
  - **Claim pointer** The authors claim that the HMG20A-PHF14 complex modulates the Hippo pathway through direct interaction with TEAD1.
  - **Evidence pointer** Figure 5D-I; Supplementary Figure S7C
  - **Concern** The evidence for Hippo pathway modulation is indirect. While TEAD1 co-immunoprecipitation is shown, the functional significance of this interaction is not demonstrated. The authors show that YAP/TAZ-TEAD target genes are downregulated, but they also state that phospho-LATS1 and YAP levels are unchanged, suggesting the cytoplasmic Hippo pathway is not activated. The mechanism by which HMG20A-PHF14 affects TEAD activity is speculative.
  - **Why it matters** The title and abstract emphasize the modulation of Hippo and TGFβ pathways. If the mechanistic link is not firmly established, the central conclusions of the paper are weakened.
  - **Resolution test** Provide functional assays showing that HMG20A-PHF14 is required for TEAD-dependent transcription, such as reporter assays with TEAD-responsive elements, or demonstrate that the interaction with TEAD1 is necessary for the observed gene expression changes.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility and data availability
  - **Claim pointer** The authors claim that transcriptomic analyses demonstrate shared targets of HMG20A and PHF14.
  - **Evidence pointer** Figure 5A-C; Supplementary Table S3
  - **Concern** The RNA-seq analysis is based on only two biological replicates per condition. This is underpowered for robust differential expression analysis. Additionally, the criteria for defining "shared targets" are not clearly stated, and the overlap analysis may be sensitive to thresholds.
  - **Why it matters** The transcriptomic data form the basis for the claim that HMG20A and PHF14 cooperate in regulating gene expression. Underpowered analyses can lead to false positives and negatives, undermining the reliability of the conclusions.
  - **Resolution test** Increase the number of biological replicates to at least three, ideally four, and provide clear criteria for defining shared targets, including effect size thresholds and statistical significance.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Functional relevance of the DNA binding properties
  - **Claim pointer** The authors claim that HMG20A binds four-way junction DNA with higher affinity than linear DNA, suggesting a role in binding bent DNA structures.
  - **Evidence pointer** Figure 1D, E; Supplementary Figure S1E
  - **Concern** The EMSA experiments show that HMG20A binds DNA with low sequence specificity and prefers four-way junction DNA. However, the functional relevance of this binding preference is not explored. It is unclear how this property relates to the proposed role of HMG20A in transcriptional regulation.
  - **Why it matters** The DNA binding properties are presented as a key finding, but without functional context, their significance is unclear.
  - **Resolution test** Perform experiments linking the DNA binding preference to chromatin occupancy or transcriptional activity, such as ChIP-seq for HMG20A or assays with mutated HMG20A lacking DNA binding activity.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1C
  - **Evidence pointer** Figure 1C
  - **Issue** The transactivation assay data are presented as a bar graph without indication of statistical significance or error bars.
  - **Required correction** Add error bars and statistical significance indicators to the figure.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** Materials and Methods, "RNA-seq analysis"
  - **Evidence pointer** Materials and Methods section
  - **Issue** The description of the RNA-seq analysis lacks details on the alignment, quantification, and statistical methods used.
  - **Required correction** Provide a more detailed description of the bioinformatics pipeline, including software versions and parameters.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data interpretation
  - **Affected element** Figure 5I
  - **Evidence pointer** Figure 5I
  - **Issue** The experiment with YAP-5SA overexpression is described as showing that FGF1 downregulation is not suppressed, but the data are not shown in the main text.
  - **Required correction** Include the data or move it to a supplementary figure with appropriate labeling.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of the PHF14-MECP2 complex is brief and does not fully address how this relates to the HMG20A-PHF14 complex described here.
  - **Required correction** Expand the discussion to clarify the relationship between these complexes and their potential functional overlap or distinction.
- **Technical failings that need to be addressed before the case is established** 
  1. Lack of endogenous co-immunoprecipitation for HMG20A-PHF14 interaction (R1-M1)
  2. Insufficient mechanistic evidence for Hippo pathway modulation (R1-M2)
  3. Underpowered RNA-seq analysis with only two replicates (R1-M3)
  4. Unclear functional relevance of DNA binding preference (R1-M4)
- **Assessment against Nature-style criteria** 
  - Originality: The identification of a novel HMG20A-PHF14 interaction is original and adds to the understanding of HMG protein function. However, the conceptual advance is incremental, as both proteins were previously known and their individual roles partially characterized.
  - Scientific importance: The connection to Hippo and TGFβ pathways in the context of epithelial-mesenchymal plasticity is important for cancer biology. If the mechanistic claims are fully supported, this could have significant implications for understanding EMT regulation.
  - Interdisciplinary readership: The work bridges chromatin biology, signaling pathways, and cancer biology, which could attract readers from multiple disciplines. However, the technical depth may limit accessibility to non-specialists.
  - Technical soundness: The study uses a range of techniques, but several key claims lack sufficient experimental support, as detailed in the major concerns.
  - Readability for nonspecialists: The manuscript is generally well-written, but the results section is dense and may be challenging for readers without a background in chromatin biology or signaling.
- **Recommendation posture** Supportive if technical concerns are resolved. The core finding of a novel HMG20A-PHF14 interaction is potentially interesting, but the current evidence does not fully support the mechanistic claims regarding Hippo and TGFβ pathway modulation. Addressing the major concerns would significantly strengthen the manuscript.

## Risk / unsupported claims
- The claim that HMG20A and PHF14 form a "stable nuclear complex" is not fully supported without endogenous interaction data.
- The claim that the complex "modulates the Hippo pathway" is not fully supported, as the evidence is indirect and the mechanism is speculative.
- The claim that HMG20A and PHF14 "share a large subset of targets" is based on underpowered RNA-seq data and may be unreliable.
- The functional significance of HMG20A's preference for four-way junction DNA is not established.
- The statement that PHF14 and HMG20A are required for TGFβ-induced EMT is supported by the data, but the mechanistic link to the proposed complex is not fully demonstrated.