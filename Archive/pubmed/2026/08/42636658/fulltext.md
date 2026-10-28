# Single-cell and bulk transcriptomic profiling of M2-like tumor-associated macrophages reveals a prognostic signature and an inflammation–metabolism crosstalk program in multiple myeloma


## Highlights
  •Seven MM-specific M2-TAM subsets (MM-M2) are absent in normal bone marrow.•MM-M2 subclusters exhibit distinct transcription factor programs via SCENIC.•Enhanced ligand–receptor signaling links MM-M2 to plasma and stromal cells.•An 11-gene RSF-derived MRGs signature stratifies MM patients by survival.•MM-M2 inflammatory mediators suggest links to systemic inflammation-metabolism axis.

  Seven MM-specific M2-TAM subsets (MM-M2) are absent in normal bone marrow.

  MM-M2 subclusters exhibit distinct transcription factor programs via SCENIC.

  Enhanced ligand–receptor signaling links MM-M2 to plasma and stromal cells.

  An 11-gene RSF-derived MRGs signature stratifies MM patients by survival.

  MM-M2 inflammatory mediators suggest links to systemic inflammation-metabolism axis.


## Introduction
  Multiple myeloma arises from malignant plasma cells that accumulate within the bone marrow, disrupting normal hematopoiesis and causing widespread organ damage. Skeletal destruction, renal impairment, hypercalcemia, and anemia define its clinical presentation. It is the second most common hematological malignancy worldwide, responsible for close to 10% of all blood cancers. The numbers are sobering: GLOBOCAN 2022 reported approximately 188,000 new diagnoses and 121,000 deaths in a single year [1,2].

  The last twenty years have brought major treatment advances. Proteasome inhibitors came first, then IMiDs, anti-CD38 monoclonal antibodies, and autologous stem cell transplantation. Each has broadened what clinicians can offer. Yet the problem persists: nearly all patients relapse eventually, and only a fraction achieve lasting remission [3,4]. Why outcomes vary so widely from patient to patient is not fully understood, but cytogenetic heterogeneity and the way plasma cells co-opt their bone marrow surroundings clearly play a role. Better prognostic markers and new druggable targets are badly needed.

  The bone marrow microenvironment matters enormously in myeloma [5,6]. Stromal cells, osteoclasts, endothelial cells, and immune populations all work together to shield plasma cells from both immune attack and chemotherapy. Macrophages deserve special attention here. Tumor-associated macrophages (TAMs) are the dominant myeloid cell type in the MM niche, accounting for around 10% of total marrow cellularity [7]. They are recruited by chemokines that plasma cells and stromal cells secrete — notably CXCL12, CCL2, and VEGF — which attract circulating monocytes and promote their differentiation toward an M2-polarized, immunosuppressive phenotype via bidirectional cross-talk with the niche [7,8].

  What do M2-TAMs actually do? They promote tumor growth on several fronts. Their secretion of IL-10, TGF-β, and IL-6 impairs cytotoxic T-cell function and facilitates immune evasion, while production of VEGF and matrix metalloproteinases promotes angiogenesis [9,10]. These are not just laboratory observations. Clinically, elevated CD68⁺/CD163⁺ macrophage density in the marrow correlates with increased microvessel density, poorer responses to chemotherapy, and worse overall survival, independent of disease stage [11,12].

  There is a problem with how M2-TAMs have been studied so far, though. Most work treats them as one uniform group. But immune cells are rarely that simple. M2 macrophages almost certainly contain transcriptionally diverse subsets, and different subsets may matter differently for disease progression. Bulk transcriptomics cannot see this kind of internal variation because it averages expression across all cells in a sample [13].

  Single-cell RNA sequencing (scRNA-seq) offers a way around this limitation. It reads gene expression cell by cell, which means rare subpopulations, regulatory circuits, differentiation paths, and signaling networks that bulk methods miss entirely can now be detected [14,15]. Several groups have already applied scRNA-seq to MM and found stepwise immune dysregulation — affecting T cells, NK cells, and myeloid populations — as disease progresses from MGUS through smoldering myeloma to overt MM [16,17]. Separately, hdWGCNA can extract co-expression modules from specific cell subsets at single-cell resolution [18]. And consensus machine learning frameworks — which pool predictions across many algorithm configurations — tend to outperform single-algorithm Cox regression when tested on independent cohorts [19,20].

  That is the starting point for the present study. We combined MM and normal bone marrow scRNA-seq data to isolate an MM-restricted M2-TAM subpopulation (MM-M2), mapped its transcription factor programs and signaling networks, and built a consensus prognostic gene signature (MRGs). The gene candidates came from hdWGCNA modules, and the final model was selected from 101 algorithm configurations across ten machine learning methods. The MRGs signature stratified patients by survival, exposed different immune microenvironment profiles between risk groups, and flagged candidate compounds for high-risk disease.


