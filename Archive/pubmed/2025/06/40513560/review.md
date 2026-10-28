## Review setup
- **Input scope** Full manuscript text including summary, introduction, results, discussion, methods, and supplementary figure legends
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical rigor as presented in the provided text
- **Shared manuscript claim summary** The authors report that aged muscle stem cells (MuSCs) exhibit reduced prostaglandin E2 (PGE2)-EP4 receptor signaling, leading to precocious commitment and mitotic catastrophe. They propose that short-term PGE2 treatment reverses these age-related dysfunctions by altering chromatin accessibility, restoring cycling trajectories, and enhancing regeneration and strength in aged mice.
- **Visible evidence base** Figures 1-7 and supplementary figures S1-S7 as referenced in the text; GEO datasets GSE145297 and GSE191190; code deposited at doi.org/10.5281/zenodo.15377238
- **Missing materials affecting confidence** Actual figure images and data plots are not provided; statistical details (exact p-values, effect sizes, n numbers per experiment) are only partially described in the text; supplementary tables S1-S5 are referenced but not included; movies S1-S2 are not viewable

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially important finding that PGE2 can reverse aged MuSC dysfunction through epigenetic mechanisms. The combination of single-cell transcriptomics, ATAC-seq with neural network analysis, and functional in vivo assays is ambitious and largely appropriate. However, several technical concerns regarding data presentation, statistical rigor, and causal inference need to be addressed before the conclusions are fully supported. The claim of a "molecular memory" is intriguing but requires stronger evidence linking chromatin changes to long-term functional outcomes.
- **Who would be interested in the results, and why** Researchers in stem cell biology, aging research, regenerative medicine, and skeletal muscle physiology would find these results of high interest. The work has potential translational implications for treating sarcopenia and improving muscle regeneration in the elderly. Additionally, the application of ChromBPNet to a stem cell aging context will interest computational biologists developing deep learning approaches for epigenomics.
- **Major strengths** 1) The study addresses a clinically relevant problem (age-related muscle dysfunction) with a clear mechanistic hypothesis. 2) The multiomic approach integrating scRNA-seq, ATAC-seq, and neural network modeling is sophisticated and provides a comprehensive view. 3) The functional validation through transplantation, injury models, and exercise paradigms strengthens the translational relevance. 4) The identification of AP1 as a key transcription factor in aged MuSC dysfunction is well-supported by multiple lines of evidence.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The finding that PGE2 can reverse aged MuSC dysfunction through epigenetic reprogramming is novel and extends previous work on PGE2 in young muscle regeneration. Scientific importance: The work has high importance for understanding and potentially treating age-related muscle decline. Interdisciplinary readership: The combination of stem cell biology, epigenomics, and deep learning will attract readers from multiple fields. Technical soundness: The experimental design is generally sound, but several technical concerns (detailed below) need resolution. Readability for nonspecialists: The manuscript is well-written and accessible, though the ChromBPNet methodology may be challenging for non-computational readers.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and reproducibility
- **Claim pointer** The authors claim that PGE2 treatment significantly increases muscle mass and strength in aged mice (Figure 2F-H), and that a single PGE2 injection leads to increased myofiber cross-sectional area.
- **Evidence pointer** Figure 2F-H, Figure 2D-E, Methods section "In vivo muscle force measurement"
- **Concern** The text states that "a single dmPGE2 treatment led to a robust regenerative response that culminated in increased muscle mass and strength in male and female aged mice" but does not provide specific n numbers, effect sizes, or exact p-values for these key functional outcomes. The methods indicate that "sample size was determined based on practical and experimental consideration, with no statistical methods used to predetermine sample size," which raises concerns about statistical power. For the force measurements, n=5 mice per group is stated, but it is unclear if this applies to all functional assays. The authors should provide complete statistical details for all functional measurements, including exact p-values, confidence intervals, and effect sizes.
- **Why it matters** The central translational claim of this paper is that PGE2 improves muscle function in aged mice. Without rigorous statistical reporting, the strength of this claim cannot be adequately evaluated. Underpowered studies with small sample sizes are prone to false positives, and the lack of predetermined sample size calculations is concerning.
- **Resolution test** Provide complete statistical reporting for all functional assays, including n numbers, exact p-values, effect sizes, and confidence intervals. If possible, include power calculations or justification for sample sizes. Consider showing individual data points in figures to demonstrate the distribution of the data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that "PGE2 treatment overcomes intrinsic defects of aged MuSCs" and that the effects are mediated through EP4 receptor signaling, chromatin remodeling, and suppression of AP1 activity.
- **Evidence pointer** Figure 5A-B, Figure 6C, Figure 6I-K, Results section "PGE2 treatment promotes aged MuSC proliferation and survival"
- **Concern** While the authors show correlations between PGE2 treatment, chromatin changes, and functional improvements, the causal chain is not fully established. Specifically: (1) The claim that EP4 restoration is necessary for the observed effects is only supported by a pharmacological antagonist (ONO-AE3-208) in vitro; genetic loss-of-function experiments (e.g., conditional EP4 knockout in aged MuSCs) would strengthen this. (2) The link between AP1 suppression and functional improvement is correlative; the authors do not demonstrate that preventing AP1 suppression blocks the beneficial effects of PGE2. (3) The "molecular memory" concept is inferred from sustained functional effects after transient exposure, but the persistence of chromatin changes is not directly demonstrated over the full time course.
- **Why it matters** The manuscript proposes a specific mechanistic model (PGE2-EP4-CREB signaling suppresses AP1, leading to chromatin remodeling and functional improvement). Without direct causal evidence, alternative explanations (e.g., off-target effects of PGE2, indirect effects through other cell types) cannot be excluded. The therapeutic potential of targeting this pathway depends on understanding the precise mechanism.
- **Resolution test** Include genetic loss-of-function experiments (e.g., EP4 conditional knockout in aged MuSCs) to confirm receptor dependence. Use experimental approaches to manipulate AP1 activity (e.g., dominant-negative JUN or AP1 inhibitors) to test whether AP1 suppression is required for PGE2 effects. Demonstrate persistence of chromatin changes at the time points where functional improvements are observed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability and reproducibility
- **Claim pointer** The authors claim that ChromBPNet analysis reveals specific transcription factor binding patterns that explain PGE2-mediated changes in chromatin accessibility.
- **Evidence pointer** Figure 5C-F, Figure S4A-E, Methods section "ChromBPNet Analysis"
- **Concern** The ChromBPNet analysis is a central component of the mechanistic claims, but the description of the model training, validation, and interpretation is insufficient for reproducibility. Key details are missing: (1) The number of training/validation/test peaks is not stated. (2) The criteria for selecting "differentially accessible" peaks are not fully described. (3) The method for matching motifs to archetypal motifs and calculating confidence scores is described but not validated against known binding sites. (4) The statement that "our model confirmed the contribution of two 'GC'-centered E-box motifs" is based on visual inspection of contribution scores, but quantitative metrics of model performance (e.g., AUROC, correlation between predicted and observed accessibility) are not provided.
- **Why it matters** Deep learning models can be powerful but are also prone to overfitting and can produce spurious results if not properly validated. The reproducibility of the ChromBPNet analysis is essential for the credibility of the mechanistic claims. Without adequate model validation metrics, readers cannot assess whether the identified motifs are biologically meaningful or artifacts of the model.
- **Resolution test** Provide detailed model training and validation statistics, including performance metrics on held-out test data. Include a clear description of hyperparameter selection and model architecture. Validate the motif predictions against independent datasets (e.g., ChIP-seq data for CREB, AP1, and MyoD in MuSCs). Make the code and processed data publicly available in a format that allows others to reproduce the analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Experimental design and controls
- **Claim pointer** The authors claim that "short-term exposure of aged MuSCs to PGE2 augments their long-term regenerative capacity upon transplantation" (Figure 2I-J).
- **Evidence pointer** Figure 2I-J, Methods section "Muscle stem cell transplantation"
- **Concern** The transplantation experiments are described as using "freshly-isolated aged MuSCs" treated with PGE2 for 24 hours before transplantation. However, the text also states that "all MuSC culture assays and transplantations were performed after 1 week of culture unless noted otherwise." This discrepancy is confusing. If cells were cultured for 1 week before transplantation, the "short-term exposure" claim is misleading. Additionally, the text mentions that PGE2-treated aged MuSCs show engraftment comparable to young MuSCs, but the comparison to young MuSCs is only shown in supplementary Figure S1C, and the statistical comparison is not described in the main text.
- **Why it matters** The transplantation experiments are critical for demonstrating that PGE2 has a lasting effect on MuSC function. The timing of PGE2 exposure relative to transplantation affects the interpretation of whether the effect is truly "short-term" and whether it represents a stable epigenetic change. The comparison to young MuSCs is important for benchmarking the degree of rejuvenation.
- **Resolution test** Clarify the exact timeline of PGE2 treatment and culture before transplantation. Provide statistical analysis of the comparison between PGE2-treated aged MuSCs and young MuSCs. If cells were cultured for 1 week, discuss whether the effects of PGE2 are maintained through multiple cell divisions, which would strengthen the "molecular memory" claim.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of single-cell data
- **Claim pointer** The authors claim that single-cell transcriptomic analysis reveals an altered aged MuSC trajectory that favors direct commitment over cell cycle entry, and that PGE2 treatment reverses this.
- **Evidence pointer** Figure 4B-H, Figure S2A-D, Figure S3A-G
- **Concern** The trajectory analysis is used to support a key mechanistic claim, but the details of the analysis are not fully described. Specifically: (1) The number of cells per condition and the number of biological replicates for the scRNA-seq are not stated. (2) The criteria for defining "direct commitment" versus "cycling" trajectories are not clearly operationalized. (3) The statistical significance of the differences in trajectory proportions between young and aged, and between vehicle and PGE2-treated, is not reported. (4) The statement that "Myocyte 2 population was enriched in aged samples" is based on clustering, but the authors do not demonstrate that this enrichment is statistically significant after accounting for multiple comparisons.
- **Why it matters** The trajectory analysis is a central piece of evidence for the claim that aged MuSCs are biased toward a dysfunctional differentiation pathway. If the trajectory assignments are not robust or the differences are not statistically significant, the mechanistic model is weakened. The scRNA-seq data also underpin the claim that PGE2 restores a cycling trajectory, which is important for the therapeutic potential.
- **Resolution test** Provide detailed statistics for the scRNA-seq analysis, including cell numbers, replicate information, and statistical tests for trajectory proportion differences. Describe the trajectory inference method and the criteria for assigning cells to trajectories. Consider validating the trajectory findings with an independent method (e.g., RNA velocity or pseudotime analysis with a different algorithm).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Results section "PGE2 treatment promotes aged MuSC proliferation and survival"
- **Evidence pointer** Figure 7I, Results section
- **Issue** The text states "We assessed the cell death of aged MuSCs to determine if it resulted from apoptosis or necroptosis by flow cytometry quantification of Annexin V and 7AAD immunostaining, respectively." This sentence is grammatically awkward and the assignment of Annexin V to apoptosis and 7AAD to necroptosis is an oversimplification. Annexin V detects phosphatidylserine externalization, which occurs in both apoptosis and necroptosis, while 7AAD is a membrane impermeant dye that stains necrotic cells. The distinction between apoptosis and necroptosis cannot be made solely based on these two markers.
- **Required correction** Rewrite the sentence for clarity and acknowledge the limitations of Annexin V/7AAD staining for distinguishing apoptosis from necroptosis. Consider adding additional markers (e.g., cleaved caspase-3 for apoptosis, p-MLKL for necroptosis) to support the claim.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure presentation
- **Affected element** Figure 5E-F
- **Evidence pointer** Figure 5E-F
- **Issue** The text describes "clusters" of regulatory sites based on transcription factor combinations, but the figure legends do not clearly explain how these clusters are defined or how the reader should interpret the visualization. The use of UMAP embeddings for regulatory sites is unconventional and may be confusing to readers unfamiliar with this approach.
- **Required correction** Provide a more detailed figure legend explaining the clustering approach and the interpretation of the UMAP visualization. Consider adding a schematic diagram to illustrate the workflow from ATAC-seq to ChromBPNet to motif analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout the manuscript
- **Evidence pointer** Multiple sections
- **Issue** The term "molecular memory" is used to describe the persistent effects of PGE2 on MuSC function. While this is an evocative term, it is not well-defined and could be confused with other uses of "memory" in immunology (e.g., trained immunity) or epigenetics (e.g., cellular memory). The authors should either define the term clearly or use more precise language (e.g., "persistent epigenetic remodeling").
- **Required correction** Define "molecular memory" in the context of this study and discuss how it relates to established concepts of epigenetic memory. Alternatively, use more precise terminology throughout.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 4D-G
- **Evidence pointer** Figure 4D-G
- **Issue** The text describes "enriched" gene expression patterns in specific clusters, but the specific genes and their expression levels are not shown in the main figures. The reader cannot evaluate the biological significance of the cluster definitions without seeing the underlying gene expression data.
- **Required correction** Include a heatmap or dot plot showing the expression of key marker genes across clusters in the main figures or as a supplementary figure. This will allow readers to assess the biological validity of the cluster assignments.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methods clarity
- **Affected element** Methods section "Muscle stem cell culture, treatment and lentiviral infection"
- **Evidence pointer** Methods section
- **Issue** The methods state that PGE2 was added at 10 ng/ml, but the rationale for this concentration is not provided. Additionally, the text mentions that cells were treated for 24 hours, but it is unclear if this is the optimal duration or if dose-response experiments were performed.
- **Required correction** Provide justification for the PGE2 concentration and treatment duration, or cite previous studies that established these parameters. If dose-response experiments were performed, include the results.

## Risk / unsupported claims
- The claim that PGE2 treatment "restores" EP4 signaling to young levels is based on a single time point (24 hours) and may not reflect the long-term state of the cells.
- The statement that "PGE2 acts as a transcriptional repressor of AP1" is an oversimplification; the data show reduced AP1 activity at specific loci, but the global effect on AP1 targets is not fully characterized.
- The claim that "a single PGE2 injection" leads to long-term improvements in muscle strength is based on a single experimental paradigm (downhill running) and may not generalize to other exercise or injury models.
- The "molecular memory" concept is inferred from functional outcomes but is not directly demonstrated at the chromatin level over the full time course of the experiments.
- The statement that ChromBPNet "overcomes the limitations of antibodies and the imprecise nature of ChIP-seq" is overly broad; while ChromBPNet has advantages, it also has limitations (e.g., dependence on ATAC-seq quality, potential for false positives in motif identification) that are not discussed.
- The translational potential of PGE2 for treating sarcopenia is suggested but not directly tested; the experiments use acute injury and exercise models, not chronic age-related muscle wasting.