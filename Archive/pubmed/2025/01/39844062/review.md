## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, conclusion, and supplementary information descriptions.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with Nature-style criteria. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors report the first genome-wide identification of 90 MATE and 14 ALMT genes in lentil, including phylogenetic classification, duplication analysis, promoter element prediction, structural modeling, and expression profiling of six selected genes under aluminum stress in tolerant versus sensitive genotypes.
- **Visible evidence base** Main text figures (Figs 1–7), supplementary figures (S1–S3), supplementary tables (S1–S7), and supplementary sequence files (S1–S3). No raw data files, alignment files, or statistical output tables were provided.
- **Missing materials affecting confidence** Raw qRT-PCR data with individual replicate values, statistical test outputs (exact p-values, error bars), accession numbers for all identified genes, multiple sequence alignment files, and validation of reference gene stability. The manuscript states statistical significance but does not provide effect sizes or confidence intervals.

## Reviewer
- **Overall assessment** This manuscript presents a descriptive genome-wide inventory of MATE and ALMT transporters in lentil, with some evolutionary and structural analyses. The work is competent but largely confirmatory, applying established bioinformatics pipelines to a new species. The expression data are limited to six genes and lack mechanistic validation. The claim that specific genes are involved in aluminum tolerance via citrate secretion is plausible but not experimentally demonstrated. The manuscript would benefit from functional validation or at least stronger correlative evidence linking expression to phenotype.
- **Who would be interested in the results, and why** Researchers working on aluminum tolerance in legumes, particularly those interested in MATE and ALMT transporter families. The gene inventory and phylogenetic placement will be useful for comparative genomics studies. Breeders targeting acid soil tolerance in lentil may find candidate genes for marker development. The study is of moderate interest to the plant abiotic stress community but is unlikely to attract broad interdisciplinary readership.
- **Major strengths** First genome-wide report of these families in lentil. Comprehensive bioinformatics analysis including duplication, collinearity, promoter elements, and structural modeling. Inclusion of two contrasting genotypes for expression analysis is appropriate. Clear writing and logical organization.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (expression data without statistical rigor), R1-M2 (functional claims without functional evidence), R1-M3 (phylogenetic classification not robustly supported).
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The approach is standard and has been applied to many species. The novelty is limited to the species choice.  
  - **Scientific importance** Low to moderate. Aluminum tolerance is agronomically relevant, but the study does not advance mechanistic understanding.  
  - **Interdisciplinary readership** Limited. The work is primarily of interest to plant molecular biologists and breeders.  
  - **Technical soundness** Generally acceptable for the bioinformatics components, but the expression analysis lacks statistical rigor and the structural predictions are not experimentally validated.  
  - **Readability for nonspecialists** The manuscript is readable but assumes familiarity with genomics terminology. Some figures are dense and would benefit from simplification.