## Materials and methods

### Data sources and processing
  Two scRNA-seq datasets — GSE124310 and GSE278230, both hosted on GEO — provided the raw single-cell data for MM and normal bone marrow. We kept the quality filters from the original publications. Cells made it through if they expressed at least 500 genes, had mitochondrial reads below 20%, and erythrocyte gene content under 1%. Anything that failed was dropped. Harmony [21] handled batch correction between the two datasets. The downstream pipeline — log-normalization, principal component analysis, UMAP projection, and Louvain clustering — ran in Seurat v4.3.0 [22]. For cell-type labels, we followed the annotation scheme published by Wang et al. [23].

  For bulk-level validation, we brought in three additional GEO datasets. GSE9782 [24] served as the training cohort (it includes survival follow-up for bortezomib-treated patients). GSE57317 [25] was the independent validation set. GSE6477 [26] contributed normal-versus-MM comparisons for differential expression. Expression values were converted to TPM before running limma [27] for differential analysis. All data used here are publicly available—no restricted-access materials were involved.


### Intercellular communication
  For cell-to-cell signaling, we ran two tools that work quite differently from each other. CellCall [28] takes a pathway-centered approach — it curates ligand–receptor–transcription factor axes from KEGG and infers both intercellular and intracellular regulatory signals simultaneously. We used it to compare pathway activity between MM and normal samples.

  CellChat v1.6.0 [15] uses a different framework. It draws on its own curated database (CellChatDB.human) to quantify ligand–receptor pair probabilities between annotated cell types. We looked at 32 pathways across all cell types, paying closest attention to interactions that involved M2 macrophages — both as signal senders and as receivers.


### Transcription factor networks
  SCENIC [29] was used to map transcription factor (TF) activity in each M2-TAM subcluster. How it works: co-expression modules go in first, and RcisTarget scans for enriched cis-regulatory motifs near the transcription start site (using the hg19-tss-centered-10 kb ranking database). The output is a set of regulons — TFs paired with their predicted target genes. We visualized the top-ranked regulons per subcluster using pheatmap.


### Enrichment analyses
  GO and KEGG [31] enrichment were run through clusterProfiler [30]. The significance cutoff was FDR < 0.05. For pathway-level scoring across individual cells or samples, we applied GSVA [32], which converts gene sets into sample-level enrichment scores with no need for an explicit reference group.


### Co-expression modules via hdWGCNA
  The standard WGCNA algorithm was not designed for single-cell data — it expects a sample-by-gene matrix, not a cell-by-gene matrix with tens of thousands of observations. hdWGCNA [18] gets around this limitation by grouping cells into metacells before building the co-expression network—a compromise that keeps enough resolution without sacrificing statistical power. We applied it to the M2 macrophage compartment and compared module distributions between MM and normal samples to identify the modules most tightly associated with MM-M2 cells.


### Trajectory reconstruction
  Monocle 2 [33] reconstructed the pseudotime trajectory of M2-TAM subpopulations. DDRTree was the dimensionality reduction method. Cells were ordered along the trajectory according to their differentially expressed gene profiles, so that the shift from normal M2 states to MM-specific phenotypes.


### Building and testing the prognostic model
  The gene-level inputs came from intersecting hdWGCNA key modules with GSE6477 DEGs. Prognostic filtering used bootstrap univariate Cox regression on GSE9782 [24], with GSE57317 [25] held back for validation.

  We did not settle for one algorithm. Instead, we tested 101 combinations across 10 methods [34]: random survival forests [35], elastic net regression [36], Lasso penalized Cox [37], Ridge, stepwise Cox, CoxBoost [38], partial least squares Cox regression [39], supervised principal components [40], gradient boosted models [41], and survival support vector machines [42]. Each combination was fit via leave-one-out cross-validation on the training data. All resulting models were tested on the validation cohort. The model with the highest average C-index was kept as the final MRGs signature.


