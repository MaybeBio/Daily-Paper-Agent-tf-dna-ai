## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information descriptions.
- **Assessment boundary** Scientific content, technical soundness, data interpretation, and claims as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors map GLK transcription factor binding by ChIP-seq in five plant species (Arabidopsis, tomato, tobacco, rice, maize) and report that most binding sites are species-specific, with conserved sites enriched near photosynthesis genes and under purifying selection. They further use machine learning to predict regulatory potential and argue that cis-variation drives cistrome divergence, with many binding sites being genetically redundant.
- **Visible evidence base** ChIP-seq data for GLK1/2 in five species, RNA-seq for Arabidopsis and tomato glk mutants, ATAC-seq data, DAP-seq co-binding data, machine learning models (k-mer grammar and random forest), synteny and Ks analyses, nucleotide diversity analysis using 1001 genomes data.
- **Missing materials affecting confidence** Supplementary Data files 1–13, Supplementary Figures 1–10, and Supplementary Tables 1–3 are referenced but not provided. Specific statistical test details, peak calling parameters beyond those stated, and raw data quality metrics are not fully assessable.

## Reviewer
- **Overall assessment** This manuscript addresses an important and underexplored question in plant regulatory genomics: the evolutionary dynamics of TF binding across species. The experimental design, spanning five species with conserved TF function, is ambitious and appropriate. The central finding, that most GLK binding sites are species-specific despite conserved function, aligns with observations in animals and yeast and is of broad interest. However, the strength of the conclusions depends heavily on the comparability of ChIP-seq data across species generated under different expression systems (stable vs. transient, native vs. overexpressed), which is a significant technical concern. The machine learning and selection analyses are valuable but require more rigorous validation and clearer presentation of limitations. Overall, the manuscript is potentially important but currently does not fully establish its case from the provided evidence.
- **Who would be interested in the results, and why** Plant molecular biologists studying transcriptional regulation, particularly those working on photosynthesis gene regulation and GOLDEN2-LIKE factors. Evolutionary genomicists interested in cis-regulatory evolution and cistrome dynamics across eukaryotes. Researchers developing machine learning approaches for predicting TF binding and regulatory outcomes. The findings on binding site redundancy and purifying selection have implications for interpreting non-coding variants in crop genomes.
- **Major strengths** 1) The cross-species design is a significant strength, addressing a question rarely tackled in plants with this breadth. 2) The combination of ChIP-seq, RNA-seq, population genetics, and machine learning provides a multi-faceted view. 3) The demonstration that conserved binding sites have stronger regulatory potential and are under purifying selection is a compelling and important result. 4) The heterologous expression experiment (maize GLK1 in Arabidopsis) is an elegant test of cis vs. trans determinants of binding. 5) The manuscript is generally clearly written and accessible to a broad audience.
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
  - R1-m5
  - R1-m6
