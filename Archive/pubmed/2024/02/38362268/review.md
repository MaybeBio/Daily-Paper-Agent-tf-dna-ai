## Review setup
- **Input scope** Full manuscript text (Summary, Introduction, Results, Discussion, STAR Methods) as provided
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and evidence as presented in the supplied text; no external data or code was accessed
- **Shared manuscript claim summary** The authors present Graphylo, a deep learning model combining convolutional neural networks (CNNs) and graph convolutional networks (GCNs) operating on whole-genome multiple sequence alignments from 58 placental mammals plus inferred ancestral sequences, to predict transcription factor binding sites (TFBS) and RNA binding protein (RBP) sites in the human genome. They claim consistent outperformance over single-species deep learning baselines and conservation-score-augmented methods across 13 ENCODE DREAM TF datasets and 31 RBP datasets, with interpretability via species attention weights and integrated gradients.
- **Visible evidence base** Results section with performance comparisons (Figures 2-6), attention weight analysis (Figure 7), genome browser comparisons (Figure 8), integrated gradients (Figure 9), running time metrics, and method descriptions in STAR Methods
- **Missing materials affecting confidence** Actual figures and figure legends were not provided; exact numerical results per dataset are not fully tabulated; hyperparameter grid search details are incomplete; no ablation studies are described; code was not inspected; statistical test details are partially reported

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in regulatory genomics: improving TFBS prediction by leveraging evolutionary information from multiple alignments in a phylogenetically informed manner. The core idea of combining CNNs with GCNs over a phylogenetic tree is conceptually sound and, to my knowledge, novel in this application domain. The reported performance gains are plausible and the interpretability analyses are a welcome addition. However, the evidence as presented has several gaps that prevent full confidence in the claims. The lack of actual figures, incomplete methodological details, and absence of ablation studies or uncertainty quantification limit the strength of the conclusions. The running time analysis reveals a practical scalability concern that is acknowledged but not fully addressed. Overall, the work is promising and likely of interest to the computational genomics community, but the current evidence base is insufficient to fully establish the superiority claims.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, TFBS prediction, and deep learning applications to genomics would be the primary audience. Researchers developing methods that integrate evolutionary information into predictive models would find the GCN-over-phylogeny approach of particular interest. The interpretability analyses (attention weights, integrated gradients) may also appeal to those studying model interpretability in genomics. The work could also be relevant to researchers studying regulatory evolution and sequence conservation.

- **Major strengths**
  1. The conceptual novelty of applying GCNs over a phylogenetic tree to integrate evolutionary information for TFBS prediction is a genuine contribution. This goes beyond simple conservation scores and allows the model to learn how information flows across evolutionary relationships.
  2. The use of both extant and inferred ancestral sequences is thoughtful, and the finding that attention focuses on leaves rather than internal nodes is an interesting empirical observation with implications for model design.
  3. The evaluation across multiple benchmark datasets (ENCODE DREAM TF, RBP CLIP) provides breadth, and the comparison against several baselines including conservation-augmented versions is appropriate.
  4. The interpretability analyses (attention weights, integrated gradients) are valuable and go beyond typical black-box reporting.
  5. The manuscript is generally well-written and the biological rationale is clearly explained.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** "Graphylo outperforms all baseline predictors on 9 of the 13 different TF/cell-type pairs introduced in the DREAM challenge and 29 of the 31 different RBP binding datasets"
