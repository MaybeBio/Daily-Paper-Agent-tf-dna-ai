## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and supplementary information descriptions
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present a comparative single-cell multiomics analysis of the primary motor cortex across human, macaque, marmoset, and mouse, integrating gene expression, chromatin accessibility, DNA methylation, and chromatin conformation data from over 200,000 cells. They report evidence for species-specific gene regulatory programs, contributions of transposable elements to human-specific candidate cis-regulatory elements, conserved regulatory syntax across mammals, and utility of epigenetic conservation for interpreting disease-associated genetic variants.
- **Visible evidence base** Main text figures 1–7 (referenced), extended data figures 1–12 (referenced), supplementary tables 1–34 (referenced), methods section, and abstract. No raw data, code, or supplementary files were available for direct inspection.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and technically ambitious dataset that will be of considerable interest to the fields of comparative genomics, neurobiology, and regulatory evolution. The integration of four molecular modalities across four species and 21 cell types is a significant achievement. The central claims regarding divergence of transcription factor expression corresponding to species-specific epigenome landscapes, the role of transposable elements in human-specific regulatory elements, and the utility of epigenetic conservation for variant interpretation are plausible and generally supported by the presented analyses. However, the manuscript would be strengthened by addressing several methodological concerns, particularly regarding the robustness of cross-species comparisons, the treatment of technical confounders, and the statistical rigor of some correlative claims. The deep learning model section, while promising, requires additional validation details to fully support the claim of conserved regulatory syntax.
- **Who would be interested in the results, and why** Researchers in evolutionary genomics, regulatory biology, and neuroscience will find this resource valuable. The cell-type-resolved cross-species dataset provides a unique reference for studying how cis-regulatory divergence shapes species-specific neural traits. The integration of multiple epigenomic modalities offers a template for similar comparative studies. The demonstration that epigenetic conservation aids in interpreting non-coding disease variants has direct translational relevance for neuropsychiatric and neurological disease genetics. The machine learning component will interest computational biologists working on regulatory sequence modeling.
- **Major strengths** 1) The scale and multi-modal nature of the dataset is impressive and represents a major resource for the community. 2) The systematic framework for classifying conservation levels (sequence, tissue, cell type) is clear and well-structured. 3) The integration of 3D genome data with epigenomic conservation provides a novel perspective on regulatory evolution. 4) The application to disease variant interpretation demonstrates practical utility. 5) The deep learning approach to test regulatory syntax conservation is conceptually innovative.
- **Major Concerns** 
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: No)
  - **R1-M4** (Blocking: No)
  - **R1-M5** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2
- **Assessment against Nature-style criteria** 
  - **Originality** High. The multi-modal, multi-species single-cell comparative approach is novel and goes beyond previous transcriptome-only comparisons.
  - **Scientific importance** High. Addresses fundamental questions about regulatory evolution and provides a resource with broad applicability.
  - **Interdisciplinary readership** Broad. Will appeal to evolutionary biologists, neuroscientists, genomicists, and computational biologists.
  - **Technical soundness** Generally strong but with concerns detailed below regarding cross-species normalization, mappability correction, and statistical validation of the deep learning model.
  - **Readability for nonspecialists** The abstract and main text are largely accessible, though some sections (particularly the deep learning and 3D genome analyses) may be challenging for non-experts. The figures are referenced but not visible for assessment.
