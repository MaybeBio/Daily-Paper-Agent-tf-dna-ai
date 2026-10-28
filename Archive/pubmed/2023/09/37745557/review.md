## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Technical soundness, methodological novelty, validation rigor, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present Allo, a tool that allocates multi-mapped reads (MMRs) in ChIP-seq and ATAC-seq data by combining probabilistic read allocation with a convolutional neural network (CNN) that classifies potential peak regions based on uniquely-mapped read distributions. They claim improved accuracy over random allocation and read-count-only methods, competitive performance with SmartMap, and demonstrate discovery of new regulatory elements in repetitive regions, including younger transposable elements.
- **Visible evidence base** Main text figures (Figures 1–7), methods descriptions, supplementary figure references, and supplementary table references
- **Missing materials affecting confidence** Supplementary figures and tables (including training details, dataset IDs, and full results) were not provided; code repository and exact software versions referenced but not independently verified; no line-level data or intermediate outputs available

## Reviewer

- **Overall assessment** The manuscript addresses a relevant and under-served problem in regulatory genomics: the systematic exclusion of multi-mapped reads from repeat-rich regions. The proposed method, Allo, is pragmatic and integrates a sensible combination of existing ideas (probabilistic allocation, CNN-based peak classification) into a usable tool with read-level output. The validation strategy using artificially shortened reads to create ground truth is clever and appropriate. However, several technical aspects require clarification and additional evidence before the central claims can be fully accepted. The comparison with SmartMap is incomplete, the statistical treatment of some results is unclear, and the generalizability of the CNN across assays and species needs stronger support. Overall, the work is promising and likely of interest to the genomics community, but the current evidence does not fully establish all stated claims.

- **Who would be interested in the results, and why** Researchers working on regulatory genomics, especially those studying transcription factor binding, chromatin accessibility, and epigenomic marks in repetitive or transposable element regions. The tool's compatibility with standard pipelines (SAM/BAM output) makes it potentially useful for ENCODE-style analyses and for evolutionary studies of repeat-derived regulatory elements. The method may also interest computational biologists developing read allocation or peak calling strategies.

- **Major strengths**  
  1. Addresses a real and acknowledged gap: MMRs are routinely discarded, leading to blind spots in repeat-rich regions.  
  2. The ground-truth validation approach (artificially shortening reads) is well conceived and provides a quantitative basis for comparing allocation methods.  
  3. Allo outputs standard alignment files, facilitating integration with existing tools and workflows.  
  4. The demonstration on 200 ENCODE datasets provides a broad view of potential impact.  
  5. The finding that Allo is particularly effective for younger TEs is biologically interesting and well contextualized.

- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness of validation  
- **Claim pointer** "Allo outcompetes both random allocation as well as read count only allocation in all K562 datasets using narrow peak mode" and similar accuracy claims in Figures 3A and 3C.  
- **Evidence pointer** Figure 3A, 3C; Methods "Read allocation accuracy"  
- **Concern** The accuracy metric is defined as the percentage of correctly allocated reads relative to ground truth. However, the ground truth is derived from full-length reads that were uniquely mappable, then artificially shortened to become multi-mapped. This creates a specific and somewhat artificial scenario: the MMRs in question are only multi-mapped because of truncation, not because of genuine genomic duplication or repeat structure. Real MMRs arising from paralogous sequences or recent repeats may have different properties (e.g., base quality, flanking context) that affect allocation difficulty. The authors do not discuss how representative this artificial MMR set is of endogenous MMRs.  
- **Why it matters** If the validation set is not representative, the reported accuracy improvements may not translate to real-world performance on native MMR populations.  
- **Resolution test** Provide a comparison using endogenous MMRs where ground truth can be established by other means (e.g., simulations with realistic repeat structures, or using long-read data to define true origins). Alternatively, discuss explicitly the limitations of the artificial shortening approach and justify its representativeness.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Completeness of comparison with existing method  
- **Claim pointer** "Allo's allocation accuracy and performance is competitive with that of SmartMap" (Section title and Figure 4A).  
- **Evidence pointer** Figure 4A; Methods "SmartMap comparison"  
- **Concern** The comparison with SmartMap is indirect and incomplete. The authors state they could not compare per-read accuracy because SmartMap outputs BedGraph files, and they instead compare average read depth at peaks. This is a reasonable workaround, but it does not directly assess allocation accuracy. Moreover, the peak-level comparison is affected by the fact that SmartMap's output is a continuous signal, not discrete read assignments, and the conversion to read depth may introduce artifacts. The authors also note that MACS2 could not call peaks on SmartMap BedGraph files properly, which raises questions about the comparability of the peak sets used.  
- **Why it matters** The claim of competitiveness with SmartMap is central to positioning Allo within the existing tool landscape. An indirect comparison with acknowledged technical difficulties weakens this claim.  
- **Resolution test** Provide a more direct comparison, perhaps by using SmartMap's output to derive read assignments (if possible) or by using a common downstream metric (e.g., FRiP, peak reproducibility) that is less sensitive to file format differences. Alternatively, clearly state the limitations of the comparison and avoid over-interpreting the results.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability of the CNN  
- **Claim pointer** "Both narrow and mixed peak neural networks were able to predict above 80% accuracy (0.5 cutoff) across all datasets (Figure 2B) including those in other species."  
- **Evidence pointer** Figure 2B; Methods "Convolutional neural network training and testing set generation"  
- **Concern** The CNN is trained on human ENCODE data (10 TF and 9 histone datasets) and tested on human, mouse, and fly datasets. While cross-species accuracy above 80% is encouraging, the number of test datasets per species is not stated, and the diversity of chromatin contexts (e.g., different histone marks, different cell types) is limited. The authors do not report performance on ATAC-seq data in the cross-species test, despite claiming applicability to ATAC-seq.  
- **Why it matters** If the CNN's peak classification is not robust across diverse chromatin landscapes, the method's utility beyond the tested conditions is uncertain.  
- **Resolution test** Report the number of datasets per species and per assay type in the cross-species test. Include ATAC-seq data in the cross-species evaluation. Provide confidence intervals or variance estimates for the accuracy figures.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Statistical rigor of enrichment analyses  
- **Claim pointer** "Allo-only peaks have a higher overlap with repetitive elements compared with UMR peaks (Figure 7B, each dot represents a ChIP-seq dataset)."  
- **Evidence pointer** Figure 7B, 7C; Methods "ENCODE K562 analysis"  
- **Concern** The comparison of overlap fractions between Allo-only peaks and UMR peaks with repetitive elements is presented as a scatter plot. It is unclear whether the differences are statistically significant across the 200 datasets. The authors mention "randomly sampled genomic regions" for the comparison in Figure 7C, but the details of the null model (e.g., matching for length, GC content, mappability) are not provided. Without a proper statistical test, the claim of enrichment is not fully supported.  
- **Why it matters** The biological conclusions about TF-repeat associations depend on the statistical validity of the enrichment analysis.  
- **Resolution test** Provide formal statistical tests (e.g., paired Wilcoxon test) comparing overlap fractions between Allo-only and UMR peaks across datasets. Describe the null model for random regions in detail, including matching criteria.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Interpretation of younger TE enrichment  
- **Claim pointer** "Allo may be particularly effective in identifying ChIP-seq peaks in younger TEs, which hold evolutionary significance due to their emergence during human evolution from primates."  
- **Evidence pointer** Figure 7D, 7E; Methods "Transposable element dating"  
- **Concern** The observation that younger TEs have more Allo-only peaks is attributed to lower mappability. However, the authors also note that human-specific TEs do not follow the general trend, and they explain this by shorter element length. This explanation is plausible but not directly tested. The analysis relies on dating from external sources, and the merging of different dating studies may introduce inconsistencies.  
- **Why it matters** The evolutionary interpretation is a key selling point of the paper. If the trend is confounded by element length or other factors, the conclusion may be overstated.  
- **Resolution test** Perform a multivariate analysis (e.g., logistic regression) including element age, length, and sequence divergence as predictors of Allo-only peak presence. This would help disentangle the effects.

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of methods  
- **Affected element** CNN training details  
- **Evidence pointer** Methods "Convolutional neural network architecture and training"  
- **Issue** The description of the CNN architecture is brief. The number of layers, filter sizes, pooling strategies, and regularization techniques are not specified in the main text.  
- **Required correction** Provide a full architectural description in the main text or a supplementary figure, including hyperparameter choices and training convergence criteria.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Software dependencies  
- **Evidence pointer** Methods "Availability"  
- **Issue** The manuscript states Allo is available on GitHub and PyPI, but does not list specific dependency versions or provide a containerized environment (e.g., Docker) for reproducibility.  
- **Required correction** Add a requirements file or environment specification, and consider providing a Docker image or conda environment file.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Presentation of results  
- **Affected element** Figure 4C  
- **Evidence pointer** Figure 4C; Methods "Performance metrics"  
- **Issue** The performance comparison shows Allo using more CPU time than SmartMap, but the authors note that multi-threading reduces wall-time. The figure appears to show CPU time, not wall-time, which may be misleading for users.  
- **Required correction** Clarify in the figure legend whether CPU time or wall-time is shown, and present both metrics for clarity.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Biological validation  
- **Affected element** CTCF motif analysis  
- **Evidence pointer** Methods "Motif identification and scanning"  
- **Issue** The motif analysis shows that the CTCF motif is enriched in Allo-only peaks, which is reassuring. However, the authors do not report whether the motif is centrally enriched, which is a hallmark of true binding sites.  
- **Required correction** Add a motif centrality analysis (e.g., average motif distance from peak center) for Allo-only peaks.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Scope of claims  
- **Affected element** Discussion  
- **Evidence pointer** Discussion section  
- **Issue** The discussion states that Allo "should be used across all datasets," which is a strong recommendation. The evidence presented focuses on ChIP-seq and one ATAC-seq dataset.  
- **Required correction** Soften the recommendation or provide additional validation on diverse assay types (e.g., more ATAC-seq, Cut&Run).

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (representativeness of artificial MMR ground truth) and R1-M2 (incomplete SmartMap comparison) are the most critical. Without addressing these, the central accuracy claims are not fully established.