### Risk groups and survival curves
  Survminer determined the optimal score cutoff. Patients above the cutoff were labeled high-risk; those below, low-risk. Kaplan–Meier curves (survival package [43]) and time-dependent ROC analysis assessed stratification performance.


### Immune landscape profiling
  ESTIMATE [44] generated stromal and immune scores from bulk expression. For granular immune cell composition, the IOBR package [20] ran six deconvolution algorithms side by side: CIBERSORT [45], EPIC [46], MCPcounter [47], TIMER [48], xCell [49], and quanTIseq [50]. The rationale for running all six in parallel is simple: no single algorithm is bias-free.


### Drug sensitivity screen
  CCLE [51] supplied cancer cell line expression profiles. Drug response data came from two sources: CTRP v.2.0 [52] (which tests compounds against hundreds of cell lines) and the PRISM repurposing dataset [53] (which screens approved and experimental compounds in a high-throughput format). We then compared AUC values between the high- and low-risk groups to see which compounds behaved differently.


### Metabolic and inflammatory pathway scoring
  Metabolic and inflammatory transcriptional programs were evaluated using ten MSigDB Hallmark v7.5 gene sets: HALLMARK_GLYCOLYSIS, HALLMARK_OXIDATIVE_PHOSPHORYLATION, HALLMARK_FATTY_ACID_METABOLISM, HALLMARK_HYPOXIA, HALLMARK_MTORC1_SIGNALING, HALLMARK_CHOLESTEROL_HOMEOSTASIS, HALLMARK_TNFA_SIGNALING_VIA_NFKB, HALLMARK_IL6_JAK_STAT3_SIGNALING, HALLMARK_INFLAMMATORY_RESPONSE and HALLMARK_INTERFERON_GAMMA_RESPONSE. The raw 10x data were reprocessed in Python with Scanpy. Cells with fewer than 500 detected genes or more than 20% mitochondrial transcripts were removed; counts were normalized to 10,000 per cell and log-transformed. After selection of 2000 highly variable genes, principal-component analysis (30 components), Harmony integration by sample (maximum 10 iterations), and Leiden clustering were performed. At single-cell resolution, an AUCell-style score was calculated in Python by ranking genes within each cell and integrating recovery over the top 5% of detected genes (maxRank = 0.05 × the number of genes). MM-M2 cells were defined as MM-enriched macrophage subclusters (Ro/e > 1) with above-median M2-marker scores. AUCell-style pathway scoring and SCENIC were treated as complementary, non-equivalent analyses: the former measured enrichment of predefined pathway gene sets, whereas SCENIC inferred transcription-factor regulon activity from co-expression and motif information. In the bulk cohorts, the same Hallmark sets were scored with a Python implementation of ssGSEA using descending gene ranks and a weighting exponent of 0.25.


### Inflammation–metabolism crosstalk and systemic scoring
  Associations between inflammatory and metabolic pathway scores were examined with two-sided Spearman correlation, across MM-M2 cells in the single-cell analysis and across patients in the bulk cohorts. Because these analyses were exploratory, nominal p < 0.05 was used for the correlation heatmaps without multiplicity adjustment. MRGs genes were annotated by membership in the Hallmark and KEGG v7.5.1 gene sets, supplemented by curated literature evidence. For each bulk cohort, pathway scores were z-standardized across samples and the composite metabolic score was calculated as the mean of the six standardized metabolic pathway scores. Survival was compared after a median split by Kaplan–Meier analysis and a log-rank test. A Cox model containing both the standardized composite metabolic score and the standardized MRGs risk score was used to determine whether the two measures carried overlapping prognostic information.


## Results

### Building the single-cell atlas
  After filtering and batch correction, the merged scRNA-seq dataset resolved into distinct populations on UMAP: plasma cells, T cells, macrophages, NK cells, B cells, endothelial cells, stromal cells, and others (Fig. 1B). Marker gene dot plots (Fig. 1A) and feature plots (Fig. 1C) confirmed the annotations. A ClusterGVis heatmap captured the top differentially expressed genes per cluster (Fig. 1D). The atlas covers the major cellular compartments of the MM bone marrow niche.Fig. 1Single-cell atlas of MM and normal bone marrow. (A) Marker gene dot plot across clusters. (B) UMAP of all cell populations. (C) Feature plots for representative markers. (D) Top differentially expressed genes per cluster (ClusterGVis heatmap).Fig 1 dummy alt text


