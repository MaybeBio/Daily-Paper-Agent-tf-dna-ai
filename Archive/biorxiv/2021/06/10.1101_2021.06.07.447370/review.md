## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, declarations)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors present RBPSpot, a tool combining BWT/FM-index-based inexact k-mer seed discovery with a two-hidden-layer deep feed-forward neural network to predict RBP binding sites in human RNA. They claim high accuracy (~90%) across 131 RBPs, superiority over five existing tools including deep learning approaches, and support from molecular dynamics simulations.
- **Visible evidence base** Abstract, introduction, methods sections (data retrieval, motif discovery, dataset construction, feature generation, machine learning implementation, structural analysis), results sections (motif statistics, co-occurrence analysis, benchmarking, MD simulations), conclusion, declarations
- **Missing materials affecting confidence** Supplementary Data files (Sheets 1-15), Supplementary Figures 1-2, Table 1, specific performance metrics per RBP, hyperparameter details, code implementation details, exact dataset compositions

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in RBP binding site prediction and introduces a reasonable approach combining efficient k-mer search with contextual feature learning. The authors demonstrate awareness of key limitations in existing tools, particularly regarding negative dataset construction and contextual information. However, the manuscript has several significant issues that prevent full confidence in the claims. The benchmarking methodology has potential circularity concerns, the MD simulation section is underdeveloped and does not clearly connect to the predictive model validation, and critical implementation details are missing. The claim of outperforming "much complex deep-learning models" requires more careful statistical analysis and consideration of training conditions. The work is potentially valuable but requires substantial revision and additional validation before the claims can be considered established.

- **Who would be interested in the results, and why** Computational biologists working on RNA-protein interactions, bioinformaticians developing prediction tools for regulatory genomics, and experimental biologists studying post-transcriptional regulation would find this work relevant. The tool's ability to build custom models from user data is a practical feature. The emphasis on contextual information and careful negative dataset construction addresses a recognized gap in the field. The SARS-CoV-2 application, while preliminary, may attract attention from virology researchers.