- **Assessment against Nature-style criteria**  
  - **Originality**: Moderate to high. The combination of probabilistic allocation with CNN-based peak classification is novel, and the focus on MMRs in regulatory genomics is timely. However, the individual components are not new.  
  - **Scientific importance**: High. The problem of repeat-derived regulatory elements is significant, and a usable tool that integrates with existing pipelines could have broad impact.  
  - **Interdisciplinary readership**: Moderate. The work is primarily of interest to computational genomics and epigenetics researchers. The evolutionary angle may attract a broader audience, but the technical focus limits cross-disciplinary appeal.  
  - **Technical soundness**: Currently not fully established. The validation approach is clever but has limitations (R1-M1), and the comparison with SmartMap is incomplete (R1-M2). Additional statistical rigor is needed for the enrichment analyses (R1-M4).  
  - **Readability for nonspecialists**: Good. The manuscript is clearly written, with helpful figures and a logical flow. The methods are detailed, though some technical aspects (e.g., CNN architecture) could be better explained for a general audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is valuable, and the tool appears functional and useful. However, the current evidence does not fully support all claims, particularly regarding accuracy and competitiveness with existing methods. Addressing R1-M1 and R1-M2, along with the minor comments, would substantially strengthen the manuscript.

## Risk / unsupported claims
- The claim that Allo "outcompetes" other methods is based on a specific artificial ground truth scenario; generalizability to native MMRs is not demonstrated.
- The claim of competitiveness with SmartMap is based on an indirect comparison with acknowledged technical difficulties; direct per-read accuracy comparison was not performed.
- The statement that Allo "should be used across all datasets" is not supported by the breadth of validation presented.
- The biological interpretation of younger TE enrichment is plausible but not rigorously tested against confounding factors (e.g., element length).
- The cross-species generalizability of the CNN is based on an unspecified number of datasets; the robustness of the 80% accuracy claim is unclear.