### Finding MM-M2
  Cell-type proportions shifted between MM and normal marrow, with macrophages standing out (Fig. 2A). Splitting the UMAP by disease status made the difference visible (Fig. 2B). M2 macrophages were significantly overrepresented in MM; M1 levels held steady (Fig. 2C).Fig. 2MM-M2 subpopulation identification. (A) Cell-type proportion changes between MM and normal. (B) Macrophage UMAP, split by disease. (C) M1 vs. M2 proportions. (D) M2 sub-clustering. (E) Subcluster distribution; clusters 0, 1, 3, 4, 5, 7, 9 = MM-M2. (F) Ro/e enrichment. (G) Top-six SCENIC regulons per subcluster.Fig 2 dummy alt text

  The picture got more interesting once we re-clustered the M2 cells (Fig. 2D). Seven subclusters — numbered 0, 1, 3, 4, 5, 7, and 9 — were almost entirely absent from normal bone marrow and present only in MM samples (Fig. 2E), collectively designated MM-M2. Ro/e analysis corroborated this enrichment statistically (Fig. 2F). SCENIC regulon analysis added another layer: each subcluster had a unique combination of top-ranked regulons (Fig. 2G). MM-M2, in other words, is not one population. It is several, each running a different transcriptional program.


### Communication rewiring in MM
  CellChat picked up numerous pathways whose activity changed between MM and normal marrow (Fig. 3A). The incoming and outgoing signal heatmaps (Fig. 3B, C) showed that communication roles shifted across cell types. M2 macrophages stood out: their ligand–receptor interaction strength was substantially increased in MM relative to normal marrow, both in the context of M2 cells as signal senders (Fig. 3D) and as signal receivers (Fig. 3E), In short, M2-TAMs in MM are wired into a denser signaling network with plasma cells and stromal cells than their counterparts in healthy marrow. This likely helps maintain the immunosuppressive niche.Fig. 3Differential intercellular communication. (A) Pathway-level differences. (B) Incoming signal heatmap. (C) Outgoing signal heatmap. (D) M2 as ligand source. (E) M2 as receptor target.Fig 3 dummy alt text


### Differentiation trajectory and gene modules
  Pseudotime ordering traced a differentiation arc — normal M2 macrophages at one end, MM-M2 at the other, with intermediate states in between (Fig. 4A, B). We then used hdWGCNA to find co-expression modules within the M2 compartment, looking for the gene programs that drive this phenotypic shift. The soft-threshold plot confirmed scale-free topology (Fig. 4C). The dendrogram partitioned genes into modules (Fig. 4D), and module eigengene correlations showed clean separation (Fig. 4E). Projecting module activity onto UMAP space showed which modules were active in which subsets (Fig. 4F) — and these modules served as the starting point for building the prognostic model.Fig. 4Pseudotime and co-expression networks. (A–B) M2-TAM differentiation trajectory. (C) Soft-threshold selection. (D) Gene dendrogram and modules. (E) Module eigengene correlations. (F) Module activity on UMAP.Fig 4 dummy alt text


### The 101-Algorithm prognostic model
  Candidate genes came from intersecting hdWGCNA modules with GSE6477 DEGs, then filtering by bootstrap Cox regression. The 101 algorithm combinations each produced a model; LOOCV on GSE9782 fit them, GSE57317 tested them. The winning combination — highest mean C-index — became the MRGs signature (Fig. 5A).Fig. 5MRGs model performance. (A) C-index across 101 combinations. (B–C) Kaplan–Meier curves, training and validation. (D–E) Time-dependent ROC. (F) Per-gene multivariate contribution.Fig 5 dummy alt text

  Prognostically, the MRGs signature performed well. High-risk patients died sooner in both the training and validation cohorts (Fig. 5B, C). ROC curves at different time points confirmed reasonable discriminative power (Fig. 5D, E). A multivariate analysis showed which genes in the signature contributed independently to the prediction (Fig. 5F).


### Two different immune worlds
  By ESTIMATE, high-risk patients had lower stromal, immune, and composite scores, meaning higher tumor purity (Fig. 6A–D). All six deconvolution algorithms agreed: low-risk patients had more immune cell infiltration than high-risk patients (Fig. 6E). We also correlated individual MRGs genes with the infiltration estimates, which connected specific signature genes to specific immune cell types (Fig. 6F).Fig. 6Immune microenvironment by risk group. (A–D) ESTIMATE score differences. (E) Six-algorithm infiltration comparison. (F) Gene-immune cell correlations.Fig 6 dummy alt text