- **Evidence pointer** Figures 2, 3, 5; location not provided for per-dataset numerical values
- **Concern** The central performance claim is presented through figures that were not provided in the manuscript text. While aggregate statistics (Wilcoxon p-values) are given, the per-dataset results are not tabulated. This makes it impossible to assess the magnitude and consistency of improvements, identify potential failure cases, or evaluate whether the gains are concentrated in specific TF families or cell types. The claim of "consistent outperformance" cannot be fully verified without the underlying data.
- **Why it matters** The primary contribution of the paper is the claimed performance improvement. Without access to the detailed results, the reader cannot evaluate the robustness of the finding, nor can they assess whether the improvement is practically meaningful or only marginal in specific cases.
- **Resolution test** Provide a supplementary table with per-dataset AUPR/AUROC values for all models compared, including standard deviations or confidence intervals. This would allow verification of the aggregate claims and assessment of consistency across datasets.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** "We performed a grid search on realistic values for each hyperparameter and settled down with 32 CNN filters of the size of (6×11), 32 for the hidden weight size of GCN, and 64 perceptrons for the fully connected layer."
- **Evidence pointer** STAR Methods, Training Graphylo section
- **Concern** The hyperparameter search is described only in a single sentence. The range of values tested, the selection criterion, and whether the same hyperparameters were used across all datasets are not specified. More critically, there is no ablation study isolating the contribution of the GCN component versus the CNN backbone, nor an analysis of how sensitive results are to the number of GCN layers, the attention mechanism, or the choice of species included. Without such analyses, it is unclear whether the performance gains come from the phylogenetic integration or from other architectural choices.
- **Why it matters** The paper's central claim is that phylogenetic integration via GCNs improves prediction. Without ablations, alternative explanations (e.g., the specific CNN architecture, the use of ancestral sequences, or the attention mechanism) cannot be ruled out. This weakens the causal interpretation of the results.
- **Resolution test** Add an ablation study that removes or modifies key components: (1) GCN removed (CNN only on human sequence), (2) GCN replaced with simple concatenation of conservation scores, (3) attention mechanism removed, (4) ancestral sequences excluded. Report performance for each variant across a subset of datasets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** "Graphylo outperforms all baseline predictors on 9 of the 13 different TF/cell-type pairs... with Wilcoxon signed-rank test p value of 1.81×10−2 and 3.54×10−6, against the second-best predictor for TF prediction (FactorNet+PhastCons) and RBP binding prediction (DeepA-RBPBS), respectively."
- **Evidence pointer** Results, Predictive performance section
- **Concern** The Wilcoxon signed-rank test is appropriate for paired comparisons, but the manuscript does not report whether the test was one-sided or two-sided, nor whether multiple testing correction was applied across the multiple comparisons performed (13 TF datasets, 31 RBP datasets, multiple baselines). Additionally, the p-value for the TF comparison (1.81×10−2) is not particularly small, and with only 13 paired observations, the power of the test is limited. The manuscript also does not report effect sizes or confidence intervals for the improvements.
- **Why it matters** The statistical evidence supporting the superiority claim is central. Without proper reporting of test details and effect sizes, the reader cannot assess the strength of the evidence, and the borderline p-value for the TF comparison raises questions about the robustness of the finding.
- **Resolution test** Report one-sided versus two-sided test specification, apply multiple testing correction across all comparisons, and provide effect sizes (e.g., median improvement with interquartile range) alongside p-values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Practical applicability
- **Claim pointer** "In terms of inference, predicting transcription factor binding on a single human region of 201 nucleotides takes approximately 20 ms. To make genome-wide predictions with a 50 bp stride, it would take approximately 334 h or 14 days using the same GPU."
- **Evidence pointer** Results, Running time section
- **Concern** The reported inference time of 14 days for genome-wide predictions is a substantial practical limitation. The authors acknowledge this in the Discussion but do not propose concrete solutions or demonstrate that the model can be made more efficient. This raises questions about the practical utility of the method for real-world applications, where researchers may need to score millions of candidate regions.
- **Why it matters** If the method is too slow for practical use, its impact will be limited regardless of predictive accuracy. The manuscript should either demonstrate ways to mitigate this (e.g., batch processing, GPU optimization, reduced species sets) or provide a clearer discussion of the trade-offs.
- **Resolution test** Provide benchmarks with optimized inference (e.g., larger batch sizes, mixed precision) and discuss potential speedups. Alternatively, demonstrate that a reduced set of species (e.g., 10-15 key species) achieves comparable performance, which would substantially reduce computational cost.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability validation
- **Claim pointer** "The attention weights allow for the relative importance of different species to be determined... Although Graphylo is not 'told' that its goal is to make a prediction that pertains to the human sequence, it learns to assign the highest attention to that sequence (and to the human-chimp ancestral sequence, which is nearly identical)."
- **Evidence pointer** Results, Species attention weights section, Figure 7
- **Concern** The attention weight analysis is descriptive. The manuscript does not validate whether the learned attention weights correlate with any external measure of species relevance (e.g., evolutionary distance, sequence conservation, or known functional importance). The claim that the model "learns" to focus on human is interesting, but without quantitative validation, it remains an observation rather than a demonstrated property. Additionally, the integrated gradients analysis is presented for only two examples (Figure 9), which is insufficient to draw general conclusions about model behavior.
- **Why it matters** The interpretability analyses are presented as a strength of the approach. However, without validation, they risk being anecdotal. The claim that attention weights provide "insights into the role played by different species" needs quantitative support.
- **Resolution test** Correlate attention weights with evolutionary distance from human or with per-species conservation scores across all datasets. For integrated gradients, provide a quantitative summary across multiple examples (e.g., frequency of motif matches in high-attribution regions).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2B description
- **Evidence pointer** Results, Predictive performance section
- **Issue** The text states "Performance (area under the precision-recall curve) gain of Graphylo compared with the FactorNet+PhastCons model on 124 dataset" but the figure legend is not provided. It is unclear whether this panel shows per-dataset gains as a scatter or bar plot, and what the "124 dataset" refers to exactly (the balanced set described later).
- **Required correction** Clarify the figure description and ensure the legend explicitly states what is plotted, the number of datasets, and the metric used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data preprocessing, alignment refinement
- **Evidence pointer** STAR Methods, Alignment refinement section
- **Issue** The alignment refinement step removes sequences with more than 2 gaps per 201 bp. The manuscript does not report how many sequences were removed on average across the datasets, nor whether this filtering was applied consistently across all species and genomic regions.
- **Required correction** Report the fraction of removed sequences and discuss potential biases introduced by this filtering step.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Baseline descriptions
- **Evidence pointer** STAR Methods, Baseline models section
- **Issue** The description of the FactorNet variant with PhastCons scores states that "we set all DNase-Seq values to zero" for the original model, but it is unclear whether the PhastCons-augmented version replaces DNase-Seq entirely or concatenates both inputs. The exact input representation for each baseline should be specified.
- **Required correction** Provide a clear specification of input features for each baseline model variant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 4 description
- **Evidence pointer** Results, Predictive performance section
- **Issue** The text describes "mean relative percentage improvement of Graphylo test recall score over FactorNet+PhastCons for 17 different false discovery rate thresholds" but does not explain how these 17 thresholds were chosen or whether they are evenly spaced.
- **Required correction** Specify the FDR thresholds used and the rationale for their selection.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Discussion of attention patterns
- **Evidence pointer** Results, Species attention weights section
- **Issue** The three distinct attention patterns are described but not interpreted biologically. For example, what does it mean when attention is spread across the entire tree versus focused on human? Is there a relationship with TF binding specificity or evolutionary conservation of the TF motif?
- **Required correction** Add a brief discussion of the potential biological meaning of the different attention patterns.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Integrated gradients computation
- **Evidence pointer** STAR Methods, Interpretation of GraphQL predictions section
- **Issue** The baseline for integrated gradients is set to zero, but for one-hot encoded DNA sequences, a zero vector is not a valid biological sequence. The choice of baseline may affect the attribution results.
- **Required correction** Justify the choice of zero baseline or discuss alternative baselines (e.g., uniform distribution over nucleotides) and their potential impact.

## Risk / unsupported claims
- The claim that Graphylo is "the first deep learning predictor to utilize multiple DNA sequence alignments for TF prediction" is a strong novelty claim that cannot be fully verified from the provided text alone, as the authors do not provide a comprehensive literature comparison.
- The statement that "Graphylo consistently outperforms both single-species deep learning techniques and methods that incorporate inter-species conservation scores" is not fully supported without per-dataset results and effect sizes.
- The biological interpretation of the CEBPB-HepG2 versus CEBPB-HCT116 integrated gradients differences (heterodimer recognition in cancer cells) is speculative and based on two examples only.
- The claim that attention weights "allow for the relative importance of different species to be determined" implies a causal interpretation that is not validated.
- The practical utility of the method is questionable given the reported inference time of 14 days for genome-wide predictions, and this limitation is not adequately addressed.