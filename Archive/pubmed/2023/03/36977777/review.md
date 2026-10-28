## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Conclusion, Methods, selected references)
- **Assessment boundary** Scientific soundness, logical consistency, and support of claims by presented data; no assessment of editorial fit or journal-specific scope
- **Shared manuscript claim summary** The authors characterize early cellular events and potential transcriptional regulators of cellulase induction in *Penicillium janthinellum* NCIM 1366 by integrating secretome profiling, transcriptome analysis, promoter motif analysis, and enzyme activity measurements across multiple carbon sources.
- **Visible evidence base** Figures 1–5, Tables 1–5, Supplementary Files 1–6, Methods section
- **Missing materials affecting confidence** Raw RNA-seq data, differential expression statistics, quality metrics for transcriptome assembly, LC-MS/MS spectral counts, statistical tests for enzyme activity comparisons, full promoter sequences, and validation experiments for TF binding predictions

## Reviewer
- **Overall assessment** The manuscript presents a descriptive multi-omics survey of cellulase induction in a lesser-studied fungal strain. The integration of secretome and transcriptome data with promoter motif analysis is a reasonable exploratory approach. However, the study is largely correlative, and several key claims are not adequately supported by the evidence presented. The absence of statistical rigor in transcriptome analysis, the lack of functional validation for predicted regulators, and the speculative interpretation of docking and correlation results substantially weaken the conclusions. The work may serve as a useful resource for the community, but the central claims regarding regulatory mechanisms are not established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in fungal biotechnology, particularly those working on cellulase production and regulation in *Penicillium* species, would find the secretome and transcriptome datasets useful as a reference. The identification of candidate transcription factors and the observation of glucose-tolerant BGL activity may also interest groups focused on industrial enzyme improvement. However, the lack of mechanistic validation limits broader appeal.
- **Major strengths**
  - The study addresses a relevant and under-explored organism for cellulase production, providing new genomic and proteomic context for *P. janthinellum*.
  - The multi-omics approach (transcriptome, secretome, promoter analysis) is integrative and provides a broad dataset that could generate hypotheses for future work.
  - The observation of glucose-tolerant BGL activity and the docking-based explanation for reduced feedback inhibition is an interesting and potentially useful finding for industrial applications.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor and data support
  - **Claim pointer** The authors claim that 758 transcription factors were differentially expressed on cellulose induction, and that 13 TFs were identified whose binding site frequencies positively correlate with cellulase abundance in the secretome.
  - **Evidence pointer** Results section "Overview of TFs and pathways regulating cellulase expression"; Table 5; Figure 4; Methods "Transcriptome profiling"
  - **Concern** The transcriptome analysis is described without any statistical framework. No thresholds for differential expression (e.g., fold change cutoff, adjusted p-value, FDR) are provided. The claim of "differentially expressed" is therefore not verifiable. Furthermore, the correlation analysis between TF binding site frequency and protein abundance appears to be based on a small number of data points (13 cellulases) without any reported correlation coefficients, confidence intervals, or significance testing. The correlation values in Figure 4 are presented without statistical support.
  - **Why it matters** Without statistical rigor, the central claim identifying potential regulators is unsupported. The reader cannot assess whether the observed correlations are meaningful or due to chance. This undermines the main conclusion of the manuscript.
  - **Resolution test** Provide complete differential expression analysis with defined thresholds and adjusted p-values. Report correlation coefficients with p-values or confidence intervals for the TF binding site versus abundance analysis. If sample sizes are too small for robust correlation, state this limitation explicitly and temper the claims accordingly.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional validation
  - **Claim pointer** The authors state that "cellulase expression is possibly preceded by up-regulation of 12 TFs and down-regulation of 16 TFs, which cumulatively regulate transcription, translation, nutrient metabolism and stress response."
  - **Evidence pointer** Results section "Overview of TFs and pathways regulating cellulase expression"; Figure 5; Supplementary File 6
  - **Concern** The manuscript identifies candidate TFs based on promoter binding site predictions and transcriptomic correlation, but provides no functional validation. There are no knockout, knockdown, or overexpression experiments, no electrophoretic mobility shift assays, no chromatin immunoprecipitation, and no reporter assays to confirm that any of the predicted TFs actually bind these promoters or regulate cellulase expression. The pathway assignments are purely speculative.
  - **Why it matters** The title and abstract promise "potential regulators of cellulase induction," but the evidence presented is entirely correlative and predictive. Without any functional data, the claim that these TFs "regulate" cellulase expression is not supported. The manuscript overreaches in its conclusions.
  - **Resolution test** Either add functional validation for at least the top candidate TFs, or substantially revise the language to clearly frame these as hypotheses requiring experimental testing. The term "regulators" should be replaced with "candidate regulators" throughout.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Data availability and reproducibility
  - **Claim pointer** The authors present transcriptome and secretome data as central evidence for their conclusions.
  - **Evidence pointer** Methods "Transcriptome profiling" and "Secretome profiling"
  - **Concern** Raw RNA-seq data, processed count matrices, and differential expression results are not provided or referenced with accession numbers. Similarly, LC-MS/MS raw data and spectral count tables are not provided. The Methods section lacks critical details: sequencing platform, read length, depth, quality filtering parameters, reference assembly version, and the statistical method for identifying differentially expressed genes. For the secretome, no details on protein identification thresholds, false discovery rates, or quantification methods are given.
  - **Why it matters** Reproducibility is a fundamental requirement for scientific publication. Without access to the underlying data and detailed methods, other researchers cannot verify or build upon these findings. This is particularly important given that the study's conclusions rest entirely on these datasets.
  - **Resolution test** Deposit raw and processed data in appropriate public repositories (e.g., NCBI SRA, GEO, ProteomeXchange) and provide accession numbers. Expand the Methods to include all necessary parameters and thresholds.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of docking results
  - **Claim pointer** The authors state that docking studies indicated that Bgl2 has different binding sites for cellobiose and glucose, which "helps to alleviate feedback inhibition, probably accounting for the low level of glucose tolerance exhibited."
  - **Evidence pointer** Results section "Activity of PJ-1366 BGLs in the presence of glucose"; Figure 3; Methods "Homology modelling and docking studies"
  - **Concern** The docking study is presented as supporting evidence for glucose tolerance, but the results are not shown in the main text or supplementary materials. No docking scores, binding energies, or structural figures are provided. The connection between predicted binding sites and experimentally observed glucose tolerance is speculative. Furthermore, the experimental data show that 95% of BGL activity is lost at 0.1 M glucose, which is a severe inhibition, not a notable tolerance. The claim of "low level of glucose tolerance" is not well supported by the data presented.
  - **Why it matters** The docking results are used to explain a potentially important industrial property, but the evidence is incomplete and the interpretation appears overstated. The experimental data actually demonstrate strong glucose inhibition, which contradicts the narrative of tolerance.
  - **Resolution test** Provide the docking results in full, including scores and structural models. Reconcile the experimental data with the claims: 95% activity loss at 0.1 M glucose should be described as substantial inhibition, not tolerance. Either present a more nuanced interpretation or revise the claim.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Experimental design
  - **Affected element** Enzyme activity time course
  - **Evidence pointer** Figure 1; Methods "Enzyme activities"
  - **Issue** The authors state that biomass weight was not measured due to the insoluble nature of some substrates. This limits the interpretation of enzyme activity data, as activities are not normalized to biomass. Comparisons between substrates may reflect differences in growth rather than specific enzyme production.
  - **Required correction** Acknowledge this limitation explicitly in the Results or Discussion. If possible, provide protein concentration as an alternative normalization.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 4
  - **Evidence pointer** Figure 4
  - **Issue** The correlation heatmap in Figure 4 lacks axis labels, a color scale legend, and any indication of the statistical significance of the correlations. The reader cannot interpret the magnitude or reliability of the reported correlations.
  - **Required correction** Add a color scale with numerical values, label both axes clearly, and indicate which correlations are statistically significant.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Abstract and Results
  - **Evidence pointer** Abstract; Results "Overview of TFs and pathways regulating cellulase expression"
  - **Issue** The term "differentially expressed" is used without specifying the comparison (e.g., cellulose vs. glucose). The control condition is not clearly defined in the transcriptome experiment.
  - **Required correction** Specify the comparison being made and define the control condition in both the Abstract and Results.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature support
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** Several statements about TF function in other fungi are made without citations. For example, the roles of Rox1, Ste12, and Gcn4 in cellulase regulation are stated as established facts, but no references are provided in the text.
  - **Required correction** Add appropriate citations for all statements about previously characterized transcription factors and their roles in other organisms.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Data interpretation
  - **Affected element** Figure 2
  - **Evidence pointer** Figure 2
  - **Issue** The authors state that "Wheat bran did stimulate expression of exo- and endoglucanases, and, in agreement with the enzyme activity profiles, the expression could not be sustained." However, the figure shows relative abundance without error bars or statistical comparison across time points. The claim of "not sustained" is not clearly supported by the data as presented.
  - **Required correction** Provide statistical analysis of temporal trends or show individual data points to support this claim.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of statistical framework for transcriptome and correlation analyses
  - R1-M2: No functional validation of predicted regulators
  - R1-M3: Missing data availability and incomplete methods for omics datasets
  - R1-M4: Docking results not shown and interpretation inconsistent with experimental data

## Risk / unsupported claims
- The claim that 13 TFs are "potential regulators" of cellulase induction is unsupported without functional validation or statistical evidence for the correlations.
- The claim that Bgl2's distinct binding sites "help to alleviate feedback inhibition" is speculative and not supported by the presented docking data (which are not shown) or the experimental data (which show 95% inhibition at 0.1 M glucose).
- The statement that "cellulase expression is possibly preceded by up-regulation of 12 TFs and down-regulation of 16 TFs" is presented as a finding, but the temporal relationship is not established by the data (only a single 4-hour time point was analyzed).
- The claim that the combination of wheat bran and cellulose is the "best inducer" is based on enzyme activity comparisons without statistical testing.
- The assertion that "the lack of significant extracellular BGL activity could be a reason" for the decline in endoglucanase induction is purely speculative and not tested.
- The statement that "excellent catalytic activity and the low, but significant level of glucose tolerance... can explain the higher level of BGL activity" is not directly supported by kinetic or comparative data presented in this manuscript.