### Pathways and drug leads
  GSEA [54] painted a clear picture of the biology: proliferation and immune evasion pathways dominated in high-risk patients, while active immune signaling was enriched in the low-risk group (Fig. 7A). Gene-by-pathway correlations then showed which MRGs genes drove which pathways (Fig. 7B).Fig. 7Functional and drug sensitivity profiles. (A) GSEA pathway enrichment. (B) Gene-pathway correlations. (C) CTRP sensitivity. (D) PRISM sensitivity.Fig 7 dummy alt text

  From the CTRP and PRISM drug screens, we pulled out compounds whose AUC values differed significantly between the two risk groups (Fig. 7C, D). To be clear, these are not clinical recommendations — they are leads, suggesting that MRGs-based stratification might help match patients with the right compounds.


### Hypoxia-associated transcriptional changes in MM-M2 macrophages
  Pathway scoring identified a distinct transcriptional pattern in MM macrophages compared with normal bone-marrow macrophages. The hypoxia Hallmark score was higher (p ≈ 6 × 10⁻⁴⁹) and the oxidative-phosphorylation score was lower (p ≈ 3 × 10⁻⁵⁶), whereas the glycolysis score did not differ (p = 0.79). Thus, the data support a hypoxia-skewed transcriptional state with reduced oxidative-phosphorylation-associated expression, not generalized glycolytic activation (Fig. 8A, B). These scores also changed along the inferred trajectory from normal to MM-enriched macrophage states (Fig. 8C). They reflect gene-expression programs and should not be interpreted as direct measurements of metabolic flux.Fig. 8Hypoxia-associated transcriptional programs and inflammation–metabolism correlations in MM-M2 macrophages. (A) Hallmark pathway scores calculated with an AUCell-style procedure across macrophage subclusters (asterisks, MM-M2). (B) Hypoxia and oxidative-phosphorylation scores in MM and normal macrophages. (C) Pathway scores along the inferred differentiation trajectory. (D) Spearman correlations between inflammatory and metabolic pathway scores within MM-M2 cells. (E) Hypothesis-generating model of the observed associations among hypoxia-related, HIF-1α/NF-κB/STAT3 and inflammatory transcriptional programs. The schematic does not establish causal directionality.Fig 8 dummy alt text


### Inflammatory and metabolic transcriptional programs are correlated in MM-M2 cells and bulk cohorts
  We next tested whether the hypoxia-associated pattern coincided with inflammatory transcriptional programs. Within MM-M2 cells, the hypoxia score correlated with NF-κB (r = 0.36), STAT3 (r = 0.38), inflammatory-response (r = 0.45) and interferon-γ-response scores (r = 0.49); the oxidative-phosphorylation score was inversely correlated with NF-κB signaling (Fig. 8D). Similar correlations were observed in the bulk training cohort, where the hypoxia score correlated with NF-κB (r = 0.64), STAT3 (r = 0.41) and inflammatory-response scores (r = 0.45) (Fig. 9F). Agreement across the two data resolutions supports the reproducibility of these associations, but does not establish their direction or causality.Fig. 9Systemic inflammation–metabolism axis and the MRGs signature. (A) Inflammatory and metabolic annotation of the MRGs genes. (B) Composite metabolic and inflammatory scores by MRGs risk group in the training and validation cohorts. (C, D) Kaplan–Meier analysis by metabolic-score median in the training (C) and validation (D) cohorts. (E) Multivariate Cox analysis (composite metabolic score with the MRGs risk score). (F) Patient-level Spearman correlation between inflammatory and metabolic pathways.Fig 9 dummy alt text


### The inflammation–metabolism axis maps onto the MRGs prognostic signature
  Finally, we connected this axis to the prognostic signature. Seven of the eleven MRGs genes carry inflammatory or metabolic functions, including the glycolytic enzyme PKM (PKM2), the mitochondrial-ribosome and oxidative-phosphorylation gene DAP3, the amino-acid and lipid metabolism genes CNDP2 and GDPD5, and the inflammatory genes IFI16, TNFRSF14 and CDKN2A (Fig. 9A). At the cohort level, the composite metabolic score was significantly higher in high-risk than in low-risk patients in both the training (GSE9782, p = 0.013) and validation (GSE57317, p = 0.018) cohorts, whereas inflammatory scores were not elevated and trended lower in high-risk disease, consistent with the immune-depleted high-risk microenvironment described above (Fig. 9B). The composite metabolic score stratified overall survival in both cohorts (log-rank p = 0.047 and p = 0.0097); because it is collinear with the MRGs risk score, it reflects the same prognostic axis rather than providing independent prognostic value (Fig. 9C–E).