- **Technical failings that need to be addressed before the case is established** R1-M1 (comparability of ChIP-seq data), R1-M2 (definition of conservation and peak calling thresholds), R1-M3 (machine learning model validation and interpretation).
- **Assessment against Nature-style criteria** **Originality**: High. This is among the first multi-species TF binding comparisons in plants and directly tests evolutionary models developed in animals. **Scientific importance**: High. The findings challenge assumptions about conserved TF function implying conserved binding and have implications for understanding regulatory evolution and crop improvement. **Interdisciplinary readership**: Moderate to high. The topic bridges plant biology, evolutionary genomics, and computational biology, and the findings are relevant to broader questions of cis-regulatory evolution. **Technical soundness**: Moderate. The core ChIP-seq and RNA-seq approaches are standard, but the cross-species comparability issue is a major technical weakness that is not fully addressed. The machine learning analyses are appropriate but need more rigorous validation. **Readability for nonspecialists**: Good. The manuscript is well-structured and explains concepts clearly, though some sections (e.g., machine learning details) may be dense for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding cross-species ChIP-seq comparability and the robustness of the conservation analysis. The core question is important and the data are potentially valuable, but the current evidence does not fully exclude alternative explanations (e.g., technical artifacts driving apparent divergence).

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Data comparability
- **Claim pointer** The authors claim that "most of their binding sites are species-specific" based on ChIP-seq comparisons across five species.
- **Evidence pointer** Results section "Most GLK ChIP-seq target genes are species-specific"; Methods section "ChIP-seq"
- **Concern** The ChIP-seq data were generated under fundamentally different conditions across species: stable transgenic overexpression with different tags (GFP vs. HA) in Arabidopsis, rice, and tomato; transient overexpression via agroinfiltration in tobacco; and published data from a previous study in maize. Overexpression levels, tissue types (leaf vs. fruit), and developmental stages vary. These differences could substantially affect peak calling sensitivity and specificity, potentially creating artifactual species-specific binding or masking true conserved binding. The authors do not provide a rigorous assessment of how these technical variables might influence the cross-species comparison.
- **Why it matters** The central conclusion of widespread cistrome divergence rests entirely on the comparability of ChIP-seq data across species. If technical differences (e.g., lower sensitivity in one species) drive the apparent lack of conservation, the biological conclusion would be substantially weakened. This is a known and serious issue in cross-species ChIP-seq comparisons.
- **Resolution test** The authors should provide a detailed comparison of ChIP-seq quality metrics across all datasets (e.g., FRiP scores, number of peaks, peak width distributions, signal-to-noise ratios). They should perform a spike-in normalization or equivalent approach to calibrate binding strength across species. Ideally, they should validate a subset of species-specific and conserved binding sites by an orthogonal method (e.g., electrophoretic mobility shift assay or reporter assays) in at least two species. They should also demonstrate that the conservation analysis is robust when using matched analysis pipelines and thresholds, and ideally when downsampling data to equal sequencing depth.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation / Conservation definition
- **Claim pointer** The authors claim that "Conserved binding sites are often found near photosynthetic genes dependent on GLK for expression, but sites near non-differentially expressed genes in the glk mutant are nevertheless under purifying selection."
- **Evidence pointer** Results sections "Conserved GLK targets in photosynthesis-related processes" and "GLK binding sites in non-DEGs are also under negative selection"; Figure 5
- **Concern** The definition of "conserved" binding sites relies on orthologous gene assignment and peak overlap, but the criteria for conservation are not fully described. Specifically, it is unclear how peak overlap is determined across species with different genome sizes, promoter lengths, and gene densities. The statement that non-DEG binding sites are under purifying selection is based on nucleotide diversity analysis, but the comparison groups (conserved vs. non-conserved; DEG vs. non-DEG) may be confounded by genomic features such as GC content, recombination rate, or proximity to coding sequence. The statistical approach for the selection analysis is not fully detailed.
- **Why it matters** The interpretation that conserved sites are functional and non-conserved sites are redundant or neutral depends critically on how conservation is defined and how selection is measured. If the conservation definition is too stringent or biased, the conclusions about functional importance could be incorrect. The purifying selection result for non-DEG sites is a key and somewhat counterintuitive finding that needs robust support.
- **Resolution test** The authors should clearly define the conservation criteria, including the exact peak overlap rules and orthology assignment methods. They should perform sensitivity analyses using different conservation thresholds and show that the conclusions hold. For the selection analysis, they should control for potential confounders (e.g., by matching conserved and non-conserved sites for GC content, distance to TSS, and recombination rate) and provide full details of the statistical tests used. They should also consider using a more direct measure of selection, such as dN/dS or a phylogenetic footprinting approach.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Machine learning
- **Claim pointer** The authors claim that "The binding sites' regulatory potential can be predicted by machine learning model using quantitative genome features and TF co-binding information."
- **Evidence pointer** Results section "Use of machine learning model to predict transcription outcome"; Figure 7
- **Concern** The random forest model is trained to distinguish DEGs from non-DEGs among GLK target genes, but the number of DEGs is small (202 in Arabidopsis). The model uses features including ChIP-seq signal, distance to TSS, expression level, and DAP-seq co-binding. The validation approach (500 random train/test splits) is reasonable, but the reported performance metrics (AUC 0.77) may be optimistic given the small sample size and the potential for overfitting. The feature importance analysis is descriptive and does not establish causality. The model is only applied to Arabidopsis, so its generalizability to other species is untested.
- **Why it matters** The machine learning model is presented as a tool to interpret the regulatory code and predict which binding sites matter. If the model is overfitted or not generalizable, this claim is weakened. The finding that co-binding information is important is interesting but needs more rigorous validation to be convincing.
- **Resolution test** The authors should use cross-validation or a nested cross-validation approach to obtain more reliable performance estimates. They should test the model's generalizability by training on one species and testing on another (e.g., train on Arabidopsis, test on tomato). They should also compare the random forest model to simpler baseline models (e.g., logistic regression using only ChIP-seq signal) to demonstrate the added value of the complex features. Feature importance should be validated by permutation tests or similar approaches.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data interpretation / Causal inference
- **Claim pointer** The authors state that "genome cis-variation caused wide-spread TF binding divergence" based on the heterologous expression experiment.
- **Evidence pointer** Results section "Cistrome dynamics and TF-binding divergence"; Figure 6
- **Concern** The heterologous expression experiment (maize GLK1 in Arabidopsis) is a clever approach, but the interpretation that binding is "largely determined in cis" is based on the observation that maize GLK1 recapitulates Arabidopsis GLK binding patterns. However, this experiment only tests one direction (maize TF in Arabidopsis genome). It does not test the reciprocal experiment (Arabidopsis GLK in maize genome), which would be needed to fully separate cis and trans effects. Additionally, the maize GLK1 protein may have different intrinsic binding preferences or affinities that could confound the interpretation.
- **Why it matters** The conclusion about cis vs. trans determinants is important for understanding the mechanisms of cistrome evolution. A one-directional experiment is insufficient to make a strong claim about the relative contributions of cis and trans variation.
- **Resolution test** The authors should either perform the reciprocal experiment (Arabidopsis GLK in maize) or clearly acknowledge this limitation and temper their conclusion. They should also compare the binding motifs of maize and Arabidopsis GLKs to rule out differences in intrinsic binding preferences. If the reciprocal experiment is not feasible, the claim should be revised to state that cis-variation is sufficient to explain the observed divergence in this context, rather than claiming it is the cause.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Evolutionary analysis
- **Claim pointer** The authors claim that "sites near non-differentially expressed genes in the glk mutant are nevertheless under purifying selection."
- **Evidence pointer** Results section "GLK binding sites in non-DEGs are also under negative selection"; Figure 5d–f
- **Concern** The nucleotide diversity analysis uses Arabidopsis 1001 genomes data, but the analysis is limited to Arabidopsis. The comparison between conserved and non-conserved sites is based on cross-species conservation, but the selection analysis is only performed in one species. This is a reasonable approach, but the interpretation that purifying selection indicates functionality is indirect. The authors do not discuss the possibility that the observed reduced diversity could be due to linked selection or demographic effects rather than direct purifying selection on the binding site.
- **Why it matters** The claim that non-DEG binding sites are functional and under selection is important because it challenges the simple view that only differentially expressed targets matter. If the selection signal is confounded, this conclusion is weakened.
- **Resolution test** The authors should provide more detail on the nucleotide diversity calculation, including how the background was defined and whether the analysis was corrected for multiple testing. They should consider using a population genetic model to distinguish direct selection from linked selection. They could also test whether the signal is specific to GLK binding sites by comparing to matched control sites that are not bound by GLK.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract begins with a statement about animal genomes, which may give the impression that the study is primarily about animals. The relevance to plants is only introduced later.
- **Required correction** Consider rephrasing the opening to directly frame the plant-focused question, while still acknowledging the animal literature as motivation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail / Methods
- **Affected element** Methods section "ChIP-seq"
- **Evidence pointer** Methods, "ChIP-seq" paragraph
- **Issue** The description of the ChIP-seq library preparation mentions "TS-Tn5" but does not explain what this is or provide a reference. This is a non-standard term that may confuse readers.
- **Required correction** Define TS-Tn5 or replace with a more standard description of the tagmentation-based library preparation method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation / Statistics
- **Affected element** Figure 5b
- **Evidence pointer** Figure 5b legend
- **Issue** The figure legend states "Kruskal test" but does not specify whether this is a one-sided or two-sided test, nor does it provide the number of comparisons or the correction method used.
- **Required correction** Provide full statistical details in the figure legend or methods, including the test type, sample sizes, and multiple testing correction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity / Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The discussion of "genetically redundant" binding sites is somewhat vague. The authors could more clearly define what they mean by redundancy and how it relates to the observed purifying selection.
- **Required correction** Clarify the concept of redundancy in this context and discuss how purifying selection can act on sites that are not individually essential for gene expression.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail / Data availability
- **Affected element** Methods section "ChIP-seq data analyses"
- **Evidence pointer** Methods, "ChIP-seq data analyses" paragraph
- **Issue** The authors state that "the ENCODE2 ChIP-seq pipeline with MACS2 and IDR" was used, but do not provide version numbers for all tools or the specific parameters used for IDR beyond the NSC/RSC/FRiP thresholds.
- **Required correction** Provide complete software versions and parameters, or a link to a public repository where the pipeline configuration is available.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data presentation / Completeness
- **Affected element** Results section "Genome-wide identification of GLK binding"
- **Evidence pointer** Results, first paragraph
- **Issue** The number of peaks identified per species is not stated in the main text. This information is critical for evaluating the comparability of the datasets.
- **Required correction** Report the number of peaks identified for each species in the main text or in a supplementary table.

## Risk / unsupported claims
- The claim that "most of the TF binding sites are genetically redundant" is not directly supported by the data presented. The authors show that many binding sites are not associated with differential expression, but this does not demonstrate redundancy, as these sites could have functions in other conditions or tissues.
- The claim that "genome cis-variation caused wide-spread TF binding divergence" is only partially supported, as the heterologous expression experiment is one-directional and does not rule out trans effects.
- The statement that "conserved binding sites are often found near photosynthetic genes dependent on GLK for expression" is supported, but the quantitative extent of this enrichment is not fully reported.
- The prediction accuracy of the machine learning model (AUC 0.77) is presented without confidence intervals or comparison to a null model, making it difficult to assess its significance.
- The purifying selection analysis is limited to Arabidopsis and may not be generalizable to other species.