- **Recommendation posture** Currently not established from the provided evidence. The descriptive genomics are acceptable, but the central claim regarding aluminum tolerance mechanisms is not supported by the data presented. Major revisions and additional experimental evidence are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that six genes responded to Al stress with varying expression patterns and that LcM46 showed significantly higher expression in the tolerant genotype at all time points.
- **Evidence pointer** Figure 7, Methods section "RNA extraction and qRT-PCR analysis", Statistical analyses section
- **Concern** The qRT-PCR data are presented as mean fold changes with only two significance thresholds indicated (p < 0.05 and p < 0.0001). No error bars are visible in Figure 7, no individual replicate data are shown, and no information is provided on the number of technical replicates, normalization strategy beyond using beta-tubulin, or validation of beta-tubulin stability under Al stress. The statistical test used is stated as Student's t-test, but it is unclear whether this was applied to delta-Ct values or fold changes, and whether multiple testing corrections were applied.
- **Why it matters** The expression data are the only experimental evidence in the manuscript. Without proper statistical reporting, the claim that specific genes are differentially expressed and therefore involved in Al tolerance cannot be evaluated. This is the core evidence for the paper's main conclusion.
- **Resolution test** Provide raw Ct values or at minimum mean fold changes with standard deviation/standard error for each biological replicate. State the number of biological and technical replicates. Validate reference gene stability under Al stress. Report exact p-values and specify whether multiple testing corrections were applied. Provide a clear description of the statistical model used.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors conclude that LcM42, LcM46, and other genes "might play a major role in aluminum detoxification" and that the study "will aid in valuable understanding for future functional studies of these transporters in generating Al tolerant cultivars."
- **Evidence pointer** Discussion section, Conclusion section, Figure 5, Figure 7
- **Concern** The conclusion that specific genes are involved in Al tolerance is based on (a) sequence similarity to known Al-tolerance genes, (b) presence of a citrate exuding motif, and (c) differential expression under Al stress. None of these provide direct evidence of function. The structural predictions are based on homology modeling without experimental validation. The expression data show correlation, not causation. No loss-of-function or gain-of-function experiments are presented.
- **Why it matters** The title and conclusion imply functional significance, but the data are purely descriptive. Overstating conclusions from in silico and correlative data is a common weakness in genomics papers and undermines the scientific value of the work.
- **Resolution test** Either temper the conclusions to match the descriptive nature of the data, or add functional validation such as heterologous expression, complementation in yeast or Arabidopsis mutants, or at minimum, measurement of organic acid exudation in lentil roots under Al stress.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that 90 MATE and 14 ALMT genes were identified and classified into four and five subfamilies/clades, respectively.
- **Evidence pointer** Methods section "Screening and identification", Figure 2, Supplementary Table S1
- **Concern** The phylogenetic analysis uses 33 known MATE and 29 known ALMT proteins from other species. The selection criteria for these reference sequences are not described. The bootstrap support values for key nodes are not reported in the text or figure. The classification into subfamilies appears to be based on the tree topology, but without bootstrap values, the robustness of the classification cannot be assessed. Additionally, the number of MATE genes (90) is unusually high compared to other species, and the authors do not discuss whether this could be due to redundant isoforms or assembly artifacts.
- **Why it matters** The subfamily classification is used to predict function. If the phylogenetic placement is not robust, the functional predictions are unreliable. The unusually high gene count also warrants discussion.
- **Resolution test** Report bootstrap values for major nodes in the phylogenetic trees. Describe the criteria for selecting reference sequences. Discuss the possibility of assembly artifacts or provide evidence that all 90 MATE genes are expressed or have intact open reading frames.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Chromosomal location, gene duplication and collinearity analysis"
- **Evidence pointer** Methods section
- **Issue** The criteria for defining tandem duplication are not stated. The authors mention "less than 10 gene loci apart" but do not specify whether this refers to physical distance or gene order. The threshold of 50% protein similarity is mentioned but not justified.
- **Required correction** Provide a clear definition of tandem duplication with reference to the method used. Justify the chosen thresholds.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Prediction of the cis-acting regulatory elements"
- **Evidence pointer** Methods section
- **Issue** The authors state that 2000 bp upstream regions were analyzed using PlantCARE, but no details are given on how the promoter regions were extracted from the genome assembly or whether the assembly annotation was used to define transcription start sites.
- **Required correction** Describe the source of the promoter sequences and the criteria for defining the upstream region.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 7
- **Evidence pointer** Figure 7
- **Issue** The figure lacks error bars and the significance markers are not defined in the legend. The y-axis label is "Relative expression" but the scale is not described.
- **Required correction** Add error bars, define significance markers in the legend, and describe the calculation of relative expression.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Identification of MATE and ALMT genes"
- **Evidence pointer** Results section
- **Issue** The authors report the number of genes per chromosome but do not provide a table or figure showing the distribution of gene lengths, exon counts, or other genomic features that would help validate the gene models.
- **Required correction** Consider adding a supplementary table with genomic coordinates, gene length, and exon count for all identified genes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** Several typographical errors and awkward phrasings are present, e.g., "confertolerance" in the Introduction, "demostrates" in the Discussion, "reducndancy" in the Discussion, "proeins" in the Discussion.
- **Required correction** Thorough language editing is needed.

## Risk / unsupported claims
- The claim that LcM42, LcM46, LcM47, LcM1, LcALMT8, and LcALMT14 are involved in Al tolerance is unsupported by direct functional evidence.
- The claim that LcM46 is a "potential gene for tolerance against Al toxicity" is based solely on expression correlation.
- The claim that the presence of a citrate exuding motif indicates citrate transport function is not validated experimentally.
- The statement that "tandem duplication played a major role in amplification of MATE family" is supported by the analysis but the functional consequences are speculative.
- The predicted subcellular localization of LcM42 (vacuole) versus LcM46 (plasma membrane) is based on in silico prediction and is not experimentally verified.
- The evolutionary divergence times (26.37 to 217.20 MYA) are based on a molecular clock assumption that is not described or justified.
- The claim that the study "will aid in valuable understanding for future functional studies" is reasonable but the current data do not establish a functional role for any specific gene.