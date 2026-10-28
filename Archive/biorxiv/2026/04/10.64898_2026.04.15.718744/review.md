## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results sections for three protein systems, methods overview, supplemental figure descriptions)
- **Assessment boundary** Scientific content, data presentation, claims versus evidence, methodological transparency, and reproducibility as presented in the manuscript
- **Shared manuscript claim summary** The authors present GROQ-seq, a growth-based pooled assay coupling protein variant activity to antibiotic resistance via DHFR, and report pilot datasets for three protein classes (transcription factors LacI, RamR, VanR; T7 RNA polymerase; TEV protease), claiming broad mutational coverage, quantitative reproducibility, and utility for machine learning training
- **Visible evidence base** Abstract, introduction, results narrative for three systems, methods overview, supplemental figure legends, comparison to published datasets (Suckow, Tack, Meger, d'Oelsnitz, von der Dunk, Sundar, Meyer), tables referenced but not shown
- **Missing materials affecting confidence** All figures, tables, and supplemental figures referenced in the text are not provided; technical bulletins cited as references 2-4 are not included; the primary methods paper (Spinner et al., reference 1) is not available; raw data files are not accessible

## Reviewer
- **Overall assessment** This manuscript describes a substantial experimental effort to generate deep mutational scanning datasets for three functionally distinct protein classes using a unified growth-based selection platform. The conceptual framing, namely that large unified datasets across protein functions are needed to train generalizable predictive models, is timely and important. The reported dataset sizes (44,914 LacI, 32,593 RamR, 23,966 VanR, 34,641 T7 RNAP, 18,465 TEV variants) represent a significant resource contribution. However, the manuscript as presented is a data descriptor rather than a scientific study with mechanistic insights, and the absence of all figures, tables, and supplemental materials makes it impossible to evaluate the central claims of data quality, reproducibility, and quantitative accuracy. The comparisons to existing datasets are described only in narrative form with correlation coefficients, but the underlying scatter plots and analysis details are not visible. The claim that these are the largest openly available DMS resources for these proteins requires verification against the cited literature. The manuscript would benefit from clearer articulation of what is novel beyond the datasets themselves, and the technical limitations described (e.g., T7 RNAP dynamic range of only 0.7 orders of magnitude) raise questions about the generalizability of the platform across protein classes.

- **Who would be interested in the results, and why** Researchers in protein engineering, deep mutational scanning, and machine learning for protein function prediction would be the primary audience. The datasets could serve as training and benchmarking resources for models predicting transcription factor activity, polymerase function, and protease specificity. The unified experimental platform across protein classes addresses a recognized gap in the field, namely the lack of comparable datasets generated under consistent conditions. Biotechnology researchers interested in engineering LacI, RamR, VanR, T7 RNAP, or TEV protease for synthetic biology applications would also find the variant effect maps valuable. The comparison to prior datasets (Tack, Meger, d'Oelsnitz, Sundar) would interest groups studying assay-dependent effects in deep mutational scanning.

- **Major strengths**
  1. The conceptual motivation is strong: unified datasets across protein classes are genuinely needed for training generalizable protein function prediction models
  2. The platform design, using a calibration ladder for converting fitness to quantitative function values, addresses a known limitation in pooled assays
  3. The breadth of mutational libraries (SSVL, SSM, epPCR) and the inclusion of insertions and deletions beyond single substitutions is commendable
  4. The transparency about limitations (e.g., toxicity bias in TF circuits, low dynamic range for T7 RNAP) is refreshing and scientifically honest
  5. The reported reproducibility metrics (across barcodes, runs, and independent facilities) suggest careful experimental design

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim pointer** The manuscript claims to present sequence-function datasets with quantitative measurements, reproducibility metrics, and comparisons to existing datasets, but none of the supporting figures, tables, or supplemental materials are visible in the provided text
- **Evidence pointer** All figures (1-20), tables (1-3), and supplemental figures (1-5, 45) are referenced but not provided
- **Concern** The manuscript is fundamentally a data descriptor, yet the actual data presentation is entirely absent from the provided material. Every quantitative claim, from the distribution of variant effects to the correlation coefficients with prior datasets, depends on figures and tables that cannot be evaluated. The reader cannot assess whether the data support the stated conclusions about mutational robustness, positional effects, or agreement with published work. This is not a minor omission but a complete absence of the evidentiary basis for the paper's central claims.
- **Why it matters** Without access to the figures and tables, the scientific content of the manuscript cannot be verified. The claims about dataset quality, dynamic range, reproducibility, and biological insights are all unverifiable. A data descriptor that does not show its data cannot fulfill its purpose.
- **Resolution test** Provide all figures, tables, and supplemental materials. The manuscript should be re-reviewed with the complete set of visual data presentations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** The manuscript claims these are "the largest openly available DMS resources for these proteins" and that the data show "high reproducibility" across barcodes, runs, and independent facilities
- **Evidence pointer** Section "GROQ-seq Data on Transcription Factors, TEV Protease and T7 RNA Polymerase"; reference to Spinner et al. 1; Figures 10 and 15
- **Concern** The claim of being the largest openly available DMS resource for each protein is stated without a systematic comparison to existing databases or publications. For LacI, prior deep mutational scanning studies exist (e.g., Tack et al., which the authors cite), and the claim of "largest" requires a quantitative comparison of variant counts, mutational coverage, and accessibility. Similarly, the reproducibility claims reference a separate publication (Spinner et al.) and figures that are not provided. The reader cannot verify either the superlative claim or the reproducibility metrics.
- **Why it matters** The primary value proposition of this manuscript is the dataset resource itself. If the "largest" claim is inaccurate, or if the reproducibility metrics are not as strong as implied, the contribution is substantially diminished. These claims are central to the paper's significance and must be verifiable from the provided materials.
- **Resolution test** Provide a systematic comparison table of existing DMS datasets for each protein with variant counts and coverage. Show the reproducibility data in the main figures with clear statistical metrics.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The manuscript states that the T7 RNAP assay has "noticeably lower dynamic range, with little or no ability to distinguish variants with higher activity than wild-type" and that the TF circuit shows "mild toxicity at high transcriptional output, causing variants with high uninduced transcription to drop out of the dataset"
- **Evidence pointer** Sections "T7 RNA Polymerase" and "GROQ-seq Data on Transcription Factors"; Figures 11A, 12A; Supplemental Figure 3
- **Concern** These are significant technical limitations that directly affect the interpretability of the datasets. For T7 RNAP, a dynamic range of approximately 0.7 orders of magnitude (about 5-fold) is quite narrow, and the inability to detect gain-of-function variants limits the utility of the dataset for understanding activating mutations. For the TF assays, the dropout of high-activity variants due to toxicity introduces a systematic bias that could distort the apparent distribution of variant effects. The manuscript acknowledges these limitations but does not provide a quantitative assessment of their impact on the conclusions. For example, what fraction of variants dropped out? How does the truncation of the distribution affect the reported percentages of variants with wild-type-like activity?
- **Why it matters** These limitations affect the core scientific claims about mutational robustness. If a substantial fraction of high-activity variants are missing from the dataset, the reported percentages of tolerant positions may be overestimates. The reader needs to understand the magnitude of these biases to interpret the data correctly.
- **Resolution test** Provide quantitative estimates of dropout rates, show the distribution of variants across the dynamic range, and discuss how the truncation affects the reported conclusions about mutational tolerance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparative analysis
- **Claim pointer** The manuscript describes comparisons to existing datasets (Suckow, Tack, Meger, d'Oelsnitz, Sundar) with correlation coefficients, but the comparisons are only described narratively
- **Evidence pointer** Sections on LacI and RamR comparisons; Figures 9 and 20
- **Concern** The comparisons to prior datasets are a valuable aspect of the manuscript, as they address the question of whether sequence-function relationships are assay-dependent. However, the narrative descriptions of "weak correlation" (Spearman rho = 0.27 with Suckow), "approximately linear correlation" (rho = 0.54 with Tack), and "non-linear correlation" (rho = -0.64 with Meger) are insufficient without the actual scatter plots and a discussion of why the correlations are not stronger. The authors state that differences "highlight the sensitivity of sequence-function relationships to assay context," but this important point is not developed. What specific assay differences explain the discrepancies? Are the differences systematic or random?
- **Why it matters** The comparative analysis is one of the most scientifically interesting aspects of the manuscript, as it speaks to the generalizability of DMS measurements across platforms. A superficial treatment of these comparisons weakens the manuscript's contribution to understanding assay-dependent effects in deep mutational scanning.
- **Resolution test** Show the scatter plots for each comparison with the overlapping variant sets clearly identified. Provide a detailed discussion of the sources of discrepancy, including differences in assay design, growth conditions, and measurement scales.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The manuscript interprets positions where mutations increase repression as related to "allosteric communication between protein domains" and notes that "the ordering of mutational tolerance (RamR > VanR > LacI) mirrors the increasing fraction of alpha-helical content"
- **Evidence pointer** Sections on TF results; Figures 1-3, 5-7
- **Concern** The biological interpretations are intriguing but are presented with limited supporting analysis. The claim about allosteric communication is based on a small number of example positions (S61, N142 in LacI; S240 in VanR) without a systematic analysis of whether positions with gain-of-function mutations are enriched in specific structural or functional categories. The correlation between alpha-helical content and mutational tolerance is based on only three proteins, which is insufficient for a robust statistical claim. The authors should either temper these interpretations or provide additional analysis, such as a comparison with a larger set of proteins or a more rigorous structural analysis.
- **Why it matters** These interpretations go beyond the data description and make claims about protein biophysics. If they are not well-supported, they could mislead readers and undermine confidence in the authors' scientific judgment.
- **Resolution test** Provide a systematic analysis of gain-of-function positions in the context of protein structure and function. Either expand the alpha-helical content analysis to more proteins or soften the claim to a hypothesis-generating observation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that GROQ-seq enables "scalable characterization of large variant libraries" but does not specify the scale achieved in this study. The abstract also does not mention the key limitation of the T7 RNAP assay (low dynamic range) or the toxicity bias in the TF assays.
- **Required correction** Include the total number of variants characterized and briefly note the assay limitations to set appropriate expectations for readers.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods description
- **Evidence pointer** Section "GROQ-seq Analysis Pipeline"
- **Issue** The description of the Bayesian regression for calibration is too brief. The text mentions "well-calibrated posterior uncertainties" but does not describe the prior distributions, the likelihood function, or the validation approach for the calibration.
- **Required correction** Provide a more detailed description of the statistical model, including the prior choices and any validation against known standards.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data completeness
- **Affected element** Variant coverage
- **Evidence pointer** Tables 1-3
- **Issue** The text reports percentages of possible single-mutant variants covered (57.3% for LacI, 80% for RamR, 48.6% for VanR) but does not discuss whether the missing variants are randomly distributed or biased toward particular positions or amino acid substitutions.
- **Required correction** Provide an analysis of the missing variants to demonstrate that coverage is unbiased, or discuss the implications if bias exists.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** VanR comparison with Meyer et al.
- **Evidence pointer** Section "GROQ-seq Data on Transcription Factors"
- **Issue** The comparison with the Meyer et al. engineered VanR variant is based on only three mutations (T49I, A111V, P179S) and the authors note that A111V shows near-wild-type activity in their dataset. This is an interesting observation, but the discussion is brief and does not explore possible explanations for the discrepancy.
- **Required correction** Expand the discussion of this comparison, including possible reasons for the context-dependent effect of A111V.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure numbering
- **Evidence pointer** Sections on T7 RNAP and TEV protease
- **Issue** The text references "Figure 18B" for the T7 RNAP structure and "Figure 12B" for the TEV protease structure, but the figure numbering appears inconsistent with the order of presentation in the text. This may be a typographical error.
- **Required correction** Verify all figure cross-references for consistency.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Author contributions
- **Evidence pointer** Footnotes
- **Issue** The footnote indicates that an author was added after the original submission. This is noted transparently, but the manuscript does not include a formal author contributions statement or competing interests declaration.
- **Required correction** Add standard declarations for author contributions and competing interests.

## Risk / unsupported claims
- The claim that these are "the largest openly available DMS resources" for LacI, RamR, VanR, T7 RNAP, and TEV protease cannot be verified without a systematic comparison to existing databases and publications
- The claim of "high reproducibility" across independent facilities is referenced to a separate publication (Spinner et al.) and cannot be evaluated from the provided material
- The biological interpretation that gain-of-function mutations cluster in regions of allosteric communication is based on a small number of examples and is not systematically supported
- The correlation between alpha-helical content and mutational tolerance is based on only three proteins and is not statistically robust
- The comparison with the von der Dunk et al. finding that approximately 25% of single substitutions preserve backbone structure is suggestive but the connection to the observed 26.3-55.4% tolerance range across different proteins is not quantitatively developed
- The claim that the TEV protease dataset has "exceptional measurement resolution and dynamic range" is based on a comparison across 20 conditions, but the actual resolution metrics are not presented
- The statement that the T7 RNAP dataset is "the only deep mutational scanning effort on this protein to date" requires verification against the literature
- The manuscript does not provide information on the number of biological replicates, the sequencing depth, or the quality filtering thresholds used, making the data quality claims unverifiable