- **Major strengths**
  1. The approach of using BWT/FM-index for ultrafast inexact k-mer search is computationally efficient and practical for genome-scale applications
  2. The careful attention to negative dataset construction, using expression-matched non-binding regions, is a methodological improvement over random negative selection
  3. The comprehensive benchmarking across three datasets and five tools is commendable in scope
  4. The finding of CG enrichment in flanking regions is an interesting biological observation that could have broader implications
  5. The tool's flexibility for building custom models is a practical advantage

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Benchmarking methodology
- **Claim pointer** "It clearly outperformed some recently developed tools, including some with much complex deep-learning models, during a highly comprehensive bench-marking process involving three different data-sets and more than 50 RBPs"
- **Evidence pointer** Results section "Comparative benchmarking", Figure 8, Figure 9
- **Concern** The benchmarking methodology has potential circularity. RBPSpot's models are trained on datasets derived from the same CLIP-seq data that define the positive instances. When testing on GraphProt and beRBP datasets, the authors do not clarify whether the RBPSpot models were retrained on those datasets or used as pre-trained models. If pre-trained models were used, the comparison is unfair because the other tools' models were trained on their respective datasets. If retrained, the comparison is more equitable but the claim of "outperforming" needs statistical significance testing that is not reported. Additionally, the threshold of 0.7 for DeepBind binary decisions is arbitrary and may disadvantage DeepBind.
- **Why it matters** The central claim of the manuscript is that RBPSpot outperforms existing tools. If the benchmarking is not methodologically sound, this claim is not established, undermining the primary contribution of the work.
- **Resolution test** Provide detailed benchmarking protocols: specify whether models were retrained for each dataset, report per-RBP performance with confidence intervals, perform paired statistical tests (e.g., Wilcoxon signed-rank) across RBPs for each tool comparison, and justify the DeepBind threshold choice.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / MD simulation validation
- **Claim pointer** "The developed models also got support from MD-simulation studies" and "Structural and molecular dynamics analysis supports the RBP binding site models"
- **Evidence pointer** Results section "Structural and molecular dynamics analysis", Figure 10, Table 1
- **Concern** The MD simulation section is severely underdeveloped. The authors state that RMSD analysis of 13 RBP-RNA complexes showed that sequences with the prime motif were more stable than those without, but provide no quantitative details: no RMSD values for most complexes, no statistical analysis comparing conditions, no information on simulation convergence, no error estimates. The example given for AGO2 is anecdotal. Furthermore, the connection between MD stability and predictive model validity is not clearly articulated. A stable complex in a 20 ns simulation does not necessarily validate that the predicted binding site is functionally relevant.
- **Why it matters** The MD simulations are presented as supporting evidence for the model's biological validity. Without rigorous quantitative analysis and clear logical connection to the predictive model, this support is not established.
- **Resolution test** Provide quantitative RMSD data for all 13 complexes with statistical comparison between conditions (e.g., mean RMSD ± SD, significance tests), include additional metrics such as RMSF or binding energy calculations, and explicitly articulate how MD stability relates to binding site validity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility / Methodological detail
- **Claim pointer** "The detailed algorithmic implementation pseudo-code of the implemented algorithm is given in the supplementary methods"
- **Evidence pointer** Methods section "Identification of motif seed candidates", Supplementary methods
- **Concern** The methods section lacks critical implementation details necessary for reproducibility. The DNN architecture description is incomplete: no information on dropout rates, batch normalization, learning rate schedules, early stopping criteria, or weight initialization strategies. The feature engineering process is described at a high level but the exact computation of pentamer/heptamer probability tensors is not fully specified. The threshold for "significant" k-mer enrichment is not defined. The recursive motif discovery process for mutually exclusive motifs is described vaguely. The supplementary methods are referenced but not provided in the manuscript.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publication. Without complete methodological detail, other researchers cannot implement or validate the approach.
- **Resolution test** Provide complete algorithmic descriptions, including all hyperparameters, feature computation formulas, threshold definitions, and the full pseudo-code in the main text or supplementary materials.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Biological interpretation
- **Claim pointer** "Contextual CG distribution pattern appeared important" and "Approximately 69% of RBPs target regions exhibited CG among the most dominant feature for each position"
- **Evidence pointer** Results section "Contextual information surrounding the anchored motif"
- **Concern** The biological interpretation of the CG enrichment finding is superficial. The authors note the observation but do not explore its mechanistic implications. CG dinucleotides are known to be underrepresented in eukaryotic genomes and are associated with CpG islands, DNA methylation, and RNA stability. The authors do not discuss whether the CG enrichment in RBP binding regions reflects a general property of RNA structure, a specific recognition element, or an artifact of the CLIP-seq data. No comparison is made to appropriate genomic background controls beyond the negative dataset.
- **Why it matters** The CG enrichment observation could be a significant biological finding, but without deeper analysis and interpretation, it remains an unexplained correlation. This limits the scientific importance of the work.
- **Resolution test** Provide additional analysis of CG enrichment: compare to genomic background, examine whether CG enrichment correlates with binding affinity or functional outcomes, discuss potential mechanistic roles, and relate to existing literature on CG-containing RNA motifs.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Dataset quality
- **Claim pointer** "This way a total of 52 RBP data were used from RBPSpot dataset for the comparison purpose"
- **Evidence pointer** Methods section "Datasets creation", Results section "Comparative benchmarking"
- **Concern** The dataset construction for benchmarking is not fully described. The authors state that 52 RBPs were used from the RBPSpot dataset for comparison, but do not specify which RBPs were excluded and why. The criteria for inclusion in the benchmarking (at least one other tool having a model) may introduce selection bias. Additionally, the negative dataset construction for the GraphProt and beRBP datasets is not described in detail, and it is unclear whether the authors used the original negative datasets or constructed new ones.
- **Why it matters** Dataset composition directly affects benchmarking outcomes. Selection bias in which RBPs are compared could inflate or deflate performance estimates.
- **Resolution test** Provide complete lists of RBPs used for each comparison, justify inclusion/exclusion criteria, and describe the negative dataset construction for all three benchmarking datasets.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Writing
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "average accuracy of ∼90%" but does not specify whether this is across all 131 RBPs or only a subset. The abstract also does not mention the number of RBPs used for benchmarking.
- **Required correction** Specify the exact number of RBPs and the range of accuracy values in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness / Statistical reporting
- **Affected element** Performance metrics
- **Evidence pointer** Results section "DNN implementation", Figure 6, Figure 7
- **Issue** The manuscript reports accuracy, AUC, F1-score, and MCC but does not report confidence intervals or variance measures for these metrics. The violin plots in Figure 6 show distributions but no numerical summary statistics are provided in the text.
- **Required correction** Report mean ± standard deviation or confidence intervals for all performance metrics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity / Terminology
- **Affected element** Methods section
- **Evidence pointer** Methods section "Identification of motif seed candidates"
- **Issue** The term "relatives" for k-mers with 70% similarity is not formally defined. It is unclear whether this refers to Hamming distance, Levenshtein distance, or some other similarity measure.
- **Required correction** Define the similarity measure explicitly and provide the exact matching criteria.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness / Feature selection
- **Affected element** Feature engineering
- **Evidence pointer** Methods section "Feature generation"
- **Issue** The manuscript states that features were evaluated for discrimination power but does not describe the feature selection methodology. It is unclear whether all features were used or a subset was selected.
- **Required correction** Describe the feature selection process, including any ranking or filtering criteria.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity / Figure quality
- **Affected element** Figure 10
- **Evidence pointer** Results section "Structural and molecular dynamics analysis"
- **Issue** The RMSD plots in Figure 10 are described but not shown in the manuscript text. The figure is referenced but its content is not described in sufficient detail.
- **Required correction** Provide a clear description of what is shown in Figure 10, including axis labels, conditions compared, and the number of replicates.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness / Model comparison
- **Affected element** Benchmarking
- **Evidence pointer** Results section "Comparative benchmarking"
- **Issue** The manuscript does not describe the computational resources or runtime for RBPSpot compared to the other tools. The claim of "ultra-fast" performance is not quantified.
- **Required correction** Report runtime and resource usage for RBPSpot and compared tools.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity / Availability
- **Affected element** Software availability
- **Evidence pointer** Declarations section
- **Issue** The manuscript states the software is available at a webserver and GitHub, but does not specify the license, version, or system requirements.
- **Required correction** Provide license information, version number, and system requirements for the software.

## Risk / unsupported claims
1. The claim that RBPSpot "clearly outperformed" all compared tools is not statistically substantiated; no significance testing is reported.
2. The MD simulation support for the models is not quantitatively established; only anecdotal evidence is provided.
3. The claim of "ultra-fast" performance is not quantified with runtime comparisons.
4. The statement that "approximately 69% of RBPs target regions exhibited CG among the most dominant feature" is presented without statistical context or comparison to appropriate controls.
5. The claim that the tool covers "most of the human RBPs for which sufficient CLIP-seq data is available (131 RBPs)" is not verifiable without a list of the RBPs and the criteria for "sufficient" data.
6. The SARS-CoV-2 application is presented as potentially having "therapeutic value," but no functional validation or experimental evidence is provided to support this claim.
7. The statement that simpler models "can outperform" complex deep-learning models is presented as a general conclusion from this work, but the evidence is limited to the specific datasets and RBPs tested.