- **Recommendation posture** Supportive if technical concerns are resolved. The dataset and conceptual framework are valuable, but the current manuscript does not fully address several methodological issues that are critical for the validity of the main claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "divergence of transcription factor expression corresponds to species-specific epigenome landscapes" and present correlations between TF expression divergence and chromatin accessibility divergence across cell types (Figure 2i).
- **Evidence pointer** Main text, section "Comparative analysis of chromatin accessibility across species", Figure 2i, Methods section "Comparison of conservation index to sequence conservation"
- **Concern** The correlation between TF expression divergence and epigenome divergence (Pearson r = 0.855) is presented as evidence that TF expression changes drive regulatory landscape evolution. However, this analysis appears to be purely correlative and may be confounded by several factors. First, the analysis uses pseudo-bulk data aggregated across cells within a cell type, which may inflate correlations due to compositional effects. Second, the direction of causality is not addressed; epigenome divergence could equally drive TF expression divergence. Third, the analysis does not appear to control for phylogenetic non-independence; species are not independent data points, and the effective sample size for evolutionary correlations is the number of species (n = 4), not the number of cell types. Standard phylogenetic comparative methods should be applied. Fourth, the correlation may be driven by a few outlier cell types or TFs. Robustness analyses (e.g., jackknife, permutation) are not described.
- **Why it matters** This correlation is a central piece of evidence for the claim that TF expression divergence shapes species-specific regulatory programs. If the correlation is inflated by technical or phylogenetic confounders, the conclusion is weakened. The causal interpretation is also not justified by the correlational design.
- **Resolution test** The authors should (1) apply phylogenetic generalized least squares or similar methods that account for the non-independence of species, (2) perform sensitivity analyses excluding individual cell types or TFs, (3) test the reverse causal direction (e.g., using mediation or causal inference frameworks), and (4) report effect sizes and confidence intervals rather than only p-values.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "Transposable elements contribute to nearly 80% of the human-specific candidate cis-regulatory elements in cortical cells" and use this to support the role of TEs in species-specific regulation.
- **Evidence pointer** Main text, section "Comparative analysis of chromatin accessibility across species", Figure 2g, Methods section "Annotation of TEs and TSS proximity"
- **Concern** The calculation of TE contribution to human-specific cCREs may be substantially affected by mappability artifacts. The authors acknowledge mappability issues and apply a correction for ATAC-seq peaks, but the correction is described only briefly. Specifically, the authors state that they "normalized chromatin accessibility for mappability" but do not provide details on how this normalization was performed, how it affects the classification of human-specific cCREs, or whether the 80% figure is robust to different mappability thresholds. Given that repetitive elements (including TEs) are inherently difficult to map uniquely, the high TE contribution could be an artifact of differential mappability across species. Additionally, the classification of "human-specific" relies on liftOver, which can produce spurious results in repetitive regions. The authors should provide a more detailed sensitivity analysis, perhaps using multiple mappability thresholds or excluding multi-mapping reads entirely.
- **Why it matters** The claim that TEs contribute to nearly 80% of human-specific cCREs is a headline finding with implications for understanding human-specific evolution. If this figure is inflated by technical artifacts, the conclusion is not reliable. The manuscript's own data (Extended Data Figure 9) suggest mappability is a significant concern, yet the correction is not fully described.
- **Resolution test** The authors should (1) provide a detailed description of the mappability normalization procedure, (2) report the proportion of human-specific cCREs in TEs under different mappability thresholds (e.g., excluding all multi-mapping reads, using different mappability score cutoffs), (3) validate a subset of human-specific TE-containing cCREs by orthogonal methods (e.g., PCR, targeted sequencing), and (4) assess whether the 80% figure changes when using alternative alignment strategies.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "epigenetic conservation combined with sequence similarity helps to uncover functional cis-regulatory elements and enhances our ability to interpret genetic variants contributing to neurological disease and traits."
- **Evidence pointer** Main text, section "Epigenome conservation helps to interpret non-coding risk variants", Figure 7, Methods section "External datasets"
- **Concern** The LDSC analysis demonstrates that epigenetic conservation improves enrichment for disease variants, which is a useful finding. However, the analysis is limited to a set of neurological traits and the improvement is modest. The authors do not compare their approach to existing methods for prioritizing regulatory variants (e.g., using evolutionary conservation alone, or functional genomic annotations such as Roadmap Epigenomics). It is unclear whether the epigenetic conservation metric adds value beyond existing resources. Additionally, the analysis uses only human cCREs; the authors do not test whether the approach generalizes to other species or to non-neurological traits.
- **Why it matters** The claim that this approach "enhances our ability to interpret genetic variants" is potentially important for the field, but the current analysis does not demonstrate a clear advantage over existing methods. A head-to-head comparison would strengthen the claim.
- **Resolution test** The authors should (1) compare their epigenetic conservation metric to existing variant prioritization approaches (e.g., CADD, Eigen, Genomic Evolutionary Rate Profiling) in the same LDSC framework, (2) test additional trait categories beyond neurological, and (3) assess whether the improvement is statistically significant after multiple testing correction.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the genomic regulatory syntax is highly preserved from rodents to primates" based on the performance of their deep learning model.
- **Evidence pointer** Main text, section "Predicting cCRE use from DNA sequence", Figure 6, Methods section "Training"
- **Concern** The deep learning model is trained and evaluated within species, and cross-species performance is assessed by training on three species and predicting on the held-out fourth. While this is a reasonable design, the claim of "highly preserved regulatory syntax" requires a more rigorous demonstration. Specifically, the authors should compare their model's cross-species performance to a null model that uses only sequence features (e.g., GC content, motif presence) without learning regulatory syntax. Additionally, the model's performance is evaluated on cCREs, which are defined by chromatin accessibility; this creates a circularity concern, as the model is trained to predict the same type of data it is evaluated on. The authors should clarify whether the model learns general regulatory syntax or simply memorizes sequence features associated with accessibility.
- **Why it matters** The claim of conserved regulatory syntax is conceptually important and has implications for cross-species regulatory prediction. If the model's performance is driven by simple sequence features rather than learned syntax, the claim is overstated.
- **Resolution test** The authors should (1) compare their model to simpler baselines (e.g., k-mer frequency models, motif-based models), (2) perform ablation studies removing different sequence features, and (3) test the model on held-out regulatory elements that are not defined by chromatin accessibility (e.g., validated enhancers from other assays).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors identify cell-type-specific conserved and divergent gene regulatory programs, including species-specific cell type composition changes.
- **Evidence pointer** Main text, sections "Comparing gene expression across species" and "Comparative analysis of chromatin accessibility across species", Figures 1c,d and 2
- **Concern** The analysis of cell type composition (Figure 1c,d) is based on unsupervised clustering and integration across species. The authors note that cell type fractions are "highly species specific," but the interpretation of this finding is underdeveloped. For example, the expansion of oligodendrocytes in humans could reflect biological differences or technical artifacts (e.g., differential cell survival, nuclei isolation efficiency across species). The authors do not validate their cell type composition estimates with independent methods (e.g., immunohistochemistry, flow cytometry). Additionally, the integration approach using orthologous genes may introduce biases if gene annotation quality differs across species.
- **Why it matters** The claim of species-specific cell type composition is a notable finding, but if it is driven by technical artifacts, it would mislead interpretations of regulatory evolution. The manuscript would benefit from a more cautious interpretation and additional validation.
- **Resolution test** The authors should (1) validate cell type composition estimates using an independent approach, (2) assess the sensitivity of their results to different clustering parameters and integration methods, and (3) discuss potential technical confounders more thoroughly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "Divergence of cis-regulatory elements drives species-specific traits" is presented as an established fact, but the manuscript itself provides evidence that this is an active area of investigation. The opening could be more nuanced.
- **Required correction** Consider revising to "Divergence of cis-regulatory elements is thought to drive species-specific traits" or similar.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, cell type annotation
- **Evidence pointer** Methods section "10x multiome sequence data processing and clustering"
- **Issue** The manuscript states that cell types were annotated by "reference mapping to published M1 snRNA-seq datasets" but does not specify which datasets were used for each species or how reference labels were transferred. This limits reproducibility.
- **Required correction** Provide specific references for the reference datasets used for each species and describe the label transfer procedure in more detail.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, DMR calling
- **Evidence pointer** Methods section "Cluster-level DNA methylome analysis"
- **Issue** The DMR calling procedure uses a minimum methylation difference of 0.3, which is a relatively high threshold. The authors do not report how sensitive their results are to this parameter.
- **Required correction** Report the number of DMRs identified at different thresholds or justify the chosen threshold with reference to prior work.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Main text, section "Comparing gene expression across species"
- **Evidence pointer** Main text, paragraph beginning "Of 13,822 gene orthologues..."
- **Issue** The distinction between "mammal-conserved" and "primate-conserved" genes is clear, but the criteria for "non-ubiquitous" expression are not defined in the main text.
- **Required correction** Define the specificity threshold used to classify genes as non-ubiquitous in the main text or refer readers to the Methods section more explicitly.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, deep learning model
- **Evidence pointer** Methods section "Training"
- **Issue** The manuscript states that models were trained on a single GPU, but does not report training time, number of parameters, or convergence criteria. This limits the ability to assess the computational feasibility of the approach.
- **Required correction** Provide basic model specifications and training details.

## Risk / unsupported claims
- The claim that "divergence of transcription factor expression corresponds to species-specific epigenome landscapes" is supported only by correlational analysis that does not account for phylogenetic non-independence or establish causality.
- The claim that "Transposable elements contribute to nearly 80% of the human-specific candidate cis-regulatory elements" may be inflated by mappability artifacts; the correction procedure is not described in sufficient detail to assess its adequacy.
- The claim that "the genomic regulatory syntax is highly preserved from rodents to primates" is based on a deep learning model whose performance is not compared to simpler baselines, making it unclear whether the model learns general regulatory syntax or simple sequence features.
- The claim that "epigenetic conservation combined with sequence similarity helps to uncover functional cis-regulatory elements" is not compared to existing variant prioritization methods, so the incremental value is unclear.
- The finding of species-specific cell type composition is not validated by independent methods and may be affected by technical artifacts in nuclei isolation or clustering.