## Discussion
  MM treatment has improved, but the core problem has not gone away: most patients relapse, and long-lasting remissions are rare [3,4]. A large part of the blame falls on the bone marrow microenvironment — M2-polarized TAMs in particular maintain tumor cell survival, blunt immune responses, and blunt drug efficacy [7,10,55]. None of this is new. What has been missing is a finer-grained look at whether M2-TAMs are internally diverse and, if so, whether that diversity has clinical consequences. That is what we set out to do, using scRNA-seq combined with multi-cohort bulk transcriptomic data to define MM-specific M2-TAM populations and to build a prognostic signature — MRGs — derived from 101 machine learning algorithm configurations.

  The central finding, we think, is that MM-M2 exists as a transcriptionally distinct entity. Seven M2 subclusters turned up exclusively in myeloma marrow; healthy controls had almost none of them. Both Ro/e enrichment and SCENIC regulon analysis confirmed this independently, supporting both the disease-specificity of these subclusters and their transcriptional heterogeneity. Earlier scRNA-seq work had hinted at something along these lines — Zavidij et al. [16] described stepwise myeloid remodeling from MGUS to MM, and Liu et al. [17] saw shifts in macrophage polarization within MM marrow — but neither study broke open the M2 compartment itself. Our data suggest that what we call M2 is actually a collection of functionally distinct cell states, each driven by its own transcription factor program. STAT3, NF-κB, and HIF-1α — recognized drivers of M2 polarization [56,57] — appeared across subclusters but with differing relative activity, which raises the possibility that different MM-M2 subsets promote tumor growth through different mechanisms. If that holds up in functional experiments, some of these subsets could become selective therapeutic targets.

  The signaling data tell a consistent story. In MM, ligand–receptor interaction strength involving M2 macrophages — both outgoing and incoming — was markedly higher than in normal marrow. On one side, TAMs produce IL-6, VEGF, and CCL2 that sustain plasma cell survival and drive angiogenesis [7,8,58]. On the other, stromal and plasma cells release CXCL12 and M-CSF, which push macrophages further toward M2 polarization [8]. The fact that CellChat and CellCall, two tools with quite different underlying logic, both picked up this reciprocal axis strengthens our confidence in the result. At a practical level, the pathway-resolution we obtained here might help identify which signaling nodes are worth targeting to disrupt TME–TAM crosstalk.

  Two choices we made in the analysis deserve some explanation. We chose hdWGCNA over conventional differential expression analysis for gene selection. The reason is straightforward: hdWGCNA pulls out co-expressed gene modules from a defined cell population, so the resulting gene sets are functionally related by design. Had we simply used all M2 markers or all DEGs, we would have included many genes unrelated to MM-M2 biology, and that would dilute the prognostic signal. Second, we deliberately avoided committing to a single prognostic algorithm. Lasso-Cox is the default in many comparable studies [59,60], but it can overfit badly when sample sizes are small. Instead we ran 101 algorithm combinations across 10 methods and picked whichever achieved the best mean C-index on the independent validation cohort. That MRGs performed well in both GSE9782 and GSE57317 gives us some confidence that the result is not an artifact of one particular method.

  The immune profiling results help explain, biologically, what the MRGs score reflects. Patients classified as high-risk had lower stromal and immune scores and less immune cell infiltration, and this pattern held across all six deconvolution algorithms we tested. Since M2-TAMs are known to suppress anti-tumor immunity via IL-10, TGF-β, Treg induction, and checkpoint ligand upregulation [9,10,55], a link between high MRGs scores and an immune-depleted microenvironment makes biological sense. On the flip side, low-risk patients were enriched for immune activation gene sets in GSEA. This is speculative, but it raises the question of whether these patients might respond better to immunotherapy. Checkpoint blockade is still experimental in MM [61]; our data do not answer the question directly, but they offer a rationale for testing it. As for the drug sensitivity screen, CTRP and PRISM flagged compounds whose activity differed between risk groups. Some chemotherapeutic agents can repolarize TAMs through immunogenic cell death [62,63], so in principle MRGs-based stratification could one day help guide combination therapy. That remains speculative for now.

  The pathway-score analysis adds a transcriptional dimension to the MM-M2 phenotype. Higher hypoxia scores accompanied lower oxidative-phosphorylation scores, without a detectable change in glycolysis. Hypoxia scores also correlated with NF-κB- and STAT3-related programs in single cells and bulk cohorts. These observations are compatible with the previously described lactate–HIF-1α axis of macrophage polarization [57], but they do not show that this axis is active or causal in the present samples. Fig. 8E is therefore presented as a hypothesis-generating model rather than a resolved mechanism.

  These associations suggest several lines of translational work. HIF-1α-directed treatment could be tested for its ability to alter the MM-M2 transcriptional state; macrophage depletion or repolarization could be examined alone and with established anti-myeloma therapy; and metabolic interventions could be evaluated in models that preserve interactions among plasma cells, stromal cells and macrophages. Such strategies cannot be inferred to be effective from the present data. They require metabolic-flux measurements, perturbation of the proposed HIF-1α/NF-κB/STAT3 nodes, primary-cell co-culture experiments and in vivo validation. At the patient level, the composite metabolic score was collinear with MRGs and is best regarded as another readout of the same prognostic axis, not as an independent biomarker.

  We should be upfront about this study's limitations. The scRNA-seq datasets are from public repositories, and the sample sizes are not large. Selection bias is a real concern. The model was trained and validated retrospectively, so prospective testing is essential before drawing clinical conclusions. We also have no functional data on MM-M2 subsets. Everything here is transcriptomic; whether these subsets actually behave differently in the marrow requires in vitro and in vivo follow-up. The drug sensitivity analysis, similarly, comes from cell line data and has no clinical validation behind it. Several caveats apply specifically to the inflammation–metabolism analyses: the associations reported here are transcriptome-based correlations rather than demonstrations of causality, and functional perturbation of the lactate/HIF axis will be needed to establish directionality; the systemic metabolic score is a transcriptomic surrogate that was not validated against circulating biomarkers and is collinear with the MRGs risk score rather than independently prognostic; and the single-cell crosstalk was assessed at pathway-score resolution, so transcription-factor regulon activity (HIF1A, NF-κB, STAT3) would further resolve the axis.

  To sum up: by integrating single-cell and bulk transcriptomic data, we identified M2-TAM subsets that are specific to MM and transcriptionally distinct from each other, characterized how they communicate with other cells in the marrow, and built a consensus prognostic signature — MRGs — derived from hdWGCNA modules and tested across 101 machine learning configurations. MRGs separates patients by survival, captures real differences in the immune microenvironment, and generates drug hypotheses worth following up. We think these findings bring us a step closer to understanding what macrophage heterogeneity means in MM, and they may eventually help refine how we stratify patients by risk.


## Ethics statement
  This study was based exclusively on publicly available, de-identified datasets from the Gene Expression Omnibus (GEO). No human subjects were recruited, and no patient-identifiable information was accessed. Ethical approval was therefore not required.


### Informed consent
  Not applicable. All data used in this study were obtained from publicly available repositories with no direct patient contact.


## CRediT authorship contribution statement
  Hui Zhao: Writing – original draft, Validation, Investigation, Data curation, Conceptualization. Jing Kang: Software, Investigation. Huiling Ouyang: Methodology. Xiaye Lv: Visualization, Investigation. Ziying Huang: Methodology. Bingni Zhao: Software. Kai Wang: Writing – review & editing, Validation, Project administration, Funding acquisition.


## Declaration of competing interest
  The authors declare the following financial interests/personal relationships which may be considered as potential competing interests:

  Kai Wang reports financial support was provided by Shaanxi Provincial Department of Science and Technology. Kai Wang reports financial support was provided by Xi’an Municipal Health Commission. If there are other authors, they declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.


## Data availability
  All datasets analyzed in this study are publicly available. Single-cell RNA sequencing data can be downloaded from GEO under accession numbers GSE124310 and GSE278230. Bulk transcriptomic datasets are available under accession numbers GSE9782, GSE57317, and GSE6477. No new data were generated in this study.


## Funding
  This work was supported by the Shaanxi Provincial Department of Science and Technology (Grant No. 2023-YBSF-494) and the Xi’an Municipal Health Commission (Grant Nos. 2023yp29, 2024zp07, and 2024yb24).